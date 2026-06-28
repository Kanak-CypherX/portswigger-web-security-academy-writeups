# User ID Controlled by Request Parameter with Unpredictable User IDs

## Challenge Information

| Field          | Details                          |
| -------------- | -------------------------------- |
| **Platform**   | PortSwigger Web Security Academy |
| **Category**   | Access Control                   |
| **Difficulty** | Medium                           |

## Problem Statement

This lab contains a horizontal privilege escalation vulnerability on the user account page. Although users are identified using GUIDs, it is still possible to access another user's information.

**Objective:** Find Carlos's GUID and retrieve his API key.

**Credentials**

* Username: `wiener`
* Password: `peter`

## Approach

* Explore the application and locate a blog post written by Carlos.
* Identify Carlos's GUID from the blog URL.
* Modify the account request using Burp Suite.
* Replace your user ID with Carlos's GUID to access his account information.

## Solution

### Step 1 – Login to the Application

Open the lab and log in using the provided credentials.

**Username:** `wiener`

**Password:** `peter`

### Step 2 – Find Carlos's Blog

Browse the available blog posts and locate one written by **Carlos**.

Observe the URL and note the GUID present in the `userId` parameter.

> <img width="908" height="606" alt="image" src="https://github.com/user-attachments/assets/5612fe73-4fbd-45e3-b40a-39cc3f2a5130" />

<img width="1006" height="508" alt="image" src="https://github.com/user-attachments/assets/9a3ca4b1-c241-4158-9fc6-296b4463de4e" />

### Step 3 – Capture the Account Request & Modify the User ID

Open your account page and capture the request using Burp Suite.

Send the request to **Repeater**.

Replace your own GUID with Carlos's GUID obtained from the blog URL and Send the modified request.

### Step 5 – Retrieve the API Key

The response now displays Carlos's account information, including his API key.

Copy the API key and submit it to solve the lab.

> <img width="900" height="482" alt="Screenshot 2026-06-28 171149" src="https://github.com/user-attachments/assets/96cdb938-8c8a-4684-92fe-cd113a953988" />


## Learning

* GUIDs should not be treated as access control mechanisms.
* Applications must verify that users are authorized to access requested resources.
* Simply using unpredictable identifiers does not prevent horizontal privilege escalation.

