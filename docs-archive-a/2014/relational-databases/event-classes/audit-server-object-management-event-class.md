---
title: Audit Server Object Management 事件类 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Audit Server Object Management event class
ms.assetid: 106ffe8d-da60-4b1f-8866-6cef6a5931ad
author: stevestein
ms.author: sstein
ms.openlocfilehash: 95967c205b255a9f5accb979f1cb9e5c1eeebeed
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689899"
---
# <a name="audit-server-object-management-event-class"></a><span data-ttu-id="8a2b1-102">Audit Server Object Management 事件类</span><span class="sxs-lookup"><span data-stu-id="8a2b1-102">Audit Server Object Management Event Class</span></span>
  <span data-ttu-id="8a2b1-103">在对服务器对象执行 CREATE、ALTER 或 DROP 的情况下，会发生 **Audit Server Object Management** 事件类。</span><span class="sxs-lookup"><span data-stu-id="8a2b1-103">The **Audit Server Object Management** event class occurs in the case of CREATE, ALTER, or DROP for server objects.</span></span>  
  
## <a name="audit-server-object-management-event-class-data-columns"></a><span data-ttu-id="8a2b1-104">Audit Server Object Management 事件类的数据列</span><span class="sxs-lookup"><span data-stu-id="8a2b1-104">Audit Server Object Management Event Class Data Columns</span></span>  
  
