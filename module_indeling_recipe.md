# Module-indeling: Recipe Sharing Platform

Op basis van de functionele ontwikkelingsmethode is het programma opgesplitst in specifieke modules. Elke module bestaat uit een `.c` bestand (de logica) en een `.h` bestand (de definities/interfaces).

### 1. Main Module (`main.c`)
Dit is het startpunt van de applicatie. Het bevat de hoofd-loop en stuurt de interactie tussen de andere modules aan.

### 2. User & Auth Module (`auth.c` / `auth.h`)
Beheert alles wat met de gebruiker te maken heeft, zoals profielgegevens en toegangscontrole.

### 3. Recipe Management Module (`recipe.c` / `recipe.h`)
De kernmodule voor de recept-data. Hierin worden de structuren voor ingrediënten en instructies beheerd.

### 4. Search & Filter Module (`search.c` / `search.h`)
Bevat de algoritmes om door de verzameling recepten te bladeren op basis van criteria zoals dieet of tijd.

### 5. Storage Module (`storage.c` / `storage.h`)
Verzorgt de persistente opslag. Deze module leest en schrijft data naar het lokale bestandssysteem.

### 6. User Interface Module (`ui.c` / `ui.h`)
Verantwoordelijk voor alle tekstuele output en input-verwerking van de gebruiker..