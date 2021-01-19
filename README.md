egeneralov.ejabberd
===================

Provide ejabberd installation and docker-compose for local development.

Requirements
------------

- debian-powered machine

Role Variables
--------------

- **version**: string, default `20.12`
- **deployment_type**: string, oneof `[deb, docker]`, default `docker`
- **base_path**: string, default `"{{ _base_path_[deployment_type] }}"`
- **_base_path_**:
  - **deb**: string, default `/opt/ejabberd/conf`
  - **docker**: string, default `/home/ejabberd/conf/`
- **users**: dict
  - **username**: **password**
- **configuration**: dict, will be placed as `ejabberd.yml`
- **docker_volumes**: list, volumes for docker container, default:
  - `/opt/ejabberd/conf/ejabberd.yml:/home/ejabberd/conf/ejabberd.yml`
  - `ejabberd:/home/ejabberd/database`

Dependencies
------------

if `deployment_type == docker`:
- egeneralov.docker
- egeneralov.python
- egeneralov.glauth

Example Playbook
----------------

- [tests/test.yml](tests/test.yml) with `deployment_type=deb`, as system-wide installation
- [tests/ldap.yml](tests/ldap.yml)

License
-------

MIT

Author Information
------------------

Eduard Generalov <eduard@generalov.net>
