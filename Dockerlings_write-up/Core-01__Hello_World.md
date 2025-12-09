# Core-01: Hello World
The execise for core-01 requires the person to verify that the Docker installation is working properly. How the exercise does so is by given a Dockerfile and the main objective is to modify it so it will be able to run a container that output "Hello Docker". First thing to do is to check the Dockerfile itself. 
## Initial Dockerfile
![](https://beta.appflowy.cloud/api/file_storage/0535e7ca-62b3-4f1c-b53c-bb4dd6534174/v1/blob/37fa952f%2D8d10%2D4b30%2Db7fd%2D8a3ab480f3a9/o909kfjfLs6VPzoW_80wnwG_B5ITkdekNvvrIDcxnWQ=.png)
Image 1: Dockerfile content
Based on the content of the Dockerfile, the first thing it will do is to use busybox, which is a stripdown implementation of around 400 commonly used UNIX commands. It removes most of the rarely used options that is available on the command itself for a very lightweight image of linux, as such it is commonly used for docker images for its low size image. After that, the docker will run a echo command line that will echo "Hello World". 

## Solving Steps
So the first thing to do for this exercise is to open up the dockerfile on a text editor. This is to change the command to echo "Hello Docker" instead of "Hello World". For this write-up, I will be using nano.
![](https://beta.appflowy.cloud/api/file_storage/0535e7ca-62b3-4f1c-b53c-bb4dd6534174/v1/blob/37fa952f%2D8d10%2D4b30%2Db7fd%2D8a3ab480f3a9/ozLVGheNilCcOeob0EUz9zDJkRZbqBwG92ts65LaH7w=.png)
Image 2: Changing the Dockerfile content
After done changing the content of the Dockerfile, the Dockerfile could be verify by using the available auto verifier on dockerlings itself to check.
![](https://beta.appflowy.cloud/api/file_storage/0535e7ca-62b3-4f1c-b53c-bb4dd6534174/v1/blob/37fa952f%2D8d10%2D4b30%2Db7fd%2D8a3ab480f3a9/obgFLmzMYjqaPit-YrkeeA20JXbYXqYGkwgQkjSCx6A=.png)
Image 3: Verifying the dockerfile exercise
With this, the dockerfile is verified to be correct and the expected result is given from the image. This marks the finish for the first exercise of dockerlings. 
P.S. : if you still get wrong answer when checking the Dockerfile, it could be that the verifier can't create the docker image because of getting denied permission to do so, as such you could run dockerlings with sudo privilage for the auto verify to work.
