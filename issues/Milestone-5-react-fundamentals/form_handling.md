# Milestone: React Fundamentals

## Handling Forms with Formik

### Goal

Learn how to build and manage forms efficiently using Formik.

## Tasks

- [x] Research what Formik is and why it's useful for handling forms in React.
Formik is a popular open-source library for handling forms in React and React Native. It simplifies form state management, validation, and submission, making it easier to build complex forms with less code.

**Why is Formik Useful?**

- Formik manages form state, including values, errors, and touched fields, reducing the need for boilerplate code1.
- It integrates seamlessly with validation libraries like Yup, allowing for robust and scalable form validation.
- Formik handles form submission, including preventing default behavior and managing form state during submission1.
- With a simple and intuitive API, Formik makes it easy to build and maintain forms2.

Source: [Formik Docs](https://formik.org/docs/tutorial)

Install Formik and Yup: `npm install formik yup`

- [x] Create a form with the following fields:
  - Name (text input)
  - Email (validated with Formik & Yup)
  - A submit button
- [x] Use Formik’s useFormik hook or `<Formik>` component for form handling.
- [x] Implement basic validation using Yup.
- [x] Push your form component to GitHub.
- [x] Reflection (in form_handling.md):
  - How does Formik simplify form management compared to handling state manually?
    Formik centralizes and automates common tasks associated with form management:
    - **State Management:** Instead of creating individual state variables for each form field, Formik manages the entire form state in one place.
    - **Change Handling:** Formik automatically tracks user input and updates state, removing the need to write custom `onChange` handlers for every input.
    - **Error Handling:** It integrates validation (especially with libraries like Yup) seamlessly, handling errors and form-level validation without extra boilerplate code.
    - **Submission Handling:** Formik provides a standardized way to handle form submissions, including managing submission state and resetting forms.
  
  - What are the benefits of using Formik’s validation instead of writing validation logic manually?
    Using Formik’s validation, especially when combined with Yup, offers several benefits:
    - **Declarative Schema:** Validation rules are declared in a schema object, making them easier to read, maintain, and update.
    - **Consistency:** Ensures consistent validation across the application with less chance for human error.
    - **Less Boilerplate:** Eliminates the need for writing repetitive validation logic for each field, reducing code complexity.
    - **Integration:** Validation errors are automatically passed to the form components, allowing for straightforward error display using components like `ErrorMessage`.
    - **Extensibility:** Yup provides a robust set of built-in validators and allows for custom validations when needed.
