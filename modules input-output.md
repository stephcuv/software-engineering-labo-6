# Dataflow Specificaties: Inputs & Outputs per Module

Dit overzicht beschrijft welke gegevens elke module ingaat (input) en wat het resultaat of de actie is die eruit voortkomt (output).

---

## 1. Account Module
* **Inputs:** Gebruikersnaam(string), e-mailadres(string), wachtwoord(string).
* **Outputs:** Sessie-token (login status)(string), bevestiging van registratie(bool), bijgewerkt gebruikersprofiel, toegangsweigering(bool) (bij ban).

## 2. Recipe Management Module
* **Inputs:** Receptnaam(string), lijst van ingrediënten (string), stappenplan, bereidingstijd, categorie-tags (array van strings).
* **Outputs:** Gestructureerd receptobject, visuele weergave van het recept op het scherm, bevestiging van wijziging/verwijdering (bool).

## 3. Search & Filter Module
* **Inputs:** Zoektermen (strings), gekozen filters (tag, ingrediënt, minimale rating, kleur).
* **Outputs:** Een gefilterde lijst met recepten die voldoen aan de criteria, "geen resultaten" melding.

## 4. Community Module
* **Inputs:** Sterrenscore (1-5)(int), tekstuele review (string), volg-verzoek voor een user, ID van een favoriet recept (int).
* **Outputs:** Gemiddelde score-update voor een recept (int), lijst van favorieten (array van strings), notificatie naar de gevolgde user (string).

## 5. Moderation Module
* **Inputs:** Ingediende recepten (voor review) (array van strings), rapportages van gebruikers over ongepaste content (string).
* **Outputs:** Status-update van recept (string)(Gepubliceerd/Afgewezen), verwijdering van gerapporteerde content (bool).

## 6. Utility Module
* **Inputs:** Originele ingrediënt-hoeveelheden (int), gewenst aantal personen(int), recept-ID(int).
* **Outputs:** Herberekende ingrediëntenlijst (int), gegenereerde deelbare URL (string), chronologisch overzicht van activiteiten (array van strings).

## 7. Storage Module
* **Inputs:** Recept-objecten, user-structs, review-data (om op te slaan).
* **Outputs:** Data weggeschreven naar bestand/database, geladen data-objecten bij opstarten van het programma.

## 8. Main Module
* **Inputs:** Gebruikerskeuzes uit het menu (keyboard input), status van de sub-modules.
* **Outputs:** Menuschermen, aansturing van specifieke modulefuncties, afsluiten van het programma.