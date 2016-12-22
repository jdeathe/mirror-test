# Mirror Test

This repository demonstrates mirroring between different GIT hosts.

Source: [Gitlaba](https://gitlab.com/jdeathe/mirror-test)

Shared: [Github](https://github.com/jdeathe/mirror-test)

## Mirror to Github remote

1. Create the new Shared repository on Github

2. On a clean checkout of the Source repository with only the master and dev branches add the `github` remote and mirror the Source to the Shared repository. 

```
git remote add github git@github.com:jdeathe/mirror-test.git
git push --mirror github
```

