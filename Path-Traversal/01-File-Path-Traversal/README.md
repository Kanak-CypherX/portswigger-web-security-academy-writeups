# File Path Traversal – Simple Case

## Challenge Information

| Field          | Details                                      |
| -------------- | -------------------------------------------- |
| **Platform**   | PortSwigger Web Security Academy             |
| **Category**   | Server-side Vulnerabilities – Path Traversal |
| **Difficulty** | Easy                                         |

## Problem Statement

This lab contains a path traversal vulnerability in the display of product images.

**Goal:** Retrieve the contents of the `/etc/passwd` file.

## Approach

* Open the lab in Burp Suite.
* Capture the request containing the `filename` parameter.
* Send the request to Repeater.
* Modify the `filename` parameter to perform a path traversal attack.

## Solution

### Step 1 – Open the Lab

Launch the PortSwigger lab in Burp Suite Browser.

> <img width="1088" height="404" alt="Screenshot 2026-06-28 154155" src="https://github.com/user-attachments/assets/12a4249e-e00b-473e-9980-fac482ad5707" />

### Step 2 – Capture the Request & Send the Request to Repeater

Turn **Intercept ON** and capture the request that contains the `filename` parameter.
Right-click the request and select **Send to Repeater**.

> <img width="1095" height="571" alt="Screenshot 2026-06-28 154333" src="https://github.com/user-attachments/assets/66400d75-feaa-4fc0-a10f-38cd7f4fd467" />

### Step 3 – Modify the Payload

Replace the filename with:

```http
../../../etc/passwd
```

Send the request.

> <img width="1049" height="578" alt="image" src="https://github.com/user-attachments/assets/4743b6e5-0f3e-4932-bd2a-c25df27450f6" />

### Step 4 – Observe the Response

The server responds with **200 OK** and returns the contents of the `/etc/passwd` file.

The lab is successfully solved.

> <img width="829" height="558" alt="image" src="https://github.com/user-attachments/assets/abca8ac8-223a-4fa2-ba91-a0bf97032f8f" />


## Learning

* Learned how Path Traversal vulnerabilities occur.
* Practiced modifying HTTP requests using Burp Suite Repeater.
* Understood the importance of validating file paths on the server side.

