
#### Basic Communication
If the db or service is running locally, use `host.docker.internal` instead of localhost in connection strings.

To get IP of container: 
`docker container inspect`
That IP can be used in another container to communicate with the container.

#### Networks
Add `--network my_network` to the run command of containers.
This handles the IP resolving automatically.

If you give a container a name, it can be used as the IP for the container.