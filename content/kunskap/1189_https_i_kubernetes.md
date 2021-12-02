Skapa kluster 

cost optimized preset configuration.

Availability None

version 1.20.9
create
Video för det ovanför!!

https://logz.io/blog/azure-kubernetes-cluster-aks/

  az login

Testa att vi hittar klustret
  az aks show --name name_of_aks_cluster --resource-group name_of_resource_group
  az aks show --name artikel --resource-group DIDA-ANAR12-DV1617-H21-LP2

Ladda ner config till kubectl

az aks get-credentials --name artikel --resource-group DIDA-ANAR12-DV1617-H21-LP2

kolla att det fungerade
  kubectl get nodes
  NAME                                STATUS     ROLES   AGE     VERSION
  aks-agentpool-86164874-vmss000000   Ready      agent   11m     v1.20.9
  aks-userpool-86164874-vmss000000    Ready      agent   9m46s   v1.20.9
  aks-userpool-86164874-vmss000002    NotReady   agent   10m     v1.20.9


installera helm

  https://helm.sh/docs/intro/install/

https://cert-manager.io/docs/tutorials/acme/ingress/#step-2-deploy-the-nginx-ingress-controller

driftsätta nginx ingress controller

  helm repo add ingress-nginx https://kubernetes.github.io/ingress-nginx

  $ helm repo update
Hang tight while we grab the latest from your chart repositories...
...Skip local chart repository
...Successfully got an update from the "stable" chart repository
...Successfully got an update from the "ingress-nginx" chart repository
...Successfully got an update from the "coreos" chart repository
Update Complete. ⎈ Happy Helming!⎈


  helm install nginx ingress-nginx/ingress-nginx --set rbac.create=true --version 4.0.12
```
NAME: nginx
LAST DEPLOYED: Wed Dec  1 14:23:02 2021
NAMESPACE: default
STATUS: deployed
REVISION: 1
TEST SUITE: None
NOTES:
The ingress-nginx controller has been installed.
It may take a few minutes for the LoadBalancer IP to be available.
You can watch the status by running 'kubectl --namespace default get services -o wide -w nginx-ingress-nginx-controller'

An example Ingress that makes use of the controller:
  apiVersion: networking.k8s.io/v1
  kind: Ingress
  metadata:
    name: example
    namespace: foo
  spec:
    ingressClassName: nginx
    rules:
      - host: www.example.com
        http:
          paths:
            - backend:
                service:
                  name: exampleService
                  port:
                    number: 80
              path: /
    # This section is only required if TLS is to be enabled for the Ingress
    tls:
      - hosts:
        - www.example.com
        secretName: example-tls

If TLS is enabled for the Ingress, a Secret containing the certificate and key must also be provided:

  apiVersion: v1
  kind: Secret
  metadata:
    name: example-tls
    namespace: foo
  data:
    tls.crt: <base64 encoded cert>
    tls.key: <base64 encoded key>
  type: kubernetes.io/tls
```

 kubectl get svc
```
NAME                                       TYPE           CLUSTER-IP     EXTERNAL-IP     PORT(S)                      AGE
kubernetes                                 ClusterIP      10.0.0.1       <none>          443/TCP                      22m
nginx-ingress-nginx-controller             LoadBalancer   10.0.194.219   20.67.217.206   80:30710/TCP,443:32004/TCP   49s
nginx-ingress-nginx-controller-admission   ClusterIP      10.0.189.69    <none>          443/TCP                      49s
```

Testa gå in på ip i webbläsare och kolla att de får 404 nginx.

Koppla domän till ip
kopiera external IP



Driftsätta exempel app

apiVersion: apps/v1
kind: Deployment
metadata:
  name: kuard
spec:
  selector:
    matchLabels:
      app: kuard
  replicas: 1
  template:
    metadata:
      labels:
        app: kuard
    spec:
      containers:
      - image: gcr.io/kuar-demo/kuard-amd64:1
        imagePullPolicy: Always
        name: kuard
        ports:
        - containerPort: 8080

  kubectl apply -f 001-app.yaml 
  deployment.apps/kuard created

  kubectl get deployment
NAME                             READY   UP-TO-DATE   AVAILABLE   AGE
kuard                            1/1     1            1           75s
nginx-ingress-nginx-controller   1/1     1            1           9m28s

apiVersion: v1
kind: Service
metadata:
  name: kuard
spec:
  ports:
  - port: 80
    targetPort: 8080
    protocol: TCP
  selector:
    app: kuard

kubectl apply -f 002-service.yaml 
service/kuard created

  kubectl get svc
