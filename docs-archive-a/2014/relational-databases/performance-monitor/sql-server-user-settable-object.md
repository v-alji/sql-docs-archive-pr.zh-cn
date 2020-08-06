---
title: SQL Server - User Settable 对象 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- User Settable object
- SQLServer:User Settable
ms.assetid: 633de3ef-533c-4f0c-9c7b-c105129d8e94
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 7243ab4767c8de93dccf4556f136a94b47554d3d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687792"
---
# <a name="sql-server-user-settable-object"></a><span data-ttu-id="9be46-102">SQL Server User Settable 对象</span><span class="sxs-lookup"><span data-stu-id="9be46-102">SQL Server, User Settable Object</span></span>
  <span data-ttu-id="9be46-103">通过 Microsoft **中的** User Settable [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 对象可以创建自定义计数器实例。</span><span class="sxs-lookup"><span data-stu-id="9be46-103">The **User Settable** object in Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] allows you to create custom counter instances.</span></span> <span data-ttu-id="9be46-104">自定义计数器实例用于监视服务器上现有计数器没有监视到的方面，例如您的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库唯一具有的组件（例如，记录的客户定单数或产品目录）。</span><span class="sxs-lookup"><span data-stu-id="9be46-104">Use custom counter instances to monitor aspects of the server not monitored by existing counters, such as components unique to your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database (for example, the number of customer orders logged or the product inventory).</span></span>  
  
 <span data-ttu-id="9be46-105">“User Settable”对象包含 10 个查询计数器实例：“用户计数器 1”到“用户计数器 10” 。</span><span class="sxs-lookup"><span data-stu-id="9be46-105">The **User Settable** object contains 10 instances of the query counter: **User counter 1** through **User counter 10**.</span></span> <span data-ttu-id="9be46-106">这些计数器映射到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 存储过程 **sp_user_counter1** 到 **sp_user_counter10**。</span><span class="sxs-lookup"><span data-stu-id="9be46-106">These counters map to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stored procedures **sp_user_counter1** through **sp_user_counter10**.</span></span> <span data-ttu-id="9be46-107">由于这些存储过程由用户应用程序执行，因此，这些存储过程设置的值显示在系统监视器中。</span><span class="sxs-lookup"><span data-stu-id="9be46-107">As these stored procedures are executed by user applications, the values set by the stored procedures are displayed in System Monitor.</span></span> <span data-ttu-id="9be46-108">计数器可以监视任何单一的整型值，例如，用于计算某产品在一天中获得的订单数的存储过程。</span><span class="sxs-lookup"><span data-stu-id="9be46-108">A counter can monitor any single integer value (for example, a stored procedure that counts how many orders for a particular product have occurred in one day).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9be46-109">系统监视器不会自动轮询用户计数器存储过程。</span><span class="sxs-lookup"><span data-stu-id="9be46-109">The user counter stored procedures are not polled automatically by System Monitor.</span></span> <span data-ttu-id="9be46-110">必须由一个用户应用程序明确执行用户计数器存储过程，以更新计数器值。</span><span class="sxs-lookup"><span data-stu-id="9be46-110">They must be explicitly executed by a user application for the counter values to be updated.</span></span> <span data-ttu-id="9be46-111">可以使用触发器自动更新计数器值。</span><span class="sxs-lookup"><span data-stu-id="9be46-111">Use a trigger to update the value of the counter automatically.</span></span> <span data-ttu-id="9be46-112">例如，要创建一个计数器来监视某表中的行数，可以针对执行以下语句的表创建 INSERT 和 DELETE 触发器： `SELECT COUNT(*) FROM table`。</span><span class="sxs-lookup"><span data-stu-id="9be46-112">For example, to create a counter that monitors the number of rows in a table, create an INSERT and DELETE trigger on the table that executes the following statement: `SELECT COUNT(*) FROM table`.</span></span> <span data-ttu-id="9be46-113">每当由于对表执行了 INSERT 或 DELETE 操作而激发了触发器时，系统监视器计数器就会自动更新。</span><span class="sxs-lookup"><span data-stu-id="9be46-113">Whenever the trigger is fired because of an INSERT or DELETE operation occurring on the table, the System Monitor counter is automatically updated.</span></span>  
  
 <span data-ttu-id="9be46-114">下表介绍 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] User Settable 对象。</span><span class="sxs-lookup"><span data-stu-id="9be46-114">This table describes the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **User Settable** object.</span></span>  
  
|<span data-ttu-id="9be46-115">SQL Server User Settable 计数器</span><span class="sxs-lookup"><span data-stu-id="9be46-115">SQL Server User Settable counters</span></span>|<span data-ttu-id="9be46-116">说明</span><span class="sxs-lookup"><span data-stu-id="9be46-116">Description</span></span>|  
|---------------------------------------|-----------------|  
|<span data-ttu-id="9be46-117">**查询**</span><span class="sxs-lookup"><span data-stu-id="9be46-117">**Query**</span></span>|<span data-ttu-id="9be46-118">**User Settable** 对象包含 Query 计数器。</span><span class="sxs-lookup"><span data-stu-id="9be46-118">The **User Settable** object contains the query counter.</span></span> <span data-ttu-id="9be46-119">用户对查询对象中的 **用户计数器** 进行配置。</span><span class="sxs-lookup"><span data-stu-id="9be46-119">Users configure the **User counters** within the query object.</span></span>|  
  
 <span data-ttu-id="9be46-120">此表列出了 **Query** 计数器的 **实例** 。</span><span class="sxs-lookup"><span data-stu-id="9be46-120">This table describes the **instances** of the **Query** counter.</span></span>  
  
