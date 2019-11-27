---
author:
    - aar
revision:
    "2019-10-15": "(A, aar) Första versionen."
...
Kmom04: Monitoring
==================================

Nu när vi har ett system uppe och rullande behöver vi veta när något går fel, vi ska övervaka hela produktionsmiljön och alla dess delar.



<!-- more -->

[FIGURE src="https://upload.wikimedia.org/wikipedia/commons/d/d2/IoT_environmental_monitoring_system_solution_-_Overview.jpg" caption="Överblick av olika delar som kan ingå i ett system med övervakning."]


<small><i>(Detta är instruktionen för kursmomentet och omfattar det som skall göras inom ramen för kursmomentet. Momentet omfattar cirka **20 studietimmar** inklusive läsning, arbete med övningar och uppgifter, felsökning, problemlösning, redovisning och eftertanke. Läs igenom hela kursmomentet innan du börjar jobba. Om möjligt -- planera och prioritera var du vill lägga tiden.)</i></small>




<!-- https://old.reddit.com/r/devops/comments/afqye3/whats_your_monitoring_and_alerting_stack_look_like/
https://itnext.io/deploy-elk-stack-in-docker-to-monitor-containers-c647d7e2bfcd
 -->
 
<!-- Elastic stack
https://logz.io/blog/10-elasticsearch-concepts/
https://github.com/nickjj/ansible-docker
https://www.guru99.com/elk-stack-tutorial.html
    Ny instance med t2.small
    Ny SG
    RP i LB nod för ELK
    Installera Beats på övriga instancer
    +1 app instance?
    Om de kör provision igen för att bara få upp ELK kommer det även starta upp en till av varje annan!!
    load balancer - https://galaxy.ansible.com/entercloudsuite/filebeat
        https -> http, enabled -> started?
    galaxy https://blog.ktz.me/getting-started-with-ansible-galaxy/
 -->


### Monitoring {#monitoring}

När system ligger utspridda på virtuelle servrar jorden runt är det inte lätt att hålla koll på att alla servrar och system hela tiden är igång. Här kommer infrastruktur monitoring in i bilden men vi kan också ha application monitoring där vi övervakar metrics från system. T.ex. hur många request varje server har fått eller hur många 404 requests.

