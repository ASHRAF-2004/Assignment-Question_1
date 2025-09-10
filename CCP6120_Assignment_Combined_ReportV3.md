
# CCP6120 OOPDS Assignment - Report

## 1. Introduction
This report discusses two C++ programs designed for **Object-Oriented Programming (OOP)** and **Data Structures** using **Linked Lists**, **Stacks**, and **Queues**. The assignment includes:

1. **Bank Account Management System** – implemented using a **Singly Linked List**.
2. **Warehouse Inventory & Shipping System** – utilizing **Stacks (LIFO)** and **Queues (FIFO)**.

Each program adheres to **OOP principles**, such as **encapsulation**, **dynamic memory management**, and **modular design**.

---

## 2. Bank Account Management System (C++ - Singly Linked List)

### Overview:
The **Bank Account Management System** is a console application that manages user accounts using a **singly linked list**. Each node in the list represents an account, which stores the account number, customer name, and balance.

### Key Features:
- **Add Account**: Create a new account with unique account numbers, customer names, and balances.
- **Display Accounts**: View the list of all existing accounts.
- **Deposit/Withdraw**: Perform deposits or withdrawals, ensuring sufficient balance.
- **Search/Delete Accounts**: Locate or remove an account based on its number.
- **Exit**: Close the system.

### Method Explanations:
1. **addAccount()**: Adds a new account to the linked list, preventing duplicates.
2. **deposit()**: Deposits a specified amount into an existing account.
3. **withdraw()**: Withdraws a specified amount, ensuring sufficient balance.
4. **deleteAccount()**: Deletes an account from the linked list.
5. **displayAll()**: Displays all accounts.

```cpp
class Node {
public:
    int accNo;
    string name;
    long long balance;
    Node* next;
    Node(int a, const string& n, long long b) : accNo(a), name(n), balance(b), next(nullptr) {}
};
```

### Example of Usage:
- **Add Account**: Adds account number `1001`, customer name "John Doe", and initial balance of `5000`.
- **Deposit**: Deposits `1500` into account `1001`, updating the balance to `6500`.
- **Withdraw**: Withdraws `3000` from account `1001`, leaving a balance of `3500`.
- **Delete Account**: Deletes account `1001` from the list.
- **Display All Accounts**: Shows all current accounts in the list.

### Code Implementation:
The system uses dynamic memory management to handle the linked list of accounts. Each account is represented by a `Node` class. The `Bank` class manages the list operations, ensuring proper insertion, searching, and deletion.

---

## 3. Warehouse Inventory & Shipping System (C++ - Stack and Queue)

### Overview:
This **Warehouse Inventory & Shipping System** allows for managing incoming and outgoing inventory using **Stack** and **Queue** data structures.

- **Stack**: Used for managing incoming inventory (Last In, First Out - LIFO).
- **Queue**: Used for managing outgoing shipments (First In, First Out - FIFO).

### Key Features:
- **Add Incoming Item**: Adds an item to the inventory stack.
- **Process Incoming Item**: Moves an item from the stack to the shipping queue.
- **Ship Item**: Ships an item from the shipping queue.
- **View Last Incoming Item**: Shows the most recently added item in the inventory.
- **View Next Shipment**: Shows the next item to ship from the queue.
- **Exit**: Close the system.

### Method Explanations:
1. **pushItem()**: Adds an incoming item to the stack.
2. **popItem()**: Removes the top item from the stack for processing.
3. **enqueue()**: Adds an item to the shipping queue.
4. **dequeue()**: Ships an item from the queue.
5. **peekLastItem()**: Views the most recent item in the stack.
6. **peekNextItem()**: Views the next item in the queue.

```cpp
class Stack {
private:
    static const int MAX = 100;
    string items[MAX];
    int top;
public:
    Stack() { top = -1; }
    void pushItem(string item);
    string popItem();
    string peekLastItem();
    bool isEmpty();
};
```

