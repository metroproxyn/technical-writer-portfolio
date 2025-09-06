# User Manual Improvement

**Objective:** Demonstrate the ability to analyze poorly structured technical content and rewrite it according to modern technical writing standards (Microsoft Writing Style Guide, Plain English).

**Context:** This sample is based on a test assignment for a Technical Writer position. The task was to improve a provided user manual excerpt, focusing on clarity, scannability, and user-centricity.

## Original Content

The original text was poorly structured, contained promotional language, buried critical information, and used inconsistent terminology.

> **Add or Edit the user**
>
> We understand that time is valuable, which is why our platform automatically adds users as soon as they register, freeing up your precious resources. But we also know that sometimes, you may want to take matters into your own hands or prevent unauthorized access.
>
> With our platform, you have the flexibility to manually register a user or restrict access to certain features for unregistered users upon their request. This ensures that you have full control over your user base and can provide the best possible experience for your customers.
>
> When you want to add a user do the following:
> 1. Go to the "Users", then click 'New user' button and enter email of the user
> 2. enter password of the user. (The user will be able to change the password later).
> 3. Under Profile fields, enter the user name. There must be no digits in the user name and the number of characters must be from 1 to 128. We allow to enter single quotation mark, minus sign, period and blank space.
> 4. Type the surname of the user. There must be no digits in the user surname and the number of characters must be from 1 to 128. We allow to enter single quotation mark, minus sign, period and blank space.
> 5. Select user date of birth
> 6. Enter the name of the city where the user lives.
> 7. Type the phone number of the user
> 8. Check the checkbox whether the user is male or female
> 9. When you finish with filling in the form you can click "Create" button to create the user.
> 10. To edit user, push the email of a user you want to edit.
> 11. Tap 'Edit user' on the user details page, at the top right
> 12. Make changes, for example: First, last names, nickname, date of birth, country, city, address, profession, time zone, security question, personal ID.
> 13. Click Update user to finish editing of the user.
>
> Per the established protocols of the system, once a user has been registered within the framework, they shall not be able to be removed from the system.

## Improved Version

This redaction transforms the original text into a clear, concise, and action-oriented guide. The revisions are grounded in the principles of the Microsoft Writing Style Guide and Plain English, directly addressing the user's need to complete the task efficiently.

**Add or edit a user**

You can add new users manually or update details for existing users.

**NOTE:** Registered users can't be deleted from the system.

**Add a user**

1.  Go to **Users**.
2.  Select **New user**.
3.  Enter the user's email address.
4.  Enter a password.
    The user can change the password later.
5.  In the **Profile** section, enter the user's first name.
    - The name must be 1--128 characters.
    - Numbers aren't allowed.
    - Apostrophes, hyphens, periods, and spaces are allowed.
6.  Enter the user's last name.
    - The last name follows the same rules as the first name.
7.  Select the user's date of birth.
8.  Enter the user's city.
9.  Enter the user's phone number.
10. Select the user's gender.
11. When finished, select **Create**.

**Edit a user**

1.  In **Users**, select the user's email address.
2.  On the user details page, select **Edit user** (top right).
3.  Update the fields as needed, such as:
    - First name
    - Last name
    - Nickname
    - Date of birth
    - Country
    - City
    - Address
    - Profession
    - Time zone
    - Security question
    - Personal ID
4.  Select **Update user** to save changes.

### Comments on changes

The following comments explain the changes I have implemented.

#### 1. Removing the introductory marketing-style text
- **Before:** "We understand your time is valuable... ensures the best possible experience..."
- **After:** "You can add new users manually or update details for existing users."
- **Why:** The user needs clear instructions, not promotional text. This follows the Microsoft Style Guide recommendation to be direct and user-focused.
- **See:** [Microsoft Writing Style Guide → Word choice → Use simple words, concise sentences](https://learn.microsoft.com/en-us/style-guide/word-choice/use-simple-words-concise-sentences)

#### 2. Highlighting the critical system limitation upfront
- **Before:** A long, formal sentence hidden at the end: "Per the established protocols of the system..."
- **After:** NOTE: Registered users can't be deleted from the system. (placed at the beginning)
- **Why:** Important system limitations should be highlighted immediately to prevent user frustration and support requests.
- **See:** [Microsoft Writing Style Guide → Content organization → Notes, tips, and warnings](https://learn.microsoft.com/en-us/style-guide/content/notes-tips-cautions)

#### 3. Structuring into clear, actionable steps
- **Before:** Long paragraphs with mixed actions and inconsistent formatting
- **After:** Two separate procedures (Add a user, Edit a user) with numbered steps
- **Why:** Makes content scannable and easy to follow. Each step starts with an imperative verb.
- **See:** [Microsoft Writing Style Guide → Global communications → Use imperative mood in procedures](https://learn.microsoft.com/en-us/style-guide/global-communications/writing-tips#tips-for-all-global-content)

#### 4. Consistent UI element formatting
- **Before:** UI elements inconsistently marked with quotes or not marked
- **After:** All UI elements (**Users**, **New user**, **Create**) in **bold**
- **Why:** Helps users quickly locate on-screen elements and distinguishes from regular text
- **See:** [Microsoft Writing Style Guide → Formatting punctuation → Text describing UI interaction](https://learn.microsoft.com/en-us/style-guide/punctuation/formatting-punctuation)

#### 5. Simplifying field validation rules
- **Before:** Same long rules repeated twice for first and last names
- **After:** Single bullet list for first name + note about same rules for last name
- **Why:** Avoids redundancy and improves clarity using "write for scanning" principle
- **See:** [Microsoft Writing Style Guide → Top 10 tips → Be brief](https://learn.microsoft.com/en-us/style-guide/top-10-tips-style-voice)

#### 6. Using consistent terminology
- **Before:** Mixed verbs for same action ("click", "push", "tap")
- **After:** Single consistent verb ("Select") for all UI interactions
- **Why:** Reduces cognitive load and prevents confusion through consistent terminology
- **See:** [Microsoft Writing Style Guide → Procedures → Describing interactions with UI](https://learn.microsoft.com/en-us/style-guide/procedures-instructions/describing-interactions-with-ui)
```