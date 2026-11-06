


# kargo-demo
a demo, for kargo


# Goals

Demonstrate simple configuration of Kargo and promotions through 3 Stages.

* Generate images from this repo, to public ghcr packages, built by Github actions on commit/update, update accoring to semVer i.e. 1.0.0 -> 1.0.1 etc 
* Create argocd app, and have 3 varieties of the app, integrate kustomize later (overlays?)
* Each app refers to a particular image version of the fastapi-app image 
* stages and promotions etc from there , multi track drifting


# Apply the 3 apps

The Application manifests in `kargo-fastapi/` deliberately leave out the destination cluster, so you can choose it when you deploy. Argo CD rejects an Application with no destination cluster, so pass one with `--dest-server` or `--dest-name`.

Find the clusters registered with your Argo CD instance:

```
argocd cluster list
```

Deploy to a cluster by its API server URL:

```
DEST_SERVER=https://<cluster-api-server>   # e.g. http://cluster-kargo-demo:8001

argocd app create -f kargo-fastapi/kargo-fastapi-app-dev.yaml   --dest-server "$DEST_SERVER"
argocd app create -f kargo-fastapi/kargo-fastapi-app-stage.yaml --dest-server "$DEST_SERVER"
argocd app create -f kargo-fastapi/kargo-fastapi-app-prod.yaml  --dest-server "$DEST_SERVER"
```

Or deploy to a cluster by the name Argo CD knows it by:

```
DEST_NAME=<cluster-name>

argocd app create -f kargo-fastapi/kargo-fastapi-app-dev.yaml   --dest-name "$DEST_NAME"
argocd app create -f kargo-fastapi/kargo-fastapi-app-stage.yaml --dest-name "$DEST_NAME"
argocd app create -f kargo-fastapi/kargo-fastapi-app-prod.yaml  --dest-name "$DEST_NAME"
```

Each environment can go to a different cluster: set a different value on each command.


##

sleep chart requires

