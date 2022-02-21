---
layout: plain
title:  Polypheny Connector for Python
---

The Polypheny Connector for Python provides an interface for developing Python applications that can connect to Polypheny-DB and perform all standard operations. It provides a programming alternative to developing applications in Java using the Polypheny JDBC driver.

The connector is a native, pure Python package that has no dependencies on JDBC or ODBC. It can be installed using pip on Linux, macOS, and Windows platforms where Python 3.6 and higher is installed.

The connector supports developing applications using the Python Database API v2 specification ([PEP-249](https://www.python.org/dev/peps/pep-0249/)), including using the following standard API objects:
* Connection objects for connecting to Polypheny-DB.
* Cursor objects for executing DDL/DML statements and queries, that are compliant with [*PolySQL*](https://polypheny.org/documentation/PolySQL/).

The connector establishes access to Polypheny-DBs via the *Avatica general purpose interface*.

For information about changes in the latest version of the Polypheny Connector for Python, see the 
[Release Notes](https://github.com/polypheny/Polypheny-Connector-Python/blob/master/CHANGELOG.md) (GitHub)
{:.message}

* **[Installation]** --- Installing the Python Connector.
* **[Getting Started]** --- Using the Python Connector.


[Installation]: Installation.md
[Getting Started]: GettingStarted.md
