# HTML Form to Google Forms Backend

This project provides a simple way to use Google Forms as a backend database for your static HTML forms. It leverages Javascript to receive form submissions and automatically populate to Google Forms and a linked Google Sheet.

## How it Works

1.  **Javascript:** The script tag will:
    * Accept form data.
    * Extract the submitted data.
    * Send the data as a `POST` request to Google Forms and a linked Google Sheet.
    * Optionally redirect the user to a success or error page.

2.  **HTML Form Configuration:** Your HTML form needs to be configured to:
    * Submit data using the `POST` method.
    * Set the `action` attribute of the `<form>` tag to the URL of the deployed Google Apps Script web app.
    * Ensure the `name` attribute of your HTML form input fields matches the corresponding question titles in your Google Form (and the headers in the linked Google Sheet).

## Setup Instructions

1.  **Create a Google Form:** Design your Google Form with the fields you need.
2.  **Link to a Google Sheet:** Ensure your Google Form is linked to a Google Sheet where the responses will be stored.
3.  **Extract the name attributes from the form elements.
4.  **Update HTML Form:** In your HTML form, set the `action` attribute to the Google Form url you copied in the previous step. Ensure the `method` is set to `POST` and the `name` attributes of your input fields match your Google Form questions.

## Example HTML Form

```html
<form action="YOUR_WEB_APP_URL_HERE" method="post">
  <div>
    <label for="name">Name:</label>
    <input type="text" id="name" name="Name">
  </div>
  <div>
    <label for="email">Email:</label>
    <input type="email" id="email" name="Email Address">
  </div>
  <div>
    <label for="message">Message:</label>
    <textarea id="message" name="Your Message"></textarea>
  </div>
  <button type="submit">Submit</button>
</form>
