PortSwigger provides intentionally vulnerable web applications specifically designed for safe and legal cybersecurity training.

I completed **11 beginner-level labs** covering several common web application vulnerability categories.

I first attempted each challenge myself. When I was unable to fully solve or understand a lab, I used PortSwigger's educational resources and additional guidance to understand the solution.

I then reproduced the technique within the authorized training environment and focused on understanding:

- What caused the vulnerability
- Why the technique worked
- What security impact it could have
- How the vulnerability could be prevented

This portion represents **guided cybersecurity learning**, not independent professional penetration testing.

---

## Vulnerabilities Studied

### SQL Injection

The SQL injection exercises demonstrated how insecure database queries can allow user-controlled input to modify SQL logic.

Topics included:

- Authentication bypass
- Hidden data exposure
- Manipulating SQL query conditions

One exercise demonstrated how SQL comment syntax could alter an insecure authentication query.

For example:

```text
administrator'--
```

The apostrophe closes the existing SQL string, while `--` causes the remaining portion of the SQL statement to be treated as a comment.

In an insecure authentication query, this can cause the password comparison to no longer be evaluated.

Another exercise demonstrated the use of:

```text
' OR 1=1--
```

Because:

```text
1=1
```

is always true, the condition can cause a vulnerable query to return records that would normally remain hidden.

These exercises helped me understand why **parameterized queries and prepared statements** are important defenses against SQL injection.

---

### Reflected Cross-Site Scripting

The reflected XSS lab demonstrated how user-controlled input can become executable browser content when an application returns that input without safely encoding it.

I learned that applications should treat untrusted input as data rather than executable content.

---

### Stored Cross-Site Scripting

The stored XSS exercise demonstrated how malicious input can become more dangerous when it is saved by an application and later displayed to other users.

This helped me understand the difference between:

- Reflected XSS
- Stored XSS

---

### DOM-Based Cross-Site Scripting

The DOM-based XSS exercise demonstrated that security vulnerabilities can also originate from client-side JavaScript.

I learned that insecure processing of user-controlled data inside the browser can create vulnerabilities even when the server itself is not directly generating malicious content.

---

### Broken Access Control

The access-control exercises demonstrated why simply hiding administrative functionality is not sufficient security.

Sensitive functionality should always have server-side authorization controls that verify whether a user is actually permitted to access it.

---

### Hidden Administrative Functionality

Another exercise demonstrated the risks of relying on hidden or unlinked administrative pages.

A major takeaway was:

> **A resource being difficult to find does not make it secure.**

Authorization must still be enforced by the application.

---

### Username Enumeration

The username-enumeration exercise demonstrated how differences in authentication responses can unintentionally reveal whether an account exists.

This showed how seemingly small differences in error messages or application behavior can provide useful information to an attacker.

---

### Two-Factor Authentication Bypass

This exercise demonstrated that multi-factor authentication only provides protection when every stage of authentication is correctly enforced.

If application logic allows a required authentication step to be skipped, the additional security control can become ineffective.

---

### File Path Traversal

The path-traversal exercise demonstrated how insecure handling of user-controlled file paths can allow access to files outside the directory intended by an application.

I learned why applications should restrict filesystem access and avoid trusting raw user-supplied paths.

---

### Operating System Command Injection

The command-injection exercise demonstrated the danger of allowing user-controlled input to influence operating system commands.

This introduced me to the importance of:

- Separating user input from executable commands
- Validating inputs
- Using allowlists
- Avoiding unnecessary operating system commands
- Following the principle of least privilege

---

## What I Learned from PortSwigger

The main goal of this portion was not to memorize exploit payloads.

Instead, I focused on understanding the patterns that caused the vulnerabilities.

Several concepts appeared repeatedly:

- User-controlled input should never automatically be trusted.
- Database commands should remain separate from user-controlled data.
- Browser output should safely handle untrusted content.
- Authentication must be enforced on the server.
- Authorization should protect every sensitive resource.
- Hidden functionality is not the same as protected functionality.
- Filesystem access should be restricted.
- Applications should avoid unsafe operating system command execution.

One of the biggest lessons was that understanding **why** a technique works is more useful than simply knowing what input completes a training lab.

---
