---
author:
    - aar
revision:
    "2019-10-15": "(A, aar) Första versionen."
...
Kmom05: DevSecOps
==================================

Devops handlar om att brygga kommunikationsbarriärer, det är stort fokus på development och operations teams men även security behöver inkluderas för att det ska bli ett bra resultat. Inom devops ska det gå snabbt och man ska ta risker och då är security teamets roll att fungera som skyddsnät och skydda företagets tillgångar.



<!-- more -->

[FIGURE src="img/devops/devops-security.png" caption="Hur det inte ska se ut när man kör devops."]

Vi har redan gjort några saker för att förbättra vår säkerhet, vi har stängt av ssh inloggning som root användare, vi har en ny användare i database bara för microbloggen, vi pushar inte AWS nycklarna till GitHub och vi sparar känslig information som behövs till CircleCi som hemlig miljövariabler.

[WARNING]	

 **Kursutveckling pågår**	

 Kursen ges hösten 2019 läsperiod 2.

[/WARNING]
<small><i>(Detta är instruktionen för kursmomentet och omfattar det som skall göras inom ramen för kursmomentet. Momentet omfattar cirka **20 studietimmar** inklusive läsning, arbete med övningar och uppgifter, felsökning, problemlösning, redovisning och eftertanke. Läs igenom hela kursmomentet innan du börjar jobba. Om möjligt -- planera och prioritera var du vill lägga tiden.)</i></small>



### Vad är DevSecOps {#devsecops}

https://www.newcontext.com/what-is-devsecops/


### Stuff

Säkra Docker i CircleCi? (docker benchmark)
Säkra infrastruktur (deployer node, ssh_scan?(s.100+)) nämn audit cloud infrastructure (s.341+)
snyk/Zap i CircleCi
Databas, får bara ansluta från app server. (bra infp s.108+)
Bättre https? (s.138+) hsts, https://testssl.sh/ / ssllabs.com
Säkra ci/cd kedja s148+ 


dependency scanning (snyk)
User management (hashicorp vault/mozilla sops)


https://cheatsheetseries.owasp.org/cheatsheets/Docker_Security_Cheat_Sheet.html
Docker Linux Security Module (seccomp, AppArmor, or SELinux)?
docker analysis https://cheatsheetseries.owasp.org/cheatsheets/Docker_Security_Cheat_Sheet.html#rule-9---use-static-analysis-tools

zap s.~50?
 zap baseline https://blog.mozilla.org/security/2017/01/25/setting-a-baseline-for-web-security-controls/ s.48
Säkra AWS miljön, vpc och access node. Hur blir det med ansible-deploy om de inte kan ssh in på app noden??!?!?
    multi factor authentic med duo security, på deploy noden? s 88-89

