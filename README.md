# Task3-SoftwareDepartment
https://wasanproject2984.infy.click/ccc/?i=1

## PHP Debugging

### Problem

After uploading the project to the hosting server, the chatbot interface loaded successfully. However, whenever the user sent a message, the application displayed the following error:
<img width="1640" height="1640" alt="IMG_0705" src="https://github.com/user-attachments/assets/089af4ab-db4a-4ec8-91b5-5e57395db292" />



The front-end interface worked correctly, but the PHP backend failed to communicate with the Gemini API, preventing the chatbot from generating responses.

---

## Solution

The following modifications were made to resolve the issue:

1. Renamed the PHP file to `ro.php`.

2. Updated the AI model from:

```php
$model = "gemini-2.0-flash";
```

to:

```php
$model = "gemini-flash-latest";
```

3. Corrected the Gemini API endpoint.

**From:**

```php
$url   = "https://generativelanguage.googleapis.com/v1beta/models/{$model}:generateContent?key=" . GEMINI_API_KEY;
```

**To:**

```php
$url = "https://generativelanguage.googleapis.com/v1beta/models/gemini-flash-latest:generateContent?key=" . $API_KEY;
```

4. Updated the existing `config.php` file by adding the Gemini API key.

5. Added the following variable inside `config.php`:

```php
$API_KEY = "YOUR_GEMINI_API_KEY";
```

6. Modified the PHP code to load the API key from `config.php` instead of hardcoding it in the source code.

7. Tested the communication between the client, the PHP backend, and the Gemini API.

---

## Result

After applying these changes, the server connection issue was resolved successfully. The chatbot was able to send user messages to the Gemini API and display AI-generated responses correctly without any connection errors.

---

## Technologies Used

- HTML5
- CSS3
- JavaScript
- PHP
- Google Gemini API
- GitHub
- InfinityFree Hosting

---

## Project Structure

```text
Task3-SoftwareDepartment/
│
├── index.html
├── style.css
├── app.js
├── config.php
├── ro.php
└── README.md
```

---

## How to Run the Project

1. Upload all project files to a PHP-supported hosting server.
2. Add your Gemini API key inside `config.php`.
3. Open the website in your browser.
4. Send a message through the chatbot interface.
5. The PHP backend forwards the request to the Gemini API and returns the generated response.

---

## Screenshots

### Before Fix
The chatbot displayed the following error after sending a message:
<img width="1640" height="1640" alt="IMG_0705" src="https://github.com/user-attachments/assets/317d2947-021e-4ed0-a3d4-098b079ad727" />



### After Fix
The chatbot successfully connected to the Gemini API and returned AI-generated responses without any server connection errors.
<img width="1640" height="1640" alt="IMG_0706" src="https://github.com/user-attachments/assets/b020f9ed-c857-4d0f-9ddb-9c610e7884f6" />



