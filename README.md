# Cadmus Inquisition Graffiti API

Quick Docker image build:

```bash
docker build . -t vedph2020/cadmus_ingra_api:1.1.0 -t vedph2020/cadmus_ingra_api:latest
docker push vedph2020/cadmus_ingra_api:1.1.0
```

(replace with the current version).

This is a Cadmus API layer customized for the Ingra project. Most of its code is derived from shared Cadmus libraries.

## History

- 2021-12-22: updated packages.

- 2021-10-17: updated to include refactored `DocReferencesPart` from bricks. This is a breaking change for the model of this part, see <https://github.com/vedph/cadmus_ingra> for more.

- 2021-10-17: breaking change for auth database by AspNetCore.Identity.Mongo 8.3.1 (used since Cadmus.Api.Controllers 1.3.0, Cadmus.Api.Services 1.2.0):

```js
/*
Removed fields:
AuthenticatorKey = null
RecoveryCodes = []
*/
db.Users.updateMany({}, { $unset: {"AuthenticatorKey": 1, "RecoveryCodes": 1} });
```
