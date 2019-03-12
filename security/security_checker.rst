.. index::
    single: Security; Vulnerability Checker

How to Check for Known Security Vulnerabilities in Your Dependencies
====================================================================

When using lots of dependencies in your Symfony projects, some of them may
contain security vulnerabilities. That's why Symfony includes a command called
``security:check`` that checks your ``composer.lock`` file to find any known
security vulnerability in your installed dependencies:

.. code-block:: terminal

    $ php bin/console security:check

A good security practice is to execute this command regularly to be able to
update or replace compromised dependencies as soon as possible. Internally,
this command uses the public `security advisories database`_ published by the
FriendsOfPHP organization.

.. tip::

    The ``security:check`` command terminates with a non-zero exit code if
    any of your dependencies is affected by a known security vulnerability.
    This way you can add it to your project build process and your continuous
    integration workflows to make them fail when there are vulnerabilities.

.. tip::

    Earlier versions of this command used a tool hosted at a now deprecated URL,
    with the tool having since been moved to a new location, which has been 
    reflected in newer versions of the bundle. Use the latest version of the 
    command to avoid getting exit code zero and breaking existing build plans
    if the command has been integrated into project build process.
    
.. note::

    To enable the ``security:check`` command, make sure the
    `SensioDistributionBundle`_ is installed and enabled in your application.

.. tip::

    The security checker is also available as an independent console application
    and distributed as a PHAR file so you can use it in any PHP application.
    Check out the `Security Checker repository`_ for more details.

.. _`security advisories database`: https://github.com/FriendsOfPHP/security-advisories
.. _`SensioDistributionBundle`: https://github.com/sensiolabs/SensioDistributionBundle
.. _`Security Checker repository`: https://github.com/sensiolabs/security-checker
