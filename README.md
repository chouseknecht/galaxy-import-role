# galaxy-import-role

[![Build Status](https://travis-ci.org/chouseknecht/galaxy-import-role.svg?branch=master)](https://travis-ci.org/chouseknecht/galaxy-import-role)

Automate Galaxy role imports by using the Galaxy API directly, rather than the `ansible-galaxy` CLI.

## Requirements

Uses the [Ansible uri module](http://docs.ansible.com/ansible/uri_module.html) to make requests to the Galaxy API. In versions of Ansible prior to 2.1 this required httplib2. With newer versions of Anaible the uri module should just work.

Authentication to the Galaxy API requires a [GitHub personal access token](https://help.github.com/articles/creating-an-access-token-for-command-line-use/).


## Role Variables

galaxy_protocol 
> Set to *http* or *https*. Defaults to *https*.

galaxy_server
> The Galaxy server address. Defaults to *galaxy.ansible.com*. 

github_token
> Your GitHub personal access token.

github_repos
> List of repos with namespace, repo and reference attributes. The reference attribute is optional, and can be used to specify a GitHub branch.

galaxy_wait
> Whether or not to wait on the import results. Defaults to *true*.

galaxy_assert_success
> Whether or not to fail when an import fails. Used only when `galaxy_wait` is *true*. Defaults to *true*. 

## Dependencies

None.

## Examples

Run this role with the following example playbook: 

```
    - name: Auto import to galaxy
      hosts: localhost
      connection: local
      gather_facts: no
      roles:
        - role: galaxy-import
          github_token: < your GitHub personal access token here > 
          github_repos:
            - namespace: chouseknecht
              name: ansible-role-autoimport
```

## License

[Apache v2](http://apache.org/licenses/)


## Author 

[@chouseknecht](https://github.com/chouseknecht)
