# UCLALib Ansible Role: Apache HTTPD

Deploys Apache HTTPD on RHEL servers

This role installs and configures a default set-up of an Apache HTTPD web server.

It uses a standard http.conf file and creates an empty vhosts directory at `/etc/httpd/vhosts`.

Include this role as part of a play to configure your base web server. Then have your application-specific role set-up the necessary virtual host configuration.

## Dependencies

For a RHEL system, it must already be subscribed to Red Hat and base repositories enabled via `ansible_uclalib_role_rhel7repos`

## Variables

* `apache_packages` - list the httpd related packages to be installed in this role

* `httpd_base_path` - defines the httpd base path (usually set to /etc/httpd)

* `httpd_conf_path` - defines the httpd configuration file path

* `ssl_conf_path` - defines the path to the directory where the ssl.conf file is stored

* `use_ssl` - defines if the ssl.conf file should be configured to Listen on port 443 (`yes` or `no` - default is `yes` )

## SSL Support

SSL support enabled only configures HTTPD to listen on ports 80 and 443. This role does not perform any certificate set-up. You'll need to do this separately in your application-specific role during the virtual host configuration.

## Example Usage in a Play

```
- name: uclalib_example_play.yml
  sudo: true
  hosts: test

    roles:
      - { role: uclalib_role_apache }
```
