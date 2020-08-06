---
title: “更新统计信息”任务（维护计划）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.maint.statistics.f1
helpviewer_keywords:
- Updates Statistics Task dialog box
ms.assetid: 22902fd0-eb39-4f18-af94-3fcb69d2a3a4
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 486ef2da96785ed200900f497435117ef6437cb5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591333"
---
# <a name="update-statistics-task-maintenance-plan"></a><span data-ttu-id="c8e82-102">“更新统计信息”任务（维护计划）</span><span class="sxs-lookup"><span data-stu-id="c8e82-102">Update Statistics Task (Maintenance Plan)</span></span>
  <span data-ttu-id="c8e82-103">使用“更新统计信息任务”对话框可以更新与表和索引中的数据有关的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 信息。</span><span class="sxs-lookup"><span data-stu-id="c8e82-103">Use the **Update Statistics Task** dialog to update [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] information about the data in the tables and indexes.</span></span> <span data-ttu-id="c8e82-104">此任务实现对数据库中的用户表创建的每个索引的分发统计信息进行重新抽样。</span><span class="sxs-lookup"><span data-stu-id="c8e82-104">This task resamples the distribution statistics of each index created on user tables in the database.</span></span> <span data-ttu-id="c8e82-105">分发统计信息由 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用，以便在处理 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句期间优化在各表之间的导航。</span><span class="sxs-lookup"><span data-stu-id="c8e82-105">The distribution statistics are used by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to optimize navigation through tables during the processing of [!INCLUDE[tsql](../../includes/tsql-md.md)] statements.</span></span> <span data-ttu-id="c8e82-106">为了自动生成分布统计信息， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 定期从每个索引所对应的表中抽样数据。</span><span class="sxs-lookup"><span data-stu-id="c8e82-106">To build the distribution statistics automatically, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] periodically samples the data in the corresponding table for each index.</span></span> <span data-ttu-id="c8e82-107">此样本的大小取决于表中的行数和数据修改的频率。</span><span class="sxs-lookup"><span data-stu-id="c8e82-107">This size of the sample is based on the number of rows in the table and the frequency of data modification.</span></span> <span data-ttu-id="c8e82-108">使用此选项可以利用表中指定的数据百分比执行另一次抽样。</span><span class="sxs-lookup"><span data-stu-id="c8e82-108">Use this option to perform an additional sampling using the specified percentage of data in the tables.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="c8e82-109">使用此信息来创建更好的查询计划。</span><span class="sxs-lookup"><span data-stu-id="c8e82-109">uses this information to create better query plans.</span></span>  
  
 <span data-ttu-id="c8e82-110">此任务执行 UPDATE STATISTICS 语句。</span><span class="sxs-lookup"><span data-stu-id="c8e82-110">This task executes the UPDATE STATISTICS statement.</span></span>  
  
## <a name="options"></a><span data-ttu-id="c8e82-111">选项</span><span class="sxs-lookup"><span data-stu-id="c8e82-111">Options</span></span>  
 <span data-ttu-id="c8e82-112">**Connection**</span><span class="sxs-lookup"><span data-stu-id="c8e82-112">**Connection**</span></span>  
 <span data-ttu-id="c8e82-113">选择执行此任务时使用的服务器连接。</span><span class="sxs-lookup"><span data-stu-id="c8e82-113">Select the server connection to use when performing this task.</span></span>  
  
 <span data-ttu-id="c8e82-114">**新建**</span><span class="sxs-lookup"><span data-stu-id="c8e82-114">**New**</span></span>  
 <span data-ttu-id="c8e82-115">创建一个新的服务器连接，在执行此任务时使用。</span><span class="sxs-lookup"><span data-stu-id="c8e82-115">Create a new server connection to use when performing this task.</span></span> <span data-ttu-id="c8e82-116">下面对 **“新建连接”** 对话框进行了介绍。</span><span class="sxs-lookup"><span data-stu-id="c8e82-116">The **New Connection** dialog box is described below.</span></span>  
  
 <span data-ttu-id="c8e82-117">**数据库**</span><span class="sxs-lookup"><span data-stu-id="c8e82-117">**Databases**</span></span>  
 <span data-ttu-id="c8e82-118">指定受此任务影响的数据库。</span><span class="sxs-lookup"><span data-stu-id="c8e82-118">Specify the databases affected by this task.</span></span>  
  
