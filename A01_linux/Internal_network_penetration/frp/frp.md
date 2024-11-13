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