# Tajinaste API

API REST service for providing PostgreSQL data to [Tajinaste Manager](https://github.com/pedroetb/tajinaste-manager).

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Sponsor](https://img.shields.io/badge/-Sponsor-fafbfc?logo=GitHub%20Sponsors)](https://github.com/sponsors/pedroetb)

## Variables

### Preset variables

These variables already have a default value set, but you can overwrite it in your environment before running the service:

* **POSTGRES_PROTOCOL**: Protocol value used at PostgreSQL URI for database connection (default: `postgres`).
* **POSTGRES_USER**: Username value used at PostgreSQL URI for database connection (default: `postgres`).
* **POSTGRES_HOST**: Hostname value used at PostgreSQL URI for database connection (default: `db`).
* **POSTGRES_PORT**: Port value used at PostgreSQL URI for database connection (default: `5432`).
* **POSTGRES_DB**: Database value used at PostgreSQL URI for database connection (default: `tajinaste`).
* **POSTGRES_PARAMS**: Params value used at PostgreSQL URI for database connection, must start with `?` if specified.
* **PGRST_DB_SCHEMAS**: PostgreSQL database schemas (comma separated) exposed through API REST, where users will consume data (default: `api`).
* **PGRST_DB_ANON_ROLE**: PostgreSQL database role used when API REST receive requests from unauthenticated users (default: `tajinaste_guest`).
* **PGRST_SERVER_PORT**: TCP port to bind API REST and expose through Traefik reverse proxy (default: `3000`).

### Secret variables

You must set these variables in your environment before running the service:

* **POSTGRES_PASSWORD**: Password value used at PostgreSQL URI for database connection with user *POSTGRES_USER* (default: `changeme`).
* **PGRST_JWT_SECRET**: Public key used to decode JWT tokens sent by users. It must be a single-lined valid JWK, at least 32 characters long.

## Key generation

To generate a public/private key pair in JWK format, use a utility like [latchset/jose](https://github.com/latchset/jose).

Install and use it from shell:

```sh
apt install jose

jose jwk gen -i '{"alg": "RS256"}' -o rsa.jwk
jose jwk pub -i rsa.jwk -o rsa.jwk.pub

# now rsa.jwk.pub contains the public key, and rsa.jwk the private key
```

## License

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

This project is released under the [MIT License](LICENSE).
