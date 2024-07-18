import sqlite3
def authenticate_user(username, password):
conn = sqlite3.connect('bank.db')
cursor = conn.cursor()
query = f"SELECT * FROM users WHERE username='{username}' AND password='{password}'"
cursor.execute(query)
user = cursor.fetchone()
conn.close()
return user
username = input("Enter username: ")
password = input("Enter password: ")
user = authenticate_user(username, password)
if user:
print("Login successful!")
else:
print("Invalid credentials.")
