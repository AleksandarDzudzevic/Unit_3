![](https://github.com/AleksandarDzudzevic/Unit_3/blob/main/quiz49text.png)
## Pythion code
```.py
import sqlite3
from passlib.context import CryptContext
red = "\33[0;31m"
green = "\033[0;32m"
pwd_config = CryptContext(schemes = ["pbkdf2_sha256"],
                          default = "pbkdf2_sha256",
                          pbkdf2_sha256__default_rounds = 30000
                          )


# this function receives unsafe password and returns the hashed password
def encrypt_password(user_passowrd):
    return pwd_config.encrypt(user_passowrd)


def check_password(hashed_password, user_password):
    return pwd_config.verify(user_password, hashed_password)


class database_worker:
    def __init__(self, name):
        self.connection = sqlite3.connect(name)
        self.cursor = self.connection.cursor()

    def search(self, query):
        result = self.cursor.execute(query).fetchall()
        return result

    def run_save(self, query):
        self.cursor.execute(query)
        self.connection.commit()

    def close(self):
        self.connection.close()


x = database_worker("bitcoin_exchange.db")
query = "SELECT * from ledger"
result = x.search(query)
#print(result)
x.close()
bitcoin_amount=0
for row in result:
    #print(row)
    id= row[0]
    sender_id=row[1]
    receiver_id=row[2]
    amount=row[3]
    hash=row[4]
    string_hash=f"id {id},sender_id {sender_id},receiver_id {receiver_id},amount {amount}"
    equal=check_password(hashed_password = hash, user_password = string_hash)
    if equal is False:
        print(f"{red} Error signature")
    else:
        print(f"{green} Signature matches")
        bitcoin_amount+=amount
print(f"Total amount of btc is {bitcoin_amount} BTC")
```
## Proof
![](https://github.com/AleksandarDzudzevic/Unit_3/blob/main/quiz049test.png)
