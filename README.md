# Kasten Bulk Restore

This repository contains the script to perform a bulk restore of namespaces using Kasten k10.

The script takes namespaces (separated by comma) as input parameters and checks if k10 RestorePoint/RestorePointContent exists for the namespace in the Target cluster. 

If exists, the script performs a RestoreAction. If it doesn't exist, a warning message is issued and the namespace is skipped. Optional storage class parameter can be specified to apply a transform operation during restore. 


## Pre-requisites

* The environment running the script can execute kubectl commands.
* The environment running the script is connected to the target cluster where namespaces are to be restored. Run `kubectl config current-context` to verify.
* The user has permissions to create new namespaces on the target cluster. 
* RestorePoint/RestorePointContent exists for the namespaces being restored on the target cluster.


## Usage

```
./k10-bulk-restore.sh -n <namespaces_to_restore> [-s storageclass] [-t timeout]
```

Parameters:

-n (Required) Specifies the namespaces to be restored. Multiple namespaces can be provided separated by comma.

-s (Optional) Specifies the name of the storageclass to be used for restore. If the storage class doesn't exist the script will abort.

-t (Optional) Specifies the timeout value in seconds. The script will check for status of restored namespaces and report until this timeout is reached. If not specified, the timeout will default to 1 Hr.

