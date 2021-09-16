# Clickjacking

## Information

Clickjacking  is a technique of tricking a Web user into clicking on something different.

## Observation

If server didn't return an **X-Frame-Options** header which means that this website could be at risk of a clickjacking attack.

## POC-Code
```javascript
<html>
   <head>
     <title>Clickjack POC</title>
   </head>
   <body>
     <iframe src="https://websiteurl.com" width="1000" height="500"></iframe>
   </body>
</html>
```

## Remediation

1. The server-side header **X-Frame-Options** can permit or forbid displaying the page inside a frame.

> `X-Frame-Options: DENY` (Never ever show the page inside a frame)

> `X-Frame-Options: SAMEORIGIN` (Allow inside a frame if the parent document comes from the same origin)

> `X-FRAME-Options: ALLOW-FROM https://weisiteurl.com` (Allow inside a frame if the parent document is from the given domain)

2. **Content-Security-Policy** response header allows web site administrators to control resources the user agent is allowed to load for a given page. With a few exceptions, policies. for clickjacking protection is to incorporate the `frame-ancestors` Navigation directives(it is govern to which locations a user can navigate or submit a form) in the application's CSP.

> `Content-Security-Policy: frame-ancestors 'none'` -> is similar to the X-Frame-Options: DENY

> `Content-Security-Policy: frame-ancestors 'self'` -> is similar to the X-Frame-Options: SAMEORIGIN

> `Content-Security-Policy: frame-ancestors https://weisiteurl.com'` -> is similar to the X-Frame-Options: ALLOW-FROM https://weisiteurl.com

## Refrence

- https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/X-Frame-Options
- https://portswigger.net/web-security/clickjacking
