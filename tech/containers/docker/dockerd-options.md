dockerd | Docker Documentation<br>
 https://docs.docker.com/engine/reference/commandline/dockerd/#daemon-socket-option  



Docker - How do I set the Docker daemon options?
 https://success.docker.com/article/how-do-i-set-the-docker-daemon-options


Configure and troubleshoot the Docker daemon | Docker Documentation
 https://docs.docker.com/config/daemon/



Connecting to insecure registry
bash-4.2# cat /etc/sysconfig/docker

OPTIONS='-D --insecure-registry=ssss-docker-local.dockerhub-yyy.xxxcorp.com:443 --insecure-registry=dddd-docker-local.dockerhub-xxxx.yyycorp.com:80 --insecure-registry=http://dddd-docker-local.dockerhub-xxx.yyycorp.com:80 --insecure-registry=10.0.0.0/8'
