.. _ModelerIntroduction:

Introduction
------------

The modeler uses a toolkit called `BPMN-js
<https://github.com/bpmn-io/bpmn-js>`_. The modeler is used when creating or editing a process on the 'Processes' page.
This chapter will explain the features of the modeler.

.. _ModelerSupportedBpmnItems:

Supported BPMN items
--------------------

This table shows BPMN items that are currently supported by Chassis Automation's modeler.

+-------------------------------+----------------------------------------------------------------------+
| Item                          | Brief description                                                    |
+===============================+======================================================================+
| Start-event                   | The very beginning of a process                                      |
+-------------------------------+----------------------------------------------------------------------+
| User-task                     | The assigned user has to execute a task before the process continues |
+-------------------------------+----------------------------------------------------------------------+
| Send-task                     | Send a message with a task to the assigned user                      |
+-------------------------------+----------------------------------------------------------------------+
| Receive-task                  | Send a message to the assigned user                                  |
+-------------------------------+----------------------------------------------------------------------+
| Exclusive gateway (X-OR)      | The flow gets divided to one of the output branches                  |
+-------------------------------+----------------------------------------------------------------------+
| End-event                     | The very end of a process.                                           |
+-------------------------------+----------------------------------------------------------------------+

.. _ModelerBasics:

Modeler initialization
----------------------

The modeler component can be found in ``chassis-automation-client/src/app/processes/pages/modeler/modeler.component.ts``.
The modeler is initialized in the ``instantiateModeler()`` function and is stored in the ``modeler`` property of the modeler component.
If you need to add additional modules to the modeler, you can import them to the modeler component add them to the ``additionalModules`` array
in the ``instantiateModeler()`` function. An example is shown below.

.. code-block:: javascript

    import { AdditionalModuleName } from 'additional/module/path';

    export class ModelerComponent implements OnInit, OnDestroy {

        instantiateModeler() {
            return new Modeler({
                container: '.canvas',
                additionalModules: [
                    // Add additional modules here
                ]
            });
        }
    }

.. _ModelerHostListener:

Properties panel
----------------

To enable user interaction with BPMN items in order to edit their properties, a ``@HostListener`` is created.
This host listener listens to click events that occur on editable BPMN items and calls a function that will display the selected item's properties in the properties panel.
If you want to extend the range of items that are editable, you can add the type of the item that should be editable to the ``editableTypes`` array, which is a property of the modeler component.
A new editable type should be added to this array as a **lowercase string without any spaces or other seperators between words**. Currently, this array holds the following values.

.. code-block:: javascript

    protected editableTypes = ['task', 'exclusivegateway', 'startevent', 'endevent'];

When an editableType is clicked, the ``initProperties(id: string, type: string)`` initializes the properties for the selected item.
The properties will be displayed if they already exist for the clicked item. If they don't exist, they will be created by the ``generatePropertiesByType(id: string, type: string, sequence: any)`` function in the properties service.

The properties service
~~~~~~~~~~~~~~~~~~~~~~

The properties service can be found in ``chassis-automation-client/src/app/processes/services/properties.service.ts``.
This service generates the properties (``generatePropertiesByType()``) and holds additional information for the properties panel that will be returned from the ``helpers()`` function.

Extending the properties generator
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

To extend the properties generator, you have to add another ``case`` for the ``switch`` that checks for the type of the selected item to the ``generatePropertiesByType()`` method.
Within this ``case``, you can set the desired properties and their values that should be set when te properties get generated. Mostly, the property values are empty, because
they have to be set by the end-user. An example is shown below.

.. code-block:: javascript

    generatePropertiesByType(id: string, type: string, sequence: any) {
        const property = {id: id, type: type};
        switch (type) {
            case 'newtype':
                property['firstProperty'] = '';
                property['secondProperty'] = [];
                property['thirdProperty'] = {
                    'firstExample': 'This property has pre-set values'
                    'secondExample': 'Another pre-set value'
                };
                break;
            // More properties here
        }
        return property;
    }

To render the properties, you need to add a new ``ng-template`` element to the html template for the modeler.
You can find the html template in ``chassis-automation-client/src/app/processes/pages/modeler/modeler.component.html``.

Extending the helpers
~~~~~~~~~~~~~~~~~~~~~

The ``helpers()`` method returns an object that holds more information for the end-user about certain properties.
During rendering, this information will be shown in pop-up balloons in the properties panel.
If you want to extend the helpers, you can simply add a new property to the object that the ``helpers()`` method returns.
You can find an example below.

.. code-block:: javascript

    helpers() {
        return {
            id: 'The identifier is unique and can\'t be modified.',
            type: 'This is the type of the selected item.',
            // Add more helpers here
        };
    }
