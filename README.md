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
| [haproxy_backend](defaults/main.yml#L311) | list |  |
| [haproxy_backend.0](defaults/main.yml#L312) | dict |  |
| [haproxy_backend.0.acl](defaults/main.yml#L337) | list |  |
| [haproxy_backend.0.acl.0](defaults/main.yml#L338) | dict |  |
| [haproxy_backend.0.acl.0.fetch](defaults/main.yml#L339) | str | `path -i /` |
| [haproxy_backend.0.acl.0.name](defaults/main.yml#L338) | str | `is_root` |
| [haproxy_backend.0.acl.1](defaults/main.yml#L340) | dict |  |
| [haproxy_backend.0.acl.1.fetch](defaults/main.yml#L341) | str | `res.hdr(Set-cookie) -m sub Path=` |
| [haproxy_backend.0.acl.1.name](defaults/main.yml#L340) | str | `hdr_set_cookie_path` |
| [haproxy_backend.0.balance](defaults/main.yml#L314) | str | `source` |
| [haproxy_backend.0.compression](defaults/main.yml#L318) | dict |  |
| [haproxy_backend.0.compression.algo](defaults/main.yml#L319) | str | `gzip` |
| [haproxy_backend.0.compression.type](defaults/main.yml#L320) | list |  |
| [haproxy_backend.0.compression.type.0](defaults/main.yml#L321) | str | `text/plain` |
| [haproxy_backend.0.compression.type.1](defaults/main.yml#L322) | str | `text/css` |
| [haproxy_backend.0.compression.type.2](defaults/main.yml#L323) | str | `application/json` |
| [haproxy_backend.0.compression.type.3](defaults/main.yml#L324) | str | `application/x-javascript` |
| [haproxy_backend.0.compression.type.4](defaults/main.yml#L325) | str | `text/xml` |
| [haproxy_backend.0.compression.type.5](defaults/main.yml#L326) | str | `application/xml` |
| [haproxy_backend.0.compression.type.6](defaults/main.yml#L327) | str | `application/xml+rss` |
| [haproxy_backend.0.compression.type.7](defaults/main.yml#L328) | str | `text/javascript` |
| [haproxy_backend.0.compression.type.8](defaults/main.yml#L329) | str | `application/javascript` |
| [haproxy_backend.0.hash_type](defaults/main.yml#L315) | dict |  |
| [haproxy_backend.0.hash_type.function](defaults/main.yml#L317) | str | `djb2` |
| [haproxy_backend.0.hash_type.method](defaults/main.yml#L316) | str | `consistent` |
| [haproxy_backend.0.http_request](defaults/main.yml#L342) | list |  |
| [haproxy_backend.0.http_request.0](defaults/main.yml#L343) | dict |  |
| [haproxy_backend.0.http_request.0.action](defaults/main.yml#L343) | str | `set-header` |
| [haproxy_backend.0.http_request.0.condition](defaults/main.yml#L345) | str | `!{ ssl_fc } is_root` |
| [haproxy_backend.0.http_request.0.params](defaults/main.yml#L344) | str | `Test-Header test-value` |
| [haproxy_backend.0.http_response](defaults/main.yml#L346) | list |  |
| [haproxy_backend.0.http_response.0](defaults/main.yml#L347) | dict |  |
| [haproxy_backend.0.http_response.0.action](defaults/main.yml#L347) | str | `replace-value` |
| [haproxy_backend.0.http_response.0.condition](defaults/main.yml#L349) | str | `is_root` |
| [haproxy_backend.0.http_response.0.params](defaults/main.yml#L348) | str | `Cache-control ^public$ private` |
| [haproxy_backend.0.mode](defaults/main.yml#L313) | str | `http` |
| [haproxy_backend.0.name](defaults/main.yml#L312) | str | `app` |
| [haproxy_backend.0.option](defaults/main.yml#L330) | list |  |
| [haproxy_backend.0.option.0](defaults/main.yml#L331) | dict |  |
| [haproxy_backend.0.option.0.name](defaults/main.yml#L331) | str | `forwardfor` |
| [haproxy_backend.0.option.1](defaults/main.yml#L332) | dict |  |
| [haproxy_backend.0.option.1.name](defaults/main.yml#L332) | str | `httpchk` |
| [haproxy_backend.0.option.1.params](defaults/main.yml#L333) | str | `/` |
| [haproxy_backend.0.server](defaults/main.yml#L353) | list |  |
| [haproxy_backend.0.server.0](defaults/main.yml#L354) | dict |  |
| [haproxy_backend.0.server.0.address](defaults/main.yml#L355) | str | `10.10.10.10` |
| [haproxy_backend.0.server.0.name](defaults/main.yml#L354) | str | `server1` |
| [haproxy_backend.0.server.0.params](defaults/main.yml#L357) | str | `check` |
| [haproxy_backend.0.server.0.port](defaults/main.yml#L356) | int | `6400` |
| [haproxy_backend.0.server.1](defaults/main.yml#L358) | dict |  |
| [haproxy_backend.0.server.1.address](defaults/main.yml#L359) | str | `10.10.10.11` |
| [haproxy_backend.0.server.1.name](defaults/main.yml#L358) | str | `server2` |
| [haproxy_backend.0.server.1.params](defaults/main.yml#L361) | str | `check` |
| [haproxy_backend.0.server.1.port](defaults/main.yml#L360) | int | `6400` |
| [haproxy_backend.0.stick](defaults/main.yml#L366) | list |  |
| [haproxy_backend.0.stick.0](defaults/main.yml#L367) | dict |  |
| [haproxy_backend.0.stick.0.pattern](defaults/main.yml#L368) | str | `res.cook(JSESSIONID)` |
| [haproxy_backend.0.stick.0.table](defaults/main.yml#L369) | str | `app` |
| [haproxy_backend.0.stick.0.type](defaults/main.yml#L367) | str | `store-response` |
| [haproxy_backend.0.stick.1](defaults/main.yml#L370) | dict |  |
| [haproxy_backend.0.stick.1.pattern](defaults/main.yml#L371) | str | `req.cook(JSESSIONID)` |
| [haproxy_backend.0.stick.1.type](defaults/main.yml#L370) | str | `on` |
| [haproxy_backend.0.stick_table](defaults/main.yml#L362) | dict |  |
| [haproxy_backend.0.stick_table.len](defaults/main.yml#L364) | int | `32` |
| [haproxy_backend.0.stick_table.size](defaults/main.yml#L365) | str | `1M` |
| [haproxy_backend.0.stick_table.type](defaults/main.yml#L363) | str | `string` |
| [haproxy_backend.0.timeout](defaults/main.yml#L334) | list |  |
| [haproxy_backend.0.timeout.0](defaults/main.yml#L335) | dict |  |
| [haproxy_backend.0.timeout.0.name](defaults/main.yml#L335) | str | `tunnel` |
| [haproxy_backend.0.timeout.0.value](defaults/main.yml#L336) | str | `86400s` |
| [haproxy_backend.0.use_server](defaults/main.yml#L350) | list |  |
| [haproxy_backend.0.use_server.0](defaults/main.yml#L351) | dict |  |
| [haproxy_backend.0.use_server.0.condition](defaults/main.yml#L352) | str | `hdr(host) -i test.nnc.guru` |
| [haproxy_backend.0.use_server.0.name](defaults/main.yml#L351) | str | `server1` |
| [haproxy_cert_dir](defaults/main.yml#L16) | str | `{{ haproxy_config_dir }}/certs` |
| [haproxy_cert_name](defaults/main.yml#L17) | str |  |
| [haproxy_config_dir](defaults/main.yml#L8) | str | `/etc/haproxy` |
| [haproxy_defaults](defaults/main.yml#L135) | dict |  |
| [haproxy_defaults.log](defaults/main.yml#L137) | list |  |
| [haproxy_defaults.log.0](defaults/main.yml#L138) | dict |  |
| [haproxy_defaults.log.0.global](defaults/main.yml#L138) | bool | `True` |
| [haproxy_defaults.maxconn](defaults/main.yml#L162) | int | `3000` |
| [haproxy_defaults.mode](defaults/main.yml#L136) | str | `http` |
| [haproxy_defaults.option](defaults/main.yml#L139) | list |  |
| [haproxy_defaults.option.0](defaults/main.yml#L140) | dict |  |
| [haproxy_defaults.option.0.name](defaults/main.yml#L140) | str | `httplog` |
| [haproxy_defaults.option.1](defaults/main.yml#L141) | dict |  |
| [haproxy_defaults.option.1.name](defaults/main.yml#L141) | str | `dontlognull` |
| [haproxy_defaults.option.2](defaults/main.yml#L142) | dict |  |
| [haproxy_defaults.option.2.name](defaults/main.yml#L142) | str | `http-server-close` |
| [haproxy_defaults.option.3](defaults/main.yml#L143) | dict |  |
| [haproxy_defaults.option.3.name](defaults/main.yml#L143) | str | `forwardfor` |
| [haproxy_defaults.option.3.params](defaults/main.yml#L144) | str | `except 127.0.0.0/8` |
| [haproxy_defaults.option.4](defaults/main.yml#L145) | dict |  |
| [haproxy_defaults.option.4.name](defaults/main.yml#L145) | str | `redispatch` |
| [haproxy_defaults.retries](defaults/main.yml#L146) | int | `3` |
| [haproxy_defaults.timeout](defaults/main.yml#L147) | list |  |
| [haproxy_defaults.timeout.0](defaults/main.yml#L148) | dict |  |
| [haproxy_defaults.timeout.0.name](defaults/main.yml#L148) | str | `http-request` |
| [haproxy_defaults.timeout.0.value](defaults/main.yml#L149) | str | `10s` |
| [haproxy_defaults.timeout.1](defaults/main.yml#L150) | dict |  |
| [haproxy_defaults.timeout.1.name](defaults/main.yml#L150) | str | `queue` |
| [haproxy_defaults.timeout.1.value](defaults/main.yml#L151) | str | `1m` |
| [haproxy_defaults.timeout.2](defaults/main.yml#L152) | dict |  |
| [haproxy_defaults.timeout.2.name](defaults/main.yml#L152) | str | `connect` |
| [haproxy_defaults.timeout.2.value](defaults/main.yml#L153) | str | `10s` |
| [haproxy_defaults.timeout.3](defaults/main.yml#L154) | dict |  |
| [haproxy_defaults.timeout.3.name](defaults/main.yml#L154) | str | `client` |
| [haproxy_defaults.timeout.3.value](defaults/main.yml#L155) | str | `1m` |
| [haproxy_defaults.timeout.4](defaults/main.yml#L156) | dict |  |
| [haproxy_defaults.timeout.4.name](defaults/main.yml#L156) | str | `server` |
| [haproxy_defaults.timeout.4.value](defaults/main.yml#L157) | str | `1m` |
| [haproxy_defaults.timeout.5](defaults/main.yml#L158) | dict |  |
| [haproxy_defaults.timeout.5.name](defaults/main.yml#L158) | str | `http-keep-alive` |
| [haproxy_defaults.timeout.5.value](defaults/main.yml#L159) | str | `10s` |
| [haproxy_defaults.timeout.6](defaults/main.yml#L160) | dict |  |
| [haproxy_defaults.timeout.6.name](defaults/main.yml#L160) | str | `check` |
| [haproxy_defaults.timeout.6.value](defaults/main.yml#L161) | str | `10s` |
| [haproxy_destination_config_path](defaults/main.yml#L9) | str | `{{ haproxy_config_dir }}/haproxy.cfg` |
| [haproxy_frontend](defaults/main.yml#L204) | list |  |
| [haproxy_frontend.0](defaults/main.yml#L205) | dict |  |
| [haproxy_frontend.0.backlog](defaults/main.yml#L212) | int | `10000` |
| [haproxy_frontend.0.bind](defaults/main.yml#L207) | list |  |
| [haproxy_frontend.0.bind.0](defaults/main.yml#L208) | dict |  |
| [haproxy_frontend.0.bind.0.address](defaults/main.yml#L208) | str | `127.0.0.1` |
| [haproxy_frontend.0.bind.0.port](defaults/main.yml#L209) | int | `5001` |
| [haproxy_frontend.0.bind.1](defaults/main.yml#L210) | dict |  |
| [haproxy_frontend.0.bind.1.address](defaults/main.yml#L210) | str | `127.0.0.1` |
| [haproxy_frontend.0.bind.1.port](defaults/main.yml#L211) | int | `5002` |
| [haproxy_frontend.0.default_backend](defaults/main.yml#L216) | str | `app` |
| [haproxy_frontend.0.mode](defaults/main.yml#L206) | str | `http` |
| [haproxy_frontend.0.name](defaults/main.yml#L205) | str | `main-http` |
| [haproxy_frontend.0.use_backend](defaults/main.yml#L213) | list |  |
| [haproxy_frontend.0.use_backend.0](defaults/main.yml#L214) | dict |  |
| [haproxy_frontend.0.use_backend.0.condition](defaults/main.yml#L215) | str | `!{ ssl_fc }` |
| [haproxy_frontend.0.use_backend.0.name](defaults/main.yml#L214) | str | `app` |
| [haproxy_frontend.1](defaults/main.yml#L217) | dict |  |
| [haproxy_frontend.1.acl](defaults/main.yml#L243) | list |  |
| [haproxy_frontend.1.acl.0](defaults/main.yml#L244) | dict |  |
| [haproxy_frontend.1.acl.0.fetch](defaults/main.yml#L245) | str | `path -i  /` |
| [haproxy_frontend.1.acl.0.name](defaults/main.yml#L244) | str | `is_root` |
| [haproxy_frontend.1.bind](defaults/main.yml#L219) | list |  |
| [haproxy_frontend.1.bind.0](defaults/main.yml#L220) | dict |  |
| [haproxy_frontend.1.bind.0.address](defaults/main.yml#L220) | str | `127.0.0.1` |
| [haproxy_frontend.1.bind.0.port](defaults/main.yml#L221) | int | `5003` |
| [haproxy_frontend.1.capture](defaults/main.yml#L235) | list |  |
| [haproxy_frontend.1.capture.0](defaults/main.yml#L236) | dict |  |
| [haproxy_frontend.1.capture.0.len](defaults/main.yml#L238) | int | `32` |
| [haproxy_frontend.1.capture.0.name](defaults/main.yml#L237) | str | `JSESSIONID` |
| [haproxy_frontend.1.capture.0.type](defaults/main.yml#L236) | str | `cookie` |
| [haproxy_frontend.1.capture.1](defaults/main.yml#L239) | dict |  |
| [haproxy_frontend.1.capture.1.len](defaults/main.yml#L241) | int | `15` |
| [haproxy_frontend.1.capture.1.name](defaults/main.yml#L240) | str | `Host` |
| [haproxy_frontend.1.capture.1.type](defaults/main.yml#L239) | str | `request header` |
| [haproxy_frontend.1.http_request](defaults/main.yml#L246) | list |  |
| [haproxy_frontend.1.http_request.0](defaults/main.yml#L247) | dict |  |
| [haproxy_frontend.1.http_request.0.action](defaults/main.yml#L247) | str | `set-header` |
| [haproxy_frontend.1.http_request.0.condition](defaults/main.yml#L249) | str | `!{ ssl_fc }` |
| [haproxy_frontend.1.http_request.0.params](defaults/main.yml#L248) | str | `X-Forwarded-Proto http` |
| [haproxy_frontend.1.mode](defaults/main.yml#L218) | str | `http` |
| [haproxy_frontend.1.monitor_uri](defaults/main.yml#L242) | str | `/haproxy` |
| [haproxy_frontend.1.name](defaults/main.yml#L217) | str | `main-https` |
| [haproxy_frontend.1.option](defaults/main.yml#L222) | list |  |
| [haproxy_frontend.1.option.0](defaults/main.yml#L223) | dict |  |
| [haproxy_frontend.1.option.0.name](defaults/main.yml#L223) | str | `contstats` |
| [haproxy_frontend.1.option.1](defaults/main.yml#L224) | dict |  |
| [haproxy_frontend.1.option.1.name](defaults/main.yml#L224) | str | `http-server-close` |
| [haproxy_frontend.1.option.2](defaults/main.yml#L225) | dict |  |
| [haproxy_frontend.1.option.2.name](defaults/main.yml#L225) | str | `httplog` |
| [haproxy_frontend.1.redirect](defaults/main.yml#L250) | list |  |
| [haproxy_frontend.1.redirect.0](defaults/main.yml#L251) | dict |  |
| [haproxy_frontend.1.redirect.0.code](defaults/main.yml#L253) | int | `301` |
| [haproxy_frontend.1.redirect.0.condition](defaults/main.yml#L255) | str | `!{ ssl_fc }` |
| [haproxy_frontend.1.redirect.0.option](defaults/main.yml#L254) | str | `drop-query` |
| [haproxy_frontend.1.redirect.0.type](defaults/main.yml#L251) | str | `scheme` |
| [haproxy_frontend.1.redirect.0.value](defaults/main.yml#L252) | str | `https` |
| [haproxy_frontend.1.timeout](defaults/main.yml#L226) | list |  |
| [haproxy_frontend.1.timeout.0](defaults/main.yml#L227) | dict |  |
| [haproxy_frontend.1.timeout.0.name](defaults/main.yml#L227) | str | `client` |
| [haproxy_frontend.1.timeout.0.value](defaults/main.yml#L228) | str | `300s` |
| [haproxy_frontend.1.timeout.1](defaults/main.yml#L229) | dict |  |
| [haproxy_frontend.1.timeout.1.name](defaults/main.yml#L229) | str | `http-keep-alive` |
| [haproxy_frontend.1.timeout.1.value](defaults/main.yml#L230) | str | `1s` |
| [haproxy_frontend.1.timeout.2](defaults/main.yml#L231) | dict |  |
| [haproxy_frontend.1.timeout.2.name](defaults/main.yml#L231) | str | `http-request` |
| [haproxy_frontend.1.timeout.2.value](defaults/main.yml#L232) | str | `15s` |
| [haproxy_frontend.1.timeout.3](defaults/main.yml#L233) | dict |  |
| [haproxy_frontend.1.timeout.3.name](defaults/main.yml#L233) | str | `tarpit` |
| [haproxy_frontend.1.timeout.3.value](defaults/main.yml#L234) | str | `60s` |
| [haproxy_frontend.1.use_backend](defaults/main.yml#L256) | list |  |
| [haproxy_frontend.1.use_backend.0](defaults/main.yml#L257) | dict |  |
| [haproxy_frontend.1.use_backend.0.condition](defaults/main.yml#L258) | str | `!{ ssl_fc }` |
| [haproxy_frontend.1.use_backend.0.name](defaults/main.yml#L257) | str | `app` |
| [haproxy_global](defaults/main.yml#L87) | dict |  |
| [haproxy_global.chroot](defaults/main.yml#L99) | str | `/var/lib/haproxy` |
| [haproxy_global.cpu_map](defaults/main.yml#L119) | str |  |
| [haproxy_global.daemon](defaults/main.yml#L104) | bool | `True` |
| [haproxy_global.group](defaults/main.yml#L103) | str | `haproxy` |
| [haproxy_global.log](defaults/main.yml#L88) | list |  |
| [haproxy_global.log.0](defaults/main.yml#L90) | dict |  |
| [haproxy_global.log.0.address](defaults/main.yml#L90) | str | `127.0.0.1` |
| [haproxy_global.log.0.facility](defaults/main.yml#L91) | str | `local0` |
| [haproxy_global.maxconn](defaults/main.yml#L101) | int | `4000` |
| [haproxy_global.nbthread](defaults/main.yml#L117) | int |  |
| [haproxy_global.pidfile](defaults/main.yml#L100) | str | `/var/run/haproxy.pid` |
| [haproxy_global.quiet](defaults/main.yml#L129) | bool |  |
| [haproxy_global.spread_checks](defaults/main.yml#L127) | int |  |
| [haproxy_global.stats_socket](defaults/main.yml#L105) | list |  |
| [haproxy_global.stats_socket.0](defaults/main.yml#L106) | dict |  |
| [haproxy_global.stats_socket.0.path](defaults/main.yml#L106) | str | `/var/lib/haproxy/stats` |
| [haproxy_global.tune](defaults/main.yml#L121) | dict |  |
| [haproxy_global.tune.bufsize](defaults/main.yml#L124) | int | `16384` |
| [haproxy_global.tune.maxrewrite](defaults/main.yml#L125) | int | `1024` |
| [haproxy_global.tune.ssl_cachesize](defaults/main.yml#L122) | int | `20000` |
| [haproxy_global.tune.ssl_lifetime](defaults/main.yml#L123) | int | `300` |
| [haproxy_global.tune_ssl_default_dh_param](defaults/main.yml#L98) | int | `2048` |
| [haproxy_global.user](defaults/main.yml#L102) | str | `haproxy` |
| [haproxy_ip_nonlocal_bind](defaults/main.yml#L81) | bool |  |
| [haproxy_letsencrypt](defaults/main.yml#L420) | dict |  |
| [haproxy_letsencrypt.cert_dir](defaults/main.yml#L426) | str | `/etc/letsencrypt/live` |
| [haproxy_letsencrypt.deploy_hook](defaults/main.yml#L428) | bool | `True` |
| [haproxy_letsencrypt.domains](defaults/main.yml#L424) | list |  |
| [haproxy_letsencrypt.enabled](defaults/main.yml#L422) | bool |  |
| [haproxy_listen](defaults/main.yml#L377) | list |  |
| [haproxy_listen.0](defaults/main.yml#L378) | dict |  |
| [haproxy_listen.0.bind](defaults/main.yml#L381) | list |  |
| [haproxy_listen.0.bind.0](defaults/main.yml#L382) | dict |  |
| [haproxy_listen.0.bind.0.address](defaults/main.yml#L382) | str | `127.0.0.1` |
| [haproxy_listen.0.bind.0.port](defaults/main.yml#L383) | int | `8000` |
| [haproxy_listen.0.mode](defaults/main.yml#L379) | str | `http` |
| [haproxy_listen.0.monitor_uri](defaults/main.yml#L380) | str | `/haproxy` |
| [haproxy_listen.0.name](defaults/main.yml#L378) | str | `http_health_check` |
| [haproxy_listen.0.option](defaults/main.yml#L384) | list |  |
| [haproxy_listen.0.option.0](defaults/main.yml#L385) | dict |  |
| [haproxy_listen.0.option.0.name](defaults/main.yml#L385) | str | `dontlognull` |
| [haproxy_listen.0.option.1](defaults/main.yml#L386) | dict |  |
| [haproxy_listen.0.option.1.name](defaults/main.yml#L386) | str | `httpchk` |
| [haproxy_listen.1](defaults/main.yml#L387) | dict |  |
| [haproxy_listen.1.bind](defaults/main.yml#L389) | list |  |
| [haproxy_listen.1.bind.0](defaults/main.yml#L390) | dict |  |
| [haproxy_listen.1.bind.0.address](defaults/main.yml#L390) | str | `127.0.0.1` |
| [haproxy_listen.1.bind.0.port](defaults/main.yml#L391) | int | `9000` |
| [haproxy_listen.1.mode](defaults/main.yml#L388) | str | `http` |
| [haproxy_listen.1.name](defaults/main.yml#L387) | str | `stats` |
| [haproxy_listen.1.stats](defaults/main.yml#L392) | dict |  |
| [haproxy_listen.1.stats.auth](defaults/main.yml#L399) | list |  |
| [haproxy_listen.1.stats.auth.0](defaults/main.yml#L400) | dict |  |
| [haproxy_listen.1.stats.auth.0.login](defaults/main.yml#L400) | str | `admin-user` |
| [haproxy_listen.1.stats.auth.0.password](defaults/main.yml#L401) | str | `password123` |
| [haproxy_listen.1.stats.enable](defaults/main.yml#L393) | bool | `True` |
| [haproxy_listen.1.stats.hide_version](defaults/main.yml#L394) | bool | `True` |
| [haproxy_listen.1.stats.realm](defaults/main.yml#L398) | str | `HAProxy\ Statistics` |
| [haproxy_listen.1.stats.refresh](defaults/main.yml#L402) | str | `5s` |
| [haproxy_listen.1.stats.scope](defaults/main.yml#L395) | list |  |
| [haproxy_listen.1.stats.scope.0](defaults/main.yml#L396) | str | `.` |
| [haproxy_listen.1.stats.uri](defaults/main.yml#L397) | str | `/admin?stats` |
| [haproxy_log_file](defaults/main.yml#L10) | str | `/var/log/haproxy.log` |
| [haproxy_logging](defaults/main.yml#L488) | dict |  |
| [haproxy_logging.capture_request_headers](defaults/main.yml#L494) | list |  |
| [haproxy_logging.capture_response_headers](defaults/main.yml#L496) | list |  |
| [haproxy_logging.custom_log_format](defaults/main.yml#L498) | str |  |
| [haproxy_logging.destination](defaults/main.yml#L490) | str | `/dev/log` |
| [haproxy_logging.facility](defaults/main.yml#L491) | str | `local0` |
| [haproxy_logging.level](defaults/main.yml#L492) | str | `info` |
| [haproxy_logging.per_backend_log_level](defaults/main.yml#L500) | dict |  |
| [haproxy_logrotate_file](defaults/main.yml#L11) | str | `/etc/logrotate.d/haproxy` |
| [haproxy_network_routes](defaults/main.yml#L47) | list |  |
| [haproxy_peers](defaults/main.yml#L534) | dict |  |
| [haproxy_peers.enabled](defaults/main.yml#L535) | bool |  |
| [haproxy_peers.name](defaults/main.yml#L536) | str | `haproxy_cluster` |
| [haproxy_peers.peers](defaults/main.yml#L537) | list |  |
| [haproxy_policy_routing](defaults/main.yml#L58) | dict |  |
| [haproxy_policy_routing.enabled](defaults/main.yml#L59) | bool |  |
| [haproxy_policy_routing.tables](defaults/main.yml#L60) | list |  |
| [haproxy_private_ip](defaults/main.yml#L29) | str |  |
| [haproxy_public_ip](defaults/main.yml#L24) | str |  |
| [haproxy_rate_limits](defaults/main.yml#L451) | list |  |
| [haproxy_security](defaults/main.yml#L464) | dict |  |
| [haproxy_security.hide_server_header](defaults/main.yml#L482) | bool |  |
| [haproxy_security.ip_blacklist](defaults/main.yml#L471) | dict |  |
| [haproxy_security.ip_blacklist.apply_to](defaults/main.yml#L476) | list |  |
| [haproxy_security.ip_blacklist.enabled](defaults/main.yml#L472) | bool |  |
| [haproxy_security.ip_blacklist.ips](defaults/main.yml#L474) | list |  |
| [haproxy_security.ip_whitelist](defaults/main.yml#L465) | dict |  |
| [haproxy_security.ip_whitelist.apply_to](defaults/main.yml#L470) | list |  |
| [haproxy_security.ip_whitelist.enabled](defaults/main.yml#L466) | bool |  |
| [haproxy_security.ip_whitelist.ips](defaults/main.yml#L468) | list |  |
| [haproxy_security.request_body_size_limit](defaults/main.yml#L477) | dict |  |
| [haproxy_security.request_body_size_limit.enabled](defaults/main.yml#L478) | bool |  |
| [haproxy_security.request_body_size_limit.max_bytes](defaults/main.yml#L480) | int | `10485760` |
| [haproxy_ssl](defaults/main.yml#L408) | dict |  |
| [haproxy_ssl.cert_dir](defaults/main.yml#L410) | str | `{{ haproxy_config_dir }}/certs` |
| [haproxy_ssl.default_bind_ciphers](defaults/main.yml#L412) | str |  |
| [haproxy_ssl.default_bind_options](defaults/main.yml#L414) | str |  |
| [haproxy_ssl.ocsp_stapling](defaults/main.yml#L418) | bool |  |
| [haproxy_ssl.session_cache_size](defaults/main.yml#L416) | int | `20000` |
| [haproxy_stats](defaults/main.yml#L506) | dict |  |
| [haproxy_stats.auth](defaults/main.yml#L513) | dict |  |
| [haproxy_stats.auth.enabled](defaults/main.yml#L514) | bool |  |
| [haproxy_stats.auth.password](defaults/main.yml#L516) | str |  |
| [haproxy_stats.auth.username](defaults/main.yml#L515) | str | `admin` |
| [haproxy_stats.bind_ip](defaults/main.yml#L509) | str | `127.0.0.1` |
| [haproxy_stats.enabled](defaults/main.yml#L508) | bool |  |
| [haproxy_stats.port](defaults/main.yml#L510) | int | `8404` |
| [haproxy_stats.prometheus](defaults/main.yml#L517) | dict |  |
| [haproxy_stats.prometheus.enabled](defaults/main.yml#L519) | bool |  |
| [haproxy_stats.prometheus.uri](defaults/main.yml#L520) | str | `/metrics` |
| [haproxy_stats.refresh](defaults/main.yml#L512) | str | `10s` |
| [haproxy_stats.runtime_api](defaults/main.yml#L521) | dict |  |
| [haproxy_stats.runtime_api.enabled](defaults/main.yml#L523) | bool |  |
| [haproxy_stats.runtime_api.level](defaults/main.yml#L525) | str | `admin` |
| [haproxy_stats.runtime_api.socket](defaults/main.yml#L524) | str | `/var/run/haproxy/admin.sock` |
| [haproxy_stats.uri](defaults/main.yml#L511) | str | `/stats` |
| [haproxy_stick_tables](defaults/main.yml#L436) | list |  |
| [haproxy_whitelist_file_dir](defaults/main.yml#L13) | str | `{{ haproxy_config_dir }}/whitelist` |
| [haproxy_whitelist_file_name](defaults/main.yml#L14) | str |  |




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
        haproxy_log_file: /var/log/haproxy.log

```

## License


license (GPL-2.0-or-later, MIT, etc)


## Author Information


**Author:** gkorkmaz




**GitHub:** [gkorkmaz](https://github.com/gkorkmaz)

---
*This documentation was automatically generated using [docsible](https://github.com/zbohm/docsible).*
<!-- DOCSIBLE END -->
