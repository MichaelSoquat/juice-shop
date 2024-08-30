# Challenge: 

Name: Captcha bypass

Description: Submit at least 10 customer feedbacks within 20 seconds

Difficulty: 3 star

Category: Broken Anti Automation

## Tools used:

Burpsuite

## Resources used:

None.

# Solution:

1. We first need to understand the logic behind the captcha
2. We go to the customer feedback and fill out the form with a random feedback
3. Then start the burpsuite and start the intercepter
4. Submit the form
5. We see that there are 2 keys in the body of our request that are important
   `captchaId` It looks like the captchas are hard coded and depended on the id always the same question
   `captcha` It´s the answer we entered into the input form field. So the answer should always be correct if the id doesnt change.
6. So we can simply copy this request and add it to the repeater
7. Now you can manually trigger this request 10 times in 20 seconds and solve this challenge
   
# Link to my video: 

https://www.loom.com/share/f6d1af8db61b43f991b28091dc29e959?sid=1d6025d7-a546-47f6-92c4-46a0b22abbf2

