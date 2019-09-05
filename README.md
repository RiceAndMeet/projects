# Elastic Cloud on Kubernetes (ECK) Sample Code

### Software Prerequsite 
- Kubectl 1.11+
- Kubernetes 1.13 + 
- Kubernetes cluster admin access

### Download and apply ECK CustomResourceDefinition, Operator Setup and Role
`kubectl apply -f https://download.elastic.co/downloads/eck/0.9.0/all-in-one.yaml` 

### start Elasticsearch Cluster and Kibana Instances 
`kubectl apply -f elasticsearch.yml`
`kubectl apply -f kibana.yml`

### Connect to Kibana 
#### Bind local port with kibana service port 
`kubectl port-forward service/kibana-kb-http 5601`
#### retrieve default user "elastic" password 
`echo $(kubectl get secret elasticsearch-es-elastic-user -o=jsonpath='{.data.elastic}' | base64 --decode)`
#### Open https://localhost:5601 in your browser

### install Filebeat & Metricbeat to enable logging and metric collecting on the cluster 
`kubectl apply -f filebeat.yml`

`kubectl apply -f metricbeat.yml`
