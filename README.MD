# Lab Overview

This project focusing on turning **procedural program** into **oop style program** the program task is to manage `books`, `members`.

```
library-management-oop/
│
├── oop_solution
│ ├── library_oop.py        # oop style program 
│ └── test_oop.py           # Tester for oop style
├── procedural_version
│ ├── library_procedural.py # procedural program
│ └── test_procedural.py    # Tester for procedural version
└── README.md               # This file 
 
```

---

# Design Overview

## Book Class

### `__init__` Function
- **Attributes:** `id`, `title`, `author`, `total_copies`, `available_copies`.  
- **Stores:**  
  - `id` in `self.id`.
  - `title` in `self.title`.
  - `author` in `self.author`.
  - `total_copies` in `self.total_copies`.
  - `available_copies` in `self.available_copies`.

### `can_borrow` Function
- **Return:**
The boolean value of `self.available_copies > 0`.

### `borrow_one` Function
- **Description:**
Call the `can_borrow` function if it's return `True` decrease `self.available_copies` by 1 then return `True` if `can_borrow` function return `False` this function will return `False`.

### `return_one` Function
- **Description:**
If `self.available_copies` < `self.total_copies` increase `self.available_copies` by 1 then return `True` if not return `False`.

---

## Member Class

### '__init__' Function
- **Attributes:** `id`, `name`, `email`, `borrowed_books`.
- **Stores:**
  - `id` in `self.id`.
  - `name` in `self.name`.
  - `email` in `self.email`.
  - `borrowed_books` in `self.borrowed_books`.
  
### 'can_borrow' Function
- **Description:**
If the length of `self.borrowed_books` is less than 3 return `True` otherwise return `False`.

### 'borrow_one' Function
- **Attributes:** `book_id`
- **Description:**
Call the `can_borrow` function if it's return `True` append `book_id` to the `self.borrowed_books` and return `True` otherwise return `False`.

---
## Library Class

### `__init__` Function
- **Attributes:** `books`, `members`.  
- **Stores:**
  - `books` in `self.books`.
  - `members` in `self.members`.
  - `self.borrowed_books` as an empty list.

### `add_book` Function
- **Attributes:** `book_id`, `title`, `author`, `available_copies`  
- **Variable:**  
  - `book` — create `Book` using attributes.
- **Description:** Create `Book` object then append it to `self.books` and finally print a message to announce the user that the book has been added.  

### `add_member` Function
- **Attributes:** `member_id`, `name`, `email`.  
- **Variable:**  
  - `member` — A `Member` object that made from attributes.
- **Description:**  Create `Member` object then append it to `self.members` then print a message to announce the user that the member has been resgistered.

### `borrow_book` Function
- **Attributes:** `member_id`, `book_id`
- **Variables:**
  - `member` — contains the member from `self.find_member` using `member_id`.
  - `book` — contains the book from `self.find_book` using `book_id`.
  - `transaction` — a dictionary that contains `member_id`, `book_id`, `member_name`, `book_title`.
- **Description:** First, the function check if it can borrow the book or not if not return `False` but if it can call the `borrow_one` function from the `book` and `borrow_one` function from the `member` then append the `transaction` to the `self.borrowed_books` after that print a message saying that which member borrow which book and finally return `True`

### `return_book` Function
- **Attributes:** `member_id`, `book_id`.
- **Variables:**
  - `member` — contains the member from `self.find_member` using `member_id`.
  - `book` — contains the book from `self.find_book` using `book_id`.   
- **Description:** First, the function check if the member and the book are exist and check if the book has been borrowed or not if not return `False` then call `return_one` function from the book and remove `book_id` from the `member.borrowed_books` after that pop the transaction that has the same `member_id` and `book_id` from the transactions then print a message telling that this `member` has return the `book` then return `True`.

### `display_available_books` Function
- **Description:** display the information of all book that can borrow from the `books`.

### `display_member_books` Function
- **Attributes:** `member_id`.
- **Variables:**
  - `member` — contains the member from `self.find_member` using `member_id`.
- **Description:** display all the books that this `member` borrowed.

### `find_book` Function
- **Attributes:** `book_id`.
- **Descritption:** loop through the `self.books` if the `book.id` is equal to `book_id` then return that `book` if doesn't find anything return `None`.

### `find_member` Function
- **Attributes:** `member_id`.
- **Description:** loop through the `self.members` if the `member.id` is equal to `member_id` then return that `member` if doesn't find anything return `None`.

---

## Testing — test_oop.py
In the test_oop.py have case that cover these cases:
  - Adding books and members.
  - Borrowing and returning books.
  - Displaying information.
  - Borrowing unavailable books.
  - Exceeding borrowing limit.
  - Return books not borrowed.
  - Non-existent books/members.

---
# How to Run

You can run the `test_oop.py` using the `py` command.
