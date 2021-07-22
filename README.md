# e-commerce-search-sample
A step-by-step guide to build a sample e-commerce product catalog SEARCH functionality using Elasticsearch &amp; ReactJS

You will build working end-to-end e-commerce solution with more focus on 'Search' features such as auto-completion, guided search, fuzzy search, entity tagging, faceted search and more.  
## Part 1 - Setup software on local machine

### Setup Kubernentes enviornment
Follow below instructions to setup Minikube on your machine (Windows/Mac),


### Setup Elastic Cloud for Kubernetes (ECK) and Elastic Stack

Install custom resource definitions and the operator with its RBAC rules:
kubectl apply -f https://download.elastic.co/downloads/eck/1.6.0/all-in-one.yaml

Monitor the operator logs
kubectl -n elastic-system logs -f statefulset.apps/elastic-operator

kubectl apply -f elasticsearch.yaml

More details refer to, https://www.elastic.co/guide/en/cloud-on-k8s/current/k8s-deploy-eck.html


