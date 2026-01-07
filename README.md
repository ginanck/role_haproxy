<!-- DOCSIBLE START -->
# Ansible Role: role_haproxy


role_haproxy to install haproxy


## Table of Contents

- [Requirements](#requirements)
- [Dependencies](#dependencies)
- [Role Variables](#role-variables)
- [Task Overview](#task-overview)
- [Example Playbook](#example-playbook)
- [Documentation Maintenance](#documentation-maintenance)
- [License](#license)
- [Author Information](#author-information)

## Requirements



- Ansible >= 2.9


- Supported platforms:
  - Ubuntu (jammy, noble)
  - Debian (bullseye, bookworm)
  - AlmaLinux (9, 10)
  - RockyLinux (9.0, 10)



## Dependencies


This role requires the following roles and collections:




  
    
  

  
    
  

  
    
  

  
    
  



**Roles:**

- [role_base](https://github.com/ginanck/role_base.git) (version: master)




**Collections:**

- `community.docker` (>= 4.8.1)

- `community.general` (>= 6.6.1)

- `ansible.posix` (>= 1.5.4)



To install all dependencies:
```bash
ansible-galaxy install -r meta/install_requirements.yml
```


## Role Variables



### File: `defaults/main.yml`

| Variable | Default Value | Description |
|----------|---------------|-------------|
| `haproxy_config_dir` | `/etc/haproxy` | None |
| `haproxy_destination_config_path` | `{{ haproxy_config_dir }}/haproxy.cfg` | None |
| `haproxy_log_file` | `/var/log/haproxy.log` | None |
| `haproxy_logrotate_file` | `/etc/logrotate.d/haproxy` | None |
| `haproxy_whitelist_file_dir` | `{{ haproxy_config_dir }}/whitelist` | None |
| `haproxy_whitelist_file_name` | `` | None |
| `haproxy_cert_dir` | `{{ haproxy_config_dir }}/certs` | None |
| `haproxy_cert_name` | `` | None |
| `haproxy_global` | `{}` | None |
| `haproxy_global.log` | `[]` | None |
| `haproxy_global.log.0` | `{}` | None |
| `haproxy_global.log.0.address` | `127.0.0.1` | None |
| `haproxy_global.log.0.facility` | `local2` | None |
| `haproxy_global.log.0.max_level` | `info` | None |
| `haproxy_global.log.0.min_level` | `alert` | None |
| `haproxy_global.tune_ssl_default_dh_param` | `2048` | None |
| `haproxy_global.chroot` | `/var/lib/haproxy` | None |
| `haproxy_global.pidfile` | `/var/run/haproxy.pid` | None |
| `haproxy_global.maxconn` | `4000` | None |
| `haproxy_global.user` | `haproxy` | None |
| `haproxy_global.group` | `haproxy` | None |
| `haproxy_global.daemon` | `True` | None |
| `haproxy_global.stats_socket` | `[]` | None |
| `haproxy_global.stats_socket.0` | `{}` | None |
| `haproxy_global.stats_socket.0.path` | `/var/lib/haproxy/stats` | None |
| `haproxy_defaults` | `{}` | None |
| `haproxy_defaults.mode` | `http` | None |
| `haproxy_defaults.log` | `[]` | None |
| `haproxy_defaults.log.0` | `{}` | None |
| `haproxy_defaults.log.0.global` | `True` | None |
| `haproxy_defaults.option` | `[]` | None |
| `haproxy_defaults.option.0` | `{}` | None |
| `haproxy_defaults.option.0.name` | `httplog` | None |
| `haproxy_defaults.option.1` | `{}` | None |
| `haproxy_defaults.option.1.name` | `dontlognull` | None |
| `haproxy_defaults.option.2` | `{}` | None |
| `haproxy_defaults.option.2.name` | `http-server-close` | None |
| `haproxy_defaults.option.3` | `{}` | None |
| `haproxy_defaults.option.3.name` | `forwardfor` | None |
| `haproxy_defaults.option.3.params` | `except 127.0.0.0/8` | None |
| `haproxy_defaults.option.4` | `{}` | None |
| `haproxy_defaults.option.4.name` | `redispatch` | None |
| `haproxy_defaults.retries` | `3` | None |
| `haproxy_defaults.timeout` | `[]` | None |
| `haproxy_defaults.timeout.0` | `{}` | None |
| `haproxy_defaults.timeout.0.name` | `http-request` | None |
| `haproxy_defaults.timeout.0.value` | `10s` | None |
| `haproxy_defaults.timeout.1` | `{}` | None |
| `haproxy_defaults.timeout.1.name` | `queue` | None |
| `haproxy_defaults.timeout.1.value` | `1m` | None |
| `haproxy_defaults.timeout.2` | `{}` | None |
| `haproxy_defaults.timeout.2.name` | `connect` | None |
| `haproxy_defaults.timeout.2.value` | `10s` | None |
| `haproxy_defaults.timeout.3` | `{}` | None |
| `haproxy_defaults.timeout.3.name` | `client` | None |
| `haproxy_defaults.timeout.3.value` | `1m` | None |
| `haproxy_defaults.timeout.4` | `{}` | None |
| `haproxy_defaults.timeout.4.name` | `server` | None |
| `haproxy_defaults.timeout.4.value` | `1m` | None |
| `haproxy_defaults.timeout.5` | `{}` | None |
| `haproxy_defaults.timeout.5.name` | `http-keep-alive` | None |
| `haproxy_defaults.timeout.5.value` | `10s` | None |
| `haproxy_defaults.timeout.6` | `{}` | None |
| `haproxy_defaults.timeout.6.name` | `check` | None |
| `haproxy_defaults.timeout.6.value` | `10s` | None |
| `haproxy_defaults.maxconn` | `3000` | None |
| `haproxy_listen` | `[]` | None |
| `haproxy_listen.0` | `{}` | None |
| `haproxy_listen.0.name` | `http_health_check` | None |
| `haproxy_listen.0.mode` | `http` | None |
| `haproxy_listen.0.monitor_uri` | `/haproxy` | None |
| `haproxy_listen.0.bind` | `[]` | None |
| `haproxy_listen.0.bind.0` | `{}` | None |
| `haproxy_listen.0.bind.0.address` | `127.0.0.1` | None |
| `haproxy_listen.0.bind.0.port` | `8000` | None |
| `haproxy_listen.0.option` | `[]` | None |
| `haproxy_listen.0.option.0` | `{}` | None |
| `haproxy_listen.0.option.0.name` | `dontlognull` | None |
| `haproxy_listen.0.option.1` | `{}` | None |
| `haproxy_listen.0.option.1.name` | `httpchk` | None |
| `haproxy_listen.1` | `{}` | None |
| `haproxy_listen.1.name` | `stats` | None |
| `haproxy_listen.1.mode` | `http` | None |
| `haproxy_listen.1.bind` | `[]` | None |
| `haproxy_listen.1.bind.0` | `{}` | None |
| `haproxy_listen.1.bind.0.address` | `127.0.0.1` | None |
| `haproxy_listen.1.bind.0.port` | `9000` | None |
| `haproxy_listen.1.stats` | `{}` | None |
| `haproxy_listen.1.stats.enable` | `True` | None |
| `haproxy_listen.1.stats.hide_version` | `True` | None |
| `haproxy_listen.1.stats.scope` | `[]` | None |
| `haproxy_listen.1.stats.scope.0` | `.` | None |
| `haproxy_listen.1.stats.uri` | `/admin?stats` | None |
| `haproxy_listen.1.stats.realm` | `HAProxy\ Statistics` | None |
| `haproxy_listen.1.stats.auth` | `[]` | None |
| `haproxy_listen.1.stats.auth.0` | `{}` | None |
| `haproxy_listen.1.stats.auth.0.login` | `admin-user` | None |
| `haproxy_listen.1.stats.auth.0.password` | `password123` | None |
| `haproxy_listen.1.stats.refresh` | `5s` | None |
| `haproxy_frontend` | `[]` | None |
| `haproxy_frontend.0` | `{}` | None |
| `haproxy_frontend.0.name` | `main-http` | None |
| `haproxy_frontend.0.mode` | `http` | None |
| `haproxy_frontend.0.bind` | `[]` | None |
| `haproxy_frontend.0.bind.0` | `{}` | None |
| `haproxy_frontend.0.bind.0.address` | `127.0.0.1` | None |
| `haproxy_frontend.0.bind.0.port` | `5001` | None |
| `haproxy_frontend.0.bind.1` | `{}` | None |
| `haproxy_frontend.0.bind.1.address` | `127.0.0.1` | None |
| `haproxy_frontend.0.bind.1.port` | `5002` | None |
| `haproxy_frontend.0.backlog` | `10000` | None |
| `haproxy_frontend.0.use_backend` | `[]` | None |
| `haproxy_frontend.0.use_backend.0` | `{}` | None |
| `haproxy_frontend.0.use_backend.0.name` | `app` | None |
| `haproxy_frontend.0.use_backend.0.condition` | `!{ ssl_fc }` | None |
| `haproxy_frontend.0.default_backend` | `app` | None |
| `haproxy_frontend.1` | `{}` | None |
| `haproxy_frontend.1.name` | `main-https` | None |
| `haproxy_frontend.1.mode` | `http` | None |
| `haproxy_frontend.1.bind` | `[]` | None |
| `haproxy_frontend.1.bind.0` | `{}` | None |
| `haproxy_frontend.1.bind.0.address` | `127.0.0.1` | None |
| `haproxy_frontend.1.bind.0.port` | `5003` | None |
| `haproxy_frontend.1.option` | `[]` | None |
| `haproxy_frontend.1.option.0` | `{}` | None |
| `haproxy_frontend.1.option.0.name` | `contstats` | None |
| `haproxy_frontend.1.option.1` | `{}` | None |
| `haproxy_frontend.1.option.1.name` | `http-server-close` | None |
| `haproxy_frontend.1.option.2` | `{}` | None |
| `haproxy_frontend.1.option.2.name` | `httplog` | None |
| `haproxy_frontend.1.timeout` | `[]` | None |
| `haproxy_frontend.1.timeout.0` | `{}` | None |
| `haproxy_frontend.1.timeout.0.name` | `client` | None |
| `haproxy_frontend.1.timeout.0.value` | `300s` | None |
| `haproxy_frontend.1.timeout.1` | `{}` | None |
| `haproxy_frontend.1.timeout.1.name` | `http-keep-alive` | None |
| `haproxy_frontend.1.timeout.1.value` | `1s` | None |
| `haproxy_frontend.1.timeout.2` | `{}` | None |
| `haproxy_frontend.1.timeout.2.name` | `http-request` | None |
| `haproxy_frontend.1.timeout.2.value` | `15s` | None |
| `haproxy_frontend.1.timeout.3` | `{}` | None |
| `haproxy_frontend.1.timeout.3.name` | `tarpit` | None |
| `haproxy_frontend.1.timeout.3.value` | `60s` | None |
| `haproxy_frontend.1.capture` | `[]` | None |
| `haproxy_frontend.1.capture.0` | `{}` | None |
| `haproxy_frontend.1.capture.0.type` | `cookie` | None |
| `haproxy_frontend.1.capture.0.name` | `JSESSIONID` | None |
| `haproxy_frontend.1.capture.0.len` | `32` | None |
| `haproxy_frontend.1.capture.1` | `{}` | None |
| `haproxy_frontend.1.capture.1.type` | `request header` | None |
| `haproxy_frontend.1.capture.1.name` | `Host` | None |
| `haproxy_frontend.1.capture.1.len` | `15` | None |
| `haproxy_frontend.1.monitor_uri` | `/haproxy` | None |
| `haproxy_frontend.1.acl` | `[]` | None |
| `haproxy_frontend.1.acl.0` | `{}` | None |
| `haproxy_frontend.1.acl.0.name` | `is_root` | None |
| `haproxy_frontend.1.acl.0.fetch` | `path -i  /` | None |
| `haproxy_frontend.1.http_request` | `[]` | None |
| `haproxy_frontend.1.http_request.0` | `{}` | None |
| `haproxy_frontend.1.http_request.0.action` | `set-header` | None |
| `haproxy_frontend.1.http_request.0.params` | `X-Forwarded-Proto http` | None |
| `haproxy_frontend.1.http_request.0.condition` | `!{ ssl_fc }` | None |
| `haproxy_frontend.1.redirect` | `[]` | None |
| `haproxy_frontend.1.redirect.0` | `{}` | None |
| `haproxy_frontend.1.redirect.0.type` | `scheme` | None |
| `haproxy_frontend.1.redirect.0.value` | `https` | None |
| `haproxy_frontend.1.redirect.0.code` | `301` | None |
| `haproxy_frontend.1.redirect.0.option` | `drop-query` | None |
| `haproxy_frontend.1.redirect.0.condition` | `!{ ssl_fc }` | None |
| `haproxy_frontend.1.use_backend` | `[]` | None |
| `haproxy_frontend.1.use_backend.0` | `{}` | None |
| `haproxy_frontend.1.use_backend.0.name` | `app` | None |
| `haproxy_frontend.1.use_backend.0.condition` | `!{ ssl_fc }` | None |
| `haproxy_backend` | `[]` | None |
| `haproxy_backend.0` | `{}` | None |
| `haproxy_backend.0.name` | `app` | None |
| `haproxy_backend.0.mode` | `http` | None |
| `haproxy_backend.0.balance` | `source` | None |
| `haproxy_backend.0.hash_type` | `{}` | None |
| `haproxy_backend.0.hash_type.method` | `consistent` | None |
| `haproxy_backend.0.hash_type.function` | `djb2` | None |
| `haproxy_backend.0.compression` | `{}` | None |
| `haproxy_backend.0.compression.algo` | `gzip` | None |
| `haproxy_backend.0.compression.type` | `[]` | None |
| `haproxy_backend.0.compression.type.0` | `text/plain` | None |
| `haproxy_backend.0.compression.type.1` | `text/css` | None |
| `haproxy_backend.0.compression.type.2` | `application/json` | None |
| `haproxy_backend.0.compression.type.3` | `application/x-javascript` | None |
| `haproxy_backend.0.compression.type.4` | `text/xml` | None |
| `haproxy_backend.0.compression.type.5` | `application/xml` | None |
| `haproxy_backend.0.compression.type.6` | `application/xml+rss` | None |
| `haproxy_backend.0.compression.type.7` | `text/javascript` | None |
| `haproxy_backend.0.compression.type.8` | `application/javascript` | None |
| `haproxy_backend.0.option` | `[]` | None |
| `haproxy_backend.0.option.0` | `{}` | None |
| `haproxy_backend.0.option.0.name` | `forwardfor` | None |
| `haproxy_backend.0.option.1` | `{}` | None |
| `haproxy_backend.0.option.1.name` | `httpchk` | None |
| `haproxy_backend.0.option.1.params` | `/` | None |
| `haproxy_backend.0.timeout` | `[]` | None |
| `haproxy_backend.0.timeout.0` | `{}` | None |
| `haproxy_backend.0.timeout.0.name` | `tunnel` | None |
| `haproxy_backend.0.timeout.0.value` | `86400s` | None |
| `haproxy_backend.0.acl` | `[]` | None |
| `haproxy_backend.0.acl.0` | `{}` | None |
| `haproxy_backend.0.acl.0.name` | `is_root` | None |
| `haproxy_backend.0.acl.0.fetch` | `path -i /` | None |
| `haproxy_backend.0.acl.1` | `{}` | None |
| `haproxy_backend.0.acl.1.name` | `hdr_set_cookie_path` | None |
| `haproxy_backend.0.acl.1.fetch` | `res.hdr(Set-cookie) -m sub Path=` | None |
| `haproxy_backend.0.http_request` | `[]` | None |
| `haproxy_backend.0.http_request.0` | `{}` | None |
| `haproxy_backend.0.http_request.0.action` | `set-header` | None |
| `haproxy_backend.0.http_request.0.params` | `Test-Header test-value` | None |
| `haproxy_backend.0.http_request.0.condition` | `!{ ssl_fc } is_root` | None |
| `haproxy_backend.0.http_response` | `[]` | None |
| `haproxy_backend.0.http_response.0` | `{}` | None |
| `haproxy_backend.0.http_response.0.action` | `replace-value` | None |
| `haproxy_backend.0.http_response.0.params` | `Cache-control ^public$ private` | None |
| `haproxy_backend.0.http_response.0.condition` | `is_root` | None |
| `haproxy_backend.0.use_server` | `[]` | None |
| `haproxy_backend.0.use_server.0` | `{}` | None |
| `haproxy_backend.0.use_server.0.name` | `server1` | None |
| `haproxy_backend.0.use_server.0.condition` | `hdr(host) -i test.nnc.guru` | None |
| `haproxy_backend.0.server` | `[]` | None |
| `haproxy_backend.0.server.0` | `{}` | None |
| `haproxy_backend.0.server.0.name` | `server1` | None |
| `haproxy_backend.0.server.0.address` | `10.10.10.10` | None |
| `haproxy_backend.0.server.0.port` | `6400` | None |
| `haproxy_backend.0.server.0.params` | `check` | None |
| `haproxy_backend.0.server.1` | `{}` | None |
| `haproxy_backend.0.server.1.name` | `server2` | None |
| `haproxy_backend.0.server.1.address` | `10.10.10.11` | None |
| `haproxy_backend.0.server.1.port` | `6400` | None |
| `haproxy_backend.0.server.1.params` | `check` | None |
| `haproxy_backend.0.stick_table` | `{}` | None |
| `haproxy_backend.0.stick_table.type` | `string` | None |
| `haproxy_backend.0.stick_table.len` | `32` | None |
| `haproxy_backend.0.stick_table.size` | `1M` | None |
| `haproxy_backend.0.stick` | `[]` | None |
| `haproxy_backend.0.stick.0` | `{}` | None |
| `haproxy_backend.0.stick.0.type` | `store-response` | None |
| `haproxy_backend.0.stick.0.pattern` | `res.cook(JSESSIONID)` | None |
| `haproxy_backend.0.stick.0.table` | `app` | None |
| `haproxy_backend.0.stick.1` | `{}` | None |
| `haproxy_backend.0.stick.1.type` | `on` | None |
| `haproxy_backend.0.stick.1.pattern` | `req.cook(JSESSIONID)` | None |




## Task Overview


This role performs the following tasks:


### `install-Debian.yml`


- **Install HAProxy from APT Repository**


### `main.yml`


- **Check Packages**
- **Install HAProxy Package from Repository**
- **Install rsyslog**
- **Configure rsyslog for container compatibility**
- **configure haproxy logging**
- **Create Certificate Folder**
- **Copy Certificate to Host**
- **Create Whitelist Folder**
- **Copy Whitelist File to Host**
- **Ensure log file for HAProxy exists**
- **Correct logrotate configuration**
- **Configure haproxy using haproxy.cfg**


### `install-RedHat.yml`


- **Install HAProxy from YUM Repository**




## Example Playbook

```yaml
---
- hosts: all
  become: yes
  roles:
    - role: role_haproxy

      vars:
        haproxy_config_dir: /etc/haproxy
        haproxy_destination_config_path: {{ haproxy_config_dir }}/haproxy.cfg
        haproxy_log_file: /var/log/haproxy.log

```

## Documentation Maintenance

### Updating Dependencies

1. **Update** `meta/main.yml`:
   ```yaml
   documented_requirements:
     - src: https://github.com/user/role.git
       version: master
     - name: collection.name
       version: 1.0.0
   ```

2. **Sync** `meta/install_requirements.yml` with the same requirements

3. **Regenerate** documentation:
   ```bash
   pre-commit run --all-files
   ```

### Template Updates

- Edit `.docsible_template.md` for structure changes
- Test with: `docsible --role . --md-template .docsible_template.md -nob -com -tl`
- Commit both template and generated README.md

### Quick Checklist

When updating dependencies:
- [ ] Add to `meta/main.yml` → `documented_requirements`
- [ ] Add to `meta/install_requirements.yml`
- [ ] Run `pre-commit run --all-files`
- [ ] Verify generated README.md
- [ ] Commit all changes

## License


license (GPL-2.0-or-later, MIT, etc)


## Author Information


**Author:** gkorkmaz




**GitHub:** [gkorkmaz](https://github.com/gkorkmaz)

---
*This documentation was automatically generated using [docsible](https://github.com/zbohm/docsible).*
<!-- DOCSIBLE END -->
