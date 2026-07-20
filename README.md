


# kargo-demo
a demo, for kargo


# Goals

Demonstrate simple configuration of Kargo and promotions through 3 Stages.

* Generate images from this repo, to public ghcr packages, built by Github actions on commit/update, update accoring to semVer i.e. 1.0.0 -> 1.0.1 etc 
* Create argocd app, and have 3 varieties of the app, integrate kustomize later (overlays?)
* Each app refers to a particular image version of the fastapi-app image 
* stages and promotions etc from there , multi track drifting


# Apply the 3 apps

'''
argocd app create -f kargo-fastapi-app-dev.yaml
argocd app create -f kargo-fastapi-app-stage.yaml
argocd app create -f kargo-fastapi-app-prod.yaml
```


##

sleep chart requires

