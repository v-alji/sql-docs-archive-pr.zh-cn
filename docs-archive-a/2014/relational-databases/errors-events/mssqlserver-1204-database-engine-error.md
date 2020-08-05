---
title: MSSQLSERVER_1204 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1204 (Database Engine error)
ms.assetid: de6ece78-79de-484d-9224-ca0f7645815f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 7ca03c19552b88e391d2de053193a70531571ece
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581274"
---
# <a name="mssqlserver_1204"></a><span data-ttu-id="08f03-102">MSSQLSERVER_1204</span><span class="sxs-lookup"><span data-stu-id="08f03-102">MSSQLSERVER_1204</span></span>
    
## <a name="details"></a><span data-ttu-id="08f03-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="08f03-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="08f03-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="08f03-104">Product Name</span></span>|<span data-ttu-id="08f03-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="08f03-105">SQL Server</span></span>|  
|<span data-ttu-id="08f03-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="08f03-106">Event ID</span></span>|<span data-ttu-id="08f03-107">1204</span><span class="sxs-lookup"><span data-stu-id="08f03-107">1204</span></span>|  
|<span data-ttu-id="08f03-108">事件源</span><span class="sxs-lookup"><span data-stu-id="08f03-108">Event Source</span></span>|<span data-ttu-id="08f03-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="08f03-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="08f03-110">组件</span><span class="sxs-lookup"><span data-stu-id="08f03-110">Component</span></span>|<span data-ttu-id="08f03-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="08f03-111">SQLEngine</span></span>|  
|<span data-ttu-id="08f03-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="08f03-112">Symbolic Name</span></span>|<span data-ttu-id="08f03-113">LK_OUTOF</span><span class="sxs-lookup"><span data-stu-id="08f03-113">LK_OUTOF</span></span>|  
|<span data-ttu-id="08f03-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="08f03-114">Message Text</span></span>|<span data-ttu-id="08f03-115">SQL Server 数据库引擎的实例此时无法获得 LOCK 资源。</span><span class="sxs-lookup"><span data-stu-id="08f03-115">The instance of the SQL Server Database Engine cannot obtain a LOCK resource at this time.</span></span> <span data-ttu-id="08f03-116">请在活动用户较少时重新运行该语句。</span><span class="sxs-lookup"><span data-stu-id="08f03-116">Rerun your statement when there are fewer active users.</span></span> <span data-ttu-id="08f03-117">请询问数据库管理员，检查此实例的锁定和内存配置，或检查是否有长时间运行的事务。</span><span class="sxs-lookup"><span data-stu-id="08f03-117">Ask the database administrator to check the lock and memory configuration for this instance, or to check for long-running transactions.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="08f03-118">说明</span><span class="sxs-lookup"><span data-stu-id="08f03-118">Explanation</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="08f03-119">无法获得锁资源。</span><span class="sxs-lookup"><span data-stu-id="08f03-119">cannot obtain a lock resource.</span></span> <span data-ttu-id="08f03-120">这可能是由以下任一原因导致的：</span><span class="sxs-lookup"><span data-stu-id="08f03-120">This can be caused by either of the following reasons:</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="08f03-121">无法从操作系统分配更多的内存，因为其他进程正在使用它，或者因为服务器在配置了“最大服务器内存”选项的情况下运行。</span><span class="sxs-lookup"><span data-stu-id="08f03-121">cannot allocate more memory from the operating system, either because other processes are using it, or because the server is operating with the **max server memory** option configured.</span></span>  
  
-   <span data-ttu-id="08f03-122">锁管理器使用的内存不会超过可供 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用的内存的 60%。</span><span class="sxs-lookup"><span data-stu-id="08f03-122">The lock manager will not use more than 60 percent of the memory available to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="08f03-123">用户操作</span><span class="sxs-lookup"><span data-stu-id="08f03-123">User Action</span></span>  
 <span data-ttu-id="08f03-124">如果您怀疑 SQL Server 无法分配足够的内存，请尝试执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="08f03-124">If you suspect that SQL Server cannot allocate sufficient memory, try the following:</span></span>  
  
-   <span data-ttu-id="08f03-125">如果除 SQL Server 外的应用程序正在占用资源，请尝试停止这些应用程序，或者考虑在单独的服务器上运行它们。</span><span class="sxs-lookup"><span data-stu-id="08f03-125">If applications besides SQL Server are consuming resources, try stopping these applications or consider running them on a separate server.</span></span> <span data-ttu-id="08f03-126">这样其他进程将释放并删除内存供 SQL Server 使用。</span><span class="sxs-lookup"><span data-stu-id="08f03-126">This will remove release memory from other processes for SQL Server.</span></span>  
  
-   <span data-ttu-id="08f03-127">如果已配置 max server memory，请增大其设置。</span><span class="sxs-lookup"><span data-stu-id="08f03-127">If you have configured max server memory, increase max server memory setting.</span></span>  
  
 <span data-ttu-id="08f03-128">如果您怀疑锁管理器使用了最大可用内存，请识别持有最多锁的事务并终止它。</span><span class="sxs-lookup"><span data-stu-id="08f03-128">If you suspect that the lock manager has used the maximum amount of available memory identify the transaction that is holding the most locks and terminate it.</span></span> <span data-ttu-id="08f03-129">以下脚本将识别持有最多锁的事务：</span><span class="sxs-lookup"><span data-stu-id="08f03-129">The following script will identify the transaction with the most locks:</span></span>  
  
```  
SELECT request_session_id, COUNT (*) num_locks  
FROM sys.dm_tran_locks  
GROUP BY request_session_id   
ORDER BY count (*) DESC  
```  
  
 <span data-ttu-id="08f03-130">采用最大会话 id，并使用 KILL 命令终止它。</span><span class="sxs-lookup"><span data-stu-id="08f03-130">Take the highest session id, and terminate it using the KILL command.</span></span>  
  
  
