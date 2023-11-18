#k8s 

- Create secrets generic
- Link secrets into ETCD through `etcdctl`
- Encrypted secrets data stored in ETCD
	- Create `encryption-proivder-config` file called `enc.yaml` at local directory (on k8s cluster server)
	- Add argument `--encryption-provider-config`  in `kube-apiserver.yaml` file
	- Add config in volumeMounts
	- Add config in volumes