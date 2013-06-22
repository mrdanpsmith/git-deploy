git-deploy
===============

Simple git post-receive hook designed to allow automated deploy of applications via git push.

The idea of this one is to make it so that you can run a simple callback when there's pushes to a remote git repository.

The hook is configurable using the same git configuration that git itself uses and requires only python scripting support in order to run.

The git configuration values are as follows:

    [deploy]
        scripttorun = the filename of a deployment script to run after the code is updated (Optional)
        refpattern = a regex pattern to compare against the refs being pushed and determine whether its actionable (defaults to "refs/heads/master") (Optional)
