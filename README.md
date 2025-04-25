# HTML Form to Google Forms

This project provides a simple way to use Google Forms as a backend database for your static HTML forms. It leverages Javascript to send form data and automatically populate to Google Forms and a linked Google Sheet.

## How it Works

1.  **Javascript:** The script tag will:
    * Accept form data.
    * Extract the submitted data.
    * Send the data as a `GET` request to Google Forms and a linked Google Sheet.
    * Optionally alert the user of success.

2.  **HTML Form Configuration:** Your HTML form needs to be configured to:
    * Submit data using the `GET` method.
    * Set the `endpoint` variable inside the `<script>` tag to the URL of the public Google Forms url.
    * Ensure the `name` attribute of your HTML form input fields matches the corresponding name attributes in your Google Form.

## Setup Instructions

1.  **Create a Google Form:** Design your Google Form with the fields you need.
2.  **Link to a Google Sheet:** Ensure your Google Form is linked to a Google Sheet where the responses will be stored.
3.  **Extract the name attributes from the form elements.
4.  **Update HTML Form:** In your HTML form, set the `endpoint` variable in the script tag to the Google Form url you copied in the previous step.
5.  Ensure the `name` attributes of your input fields match your Google Form input attributes.

## Example HTML Form
[https://tefftechnologies.github.io/Google-Forms-DB/](https://tefftechnologies.github.io/Google-Forms-DB/)

```html
<form  id="gform">
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
```

```javascript
  const form = document.querySelector("#gform")
  form.addEventListener('submit', (event) => {
          event.preventDefault();
          formSubmit();
          alert("Data has been sent to Google Forms");
  })

  const formSubmit = async () => {
      const formData = new FormData(form);

      const convertFormEntries = Array.from(
          formData,
          ([key, value]) => (
              [key, typeof value === 'string' ? value : value.name]
          ),
      );

      const queryString = new URLSearchParams(convertFormEntries).toString();

      const endpoint = "[GOOGLE FORM URL]";
      
      try {
          const response = await fetch(endpoint + '?' + queryString, {
              method: "GET",
          });
      } catch (e) {
          console.error(e)
      }
  }
