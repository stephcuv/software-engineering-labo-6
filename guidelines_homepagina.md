# Wireframe Specificaties: Homepage - Recipe Sharing Platform

Dit document beschrijft de structuur en de functionele elementen van de homepage. Het doel van de homepage is om gebruikers te inspireren, populaire content te tonen en een snelle toegang tot de zoekfunctie te bieden.

---

## 1. Header (Navigatie)
* **Links:** Logo van het platform (linkt naar home).
* **Midden:** Navigatiemenu:
    * Recepten Ontdekken
    * Maaltijdplanners
    * Community/Blog
* **Rechts:** * Zoekicoon (vergrootglas)
    * Knop: "Recept Uploaden" (primaire actie)
    * Gebruikersprofiel / Login-icoon

---

## 2. Hero Sectie (Boven de vouw)
* **Achtergrond:** Een kwalitatieve, beeldvullende foto van een seizoensgebonden gerecht.
* **Centraal:** * **Headline:** "Wat eten we vandaag?"
    * **Grote Zoekbalk:** Inputveld met tekst "Zoek op ingrediënt, dieet of keuken..."
    * **Quick Tags:** Kleine knoppen onder de zoekbalk voor populaire filters (bijv. "Vegetarisch", "Binnen 20 min", "Pasta").

---

## 3. Sectie: Populaire Categorieën
* **Layout:** Horizontale rij met ronde iconen of vierkante kaarten.
* **Items:**
    * Ontbijt
    * Lunch
    * Diner
    * Desserts
    * Vegan

---

## 4. Sectie: Trending Recepten (Grid)
* **Titel:** "Nu populair in de community"
* **Kaart Structuur (Recipe Card):**
    * **Afbeelding:** Ratio 4:3.
    * **Overlay:** Hartje (Save/Favorite) rechtsboven.
    * **Info:** * Titel van het recept (Bold)
        * Rating (Sterren + aantal reviews)
        * Bereidingstijd (bijv. ⏱ 30 min)
        * Moeilijkheidsgraad

---

## 5. Sectie: "Chef van de Week" (Sociale Component)
* **Layout:** Twee kolommen (60/40 splitsing).
* **Links:** Een korte bio en foto van een actieve gebruiker.
* **Rechts:** Een kleine preview van hun top 3 best beoordeelde recepten.

---

## 6. Footer
* **Kolom 1:** Over ons & Missie.
* **Kolom 2:** Snelkoppelingen (FAQ, Contact, Privacy).
* **Kolom 3:** Nieuwsbriefinschrijving ("Ontvang wekelijks recepten").
* **Onderaan:** Social media iconen en copyright info.

---

## Functionele Notities
- **Sticky Header:** De navigatie blijft zichtbaar tijdens het scrollen.
- **Lazy Loading:** Afbeeldingen in de recepten-grid laden pas in wanneer ze in beeld komen voor snelheid.
- **Responsive Design:** Op mobiel wordt de grid van 4 kolommen naar 1 of 2 kolommen aangepast.