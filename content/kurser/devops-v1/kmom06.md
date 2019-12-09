---
author:
    - aar
revision:
    "2019-10-15": "(A, aar) Första versionen."
...
Kmom06: Container orchestration
==================================

Er Microblog har fått många nya användare och ni behöver utöka er infrastruktur för att hantera tycket på servrarna. Ni börjar med att utöka hur ni använder Ansible och startar upp fler servrar och containrar på servrarna. Dock märker ni snabbt att det är krångligt och Ansible är inte gjort för att användas till detta. Istället  börjar ni läsa på om container orchestration.



<!-- more -->
[WARNING]	

 **Kursutveckling pågår**	

 Kursen ges hösten 2019 läsperiod 2.

[/WARNING]



[FIGURE src="https://miro.medium.com/max/660/1*Mdj9wylSl0wqJ9sB0ENbRA.png" caption="Hur det är att lära sig kubernetes."]

Vi kommer använda oss utav Kubernetes (K8s) för container orchestration men det är bra att känna till vilka andra verktyg som finns och lite om vad som skiljer dem åt. Läs [What Is Container Orchestration?](https://blog.newrelic.com/engineering/container-orchestration-explained/)



### Kubernetes {#k8s}

Börja med en snabb introduktion till Kubernetes begrepp.

[YOUTUBE src="PH-2FfFD2PU" caption="Kubernetes in 5 mins."]

Om det inte var pedagogiskt nog som förklaring av Kubernetes kan jag rekommendera följande video där de lär ut Kubernetes som en barnbok.

[YOUTUBE src="Q4W8Z-D-gcQ" caption="The Illustrated Children's Guide to Kubernetes."]

Kubernetes har själva väldigt mycket och bra material för att lära sig Kubernetes och alla dess delar. En bra utgångspunkt är deras [dokumentation](https://kubernetes.io/docs/home/), där finns länkar till det mesta. För att få en bättre förståelse för grunderna i K8s (Kubernetes) och hur man kan interagera med det ska ni jobba igenom modul 1-6 i [Learn Kubernetes basics](https://kubernetes.io/docs/tutorials/kubernetes-basics/).



#### Kubernetes yaml {#yaml}

Det finns två sätt att hantera objekt (pods, deployments, etc...) i K8s imperative och declarative. I imperative kör vi kommandon i terminalen för att jobba mot ett K8s kluster, som ni gjorde i Kubernetes basics, och i declarative skriver vi konfiguration i filer och kör mot klustret. Läs om deras olika [för och nackdelar](https://kubernetes.io/docs/concepts/overview/working-with-objects/object-management/). Vi vill givetvis jobba declarative för att då kan vi spara konfigurationen i Git och vi behöver inte oroa oss för snowflake servrar eller att bara en person har kunskapen om klustret.

[FIGURE src="https://www.digitalocean.com/community/tutorials/imperative-vs-declarative-kubernetes-management-a-digitalocean-comic" caption="digitalocean förklarar imperativ vs declarative"]

K8s använder yaml filer för att skriva konfigurationen i filer, som Ansible. Läs igenom [Kubernetes deployment tutorial](https://devopscube.com/kubernetes-deployment-tutorial/) för en överblick av hur filerna struktureras och vad de kan innehålla. Ni behöver inte jobba med i guiden, räcker om ni läser och förstår.

Ni kan öva på att använda [konfig filer på katacoda](https://www.katacoda.com/courses/kubernetes/creating-kubernetes-yaml-definitions).



#### Stateless applications {#statless}

K8s bygger på virtualisering och containrar, vilket är i grunden stateless. Vi har inte tillgång till persistent data, när vi stänger ner en container så försvinner dess data. K8s och även Docker är i grunden byggt för att köra stateless applikationer, men när populariteten av verktygen har ökat har även användningsområden ökat och de har då lagt till olika lösningar för att få till persistent data (stateful). Men det är inte lika lätt att få till persistent data i K8s som det är i Docker. Läs [Stateful vs Stateless Applications on Kubernetes](https://linuxhint.com/stateful-vs-stateless-kubernetes/) för en bättre genomgång av skillnaden.

Ni ska börja med att öva på att skapa en stateless applikation och som tur är har K8s själva en bra guide för det. Jobba igenom [Deploying PHP Guestbook application with Redis](https://kubernetes.io/docs/tutorials/stateless-application/guestbook/). Ni behöver ha en miljö att köra K8s klustret i, i guiden finns det länk till sandbox miljöer både i Katacoda och Play with Kubernetes som ni kan använda. Jag rekommenderar Katacoda då jag inte fick Play with K8s att fungera. Katacoda har dessutom Nano installerat så ni kan skriva konfigurationen till filer. Allt borde fungera utan problem fram tills steget [Viewing the Frontend Service via NodePort](https://kubernetes.io/docs/tutorials/stateless-application/guestbook/#viewing-the-frontend-service-via-nodeport), Katacoda kör inte minikube för att starta sitt kluster så ni kan inte använda det för att få en extern ip till ert kluster. Istället kan ni i Katacoda klicka på `+` som finns uppe på er terminal och välja `select port to view on host 1`. Då öppnas en ny tab i webbläsaren med koppling till klustret och där skriver ni in NodePort för er frontend service.

Det finns en mängd olika sätta och verktyg för att köra Kubernetes beroende på vilken miljö man vill köra det i. Ni kan läsa [Deploy Kubernetes In Five Different Ways](https://platform9.com/blog/5-methods-deploy-kubernetes/) för en kort överblick av några.



#### Stateful applications {#stateful}

Nu när ni har testat på att köra en stateless applikatopn i K8s ska ni lära er hur man kan köra en stateful applikation. Börja med att läsa [The sad state of stateful Pods in Kubernetes](https://elastisys.com/2018/09/18/sad-state-stateful-pods-kubernetes/) för en förklaring av problemet med stateful applikationer.

Läs sen om några av de olika sätten vi kan skapa volymer i K8s och jobba sen igenom [](https://www.katacoda.com/mjboxboat/courses/kubernetes-fundamentals-2/persistent-volumes).

https://kubernetes.io/docs/tasks/configure-pod-container/configure-persistent-volume-storage/

Innan ni stänger ner hela miljön, lägg till webui https://kubernetes.io/docs/tasks/access-application-cluster/web-ui-dashboard/ för att inspektera K8s infrastrukturen.

https://www.katacoda.com/courses/kubernetes/liveness-readiness-healthchecks

https://www.katacoda.com/javajon/courses/kubernetes-pipelines/helm

#### Designa för Kubernetes {#design} 

Ni har nu titta lite på hur en applikations design/arkitektur påverkar hur lätt det är att köra den i K8s, det finns så klart flera saker som är bra att tänka på när man skapa sin applikation men även hur man sätter upp den i K8s. Läs [Architecting Applications for Kubernetes](https://www.digitalocean.com/community/tutorials/architecting-applications-for-kubernetes) som tar upp lite om hur man ska tänka runt applikationen men även hur man använder K8s. Läs sen [Modernizing Applications for Kubernetes](https://www.digitalocean.com/community/tutorials/modernizing-applications-for-kubernetes) som handlar mer om hur man kan skriva om en applikation för att den ska fungera bättre för K8s.



### Microblog i Kubernetes {#microblog}

Nu ska vi sätta upp Microbloggen i Kubernetes. Vi behöver en miljö att köra K8s i. AWS har en managed Kubernetes service kallat [EKS](https://aws.amazon.com/eks/) men det kostar ju massa kredit vilket vi inte har oändligt at så vi kommer använda oss utan [Kubernetes Operations](https://github.com/kubernetes/kops) (Kops). Kops skriver om sig själva "The easiest way to get a production grade Kubernetes cluster up and running." och än så länge har det varit väldigt trevlig att använda. Vi ska använda Kops för att sätta upp ett K8s kluster på vanliga EC2 servrar på AWS så blir det billigare än att använda EKS.



#### Kubernetes på AWS med Kops {#k8s_aws}
<!-- 
https://medium.com/containermind/how-to-create-a-kubernetes-cluster-on-aws-in-few-minutes-89dda10354f4
https://github.com/kubernetes/kops/blob/master/docs/install.md
https://kubernetes.io/docs/setup/production-environment/tools/kops/
 -->

Vi behöver använda följande verktyg för att få upp ett kluster [Kops](https://github.com/kubernetes/kops), [kubectl](https://kubernetes.io/docs/reference/kubectl/overview/) och [AWS cli](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-welcome.html).



##### Installera verktyg {#install}

- Installera [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/), jag rekommendera att göra [Enabling shell autocompletion](https://kubernetes.io/docs/tasks/tools/install-kubectl/#enabling-shell-autocompletion) så kan ni använda `tab` för att autocomplete kommandon och resurser i kubectl.

- Installera aws-cli med `pip3 install awscli --upgrade --user`.

- Installera [Kops](https://github.com/kubernetes/kops#installing).

När allt är installerat behöver både AWS cli och Kops era AWS nycklar som miljövariabler men de använder olika namn för samma nyckel. I mappen `kubernetes` kan ni hitta filen `export_aws_keys.sh`. Den fungera som insert skriptet i Ansible, så kopiera era AWS nycklar och kör skriptet med `. export_aws_keys.sh`.



##### Domän för Kubernetes klustret {#doman}

Kops behöver ett domännamn kopplat till klustret, ni kan välja att använda samma domän ni redan har eller att skapa en specifik subdomän för k8s. Om ni använder samma domän behöver ni gå in i Route 53 och ta bort de Record sets med `Type A`. Kops kommer skapa egna records. Om ni skapar en subdomän för klustret gör följande:

1. skapa en nu hosted zone och döp den till vad ni vill att subdomänen ska heta, jag döpte min till `k8s.<domain>`.

1. Kopiera `NS` värdena för er subdomänen.

1. Gå sen till förälder domänens hosted zone och skapa ett nytt Record set, med typen NS.

1. Klistra in NS värdena ni kopierade som values.

I terminalen kan ni köra `dig NS <subdomain>` för att kolla att den har rätt NS värden.



##### S3 Bucket för klustret {#s3}

Vi börjar med att konfigurera AWS cli, välj None på alla utom `region` i och med att vi har AWS nycklarna som ENV variabler.

```
aws configure

AWS Access Key ID [None]:
AWS Secret Access Key [None]:
Default region name [None]: us-east-1
Default output format [None]:
```

Kops behöver någonstans att spara data om klustret efter att vi skapat det. Vi ska använda en [S3 bucket på AWS](https://docs.aws.amazon.com/AmazonS3/latest/dev/Welcome.html) (Simple Storage Service), om vi hade varit på ett företag och flera personer ska kunna jobba mot klustret kan alla få tillgång till Bucket:en då behöver vi inte spara undan all data och skicka den mellan alla på något sätt. VI kopplar klustrets namn till domänen det ska vara kopplat till.

```
bucket_name=clusters.<domain>
export KOPS_STATE_STORE=s3://${bucket_name}

aws s3api create-bucket \
--bucket ${bucket_name} \
--region us-east-1
```



##### Skapa Kubernetes kluster {#skapa}

Vi börjar med att sätta namn på klustret.

```
export KOPS_CLUSTER_NAME=k8s.<domain>
```

Skapa kluster konfiguration.

```
kops create cluster --node-count=2 --node-size=t2.medium --zones=us-east-1a --name=${KOPS_CLUSTER_NAME} --master-size=t2.medium --ssh-public-key=<path-to-ssh-.pub-key>

kops get cluster
```

Ni kan kolla över hela konfigurationen med `kops edit cluster`. Vi vill inte ändra något i den så bara stäng ner den igen när ni kollat vad som finns där.

Nu ska vi skapa klustret och servrarna på AWS.

```
kops update cluster --yes
```

Nu kan ni spamma `kops validate cluster` till klustret är redo, det kan ta flera minuter innan domänen och allt är uppe och rullar. Vi har skapat 3 servrar på AWS, 1 master och 2 nodes.

När ni kan se `Your cluster <domain> is ready` har ni ett fungerande Kubernetes kluster upp och rullar. Nu kan ni köra `kubectl -n kube-system get po` för att se alla delar av klustret.

När ni ska stänga ner klustret kan ni göra det med

```
kops delete cluster  --yes
```

Det kommer ta bort alla servrar på AWS.

<!-- 
Spara er Kubernetes konfiguration.

```
kops get -o yaml > k8s-config.yml
kops create -f k8s-config.yml
kops update cluster --ssh-public-key=~/.ssh/aws.pub --yes
```
-->


##### Dashboard {#dashboard}

Det finns en [dashboard för K8s kluster](https://kubernetes.io/docs/tasks/access-application-cluster/web-ui-dashboard/), vi ska installer. Så vi får en grafisk vy för klustret.

```
kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/v1.10.1/src/deploy/recommended/kubernetes-dashboard.yaml
```

Sen behöver vi en token för att logga in på UI:t, `kops get secrets admin --type secret -oplaintext`, kopiera utskriften.

Nu ska vi börja använda `kubectl` för at jobba mot klustret och starta en proxy till klustret för att komma åt  UI:t.

```
kubectl proxy
```

Gå till `http://localhost:8001/api/v1/namespaces/kube-system/services/https:kubernetes-dashboard:/proxy` i webbläsaren och logga in med token. Läs [using dashboard](https://kubernetes.io/docs/tasks/access-application-cluster/web-ui-dashboard/#using-dashboard) för en snabb överblick av UI:t.

Nu är vi redo att börja sätta upp Microbloggen på klustret. Vi börjar med att få upp en databas.



#### Mysql i Kubernetes {#mysql}
<!--
secret from https://www.serverlab.ca/tutorials/containers/kubernetes/how-to-deploy-mysql-server-5-7-to-kubernetes/
setup deployment https://kubernetes.io/docs/tasks/run-application/run-single-instance-stateful-application/
 -->

Vi läste tidigare att det inte är så bra att köra database i K8s, men vi gör det ändå för att öva på stateful applikationer. Vi ska använda PersistentVolumeClaim för att få stateful data åt databasen. Det är inte säkert egentligen då vi förlorar all data om noderna går ner. Om vi har gjort detta i verkligheten hade vi kopplat datan till en S3 Bucket också.



##### Skydda lösenord med Secrets {#secrets}

Vi börjar med att skapa en [secret](https://kubernetes.io/docs/concepts/configuration/secret/) file då vi kommer sätta lösenord i deployments filerna. Vi behöver ett root lösenord och en lösenord åt Microblogen.

```
echo -n "my-super-secret-root-password" | base64
<password-string>

echo -n "micropassw" | base64
<password-string>
```

Skapa en fil, `mysql-secrets.yml`.

```
---
apiVersion: v1
kind: Secret
metadata:
  name: mysql-secrets
type: Opaque
data:
  ROOT_PASSWORD: <password-string>
  DB_PASSWORD: <password-string>
```

Aktivera dem i kubectl.

```
kubectl apply -f mysql-secrets.yml

kubectl get secret
NAME                  TYPE                                  DATA   AGE
default-token-8ld8g   kubernetes.io/service-account-token   3      37m
mysql-secrets         Opaque                                2      36s

kubectl describe secret mysql-secrets
Name:         mysql-secrets
Namespace:    default
Labels:       <none>
Annotations:
Type:         Opaque

Data
====
DB_PASSWORD:    34 bytes
ROOT_PASSWORD:  29 bytes
```



##### Persisten data med PersistentVolumeClaim {#mysql-pvc}

Skapa filen `mysql-pv.yml`.

```
apiVersion: v1
kind: PersistentVolume
metadata:
  name: mysql-pv-volume
  labels:
    type: local
spec:
  storageClassName: manual
  capacity:
    storage: 5Gi
  accessModes:
    - ReadWriteOnce
  hostPath:
    path: "/mnt/data"
---
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: mysql-pv-claim
spec:
  storageClassName: manual
  accessModes:
    - ReadWriteOnce
  resources:
    requests:
      storage: 5Gi
```

Vi skapar en Volym med 5 gig och `ReadWriteOnce` så at bara en nod kan använda volymen.

```
kubectl apply -f mysql-pv.yml

kubectl get persistentvolumeclaim mysql-pv-claim
NAME             STATUS   VOLUME            CAPACITY   ACCESS MODES   STORAGECLASS   AGE
mysql-pv-claim   Bound    mysql-pv-volume   5Gi        RWO            manual         66s
```



##### Mysql deployment {#mysql-deploy}

Skapa filen `mysql-deployment.yml`. I den skapar vi en Service, så att Microblogen sen kan koppla upp sig mot databasen.

```
apiVersion: v1
kind: Service
metadata:
  name: mysql
spec:
  ports:
  - port: 3306
  selector:
    app: mysql
  clusterIP: None
```

Vi sätter `clusterIP: None` så att Servicens IP kopplas direkt mot POD:en. Det är att föredra om man bara ska ha en POD bakom en service, vilket vi ska.

Lägg till följande i slutet av filen.

```
---
apiVersion: apps/v1 # for versions before 1.9.0 use apps/v1beta2
kind: Deployment
metadata:
  name: mysql
spec:
  selector:
    matchLabels:
      app: mysql
  strategy:
    type: Recreate
  template:
    metadata:
      labels:
        app: mysql
    spec:
      containers:
      - image: mysql:5.7
        name: mysql
        env:
          # Use secret in real usage
        - name: MYSQL_USER
          value: microblog
        - name: MYSQL_DATABASE
          value: microblog
        - name: MYSQL_PASSWORD
          valueFrom:
            secretKeyRef:
              name: mysql-secrets
              key: DB_PASSWORD
        - name: MYSQL_ROOT_PASSWORD
          valueFrom:
            secretKeyRef:
              name: mysql-secrets
              key: ROOT_PASSWORD
        ports:
        - containerPort: 3306
          name: mysql
        volumeMounts:
        - name: mysql-persistent-storage
          mountPath: /var/lib/mysql
      volumes:
      - name: mysql-persistent-storage
        persistentVolumeClaim:
          claimName: mysql-pv-claim
```

Vi läser lösenorden från secrets och mountar PV:n vi skapade tidigare. Notera ` strategy:` `type: Recreate`, det gör att K8s inte gör rolling updates. Vi vill inte använda det för databasen i och med att vi bara vill ha en igång åt gången. Nu kommer POD:en först soppas och en startas en ny med updaterad konfiguration.

Nu kan vi starta mysql.

```
kubectl apply -f mysql-deployment.yml

kubectl get pods -l app=mysql
NAME                     READY   STATUS    RESTARTS   AGE
mysql-647b4cc668-nwmnm   1/1     Running   0          22s
```

Ni kan testa koppla upp er till databasen.

```
kubectl run -it --rm --image=mysql:5.7 --restart=Never mysql-client -- mysql -h mysql -pmy-super-secret-root-password

mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| microblog          |
| mysql              |
| performance_schema |
| sys                |
+--------------------+
5 rows in set (0.00 sec)

mysql>
```

Nu har vi en database i Kubernetes vi kan koppla Microbloggen till.

<!-- ```
kubectl delete deployment,svc mysql
kubectl delete pvc mysql-pv-claim
kubectl delete pv mysql-pv-volume
``` -->



#### Microblog deployment {#microblog}

Nästa steg är då att skapa en deployment för Microblogen, än så länga i kursmomentet har ni bara följt med och inte behövt tänka själva. Ni borde ha lärt er tillräckligt för att skapa en service och deployment för Microblogen. Skriv konfigurationen i en fil med namnet `microblog-deployment.yml`. Den ska ha 2 replicas, så att det alltid finns två pods rullande som kan hantera trafik.

Kolla i er `docker-compose.yml` för vilka env variabler ni behöver för att starta containern. Ni kan använda `mysql` istället för en IP till database i env variabeln `DATABASE_URL`.

För att felsöka kan ni använda följande kommandon och UI:t.

```
kubectl get po

kubectl decribe po

kubectl describe deployment microblog

kubectl logs <pod-name>
```

Nästa steg är att sätta upp https och koppla domän till microbloggen, men ni kan redan nu skapa en LoadBalancer eller NodePort Service till micrblogen så att den får en extern-ip. Ni kan få fram URL:en till microblogen med `kubectl get svc` och kolumnen `EXTERNAL-IP`. För mig var det `a0c6658f7626f461f925fa51f0a05c54-735889698.us-east-1.elb.amazonaws.com:5000`. [Här](https://medium.com/google-cloud/kubernetes-nodeport-vs-loadbalancer-vs-ingress-when-should-i-use-what-922f010849e0) kan ni läsa en kort sammanfattning om de olika services som finns och skillnaden.



#### Treafik (HTTPS)

https://medium.com/@geraldcroes/kubernetes-traefik-101-when-simplicity-matters-957eeede2cf8
https://helm.sh/docs/intro/quickstart/



### Kubernetes i produktion {#production}

Läs följande artiklar som tar upp olika saker man behöver tänka när man ska köra K8s i produktion:

- [Kubernetes in production vs. Kubernetes in development: 4 myths](https://enterprisersproject.com/article/2018/11/kubernetes-production-4-myths-debunked)

- [7 Key Considerations for Kubernetes in Production](https://thenewstack.io/7-key-considerations-for-kubernetes-in-production/)

Kolla på "Running Kubernetes in Production: A Million Ways to Crash Your Cluster" där Henning Jacobs från websidan [Zalando.se](https://www.zalando.se/) pratar om hur de använder Kubernetes och vad de lärt sig av att köra det i produktions miljön.

[YOUTUBE src="pKFQuED_2kg" caption="Running Kubernetes in Production: A Million Ways to Crash Your Cluster"]



### Video {#video}

Det finns generellt kursmaterial i video form.

1. Kursen innehåller föreläsningar som spelas in och därefter läggs i spellistan "[Devops streams](https://www.youtube.com/playlist?list=PLKtP9l5q3ce90068cUPVMcPguKtFAqnvi)".

1. I "[kursen devops](https://www.youtube.com/playlist?list=PLKtP9l5q3ce8s67TUj2qS85C4g1pbrx78)" hittar du alla videor som är kopplade till kursmomentet, de börjar på 6xx i namnet.



Uppgifter  {#uppgifter}
-------------------------------------------

Följande uppgifter skall utföras och resultatet skall redovisas via me-sidan.

1. Försäkra dig om att du har pushat repot med din senaste kod och taggat din inlämning med version v6.0.0.



Resultat & Redovisning  {#resultat_redovisning}
-----------------------------------------------

Läs [instruktionen om hur du skall redovisa](./../redovisa).

Se till att följande frågor besvaras i texten:

1. Vad är ert första intryck av Kubernetes? Skulle ni vilja använda det i framtiden?

1. Vad är Container orchestration?

1. Varför är det svårare med stateful applikation jämfört med stateless i k8s?

1. Vad ska vi tänka på när vi designar ett projekt som ska köras i K8s?

1. Vad är viktigt att tänka på när man ska köra K8s i produktion?

1. Hur känns det efter att ni använt K8s, var det lika svårt som alla skriver/säger att det är?
