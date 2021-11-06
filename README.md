# k8s with MongoDB Database

## 1. Goal:

The goal for this assignment is to deploy an application locally (*local computer is the host*) using **kubernetes**. <br>
The application has a database. The user will interact with the front-end in order to input or read data stored in the database.<br>
The **database** is set up so that the front-end authenticate before accessing the back-end (wich is the database in this case).

## 2. Architecture:

## 3. Software tools used:

* [kubernetes](https://kubernetes.io/)

We avoid using a cloud provider for the deployment for cost purposes.<br>
This is not used in a production environment.

## 4. Precedure:

1. Create a cluster with a loadbalancer with port mapping “8080:8081”
```
k3d cluster create mycluster -p "8080:8081@loadbalancer"
```
		* port `8080` is for the access to the front-end.
		* port `8081` is for the access to the application
		* port `27017` is the port open in order to access the database
		
	2. Encode the username and password
	
		echo -n mongo-root-username | base64

			output: bW9uZ28tcm9vdC11c2VybmFtZQ==

		echo -n mongo-root-password | base64
		
			output: bW9uZ28tcm9vdC1wYXNzd29yZA==

		Create a secret.yaml file for the credentials
		Then, run
		
			$ kubectl apply -f secret.yaml
			

# Source:

* This lab was from [Kura Labs](https://github.com/ibrahima1289/k8s-mongoDB/blob/main/K8s%20and%20MongoDB%20assignment.pdf).
