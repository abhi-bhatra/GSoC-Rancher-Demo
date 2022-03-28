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
---

#### Setup Rancher on existing cluster

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
  <li>Check for Rancher Container is up and Running</li>
  
  ![Screenshot from 2022-03-28 07-57-12](https://user-images.githubusercontent.com/63901956/160316208-469459e9-a49f-4ff4-956a-67304874f380.png)
  
  <li>Run the Web UI of the Rancher: `http://localhost`</li>
  <li>UI will open: <li>
  
  ![Screenshot from 2022-03-22 14-21-27](https://user-images.githubusercontent.com/63901956/160294831-fb11b5b2-8214-4bdc-b403-c2394370ec79.png)
  
  Run the command: `kubectl get secret --namespace cattle-system bootstrap-secret -o -go-template='{{.data.bootstrapPassword | base64decode}}{{"\n"}}'`
  
  <li>Create new passwords for Rancher</li>
  <li>Now on this tab we can create our new cluster or can import an existing one</li>
  <li>Import your cluster</li>
  
  ![Screenshot from 2022-03-28 08-02-33](https://user-images.githubusercontent.com/63901956/160316637-e1deb81d-34a1-46ef-8a54-cc4eb4a032fc.png)
  
  <li>Once created, Run the kubectl command below on an existing Kubernetes cluster running a supported Kubernetes version to import it into Rancher: </li>
 
  ![Screenshot from 2022-03-28 08-10-13](https://user-images.githubusercontent.com/63901956/160317354-1765eae4-a5d7-4751-9ffc-ed97c15a6b45.png)
 
  </ul>
  
#### Set-Up the k8s cluster on Azure AKS

1. Ensure that you have k8s tools installed, visit here for more details: https://kubernetes.io/docs/tasks/tools/ 

2. Once you created Azure AKS cluster, click on `connect`and copy the commands into your system
![Screenshot from 2022-03-28 08-17-32](https://user-images.githubusercontent.com/63901956/160318071-c6f744a0-5451-4ec1-8eb6-1604722903aa.png)


3. Create a namespace `kubectl create namespace <namespace>`
4. If the docker images are stored in private registries, then create docker certificates, regcred secrets, for pulling images from private registries.
5. Apply yaml files: 
<ul>
  <li>configmap</li>
  <li>secrets</li>
  <li>pvc</li>
  <li>deployment</li>
  <li>service</li>
</ul>

6. Sample deployment files for the protocols:
 <ul>
  <li>Ethereum Frontend: https://github.com/abhi-bhatra/GSoC-Rancher-Demo/tree/master/eth-frontend</li>
  <li>Ethereum Backend: https://github.com/abhi-bhatra/GSoC-Rancher-Demo/tree/master/eth-backend</li>
  <li>Databases: https://github.com/abhi-bhatra/GSoC-Rancher-Demo/tree/master/database</li>
</ul>

**Note: Plan to deploy some more protocols together and manage all the protocols using Rancher Dashboard**
