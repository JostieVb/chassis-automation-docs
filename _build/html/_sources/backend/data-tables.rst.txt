Data tables
===========

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

Feel free to add other columns to prefixed tables. Make sure that editable columns are prefixed with ``ca_``.
Tables that are prefixed will be shown on the 'Data tables' page in the prototype and can be linked to a form with the form builder.
Thereafter, prefixed columns can be linked to form input field with the form builder.

.. danger::

    In editable tables, both the table name and all columns that can be linked to a form input field must have the ``ca_`` prefix.

.. _DataTablesMigrationAndSeeding:

Migration and seeding
---------------------

Migrate and seed Chassis Automation's data tables by running the following command:
``php artisan migrate:refresh --seed``.

After executing this command, three tests accounts are created. The table below shows their default credentials and permissions.

+----------------------------------+------------+---------------------------------------------------+
| Username                         | Password   | Permissions                                       |
+==================================+============+===================================================+
| admin@chassis-automation.com     | admin      | dashboard, entries, processes, forms, data-tables |
+----------------------------------+------------+---------------------------------------------------+
| logistics@chassis-automation.com | admin      | dashboard, entries                                |
+----------------------------------+------------+---------------------------------------------------+
| supplier@chassis-automation.com  | admin      | dashboard, entries, products                      |
+----------------------------------+------------+---------------------------------------------------+

.. _DataTablesEditUserPermissions:

Edit user permissions
---------------------

To edit the user permissions, you can change the values that are stored in the ``permissions`` column of the ``users`` table.

.. danger::

    User permissions are stored in the database as CSV format.