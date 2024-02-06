# docker instructions:

# to build an image:
docker build -t image-name . 
* optional adding "-f ./dockerfile.dev" if wanting a different file other than the default Dockerfile
* the "." at the end of the image script is a must it refers to the location of the files to run inside the dockerfile commands
* remove all images by running (-f stands for force rmi stands remove images and the $() is a batch for replacing the result inside of it with thr $()): docker rmi -f $(docker images -a -q)


# to run a container:
docker run -p XX:XX -v $PWD:/usr/src/app -v /usr/src/app/node_modules --name my-node-container node-app-dev

* -p stands for port the left side to the column is the port on our local machine : right side of column is the port inside the container itself
* -v $PWD:/usr/src/app: This binds the current directory ($PWD) on the host to the /usr/src/app directory inside the container. when using a bind mount in Docker, only the specific files that are modified on the local machine will be transferred to the container. Other files in the bind-mounted directory will remain unaffected unless they are explicitly modified.
* -v /usr/src/app/node_modules: This mounts the node_modules directory inside the container separately, to optmize perforamnce that the dir is not mounted to the local machine unlike the other dirs/files.
* --name tag for container name 
* the last command is the image name that we built previosuly
