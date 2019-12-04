### Rodar geração do Vagrant
```
vagrant up
```
### Ver status das máquinas criadas
```
vagrant status
```
### Instalando metrics server
- Abrir o arquivo:
```
vim metrics-server/deploy/1.8+/metrics-server-deployment.yaml
trocar readOnlyRootFileSystem para false
incluir em args:
  --kubelet-insecure-tls
  --kubelet-preferred-address-types=InternalIP
kubectl apply -f metrics-server/deploy/1.8+/
```
### Fazendo backup do etcd
```
etcdctl snapshot save --cacert ca.crt --cert server.crt --key server.key /root/etcd.db
```
### fazendo consultas no etcd
```
etcdctl get '' --prefix --keys-only --cacert ca.crt --cert server.crt --key server.key
etcdctl get '/registry/pods/default' --prefix --cacert ca.crt --cert server.crt --key server.key
```
### Criar namespace
```
kubectl create ns <namespace-name>
```
### Criar service account sa atrelado a um namespace
```
kubectl create sa sa-restart -n <namespace-name>
```
### ver qual namespace estou
```
kubectl config view
```
