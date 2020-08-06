---
title: ObjectType 跟踪事件列 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- SQL Server event classes, Object Type column values
- events [SQL Server], Object Type column values
- event classes [SQL Server], Object Type column values
- Object Type column values [SQL Server]
ms.assetid: 42f85c50-34c9-49ca-955f-af9595e2707f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1f90661e5ebedc91505989c3d80dcec78436ce86
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579599"
---
# <a name="objecttype-trace-event-column"></a><span data-ttu-id="dea46-102">ObjectType 跟踪事件列</span><span class="sxs-lookup"><span data-stu-id="dea46-102">ObjectType Trace Event Column</span></span>
  <span data-ttu-id="dea46-103">ObjectType 跟踪事件列用在各种跟踪事件中。</span><span class="sxs-lookup"><span data-stu-id="dea46-103">The Object Type trace event column is used in a variety of trace events.</span></span> <span data-ttu-id="dea46-104">本主题说明此列的可能值以及其相关定义。</span><span class="sxs-lookup"><span data-stu-id="dea46-104">This topic describes the possible values of this column and their associated definitions.</span></span>  
  
## <a name="object-type-column-values"></a><span data-ttu-id="dea46-105">ObjectType 列值</span><span class="sxs-lookup"><span data-stu-id="dea46-105">Object Type Column Values</span></span>  
  
