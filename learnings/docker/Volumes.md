Types of data in a container:
- The base application data. Source code etc.
- Temporaryy app data. Fetched and produced when runnign the container. Usually temporary and fine if it is cleared regularly.
- Permanent App data. Fetched/Produced in running container. Stored in files or DB. Must not be lost when the container stops/restarts.

Volumes are folders on the host machone that Docker will be aware of and will be mapped to folders in the container.

#### Creating Volumes (No docker-compose)
2 types:

1. **Anonymous**
   Add the following to the Dockerfile:
```dockerfile
...
# This is the path in the container
VOLUME [ "/app/feedback" ]
...
```

2. **Named**
   The following is added to the run command:
   `-v localmachine:/app/docker-location`
   Example: `-v feedback:/app/feedback`
   

#### Bind mounts
A path/folder is being defined between host machine and the docker container.
Can bind a whole folder and a single file.

Add the following to the run command:
`-v "<abolute_path_from_host>:<workdir_of_container>"`

Some shorcuts to get absolute path:
- mac/linux: `-v $(pwd):/app`
- windows: `-v "%cd%":/app`

Can be issues with files that dont need to be readded being readded. Can be fixed with anon volume:
`-v /app/<file>`
example: `-v /app/node_modules`


#### Readonly Volumes
`-v <host>:<container>:ro`

We can still change the files on host, but container can't change them.
If you supply a more specific volume path (Like anonymous for node_modules), it will change it to read/write


