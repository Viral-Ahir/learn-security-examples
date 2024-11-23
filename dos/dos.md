# Denial-of-Service (DoS)

This example demonstrates DoS vulnerabilities and how they can be exploited.

## Steps to reproduce

1. Install all dependencies

   `$ npm install`

2. Ignore if you have already done this once. Insert test data in the MongoDB database. Make sure the mongod is up and running by typing the `mongosh` command in the termainal. If mongod process is up then you will see that the connection was successful. Command to insert test data:

   `$ npx ts-node insert-test-users.ts`

This will create a database in MongoDB called **infodisclosure**. Verify its presence by connecting with mongosh and running the command `show dbs;`.

2. Start the **insecure.ts** server

   `$ npx ts-node insecure.ts`

3. In the browser, pretend to be a hacker and type a malicious request

   ```
       http://localhost:3000/userinfo?id[$ne]=
   ```

4. Do you see the server crashing?

## For you to do

Answer the following:

1. Briefly explain the potential vulnerabilities in **insecure.ts** that can lead to a DoS attack.
   ANSWER -
   The DoS vulnerability comes from missing error handling when querying the database. If an error occurs, the server can crash, making it unavailable to users.
2. Briefly explain how a malicious attacker can exploit them.
   ANSWER -
   An attacker can exploit this by sending many bad requests to cause the server to crash or slow down, resulting in a DoS attack.
3. Briefly explain the defensive techniques used in **secure.ts** to prevent the DoS vulnerability?
   ANSWER -
   Rate limiting is used to block excessive requests from one IP, which helps prevent DoS attacks. It also sanitizes inputs to avoid errors, keeping the server running smoothly even under attack.
