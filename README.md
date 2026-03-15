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
| [haproxy_backend](defaults/main.yml#L257) | list |  |
| [haproxy_backend.0](defaults/main.yml#L258) | dict |  |
| [haproxy_backend.0.acl](defaults/main.yml#L283) | list |  |
| [haproxy_backend.0.acl.0](defaults/main.yml#L284) | dict |  |
| [haproxy_backend.0.acl.0.fetch](defaults/main.yml#L285) | str | `path -i /` |
| [haproxy_backend.0.acl.0.name](defaults/main.yml#L284) | str | `is_root` |
| [haproxy_backend.0.acl.1](defaults/main.yml#L286) | dict |  |
| [haproxy_backend.0.acl.1.fetch](defaults/main.yml#L287) | str | `res.hdr(Set-cookie) -m sub Path=` |
| [haproxy_backend.0.acl.1.name](defaults/main.yml#L286) | str | `hdr_set_cookie_path` |
| [haproxy_backend.0.balance](defaults/main.yml#L260) | str | `source` |
| [haproxy_backend.0.compression](defaults/main.yml#L264) | dict |  |
| [haproxy_backend.0.compression.algo](defaults/main.yml#L265) | str | `gzip` |
| [haproxy_backend.0.compression.type](defaults/main.yml#L266) | list |  |
| [haproxy_backend.0.compression.type.0](defaults/main.yml#L267) | str | `text/plain` |
| [haproxy_backend.0.compression.type.1](defaults/main.yml#L268) | str | `text/css` |
| [haproxy_backend.0.compression.type.2](defaults/main.yml#L269) | str | `application/json` |
| [haproxy_backend.0.compression.type.3](defaults/main.yml#L270) | str | `application/x-javascript` |
| [haproxy_backend.0.compression.type.4](defaults/main.yml#L271) | str | `text/xml` |
| [haproxy_backend.0.compression.type.5](defaults/main.yml#L272) | str | `application/xml` |
| [haproxy_backend.0.compression.type.6](defaults/main.yml#L273) | str | `application/xml+rss` |
| [haproxy_backend.0.compression.type.7](defaults/main.yml#L274) | str | `text/javascript` |
| [haproxy_backend.0.compression.type.8](defaults/main.yml#L275) | str | `application/javascript` |
| [haproxy_backend.0.hash_type](defaults/main.yml#L261) | dict |  |
| [haproxy_backend.0.hash_type.function](defaults/main.yml#L263) | str | `djb2` |
| [haproxy_backend.0.hash_type.method](defaults/main.yml#L262) | str | `consistent` |
| [haproxy_backend.0.http_request](defaults/main.yml#L288) | list |  |
| [haproxy_backend.0.http_request.0](defaults/main.yml#L289) | dict |  |
| [haproxy_backend.0.http_request.0.action](defaults/main.yml#L289) | str | `set-header` |
| [haproxy_backend.0.http_request.0.condition](defaults/main.yml#L291) | str | `!{ ssl_fc } is_root` |
| [haproxy_backend.0.http_request.0.params](defaults/main.yml#L290) | str | `Test-Header test-value` |
| [haproxy_backend.0.http_response](defaults/main.yml#L292) | list |  |
| [haproxy_backend.0.http_response.0](defaults/main.yml#L293) | dict |  |
| [haproxy_backend.0.http_response.0.action](defaults/main.yml#L293) | str | `replace-value` |
| [haproxy_backend.0.http_response.0.condition](defaults/main.yml#L295) | str | `is_root` |
| [haproxy_backend.0.http_response.0.params](defaults/main.yml#L294) | str | `Cache-control ^public$ private` |
| [haproxy_backend.0.mode](defaults/main.yml#L259) | str | `http` |
| [haproxy_backend.0.name](defaults/main.yml#L258) | str | `app` |
| [haproxy_backend.0.option](defaults/main.yml#L276) | list |  |
| [haproxy_backend.0.option.0](defaults/main.yml#L277) | dict |  |
| [haproxy_backend.0.option.0.name](defaults/main.yml#L277) | str | `forwardfor` |
| [haproxy_backend.0.option.1](defaults/main.yml#L278) | dict |  |
| [haproxy_backend.0.option.1.name](defaults/main.yml#L278) | str | `httpchk` |
| [haproxy_backend.0.option.1.params](defaults/main.yml#L279) | str | `/` |
| [haproxy_backend.0.server](defaults/main.yml#L299) | list |  |
| [haproxy_backend.0.server.0](defaults/main.yml#L300) | dict |  |
| [haproxy_backend.0.server.0.address](defaults/main.yml#L301) | str | `10.10.10.10` |
| [haproxy_backend.0.server.0.name](defaults/main.yml#L300) | str | `server1` |
| [haproxy_backend.0.server.0.params](defaults/main.yml#L303) | str | `check` |
| [haproxy_backend.0.server.0.port](defaults/main.yml#L302) | int | `6400` |
| [haproxy_backend.0.server.1](defaults/main.yml#L304) | dict |  |
| [haproxy_backend.0.server.1.address](defaults/main.yml#L305) | str | `10.10.10.11` |
| [haproxy_backend.0.server.1.name](defaults/main.yml#L304) | str | `server2` |
| [haproxy_backend.0.server.1.params](defaults/main.yml#L307) | str | `check` |
| [haproxy_backend.0.server.1.port](defaults/main.yml#L306) | int | `6400` |
| [haproxy_backend.0.stick](defaults/main.yml#L312) | list |  |
| [haproxy_backend.0.stick.0](defaults/main.yml#L313) | dict |  |
| [haproxy_backend.0.stick.0.pattern](defaults/main.yml#L314) | str | `res.cook(JSESSIONID)` |
| [haproxy_backend.0.stick.0.table](defaults/main.yml#L315) | str | `app` |
| [haproxy_backend.0.stick.0.type](defaults/main.yml#L313) | str | `store-response` |
| [haproxy_backend.0.stick.1](defaults/main.yml#L316) | dict |  |
| [haproxy_backend.0.stick.1.pattern](defaults/main.yml#L317) | str | `req.cook(JSESSIONID)` |
| [haproxy_backend.0.stick.1.type](defaults/main.yml#L316) | str | `on` |
| [haproxy_backend.0.stick_table](defaults/main.yml#L308) | dict |  |
| [haproxy_backend.0.stick_table.len](defaults/main.yml#L310) | int | `32` |
| [haproxy_backend.0.stick_table.size](defaults/main.yml#L311) | str | `1M` |
| [haproxy_backend.0.stick_table.type](defaults/main.yml#L309) | str | `string` |
| [haproxy_backend.0.timeout](defaults/main.yml#L280) | list |  |
| [haproxy_backend.0.timeout.0](defaults/main.yml#L281) | dict |  |
| [haproxy_backend.0.timeout.0.name](defaults/main.yml#L281) | str | `tunnel` |
| [haproxy_backend.0.timeout.0.value](defaults/main.yml#L282) | str | `86400s` |
| [haproxy_backend.0.use_server](defaults/main.yml#L296) | list |  |
| [haproxy_backend.0.use_server.0](defaults/main.yml#L297) | dict |  |
| [haproxy_backend.0.use_server.0.condition](defaults/main.yml#L298) | str | `hdr(host) -i test.nnc.guru` |
| [haproxy_backend.0.use_server.0.name](defaults/main.yml#L297) | str | `server1` |
| [haproxy_cert_dir](defaults/main.yml#L16) | str | `{{ haproxy_config_dir }}/certs` |
| [haproxy_cert_name](defaults/main.yml#L17) | str |  |
| [haproxy_config_dir](defaults/main.yml#L8) | str | `/etc/haproxy` |
| [haproxy_defaults](defaults/main.yml#L81) | dict |  |
| [haproxy_defaults.log](defaults/main.yml#L83) | list |  |
| [haproxy_defaults.log.0](defaults/main.yml#L84) | dict |  |
| [haproxy_defaults.log.0.global](defaults/main.yml#L84) | bool | `True` |
| [haproxy_defaults.maxconn](defaults/main.yml#L108) | int | `3000` |
| [haproxy_defaults.mode](defaults/main.yml#L82) | str | `http` |
| [haproxy_defaults.option](defaults/main.yml#L85) | list |  |
| [haproxy_defaults.option.0](defaults/main.yml#L86) | dict |  |
| [haproxy_defaults.option.0.name](defaults/main.yml#L86) | str | `httplog` |
| [haproxy_defaults.option.1](defaults/main.yml#L87) | dict |  |
| [haproxy_defaults.option.1.name](defaults/main.yml#L87) | str | `dontlognull` |
| [haproxy_defaults.option.2](defaults/main.yml#L88) | dict |  |
| [haproxy_defaults.option.2.name](defaults/main.yml#L88) | str | `http-server-close` |
| [haproxy_defaults.option.3](defaults/main.yml#L89) | dict |  |
| [haproxy_defaults.option.3.name](defaults/main.yml#L89) | str | `forwardfor` |
| [haproxy_defaults.option.3.params](defaults/main.yml#L90) | str | `except 127.0.0.0/8` |
| [haproxy_defaults.option.4](defaults/main.yml#L91) | dict |  |
| [haproxy_defaults.option.4.name](defaults/main.yml#L91) | str | `redispatch` |
| [haproxy_defaults.retries](defaults/main.yml#L92) | int | `3` |
| [haproxy_defaults.timeout](defaults/main.yml#L93) | list |  |
| [haproxy_defaults.timeout.0](defaults/main.yml#L94) | dict |  |
| [haproxy_defaults.timeout.0.name](defaults/main.yml#L94) | str | `http-request` |
| [haproxy_defaults.timeout.0.value](defaults/main.yml#L95) | str | `10s` |
| [haproxy_defaults.timeout.1](defaults/main.yml#L96) | dict |  |
| [haproxy_defaults.timeout.1.name](defaults/main.yml#L96) | str | `queue` |
| [haproxy_defaults.timeout.1.value](defaults/main.yml#L97) | str | `1m` |
| [haproxy_defaults.timeout.2](defaults/main.yml#L98) | dict |  |
| [haproxy_defaults.timeout.2.name](defaults/main.yml#L98) | str | `connect` |
| [haproxy_defaults.timeout.2.value](defaults/main.yml#L99) | str | `10s` |
| [haproxy_defaults.timeout.3](defaults/main.yml#L100) | dict |  |
| [haproxy_defaults.timeout.3.name](defaults/main.yml#L100) | str | `client` |
| [haproxy_defaults.timeout.3.value](defaults/main.yml#L101) | str | `1m` |
| [haproxy_defaults.timeout.4](defaults/main.yml#L102) | dict |  |
| [haproxy_defaults.timeout.4.name](defaults/main.yml#L102) | str | `server` |
| [haproxy_defaults.timeout.4.value](defaults/main.yml#L103) | str | `1m` |
| [haproxy_defaults.timeout.5](defaults/main.yml#L104) | dict |  |
| [haproxy_defaults.timeout.5.name](defaults/main.yml#L104) | str | `http-keep-alive` |
| [haproxy_defaults.timeout.5.value](defaults/main.yml#L105) | str | `10s` |
| [haproxy_defaults.timeout.6](defaults/main.yml#L106) | dict |  |
| [haproxy_defaults.timeout.6.name](defaults/main.yml#L106) | str | `check` |
| [haproxy_defaults.timeout.6.value](defaults/main.yml#L107) | str | `10s` |
| [haproxy_destination_config_path](defaults/main.yml#L9) | str | `{{ haproxy_config_dir }}/haproxy.cfg` |
| [haproxy_frontend](defaults/main.yml#L150) | list |  |
| [haproxy_frontend.0](defaults/main.yml#L151) | dict |  |
| [haproxy_frontend.0.backlog](defaults/main.yml#L158) | int | `10000` |
| [haproxy_frontend.0.bind](defaults/main.yml#L153) | list |  |
| [haproxy_frontend.0.bind.0](defaults/main.yml#L154) | dict |  |
| [haproxy_frontend.0.bind.0.address](defaults/main.yml#L154) | str | `127.0.0.1` |
| [haproxy_frontend.0.bind.0.port](defaults/main.yml#L155) | int | `5001` |
| [haproxy_frontend.0.bind.1](defaults/main.yml#L156) | dict |  |
| [haproxy_frontend.0.bind.1.address](defaults/main.yml#L156) | str | `127.0.0.1` |
| [haproxy_frontend.0.bind.1.port](defaults/main.yml#L157) | int | `5002` |
| [haproxy_frontend.0.default_backend](defaults/main.yml#L162) | str | `app` |
| [haproxy_frontend.0.mode](defaults/main.yml#L152) | str | `http` |
| [haproxy_frontend.0.name](defaults/main.yml#L151) | str | `main-http` |
| [haproxy_frontend.0.use_backend](defaults/main.yml#L159) | list |  |
| [haproxy_frontend.0.use_backend.0](defaults/main.yml#L160) | dict |  |
| [haproxy_frontend.0.use_backend.0.condition](defaults/main.yml#L161) | str | `!{ ssl_fc }` |
| [haproxy_frontend.0.use_backend.0.name](defaults/main.yml#L160) | str | `app` |
| [haproxy_frontend.1](defaults/main.yml#L163) | dict |  |
| [haproxy_frontend.1.acl](defaults/main.yml#L189) | list |  |
| [haproxy_frontend.1.acl.0](defaults/main.yml#L190) | dict |  |
| [haproxy_frontend.1.acl.0.fetch](defaults/main.yml#L191) | str | `path -i  /` |
| [haproxy_frontend.1.acl.0.name](defaults/main.yml#L190) | str | `is_root` |
| [haproxy_frontend.1.bind](defaults/main.yml#L165) | list |  |
| [haproxy_frontend.1.bind.0](defaults/main.yml#L166) | dict |  |
| [haproxy_frontend.1.bind.0.address](defaults/main.yml#L166) | str | `127.0.0.1` |
| [haproxy_frontend.1.bind.0.port](defaults/main.yml#L167) | int | `5003` |
| [haproxy_frontend.1.capture](defaults/main.yml#L181) | list |  |
| [haproxy_frontend.1.capture.0](defaults/main.yml#L182) | dict |  |
| [haproxy_frontend.1.capture.0.len](defaults/main.yml#L184) | int | `32` |
| [haproxy_frontend.1.capture.0.name](defaults/main.yml#L183) | str | `JSESSIONID` |
| [haproxy_frontend.1.capture.0.type](defaults/main.yml#L182) | str | `cookie` |
| [haproxy_frontend.1.capture.1](defaults/main.yml#L185) | dict |  |
| [haproxy_frontend.1.capture.1.len](defaults/main.yml#L187) | int | `15` |
| [haproxy_frontend.1.capture.1.name](defaults/main.yml#L186) | str | `Host` |
| [haproxy_frontend.1.capture.1.type](defaults/main.yml#L185) | str | `request header` |
| [haproxy_frontend.1.http_request](defaults/main.yml#L192) | list |  |
| [haproxy_frontend.1.http_request.0](defaults/main.yml#L193) | dict |  |
| [haproxy_frontend.1.http_request.0.action](defaults/main.yml#L193) | str | `set-header` |
| [haproxy_frontend.1.http_request.0.condition](defaults/main.yml#L195) | str | `!{ ssl_fc }` |
| [haproxy_frontend.1.http_request.0.params](defaults/main.yml#L194) | str | `X-Forwarded-Proto http` |
| [haproxy_frontend.1.mode](defaults/main.yml#L164) | str | `http` |
| [haproxy_frontend.1.monitor_uri](defaults/main.yml#L188) | str | `/haproxy` |
| [haproxy_frontend.1.name](defaults/main.yml#L163) | str | `main-https` |
| [haproxy_frontend.1.option](defaults/main.yml#L168) | list |  |
| [haproxy_frontend.1.option.0](defaults/main.yml#L169) | dict |  |
| [haproxy_frontend.1.option.0.name](defaults/main.yml#L169) | str | `contstats` |
| [haproxy_frontend.1.option.1](defaults/main.yml#L170) | dict |  |
| [haproxy_frontend.1.option.1.name](defaults/main.yml#L170) | str | `http-server-close` |
| [haproxy_frontend.1.option.2](defaults/main.yml#L171) | dict |  |
| [haproxy_frontend.1.option.2.name](defaults/main.yml#L171) | str | `httplog` |
| [haproxy_frontend.1.redirect](defaults/main.yml#L196) | list |  |
| [haproxy_frontend.1.redirect.0](defaults/main.yml#L197) | dict |  |
| [haproxy_frontend.1.redirect.0.code](defaults/main.yml#L199) | int | `301` |
| [haproxy_frontend.1.redirect.0.condition](defaults/main.yml#L201) | str | `!{ ssl_fc }` |
| [haproxy_frontend.1.redirect.0.option](defaults/main.yml#L200) | str | `drop-query` |
| [haproxy_frontend.1.redirect.0.type](defaults/main.yml#L197) | str | `scheme` |
| [haproxy_frontend.1.redirect.0.value](defaults/main.yml#L198) | str | `https` |
| [haproxy_frontend.1.timeout](defaults/main.yml#L172) | list |  |
| [haproxy_frontend.1.timeout.0](defaults/main.yml#L173) | dict |  |
| [haproxy_frontend.1.timeout.0.name](defaults/main.yml#L173) | str | `client` |
| [haproxy_frontend.1.timeout.0.value](defaults/main.yml#L174) | str | `300s` |
| [haproxy_frontend.1.timeout.1](defaults/main.yml#L175) | dict |  |
| [haproxy_frontend.1.timeout.1.name](defaults/main.yml#L175) | str | `http-keep-alive` |
| [haproxy_frontend.1.timeout.1.value](defaults/main.yml#L176) | str | `1s` |
| [haproxy_frontend.1.timeout.2](defaults/main.yml#L177) | dict |  |
| [haproxy_frontend.1.timeout.2.name](defaults/main.yml#L177) | str | `http-request` |
| [haproxy_frontend.1.timeout.2.value](defaults/main.yml#L178) | str | `15s` |
| [haproxy_frontend.1.timeout.3](defaults/main.yml#L179) | dict |  |
| [haproxy_frontend.1.timeout.3.name](defaults/main.yml#L179) | str | `tarpit` |
| [haproxy_frontend.1.timeout.3.value](defaults/main.yml#L180) | str | `60s` |
| [haproxy_frontend.1.use_backend](defaults/main.yml#L202) | list |  |
| [haproxy_frontend.1.use_backend.0](defaults/main.yml#L203) | dict |  |
| [haproxy_frontend.1.use_backend.0.condition](defaults/main.yml#L204) | str | `!{ ssl_fc }` |
| [haproxy_frontend.1.use_backend.0.name](defaults/main.yml#L203) | str | `app` |
| [haproxy_global](defaults/main.yml#L35) | dict |  |
| [haproxy_global.chroot](defaults/main.yml#L47) | str | `/var/lib/haproxy` |
| [haproxy_global.cpu_map](defaults/main.yml#L65) | str |  |
| [haproxy_global.daemon](defaults/main.yml#L52) | bool | `True` |
| [haproxy_global.group](defaults/main.yml#L51) | str | `haproxy` |
| [haproxy_global.log](defaults/main.yml#L36) | list |  |
| [haproxy_global.log.0](defaults/main.yml#L38) | dict |  |
| [haproxy_global.log.0.address](defaults/main.yml#L38) | str | `127.0.0.1` |
| [haproxy_global.log.0.facility](defaults/main.yml#L39) | str | `local0` |
| [haproxy_global.maxconn](defaults/main.yml#L49) | int | `4000` |
| [haproxy_global.nbthread](defaults/main.yml#L63) | int |  |
| [haproxy_global.pidfile](defaults/main.yml#L48) | str | `/var/run/haproxy.pid` |
| [haproxy_global.quiet](defaults/main.yml#L75) | bool |  |
| [haproxy_global.spread_checks](defaults/main.yml#L73) | int |  |
| [haproxy_global.stats_socket](defaults/main.yml#L53) | list |  |
| [haproxy_global.stats_socket.0](defaults/main.yml#L54) | dict |  |
| [haproxy_global.stats_socket.0.path](defaults/main.yml#L54) | str | `/var/lib/haproxy/stats` |
| [haproxy_global.tune](defaults/main.yml#L67) | dict |  |
| [haproxy_global.tune.bufsize](defaults/main.yml#L70) | int | `16384` |
| [haproxy_global.tune.maxrewrite](defaults/main.yml#L71) | int | `1024` |
| [haproxy_global.tune.ssl_cachesize](defaults/main.yml#L68) | int | `20000` |
| [haproxy_global.tune.ssl_lifetime](defaults/main.yml#L69) | int | `300` |
| [haproxy_global.tune_ssl_default_dh_param](defaults/main.yml#L46) | int | `2048` |
| [haproxy_global.user](defaults/main.yml#L50) | str | `haproxy` |
| [haproxy_letsencrypt](defaults/main.yml#L366) | dict |  |
| [haproxy_letsencrypt.cert_dir](defaults/main.yml#L372) | str | `/etc/letsencrypt/live` |
| [haproxy_letsencrypt.deploy_hook](defaults/main.yml#L374) | bool | `True` |
| [haproxy_letsencrypt.domains](defaults/main.yml#L370) | list |  |
| [haproxy_letsencrypt.enabled](defaults/main.yml#L368) | bool |  |
| [haproxy_listen](defaults/main.yml#L323) | list |  |
| [haproxy_listen.0](defaults/main.yml#L324) | dict |  |
| [haproxy_listen.0.bind](defaults/main.yml#L327) | list |  |
| [haproxy_listen.0.bind.0](defaults/main.yml#L328) | dict |  |
| [haproxy_listen.0.bind.0.address](defaults/main.yml#L328) | str | `127.0.0.1` |
| [haproxy_listen.0.bind.0.port](defaults/main.yml#L329) | int | `8000` |
| [haproxy_listen.0.mode](defaults/main.yml#L325) | str | `http` |
| [haproxy_listen.0.monitor_uri](defaults/main.yml#L326) | str | `/haproxy` |
| [haproxy_listen.0.name](defaults/main.yml#L324) | str | `http_health_check` |
| [haproxy_listen.0.option](defaults/main.yml#L330) | list |  |
| [haproxy_listen.0.option.0](defaults/main.yml#L331) | dict |  |
| [haproxy_listen.0.option.0.name](defaults/main.yml#L331) | str | `dontlognull` |
| [haproxy_listen.0.option.1](defaults/main.yml#L332) | dict |  |
| [haproxy_listen.0.option.1.name](defaults/main.yml#L332) | str | `httpchk` |
| [haproxy_listen.1](defaults/main.yml#L333) | dict |  |
| [haproxy_listen.1.bind](defaults/main.yml#L335) | list |  |
| [haproxy_listen.1.bind.0](defaults/main.yml#L336) | dict |  |
| [haproxy_listen.1.bind.0.address](defaults/main.yml#L336) | str | `127.0.0.1` |
| [haproxy_listen.1.bind.0.port](defaults/main.yml#L337) | int | `9000` |
| [haproxy_listen.1.mode](defaults/main.yml#L334) | str | `http` |
| [haproxy_listen.1.name](defaults/main.yml#L333) | str | `stats` |
| [haproxy_listen.1.stats](defaults/main.yml#L338) | dict |  |
| [haproxy_listen.1.stats.auth](defaults/main.yml#L345) | list |  |
| [haproxy_listen.1.stats.auth.0](defaults/main.yml#L346) | dict |  |
| [haproxy_listen.1.stats.auth.0.login](defaults/main.yml#L346) | str | `admin-user` |
| [haproxy_listen.1.stats.auth.0.password](defaults/main.yml#L347) | str | `password123` |
| [haproxy_listen.1.stats.enable](defaults/main.yml#L339) | bool | `True` |
| [haproxy_listen.1.stats.hide_version](defaults/main.yml#L340) | bool | `True` |
| [haproxy_listen.1.stats.realm](defaults/main.yml#L344) | str | `HAProxy\ Statistics` |
| [haproxy_listen.1.stats.refresh](defaults/main.yml#L348) | str | `5s` |
| [haproxy_listen.1.stats.scope](defaults/main.yml#L341) | list |  |
| [haproxy_listen.1.stats.scope.0](defaults/main.yml#L342) | str | `.` |
| [haproxy_listen.1.stats.uri](defaults/main.yml#L343) | str | `/admin?stats` |
| [haproxy_log_file](defaults/main.yml#L10) | str | `/var/log/haproxy.log` |
| [haproxy_logging](defaults/main.yml#L434) | dict |  |
| [haproxy_logging.capture_request_headers](defaults/main.yml#L440) | list |  |
| [haproxy_logging.capture_response_headers](defaults/main.yml#L442) | list |  |
| [haproxy_logging.custom_log_format](defaults/main.yml#L444) | str |  |
| [haproxy_logging.destination](defaults/main.yml#L436) | str | `/dev/log` |
| [haproxy_logging.facility](defaults/main.yml#L437) | str | `local0` |
| [haproxy_logging.level](defaults/main.yml#L438) | str | `info` |
| [haproxy_logging.per_backend_log_level](defaults/main.yml#L446) | dict |  |
| [haproxy_logrotate_file](defaults/main.yml#L11) | str | `/etc/logrotate.d/haproxy` |
| [haproxy_peers](defaults/main.yml#L480) | dict |  |
| [haproxy_peers.enabled](defaults/main.yml#L481) | bool |  |
| [haproxy_peers.name](defaults/main.yml#L482) | str | `haproxy_cluster` |
| [haproxy_peers.peers](defaults/main.yml#L483) | list |  |
| [haproxy_private_ip](defaults/main.yml#L29) | str |  |
| [haproxy_public_ip](defaults/main.yml#L24) | str |  |
| [haproxy_rate_limits](defaults/main.yml#L397) | list |  |
| [haproxy_security](defaults/main.yml#L410) | dict |  |
| [haproxy_security.hide_server_header](defaults/main.yml#L428) | bool |  |
| [haproxy_security.ip_blacklist](defaults/main.yml#L417) | dict |  |
| [haproxy_security.ip_blacklist.apply_to](defaults/main.yml#L422) | list |  |
| [haproxy_security.ip_blacklist.enabled](defaults/main.yml#L418) | bool |  |
| [haproxy_security.ip_blacklist.ips](defaults/main.yml#L420) | list |  |
| [haproxy_security.ip_whitelist](defaults/main.yml#L411) | dict |  |
| [haproxy_security.ip_whitelist.apply_to](defaults/main.yml#L416) | list |  |
| [haproxy_security.ip_whitelist.enabled](defaults/main.yml#L412) | bool |  |
| [haproxy_security.ip_whitelist.ips](defaults/main.yml#L414) | list |  |
| [haproxy_security.request_body_size_limit](defaults/main.yml#L423) | dict |  |
| [haproxy_security.request_body_size_limit.enabled](defaults/main.yml#L424) | bool |  |
| [haproxy_security.request_body_size_limit.max_bytes](defaults/main.yml#L426) | int | `10485760` |
| [haproxy_ssl](defaults/main.yml#L354) | dict |  |
| [haproxy_ssl.cert_dir](defaults/main.yml#L356) | str | `{{ haproxy_config_dir }}/certs` |
| [haproxy_ssl.default_bind_ciphers](defaults/main.yml#L358) | str |  |
| [haproxy_ssl.default_bind_options](defaults/main.yml#L360) | str |  |
| [haproxy_ssl.ocsp_stapling](defaults/main.yml#L364) | bool |  |
| [haproxy_ssl.session_cache_size](defaults/main.yml#L362) | int | `20000` |
| [haproxy_stats](defaults/main.yml#L452) | dict |  |
| [haproxy_stats.auth](defaults/main.yml#L459) | dict |  |
| [haproxy_stats.auth.enabled](defaults/main.yml#L460) | bool |  |
| [haproxy_stats.auth.password](defaults/main.yml#L462) | str |  |
| [haproxy_stats.auth.username](defaults/main.yml#L461) | str | `admin` |
| [haproxy_stats.bind_ip](defaults/main.yml#L455) | str | `127.0.0.1` |
| [haproxy_stats.enabled](defaults/main.yml#L454) | bool |  |
| [haproxy_stats.port](defaults/main.yml#L456) | int | `8404` |
| [haproxy_stats.prometheus](defaults/main.yml#L463) | dict |  |
| [haproxy_stats.prometheus.enabled](defaults/main.yml#L465) | bool |  |
| [haproxy_stats.prometheus.uri](defaults/main.yml#L466) | str | `/metrics` |
| [haproxy_stats.refresh](defaults/main.yml#L458) | str | `10s` |
| [haproxy_stats.runtime_api](defaults/main.yml#L467) | dict |  |
| [haproxy_stats.runtime_api.enabled](defaults/main.yml#L469) | bool |  |
| [haproxy_stats.runtime_api.level](defaults/main.yml#L471) | str | `admin` |
| [haproxy_stats.runtime_api.socket](defaults/main.yml#L470) | str | `/var/run/haproxy/admin.sock` |
| [haproxy_stats.uri](defaults/main.yml#L457) | str | `/stats` |
| [haproxy_stick_tables](defaults/main.yml#L382) | list |  |
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
