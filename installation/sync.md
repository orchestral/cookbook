## Sync application skeleton

> Disclaimer: This is an advanced method to keep your application up to date with upstream. However you can skip this part if you not to familiar with Git or merging conflict.

Many time keeping the application skeleton up to date with [orchestra/platform](https://github.com/orchestral/platform) is such a PITA, I would recommend doing the following if you're using GIT as your source control.

First, if you already commit added "patio" project to Git, you need to create an orphan branch so we can have a clean branch that we stage merging updates from `orchestra/platform` when we fetch updates.

    $ git checkout --orphan skeleton
    
Next, let's commit our base skeleton.

    $ git commit -sam "Initial base skeleton"

Now, let's add `orchestra/platform` as a remote.

    $ git remote add orchestra git@github.com:orchestral/platform.git
    
Before fetching remotes, we should disable fetching tags. You can set this permanently per project via:

    $ git config remote.orchestra.tagopt --no-tags
    
You should also disable pushing any changes to `orchestra` remote.

    $ git remote set-url --push orchestra no_push

### Fetching updates

Once everything is ready, we can start fetching the remote:

    $ git fetch orchestra
    
### Merge updates

To merge updates, it better to use `--squash` to merge all changes into single commit.

    $ git merge --squash orchestra/3.1
    
If you happen to see the following:

```
➜  patio git:skeleton ✓ gm --squash orchestra/3.1
error: The following untracked working tree files would be overwritten by merge:
	public/packages/.gitkeep
Please move or remove them before you can merge.
Aborting
```

Just delete the file and you're set to go

    $ rm public/packages/.gitkeep
    
Let's try again:

```
➜  patio git:skeleton ✓ gm --squash orchestra/3.1
Auto-merging resources/config/auth.php
CONFLICT (add/add): Merge conflict in resources/config/auth.php
Auto-merging composer.json
CONFLICT (add/add): Merge conflict in composer.json
Squash commit -- not updating HEAD
Automatic merge failed; fix conflicts and then commit the result.
```

Two files has merge conflict, this is typical when you're using this approach (which is why it's mark as advanced). Manually merge the conflict and commit the code.

    $ git add .
    $ git commit -sam "Update skeleton (with update to ...)"
    
As an example:

```
➜  patio git:skeleton ✗ gc -sam "Update skeleton with update to auth config"
[skeleton 5002b82] Update skeleton with update to auth config
 5 files changed, 359 insertions(+)
 create mode 100644 .travis.yml
 create mode 100644 docs/changes.md
 create mode 100644 public/packages/.gitkeep
 create mode 100644 readme.md
```

You might see that this approach also add `.travis.yml`, `docs/changes.md` and `readme.md`. You can either keep this file or remove it

    $ git rm .travis.yml docs/changes.md readme.md
    $ git commit -sam "Remove irrelevant skeleton files"
    
> Do remember each time we merge `orchestra` remote, these files will also be included.

### Applying changes to your code

Now, remember `skeleton` branch is an orphan branch. We would need to merge this changes to our working branch:

    $ git checkout master
    $ git merge skeleton
