---
layout: plain
title:  Installing the Python Connector
---

This topic provides instructions for installing the Polypheny Connector for Python. The connector can currently be installed in Linux, macOS, and Windows environments.

The developer notes are hosted on [GitHub](https://github.com/polypheny/Polypheny-Connector-Python), along with the source code.

* this unordered seed list will be replaced by toc as unordered list
{:toc}


## Prerequisites

The following software packages are required to install the Polypheny Connector for Python.

### Python

The Polypheny Connector for Python requires Python 3.6 or higher.

To verify your version of Python:
```bash
python --version
```

### Python Package Installer and Setup Tools

The Polypheny Connector for Python is installed by pip, a standard Python package installer and manager.

Use pip version 19.0 or later. Execute the following command to ensure the required version is installed:

```bash
python -m pip install --upgrade pip
```
If both Python 2.7.x and Python 3.x are installed, use pip3 to install the connector with Python 3.x.
{:.message}
Furthermore we **recommend** creating a virtual environment using [anaconda](https://www.anaconda.com/)
{:.message}


## Install the Connector

The Polypheny Connector for Python is available in [PyPI](https://pypi.org/project/polypheny/). A change log is available on the site, so you can determine the changes that have been implemented in each release.

1. Determine the version of the Polypheny Connector for Python that you plan to install.
2. To install the connector, run the following command:
```bash
pip install poylpheny==<version>
```
where version is the version of the connector that you want to install.

If you want the latest version of the Connector, simply execute:
```bash
pip install poylpheny
```

## Verify Your Installation
Create a file (e.g. validate.py) containing the following Python sample code, which connects to Polypheny and fetches some dummy information:
```python
#!/usr/bin/env python
import polypheny

# Connect to Polypheny
connection = polypheny.connect('<polypheny_host>', 20591, user='pa', password='')

# Get a cursor
cursor = connection.cursor()

# Execute a query
cursor.execute("SELECT * FROM emps")
result = cursor.fetchall()
print("Result Set: ", result)

# Close the connection
connection.close()
```

Before running the example:
* Replace <polypheny_host> with the DNS entry of your Polypheny-DB installation.
  * If you've installed Polypheny-DB locally, use `localhost.
* Replace `user` and `password` with the user name and password that you use to connect to Polypheny-DB.

Next, execute the sample code. For example, if you created a file named `validate.py`:
```bash
python validate.py
```

You should receive an output similar to this:
```
Result Set:  [[100, 10, 'Bill', 10000, 1000], [110, 10, 'Theodore', 11500, 250], [150, 20, 'Sebastian', 7000, 400], [200, 30, 'Eric', 8000, 500]]
```

**Congratulations you have connected your application to Polypheny-DB!**