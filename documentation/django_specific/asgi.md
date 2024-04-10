# Asynchronous Server Gateway Interface (ASGI)
## ASGI is the Successor to WSGI
ASGI is the successor to the WSGI (Web Server Gateway Interface), which was the traditional
Python standard for web servers and applications to communicate. While WSGI is synchronous and can
handle only one request at a time in a single process, ASGI supports asynchronous processing,
allowing for more efficient handling of long-running connections, such as those needed for:
* Websockets
* HTTP/2
* Long Polling

## Asynchronous Programming
Allows a single server process to handle multiple requests simultaneously by pausing the execution
of one task to wait for I/O operations while another task is executed. This can lead to significant
performance improvements for certain types of applications, particularly those that are I/O-bound or
that need to manage long-lived network connections.

## Django & ASGI
* Starting in Django 3.0, Django has built-in support for ASGI.
* Django projects can still use WSGI if they don't require async features.
* The `asgi.py` file is generated automatically, and can be customized.
* To use Django with an ASGI server, you specify the path to your project's `asgi.py` module when configuring the server.

## When to Use ASGI
* WebSocket Support: Real-time features / chat / live notifications. WSGI doesn't support these.
* Asynchronous Views: Use `async def` to support async Views.
* Channels: Django Channels extends Django to handle WebSockets, chat protocols, IoT protocols, and more.
* Middleware: Certain Django Middleware requires it.

## Deployment
See the `../deployment` directory of documentation for details on different deployment options.

Options:
* [Daphne](https://docs.djangoproject.com/en/5.0/howto/deployment/asgi/daphne/): HTTP, HTTP2, WebSocket, developed as part of the Django Channels project. Bulkier. Use this if using Django Channels.
* [Uvicorn](https://www.uvicorn.org/): Uvicorn is an ASGI web server implementation for Python. Lightweight.
* [Hypercorn](https://docs.djangoproject.com/en/5.0/howto/deployment/asgi/hypercorn/): Supports HTTP/1, HTTP/2, and HTTP/3 with an emphasis on protocol support.