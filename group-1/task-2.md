---
description: >-
  Test the endpoint, which allows user to change password:          `POST
  https://qa-test-task-6ceh.onrender.com/change-password` . The endpoint accepts
  the fields `password, confirmPassword` ;
---

# Task 2

Notes before we start:

1. Fields' = body params, not query params.
2. How can we uderstand on which profile we should update data — it must be unique field, maybe email or special id. Or we should use query params? It is a key point. If we keep email as unique field, I guess there will be no opportunity to update it. So, let's say it's unique and can not be changed.
3. Usually we use limits for password, like: minimum 8 characters, must contain letters, digits and special symbols.
4. Password and confirmPassword must be equal and it is sensitive to layout of keyboard.

