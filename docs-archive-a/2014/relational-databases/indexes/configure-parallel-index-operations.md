---
title: 配置并行索引操作 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- index parallel operations [SQL Server]
- processors [SQL Server], parallel index operations
- max degree of parallelism option
- MAXDOP index option, parallel index operations
- parallel index operations [SQL Server]
ms.assetid: 8ec8c71e-5fc1-443a-92da-136ee3fc7f88
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8831aadae15af03a05f4ab03cfe514e54566df1f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577633"
---
# <a name="configure-parallel-index-operations"></a><span data-ttu-id="6ad75-102">配置并行索引操作</span><span class="sxs-lookup"><span data-stu-id="6ad75-102">Configure Parallel Index Operations</span></span>
  <span data-ttu-id="6ad75-103">本主题通过使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中定义最大并行度 (max degree of parallelism) 并说明如何修改此设置。</span><span class="sxs-lookup"><span data-stu-id="6ad75-103">This topic defines max degree of parallelism and explains how to modify this setting in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="6ad75-104">在运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Enterprise 或更高版本的多处理器计算机上，索引语句可能会像其他查询那样，使用多个处理器来执行与索引语句关联的扫描、排序和索引操作。</span><span class="sxs-lookup"><span data-stu-id="6ad75-104">On multiprocessor computers that are running [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Enterprise or higher, index statements may use multiple processors to perform the scan, sort, and index operations associated with the index statement just like other queries do.</span></span> <span data-ttu-id="6ad75-105">用于运行单个索引语句的处理器数由 [最大并行度](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md) 配置选项、当前工作负荷以及索引统计信息决定。</span><span class="sxs-lookup"><span data-stu-id="6ad75-105">The number of processors used to run a single index statement is determined by the [max degree of parallelism](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md) configuration option, the current workload, and the index statistics.</span></span> <span data-ttu-id="6ad75-106">max degree of parallelism 选项决定了执行并行计划时使用的最大处理器数。</span><span class="sxs-lookup"><span data-stu-id="6ad75-106">The max degree of parallelism option determines the maximum number of processors to use in parallel plan execution.</span></span> <span data-ttu-id="6ad75-107">如果 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 检测到系统忙，索引操作的并行度将自动降低，然后再开始执行语句。</span><span class="sxs-lookup"><span data-stu-id="6ad75-107">If the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] detects that the system is busy, the degree of parallelism of the index operation is automatically reduced before statement execution starts.</span></span> <span data-ttu-id="6ad75-108">如果非分区索引的第一个键列包含有限数量的非重复值，或者每个非重复值的出现频率变化较大， [!INCLUDE[ssDE](../../includes/ssde-md.md)] 也可能会降低并行度。</span><span class="sxs-lookup"><span data-stu-id="6ad75-108">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] can also reduce the degree of parallelism if the leading key column of a non-partitioned index has a limited number of distinct values or the frequency of each distinct value varies significantly.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6ad75-109">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的各版本中均不提供并行索引操作。</span><span class="sxs-lookup"><span data-stu-id="6ad75-109">Parallel index operations are not available in every [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] edition.</span></span> <span data-ttu-id="6ad75-110">有关详细信息，请参阅 [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)。</span><span class="sxs-lookup"><span data-stu-id="6ad75-110">For more information, see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
 <span data-ttu-id="6ad75-111">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="6ad75-111">**In This Topic**</span></span>  
  
