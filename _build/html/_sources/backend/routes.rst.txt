Routes
======

.. _RoutesIntroduction:

Introduction
------------

To access data from the API, certain routes are registered. You can find these routes in
``chassis-automation-api/routes/api.php``.

.. _RoutesMiddleware:

Middleware and permissions
--------------------------

Chassis Automation uses two important middlewares: ``api:auth`` and ``permission:{{permission-name}}``.

The ``api:auth`` middleware handles the user authentication. All routes should be registered within this middleware group.
An example is shown below.

.. code-block:: php

    Route::group(['middleware' => 'auth:api'], function () {
        Route::get('/processes', '\App\Processes\Http\Controllers\ProcessesController@getProcesses');
    }

The ``permission:{{permission-name}}`` middleware makes sure that the authenticated user has the right permission to
access a route. The ``{{permission-name}}`` placeholder should be replaced by the desired permission that is
registered in the database, as stated earlier. The example below combines the ``auth:api`` middleware and the ``permission:processes`` middleware
to make sure that a user must be authenticated and have the **processes** permission to access the route.

.. code-block:: php

    Route::group(['middleware' => 'auth:api'], function () {
        Route::group(['middleware' => 'permission:processes'], function () {
            Route::get('/processes', '\App\Processes\Http\Controllers\ProcessesController@getProcesses');
        }
    }

.. tip::

    If you need to make changes to the ``permission:{{permission-name}}`` middleware, you can find it in
    ``chassis-automation-api/app/Http/Middleware/CheckPermissions.php``.