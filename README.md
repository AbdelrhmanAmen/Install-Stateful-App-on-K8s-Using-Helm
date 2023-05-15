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
2) Deploy Mongo DB StatefulSet
3) Deploy MongoExpress
4) Deploy Ingress
