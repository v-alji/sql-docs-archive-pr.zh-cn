---
title: Audit Server Object GDR 事件类 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Audit Server Object GDR event class
ms.assetid: 117fedca-c1c4-469a-929a-9ea332c83d25
author: stevestein
ms.author: sstein
ms.openlocfilehash: b4088e6ee7fc75e061ccc94a1b65e364fd4ceace
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588537"
---
# <a name="audit-server-object-gdr-event-class"></a><span data-ttu-id="64316-102">Audit Server Object GDR 事件类</span><span class="sxs-lookup"><span data-stu-id="64316-102">Audit Server Object GDR Event Class</span></span>
  <span data-ttu-id="64316-103">只要 Microsoft SQL Server 中的任何用户针对服务器对象权限发出 GRANT、REVOKE 或 DENY， **Audit Server Object GDR** 事件类就会出现。</span><span class="sxs-lookup"><span data-stu-id="64316-103">The **Audit Server Object GDR** event class occurs whenever a GRANT, REVOKE, or DENY is issued for a server object permission by any user in Microsoft SQL Server.</span></span>  
  
## <a name="audit-server-object-gdr-event-class-data-columns"></a><span data-ttu-id="64316-104">Audit Server Object GDR 事件类的数据列</span><span class="sxs-lookup"><span data-stu-id="64316-104">Audit Server Object GDR Event Class Data Columns</span></span>  
  
