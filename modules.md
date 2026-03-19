# Modularisatie van de User Story Map
## Recipe Sharing Platform

## 1. Inleiding
- Voor de ontwikkeling van het Recipe Sharing Platform wordt **functionele decompositie** gebruikt.
- Het programma wordt opgesplitst in kleinere modules op basis van functionaliteit.
- Elke module bestaat uit:
  - een `.h` bestand (interface)
  - een `.c` bestand (implementatie)

### Voordelen
- duidelijke structuur
- betere onderhoudbaarheid
- herbruikbare code
- lage koppeling tussen modules

---

# 2. Modulestructuur

## 2.1 Account Module

### Bestanden
- `account.h`
- `account.c`

### Verantwoordelijkheid
- Beheer van gebruikersaccounts


### Voorbeeld functies
- `registerUser()`
- `loginUser()`
- `resetPassword()`
- `updateUserProfile()`
- `banUser()`

---

## 2.2 Recipe Management Module

### Bestanden
- `recipe.h`
- `recipe.c`

### Verantwoordelijkheid
- Beheer van recepten


### Voorbeeld functies
- `addRecipe()`
- `editRecipe()`
- `deleteRecipe()`
- `displayRecipe()`
- `addIngredients()`

---

## 2.3 Search & Filter Module

### Bestanden
- `search.h`
- `search.c`

### Verantwoordelijkheid
- Zoeken en filteren van recepten

### Voorbeeld functies
- `searchRecipe()`
- `filterByTag()`
- `filterByIngredient()`
- `filterByRating()`

---

## 2.4 Community Module

### Bestanden
- `community.h`
- `community.c`

### Verantwoordelijkheid
- Interactie tussen gebruikers

### Voorbeeld functies
- `addReview()`
- `rateRecipe()`
- `followUser()`
- `saveFavoriteRecipe()`

---

## 2.5 Moderation Module

### Bestanden
- `moderation.h`
- `moderation.c`

### Verantwoordelijkheid
- Controle en moderatie van content

### Voorbeeld functies
- `approveRecipe()`
- `rejectRecipe()`
- `reviewReportedRecipe()`

---

## 2.6 Utility Module

### Bestanden
- `utils.h`
- `utils.c`

### Verantwoordelijkheid
- Extra hulpmiddelen voor het platform


### Voorbeeld functies
- `calculatePortions()`
- `generateRecipeURL()`
- `showActivityFeed()`

---

## 2.7 Storage Module

### Bestanden
- `storage.h`
- `storage.c`

### Verantwoordelijkheid
- Opslaan en laden van data


### Voorbeeld functies
- `saveRecipe()`
- `loadRecipes()`
- `saveUser()`

---

## 2.8 Main Module

### Bestand
- `main.c`

### Verantwoordelijkheid
- Coördinatie van het volledige programma

### Taken
- hoofdmenu tonen
- modules aanroepen
- program flow beheren

### Voorbeeld functie
- `main()`

---

# 3. Overzicht van de Modules

| Module | Doel |
|------|------|
| Account | gebruikersbeheer |
| Recipe | recepten beheren |
| Search | zoeken en filteren |
| Community | interactie tussen gebruikers |
| Moderation | controle van content |
| Utility | extra functionaliteiten |
| Storage | data opslaan |
| Main | programmacoördinatie |

---

# 4. Conclusie

- Het Recipe Sharing Platform wordt opgesplitst in duidelijke modules.
- Elke module heeft één specifieke verantwoordelijkheid.
- Modules communiceren via functies.
- Hierdoor blijft het systeem:
  - overzichtelijk
  - onderhoudbaar
  - schaalbaar