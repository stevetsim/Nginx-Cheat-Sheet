# Nginx Cheat Sheet

## 1. Security
### CSP (Content Security Policy)
The HTTP Content-Security-Policy response header gives website administrators the ability to manage resources that the user's browser is permitted to load for a specific page. Generally, policies involve identifying server origins and script endpoints, with a few exceptions. This is useful for protecting against cross-site scripting attacks.

```
server {
  # Security Headers
  add_header Content-Security-Policy ...
}
```
