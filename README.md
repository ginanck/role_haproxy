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
| [haproxy_backend](defaults/main.yml#L312) | list |  |
| [haproxy_backend.0](defaults/main.yml#L313) | dict |  |
| [haproxy_backend.0.acl](defaults/main.yml#L338) | list |  |
| [haproxy_backend.0.acl.0](defaults/main.yml#L339) | dict |  |
| [haproxy_backend.0.acl.0.fetch](defaults/main.yml#L340) | str | `path -i /` |
| [haproxy_backend.0.acl.0.name](defaults/main.yml#L339) | str | `is_root` |
| [haproxy_backend.0.acl.1](defaults/main.yml#L341) | dict |  |
| [haproxy_backend.0.acl.1.fetch](defaults/main.yml#L342) | str | `res.hdr(Set-cookie) -m sub Path=` |
| [haproxy_backend.0.acl.1.name](defaults/main.yml#L341) | str | `hdr_set_cookie_path` |
| [haproxy_backend.0.balance](defaults/main.yml#L315) | str | `source` |
| [haproxy_backend.0.compression](defaults/main.yml#L319) | dict |  |
| [haproxy_backend.0.compression.algo](defaults/main.yml#L320) | str | `gzip` |
| [haproxy_backend.0.compression.type](defaults/main.yml#L321) | list |  |
| [haproxy_backend.0.compression.type.0](defaults/main.yml#L322) | str | `text/plain` |
| [haproxy_backend.0.compression.type.1](defaults/main.yml#L323) | str | `text/css` |
| [haproxy_backend.0.compression.type.2](defaults/main.yml#L324) | str | `application/json` |
| [haproxy_backend.0.compression.type.3](defaults/main.yml#L325) | str | `application/x-javascript` |
| [haproxy_backend.0.compression.type.4](defaults/main.yml#L326) | str | `text/xml` |
| [haproxy_backend.0.compression.type.5](defaults/main.yml#L327) | str | `application/xml` |
| [haproxy_backend.0.compression.type.6](defaults/main.yml#L328) | str | `application/xml+rss` |
| [haproxy_backend.0.compression.type.7](defaults/main.yml#L329) | str | `text/javascript` |
| [haproxy_backend.0.compression.type.8](defaults/main.yml#L330) | str | `application/javascript` |
| [haproxy_backend.0.hash_type](defaults/main.yml#L316) | dict |  |
| [haproxy_backend.0.hash_type.function](defaults/main.yml#L318) | str | `djb2` |
| [haproxy_backend.0.hash_type.method](defaults/main.yml#L317) | str | `consistent` |
| [haproxy_backend.0.http_request](defaults/main.yml#L343) | list |  |
| [haproxy_backend.0.http_request.0](defaults/main.yml#L344) | dict |  |
| [haproxy_backend.0.http_request.0.action](defaults/main.yml#L344) | str | `set-header` |
| [haproxy_backend.0.http_request.0.condition](defaults/main.yml#L346) | str | `!{ ssl_fc } is_root` |
| [haproxy_backend.0.http_request.0.params](defaults/main.yml#L345) | str | `Test-Header test-value` |
| [haproxy_backend.0.http_response](defaults/main.yml#L347) | list |  |
| [haproxy_backend.0.http_response.0](defaults/main.yml#L348) | dict |  |
| [haproxy_backend.0.http_response.0.action](defaults/main.yml#L348) | str | `replace-value` |
| [haproxy_backend.0.http_response.0.condition](defaults/main.yml#L350) | str | `is_root` |
| [haproxy_backend.0.http_response.0.params](defaults/main.yml#L349) | str | `Cache-control ^public$ private` |
| [haproxy_backend.0.mode](defaults/main.yml#L314) | str | `http` |
| [haproxy_backend.0.name](defaults/main.yml#L313) | str | `app` |
| [haproxy_backend.0.option](defaults/main.yml#L331) | list |  |
| [haproxy_backend.0.option.0](defaults/main.yml#L332) | dict |  |
| [haproxy_backend.0.option.0.name](defaults/main.yml#L332) | str | `forwardfor` |
| [haproxy_backend.0.option.1](defaults/main.yml#L333) | dict |  |
| [haproxy_backend.0.option.1.name](defaults/main.yml#L333) | str | `httpchk` |
| [haproxy_backend.0.option.1.params](defaults/main.yml#L334) | str | `/` |
| [haproxy_backend.0.server](defaults/main.yml#L354) | list |  |
| [haproxy_backend.0.server.0](defaults/main.yml#L355) | dict |  |
| [haproxy_backend.0.server.0.address](defaults/main.yml#L356) | str | `10.10.10.10` |
| [haproxy_backend.0.server.0.name](defaults/main.yml#L355) | str | `server1` |
| [haproxy_backend.0.server.0.params](defaults/main.yml#L358) | str | `check` |
| [haproxy_backend.0.server.0.port](defaults/main.yml#L357) | int | `6400` |
| [haproxy_backend.0.server.1](defaults/main.yml#L359) | dict |  |
| [haproxy_backend.0.server.1.address](defaults/main.yml#L360) | str | `10.10.10.11` |
| [haproxy_backend.0.server.1.name](defaults/main.yml#L359) | str | `server2` |
| [haproxy_backend.0.server.1.params](defaults/main.yml#L362) | str | `check` |
| [haproxy_backend.0.server.1.port](defaults/main.yml#L361) | int | `6400` |
| [haproxy_backend.0.stick](defaults/main.yml#L367) | list |  |
| [haproxy_backend.0.stick.0](defaults/main.yml#L368) | dict |  |
| [haproxy_backend.0.stick.0.pattern](defaults/main.yml#L369) | str | `res.cook(JSESSIONID)` |
| [haproxy_backend.0.stick.0.table](defaults/main.yml#L370) | str | `app` |
| [haproxy_backend.0.stick.0.type](defaults/main.yml#L368) | str | `store-response` |
| [haproxy_backend.0.stick.1](defaults/main.yml#L371) | dict |  |
| [haproxy_backend.0.stick.1.pattern](defaults/main.yml#L372) | str | `req.cook(JSESSIONID)` |
| [haproxy_backend.0.stick.1.type](defaults/main.yml#L371) | str | `on` |
| [haproxy_backend.0.stick_table](defaults/main.yml#L363) | dict |  |
| [haproxy_backend.0.stick_table.len](defaults/main.yml#L365) | int | `32` |
| [haproxy_backend.0.stick_table.size](defaults/main.yml#L366) | str | `1M` |
| [haproxy_backend.0.stick_table.type](defaults/main.yml#L364) | str | `string` |
| [haproxy_backend.0.timeout](defaults/main.yml#L335) | list |  |
| [haproxy_backend.0.timeout.0](defaults/main.yml#L336) | dict |  |
| [haproxy_backend.0.timeout.0.name](defaults/main.yml#L336) | str | `tunnel` |
| [haproxy_backend.0.timeout.0.value](defaults/main.yml#L337) | str | `86400s` |
| [haproxy_backend.0.use_server](defaults/main.yml#L351) | list |  |
| [haproxy_backend.0.use_server.0](defaults/main.yml#L352) | dict |  |
| [haproxy_backend.0.use_server.0.condition](defaults/main.yml#L353) | str | `hdr(host) -i test.nnc.guru` |
| [haproxy_backend.0.use_server.0.name](defaults/main.yml#L352) | str | `server1` |
| [haproxy_cert_dir](defaults/main.yml#L17) | str | `{{ haproxy_config_dir }}/certs` |
| [haproxy_cert_name](defaults/main.yml#L18) | str |  |
| [haproxy_config_dir](defaults/main.yml#L8) | str | `/etc/haproxy` |
| [haproxy_defaults](defaults/main.yml#L136) | dict |  |
| [haproxy_defaults.log](defaults/main.yml#L138) | list |  |
| [haproxy_defaults.log.0](defaults/main.yml#L139) | dict |  |
| [haproxy_defaults.log.0.global](defaults/main.yml#L139) | bool | `True` |
| [haproxy_defaults.maxconn](defaults/main.yml#L163) | int | `3000` |
| [haproxy_defaults.mode](defaults/main.yml#L137) | str | `http` |
| [haproxy_defaults.option](defaults/main.yml#L140) | list |  |
| [haproxy_defaults.option.0](defaults/main.yml#L141) | dict |  |
| [haproxy_defaults.option.0.name](defaults/main.yml#L141) | str | `httplog` |
| [haproxy_defaults.option.1](defaults/main.yml#L142) | dict |  |
| [haproxy_defaults.option.1.name](defaults/main.yml#L142) | str | `dontlognull` |
| [haproxy_defaults.option.2](defaults/main.yml#L143) | dict |  |
| [haproxy_defaults.option.2.name](defaults/main.yml#L143) | str | `http-server-close` |
| [haproxy_defaults.option.3](defaults/main.yml#L144) | dict |  |
| [haproxy_defaults.option.3.name](defaults/main.yml#L144) | str | `forwardfor` |
| [haproxy_defaults.option.3.params](defaults/main.yml#L145) | str | `except 127.0.0.0/8` |
| [haproxy_defaults.option.4](defaults/main.yml#L146) | dict |  |
| [haproxy_defaults.option.4.name](defaults/main.yml#L146) | str | `redispatch` |
| [haproxy_defaults.retries](defaults/main.yml#L147) | int | `3` |
| [haproxy_defaults.timeout](defaults/main.yml#L148) | list |  |
| [haproxy_defaults.timeout.0](defaults/main.yml#L149) | dict |  |
| [haproxy_defaults.timeout.0.name](defaults/main.yml#L149) | str | `http-request` |
| [haproxy_defaults.timeout.0.value](defaults/main.yml#L150) | str | `10s` |
| [haproxy_defaults.timeout.1](defaults/main.yml#L151) | dict |  |
| [haproxy_defaults.timeout.1.name](defaults/main.yml#L151) | str | `queue` |
| [haproxy_defaults.timeout.1.value](defaults/main.yml#L152) | str | `1m` |
| [haproxy_defaults.timeout.2](defaults/main.yml#L153) | dict |  |
| [haproxy_defaults.timeout.2.name](defaults/main.yml#L153) | str | `connect` |
| [haproxy_defaults.timeout.2.value](defaults/main.yml#L154) | str | `10s` |
| [haproxy_defaults.timeout.3](defaults/main.yml#L155) | dict |  |
| [haproxy_defaults.timeout.3.name](defaults/main.yml#L155) | str | `client` |
| [haproxy_defaults.timeout.3.value](defaults/main.yml#L156) | str | `1m` |
| [haproxy_defaults.timeout.4](defaults/main.yml#L157) | dict |  |
| [haproxy_defaults.timeout.4.name](defaults/main.yml#L157) | str | `server` |
| [haproxy_defaults.timeout.4.value](defaults/main.yml#L158) | str | `1m` |
| [haproxy_defaults.timeout.5](defaults/main.yml#L159) | dict |  |
| [haproxy_defaults.timeout.5.name](defaults/main.yml#L159) | str | `http-keep-alive` |
| [haproxy_defaults.timeout.5.value](defaults/main.yml#L160) | str | `10s` |
| [haproxy_defaults.timeout.6](defaults/main.yml#L161) | dict |  |
| [haproxy_defaults.timeout.6.name](defaults/main.yml#L161) | str | `check` |
| [haproxy_defaults.timeout.6.value](defaults/main.yml#L162) | str | `10s` |
| [haproxy_destination_config_path](defaults/main.yml#L9) | str | `{{ haproxy_config_dir }}/haproxy.cfg` |
| [haproxy_frontend](defaults/main.yml#L205) | list |  |
| [haproxy_frontend.0](defaults/main.yml#L206) | dict |  |
| [haproxy_frontend.0.backlog](defaults/main.yml#L213) | int | `10000` |
| [haproxy_frontend.0.bind](defaults/main.yml#L208) | list |  |
| [haproxy_frontend.0.bind.0](defaults/main.yml#L209) | dict |  |
| [haproxy_frontend.0.bind.0.address](defaults/main.yml#L209) | str | `127.0.0.1` |
| [haproxy_frontend.0.bind.0.port](defaults/main.yml#L210) | int | `5001` |
| [haproxy_frontend.0.bind.1](defaults/main.yml#L211) | dict |  |
| [haproxy_frontend.0.bind.1.address](defaults/main.yml#L211) | str | `127.0.0.1` |
| [haproxy_frontend.0.bind.1.port](defaults/main.yml#L212) | int | `5002` |
| [haproxy_frontend.0.default_backend](defaults/main.yml#L217) | str | `app` |
| [haproxy_frontend.0.mode](defaults/main.yml#L207) | str | `http` |
| [haproxy_frontend.0.name](defaults/main.yml#L206) | str | `main-http` |
| [haproxy_frontend.0.use_backend](defaults/main.yml#L214) | list |  |
| [haproxy_frontend.0.use_backend.0](defaults/main.yml#L215) | dict |  |
| [haproxy_frontend.0.use_backend.0.condition](defaults/main.yml#L216) | str | `!{ ssl_fc }` |
| [haproxy_frontend.0.use_backend.0.name](defaults/main.yml#L215) | str | `app` |
| [haproxy_frontend.1](defaults/main.yml#L218) | dict |  |
| [haproxy_frontend.1.acl](defaults/main.yml#L244) | list |  |
| [haproxy_frontend.1.acl.0](defaults/main.yml#L245) | dict |  |
| [haproxy_frontend.1.acl.0.fetch](defaults/main.yml#L246) | str | `path -i  /` |
| [haproxy_frontend.1.acl.0.name](defaults/main.yml#L245) | str | `is_root` |
| [haproxy_frontend.1.bind](defaults/main.yml#L220) | list |  |
| [haproxy_frontend.1.bind.0](defaults/main.yml#L221) | dict |  |
| [haproxy_frontend.1.bind.0.address](defaults/main.yml#L221) | str | `127.0.0.1` |
| [haproxy_frontend.1.bind.0.port](defaults/main.yml#L222) | int | `5003` |
| [haproxy_frontend.1.capture](defaults/main.yml#L236) | list |  |
| [haproxy_frontend.1.capture.0](defaults/main.yml#L237) | dict |  |
| [haproxy_frontend.1.capture.0.len](defaults/main.yml#L239) | int | `32` |
| [haproxy_frontend.1.capture.0.name](defaults/main.yml#L238) | str | `JSESSIONID` |
| [haproxy_frontend.1.capture.0.type](defaults/main.yml#L237) | str | `cookie` |
| [haproxy_frontend.1.capture.1](defaults/main.yml#L240) | dict |  |
| [haproxy_frontend.1.capture.1.len](defaults/main.yml#L242) | int | `15` |
| [haproxy_frontend.1.capture.1.name](defaults/main.yml#L241) | str | `Host` |
| [haproxy_frontend.1.capture.1.type](defaults/main.yml#L240) | str | `request header` |
| [haproxy_frontend.1.http_request](defaults/main.yml#L247) | list |  |
| [haproxy_frontend.1.http_request.0](defaults/main.yml#L248) | dict |  |
| [haproxy_frontend.1.http_request.0.action](defaults/main.yml#L248) | str | `set-header` |
| [haproxy_frontend.1.http_request.0.condition](defaults/main.yml#L250) | str | `!{ ssl_fc }` |
| [haproxy_frontend.1.http_request.0.params](defaults/main.yml#L249) | str | `X-Forwarded-Proto http` |
| [haproxy_frontend.1.mode](defaults/main.yml#L219) | str | `http` |
| [haproxy_frontend.1.monitor_uri](defaults/main.yml#L243) | str | `/haproxy` |
| [haproxy_frontend.1.name](defaults/main.yml#L218) | str | `main-https` |
| [haproxy_frontend.1.option](defaults/main.yml#L223) | list |  |
| [haproxy_frontend.1.option.0](defaults/main.yml#L224) | dict |  |
| [haproxy_frontend.1.option.0.name](defaults/main.yml#L224) | str | `contstats` |
| [haproxy_frontend.1.option.1](defaults/main.yml#L225) | dict |  |
| [haproxy_frontend.1.option.1.name](defaults/main.yml#L225) | str | `http-server-close` |
| [haproxy_frontend.1.option.2](defaults/main.yml#L226) | dict |  |
| [haproxy_frontend.1.option.2.name](defaults/main.yml#L226) | str | `httplog` |
| [haproxy_frontend.1.redirect](defaults/main.yml#L251) | list |  |
| [haproxy_frontend.1.redirect.0](defaults/main.yml#L252) | dict |  |
| [haproxy_frontend.1.redirect.0.code](defaults/main.yml#L254) | int | `301` |
| [haproxy_frontend.1.redirect.0.condition](defaults/main.yml#L256) | str | `!{ ssl_fc }` |
| [haproxy_frontend.1.redirect.0.option](defaults/main.yml#L255) | str | `drop-query` |
| [haproxy_frontend.1.redirect.0.type](defaults/main.yml#L252) | str | `scheme` |
| [haproxy_frontend.1.redirect.0.value](defaults/main.yml#L253) | str | `https` |
| [haproxy_frontend.1.timeout](defaults/main.yml#L227) | list |  |
| [haproxy_frontend.1.timeout.0](defaults/main.yml#L228) | dict |  |
| [haproxy_frontend.1.timeout.0.name](defaults/main.yml#L228) | str | `client` |
| [haproxy_frontend.1.timeout.0.value](defaults/main.yml#L229) | str | `300s` |
| [haproxy_frontend.1.timeout.1](defaults/main.yml#L230) | dict |  |
| [haproxy_frontend.1.timeout.1.name](defaults/main.yml#L230) | str | `http-keep-alive` |
| [haproxy_frontend.1.timeout.1.value](defaults/main.yml#L231) | str | `1s` |
| [haproxy_frontend.1.timeout.2](defaults/main.yml#L232) | dict |  |
| [haproxy_frontend.1.timeout.2.name](defaults/main.yml#L232) | str | `http-request` |
| [haproxy_frontend.1.timeout.2.value](defaults/main.yml#L233) | str | `15s` |
| [haproxy_frontend.1.timeout.3](defaults/main.yml#L234) | dict |  |
| [haproxy_frontend.1.timeout.3.name](defaults/main.yml#L234) | str | `tarpit` |
| [haproxy_frontend.1.timeout.3.value](defaults/main.yml#L235) | str | `60s` |
| [haproxy_frontend.1.use_backend](defaults/main.yml#L257) | list |  |
| [haproxy_frontend.1.use_backend.0](defaults/main.yml#L258) | dict |  |
| [haproxy_frontend.1.use_backend.0.condition](defaults/main.yml#L259) | str | `!{ ssl_fc }` |
| [haproxy_frontend.1.use_backend.0.name](defaults/main.yml#L258) | str | `app` |
| [haproxy_global](defaults/main.yml#L88) | dict |  |
| [haproxy_global.chroot](defaults/main.yml#L100) | str | `/var/lib/haproxy` |
| [haproxy_global.cpu_map](defaults/main.yml#L120) | str |  |
| [haproxy_global.daemon](defaults/main.yml#L105) | bool | `True` |
| [haproxy_global.group](defaults/main.yml#L104) | str | `haproxy` |
| [haproxy_global.log](defaults/main.yml#L89) | list |  |
| [haproxy_global.log.0](defaults/main.yml#L91) | dict |  |
| [haproxy_global.log.0.address](defaults/main.yml#L91) | str | `127.0.0.1` |
| [haproxy_global.log.0.facility](defaults/main.yml#L92) | str | `local0` |
| [haproxy_global.maxconn](defaults/main.yml#L102) | int | `4000` |
| [haproxy_global.nbthread](defaults/main.yml#L118) | int |  |
| [haproxy_global.pidfile](defaults/main.yml#L101) | str | `/var/run/haproxy.pid` |
| [haproxy_global.quiet](defaults/main.yml#L130) | bool |  |
| [haproxy_global.spread_checks](defaults/main.yml#L128) | int |  |
| [haproxy_global.stats_socket](defaults/main.yml#L106) | list |  |
| [haproxy_global.stats_socket.0](defaults/main.yml#L107) | dict |  |
| [haproxy_global.stats_socket.0.path](defaults/main.yml#L107) | str | `/var/lib/haproxy/stats` |
| [haproxy_global.tune](defaults/main.yml#L122) | dict |  |
| [haproxy_global.tune.bufsize](defaults/main.yml#L125) | int | `16384` |
| [haproxy_global.tune.maxrewrite](defaults/main.yml#L126) | int | `1024` |
| [haproxy_global.tune.ssl_cachesize](defaults/main.yml#L123) | int | `20000` |
| [haproxy_global.tune.ssl_lifetime](defaults/main.yml#L124) | int | `300` |
| [haproxy_global.tune_ssl_default_dh_param](defaults/main.yml#L99) | int | `2048` |
| [haproxy_global.user](defaults/main.yml#L103) | str | `haproxy` |
| [haproxy_ip_nonlocal_bind](defaults/main.yml#L82) | bool |  |
| [haproxy_letsencrypt](defaults/main.yml#L421) | dict |  |
| [haproxy_letsencrypt.cert_dir](defaults/main.yml#L427) | str | `/etc/letsencrypt/live` |
| [haproxy_letsencrypt.deploy_hook](defaults/main.yml#L429) | bool | `True` |
| [haproxy_letsencrypt.domains](defaults/main.yml#L425) | list |  |
| [haproxy_letsencrypt.enabled](defaults/main.yml#L423) | bool |  |
| [haproxy_listen](defaults/main.yml#L378) | list |  |
| [haproxy_listen.0](defaults/main.yml#L379) | dict |  |
| [haproxy_listen.0.bind](defaults/main.yml#L382) | list |  |
| [haproxy_listen.0.bind.0](defaults/main.yml#L383) | dict |  |
| [haproxy_listen.0.bind.0.address](defaults/main.yml#L383) | str | `127.0.0.1` |
| [haproxy_listen.0.bind.0.port](defaults/main.yml#L384) | int | `8000` |
| [haproxy_listen.0.mode](defaults/main.yml#L380) | str | `http` |
| [haproxy_listen.0.monitor_uri](defaults/main.yml#L381) | str | `/haproxy` |
| [haproxy_listen.0.name](defaults/main.yml#L379) | str | `http_health_check` |
| [haproxy_listen.0.option](defaults/main.yml#L385) | list |  |
| [haproxy_listen.0.option.0](defaults/main.yml#L386) | dict |  |
| [haproxy_listen.0.option.0.name](defaults/main.yml#L386) | str | `dontlognull` |
| [haproxy_listen.0.option.1](defaults/main.yml#L387) | dict |  |
| [haproxy_listen.0.option.1.name](defaults/main.yml#L387) | str | `httpchk` |
| [haproxy_listen.1](defaults/main.yml#L388) | dict |  |
| [haproxy_listen.1.bind](defaults/main.yml#L390) | list |  |
| [haproxy_listen.1.bind.0](defaults/main.yml#L391) | dict |  |
| [haproxy_listen.1.bind.0.address](defaults/main.yml#L391) | str | `127.0.0.1` |
| [haproxy_listen.1.bind.0.port](defaults/main.yml#L392) | int | `9000` |
| [haproxy_listen.1.mode](defaults/main.yml#L389) | str | `http` |
| [haproxy_listen.1.name](defaults/main.yml#L388) | str | `stats` |
| [haproxy_listen.1.stats](defaults/main.yml#L393) | dict |  |
| [haproxy_listen.1.stats.auth](defaults/main.yml#L400) | list |  |
| [haproxy_listen.1.stats.auth.0](defaults/main.yml#L401) | dict |  |
| [haproxy_listen.1.stats.auth.0.login](defaults/main.yml#L401) | str | `admin-user` |
| [haproxy_listen.1.stats.auth.0.password](defaults/main.yml#L402) | str | `password123` |
| [haproxy_listen.1.stats.enable](defaults/main.yml#L394) | bool | `True` |
| [haproxy_listen.1.stats.hide_version](defaults/main.yml#L395) | bool | `True` |
| [haproxy_listen.1.stats.realm](defaults/main.yml#L399) | str | `HAProxy\ Statistics` |
| [haproxy_listen.1.stats.refresh](defaults/main.yml#L403) | str | `5s` |
| [haproxy_listen.1.stats.scope](defaults/main.yml#L396) | list |  |
| [haproxy_listen.1.stats.scope.0](defaults/main.yml#L397) | str | `.` |
| [haproxy_listen.1.stats.uri](defaults/main.yml#L398) | str | `/admin?stats` |
| [haproxy_log_dir](defaults/main.yml#L10) | str | `/var/log/haproxy` |
| [haproxy_log_file](defaults/main.yml#L11) | str | `{{ haproxy_log_dir }}/haproxy.log` |
| [haproxy_logging](defaults/main.yml#L489) | dict |  |
| [haproxy_logging.capture_request_headers](defaults/main.yml#L495) | list |  |
| [haproxy_logging.capture_response_headers](defaults/main.yml#L497) | list |  |
| [haproxy_logging.custom_log_format](defaults/main.yml#L499) | str |  |
| [haproxy_logging.destination](defaults/main.yml#L491) | str | `/dev/log` |
| [haproxy_logging.facility](defaults/main.yml#L492) | str | `local0` |
| [haproxy_logging.level](defaults/main.yml#L493) | str | `info` |
| [haproxy_logging.logrotate](defaults/main.yml#L507) | dict |  |
| [haproxy_logging.logrotate.frequency](defaults/main.yml#L508) | str | `daily` |
| [haproxy_logging.logrotate.retain](defaults/main.yml#L509) | int | `14` |
| [haproxy_logging.per_backend_log_level](defaults/main.yml#L501) | dict |  |
| [haproxy_logging.rsyslog](defaults/main.yml#L503) | dict |  |
| [haproxy_logging.rsyslog.udp_listen](defaults/main.yml#L505) | bool |  |
| [haproxy_logrotate_file](defaults/main.yml#L12) | str | `/etc/logrotate.d/haproxy` |
| [haproxy_network_routes](defaults/main.yml#L48) | list |  |
| [haproxy_peers](defaults/main.yml#L543) | dict |  |
| [haproxy_peers.enabled](defaults/main.yml#L544) | bool |  |
| [haproxy_peers.name](defaults/main.yml#L545) | str | `haproxy_cluster` |
| [haproxy_peers.peers](defaults/main.yml#L546) | list |  |
| [haproxy_policy_routing](defaults/main.yml#L59) | dict |  |
| [haproxy_policy_routing.enabled](defaults/main.yml#L60) | bool |  |
| [haproxy_policy_routing.tables](defaults/main.yml#L61) | list |  |
| [haproxy_private_ip](defaults/main.yml#L30) | str |  |
| [haproxy_public_ip](defaults/main.yml#L25) | str |  |
| [haproxy_rate_limits](defaults/main.yml#L452) | list |  |
| [haproxy_security](defaults/main.yml#L465) | dict |  |
| [haproxy_security.hide_server_header](defaults/main.yml#L483) | bool |  |
| [haproxy_security.ip_blacklist](defaults/main.yml#L472) | dict |  |
| [haproxy_security.ip_blacklist.apply_to](defaults/main.yml#L477) | list |  |
| [haproxy_security.ip_blacklist.enabled](defaults/main.yml#L473) | bool |  |
| [haproxy_security.ip_blacklist.ips](defaults/main.yml#L475) | list |  |
| [haproxy_security.ip_whitelist](defaults/main.yml#L466) | dict |  |
| [haproxy_security.ip_whitelist.apply_to](defaults/main.yml#L471) | list |  |
| [haproxy_security.ip_whitelist.enabled](defaults/main.yml#L467) | bool |  |
| [haproxy_security.ip_whitelist.ips](defaults/main.yml#L469) | list |  |
| [haproxy_security.request_body_size_limit](defaults/main.yml#L478) | dict |  |
| [haproxy_security.request_body_size_limit.enabled](defaults/main.yml#L479) | bool |  |
| [haproxy_security.request_body_size_limit.max_bytes](defaults/main.yml#L481) | int | `10485760` |
| [haproxy_ssl](defaults/main.yml#L409) | dict |  |
| [haproxy_ssl.cert_dir](defaults/main.yml#L411) | str | `{{ haproxy_config_dir }}/certs` |
| [haproxy_ssl.default_bind_ciphers](defaults/main.yml#L413) | str |  |
| [haproxy_ssl.default_bind_options](defaults/main.yml#L415) | str |  |
| [haproxy_ssl.ocsp_stapling](defaults/main.yml#L419) | bool |  |
| [haproxy_ssl.session_cache_size](defaults/main.yml#L417) | int | `20000` |
| [haproxy_stats](defaults/main.yml#L515) | dict |  |
| [haproxy_stats.auth](defaults/main.yml#L522) | dict |  |
| [haproxy_stats.auth.enabled](defaults/main.yml#L523) | bool |  |
| [haproxy_stats.auth.password](defaults/main.yml#L525) | str |  |
| [haproxy_stats.auth.username](defaults/main.yml#L524) | str | `admin` |
| [haproxy_stats.bind_ip](defaults/main.yml#L518) | str | `127.0.0.1` |
| [haproxy_stats.enabled](defaults/main.yml#L517) | bool |  |
| [haproxy_stats.port](defaults/main.yml#L519) | int | `8404` |
| [haproxy_stats.prometheus](defaults/main.yml#L526) | dict |  |
| [haproxy_stats.prometheus.enabled](defaults/main.yml#L528) | bool |  |
| [haproxy_stats.prometheus.uri](defaults/main.yml#L529) | str | `/metrics` |
| [haproxy_stats.refresh](defaults/main.yml#L521) | str | `10s` |
| [haproxy_stats.runtime_api](defaults/main.yml#L530) | dict |  |
| [haproxy_stats.runtime_api.enabled](defaults/main.yml#L532) | bool |  |
| [haproxy_stats.runtime_api.level](defaults/main.yml#L534) | str | `admin` |
| [haproxy_stats.runtime_api.socket](defaults/main.yml#L533) | str | `/var/run/haproxy/admin.sock` |
| [haproxy_stats.uri](defaults/main.yml#L520) | str | `/stats` |
| [haproxy_stick_tables](defaults/main.yml#L437) | list |  |
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
| [Assert Let's Encrypt config when enabled](tasks/validation.yml#L) | ansible.builtin.assert | Yes | N/A |
| [Assert stats auth credentials when stats + auth enabled](tasks/validation.yml#L) | ansible.builtin.assert | Yes | N/A |
| [Assert peers list is non-empty when HA peers enabled](tasks/validation.yml#L) | ansible.builtin.assert | Yes | N/A |
| [Assert rate limit tables reference existing stick tables](tasks/validation.yml#L) | ansible.builtin.assert | No | N/A |
| [Assert static routes have required fields](tasks/validation.yml#L) | ansible.builtin.assert | No | N/A |
| [Assert policy routing tables have required fields](tasks/validation.yml#L) | ansible.builtin.assert | Yes | N/A |
| [Assert policy routing table numbers are unique](tasks/validation.yml#L) | ansible.builtin.assert | Yes | N/A |
| [Validate HAProxy configuration syntax](tasks/validation.yml#L) | ansible.builtin.command | No | N/A |




### File: `tasks/logging.yml`

| Task Name | Module | Has Conditions | Line |
|-----------|--------|----------------|------|
| [Install Rsyslog Package](tasks/logging.yml#L) | ansible.builtin.package | No | N/A |
| [Create HAProxy Log Directory](tasks/logging.yml#L) | ansible.builtin.file | No | N/A |
| [Deploy Rsyslog Configuration for HAProxy](tasks/logging.yml#L) | ansible.builtin.template | No | N/A |
| [Enable and Start Rsyslog Service](tasks/logging.yml#L) | ansible.builtin.service | Yes | N/A |
| [Deploy Logrotate Configuration for HAProxy](tasks/logging.yml#L) | ansible.builtin.template | No | N/A |




### File: `tasks/routing.yml`

| Task Name | Module | Has Conditions | Line |
|-----------|--------|----------------|------|
| [Set Routing State Facts](tasks/routing.yml#L) | ansible.builtin.set_fact | No | N/A |
| [Enable IP Non-Local Bind via Sysctl](tasks/routing.yml#L) | ansible.posix.sysctl | Yes | N/A |
| [Check Existing Static Routes](tasks/routing.yml#L) | ansible.builtin.command | Yes | N/A |
| [Apply Static Routes](tasks/routing.yml#L) | ansible.builtin.command | Yes | N/A |
| [Register Policy Routing Tables in rt_tables](tasks/routing.yml#L) | ansible.builtin.lineinfile | Yes | N/A |
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




### File: `tasks/ssl.yml`

| Task Name | Module | Has Conditions | Line |
|-----------|--------|----------------|------|
| [Create HAProxy SSL cert directory](tasks/ssl.yml#L) | ansible.builtin.file | No | N/A |
| [Combine Let's Encrypt certs into HAProxy PEM format](tasks/ssl.yml#L) | ansible.builtin.shell | No | N/A |
| [Set correct permissions on HAProxy PEM files](tasks/ssl.yml#L) | ansible.builtin.file | No | N/A |
| [Install Let's Encrypt renewal deploy-hook for HAProxy](tasks/ssl.yml#L) | ansible.builtin.copy | Yes | N/A |




### File: `tasks/install-Debian.yml`

| Task Name | Module | Has Conditions | Line |
|-----------|--------|----------------|------|
| [Install HAProxy from APT Repository](tasks/install-Debian.yml#L) | ansible.builtin.apt | No | N/A |




### File: `tasks/main.yml`

| Task Name | Module | Has Conditions | Line |
|-----------|--------|----------------|------|
| [Check Packages](tasks/main.yml#L) | ansible.builtin.package_facts | No | N/A |
| [Install HAProxy Package from Repository](tasks/main.yml#L) | ansible.builtin.include_tasks | Yes | N/A |
| [Create Certificate Folder](tasks/main.yml#L) | ansible.builtin.file | Yes | N/A |
| [Copy Certificate to Host](tasks/main.yml#L) | ansible.builtin.copy | Yes | N/A |
| [Create Whitelist Folder](tasks/main.yml#L) | ansible.builtin.file | Yes | N/A |
| [Copy Whitelist File to Host](tasks/main.yml#L) | ansible.builtin.copy | Yes | N/A |
| [Include Network Routing Tasks](tasks/main.yml#L) | ansible.builtin.include_tasks | No | N/A |
| [Create runtime API socket directory](tasks/main.yml#L) | ansible.builtin.file | Yes | N/A |
| [Include SSL certificate tasks](tasks/main.yml#L) | ansible.builtin.include_tasks | Yes | N/A |
| [Include Logging Tasks](tasks/main.yml#L) | ansible.builtin.include_tasks | No | N/A |
| [Configure haproxy using haproxy.cfg](tasks/main.yml#L) | ansible.builtin.template | No | N/A |
| [Run pre-flight validation checks](tasks/main.yml#L) | ansible.builtin.include_tasks | No | N/A |




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


license (GPL-2.0-or-later, MIT, etc)


## Author Information


**Author:** gkorkmaz




**GitHub:** [gkorkmaz](https://github.com/gkorkmaz)

---
*This documentation was automatically generated using [docsible](https://github.com/zbohm/docsible).*
<!-- DOCSIBLE END -->
