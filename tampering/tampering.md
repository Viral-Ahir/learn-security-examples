# Tampering

This example demonstrates tampering through script injection.

## Steps to reproduce

1. Install all dependencies

   `npm install`

2. Start the **insecure.ts** server

   `npx ts-node insecure.ts`

3. In the browser, type a potentially malicious script in the name field of the form

   ```
       <script> document.body.innerHTML = "<a href='https://google.com'> Gotcha </a>"</script>
   ```

4. Do you see the potentially malicious hyperlink being injected into the form?

## For you to do

Answer the following:

1. Briefly explain the potential vulnerabilities in **insecure.ts**
   ANSWER -
   insecure.ts is vulnerable to Cross-Site Scripting (XSS) due to unsanitized user input. Malicious scripts submitted in the "name" field are directly used, allowing attacks like data theft or manipulation.
2. Briefly explain how a malicious attacker can exploit them.
   ANSWER -
   An attacker can inject a script in the "name" field. If the input isn’t sanitized, the script runs when the page loads, enabling actions like stealing cookies or redirecting users to harmful sites.
3. Briefly explain why **secure.ts** does not have the same vulnerabilties?
   ANSWER -
   secure.ts prevents XSS by sanitizing user inputs, ensuring any malicious scripts are neutralized before execution, protecting the app from harmful code injections.
