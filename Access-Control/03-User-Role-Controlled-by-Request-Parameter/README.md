
# User Role Controlled by Request Parameter

## Challenge Information

| Field          | Details                          |
| -------------- | -------------------------------- |
| **Platform**   | PortSwigger Web Security Academy |
| **Category**   | Access Control                   |
| **Difficulty** | Medium                           |

## Problem Statement

This lab contains an administrator panel at `/admin` that identifies administrators using a forgeable cookie.

**Objective:** Access the administrator panel and delete the user **carlos**.

**Credentials:**

* Username: `wiener`
* Password: `peter`

## Approach

* Log in using the provided credentials.
* Capture the authenticated request using Burp Suite.
* Inspect cookies and request parameters.
* Modify the administrator cookie to escalate privileges.

## Solution

### Step 1 – Login to the Application

Open the lab and log in using the provided credentials.

**Username:** `wiener`

**Password:** `peter`

> <img width="929" height="427" alt="image" src="https://github.com/user-attachments/assets/aa276749-8350-4243-b580-28b94324d18d" />

### Step 2 – Capture the Request

Turn **Intercept ON** in Burp Suite.

Capture the login request and send it to **Repeater**.

> <img width="1028" height="543" alt="image" src="https://github.com/user-attachments/assets/952fb6c6-add3-4721-aa33-dfd6d7de0e20" />

### Step 3 – Modify the Cookie

Locate the cookie that controls the administrator role.

Modify it from:

```http
Admin=false
```
to
```http
Admin=true
```

Send the modified request.

> <img width="711" height="453" alt="image" src="https://github.com/user-attachments/assets/17c21932-fef9-4226-b826-5e5a93a7c6bc" />

### Step 4 – Access the Admin Panel

The server now treats the session as an administrator.

Open the `/admin` endpoint to access the administrator panel.

### Step 5 – Delete the User

Locate the user **carlos** and delete the account.

The lab is successfully solved.

## Learning

* Never trust client-side cookies for authorization.
* User roles should always be validated on the server.
* Sensitive authorization data must not be modifiable by the client.
