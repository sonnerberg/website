---
author:
    - aar
revision:
    "2019-10-15": "(A, aar) Första versionen."
...
Kmom05: Continuous Security
==================================

Devops handlar om att brygga kommunikationsbarriärer, det är stort fokus på development och operations teams men även security behöver inkluderas för att det ska bli ett bra resultat. Inom devops ska det gå snabbt och man ska ta risker och då är security teamets roll att fungera som skyddsnät och skydda företagets tillgångar.



<!-- more -->

[WARNING]	

 **Kursutveckling pågår**	

 Kursen ges hösten 2019 läsperiod 2.

[/WARNING]
<small><i>(Detta är instruktionen för kursmomentet och omfattar det som skall göras inom ramen för kursmomentet. Momentet omfattar cirka **20 studietimmar** inklusive läsning, arbete med övningar och uppgifter, felsökning, problemlösning, redovisning och eftertanke. Läs igenom hela kursmomentet innan du börjar jobba. Om möjligt -- planera och prioritera var du vill lägga tiden.)</i></small>



Säkra Docker

Säkra CI/CD flödet
static code analasys
dynamic --||--
dependency scanning
Security tests (typ enhetstester som testar säkerhet)
User management (heter det helm? vault tjänst som kan hämta ssh nycklar och annan information från)
splunk?


https://cheatsheetseries.owasp.org/cheatsheets/Docker_Security_Cheat_Sheet.html
Docker Linux Security Module (seccomp, AppArmor, or SELinux)?
docker analysis https://cheatsheetseries.owasp.org/cheatsheets/Docker_Security_Cheat_Sheet.html#rule-9---use-static-analysis-tools

Säkra AWS miljön, vpc och access node

Läs [Container security best practices](https://logz.io/blog/container-security-best-practices/) för en kort översikt av några saker att tänkta på när man jobbar med containrar i produktion. De pratar om Immutable deployment, alltså att bygga ny instance vid varje deploy och ta bort den gamla. Vår infrastructure är inte mogen nog för det. Vår monitoring är för simpel och vi har inte satt upp någon logging monitoring som kan analysera för säkerhetsintrång.

https://github.com/freach/docker-image-policy-plugin whitelist docker images för pull

Fail2Ban

Om vi inte hade haft AWS student konton hade vi använt oss av Identity and Access Management (IAM). Med det kan vi kontrollera vem som har rättigheter att skapa/ändra/radera resurser på AWS. Vi kan t.ex. skapa en ny användare som används av `gather_aws_instances.yml` playbooken och den användaren har bara rättigheter att läsa data från AWS. Då hade vi inte varit lika sårbara om vi hade råkat läcka AWS nycklarna.

<!-- https://kryptera.se/t/elk-stack/ ossec 
https://www.redhat.com/en/topics/devops/what-is-devsecops
https://techbeacon.com/security/6-devsecops-best-practices-automate-early-often
https://techbeacon.com/security/10-top-open-source-tools-docker-security
https://cheatsheetseries.owasp.org/cheatsheets/Docker_Security_Cheat_Sheet.html#rule-9---use-static-analysis-tools

Text om virtualisering och olika tekniker, hur det fungerar?
-->


Staging miljö? Vad för tester då?

Labbmiljön  {#labbmiljo}
---------------------------------

Ingen labbmiljö än så länge!



Läs & Studera  {#lasanvisningar}
---------------------------------

*(ca: 4-6 studietimmar)*



### Bok {#bok}

Kolla in följande.



### Artiklar {#artiklar}

Kika igenom följande artiklar.



### Video {#video}

Det finns generellt kursmaterial i video form.


1. Kursen innehåller föreläsningar som spelas in och därefter läggs i spellistan "[Devops streams](https://www.youtube.com/playlist?list=PLKtP9l5q3ce90068cUPVMcPguKtFAqnvi)".

1. I "[kursen devops](https://www.youtube.com/playlist?list=PLKtP9l5q3ce8s67TUj2qS85C4g1pbrx78)" hittar du alla videor som är kopplade till kursmomentet, de börjar på 5xx i namnet.



Övningar & Uppgifter  {#ovningar_uppgifter}
-------------------------------------------

### Övningarr {#ovningar}

Gör följande övningar, de behövs normalt för att klara uppgifterna..



### Uppgifter {#uppgifter}

Följande uppgifter skall utföras och resultatet skall redovisas via me-sidan.


1. Försäkra dig om att du har pushat repot med din senaste kod och taggat din inlämning med version v5.0.0.



Resultat & Redovisning  {#resultat_redovisning}
-----------------------------------------------

Läs [instruktionen om hur du skall redovisa](./../redovisa).

Se till att följande frågor besvaras i texten:

...