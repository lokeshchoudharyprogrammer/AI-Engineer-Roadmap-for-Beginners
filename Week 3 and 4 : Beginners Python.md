# Week 3 and 4 : Beginners Python
Certainly! Let's delve deeper into each topic, explaining how they work with examples.

### Week 3: Modules, Files, Exception Handling

#### Day 1: Modules and Packages
- **Modules**: Modules in Python are simply Python files with a .py extension that contain Python code. These modules can define functions, classes, and variables, and can be imported into other modules or scripts to reuse code.

  - **Example**:
    ```python
    # math_module.py
    def square(x):
        return x * x
    ```

    ```python
    # main_script.py
    import math_module

    result = math_module.square(5)
    print(result)  # Output: 25
    ```

- **Packages**: Packages are a way of organizing related modules into a directory hierarchy. A package is a directory that contains a special file called `__init__.py`, which can also contain sub-packages or modules.

  - **Example**:
    ```
    my_package/
    ├── __init__.py
    ├── math/
    │   ├── __init__.py
    │   └── math_functions.py
    └── utils/
        ├── __init__.py
        └── utility_functions.py
    ```

#### Day 2: File Handling - Reading and Writing Files
- **File Modes**:
  - `r`: Read mode - Opens a file for reading. Raises an error if the file does not exist.
  - `w`: Write mode - Opens a file for writing. Creates a new file if it does not exist or truncates the file if it exists.
  - `a`: Append mode - Opens a file for appending. Creates a new file if it does not exist.
  - `r+`: Read and Write mode - Opens a file for reading and writing.

- **Using `with` Statement**: The `with` statement ensures proper file closure after usage. It's recommended for file handling in Python as it automatically handles exceptions and file closing.

  - **Example - Reading from a File**:
    ```python
    with open("data.txt", "r") as file:
        contents = file.read()
        print(contents)
    ```

  - **Example - Writing to a File**:
    ```python
    names = ["Alice", "Bob", "Charlie"]
    with open("names.txt", "w") as file:
        for name in names:
            file.write(name + "\n")
    ```

#### Day 3: Exception Handling
- **`try`, `except`, `finally`**: Exception handling in Python is done using `try`, `except`, and optionally `finally` blocks. It allows handling of errors and exceptions gracefully.

  - **Example**:
    ```python
    try:
        result = 10 / 0  # Raises ZeroDivisionError
    except ZeroDivisionError:
        print("Error: Division by zero")
    ```

  - **Catching Specific Exceptions**:
    ```python
    try:
        num = int("abc")  # Raises ValueError
    except ValueError:
        print("Error: Invalid conversion to integer")
    ```

- **Common Exceptions**:
  - `ZeroDivisionError`: Raised when division or modulo by zero is encountered.
  - `ValueError`: Raised when a function receives an argument of the correct type but with an invalid value.

#### Day 4: Classes and Objects
- **Classes**: Classes in Python allow you to create new types. They act as blueprints for creating objects, which are instances of a class. Classes can have attributes (variables) and methods (functions).

  - **Example**:
    ```python
    class Person:
        def __init__(self, name, age):
            self.name = name
            self.age = age

        def greet(self):
            print(f"Hello, my name is {self.name} and I am {self.age} years old.")

    person1 = Person("Alice", 30)
    person1.greet()  # Output: Hello, my name is Alice and I am 30 years old.
    ```

- **`__init__` Method**: The `__init__` method is a special method in Python classes that is called when a new object is created. It initializes the object's attributes.

- **Attributes and Methods**:
  - **Attributes**: Variables that belong to an object.
  - **Methods**: Functions that belong to an object.

#### Day 5: More on Classes - Inheritance and Special Methods
- **Inheritance**: Inheritance allows a new class (subclass) to inherit attributes and methods from an existing class (superclass). It helps in reusability and creates a hierarchy of classes.

  - **Example**:
    ```python
    class Vehicle:
        def __init__(self, brand, model):
            self.brand = brand
            self.model = model

        def details(self):
            print(f"Brand: {self.brand}, Model: {self.model}")

    class Car(Vehicle):
        def __init__(self, brand, model, color):
            super().__init__(brand, model)
            self.color = color

        def details(self):
            print(f"Brand: {self.brand}, Model: {self.model}, Color: {self.color}")

    vehicle1 = Vehicle("Toyota", "Camry")
    car1 = Car("Honda", "Civic", "Red")

    vehicle1.details()  # Output: Brand: Toyota, Model: Camry
    car1.details()      # Output: Brand: Honda, Model: Civic, Color: Red
    ```

