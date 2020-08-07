---
title: MSSQLSERVER_605 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 605 (Database Engine error)
ms.assetid: d8d3a22e-1ff8-48a4-891f-4c8619437e24
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e196fba84af492b25e798629d3e808b1bf22857e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589581"
---
# <a name="mssqlserver_605"></a><span data-ttu-id="d1a00-102">MSSQLSERVER_605</span><span class="sxs-lookup"><span data-stu-id="d1a00-102">MSSQLSERVER_605</span></span>
    
## <a name="details"></a><span data-ttu-id="d1a00-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="d1a00-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d1a00-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="d1a00-104">Product Name</span></span>|<span data-ttu-id="d1a00-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="d1a00-105">SQL Server</span></span>|  
|<span data-ttu-id="d1a00-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="d1a00-106">Event ID</span></span>|<span data-ttu-id="d1a00-107">605</span><span class="sxs-lookup"><span data-stu-id="d1a00-107">605</span></span>|  
|<span data-ttu-id="d1a00-108">事件源</span><span class="sxs-lookup"><span data-stu-id="d1a00-108">Event Source</span></span>|<span data-ttu-id="d1a00-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="d1a00-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="d1a00-110">组件</span><span class="sxs-lookup"><span data-stu-id="d1a00-110">Component</span></span>|<span data-ttu-id="d1a00-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="d1a00-111">SQLEngine</span></span>|  
|<span data-ttu-id="d1a00-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="d1a00-112">Symbolic Name</span></span>|<span data-ttu-id="d1a00-113">WRONGPAGE</span><span class="sxs-lookup"><span data-stu-id="d1a00-113">WRONGPAGE</span></span>|  
|<span data-ttu-id="d1a00-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="d1a00-114">Message Text</span></span>|<span data-ttu-id="d1a00-115">尝试在数据库 %d 中提取逻辑页 %S_PGID 失败。</span><span class="sxs-lookup"><span data-stu-id="d1a00-115">Attempt to fetch logical page %S_PGID in database %d failed.</span></span> <span data-ttu-id="d1a00-116">该逻辑页属于分配单元 %I64d，而非 %I64d。</span><span class="sxs-lookup"><span data-stu-id="d1a00-116">It belongs to allocation unit %I64d not to %I64d.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="d1a00-117">说明</span><span class="sxs-lookup"><span data-stu-id="d1a00-117">Explanation</span></span>  
 <span data-ttu-id="d1a00-118">此错误通常表示指定数据库中的页或分配已损坏。</span><span class="sxs-lookup"><span data-stu-id="d1a00-118">This error generally signifies page or allocation corruption in the specified database.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="d1a00-119">会在根据页链接或使用索引分配映射 (IAM) 读取属于表的页时，检测到此损坏。</span><span class="sxs-lookup"><span data-stu-id="d1a00-119">detects corruption when reading pages belonging to a table either by following the page linkages or by using the Index Allocation Map (IAM).</span></span> <span data-ttu-id="d1a00-120">分配给表的所有页必须属于与该表相关联的分配单元之一。</span><span class="sxs-lookup"><span data-stu-id="d1a00-120">All pages allocated to a table must belong to one of the allocation units associated with the table.</span></span> <span data-ttu-id="d1a00-121">如果页眉中包含的分配单元 ID 不匹配与表相关联的分配单元 ID，将引发此异常。</span><span class="sxs-lookup"><span data-stu-id="d1a00-121">If the allocation unit ID contained in the page header does not match an allocation unit ID associated with the table, this exception is raised.</span></span> <span data-ttu-id="d1a00-122">错误消息中列出的第一个分配单元 ID 是页眉中显示的 ID，而第二个分配单元值则是与表相关联的 ID。</span><span class="sxs-lookup"><span data-stu-id="d1a00-122">The first allocation unit ID listed in the error message is the ID present in the page header, and the second allocation unit value is the ID associated with the table.</span></span>  
  
 <span data-ttu-id="d1a00-123">**数据损坏错误**</span><span class="sxs-lookup"><span data-stu-id="d1a00-123">**Data Corruption Errors**</span></span>  
  
 <span data-ttu-id="d1a00-124">严重级别为 21 表示可能存在数据损坏。</span><span class="sxs-lookup"><span data-stu-id="d1a00-124">A severity level of 21 indicates potential data corruption.</span></span> <span data-ttu-id="d1a00-125">可能的原因包括损坏的页链、损坏的 IAM 或该对象的 [sys.objects](/sql/relational-databases/system-catalog-views/sys-objects-transact-sql) 目录视图中存在无效条目。</span><span class="sxs-lookup"><span data-stu-id="d1a00-125">Possible causes are a damaged page chain, a corrupt IAM, or an invalid entry in the [sys.objects](/sql/relational-databases/system-catalog-views/sys-objects-transact-sql) catalog view for that object.</span></span> <span data-ttu-id="d1a00-126">这些错误通常由硬件或磁盘设备驱动程序故障而引起。</span><span class="sxs-lookup"><span data-stu-id="d1a00-126">These errors are often caused by hardware or disk device driver failure.</span></span>  
  
 <span data-ttu-id="d1a00-127">**暂时性错误**</span><span class="sxs-lookup"><span data-stu-id="d1a00-127">**Transient Errors**</span></span>  
  
 <span data-ttu-id="d1a00-128">严重级别为 12 表示可能存在暂时性错误，即在缓存中出现错误，但不表示对磁盘上的数据造成破坏。</span><span class="sxs-lookup"><span data-stu-id="d1a00-128">A severity level of 12 indicates a potential transient error; that is, it occurs in the cache and does not indicate damage to data on disk.</span></span> <span data-ttu-id="d1a00-129">暂时性的 605 错误可由以下条件引发：</span><span class="sxs-lookup"><span data-stu-id="d1a00-129">Transient 605 errors can be caused by the following conditions:</span></span>  
  
