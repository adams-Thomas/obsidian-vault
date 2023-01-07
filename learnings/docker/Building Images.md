```dockerfile
	# Environment you want to build
	FROM node 

	# The working directory in the docker container
	WORKDIR /app

	COPY package.json /app

	# Use RUN to run any commands you want
	RUN npm install

	# Copy desired files from the physical computer to docker image
	COPY . /app

	# Expose a port to access the running server etc
	EXPOSE 80

	# Final command to start the container if needed
	CMD ["node", "server.js"]
```

Runs with the following commands:
`docker build .`
`docker run -p 3000:80 <ID from above>

Notes on above DockerFile:
- Any changes to the source code won't be reflected unless you manually recreate the image.
- The `.` is context for docker cli to know where the DockerFile is
- Even though port 80 is exposed in Dockerfile, an external port still need to be assigned to it. Hence the `3000:80`
- Copy across the package.json and npm install before main source code copy. This prevents any commands like that from running everytime you change your source code and rebuild.
