---
title: Analysis Services 配置-数据目录 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: ef732855-b7af-4f40-a619-5573c1c354bb
author: heidisteen
ms.author: heidist
ms.openlocfilehash: e0711c6998e8f931e7d561bb388a0d7809733a44
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586233"
---
# <a name="analysis-services-configuration---data-directories"></a><span data-ttu-id="4dbea-102">Analysis Services 配置 - 数据目录</span><span class="sxs-lookup"><span data-stu-id="4dbea-102">Analysis Services Configuration - Data Directories</span></span>
  <span data-ttu-id="4dbea-103">下表中的默认目录是在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装过程中可由用户配置的目录。</span><span class="sxs-lookup"><span data-stu-id="4dbea-103">The default directories in the following table are user-configurable during [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup.</span></span> <span data-ttu-id="4dbea-104">对这些文件的访问权限授予了本地管理员和在 \<instance> 安装过程中创建并设置的 SQLServerMSASUser $ 安全组的成员。</span><span class="sxs-lookup"><span data-stu-id="4dbea-104">Permission to access these files is granted to local administrators and to members of the SQLServerMSASUser$\<instance> security group that is created and provisioned during Setup.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="4dbea-105">UI 元素列表</span><span class="sxs-lookup"><span data-stu-id="4dbea-105">UI element list</span></span>  
  
|<span data-ttu-id="4dbea-106">说明</span><span class="sxs-lookup"><span data-stu-id="4dbea-106">Description</span></span>|<span data-ttu-id="4dbea-107">默认目录</span><span class="sxs-lookup"><span data-stu-id="4dbea-107">Default directory</span></span>|<span data-ttu-id="4dbea-108">建议</span><span class="sxs-lookup"><span data-stu-id="4dbea-108">Recommendations</span></span>|  
|-----------------|-----------------------|---------------------|  
|<span data-ttu-id="4dbea-109">数据根目录</span><span class="sxs-lookup"><span data-stu-id="4dbea-109">Data root directory</span></span>|<span data-ttu-id="4dbea-110">C:\Program Files\Microsoft SQL Server\MSAS12. \<InstanceID>\OLAP\Data \| 确保 \Program files\Microsoft SQL Server \ 文件夹受到有限权限的保护。</span><span class="sxs-lookup"><span data-stu-id="4dbea-110">C:\Program Files\Microsoft SQL Server\MSAS12.\<InstanceID>\OLAP\Data\|Ensure that the \Program files\Microsoft SQL Server\ folder is protected with limited permissions.</span></span> <span data-ttu-id="4dbea-111">在许多配置中，[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 性能取决于数据目录所在的存储区的性能。</span><span class="sxs-lookup"><span data-stu-id="4dbea-111">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] performance depends, in many configurations, on the performance of the storage on which the data directory is located.</span></span> <span data-ttu-id="4dbea-112">请将此目录放置在附加到系统上的最高性能存储区中。</span><span class="sxs-lookup"><span data-stu-id="4dbea-112">Place this directory on the highest performing storage that is attached to the system.</span></span> <span data-ttu-id="4dbea-113">对于故障转移群集安装，应确保数据目录位于共享磁盘上。</span><span class="sxs-lookup"><span data-stu-id="4dbea-113">For failover cluster installations, ensure that data directories are placed on the shared disk.</span></span>|  
|<span data-ttu-id="4dbea-114">日志文件目录</span><span class="sxs-lookup"><span data-stu-id="4dbea-114">Log file directory</span></span>|<span data-ttu-id="4dbea-115">C:\Program Files\Microsoft SQL Server\MSAS12. \<InstanceID>\OLAP\Log \| 这是 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 日志文件的目录，其中包括 FlightRecorder 日志。</span><span class="sxs-lookup"><span data-stu-id="4dbea-115">C:\Program Files\Microsoft SQL Server\MSAS12.\<InstanceID>\OLAP\Log\|This is the directory for [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] log files, and it includes the FlightRecorder log.</span></span> <span data-ttu-id="4dbea-116">如果要延长网络流量记录器持续时间，请确保该日志目录有足够的空间。</span><span class="sxs-lookup"><span data-stu-id="4dbea-116">If you increase the flight recorder duration, ensure that the log directory has adequate space.</span></span>|  
|<span data-ttu-id="4dbea-117">Temp 目录</span><span class="sxs-lookup"><span data-stu-id="4dbea-117">Temp directory</span></span>|<span data-ttu-id="4dbea-118">C:\Program Files\Microsoft SQL Server\MSAS12. \<InstanceID>\OLAP\Temp \| 将 Temp 目录放置在高性能存储子系统上。</span><span class="sxs-lookup"><span data-stu-id="4dbea-118">C:\Program Files\Microsoft SQL Server\MSAS12.\<InstanceID>\OLAP\Temp\|Place the Temp directory on the high performance storage subsystem.</span></span>|  
|<span data-ttu-id="4dbea-119">备份目录</span><span class="sxs-lookup"><span data-stu-id="4dbea-119">Backup directory</span></span>|<span data-ttu-id="4dbea-120">C:\Program Files\Microsoft SQL Server\MSAS12. \<InstanceID>\OLAP\Backup \| 这是 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 默认备份文件的目录。</span><span class="sxs-lookup"><span data-stu-id="4dbea-120">C:\Program Files\Microsoft SQL Server\MSAS12.\<InstanceID>\OLAP\Backup\|This is the directory for [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] default backup files.</span></span> <span data-ttu-id="4dbea-121">对于 PowerPivot for SharePoint 安装，这还是 PowerPivot 系统服务缓存 PowerPivot 数据文件的位置。</span><span class="sxs-lookup"><span data-stu-id="4dbea-121">For PowerPivot for SharePoint installations, it also where the PowerPivot System Services caches PowerPivot data files.</span></span><br /><br /> <span data-ttu-id="4dbea-122">确保设置合适的权限以防止数据丢失，并确保 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 服务的用户组具有写入备份目录的足够权限。</span><span class="sxs-lookup"><span data-stu-id="4dbea-122">Ensure appropriate permissions are set to prevent data loss, and that the user group for the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] service has adequate permissions to write to the backup directory.</span></span> <span data-ttu-id="4dbea-123">不支持对备份目录使用映射的驱动器。</span><span class="sxs-lookup"><span data-stu-id="4dbea-123">Using a mapped drive for backup directories is not supported.</span></span>|  
  
