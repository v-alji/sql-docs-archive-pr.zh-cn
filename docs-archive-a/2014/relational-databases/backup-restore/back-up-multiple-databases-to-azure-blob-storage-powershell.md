---
title: 使用 PowerShell 将多个数据库备份到 Azure Blob 存储服务 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: f7008339-e69d-4e20-9265-d649da670460
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 95da5d0009f88943029e62960e7429b292242bbb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587437"
---
# <a name="use-powershell-to-backup-multiple-databases-to-azure-blob-storage-service"></a><span data-ttu-id="6a73e-102">使用 PowerShell 将多个数据库备份到 Azure Blob 存储服务</span><span class="sxs-lookup"><span data-stu-id="6a73e-102">Use PowerShell to Backup Multiple Databases to Azure Blob Storage Service</span></span>
  <span data-ttu-id="6a73e-103">本主题提供一些示例脚本，可用于通过 PowerShell cmdlet 自动备份到 Azure Blob 存储服务。</span><span class="sxs-lookup"><span data-stu-id="6a73e-103">This topic provides sample scripts that can be used to automate backups to Azure Blob storage service using PowerShell cmdlets.</span></span>  
  
## <a name="overview-of-powershell-cmdlets-for-backup-and-restore"></a><span data-ttu-id="6a73e-104">用于备份和还原的 PowerShell cmdlet 的概述</span><span class="sxs-lookup"><span data-stu-id="6a73e-104">Overview of PowerShell cmdlets for Backup and Restore</span></span>  
 <span data-ttu-id="6a73e-105">`Backup-SqlDatabase` 和 `Restore-SqlDatabase` 是两个用于进行备份和还原操作的主要 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="6a73e-105">The `Backup-SqlDatabase` and `Restore-SqlDatabase` are the two main cmdlets available to do backup and restore operations.</span></span> <span data-ttu-id="6a73e-106">此外，可能还需要其他 cmdlet 才能自动备份到 Azure Blob 存储，如这组 SqlCredential\*\*\*\* cmdlet。下面列出了 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中提供的用于备份和还原操作中的 PowerShell cmdlet：</span><span class="sxs-lookup"><span data-stu-id="6a73e-106">In addition, there are other cmdlets that may be required to automate backups to Azure Blob storage like the set of **SqlCredential** cmdlets  Following is a list of PowerShell cmdlets available in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] that are used in backup and restore operations:</span></span>  
  
 <span data-ttu-id="6a73e-107">Backup-SqlDatabase</span><span class="sxs-lookup"><span data-stu-id="6a73e-107">Backup-SqlDatabase</span></span>  
 <span data-ttu-id="6a73e-108">此 cmdlet 用于创建 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 备份。</span><span class="sxs-lookup"><span data-stu-id="6a73e-108">This cmdlet is used to create a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Backup.</span></span>  
  
 <span data-ttu-id="6a73e-109">Restore-SqlDatabase</span><span class="sxs-lookup"><span data-stu-id="6a73e-109">Restore-SqlDatabase</span></span>  
 <span data-ttu-id="6a73e-110">用于还原数据库。</span><span class="sxs-lookup"><span data-stu-id="6a73e-110">Used to restore a database.</span></span>  
  
 <span data-ttu-id="6a73e-111">New-SqlCredential</span><span class="sxs-lookup"><span data-stu-id="6a73e-111">New-SqlCredential</span></span>  
 <span data-ttu-id="6a73e-112">此 cmdlet 用于创建一个 SQL 凭据，后者用于 SQL Server 备份到 Azure 存储。</span><span class="sxs-lookup"><span data-stu-id="6a73e-112">This cmdlet is used to create a SQL Credential to use for SQL Server Backup to Azure Storage.</span></span> <span data-ttu-id="6a73e-113">有关凭据及其在 SQL Server 备份和还原中的用法的详细信息，请参阅[使用 Azure Blob 存储服务 SQL Server 备份和还原](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)。</span><span class="sxs-lookup"><span data-stu-id="6a73e-113">For more information on credentials and their use in SQL Server Backup and Restore, see [SQL Server Backup and Restore with Azure Blob Storage Service](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md).</span></span>  
  
 <span data-ttu-id="6a73e-114">Get-SqlCredential</span><span class="sxs-lookup"><span data-stu-id="6a73e-114">Get-SqlCredential</span></span>  
 <span data-ttu-id="6a73e-115">此 cmdlet 用于检索凭据对象及其属性。</span><span class="sxs-lookup"><span data-stu-id="6a73e-115">This cmdlet is used to retrieve the Credential object and its properties.</span></span>  
  
 <span data-ttu-id="6a73e-116">Remove-SqlCredential</span><span class="sxs-lookup"><span data-stu-id="6a73e-116">Remove-SqlCredential</span></span>  
 <span data-ttu-id="6a73e-117">删除 SQL 凭据对象。</span><span class="sxs-lookup"><span data-stu-id="6a73e-117">Delete a SQL Credential object</span></span>  
  
 <span data-ttu-id="6a73e-118">Set-SqlCredential</span><span class="sxs-lookup"><span data-stu-id="6a73e-118">Set-SqlCredential</span></span>  
 <span data-ttu-id="6a73e-119">此 cmdlet 用于更改或设置 SQL 凭据对象的属性。</span><span class="sxs-lookup"><span data-stu-id="6a73e-119">This cmdlet is used to change or set the properties of the SQL Credential Object.</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="6a73e-120">凭据 cmdlet 用于备份和还原到 Azure Blob 存储的场景中。</span><span class="sxs-lookup"><span data-stu-id="6a73e-120">The Credential cmdlets are used in Backup and Restore to Azure Blob storage scenarios.</span></span>  
  
