---
title: “重新生成索引”任务（维护计划）| Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.maint.reindex.f1
- reindex
helpviewer_keywords:
- Rebuild Index Task dialog box
ms.assetid: 33e2940b-139f-4563-b0cb-5683f08bd879
author: rothja
ms.author: jroth
ms.openlocfilehash: bc9d7c85a72c34cee1ef7af8cb4b4f25f918a3fd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580712"
---
# <a name="rebuild-index-task-maintenance-plan"></a><span data-ttu-id="15f96-102">“重新生成索引”任务（维护计划）</span><span class="sxs-lookup"><span data-stu-id="15f96-102">Rebuild Index Task (Maintenance Plan)</span></span>
  <span data-ttu-id="15f96-103">使用“重新生成索引任务”对话框可用利用新的填充因子对数据库中的表重新创建索引。</span><span class="sxs-lookup"><span data-stu-id="15f96-103">Use the **Rebuild Index Task** dialog to re-create the indexes on the tables in the database with a new fill factor.</span></span> <span data-ttu-id="15f96-104">填充因子确定索引中每页上的空白空间量，以容纳将来的扩展内容。</span><span class="sxs-lookup"><span data-stu-id="15f96-104">The fill factor determines the amount of empty space on each page in the index, to accommodate future expansion.</span></span> <span data-ttu-id="15f96-105">随着向表中添加数据，由于没有维持填充因子，可用空间将逐渐填满。</span><span class="sxs-lookup"><span data-stu-id="15f96-105">As data is added to the table, the free space fills because the fill factor is not maintained.</span></span> <span data-ttu-id="15f96-106">重新组织数据页和索引页可以重新建立可用空间。</span><span class="sxs-lookup"><span data-stu-id="15f96-106">Reorganizing data and index pages can re-establish the free space.</span></span>  
  
 <span data-ttu-id="15f96-107">**“‘重新生成索引’任务”** 使用 ALTER INDEX 语句。</span><span class="sxs-lookup"><span data-stu-id="15f96-107">The **Rebuild Index Task** uses the ALTER INDEX statement.</span></span>  
  
## <a name="options"></a><span data-ttu-id="15f96-108">选项</span><span class="sxs-lookup"><span data-stu-id="15f96-108">Options</span></span>  
 <span data-ttu-id="15f96-109">**Connection**</span><span class="sxs-lookup"><span data-stu-id="15f96-109">**Connection**</span></span>  
 <span data-ttu-id="15f96-110">选择执行此任务时使用的服务器连接。</span><span class="sxs-lookup"><span data-stu-id="15f96-110">Select the server connection to use when performing this task.</span></span>  
  
 <span data-ttu-id="15f96-111">**新建**</span><span class="sxs-lookup"><span data-stu-id="15f96-111">**New**</span></span>  
 <span data-ttu-id="15f96-112">创建一个新的服务器连接，在执行此任务时使用。</span><span class="sxs-lookup"><span data-stu-id="15f96-112">Create a new server connection to use when performing this task.</span></span> <span data-ttu-id="15f96-113">下面对 **“新建连接”** 对话框进行了介绍。</span><span class="sxs-lookup"><span data-stu-id="15f96-113">The **New Connection** dialog box is described below.</span></span>  
  
 <span data-ttu-id="15f96-114">**数据库**</span><span class="sxs-lookup"><span data-stu-id="15f96-114">**Databases**</span></span>  
 <span data-ttu-id="15f96-115">指定受此任务影响的数据库。</span><span class="sxs-lookup"><span data-stu-id="15f96-115">Specify the databases affected by this task.</span></span>  
  
