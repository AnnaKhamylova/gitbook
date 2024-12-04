---
description: >-
  Test the corresponding frontend interface available at
  https://qa-test-task-6ceh.onrender.com/ (note that it may take some time for
  the website to load). Please analyze identified bugs and attach s
---

# Task 3

Should I test only frontend? I have no Figma or requirements, so let's test everything we can — but only functional.

Before all I can say that in real world we should authorize before editing the profile.

Positive cases

* Fill all fields in profile settings and tap 'Save'. &#x20;

Result: weird text for error and 404 not found. In response also no explanation of error.

<figure><img src="../.gitbook/assets/Снимок экрана 2024-12-04 в 16.40.41.png" alt=""><figcaption></figcaption></figure>



<figure><img src="../.gitbook/assets/Снимок экрана 2024-12-04 в 17.00.57.png" alt=""><figcaption></figcaption></figure>

Expected result: We can wee 2xx success and success message. If we have an error it should be with message-explanation for user.

* Fill password and confirmPassword with 8-length equal passwords.

Negative cases



Notes

