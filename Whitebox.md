# White-Box Design – Filter Module (`searchRecipe`)

## Module Purpose
The `searchRecipe` module searches recipes in the storage module and filters them according to user-defined criteria.

## Inputs

| Variable | Type | Description |
|--------|--------|--------|
| `searchQuery` | char | Text used to match recipe names |
| `filterTag` | char | Tag/category filter |
| `minRating` | int | Minimum rating threshold |
| `color` | char | Color/category filter |

## Outputs

| Output | Type | Description |
|------|------|------|
| `results` | `struct Recipe[]` | List of matching recipes |
| `resultsCount` | int | Number of matching recipes |
| Message | string | "Geen resultaten gevonden" when no matches exist |

---

# Internal Variables

| Variable | Type | Description |
|------|------|------|
| `resultsCount` | int | Counter for matching recipes |
| `results` | list | Collection of valid recipes |

---

# Algorithm (White-Box Logic)

```
function searchRecipe(searchQuery, filterTag, minRating, color)

    resultsCount = 0
    results = empty list

    for each recipe in StorageModule

        if searchQuery != ""
            if recipe.name does not contain searchQuery
                continue

        if filterTag != ""
            if recipe.tag != filterTag
                continue

        if minRating > 0
            if recipe.rating < minRating
                continue

        if color != ""
            if recipe.color != color
                continue

        add recipe to results
        resultsCount++

    if resultsCount > 0
        return results, resultsCount
    else
        return "Geen resultaten gevonden"
```

---

# White-Box Control Flow Diagram

```mermaid
graph TD

A[Start searchRecipe] --> B[Load recipes from Storage]
B --> C{More recipes available?}

C -->|Yes| D[Get next recipe]

D --> E{searchQuery match?}
E -->|No| C
E -->|Yes| F{filterTag match?}

F -->|No| C
F -->|Yes| G{rating >= minRating?}

G -->|No| C
G -->|Yes| H{color match?}

H -->|No| C
H -->|Yes| I[Add recipe to results]

I --> J[resultsCount++]
J --> C

C -->|No| K{resultsCount > 0?}

K -->|Yes| L[Return results and resultsCount]
K -->|No| M[Return "Geen resultaten gevonden"]
```

---

# White-Box Characteristics

The module exposes its internal logic:

- Iteration through stored recipes
- Conditional filtering steps
- Internal state (`results`, `resultsCount`)
- Decision points for each filter condition
- Final decision based on results count