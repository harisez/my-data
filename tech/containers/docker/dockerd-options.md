dockerd | Docker Documentation
 https://docs.docker.com/engine/reference/commandline/dockerd/#daemon-socket-option


Connecting to insecure registry
bash-4.2# cat /etc/sysconfig/docker
# /etc/sysconfig/docker

# Modify these options if you want to change the way the docker daemon runs

OPTIONS='-D --insecure-registry=ssss-docker-local.dockerhub-yyy.xxxcorp.com:443 --insecure-registry=dddd-docker-local.dockerhub-xxxx.yyycorp.com:80 --insecure-registry=http://dddd-docker-local.dockerhub-xxx.yyycorp.com:80 --insecure-registry=10.0.0.0/8'
