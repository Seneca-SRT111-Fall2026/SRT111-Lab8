# Lab 8
In this lab, you will create five Python scripts. All scripts must be written in GitHub Codespaces.<br>

In Python, everything is an object — numbers, strings, lists, dictionaries etc... <br>
Objects are created from classes, which are like blueprints describing how those objects behave and what data they store.

# Lab Objectives
- Understand what classes and objects are in Python
- To be able to use a pre-defined class by creating class objects and calling class methods.
- Create and use your own classes.
- Define attributes (variables) and methods (functions) inside a class
- Understand the instance variables, self parameter, and constructor function.
- Create and manipulate multiple objects from the same class
  
# Submission Instructions
For each task:
1. **Write the script** in Codespaces.  
2. **Run the script** from the **terminal**.  
3. **Take a screenshot** that clearly shows:  
   - Your **code** in the editor.  
   - The **terminal output**, including your **username** visible in the terminal.  
4. **Insert the screenshot** into a Word document under the heading that matches the task name:  
   - Example: **Lab8a**, **Lab8b**, **Lab8c**, etc.  
5. After completing all tasks, **convert the Word document to PDF**.  Name the PDF file using your **yoursenecausername.pdf**
6. **Submit the PDF file** as your final lab submission on Blackbaord.

  
## INVESTIGATION 1: CREATING A SIMPLE CLASS

In Python, a class is a blueprint for creating objects. It defines a set of attributes and methods that the objects created from the class can have. Here's a demonstration of creating a simple class :

A class is defined using the class keyword, followed by the class name and a colon.
```Python
class Dog:
    pass
```

Attributes are variables that belong to the class. These are usually defined in a special method called `__init__`. This method is called automatically when a new object is created from the class. The self parameter is a reference to the current instance/object of the class.
```Python
class Dog:
    def __init__(self, name, breed):
        self._name = name
        self._breed = breed
```

Methods are functions that belong to the class.
```Python
class Dog:
    def __init__(self, dog_name, dog_breed):
        self._name = name
        self._breed = breed

    def bark(self):
        return f"{self._name} says woof!"
```

You can create an object (an instance of a class) by calling the class name with the required arguments.
```Python
my_dog = Dog("Buddy", "Golden Retriever")
```

You can access class methods of an object using dot notation.
```Python
print(my_dog.bark())  # Output: Buddy says woof!
```

### lab7a - class Dog
**Objective:** Practice reading data from a text file in Python.  

### Creating class object and calling class method.
**Instructions:** Practice reading data from a text file in Python.  

- Review the code in the file dog.py. Understand the class definition and how instance variables have been created inside the constructor.
- Open the file dog_tester.py.
- The class dog has been imported.
- Create a new object of the `class Dog` inside `main()` function.
- Call the bark method for the object.
- Run the file using the command: `python ./dog_tester.py`.
- Take a clear screenshot of the `main()` from `dog_tester.py` and the output. Add this screenshot in the pdf.

## lab7b - class Cylinder
### Creating a class method, testing the class independently

- A class `Cylinder` has been created for you in the file `cylinder.py`
- Complete the `volume` method.
- Create a new file called `cylinder_tester.py`
- Add comments in `cylinder_tester.py` to explain the purpose of this file.
- Import `class Cylinder` in the `cylinder_tester.py`.
- Create the `main()` function.
- Create a class object.
- Call both class methods.
- Print the output.
- Run the script from command line using the command: `python ./cylinder_tester.py`.
- Take a clear screenshot of volume() method, `main()` form `cylinder_tester.py` and the output. Add this screenshot in the pdf.


## lab7c - class CashRegister
### Adding instance variable and class method in an existing class to extend the functionality

We did an example of implementing `CashRegister` class. Suppose the CashRegister needs to support a method undo() that undoes the addition of the preceding item. This enables a cashier to quickly undo a mistake. 

- Complete the undo function in `cashregister.py` according to the instructions given.
- Create a new file called `cashregister_tester.py`
- Add comments in `cashregister_tester.py` to explain the purpose of this file.
- Import `class CashRegister` in the `cashregister_tester.py`.
- Add main() function in the `cashregister_tester.py`.
- Test the undo functionality by creating an object of the class and calling the necessary methods inside main() and then calling the main().
- Run the script from command line using the command: `python ./cashregister_tester.py`.
- Take a clear screenshot of undo() method, main() from `cashregister_tester.py` and the output. Add this screenshot in the pdf.


## Lab 7 Sign-Off
- Submit the pdf including the  above mentioned screenshots.
- The screenshot must show your username on github codespaces.
- Make sure screenshots are readable.
- Name your file as: StudentFullName_PRG101_Lab7.pdf
