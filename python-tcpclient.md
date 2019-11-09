<!-- TITLE: Python Tcpclient -->
<!-- SUBTITLE: A quick summary of Python Tcpclient -->

```
s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
# now connect to the web server on port 80 - the normal http port
s.connect(("www.python.org", 80))
```