|<span data-ttu-id="dea46-106">值</span><span class="sxs-lookup"><span data-stu-id="dea46-106">Value</span></span>|<span data-ttu-id="dea46-107">定义</span><span class="sxs-lookup"><span data-stu-id="dea46-107">Definition</span></span>|  
|-----------|----------------|  
|<span data-ttu-id="dea46-108">8259</span><span class="sxs-lookup"><span data-stu-id="dea46-108">8259</span></span>|<span data-ttu-id="dea46-109">检查约束</span><span class="sxs-lookup"><span data-stu-id="dea46-109">Check Constraint</span></span>|  
|<span data-ttu-id="dea46-110">8260</span><span class="sxs-lookup"><span data-stu-id="dea46-110">8260</span></span>|<span data-ttu-id="dea46-111">默认值（约束或独立）</span><span class="sxs-lookup"><span data-stu-id="dea46-111">Default (constraint or standalone)</span></span>|  
|<span data-ttu-id="dea46-112">8262</span><span class="sxs-lookup"><span data-stu-id="dea46-112">8262</span></span>|<span data-ttu-id="dea46-113">外键约束</span><span class="sxs-lookup"><span data-stu-id="dea46-113">Foreign-key Constraint</span></span>|  
|<span data-ttu-id="dea46-114">8272</span><span class="sxs-lookup"><span data-stu-id="dea46-114">8272</span></span>|<span data-ttu-id="dea46-115">存储过程</span><span class="sxs-lookup"><span data-stu-id="dea46-115">Stored Procedure</span></span>|  
|<span data-ttu-id="dea46-116">8274</span><span class="sxs-lookup"><span data-stu-id="dea46-116">8274</span></span>|<span data-ttu-id="dea46-117">规则</span><span class="sxs-lookup"><span data-stu-id="dea46-117">Rule</span></span>|  
|<span data-ttu-id="dea46-118">8275</span><span class="sxs-lookup"><span data-stu-id="dea46-118">8275</span></span>|<span data-ttu-id="dea46-119">系统表</span><span class="sxs-lookup"><span data-stu-id="dea46-119">System Table</span></span>|  
|<span data-ttu-id="dea46-120">8276</span><span class="sxs-lookup"><span data-stu-id="dea46-120">8276</span></span>|<span data-ttu-id="dea46-121">服务器上的触发器</span><span class="sxs-lookup"><span data-stu-id="dea46-121">Trigger on Server</span></span>|  
|<span data-ttu-id="dea46-122">8277</span><span class="sxs-lookup"><span data-stu-id="dea46-122">8277</span></span>|<span data-ttu-id="dea46-123">（用户定义的）表</span><span class="sxs-lookup"><span data-stu-id="dea46-123">(User-defined) Table</span></span>|  
|<span data-ttu-id="dea46-124">8278</span><span class="sxs-lookup"><span data-stu-id="dea46-124">8278</span></span>|<span data-ttu-id="dea46-125">查看</span><span class="sxs-lookup"><span data-stu-id="dea46-125">View</span></span>|  
|<span data-ttu-id="dea46-126">8280</span><span class="sxs-lookup"><span data-stu-id="dea46-126">8280</span></span>|<span data-ttu-id="dea46-127">扩展存储过程</span><span class="sxs-lookup"><span data-stu-id="dea46-127">Extended Stored Procedure</span></span>|  
|<span data-ttu-id="dea46-128">16724</span><span class="sxs-lookup"><span data-stu-id="dea46-128">16724</span></span>|<span data-ttu-id="dea46-129">CLR 触发器</span><span class="sxs-lookup"><span data-stu-id="dea46-129">CLR Trigger</span></span>|  
|<span data-ttu-id="dea46-130">16964</span><span class="sxs-lookup"><span data-stu-id="dea46-130">16964</span></span>|<span data-ttu-id="dea46-131">数据库</span><span class="sxs-lookup"><span data-stu-id="dea46-131">Database</span></span>|  
|<span data-ttu-id="dea46-132">16975</span><span class="sxs-lookup"><span data-stu-id="dea46-132">16975</span></span>|<span data-ttu-id="dea46-133">对象</span><span class="sxs-lookup"><span data-stu-id="dea46-133">Object</span></span>|  
|<span data-ttu-id="dea46-134">17222</span><span class="sxs-lookup"><span data-stu-id="dea46-134">17222</span></span>|<span data-ttu-id="dea46-135">全文目录</span><span class="sxs-lookup"><span data-stu-id="dea46-135">FullText Catalog</span></span>|  
|<span data-ttu-id="dea46-136">17232</span><span class="sxs-lookup"><span data-stu-id="dea46-136">17232</span></span>|<span data-ttu-id="dea46-137">CLR 存储过程</span><span class="sxs-lookup"><span data-stu-id="dea46-137">CLR Stored Procedure</span></span>|  
|<span data-ttu-id="dea46-138">17235</span><span class="sxs-lookup"><span data-stu-id="dea46-138">17235</span></span>|<span data-ttu-id="dea46-139">架构</span><span class="sxs-lookup"><span data-stu-id="dea46-139">Schema</span></span>|  
|<span data-ttu-id="dea46-140">17475</span><span class="sxs-lookup"><span data-stu-id="dea46-140">17475</span></span>|<span data-ttu-id="dea46-141">凭据</span><span class="sxs-lookup"><span data-stu-id="dea46-141">Credential</span></span>|  
|<span data-ttu-id="dea46-142">17491</span><span class="sxs-lookup"><span data-stu-id="dea46-142">17491</span></span>|<span data-ttu-id="dea46-143">DDL 事件</span><span class="sxs-lookup"><span data-stu-id="dea46-143">DDL Event</span></span>|  
|<span data-ttu-id="dea46-144">17741</span><span class="sxs-lookup"><span data-stu-id="dea46-144">17741</span></span>|<span data-ttu-id="dea46-145">管理事件</span><span class="sxs-lookup"><span data-stu-id="dea46-145">Management Event</span></span>|  
|<span data-ttu-id="dea46-146">17747</span><span class="sxs-lookup"><span data-stu-id="dea46-146">17747</span></span>|<span data-ttu-id="dea46-147">安全性事件</span><span class="sxs-lookup"><span data-stu-id="dea46-147">Security Event</span></span>|  
|<span data-ttu-id="dea46-148">17749</span><span class="sxs-lookup"><span data-stu-id="dea46-148">17749</span></span>|<span data-ttu-id="dea46-149">用户事件</span><span class="sxs-lookup"><span data-stu-id="dea46-149">User Event</span></span>|  
|<span data-ttu-id="dea46-150">17985</span><span class="sxs-lookup"><span data-stu-id="dea46-150">17985</span></span>|<span data-ttu-id="dea46-151">CLR 聚合函数</span><span class="sxs-lookup"><span data-stu-id="dea46-151">CLR Aggregate Function</span></span>|  
|<span data-ttu-id="dea46-152">17993</span><span class="sxs-lookup"><span data-stu-id="dea46-152">17993</span></span>|<span data-ttu-id="dea46-153">内联表值 SQL 函数</span><span class="sxs-lookup"><span data-stu-id="dea46-153">Inline Table-valued SQL Function</span></span>|  
|<span data-ttu-id="dea46-154">18000</span><span class="sxs-lookup"><span data-stu-id="dea46-154">18000</span></span>|<span data-ttu-id="dea46-155">分区函数</span><span class="sxs-lookup"><span data-stu-id="dea46-155">Partition Function</span></span>|  
|<span data-ttu-id="dea46-156">18002</span><span class="sxs-lookup"><span data-stu-id="dea46-156">18002</span></span>|<span data-ttu-id="dea46-157">复制筛选过程</span><span class="sxs-lookup"><span data-stu-id="dea46-157">Replication Filter Procedure</span></span>|  
|<span data-ttu-id="dea46-158">18004</span><span class="sxs-lookup"><span data-stu-id="dea46-158">18004</span></span>|<span data-ttu-id="dea46-159">表值 SQL 函数</span><span class="sxs-lookup"><span data-stu-id="dea46-159">Table-valued SQL Function</span></span>|  
|<span data-ttu-id="dea46-160">18259</span><span class="sxs-lookup"><span data-stu-id="dea46-160">18259</span></span>|<span data-ttu-id="dea46-161">服务器角色</span><span class="sxs-lookup"><span data-stu-id="dea46-161">Server Role</span></span>|  
|<span data-ttu-id="dea46-162">18263</span><span class="sxs-lookup"><span data-stu-id="dea46-162">18263</span></span>|[!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="dea46-163">Windows 组</span><span class="sxs-lookup"><span data-stu-id="dea46-163">Windows Group</span></span>|  
|<span data-ttu-id="dea46-164">19265</span><span class="sxs-lookup"><span data-stu-id="dea46-164">19265</span></span>|<span data-ttu-id="dea46-165">非对称密钥</span><span class="sxs-lookup"><span data-stu-id="dea46-165">Asymmetric Key</span></span>|  
|<span data-ttu-id="dea46-166">19277</span><span class="sxs-lookup"><span data-stu-id="dea46-166">19277</span></span>|<span data-ttu-id="dea46-167">主密钥</span><span class="sxs-lookup"><span data-stu-id="dea46-167">Master Key</span></span>|  
|<span data-ttu-id="dea46-168">19280</span><span class="sxs-lookup"><span data-stu-id="dea46-168">19280</span></span>|<span data-ttu-id="dea46-169">主密钥</span><span class="sxs-lookup"><span data-stu-id="dea46-169">Primary Key</span></span>|  
|<span data-ttu-id="dea46-170">19283</span><span class="sxs-lookup"><span data-stu-id="dea46-170">19283</span></span>|<span data-ttu-id="dea46-171">ObfusKey</span><span class="sxs-lookup"><span data-stu-id="dea46-171">ObfusKey</span></span>|  
|<span data-ttu-id="dea46-172">19521</span><span class="sxs-lookup"><span data-stu-id="dea46-172">19521</span></span>|<span data-ttu-id="dea46-173">非对称密钥登录名</span><span class="sxs-lookup"><span data-stu-id="dea46-173">Asymmetric Key Login</span></span>|  
|<span data-ttu-id="dea46-174">19523</span><span class="sxs-lookup"><span data-stu-id="dea46-174">19523</span></span>|<span data-ttu-id="dea46-175">证书登录</span><span class="sxs-lookup"><span data-stu-id="dea46-175">Certificate Login</span></span>|  
|<span data-ttu-id="dea46-176">19538</span><span class="sxs-lookup"><span data-stu-id="dea46-176">19538</span></span>|<span data-ttu-id="dea46-177">角色</span><span class="sxs-lookup"><span data-stu-id="dea46-177">Role</span></span>|  
|<span data-ttu-id="dea46-178">19539</span><span class="sxs-lookup"><span data-stu-id="dea46-178">19539</span></span>|<span data-ttu-id="dea46-179">SQL 登录名</span><span class="sxs-lookup"><span data-stu-id="dea46-179">SQL Login</span></span>|  
|<span data-ttu-id="dea46-180">19543</span><span class="sxs-lookup"><span data-stu-id="dea46-180">19543</span></span>|<span data-ttu-id="dea46-181">Windows 登录名</span><span class="sxs-lookup"><span data-stu-id="dea46-181">Windows Login</span></span>|  
|<span data-ttu-id="dea46-182">20034</span><span class="sxs-lookup"><span data-stu-id="dea46-182">20034</span></span>|<span data-ttu-id="dea46-183">远程服务绑定</span><span class="sxs-lookup"><span data-stu-id="dea46-183">Remote Service Binding</span></span>|  
|<span data-ttu-id="dea46-184">20036</span><span class="sxs-lookup"><span data-stu-id="dea46-184">20036</span></span>|<span data-ttu-id="dea46-185">数据库上的事件通知</span><span class="sxs-lookup"><span data-stu-id="dea46-185">Event Notification on Database</span></span>|  
|<span data-ttu-id="dea46-186">20037</span><span class="sxs-lookup"><span data-stu-id="dea46-186">20037</span></span>|<span data-ttu-id="dea46-187">事件通知</span><span class="sxs-lookup"><span data-stu-id="dea46-187">Event Notification</span></span>|  
|<span data-ttu-id="dea46-188">20038</span><span class="sxs-lookup"><span data-stu-id="dea46-188">20038</span></span>|<span data-ttu-id="dea46-189">标量 SQL 函数</span><span class="sxs-lookup"><span data-stu-id="dea46-189">Scalar SQL Function</span></span>|  
|<span data-ttu-id="dea46-190">20047</span><span class="sxs-lookup"><span data-stu-id="dea46-190">20047</span></span>|<span data-ttu-id="dea46-191">对象上的事件通知</span><span class="sxs-lookup"><span data-stu-id="dea46-191">Event Notification on Object</span></span>|  
|<span data-ttu-id="dea46-192">20051</span><span class="sxs-lookup"><span data-stu-id="dea46-192">20051</span></span>|<span data-ttu-id="dea46-193">同义词</span><span class="sxs-lookup"><span data-stu-id="dea46-193">Synonym</span></span>|  
|<span data-ttu-id="dea46-194">20307</span><span class="sxs-lookup"><span data-stu-id="dea46-194">20307</span></span>|<span data-ttu-id="dea46-195">序列</span><span class="sxs-lookup"><span data-stu-id="dea46-195">Sequence</span></span>|  
|<span data-ttu-id="dea46-196">20549</span><span class="sxs-lookup"><span data-stu-id="dea46-196">20549</span></span>|<span data-ttu-id="dea46-197">端点</span><span class="sxs-lookup"><span data-stu-id="dea46-197">End Point</span></span>|  
|<span data-ttu-id="dea46-198">20801</span><span class="sxs-lookup"><span data-stu-id="dea46-198">20801</span></span>|<span data-ttu-id="dea46-199">可能缓存的即席查询</span><span class="sxs-lookup"><span data-stu-id="dea46-199">Adhoc Queries which may be cached</span></span>|  
|<span data-ttu-id="dea46-200">20816</span><span class="sxs-lookup"><span data-stu-id="dea46-200">20816</span></span>|<span data-ttu-id="dea46-201">可能缓存的已准备查询</span><span class="sxs-lookup"><span data-stu-id="dea46-201">Prepared Queries which may be cached</span></span>|  
|<span data-ttu-id="dea46-202">20819</span><span class="sxs-lookup"><span data-stu-id="dea46-202">20819</span></span>|<span data-ttu-id="dea46-203">Service Broker 服务队列</span><span class="sxs-lookup"><span data-stu-id="dea46-203">Service Broker Service Queue</span></span>|  
|<span data-ttu-id="dea46-204">20821</span><span class="sxs-lookup"><span data-stu-id="dea46-204">20821</span></span>|<span data-ttu-id="dea46-205">唯一约束</span><span class="sxs-lookup"><span data-stu-id="dea46-205">Unique Constraint</span></span>|  
|<span data-ttu-id="dea46-206">21057</span><span class="sxs-lookup"><span data-stu-id="dea46-206">21057</span></span>|<span data-ttu-id="dea46-207">应用程序角色</span><span class="sxs-lookup"><span data-stu-id="dea46-207">Application Role</span></span>|  
|<span data-ttu-id="dea46-208">21059</span><span class="sxs-lookup"><span data-stu-id="dea46-208">21059</span></span>|<span data-ttu-id="dea46-209">证书</span><span class="sxs-lookup"><span data-stu-id="dea46-209">Certificate</span></span>|  
|<span data-ttu-id="dea46-210">21075</span><span class="sxs-lookup"><span data-stu-id="dea46-210">21075</span></span>|<span data-ttu-id="dea46-211">服务器</span><span class="sxs-lookup"><span data-stu-id="dea46-211">Server</span></span>|  
|<span data-ttu-id="dea46-212">21076</span><span class="sxs-lookup"><span data-stu-id="dea46-212">21076</span></span>|<span data-ttu-id="dea46-213">Transact-SQL 触发器</span><span class="sxs-lookup"><span data-stu-id="dea46-213">Transact-SQL Trigger</span></span>|  
|<span data-ttu-id="dea46-214">21313</span><span class="sxs-lookup"><span data-stu-id="dea46-214">21313</span></span>|<span data-ttu-id="dea46-215">Assembly</span><span class="sxs-lookup"><span data-stu-id="dea46-215">Assembly</span></span>|  
|<span data-ttu-id="dea46-216">21318</span><span class="sxs-lookup"><span data-stu-id="dea46-216">21318</span></span>|<span data-ttu-id="dea46-217">CLR 标量函数</span><span class="sxs-lookup"><span data-stu-id="dea46-217">CLR Scalar Function</span></span>|  
|<span data-ttu-id="dea46-218">21321</span><span class="sxs-lookup"><span data-stu-id="dea46-218">21321</span></span>|<span data-ttu-id="dea46-219">内联标量 SQL 函数</span><span class="sxs-lookup"><span data-stu-id="dea46-219">Inline scalar SQL Function</span></span>|  
|<span data-ttu-id="dea46-220">21328</span><span class="sxs-lookup"><span data-stu-id="dea46-220">21328</span></span>|<span data-ttu-id="dea46-221">分区方案</span><span class="sxs-lookup"><span data-stu-id="dea46-221">Partition Scheme</span></span>|  
|<span data-ttu-id="dea46-222">21333</span><span class="sxs-lookup"><span data-stu-id="dea46-222">21333</span></span>|<span data-ttu-id="dea46-223">用户</span><span class="sxs-lookup"><span data-stu-id="dea46-223">User</span></span>|  
|<span data-ttu-id="dea46-224">21571</span><span class="sxs-lookup"><span data-stu-id="dea46-224">21571</span></span>|<span data-ttu-id="dea46-225">Service Broker 服务约定</span><span class="sxs-lookup"><span data-stu-id="dea46-225">Service Broker Service Contract</span></span>|  
|<span data-ttu-id="dea46-226">21572</span><span class="sxs-lookup"><span data-stu-id="dea46-226">21572</span></span>|<span data-ttu-id="dea46-227">数据库上的触发器</span><span class="sxs-lookup"><span data-stu-id="dea46-227">Trigger on Database</span></span>|  
|<span data-ttu-id="dea46-228">21574</span><span class="sxs-lookup"><span data-stu-id="dea46-228">21574</span></span>|<span data-ttu-id="dea46-229">CLR 表值函数</span><span class="sxs-lookup"><span data-stu-id="dea46-229">CLR Table-valued Function</span></span>|  
|<span data-ttu-id="dea46-230">21577</span><span class="sxs-lookup"><span data-stu-id="dea46-230">21577</span></span>|<span data-ttu-id="dea46-231">内部表（例如，XML 节点表、队列表。）</span><span class="sxs-lookup"><span data-stu-id="dea46-231">Internal Table (For example, XML Node Table, Queue Table.)</span></span>|  
|<span data-ttu-id="dea46-232">21581</span><span class="sxs-lookup"><span data-stu-id="dea46-232">21581</span></span>|<span data-ttu-id="dea46-233">Service Broker 消息类型</span><span class="sxs-lookup"><span data-stu-id="dea46-233">Service Broker Message Type</span></span>|  
|<span data-ttu-id="dea46-234">21586</span><span class="sxs-lookup"><span data-stu-id="dea46-234">21586</span></span>|<span data-ttu-id="dea46-235">Service Broker 路由</span><span class="sxs-lookup"><span data-stu-id="dea46-235">Service Broker Route</span></span>|  
|<span data-ttu-id="dea46-236">21587</span><span class="sxs-lookup"><span data-stu-id="dea46-236">21587</span></span>|<span data-ttu-id="dea46-237">统计信息</span><span class="sxs-lookup"><span data-stu-id="dea46-237">Statistics</span></span>|  
|<span data-ttu-id="dea46-238">21825</span><span class="sxs-lookup"><span data-stu-id="dea46-238">21825</span></span><br /><br /> <span data-ttu-id="dea46-239">21827</span><span class="sxs-lookup"><span data-stu-id="dea46-239">21827</span></span><br /><br /> <span data-ttu-id="dea46-240">21831</span><span class="sxs-lookup"><span data-stu-id="dea46-240">21831</span></span><br /><br /> <span data-ttu-id="dea46-241">21843</span><span class="sxs-lookup"><span data-stu-id="dea46-241">21843</span></span><br /><br /> <span data-ttu-id="dea46-242">21847</span><span class="sxs-lookup"><span data-stu-id="dea46-242">21847</span></span>|<span data-ttu-id="dea46-243">用户</span><span class="sxs-lookup"><span data-stu-id="dea46-243">User</span></span>|  
|<span data-ttu-id="dea46-244">22099</span><span class="sxs-lookup"><span data-stu-id="dea46-244">22099</span></span>|<span data-ttu-id="dea46-245">Service Broker 服务</span><span class="sxs-lookup"><span data-stu-id="dea46-245">Service Broker Service</span></span>|  
|<span data-ttu-id="dea46-246">22601</span><span class="sxs-lookup"><span data-stu-id="dea46-246">22601</span></span>|<span data-ttu-id="dea46-247">索引</span><span class="sxs-lookup"><span data-stu-id="dea46-247">Index</span></span>|  
|<span data-ttu-id="dea46-248">22604</span><span class="sxs-lookup"><span data-stu-id="dea46-248">22604</span></span>|<span data-ttu-id="dea46-249">证书登录</span><span class="sxs-lookup"><span data-stu-id="dea46-249">Certificate Login</span></span>|  
|<span data-ttu-id="dea46-250">22611</span><span class="sxs-lookup"><span data-stu-id="dea46-250">22611</span></span>|<span data-ttu-id="dea46-251">XMLSchema</span><span class="sxs-lookup"><span data-stu-id="dea46-251">XMLSchema</span></span>|  
|<span data-ttu-id="dea46-252">22868</span><span class="sxs-lookup"><span data-stu-id="dea46-252">22868</span></span>|<span data-ttu-id="dea46-253">类型</span><span class="sxs-lookup"><span data-stu-id="dea46-253">Type</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dea46-254">另请参阅</span><span class="sxs-lookup"><span data-stu-id="dea46-254">See Also</span></span>  
 [<span data-ttu-id="dea46-255">sp_trace_setevent (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="dea46-255">sp_trace_setevent &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)  
  
  
