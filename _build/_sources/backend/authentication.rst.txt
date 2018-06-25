Authentication
==============

.. _AuthenticationIntroduction:

Introduction
------------

The Chassis Automation prototype uses `Laravel Passport
<https://laravel.com/docs/5.6/passport>`_ to authenticate users. This chapter will further inform you
about authentication of the prototype.

.. _AuthenticationLaravelPassport:

Laravel Passport
----------------

To grant the user access to the back-end, a JWT (Jason Web Token) is used to authenticate the user.
When the user is trying to log in, Laravel Passport automatically uses the `OAuth 2.0 authentication framework
<https://oauth.net/>`_ to authenticate the user. If the user has entered the correct credentials, the back-end will
return a JWT token. This token should always be send with any request coming from the front-end to ensure that the back-end
will authenticate the currently logged in user. The expiration time of the token is set according to its default value: 365 days.