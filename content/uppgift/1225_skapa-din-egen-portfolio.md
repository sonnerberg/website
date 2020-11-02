---
author: nik
category:
    - kurs/design-v3
revision:
    "2020-10-12": (B, nik) Uppdaterad inför ht20
    "2020-08-26": (A, nik) Draft
...
Skapa din egen portfolio-sida
===================================

Du skall sätta samman en portfolio-sida till kursen design. För att göra det skall du använda en förberedd kopia av ramverket [Pico](http://picocms.org/) med innehåll anpassat till kursen design.

Du behöver installera din portfolio, fylla den med innehåll och sedan lägga till egen style med hjälp utav CSS.

Du skall också skapa ett Git-repo av din portfolio-sida och ladda upp det till Github.

<!--more-->

Förkunskaper {#forkunskaper}
-----------------------

Du har en labbmiljö som motsvarar [labbmiljön för kursen design](kurser/design-v3/kmom01#labbmiljo).


Introduktion och förberedelse {#intro}
-----------------------

Gör följande steg för att förbereda dig inför uppgiften.

### Kopiera från example/portfolio

Det finns en förberedd installation som är specifik för kursen design och dess portfolio-sida. Kopiera den och installera det som behövs med composer

```
# Stå i rooten av kursrepot
rsync -ravd example/portfolio/ me/portfolio/
cd me/portfolio
composer install
```

Nu kan du öppna en webbläsare och peka mot katalogen `me/portfolio`. Får du problem eller felmeddelanden så hojta till i chatten så hjälper vi dig den sista biten.

### Publicera till studentservern {#publicera}

För att din portfolio ska fungera på studentservern så behöver du uppdatera två rader i `me/portfolio/.htaccess`, annars får du 404 på dina länkar och 500 på bilderna.

I följande stycke:

```text
# Rewrite 1 - For request via www.student.bth.se
RewriteCond %{HTTP_HOST} ^www\.student\.bth\.se$ [NC]
RewriteRule ^image/(.*)$ /~mosstud/dbwebb-kurser/design/me/portfolio/assets/cimage/img.php?src=$1 [QSA,NC,L]

RewriteCond %{HTTP_HOST} ^www\.student\.bth\.se$ [NC]
RewriteRule (.*) /~mosstud/dbwebb-kurser/design/me/portfolio/index.php/$1 [NC,L]
```

Så ska ni byta ut `mosstud` till ert egna studentakronym (ex. `abcd20`).

Därefter kan ni publicera till studentservern för att se att allt fungerar:

```
dbwebb publish me
```

#### Bilder laddas inte lokalt

Det kan hända att du får 404 på dina bilder lokalt. Om du går in i devtools (F12) och går till network, så kan du se alla filer som hämtas för hemsidan. Där kan du se länkarna till de bilder som inte laddas in. Om du öppnar en av dem och får felmeddelandet:

```
[img.php]

img.php: Uncaught exception

Cachedir is not a directory.
```

Så behöver du uppdatera rättigheterna på cache-mappen med hjälp utav:

```bash
# Stå i me/portfolio
chmod -R 777 cache/*
```

### Git {#git}

Gör ett git-repo av alla filer i katalogen.

```
# Stå i me/portfolio
git init
git add .
```

Nu har du ett repo, ett _repository_ eller _source code repository_ och du har lagt till alla filerna i katalogen så de är en del av repot.

Informationen om själva repot lagras i den dolda katalogen `.git`. Om du behöver starta om så kan du ta bort den katalogen. Den återskapas när du kör `git init` igen.

```text
ls -la .git
```

Du kan kontrollera statusen på ditt nyskapade Git repo genom att köra:

```text
git status
```

Kommandot visar dig statusen för ditt repo och berättar vilka filer som ändrats och som är och inte är _commit:ade_.

För att "skriva till repot", eller göra en _commit_ på de ändringar som gjorts, så utför du en commit.

```
git commit -m "Här skriver du ett bra commit meddelande"
```

Eventuellt kommer Git be dig att ange din epost och namn för att kunna identifiera dig som den som gör commit:sen.

```text
git config user.email "user@dbwebb.se"
git config user.name "Niklas Andersson"
```

Nu är alla filerna tillagda till ditt repo.

#### Historik {#githist}

Git som versionshanteringssystem kommer ihåg den historik som du committat till repo. Den minns varje commit och vid behov kan man se exakt den kodversionen som gällde för en viss commit.

För att göra det enkelt att se sin egen commithistorik så lägger vi till två alias som visar en lista över alla commits, commit-meddelandet och tidpunkten.

Kör följande två kommandon i din terminal.

```text
git config --global alias.hist 'log --all --decorate --pretty=format:"%h %ad | %s%d [%an]" --graph --date=short'
git config --global alias.tree "log --graph --abbrev-commit --decorate --date=relative --format=format:'%C(bold blue)%h%C(reset) - %C(bold green)(%ar)%C(reset) %C(white)%s%C(reset) %C(dim white)- %an%C(reset)%C(auto)%d%C(reset)' --all"
```

Du har nu två alias som du kan använda för att visa din commit-historik.

```text
git hist
git tree
```

Du får fram en lista av dina commits, den senaste visas överst.

#### Github {#github}

Gå till GitHub och skapa ett nytt repository dit du kan ladda upp git-repot.

Ladda upp ditt git-repo till GitHub (byt ut `git@github.com:dbwebb-se/design-v3.git` mot länken till ditt egna repo).

```text
git branch -M main
git remote add origin git@github.com:dbwebb-se/design-v3.git
git push -u origin main
```

Använd SSH-nycklar för att identifiera dig, det blir enklare för dig att slippa behöva skriva in lösenord varje gång du ska ladda upp ditt repo.

Får du problem med SSH-nycklarna så pröva igen, [GitHub själva har en bra stegvis guide](https://docs.github.com/en/github/authenticating-to-github/connecting-to-github-with-ssh) på hur man kan göra.

När det är klart har du publicerat din portfolio på GitHub.

### Git tag {#gittag}

När du är klar med alla uppdateringar så kan du committa alla ändringar i ditt git repo. Du kan också lägga till en tagg för att markera nuvarande status i git repot som väl fungerande.

En samling taggar ger en historik av koden och gör det enklare att gå tillbaka till ett visst läge i koden.

Se till att du lagt till alla filer och committat alla ändringar innan du taggar.

Du taggar med kommandot `git tag`.

```text
git tag -a v1.0.0 -m "Ett meddelande för denna taggen"
```

När du är klar kan du ladda upp git repot och dess taggar till GitHub.

```text
git push
git push --tags
```

### Bekanta dig {#bekanta}

Bekanta dig med strukturen för din portfolio-katalog och se vad som finns där. Om du inte har, läs igenom artikeln "[Vad är Pico?](kunskap/vad-ar-pico)".

Du kan följa med i videon nedan för att se hur man kan:

* Uppdatera startsidan
* Lägg till ny sida
* Lägg till under-sidor (subpages)
* Modifiera HTML-strukturen på sidan
* Redigera flash-bilden
* Hur du lägger till en bild på sidan

[YOUTUBE src="6aVDmXDXqDs" list="PLKtP9l5q3ce8h3PKihj_CSVBkyxtORWiy" width=700 caption="Pico introduktion"]

Krav {#krav}
-----------------------

1. Förstasidan `portfolio/content/index.md` skall innehålla en hälsning/presentation av/om dig tillsammans med minst en bild som representerar dig.

1. Uppdatera länken i footern så den länkar till ditt egna Github-repo.

1. Byt ut flash-bilden som finns på samtliga sidor.

1. Skapa en `report/kmom01.md` där du påbörjar ett utkast till din redovisningstext för kursmomentet.

1. Skapa ditt eget tema, se "[Vad är Pico? - Tema](kunskap/vad-ar-pico#tema)" för mer information.

1. I din portfolio-mapp (`me/portfolio/`), skapa en fil som heter `github.txt` som innehåller enbart länken till ditt Github-repo (ex: `https://github.com/dbwebb-se/design-v3`)

1. Publicera dina filer till studentservern, `dbwebb publish me`, och kontrollera att allt fungerar som det ska.

1. Commit:a dina ändringar och lägg till en ny tagg (1.0.\*).

1. Push:a repot till GitHub, inklusive taggarna.

Tips från coachen {#tips}
-----------------------

Gör små commits och gör dem ofta, när du väl har din bas. Använd tydliga commit-meddelanden så historiken ser bra ut, det är en bra övning inför projektkurserna och arbetslivet.

Lycka till och hojta till i chatt om du behöver hjälp!
