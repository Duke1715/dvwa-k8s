# dvwa-k8s

[Damn Vulnerable Web Application (DVWA)](http://www.dvwa.co.uk/) inside of [k8s](https://kubernetes.io/docs/concepts/overview/what-is-kubernetes/) just because we can 

## How-to

## Step1

* [ ] `helm install --name mysql stable/mysql`
* [ ] `helm install --namespace ingress stable/nginx-ingress`
Cert-manager:
### Kubernetes 1.16+
* `kubectl apply --validate=false -f https://github.com/jetstack/cert-manager/releases/download/v1.0.4/cert-manager.yaml`

### Kubernetes <1.16
* `kubectl apply --validate=false -f https://github.com/jetstack/cert-manager/releases/download/v1.0.4/cert-manager-legacy.yaml`
* `kubectl create namespace cert-manager`
* `helm repo add jetstack https://charts.jetstack.io && helm repo update`
### Helm v3+
  `helm install cert-manager jetstack/cert-manager --namespace cert-manager --version v1.0.4 #--set installCRDs=true`

### Helm v2
  `helm install --name cert-manager --namespace cert-manager --version v1.0.4 jetstack/cert-manager #--set installCRDs=true`

## Step 2

* [ ] `kubectl create configmap php-config --from-file=php.ini`
* [ ] `kubectl create configmap web-dvwa-config --from-file=config.inc.php`
* [ ] `kubectl create -f clusterissuer.yml`
* [ ] `kubectl create -f svc.yml`
* [ ] `kubectl create -f deployment.yml`
* [ ] `kubectl create -f ingress.yml`
