# Cadmus Inquisition Graffiti API

Quick Docker image build:

```bash
docker build . -t vedph2020/cadmus_ingra_api:2.0.3 -t vedph2020/cadmus_ingra_api:latest
docker push vedph2020/cadmus_ingra_api:2.0.3
```

(replace with the current version).

This is a Cadmus API layer customized for the Ingra project. Most of its code is derived from shared Cadmus libraries.

## History

- 2022-11-28: updated packages.
- 2022-11-10: upgraded to NET 7.

### 2.0.3

- 2022-10-10: updated packages and injection in `Startup.cs` for new `IRepositoryProvider`.
- 2022-10-05:
  - preview infrastructure.
  - updated packages (with fixes for legacy parts dependency).

### 2.0.2

- 2022-09-29: optional HTTPS.

### 2.0.1

- 2022-09-27: updated packages and added preview infrastructure.
- 2022-07-30: updated packages including updated Cadmus INGRA core.

### 1.1.0

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
