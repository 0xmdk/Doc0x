## Get WildCard Cert from Let's Encrypt

```bash
certbot certonly --manual \
  --preferred-challenges=dns \
  --email marcin@hotmail.com \
  --server https://acme-v02.api.letsencrypt.org/directory \
  --agree-tos \
  --manual-public-ip-logging-ok \
  -d “*.domain.com”
```

## Convert to PFX

```bash
openssl pkcs12 -inkey bob_key.pem -in bob_cert.cert -export -out bob_pfx.pfx
```

## For updating CGI Wildcard

- Log into Web-ADM Proxy at AWS
- switch to root
- enter:

```bash
certbot certonly --manual --preferred-challenges=dns --email tsobers@creativegroupinc.com --server https://acme-v02.api.letsencrypt.org/directory --agree-tos --manual-public-ip-logging-ok -d "*.creativegroupinc.com"
```

- Log into Go Daddy and find the following TXT record: "acme-challenge.creativegroupinc.com"
- update the value from the certbot value returned in certbot; save and close
- Verify Record was updated at: "https://toolbox.googleapps.com/apps/dig/#TXT/_acme-challenge.creativegroupinc.com"
- New certs are now in. "/etc/letsencrypt/live/creativegroupinc.com" on AWS Proxy Server
- Copy this cert to bitwarden, waproxy & ovpn servers.