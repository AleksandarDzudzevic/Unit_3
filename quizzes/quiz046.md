![](https://github.com/AleksandarDzudzevic/Unit_3/blob/main/quiz046text.png)
## Python code:
```.py
import sqlite3

haiku = """Code flows like a stream
Algorithms guide its way
In silence, it solves"""

connection = sqlite3.connect("quiz46.db")
# step 2 get the cursor of the database
cursor = connection.cursor()
# step 3 ready run queries
query = f"""Create Table if not exists Words(
id INTEGER PRIMARY KEY,
word_text NOT NULL,
word_length int 
)
"""
cursor.execute(query)

# Step 4 commit save changes in the database
connection.commit()

for word in haiku.split():
    query2=f"""
    Insert into Words(word_text,word_length) values('{word}',{len(word)});
    """

    cursor.execute(query2)
    connection.commit()

connection.commit()
query3=f"""
Select avg(word_length) from words;
"""
cursor.execute(query3)
print(cursor.fetchone())


# Step 5 :close the connection
connection.close()
```
## SL part proof:
![](https://github.com/AleksandarDzudzevic/Unit_3/blob/main/quiz046testSl.png)
## HL part proof
![](https://github.com/AleksandarDzudzevic/Unit_3/blob/main/quiz046testHl.png)
