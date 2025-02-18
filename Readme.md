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
    private_key_passphrase: ((github_private_key_passphrase))
```

```bash
fly -t tutorial set-pipeline -p my-pipeline -c pipeline.yml \
  --var github_private_key="$(cat ~/.ssh/id_rsa)" --var github_private_key_passphrase="yourPassphraseHere"
```
