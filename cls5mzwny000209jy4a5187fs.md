---
title: "How to migrate SQL db data in Django?"
datePublished: Sat Feb 03 2024 05:31:49 GMT+0000 (Coordinated Universal Time)
cuid: cls5mzwny000209jy4a5187fs
slug: how-to-migrate-sql-db-data-in-django
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1706170635353/35f932b3-0b88-4d0e-9ec9-2034432f3db4.png
tags: postgresql, python, django, sql, django-rest-framework, django-orm, migrations, azure-postgresql

---

I recently had a task at hand to migrate from a on VM PostgreSQL DB instance to [Azure PostgreSQL Flexible server](https://learn.microsoft.com/en-us/azure/postgresql/) (*a cloud native managed PostgreSQL server*). We use docker compose for service orchestration for local development due to its easy of use and we ended up with same setup on a VM as well. Now the app is scaling up so I decided to move to a managed SQL instance (Azure PostgreSQL flex servers in this case).

Below are some of the key differences with various aspects between the two approaches -

| **Aspect** | **Managed PostgreSQL Instance** | **PostgreSQL in Docker Compose** |
| --- | --- | --- |
| **Ease of Management** | \- Automated routine tasks (backups, updates) | \- Requires manual management |
| **Automatic Scaling** | \- Built-in scaling features | \- Manual scaling based on Docker configurations |
| **High Availability** | \- Built-in configurations for high availability | \- Configuration required for high availability |
| **Security** | \- Often includes encryption at rest/in transit | \- Requires manual implementation of security features |
| **SLA (Service Level Agreements)** | \- Provider offers SLAs | \- No SLAs; depends on self-managed infrastructure |
| **Portability** | \- Less portable due to service dependencies | \- Highly portable across different environments |
| **Development and Testing** | \- May be less suitable for local development | \- Excellent for local development and testing |
| **Custom Configurations** | \- Limited control over configurations | \- Full control over PostgreSQL configurations |
| **Cost Control** | \- Costs associated with the service provider | \- More control over infrastructure costs |
| **Learning and Control** | \- Higher abstraction; less control over internals | \- Deeper understanding and control of PostgreSQL |

### Now the important stuff, read on -

[Django](https://www.djangoproject.com/) provides a utility called `dumpdata` to export data from one database and `loaddata` to import data into another database. This can be useful when migrating data between PostgreSQL databases.

To export data from your source database, you can use the following command:

```python
python manage.py dumpdata > data_dump.json
```

This will create a JSON file (`data_dump.json`) containing serialized data for all installed apps.

To import this data into your destination database, you can use the following command:

```python
python manage.py loaddata data_dump.json
```

Make sure to run these commands with the appropriate environment and settings for your Django project. Additionally, keep in mind that this method assumes that the database schema is already in place in the destination database.

If you're working with multiple databases in your Django project, you may need to specify the database using the `--database` option. For example:

```python
python manage.py dumpdata --database=source_db > data_dump.json
python manage.py loaddata --database=destination_db data_dump.json
```

Replace `source_db` and `destination_db` with the aliases or names of your source and destination databases.

### Conclusion

This makes me realize how awesome [Django's mature eco-system](https://djangopackages.org/) is and has been through the test of time. If Django out of the box is old school for you, I recommend using [Django REST framework](https://www.django-rest-framework.org/) or the more new shiner framework - [Django-ninja](https://django-ninja.dev/). [Django's ORM](https://docs.djangoproject.com/en/5.0/topics/db/queries/) and [admin](https://docs.djangoproject.com/en/5.0/ref/contrib/admin/) console I like the most among other cool things that come with it.

Other articles on Django that I have covered in the past -

1. [Django REST Framework](https://nikhilakki.in/web-frameworks-in-python-django-rest-framework)
    
2. [Django](https://nikhilakki.in/web-frameworks-in-python-django)
    
3. [Intro to HTMX](https://nikhilakki.in/htmx-unleashing-the-power-of-dynamic-web-applications)
    
4. [Intro to Alpine JS](https://nikhilakki.in/alpinejs-a-lightweight-javascript-framework-that-packs-a-mountain-of-power)