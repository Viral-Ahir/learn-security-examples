# Privilege Escalation

The example demonstrates a privilege escalation vulnerability and how to exploit it.

## Steps to reproduce

1. Install all dependencies

   `$ npm install`

2. Start the **insecure.ts** server

   `$ npx ts-node insecure.ts`

3. In the browser, send a GET request

   ```
       http://localhost:3000/send-form
   ```

4. Try different UserIds and see which one gives you authorized access to change the role of that user.

## For you to do

Answer the following:

1. Briefly explain the potential vulnerabilities in **insecure.ts**
   ANSWER -
   The potential vulnerability arises from relying on untrusted input from req.body without any proper authentication or authorization checks. The code assumes that the user is allowed to update the role based solely on the request, which makes it vulnerable to privilege escalation.
2. Briefly explain how a malicious attacker can exploit them.
   ANSWER -
   In this attacker can exploit this by sending a request to change another user's role, potentially escalating their privileges.
3. Briefly explain the defensive techniques used in **secure.ts** to prevent the privilege escalation vulnerability?
   ANSWER -
   The issue is fixed by using session-based authentication. It checks if the user is logged in and if they have the admin role before allowing any role changes, preventing privilege escalation.
