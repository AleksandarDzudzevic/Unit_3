## Python code
![](https://github.com/AleksandarDzudzevic/Unit_3/blob/main/quiz047text.png)
```.py
import sqlite3
from passlib.context import CryptContext

pwd_config = CryptContext(schemes = ["pbkdf2_sha256"],
                          default = "pbkdf2_sha256",
                          pbkdf2_sha256__default_rounds = 30000
                          )


# this function receives unsafe password and returns the hashed password
def encrypt_password(user_passowrd):
    return pwd_config.encrypt(user_passowrd)


def check_password(hashed_password, user_password):
    return pwd_config.verify(user_password, hashed_password)


from kivymd.app import MDApp
from secure_password import encrypt_password


class database_worker:
    def __init__(self, name):
        self.connection = sqlite3.connect("payments.db")
        self.cursor = self.connection.cursor()

    def search(self, query):
        result = self.cursor.execute(query).fetchall()
        return result

    def run_save(self, query):
        self.cursor.execute(query)
        self.connection.commit()

    def close(self):
        self.connection.close()


class quiz047(MDApp):
    def __init__(self, **kwargs):
        super().__init__(**kwargs)
        self.components = {"basic": 0}

    def build(self):
        return

    def save(self):
        pass

    def update(self):
        base = self.root.ids.base.text
        hash = ""
        ids = ["inhabitant", "income_tax", "pension", "health"]
        if base != "":
            total = int(base)
            hash += f"base{total}"
            for id in ids:
                value = self.root.ids[id].text
                if value != "":
                    new_value = f"{int(value) * int(base) // 100} JPY"
                    total -= int(value) * int(base) // 100
                    hash += f"{id}{value}"
                else:
                    new_value = "JPY"
                    hash += f"text"
                self.root.ids[id + "_label"].text = new_value
            hash += f"total{total}"
            self.root.ids.salary_label.text = f"{total} JPY"
            encrypted_hash = encrypt_password(hash)
            self.root.ids.hash.text = encrypted_hash[(len(encrypted_hash) - 50):len(encrypted_hash)]

    def save(self):
        base = self.root.ids.base.text
        hash = ""
        ids = ["inhabitant", "income_tax", "pension", "health"]

        if base != "":
            total = int(base)
            hash += f"base{total}"
            for column in ids:
                value = self.root.ids[column].text
                if value != "":
                    new_value = f"{int(value) * int(base) // 100} JPY"
                    total -= int(value) * int(base) / 100
                    hash += f"id_of_textField{value}"
                else:
                    new_value = " JPY"
                    hash += f"id_of_textField{0}"
                self.root.ids[f"{column}_label"].text = new_value
            hash += f"total{total}"
            self.root.ids.salary_label.text = f"{total} JPY"
            encrypted_hash = encrypt_password(hash)
            self.root.ids.hash.text = encrypted_hash[:50]

        inhabitant = int(self.root.ids.inhabitant_label.text.split(" JPY")[0])
        income_tax = int(self.root.ids.income_tax_label.text.split(" JPY")[0])
        pension = int(self.root.ids.pension_label.text.split(" JPY")[0])
        health = int(self.root.ids.health_label.text.split(" JPY")[0])
        total = int(self.root.ids.salary_label.text.split(" JPY")[0].split('.')[0])
        hash = self.root.ids.hash.text

        query = f"INSERT into payments(base, inhabitant, income_tax, pension, health, total, hash) values('{int(base)}', '{inhabitant}', '{income_tax}', '{pension}', '{health}', '{total}', '{hash}')"
        db = database_worker("payments.db")
        db.run_save(query)
        db.close()
        self.root.ids.hash.text = f"Payment saved"

    def clear(self):
        for label in ["base", "inhabitant", "income_tax", "pension", "health"]:
            self.root.ids[label].text = ""
            self.root.ids[label + "_label"].text = " JPY"

        self.root.ids["salary_label"].text = " JPY"
        self.root.ids.hash.text = "----"


    def fraud(self):
        data = database_worker("payments.db")
        query = "SELECT * from payments"
        result = data.search(query)
        data.close()
        print(len(result))
        for column in result:
            base = column[1]
            inhabitant = column[2]
            income_tax = column[3]
            pension = column[4]
            health = column[5]
            total = column[6]
            hash = column[7]
            hash = hash[-50:]
            hash_to_check = f"base{base},inhabitant{int(inhabitant)//int(base) * 100},income_tax{int(income_tax)//int(base) * 100},pension{int(pension)//int(base)*100},health{int(health)//int(base)*100},total{int(total)//int(base)*100}"
            encrypted_hash = encrypt_password(hash_to_check)
            if encrypted_hash[-50:] == hash:
                print(f"Payment {column[0]} NOT FRAUD")
            else:
                print(f"Payment {column[0]} FRAUD")
m = quiz047()
create = """CREATE TABLE if not exists payments(
            id INTEGER PRIMARY KEY,
            base int,
            inhabitant int,
            income_tax int,
            pension int,
            health int
            total int,
            hash text
    )"""
m.fraud()
m.run()
```
## Database payments.db given 
![](https://github.com/AleksandarDzudzevic/Unit_3/blob/main/quiz047db.png)
## Proof
![](https://github.com/AleksandarDzudzevic/Unit_3/blob/main/quiz047test.gif)
