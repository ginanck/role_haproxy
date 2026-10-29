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

**These are static variables with lower priority**



#### File: defaults/main.yml

| Var | Type | Value |
|-----|------|-------|
| [haproxy_backend](defaults/main.yml#L320) | list |  |
| [haproxy_backend.0](defaults/main.yml#L321) | dict |  |
| [haproxy_backend.0.acl](defaults/main.yml#L346) | list |  |
| [haproxy_backend.0.acl.0](defaults/main.yml#L347) | dict |  |
| [haproxy_backend.0.acl.0.fetch](defaults/main.yml#L348) | str | `path -i /` |
| [haproxy_backend.0.acl.0.name](defaults/main.yml#L347) | str | `is_root` |
| [haproxy_backend.0.acl.1](defaults/main.yml#L349) | dict |  |
| [haproxy_backend.0.acl.1.fetch](defaults/main.yml#L350) | str | `res.hdr(Set-cookie) -m sub Path=` |
| [haproxy_backend.0.acl.1.name](defaults/main.yml#L349) | str | `hdr_set_cookie_path` |
| [haproxy_backend.0.balance](defaults/main.yml#L323) | str | `source` |
| [haproxy_backend.0.compression](defaults/main.yml#L327) | dict |  |
| [haproxy_backend.0.compression.algo](defaults/main.yml#L328) | str | `gzip` |
| [haproxy_backend.0.compression.type](defaults/main.yml#L329) | list |  |
| [haproxy_backend.0.compression.type.0](defaults/main.yml#L330) | str | `text/plain` |
| [haproxy_backend.0.compression.type.1](defaults/main.yml#L331) | str | `text/css` |
| [haproxy_backend.0.compression.type.2](defaults/main.yml#L332) | str | `application/json` |
| [haproxy_backend.0.compression.type.3](defaults/main.yml#L333) | str | `application/x-javascript` |
| [haproxy_backend.0.compression.type.4](defaults/main.yml#L334) | str | `text/xml` |
| [haproxy_backend.0.compression.type.5](defaults/main.yml#L335) | str | `application/xml` |
| [haproxy_backend.0.compression.type.6](defaults/main.yml#L336) | str | `application/xml+rss` |
| [haproxy_backend.0.compression.type.7](defaults/main.yml#L337) | str | `text/javascript` |
| [haproxy_backend.0.compression.type.8](defaults/main.yml#L338) | str | `application/javascript` |
| [haproxy_backend.0.hash_type](defaults/main.yml#L324) | dict |  |
| [haproxy_backend.0.hash_type.function](defaults/main.yml#L326) | str | `djb2` |
| [haproxy_backend.0.hash_type.method](defaults/main.yml#L325) | str | `consistent` |
| [haproxy_backend.0.http_request](defaults/main.yml#L351) | list |  |
| [haproxy_backend.0.http_request.0](defaults/main.yml#L352) | dict |  |
| [haproxy_backend.0.http_request.0.action](defaults/main.yml#L352) | str | `set-header` |
| [haproxy_backend.0.http_request.0.condition](defaults/main.yml#L354) | str | `!{ ssl_fc } is_root` |
| [haproxy_backend.0.http_request.0.params](defaults/main.yml#L353) | str | `Test-Header test-value` |
| [haproxy_backend.0.http_response](defaults/main.yml#L355) | list |  |
| [haproxy_backend.0.http_response.0](defaults/main.yml#L356) | dict |  |
| [haproxy_backend.0.http_response.0.action](defaults/main.yml#L356) | str | `replace-value` |
| [haproxy_backend.0.http_response.0.condition](defaults/main.yml#L358) | str | `is_root` |
| [haproxy_backend.0.http_response.0.params](defaults/main.yml#L357) | str | `Cache-control ^public$ private` |
| [haproxy_backend.0.mode](defaults/main.yml#L322) | str | `http` |
| [haproxy_backend.0.name](defaults/main.yml#L321) | str | `app` |
| [haproxy_backend.0.option](defaults/main.yml#L339) | list |  |
| [haproxy_backend.0.option.0](defaults/main.yml#L340) | dict |  |
| [haproxy_backend.0.option.0.name](defaults/main.yml#L340) | str | `forwardfor` |
| [haproxy_backend.0.option.1](defaults/main.yml#L341) | dict |  |
| [haproxy_backend.0.option.1.name](defaults/main.yml#L341) | str | `httpchk` |
| [haproxy_backend.0.option.1.params](defaults/main.yml#L342) | str | `/` |
| [haproxy_backend.0.server](defaults/main.yml#L362) | list |  |
| [haproxy_backend.0.server.0](defaults/main.yml#L363) | dict |  |
| [haproxy_backend.0.server.0.address](defaults/main.yml#L364) | str | `10.10.10.10` |
| [haproxy_backend.0.server.0.name](defaults/main.yml#L363) | str | `server1` |
| [haproxy_backend.0.server.0.params](defaults/main.yml#L366) | str | `check` |
| [haproxy_backend.0.server.0.port](defaults/main.yml#L365) | int | `6400` |
| [haproxy_backend.0.server.1](defaults/main.yml#L367) | dict |  |
| [haproxy_backend.0.server.1.address](defaults/main.yml#L368) | str | `10.10.10.11` |
| [haproxy_backend.0.server.1.name](defaults/main.yml#L367) | str | `server2` |
| [haproxy_backend.0.server.1.params](defaults/main.yml#L370) | str | `check` |
| [haproxy_backend.0.server.1.port](defaults/main.yml#L369) | int | `6400` |
| [haproxy_backend.0.stick](defaults/main.yml#L375) | list |  |
| [haproxy_backend.0.stick.0](defaults/main.yml#L376) | dict |  |
| [haproxy_backend.0.stick.0.pattern](defaults/main.yml#L377) | str | `res.cook(JSESSIONID)` |
| [haproxy_backend.0.stick.0.table](defaults/main.yml#L378) | str | `app` |
| [haproxy_backend.0.stick.0.type](defaults/main.yml#L376) | str | `store-response` |
| [haproxy_backend.0.stick.1](defaults/main.yml#L379) | dict |  |
| [haproxy_backend.0.stick.1.pattern](defaults/main.yml#L380) | str | `req.cook(JSESSIONID)` |
| [haproxy_backend.0.stick.1.type](defaults/main.yml#L379) | str | `on` |
| [haproxy_backend.0.stick_table](defaults/main.yml#L371) | dict |  |
| [haproxy_backend.0.stick_table.len](defaults/main.yml#L373) | int | `32` |
| [haproxy_backend.0.stick_table.size](defaults/main.yml#L374) | str | `1M` |
| [haproxy_backend.0.stick_table.type](defaults/main.yml#L372) | str | `string` |
| [haproxy_backend.0.timeout](defaults/main.yml#L343) | list |  |
| [haproxy_backend.0.timeout.0](defaults/main.yml#L344) | dict |  |
| [haproxy_backend.0.timeout.0.name](defaults/main.yml#L344) | str | `tunnel` |
| [haproxy_backend.0.timeout.0.value](defaults/main.yml#L345) | str | `86400s` |
| [haproxy_backend.0.use_server](defaults/main.yml#L359) | list |  |
| [haproxy_backend.0.use_server.0](defaults/main.yml#L360) | dict |  |
| [haproxy_backend.0.use_server.0.condition](defaults/main.yml#L361) | str | `hdr(host) -i test.nnc.guru` |
| [haproxy_backend.0.use_server.0.name](defaults/main.yml#L360) | str | `server1` |
| [haproxy_cert_dir](defaults/main.yml#L17) | str | `{{ haproxy_config_dir }}/certs` |
| [haproxy_cert_group](defaults/main.yml#L20) | str | `haproxy` |
| [haproxy_cert_name](defaults/main.yml#L18) | str |  |
| [haproxy_config_dir](defaults/main.yml#L8) | str | `/etc/haproxy` |
| [haproxy_config_staging_path](defaults/main.yml#L23) | str | `{{ haproxy_destination_config_path }}.staged` |
| [haproxy_defaults](defaults/main.yml#L144) | dict |  |
| [haproxy_defaults.log](defaults/main.yml#L146) | list |  |
| [haproxy_defaults.log.0](defaults/main.yml#L147) | dict |  |
| [haproxy_defaults.log.0.global](defaults/main.yml#L147) | bool | `True` |
| [haproxy_defaults.maxconn](defaults/main.yml#L171) | int | `3000` |
| [haproxy_defaults.mode](defaults/main.yml#L145) | str | `http` |
| [haproxy_defaults.option](defaults/main.yml#L148) | list |  |
| [haproxy_defaults.option.0](defaults/main.yml#L149) | dict |  |
| [haproxy_defaults.option.0.name](defaults/main.yml#L149) | str | `httplog` |
| [haproxy_defaults.option.1](defaults/main.yml#L150) | dict |  |
| [haproxy_defaults.option.1.name](defaults/main.yml#L150) | str | `dontlognull` |
| [haproxy_defaults.option.2](defaults/main.yml#L151) | dict |  |
| [haproxy_defaults.option.2.name](defaults/main.yml#L151) | str | `http-server-close` |
| [haproxy_defaults.option.3](defaults/main.yml#L152) | dict |  |
| [haproxy_defaults.option.3.name](defaults/main.yml#L152) | str | `forwardfor` |
| [haproxy_defaults.option.3.params](defaults/main.yml#L153) | str | `except 127.0.0.0/8` |
| [haproxy_defaults.option.4](defaults/main.yml#L154) | dict |  |
| [haproxy_defaults.option.4.name](defaults/main.yml#L154) | str | `redispatch` |
| [haproxy_defaults.retries](defaults/main.yml#L155) | int | `3` |
| [haproxy_defaults.timeout](defaults/main.yml#L156) | list |  |
| [haproxy_defaults.timeout.0](defaults/main.yml#L157) | dict |  |
| [haproxy_defaults.timeout.0.name](defaults/main.yml#L157) | str | `http-request` |
| [haproxy_defaults.timeout.0.value](defaults/main.yml#L158) | str | `10s` |
| [haproxy_defaults.timeout.1](defaults/main.yml#L159) | dict |  |
| [haproxy_defaults.timeout.1.name](defaults/main.yml#L159) | str | `queue` |
| [haproxy_defaults.timeout.1.value](defaults/main.yml#L160) | str | `1m` |
| [haproxy_defaults.timeout.2](defaults/main.yml#L161) | dict |  |
| [haproxy_defaults.timeout.2.name](defaults/main.yml#L161) | str | `connect` |
| [haproxy_defaults.timeout.2.value](defaults/main.yml#L162) | str | `10s` |
| [haproxy_defaults.timeout.3](defaults/main.yml#L163) | dict |  |
| [haproxy_defaults.timeout.3.name](defaults/main.yml#L163) | str | `client` |
| [haproxy_defaults.timeout.3.value](defaults/main.yml#L164) | str | `1m` |
| [haproxy_defaults.timeout.4](defaults/main.yml#L165) | dict |  |
| [haproxy_defaults.timeout.4.name](defaults/main.yml#L165) | str | `server` |
| [haproxy_defaults.timeout.4.value](defaults/main.yml#L166) | str | `1m` |
| [haproxy_defaults.timeout.5](defaults/main.yml#L167) | dict |  |
| [haproxy_defaults.timeout.5.name](defaults/main.yml#L167) | str | `http-keep-alive` |
| [haproxy_defaults.timeout.5.value](defaults/main.yml#L168) | str | `10s` |
| [haproxy_defaults.timeout.6](defaults/main.yml#L169) | dict |  |
| [haproxy_defaults.timeout.6.name](defaults/main.yml#L169) | str | `check` |
| [haproxy_defaults.timeout.6.value](defaults/main.yml#L170) | str | `10s` |
| [haproxy_destination_config_path](defaults/main.yml#L9) | str | `{{ haproxy_config_dir }}/haproxy.cfg` |
| [haproxy_frontend](defaults/main.yml#L213) | list |  |
| [haproxy_frontend.0](defaults/main.yml#L214) | dict |  |
| [haproxy_frontend.0.backlog](defaults/main.yml#L221) | int | `10000` |
| [haproxy_frontend.0.bind](defaults/main.yml#L216) | list |  |
| [haproxy_frontend.0.bind.0](defaults/main.yml#L217) | dict |  |
| [haproxy_frontend.0.bind.0.address](defaults/main.yml#L217) | str | `127.0.0.1` |
| [haproxy_frontend.0.bind.0.port](defaults/main.yml#L218) | int | `5001` |
| [haproxy_frontend.0.bind.1](defaults/main.yml#L219) | dict |  |
| [haproxy_frontend.0.bind.1.address](defaults/main.yml#L219) | str | `127.0.0.1` |
| [haproxy_frontend.0.bind.1.port](defaults/main.yml#L220) | int | `5002` |
| [haproxy_frontend.0.default_backend](defaults/main.yml#L225) | str | `app` |
| [haproxy_frontend.0.mode](defaults/main.yml#L215) | str | `http` |
| [haproxy_frontend.0.name](defaults/main.yml#L214) | str | `main-http` |
| [haproxy_frontend.0.use_backend](defaults/main.yml#L222) | list |  |
| [haproxy_frontend.0.use_backend.0](defaults/main.yml#L223) | dict |  |
| [haproxy_frontend.0.use_backend.0.condition](defaults/main.yml#L224) | str | `!{ ssl_fc }` |
| [haproxy_frontend.0.use_backend.0.name](defaults/main.yml#L223) | str | `app` |
| [haproxy_frontend.1](defaults/main.yml#L226) | dict |  |
| [haproxy_frontend.1.acl](defaults/main.yml#L252) | list |  |
| [haproxy_frontend.1.acl.0](defaults/main.yml#L253) | dict |  |
| [haproxy_frontend.1.acl.0.fetch](defaults/main.yml#L254) | str | `path -i  /` |
| [haproxy_frontend.1.acl.0.name](defaults/main.yml#L253) | str | `is_root` |
| [haproxy_frontend.1.bind](defaults/main.yml#L228) | list |  |
| [haproxy_frontend.1.bind.0](defaults/main.yml#L229) | dict |  |
| [haproxy_frontend.1.bind.0.address](defaults/main.yml#L229) | str | `127.0.0.1` |
| [haproxy_frontend.1.bind.0.port](defaults/main.yml#L230) | int | `5003` |
| [haproxy_frontend.1.capture](defaults/main.yml#L244) | list |  |
| [haproxy_frontend.1.capture.0](defaults/main.yml#L245) | dict |  |
| [haproxy_frontend.1.capture.0.len](defaults/main.yml#L247) | int | `32` |
| [haproxy_frontend.1.capture.0.name](defaults/main.yml#L246) | str | `JSESSIONID` |
| [haproxy_frontend.1.capture.0.type](defaults/main.yml#L245) | str | `cookie` |
| [haproxy_frontend.1.capture.1](defaults/main.yml#L248) | dict |  |
| [haproxy_frontend.1.capture.1.len](defaults/main.yml#L250) | int | `15` |
| [haproxy_frontend.1.capture.1.name](defaults/main.yml#L249) | str | `Host` |
| [haproxy_frontend.1.capture.1.type](defaults/main.yml#L248) | str | `request header` |
| [haproxy_frontend.1.http_request](defaults/main.yml#L255) | list |  |
| [haproxy_frontend.1.http_request.0](defaults/main.yml#L256) | dict |  |
| [haproxy_frontend.1.http_request.0.action](defaults/main.yml#L256) | str | `set-header` |
| [haproxy_frontend.1.http_request.0.condition](defaults/main.yml#L258) | str | `!{ ssl_fc }` |
| [haproxy_frontend.1.http_request.0.params](defaults/main.yml#L257) | str | `X-Forwarded-Proto http` |
| [haproxy_frontend.1.mode](defaults/main.yml#L227) | str | `http` |
| [haproxy_frontend.1.monitor_uri](defaults/main.yml#L251) | str | `/haproxy` |
| [haproxy_frontend.1.name](defaults/main.yml#L226) | str | `main-https` |
| [haproxy_frontend.1.option](defaults/main.yml#L231) | list |  |
| [haproxy_frontend.1.option.0](defaults/main.yml#L232) | dict |  |
| [haproxy_frontend.1.option.0.name](defaults/main.yml#L232) | str | `contstats` |
| [haproxy_frontend.1.option.1](defaults/main.yml#L233) | dict |  |
| [haproxy_frontend.1.option.1.name](defaults/main.yml#L233) | str | `http-server-close` |
| [haproxy_frontend.1.option.2](defaults/main.yml#L234) | dict |  |
| [haproxy_frontend.1.option.2.name](defaults/main.yml#L234) | str | `httplog` |
| [haproxy_frontend.1.redirect](defaults/main.yml#L259) | list |  |
| [haproxy_frontend.1.redirect.0](defaults/main.yml#L260) | dict |  |
| [haproxy_frontend.1.redirect.0.code](defaults/main.yml#L262) | int | `301` |
| [haproxy_frontend.1.redirect.0.condition](defaults/main.yml#L264) | str | `!{ ssl_fc }` |
| [haproxy_frontend.1.redirect.0.option](defaults/main.yml#L263) | str | `drop-query` |
| [haproxy_frontend.1.redirect.0.type](defaults/main.yml#L260) | str | `scheme` |
| [haproxy_frontend.1.redirect.0.value](defaults/main.yml#L261) | str | `https` |
| [haproxy_frontend.1.timeout](defaults/main.yml#L235) | list |  |
| [haproxy_frontend.1.timeout.0](defaults/main.yml#L236) | dict |  |
| [haproxy_frontend.1.timeout.0.name](defaults/main.yml#L236) | str | `client` |
| [haproxy_frontend.1.timeout.0.value](defaults/main.yml#L237) | str | `300s` |
| [haproxy_frontend.1.timeout.1](defaults/main.yml#L238) | dict |  |
| [haproxy_frontend.1.timeout.1.name](defaults/main.yml#L238) | str | `http-keep-alive` |
| [haproxy_frontend.1.timeout.1.value](defaults/main.yml#L239) | str | `1s` |
| [haproxy_frontend.1.timeout.2](defaults/main.yml#L240) | dict |  |
| [haproxy_frontend.1.timeout.2.name](defaults/main.yml#L240) | str | `http-request` |
| [haproxy_frontend.1.timeout.2.value](defaults/main.yml#L241) | str | `15s` |
| [haproxy_frontend.1.timeout.3](defaults/main.yml#L242) | dict |  |
| [haproxy_frontend.1.timeout.3.name](defaults/main.yml#L242) | str | `tarpit` |
| [haproxy_frontend.1.timeout.3.value](defaults/main.yml#L243) | str | `60s` |
| [haproxy_frontend.1.use_backend](defaults/main.yml#L265) | list |  |
| [haproxy_frontend.1.use_backend.0](defaults/main.yml#L266) | dict |  |
| [haproxy_frontend.1.use_backend.0.condition](defaults/main.yml#L267) | str | `!{ ssl_fc }` |
| [haproxy_frontend.1.use_backend.0.name](defaults/main.yml#L266) | str | `app` |
| [haproxy_global](defaults/main.yml#L96) | dict |  |
| [haproxy_global.chroot](defaults/main.yml#L108) | str | `/var/lib/haproxy` |
| [haproxy_global.cpu_map](defaults/main.yml#L128) | str |  |
| [haproxy_global.daemon](defaults/main.yml#L113) | bool | `True` |
| [haproxy_global.group](defaults/main.yml#L112) | str | `haproxy` |
| [haproxy_global.log](defaults/main.yml#L97) | list |  |
| [haproxy_global.log.0](defaults/main.yml#L99) | dict |  |
| [haproxy_global.log.0.address](defaults/main.yml#L99) | str | `127.0.0.1` |
| [haproxy_global.log.0.facility](defaults/main.yml#L100) | str | `local0` |
| [haproxy_global.maxconn](defaults/main.yml#L110) | int | `4000` |
| [haproxy_global.nbthread](defaults/main.yml#L126) | int |  |
| [haproxy_global.pidfile](defaults/main.yml#L109) | str | `/var/run/haproxy.pid` |
| [haproxy_global.quiet](defaults/main.yml#L138) | bool |  |
| [haproxy_global.spread_checks](defaults/main.yml#L136) | int |  |
| [haproxy_global.stats_socket](defaults/main.yml#L114) | list |  |
| [haproxy_global.stats_socket.0](defaults/main.yml#L115) | dict |  |
| [haproxy_global.stats_socket.0.path](defaults/main.yml#L115) | str | `/var/lib/haproxy/stats` |
| [haproxy_global.tune](defaults/main.yml#L130) | dict |  |
| [haproxy_global.tune.bufsize](defaults/main.yml#L133) | int | `16384` |
| [haproxy_global.tune.maxrewrite](defaults/main.yml#L134) | int | `1024` |
| [haproxy_global.tune.ssl_cachesize](defaults/main.yml#L131) | int | `20000` |
| [haproxy_global.tune.ssl_lifetime](defaults/main.yml#L132) | int | `300` |
| [haproxy_global.tune_ssl_default_dh_param](defaults/main.yml#L107) | int | `2048` |
| [haproxy_global.user](defaults/main.yml#L111) | str | `haproxy` |
| [haproxy_ip_nonlocal_bind](defaults/main.yml#L90) | bool |  |
| [haproxy_listen](defaults/main.yml#L386) | list |  |
| [haproxy_listen.0](defaults/main.yml#L387) | dict |  |
| [haproxy_listen.0.bind](defaults/main.yml#L390) | list |  |
| [haproxy_listen.0.bind.0](defaults/main.yml#L391) | dict |  |
| [haproxy_listen.0.bind.0.address](defaults/main.yml#L391) | str | `127.0.0.1` |
| [haproxy_listen.0.bind.0.port](defaults/main.yml#L392) | int | `8000` |
| [haproxy_listen.0.mode](defaults/main.yml#L388) | str | `http` |
| [haproxy_listen.0.monitor_uri](defaults/main.yml#L389) | str | `/haproxy` |
| [haproxy_listen.0.name](defaults/main.yml#L387) | str | `http_health_check` |
| [haproxy_listen.0.option](defaults/main.yml#L393) | list |  |
| [haproxy_listen.0.option.0](defaults/main.yml#L394) | dict |  |
| [haproxy_listen.0.option.0.name](defaults/main.yml#L394) | str | `dontlognull` |
| [haproxy_listen.0.option.1](defaults/main.yml#L395) | dict |  |
| [haproxy_listen.0.option.1.name](defaults/main.yml#L395) | str | `httpchk` |
| [haproxy_listen.1](defaults/main.yml#L396) | dict |  |
| [haproxy_listen.1.bind](defaults/main.yml#L398) | list |  |
| [haproxy_listen.1.bind.0](defaults/main.yml#L399) | dict |  |
| [haproxy_listen.1.bind.0.address](defaults/main.yml#L399) | str | `127.0.0.1` |
| [haproxy_listen.1.bind.0.port](defaults/main.yml#L400) | int | `9000` |
| [haproxy_listen.1.mode](defaults/main.yml#L397) | str | `http` |
| [haproxy_listen.1.name](defaults/main.yml#L396) | str | `stats` |
| [haproxy_listen.1.stats](defaults/main.yml#L401) | dict |  |
| [haproxy_listen.1.stats.auth](defaults/main.yml#L408) | list |  |
| [haproxy_listen.1.stats.auth.0](defaults/main.yml#L409) | dict |  |
| [haproxy_listen.1.stats.auth.0.login](defaults/main.yml#L409) | str | `admin-user` |
| [haproxy_listen.1.stats.auth.0.password](defaults/main.yml#L410) | str | `{{ haproxy_stats_password }}` |
| [haproxy_listen.1.stats.enable](defaults/main.yml#L402) | bool | `True` |
| [haproxy_listen.1.stats.hide_version](defaults/main.yml#L403) | bool | `True` |
| [haproxy_listen.1.stats.realm](defaults/main.yml#L407) | str | `HAProxy\ Statistics` |
| [haproxy_listen.1.stats.refresh](defaults/main.yml#L411) | str | `5s` |
| [haproxy_listen.1.stats.scope](defaults/main.yml#L404) | list |  |
| [haproxy_listen.1.stats.scope.0](defaults/main.yml#L405) | str | `.` |
| [haproxy_listen.1.stats.uri](defaults/main.yml#L406) | str | `/admin?stats` |
| [haproxy_log_dir](defaults/main.yml#L10) | str | `/var/log/haproxy` |
| [haproxy_log_file](defaults/main.yml#L11) | str | `{{ haproxy_log_dir }}/haproxy.log` |
| [haproxy_logging](defaults/main.yml#L487) | dict |  |
| [haproxy_logging.capture_request_headers](defaults/main.yml#L493) | list |  |
| [haproxy_logging.capture_response_headers](defaults/main.yml#L495) | list |  |
| [haproxy_logging.custom_log_format](defaults/main.yml#L497) | str |  |
| [haproxy_logging.destination](defaults/main.yml#L489) | str | `/dev/log` |
| [haproxy_logging.facility](defaults/main.yml#L490) | str | `local0` |
| [haproxy_logging.level](defaults/main.yml#L491) | str | `info` |
| [haproxy_logging.logrotate](defaults/main.yml#L505) | dict |  |
| [haproxy_logging.logrotate.frequency](defaults/main.yml#L506) | str | `daily` |
| [haproxy_logging.logrotate.retain](defaults/main.yml#L507) | int | `14` |
| [haproxy_logging.per_backend_log_level](defaults/main.yml#L499) | dict |  |
| [haproxy_logging.rsyslog](defaults/main.yml#L501) | dict |  |
| [haproxy_logging.rsyslog.udp_listen](defaults/main.yml#L503) | bool |  |
| [haproxy_logrotate_file](defaults/main.yml#L12) | str | `/etc/logrotate.d/haproxy` |
| [haproxy_network_routes](defaults/main.yml#L56) | list |  |
| [haproxy_peers](defaults/main.yml#L541) | dict |  |
| [haproxy_peers.enabled](defaults/main.yml#L542) | bool |  |
| [haproxy_peers.name](defaults/main.yml#L543) | str | `haproxy_cluster` |
| [haproxy_peers.peers](defaults/main.yml#L544) | list |  |
| [haproxy_policy_routing](defaults/main.yml#L67) | dict |  |
| [haproxy_policy_routing.enabled](defaults/main.yml#L68) | bool |  |
| [haproxy_policy_routing.tables](defaults/main.yml#L69) | list |  |
| [haproxy_private_ip](defaults/main.yml#L38) | str |  |
| [haproxy_public_ip](defaults/main.yml#L33) | str |  |
| [haproxy_rate_limits](defaults/main.yml#L450) | list |  |
| [haproxy_security](defaults/main.yml#L463) | dict |  |
| [haproxy_security.hide_server_header](defaults/main.yml#L481) | bool |  |
| [haproxy_security.ip_blacklist](defaults/main.yml#L470) | dict |  |
| [haproxy_security.ip_blacklist.apply_to](defaults/main.yml#L475) | list |  |
| [haproxy_security.ip_blacklist.enabled](defaults/main.yml#L471) | bool |  |
| [haproxy_security.ip_blacklist.ips](defaults/main.yml#L473) | list |  |
| [haproxy_security.ip_whitelist](defaults/main.yml#L464) | dict |  |
| [haproxy_security.ip_whitelist.apply_to](defaults/main.yml#L469) | list |  |
| [haproxy_security.ip_whitelist.enabled](defaults/main.yml#L465) | bool |  |
| [haproxy_security.ip_whitelist.ips](defaults/main.yml#L467) | list |  |
| [haproxy_security.request_body_size_limit](defaults/main.yml#L476) | dict |  |
| [haproxy_security.request_body_size_limit.enabled](defaults/main.yml#L477) | bool |  |
| [haproxy_security.request_body_size_limit.max_bytes](defaults/main.yml#L479) | int | `10485760` |
| [haproxy_ssl](defaults/main.yml#L417) | dict |  |
| [haproxy_ssl.cert_dir](defaults/main.yml#L419) | str | `{{ haproxy_config_dir }}/certs` |
| [haproxy_ssl.default_bind_ciphers](defaults/main.yml#L421) | str |  |
| [haproxy_ssl.default_bind_options](defaults/main.yml#L423) | str |  |
| [haproxy_ssl.ocsp_stapling](defaults/main.yml#L427) | bool |  |
| [haproxy_ssl.session_cache_size](defaults/main.yml#L425) | int | `20000` |
| [haproxy_stats](defaults/main.yml#L513) | dict |  |
| [haproxy_stats.auth](defaults/main.yml#L520) | dict |  |
| [haproxy_stats.auth.enabled](defaults/main.yml#L521) | bool |  |
| [haproxy_stats.auth.password](defaults/main.yml#L523) | str |  |
| [haproxy_stats.auth.username](defaults/main.yml#L522) | str | `admin` |
| [haproxy_stats.bind_ip](defaults/main.yml#L516) | str | `127.0.0.1` |
| [haproxy_stats.enabled](defaults/main.yml#L515) | bool |  |
| [haproxy_stats.port](defaults/main.yml#L517) | int | `8404` |
| [haproxy_stats.prometheus](defaults/main.yml#L524) | dict |  |
| [haproxy_stats.prometheus.enabled](defaults/main.yml#L526) | bool |  |
| [haproxy_stats.prometheus.uri](defaults/main.yml#L527) | str | `/metrics` |
| [haproxy_stats.refresh](defaults/main.yml#L519) | str | `10s` |
| [haproxy_stats.runtime_api](defaults/main.yml#L528) | dict |  |
| [haproxy_stats.runtime_api.enabled](defaults/main.yml#L530) | bool |  |
| [haproxy_stats.runtime_api.level](defaults/main.yml#L532) | str | `admin` |
| [haproxy_stats.runtime_api.socket](defaults/main.yml#L531) | str | `/var/run/haproxy/admin.sock` |
| [haproxy_stats.uri](defaults/main.yml#L518) | str | `/stats` |
| [haproxy_stats_password](defaults/main.yml#L26) | str |  |
| [haproxy_stick_tables](defaults/main.yml#L435) | list |  |
| [haproxy_whitelist_file_dir](defaults/main.yml#L14) | str | `{{ haproxy_config_dir }}/whitelist` |
| [haproxy_whitelist_file_name](defaults/main.yml#L15) | str |  |




## Task Overview


This role performs the following tasks:


### File: `tasks/validation.yml`

| Task Name | Module | Has Conditions | Line |
|-----------|--------|----------------|------|
| [Assert haproxy_global is defined and sane](tasks/validation.yml#L) | ansible.builtin.assert | No | N/A |
| [Assert haproxy_defaults mode is valid](tasks/validation.yml#L) | ansible.builtin.assert | No | N/A |
| [Assert frontend modes are valid](tasks/validation.yml#L) | ansible.builtin.assert | No | N/A |
| [Assert backend modes are valid](tasks/validation.yml#L) | ansible.builtin.assert | No | N/A |
| [Assert stats auth credentials when stats + auth enabled](tasks/validation.yml#L) | ansible.builtin.assert | Yes | N/A |
| [Assert peers list is non-empty when HA peers enabled](tasks/validation.yml#L) | ansible.builtin.assert | Yes | N/A |
| [Assert rate limit tables reference existing stick tables](tasks/validation.yml#L) | ansible.builtin.assert | No | N/A |
| [Assert static routes have required fields](tasks/validation.yml#L) | ansible.builtin.assert | No | N/A |
| [Assert policy routing tables have required fields](tasks/validation.yml#L) | ansible.builtin.assert | Yes | N/A |
| [Assert policy routing table numbers are unique](tasks/validation.yml#L) | ansible.builtin.assert | Yes | N/A |
| [Assert every stats endpoint uses a vault supplied password](tasks/validation.yml#L) | ansible.builtin.assert | No | N/A |
| [Validate HAProxy configuration syntax](tasks/validation.yml#L) | ansible.builtin.command | No | N/A |




### File: `tasks/logging.yml`

| Task Name | Module | Has Conditions | Line |
|-----------|--------|----------------|------|
| [Install Rsyslog Package](tasks/logging.yml#L) | ansible.builtin.package | No | N/A |
| [Create HAProxy Log Directory](tasks/logging.yml#L) | ansible.builtin.file | No | N/A |
| [Deploy Rsyslog Configuration for HAProxy](tasks/logging.yml#L) | ansible.builtin.template | No | N/A |
| [Enable and Start Rsyslog Service](tasks/logging.yml#L) | ansible.builtin.service | Yes | N/A |
| [Deploy Logrotate Configuration for HAProxy](tasks/logging.yml#L) | ansible.builtin.template | No | N/A |




### File: `tasks/preflight.yml`

| Task Name | Module | Has Conditions | Line |
|-----------|--------|----------------|------|
| [Assert a vault supplied stats password when stats auth is configured](tasks/preflight.yml#L) | ansible.builtin.assert | Yes | N/A |
| [Assert the certificate group exists when a certificate is deployed](tasks/preflight.yml#L) | ansible.builtin.getent | Yes | N/A |
| [Fail when the certificate group is missing](tasks/preflight.yml#L) | ansible.builtin.assert | Yes | N/A |




### File: `tasks/routing.yml`

| Task Name | Module | Has Conditions | Line |
|-----------|--------|----------------|------|
| [Set Routing State Facts](tasks/routing.yml#L) | ansible.builtin.set_fact | No | N/A |
| [Enable IP Non-Local Bind via Sysctl](tasks/routing.yml#L) | ansible.posix.sysctl | Yes | N/A |
| [Check Existing Static Routes](tasks/routing.yml#L) | ansible.builtin.command | Yes | N/A |
| [Apply Static Routes](tasks/routing.yml#L) | ansible.builtin.command | Yes | N/A |
| [Register Policy Routing Tables in rt_tables](tasks/routing.yml#L) | ansible.builtin.lineinfile | Yes | N/A |
| [Check Existing Policy Routing Table Default Routes](tasks/routing.yml#L) | ansible.builtin.command | Yes | N/A |
| [Add Policy Routing Table Default Routes](tasks/routing.yml#L) | ansible.builtin.command | Yes | N/A |
| [Check Existing Policy Routing Rules](tasks/routing.yml#L) | ansible.builtin.command | Yes | N/A |
| [Add Policy Routing Rules](tasks/routing.yml#L) | ansible.builtin.command | Yes | N/A |
| [Deploy HAProxy Routing Script](tasks/routing.yml#L) | ansible.builtin.template | Yes | N/A |
| [Deploy HAProxy Routing Systemd Service](tasks/routing.yml#L) | ansible.builtin.template | Yes | N/A |
| [Flush Handlers Before Enabling Routing Service](tasks/routing.yml#L) | ansible.builtin.meta | No | N/A |
| [Enable HAProxy Routing Service](tasks/routing.yml#L) | ansible.builtin.systemd | Yes | N/A |
| [Check If HAProxy Routing Service Exists](tasks/routing.yml#L) | ansible.builtin.stat | No | N/A |
| [Check If HAProxy Routing Script Exists](tasks/routing.yml#L) | ansible.builtin.stat | No | N/A |
| [Read Existing Routing Script for Cleanup Data](tasks/routing.yml#L) | ansible.builtin.slurp | Yes | N/A |
| [Parse Managed Resources from Old Script](tasks/routing.yml#L) | ansible.builtin.set_fact | Yes | N/A |
| [Remove Managed Policy Routing Rules](tasks/routing.yml#L) | ansible.builtin.shell | Yes | N/A |
| [Flush Managed Policy Routing Tables](tasks/routing.yml#L) | ansible.builtin.command | Yes | N/A |
| [Remove Managed Table Entries from rt_tables](tasks/routing.yml#L) | ansible.builtin.lineinfile | Yes | N/A |
| [Remove Managed Static Routes](tasks/routing.yml#L) | ansible.builtin.command | Yes | N/A |
| [Stop and Disable HAProxy Routing Service](tasks/routing.yml#L) | ansible.builtin.systemd | Yes | N/A |
| [Remove HAProxy Routing Systemd Service File](tasks/routing.yml#L) | ansible.builtin.file | Yes | N/A |
| [Remove HAProxy Routing Script](tasks/routing.yml#L) | ansible.builtin.file | Yes | N/A |
| [Check If HAProxy Sysctl Config Exists](tasks/routing.yml#L) | ansible.builtin.stat | No | N/A |
| [Remove IP Non-Local Bind Sysctl Config](tasks/routing.yml#L) | ansible.builtin.file | Yes | N/A |
| [Reload Sysctl After Removing HAProxy Config](tasks/routing.yml#L) | ansible.builtin.command | Yes | N/A |




### File: `tasks/install-Debian.yml`

| Task Name | Module | Has Conditions | Line |
|-----------|--------|----------------|------|
| [Install HAProxy from APT Repository](tasks/install-Debian.yml#L) | ansible.builtin.apt | No | N/A |




### File: `tasks/main.yml`

| Task Name | Module | Has Conditions | Line |
|-----------|--------|----------------|------|
| [Check Packages](tasks/main.yml#L) | ansible.builtin.package_facts | No | N/A |
| [Run Pre-flight Checks](tasks/main.yml#L) | ansible.builtin.include_tasks | No | N/A |
| [Install HAProxy Package from Repository](tasks/main.yml#L) | ansible.builtin.include_tasks | Yes | N/A |
| [Create Certificate Folder](tasks/main.yml#L) | ansible.builtin.file | Yes | N/A |
| [Copy Certificate to Host](tasks/main.yml#L) | ansible.builtin.copy | Yes | N/A |
| [Create Whitelist Folder](tasks/main.yml#L) | ansible.builtin.file | Yes | N/A |
| [Copy Whitelist File to Host](tasks/main.yml#L) | ansible.builtin.copy | Yes | N/A |
| [Include Network Routing Tasks](tasks/main.yml#L) | ansible.builtin.include_tasks | No | N/A |
| [Create runtime API socket directory](tasks/main.yml#L) | ansible.builtin.file | Yes | N/A |
| [Include Logging Tasks](tasks/main.yml#L) | ansible.builtin.include_tasks | No | N/A |
| [Render HAProxy configuration to the staging path](tasks/main.yml#L) | ansible.builtin.template | No | N/A |
| [Validate the staged HAProxy configuration](tasks/main.yml#L) | ansible.builtin.command | No | N/A |
| [Install the validated HAProxy configuration](tasks/main.yml#L) | ansible.builtin.copy | No | N/A |
| [Run pre-flight validation checks](tasks/main.yml#L) | ansible.builtin.include_tasks | No | N/A |
| [Ensure HAProxy Service is Started and Enabled](tasks/main.yml#L) | ansible.builtin.systemd | No | N/A |




### File: `tasks/install-RedHat.yml`

| Task Name | Module | Has Conditions | Line |
|-----------|--------|----------------|------|
| [Install HAProxy from YUM Repository](tasks/install-RedHat.yml#L) | ansible.builtin.dnf | No | N/A |






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
        haproxy_log_dir: /var/log/haproxy

```

## License


MIT


## Author Information


**Author:** gkorkmaz




**GitHub:** [gkorkmaz](https://github.com/gkorkmaz)

---
*This documentation was automatically generated using [docsible](https://github.com/zbohm/docsible).*
<!-- DOCSIBLE END -->
