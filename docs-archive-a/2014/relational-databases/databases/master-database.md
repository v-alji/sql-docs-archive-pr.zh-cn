---
title: master 数据库 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- master database [SQL Server], about
- master database [SQL Server]
ms.assetid: 660e909f-61eb-406b-bbce-8864dd629ba0
author: stevestein
ms.author: sstein
ms.openlocfilehash: ac38453237ed6816c32ed974e8141c57c93ceb44
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693921"
---
# <a name="master-database"></a><span data-ttu-id="33099-102">master 数据库</span><span class="sxs-lookup"><span data-stu-id="33099-102">master Database</span></span>
  <span data-ttu-id="33099-103">**master** 数据库记录 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 系统的所有系统级信息。</span><span class="sxs-lookup"><span data-stu-id="33099-103">The **master** database records all the system-level information for a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system.</span></span> <span data-ttu-id="33099-104">这包括实例范围的元数据（例如登录帐户）、端点、链接服务器和系统配置设置。</span><span class="sxs-lookup"><span data-stu-id="33099-104">This includes instance-wide metadata such as logon accounts, endpoints, linked servers, and system configuration settings.</span></span> <span data-ttu-id="33099-105">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中，系统对象不再存储在 **master** 数据库中，而是存储在 [Resource 数据库](resource-database.md)中。</span><span class="sxs-lookup"><span data-stu-id="33099-105">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], system objects are no longer stored in the **master** database; instead, they are stored in the [Resource database](resource-database.md).</span></span> <span data-ttu-id="33099-106">此外， **master** 数据库还记录了所有其他数据库的存在、数据库文件的位置以及 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的初始化信息。</span><span class="sxs-lookup"><span data-stu-id="33099-106">Also, **master** is the database that records the existence of all other databases and the location of those database files and records the initialization information for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="33099-107">因此，如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] master **数据库不可用，则** 无法启动。</span><span class="sxs-lookup"><span data-stu-id="33099-107">Therefore, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cannot start if the **master** database is unavailable.</span></span>  
  
## <a name="physical-properties-of-master"></a><span data-ttu-id="33099-108">master 数据库的物理属性</span><span class="sxs-lookup"><span data-stu-id="33099-108">Physical Properties of master</span></span>  
 <span data-ttu-id="33099-109">下表列出了 **master** 数据和日志文件的初始配置值。</span><span class="sxs-lookup"><span data-stu-id="33099-109">The following table lists the initial configuration values of the **master** data and log files.</span></span> <span data-ttu-id="33099-110">对于不同版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，这些文件的大小可能略有不同。</span><span class="sxs-lookup"><span data-stu-id="33099-110">The sizes of these files may vary slightly for different editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
