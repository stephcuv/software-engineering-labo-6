# Black Box Testplan: Navigatie & Homepagina

Dit document focust specifiek op de gebruikerservaring en de interface-logica van de homepagina. We testen hier of de `main` module de gebruiker correct door de applicatie loodst en of de homepagina robuust genoeg is om foutieve invoer op te vangen.

## 1. Succesvolle Testscenario's (Positive Testing)
Deze tests controleren of de applicatie werkt zoals bedoeld bij correct gebruik.

| Test ID | Scenario | Input (Actie) | Verwachte Output / Gedrag |
| :--- | :--- | :--- | :--- |
| **BBN-01** | **Correcte Opstart** | Start het programma op. | De applicatie laadt zonder fouten; de header, zoekbalk en trending recepten zijn direct zichtbaar. |
| **BBN-02** | **Menu Navigatie** | Klik op "Explore" in de navigatiebalk. | De interface ververst en toont de uitgebreide ontdekkingspagina (Explore View). |
| **BBN-03** | **Logo-link Check** | Navigeer diep in een recept en klik vervolgens op het [Logo]. | De gebruiker keert onmiddellijk terug naar de standaard Homepagina-staat. |
| **BBN-04** | **Recept Selectie** | Klik op de afbeelding van een "Trending" recept. | De `main` module roept de detail-view aan en toont de specifieke data van dat recept. |
| **BBN-05** | **Categorie Filter** | Klik op de horizontale chip "Vegan". | De lijst op de homepage wordt direct gefilterd; alleen recepten met het label 'Vegan' blijven over. |

## 2. Negatieve & Faal-scenario's (Negative Testing)
Deze tests dagen het systeem uit door onverwachte of foutieve acties uit te voeren. Hiermee controleren we de stabiliteit.

| Test ID | Scenario | Input (Actie) | Verwachte Output / Gedrag |
| :--- | :--- | :--- | :--- |
| **BBN-06** | **Ontbrekende Data** | Verwijder het receptenbestand (`recipes.dat`) en start de app. | De app crasht niet, maar toont een nette melding op de homepagina: "Geen recepten beschikbaar." |
| **BBN-07** | **Lege Zoekopdracht** | Klik op het zoek-icoon [🔍] zonder tekst in te vullen. | De pagina ververst niet of geeft een subtiele melding: "Voer een zoekterm in om te filteren." |
| **BBN-08** | **Ongeldige URL/ID** | Probeer handmatig een recept-ID te benaderen dat niet bestaat (via CLI of URL). | De Web Server vangt dit op en toont een 404-foutpagina in plaats van een leeg wit scherm. |
| **BBN-09** | **Deep-link zonder Login** | Klik op "Create [+]" terwijl je niet bent ingelogd. | De applicatie blokkeert de toegang en stuurt de gebruiker automatisch door naar het inlogscherm. |
| **BBN-10** | **Buffer Overflow Check**| Voer een extreem lange reeks tekens (bijv. 1000+) in de zoekbalk in. | De applicatie breekt de input af of weigert deze; het systeem mag onder geen beding 'bevriezen' of crashen. |
| **BBN-11** | **Conflict in Filters** | Selecteer twee tegenstrijdige filters (bijv. "Vlees" en "Vegan"). | Het systeem toont nul resultaten met de melding: "Geen combinaties gevonden voor deze filters." |

## 3. Evaluatiecriteria
De tests worden als 'geslaagd' beschouwd indien:
1. De applicatie bij **succesvolle scenario's** binnen 2 seconden reageert.
2. De applicatie bij **faal-scenario's** altijd een begrijpelijke foutmelding geeft aan de gebruiker.
3. Er geen geheugenlekken of crashes optreden in de `main` module tijdens het navigeren tussen Home en subpagina's.