
# DigitalOcean Kubernetes Challenge 2021


## Deploy MongoDB Cluster on Kubernetes (NO SQL)


## What are Kubernetes?
Kubernetes is a portable, extensible, open-source platform for managing containerized workloads and services, that facilitates both declarative configuration and automation.


## Depolyment Guide

### Prerequisites
- [Git installation guide](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
- [kubectl installation guide](https://kubernetes.io/docs/tasks/tools/install-kubectl/)
- [doctl installation guide](https://docs.digitalocean.com/reference/doctl/how-to/install/#step-1-install-doctl)
- [DigitalOcean account](https://www.digitalocean.com/)

### Step 1: Create a Kubernetes cluster
Digital ocean makes it easier to create Kubernetes clusters.
- Head to [DigitalOcean](https://www.digitalocean.com/) and click on the **Kubernetes** button in **Create** dropdown button on the top right.
- Choose and fill in the following fields (side note: you can leave the fields unchanged for the challenge):
    - **Region**: Choose the region where you want to create your cluster.
    - **Name**: Choose a name for your cluster.
    - **Version**: Choose the version of Kubernetes you want to use.
    - **Node Pool**: Choose the node pool you want to use.
    side note: you can leave the fields as they are.
- Click on **Create** button.
- Wait until the cluster is created.

<img width="1440" alt="Screenshot 2022-01-07 at 10 12 51 PM" src="https://user-images.githubusercontent.com/73380583/148593696-5fa853e4-5f8a-4d75-8c8e-9c483a378f22.png">

### Step 2: Connect to the cluster
- In the **Overview** tab, **Getting Started** section will have the required information.
- Go to second tab **Connecting to kubernetes** and copy the command to configure the cluster certificate/kubeconfig which looks something like `doctl kubernetes cluster kubeconfig`.
- Run the command in the terminal.

<img width="1440" alt="Screenshot 2021-12-30 at 11 11 42 PM" src="https://user-images.githubusercontent.com/73380583/148593976-24285847-af68-470f-9b7a-5a87cded5be6.png">

### Step 3: Deploy MongoDB Cluster
- Clone this [MongoDB Kubernetes Challenge Repo](https://github.com/csfx-py/DOproject) using `git clone https://github.com/csfx-py/DOproject.git`.
- Go to the repo directory
- Optional step: change the mongodb credentials:
    - Open **mongodb-secrets.yaml** file
    - Change the username and password with base64 encoded values.
    - Save the file.
- Run `kubectl apply -f .` to deploy the MongoDB cluster.
- Wait until the deployment is complete.
- Run `kubectl get all` to check the status of the deployment.

<img width="1440" alt="Screenshot 2021-12-30 at 11 10 01 PM" src="https://user-images.githubusercontent.com/73380583/148594160-b621c218-166c-424f-8c9d-157cf5a71bcb.png">


### Step 4: Verify the deployment
- Run `kubectl exec deployment/mongo-client -it -- /bin/bash` to connect to the MongoDB cluster.
- The prompt should change to *root@mongo-client-xxx*
    - Run `mongo --host mongo-nodeport-svc --port 27017 -u <username> -p <password>` where *username* and *password* are the values you entered in **mongodb-secrets.yaml** file.
    - You should see the mongoDB info and prompt for mongo commands.

<img width="1440" alt="Screenshot 2021-12-30 at 11 10 04 PM" src="https://user-images.githubusercontent.com/73380583/148593794-cb6b2ef2-9647-4ee8-9d55-cc89435ea616.png">


### Step 5: Its over , Completed
Congratulations! You have successfully deployed a MongoDB cluster on Kubernetes.

