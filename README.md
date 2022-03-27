![rancher-logo-horiz-color](https://user-images.githubusercontent.com/63901956/160286983-ecb37c4d-d870-41a5-84b5-351e3d9c6bf8.svg)

# GSoC-Rancher-Demo
Let's see how Rancher helps in easy management of Blockchain Protocols

### Let's Get Started
---
1. **Introduction to Rancher** <br />
Rancher is an open-source software which offeres **Kubernetes-as-a-Service**. It is used to provision and manage Kubernetes clusters. You can import existing clusters, either custom or managed clusters like EKS and GKE, or define and deploy your own with RKE or K3s.

2. **Introduction to Blockchain** <br />

![blockchain-technology-overview](https://user-images.githubusercontent.com/63901956/160287365-df73e448-63de-42f4-b44b-dbb918cbd22f.jpeg)

Blockchain technology is most simply defined as a decentralized, distributed ledger that records the provenance of a digital asset. By inherent design, the data on a blockchain is unable to be modified, which makes it a legitimate disruptor for industries like payments, cybersecurity and healthcare.

2.1. **Blockchain Protocol Development** <br />
Before we start, remember that blockchain is an immutable chain of records called ‘blocks’ that contains:
<ul>
  <li>transactions</li>
  <li>data</li>
  <li>files</li>
</ul>

Blocks are chained together with hashes. Developing a blockchain from scratch and its implementation can take months or years to complete because it requires thorough research. It takes a lot of consideration and time to discover and implement an idea successfully.

3. We will try to provision multiple blockchain protocols on Kubernetes clusters and then integrate the Rancher to the cluster to provision and manage the complex blockchain infrastructure.

### How-to Guide

1. Store the docker images in the private or public Docker registries.
2. Create a cluster in Azure AKS
<img width="960" alt="cluster" src="https://user-images.githubusercontent.com/63901956/160291584-09617068-112d-41d2-bf4c-dffbe2f7412a.png">

Steps to create AKS Cluster: https://docs.microsoft.com/en-us/azure/aks/kubernetes-walkthrough-portal

3. Create a Virtual Machine, or You can also run Rancher in your local machine:
<ul>
  <li>Install Docker on your system: https://docs.docker.com/engine/install/</li>
  <li>Install Rancher, visit: https://rancher.com/quick-start</li>
</ul>

Or use:
```shell
sudo docker run --privileged -d --restart=unless-stopped -p 80:80 -p 443:443 rancher/rancher
```
<ul>
  <li>Run the Web UI of the Rancher: `http://localhost`</li>
