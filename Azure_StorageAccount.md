# AzCopy
Microsoft Documentation : https://github.com/Azure/azure-storage-azcopy


# Azure Storage Account migration ( Synchronization )

AzCopy available on AzureCloudShell ( https://shell.azure.com/ )AzCopy available on AzureCloudShell ( https://shell.azure.com/ ) or Installation Guidelines available for Linux and Mac. This script tested on AzureCloudShell. 

##### Coverage Area
This script applicable for Storage account Share Files purpose only. Never tested for Blob files.

``` Azure
# Declare Variables
$Source1="https://XXXXX.file.core.windows.net/{SourceFolder}"
$Source1K="*******************************"
$Destination1="https://XXXXXX.file.core.windows.net/{DestinationFolder}"
$DestinationK1="*******************************"
```
#### One storage account to another storage account
```
azcopy --source $Source1 --destination $Destination1 --sync-copy --block-size-in-mb 24 --recursive --source-key $Source1K --dest-key $DestinationK1
```

*** --block-size-in-mb 24 increase the performance 10 times. Without Block size speed was 27 Mbps after that 16 MB/s

#### Same storage account, one share to another share
```
azcopy --source $Source1 --destination $Destination1 --sync-copy --sync-copy --block-size-in-mb 24 --recursive --source-key $Source1K --dest-key $DestinationK1
```

### MyExperience
1. One Storage to another storage sync speed 35 Mb to 50 Mb
2. Same storage account one share to another share sync speed up to 100 Mb


### April 9 
I discover that azcopy performance depends on host node. Today i ran one syn from azure cloud shell and the max speed was 9-12 MB/s. I have one vertual machine whiere CPU 12 and RAM 40 GB. I execute that same syn but speed was 85-09 MB/s. 

From same host azcopy dont allow multiple sync same time. 
