# Kasten Bulk Restore

This repository contains the script to perform a bulk restore of namespaces using Kasten K10. 

## Pre-requisites

* The environment running the script can execute kubectl commands.
* The environment running the script is connected to the target cluster where namespaces are to be restored. Run `kubectl config current-context` to verify.
* RestorePoint/RestorePointContent exists for the namespaces being restored on the target cluster.

Note: If the RestorePoint/RestorePointContent doesn't exist on the target cluster, the script will issue a warning and skip the namespace from the restore.

## Usage

```
./k10-bulk-restore.sh -n <namespaces_to_restore> [-s storageclass] [-t timeout]
```

Parameters:

-n (Required) Specifies the namespaces to be restored. Multiple namespaces can be provided separated by comma.

-s (Optional) Specifies the name of the storageclass to be used for restore.

-t (Optional) Specifies the timeout value in seconds. The script will check for status of restored namespaces until this timeout is reached. If not specified, the timeout will default to 1 Hr.

