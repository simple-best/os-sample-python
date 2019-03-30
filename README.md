# Flask Sample Application

This repository provides a sample Python web application implemented using the Flask web framework

This sample Python application relies on the support provided by the default S2I builder for deploying a WSGI application using the ``gunicorn`` WSGI server. The requirements which need to be satisfied for this to work are:

* The WSGI application code file needs to be named ``wsgi.py``.
* The WSGI application entry point within the code file needs to be named ``application``.
* The ``gunicorn`` package must be listed in the ``requirements.txt`` file for ``pip``.

In addition, the ``.s2i/environment`` file has been created to allow environment variables to be set to override the behaviour of the default S2I builder for Python.

* The environment variable ``APP_CONFIG`` has been set to declare the name of the config file for ``gunicorn``.


## Deployment Steps

1. To deploy this sample Python web application from the OpenShift web console, ``python:3.7`` or ``python:latest``.

2. Use the following git URL    https://github.com/simple-best/os-sample-python.git

3. If using the ``oc`` command line tool (cli) instead of the OpenShift web console, you can run:

```
oc sample_py_flask_app https://github.com/simple-best/os-sample-python.git
```

4. If no language type is specified, OpenShift will determine the language by inspecting the code repository. 
   - Because the code repository contains a ``requirements.txt``, it will subsequently be interpreted as including a Python application. 
   - When such automatic detection is used, ``python:latest`` will be used.

5. If needing to select a specific Python version when using ``oc new-app``, you should instead use the form:

```
oc sample_py_flask python:3.7~https://github.com/OpenShiftDemos/os-sample-python.git
```
