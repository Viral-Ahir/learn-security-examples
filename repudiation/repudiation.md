# Repudiation

The example demonstrates a vulnerability that can lead to repudiation by malicious users attempting to access the services provided by a server.

## Steps to reproduce

1. Install all dependencies

   `$ npm install`

2. Run the server **insecure.ts**.

3. Pretend to be a malicous user and interact with the services by sending requests from the browser.

4. Do you think your actions can be repudiated?

## For you to do

1. Briefly explain the vulnerability.
   ANSWER -
   The vulnerability arises from the lack of logging and authentication, making it difficult to track which user performed certain actions. Without proper logs, a malicious user could send requests without being held accountable, leading to repudiation, where they can deny performing any action.
2. Briefly explain why the vulnerability is addressed in **secure.ts**.
   ANSWER -
   It is addressed by introducing a middleware that logs every incoming request along with the user's actions. This ensures accountability, as all actions are recorded with the user's identity and the timestamps, making it harder for users to deny their actions.
3. Which design pattern is used in the secure version to address the vulnerability? Briefly explain how it works?
   ANSWER -
   Factory pattern
