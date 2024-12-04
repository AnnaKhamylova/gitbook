---
description: >-
  Test the endpoint, which allows user to change password:  `POST
  https://qa-test-task-6ceh.onrender.com/change-password` . The endpoint accepts
  the fields `password, confirmPassword` ;
---

# Task 2

Notes before we start:

1. Fields' = body params, not query params. If method will accept query params — it's high severity.
2. How can we uderstand on which profile we should update data — it must be unique field, maybe email or special id. Or we should use query params? It is a key point. If we keep email as unique field, I guess there will be no opportunity to update it. So, let's say it's unique and can not be changed. It's blocker for testing.
3. Usually we use limits for password, like: minimum 8 characters, must contain letters, digits and special symbols, it should not be equal to previous 3 password-combinations. These bugs would be medium severity.
4. Password and confirmPassword must be equal and it is sensitive to layout of keyboard. These bugs would be with high severity.

I think there is no sense in testing this endpoint without understanding point 2 — it's blocker.
