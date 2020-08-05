---
title: 删除具有活动租约的备份 Blob 文件 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: 13a8f879-274f-4934-a722-b4677fc9a782
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 02aea910589633a5c3ec79e283c757727b4d92cb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581330"
---
# <a name="deleting-backup-blob-files-with-active-leases"></a><span data-ttu-id="ff99d-102">删除具有活动租约的备份 Blob 文件</span><span class="sxs-lookup"><span data-stu-id="ff99d-102">Deleting Backup Blob Files with Active Leases</span></span>
  <span data-ttu-id="ff99d-103">备份到 Azure 存储或从中还原时，SQL Server 会获得无限期租约以锁定对 blob 的独占访问。</span><span class="sxs-lookup"><span data-stu-id="ff99d-103">When backing up to or restoring from Azure storage, SQL Server acquires an infinite lease in order to lock exclusive access to the blob.</span></span> <span data-ttu-id="ff99d-104">当成功完成备份或还原过程时，释放租约。</span><span class="sxs-lookup"><span data-stu-id="ff99d-104">When the backup or restore process is successfully completed, the lease is released.</span></span> <span data-ttu-id="ff99d-105">如果备份或还原失败，备份过程将尝试清除所有无效 blob。</span><span class="sxs-lookup"><span data-stu-id="ff99d-105">If a backup or restore fails, the backup process attempts to clean up any invalid blob.</span></span> <span data-ttu-id="ff99d-106">但是，如果由于持续很长时间的网络连接故障而导致备份失败，备份过程可能无法再次访问 blob 且 blob 可能保持孤立状态。</span><span class="sxs-lookup"><span data-stu-id="ff99d-106">However, if the backup fails due to prolonged or sustained network connectivity failure, the backup  process may not be able gain access to the blob and the blob may remain orphaned.</span></span> <span data-ttu-id="ff99d-107">这意味着在释放租约前，不能写入或删除 blob。</span><span class="sxs-lookup"><span data-stu-id="ff99d-107">This means that the blob cannot be written to or deleted until the lease is released.</span></span> <span data-ttu-id="ff99d-108">本主题说明如何释放租约和删除 blob。</span><span class="sxs-lookup"><span data-stu-id="ff99d-108">This topic describes how to release the lease and deleting the blob..</span></span>  
  
 <span data-ttu-id="ff99d-109">有关租约类型的详细信息，请阅读此 [文章](https://go.microsoft.com/fwlink/?LinkId=275664)。</span><span class="sxs-lookup"><span data-stu-id="ff99d-109">For more information on the types of leases, read this [article](https://go.microsoft.com/fwlink/?LinkId=275664).</span></span>  
  
 <span data-ttu-id="ff99d-110">如果备份操作失败，它可能生成无效的备份文件。</span><span class="sxs-lookup"><span data-stu-id="ff99d-110">If the backup operation fails, it can result in a backup file that is not valid.</span></span>  <span data-ttu-id="ff99d-111">备份 blob 文件可能还有活动租约，以防止其被删除或覆盖。</span><span class="sxs-lookup"><span data-stu-id="ff99d-111">The backup blob file might also have an active lease, preventing it from being deleted or overwritten.</span></span>  <span data-ttu-id="ff99d-112">为了删除或覆盖这类 blob，应首先中断租约。如果备份失败，我们建议您清除租约并删除 blob。</span><span class="sxs-lookup"><span data-stu-id="ff99d-112">In order to delete or overwrite such blobs, the lease should first be broken.If there are backup failures, we recommend that you clean up leases and delete blobs.</span></span> <span data-ttu-id="ff99d-113">您还可以选择作为存储管理任务一部分的定期清除。</span><span class="sxs-lookup"><span data-stu-id="ff99d-113">You can also choose cleanup periodically as part of storage management tasks.</span></span>  
  
 <span data-ttu-id="ff99d-114">如果还原失败，将不阻止后续还原，因此活动租约不会导致问题。</span><span class="sxs-lookup"><span data-stu-id="ff99d-114">If there is a restore failure, subsequent restores are not blocked, and therefore the active lease may not be an issue.</span></span> <span data-ttu-id="ff99d-115">仅当必须覆盖或删除 blob 时，才有必要中断租约。</span><span class="sxs-lookup"><span data-stu-id="ff99d-115">Breaking the lease is only necessary when you have to overwrite or delete the blob.</span></span>  
  
## <a name="managing-orphaned-blobs"></a><span data-ttu-id="ff99d-116">管理孤立的 Blob</span><span class="sxs-lookup"><span data-stu-id="ff99d-116">Managing Orphaned Blobs</span></span>  
 <span data-ttu-id="ff99d-117">以下步骤说明在备份或还原活动失败后如何进行清除。</span><span class="sxs-lookup"><span data-stu-id="ff99d-117">The follow steps describe how to clean up after failed backup or restore activity.</span></span> <span data-ttu-id="ff99d-118">可以使用 PowerShell 脚本来执行所有这些步骤。</span><span class="sxs-lookup"><span data-stu-id="ff99d-118">All the steps can be done using PowerShell scripts.</span></span> <span data-ttu-id="ff99d-119">在接下来的章节中提供了代码示例：</span><span class="sxs-lookup"><span data-stu-id="ff99d-119">A code example is provided in the following section:</span></span>  
  
1.  <span data-ttu-id="ff99d-120">**标识具有租约的 blob：** 如果您有运行备份过程的脚本或进程，可能可以捕获脚本或进程内的失败并使用它清除 blob。</span><span class="sxs-lookup"><span data-stu-id="ff99d-120">**Identifying blobs that have leases:** If you have a script or a process that runs the backup processes, you might be able to capture the failure within the script or process and use that to clean up the blobs.</span></span>   <span data-ttu-id="ff99d-121">您还可以使用 LeaseStats 和 LeastState 属性来标识具有租约的 blob。</span><span class="sxs-lookup"><span data-stu-id="ff99d-121">You can also use the LeaseStats and LeastState properties to identify the blobs that have leases on them.</span></span> <span data-ttu-id="ff99d-122">一旦您标识了 blob，我们建议您查看列表，在删除 blob 前验证备份文件的有效性。</span><span class="sxs-lookup"><span data-stu-id="ff99d-122">Once you have identified the blobs, we recommend that you review the list, verify the validity of the backup file before deleting the blob.</span></span>  
  
2.  <span data-ttu-id="ff99d-123">**中断租约：** 获得授权的请求可以中断租约而不提供租约 ID。</span><span class="sxs-lookup"><span data-stu-id="ff99d-123">**Breaking the lease:** An authorized request can break the lease without supplying a lease ID.</span></span> <span data-ttu-id="ff99d-124">有关详细信息，请参阅 [此处](https://go.microsoft.com/fwlink/?LinkID=275664) 。</span><span class="sxs-lookup"><span data-stu-id="ff99d-124">See [here](https://go.microsoft.com/fwlink/?LinkID=275664) for more information.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="ff99d-125">SQL Server 发出租约 ID 以在还原操作期间建立独占访问。</span><span class="sxs-lookup"><span data-stu-id="ff99d-125">SQL Server issues a lease ID to establish exclusive access during the restore operation.</span></span> <span data-ttu-id="ff99d-126">还原租约 ID 是 BAC2BAC2BAC2BAC2BAC2BAC2BAC2BAC2。</span><span class="sxs-lookup"><span data-stu-id="ff99d-126">The restore lease ID is BAC2BAC2BAC2BAC2BAC2BAC2BAC2BAC2.</span></span>  
  
3.  <span data-ttu-id="ff99d-127">**删除 Blob：** 要删除具有活动租约的 blob，必须首先中断租约。</span><span class="sxs-lookup"><span data-stu-id="ff99d-127">**Deleting the Blob:** To delete a blob that has an active lease, you must first break the lease.</span></span>  
  
###  <a name="powershell-script-example"></a><a name="Code_Example"></a><span data-ttu-id="ff99d-128">PowerShell 脚本示例</span><span class="sxs-lookup"><span data-stu-id="ff99d-128">PowerShell Script Example</span></span>  
 <span data-ttu-id="ff99d-129">\*\* \* \* 重要 \* 提示 \* \*\*如果你运行的是 PowerShell 2.0，则加载 Microsoft WindowsAzure.Storage.dll 程序集时可能会遇到问题。</span><span class="sxs-lookup"><span data-stu-id="ff99d-129">**\*\* Important \*\*** If you are running PowerShell 2.0, you may have problems loading the Microsoft WindowsAzure.Storage.dll assembly.</span></span> <span data-ttu-id="ff99d-130">我们建议您升级到 Powershell 3.0 以解决该问题。</span><span class="sxs-lookup"><span data-stu-id="ff99d-130">We recommend that you upgrade to Powershell 3.0 to solve the issue.</span></span> <span data-ttu-id="ff99d-131">您也可以为 PowerShell 2.0 使用以下解决方法：</span><span class="sxs-lookup"><span data-stu-id="ff99d-131">You may also use the following workaround for PowerShell 2.0:</span></span>  
  
-   <span data-ttu-id="ff99d-132">使用以下语句创建或修改 powershell.exe.config 文件以在运行时加载 .NET 2.0 和 .NET 4.0 程序集：</span><span class="sxs-lookup"><span data-stu-id="ff99d-132">Create or modify the powershell.exe.config file to load .NET 2.0 and .NET 4.0 assemblies at runtime with the following:</span></span>  
  
    ```xml
    <?xml version="1.0"?>
    <configuration>
        <startup useLegacyV2RuntimeActivationPolicy="true">
            <supportedRuntime version="v4.0.30319"/>
            <supportedRuntime version="v2.0.50727"/>
        </startup>
    </configuration>
    ```  
  
 <span data-ttu-id="ff99d-133">下面的示例说明了如何标识具有活动租约的 blob，然后中断租约。</span><span class="sxs-lookup"><span data-stu-id="ff99d-133">The following example illustrates identifying blobs that have active leases and then breaking them.</span></span> <span data-ttu-id="ff99d-134">该示例还演示如何为释放租约 ID 进行筛选。</span><span class="sxs-lookup"><span data-stu-id="ff99d-134">The example also demonstrates how filter for release lease IDs.</span></span>  
  
 <span data-ttu-id="ff99d-135">有关运行此脚本的提示</span><span class="sxs-lookup"><span data-stu-id="ff99d-135">Tips on running this script</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="ff99d-136">如果与此脚本同时运行备份到 Azure Blob 存储服务，则备份可能会失败，因为此脚本将中断备份尝试同时获取的租约。</span><span class="sxs-lookup"><span data-stu-id="ff99d-136">If a backup to Azure Blob storage service is running at the same time as this script, the backup can fail since this script will break the lease that the backup is trying to acquire at the same time.</span></span> <span data-ttu-id="ff99d-137">我们建议在维护时间段或预计没有执行备份时运行此脚本。</span><span class="sxs-lookup"><span data-stu-id="ff99d-137">We recommend running this script during a maintenance windows or when no backups are expected to run.</span></span>  
  
1.  <span data-ttu-id="ff99d-138">运行此脚本时，系统将提示你为存储帐户、存储密钥、容器和 Azure 存储程序集路径和名称参数提供值。</span><span class="sxs-lookup"><span data-stu-id="ff99d-138">When you run this script, you will be prompted to provide values for the storage account, storage key, container, and the Azure storage assembly path and name parameters.</span></span> <span data-ttu-id="ff99d-139">存储程序集的路径为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例的安装目录。</span><span class="sxs-lookup"><span data-stu-id="ff99d-139">The path of the storage is assembly is the installation directory of the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="ff99d-140">存储程序集的文件名为 Microsoft.WindowsAzure.Storage.dll。</span><span class="sxs-lookup"><span data-stu-id="ff99d-140">The file name for the storage assembly is Microsoft.WindowsAzure.Storage.dll.</span></span> <span data-ttu-id="ff99d-141">以下是提示和输入的值的示例：</span><span class="sxs-lookup"><span data-stu-id="ff99d-141">Following is an example of the prompts and values entered:</span></span>  
  
    ```  
    cmdlet  at command pipeline position 1  
    Supply values for the following parameters:  
    storageAccount: mycloudstorageaccount  
    storageKey: 0BopKY7eEha3gBnistYk+904nf  
    blobContainer: mycontainer   
    storageAssemblyPath: C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Binn\Microsoft.WindowsAzure.Storage.dll  
    ```  
  
2.  <span data-ttu-id="ff99d-142">如果没有已锁定租约的 blob，您应该看到以下消息：</span><span class="sxs-lookup"><span data-stu-id="ff99d-142">If there are no blobs that have locked leases you should see the following message:</span></span>  
  
     <span data-ttu-id="ff99d-143">**没有具有已锁定租约状态的 blob**</span><span class="sxs-lookup"><span data-stu-id="ff99d-143">**There are no blobs with locked lease status**</span></span>  
  
     <span data-ttu-id="ff99d-144">如果有具有已锁定租约的 blob，您应该看到以下消息：</span><span class="sxs-lookup"><span data-stu-id="ff99d-144">If there are blobs with locked leases, you should see the following messages:</span></span>  
  
     <span data-ttu-id="ff99d-145">**正在中断租约**</span><span class="sxs-lookup"><span data-stu-id="ff99d-145">**Breaking Leases**</span></span>  
  
     <span data-ttu-id="ff99d-146">**上的租约 \<URL of the Blob> 是还原租约：仅当具有的 blob 具有仍处于活动状态的还原租约时，才能看到此消息。**</span><span class="sxs-lookup"><span data-stu-id="ff99d-146">**The lease on \<URL of the Blob> is a restore lease: You will see this message only if you have a blob with a restore lease that is still active.**</span></span>  
  
     <span data-ttu-id="ff99d-147">**上的租约 \<URL of the Blob> 不是还原租约中断租约 \<URL of the Bob> 。**</span><span class="sxs-lookup"><span data-stu-id="ff99d-147">**The lease on \<URL of the Blob> is not a restore lease Breaking lease on \<URL of the Bob>.**</span></span>  
  
```powershell
param(  
       [Parameter(Mandatory=$true)]  
       [string]$storageAccount,  
       [Parameter(Mandatory=$true)]  
       [string]$storageKey,  
       [Parameter(Mandatory=$true)]  
       [string]$blobContainer,  
       [Parameter(Mandatory=$true)]  
       [string]$storageAssemblyPath  
)  
  
# Well known Restore Lease ID  
$restoreLeaseId = "BAC2BAC2BAC2BAC2BAC2BAC2BAC2BAC2"  
  
# Load the storage assembly without locking the file for the duration of the PowerShell session  
$bytes = [System.IO.File]::ReadAllBytes($storageAssemblyPath)  
[System.Reflection.Assembly]::Load($bytes)  
  
$cred = New-Object 'Microsoft.WindowsAzure.Storage.Auth.StorageCredentials' $storageAccount, $storageKey  
$client = New-Object 'Microsoft.WindowsAzure.Storage.Blob.CloudBlobClient' "https://$storageAccount.blob.core.windows.net", $cred  
$container = $client.GetContainerReference($blobContainer)  
  
#list all the blobs  
$allBlobs = $container.ListBlobs()
  
$lockedBlobs = @()  
# filter blobs that are have Lease Status as "locked"  
foreach($blob in $allBlobs)  
{  
    $blobProperties = $blob.Properties
    if($blobProperties.LeaseStatus -eq "Locked")  
    {  
        $lockedBlobs += $blob  
    }  
}  
  
if ($lockedBlobs.Count -eq 0)  
{
    Write-Host " There are no blobs with locked lease status"  
}

if($lockedBlobs.Count -gt 0)  
{  
    Write-Host "Breaking leases"  
    foreach($blob in $lockedBlobs )
    {  
        try  
        {  
            $blob.AcquireLease($null, $restoreLeaseId, $null, $null, $null)  
            Write-Host "The lease on $($blob.Uri) is a restore lease"  
        }  
        catch [Microsoft.WindowsAzure.Storage.StorageException]  
        {  
            if($_.Exception.RequestInformation.HttpStatusCode -eq 409)  
            {  
                Write-Host "The lease on $($blob.Uri) is not a restore lease"  
            }  
        }  
  
        Write-Host "Breaking lease on $($blob.Uri)"  
        $blob.BreakLease($(New-TimeSpan), $null, $null, $null) | Out-Null  
    }  
}
```  
  
## <a name="see-also"></a><span data-ttu-id="ff99d-148">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ff99d-148">See Also</span></span>  
 [<span data-ttu-id="ff99d-149">从 SQL Server 备份到 URL 的最佳做法和故障排除</span><span class="sxs-lookup"><span data-stu-id="ff99d-149">SQL Server Backup to URL Best Practices and Troubleshooting</span></span>](sql-server-backup-to-url-best-practices-and-troubleshooting.md)  
