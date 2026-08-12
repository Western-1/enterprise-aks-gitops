# GitOps repository — Enterprise AKS Platform

This repository is the **single source of truth** for everything running inside the
Kubernetes cluster. Argo CD watches it and makes the cluster match this repo.
Nothing is applied to the cluster by hand — only Argo CD does it.

## Layout

```
clusters/
└── dev/                 cluster-level config for the dev environment
infrastructure/
└── argocd/              app-of-apps: Argo CD reads this folder and creates every app
apps/                    application manifests (media-api, worker, redis…)
```

## How it works

```
git push  →  Argo CD polls the repo  →  compares with the cluster  →  syncs
```

If someone changes the cluster by hand, Argo CD reverts it. If you change the
repo, Argo CD applies it. Git is the truth.

## Repos

| Repo | Role |
|---|---|
| [enterprise-aks-platform](https://github.com/Western-1/enterprise-aks-platform) | Infrastructure as Code (Terraform) + docs |
| this repo | Everything inside the cluster (GitOps) |

[Українська версія](README.ua.md)