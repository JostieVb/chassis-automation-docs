Folder structure
================

.. _BackendFolderStructureIntroduction:

Introduction
------------

This chapter focuses on clarifying the back-end folder structure.
Because Chassis Automation doesn't depend on Chassis packages yet, the ``kaiser`` folder will not
be displayed below.

.. _BackendFolderStructure:

Folder structure
----------------

The overview below shows the global folder structure of Chassis Automation's back-end.

.. code-block:: text

    chassis-automation-api
    ├── app
    │   ├── {{Controller-name}} // Every controller has its own folder like this
    │   │   ├── Http
    │   │   │   └── Controllers // All controllers will be displayed here: ControllerName.php
    │   │   └── Models          // If a controller uses models, they will be here
    │   └── User.php            // Default user model
    ├── bootstrap
    ├── config
    ├── database
    │   ├── factories
    │   ├── migrations          // The database migrations can be found here
    │   └── seeds
    ├── public                  // Public files, like index.php and .htaccess
    ├── resources
    ├── routes
    │   ├── api.php             // The routes that will be used to access data from the API are described here
    │   ├── channels.php
    │   ├── console.php
    │   └── web.php
    ├── storage                 // Cache storage
    ├── tests
    ├── vendor                  // All installed back-end packages will appear here
    ├── .env                    // Holds import config data e.g. database credentials
    ├── composer.json
    ├── composer.lock
    ├── package.json
    ├── phpunit.xml
    ├── readme.md
    ├── server.php
    └── webpack.mix.js