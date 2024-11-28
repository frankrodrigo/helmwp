
### Generate the manifests:
`helm template -g --output-dir ./ymls . -f stage/values.yaml -f stage/secrets.yaml`

### Install, Uninstall, List
- To install
```
helm install --dry-run wordpress-db -n wpdb . -f dev/values.yaml
helm install wordpress-db -n wpdb . -f dev/values.yaml -f dev/secrets.yaml --create-namespace
helm ls -n wpdb

helm install wordpress-app -n wpapp . -f dev/values.yaml -f dev/secrets.yaml --create-namespace
helm ls -n wpapp
```

- To upgrade
```
helm upgrade wordpress-db -n wpdb . -f dev/values.yaml -f dev/secrets.yaml
```
- To uninstall
```
helm uninstall wordpress-db -n wpdb
helm uninstall wordpress-app -n wpapp

```

### DB Connection issue
- the volume is used for db container is hostpath. if db is configured incorrectly, the miss-configured db files will be stored in the volume. Untill the volume is cleared, you will get db issue

- check the env variables
