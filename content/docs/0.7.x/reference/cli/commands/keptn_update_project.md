---
date: "2020-07-21T16:03:07+02:00"
title: "keptn update project"
slug: keptn_update_project
---
## keptn update project

Updates an existing Keptn project

### Synopsis

Updates an existing Keptn project with the provided name. 
Updating a shipyard file is not possible.

By executing the *update project* command, Keptn will add the provided upstream repository to the existing internal Git repository that is used to maintain all project-related resources. 
To upstream this internal Git repository to a remote repository, the Git user (*--git-user*), an access token (*--git-token*), and the remote URL (*--git-remote-url*) are required.

For more information about updating projects or upstream repositories, please go to [Manage Keptn](https://keptn.sh/docs/0.7.x/manage/)


```
keptn update project PROJECTNAME --git-user=GIT_USER --git-token=GIT_TOKEN --git-remote-url=GIT_REMOTE_URL [flags]
```

### Examples

```
keptn update project PROJECTNAME --git-user=GIT_USER --git-token=GIT_TOKEN --git-remote-url=GIT_REMOTE_URL
```

### Options

```
  -r, --git-remote-url string   The remote url of the upstream target
  -t, --git-token string        The git token of the git user
  -u, --git-user string         The git user of the upstream target
  -h, --help                    help for project
```

### Options inherited from parent commands

```
      --mock                 mocking of server communication - ATTENTION: your commands will not be sent to the keptn server
  -q, --quiet                suppress debug and info output
      --suppress-websocket   disables websocket communication - use the ID of Keptn context (if provided) for checking the result of your command
  -v, --verbose              verbose logging
```

### SEE ALSO

* [keptn update](../keptn_update/)	 - 

###### Auto generated by spf13/cobra on 21-Jul-2020