### <a name="powershell-for-multi-database-multi-instance-backup-operations"></a><span data-ttu-id="6a73e-121">用于多数据库、多实例备份操作的 PowerShell</span><span class="sxs-lookup"><span data-stu-id="6a73e-121">PowerShell for Multi-Database, Multi-Instance Backup Operations</span></span>  
 <span data-ttu-id="6a73e-122">以下几个部分包含用于多种操作的脚本，如在多个 SQL Server 实例上创建 SQL 凭据，备份 SQL Server 实例中的所有用户数据库等。</span><span class="sxs-lookup"><span data-stu-id="6a73e-122">The following sections include scripts for various operations like creating a SQL Credential on multiple instance of SQL Server, backing up all user databases in an instance of SQL Server, and such.</span></span> <span data-ttu-id="6a73e-123">可使用这些脚本根据所处环境的要求自动进行备份操作或安排备份操作。</span><span class="sxs-lookup"><span data-stu-id="6a73e-123">You can use these scripts to automate or schedule backup operations according to the requirements of your environment.</span></span> <span data-ttu-id="6a73e-124">此处提供的脚本仅为示例，可针对所处环境修改或扩展这些脚本。</span><span class="sxs-lookup"><span data-stu-id="6a73e-124">The scripts provided here are examples, and may be modified or extended for your environment.</span></span>  
  
 <span data-ttu-id="6a73e-125">以下是这些示例脚本的注意事项：</span><span class="sxs-lookup"><span data-stu-id="6a73e-125">The following are considerations for the sample scripts:</span></span>  
  
1.  <span data-ttu-id="6a73e-126">**在 SQL Server PowerShell 路径中导航：** Windows PowerShell 实现了一些 cmdlet，可在表示 PowerShell 提供程序支持的对象层次的路径结构中导航。</span><span class="sxs-lookup"><span data-stu-id="6a73e-126">**Navigating SQL Server PowerShell paths:** Windows PowerShell implements cmdlets to navigate the path structure that represents the hierarchy of objects supported by a PowerShell provider.</span></span> <span data-ttu-id="6a73e-127">在您导航到该路径中的节点时，可以使用其他 cmdlet 以便针对当前对象执行基本操作。</span><span class="sxs-lookup"><span data-stu-id="6a73e-127">When you have navigated to a node in the path, you can use other cmdlets to perform basic operations on the current object.</span></span>  
  
