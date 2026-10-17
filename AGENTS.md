# AGENTS.md

devservices config for the shared PostgreSQL container used by Sentry developer environments. The only service definition is [`devservices/config.yml`](devservices/config.yml).

- Check a config change: `pip install -r requirements-dev.txt`, then `devservices up`, `devservices status`, and `devservices down`. CI ([`.github/workflows/ci.yml`](.github/workflows/ci.yml)) runs these through `getsentry/action-validate-devservices-config` when `devservices/`, the workflow, or `requirements-dev.txt` changes.
- Other repos depend on this one by name and on branch `main`. Renaming the service or changing the port, user, or database breaks them.
- Usage and connection settings: [README.md](README.md).
