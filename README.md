# Kasten Bulk Restore

This repository contains the script to perform a bulk restore of namespaces using Kasten k10.

The script takes namespaces separated by comma as input parameters and checks if k10 RestorePoint or RestorePointContent exists for the namespace in the Target cluster. If it exists, the script performs a RestoreAction. If it doesn't exist, a warning message is issued and the namespace is skipped. The script also reports the status of the RestoreAction based on the provided timeout parameter.


## Pre-requisites

* The environment running the script can execute kubectl commands.
* The environment running the script is connected to the target cluster where namespaces are to be restored. Run `kubectl config current-context` to verify.
* RestorePoint/RestorePointContent exists for the namespaces being restored on the target cluster.


## Usage

```
./k10-bulk-restore.sh -n <namespaces_to_restore> [-s storageclass] [-t timeout]
```

Parameters:

-n (Required) Specifies the namespaces to be restored. Multiple namespaces can be provided separated by comma.

-s (Optional) Specifies the name of the storageclass to be used for restore.

-t (Optional) Specifies the timeout value in seconds. The script will check for status of restored namespaces until this timeout is reached. If not specified, the timeout will default to 1 Hr.

