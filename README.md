# ElasticSearchDeployment
Muti node elasticsearch deloyment on kuberenetes cluster

This elastic search YAML creates 3 nodes elastic cluster inside the kuberenetes with type as "loadbalancer" with 64Gb SSD storage attached to each node.

Also the elastic search cluster is deployed as stateful service and thus in case of any node failure ,it is reinitialized automatically without loss of any data.

The cluster created is also secured cluster.Following securities are provided:
a.)Cluster can be acccesed only inside the resource VNET.
2.)Cluster uses auth details as well certificate for authentication

Steps for installing the cluster:
1.)Install the elastic search operator on the kuberenetes cluster using the depency.txt file inside dependency folder.
2.)Apply the elastic.yaml using kubectl apply -f elastic.yaml
3.)A stateful elastic service would be created and same can be seen by using kubectl get svc -o wide
4.)Once all the three pods(nodes) are up and elastic service is up and running ,copy the loadbalancer of elastic service created.Once you do ,kubectl get svc -o wide,you will see type as "loadbalancer" corresponding to elastic service ,copy the IP.
5.)Reopen the elastic.yaml again and uncomment the TLS section and paste the copied ip infront ip key and apply the elasctic.yaml again.
