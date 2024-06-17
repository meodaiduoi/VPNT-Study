#Kubernetes #etcdctl
## Ref:
`etcdctl` is a command line client for [**etcd**](https://github.com/coreos/etcd).
[Backup and restore etcd cluster on Kubernetes](https://medium.com/@mehmetodabashi/backup-and-restore-etcd-cluster-on-kubernetes-93c19b1c070)
[How to Backup and Restore ETCD Snapshot on Kubernetes Cluster](https://medium.com/@werkjober/how-to-backup-and-restore-etcd-snapshot-on-kubernetes-cluster-c612ce5b6147)
[etcdctl restore snapshot: always specify --data-dir](https://sukantamaikap.com/posts/2023-12-12---etcd-backup-and-restore/etcd-backup-and-restore)
## Step 1 set ETCDCTL_API version

``` sh
# set version variable of etcd and check
export ETCDCTL_API=3 # export etcdctl version variable
etctd version

# output
╰$ etcdctl version  
etcdctl version: 3.5.14
API version: 3.5
```

## Step 2: get etcd.yaml backup info

``` sh
cat /etc/kubernetes/manifests/etcd.yaml
```

![[Pasted image 20240617161946.png]]
## Step 3: Backup

Since our ETCD database is TLS-Enabled, the following options are mandatory:

| Flag:                          | Description:                                                                             |
| ------------------------------ | ---------------------------------------------------------------------------------------- |
| `--cacert`                     | verify certificates of TLS-enabled secure servers using this CA bundle<br>               |
| `--cert`                       | identify secure client using this TLS certificate file                                   |
| `--endpoints=[127.0.0.1:2379]` | This is the default as ETCD is running on master node and exposed on localhost 2379.<br> |
| `--key`                        | identify secure client using this TLS key file<br>                                       |

**Template:**

```
ETCDCTL_API=3 etcdctl \  
  --endpoints=https://127.0.0.1:2379 \  
  --cacert=<ca-file> \  
  --cert=<cert-file> \  
  --key=<key-file> \  
  snapshot save <backup-file-location>
```

**Example:**

```sh
ETCDCTL_API=3 etcdctl \  
  --endpoints=https://127.0.0.1:2379 \  
  --cacert=/etc/kubernetes/pki/etcd/ca.crt \  
  --cert=/etc/kubernetes/pki/etcd/server.crt \  
  --key=/etc/kubernetes/pki/etcd/server.key \  
  snapshot save /opt/backup/etcd.db
  
# example output
Snapshot saved at /opt/backup/etcd.db
```
## Step 4: Restore

**Example restore:**

``` sh
ETCDCTL_API=3 etcdctl --data-dir="<restore-dir>" \  
--endpoints=https://127.0.0.1:2379 \  
--cacert=/etc/kubernetes/pki/etcd/ca.crt \  
--cert=/etc/kubernetes/pki/etcd/server.crt \  
--key=/etc/kubernetes/pki/etcd/server.key \  
snapshot restore <save-location>/<snapshot-name.db>
```

Here is the **command to restore etcd.**

``` sh
ETCDCTL_API=3 etcdctl snapshot restore <backup-file-location>
```

Let’s execute the etcd restore command. In my case `/opt/backup/etcd.db` is the backup file.

``` sh
ETCDCTL_API=3 etcdctl snapshot restore /opt/backup/etcd.db
```

If you want to use a specific data directory for the restore, you can add the location using the `--data-dir` flag as shown below.

``` sh
ETCDCTL_API=3 etcdctl --data-dir /opt/etcd snapshot restore /opt/backup/etcd.db
```


Similarly use the help option for **snapshot restore** to see all available options for restoring the backup.

``` sh
etcdctl snapshot restore -h
```

For a detailed explanation on how to make use of the `etcdctl` command line tool and work with the -h flags, check out the solution video for the Backup and Restore.

## Note about using `--data-dir`

- Normally, restoring an etcd snapshot involves creating a new directory and specifying it with the `--data-dir` flag in the `etcdctl restore snapshot` command. This ensures the restored data doesn't overwrite any existing data.
    
- However, if you run the command without `--data-dir`, `etcdctl` uses your current working directory by default. This can lead to issues if you try to restore a snapshot again from the same directory.
    
- The article recommends always specifying `--data-dir` to a new directory and updating the etcd manifest to use the new data directory path.
    
- It also highlights that not specifying `--data-dir` can overwrite some etcd cluster data like member ID, causing the restored cluster to lose its former identity.