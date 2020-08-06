---
title: SQL Server Management Studio 对内存中 OLTP 的支持 | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: ee847b5f-6a1a-448e-a746-d61a023881ff
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 644ba0cfdbe2f0043364c633676bbc536c641efa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577641"
---
# <a name="sql-server-management-studio-support-for-in-memory-oltp"></a><span data-ttu-id="efa53-102">对内存中 OLTP 的 SQL Server Management Studio 支持</span><span class="sxs-lookup"><span data-stu-id="efa53-102">SQL Server Management Studio Support for In-Memory OLTP</span></span>
  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="efa53-103">是用于管理 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 基础结构的集成环境。</span><span class="sxs-lookup"><span data-stu-id="efa53-103">is an integrated environment for managing your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] infrastructure.</span></span> [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="efa53-104">提供用于配置、监视和管理 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例的工具。</span><span class="sxs-lookup"><span data-stu-id="efa53-104">provides tools to configure, monitor, and administer instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="efa53-105">有关详细信息，请参阅 [SQL Server Management Studio](../../ssms/sql-server-management-studio-ssms.md)</span><span class="sxs-lookup"><span data-stu-id="efa53-105">For more information, see [SQL Server Management Studio](../../ssms/sql-server-management-studio-ssms.md)</span></span>  
  
 <span data-ttu-id="efa53-106">本主题中的任务说明如何使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 来管理内存优化的表、内存优化的表的索引、本机编译的存储过程以及用户定义的内存优化的表类型。</span><span class="sxs-lookup"><span data-stu-id="efa53-106">The tasks in this topic describe how to use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to manage memory-optimized tables; indexes on memory-optimized tables; natively compiled stored procedures; and user-defined, memory-optimized table types.</span></span>  
  
 <span data-ttu-id="efa53-107">有关如何以编程方式创建内存优化表的信息，请参阅 [创建内存优化表和本机编译的存储过程](creating-a-memory-optimized-table-and-a-natively-compiled-stored-procedure.md)。</span><span class="sxs-lookup"><span data-stu-id="efa53-107">For information on how to programmatically create memory-optimized tables, see [Creating a Memory-Optimized Table and a Natively Compiled Stored Procedure](creating-a-memory-optimized-table-and-a-natively-compiled-stored-procedure.md).</span></span>  
  
### <a name="to-create-a-database-with-a-memory-optimized-data-filegroup"></a><span data-ttu-id="efa53-108">使用内存优化的数据文件组创建数据库</span><span class="sxs-lookup"><span data-stu-id="efa53-108">To create a database with a memory-optimized data filegroup</span></span>  
  
1.  <span data-ttu-id="efa53-109">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库引擎实例，然后展开该实例。</span><span class="sxs-lookup"><span data-stu-id="efa53-109">In **Object Explorer**, connect to an instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Database Engine and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="efa53-110">右键单击“数据库”，然后单击“新建数据库”。</span><span class="sxs-lookup"><span data-stu-id="efa53-110">Right-click **Databases**, and then click **New Database**.</span></span>  
  
3.  <span data-ttu-id="efa53-111">若要添加新内存优化的数据文件组，请单击“文件组”页。</span><span class="sxs-lookup"><span data-stu-id="efa53-111">To add a new memory-optimized data filegroup, click the **Filegroups** page.</span></span> <span data-ttu-id="efa53-112">在“内存优化数据”下，单击“添加文件组”，然后输入内存优化数据文件组的名称。</span><span class="sxs-lookup"><span data-stu-id="efa53-112">Under **MEMORY OPTIMIZED DATA**, click **Add filegroup** and then enter the name of the memory-optimized data filegroup.</span></span>  <span data-ttu-id="efa53-113">标有 **“FILESTREAM 文件”** 的列表示文件组中的容器数。</span><span class="sxs-lookup"><span data-stu-id="efa53-113">The column labeled **FILESTREAM Files** represents the number of containers in the filegroup.</span></span> <span data-ttu-id="efa53-114">容器是在 **“常规”** 页上添加的。</span><span class="sxs-lookup"><span data-stu-id="efa53-114">Containers are added on the **General** page.</span></span>  
  
4.  <span data-ttu-id="efa53-115">要向文件组添加文件（容器），请单击“常规”页。</span><span class="sxs-lookup"><span data-stu-id="efa53-115">To add a file (container) to the filegroup, click the **General** page.</span></span> <span data-ttu-id="efa53-116">在 **“数据库文件”** 下，单击 **“添加”** 。</span><span class="sxs-lookup"><span data-stu-id="efa53-116">Under **Database files**, click **Add**.</span></span> <span data-ttu-id="efa53-117">在“文件类型”中选择“FILESTREAM 数据”，指定容器的逻辑名称，选择内存优化文件组，并确保“自动增长/最大大小”设置为“无限制”。</span><span class="sxs-lookup"><span data-stu-id="efa53-117">Select **File Type** as **FILESTREAM Data**, specify the logical name of the container, select the memory-optimized filegroup, and make sure that **Autogrowth / Maxsize** is set to **Unlimited**.</span></span>  
  
     <span data-ttu-id="efa53-118">有关如何使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 创建新数据库的更多信息，请参阅[创建数据库](../databases/create-a-database.md)。</span><span class="sxs-lookup"><span data-stu-id="efa53-118">For more information on how to create a new database by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], see [Create a Database](../databases/create-a-database.md).</span></span>  
  
