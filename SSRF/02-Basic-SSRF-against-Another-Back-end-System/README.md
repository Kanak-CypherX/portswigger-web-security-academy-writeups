# Basic SSRF against Another Back-end System

## Challenge Information

| Field | Details |
|-------|---------|
| **Platform** | PortSwigger Web Security Academy |
| **Category** | Server-Side Request Forgery (SSRF) |
| **Difficulty** | Medium |

## Problem Statement

This lab contains a stock check feature that fetches data from an internal system.

**Objective:** Use the stock check functionality to scan the internal `192.168.0.X` network, identify the server hosting the administrator interface on port `8080`, and delete the user **carlos**.

## Approach

- Capture the stock check request using Burp Suite.
- Identify the `stockApi` parameter.
- Enumerate the internal IP range (`192.168.0.1–255`).
- Find the host exposing the administrator interface.
- Access the admin panel and delete the user **carlos**.

## Solution

### Step 1 – Capture the Request

Open the lab and click **Check Stock**.

Intercept the request using Burp Suite and send it to **Repeater**.

> <img width="870" height="558" alt="image" src="https://github.com/user-attachments/assets/e7b5ac5a-8065-41fc-8f2a-e4dfc18b613c" />

<img width="918" height="510" alt="image" src="https://github.com/user-attachments/assets/164933d2-05d1-4a94-a30f-184171ae5d44" />

### Step 2 – Identify the SSRF Parameter

Locate the `stockApi` parameter in the request.

Example:

```http
stockApi=http://192.168.0.X:8080/
```

> <img width="1029" height="440" alt="image" src="https://github.com/user-attachments/assets/7001efa3-e9e0-41be-885f-dcb48dcdd10e" />

### Step 3 – Scan the Internal Network

Use Burp Suite Intruder to enumerate the internal IP range.

Set the payload position on the last octet of the IP address.

Example payload:

```text
192.168.0.1
192.168.0.2
...
192.168.0.255
```

Look for the response that returns **HTTP 200 OK**.

> <img width="1202" height="309" alt="image" src="https://github.com/user-attachments/assets/7f0f3167-4cdb-471b-a85c-982a2c6d9394" />

<img width="1192" height="289" alt="image" src="https://github.com/user-attachments/assets/9eadaf3f-d353-4581-96a4-f049671136cc" />

### Step 4 – Access the Administrator Panel

Once the correct IP is identified, update the request:

```http
http://192.168.0.X:8080/admin
```

Send the request.

The administrator panel is displayed.

> <img width="1086" height="552" alt="image" src="https://github.com/user-attachments/assets/ef0e816d-7895-42eb-9beb-5807468c0bc3" />

### Step 5 – Delete the User

Locate the delete link for **carlos**.

Copy the path and send a request similar to:

```http
http://192.168.0.X:8080/admin/delete?username=carlos
```

The user is deleted.

> <img width="1085" height="553" alt="image" src="https://github.com/user-attachments/assets/1ba3edd7-7c77-4e86-a2e6-7735d297d0be" />

### Step 6 – Lab Solved

Refresh the application.

The lab is successfully solved.

> <img width="1084" height="325" alt="image" src="https://github.com/user-attachments/assets/a5da6ae6-9bf8-4b03-8cef-155ca4f86db7" />

## Learning

- SSRF vulnerabilities can expose internal services that are not accessible from the internet.
- Internal IP addresses should never be trusted solely because they are part of a private network.
- Validate and restrict user-controlled URLs before making server-side requests.
- Burp Suite Intruder can be used to enumerate internal networks during SSRF testing.

