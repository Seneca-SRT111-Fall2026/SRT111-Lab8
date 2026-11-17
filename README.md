<h1 align="center">SRT111 Lab 8 - Fall 2026</h1>

<p align="center">
<b>Prepared by:</b> Tiayyba Riaz<br>
<b>Total Marks:</b> 10<br>
<b>Percentage Towards Final Grade:</b> 2%
</p>

Python is an **object-oriented** language: almost everything you have used so far, such as strings, lists, dictionaries and even Pandas DataFrames, is an **object**. An object holds some **data** and has **methods** that work on that data. Objects are made from **classes**. A class is a blueprint: it says which data (instance variables) each object stores and which methods it has.

In the first part of this lab, you will **use** a class that is already written, **complete** a method inside a class, and **extend** the `CashRegister` class from the Week 11 slides with an `undo()` method. In the second part, you will work with **several objects** of the same class, see what happens when two variables **refer** to the same object, add a **class variable** for the tax rate, and finally use a **list of tuples** inside a new class to print a store receipt.

In this lab, every class lives in its own file (for example `dog.py`), and you test it from a separate **tester** file (for example `task1.py`) that imports the class. You will continue to use a `main()` function in every tester, as practised in Labs 4 to 7.

The lab is divided into two components:

- **Part A: In-Class Lab** (must be completed during the scheduled lab period and demonstrated to the professor for grading).
- **Part B: Take-Home Lab** (can be completed independently after the scheduled class and is submitted as a link to your GitHub repository).

## Academic Integrity and Use of AI

This lab is intended to assess your individual understanding of Python programming. You may use AI tools (e.g., ChatGPT, Copilot, Gemini) to help explain concepts, syntax, or error messages. However, all submitted code must be your own work, and you must be able to explain your solution if asked by the professor.

Submitting copied, shared, or AI-generated solutions as your own work may result in a grade of zero and may be handled according to the College Academic Integrity Policy.

## Lab Objectives

By the end of this lab, you should be able to:

- Explain the difference between a class and an object.
- Create objects from a class and call their methods with dot notation.
- Import a class from another file into a tester program.
- Explain what the constructor `__init__`, the `self` parameter and instance variables do.
- Complete and add methods in an existing class, and use a list as an instance variable.
- Create several objects of the same class and explain why each one has its own data.
- Explain what happens when two variables refer to the same object.
- Use a class variable that is shared by all objects of a class.
- Store items as a list of tuples inside a class and print a formatted receipt.
- Test a class by printing actual and expected results.

## Required Comment Header

For every file created in this lab (class files **and** tester files), include the following comment block at the top of the file. The starter code in this lab does **not** include it: add it yourself to every file, before the starter code. Marks are deducted for every missing header.

```python
# Author: Your Name
# Date: YYYY-MM-DD
# Purpose: Brief description of what the program does.
```

## Setting Up: One Folder for the Whole Lab

The tester files import the classes with lines such as `from dog import Dog`. This works only when the class file and the tester file are in the **same folder** and you run the tester **from that folder**. For this reason, use **VS Code** for both parts of this lab (not Jupyter Lab), and keep **all** Lab 8 files in one folder.

- Open your local Git repository `SRT111F2026` on your computer.
- Create a new folder named `Lab08` inside the repository (capital `L`, then a zero: `Lab08`).
- Open the `Lab08` folder in VS Code. Create every file for Part A and Part B in this folder.
- Run each tester from the VS Code terminal, inside `Lab08`, for example: `python task1.py` (on a Mac, use `python3` if `python` is not found).

There are no starter files to download: copy the starter code for each task from this page.

<details markdown="1">

<summary><b>Common Errors in This Lab</b></summary>

<br>

| Error message | Most likely cause |
|---|---|
| `ModuleNotFoundError: No module named 'dog'` | `dog.py` is not in the same folder as the tester, or the terminal is not in the `Lab08` folder. Check the file name (all lower case). |
| `TypeError: ... takes 0 positional arguments but 1 was given` | You forgot `self` in the method definition: `def click(self):` |
| `NameError: name '_value' is not defined` | You forgot `self.` in front of an instance variable inside a method. |
| `<bound method ...>` is printed | You forgot the `()` when calling a method: `tally.getValue()` |
| `<__main__.Dog object at 0x...>` is printed | You printed the object itself. Call one of its methods instead. |
| `None` is printed | The method has no `return` statement (or still contains `pass`). |

