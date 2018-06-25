Deploy
======

.. _DeployIntroduction:

Introduction
------------

This chapter informs you about how to deploy Chassis Automation's front-end to a live server.

.. _DeployDeployment:

Deployment
----------

Before building, make sure that the right location of the Chassis Automation API on your live server is set correctly in ``chassis-automation-client/src/app/global.ts``.
After that, run ``ng build`` to build the project. The build artifacts will be stored in the ``dist/`` directory. Use the ``-prod`` flag for a production build.

When done building, copy all content from the ``dist/`` directory to your live server.