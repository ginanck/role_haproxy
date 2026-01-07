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
| [haproxy_backend](defaults/main.yml#L148) | list |  |
| [haproxy_backend.0](defaults/main.yml#L149) | dict |  |
| [haproxy_backend.0.acl](defaults/main.yml#L174) | list |  |
| [haproxy_backend.0.acl.0](defaults/main.yml#L175) | dict |  |
| [haproxy_backend.0.acl.0.fetch](defaults/main.yml#L176) | str | `path -i /` |
| [haproxy_backend.0.acl.0.name](defaults/main.yml#L175) | str | `is_root` |
| [haproxy_backend.0.acl.1](defaults/main.yml#L177) | dict |  |
| [haproxy_backend.0.acl.1.fetch](defaults/main.yml#L178) | str | `res.hdr(Set-cookie) -m sub Path=` |
| [haproxy_backend.0.acl.1.name](defaults/main.yml#L177) | str | `hdr_set_cookie_path` |
| [haproxy_backend.0.balance](defaults/main.yml#L151) | str | `source` |
| [haproxy_backend.0.compression](defaults/main.yml#L155) | dict |  |
| [haproxy_backend.0.compression.algo](defaults/main.yml#L156) | str | `gzip` |
| [haproxy_backend.0.compression.type](defaults/main.yml#L157) | list |  |
| [haproxy_backend.0.compression.type.0](defaults/main.yml#L158) | str | `text/plain` |
| [haproxy_backend.0.compression.type.1](defaults/main.yml#L159) | str | `text/css` |
| [haproxy_backend.0.compression.type.2](defaults/main.yml#L160) | str | `application/json` |
| [haproxy_backend.0.compression.type.3](defaults/main.yml#L161) | str | `application/x-javascript` |
| [haproxy_backend.0.compression.type.4](defaults/main.yml#L162) | str | `text/xml` |
| [haproxy_backend.0.compression.type.5](defaults/main.yml#L163) | str | `application/xml` |
| [haproxy_backend.0.compression.type.6](defaults/main.yml#L164) | str | `application/xml+rss` |
| [haproxy_backend.0.compression.type.7](defaults/main.yml#L165) | str | `text/javascript` |
| [haproxy_backend.0.compression.type.8](defaults/main.yml#L166) | str | `application/javascript` |
| [haproxy_backend.0.hash_type](defaults/main.yml#L152) | dict |  |
| [haproxy_backend.0.hash_type.function](defaults/main.yml#L154) | str | `djb2` |
| [haproxy_backend.0.hash_type.method](defaults/main.yml#L153) | str | `consistent` |
| [haproxy_backend.0.http_request](defaults/main.yml#L179) | list |  |
| [haproxy_backend.0.http_request.0](defaults/main.yml#L180) | dict |  |
| [haproxy_backend.0.http_request.0.action](defaults/main.yml#L180) | str | `set-header` |
| [haproxy_backend.0.http_request.0.condition](defaults/main.yml#L182) | str | `!{ ssl_fc } is_root` |
| [haproxy_backend.0.http_request.0.params](defaults/main.yml#L181) | str | `Test-Header test-value` |
| [haproxy_backend.0.http_response](defaults/main.yml#L183) | list |  |
| [haproxy_backend.0.http_response.0](defaults/main.yml#L184) | dict |  |
| [haproxy_backend.0.http_response.0.action](defaults/main.yml#L184) | str | `replace-value` |
| [haproxy_backend.0.http_response.0.condition](defaults/main.yml#L186) | str | `is_root` |
| [haproxy_backend.0.http_response.0.params](defaults/main.yml#L185) | str | `Cache-control ^public$ private` |
| [haproxy_backend.0.mode](defaults/main.yml#L150) | str | `http` |
| [haproxy_backend.0.name](defaults/main.yml#L149) | str | `app` |
| [haproxy_backend.0.option](defaults/main.yml#L167) | list |  |
| [haproxy_backend.0.option.0](defaults/main.yml#L168) | dict |  |
| [haproxy_backend.0.option.0.name](defaults/main.yml#L168) | str | `forwardfor` |
| [haproxy_backend.0.option.1](defaults/main.yml#L169) | dict |  |
| [haproxy_backend.0.option.1.name](defaults/main.yml#L169) | str | `httpchk` |
| [haproxy_backend.0.option.1.params](defaults/main.yml#L170) | str | `/` |
| [haproxy_backend.0.server](defaults/main.yml#L190) | list |  |
| [haproxy_backend.0.server.0](defaults/main.yml#L191) | dict |  |
| [haproxy_backend.0.server.0.address](defaults/main.yml#L192) | str | `10.10.10.10` |
| [haproxy_backend.0.server.0.name](defaults/main.yml#L191) | str | `server1` |
| [haproxy_backend.0.server.0.params](defaults/main.yml#L194) | str | `check` |
| [haproxy_backend.0.server.0.port](defaults/main.yml#L193) | int | `6400` |
| [haproxy_backend.0.server.1](defaults/main.yml#L195) | dict |  |
| [haproxy_backend.0.server.1.address](defaults/main.yml#L196) | str | `10.10.10.11` |
| [haproxy_backend.0.server.1.name](defaults/main.yml#L195) | str | `server2` |
| [haproxy_backend.0.server.1.params](defaults/main.yml#L198) | str | `check` |
| [haproxy_backend.0.server.1.port](defaults/main.yml#L197) | int | `6400` |
| [haproxy_backend.0.stick](defaults/main.yml#L203) | list |  |
| [haproxy_backend.0.stick.0](defaults/main.yml#L204) | dict |  |
| [haproxy_backend.0.stick.0.pattern](defaults/main.yml#L205) | str | `res.cook(JSESSIONID)` |
| [haproxy_backend.0.stick.0.table](defaults/main.yml#L206) | str | `app` |
| [haproxy_backend.0.stick.0.type](defaults/main.yml#L204) | str | `store-response` |
| [haproxy_backend.0.stick.1](defaults/main.yml#L207) | dict |  |
| [haproxy_backend.0.stick.1.pattern](defaults/main.yml#L208) | str | `req.cook(JSESSIONID)` |
| [haproxy_backend.0.stick.1.type](defaults/main.yml#L207) | str | `on` |
| [haproxy_backend.0.stick_table](defaults/main.yml#L199) | dict |  |
| [haproxy_backend.0.stick_table.len](defaults/main.yml#L201) | int | `32` |
| [haproxy_backend.0.stick_table.size](defaults/main.yml#L202) | str | `1M` |
| [haproxy_backend.0.stick_table.type](defaults/main.yml#L200) | str | `string` |
| [haproxy_backend.0.timeout](defaults/main.yml#L171) | list |  |
| [haproxy_backend.0.timeout.0](defaults/main.yml#L172) | dict |  |
| [haproxy_backend.0.timeout.0.name](defaults/main.yml#L172) | str | `tunnel` |
| [haproxy_backend.0.timeout.0.value](defaults/main.yml#L173) | str | `86400s` |
| [haproxy_backend.0.use_server](defaults/main.yml#L187) | list |  |
| [haproxy_backend.0.use_server.0](defaults/main.yml#L188) | dict |  |
| [haproxy_backend.0.use_server.0.condition](defaults/main.yml#L189) | str | `hdr(host) -i test.nnc.guru` |
| [haproxy_backend.0.use_server.0.name](defaults/main.yml#L188) | str | `server1` |
| [haproxy_cert_dir](defaults/main.yml#L12) | str | `{{ haproxy_config_dir }}/certs` |
| [haproxy_cert_name](defaults/main.yml#L13) | str |  |
| [haproxy_config_dir](defaults/main.yml#L4) | str | `/etc/haproxy` |
| [haproxy_defaults](defaults/main.yml#L36) | dict |  |
| [haproxy_defaults.log](defaults/main.yml#L38) | list |  |
| [haproxy_defaults.log.0](defaults/main.yml#L39) | dict |  |
| [haproxy_defaults.log.0.global](defaults/main.yml#L39) | bool | `True` |
| [haproxy_defaults.maxconn](defaults/main.yml#L63) | int | `3000` |
| [haproxy_defaults.mode](defaults/main.yml#L37) | str | `http` |
| [haproxy_defaults.option](defaults/main.yml#L40) | list |  |
| [haproxy_defaults.option.0](defaults/main.yml#L41) | dict |  |
| [haproxy_defaults.option.0.name](defaults/main.yml#L41) | str | `httplog` |
| [haproxy_defaults.option.1](defaults/main.yml#L42) | dict |  |
| [haproxy_defaults.option.1.name](defaults/main.yml#L42) | str | `dontlognull` |
| [haproxy_defaults.option.2](defaults/main.yml#L43) | dict |  |
| [haproxy_defaults.option.2.name](defaults/main.yml#L43) | str | `http-server-close` |
| [haproxy_defaults.option.3](defaults/main.yml#L44) | dict |  |
| [haproxy_defaults.option.3.name](defaults/main.yml#L44) | str | `forwardfor` |
| [haproxy_defaults.option.3.params](defaults/main.yml#L45) | str | `except 127.0.0.0/8` |
| [haproxy_defaults.option.4](defaults/main.yml#L46) | dict |  |
| [haproxy_defaults.option.4.name](defaults/main.yml#L46) | str | `redispatch` |
| [haproxy_defaults.retries](defaults/main.yml#L47) | int | `3` |
| [haproxy_defaults.timeout](defaults/main.yml#L48) | list |  |
| [haproxy_defaults.timeout.0](defaults/main.yml#L49) | dict |  |
| [haproxy_defaults.timeout.0.name](defaults/main.yml#L49) | str | `http-request` |
| [haproxy_defaults.timeout.0.value](defaults/main.yml#L50) | str | `10s` |
| [haproxy_defaults.timeout.1](defaults/main.yml#L51) | dict |  |
| [haproxy_defaults.timeout.1.name](defaults/main.yml#L51) | str | `queue` |
| [haproxy_defaults.timeout.1.value](defaults/main.yml#L52) | str | `1m` |
| [haproxy_defaults.timeout.2](defaults/main.yml#L53) | dict |  |
| [haproxy_defaults.timeout.2.name](defaults/main.yml#L53) | str | `connect` |
| [haproxy_defaults.timeout.2.value](defaults/main.yml#L54) | str | `10s` |
| [haproxy_defaults.timeout.3](defaults/main.yml#L55) | dict |  |
| [haproxy_defaults.timeout.3.name](defaults/main.yml#L55) | str | `client` |
| [haproxy_defaults.timeout.3.value](defaults/main.yml#L56) | str | `1m` |
| [haproxy_defaults.timeout.4](defaults/main.yml#L57) | dict |  |
| [haproxy_defaults.timeout.4.name](defaults/main.yml#L57) | str | `server` |
| [haproxy_defaults.timeout.4.value](defaults/main.yml#L58) | str | `1m` |
| [haproxy_defaults.timeout.5](defaults/main.yml#L59) | dict |  |
| [haproxy_defaults.timeout.5.name](defaults/main.yml#L59) | str | `http-keep-alive` |
| [haproxy_defaults.timeout.5.value](defaults/main.yml#L60) | str | `10s` |
| [haproxy_defaults.timeout.6](defaults/main.yml#L61) | dict |  |
| [haproxy_defaults.timeout.6.name](defaults/main.yml#L61) | str | `check` |
| [haproxy_defaults.timeout.6.value](defaults/main.yml#L62) | str | `10s` |
| [haproxy_destination_config_path](defaults/main.yml#L5) | str | `{{ haproxy_config_dir }}/haproxy.cfg` |
| [haproxy_frontend](defaults/main.yml#L92) | list |  |
| [haproxy_frontend.0](defaults/main.yml#L93) | dict |  |
| [haproxy_frontend.0.backlog](defaults/main.yml#L100) | int | `10000` |
| [haproxy_frontend.0.bind](defaults/main.yml#L95) | list |  |
| [haproxy_frontend.0.bind.0](defaults/main.yml#L96) | dict |  |
| [haproxy_frontend.0.bind.0.address](defaults/main.yml#L96) | str | `127.0.0.1` |
| [haproxy_frontend.0.bind.0.port](defaults/main.yml#L97) | int | `5001` |
| [haproxy_frontend.0.bind.1](defaults/main.yml#L98) | dict |  |
| [haproxy_frontend.0.bind.1.address](defaults/main.yml#L98) | str | `127.0.0.1` |
| [haproxy_frontend.0.bind.1.port](defaults/main.yml#L99) | int | `5002` |
| [haproxy_frontend.0.default_backend](defaults/main.yml#L104) | str | `app` |
| [haproxy_frontend.0.mode](defaults/main.yml#L94) | str | `http` |
| [haproxy_frontend.0.name](defaults/main.yml#L93) | str | `main-http` |
| [haproxy_frontend.0.use_backend](defaults/main.yml#L101) | list |  |
| [haproxy_frontend.0.use_backend.0](defaults/main.yml#L102) | dict |  |
| [haproxy_frontend.0.use_backend.0.condition](defaults/main.yml#L103) | str | `!{ ssl_fc }` |
| [haproxy_frontend.0.use_backend.0.name](defaults/main.yml#L102) | str | `app` |
| [haproxy_frontend.1](defaults/main.yml#L105) | dict |  |
| [haproxy_frontend.1.acl](defaults/main.yml#L131) | list |  |
| [haproxy_frontend.1.acl.0](defaults/main.yml#L132) | dict |  |
| [haproxy_frontend.1.acl.0.fetch](defaults/main.yml#L133) | str | `path -i  /` |
| [haproxy_frontend.1.acl.0.name](defaults/main.yml#L132) | str | `is_root` |
| [haproxy_frontend.1.bind](defaults/main.yml#L107) | list |  |
| [haproxy_frontend.1.bind.0](defaults/main.yml#L108) | dict |  |
| [haproxy_frontend.1.bind.0.address](defaults/main.yml#L108) | str | `127.0.0.1` |
| [haproxy_frontend.1.bind.0.port](defaults/main.yml#L109) | int | `5003` |
| [haproxy_frontend.1.capture](defaults/main.yml#L123) | list |  |
| [haproxy_frontend.1.capture.0](defaults/main.yml#L124) | dict |  |
| [haproxy_frontend.1.capture.0.len](defaults/main.yml#L126) | int | `32` |
| [haproxy_frontend.1.capture.0.name](defaults/main.yml#L125) | str | `JSESSIONID` |
| [haproxy_frontend.1.capture.0.type](defaults/main.yml#L124) | str | `cookie` |
| [haproxy_frontend.1.capture.1](defaults/main.yml#L127) | dict |  |
| [haproxy_frontend.1.capture.1.len](defaults/main.yml#L129) | int | `15` |
| [haproxy_frontend.1.capture.1.name](defaults/main.yml#L128) | str | `Host` |
| [haproxy_frontend.1.capture.1.type](defaults/main.yml#L127) | str | `request header` |
| [haproxy_frontend.1.http_request](defaults/main.yml#L134) | list |  |
| [haproxy_frontend.1.http_request.0](defaults/main.yml#L135) | dict |  |
| [haproxy_frontend.1.http_request.0.action](defaults/main.yml#L135) | str | `set-header` |
| [haproxy_frontend.1.http_request.0.condition](defaults/main.yml#L137) | str | `!{ ssl_fc }` |
| [haproxy_frontend.1.http_request.0.params](defaults/main.yml#L136) | str | `X-Forwarded-Proto http` |
| [haproxy_frontend.1.mode](defaults/main.yml#L106) | str | `http` |
| [haproxy_frontend.1.monitor_uri](defaults/main.yml#L130) | str | `/haproxy` |
| [haproxy_frontend.1.name](defaults/main.yml#L105) | str | `main-https` |
| [haproxy_frontend.1.option](defaults/main.yml#L110) | list |  |
| [haproxy_frontend.1.option.0](defaults/main.yml#L111) | dict |  |
| [haproxy_frontend.1.option.0.name](defaults/main.yml#L111) | str | `contstats` |
| [haproxy_frontend.1.option.1](defaults/main.yml#L112) | dict |  |
| [haproxy_frontend.1.option.1.name](defaults/main.yml#L112) | str | `http-server-close` |
| [haproxy_frontend.1.option.2](defaults/main.yml#L113) | dict |  |
| [haproxy_frontend.1.option.2.name](defaults/main.yml#L113) | str | `httplog` |
| [haproxy_frontend.1.redirect](defaults/main.yml#L138) | list |  |
| [haproxy_frontend.1.redirect.0](defaults/main.yml#L139) | dict |  |
| [haproxy_frontend.1.redirect.0.code](defaults/main.yml#L141) | int | `301` |
| [haproxy_frontend.1.redirect.0.condition](defaults/main.yml#L143) | str | `!{ ssl_fc }` |
| [haproxy_frontend.1.redirect.0.option](defaults/main.yml#L142) | str | `drop-query` |
| [haproxy_frontend.1.redirect.0.type](defaults/main.yml#L139) | str | `scheme` |
| [haproxy_frontend.1.redirect.0.value](defaults/main.yml#L140) | str | `https` |
| [haproxy_frontend.1.timeout](defaults/main.yml#L114) | list |  |
| [haproxy_frontend.1.timeout.0](defaults/main.yml#L115) | dict |  |
| [haproxy_frontend.1.timeout.0.name](defaults/main.yml#L115) | str | `client` |
| [haproxy_frontend.1.timeout.0.value](defaults/main.yml#L116) | str | `300s` |
| [haproxy_frontend.1.timeout.1](defaults/main.yml#L117) | dict |  |
| [haproxy_frontend.1.timeout.1.name](defaults/main.yml#L117) | str | `http-keep-alive` |
| [haproxy_frontend.1.timeout.1.value](defaults/main.yml#L118) | str | `1s` |
| [haproxy_frontend.1.timeout.2](defaults/main.yml#L119) | dict |  |
| [haproxy_frontend.1.timeout.2.name](defaults/main.yml#L119) | str | `http-request` |
| [haproxy_frontend.1.timeout.2.value](defaults/main.yml#L120) | str | `15s` |
| [haproxy_frontend.1.timeout.3](defaults/main.yml#L121) | dict |  |
| [haproxy_frontend.1.timeout.3.name](defaults/main.yml#L121) | str | `tarpit` |
| [haproxy_frontend.1.timeout.3.value](defaults/main.yml#L122) | str | `60s` |
| [haproxy_frontend.1.use_backend](defaults/main.yml#L144) | list |  |
| [haproxy_frontend.1.use_backend.0](defaults/main.yml#L145) | dict |  |
| [haproxy_frontend.1.use_backend.0.condition](defaults/main.yml#L146) | str | `!{ ssl_fc }` |
| [haproxy_frontend.1.use_backend.0.name](defaults/main.yml#L145) | str | `app` |
| [haproxy_global](defaults/main.yml#L15) | dict |  |
| [haproxy_global.chroot](defaults/main.yml#L27) | str | `/var/lib/haproxy` |
| [haproxy_global.daemon](defaults/main.yml#L32) | bool | `True` |
| [haproxy_global.group](defaults/main.yml#L31) | str | `haproxy` |
| [haproxy_global.log](defaults/main.yml#L16) | list |  |
| [haproxy_global.log.0](defaults/main.yml#L18) | dict |  |
| [haproxy_global.log.0.address](defaults/main.yml#L18) | str | `127.0.0.1` |
| [haproxy_global.log.0.facility](defaults/main.yml#L19) | str | `local0` |
| [haproxy_global.maxconn](defaults/main.yml#L29) | int | `4000` |
| [haproxy_global.pidfile](defaults/main.yml#L28) | str | `/var/run/haproxy.pid` |
| [haproxy_global.stats_socket](defaults/main.yml#L33) | list |  |
| [haproxy_global.stats_socket.0](defaults/main.yml#L34) | dict |  |
| [haproxy_global.stats_socket.0.path](defaults/main.yml#L34) | str | `/var/lib/haproxy/stats` |
| [haproxy_global.tune_ssl_default_dh_param](defaults/main.yml#L26) | int | `2048` |
| [haproxy_global.user](defaults/main.yml#L30) | str | `haproxy` |
| [haproxy_listen](defaults/main.yml#L65) | list |  |
| [haproxy_listen.0](defaults/main.yml#L66) | dict |  |
| [haproxy_listen.0.bind](defaults/main.yml#L69) | list |  |
| [haproxy_listen.0.bind.0](defaults/main.yml#L70) | dict |  |
| [haproxy_listen.0.bind.0.address](defaults/main.yml#L70) | str | `127.0.0.1` |
| [haproxy_listen.0.bind.0.port](defaults/main.yml#L71) | int | `8000` |
| [haproxy_listen.0.mode](defaults/main.yml#L67) | str | `http` |
| [haproxy_listen.0.monitor_uri](defaults/main.yml#L68) | str | `/haproxy` |
| [haproxy_listen.0.name](defaults/main.yml#L66) | str | `http_health_check` |
| [haproxy_listen.0.option](defaults/main.yml#L72) | list |  |
| [haproxy_listen.0.option.0](defaults/main.yml#L73) | dict |  |
| [haproxy_listen.0.option.0.name](defaults/main.yml#L73) | str | `dontlognull` |
| [haproxy_listen.0.option.1](defaults/main.yml#L74) | dict |  |
| [haproxy_listen.0.option.1.name](defaults/main.yml#L74) | str | `httpchk` |
| [haproxy_listen.1](defaults/main.yml#L75) | dict |  |
| [haproxy_listen.1.bind](defaults/main.yml#L77) | list |  |
| [haproxy_listen.1.bind.0](defaults/main.yml#L78) | dict |  |
| [haproxy_listen.1.bind.0.address](defaults/main.yml#L78) | str | `127.0.0.1` |
| [haproxy_listen.1.bind.0.port](defaults/main.yml#L79) | int | `9000` |
| [haproxy_listen.1.mode](defaults/main.yml#L76) | str | `http` |
| [haproxy_listen.1.name](defaults/main.yml#L75) | str | `stats` |
| [haproxy_listen.1.stats](defaults/main.yml#L80) | dict |  |
| [haproxy_listen.1.stats.auth](defaults/main.yml#L87) | list |  |
| [haproxy_listen.1.stats.auth.0](defaults/main.yml#L88) | dict |  |
| [haproxy_listen.1.stats.auth.0.login](defaults/main.yml#L88) | str | `admin-user` |
| [haproxy_listen.1.stats.auth.0.password](defaults/main.yml#L89) | str | `password123` |
| [haproxy_listen.1.stats.enable](defaults/main.yml#L81) | bool | `True` |
| [haproxy_listen.1.stats.hide_version](defaults/main.yml#L82) | bool | `True` |
| [haproxy_listen.1.stats.realm](defaults/main.yml#L86) | str | `HAProxy\ Statistics` |
| [haproxy_listen.1.stats.refresh](defaults/main.yml#L90) | str | `5s` |
| [haproxy_listen.1.stats.scope](defaults/main.yml#L83) | list |  |
| [haproxy_listen.1.stats.scope.0](defaults/main.yml#L84) | str | `.` |
| [haproxy_listen.1.stats.uri](defaults/main.yml#L85) | str | `/admin?stats` |
| [haproxy_log_file](defaults/main.yml#L6) | str | `/var/log/haproxy.log` |
| [haproxy_logrotate_file](defaults/main.yml#L7) | str | `/etc/logrotate.d/haproxy` |
| [haproxy_whitelist_file_dir](defaults/main.yml#L9) | str | `{{ haproxy_config_dir }}/whitelist` |
| [haproxy_whitelist_file_name](defaults/main.yml#L10) | str |  |




## Task Overview


This role performs the following tasks:


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
| [Configure haproxy using haproxy.cfg](tasks/main.yml#L) | ansible.builtin.template | No | N/A |




### File: `tasks/install-RedHat.yml`

| Task Name | Module | Has Conditions | Line |
|-----------|--------|----------------|------|
| [Install HAProxy from YUM Repository](tasks/install-RedHat.yml#L) | ansible.builtin.yum | No | N/A |






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
