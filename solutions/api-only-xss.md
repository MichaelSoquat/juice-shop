# Table of contents

- [Challenge](#challenge)
- [Tools](#tools)
- [Resources](#resources)
- [Solution](#solution)
- [Video](#video)

# Challenge: 

Name: API-only XSS

Description: Persistent `<iframe src="javascript:alert('xss')">` by using the API

Difficulty: 3 star

Category: XSS

The videos and solution descriptions in the OWASP Juice Shop are for educational purposes only.

# Tools:

Burpsuite

# Resources:

None.

# Solution:

1. Go to the products, choose one of them and open it
2. Open the intercepter in burpsuite
3. Write a review and submit it to get the API Call with the Bearer Token
4. Copy the request and paste it into the burpsuite repeater
5. Change the url to `api/products`
6. If we send a get request to that endpoint we get all products with the description
7. We want to change the first product so we need this endpoint:
   
   ```
   api/products/1
   ```
   
8. You can verify the endpoint doing another Get-Request to that endpoint. You only get the information for the first product
9. With `OPTIONS` in front of your url and clicking on "Send" you can get the information of which options the endpoint is accepting (We need the `PUT` Option)
10. We change `OPTIONS` with `PUT`
11. Copy the json from the Get-Request and paste it into your Put-Request. We only need the `description` key with that value:
    
    ```
    "<iframe src=\"javascript:alert('xss')\">"
    ```

    It is important to add the back slashes. If you dont do it the iframe cannot be read completely because the quotes cannot be realized.
12. Add this to the header:
    
    ```
    Content-type: application/json
    ```
    
13. If you send the request now the XSS is persistent

# Video: 

https://www.loom.com/share/f0a2ef1c65474d88bf2dd0e8cf229d23?sid=b72eabcf-3e63-484e-9796-82c177bb392e
