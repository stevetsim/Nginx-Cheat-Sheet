# Nginx Cheat Sheet

## 1. Security
### CSP (Content Security Policy)
The HTTP Content-Security-Policy response header gives website administrators the ability to manage resources that the user's browser is permitted to load for a specific page. Generally, policies involve identifying server origins and script endpoints, with a few exceptions. This is useful for protecting against cross-site scripting attacks.

**default.conf**
```
server {
  # Security Headers
  add_header Content-Security-Policy ...
}
```

**Directive**
| Directive    | Example                  | Description                                                                                  |
| ------------ | ------------------------ | -------------------------------------------------------------------------------------------- |
| child-src    | 'self'                   | Defines the valid sources for web workers and nested browsing contexts loaded using elements |
| default-src  | 'self' cdn.example.com   | Serves as a fallback for the other fetch directives.                                         |
| script-src   | 'self' js.example.com    | Specifies valid sources for JavaScript and WebAssembly resources.                            |
| style-src    | 'self' css.example.com   | Specifies valid sources for stylesheets.                                                     |
| img-src      | 'self' img.example.com   | Specifies valid sources of images and favicons.                                              |
| connect-src  | 'self'                   | Restricts the URLs which can be loaded using script interfaces.                              |
| font-src     | font.example.com         | Specifies valid sources for fonts loaded                                                     |
| object-src   | 'self'                   | Specifies valid sources for the <object>, <embed>, and <applet> elements.                    |
| media-src    | media.example.com        | Specifies valid sources for loading media                                                    |
| frame-src    | 'self' frame.example.com | Specifies valid sources for nested browsing contexts loading using elements                  |
| manifest-src | 'self'                   | Specifies valid sources of application manifest files.                                       |

**Source Value**
| Source Value  | Example                    | Description                          |
| ------------- | -------------------------- | ------------------------------------ |
| *             | img-src *                  | Allowing All                         |
| none          | object-src 'none'          | Block all resource of this directive |
| self          | script-src 'self'          | Allowing the same origin             |
| data          | img-src 'self' data:       | Allowing data type base64 images     |
| example.com   | img-src example.com        | Allowing specific domain             |
| *.example.com | img-src *.example.com      |                                      |
| unsafe-inline | script-src 'unsafe-inline' |                                      |
| unsafe-eval   | script-src 'unsafe-eval'   |                                      |

### Useful Site for Testing CSP
[CSP Evaluator](https://csp-evaluator.withgoogle.com/)