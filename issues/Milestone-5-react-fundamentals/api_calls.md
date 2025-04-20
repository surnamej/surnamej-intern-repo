# Milestone: React Fundamentals

## Making API Calls with Axios

### Goal

Learn how to set up and manage API requests using Axios in a React project.

### Why is this important?

Focus Bear relies on API calls for authentication, payments, and data retrieval. Understanding how to use Axios properly ensures that API requests are efficient, secure, and well-structured.

## Tasks

- [x] Research how Axios works and why it's commonly used for API calls.
Axios is a popular JavaScript library used to make HTTP requests from the browser or Node.js. It simplifies the process of making requests and handling responses, providing a clean and intuitive API. Axios supports promises, making it easy to handle asynchronous operations using async/await syntax.

Why use Axios?:

- Axios provides a simple API for making HTTP requests, which is more concise and easier to use compared to the Fetch API.
- Axios allows you to intercept requests and responses, enabling you to modify or handle them globally.
- Axios has built-in error handling, making it easier to manage errors compared to the Fetch API2.
- Axios uses XMLHttpRequest under the hood, which is supported by most browsers, including older ones1.

- [x] Set up an Axios instance with the following requirements:
  Install Axios by: `npm install axios`
  - A base URL for API requests.
  - Default headers (including accept: "*/*" and a dynamically generated request ID).
  - Request timeouts to prevent hanging requests.
  - Request cancellation using AbortController.
- [x] Add an Axios request interceptor that:
  - Retrieves an authentication token from local storage.
  - Attaches the token to the request headers if available.
  - Properly handles errors.
- [x] Make a test API request that:
  - Sends a POST request to an endpoint with parameters.
  - Handles the response and redirects if necessary.

- [x] Push your Axios setup to GitHub.
- [x] Reflection (in api_calls.md):
  - Why is it useful to create a reusable Axios instance?
  Creating a reusable Axios instance centralizes configuration for API calls. This approach ensures that all requests share the same base URL, default headers, timeout settings, and interceptors, reducing code duplication. It simplifies maintenance and makes it easier to update configuration details (such as API endpoints or headers) across the entire application.

  - How does intercepting requests help with authentication?
  Using a request interceptor allows me to automatically attach an authentication token to every outgoing API call. By retrieving the token from local storage and appending it to the request headers, I ensure that secured endpoints receive the proper credentials without requiring additional code in each component. This leads to a more consistent and secure approach for handling authentication.

  - What happens if an API request times out, and how can you handle it?
  If an API request exceeds the specified timeout (e.g., 10 seconds), Axios will throw a timeout error (often indicated by the code `ECONNABORTED`). Handling such timeouts is crucial to avoid leaving the application waiting indefinitely. In my setup, I catch the timeout error to log it and can further implement user notifications, retry logic, or fallback mechanisms to ensure a smooth user experience.
