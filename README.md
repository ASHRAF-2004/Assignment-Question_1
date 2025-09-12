# Bank Account Management System Using Singly Linked List in C++

## Overview
Design and implement a Bank Account Management System in C++ using Object-Oriented Programming (OOP) concepts and singly linked lists. Your system should define appropriate classes, encapsulating data and behaviors using principles such as encapsulation, modularity, and dynamic memory management.

Each node in the list must represent a bank account with:
- Account Number
- Customer Name
- Account Balance

### Implement class methods to:
1. Add a new account (prevent duplicates)
2. Display all accounts
3. Search by account number
4. Deposit and withdraw (with balance validation)
5. Delete an account
6. Exit the system

### Demonstrate use of:
- Class encapsulation
- Proper memory handling with constructors/destructors
- A menu-driven interface for user interaction

## Sample Output Preview
```
1. Add Account
2. Display Accounts
3. Deposit
4. Withdraw
5. Search Account
6. Delete Account
7. Exit
Enter choice: 1
Enter unique account number: 12345
Enter full name: John Doe
Enter initial balance (>= 0): 1000
Account added.

Enter choice: 2
Account No: 12345; Name: John Doe; Balance: 1000

Enter choice: 3
Enter account number: 12345
Enter deposit amount (> 0): 500
Deposit successful.

Enter choice: 4
Enter account number: 12345
Enter withdrawal amount (> 0): 200
Withdraw successful.

Enter choice: 6
Enter account number to delete: 12345
Account deleted.

Enter choice: 7
Exiting...
```

## Marking Rubric (Total: 25 Marks)

### Criteria
| Criteria | Marks |
| -------- | ----- |
| Class design & OOP principles (encapsulation, constructors, destructors) | 5 |
| Linked list implementation (add, search, display) | 5 |
| Functionality: deposit, withdraw, error handling | 5 |
| Dynamic memory management | 4 |
| Menu-driven interface & usability | 3 |
| Code readability & comments | 3 |
