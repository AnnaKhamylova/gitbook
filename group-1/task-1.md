---
description: >-
  Test the endpoint, which updates user profile: `POST
  https://qa-test-task-6ceh.onrender.com/profile` . The endpoint accepts the
  fields `firstName, lastName, email, phone` ;
---

# Task 1

Notes before we start:

1. 'Fields' = body params, not query params.
2. How can we uderstand on which profile we should update data — it must be unique field, maybe email or special id. Or we should use query params? It is a key point. If we keep email as unique field, I guess there will be no opportunity to update it. So, let's say it's unique and can not be changed.
3. Usually we use limits for fields, like: email mask, limits for number of characters in firstName/lastName, phone mask, etc. Let's say here we should use both masks and limit of 256 characters for both names.
4. We restrict to delete information from any field, if it was not empty.
5. What do we expect to see in response? It is also a key question. Let's say here that we expect to see  "success" and "message" fields for both positive ang negative cases.
6. For full testing I need to see if this method really changed the data — and not just send me 200 and success. So I need to use GET method or access to the DB (both are preferrable). Or maybe we can send encrypted id/email of profile in response, so I can see the id of profile... There are many options, so we need to choose something.
7. We are going to test only functionality without perfomance, etc.
8. (optional question) Maybe we can use PUT or PATCH instead of POST? Why is it POST? That is not key point, but I am just interested.

Positive cases

<table data-view="cards"><thead><tr><th></th><th></th><th></th></tr></thead><tbody><tr><td><strong>Send request with new firstName and existant email</strong></td><td></td><td></td></tr><tr><td><strong>Send request with new secondName and existant email</strong></td><td></td><td></td></tr><tr><td>Send request with new phone and existant email</td><td></td><td></td></tr><tr><td><strong>Send request with new firstName, secondName, phone and existant email</strong></td><td></td><td></td></tr></tbody></table>

**Negative cases**

<table data-view="cards"><thead><tr><th></th><th></th><th></th><th></th><th></th></tr></thead><tbody><tr><td><strong>Send request with non-existant email</strong><br><br>I need access to GET method or DB.</td><td></td><td></td><td></td><td></td></tr><tr><td>Send request with invalid email</td><td></td><td></td><td></td><td></td></tr><tr><td>Send request without email</td><td></td><td></td><td></td><td></td></tr><tr><td>Send two requests with equal fields. </td><td></td><td><p>Request:</p><pre class="language-postman_json"><code class="lang-postman_json">{
    "firstName": "name",
    "lastName": "name",
    "email": "mailmail@mail.ru"
}
</code></pre></td><td>Expected response: ??? depends on requirements</td><td>If we accept that this is bug, severity would be low or medium — really depends</td></tr><tr><td>Send request without any changes in profile</td><td><strong>Note: we should restrict updating profile if no data was changed. This restriction should be on frontend, so we never send a request without changes, but let's check it here anyway</strong></td><td><p>Request:</p><pre class="language-postman_json"><code class="lang-postman_json">{
    "firstName": "name"//the same as in DB,
    "lastName": "name"// the same as in DB,
    "email": "mailmail@mail.ru"
}
</code></pre></td><td><p>Response:</p><pre class="language-json"><code class="lang-json">{
    "success": true,
    "message": "Profile saved successfully"
}
</code></pre></td><td>Severity — low</td></tr><tr><td>Send request with valid email and firstName > 256 characters</td><td></td><td>Severity — low</td><td></td><td></td></tr><tr><td>Send request with valid email and lastName > 256 characters</td><td></td><td>Severity — low</td><td></td><td></td></tr><tr><td>Send request with empty firstName and lastName</td><td></td><td></td><td></td><td></td></tr><tr><td>Send request without firstName</td><td></td><td></td><td></td><td></td></tr><tr><td>Send request without lastName</td><td></td><td></td><td></td><td></td></tr><tr><td>Send request with valid fields + invalid phone </td><td></td><td></td><td></td><td></td></tr><tr><td>Send request with two fields firstName</td><td></td><td></td><td></td><td></td></tr><tr><td>Send requests with letter in Russian layout in the name of field</td><td></td><td></td><td></td><td></td></tr><tr><td></td><td></td><td></td><td></td><td></td></tr></tbody></table>

