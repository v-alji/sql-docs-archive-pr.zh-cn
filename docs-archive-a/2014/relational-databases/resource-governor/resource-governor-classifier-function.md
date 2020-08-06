---
title: 资源调控器分类器函数 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Resource Governor, classifier function
- user-defined functions [SQL Server], classifier function
- classifier function [SQL Server]
- classifier function [SQL Server], overview
ms.assetid: 64c25012-7068-476f-afa2-0b4f3adde9a4
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 69b6fd10ac0adc6f76925e0d41f110b917111466
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689307"
---
# <a name="resource-governor-classifier-function"></a><span data-ttu-id="23ef8-102">Resource Governor Classifier Function</span><span class="sxs-lookup"><span data-stu-id="23ef8-102">Resource Governor Classifier Function</span></span>
  <span data-ttu-id="23ef8-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 资源调控器分类过程会根据传入会话的特征将其分配给工作负荷组。</span><span class="sxs-lookup"><span data-stu-id="23ef8-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] resource governor classification process assigns incoming sessions to a workload group based on the characteristics of the session.</span></span> <span data-ttu-id="23ef8-104">您可以通过编写用户定义函数（称为分类器函数）来定制分类逻辑。</span><span class="sxs-lookup"><span data-stu-id="23ef8-104">You can tailor the classification logic by writing a user-defined function, called a classifier function.</span></span>  
  
## <a name="classification"></a><span data-ttu-id="23ef8-105">分类</span><span class="sxs-lookup"><span data-stu-id="23ef8-105">Classification</span></span>  
 <span data-ttu-id="23ef8-106">资源调控器支持对传入会话的分类。</span><span class="sxs-lookup"><span data-stu-id="23ef8-106">Resource Governor supports the classification of incoming sessions.</span></span> <span data-ttu-id="23ef8-107">分类基于函数中包含的一组用户编写的条件。</span><span class="sxs-lookup"><span data-stu-id="23ef8-107">Classification is based on a set of user-written criteria contained in a function.</span></span> <span data-ttu-id="23ef8-108">函数逻辑的结果使资源调控器可以将会话归入现有工作负荷组类。</span><span class="sxs-lookup"><span data-stu-id="23ef8-108">The results of the function logic enable Resource Governor to classify sessions into existing workload groups.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="23ef8-109">内部工作负荷组中填入的是仅供内部使用的请求。</span><span class="sxs-lookup"><span data-stu-id="23ef8-109">The internal workload group is populated with requests that are for internal use only.</span></span> <span data-ttu-id="23ef8-110">您不能更改用于路由这些请求的标准，也不能将请求归入内部工作负荷组类。</span><span class="sxs-lookup"><span data-stu-id="23ef8-110">You cannot change the criteria used for routing these requests and you cannot classify requests into the internal workload group.</span></span>  
  
 <span data-ttu-id="23ef8-111">您可以编写一个标量函数，在其中包含用于将传入会话分配给工作负荷组的逻辑。</span><span class="sxs-lookup"><span data-stu-id="23ef8-111">You can write a scalar function that contains the logic that is used to assign incoming sessions to a workload group.</span></span> <span data-ttu-id="23ef8-112">必须先完成下列操作，才能使用此函数：</span><span class="sxs-lookup"><span data-stu-id="23ef8-112">Before you can use this function, you must complete the following actions:</span></span>  
  
