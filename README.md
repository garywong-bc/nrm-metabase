## Local


```bash
UID="$(id -u)" GID="$(id -g)" docker-compose up
```

rm -rf postgresql/data/*

## OpenShift

oc -n 245e18-tools create secret docker-registry docker-pull-passthru \
    --docker-server=docker-remote.artifacts.developer.gov.bc.ca \
    --docker-username=default-245e18-xxxxxx \
    --docker-password=xxxxxx \
    --docker-email=default-245e18-ujotfv@245e18-tools.local




oc -n 245e18-tools secrets link default docker-pull-passthru
oc -n 245e18-tools secrets link builder docker-pull-passthru

==



```bash

~/p/lucy-web ❯❯❯ export NAMESPACE=245e18-tools                                                                                  feature/self-contained-metabase-postgresql ✱ ◼
~/p/lucy-web ❯❯❯ export METABASE_VERSION=v0.39.4                                                                                feature/self-contained-metabase-postgresql ✱ ◼
~/p/lucy-web ❯❯❯ oc process -n $NAMESPACE -f ./api/openshift/tools/metabase/metabase.bc.yaml -p METABASE_VERSION=$METABASE_VERSION -o yaml | oc apply -n $NAMESPACE -f -
imagestream.image.openshift.io/metabase unchanged
buildconfig.build.openshift.io/metabase configured

```

    


