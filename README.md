git-deploy
===============
This is a git post-receive python hook designed to allow automated deploy of applications via git push.

It is also designed so that you can run a simple callback when there are pushes to a git repository.

Requirements
---------------
* python
* git repository

Installation
---------------
Copy post-receive into your git hooks directory.

Configure as per the instructions below.

Configuration
---------------
**Regular repositories:**

Change the repository configuration property receive.denyCurrentBranch to ignore.
```bash
git config --local receive.denyCurrentBranch ignore
```
See [this article](https://www.kernel.org/pub/software/scm/git/docs/git-config.html) for more details on how to configure git.

Start with an empty repository or ensure the branch is set to master.

**Bare repositories:**

Configure deploy.destination to the directory you want the updated code in. 
```bash
git config --local deploy.destination /var/www/public/mysite.com
```
See [this article](https://www.kernel.org/pub/software/scm/git/docs/git-config.html) for more details on how to configure git.

**Deploy Scripts:**

If you want to do more than simply send code updates, you can configure the post-receive hook so that a single deploy script runs.

The script will run with the working directory as the repository root and should be marked as executable.

```bash
git config --local deploy.script deploy.py
```
See [this article](https://www.kernel.org/pub/software/scm/git/docs/git-config.html) for more details on how to configure git.

Custom Configuration Values
---------------
The git configuration values are as follows:

    [deploy]
        script = script to run after the code is updated (Optional)
        destination = in a bare repository, the directory to update (Required for bare repositories [see above])

Troubleshooting
---------------
**The post-receive hook is not executing on push.**

Make sure that the post-receive hook is marked as executable according to your operating system (chmod +x on unix-like systems).

**My deployment script is not executing on push.**

Make sure that the deployment script is marked as executable according to your operating system (chmod +x on unix-like systems).

**The remote push refuses to update the target server.**

Make sure that the repository has receive.denyCurrentBranch set to ignore.
