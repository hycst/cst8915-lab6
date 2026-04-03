## CST8915 Lab 6 – Deploy Algonquin Pet Store to AKS ( Azure Kubernetes Service (AKS) Deployment)



---

##  Objective

The objective of this lab is to deploy a microservices-based application (Algonquin Pet Store) to **Azure Kubernetes Service (AKS)** using Kubernetes YAML configuration files and verify that all services are running and accessible.

---

##  Technologies Used

* Azure Kubernetes Service (AKS)
* Azure CLI
* kubectl
* Docker containers
* Kubernetes (Deployment & Service)
* RabbitMQ

---

##  Deployment Steps

### 1. Connect to AKS

```bash
az login
az account set --subscription <subscription-id>
az aks get-credentials --resource-group AlgonquinPetStoreRG --name AlgonquinPetStoreCluster
```

### 2. Deploy Application

```bash
kubectl apply -f algonquin-pet-store-all-in-one.yaml
```

### 3. Verify Deployment

```bash
kubectl get pods
kubectl get services
```

---

##  Results

* All pods are running successfully:

  * order-service
  * product-service
  * store-front
  * rabbitmq

* Application is accessible via external IP:

```
http://<EXTERNAL-IP>
```

---

##  Application Endpoints

| Service            | URL         |
| ------------------ | ----------- |
| Store Front        | `/`         |
| Products           | `/products` |
| Orders             | `/orders`   |
| RabbitMQ Dashboard | `/rabbitmq` |

---

##  Demo Video

Watch the demonstration video here:
 https://youtu.be/yqGH3Kkut8Q

---

##  Cleanup

To avoid extra Azure charges:

```bash
kubectl delete -f algonquin-pet-store-all-in-one.yaml
```

Also delete:

* Resource Group: AlgonquinPetStoreRG
* Related Azure resources

---

##  Conclusion

This lab demonstrated how to:

* Deploy a multi-service application to AKS
* Use kubectl to manage Kubernetes resources
* Expose services via LoadBalancer
* Access and test cloud-based microservices

---

##  Notes

* Azure subscription issues were resolved by selecting the correct tenant and enabling MFA login.
* Proper subscription selection is critical for accessing AKS resources.

---