</details>

---

## Part A - In-Class Lab [30% of Lab Marks]

Complete all assigned in-class tasks during your scheduled lab.

**Part A Marking (3 marks):**

| Task | Marks |
|---|---|
| Task 1 - Using a Class | 1.0 |
| Task 2 - Completing a Method | 1.0 |
| Task 3 - Adding undo() to CashRegister | 1.0 |
| **Total** | **3** |

- Complete Part A in VS Code, in your `Lab08` folder (see [Setting Up](#setting-up-one-folder-for-the-whole-lab)).
- Demonstrate your completed work to the professor before leaving the lab.
- The professor may ask you to explain portions of your code.
- No submission is required for Part A. Keep the files in `Lab08`: Part B uses `cashregister.py` from Task 3.

<details markdown="1">

<summary><b>Quick Reference: Classes and Objects</b></summary>

<br>

A **class** is defined with the keyword `class`. Class names start with an upper-case letter, with an upper-case letter for each new word (`TallyCounter`, `CashRegister`).

```python
class TallyCounter:
    def __init__(self):             # the constructor
        self._value = 0             # an instance variable

    def click(self):                # a method
        self._value = self._value + 1

    def getValue(self):
        return self._value
```

| Word | Meaning |
|---|---|
| **constructor** `__init__` | A special method that runs automatically every time a new object is created. It creates the instance variables. |
| **`self`** | The first parameter of every method. It is the object the method is working on. |
| **instance variable** | A variable that belongs to one object, written `self._name`. Every object has its own copy. |
| **`_` (underscore)** | Means "do not use this variable from outside the class". Use the methods instead. |

**Using a class from another file** (if the class above were saved in `tallycounter.py`):

| Code | Meaning |
|---|---|
| `from tallycounter import TallyCounter` | Import the class `TallyCounter` from the file `tallycounter.py` (no `.py` in the import) |
| `tally1 = TallyCounter()` | Create an object. This runs `__init__` automatically. Any arguments you write in the brackets are passed to `__init__` (you never pass `self`). |
| `tally1.click()` | Call a method on the object: object name, dot, method name, brackets |
| `print(tally1.getValue())` | Print the value that the method **returns** |

</details>

### Task 1 - Using a Class

**Objective:** Practice creating objects from a class that is already written and calling their methods.

**Instructions:**

- Create a file named `dog.py` and add the required comment header. Copy the following class into your file, below the comment header. This class is complete: do not change it, but read the comments carefully. Note how the constructor stores the name and breed in instance variables, and how each method uses them through `self`.

  ```python
  class Dog:
      # __init__ is the constructor. It runs automatically every time
      # a new Dog object is created, for example: Dog("Buddy", "Golden Retriever")
      def __init__(self, name, breed):
          # self is the object being created.
          # self._name and self._breed are instance variables:
          # every Dog object gets its own copy of them.
          self._name = name
          self._breed = breed

      def bark(self):
          # A method can use the object's instance variables through self.
          return self._name + " says woof!"

      def getName(self):
          return self._name

      def getBreed(self):
          return self._breed
  ```

- Create a file named `task1.py` (the **tester** for the `Dog` class) and add the required comment header. Copy the following starter code into your file, below the comment header. The first dog is done for you as an example:

  ```python
  from dog import Dog


  def main():
      dog1 = Dog("Buddy", "Golden Retriever")     # done for you: creates a Dog object
      print(dog1.bark())                          # done for you: calls the bark() method

      # 1. Create a second Dog object named "Luna" of breed "Husky", and store it in dog2
      # 2. Print what dog2 says (call bark() on dog2)
      # 3. Print the name and breed of dog2 like this: Luna is a Husky
      #    (call getName() and getBreed() on dog2)


  main()
  ```

- Complete `main()` by following the numbered comments.
- Run your script with `python task1.py` and verify the output.

**Expected Output:**

```text
Buddy says woof!
Luna says woof!
Luna is a Husky
```

> **Think about it:** `dog1` and `dog2` were made from the same class, but `dog1.bark()` and `dog2.bark()` print different names. Where is each dog's name stored? What would `print(dog1)` show instead, and why?

<details markdown="1">

<summary><b>Quick Reference: Writing a Method</b></summary>

<br>

A method is written like a function, with two differences: it is written **inside** the class, and its first parameter is **`self`**. Inside the method, use `self.` to read the object's instance variables:

```python
def getValue(self):
    return self._value          # self._value, not just _value
```

A method that gives back an answer must **`return`** it. A method without `return` gives back `None`.

</details>

### Task 2 - Completing a Method

**Objective:** Practice writing a method that uses the object's instance variables, and test the class from a separate file.

**Instructions:**

- Create a file named `cylinder.py` and add the required comment header. Copy the following starter code into your file, below the comment header. `getSurfaceArea()` is done for you as an example:

  ```python
  import math


  class Cylinder:
      def __init__(self, radius, height):
          self._radius = radius
          self._height = height

      def getRadius(self):
          return self._radius

      def getHeight(self):
          return self._height

      def getSurfaceArea(self):
          # done for you as an example
          # Surface area = 2 * pi * radius ** 2 + 2 * pi * radius * height
          top = math.pi * self._radius ** 2
          side = 2 * math.pi * self._radius * self._height
          return 2 * top + side

      def getVolume(self):
          # Volume = pi * radius ** 2 * height
          # 1. Calculate the volume with math.pi, self._radius and self._height,
          #    and store it in a variable named volume
          # 2. Return volume
          # (Delete the word pass below when you add your code.)
          pass
  ```

- Complete `getVolume()` by following the numbered comments. Use `getSurfaceArea()` as your example.
- Create a file named `task2.py` (the tester for the `Cylinder` class) and add the required comment header. Copy the following starter code into your file, below the comment header:

  ```python
  from cylinder import Cylinder


  def main():
      can = Cylinder(3, 10)                                       # done for you: radius 3, height 10
      print("Can radius:", can.getRadius(), "height:", can.getHeight())   # done for you
      print("Can surface area:", round(can.getSurfaceArea(), 2))  # done for you

      # 1. Print "Can volume:" and the volume of can, rounded to 2 decimal places
      # 2. Create a second Cylinder with radius 1 and height 5, and store it in pipe
      # 3. Print "Pipe volume:" and the volume of pipe, rounded to 2 decimal places


  main()
  ```

- Complete `main()` by following the numbered comments.
- Run your script with `python task2.py` and verify the output.

**Expected Output:**

```text
Can radius: 3 height: 10
Can surface area: 245.04
Can volume: 282.74
Pipe volume: 15.71
```

> **Think about it:** `getVolume()` has only one parameter, `self`, but it still knows the radius and height. How? When you call `pipe.getVolume()`, what is `self`?

### Task 3 - Adding undo() to CashRegister

**Objective:** Practice extending an existing class with a new instance variable and a new method, and test it by comparing actual and expected results.

In the Week 11 slides, we wrote a `CashRegister` class that can add items and work out the total. Now the cashier needs an `undo()` method that removes the most recently added item, to quickly correct a mistake. To know **which** price to remove, the register must remember every price it was given, so you will add a list of prices to the class.

**Instructions:**

- Create a file named `cashregister.py` and add the required comment header. Copy the following starter code into your file, below the comment header. It is the `CashRegister` class from the slides with some new numbered comments:

  ```python
  class CashRegister:
      def __init__(self):
          self._itemCount = 0
          self._totalPrice = 0.0
          # 1. Add an instance variable named _prices that starts as an empty list

      def addItem(self, price):
          self._itemCount = self._itemCount + 1
          self._totalPrice = self._totalPrice + price
          # 2. Add price to the end of the _prices list (use append())

      def getTotal(self):
          return self._totalPrice

      def getCount(self):
          return self._itemCount

      def clear(self):
          self._itemCount = 0
          self._totalPrice = 0.0
          # 3. Make the _prices list empty again

      def undo(self):
          # Removes the most recently added item.
          # 4. If the _prices list is empty (its len() is 0), print "Nothing to undo" and return
          # 5. Otherwise, remove the last price from the list with pop() and store it in lastPrice
          # 6. Subtract lastPrice from _totalPrice, and subtract 1 from _itemCount
          # (Delete the word pass below when you add your code.)
          pass
  ```

- Complete the class by following the numbered comments. Note step 3: `clear()` must also empty the list, or `undo()` would remove a price that was already cleared.
- Create a file named `task3.py` (the tester for `CashRegister`) and add the required comment header. Copy the following starter code into your file, below the comment header:

  ```python
  from cashregister import CashRegister


  def main():
      register1 = CashRegister()
      register1.addItem(1.95)                     # done for you
      # 1. Add three more items to register1: 2.50, 4.25 and 3.00

      print("Count:", register1.getCount(), "Expected: 4")                   # done for you
      print("Total:", round(register1.getTotal(), 2), "Expected: 11.7")      # done for you

      # 2. Call undo() on register1 two times
      # 3. Print the count and total again, like above. The expected values are now 2 and 4.45
      # 4. Call clear() on register1, then print the count (expected: 0)
      # 5. Call undo() on register1 one more time. It should print "Nothing to undo"


  main()
  ```

- Complete `main()` by following the numbered comments.
- Run your script with `python task3.py`. On every line, the actual value must match the expected value.

**Expected Output:**

```text
Count: 4 Expected: 4
Total: 11.7 Expected: 11.7
Count: 2 Expected: 2
Total: 4.45 Expected: 4.45
Count: 0 Expected: 0
Nothing to undo
```

> **Think about it:** Printing the actual value next to the expected value is how the slides test a class ("unit testing"). If a line did not match, how would it help you find the mistake?

---

## Part B - Take-Home Lab [70% of Lab Marks]

Complete the following tasks independently after the scheduled lab using VS Code, in the same `Lab08` folder as Part A.

**Part B Marking (7 marks):**

| Task | Marks |
|---|---|
| Task 4 - Many Objects and Object References | 2.0 |
| Task 5 - A Class Variable for the Tax Rate | 2.0 |
| Task 6 - Printing a Receipt with a List of Tuples | 3.0 |
| Submission requirements (exact repo, folder and file names, comment headers, code pushed to GitHub) | up to 100% deduction may apply |
| **Total** | **7** |

> Marks are awarded only when the required classes, methods and variables are used as instructed. Correct output alone is not enough.

**Before You Begin:**

- Make sure your Part A files are in `SRT111F2026/Lab08`. Tasks 4 and 5 use your `cashregister.py` from Task 3, so it must have a working `undo()`.
- Use these file names **exactly**, all in lower case: `task4.py`, `task5.py`, `itemregister.py`, `task6.py`.

**For each task:**

- Run the tester from the `Lab08` folder using the VS Code terminal and compare your output with the expected output.
- Each tester asks you to answer a question in a **comment** at the bottom of the file. These answers are marked, so do not skip them.
- No screenshots or PDF are required for this lab. Your code in GitHub is your submission.

<details markdown="1">

<summary><b>Quick Reference: Many Objects and Object References</b></summary>

<br>

Every call to the constructor makes a **new** object with its **own** instance variables:

```python
register1 = CashRegister()      # one object
register2 = CashRegister()      # a second, separate object
register1.addItem(1.95)         # changes register1 only
```

A variable does not hold the object itself. It holds a **reference**: where the object is stored in memory. `b = a` does **not** make a new object. It gives the **same** object a second name:

```python
reg1 = CashRegister()
reg2 = reg1                     # no new object is made!
reg2.addItem(5.00)
print(reg1.getCount())          # 1  (same object)
```

</details>

### Task 4 - Many Objects and Object References

**Objective:** Practice creating several objects of the same class, comparing their data, and seeing what happens when two variables refer to the same object.

**Instructions:**

- Create a file named `task4.py` and add the required comment header. Copy the following starter code into your file, below the comment header:

  ```python
  from cashregister import CashRegister


  def main():
      register1 = CashRegister()                  # done for you
      register1.addItem(3.50)
      register1.addItem(2.25)
      register1.addItem(10.00)

      # 1. Create a second CashRegister object, store it in register2,
      #    and add two items to it: 5.00 and 7.25

      print("Register 1 - items:", register1.getCount(), "total:", round(register1.getTotal(), 2))   # done for you
      # 2. Print register2 the same way, starting with "Register 2 - items:"
      # 3. Compare the totals of the two registers (use getTotal()) with if/elif/else, and print one of:
      #    "Register 1 collected more money"
      #    "Register 2 collected more money"
      #    "Both registers collected the same amount"

      print()
      print("--- References ---")
      register3 = register1                       # done for you: no new object is made!
      register3.addItem(1.00)                     # done for you
      # 4. Print register1 again, the same way as above


  main()

  # Reflection (answer in 2-4 sentences):
  # The program added an item to register3, but register1 changed. Explain why.
  # How would you change the line register3 = register1 to get a separate, empty register?
  ```

- Complete `main()` by following the numbered comments. Do not change the code that is done for you.
- At the **bottom** of `task4.py`, answer the reflection question in a comment of 2-4 sentences.
- Run your script with `python task4.py` and verify the output.

**Expected Output:**

```text
Register 1 - items: 3 total: 15.75
Register 2 - items: 2 total: 12.25
Register 1 collected more money

--- References ---
Register 1 - items: 4 total: 16.75
```

> **Think about it:** Change the items so that both registers have the same total, and run the script again. Does your program print the third message? Change them back before you submit.

<details markdown="1">

<summary><b>Quick Reference: Class Variables</b></summary>

<br>

An **instance variable** belongs to **one** object (`self._totalPrice`): every register has its own total. A **class variable** belongs to the **class**: there is only **one** copy, shared by all objects. It is defined inside the class but **outside** any method, usually at the top, and it is used with the **class name**:

```python
class BankAccount:
    lastAccNum = 1000               # a class variable

    def __init__(self):
        self._balance = 0           # an instance variable
        BankAccount.lastAccNum = BankAccount.lastAccNum + 1
        self._accountNumber = BankAccount.lastAccNum
```

</details>

### Task 5 - A Class Variable for the Tax Rate

**Objective:** Practice adding a class variable and a new method to an existing class, and see that a class variable is shared by all objects.

So far, `CashRegister` works out the total **without** tax. Every register in the store uses the same tax rate (13% HST in Ontario), so the rate should be stored **once**, in a class variable, not in every object.

**Instructions:**

- Open your `cashregister.py` from Task 3 and make the following changes. Do not remove anything from Task 3.
  1. Add a class variable `TAX_RATE = 0.13` inside the class, **above** `__init__` (outside any method).
  2. Add a new method `getTotalWithTax(self)` at the end of the class. It must:
     - work out the tax: `self._totalPrice` multiplied by `CashRegister.TAX_RATE`,
     - **return** `self._totalPrice` plus the tax.
  3. `getTotalWithTax()` must **not** change `_totalPrice`. It only calculates and returns a value.

  `getTotalWithTax()` is an ordinary method like `getTotal()`: its first parameter is `self`, and you call it on an object (`register1.getTotalWithTax()`). The only new thing is that it reads a class variable, using the class name.

- Create a file named `task5.py` and add the required comment header. Copy the following starter code into your file, below the comment header:

  ```python
  from cashregister import CashRegister


  def main():
      register1 = CashRegister()
      register1.addItem(20.00)
      register1.addItem(5.00)

      print("Tax rate:", CashRegister.TAX_RATE)                          # done for you
      print("Total before tax:", round(register1.getTotal(), 2))         # done for you
      # 1. Print "Total with tax:" and register1.getTotalWithTax(), rounded to 2 decimal places
      # 2. Print "Total before tax:" again, to show that getTotalWithTax() did not change the total

      # 3. Create a second CashRegister object, store it in register2, and add one item: 10.00
      # 4. Print "Register 2 with tax:" and the total with tax of register2, rounded to 2 decimal places

      print()
      print("--- Tax rate changed to 5% ---")
      CashRegister.TAX_RATE = 0.05                                       # done for you
      # 5. Print "Register 1 with tax:" and "Register 2 with tax:" again, rounded to 2 decimal places


  main()

  # Reflection (answer in 2-4 sentences):
  # TAX_RATE was changed only once, but the total with tax changed for BOTH registers. Why?
  # Why is the tax rate a class variable, while _totalPrice is an instance variable?
  ```

- Complete `main()` by following the numbered comments.
- At the **bottom** of `task5.py`, answer the reflection question in a comment of 2-4 sentences.
- Run your script with `python task5.py` and verify the output. Then run `python task3.py` and `python task4.py` again: they must still give the same output as before.

**Expected Output:**

```text
Tax rate: 0.13
Total before tax: 25.0
Total with tax: 28.25
Total before tax: 25.0
Register 2 with tax: 11.3

--- Tax rate changed to 5% ---
Register 1 with tax: 26.25
Register 2 with tax: 10.5
```

> **Think about it:** What would go wrong if the tax rate were an instance variable (`self._taxRate = 0.13` in `__init__`) and the government changed the rate?

<details markdown="1">

<summary><b>Quick Reference: A List of Tuples and Formatted Output</b></summary>

<br>

A **tuple** groups a few values together, for example a name and a price: `("Apple", 2.5)`. A list can hold many tuples:

```python
items = []
items.append(("Apple", 2.5))        # note the two sets of brackets
items.append(("Bread", 3.0))
```

A `for` loop can take each tuple apart into two variables:

```python
for name, price in items:
    print(name, price)
```

**Lining up columns.** In an f-string, a number after `:` sets the width of the column. `<` lines the text up on the left and `>` on the right. `.2f` shows a number with 2 decimal places:

| Code | Result (dots show the spaces) |
|---|---|
| `f"{'Apple':<12}"` | `Apple.......` (12 characters, text on the left) |
| `f"{2.5:>8.2f}"` | `....2.50` (8 characters, number on the right, 2 decimals) |
| `"-" * 20` | `--------------------` (20 dashes) |

</details>

### Task 6 - Printing a Receipt with a List of Tuples

**Objective:** Practice storing data in a list of tuples inside a class, working out values from that list, and printing a formatted receipt.

`CashRegister` only keeps a running total and a count. That is not enough to print a receipt that shows the **name** and **price** of every item. In this task, you will complete a new class, `ItemRegister`, that stores every item as a `(name, price)` tuple in a list. Its `addItem()` method takes two parameters, a name and a price.

`ItemRegister` is a **new** class in a **new** file, so your `CashRegister` and Tasks 3 to 5 keep working without changes.

**Instructions:**

- Create a file named `itemregister.py` and add the required comment header. Copy the following starter code into your file, below the comment header. The constructor and `addItem()` are done for you:

  ```python
  class ItemRegister:
      def __init__(self):
          # done for you: one list that holds a (name, price) tuple for every item
          self._items = []

      def addItem(self, name, price):
          # done for you: adds one tuple, for example ("Apple", 2.5), to the list
          self._items.append((name, price))

      def getCount(self):
          # 1. Return the number of items in the _items list (use len())
          # (Delete the word pass below when you add your code.)
          pass

      def getTotal(self):
          # 2. Add up the prices of all items and return the total:
          #    - start with total = 0.0
          #    - loop over the list with:   for name, price in self._items:
          #    - inside the loop, add price to total
          #    - after the loop, return total
          # (Delete the word pass below when you add your code.)
          pass

      def printReceipt(self):
          print("RECEIPT")                        # done for you
          total = 0.0                             # done for you
          # 3. Loop over the list with:   for name, price in self._items:
          #    inside the loop, print each item with:   print(f"{name:<12}{price:>8.2f}")
          #    and add price to total
          # 4. Print a line of 20 dashes:   print("-" * 20)
          # 5. Print the number of items:   print("Items:", len(self._items))
          # 6. Print the total:   print(f"{'Total:':<12}{total:>8.2f}")
          # (Delete the word pass below when you add your code.)
          pass
  ```

- Complete `getCount()`, `getTotal()` and `printReceipt()` by following the numbered comments. `getTotal()` must work out the total from the list each time it is called (there is no `_totalPrice` variable in this class).
- Create a file named `task6.py` (the tester for `ItemRegister`) and add the required comment header. Copy the following starter code into your file, below the comment header:

  ```python
  from itemregister import ItemRegister


  def main():
      register1 = ItemRegister()
      register1.addItem("Apple", 2.50)            # done for you
      # 1. Add two more items to register1: "Bread" for 3.00 and "Milk" for 4.20

      # 2. Print the count and the total, with the expected values, like Task 3:
      #    Count: 3 Expected: 3
      #    Total: 9.7 Expected: 9.7
      #    (round the total to 2 decimal places)

      print()
      # 3. Call printReceipt() on register1


  main()

  # Reflection (answer in 2-4 sentences):
  # CashRegister keeps a running total in _totalPrice, while ItemRegister works out the total
  # from its list of items. Code that calls getTotal() works the same way with both classes.
  # Which idea from the Week 11 slides explains this? Which class would make undo() easier to write, and why?
  ```

- Complete `main()` by following the numbered comments.
- At the **bottom** of `task6.py`, answer the reflection question in a comment of 2-4 sentences.
- Run your script with `python task6.py` and verify the output. The receipt must match **exactly**, including the spaces.

**Expected Output:**

```text
Count: 3 Expected: 3
Total: 9.7 Expected: 9.7

RECEIPT
Apple           2.50
Bread           3.00
Milk            4.20
--------------------
Items: 3
Total:          9.70
```

> **Think about it:** Add a fourth item with a long name, such as `"Orange Juice 2L"`, and run the script again. What happens to the receipt, and which number in the f-string would you change to fix it? Remove the item before you submit.

## Part B Submission

Part B is graded **directly from your GitHub repository**. The structure below must match **exactly**, including upper and lower case. A file with the wrong name or in the wrong folder is treated as missing.

```text
SRT111F2026/                   <- your repository, with exactly this name
└── Lab08/                     <- capital L, zero, eight
    ├── dog.py                 <- Part A, Task 1
    ├── task1.py               <- Part A, Task 1
    ├── cylinder.py            <- Part A, Task 2
    ├── task2.py               <- Part A, Task 2
    ├── cashregister.py        <- Task 3, with TAX_RATE and getTotalWithTax() from Task 5
    ├── task3.py               <- Part A, Task 3
    ├── task4.py
    ├── task5.py
    ├── itemregister.py        <- Task 6
    └── task6.py
```

- Do **not** rename the repository, and do not put the files in a sub-folder of `Lab08` or at the top level of the repository.
- Part B needs `cashregister.py` from Part A, so push **all** ten files. Part A files are graded in class and do not change your Part B grade, but Tasks 4 and 5 cannot run without `cashregister.py`.
- Commit and push the `Lab08` folder to GitHub. Open your repository on github.com in a browser and confirm that all ten files are inside `Lab08`.
- On Blackboard, submit **only the link** to your repository, for example: `https://github.com/yourgithubusername/SRT111F2026`
- No screenshots and no PDF are required.

### Part B Grading Checklist

Your repository will be checked against the following list. Use it to check your own work before you submit.

| # | Check |
|---|---|
| 1 | The repository is named `SRT111F2026` and contains a folder named `Lab08`. |
| 2 | `Lab08` contains the ten files with the exact names shown above. |
| 3 | Every `.py` file starts with the required comment header (Author, Date, Purpose). |
| 4 | Every tester (`task4.py` to `task6.py`) has a `main()` function, calls `main()`, runs from the `Lab08` folder without errors and prints the expected output. |
| 5 | `cashregister.py` still has a working `undo()` and `clear()` from Task 3, and `task3.py` still prints its expected output. |
| 6 | Task 4 creates two separate `CashRegister` objects, compares their totals in `main()` with `getTotal()` and `if`/`elif`/`else`, and has the reflection comment at the bottom. |
| 7 | Task 5 adds the class variable `TAX_RATE = 0.13` outside any method, and `getTotalWithTax()` uses `self._totalPrice` and `CashRegister.TAX_RATE`, returns the total with tax and does not change `_totalPrice`. `task5.py` has the reflection comment at the bottom. |
| 8 | Task 6 completes `getCount()` with `len()`, `getTotal()` with a loop over the list of tuples, and `printReceipt()` (which adds up its own total in the loop) with the exact layout. `task6.py` has the reflection comment at the bottom. |
| 9 | The repository link was submitted on Blackboard. |

> **Deductions:** Marks are deducted for **every** missing comment header (Author, Date, Purpose), incorrect file or folder name, file in the wrong place, and missing reflection comment. Serious problems, such as a repository that cannot be found or code that was not pushed, can lead to a deduction of up to 100% of Part B.