## <a name="notes"></a><span data-ttu-id="4dbea-124">注释</span><span class="sxs-lookup"><span data-stu-id="4dbea-124">Notes</span></span>  
  
-   <span data-ttu-id="4dbea-125">在 SharePoint 场上部署的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 实例将应用程序文件、数据文件和属性存储于内容数据库和服务应用程序数据库中。</span><span class="sxs-lookup"><span data-stu-id="4dbea-125">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instances that are deployed on a SharePoint farm store application files, data files, and properties in content databases and service application databases.</span></span>  
  
-   <span data-ttu-id="4dbea-126">向现有安装添加功能时，不能更改以前安装的功能的位置，也不能为新功能指定该位置。</span><span class="sxs-lookup"><span data-stu-id="4dbea-126">When you add features to an existing installation, you cannot change the location of a previously installed feature, nor can you specify the location for a new feature.</span></span>  
  
-   <span data-ttu-id="4dbea-127">如果指定非默认的安装目录，请确保安装文件夹对于此 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例是唯一的。</span><span class="sxs-lookup"><span data-stu-id="4dbea-127">If you specify non-default installation directories, ensure that the installation folders are unique to this instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="4dbea-128">此对话框中的任何目录都不应与其他 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例的目录共享。</span><span class="sxs-lookup"><span data-stu-id="4dbea-128">None of the directories in this dialog box should be shared with directories from other instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="4dbea-129">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 实例中的[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 组件也应安装到单独的目录。</span><span class="sxs-lookup"><span data-stu-id="4dbea-129">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] and [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] components within an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] should also be installed to separate directories.</span></span>  
  
-   <span data-ttu-id="4dbea-130">在下列情况下，不能安装程序文件和数据文件：</span><span class="sxs-lookup"><span data-stu-id="4dbea-130">Program files and data files cannot be installed in the following situations:</span></span>  
  
    -   <span data-ttu-id="4dbea-131">在可移动磁盘驱动器上</span><span class="sxs-lookup"><span data-stu-id="4dbea-131">On a removable disk drive</span></span>  
  
    -   <span data-ttu-id="4dbea-132">在使用压缩的文件系统上</span><span class="sxs-lookup"><span data-stu-id="4dbea-132">On a file system that uses compression</span></span>  
  
    -   <span data-ttu-id="4dbea-133">在系统文件所在的目录上</span><span class="sxs-lookup"><span data-stu-id="4dbea-133">To a directory where system files are located</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4dbea-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4dbea-134">See Also</span></span>  
 [<span data-ttu-id="4dbea-135">SQL Server 的默认实例和命名实例的文件位置</span><span class="sxs-lookup"><span data-stu-id="4dbea-135">File Locations for Default and Named Instances of SQL Server</span></span>](../../../2014/sql-server/install/file-locations-for-default-and-named-instances-of-sql-server.md)  
  
  
