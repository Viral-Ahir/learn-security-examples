# Spoofing

This example demonstrates spoofind through two ways -- Stealing cookies programmatically and cross site request forgery (CSRF).

## Steps to reproduce the vulnerability

1. Install dependencies

   `$ npx install`

2. Start the **insecure.ts** server

   `npx ts-node insecure.ts`

3. Start the malicious server **mal.ts**

   `npx ts-node mal.ts`

4. Open **http://localhost:8000** in a browser, type a name and Submit.

5. Open the **Application** tab in the Browser's inspect pane. Find the **Cookies** under **Storage**. You should see a **connect.sid** cookie being set.

6. Open the HTML file **mal-steal-cookie.html** file in the same browser (different tab). Open inspect and view the console.

7. Click the link in the HTML file. Do you see the cookie being stolen in the console?

8. Open the HTML file **mal-csrf.html** file in the same browser (different tab). What do you see if the user has not logged out of **insecure.ts**? What do you see if the user has logged out?

## For you to answer

1. Briefly explain the spoofing vulnerability in **insecure.ts**.
   ANSWER -
   Insecure version doesn’t handle cookies securely. Since cookies aren’t marked as HttpOnly, they can be stolen by JavaScript in the browser. On top of that, there’s no sameSite protection, so cookies are sent with requests from other sites, making CSRF attacks possible. The app also doesn’t verify requests with CSRF tokens, making it easy for attackers to misuse a logged-in user’s session.
2. Briefly explain different ways in which vulnerability can be exploited.
   ANSWER -
   Attackers can steal session cookies by running malicious JavaScript on a user’s browser or exploit the CSRF vulnerability by tricking the user into clicking a malicious link or submitting a form.
3. Briefly explain why **secure.ts** does not have the spoofing vulnerability in **insecure.ts**.
   ANSWER -
   secure.ts fixes these issues by setting cookies as HttpOnly and using sameSite, preventing JavaScript access and blocking cross-site requests, thus protecting against cookie theft and CSRF attacks.