|<span data-ttu-id="9be46-121">Query 计数器实例</span><span class="sxs-lookup"><span data-stu-id="9be46-121">Query counter instances</span></span>|<span data-ttu-id="9be46-122">说明</span><span class="sxs-lookup"><span data-stu-id="9be46-122">Description</span></span>|  
|-----------------------------|-----------------|  
|<span data-ttu-id="9be46-123">**用户计数器 1**</span><span class="sxs-lookup"><span data-stu-id="9be46-123">**User counter 1**</span></span>|<span data-ttu-id="9be46-124">使用 **sp_user_counter1**定义。</span><span class="sxs-lookup"><span data-stu-id="9be46-124">Defined using **sp_user_counter1**.</span></span>|  
|<span data-ttu-id="9be46-125">**用户计数器 2**</span><span class="sxs-lookup"><span data-stu-id="9be46-125">**User counter 2**</span></span>|<span data-ttu-id="9be46-126">使用 **sp_user_counter2**定义。</span><span class="sxs-lookup"><span data-stu-id="9be46-126">Defined using **sp_user_counter2**.</span></span>|  
|<span data-ttu-id="9be46-127">**用户计数器 3**</span><span class="sxs-lookup"><span data-stu-id="9be46-127">**User counter 3**</span></span>|<span data-ttu-id="9be46-128">使用 **sp_user_counter3**定义。</span><span class="sxs-lookup"><span data-stu-id="9be46-128">Defined using **sp_user_counter3**.</span></span>|  
|<span data-ttu-id="9be46-129">...</span><span class="sxs-lookup"><span data-stu-id="9be46-129">...</span></span>||  
|<span data-ttu-id="9be46-130">**用户计数器 10**</span><span class="sxs-lookup"><span data-stu-id="9be46-130">**User counter 10**</span></span>|<span data-ttu-id="9be46-131">使用 **sp_user_counter10**定义。</span><span class="sxs-lookup"><span data-stu-id="9be46-131">Defined using **sp_user_counter10**.</span></span>|  
  
 <span data-ttu-id="9be46-132">要使用用户计数器存储过程，只需从自己的应用程序中执行它们，并用一个整型参数表示计数器的新值。</span><span class="sxs-lookup"><span data-stu-id="9be46-132">To make use of the user counter stored procedures, execute them from your own application with a single integer parameter representing the new value for the counter.</span></span> <span data-ttu-id="9be46-133">例如，若要将 **用户计数器 1** 的值设置为 10，执行下面的 Transact-SQL 语句：</span><span class="sxs-lookup"><span data-stu-id="9be46-133">For example, to set **User counter 1** to the value 10, execute this Transact-SQL statement:</span></span>  
  
```  
EXECUTE sp_user_counter1 10  
```  
  
 <span data-ttu-id="9be46-134">用户计数器存储过程可从任何可以调用其他存储过程（例如自己的存储过程）的位置调用。</span><span class="sxs-lookup"><span data-stu-id="9be46-134">The user counter stored procedures can be called from anywhere other stored procedures can be called, such as your own stored procedures.</span></span> <span data-ttu-id="9be46-135">例如，可以创建以下存储过程来对自一个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例启动以来连接和尝试连接的次数计数：</span><span class="sxs-lookup"><span data-stu-id="9be46-135">For example, you can create the following stored procedure to count the number of connections and attempted connections since an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] was started:</span></span>  
  
```  
DROP PROC My_Proc  
GO  
CREATE PROC My_Proc  
AS   
   EXECUTE sp_user_counter1 @@CONNECTIONS  
GO  
```  
  
 <span data-ttu-id="9be46-136">@@CONNECTIONS 函数返回自一个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例启动以来连接或尝试连接的次数。</span><span class="sxs-lookup"><span data-stu-id="9be46-136">The @@CONNECTIONS function returns the number of connections or attempted connections since an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] started.</span></span> <span data-ttu-id="9be46-137">此值作为参数传递给 **sp_user_counter1** 存储过程。</span><span class="sxs-lookup"><span data-stu-id="9be46-137">This value is passed to the **sp_user_counter1** stored procedure as the parameter.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="9be46-138">应使用户计数器存储过程中定义的查询尽可能简单。</span><span class="sxs-lookup"><span data-stu-id="9be46-138">Make the queries defined in the user counter stored procedures as simple as possible.</span></span> <span data-ttu-id="9be46-139">执行排序或哈希操作等会占用大量内存的查询，或执行大量 I/O 操作的查询，开销会很大，并且会影响性能。</span><span class="sxs-lookup"><span data-stu-id="9be46-139">Memory-intensive queries that perform substantial sort or hash operations or queries that perform large amounts of I/O are expensive to execute and can impact performance.</span></span>  
  
## <a name="permissions"></a><span data-ttu-id="9be46-140">权限</span><span class="sxs-lookup"><span data-stu-id="9be46-140">Permissions</span></span>  
 <span data-ttu-id="9be46-141">**sp_user_counter** 可供所有用户使用，但仅限于针对查询计数器。</span><span class="sxs-lookup"><span data-stu-id="9be46-141">**sp_user_counter** is available for all users but can be restricted for any query counter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9be46-142">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9be46-142">See Also</span></span>  
 [<span data-ttu-id="9be46-143">监视资源使用情况（系统监视器）</span><span class="sxs-lookup"><span data-stu-id="9be46-143">Monitor Resource Usage &#40;System Monitor&#41;</span></span>](monitor-resource-usage-system-monitor.md)  
  
  