### Example of Usage:
- **Add Incoming Item**: Adds items like "Laptop" and "Monitor" to the stack.
- **Process Incoming Item**: Moves "Monitor" and "Laptop" from the stack to the queue.
- **Ship Item**: Ships items "Monitor" and "Laptop" from the queue.
- **View Last Incoming Item**: Displays "Monitor" as the last item added.
- **View Next Shipment**: Shows "Monitor" as the next item to be shipped.

### Code Implementation:
The program uses **Stacks** for incoming inventory and **Queues** for outgoing shipments. The `Stack` class manages the LIFO operations, while the `Queue` class manages the FIFO operations. Both classes ensure that the system handles inventory and shipping efficiently.

---

## 4. Conclusion
Both programs are designed with **OOP principles** in mind. The **Bank Account Management System** effectively utilizes a **singly linked list** to manage accounts, while the **Warehouse Inventory & Shipping System** uses **Stacks** and **Queues** to simulate inventory management and order fulfillment.

Each program has a **menu-driven interface**, which ensures ease of use and user interaction. Proper error handling is integrated to handle invalid operations, such as duplicate account creation or attempting to ship when the queue is empty.

The **bank system** demonstrates **dynamic memory management** using linked lists, while the **warehouse system** showcases **data structure operations** using stacks and queues to manage inventory and shipments.

```cpp
// Compilation and Execution Instructions for both programs
g++ bank_system.cpp -o bank_system
./bank_system

g++ warehouse_system.cpp -o warehouse_system
./warehouse_system
```

---

## 5. References
- **Bank Account Management System** (CCP6120-OOPDS Assignment).
- **Warehouse Inventory & Shipping System** (CCP6120-OOPDS Assignment).

## 8. Bank Account Management System (C++ · Singly Linked List) - Full Explanation

### 1. `addAccount()` — Adds a new account to the linked list.
This method is responsible for adding a new account to the linked list. It ensures that the account number is unique and the balance is valid before the account is added.

#### Code:
```cpp
bool addAccount(int accNo, const string& name, long long initial) {
    if (accNo <= 0 || initial < 0) return false;  // Invalid account number or balance
    if (exists(accNo)) return false;  // Account already exists

    Node* n = new (std::nothrow) Node(accNo, name, initial);
    if (!n) return false;  // Memory allocation failed

    // Insert at the beginning of the list (O(1) operation)
    n->next = head;
    head = n;
    return true;
}
```

#### Explanation:
- Checks if the account number and initial deposit are valid.
- Ensures no duplicate accounts exist.
- Allocates memory for the new account node and inserts it at the front of the list.

#### Example Result:
If an account with account number 1001 is added with the name "John Doe" and an initial deposit of 5000, the result will be:
```
Account added successfully: Account No: 1001; Name: John Doe; Balance: 5000
```

### 2. `deposit()` — Deposits a specified amount into an account.
This method allows users to deposit a specified amount into an account. It checks if the amount is positive and updates the account balance.

#### Code:
```cpp
bool deposit(int accNo, long long amount) {
    if (amount <= 0) return false;  // Invalid deposit amount
    Node* cur = head;
    while (cur) {
        if (cur->accNo == accNo) {
            cur->balance += amount;
            return true;
        }
        cur = cur->next;
    }
    return false;  // Account not found
}
```

#### Explanation:
- Ensures that the deposit amount is valid (greater than zero).
- Searches for the account and adds the deposit amount to the balance.

#### Example Result:
For account 1001 with balance 5000, depositing 1500 results in:
```
Deposit successful: Account No: 1001; New Balance: 6500
```

### 3. `withdraw()` — Withdraws a specified amount from an account, subject to balance validation.
This method allows the user to withdraw a specified amount, but only if there are sufficient funds in the account. It performs a balance validation.

#### Code:
```cpp
int withdraw(int accNo, long long amount) {
    if (amount <= 0) return -1;  // Invalid withdrawal amount
    Node* cur = head;
    while (cur) {
        if (cur->accNo == accNo) {
            if (cur->balance < amount) return -2;  // Insufficient funds
            cur->balance -= amount;
            return 1;  // Withdrawal successful
        }
        cur = cur->next;
    }
    return 0;  // Account not found
}
```

#### Explanation:
- Checks if the withdrawal amount is valid and that sufficient funds exist.
- Updates the balance if the withdrawal is valid, or returns an error if the account does not have enough funds.

