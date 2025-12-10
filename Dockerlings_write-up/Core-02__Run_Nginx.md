# Core-02: Run Nginx
The exercise core-02 require the user to pull and run the official nginx image, expose the port 80 to the network and verify it locally. This exercise teaches about how to pull docker images from docker hub and to run the docker image with specific requirement based on the user need. This time, there is no given Dockerfile for this exercise, but the question itself already give the hint for the exercise. 
## Solving steps
In docker, you could use an images available publicly in docker hub to be run in your machine. As such, the first step for this exercise is to pull the nginx docker image by using `docker pull nginx`.` `
You can check the images that is currently in the local machine by using `docker images`.
After confirming the nginx image is ready, you can run it using docker run command and supplying some flags based on the exercise requirements. As such, the command for running the nginx image will look like this: `docker run -d —name my-nginx -p 8080:80 nginx`. The flags used in the command are -d, which is use to mean that the docker is run as detached mode, —name is used to specify the name of the container which in this case is my-nginx and -p which used to specify the port for the container to use in the format of HOST_PORT:CONTAINER_PORT.
After done running the docker, the website could be check by using curl or opening the browser to `http://localhost:8080` to verify the existence.
![](https://beta.appflowy.cloud/api/file_storage/0535e7ca-62b3-4f1c-b53c-bb4dd6534174/v1/blob/77d46c07%2D2d3f%2D47cf%2Db988%2D59417eee5f2c/Odv3UKCT-7Jo7hOqniCcuf-LZqh1JIPVVULYZBhY3bE=.png)
 With this, the exercise is completed and core-02 is done.