Läs [Container security best practices](https://logz.io/blog/container-security-best-practices/) för en kort översikt av några saker att tänkta på när man jobbar med containrar i produktion. De pratar om Immutable deployment, alltså att bygga ny instance vid varje deploy och ta bort den gamla. Vår infrastructure är inte mogen nog för det. Vår monitoring är för simpel och vi har inte satt upp någon logging monitoring som kan analysera för säkerhetsintrång.

https://github.com/freach/docker-image-policy-plugin whitelist docker images för pull

Om vi inte hade haft AWS student konton hade vi använt oss av Identity and Access Management (IAM). Med det kan vi kontrollera vem som har rättigheter att skapa/ändra/radera resurser på AWS. Vi kan t.ex. skapa en ny användare som används av `gather_aws_instances.yml` playbooken och den användaren har bara rättigheter att läsa data från AWS. Då hade vi inte varit lika sårbara om vi hade råkat läcka AWS nycklarna.

<!-- https://kryptera.se/t/elk-stack/ ossec 
https://www.redhat.com/en/topics/devops/what-is-devsecops
https://techbeacon.com/security/6-devsecops-best-practices-automate-early-often
https://techbeacon.com/security/10-top-open-source-tools-docker-security
https://cheatsheetseries.owasp.org/cheatsheets/Docker_Security_Cheat_Sheet.html#rule-9---use-static-analysis-tools


https://www.denimgroup.com/resources/blog/2019/09/getting-started-questions/
https://circleci.com/blog/adding-application-and-image-scanning-to-your-cicd-pipeline/
https://app.snyk.io/org/andreasarne/manage/billing
https://www.aquasec.com/use-cases/devsecops-automation/
https://vaddy.net/
https://github.com/aquasecurity/trivy#comparison-with-other-scanners
https://www.qualys.com/community-edition/
https://github.com/hadolint/hadolint
https://github.com/ottomatica/opunit
https://sonarcloud.io/dashboard?id=AndreasArne_redovisnings-sida
https://github.com/docker/docker-bench-security
https://github.com/OWASP/Container-Security-Verification-Standard
-->


### SAST vs. DAST {#sast-dast}

Static Application Security Testing (SAST), eller bara Static Code Analysis, är att analysera källkoden för kända säkerhetsrisker och sårbarheter utan att exekvera programmet. SAST är bra på att fånga upp programmeringsmisstag tidigt i utvecklingsprocessen av en applikation. Vi kommer använda [Bandit](https://github.com/PyCQA/bandit) för att utföra SAST på vår Python kod.

Dynamic Application Security Testing (DAST) letar efter sårbarheter i webapplikationer genom att skanna och utföra attacker på applikationen. Vi kommer använda [Zap](https://www.owasp.org/index.php/OWASP_Zed_Attack_Proxy_Project) för att utföra DAST på Microbloggen.

Läs [SAST vs. DAST](https://www.synopsys.com/blogs/software-security/sast-vs-dast-difference/) för en jämförelse av de två och vad de är bra på.



#### Bandit {#bandit}

[Bandit](https://github.com/PyCQA/bandit) är ett linting verktyg (som pylint) fast det analyserar istället säkerhet i koden. Ladda ner Bandit och lägg till det i `requirements/test.txt` så att det är en del av paketen för testning. Testa att köra Bandit med `bandit -r app` så att det bara analyserar koden för applikationen, vi behöver inte köra det mot testerna.

Om ni har kodrader som ni anser är false-positivs kan ni lägga `# nosec` som en kommentar i slutet på den raden. Då ignorerar Bandit den raden. Det går även att hoppa över hela tester, ni kan skapa filen `.bandit.yml` och i den skriva:

```
skips: [<'list of tests'>]
```

För att Bandit ska läsa konfigurationen kör Bandit med `bandit -c .bandit.yml -r app`. Om ni får några fel kan ni antingen fixa felet, lägga till `# nosec` eller hoppa över regeln helt. Analysera felet och gör ett aktivt val över vad som är en passande åtgärd på felet.

Lägg till ett make target I Makefile som kör Bandit på `app` mappen. Gör sen så att Bandit är en del av testerna som körs i Dockerfile_test och som en del av CircleCi.



### Zap {#zap}

[Zap](https://www.owasp.org/index.php/OWASP_Zed_Attack_Proxy_Project)/[Zap på Github](https://github.com/zaproxy/zaproxy) är ett verktyg som kan testa väldigt många saker, speciellt från OWASP10. Det går att köra det både automatiskt och manuellt.

Vi kommer att nöja oss med att köra deras [Baseline tester](https://github.com/zaproxy/zaproxy/wiki/ZAP-Baseline-Scan) på Microbloggen, då utförs inga aktiva attacker, den bara skannar websidan. Mozilla har ett [blogginlägg](https://blog.mozilla.org/security/2017/01/25/setting-a-baseline-for-web-security-controls/) där de förklarar hur ni kan köra Zap med baseline testerna. Följ den för att testa köra den mot er Microblog, ni behöver inte lägga till det i CircleCi.

Det går även att köra Zap mot er lokala miljö, men då måste ni sätta nätverk när ni startar containern:

<!-- `docker run -t owasp/zap2docker-stable zap-baseline.py -t https://<domain>` -->
```
docker run --net host owasp/zap2docker-weekly zap-baseline.py -t http://0.0.0.0:8000
```

Fixa minst 5 valfria varningar från Zap, beskriv vilka och vad ni gjorde i redovisningstexten. Det lättaste sättet att fixa dem är att logga in på AWS instansen och ändra i Nginx konfigurationen, ladda om Nginx och köra Zap igen för att se om varningen försvann.

Egentligen skulle vi lagt till Zap i CircleCi men vi har ingen staging miljö att köra den mot. Så vi får nöja oss med att köra det manuellt innan push. Lägg till ett make target i Makefilen som kör Zap mot er Microblog, döp det till `Zap`.



### Lästips {#lastips}

1. [Zapping the top 10](https://www.owasp.org/index.php/ZAPpingTheTop1), hur ni kan använda Zap för att testa OWASP10 sårbarheterna.



### Video {#video}

Det finns generellt kursmaterial i video form.


1. Kursen innehåller föreläsningar som spelas in och därefter läggs i spellistan "[Devops streams](https://www.youtube.com/playlist?list=PLKtP9l5q3ce90068cUPVMcPguKtFAqnvi)".

1. I "[kursen devops](https://www.youtube.com/playlist?list=PLKtP9l5q3ce8s67TUj2qS85C4g1pbrx78)" hittar du alla videor som är kopplade till kursmomentet, de börjar på 5xx i namnet.



### Uppgifter {#uppgifter}

Följande uppgifter skall utföras och resultatet skall redovisas via me-sidan.

1. Vad ska bandit köras som, make validate eller test? och som ett eget target? Lägg till det så sker när kör test docker.

1. Fixa minst 5 varningar från Zap testerna. Glöm inte bort att uppdatera er Nginx config i Ansible!

1. Försäkra dig om att du har pushat repot med din senaste kod och taggat din inlämning med version v5.0.0.



Resultat & Redovisning  {#resultat_redovisning}
-----------------------------------------------

Läs [instruktionen om hur du skall redovisa](./../redovisa).

Se till att följande frågor besvaras i texten:

1. Ändrade ni något i er kod efter ni kört Bandit? Använder ni `# nosec` för att ignorera någon kod eller skippa något test? Varför?

1. Beskriv vilka Zap varningar ni fixade och hur ni löste dem.