2.  <span data-ttu-id="6a73e-128">`Get-ChildItem` cmdlet：`Get-ChildItem` 返回的信息取决于 SQL Server PowerShell 路径中的位置。</span><span class="sxs-lookup"><span data-stu-id="6a73e-128">`Get-ChildItem` cmdlet: The information returned by the `Get-ChildItem` depends on the location in a SQL Server PowerShell path.</span></span> <span data-ttu-id="6a73e-129">例如，如果该位置在计算机级别，则此 cmdlet 返回计算机上安装的所有 SQL Server 数据库引擎实例。</span><span class="sxs-lookup"><span data-stu-id="6a73e-129">For example, if the location is at the computer level, this cmdlet returns all the SQL Server database engine instances installed on the computer.</span></span> <span data-ttu-id="6a73e-130">再举一个例子，如果该位置在数据库等对象级别，则此 cmdlet 返回数据库对象的列表。</span><span class="sxs-lookup"><span data-stu-id="6a73e-130">As another example, if the location is at the object level such as databases, then this cmdlet returns a list of database objects.</span></span>  <span data-ttu-id="6a73e-131">默认情况下，`Get-ChildItem` cmdlet 不返回系统对象。</span><span class="sxs-lookup"><span data-stu-id="6a73e-131">By default the `Get-ChildItem` cmdlet does not return system objects.</span></span>  <span data-ttu-id="6a73e-132">使用 -Force 参数可查看系统对象。</span><span class="sxs-lookup"><span data-stu-id="6a73e-132">Using the -Force parameter you can see the system objects.</span></span>  
  
     <span data-ttu-id="6a73e-133">有关详细信息，请参阅 [Navigate SQL Server PowerShell Paths](../../powershell/navigate-sql-server-powershell-paths.md)。</span><span class="sxs-lookup"><span data-stu-id="6a73e-133">For more information, see [Navigate SQL Server PowerShell Paths](../../powershell/navigate-sql-server-powershell-paths.md).</span></span>  
  
3.  <span data-ttu-id="6a73e-134">尽管可通过更改变量值独立尝试每个代码示例，但对于所有备份和还原到 Azure Blob 存储服务的操作，创建 Azure 存储帐户和 SQL 凭据均为先决条件和必备条件。</span><span class="sxs-lookup"><span data-stu-id="6a73e-134">Although each code sample can be tried independently by changing the variable values, creating an Azure Storage Account and a SQL Credential are prerequisites and required for all backup and restore operations to Azure Blob storage service.</span></span>  
  
### <a name="create-a-sql-credential-on-all-the-instances-of-sql-server"></a><span data-ttu-id="6a73e-135">在所有 SQL Server 实例上创建 SQL 凭据</span><span class="sxs-lookup"><span data-stu-id="6a73e-135">Create a SQL Credential on All the Instances of SQL Server</span></span>  
 <span data-ttu-id="6a73e-136">下面有两个示例脚本，并且二者都在计算机上的所有 SQL Server 实例上创建 SQL 凭据“mybackupToURL”。</span><span class="sxs-lookup"><span data-stu-id="6a73e-136">There are two sample scripts, and both create a SQL Credential "mybackupToURL" on all the instances of SQL Server on a computer.</span></span> <span data-ttu-id="6a73e-137">第一个示例比较简单，它创建凭据但不捕获异常。</span><span class="sxs-lookup"><span data-stu-id="6a73e-137">The first example creates is simple and creates the credential and does not trap exceptions.</span></span>  <span data-ttu-id="6a73e-138">例如，如果计算机的某个实例上已有同名的现有凭据，则该脚本将失败。</span><span class="sxs-lookup"><span data-stu-id="6a73e-138">For example, if there was already an existing credential with the same name on one of the instances of the computer, the script would fail.</span></span> <span data-ttu-id="6a73e-139">第二个示例捕获错误并允许脚本继续运行。</span><span class="sxs-lookup"><span data-stu-id="6a73e-139">The second example traps errors and allows the script to continue.</span></span>  
  
