---
title: FILESTREAM 和 FileTable 与 AlwaysOn 可用性组 (SQL Server) |Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- FileTables [SQL Server], Availability Groups
- FILESTREAM [SQL Server], Availability Groups
- Availability Groups [SQL Server], interoperability
ms.assetid: fdceda9a-a9db-4d1d-8745-345992164a98
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e7de7b4d66890bb5f1fe49799844f666de81f4db
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585975"
---
# <a name="filestream-and-filetable-with-alwayson-availability-groups-sql-server"></a><span data-ttu-id="a1ca8-102">FILESTREAM 和 FileTable 与 AlwaysOn 可用性组 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="a1ca8-102">FILESTREAM and FileTable with AlwaysOn Availability Groups (SQL Server)</span></span>
  <span data-ttu-id="a1ca8-103">本主题包含将 FILESTREAM 和 FileTable 功能与 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 中的 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]一起使用有关的信息。</span><span class="sxs-lookup"><span data-stu-id="a1ca8-103">This topic contains information about the using the FILESTREAM and FileTable features with [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span>  
  
 <span data-ttu-id="a1ca8-104">支持所有 FILESTREAM 功能。</span><span class="sxs-lookup"><span data-stu-id="a1ca8-104">All FILESTREAM functionality is supported.</span></span> <span data-ttu-id="a1ca8-105">故障转移后，FILESTREAM 数据在可读辅助副本和新的主副本上均可访问。</span><span class="sxs-lookup"><span data-stu-id="a1ca8-105">After a failover, FILESTREAM data is accessible on both readable secondary replicas and on the new primary.</span></span>  
  
 <span data-ttu-id="a1ca8-106">支持部分 FileTable 功能。</span><span class="sxs-lookup"><span data-stu-id="a1ca8-106">FileTable functionality is partially supported.</span></span> <span data-ttu-id="a1ca8-107">故障转移后，FileTable 数据在主副本上是可访问的，但是在可读辅助副本上不可访问。</span><span class="sxs-lookup"><span data-stu-id="a1ca8-107">After a failover, FileTable data is accessible on the primary replica, but FileTable data is not accessible on readable secondary replicas.</span></span>  
  
 <span data-ttu-id="a1ca8-108">**本主题内容：**</span><span class="sxs-lookup"><span data-stu-id="a1ca8-108">**In this Topic:**</span></span>  
  
-   [<span data-ttu-id="a1ca8-109">先决条件</span><span class="sxs-lookup"><span data-stu-id="a1ca8-109">Prerequisites</span></span>](#Prerequisites)  
  
-   [<span data-ttu-id="a1ca8-110">为 FILESTREAM 和 FileTable 访问使用虚拟网络名称 (VNN)</span><span class="sxs-lookup"><span data-stu-id="a1ca8-110">Using Virtual Network Names (VNNs) for FILESTREAM and FileTable Access</span></span>](#vnn)  
  
-   [<span data-ttu-id="a1ca8-111">相关任务</span><span class="sxs-lookup"><span data-stu-id="a1ca8-111">Related Tasks</span></span>](#RelatedTasks)  
  
-   [<span data-ttu-id="a1ca8-112">相关内容</span><span class="sxs-lookup"><span data-stu-id="a1ca8-112">Related Content</span></span>](#RelatedContent)  
  
##  <a name="prerequisites"></a><a name="Prerequisites"></a><span data-ttu-id="a1ca8-113">先决条件</span><span class="sxs-lookup"><span data-stu-id="a1ca8-113">Prerequisites</span></span>  
  
-   <span data-ttu-id="a1ca8-114">在将使用 FILESTREAM 的数据库（具有或不具有 FileTable）添加到某一可用性组之前，请确保在承载该可用性组的可用性副本的每个服务器实例上都启用 FILESTREAM。</span><span class="sxs-lookup"><span data-stu-id="a1ca8-114">Before adding a database that uses FILESTREAM, with or without FileTable, to an availability group, ensure that FILESTREAM is enabled on every server instance that hosts an availability replica for the availability group.</span></span> <span data-ttu-id="a1ca8-115">有关详细信息，请参阅 [Enable and Configure FILESTREAM](../../../relational-databases/blob/enable-and-configure-filestream.md)。</span><span class="sxs-lookup"><span data-stu-id="a1ca8-115">For more information, see [Enable and Configure FILESTREAM](../../../relational-databases/blob/enable-and-configure-filestream.md).</span></span>  
  
##  <a name="using-virtual-network-names-vnns-for-filestream-and-filetable-access"></a><a name="vnn"></a><span data-ttu-id="a1ca8-116">为 FILESTREAM 和 FileTable 访问使用虚拟网络名称 (Vnn) </span><span class="sxs-lookup"><span data-stu-id="a1ca8-116">Using Virtual Network Names (VNNs) for FILESTREAM and FileTable Access</span></span>  
 <span data-ttu-id="a1ca8-117">当您在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]实例上启用 FILESTREAM 时，将创建实例级别共享以便提供对 FILESTREAM 数据的访问。</span><span class="sxs-lookup"><span data-stu-id="a1ca8-117">When you enable FILESTREAM on an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], an instance-level share is created to provide access to the FILESTREAM data.</span></span> <span data-ttu-id="a1ca8-118">可通过按以下格式使用计算机名称来访问此共享：</span><span class="sxs-lookup"><span data-stu-id="a1ca8-118">You access this share by using the computer name in the following format:</span></span>  
  
 `\\<computer_name>\<filestream_share_name>`  
  
 <span data-ttu-id="a1ca8-119">但在 AlwaysOn 可用性组中，通过使用虚拟网络名称 (VNN) 虚拟化计算机的名称。</span><span class="sxs-lookup"><span data-stu-id="a1ca8-119">In an AlwaysOn availability group, however, the name of the computer is virtualized by using a Virtual Network Name, or VNN.</span></span> <span data-ttu-id="a1ca8-120">在该计算机是某一可用性组中的主副本，并且该可用性组中的数据库包含 FILESTREAM 数据时，还创建 VNN 范围的共享以便提供对 FILESTREAM 数据的访问。</span><span class="sxs-lookup"><span data-stu-id="a1ca8-120">When the computer is the primary replica in an availability group, and databases in the availability group contain FILESTREAM data, then a VNN-scoped share is also created to provide access to the FILESTREAM data.</span></span> <span data-ttu-id="a1ca8-121">这并不影响对 FILESTREAM 数据的 Transact-SQL 访问。</span><span class="sxs-lookup"><span data-stu-id="a1ca8-121">This does not affect Transact-SQL access to FILESTREAM data.</span></span> <span data-ttu-id="a1ca8-122">但是，使用文件系统 API 的应用程序必须使用 VNN 范围的共享，它具有以下格式的路径：</span><span class="sxs-lookup"><span data-stu-id="a1ca8-122">However applications that use file system APIs have to use the VNN-scoped share, which has a path in the following format:</span></span>  
  
 `\\<VNN>\<filestream_share_name>`  
  
 <span data-ttu-id="a1ca8-123">在发生以下事件之一时将创建 VNN 范围的共享。</span><span class="sxs-lookup"><span data-stu-id="a1ca8-123">This VNN-scoped share is created when one of the following events occurs.</span></span>  
  
-   <span data-ttu-id="a1ca8-124">您将包含 FILESTREAM 数据的数据库添加到主副本上的 AlwaysOn 可用性组。</span><span class="sxs-lookup"><span data-stu-id="a1ca8-124">You add a database that contains FILESTREAM data to an AlwaysOn availability group on the primary replica.</span></span> <span data-ttu-id="a1ca8-125">在此情况下，共享 `\\<computer_name>\<filestream_share_name>` 已存在。</span><span class="sxs-lookup"><span data-stu-id="a1ca8-125">In this case, the share `\\<computer_name>\<filestream_share_name>` already exists.</span></span> <span data-ttu-id="a1ca8-126">创建共享 `\\<VNN>\<filestream_share_name>` 。</span><span class="sxs-lookup"><span data-stu-id="a1ca8-126">The share `\\<VNN>\<filestream_share_name>` is created.</span></span>  
  
-   <span data-ttu-id="a1ca8-127">您对具有可用性组的主副本上的文件 i/o 流访问启用 FILESTREAM。</span><span class="sxs-lookup"><span data-stu-id="a1ca8-127">You enable FILESTREAM for file i/o streaming access on a primary replica that has availability groups.</span></span> <span data-ttu-id="a1ca8-128">创建以下共享：</span><span class="sxs-lookup"><span data-stu-id="a1ca8-128">The following shares are created:</span></span>  
  
    1.  `\\<computer_name>\<filestream_share_name>`  
  
    2.  <span data-ttu-id="a1ca8-129">`\\<VNN1>\<filestream_share_name>` 。</span><span class="sxs-lookup"><span data-stu-id="a1ca8-129">`\\<VNN1>\<filestream_share_name>` for availability group 1.</span></span>  
  
    3.  <span data-ttu-id="a1ca8-130">`\\<VNN2>\<filestream_share_name>` 。</span><span class="sxs-lookup"><span data-stu-id="a1ca8-130">`\\<VNN2>\<filestream_share_name>` for availability group 2.</span></span>  
  
 <span data-ttu-id="a1ca8-131">这些 VNN 范围的共享也传播到所有辅助副本。</span><span class="sxs-lookup"><span data-stu-id="a1ca8-131">These VNN-scoped shares are also propagated to all secondary replicas.</span></span>  
  
 <span data-ttu-id="a1ca8-132">在包含 FILESTREAM 或 FileTable 数据的数据库属于某一 AlwaysOn 可用性组时：</span><span class="sxs-lookup"><span data-stu-id="a1ca8-132">When the database that contains FILESTREAM or FileTable data belongs to an AlwaysOn availability group:</span></span>  
  
-   <span data-ttu-id="a1ca8-133">FILESTREAM 和 FileTable 函数接受或返回虚拟网络名称 (VNN)，而非计算机名称。</span><span class="sxs-lookup"><span data-stu-id="a1ca8-133">The FILESTREAM and FileTable functions accept or return virtual network names (VNNs) instead of computer names.</span></span> <span data-ttu-id="a1ca8-134">有关这些函数的详细信息，请参阅 [Filestream 和 FileTable 函数 (Transact-SQL)](/sql/relational-databases/system-functions/filestream-and-filetable-functions-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="a1ca8-134">For more information about these functions, see [Filestream and FileTable Functions &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/filestream-and-filetable-functions-transact-sql).</span></span>  
  
-   <span data-ttu-id="a1ca8-135">通过文件系统 API 对 FILESTREAM 或 FileTable 数据进行的所有访问都应该使用 VNN，而非计算机名称。</span><span class="sxs-lookup"><span data-stu-id="a1ca8-135">All access to FILESTREAM or FileTable data through the file system APIs should use VNNs instead of computer names.</span></span>  
  
 <span data-ttu-id="a1ca8-136">在该数据库是某一可用性组的一部分时，如果您的应用程序尝试使用格式为 `\\<computer_name>\<filestream_share_name>` 的计算机名称访问该共享，将会引发错误。</span><span class="sxs-lookup"><span data-stu-id="a1ca8-136">If your application tries to access the share by using the computer name in the format `\\<computer_name>\<filestream_share_name>` when the database is part of an availability group, then an error is raised.</span></span>  
  
 <span data-ttu-id="a1ca8-137">在该数据库不是某一可用性组的一部分时，如果您的应用程序尝试使用 VNN 范围的路径访问该共享，则该请求可能会成功。</span><span class="sxs-lookup"><span data-stu-id="a1ca8-137">If your application tries to access the share by using a VNN-scoped path when the database is not part of an availability group, then the request may succeed.</span></span> <span data-ttu-id="a1ca8-138">在此情况下，虚拟网络名称将解析为计算机名称。</span><span class="sxs-lookup"><span data-stu-id="a1ca8-138">In this case, the virtual network name is resolved to the computer name.</span></span> <span data-ttu-id="a1ca8-139">但是，强烈不推荐这一用法，因为如果删除该可用性组，该 VNN 范围的路径将会停止。</span><span class="sxs-lookup"><span data-stu-id="a1ca8-139">However this usage is strongly discouraged, since the VNN-scoped path will stop working if the availability group is dropped.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="a1ca8-140">相关任务</span><span class="sxs-lookup"><span data-stu-id="a1ca8-140">Related Tasks</span></span>  
  
-   [<span data-ttu-id="a1ca8-141">启用和配置 FILESTREAM</span><span class="sxs-lookup"><span data-stu-id="a1ca8-141">Enable and Configure FILESTREAM</span></span>](../../../relational-databases/blob/enable-and-configure-filestream.md)  
  
-   [<span data-ttu-id="a1ca8-142">启用 FileTable 的先决条件</span><span class="sxs-lookup"><span data-stu-id="a1ca8-142">Enable the Prerequisites for FileTable</span></span>](../../../relational-databases/blob/enable-the-prerequisites-for-filetable.md)  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="a1ca8-143">相关内容</span><span class="sxs-lookup"><span data-stu-id="a1ca8-143">Related Content</span></span>  
 <span data-ttu-id="a1ca8-144">无。</span><span class="sxs-lookup"><span data-stu-id="a1ca8-144">None.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1ca8-145">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a1ca8-145">See Also</span></span>  
 [<span data-ttu-id="a1ca8-146">AlwaysOn 可用性组 &#40;SQL Server 概述&#41;</span><span class="sxs-lookup"><span data-stu-id="a1ca8-146">Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](overview-of-always-on-availability-groups-sql-server.md)  
  
  
