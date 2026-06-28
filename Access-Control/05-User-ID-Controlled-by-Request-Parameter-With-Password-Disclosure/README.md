# User ID Controlled by Request Parameter with Password Disclosure

## Challenge Information

| Field          | Details                          |
| -------------- | -------------------------------- |
| **Platform**   | PortSwigger Web Security Academy |
| **Category**   | Access Control                   |
| **Difficulty** | Medium                           |

## Problem Statement

This lab contains an insecure account page that exposes the current user's password in a prefilled input field. By exploiting an insecure direct object reference (IDOR), it is possible to access another user's account information.

**Objective:** Retrieve the administrator's password, log in as the administrator, and delete the user **carlos**.

**Credentials**

* Username: `wiener`
* Password: `peter`

## Approach

* Log in using the provided credentials.
* Capture the account request in Burp Suite.
* Modify the user identifier to access the administrator's account.
* Retrieve the administrator's password.
* Log in as the administrator and delete the user **carlos**.

## Solution

### Step 1 – Login to the Application

Open the lab and log in with the provided credentials.

**Username:** `wiener`

**Password:** `peter`

> <img width="831" height="584" alt="image" src="https://github.com/user-attachments/assets/fef2cbc9-f874-4cfc-bd16-12319e7a678e" />

### Step 2 – Capture the Account Request

Navigate to the account page.

Intercept the request using Burp Suite and send it to **Repeater**.

### Step 3 – Modify the User ID & Retrieve the Administrator Password

Locate the parameter that identifies the current user.

Replace your user ID with:

```text
administrator
```

The response now displays the administrator's account information, including the prefilled password.

Copy the password.
Send the modified request.

> <img width="1306" height="663" alt="image" src="https://github.com/user-attachments/assets/d1803752-c83d-403a-b1a8-7523b9a7c87e" />

### Step 4 – Login as Administrator

Log out of the current account.

Sign in using the administrator credentials obtained in the previous step.

> 

### Step 5 – Delete the User

Open the administrator panel.

Locate the user **carlos** and delete the account.

The lab is successfully solved.

> <img width="1021" height="353" alt="image" src="https://github.com/user-attachments/assets/f243ba61-42ac-4e4d-9d21-82c08be06ea1" />

## Learning

* Sensitive information such as passwords should never be returned to the client.
* Access to user data must always be validated on the server.
* IDOR vulnerabilities can lead to unauthorized access and privilege escalation.
* Passwords should be securely hashed and never exposed in application responses.

