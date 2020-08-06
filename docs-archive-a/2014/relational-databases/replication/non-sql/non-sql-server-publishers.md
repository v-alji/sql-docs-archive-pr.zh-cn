---
title: 非 SQL Server 发布服务器 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- heterogeneous database replication, non-SQL Server Publishers
- non-SQL Server Publishers
- heterogeneous data sources, non-SQL Server Publishers
- Publishers [SQL Server replication], Oracle
ms.assetid: 08a160a6-33be-46b5-bc7b-d53180d8bdf1
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f15f07dbf294d697afd385318f3dbf1447c8e2d8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577546"
---
# <a name="non-sql-server-publishers"></a><span data-ttu-id="94a93-102">非 SQL Server 发布服务器</span><span class="sxs-lookup"><span data-stu-id="94a93-102">Non-SQL Server Publishers</span></span>
  <span data-ttu-id="94a93-103">通过从非源发布数据 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ，您可以在中合并数据 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="94a93-103">Publishing data from non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sources allows you to consolidate data in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="94a93-104">可以订阅从 Oracle 数据库发布的快照或事务数据。</span><span class="sxs-lookup"><span data-stu-id="94a93-104">can subscribe to snapshot or transactional data published from an Oracle database.</span></span> <span data-ttu-id="94a93-105">有关从 Oracle 发布的详细信息，请参阅 [Oracle 发布概述](oracle-publishing-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="94a93-105">For more information about publishing from Oracle, see [Oracle Publishing Overview](oracle-publishing-overview.md).</span></span>  
  
 <span data-ttu-id="94a93-106">不推荐异类复制到非 SQL Server 订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="94a93-106">Heterogeneous replication to non-SQL Server subscribers is deprecated.</span></span> <span data-ttu-id="94a93-107">不推荐使用 Oracle 发布。</span><span class="sxs-lookup"><span data-stu-id="94a93-107">Oracle Publishing is deprecated.</span></span> <span data-ttu-id="94a93-108">若要移动数据，请创建使用变更数据捕获和 [!INCLUDE[ssIS](../../../includes/ssis-md.md)]的解决方案。</span><span class="sxs-lookup"><span data-stu-id="94a93-108">To move data, create solutions using change data capture and [!INCLUDE[ssIS](../../../includes/ssis-md.md)].</span></span>  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
  
 <span data-ttu-id="94a93-109">从非[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 数据库发布适用于下列方案：</span><span class="sxs-lookup"><span data-stu-id="94a93-109">Publishing from non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] databases is ideal for the following scenarios:</span></span>  
  
|<span data-ttu-id="94a93-110">方案</span><span class="sxs-lookup"><span data-stu-id="94a93-110">Scenario</span></span>|<span data-ttu-id="94a93-111">说明</span><span class="sxs-lookup"><span data-stu-id="94a93-111">Description</span></span>|  
|--------------|-----------------|  
|[!INCLUDE[msCoName](../../../includes/msconame-md.md)] <span data-ttu-id="94a93-112">.NET Framework 应用程序部署</span><span class="sxs-lookup"><span data-stu-id="94a93-112">.NET Framework application deployments</span></span>|<span data-ttu-id="94a93-113">使用 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Studio 和 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 开发，同时还能处理从非[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 数据库复制的数据。</span><span class="sxs-lookup"><span data-stu-id="94a93-113">Develop with [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Studio and [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] while operating on data replicated from a non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database.</span></span>|  
|<span data-ttu-id="94a93-114">数据仓库临时服务器</span><span class="sxs-lookup"><span data-stu-id="94a93-114">Data warehousing staging servers</span></span>|<span data-ttu-id="94a93-115">使 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 临时数据库与非[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 数据库保持同步。</span><span class="sxs-lookup"><span data-stu-id="94a93-115">Keep [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] staging databases synchronized with a non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database.</span></span>|  
|<span data-ttu-id="94a93-116">迁移到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="94a93-116">Migration to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]</span></span>|<span data-ttu-id="94a93-117">针对 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 执行实时应用程序测试，同时复制源系统的更改。</span><span class="sxs-lookup"><span data-stu-id="94a93-117">Test your application in real time against [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] while replicating the source system's changes.</span></span> <span data-ttu-id="94a93-118">对迁移满意后，切换到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="94a93-118">Switch to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] when satisfied with the migration.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="94a93-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="94a93-119">See Also</span></span>  
 [<span data-ttu-id="94a93-120">异类数据库复制</span><span class="sxs-lookup"><span data-stu-id="94a93-120">Heterogeneous Database Replication</span></span>](heterogeneous-database-replication.md)  
  
  
