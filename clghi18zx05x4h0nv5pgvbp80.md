---
title: "Top 10 Python best practices"
datePublished: Sat Apr 15 2023 04:49:39 GMT+0000 (Coordinated Universal Time)
cuid: clghi18zx05x4h0nv5pgvbp80
slug: top-10-python-best-practices
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1679322078221/7871fa6c-2202-433f-9e58-4f885ca9d006.png
tags: python, styleguide, best-practices, code-quality, python-beginner

---

1. **Follow PEP 8 style guide:** PEP 8 is the official style guide for Python code. Following PEP 8 can make your code more readable and easier to maintain.
    
    ```python
    # Good
    def calculate_area(radius):
        """
        Calculates the area of a circle with given radius.
        """
        return 3.14 * radius ** 2
    
    # Bad
    def calculateArea(r):
        return 3.14 * r ** 2
    ```
    
2. **Use descriptive names:** Use descriptive and meaningful names for variables, functions, classes, and modules. This makes your code more understandable to others.
    
    ```python
    # Good
    def calculate_salary(employee):
        """
        Calculates the salary for the given employee.
        """
        hourly_rate = employee.hourly_rate
        hours_worked = employee.hours_worked
        salary = hourly_rate * hours_worked
        return salary
    
    # Bad
    def calc(employee):
        hr = employee.hr
        hw = employee.hw
        sal = hr * hw
        return sal
    ```
    
3. **Write docstrings:** Write docstrings for all functions, classes, and modules. Docstrings describe what the code does and how to use it.
    
    ```python
    # Good
    def find_largest_number(numbers):
        """
        Returns the largest number from a list of numbers.
    
        Args:
        numbers: list of integers
    
        Returns:
        largest number in the list
        """
        return max(numbers)
    
    # Bad
    def largest(numbers):
        return max(numbers)
    ```
    
4. **Avoid global variables:** Avoid using global variables as they can cause unexpected behaviour and make your code harder to understand and test.
    
    ```python
    # Good
    def calculate_tax(amount):
        tax_rate = 0.10
        tax = amount * tax_rate
        return tax
    
    # Bad
    tax_rate = 0.10
    
    def calculate_tax(amount):
        tax = amount * tax_rate
        return tax
    ```
    
5. **Use list comprehensions**: Use list comprehensions instead of loops to create lists. List comprehensions are more concise and readable.
    
    ```python
    # Good
    numbers = [1, 2, 3, 4, 5]
    squares = [num ** 2 for num in numbers]
    
    # Bad
    numbers = [1, 2, 3, 4, 5]
    squares = []
    for num in numbers:
        squares.append(num ** 2)
    ```
    
6. **Use context managers:** Use context managers to properly manage resources such as files, sockets, and database connections.
    
    ```python
    # Good
    with open('file.txt', 'r') as f:
        data = f.read()
        # do something with data
    
    # Bad
    f = open('file.txt', 'r')
    data = f.read()
    # do something with data
    f.close()
    ```
    
7. **Avoid unnecessary complexity:** Keep your code simple and easy to understand. Avoid unnecessary complexity and don't over-engineer solutions.
    
    ```python
    # Good
    def calculate_average(numbers):
        return sum(numbers) / len(numbers)
    
    # Bad
    def calculate_average(numbers):
        total = 0
        for num in numbers:
            total += num
        average = total / len(numbers)
        return average
    ```
    
8. **Write unit tests:** Write unit tests for your code to ensure that it works as expected and to catch any bugs or errors early.
    
    ```python
    # Good
    def test_calculate_area():
        assert calculate_area(5) == 78.5
        assert calculate_area(0) == 0
        assert calculate_area(-5) == 78.5
    
    # Bad
    def calculate_area(radius):
        return 3.14 * radius ** 2
    ```
    
9. **Use virtual environments:** Use virtual environments to isolate your Python environment and avoid dependency conflicts.
    
    ```python
    # Good
    $ python3 -m venv venv
    $ source venv/bin/activate
    (myenv) $ pip install requests
    
    # Bad
    $ pip install requests
    ```
    
10. **Optimize code:** Optimize your code for speed and efficiency. This includes using built-in functions and libraries, avoiding unnecessary computation, and using appropriate data structures.
    
    ```python
    # Good
    def sum_squares(numbers):
        return sum(num**2 for num in numbers)
    
    # Bad
    def sum_squares(numbers):
        squares = [num**2 for num in numbers]
        return sum(squares)
    ```
    
    *In the above example, the good code uses a generator expression to compute the squares of the numbers and sum them up in a single step, while the bad code first creates a list of squares and then sums them up. The good code is more efficient as it avoids creating an unnecessary list in memory.*