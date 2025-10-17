# LemiciIQ DevOps Exercise

## Part 1 : Version Control (Git & SSH):

## Difference between git pull vs git fetch:

- git fetch: It downloads changes from remote repository but does not merge them automatically.  
- git pull: It downloads and merges changes from the remote repository into your branch.


## Git Merge conflict example:
I created 2 branches(feature-A & feature-B) and made changes to the same file. When merging, git gave a following conflict:


```
Auto-merging code.txt
CONFLICT (add/add): Merge conflict in code.txt
Automatic merge failed; fix conflicts and then commit the result.

```


In order to perform this conflict I manually edited the file to keep both the changes:
"Hello from Feature-A and Feature-B"
and added the file to repository


## Part 2: Docker & Containerization: 

## Difference between Dockerfile, Docker Image & Docker Container:

- Dockerfile: This file contains step by step instructions/commands to build our application.
- Docker Image: It is portable package that contains our application, created using dockerfile.
- Docker Container: It is a running instance of our application. Docker containers are lightweight, ephimeral and portable in nature.

