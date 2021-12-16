# DigitalOcean Kubernetes Challenge

From the challenges present I choose to Deploy an internal container registry.

## Deploy an internal container registry
Kubernetes does not provide an internal container registry but it is often useful to add one. There are many projects which enable you to deploy an internal container registry, such as Harbour or Trow. 

## Creating/Connecting a Managed k8s cluster

1. Click on Create
  ![image](https://user-images.githubusercontent.com/67012359/146408092-0b26dcd4-060c-4276-8810-6d5e3f9e7ed6.png)
2. Choose Kubernetes from the drop down 
  ![image](https://user-images.githubusercontent.com/67012359/146408456-0175f628-5994-4889-a99e-32c25ac1ca8c.png)
3. Fill in the menu and wait for cluster creation
  ![image](https://user-images.githubusercontent.com/67012359/146408603-c47d683f-e767-41b8-884e-47340ca25876.png)
4. Install doctl from the following [link](https://docs.digitalocean.com/reference/doctl/how-to/install/)
5. Use Certificates from the Authentication for connection to the cluster. 
  ![image](https://user-images.githubusercontent.com/67012359/146408986-c8c71c0d-624c-4034-aeff-d45ddda4e51b.png)
6. Make sure you have kubectl installed. If not, try running these commands on a linux VM:
```bash
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl
rm kubectl
```
7. Try running `kubectl get nodes` to see the number of nodes. Eg: 
  ![image](https://user-images.githubusercontent.com/67012359/146409442-af33e8dd-b828-4ce4-93ca-2edd1ed5a1a0.png)

## Challenge 

### Helm Installation 

Helm helps you manage Kubernetes applications — Helm Charts help you define, install, and upgrade even the most complex Kubernetes application. We would install harbor using helm but first let's install Helm.

```bash
curl https://raw.githubusercontent.com/helm/helm/master/scripts/get-helm-3 | bash
```

### Helm Repository (Bitnami)
 A chart repository is an HTTP server that houses an index.yaml file and optionally some packaged charts. We would use Bitnami for the following.
```bash
helm repo add bitnami https://charts.bitnami.com/bitnami
```
![image](https://user-images.githubusercontent.com/67012359/146411694-4d26645e-bf92-4b40-8533-3a111a56bd21.png)

### Helm Edit Values

Before installing helm chart we need to edit the yaml file, so create a yaml file 
```
helm show values bitnami/harbor > harbor-values.yaml
```
![image](https://user-images.githubusercontent.com/67012359/146412067-567f57f9-a59b-41da-9d49-608fe5e3c26d.png)


open `harbor-values.yaml` in a editor and set admin password `harborAdminPassword: "<YOUR PASSWORD>"`

### Helm Install Chart
Installing the chart using the new yaml we have created in the repository by `helm install harbor bitnami/harbor --values harbor-values.yaml -n harbor --create-namespace`
![image](https://user-images.githubusercontent.com/67012359/146412850-6e5afc44-71d9-4897-92b0-0241f2e667d4.png)

Make Sure Pods are running using the command `kubectl get all -nharbor`


### Visit the Portal to get the Load Balancer IP
![image](https://user-images.githubusercontent.com/67012359/146413691-f031fc10-c828-4ff7-ac1a-e58d6dbe292b.png)


