# Mirror Test

This repository demonstrates mirroring a repository between different GIT hosts. The Supplier and Client repositories can be hosted internally but the Shared repository needs to be accessible to both parties.

Supplier: [Gitlab](https://gitlab.com/jdeathe/mirror-test)

Shared: [Github](https://github.com/jdeathe/mirror-test)

Client: [Bitbucket](https://bitbucket.org/jdeathe/mirror-test)

## Mirror from Supplier to Shared remote

1. Create the new Shared repository on Github.

2. Create a bare checkout of the Supplier (Source) repository. 

  ```
  $ cd /tmp
  $ git clone --bare git@github.com:jdeathe/mirror-test.git
  ```

3. Add the `shared` remote and mirror the Supplier to the Shared repository.

  ```
  $ cd /tmp/mirror-test.git
  $ git remote add shared git@github.com:jdeathe/mirror-test.git
  $ git push --mirror git@github.com:jdeathe/mirror-test.git
  ```

4. Clean up.

  ```
  $ cd -
  $ rm -rf /tmp/mirror-test.git
  ```

### Add `shared` remote to Supplier clone.

Assuming you're working directory for projects is `~/Projects` add a remote to the Shared repository named `shared`. This will allow you to push/pull to the remote (shared) branches using the remote name. i.e. `git push shared dev`.

```
$ cd ~/Projects/
$ git clone git@gitlab.com:jdeathe/mirror-test.git
$ git remote add shared git@github.com:jdeathe/mirror-test.git
```

## Mirror from Shared to Client remote

1. Create a new Client (internal) repository.

2. Create a (temporary) bare clone of the Shared repository.

  ```
  $ cd /tmp
  $ git clone --bare git@github.com:jdeathe/mirror-test.git
  ```

3. Mirror to the Client repository and clean up.

  ```
  $ cd /tmp/mirror-test.git
  $ git push --mirror git@bitbucket.org:jdeathe/mirror-test.git
  ```

4. Clean up.

  ```
  $ cd -
  $ rm -rf /tmp/mirror-test.git
  ```

### Add `shared` remote to Client clone.

Assuming you're working directory for projects is `~/Projects` add a remote to the Shared repository named `shared`. This will allow you to push/pull to the remote (shared) branches using the remote name. i.e. `git push shared dev`.

```
$ cd ~/Projects/
$ git clone git@bitbucket.org:jdeathe/mirror-test.git
$ git remote add shared git@github.com:jdeathe/mirror-test.git
```

