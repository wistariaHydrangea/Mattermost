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

```
# yum -y install nfs-utils
```

Edit /etc/exports.
(/etc/exports)

```
/mnt/mattermost 172.16.10.0/24(rw,async,no_root_squash)
```

Release service of firewall.

```
# firewall-cmd --add-service=nfs <--nfs4の場合
# firewall-cmd --runtime-to-permanent
# firewall-cmd --reload
```

rancher of nfs server

```
# systemctl enable rpcbind nfs-server
# systemctl start rpcbind nfs-server
```

### 2-2.Prepare of NFS client (kubernetes sdie)

Installing to client side neccessary packages of nfs.

```terminal
# yum -y install nfs-utils
# mkdir -p /mnt/mattermost/postgres
```

Grant permissions to the directory.

```terminal
# chmod 777 /mnt/mattermost
```

Mount to client side.

```teminal
# mount -t nfs (nfs server 'IP address' or 'hostname'):/mnt/matetrmost /mnt/mattermost
```

Edit /etc/fstab.
(/etc/fstab)

```
/dev/mapper/centos-root /                       xfs     defaults        1 1
UUID=a18716b4-cd67-4aec-af91-51be7bce2a0b /boot xfs     defaults        1 2
# /dev/mapper/centos-swap swap                    swap    defaults        0 0

(nfs server 'IP address' of 'hostname'):/mnt/mattermost  /mnt/mattermost                   nfs     defaults        0 0
```


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
