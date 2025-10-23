# Network API Documentation

Welcome to the Network API documentation portal. This project demonstrates a set of powerful, developer-friendly APIs based on the **GSMA Open Gateway (CAMARA)** standard.

These APIs abstract the complexity of global telecommunications networks, allowing developers to embed security, verification, and quality-of-service features directly into their applications.

## Why Use These Type of APIs?

Network APIs solve critical business challenges by securely exposing network capabilities. Instead of relying on less secure methods (like SMS OTP), you can leverage the network itself.

### Key Use Cases

- **Prevent Account Takeover (ATO) Fraud** – Use the **SIM Swap API** to verify if a user's SIM card has been recently changed *before* authorizing a sensitive transaction or password reset.

- **Secure User Authentication** – Use the **Number Verification API** to silently confirm that your user is in possession of a specific phone number, providing a frictionless and phishing-resistant alternative to SMS codes.

- **Guarantee Quality of Service (QoD)** – Use the **Quality on Demand API** to request a stable, high-priority network connection for lag-free cloud gaming or smooth 4K video streaming.

## Available APIs

This documentation project covers the following APIs:

- [SIM Swap API](./sim-swap-api.md) – Provides real-time information on the last SIM card change for a given phone number.
- [Number Verification API](./number-verification-api.md) – Confirms that a user is in possession of a specific phone number associated with their mobile network session.
- [Quality on Demand API](./qod-api.md) – Allows an application to request a specific network Quality of Service (QoS) profile.

Each section includes conceptual guides, how-to tutorials, and a full OpenAPI reference.

## Getting Started: Authentication

All Network APIs are secured using **OAuth 2.0 (Client Credentials Flow)**. To make your first call, you must obtain an access token. Follow these steps to do so:

1.  **Get Your Credentials:** Obtain your `CLIENT_ID` and `CLIENT_SECRET` from the developer portal.
2.  **Request a Token:** Make a `POST` request to the `/token` endpoint with your credentials.
3.  **Use the Token:** Include the returned `access_token` in the `Authorization` header of all your API requests as a Bearer token.

`Authorization: Bearer <YOUR_ACCESS_TOKEN>`

For a detailed walkthrough, refer to the **[Authentication Guide](./authentication.md)** topic.