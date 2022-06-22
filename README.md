TEAM MEMBERS: David Delgadeo, Charles Harris, Brian Cunningham, Ari Ochoa

* Java
* Maven
* Spring Boot
* Spring Data
* PostgreSQL
* Log4J
* Loki
* Grafana
* AWS RDS
* Docker
* Kubernetes

SLO
* Cluster memory remains above 20% free
* http request duration under .05 ms
* 50% or more requests under .2 ms


Kubernetes Cluster
* packages to install - helm, prometheus, grafana
Step 1: Install Postgres stack in kubernetes using helm
    -helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
    -helm repo update
    -helm install [RELEASE_NAME] prometheus-community/kube-prometheus-stack

Step 2: Kubectl edit postgres-service and make it LoadBalancer.

Step 3: Check postgres-service ClusterIP and copy and paste that into the application.properties of project 1 and upload the changes to dockerhub.

Step 4: Apply the project.yml in Kubernetes and also make project-service LoadBalancer.

Step 5: Install Prometheus and Grafana via Helm.

Step 6: Edit Prometheus-server, prometheus-alertmanager, and Grafana services into LoadBalancer.

Step 7: Use kubectl edit configmap prometheus-server and add custom targets in the "prometheus.yml: |" section. *To connect your custom metrics in your project, make sure the targets in the static_configs: is [minikube-ip]:[Port].

Step 8: Add custom rules in the alert-rules | section of the configmap

Step 9: Apply p1.yaml and p1service.yaml to create a deployment and LoadBalancer service

Step 10: Open terminal window and enter following command to port forward the app.
    -kubectl port-forward <YOUR POD RUNNING> 80:8004

Step 11: Check that deployment and service are running, if they are you can access the landing page of the app
in a browser using the external IP listed for your LoadBalancer, followed by/user/home or /item/home.  
The app is connected to a RDS database, but DO NOT ATTEMPT TO POST DATA to avoid billable charges.