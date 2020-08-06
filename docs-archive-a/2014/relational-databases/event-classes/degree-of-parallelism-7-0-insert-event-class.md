---
title: Degree of Parallelism (7.0 Insert) 事件类 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Degree of Parallelism event class
ms.assetid: 6753ef30-890f-47a3-b0b6-8abb184e1d83
author: stevestein
ms.author: sstein
ms.openlocfilehash: a56b07ac5d94a319a027dad40187de66d1079019
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586680"
---
# <a name="degree-of-parallelism-70-insert-event-class"></a><span data-ttu-id="83119-102">Degree of Parallelism (7.0 Insert) 事件类</span><span class="sxs-lookup"><span data-stu-id="83119-102">Degree of Parallelism (7.0 Insert) Event Class</span></span>
  <span data-ttu-id="83119-103">每次 **执行 SELECT、INSERT、UPDATE 或 DELETE 语句时都会发生** Degree of Parallelism (7.0 Insert) [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 事件类。</span><span class="sxs-lookup"><span data-stu-id="83119-103">The **Degree of Parallelism (7.0 Insert)** event class occurs each time [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] executes a SELECT, INSERT, UPDATE, or DELETE statement.</span></span>  
  
 <span data-ttu-id="83119-104">当该事件包含在跟踪中时，如果经常发生这些事件则所引起的开销可能会明显影响性能。</span><span class="sxs-lookup"><span data-stu-id="83119-104">When this event class is included in a trace, the amount of entailed overhead may significantly impede performance if these events occur frequently.</span></span> <span data-ttu-id="83119-105">若要最大限度地降低引起的开销，请仅将此事件类用于在短时间内监视特定问题的跟踪操作。</span><span class="sxs-lookup"><span data-stu-id="83119-105">To minimize overhead incurred, limit use of this event class to traces that briefly monitor specific problems.</span></span>  
  
## <a name="degree-of-parallelism-70-insert-event-class-data-columns"></a><span data-ttu-id="83119-106">Degree of Parallelism (7.0 Insert) 事件类的数据列</span><span class="sxs-lookup"><span data-stu-id="83119-106">Degree of Parallelism (7.0 Insert) Event Class Data Columns</span></span>  
  
|<span data-ttu-id="83119-107">数据列名称</span><span class="sxs-lookup"><span data-stu-id="83119-107">Data column name</span></span>|<span data-ttu-id="83119-108">数据类型</span><span class="sxs-lookup"><span data-stu-id="83119-108">Data type</span></span>|<span data-ttu-id="83119-109">说明</span><span class="sxs-lookup"><span data-stu-id="83119-109">Description</span></span>|<span data-ttu-id="83119-110">列 ID</span><span class="sxs-lookup"><span data-stu-id="83119-110">Column ID</span></span>|<span data-ttu-id="83119-111">可筛选</span><span class="sxs-lookup"><span data-stu-id="83119-111">Filterable</span></span>|  
|----------------------|---------------|-----------------|---------------|----------------|  
|<span data-ttu-id="83119-112">ApplicationName </span><span class="sxs-lookup"><span data-stu-id="83119-112">**ApplicationName**</span></span>|<span data-ttu-id="83119-113">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="83119-113">**nvarchar**</span></span>|<span data-ttu-id="83119-114">客户端应用程序的名称，该客户端应用程序创建了指向 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例的连接。</span><span class="sxs-lookup"><span data-stu-id="83119-114">Name of the client application that created the connection to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="83119-115">此列由应用程序传递的值填充，而不是由所显示的程序名填充。</span><span class="sxs-lookup"><span data-stu-id="83119-115">This column is populated with the values passed by the application rather than the displayed name of the program.</span></span>|<span data-ttu-id="83119-116">10</span><span class="sxs-lookup"><span data-stu-id="83119-116">10</span></span>|<span data-ttu-id="83119-117">是</span><span class="sxs-lookup"><span data-stu-id="83119-117">Yes</span></span>|  
|<span data-ttu-id="83119-118">**BinaryData**</span><span class="sxs-lookup"><span data-stu-id="83119-118">**BinaryData**</span></span>|<span data-ttu-id="83119-119">**图像**</span><span class="sxs-lookup"><span data-stu-id="83119-119">**image**</span></span>|<span data-ttu-id="83119-120">用于根据以下值完成进程的 CPU 数量：</span><span class="sxs-lookup"><span data-stu-id="83119-120">Number of CPUs used to complete the process based on the following values:</span></span><br /><br /> <span data-ttu-id="83119-121">0x00000000：指示在串行中运行的串行计划。</span><span class="sxs-lookup"><span data-stu-id="83119-121">0x00000000: Indicates a serial plan running in serial.</span></span><br /><br /> <span data-ttu-id="83119-122">0x01000000 指示以串行方式运行的并行计划。</span><span class="sxs-lookup"><span data-stu-id="83119-122">0x01000000 Indicates a parallel plan running in serial.</span></span><br /><br /> <span data-ttu-id="83119-123">>= 0x02000000：指示并行运行的并行计划。</span><span class="sxs-lookup"><span data-stu-id="83119-123">>= 0x02000000: Indicates a parallel plan running in parallel.</span></span>|<span data-ttu-id="83119-124">2</span><span class="sxs-lookup"><span data-stu-id="83119-124">2</span></span>|<span data-ttu-id="83119-125">否</span><span class="sxs-lookup"><span data-stu-id="83119-125">No</span></span>|  
|<span data-ttu-id="83119-126">**ClientProcessID**</span><span class="sxs-lookup"><span data-stu-id="83119-126">**ClientProcessID**</span></span>|<span data-ttu-id="83119-127">**int**</span><span class="sxs-lookup"><span data-stu-id="83119-127">**int**</span></span>|<span data-ttu-id="83119-128">主机为运行该客户端应用程序的进程分配的 ID。</span><span class="sxs-lookup"><span data-stu-id="83119-128">ID assigned by the host computer to the process where the client application is running.</span></span> <span data-ttu-id="83119-129">如果客户端提供了客户端进程 ID，则填充此数据列。</span><span class="sxs-lookup"><span data-stu-id="83119-129">This data column is populated if the client process ID is provided by the client.</span></span>|<span data-ttu-id="83119-130">9</span><span class="sxs-lookup"><span data-stu-id="83119-130">9</span></span>|<span data-ttu-id="83119-131">是</span><span class="sxs-lookup"><span data-stu-id="83119-131">Yes</span></span>|  
|<span data-ttu-id="83119-132">**DatabaseID**</span><span class="sxs-lookup"><span data-stu-id="83119-132">**DatabaseID**</span></span>|<span data-ttu-id="83119-133">**int**</span><span class="sxs-lookup"><span data-stu-id="83119-133">**int**</span></span>|<span data-ttu-id="83119-134">由 USE 数据库语句指定的数据库的 ID；如果未对给定实例发出 USE 数据库语句，则为默认数据库的 ID。</span><span class="sxs-lookup"><span data-stu-id="83119-134">ID of the database specified by the USE database statement or the default database if no USE database statement has been issued for a given instance.</span></span> [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="83119-135">数据列而且服务器可用，则 **ServerName** 将显示数据库名。</span><span class="sxs-lookup"><span data-stu-id="83119-135">displays the name of the database if the **ServerName** data column is captured in the trace and the server is available.</span></span> <span data-ttu-id="83119-136">可使用 DB_ID 函数来确定数据库的值。</span><span class="sxs-lookup"><span data-stu-id="83119-136">Determine the value for a database by using the DB_ID function.</span></span>|<span data-ttu-id="83119-137">3</span><span class="sxs-lookup"><span data-stu-id="83119-137">3</span></span>|<span data-ttu-id="83119-138">是</span><span class="sxs-lookup"><span data-stu-id="83119-138">Yes</span></span>|  
|<span data-ttu-id="83119-139">**DatabaseName**</span><span class="sxs-lookup"><span data-stu-id="83119-139">**DatabaseName**</span></span>|<span data-ttu-id="83119-140">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="83119-140">**nvarchar**</span></span>|<span data-ttu-id="83119-141">正在其中运行用户语句的数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="83119-141">Name of the database in which the user statement is running.</span></span>|<span data-ttu-id="83119-142">35</span><span class="sxs-lookup"><span data-stu-id="83119-142">35</span></span>|<span data-ttu-id="83119-143">是</span><span class="sxs-lookup"><span data-stu-id="83119-143">Yes</span></span>|  
|<span data-ttu-id="83119-144">**Event Class**</span><span class="sxs-lookup"><span data-stu-id="83119-144">**Event Class**</span></span>|<span data-ttu-id="83119-145">**int**</span><span class="sxs-lookup"><span data-stu-id="83119-145">**int**</span></span>|<span data-ttu-id="83119-146">事件类型 = 28。</span><span class="sxs-lookup"><span data-stu-id="83119-146">Type of Event = 28.</span></span>|<span data-ttu-id="83119-147">27</span><span class="sxs-lookup"><span data-stu-id="83119-147">27</span></span>|<span data-ttu-id="83119-148">否</span><span class="sxs-lookup"><span data-stu-id="83119-148">No</span></span>|  
|<span data-ttu-id="83119-149">**EventSequence**</span><span class="sxs-lookup"><span data-stu-id="83119-149">**EventSequence**</span></span>|<span data-ttu-id="83119-150">**int**</span><span class="sxs-lookup"><span data-stu-id="83119-150">**int**</span></span>|<span data-ttu-id="83119-151">给定事件在请求中的顺序。</span><span class="sxs-lookup"><span data-stu-id="83119-151">Sequence of a given event within the request.</span></span>|<span data-ttu-id="83119-152">51</span><span class="sxs-lookup"><span data-stu-id="83119-152">51</span></span>|<span data-ttu-id="83119-153">否</span><span class="sxs-lookup"><span data-stu-id="83119-153">No</span></span>|  
|<span data-ttu-id="83119-154">**EventSubClass**</span><span class="sxs-lookup"><span data-stu-id="83119-154">**EventSubClass**</span></span>|<span data-ttu-id="83119-155">**int**</span><span class="sxs-lookup"><span data-stu-id="83119-155">**int**</span></span>|<span data-ttu-id="83119-156">指示根据以下值执行的语句：</span><span class="sxs-lookup"><span data-stu-id="83119-156">Indicates the statement executed, based on the following values:</span></span><br /><br /> <span data-ttu-id="83119-157">1 = 选择</span><span class="sxs-lookup"><span data-stu-id="83119-157">1=Select</span></span><br /><br /> <span data-ttu-id="83119-158">2 = 插入</span><span class="sxs-lookup"><span data-stu-id="83119-158">2=Insert</span></span><br /><br /> <span data-ttu-id="83119-159">3 = 更新</span><span class="sxs-lookup"><span data-stu-id="83119-159">3=Update</span></span><br /><br /> <span data-ttu-id="83119-160">4 = 删除</span><span class="sxs-lookup"><span data-stu-id="83119-160">4=Delete</span></span>|<span data-ttu-id="83119-161">21</span><span class="sxs-lookup"><span data-stu-id="83119-161">21</span></span>|<span data-ttu-id="83119-162">否</span><span class="sxs-lookup"><span data-stu-id="83119-162">No</span></span>|  
|<span data-ttu-id="83119-163">**GroupID**</span><span class="sxs-lookup"><span data-stu-id="83119-163">**GroupID**</span></span>|<span data-ttu-id="83119-164">**int**</span><span class="sxs-lookup"><span data-stu-id="83119-164">**int**</span></span>|<span data-ttu-id="83119-165">在其中激发 SQL 跟踪事件的工作负荷组的 ID。</span><span class="sxs-lookup"><span data-stu-id="83119-165">ID of the workload group where the SQL Trace event fires.</span></span>|<span data-ttu-id="83119-166">66</span><span class="sxs-lookup"><span data-stu-id="83119-166">66</span></span>|<span data-ttu-id="83119-167">是</span><span class="sxs-lookup"><span data-stu-id="83119-167">Yes</span></span>|  
|<span data-ttu-id="83119-168">**HostName**</span><span class="sxs-lookup"><span data-stu-id="83119-168">**HostName**</span></span>|<span data-ttu-id="83119-169">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="83119-169">**nvarchar**</span></span>|<span data-ttu-id="83119-170">正在运行客户端的计算机的名称。</span><span class="sxs-lookup"><span data-stu-id="83119-170">Name of the computer on which the client is running.</span></span> <span data-ttu-id="83119-171">如果客户端提供了主机名，则填充此数据列。</span><span class="sxs-lookup"><span data-stu-id="83119-171">This data column is populated if the host name is provided by the client.</span></span> <span data-ttu-id="83119-172">若要确定主机名，请使用 HOST_NAME 函数。</span><span class="sxs-lookup"><span data-stu-id="83119-172">To determine the host name, use the HOST_NAME function.</span></span>|<span data-ttu-id="83119-173">8</span><span class="sxs-lookup"><span data-stu-id="83119-173">8</span></span>|<span data-ttu-id="83119-174">是</span><span class="sxs-lookup"><span data-stu-id="83119-174">Yes</span></span>|  
|<span data-ttu-id="83119-175">**Integer Data**</span><span class="sxs-lookup"><span data-stu-id="83119-175">**Integer Data**</span></span>|<span data-ttu-id="83119-176">**int**</span><span class="sxs-lookup"><span data-stu-id="83119-176">**int**</span></span>|<span data-ttu-id="83119-177">授予查询用来执行操作的“工作区内存”总量 (KB)，这些操作涉及到哈希、排序或创建索引操作。</span><span class="sxs-lookup"><span data-stu-id="83119-177">The amount of "workspace memory" in kilobytes that the query has been granted to perform operations involving hashing, sorts or create index operations.</span></span> <span data-ttu-id="83119-178">在执行期间将根据需要获取内存。</span><span class="sxs-lookup"><span data-stu-id="83119-178">The memory will be acquired during execution as needed.</span></span>|<span data-ttu-id="83119-179">25</span><span class="sxs-lookup"><span data-stu-id="83119-179">25</span></span>|<span data-ttu-id="83119-180">是</span><span class="sxs-lookup"><span data-stu-id="83119-180">Yes</span></span>|  
|<span data-ttu-id="83119-181">**IsSystem**</span><span class="sxs-lookup"><span data-stu-id="83119-181">**IsSystem**</span></span>|<span data-ttu-id="83119-182">**int**</span><span class="sxs-lookup"><span data-stu-id="83119-182">**int**</span></span>|<span data-ttu-id="83119-183">指示事件是发生在系统进程中还是发生在用户进程中。</span><span class="sxs-lookup"><span data-stu-id="83119-183">Indicates whether the event occurred on a system process or a user process.</span></span> <span data-ttu-id="83119-184">1 = 系统，0 = 用户。</span><span class="sxs-lookup"><span data-stu-id="83119-184">1 = system, 0 = user.</span></span>|<span data-ttu-id="83119-185">60</span><span class="sxs-lookup"><span data-stu-id="83119-185">60</span></span>|<span data-ttu-id="83119-186">是</span><span class="sxs-lookup"><span data-stu-id="83119-186">Yes</span></span>|  
|<span data-ttu-id="83119-187">**LoginName**</span><span class="sxs-lookup"><span data-stu-id="83119-187">**LoginName**</span></span>|<span data-ttu-id="83119-188">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="83119-188">**nvarchar**</span></span>|<span data-ttu-id="83119-189">用户的登录名（ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安全登录名或 Windows 登录凭据，格式为 “DOMAIN\\*username*”）。</span><span class="sxs-lookup"><span data-stu-id="83119-189">Name of the login of the user (either the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] security login or the Windows login credentials in the form of DOMAIN\\*username*).</span></span>|<span data-ttu-id="83119-190">11</span><span class="sxs-lookup"><span data-stu-id="83119-190">11</span></span>|<span data-ttu-id="83119-191">是</span><span class="sxs-lookup"><span data-stu-id="83119-191">Yes</span></span>|  
|<span data-ttu-id="83119-192">**LoginSid**</span><span class="sxs-lookup"><span data-stu-id="83119-192">**LoginSid**</span></span>|<span data-ttu-id="83119-193">**图像**</span><span class="sxs-lookup"><span data-stu-id="83119-193">**image**</span></span>|<span data-ttu-id="83119-194">登录用户的安全标识号 (SID)。</span><span class="sxs-lookup"><span data-stu-id="83119-194">Security identification number (SID) of the logged-in user.</span></span> <span data-ttu-id="83119-195">您可以在 sys.server_principals 目录视图中找到此信息。</span><span class="sxs-lookup"><span data-stu-id="83119-195">You can find this information in the sys.server_principals catalog view.</span></span> <span data-ttu-id="83119-196">服务器中的每个登录名都具有唯一的 SID。</span><span class="sxs-lookup"><span data-stu-id="83119-196">Each SID is unique for each login in the server.</span></span>|<span data-ttu-id="83119-197">41</span><span class="sxs-lookup"><span data-stu-id="83119-197">41</span></span>|<span data-ttu-id="83119-198">是</span><span class="sxs-lookup"><span data-stu-id="83119-198">Yes</span></span>|  
|<span data-ttu-id="83119-199">**NTDomainName**</span><span class="sxs-lookup"><span data-stu-id="83119-199">**NTDomainName**</span></span>|<span data-ttu-id="83119-200">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="83119-200">**nvarchar**</span></span>|<span data-ttu-id="83119-201">用户所属的 Windows 域。</span><span class="sxs-lookup"><span data-stu-id="83119-201">Windows domain to which the user belongs.</span></span>|<span data-ttu-id="83119-202">7</span><span class="sxs-lookup"><span data-stu-id="83119-202">7</span></span>|<span data-ttu-id="83119-203">是</span><span class="sxs-lookup"><span data-stu-id="83119-203">Yes</span></span>|  
|<span data-ttu-id="83119-204">**NTUserName**</span><span class="sxs-lookup"><span data-stu-id="83119-204">**NTUserName**</span></span>|<span data-ttu-id="83119-205">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="83119-205">**nvarchar**</span></span>|<span data-ttu-id="83119-206">Windows 用户名。</span><span class="sxs-lookup"><span data-stu-id="83119-206">Windows user name.</span></span>|<span data-ttu-id="83119-207">6</span><span class="sxs-lookup"><span data-stu-id="83119-207">6</span></span>|<span data-ttu-id="83119-208">是</span><span class="sxs-lookup"><span data-stu-id="83119-208">Yes</span></span>|  
|<span data-ttu-id="83119-209">**RequestID**</span><span class="sxs-lookup"><span data-stu-id="83119-209">**RequestID**</span></span>|<span data-ttu-id="83119-210">**int**</span><span class="sxs-lookup"><span data-stu-id="83119-210">**int**</span></span>|<span data-ttu-id="83119-211">启动全文查询的请求标识。</span><span class="sxs-lookup"><span data-stu-id="83119-211">Request identification that initiated the full-text query.</span></span>|<span data-ttu-id="83119-212">49</span><span class="sxs-lookup"><span data-stu-id="83119-212">49</span></span>|<span data-ttu-id="83119-213">是</span><span class="sxs-lookup"><span data-stu-id="83119-213">Yes</span></span>|  
|<span data-ttu-id="83119-214">**ServerName**</span><span class="sxs-lookup"><span data-stu-id="83119-214">**ServerName**</span></span>|<span data-ttu-id="83119-215">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="83119-215">**nvarchar**</span></span>|<span data-ttu-id="83119-216">所跟踪的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例的名称。</span><span class="sxs-lookup"><span data-stu-id="83119-216">Name of the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] being traced.</span></span>|<span data-ttu-id="83119-217">26</span><span class="sxs-lookup"><span data-stu-id="83119-217">26</span></span>|<span data-ttu-id="83119-218">否</span><span class="sxs-lookup"><span data-stu-id="83119-218">No</span></span>|  
|<span data-ttu-id="83119-219">**SessionLoginName**</span><span class="sxs-lookup"><span data-stu-id="83119-219">**SessionLoginName**</span></span>|<span data-ttu-id="83119-220">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="83119-220">**nvarchar**</span></span>|<span data-ttu-id="83119-221">发起会话的用户的登录名。</span><span class="sxs-lookup"><span data-stu-id="83119-221">Login name of the user who originated the session.</span></span> <span data-ttu-id="83119-222">例如，如果你使用 Login1 连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，再以 Login2 的身份执行语句，则 **SessionLoginName** 将显示 Login1，而 **LoginName** 将显示 Login2。</span><span class="sxs-lookup"><span data-stu-id="83119-222">For example, if you connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using Login1 and execute a statement as Login2, **SessionLoginName** shows Login1 and **LoginName** shows Login2.</span></span> <span data-ttu-id="83119-223">此列将同时显示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名和 Windows 登录名。</span><span class="sxs-lookup"><span data-stu-id="83119-223">This column displays both [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and Windows logins.</span></span>|<span data-ttu-id="83119-224">64</span><span class="sxs-lookup"><span data-stu-id="83119-224">64</span></span>|<span data-ttu-id="83119-225">是</span><span class="sxs-lookup"><span data-stu-id="83119-225">Yes</span></span>|  
|<span data-ttu-id="83119-226">**SPID**</span><span class="sxs-lookup"><span data-stu-id="83119-226">**SPID**</span></span>|<span data-ttu-id="83119-227">**int**</span><span class="sxs-lookup"><span data-stu-id="83119-227">**int**</span></span>|<span data-ttu-id="83119-228">发生该事件的会话的 ID。</span><span class="sxs-lookup"><span data-stu-id="83119-228">ID of the session on which the event occurred.</span></span>|<span data-ttu-id="83119-229">12</span><span class="sxs-lookup"><span data-stu-id="83119-229">12</span></span>|<span data-ttu-id="83119-230">是</span><span class="sxs-lookup"><span data-stu-id="83119-230">Yes</span></span>|  
|<span data-ttu-id="83119-231">**StartTime**</span><span class="sxs-lookup"><span data-stu-id="83119-231">**StartTime**</span></span>|<span data-ttu-id="83119-232">**datetime**</span><span class="sxs-lookup"><span data-stu-id="83119-232">**datetime**</span></span>|<span data-ttu-id="83119-233">该事件（如果存在）的启动时间。</span><span class="sxs-lookup"><span data-stu-id="83119-233">Time at which the event started, if available.</span></span>|<span data-ttu-id="83119-234">14</span><span class="sxs-lookup"><span data-stu-id="83119-234">14</span></span>|<span data-ttu-id="83119-235">是</span><span class="sxs-lookup"><span data-stu-id="83119-235">Yes</span></span>|  
|<span data-ttu-id="83119-236">**TransactionID**</span><span class="sxs-lookup"><span data-stu-id="83119-236">**TransactionID**</span></span>|<span data-ttu-id="83119-237">**bigint**</span><span class="sxs-lookup"><span data-stu-id="83119-237">**bigint**</span></span>|<span data-ttu-id="83119-238">系统分配的事务 ID。</span><span class="sxs-lookup"><span data-stu-id="83119-238">System-assigned ID of the transaction.</span></span>|<span data-ttu-id="83119-239">4</span><span class="sxs-lookup"><span data-stu-id="83119-239">4</span></span>|<span data-ttu-id="83119-240">是</span><span class="sxs-lookup"><span data-stu-id="83119-240">Yes</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="83119-241">另请参阅</span><span class="sxs-lookup"><span data-stu-id="83119-241">See Also</span></span>  
 <span data-ttu-id="83119-242">[sp_trace_setevent (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="83119-242">[sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql) </span></span>  
 [<span data-ttu-id="83119-243">INSERT (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="83119-243">INSERT &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/insert-transact-sql)  
  
  