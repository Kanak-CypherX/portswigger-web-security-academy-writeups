
# Unprotected Admin Functionality

## Challenge Information

| Field          | Details                          |
| -------------- | -------------------------------- |
| **Platform**   | PortSwigger Web Security Academy |
| **Category**   | Access Control                   |
| **Difficulty** | Easy                             |

## Problem Statement

This lab contains an unprotected admin panel.

**Goal:** Access the admin panel and delete the user **carlos**.

## Approach

* Explore the application for hidden resources.
* Check common files such as `/robots.txt`.
* Identify any sensitive paths disclosed by the application.

## Solution

### Step 1 – Access the Lab

Open the PortSwigger lab and explore the application.

> <img width="1069" height="517" alt="Screenshot 2026-06-28 161902" src="https://github.com/user-attachments/assets/33b546ca-fd7a-43f9-9a44-83928256d487" />

### Step 2 – Locate the Login Page

A login page is available. Attempting common credentials does not provide access.

### Step 3 – Check `robots.txt`

Append `/robots.txt` to the application URL.

The file reveals a disallowed path:

```text
/administrator-panel
```

> <img width="732" height="211" alt="image" src="https://github.com/user-attachments/assets/c7d96dbb-0315-4483-89e2-6a6f1169e21c" />

### Step 4 – Access the Admin Panel

Append the discovered path to the application URL:

```text
https://LAB-ID.web-security-academy.net/administrator-panel
```

The admin interface becomes accessible.

> <img width="837" height="278" alt="image" src="https://github.com/user-attachments/assets/6d5de3fa-71c3-4980-b1ac-0158790a66b8" />

### Step 5 – Delete the User

Locate the user **carlos** and delete the account.

The lab is successfully solved.

> <img width="857" height="257" alt="image" src="https://github.com/user-attachments/assets/16ad5694-3ac5-46e0-8088-15e3dc37b9fe" />

## Learning

* Sensitive administrative functionality should never be publicly accessible.
* Files such as `robots.txt` should not expose confidential paths.
* Administrative pages must be protected with proper authentication and authorization.
