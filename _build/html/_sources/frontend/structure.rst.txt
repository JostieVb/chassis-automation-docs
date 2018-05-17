Folder structure
================

.. _FrontendFolderStructureIntroduction:

Introduction
------------

This chapter focuses on clarifying the front-end folder structure.
Because Chassis Automation doesn't depend on Chassis packages yet, the ``@kaiser-software`` folder will not
be displayed below.

.. _FrontendFolderStructure:

Folder structure
----------------

The overview below shows the global folder structure of Chassis Automation's front-end.

.. code-block:: text

    chassis-automation-client
    ├── e2e                          // Folder for end-to-end testing
    ├── node_modules                 // Installed Angular packages will appear here
    ├── src
    │   ├── app
    │   │   ├── {{page-name}}        // Every page/component has its own folder like this one
    │   │   │   ├── modals           // If a page has modals, they will be here
    │   │   │   ├── models           // If a page has models, they will be here
    │   │   │   ├── pages            // All components of a page will be here
    │   │   │   ├── services         // If a page has services, they will be here
    │   │   │   └── directives       // If a page has custom directives, they will be here
    │   │   ├── app.modules.ts       // The app module where all components, services and routes are registered
    │   │   └── global.ts            // A file that holds global constants
    │   ├── assets                   // All global assets will be here
    │   │   ├── img                  // All global images will be here
    │   │   ├── resources            // bpmn-js test diagrams will be here
    │   │   └── styles
    │   │       └── global_vars.scss // This .scss file holds global scss variables
    │   ├── environments             // All global assets will be here
    │   ├── favicon.ico
    │   ├── index.html
    │   ├── main.ts
    │   ├── polyfills.ts
    │   ├── styles.scss              // Global styles are described here
    │   ├── test.ts
    │   ├── tsconfig.app.json
    │   └── typings.d.ts
    ├── angular-cli.json
    ├── editorconfig
    ├── karma.conf.js
    ├── package.json
    ├── package-lock.json
    ├── protractor.conf.js
    ├── README.md
    ├── tsconfig.json
    └── tslint.json