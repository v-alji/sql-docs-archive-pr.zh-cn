---
title: SQL Server 备份到 URL | Microsoft Docs
ms.custom: ''
ms.date: 10/18/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: 11be89e9-ff2a-4a94-ab5d-27d8edf9167d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 6918a099e00b1de9e773320b5c6c0e4089859e02
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690671"
---
# <a name="sql-server-backup-to-url"></a><span data-ttu-id="58c2d-102">SQL Server 备份到 URL</span><span class="sxs-lookup"><span data-stu-id="58c2d-102">SQL Server Backup to URL</span></span>
  <span data-ttu-id="58c2d-103">本主题介绍了使用 Azure Blob 存储服务作为备份目标所需的概念、要求和组件。</span><span class="sxs-lookup"><span data-stu-id="58c2d-103">This topic introduces the concepts, requirements and components necessary to use the Azure Blob storage service as a backup destination.</span></span> <span data-ttu-id="58c2d-104">备份和还原功能与使用磁盘或磁带时相同，或类似但区别不大。</span><span class="sxs-lookup"><span data-stu-id="58c2d-104">The backup and restore functionality are same or similar to when using DISK or TAPE, with a few differences.</span></span> <span data-ttu-id="58c2d-105">区别均为显著的例外，并且本主题中包括少量代码示例。</span><span class="sxs-lookup"><span data-stu-id="58c2d-105">The differences are and any notable exceptions, and a few code examples are included in this topic.</span></span>  
  
## <a name="requirements-components-and-concepts"></a><span data-ttu-id="58c2d-106">要求、组件和概念</span><span class="sxs-lookup"><span data-stu-id="58c2d-106">Requirements, Components, and Concepts</span></span>  
 <span data-ttu-id="58c2d-107">**本节内容：**</span><span class="sxs-lookup"><span data-stu-id="58c2d-107">**In this section:**</span></span>  
  