- **Special Methods (`__init__`, `__str__`, etc.)**: These are predefined methods in Python classes with double underscores. They enable customizing the behavior of classes and objects.

  - **Example**:
    ```python
    class Point:
        def __init__(self, x, y):
            self.x = x
            self.y = y

        def __str__(self):
            return f"({self.x}, {self.y})"

    p1 = Point(1, 2)
    print(p1)  # Output: (1, 2)
    ```
learning resources can be used. Additionally, here are some further explanations and examples for the advanced topics:

### Week 4: Advanced Topics

#### Day 1: List Comprehensions and Generators

- **List Comprehensions**:
  - List comprehensions provide a concise and readable way to create lists in Python.
  - They follow the syntax: `[expression for item in iterable if condition]`.
  - This allows for filtering and transforming data in a single line.

  - **Example 1 - Squares of Numbers**:
    ```python
    # List Comprehension to create a list of squares
    squares = [x**2 for x in range(1, 11)]
    print(squares)  # Output: [1, 4, 9, 16, 25, 36, 49, 64, 81, 100]
    ```

  - **Example 2 - Filtered Comprehension**:
    ```python
    # List Comprehension with condition
    even_squares = [x**2 for x in range(1, 11) if x % 2 == 0]
    print(even_squares)  # Output: [4, 16, 36, 64, 100]
    ```

- **Generators**:
  - Generators are functions that enable you to create iterators in a more elegant and memory-efficient way.
  - They use the `yield` keyword to return data, and the state of the function is remembered between calls.

  - **Example - Fibonacci Generator**:
    ```python
    def fibonacci_generator():
        a, b = 0, 1
        while True:
            yield a
            a, b = b, a + b

    fib_gen = fibonacci_generator()
    fib_sequence = [next(fib_gen) for _ in range(10)]
    print(fib_sequence)  # Output: [0, 1, 1, 2, 3, 5, 8, 13, 21, 34]
    ```

  - **Explanation**:
    - The `fibonacci_generator` function creates an infinite sequence of Fibonacci numbers.
    - Each time `next(fib_gen)` is called, it yields the next Fibonacci number.
    - In the list comprehension, we call `next(fib_gen)` 10 times to get the first 10 Fibonacci numbers.

#### Day 2: Decorators and Context Managers

- **Decorators**:
  - Decorators are a powerful and flexible feature in Python used to modify or extend the behavior of functions or methods.
  - They are defined with the `@decorator_name` syntax and are placed above the function definition.

  - **Example - Simple Decorator**:
    ```python
    def my_decorator(func):
        def wrapper():
            print("Something is happening before the function is called.")
            func()
            print("Something is happening after the function is called.")
        return wrapper

    @my_decorator
    def say_hello():
        print("Hello!")

    say_hello()
    ```

  - **Explanation**:
    - The `my_decorator` function takes another function as an argument (`func`).
    - It defines a nested function `wrapper` that adds behavior before and after calling `func`.
    - The `@my_decorator` syntax is a shorthand for `say_hello = my_decorator(say_hello)`.
    - When `say_hello` is called, it runs the `wrapper` function, which executes additional code.

- **Context Managers**:
  - Context managers provide a way to manage resources such as files or database connections, ensuring they are properly cleaned up after usage.
  - They use the `with` statement and the `__enter__` and `__exit__` methods.

  - **Example - Using `with` Statement**:
    ```python
    with open("example.txt", "w") as file:
        file.write("Hello, this is an example.")

    # File automatically closed after exiting the block
    ```

  - **Custom Context Manager**:
    ```python
    class MyContextManager:
        def __enter__(self):
            print("Entering the context")
            return self

        def __exit__(self, exc_type, exc_value, traceback):
            print("Exiting the context")

        def do_something(self):
            print("Doing something in the context")

    with MyContextManager() as cm:
        cm.do_something()
    ```

  - **Explanation**:
    - When the `with` block is entered, the `__enter__` method is called, and it can set up resources.
    - The code inside the `with` block executes (`cm.do_something()` in this case).
    - When the block is exited, whether by completion or exception, the `__exit__` method is called to clean up resources.

#### Day 3: Regular Expressions (RegEx)

- **Regular Expressions**:
  - Regular expressions (regex or regexp) are sequences of characters that define a search pattern.
  - They are used for pattern matching within strings, allowing for powerful and flexible text processing.

  - **Example - Matching Email Addresses**:
    ```python
    import re

    pattern = r"[a-zA-Z0-9_.+-]+@[a-zA-Z0-9-]+\.[a-zA-Z0-9-.]+"
    text = "Contact us at email@example.com or support@company.co.uk"

    emails = re.findall(pattern, text)
    print(emails)  # Output: ['email@example.com', 'support@company.co.uk']
    ```

  - **Explanation**:
    - The `findall` function searches for all occurrences of the pattern in the given text.
    - The pattern `r"[a-zA-Z0-9_.+-]+@[a-zA-Z0-9-]+\.[a-zA-Z0-9-.]+"` matches typical email address formats.
    - It finds and returns a list of all email addresses in the text.

