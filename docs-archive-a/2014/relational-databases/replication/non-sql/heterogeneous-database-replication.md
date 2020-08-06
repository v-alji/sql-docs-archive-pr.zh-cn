---
title: 异类数据库复制 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- heterogeneous database replication, about heterogeneous database replication
- replication [SQL Server], heterogeneous database replication
- heterogeneous database replication
ms.assetid: 3fd983ad-e206-45db-9054-417c9b5bb815
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d8988a425bc9519d43b8100e4cd34418114edae1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691664"
---
# <a name="heterogeneous-database-replication"></a><span data-ttu-id="fe1ea-102">异类数据库复制</span><span class="sxs-lookup"><span data-stu-id="fe1ea-102">Heterogeneous Database Replication</span></span>
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="fe1ea-103">支持下列异类事务复制和快照复制方案：</span><span class="sxs-lookup"><span data-stu-id="fe1ea-103">supports the following heterogeneous scenarios for transactional and snapshot replication:</span></span>  
  
-   <span data-ttu-id="fe1ea-104">将数据从 Oracle 发布到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="fe1ea-104">Publishing data from Oracle to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="fe1ea-105">将数据从 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 发布到非[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="fe1ea-105">Publishing data from [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Subscribers.</span></span>  
  
 <span data-ttu-id="fe1ea-106">不推荐异类复制到非 SQL Server 订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="fe1ea-106">Heterogeneous replication to non-SQL Server subscribers is deprecated.</span></span> <span data-ttu-id="fe1ea-107">不推荐使用 Oracle 发布。</span><span class="sxs-lookup"><span data-stu-id="fe1ea-107">Oracle Publishing is deprecated.</span></span> <span data-ttu-id="fe1ea-108">若要移动数据，请创建使用变更数据捕获和 [!INCLUDE[ssIS](../../../includes/ssis-md.md)]的解决方案。</span><span class="sxs-lookup"><span data-stu-id="fe1ea-108">To move data, create solutions using change data capture and [!INCLUDE[ssIS](../../../includes/ssis-md.md)].</span></span>  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
  
## <a name="publishing-data-from-oracle"></a><span data-ttu-id="fe1ea-109">从 Oracle 发布数据</span><span class="sxs-lookup"><span data-stu-id="fe1ea-109">Publishing Data from Oracle</span></span>  
 <span data-ttu-id="fe1ea-110">您可以使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 从 Oracle 发布数据，其大多数功能和简单易用性与 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 快照复制和事务复制相同。</span><span class="sxs-lookup"><span data-stu-id="fe1ea-110">You can use [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to publish data from Oracle with most of the same features and ease-of-use as [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] snapshot and transactional replication.</span></span> <span data-ttu-id="fe1ea-111">从 Oracle 发布数据非常适合于下列情形：</span><span class="sxs-lookup"><span data-stu-id="fe1ea-111">Publishing data from Oracle is ideal for the following scenarios:</span></span>  
  
|<span data-ttu-id="fe1ea-112">方案</span><span class="sxs-lookup"><span data-stu-id="fe1ea-112">Scenario</span></span>|<span data-ttu-id="fe1ea-113">说明</span><span class="sxs-lookup"><span data-stu-id="fe1ea-113">Description</span></span>|  
|--------------|-----------------|  
|[!INCLUDE[msCoName](../../../includes/msconame-md.md)] <span data-ttu-id="fe1ea-114">.NET Framework 应用程序部署</span><span class="sxs-lookup"><span data-stu-id="fe1ea-114">.NET Framework application deployments</span></span>|<span data-ttu-id="fe1ea-115">使用 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Studio 和 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 开发，同时还能处理从非[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 数据库复制的数据。</span><span class="sxs-lookup"><span data-stu-id="fe1ea-115">Develop with [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Studio and [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] while operating on data replicated from a non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database.</span></span>|  
|<span data-ttu-id="fe1ea-116">数据仓库临时服务器</span><span class="sxs-lookup"><span data-stu-id="fe1ea-116">Data warehousing staging servers</span></span>|<span data-ttu-id="fe1ea-117">使 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 临时数据库与非[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 数据库保持同步。</span><span class="sxs-lookup"><span data-stu-id="fe1ea-117">Keep [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] staging databases synchronized with a non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database.</span></span>|  
|<span data-ttu-id="fe1ea-118">迁移到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe1ea-118">Migration to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]</span></span>|<span data-ttu-id="fe1ea-119">针对 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 执行实时应用程序测试，同时复制源系统的更改。</span><span class="sxs-lookup"><span data-stu-id="fe1ea-119">Test your application in real time against [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] while replicating the source system's changes.</span></span> <span data-ttu-id="fe1ea-120">对迁移满意后，切换到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="fe1ea-120">Switch to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] when satisfied with the migration.</span></span>|  
  
 <span data-ttu-id="fe1ea-121">有关详细信息，请参阅 [Oracle 发布概述](oracle-publishing-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="fe1ea-121">For more information, see [Oracle Publishing Overview](oracle-publishing-overview.md).</span></span>  
  
## <a name="publishing-data-to-non-sql-server-subscribers"></a><span data-ttu-id="fe1ea-122">将数据发布到非 SQL Server 订阅服务器</span><span class="sxs-lookup"><span data-stu-id="fe1ea-122">Publishing Data to Non-SQL Server Subscribers</span></span>  
 <span data-ttu-id="fe1ea-123">支持将下列非[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 数据库作为快照和事务发布的订阅服务器：</span><span class="sxs-lookup"><span data-stu-id="fe1ea-123">The following non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] databases are supported as Subscribers to snapshot and transactional publications:</span></span>  
  
-   <span data-ttu-id="fe1ea-124">用于 Oracle 所支持的所有平台的 Oracle。</span><span class="sxs-lookup"><span data-stu-id="fe1ea-124">Oracle for all platforms that Oracle supports.</span></span>  
  
-   <span data-ttu-id="fe1ea-125">用于 AS400、MVS、Unix、Linux 和 Windows 的 IBM DB2。</span><span class="sxs-lookup"><span data-stu-id="fe1ea-125">IBM DB2 for AS400, MVS, Unix, Linux, and Windows.</span></span>  
  
 <span data-ttu-id="fe1ea-126">有关详细信息，请参阅 [Non-SQL Server Subscribers](non-sql-server-subscribers.md)。</span><span class="sxs-lookup"><span data-stu-id="fe1ea-126">For more information, see [Non-SQL Server Subscribers](non-sql-server-subscribers.md).</span></span>  
  
  
