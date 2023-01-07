## Sharing Images
1. Share the plain Dockerfile with source code.
2. Share a built image.

## Pushing to Dockerhub
1. **Dockerhub**
   Can store public,privare and "official" images.
   `docker push <IMAGE_NAME>` to push to Dockerhub.
   `docker pull <IMAGE_NAME>` to get the image.
   
   Main steps to deploy:
   1. Create repository and chose your settings.
   2. In local env:
	   1. Set tag of image to the same as the repo on Dockerhub
	   2. Login with `docker login`
	   3. Then run `docker push <IMAGE/REPO NAME>` 

2. **Private registry**
   Any provider/registry