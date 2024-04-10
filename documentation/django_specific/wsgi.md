# Web Server Gateway Interface (WSGI)
## Standard Python Interface between Web Server and Web Applications
Describes how a web server communicates with web applications, and how web applications can be
chained together to process one request. Is synchronous in nature, which means it handles one
request at a time per process. Traditional way of serving Python web applications.

> **Warning:** When using async Views, it's crucial to ensure that your database and DB driver support async operations or are properly managed to avoid blocking the async loop.

## Key Points
* Purpose: Created to establish a standard interface b/w web server and Python apps.
* Synchronous Processing: Limits ability to handle concurrent, long-running, or I/O-bound requests efficiently.
* Components:
  * The WSGI Server (or Gateway): Serves static files. Forwards requests from client to the application. Sends response to the client.
  * The WSGI Application: Processes request and returns a response (Django, Flask, etc.)
* Built-in: Django comes with a built-in WSGI application called `wsgi.py`.

## Deployment
See the `../deployment` directory of documentation for details on different deployment options.

Options include:
* [Gunicorn](https://gunicorn.org/)
* [uWSGI](https://uwsgi-docs.readthedocs.io/en/latest/)
* [mod_wsgi (Apache)](https://modwsgi.readthedocs.io/en/master/)

These would be configured to use Django's `wsgi.py` file as the entry point for serving the application.

## Possible Issues
* Performance: While some aspects of performance improve, `sync_to_async` wrapped ORM calls incur additional overhead from thread pool.
* Database Connections: While Django manages database connections, it's crucial to ensure that your database and DB driver support async.
* Complexity: Writing async code can introduce additional complexity, particularly when dealing with synchronous dependencies like the ORM.