# **Serverless**


Serverless is a cloud execution approach that makes building and running cloud-native apps easier and more cost-effective.

- Provides the computer resources needed to run application code on demand or in reaction to a specified event automatically.


+ Scales those resources up or down automatically in response to increased or decreasing demand.

- When the application is stopped, the resources are automatically scaled down to zero.

Serverless delegates all management responsibilities for backend cloud infrastructure and operational chores to the cloud provider, including provisioning, scheduling, scaling, patching. This frees up time for developers to work on and improve their front-end application code and business logic.

<br>


## ***Serverless pros and cons***


### **Pros**

- It allows development teams to concentrate on producing code rather than infrastructure management. It provides developers a lot more time to experiment and improve the functionality.

- It enables developers to code in any language or framework: Java, Python, node.js.

- Serverless application development solutions offer near-total insight into system and user times, as well as the ability to systematically aggregate such data.

<br>

### **Cons**

- Serverless delivers significant cost reductions for spiky workloads due to its ability to scale up and down on demand in response to workload. However, it does not provide the same cost reductions for workloads that are predictable, steady.

- Monitoring and debugging are difficult in any distributed system, but moving to a serverless design simply adds to the difficulty.

<br>

### **Use cases for serverless**

- Serverless and microservices

- API backends

- Data processing

- Massively parallel compute/“Map” operations

- Stream processing workloads

<br>



## ***Deploying Serverless Functions***

To deploy Serverless Functions we can put files with extensions matching supported languages and exported functions in the '/api' directory at the project's root.

<br>

<br>

# **An Effective Python Environment: Making Yourself at Home**

### ***Shells***

This typically text-based interface is provided by a shell, which is a software. Shells frequently include a programming language that may be used to alter files, install software. For example:

- Unix Shells

- Bourne Shell (sh)

- Bourne-Again Shell (bash): 

    Bash expanded user-interaction features, building on the popularity of the original Bourne shell. Tab completion, history, and wildcard searching for commands and locations are all available in bash. More data types, such as arrays, are available in the bash programming language.

- Z Shell (zsh):

    Zsh combines the best elements of previous shells with a few of its own to provide a unique experience. Zsh provides autocorrection for misspelled commands, shorthand for editing multiple files, and advanced command prompt customization.

    In addition, Zsh provides a platform for extensive customisation. Oh My Zsh is a project that provides a large number of themes and plugins and is frequently used in conjunction with Zsh.


<br>

<br>

# **http.server — Base Classes for Implementing Web Servers**

### ***HTTP GET***

To add support for an HTTP method in a request handler class, implement the method do_METHOD(). For consistency, the request handler methods take no arguments. All of the parameters for the request are parsed by BaseHTTPRequestHandler and stored as instance attributes of the request instance.

```
from http.server import BaseHTTPRequestHandler
from urllib import parse


class GetHandler(BaseHTTPRequestHandler):

    def do_GET(self):
        parsed_path = parse.urlparse(self.path)
        message_parts = [
            'CLIENT VALUES:',
            'client_address={} ({})'.format(
                self.client_address,
                self.address_string()),
            'command={}'.format(self.command),
            'path={}'.format(self.path),
            'real path={}'.format(parsed_path.path),
            'query={}'.format(parsed_path.query),
            'request_version={}'.format(self.request_version),
            '',
            'SERVER VALUES:',
            'server_version={}'.format(self.server_version),
            'sys_version={}'.format(self.sys_version),
            'protocol_version={}'.format(self.protocol_version),
            '',
            'HEADERS RECEIVED:',
        ]
        for name, value in sorted(self.headers.items()):
            message_parts.append(
                '{}={}'.format(name, value.rstrip())
            )
        message_parts.append('')
        message = '\r\n'.join(message_parts)
        self.send_response(200)
        self.send_header('Content-Type',
                         'text/plain; charset=utf-8')
        self.end_headers()
        self.wfile.write(message.encode('utf-8'))


if __name__ == '__main__':
    from http.server import HTTPServer
    server = HTTPServer(('localhost', 8080), GetHandler)
    print('Starting server, use <Ctrl-C> to stop')
    server.serve_forever()
```

<br>

### ***HTTP POST***

Supporting POST requests is a little more work, because the base class does not parse the form data automatically. The cgi module provides the FieldStorage class which knows how to parse the form, if it is given the correct inputs.

```
http_server_POST.py
import cgi
from http.server import BaseHTTPRequestHandler
import io


class PostHandler(BaseHTTPRequestHandler):

    def do_POST(self):
        # Parse the form data posted
        form = cgi.FieldStorage(
            fp=self.rfile,
            headers=self.headers,
            environ={
                'REQUEST_METHOD': 'POST',
                'CONTENT_TYPE': self.headers['Content-Type'],
            }
        )

        # Begin the response
        self.send_response(200)
        self.send_header('Content-Type',
                         'text/plain; charset=utf-8')
        self.end_headers()

        out = io.TextIOWrapper(
            self.wfile,
            encoding='utf-8',
            line_buffering=False,
            write_through=True,
        )

        out.write('Client: {}\n'.format(self.client_address))
        out.write('User-agent: {}\n'.format(
            self.headers['user-agent']))
        out.write('Path: {}\n'.format(self.path))
        out.write('Form data:\n')

        # Echo back information about what was posted in the form
        for field in form.keys():
            field_item = form[field]
            if field_item.filename:
                # The field contains an uploaded file
                file_data = field_item.file.read()
                file_len = len(file_data)
                del file_data
                out.write(
                    '\tUploaded {} as {!r} ({} bytes)\n'.format(
                        field, field_item.filename, file_len)
                )
            else:
                # Regular form value
                out.write('\t{}={}\n'.format(
                    field, form[field].value))

        # Disconnect our encoding wrapper from the underlying
        # buffer so that deleting the wrapper doesn't close
        # the socket, which is still being used by the server.
        out.detach()


if __name__ == '__main__':
    from http.server import HTTPServer
    server = HTTPServer(('localhost', 8080), PostHandler)
    print('Starting server, use <Ctrl-C> to stop')
    server.serve_forever()
```
