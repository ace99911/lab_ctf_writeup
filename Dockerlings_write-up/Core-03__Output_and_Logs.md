# Core-03: Output and Logs
The exercise for core-03 require the user to retrieve the logs from a docker container run in the machine. This teaches the user on the commands that will be used for retrieving the logs file of the docker that have been run in the container. For this exercise, the dockerfile is already available on the file location of core-03. The user just require to build and run the docker container to collect the log from it

## Initial dockerfile
![](https://beta.appflowy.cloud/api/file_storage/0535e7ca-62b3-4f1c-b53c-bb4dd6534174/v1/blob/92313b6d%2D01d5%2D431c%2D9d40%2D128c3682cf97/CLryhYtGZNCMjnCSZTQpbjnbRgh1Lsnbh7uJlR22Q4A=.png)
Based on the dockerfile given, this container will retieve the busybox docker image as the base image for this container. After that it wil run a sh -c command that will take the echo command to print out 'Starting process...', 'Process is running', and 'Process finished.' with a 0.1s sleep between each echo.
## Solving steps
The first thing to do is to for this exercise is to build and run the docker container. Based on the knowledge from the earlier exercises, the command used for building and running the docker container should be` docker build -t logging-app .` and `docker run -d --name my-logger logging-app` repectively.

After done running the container, the user are required to retrieve the exercise's log. The main way to retrieve such log is through the `docker logs` command. For this exercise, only the basic command of docker logs will be used and no extra options is needed. As such, the command that will be used to retrieve the logs is `docker logs my-logger > logs.txt` .  This command will retrieve the log of the container and then stored the log file in logs.txt. The picture below shows the expected result from the container log.
![](https://beta.appflowy.cloud/api/file_storage/0535e7ca-62b3-4f1c-b53c-bb4dd6534174/v1/blob/92313b6d%2D01d5%2D431c%2D9d40%2D128c3682cf97/ts_0lNHkYdSPaWACFCkNyX26FFfQrVsh4dFw2WCJYo8=.png)
 After that, the task should be completed and the user could check with the auto verifier to verify the result.
![](https://beta.appflowy.cloud/api/file_storage/0535e7ca-62b3-4f1c-b53c-bb4dd6534174/v1/blob/92313b6d%2D01d5%2D431c%2D9d40%2D128c3682cf97/XvEh1EXmpbyS_4lb3k2CJsMzuZiB67rG4P6zEgjyA8g=.png)
With this, the logs.txt have been verify and the exercise is completed. This marks the end of core-03 exercise on how to retrieve log from a container.
