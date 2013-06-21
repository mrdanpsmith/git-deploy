git-push-deploy
===============

Simple git post-receive hook designed to allow automated deploy of applications via git push.

The idea of this one is to make it so that you can run a simple callback when there's pushes to a remote git repository.

The hook is configurable using the same git configuration that git itself uses and requires only python scripting support in order to run.

The git configuration values are as follows:

    [postgit]
        destination = directory to deploy to (absolute path) (Required)
        temp_path = your temp directory (defaults to the system set temp directory) (Optional)
        script_to_run = the filename of the script in the build to run (Required)
        archive_format = the archive format to produce from the git revision (defaults to tar) (Optional)
        delete_archive = whether or not to delete the git archive created from the revision after extraction (defaults to True) (Optional)
        pattern = a regex pattern to compare against the refs being pushed and determine whether to run the deployment (defaults to "refs/heads/master") (Optional)
