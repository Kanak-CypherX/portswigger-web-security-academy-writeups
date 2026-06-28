
# Username Enumeration via Different Responses

## Challenge Information

| Field | Details |
|-------|---------|
| **Platform** | PortSwigger Web Security Academy |
| **Category** | Authentication |
| **Difficulty** | Easy |

## Problem Statement

This lab is vulnerable to username enumeration. The application returns different error messages for invalid usernames and incorrect passwords, allowing an attacker to identify valid usernames.

**Objective:** Enumerate a valid username, identify the correct password, and log in to the application.

## Approach

- Observe the application's login responses.
- Compare the error messages for invalid usernames and incorrect passwords.
- Identify a valid username based on the response difference.
- Perform password enumeration for the valid username.
- Log in successfully.

## Solution

### Step 1 – Open the Lab

Launch the PortSwigger Web Security Academy lab.

> <img width="1095" height="425" alt="image" src="https://github.com/user-attachments/assets/18f15330-e3d4-46d6-a5f6-d78f1bab0c58" />

### Step 2 – Capture the Login Request

Intercept the login request using Burp Suite.

Send the request to **Intruder**.

> <img width="1250" height="650" alt="image" src="https://github.com/user-attachments/assets/9126b4ad-cebd-4e22-a53c-0bfea827b6e2" />

### Step 3 – Enumerate Usernames

Use the username wordlist while keeping the password constant.

Observe the server responses.

One username returns a different response, indicating it is valid.

> <img width="1138" height="571" alt="image" src="https://github.com/user-attachments/assets/fa2f0fc0-c3e3-4bf5-889e-c1a9aded32db" />

<img width="1121" height="301" alt="image" src="https://github.com/user-attachments/assets/9ed366d5-bf77-4d90-9be4-67d061c4caac" />

### Step 4 – Enumerate Passwords

Use the discovered username.

Keep the username fixed and perform a password attack using the password wordlist.

> <img width="1202" height="602" alt="image" src="https://github.com/user-attachments/assets/d5b54af2-0f2d-4a07-a318-7120b009f2d9" />

<img width="1084" height="329" alt="image" src="https://github.com/user-attachments/assets/4683f8ec-9cfc-4ddf-87c3-97b6f8f02811" />

### Step 5 – Login Successfully

Use the valid username and password to log in.

The lab is successfully solved.

> <img width="789" height="375" alt="image" src="https://github.com/user-attachments/assets/00bce543-085f-4971-8ce7-781e52646930" />

## Learning

- Applications should return generic authentication error messages.
- Different responses can allow attackers to enumerate valid usernames.
- Rate limiting and account lockout mechanisms help reduce brute-force attacks.
- Authentication responses should not reveal whether a username exists.
