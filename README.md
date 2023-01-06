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

![alt text](![image](https://user-images.githubusercontent.com/84071887/211070619-fecccffe-386e-4ab8-8750-107a763f1f98.png) "Login page")
