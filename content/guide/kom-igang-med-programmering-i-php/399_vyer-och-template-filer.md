---
author: mos
revision:
    "2018-03-13": "(A, mos) Första versionen, uppdelad av större dokument."
...
Vyer och templatefiler
=======================

Jobba med begreppet templatefiler och vyer.



PHP korta taggar, "short tags" {#short-tags}
-----------------------

Det finns flera varianter på PHP-taggar. Du har kanske noterat att jag mixar två varianter.

```php
<?php $title = "Titel på min nya sida"; ?> <!-- Den "vanliga" PHP-taggen  -->

<?= $title ?>  <!-- Den korta varianten som är samma sak som <?php echo $title; ?> -->
```

Den korta varianten lämpar sig för användning tillsammans med HTML-kod. Det är en kortare variant för att skriva `<?php echo $title; ?>`. Du sparar ett par tecken och koden blir lättare att läsa.
