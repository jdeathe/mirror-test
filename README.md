# Mirror Test

This repository demonstrates mirroring between different GIT hosts.

Source: [Gitlab](https://gitlab.com/jdeathe/mirror-test)

Shared: [Github](https://github.com/jdeathe/mirror-test)

Client: [Bitbucket](https://bitbucket.org/jdeathe/mirror-test)

## Mirror to Github remote

1. Create the new Shared repository on Github

2. On a clean checkout of the Source repository with only the master and dev branches add the `github` remote and mirror the Source to the Shared repository. 

  ```
  $ git remote add github git@github.com:jdeathe/mirror-test.git
  $ git push --mirror github
  ```

## Client's private mirror

1. Create a new Client (internal) repository.

2. Create a (temporary) bare clone of the Shared repository.

  ```
  $ cd /tmp
  $ git clone --bare git@github.com:jdeathe/mirror-test.git
  ```

3. Mirror to the Client repository.

  ```
  $ cd /tmp/mirror-test.git
  $ git push --mirror git@bitbucket.org:jdeathe/mirror-test.git
  ```

