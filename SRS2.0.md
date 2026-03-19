# Software Requirements Specification (SRS)

## 1. Functional Requirements

These requirements define the specific behaviors and functions the system must provide.

### High Priority (MVP)

* **User Authentication:** Users must be able to log in (aanmelden) and reset passwords (wachtwoord resetten).
* **Recipe Management:** Users can upload recipes (recepten uploaden), view recipes (recepten bekijken), and delete their own recipes (eigen recepten verwijderen).
* **Search Functionality:** Users must be able to search for specific recipes (zoekfunctie voor recepten).

### Medium Priority (Must Have)

* **Profile Management:** Users can change personal information (persoonlijke informatie wijzigen) and personalize accounts (account personalisatie).
* **Content Control:** Users can edit existing recipes (recepten editen) and generate unique sharing links (URL naar recepten kunnen maken).
* **Moderation:** Administrators must be able to approve or reject submitted recipes (recepten goedkeuren/afwijzen).
* **Engagement:** An activity feed to track recent updates (activiteit feed).

### Low Priority (Nice to Have)

* **Organization:** Support for tags, categories, and tag-based filtering (tags en categorieën, filteren volgens tags).
* **Feedback:** A system for user reviews and ratings (reviews en ratings).
* **Tools:** A portion calculator for scaling ingredients (portie calculator).
* **Safety:** A ban system for user moderation (ban systeem).

---

## 2. Data Requirements

* **Storage:** A structured system for database management.
* **Administrative Access:** Tools to directly view the database for troubleshooting.
* **Security:** Regular database backups to prevent data loss.
* **Password Storage:** User passwords must be stored using a secure hashing algorithm (e.g., bcrypt or Argon2) with salting.
* **Data Protection:** Personal user data such as email addresses and profile information must be stored securely and protected from unauthorized access.

---

## 3. Performance Requirements

* **Search Speed:** The search function should return results within less than 2 seconds to maintain usability.
* **Reliability:** Database backups must occur daily without affecting system uptime.

---

## 4. Constraints

* **Permissions:** Only users with Admin roles can access database viewing tools and recipe approval features.
* **Secure Communication:** All communication between clients and the platform must use HTTPS (TLS encryption).
* **Data Privacy:** User password resets must be handled via secure, encrypted tokens.
* **Authorization Enforcement:** All permission checks must be enforced server-side.

---

## 5. Guidelines

* **User Experience (UX):** The “Nice to Have” features (such as the portion calculator) should not clutter the primary mobile view.
* **Scalability:** The database architecture should allow for horizontal scaling as the recipe count grows.

---

## 6. Use Cases

### Use Case 1: Uploading a Recipe

Actor: Registered User

Description: The user submits a new recipe to the platform.

Main Flow:

1. User logs into the account.
2. User selects "Upload Recipe."
3. User enters title, ingredients, instructions, and optional tags.
4. User saves the recipe.

Post-condition: Recipe is saved and sent to the moderation queue.

---

### Use Case 2: Recipe Moderation

Actor: Administrator

Description: An admin reviews pending content to ensure it meets community standards.

Main Flow:

1. Admin logs into the admin dashboard.
2. Admin views the list of recipes pending approval.
3. Admin reviews content and selects "Approve" or "Reject."

Post-condition: If approved, the recipe becomes public and searchable.

---

## 7. Security Requirements

### 7.1 Authentication

* Users must authenticate using a unique account consisting of email and password.
* Passwords must be stored using secure hashing with salting.
* Password reset must use secure, time-limited tokens.
* Login attempts must be rate limited to prevent brute-force attacks.
* User sessions must use secure session tokens with automatic expiration.

### 7.2 Authorization

* The system must implement role-based access control (RBAC).
* Standard users may only edit or delete their own recipes.
* Administrators may approve, reject, or remove recipes.
* Only administrators may access database viewing tools.

### 7.3 Application Security

* All user input must be validated and sanitized.
* The system must protect against SQL injection attacks.
* The system must protect against cross-site scripting (XSS).
* The system must protect against cross-site request forgery (CSRF).
* Uploaded files (such as recipe images) must be validated for file type and size.

### 7.4 Logging and Monitoring

* Login attempts must be logged.
* Administrative actions such as moderation or banning users must be logged.
* Logs must be protected from unauthorized modification.
