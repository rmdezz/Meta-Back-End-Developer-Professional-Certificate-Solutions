# Forms and validation

Forms are used to capture user input on websites, but it's important to make sure that the data entered is usable. Form validation is a process that checks if the user input is valid and meets the defined rules.

There are two methods of form validation: client-side validation and server-side validation.

# Client-side Validation

Client-side validation is performed by the web browser or JavaScript code and provides immediate feedback to the user. It checks for errors as soon as they are typed into the form and alerts the user of invalid data and how to change it for successful submission.

For example, using the **`input`** element with the **`type`** attribute set to **`email`** will validate the user's input as an email address. If the user enters an invalid email address, the browser will display an error message informing them of the error.

HTML provides several input types that can be validated by the browser, including:

- **`email`** for email addresses
- **`tel`** for telephone numbers
- **`url`** for URLs
- **`date`** for date values
- **`time`** for time values
- **`number`** for numeric values
- **`range`** for numeric values with a minimum and maximum value
- **`color`** for color selection

The **`required`** attribute can also be used to indicate that a value must be supplied to an input field. The browser will alert the user if a required value is missing.

## Examples of Client-side Validation using HTML and JavaScript:

### Required Field Validation

- HTML Code:

```python
<input type="text" required>
```

- JavaScript Code

```python
if (!form.elements[i].value) {
     alert("This field is required.");
}
```

### Email Validation

- HTML Code

```python
<input type="email">
```

- JavaScript Code

```python
var email = form.elements[i].value;
var reg = /^[a-zA-Z0-9._-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,4}$/;
if (!reg.test(email)) {
     alert("Please enter a valid email address.");
}
```

### Number Validation

- HTML Code

```python
<input type="number">
```

- JavaScript Code

```python
var number = form.elements[i].value;
if (isNaN(number)) {
     alert("Please enter a valid number.");
}
```

### Password Validation

- HTML Code

```python
<input type="password">
```

- JavaScript Code

```python
var password = form.elements[i].value;
if (password.length < 8) {
     alert("Password must be at least 8 characters long.");
}
```

# Server-Side Validation

Server-side validation checks for errors after the data has been submitted to the web server. It is more secure as it prevents malicious users from tampering with the website's code and submitting invalid data to the server.

When the form data is received by the server, the backend will validate the data before processing it. This validation can run more complex checks, such as checking the data against a database or validating the data against business requirements.

Most websites use both client-side and server-side validation to provide immediate feedback to users and to protect against malicious data submission and ensure data integrity.

# Conclusion

Form validation is a crucial step in capturing user input and ensuring that the data entered is usable. HTML provides several methods for client-side validation and server-side validation can be used for additional security. You'll learn more about HTML's validation capabilities in future lessons.