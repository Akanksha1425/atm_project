# atm_project
# ATM Simulation

This project is a simple ATM simulation written in Python. It allows users to check their balance, withdraw money, deposit money, and exit the simulation. The purpose of this project is to demonstrate basic Python programming concepts including conditionals, loops, and input handling.

## Features

- **Check Balance:** Allows the user to view their current balance.
- **Withdraw Amount:** Allows the user to withdraw a specified amount from their account, ensuring they do not withdraw more than their available balance.
- **Deposit Amount:** Allows the user to deposit a specified amount into their account.
- **Exit:** Allows the user to exit the ATM simulation.

## Getting Started

### Prerequisites

Make sure you have Python installed on your system. You can download it from [here](https://www.python.org/downloads/).

### Running the Program

1. Clone the repository to your local machine:
    ```bash
    git clone https://github.com/your-username/your-repository.git
    ```
2. Navigate to the project directory:
    ```bash
    cd your-repository
    ```
3. Run the program:
    ```bash
    python atm_simulation.py
    ```

## Code Explanation

Here is a brief explanation of the code structure:

- **Initialization:** The program starts by simulating the insertion of a card and asking for the user's PIN.
- **Main Menu:** If the PIN is correct, the user is presented with a menu of options (check balance, withdraw, deposit, exit).
- **Operations:** Depending on the user’s choice, the program performs the corresponding operation and then returns to the main menu until the user chooses to exit.

```python
import time

print("Please insert your card")
time.sleep(5)
password = 1234
balance = 5000

pin = int(input("Enter your Pin: "))
if pin == password:
    while True:
        print("""
        1 == Check balance
        2 == Withdraw amount
        3 == Deposit balance
        4 == Exit
        """)
        try:
            option = int(input("Please enter your choice: "))
        except ValueError:
            print("Please enter a valid option")
            continue

        if option == 1:
            print(f"Your current balance is {balance}")
        elif option == 2:
            withdraw_amount = int(input("Please enter your withdrawal amount: ")) 
            if withdraw_amount > balance:
                print("Not enough balance")
            else:
                balance -= withdraw_amount
                print(f"{withdraw_amount} is debited from your account")
                print(f"Your updated balance is {balance}")
        elif option == 3:
            deposit_amount = int(input("Please enter deposit amount: "))
            balance += deposit_amount
            print(f"{deposit_amount} is credited to your account")
            print(f"Your updated balance is {balance}")
        elif option == 4:
            print("Thank you for using the ATM. Goodbye!")
            break
        else:
            print("Invalid option. Please try again.")
else:
    print("Wrong Pin")
