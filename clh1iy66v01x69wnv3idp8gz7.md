---
title: "How to bundle your Python app as a pip package & upload to PyPi?"
datePublished: Sat Apr 29 2023 05:10:39 GMT+0000 (Coordinated Universal Time)
cuid: clh1iy66v01x69wnv3idp8gz7
slug: how-to-bundle-your-python-app-as-a-pip-package-upload-to-pypi
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1680805603909/9c100d2d-554e-4cba-b006-4203bb8b17bb.png
tags: python, pypi, pip-package, packaging-python-code, bundle-python-code

---

In this post, we are going to look at the Python tool called [Flit](https://flit.pypa.io/en/stable/) and we are going to publish our very own [Daily Jokes generator CLI app.](https://pypi.org/project/jokes_daily/)

Jokes Daily is a simple app using native Python std library *(and nothing else)* to fetch jokes from [*jokeapi.dev*](https://v2.jokeapi.dev).

### What is Flit?

Flit is a lightweight tool for building and publishing Python packages. Here's a step-by-step guide to package a Python app using Flit:

1. Create a new directory for your project and navigate into it.
    
2. An alternative approach to packaging a Python app with Flit is to use a `pyproject.toml` file. Here's how you can do it:
    
    1. Create a new directory for your project and navigate into it.
        
    2. Create a `pyproject.toml` file and add the following code:
        
    
    ```ini
    [tool.flit.metadata]
    module = "jokes_daily"
    author = "Nikhil Akki"
    description = "A CLI app for fetching Jokes from https://v2.jokeapi.dev"
    
    [tool.flit.scripts]
    jokes_daily = "jokes_daily.cli:main"
    ```
    
    This will define your package metadata, including the name, version, and author, as well as the package's entry point (the script that will be run when the package is invoked).
    
    1. Create a `__init__.py` file in your project directory and add any necessary code to initialize your app.
        
    2. Create a `__main__.py` file in your project directory and add the following code:
        
    
    ```python
    def main():
        # Add code here to execute when the script is run
    
    if __name__ == "__main__":
        main()
    ```
    
    This will define the entry point for your app.
    
    1. Install Flit by running `pip install flit`.
        
    2. Build your package by running `flit build`. This will create a distribute-able package in the `dist` directory.
        
    3. Test your package by installing it in a virtual environment. To do this, create a new virtual environment and activate it, then run `pip install /path/to/jokes_daily.X.Y.Z.tar.gz`, where `X.Y.Z` is the version of your package.
        
    4. Once you're satisfied that your package works correctly, you can publish it to PyPI by running `flit publish`. This will upload your package to PyPI, making it available for others to install and use. But before you can publish you have to setup a PyPi account. Steps are mentioned below for PyPi and Test PyPi repository.
        

### What is PyPi & Test PyPi?

PyPI (Python Package Index) is a centralized repository of Python packages that allows developers to find, share, and install Python packages. TestPyPI is a testing version of PyPI that provides a sandbox environment for developers to test their packages before uploading them to the production PyPI server. It ensures that packages are working as expected and compatible with PyPI infrastructure.

#### How to upload to PyPI?

To upload packages to PyPI, you need to authenticate yourself using an API token. Here are the steps to set up a PyPI token:

1. Log in to your PyPI account on the PyPI website ([https://pypi.org/](https://pypi.org/)).
    
2. Click on your username in the top right corner of the page, and select "Account settings" from the dropdown menu.
    
3. Scroll down to the "API token" section and click the "Add API token" button.
    
4. Enter a description for your token (for example, "My PyPI token for package uploads"), and click the "Create" button.
    
5. Your token will be displayed on the page. Make sure to copy it and store it in a secure place, as you won't be able to see it again.
    
6. To use your PyPI token with Flit, you can add it to your `~/.pypirc` file. If you don't have this file, you can create it by running `touch ~/.pypirc`. Then, open the file in a text editor and add the following lines:
    
7. ```ini
    [distutils]
    index-servers =
        pypi
    
    [pypi]
    username = __token__
    password = YOUR_TOKEN_HERE
    ```
    
    1. Replace `YOUR_TOKEN_HERE` with your actual PyPI token.
        
    2. Save the `~/.pypirc` file.
        
    
    Now you should be able to use Flit to upload packages to PyPI using your API token.
    
    #### How to upload to Test PyPi?
    
    If you want to upload packages to the TestPyPI server, you can set up a separate PyPI token for it. Here are the steps:
    
    1. Log in to your PyPI account on the PyPI website ([https://pypi.org/](https://pypi.org/)).
        
    2. Click on your username in the top right corner of the page, and select "Account settings" from the dropdown menu.
        
    3. Scroll down to the "API token" section and click the "Add API token" button.
        
    4. Enter a description for your token (for example, "My TestPyPI token for package uploads"), and select "TestPyPI" from the "Select a server" dropdown menu. Then click the "Create" button.
        
    5. Your token will be displayed on the page. Make sure to copy it and store it in a secure place, as you won't be able to see it again.
        
    6. To use your TestPyPI token with Flit, you can add it to your `~/.pypirc` file. If you don't have this file, you can create it by running `touch ~/.pypirc`. Then, open the file in a text editor and add the following lines:
        
    
    ```ini
    [distutils]
    index-servers =
        pypi
        testpypi
    
    [pypi]
    username = __token__
    password = YOUR_PYPI_TOKEN_HERE
    
    [testpypi]
    repository = https://test.pypi.org/legacy/
    username = __token__
    password = YOUR_TESTPYPI_TOKEN_HERE
    ```
    
    1. Replace `YOUR_TESTPYPI_TOKEN_HERE` with your actual TestPyPI token.
        
    2. Save the `~/.pypirc` file.
        
    
    Now you can use Flit to upload packages to TestPyPI by specifying the `--repository testpypi` option when running the `flit publish` command. For example:
    
    ```bash
    flit publish --repository testpypi
    ```
    
    This will upload your package to the TestPyPI server using the TestPyPI token you set up in the `~/.pypirc` file.
    

### Takeaway

In conclusion, Flit is a tool that simplifies the creation and distribution of Python packages, and PyPI is a centralized repository of Python packages that makes it easy for developers to share and install packages. Additionally, TestPyPI provides a sandbox environment for developers to test their packages before uploading them to the production PyPI server, ensuring package quality. By using Flit with PyPI and TestPyPI, developers can easily upload their packages to either server and make them available for others to use, which can help to improve the overall quality and productivity of the Python community.