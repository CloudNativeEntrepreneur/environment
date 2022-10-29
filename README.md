# Environment

Resources to create in environments (namespaces)

NOTE: The Secret created here is an example, and doesn't work. You'll need to create a real secret store and put the actual credentials there.

If running locally, you can "log in" per environment manually if you don't have a production secret store.

```
kubectl -n example-prod-env create secret docker-registry ghcr --docker-server=https://ghcr.io --docker-username=<your-github-username> --docker-password=<github_PAT_packages:read> --docker-email=<your-github-email>
kubectl -n example-prod-env patch serviceaccount default -p '{"imagePullSecrets": [{"name": "ghcr"}]}'
```

Because the fake secret doesn't work, and I want to be able to create the real one manually while developing locally, the fake one has the wrong name as well - when setting up your real secret store, change it's name to "ghcr" as well.