|<span data-ttu-id="33099-111">文件</span><span class="sxs-lookup"><span data-stu-id="33099-111">File</span></span>|<span data-ttu-id="33099-112">逻辑名称</span><span class="sxs-lookup"><span data-stu-id="33099-112">Logical name</span></span>|<span data-ttu-id="33099-113">物理名称</span><span class="sxs-lookup"><span data-stu-id="33099-113">Physical name</span></span>|<span data-ttu-id="33099-114">文件增长</span><span class="sxs-lookup"><span data-stu-id="33099-114">File growth</span></span>|  
|----------|------------------|-------------------|-----------------|  
|<span data-ttu-id="33099-115">主数据</span><span class="sxs-lookup"><span data-stu-id="33099-115">Primary data</span></span>|<span data-ttu-id="33099-116">主</span><span class="sxs-lookup"><span data-stu-id="33099-116">master</span></span>|<span data-ttu-id="33099-117">master.mdf</span><span class="sxs-lookup"><span data-stu-id="33099-117">master.mdf</span></span>|<span data-ttu-id="33099-118">以 10% 的速度自动增长到磁盘充满为止。</span><span class="sxs-lookup"><span data-stu-id="33099-118">Autogrow by 10 percent until the disk is full.</span></span>|  
|<span data-ttu-id="33099-119">日志</span><span class="sxs-lookup"><span data-stu-id="33099-119">Log</span></span>|<span data-ttu-id="33099-120">mastlog</span><span class="sxs-lookup"><span data-stu-id="33099-120">mastlog</span></span>|<span data-ttu-id="33099-121">mastlog.ldf</span><span class="sxs-lookup"><span data-stu-id="33099-121">mastlog.ldf</span></span>|<span data-ttu-id="33099-122">以 10% 的速度自动增长到最大 2 TB。</span><span class="sxs-lookup"><span data-stu-id="33099-122">Autogrow by 10 percent to a maximum of 2 terabytes.</span></span>|  
  
 <span data-ttu-id="33099-123">有关如何移动 **master** 数据和日志文件的信息，请参阅 [移动系统数据库](system-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="33099-123">For information about how to move the **master** data and log files, see [Move System Databases](system-databases.md).</span></span>  
  
### <a name="database-options"></a><span data-ttu-id="33099-124">数据库选项</span><span class="sxs-lookup"><span data-stu-id="33099-124">Database Options</span></span>  
 <span data-ttu-id="33099-125">下表列出了 **master** 数据库中每个数据库选项的默认值以及该选项是否可以修改。</span><span class="sxs-lookup"><span data-stu-id="33099-125">The following table lists the default value for each database option in the **master** database and whether the option can be modified.</span></span> <span data-ttu-id="33099-126">若要查看这些选项的当前设置，请使用 [sys.databases](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) 目录视图。</span><span class="sxs-lookup"><span data-stu-id="33099-126">To view the current settings for these options, use the [sys.databases](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) catalog view.</span></span>  
  
|<span data-ttu-id="33099-127">数据库选项</span><span class="sxs-lookup"><span data-stu-id="33099-127">Database option</span></span>|<span data-ttu-id="33099-128">默认值</span><span class="sxs-lookup"><span data-stu-id="33099-128">Default value</span></span>|<span data-ttu-id="33099-129">是否可修改</span><span class="sxs-lookup"><span data-stu-id="33099-129">Can be modified</span></span>|  
|---------------------|-------------------|---------------------|  
|<span data-ttu-id="33099-130">ALLOW_SNAPSHOT_ISOLATION</span><span class="sxs-lookup"><span data-stu-id="33099-130">ALLOW_SNAPSHOT_ISOLATION</span></span>|<span data-ttu-id="33099-131">ON</span><span class="sxs-lookup"><span data-stu-id="33099-131">ON</span></span>|<span data-ttu-id="33099-132">否</span><span class="sxs-lookup"><span data-stu-id="33099-132">No</span></span>|  
|<span data-ttu-id="33099-133">ANSI_NULL_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="33099-133">ANSI_NULL_DEFAULT</span></span>|<span data-ttu-id="33099-134">OFF</span><span class="sxs-lookup"><span data-stu-id="33099-134">OFF</span></span>|<span data-ttu-id="33099-135">是</span><span class="sxs-lookup"><span data-stu-id="33099-135">Yes</span></span>|  
|<span data-ttu-id="33099-136">ANSI_NULLS</span><span class="sxs-lookup"><span data-stu-id="33099-136">ANSI_NULLS</span></span>|<span data-ttu-id="33099-137">OFF</span><span class="sxs-lookup"><span data-stu-id="33099-137">OFF</span></span>|<span data-ttu-id="33099-138">是</span><span class="sxs-lookup"><span data-stu-id="33099-138">Yes</span></span>|  
|<span data-ttu-id="33099-139">ANSI_PADDING</span><span class="sxs-lookup"><span data-stu-id="33099-139">ANSI_PADDING</span></span>|<span data-ttu-id="33099-140">OFF</span><span class="sxs-lookup"><span data-stu-id="33099-140">OFF</span></span>|<span data-ttu-id="33099-141">是</span><span class="sxs-lookup"><span data-stu-id="33099-141">Yes</span></span>|  
|<span data-ttu-id="33099-142">ANSI_WARNINGS</span><span class="sxs-lookup"><span data-stu-id="33099-142">ANSI_WARNINGS</span></span>|<span data-ttu-id="33099-143">OFF</span><span class="sxs-lookup"><span data-stu-id="33099-143">OFF</span></span>|<span data-ttu-id="33099-144">是</span><span class="sxs-lookup"><span data-stu-id="33099-144">Yes</span></span>|  
|<span data-ttu-id="33099-145">ARITHABORT</span><span class="sxs-lookup"><span data-stu-id="33099-145">ARITHABORT</span></span>|<span data-ttu-id="33099-146">OFF</span><span class="sxs-lookup"><span data-stu-id="33099-146">OFF</span></span>|<span data-ttu-id="33099-147">是</span><span class="sxs-lookup"><span data-stu-id="33099-147">Yes</span></span>|  
|<span data-ttu-id="33099-148">AUTO_CLOSE</span><span class="sxs-lookup"><span data-stu-id="33099-148">AUTO_CLOSE</span></span>|<span data-ttu-id="33099-149">OFF</span><span class="sxs-lookup"><span data-stu-id="33099-149">OFF</span></span>|<span data-ttu-id="33099-150">否</span><span class="sxs-lookup"><span data-stu-id="33099-150">No</span></span>|  
|<span data-ttu-id="33099-151">AUTO_CREATE_STATISTICS</span><span class="sxs-lookup"><span data-stu-id="33099-151">AUTO_CREATE_STATISTICS</span></span>|<span data-ttu-id="33099-152">ON</span><span class="sxs-lookup"><span data-stu-id="33099-152">ON</span></span>|<span data-ttu-id="33099-153">是</span><span class="sxs-lookup"><span data-stu-id="33099-153">Yes</span></span>|  
|<span data-ttu-id="33099-154">AUTO_SHRINK</span><span class="sxs-lookup"><span data-stu-id="33099-154">AUTO_SHRINK</span></span>|<span data-ttu-id="33099-155">OFF</span><span class="sxs-lookup"><span data-stu-id="33099-155">OFF</span></span>|<span data-ttu-id="33099-156">否</span><span class="sxs-lookup"><span data-stu-id="33099-156">No</span></span>|  
|<span data-ttu-id="33099-157">AUTO_UPDATE_STATISTICS</span><span class="sxs-lookup"><span data-stu-id="33099-157">AUTO_UPDATE_STATISTICS</span></span>|<span data-ttu-id="33099-158">ON</span><span class="sxs-lookup"><span data-stu-id="33099-158">ON</span></span>|<span data-ttu-id="33099-159">是</span><span class="sxs-lookup"><span data-stu-id="33099-159">Yes</span></span>|  
|<span data-ttu-id="33099-160">AUTO_UPDATE_STATISTICS_ASYNC</span><span class="sxs-lookup"><span data-stu-id="33099-160">AUTO_UPDATE_STATISTICS_ASYNC</span></span>|<span data-ttu-id="33099-161">OFF</span><span class="sxs-lookup"><span data-stu-id="33099-161">OFF</span></span>|<span data-ttu-id="33099-162">是</span><span class="sxs-lookup"><span data-stu-id="33099-162">Yes</span></span>|  
|<span data-ttu-id="33099-163">CHANGE_TRACKING</span><span class="sxs-lookup"><span data-stu-id="33099-163">CHANGE_TRACKING</span></span>|<span data-ttu-id="33099-164">OFF</span><span class="sxs-lookup"><span data-stu-id="33099-164">OFF</span></span>|<span data-ttu-id="33099-165">否</span><span class="sxs-lookup"><span data-stu-id="33099-165">No</span></span>|  
|<span data-ttu-id="33099-166">CONCAT_NULL_YIELDS_NULL</span><span class="sxs-lookup"><span data-stu-id="33099-166">CONCAT_NULL_YIELDS_NULL</span></span>|<span data-ttu-id="33099-167">OFF</span><span class="sxs-lookup"><span data-stu-id="33099-167">OFF</span></span>|<span data-ttu-id="33099-168">是</span><span class="sxs-lookup"><span data-stu-id="33099-168">Yes</span></span>|  
|<span data-ttu-id="33099-169">CURSOR_CLOSE_ON_COMMIT</span><span class="sxs-lookup"><span data-stu-id="33099-169">CURSOR_CLOSE_ON_COMMIT</span></span>|<span data-ttu-id="33099-170">OFF</span><span class="sxs-lookup"><span data-stu-id="33099-170">OFF</span></span>|<span data-ttu-id="33099-171">是</span><span class="sxs-lookup"><span data-stu-id="33099-171">Yes</span></span>|  
|<span data-ttu-id="33099-172">CURSOR_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="33099-172">CURSOR_DEFAULT</span></span>|<span data-ttu-id="33099-173">GLOBAL</span><span class="sxs-lookup"><span data-stu-id="33099-173">GLOBAL</span></span>|<span data-ttu-id="33099-174">是</span><span class="sxs-lookup"><span data-stu-id="33099-174">Yes</span></span>|  
|<span data-ttu-id="33099-175">数据库可用性选项</span><span class="sxs-lookup"><span data-stu-id="33099-175">Database Availability Options</span></span>|<span data-ttu-id="33099-176">ONLINE</span><span class="sxs-lookup"><span data-stu-id="33099-176">ONLINE</span></span><br /><br /> <span data-ttu-id="33099-177">MULTI_USER</span><span class="sxs-lookup"><span data-stu-id="33099-177">MULTI_USER</span></span><br /><br /> <span data-ttu-id="33099-178">READ_WRITE</span><span class="sxs-lookup"><span data-stu-id="33099-178">READ_WRITE</span></span>|<span data-ttu-id="33099-179">否</span><span class="sxs-lookup"><span data-stu-id="33099-179">No</span></span><br /><br /> <span data-ttu-id="33099-180">否</span><span class="sxs-lookup"><span data-stu-id="33099-180">No</span></span><br /><br /> <span data-ttu-id="33099-181">否</span><span class="sxs-lookup"><span data-stu-id="33099-181">No</span></span>|  
|<span data-ttu-id="33099-182">DATE_CORRELATION_OPTIMIZATION</span><span class="sxs-lookup"><span data-stu-id="33099-182">DATE_CORRELATION_OPTIMIZATION</span></span>|<span data-ttu-id="33099-183">OFF</span><span class="sxs-lookup"><span data-stu-id="33099-183">OFF</span></span>|<span data-ttu-id="33099-184">是</span><span class="sxs-lookup"><span data-stu-id="33099-184">Yes</span></span>|  
|<span data-ttu-id="33099-185">DB_CHAINING</span><span class="sxs-lookup"><span data-stu-id="33099-185">DB_CHAINING</span></span>|<span data-ttu-id="33099-186">ON</span><span class="sxs-lookup"><span data-stu-id="33099-186">ON</span></span>|<span data-ttu-id="33099-187">否</span><span class="sxs-lookup"><span data-stu-id="33099-187">No</span></span>|  
|<span data-ttu-id="33099-188">ENCRYPTION</span><span class="sxs-lookup"><span data-stu-id="33099-188">ENCRYPTION</span></span>|<span data-ttu-id="33099-189">OFF</span><span class="sxs-lookup"><span data-stu-id="33099-189">OFF</span></span>|<span data-ttu-id="33099-190">否</span><span class="sxs-lookup"><span data-stu-id="33099-190">No</span></span>|  
|<span data-ttu-id="33099-191">NUMERIC_ROUNDABORT</span><span class="sxs-lookup"><span data-stu-id="33099-191">NUMERIC_ROUNDABORT</span></span>|<span data-ttu-id="33099-192">OFF</span><span class="sxs-lookup"><span data-stu-id="33099-192">OFF</span></span>|<span data-ttu-id="33099-193">是</span><span class="sxs-lookup"><span data-stu-id="33099-193">Yes</span></span>|  
|<span data-ttu-id="33099-194">PAGE_VERIFY</span><span class="sxs-lookup"><span data-stu-id="33099-194">PAGE_VERIFY</span></span>|<span data-ttu-id="33099-195">CHECKSUM</span><span class="sxs-lookup"><span data-stu-id="33099-195">CHECKSUM</span></span>|<span data-ttu-id="33099-196">是</span><span class="sxs-lookup"><span data-stu-id="33099-196">Yes</span></span>|  
|<span data-ttu-id="33099-197">PARAMETERIZATION</span><span class="sxs-lookup"><span data-stu-id="33099-197">PARAMETERIZATION</span></span>|<span data-ttu-id="33099-198">SIMPLE</span><span class="sxs-lookup"><span data-stu-id="33099-198">SIMPLE</span></span>|<span data-ttu-id="33099-199">是</span><span class="sxs-lookup"><span data-stu-id="33099-199">Yes</span></span>|  
|<span data-ttu-id="33099-200">QUOTED_IDENTIFIER</span><span class="sxs-lookup"><span data-stu-id="33099-200">QUOTED_IDENTIFIER</span></span>|<span data-ttu-id="33099-201">OFF</span><span class="sxs-lookup"><span data-stu-id="33099-201">OFF</span></span>|<span data-ttu-id="33099-202">是</span><span class="sxs-lookup"><span data-stu-id="33099-202">Yes</span></span>|  
|<span data-ttu-id="33099-203">READ_COMMITTED_SNAPSHOT</span><span class="sxs-lookup"><span data-stu-id="33099-203">READ_COMMITTED_SNAPSHOT</span></span>|<span data-ttu-id="33099-204">OFF</span><span class="sxs-lookup"><span data-stu-id="33099-204">OFF</span></span>|<span data-ttu-id="33099-205">否</span><span class="sxs-lookup"><span data-stu-id="33099-205">No</span></span>|  
|<span data-ttu-id="33099-206">RECOVERY</span><span class="sxs-lookup"><span data-stu-id="33099-206">RECOVERY</span></span>|<span data-ttu-id="33099-207">SIMPLE</span><span class="sxs-lookup"><span data-stu-id="33099-207">SIMPLE</span></span>|<span data-ttu-id="33099-208">是</span><span class="sxs-lookup"><span data-stu-id="33099-208">Yes</span></span>|  
|<span data-ttu-id="33099-209">RECURSIVE_TRIGGERS</span><span class="sxs-lookup"><span data-stu-id="33099-209">RECURSIVE_TRIGGERS</span></span>|<span data-ttu-id="33099-210">OFF</span><span class="sxs-lookup"><span data-stu-id="33099-210">OFF</span></span>|<span data-ttu-id="33099-211">是</span><span class="sxs-lookup"><span data-stu-id="33099-211">Yes</span></span>|  
|<span data-ttu-id="33099-212">Service Broker 选项</span><span class="sxs-lookup"><span data-stu-id="33099-212">Service Broker Options</span></span>|<span data-ttu-id="33099-213">DISABLE_BROKER</span><span class="sxs-lookup"><span data-stu-id="33099-213">DISABLE_BROKER</span></span>|<span data-ttu-id="33099-214">否</span><span class="sxs-lookup"><span data-stu-id="33099-214">No</span></span>|  
|<span data-ttu-id="33099-215">TRUSTWORTHY</span><span class="sxs-lookup"><span data-stu-id="33099-215">TRUSTWORTHY</span></span>|<span data-ttu-id="33099-216">OFF</span><span class="sxs-lookup"><span data-stu-id="33099-216">OFF</span></span>|<span data-ttu-id="33099-217">是</span><span class="sxs-lookup"><span data-stu-id="33099-217">Yes</span></span>|  
  
 <span data-ttu-id="33099-218">有关这些数据库选项的说明，请参阅 [ALTER DATABASE (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="33099-218">For a description of these database options, see [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql).</span></span>  
  
## <a name="restrictions"></a><span data-ttu-id="33099-219">限制</span><span class="sxs-lookup"><span data-stu-id="33099-219">Restrictions</span></span>  
 <span data-ttu-id="33099-220">不能在 **master** 数据库中执行下列操作：</span><span class="sxs-lookup"><span data-stu-id="33099-220">The following operations cannot be performed on the **master** database:</span></span>  
  
-   <span data-ttu-id="33099-221">添加文件或文件组。</span><span class="sxs-lookup"><span data-stu-id="33099-221">Adding files or filegroups.</span></span>  
  
-   <span data-ttu-id="33099-222">更改排序规则。</span><span class="sxs-lookup"><span data-stu-id="33099-222">Changing collation.</span></span> <span data-ttu-id="33099-223">默认排序规则为服务器排序规则。</span><span class="sxs-lookup"><span data-stu-id="33099-223">The default collation is the server collation.</span></span>  
  
-   <span data-ttu-id="33099-224">更改数据库所有者。</span><span class="sxs-lookup"><span data-stu-id="33099-224">Changing the database owner.</span></span> <span data-ttu-id="33099-225">**master** 的所有者是 **sa**。</span><span class="sxs-lookup"><span data-stu-id="33099-225">**master** is owned by **sa**.</span></span>  
  
-   <span data-ttu-id="33099-226">创建全文目录或全文索引。</span><span class="sxs-lookup"><span data-stu-id="33099-226">Creating a full-text catalog or full-text index.</span></span>  
  
-   <span data-ttu-id="33099-227">在数据库的系统表上创建触发器。</span><span class="sxs-lookup"><span data-stu-id="33099-227">Creating triggers on system tables in the database.</span></span>  
  
-   <span data-ttu-id="33099-228">删除数据库。</span><span class="sxs-lookup"><span data-stu-id="33099-228">Dropping the database.</span></span>  
  
-   <span data-ttu-id="33099-229">正在从数据库中删除**guest**用户。</span><span class="sxs-lookup"><span data-stu-id="33099-229">Dropping the **guest** user from the database.</span></span>  
  
-   <span data-ttu-id="33099-230">启用变更数据捕获。</span><span class="sxs-lookup"><span data-stu-id="33099-230">Enabling change data capture.</span></span>  
  
-   <span data-ttu-id="33099-231">参与数据库镜像。</span><span class="sxs-lookup"><span data-stu-id="33099-231">Participating in database mirroring.</span></span>  
  
-   <span data-ttu-id="33099-232">删除主文件组、主数据文件或日志文件。</span><span class="sxs-lookup"><span data-stu-id="33099-232">Removing the primary filegroup, primary data file, or log file.</span></span>  
  
-   <span data-ttu-id="33099-233">重命名数据库或主文件组。</span><span class="sxs-lookup"><span data-stu-id="33099-233">Renaming the database or primary filegroup.</span></span>  
  
-   <span data-ttu-id="33099-234">将数据库设置为 OFFLINE。</span><span class="sxs-lookup"><span data-stu-id="33099-234">Setting the database to OFFLINE.</span></span>  
  
-   <span data-ttu-id="33099-235">将数据库或主文件组设置为 READ_ONLY。</span><span class="sxs-lookup"><span data-stu-id="33099-235">Setting the database or primary filegroup to READ_ONLY.</span></span>  
  
## <a name="recommendations"></a><span data-ttu-id="33099-236">建议</span><span class="sxs-lookup"><span data-stu-id="33099-236">Recommendations</span></span>  
 <span data-ttu-id="33099-237">使用 **master** 数据库时，请考虑下列建议：</span><span class="sxs-lookup"><span data-stu-id="33099-237">When you work with the **master** database, consider the following recommendations:</span></span>  
  
-   <span data-ttu-id="33099-238">始终有一个 **master** 数据库的当前备份可用。</span><span class="sxs-lookup"><span data-stu-id="33099-238">Always have a current backup of the **master** database available.</span></span>  
  
-   <span data-ttu-id="33099-239">执行下列操作后，尽快备份 **master** 数据库：</span><span class="sxs-lookup"><span data-stu-id="33099-239">Back up the **master** database as soon as possible after the following operations:</span></span>  
  
    -   <span data-ttu-id="33099-240">创建、修改或删除任意数据库</span><span class="sxs-lookup"><span data-stu-id="33099-240">Creating, modifying, or dropping any database</span></span>  
  
    -   <span data-ttu-id="33099-241">更改服务器或数据库的配置值</span><span class="sxs-lookup"><span data-stu-id="33099-241">Changing server or database configuration values</span></span>  
  
    -   <span data-ttu-id="33099-242">修改或添加登录帐户</span><span class="sxs-lookup"><span data-stu-id="33099-242">Modifying or adding logon accounts</span></span>  
  
-   <span data-ttu-id="33099-243">不要在 **master**中创建用户对象。</span><span class="sxs-lookup"><span data-stu-id="33099-243">Do not create user objects in **master**.</span></span> <span data-ttu-id="33099-244">否则，必须更频繁地备份 **master** 。</span><span class="sxs-lookup"><span data-stu-id="33099-244">If you do, **master** must be backed up more frequently.</span></span>  
  
-   <span data-ttu-id="33099-245">不要针对 **master** 数据库将 TRUSTWORTHY 选项设置为 ON。</span><span class="sxs-lookup"><span data-stu-id="33099-245">Do not set the TRUSTWORTHY option to ON for the **master** database.</span></span>  
  
## <a name="what-to-do-if-master-becomes-unusable"></a><span data-ttu-id="33099-246">当 master 不可用时怎么办</span><span class="sxs-lookup"><span data-stu-id="33099-246">What to Do If master Becomes Unusable</span></span>  
 <span data-ttu-id="33099-247">如果 **master** 数据库不可用，则可以通过下列两种方式之一将该数据库返回到可用状态：</span><span class="sxs-lookup"><span data-stu-id="33099-247">If **master** becomes unusable, you can return the database to a usable state in either of the following ways:</span></span>  
  
-   <span data-ttu-id="33099-248">从当前数据库备份还原 **master** 。</span><span class="sxs-lookup"><span data-stu-id="33099-248">Restore **master** from a current database backup.</span></span>  
  
     <span data-ttu-id="33099-249">如果你可以启动服务器实例，则应该能够从完整数据库备份还原 **master** 。</span><span class="sxs-lookup"><span data-stu-id="33099-249">If you can start the server instance, you should be able to restore **master** from a full database backup.</span></span> <span data-ttu-id="33099-250">有关详细信息，请参阅[还原 master 数据库 (Transact-SQL)](../backup-restore/restore-the-master-database-transact-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="33099-250">For more information, see [Restore the master Database &#40;Transact-SQL&#41;](../backup-restore/restore-the-master-database-transact-sql.md).</span></span>  
  
-   <span data-ttu-id="33099-251">完全重新生成 **master** 。</span><span class="sxs-lookup"><span data-stu-id="33099-251">Rebuild **master** completely.</span></span>  
  
     <span data-ttu-id="33099-252">如果由于 **master** 严重损坏而无法启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，则必须重新生成 **master**。</span><span class="sxs-lookup"><span data-stu-id="33099-252">If severe damage to **master** prevents you from starting [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you must rebuild **master**.</span></span> <span data-ttu-id="33099-253">有关详细信息，请参阅 [重新生成系统数据库](rebuild-system-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="33099-253">For more information, see [Rebuild System Databases](rebuild-system-databases.md).</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="33099-254">重新生成 **master** 将重新生成所有系统数据库。</span><span class="sxs-lookup"><span data-stu-id="33099-254">Rebuilding **master** rebuilds all of the system databases.</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="33099-255">相关内容</span><span class="sxs-lookup"><span data-stu-id="33099-255">Related Content</span></span>  
 [<span data-ttu-id="33099-256">重新生成系统数据库</span><span class="sxs-lookup"><span data-stu-id="33099-256">Rebuild System Databases</span></span>](rebuild-system-databases.md)  
  
 [<span data-ttu-id="33099-257">系统数据库</span><span class="sxs-lookup"><span data-stu-id="33099-257">System Databases</span></span>](system-databases.md)  
  
 [<span data-ttu-id="33099-258">sys.databases (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="33099-258">sys.databases &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)  
  
 [<span data-ttu-id="33099-259">sys.master_files (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="33099-259">sys.master_files &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-master-files-transact-sql)  
  
 [<span data-ttu-id="33099-260">移动数据库文件</span><span class="sxs-lookup"><span data-stu-id="33099-260">Move Database Files</span></span>](move-database-files.md)  
  
  
