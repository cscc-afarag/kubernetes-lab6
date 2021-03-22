# kubernetes-lab3

In this lab you are first tasked with creating a running [WordPress][wordpress] application.


The WordPress application we are going to deploy has two major parts: A MySQL database that will be used to store persistent data and the actual WordPress container.

For this lab you should have multiple (6) manifest files that fulfill the below requirements.

### *Tips*
- Use the previous examples and online resources
- You will need make use of labels and selectors
- Some components might have to be created before you can create ones that reference it.
- The requirments are not in order.

---
### Secret
- For the mysql database password, create an opaque `Secret` for the database to use.
---
### Stateful MySQL Database and Service

#### Database
- For the actual database we want a `StatefulSet`
- Use *1* replica
- use the image `mysql:5.6`
- Should have a volume mount using volume claim
- 'standard' storage class with 'ReadWriteOnce' access

#### Service
- Create a `Service` for the database
- Should exposed only to the wordpress instance
  
*tips*
- We do not need the PVC to be created ahead of time for its storage. Use the volumeClaimTemplates feature of the StatefulSet
---
### WordPress PVC

- For the wordpress to be able to write data it needs a PVC.
- Create a PVC with a 'ReadWriteMany' access and requested storage
---
### Wordpress Deployment and Service
#### Deployment
- Here we want the actual wordpress instance as a `Deployment`
- *2* replicas using the `wordpress:4.9-apache` image
  
#### Service
- Expose our wordpress instance using a `NodePort`

*tips*
- when everything is running use the `minikube service` command to access the deployment.

---
### **When done** 
- clearly name each of the **6** manifest files and zip them into a zip called `wordpress.zip`

---

[wordpress]: https://wordpress.org/
