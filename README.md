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
| [haproxy_backend](defaults/main.yml#L336) | list |  |
| [haproxy_backend.0](defaults/main.yml#L337) | dict |  |
| [haproxy_backend.0.acl](defaults/main.yml#L362) | list |  |
| [haproxy_backend.0.acl.0](defaults/main.yml#L363) | dict |  |
| [haproxy_backend.0.acl.0.fetch](defaults/main.yml#L364) | str | `path -i /` |
| [haproxy_backend.0.acl.0.name](defaults/main.yml#L363) | str | `is_root` |
| [haproxy_backend.0.acl.1](defaults/main.yml#L365) | dict |  |
| [haproxy_backend.0.acl.1.fetch](defaults/main.yml#L366) | str | `res.hdr(Set-cookie) -m sub Path=` |
| [haproxy_backend.0.acl.1.name](defaults/main.yml#L365) | str | `hdr_set_cookie_path` |
| [haproxy_backend.0.balance](defaults/main.yml#L339) | str | `source` |
| [haproxy_backend.0.compression](defaults/main.yml#L343) | dict |  |
| [haproxy_backend.0.compression.algo](defaults/main.yml#L344) | str | `gzip` |
| [haproxy_backend.0.compression.type](defaults/main.yml#L345) | list |  |
| [haproxy_backend.0.compression.type.0](defaults/main.yml#L346) | str | `text/plain` |
| [haproxy_backend.0.compression.type.1](defaults/main.yml#L347) | str | `text/css` |
| [haproxy_backend.0.compression.type.2](defaults/main.yml#L348) | str | `application/json` |
| [haproxy_backend.0.compression.type.3](defaults/main.yml#L349) | str | `application/x-javascript` |
| [haproxy_backend.0.compression.type.4](defaults/main.yml#L350) | str | `text/xml` |
| [haproxy_backend.0.compression.type.5](defaults/main.yml#L351) | str | `application/xml` |
| [haproxy_backend.0.compression.type.6](defaults/main.yml#L352) | str | `application/xml+rss` |
| [haproxy_backend.0.compression.type.7](defaults/main.yml#L353) | str | `text/javascript` |
| [haproxy_backend.0.compression.type.8](defaults/main.yml#L354) | str | `application/javascript` |
| [haproxy_backend.0.hash_type](defaults/main.yml#L340) | dict |  |
| [haproxy_backend.0.hash_type.function](defaults/main.yml#L342) | str | `djb2` |
| [haproxy_backend.0.hash_type.method](defaults/main.yml#L341) | str | `consistent` |
| [haproxy_backend.0.http_request](defaults/main.yml#L367) | list |  |
| [haproxy_backend.0.http_request.0](defaults/main.yml#L368) | dict |  |
| [haproxy_backend.0.http_request.0.action](defaults/main.yml#L368) | str | `set-header` |
| [haproxy_backend.0.http_request.0.condition](defaults/main.yml#L370) | str | `!{ ssl_fc } is_root` |
| [haproxy_backend.0.http_request.0.params](defaults/main.yml#L369) | str | `Test-Header test-value` |
| [haproxy_backend.0.http_response](defaults/main.yml#L371) | list |  |
| [haproxy_backend.0.http_response.0](defaults/main.yml#L372) | dict |  |
| [haproxy_backend.0.http_response.0.action](defaults/main.yml#L372) | str | `replace-value` |
| [haproxy_backend.0.http_response.0.condition](defaults/main.yml#L374) | str | `is_root` |
| [haproxy_backend.0.http_response.0.params](defaults/main.yml#L373) | str | `Cache-control ^public$ private` |
| [haproxy_backend.0.mode](defaults/main.yml#L338) | str | `http` |
| [haproxy_backend.0.name](defaults/main.yml#L337) | str | `app` |
| [haproxy_backend.0.option](defaults/main.yml#L355) | list |  |
| [haproxy_backend.0.option.0](defaults/main.yml#L356) | dict |  |
| [haproxy_backend.0.option.0.name](defaults/main.yml#L356) | str | `forwardfor` |
| [haproxy_backend.0.option.1](defaults/main.yml#L357) | dict |  |
| [haproxy_backend.0.option.1.name](defaults/main.yml#L357) | str | `httpchk` |
| [haproxy_backend.0.option.1.params](defaults/main.yml#L358) | str | `/` |
| [haproxy_backend.0.server](defaults/main.yml#L378) | list |  |
| [haproxy_backend.0.server.0](defaults/main.yml#L379) | dict |  |
| [haproxy_backend.0.server.0.address](defaults/main.yml#L380) | str | `10.10.10.10` |
| [haproxy_backend.0.server.0.name](defaults/main.yml#L379) | str | `server1` |
| [haproxy_backend.0.server.0.params](defaults/main.yml#L382) | str | `check` |
| [haproxy_backend.0.server.0.port](defaults/main.yml#L381) | int | `6400` |
| [haproxy_backend.0.server.1](defaults/main.yml#L383) | dict |  |
| [haproxy_backend.0.server.1.address](defaults/main.yml#L384) | str | `10.10.10.11` |
| [haproxy_backend.0.server.1.name](defaults/main.yml#L383) | str | `server2` |
| [haproxy_backend.0.server.1.params](defaults/main.yml#L386) | str | `check` |
| [haproxy_backend.0.server.1.port](defaults/main.yml#L385) | int | `6400` |
| [haproxy_backend.0.stick](defaults/main.yml#L391) | list |  |
| [haproxy_backend.0.stick.0](defaults/main.yml#L392) | dict |  |
| [haproxy_backend.0.stick.0.pattern](defaults/main.yml#L393) | str | `res.cook(JSESSIONID)` |
| [haproxy_backend.0.stick.0.table](defaults/main.yml#L394) | str | `app` |
| [haproxy_backend.0.stick.0.type](defaults/main.yml#L392) | str | `store-response` |
| [haproxy_backend.0.stick.1](defaults/main.yml#L395) | dict |  |
| [haproxy_backend.0.stick.1.pattern](defaults/main.yml#L396) | str | `req.cook(JSESSIONID)` |
| [haproxy_backend.0.stick.1.type](defaults/main.yml#L395) | str | `on` |
| [haproxy_backend.0.stick_table](defaults/main.yml#L387) | dict |  |
| [haproxy_backend.0.stick_table.len](defaults/main.yml#L389) | int | `32` |
| [haproxy_backend.0.stick_table.size](defaults/main.yml#L390) | str | `1M` |
| [haproxy_backend.0.stick_table.type](defaults/main.yml#L388) | str | `string` |
| [haproxy_backend.0.timeout](defaults/main.yml#L359) | list |  |
| [haproxy_backend.0.timeout.0](defaults/main.yml#L360) | dict |  |
| [haproxy_backend.0.timeout.0.name](defaults/main.yml#L360) | str | `tunnel` |
| [haproxy_backend.0.timeout.0.value](defaults/main.yml#L361) | str | `86400s` |
| [haproxy_backend.0.use_server](defaults/main.yml#L375) | list |  |
| [haproxy_backend.0.use_server.0](defaults/main.yml#L376) | dict |  |
| [haproxy_backend.0.use_server.0.condition](defaults/main.yml#L377) | str | `hdr(host) -i test.nnc.guru` |
| [haproxy_backend.0.use_server.0.name](defaults/main.yml#L376) | str | `server1` |
| [haproxy_backup_dir](defaults/main.yml#L32) | str | `/var/backups/haproxy` |
| [haproxy_backup_retention_days](defaults/main.yml#L33) | int | `30` |
| [haproxy_cert_dir](defaults/main.yml#L17) | str | `{{ haproxy_config_dir }}/certs` |
| [haproxy_cert_group](defaults/main.yml#L22) | str | `haproxy` |
| [haproxy_cert_name](defaults/main.yml#L18) | str |  |
| [haproxy_certificates](defaults/main.yml#L20) | list |  |
| [haproxy_config_dir](defaults/main.yml#L8) | str | `/etc/haproxy` |
| [haproxy_config_staging_path](defaults/main.yml#L25) | str | `{{ haproxy_destination_config_path }}.staged` |
| [haproxy_defaults](defaults/main.yml#L160) | dict |  |
| [haproxy_defaults.log](defaults/main.yml#L162) | list |  |
| [haproxy_defaults.log.0](defaults/main.yml#L163) | dict |  |
| [haproxy_defaults.log.0.global](defaults/main.yml#L163) | bool | `True` |
| [haproxy_defaults.maxconn](defaults/main.yml#L187) | int | `3000` |
| [haproxy_defaults.mode](defaults/main.yml#L161) | str | `http` |
| [haproxy_defaults.option](defaults/main.yml#L164) | list |  |
| [haproxy_defaults.option.0](defaults/main.yml#L165) | dict |  |
| [haproxy_defaults.option.0.name](defaults/main.yml#L165) | str | `httplog` |
| [haproxy_defaults.option.1](defaults/main.yml#L166) | dict |  |
| [haproxy_defaults.option.1.name](defaults/main.yml#L166) | str | `dontlognull` |
| [haproxy_defaults.option.2](defaults/main.yml#L167) | dict |  |
| [haproxy_defaults.option.2.name](defaults/main.yml#L167) | str | `http-server-close` |
| [haproxy_defaults.option.3](defaults/main.yml#L168) | dict |  |
| [haproxy_defaults.option.3.name](defaults/main.yml#L168) | str | `forwardfor` |
| [haproxy_defaults.option.3.params](defaults/main.yml#L169) | str | `except 127.0.0.0/8` |
| [haproxy_defaults.option.4](defaults/main.yml#L170) | dict |  |
| [haproxy_defaults.option.4.name](defaults/main.yml#L170) | str | `redispatch` |
| [haproxy_defaults.retries](defaults/main.yml#L171) | int | `3` |
| [haproxy_defaults.timeout](defaults/main.yml#L172) | list |  |
| [haproxy_defaults.timeout.0](defaults/main.yml#L173) | dict |  |
| [haproxy_defaults.timeout.0.name](defaults/main.yml#L173) | str | `http-request` |
| [haproxy_defaults.timeout.0.value](defaults/main.yml#L174) | str | `10s` |
| [haproxy_defaults.timeout.1](defaults/main.yml#L175) | dict |  |
| [haproxy_defaults.timeout.1.name](defaults/main.yml#L175) | str | `queue` |
| [haproxy_defaults.timeout.1.value](defaults/main.yml#L176) | str | `1m` |
| [haproxy_defaults.timeout.2](defaults/main.yml#L177) | dict |  |
| [haproxy_defaults.timeout.2.name](defaults/main.yml#L177) | str | `connect` |
| [haproxy_defaults.timeout.2.value](defaults/main.yml#L178) | str | `10s` |
| [haproxy_defaults.timeout.3](defaults/main.yml#L179) | dict |  |
| [haproxy_defaults.timeout.3.name](defaults/main.yml#L179) | str | `client` |
| [haproxy_defaults.timeout.3.value](defaults/main.yml#L180) | str | `1m` |
| [haproxy_defaults.timeout.4](defaults/main.yml#L181) | dict |  |
| [haproxy_defaults.timeout.4.name](defaults/main.yml#L181) | str | `server` |
| [haproxy_defaults.timeout.4.value](defaults/main.yml#L182) | str | `1m` |
| [haproxy_defaults.timeout.5](defaults/main.yml#L183) | dict |  |
| [haproxy_defaults.timeout.5.name](defaults/main.yml#L183) | str | `http-keep-alive` |
| [haproxy_defaults.timeout.5.value](defaults/main.yml#L184) | str | `10s` |
| [haproxy_defaults.timeout.6](defaults/main.yml#L185) | dict |  |
| [haproxy_defaults.timeout.6.name](defaults/main.yml#L185) | str | `check` |
| [haproxy_defaults.timeout.6.value](defaults/main.yml#L186) | str | `10s` |
| [haproxy_destination_config_path](defaults/main.yml#L9) | str | `{{ haproxy_config_dir }}/haproxy.cfg` |
| [haproxy_firewall_manage](defaults/main.yml#L38) | bool |  |
| [haproxy_firewall_ports](defaults/main.yml#L39) | list |  |
| [haproxy_frontend](defaults/main.yml#L229) | list |  |
| [haproxy_frontend.0](defaults/main.yml#L230) | dict |  |
| [haproxy_frontend.0.backlog](defaults/main.yml#L237) | int | `10000` |
| [haproxy_frontend.0.bind](defaults/main.yml#L232) | list |  |
| [haproxy_frontend.0.bind.0](defaults/main.yml#L233) | dict |  |
| [haproxy_frontend.0.bind.0.address](defaults/main.yml#L233) | str | `127.0.0.1` |
| [haproxy_frontend.0.bind.0.port](defaults/main.yml#L234) | int | `5001` |
| [haproxy_frontend.0.bind.1](defaults/main.yml#L235) | dict |  |
| [haproxy_frontend.0.bind.1.address](defaults/main.yml#L235) | str | `127.0.0.1` |
| [haproxy_frontend.0.bind.1.port](defaults/main.yml#L236) | int | `5002` |
| [haproxy_frontend.0.default_backend](defaults/main.yml#L241) | str | `app` |
| [haproxy_frontend.0.mode](defaults/main.yml#L231) | str | `http` |
| [haproxy_frontend.0.name](defaults/main.yml#L230) | str | `main-http` |
| [haproxy_frontend.0.use_backend](defaults/main.yml#L238) | list |  |
| [haproxy_frontend.0.use_backend.0](defaults/main.yml#L239) | dict |  |
| [haproxy_frontend.0.use_backend.0.condition](defaults/main.yml#L240) | str | `!{ ssl_fc }` |
| [haproxy_frontend.0.use_backend.0.name](defaults/main.yml#L239) | str | `app` |
| [haproxy_frontend.1](defaults/main.yml#L242) | dict |  |
| [haproxy_frontend.1.acl](defaults/main.yml#L268) | list |  |
| [haproxy_frontend.1.acl.0](defaults/main.yml#L269) | dict |  |
| [haproxy_frontend.1.acl.0.fetch](defaults/main.yml#L270) | str | `path -i  /` |
| [haproxy_frontend.1.acl.0.name](defaults/main.yml#L269) | str | `is_root` |
| [haproxy_frontend.1.bind](defaults/main.yml#L244) | list |  |
| [haproxy_frontend.1.bind.0](defaults/main.yml#L245) | dict |  |
| [haproxy_frontend.1.bind.0.address](defaults/main.yml#L245) | str | `127.0.0.1` |
| [haproxy_frontend.1.bind.0.port](defaults/main.yml#L246) | int | `5003` |
| [haproxy_frontend.1.capture](defaults/main.yml#L260) | list |  |
| [haproxy_frontend.1.capture.0](defaults/main.yml#L261) | dict |  |
| [haproxy_frontend.1.capture.0.len](defaults/main.yml#L263) | int | `32` |
| [haproxy_frontend.1.capture.0.name](defaults/main.yml#L262) | str | `JSESSIONID` |
| [haproxy_frontend.1.capture.0.type](defaults/main.yml#L261) | str | `cookie` |
| [haproxy_frontend.1.capture.1](defaults/main.yml#L264) | dict |  |
| [haproxy_frontend.1.capture.1.len](defaults/main.yml#L266) | int | `15` |
| [haproxy_frontend.1.capture.1.name](defaults/main.yml#L265) | str | `Host` |
| [haproxy_frontend.1.capture.1.type](defaults/main.yml#L264) | str | `request header` |
| [haproxy_frontend.1.http_request](defaults/main.yml#L271) | list |  |
| [haproxy_frontend.1.http_request.0](defaults/main.yml#L272) | dict |  |
| [haproxy_frontend.1.http_request.0.action](defaults/main.yml#L272) | str | `set-header` |
| [haproxy_frontend.1.http_request.0.condition](defaults/main.yml#L274) | str | `!{ ssl_fc }` |
| [haproxy_frontend.1.http_request.0.params](defaults/main.yml#L273) | str | `X-Forwarded-Proto http` |
| [haproxy_frontend.1.mode](defaults/main.yml#L243) | str | `http` |
| [haproxy_frontend.1.monitor_uri](defaults/main.yml#L267) | str | `/haproxy` |
| [haproxy_frontend.1.name](defaults/main.yml#L242) | str | `main-https` |
| [haproxy_frontend.1.option](defaults/main.yml#L247) | list |  |
| [haproxy_frontend.1.option.0](defaults/main.yml#L248) | dict |  |
| [haproxy_frontend.1.option.0.name](defaults/main.yml#L248) | str | `contstats` |
| [haproxy_frontend.1.option.1](defaults/main.yml#L249) | dict |  |
| [haproxy_frontend.1.option.1.name](defaults/main.yml#L249) | str | `http-server-close` |
| [haproxy_frontend.1.option.2](defaults/main.yml#L250) | dict |  |
| [haproxy_frontend.1.option.2.name](defaults/main.yml#L250) | str | `httplog` |
| [haproxy_frontend.1.redirect](defaults/main.yml#L275) | list |  |
| [haproxy_frontend.1.redirect.0](defaults/main.yml#L276) | dict |  |
| [haproxy_frontend.1.redirect.0.code](defaults/main.yml#L278) | int | `301` |
| [haproxy_frontend.1.redirect.0.condition](defaults/main.yml#L280) | str | `!{ ssl_fc }` |
| [haproxy_frontend.1.redirect.0.option](defaults/main.yml#L279) | str | `drop-query` |
| [haproxy_frontend.1.redirect.0.type](defaults/main.yml#L276) | str | `scheme` |
| [haproxy_frontend.1.redirect.0.value](defaults/main.yml#L277) | str | `https` |
| [haproxy_frontend.1.timeout](defaults/main.yml#L251) | list |  |
| [haproxy_frontend.1.timeout.0](defaults/main.yml#L252) | dict |  |
| [haproxy_frontend.1.timeout.0.name](defaults/main.yml#L252) | str | `client` |
| [haproxy_frontend.1.timeout.0.value](defaults/main.yml#L253) | str | `300s` |
| [haproxy_frontend.1.timeout.1](defaults/main.yml#L254) | dict |  |
| [haproxy_frontend.1.timeout.1.name](defaults/main.yml#L254) | str | `http-keep-alive` |
| [haproxy_frontend.1.timeout.1.value](defaults/main.yml#L255) | str | `1s` |
| [haproxy_frontend.1.timeout.2](defaults/main.yml#L256) | dict |  |
| [haproxy_frontend.1.timeout.2.name](defaults/main.yml#L256) | str | `http-request` |
| [haproxy_frontend.1.timeout.2.value](defaults/main.yml#L257) | str | `15s` |
| [haproxy_frontend.1.timeout.3](defaults/main.yml#L258) | dict |  |
| [haproxy_frontend.1.timeout.3.name](defaults/main.yml#L258) | str | `tarpit` |
| [haproxy_frontend.1.timeout.3.value](defaults/main.yml#L259) | str | `60s` |
| [haproxy_frontend.1.use_backend](defaults/main.yml#L281) | list |  |
| [haproxy_frontend.1.use_backend.0](defaults/main.yml#L282) | dict |  |
| [haproxy_frontend.1.use_backend.0.condition](defaults/main.yml#L283) | str | `!{ ssl_fc }` |
| [haproxy_frontend.1.use_backend.0.name](defaults/main.yml#L282) | str | `app` |
| [haproxy_global](defaults/main.yml#L112) | dict |  |
| [haproxy_global.chroot](defaults/main.yml#L124) | str | `/var/lib/haproxy` |
| [haproxy_global.cpu_map](defaults/main.yml#L144) | str |  |
| [haproxy_global.daemon](defaults/main.yml#L129) | bool | `True` |
| [haproxy_global.group](defaults/main.yml#L128) | str | `haproxy` |
| [haproxy_global.log](defaults/main.yml#L113) | list |  |
| [haproxy_global.log.0](defaults/main.yml#L115) | dict |  |
| [haproxy_global.log.0.address](defaults/main.yml#L115) | str | `127.0.0.1` |
| [haproxy_global.log.0.facility](defaults/main.yml#L116) | str | `local0` |
| [haproxy_global.maxconn](defaults/main.yml#L126) | int | `4000` |
| [haproxy_global.nbthread](defaults/main.yml#L142) | int |  |
| [haproxy_global.pidfile](defaults/main.yml#L125) | str | `/var/run/haproxy.pid` |
| [haproxy_global.quiet](defaults/main.yml#L154) | bool |  |
| [haproxy_global.spread_checks](defaults/main.yml#L152) | int |  |
| [haproxy_global.stats_socket](defaults/main.yml#L130) | list |  |
| [haproxy_global.stats_socket.0](defaults/main.yml#L131) | dict |  |
| [haproxy_global.stats_socket.0.path](defaults/main.yml#L131) | str | `/var/lib/haproxy/stats` |
| [haproxy_global.tune](defaults/main.yml#L146) | dict |  |
| [haproxy_global.tune.bufsize](defaults/main.yml#L149) | int | `16384` |
| [haproxy_global.tune.maxrewrite](defaults/main.yml#L150) | int | `1024` |
| [haproxy_global.tune.ssl_cachesize](defaults/main.yml#L147) | int | `20000` |
| [haproxy_global.tune.ssl_lifetime](defaults/main.yml#L148) | int | `300` |
| [haproxy_global.tune_ssl_default_dh_param](defaults/main.yml#L123) | int | `2048` |
| [haproxy_global.user](defaults/main.yml#L127) | str | `haproxy` |
| [haproxy_ip_nonlocal_bind](defaults/main.yml#L106) | bool |  |
| [haproxy_listen](defaults/main.yml#L402) | list |  |
| [haproxy_listen.0](defaults/main.yml#L403) | dict |  |
| [haproxy_listen.0.bind](defaults/main.yml#L406) | list |  |
| [haproxy_listen.0.bind.0](defaults/main.yml#L407) | dict |  |
| [haproxy_listen.0.bind.0.address](defaults/main.yml#L407) | str | `127.0.0.1` |
| [haproxy_listen.0.bind.0.port](defaults/main.yml#L408) | int | `8000` |
| [haproxy_listen.0.mode](defaults/main.yml#L404) | str | `http` |
| [haproxy_listen.0.monitor_uri](defaults/main.yml#L405) | str | `/haproxy` |
| [haproxy_listen.0.name](defaults/main.yml#L403) | str | `http_health_check` |
| [haproxy_listen.0.option](defaults/main.yml#L409) | list |  |
| [haproxy_listen.0.option.0](defaults/main.yml#L410) | dict |  |
| [haproxy_listen.0.option.0.name](defaults/main.yml#L410) | str | `dontlognull` |
| [haproxy_listen.0.option.1](defaults/main.yml#L411) | dict |  |
| [haproxy_listen.0.option.1.name](defaults/main.yml#L411) | str | `httpchk` |
| [haproxy_listen.1](defaults/main.yml#L412) | dict |  |
| [haproxy_listen.1.bind](defaults/main.yml#L414) | list |  |
| [haproxy_listen.1.bind.0](defaults/main.yml#L415) | dict |  |
| [haproxy_listen.1.bind.0.address](defaults/main.yml#L415) | str | `127.0.0.1` |
| [haproxy_listen.1.bind.0.port](defaults/main.yml#L416) | int | `9000` |
| [haproxy_listen.1.mode](defaults/main.yml#L413) | str | `http` |
| [haproxy_listen.1.name](defaults/main.yml#L412) | str | `stats` |
| [haproxy_listen.1.stats](defaults/main.yml#L417) | dict |  |
| [haproxy_listen.1.stats.auth](defaults/main.yml#L424) | list |  |
| [haproxy_listen.1.stats.auth.0](defaults/main.yml#L425) | dict |  |
| [haproxy_listen.1.stats.auth.0.login](defaults/main.yml#L425) | str | `admin-user` |
| [haproxy_listen.1.stats.auth.0.password](defaults/main.yml#L426) | str | `{{ haproxy_stats_password }}` |
| [haproxy_listen.1.stats.enable](defaults/main.yml#L418) | bool | `True` |
| [haproxy_listen.1.stats.hide_version](defaults/main.yml#L419) | bool | `True` |
| [haproxy_listen.1.stats.realm](defaults/main.yml#L423) | str | `HAProxy\ Statistics` |
| [haproxy_listen.1.stats.refresh](defaults/main.yml#L427) | str | `5s` |
| [haproxy_listen.1.stats.scope](defaults/main.yml#L420) | list |  |
| [haproxy_listen.1.stats.scope.0](defaults/main.yml#L421) | str | `.` |
| [haproxy_listen.1.stats.uri](defaults/main.yml#L422) | str | `/admin?stats` |
| [haproxy_log_dir](defaults/main.yml#L10) | str | `/var/log/haproxy` |
| [haproxy_log_file](defaults/main.yml#L11) | str | `{{ haproxy_log_dir }}/haproxy.log` |
| [haproxy_logging](defaults/main.yml#L503) | dict |  |
| [haproxy_logging.capture_request_headers](defaults/main.yml#L509) | list |  |
| [haproxy_logging.capture_response_headers](defaults/main.yml#L511) | list |  |
| [haproxy_logging.custom_log_format](defaults/main.yml#L513) | str |  |
| [haproxy_logging.destination](defaults/main.yml#L505) | str | `/dev/log` |
| [haproxy_logging.facility](defaults/main.yml#L506) | str | `local0` |
| [haproxy_logging.level](defaults/main.yml#L507) | str | `info` |
| [haproxy_logging.logrotate](defaults/main.yml#L521) | dict |  |
| [haproxy_logging.logrotate.frequency](defaults/main.yml#L522) | str | `daily` |
| [haproxy_logging.logrotate.retain](defaults/main.yml#L523) | int | `14` |
| [haproxy_logging.per_backend_log_level](defaults/main.yml#L515) | dict |  |
| [haproxy_logging.rsyslog](defaults/main.yml#L517) | dict |  |
| [haproxy_logging.rsyslog.udp_listen](defaults/main.yml#L519) | bool |  |
| [haproxy_logrotate_file](defaults/main.yml#L12) | str | `/etc/logrotate.d/haproxy` |
| [haproxy_network_routes](defaults/main.yml#L72) | list |  |
| [haproxy_peers](defaults/main.yml#L559) | dict |  |
| [haproxy_peers.enabled](defaults/main.yml#L560) | bool |  |
| [haproxy_peers.name](defaults/main.yml#L561) | str | `haproxy_cluster` |
| [haproxy_peers.peers](defaults/main.yml#L562) | list |  |
| [haproxy_policy_routing](defaults/main.yml#L83) | dict |  |
| [haproxy_policy_routing.enabled](defaults/main.yml#L84) | bool |  |
| [haproxy_policy_routing.tables](defaults/main.yml#L85) | list |  |
| [haproxy_private_ip](defaults/main.yml#L54) | str |  |
| [haproxy_public_ip](defaults/main.yml#L49) | str |  |
| [haproxy_rate_limits](defaults/main.yml#L466) | list |  |
| [haproxy_restore_config](defaults/main.yml#L34) | str |  |
| [haproxy_security](defaults/main.yml#L479) | dict |  |
| [haproxy_security.hide_server_header](defaults/main.yml#L497) | bool |  |
| [haproxy_security.ip_blacklist](defaults/main.yml#L486) | dict |  |
| [haproxy_security.ip_blacklist.apply_to](defaults/main.yml#L491) | list |  |
| [haproxy_security.ip_blacklist.enabled](defaults/main.yml#L487) | bool |  |
| [haproxy_security.ip_blacklist.ips](defaults/main.yml#L489) | list |  |
| [haproxy_security.ip_whitelist](defaults/main.yml#L480) | dict |  |
| [haproxy_security.ip_whitelist.apply_to](defaults/main.yml#L485) | list |  |
| [haproxy_security.ip_whitelist.enabled](defaults/main.yml#L481) | bool |  |
| [haproxy_security.ip_whitelist.ips](defaults/main.yml#L483) | list |  |
| [haproxy_security.request_body_size_limit](defaults/main.yml#L492) | dict |  |
| [haproxy_security.request_body_size_limit.enabled](defaults/main.yml#L493) | bool |  |
| [haproxy_security.request_body_size_limit.max_bytes](defaults/main.yml#L495) | int | `10485760` |
| [haproxy_selinux_manage](defaults/main.yml#L37) | bool | `True` |
| [haproxy_ssl](defaults/main.yml#L433) | dict |  |
| [haproxy_ssl.cert_dir](defaults/main.yml#L435) | str | `{{ haproxy_config_dir }}/certs` |
| [haproxy_ssl.default_bind_ciphers](defaults/main.yml#L437) | str |  |
| [haproxy_ssl.default_bind_options](defaults/main.yml#L439) | str |  |
| [haproxy_ssl.ocsp_stapling](defaults/main.yml#L443) | bool |  |
| [haproxy_ssl.session_cache_size](defaults/main.yml#L441) | int | `20000` |
| [haproxy_stats](defaults/main.yml#L529) | dict |  |
| [haproxy_stats.auth](defaults/main.yml#L536) | dict |  |
| [haproxy_stats.auth.enabled](defaults/main.yml#L537) | bool |  |
| [haproxy_stats.auth.password](defaults/main.yml#L539) | str |  |
| [haproxy_stats.auth.username](defaults/main.yml#L538) | str | `admin` |
| [haproxy_stats.bind_ip](defaults/main.yml#L532) | str | `127.0.0.1` |
| [haproxy_stats.enabled](defaults/main.yml#L531) | bool |  |
| [haproxy_stats.port](defaults/main.yml#L533) | int | `8404` |
| [haproxy_stats.prometheus](defaults/main.yml#L540) | dict |  |
| [haproxy_stats.prometheus.enabled](defaults/main.yml#L542) | bool |  |
| [haproxy_stats.prometheus.uri](defaults/main.yml#L543) | str | `/metrics` |
| [haproxy_stats.refresh](defaults/main.yml#L535) | str | `10s` |
| [haproxy_stats.runtime_api](defaults/main.yml#L544) | dict |  |
| [haproxy_stats.runtime_api.enabled](defaults/main.yml#L546) | bool |  |
| [haproxy_stats.runtime_api.level](defaults/main.yml#L550) | str | `admin` |
| [haproxy_stats.runtime_api.socket](defaults/main.yml#L547) | str | `/var/run/haproxy/admin.sock` |
| [haproxy_stats.runtime_api.socket_dir_mode](defaults/main.yml#L549) | str | `0750` |
| [haproxy_stats.runtime_api.socket_mode](defaults/main.yml#L548) | str | `660` |
| [haproxy_stats.uri](defaults/main.yml#L534) | str | `/stats` |
| [haproxy_stats_password](defaults/main.yml#L42) | str |  |
| [haproxy_stick_tables](defaults/main.yml#L451) | list |  |
| [haproxy_use_official_repo](defaults/main.yml#L28) | bool |  |
| [haproxy_version](defaults/main.yml#L29) | str |  |
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




### File: `tasks/selinux.yml`

| Task Name | Module | Has Conditions | Line |
|-----------|--------|----------------|------|
| [Allow HAProxy to connect to any backend port under SELinux](tasks/selinux.yml#L) | ansible.posix.seboolean | Yes | N/A |




### File: `tasks/restore.yml`

| Task Name | Module | Has Conditions | Line |
|-----------|--------|----------------|------|
| [Validate the requested restore archive](tasks/restore.yml#L) | ansible.builtin.assert | No | N/A |
| [Stage the archived configuration](tasks/restore.yml#L) | ansible.builtin.copy | No | N/A |
| [Validate the restored configuration](tasks/restore.yml#L) | ansible.builtin.command | No | N/A |
| [Install the restored configuration](tasks/restore.yml#L) | ansible.builtin.copy | No | N/A |




### File: `tasks/firewall.yml`

| Task Name | Module | Has Conditions | Line |
|-----------|--------|----------------|------|
| [Open the declared HAProxy ports in firewalld](tasks/firewall.yml#L) | ansible.posix.firewalld | Yes | N/A |




### File: `tasks/certs.yml`

| Task Name | Module | Has Conditions | Line |
|-----------|--------|----------------|------|
| [Deploy the legacy single certificate](tasks/certs.yml#L) | ansible.builtin.copy | Yes | N/A |
| [Deploy the declared certificate pairs](tasks/certs.yml#L) | ansible.builtin.copy | No | N/A |
| [Prepare a working directory for PEM bundling](tasks/certs.yml#L) | ansible.builtin.file | No | N/A |
| [Stage the certificate fragment for PEM bundling](tasks/certs.yml#L) | ansible.builtin.copy | No | N/A |
| [Stage the private key fragment for PEM bundling](tasks/certs.yml#L) | ansible.builtin.copy | No | N/A |
| [Stage the chain fragment for PEM bundling](tasks/certs.yml#L) | ansible.builtin.copy | No | N/A |
| [Assemble the PEM bundle expected by HAProxy](tasks/certs.yml#L) | ansible.builtin.assemble | No | N/A |




### File: `tasks/install-Debian.yml`

| Task Name | Module | Has Conditions | Line |
|-----------|--------|----------------|------|
| [Include the official HAProxy repository when requested](tasks/install-Debian.yml#L) | ansible.builtin.include_tasks | No | N/A |
| [Install HAProxy from the configured APT source](tasks/install-Debian.yml#L) | ansible.builtin.apt | No | N/A |




### File: `tasks/backup.yml`

| Task Name | Module | Has Conditions | Line |
|-----------|--------|----------------|------|
| [Read the live configuration checksum](tasks/backup.yml#L) | ansible.builtin.stat | No | N/A |
| [Read the candidate configuration checksum](tasks/backup.yml#L) | ansible.builtin.stat | No | N/A |
| [Create the configuration backup directory](tasks/backup.yml#L) | ansible.builtin.file | Yes | N/A |
| [Back up the configuration that is about to be replaced](tasks/backup.yml#L) | ansible.builtin.copy | Yes | N/A |
| [Prune expired configuration backups](tasks/backup.yml#L) | ansible.builtin.find | No | N/A |
| [Remove expired configuration backups](tasks/backup.yml#L) | ansible.builtin.file | No | N/A |




### File: `tasks/repo-Debian.yml`

| Task Name | Module | Has Conditions | Line |
|-----------|--------|----------------|------|
| [Add the official HAProxy repository signing key](tasks/repo-Debian.yml#L) | ansible.builtin.get_url | Yes | N/A |
| [Add the official HAProxy repository](tasks/repo-Debian.yml#L) | ansible.builtin.apt_repository | Yes | N/A |




### File: `tasks/main.yml`

| Task Name | Module | Has Conditions | Line |
|-----------|--------|----------------|------|
| [Check Packages](tasks/main.yml#L) | ansible.builtin.package_facts | No | N/A |
| [Run Pre-flight Checks](tasks/main.yml#L) | ansible.builtin.include_tasks | No | N/A |
| [Install HAProxy Package from Repository](tasks/main.yml#L) | ansible.builtin.include_tasks | Yes | N/A |
| [Create Certificate Folder](tasks/main.yml#L) | ansible.builtin.file | Yes | N/A |
| [Deploy Certificates](tasks/main.yml#L) | ansible.builtin.include_tasks | No | N/A |
| [Create Whitelist Folder](tasks/main.yml#L) | ansible.builtin.file | Yes | N/A |
| [Copy Whitelist File to Host](tasks/main.yml#L) | ansible.builtin.copy | Yes | N/A |
| [Include Network Routing Tasks](tasks/main.yml#L) | ansible.builtin.include_tasks | No | N/A |
| [Create runtime API socket directory](tasks/main.yml#L) | ansible.builtin.file | Yes | N/A |
| [Include Logging Tasks](tasks/main.yml#L) | ansible.builtin.include_tasks | No | N/A |
| [Restore an archived configuration when requested](tasks/main.yml#L) | ansible.builtin.include_tasks | Yes | N/A |
| [Render HAProxy configuration to the staging path](tasks/main.yml#L) | ansible.builtin.template | No | N/A |
| [Validate the staged HAProxy configuration](tasks/main.yml#L) | ansible.builtin.command | No | N/A |
| [Back up the configuration that is about to be replaced](tasks/main.yml#L) | ansible.builtin.include_tasks | No | N/A |
| [Install the validated HAProxy configuration](tasks/main.yml#L) | ansible.builtin.copy | No | N/A |
| [Run pre-flight validation checks](tasks/main.yml#L) | ansible.builtin.include_tasks | No | N/A |
| [Apply SELinux settings](tasks/main.yml#L) | ansible.builtin.include_tasks | Yes | N/A |
| [Manage firewall rules](tasks/main.yml#L) | ansible.builtin.include_tasks | Yes | N/A |
| [Ensure HAProxy Service is Started and Enabled](tasks/main.yml#L) | ansible.builtin.systemd | No | N/A |




### File: `tasks/install-RedHat.yml`

| Task Name | Module | Has Conditions | Line |
|-----------|--------|----------------|------|
| [Install HAProxy from the configured DNF source](tasks/install-RedHat.yml#L) | ansible.builtin.dnf | No | N/A |






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
