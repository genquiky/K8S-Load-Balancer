
# KUBERNETES Part xx: Load Balancer

In this part I have created a `deployment` with 3 replicas, exposing the `pods` to the internet through the `service` object and demonstrating how the load balancer applies traffic to each `endpoint`.

Glossary:

[1. Creating a local cluster with 1 node (Control Plane)](#one)
>[1.1 Installing Docker Desktop for mac](#1-1)<br>
>[1.2 Installing Minikube](#1-2)<br>
>[1.3 Run Minikube](#1-3)<br>
>[1.4 Checking the status](#1-4)<br>
>[1.5 Checking the cluster](#1-5)<br>
>[1.6 Stopping the cluster](#1-6)<br>

[2. Creating a new cluster with 2 nodes](#two)
>[2.1 Adding a new cluster](#2-1)<br>
>[2.2 Checking the new cluster](#2-2)<br>
>[2.3 Decommissioning the cluster](#2-3)<br>

[3. GUI monitoring dashboards](#three)
>[2.1 Adding a new cluster](#3-1)<br>
>[2.2 Checking the new cluster](#3-2)<br>



Steps:

<b>1.1 Creating a deployment `gen-deploy` with 3 replicas and adding the text `hello from:deploy` in the image</b>
<a id="1-1"></a>



<img width="872" height="auto" alt="image" src="https://github.com/genquiky/K8S-Load-Balancer/blob/main/images/01.png" />

  ```bash
   kubectl create deployment gen-deploy --image=pbitty/hello-from:latest --port=80 --replicas=3
   ```









<b>1.2 Checking the deployment and the pods created</b>
<a id="1-1"></a>




<img width="872" height="auto" alt="image" src="https://github.com/genquiky/K8S-Load-Balancer/blob/main/images/02.png" />

   ```bash
   kubectl get deploy,po --show-labels
   ```

<b>1.3 I have exposed the `service` object with the `type=NodePort` to be accessible from the external world</b>
<a id="1-1"></a>




<img width="872" height="auto" alt="image" src="https://github.com/genquiky/K8S-Load-Balancer/blob/main/images/03.png" />

   ```bash
   kubectl expose deployment gen-deploy --type=NodePort
   ```




<b>1.3 Installing Docker Desktop for mac</b>
<a id="1-1"></a>


<img width="872" height="auto" alt="image" src="https://github.com/genquiky/K8S-Load-Balancer/blob/main/images/06.png" />

<br>
<br>
<br>
<br>



Steps:

<b>1.1 Installing Docker Desktop for mac</b>
<a id="1-1"></a>


<img width="600" height="auto" alt="image" src="https://github.com/genquiky/K8S-Load-Balancer/blob/main/images/07.png" />

<br>
<br>
<br>
<br>





Steps:

<b>1.1 Installing Docker Desktop for mac</b>
<a id="1-1"></a>


<img width="872" height="auto" alt="image" src="https://github.com/genquiky/K8S-Load-Balancer/blob/main/images/08.png" />

<br>
<br>
<br>
<br>
