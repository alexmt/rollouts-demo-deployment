# Canary deployment using Argo Rollouts

Repository demonstrates implementation of Canary deployment using Argo Rollouts

![demo](./demo.png)

Steps:

1. Create the Argo CD application using deployment repo https://github.com/alexmt/rollouts-demo-deployment: 

```
argocd app create rollouts-demo --repo https://github.com/alexmt/rollouts-demo-deployment --path . --dest-server https://kubernetes.default.svc --dest-namespace rollouts-demo --sync-policy automated
```

2. Make sure application is running by visiting http://rollouts-demo.apps.argoproj.io/.

3. Change image tag in `kustomization.yaml`. Available tags are `red`, `green`, `blue`, `yellow` and synchronize the change using Argo CD.

4. Verify that application is serving canary traffic and promote canary deployment.