NAME                                       TYPE           CLUSTER-IP     EXTERNAL-IP     PORT(S)                      AGE
kuard                                      ClusterIP      10.0.92.208    <none>          80/TCP                       67s
kubernetes                                 ClusterIP      10.0.0.1       <none>          443/TCP                      31m
nginx-ingress-nginx-controller             LoadBalancer   10.0.194.219   20.67.217.206   80:30710/TCP,443:32004/TCP   10m
nginx-ingress-nginx-controller-admission   ClusterIP      10.0.189.69    <none>          443/TCP                      10m


kubectl apply -f 003-ingress.yaml 
ingress.networking.k8s.io/kuard created

kubectl get ingress -w
  NAME    CLASS    HOSTS               ADDRESS   PORTS     AGE
  kuard   <none>   k8s.arnesson.tech             80, 443   16s
  kuard   <none>   k8s.arnesson.tech   20.67.217.206   80, 443   58s


http://domän - får security issue

curl -kivL -H 'Host: www.example.com' 'http://203.0.113.2'
  ...
  <html>
<head><title>404 Not Found</title></head>
<body>
<center><h1>404 Not Found</h1></center>
<hr><center>nginx</center>
</body>
</html>

alternativt
<!doctype html>

<html lang="en">
<head>
  <meta charset="utf-8">

  <title>KUAR Demo</title>

  <link rel="stylesheet" href="/static/css/bootstrap.min.css">
  <link rel="stylesheet" href="/static/css/styles.css">

  <script>
var pageContext = {"hostname":"kuard-5cd5556bc9-mml79","addrs":["10.244.0.10"],"version":"v0.8.1-1","versionColor":"hsl(18,100%,50%)","requestDump":"GET / HTTP/1.1\r\nHost: k8s.arnesson.tech\r\nAccept: */*\r\nUser-Agent: curl/7.74.0\r\nX-Forwarded-For: 10.244.0.1\r\nX-Forwarded-Host: k8s.arnesson.tech\r\nX-Forwarded-Port: 443\r\nX-Forwarded-Proto: https\r\nX-Forwarded-Scheme: https\r\nX-Real-Ip: 10.244.0.1\r\nX-Request-Id: 8d31add9483d046f572171216e7f01b7\r\nX-Scheme: https","requestProto":"HTTP/1.1","requestAddr":"10.244.0.8:48746"}
  </script>
</head>


<svg style="position: absolute; width: 0; height: 0; overflow: hidden;" version="1.1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink">
<defs>
<symbol id="icon-power" viewBox="0 0 32 32">
<title>power</title>
<path class="path1" d="M12 0l-12 16h12l-8 16 28-20h-16l12-12z"></path>
</symbol>
<symbol id="icon-notification" viewBox="0 0 32 32">
<title>notification</title>
<path class="path1" d="M16 3c-3.472 0-6.737 1.352-9.192 3.808s-3.808 5.72-3.808 9.192c0 3.472 1.352 6.737 3.808 9.192s5.72 3.808 9.192 3.808c3.472 0 6.737-1.352 9.192-3.808s3.808-5.72 3.808-9.192c0-3.472-1.352-6.737-3.808-9.192s-5.72-3.808-9.192-3.808zM16 0v0c8.837 0 16 7.163 16 16s-7.163 16-16 16c-8.837 0-16-7.163-16-16s7.163-16 16-16zM14 22h4v4h-4zM14 6h4v12h-4z"></path>
</symbol>
</defs>
</svg>

<body>
  <div id="root"></div>
  <script src="/built/bundle.js" type="text/javascript"></script>
</body>
</html>
* Connection #1 to host k8s.arnesson.tech left intact





installera cert-manager
https://cert-manager.io/docs/installation/

kubectl apply -f https://github.com/jetstack/cert-manager/releases/download/v1.6.1/cert-manager.yaml



staging

   apiVersion: cert-manager.io/v1
   kind: Issuer
   metadata:
     name: letsencrypt-staging
   spec:
     acme:
       # The ACME server URL
       server: https://acme-staging-v02.api.letsencrypt.org/directory
       # Email address used for ACME registration
       email: aar@bth.se
       # Name of a secret used to store the ACME account private key
       privateKeySecretRef:
         name: letsencrypt-staging
       # Enable the HTTP-01 challenge provider
       solvers:
       - http01:
           ingress:
             class:  nginx

