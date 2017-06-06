# Time Based One Time HTTP Basic Authentication

## Example

Generate user and pass secret keys.

```
make-totp-secret > /var/tmp/user.secret
make-totp-secret > /var/tmp/pass.secret
```

Print QR code in terminal.

```
cat /var/tmp/user.secret | qr
cat /var/tmp/pass.secret | qr
```

Generate htpasswd file.

```
make-totp-htpasswd /var/tmp/user.secret /var/tmp/pass.secret /var/tmp/htpasswd
```

Cron job to re-generate htpasswd file every minute.

```
*/1 * * * * www-data make-totp-htpasswd /var/tmp/user.secret /var/tmp/pass.secret /var/tmp/htpasswd
```
