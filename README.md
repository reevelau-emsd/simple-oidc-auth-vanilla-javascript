# Simple OIDC Auth Vanilla Javascript

**Demonstration purposes! Consider to official keycloak js adapter for enhanced features and security**

This repository contains a simple HTML page with vanilla JavaScript designed to demonstrate the authentication and token retrieval functionalities using Keycloak's OpenID Connect (OIDC) endpoints.

## Prerequisites

- Docker: Needed to run an NGINX container to serve the virtual route `/callback`.
- A Keycloak server: You will need access to a Keycloak server to configure clients and realms.

## Configuration

Before running the demo, you need to update the JavaScript file with your specific Keycloak details. Edit the following constants in the script:

```javascript
const KEYCLOAK_CLIENT_ID = 'your-client-id';
const REDIRECT_URI = 'http://localhost:8080/callback'; // Make sure this matches the URI registered in Keycloak
const KEYCLOAK_SERVER_URL = 'https://yourkeycloak.endpoint/';
const KEYCLOAK_REALM = 'your.realm';
```

Ensure these values match your Keycloak client settings and realm configuration.

## Keycloak Client Setup

1. Log into your Keycloak admin console.
2. Create a new client or select an existing one.
3. Configure the client accordingly:
   - Set `Valid Redirect URIs` to include `http://localhost:8080/callback`.
   - In the `Web Origins` field, add a `+` to enable CORS settings for your callback domain.

## Running the Demo

To run the demo, use Docker to set up an NGINX server:

```bash
docker run --name nginx-keycloak -v ./html:/usr/share/nginx/html:ro -v ./conf.d:/etc/nginx/conf.d:ro -p 8080:80 -d nginx:latest
```

This command pulls the NGINX image, mounts the directory containing your HTML and JavaScript files to the appropriate path inside the container, and exposes the server on port 8080 of your localhost.

## Usage

Open your browser and navigate to `http://localhost:8080`. The demo page will guide you through the process of authenticating via Keycloak and showing the token response.
