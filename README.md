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

The matrix guard calls the reusable `Wirefit/wirefit/actions/matrix` action
from `master`, which includes the extractor cache changes. The
[matrix guard](.github/workflows/matrix.yml) validates
published manifests and checks deployed compatibility on branch pushes, pull
requests, daily runs, and manual runs. Its `compatibility-matrix` artifact contains
Markdown, JSON, and HTML reports. Compatibility warnings pass; incompatible edges
fail the check.

The [Pages workflow](.github/workflows/pages.yml) uses pinned revision
`a13ee3532102515a4dd6ed36b3bdef86f97f26aa`
and publishes on pushes to `main`, daily runs, and manual runs. It also publishes
reports containing incompatible edges so the dashboard remains available.
The matrix action and its CLI version both track `master`.
To upgrade Pages, update its source ref, action ref,
and `version` together.
