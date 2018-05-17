BPMN controller
===============

.. _BpmnControllerIntroduction:

Introduction
------------

The BPMN controller handles requests coming from a caller in the front-end.
These calls are made by sending a ``POST`` request to the ``/call`` end-point of the API.
Subsequently, the request will be handled by ``BpmnController.php``, which you can find in
``chassis-automation-api/app/Bpmn/Http/Controllers/BpmnController.php``.

Below you can find more information about the functioning of the BPMN controller.

.. _BpmnControllerHandlingRequests:

Handling requests
-----------------

The request will be handled by the ``callHandler($request)`` you can find in ``BpmnController.php``.
The handler will get the desired data from the request. After that, it will check if a workflow is linked to the
form that made the call from the front-end. If a workflow is found, the handler will determine which task it should execute next.
After that, the handler will automatically get the type of the next task (e.g. ``exclusivegateway`` or ``endevent``).
Based on the type of the next task, the handler will execute the task and after execution a check will be performed to determine
if other tasks should be executed.

.. tip::

    By implementing more BPMN features, the workflow designer

.. _BpmnControllerExtendingBpmnController:

Extending the BPMN controller
-----------------------------

Extending the support of BPMN items by the BPMN controller is done by adding another type check at the end of the
``callHandler``. After that, within this check a function can be called that will handle the execution of the task.