|<span data-ttu-id="8a2b1-105">数据列名称</span><span class="sxs-lookup"><span data-stu-id="8a2b1-105">Data column name</span></span>|<span data-ttu-id="8a2b1-106">数据类型</span><span class="sxs-lookup"><span data-stu-id="8a2b1-106">Data type</span></span>|<span data-ttu-id="8a2b1-107">说明</span><span class="sxs-lookup"><span data-stu-id="8a2b1-107">Description</span></span>|<span data-ttu-id="8a2b1-108">列 ID</span><span class="sxs-lookup"><span data-stu-id="8a2b1-108">Column ID</span></span>|<span data-ttu-id="8a2b1-109">可筛选</span><span class="sxs-lookup"><span data-stu-id="8a2b1-109">Filterable</span></span>|  
|----------------------|---------------|-----------------|---------------|----------------|  
|<span data-ttu-id="8a2b1-110">ApplicationName </span><span class="sxs-lookup"><span data-stu-id="8a2b1-110">**ApplicationName**</span></span>|<span data-ttu-id="8a2b1-111">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="8a2b1-111">**nvarchar**</span></span>|<span data-ttu-id="8a2b1-112">与 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例建立连接的客户端应用程序的名称。</span><span class="sxs-lookup"><span data-stu-id="8a2b1-112">Name of the client application that created the connection to an instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="8a2b1-113">此列由应用程序传递的值填充，而不是由所显示的程序名填充。</span><span class="sxs-lookup"><span data-stu-id="8a2b1-113">This column is populated with the values passed by the application rather than the displayed name of the program.</span></span>|<span data-ttu-id="8a2b1-114">10</span><span class="sxs-lookup"><span data-stu-id="8a2b1-114">10</span></span>|<span data-ttu-id="8a2b1-115">是</span><span class="sxs-lookup"><span data-stu-id="8a2b1-115">Yes</span></span>|  
|<span data-ttu-id="8a2b1-116">**DatabaseID**</span><span class="sxs-lookup"><span data-stu-id="8a2b1-116">**DatabaseID**</span></span>|<span data-ttu-id="8a2b1-117">**int**</span><span class="sxs-lookup"><span data-stu-id="8a2b1-117">**int**</span></span>|<span data-ttu-id="8a2b1-118">由 USE *database* 语句指定的数据库的 ID；如果未对给定实例发出 USE *database* 语句，则为默认数据库的 ID。</span><span class="sxs-lookup"><span data-stu-id="8a2b1-118">ID of the database specified by the USE *database* statement or the default database if no USE *database* statement has been issued for a given instance.</span></span> [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="8a2b1-119">数据列而且服务器可用，则 **ServerName** 将显示数据库名。</span><span class="sxs-lookup"><span data-stu-id="8a2b1-119">displays the name of the database if the **ServerName** data column is captured in the trace and the server is available.</span></span> <span data-ttu-id="8a2b1-120">可使用 DB_ID 函数来确定数据库的值。</span><span class="sxs-lookup"><span data-stu-id="8a2b1-120">Determine the value for a database by using the DB_ID function.</span></span>|<span data-ttu-id="8a2b1-121">3</span><span class="sxs-lookup"><span data-stu-id="8a2b1-121">3</span></span>|<span data-ttu-id="8a2b1-122">是</span><span class="sxs-lookup"><span data-stu-id="8a2b1-122">Yes</span></span>|  
|<span data-ttu-id="8a2b1-123">**DatabaseName**</span><span class="sxs-lookup"><span data-stu-id="8a2b1-123">**DatabaseName**</span></span>|<span data-ttu-id="8a2b1-124">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="8a2b1-124">**nvarchar**</span></span>|<span data-ttu-id="8a2b1-125">正在其中运行用户语句的数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="8a2b1-125">Name of the database in which the user statement is running.</span></span>|<span data-ttu-id="8a2b1-126">35</span><span class="sxs-lookup"><span data-stu-id="8a2b1-126">35</span></span>|<span data-ttu-id="8a2b1-127">是</span><span class="sxs-lookup"><span data-stu-id="8a2b1-127">Yes</span></span>|  
|<span data-ttu-id="8a2b1-128">**DBUserName**</span><span class="sxs-lookup"><span data-stu-id="8a2b1-128">**DBUserName**</span></span>|<span data-ttu-id="8a2b1-129">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="8a2b1-129">**nvarchar**</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="8a2b1-130">用户名。</span><span class="sxs-lookup"><span data-stu-id="8a2b1-130">user name of the client.</span></span>|<span data-ttu-id="8a2b1-131">40</span><span class="sxs-lookup"><span data-stu-id="8a2b1-131">40</span></span>|<span data-ttu-id="8a2b1-132">是</span><span class="sxs-lookup"><span data-stu-id="8a2b1-132">Yes</span></span>|  
|<span data-ttu-id="8a2b1-133">**EventSequence**</span><span class="sxs-lookup"><span data-stu-id="8a2b1-133">**EventSequence**</span></span>|<span data-ttu-id="8a2b1-134">**int**</span><span class="sxs-lookup"><span data-stu-id="8a2b1-134">**int**</span></span>|<span data-ttu-id="8a2b1-135">给定事件在请求中的顺序。</span><span class="sxs-lookup"><span data-stu-id="8a2b1-135">Sequence of a given event within the request.</span></span>|<span data-ttu-id="8a2b1-136">51</span><span class="sxs-lookup"><span data-stu-id="8a2b1-136">51</span></span>|<span data-ttu-id="8a2b1-137">否</span><span class="sxs-lookup"><span data-stu-id="8a2b1-137">No</span></span>|  
|<span data-ttu-id="8a2b1-138">**EventSubClass**</span><span class="sxs-lookup"><span data-stu-id="8a2b1-138">**EventSubClass**</span></span>|<span data-ttu-id="8a2b1-139">**int**</span><span class="sxs-lookup"><span data-stu-id="8a2b1-139">**int**</span></span>|<span data-ttu-id="8a2b1-140">事件子类的类型。</span><span class="sxs-lookup"><span data-stu-id="8a2b1-140">Type of event subclass.</span></span><br /><br /> <span data-ttu-id="8a2b1-141">1 = 创建</span><span class="sxs-lookup"><span data-stu-id="8a2b1-141">1=Create</span></span><br /><br /> <span data-ttu-id="8a2b1-142">2 = 更改</span><span class="sxs-lookup"><span data-stu-id="8a2b1-142">2=Alter</span></span><br /><br /> <span data-ttu-id="8a2b1-143">3 = 删除</span><span class="sxs-lookup"><span data-stu-id="8a2b1-143">3=Drop</span></span><br /><br /> <span data-ttu-id="8a2b1-144">4 = 转储</span><span class="sxs-lookup"><span data-stu-id="8a2b1-144">4=Dump</span></span><br /><br /> <span data-ttu-id="8a2b1-145">7 = 凭据已映射到登录帐户</span><span class="sxs-lookup"><span data-stu-id="8a2b1-145">7=Credential mapped to login</span></span><br /><br /> <span data-ttu-id="8a2b1-146">9 = 已删除凭据映射表</span><span class="sxs-lookup"><span data-stu-id="8a2b1-146">9=Credential Map Dropped</span></span><br /><br /> <span data-ttu-id="8a2b1-147">11 = 加载</span><span class="sxs-lookup"><span data-stu-id="8a2b1-147">11=Load</span></span>|<span data-ttu-id="8a2b1-148">21</span><span class="sxs-lookup"><span data-stu-id="8a2b1-148">21</span></span>|<span data-ttu-id="8a2b1-149">是</span><span class="sxs-lookup"><span data-stu-id="8a2b1-149">Yes</span></span>|  
|<span data-ttu-id="8a2b1-150">**HostName**</span><span class="sxs-lookup"><span data-stu-id="8a2b1-150">**HostName**</span></span>|<span data-ttu-id="8a2b1-151">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="8a2b1-151">**nvarchar**</span></span>|<span data-ttu-id="8a2b1-152">正在运行客户端的计算机的名称。</span><span class="sxs-lookup"><span data-stu-id="8a2b1-152">Name of the computer on which the client is running.</span></span> <span data-ttu-id="8a2b1-153">如果客户端提供了主机名，则填充此数据列。</span><span class="sxs-lookup"><span data-stu-id="8a2b1-153">This data column is populated if the client provides the host name.</span></span> <span data-ttu-id="8a2b1-154">若要确定主机名，请使用 HOST_NAME 函数。</span><span class="sxs-lookup"><span data-stu-id="8a2b1-154">To determine the host name, use the HOST_NAME function.</span></span>|<span data-ttu-id="8a2b1-155">8</span><span class="sxs-lookup"><span data-stu-id="8a2b1-155">8</span></span>|<span data-ttu-id="8a2b1-156">是</span><span class="sxs-lookup"><span data-stu-id="8a2b1-156">Yes</span></span>|  
|<span data-ttu-id="8a2b1-157">**IsSystem**</span><span class="sxs-lookup"><span data-stu-id="8a2b1-157">**IsSystem**</span></span>|<span data-ttu-id="8a2b1-158">**int**</span><span class="sxs-lookup"><span data-stu-id="8a2b1-158">**int**</span></span>|<span data-ttu-id="8a2b1-159">指示事件是发生在系统进程中还是发生在用户进程中。</span><span class="sxs-lookup"><span data-stu-id="8a2b1-159">Indicates whether the event occurred on a system process or a user process.</span></span> <span data-ttu-id="8a2b1-160">1 = 系统，0 = 用户。</span><span class="sxs-lookup"><span data-stu-id="8a2b1-160">1 = system, 0 = user.</span></span>|<span data-ttu-id="8a2b1-161">60</span><span class="sxs-lookup"><span data-stu-id="8a2b1-161">60</span></span>|<span data-ttu-id="8a2b1-162">是</span><span class="sxs-lookup"><span data-stu-id="8a2b1-162">Yes</span></span>|  
|<span data-ttu-id="8a2b1-163">**LoginName**</span><span class="sxs-lookup"><span data-stu-id="8a2b1-163">**LoginName**</span></span>|<span data-ttu-id="8a2b1-164">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="8a2b1-164">**nvarchar**</span></span>|<span data-ttu-id="8a2b1-165">用户的登录名（ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安全登录名或 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 登录凭据，格式为“DOMAIN\username”）。</span><span class="sxs-lookup"><span data-stu-id="8a2b1-165">Name of the login of the user (either [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] security login or the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows login credentials in the form of DOMAIN\username).</span></span>|<span data-ttu-id="8a2b1-166">11</span><span class="sxs-lookup"><span data-stu-id="8a2b1-166">11</span></span>|<span data-ttu-id="8a2b1-167">是</span><span class="sxs-lookup"><span data-stu-id="8a2b1-167">Yes</span></span>|  
|<span data-ttu-id="8a2b1-168">**LoginSid**</span><span class="sxs-lookup"><span data-stu-id="8a2b1-168">**LoginSid**</span></span>|<span data-ttu-id="8a2b1-169">**图像**</span><span class="sxs-lookup"><span data-stu-id="8a2b1-169">**image**</span></span>|<span data-ttu-id="8a2b1-170">登录用户的安全标识号 (SID)。</span><span class="sxs-lookup"><span data-stu-id="8a2b1-170">Security identification number (SID) of the logged-in user.</span></span> <span data-ttu-id="8a2b1-171">你可以在 **sys.server_principals** 目录视图中找到此信息。</span><span class="sxs-lookup"><span data-stu-id="8a2b1-171">You can find this information in the **sys.server_principals** catalog view.</span></span> <span data-ttu-id="8a2b1-172">服务器中的每个登录名都具有唯一的 SID。</span><span class="sxs-lookup"><span data-stu-id="8a2b1-172">Each SID is unique for each login in the server.</span></span>|<span data-ttu-id="8a2b1-173">41</span><span class="sxs-lookup"><span data-stu-id="8a2b1-173">41</span></span>|<span data-ttu-id="8a2b1-174">是</span><span class="sxs-lookup"><span data-stu-id="8a2b1-174">Yes</span></span>|  
|<span data-ttu-id="8a2b1-175">**NTDomainName**</span><span class="sxs-lookup"><span data-stu-id="8a2b1-175">**NTDomainName**</span></span>|<span data-ttu-id="8a2b1-176">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="8a2b1-176">**nvarchar**</span></span>|<span data-ttu-id="8a2b1-177">用户所属的 Windows 域。</span><span class="sxs-lookup"><span data-stu-id="8a2b1-177">Windows domain to which the user belongs.</span></span>|<span data-ttu-id="8a2b1-178">7</span><span class="sxs-lookup"><span data-stu-id="8a2b1-178">7</span></span>|<span data-ttu-id="8a2b1-179">是</span><span class="sxs-lookup"><span data-stu-id="8a2b1-179">Yes</span></span>|  
|<span data-ttu-id="8a2b1-180">**NTUserName**</span><span class="sxs-lookup"><span data-stu-id="8a2b1-180">**NTUserName**</span></span>|<span data-ttu-id="8a2b1-181">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="8a2b1-181">**nvarchar**</span></span>|<span data-ttu-id="8a2b1-182">Windows 用户名。</span><span class="sxs-lookup"><span data-stu-id="8a2b1-182">Windows user name.</span></span>|<span data-ttu-id="8a2b1-183">6</span><span class="sxs-lookup"><span data-stu-id="8a2b1-183">6</span></span>|<span data-ttu-id="8a2b1-184">是</span><span class="sxs-lookup"><span data-stu-id="8a2b1-184">Yes</span></span>|  
|<span data-ttu-id="8a2b1-185">**ObjectName**</span><span class="sxs-lookup"><span data-stu-id="8a2b1-185">**ObjectName**</span></span>|<span data-ttu-id="8a2b1-186">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="8a2b1-186">**nvarchar**</span></span>|<span data-ttu-id="8a2b1-187">引用的对象名。</span><span class="sxs-lookup"><span data-stu-id="8a2b1-187">Name of the object being referenced.</span></span>|<span data-ttu-id="8a2b1-188">34</span><span class="sxs-lookup"><span data-stu-id="8a2b1-188">34</span></span>|<span data-ttu-id="8a2b1-189">是</span><span class="sxs-lookup"><span data-stu-id="8a2b1-189">Yes</span></span>|  
|<span data-ttu-id="8a2b1-190">**ObjectType**</span><span class="sxs-lookup"><span data-stu-id="8a2b1-190">**ObjectType**</span></span>|<span data-ttu-id="8a2b1-191">**int**</span><span class="sxs-lookup"><span data-stu-id="8a2b1-191">**int**</span></span>|<span data-ttu-id="8a2b1-192">表示事件中涉及的对象类型的值。</span><span class="sxs-lookup"><span data-stu-id="8a2b1-192">Value representing the type of the object involved in the event.</span></span> <span data-ttu-id="8a2b1-193">此值对应于 **sys.objects** 目录视图中的类型列。</span><span class="sxs-lookup"><span data-stu-id="8a2b1-193">This value corresponds to the type column in the **sys.objects** catalog view.</span></span> <span data-ttu-id="8a2b1-194">有关值的信息，请参阅 [ObjectType 跟踪事件列](objecttype-trace-event-column.md)。</span><span class="sxs-lookup"><span data-stu-id="8a2b1-194">For values, see [ObjectType Trace Event Column](objecttype-trace-event-column.md).</span></span>|<span data-ttu-id="8a2b1-195">28</span><span class="sxs-lookup"><span data-stu-id="8a2b1-195">28</span></span>|<span data-ttu-id="8a2b1-196">是</span><span class="sxs-lookup"><span data-stu-id="8a2b1-196">Yes</span></span>|  
|<span data-ttu-id="8a2b1-197">**OwnerName**</span><span class="sxs-lookup"><span data-stu-id="8a2b1-197">**OwnerName**</span></span>|<span data-ttu-id="8a2b1-198">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="8a2b1-198">**nvarchar**</span></span>|<span data-ttu-id="8a2b1-199">对象所有者的数据库用户名。</span><span class="sxs-lookup"><span data-stu-id="8a2b1-199">Database user name of the object owner.</span></span>|<span data-ttu-id="8a2b1-200">37</span><span class="sxs-lookup"><span data-stu-id="8a2b1-200">37</span></span>|<span data-ttu-id="8a2b1-201">是</span><span class="sxs-lookup"><span data-stu-id="8a2b1-201">Yes</span></span>|  
|<span data-ttu-id="8a2b1-202">**RequestID**</span><span class="sxs-lookup"><span data-stu-id="8a2b1-202">**RequestID**</span></span>|<span data-ttu-id="8a2b1-203">**int**</span><span class="sxs-lookup"><span data-stu-id="8a2b1-203">**int**</span></span>|<span data-ttu-id="8a2b1-204">包含该语句的请求的 ID。</span><span class="sxs-lookup"><span data-stu-id="8a2b1-204">ID of the request containing the statement.</span></span>|<span data-ttu-id="8a2b1-205">49</span><span class="sxs-lookup"><span data-stu-id="8a2b1-205">49</span></span>|<span data-ttu-id="8a2b1-206">是</span><span class="sxs-lookup"><span data-stu-id="8a2b1-206">Yes</span></span>|  
|<span data-ttu-id="8a2b1-207">**ServerName**</span><span class="sxs-lookup"><span data-stu-id="8a2b1-207">**ServerName**</span></span>|<span data-ttu-id="8a2b1-208">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="8a2b1-208">**nvarchar**</span></span>|<span data-ttu-id="8a2b1-209">所跟踪的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例的名称。</span><span class="sxs-lookup"><span data-stu-id="8a2b1-209">Name of the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] being traced.</span></span>|<span data-ttu-id="8a2b1-210">26</span><span class="sxs-lookup"><span data-stu-id="8a2b1-210">26</span></span>|<span data-ttu-id="8a2b1-211">否</span><span class="sxs-lookup"><span data-stu-id="8a2b1-211">No</span></span>|  
|<span data-ttu-id="8a2b1-212">**SessionLoginName**</span><span class="sxs-lookup"><span data-stu-id="8a2b1-212">**SessionLoginName**</span></span>|<span data-ttu-id="8a2b1-213">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="8a2b1-213">**nvarchar**</span></span>|<span data-ttu-id="8a2b1-214">发起会话的用户的登录名。</span><span class="sxs-lookup"><span data-stu-id="8a2b1-214">Login name of the user who originated the session.</span></span> <span data-ttu-id="8a2b1-215">例如，如果你使用 Login1 连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，再以 Login2 的身份执行语句，则 **SessionLoginName** 将显示 Login1，而 **LoginName** 将显示 Login2。</span><span class="sxs-lookup"><span data-stu-id="8a2b1-215">For example, if you connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using Login1 and execute a statement as Login2, **SessionLoginName** shows Login1 and **LoginName** shows Login2.</span></span> <span data-ttu-id="8a2b1-216">此列将同时显示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名和 Windows 登录名。</span><span class="sxs-lookup"><span data-stu-id="8a2b1-216">This column displays both [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and Windows logins.</span></span>|<span data-ttu-id="8a2b1-217">64</span><span class="sxs-lookup"><span data-stu-id="8a2b1-217">64</span></span>|<span data-ttu-id="8a2b1-218">是</span><span class="sxs-lookup"><span data-stu-id="8a2b1-218">Yes</span></span>|  
|<span data-ttu-id="8a2b1-219">**SPID**</span><span class="sxs-lookup"><span data-stu-id="8a2b1-219">**SPID**</span></span>|<span data-ttu-id="8a2b1-220">**int**</span><span class="sxs-lookup"><span data-stu-id="8a2b1-220">**int**</span></span>|<span data-ttu-id="8a2b1-221">发生该事件的会话的 ID。</span><span class="sxs-lookup"><span data-stu-id="8a2b1-221">ID of the session on which the event occurred.</span></span>|<span data-ttu-id="8a2b1-222">12</span><span class="sxs-lookup"><span data-stu-id="8a2b1-222">12</span></span>|<span data-ttu-id="8a2b1-223">是</span><span class="sxs-lookup"><span data-stu-id="8a2b1-223">Yes</span></span>|  
|<span data-ttu-id="8a2b1-224">**StartTime**</span><span class="sxs-lookup"><span data-stu-id="8a2b1-224">**StartTime**</span></span>|<span data-ttu-id="8a2b1-225">**datetime**</span><span class="sxs-lookup"><span data-stu-id="8a2b1-225">**datetime**</span></span>|<span data-ttu-id="8a2b1-226">该事件（如果存在）的启动时间。</span><span class="sxs-lookup"><span data-stu-id="8a2b1-226">Time at which the event started, if available.</span></span>|<span data-ttu-id="8a2b1-227">14</span><span class="sxs-lookup"><span data-stu-id="8a2b1-227">14</span></span>|<span data-ttu-id="8a2b1-228">是</span><span class="sxs-lookup"><span data-stu-id="8a2b1-228">Yes</span></span>|  
|<span data-ttu-id="8a2b1-229">**Success**</span><span class="sxs-lookup"><span data-stu-id="8a2b1-229">**Success**</span></span>|<span data-ttu-id="8a2b1-230">**int**</span><span class="sxs-lookup"><span data-stu-id="8a2b1-230">**int**</span></span>|<span data-ttu-id="8a2b1-231">1 = 成功。</span><span class="sxs-lookup"><span data-stu-id="8a2b1-231">1 = success.</span></span> <span data-ttu-id="8a2b1-232">0 = 失败。</span><span class="sxs-lookup"><span data-stu-id="8a2b1-232">0 = failure.</span></span> <span data-ttu-id="8a2b1-233">例如，值为 1 时表示权限检查成功；值为 0 时表示权限检查失败。</span><span class="sxs-lookup"><span data-stu-id="8a2b1-233">For example, a value of 1 indicates success of a permissions check and a value of 0 indicates failure of that check.</span></span>|<span data-ttu-id="8a2b1-234">23</span><span class="sxs-lookup"><span data-stu-id="8a2b1-234">23</span></span>|<span data-ttu-id="8a2b1-235">是</span><span class="sxs-lookup"><span data-stu-id="8a2b1-235">Yes</span></span>|  
|<span data-ttu-id="8a2b1-236">**TransactionID**</span><span class="sxs-lookup"><span data-stu-id="8a2b1-236">**TransactionID**</span></span>|<span data-ttu-id="8a2b1-237">**bigint**</span><span class="sxs-lookup"><span data-stu-id="8a2b1-237">**bigint**</span></span>|<span data-ttu-id="8a2b1-238">系统分配的事务 ID。</span><span class="sxs-lookup"><span data-stu-id="8a2b1-238">System-assigned ID of the transaction.</span></span>|<span data-ttu-id="8a2b1-239">4</span><span class="sxs-lookup"><span data-stu-id="8a2b1-239">4</span></span>|<span data-ttu-id="8a2b1-240">是</span><span class="sxs-lookup"><span data-stu-id="8a2b1-240">Yes</span></span>|  
|<span data-ttu-id="8a2b1-241">**XactSequence**</span><span class="sxs-lookup"><span data-stu-id="8a2b1-241">**XactSequence**</span></span>|<span data-ttu-id="8a2b1-242">**bigint**</span><span class="sxs-lookup"><span data-stu-id="8a2b1-242">**bigint**</span></span>|<span data-ttu-id="8a2b1-243">用于说明当前事务的标记。</span><span class="sxs-lookup"><span data-stu-id="8a2b1-243">Token used to describe the current transaction.</span></span>|<span data-ttu-id="8a2b1-244">50</span><span class="sxs-lookup"><span data-stu-id="8a2b1-244">50</span></span>|<span data-ttu-id="8a2b1-245">是</span><span class="sxs-lookup"><span data-stu-id="8a2b1-245">Yes</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8a2b1-246">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8a2b1-246">See Also</span></span>  
 <span data-ttu-id="8a2b1-247">[SQL Server 事件探查器](../../tools/sql-server-profiler/sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="8a2b1-247">[SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md) </span></span>  
 [<span data-ttu-id="8a2b1-248">sp_trace_setevent (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="8a2b1-248">sp_trace_setevent &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)  
  
  