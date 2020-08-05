---
title: 远程 Blob 存储 (RBS) ，AlwaysOn 可用性组 (SQL Server) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
ms.assetid: 01a70258-d4fd-40bc-bc44-c490b5d6c420
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f12a11162d286731b2b510a9051183e6c3025b2a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579801"
---
# <a name="remote-blob-store-rbs-and-alwayson-availability-groups-sql-server"></a><span data-ttu-id="d01f7-102">远程 Blob 存储区 (RBS) 和 AlwaysOn 可用性组 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="d01f7-102">Remote Blob Store (RBS) and AlwaysOn Availability Groups (SQL Server)</span></span>
  [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]<span data-ttu-id="d01f7-103">可为 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [远程 Blob 存储 (RBS](../../../relational-databases/blob/remote-blob-store-rbs-sql-server.md)提供高可用性和灾难恢复解决方案， (blob) ) blob 对象。</span><span class="sxs-lookup"><span data-stu-id="d01f7-103">can provide a high-availability and disaster recovery solution for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)][Remote Blob Store (RBS)](../../../relational-databases/blob/remote-blob-store-rbs-sql-server.md) BLOB objects (blobs).</span></span> [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] <span data-ttu-id="d01f7-104">通过将存储到可用性数据库中的所有 RBS 元数据和架构复制到辅助副本的方式来保护它们。</span><span class="sxs-lookup"><span data-stu-id="d01f7-104">protects any RBS metadata and schemas stored in an availability database by replicating them to the secondary replicas.</span></span> <span data-ttu-id="d01f7-105">这是 SharePoint 内容数据库。</span><span class="sxs-lookup"><span data-stu-id="d01f7-105">This is the SharePoint Content Database.</span></span> <span data-ttu-id="d01f7-106">一般来说， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 不通过 Blob 单独存储此 RBS 元数据。</span><span class="sxs-lookup"><span data-stu-id="d01f7-106">Generally speaking, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] stores this RBS metadata independently from the blob.</span></span>  
  
 <span data-ttu-id="d01f7-107">RBD BLOB 数据保护取决于 BLOB 存储位置，如下所示：</span><span class="sxs-lookup"><span data-stu-id="d01f7-107">The protection for RBD BLOB data depends on the BLOB Store Location, as follows:</span></span>  
  
|<span data-ttu-id="d01f7-108">BLOB 存储位置</span><span class="sxs-lookup"><span data-stu-id="d01f7-108">BLOB Store Location</span></span>|<span data-ttu-id="d01f7-109">可用性组是否能够保护此 BLOB 数据？</span><span class="sxs-lookup"><span data-stu-id="d01f7-109">Can Availability Groups Protect This BLOB Data?</span></span>|  
|-------------------------|-----------------------------------------------------|  
|<span data-ttu-id="d01f7-110">包含 RBS 元数据的同一数据库（使用 RBS 远程 FILESTREAM 提供程序存储）</span><span class="sxs-lookup"><span data-stu-id="d01f7-110">The same database that contains the RBS metadata  (stored using a RBS remote FILESTREAM provider)</span></span>|<span data-ttu-id="d01f7-111">是</span><span class="sxs-lookup"><span data-stu-id="d01f7-111">Yes</span></span>|  
|<span data-ttu-id="d01f7-112">同一 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例中的另一个数据库（使用 RBS 远程 FILESTREAM 提供程序存储）</span><span class="sxs-lookup"><span data-stu-id="d01f7-112">Another database in the same instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (stored using a RBS remote FILESTREAM provider)</span></span>|<span data-ttu-id="d01f7-113">是</span><span class="sxs-lookup"><span data-stu-id="d01f7-113">Yes</span></span><br /><br /> <span data-ttu-id="d01f7-114">建议您将此数据库放置在包含 RBS 元数据的数据库所在的同一可用性组中。</span><span class="sxs-lookup"><span data-stu-id="d01f7-114">We recommend that you put this database in the same availability group as the database that contains the RBS metadata.</span></span>|  
|<span data-ttu-id="d01f7-115">不同 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例中的另一个数据库（使用 RBS 远程 FILESTREAM 提供程序存储）</span><span class="sxs-lookup"><span data-stu-id="d01f7-115">Another database in a different instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (stored using a RBS remote FILESTREAM provider)</span></span>|<span data-ttu-id="d01f7-116">是</span><span class="sxs-lookup"><span data-stu-id="d01f7-116">Yes</span></span><br /><br /> <span data-ttu-id="d01f7-117">此数据库必须位于单独的可用性组中。</span><span class="sxs-lookup"><span data-stu-id="d01f7-117">This database must be in a separate availability group.</span></span>|  
|<span data-ttu-id="d01f7-118">第三方 BLOB 存储</span><span class="sxs-lookup"><span data-stu-id="d01f7-118">A third-party BLOB store</span></span>|<span data-ttu-id="d01f7-119">否</span><span class="sxs-lookup"><span data-stu-id="d01f7-119">No</span></span><br /><br /> <span data-ttu-id="d01f7-120">若要保护此 BLOB 数据，请使用 BLOB 存储提供程序的高可用性机制。</span><span class="sxs-lookup"><span data-stu-id="d01f7-120">To protect this BLOB data, use the high-availability mechanisms of the BLOB store provider.</span></span>|  
  
