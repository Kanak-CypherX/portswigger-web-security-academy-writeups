
# Unprotected Admin Functionality with Unpredictable URL

## Challenge Information

| Field          | Details                          |
| -------------- | -------------------------------- |
| **Platform**   | PortSwigger Web Security Academy |
| **Category**   | Access Control                   |
| **Difficulty** | Easy                             |

## Problem Statement

This lab contains an administrator panel located at an unpredictable URL. Although the URL is not obvious, it is disclosed somewhere within the application.

**Objective:** Find the hidden administrator panel and delete the user **carlos**.

## Approach

* Explore the application carefully.
* Inspect the page source for hidden paths.
* Identify the administrator URL and access the admin panel.

## Solution

### Step 1 – Access the Lab

Open the PortSwigger lab and explore the application.

### Step 2 – View the Page Source & Identify the Hidden Admin Path

Right-click anywhere on the page and select **View Page Source**.

locate the hidden administrator path.

> <img width="628" height="712" alt="image" src="https://github.com/user-attachments/assets/0d433c8a-2552-42c6-8799-c4f69f8d8e2c" />

### Step 3 – Access the Administrator Panel

Append the discovered path to the application URL.

Example:

```text
https://LAB-ID.web-security-academy.net/admin-nflzsr
```

The administrator panel is displayed.

> <img width="783" height="211" alt="image" src="https://github.com/user-attachments/assets/5e7f71dc-3f9e-4fe7-af8e-75fb093bb57c" />

### Step 4 – Delete the User

Locate the user **carlos** and delete the account.

The lab is successfully solved.

> <img width="686" height="250" alt="image" src="https://github.com/user-attachments/assets/f402cc52-580a-4faf-9da6-b668556cc719" />

## Learning

* Hidden URLs are not a secure access control mechanism.
* Sensitive endpoints should always require proper authentication and authorization.
* Information disclosed in page source can expose administrative functionality.
