# SIM Swap API

**The SIM Swap API is a crucial security tool designed to combat Account Takeover (ATO) fraud.**

It allows your application to check if a phone number's SIM card has been recently changed (or "swapped"). This check helps you verify that you are interacting with the legitimate owner of the phone number, not a fraudster.

---

## The Business Problem: What is SIM Swap Fraud?

SIM Swap Fraud (or "port-out scam") is an increasingly common attack:

1.  **The Attack:** A fraudster tricks a mobile operator (through social engineering or an insider) into transferring a victim's phone number to a new SIM card controlled by the fraudster.
2.  **The Takeover:** The fraudster now receives all the victim's calls and SMS messages, including one-time passwords (OTPs) for banking, email, and social media.
3.  **The Damage:** The fraudster uses these OTPs to reset passwords and gain unauthorized access to the victim's sensitive accounts, often draining bank funds.

### How This API Solves the Problem

The SIM Swap API provides a critical layer of defense.

By calling this API **before** sending an SMS OTP or authorizing a high-risk transaction (like a password reset or large money transfer), your application can get an instant answer: "Has this phone number's SIM card changed in the last 24 hours?"

If the answer is **yes**, you can block the high-risk action and request stronger identity verification.

---

## Tutorial: How to Prevent ATO with the SIM Swap API

Let's walk through a common scenario: a user wants to reset their password using their phone number.

### Flowchart

`[User requests password reset]` → `[Your Server]` → `[Call SIM Swap API]` → `[Check Response]` → `[Block or Allow]`

### Step-by-Step Implementation

1.  **User Initiates Reset:** Your user enters their phone number `+34612345678` into your "Reset Password" form.
2.  **Server Makes Check (Backend):** Before sending an SMS, your server (which has a valid access token) calls the SIM Swap API.
    ```bash
    # This is a conceptual example.
    # Your server makes this call, not the user's browser.
    
    curl -X POST '[https://api.network.com/sim-swap/v1/check](https://api.network.com/sim-swap/v1/check)' \
    -H 'Authorization: Bearer <YOUR_ACCESS_TOKEN>' \
    -H 'Content-Type: application/json' \
    -d '{
          "phoneNumber": "+34612345678",
          "maxAgeHours": 24
        }'
    ```
3.  **API Responds:** The API checks with the mobile operator and returns a JSON response.

    **Scenario A (No Swap Detected):**
    ```json
    {
      "swapped": false
    }
    ```
    **Scenario B (Swap Detected):**
    ```json
    {
      "swapped": true,
      "lastSwapTimestamp": "2025-10-24T10:30:01Z"
    }
    ```

4.  **Your Server Applies Logic:**
    * **If `swapped: false`:** Everything is normal. You can safely proceed to send the SMS OTP.
    * **If `swapped: true`:** This is a **HIGH-RISK** signal. You should **NOT** send the SMS. Instead, redirect the user to a higher-friction verification method (e.g., "Please contact support," "Answer your security questions," or "Verify via your email").

---

## API Reference

This section details the technical specification of the SIM Swap API.

*(**Note for Portfolio:** In a real Docusaurus implementation, this section would automatically render an interactive OpenAPI specification. For now, this Markdown file links to the spec and provides a summary).*

**[➡️ View Full OpenAPI Specification (sim-swap.openapi.yaml)](./sim-swap.openapi.yaml)** (TBD)

### Endpoint: Check SIM Swap Status

**`POST /sim-swap/v1/check`**

This endpoint checks if a SIM swap has occurred for a given phone number within a specified time window.

#### Request Body

| Field | Type | Required | Description |
| :--- | :--- | :--- | :--- |
| `phoneNumber` | `string` | Yes | The phone number to check in E.164 format. |
| `maxAgeHours` | `integer`| No | *Optional.* The lookback period in hours. (Default: 24) |

**Example Request:**
```json
{
  "phoneNumber": "+34612345678",
  "maxAgeHours": 24
}
```

#### Responses

**`200 OK`** – Success

```json
{
  "swapped": boolean
}
```

  * **`swapped` (boolean):** `true` if a swap was detected within the `maxAgeHours` window, `false` otherwise.

**`400 Bad Request`** – Invalid Input

```json
{
  "error": "INVALID_PHONE_NUMBER",
  "message": "Phone number must be in E.164 format."
}
```

**`404 Not Found`** – Number Not Found

```json
{
  "error": "NOT_FOUND",
  "message": "The specified phone number was not found or is not subscribed to this service."
}
```