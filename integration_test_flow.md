# Integration Test Flow – Home & Filter Modules

## 1. Test Scenario: Van Home naar Gefilterd Zoeken
Dit scenario test de overdracht van de zoekcontext (zoals een geselecteerde categorie of zoekterm) van de `loadHomePage` module naar de `searchRecipe` module. Dit gebeurt wanneer een gebruiker op de homepagina een zoekopdracht start of een categorie selecteert en vervolgens doorklikt om alle specifieke resultaten te bekijken.

## 2. Data Flow Diagram
De onderstaande flowchart laat globaal zien hoe data van de algemene weergave op de homepagina naar de specifieke filterlogica stroomt.

```mermaid
graph TD
    SubGraph1[**Module: loadHomePage**]
    A[Gebruiker opent Home] --> B[loadHomePage userID, "", ""]
    B --> C{Gebruiker klikt op 'Vegan' categorie}
    
    C -->|Trigger Filter| D[**Data Transfer Object DTO**]
    
    SubGraph2[**Module: searchRecipe**]
    D --> E[searchRecipe "", "Vegan", 0, ""]
    E --> F[Filtert Storage op 'Vegan']
    F --> G[Toon specifieke resultaten]
```s
## 3. Data Interface Specification
Wanneer de gebruiker van de Homepagina naar de overzichtelijke zoekresultaten navigeert, worden de volgende variabelen overgedragen tussen de modules:

| Parameter | Bron: `loadHomePage` | Doel: `searchRecipe` | Beschrijving |
| :--- | :--- | :--- | :--- |
| **Search State** | `searchQuery` | `searchQuery` | De tekst die al in de zoekbalk stond op de homepagina. |
| **Category State** | `selectedCategory` | `filterTag` | De geselecteerde categorie (bijv. via een knop) op de homepagina. |
| **User Context** | `userID` | *(Intern)* | Gebruikt voor gepersonaliseerde resultaten of logging (optioneel in verdere iteraties). |

## 4. Sequence Diagram (Tijdsvolgorde)
Dit diagram toont de exacte chronologische interactie tussen de User Interface (UI), de twee modules en de gedeelde database (`StorageModule`).

```mermaid
sequenceDiagram
    autonumber
    participant UI as User Interface
    participant Home as loadHomePage
    participant Filter as searchRecipe
    participant Storage as StorageModule

    Note over UI,Storage: Stap 1: Initialisatie van de Homepagina
    UI->>Home: loadHomePage(userID=12, "Ontbijt", "Pannenkoek")
    activate Home
    Home->>Storage: Haal alle recepten op
    activate Storage
    Storage-->>Home: Retourneer dataset (List)
    deactivate Storage
    Home-->>UI: Return (trendingRecipes, recentRecipes, categories)
    deactivate Home

    Note over UI,Filter: Gebruiker klikt op "Toon alle resultaten"

    Note over UI,Storage: Stap 2: Transitie naar Filter/Zoekpagina
    UI->>Filter: searchRecipe("Pannenkoek", "Ontbijt", 0, "")
    activate Filter
    Filter->>Storage: Haal alle recepten op
    activate Storage
    Storage-->>Filter: Retourneer dataset (List)
    deactivate Storage
    Filter-->>UI: Return (results, resultsCount)
    deactivate Filter
```

## 5. Test Case: "Seizoensgebonden Zoekopdracht"

**Doel:** Verifiëren dat een zoekterm en categorie geselecteerd op de Homepagina correct en zonder dataverlies worden verwerkt door de Filter module.

**Stappen:**
1.  **Input Home:** De UI roept op: `loadHomePage(userID=12, selectedCategory="Ontbijt", searchQuery="Pannenkoek")`.
2.  **Actie:** De UI toont enkele trending pannenkoek-recepten. De gebruiker klikt op "Toon alle resultaten".
3.  **Integratie-stap:** De interface pakt de argumenten van de Home-module en geeft deze als input door aan de filter-module: `searchRecipe(searchQuery="Pannenkoek", filterTag="Ontbijt", minRating=0, color="")`.
4.  **Verwachte Output:** * De `results` lijst uit `searchRecipe` bevat uitsluitend objecten waarbij `recipe.tag == "Ontbijt"` EN `recipe.name` de term "Pannenkoek" bevat.
    * `resultsCount` is groter dan 0 en komt exact overeen met het aantal objecten in de `results` lijst.

## 6. White-Box Integratie Karakteristieken
* **Shared Resource:** Beide modules communiceren met dezelfde `StorageModule`. De integratietest bewijst of de data-consistentie tussen beide aanroepen behouden blijft.
* **State Consistency:** Als `loadHomePage` aangeeft dat er trending recepten zijn in de categorie "Ontbijt", dan *moet* een daaropvolgende aanroep naar `searchRecipe` met dezelfde tag minimaal diezelfde recepten retourneren.
