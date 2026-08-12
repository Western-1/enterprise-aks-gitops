# GitOps-репозиторій — Enterprise AKS Platform

Цей репозиторій — **єдине джерело істини** для всього, що працює всередині
Kubernetes-кластера. Argo CD стежить за ним і приводить кластер у відповідність.
Нічого не застосовується вручну — тільки Argo CD.

## Структура

```
clusters/
└── dev/                 конфіг рівня кластера для dev-середовища
infrastructure/
└── argocd/              app-of-apps: Argo CD читає цю папку і створює кожен застосунок
apps/                    маніфести застосунків (media-api, worker, redis…)
```

## Як це працює

```
git push  →  Argo CD читає репо  →  порівнює з кластером  →  синхронізує
```

Якщо хтось змінив кластер руками — Argo CD поверне як було. Якщо змінити репо —
Argo CD застосує. Git — це істина.

## Репозиторії

| Репо | Роль |
|---|---|
| [enterprise-aks-platform](https://github.com/Western-1/enterprise-aks-platform) | Інфраструктура як код (Terraform) + документація |
| цей репо | Усе всередині кластера (GitOps) |

[English version](README.md)