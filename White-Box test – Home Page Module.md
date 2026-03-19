# White-Box Design – Home Page Module (`loadHomePage`)

## Module Purpose
The `loadHomePage` module loads and prepares the content for the home page of the recipe platform, including trending recipes, categories, and recent uploads.

## Inputs

| Variable | Type | Description |
|--------|--------|--------|
| `userID` | int | ID of the logged-in user |
| `selectedCategory` | char | Selected category filter |
| `searchQuery` | char | Search text entered by the user |

## Outputs

| Output | Type | Description |
|------|------|------|
| `trendingRecipes` | `struct Recipe[]` | List of trending recipes |
| `recentRecipes` | `struct Recipe[]` | Recently uploaded recipes |
| `categories` | `string[]` | Available recipe categories |
| Message | string | Message when no recipes are available |

---

# Internal Variables

| Variable | Type | Description |
|------|------|------|
| `trendingRecipes` | list | Collection of trending recipes |
| `recentRecipes` | list | Collection of recent recipes |
| `categories` | list | Available categories |
| `recipeCount` | int | Counter for recipes found |

---

# Algorithm (White-Box Logic)

```pseudo

    function loadHomePage(userID, selectedCategory, searchQuery)

    trendingRecipes = empty list
    recentRecipes = empty list
    categories = getCategories()
    recipeCount = 0

    for each recipe in StorageModule

        if selectedCategory != ""
            if recipe.category != selectedCategory
                continue

        if searchQuery != ""
            if recipe.name does not contain searchQuery
                continue

        if recipe.isTrending == true
            add recipe to trendingRecipes

        if recipe.uploadDate is recent
            add recipe to recentRecipes

        recipeCount++

    if recipeCount > 0
        return trendingRecipes, recentRecipes, categories
    else
        return "Geen recepten beschikbaar"

---

# White-Box Control Flow Diagram

```mermaid
graph TD

A[Start loadHomePage] --> B[Load recipes from Storage]
B --> C{More recipes available?}

C -->|Yes| D[Get next recipe]

D --> E{Category matches?}
E -->|No| C
E -->|Yes| F{Search query matches?}

F -->|No| C
F -->|Yes| G{Recipe is trending?}

G -->|Yes| H[Add to trendingRecipes]
G -->|No| I[Check recent upload]

H --> I

I --> J{Recently uploaded?}
J -->|Yes| K[Add to recentRecipes]
J -->|No| L[Continue]

K --> L
L --> C

C -->|No| M{recipeCount > 0?}

M -->|Yes| N[Return homepage data]
M -->|No| O[Return "Geen recepten beschikbaar"]