-   <span data-ttu-id="6ad75-112">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="6ad75-112">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="6ad75-113">限制和局限</span><span class="sxs-lookup"><span data-stu-id="6ad75-113">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="6ad75-114">安全性</span><span class="sxs-lookup"><span data-stu-id="6ad75-114">Security</span></span>](#Security)  
  
-   <span data-ttu-id="6ad75-115">**若要设置最大并行度，请使用：**</span><span class="sxs-lookup"><span data-stu-id="6ad75-115">**To set the max degree of parallelism, using:**</span></span>  
  
     [<span data-ttu-id="6ad75-116">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="6ad75-116">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="6ad75-117">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="6ad75-117">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="6ad75-118">开始之前</span><span class="sxs-lookup"><span data-stu-id="6ad75-118">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="6ad75-119">限制和局限</span><span class="sxs-lookup"><span data-stu-id="6ad75-119">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="6ad75-120">查询优化器使用的处理器数量通常能够提供最佳的性能。</span><span class="sxs-lookup"><span data-stu-id="6ad75-120">The number of processors that are used by the query optimizer typically provides optimal performance.</span></span> <span data-ttu-id="6ad75-121">但是，有些操作（如创建、重新生成或删除很大的索引）占用大量资源，在索引操作期间会造成没有足够的资源供其他应用程序和数据库操作使用。</span><span class="sxs-lookup"><span data-stu-id="6ad75-121">However, operations such as creating, rebuilding, or dropping very large indexes are resource intensive and can cause insufficient resources for other applications and database operations for the duration of the index operation.</span></span> <span data-ttu-id="6ad75-122">出现此问题时，您可以通过限制用于索引操作的处理器数，手动配置用于运行索引语句的最大处理器数。</span><span class="sxs-lookup"><span data-stu-id="6ad75-122">When this problem occurs, you can manually configure the maximum number of processors that are used to run the index statement by limiting the number of processors to use for the index operation.</span></span>  
  
-   <span data-ttu-id="6ad75-123">MAXDOP 索引选项只为指定此选项的查询覆盖 max degree of parallelism 配置选项。</span><span class="sxs-lookup"><span data-stu-id="6ad75-123">The MAXDOP index option overrides the max degree of parallelism configuration option only for the query specifying this option.</span></span> <span data-ttu-id="6ad75-124">下表列出了可为 max degree of parallelism 配置选项和 MAXDOP 索引选项指定的有效整数值。</span><span class="sxs-lookup"><span data-stu-id="6ad75-124">The following table lists the valid integer values that can be specified with the max degree of parallelism configuration option and the MAXDOP index option.</span></span>  
  
    |<span data-ttu-id="6ad75-125">值</span><span class="sxs-lookup"><span data-stu-id="6ad75-125">Value</span></span>|<span data-ttu-id="6ad75-126">说明</span><span class="sxs-lookup"><span data-stu-id="6ad75-126">Description</span></span>|  
    |-----------|-----------------|  
    |<span data-ttu-id="6ad75-127">0</span><span class="sxs-lookup"><span data-stu-id="6ad75-127">0</span></span>|<span data-ttu-id="6ad75-128">指定服务器根据当前系统工作负荷确定所使用的 CPU 数目。</span><span class="sxs-lookup"><span data-stu-id="6ad75-128">Specifies that the server determines the number of CPUs that are used, depending on the current system workload.</span></span> <span data-ttu-id="6ad75-129">这是默认值，还是推荐设置。</span><span class="sxs-lookup"><span data-stu-id="6ad75-129">This is the default value and recommended setting.</span></span>|  
    |<span data-ttu-id="6ad75-130">1</span><span class="sxs-lookup"><span data-stu-id="6ad75-130">1</span></span>|<span data-ttu-id="6ad75-131">取消生成并行计划。</span><span class="sxs-lookup"><span data-stu-id="6ad75-131">Suppresses parallel plan generation.</span></span> <span data-ttu-id="6ad75-132">操作将以串行方式执行。</span><span class="sxs-lookup"><span data-stu-id="6ad75-132">The operation will be executed serially.</span></span>|  
    |<span data-ttu-id="6ad75-133">2-64</span><span class="sxs-lookup"><span data-stu-id="6ad75-133">2-64</span></span>|<span data-ttu-id="6ad75-134">将处理器的数量限制为指定的值。</span><span class="sxs-lookup"><span data-stu-id="6ad75-134">Limits the number of processors to the specified value.</span></span> <span data-ttu-id="6ad75-135">根据当前工作负荷，可能使用较少的处理器。</span><span class="sxs-lookup"><span data-stu-id="6ad75-135">Fewer processors may be used depending on the current workload.</span></span> <span data-ttu-id="6ad75-136">如果指定的值大于可用的 CPU 数量，将使用实际可用的 CPU 数量。</span><span class="sxs-lookup"><span data-stu-id="6ad75-136">If a value larger than the number of available CPUs is specified, the actual number of available CPUs is used.</span></span>|  
  
-   <span data-ttu-id="6ad75-137">并行索引执行和 MAXDOP 索引选项适用于下列 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句：</span><span class="sxs-lookup"><span data-stu-id="6ad75-137">Parallel index execution and the MAXDOP index option apply to the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statements:</span></span>  
  
    -   <span data-ttu-id="6ad75-138">CREATE INDEX</span><span class="sxs-lookup"><span data-stu-id="6ad75-138">CREATE INDEX</span></span>  
  
    -   <span data-ttu-id="6ad75-139">ALTER INDEX REBUILD</span><span class="sxs-lookup"><span data-stu-id="6ad75-139">ALTER INDEX REBUILD</span></span>  
  
    -   <span data-ttu-id="6ad75-140">DROP INDEX（只适用于聚集索引。）</span><span class="sxs-lookup"><span data-stu-id="6ad75-140">DROP INDEX (This applies to clustered indexes only.)</span></span>  
  
    -   <span data-ttu-id="6ad75-141">ALTER TABLE ADD (索引) CONSTRAINT</span><span class="sxs-lookup"><span data-stu-id="6ad75-141">ALTER TABLE ADD (index) CONSTRAINT</span></span>  
  
    -   <span data-ttu-id="6ad75-142">ALTER TABLE DROP (聚集索引) CONSTRAINT</span><span class="sxs-lookup"><span data-stu-id="6ad75-142">ALTER TABLE DROP (clustered index) CONSTRAINT</span></span>  
  
-   <span data-ttu-id="6ad75-143">不能在 ALTER INDEX REORGANIZE 语句中指定 MAXDOP 索引选项。</span><span class="sxs-lookup"><span data-stu-id="6ad75-143">The MAXDOP index option cannot be specified in the ALTER INDEX REORGANIZE statement.</span></span>  
  
-   <span data-ttu-id="6ad75-144">如果查询优化器将并行度应用于生成操作，则需要排序的已分区索引操作的内存需求可能会很大。</span><span class="sxs-lookup"><span data-stu-id="6ad75-144">Memory requirements for partitioned index operations that require sorting can be greater if the query optimizer applies degrees of parallelism to the build operation.</span></span> <span data-ttu-id="6ad75-145">并行度越高，内存需求就越大。</span><span class="sxs-lookup"><span data-stu-id="6ad75-145">The higher the degrees of parallelism, the greater the memory requirement is.</span></span> <span data-ttu-id="6ad75-146">有关详细信息，请参阅 [Partitioned Tables and Indexes](../partitions/partitioned-tables-and-indexes.md)。</span><span class="sxs-lookup"><span data-stu-id="6ad75-146">For more information, see [Partitioned Tables and Indexes](../partitions/partitioned-tables-and-indexes.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="6ad75-147">Security</span><span class="sxs-lookup"><span data-stu-id="6ad75-147">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="6ad75-148">权限</span><span class="sxs-lookup"><span data-stu-id="6ad75-148">Permissions</span></span>  
 <span data-ttu-id="6ad75-149">要求对表或视图具有 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="6ad75-149">Requires ALTER permission on the table or view.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="6ad75-150">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="6ad75-150">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-set-max-degree-of-parallelism-on-an-index"></a><span data-ttu-id="6ad75-151">设置索引的最大并行度</span><span class="sxs-lookup"><span data-stu-id="6ad75-151">To set max degree of parallelism on an index</span></span>  
  
1.  <span data-ttu-id="6ad75-152">在对象资源管理器中，单击加号以展开所需的数据库，其中包含您要设置索引最大并行度的表。</span><span class="sxs-lookup"><span data-stu-id="6ad75-152">In Object Explorer, click the plus sign to expand the database that contains the table on which you want to set max degree of parallelism for an index.</span></span>  
  
2.  <span data-ttu-id="6ad75-153">展开 **“表”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="6ad75-153">Expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="6ad75-154">单击加号以展开您要设置索引的最大并行度的表。</span><span class="sxs-lookup"><span data-stu-id="6ad75-154">Click the plus sign to expand the table on which you want to set max degree of parallelism for an index.</span></span>  
  
4.  <span data-ttu-id="6ad75-155">展开 **“索引”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="6ad75-155">Expand the **Indexes** folder.</span></span>  
  
5.  <span data-ttu-id="6ad75-156">右键单击要为其设置最大并行度的索引，然后选择“属性”  。</span><span class="sxs-lookup"><span data-stu-id="6ad75-156">Right-click the index for which you want to set the max degree of parallelism and select **Properties**.</span></span>  
  
6.  <span data-ttu-id="6ad75-157">在 **“选择页”** 下，选择 **“选项”** 。</span><span class="sxs-lookup"><span data-stu-id="6ad75-157">Under **Select a page**, select **Options**.</span></span>  
  
7.  <span data-ttu-id="6ad75-158">选择 **“最大并行度”** ，然后输入 1 和 64 之间的某个值。</span><span class="sxs-lookup"><span data-stu-id="6ad75-158">Select **Maximum degree of parallelism**, and then enter some value between 1 and 64.</span></span>  
  
8.  <span data-ttu-id="6ad75-159">单击“确定”。 </span><span class="sxs-lookup"><span data-stu-id="6ad75-159">Click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="6ad75-160">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="6ad75-160">Using Transact-SQL</span></span>  
  
#### <a name="to-set-max-degree-of-parallelism-on-an-existing-index"></a><span data-ttu-id="6ad75-161">设置现有索引的最大并行度</span><span class="sxs-lookup"><span data-stu-id="6ad75-161">To set max degree of parallelism on an existing index</span></span>  
  
1.  <span data-ttu-id="6ad75-162">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="6ad75-162">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="6ad75-163">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="6ad75-163">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="6ad75-164">将以下示例复制并粘贴到查询窗口中，然后单击“执行”  。</span><span class="sxs-lookup"><span data-stu-id="6ad75-164">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;   
    GO  
    /*Alters the IX_ProductVendor_VendorID index on the Purchasing.ProductVendor table so that, if the server has eight or more processors, the Database Engine will limit the execution of the index operation to eight or fewer processors.  
    */  
    ALTER INDEX IX_ProductVendor_VendorID ON Purchasing.ProductVendor  
    REBUILD WITH (MAXDOP=8);   
    GO  
    ```  
  
 <span data-ttu-id="6ad75-165">有关详细信息，请参阅 [ALTER INDEX (Transact-SQL)](/sql/t-sql/statements/alter-index-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="6ad75-165">For more information, see [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql).</span></span>  
  
#### <a name="set-max-degree-of-parallelism-on-a-new-index"></a><span data-ttu-id="6ad75-166">设置新建索引的最大并行度</span><span class="sxs-lookup"><span data-stu-id="6ad75-166">Set max degree of parallelism on a new index</span></span>  
  
1.  <span data-ttu-id="6ad75-167">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="6ad75-167">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="6ad75-168">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="6ad75-168">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="6ad75-169">将以下示例复制并粘贴到查询窗口中，然后单击“执行”  。</span><span class="sxs-lookup"><span data-stu-id="6ad75-169">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    CREATE INDEX IX_ProductVendor_NewVendorID   
    ON Purchasing.ProductVendor (BusinessEntityID)  
    WITH (MAXDOP=8);  
    GO  
    ```  
  
 <span data-ttu-id="6ad75-170">有关详细信息，请参阅 [CREATE INDEX (Transact-SQL)](/sql/t-sql/statements/create-index-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="6ad75-170">For more information, see [CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql).</span></span>  
  
  
