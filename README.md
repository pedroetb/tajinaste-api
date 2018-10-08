# Tajinaste API

## Variables

### Preset variables


### Secret variables

You must set these variables in your environment before running the service:
* **POSTGRES_PASSWORD**: PostgreSQL database password for user *POSTGRES_USER*.
* **PGRST_JWT_SECRET**: Public key used to verify the JWT sent by users. It must be a single-lined valid JWK.

## Key generation

To generate a public/private key pair in JWK format, use a utility like [latchset/jose](https://github.com/latchset/jose).

Install and use it from shell:

```
apt install jose

jose jwk gen -i '{"alg": "RS256"}' -o rsa.jwk
jose jwk pub -i rsa.jwk -o rsa.jwk.pub

# now rsa.jwk.pub contains the public key, and rsa.jwk the private key
```
