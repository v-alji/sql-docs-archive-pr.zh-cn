---
title: Audit Change Database Owner 事件类 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Audit Change Database Owner event class
ms.assetid: 2f1dd4fc-2540-423c-80ad-c5bc712c42e0
author: stevestein
ms.author: sstein
ms.openlocfilehash: 11f3a12c892a76277063827393b682809478ce46
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689904"
---
# <a name="audit-change-database-owner-event-class"></a><span data-ttu-id="e06a8-102">Audit Change Database Owner 事件类</span><span class="sxs-lookup"><span data-stu-id="e06a8-102">Audit Change Database Owner Event Class</span></span>
  <span data-ttu-id="e06a8-103">当您使用 ALTER AUTHORIZATION 语句更改数据库的所有者时，将发生 **Audit Change Database Owner** 事件类，并检查该操作所需的权限。</span><span class="sxs-lookup"><span data-stu-id="e06a8-103">The **Audit Change Database Owner** event class occurs when you use the ALTER AUTHORIZATION statement to change the owner of a database, and the permissions required to do that are checked.</span></span>  
  
## <a name="audit-change-database-owner-event-class-data-columns"></a><span data-ttu-id="e06a8-104">Audit Change Database Owner 事件类的数据列</span><span class="sxs-lookup"><span data-stu-id="e06a8-104">Audit Change Database Owner Event Class Data Columns</span></span>  
  
