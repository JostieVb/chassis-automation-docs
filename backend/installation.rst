Installation
============

.. _BackendInstallationIntroduction:

Introduction
------------

Chassis Automation's back-end is available on `Github
<https://github.com/JostieVb/chassis-automation-api>`_ as ``chassis-automation-api``.
Clone the project from Github. When completed, navigate to the project folder and run ``composer install``.

.. _BackendInstallationDatabaseSetup:

Database set-up
---------------

When the installation is completed, you should set the correct database connection credentials in ``chassis-automation-api/.env``.
You should set the following contents.

.. code-block:: php

    DB_HOST=database_host
    DB_DATABASE=database_name
    DB_USERNAME=username
    DB_PASSWORD=password

When the right credentials are set and a database connection is accomplished, you can run ``php artisan migrate:refresh --seed`` to migrate and seed the database tables.

.. _BackendInstallationDevelopmentServer:

Development server
------------------

To run a development server locally, navigate to the project folder
and run ``php artisan serve``. The API will be available on ``http://localhost:8000``.