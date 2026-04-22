# atm-system-python
#Hello! I am new to programming and learning python. This is the first project I made after learning about 2 weeks.

#Features:
- Login with 3 attempts
- Deposit money
- Withdraw money
- Check balance

#What I learned:
- Dictionary and list usage
- Loops and condtions
- Basic systm design

#What I will learn next:
- Add file saving
- Improve structure with functions

#Below is the code I wrote:

# User Data
users = {
"user1": {
"id": "eric.12",
"password": "1234",
"balance": 5000
},
"user2": {
"id": "jack19",
"password": "9999",
"balance": 10000
},
"user3": {
"id": "liam41",
"password": "9876",
"balance": 8000
}
}

attempt = 0

while attempt < 3:

# Ask for Login
id_input = input("Enter your ID: ")
password_input = input("Enter your password: ")

# set current user
current_user = None

# check if the user exists and the password is correct
for user in users.values():
if id_input == user["id"] and password_input == user["password"]:
print("Access Granted!")
current_user = user
break

if current_user:

# Welcome message
print("--Welcome to The Bank of Something!--")

# menu loop
while True:
menu_selection = int(input("--Please select your Option!-- \nEnter 1 for Withdraw. \nEnter 2 for Deposit. \nEnter 3 to Check Balance. \nEnter 4 for Exit \nEnter your Option: "))

if menu_selection == 1:

withdraw_amount = int(input("You have selected Withdraw! \nPlease enter your withdraw amount: "))

if withdraw_amount <= current_user["balance"]:
current_user["balance"] -= withdraw_amount
print(f"You have successfully withdrawn {withdraw_amount} from your account. \nYour new balance is {current_user['balance']}")
else:
print("Insufficient balance!")

elif menu_selection == 2:

deposit_amount = int(input("Enter your deposit amount: "))
current_user["balance"] += deposit_amount
print(f"You have successfully deposited {deposit_amount} to your account. \nYour new balance is {current_user['balance']}.")

elif menu_selection == 3:
print(f"Your balance is {current_user['balance']}.")

elif menu_selection == 4:
print("Thank you for using our services!")
break

else:
print("Invalid option! \nTry Again!")

break

else:
print("Wrong ID or password! \nTry Again!")
attempt += 1

if attempt >= 3:
print("Too many failed attempts. Please try again later.")