|<span data-ttu-id="e06a8-105">数据列名称</span><span class="sxs-lookup"><span data-stu-id="e06a8-105">Data column name</span></span>|<span data-ttu-id="e06a8-106">数据类型</span><span class="sxs-lookup"><span data-stu-id="e06a8-106">Data type</span></span>|<span data-ttu-id="e06a8-107">说明</span><span class="sxs-lookup"><span data-stu-id="e06a8-107">Description</span></span>|<span data-ttu-id="e06a8-108">列 ID</span><span class="sxs-lookup"><span data-stu-id="e06a8-108">Column ID</span></span>|<span data-ttu-id="e06a8-109">可筛选</span><span class="sxs-lookup"><span data-stu-id="e06a8-109">Filterable</span></span>|  
|----------------------|---------------|-----------------|---------------|----------------|  
|<span data-ttu-id="e06a8-110">ApplicationName </span><span class="sxs-lookup"><span data-stu-id="e06a8-110">**ApplicationName**</span></span>|<span data-ttu-id="e06a8-111">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="e06a8-111">**nvarchar**</span></span>|<span data-ttu-id="e06a8-112">与 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例建立连接的客户端应用程序的名称。</span><span class="sxs-lookup"><span data-stu-id="e06a8-112">Name of the client application that created the connection to an instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="e06a8-113">此列由应用程序传递的值填充，而不是由所显示的程序名填充。</span><span class="sxs-lookup"><span data-stu-id="e06a8-113">This column is populated with the values passed by the application rather than the displayed name of the program.</span></span>|<span data-ttu-id="e06a8-114">10</span><span class="sxs-lookup"><span data-stu-id="e06a8-114">10</span></span>|<span data-ttu-id="e06a8-115">是</span><span class="sxs-lookup"><span data-stu-id="e06a8-115">Yes</span></span>|  
|<span data-ttu-id="e06a8-116">**ClientProcessID**</span><span class="sxs-lookup"><span data-stu-id="e06a8-116">**ClientProcessID**</span></span>|<span data-ttu-id="e06a8-117">**int**</span><span class="sxs-lookup"><span data-stu-id="e06a8-117">**int**</span></span>|<span data-ttu-id="e06a8-118">主机为运行该客户端应用程序的进程分配的 ID。</span><span class="sxs-lookup"><span data-stu-id="e06a8-118">ID assigned by the host computer to the process where the client application is running.</span></span> <span data-ttu-id="e06a8-119">如果客户端提供了客户端进程 ID，则填充此数据列。</span><span class="sxs-lookup"><span data-stu-id="e06a8-119">This data column is populated if the client provides the client process ID.</span></span>|<span data-ttu-id="e06a8-120">9</span><span class="sxs-lookup"><span data-stu-id="e06a8-120">9</span></span>|<span data-ttu-id="e06a8-121">是</span><span class="sxs-lookup"><span data-stu-id="e06a8-121">Yes</span></span>|  
|<span data-ttu-id="e06a8-122">**DatabaseID**</span><span class="sxs-lookup"><span data-stu-id="e06a8-122">**DatabaseID**</span></span>|<span data-ttu-id="e06a8-123">**int**</span><span class="sxs-lookup"><span data-stu-id="e06a8-123">**int**</span></span>|<span data-ttu-id="e06a8-124">由 USE *database* 语句指定的数据库的 ID；如果未对给定实例发出 USE *database* 语句，则为默认数据库的 ID。</span><span class="sxs-lookup"><span data-stu-id="e06a8-124">ID of the database specified by the USE *database* statement or the default database if no USE *database* statement has been issued for a given instance.</span></span> [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="e06a8-125">数据列而且服务器可用，则 **ServerName** 将显示数据库名。</span><span class="sxs-lookup"><span data-stu-id="e06a8-125">displays the name of the database if the **ServerName** data column is captured in the trace and the server is available.</span></span> <span data-ttu-id="e06a8-126">可使用 DB_ID 函数来确定数据库的值。</span><span class="sxs-lookup"><span data-stu-id="e06a8-126">Determine the value for a database by using the DB_ID function.</span></span>|<span data-ttu-id="e06a8-127">3</span><span class="sxs-lookup"><span data-stu-id="e06a8-127">3</span></span>|<span data-ttu-id="e06a8-128">是</span><span class="sxs-lookup"><span data-stu-id="e06a8-128">Yes</span></span>|  
|<span data-ttu-id="e06a8-129">**DatabaseName**</span><span class="sxs-lookup"><span data-stu-id="e06a8-129">**DatabaseName**</span></span>|<span data-ttu-id="e06a8-130">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="e06a8-130">**nvarchar**</span></span>|<span data-ttu-id="e06a8-131">正在其中运行用户语句的数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="e06a8-131">Name of the database in which the user statement is running.</span></span>|<span data-ttu-id="e06a8-132">35</span><span class="sxs-lookup"><span data-stu-id="e06a8-132">35</span></span>|<span data-ttu-id="e06a8-133">是</span><span class="sxs-lookup"><span data-stu-id="e06a8-133">Yes</span></span>|  
|<span data-ttu-id="e06a8-134">**DBUserName**</span><span class="sxs-lookup"><span data-stu-id="e06a8-134">**DBUserName**</span></span>|<span data-ttu-id="e06a8-135">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="e06a8-135">**nvarchar**</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="e06a8-136">用户名。</span><span class="sxs-lookup"><span data-stu-id="e06a8-136">user name of the client.</span></span>|<span data-ttu-id="e06a8-137">40</span><span class="sxs-lookup"><span data-stu-id="e06a8-137">40</span></span>|<span data-ttu-id="e06a8-138">是</span><span class="sxs-lookup"><span data-stu-id="e06a8-138">Yes</span></span>|  
|<span data-ttu-id="e06a8-139">**EventClass**</span><span class="sxs-lookup"><span data-stu-id="e06a8-139">**EventClass**</span></span>|<span data-ttu-id="e06a8-140">**int**</span><span class="sxs-lookup"><span data-stu-id="e06a8-140">**int**</span></span>|<span data-ttu-id="e06a8-141">事件类型 = 152。</span><span class="sxs-lookup"><span data-stu-id="e06a8-141">Type of event = 152.</span></span>|<span data-ttu-id="e06a8-142">27</span><span class="sxs-lookup"><span data-stu-id="e06a8-142">27</span></span>|<span data-ttu-id="e06a8-143">否</span><span class="sxs-lookup"><span data-stu-id="e06a8-143">No</span></span>|  
|<span data-ttu-id="e06a8-144">**EventSequence**</span><span class="sxs-lookup"><span data-stu-id="e06a8-144">**EventSequence**</span></span>|<span data-ttu-id="e06a8-145">**int**</span><span class="sxs-lookup"><span data-stu-id="e06a8-145">**int**</span></span>|<span data-ttu-id="e06a8-146">给定事件在请求中的顺序。</span><span class="sxs-lookup"><span data-stu-id="e06a8-146">Sequence of a given event within the request.</span></span>|<span data-ttu-id="e06a8-147">51</span><span class="sxs-lookup"><span data-stu-id="e06a8-147">51</span></span>|<span data-ttu-id="e06a8-148">否</span><span class="sxs-lookup"><span data-stu-id="e06a8-148">No</span></span>|  
|<span data-ttu-id="e06a8-149">**HostName**</span><span class="sxs-lookup"><span data-stu-id="e06a8-149">**HostName**</span></span>|<span data-ttu-id="e06a8-150">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="e06a8-150">**nvarchar**</span></span>|<span data-ttu-id="e06a8-151">正在运行客户端的计算机的名称。</span><span class="sxs-lookup"><span data-stu-id="e06a8-151">Name of the computer on which the client is running.</span></span> <span data-ttu-id="e06a8-152">如果客户端提供了主机名，则填充此数据列。</span><span class="sxs-lookup"><span data-stu-id="e06a8-152">This data column is populated if the client provides the host name.</span></span> <span data-ttu-id="e06a8-153">若要确定主机名，请使用 HOST_NAME 函数。</span><span class="sxs-lookup"><span data-stu-id="e06a8-153">To determine the host name, use the HOST_NAME function.</span></span>|<span data-ttu-id="e06a8-154">8</span><span class="sxs-lookup"><span data-stu-id="e06a8-154">8</span></span>|<span data-ttu-id="e06a8-155">是</span><span class="sxs-lookup"><span data-stu-id="e06a8-155">Yes</span></span>|  
|<span data-ttu-id="e06a8-156">**IsSystem**</span><span class="sxs-lookup"><span data-stu-id="e06a8-156">**IsSystem**</span></span>|<span data-ttu-id="e06a8-157">**int**</span><span class="sxs-lookup"><span data-stu-id="e06a8-157">**int**</span></span>|<span data-ttu-id="e06a8-158">指示事件是发生在系统进程中还是发生在用户进程中。</span><span class="sxs-lookup"><span data-stu-id="e06a8-158">Indicates whether the event occurred on a system process or a user process.</span></span> <span data-ttu-id="e06a8-159">1 = 系统，0 = 用户。</span><span class="sxs-lookup"><span data-stu-id="e06a8-159">1 = system, 0 = user.</span></span>|<span data-ttu-id="e06a8-160">60</span><span class="sxs-lookup"><span data-stu-id="e06a8-160">60</span></span>|<span data-ttu-id="e06a8-161">是</span><span class="sxs-lookup"><span data-stu-id="e06a8-161">Yes</span></span>|  
|<span data-ttu-id="e06a8-162">**LoginName**</span><span class="sxs-lookup"><span data-stu-id="e06a8-162">**LoginName**</span></span>|<span data-ttu-id="e06a8-163">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="e06a8-163">**nvarchar**</span></span>|<span data-ttu-id="e06a8-164">用户的登录名（ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安全登录名或 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 登录凭据，格式为“DOMAIN\username”）。</span><span class="sxs-lookup"><span data-stu-id="e06a8-164">Name of the login of the user (either the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] security login or the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows login credentials in the form of DOMAIN\username).</span></span>|<span data-ttu-id="e06a8-165">11</span><span class="sxs-lookup"><span data-stu-id="e06a8-165">11</span></span>|<span data-ttu-id="e06a8-166">是</span><span class="sxs-lookup"><span data-stu-id="e06a8-166">Yes</span></span>|  
|<span data-ttu-id="e06a8-167">**LoginSid**</span><span class="sxs-lookup"><span data-stu-id="e06a8-167">**LoginSid**</span></span>|<span data-ttu-id="e06a8-168">**图像**</span><span class="sxs-lookup"><span data-stu-id="e06a8-168">**image**</span></span>|<span data-ttu-id="e06a8-169">登录用户的安全标识号 (SID)。</span><span class="sxs-lookup"><span data-stu-id="e06a8-169">Security identification number (SID) of the logged-in user.</span></span> <span data-ttu-id="e06a8-170">你可以在 **sys.server_principals** 目录视图中找到此信息。</span><span class="sxs-lookup"><span data-stu-id="e06a8-170">You can find this information in the **sys.server_principals** catalog view.</span></span> <span data-ttu-id="e06a8-171">服务器中的每个登录名都具有唯一的 SID。</span><span class="sxs-lookup"><span data-stu-id="e06a8-171">Each SID is unique for each login in the server.</span></span>|<span data-ttu-id="e06a8-172">41</span><span class="sxs-lookup"><span data-stu-id="e06a8-172">41</span></span>|<span data-ttu-id="e06a8-173">是</span><span class="sxs-lookup"><span data-stu-id="e06a8-173">Yes</span></span>|  
|<span data-ttu-id="e06a8-174">**NTDomainName**</span><span class="sxs-lookup"><span data-stu-id="e06a8-174">**NTDomainName**</span></span>|<span data-ttu-id="e06a8-175">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="e06a8-175">**nvarchar**</span></span>|<span data-ttu-id="e06a8-176">用户所属的 Windows 域。</span><span class="sxs-lookup"><span data-stu-id="e06a8-176">Windows domain to which the user belongs.</span></span>|<span data-ttu-id="e06a8-177">7</span><span class="sxs-lookup"><span data-stu-id="e06a8-177">7</span></span>|<span data-ttu-id="e06a8-178">是</span><span class="sxs-lookup"><span data-stu-id="e06a8-178">Yes</span></span>|  
|<span data-ttu-id="e06a8-179">**NTUserName**</span><span class="sxs-lookup"><span data-stu-id="e06a8-179">**NTUserName**</span></span>|<span data-ttu-id="e06a8-180">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="e06a8-180">**nvarchar**</span></span>|<span data-ttu-id="e06a8-181">Windows 用户名。</span><span class="sxs-lookup"><span data-stu-id="e06a8-181">Windows user name.</span></span>|<span data-ttu-id="e06a8-182">6</span><span class="sxs-lookup"><span data-stu-id="e06a8-182">6</span></span>|<span data-ttu-id="e06a8-183">是</span><span class="sxs-lookup"><span data-stu-id="e06a8-183">Yes</span></span>|  
|<span data-ttu-id="e06a8-184">**RequestID**</span><span class="sxs-lookup"><span data-stu-id="e06a8-184">**RequestID**</span></span>|<span data-ttu-id="e06a8-185">**int**</span><span class="sxs-lookup"><span data-stu-id="e06a8-185">**int**</span></span>|<span data-ttu-id="e06a8-186">包含该语句的请求的 ID。</span><span class="sxs-lookup"><span data-stu-id="e06a8-186">ID of the request containing the statement.</span></span>|<span data-ttu-id="e06a8-187">49</span><span class="sxs-lookup"><span data-stu-id="e06a8-187">49</span></span>|<span data-ttu-id="e06a8-188">是</span><span class="sxs-lookup"><span data-stu-id="e06a8-188">Yes</span></span>|  
|<span data-ttu-id="e06a8-189">**ServerName**</span><span class="sxs-lookup"><span data-stu-id="e06a8-189">**ServerName**</span></span>|<span data-ttu-id="e06a8-190">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="e06a8-190">**nvarchar**</span></span>|<span data-ttu-id="e06a8-191">所跟踪的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例的名称。</span><span class="sxs-lookup"><span data-stu-id="e06a8-191">Name of the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] being traced.</span></span>|<span data-ttu-id="e06a8-192">26</span><span class="sxs-lookup"><span data-stu-id="e06a8-192">26</span></span>|<span data-ttu-id="e06a8-193">否</span><span class="sxs-lookup"><span data-stu-id="e06a8-193">No</span></span>|  
|<span data-ttu-id="e06a8-194">**SessionLoginName**</span><span class="sxs-lookup"><span data-stu-id="e06a8-194">**SessionLoginName**</span></span>|<span data-ttu-id="e06a8-195">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="e06a8-195">**nvarchar**</span></span>|<span data-ttu-id="e06a8-196">发起会话的用户的登录名。</span><span class="sxs-lookup"><span data-stu-id="e06a8-196">Login name of the user who originated the session.</span></span> <span data-ttu-id="e06a8-197">例如，如果你使用 Login1 连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，再以 Login2 的身份执行语句，则 **SessionLoginName** 将显示 Login1，而 **LoginName** 将显示 Login2。</span><span class="sxs-lookup"><span data-stu-id="e06a8-197">For example, if you connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using Login1 and execute a statement as Login2, **SessionLoginName** shows Login1 and **LoginName** shows Login2.</span></span> <span data-ttu-id="e06a8-198">此列将同时显示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名和 Windows 登录名。</span><span class="sxs-lookup"><span data-stu-id="e06a8-198">This column displays both [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and Windows logins.</span></span>|<span data-ttu-id="e06a8-199">64</span><span class="sxs-lookup"><span data-stu-id="e06a8-199">64</span></span>|<span data-ttu-id="e06a8-200">是</span><span class="sxs-lookup"><span data-stu-id="e06a8-200">Yes</span></span>|  
|<span data-ttu-id="e06a8-201">**SPID**</span><span class="sxs-lookup"><span data-stu-id="e06a8-201">**SPID**</span></span>|<span data-ttu-id="e06a8-202">**int**</span><span class="sxs-lookup"><span data-stu-id="e06a8-202">**int**</span></span>|<span data-ttu-id="e06a8-203">触发事件的会话 ID。</span><span class="sxs-lookup"><span data-stu-id="e06a8-203">ID of the session on which the even occurred.</span></span>|<span data-ttu-id="e06a8-204">12</span><span class="sxs-lookup"><span data-stu-id="e06a8-204">12</span></span>|<span data-ttu-id="e06a8-205">是</span><span class="sxs-lookup"><span data-stu-id="e06a8-205">Yes</span></span>|  
|<span data-ttu-id="e06a8-206">**StartTime**</span><span class="sxs-lookup"><span data-stu-id="e06a8-206">**StartTime**</span></span>|<span data-ttu-id="e06a8-207">**datetime**</span><span class="sxs-lookup"><span data-stu-id="e06a8-207">**datetime**</span></span>|<span data-ttu-id="e06a8-208">该事件（如果存在）的启动时间。</span><span class="sxs-lookup"><span data-stu-id="e06a8-208">Time at which the event started, if available.</span></span>|<span data-ttu-id="e06a8-209">14</span><span class="sxs-lookup"><span data-stu-id="e06a8-209">14</span></span>|<span data-ttu-id="e06a8-210">是</span><span class="sxs-lookup"><span data-stu-id="e06a8-210">Yes</span></span>|  
|<span data-ttu-id="e06a8-211">**Success**</span><span class="sxs-lookup"><span data-stu-id="e06a8-211">**Success**</span></span>|<span data-ttu-id="e06a8-212">**int**</span><span class="sxs-lookup"><span data-stu-id="e06a8-212">**int**</span></span>|<span data-ttu-id="e06a8-213">1 = 成功。</span><span class="sxs-lookup"><span data-stu-id="e06a8-213">1 = success.</span></span> <span data-ttu-id="e06a8-214">0 = 失败。</span><span class="sxs-lookup"><span data-stu-id="e06a8-214">0 = failure.</span></span> <span data-ttu-id="e06a8-215">例如，值为 1 表示权限检查成功，值为 0 表示该检查失败。</span><span class="sxs-lookup"><span data-stu-id="e06a8-215">For example, a value of 1 indicates success of a permissions check and a value of 0 indicates a failure of that check).</span></span>|<span data-ttu-id="e06a8-216">23</span><span class="sxs-lookup"><span data-stu-id="e06a8-216">23</span></span>|<span data-ttu-id="e06a8-217">是</span><span class="sxs-lookup"><span data-stu-id="e06a8-217">Yes</span></span>|  
|<span data-ttu-id="e06a8-218">**TargetLoginName**</span><span class="sxs-lookup"><span data-stu-id="e06a8-218">**TargetLoginName**</span></span>|<span data-ttu-id="e06a8-219">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="e06a8-219">**nvarchar**</span></span>|<span data-ttu-id="e06a8-220">对于以登录为目标的操作，是目标登录的名称。</span><span class="sxs-lookup"><span data-stu-id="e06a8-220">For actions that target a login, the name of the targeted login.</span></span>|<span data-ttu-id="e06a8-221">42</span><span class="sxs-lookup"><span data-stu-id="e06a8-221">42</span></span>|<span data-ttu-id="e06a8-222">是</span><span class="sxs-lookup"><span data-stu-id="e06a8-222">Yes</span></span>|  
|<span data-ttu-id="e06a8-223">**TargetLoginSid**</span><span class="sxs-lookup"><span data-stu-id="e06a8-223">**TargetLoginSid**</span></span>|<span data-ttu-id="e06a8-224">**图像**</span><span class="sxs-lookup"><span data-stu-id="e06a8-224">**image**</span></span>|<span data-ttu-id="e06a8-225">对于以登录为目标的操作，是目标登录的安全标识号 (SID)。</span><span class="sxs-lookup"><span data-stu-id="e06a8-225">For actions that target a login, the security identification number (SID) of the targeted login.</span></span>|<span data-ttu-id="e06a8-226">43</span><span class="sxs-lookup"><span data-stu-id="e06a8-226">43</span></span>|<span data-ttu-id="e06a8-227">是</span><span class="sxs-lookup"><span data-stu-id="e06a8-227">Yes</span></span>|  
|<span data-ttu-id="e06a8-228">**TargetUserName**</span><span class="sxs-lookup"><span data-stu-id="e06a8-228">**TargetUserName**</span></span>|<span data-ttu-id="e06a8-229">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="e06a8-229">**nvarchar**</span></span>|<span data-ttu-id="e06a8-230">如果是针对某个数据库用户的操作（例如授予用户权限），则为该用户的名称。</span><span class="sxs-lookup"><span data-stu-id="e06a8-230">For actions that target a database user (for example, granting permission to a user), the name of that user.</span></span>|<span data-ttu-id="e06a8-231">39</span><span class="sxs-lookup"><span data-stu-id="e06a8-231">39</span></span>|<span data-ttu-id="e06a8-232">是</span><span class="sxs-lookup"><span data-stu-id="e06a8-232">Yes</span></span>|  
|<span data-ttu-id="e06a8-233">**TransactionID**</span><span class="sxs-lookup"><span data-stu-id="e06a8-233">**TransactionID**</span></span>|<span data-ttu-id="e06a8-234">**bigint**</span><span class="sxs-lookup"><span data-stu-id="e06a8-234">**bigint**</span></span>|<span data-ttu-id="e06a8-235">系统分配的事务 ID。</span><span class="sxs-lookup"><span data-stu-id="e06a8-235">System-assigned ID of the transaction.</span></span>|<span data-ttu-id="e06a8-236">4</span><span class="sxs-lookup"><span data-stu-id="e06a8-236">4</span></span>|<span data-ttu-id="e06a8-237">是</span><span class="sxs-lookup"><span data-stu-id="e06a8-237">Yes</span></span>|  
|<span data-ttu-id="e06a8-238">**XactSequence**</span><span class="sxs-lookup"><span data-stu-id="e06a8-238">**XactSequence**</span></span>|<span data-ttu-id="e06a8-239">**bigint**</span><span class="sxs-lookup"><span data-stu-id="e06a8-239">**bigint**</span></span>|<span data-ttu-id="e06a8-240">用于说明当前事务的标记。</span><span class="sxs-lookup"><span data-stu-id="e06a8-240">Token used to describe the current transaction.</span></span>|<span data-ttu-id="e06a8-241">50</span><span class="sxs-lookup"><span data-stu-id="e06a8-241">50</span></span>|<span data-ttu-id="e06a8-242">是</span><span class="sxs-lookup"><span data-stu-id="e06a8-242">Yes</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e06a8-243">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e06a8-243">See Also</span></span>  
 <span data-ttu-id="e06a8-244">[sp_trace_setevent (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e06a8-244">[sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql) </span></span>  
 [<span data-ttu-id="e06a8-245">ALTER AUTHORIZATION (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="e06a8-245">ALTER AUTHORIZATION &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-authorization-transact-sql)  
  
  