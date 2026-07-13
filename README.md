# wirefit-contracts

The [wirefit](https://github.com/Wirefit/wirefit) contracts repo for the demo landscape:
services publish their extracted IR here on merge to main (`wirefit publish`), PR checks
read it (`wirefit check`), and deployments are recorded per environment
(`wirefit record-deploy`). No broker, no database — just this git repo.

Layout (written by wirefit, don't edit by hand):

```
contracts/<service>/manifest.yaml
contracts/<service>/provides/<interaction-id>.ir.json
contracts/<service>/consumes/<provider>/<interaction-id>.ir.json
_envs/    # per-environment deploy records
_blobs/   # content-addressed IR blobs
```

**Deployed compatibility matrix:** <https://tieulongho.github.io/wirefit-contracts/>
(re-rendered by the [matrix pages workflow](.github/workflows/pages.yml) on every push to main)
