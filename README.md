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

**Directive**
|Directive|example|description|
|---|---|---|
|default-src|'self' cdn.example.com|Serves as a fallback for the other fetch directives.|
|script-src|'self' js.example.com|Specifies valid sources for JavaScript and WebAssembly resources.|
|style-src|	'self' css.example.com||
|img-src|'self' img.example.com||
|connect-src|'self'||
|font-src|font.example.com||
|object-src|'self'||
|media-src|media.example.com||
