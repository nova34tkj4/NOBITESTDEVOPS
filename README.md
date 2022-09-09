# NOBITESTDEVOPS
1. Deploy two linux vm instance
2. Install Docker
-sudo yum install -y yum-utils
-sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
-sudo yum install docker-ce docker-ce-cli containerd.io docker-compose-plugin
-sudo systemctl start docker
3. Deploy simple nodejs using docker
-create directory nodejs
-create a package.json file that describes app and its dependencies
-create a server.js file that defines a web app using the Express.js framework
-Creating a Dockerfile
-Building image : docker build . -t nodejs/node-web-app
-Run image : docker run -p 8080:8080 -d nodejs/node-web-app
-test : curl -i localhost:8080
4. Deploy nginx container inside docker
FROM nginx:latest
5.  Deploy reserve proxy to nodejs
-create directory nginx
-create default.conf for reserve proxy
-Creating a Dockerfile
-Building image : sudo docker build -t nginx-reverse-proxy .
-Run image : docker run -p 80:80 -d nodejs/node-web-app
-test: Test curl from instance b and success reserve proxy instance a

Bonus Points:
- Use Jenkins, pointing git on config and build stage :
- Deploy my simple nodejs docker orchestration Kubernetes on eks aws
    create directory kubernetes
    create namespaces : create ns nodejs
    create deployment app : apply -f deployment.yaml -n nodejs
    create service app : appy -f node-app-service.yaml -n nodejs
    testing using port forward: kubectl port-forward service/node-app-service 5000:5000 -n nodejs
    and test on chrome using url:port
- Deploy ingress and using tls ssl
create ingress and pointing to service use tls ssl