- **Common Regex Patterns**:
  - `.`: Matches any single character except newline.
  - `^`: Matches the start of a string.
  - `$`: Matches the end of a string.
  - `*`: Matches zero or more occurrences of the preceding character.
  - `+`: Matches one or more occurrences of the preceding character.
  - `\d`: Matches any decimal digit.
  - `\w`: Matches any alphanumeric character and underscore.
  - `\s`: Matches any whitespace character.

#### Day 4: Working with JSON and CSV Data

- **JSON (JavaScript Object Notation)**:
  - JSON is a lightweight data interchange format that is easy for humans to read and write, and easy for machines to parse and generate.
  - Python provides the `json` module for working with JSON data.

  - **Example - Reading and Writing JSON**:
    ```python
    import json

    # Writing JSON to a file
    data = {"name": "Alice", "age": 30}
    with open("data.json", "w") as json_file:
        json.dump(data, json_file)

    # Reading JSON from a file
    with open("data.json", "r") as json_file:
        loaded_data = json.load(json_file)
        print(loaded_data)  # Output

        : `{'name': 'Alice', 'age': 30}`

  - **Explanation**:
    - The `json.dump()` function writes Python data to a JSON file.
    - The `json.load()` function reads JSON data from a file and converts it into a Python dictionary.

- **CSV (Comma-Separated Values)**:
  - CSV is a simple file format used to store tabular data, such as a spreadsheet or database.
  - Python provides the `csv` module for reading and writing CSV files.

  - **Example - Reading and Writing CSV**:
    ```python
    import csv

    # Writing CSV data to a file
    with open('data.csv', mode='w', newline='') as csv_file:
        writer = csv.writer(csv_file)
        writer.writerow(['Name', 'Age'])
        writer.writerow(['Alice', 30])
        writer.writerow(['Bob', 25])

    # Reading CSV data from a file
    with open('data.csv', mode='r') as csv_file:
        reader = csv.reader(csv_file)
        for row in reader:
            print(row)
    ```

  - **Explanation**:
    - The `csv.writer()` and `csv.reader()` functions handle writing and reading CSV files respectively.
    - `writerow()` writes a single row to the CSV file.
    - When reading, each row is returned as a list of strings.

#### Day 5: Working with APIs (Application Programming Interfaces)

- **APIs (Application Programming Interfaces)**:
  - APIs allow different software applications to communicate with each other.
  - RESTful APIs are commonly used for web services, where data is exchanged in a structured format such as JSON.

  - **Example - Making API Requests with `requests`**:
    ```python
    import requests

    url = "https://api.example.com/data"
    response = requests.get(url)

    if response.status_code == 200:
        data = response.json()
        print(data)
    else:
        print("Error fetching data")
    ```

  - **Explanation**:
    - The `requests` library is commonly used for making HTTP requests to APIs.
    - `requests.get()` sends a GET request to the specified URL.
    - We check the response status code, and if it's 200 (OK), we parse the JSON data.

- **Authentication with APIs**:
  - Many APIs require authentication using tokens or API keys.
  - This can be done by including the authentication details in the request headers.

  - **Example - Authenticating with API Key**:
    ```python
    import requests

    url = "https://api.example.com/data"
    headers = {
        "Authorization": "Bearer YOUR_API_KEY"
    }

    response = requests.get(url, headers=headers)

    if response.status_code == 200:
        data = response.json()
        print(data)
    else:
        print("Error fetching data")
    ```

  - **Explanation**:
    - In this example, we include an API key in the request headers using the `"Authorization"` field.
    - This is a common method for authenticating API requests.

### Additional Resources:

- Python Official Documentation:
  - [Python Documentation](https://docs.python.org/3/)
  - [Python Standard Library - Built-in Modules](https://docs.python.org/3/library/index.html)

- Online Platforms for Practice:
  - [HackerRank Python Practice](https://www.hackerrank.com/domains/tutorials/10-days-of-python)
  - [LeetCode Python Problems](https://leetcode.com/problemset/all/?topicSlugs=array)

By following this weekly plan and practicing the provided examples and exercises, you'll build a solid foundation in Python programming. Remember to refer to the documentation and other resources for deeper understanding, and keep exploring new concepts as you progress. Happy coding!
