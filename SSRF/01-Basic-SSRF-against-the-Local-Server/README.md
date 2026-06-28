# Basic SSRF against the Local Server

## Challenge Information

| Field | Details |
|-------|---------|
| **Platform** | PortSwigger Web Security Academy |
| **Category** | Server-Side Request Forgery (SSRF) |
| **Difficulty** | Hard |

## Problem Statement

This lab contains a stock check feature that fetches data from an internal system.

**Objective:** Exploit the SSRF vulnerability to access the administrator interface at `http://localhost/admin` and delete the user **carlos**.

## Approach

- Intercept the stock check request using Burp Suite.
- Identify the `stockApi` parameter.
- Modify the parameter to target the local server.
- Access the administrator panel and delete the user **carlos**.

## Solution

### Step 1 – Access the Lab

Open the lab and enable **Intercept** in Burp Suite.

Navigate to any product page.

> <img width="1027" height="555" alt="image" src="https://github.com/user-attachments/assets/3f9afd3e-f8ea-484b-847c-977676e790de" />

### Step 2 – Capture the Stock Check Request

Click **Check Stock** to intercept the request.

Send the intercepted request to **Repeater**.

> <img width="778" height="475" alt="image" src="https://github.com/user-attachments/assets/cea9ec97-6d08-4215-b9da-04c9e32540d9" />

### Step 3 – Identify the SSRF Parameter

Locate the `stockApi` parameter in the request.

Example:

```http
stockApi=http://stock.weliketoshop.net:8080/product/stock/check?productId=1
```

> <img width="755" height="325" alt="image" src="https://github.com/user-attachments/assets/aa27aa39-8325-4b00-a83d-fc868085996b" />

### Step 4 – Modify the Request

Replace the `stockApi` value with:

```http
http://localhost/admin
```

Send the modified request.

The response now displays the administrator interface.

> <img width="937" height="471" alt="image" src="https://github.com/user-attachments/assets/09fc9af3-5ae3-4a1e-a584-0de98169f6f4" />

<img width="846" height="456" alt="image" src="https://github.com/user-attachments/assets/a45619e8-fada-4d28-945a-b250de90aa65" />

### Step 5 – Delete the User

In the response, locate the delete link for **carlos**.

Copy the delete path and update the `stockApi` parameter with it.

Example:

```http
http://localhost/admin/delete?username=carlos
```

Send the request.

> <img width="856" height="327" alt="image" src="https://github.com/user-attachments/assets/d10c55d9-83b0-4004-9a86-3dbec457bc4b" />

### Step 6 – Lab Solved

Refresh the application.

The lab is successfully solved.

## Learning

- SSRF allows a server to send requests to internal systems on behalf of the attacker.
- Internal services such as `localhost` should never be directly accessible through user-controlled input.
- Applications should validate and restrict outgoing requests to trusted destinations.
