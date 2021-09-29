# External repositories management documentation

## Overview

This documentation is mainly used to help teachers, creative content creators or admins to manage custom repositories on a Deadlock platform.


## What's a Deadlock challenges repository?


A Deadlock challenges repository consists of 2 main parts : 

- a **resources** folder which contains all of the challenges 
- a **registry** containing the images of each challenge


A typical Deadlock challenges repository structure would look something like that :

```
├── README.md
├── build
│   ├── build-image.sh
│   └── parse_yaml.sh
└── resources
    └── code_palindrome_test
        ├── Dockerfile
        ├── challenge.yaml
        ├── docs
        │   ├── ...
        ├── run.sh
        ├── src
        │   └── ...
        └── thumbnail.png
```


Also, you can take a look at [this template][template_repo]. It's a good example and a place to start from, feel free to copy all the files from it.

## See also

* [Maintainer's guide](maintainer-guide.md) if you're a challenges creator and would like to share them
* [Deadlock admin's guide](admin-guide.md) if you are a Deadlock instance administrator and would like to add a repository

[template_repo]: https://git.e-biz.fr/deadlock-public/deadlock-challenges-example