```powershell
import-module sqlps  
  
# create variables  
$storageAccount = "mystorageaccount"  
$storageKey = "<storageaccesskeyvalue>"  
$secureString = ConvertTo-SecureString $storageKey  -asplaintext -force  
$credentialName = "mybackuptoURL"  
  
#cd to computer level  
cd sqlserver:\sql\COMPUTERNAME  
# get the list of instances  
$instances = Get-ChildItem  
#pipe the instances to new-sqlcredentail cmdlet to create SQL credential  
$instances | New-SqlCredential -Name $credentialName -Identity $storageAccount -Secret $secureString  
```  
  
```powershell
import-module sqlps  
  
# set the parameter values
$storageAccount = "mystorageaccount"  
$storageKey = "<storageaccesskeyvalue>"  
$secureString = ConvertTo-SecureString $storageKey  -asplaintext -force  
$credentialName = "mybackuptoURL"  
  
#cd to computer level  
cd sqlserver:\sql\COMPUTERNAME  
# get the list of instances  
$instances = Get-ChildItem  
#loop through instances and create a SQL credential, output any errors  
ForEach ($instance In $instances)  
{  
    Try  
{  
     New-SqlCredential -Name $credentialName -path "SQLServer:\SQL\$($instance.name)" -Identity $storageAccount -Secret $secureString -ea Stop
}  
Catch [Exception]  
    {
            Write-Host "instance - $($instance.name): "$_.Exception.Message
    }
 }
```  
  
### <a name="remove-a-sql-credential-from-all-the-instances-of-sql-server"></a><span data-ttu-id="6a73e-140">从所有 SQL Server 实例中删除 SQL 凭据</span><span class="sxs-lookup"><span data-stu-id="6a73e-140">Remove A SQL Credential from All the Instances of SQL Server</span></span>  
 <span data-ttu-id="6a73e-141">此脚本可用于从计算机上安装的所有 SQL Server 实例中删除某个特定凭据。</span><span class="sxs-lookup"><span data-stu-id="6a73e-141">This script can be used to remove a specific credential from all the instances of SQL Server installed on the computer.</span></span> <span data-ttu-id="6a73e-142">如果某个特定实例上不存在凭据对象，则显示一条错误消息，而该脚本继续运行，直到检查完所有实例。</span><span class="sxs-lookup"><span data-stu-id="6a73e-142">If the Credential object does not exist on a specific instance, an error message is displayed, and the script continues until all instances are checked.</span></span>  
  
```powershell
import-module sqlps  
  
cd SQLServer:\SQL\COMPUTERNAME  
$credentialName = "mybackuptoURL"  
  
$instances = Get-ChildItem  
  
ForEach ($instance In $instances)  
   {
    Try  
        {  
            $path = "SQLServer:\SQL\$($instance.name)\credentials\$credentialName"   
            Remove-SqlCredential -Path $path -ea stop   
         }  
         Catch [Exception]  
         {  
            Write-Host $_.Exception.Message
        }
    }  
```  
  
### <a name="full-database-backup-for-all-databases-including-system-databases"></a><span data-ttu-id="6a73e-143">为所有数据库（包括系统数据库）进行完整数据库备份</span><span class="sxs-lookup"><span data-stu-id="6a73e-143">Full Database Backup for all Databases (INCLUDING SYSTEM DATABASES)</span></span>  
 <span data-ttu-id="6a73e-144">以下脚本创建计算机上所有数据库的备份。</span><span class="sxs-lookup"><span data-stu-id="6a73e-144">The following script creates backups of all databases on the computer.</span></span> <span data-ttu-id="6a73e-145">其中包括用户数据库和 **msdb** 系统数据库。</span><span class="sxs-lookup"><span data-stu-id="6a73e-145">This includes both user databases and **msdb** system database.</span></span> <span data-ttu-id="6a73e-146">该脚本筛选出 **tempdb** 和 **model** 系统数据库。</span><span class="sxs-lookup"><span data-stu-id="6a73e-146">The script filters out **tempdb** and **model** system databases.</span></span>  
  
