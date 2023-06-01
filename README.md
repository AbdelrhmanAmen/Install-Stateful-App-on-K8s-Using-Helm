# Install-Stateful-App-on-K8s-Using-Helm

## What to Achieve 
- Deploy a managed k8s cluster on Linode (Akamai).

<p align="center">
  <img src="https://github.com/AbdelrhmanAmen/Install-Stateful-App-on-K8s-Using-Helm/assets/73068684/228305d2-34e9-4d48-9f12-c3e4348ee526"height="250"/>
</p>

- Deploy a replicated database and configure its persistent volumes.
- Make the database accessible through a UI client from browser using ingress.

<p align="center">
  <img src="https://github.com/AbdelrhmanAmen/Install-Stateful-App-on-K8s-Using-Helm/assets/73068684/809017c0-69cd-4ac3-a634-1a4f9c623f97"/>
</p>

## Steps
1) Create the cluster

- Choose cluster `name`, `region`, `kubernetes version` and `number of nodes`.
<div align=center>
<img src="https://github.com/AbdelrhmanAmen/Install-Stateful-App-on-K8s-Using-Helm/assets/73068684/afe4b394-e407-4992-aaaa-69d0958f5e76"/>
 </div>

- To connect to the cluster and use **kubectl commands** download the kubeconfig.yaml file and set this environment variable: `export KUBECONFIG=<path-to-yaml-file>`.
 
   1- <div align=center>
    <img src="https://github.com/AbdelrhmanAmen/Install-Stateful-App-on-K8s-Using-Helm/assets/73068684/cd43ac04-9dee-4a04-a5a1-2f628587aef5"/>
     </div>

    2- <div align=center >
    <img src="https://github.com/AbdelrhmanAmen/Install-Stateful-App-on-K8s-Using-Helm/assets/73068684/f0103b5c-ed87-4ef5-af35-f03f4284cbbb"/>
     </div>

2) Deploy Mongo DB StatefulSet
  > Use a [MongoDB](https://github.com/bitnami/charts/tree/main/bitnami/mongodb) Helm chart which is a bundle of configuration files templates.
  > check the MongoDB chart parameters and specify what you need.
  > after that to use the helm char with your values.yaml, run this command `helm intall [your-release-name] --values <path-to-yaml-file> [chart-name]`.
  Note in the output the creation of headless services like this:
  
 <div align=center >
    <img src="https://github.com/AbdelrhmanAmen/Install-Stateful-App-on-K8s-Using-Helm/assets/73068684/532d0238-f734-49f5-819f-9b6c8a9beb4f"/>
  </div>
     
3) Deploy MongoExpress

create a deployment yaml file specify the number of replicas and the environment variables
    
4) Deploy Ingress

using helm again run the following command, no need for any configuration
  ```
      helm repo add ingress-nginx https://kubernetes.github.io/ingress-nginx
      helm repo update
      helm install [RELEASE_NAME] ingress-nginx/ingress-nginx
  ```
