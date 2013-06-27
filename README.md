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
Regular repositories:
It is necessary to set receive.denyCurrentBranch to ignore to set target repository branch to master.

Bare repositories:
It is necessary to set deploy.destination to the directory you want the updated code in. 

All custom configuration
---------------
The git configuration values are as follows:

    [deploy]
        scripttorun = script to run after the code is updated (Optional)
	destination = in a bare repository, the directory to update (Required for bare repositories [see above])
