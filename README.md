# buckler-external-repo

We recommend that if you are using Buckler for your project, you include it as
a submodule in your own repo. This repo is an example of how to do so. For more
information on submodules, read the descriptions here:
[Git Submodules](https://git-scm.com/book/en/v2/Git-Tools-Submodules)


### Setting up the new repo

First clone your repository locally. Then set up the folders:

```
$ mkdir software
$ cd software/
$ mkdir apps/
```

Next, create the submodule:

```
$ cd software/
$ git submodule add https://github.com/lab11/buckler.git
$ git submodule update --init --recursive
```

Be sure to create a .gitignore like Buckler does:

```
$ cd software/
$ cp buckler/software/.gitignore .
```

Next, create a basic application:

```
$ cd software/apps/
$ mkdir blink
$ cd blink/
$ cp ../../buckler/software/apps/blink/* .
```

And edit the folder paths within it so they point to the correct locations:

```
NRF_BASE_DIR = ../../buckler/software/nrf5x-base/
```
```
include ../../buckler/software/boards/buckler_revB/Board.mk
```

The application should now build correctly and flash onto a board. For future
applications, you can copy the Makefile used in `blink/` into the new
application directories in order to compile them.

Be sure to add all files (including the submodule directory) and commit them to
your repository.


### Dealing with problems

If you ever find that the submodule folder is empty (no files inside it) or
out of date, there is one command that will fix it:

```
$ git submodule update --init --recursive
```

If you need to update the submodule, `cd` into it, and do a `git checkout` of
the correct branch (likely master), and do a `git pull` just as if you were in
a normal directory. Once the submodule is updated, `cd` back up into your own
repository and you will see that the submodule directory is marked as changed
in git. You can `git add` it and `git commit` it to update it on Github.

After you've committed it, team members will need to update their own local
repositories by running `git submodule update --init --recursive`.

