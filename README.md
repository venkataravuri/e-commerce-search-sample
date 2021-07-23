# e-commerce-search-sample
A step-by-step guide to build a sample e-commerce product catalog SEARCH functionality using Elasticsearch &amp; ReactJS

You will build working end-to-end e-commerce solution with more focus on 'Search' features such as auto-completion, guided search, fuzzy search, entity tagging, faceted search and more.  
## Part 1 - Setup software on local machine

### Setup Kubernentes enviornment
Follow below instructions to setup Minikube on your machine (Windows/Mac),

brew install helm


### Setup Elastic Cloud for Kubernetes (ECK) and Elastic Stack

Installing ECK using helm chart
```sh
helm repo add elastic https://helm.elastic.co
helm repo update
```

helm install elasticsearch elastic/elasticsearch --set replicas=1,minimumMasterNodes=1
kubectl port-forward svc/elasticsearch-master 9200



