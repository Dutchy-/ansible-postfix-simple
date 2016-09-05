# ansible-postfix-simple
An ansible role for postfix with a secure and simple configuration.

## Features

 - Maps all domains with a catch-all to a single system user. Could fairly easily be changed by editing `templates/virtual.j2`.
 - Secure TLS configurations (best effort on smtp and mandatory tls on submission).
 - SPF record checking
 - OpenDKIM pre-configured, needs separate role.
 - Opens ports smtp (25) and submission (587) in ufw.

## Example

```yaml
- role: smtp
  user: dutchy
  hostname: mail.example.org
  certificate_file: /etc/letsencrypt/live/mail.example.org/cert.pem
  certificate_key_file: /etc/letsencrypt/live/mail.example.org/privkey.pem
  domains:
  - example.org
  - example.com
```
