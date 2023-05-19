![Banner image](https://user-images.githubusercontent.com/10284570/173569848-c624317f-42b1-45a6-ab09-f0ea3c247648.png)

# n8n-nodes-printer

This node gives you the ability to print via a CUPS server.
This means you need to have a CUPS server, which must be online when the workflow sends files to print.
The server will manage all the printers you need.


## Prerequisites

The 'cups-client' package is required: https://pkgs.org/download/cups-client.
You can add it to your Dockerfile as follows:

RUN apk --no-cache add su-exec cups-client

## Dealing with 'Error - The printer or class does not exist'

You may encounter the 'Error - The printer or class does not exist' issue due to your network configuration (for instance, if you're not on the same LAN).
You need to add the reverse resolution name of the printer to CUPS (as the ServerName in /etc/cups/client.conf).

You can add this to your Dockerfile as follows:

RUN mkdir -p /etc/cups && \
    echo "ServerName 192.168.1.100" > /etc/cups/client.conf

## License

[MIT](https://github.com/n8n-io/n8n-nodes-starter/blob/master/LICENSE.md)
