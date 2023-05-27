---
title: "What is an ORM?"
datePublished: Sat May 27 2023 04:46:39 GMT+0000 (Coordinated Universal Time)
cuid: cli5if5su01ugbwnv13b5ev12
slug: what-is-an-orm
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1683217911297/d7f13152-48d8-442e-8ec5-fcc250c18bf6.png
tags: python, databases, orm, sqlalchemy, orm-object-relational-mapping

---

### Introduction

ORM stands for Object-Relational Mapping. It is a programming technique that enables developers to access and manipulate data in a database using an object-oriented programming language. In other words, it's a way to map database tables to classes in an object-oriented programming language like Python, Java, or C#.

ORMs provide an abstraction layer between the application and the database, making it easier for developers to interact with the database without needing to write complex SQL queries. ORMs handle the conversion between the object-oriented data used in the application and the relational data stored in the database.

Some popular ORMs include SQLAlchemy for Python, Hibernate for Java, and Entity Framework for C#. ORMs can help developers to write more maintainable and scalable applications by reducing the amount of boilerplate code required to interact with databases.

### A simpler explaination

Imagine you have a lot of toys, and you want to keep them organized so that you can find them easily when you want to play. So you put each toy in a box and write its name on the box. Now, when you want to play with a particular toy, you can simply look for its box, and you will find it easily.

Similarly, when we want to store and organize data (like names, ages, and addresses of people) on a computer, we use something called a database. The database is like a big box where we can store lots of information, but it's not very easy for us to find the information we need because it's not organized like our toy boxes.

That's where ORM comes in. ORM helps us to organize the information in the database in a way that is easier for us to understand and work with, just like the toy boxes. So when we want to find a particular piece of information (like the name of a person), we can just look for it in the ORM, and we will find it easily.

### ORM(s) in Python eco-system

There are several popular ORMs (Object-Relational Mapping) in Python. Some of them are:

1. [**SQLAlchemy**](https://github.com/sqlalchemy/sqlalchemy): It's a full-featured ORM that supports multiple database backends, including PostgreSQL, MySQL, Oracle, and SQLite. SQLAlchemy provides a high-level SQL expression language and a powerful object-relational mapper.
    
2. Django ORM: It's the default ORM provided by the Django web framework. The Django ORM is easy to use and provides a lot of features out of the box, like automatic table creation, query construction, and transaction management.
    
3. [**Peewee**](https://github.com/coleifer/peewee): It's a lightweight ORM that supports SQLite, MySQL, and PostgreSQL. Peewee has a simple and intuitive syntax and provides features like query building, schema migrations, and connection pooling.
    
4. [**Pony ORM**](https://github.com/ponyorm/pony): It's a fast and lightweight ORM that supports SQLite, MySQL, PostgreSQL, and Oracle. Pony ORM provides an intuitive and Pythonic syntax and supports advanced features like entity relationships, schema migrations, and database introspection.
    
5. [**Tortoise ORM**](https://github.com/tortoise/tortoise-orm): It's an easy-to-use ORM that supports PostgreSQL, MySQL, SQLite, and MariaDB. Tortoise ORM provides an intuitive syntax and supports features like query building, schema migrations, and connection pooling.
    
6. [**Databases**](https://github.com/encode/databases): Databases gives you simple asyncio support for a range of databases. It allows you to make queries using the powerful [SQLAlchemy Core](https://docs.sqlalchemy.org/en/latest/core/) expression language, and provides support for PostgreSQL, MySQL, and SQLite.
    

These are just a few examples, and there are many other ORMs available in Python, each with their own strengths and weaknesses.

### SQL Alchemy Example

```python
# example_db_operations.py
from sqlalchemy import create_engine, Column, Integer, String
from sqlalchemy.orm import sessionmaker
from sqlalchemy.ext.declarative import declarative_base

# create an engine to connect to a database
engine = create_engine('sqlite:///example.db')
# create a session factory
Session = sessionmaker(bind=engine)
# create a base class for declarative models
Base = declarative_base()

# define a model class for a table
class Person(Base):
    __tablename__ = 'people'
    id = Column(Integer, primary_key=True)
    name = Column(String)
    age = Column(Integer)

# create the table in the database
Base.metadata.create_all(engine)

# create a session to interact with the database
session = Session()

# add a new person to the table
person = Person(name='Nikhil', age=25)
session.add(person)
session.commit()

# retrieve all people from the table
people = session.query(Person).all()
for person in people:
    print(person.name, person.age)

# close the session
session.close()
```

*In the above example, we first create an engine object that connects to an SQLite database. We then create a session factory and a base class for declarative models using SQLAlchemy's ORM. We define a* `Person` *class that maps to a* `people` *table in the database, with columns for* `id`*,* `name`*, and* `age`*. We use the* `metadata` *attribute of the base class to create the table in the database.*

*We then create a session object to interact with the database and add a new person to the table using* `session.add()`*. We commit the changes to the database using* `session.commit()`*. We retrieve all people from the table using* `session.query(Person).all()` *and print their names and ages.*

*Finally, we close the session object to release any resources it was using.*

### Takeway

In conclusion, ORMs provide a powerful tool for developers to work with databases in a more intuitive and productive way. By mapping database tables to classes in an object-oriented programming language, developers can work with data in a more natural way, using objects and methods rather than complex SQL queries. This not only simplifies the code but also reduces the amount of boilerplate code that needs to be written. Popular ORMs like SQLAlchemy, Django ORM, Peewee, Pony ORM, and Tortoise ORM provide a wide range of features and support multiple database backends, making them an essential tool for developers working on database-driven applications.

### Source code

%[https://github.com/nikhilakki/nikhilakki.in-blog-code-examples/tree/main/sqlalchemy101]