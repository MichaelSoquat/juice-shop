# Table of contents

- [Challenge](#challenge)
- [Tools](#tools)
- [Resources](#resources)
- [Solution](#solution)
- [Video](#video)

# Challenge: 

Name: Admin registration

Description: Register as a user with admin privileges

Difficulty: 3 star

Category: Improper input validation

The videos and solution descriptions in the OWASP Juice Shop are for educational purposes only.

# Tools:

Burpsuite, jwt.io

# Resources:

None.

# Solution:

1. We first need to find the location where we see if someone is an admin or a customer
   To verify that start the burpsuite with the intercepter on and do a simple get request.
   What we need is the Bearer token. You can add the Bearer token which is a Json web token to `jwt.io`
   The decoded token tells us that we have the key `role` in it with either `admin` or `customer`
2. So lets try to register a new person and add this key `role` with the value `admin` into the body of the registration post request
3. Fill the form of the registration
4. Open the intercepter in burpsuite
5. Submit the form
6. If you see the post request of the registration add this additionally to the body:

   ```
   role: "admin",
   ```
   
8. Forward the request and you are an admin now

# Video: 

https://www.loom.com/share/2ca2bd47109a4fd0a07bc3bd2db2bded?sid=607e9019-82b1-46c8-8ce2-126c4a4cab1a