```powershell
import-module sqlps  
# set the parameter values  
$storageAccount = "mystorageaccount"  
$blobContainer = "privatecontainertest"  
$backupUrlContainer = "https://$storageAccount.blob.core.windows.net/$blobContainer/"  
$credentialName = "mybackuptoURL"  
  
# cd to computer level
cd SQLServer:\SQL\COMPUTERNAME  
$instances = Get-ChildItem
# loop through each instances and backup up all the  databases -filter out tempdb and model databases  
  
 ForEach ($instance In $instances)  
 {  
   $path = "sqlserver:\sql\$($instance.name)\databases"  
   $alldatabases = Get-ChildItem -Force -path $path | Where-Object {$_.name -ne "tempdb" -and $_.name -ne "model"}   
   $alldatabases | Backup-SqlDatabase -BackupContainer $backupUrlContainer -SqlCredential $credentialName -Compression On -script   
 }
```  
  
### <a name="full-database-backup-for-all-user-databases"></a><span data-ttu-id="6a73e-147">为所有用户数据库进行完整数据库备份</span><span class="sxs-lookup"><span data-stu-id="6a73e-147">Full Database Backup for ALL User Databases</span></span>  
 <span data-ttu-id="6a73e-148">以下脚本可用于备份计算机上所有 SQL Server 实例上的所有用户数据库。</span><span class="sxs-lookup"><span data-stu-id="6a73e-148">The following script can be used to back up all the user databases on all the instances of SQL Server on the computer.</span></span>  
  
```powershell
import-module sqlps
  
$storageAccount = "mystorageaccount"  
$blobContainer = "privatecontainertest"  
$backupUrlContainer = "https://$storageAccount.blob.core.windows.net/$blobContainer/"  
$credentialName = "mybackuptoURL"  
  
# cd to computer level
cd SQLServer:\SQL\COMPUTERNAME  
$instances = Get-ChildItem
# loop through each instances and backup up all the user databases  
 ForEach ($instance In $instances)  
 {  
    $databases = dir "sqlserver:\sql\$($instance.name)\databases"  
    $databases | Backup-SqlDatabase -BackupContainer $backupUrlContainer -SqlCredential $credentialName -Compression On
 }  
```  
  
### <a name="full-database-backup-for-master-and-msdb-system-databases-on-all-the-instances-of-sql-server"></a><span data-ttu-id="6a73e-149">为所有 SQL Server 实例上的 MASTER 和 MSDB（系统数据库）进行完整数据库备份</span><span class="sxs-lookup"><span data-stu-id="6a73e-149">Full Database Backup for MASTER and MSDB (SYSTEM DATABASES) On All the Instances of SQL Server</span></span>  
 <span data-ttu-id="6a73e-150">以下脚本可用于备份在计算机上安装的所有 SQL Server 实例上的 **master** 和 **msdb** 数据库。</span><span class="sxs-lookup"><span data-stu-id="6a73e-150">The following script can be used to back up **master** and **msdb** databases on all the instances of SQL Server installed on the computer.</span></span>  
  
```powershell
import-module sqlps  
  
$storageAccount = "mystorageaccount"  
$blobContainer = "privatecontainertest"  
$backupUrlContainer = "https://$storageAccount.blob.core.windows.net/$blobContainer/"  
$credentialName = "mybackupToUrl"  
$sysDbs = "master", "msdb"  
  
#cd to computer level  
cd sqlserver:\sql\COMPUTERNAME  
$instances = Get-ChildItem
ForEach ($instance In $instances)  
 {  
      ForEach ($s In $sysdbs)  
     {  
        Backup-SqlDatabase -Database $s -path "sqlserver:\sql\$($instance.name)" -BackupContainer  $backupUrlContainer -SqlCredential $credentialName -Compression On   
}
 } 
```  
  
