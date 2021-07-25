# E-Commerce Search Sample
A step-by-step guide to build a sample e-commerce product catalog search functionality using,
* Elasticsearch & Elastic App Search
* ReactJS

This sample end-to-end e-commerce solution with focus on 'Search' features such as,
1. Auto completion vs Auto Suggestions
1. Guided search
1. Fuzzy search
1. Entity tagging
1. Faceted search
1. Relevance
    1. Synonyms
1. Ranking

## Part 1 - Software Installation
This sample follows Cloud-Native Architecture with following software,
1. Kubernetes (Minikube) for running ElasticSearch & Elastic App Serch
1. Helm - Package manager for Kubernetes
1. NodeJS
1. Brew for MacOS

### Install & Configure Minikube
On macOS,
```sh
brew install minikube
```
Use 'hyperkit' as virtualization for MacOS,
```sh
minikube config set driver hyperkit
```
on Windows,
TODO

Minikube configurations
```sh
minikube config set cpus 4
minikube config set memory 10240
```

### Setup Kubernentes enviornment
Follow below instructions to setup Minikube on your machine (Windows/Mac),
```sh
brew install helm
```

### Setup Elastic Cloud for Kubernetes (ECK) and Elastic Stack
Installing ECK using helm chart
```sh
helm repo add elastic https://helm.elastic.co
helm repo update
```
#### Install ECK
These instructions are from, https://www.elastic.co/guide/en/cloud-on-k8s/current/k8s-quickstart.html
Any issues refer to Elasticsearch site for more details.
```sh
helm install elastic-operator elastic/eck-operator -n elastic-system --create-namespace
```
Check ECK monitor operator logs,
```sh
kubectl -n elastic-system logs -f statefulset.apps/elastic-operator
```
#### Install ElasticSearch
The K8s manifest file is created with instructions from,
https://www.elastic.co/guide/en/cloud-on-k8s/current/k8s-deploy-elasticsearch.html
```sh
kubectl apply -f elasticsearch.yaml
```
##### Instructions to verify Elasticseach installation,
```sh
kubectl logs -f quickstart-es-default-0
```
Get the credentials. A default user named 'elastic' is automatically created with the password stored in a Kubernetes secret:
```sh
PASSWORD=$(kubectl get secret quickstart-es-elastic-user -o go-template='{{.data.elastic | base64decode}}')
```
From your local workstation, use the following command in a separate terminal,
```sh
kubectl port-forward service/quickstart-es-http 9200
```
Then verify Elasticsearch from local machine,
```sh
curl -u "elastic:$PASSWORD" -k "https://localhost:9200"
```
#### Install Elastic App Search
The K8s manifest is prepared from,
https://www.elastic.co/guide/en/cloud-on-k8s/current/k8s-enterprise-search-quickstart.html
Install Elasitc App Search
```sh
kubectl apply -f enterprisesearch.yaml
```
Any issues refer to above documenation.
#### Access Elastic App Search
```sh
kubectl port-forward service/enterprise-search-quickstart-ent-http 3002
```
Open https://localhost:3002 in your browser.
Login as the 'elastic' user created with the Elasticsearch cluster. Its password can be obtained with:
```sh
kubectl get secret quickstart-es-elastic-user -o=jsonpath='{.data.elastic}' | base64 --decode; echo
```
### Install Node
Node 16 has issues with search-ui, use Node 14

## Configure Elastic App Search
### Create Search Engine
https://github.com/elastic/search-ui

### Build & Run E-Commerce Search Sample
Modify e-commerce-search-ui/src/config/engines.json file, update following information,
1. ?
1. ?

```sh
cd e-commerce-search-ui
npm install
npm run
```
