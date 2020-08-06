---
title: MSSQLSERVER_41030 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 41030 (Database Engine error)
ms.assetid: c85341ae-0fbf-42ae-9275-4cfe678238f0
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b137b739d4c1641b88983708df62d2e52fd0eab5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691736"
---
# <a name="mssqlserver_41030"></a><span data-ttu-id="27e09-102">MSSQLSERVER_41030</span><span class="sxs-lookup"><span data-stu-id="27e09-102">MSSQLSERVER_41030</span></span>
    
## <a name="details"></a><span data-ttu-id="27e09-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="27e09-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="27e09-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="27e09-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="27e09-105">事件 ID</span><span class="sxs-lookup"><span data-stu-id="27e09-105">Event ID</span></span>|<span data-ttu-id="27e09-106">41030</span><span class="sxs-lookup"><span data-stu-id="27e09-106">41030</span></span>|  
|<span data-ttu-id="27e09-107">事件源</span><span class="sxs-lookup"><span data-stu-id="27e09-107">Event Source</span></span>|<span data-ttu-id="27e09-108">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="27e09-108">MSSQLSERVER</span></span>|  
|<span data-ttu-id="27e09-109">组件</span><span class="sxs-lookup"><span data-stu-id="27e09-109">Component</span></span>|<span data-ttu-id="27e09-110">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="27e09-110">SQLEngine</span></span>|  
|<span data-ttu-id="27e09-111">符号名称</span><span class="sxs-lookup"><span data-stu-id="27e09-111">Symbolic Name</span></span>|<span data-ttu-id="27e09-112">OPEN_CLUSTER_SUB_KEY</span><span class="sxs-lookup"><span data-stu-id="27e09-112">OPEN_CLUSTER_SUB_KEY</span></span>|  
|<span data-ttu-id="27e09-113">消息正文</span><span class="sxs-lookup"><span data-stu-id="27e09-113">Message Text</span></span>|<span data-ttu-id="27e09-114">无法打开 Windows Server 故障转移群集注册表子项“%.\*ls”（错误代码 %d）。</span><span class="sxs-lookup"><span data-stu-id="27e09-114">Failed to open the Windows Server Failover Clustering registry subkey '%.\*ls' (Error code %d).</span></span>  <span data-ttu-id="27e09-115">父键为群集根键。</span><span class="sxs-lookup"><span data-stu-id="27e09-115">The parent key is the cluster root key.</span></span>  <span data-ttu-id="27e09-116">WSFC 服务可能未在运行或是在其当前状态下无法访问，或指定的参数无效。</span><span class="sxs-lookup"><span data-stu-id="27e09-116">The WSFC service may not be running or may not be accessible in its current state, or the specified arguments are invalid.</span></span> <span data-ttu-id="27e09-117">如果已删除对应的可用性组，则会出现此错误。</span><span class="sxs-lookup"><span data-stu-id="27e09-117">If the corresponding availability group has been dropped, this error is expected.</span></span> <span data-ttu-id="27e09-118">有关此错误代码的信息，请参阅 Windows 开发文档中的“系统错误代码”。</span><span class="sxs-lookup"><span data-stu-id="27e09-118">For information about this error code, see "System Error Codes" in the Windows Development documentation.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="27e09-119">说明</span><span class="sxs-lookup"><span data-stu-id="27e09-119">Explanation</span></span>  
 <span data-ttu-id="27e09-120">如果 WSFC 群集损坏，则将删除与 [!INCLUDE[ssHADR](../../includes/sshadr-md.md)]相关的所有注册表项。</span><span class="sxs-lookup"><span data-stu-id="27e09-120">If a WSFC cluster is destroyed, it removes all registry keys related to [!INCLUDE[ssHADR](../../includes/sshadr-md.md)].</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="27e09-121">用户操作</span><span class="sxs-lookup"><span data-stu-id="27e09-121">User Action</span></span>  
 <span data-ttu-id="27e09-122">重新创建 WSFC 群集之后，请在其中 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的实例启用了 AlwaysOn 的每个群集节点上禁用后重新启用 AlwaysOn。</span><span class="sxs-lookup"><span data-stu-id="27e09-122">After re-creating a WSFC cluster, disable and then re-enable AlwaysOn on every cluster node on which an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is enabled for AlwaysOn.</span></span> <span data-ttu-id="27e09-123">您可使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置管理器执行此任务。</span><span class="sxs-lookup"><span data-stu-id="27e09-123">You can use the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager for this task.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27e09-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="27e09-124">See Also</span></span>  
 <span data-ttu-id="27e09-125">[启用和禁用 AlwaysOn 可用性组 &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/enable-and-disable-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="27e09-125">[Enable and Disable AlwaysOn Availability Groups &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/enable-and-disable-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="27e09-126">Windows Server 故障转移群集 (WSFC) 与 SQL Server</span><span class="sxs-lookup"><span data-stu-id="27e09-126">Windows Server Failover Clustering &#40;WSFC&#41; with SQL Server</span></span>](../../sql-server/failover-clusters/windows/windows-server-failover-clustering-wsfc-with-sql-server.md)  
  
  
