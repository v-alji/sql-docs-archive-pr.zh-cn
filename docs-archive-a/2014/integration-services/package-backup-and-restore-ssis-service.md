---
title: 包备份和还原 (SSIS 服务) |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SSIS packages, backup and restore
- backing up packages [Integration Services]
- packages [Integration Services], backup and restore
- SQL Server Integration Services packages, backup and restore
- restoring packages [Integration Services]
- Integration Services packages, backup and restore
ms.assetid: c67d3b83-a6c8-40de-920f-9236de4ac87f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c4cd6f3856b69485c01e4b38d89e2f7e2ec56f74
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590284"
---
# <a name="package-backup-and-restore-ssis-service"></a><span data-ttu-id="d0c96-102">包备份和还原（SSIS 服务）</span><span class="sxs-lookup"><span data-stu-id="d0c96-102">Package Backup and Restore (SSIS Service)</span></span>
    
> [!IMPORTANT]  
>  <span data-ttu-id="d0c96-103">本主题论述 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服务，该服务是用于管理 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 包的一种 Windows 服务。</span><span class="sxs-lookup"><span data-stu-id="d0c96-103">This topic discusses the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service, a Windows service for managing [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages.</span></span> [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] <span data-ttu-id="d0c96-104">支持该服务以便与 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]的早期版本向后兼容。</span><span class="sxs-lookup"><span data-stu-id="d0c96-104">supports the service for backward compatibility with earlier releases of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].</span></span> <span data-ttu-id="d0c96-105">从 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]开始，您可以在 Integration Services 服务器上管理诸如包之类的对象。</span><span class="sxs-lookup"><span data-stu-id="d0c96-105">Starting in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], you can manage objects such as packages on the Integration Services server.</span></span>  
  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="d0c96-106">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 包可以保存到文件系统或 msdb（一种 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 系统数据库）中。</span><span class="sxs-lookup"><span data-stu-id="d0c96-106">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages can be saved to the file system or msdb, a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] system database.</span></span> <span data-ttu-id="d0c96-107">可以使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 备份和还原功能来备份和还原保存到 msdb 中的包。</span><span class="sxs-lookup"><span data-stu-id="d0c96-107">Packages saved to msdb can be backed up and restored using [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] backup and restore features.</span></span>  
  
 <span data-ttu-id="d0c96-108">有关备份和还原 msdb 数据库的详细信息，请单击下列某个主题：</span><span class="sxs-lookup"><span data-stu-id="d0c96-108">For more information about backing up and restoring the msdb database, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="d0c96-109">SQL Server 数据库的备份和还原</span><span class="sxs-lookup"><span data-stu-id="d0c96-109">Back Up and Restore of SQL Server Databases</span></span>](../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md)  
  
-   [<span data-ttu-id="d0c96-110">备份和还原系统数据库 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="d0c96-110">Back Up and Restore of System Databases &#40;SQL Server&#41;</span></span>](../relational-databases/backup-restore/back-up-and-restore-of-system-databases-sql-server.md)  
  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="d0c96-111">包括可用于管理包的 **dtutil** 命令提示实用工具 (dtutil.exec)。</span><span class="sxs-lookup"><span data-stu-id="d0c96-111">includes the **dtutil** command-prompt utility (dtutil.exec), which you can use to manage packages.</span></span> <span data-ttu-id="d0c96-112">有关详细信息，请参阅 [dtutil Utility](dtutil-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="d0c96-112">For more information, see [dtutil Utility](dtutil-utility.md).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="d0c96-113">配置文件</span><span class="sxs-lookup"><span data-stu-id="d0c96-113">Configuration Files</span></span>  
 <span data-ttu-id="d0c96-114">包所包括的所有配置文件都存储在文件系统中。</span><span class="sxs-lookup"><span data-stu-id="d0c96-114">Any configuration files that the packages include are stored in the file system.</span></span> <span data-ttu-id="d0c96-115">在备份 msdb 数据库时并不会备份这些文件；因此，你应该确保定期备份配置文件，以便保护保存到 msdb 中的包。</span><span class="sxs-lookup"><span data-stu-id="d0c96-115">These files are not backed up when you back up the msdb database; therefore, you should make sure that the configuration files are backed up regularly as part of your plan for securing packages saved to msdb.</span></span> <span data-ttu-id="d0c96-116">若要将配置包括在 msdb 数据库的备份中，应该考虑使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 配置类型，而不使用基于文件的配置。</span><span class="sxs-lookup"><span data-stu-id="d0c96-116">To include configurations in the backup of the msdb database, you should consider using the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] configuration type instead of file-based configurations.</span></span>  
  
## <a name="packages-stored-in-the-file-system"></a><span data-ttu-id="d0c96-117">在文件系统中存储的包</span><span class="sxs-lookup"><span data-stu-id="d0c96-117">Packages Stored in the File System</span></span>  
 <span data-ttu-id="d0c96-118">备份服务器文件系统的计划中应当包括对保存到文件系统的包的备份。</span><span class="sxs-lookup"><span data-stu-id="d0c96-118">The backup of packages that are saved to the file system should be included in the plan for backing up the file system of the server.</span></span> <span data-ttu-id="d0c96-119">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服务配置文件的默认名称为 MsDtsSrvr.ini.xml，它列出服务器上该服务所监视的文件夹。</span><span class="sxs-lookup"><span data-stu-id="d0c96-119">The [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service configuration file, which has the default name MsDtsSrvr.ini.xml, lists the folders on the server that the service monitors.</span></span> <span data-ttu-id="d0c96-120">您应该确保备份这些文件夹。</span><span class="sxs-lookup"><span data-stu-id="d0c96-120">You should make sure these folders are backed up.</span></span> <span data-ttu-id="d0c96-121">另外，包可以存储在服务器上的其他文件夹中，因此应该确保在备份中包括这些文件夹。</span><span class="sxs-lookup"><span data-stu-id="d0c96-121">Additionally, packages may be stored in other folders on the server and you should make sure to include these folders in the backup.</span></span>  
  
  
