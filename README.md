# galaxy-import-role

Automate importing one or more roles to Galaxy. By-passes the Galaxy CLI and uses the API directly.


## Requirements

Uses the Ansible uri module to make requests to the Galaxy API. In versions of Ansible prior to 2.1 this required httplib2. 

Authentication to Galaxy via its API requires a [GitHub personal access token](https://help.github.com/articles/creating-an-access-token-for-command-line-use/).


## Role Variables

galaxy_protocol 
> Set to *http* or *https*. Defaults to *https*.

galaxy_server
> The Galaxy server address. Defaults to *galaxy.ansible.com*. 

github_token
> Your GitHub personal access token.

github_repos
> List of repos with namespace, repo and reference attributes. The reference attribute is optionally. Set to a valid GitHub branch name. 

galaxy_wait
> Whether or not to wait on the import results. Defaults to *yes*.

galaxy_assert_success
> Whether or not to fail when an import fails. Used only when `galaxy_wait` is *true*. Defaults to *yes*. 

## Dependencies

None.

## Example Playbook

Run this role with the following example playbook: 

```
    - name: Auto import to galaxy
      hosts: localhost
      connection: local
      gather_facts: no
      vars:
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
