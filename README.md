# LemiciIQ DevOps Exercise

## Difference between git pull vs git fetch:

- git fetch: It downloads changes from remote repository but does not merge them automatically.  
- git pull: It downloads and merges changes from the remote repository into your branch.


## Git Merge conflict example:
I created 2 branches(feature-A & feature-B) and made changes to the same file. When merging, git gave a following conflict:


```
<<<<<<< HEAD
Hello from Feature A
=======
Hello from Feature B
>>>>>>> feature-B 
```


In order to perform this conflict I manually edited the file to keep both the changes:
"Hello from Feature-A and Feature-B"
and added the file to repository

