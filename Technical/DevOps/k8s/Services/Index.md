#k8s 

- Node Port
- Cluster IP
- Ingress
- Load Balance

To connect to service in another namespace, we need to connect to its dns:
exp: mysql.connect("db-service.dev.svc.cluster.local")
	- db-service: service name
	- dev: namespace
	- svc: service
	- cluser.local: domain

## ClusterIP

- **Allow** other objects **inside** the cluster can connect to each others
- **Not allowed** other **outside** requests such as from browsers