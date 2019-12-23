## KubeConfig

#### Generate a CA private key
```
openssl genrsa -out john.key 2048
```

#### Create a self signed Certificate
```
openssl req -new -key john.key -subj "/CN=john" -out john.csr
```
or
```
openssl req -new -key john.pem -out john-csr.pem -subj "/CN=john"
openssl x509 -req -in john-csr.pem -CA ca.crt -CAkey ca.key -CAcreateserial -out john.crt -day 10000
```

#### Describe one or many contexts
```
kubectl config  get-contexts
```

#### Displays the current-context
```
kubectl config view
kubectl config view --kubeconfig=[current_context]
```

#### Sets the current-context in a kubeconfig file
```
kubectl confin use-context [current_context]
kubectl config --kubeconfig=/root/my-kube-config use-context [current_context]
```

#### References
- [`https://kubernetes.io/docs/tasks/access-application-cluster/configure-access-multiple-clusters/`](https://kubernetes.io/docs/tasks/access-application-cluster/configure-access-multiple-clusters/)
- [`https://kubernetes.io/docs/tasks/administer-cluster/kubeadm/kubeadm-certs/`](https://kubernetes.io/docs/tasks/administer-cluster/kubeadm/kubeadm-certs/)