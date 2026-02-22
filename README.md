
# KUBERNETES Part II: Service and Load Balancer

In this practical exercise I have created a `deployment` with 3 replicas, exposing the `pods` to the internet through the `service` object and demonstrating how the `load balancer` distributes traffic to each `endpoint`.


Steps:

<b>1.1 Creating a deployment `gen-deploy` with 3 replicas and adding the text `hello from:deploy` in the image:</b>
<a id="1-1"></a>


<img width="872" height="auto" alt="image" src="https://github.com/genquiky/K8S-Load-Balancer/blob/main/images/01.png" />

  ```bash
   kubectl create deployment gen-deploy --image=pbitty/hello-from:latest --port=80 --replicas=3
   ```
<br>
<br>

<b>1.2 Checking the `deployment` and the replicated `pods` created:</b>
<a id="1-1"></a>

<img width="872" height="auto" alt="image" src="https://github.com/genquiky/K8S-Load-Balancer/blob/main/images/02.png" />

   ```bash
   kubectl get deploy,po --show-labels
   ```
<br>
<br>

<b>1.3 Exposing the `service` object with the `type=NodePort` to be accessible from the external world:</b>
<a id="1-1"></a>


<img width="872" height="auto" alt="image" src="https://github.com/genquiky/K8S-Load-Balancer/blob/main/images/03.png" />

   ```bash
   kubectl expose deployment gen-deploy --type=NodePort
   ```

<br>
<br>

<b>1.4 Listing the `deploy`, `pods`, `service` and `endpoints` IPs with the label `gen-deploy`:</b>

Assigned endpoints IPs:<br>
10.244.0.4:80<br>
10.244.1.10:80<br>
10.244.1.9:80
<br>
<br>

<img width="872" height="auto" alt="image" src="https://github.com/genquiky/K8S-Load-Balancer/blob/main/images/06.png" />

   ```bash
   kubectl get deploy,po,svc,ep -l app=gen-deploy --show-labels
   ```

<br>
<br>

<b>1.5 Checking the IP assigned to the `service` exposed to the internet, from the cluster using `minikube`.</b> 
<br>This is a unique external IP access to the application `192.168.49.2:31747`

<img width="600" height="auto" alt="image" src="https://github.com/genquiky/K8S-Load-Balancer/blob/main/images/07.png" />

```bash
   minikube service gen-deploy
   ```
<br>
<br>

<b>1.6 Accessing the service in the cluster using the URL assigned by Kubernetes from the outside:</b>
<br>Here I can confirm access to the application and that the `load balancer` distributes traffic to each `replicas`.

<img width="872" height="auto" alt="image" src="https://github.com/genquiky/K8S-Load-Balancer/blob/main/images/08.png" />

```bash
   minikube ssh
   curl http:192.168.49.2:31747
   ```
<br>

`Hello from gen-deploy`<br>
`Hello from gen-deploy`<br>
`Hello from gen-deploy`<br>
