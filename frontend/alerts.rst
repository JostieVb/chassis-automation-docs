Alerts
======

.. _AlertsIntroduction:

Introduction
------------

Alerts can be send to the end-user on a call-back function or in other cases.
The alerts will pop-up in the bottom right corner of the screen. In this chapter, you will learn
how to use these alerts and how to configure them.

.. _AlertsImplementingAnAlert:

Implementing an alert
---------------------

To implement an alert, you need to ``import`` the ``AlertService`` (alert.service.ts) and the ``Alert`` (alert.ts) model.
You can find these files in ``chassis-automation-client/src/app/components/alert``.
To show a new alert to the user, you have to emit a new instance of an ``Alert`` to the ``alert`` property of the ``AlertService``
with the desired content. The table below shows the ``Alert`` model's constructor parameters.

+----------------------------+-----------------------------------------------------------------------------------------------------------------------+---------------+-------------+
| Parameter name             | Brief description                                                                                                     | Default value |Type         |
+============================+=======================================================================================================================+===============+=============+
| message                    | The message that should be displayed in the alert                                                                     |               | ``string``  |
+----------------------------+-----------------------------------------------------------------------------------------------------------------------+---------------+-------------+
| type                       | The type of the alert (success | warning | danger | info)                                                             |               | ``string``  |
+----------------------------+-----------------------------------------------------------------------------------------------------------------------+---------------+-------------+
| prefix (optional)          | An optional prefix that will be displayed before the message                                                          | ``''``        | ``string``  |
+----------------------------+-----------------------------------------------------------------------------------------------------------------------+---------------+-------------+
| clearAlertBox (optional)   | An optional boolean that indicates whether the alert box should be cleared before showing the alert (true | false)    | ``false``     | ``boolean`` |
+----------------------------+-----------------------------------------------------------------------------------------------------------------------+---------------+-------------+
| dismissable (optional)     | An optional boolean that indicates whether the alert can be dismissed (true | false)                                  | ``true``      | ``boolean`` |
+----------------------------+-----------------------------------------------------------------------------------------------------------------------+---------------+-------------+
| interval (optional)        | An optional interval that holds the amount of time an alert should be shown. The default value is 5 seconds (5000 ms) | ``5000``      | ``number``  |
+----------------------------+-----------------------------------------------------------------------------------------------------------------------+---------------+-------------+

An alert can also be displayed for an infinite amount of time instead of a fixed time span. To achieve this, you have to set the ``interval`` parameter to ``0``.
If both the ``interval`` is set to ``0`` and ``dismissable`` is ``false``, the alert will automatically get the default interval, because it is not user friendly
to show an alert that is shown forever and can't be dismissed by the user.

The code example below shows a case where a form is submitted. After submission, an alert of the type ``success`` is send to the user
with a prefix.

.. code-block:: javascript

    // Other imports...

    import { AlertService } from './components/services/alert.service';
    import { Alert } from './components/alert/alert';

    constructor(
        // Other injectables...

        private alertService: AlertService

    ) {}

    export class ExampleComponent {

        protected submitForm(data: any) {
            // Do the form submit. When complete, notify the user through an alert

            this.alertService.alert.next(
                new Alert(
                    'The form was successfully submitted.',
                    'success',
                    'Yay!',
                    true,
                    true,
                    3000
                )
            );

        }

    }

The image below shows how the alert will be rendered to the end-user. Because an optional interval was provided, this
alert will be shown for 3 seconds instead of the default 5 seconds.

.. image:: images/alert-example.jpg