-   <span data-ttu-id="23ef8-113">使用 ALTER RESOURCE GOVERNOR 语句创建并注册此函数。</span><span class="sxs-lookup"><span data-stu-id="23ef8-113">Create and register the function using the ALTER RESOURCE GOVERNOR statement.</span></span> <span data-ttu-id="23ef8-114">有关详细信息，请参阅 [ALTER RESOURCE GOVERNOR (Transact-SQL)](/sql/t-sql/statements/alter-resource-governor-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="23ef8-114">For more information, see [ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-resource-governor-transact-sql).</span></span>  
  
-   <span data-ttu-id="23ef8-115">使用带 RECONFIGURE 参数的 ALTER RESOURCE GOVERNOR 语句更新资源调控器配置。</span><span class="sxs-lookup"><span data-stu-id="23ef8-115">Update the Resource Governor configuration using the ALTER RESOURCE GOVERNOR statement with the RECONFIGURE parameter.</span></span>  
  
 <span data-ttu-id="23ef8-116">创建此函数并应用配置更改后，资源调控器分类器将使用此函数返回的工作负荷组名称将新请求发送到相应的工作负荷组。</span><span class="sxs-lookup"><span data-stu-id="23ef8-116">After you create the function and apply the configuration changes, the Resource Governor classifier will use the workload group name returned by the function to send a new request to the appropriate workload group.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="23ef8-117">如果分类函数没有在指定的登录超时内完成，则客户端会话将超时。</span><span class="sxs-lookup"><span data-stu-id="23ef8-117">The client session may time out if the classification function does not complete within the specified time-out for the login.</span></span> <span data-ttu-id="23ef8-118">登录超时是客户端属性，因此服务器意识不到超时。长时间运行的分类器函数可使服务器长期保留孤立连接。</span><span class="sxs-lookup"><span data-stu-id="23ef8-118">Login time-out is a client property and as such, the server is unaware of a time-out. A long-running classifier function can leave the server with orphaned connections for long periods.</span></span> <span data-ttu-id="23ef8-119">创建在连接超时之前完成其执行的分类器函数非常重要。</span><span class="sxs-lookup"><span data-stu-id="23ef8-119">It is important that you create classifier functions that finish executing before a connection time-out.</span></span>  
  
 <span data-ttu-id="23ef8-120">用户定义的函数具有以下特征和行为：</span><span class="sxs-lookup"><span data-stu-id="23ef8-120">The user-defined function has the following characteristics and behaviors:</span></span>  
  
-   <span data-ttu-id="23ef8-121">将针对每个新会话评估用户定义函数，即使在启用了连接池的情况下也会这样做。</span><span class="sxs-lookup"><span data-stu-id="23ef8-121">The user-defined function is evaluated for every new session, even when connection pooling is enabled.</span></span>  
  
-   <span data-ttu-id="23ef8-122">用户定义的函数为会话提供工作负荷组上下文。</span><span class="sxs-lookup"><span data-stu-id="23ef8-122">The user-defined function gives workload group context for the session.</span></span> <span data-ttu-id="23ef8-123">确定组成员身份后，此会话将在会话的整个生存期内一直绑定到工作负荷组。</span><span class="sxs-lookup"><span data-stu-id="23ef8-123">After group membership is determined, the session is bound to the workload group for the lifetime of the session.</span></span>  
  
-   <span data-ttu-id="23ef8-124">如果用户定义的函数返回默认值 NULL 或不存在的组名称，则会话将拥有默认工作负荷组上下文。</span><span class="sxs-lookup"><span data-stu-id="23ef8-124">If the user-defined function returns NULL, default, or the name of non-existent group the session is given the default workload group context.</span></span> <span data-ttu-id="23ef8-125">如果由于任何原因而导致函数失败，则会话也将拥有默认上下文。</span><span class="sxs-lookup"><span data-stu-id="23ef8-125">The session is also given the default context if the function fails for any reason.</span></span>  
  
-   <span data-ttu-id="23ef8-126">函数应在服务器范围（master 数据库）内定义。</span><span class="sxs-lookup"><span data-stu-id="23ef8-126">The function should be defined with server scope (master database).</span></span>  
  
-   <span data-ttu-id="23ef8-127">分类器用户定义的函数的指定只在执行 ALTER RESOURCE GOVERNOR RECONFIGURE 后生效。</span><span class="sxs-lookup"><span data-stu-id="23ef8-127">The classifier user-defined function designation only takes effect after ALTER RESOURCE GOVERNOR RECONFIGURE is executed.</span></span>  
  
-   <span data-ttu-id="23ef8-128">一次只能将一个用户定义的函数指定为分类器。</span><span class="sxs-lookup"><span data-stu-id="23ef8-128">Only one user-defined function can be designated as a classifier at a time.</span></span>  
  
-   <span data-ttu-id="23ef8-129">除非删除分类器用户定义函数的分类器状态，否则不能删除或更改分类器用户定义的函数。</span><span class="sxs-lookup"><span data-stu-id="23ef8-129">The classifier user-defined function cannot be dropped or altered unless its classifier status is removed.</span></span>  
  
-   <span data-ttu-id="23ef8-130">如果缺少分类器用户定义的函数，则将所有会话归入默认组类。</span><span class="sxs-lookup"><span data-stu-id="23ef8-130">In the absence of a classifier user-defined function, all sessions are classified into the default group.</span></span>  
  
-   <span data-ttu-id="23ef8-131">分类器函数返回的工作负荷组位于架构绑定限制的作用域之外。</span><span class="sxs-lookup"><span data-stu-id="23ef8-131">The workload group returned by the classifier function is outside the scope of the schema-binding restriction.</span></span> <span data-ttu-id="23ef8-132">例如，不能删除表，但可以删除工作负荷组。</span><span class="sxs-lookup"><span data-stu-id="23ef8-132">For example, you cannot drop a table, but you can drop a workload group.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="23ef8-133">建议在服务器上启用专用管理员连接 (DAC)。</span><span class="sxs-lookup"><span data-stu-id="23ef8-133">We recommend enabling the Dedicated Administrator Connection (DAC) on the server.</span></span> <span data-ttu-id="23ef8-134">DAC 不进行资源调控器分类，因此可用于监视分类器函数并排除其故障。</span><span class="sxs-lookup"><span data-stu-id="23ef8-134">The DAC is not subject to Resource Governor classification and can be used to monitor and troubleshoot a classifier function.</span></span> <span data-ttu-id="23ef8-135">有关详细信息，请参阅 [用于数据库管理员的诊断连接](../../database-engine/configure-windows/diagnostic-connection-for-database-administrators.md)。</span><span class="sxs-lookup"><span data-stu-id="23ef8-135">For more information, see [Diagnostic Connection for Database Administrators](../../database-engine/configure-windows/diagnostic-connection-for-database-administrators.md).</span></span> <span data-ttu-id="23ef8-136">如果没有 DAC 可用来进行故障排除，则另一个选择是在单用户模式下重新启动系统。</span><span class="sxs-lookup"><span data-stu-id="23ef8-136">If a DAC is not available for troubleshooting, the other option is to restart the system in single user mode.</span></span> <span data-ttu-id="23ef8-137">虽然单用户模式不进行分类，但是它使您无法在资源调控器分类运行时对它进行诊断。</span><span class="sxs-lookup"><span data-stu-id="23ef8-137">Although single user mode is not subject to classification, it does not give you the ability to diagnose Resource Governor classification while it is running.</span></span>  
  
### <a name="classification-process"></a><span data-ttu-id="23ef8-138">分类过程</span><span class="sxs-lookup"><span data-stu-id="23ef8-138">Classification Process</span></span>  
 <span data-ttu-id="23ef8-139">在资源调控器上下文中，会话的登录过程包含下列步骤：</span><span class="sxs-lookup"><span data-stu-id="23ef8-139">In the context of Resource Governor, the login process for a session consists of the following steps:</span></span>  
  
1.  <span data-ttu-id="23ef8-140">登录身份验证</span><span class="sxs-lookup"><span data-stu-id="23ef8-140">Login authentication</span></span>  
  
2.  <span data-ttu-id="23ef8-141">LOGON 触发器执行</span><span class="sxs-lookup"><span data-stu-id="23ef8-141">LOGON trigger execution</span></span>  
  
3.  <span data-ttu-id="23ef8-142">分类</span><span class="sxs-lookup"><span data-stu-id="23ef8-142">Classification</span></span>  
  
 <span data-ttu-id="23ef8-143">分类启动时，资源调控器执行分类器函数，并使用函数返回的值将请求发送到相应的工作负荷组。</span><span class="sxs-lookup"><span data-stu-id="23ef8-143">When classification starts, Resource Governor executes the classifier function and uses the value returned by the function to send requests to the appropriate workload group.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="23ef8-144">在 [sys.dm_exec_sessions](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql) 和 [sys.dm_exec_requests](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql)中公开有关分类器函数和 LOGON 触发器的执行信息。</span><span class="sxs-lookup"><span data-stu-id="23ef8-144">Information about the execution of the classifier function and LOGON triggers is exposed in [sys.dm_exec_sessions](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql) and [sys.dm_exec_requests](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql).</span></span>  
  
## <a name="classification-function-tasks"></a><span data-ttu-id="23ef8-145">分类函数任务</span><span class="sxs-lookup"><span data-stu-id="23ef8-145">Classification Function Tasks</span></span>  
  
|<span data-ttu-id="23ef8-146">任务说明</span><span class="sxs-lookup"><span data-stu-id="23ef8-146">Task Description</span></span>|<span data-ttu-id="23ef8-147">主题</span><span class="sxs-lookup"><span data-stu-id="23ef8-147">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="23ef8-148">说明如何创建和测试分类器用户定义函数。</span><span class="sxs-lookup"><span data-stu-id="23ef8-148">Describes how to create and test a classifier user-defined function.</span></span>|[<span data-ttu-id="23ef8-149">创建和测试分类器用户定义函数</span><span class="sxs-lookup"><span data-stu-id="23ef8-149">Create and Test a Classifier User-Defined Function</span></span>](create-and-test-a-classifier-user-defined-function.md)|  
  
## <a name="see-also"></a><span data-ttu-id="23ef8-150">另请参阅</span><span class="sxs-lookup"><span data-stu-id="23ef8-150">See Also</span></span>  
 <span data-ttu-id="23ef8-151">[资源调控器](resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="23ef8-151">[Resource Governor](resource-governor.md) </span></span>  
 <span data-ttu-id="23ef8-152">[启用资源调控器](enable-resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="23ef8-152">[Enable Resource Governor](enable-resource-governor.md) </span></span>  
 <span data-ttu-id="23ef8-153">[资源调控器资源池](resource-governor-resource-pool.md) </span><span class="sxs-lookup"><span data-stu-id="23ef8-153">[Resource Governor Resource Pool](resource-governor-resource-pool.md) </span></span>  
 <span data-ttu-id="23ef8-154">[资源调控器工作负荷组](resource-governor-workload-group.md) </span><span class="sxs-lookup"><span data-stu-id="23ef8-154">[Resource Governor Workload Group](resource-governor-workload-group.md) </span></span>  
 <span data-ttu-id="23ef8-155">[使用模板配置资源调控器](configure-resource-governor-using-a-template.md) </span><span class="sxs-lookup"><span data-stu-id="23ef8-155">[Configure Resource Governor Using a Template](configure-resource-governor-using-a-template.md) </span></span>  
 [<span data-ttu-id="23ef8-156">查看资源调控器属性</span><span class="sxs-lookup"><span data-stu-id="23ef8-156">View Resource Governor Properties</span></span>](view-resource-governor-properties.md)  
  
  
