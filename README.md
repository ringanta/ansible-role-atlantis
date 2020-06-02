Atlantis
=========

Ansible role to setup Atlantis which secured with Caddy automatic HTTPS and Oauth2 Proxy with Github as identity provider.

Requirements
------------

This role is developed and only tested on Ansible 2.9

Role Variables
--------------

- `atlantis_port` - Port number where Atlantis run.
- `atlantis_url` - URL of the Atlantis. For example, _https://23.21.24.224.xip.io_. **Required**
- `atlantis_domain` - Domain name of the Atlantis. For example, `23.21.24.224.xip.io`. **Required**
- `atlantis_gh_user` - Github username used by Atlantis to interact with Github. **Required**
- `atlantis_gh_token` - Github token of the Github username that is used by Atlantis. **Required**
- `atlantis_gh_webhook_secret` - Github webhook secret used by Atlantis to verify incoming webhook from Github. **Required**
- `atlantis_repo_allowlist` - List of Github repository monitored by Atlantis. **Required**
- `atlantis_default_tf_version` - Default terraform version used by Atlantis.
- `oauth2_proxy_port` - Port number where Oauth2 Proxy run.
- `oauth2_proxy_cookie_secret` - Secret that used by Oauth2 Proxy. It can be generated using ` python -c 'import os,base64; print(base64.urlsafe_b64encode(os.urandom(16)).decode())'`. **Required**
- `oauth2_client_id` - Github Oauth client ID. **Required**
- `oauth2_client_secret` - Github Oauth client secret. **Required**
- `oauth2_proxy_gh_org` - Github organization that is allowed to access Atlantis. **Required**
- `oauth2_proxy_gh_team` - Github team that is allow to access Atlantis. Multiple team is separated by comma. **Required**
- `oauth2_proxy_version` - Version of Oauth2 Proxy.
- `oauth2_proxy_binary_url` - URL from which Oauth Proxy downloaded.

Dependencies
------------

This role has no dependency to other role

Example Playbook
----------------

```yml
---
- hosts: all
  roles:
    - role: ringanta.atlantis
      atlantis_domain: example.com
      atlantis_url: https://example.com
      atlantis_repo_allowlist: github.com/ringanta-demo-atlantis/*
      atlantis_gh_user: ringanta
      atlantis_gh_token: 11111aaaaaaaaaaaaaaaaaa111111
      atlantis_gh_webhook_secret: github_webhook_secret
      oauth2_proxy_cookie_secret: cookie_secret
      oauth2_proxy_client_id: oauth_client_id
      oauth2_proxy_client_secret: oauth_client_secret
      oauth2_proxy_gh_org: ringanta-demo-atlantis
      oauth2_proxy_gh_team: team-terraform
```

License
-------

MIT

Author Information
------------------

[Roy Ginting](https://ringanta.id/)