$ kubectl describe Issuer letsencrypt-staging
Name:         letsencrypt-staging
Namespace:    default
Labels:       <none>
Annotations:  <none>
API Version:  cert-manager.io/v1
Kind:         Issuer
Metadata:
  Creation Timestamp:  2021-12-01T14:58:15Z
  Generation:          1
  Managed Fields:
    API Version:  cert-manager.io/v1
    Fields Type:  FieldsV1
    fieldsV1:
      f:metadata:
        f:annotations:
          .:
          f:kubectl.kubernetes.io/last-applied-configuration:
      f:spec:
        .:
        f:acme:
          .:
          f:email:
          f:privateKeySecretRef:
            .:
            f:name:
          f:server:
          f:solvers:
    Manager:      kubectl-client-side-apply
    Operation:    Update
    Time:         2021-12-01T14:58:15Z
    API Version:  cert-manager.io/v1
    Fields Type:  FieldsV1
    fieldsV1:
      f:status:
        .:
        f:acme:
          .:
          f:lastRegisteredEmail:
          f:uri:
        f:conditions:
    Manager:         controller
    Operation:       Update
    Time:            2021-12-01T14:58:16Z
  Resource Version:  11689
  UID:               584f8f36-4526-4432-9913-fab095dd6725
Spec:
  Acme:
    Email:            aar@bth.se
    Preferred Chain:  
    Private Key Secret Ref:
      Name:  letsencrypt-staging
    Server:  https://acme-staging-v02.api.letsencrypt.org/directory
    Solvers:
      http01:
        Ingress:
          Class:  nginx
Status:
  Acme:
    Last Registered Email:  aar@bth.se
    Uri:                    https://acme-staging-v02.api.letsencrypt.org/acme/acct/35545288
  Conditions:
    Last Transition Time:  2021-12-01T14:58:16Z
    Message:               The ACME account was registered with the ACME server
    Observed Generation:   1
    Reason:                ACMEAccountRegistered
    Status:                True
    Type:                  Ready
Events:                    <none>

Kolla att är registered under status.

samma med prod


updater 003-ingress att använda staging
$ kubectl apply -f 003-ingress.yaml 
ingress.networking.k8s.io/kuard configured

kubectl get certificate
NAME                  READY   SECRET                AGE
artiekl-example-tls   True    artiekl-example-tls   4m


$ kubectl describe certificate artiekl-example-tls
Name:         artiekl-example-tls
Namespace:    default
Labels:       <none>
Annotations:  <none>
API Version:  cert-manager.io/v1
Kind:         Certificate
Metadata:
  Creation Timestamp:  2021-12-01T15:00:59Z
  Generation:          1
  Managed Fields:
    API Version:  cert-manager.io/v1
    Fields Type:  FieldsV1
    fieldsV1:
      f:metadata:
        f:ownerReferences:
          .:
          k:{"uid":"91034500-dd3b-4a05-b53f-341b25600cd2"}:
            .:
            f:apiVersion:
            f:blockOwnerDeletion:
            f:controller:
            f:kind:
            f:name:
            f:uid:
      f:spec:
        .:
        f:dnsNames:
        f:issuerRef:
          .:
          f:group:
          f:kind:
          f:name:
        f:privateKey:
        f:secretName:
        f:usages:
      f:status:
        .:
        f:conditions:
        f:notAfter:
        f:notBefore:
        f:renewalTime:
        f:revision:
    Manager:    controller
    Operation:  Update
    Time:       2021-12-01T15:01:25Z
  Owner References:
    API Version:           networking.k8s.io/v1
    Block Owner Deletion:  true
    Controller:            true
    Kind:                  Ingress
    Name:                  kuard
    UID:                   91034500-dd3b-4a05-b53f-341b25600cd2
  Resource Version:        12085
  UID:                     102284a3-0cdb-43b0-8182-86ea7a76246f
Spec:
  Dns Names:
    k8s.arnesson.tech
  Issuer Ref:
    Group:      cert-manager.io
    Kind:       Issuer
    Name:       letsencrypt-staging
  Secret Name:  artiekl-example-tls
  Usages:
    digital signature
    key encipherment
Status:
  Conditions:
    Last Transition Time:  2021-12-01T15:01:25Z
    Message:               Certificate is up to date and has not expired
    Observed Generation:   1
    Reason:                Ready
    Status:                True
    Type:                  Ready
  Not After:               2022-03-01T14:01:24Z
  Not Before:              2021-12-01T14:01:25Z
  Renewal Time:            2022-01-30T14:01:24Z
  Revision:                1
Events:
  Type    Reason     Age    From          Message
  ----    ------     ----   ----          -------
  Normal  Issuing    5m27s  cert-manager  Issuing certificate as Secret was previously issued by Issuer.cert-manager.io/letsencrypt-prod
  Normal  Reused     5m27s  cert-manager  Reusing private key stored in existing Secret resource "artiekl-example-tls"
  Normal  Requested  5m27s  cert-manager  Created new CertificateRequest resource "artiekl-example-tls-llqhg"
  Normal  Issuing    5m1s   cert-manager  The certificate has been successfully issued



