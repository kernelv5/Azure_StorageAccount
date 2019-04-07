#### Azure Storage Account migration ( Synchronization )

AzCopy available on AzureCloudShell ( https://shell.azure.com/ )AzCopy available on AzureCloudShell ( https://shell.azure.com/ ) or Installation Guidelines available for Linux and Mac. This script tested on AzureCloudShell. 

##### Coverage Area
This script applicable for Storage account Share Files purpose only. Never tested for Blob files.

``` Azure
# Declare Variables
$Source1="https://XXXXX.file.core.windows.net/alf-data/solr4Backup"
$Source1K="*******************************"
$Destination1="https://XXXXXX.file.core.windows.net/alf-data/solr4Backup"
$DestinationK1="*******************************"
```
###### One storage account to another storage account
```
azcopy --source $Source1 --destination $Destination1 --sync-copy --recursive --source-key $Source1K --dest-key $DestinationK1
```

###### Same storage account, one share to another share
```
azcopy --source $Source1 --destination $Destination1 --sync-copy --sync-copy --block-size-in-mb 24 --recursive --source-key $Source1K --dest-key $DestinationK1
```

##### MyExperience
1. One Storage to another storage sync speed 35 Mb to 50 Mb
2. Same storage account one share to another share sync speed up to 100 Mb