-   [<span data-ttu-id="58c2d-108">安全性</span><span class="sxs-lookup"><span data-stu-id="58c2d-108">Security</span></span>](#security)  
  
-   [<span data-ttu-id="58c2d-109">关键组件和概念简介</span><span class="sxs-lookup"><span data-stu-id="58c2d-109">Introduction to Key Components and Concepts</span></span>](#intorkeyconcepts)  
  
-   [<span data-ttu-id="58c2d-110">Azure Blob 存储服务</span><span class="sxs-lookup"><span data-stu-id="58c2d-110">Azure Blob Storage Service</span></span>](#Blob)  
  
-   [<span data-ttu-id="58c2d-111">SQL Server 组件</span><span class="sxs-lookup"><span data-stu-id="58c2d-111">SQL Server Components</span></span>](#sqlserver)  
  
-   [<span data-ttu-id="58c2d-112">限制</span><span class="sxs-lookup"><span data-stu-id="58c2d-112">Limitations</span></span>](#limitations)  
  
-   [<span data-ttu-id="58c2d-113">支持备份/还原语句</span><span class="sxs-lookup"><span data-stu-id="58c2d-113">Support for Backup/Restore Statements</span></span>](#Support)  
  
-   [<span data-ttu-id="58c2d-114">使用 SQL Server Management Studio 中的备份任务</span><span class="sxs-lookup"><span data-stu-id="58c2d-114">Using Backup Task in SQL Server Management Studio</span></span>](sql-server-backup-to-url.md#BackupTaskSSMS)  
  
-   [<span data-ttu-id="58c2d-115">使用维护计划向导将 SQL Server 备份到 URL</span><span class="sxs-lookup"><span data-stu-id="58c2d-115">SQL Server Backup to URL Using Maintenance Plan Wizard</span></span>](sql-server-backup-to-url.md#MaintenanceWiz)  
  
-   [<span data-ttu-id="58c2d-116">使用 SQL Server Management Studio 从 Azure 存储还原</span><span class="sxs-lookup"><span data-stu-id="58c2d-116">Restoring from Azure storage Using SQL Server Management Studio</span></span>](sql-server-backup-to-url.md#RestoreSSMS)  
  
###  <a name="security"></a><a name="security"></a> <span data-ttu-id="58c2d-117">Security</span><span class="sxs-lookup"><span data-stu-id="58c2d-117">Security</span></span>  
 <span data-ttu-id="58c2d-118">下面是备份到 Azure Blob 存储服务或从中还原时的安全注意事项和要求。</span><span class="sxs-lookup"><span data-stu-id="58c2d-118">The following are security considerations and requirements when backing up to or restoring from the Azure Blob storage services.</span></span>  
  
-   <span data-ttu-id="58c2d-119">为 Azure Blob 存储服务创建容器时，我们建议你将访问权限设置为 "**专用**"。</span><span class="sxs-lookup"><span data-stu-id="58c2d-119">When creating a container for the Azure Blob storage service, we recommend that you set the access to **private**.</span></span> <span data-ttu-id="58c2d-120">将访问权限设置为“私有”后，只允许可提供对 Azure 帐户进行身份验证所需的信息的用户或帐户进行访问。</span><span class="sxs-lookup"><span data-stu-id="58c2d-120">Setting the access to private restricts the access to users or accounts able to provide the necessary information to authenticate to the Azure account.</span></span>  
  
    > [!IMPORTANT]  
    >  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="58c2d-121">要求在凭据中存储 Azure 帐户名和访问密钥身份验证 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="58c2d-121">requires Azure account name and access key authentication to be stored in a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Credential.</span></span> <span data-ttu-id="58c2d-122">此信息用于在执行备份或还原操作时向 Azure 帐户进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="58c2d-122">This information is used to authenticate to the Azure account when it performs backup or restore operations.</span></span>  
  
-   <span data-ttu-id="58c2d-123">用于发出 BACKUP 或 RESTORE 命令的用户帐户应属于具有“更改任意凭据”权限的 **db_backup 操作员**数据库角色。</span><span class="sxs-lookup"><span data-stu-id="58c2d-123">The user account that is used to issue BACKUP or RESTORE commands should be in the **db_backup operator** database role with **Alter any credential** permissions.</span></span>  
  
###  <a name="introduction-to-key-components-and-concepts"></a><a name="intorkeyconcepts"></a><span data-ttu-id="58c2d-124">关键组件和概念简介</span><span class="sxs-lookup"><span data-stu-id="58c2d-124">Introduction to Key Components and Concepts</span></span>  
 <span data-ttu-id="58c2d-125">以下两节介绍 Azure Blob 存储服务，以及 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 备份到 Azure blob 存储服务或从中还原时使用的组件。</span><span class="sxs-lookup"><span data-stu-id="58c2d-125">The following two sections introduce the Azure Blob storage service, and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] components used when backing up to or restoring from the Azure Blob storage service.</span></span> <span data-ttu-id="58c2d-126">了解这些组件以及它们之间的交互对备份到 Azure Blob 存储服务或从中进行还原来说至关重要。</span><span class="sxs-lookup"><span data-stu-id="58c2d-126">It is important to understand the components and the interaction between them to do a backup to or restore from the Azure Blob storage service.</span></span>  
  
 <span data-ttu-id="58c2d-127">创建 Azure 帐户是这个过程的第一步。</span><span class="sxs-lookup"><span data-stu-id="58c2d-127">Creating an Azure account is the first step to this process.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="58c2d-128">使用**Azure 存储帐户名称**及其**访问密钥**值来进行身份验证，并将 blob 写入和读取到存储服务。</span><span class="sxs-lookup"><span data-stu-id="58c2d-128">uses the **Azure storage account name** and its **access key** values to authenticate and write and read blobs to the storage service.</span></span> <span data-ttu-id="58c2d-129">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 凭据存储此身份验证信息并在备份或还原操作期间使用它。</span><span class="sxs-lookup"><span data-stu-id="58c2d-129">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Credential stores this authentication information and is used during the backup or restore operations.</span></span> <span data-ttu-id="58c2d-130">有关创建存储帐户和执行简单还原的完整演练，请参阅[使用 Azure 存储服务进行 SQL Server 备份和还原教程](https://go.microsoft.com/fwlink/?LinkId=271615)。</span><span class="sxs-lookup"><span data-stu-id="58c2d-130">For a complete walkthrough of creating a storage account and performing a simple restore, see [Tutorial Using Azure Storage Service for SQL Server Backup and Restore](https://go.microsoft.com/fwlink/?LinkId=271615).</span></span>  
  
 <span data-ttu-id="58c2d-131">![将存储帐户映射到 sql 凭据](../../tutorials/media/backuptocloud-storage-credential-mapping.gif "将存储帐户映射到 sql 凭据")</span><span class="sxs-lookup"><span data-stu-id="58c2d-131">![mapping storage account to sql credentials](../../tutorials/media/backuptocloud-storage-credential-mapping.gif "mapping storage account to sql credentials")</span></span>  
  
###  <a name="azure-blob-storage-service"></a><a name="Blob"></a><span data-ttu-id="58c2d-132">Azure Blob 存储服务</span><span class="sxs-lookup"><span data-stu-id="58c2d-132">Azure Blob Storage Service</span></span>  
 <span data-ttu-id="58c2d-133">**存储帐户：** 存储帐户是所有存储服务的起始点。</span><span class="sxs-lookup"><span data-stu-id="58c2d-133">**Storage Account:** The storage account is the starting point for all storage services.</span></span> <span data-ttu-id="58c2d-134">若要访问 Azure Blob 存储服务，请先创建一个 Azure 存储帐户。</span><span class="sxs-lookup"><span data-stu-id="58c2d-134">To access the Azure Blob Storage service, first create an Azure storage account.</span></span> <span data-ttu-id="58c2d-135">**存储帐户名称**及其**访问密钥**属性是对 Azure Blob 存储服务及其组件进行身份验证所必需的。</span><span class="sxs-lookup"><span data-stu-id="58c2d-135">The **storage account name** and its **access key** properties are required to authenticate to the Azure Blob Storage service and its components.</span></span>  
  
 <span data-ttu-id="58c2d-136">**容器：** 容器提供一组 Blob 的分组，并且可以存储无限数量的 Blob。</span><span class="sxs-lookup"><span data-stu-id="58c2d-136">**Container:** A container provides a grouping of a set of Blobs, and can store an unlimited number of Blobs.</span></span> <span data-ttu-id="58c2d-137">若要将 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 备份写入 Azure Blob 服务，必须至少创建根容器。</span><span class="sxs-lookup"><span data-stu-id="58c2d-137">To write a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backup to the Azure Blob service, you must have at least the root container created.</span></span>  
  
 <span data-ttu-id="58c2d-138">**Blob：** 任意类型和大小的文件。</span><span class="sxs-lookup"><span data-stu-id="58c2d-138">**Blob:** A file of any type and size.</span></span> <span data-ttu-id="58c2d-139">可将两类 Blob 存储到 Azure 存储服务中：块 Blob 和页 Blob。</span><span class="sxs-lookup"><span data-stu-id="58c2d-139">There are two types of blobs that can be stored in the Azure Blob storage service: block and page blobs.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="58c2d-140">备份将页 Blob 作为 Blob 类型。</span><span class="sxs-lookup"><span data-stu-id="58c2d-140">backup uses page Blobs as the Blob type.</span></span> <span data-ttu-id="58c2d-141">可以使用以下 URL 格式对 blob 寻址： https:// \<storage account> . blob.core.windows.net/\<container>/\<blob></span><span class="sxs-lookup"><span data-stu-id="58c2d-141">Blobs are addressable using the following URL format: https://\<storage account>.blob.core.windows.net/\<container>/\<blob></span></span>  
  
 <span data-ttu-id="58c2d-142">![Azure Blob 存储](../../database-engine/media/backuptocloud-blobarchitecture.gif "Azure Blob 存储")</span><span class="sxs-lookup"><span data-stu-id="58c2d-142">![Azure Blob Storage](../../database-engine/media/backuptocloud-blobarchitecture.gif "Azure Blob Storage")</span></span>  
  
 <span data-ttu-id="58c2d-143">有关 Azure Blob 存储服务的详细信息，请参阅[如何使用 Azure Blob 存储服务](https://www.windowsazure.com/develop/net/how-to-guides/blob-storage/)</span><span class="sxs-lookup"><span data-stu-id="58c2d-143">For more information about the Azure Blob storage service, see [How to use the Azure Blob Storage Service](https://www.windowsazure.com/develop/net/how-to-guides/blob-storage/)</span></span>  
  
 <span data-ttu-id="58c2d-144">有关页 Blob 的详细信息，请参阅[了解块 Blob 和页 Blob](https://msdn.microsoft.com/library/windowsazure/ee691964.aspx)</span><span class="sxs-lookup"><span data-stu-id="58c2d-144">For more information about page Blobs, see [Understanding Block and Page Blobs](https://msdn.microsoft.com/library/windowsazure/ee691964.aspx)</span></span>  
  
###  <a name="ssnoversion-components"></a><a name="sqlserver"></a> <span data-ttu-id="58c2d-145">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 组件</span><span class="sxs-lookup"><span data-stu-id="58c2d-145">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Components</span></span>  
 <span data-ttu-id="58c2d-146">**URL：** URL 指定统一资源标识符 (URI) 来标识唯一备份文件。</span><span class="sxs-lookup"><span data-stu-id="58c2d-146">**URL:** A URL specifies a Uniform Resource Identifier (URI) to a unique backup file.</span></span> <span data-ttu-id="58c2d-147">URL 用于提供 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 备份文件的位置和名称。</span><span class="sxs-lookup"><span data-stu-id="58c2d-147">The URL is used to provide the location and name of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backup file.</span></span> <span data-ttu-id="58c2d-148">在此实现中，唯一有效的 URL 是指向 Azure 存储帐户中的页 Blob 的 URL。</span><span class="sxs-lookup"><span data-stu-id="58c2d-148">In this implementation, the only valid URL is one that points to a page Blob in an Azure storage account.</span></span> <span data-ttu-id="58c2d-149">该 URL 必须指向实际 Blob，而不仅仅是容器。</span><span class="sxs-lookup"><span data-stu-id="58c2d-149">The URL must point to an actual Blob, not just a container.</span></span> <span data-ttu-id="58c2d-150">如果 Blob 不存在，则创建它。</span><span class="sxs-lookup"><span data-stu-id="58c2d-150">If the Blob does not exist, it is created.</span></span> <span data-ttu-id="58c2d-151">如果指定了现有 Blob，BACKUP 将失败，除非指定了 "WITH FORMAT" 选项。</span><span class="sxs-lookup"><span data-stu-id="58c2d-151">If an existing Blob is specified, BACKUP fails, unless the "WITH FORMAT" option is specified.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="58c2d-152">如果选择将备份文件复制并上传到 Azure Blob 存储服务，请使用页 Blob 作为存储选项。</span><span class="sxs-lookup"><span data-stu-id="58c2d-152">If you choose to copy and upload a backup file to the Azure Blob storage service, use page blob as your storage option.</span></span> <span data-ttu-id="58c2d-153">不支持从块 Blob 进行还原。</span><span class="sxs-lookup"><span data-stu-id="58c2d-153">Restores from Block Blobs are not supported.</span></span> <span data-ttu-id="58c2d-154">从块 blob 类型 RESTORE 将出错并且失败。</span><span class="sxs-lookup"><span data-stu-id="58c2d-154">RESTORE from a block blob type fails with an error.</span></span>  
  
 <span data-ttu-id="58c2d-155">下面是一个示例 URL 值： http [s]：//ACCOUNTNAME.Blob.core.windows.net/ \<CONTAINER> / \<FILENAME.bak> 。</span><span class="sxs-lookup"><span data-stu-id="58c2d-155">Here is a sample URL value: http[s]://ACCOUNTNAME.Blob.core.windows.net/\<CONTAINER>/\<FILENAME.bak>.</span></span> <span data-ttu-id="58c2d-156">HTTPS 不是必需的，但建议这样做。</span><span class="sxs-lookup"><span data-stu-id="58c2d-156">HTTPS is not required, but is recommended.</span></span>  
  
 <span data-ttu-id="58c2d-157">**凭据：** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 凭据是用于存储连接到 SQL Server 外部资源所需的身份验证信息的对象。</span><span class="sxs-lookup"><span data-stu-id="58c2d-157">**Credential:** A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] credential is an object that is used to store authentication information required to connect to a resource outside of SQL Server.</span></span>  <span data-ttu-id="58c2d-158">在这里， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 备份和还原进程使用凭据对 Azure Blob 存储服务进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="58c2d-158">Here, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backup and restore processes use credential to authenticate to the Azure Blob storage service.</span></span> <span data-ttu-id="58c2d-159">凭据存储着存储帐户的名称和存储帐户的 **access key** 值。</span><span class="sxs-lookup"><span data-stu-id="58c2d-159">The Credential stores the name of the storage account and the storage account **access key** values.</span></span> <span data-ttu-id="58c2d-160">创建凭据后，在发出 BACKUP/RESTORE 命令时必须在 WITH CREDENTIAL 选项中指定它。</span><span class="sxs-lookup"><span data-stu-id="58c2d-160">Once the credential is created, it must be specified in the WITH CREDENTIAL option when issuing the BACKUP/RESTORE statements.</span></span> <span data-ttu-id="58c2d-161">有关如何查看、复制或重新生成存储帐户**访问密钥**的详细信息，请参阅[存储帐户访问密钥](https://msdn.microsoft.com/library/windowsazure/hh531566.aspx)。</span><span class="sxs-lookup"><span data-stu-id="58c2d-161">For more information about how to view, copy or regenerate storage account **access keys**, see [Storage Account Access Keys](https://msdn.microsoft.com/library/windowsazure/hh531566.aspx).</span></span>  
  
 <span data-ttu-id="58c2d-162">有关如何创建 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 凭据的分步说明，请参阅本主题后面的 [创建凭据](#credential) 示例。</span><span class="sxs-lookup"><span data-stu-id="58c2d-162">For step by step instructions about how to create a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Credential, see [Create a Credential](#credential) example later in this topic.</span></span>  
  
 <span data-ttu-id="58c2d-163">有关凭据的一般信息，请参阅 [凭据](../security/authentication-access/credentials-database-engine.md)</span><span class="sxs-lookup"><span data-stu-id="58c2d-163">For general information about credentials, see [Credentials](../security/authentication-access/credentials-database-engine.md)</span></span>  
  
 <span data-ttu-id="58c2d-164">有关使用凭据的其他示例的信息，请参阅[创建 SQL Server 代理代理](../../ssms/agent/create-a-sql-server-agent-proxy.md)。</span><span class="sxs-lookup"><span data-stu-id="58c2d-164">For information, on other examples where credentials are used, see [Create a SQL Server Agent Proxy](../../ssms/agent/create-a-sql-server-agent-proxy.md).</span></span>  
  
###  <a name="limitations"></a><a name="limitations"></a> <span data-ttu-id="58c2d-165">限制</span><span class="sxs-lookup"><span data-stu-id="58c2d-165">Limitations</span></span>  
  
-   <span data-ttu-id="58c2d-166">不支持备份到高级存储。</span><span class="sxs-lookup"><span data-stu-id="58c2d-166">Backup to premium storage is not supported.</span></span>  
  
-   <span data-ttu-id="58c2d-167">支持的最大备份大小为 1 TB。</span><span class="sxs-lookup"><span data-stu-id="58c2d-167">The maximum backup size supported is 1 TB.</span></span>  
  
-   <span data-ttu-id="58c2d-168">可使用 TSQL、SMO 或 PowerShell cmdlet 发出备份或还原语句。</span><span class="sxs-lookup"><span data-stu-id="58c2d-168">You can issue backup or restore statements by using TSQL, SMO, or PowerShell cmdlets.</span></span> <span data-ttu-id="58c2d-169">当前未启用备份到 Azure Blob 存储服务或从该 SQL Server Management Studio 服务还原的备份或还原向导。</span><span class="sxs-lookup"><span data-stu-id="58c2d-169">A backup to or restoring from the Azure Blob storage service by using SQL Server Management Studio Backup or Restore wizard is not currently enabled.</span></span>  
  
-   <span data-ttu-id="58c2d-170">不支持创建逻辑设备名称。</span><span class="sxs-lookup"><span data-stu-id="58c2d-170">Creating a logical device name is not supported.</span></span> <span data-ttu-id="58c2d-171">因此，不支持使用 sp_dumpdevice 或通过 SQL Server Management Studio 将 URL 添加为备份设备。</span><span class="sxs-lookup"><span data-stu-id="58c2d-171">So adding URL as a backup device using sp_dumpdevice or through SQL Server Management Studio is not supported.</span></span>  
  
-   <span data-ttu-id="58c2d-172">不支持追加到现有备份 blob。</span><span class="sxs-lookup"><span data-stu-id="58c2d-172">Appending to existing backup blobs is not supported.</span></span> <span data-ttu-id="58c2d-173">只能使用 WITH FORMAT 选项覆盖到现有 Blob 的备份。</span><span class="sxs-lookup"><span data-stu-id="58c2d-173">Backups to an existing Blob can only be overwritten by using the WITH FORMAT option.</span></span>  
  
-   <span data-ttu-id="58c2d-174">不支持在单个备份操作中备份到多个 blob。</span><span class="sxs-lookup"><span data-stu-id="58c2d-174">Backup to multiple blobs in a single backup operation is not supported.</span></span> <span data-ttu-id="58c2d-175">例如，下面的代码将返回错误：</span><span class="sxs-lookup"><span data-stu-id="58c2d-175">For example, the following returns an error:</span></span>  
  
    ```sql
    BACKUP DATABASE AdventureWorks2012
    TO URL = 'https://mystorageaccount.blob.core.windows.net/mycontainer/AdventureWorks2012_1.bak'
       URL = 'https://mystorageaccount.blob.core.windows.net/mycontainer/AdventureWorks2012_2.bak'
          WITH CREDENTIAL = 'mycredential'
         ,STATS = 5;  
    GO
    ```  
  
-   <span data-ttu-id="58c2d-176">不支持使用 `BACKUP` 指定块大小。</span><span class="sxs-lookup"><span data-stu-id="58c2d-176">Specifying a block size with `BACKUP` is not supported.</span></span>  
  
-   <span data-ttu-id="58c2d-177">不支持指定 `MAXTRANSFERSIZE`。</span><span class="sxs-lookup"><span data-stu-id="58c2d-177">Specifying `MAXTRANSFERSIZE` is not supported.</span></span>  
  
-   <span data-ttu-id="58c2d-178">不支持指定备份集选项 - `RETAINDAYS` 和 `EXPIREDATE`。</span><span class="sxs-lookup"><span data-stu-id="58c2d-178">Specifying backupset options - `RETAINDAYS` and `EXPIREDATE` are not supported.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="58c2d-179">要求备份设备名称最多包含 259 个字符。</span><span class="sxs-lookup"><span data-stu-id="58c2d-179">has a maximum limit of 259 characters for a backup device name.</span></span> <span data-ttu-id="58c2d-180">对于用于指定 URL“https://.blob.core.windows.net//.bak”所需的元素，BACKUP TO URL 占用 36 个字符，其余 223 个字符将用于帐户、容器和 Blob 名称。</span><span class="sxs-lookup"><span data-stu-id="58c2d-180">The BACKUP TO URL consumes 36 characters for the required elements used to specify the URL - 'https://.blob.core.windows.net//.bak', leaving 223 characters for account, container, and blob names put together.</span></span>  
  
###  <a name="support-for-backuprestore-statements"></a><a name="Support"></a> <span data-ttu-id="58c2d-181">对备份/还原语句的支持</span><span class="sxs-lookup"><span data-stu-id="58c2d-181">Support for Backup/Restore Statements</span></span>  
  
|||||  
|-|-|-|-|  
|<span data-ttu-id="58c2d-182">备份/还原语句</span><span class="sxs-lookup"><span data-stu-id="58c2d-182">Backup/Restore Statement</span></span>|<span data-ttu-id="58c2d-183">支持</span><span class="sxs-lookup"><span data-stu-id="58c2d-183">Supported</span></span>|<span data-ttu-id="58c2d-184">例外</span><span class="sxs-lookup"><span data-stu-id="58c2d-184">Exceptions</span></span>|<span data-ttu-id="58c2d-185">注释</span><span class="sxs-lookup"><span data-stu-id="58c2d-185">Comments</span></span>|  
|<span data-ttu-id="58c2d-186">BACKUP</span><span class="sxs-lookup"><span data-stu-id="58c2d-186">BACKUP</span></span>|<span data-ttu-id="58c2d-187">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="58c2d-187">&#x2713;</span></span>|<span data-ttu-id="58c2d-188">不支持 BLOCKSIZE 和 MAXTRANSFERSIZE。</span><span class="sxs-lookup"><span data-stu-id="58c2d-188">BLOCKSIZE, and MAXTRANSFERSIZE are not supported.</span></span>|<span data-ttu-id="58c2d-189">要求指定 WITH CREDENTIAL</span><span class="sxs-lookup"><span data-stu-id="58c2d-189">Requires WITH CREDENTIAL specified</span></span>|  
|<span data-ttu-id="58c2d-190">RESTORE</span><span class="sxs-lookup"><span data-stu-id="58c2d-190">RESTORE</span></span>|<span data-ttu-id="58c2d-191">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="58c2d-191">&#x2713;</span></span>||<span data-ttu-id="58c2d-192">要求指定 WITH CREDENTIAL</span><span class="sxs-lookup"><span data-stu-id="58c2d-192">Requires WITH CREDENTIAL specified</span></span>|  
|<span data-ttu-id="58c2d-193">RESTORE FILELISTONLY</span><span class="sxs-lookup"><span data-stu-id="58c2d-193">RESTORE FILELISTONLY</span></span>|<span data-ttu-id="58c2d-194">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="58c2d-194">&#x2713;</span></span>||<span data-ttu-id="58c2d-195">要求指定 WITH CREDENTIAL</span><span class="sxs-lookup"><span data-stu-id="58c2d-195">Requires WITH CREDENTIAL specified</span></span>|  
|<span data-ttu-id="58c2d-196">RESTORE HEADERONLY</span><span class="sxs-lookup"><span data-stu-id="58c2d-196">RESTORE HEADERONLY</span></span>|<span data-ttu-id="58c2d-197">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="58c2d-197">&#x2713;</span></span>||<span data-ttu-id="58c2d-198">要求指定 WITH CREDENTIAL</span><span class="sxs-lookup"><span data-stu-id="58c2d-198">Requires WITH CREDENTIAL specified</span></span>|  
|<span data-ttu-id="58c2d-199">RESTORE LABELONLY</span><span class="sxs-lookup"><span data-stu-id="58c2d-199">RESTORE LABELONLY</span></span>|<span data-ttu-id="58c2d-200">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="58c2d-200">&#x2713;</span></span>||<span data-ttu-id="58c2d-201">要求指定 WITH CREDENTIAL</span><span class="sxs-lookup"><span data-stu-id="58c2d-201">Requires WITH CREDENTIAL specified</span></span>|  
|<span data-ttu-id="58c2d-202">RESTORE VERIFYONLY</span><span class="sxs-lookup"><span data-stu-id="58c2d-202">RESTORE VERIFYONLY</span></span>|<span data-ttu-id="58c2d-203">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="58c2d-203">&#x2713;</span></span>||<span data-ttu-id="58c2d-204">要求指定 WITH CREDENTIAL</span><span class="sxs-lookup"><span data-stu-id="58c2d-204">Requires WITH CREDENTIAL specified</span></span>|  
|<span data-ttu-id="58c2d-205">RESTORE REWINDONLY</span><span class="sxs-lookup"><span data-stu-id="58c2d-205">RESTORE REWINDONLY</span></span>|<span data-ttu-id="58c2d-206">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="58c2d-206">&#x2713;</span></span>|||  
  
 <span data-ttu-id="58c2d-207">有关备份语句的语法和一般信息，请参阅 [BACKUP (Transact-SQL)](/sql/t-sql/statements/backup-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="58c2d-207">For syntax and general information about backup statements, see [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql).</span></span>  
  
 <span data-ttu-id="58c2d-208">有关还原语句的语法和一般信息，请参阅 [RESTORE (Transact-SQL)](/sql/t-sql/statements/restore-statements-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="58c2d-208">For syntax and general information about restore statements, see [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql).</span></span>  
  
### <a name="support-for-backup-arguments"></a><span data-ttu-id="58c2d-209">对备份参数的支持</span><span class="sxs-lookup"><span data-stu-id="58c2d-209">Support for Backup Arguments</span></span>  
  
|||||  
|-|-|-|-|  
|<span data-ttu-id="58c2d-210">参数</span><span class="sxs-lookup"><span data-stu-id="58c2d-210">Argument</span></span>|<span data-ttu-id="58c2d-211">支持</span><span class="sxs-lookup"><span data-stu-id="58c2d-211">Supported</span></span>|<span data-ttu-id="58c2d-212">异常</span><span class="sxs-lookup"><span data-stu-id="58c2d-212">Exception</span></span>|<span data-ttu-id="58c2d-213">注释</span><span class="sxs-lookup"><span data-stu-id="58c2d-213">Comments</span></span>|  
|<span data-ttu-id="58c2d-214">DATABASE</span><span class="sxs-lookup"><span data-stu-id="58c2d-214">DATABASE</span></span>|<span data-ttu-id="58c2d-215">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="58c2d-215">&#x2713;</span></span>|||  
|<span data-ttu-id="58c2d-216">LOG</span><span class="sxs-lookup"><span data-stu-id="58c2d-216">LOG</span></span>|<span data-ttu-id="58c2d-217">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="58c2d-217">&#x2713;</span></span>|||  
||  
|<span data-ttu-id="58c2d-218">TO (URL)</span><span class="sxs-lookup"><span data-stu-id="58c2d-218">TO (URL)</span></span>|<span data-ttu-id="58c2d-219">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="58c2d-219">&#x2713;</span></span>|<span data-ttu-id="58c2d-220">与 DISK 和 TAPE 不同，URL 不支持指定或创建逻辑名称。</span><span class="sxs-lookup"><span data-stu-id="58c2d-220">Unlike DISK and TAPE, URL does not support specifying or creating a logical name.</span></span>|<span data-ttu-id="58c2d-221">此参数用于指定备份文件的 URL 路径。</span><span class="sxs-lookup"><span data-stu-id="58c2d-221">This argument is used to specify the URL path for the backup file.</span></span>|  
|<span data-ttu-id="58c2d-222">MIRROR TO</span><span class="sxs-lookup"><span data-stu-id="58c2d-222">MIRROR TO</span></span>|<span data-ttu-id="58c2d-223">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="58c2d-223">&#x2713;</span></span>|||  
|<span data-ttu-id="58c2d-224">**WITH 选项：**</span><span class="sxs-lookup"><span data-stu-id="58c2d-224">**WITH OPTIONS:**</span></span>||||  
|<span data-ttu-id="58c2d-225">CREDENTIAL</span><span class="sxs-lookup"><span data-stu-id="58c2d-225">CREDENTIAL</span></span>|<span data-ttu-id="58c2d-226">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="58c2d-226">&#x2713;</span></span>||<span data-ttu-id="58c2d-227">仅当使用 BACKUP TO URL 选项备份到 Azure Blob 存储服务时，才支持 WITH CREDENTIAL。</span><span class="sxs-lookup"><span data-stu-id="58c2d-227">WITH CREDENTIAL is only supported when using BACKUP TO URL option to back up to the Azure Blob storage service.</span></span>|  
|<span data-ttu-id="58c2d-228">DIFFERENTIAL</span><span class="sxs-lookup"><span data-stu-id="58c2d-228">DIFFERENTIAL</span></span>|<span data-ttu-id="58c2d-229">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="58c2d-229">&#x2713;</span></span>|||  
|<span data-ttu-id="58c2d-230">COPY_ONLY</span><span class="sxs-lookup"><span data-stu-id="58c2d-230">COPY_ONLY</span></span>|<span data-ttu-id="58c2d-231">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="58c2d-231">&#x2713;</span></span>|||  
|<span data-ttu-id="58c2d-232">COMPRESSION&#124;NO_COMPRESSION</span><span class="sxs-lookup"><span data-stu-id="58c2d-232">COMPRESSION&#124;NO_COMPRESSION</span></span>|<span data-ttu-id="58c2d-233">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="58c2d-233">&#x2713;</span></span>|||  
|<span data-ttu-id="58c2d-234">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="58c2d-234">DESCRIPTION</span></span>|<span data-ttu-id="58c2d-235">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="58c2d-235">&#x2713;</span></span>|||  
|<span data-ttu-id="58c2d-236">名称</span><span class="sxs-lookup"><span data-stu-id="58c2d-236">NAME</span></span>|<span data-ttu-id="58c2d-237">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="58c2d-237">&#x2713;</span></span>|||  
|<span data-ttu-id="58c2d-238">EXPIREDATE &#124; RETAINDAYS</span><span class="sxs-lookup"><span data-stu-id="58c2d-238">EXPIREDATE &#124; RETAINDAYS</span></span>|<span data-ttu-id="58c2d-239">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="58c2d-239">&#x2713;</span></span>|||  
|<span data-ttu-id="58c2d-240">NOINIT &#124; INIT</span><span class="sxs-lookup"><span data-stu-id="58c2d-240">NOINIT &#124; INIT</span></span>|<span data-ttu-id="58c2d-241">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="58c2d-241">&#x2713;</span></span>||<span data-ttu-id="58c2d-242">如果使用，则忽略此选项。</span><span class="sxs-lookup"><span data-stu-id="58c2d-242">This option is ignored if used.</span></span><br /><br /> <span data-ttu-id="58c2d-243">不能追加到 blob。</span><span class="sxs-lookup"><span data-stu-id="58c2d-243">Appending to blobs is not possible.</span></span> <span data-ttu-id="58c2d-244">要覆盖备份，请使用 FORMAT 参数。</span><span class="sxs-lookup"><span data-stu-id="58c2d-244">To overwrite a backup use the FORMAT argument.</span></span>|  
|<span data-ttu-id="58c2d-245">NOSKIP &#124; SKIP</span><span class="sxs-lookup"><span data-stu-id="58c2d-245">NOSKIP &#124; SKIP</span></span>|<span data-ttu-id="58c2d-246">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="58c2d-246">&#x2713;</span></span>|||  
|<span data-ttu-id="58c2d-247">NOFORMAT &#124; FORMAT</span><span class="sxs-lookup"><span data-stu-id="58c2d-247">NOFORMAT &#124; FORMAT</span></span>|<span data-ttu-id="58c2d-248">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="58c2d-248">&#x2713;</span></span>||<span data-ttu-id="58c2d-249">如果使用，则忽略此选项。</span><span class="sxs-lookup"><span data-stu-id="58c2d-249">This option is ignored if used.</span></span><br /><br /> <span data-ttu-id="58c2d-250">除非指定 WITH FORMAT，否则对现有 blob 的备份失败。</span><span class="sxs-lookup"><span data-stu-id="58c2d-250">A backup taken to an existing blob fails unless WITH FORMAT is specified.</span></span> <span data-ttu-id="58c2d-251">指定 WITH FORMAT 时，覆盖现有 blob。</span><span class="sxs-lookup"><span data-stu-id="58c2d-251">The existing blob is overwritten when WITH FORMAT is specified.</span></span>|  
|<span data-ttu-id="58c2d-252">MEDIADESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="58c2d-252">MEDIADESCRIPTION</span></span>|<span data-ttu-id="58c2d-253">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="58c2d-253">&#x2713;</span></span>|||  
|<span data-ttu-id="58c2d-254">MEDIANAME</span><span class="sxs-lookup"><span data-stu-id="58c2d-254">MEDIANAME</span></span>|<span data-ttu-id="58c2d-255">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="58c2d-255">&#x2713;</span></span>|||  
|<span data-ttu-id="58c2d-256">BLOCKSIZE</span><span class="sxs-lookup"><span data-stu-id="58c2d-256">BLOCKSIZE</span></span>|<span data-ttu-id="58c2d-257">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="58c2d-257">&#x2713;</span></span>|||  
|<span data-ttu-id="58c2d-258">BUFFERCOUNT</span><span class="sxs-lookup"><span data-stu-id="58c2d-258">BUFFERCOUNT</span></span>|<span data-ttu-id="58c2d-259">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="58c2d-259">&#x2713;</span></span>|||  
|<span data-ttu-id="58c2d-260">MAXTRANSFERSIZE</span><span class="sxs-lookup"><span data-stu-id="58c2d-260">MAXTRANSFERSIZE</span></span>|<span data-ttu-id="58c2d-261">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="58c2d-261">&#x2713;</span></span>|||  
|<span data-ttu-id="58c2d-262">NO_CHECKSUM &#124; CHECKSUM</span><span class="sxs-lookup"><span data-stu-id="58c2d-262">NO_CHECKSUM &#124; CHECKSUM</span></span>|<span data-ttu-id="58c2d-263">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="58c2d-263">&#x2713;</span></span>|||  
|<span data-ttu-id="58c2d-264">STOP_ON_ERROR &#124; CONTINUE_AFTER_ERROR</span><span class="sxs-lookup"><span data-stu-id="58c2d-264">STOP_ON_ERROR &#124; CONTINUE_AFTER_ERROR</span></span>|<span data-ttu-id="58c2d-265">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="58c2d-265">&#x2713;</span></span>|||  
|<span data-ttu-id="58c2d-266">统计信息</span><span class="sxs-lookup"><span data-stu-id="58c2d-266">STATS</span></span>|<span data-ttu-id="58c2d-267">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="58c2d-267">&#x2713;</span></span>|||  
|<span data-ttu-id="58c2d-268">REWIND &#124; NOREWIND</span><span class="sxs-lookup"><span data-stu-id="58c2d-268">REWIND &#124; NOREWIND</span></span>|<span data-ttu-id="58c2d-269">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="58c2d-269">&#x2713;</span></span>|||  
|<span data-ttu-id="58c2d-270">UNLOAD &#124; NOUNLOAD</span><span class="sxs-lookup"><span data-stu-id="58c2d-270">UNLOAD &#124; NOUNLOAD</span></span>|<span data-ttu-id="58c2d-271">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="58c2d-271">&#x2713;</span></span>|||  
|<span data-ttu-id="58c2d-272">NORECOVERY &#124; STANDBY</span><span class="sxs-lookup"><span data-stu-id="58c2d-272">NORECOVERY &#124; STANDBY</span></span>|<span data-ttu-id="58c2d-273">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="58c2d-273">&#x2713;</span></span>|||  
|<span data-ttu-id="58c2d-274">NO_TRUNCATE</span><span class="sxs-lookup"><span data-stu-id="58c2d-274">NO_TRUNCATE</span></span>|<span data-ttu-id="58c2d-275">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="58c2d-275">&#x2713;</span></span>|||  
  
 <span data-ttu-id="58c2d-276">有关备份参数的详细信息，请参阅 [BACKUP (Transact-SQL)](/sql/t-sql/statements/backup-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="58c2d-276">For more information about backup arguments, see [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql).</span></span>  
  
### <a name="support-for-restore-arguments"></a><span data-ttu-id="58c2d-277">对还原参数的支持</span><span class="sxs-lookup"><span data-stu-id="58c2d-277">Support for Restore Arguments</span></span>  
  
|||||  
|-|-|-|-|  
|<span data-ttu-id="58c2d-278">参数</span><span class="sxs-lookup"><span data-stu-id="58c2d-278">Argument</span></span>|<span data-ttu-id="58c2d-279">支持</span><span class="sxs-lookup"><span data-stu-id="58c2d-279">Supported</span></span>|<span data-ttu-id="58c2d-280">例外</span><span class="sxs-lookup"><span data-stu-id="58c2d-280">Exceptions</span></span>|<span data-ttu-id="58c2d-281">注释</span><span class="sxs-lookup"><span data-stu-id="58c2d-281">Comments</span></span>|  
|<span data-ttu-id="58c2d-282">DATABASE</span><span class="sxs-lookup"><span data-stu-id="58c2d-282">DATABASE</span></span>|<span data-ttu-id="58c2d-283">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="58c2d-283">&#x2713;</span></span>|||  
|<span data-ttu-id="58c2d-284">LOG</span><span class="sxs-lookup"><span data-stu-id="58c2d-284">LOG</span></span>|<span data-ttu-id="58c2d-285">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="58c2d-285">&#x2713;</span></span>|||  
|<span data-ttu-id="58c2d-286">FROM (URL)</span><span class="sxs-lookup"><span data-stu-id="58c2d-286">FROM (URL)</span></span>|<span data-ttu-id="58c2d-287">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="58c2d-287">&#x2713;</span></span>||<span data-ttu-id="58c2d-288">FROM URL 参数用于指定备份文件的 URL 路径。</span><span class="sxs-lookup"><span data-stu-id="58c2d-288">The FROM URL argument is used to specify the URL path for the backup file.</span></span>|  
|<span data-ttu-id="58c2d-289">**WITH Options:**</span><span class="sxs-lookup"><span data-stu-id="58c2d-289">**WITH Options:**</span></span>||||  
|<span data-ttu-id="58c2d-290">CREDENTIAL</span><span class="sxs-lookup"><span data-stu-id="58c2d-290">CREDENTIAL</span></span>|<span data-ttu-id="58c2d-291">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="58c2d-291">&#x2713;</span></span>||<span data-ttu-id="58c2d-292">仅当使用 RESTORE FROM URL 选项从 Azure Blob 存储服务还原时，才支持 WITH CREDENTIAL。</span><span class="sxs-lookup"><span data-stu-id="58c2d-292">WITH CREDENTIAL is only supported when using RESTORE FROM URL option to restore from Azure Blob Storage service.</span></span>|  
|<span data-ttu-id="58c2d-293">PARTIAL</span><span class="sxs-lookup"><span data-stu-id="58c2d-293">PARTIAL</span></span>|<span data-ttu-id="58c2d-294">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="58c2d-294">&#x2713;</span></span>|||  
|<span data-ttu-id="58c2d-295">RECOVERY &#124; NORECOVERY &#124; STANDBY</span><span class="sxs-lookup"><span data-stu-id="58c2d-295">RECOVERY &#124; NORECOVERY &#124; STANDBY</span></span>|<span data-ttu-id="58c2d-296">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="58c2d-296">&#x2713;</span></span>|||  
|<span data-ttu-id="58c2d-297">LOADHISTORY</span><span class="sxs-lookup"><span data-stu-id="58c2d-297">LOADHISTORY</span></span>|<span data-ttu-id="58c2d-298">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="58c2d-298">&#x2713;</span></span>|||  
|<span data-ttu-id="58c2d-299">MOVE</span><span class="sxs-lookup"><span data-stu-id="58c2d-299">MOVE</span></span>|<span data-ttu-id="58c2d-300">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="58c2d-300">&#x2713;</span></span>|||  
|<span data-ttu-id="58c2d-301">REPLACE</span><span class="sxs-lookup"><span data-stu-id="58c2d-301">REPLACE</span></span>|<span data-ttu-id="58c2d-302">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="58c2d-302">&#x2713;</span></span>|||  
|<span data-ttu-id="58c2d-303">RESTART</span><span class="sxs-lookup"><span data-stu-id="58c2d-303">RESTART</span></span>|<span data-ttu-id="58c2d-304">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="58c2d-304">&#x2713;</span></span>|||  
|<span data-ttu-id="58c2d-305">RESTRICTED_USER</span><span class="sxs-lookup"><span data-stu-id="58c2d-305">RESTRICTED_USER</span></span>|<span data-ttu-id="58c2d-306">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="58c2d-306">&#x2713;</span></span>|||  
|<span data-ttu-id="58c2d-307">FILE</span><span class="sxs-lookup"><span data-stu-id="58c2d-307">FILE</span></span>|<span data-ttu-id="58c2d-308">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="58c2d-308">&#x2713;</span></span>|||  
|<span data-ttu-id="58c2d-309">PASSWORD</span><span class="sxs-lookup"><span data-stu-id="58c2d-309">PASSWORD</span></span>|<span data-ttu-id="58c2d-310">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="58c2d-310">&#x2713;</span></span>|||  
|<span data-ttu-id="58c2d-311">MEDIANAME</span><span class="sxs-lookup"><span data-stu-id="58c2d-311">MEDIANAME</span></span>|<span data-ttu-id="58c2d-312">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="58c2d-312">&#x2713;</span></span>|||  
|<span data-ttu-id="58c2d-313">MEDIAPASSWORD</span><span class="sxs-lookup"><span data-stu-id="58c2d-313">MEDIAPASSWORD</span></span>|<span data-ttu-id="58c2d-314">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="58c2d-314">&#x2713;</span></span>|||  
|<span data-ttu-id="58c2d-315">BLOCKSIZE</span><span class="sxs-lookup"><span data-stu-id="58c2d-315">BLOCKSIZE</span></span>|<span data-ttu-id="58c2d-316">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="58c2d-316">&#x2713;</span></span>|||  
|<span data-ttu-id="58c2d-317">BUFFERCOUNT</span><span class="sxs-lookup"><span data-stu-id="58c2d-317">BUFFERCOUNT</span></span>|<span data-ttu-id="58c2d-318">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="58c2d-318">&#x2713;</span></span>|||  
|<span data-ttu-id="58c2d-319">MAXTRANSFERSIZE</span><span class="sxs-lookup"><span data-stu-id="58c2d-319">MAXTRANSFERSIZE</span></span>|<span data-ttu-id="58c2d-320">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="58c2d-320">&#x2713;</span></span>|||  
|<span data-ttu-id="58c2d-321">CHECKSUM &#124; NO_CHECKSUM</span><span class="sxs-lookup"><span data-stu-id="58c2d-321">CHECKSUM &#124; NO_CHECKSUM</span></span>|<span data-ttu-id="58c2d-322">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="58c2d-322">&#x2713;</span></span>|||  
|<span data-ttu-id="58c2d-323">STOP_ON_ERROR &#124; CONTINUE_AFTER_ERROR</span><span class="sxs-lookup"><span data-stu-id="58c2d-323">STOP_ON_ERROR &#124; CONTINUE_AFTER_ERROR</span></span>|<span data-ttu-id="58c2d-324">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="58c2d-324">&#x2713;</span></span>|||  
|<span data-ttu-id="58c2d-325">FILESTREAM</span><span class="sxs-lookup"><span data-stu-id="58c2d-325">FILESTREAM</span></span>|<span data-ttu-id="58c2d-326">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="58c2d-326">&#x2713;</span></span>|||  
|<span data-ttu-id="58c2d-327">统计信息</span><span class="sxs-lookup"><span data-stu-id="58c2d-327">STATS</span></span>|<span data-ttu-id="58c2d-328">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="58c2d-328">&#x2713;</span></span>|||  
|<span data-ttu-id="58c2d-329">REWIND &#124; NOREWIND</span><span class="sxs-lookup"><span data-stu-id="58c2d-329">REWIND &#124; NOREWIND</span></span>|<span data-ttu-id="58c2d-330">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="58c2d-330">&#x2713;</span></span>|||  
|<span data-ttu-id="58c2d-331">UNLOAD &#124; NOUNLOAD</span><span class="sxs-lookup"><span data-stu-id="58c2d-331">UNLOAD &#124; NOUNLOAD</span></span>|<span data-ttu-id="58c2d-332">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="58c2d-332">&#x2713;</span></span>|||  
|<span data-ttu-id="58c2d-333">KEEP_REPLICATION</span><span class="sxs-lookup"><span data-stu-id="58c2d-333">KEEP_REPLICATION</span></span>|<span data-ttu-id="58c2d-334">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="58c2d-334">&#x2713;</span></span>|||  
|<span data-ttu-id="58c2d-335">KEEP_CDC</span><span class="sxs-lookup"><span data-stu-id="58c2d-335">KEEP_CDC</span></span>|<span data-ttu-id="58c2d-336">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="58c2d-336">&#x2713;</span></span>|||  
|<span data-ttu-id="58c2d-337">ENABLE_BROKER &#124; ERROR_BROKER_CONVERSATIONS &#124; NEW_BROKER</span><span class="sxs-lookup"><span data-stu-id="58c2d-337">ENABLE_BROKER &#124; ERROR_BROKER_CONVERSATIONS &#124; NEW_BROKER</span></span>|<span data-ttu-id="58c2d-338">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="58c2d-338">&#x2713;</span></span>|||  
|<span data-ttu-id="58c2d-339">STOPAT &#124; STOPATMARK &#124; STOPBEFOREMARK</span><span class="sxs-lookup"><span data-stu-id="58c2d-339">STOPAT &#124; STOPATMARK &#124; STOPBEFOREMARK</span></span>|<span data-ttu-id="58c2d-340">&#x2713;</span><span class="sxs-lookup"><span data-stu-id="58c2d-340">&#x2713;</span></span>|||  
  
 <span data-ttu-id="58c2d-341">有关还原参数的详细信息，请参阅[RESTORE 参数 (Transact-SQL)](/sql/t-sql/statements/restore-statements-arguments-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="58c2d-341">For more information about Restore arguments, see [RESTORE Arguments &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-arguments-transact-sql).</span></span>  
  
##  <a name="using-backup-task-in-sql-server-management-studio"></a><a name="BackupTaskSSMS"></a><span data-ttu-id="58c2d-342">在 SQL Server Management Studio 中使用备份任务</span><span class="sxs-lookup"><span data-stu-id="58c2d-342">Using Backup Task in SQL Server Management Studio</span></span>  
 <span data-ttu-id="58c2d-343">SQL Server Management Studio 中的备份任务已经过增强，其中包括 URL 作为一个目标选项，以及备份到 Azure 存储所需的其他支持对象，例如 SQL 凭据。</span><span class="sxs-lookup"><span data-stu-id="58c2d-343">The Backup task in SQL Server Management Studio has been enhanced to include URL as one of the destination options, and other supporting objects required to backup to Azure storage like the SQL Credential.</span></span>  
  
 <span data-ttu-id="58c2d-344">以下步骤描述对 "备份数据库" 任务所做的更改，以允许备份到 Azure 存储空间。：</span><span class="sxs-lookup"><span data-stu-id="58c2d-344">The following steps describe the changes made to the Back Up Database task to allow for backing up to Azure storage.:</span></span>  
  
1.  <span data-ttu-id="58c2d-345">启动 SQL Server Management Studio 并连接到 SQL Server 实例。</span><span class="sxs-lookup"><span data-stu-id="58c2d-345">Start SQL Server Management Studio and connect to the SQL Server instance.</span></span>  <span data-ttu-id="58c2d-346">选择要备份的数据库，右键单击 "**任务**"，然后选择 "**备份 ...**"这将打开 "备份数据库" 对话框。</span><span class="sxs-lookup"><span data-stu-id="58c2d-346">Select a database you want to backup, and right click on **Tasks**, and select **Back Up..**. This opens the Back Up Database dialog box.</span></span>  
  
2.  <span data-ttu-id="58c2d-347">在 "常规" 页上，使用**URL**选项创建到 Azure 存储的备份。</span><span class="sxs-lookup"><span data-stu-id="58c2d-347">On the general page the **URL** option is used to create a backup to Azure storage.</span></span> <span data-ttu-id="58c2d-348">选择此选项后，将看到此页上启用其他选项：</span><span class="sxs-lookup"><span data-stu-id="58c2d-348">When you select this option, you see other options enabled on this page:</span></span>  
  
    1.  <span data-ttu-id="58c2d-349">**文件名：** 备份文件的名称。</span><span class="sxs-lookup"><span data-stu-id="58c2d-349">**File Name:** Name of the backup file.</span></span>  
  
    2.  <span data-ttu-id="58c2d-350">**SQL 凭据：** 可指定现有的 SQL Server 凭据，也可通过单击“SQL 凭据”框旁的 **“创建”** ，新建一个。</span><span class="sxs-lookup"><span data-stu-id="58c2d-350">**SQL Credential:** You can either specify an existing SQL Server Credential, or can create a new one by clicking on the **Create** next to the SQL Credential box.</span></span>  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="58c2d-351">单击 **“创建”** 打开的对话框需要管理证书或订阅的发布配置文件。</span><span class="sxs-lookup"><span data-stu-id="58c2d-351">The dialog that opens when you click **Create** requires a management certificate or the publishing profile for the subscription.</span></span> <span data-ttu-id="58c2d-352">SQL Server 当前支持发布配置文件版本 2.0。</span><span class="sxs-lookup"><span data-stu-id="58c2d-352">SQL Server currently supports publishing profile version 2.0.</span></span> <span data-ttu-id="58c2d-353">要下载支持的发布配置文件版本，请参阅 [下载发布配置文件 2.0](https://go.microsoft.com/fwlink/?LinkId=396421)。</span><span class="sxs-lookup"><span data-stu-id="58c2d-353">To download the supported version of the publishing profile, see [Download Publishing Profile 2.0](https://go.microsoft.com/fwlink/?LinkId=396421).</span></span>  
        >   
        >  <span data-ttu-id="58c2d-354">如果您无权访问管理证书或发布配置文件，可以创建一个 SQL 凭据，方法是使用 Transact-SQL 或 SQL Server Management Studio 指定存储帐户名称和访问密钥信息。</span><span class="sxs-lookup"><span data-stu-id="58c2d-354">If you do not have access to the management certificate or publishing profile, you can create a SQL Credential by specifying the storage account name and access key information using Transact-SQL or SQL Server Management Studio.</span></span> <span data-ttu-id="58c2d-355">请参阅[创建凭据](#credential)部分中的示例代码，使用 transact-sql 创建凭据。</span><span class="sxs-lookup"><span data-stu-id="58c2d-355">See the sample code in the [Create a Credential](#credential) section to create a credential using Transact-SQL.</span></span> <span data-ttu-id="58c2d-356">或者，使用 SQL Server Management Studio，从数据库引擎实例中右键单击 **“安全性”**，依次选择 **“新建”** 和 **“凭据”**。</span><span class="sxs-lookup"><span data-stu-id="58c2d-356">Alternatively, using SQL Server Management Studio, from the database engine instance, right click **Security**, select **New**, and select **Credential**.</span></span> <span data-ttu-id="58c2d-357">在 **“标识”** 字段中指定存储帐户名称，在 **“密码”** 字段中指定访问密钥。</span><span class="sxs-lookup"><span data-stu-id="58c2d-357">Specify the storage account name for **Identity** and the access key in the **Password** field.</span></span>  
  
    3.  <span data-ttu-id="58c2d-358">**Azure 存储容器：** 用于存储备份文件的 Azure 存储容器的名称。</span><span class="sxs-lookup"><span data-stu-id="58c2d-358">**Azure storage container:** The name of the Azure storage container to store the backup files.</span></span>  
  
    4.  <span data-ttu-id="58c2d-359">**URL 前缀：** 使用在上一步中所述的字段中指定的信息自动生成此信息。</span><span class="sxs-lookup"><span data-stu-id="58c2d-359">**URL prefix:** This is built automatically using the information specified in the fields described in the previous steps.</span></span> <span data-ttu-id="58c2d-360">如果手动编辑此值，则确保它与以前提供的其他信息相匹配。</span><span class="sxs-lookup"><span data-stu-id="58c2d-360">If you do edit this value manually, make sure it matches with the other information you provided previously.</span></span> <span data-ttu-id="58c2d-361">例如，如果修改存储 URL，则确保设置 SQL 凭据以向同一存储帐户进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="58c2d-361">For example if you modify the storage URL, make sure the SQL Credential is set to authenticate to the same storage account.</span></span>  
  
 <span data-ttu-id="58c2d-362">选择 **URL** 作为目标后，将禁用“媒体选项”页中的某些选项。</span><span class="sxs-lookup"><span data-stu-id="58c2d-362">When you select URL as the destination, certain options in the **Media Options** page are disabled.</span></span>  <span data-ttu-id="58c2d-363">以下主题详细介绍“备份数据库”对话框：</span><span class="sxs-lookup"><span data-stu-id="58c2d-363">The following topics have more information on the Back Up Database dialog:</span></span>  
  
 [<span data-ttu-id="58c2d-364">备份数据库（“常规”页）</span><span class="sxs-lookup"><span data-stu-id="58c2d-364">Back Up Database &#40;General Page&#41;</span></span>](../../integration-services/general-page-of-integration-services-designers-options.md)  
  
 [<span data-ttu-id="58c2d-365">备份数据库（“媒体选项”页）</span><span class="sxs-lookup"><span data-stu-id="58c2d-365">Back Up Database &#40;Media Options Page&#41;</span></span>](back-up-database-media-options-page.md)  
  
 [<span data-ttu-id="58c2d-366">备份数据库（“备份选项”页）</span><span class="sxs-lookup"><span data-stu-id="58c2d-366">Back Up Database &#40;Backup Options Page&#41;</span></span>](back-up-database-backup-options-page.md)  
  
 [<span data-ttu-id="58c2d-367">创建凭据 - 向 Azure 存储进行身份验证</span><span class="sxs-lookup"><span data-stu-id="58c2d-367">Create Credential - Authenticate to Azure Storage</span></span>](create-credential-authenticate-to-azure-storage.md)  
  
##  <a name="sql-server-backup-to-url-using-maintenance-plan-wizard"></a><a name="MaintenanceWiz"></a><span data-ttu-id="58c2d-368">使用维护计划向导 SQL Server 备份到 URL</span><span class="sxs-lookup"><span data-stu-id="58c2d-368">SQL Server Backup to URL Using Maintenance Plan Wizard</span></span>  
 <span data-ttu-id="58c2d-369">与前面所述的备份任务类似，SQL Server Management Studio 中的维护计划向导已经过增强，其中包括**URL**作为一个目标选项，以及备份到 Azure 存储所需的其他支持对象，例如 SQL 凭据。</span><span class="sxs-lookup"><span data-stu-id="58c2d-369">Similar to the backup task described previously, the Maintenance Plan Wizard in SQL Server Management Studio has been enhanced to include **URL** as one of the destination options, and other supporting objects required to backup to Azure storage like the SQL Credential.</span></span> <span data-ttu-id="58c2d-370">有关详细信息，请参阅 **Using Maintenance Plan Wizard** 中的“定义备份任务”部分 [](../maintenance-plans/use-the-maintenance-plan-wizard.md#SSMSProcedure)。</span><span class="sxs-lookup"><span data-stu-id="58c2d-370">For more information, see  the **Define Backup Tasks** section in [Using Maintenance Plan Wizard](../maintenance-plans/use-the-maintenance-plan-wizard.md#SSMSProcedure).</span></span>  
  
##  <a name="restoring-from-azure-storage-using-sql-server-management-studio"></a><a name="RestoreSSMS"></a><span data-ttu-id="58c2d-371">使用 SQL Server Management Studio 从 Azure 存储还原</span><span class="sxs-lookup"><span data-stu-id="58c2d-371">Restoring from Azure storage Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="58c2d-372">如果要还原数据库，则加入 **URL** 作为要从其进行还原的设备。</span><span class="sxs-lookup"><span data-stu-id="58c2d-372">If you are restoring a database, **URL** is included as the device to restore from.</span></span> <span data-ttu-id="58c2d-373">以下步骤描述了还原任务中的更改允许从 Azure 存储还原：</span><span class="sxs-lookup"><span data-stu-id="58c2d-373">Following steps describe the changes in the Restore task to allow restoring from Azure storage:</span></span>  
  
1.  <span data-ttu-id="58c2d-374">在 SQL Server Management Studio 中还原任务的 **“常规”** 页中选择 **“设备”** 后，将进入 **“选择备份设备”** 对话框，其中包括 **“URL”** 作为备份介质类型。</span><span class="sxs-lookup"><span data-stu-id="58c2d-374">When you select **Devices** in the **General** page of the Restore task in SQL Server Management Studio, this takes you to the **Select backup devices** dialog box which includes **URL** as a backup media type.</span></span>  
  
2.  <span data-ttu-id="58c2d-375">选择 **“URL”** 并单击 **“添加”** 时，将打开 **“连接到 Azure 存储”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="58c2d-375">When you select **URL** and click **Add**, this opens the **Connect to Azure storage** dialog.</span></span> <span data-ttu-id="58c2d-376">指定要向 Azure 存储进行身份验证的 SQL 凭据信息。</span><span class="sxs-lookup"><span data-stu-id="58c2d-376">Specify the SQL Credential information to authenticate to Azure storage.</span></span>  
  
3.  <span data-ttu-id="58c2d-377">然后，SQL Server 使用提供的 SQL 凭据信息连接到 Azure 存储，然后打开 "**在 Azure 中定位备份文件**" 对话框。</span><span class="sxs-lookup"><span data-stu-id="58c2d-377">SQL Server then connects to Azure storage using the SQL Credential information you provided and opens the **Locate Backup File in Azure** dialog.</span></span> <span data-ttu-id="58c2d-378">此页上显示位于存储中的备份文件。</span><span class="sxs-lookup"><span data-stu-id="58c2d-378">The backup files residing in the storage are displayed on this page.</span></span> <span data-ttu-id="58c2d-379">选择要用于还原的文件，然后单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="58c2d-379">Select the file you want to use to restore and click **OK**.</span></span> <span data-ttu-id="58c2d-380">这会使你返回到 "**选择备份设备**" 对话框，然后单击此对话框上的 **"确定"** 将返回主 "**还原**" 对话框，你可以在该对话框中完成还原。</span><span class="sxs-lookup"><span data-stu-id="58c2d-380">This takes you back to the **Select Backup Devices** dialog, and Clicking **OK** on this dialog takes you back to the main **Restore** dialog where you will be able complete the restore.</span></span>  <span data-ttu-id="58c2d-381">有关详细信息，请参阅以下主题：</span><span class="sxs-lookup"><span data-stu-id="58c2d-381">For more information see, the following topics:</span></span>  
  
     [<span data-ttu-id="58c2d-382">还原数据库（“常规”页）</span><span class="sxs-lookup"><span data-stu-id="58c2d-382">Restore Database &#40;General Page&#41;</span></span>](restore-database-general-page.md)  
  
     [<span data-ttu-id="58c2d-383">还原数据库（“文件”页）</span><span class="sxs-lookup"><span data-stu-id="58c2d-383">Restore Database &#40;Files Page&#41;</span></span>](restore-database-files-page.md)  
  
     [<span data-ttu-id="58c2d-384">还原数据库（“选项”页）</span><span class="sxs-lookup"><span data-stu-id="58c2d-384">Restore Database &#40;Options Page&#41;</span></span>](restore-database-options-page.md)  
  
##  <a name="code-examples"></a><a name="Examples"></a> <span data-ttu-id="58c2d-385">代码示例</span><span class="sxs-lookup"><span data-stu-id="58c2d-385">Code Examples</span></span>  
 <span data-ttu-id="58c2d-386">本节包含以下示例。</span><span class="sxs-lookup"><span data-stu-id="58c2d-386">This section contains the following examples.</span></span>  
  
-   [<span data-ttu-id="58c2d-387">创建凭据</span><span class="sxs-lookup"><span data-stu-id="58c2d-387">Create a Credential</span></span>](#credential)  
  
-   [<span data-ttu-id="58c2d-388">备份整个数据库</span><span class="sxs-lookup"><span data-stu-id="58c2d-388">Backing up a complete database</span></span>](#complete)  
  
-   [<span data-ttu-id="58c2d-389">备份数据库和日志</span><span class="sxs-lookup"><span data-stu-id="58c2d-389">Backing up the database and log</span></span>](#databaselog)  
  
-   [<span data-ttu-id="58c2d-390">创建主文件组的完整文件备份</span><span class="sxs-lookup"><span data-stu-id="58c2d-390">Creating a full file backup of the primary filegroup</span></span>](#filebackup)  
  
-   [<span data-ttu-id="58c2d-391">创建主文件组的差异文件备份</span><span class="sxs-lookup"><span data-stu-id="58c2d-391">Creating a differential file backup of the primary filegroups</span></span>](#differential)  
  
-   [<span data-ttu-id="58c2d-392">还原数据库并移动文件</span><span class="sxs-lookup"><span data-stu-id="58c2d-392">Restoring a database and move files</span></span>](#restoredbwithmove)  
  
-   [<span data-ttu-id="58c2d-393">使用 STOPAT 还原到时间点</span><span class="sxs-lookup"><span data-stu-id="58c2d-393">Restoring to a point-in-time using STOPAT</span></span>](#PITR)  
  
###  <a name="create-a-credential"></a><a name="credential"></a> <span data-ttu-id="58c2d-394">创建凭据</span><span class="sxs-lookup"><span data-stu-id="58c2d-394">Create a Credential</span></span>  
 <span data-ttu-id="58c2d-395">以下示例创建了一个用于存储 Azure 存储身份验证信息的凭据。</span><span class="sxs-lookup"><span data-stu-id="58c2d-395">The following example creates a credential that stores the Azure Storage authentication information.</span></span>  

   ```sql
   IF NOT EXISTS  
   (SELECT * FROM sys.credentials   
   WHERE credential_identity = 'mycredential')  
   CREATE CREDENTIAL mycredential WITH IDENTITY = 'mystorageaccount'  
   ,SECRET = '<storage access key>' ;  
   ```
  
   ```csharp
   // Connect to default sql server instance on local machine  
   Server server = new Server(".");  
   string identity = "mystorageaccount";  
   string secret = "<storage access key>";  
  
   // Create a Credential  
   string credentialName = "mycredential";  
   Credential credential = new Credential(server, credentialName);  
   credential.Create(identity, secret);  
   ```  
  
   ```powershell
   # create variables  
   $storageAccount = "mystorageaccount"  
   $storageKey = "<storage access key>"  
   $secureString = ConvertTo-SecureString $storageKey  -asplaintext -force  
   $credentialName = "mycredential"  
  
   $srvPath = "SQLSERVER:\SQL\COMPUTERNAME\INSTANCENAME"  
   # for default instance, the $srvpath variable would be "SQLSERVER:\SQL\COMPUTERNAME\DEFAULT"  
  
   # Create a credential  
   New-SqlCredential -Name $credentialName -Path $srvpath -Identity $storageAccount -Secret $secureString
   ```  
  
###  <a name="backing-up-a-complete-database"></a><a name="complete"></a><span data-ttu-id="58c2d-396">备份整个数据库</span><span class="sxs-lookup"><span data-stu-id="58c2d-396">Backing up a complete database</span></span>  
 <span data-ttu-id="58c2d-397">下面的示例将 AdventureWorks2012 数据库备份到 Azure Blob 存储服务。</span><span class="sxs-lookup"><span data-stu-id="58c2d-397">The following example backs up the AdventureWorks2012 database to the Azure Blob storage service.</span></span>
  
   ```sql
   BACKUP DATABASE AdventureWorks2012   
   TO URL = 'https://mystorageaccount.blob.core.windows.net/mycontainer/AdventureWorks2012.bak'   
         WITH CREDENTIAL = 'mycredential'   
         ,COMPRESSION  
         ,STATS = 5;  
   GO
   ```  
  
   ```csharp
   // Connect to default sql server instance on local machine  
   Server server = new Server(".");  
   string identity = "mystorageaccount";  
  
   string credentialName = "mycredential";  
   string dbName = "AdventureWorks2012";  
   string blobContainerName = "mycontainer";  
  
   // Generate Unique Url  
   string url = String.Format(@"https://{0}.blob.core.windows.net/{1}/{2}-{3}.bak",  
            identity,  
            blobContainerName,  
            dbName,  
            DateTime.Now.ToString("s").Replace(":", "-"));  
  
   // Backup to Url  
   Backup backup = new Backup();  
   backup.CredentialName = credentialName;  
   backup.Database = dbName;  
   backup.CompressionOption = BackupCompressionOptions.On;  
   backup.Devices.AddDevice(url, DeviceType.Url);  
   backup.SqlBackup(server);  
   ```
  
   ```powershell
   # create variables  
   $backupUrlContainer = "https://mystorageaccount.blob.core.windows.net/mycontainer/"  
   $credentialName = "mycredential"  
   $srvPath = "SQLSERVER:\SQL\COMPUTERNAME\INSTANCENAME"   
   # for default instance, the $srvpath varilable would be "SQLSERVER:\SQL\COMPUTERNAME\DEFAULT"  
  
   # navigate to SQL Server Instance  
   CD $srvPath   
   $backupFile = $backupUrlContainer + "AdventureWorks2012" +  ".bak"  
   Backup-SqlDatabase -Database AdventureWorks2012 -backupFile $backupFile  -SqlCredential $credentialName -CompressionOption On
   ```  
  
###  <a name="backing-up-the-database-and-log"></a><a name="databaselog"></a><span data-ttu-id="58c2d-398">备份数据库和日志</span><span class="sxs-lookup"><span data-stu-id="58c2d-398">Backing up the database and log</span></span>  
 <span data-ttu-id="58c2d-399">下面的示例备份 AdventureWorks2012 示例数据库，默认情况下，该数据库使用简单恢复模式。</span><span class="sxs-lookup"><span data-stu-id="58c2d-399">The following example backups up the AdventureWorks2012 sample database, which uses the simple recovery model by default.</span></span> <span data-ttu-id="58c2d-400">若要支持日志备份，请将 AdventureWorks2012 数据库改为使用完整恢复模式。</span><span class="sxs-lookup"><span data-stu-id="58c2d-400">To support log backups, the AdventureWorks2012 database is modified to use the full recovery model.</span></span> <span data-ttu-id="58c2d-401">然后，该示例将创建一个完整的数据库备份到 Azure Blob，并在一段更新活动后备份该日志。</span><span class="sxs-lookup"><span data-stu-id="58c2d-401">The example then creates a full database backup to Azure Blob, and after a period of update activity, backs up the log.</span></span> <span data-ttu-id="58c2d-402">此示例将创建具有日期时间戳的备份文件名。</span><span class="sxs-lookup"><span data-stu-id="58c2d-402">This example creates a backup file name with a datetime stamp.</span></span>  
  
   ```sql
   -- To permit log backups, before the full database backup, modify the database   
   -- to use the full recovery model.  
   USE master;  
   GO  
   ALTER DATABASE AdventureWorks2012  
      SET RECOVERY FULL;  
   GO  
  
   -- Back up the full AdventureWorks2012 database.  
          -- First create a file name for the backup file with DateTime stamp  
  
   DECLARE @Full_Filename AS VARCHAR (300);  
   SET @Full_Filename = 'https://mystorageaccount.blob.core.windows.net/mycontainer/AdventureWorks2012_Full_'+   
   REPLACE (REPLACE (REPLACE (CONVERT (VARCHAR (40), GETDATE (), 120), '-','_'),':', '_'),' ', '_') + '.bak';   
   --Back up Adventureworks2012 database  
  
   BACKUP DATABASE AdventureWorks2012  
   TO URL =  @Full_Filename  
   WITH CREDENTIAL = 'mycredential';  
   ,COMPRESSION  
   GO  
   -- Back up the AdventureWorks2012 log.  
   DECLARE @Log_Filename AS VARCHAR (300);  
   SET @Log_Filename = 'https://mystorageaccount.blob.core.windows.net/mycontainer/AdventureWorks2012_Log_'+   
   REPLACE (REPLACE (REPLACE (CONVERT (VARCHAR (40), GETDATE (), 120), '-','_'),':', '_'),' ', '_') + '.trn';  
   BACKUP LOG AdventureWorks2012  
    TO URL = @Log_Filename  
    WITH CREDENTIAL = 'mycredential'  
    ,COMPRESSION;  
   GO  
   ```
  
   ```csharp
   // Connect to default sql server instance on local machine  
   Server server = new Server(".");  
   string identity = "mystorageaccount";  
  
   string credentialName = "mycredential";  
   string dbName = "AdventureWorks2012";  
   string blobContainerName = "mycontainer";  
  
   // Generate Unique Url for data backup  
   string urlDataBackup = String.Format(@"https://{0}.blob.core.windows.net/{1}/{2}_Data-{3}.bak",  
            identity,  
            blobContainerName,  
            dbName,  
            DateTime.Now.ToString("s").Replace(":", "-"));  
  
   // Backup Database to Url  
   Backup backupData = new Backup();  
   backupData.CredentialName = credentialName;  
   backupData.Database = dbName;  
   backup.CompressionOption = BackupCompressionOptions.On;  
   backupData.Devices.AddDevice(urlDataBackup, DeviceType.Url);  
   backupData.SqlBackup(server);  
  
   // Generate Unique Url for data backup  
   string urlLogBackup = String.Format(@"https://{0}.blob.core.windows.net/{1}/{2}_Log-{3}.bak",  
            identity,  
            blobContainerName,  
            dbName,  
            DateTime.Now.ToString("s").Replace(":", "-"));  
  
   // Backup Database Log to Url  
   Backup backupLog = new Backup();  
   backupLog.CredentialName = credentialName;  
   backupLog.Database = dbName;  
   backup.CompressionOption = BackupCompressionOptions.On;  
   backupLog.Devices.AddDevice(urlLogBackup, DeviceType.Url);  
   backupLog.Action = BackupActionType.Log;  
   backupLog.SqlBackup(server);  
   ```  

   ```powershell
   #create variables  
   $backupUrlContainer = "https://mystorageaccount.blob.core.windows.net/mycontainer/"  
   $credentialName = "mycredential"  
   $srvPath = "SQLSERVER:\SQL\COMPUTERNAME\INSTANCENAME"  
   # for default instance, the $srvpath variable would be "SQLSERVER:\SQL\COMPUTERNAME\DEFAULT"  
  
   # navigate to theSQL Server Instance
   CD $srvPath   
   #Create a unique file name for the full database backup  
   $backupFile = $backupUrlContainer + "AdventureWorks2012_" + (Get-Date).ToString("s").Replace("-","_").Replace(":", "_").Replace(" ","_").Replace("/", "_") +  ".bak"  
  
   #Backup Database to URL
   Backup-SqlDatabase -Database AdventureWorks2012 -backupFile $backupFile  -SqlCredential $credentialName -CompressionOption On -BackupAction Database    
  
   #Create a unique file name for log backup  
  
   $backupFile = $backupUrlContainer + "AdventureWorks2012_" + (Get-Date).ToString("s").Replace("-","_").Replace(":", "_").Replace(" ","_").Replace("/", "_") +  ".trn"  
  
   #Backup Log to URL
   Backup-SqlDatabase -Database AdventureWorks2012 -backupFile $backupFile  -SqlCredential $credentialName -CompressionOption On -BackupAction Log
   ```  
  
###  <a name="creating-a-full-file-backup-of-the-primary-filegroup"></a><a name="filebackup"></a><span data-ttu-id="58c2d-403">创建主文件组的完整文件备份</span><span class="sxs-lookup"><span data-stu-id="58c2d-403">Creating a full file backup of the primary filegroup</span></span>  
 <span data-ttu-id="58c2d-404">下面的示例创建主文件组的完整文件备份。</span><span class="sxs-lookup"><span data-stu-id="58c2d-404">The following example creates a full file backup of the primary filegroup.</span></span>
  
   ```sql
   --Back up the files in Primary:  
   BACKUP DATABASE AdventureWorks2012  
       FILEGROUP = 'Primary'  
       TO URL = 'https://mystorageaccount.blob.core.windows.net/mycontainer/AdventureWorks2012files.bck'  
       WITH CREDENTIAL = 'mycredential'  
       ,COMPRESSION;  
   GO  
   ```
  
   ```csharp
   // Connect to default sql server instance on local machine  
   Server server = new Server(".");  
   string identity = "mystorageaccount";  
  
   string credentialName = "mycredential";  
   string dbName = "AdventureWorks2012";  
   string blobContainerName = "mycontainer";  
  
   // Generate Unique Url  
   string url = String.Format(@"https://{0}.blob.core.windows.net/{1}/{2}-{3}.bck",  
            identity,  
            blobContainerName,  
            dbName,  
            DateTime.Now.ToString("s").Replace(":", "-"));  
  
   // Backup to Url  
   Backup backup = new Backup();  
   backup.CredentialName = credentialName;  
   backup.Database = dbName;  
   backup.Action = BackupActionType.Files;  
   backup.DatabaseFileGroups.Add("PRIMARY");  
   backup.CompressionOption = BackupCompressionOptions.On;  
   backup.Devices.AddDevice(url, DeviceType.Url);  
   backup.SqlBackup(server);
   ```
  
   ```powershell
   #create variables  
   $backupUrlContainer = "https://mystorageaccount.blob.core.windows.net/mycontainer/"  
   $credentialName = "mycredential"  
   $srvPath = "SQLSERVER:\SQL\COMPUTERNAME\INSTANCENAME"  
   # for default instance, the $srvpath variable would be "SQLSERVER:\SQL\COMPUTERNAME\DEFAULT"  
  
   # navigate to the SQL Server Instance  
  
   CD $srvPath   
   #Create a unique file name for the file backup  
   $backupFile = $backupUrlContainer + "AdventureWorks2012_" + (Get-Date).ToString("s").Replace("-","_").Replace(":", "_").Replace(" ","_").Replace("/", "_") +  ".bck"  
  
   #Backup Primary File Group to URL  
  
   Backup-SqlDatabase -Database AdventureWorks2012 -backupFile $backupFile  -SqlCredential $credentialName -CompressionOption On -BackupAction Files -DatabaseFileGroup Primary
   ```  
  
###  <a name="creating-a-differential-file-backup-of-the-primary-filegroup"></a><a name="differential"></a><span data-ttu-id="58c2d-405">创建主文件组的差异文件备份</span><span class="sxs-lookup"><span data-stu-id="58c2d-405">Creating a differential file backup of the primary filegroup</span></span>  
 <span data-ttu-id="58c2d-406">下面的示例创建主文件组的差异文件备份。</span><span class="sxs-lookup"><span data-stu-id="58c2d-406">The following example creates a differential file backup of the primary filegroup.</span></span>  
  
   ```sql
   --Back up the files in Primary:  
   BACKUP DATABASE AdventureWorks2012  
       FILEGROUP = 'Primary'  
       TO URL = 'https://mystorageaccount.blob.core.windows.net/mycontainer/AdventureWorks2012filesdiff.bck'  
       WITH   
          CREDENTIAL = 'mycredential'  
          ,COMPRESSION  
      ,DIFFERENTIAL;  
   GO
   ```
  
   ```csharp
   // Connect to default sql server instance on local machine  
   Server server = new Server(".");  
   string identity = "mystorageaccount";  
  
   string credentialName = "mycredential";  
   string dbName = "AdventureWorks2012";  
   string blobContainerName = "mycontainer";  
  
   // Generate Unique Url  
   string url = String.Format(@"https://{0}.blob.core.windows.net/{1}/{2}-{3}.bak",  
            identity,  
            blobContainerName,  
            dbName,  
            DateTime.Now.ToString("s").Replace(":", "-"));  
  
   // Backup to Url  
   Backup backup = new Backup();  
   backup.CredentialName = credentialName;  
   backup.Database = dbName;  
   backup.Action = BackupActionType.Files;  
   backup.DatabaseFileGroups.Add("PRIMARY");  
   backup.Incremental = true;  
   backup.CompressionOption = BackupCompressionOptions.On;  
   backup.Devices.AddDevice(url, DeviceType.Url);  
   backup.SqlBackup(server); 
   ```

   ```powershell
   #create variables  
   $backupUrlContainer = "https://mystorageaccount.blob.core.windows.net/mycontainer/"  
   $credentialName = "mycredential"  
   $srvPath = "SQLSERVER:\SQL\COMUTERNAME\INSTANCENAME"  
   # for default instance, the $srvpath variable would be "SQLSERVER:\SQL\COMPUTERNAME\DEFAULT"  
  
   # navigate to SQL Server Instance
   CD $srvPath   
  
   #create a unique file name for the full backup  
   $backupdbFile = $backupUrlContainer + "AdventureWorks2012_" + (Get-Date).ToString("s").Replace("-","_").Replace(":", "_").Replace(" ","_").Replace("/", "_") +  ".bak"  
  
   #Create a differential backup of the primary filegroup
   Backup-SqlDatabase -Database AdventureWorks2012 -backupFile $backupFile  -SqlCredential $credentialName -CompressionOption On -BackupAction Files -DatabaseFileGroup Primary -Incremental
   ```  
  
###  <a name="restore-a-database-and-move-files"></a><a name="restoredbwithmove"></a><span data-ttu-id="58c2d-407">还原数据库并移动文件</span><span class="sxs-lookup"><span data-stu-id="58c2d-407">Restore a database and move files</span></span>  
 <span data-ttu-id="58c2d-408">要还原完整数据库备份并将还原的数据库移到 C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Data 目录，请使用以下步骤。</span><span class="sxs-lookup"><span data-stu-id="58c2d-408">To restore a full database backup and move the restored database to C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Data directory, use the following steps.</span></span>
  
   ```sql
   -- Backup the tail of the log first
   DECLARE @Log_Filename AS VARCHAR (300);  
   SET @Log_Filename = 'https://mystorageaccount.blob.core.windows.net/mycontainer/AdventureWorks2012_Log_'+   
   REPLACE (REPLACE (REPLACE (CONVERT (VARCHAR (40), GETDATE (), 120), '-','_'),':', '_'),' ', '_') + '.trn';  
   BACKUP LOG AdventureWorks2012  
    TO URL = @Log_Filename  
    WITH CREDENTIAL = 'mycredential'  
    ,NORECOVERY;  
   GO  
  
   RESTORE DATABASE AdventureWorks2012 FROM URL = 'https://mystorageaccount.blob.core.windows.net/mycontainer/AdventureWorks2012.bak'  
   WITH CREDENTIAL = 'mycredential'  
    ,MOVE 'AdventureWorks2012_data' to 'C:\Program Files\Microsoft SQL Server\myinstance\MSSQL\DATA\AdventureWorks2012.mdf'  
    ,MOVE 'AdventureWorks2012_log' to 'C:\Program Files\Microsoft SQL Server\myinstance\MSSQL\DATA\AdventureWorks2012.ldf'  
    ,STATS = 5
   ```
  
   ```csharp
   // Connect to default sql server instance on local machine  
   Server server = new Server(".");  
   string identity = "mystorageaccount";  
  
   string credentialName = "mycredential";  
   string dbName = "AdventureWorks2012";  
   string blobContainerName = "mycontainer";  
  
   // Generate Unique Url  
   string urlBackupData = String.Format(@"https://{0}.blob.core.windows.net/{1}/{2}-Data{3}.bak",  
            identity,  
            blobContainerName,  
            dbName,  
            DateTime.Now.ToString("s").Replace(":", "-"));  
  
   // Backup to Url  
   Backup backup = new Backup();  
   backup.CredentialName = credentialName;  
   backup.Database = dbName;  
   backup.Devices.AddDevice(urlBackupData, DeviceType.Url);  
   backup.SqlBackup(server);  
  
   // Generate Unique Url for tail log backup  
   string urlTailLogBackup = String.Format(@"https://{0}.blob.core.windows.net/{1}/{2}-TailLog{3}.bak",  
            identity,  
            blobContainerName,  
            dbName,  
            DateTime.Now.ToString("s").Replace(":", "-"));  
  
   // Backup Tail Log to Url  
   Backup backupTailLog = new Backup();  
   backupTailLog.CredentialName = credentialName;  
   backupTailLog.Database = dbName;  
   backupTailLog.Action = BackupActionType.Log;  
   backupTailLog.NoRecovery = true;  
   backupTailLog.Devices.AddDevice(urlTailLogBackup, DeviceType.Url);  
   backupTailLog.SqlBackup(server);  
  
   // Restore a database and move files  
   string newDataFilePath = server.MasterDBLogPath  + @"\" + dbName + DateTime.Now.ToString("s").Replace(":", "-") + ".mdf";  
   string newLogFilePath = server.MasterDBLogPath  + @"\" + dbName + DateTime.Now.ToString("s").Replace(":", "-") + ".ldf";  
  
   Restore restore = new Restore();  
   restore.CredentialName = credentialName;  
   restore.Database = dbName;  
   restore.ReplaceDatabase = true;  
   restore.Devices.AddDevice(urlBackupData, DeviceType.Url);  
   restore.RelocateFiles.Add(new RelocateFile(dbName, newDataFilePath));  
   restore.RelocateFiles.Add(new RelocateFile(dbName+ "_Log", newLogFilePath));  
   restore.SqlRestore(server);
   ```  

   ```powershell
   #create variables  
   $backupUrlContainer = "https://mystorageaccount.blob.core.windows.net/mycontainer/"  
   $credentialName = "mycredential"  
   $srvPath = "SQLSERVER:\SQL\COMPUTERNAME\INSTNACENAME"  
   # for default instance, the $srvpath variable would be "SQLSERVER:\SQL\COMPUTERNAME\DEFAULT"  
  
   # navigate to SQL Server Instance
   CD $srvPath   
  
   #create a unique file name for the full backup  
   $backupdbFile = $backupUrlContainer + "AdventureWorks2012_" + (Get-Date).ToString("s").Replace("-","_").Replace(":", "_").Replace(" ","_").Replace("/", "_") +  ".bak"  
  
   # Full database backup to URL  
   Backup-SqlDatabase -Database AdventureWorks2012 -backupFile $backupdbFile  -SqlCredential $credentialName -CompressionOption On      
  
   #Create a unique file name for the tail log backup  
   $backuplogFile = $backupUrlContainer + "AdventureWorks2012_" + (Get-Date).ToString("s").Replace("-","_").Replace(":", "_").Replace(" ","_").Replace("/", "_") +  ".trn"  
  
   #Backup tail log to URL
   Backup-SqlDatabase -Database AdventureWorks2012 -backupFile $backupFile  -SqlCredential $credentialName  -BackupAction Log -NoRecovery    
  
   # Restore Database and move files
   $newDataFilePath = New-Object Microsoft.SqlServer.Management.Smo.RelocateFile ("AdventureWorks_Data","C:\Program Files\Microsoft SQL Server\myinstance\MSSQL\DATA\AdventureWorks2012.mdf")  
   $newLogFilePath = New-Object Microsoft.SqlServer.Management.Smo.RelocateFile("AdventureWorks_Log","C:\Program Files\Microsoft SQL Server\myinstance\MSSQL\DATA\AdventureWorks2012.ldf")  
  
   Restore-SqlDatabase -Database AdventureWorks2012 -SqlCredential $credentialName -BackupFile $backupdbFile -RelocateFile @($newDataFilePath,$newLogFilePath)
   ```  
  
###  <a name="restoring-to-a-point-in-time-using-stopat"></a><a name="PITR"></a> <span data-ttu-id="58c2d-409">使用 STOPAT 还原到时间点</span><span class="sxs-lookup"><span data-stu-id="58c2d-409">Restoring to a point-in-time using STOPAT</span></span>  
 <span data-ttu-id="58c2d-410">下面的示例将数据库状态还原到某个时间点并显示一个还原操作。</span><span class="sxs-lookup"><span data-stu-id="58c2d-410">The following example restores a database to its state to a point in time, and shows a restore operation.</span></span>  
  
   ```sql
   RESTORE DATABASE AdventureWorks FROM URL = 'https://mystorageaccount.blob.core.windows.net/mycontainer/AdventureWorks2012.bak'   
   WITH   
     CREDENTIAL = 'mycredential'  
    ,MOVE 'AdventureWorks2012_data' to 'C:\Program Files\Microsoft SQL Server\myinstance\MSSQL\DATA\AdventureWorks2012.mdf'  
    ,Move 'AdventureWorks2012_log' to 'C:\Program Files\Microsoft SQL Server\myinstance\MSSQL\DATA\AdventureWorks2012.ldf'  
    ,NORECOVERY  
    --,REPLACE  
    ,STATS = 5;  
   GO   
  
   RESTORE LOG AdventureWorks FROM URL = 'https://mystorageaccount.blob.core.windows.net/mycontainer/AdventureWorks2012.trn'   
   WITH CREDENTIAL = 'mycredential'  
    ,RECOVERY   
    ,STOPAT = 'Oct 23, 2012 5:00 PM'   
   GO  
   ```  
  
   ```csharp
   // Connect to default sql server instance on local machine  
   Server server = new Server(".");  
   string identity = "mystorageaccount";  
  
   string credentialName = "mycredential";  
   string dbName = "AdventureWorks2012";  
   string blobContainerName = "mycontainer";  
  
   // Generate Unique Url  
   string urlBackupData = String.Format(@"https://{0}.blob.core.windows.net/{1}/{2}-Data{3}.bak",  
            identity,  
            blobContainerName,  
            dbName,  
            DateTime.Now.ToString("s").Replace(":", "-"));  
  
   // Backup to Url  
   Backup backup = new Backup();  
   backup.CredentialName = credentialName;  
   backup.Database = dbName;  
   backup.Devices.AddDevice(urlBackupData, DeviceType.Url);  
   backup.SqlBackup(server);  
  
   // Generate Unique Url for Tail Log backup  
   string urlTailLogBackup = String.Format(@"https://{0}.blob.core.windows.net/{1}/{2}-TailLog{3}.bak",  
            identity,  
            blobContainerName,  
            dbName,  
            DateTime.Now.ToString("s").Replace(":", "-"));  
  
   // Backup Tail Log to Url  
   Backup backupTailLog = new Backup();  
   backupTailLog.CredentialName = credentialName;  
   backupTailLog.Database = dbName;  
   backupTailLog.Action = BackupActionType.Log;  
   backupTailLog.NoRecovery = true;  
   backupTailLog.Devices.AddDevice(urlTailLogBackup, DeviceType.Url);  
   backupTailLog.SqlBackup(server);  
  
   // Restore a database and move files  
   string newDataFilePath = server.MasterDBLogPath + @"\" + dbName + DateTime.Now.ToString("s").Replace(":", "-") + ".mdf";  
   string newLogFilePath = server.MasterDBLogPath + @"\" + dbName + DateTime.Now.ToString("s").Replace(":", "-") + ".ldf";  
  
   Restore restore = new Restore();  
   restore.CredentialName = credentialName;  
   restore.Database = dbName;  
   restore.ReplaceDatabase = true;  
   restore.NoRecovery = true;  
   restore.Devices.AddDevice(urlBackupData, DeviceType.Url);  
   restore.RelocateFiles.Add(new RelocateFile(dbName, newDataFilePath));  
   restore.RelocateFiles.Add(new RelocateFile(dbName + "_Log", newLogFilePath));  
   restore.SqlRestore(server);  
      
   // Restore transaction Log with stop at   
   Restore restoreLog = new Restore();  
   restoreLog.CredentialName = credentialName;  
   restoreLog.Database = dbName;  
   restoreLog.Action = RestoreActionType.Log;  
   restoreLog.Devices.AddDevice(urlBackupData, DeviceType.Url);  
   restoreLog.ToPointInTime = DateTime.Now.ToString();   
   restoreLog.SqlRestore(server);
   ```
  
   ```powershell
   #create variables  
   $backupUrlContainer = "https://mystorageaccount.blob.core.windows.net/mycontainer/"  
   $credentialName = "mycredential"  
   $srvPath = "SQLSERVER:\SQL\COMPUTERNAME\INSTANCENAME"  
   # for default instance, the $srvpath variable would be "SQLSERVER:\SQL\COMPUTERNAME\DEFAULT"  
  
   # Navigate to SQL Server Instance Directory
   CD $srvPath   
  
   #create a unique file name for the full backup  
   $backupdbFile = $backupUrlContainer + "AdventureWorks2012_" + (Get-Date).ToString("s").Replace("-","_").Replace(":", "_").Replace(" ","_").Replace("/", "_") +  ".bak"  
  
   # Full database backup to URL  
   Backup-SqlDatabase -Database AdventureWorks2012 -backupFile $backupdbFile  -SqlCredential $credentialName -CompressionOption On     
  
   #Create a unique file name for the tail log backup  
   $backuplogFile = $backupUrlContainer + "AdventureWorks2012_" + (Get-Date).ToString("s").Replace("-","_").Replace(":", "_").Replace(" ","_").Replace("/", "_") +  ".trn"  
  
   #Backup tail log to URL
   Backup-SqlDatabase -Database AdventureWorks2012 -backupFile $backupFile  -SqlCredential $credentialName  -BackupAction Log -NoRecovery     
  
   # Restore Database and move files
   $newDataFilePath = New-Object Microsoft.SqlServer.Management.Smo.RelocateFile ("AdventureWorks_Data","C:\Program Files\Microsoft SQL Server\myinstance\MSSQL\DATA\AdventureWorks2012.mdf")  
   $newLogFilePath = New-Object Microsoft.SqlServer.Management.Smo.RelocateFile("AdventureWorks_Log","C:\Program Files\Microsoft SQL Server\myinstance\MSSQL\DATA\AdventureWorks2012.ldf")  
  
   Restore-SqlDatabase -Database AdventureWorks2012 -SqlCredential $credentialName -BackupFile $backupdbFile -RelocateFile @($newDataFilePath,$newLogFilePath) -NoRecovery    
  
   # Restore Transaction log with Stop At:  
   Restore-SqlDatabase -Database AdventureWorks2012 -SqlCredential $credentialName -BackupFile $backuplogFile  -ToPointInTime (Get-Date).ToString()
   ```  
  
## <a name="see-also"></a><span data-ttu-id="58c2d-411">另请参阅</span><span class="sxs-lookup"><span data-stu-id="58c2d-411">See Also</span></span>  
 <span data-ttu-id="58c2d-412">[SQL Server 备份到 URL 最佳实践和故障排除](sql-server-backup-to-url-best-practices-and-troubleshooting.md) </span><span class="sxs-lookup"><span data-stu-id="58c2d-412">[SQL Server Backup to URL Best Practices and Troubleshooting](sql-server-backup-to-url-best-practices-and-troubleshooting.md) </span></span>  
 [<span data-ttu-id="58c2d-413">备份和还原系统数据库 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="58c2d-413">Back Up and Restore of System Databases &#40;SQL Server&#41;</span></span>](back-up-and-restore-of-system-databases-sql-server.md)   