### <a name="full-database-backup-for-all-user-databases-on-an-instance-of-sql-server"></a><span data-ttu-id="6a73e-151">为 SQL Server 实例上的所有用户数据库进行完整数据库备份</span><span class="sxs-lookup"><span data-stu-id="6a73e-151">Full Database Backup for All User Databases on an Instance of SQL Server</span></span>  
 <span data-ttu-id="6a73e-152">以下脚本用于仅备份具名的 SQL Server 实例上提供的用户数据库。</span><span class="sxs-lookup"><span data-stu-id="6a73e-152">The following script is used to back up only the user databases available on a named instance of SQL Server.</span></span> <span data-ttu-id="6a73e-153">更改 $srvPath 参数值后，同一脚本还可用于计算机上的默认实例。</span><span class="sxs-lookup"><span data-stu-id="6a73e-153">The same script can be used for the default instance on the computer by changing the $srvPath parameter value.</span></span>  
  
```powershell
import-module sqlps  
  
$storageAccount = "mystorageaccount"  
$blobContainer = "privatecontainertest"  
$backupUrlContainer = "https://$storageAccount.blob.core.windows.net/$blobContainer/"  
$srvPath = "SQLServer:\SQL\COMPUTERNAME\INSTANCENAME"  # for default instance, the $srvpath variable is "SQLSERVER:\SQL\COMPUTERNAME\DEFAULT"  
$credentialName = "mybackupToUrl"  
  
#cd to computer level  
cd sqlserver:\sql\COMPUTERNAME  
  
#retrieves the database objects for a specific instance  
$databases = dir $srvPath\databases  
  
#backup all the user databases  
$databases | Backup-SqlDatabase -BackupContainer $backupUrlContainer -SqlCredential $credentialName -Compression On  
```  
  
### <a name="full-database-backup-for-only-system-databases-master-and-msdb-on-an-instance-of-sql-server"></a><span data-ttu-id="6a73e-154">仅为 SQL Server 实例上的系统数据库（MASTER 和 MSDB）进行完整数据库备份</span><span class="sxs-lookup"><span data-stu-id="6a73e-154">Full Database Backup for Only System Databases (MASTER AND MSDB) On an Instance of SQL Server</span></span>  
 <span data-ttu-id="6a73e-155">完整脚本可用于备份 SQL Server 的命名实例上的 **master** 和 **msdb** 数据库。</span><span class="sxs-lookup"><span data-stu-id="6a73e-155">The full script can be used to back up the **master** and the **msdb** databases on a named instance of SQL Server.</span></span> <span data-ttu-id="6a73e-156">更改 $srvPath 参数值后，同一脚本还可用于计算机上的默认实例。</span><span class="sxs-lookup"><span data-stu-id="6a73e-156">The same script can be used for the default instance on the computer by changing the $srvpath parameter value.</span></span>  
  
```powershell
import-module sqlps  
  
$storageAccount = "mystorageaccount"  
$blobContainer = "privatecontainertest"  
$backupUrlContainer = "https://$storageAccount.blob.core.windows.net/$blobContainer/"  
$srvPath = "SQLServer:\SQL\COMPUTERNAME\INSTANCENAME" # for default instance, the $srvpath variable is "SQLSERVER:\SQL\COMPUTERNAME\DEFAULT"  
$credentialName = "mybackupToUrl"  
  
#navigate to instance level  
cd $srvPath  
  
$sysDbs = "master", "msdb"  
ForEach ($s In $sysDbs)
{  
Backup-SqlDatabase -Database $s -BackupContainer $backupUrlContainer -SqlCredential $credentialName -Compression On  
}
```  
  
## <a name="see-also"></a><span data-ttu-id="6a73e-157">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6a73e-157">See Also</span></span>
 <span data-ttu-id="6a73e-158">[SQL Server Azure Blob 存储服务进行备份和还原](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md) [SQL SERVER 备份到 URL 最佳做法和故障排除](sql-server-backup-to-url-best-practices-and-troubleshooting.md)</span><span class="sxs-lookup"><span data-stu-id="6a73e-158">[SQL Server Backup and Restore with Azure Blob Storage Service](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md) [SQL Server Backup to URL Best Practices and Troubleshooting](sql-server-backup-to-url-best-practices-and-troubleshooting.md)</span></span>  