### <a name="to-create-a-memory-optimized-table"></a><span data-ttu-id="efa53-119">创建内存优化的表</span><span class="sxs-lookup"><span data-stu-id="efa53-119">To create a memory-optimized table</span></span>  
  
1.  <span data-ttu-id="efa53-120">在“对象资源管理器”中，右键单击数据库的**Tables**“表”节点，单击“新建”，然后单击“内存优化的表”。</span><span class="sxs-lookup"><span data-stu-id="efa53-120">In **Object Explorer**, right-click the **Tables** node of your database, click **New**, and then click **Memory Optimized Table**.</span></span>  
  
     <span data-ttu-id="efa53-121">此时会显示用于创建内存优化表的模板。</span><span class="sxs-lookup"><span data-stu-id="efa53-121">A template for creating memory-optimized tables is displayed.</span></span>  
  
2.  <span data-ttu-id="efa53-122">若要替换模板参数，请单击 **“指定模板参数的值”** （在 **“查询”** 菜单上）。</span><span class="sxs-lookup"><span data-stu-id="efa53-122">To replace the template parameters, click **Specify Values for Template Parameters** on the **Query** menu.</span></span>  
  
     <span data-ttu-id="efa53-123">有关如何使用模板的更多信息，请参阅 [Template Explorer](../../ssms/template/template-explorer.md)。</span><span class="sxs-lookup"><span data-stu-id="efa53-123">For more information on how to use templates, see [Template Explorer](../../ssms/template/template-explorer.md).</span></span>  
  
3.  <span data-ttu-id="efa53-124">在“对象资源管理器”中，表先按基于磁盘的表，然后按内存优化表的顺序排序。</span><span class="sxs-lookup"><span data-stu-id="efa53-124">In **Object Explorer**, tables will be ordered first by disk-based tables followed by memory-optimized tables.</span></span> <span data-ttu-id="efa53-125">使用 **“对象资源管理器详细信息”** 可以查看按名称排序的所有表。</span><span class="sxs-lookup"><span data-stu-id="efa53-125">Use **Object Explorer Details** to see all tables ordered by name.</span></span>  
  
### <a name="to-create-a-natively-compiled-stored-procedure"></a><span data-ttu-id="efa53-126">创建本机编译的存储过程</span><span class="sxs-lookup"><span data-stu-id="efa53-126">To create a natively compiled stored procedure</span></span>  
  
