# sentry-shared-postgres

The shared PostgreSQL instance that [devservices](https://github.com/getsentry/devservices) runs for Sentry developer environments.

## Use it from your service

Add `postgres` as a remote dependency in your service's `devservices/config.yml`:

```yaml
x-sentry-service-config:
  dependencies:
    postgres:
      description: Shared instance of postgres used by sentry services
      remote:
        repo_name: sentry-shared-postgres
        branch: main
        repo_link: https://github.com/getsentry/sentry-shared-postgres.git
```

`devservices up` in your service then starts this instance.

## Connect

| Setting  | Value               |
| -------- | ------------------- |
| Host     | `127.0.0.1`         |
| Port     | `5432`              |
| User     | `postgres`          |
| Password | none (`trust` auth) |
| Database | `sentry`            |

The server runs PostgreSQL 14 (`ghcr.io/getsentry/image-mirror-library-postgres:14-alpine`) with `wal_level=logical`, one replication slot, and one WAL sender. Data persists in the `postgres-data` Docker volume.

[`devservices/config.yml`](devservices/config.yml) is the source for these settings.
