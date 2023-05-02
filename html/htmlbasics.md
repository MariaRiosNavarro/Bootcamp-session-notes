
#HTML

##Index


- to check

-[HTML Forms](https://github.com/neuefische/ffm-web-23-3/blob/main/sessions/html-forms/html-forms.md)

-



<hr>

#HTML Forms

The <form> tag must be wrapped around the complete form with all elements, that are presented as form controls to the user.
Each fragment of information (each form field) requires a unique name. It can be set with the name attribute and pairs up with the entered data, when submitting the form.
It is required to define, which label and form field belong together. Use the for attribute on the <label> and the id attribute on the form field. Their values needs to match.

  ```
  <label for="first-name">First name</label>
  <input name="first-name" id="first-name" />
  ```
 
  Different types of form fields:
  
  text, email, number, data, color
  
  Multi-line text: <textarea>
  
  ````
  <label for="personal-message">Personal Message</label>
  <textarea name="personal-message" id="personal-message"></textarea>
  ````
  
  
  
  
  Select / dropdown menu
The <select> field lets the user choose between different options wrapped into <option> tags that are nested into their parent <select> tag - this renders a dropdown menu. Each <option> has a value attribute defining the data to be submitted. 
The option's text presented to the user is defined between the opening and closing tag.
  
  ````
  <label for="billing-plan">Billing plan</label>
<select name="billing-plan" id="billing-plan">
  <option value="weekly">Weekly billing</option>
  <option value="monthly">Monthly billing</option>
  <option value="yearly">Monthly billing</option>
</select>
  `````
  
 Radio elements
The <input type="radio" /> element is another way of presenting a choice with different options to the user. In many situations it can be used as an alternative to <select>.
  
  ````
  <input
  type="radio"
  name="billing-plan"
  id="billing-plan-weekly"
  value="weekly"
/>
<label for="billing-plan-weekly">Weekly billing</label>

<input
  type="radio"
  name="billing-plan"
  id="billing-plan-monthly"
  value="monthly"
/>
<label for="billing-plan-monthly">Monthly billing</label>

<input
  type="radio"
  name="billing-plan"
  id="billing-plan-yearly"
  value="yearly"
/>
<label for="billing-plan-yearly">Yearly billing</label>
  
  ````
  
  ❗️ The name attribute must be equal among all radio elements that refer to the same choice. The browser groups them together and ensures only one radio element can be selected at the same time.
  
  
  Checkboxes
In contrast to the radio element, <input type="checkbox" /> presents individual choices, that are not related to each other. Each choice can either be "on" ("true") or "off" ("false").
  
  ````
  <input type="checkbox" name="accept-data-privacy" id="accept-data-privacy" />
<label for="accept-data-privacy">I accept the data privacy agreement </label>

<input
  type="checkbox"
  name="accept-terms-conditions"
  id="accept-terms-conditions"
/>
<label for="accept-terms-conditions">I accept the terms and conditions </label>
  
  ````
  
  [more inputs here](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input)  
  
  
 Buttons types: submit, reset, button
  
  
 Fieldset and Legend:
  
  The ```<fieldset>``` element is used to group multiple fields together. Use the <legend> element to provide a caption for such a group.
  
  ````
  <fieldset>
  <legend>Personal information</legend>

  <label for="first-name">First name</label>
  <input type="text" name="first-name" id="first-name" />

  <label for="email">Email address</label>
  <input type="email" name="email" id="email" />
</fieldset>
  
  ````
  
  aria labels: The aria-label attribute defines a label for an interactive element. Use it when the accessible name is missing and there is no content visible in the DOM that can be referenced via the aria-labelledby attribute, e.g. a button with no text but only an icon:
  The aria-labelledby attribute identifies which element labels the element it is applied to. Use the id attribute to create the connection:
  ````
<h2 id="title">Personal Information Form</h2>
<form aria-labelledby="title">...</form>
  ````
  
  aria-describedby
  
  The aria-describedby attribute allows more verbose information than a label. Use the id attribute to create the connection:
  
  ````
  <p id="description">
  We need some personal information about you in order to proceed. Please fill
  in this form so that we can help you.
</p>
<fieldset aria-describedby="description">...</fieldset>
  ````

  