1.  <span data-ttu-id="efa53-127">在“对象资源管理器”中，右键单击数据库的“存储过程”节点，单击“新建”，然后单击“本机编译的存储过程”。</span><span class="sxs-lookup"><span data-stu-id="efa53-127">In **Object Explorer**, right-click the **Stored Procedures** node of your database, click **New**, and then click **Natively Compiled Stored Procedure**.</span></span>  
  
     <span data-ttu-id="efa53-128">此时会显示用于创建本机编译存储过程的模板。</span><span class="sxs-lookup"><span data-stu-id="efa53-128">A template for creating natively compiled stored procedures is displayed.</span></span>  
  
2.  <span data-ttu-id="efa53-129">若要替换模板参数，请单击 **“指定模板参数的值”** （在 **“查询”** 菜单上）。</span><span class="sxs-lookup"><span data-stu-id="efa53-129">To replace the template parameters, click **Specify Values for Template Parameters** on the **Query menu**.</span></span>  
  
     <span data-ttu-id="efa53-130">有关如何创建新存储过程的更多信息，请参阅 [Create a Stored Procedure](../stored-procedures/create-a-stored-procedure.md)。</span><span class="sxs-lookup"><span data-stu-id="efa53-130">For more information on how to create a new stored procedure, see [Create a Stored Procedure](../stored-procedures/create-a-stored-procedure.md).</span></span>  
  
### <a name="to-create-a-user-defined-memory-optimized-table-type"></a><span data-ttu-id="efa53-131">创建用户定义的内存优化表类型</span><span class="sxs-lookup"><span data-stu-id="efa53-131">To create a user-defined memory-optimized table type</span></span>  
  
1.  <span data-ttu-id="efa53-132">在“对象资源管理器”中，展开数据库的“类型”节点，右键单击“用户定义的表类型”节点，单击“新建”，然后单击“用户定义的内存优化表类型”。</span><span class="sxs-lookup"><span data-stu-id="efa53-132">In **Object Explorer**, expand the **Types** node of your database, right-click the **User-Defined Table Types** node, click **New**, and then click **User-Defined Memory Optimized Table Type**.</span></span>  
  
     <span data-ttu-id="efa53-133">将显示创建用户定义的内存优化表类型所用的模板。</span><span class="sxs-lookup"><span data-stu-id="efa53-133">A template for creating user-defined memory-optimized table type is displayed.</span></span>  
  