-   <span data-ttu-id="c8e82-119">**“所有数据库”**</span><span class="sxs-lookup"><span data-stu-id="c8e82-119">**All databases**</span></span>  
  
     <span data-ttu-id="c8e82-120">生成的维护计划将对除 tempdb 之外的所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库运行维护任务。</span><span class="sxs-lookup"><span data-stu-id="c8e82-120">Generate a maintenance plan that runs maintenance tasks against all [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases, except tempdb.</span></span>  
  
-   <span data-ttu-id="c8e82-121">**所有系统数据库**</span><span class="sxs-lookup"><span data-stu-id="c8e82-121">**All system databases**</span></span>  
  
     <span data-ttu-id="c8e82-122">生成的维护计划将对除 tempdb 之外的所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 系统数据库运行维护任务。</span><span class="sxs-lookup"><span data-stu-id="c8e82-122">Generate a maintenance plan that runs maintenance tasks against each of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system databases except tempdb.</span></span> <span data-ttu-id="c8e82-123">对用户创建的数据库不运行维护任务。</span><span class="sxs-lookup"><span data-stu-id="c8e82-123">No maintenance tasks are run against user-created databases.</span></span>  
  
-   <span data-ttu-id="c8e82-124">**所有用户数据库**</span><span class="sxs-lookup"><span data-stu-id="c8e82-124">**All user databases**</span></span>  
  
     <span data-ttu-id="c8e82-125">生成的维护计划将对用户创建的所有数据库运行维护任务。</span><span class="sxs-lookup"><span data-stu-id="c8e82-125">Generate a maintenance plan that runs maintenance tasks against all user-created databases.</span></span> <span data-ttu-id="c8e82-126">但不会对 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 系统数据库运行任何维护任务。</span><span class="sxs-lookup"><span data-stu-id="c8e82-126">No maintenance tasks are run against the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system databases.</span></span>  
  
-   <span data-ttu-id="c8e82-127">**特定数据库**</span><span class="sxs-lookup"><span data-stu-id="c8e82-127">**These specific databases**</span></span>  
  
     <span data-ttu-id="c8e82-128">生成的维护计划将只对所选数据库运行维护任务。</span><span class="sxs-lookup"><span data-stu-id="c8e82-128">Generate a maintenance plan that runs maintenance tasks against only those databases that are selected.</span></span> <span data-ttu-id="c8e82-129">如果选择此选项，则必须至少在列表中选择一个数据库。</span><span class="sxs-lookup"><span data-stu-id="c8e82-129">At least one database in the list must be selected if this option is chosen.</span></span>  
  
 <span data-ttu-id="c8e82-130">**注意** 只能对兼容级别设置为 80 或更高的数据库运行维护计划。</span><span class="sxs-lookup"><span data-stu-id="c8e82-130">**Note** Maintenance plans only run against databases set to compatibility level 80 or higher.</span></span> <span data-ttu-id="c8e82-131">不显示兼容级别设置为 70 或更低的数据库。</span><span class="sxs-lookup"><span data-stu-id="c8e82-131">Databases set to compatibility level 70 or lower are not displayed.</span></span>  
  
 <span data-ttu-id="c8e82-132">**Object**</span><span class="sxs-lookup"><span data-stu-id="c8e82-132">**Object**</span></span>  
 <span data-ttu-id="c8e82-133">将“选择”网格限制为显示表、显示视图或同时显示两者。</span><span class="sxs-lookup"><span data-stu-id="c8e82-133">Limit the **Selection** grid to display tables, views, or both.</span></span>  
  
 <span data-ttu-id="c8e82-134">**选择**</span><span class="sxs-lookup"><span data-stu-id="c8e82-134">**Selection**</span></span>  
 <span data-ttu-id="c8e82-135">指定受此任务影响的表或索引。</span><span class="sxs-lookup"><span data-stu-id="c8e82-135">Specify the tables or indexes affected by this task.</span></span> <span data-ttu-id="c8e82-136">在“对象”框中选择 **“表和视图”** 时不可用。</span><span class="sxs-lookup"><span data-stu-id="c8e82-136">Not available when **Tables and Views** is selected in the Object box.</span></span>  
  
 <span data-ttu-id="c8e82-137">**所有现有统计信息**</span><span class="sxs-lookup"><span data-stu-id="c8e82-137">**All existing statistics**</span></span>  
 <span data-ttu-id="c8e82-138">同时更新列和索引的统计信息。</span><span class="sxs-lookup"><span data-stu-id="c8e82-138">Update statistics for both columns and indexes.</span></span>  
  
 <span data-ttu-id="c8e82-139">**仅限列统计信息**</span><span class="sxs-lookup"><span data-stu-id="c8e82-139">**Column statistics only**</span></span>  
 <span data-ttu-id="c8e82-140">仅更新列统计信息。</span><span class="sxs-lookup"><span data-stu-id="c8e82-140">Only update column statistics.</span></span>  
  
 <span data-ttu-id="c8e82-141">**仅限索引统计信息**</span><span class="sxs-lookup"><span data-stu-id="c8e82-141">**Index statistics only**</span></span>  
 <span data-ttu-id="c8e82-142">仅更新索引统计信息。</span><span class="sxs-lookup"><span data-stu-id="c8e82-142">Only update index statistics.</span></span>  
  
 <span data-ttu-id="c8e82-143">**扫描类型**</span><span class="sxs-lookup"><span data-stu-id="c8e82-143">**Scan type**</span></span>  
 <span data-ttu-id="c8e82-144">用于收集已更新统计信息的扫描的类型。</span><span class="sxs-lookup"><span data-stu-id="c8e82-144">Type of scan used to gather updated statistics.</span></span>  
  
 <span data-ttu-id="c8e82-145">**完全扫描**</span><span class="sxs-lookup"><span data-stu-id="c8e82-145">**Full scan**</span></span>  
 <span data-ttu-id="c8e82-146">读取表或视图中的所有行来收集统计信息。</span><span class="sxs-lookup"><span data-stu-id="c8e82-146">Read all rows in the table or view to gather the statistics.</span></span>  
  
 <span data-ttu-id="c8e82-147">**抽样依据**</span><span class="sxs-lookup"><span data-stu-id="c8e82-147">**Sample by**</span></span>  
 <span data-ttu-id="c8e82-148">指定在收集较大型的表或视图的统计信息时要抽样的表或索引视图的百分比或者行数。</span><span class="sxs-lookup"><span data-stu-id="c8e82-148">Specify the percentage of the table or indexed view, or the number of rows to sample when collecting statistics for larger tables or views.</span></span>  
  
 <span data-ttu-id="c8e82-149">**查看 T-SQL**</span><span class="sxs-lookup"><span data-stu-id="c8e82-149">**View T-SQL**</span></span>  
 <span data-ttu-id="c8e82-150">根据所选选项，查看针对此任务的服务器执行的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句。</span><span class="sxs-lookup"><span data-stu-id="c8e82-150">View the [!INCLUDE[tsql](../../includes/tsql-md.md)] statements performed against the server for this task, based on the selected options.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c8e82-151">当受影响的对象很多时，可能需要相当长的时间才可显示。</span><span class="sxs-lookup"><span data-stu-id="c8e82-151">When the number of objects affected is large, this display can take a considerable amount of time.</span></span>  
  
## <a name="new-connection-dialog-box"></a><span data-ttu-id="c8e82-152">“新建连接”对话框</span><span class="sxs-lookup"><span data-stu-id="c8e82-152">New Connection Dialog Box</span></span>  
 <span data-ttu-id="c8e82-153">**连接名称**</span><span class="sxs-lookup"><span data-stu-id="c8e82-153">**Connection name**</span></span>  
 <span data-ttu-id="c8e82-154">输入新连接的名称。</span><span class="sxs-lookup"><span data-stu-id="c8e82-154">Enter a name for the new connection.</span></span>  
  
 <span data-ttu-id="c8e82-155">**选择或输入服务器名称**</span><span class="sxs-lookup"><span data-stu-id="c8e82-155">**Select or enter a server name**</span></span>  
 <span data-ttu-id="c8e82-156">选择执行此任务时所要连接的服务器。</span><span class="sxs-lookup"><span data-stu-id="c8e82-156">Select a server to connect to when performing this task.</span></span>  
  
 <span data-ttu-id="c8e82-157">**“刷新”**</span><span class="sxs-lookup"><span data-stu-id="c8e82-157">**Refresh**</span></span>  
 <span data-ttu-id="c8e82-158">刷新可用服务器的列表。</span><span class="sxs-lookup"><span data-stu-id="c8e82-158">Refresh the list of available servers.</span></span>  
  
 <span data-ttu-id="c8e82-159">**输入登录服务器所需的信息**</span><span class="sxs-lookup"><span data-stu-id="c8e82-159">**Enter information to log on to the server**</span></span>  
 <span data-ttu-id="c8e82-160">指定如何对服务器进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="c8e82-160">Specify how to authenticate against the server.</span></span>  
  
 <span data-ttu-id="c8e82-161">**使用 Windows 集成安全性**</span><span class="sxs-lookup"><span data-stu-id="c8e82-161">**Use Windows integrated security**</span></span>  
 <span data-ttu-id="c8e82-162">使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 身份验证连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="c8e82-162">Connect to an instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] with [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Authentication.</span></span>  
  
 <span data-ttu-id="c8e82-163">**使用特定用户名和密码**</span><span class="sxs-lookup"><span data-stu-id="c8e82-163">**Use a specific user name and password**</span></span>  
 <span data-ttu-id="c8e82-164">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="c8e82-164">Connect to an instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="c8e82-165">此选项不可用。</span><span class="sxs-lookup"><span data-stu-id="c8e82-165">This option is not available.</span></span>  
  
 <span data-ttu-id="c8e82-166">**用户名**</span><span class="sxs-lookup"><span data-stu-id="c8e82-166">**User name**</span></span>  
 <span data-ttu-id="c8e82-167">提供一个在进行身份验证时要使用的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名。</span><span class="sxs-lookup"><span data-stu-id="c8e82-167">Provide a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login to use when authenticating.</span></span> <span data-ttu-id="c8e82-168">此选项不可用。</span><span class="sxs-lookup"><span data-stu-id="c8e82-168">This option is not available.</span></span>  
  
 <span data-ttu-id="c8e82-169">**密码**</span><span class="sxs-lookup"><span data-stu-id="c8e82-169">**Password**</span></span>  
 <span data-ttu-id="c8e82-170">提供一个在进行身份验证时要使用的密码。</span><span class="sxs-lookup"><span data-stu-id="c8e82-170">Provide a password to use when authenticating.</span></span> <span data-ttu-id="c8e82-171">此选项不可用。</span><span class="sxs-lookup"><span data-stu-id="c8e82-171">This option is not available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8e82-172">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c8e82-172">See Also</span></span>  
 [<span data-ttu-id="c8e82-173">更新统计信息 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="c8e82-173">UPDATE STATISTICS &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/update-statistics-transact-sql)  
  
  
