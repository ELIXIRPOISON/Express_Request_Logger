# Request Logging Middleware in Node.js with Express

## Overview
This project is a Node.js application built with the Express framework. It demonstrates how to implement request logging middleware to capture and log details about incoming HTTP requests. Middleware is a core concept in Express, and this project helps understand its usage for improving observability and debugging in web applications.

## Key Features
1. **Custom Middleware**:
   - The `requestLogger` middleware is implemented to log essential details such as:
     - HTTP method (e.g., GET, POST)
     - Request URL (e.g., `/test`)
     - IP address of the client
     - Timestamps to know when the request occurred.
   - This information is displayed using `console.log`.

2. **Morgan Integration**:
   - Morgan, a popular HTTP request logger middleware, is included for advanced logging.
   - It provides preformatted log styles like `combined`, `common`, and `dev` for consistent and detailed logs.
   - Logs include request status, response time, and more, which helps in monitoring and troubleshooting.

3. **Global Middleware**:
   - The `requestLogger` middleware and Morgan are applied globally to ensure all incoming requests are logged automatically, regardless of the route.

4. **Simple Test Routes**:
   - Two example routes (`/` and `/test`) are provided to test the middleware:
     - `/` returns a "Hello, World!" response.
     - `/test` returns a JSON object to simulate an API response.

## How It Works
1. **Middleware Processing**:
   - When a client sends an HTTP request, it first passes through the middleware functions.
   - The `requestLogger` middleware captures the request details and logs them to the console.
   - Morgan, if enabled, logs the same request details in a structured format.

2. **Routing**:
   - After passing through the middleware, the request is handled by the appropriate route handler (e.g., `/` or `/test`).

3. **Server Response**:
   - The server sends the appropriate response (HTML or JSON) back to the client while the logs are generated in the terminal.

## Usage and Benefits
1. **Improved Observability**:
   - Helps developers monitor incoming requests and identify potential issues.
   - Captures useful information such as timestamps, which aids in debugging.

2. **Customizability**:
   - Custom middleware can be extended to include additional details like user agents or request headers.
   - Morgan's flexibility allows developers to log to files, filter sensitive data, and define custom formats.

3. **Scalability**:
   - The project can be expanded for production use by integrating advanced logging frameworks or services like Winston, Elasticsearch, or Datadog.

## Challenges Faced
1. **Understanding Middleware**:
   - Understanding the middleware execution flow and ensuring the `next()` function was correctly used to pass control.

2. **Log Verbosity**:
   - Managing verbosity and choosing the right log level (`info`, `debug`, etc.) for different environments (e.g., development vs. production).

3. **IP Logging**:
   - In environments behind proxies (e.g., NGINX), capturing the real client IP address requires enabling Express’s `trust proxy` setting.

## How to Run
1. **Install Dependencies**:
   ```bash
   npm install
