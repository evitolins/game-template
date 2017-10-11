Git Hooks
======================================================
To make sure our repos are free of issues, and setup consistently across all
our enviornments, we provide hooks to regulate certain Git activity.


Installation
---------------------------------------
Simply run `./utils/install-git-hooks` from the repo's root directory to ensure
all the latest git hooks are connected.

> After running the installation, those hooks that are installed will then be
automatically updated when changes are made to the repo.
> However, if new hooks are added to the `install-git-hooks` file, it will need to be
re-run.


Hooks
---------------------------------------

### Pre-Commit
...