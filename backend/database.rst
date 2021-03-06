Database
========

.. _DatabaseIntroduction:

Introduction
------------

This chapter will inform you about the Chassis Automation database, called ``chassis_automation``.

.. _DatabaseStructure:

Structure
---------

The table below displays all tables that are currently being used by the back-end.

+-------------------------------+---------------------------------------------------------------+
| Data table name               | Brief description                                             |
+===============================+===============================================================+
| bpmn_content                  | Holds all content of forms that are linked to processes       |
+-------------------------------+---------------------------------------------------------------+
| entry                         | Holds all entries                                             |
+-------------------------------+---------------------------------------------------------------+
| form                          | Holds all forms created with the form builder                 |
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

.. _DatabaseMigrationAndSeeding:

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

.. _DatabaseEditUserPermissions:

Edit user permissions
---------------------

To edit the user permissions, you can change the values that are stored in the ``permissions`` column of the ``users`` table.

.. danger::

    User permissions are stored in the database as CSV format.