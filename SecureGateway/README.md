# Secure Gateway

The Secure Gateway client requires a Service to connect to from within Bluemix. For additional information about Secure Gateway and the Client CLI, check the [Bluemix Docs](https://console.ng.bluemix.net/docs/services/SecureGateway/sg_010.html#sg_010).

The container image currently has the client running as the `ENTRYPOINT` to the docker container. This means that command line parameters may be passed directly to the container as part of the `docker run` command if desired.

**Note** The client CLI is running as the main process within the container. Once working with the CLI **do not** `quit` out of the CLI. This will stop the container. Instead, just close the terminal window. This ensures the container stays running in the background. This is not the desired solution, but is the current workaround to some of the functionality of the container.

### Build the Docker Image
```
  docker build . -t s390x/securegateway
```

### Running the Container
Once the service is created, select `Add Gateway` then `Add Client`.

Start the container with the following commands:
```
  docker run -it s390x/securegateway
```

See the note above for proper way to leave client running. To make modifications to a running container, use `docker attach`

### CLI commands
Once in the CLI, the useful commands can be listed by typing `help`.

All commands here are typed after the `cli>` prompt shown when connecting/attaching to the docker container. After connecting to a gateway, this prompt changes to `gateway_id>`.

1. Connect your client to the Gateway created in Bluemix
  - First provide a token `t <token_from_bluemix>`
  - Then connect with the Gateway ID `c <gateway_id_from_bluemix>`
2. Add ACLs to backend services
  - List your workers and identify their id `list`
  - Add backend service to secure gateway `acl allow hostname:port worker_id`

**Remember** to close the terminal window, not `quit` after any modifications.

### Add Destination on Bluemix
Select Add Destination on Bluemix and use Advanced Setup.

1. Select 'On Premises Destination' radio button
2. Specify the same `hostname:port` as provided to the client cli. No protocol is required here.
3. Check for client connection establishment by using the generated cloud host and port
