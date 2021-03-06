<!-- TITLE: Webappchecklist -->
<!-- SUBTITLE: A quick summary of Webappchecklist -->

# Things to Examine

## Server Side technology
* What web server
* What client stuff?
* Application?
* Database?
* WAF / IPS / IDS?
* Third party components?

## Cookies
* Anything sensitive in the cookie
* Scoping
* HTTPOnly
* Secure

## Login Sequence
* Are cookies changed upon login?  (Session fixation)
* Result a 200 or 302?  (Someday we need to check this)
* Autocomplete?
* Username Enumeration
* Remember Me Functionality

## Forgot Password Sequence
* Username Enumeration
* Email password
* predictable reset link?
* Lame Security questions
* Credential Storage (if it sends you plaintext password)

## Passwords
* Complexity
* History
* Minimum Age
* Change password sequence
	* Old password required?
* Predictable initial password (hard to test for, but maybe)

## SSO
* Don't know much to test here but should be.
* Flesh me out

## Session Information
* How are sessions managed?
* Which cookies are critical?
* Logout Function?
	* Does the logout function work?
* How long are sessions maintained?
* User impersonation functions?

## URLS
* Sensitive information in URL

## Vertical Privilege Escalation

## Horizontal Privilege Escalation

## IDOR

## Rich Components
* Flash
* Java

## Ajax / API Testing

## SSL Usage
* Is port 80 available?
	* What works on port 80?
* HSTS
* SSL Scan
* 

## Sensitive information on page without cause
* Click to see sensitive information so it's only onscreen when needed.

## XSS

## SQL Injection

## XML Handling

## SSRF

## CSRF

## Request Smuggling

## File Upload Functionality

## Directory Traversal Attacks

## Object Serialization

## Workflow Bypasses

## HTTP Headers

