bash-4.2# cat /etc/docker/daemon.json
{
  "hosts": ["tcp://0.0.0.0:2375","unix:///var/run/docker.sock"]
}


Debug / TLS etc :
bash-4.2# cat /etc/docker/daemon.json.debug
{
  "debug": true,
  "tls": true,
  "tlscert": "/var/docker/server.pem",
  "tlskey": "/var/docker/serverkey.pem",
  "hosts": ["tcp://192.168.59.3:2376"]
}