2.  <span data-ttu-id="efa53-134">若要替换模板参数，请单击 **“指定模板参数的值”** （在 **“查询”** 菜单上）。</span><span class="sxs-lookup"><span data-stu-id="efa53-134">To replace the template parameters, click **Specify Values for Template Parameters** on the **Query** menu.</span></span>  
  
     <span data-ttu-id="efa53-135">有关如何创建新存储过程的更多信息，请参阅 [CREATE TYPE (Transact-SQL)](/sql/t-sql/statements/create-type-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="efa53-135">For more information on how to create a new stored procedure, see [CREATE TYPE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-type-transact-sql).</span></span>  
  
## <a name="memory-monitoring"></a><span data-ttu-id="efa53-136">内存监视</span><span class="sxs-lookup"><span data-stu-id="efa53-136">Memory Monitoring</span></span>  
  
#### <a name="view-memory-usage-by-memory-optimized-objects-report"></a><span data-ttu-id="efa53-137">查看内存优化对象的内存使用情况报表</span><span class="sxs-lookup"><span data-stu-id="efa53-137">View Memory Usage by Memory-Optimized Objects Report</span></span>  
  
-   <span data-ttu-id="efa53-138">在“对象资源管理器”中，右键单击数据库，然后依次单击“报表”、“标准报表”、“内存优化对象的内存使用情况”。</span><span class="sxs-lookup"><span data-stu-id="efa53-138">In **Object Explorer**, right-click your database, click **Reports**, click **Standard Reports**, and then click **Memory Usage By Memory Optimized Objects**.</span></span>  
  
     <span data-ttu-id="efa53-139">该报表提供数据库中的内存优化对象占用的内存空间详细数据。</span><span class="sxs-lookup"><span data-stu-id="efa53-139">This report provides detailed data on the utilization of memory space by memory-optimized objects within the database.</span></span>  
  
#### <a name="view-properties-for-allocated-and-used-memory-for-a-table-database"></a><span data-ttu-id="efa53-140">查看为表、数据库分配和使用的内存的属性</span><span class="sxs-lookup"><span data-stu-id="efa53-140">View Properties for Allocated and Used Memory for a Table, Database</span></span>  
  
1.  <span data-ttu-id="efa53-141">获取有关内存使用情况的信息：</span><span class="sxs-lookup"><span data-stu-id="efa53-141">To get information about in-memory usage:</span></span>  
  
    -   <span data-ttu-id="efa53-142">在“对象资源管理器”中，右键单击内存优化表，然后依次单击“属性”、“存储”页。</span><span class="sxs-lookup"><span data-stu-id="efa53-142">In **Object Explorer**, right-click on your memory-optimized table, click **Properties**, and then the **Storage** page.</span></span> <span data-ttu-id="efa53-143">**“数据空间”** 属性的值指示表中数据占用的内存。</span><span class="sxs-lookup"><span data-stu-id="efa53-143">The value for the **Data Space** property indicates the memory used by the data in the table.</span></span> <span data-ttu-id="efa53-144">**“索引空间”** 属性的值指示表中索引占用的内存。</span><span class="sxs-lookup"><span data-stu-id="efa53-144">The value for the **Index Space** property indicates the memory used by the indexes on table.</span></span>  
  
    -   <span data-ttu-id="efa53-145">在“对象资源管理器”中，右键单击数据库，单击“属性”，然后单击“常规”页。</span><span class="sxs-lookup"><span data-stu-id="efa53-145">In **Object Explorer**, right-click on your database, click **Properties**, and then click the **General** page.</span></span> <span data-ttu-id="efa53-146">“分配给内存优化对象的内存”属性的值指示分配给数据库中内存优化对象的内存。</span><span class="sxs-lookup"><span data-stu-id="efa53-146">The value for the **Memory Allocated To Memory Optimized Objects** property indicates the memory allocated to memory-optimized objects in the database.</span></span> <span data-ttu-id="efa53-147">“内存优化对象使用的内存”属性的值指示数据库中内存优化对象使用的内存。</span><span class="sxs-lookup"><span data-stu-id="efa53-147">The value for the **Memory Used By Memory Optimized Objects** property indicates the memory used by memory-optimized objects in the database.</span></span>  
  
## <a name="supported-features-in-ssmanstudiofull"></a><span data-ttu-id="efa53-148">中支持的功能 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]</span><span class="sxs-lookup"><span data-stu-id="efa53-148">Supported Features in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]</span></span>  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="efa53-149">支持具有内存优化的数据文件组、内存优化的表、索引和本机编译的存储过程的数据库上数据库引擎所支持的功能和操作。</span><span class="sxs-lookup"><span data-stu-id="efa53-149">supports features and operations that are supported by the database engine on databases with memory-optimized data filegroup, memory-optimized tables, indexes, and natively compiled stored procedures.</span></span>  
  
 <span data-ttu-id="efa53-150">对于数据库、表、存储过程、用户定义的表类型或索引对象，以下 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 功能已得到更新或扩展，以便支持内存中 OLTP。</span><span class="sxs-lookup"><span data-stu-id="efa53-150">For database, table, stored procedure, user-defined table type, or index objects, the following [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] features have been updated or extended to support In-Memory OLTP.</span></span>  
  
-   <span data-ttu-id="efa53-151">“对象资源管理器”</span><span class="sxs-lookup"><span data-stu-id="efa53-151">Object Explorer</span></span>  
  
    -   <span data-ttu-id="efa53-152">上下文菜单</span><span class="sxs-lookup"><span data-stu-id="efa53-152">Context menus</span></span>  
  
    -   <span data-ttu-id="efa53-153">筛选器设置</span><span class="sxs-lookup"><span data-stu-id="efa53-153">Filter settings</span></span>  
  
    -   <span data-ttu-id="efa53-154">编写脚本为</span><span class="sxs-lookup"><span data-stu-id="efa53-154">Script As</span></span>  
  
    -   <span data-ttu-id="efa53-155">任务</span><span class="sxs-lookup"><span data-stu-id="efa53-155">Tasks</span></span>  
  
    -   <span data-ttu-id="efa53-156">报表</span><span class="sxs-lookup"><span data-stu-id="efa53-156">Reports</span></span>  
  
    -   <span data-ttu-id="efa53-157">属性</span><span class="sxs-lookup"><span data-stu-id="efa53-157">Properties</span></span>  
  
    -   <span data-ttu-id="efa53-158">数据库任务：</span><span class="sxs-lookup"><span data-stu-id="efa53-158">Database tasks:</span></span>  
  
        -   <span data-ttu-id="efa53-159">附加和分离包含内存优化表的数据库。</span><span class="sxs-lookup"><span data-stu-id="efa53-159">Attach and detach a database that contains memory-optimized tables.</span></span>  
  
             <span data-ttu-id="efa53-160">“附加数据库”用户界面不显示内存优化数据文件组。</span><span class="sxs-lookup"><span data-stu-id="efa53-160">The **Attach Databases** user interface does not display the memory-optimized data filegroup.</span></span> <span data-ttu-id="efa53-161">但是，您可以继续附加数据库并且数据库将正确附加。</span><span class="sxs-lookup"><span data-stu-id="efa53-161">However, you can proceed with attaching the database and the database will be attached correctly.</span></span>  
  
            > [!NOTE]  
            >  <span data-ttu-id="efa53-162">如果要使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 附加具有内存优化数据文件组容器的数据库，并且该数据库的内存优化数据文件组容器是在另一台计算机上创建的，则该内存优化数据文件组容器在两台计算机上的位置必须相同。</span><span class="sxs-lookup"><span data-stu-id="efa53-162">If you want to use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to attach a database that has a memory-optimized data filegroup container, and if the database's memory-optimized data filegroup container was created on another computer, the location of the memory-optimized data filegroup container must be the same on both computers.</span></span> <span data-ttu-id="efa53-163">如果希望该数据库的内存优化数据文件组容器在新计算机上的位置不同，则可使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 附加该数据库。</span><span class="sxs-lookup"><span data-stu-id="efa53-163">If you want the location of the database's memory-optimized data filegroup container to be different on the new computer, you can, use [!INCLUDE[tsql](../../includes/tsql-md.md)] to attach the database.</span></span> <span data-ttu-id="efa53-164">在下例中，内存优化数据文件组容器在新计算机上的位置为 C:\Folder2。</span><span class="sxs-lookup"><span data-stu-id="efa53-164">In the following example, the location of the memory-optimized data filegroup container on the new computer is C:\Folder2.</span></span> <span data-ttu-id="efa53-165">但是，在第一台计算机上创建内存优化数据文件组容器时，该位置为 C:\Folder1。</span><span class="sxs-lookup"><span data-stu-id="efa53-165">But when the memory-optimized data filegroup container was created, on the first computer, the location was C:\Folder1.</span></span>  
            >   
            >  `CREATE DATABASE[imoltp] ON`  
            >   
            >  `(NAME =N'imoltp',FILENAME=N'C:\Folder2\imoltp.mdf'),`  
            >   
            >  `(NAME =N'imoltp_mod1',FILENAME=N'C:\Folder2\imoltp_mod1'),`  
            >   
            >  `(NAME =N'imoltp_log',FILENAME=N'C:\Folder2\imoltp_log.ldf')`  
            >   
            >  `FOR ATTACH`  
            >   
            >  `GO`  
  
        -   <span data-ttu-id="efa53-166">生成脚本。</span><span class="sxs-lookup"><span data-stu-id="efa53-166">Generate scripts.</span></span>  
  
             <span data-ttu-id="efa53-167">在 **“生成和发布脚本向导”** 中， **“检查对象是否存在”** 脚本编写选项的默认值是 FALSE。</span><span class="sxs-lookup"><span data-stu-id="efa53-167">In the **Generate and Publish Scripts Wizard**, the default value for **Check for object existence** scripting option is FALSE.</span></span> <span data-ttu-id="efa53-168">如果“检查对象是否存在”脚本编写选项的值在向导的“设置脚本编写选项”屏幕中设置为 TRUE，则生成的脚本将包含“CREATE PROCEDURE <过程名称> AS”和“ALTER PROCEDURE <过程名称> <过程定义>”。</span><span class="sxs-lookup"><span data-stu-id="efa53-168">If the value of **Check for object existence** scripting option is set to TRUE in the **Set Scripting Options** screen of the wizard, the script generated would contain "CREATE PROCEDURE <procedure_name> AS" and "ALTER PROCEDURE <procedure_name> <procedure_definition>".</span></span> <span data-ttu-id="efa53-169">在执行时，生成的脚本将返回错误，因为在本机编译的存储过程中不支持 ALTER PROCEDURE。</span><span class="sxs-lookup"><span data-stu-id="efa53-169">When executed, the generated script will return an error as ALTER PROCEDURE is not supported on natively compiled stored procedures.</span></span>  
  
             <span data-ttu-id="efa53-170">更改每个本机编译的存储过程的生成的脚本：</span><span class="sxs-lookup"><span data-stu-id="efa53-170">To change the generated script for each natively compiled stored procedure:</span></span>  
  
            1.  <span data-ttu-id="efa53-171">在“CREATE PROCEDURE <过程名称> AS”中，使用“<过程定义>”替换“AS”。</span><span class="sxs-lookup"><span data-stu-id="efa53-171">In "CREATE PROCEDURE <procedure_name> AS", replace "AS" with "<procedure_definition>".</span></span>  
  
            2.  <span data-ttu-id="efa53-172">删除“ALTER PROCEDURE <过程名称> <过程定义>”。</span><span class="sxs-lookup"><span data-stu-id="efa53-172">Delete "ALTER PROCEDURE <procedure_name> <procedure_definition>".</span></span>  
  
        -   <span data-ttu-id="efa53-173">复制数据库。</span><span class="sxs-lookup"><span data-stu-id="efa53-173">Copy databases.</span></span> <span data-ttu-id="efa53-174">对于具有内存优化的对象的数据库，将不在事务内执行在目标服务器上创建数据库以及传输数据。</span><span class="sxs-lookup"><span data-stu-id="efa53-174">For databases with memory-optimized objects, the creation of the database on the destination server and transfer of data will not be executed within a transaction.</span></span>  
  
        -   <span data-ttu-id="efa53-175">导入和导出数据。</span><span class="sxs-lookup"><span data-stu-id="efa53-175">Import and export data.</span></span> <span data-ttu-id="efa53-176">使用“[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 从一个或多个表或视图中导入和导出向导复制数据”选项。</span><span class="sxs-lookup"><span data-stu-id="efa53-176">Use the **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Import and Export WizardCopy data from one or more tables or views** option.</span></span> <span data-ttu-id="efa53-177">如果目标表是目标数据库中不存在的内存优化表：</span><span class="sxs-lookup"><span data-stu-id="efa53-177">If the destination table is a memory-optimized table that does not exist in the destination database:</span></span>  
  
            1.  <span data-ttu-id="efa53-178">在 **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 导入与导出向导”** 中的 **“指定表复制或查询”** 屏幕上，选择 **“复制一个或多个表或视图的数据”** 。</span><span class="sxs-lookup"><span data-stu-id="efa53-178">In the **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Import and Export Wizard**, in the **Specify Table Copy or Query** screen, select **Copy data from one or more tables or views**.</span></span> <span data-ttu-id="efa53-179">然后单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="efa53-179">Then click **Next**.</span></span>  
  
            2.  <span data-ttu-id="efa53-180">单击 **“编辑映射”** 。</span><span class="sxs-lookup"><span data-stu-id="efa53-180">Click **Edit Mappings**.</span></span> <span data-ttu-id="efa53-181">然后选择 **“创建目标表”** 并单击 **“编辑 SQL”** 。</span><span class="sxs-lookup"><span data-stu-id="efa53-181">Then select **Create destination table** and click **Edit SQL**.</span></span> <span data-ttu-id="efa53-182">在目标数据库上输入用于创建内存优化表的 CREATE TABLE 语法。</span><span class="sxs-lookup"><span data-stu-id="efa53-182">Enter the CREATE TABLE syntax for creating a memory-optimized table on the destination database.</span></span> <span data-ttu-id="efa53-183">单击 **“确定”** 并完成向导中的剩余步骤。</span><span class="sxs-lookup"><span data-stu-id="efa53-183">Click **OK** and complete the remaining steps in the wizard.</span></span>  
  
        -   <span data-ttu-id="efa53-184">维护计划。</span><span class="sxs-lookup"><span data-stu-id="efa53-184">Maintenance plans.</span></span> <span data-ttu-id="efa53-185">不支持对内存优化的表及其索引执行重新组织索引和重建索引的维护任务。</span><span class="sxs-lookup"><span data-stu-id="efa53-185">The maintenance tasks reorganize index and rebuild index are not supported on memory-optimized tables and their indexes.</span></span> <span data-ttu-id="efa53-186">因此，在执行重建索引和重新组织索引的维护计划时，将忽略选定数据库中的内存优化表及其索引。</span><span class="sxs-lookup"><span data-stu-id="efa53-186">Therefore, when a maintenance plan for rebuild index and reorganize index are executed, the memory-optimized tables and their indexes in the selected databases are omitted.</span></span>  
  
             <span data-ttu-id="efa53-187">对内存优化的表及其索引的抽样扫描不支持维护任务更新统计信息。</span><span class="sxs-lookup"><span data-stu-id="efa53-187">The maintenance task update statistics are not supported with a sample scan on memory-optimized tables and their indexes.</span></span> <span data-ttu-id="efa53-188">因此，在执行更新统计信息的维护计划时，始终将内存优化的表及其索引的统计信息更新到 `WITH FULLSCAN, NORECOMPUTE`。</span><span class="sxs-lookup"><span data-stu-id="efa53-188">Therefore, when a maintenance plan for update statistics is executed, the statistics for memory-optimized tables and their indexes are always updated to `WITH FULLSCAN, NORECOMPUTE`.</span></span>  
  
-   <span data-ttu-id="efa53-189">“对象资源管理器详细信息”窗格</span><span class="sxs-lookup"><span data-stu-id="efa53-189">Object Explorer details pane</span></span>  
  
-   <span data-ttu-id="efa53-190">模板资源管理器</span><span class="sxs-lookup"><span data-stu-id="efa53-190">Template Explorer</span></span>  
  
## <a name="unsupported-features-in-ssmanstudiofull"></a><span data-ttu-id="efa53-191">中不支持的功能 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]</span><span class="sxs-lookup"><span data-stu-id="efa53-191">Unsupported Features in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]</span></span>  
 <span data-ttu-id="efa53-192">对于内存中 OLTP 对象，数据库引擎不支持的功能和操作， [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 同样不支持。</span><span class="sxs-lookup"><span data-stu-id="efa53-192">For In-Memory OLTP objects, [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] does not support features and operations that are also not supported by the database engine.</span></span>  
  
 <span data-ttu-id="efa53-193">有关不支持的功能的详细信息 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，请参阅[支持的 SQL Server 功能](unsupported-sql-server-features-for-in-memory-oltp.md)。</span><span class="sxs-lookup"><span data-stu-id="efa53-193">For more information on unsupported [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] features, see [Supported SQL Server Features](unsupported-sql-server-features-for-in-memory-oltp.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efa53-194">另请参阅</span><span class="sxs-lookup"><span data-stu-id="efa53-194">See Also</span></span>  
 [<span data-ttu-id="efa53-195">SQL Server 对内存中 OLTP 的支持</span><span class="sxs-lookup"><span data-stu-id="efa53-195">SQL Server Support for In-Memory OLTP</span></span>](sql-server-support-for-in-memory-oltp.md)  
  
  