-   <span data-ttu-id="15f96-116">**“所有数据库”**</span><span class="sxs-lookup"><span data-stu-id="15f96-116">**All databases**</span></span>  
  
     <span data-ttu-id="15f96-117">生成的维护计划将对除 tempdb 之外的所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库运行维护任务。</span><span class="sxs-lookup"><span data-stu-id="15f96-117">Generate a maintenance plan that runs maintenance tasks against all [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases except tempdb.</span></span>  
  
-   <span data-ttu-id="15f96-118">**所有系统数据库**</span><span class="sxs-lookup"><span data-stu-id="15f96-118">**All system databases**</span></span>  
  
     <span data-ttu-id="15f96-119">生成的维护计划将对除 tempdb 之外的所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 系统数据库运行维护任务。</span><span class="sxs-lookup"><span data-stu-id="15f96-119">Generate a maintenance plan that runs maintenance tasks against each of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system databases except tempdb.</span></span> <span data-ttu-id="15f96-120">对用户创建的数据库不运行维护任务。</span><span class="sxs-lookup"><span data-stu-id="15f96-120">No maintenance tasks are run against user-created databases.</span></span>  
  
-   <span data-ttu-id="15f96-121">**所有用户数据库**</span><span class="sxs-lookup"><span data-stu-id="15f96-121">**All user databases**</span></span>  
  
     <span data-ttu-id="15f96-122">生成的维护计划将对用户创建的所有数据库运行维护任务。</span><span class="sxs-lookup"><span data-stu-id="15f96-122">Generate a maintenance plan that runs maintenance tasks against all user-created databases.</span></span> <span data-ttu-id="15f96-123">但不会对 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 系统数据库运行任何维护任务。</span><span class="sxs-lookup"><span data-stu-id="15f96-123">No maintenance tasks are run against the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system databases.</span></span>  
  
-   <span data-ttu-id="15f96-124">**特定数据库**</span><span class="sxs-lookup"><span data-stu-id="15f96-124">**These specific databases**</span></span>  
  
     <span data-ttu-id="15f96-125">生成的维护计划将只对所选数据库运行维护任务。</span><span class="sxs-lookup"><span data-stu-id="15f96-125">Generate a maintenance plan that runs maintenance tasks against only those databases that are selected.</span></span> <span data-ttu-id="15f96-126">如果选择此选项，则必须至少在列表中选择一个数据库。</span><span class="sxs-lookup"><span data-stu-id="15f96-126">At least one database in the list must be selected if this option is chosen.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="15f96-127">只能对兼容级别被设置为 80 或更高的数据库运行维护计划。</span><span class="sxs-lookup"><span data-stu-id="15f96-127">Maintenance plans only run against databases set to compatibility level 80 or higher.</span></span> <span data-ttu-id="15f96-128">不显示兼容级别设置为 70 或更低的数据库。</span><span class="sxs-lookup"><span data-stu-id="15f96-128">Databases set to compatibility level 70 or lower are not displayed.</span></span>  
  
 <span data-ttu-id="15f96-129">**Object**</span><span class="sxs-lookup"><span data-stu-id="15f96-129">**Object**</span></span>  
 <span data-ttu-id="15f96-130">将“选择”网格限制为显示表、显示视图或同时显示两者。</span><span class="sxs-lookup"><span data-stu-id="15f96-130">Limit the **Selection** grid to display tables, views, or both.</span></span>  
  
 <span data-ttu-id="15f96-131">**选择**</span><span class="sxs-lookup"><span data-stu-id="15f96-131">**Selection**</span></span>  
 <span data-ttu-id="15f96-132">指定受此任务影响的表或索引。</span><span class="sxs-lookup"><span data-stu-id="15f96-132">Specify the tables or indexes affected by this task.</span></span> <span data-ttu-id="15f96-133">在“对象”框中选择 **“表和视图”** 时不可用。</span><span class="sxs-lookup"><span data-stu-id="15f96-133">Not available when **Tables and Views** is selected in the Object box.</span></span>  
  
 <span data-ttu-id="15f96-134">**使用默认可用空间重新组织页**</span><span class="sxs-lookup"><span data-stu-id="15f96-134">**Reorganize pages with the default amount of free space**</span></span>  
 <span data-ttu-id="15f96-135">删除数据库中表上的索引，并使用在创建索引时指定的填充因子重新创建索引。</span><span class="sxs-lookup"><span data-stu-id="15f96-135">Drop the indexes on the tables in the database and re-create them with the fill factor that was specified when the indexes were created.</span></span>  
  
 <span data-ttu-id="15f96-136">**将每页的可用空间百分比更改为**</span><span class="sxs-lookup"><span data-stu-id="15f96-136">**Change free space per page percentage to**</span></span>  
 <span data-ttu-id="15f96-137">删除数据库中表上的索引，并使用新的、自动计算的填充因子重新创建索引，从而在索引页上保留指定的可用空间。</span><span class="sxs-lookup"><span data-stu-id="15f96-137">Drop the indexes on the tables in the database and re-create them with a new, automatically calculated fill factor, thereby reserving the specified amount of free space on the index pages.</span></span> <span data-ttu-id="15f96-138">百分比越高，索引页上保留的可用空间就越多，并且索引增长也就越大。</span><span class="sxs-lookup"><span data-stu-id="15f96-138">The higher the percentage, the more free space is reserved on the index pages, and the larger the index grows.</span></span> <span data-ttu-id="15f96-139">有效值为 0 到 100。</span><span class="sxs-lookup"><span data-stu-id="15f96-139">Valid values are from 0 through 100.</span></span>  
  
 <span data-ttu-id="15f96-140">**对 tempdb 中的结果进行排序**</span><span class="sxs-lookup"><span data-stu-id="15f96-140">**Sort results in tempdb**</span></span>  
 <span data-ttu-id="15f96-141">使用 `SORT_IN_TEMPDB` 选项，该选项确定在索引创建过程中生成的中间排序结果的临时存储位置。</span><span class="sxs-lookup"><span data-stu-id="15f96-141">Use the `SORT_IN_TEMPDB`option, which determines where the intermediate sort results, generated during index creation, are temporarily stored.</span></span> <span data-ttu-id="15f96-142">如果不需要执行排序操作，或者可以在内存中执行排序，则系统会忽略 `SORT_IN_TEMPDB`选项。</span><span class="sxs-lookup"><span data-stu-id="15f96-142">If a sort operation is not required, or if the sort can be performed in memory, the `SORT_IN_TEMPDB`option is ignored.</span></span>  
  
 <span data-ttu-id="15f96-143">**重建索引时保持索引联机**</span><span class="sxs-lookup"><span data-stu-id="15f96-143">**Keep index online while reindexing**</span></span>  
 <span data-ttu-id="15f96-144">使用 `ONLINE` 选项，用户可以在索引操作期间访问基础表或聚集索引数据以及任何关联的非聚集索引。</span><span class="sxs-lookup"><span data-stu-id="15f96-144">Use the `ONLINE` option which allows users to access the underlying table or clustered index data and any associated nonclustered indexes during index operations.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="15f96-145">在 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的各版本中均不提供联机索引操作。</span><span class="sxs-lookup"><span data-stu-id="15f96-145">Online index operations are not available in every edition of [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="15f96-146">有关各个版本支持的功能列表 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，请参阅 SQL Server 2014 的各个[版本支持的功能](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)。</span><span class="sxs-lookup"><span data-stu-id="15f96-146">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
 <span data-ttu-id="15f96-147">**查看 T-SQL**</span><span class="sxs-lookup"><span data-stu-id="15f96-147">**View T-SQL**</span></span>  
 <span data-ttu-id="15f96-148">根据所选选项，查看针对此任务的服务器执行的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句。</span><span class="sxs-lookup"><span data-stu-id="15f96-148">View the [!INCLUDE[tsql](../../includes/tsql-md.md)] statements performed against the server for this task, based on the selected options.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="15f96-149">当受影响的对象很多时，可能需要相当长的时间才可显示。</span><span class="sxs-lookup"><span data-stu-id="15f96-149">When the number of objects affected is large, this display can take a considerable amount of time.</span></span>  
  
## <a name="new-connection-dialog-box"></a><span data-ttu-id="15f96-150">“新建连接”对话框</span><span class="sxs-lookup"><span data-stu-id="15f96-150">New Connection Dialog Box</span></span>  
 <span data-ttu-id="15f96-151">**连接名称**</span><span class="sxs-lookup"><span data-stu-id="15f96-151">**Connection name**</span></span>  
 <span data-ttu-id="15f96-152">输入新连接的名称。</span><span class="sxs-lookup"><span data-stu-id="15f96-152">Enter a name for the new connection.</span></span>  
  
 <span data-ttu-id="15f96-153">**选择或输入服务器名称**</span><span class="sxs-lookup"><span data-stu-id="15f96-153">**Select or enter a server name**</span></span>  
 <span data-ttu-id="15f96-154">选择执行此任务时所要连接的服务器。</span><span class="sxs-lookup"><span data-stu-id="15f96-154">Select a server to connect to when performing this task.</span></span>  
  
 <span data-ttu-id="15f96-155">**“刷新”**</span><span class="sxs-lookup"><span data-stu-id="15f96-155">**Refresh**</span></span>  
 <span data-ttu-id="15f96-156">刷新可用服务器的列表。</span><span class="sxs-lookup"><span data-stu-id="15f96-156">Refresh the list of available servers.</span></span>  
  
 <span data-ttu-id="15f96-157">**输入登录服务器所需的信息**</span><span class="sxs-lookup"><span data-stu-id="15f96-157">**Enter information to log on to the server**</span></span>  
 <span data-ttu-id="15f96-158">指定如何对服务器进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="15f96-158">Specify how to authenticate against the server.</span></span>  
  
 <span data-ttu-id="15f96-159">**使用 Windows 集成安全性**</span><span class="sxs-lookup"><span data-stu-id="15f96-159">**Use Windows integrated security**</span></span>  
 <span data-ttu-id="15f96-160">使用 Windows 身份验证连接到 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 的实例。</span><span class="sxs-lookup"><span data-stu-id="15f96-160">Connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] with Windows Authentication.</span></span>  
  
 <span data-ttu-id="15f96-161">**使用特定用户名和密码**</span><span class="sxs-lookup"><span data-stu-id="15f96-161">**Use a specific user name and password**</span></span>  
 <span data-ttu-id="15f96-162">使用 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 身份验证连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的实例。</span><span class="sxs-lookup"><span data-stu-id="15f96-162">Connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="15f96-163">此选项不可用。</span><span class="sxs-lookup"><span data-stu-id="15f96-163">This option is not available.</span></span>  
  
 <span data-ttu-id="15f96-164">**用户名**</span><span class="sxs-lookup"><span data-stu-id="15f96-164">**User name**</span></span>  
 <span data-ttu-id="15f96-165">提供一个在进行身份验证时要使用的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名。</span><span class="sxs-lookup"><span data-stu-id="15f96-165">Provide a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login to use when authenticating.</span></span> <span data-ttu-id="15f96-166">此选项不可用。</span><span class="sxs-lookup"><span data-stu-id="15f96-166">This option is not available.</span></span>  
  
 <span data-ttu-id="15f96-167">**密码**</span><span class="sxs-lookup"><span data-stu-id="15f96-167">**Password**</span></span>  
 <span data-ttu-id="15f96-168">提供一个在进行身份验证时要使用的密码。</span><span class="sxs-lookup"><span data-stu-id="15f96-168">Provide a password to use when authenticating.</span></span> <span data-ttu-id="15f96-169">此选项不可用。</span><span class="sxs-lookup"><span data-stu-id="15f96-169">This option is not available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15f96-170">另请参阅</span><span class="sxs-lookup"><span data-stu-id="15f96-170">See Also</span></span>  
 <span data-ttu-id="15f96-171">[ALTER INDEX (Transact-SQL)](/sql/t-sql/statements/alter-index-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="15f96-171">[ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql) </span></span>  
 <span data-ttu-id="15f96-172">[DBCC DBREINDEX (Transact-SQL)](/sql/t-sql/database-console-commands/dbcc-dbreindex-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="15f96-172">[DBCC DBREINDEX &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-dbreindex-transact-sql) </span></span>  
 <span data-ttu-id="15f96-173">[CREATE INDEX (Transact-SQL)](/sql/t-sql/statements/create-index-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="15f96-173">[CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql) </span></span>  
 <span data-ttu-id="15f96-174">[用于索引的 SORT_IN_TEMPDB 选项](../indexes/indexes.md) </span><span class="sxs-lookup"><span data-stu-id="15f96-174">[SORT_IN_TEMPDB Option For Indexes](../indexes/indexes.md) </span></span>  
 <span data-ttu-id="15f96-175">[联机索引操作准则](../indexes/guidelines-for-online-index-operations.md) </span><span class="sxs-lookup"><span data-stu-id="15f96-175">[Guidelines for Online Index Operations](../indexes/guidelines-for-online-index-operations.md) </span></span>  
 <span data-ttu-id="15f96-176">[联机索引操作的工作方式](../indexes/how-online-index-operations-work.md) </span><span class="sxs-lookup"><span data-stu-id="15f96-176">[How Online Index Operations Work](../indexes/how-online-index-operations-work.md) </span></span>  
 [<span data-ttu-id="15f96-177">联机执行索引操作</span><span class="sxs-lookup"><span data-stu-id="15f96-177">Perform Index Operations Online</span></span>](../indexes/perform-index-operations-online.md)  
  
  