|<span data-ttu-id="64316-105">数据列名称</span><span class="sxs-lookup"><span data-stu-id="64316-105">Data column name</span></span>|<span data-ttu-id="64316-106">数据类型</span><span class="sxs-lookup"><span data-stu-id="64316-106">Data type</span></span>|<span data-ttu-id="64316-107">说明</span><span class="sxs-lookup"><span data-stu-id="64316-107">Description</span></span>|<span data-ttu-id="64316-108">列 ID</span><span class="sxs-lookup"><span data-stu-id="64316-108">Column ID</span></span>|<span data-ttu-id="64316-109">可筛选</span><span class="sxs-lookup"><span data-stu-id="64316-109">Filterable</span></span>|  
|----------------------|---------------|-----------------|---------------|----------------|  
|<span data-ttu-id="64316-110">ApplicationName </span><span class="sxs-lookup"><span data-stu-id="64316-110">**ApplicationName**</span></span>|<span data-ttu-id="64316-111">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="64316-111">**nvarchar**</span></span>|<span data-ttu-id="64316-112">与 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例建立连接的客户端应用程序的名称。</span><span class="sxs-lookup"><span data-stu-id="64316-112">Name of the client application that created the connection to an instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="64316-113">此列由应用程序传递的值填充，而不是由所显示的程序名填充。</span><span class="sxs-lookup"><span data-stu-id="64316-113">This column is populated with the values passed by the application rather than the displayed name of the program.</span></span>|<span data-ttu-id="64316-114">10</span><span class="sxs-lookup"><span data-stu-id="64316-114">10</span></span>|<span data-ttu-id="64316-115">是</span><span class="sxs-lookup"><span data-stu-id="64316-115">Yes</span></span>|  
|<span data-ttu-id="64316-116">**ClientProcessID**</span><span class="sxs-lookup"><span data-stu-id="64316-116">**ClientProcessID**</span></span>|<span data-ttu-id="64316-117">**int**</span><span class="sxs-lookup"><span data-stu-id="64316-117">**int**</span></span>|<span data-ttu-id="64316-118">主机为运行该客户端应用程序的进程分配的 ID。</span><span class="sxs-lookup"><span data-stu-id="64316-118">ID assigned by the host computer to the process where the client application is running.</span></span> <span data-ttu-id="64316-119">如果客户端提供了客户端进程 ID，则填充此数据列。</span><span class="sxs-lookup"><span data-stu-id="64316-119">This data column is populated if the client provides the client process ID.</span></span>|<span data-ttu-id="64316-120">9</span><span class="sxs-lookup"><span data-stu-id="64316-120">9</span></span>|<span data-ttu-id="64316-121">是</span><span class="sxs-lookup"><span data-stu-id="64316-121">Yes</span></span>|  
|<span data-ttu-id="64316-122">**DatabaseID**</span><span class="sxs-lookup"><span data-stu-id="64316-122">**DatabaseID**</span></span>|<span data-ttu-id="64316-123">**int**</span><span class="sxs-lookup"><span data-stu-id="64316-123">**int**</span></span>|<span data-ttu-id="64316-124">由 USE *database* 语句指定的数据库的 ID；如果未对给定实例发出 USE *database* 语句，则为默认数据库的 ID。</span><span class="sxs-lookup"><span data-stu-id="64316-124">ID of the database specified by the USE *database* statement or the default database if no USE *database* statement has been issued for a given instance.</span></span> [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="64316-125">数据列而且服务器可用，则 **ServerName** 将显示数据库名。</span><span class="sxs-lookup"><span data-stu-id="64316-125">displays the name of the database if the **ServerName** data column is captured in the trace and the server is available.</span></span> <span data-ttu-id="64316-126">可使用 DB_ID 函数来确定数据库的值。</span><span class="sxs-lookup"><span data-stu-id="64316-126">Determine the value for a database by using the DB_ID function.</span></span>|<span data-ttu-id="64316-127">3</span><span class="sxs-lookup"><span data-stu-id="64316-127">3</span></span>|<span data-ttu-id="64316-128">是</span><span class="sxs-lookup"><span data-stu-id="64316-128">Yes</span></span>|  
|<span data-ttu-id="64316-129">**DatabaseName**</span><span class="sxs-lookup"><span data-stu-id="64316-129">**DatabaseName**</span></span>|<span data-ttu-id="64316-130">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="64316-130">**nvarchar**</span></span>|<span data-ttu-id="64316-131">正在其中运行用户语句的数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="64316-131">Name of the database in which the user statement is running.</span></span>|<span data-ttu-id="64316-132">35</span><span class="sxs-lookup"><span data-stu-id="64316-132">35</span></span>|<span data-ttu-id="64316-133">是</span><span class="sxs-lookup"><span data-stu-id="64316-133">Yes</span></span>|  
|<span data-ttu-id="64316-134">**DBUserName**</span><span class="sxs-lookup"><span data-stu-id="64316-134">**DBUserName**</span></span>|<span data-ttu-id="64316-135">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="64316-135">**nvarchar**</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="64316-136">用户名。</span><span class="sxs-lookup"><span data-stu-id="64316-136">user name of the client.</span></span>|<span data-ttu-id="64316-137">40</span><span class="sxs-lookup"><span data-stu-id="64316-137">40</span></span>|<span data-ttu-id="64316-138">是</span><span class="sxs-lookup"><span data-stu-id="64316-138">Yes</span></span>|  
|<span data-ttu-id="64316-139">**EventClass**</span><span class="sxs-lookup"><span data-stu-id="64316-139">**EventClass**</span></span>|<span data-ttu-id="64316-140">**int**</span><span class="sxs-lookup"><span data-stu-id="64316-140">**int**</span></span>|<span data-ttu-id="64316-141">事件的类型为 171</span><span class="sxs-lookup"><span data-stu-id="64316-141">Type of event=171</span></span>|<span data-ttu-id="64316-142">27</span><span class="sxs-lookup"><span data-stu-id="64316-142">27</span></span>|<span data-ttu-id="64316-143">否</span><span class="sxs-lookup"><span data-stu-id="64316-143">No</span></span>|  
|<span data-ttu-id="64316-144">**EventSequence**</span><span class="sxs-lookup"><span data-stu-id="64316-144">**EventSequence**</span></span>|<span data-ttu-id="64316-145">**int**</span><span class="sxs-lookup"><span data-stu-id="64316-145">**int**</span></span>|<span data-ttu-id="64316-146">给定事件在请求中的顺序。</span><span class="sxs-lookup"><span data-stu-id="64316-146">Sequence of a given event within the request.</span></span>|<span data-ttu-id="64316-147">51</span><span class="sxs-lookup"><span data-stu-id="64316-147">51</span></span>|<span data-ttu-id="64316-148">否</span><span class="sxs-lookup"><span data-stu-id="64316-148">No</span></span>|  
|<span data-ttu-id="64316-149">**EventSubClass**</span><span class="sxs-lookup"><span data-stu-id="64316-149">**EventSubClass**</span></span>|<span data-ttu-id="64316-150">**int**</span><span class="sxs-lookup"><span data-stu-id="64316-150">**int**</span></span>|<span data-ttu-id="64316-151">事件子类的类型。</span><span class="sxs-lookup"><span data-stu-id="64316-151">Type of event subclass.</span></span><br /><br /> <span data-ttu-id="64316-152">1 = 授予</span><span class="sxs-lookup"><span data-stu-id="64316-152">1=Grant</span></span><br /><br /> <span data-ttu-id="64316-153">2 = 撤消</span><span class="sxs-lookup"><span data-stu-id="64316-153">2=Revoke</span></span><br /><br /> <span data-ttu-id="64316-154">3 = 拒绝</span><span class="sxs-lookup"><span data-stu-id="64316-154">3=Deny</span></span>|<span data-ttu-id="64316-155">21</span><span class="sxs-lookup"><span data-stu-id="64316-155">21</span></span>|<span data-ttu-id="64316-156">是</span><span class="sxs-lookup"><span data-stu-id="64316-156">Yes</span></span>|  
|<span data-ttu-id="64316-157">**HostName**</span><span class="sxs-lookup"><span data-stu-id="64316-157">**HostName**</span></span>|<span data-ttu-id="64316-158">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="64316-158">**nvarchar**</span></span>|<span data-ttu-id="64316-159">正在运行客户端的计算机的名称。</span><span class="sxs-lookup"><span data-stu-id="64316-159">Name of the computer on which the client is running.</span></span> <span data-ttu-id="64316-160">如果客户端提供了主机名，则填充此数据列。</span><span class="sxs-lookup"><span data-stu-id="64316-160">This data column is populated if the client provides the host name.</span></span> <span data-ttu-id="64316-161">若要确定主机名，请使用 HOST_NAME 函数。</span><span class="sxs-lookup"><span data-stu-id="64316-161">To determine the host name, use the HOST_NAME function.</span></span>|<span data-ttu-id="64316-162">8</span><span class="sxs-lookup"><span data-stu-id="64316-162">8</span></span>|<span data-ttu-id="64316-163">是</span><span class="sxs-lookup"><span data-stu-id="64316-163">Yes</span></span>|  
|<span data-ttu-id="64316-164">**IsSystem**</span><span class="sxs-lookup"><span data-stu-id="64316-164">**IsSystem**</span></span>|<span data-ttu-id="64316-165">**int**</span><span class="sxs-lookup"><span data-stu-id="64316-165">**int**</span></span>|<span data-ttu-id="64316-166">指示事件是发生在系统进程中还是发生在用户进程中。</span><span class="sxs-lookup"><span data-stu-id="64316-166">Indicates whether the event occurred on a system process or a user process.</span></span> <span data-ttu-id="64316-167">1 = 系统，0 = 用户。</span><span class="sxs-lookup"><span data-stu-id="64316-167">1 = system, 0 = user.</span></span>|<span data-ttu-id="64316-168">60</span><span class="sxs-lookup"><span data-stu-id="64316-168">60</span></span>|<span data-ttu-id="64316-169">是</span><span class="sxs-lookup"><span data-stu-id="64316-169">Yes</span></span>|  
|<span data-ttu-id="64316-170">**LoginName**</span><span class="sxs-lookup"><span data-stu-id="64316-170">**LoginName**</span></span>|<span data-ttu-id="64316-171">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="64316-171">**nvarchar**</span></span>|<span data-ttu-id="64316-172">用户的登录名（ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安全登录名或 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 登录凭据，格式为“域\用户名”）。</span><span class="sxs-lookup"><span data-stu-id="64316-172">Name of the login of the user (either a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] security login or the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows login credentials in the form of DOMAIN\username).</span></span>|<span data-ttu-id="64316-173">11</span><span class="sxs-lookup"><span data-stu-id="64316-173">11</span></span>|<span data-ttu-id="64316-174">是</span><span class="sxs-lookup"><span data-stu-id="64316-174">Yes</span></span>|  
|<span data-ttu-id="64316-175">**LoginSid**</span><span class="sxs-lookup"><span data-stu-id="64316-175">**LoginSid**</span></span>|<span data-ttu-id="64316-176">**图像**</span><span class="sxs-lookup"><span data-stu-id="64316-176">**image**</span></span>|<span data-ttu-id="64316-177">登录用户的安全标识号 (SID)。</span><span class="sxs-lookup"><span data-stu-id="64316-177">Security identification number (SID) of the logged-in user.</span></span> <span data-ttu-id="64316-178">你可以在 **sys.server_principals** 目录视图中找到此信息。</span><span class="sxs-lookup"><span data-stu-id="64316-178">You can find this information in the **sys.server_principals** catalog view.</span></span> <span data-ttu-id="64316-179">服务器中的每个登录名都具有唯一的 SID。</span><span class="sxs-lookup"><span data-stu-id="64316-179">Each SID is unique for each login in the server.</span></span>|<span data-ttu-id="64316-180">41</span><span class="sxs-lookup"><span data-stu-id="64316-180">41</span></span>|<span data-ttu-id="64316-181">是</span><span class="sxs-lookup"><span data-stu-id="64316-181">Yes</span></span>|  
|<span data-ttu-id="64316-182">**NTDomainName**</span><span class="sxs-lookup"><span data-stu-id="64316-182">**NTDomainName**</span></span>|<span data-ttu-id="64316-183">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="64316-183">**nvarchar**</span></span>|<span data-ttu-id="64316-184">用户所属的 Windows 域。</span><span class="sxs-lookup"><span data-stu-id="64316-184">Windows domain to which the user belongs.</span></span>|<span data-ttu-id="64316-185">7</span><span class="sxs-lookup"><span data-stu-id="64316-185">7</span></span>|<span data-ttu-id="64316-186">是</span><span class="sxs-lookup"><span data-stu-id="64316-186">Yes</span></span>|  
|<span data-ttu-id="64316-187">**NTUserName**</span><span class="sxs-lookup"><span data-stu-id="64316-187">**NTUserName**</span></span>|<span data-ttu-id="64316-188">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="64316-188">**nvarchar**</span></span>|<span data-ttu-id="64316-189">Windows 用户名。</span><span class="sxs-lookup"><span data-stu-id="64316-189">Windows user name.</span></span>|<span data-ttu-id="64316-190">6</span><span class="sxs-lookup"><span data-stu-id="64316-190">6</span></span>|<span data-ttu-id="64316-191">是</span><span class="sxs-lookup"><span data-stu-id="64316-191">Yes</span></span>|  
|<span data-ttu-id="64316-192">**ObjectName**</span><span class="sxs-lookup"><span data-stu-id="64316-192">**ObjectName**</span></span>|<span data-ttu-id="64316-193">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="64316-193">**nvarchar**</span></span>|<span data-ttu-id="64316-194">引用的对象名。</span><span class="sxs-lookup"><span data-stu-id="64316-194">Name of the object being referenced.</span></span>|<span data-ttu-id="64316-195">34</span><span class="sxs-lookup"><span data-stu-id="64316-195">34</span></span>|<span data-ttu-id="64316-196">是</span><span class="sxs-lookup"><span data-stu-id="64316-196">Yes</span></span>|  
|<span data-ttu-id="64316-197">**ObjectType**</span><span class="sxs-lookup"><span data-stu-id="64316-197">**ObjectType**</span></span>|<span data-ttu-id="64316-198">**int**</span><span class="sxs-lookup"><span data-stu-id="64316-198">**int**</span></span>|<span data-ttu-id="64316-199">表示事件中涉及的对象类型的值。</span><span class="sxs-lookup"><span data-stu-id="64316-199">Value representing the type of the object involved in the event.</span></span> <span data-ttu-id="64316-200">此值对应于 **sys.objects** 目录视图中的类型列。</span><span class="sxs-lookup"><span data-stu-id="64316-200">This value corresponds to the type column in the **sys.objects** catalog view.</span></span> <span data-ttu-id="64316-201">有关值的信息，请参阅 [ObjectType 跟踪事件列](objecttype-trace-event-column.md)。</span><span class="sxs-lookup"><span data-stu-id="64316-201">For values, see [ObjectType Trace Event Column](objecttype-trace-event-column.md).</span></span>|<span data-ttu-id="64316-202">28</span><span class="sxs-lookup"><span data-stu-id="64316-202">28</span></span>|<span data-ttu-id="64316-203">是</span><span class="sxs-lookup"><span data-stu-id="64316-203">Yes</span></span>|  
|<span data-ttu-id="64316-204">**OwnerName**</span><span class="sxs-lookup"><span data-stu-id="64316-204">**OwnerName**</span></span>|<span data-ttu-id="64316-205">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="64316-205">**nvarchar**</span></span>|<span data-ttu-id="64316-206">对象所有者的数据库用户名。</span><span class="sxs-lookup"><span data-stu-id="64316-206">Database user name of the object owner.</span></span>|<span data-ttu-id="64316-207">37</span><span class="sxs-lookup"><span data-stu-id="64316-207">37</span></span>|<span data-ttu-id="64316-208">是</span><span class="sxs-lookup"><span data-stu-id="64316-208">Yes</span></span>|  
|<span data-ttu-id="64316-209">**权限**</span><span class="sxs-lookup"><span data-stu-id="64316-209">**Permissions**</span></span>|<span data-ttu-id="64316-210">**bigint**</span><span class="sxs-lookup"><span data-stu-id="64316-210">**bigint**</span></span>|<span data-ttu-id="64316-211">表示所检查的权限类型的整型值。</span><span class="sxs-lookup"><span data-stu-id="64316-211">Integer value representing the type of permissions checked.</span></span><br /><br /> <span data-ttu-id="64316-212">1 = SELECT ALL</span><span class="sxs-lookup"><span data-stu-id="64316-212">1 = SELECT ALL</span></span><br /><br /> <span data-ttu-id="64316-213">2 = UPDATE ALL</span><span class="sxs-lookup"><span data-stu-id="64316-213">2 = UPDATE ALL</span></span><br /><br /> <span data-ttu-id="64316-214">4 = REFERENCES ALL</span><span class="sxs-lookup"><span data-stu-id="64316-214">4 = REFERENCES ALL</span></span><br /><br /> <span data-ttu-id="64316-215">8 = INSERT</span><span class="sxs-lookup"><span data-stu-id="64316-215">8 = INSERT</span></span><br /><br /> <span data-ttu-id="64316-216">16 = DELETE</span><span class="sxs-lookup"><span data-stu-id="64316-216">16 = DELETE</span></span><br /><br /> <span data-ttu-id="64316-217">32 = EXECUTE（仅限于过程）</span><span class="sxs-lookup"><span data-stu-id="64316-217">32 = EXECUTE (procedures only)</span></span><br /><br /> <span data-ttu-id="64316-218">4096 = SELECT ANY（至少一列）</span><span class="sxs-lookup"><span data-stu-id="64316-218">4096 = SELECT ANY (at least one column)</span></span><br /><br /> <span data-ttu-id="64316-219">8192 = UPDATE ANY</span><span class="sxs-lookup"><span data-stu-id="64316-219">8192 = UPDATE ANY</span></span>|<span data-ttu-id="64316-220">19</span><span class="sxs-lookup"><span data-stu-id="64316-220">19</span></span>|<span data-ttu-id="64316-221">是</span><span class="sxs-lookup"><span data-stu-id="64316-221">Yes</span></span>|  
|<span data-ttu-id="64316-222">**RequestID**</span><span class="sxs-lookup"><span data-stu-id="64316-222">**RequestID**</span></span>|<span data-ttu-id="64316-223">**int**</span><span class="sxs-lookup"><span data-stu-id="64316-223">**int**</span></span>|<span data-ttu-id="64316-224">包含该语句的请求的 ID。</span><span class="sxs-lookup"><span data-stu-id="64316-224">ID of the request containing the statement.</span></span>|<span data-ttu-id="64316-225">49</span><span class="sxs-lookup"><span data-stu-id="64316-225">49</span></span>|<span data-ttu-id="64316-226">是</span><span class="sxs-lookup"><span data-stu-id="64316-226">Yes</span></span>|  
|<span data-ttu-id="64316-227">**ServerName**</span><span class="sxs-lookup"><span data-stu-id="64316-227">**ServerName**</span></span>|<span data-ttu-id="64316-228">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="64316-228">**nvarchar**</span></span>|<span data-ttu-id="64316-229">所跟踪的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例的名称。</span><span class="sxs-lookup"><span data-stu-id="64316-229">Name of the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] being traced.</span></span>|<span data-ttu-id="64316-230">26</span><span class="sxs-lookup"><span data-stu-id="64316-230">26</span></span>|<span data-ttu-id="64316-231">否</span><span class="sxs-lookup"><span data-stu-id="64316-231">No</span></span>|  
|<span data-ttu-id="64316-232">**SessionLoginName**</span><span class="sxs-lookup"><span data-stu-id="64316-232">**SessionLoginName**</span></span>|<span data-ttu-id="64316-233">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="64316-233">**nvarchar**</span></span>|<span data-ttu-id="64316-234">发起会话的用户的登录名。</span><span class="sxs-lookup"><span data-stu-id="64316-234">Login name of the user who originated the session.</span></span> <span data-ttu-id="64316-235">例如，如果你使用 Login1 连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，再以 Login2 的身份执行语句，则 **SessionLoginName** 将显示 Login1，而 **LoginName** 将显示 Login2。</span><span class="sxs-lookup"><span data-stu-id="64316-235">For example, if you connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using Login1 and execute a statement as Login2, **SessionLoginName** shows Login1 and **LoginName** shows Login2.</span></span> <span data-ttu-id="64316-236">此列将同时显示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名和 Windows 登录名。</span><span class="sxs-lookup"><span data-stu-id="64316-236">This column displays both [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and Windows logins.</span></span>|<span data-ttu-id="64316-237">64</span><span class="sxs-lookup"><span data-stu-id="64316-237">64</span></span>|<span data-ttu-id="64316-238">是</span><span class="sxs-lookup"><span data-stu-id="64316-238">Yes</span></span>|  
|<span data-ttu-id="64316-239">**SPID**</span><span class="sxs-lookup"><span data-stu-id="64316-239">**SPID**</span></span>|<span data-ttu-id="64316-240">**int**</span><span class="sxs-lookup"><span data-stu-id="64316-240">**int**</span></span>|<span data-ttu-id="64316-241">发生该事件的会话的 ID。</span><span class="sxs-lookup"><span data-stu-id="64316-241">ID of the session on which the event occurred.</span></span>|<span data-ttu-id="64316-242">12</span><span class="sxs-lookup"><span data-stu-id="64316-242">12</span></span>|<span data-ttu-id="64316-243">是</span><span class="sxs-lookup"><span data-stu-id="64316-243">Yes</span></span>|  
|<span data-ttu-id="64316-244">**StartTime**</span><span class="sxs-lookup"><span data-stu-id="64316-244">**StartTime**</span></span>|<span data-ttu-id="64316-245">**datetime**</span><span class="sxs-lookup"><span data-stu-id="64316-245">**datetime**</span></span>|<span data-ttu-id="64316-246">该事件（如果存在）的启动时间。</span><span class="sxs-lookup"><span data-stu-id="64316-246">Time at which the event started, if available.</span></span>|<span data-ttu-id="64316-247">14</span><span class="sxs-lookup"><span data-stu-id="64316-247">14</span></span>|<span data-ttu-id="64316-248">是</span><span class="sxs-lookup"><span data-stu-id="64316-248">Yes</span></span>|  
|<span data-ttu-id="64316-249">**Success**</span><span class="sxs-lookup"><span data-stu-id="64316-249">**Success**</span></span>|<span data-ttu-id="64316-250">**int**</span><span class="sxs-lookup"><span data-stu-id="64316-250">**int**</span></span>|<span data-ttu-id="64316-251">1 = 成功。</span><span class="sxs-lookup"><span data-stu-id="64316-251">1 = success.</span></span> <span data-ttu-id="64316-252">0 = 失败。</span><span class="sxs-lookup"><span data-stu-id="64316-252">0 = failure.</span></span> <span data-ttu-id="64316-253">例如，值为 1 时表示权限检查成功；值为 0 时表示权限检查失败。</span><span class="sxs-lookup"><span data-stu-id="64316-253">For example, a value of 1 indicates success of a permissions check and a value of 0 indicates failure of that check.</span></span>|<span data-ttu-id="64316-254">23</span><span class="sxs-lookup"><span data-stu-id="64316-254">23</span></span>|<span data-ttu-id="64316-255">是</span><span class="sxs-lookup"><span data-stu-id="64316-255">Yes</span></span>|  
|<span data-ttu-id="64316-256">**TargetLoginName**</span><span class="sxs-lookup"><span data-stu-id="64316-256">**TargetLoginName**</span></span>|<span data-ttu-id="64316-257">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="64316-257">**nvarchar**</span></span>|<span data-ttu-id="64316-258">如果是针对登录的操作（例如，添加新的登录），则为所针对登录的名称。</span><span class="sxs-lookup"><span data-stu-id="64316-258">For actions that target a login (for example, adding a new login), the name of the targeted login.</span></span>|<span data-ttu-id="64316-259">42</span><span class="sxs-lookup"><span data-stu-id="64316-259">42</span></span>|<span data-ttu-id="64316-260">是</span><span class="sxs-lookup"><span data-stu-id="64316-260">Yes</span></span>|  
|<span data-ttu-id="64316-261">**TargetLoginSid**</span><span class="sxs-lookup"><span data-stu-id="64316-261">**TargetLoginSid**</span></span>|<span data-ttu-id="64316-262">**图像**</span><span class="sxs-lookup"><span data-stu-id="64316-262">**image**</span></span>|<span data-ttu-id="64316-263">如果是针对登录的操作（例如，添加新的登录），则为所针对登录的安全标识号 (SID)。</span><span class="sxs-lookup"><span data-stu-id="64316-263">For actions that target a login (for example, adding a new login), the security identification number (SID) of the targeted login.</span></span>|<span data-ttu-id="64316-264">43</span><span class="sxs-lookup"><span data-stu-id="64316-264">43</span></span>|<span data-ttu-id="64316-265">是</span><span class="sxs-lookup"><span data-stu-id="64316-265">Yes</span></span>|  
|<span data-ttu-id="64316-266">**TextData**</span><span class="sxs-lookup"><span data-stu-id="64316-266">**TextData**</span></span>|<span data-ttu-id="64316-267">**ntext**</span><span class="sxs-lookup"><span data-stu-id="64316-267">**ntext**</span></span>|<span data-ttu-id="64316-268">依赖于跟踪中捕获的事件类的文本值。</span><span class="sxs-lookup"><span data-stu-id="64316-268">Text value dependent on the event class captured in the trace.</span></span>|<span data-ttu-id="64316-269">1</span><span class="sxs-lookup"><span data-stu-id="64316-269">1</span></span>|<span data-ttu-id="64316-270">是</span><span class="sxs-lookup"><span data-stu-id="64316-270">Yes</span></span>|  
|<span data-ttu-id="64316-271">**TransactionID**</span><span class="sxs-lookup"><span data-stu-id="64316-271">**TransactionID**</span></span>|<span data-ttu-id="64316-272">**bigint**</span><span class="sxs-lookup"><span data-stu-id="64316-272">**bigint**</span></span>|<span data-ttu-id="64316-273">系统分配的事务 ID。</span><span class="sxs-lookup"><span data-stu-id="64316-273">System-assigned ID of the transaction.</span></span>|<span data-ttu-id="64316-274">4</span><span class="sxs-lookup"><span data-stu-id="64316-274">4</span></span>|<span data-ttu-id="64316-275">是</span><span class="sxs-lookup"><span data-stu-id="64316-275">Yes</span></span>|  
|<span data-ttu-id="64316-276">**XactSequence**</span><span class="sxs-lookup"><span data-stu-id="64316-276">**XactSequence**</span></span>|<span data-ttu-id="64316-277">**bigint**</span><span class="sxs-lookup"><span data-stu-id="64316-277">**bigint**</span></span>|<span data-ttu-id="64316-278">用于说明当前事务的标记。</span><span class="sxs-lookup"><span data-stu-id="64316-278">Token used to describe the current transaction.</span></span>|<span data-ttu-id="64316-279">50</span><span class="sxs-lookup"><span data-stu-id="64316-279">50</span></span>|<span data-ttu-id="64316-280">是</span><span class="sxs-lookup"><span data-stu-id="64316-280">Yes</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="64316-281">另请参阅</span><span class="sxs-lookup"><span data-stu-id="64316-281">See Also</span></span>  
 <span data-ttu-id="64316-282">[SQL Server 事件探查器](../../tools/sql-server-profiler/sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="64316-282">[SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md) </span></span>  
 <span data-ttu-id="64316-283">[sp_trace_setevent (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="64316-283">[sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql) </span></span>  
 <span data-ttu-id="64316-284">[GRANT (Transact-SQL)](/sql/t-sql/statements/grant-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="64316-284">[GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql) </span></span>  
 <span data-ttu-id="64316-285">[REVOKE (Transact-SQL)](/sql/t-sql/statements/revoke-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="64316-285">[REVOKE &#40;Transact-SQL&#41;](/sql/t-sql/statements/revoke-transact-sql) </span></span>  
 [<span data-ttu-id="64316-286">DENY (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="64316-286">DENY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/deny-transact-sql)  
  
  