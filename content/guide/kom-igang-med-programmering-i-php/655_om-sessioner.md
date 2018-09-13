---
author: mos
revision:
    "2018-09-13": "(A, mos) Första versionen."
...
Om Sessioner
=======================

Sessioner ger webbplatsen ett minne, de gör det möjligt att komma ihåg information mellan sidladdningar. Man kan till exempel låta en användare logga in och sedan minnas vilken användare man visar en sida för.

Låt oss se hur man jobbar med sessionen i php.



Starta namngiven session {#start}
------------------------

En session i php behöver startas innan den kan användas. För att göra det enkelt för oss så startar vi den alltid i en konfigurationsfil `config.php` som inkluderas i alla sidkontroller. Då vet vi att sessionen alltid är startad och att den är startad på exakt samma sätt med samma namn.

En session kan namnges, det ger möjligheten att jobba mot flera namngivna sessioner samtidigt och det ger möjligheten att en webbplats kan vara säker på att ens session inte krockar med andra sessioner som körs på samma webbplats.

Så, en namngiven session och vi startar den i `config.php`.

```php
// Start the named session,
// the name is based on the path to this file.
$name = preg_replace("/[^a-z\d]/i", __DIR__);
session_name($name);
session_start();
```

Vår taktik på att namnge sessionen är att använda sökvägen till katalogen där `config.php` ligger. Då får alla våra exempelprogram (som sparas i en viss katalog) egna sessioner och vi undviker att olika exempelprogram krockar med varandras sessioner.

I manualen kan vi läsa om [`session_start()`](http://php.net/manual/en/function.session-start.php) och [`session_name()`](http://php.net/manual/en/function.session-name.php).



Förstör en session {#destroy}
------------------------

När man jobbar med sessioner så vill man kunna förstöra en sessino och starta om. Det kan vara ett viktigt utvecklingsverktyg och underlätta felsökningen om man har möjligheten att verkligen förstöra en session och börja om från början.

I manualen för [`session_destroy()`](http://php.net/manual/en/function.session-destroy.php) finns exempelkod för hur man skall förstöra sessionen. Den ser ut så här.

```php
// Initialize the session.
// If you are using session_name("something"), don't forget it now!
session_start();

// Unset all of the session variables.
$_SESSION = array();

// If it's desired to kill the session, also delete the session cookie.
// Note: This will destroy the session, and not just the session data!
if (ini_get("session.use_cookies")) {
    $params = session_get_cookie_params();
    setcookie(session_name(), '', time() - 42000,
        $params["path"], $params["domain"],
        $params["secure"], $params["httponly"]
    );
}

// Finally, destroy the session.
session_destroy();
```

Jag väljer att göra en egen funktion som förstör en session. Min funktion får förutsätta att sessionen redan är startad. Jag har ju mina namngivna sessioner som startas i filen `config.php`. Funktionen ser då ut så här.

```php
/**
 * Destroy a session, the session must be started.
 *
 * @return void
 */
function sessionDestroy()
{
    // Unset all of the session variables.
    $_SESSION = [];

    // If it's desired to kill the session, also delete the session cookie.
    // Note: This will destroy the session, and not just the session data!
    if (ini_get("session.use_cookies")) {
        $params = session_get_cookie_params();
        setcookie(
            session_name(),
            '',
            time() - 42000,
            $params["path"],
            $params["domain"],
            $params["secure"],
            $params["httponly"]
        );
    }

    // Finally, destroy the session.
    session_destroy();
}
```

Jag nöjer mig med att konstatera att manualen säger att denna koden förstör sessionen, och dess session-cookie. Jag bryr mig inte om detaljerna.
