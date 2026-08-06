# Task3-SoftwareDepartment

## PHP Debugging

### Problem

After uploading the project to the hosting server, the chatbot interface loaded successfully. However, whenever the user sent a message, the application displayed the following error:

> "حدث خطأ أثناء الاتصال بالخادم، حاول مجددًا."

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

```text
https://generativelanguage.googleapis.com/v1beta/models/{$model}:generateContent
```

**To:**

```text
https://generativelanguage.googleapis.com/v1beta/models/gemini-flash-latest:generateContent
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

> "حدث خطأ أثناء الاتصال بالخادم، حاول مجددًا."

### After Fix

The chatbot successfully connected to the Gemini API and returned AI-generated responses without any server connection errors.