-   <span data-ttu-id="d1a00-130">操作系统过早地通知 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 已完成某个 I/O 操作；尽管不存在实际的数据损坏，但显示错误消息。</span><span class="sxs-lookup"><span data-stu-id="d1a00-130">The operating system prematurely notifies [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that an I/O operation has completed; the error message is displayed even though no actual data corruption exists.</span></span>  
  
 <span data-ttu-id="d1a00-131">运行带有优化器提示 NOLOCK 的查询，或将事务隔离级别设置为 READ UNCOMMITTED。</span><span class="sxs-lookup"><span data-stu-id="d1a00-131">Running a query with the Optimizer hint NOLOCK or setting the transaction isolation level to READ UNCOMMITTED.</span></span> <span data-ttu-id="d1a00-132">当使用 NOLOCK 或 READ UNCOMMITTED 的查询尝试读取被其他用户移走或更改的数据时，将发生 605 错误。</span><span class="sxs-lookup"><span data-stu-id="d1a00-132">When a query that is using NOLOCK or READ UNCOMMITTED tries to read data that is being moved or changed by another user, a 605 error occurs.</span></span> <span data-ttu-id="d1a00-133">若要验证是否为暂时性的 605 错误，请稍后重新运行该查询。</span><span class="sxs-lookup"><span data-stu-id="d1a00-133">To verify that it is a transient 605 error, rerun the query later.</span></span> <span data-ttu-id="d1a00-134">有关详细信息，请参阅此知识库文章 [235880](https://support.microsoft.com/kb/235880/en-us)：“You receive an "Error 605" error message when you run a query with the optimizer hint NOLOCK or you set the transaction isolation level to READ UNCOMMITTED in SQL Server.”（当用优化程序提示 NOLOCK 运行查询或者在 SQL Server 中将事务隔离级别设为 READ UNCOMMITTED 时，将收到“错误 605”错误消息）。</span><span class="sxs-lookup"><span data-stu-id="d1a00-134">For more information, see this KB article [235880](https://support.microsoft.com/kb/235880/en-us): "You receive an "Error 605" error message when you run a query with the optimizer hint NOLOCK or you set the transaction isolation level to READ UNCOMMITTED in SQL Server."</span></span>  
  
 <span data-ttu-id="d1a00-135">通常，如果在数据访问期间发生该错误，但后续的 DBCC CHECKDB 操作在没有出错的情况下完成，则 605 错误可能是暂时的。</span><span class="sxs-lookup"><span data-stu-id="d1a00-135">In general, if the error occurs during data access but subsequent DBCC CHECKDB operations complete without error, the 605 error was probably transient.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="d1a00-136">用户操作</span><span class="sxs-lookup"><span data-stu-id="d1a00-136">User Action</span></span>  
 <span data-ttu-id="d1a00-137">如果 605 错误不是暂时性的，则说明问题很严重，必须运行以下任务来纠正该问题：</span><span class="sxs-lookup"><span data-stu-id="d1a00-137">If the 605 error is not transient, the problem is severe and must be corrected by performing the following tasks:</span></span>  
  
1.  <span data-ttu-id="d1a00-138">运行以下查询，确定与消息中指定的分配单元相关联的表。</span><span class="sxs-lookup"><span data-stu-id="d1a00-138">Identify the tables associated with the allocation units specified in the message by running the following query.</span></span> <span data-ttu-id="d1a00-139">用错误消息中说明的分配单元替换 `allocation_unit_id`。</span><span class="sxs-lookup"><span data-stu-id="d1a00-139">Replace `allocation_unit_id` with the allocation units specified in the error message.</span></span>  
  
     <span data-ttu-id="d1a00-140">USE`database_name`;</span><span class="sxs-lookup"><span data-stu-id="d1a00-140">USE`database_name`;</span></span>  
  
     <span data-ttu-id="d1a00-141">GO</span><span class="sxs-lookup"><span data-stu-id="d1a00-141">GO</span></span>  
  
     <span data-ttu-id="d1a00-142">SELECT au.allocation_unit_id, OBJECT_NAME(p.object_id) AS table_name, fg.name AS filegroup_name,</span><span class="sxs-lookup"><span data-stu-id="d1a00-142">SELECT au.allocation_unit_id, OBJECT_NAME(p.object_id) AS table_name, fg.name AS filegroup_name,</span></span>  
  
     <span data-ttu-id="d1a00-143">au.type_desc AS allocation_type, au.data_pages, partition_number</span><span class="sxs-lookup"><span data-stu-id="d1a00-143">au.type_desc AS allocation_type, au.data_pages, partition_number</span></span>  
  
     <span data-ttu-id="d1a00-144">FROM sys.allocation_units AS au</span><span class="sxs-lookup"><span data-stu-id="d1a00-144">FROM sys.allocation_units AS au</span></span>  
  
     <span data-ttu-id="d1a00-145">JOIN sys.partitions AS p ON au.container_id = p.partition_id</span><span class="sxs-lookup"><span data-stu-id="d1a00-145">JOIN sys.partitions AS p ON au.container_id = p.partition_id</span></span>  
  
     <span data-ttu-id="d1a00-146">JOIN sys.filegroups AS fg ON fg.data_space_id = au.data_space_id</span><span class="sxs-lookup"><span data-stu-id="d1a00-146">JOIN sys.filegroups AS fg ON fg.data_space_id = au.data_space_id</span></span>  
  
     <span data-ttu-id="d1a00-147">WHERE au.allocation_unit_id = `allocation_unit_id` OR au.allocation_unit_id = `allocation_unit_id`</span><span class="sxs-lookup"><span data-stu-id="d1a00-147">WHERE au.allocation_unit_id = `allocation_unit_id` OR au.allocation_unit_id = `allocation_unit_id`</span></span>  
  
     <span data-ttu-id="d1a00-148">ORDER BY au.allocation_unit_id;</span><span class="sxs-lookup"><span data-stu-id="d1a00-148">ORDER BY au.allocation_unit_id;</span></span>  
  
     <span data-ttu-id="d1a00-149">GO</span><span class="sxs-lookup"><span data-stu-id="d1a00-149">GO</span></span>  
  
2.  <span data-ttu-id="d1a00-150">对与错误消息中说明的第二个分配单元 ID 相关联的表，执行不带 REPAIR 子句的 DBCC CHECKTABLE。</span><span class="sxs-lookup"><span data-stu-id="d1a00-150">Execute DBCC CHECKTABLE without a REPAIR clause on the table associated with the second allocation unit ID specified in the error message.</span></span>  
  
3.  <span data-ttu-id="d1a00-151">尽快执行不带 REPAIR 子句的 DBCC CHECKDB，以确定整个数据库中的总体损坏程度。</span><span class="sxs-lookup"><span data-stu-id="d1a00-151">Execute DBCC CHECKDB without a REPAIR clause as soon as possible to determine the full extent of the corruption in the entire database.</span></span>  
  
4.  <span data-ttu-id="d1a00-152">检查错误日志以查找经常随 605 错误一起发生的其他错误，并检查 Windows 事件日志以查找任何与系统或硬件有关的问题。</span><span class="sxs-lookup"><span data-stu-id="d1a00-152">Check the error log for other errors that often accompany a 605 error and examine the Windows Event Log for any system or hardware related issues.</span></span> <span data-ttu-id="d1a00-153">修复日志中包含的所有与硬件相关的问题。</span><span class="sxs-lookup"><span data-stu-id="d1a00-153">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="d1a00-154">如果问题与硬件无关，请执行以下任务之一：</span><span class="sxs-lookup"><span data-stu-id="d1a00-154">If the problem is not hardware related, perform one of the following tasks:</span></span>  
  
1.  <span data-ttu-id="d1a00-155">从已知的干净备份中还原数据库。</span><span class="sxs-lookup"><span data-stu-id="d1a00-155">Restore the database from a known clean backup.</span></span> <span data-ttu-id="d1a00-156">可以利用页面还原备份功能来还原损坏的页。</span><span class="sxs-lookup"><span data-stu-id="d1a00-156">You can leverage the page restore backup feature to restore just the damaged pages.</span></span>  
  
2.  <span data-ttu-id="d1a00-157">运行带有 REPAIR 子句的 DBCC CHECKDB（这是步骤 3 中所执行 DBCC CHECKDB 操作推荐的做法），以修复损坏。</span><span class="sxs-lookup"><span data-stu-id="d1a00-157">Run DBCC CHECKDB with the REPAIR clause recommended by the DBCC CHECKDB operation performed in step 3 to repair the corruption.</span></span> <span data-ttu-id="d1a00-158">如果运行具有 REPAIR 子句的 DBCC CHECKDB 无法解决存在的问题，请与主要支持提供商联系。</span><span class="sxs-lookup"><span data-stu-id="d1a00-158">If running DBCC CHECKDB with one of the REPAIR clauses does not correct the problem, contact your primary support provider.</span></span> <span data-ttu-id="d1a00-159">提供 DBCC CHECKDB 的输出以供查看。</span><span class="sxs-lookup"><span data-stu-id="d1a00-159">Have the output from DBCC CHECKDB available for review.</span></span>  
  
    > [!CAUTION]  
    >  <span data-ttu-id="d1a00-160">如果您不确定运行带有 REPAIR 子句的 DBCC CHECKDB 会对数据造成何种影响，请在运行该语句前与您的主要支持提供商联系。</span><span class="sxs-lookup"><span data-stu-id="d1a00-160">If you are not sure what effect DBCC CHECKDB with a REPAIR clause has on your data, contact your primary support provider before running this statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1a00-161">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d1a00-161">See Also</span></span>  
 [<span data-ttu-id="d1a00-162">DBCC CHECKTABLE (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="d1a00-162">DBCC CHECKTABLE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/database-console-commands/dbcc-checktable-transact-sql)  
  
  
