# Clickjacking

## Information

Clickjacking  is a technique of tricking a Web user into clicking on something different.

## Observation

If server didn't return an X-Frame-Options header which means that this website could be at risk of a clickjacking attack.

## POC-Code
```javascript
<html>
   <head>
     <title>Clickjack POC</title>
   </head>
   <body>
     <p>Website is vulnerable to clickjacking!</p>
     <iframe src="https://websiteurl.com" width="1000" height="500"></iframe>
   </body>
</html>
```

## Remediation

The server-side header **X-Frame-Options** can permit or forbid displaying the page inside a frame.

> `X-Frame-Options: DENY` (Never ever show the page inside a frame)

> `X-Frame-Options: SAMEORIGIN` (Allow inside a frame if the parent document comes from the same origin)

> `X-FRAME-Options: ALLOW-FROM https://weisiteurl.com` (Allow inside a frame if the parent document is from the given domain)


## Refrence

- https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/X-Frame-Options
