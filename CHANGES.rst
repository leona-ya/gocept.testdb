Changelog
=========

5.3 (unreleased)
----------------

- Restrict supported SQLALchemy to < 2.


5.2 (2021-04-26)
----------------

- Ensure compatibility with ``pytest > 6.0``.

- Add support for Python 3.9.

- Switch CI to GHA.

- Fix PostgreSQL ``drop_db`` to be able to forcibly drop a data base with open
  connections, even though there is no database with the same name as the user.


5.1 (2020-07-06)
----------------

- Forcibly close connections to test database before dropping, so this does not
  have to be done beforehand. (Ported from 4.x but missing in change log
  there.)

- Calculate a random database name that is random enough for parallel
  execution. (Ported from 4.2)


5.0 (2020-07-02)
----------------

Backwards incompatible changes
++++++++++++++++++++++++++++++

- *Caution:* This release is based on version 1.3 ignoring the changes made in
  the 4.x releases! At least some of those changes will be added later on.

- Drop support for Python 2.6 and Python 3.3 up to 3.5.

- Remove module ``gocept.testdb.db`` containing only imports for backwards
  compatibility, import now from ``gocept.testdb.mysql`` resp.
  ``gocept.testdb.postgres``.

Features
++++++++

- Officially support Python 3.6 up to 3.8.

- Add support to specify the port to connect to the database, thus the
  environment variables ``MYSQL_PORT`` and ``POSTGRES_PORT`` are taken into
  account. This eases using docker containers on custom ports.

Other changes
+++++++++++++

- Migrate code to Github.


1.3 (2015-10-07)
----------------

- Drop support of Python 3.2.

- Streamline documentation.


1.3a1 (2015-09-24)
------------------

- Officially support Python 3.2 up to Python 3.4.

- Switch PyMySQL driver to support Python 3 for MySQL.

- Add environment variable ``MYSQL_COMMAND_POSTFIX`` to use MySQL commands like
  `mysql5` instead of `mysql`.



1.2.1 (2013-09-03)
------------------

- Improve retry logic for dropping databases: ensure that db actually exists
  before trying to drop it (#12706).


1.2 (2013-06-21)
----------------

- Provisional compatibility to Python 3 (no compatible mysql driver exists yet,
  though).
- Fixed test code that made implicit assumptions about existing databases on
  the PostgreSQL server used or depended on timing conditions.


1.1.1 (2013-03-19)
------------------

- Use `template0` when changing `LC_COLLATE` which was introduced in v1.1.


1.1 (2013-03-19)
----------------

- Add possibility to set the `LC_COLLATE` when creating a database.


1.0 (2013-03-12)
----------------

- Allow a postfix for mysql-commands.


1.0b5 (2011-12-22)
------------------

- Use timestamp for randomizing database names to avoid collisions.


1.0b4 (2011-09-23)
------------------

- `drop-all` entry point now also works, if PostgreSQL or MySQL is not
  installed/running.

1.0b3 (2011-05-13)
------------------

- Added `connect` convenience method.


1.0b2 (2011-05-04)
------------------

- Added `is_testing` property as a convenience API.
- Added `exists` property as a convenience API.


1.0b1 (2011-04-12)
------------------

- Changed the protocol for using test databases: separated instantiating a
  Database instance from creating the database on the server. Creating
  Database instances is cheap now so they can be interacted with and passed
  around, deferring the expensive database creation on the server to the
  moment db.create() is called explicitly. This is also more symmetric with
  respect to db.drop().

- Added functionality for dropping all databases matching the testdb naming
  scheme which may have been left on the server by earlier test runs.
  Optionally also drops the template db.

- Added option to specify the name of the database for MySQL and PostgreSQL.

- Added an option to specify a template database for PostgreSQL. If it does
  not exist, it is created from the specified schema. It is also possible to
  force the creation of the template even if it exists (dropping the current
  template database). Whenever the schema has changed since the template db
  was last created, the template db is updated automatically.


0.4 (2010-12-15)
----------------

- Added option to specify the encoding for the PostgreSQL database.

- Updated PostgreSQL protocol from ``postgres:`` to ``postgresql:`` as the
  former one is deprecated in SQLAlchemy 0.6, thus requiring atleast version
  0.5.6 of SQLAlchemy.

- Added documentation how to develop this package further.

- Added doumentation about usage of `Database prefix`.


0.3 (2010-10-15)
----------------

- PostgreSQL: Don't call createdb/dropdb with ``--quite`` but only psql.

0.2 (2009-02-26)
----------------

- implemented authentication with password for mysql.
  Passwords for postgres are still not supported, though.

0.1 (2008-09-26)
----------------

- first release
