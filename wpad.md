<!-- TITLE: Wpad -->
<!-- SUBTITLE: A quick summary of Wpad -->

# DNS
# WINS
# NMB
# DHCP
Can this be sent unsolicited?

# Example Response

```text
function FindProxyForURL(url, host) {
        return "PROXY 10.0.0.169:8080";
}
```



# Example Python Server (note content-type)

```text
import SimpleHTTPServer
import SocketServer
import logging

PORT = 80


class GetHandler(SimpleHTTPServer.SimpleHTTPRequestHandler):

    def do_GET(self):
        logging.error(self.headers)
        SimpleHTTPServer.SimpleHTTPRequestHandler.do_GET(self)

Handler = GetHandler

Handler.extensions_map.update({
    '.dat': 'application/x-ns-proxy-autoconfig',
});

httpd = SocketServer.TCPServer(("", PORT), Handler)

print "serving at port", PORT
httpd.serve_forever()

```


