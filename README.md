import sqlite3

db = sqlite3.connect(":memory:")

cursor = db.cursor()

cursor.execute('''
create table Ages(
  name VARCHAR(128),
  age INTEGER
)''')


cursor.execute('''DELETE FROM Ages''')

cursor.execute('''INSERT INTO Ages (name, age) VALUES ('Mara', 28)''')
cursor.execute('''INSERT INTO Ages (name, age) VALUES ('Otto', 33)''')
cursor.execute('''INSERT INTO Ages (name, age) VALUES ('Fyn', 31)''')
cursor.execute('''INSERT INTO Ages (name, age) VALUES ('Neshawn', 17)''')


cursor.execute('''SELECT hex(name||age) AS X FROM Ages ORDER BY X''')


user1 = cursor.fetchone()
print("The first row in the resulting record set: " + user1[-1])

db.commit()
db.close()

