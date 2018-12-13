---
author: efo
category:
    - ramverk2
    - verktyg
revision:
    "2018-11-07": "(A, efo) Första utgåvan för ramverk2 version 2 av kursen."
...
GitHub Education Pack och en server på Digital Ocean
==================================

[FIGURE src=/image/ramverk2/do.png class="right"]

Vi kommer i denna artikel titta på hur vi skaffar oss en Linux-baserad server på Digital Ocean genom att använda GitHub Education Pack.

<!--more-->

Vi använder GitHub Education Pack för att skaffa en gratis server på Digital Ocean och en del andra verktyg, som är bra att ha. Sedan skaffar vi en server och ser till att säkra upp denna servern genom att använda SSH-nycklar för inloggning, brandväggen `ufw` och verktyget `fail2ban`.



Förutsättning {#pre}
--------------------------------------

Du har din student e-postadress nära till hands då den behövs för att få tillgång till GitHub Education Pack.



GitHub Education Pack {#gep}
--------------------------------------

För att få tillgång till rabatter och rabattkoder som erbjuds i [GitHub Education Pack](https://education.github.com/pack) behöver du GitHub veta att du är student. Gå till den länkade sidan och tryck på den blåa knappen "Get your Pack". Viktigt att du använder din student mail när du registrerar dig då mailen måste vara kopplat till en undervisningsinstitution.



Digital Ocean {#do}
--------------------------------------

När du är verifierad via GitHub får du tillgång till en rabattkod för Digital Ocean. Efter det går du till [Digital Ocean Sign Up](https://cloud.digitalocean.com/registrations/new) och skapar ett konto. Du behöver ange ett kreditkort, men vi kommer sedan använda rabattkoden så det kommer inte kosta något.

När du har skapat kontot gå till Account längst upp till höger under din användare logga. Gå sedan till Billing fliken och scrolla ner till Promo Code. Här lägger du in rabattkoden du fick från Github Education Pack när du tryckte på länken 'request your offer code'.

Gå sedan till första sidan och tryck 'New Droplet'. Instruktioner i kommande stycken och resten av kursen kommer utgå från en Debian Stretch droplet, så en stark rekommendation är att välja en sån droplet. Jag rekommenderar att ni kör en 10$/månad droplet, då man får bra prestanda och samtidigt inte använder hela rabatten under kursens gång. Välj Frankfurt eller London som region och lägg till din `id_rsa.pub` SSH nyckel så du kan logga in på servern.



Första 10 minuter på en server {#first10}
--------------------------------------

Med utgångspunkt i artiklar som [My First 5 Minutes On A Server; Or, Essential Security for Linux Servers](https://plusbryan.com/my-first-5-minutes-on-a-server-or-essential-security-for-linux-servers) och [My First 10 Minutes On a Server - Primer for Securing Ubuntu](https://www.codelitt.com/blog/my-first-10-minutes-on-a-server-primer-for-securing-ubuntu/) ska vi i följande stycke titta på hur vi säkrar upp en Linux-baserad server av Ubuntu eller Debian variant.

### Lösenord

Än så länge har vi inte ens ett lösenord till vår `root` användare så låt oss se till att sätter ett lösenord. Välj ett säkert lösenord och med säkert lösenord menas ett slumpat och komplext lösenord. Jag rekommenderar starkt att använda en Password Manager och skapa lösenordet med hjälp av denna Password Manager inställt på den mest komplexa inställningen du kan hitta. För Mac och Linux rekommenderas [pass](https://www.passwordstore.org) och för Windows verkar [LastPass](https://www.lastpass.com) vara det mest använda gratis programmet som finns.

När du har skapat ett slumpmässigt och komplext lösenord skriv följande kommando och följ instruktionerna.

```bash
passwd
```



### Uppdatera servern

Nästa steg är att uppdatera serverns programvara till senaste version genom att använda verktyget `apt-get`.

```bash
apt-get update
apt-get upgrade
```



### Skapa din egen användare

Vi vill aldrig logga in som `root` då `root` har tillgång till för mycket. Så vi skapar en egen användare `deploy` med följande kommandon. Du kan byta ut `deploy` mot vad som helst, men då ska du göra det i alla följande kommandon.

```bash
useradd deploy
mkdir /home/deploy
mkdir /home/deploy/.ssh
chmod 700 /home/deploy/.ssh
```

Vi passar på att i samma veva ställa in vilken förvald terminal vår nya använda ska använda, vi väljer `bash` då vi är vana vid den.

```bash
usermod -s /bin/bash deploy
```



### Stänga av inloggning med lösenord

Lösenord kan knäckas.

Därför använder vi istället SSH nycklar för att autentisera oss mot servern.



Ett domän till din server {#domain}
--------------------------------------

Som en del av Github Education Pack får du som student även ett domän-namn på top-domänen .me gratis under ett år.



Avslutningsvis {#avslutning}
--------------------------------------

Vi har i denna artikel skaffat oss GitHub Education Pack, en gratis server på Digital Ocean och säkrat upp denna servern.