$ kubectl describe secret artiekl-example-tls
Name:         artiekl-example-tls
Namespace:    default
Labels:       <none>
Annotations:  cert-manager.io/alt-names: k8s.arnesson.tech
              cert-manager.io/certificate-name: artiekl-example-tls
              cert-manager.io/common-name: k8s.arnesson.tech
              cert-manager.io/ip-sans: 
              cert-manager.io/issuer-group: cert-manager.io
              cert-manager.io/issuer-kind: Issuer
              cert-manager.io/issuer-name: letsencrypt-prod
              cert-manager.io/uri-sans: 

Type:  kubernetes.io/tls

Data
====
tls.crt:  5595 bytes
tls.key:  1679 bytes


updater ingress att använda prod istället

$ kubectl apply -f 003-ingress.yaml 
ingress.networking.k8s.io/kuard configured

radera gamla hemligheten så att den skapar en ny riktgt

$ kubectl delete secret artiekl-example-tls
secret "artiekl-example-tls" deleted


$ kubectl describe certificate artiekl-example-tls
Name:         artiekl-example-tls
Namespace:    default
Labels:       <none>
Annotations:  <none>
API Version:  cert-manager.io/v1
Kind:         Certificate
Metadata:
  Creation Timestamp:  2021-12-01T15:00:59Z
  Generation:          2
  Managed Fields:
    API Version:  cert-manager.io/v1
    Fields Type:  FieldsV1
    fieldsV1:
      f:metadata:
        f:ownerReferences:
          .:
          k:{"uid":"91034500-dd3b-4a05-b53f-341b25600cd2"}:
            .:
            f:apiVersion:
            f:blockOwnerDeletion:
            f:controller:
            f:kind:
            f:name:
            f:uid:
      f:spec:
        .:
        f:dnsNames:
        f:issuerRef:
          .:
          f:group:
          f:kind:
          f:name:
        f:privateKey:
        f:secretName:
        f:usages:
      f:status:
        .:
        f:conditions:
        f:notAfter:
        f:notBefore:
        f:renewalTime:
        f:revision:
    Manager:    controller
    Operation:  Update
    Time:       2021-12-01T15:09:31Z
  Owner References:
    API Version:           networking.k8s.io/v1
    Block Owner Deletion:  true
    Controller:            true
    Kind:                  Ingress
    Name:                  kuard
    UID:                   91034500-dd3b-4a05-b53f-341b25600cd2
  Resource Version:        13022
  UID:                     102284a3-0cdb-43b0-8182-86ea7a76246f
Spec:
  Dns Names:
    k8s.arnesson.tech
  Issuer Ref:
    Group:      cert-manager.io
    Kind:       Issuer
    Name:       letsencrypt-prod
  Secret Name:  artiekl-example-tls
  Usages:
    digital signature
    key encipherment
Status:
  Conditions:
    Last Transition Time:  2021-12-01T15:09:31Z
    Message:               Certificate is up to date and has not expired
    Observed Generation:   2
    Reason:                Ready
    Status:                True
    Type:                  Ready
  Not After:               2022-03-01T14:09:29Z
  Not Before:              2021-12-01T14:09:30Z
  Renewal Time:            2022-01-30T14:09:29Z
  Revision:                3
Events:
  Type    Reason     Age                  From          Message
  ----    ------     ----                 ----          -------
  Normal  Issuing    10m                  cert-manager  Issuing certificate as Secret was previously issued by Issuer.cert-manager.io/letsencrypt-prod
  Normal  Requested  10m                  cert-manager  Created new CertificateRequest resource "artiekl-example-tls-llqhg"
  Normal  Reused     3m28s (x2 over 10m)  cert-manager  Reusing private key stored in existing Secret resource "artiekl-example-tls"
  Normal  Issuing    3m28s                cert-manager  Issuing certificate as Secret was previously issued by Issuer.cert-manager.io/letsencrypt-staging
  Normal  Requested  3m28s                cert-manager  Created new CertificateRequest resource "artiekl-example-tls-j7cdd"
  Normal  Issuing    103s                 cert-manager  Issuing certificate as Secret does not exist
  Normal  Generated  102s                 cert-manager  Stored new private key in temporary Secret resource "artiekl-example-tls-9j2tv"
  Normal  Requested  102s                 cert-manager  Created new CertificateRequest resource "artiekl-example-tls-hkgvj"
  Normal  Issuing    98s (x3 over 9m44s)  cert-manager  The certificate has been successfully issued


gå till webbläsaren så ska sidan synas.