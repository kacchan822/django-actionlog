===================
 Django Actionlog
===================


Getting Started
===============

Django Action is can be check the python-time, sql-time and query-count for each requests
for the Django Framework. Result outputs the log to file, console or fluentd.

.. image:: https://raw.github.com/fujimisakari/django-actionlog/master/example/django-actionlog.png


Requirements
============

Django Actionlog requires Django 1.6 or later.


Getting It
==========

You can get Django Actionlog by using pip or easy_install::

    $ pip install django-actionlog
    or
    $ easy_install django-actionlog

If you want to install it from source, grab the git repository from GitHub and run setup.py::

    $ git clone git://github.com/fujimisakari/django-actionlog.git
    $ cd django-actionlog
    $ python setup.py install


Installing It
=============

To enable `django_actionlog` in your project you need to add it to `MIDDLEWARE_CLASSES` and `ACTION_LOG_SETTING` in your projects 
`settings.py` file::

    MIDDLEWARE_CLASSES = (
        ...
        'django_actionlog.middleware.ActionLogMiddleware',
        ...
    )

    # Action Log
    ACTION_LOG_SETTING = {'handler_type': 'stdout'}


Using It
========

Case of output runserver console ::

    ACTION_LOG_SETTING = {'handler_type': 'stdout'}

Case of output file ::

    # default logfile: `/tmp/django_action.log`
    ACTION_LOG_SETTING = {'handler_type': 'file', 'logfile': '/tmp/my_action.log'}


Case of output fluentd ::

    # default host: `localhost`
    # default port: `24224`
    # default tag_name: `django.actionlog`
    ACTION_LOG_SETTING = {'handler_type': 'fluentd', 'host': 'example.com', 'tag_name': 'my_service.foo'}
    
Case of want to output custom actionlog ::

    from django-actionlog import actionlog

    ...    
    actionlog.log({'foo': 'bar', 'fizz': 'buzz'...})
    ...