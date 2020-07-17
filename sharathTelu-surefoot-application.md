## Howdy, job seeker!

Below are 3 code exercises that will allow us to get a sense for your coding chops and give you exposure to the type of work you'd be doing on a regular basis to ensure you enjoy it. This is isn’t your standard front-end dev gig, as you’ll be writing code that is inserted into websites via 3rd party testing tools like Optimizely and Dynamic Yield. The below exercises are designed to reflect that.  

#### Instructions
1) Create a new gist containing the raw text from the below exercises
2) Name your gist `"yourName-surefoot-application.md"`
3) Add your code (in your new file) where indicated 
4) When complete, revisit the [job requirements](http://surefoot.me/jobs/engineer/) at the bottom of the description to ensure you're sending a complete application and :shipit:

Feel free to email jobs@surefoot.me with any questions.

---------------------------------------------------------
## Exercise 1: Form validation
*Hypothesis:* Adding form validation to the "name" and "message" fields of the email form will increase form submissions.

*Device type:* Desktop only  

*URL:* http://surefoot.me/engineer-application-sandbox/

*Dev notes:*
- Currently, the form only checks for a valid email.
- Please execute your code on DOM ready and use javascript to handle validation.
- Styling/layout of error messaging is up to you.
- Include a few lines of a README-esque description that explains your code to a non-technical person.

**Your code here:**

```
/* HTML file */
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Sure Foot Application</title>
    <link rel="stylesheet" type="text/css" href="./style.css">
    <script src="https://kit.fontawesome.com/5901743741.js"></script>  
</head>

<body>
    <div class="header">
        <h3 class="header-title title"> You have arrived, welcome! </h3>
        <p class="header-content">Thanks for your interest in our available engineer role! If you have any questions, 
            please refer to the original application page or email us - hello@surefoot.me.
        </p>
    </div>
    <div class="container">
        <div class="schedule-call-container">
            <h4 class="call-title title">schedule a call</h4>
            <p class="call-content">once scheduled you will receive a calendar invitation and follow-up email confirming 
                call details
            </p>
            <button class="call-button button"type="submit">schedule your call now</button>
        </div>
        <div class="form-container">
            <h4 class="form-title title">or shoot us an email</h4>
            <form class="form">
                <div class="form-control">
                    <p class="error-message">Error</p>
                    <input type="text" id="name" placeholder="first and last name">
                </div>
                <div class="form-control">
                    <p class="error-message">Error</p>
                    <input type="text" id="email" placeholder="email address">
                </div>
                <div class="form-control">
                    <p class="error-message">Error</p>
                    <textarea id="message" placeholder="your message"></textarea>
                </div>
                <button class="form-submit button" type="submit">send</button>
            </form>
        </div>
    </div>
    <div class="modal-bg">
        <div class="modal">
            <i class="fas fa-times close"></i>
            <h3>Whoops! Looks like we already received your application. We, appreaciate your
                patience while your application is under review.
            </h3>
            <img src=https://media.giphy.com/media/XbxZ41fWLeRECPsGIJ/giphy.gif>
        </div>
    </div>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/3.2.1/jquery.min.js"></script>
    <script src="./app.js"></script>
</body>
</html>

```
/* Form Validation Code */
```
$(document).ready(function() {   
    let form = document.querySelector('.form');
    let name = document.querySelector('#name');
    let email = document.querySelector('#email');
    let message = document.querySelector('#message');
    
    form.addEventListener('submit', (event) => {
        event.preventDefault();
        validate();
    })

    function validate() {
        let checkName = name.value.trim();
        let checkEmail = email.value.trim();
        let checkMessage = message.value.trim(); 
        if(!checkName) {
            let formControl = name.parentElement;
            let errorMessage = formControl.querySelector('.error-message');
            errorMessage.classList.add('show-error');
            errorMessage.textContent = "enter a valid name";
            return false;
        }

        if(!validateEmail(checkEmail)) {
            let formControl = email.parentElement;
            let errorMessage = formControl.querySelector('.error-message');
            errorMessage.classList.add('show-error');
            errorMessage.textContent = "enter a valid email";
            return false;
        }

        if(!checkMessage) {
            let formControl = message.parentElement;
            let errorMessage = formControl.querySelector('.error-message');
            errorMessage.classList.add('show-error');
            errorMessage.textContent = "please enter a message";
            return false;
        }

        if(checkMessage.length > 150) {
            let formControl = message.parentElement;
            let errorMessage = formControl.querySelector('.error-message');
            errorMessage.classList.add('show-error');
            errorMessage.textContent = "please keep the message less than 150 characters";
            return false;
        }

        function validateEmail(email) {
            const re = /^(([^<>()\[\]\\.,;:\s@"]+(\.[^<>()\[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;
            return re.test(String(email).toLowerCase());
        }
        return true;
    }
});

```
/* Code Break-Down */
```
*  We have a created a form by using HTML. Now we need to validate the form before submission. 
For Example, If the user does not enter the correct data or leaves a field empty we need to display an error.

* For form validation we need JavaScript.

* In the JavaScript file, we have two functions. 'addEventListener' and 'validate'. When the send button is clicked the addEventListener function executes the code inside validate function which is responsible for validating the form.
   
* In the validate function, we check for any missing fields, incorrect email and message length which should be less than 150 characters. 

*If all the above conditions are passed, the function returns a value of 'true' otherwise an error message is displayed and the function returns 'false'.

---

## Exercise 2: Form restyling

*Hypothesis:* Swapping the position of the two forms and restyling the email form will increase email form submissions.

*Device type:* Desktop only

*URL:* http://surefoot.me/engineer-application-sandbox/

*Mockup:* https://goo.gl/oMM3Pe

*Dev notes:*
- Swap the positions of the "schedule a call" and email forms.
- Restyle the form to resemble the mockup but don't worry too much about pixel perfection.
- Include a few lines of a README-esque description that explains your code to a non-technical person.


**Your code here:**

```
/* Form Restyling Code */
```
@import url('https://fonts.googleapis.com/css2?family=Cabin:wght@400;700&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Open+Sans:wght@300&display=swap');

* {
    box-sizing: border-box;
}

body {
   font-family: 'Cabin', sans-serif;
   margin: 5vh;
}

.title {
    color: #522fae;
    font-size: 2em;
    margin-bottom: 0;
}

.button {
    color: #ffffff;
    background-color: #522fae;
    border-radius: 3px;
    border: none;
    font-size: 1.1em;
    font-weight: 600;
    letter-spacing: 0.1em;
    cursor: pointer;
}

.button:hover {
    background-color: orange
}

.button:focus {
    outline: none;
}

/* Header */
.header-content {
    font-size: 1.1em;
    width: 60%;
    font-family: 'Open Sans', sans-serif;
}

.container {
    display: grid;
    grid-template-columns: 1fr 1fr;
}

/* Call */
.call-content {
    font-size: 0.95em;
    font-family: 'Open Sans', sans-serif;
    width: 80%;
}

.call-button {
    padding: 1.8vh 6vh;

}

/* Form */
.form {
    display: flex;
    flex-direction: column;
    width: 60%;
}
.form-title {
    margin-bottom: 2vh;
}

.form-control {
    position: relative;
    width: 100%;
}

.form-control>input, .form-control>textarea {
    margin-top: 3vh;
    border-radius: 3px;
    border: none;
    background-color: #efefef;
    color: #5a5a5a;
    font-size: 0.9em;
}

.form-control>input:focus, .form-control>textarea:focus {
    outline: none;
}

.form-control>input{
    padding: 1.5vh;
    width: 28vw;
    margin-top: 3vh;
}

.form-control>textarea {
    padding: 1.5vh;
    width: 28vw ;
    padding-bottom: 12vh;
    font-size: 1.1em;
}

.form-submit {
    margin-top: 3vh;
    padding: 1.8vh;
    align-self: flex-end;
}

.error-message {
    margin-bottom: 0;
    visibility: hidden;
    position: absolute;
    top: -2vh;
    left: 0;
    color: red;
}

.show-error {
    visibility: visible;
}

```
/* Code Break-Down */
```
* Like we discussed, we have created the form using HTML. But, HTML only creates a bare-bones structure. Now we need to style the form to make it look pretty. For Example, we need to add color, height, width etc to the form elements.

* Styling is done using CSS.

* There are multiple ways to select or target the HTML elements in CSS. Here are three ways to do it

  * Using Class Name. This is represented by a dot. For Example, ".className".
  * Using ID. This is represented by a hash. For Example, "#idName".
  * Using element name. Representing directly using element name. For Example, "body", "h1" "p" etc.

* Now, after selection we need to add properties like color, size etc. Below is an example of how we can do it using className.

  .title {
    color: red;
    font-size: 16px;
  }   

---

## Exercise 3: Cookie monster

*Hypothesis:* Disallowing return users to resubmit the email form will decrease spam.

*Device:* Desktop only

*URL:* http://surefoot.me/engineer-application-sandbox/

*Dev Notes:*
- If user has already submitted the email form, don’t allow them to resubmit. Instead, show the message "Hmm, you look familiar. While you're waiting for our reply, here's a GIF we think you should see."
- GIF can be anything you desire.
- Styling of messaging is up to you.
- Include a few lines of a README-esque description that explains your code to a non-technical person.


**Your code here:**
```
/* CSS */
```

/* Modal */
.modal-bg {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100vh;
    background-color: rgba(248,246,246,0.5);
    display: flex;
    justify-content: center;
    visibility: hidden;
    opacity: 0;
}
 
.bg-active {
    visibility: visible;
    opacity: 1;
}
 
.modal {
    background-color: #efefef;
    width: 500px;
    height: 500px;
    margin-top: 40px;
    display: flex;
    flex-direction: column;
    border-radius: 5px;
    position: relative;
}
 
.modal > h3 {
    align-self: center;
    margin: 5rem 3rem 2rem;
    color: #522fae;
}

.modal > img {
    width: 250px;
    height: 250px;
    align-self: center;
}

.close {
    position: absolute;
    top: 20px;
    right: 20px;
    color: #522fae;
    font-size: 2em;
    cursor: pointer;
}

```
/* Cookie Monster Code */
```
$(document).ready(function() {   
    let form = document.querySelector('.form');
    let name = document.querySelector('#name');
    let email = document.querySelector('#email');
    let message = document.querySelector('#message');
    let modalBg = document.querySelector('.modal-bg');
    let closeBtn = document.querySelector('.close');

    form.addEventListener('submit', (event) => {
        event.preventDefault();
        let emailValue = email.value.trim();
        if(validate()) {
           preventReSubmission(emailValue);
        }
    });

    closeBtn.addEventListener('click', closeModal);

    function validate() {
        let checkName = name.value.trim();
        let checkEmail = email.value.trim();
        let checkMessage = message.value.trim(); 
        if(!checkName) {
            let formControl = name.parentElement;
            let errorMessage = formControl.querySelector('.error-message');
            errorMessage.classList.add('show-error');
            errorMessage.textContent = "enter a valid name";
            return false;
        }

        if(!validateEmail(checkEmail)) {
            let formControl = email.parentElement;
            let errorMessage = formControl.querySelector('.error-message');
            errorMessage.classList.add('show-error');
            errorMessage.textContent = "enter a valid email";
            return false;
        }

        if(!checkMessage) {
            let formControl = message.parentElement;
            let errorMessage = formControl.querySelector('.error-message');
            errorMessage.classList.add('show-error');
            errorMessage.textContent = "please enter a message";
            return false;
        }

        if(checkMessage.length > 150) {
            let formControl = message.parentElement;
            let errorMessage = formControl.querySelector('.error-message');
            errorMessage.classList.add('show-error');
            errorMessage.textContent = "please keep the message less than 150 characters";
            return false;
        }

        function validateEmail(email) {
            const re = /^(([^<>()\[\]\\.,;:\s@"]+(\.[^<>()\[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;
            return re.test(String(email).toLowerCase());
        }
        return true;
    }
    
    function preventReSubmission(email) {
        if(!localStorage.getItem(email)) {
            localStorage.setItem(email, 1);
        }
        else {
            modalBg.classList.add('bg-active');
        }
    }

    function closeModal() {
        modalBg.classList.remove('bg-active');
    }
});

```
/* Code Break-Down */
```
* To prevent the form from re-submitting, we save the email id's in the local storage of the browser. Data in the local storage is present until the user clears the browsing history, cookies. 

* Now we can check if the email is already registered directly on the browser instead of checking for it in the database.

* For this, we have written a function 'preventReSubmission'. Here, if the email is not already registered it is added to the local storage. Otherwise, a message is popped up preventing the form from resubmission.