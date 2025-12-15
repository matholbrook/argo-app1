# argo-app1

argocd testing

## Create Argo App using CLI

```bash
argocd app create argo-app1 \
--project default \
--repo https://github.com/matholbrook/argo-app1.git \
--path "./web-apache-app1" \
--dest-server https://kubernetes.default.svc
```

## Sync App

```bash
$ argocd app sync argo-app1
TIMESTAMP                  GROUP        KIND   NAMESPACE                   NAME    STATUS    HEALTH        HOOK  MESSAGE
2025-12-15T15:18:54+00:00            Service  app-foo-prd         crazy-caracal  OutOfSync  Missing              
2025-12-15T15:18:54+00:00   apps  Deployment  app-foo-prd         crazy-caracal  OutOfSync  Missing              
2025-12-15T15:18:55+00:00            Service  app-foo-prd         crazy-caracal  OutOfSync  Healthy              
2025-12-15T15:18:55+00:00            Service  app-foo-prd         crazy-caracal    Synced  Healthy              
2025-12-15T15:18:55+00:00            Service  app-foo-prd         crazy-caracal    Synced   Healthy              service/crazy-caracal created
2025-12-15T15:18:55+00:00   apps  Deployment  app-foo-prd         crazy-caracal  OutOfSync  Missing              deployment.apps/crazy-caracal created

Name:               argocd/argo-app1
Project:            default
Server:             https://kubernetes.default.svc
Namespace:          
URL:                https://argocd.example.com/applications/argo-app1
Source:
- Repo:             https://github.com/matholbrook/argo-app1.git
  Target:           
  Path:             ./web-apache-app1
SyncWindow:         Sync Allowed
Sync Policy:        Manual
Sync Status:        Synced to  (51037eb)
Health Status:      Progressing

Operation:          Sync
Sync Revision:      51037eb909c42893beb2a1e40ad516df046d2786
Phase:              Succeeded
Start:              2025-12-15 15:18:55 +0000 GMT
Finished:           2025-12-15 15:18:55 +0000 GMT
Duration:           0s
Message:            successfully synced (all tasks run)

GROUP  KIND        NAMESPACE    NAME           STATUS  HEALTH       HOOK  MESSAGE
       Service     app-foo-prd  crazy-caracal  Synced  Healthy            service/crazy-caracal created
apps   Deployment  app-foo-prd  crazy-caracal  Synced  Progressing        deployment.apps/crazy-caracal created
```