---
title: Audit Change Audit 事件类 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Audit Change Audit event class
ms.assetid: 8cfacc82-cee8-4199-a69e-acedecfc0b3b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 199a3f073e0844489d4e4bbe10e6fb87cd92b48f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689911"
---
# <a name="audit-change-audit-event-class"></a><span data-ttu-id="0308e-102">Audit Change Audit 事件类</span><span class="sxs-lookup"><span data-stu-id="0308e-102">Audit Change Audit Event Class</span></span>
  <span data-ttu-id="0308e-103">只要修改审核跟踪，就会发生 **Audit Change Audit** 事件类。</span><span class="sxs-lookup"><span data-stu-id="0308e-103">The **Audit Change Audit** event class occurs whenever an audit trace modification is made.</span></span>  
  
## <a name="audit-change-audit-event-class-data-columns"></a><span data-ttu-id="0308e-104">Audit Change Audit 事件类的数据列</span><span class="sxs-lookup"><span data-stu-id="0308e-104">Audit Change Audit Event Class Data Columns</span></span>  
  
|<span data-ttu-id="0308e-105">数据列名称</span><span class="sxs-lookup"><span data-stu-id="0308e-105">Data column name</span></span>|<span data-ttu-id="0308e-106">数据类型</span><span class="sxs-lookup"><span data-stu-id="0308e-106">Data type</span></span>|<span data-ttu-id="0308e-107">说明</span><span class="sxs-lookup"><span data-stu-id="0308e-107">Description</span></span>|<span data-ttu-id="0308e-108">列 ID</span><span class="sxs-lookup"><span data-stu-id="0308e-108">Column ID</span></span>|<span data-ttu-id="0308e-109">可筛选</span><span class="sxs-lookup"><span data-stu-id="0308e-109">Filterable</span></span>|  
|----------------------|---------------|-----------------|---------------|----------------|  
|<span data-ttu-id="0308e-110">ApplicationName </span><span class="sxs-lookup"><span data-stu-id="0308e-110">**ApplicationName**</span></span>|<span data-ttu-id="0308e-111">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="0308e-111">**nvarchar**</span></span>|<span data-ttu-id="0308e-112">与 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例建立连接的客户端应用程序的名称。</span><span class="sxs-lookup"><span data-stu-id="0308e-112">Name of the client application that created the connection to an instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="0308e-113">此列由应用程序传递的值填充，而不是由所显示的程序名填充。</span><span class="sxs-lookup"><span data-stu-id="0308e-113">This column is populated with the values passed by the application rather than the displayed name of the program.</span></span>|<span data-ttu-id="0308e-114">10</span><span class="sxs-lookup"><span data-stu-id="0308e-114">10</span></span>|<span data-ttu-id="0308e-115">是</span><span class="sxs-lookup"><span data-stu-id="0308e-115">Yes</span></span>|  
|<span data-ttu-id="0308e-116">**ClientProcessID**</span><span class="sxs-lookup"><span data-stu-id="0308e-116">**ClientProcessID**</span></span>|<span data-ttu-id="0308e-117">**int**</span><span class="sxs-lookup"><span data-stu-id="0308e-117">**int**</span></span>|<span data-ttu-id="0308e-118">主机为运行该客户端应用程序的进程分配的 ID。</span><span class="sxs-lookup"><span data-stu-id="0308e-118">ID assigned by the host computer to the process where the client application is running.</span></span> <span data-ttu-id="0308e-119">如果客户端提供了客户端进程 ID，则填充此数据列。</span><span class="sxs-lookup"><span data-stu-id="0308e-119">This data column is populated if the client provides the client process ID.</span></span>|<span data-ttu-id="0308e-120">9</span><span class="sxs-lookup"><span data-stu-id="0308e-120">9</span></span>|<span data-ttu-id="0308e-121">是</span><span class="sxs-lookup"><span data-stu-id="0308e-121">Yes</span></span>|  
|<span data-ttu-id="0308e-122">**ColumnPermissions**</span><span class="sxs-lookup"><span data-stu-id="0308e-122">**ColumnPermissions**</span></span>|<span data-ttu-id="0308e-123">**int**</span><span class="sxs-lookup"><span data-stu-id="0308e-123">**int**</span></span>|<span data-ttu-id="0308e-124">指示是否已设置了列权限。</span><span class="sxs-lookup"><span data-stu-id="0308e-124">Indicator of whether a column permission was set.</span></span> <span data-ttu-id="0308e-125">分析语句文本，以确定将哪些权限应用到了哪些列。</span><span class="sxs-lookup"><span data-stu-id="0308e-125">Parse the statement text to determine which permissions were applied to which columns.</span></span>|<span data-ttu-id="0308e-126">44</span><span class="sxs-lookup"><span data-stu-id="0308e-126">44</span></span>|<span data-ttu-id="0308e-127">是</span><span class="sxs-lookup"><span data-stu-id="0308e-127">Yes</span></span>|  
|<span data-ttu-id="0308e-128">**DatabaseID**</span><span class="sxs-lookup"><span data-stu-id="0308e-128">**DatabaseID**</span></span>|<span data-ttu-id="0308e-129">**int**</span><span class="sxs-lookup"><span data-stu-id="0308e-129">**int**</span></span>|<span data-ttu-id="0308e-130">由 USE *database* 语句指定的数据库的 ID；如果未对给定实例发出 USE *database* 语句，则为默认数据库的 ID。</span><span class="sxs-lookup"><span data-stu-id="0308e-130">ID of the database specified by the USE *database* statement or the default database if no USE *database* statement has been issued for a given instance.</span></span> [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="0308e-131">数据列而且服务器可用，则 **ServerName** 将显示数据库名。</span><span class="sxs-lookup"><span data-stu-id="0308e-131">displays the name of the database if the **ServerName** data column is captured in the trace and the server is available.</span></span> <span data-ttu-id="0308e-132">可使用 DB_ID 函数来确定数据库的值。</span><span class="sxs-lookup"><span data-stu-id="0308e-132">Determine the value for a database by using the DB_ID function.</span></span>|<span data-ttu-id="0308e-133">3</span><span class="sxs-lookup"><span data-stu-id="0308e-133">3</span></span>|<span data-ttu-id="0308e-134">是</span><span class="sxs-lookup"><span data-stu-id="0308e-134">Yes</span></span>|  
|<span data-ttu-id="0308e-135">**DatabaseName**</span><span class="sxs-lookup"><span data-stu-id="0308e-135">**DatabaseName**</span></span>|<span data-ttu-id="0308e-136">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="0308e-136">**nvarchar**</span></span>|<span data-ttu-id="0308e-137">正在其中运行用户语句的数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="0308e-137">Name of the database in which the user statement is running.</span></span>|<span data-ttu-id="0308e-138">35</span><span class="sxs-lookup"><span data-stu-id="0308e-138">35</span></span>|<span data-ttu-id="0308e-139">是</span><span class="sxs-lookup"><span data-stu-id="0308e-139">Yes</span></span>|  
|<span data-ttu-id="0308e-140">**DBUserName**</span><span class="sxs-lookup"><span data-stu-id="0308e-140">**DBUserName**</span></span>|<span data-ttu-id="0308e-141">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="0308e-141">**nvarchar**</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="0308e-142">用户名。</span><span class="sxs-lookup"><span data-stu-id="0308e-142">user name of the client.</span></span>|<span data-ttu-id="0308e-143">40</span><span class="sxs-lookup"><span data-stu-id="0308e-143">40</span></span>|<span data-ttu-id="0308e-144">是</span><span class="sxs-lookup"><span data-stu-id="0308e-144">Yes</span></span>|  
|<span data-ttu-id="0308e-145">**EventClass**</span><span class="sxs-lookup"><span data-stu-id="0308e-145">**EventClass**</span></span>|<span data-ttu-id="0308e-146">**int**</span><span class="sxs-lookup"><span data-stu-id="0308e-146">**int**</span></span>|<span data-ttu-id="0308e-147">事件类型 = 117。</span><span class="sxs-lookup"><span data-stu-id="0308e-147">Type of event = 117.</span></span>|<span data-ttu-id="0308e-148">27</span><span class="sxs-lookup"><span data-stu-id="0308e-148">27</span></span>|<span data-ttu-id="0308e-149">否</span><span class="sxs-lookup"><span data-stu-id="0308e-149">No</span></span>|  
|<span data-ttu-id="0308e-150">**EventSequence**</span><span class="sxs-lookup"><span data-stu-id="0308e-150">**EventSequence**</span></span>|<span data-ttu-id="0308e-151">**int**</span><span class="sxs-lookup"><span data-stu-id="0308e-151">**int**</span></span>|<span data-ttu-id="0308e-152">给定事件在请求中的顺序。</span><span class="sxs-lookup"><span data-stu-id="0308e-152">Sequence of a given event within the request.</span></span>|<span data-ttu-id="0308e-153">51</span><span class="sxs-lookup"><span data-stu-id="0308e-153">51</span></span>|<span data-ttu-id="0308e-154">否</span><span class="sxs-lookup"><span data-stu-id="0308e-154">No</span></span>|  
|<span data-ttu-id="0308e-155">**EventSubClass**</span><span class="sxs-lookup"><span data-stu-id="0308e-155">**EventSubClass**</span></span>|<span data-ttu-id="0308e-156">**int**</span><span class="sxs-lookup"><span data-stu-id="0308e-156">**int**</span></span>|<span data-ttu-id="0308e-157">事件子类的类型。</span><span class="sxs-lookup"><span data-stu-id="0308e-157">Type of event subclass.</span></span><br /><br /> <span data-ttu-id="0308e-158">1 = 审核已开始</span><span class="sxs-lookup"><span data-stu-id="0308e-158">1=Audit started</span></span><br /><br /> <span data-ttu-id="0308e-159">2 = 审核已停止</span><span class="sxs-lookup"><span data-stu-id="0308e-159">2=Audit stopped</span></span><br /><br /> <span data-ttu-id="0308e-160">3 = C2 模式已打开</span><span class="sxs-lookup"><span data-stu-id="0308e-160">3=C2 mode ON</span></span><br /><br /> <span data-ttu-id="0308e-161">4 = C2 模式已关闭</span><span class="sxs-lookup"><span data-stu-id="0308e-161">4=C2 mode OFF</span></span>|<span data-ttu-id="0308e-162">21</span><span class="sxs-lookup"><span data-stu-id="0308e-162">21</span></span>|<span data-ttu-id="0308e-163">是</span><span class="sxs-lookup"><span data-stu-id="0308e-163">Yes</span></span>|  
|<span data-ttu-id="0308e-164">**HostName**</span><span class="sxs-lookup"><span data-stu-id="0308e-164">**HostName**</span></span>|<span data-ttu-id="0308e-165">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="0308e-165">**nvarchar**</span></span>|<span data-ttu-id="0308e-166">正在运行客户端的计算机的名称。</span><span class="sxs-lookup"><span data-stu-id="0308e-166">Name of the computer on which the client is running.</span></span> <span data-ttu-id="0308e-167">如果客户端提供了主机名，则填充此数据列。</span><span class="sxs-lookup"><span data-stu-id="0308e-167">This data column is populated if the client provides the host name.</span></span> <span data-ttu-id="0308e-168">若要确定主机名，请使用 HOST_NAME 函数。</span><span class="sxs-lookup"><span data-stu-id="0308e-168">To determine the host name, use the HOST_NAME function.</span></span>|<span data-ttu-id="0308e-169">8</span><span class="sxs-lookup"><span data-stu-id="0308e-169">8</span></span>|<span data-ttu-id="0308e-170">是</span><span class="sxs-lookup"><span data-stu-id="0308e-170">Yes</span></span>|  
|<span data-ttu-id="0308e-171">**IsSystem**</span><span class="sxs-lookup"><span data-stu-id="0308e-171">**IsSystem**</span></span>|<span data-ttu-id="0308e-172">**int**</span><span class="sxs-lookup"><span data-stu-id="0308e-172">**int**</span></span>|<span data-ttu-id="0308e-173">指示事件是发生在系统进程中还是发生在用户进程中。</span><span class="sxs-lookup"><span data-stu-id="0308e-173">Indicates whether the event occurred on a system process or a user process.</span></span> <span data-ttu-id="0308e-174">1 = 系统，0 = 用户。</span><span class="sxs-lookup"><span data-stu-id="0308e-174">1 = system, 0 = user.</span></span>|<span data-ttu-id="0308e-175">60</span><span class="sxs-lookup"><span data-stu-id="0308e-175">60</span></span>|<span data-ttu-id="0308e-176">是</span><span class="sxs-lookup"><span data-stu-id="0308e-176">Yes</span></span>|  
|<span data-ttu-id="0308e-177">**LoginName**</span><span class="sxs-lookup"><span data-stu-id="0308e-177">**LoginName**</span></span>|<span data-ttu-id="0308e-178">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="0308e-178">**nvarchar**</span></span>|<span data-ttu-id="0308e-179">用户的登录名（ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安全登录名或 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 登录凭据，格式为“DOMAIN\username”）。</span><span class="sxs-lookup"><span data-stu-id="0308e-179">Name of the login of the user (either the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] security login or the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows login credentials in the form of DOMAIN\username).</span></span>|<span data-ttu-id="0308e-180">11</span><span class="sxs-lookup"><span data-stu-id="0308e-180">11</span></span>|<span data-ttu-id="0308e-181">是</span><span class="sxs-lookup"><span data-stu-id="0308e-181">Yes</span></span>|  
|<span data-ttu-id="0308e-182">**LoginSid**</span><span class="sxs-lookup"><span data-stu-id="0308e-182">**LoginSid**</span></span>|<span data-ttu-id="0308e-183">**图像**</span><span class="sxs-lookup"><span data-stu-id="0308e-183">**image**</span></span>|<span data-ttu-id="0308e-184">登录用户的安全标识号 (SID)。</span><span class="sxs-lookup"><span data-stu-id="0308e-184">Security identification number (SID) of the logged-in user.</span></span> <span data-ttu-id="0308e-185">你可以在 **sys.server_principals** 目录视图中找到此信息。</span><span class="sxs-lookup"><span data-stu-id="0308e-185">You can find this information in the **sys.server_principals** catalog view.</span></span> <span data-ttu-id="0308e-186">服务器中的每个登录名都具有唯一的 SID。</span><span class="sxs-lookup"><span data-stu-id="0308e-186">Each SID is unique for each login in the server.</span></span>|<span data-ttu-id="0308e-187">41</span><span class="sxs-lookup"><span data-stu-id="0308e-187">41</span></span>|<span data-ttu-id="0308e-188">是</span><span class="sxs-lookup"><span data-stu-id="0308e-188">Yes</span></span>|  
|<span data-ttu-id="0308e-189">**NestLevel**</span><span class="sxs-lookup"><span data-stu-id="0308e-189">**NestLevel**</span></span>|<span data-ttu-id="0308e-190">**int**</span><span class="sxs-lookup"><span data-stu-id="0308e-190">**int**</span></span>|<span data-ttu-id="0308e-191">表示 @@NESTLEVEL 所返回的数据的整数。</span><span class="sxs-lookup"><span data-stu-id="0308e-191">Integer representing the data returned by @@NESTLEVEL.</span></span>|<span data-ttu-id="0308e-192">29</span><span class="sxs-lookup"><span data-stu-id="0308e-192">29</span></span>|<span data-ttu-id="0308e-193">是</span><span class="sxs-lookup"><span data-stu-id="0308e-193">Yes</span></span>|  
|<span data-ttu-id="0308e-194">**NTDomainName**</span><span class="sxs-lookup"><span data-stu-id="0308e-194">**NTDomainName**</span></span>|<span data-ttu-id="0308e-195">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="0308e-195">**nvarchar**</span></span>|<span data-ttu-id="0308e-196">用户所属的 Windows 域。</span><span class="sxs-lookup"><span data-stu-id="0308e-196">Windows domain to which the user belongs.</span></span>|<span data-ttu-id="0308e-197">7</span><span class="sxs-lookup"><span data-stu-id="0308e-197">7</span></span>|<span data-ttu-id="0308e-198">是</span><span class="sxs-lookup"><span data-stu-id="0308e-198">Yes</span></span>|  
|<span data-ttu-id="0308e-199">**NTUserName**</span><span class="sxs-lookup"><span data-stu-id="0308e-199">**NTUserName**</span></span>|<span data-ttu-id="0308e-200">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="0308e-200">**nvarchar**</span></span>|<span data-ttu-id="0308e-201">Windows 用户名。</span><span class="sxs-lookup"><span data-stu-id="0308e-201">Windows user name.</span></span>|<span data-ttu-id="0308e-202">6</span><span class="sxs-lookup"><span data-stu-id="0308e-202">6</span></span>|<span data-ttu-id="0308e-203">是</span><span class="sxs-lookup"><span data-stu-id="0308e-203">Yes</span></span>|  
|<span data-ttu-id="0308e-204">**OwnerName**</span><span class="sxs-lookup"><span data-stu-id="0308e-204">**OwnerName**</span></span>|<span data-ttu-id="0308e-205">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="0308e-205">**nvarchar**</span></span>|<span data-ttu-id="0308e-206">对象所有者的数据库用户名。</span><span class="sxs-lookup"><span data-stu-id="0308e-206">Database user name of the object owner.</span></span>|<span data-ttu-id="0308e-207">37</span><span class="sxs-lookup"><span data-stu-id="0308e-207">37</span></span>|<span data-ttu-id="0308e-208">是</span><span class="sxs-lookup"><span data-stu-id="0308e-208">Yes</span></span>|  
|<span data-ttu-id="0308e-209">**RequestID**</span><span class="sxs-lookup"><span data-stu-id="0308e-209">**RequestID**</span></span>|<span data-ttu-id="0308e-210">**int**</span><span class="sxs-lookup"><span data-stu-id="0308e-210">**int**</span></span>|<span data-ttu-id="0308e-211">包含该语句的请求的 ID。</span><span class="sxs-lookup"><span data-stu-id="0308e-211">ID of the request containing the statement.</span></span>|<span data-ttu-id="0308e-212">49</span><span class="sxs-lookup"><span data-stu-id="0308e-212">49</span></span>|<span data-ttu-id="0308e-213">是</span><span class="sxs-lookup"><span data-stu-id="0308e-213">Yes</span></span>|  
|<span data-ttu-id="0308e-214">**ServerName**</span><span class="sxs-lookup"><span data-stu-id="0308e-214">**ServerName**</span></span>|<span data-ttu-id="0308e-215">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="0308e-215">**nvarchar**</span></span>|<span data-ttu-id="0308e-216">所跟踪的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例的名称。</span><span class="sxs-lookup"><span data-stu-id="0308e-216">Name of the instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] being traced.</span></span>|<span data-ttu-id="0308e-217">26</span><span class="sxs-lookup"><span data-stu-id="0308e-217">26</span></span>|<span data-ttu-id="0308e-218">否</span><span class="sxs-lookup"><span data-stu-id="0308e-218">No</span></span>|  
|<span data-ttu-id="0308e-219">**SessionLoginName**</span><span class="sxs-lookup"><span data-stu-id="0308e-219">**SessionLoginName**</span></span>|<span data-ttu-id="0308e-220">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="0308e-220">**nvarchar**</span></span>|<span data-ttu-id="0308e-221">发起会话的用户的登录名。</span><span class="sxs-lookup"><span data-stu-id="0308e-221">Login name of the user who originated the session.</span></span> <span data-ttu-id="0308e-222">例如，如果你使用 Login1 连接到 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，再以 Login2 的身份执行语句，则 SessionLoginName 将显示 Login1，而 LoginName 将显示 Login2   。</span><span class="sxs-lookup"><span data-stu-id="0308e-222">For example, if you connect to [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using Login1 and execute a statement as Login2, **SessionLoginName** shows Login1 and **LoginName** shows Login2.</span></span> <span data-ttu-id="0308e-223">此列将同时显示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名和 Windows 登录名。</span><span class="sxs-lookup"><span data-stu-id="0308e-223">This column displays both [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and Windows logins.</span></span>|<span data-ttu-id="0308e-224">64</span><span class="sxs-lookup"><span data-stu-id="0308e-224">64</span></span>|<span data-ttu-id="0308e-225">是</span><span class="sxs-lookup"><span data-stu-id="0308e-225">Yes</span></span>|  
|<span data-ttu-id="0308e-226">**SPID**</span><span class="sxs-lookup"><span data-stu-id="0308e-226">**SPID**</span></span>|<span data-ttu-id="0308e-227">**int**</span><span class="sxs-lookup"><span data-stu-id="0308e-227">**int**</span></span>|<span data-ttu-id="0308e-228">发生该事件的会话的 ID。</span><span class="sxs-lookup"><span data-stu-id="0308e-228">ID of the session on which the event occurred.</span></span>|<span data-ttu-id="0308e-229">12</span><span class="sxs-lookup"><span data-stu-id="0308e-229">12</span></span>|<span data-ttu-id="0308e-230">是</span><span class="sxs-lookup"><span data-stu-id="0308e-230">Yes</span></span>|  
|<span data-ttu-id="0308e-231">**StartTime**</span><span class="sxs-lookup"><span data-stu-id="0308e-231">**StartTime**</span></span>|<span data-ttu-id="0308e-232">**datetime**</span><span class="sxs-lookup"><span data-stu-id="0308e-232">**datetime**</span></span>|<span data-ttu-id="0308e-233">该事件（如果存在）的启动时间。</span><span class="sxs-lookup"><span data-stu-id="0308e-233">Time at which the event started, if available.</span></span>|<span data-ttu-id="0308e-234">14</span><span class="sxs-lookup"><span data-stu-id="0308e-234">14</span></span>|<span data-ttu-id="0308e-235">是</span><span class="sxs-lookup"><span data-stu-id="0308e-235">Yes</span></span>|  
|<span data-ttu-id="0308e-236">**Success**</span><span class="sxs-lookup"><span data-stu-id="0308e-236">**Success**</span></span>|<span data-ttu-id="0308e-237">**int**</span><span class="sxs-lookup"><span data-stu-id="0308e-237">**int**</span></span>|<span data-ttu-id="0308e-238">1 = 成功。</span><span class="sxs-lookup"><span data-stu-id="0308e-238">1 = success.</span></span> <span data-ttu-id="0308e-239">0 = 失败。</span><span class="sxs-lookup"><span data-stu-id="0308e-239">0 = failure.</span></span> <span data-ttu-id="0308e-240">例如，值为 1 时表示权限检查成功；值为 0 时表示权限检查失败。</span><span class="sxs-lookup"><span data-stu-id="0308e-240">For example, a value of 1 indicates success of a permissions check and a value of 0 indicates failure of that check.</span></span>|<span data-ttu-id="0308e-241">23</span><span class="sxs-lookup"><span data-stu-id="0308e-241">23</span></span>|<span data-ttu-id="0308e-242">是</span><span class="sxs-lookup"><span data-stu-id="0308e-242">Yes</span></span>|  
|<span data-ttu-id="0308e-243">**TextData**</span><span class="sxs-lookup"><span data-stu-id="0308e-243">**TextData**</span></span>|<span data-ttu-id="0308e-244">**ntext**</span><span class="sxs-lookup"><span data-stu-id="0308e-244">**ntext**</span></span>|<span data-ttu-id="0308e-245">依赖于跟踪中捕获的事件类的文本值。</span><span class="sxs-lookup"><span data-stu-id="0308e-245">Text value dependent on the event class captured in the trace.</span></span>|<span data-ttu-id="0308e-246">1</span><span class="sxs-lookup"><span data-stu-id="0308e-246">1</span></span>|<span data-ttu-id="0308e-247">是</span><span class="sxs-lookup"><span data-stu-id="0308e-247">Yes</span></span>|  
|<span data-ttu-id="0308e-248">**XactSequence**</span><span class="sxs-lookup"><span data-stu-id="0308e-248">**XactSequence**</span></span>|<span data-ttu-id="0308e-249">**bigint**</span><span class="sxs-lookup"><span data-stu-id="0308e-249">**bigint**</span></span>|<span data-ttu-id="0308e-250">用于说明当前事务的标记。</span><span class="sxs-lookup"><span data-stu-id="0308e-250">Token used to describe the current transaction.</span></span>|<span data-ttu-id="0308e-251">50</span><span class="sxs-lookup"><span data-stu-id="0308e-251">50</span></span>|<span data-ttu-id="0308e-252">是</span><span class="sxs-lookup"><span data-stu-id="0308e-252">Yes</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0308e-253">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0308e-253">See Also</span></span>  
 <span data-ttu-id="0308e-254">[扩展事件](../extended-events/extended-events.md) </span><span class="sxs-lookup"><span data-stu-id="0308e-254">[Extended Events](../extended-events/extended-events.md) </span></span>  
 [<span data-ttu-id="0308e-255">sp_trace_setevent (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="0308e-255">sp_trace_setevent &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)  
  
  