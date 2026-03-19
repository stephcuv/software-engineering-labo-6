
## 1. Functional Requirements 

These requirements define the specific behaviors and functions the system must provide. 

 

### High Priority (MVP) 

* **User Authentication:** Users must be able to log in (**aanmelden**) and reset passwords (**wachtwoord resetten**). 

* **Recipe Management:** Users can upload recipes (**recepten uploaden**), view recipes (**recepten bekijken**), and delete their own recipes (**eigen recepten verwijderen**). 

* **Search Functionality:** Users must be able to search for specific recipes (**zoekfunctie voor recepten**). 

 

### Medium Priority (Must Have) 

* **Profile Management:** Users can change personal information (**persoonlijke informatie wijzigen**) and personalize accounts (**account personalisatie**). 

* **Content Control:** Users can edit existing recipes (**recepten editen**) and generate unique sharing links (**URL naar recepten kunnen maken**). 

* **Moderation:** Administrators must be able to approve or reject submitted recipes (**recepten goedkeuren/afwijzen**). 

* **Engagement:** An activity feed to track recent updates (**activiteit feed**). 

 

### Low Priority (Nice to Have) 

* **Organization:** Support for tags, categories, and tag-based filtering (**tags en categorieën**, **filteren volgens tags**). 

* **Feedback:** A system for user reviews and ratings (**reviews en ratings**). 

* **Tools:** A portion calculator for scaling ingredients (**portie calculator**). 

* **Safety:** A ban system for user moderation (**ban systeem**). 

 

--- 

 

## 2. Data Requirements 

* **Storage:** A structured system for **database management**. 

* **Administrative Access:** Tools to directly **view the database** for troubleshooting. 

* **Security:** Regular **database backups** to prevent data loss. 

 

--- 

 

## 3. Performance Requirements 

* **Search Speed:** The search function should return results within < 2 seconds to maintain usability. 

* **Reliability:** Database backups must occur daily without affecting system uptime. 

 

--- 

 

## 4. Constraints 

* **Permissions:** Only users with "Admin" roles can access database viewing and recipe approval tools. 

* **Data Privacy:** User password resets must be handled via secure, encrypted tokens. 

 

--- 

 

## 5. Guidelines 

* **User Experience (UX):** The "Nice to Have" features (like the portion calculator) should not clutter the primary mobile view. 

* **Scalability:** The database architecture should allow for horizontal scaling as the recipe count grows. 

 

--- 

 

## 6. Use Cases 

 

 

 

### Use Case 1: Uploading a Recipe 

* **Actor:** Registered User 

* **Description:** The user submits a new recipe to the platform. 

* **Main Flow:** 1. User logs into the account. 

    2. User selects "Upload Recipe." 

    3. User enters title, ingredients, instructions, and optional tags. 

    4. User saves the recipe. 

* **Post-condition:** Recipe is saved and sent to the moderation queue. 

 

### Use Case 2: Recipe Moderation 

* **Actor:** Administrator 

* **Description:** An admin reviews pending content to ensure it meets community standards. 

* **Main Flow:** 

    1. Admin logs into the admin dashboard. 

    2. Admin views the list of recipes pending approval. 

    3. Admin reviews content and selects "Approve" or "Reject." 

* **Post-condition:** If approved, the recipe becomes public and searchable. 