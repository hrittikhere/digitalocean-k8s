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
6. Make sure you have kubectl installed.
7. Try running `kubectl get nodes` to see the number of nodes. Eg: 
  ![image](https://user-images.githubusercontent.com/67012359/146409442-af33e8dd-b828-4ce4-93ca-2edd1ed5a1a0.png)
