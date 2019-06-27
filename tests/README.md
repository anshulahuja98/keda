## Prerequisits

- [node](https://nodejs.org/en/)
- `kubectl` logged into a Kubernetes cluster.
- Each scaler test might define additional requirements. For example, `azure-queue.test.ts` requires an env var `TEST_STORAGE_CONNECTION_STRING`

## Running tests:

```bash
npm install
npm test --verbose
```

## E2E test setup

- `setup.test.ts` deploys `/deploy/KedaScaleController.yaml` to `keda` namespace in the cluster, and updates the image to `kedacore/keda:master`
- `cleanup.test.ts` deletes keda and all its components from the cluster.
- each `scalers/*.test.ts` runs in parallel using [ava](https://github.com/avajs/ava) framework.

See `azure-queue.test.ts` for a test example.