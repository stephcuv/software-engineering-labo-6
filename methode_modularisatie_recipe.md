# Strategie voor Modularisatie: Recipe Sharing Platform

## 1. Gebruikte AI-Prompt
Om tot een deze modularisatie-strategie te komen, is de volgende prompt gegeven aan een AI-assistent:

> *"Ik ontwikkel een 'Recipe Sharing Platform' in de programmeertaal C. Ik werk volgens de functionele ontwikkelingsmethode. Help me een strategie te bepalen om mijn programma op te splitsen in modules. Leg uit hoe ik dit het beste aanpak met .c en .h bestanden, hoe ik abstractie toepas en hoe ik de schaalbaarheid van het project waarborg zonder de code onnodig complex te maken voor een beginnende C-programmeur."*

---

## 2. Gekozen Methodologie: Functionele Decompositie

De kern van de gekozen strategie is **Functionele Decompositie**. In de context van C-programmeren betekent dit dat we het probleem (het bouwen van een platform) niet zien als één grote taak, maar als een verzameling van kleinere, onafhankelijke sub-taken. 

### Hoe het werkt
Bij functionele decompositie kijken we naar wat het programma moet *doen*. Elke grote handeling (zoals "een recept opslaan" of "een gebruiker inloggen") wordt een aparte module. In C dwingen we deze scheiding af door gebruik te maken van het tweetal: **Header-bestanden (.h)** en **Bronbestanden (.c)**.

1.  **De Interface (.h):** Dit is het 'contract' van de module. Hierin staan de definities van structuren en de headers van functies die voor de rest van het programma beschikbaar zijn. Het vertelt *wat* de module doet, zonder te verklappen *hoe*.
2.  **De Implementatie (.c):** Hier staat de daadwerkelijke logica. Hier worden de functies uit de header uitgeschreven.

---

## 3. Toepassing van de Strategie

Om deze modularisatie succesvol toe te passen in dit project, gebruiken we de volgende drie principes:

### A. Encapsulatie (Afscherming)
Een belangrijk onderdeel van de strategie is dat modules zo weining mogelijk van elkaars interne werking weten. Als de module voor "Recepten" een ingrediënt aanpast, hoeft de module voor "User Interface" niet te weten hoe die data in het geheugen staat; de UI roept simpelweg een functie aan. Dit noemen we *informatie-verstopping*. In C bereiken we dit door hulp-functies in het .c bestand `static` te maken, zodat ze onzichtbaar zijn voor andere modules.

### B. Koppeling en Cohesie
We streven naar **hoge cohesie**: dit betekent dat alle code binnen één module ook echt bij elkaar hoort (bijvoorbeeld: alle code in de opslag-module gaat over bestanden). Tegelijkertijd willen we **lage koppeling**: modules moeten zo onafhankelijk mogelijk van elkaar kunnen functioneren. Als we de manier waarop we data opslaan veranderen (van tekstbestand naar database), mag dit geen invloed hebben op de manier waarop we een recept aanmaken in de UI.

### C. De 'Main' als hoofdmodule
In deze methodologie werkt het `main.c` bestand enkel als een coördinator. Het bevat de hoofdlus van het programma en roept functies uit de verschillende modules aan in de juiste volgorde. De `main` bevat zelf bijna geen logica, maar delegeert alles naar de gespecialiseerde modules.

---

## 4. Voordelen voor het Project

Door deze methode toe te passen, behalen we de volgende voordelen:
* **Foutopsporing:** Als er iets misgaat bij het zoeken, weten we direct dat de fout in de 'Search' module zit en hoeven we niet door duizenden regels code te zoeken.
* **Samenwerking:** Verschillende programmeurs kunnen gelijktijdig aan verschillende modules werken zonder elkaars code te overschrijven.
* **Herbruikbaarheid:** Modules zoals de 'Storage' module kunnen in toekomstige projecten opnieuw gebruikt worden met minimale aanpassingen.

---

## 5. Conclusie
De functionele ontwikkelingsmethode is de meest logische stap voor een C-project van deze omvang. Het dwingt ons om vooraf na te denken over de structuur, wat resulteert in code die niet alleen werkt, maar ook leesbaar en onderhoudbaar is voor de toekomst.