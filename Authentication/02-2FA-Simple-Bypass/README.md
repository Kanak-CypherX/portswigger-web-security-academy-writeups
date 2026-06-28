# 2FA Simple Bypass

## Challenge Information

| Field | Details |
|-------|---------|
| **Platform** | PortSwigger Web Security Academy |
| **Category** | Authentication |
| **Difficulty** | Easy |

## Problem Statement

This lab uses a two-factor authentication (2FA) mechanism that is incorrectly implemented. After logging in as one user, it is possible to bypass the second authentication step and gain unauthorized access to another user's account.

**Objective:** Access Carlos's account page by bypassing the 2FA verification process.

## Approach

- Log in using the provided credentials.
- Observe the 2FA verification process.
- Analyze the requests in Burp Suite.
- Modify the request to bypass the second authentication step.

## Solution

### Step 1 – Login to the Application

Log in using the provided credentials.

**Username:** `wiener`

**Password:** `peter`

> <img width="579" height="261" alt="image" src="https://github.com/user-attachments/assets/9dd27d5c-2b12-49fd-a1f1-28aa0fca2166" />

### Step 2 – Intercept the 2FA Request

After logging in, Burp Suite intercepts the request for the two-factor authentication page.

Inspect the request and identify the parameters related to authentication.

> <img width="1051" height="510" alt="image" src="https://github.com/user-attachments/assets/8efeb139-59c6-4221-8211-03be8026fe32" />

### Step 3 – Modify the Request

Modify the request so that it references Carlos's account instead of the current user.

Forward the modified request.

### Step 4 – Bypass the Verification

The application grants access to Carlos's account without requiring the correct second-factor verification.

### Step 5 – Lab Solved

## Learning

- Two-factor authentication must always be enforced on the server side.
- Authentication workflows should validate every step before granting access.
- User-controlled parameters should never determine authentication state.
- Improper implementation of 2FA can lead to authentication bypass vulnerabilities.
