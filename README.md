# e-commerce-search-sample
A step-by-step guide to build a sample e-commerce product catalog SEARCH functionality using Elasticsearch &amp; ReactJS

You will build working end-to-end e-commerce solution with more focus on 'Search' features such as auto-completion, guided search, fuzzy search, entity tagging, faceted search and more.  
## Part 1 - Setup software on local machine

For MacOS,
minikube config set driver hyperkit

minikube config set memory 10240

### Setup Kubernentes enviornment
Follow below instructions to setup Minikube on your machine (Windows/Mac),

brew install helm


### Setup Elastic Cloud for Kubernetes (ECK) and Elastic Stack

Installing ECK using helm chart
```sh
helm repo add elastic https://helm.elastic.co
helm repo update
```

helm install elastic-operator elastic/eck-operator -n elastic-system --create-namespace

Monitor operator logs,
kubectl -n elastic-system logs -f statefulset.apps/elastic-operator

kubectl apply -f elasticsearch.yaml
https://www.elastic.co/guide/en/cloud-on-k8s/current/k8s-deploy-elasticsearch.html


kubectl logs -f quickstart-es-default-0

    Get the credentials.

    A default user named elastic is automatically created with the password stored in a Kubernetes secret:

PASSWORD=$(kubectl get secret quickstart-es-elastic-user -o go-template='{{.data.elastic | base64decode}}')

    From your local workstation, use the following command in a separate terminal:

kubectl port-forward service/equickstart-es-http 9200

    Then request localhost:
curl -u "elastic:$PASSWORD" -k "https://localhost:9200"

kubectl get pods --selector='enterprisesearch.k8s.elastic.co/name=enterprise-search-quickstart'

kubectl apply -f enterprisesearch.yaml
https://www.elastic.co/guide/en/cloud-on-k8s/current/k8s-enterprise-search-quickstart.html

kubectl port-forward service/enterprise-search-quickstart-ent-http 3002
Open https://localhost:3002 in your browser.



