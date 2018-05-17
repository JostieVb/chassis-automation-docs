.. _DataTablesIntroduction:

Introduction
------------

The Chassis Automation's database, called ``chassis_automation``, both uses a fixed structure of data tables and editable tables
for data storage.

.. _DataTablesStructure:

Structure
---------

Fixed data tables are tables that cannot be edited through the front-end on the 'Data tables' page in the prototype.
These tables hold important data that must be accessible for the back-end in a fixed structure. The table
below shows these fixed data tables.

+-------------------------------+---------------------------------------------------------------+
| Data table name               | Brief description                                             |
+===============================+===============================================================+
| entry                         | Holds all entries                                             |
+-------------------------------+---------------------------------------------------------------+
| form                          | Holds all forms created with the form builder                 |
+-------------------------------+---------------------------------------------------------------+
| link                          | Holds the links between forms and processes (workflows)       |
+-------------------------------+---------------------------------------------------------------+
| migrations                    | Holds all database migrations                                 |
+-------------------------------+---------------------------------------------------------------+
| oauth_access_tokens           | Holds all access tokens entries                               |
+-------------------------------+---------------------------------------------------------------+
| oauth_clients                 | Holds registered clients (chassis-automation-client)          |
+-------------------------------+---------------------------------------------------------------+
| oauth_personal_access_clients | Holds all personal access clients (chassis-automation-client) |
+-------------------------------+---------------------------------------------------------------+
| oauth_refresh_tokens          | Holds the refresh tokens                                      |
+-------------------------------+---------------------------------------------------------------+
| password_resets               | Holds the password resets                                     |
+-------------------------------+---------------------------------------------------------------+
| process                       | Holds registered clients (chassis-automation-client)          |
+-------------------------------+---------------------------------------------------------------+
| users                         | Holds registered users                                        |
+-------------------------------+---------------------------------------------------------------+

Chassis Automation also support dynamic tables. These tables are used to link to forms using the form builder.
and their names **must** start with the ``ca_`` prefix. By default, a dynamic table **must** have at least the following columns.

+-------------------------------+---------------------------------+
| Column name                   | Brief description               |
+===============================+=================================+
| id                            | Primary key                     |
+-------------------------------+---------------------------------+
| added_by                      | Foreign key                     |
+-------------------------------+---------------------------------+
| status                        | Indicates the status of an item |
+-------------------------------+---------------------------------+

