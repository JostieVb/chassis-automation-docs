Back-end
========

Chassis Automation's back-end is a Laravel 5 API. Therefore, the back-end relies on Composer to install
and update dependencies. Please install `Composer
<https://getcomposer.org/>`_ if you don't have it installed yet.

.. rubric:: Installation

This chapter will explain the installation process of Chassis Automation's back-end.

.. toctree::
    :hidden:

    installation

* :ref:`BackendInstallationIntroduction`
* :ref:`BackendInstallationDatabaseSetup`
* :ref:`BackendInstallationDevelopmentServer`

.. rubric:: Folder structure

.. toctree::
    :hidden:

    structure

* :ref:`BackendFolderStructureIntroduction`
* :ref:`BackendFolderStructure`

.. rubric:: Authentication

This chapter will explain the usage of Laravel Passport within the prototype.

.. toctree::
    :hidden:

    authentication

* :ref:`AuthenticationIntroduction`
* :ref:`RoutesMiddleware`

.. rubric:: Routes

Routes are the API end-points for Chassis Automation. This chapter provides more information about the usage and other stuff.

.. toctree::
    :hidden:

    routes

* :ref:`RoutesIntroduction`
* :ref:`RoutesMiddleware`

.. rubric:: Data tables

This chapter will explain the database structure and the usage of prefixed data tables and columns for data storage.

.. toctree::
    :hidden:

    data-tables

* :ref:`DataTablesIntroduction`
* :ref:`DataTablesStructure`

.. rubric:: BPMN controller

The BPMN controller handles calls from the front-end that should be linked to a process. This chapter will explain
the usage of the BPMN controller.

.. toctree::
    :hidden:

    bpmn-controller

* :ref:`BpmnControllerIntroduction`
* :ref:`BpmnControllerHandlingRequests`
* :ref:`BpmnControllerExtendingBpmnController`

