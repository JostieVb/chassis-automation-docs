Installation
============

.. _FrontendInstallationIntroduction:

Introduction
------------

Clone the project from `Github
<https://github.com/JostieVb/chassis-automation-client>`_. When completed, navigate to the project folder and run ``npm install``.

.. _FrontendInstallationSettingUp:

Setting up
----------

When the installation is completed, some other import things should be set.
In ``chassis-automation-client/src/app/`` you can find a file called ``global.ts`` that holds two constants name ``API_BASE`` and ``BACKEND_BASE``
By default, these constants will have the following values.

.. code-block:: javascript

    export const API_BASE = 'http://localhost:8000/api/';
    export const BACKEND_BASE = 'http://localhost:8000/';

These constants must correspond to the locations where back-end API will run.
If you are running Chassis Automation on another server or port, please change these constants to the right values.

.. _FrontendInstallationDevelopmentServer:

Development server
------------------

To run a development server locally, navigate to the project folder
and run ``ng serve``. The app will be available on ``http://localhost:9000`` and will automatically reload
if you change any of the source files.