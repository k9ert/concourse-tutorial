this is based on:
https://concourse-ci.org/getting-started.html

# list of resources
* https://github.com/concourse/git-resource



# list of resource-types
https://resource-types.concourse-ci.org/

# notes

This is the way to avoid private_key in plain-text:

```
resources:
- name: repo
  type: git
  source:
    uri: git@github.com:concourse/examples.git
    branch: master
    private_key: ((github_private_key))
```

```bash
fly -t tutorial set-pipeline -p my-pipeline -c pipeline.yml \
  --var github_private_key="$(cat ~/.ssh/id_rsa)"
```
