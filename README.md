# How I Hacked my university’s Lab Portal and gained access to all accounts :)

## A tale of IDOR leads to account takeover!!!

I want to share with you how I hacked my college’s website on the first day of 2023.

### website: redacted.univ.edu.in

## what is IDOR?

This is a type of access control vulnerability that arises when an application uses user-supplied input to access objects directly without any filters.

## What is an account takeover vulnerability?

This vulnerability allows the attacker to gain unauthorized and full access to the victim’s account by exploiting the authentication flaw in the application.

Now, let’s look at the bugs.

To help understand better, having IDOR vulnerability means there is a chance of horizontal privilege escalation. Which can help tamper with sensitive information across users.

The website has a login page that contains USERNAME and PASSWORD fields.

![image](https://user-images.githubusercontent.com/84071887/211071267-d5a614fd-af35-4f47-b721-c6c314079ae2.png)

When I tried to log in using my credentials it redirects me to the dashboard page.

Where I can see My account info, Settings, log out, and other pieces of stuff.

Then I opened the settings page, It has my username, Reg num, gender, Dept, mail id, and mobile number.

And also there is one option to change the password…..

![image](https://user-images.githubusercontent.com/84071887/211071343-67612456-0a5b-4ed7-bc79-74c6565668aa.png)

## Why can't we try IDOR here?

Suddenly opened Burpsuite and intercepted the password change request.

### The request :

![image](https://user-images.githubusercontent.com/84071887/211071483-dae5375c-7203-4e7b-830d-90ed749069f0.png)

In the header, there is an Authorization Bearer token. It is authorizing the user. (BUT NOT in password change)

## Decoded the JWT Token :

![image](https://user-images.githubusercontent.com/84071887/211071545-d04758a2-fcad-4a5e-8cae-6e223ff6bac1.png)


I changed the values of the data(JWT) and sent the request. Surprisingly

NO ERROR. Successfully changing the password.

The server is checking only if the JWT is present or not but it is not validating it.

## The response :

![image](https://user-images.githubusercontent.com/84071887/211071667-e139131f-c668-4b1b-aabb-9d518c0ff440.png)

Then I checked each and every parameter in the request. And removed the unwanted parameters.

![image](https://user-images.githubusercontent.com/84071887/211071722-d3c77f05-e4ed-444b-a0fb-99d3d0accb24.png)


we need only a username, password, and key for the request.

Key — Here key value is “john” for every request.

## Exploitation Starts Here :
I entered some other username(friends account)and checked the response was success 200 OK.

And the password is changed for that account.

# Account takeover was done successfully !!!

![image](https://user-images.githubusercontent.com/84071887/211071809-034fcd6e-d13b-48ec-9abc-2f4fc0b6b53d.png)


#### Regards,

##### SHARAN K

## HAPPY HACKING ##
