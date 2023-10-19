## Consulting mission for Kent AB
This repository contains the base solution for Kent AB, describing the problems and how they are solved or how we will move to solve them

### Problems:
This is what I took away as your main problems and the reson conntacting us at CK AB.

1. High load on servers in peek hours
2. Downtime to single point of failiure
3. Slow development process for internal developers 
4. Failiures are common when changes are deployed

### Our Solutions:
This section covers what our prof of concept covers and what we can exand upon marked with (*parentecies and italic*)

1. With the prof of consept  kubernetes cluster the servers can be scaled to multiple instances to handle desiered load. *(We can include auto scalers to make the system scale up in peak hours and down when no one is using it)*
   
2. Downtime becuse of failiure of a single instance is handeled with this PoC. It is still suseptive to powero outages, like the one Kent AB experienced when the electricity went out in the server room. *(This can be solved whith this solution being deployed to the cloud or to multiple servers in diffrent places)*

3. A slow development process is addressed with this PoC becuse now developers can push changes to the git repository or directly to docker hub and from there the images will be deployed. They can either try the docker bilds themselfs localy through docker or minikube and iterate faster. *(For the future we want in inplement GitOps principles for this project where the whole deployment process is handled by ArgoCD and GitHub Actions where your git repository represents the actual state of the application)*

4. Failiures will be removed by the PoC by doing rolling updates where if a deployment does not work it crash and the stabel deployment will still be there serving customers. *(How to detect if an application is broken or not is an extensive task that requires testing that we can look into if intrested)*

### Tasks

These tasks where assined to me to create a PoC for your new server setup. 

- [x] Create a Kubernetes cluster (Minikube)

- [x] Containerize the application using Docker (https://www.docker.com/)

- [x] Push the container image to a Container Registry (https://hub.docker.com/repository/docker/frallan97/node-hostname)

- [x] Run the application inside your Kubernetes cluster. The application should be accessible from a browser.

### Extra tasks:
- [ ] Expose the application via https (and not http)

- [x] Make a trivial change to the application and do a rolling update 

- [x] Helm-ify the deployment 

---

## Run it yourself

#### Prerequisites:
This setup works on Linux, Mac and Windows 
1. Minikube (instalation link: https://minikube.sigs.k8s.io/docs/start/)
2. Helm (instalation link: https://helm.sh/docs/intro/quickstart/)
3. Docker (instalation link: https://docs.docker.com/engine/install/)
4. Dockerhub acount: (link: https://hub.docker.com/)
5. Git (instalation link: https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)


### Setup
This will only go through the linux setup (windows and mac are comming soon). This works on windows subsystem for linux(wsl).
1. Clone git repository: `git clone https://github.com/Frallan97/elastisys-test.git`
2. Start up minikube: `minikube start`
3. Run helm install: `helm install node-hostname node-hostname-helm`
4. Get ip to minikube node: `minikube ip`
5. Go to your browser and typ insert the minikube-ip followed by 31018 like this `https://<MINIKUBE-IP>:31018` 
