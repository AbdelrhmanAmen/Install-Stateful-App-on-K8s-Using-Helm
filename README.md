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

- To connect to the cluster and use **kubectl commands** download the development-kubeconfig.yaml file and set this environment variable: `export KUBECONFIG=development-kubeconfig.yaml`
<div align=center>
<img src="https://github.com/AbdelrhmanAmen/Install-Stateful-App-on-K8s-Using-Helm/assets/73068684/cd43ac04-9dee-4a04-a5a1-2f628587aef5"/>
 </div>



2) Deploy Mongo DB StatefulSet

3) Deploy MongoExpress

4) Deploy Ingress
