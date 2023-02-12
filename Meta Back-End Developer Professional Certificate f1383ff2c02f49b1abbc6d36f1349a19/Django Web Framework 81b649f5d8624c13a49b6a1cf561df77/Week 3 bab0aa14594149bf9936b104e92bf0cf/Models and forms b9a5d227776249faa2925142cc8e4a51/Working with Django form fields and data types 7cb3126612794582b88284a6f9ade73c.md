# Working with Django form fields and data types

## **Introduction**

- Often web applications collect data from the user through a HTML form and it's sent to the server for processing.
- You create a HTML form using various form elements such as input elements Radio buttons, Drop-down lists, and Checkboxes.
- In this video, you will learn how to use form fields to store correct data types in Django.

## **Building a Form**

- Suppose the manager of Little Lemon has asked you to build a customer form containing a customer's name and age.
- First, you build a HTML form that contains three input elements, one for the name, one for age, and one for the submit button.

## **Using Form Class**

- Previously, you learned that Django creates and processes forms using the Form class.
- This class defines all the expected attributes that will construct and process the form.

## **Form Fields**

- Once you lay out the structure of the form, Form fields are the building blocks that help build the form while fields are an integral part of models.
- They are especially important while using forms as they help define the visual element of the form.
- The custom logic behind the fields is defined in the Fields class used inside the Form class in Django.

## **Field Types**

- When defining attributes, you can choose from various field types.
- Some examples include:
    - CharField (for string input)
    - EmailField (for email format input)
    - IntegerField (for integers only)
    - MultipleChoiceField (for multiple options)
    - FileField (for file upload)

## **Field Arguments**

- Additionally, these form fields have different arguments that can be passed to them while specific arguments that can be passed vary according to the field and use.
- Some common arguments include:
    - Required (to mark a field as required or not)
    - Label (to specify a label for the field)
    - Initial (to set initial values for specific fields)
    - Help-text (to specify descriptive text for the field)

## **Customizing Form Fields**

- There are different widgets that can be used to customize form fields.
- For example, a widget such as Textarea can be used to override the default widget of an input field.
- It's important to remember that every form that you build will have different data requirements.

## **Form Validation**

- Django Form Fields have basic validation applied by default.
- For example, an email field will check if the input follows email format.

## **Examples**

- Let's open VS code now and explore the different fields that can be used to create a form and the customization options available.
- Examples include creating a form with a CharField, EmailField, IntegerField, MultipleChoiceField, and FileField.

## **Conclusion**

- It's important to know that these examples showcase just some of the available form fields and parameters you can use in Django.
- Exploring the Django documentation for all available options to help you create forms is a good idea.