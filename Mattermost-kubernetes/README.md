# Mattermost

## Chapter structure

- 1.Diagram
- 2.mattermost construcyion
  - 2-1.Construction of NFS Server (NFS server side)
  - 2-2.Prepare of NFS client (Or later kubernetes sdie)
  - 2-3.Prepare for DB
  - 2-4.Deploy of APP

## 1.Diagram

| 項目 | 詳細 |
| :--: | :--: |
| OS | CentOS 7 |
| mattermost | v5.16.4 |
| docker | v19.03.5 |
| kubernetes | v1.17.0 |
| postgreSQL | v11 |
| NFS | v4 |

## 2.mattermost construcyion

Mattermost construction with kubernetes.

### 2-1.Construction of NFS Server (NFS server side)

Installing neccessary packages of nfs.

Editing now...

## Reference material

1. [Installing Mattermost on Kubernetes — Mattermost 5.17 ...](https://docs.mattermost.com/install/install-kubernetes.html)
2. [mattermost/mattermost-server: Open source Slack ... - GitHub](https://github.com/mattermost/mattermost-server)
3. [mattermost-docker/contrib/kubernetes at master ... - GitHub](https://github.com/mattermost/mattermost-docker/tree/master/contrib/kubernetes)
4. [Kubernetes上にmattermostを構築する - Qiita](https://qiita.com/iguchikoma/items/d8d22a43bd0716ea1676)
5. [mattermost/mattermost-operator: Mattermost Operator ... - GitHub](https://github.com/mattermost/mattermost-operator)
6. [mattermost/mattermost-docker: Dockerfile for ... - GitHub](https://github.com/mattermost/mattermost-docker)
7. [plugins permission issue · Issue #120 · mattermost/mattermost ...](https://github.com/mattermost/mattermost-helm/issues/120)
8. [How to Add Block Storage Volumes to Kubernetes Clusters ...](https://www.digitalocean.com/docs/kubernetes/how-to/add-volumes/)
9. [Initコンテナ(Init Containers) - Kubernetes](https://kubernetes.io/ja/docs/concepts/workloads/pods/init-containers/)
