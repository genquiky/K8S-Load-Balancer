
# KUBERNETES Part xx: Load Balancer

In this part I have created a `deployment` with 3 replicas, exposing the `pods` to the internet through the `service` object and demonstrating how the load balancer adistributes traffic to each `endpoint`.


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


<b>1.4 In this step I have listed the `deploy`, `pods`, `service` and `endpoints` IP's with the label `gen-deploy`</b>
<a id="1-1"></a> <br>
Assigned endpoints IPs:<br>
10.244.0.4:80 <br>
10.244.1.10:80 <br>
10.244.1.9:80 <br>


<img width="872" height="auto" alt="image" src="https://github.com/genquiky/K8S-Load-Balancer/blob/main/images/06.png" />

   ```bash
   kubectl get deploy,po,svc,ep -l app=gen-deploy --show-labels
   ```


<b>1.5 Checking the IP assigned for the `service` exposed to the internet, from the cluster using `minikube`. This is an unique external IP access to the `endpoints`</b>
<a id="1-1"></a>

<img width="600" height="auto" alt="image" src="https://github.com/genquiky/K8S-Load-Balancer/blob/main/images/07.png" />

```bash
   minikube service gen-deploy
   ```

<b>1.6 Accessing to the service in the cluster using the URL assigned by Kubernetes from the outside.</b>
<a id="1-1"></a>
Here we can confirm that we can access to the `pods` and confirming the use of the `load balancer` for each `replica`

<img width="872" height="auto" alt="image" src="https://github.com/genquiky/K8S-Load-Balancer/blob/main/images/08.png" />

```bash
   minikube service gen-deploy
   ```
