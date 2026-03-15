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
| [haproxy_backend](defaults/main.yml#L259) | list |  |
| [haproxy_backend.0](defaults/main.yml#L260) | dict |  |
| [haproxy_backend.0.acl](defaults/main.yml#L285) | list |  |
| [haproxy_backend.0.acl.0](defaults/main.yml#L286) | dict |  |
| [haproxy_backend.0.acl.0.fetch](defaults/main.yml#L287) | str | `path -i /` |
| [haproxy_backend.0.acl.0.name](defaults/main.yml#L286) | str | `is_root` |
| [haproxy_backend.0.acl.1](defaults/main.yml#L288) | dict |  |
| [haproxy_backend.0.acl.1.fetch](defaults/main.yml#L289) | str | `res.hdr(Set-cookie) -m sub Path=` |
| [haproxy_backend.0.acl.1.name](defaults/main.yml#L288) | str | `hdr_set_cookie_path` |
| [haproxy_backend.0.balance](defaults/main.yml#L262) | str | `source` |
| [haproxy_backend.0.compression](defaults/main.yml#L266) | dict |  |
| [haproxy_backend.0.compression.algo](defaults/main.yml#L267) | str | `gzip` |
| [haproxy_backend.0.compression.type](defaults/main.yml#L268) | list |  |
| [haproxy_backend.0.compression.type.0](defaults/main.yml#L269) | str | `text/plain` |
| [haproxy_backend.0.compression.type.1](defaults/main.yml#L270) | str | `text/css` |
| [haproxy_backend.0.compression.type.2](defaults/main.yml#L271) | str | `application/json` |
| [haproxy_backend.0.compression.type.3](defaults/main.yml#L272) | str | `application/x-javascript` |
| [haproxy_backend.0.compression.type.4](defaults/main.yml#L273) | str | `text/xml` |
| [haproxy_backend.0.compression.type.5](defaults/main.yml#L274) | str | `application/xml` |
| [haproxy_backend.0.compression.type.6](defaults/main.yml#L275) | str | `application/xml+rss` |
| [haproxy_backend.0.compression.type.7](defaults/main.yml#L276) | str | `text/javascript` |
| [haproxy_backend.0.compression.type.8](defaults/main.yml#L277) | str | `application/javascript` |
| [haproxy_backend.0.hash_type](defaults/main.yml#L263) | dict |  |
| [haproxy_backend.0.hash_type.function](defaults/main.yml#L265) | str | `djb2` |
| [haproxy_backend.0.hash_type.method](defaults/main.yml#L264) | str | `consistent` |
| [haproxy_backend.0.http_request](defaults/main.yml#L290) | list |  |
| [haproxy_backend.0.http_request.0](defaults/main.yml#L291) | dict |  |
| [haproxy_backend.0.http_request.0.action](defaults/main.yml#L291) | str | `set-header` |
| [haproxy_backend.0.http_request.0.condition](defaults/main.yml#L293) | str | `!{ ssl_fc } is_root` |
| [haproxy_backend.0.http_request.0.params](defaults/main.yml#L292) | str | `Test-Header test-value` |
| [haproxy_backend.0.http_response](defaults/main.yml#L294) | list |  |
| [haproxy_backend.0.http_response.0](defaults/main.yml#L295) | dict |  |
| [haproxy_backend.0.http_response.0.action](defaults/main.yml#L295) | str | `replace-value` |
| [haproxy_backend.0.http_response.0.condition](defaults/main.yml#L297) | str | `is_root` |
| [haproxy_backend.0.http_response.0.params](defaults/main.yml#L296) | str | `Cache-control ^public$ private` |
| [haproxy_backend.0.mode](defaults/main.yml#L261) | str | `http` |
| [haproxy_backend.0.name](defaults/main.yml#L260) | str | `app` |
| [haproxy_backend.0.option](defaults/main.yml#L278) | list |  |
| [haproxy_backend.0.option.0](defaults/main.yml#L279) | dict |  |
| [haproxy_backend.0.option.0.name](defaults/main.yml#L279) | str | `forwardfor` |
| [haproxy_backend.0.option.1](defaults/main.yml#L280) | dict |  |
| [haproxy_backend.0.option.1.name](defaults/main.yml#L280) | str | `httpchk` |
| [haproxy_backend.0.option.1.params](defaults/main.yml#L281) | str | `/` |
| [haproxy_backend.0.server](defaults/main.yml#L301) | list |  |
| [haproxy_backend.0.server.0](defaults/main.yml#L302) | dict |  |
| [haproxy_backend.0.server.0.address](defaults/main.yml#L303) | str | `10.10.10.10` |
| [haproxy_backend.0.server.0.name](defaults/main.yml#L302) | str | `server1` |
| [haproxy_backend.0.server.0.params](defaults/main.yml#L305) | str | `check` |
| [haproxy_backend.0.server.0.port](defaults/main.yml#L304) | int | `6400` |
| [haproxy_backend.0.server.1](defaults/main.yml#L306) | dict |  |
| [haproxy_backend.0.server.1.address](defaults/main.yml#L307) | str | `10.10.10.11` |
| [haproxy_backend.0.server.1.name](defaults/main.yml#L306) | str | `server2` |
| [haproxy_backend.0.server.1.params](defaults/main.yml#L309) | str | `check` |
| [haproxy_backend.0.server.1.port](defaults/main.yml#L308) | int | `6400` |
| [haproxy_backend.0.stick](defaults/main.yml#L314) | list |  |
| [haproxy_backend.0.stick.0](defaults/main.yml#L315) | dict |  |
| [haproxy_backend.0.stick.0.pattern](defaults/main.yml#L316) | str | `res.cook(JSESSIONID)` |
| [haproxy_backend.0.stick.0.table](defaults/main.yml#L317) | str | `app` |
| [haproxy_backend.0.stick.0.type](defaults/main.yml#L315) | str | `store-response` |
| [haproxy_backend.0.stick.1](defaults/main.yml#L318) | dict |  |
| [haproxy_backend.0.stick.1.pattern](defaults/main.yml#L319) | str | `req.cook(JSESSIONID)` |
| [haproxy_backend.0.stick.1.type](defaults/main.yml#L318) | str | `on` |
| [haproxy_backend.0.stick_table](defaults/main.yml#L310) | dict |  |
| [haproxy_backend.0.stick_table.len](defaults/main.yml#L312) | int | `32` |
| [haproxy_backend.0.stick_table.size](defaults/main.yml#L313) | str | `1M` |
| [haproxy_backend.0.stick_table.type](defaults/main.yml#L311) | str | `string` |
| [haproxy_backend.0.timeout](defaults/main.yml#L282) | list |  |
| [haproxy_backend.0.timeout.0](defaults/main.yml#L283) | dict |  |
| [haproxy_backend.0.timeout.0.name](defaults/main.yml#L283) | str | `tunnel` |
| [haproxy_backend.0.timeout.0.value](defaults/main.yml#L284) | str | `86400s` |
| [haproxy_backend.0.use_server](defaults/main.yml#L298) | list |  |
| [haproxy_backend.0.use_server.0](defaults/main.yml#L299) | dict |  |
| [haproxy_backend.0.use_server.0.condition](defaults/main.yml#L300) | str | `hdr(host) -i test.nnc.guru` |
| [haproxy_backend.0.use_server.0.name](defaults/main.yml#L299) | str | `server1` |
| [haproxy_cert_dir](defaults/main.yml#L16) | str | `{{ haproxy_config_dir }}/certs` |
| [haproxy_cert_name](defaults/main.yml#L17) | str |  |
| [haproxy_config_dir](defaults/main.yml#L8) | str | `/etc/haproxy` |
| [haproxy_defaults](defaults/main.yml#L83) | dict |  |
| [haproxy_defaults.log](defaults/main.yml#L85) | list |  |
| [haproxy_defaults.log.0](defaults/main.yml#L86) | dict |  |
| [haproxy_defaults.log.0.global](defaults/main.yml#L86) | bool | `True` |
| [haproxy_defaults.maxconn](defaults/main.yml#L110) | int | `3000` |
| [haproxy_defaults.mode](defaults/main.yml#L84) | str | `http` |
| [haproxy_defaults.option](defaults/main.yml#L87) | list |  |
| [haproxy_defaults.option.0](defaults/main.yml#L88) | dict |  |
| [haproxy_defaults.option.0.name](defaults/main.yml#L88) | str | `httplog` |
| [haproxy_defaults.option.1](defaults/main.yml#L89) | dict |  |
| [haproxy_defaults.option.1.name](defaults/main.yml#L89) | str | `dontlognull` |
| [haproxy_defaults.option.2](defaults/main.yml#L90) | dict |  |
| [haproxy_defaults.option.2.name](defaults/main.yml#L90) | str | `http-server-close` |
| [haproxy_defaults.option.3](defaults/main.yml#L91) | dict |  |
| [haproxy_defaults.option.3.name](defaults/main.yml#L91) | str | `forwardfor` |
| [haproxy_defaults.option.3.params](defaults/main.yml#L92) | str | `except 127.0.0.0/8` |
| [haproxy_defaults.option.4](defaults/main.yml#L93) | dict |  |
| [haproxy_defaults.option.4.name](defaults/main.yml#L93) | str | `redispatch` |
| [haproxy_defaults.retries](defaults/main.yml#L94) | int | `3` |
| [haproxy_defaults.timeout](defaults/main.yml#L95) | list |  |
| [haproxy_defaults.timeout.0](defaults/main.yml#L96) | dict |  |
| [haproxy_defaults.timeout.0.name](defaults/main.yml#L96) | str | `http-request` |
| [haproxy_defaults.timeout.0.value](defaults/main.yml#L97) | str | `10s` |
| [haproxy_defaults.timeout.1](defaults/main.yml#L98) | dict |  |
| [haproxy_defaults.timeout.1.name](defaults/main.yml#L98) | str | `queue` |
| [haproxy_defaults.timeout.1.value](defaults/main.yml#L99) | str | `1m` |
| [haproxy_defaults.timeout.2](defaults/main.yml#L100) | dict |  |
| [haproxy_defaults.timeout.2.name](defaults/main.yml#L100) | str | `connect` |
| [haproxy_defaults.timeout.2.value](defaults/main.yml#L101) | str | `10s` |
| [haproxy_defaults.timeout.3](defaults/main.yml#L102) | dict |  |
| [haproxy_defaults.timeout.3.name](defaults/main.yml#L102) | str | `client` |
| [haproxy_defaults.timeout.3.value](defaults/main.yml#L103) | str | `1m` |
| [haproxy_defaults.timeout.4](defaults/main.yml#L104) | dict |  |
| [haproxy_defaults.timeout.4.name](defaults/main.yml#L104) | str | `server` |
| [haproxy_defaults.timeout.4.value](defaults/main.yml#L105) | str | `1m` |
| [haproxy_defaults.timeout.5](defaults/main.yml#L106) | dict |  |
| [haproxy_defaults.timeout.5.name](defaults/main.yml#L106) | str | `http-keep-alive` |
| [haproxy_defaults.timeout.5.value](defaults/main.yml#L107) | str | `10s` |
| [haproxy_defaults.timeout.6](defaults/main.yml#L108) | dict |  |
| [haproxy_defaults.timeout.6.name](defaults/main.yml#L108) | str | `check` |
| [haproxy_defaults.timeout.6.value](defaults/main.yml#L109) | str | `10s` |
| [haproxy_destination_config_path](defaults/main.yml#L9) | str | `{{ haproxy_config_dir }}/haproxy.cfg` |
| [haproxy_frontend](defaults/main.yml#L152) | list |  |
| [haproxy_frontend.0](defaults/main.yml#L153) | dict |  |
| [haproxy_frontend.0.backlog](defaults/main.yml#L160) | int | `10000` |
| [haproxy_frontend.0.bind](defaults/main.yml#L155) | list |  |
| [haproxy_frontend.0.bind.0](defaults/main.yml#L156) | dict |  |
| [haproxy_frontend.0.bind.0.address](defaults/main.yml#L156) | str | `127.0.0.1` |
| [haproxy_frontend.0.bind.0.port](defaults/main.yml#L157) | int | `5001` |
| [haproxy_frontend.0.bind.1](defaults/main.yml#L158) | dict |  |
| [haproxy_frontend.0.bind.1.address](defaults/main.yml#L158) | str | `127.0.0.1` |
| [haproxy_frontend.0.bind.1.port](defaults/main.yml#L159) | int | `5002` |
| [haproxy_frontend.0.default_backend](defaults/main.yml#L164) | str | `app` |
| [haproxy_frontend.0.mode](defaults/main.yml#L154) | str | `http` |
| [haproxy_frontend.0.name](defaults/main.yml#L153) | str | `main-http` |
| [haproxy_frontend.0.use_backend](defaults/main.yml#L161) | list |  |
| [haproxy_frontend.0.use_backend.0](defaults/main.yml#L162) | dict |  |
| [haproxy_frontend.0.use_backend.0.condition](defaults/main.yml#L163) | str | `!{ ssl_fc }` |
| [haproxy_frontend.0.use_backend.0.name](defaults/main.yml#L162) | str | `app` |
| [haproxy_frontend.1](defaults/main.yml#L165) | dict |  |
| [haproxy_frontend.1.acl](defaults/main.yml#L191) | list |  |
| [haproxy_frontend.1.acl.0](defaults/main.yml#L192) | dict |  |
| [haproxy_frontend.1.acl.0.fetch](defaults/main.yml#L193) | str | `path -i  /` |
| [haproxy_frontend.1.acl.0.name](defaults/main.yml#L192) | str | `is_root` |
| [haproxy_frontend.1.bind](defaults/main.yml#L167) | list |  |
| [haproxy_frontend.1.bind.0](defaults/main.yml#L168) | dict |  |
| [haproxy_frontend.1.bind.0.address](defaults/main.yml#L168) | str | `127.0.0.1` |
| [haproxy_frontend.1.bind.0.port](defaults/main.yml#L169) | int | `5003` |
| [haproxy_frontend.1.capture](defaults/main.yml#L183) | list |  |
| [haproxy_frontend.1.capture.0](defaults/main.yml#L184) | dict |  |
| [haproxy_frontend.1.capture.0.len](defaults/main.yml#L186) | int | `32` |
| [haproxy_frontend.1.capture.0.name](defaults/main.yml#L185) | str | `JSESSIONID` |
| [haproxy_frontend.1.capture.0.type](defaults/main.yml#L184) | str | `cookie` |
| [haproxy_frontend.1.capture.1](defaults/main.yml#L187) | dict |  |
| [haproxy_frontend.1.capture.1.len](defaults/main.yml#L189) | int | `15` |
| [haproxy_frontend.1.capture.1.name](defaults/main.yml#L188) | str | `Host` |
| [haproxy_frontend.1.capture.1.type](defaults/main.yml#L187) | str | `request header` |
| [haproxy_frontend.1.http_request](defaults/main.yml#L194) | list |  |
| [haproxy_frontend.1.http_request.0](defaults/main.yml#L195) | dict |  |
| [haproxy_frontend.1.http_request.0.action](defaults/main.yml#L195) | str | `set-header` |
| [haproxy_frontend.1.http_request.0.condition](defaults/main.yml#L197) | str | `!{ ssl_fc }` |
| [haproxy_frontend.1.http_request.0.params](defaults/main.yml#L196) | str | `X-Forwarded-Proto http` |
| [haproxy_frontend.1.mode](defaults/main.yml#L166) | str | `http` |
| [haproxy_frontend.1.monitor_uri](defaults/main.yml#L190) | str | `/haproxy` |
| [haproxy_frontend.1.name](defaults/main.yml#L165) | str | `main-https` |
| [haproxy_frontend.1.option](defaults/main.yml#L170) | list |  |
| [haproxy_frontend.1.option.0](defaults/main.yml#L171) | dict |  |
| [haproxy_frontend.1.option.0.name](defaults/main.yml#L171) | str | `contstats` |
| [haproxy_frontend.1.option.1](defaults/main.yml#L172) | dict |  |
| [haproxy_frontend.1.option.1.name](defaults/main.yml#L172) | str | `http-server-close` |
| [haproxy_frontend.1.option.2](defaults/main.yml#L173) | dict |  |
| [haproxy_frontend.1.option.2.name](defaults/main.yml#L173) | str | `httplog` |
| [haproxy_frontend.1.redirect](defaults/main.yml#L198) | list |  |
| [haproxy_frontend.1.redirect.0](defaults/main.yml#L199) | dict |  |
| [haproxy_frontend.1.redirect.0.code](defaults/main.yml#L201) | int | `301` |
| [haproxy_frontend.1.redirect.0.condition](defaults/main.yml#L203) | str | `!{ ssl_fc }` |
| [haproxy_frontend.1.redirect.0.option](defaults/main.yml#L202) | str | `drop-query` |
| [haproxy_frontend.1.redirect.0.type](defaults/main.yml#L199) | str | `scheme` |
| [haproxy_frontend.1.redirect.0.value](defaults/main.yml#L200) | str | `https` |
| [haproxy_frontend.1.timeout](defaults/main.yml#L174) | list |  |
| [haproxy_frontend.1.timeout.0](defaults/main.yml#L175) | dict |  |
| [haproxy_frontend.1.timeout.0.name](defaults/main.yml#L175) | str | `client` |
| [haproxy_frontend.1.timeout.0.value](defaults/main.yml#L176) | str | `300s` |
| [haproxy_frontend.1.timeout.1](defaults/main.yml#L177) | dict |  |
| [haproxy_frontend.1.timeout.1.name](defaults/main.yml#L177) | str | `http-keep-alive` |
| [haproxy_frontend.1.timeout.1.value](defaults/main.yml#L178) | str | `1s` |
| [haproxy_frontend.1.timeout.2](defaults/main.yml#L179) | dict |  |
| [haproxy_frontend.1.timeout.2.name](defaults/main.yml#L179) | str | `http-request` |
| [haproxy_frontend.1.timeout.2.value](defaults/main.yml#L180) | str | `15s` |
| [haproxy_frontend.1.timeout.3](defaults/main.yml#L181) | dict |  |
| [haproxy_frontend.1.timeout.3.name](defaults/main.yml#L181) | str | `tarpit` |
| [haproxy_frontend.1.timeout.3.value](defaults/main.yml#L182) | str | `60s` |
| [haproxy_frontend.1.use_backend](defaults/main.yml#L204) | list |  |
| [haproxy_frontend.1.use_backend.0](defaults/main.yml#L205) | dict |  |
| [haproxy_frontend.1.use_backend.0.condition](defaults/main.yml#L206) | str | `!{ ssl_fc }` |
| [haproxy_frontend.1.use_backend.0.name](defaults/main.yml#L205) | str | `app` |
| [haproxy_global](defaults/main.yml#L35) | dict |  |
| [haproxy_global.chroot](defaults/main.yml#L47) | str | `/var/lib/haproxy` |
| [haproxy_global.cpu_map](defaults/main.yml#L67) | str |  |
| [haproxy_global.daemon](defaults/main.yml#L52) | bool | `True` |
| [haproxy_global.group](defaults/main.yml#L51) | str | `haproxy` |
| [haproxy_global.log](defaults/main.yml#L36) | list |  |
| [haproxy_global.log.0](defaults/main.yml#L38) | dict |  |
| [haproxy_global.log.0.address](defaults/main.yml#L38) | str | `127.0.0.1` |
| [haproxy_global.log.0.facility](defaults/main.yml#L39) | str | `local0` |
| [haproxy_global.maxconn](defaults/main.yml#L49) | int | `4000` |
| [haproxy_global.nbthread](defaults/main.yml#L65) | int |  |
| [haproxy_global.pidfile](defaults/main.yml#L48) | str | `/var/run/haproxy.pid` |
| [haproxy_global.quiet](defaults/main.yml#L77) | bool |  |
| [haproxy_global.spread_checks](defaults/main.yml#L75) | int |  |
| [haproxy_global.stats_socket](defaults/main.yml#L53) | list |  |
| [haproxy_global.stats_socket.0](defaults/main.yml#L54) | dict |  |
| [haproxy_global.stats_socket.0.path](defaults/main.yml#L54) | str | `/var/lib/haproxy/stats` |
| [haproxy_global.tune](defaults/main.yml#L69) | dict |  |
| [haproxy_global.tune.bufsize](defaults/main.yml#L72) | int | `16384` |
| [haproxy_global.tune.maxrewrite](defaults/main.yml#L73) | int | `1024` |
| [haproxy_global.tune.ssl_cachesize](defaults/main.yml#L70) | int | `20000` |
| [haproxy_global.tune.ssl_lifetime](defaults/main.yml#L71) | int | `300` |
| [haproxy_global.tune_ssl_default_dh_param](defaults/main.yml#L46) | int | `2048` |
| [haproxy_global.user](defaults/main.yml#L50) | str | `haproxy` |
| [haproxy_letsencrypt](defaults/main.yml#L368) | dict |  |
| [haproxy_letsencrypt.cert_dir](defaults/main.yml#L374) | str | `/etc/letsencrypt/live` |
| [haproxy_letsencrypt.deploy_hook](defaults/main.yml#L376) | bool | `True` |
| [haproxy_letsencrypt.domains](defaults/main.yml#L372) | list |  |
| [haproxy_letsencrypt.enabled](defaults/main.yml#L370) | bool |  |
| [haproxy_listen](defaults/main.yml#L325) | list |  |
| [haproxy_listen.0](defaults/main.yml#L326) | dict |  |
| [haproxy_listen.0.bind](defaults/main.yml#L329) | list |  |
| [haproxy_listen.0.bind.0](defaults/main.yml#L330) | dict |  |
| [haproxy_listen.0.bind.0.address](defaults/main.yml#L330) | str | `127.0.0.1` |
| [haproxy_listen.0.bind.0.port](defaults/main.yml#L331) | int | `8000` |
| [haproxy_listen.0.mode](defaults/main.yml#L327) | str | `http` |
| [haproxy_listen.0.monitor_uri](defaults/main.yml#L328) | str | `/haproxy` |
| [haproxy_listen.0.name](defaults/main.yml#L326) | str | `http_health_check` |
| [haproxy_listen.0.option](defaults/main.yml#L332) | list |  |
| [haproxy_listen.0.option.0](defaults/main.yml#L333) | dict |  |
| [haproxy_listen.0.option.0.name](defaults/main.yml#L333) | str | `dontlognull` |
| [haproxy_listen.0.option.1](defaults/main.yml#L334) | dict |  |
| [haproxy_listen.0.option.1.name](defaults/main.yml#L334) | str | `httpchk` |
| [haproxy_listen.1](defaults/main.yml#L335) | dict |  |
| [haproxy_listen.1.bind](defaults/main.yml#L337) | list |  |
| [haproxy_listen.1.bind.0](defaults/main.yml#L338) | dict |  |
| [haproxy_listen.1.bind.0.address](defaults/main.yml#L338) | str | `127.0.0.1` |
| [haproxy_listen.1.bind.0.port](defaults/main.yml#L339) | int | `9000` |
| [haproxy_listen.1.mode](defaults/main.yml#L336) | str | `http` |
| [haproxy_listen.1.name](defaults/main.yml#L335) | str | `stats` |
| [haproxy_listen.1.stats](defaults/main.yml#L340) | dict |  |
| [haproxy_listen.1.stats.auth](defaults/main.yml#L347) | list |  |
| [haproxy_listen.1.stats.auth.0](defaults/main.yml#L348) | dict |  |
| [haproxy_listen.1.stats.auth.0.login](defaults/main.yml#L348) | str | `admin-user` |
| [haproxy_listen.1.stats.auth.0.password](defaults/main.yml#L349) | str | `password123` |
| [haproxy_listen.1.stats.enable](defaults/main.yml#L341) | bool | `True` |
| [haproxy_listen.1.stats.hide_version](defaults/main.yml#L342) | bool | `True` |
| [haproxy_listen.1.stats.realm](defaults/main.yml#L346) | str | `HAProxy\ Statistics` |
| [haproxy_listen.1.stats.refresh](defaults/main.yml#L350) | str | `5s` |
| [haproxy_listen.1.stats.scope](defaults/main.yml#L343) | list |  |
| [haproxy_listen.1.stats.scope.0](defaults/main.yml#L344) | str | `.` |
| [haproxy_listen.1.stats.uri](defaults/main.yml#L345) | str | `/admin?stats` |
| [haproxy_log_file](defaults/main.yml#L10) | str | `/var/log/haproxy.log` |
| [haproxy_logging](defaults/main.yml#L436) | dict |  |
| [haproxy_logging.capture_request_headers](defaults/main.yml#L442) | list |  |
| [haproxy_logging.capture_response_headers](defaults/main.yml#L444) | list |  |
| [haproxy_logging.custom_log_format](defaults/main.yml#L446) | str |  |
| [haproxy_logging.destination](defaults/main.yml#L438) | str | `/dev/log` |
| [haproxy_logging.facility](defaults/main.yml#L439) | str | `local0` |
| [haproxy_logging.level](defaults/main.yml#L440) | str | `info` |
| [haproxy_logging.per_backend_log_level](defaults/main.yml#L448) | dict |  |
| [haproxy_logrotate_file](defaults/main.yml#L11) | str | `/etc/logrotate.d/haproxy` |
| [haproxy_peers](defaults/main.yml#L482) | dict |  |
| [haproxy_peers.enabled](defaults/main.yml#L483) | bool |  |
| [haproxy_peers.name](defaults/main.yml#L484) | str | `haproxy_cluster` |
| [haproxy_peers.peers](defaults/main.yml#L485) | list |  |
| [haproxy_private_ip](defaults/main.yml#L29) | str |  |
| [haproxy_public_ip](defaults/main.yml#L24) | str |  |
| [haproxy_rate_limits](defaults/main.yml#L399) | list |  |
| [haproxy_security](defaults/main.yml#L412) | dict |  |
| [haproxy_security.hide_server_header](defaults/main.yml#L430) | bool |  |
| [haproxy_security.ip_blacklist](defaults/main.yml#L419) | dict |  |
| [haproxy_security.ip_blacklist.apply_to](defaults/main.yml#L424) | list |  |
| [haproxy_security.ip_blacklist.enabled](defaults/main.yml#L420) | bool |  |
| [haproxy_security.ip_blacklist.ips](defaults/main.yml#L422) | list |  |
| [haproxy_security.ip_whitelist](defaults/main.yml#L413) | dict |  |
| [haproxy_security.ip_whitelist.apply_to](defaults/main.yml#L418) | list |  |
| [haproxy_security.ip_whitelist.enabled](defaults/main.yml#L414) | bool |  |
| [haproxy_security.ip_whitelist.ips](defaults/main.yml#L416) | list |  |
| [haproxy_security.request_body_size_limit](defaults/main.yml#L425) | dict |  |
| [haproxy_security.request_body_size_limit.enabled](defaults/main.yml#L426) | bool |  |
| [haproxy_security.request_body_size_limit.max_bytes](defaults/main.yml#L428) | int | `10485760` |
| [haproxy_ssl](defaults/main.yml#L356) | dict |  |
| [haproxy_ssl.cert_dir](defaults/main.yml#L358) | str | `{{ haproxy_config_dir }}/certs` |
| [haproxy_ssl.default_bind_ciphers](defaults/main.yml#L360) | str |  |
| [haproxy_ssl.default_bind_options](defaults/main.yml#L362) | str |  |
| [haproxy_ssl.ocsp_stapling](defaults/main.yml#L366) | bool |  |
| [haproxy_ssl.session_cache_size](defaults/main.yml#L364) | int | `20000` |
| [haproxy_stats](defaults/main.yml#L454) | dict |  |
| [haproxy_stats.auth](defaults/main.yml#L461) | dict |  |
| [haproxy_stats.auth.enabled](defaults/main.yml#L462) | bool |  |
| [haproxy_stats.auth.password](defaults/main.yml#L464) | str |  |
| [haproxy_stats.auth.username](defaults/main.yml#L463) | str | `admin` |
| [haproxy_stats.bind_ip](defaults/main.yml#L457) | str | `127.0.0.1` |
| [haproxy_stats.enabled](defaults/main.yml#L456) | bool |  |
| [haproxy_stats.port](defaults/main.yml#L458) | int | `8404` |
| [haproxy_stats.prometheus](defaults/main.yml#L465) | dict |  |
| [haproxy_stats.prometheus.enabled](defaults/main.yml#L467) | bool |  |
| [haproxy_stats.prometheus.uri](defaults/main.yml#L468) | str | `/metrics` |
| [haproxy_stats.refresh](defaults/main.yml#L460) | str | `10s` |
| [haproxy_stats.runtime_api](defaults/main.yml#L469) | dict |  |
| [haproxy_stats.runtime_api.enabled](defaults/main.yml#L471) | bool |  |
| [haproxy_stats.runtime_api.level](defaults/main.yml#L473) | str | `admin` |
| [haproxy_stats.runtime_api.socket](defaults/main.yml#L472) | str | `/var/run/haproxy/admin.sock` |
| [haproxy_stats.uri](defaults/main.yml#L459) | str | `/stats` |
| [haproxy_stick_tables](defaults/main.yml#L384) | list |  |
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
| [Validate HAProxy configuration syntax](tasks/validation.yml#L) | ansible.builtin.command | No | N/A |




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
