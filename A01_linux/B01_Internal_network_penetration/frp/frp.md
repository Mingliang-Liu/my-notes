# [frp官网](https://gofrp.org/zh-cn/docs/)

## github
https://github.com/fatedier/frp

## docker
https://hub.docker.com/r/fatedier/frps
https://hub.docker.com/r/fatedier/frpc

## 
```
docker run --restart=always --network host -d -v ~/docker/frps/frps.toml:/etc/frp/frps.toml --name frps fatedier/frps:v0.61.0
docker run --restart=always --network host -d -v ~/docker/frpc/frpc.toml:/etc/frp/frpc.toml --name frpc fatedier/frpc:v0.61.0
```

# toml参考
https://github.com/fatedier/frp/blob/dev/conf/frps_full_example.toml
```
docker run --restart=always --network host -d -v /root/docker/frps/:/etc/frp/ --name frps fatedier/frps:v0.61.0 -c /etc/frp/frps.toml未成功
```
```
docker run --restart=always --network host -d --name frps fatedier/frps:v0.61.0 \
--bind-port 7000 \
--dashboard-port 7500 \
--dashboard-addr "172.24.43.161"

docker run --restart=always --network host -d --name frpc fatedier/frpc:v0.61.0 \
tcp \
--server-addr 公网ip \
--proxy-name lml_ssh \
--local-port 22 \
--remote-port 15122

```
```
frps is the server of frp (https://github.com/fatedier/frp)

Usage:
  frps [flags]
  frps [command]

Available Commands:
  completion  Generate the autocompletion script for the specified shell
  help        Help about any command
  verify      Verify that the configures is valid

Flags:
      --allow-ports string               allow ports
      --bind-addr string                 bind address (default "0.0.0.0")
  -p, --bind-port int                    bind port (default 7000)
  -c, --config string                    config file of frps
      --dashboard-addr string            dashboard address (default "0.0.0.0")
      --dashboard-port int               dashboard port
      --dashboard-pwd string             dashboard password (default "admin")
      --dashboard-tls-cert-file string   dashboard tls cert file
      --dashboard-tls-key-file string    dashboard tls key file
      --dashboard-tls-mode               if enable dashboard tls mode
      --dashboard-user string            dashboard user (default "admin")
      --disable-log-color                disable log color in console
      --enable-prometheus                enable prometheus dashboard
  -h, --help                             help for frps
      --kcp-bind-port int                kcp bind udp port
      --log-file string                  log file (default "console")
      --log-level string                 log level (default "info")
      --log-max-days int                 log max days (default 3)
      --max-ports-per-client int         max ports per client
      --proxy-bind-addr string           proxy bind address (default "0.0.0.0")
      --strict-config                    strict config parsing mode, unknown fields will cause errors (default true)
      --subdomain-host string            subdomain host
      --tls-only                         frps tls only
  -t, --token string                     auth token
  -v, --version                          version of frps
      --vhost-http-port int              vhost http port
      --vhost-http-timeout int           vhost http response header timeout (default 60)
      --vhost-https-port int             vhost https port

Use "frps [command] --help" for more information about a command.
```

```
frpc is the client of frp (https://github.com/fatedier/frp)

Usage:
  frpc [flags]
  frpc [command]

Available Commands:
  completion  Generate the autocompletion script for the specified shell
  help        Help about any command
  http        Run frpc with a single http proxy
  https       Run frpc with a single https proxy
  nathole     Actions about nathole
  reload      Hot-Reload frpc configuration
  status      Overview of all proxies status
  stcp        Run frpc with a single stcp proxy
  stop        Stop the running frpc
  sudp        Run frpc with a single sudp proxy
  tcp         Run frpc with a single tcp proxy
  tcpmux      Run frpc with a single tcpmux proxy
  udp         Run frpc with a single udp proxy
  verify      Verify that the configures is valid
  xtcp        Run frpc with a single xtcp proxy

Flags:
  -c, --config string       config file of frpc (default "./frpc.ini")
      --config-dir string   config directory, run one frpc service for each file in config directory
  -h, --help                help for frpc
      --strict-config       strict config parsing mode, unknown fields will cause an errors (default true)
  -v, --version             version of frpc

Use "frpc [command] --help" for more information about a command.

docker run --rm fatedier/frpc:v0.61.0 tcp -h
Run frpc with a single tcp proxy

Usage:
  frpc tcp [flags]

Flags:
      --bandwidth-limit string        bandwidth limit (e.g. 100KB or 1MB)
      --bandwidth-limit-mode string   bandwidth limit mode (default "client")
      --disable-log-color             disable log color in console
      --dns-server string             specify dns server instead of using system default one
  -h, --help                          help for tcp
  -i, --local-ip string               local ip (default "127.0.0.1")
  -l, --local-port int                local port
      --log-file string               console or file path (default "console")
      --log-level string              log level (default "info")
      --log-max-days int              log file reversed days (default 3)
  -p, --protocol string               optional values are [tcp kcp quic websocket wss] (default "tcp")
  -n, --proxy-name string             proxy name
  -r, --remote-port int               remote port
  -s, --server-addr string            frp server's address (default "127.0.0.1")
  -P, --server-port int               frp server's port (default 7000)
      --tls-enable                    enable frpc tls (default true)
      --tls-server-name string        specify the custom server name of tls certificate
  -t, --token string                  auth token
      --uc                            use compression
      --ue                            use encryption
  -u, --user string                   user

Global Flags:
  -c, --config string       config file of frpc (default "./frpc.ini")
      --config-dir string   config directory, run one frpc service for each file in config directory
      --strict-config       strict config parsing mode, unknown fields will cause an errors (default true)
  -v, --version             version of frpc
```