Läs Microsofts förklaring av [Monitoring](https://docs.microsoft.com/en-us/azure/devops/learn/what-is-monitoring).

Läs sen [Monitoring in a DevOps world](https://queue.acm.org/detail.cfm?id=3178371).



### Log management {#log}

Log management är processen av att samla in, lagra, hantera och analysera loggar från infrastruktur, system och applikation. Det är ett väldigt brett ämne då typ allt genererar loggar av något slag och system för att sköta log hantering är väldigt avancerade. Läs [What is log management](https://www.tripwire.com/state-of-security/security-data-protection/security-controls/what-is-log-management/) för att få en överblick av delarna som ingår i log management. Läs sen om vilken användning olika roller har av log management i [Why is log management important](https://www.graylog.org/post/why-is-log-management-important).

Läs också [ELK stack tutorial](https://www.guru99.com/elk-stack-tutorial.html) för en överblick av ett av de mest populära systemen för Log management.



### Application performance monitoring (APM) {#apm}

APM kan även kallas Application Performance Management (också APM), enligt vissa är det skillnad. APM är att övervaka, hantera och diagnosera prestanda, tillgänglighet och användare upplevelse av applikationer. Avancerade program används för att göra om data till "business value". Läs [What is application performace monitoring](https://www.eginnovations.com/blog/what-is-application-performance-monitoring/).



### Observability {#observability}

På senare år har det även börjat talas mycket om Observability vilket hänger ihop med monitoring. Vi kan se monitoring som att ha kolla på hälsan av våra system medan observability är att ha djup insikt i hur våra system beter sig. Observability ska hjälpa oss hitta fel och problem. Läs [Observability sv. Monitoring](https://dzone.com/articles/observability-vs-monitoring).

Om ni vill kan ni även kolla på [What Does the Future Hold for Observability?](https://www.youtube.com/watch?v=MkSdvPdS1oA)



### Prometheus och Grafana {#prometheus}

Vi ska använda oss av [Prometheus](https://prometheus.io/), ett väldigt populärt verktyg för att lagra tidsserie data och visualisera data. Prometheus har inbyggt stöd för att visa simpla grafer för data men oftast använder man det tillsammans med externa visualiseringsverktyg. Vi ska använda [Grafana](https://grafana.com/) för att bygga dashboards med grafer och diagram över datan från Prometheus.

Börja med att läsa [Prometheus Monitoring : The Definitive Guide in 2019](https://devconnected.com/the-definitive-guide-to-prometheus-in-2019/) för en överblick av vad Prometheus är och vad det innehåller.

När ni sen har lite kolla på hur Prometheus fungerar ska ni testa installera Prometheus, Grafana och koppla ihop dem. Men först behöver ni någonstans att kör verktygen, kolla på följande video för att uppdatera Ansible skripten för att skapa servrar på AWS:

[YOUTUBE src=xpY0Z956MZE caption="Skapa en Monitoring instance på AWS med Ansible"]

Följ nu guiden [Complete Node Exporter Mastery with Prometheus](https://devconnected.com/complete-node-exporter-mastery-with-prometheus/) som visar hur ni kan övervaka resurserna på AWS instansen som ni installerar Prometheus på. OBS! När ni sätter `scrape_interval` sätta inte mindre än 30 sekunder, era AWS instanser har begränsat med resurser, vi kan inte gå helt Crazy!  
Ni ska senare göra en Ansible playbook för att sätta upp Prometheus och Grafana, då kan ni installera det hur ni vill. Men börja med att följa guiden för att lära er verktygen först. 



### MySQL {#mysql}

Vi vill ha lite koll på vad som händer med databasen och det finns så klart en exporter för MySQL också. Jag sätter upp min exporter som en Docker container, om ni inte vill göra det kan ni följa [Complete mysql daschboard with Grafan and Prometheus](https://devconnected.com/complete-mysql-dashboard-with-grafana-prometheus).

Börja med att logga in på er databas instans. Sen behöver vi ha root lösenordet till er MySQL instans, om du inte sätter något root lösenord när du starta mysql containern kan vi hitta det i Dockers loggar för containern.

```
docker logs <mysql_container> 2>&1 | grep GENERATED
```

Sen kan vi logga in i databasen och skapa en ny användare för mysql_exporter att logga in som. Men vi måste först ändra root lösenordet innan MySQL låter oss skapa nya användare.
```
docker exec -it <container> mysql -uroot -p

mysql> ALTER USER 'root'@'localhost' IDENTIFIED BY '<password>'; # skippa detta steget om du sätter root lösenord när du skapar containern.

mysql> CREATE USER 'exporter'@'%' IDENTIFIED BY '<password>' WITH MAX_USER_CONNECTIONS 3;
mysql> GRANT PROCESS, REPLICATION CLIENT, SELECT ON *.* TO 'exporter'@'%';
mysql> GRANT SELECT ON performance_schema.* TO 'exporter'@'%';
```

Nu kan vi starta upp en `mysqld-exporter` container och koppla till databasen.

```
docker pull prom/mysqld-exporter

docker run -d \
  -p 9104:9104 \
  --network host \
  -e DATA_SOURCE_NAME="exporter:<password>@(localhost:3306)/" \
  --restart always\
  prom/mysqld-exporter:latest \
  --collect.auto_increment.columns \
  --collect.binlog_size \
  --collect.engine_innodb_status \
  --collect.engine_tokudb_status \
  --collect.global_status
```

`--collect...` är flaggor för vilken data som exportern ska samla in. Det finns väldigt många fler och ni kan läsa om dem på [GitHub](https://github.com/prometheus/mysqld_exporter#collector-flags).

Testa så det fungera i terminalen med `wget localhost:9104/metrics` om ni får ner en fil med data så fungerar det. Då behöver ni öppna upp porten på AWS så Prometheus kommer åt den.

Nu kan ni konfigurera Prometheus att hämta datan, lägg till följande i er Prometheus konfiguration:

```
scrape_configs:
  - job_name: 'mysql'
    static_configs:
            - targets: ['<database_host_ip>:9104']
```

Starta om Prometheus och gå sen in på GUI:ts webbsida och testa hämta datan `mysql_exporter_scrapes_total` för att kolla att kopplingen fungerar.

Följ sen [Create the MySQL dashboard with Grafana](https://devconnected.com/complete-mysql-dashboard-with-grafana-prometheus/#IV_Create_the_MySQL_dashboard_with_Grafana) för att skapa en MySQL Overview dashboard kopplad till datan.

Glöm inte att öppna portar i AWS så Prometheus kommer åt mysql_exporter.




#### Nginx {#nginx}

Det finns en officiel exporter för [Nginx](https://github.com/nginxinc/nginx-prometheus-exporter) som använder sig utav [ngx_http_stub_status_module](http://nginx.org/en/docs/http/ngx_http_stub_status_module.html) för att samla data. Tyvärr behöver man ha Nginx Plus för att få ut mer intressant data som hur många 4xx/5xx request man får in. Nu har vi inte Plus versionen och får nöja oss med att kunna se att servern är igång och hur många requests servern har fått.

För att exportern ska fungera behvöer ni ha `status_module` aktiverad i Nginx. Ni kan kolla det är aktiverat med kommandot `sudo nginx -V 2>&1 | grep -o with-http_stub_status_module`, om ni får utskrift med `with-http_stub_status_module` så är ni good to go! För mig vad den aktiverad i den vanliga Nginx man installerar med apt-get.

När modulen är aktiverad kan ni följa [Monitoring nginx with Prometheus and Grafana](https://dimitr.im/monitoring-nginx-with-prometheus-and-grafana), den installerar exportern med Docker, om ni inte vill det kan ni installera den [som en binary](https://github.com/nginxinc/nginx-prometheus-exporter#running-the-exporter-binary). Artikeln är lite utdaterad så docker kommandot fungerar inte, använd istället `docker run   -p 9113:9113   nginx/nginx-prometheus-exporter:0.4.2 -nginx.scrape-uri=https://<domännamn>/metrics -nginx.retries=10 -nginx.ssl-verify=false -web.telemetry-path=/prometheus` och i Nginx lägg `location` blocket i er `load-balancer` konfiguration i https server blocket.

Glöm inte att öppna portar i AWS.



#### Gunicorn {#gunicorn}

I Gunicorn kan vi få ut mer intressant data, vi kan bl.a. se request duration och hur många av de olika request typerna vi får. Jobba igenom [Monitoring Gunicorn with Prometheus](https://medium.com/@damianmyerscough/monitoring-gunicorn-with-prometheus-789954150069) för att sätta upp flödet. När ni följer guiden behöver ni tänka på att ni kör Gunicorn i Docker, detta påverkar hur ni behöver köra det. Tänk på följande när ni gör guiden:

- När ni ska starta docker containern behöver ni lägga till ett "-" i argumentet till statsd, `docker run -dP --net=host -v ${PWD}/statsd.conf:/statsd/statsd.conf prom/statsd-exporter "--statsd.mapping-config=/statsd/statsd.conf"`.

- Gunicorn har ett plugin som behöver koppla upp sig mot port 9125 på StatsD containern, det är så statsD får datan. För att Gunicorn ska kunna komma åt statsD's portar behöver de köra på samma nätverk. Då har ni två val, antingen skapar ni ett nätverk i Docker och köra båda containers på det. Det andra alternativet är att göra som i guiden där statsD containern körs på `host` nätverket, då behöver ni också köra Microblog på det nätverket. Nätverket `host` är speciellt, man kan inte öppna portar för containern manuellt utan alla portar är tillgängliga automatiskt, vilket betyder att ni inte behöver typ `-p 8000:5000` när ni startar containern. Om ni kör på `host` nätverket glöm inte försäkra er om att Nginx är kopplad till rätt port, så att hur ni kör Gunicorn i Docker inte ändras från 8000 till 5000 och ni inte ändrar till det också i Nginx.  

- För att förtydliga, statsd containern använder port 9102 för att skicka data, prometheus ska koppla upp sig på denna, och port 9125 för att ta emot data, skickas från gunicorn.

- I slutet av artikeln finns en gömd länk som visar kod för en [Grafana Gunicorn Dashboard](https://gist.github.com/dmyerscough/59896aa752ba48794d2aef4c7a0fdd6e).

Glöm inte att öppna portar i AWS.



#### Ansible {#ansible}

Skapa en ny playbook för att sätta upp Prometheus och Grafana och lägg till alla exporters i respektive playbook. I er Prometheus config behöver ni koppla alla exporters till ip addresser, ni kan använda `{{ groups['<hostname>'][0] }}` för att få ut en ip i Ansible.



### Video {#video}

Det finns generellt kursmaterial i video form.

1. Kursen innehåller föreläsningar som spelas in och därefter läggs i spellistan "[Devops streams](https://www.youtube.com/playlist?list=PLKtP9l5q3ce90068cUPVMcPguKtFAqnvi)".

1. I "[kursen devops](https://www.youtube.com/playlist?list=PLKtP9l5q3ce8s67TUj2qS85C4g1pbrx78)" hittar du alla videor som är kopplade till kursmomentet, de börjar på 4xx i namnet.



### Uppgifter {#uppgifter}

Följande uppgifter skall utföras och resultatet skall redovisas via me-sidan.

1. Ni har en till instans i er AWS infrastruktur som kör Prometheus och Grafana. Lägg till två Reverse Proxy i er Nginx konfiguration, en till Prometheus interfacet och en till Grafana. Länka till dem i er redovisningstext.

1. Ha en Dashboard för varje exporter vi gått igenom, Nginx, Mysql, Node_exporter och Gunicorn.

1. Lägg till en Ansible playbook för Prometheus och Grafana. Lägg till att installera och starta alla olika exporters i respektive playbook.

<!-- 1. Skapa larm i Prometheus som varnar om någon Docker container, Nginx eller instans inte längre är igång. Skapa även ett larm som varnar om minnet på hårddisken på Prometheus instansen har mindre än 5G kvar. -->
<!-- Hitta ett sätt som kan användas för att temporärt tar plats på hårddisken så larmet kan testas. -->

1. Försäkra dig om att du har pushat repot med din senaste kod och taggat din inlämning med version v4.0.0.



Resultat & Redovisning  {#resultat_redovisning}
-----------------------------------------------

Läs [instruktionen om hur du skall redovisa](./../redovisa).

Se till att följande frågor besvaras i texten:

1. Beskriv vad som menas med Monitoring, olika saker som brukar övervakas och vad det används till.

1. Beskriv Log management och vad det används till.

1. Beskriv APM vad det används till.

1. Beskriv Observability och försök koppla det till ovanstående frågor.

1. Hur var storleken på detta kmom? Finns det tid att göra mer?
