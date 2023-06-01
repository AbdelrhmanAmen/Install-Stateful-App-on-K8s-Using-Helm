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

create a deployment yaml file specify the number of replicas and the environment variables.
Then run `kubectl apply -f <deployment-file>` 
    
4) Deploy Ingress

using helm again run the following command, no need for any configuration
 
 ```
      helm repo add ingress-nginx https://kubernetes.github.io/ingress-nginx
      helm repo update
      helm install [RELEASE_NAME] ingress-nginx/ingress-nginx
  ```
  
 ## Final Result
  
   <div align=center >
    <img src="https://github.com/AbdelrhmanAmen/Install-Stateful-App-on-K8s-Using-Helm/assets/73068684/6f007760-552a-4196-b107-818864b98020"/>
  </div>
     
   - Node balancer has been created after running the previous commands

 <div align=center >
    <img src="https://github.com/AbdelrhmanAmen/Install-Stateful-App-on-K8s-Using-Helm/assets/73068684/eab74e4d-9bab-4f8e-8d5a-3ca25867d63b"/>
  </div>
    
   - Now we can define ingress rules (ingress.yaml) and run `kubectl apply -f <ingress-file>` 
   - we will use the hostname of the Node balancer as the host in the ingress rule
   
 ## Test
  1)
  <div align=center >
    <img src="https://github.com/AbdelrhmanAmen/Install-Stateful-App-on-K8s-Using-Helm/assets/73068684/69603e37-1753-4802-947b-8df6c6147f2f"/>
  </div>
  2)
  <div align=center >
    <img src="https://github.com/AbdelrhmanAmen/Install-Stateful-App-on-K8s-Using-Helm/assets/73068684/b58cf74a-1a1b-4545-8703-fdf270616284"/>
  </div>
  3)
  <div align=center >
    <img src="https://github.com/AbdelrhmanAmen/Install-Stateful-App-on-K8s-Using-Helm/assets/73068684/4534dfbb-3a27-4d8f-9eb0-c94d6ef6399b"/>
  </div>

  
   
