# dvwa-k8s

[Damn Vulnerable Web Application (DVWA)](http://www.dvwa.co.uk/) inside of [k8s](https://kubernetes.io/docs/concepts/overview/what-is-kubernetes/) just because we can 

## How-to

Step1

* [ ] `helm install --name mysql stable/mysql`
* [ ] `helm install --namespace ingress stable/nginx-ingress`
* [ ] `helm install --name cert-manager --namespace cert-manager --version v0.11.0 jetstack/cert-manager`

Step 2

* [ ] `kubectl create configmap php-config --from-file=php.ini`
* [ ] `kubectl create configmap web-dvwa-config --from-file=config.inc.php`
* [ ] `kubectl create -f clusterissuer.yml`
* [ ] `kubectl create -f svc.yml`
* [ ] `kubectl create -f deployment.yml`
* [ ] `kubectl create -f ingress.yml`

Step 3