#### Example Result:
For account 1001 with balance 5000, withdrawing 3000 results in:
```
Withdrawal successful: Account No: 1001; New Balance: 2000
```

### 4. `deleteAccount()` — Deletes an account from the list.
This method removes an account from the linked list. It ensures that the account exists before attempting to delete it.

#### Code:
```cpp
bool deleteAccount(int accNo) {
    if (!head) return false;  // Empty list
    if (head->accNo == accNo) {  // If head node is to be deleted
        Node* temp = head;
        head = head->next;
        delete temp;
        return true;
    }
    Node* prev = head;
    Node* cur = head->next;
    while (cur) {
        if (cur->accNo == accNo) {
            prev->next = cur->next;
            delete cur;
            return true;
        }
        prev = cur;
        cur = cur->next;
    }
    return false;  // Account not found
}
```

#### Explanation:
- Searches for the account and removes it from the list.
- Updates the pointers to ensure the list remains intact after deletion.

#### Example Result:
For account 1001, deleting the account results in:
```
Account deleted: Account No: 1001 removed from the system.
```

### 5. `displayAll()` — Displays details of all accounts in the list.
This method iterates through the linked list and displays the details of each account.

#### Code:
```cpp
void displayAll() const {
    if (!head) {
        cout << "No accounts found.\n";
        return;
    }
    Node* cur = head;
    while (cur) {
        cout << "Account No: " << cur->accNo << "; Name: " << cur->name << "; Balance: " << cur->balance << "\n";
        cur = cur->next;
    }
}
```

#### Explanation:
- Iterates through the entire list and displays each account's information in a readable format.

#### Example Result:
For multiple accounts in the list, the result is:
```
Account No: 1001; Name: John Doe; Balance: 5000
Account No: 1002; Name: Jane Smith; Balance: 2000
Account No: 1003; Name: Mark Lee; Balance: 3000
```

---

## 9. Warehouse Inventory and Shipping System Using Stack and Queue

### 9.1 Overview 
This project simulates the operations of a small warehouse inventory system. The system manages: 

- Incoming items (e.g., items newly added into the warehouse). 
- Outgoing shipments (e.g., items leaving the warehouse for delivery).

The **Stack (LIFO)** is used for incoming items because the last item added is the first to be processed. This reflects real-world warehouse behaviour where newly received items are usually on top and processed first.

The **Queue (FIFO)** is used for shipping because shipments must follow the first come, first served rule. The first processed item must be shipped before newer ones.

### 9.2 Features
The system provides a simple menu-driven interface with the following options:

1. **Add Incoming Item** – Adds a new item into the incoming stack.
2. **Process Incoming Item** – Moves the latest incoming item from the stack into the shipping queue.
3. **Ship Item** – Removes the next item from the queue and marks it as shipped.
4. **View Last Incoming Item** – Displays the item currently at the top of the stack.
5. **View Next Shipment** – Displays the item at the front of the shipping queue.
6. **Exit** – Terminates the program.

### 9.3 Technologies Used
- **Language**: C++
- **Environment**: Visual Studio Code with g++ compiler
- **Data Structures**:
  - **Stack** (LIFO) for incoming items.
  - **Queue** (FIFO) for outgoing shipments.

### 9.4 Implementation Details

#### Stack (Incoming Items)
The **Stack** is implemented using a fixed-size array. It supports **LIFO operations** and prevents **overflow** and **underflow**.

#### Queue (Outgoing Shipments)
The **Queue** is implemented using an array. It supports **FIFO operations** and uses **front** and **rear** indices to manage elements. **Circular indexing** is used for efficient handling.

---

## 10. Conclusion
Both systems demonstrate the effective use of **OOP principles** and **data structures** to simulate real-world applications in the **banking** and **warehouse management** domains. Each system handles memory efficiently, implements error handling, and provides a **menu-driven interface** for user interaction.

---

## 11. References
- **Bank Account Management System** (CCP6120-OOPDS Assignment).
- **Warehouse Inventory & Shipping System** (CCP6120-OOPDS Assignment).