##  <a name="limitations"></a><a name="Limitations"></a> <span data-ttu-id="d01f7-121">限制</span><span class="sxs-lookup"><span data-stu-id="d01f7-121">Limitations</span></span>  
  
-   <span data-ttu-id="d01f7-122">RBS maintainer 需要将目标设定在主副本上。</span><span class="sxs-lookup"><span data-stu-id="d01f7-122">RBS maintainers need to be targeted on the primary replica.</span></span>  
  
##  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="d01f7-123">建议</span><span class="sxs-lookup"><span data-stu-id="d01f7-123">Recommendations</span></span>  
  
-   <span data-ttu-id="d01f7-124">使用可用性组侦听器。</span><span class="sxs-lookup"><span data-stu-id="d01f7-124">Use an availability group listener.</span></span> <span data-ttu-id="d01f7-125">有关详细信息，请参阅 [可用性组侦听程序、客户端连接和应用程序故障转移 (SQL Server)](../../listeners-client-connectivity-application-failover.md)概念。</span><span class="sxs-lookup"><span data-stu-id="d01f7-125">For more information, see [Availability Group Listeners, Client Connectivity, and Application Failover &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md).</span></span>  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="d01f7-126">相关内容</span><span class="sxs-lookup"><span data-stu-id="d01f7-126">Related Content</span></span>  
  
-   <span data-ttu-id="d01f7-127">[维护远程 BLOB 存储](https://msdn.microsoft.com/library/gg316773\(SQL.105\).aspx) （位于 [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] 联机丛书）</span><span class="sxs-lookup"><span data-stu-id="d01f7-127">[Maintaining Remote BLOB Store](https://msdn.microsoft.com/library/gg316773\(SQL.105\).aspx) (in [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] Books Online)</span></span>  
  
-   <span data-ttu-id="d01f7-128">[运行 RBS Maintainer](https://blogs.msdn.com/b/sqlrbs/archive/2010/03/19/running-rbs-maintainer.aspx) （博客）</span><span class="sxs-lookup"><span data-stu-id="d01f7-128">[Running RBS Maintainer](https://blogs.msdn.com/b/sqlrbs/archive/2010/03/19/running-rbs-maintainer.aspx) (blog)</span></span>  
  
-   <span data-ttu-id="d01f7-129">[使用 FILESTREAM 提供程序配置 BLOB 存储 (RBS) (SharePoint 2010)](https://blogs.msdn.com/b/mvpawardprogram/archive/2012/04/02/configure-remote-blob-storage-rbs-with-the-filestream-provider-sharepoint-2010.aspx) （博客）</span><span class="sxs-lookup"><span data-stu-id="d01f7-129">[Configure Remote BLOB Storage (RBS) with the FILESTREAM provider (SharePoint 2010)](https://blogs.msdn.com/b/mvpawardprogram/archive/2012/04/02/configure-remote-blob-storage-rbs-with-the-filestream-provider-sharepoint-2010.aspx) (blog)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d01f7-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d01f7-130">See Also</span></span>  
 <span data-ttu-id="d01f7-131">[AlwaysOn 客户端连接 &#40;SQL Server&#41;](always-on-client-connectivity-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="d01f7-131">[AlwaysOn Client Connectivity &#40;SQL Server&#41;](always-on-client-connectivity-sql-server.md) </span></span>  
 [<span data-ttu-id="d01f7-132">远程 Blob 存储区 (RBS) (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="d01f7-132">Remote Blob Store &#40;RBS&#41; &#40;SQL Server&#41;</span></span>](../../../relational-databases/blob/remote-blob-store-rbs-sql-server.md)  
  
  
