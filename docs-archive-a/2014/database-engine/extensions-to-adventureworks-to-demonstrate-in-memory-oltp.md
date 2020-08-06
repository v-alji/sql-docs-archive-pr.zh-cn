---
title: 用于演示内存中 OLTP 的 AdventureWorks 扩展 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 0186b7f2-cead-4203-8360-b6890f37cde8
author: stevestein
ms.author: sstein
ms.openlocfilehash: 73a87751aa6cd4734f81b60cdd87a62939ba4ead
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693051"
---
# <a name="extensions-to-adventureworks-to-demonstrate-in-memory-oltp"></a><span data-ttu-id="002f8-102">演示内存中 OLTP 的 AdventureWorks 扩展</span><span class="sxs-lookup"><span data-stu-id="002f8-102">Extensions to AdventureWorks to Demonstrate In-Memory OLTP</span></span>
    
## <a name="overview"></a><span data-ttu-id="002f8-103">概述</span><span class="sxs-lookup"><span data-stu-id="002f8-103">Overview</span></span>  
 <span data-ttu-id="002f8-104">此示例演示属于 [!INCLUDE[hek_2](../includes/hek-2-md.md)] 一部分的新 [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]功能。</span><span class="sxs-lookup"><span data-stu-id="002f8-104">This sample showcases the new [!INCLUDE[hek_2](../includes/hek-2-md.md)] feature, which is part of [!INCLUDE[ssSQL14](../includes/sssql14-md.md)].</span></span> <span data-ttu-id="002f8-105">它演示新的内存优化表和本机编译的存储过程，可以用于展示 [!INCLUDE[hek_2](../includes/hek-2-md.md)]的性能优势。</span><span class="sxs-lookup"><span data-stu-id="002f8-105">It shows the new memory-optimized tables and natively-compiled stored procedures, and can be used to demonstrate performance benefits of [!INCLUDE[hek_2](../includes/hek-2-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="002f8-106">若要查看 SQL Server 2016 的本主题，请参阅 [演示内存中 OLTP 的 AdventureWorks 扩展](https://msdn.microsoft.com/library/mt465764.aspx)</span><span class="sxs-lookup"><span data-stu-id="002f8-106">To view this topic for SQL Server 2016, see [Extensions to AdventureWorks to Demonstrate In-Memory OLTP](https://msdn.microsoft.com/library/mt465764.aspx)</span></span>  
  
 <span data-ttu-id="002f8-107">该示例将 AdventureWorks 数据库中的 5 个表迁移到内存优化表，并包括销售订单处理演示工作负荷。</span><span class="sxs-lookup"><span data-stu-id="002f8-107">The sample migrates 5 tables in the AdventureWorks database to memory-optimized, and it includes a demo workload for sales order processing.</span></span> <span data-ttu-id="002f8-108">可以使用此演示工作负荷了解在服务器上使用 [!INCLUDE[hek_2](../includes/hek-2-md.md)] 的性能优势。</span><span class="sxs-lookup"><span data-stu-id="002f8-108">You can use this demo workload to see the performance benefit of using [!INCLUDE[hek_2](../includes/hek-2-md.md)] on your server.</span></span>  
  
 <span data-ttu-id="002f8-109">在示例说明中，我们讨论将表迁移到 [!INCLUDE[hek_2](../includes/hek-2-md.md)] 时进行的权衡，以说明 [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]中对内存优化表（尚未）不支持的功能。</span><span class="sxs-lookup"><span data-stu-id="002f8-109">In the description of the sample we discuss the tradeoffs that were made in migrating the tables to [!INCLUDE[hek_2](../includes/hek-2-md.md)] to account for the features that are not (yet) supported for memory-optimized tables in [!INCLUDE[ssSQL14](../includes/sssql14-md.md)].</span></span>  
  
 <span data-ttu-id="002f8-110">此示例的文档的结构如下：</span><span class="sxs-lookup"><span data-stu-id="002f8-110">The documentation of this sample is structured as follows:</span></span>  
  
-   <span data-ttu-id="002f8-111">安装示例和运行演示工作负荷的[先决条件](#Prerequisites)</span><span class="sxs-lookup"><span data-stu-id="002f8-111">[Prerequisites](#Prerequisites) for installing the sample and running the demo workload</span></span>  
  
-   <span data-ttu-id="002f8-112">[基于 AdventureWorks 安装内存中 OLTP 示例](#InstallingtheIn-MemoryOLTPsamplebasedonAdventureWorks)的说明</span><span class="sxs-lookup"><span data-stu-id="002f8-112">Instructions for [Installing the In-Memory OLTP sample based on AdventureWorks](#InstallingtheIn-MemoryOLTPsamplebasedonAdventureWorks)</span></span>  
  
-   <span data-ttu-id="002f8-113">[示例表和过程的说明](#Descriptionofthesampletablesandprocedures)-这包括通过示例添加到 AdventureWorks 的表和过程的说明，以及将 [!INCLUDE[hek_2](../includes/hek-2-md.md)] 一些原始 AdventureWorks 表迁移到内存优化的注意事项</span><span class="sxs-lookup"><span data-stu-id="002f8-113">[Description of the sample tables and procedures](#Descriptionofthesampletablesandprocedures) - this includes descriptions of the tables and procedures added to AdventureWorks by the [!INCLUDE[hek_2](../includes/hek-2-md.md)] sample, as well as considerations for migrating some of the original AdventureWorks tables to memory-optimized</span></span>  
  
-   <span data-ttu-id="002f8-114">执行[使用演示工作负荷执行度量](#PerformanceMeasurementsusingtheDemoWorkload)的说明 - 包括有关安装和运行 ostress（一种用于驱动工作负荷的工具）以及运行演示工作负荷本身的说明</span><span class="sxs-lookup"><span data-stu-id="002f8-114">Instructions for performing [Performance Measurements using the Demo Workload](#PerformanceMeasurementsusingtheDemoWorkload) - this includes instructions for installing and running ostress, a tool using for driving the workload, as well as running the demo workload itself</span></span>  
  
-   [<span data-ttu-id="002f8-115">示例中的内存和磁盘空间利用率</span><span class="sxs-lookup"><span data-stu-id="002f8-115">Memory and Disk Space Utilization in the Sample</span></span>](#MemoryandDiskSpaceUtilizationintheSample)  
  
##  <a name="prerequisites"></a><a name="Prerequisites"></a><span data-ttu-id="002f8-116">先决条件</span><span class="sxs-lookup"><span data-stu-id="002f8-116">Prerequisites</span></span>  
  
-   [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]<span data-ttu-id="002f8-117">RTM-评估版、开发人员版或企业版</span><span class="sxs-lookup"><span data-stu-id="002f8-117">RTM - Evaluation, Developer, or Enterprise edition</span></span>  
  
-   <span data-ttu-id="002f8-118">对于性能测试，服务器的规格类似于生产环境。</span><span class="sxs-lookup"><span data-stu-id="002f8-118">For performance testing, a server with specifications similar to your production environment.</span></span> <span data-ttu-id="002f8-119">对于此特定示例，应至少有 16 GB 内存可供 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]使用。</span><span class="sxs-lookup"><span data-stu-id="002f8-119">For this particular sample you should have at least 16GB of memory available to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="002f8-120">有关硬件的一般指导原则 [!INCLUDE[hek_2](../includes/hek-2-md.md)] ，请参阅以下博客文章：[https://cloudblogs.microsoft.com/sqlserver/2013/08/01/hardware-considerations-for-in-memory-oltp-in-sql-server-2014/](https://cloudblogs.microsoft.com/sqlserver/2013/08/01/hardware-considerations-for-in-memory-oltp-in-sql-server-2014/)</span><span class="sxs-lookup"><span data-stu-id="002f8-120">For general guidelines on hardware for [!INCLUDE[hek_2](../includes/hek-2-md.md)], see the following blog post:[https://cloudblogs.microsoft.com/sqlserver/2013/08/01/hardware-considerations-for-in-memory-oltp-in-sql-server-2014/](https://cloudblogs.microsoft.com/sqlserver/2013/08/01/hardware-considerations-for-in-memory-oltp-in-sql-server-2014/)</span></span>  
  
##  <a name="installing-the-hek_2-sample-based-on-adventureworks"></a><a name="InstallingtheIn-MemoryOLTPsamplebasedonAdventureWorks"></a><span data-ttu-id="002f8-121">基于 AdventureWorks 安装 [!INCLUDE[hek_2](../includes/hek-2-md.md)] 示例</span><span class="sxs-lookup"><span data-stu-id="002f8-121">Installing the [!INCLUDE[hek_2](../includes/hek-2-md.md)] sample based on AdventureWorks</span></span>  
 <span data-ttu-id="002f8-122">请按照以下步骤安装示例：</span><span class="sxs-lookup"><span data-stu-id="002f8-122">Follow these steps to install the sample:</span></span>  
  
1.  <span data-ttu-id="002f8-123">下载用于 AdventureWorks2014 数据库完整备份的存档：</span><span class="sxs-lookup"><span data-stu-id="002f8-123">Download the archive for the full backup of the AdventureWorks2014 database:</span></span>  
  
    1.  <span data-ttu-id="002f8-124">打开以下内容： [https://msftdbprodsamples.codeplex.com/downloads/get/880661](https://msftdbprodsamples.codeplex.com/downloads/get/880661) 。</span><span class="sxs-lookup"><span data-stu-id="002f8-124">Open the following: [https://msftdbprodsamples.codeplex.com/downloads/get/880661](https://msftdbprodsamples.codeplex.com/downloads/get/880661).</span></span>  
  
    2.  <span data-ttu-id="002f8-125">提示保存文件时，选择本地文件夹。</span><span class="sxs-lookup"><span data-stu-id="002f8-125">When prompted to save the file to a local folder.</span></span>  
  
2.  <span data-ttu-id="002f8-126">将 **AdventureWorks2014.bak** 文件提取到本地文件夹，例如“c:\temp”。</span><span class="sxs-lookup"><span data-stu-id="002f8-126">Extract the **AdventureWorks2014.bak** file to a local folder, for example 'c:\temp'.</span></span>  
  
3.  <span data-ttu-id="002f8-127">使用 [!INCLUDE[tsql](../includes/tsql-md.md)] 或 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]还原数据库备份：</span><span class="sxs-lookup"><span data-stu-id="002f8-127">Restore the database backup using [!INCLUDE[tsql](../includes/tsql-md.md)] or [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]:</span></span>  
  
    1.  <span data-ttu-id="002f8-128">标识数据文件的目标文件夹和文件名，例如</span><span class="sxs-lookup"><span data-stu-id="002f8-128">Identify the target folder and filename for the data file, for example</span></span>  
  
         <span data-ttu-id="002f8-129">“h:\DATA\AdventureWorks2014_Data.mdf”</span><span class="sxs-lookup"><span data-stu-id="002f8-129">'h:\DATA\AdventureWorks2014_Data.mdf'</span></span>  
  
    2.  <span data-ttu-id="002f8-130">标识日志文件的目标文件夹和文件名，例如</span><span class="sxs-lookup"><span data-stu-id="002f8-130">Identify the target folder and filename for the log file, for example</span></span>  
  
         <span data-ttu-id="002f8-131">“i:\DATA\AdventureWorks2014_log.ldf”</span><span class="sxs-lookup"><span data-stu-id="002f8-131">'i:\DATA\AdventureWorks2014_log.ldf'</span></span>  
  
        1.  <span data-ttu-id="002f8-132">日志文件应置于与数据文件不同的驱动器上，最好是低延迟驱动器（如 SSD 或 PCIe 存储）以实现最大性能。</span><span class="sxs-lookup"><span data-stu-id="002f8-132">The log file should be placed on a different drive than the data file, ideally a low latency drive such as an SSD or PCIe storage, for maximum performance.</span></span>  
  
     <span data-ttu-id="002f8-133">示例 T-SQL 脚本：</span><span class="sxs-lookup"><span data-stu-id="002f8-133">Example T-SQL script:</span></span>  
  
    ```  
    RESTORE DATABASE [AdventureWorks2014]   
      FROM DISK = N'C:\temp\AdventureWorks2014.bak'   
        WITH FILE = 1,    
      MOVE N'AdventureWorks2014_Data' TO N'h:\DATA\AdventureWorks2014_Data.mdf',    
      MOVE N'AdventureWorks2014_Log' TO N'i:\DATA\AdventureWorks2014_log.ldf'  
     GO  
    ```  
  
4.  <span data-ttu-id="002f8-134">通过在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]的查询窗口中运行命令，将数据库所有者更改为您服务器上的某个登录名：</span><span class="sxs-lookup"><span data-stu-id="002f8-134">Change the database owner to a login on your server, by running the following command in the query window of [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]:</span></span>  
  
    ```  
    ALTER AUTHORIZATION ON DATABASE::AdventureWorks2014 TO [<NewLogin>]  
    ```  
  
5.  <span data-ttu-id="002f8-135">[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] [!INCLUDE[hek_2](../includes/hek-2-md.md)] 从[SQL Server 2014 RTM 内存中 OLTP 示例中](https://go.microsoft.com/fwlink/?LinkID=396372)将示例脚本 "rtm sample" 下载到本地文件夹。</span><span class="sxs-lookup"><span data-stu-id="002f8-135">Download the sample script '[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] RTM [!INCLUDE[hek_2](../includes/hek-2-md.md)] Sample.sql' from [SQL Server 2014 RTM In-Memory OLTP Sample](https://go.microsoft.com/fwlink/?LinkID=396372) to a local folder.</span></span>  
  
6.  <span data-ttu-id="002f8-136">更新脚本 "RTM Sample" 中变量 "checkpoint_files_location" 的值 [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] [!INCLUDE[hek_2](../includes/hek-2-md.md)] ，以指向 [!INCLUDE[hek_2](../includes/hek-2-md.md)] 检查点文件的目标位置。</span><span class="sxs-lookup"><span data-stu-id="002f8-136">Update the value for the variable 'checkpoint_files_location' in the script '[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] RTM [!INCLUDE[hek_2](../includes/hek-2-md.md)] Sample.sql', to point to the target location for the [!INCLUDE[hek_2](../includes/hek-2-md.md)] checkpoint files.</span></span> <span data-ttu-id="002f8-137">检查点文件应置于具有良好顺序 IO 性能的驱动器上。</span><span class="sxs-lookup"><span data-stu-id="002f8-137">The checkpoint files should be placed on a drive with good sequential IO performance.</span></span>  
  
     <span data-ttu-id="002f8-138">将变量“database_name”的值更新为指向 AdventureWorks2014 数据库。</span><span class="sxs-lookup"><span data-stu-id="002f8-138">Update the value for the variable 'database_name' to point to the AdventureWorks2014 database.</span></span>  
  
    1.  <span data-ttu-id="002f8-139">请确保在 \' 路径名称中包含反斜杠 "</span><span class="sxs-lookup"><span data-stu-id="002f8-139">Be sure to include the backslash '\' as part of the path name</span></span>  
  
    2.  <span data-ttu-id="002f8-140">示例：</span><span class="sxs-lookup"><span data-stu-id="002f8-140">Example:</span></span>  
  
        ```  
        :setvar checkpoint_files_location "d:\DBData\"  
        ...  
        :setvar database_name "AdventureWorks2014"  
        ```  
  
7.  <span data-ttu-id="002f8-141">以下列两种方式之一执行示例脚本：</span><span class="sxs-lookup"><span data-stu-id="002f8-141">Execute the sample script, in one of two ways:</span></span>  
  
    1.  <span data-ttu-id="002f8-142">使用 sqlcmd 命令行实用工具。</span><span class="sxs-lookup"><span data-stu-id="002f8-142">Using the sqlcmd command-line utility.</span></span> <span data-ttu-id="002f8-143">例如，通过在包含脚本的文件夹中，从命令提示符处运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="002f8-143">For example, for example by running the following command from the command-line prompt in the folder containing the script:</span></span>  
  
        ```  
        sqlcmd -S . -E -i "ssSQL14 RTM hek_2 Sample.sql"  
        ```  
  
    2.  <span data-ttu-id="002f8-144">使用 Management Studio：</span><span class="sxs-lookup"><span data-stu-id="002f8-144">Using Management Studio:</span></span>  
  
        1.  <span data-ttu-id="002f8-145">[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] [!INCLUDE[hek_2](../includes/hek-2-md.md)] 在查询窗口中打开脚本 "RTM Sample .sql"</span><span class="sxs-lookup"><span data-stu-id="002f8-145">Open the script '[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] RTM [!INCLUDE[hek_2](../includes/hek-2-md.md)] Sample.sql' in a query window</span></span>  
  
        2.  <span data-ttu-id="002f8-146">连接到包含数据库 AdventureWorks2014 的目标服务器</span><span class="sxs-lookup"><span data-stu-id="002f8-146">Connect to the target server that contains the database AdventureWorks2014</span></span>  
  
        3.  <span data-ttu-id="002f8-147">通过单击 "查询 > SQLCMD 模式" 启用 SQLCMD 模式</span><span class="sxs-lookup"><span data-stu-id="002f8-147">Enable SQLCMD Mode, by clicking on 'Query -> SQLCMD Mode'</span></span>  
  
        4.  <span data-ttu-id="002f8-148">单击按钮 "执行" 以运行脚本</span><span class="sxs-lookup"><span data-stu-id="002f8-148">Click the button 'Execute' to run the script</span></span>  
  
##  <a name="description-of-the-sample-tables-and-procedures"></a><a name="Descriptionofthesampletablesandprocedures"></a> <span data-ttu-id="002f8-149">示例表和过程的说明</span><span class="sxs-lookup"><span data-stu-id="002f8-149">Description of the sample tables and procedures</span></span>  
 <span data-ttu-id="002f8-150">示例基于 AdventureWorks 中的现有表为产品和销售订单创建新表。</span><span class="sxs-lookup"><span data-stu-id="002f8-150">The sample creates new tables for products and sales orders, based on existing tables in AdventureWorks.</span></span> <span data-ttu-id="002f8-151">新表的架构类似于现有表，不过有几个区别，如下所述。</span><span class="sxs-lookup"><span data-stu-id="002f8-151">The schema of the new tables is similar to the existing tables, with a few differences, as explained below.</span></span>  
  
 <span data-ttu-id="002f8-152">新的内存优化表带有后缀“_inmem”。</span><span class="sxs-lookup"><span data-stu-id="002f8-152">The new memory-optimized tables carry the suffix '_inmem'.</span></span> <span data-ttu-id="002f8-153">示例还包括带有后缀“_ondisk”的对应表 - 这些表可以用于在系统上进行内存优化表与基于磁盘的表性能之间的一对一比较。</span><span class="sxs-lookup"><span data-stu-id="002f8-153">The sample also includes corresponding tables carrying the suffix '_ondisk' - these tables can be used to make a one-to-one comparison between the performance of memory-optimized tables and disk-based tables on your system..</span></span>  
  
 <span data-ttu-id="002f8-154">请注意，用于性能比较的工作负荷中使用的内存优化表具有完全持久性并且会完整记录。</span><span class="sxs-lookup"><span data-stu-id="002f8-154">Note that the memory-optimized tables used in the workload for performance comparison are fully durable and fully logged.</span></span> <span data-ttu-id="002f8-155">这些表不会牺牲持久性或可靠性来获取性能提升。</span><span class="sxs-lookup"><span data-stu-id="002f8-155">They do not sacrifice durability or reliability to attain the performance gain.</span></span>  
  
 <span data-ttu-id="002f8-156">此示例的目标工作负荷是销售订单处理，我们还考虑在其中包含产品和折扣信息。</span><span class="sxs-lookup"><span data-stu-id="002f8-156">The target workload for this sample is sales order processing, where we consider also information about products and discounts.</span></span> <span data-ttu-id="002f8-157">为此，创建了表 SalesOrderHeader、SalesOrderDetail、Product、SpecialOffer 和 SpecialOfferProduct。</span><span class="sxs-lookup"><span data-stu-id="002f8-157">To this end, the table SalesOrderHeader, SalesOrderDetail, Product, SpecialOffer, and SpecialOfferProduct.</span></span>  
  
 <span data-ttu-id="002f8-158">两个新存储过程 Sales.usp_InsertSalesOrder_inmem 和 Sales.usp_UpdateSalesOrderShipInfo_inmem 用于插入销售订单和更新给定销售订单的发货信息。</span><span class="sxs-lookup"><span data-stu-id="002f8-158">Two new stored procedures, Sales.usp_InsertSalesOrder_inmem and Sales.usp_UpdateSalesOrderShipInfo_inmem, are used to insert sales orders and to update the shipping information of a given sales order.</span></span>  
  
 <span data-ttu-id="002f8-159">新架构“Demo”包含用于执行演示工作负荷的帮助器表和存储过程。</span><span class="sxs-lookup"><span data-stu-id="002f8-159">The new schema 'Demo' contains helper tables and stored procedures to execute a demo workload.</span></span>  
  
 <span data-ttu-id="002f8-160">具体而言， [!INCLUDE[hek_2](../includes/hek-2-md.md)] 示例向 AdventureWorks 添加以下对象：</span><span class="sxs-lookup"><span data-stu-id="002f8-160">Concretely, the [!INCLUDE[hek_2](../includes/hek-2-md.md)] sample adds the following objects to AdventureWorks:</span></span>  
  
### <a name="tables-added-by-the-sample"></a><span data-ttu-id="002f8-161">示例添加的表</span><span class="sxs-lookup"><span data-stu-id="002f8-161">Tables added by the sample</span></span>  
  
#### <a name="the-new-tables"></a><span data-ttu-id="002f8-162">新表</span><span class="sxs-lookup"><span data-stu-id="002f8-162">The New Tables</span></span>  
 <span data-ttu-id="002f8-163">Sales.SalesOrderHeader_inmem</span><span class="sxs-lookup"><span data-stu-id="002f8-163">Sales.SalesOrderHeader_inmem</span></span>  
  
-   <span data-ttu-id="002f8-164">有关销售订单的表头信息。</span><span class="sxs-lookup"><span data-stu-id="002f8-164">Header information about sales orders.</span></span> <span data-ttu-id="002f8-165">每个销售订单都在此表中有对应的一行。</span><span class="sxs-lookup"><span data-stu-id="002f8-165">Each sales order has one row in this table.</span></span>  
  
 <span data-ttu-id="002f8-166">Sales.SalesOrderDetail_inmem</span><span class="sxs-lookup"><span data-stu-id="002f8-166">Sales.SalesOrderDetail_inmem</span></span>  
  
-   <span data-ttu-id="002f8-167">销售订单的详细信息。</span><span class="sxs-lookup"><span data-stu-id="002f8-167">Details of sales orders.</span></span> <span data-ttu-id="002f8-168">销售订单的每个行项都在此表中有对应的一行。</span><span class="sxs-lookup"><span data-stu-id="002f8-168">Each line item of a sales order has one row in this table.</span></span>  
  
 <span data-ttu-id="002f8-169">Sales.SpecialOffer_inmem</span><span class="sxs-lookup"><span data-stu-id="002f8-169">Sales.SpecialOffer_inmem</span></span>  
  
-   <span data-ttu-id="002f8-170">有关特价商品的信息，包括与每个特价商品关联的折扣百分比。</span><span class="sxs-lookup"><span data-stu-id="002f8-170">Information about special offers, including the discount percentage associated with each special offer.</span></span>  
  
 <span data-ttu-id="002f8-171">Sales.SpecialOfferProduct_inmem</span><span class="sxs-lookup"><span data-stu-id="002f8-171">Sales.SpecialOfferProduct_inmem</span></span>  
  
-   <span data-ttu-id="002f8-172">特价商品与产品之间的引用表。</span><span class="sxs-lookup"><span data-stu-id="002f8-172">Reference table between special offers and products.</span></span> <span data-ttu-id="002f8-173">每个特价商品可以包含零个或多个产品，每个产品可以包含在零个或多个特价商品中。</span><span class="sxs-lookup"><span data-stu-id="002f8-173">Each special offer can feature zero or more products, and each product can be featured in zero or more special offers.</span></span>  
  
 <span data-ttu-id="002f8-174">Production.Product_inmem</span><span class="sxs-lookup"><span data-stu-id="002f8-174">Production.Product_inmem</span></span>  
  
-   <span data-ttu-id="002f8-175">有关产品的信息，包括其标价。</span><span class="sxs-lookup"><span data-stu-id="002f8-175">Information about products, including their list price.</span></span>  
  
 <span data-ttu-id="002f8-176">Demo.DemoSalesOrderDetailSeed</span><span class="sxs-lookup"><span data-stu-id="002f8-176">Demo.DemoSalesOrderDetailSeed</span></span>  
  
-   <span data-ttu-id="002f8-177">在演示工作负荷中用于构造示例销售订单。</span><span class="sxs-lookup"><span data-stu-id="002f8-177">Used in the demo workload to construct sample sales orders.</span></span>  
  
 <span data-ttu-id="002f8-178">表的基于磁盘的变体：</span><span class="sxs-lookup"><span data-stu-id="002f8-178">Disk-based variations of the tables:</span></span>  
  
-   <span data-ttu-id="002f8-179">Sales.SalesOrderHeader_ondisk</span><span class="sxs-lookup"><span data-stu-id="002f8-179">Sales.SalesOrderHeader_ondisk</span></span>  
  
-   <span data-ttu-id="002f8-180">Sales.SalesOrderDetail_ondisk</span><span class="sxs-lookup"><span data-stu-id="002f8-180">Sales.SalesOrderDetail_ondisk</span></span>  
  
-   <span data-ttu-id="002f8-181">Sales.SpecialOffer_ondisk</span><span class="sxs-lookup"><span data-stu-id="002f8-181">Sales.SpecialOffer_ondisk</span></span>  
  
-   <span data-ttu-id="002f8-182">Sales.SpecialOfferProduct_ondisk</span><span class="sxs-lookup"><span data-stu-id="002f8-182">Sales.SpecialOfferProduct_ondisk</span></span>  
  
-   <span data-ttu-id="002f8-183">Production.Product_ondisk</span><span class="sxs-lookup"><span data-stu-id="002f8-183">Production.Product_ondisk</span></span>  
  
#### <a name="differences-between-original-disk-based-and-the-and-new-memory-optimized-tables"></a><span data-ttu-id="002f8-184">原始基于磁盘的表与新内存优化表之间的区别</span><span class="sxs-lookup"><span data-stu-id="002f8-184">Differences between original disk-based and the and new memory-optimized tables</span></span>  
 <span data-ttu-id="002f8-185">在很大程度上，此示例引入的新表使用的列和数据类型与原始表相同。</span><span class="sxs-lookup"><span data-stu-id="002f8-185">For the most part, the new tables introduced by this sample use the same columns and the same data types as the original tables.</span></span> <span data-ttu-id="002f8-186">但二者之间存在一些区别。</span><span class="sxs-lookup"><span data-stu-id="002f8-186">However, there are a few differences.</span></span> <span data-ttu-id="002f8-187">下面列出了区别以及更改的理由。</span><span class="sxs-lookup"><span data-stu-id="002f8-187">We list the differences below, along with a rationale for the changes.</span></span>  
  
 <span data-ttu-id="002f8-188">Sales.SalesOrderHeader_inmem</span><span class="sxs-lookup"><span data-stu-id="002f8-188">Sales.SalesOrderHeader_inmem</span></span>  
  
-   <span data-ttu-id="002f8-189">内存优化表支持*默认约束* ，大多数默认约束按原样迁移。</span><span class="sxs-lookup"><span data-stu-id="002f8-189">*Default constraints* are supported for memory-optimized tables, and most default constraints we migrated as is.</span></span> <span data-ttu-id="002f8-190">但是，原始表 Sales.SalesOrderHeader 包含两个为列 OrderDate 和 ModifiedDate 检索当前日期的默认约束。</span><span class="sxs-lookup"><span data-stu-id="002f8-190">However, the original table Sales.SalesOrderHeader contains two default constraints that retrieve the current date, for the columns OrderDate and ModifiedDate.</span></span> <span data-ttu-id="002f8-191">在具有大量并发的高吞吐量订单处理工作负荷中，任何全局资源都可能成为争用点。</span><span class="sxs-lookup"><span data-stu-id="002f8-191">In a high throughput order processing workload with a lot of concurrency, any global resource can become a point of contention.</span></span> <span data-ttu-id="002f8-192">系统时间就是全局资源，我们观察到，它可能在运行插入销售订单的 [!INCLUDE[hek_2](../includes/hek-2-md.md)] 工作负荷时成为瓶颈，特别是如果需要为销售订单表头中的多列以及销售订单详细信息检索系统时间。</span><span class="sxs-lookup"><span data-stu-id="002f8-192">System time is such a global resource, and we have observed that it can become a bottleneck when running an [!INCLUDE[hek_2](../includes/hek-2-md.md)] workload that inserts sales orders, in particular if the system time needs to be retrieved for multiple columns in the sales order header, as well as the sales order details.</span></span> <span data-ttu-id="002f8-193">此示例中解决问题的方式是仅为插入的每个销售订单检索系统时间一次，然后将该值用于 SalesOrderHeader_inmem 和 SalesOrderDetail_inmem 中的 datetime 列以及存储过程 Sales.usp_InsertSalesOrder_inmem。</span><span class="sxs-lookup"><span data-stu-id="002f8-193">The problem is addressed in this sample by retrieving the system time only once for each sales order that is inserted, and use that value for the datetime columns in SalesOrderHeader_inmem and SalesOrderDetail_inmem, in the stored procedure Sales.usp_InsertSalesOrder_inmem.</span></span>  
  
-   <span data-ttu-id="002f8-194">*别名 UDT* - 原始表将两个别名用户定义数据类型 (UDT) dbo.OrderNumber 和 dbo.AccountNumber 分别用于列 PurchaseOrderNumber 和 AccountNumber。</span><span class="sxs-lookup"><span data-stu-id="002f8-194">*Alias UDTs* - The original table uses two alias user-defined data types (UDTs) dbo.OrderNumber and dbo.AccountNumber, for the columns PurchaseOrderNumber and AccountNumber, respectively.</span></span> [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] <span data-ttu-id="002f8-195">在内存优化表中不支持别名 UDT，因而新表分别使用系统数据类型 nvarchar(25) 和 nvarchar(15)。</span><span class="sxs-lookup"><span data-stu-id="002f8-195">does not support alias UDT for memory-optimized tables, thus the new tables use system data types nvarchar(25) and nvarchar(15), respectively.</span></span>  
  
-   <span data-ttu-id="002f8-196">*索引键中可以为 Null 的列* - 在原始表中，列 SalesPersonID 可以为 Null，而在新表中，该列不可为 Null，并且默认约束值为 -1。</span><span class="sxs-lookup"><span data-stu-id="002f8-196">*Nullable columns in index keys* - In the original table, the column SalesPersonID is nullable, while in the new tables the column is not nullable and has a default constraint with value (-1).</span></span> <span data-ttu-id="002f8-197">这是因为内存优化表中的索引不能在索引键中具有可以为 Null 的列；-1 是这种情况下 NULL 的代理项。</span><span class="sxs-lookup"><span data-stu-id="002f8-197">This is because indexes on memory-optimized tables cannot have nullable columns in the index key; -1 is a surrogate for NULL in this case.</span></span>  
  
-   <span data-ttu-id="002f8-198">计算列 - 省略了计算列 SalesOrderNumber 和 TotalDue，因为 [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] 在内存优化表中不支持计算列。</span><span class="sxs-lookup"><span data-stu-id="002f8-198">*Computed columns* - The computed columns SalesOrderNumber and TotalDue are omitted, as [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] does not support computed columns in memory-optimized tables.</span></span> <span data-ttu-id="002f8-199">新视图 Sales.vSalesOrderHeader_extended_inmem 反映了列 SalesOrderNumber and TotalDue。</span><span class="sxs-lookup"><span data-stu-id="002f8-199">The new view Sales.vSalesOrderHeader_extended_inmem reflects the columns SalesOrderNumber and TotalDue.</span></span> <span data-ttu-id="002f8-200">因此，如果需要这些列，可以使用此视图。</span><span class="sxs-lookup"><span data-stu-id="002f8-200">Therefore, you can use this view if these columns are needed.</span></span>  
  
-   <span data-ttu-id="002f8-201">在*中，内存优化表不支持* 外键约束 [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="002f8-201">*Foreign key constraints* are not supported for memory-optimized tables in [!INCLUDE[ssSQL14](../includes/sssql14-md.md)].</span></span> <span data-ttu-id="002f8-202">此外，SalesOrderHeader_inmem 是示例工作负荷中的热表，并且外键约束需要对所有 DML 操作进行附加处理，因为它需要在这些约束引用的所有其他表中进行查找。</span><span class="sxs-lookup"><span data-stu-id="002f8-202">In addition, SalesOrderHeader_inmem is a hot table in the example workload, and foreign keys constraints require additional processing for all DML operations, as it requires lookups in all the other tables referenced in these constraints.</span></span> <span data-ttu-id="002f8-203">因此，假设应用程序可确保引用完整性，从而在插入行时不验证引用完整性。</span><span class="sxs-lookup"><span data-stu-id="002f8-203">Therefore, the assumption is that the app ensures referential integrity, and referential integrity is not validated when rows are inserted.</span></span> <span data-ttu-id="002f8-204">可以使用以下脚本，通过存储过程 dbo.usp_ValidateIntegrity 验证此表中数据的引用完整性：</span><span class="sxs-lookup"><span data-stu-id="002f8-204">Referential integrity for the data in this table can be verified using the stored procedure dbo.usp_ValidateIntegrity, using the following script:</span></span>  
  
    ```  
    DECLARE @o int = object_id(N'Sales.SalesOrderHeader_inmem')  
    EXEC dbo.usp_ValidateIntegrity @o  
    ```  
  
-   <span data-ttu-id="002f8-205">在 SQL Server 2014 中，内存优化表不支持*检查约束* 。</span><span class="sxs-lookup"><span data-stu-id="002f8-205">*Check constraints* are not supported for memory-optimized tables in SQ Server 2014.</span></span> <span data-ttu-id="002f8-206">使用以下脚本可随引用完整性一起验证域完整性：</span><span class="sxs-lookup"><span data-stu-id="002f8-206">Domain integrity is validated along with referential integrity using this script:</span></span>  
  
    ```  
    DECLARE @o int = object_id(N'Sales.SalesOrderHeader_inmem')  
    EXEC dbo.usp_ValidateIntegrity @o  
    ```  
  
-   <span data-ttu-id="002f8-207">*Rowguid* - 省略了 rowguid 列。</span><span class="sxs-lookup"><span data-stu-id="002f8-207">*Rowguid* - The rowguid column is omitted.</span></span> <span data-ttu-id="002f8-208">虽然内存优化表支持 uniqueidentifier，但是 [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]中不支持选项 ROWGUIDCOL。</span><span class="sxs-lookup"><span data-stu-id="002f8-208">While uniqueidentifier is support for memory-optimized tables, the option ROWGUIDCOL is not supported in [!INCLUDE[ssSQL14](../includes/sssql14-md.md)].</span></span> <span data-ttu-id="002f8-209">这种列通常用于合并复制或具有文件流列的表。</span><span class="sxs-lookup"><span data-stu-id="002f8-209">Columns of this kind are typically used for either merge replication or tables that have filestream columns.</span></span> <span data-ttu-id="002f8-210">此示例不包括其中任何一种。</span><span class="sxs-lookup"><span data-stu-id="002f8-210">This sample includes neither.</span></span>  
  
 <span data-ttu-id="002f8-211">Sales.SalesOrderDetail</span><span class="sxs-lookup"><span data-stu-id="002f8-211">Sales.SalesOrderDetail</span></span>  
  
-   <span data-ttu-id="002f8-212">*默认约束* - 类似于 SalesOrderHeader，未迁移需要系统时间/时间的默认约束，而是由插入销售订单的存储过程负责在第一次插入时插入当前系统日期/时间。</span><span class="sxs-lookup"><span data-stu-id="002f8-212">*Default constraints* - similar to SalesOrderHeader, the default constraint requiring the system date/time is not migrated, instead the stored procedure inserting sales orders takes care of inserting the current system date/time on first insert.</span></span>  
  
-   <span data-ttu-id="002f8-213">*计算列* - 在 [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] 中，内存优化表不支持未作为计算列迁移的计算列 LineTotal。</span><span class="sxs-lookup"><span data-stu-id="002f8-213">*Computed columns* - the computed column LineTotal was not migrated as computed columns are not supported with memory-optimized tables in [!INCLUDE[ssSQL14](../includes/sssql14-md.md)].</span></span> <span data-ttu-id="002f8-214">若要访问此列，请使用视图 Sales.vSalesOrderDetail_extended_inmem。</span><span class="sxs-lookup"><span data-stu-id="002f8-214">To access this column use the view Sales.vSalesOrderDetail_extended_inmem.</span></span>  
  
-   <span data-ttu-id="002f8-215">*Rowguid* - 省略了 rowguid 列。</span><span class="sxs-lookup"><span data-stu-id="002f8-215">*Rowguid* - The rowguid column is omitted.</span></span> <span data-ttu-id="002f8-216">有关详细信息，请参见表 SalesOrderHeader 的说明。</span><span class="sxs-lookup"><span data-stu-id="002f8-216">For details see the description for the table SalesOrderHeader.</span></span>  
  
-   <span data-ttu-id="002f8-217">对于 *检查* 和 *外键* 约束，请参见 SalesOrderHeader 的说明。</span><span class="sxs-lookup"><span data-stu-id="002f8-217">For *check* and *foreign key* constraints see the description of SalesOrderHeader.</span></span> <span data-ttu-id="002f8-218">以下脚本可用于验证此表的域和引用完整性：</span><span class="sxs-lookup"><span data-stu-id="002f8-218">The following script can be used to verify domain and referential integrity for this table:</span></span>  
  
    ```  
    DECLARE @o int = object_id(N'Sales.SalesOrderHeader_inmem')  
    EXEC dbo.usp_ValidateIntegrity @o  
    ```  
  
 <span data-ttu-id="002f8-219">Production.Product</span><span class="sxs-lookup"><span data-stu-id="002f8-219">Production.Product</span></span>  
  
-   <span data-ttu-id="002f8-220">*别名 UDT* - 原始表使用等效于系统数据类型位的用户定义数据类型 dbo.Flag。</span><span class="sxs-lookup"><span data-stu-id="002f8-220">*Alias UDTs* - the original table uses the user-defined data type dbo.Flag, which is equivalent to the system data type bit.</span></span> <span data-ttu-id="002f8-221">迁移的表改用位数据类型。</span><span class="sxs-lookup"><span data-stu-id="002f8-221">The migrated table uses the bit data type instead.</span></span>  
  
-   <span data-ttu-id="002f8-222">*BIN2 排序规则*-列 Name 和 ProductNumber 包含在索引键中，因此必须在中具有 BIN2 排序规则 [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="002f8-222">*BIN2 collation* - The columns Name and ProductNumber are included in index keys, and must thus have BIN2 collations in [!INCLUDE[ssSQL14](../includes/sssql14-md.md)].</span></span> <span data-ttu-id="002f8-223">这里假设应用程序不依赖于排序规则具体内容（如区分大小写）。</span><span class="sxs-lookup"><span data-stu-id="002f8-223">Here, the assumption is that the app does not rely on collation specifics, like case insensitivity.</span></span>  
  
-   <span data-ttu-id="002f8-224">*Rowguid* - 省略了 rowguid 列。</span><span class="sxs-lookup"><span data-stu-id="002f8-224">*Rowguid* - The rowguid column is omitted.</span></span> <span data-ttu-id="002f8-225">有关详细信息，请参见表 SalesOrderHeader 的说明。</span><span class="sxs-lookup"><span data-stu-id="002f8-225">For details see the description for the table SalesOrderHeader.</span></span>  
  
-   <span data-ttu-id="002f8-226">*唯一*、 *检查* 和 *外键约束* 通过两种方式实现：存储过程 Product.usp_InsertProduct_inmem 和 Product.usp_DeleteProduct_inmem 可以用于插入和删除产品；这些过程验证域和引用完整性，在违反完整性时会失败。</span><span class="sxs-lookup"><span data-stu-id="002f8-226">*Unique*, *Check* and *Foreign Key constraints* are accounted for in two ways: the stored procedures Product.usp_InsertProduct_inmem and Product.usp_DeleteProduct_inmem can be used to insert and delete products; these procedures validate domain and referential integrity, and will fail if integrity is violated.</span></span> <span data-ttu-id="002f8-227">此外，以下脚本还可用于按原样验证域和引用完整性：</span><span class="sxs-lookup"><span data-stu-id="002f8-227">In addition, the follow script can be used to validate domain and referential integrity as is:</span></span>  
  
    ```  
    DECLARE @o int = object_id(N'Production.Product')  
    EXEC dbo.usp_ValidateIntegrity @o  
    ```  
  
    -   <span data-ttu-id="002f8-228">请注意，存储过程 usp_InsertProduct_inmem 和 usp_DeleteProduct_inmem 仅考虑迁移的表之间的外键。</span><span class="sxs-lookup"><span data-stu-id="002f8-228">Note that the store procedures usp_InsertProduct_inmem and usp_DeleteProduct_inmem consider only foreign keys between the migrated tables.</span></span> <span data-ttu-id="002f8-229">不考虑对其他表 ProductModel、ProductSubcategory 和 UnitMeasure 的引用。</span><span class="sxs-lookup"><span data-stu-id="002f8-229">References to other tables ProductModel, ProductSubcategory, and UnitMeasure are not considered.</span></span>  
  
 <span data-ttu-id="002f8-230">Sales.SpecialOffer</span><span class="sxs-lookup"><span data-stu-id="002f8-230">Sales.SpecialOffer</span></span>  
  
-   <span data-ttu-id="002f8-231">*检查* 和 *外键约束* 通过两种方式实现：存储过程 Sales.usp_InsertSpecialOffer_inmem 和 Sales.usp_DeleteSpecialOffer_inmem 可用于插入和删除特价商品；这些过程验证域和引用完整性，在违反完整性时会失败。</span><span class="sxs-lookup"><span data-stu-id="002f8-231">*Check* and *Foreign Key constraints* are accounted for in two ways: the stored procedures Sales.usp_InsertSpecialOffer_inmem and Sales.usp_DeleteSpecialOffer_inmem can be used to insert and delete special offers; these procedures validate domain and referential integrity, and will fail if integrity is violated.</span></span> <span data-ttu-id="002f8-232">此外，以下脚本还可用于按原样验证域和引用完整性：</span><span class="sxs-lookup"><span data-stu-id="002f8-232">In addition, the follow script can be used to validate domain and referential integrity as is:</span></span>  
  
    ```  
    DECLARE @o int = object_id(N'Sales.SpecialOffer_inmem')  
    EXEC dbo.usp_ValidateIntegrity @o  
    ```  
  
-   <span data-ttu-id="002f8-233">*Rowguid* - 省略了 rowguid 列。</span><span class="sxs-lookup"><span data-stu-id="002f8-233">*Rowguid* - The rowguid column is omitted.</span></span> <span data-ttu-id="002f8-234">有关详细信息，请参见表 SalesOrderHeader 的说明。</span><span class="sxs-lookup"><span data-stu-id="002f8-234">For details see the description for the table SalesOrderHeader.</span></span>  
  
 <span data-ttu-id="002f8-235">Sales.SpecialOfferProduct</span><span class="sxs-lookup"><span data-stu-id="002f8-235">Sales.SpecialOfferProduct</span></span>  
  
-   <span data-ttu-id="002f8-236">*外键约束* 通过两种方式实现：存储过程 Sales.usp_InsertSpecialOfferProduct_inmem 可用于插入和删除特价商品与产品之间的关系；此过程验证引用完整性，在违反完整性时会失败。</span><span class="sxs-lookup"><span data-stu-id="002f8-236">*Foreign Key constraints* are accounted for in two ways: the stored procedure Sales.usp_InsertSpecialOfferProduct_inmem can be used to insert relationships between special offers and products; this procedures validates referential integrity, and will fail if integrity is violated.</span></span> <span data-ttu-id="002f8-237">此外，以下脚本还可用于按原样验证引用完整性：</span><span class="sxs-lookup"><span data-stu-id="002f8-237">In addition, the follow script can be used to validate referential integrity as is:</span></span>  
  
    ```  
    DECLARE @o int = object_id(N'Sales.SpecialOfferProduct_inmem')  
    EXEC dbo.usp_ValidateIntegrity @o  
    ```  
  
-   <span data-ttu-id="002f8-238">*Rowguid* - 省略了 rowguid 列。</span><span class="sxs-lookup"><span data-stu-id="002f8-238">*Rowguid* - The rowguid column is omitted.</span></span> <span data-ttu-id="002f8-239">有关详细信息，请参见表 SalesOrderHeader 的说明。</span><span class="sxs-lookup"><span data-stu-id="002f8-239">For details see the description for the table SalesOrderHeader.</span></span>  
  
#### <a name="considerations-for-indexes-on-memory-optimized-tables"></a><span data-ttu-id="002f8-240">有关内存优化表的索引的注意事项</span><span class="sxs-lookup"><span data-stu-id="002f8-240">Considerations for indexes on memory-optimized tables</span></span>  
 <span data-ttu-id="002f8-241">内存优化表的基线索引是 NONCLUSTERED 索引，该索引支持点查找（采用相等谓词的索引查找）、范围扫描（采用不相等谓词的索引查找）、全文索引扫描和有序扫描。</span><span class="sxs-lookup"><span data-stu-id="002f8-241">The baseline index for memory-optimized tables is the NONCLUSTERED index, which supports point lookups (index seek on equality predicate), range scans (index seek in inequality predicate), full index scans, and ordered scans.</span></span> <span data-ttu-id="002f8-242">此外，NONCLUSTERED 索引还支持对索引键的前导列进行搜索。</span><span class="sxs-lookup"><span data-stu-id="002f8-242">In addition, NONCLUSTERED indexes support searching on leading columns of the index key.</span></span> <span data-ttu-id="002f8-243">事实上，内存优化 NONCLUSTERED 索引支持基于磁盘的 NONCLUSTERED 索引支持的所有操作，唯一的例外是向后扫描。</span><span class="sxs-lookup"><span data-stu-id="002f8-243">In fact memory-optimized NONCLUSTERED indexes support all the operations supported by disk-based NONCLUSTERED indexes, with the only exception being backward scans.</span></span> <span data-ttu-id="002f8-244">因此，使用 NONCLUSTERED 索引是针对索引的安全选择。</span><span class="sxs-lookup"><span data-stu-id="002f8-244">Therefore, using NONCLUSTERED indexes is a safe choice for your indexes.</span></span>  
  
 <span data-ttu-id="002f8-245">HASH 索引可用于进一步优化工作负荷。</span><span class="sxs-lookup"><span data-stu-id="002f8-245">HASH indexes are can be used to further optimize the workload.</span></span> <span data-ttu-id="002f8-246">这些索引特别针对点查找和行插入进行了优化。</span><span class="sxs-lookup"><span data-stu-id="002f8-246">They are particularly optimized for point lookups and row inserts.</span></span> <span data-ttu-id="002f8-247">但是，必须考虑到这些索引不支持范围扫描、有序扫描或是对前导索引键列进行的搜索。</span><span class="sxs-lookup"><span data-stu-id="002f8-247">However, one must consider that they do not support range scans, ordered scans, or search on leading index key columns.</span></span> <span data-ttu-id="002f8-248">因此，使用这些索引时需要谨慎。</span><span class="sxs-lookup"><span data-stu-id="002f8-248">Therefore, care needs to be taken when using these indexes.</span></span> <span data-ttu-id="002f8-249">此外，还需要在创建时指定 bucket_count。</span><span class="sxs-lookup"><span data-stu-id="002f8-249">In addition, it is necessary to specify the bucket_count at create time.</span></span> <span data-ttu-id="002f8-250">它通常应设置为索引键值的一到二倍之间，不过估计过高通常不是什么问题。</span><span class="sxs-lookup"><span data-stu-id="002f8-250">It should usually be set at between one and two times the number of index key values, but overestimating is usually not a problem.</span></span>  
  
 <span data-ttu-id="002f8-251">有关 [索引指南](https://technet.microsoft.com/library/dn133166\(v=sql.120\).aspx) 和 [选择正确 bucket_count](https://technet.microsoft.com/library/dn494956\(v=sql.120\).aspx)的指南的详细信息，请参阅联机丛书。</span><span class="sxs-lookup"><span data-stu-id="002f8-251">See Books Online for more details about [index guidelines](https://technet.microsoft.com/library/dn133166\(v=sql.120\).aspx) and guidelines for [choosing the right bucket_count](https://technet.microsoft.com/library/dn494956\(v=sql.120\).aspx).</span></span>  
  
 <span data-ttu-id="002f8-252">迁移的表中的索引针对演示销售订单处理工作负荷进行了优化。</span><span class="sxs-lookup"><span data-stu-id="002f8-252">The indexes on the migrated tables have been tuned for the demo sales order processing workload.</span></span> <span data-ttu-id="002f8-253">该工作负荷依赖于表 Sales.SalesOrderHeader_inmem 和 Sales.SalesOrderDetail_inmem 中的插入和点查找，还依赖于对表 Production.Product_inmem 和 Sales.SpecialOffer_inmem 中的主键列进行的点查找。</span><span class="sxs-lookup"><span data-stu-id="002f8-253">The workload relies on inserts and point lookups in the tables Sales.SalesOrderHeader_inmem and Sales.SalesOrderDetail_inmem, and it also relies on point lookups on the primary key columns in the tables Production.Product_inmem and Sales.SpecialOffer_inmem.</span></span>  
  
 <span data-ttu-id="002f8-254">Sales.SalesOrderHeader_inmem 有三个索引，因为性能原因，而且工作负荷无需有序或范围扫描，所以这些索引都是 HASH 索引。</span><span class="sxs-lookup"><span data-stu-id="002f8-254">Sales.SalesOrderHeader_inmem has three indexes, which are all HASH indexes for performance reasons, and because no ordered or range scans are needed for the workload.</span></span>  
  
-   <span data-ttu-id="002f8-255">(SalesOrderID) 上的 HASH 索引：bucket_count 大小为 1000 万（向上舍入为 1600 万），因为预期销售订单数为 1000 万</span><span class="sxs-lookup"><span data-stu-id="002f8-255">HASH index on (SalesOrderID): bucket_count is sized at 10 million (rounded up to 16 million), because the expected number of sales orders is 10 million</span></span>  
  
-   <span data-ttu-id="002f8-256">(SalesPersonID) 上的 HASH 索引：bucket_count 为 1000 万。</span><span class="sxs-lookup"><span data-stu-id="002f8-256">HASH index on (SalesPersonID): bucket_count is 1 million.</span></span> <span data-ttu-id="002f8-257">提供的数据集不包含许多销售人员，但是允许将来增加，并且不会因 bucket_count 过大而影响点查找性能。</span><span class="sxs-lookup"><span data-stu-id="002f8-257">The data set provided does not have a lot of sales persons, but this allows for future growth, plus you don't pay a performance penalty for point lookups if the bucket_count is oversized.</span></span>  
  
-   <span data-ttu-id="002f8-258">(CustomerID) 上的 HASH 索引：bucket_count 为 1 万。</span><span class="sxs-lookup"><span data-stu-id="002f8-258">HASH index on (CustomerID): bucket_count is 1 million.</span></span> <span data-ttu-id="002f8-259">提供的数据集不包含许多客户，但是允许将来增加。</span><span class="sxs-lookup"><span data-stu-id="002f8-259">The data set provided does not have a lot of customers, but this allows for future growth.</span></span>  
  
 <span data-ttu-id="002f8-260">Sales.SalesOrderDetail_inmem 有三个索引，因为性能原因，而且工作负荷无需有序或范围扫描，所以这些索引都是 HASH 索引。</span><span class="sxs-lookup"><span data-stu-id="002f8-260">Sales.SalesOrderDetail_inmem has three indexes, which are all HASH indexes for performance reasons, and because no ordered or range scans are needed for the workload.</span></span>  
  
-   <span data-ttu-id="002f8-261">(SalesOrderID, SalesOrderDetailID) 上的 HASH 索引：这是主键索引，即使不会经常对 (SalesOrderID, SalesOrderDetailID) 进行查找，将哈希索引用于该键也可加快行插入速度。</span><span class="sxs-lookup"><span data-stu-id="002f8-261">HASH index on (SalesOrderID, SalesOrderDetailID): this is the primary key index, and even though lookups on (SalesOrderID, SalesOrderDetailID) will be infrequent, using a hash index for the key speeds up row inserts.</span></span> <span data-ttu-id="002f8-262">bucket_count 大小为 5000 万（向上舍入为 6700 万）：预期销售订单数为 1000 万，这是针对平均每个订单 5 个项目确定的大小</span><span class="sxs-lookup"><span data-stu-id="002f8-262">The bucket_count is sized at 50 million (rounded up to 67 million): the expected number of sales orders is 10 million, and this is sized to have an average of 5 items per order</span></span>  
  
-   <span data-ttu-id="002f8-263">(SalesOrderID) 上的 HASH 索引：经常按销售订单进行查找：您要查找对应于单个订单的所有行项。</span><span class="sxs-lookup"><span data-stu-id="002f8-263">HASH index on (SalesOrderID): lookups by sales order are frequent: you will want to find all the line items corresponding to a single order.</span></span>  <span data-ttu-id="002f8-264">bucket_count 大小为 1000 万（向上舍入为 1600 万），因为预期销售订单数为 1000 万</span><span class="sxs-lookup"><span data-stu-id="002f8-264">bucket_count is sized at 10 million (rounded up to 16 million), because the expected number of sales orders is 10 million</span></span>  
  
-   <span data-ttu-id="002f8-265">(ProductID) 上的 HASH 索引：bucket_count 为 1 万。</span><span class="sxs-lookup"><span data-stu-id="002f8-265">HASH index on (ProductID): bucket_count is 1 million.</span></span> <span data-ttu-id="002f8-266">提供的数据集不包含许多产品，但是允许将来增加。</span><span class="sxs-lookup"><span data-stu-id="002f8-266">The data set provided does not have a lot of product, but this allows for future growth.</span></span>  
  
 <span data-ttu-id="002f8-267">Production.Product_inmem 有三个索引</span><span class="sxs-lookup"><span data-stu-id="002f8-267">Production.Product_inmem has three indexes</span></span>  
  
-   <span data-ttu-id="002f8-268">(ProductID) 上的 HASH 索引：对 ProductID 进行的查找是演示工作负荷的关键因素，因此这是哈希索引</span><span class="sxs-lookup"><span data-stu-id="002f8-268">HASH index on (ProductID): lookups on ProductID are in the critical path for the demo workload, therefore this is a hash index</span></span>  
  
-   <span data-ttu-id="002f8-269">(Name) 上的 NONCLUSTERED 索引：这允许进行产品名称的有序扫描</span><span class="sxs-lookup"><span data-stu-id="002f8-269">NONCLUSTERED index on (Name): this will allow ordered scans of product names</span></span>  
  
-   <span data-ttu-id="002f8-270">(ProductNumber) 上的 NONCLUSTERED 索引：这允许进行产品编号的有序扫描</span><span class="sxs-lookup"><span data-stu-id="002f8-270">NONCLUSTERED index on (ProductNumber): this will allow ordered scans of product numbers</span></span>  
  
 <span data-ttu-id="002f8-271">Sales.SpecialOffer_inmem 在 (SpecialOfferID) 上有一个 HASH 索引：对特价商品进行的点查找是演示工作负荷的关键因素。</span><span class="sxs-lookup"><span data-stu-id="002f8-271">Sales.SpecialOffer_inmem has one HASH index on (SpecialOfferID): point lookups of special offers are in the critical part of the demo workload.</span></span> <span data-ttu-id="002f8-272">bucket_count 大小为 100 万，允许将来增加。</span><span class="sxs-lookup"><span data-stu-id="002f8-272">The bucket_count is sized at 1 million to allow for future growth.</span></span>  
  
 <span data-ttu-id="002f8-273">Sales.SpecialOfferProduct_inmem 未在演示工作负荷中进行引用，因而表面上无需使用此表中的哈希索引优化工作负荷 - (SpecialOfferID, ProductID) 和 (ProductID) 上的索引是 NONCLUSTERED。</span><span class="sxs-lookup"><span data-stu-id="002f8-273">Sales.SpecialOfferProduct_inmem is not referenced in the demo workload, and thus there is no apparent need to use hash indexes on this table to optimize the workload - the indexes on (SpecialOfferID, ProductID) and (ProductID) are NONCLUSTERED.</span></span>  
  
 <span data-ttu-id="002f8-274">请注意，以上某些 bucket_count 过大，但是 SalesOrderHeader_inmem 和 SalesOrderDetail_inmem 上的索引的 bucket_count 并非如此：其大小仅用于 1000 万个销售订单。</span><span class="sxs-lookup"><span data-stu-id="002f8-274">Notice that in the above some of the bucket_counts are over-sized, but not the bucket_counts for the indexes on SalesOrderHeader_inmem and SalesOrderDetail_inmem: they are sized for just 10 million sales orders.</span></span> <span data-ttu-id="002f8-275">这样做是为了可以在内存可用性较低的系统上安装示例，不过在这些情况下，演示工作负荷会由于内存不足而失败。</span><span class="sxs-lookup"><span data-stu-id="002f8-275">This was done to allow installing the sample on systems with low memory availability, although in those cases the demo workload will fail with out-of-memory.</span></span> <span data-ttu-id="002f8-276">如果的确要扩展为远远超过 1000 万个销售订单，可以随意相应地提高桶计数。</span><span class="sxs-lookup"><span data-stu-id="002f8-276">If you do want to scale well beyond 10 million sales orders, feel free to increase the bucket counts accordingly.</span></span>  
  
#### <a name="considerations-for-memory-utilization"></a><span data-ttu-id="002f8-277">内存利用率注意事项</span><span class="sxs-lookup"><span data-stu-id="002f8-277">Considerations for memory utilization</span></span>  
 <span data-ttu-id="002f8-278">示例数据库中的内存利用率（运行演示工作负荷之前以及之后）在 [内存优化表的内存利用率](#Memoryutilizationforthememory-optimizedtables)一节中进行了讨论。</span><span class="sxs-lookup"><span data-stu-id="002f8-278">Memory utilization in the sample database, both before and after running the demo workload, is discussed in the Section [Memory utilization for the memory-optimized tables](#Memoryutilizationforthememory-optimizedtables).</span></span>  
  
### <a name="stored-procedures-added-by-the-sample"></a><span data-ttu-id="002f8-279">示例添加的存储过程</span><span class="sxs-lookup"><span data-stu-id="002f8-279">Stored Procedures added by the sample</span></span>  
 <span data-ttu-id="002f8-280">用于插入销售订单和更新发货详细信息的两个重要存储过程如下：</span><span class="sxs-lookup"><span data-stu-id="002f8-280">The two key stored procedures for inserting sales order and updating shipping details are as follows:</span></span>  
  
-   <span data-ttu-id="002f8-281">Sales.usp_InsertSalesOrder_inmem</span><span class="sxs-lookup"><span data-stu-id="002f8-281">Sales.usp_InsertSalesOrder_inmem</span></span>  
  
    -   <span data-ttu-id="002f8-282">在数据库中插入新销售订单并输出该销售订单的 SalesOrderID。</span><span class="sxs-lookup"><span data-stu-id="002f8-282">Inserts a new sales order in the database and outputs the SalesOrderID for that sales order.</span></span> <span data-ttu-id="002f8-283">它采用销售订单表头的详细信息以及订单中的行项作为输入参数。</span><span class="sxs-lookup"><span data-stu-id="002f8-283">As input parameters it takes details for the sales order header, as well as the line items in the order.</span></span>  
  
    -   <span data-ttu-id="002f8-284">输出参数：</span><span class="sxs-lookup"><span data-stu-id="002f8-284">Output parameter:</span></span>  
  
        -   <span data-ttu-id="002f8-285">@SalesOrderID int - 刚插入的销售订单的 SalesOrderID</span><span class="sxs-lookup"><span data-stu-id="002f8-285">@SalesOrderID int - the SalesOrderID for the sales order that was just inserted</span></span>  
  
    -   <span data-ttu-id="002f8-286">输入参数（必需）：</span><span class="sxs-lookup"><span data-stu-id="002f8-286">Input parameters (required):</span></span>  
  
        -   <span data-ttu-id="002f8-287">@DueDate datetime2</span><span class="sxs-lookup"><span data-stu-id="002f8-287">@DueDate datetime2</span></span>  
  
        -   <span data-ttu-id="002f8-288">@CustomerID int</span><span class="sxs-lookup"><span data-stu-id="002f8-288">@CustomerID int</span></span>  
  
        -   <span data-ttu-id="002f8-289">@BillToAddressID [int]</span><span class="sxs-lookup"><span data-stu-id="002f8-289">@BillToAddressID [int]</span></span>  
  
        -   <span data-ttu-id="002f8-290">@ShipToAddressID [int]</span><span class="sxs-lookup"><span data-stu-id="002f8-290">@ShipToAddressID [int]</span></span>  
  
        -   <span data-ttu-id="002f8-291">@ShipMethodID [int]</span><span class="sxs-lookup"><span data-stu-id="002f8-291">@ShipMethodID [int]</span></span>  
  
        -   <span data-ttu-id="002f8-292">@SalesOrderDetails Sales.SalesOrderDetailType_inmem - 包含订单行项的 TVP</span><span class="sxs-lookup"><span data-stu-id="002f8-292">@SalesOrderDetails Sales.SalesOrderDetailType_inmem - TVP that contains the line items of the order</span></span>  
  
    -   <span data-ttu-id="002f8-293">输入参数（可选）：</span><span class="sxs-lookup"><span data-stu-id="002f8-293">Input parameters (optional):</span></span>  
  
        -   <span data-ttu-id="002f8-294">@Status [tinyint]</span><span class="sxs-lookup"><span data-stu-id="002f8-294">@Status [tinyint]</span></span>  
  
        -   <span data-ttu-id="002f8-295">@OnlineOrderFlag [bit]</span><span class="sxs-lookup"><span data-stu-id="002f8-295">@OnlineOrderFlag [bit]</span></span>  
  
        -   <span data-ttu-id="002f8-296">@PurchaseOrderNumber [nvarchar](25\)</span><span class="sxs-lookup"><span data-stu-id="002f8-296">@PurchaseOrderNumber [nvarchar](25\)</span></span>  
  
        -   <span data-ttu-id="002f8-297">@AccountNumber [nvarchar](15\)</span><span class="sxs-lookup"><span data-stu-id="002f8-297">@AccountNumber [nvarchar](15\)</span></span>  
  
        -   <span data-ttu-id="002f8-298">@SalesPersonID [int]</span><span class="sxs-lookup"><span data-stu-id="002f8-298">@SalesPersonID [int]</span></span>  
  
        -   <span data-ttu-id="002f8-299">@TerritoryID [int]</span><span class="sxs-lookup"><span data-stu-id="002f8-299">@TerritoryID [int]</span></span>  
  
        -   <span data-ttu-id="002f8-300">@CreditCardID [int]</span><span class="sxs-lookup"><span data-stu-id="002f8-300">@CreditCardID [int]</span></span>  
  
        -   <span data-ttu-id="002f8-301">@CreditCardApprovalCode [varchar](15\)</span><span class="sxs-lookup"><span data-stu-id="002f8-301">@CreditCardApprovalCode [varchar](15\)</span></span>  
  
        -   <span data-ttu-id="002f8-302">@CurrencyRateID [int]</span><span class="sxs-lookup"><span data-stu-id="002f8-302">@CurrencyRateID [int]</span></span>  
  
        -   <span data-ttu-id="002f8-303">@Comment nvarchar(128)</span><span class="sxs-lookup"><span data-stu-id="002f8-303">@Comment nvarchar(128)</span></span>  
  
-   <span data-ttu-id="002f8-304">Sales.usp_UpdateSalesOrderShipInfo_inmem</span><span class="sxs-lookup"><span data-stu-id="002f8-304">Sales.usp_UpdateSalesOrderShipInfo_inmem</span></span>  
  
    -   <span data-ttu-id="002f8-305">更新给定销售订单的发货信息。</span><span class="sxs-lookup"><span data-stu-id="002f8-305">Update the shipping information for a given sales order.</span></span> <span data-ttu-id="002f8-306">这也会更新销售订单所有行项的发货信息。</span><span class="sxs-lookup"><span data-stu-id="002f8-306">This will also update the shipping information for all line items of the sales order.</span></span>  
  
    -   <span data-ttu-id="002f8-307">这是本机编译的存储过程 Sales.usp_UpdateSalesOrderShipInfo_native 的包装过程，其中的重试逻辑用于处理与更新该订单的并发事务形成的（意外）潜在冲突。</span><span class="sxs-lookup"><span data-stu-id="002f8-307">This is a wrapper procedure for the natively compiled stored procedures Sales.usp_UpdateSalesOrderShipInfo_native with retry logic to deal with (unexpected) potential conflicts with concurrent transactions updating the same order.</span></span> <span data-ttu-id="002f8-308">有关重试逻辑的更多信息，请参见 [此处](https://technet.microsoft.com/library/dn169141\(v=sql.120\).aspx)的联机丛书主题。</span><span class="sxs-lookup"><span data-stu-id="002f8-308">For more information about retry logic see the Books Online topic [here](https://technet.microsoft.com/library/dn169141\(v=sql.120\).aspx).</span></span>  
  
-   <span data-ttu-id="002f8-309">Sales.usp_UpdateSalesOrderShipInfo_native</span><span class="sxs-lookup"><span data-stu-id="002f8-309">Sales.usp_UpdateSalesOrderShipInfo_native</span></span>  
  
    -   <span data-ttu-id="002f8-310">这是实际处理发货信息更新的本机编译的存储过程。</span><span class="sxs-lookup"><span data-stu-id="002f8-310">This is the natively compiled stored procedure that actually processes the update to the shipping information.</span></span> <span data-ttu-id="002f8-311">它可以从包装存储过程 Sales.usp_UpdateSalesOrderShipInfo_inmem 进行调用。</span><span class="sxs-lookup"><span data-stu-id="002f8-311">It is means to be called from the wrapper stored procedure Sales.usp_UpdateSalesOrderShipInfo_inmem.</span></span> <span data-ttu-id="002f8-312">如果客户端可以处理失败并实现重试逻辑，则您可以直接调用此过程，而不是使用包装存储过程。</span><span class="sxs-lookup"><span data-stu-id="002f8-312">If the client can deal with failures and implements retry logic, you can call this procedure directly, rather than using the wrapper stored procedure.</span></span>  
  
 <span data-ttu-id="002f8-313">以下存储过程用于演示工作负荷。</span><span class="sxs-lookup"><span data-stu-id="002f8-313">The following stored procedure is used for the demo workload.</span></span>  
  
-   <span data-ttu-id="002f8-314">Demo.usp_DemoReset</span><span class="sxs-lookup"><span data-stu-id="002f8-314">Demo.usp_DemoReset</span></span>  
  
    -   <span data-ttu-id="002f8-315">通过清空 SalesOrderHeader 和 SalesOrderDetail 表并对这两个表重设种子来重置演示。</span><span class="sxs-lookup"><span data-stu-id="002f8-315">Resets the demo by emptying and reseeding the SalesOrderHeader and SalesOrderDetail tables.</span></span>  
  
 <span data-ttu-id="002f8-316">以下存储过程用于对内存优化表进行插入和删除，同时保证域和引用完整性。</span><span class="sxs-lookup"><span data-stu-id="002f8-316">The following stored procedures are used for inserting in and deleting from memory-optimized tables while guaranteeing domain and referential integrity.</span></span>  
  
-   <span data-ttu-id="002f8-317">Production.usp_InsertProduct_inmem</span><span class="sxs-lookup"><span data-stu-id="002f8-317">Production.usp_InsertProduct_inmem</span></span>  
  
-   <span data-ttu-id="002f8-318">Production.usp_DeleteProduct_inmem</span><span class="sxs-lookup"><span data-stu-id="002f8-318">Production.usp_DeleteProduct_inmem</span></span>  
  
-   <span data-ttu-id="002f8-319">Sales.usp_InsertSpecialOffer_inmem</span><span class="sxs-lookup"><span data-stu-id="002f8-319">Sales.usp_InsertSpecialOffer_inmem</span></span>  
  
-   <span data-ttu-id="002f8-320">Sales.usp_DeleteSpecialOffer_inmem</span><span class="sxs-lookup"><span data-stu-id="002f8-320">Sales.usp_DeleteSpecialOffer_inmem</span></span>  
  
-   <span data-ttu-id="002f8-321">Sales.usp_InsertSpecialOfferProduct_inmem</span><span class="sxs-lookup"><span data-stu-id="002f8-321">Sales.usp_InsertSpecialOfferProduct_inmem</span></span>  
  
 <span data-ttu-id="002f8-322">最后，以下存储过程用于验证域和引用完整性。</span><span class="sxs-lookup"><span data-stu-id="002f8-322">Finally the following stored procedure is used to verify domain and referential integrity.</span></span>  
  
1.  <span data-ttu-id="002f8-323">dbo.usp_ValidateIntegrity</span><span class="sxs-lookup"><span data-stu-id="002f8-323">dbo.usp_ValidateIntegrity</span></span>  
  
    -   <span data-ttu-id="002f8-324">可选参数：@object_id - 要验证其完整性的对象的 ID</span><span class="sxs-lookup"><span data-stu-id="002f8-324">Optional parameter: @object_id - ID of the object to validate integrity for</span></span>  
  
    -   <span data-ttu-id="002f8-325">此过程依赖于用于需要验证的完整性规则的表 dbo.DomainIntegrity、dbo.ReferentialIntegrity 和 dbo.UniqueIntegrity - 示例基于对 AdventureWorks 数据库中的原始表存在的检查、外键和唯一约束来填充这些表。</span><span class="sxs-lookup"><span data-stu-id="002f8-325">This procedure relies on the tables dbo.DomainIntegrity, dbo.ReferentialIntegrity, and dbo.UniqueIntegrity for the integrity rules that need to be verified - the sample populates these tables based on the check, foreign key, and unique constraints that exist for the original tables in the AdventureWorks database.</span></span>  
  
    -   <span data-ttu-id="002f8-326">它依赖于帮助器过程 dbo.usp_GenerateCKCheck、dbo.usp_GenerateFKCheck 和 dbo.GenerateUQCheck 来生成执行完整性检查所需的 T-SQL。</span><span class="sxs-lookup"><span data-stu-id="002f8-326">It relies on the helper procedures dbo.usp_GenerateCKCheck, dbo.usp_GenerateFKCheck, and dbo.GenerateUQCheck to generate the T-SQL needed for performing the integrity checks.</span></span>  
  
##  <a name="performance-measurements-using-the-demo-workload"></a><a name="PerformanceMeasurementsusingtheDemoWorkload"></a> <span data-ttu-id="002f8-327">使用演示工作负荷执行度量</span><span class="sxs-lookup"><span data-stu-id="002f8-327">Performance Measurements using the Demo Workload</span></span>  
 <span data-ttu-id="002f8-328">Ostress 是由 [!INCLUDE[msCoName](../includes/msconame-md.md)] CSS [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 支持团队开发的命令行工具。</span><span class="sxs-lookup"><span data-stu-id="002f8-328">Ostress is a command-line tool that was developed by the [!INCLUDE[msCoName](../includes/msconame-md.md)] CSS [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] support team.</span></span> <span data-ttu-id="002f8-329">此工具可以用于并行执行查询或运行存储过程。</span><span class="sxs-lookup"><span data-stu-id="002f8-329">This tool can be used to execute queries or run stored procedures in parallel.</span></span> <span data-ttu-id="002f8-330">可以配置线程数来并行运行给定 T-SQL 语句，并且可以指定应对此线程执行语句的次数；Ostress 会加快线程，对所有线程并行执行语句。</span><span class="sxs-lookup"><span data-stu-id="002f8-330">You can configure the number of threads to run a given T-SQL statement in parallel, and you can specify how many times the statement should be executed on this thread; ostress will spin up the threads and execute the statement on all threads in parallel.</span></span> <span data-ttu-id="002f8-331">对所有线程完成执行之后，Ostress 会报告所有线程完成执行所花费的时间。</span><span class="sxs-lookup"><span data-stu-id="002f8-331">After execution finishes for all threads, ostress will report the time taken for all threads to finish execution.</span></span>  
  
### <a name="installing-ostress"></a><span data-ttu-id="002f8-332">安装 Ostress</span><span class="sxs-lookup"><span data-stu-id="002f8-332">Installing ostress</span></span>  
 <span data-ttu-id="002f8-333">Ostress 作为 RML 实用工具的一部分进行安装；Ostress 没有独立安装。</span><span class="sxs-lookup"><span data-stu-id="002f8-333">Ostress is installed as part of the RML Utilities; there is no standalone installation for ostress.</span></span>  
  
 <span data-ttu-id="002f8-334">安装步骤：</span><span class="sxs-lookup"><span data-stu-id="002f8-334">Installation steps:</span></span>  
  
1.  <span data-ttu-id="002f8-335">从以下页面下载并运行 RML 实用工具的 x64 安装包：[https://blogs.msdn.com/b/psssql/archive/2013/10/29/cumulative-update-2-to-the-rml-utilities-for-microsoft-sql-server-released.aspx](https://blogs.msdn.com/b/psssql/archive/2013/10/29/cumulative-update-2-to-the-rml-utilities-for-microsoft-sql-server-released.aspx)</span><span class="sxs-lookup"><span data-stu-id="002f8-335">Download and run the x64 installation package for the RML utilities from the following page: [https://blogs.msdn.com/b/psssql/archive/2013/10/29/cumulative-update-2-to-the-rml-utilities-for-microsoft-sql-server-released.aspx](https://blogs.msdn.com/b/psssql/archive/2013/10/29/cumulative-update-2-to-the-rml-utilities-for-microsoft-sql-server-released.aspx)</span></span>  
  
2.  <span data-ttu-id="002f8-336">如果出现指示某些文件正在使用的对话框，请单击“继续”</span><span class="sxs-lookup"><span data-stu-id="002f8-336">If there is a dialog box saying certain files are in use, click 'Continue'</span></span>  
  
### <a name="running-ostress"></a><span data-ttu-id="002f8-337">运行 Ostress</span><span class="sxs-lookup"><span data-stu-id="002f8-337">Running ostress</span></span>  
 <span data-ttu-id="002f8-338">Ostress 从命令行提示符运行。</span><span class="sxs-lookup"><span data-stu-id="002f8-338">Ostress is run from the command-line prompt.</span></span> <span data-ttu-id="002f8-339">从“RML 命令提示符”（作为 RML 实用工具的一部分安装）运行该工具是最方便的。</span><span class="sxs-lookup"><span data-stu-id="002f8-339">It is most convenient to run the tool from the "RML Cmd Prompt", which is installed as part of the RML Utilities.</span></span>  
  
 <span data-ttu-id="002f8-340">若要打开 RML 命令提示符，请按照以下说明执行：</span><span class="sxs-lookup"><span data-stu-id="002f8-340">To open the RML Cmd Prompt follow these instructions:</span></span>  
  
 <span data-ttu-id="002f8-341">在 Windows Server 2012 [R2] 以及 Windows 8 和 8.1 中，通过单击 Windows 键打开“开始”菜单，然后键入“rml”。</span><span class="sxs-lookup"><span data-stu-id="002f8-341">In Windows Server 2012 [R2] and in Windows 8 and 8.1, open the start menu by clicking the Windows key, and type 'rml'.</span></span> <span data-ttu-id="002f8-342">单击“RML 命令提示符”（处于搜索结果列表中）。</span><span class="sxs-lookup"><span data-stu-id="002f8-342">Click on "RML Cmd Prompt", which will be in the list of search results.</span></span>  
  
 <span data-ttu-id="002f8-343">确保命令提示符位于 RML 实用工具安装文件夹中。</span><span class="sxs-lookup"><span data-stu-id="002f8-343">Ensure that the command prompt is located in the RML Utilities installation folder.</span></span> <span data-ttu-id="002f8-344">例如：</span><span class="sxs-lookup"><span data-stu-id="002f8-344">For example:</span></span>  
  
 ![](../../2014/database-engine/media/SQLServer2014RTMIn-MemoryOLTP01.jpg)  
  
 <span data-ttu-id="002f8-345">在不使用任何命令行选项的情况下仅运行 ostress.exe 时，可以查看 Ostress 的命令行选项。</span><span class="sxs-lookup"><span data-stu-id="002f8-345">The command-line options for ostress can be seen when simply running ostress.exe without any command-line options.</span></span> <span data-ttu-id="002f8-346">对此示例运行 Ostress 时要考虑的主要选项有：</span><span class="sxs-lookup"><span data-stu-id="002f8-346">The main options to consider for running ostress with this sample are:</span></span>  
  
-   <span data-ttu-id="002f8-347">-S 要连接到的 [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 实例的名称</span><span class="sxs-lookup"><span data-stu-id="002f8-347">-S name of [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance to connect to</span></span>  
  
-   <span data-ttu-id="002f8-348">-E 使用 Windows 身份验证连接 (默认) ;如果使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 身份验证，请使用选项-u 和-P 分别指定用户名和密码</span><span class="sxs-lookup"><span data-stu-id="002f8-348">-E use Windows authentication to connect (default); if you use [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] authentication, use the options -U and -P to specify the username and password, respectively</span></span>  
  
-   <span data-ttu-id="002f8-349">-d 数据库的名称，对于此示例为 AdventureWorks2014</span><span class="sxs-lookup"><span data-stu-id="002f8-349">-d name of the database, for this example AdventureWorks2014</span></span>  
  
-   <span data-ttu-id="002f8-350">-Q 要执行的 T-SQL 语句</span><span class="sxs-lookup"><span data-stu-id="002f8-350">-Q the T-SQL statement to be executed</span></span>  
  
-   <span data-ttu-id="002f8-351">-n 处理每个输入文件/查询的连接数</span><span class="sxs-lookup"><span data-stu-id="002f8-351">-n number of connections processing each input file/query</span></span>  
  
-   <span data-ttu-id="002f8-352">-r 每个连接执行每个输入文件/查询的迭代数</span><span class="sxs-lookup"><span data-stu-id="002f8-352">-r the number of iterations for each connection to execute each input file/query</span></span>  
  
### <a name="demo-workload"></a><span data-ttu-id="002f8-353">演示工作负荷</span><span class="sxs-lookup"><span data-stu-id="002f8-353">Demo Workload</span></span>  
 <span data-ttu-id="002f8-354">演示工作负荷中使用的主要存储过程是 Sales.usp_InsertSalesOrder_inmem/ondisk。</span><span class="sxs-lookup"><span data-stu-id="002f8-354">The main stored procedure used in the demo workload is Sales.usp_InsertSalesOrder_inmem/ondisk.</span></span> <span data-ttu-id="002f8-355">下面的脚本使用示例数据构造一个表值参数 (TVP)，并调用该过程以插入包含 5 个行项的销售订单。</span><span class="sxs-lookup"><span data-stu-id="002f8-355">The script in the below constructs a table-valued parameter (TVP) with sample data, and calls the procedure to insert a sales order with 5 line items.</span></span>  
  
 <span data-ttu-id="002f8-356">Ostress 工具用于并行执行存储过程调用，以模拟并发插入销售订单的客户端。</span><span class="sxs-lookup"><span data-stu-id="002f8-356">The ostress tool is used to execute the stored procedure calls in parallel, to simulate clients inserting sales orders concurrently.</span></span>  
  
 <span data-ttu-id="002f8-357">在每次执行 Demo.usp_DemoReset 的压力运行之后重置演示。</span><span class="sxs-lookup"><span data-stu-id="002f8-357">Reset the demo after each stress run executing Demo.usp_DemoReset.</span></span> <span data-ttu-id="002f8-358">此过程删除内存优化表中的行、截断基于磁盘的表并执行数据库检查点。</span><span class="sxs-lookup"><span data-stu-id="002f8-358">This procedure deletes the rows in the memory-optimized tables, truncates the disk-based tables, and executes a database checkpoint.</span></span>  
  
 <span data-ttu-id="002f8-359">以下脚本并发执行，以模拟销售订单处理工作负荷：</span><span class="sxs-lookup"><span data-stu-id="002f8-359">The following script is executed concurrently to simulate a sales order processing workload:</span></span>  
  
```  
DECLARE   
      @i int = 0,   
      @od Sales.SalesOrderDetailType_inmem,   
      @SalesOrderID int,   
      @DueDate datetime2 = sysdatetime(),   
      @CustomerID int = rand() * 8000,   
      @BillToAddressID int = rand() * 10000,   
      @ShipToAddressID int = rand() * 10000,   
      @ShipMethodID int = (rand() * 5) + 1;   
  
INSERT INTO @od   
SELECT OrderQty, ProductID, SpecialOfferID   
FROM Demo.DemoSalesOrderDetailSeed   
WHERE OrderID= cast((rand()*106) + 1 as int);   
  
WHILE (@i < 20)   
BEGIN;   
      EXEC Sales.usp_InsertSalesOrder_inmem @SalesOrderID OUTPUT, @DueDate, @CustomerID, @BillToAddressID, @ShipToAddressID, @ShipMethodID, @od;   
      SET @i += 1   
END  
  
```  
  
 <span data-ttu-id="002f8-360">借助此脚本，构造的每个示例订单会通过在 WHILE 循环中执行的 20 个存储过程插入 20 次。</span><span class="sxs-lookup"><span data-stu-id="002f8-360">With this script, each sample order that is constructed is inserted 20 times, through 20 stored procedures executed in a WHILE loop.</span></span> <span data-ttu-id="002f8-361">因为数据库用于构造示例订单，所以使用该循环。</span><span class="sxs-lookup"><span data-stu-id="002f8-361">The loop is used to account for the fact that the database is used to construct the sample order.</span></span> <span data-ttu-id="002f8-362">在典型生产环境中，中间层应用程序将构造要插入的销售订单。</span><span class="sxs-lookup"><span data-stu-id="002f8-362">In typical production environments, the mid-tier application will construct the sales order to be inserted.</span></span>  
  
 <span data-ttu-id="002f8-363">上面的脚本将销售订单插入内存优化表中。</span><span class="sxs-lookup"><span data-stu-id="002f8-363">The above script inserts sales orders into memory-optimized tables.</span></span> <span data-ttu-id="002f8-364">用于将销售订单插入基于磁盘的表中的脚本通过将两个“_inmem”替换为“_ondisk”而派生。</span><span class="sxs-lookup"><span data-stu-id="002f8-364">The script to insert sales orders into disk-based tables is derived by replacing the two occurrences of '_inmem' with '_ondisk'.</span></span>  
  
 <span data-ttu-id="002f8-365">我们将使用 Ostress 工具通过几个并发连接执行脚本。</span><span class="sxs-lookup"><span data-stu-id="002f8-365">We will use the ostress tool to execute the scripts using several concurrent connections.</span></span> <span data-ttu-id="002f8-366">我们将使用参数“-n”控制连接数，使用参数“r”控制对每个连接执行脚本的次数。</span><span class="sxs-lookup"><span data-stu-id="002f8-366">We will use the parameter '-n' to control the number of connections, and the parameter 'r' to control how many times the script is executed on each connection.</span></span>  
  
#### <a name="functional-validation-of-the-workload"></a><span data-ttu-id="002f8-367">工作负荷的功能验证</span><span class="sxs-lookup"><span data-stu-id="002f8-367">Functional Validation of the Workload</span></span>  
 <span data-ttu-id="002f8-368">若要验证一切是否正常运行，我们将从一个示例测试开始，使用10个并发连接和5个迭代，同时插入总共 10 \* 5 \* 20 = 1000 销售订单。</span><span class="sxs-lookup"><span data-stu-id="002f8-368">To verify everything works, we will start with a sample test, using 10 concurrent connects and 5 iterations, inserting a total of 10 \* 5 \* 20 = 1000 sales order.</span></span>  
  
 <span data-ttu-id="002f8-369">对于以下命令，我们假设在本地计算机上使用默认实例。</span><span class="sxs-lookup"><span data-stu-id="002f8-369">With the below command we assume using the default instance on the local machine.</span></span> <span data-ttu-id="002f8-370">如果使用命名实例或使用远程服务器，请使用参数 -S 相应地更改服务器名称。</span><span class="sxs-lookup"><span data-stu-id="002f8-370">If you are using a named instance or using a remote server, change the server name accordingly, using the parameter -S.</span></span>  
  
 <span data-ttu-id="002f8-371">在 RML 命令提示符处使用以下命令，将 1000 个销售订单插入内存优化表：</span><span class="sxs-lookup"><span data-stu-id="002f8-371">Insert 1000 sales orders in memory-optimized tables use the following command in the RML Cmd Prompt:</span></span>  
  
 <span data-ttu-id="002f8-372">单击“复制”按钮复制该命令，将其粘贴到 RML 实用工具命令提示符处。</span><span class="sxs-lookup"><span data-stu-id="002f8-372">Click the Copy button to copy the command, and paste it into the RML Utilities command prompt.</span></span>  
  
```  
ostress.exe -n10 -r5 -S. -E -dAdventureWorks2014 -q -Q"DECLARE @i int = 0, @od Sales.SalesOrderDetailType_inmem, @SalesOrderID int, @DueDate datetime2 = sysdatetime(), @CustomerID int = rand() * 8000, @BillToAddressID int = rand() * 10000, @ShipToAddressID int = rand() * 10000, @ShipMethodID int = (rand() * 5) + 1; INSERT INTO @od SELECT OrderQty, ProductID, SpecialOfferID FROM Demo.DemoSalesOrderDetailSeed WHERE OrderID= cast((rand()*106) + 1 as int); while (@i < 20) begin; EXEC Sales.usp_InsertSalesOrder_inmem @SalesOrderID OUTPUT, @DueDate, @CustomerID, @BillToAddressID, @ShipToAddressID, @ShipMethodID, @od; set @i += 1 end"  
```  
  
 <span data-ttu-id="002f8-373">如果一切正常，则命令窗口类似于以下这样。</span><span class="sxs-lookup"><span data-stu-id="002f8-373">If everything works as expected, your command window will look similar to the following.</span></span> <span data-ttu-id="002f8-374">不会出现错误消息。</span><span class="sxs-lookup"><span data-stu-id="002f8-374">Error messages are not expected.</span></span>  
  
 ![](../../2014/database-engine/media/SQLServer2014RTMIn-MemoryOLTP02.jpg)  
  
 <span data-ttu-id="002f8-375">通过在 RML 命令提示符处运行以下命令，可以验证工作负荷对于基于磁盘的表是否也正常工作：</span><span class="sxs-lookup"><span data-stu-id="002f8-375">Validate that also the workload functions as expected for disk-based tables by running the following command in the RML Cmd Prompt:</span></span>  
  
 <span data-ttu-id="002f8-376">单击“复制”按钮复制该命令，将其粘贴到 RML 实用工具命令提示符处。</span><span class="sxs-lookup"><span data-stu-id="002f8-376">Click the Copy button to copy the command, and paste it into the RML Utilities command prompt.</span></span>  
  
```  
ostress.exe -n10 -r5 -S. -E -dAdventureWorks2014 -q -Q"DECLARE @i int = 0, @od Sales.SalesOrderDetailType_ondisk, @SalesOrderID int, @DueDate datetime2 = sysdatetime(), @CustomerID int = rand() * 8000, @BillToAddressID int = rand() * 10000, @ShipToAddressID int = rand() * 10000, @ShipMethodID int = (rand() * 5) + 1; INSERT INTO @od SELECT OrderQty, ProductID, SpecialOfferID FROM Demo.DemoSalesOrderDetailSeed WHERE OrderID= cast((rand()*106) + 1 as int); while (@i < 20) begin; EXEC Sales.usp_InsertSalesOrder_ondisk @SalesOrderID OUTPUT, @DueDate, @CustomerID, @BillToAddressID, @ShipToAddressID, @ShipMethodID, @od; set @i += 1 end"  
```  
  
#### <a name="running-the-workload"></a><span data-ttu-id="002f8-377">运行工作负荷</span><span class="sxs-lookup"><span data-stu-id="002f8-377">Running the Workload</span></span>  
 <span data-ttu-id="002f8-378">为了进行大规模测试，我们使用 100 个连接插入 1000 万个销售订单。</span><span class="sxs-lookup"><span data-stu-id="002f8-378">To test at scale we insert 10 million sales orders, using 100 connections.</span></span> <span data-ttu-id="002f8-379">此测试适合在中等服务器（例如，8 个物理核心、16 个逻辑核心以及用于日志的基本 SSD 存储）上执行。</span><span class="sxs-lookup"><span data-stu-id="002f8-379">This test performs reasonably on a modest server (e.g., 8 physical, 16 logical cores), and basic SSD storage for the log.</span></span> <span data-ttu-id="002f8-380">如果该测试在你的硬件上性能不佳，请查看[解决测试运行缓慢的问题](#Troubleshootingslow-runningtests)一节。如果要降低此测试的压力级别，请通过更改参数“-n”减少连接数。</span><span class="sxs-lookup"><span data-stu-id="002f8-380">If the test does not perform well on your hardware, take look at the Section [Troubleshooting slow-running tests](#Troubleshootingslow-runningtests).If you want to reduce the level of stress for this test, lower the number of connections by changing the parameter '-n'.</span></span> <span data-ttu-id="002f8-381">例如，若要将连接计数减少为 40，请将参数“-n100”更改为“-n40”。</span><span class="sxs-lookup"><span data-stu-id="002f8-381">For example to lower the connection count to 40, change the parameter '-n100' to '-n40'.</span></span>  
  
 <span data-ttu-id="002f8-382">作为工作负荷的性能度量，我们使用 ostress.exe 在运行工作负荷之后报告的占用时间。</span><span class="sxs-lookup"><span data-stu-id="002f8-382">As a performance measure for the workload we use the elapsed time as reported by ostress.exe after running the workload.</span></span>  
  
##### <a name="memory-optimized-tables"></a><span data-ttu-id="002f8-383">内存优化表</span><span class="sxs-lookup"><span data-stu-id="002f8-383">Memory-optimized tables</span></span>  
 <span data-ttu-id="002f8-384">我们首先对内存优化表运行工作负荷。</span><span class="sxs-lookup"><span data-stu-id="002f8-384">We will start by running the workload on memory-optimized tables.</span></span> <span data-ttu-id="002f8-385">以下命令打开 100 个线程，每个线程运行 5,000 次迭代。</span><span class="sxs-lookup"><span data-stu-id="002f8-385">The following command opens 100 threads, each running for 5,000 iterations.</span></span>  <span data-ttu-id="002f8-386">每次迭代在单独事务中插入 20 个销售订单。</span><span class="sxs-lookup"><span data-stu-id="002f8-386">Each iteration inserts 20 sales orders in separate transactions.</span></span> <span data-ttu-id="002f8-387">每次迭代进行 20 个插入，对数据库用于生成待插入数据进行补偿。</span><span class="sxs-lookup"><span data-stu-id="002f8-387">There are 20 inserts per iteration to compensate for the fact that the database is used to generate the data to be inserted.</span></span> <span data-ttu-id="002f8-388">这会生成总共 20 \* 5,000 \* 100 = 10,000,000 个销售订单插入。</span><span class="sxs-lookup"><span data-stu-id="002f8-388">This yield a total of 20 \* 5,000 \* 100 = 10,000,000 sales order inserts.</span></span>  
  
 <span data-ttu-id="002f8-389">打开 RML 命令提示符，执行以下命令：</span><span class="sxs-lookup"><span data-stu-id="002f8-389">Open the RML Cmd Prompt, and execute the following command:</span></span>  
  
 <span data-ttu-id="002f8-390">单击“复制”按钮复制该命令，将其粘贴到 RML 实用工具命令提示符处。</span><span class="sxs-lookup"><span data-stu-id="002f8-390">Click the Copy button to copy the command, and paste it into the RML Utilities command prompt.</span></span>  
  
```  
ostress.exe -n100 -r5000 -S. -E -dAdventureWorks2014 -q -Q"DECLARE @i int = 0, @od Sales.SalesOrderDetailType_inmem, @SalesOrderID int, @DueDate datetime2 = sysdatetime(), @CustomerID int = rand() * 8000, @BillToAddressID int = rand() * 10000, @ShipToAddressID int = rand() * 10000, @ShipMethodID int = (rand() * 5) + 1; INSERT INTO @od SELECT OrderQty, ProductID, SpecialOfferID FROM Demo.DemoSalesOrderDetailSeed WHERE OrderID= cast((rand()*106) + 1 as int); while (@i < 20) begin; EXEC Sales.usp_InsertSalesOrder_inmem @SalesOrderID OUTPUT, @DueDate, @CustomerID, @BillToAddressID, @ShipToAddressID, @ShipMethodID, @od; set @i += 1 end"  
```  
  
 <span data-ttu-id="002f8-391">在一台共有 8 个物理（16 个逻辑）核心的测试服务器上，需要 2 分 5 秒。</span><span class="sxs-lookup"><span data-stu-id="002f8-391">On one test server with a total number of 8 physical (16 logical) cores, this took 2 minutes and 5 seconds.</span></span> <span data-ttu-id="002f8-392">在另一台有 24 个物理（48 个逻辑）核心的测试服务器上，需要 1 分 0 秒。</span><span class="sxs-lookup"><span data-stu-id="002f8-392">On a second test server with 24 physical (48 logical) cores, this took 1 minute and 0 seconds.</span></span>  
  
 <span data-ttu-id="002f8-393">在工作负荷运行期间观察 CPU 利用率（例如使用任务管理器）。</span><span class="sxs-lookup"><span data-stu-id="002f8-393">Observe the CPU utilization while the workload is running, for example using task manager.</span></span> <span data-ttu-id="002f8-394">可以看到 CPU 利用率接近 100%。</span><span class="sxs-lookup"><span data-stu-id="002f8-394">You will see that CPU utilization is close to 100%.</span></span> <span data-ttu-id="002f8-395">如果不是这样，则存在日志 IO 瓶颈，另请参见 [运行缓慢的测试的故障排除](#Troubleshootingslow-runningtests)。</span><span class="sxs-lookup"><span data-stu-id="002f8-395">If this is not the case, you have a log IO bottleneck see also [Troubleshooting slow-running tests](#Troubleshootingslow-runningtests).</span></span>  
  
##### <a name="disk-based-tables"></a><span data-ttu-id="002f8-396">基于磁盘的表</span><span class="sxs-lookup"><span data-stu-id="002f8-396">Disk-based tables</span></span>  
 <span data-ttu-id="002f8-397">以下命令对基于磁盘的表运行工作负荷。</span><span class="sxs-lookup"><span data-stu-id="002f8-397">The following command will run the workload on disk-based tables.</span></span> <span data-ttu-id="002f8-398">请注意，此工作负荷可能要花一些时间执行，这在很大程度上是由于系统中存在闩锁争用。</span><span class="sxs-lookup"><span data-stu-id="002f8-398">Note that this workload may take a while to execute, which is largely due to latch contention in the system.</span></span> <span data-ttu-id="002f8-399">内存优化表没有闩锁，因而不会遇到这个问题。</span><span class="sxs-lookup"><span data-stu-id="002f8-399">Memory-optimized table are latch-free and thus do not suffer from this problem.</span></span>  
  
 <span data-ttu-id="002f8-400">打开 RML 命令提示符，执行以下命令：</span><span class="sxs-lookup"><span data-stu-id="002f8-400">Open the RML Cmd Prompt, and execute the following command:</span></span>  
  
 <span data-ttu-id="002f8-401">单击“复制”按钮复制该命令，将其粘贴到 RML 实用工具命令提示符处。</span><span class="sxs-lookup"><span data-stu-id="002f8-401">Click the Copy button to copy the command, and paste it into the RML Utilities command prompt.</span></span>  
  
```  
ostress.exe -n100 -r5000 -S. -E -dAdventureWorks2014 -q -Q"DECLARE @i int = 0, @od Sales.SalesOrderDetailType_ondisk, @SalesOrderID int, @DueDate datetime2 = sysdatetime(), @CustomerID int = rand() * 8000, @BillToAddressID int = rand() * 10000, @ShipToAddressID int = rand() * 10000, @ShipMethodID int = (rand() * 5) + 1; INSERT INTO @od SELECT OrderQty, ProductID, SpecialOfferID FROM Demo.DemoSalesOrderDetailSeed WHERE OrderID= cast((rand()*106) + 1 as int); while (@i < 20) begin; EXEC Sales.usp_InsertSalesOrder_ondisk @SalesOrderID OUTPUT, @DueDate, @CustomerID, @BillToAddressID, @ShipToAddressID, @ShipMethodID, @od; set @i += 1 end"  
```  
  
 <span data-ttu-id="002f8-402">在一台共有 8 个物理（16 个逻辑）核心的测试服务器上，需要 41 分 25 秒。</span><span class="sxs-lookup"><span data-stu-id="002f8-402">On one test server with a total number of 8 physical (16 logical) cores, this took 41 minutes and 25 seconds.</span></span> <span data-ttu-id="002f8-403">在另一台有 24 个物理（48 个逻辑）核心的测试服务器上，需要 52 分 16 秒。</span><span class="sxs-lookup"><span data-stu-id="002f8-403">On a second test server with 24 physical (48 logical) cores, this took 52 minutes and 16 seconds.</span></span>  
  
 <span data-ttu-id="002f8-404">此测试中内存优化表与基于磁盘的表之间存在性能差异的主要因素在于，使用基于磁盘的表时， [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 无法完全利用 CPU。</span><span class="sxs-lookup"><span data-stu-id="002f8-404">The main factor in the performance difference between memory-optimized tables and disk-based tables in this test is the fact that when using disk-based tables, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] cannot not fully utilize the CPU.</span></span> <span data-ttu-id="002f8-405">原因在于闩锁争用：并发事务尝试写入相同数据页；闩锁用于确保一次只有一个事务才能写入页。</span><span class="sxs-lookup"><span data-stu-id="002f8-405">The reason is latch contention: concurrent transactions are attempting to write to the same data page; latches are used to ensure only one transaction at a time can write to a page.</span></span> <span data-ttu-id="002f8-406">[!INCLUDE[hek_2](../includes/hek-2-md.md)] 引擎没有闩锁，数据行不是按页组织。</span><span class="sxs-lookup"><span data-stu-id="002f8-406">The [!INCLUDE[hek_2](../includes/hek-2-md.md)] engine is latch-free, and data rows are not organized in pages.</span></span> <span data-ttu-id="002f8-407">因而，并发事务不会阻塞彼此的插入，从而 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 能够完全利用 CPU。</span><span class="sxs-lookup"><span data-stu-id="002f8-407">Thus, concurrent transactions do not block each other's inserts, thus enabling [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to fully utilize the CPU.</span></span>  
  
 <span data-ttu-id="002f8-408">在工作负荷运行期间可以观察 CPU 利用率（例如使用任务管理器）。</span><span class="sxs-lookup"><span data-stu-id="002f8-408">You can observe the CPU utilization while the workload is running, for example using task manager.</span></span> <span data-ttu-id="002f8-409">对于基于磁盘的表，可以看到 CPU 利用率远低于 100%。</span><span class="sxs-lookup"><span data-stu-id="002f8-409">You will see with disk-based tables the CPU utilization is far from 100%.</span></span> <span data-ttu-id="002f8-410">在有 16 个逻辑处理器的测试配置中，利用率保持在 24% 左右。</span><span class="sxs-lookup"><span data-stu-id="002f8-410">On a test configuration with 16 logical processors, the utilization would hover around 24%.</span></span>  
  
 <span data-ttu-id="002f8-411">或者，可以使用性能监视器通过性能计数器“\SQL Server:Latches\Latch Waits/sec”查看每秒的闩锁等待数。</span><span class="sxs-lookup"><span data-stu-id="002f8-411">Optionally, you can view the number of latch waits per second using Performance Monitor, with the performance counter '\SQL Server:Latches\Latch Waits/sec'.</span></span>  
  
#### <a name="resetting-the-demo"></a><span data-ttu-id="002f8-412">重置演示</span><span class="sxs-lookup"><span data-stu-id="002f8-412">Resetting the demo</span></span>  
 <span data-ttu-id="002f8-413">若要重置演示，请打开 RML 命令提示符，执行以下命令：</span><span class="sxs-lookup"><span data-stu-id="002f8-413">To reset the demo, open the RML Cmd Prompt, and execute the following command:</span></span>  
  
```  
ostress.exe -S. -E -dAdventureWorks2014 -Q"EXEC Demo.usp_DemoReset"  
```  
  
 <span data-ttu-id="002f8-414">根据硬件情况，可能需要几分钟运行。</span><span class="sxs-lookup"><span data-stu-id="002f8-414">Depending on the hardware this may take a few minutes to run.</span></span>  
  
 <span data-ttu-id="002f8-415">我们建议在每次演示运行之后重置。</span><span class="sxs-lookup"><span data-stu-id="002f8-415">We recommend a reset after every demo run.</span></span> <span data-ttu-id="002f8-416">因为此工作负荷仅涉及插入，所以每次运行将占用更多内存，因而需要重置来防止内存不足。</span><span class="sxs-lookup"><span data-stu-id="002f8-416">Because this workload is insert-only, each run will consume more memory, and thus a reset is required to prevent running out of memory.</span></span> <span data-ttu-id="002f8-417">运行之后占用的内存量在 [运行工作负荷之后的内存利用率](#Memoryutilizationafterrunningtheworkload)一节中进行了讨论。</span><span class="sxs-lookup"><span data-stu-id="002f8-417">The amount of memory consumed after a run is discussed in Section [Memory utilization after running the workload](#Memoryutilizationafterrunningtheworkload).</span></span>  
  
###  <a name="troubleshooting-slow-running-tests"></a><a name="Troubleshootingslow-runningtests"></a> <span data-ttu-id="002f8-418">解决测试运行缓慢的问题</span><span class="sxs-lookup"><span data-stu-id="002f8-418">Troubleshooting slow-running tests</span></span>  
 <span data-ttu-id="002f8-419">测试结果通常因硬件而异，也因测试运行中使用的并发级别而异。</span><span class="sxs-lookup"><span data-stu-id="002f8-419">Test results will typically vary with hardware, and also the level of concurrency used in the test run.</span></span> <span data-ttu-id="002f8-420">结果与预期不符时要了解的几个方面有：</span><span class="sxs-lookup"><span data-stu-id="002f8-420">A couple of things to look for if the results are not as expected:</span></span>  
  
-   <span data-ttu-id="002f8-421">并发事务数：对单个线程运行工作负荷时，通过 [!INCLUDE[hek_2](../includes/hek-2-md.md)] 获得的性能提升可能小于 2 倍。</span><span class="sxs-lookup"><span data-stu-id="002f8-421">Number of concurrent transactions: When running the workload on a single thread, performance gain with [!INCLUDE[hek_2](../includes/hek-2-md.md)] will likely be less than 2X.</span></span> <span data-ttu-id="002f8-422">如果并发级别较高，则闩锁争用是唯一的大问题。</span><span class="sxs-lookup"><span data-stu-id="002f8-422">Latch contention is only a big problem if there is a high level of concurrency.</span></span>  
  
-   <span data-ttu-id="002f8-423">可供 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]使用的核心数较少：这意味着系统中的并发级别较低，因为并发执行事务的数量不能超过可供 SQL 使用的核心数。</span><span class="sxs-lookup"><span data-stu-id="002f8-423">Low number of cores available to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]: This means there will be a low level of concurrency in the system, as there can only be as many concurrently executing transactions as there are cores available to SQL.</span></span>  
  
    -   <span data-ttu-id="002f8-424">症状：如果对基于磁盘的表运行工作负荷时 CPU 利用率较高，则意味着不存在很多争用，说明缺乏并发性。</span><span class="sxs-lookup"><span data-stu-id="002f8-424">Symptom: if the CPU utilization is high when running the workload on disk-based tables, this means there is not a lot of contention, pointing to a lack of concurrency.</span></span>  
  
-   <span data-ttu-id="002f8-425">日志驱动器的速度：如果日志驱动器无法跟上系统中的事务吞吐量级别，则工作负荷会在日志 IO 方面遇到瓶颈。</span><span class="sxs-lookup"><span data-stu-id="002f8-425">Speed of the log drive: If the log drive cannot keep up with the level of transaction throughput in the system, the workload becomes bottlenecked on log IO.</span></span> <span data-ttu-id="002f8-426">虽然日志记录对于 [!INCLUDE[hek_2](../includes/hek-2-md.md)]更加高效，但是如果日志 IO 是瓶颈，则性能提升的可能性有限。</span><span class="sxs-lookup"><span data-stu-id="002f8-426">Although logging is more efficient with [!INCLUDE[hek_2](../includes/hek-2-md.md)], if log IO is a bottleneck, the potential performance gain is limited.</span></span>  
  
    -   <span data-ttu-id="002f8-427">症状：如果对内存优化表运行工作负荷时 CPU 利用率不接近于 100% 或是非常尖峰，则可能存在日志 IO 瓶颈。</span><span class="sxs-lookup"><span data-stu-id="002f8-427">Symptom: if the CPU utilization is not close to 100% or is very spiky when running the workload on memory-optimized tables, it is possible there is a log IO bottleneck.</span></span> <span data-ttu-id="002f8-428">这可以通过打开资源监视器查看日志驱动器的队列长度来进行确认。</span><span class="sxs-lookup"><span data-stu-id="002f8-428">This can be confirmed by opening Resource Monitor and looking at the queue length for the log drive.</span></span>  
  
##  <a name="memory-and-disk-space-utilization-in-the-sample"></a><a name="MemoryandDiskSpaceUtilizationintheSample"></a> <span data-ttu-id="002f8-429">示例中的内存和磁盘空间利用率</span><span class="sxs-lookup"><span data-stu-id="002f8-429">Memory and Disk Space Utilization in the Sample</span></span>  
 <span data-ttu-id="002f8-430">下面我们讨论示例数据库的内存和磁盘空间利用率方面的情况。</span><span class="sxs-lookup"><span data-stu-id="002f8-430">In the below we describe what to expect in terms of memory and disk space utilization for the sample database.</span></span> <span data-ttu-id="002f8-431">我们还会介绍在有 16 个逻辑核心的测试服务器上看到的结果。</span><span class="sxs-lookup"><span data-stu-id="002f8-431">We also show the results we have seen in on a test server with 16 logical cores.</span></span>  
  
###  <a name="memory-utilization-for-the-memory-optimized-tables"></a><a name="Memoryutilizationforthememory-optimizedtables"></a> <span data-ttu-id="002f8-432">内存优化表的内存利用率</span><span class="sxs-lookup"><span data-stu-id="002f8-432">Memory utilization for the memory-optimized tables</span></span>  
  
#### <a name="overall-utilization-of-the-database"></a><span data-ttu-id="002f8-433">数据库的总体利用率</span><span class="sxs-lookup"><span data-stu-id="002f8-433">Overall utilization of the database</span></span>  
 <span data-ttu-id="002f8-434">以下查询可用于获取系统中 [!INCLUDE[hek_2](../includes/hek-2-md.md)] 的总体内存利用率。</span><span class="sxs-lookup"><span data-stu-id="002f8-434">The following query can be used to obtain the total memory utilization for [!INCLUDE[hek_2](../includes/hek-2-md.md)] in the system.</span></span>  
  
```  
SELECT type  
   , name  
, pages_kb/1024 AS pages_MB   
FROM sys.dm_os_memory_clerks WHERE type LIKE '%xtp%'  
```  
  
 <span data-ttu-id="002f8-435">刚刚创建数据库之后的快照：</span><span class="sxs-lookup"><span data-stu-id="002f8-435">Snapshot after the database has just been created:</span></span>  
  
||||  
|-|-|-|  
|<span data-ttu-id="002f8-436">type</span><span class="sxs-lookup"><span data-stu-id="002f8-436">**type**</span></span>|<span data-ttu-id="002f8-437">name</span><span class="sxs-lookup"><span data-stu-id="002f8-437">**name**</span></span>|<span data-ttu-id="002f8-438">**pages_MB**</span><span class="sxs-lookup"><span data-stu-id="002f8-438">**pages_MB**</span></span>|  
|<span data-ttu-id="002f8-439">MEMORYCLERK_XTP</span><span class="sxs-lookup"><span data-stu-id="002f8-439">MEMORYCLERK_XTP</span></span>|<span data-ttu-id="002f8-440">默认</span><span class="sxs-lookup"><span data-stu-id="002f8-440">Default</span></span>|<span data-ttu-id="002f8-441">94</span><span class="sxs-lookup"><span data-stu-id="002f8-441">94</span></span>|  
|<span data-ttu-id="002f8-442">MEMORYCLERK_XTP</span><span class="sxs-lookup"><span data-stu-id="002f8-442">MEMORYCLERK_XTP</span></span>|<span data-ttu-id="002f8-443">DB_ID_5</span><span class="sxs-lookup"><span data-stu-id="002f8-443">DB_ID_5</span></span>|<span data-ttu-id="002f8-444">877</span><span class="sxs-lookup"><span data-stu-id="002f8-444">877</span></span>|  
|<span data-ttu-id="002f8-445">MEMORYCLERK_XTP</span><span class="sxs-lookup"><span data-stu-id="002f8-445">MEMORYCLERK_XTP</span></span>|<span data-ttu-id="002f8-446">默认</span><span class="sxs-lookup"><span data-stu-id="002f8-446">Default</span></span>|<span data-ttu-id="002f8-447">0</span><span class="sxs-lookup"><span data-stu-id="002f8-447">0</span></span>|  
|<span data-ttu-id="002f8-448">MEMORYCLERK_XTP</span><span class="sxs-lookup"><span data-stu-id="002f8-448">MEMORYCLERK_XTP</span></span>|<span data-ttu-id="002f8-449">默认</span><span class="sxs-lookup"><span data-stu-id="002f8-449">Default</span></span>|<span data-ttu-id="002f8-450">0</span><span class="sxs-lookup"><span data-stu-id="002f8-450">0</span></span>|  
  
 <span data-ttu-id="002f8-451">默认内存分配器包含系统范围内存结构，相对较小。</span><span class="sxs-lookup"><span data-stu-id="002f8-451">The default memory clerks contain system-wide memory structures and are relatively small.</span></span> <span data-ttu-id="002f8-452">用户数据库（在此例中是 ID 为 5 的数据库）的内存分配器大约为 900MB。</span><span class="sxs-lookup"><span data-stu-id="002f8-452">The memory clerk for the user database, in this case database with ID 5, is about 900MB.</span></span>  
  
#### <a name="memory-utilization-per-table"></a><span data-ttu-id="002f8-453">每个表的内存利用率</span><span class="sxs-lookup"><span data-stu-id="002f8-453">Memory utilization per table</span></span>  
 <span data-ttu-id="002f8-454">以下查询可用于深化到各个表及其索引的内存利用率：</span><span class="sxs-lookup"><span data-stu-id="002f8-454">The following query can be used to drill down into the memory utilization of the individual tables and their indexes:</span></span>  
  
```  
SELECT object_name(t.object_id) AS [Table Name]  
     , memory_allocated_for_table_kb  
 , memory_allocated_for_indexes_kb  
FROM sys.dm_db_xtp_table_memory_stats dms JOIN sys.tables t   
ON dms.object_id=t.object_id  
WHERE t.type='U'  
```  
  
 <span data-ttu-id="002f8-455">下面显示此查询对于示例全新安装的结果：</span><span class="sxs-lookup"><span data-stu-id="002f8-455">The following shows the results of this query for a fresh installation of the sample:</span></span>  
  
||||  
|-|-|-|  
|<span data-ttu-id="002f8-456">**表名**</span><span class="sxs-lookup"><span data-stu-id="002f8-456">**Table Name**</span></span>|<span data-ttu-id="002f8-457">**memory_allocated_for_table_kb**</span><span class="sxs-lookup"><span data-stu-id="002f8-457">**memory_allocated_for_table_kb**</span></span>|<span data-ttu-id="002f8-458">**memory_allocated_for_indexes_kb**</span><span class="sxs-lookup"><span data-stu-id="002f8-458">**memory_allocated_for_indexes_kb**</span></span>|  
|<span data-ttu-id="002f8-459">SpecialOfferProduct_inmem</span><span class="sxs-lookup"><span data-stu-id="002f8-459">SpecialOfferProduct_inmem</span></span>|<span data-ttu-id="002f8-460">64</span><span class="sxs-lookup"><span data-stu-id="002f8-460">64</span></span>|<span data-ttu-id="002f8-461">3840</span><span class="sxs-lookup"><span data-stu-id="002f8-461">3840</span></span>|  
|<span data-ttu-id="002f8-462">DemoSalesOrderHeaderSeed</span><span class="sxs-lookup"><span data-stu-id="002f8-462">DemoSalesOrderHeaderSeed</span></span>|<span data-ttu-id="002f8-463">1984</span><span class="sxs-lookup"><span data-stu-id="002f8-463">1984</span></span>|<span data-ttu-id="002f8-464">5504</span><span class="sxs-lookup"><span data-stu-id="002f8-464">5504</span></span>|  
|<span data-ttu-id="002f8-465">SalesOrderDetail_inmem</span><span class="sxs-lookup"><span data-stu-id="002f8-465">SalesOrderDetail_inmem</span></span>|<span data-ttu-id="002f8-466">15316</span><span class="sxs-lookup"><span data-stu-id="002f8-466">15316</span></span>|<span data-ttu-id="002f8-467">663552</span><span class="sxs-lookup"><span data-stu-id="002f8-467">663552</span></span>|  
|<span data-ttu-id="002f8-468">DemoSalesOrderDetailSeed</span><span class="sxs-lookup"><span data-stu-id="002f8-468">DemoSalesOrderDetailSeed</span></span>|<span data-ttu-id="002f8-469">64</span><span class="sxs-lookup"><span data-stu-id="002f8-469">64</span></span>|<span data-ttu-id="002f8-470">10432</span><span class="sxs-lookup"><span data-stu-id="002f8-470">10432</span></span>|  
|<span data-ttu-id="002f8-471">SpecialOffer_inmem</span><span class="sxs-lookup"><span data-stu-id="002f8-471">SpecialOffer_inmem</span></span>|<span data-ttu-id="002f8-472">3</span><span class="sxs-lookup"><span data-stu-id="002f8-472">3</span></span>|<span data-ttu-id="002f8-473">8192</span><span class="sxs-lookup"><span data-stu-id="002f8-473">8192</span></span>|  
|<span data-ttu-id="002f8-474">SalesOrderHeader_inmem</span><span class="sxs-lookup"><span data-stu-id="002f8-474">SalesOrderHeader_inmem</span></span>|<span data-ttu-id="002f8-475">7168</span><span class="sxs-lookup"><span data-stu-id="002f8-475">7168</span></span>|<span data-ttu-id="002f8-476">147456</span><span class="sxs-lookup"><span data-stu-id="002f8-476">147456</span></span>|  
|<span data-ttu-id="002f8-477">Product_inmem</span><span class="sxs-lookup"><span data-stu-id="002f8-477">Product_inmem</span></span>|<span data-ttu-id="002f8-478">124</span><span class="sxs-lookup"><span data-stu-id="002f8-478">124</span></span>|<span data-ttu-id="002f8-479">12352</span><span class="sxs-lookup"><span data-stu-id="002f8-479">12352</span></span>|  
  
 <span data-ttu-id="002f8-480">可以看到，这些表相当小：SalesOrderHeader_inmem 的大小大约为 7MB，SalesOrderDetail_inmem 的大小大约为 15MB。</span><span class="sxs-lookup"><span data-stu-id="002f8-480">As you can see the tables are fairly small: SalesOrderHeader_inmem is about 7MB, and SalesOrderDetail_inmem is about 15MB in size.</span></span>  
  
 <span data-ttu-id="002f8-481">此处比较显著的是为索引分配的内存大小（与表数据大小相比）。</span><span class="sxs-lookup"><span data-stu-id="002f8-481">What is striking here is the size of the memory allocated for indexes, compared to the size of the table data.</span></span> <span data-ttu-id="002f8-482">这是因为示例中的哈希索引针对较大数据大小预设了大小。</span><span class="sxs-lookup"><span data-stu-id="002f8-482">That is because the hash indexes in the sample are pre-sized for a larger data size.</span></span> <span data-ttu-id="002f8-483">请注意，哈希索引有固定大小，因而其大小不会随表中的数据大小而增大。</span><span class="sxs-lookup"><span data-stu-id="002f8-483">Note that hash indexes have a fixed size, and thus their size will not grow with the size of data in the table.</span></span>  
  
####  <a name="memory-utilization-after-running-the-workload"></a><a name="Memoryutilizationafterrunningtheworkload"></a> <span data-ttu-id="002f8-484">运行工作负荷之后的内存利用率</span><span class="sxs-lookup"><span data-stu-id="002f8-484">Memory utilization after running the workload</span></span>  
 <span data-ttu-id="002f8-485">插入 1000 万个销售订单之后，总体内存利用率类似于下面这样：</span><span class="sxs-lookup"><span data-stu-id="002f8-485">After insert 10 million sales orders, the all-up memory utilization looks similar to the following:</span></span>  
  
```  
SELECT type  
, name  
, pages_kb/1024 AS pages_MB   
FROM sys.dm_os_memory_clerks WHERE type LIKE '%xtp%'  
```  
  
||||  
|-|-|-|  
|<span data-ttu-id="002f8-486">type</span><span class="sxs-lookup"><span data-stu-id="002f8-486">**type**</span></span>|<span data-ttu-id="002f8-487">name</span><span class="sxs-lookup"><span data-stu-id="002f8-487">**name**</span></span>|<span data-ttu-id="002f8-488">**pages_MB**</span><span class="sxs-lookup"><span data-stu-id="002f8-488">**pages_MB**</span></span>|  
|<span data-ttu-id="002f8-489">MEMORYCLERK_XTP</span><span class="sxs-lookup"><span data-stu-id="002f8-489">MEMORYCLERK_XTP</span></span>|<span data-ttu-id="002f8-490">默认</span><span class="sxs-lookup"><span data-stu-id="002f8-490">Default</span></span>|<span data-ttu-id="002f8-491">146</span><span class="sxs-lookup"><span data-stu-id="002f8-491">146</span></span>|  
|<span data-ttu-id="002f8-492">MEMORYCLERK_XTP</span><span class="sxs-lookup"><span data-stu-id="002f8-492">MEMORYCLERK_XTP</span></span>|<span data-ttu-id="002f8-493">DB_ID_5</span><span class="sxs-lookup"><span data-stu-id="002f8-493">DB_ID_5</span></span>|<span data-ttu-id="002f8-494">7374</span><span class="sxs-lookup"><span data-stu-id="002f8-494">7374</span></span>|  
|<span data-ttu-id="002f8-495">MEMORYCLERK_XTP</span><span class="sxs-lookup"><span data-stu-id="002f8-495">MEMORYCLERK_XTP</span></span>|<span data-ttu-id="002f8-496">默认</span><span class="sxs-lookup"><span data-stu-id="002f8-496">Default</span></span>|<span data-ttu-id="002f8-497">0</span><span class="sxs-lookup"><span data-stu-id="002f8-497">0</span></span>|  
|<span data-ttu-id="002f8-498">MEMORYCLERK_XTP</span><span class="sxs-lookup"><span data-stu-id="002f8-498">MEMORYCLERK_XTP</span></span>|<span data-ttu-id="002f8-499">默认</span><span class="sxs-lookup"><span data-stu-id="002f8-499">Default</span></span>|<span data-ttu-id="002f8-500">0</span><span class="sxs-lookup"><span data-stu-id="002f8-500">0</span></span>|  
  
 <span data-ttu-id="002f8-501">可以看到， [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 将稍小于 8GB 的大小用于示例数据库中的内存优化表和索引。</span><span class="sxs-lookup"><span data-stu-id="002f8-501">As you can see, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] is using a bit under 8GB for the memory-optimized tables and indexes in the sample database.</span></span>  
  
 <span data-ttu-id="002f8-502">在一次示例运行之后查看每个表的详细内存使用率：</span><span class="sxs-lookup"><span data-stu-id="002f8-502">Looking at the detailed memory usage per table after one example run:</span></span>  
  
```  
SELECT object_name(t.object_id) AS [Table Name]  
     , memory_allocated_for_table_kb  
 , memory_allocated_for_indexes_kb  
FROM sys.dm_db_xtp_table_memory_stats dms JOIN sys.tables t   
ON dms.object_id=t.object_id  
WHERE t.type='U'  
```  
  
||||  
|-|-|-|  
|<span data-ttu-id="002f8-503">**表名**</span><span class="sxs-lookup"><span data-stu-id="002f8-503">**Table Name**</span></span>|<span data-ttu-id="002f8-504">**memory_allocated_for_table_kb**</span><span class="sxs-lookup"><span data-stu-id="002f8-504">**memory_allocated_for_table_kb**</span></span>|<span data-ttu-id="002f8-505">**memory_allocated_for_indexes_kb**</span><span class="sxs-lookup"><span data-stu-id="002f8-505">**memory_allocated_for_indexes_kb**</span></span>|  
|<span data-ttu-id="002f8-506">SalesOrderDetail_inmem</span><span class="sxs-lookup"><span data-stu-id="002f8-506">SalesOrderDetail_inmem</span></span>|<span data-ttu-id="002f8-507">5113761</span><span class="sxs-lookup"><span data-stu-id="002f8-507">5113761</span></span>|<span data-ttu-id="002f8-508">663552</span><span class="sxs-lookup"><span data-stu-id="002f8-508">663552</span></span>|  
|<span data-ttu-id="002f8-509">DemoSalesOrderDetailSeed</span><span class="sxs-lookup"><span data-stu-id="002f8-509">DemoSalesOrderDetailSeed</span></span>|<span data-ttu-id="002f8-510">64</span><span class="sxs-lookup"><span data-stu-id="002f8-510">64</span></span>|<span data-ttu-id="002f8-511">10368</span><span class="sxs-lookup"><span data-stu-id="002f8-511">10368</span></span>|  
|<span data-ttu-id="002f8-512">SpecialOffer_inmem</span><span class="sxs-lookup"><span data-stu-id="002f8-512">SpecialOffer_inmem</span></span>|<span data-ttu-id="002f8-513">2</span><span class="sxs-lookup"><span data-stu-id="002f8-513">2</span></span>|<span data-ttu-id="002f8-514">8192</span><span class="sxs-lookup"><span data-stu-id="002f8-514">8192</span></span>|  
|<span data-ttu-id="002f8-515">SalesOrderHeader_inmem</span><span class="sxs-lookup"><span data-stu-id="002f8-515">SalesOrderHeader_inmem</span></span>|<span data-ttu-id="002f8-516">1575679</span><span class="sxs-lookup"><span data-stu-id="002f8-516">1575679</span></span>|<span data-ttu-id="002f8-517">147456</span><span class="sxs-lookup"><span data-stu-id="002f8-517">147456</span></span>|  
|<span data-ttu-id="002f8-518">Product_inmem</span><span class="sxs-lookup"><span data-stu-id="002f8-518">Product_inmem</span></span>|<span data-ttu-id="002f8-519">111</span><span class="sxs-lookup"><span data-stu-id="002f8-519">111</span></span>|<span data-ttu-id="002f8-520">12032</span><span class="sxs-lookup"><span data-stu-id="002f8-520">12032</span></span>|  
|<span data-ttu-id="002f8-521">SpecialOfferProduct_inmem</span><span class="sxs-lookup"><span data-stu-id="002f8-521">SpecialOfferProduct_inmem</span></span>|<span data-ttu-id="002f8-522">64</span><span class="sxs-lookup"><span data-stu-id="002f8-522">64</span></span>|<span data-ttu-id="002f8-523">3712</span><span class="sxs-lookup"><span data-stu-id="002f8-523">3712</span></span>|  
|<span data-ttu-id="002f8-524">DemoSalesOrderHeaderSeed</span><span class="sxs-lookup"><span data-stu-id="002f8-524">DemoSalesOrderHeaderSeed</span></span>|<span data-ttu-id="002f8-525">1984</span><span class="sxs-lookup"><span data-stu-id="002f8-525">1984</span></span>|<span data-ttu-id="002f8-526">5504</span><span class="sxs-lookup"><span data-stu-id="002f8-526">5504</span></span>|  
  
 <span data-ttu-id="002f8-527">可以看到共有约 6.5GB 的数据。</span><span class="sxs-lookup"><span data-stu-id="002f8-527">We can see a total of about 6.5GB of data.</span></span> <span data-ttu-id="002f8-528">请注意，表 SalesOrderHeader_inmem 和 SalesOrderDetail_inmem 上的索引大小与插入销售订单之前的索引大小相同。</span><span class="sxs-lookup"><span data-stu-id="002f8-528">Notice that the size of the indexes on the table SalesOrderHeader_inmem and SalesOrderDetail_inmem is the same as the size of the indexes before inserting the sales orders.</span></span> <span data-ttu-id="002f8-529">索引大小未更改是因为这两个表都使用哈希索引，而哈希索引是静态的。</span><span class="sxs-lookup"><span data-stu-id="002f8-529">The index size did not change because both tables are using hash indexes, and hash indexes are static.</span></span>  
  
#### <a name="after-demo-reset"></a><span data-ttu-id="002f8-530">演示重置之后</span><span class="sxs-lookup"><span data-stu-id="002f8-530">After demo reset</span></span>  
 <span data-ttu-id="002f8-531">存储过程 Demo.usp_DemoReset 可以用于重置演示。</span><span class="sxs-lookup"><span data-stu-id="002f8-531">The stored procedure Demo.usp_DemoReset can be used to reset the demo.</span></span> <span data-ttu-id="002f8-532">它删除表 SalesOrderHeader_inmem 和 SalesOrderDetail_inmem 中的数据，并对原始表 SalesOrderHeader 和 SalesOrderDetail 中的数据重设种子。</span><span class="sxs-lookup"><span data-stu-id="002f8-532">It deletes the data in the tables SalesOrderHeader_inmem and SalesOrderDetail_inmem, and re-seeds the data from the original tables SalesOrderHeader and SalesOrderDetail.</span></span>  
  
 <span data-ttu-id="002f8-533">现在，即使表中的行已删除，这也不意味着会立即回收内存。</span><span class="sxs-lookup"><span data-stu-id="002f8-533">Now, even though the rows in the tables have been deleted, this does not mean that memory is reclaimed immediately.</span></span> [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="002f8-534">根据需要在后台从内存优化表中的已删除行回收内存。</span><span class="sxs-lookup"><span data-stu-id="002f8-534">reclaims memory from deleted rows in memory-optimized tables in the background, as needed.</span></span> <span data-ttu-id="002f8-535">可以看到，在演示重置之后（系统上没有事务工作负荷），尚未立即回收已删除行的内存：</span><span class="sxs-lookup"><span data-stu-id="002f8-535">You will see that immediately after demo reset, with no transactional workload on the system, memory from deleted rows is not yet reclaimed:</span></span>  
  
```  
SELECT type  
, name  
, pages_kb/1024 AS pages_MB   
FROM sys.dm_os_memory_clerks WHERE type LIKE '%xtp%'  
```  
  
||||  
|-|-|-|  
|<span data-ttu-id="002f8-536">type</span><span class="sxs-lookup"><span data-stu-id="002f8-536">**type**</span></span>|<span data-ttu-id="002f8-537">name</span><span class="sxs-lookup"><span data-stu-id="002f8-537">**name**</span></span>|<span data-ttu-id="002f8-538">**pages_MB**</span><span class="sxs-lookup"><span data-stu-id="002f8-538">**pages_MB**</span></span>|  
|<span data-ttu-id="002f8-539">MEMORYCLERK_XTP</span><span class="sxs-lookup"><span data-stu-id="002f8-539">MEMORYCLERK_XTP</span></span>|<span data-ttu-id="002f8-540">默认</span><span class="sxs-lookup"><span data-stu-id="002f8-540">Default</span></span>|<span data-ttu-id="002f8-541">2261</span><span class="sxs-lookup"><span data-stu-id="002f8-541">2261</span></span>|  
|<span data-ttu-id="002f8-542">MEMORYCLERK_XTP</span><span class="sxs-lookup"><span data-stu-id="002f8-542">MEMORYCLERK_XTP</span></span>|<span data-ttu-id="002f8-543">DB_ID_5</span><span class="sxs-lookup"><span data-stu-id="002f8-543">DB_ID_5</span></span>|<span data-ttu-id="002f8-544">7396</span><span class="sxs-lookup"><span data-stu-id="002f8-544">7396</span></span>|  
|<span data-ttu-id="002f8-545">MEMORYCLERK_XTP</span><span class="sxs-lookup"><span data-stu-id="002f8-545">MEMORYCLERK_XTP</span></span>|<span data-ttu-id="002f8-546">默认</span><span class="sxs-lookup"><span data-stu-id="002f8-546">Default</span></span>|<span data-ttu-id="002f8-547">0</span><span class="sxs-lookup"><span data-stu-id="002f8-547">0</span></span>|  
|<span data-ttu-id="002f8-548">MEMORYCLERK_XTP</span><span class="sxs-lookup"><span data-stu-id="002f8-548">MEMORYCLERK_XTP</span></span>|<span data-ttu-id="002f8-549">默认</span><span class="sxs-lookup"><span data-stu-id="002f8-549">Default</span></span>|<span data-ttu-id="002f8-550">0</span><span class="sxs-lookup"><span data-stu-id="002f8-550">0</span></span>|  
  
 <span data-ttu-id="002f8-551">这是预期行为：事务工作负荷运行时将回收内存。</span><span class="sxs-lookup"><span data-stu-id="002f8-551">This is expected: memory will be reclaimed when the transactional workload is running.</span></span>  
  
 <span data-ttu-id="002f8-552">如果启动演示工作负荷的第二次运行，可以看到内存利用率在开始时下降，因为以前删除的行会进行清理。</span><span class="sxs-lookup"><span data-stu-id="002f8-552">If you start a second run of the demo workload you will see the memory utilization decrease initially, as the previously deleted rows are cleaned up.</span></span> <span data-ttu-id="002f8-553">在某一时刻，内存大小会再次增大，直至工作负荷完成。</span><span class="sxs-lookup"><span data-stu-id="002f8-553">At some point the memory size will increase again, until the workload finishes.</span></span> <span data-ttu-id="002f8-554">演示重置之后插入 1000 万行之后，内存利用率非常类似于第一次运行之后的利用率。</span><span class="sxs-lookup"><span data-stu-id="002f8-554">After inserting 10 million rows after demo reset, the memory utilization will be very similar to the utilization after the first run.</span></span> <span data-ttu-id="002f8-555">例如：</span><span class="sxs-lookup"><span data-stu-id="002f8-555">For example:</span></span>  
  
```  
SELECT type  
, name  
, pages_kb/1024 AS pages_MB   
FROM sys.dm_os_memory_clerks WHERE type LIKE '%xtp%'  
```  
  
||||  
|-|-|-|  
|<span data-ttu-id="002f8-556">type</span><span class="sxs-lookup"><span data-stu-id="002f8-556">**type**</span></span>|<span data-ttu-id="002f8-557">name</span><span class="sxs-lookup"><span data-stu-id="002f8-557">**name**</span></span>|<span data-ttu-id="002f8-558">**pages_MB**</span><span class="sxs-lookup"><span data-stu-id="002f8-558">**pages_MB**</span></span>|  
|<span data-ttu-id="002f8-559">MEMORYCLERK_XTP</span><span class="sxs-lookup"><span data-stu-id="002f8-559">MEMORYCLERK_XTP</span></span>|<span data-ttu-id="002f8-560">默认</span><span class="sxs-lookup"><span data-stu-id="002f8-560">Default</span></span>|<span data-ttu-id="002f8-561">1863</span><span class="sxs-lookup"><span data-stu-id="002f8-561">1863</span></span>|  
|<span data-ttu-id="002f8-562">MEMORYCLERK_XTP</span><span class="sxs-lookup"><span data-stu-id="002f8-562">MEMORYCLERK_XTP</span></span>|<span data-ttu-id="002f8-563">DB_ID_5</span><span class="sxs-lookup"><span data-stu-id="002f8-563">DB_ID_5</span></span>|<span data-ttu-id="002f8-564">7390</span><span class="sxs-lookup"><span data-stu-id="002f8-564">7390</span></span>|  
|<span data-ttu-id="002f8-565">MEMORYCLERK_XTP</span><span class="sxs-lookup"><span data-stu-id="002f8-565">MEMORYCLERK_XTP</span></span>|<span data-ttu-id="002f8-566">默认</span><span class="sxs-lookup"><span data-stu-id="002f8-566">Default</span></span>|<span data-ttu-id="002f8-567">0</span><span class="sxs-lookup"><span data-stu-id="002f8-567">0</span></span>|  
|<span data-ttu-id="002f8-568">MEMORYCLERK_XTP</span><span class="sxs-lookup"><span data-stu-id="002f8-568">MEMORYCLERK_XTP</span></span>|<span data-ttu-id="002f8-569">默认</span><span class="sxs-lookup"><span data-stu-id="002f8-569">Default</span></span>|<span data-ttu-id="002f8-570">0</span><span class="sxs-lookup"><span data-stu-id="002f8-570">0</span></span>|  
  
### <a name="disk-utilization-for-memory-optimized-tables"></a><span data-ttu-id="002f8-571">内存优化表的磁盘利用率</span><span class="sxs-lookup"><span data-stu-id="002f8-571">Disk utilization for memory-optimized tables</span></span>  
 <span data-ttu-id="002f8-572">可以使用查询获得数据库检查点文件在给定时间的总体磁盘上大小：</span><span class="sxs-lookup"><span data-stu-id="002f8-572">The overall on-disk size for the checkpoint files of a database at a given time can be found using the query:</span></span>  
  
```  
SELECT SUM(df.size) * 8 / 1024 AS [On-disk size in MB]  
FROM sys.filegroups f JOIN sys.database_files df   
   ON f.data_space_id=df.data_space_id  
WHERE f.type=N'FX'  
  
```  
  
#### <a name="initial-state"></a><span data-ttu-id="002f8-573">初始状态</span><span class="sxs-lookup"><span data-stu-id="002f8-573">Initial state</span></span>  
 <span data-ttu-id="002f8-574">最初创建示例文件组和示例内存优化表时，会预先创建一些检查点文件，并且系统开始填充这些文件 - 预先创建的检查点文件数取决于系统中的逻辑处理器数。</span><span class="sxs-lookup"><span data-stu-id="002f8-574">When the sample filegroup and sample memory-optimized tables are created initially, a number of checkpoint files are pre-created and the system starts filling the files - the number of checkpoint files pre-created depends on the number of logical processors in the system.</span></span> <span data-ttu-id="002f8-575">因为示例最初非常小，所以预先创建的文件在初始创建之后大部分为空。</span><span class="sxs-lookup"><span data-stu-id="002f8-575">As the sample is initially very small, the pre-created files will be mostly empty after initial create.</span></span>  
  
 <span data-ttu-id="002f8-576">下面是示例在有 16 个逻辑处理器的计算机上的初始磁盘上大小：</span><span class="sxs-lookup"><span data-stu-id="002f8-576">The following shows the initial on-disk size for the sample on a machine with 16 logical processors:</span></span>  
  
```  
SELECT SUM(df.size) * 8 / 1024 AS [On-disk size in MB]  
FROM sys.filegroups f JOIN sys.database_files df   
   ON f.data_space_id=df.data_space_id  
WHERE f.type=N'FX'  
```  
  
||  
|-|  
|<span data-ttu-id="002f8-577">**磁盘上大小 (MB)**</span><span class="sxs-lookup"><span data-stu-id="002f8-577">**On-disk size in MB**</span></span>|  
|<span data-ttu-id="002f8-578">2312</span><span class="sxs-lookup"><span data-stu-id="002f8-578">2312</span></span>|  
  
 <span data-ttu-id="002f8-579">可以看到，检查点文件的磁盘上大小 (2.3GB) 与实际数据大小（接近 30MB）之间存在巨大差异。</span><span class="sxs-lookup"><span data-stu-id="002f8-579">As you can see, there is a big discrepancy between the on-disk size of the checkpoint files, which is 2.3GB, and the actual data size, which is closer to 30MB.</span></span>  
  
 <span data-ttu-id="002f8-580">可以使用以下查询更详细地查看磁盘空间利用率的来源。</span><span class="sxs-lookup"><span data-stu-id="002f8-580">Looking closer at where the disk-space utilization comes from, you can use the following query.</span></span> <span data-ttu-id="002f8-581">此查询返回的磁盘上大小与处于状态 5 (REQUIRED FOR BACKUP/HA)、6 (IN TRANSITION TO TOMBSTONE) 或 7 (TOMBSTONE) 的文件的大小接近。</span><span class="sxs-lookup"><span data-stu-id="002f8-581">The size on disk returned by this query is approximate for files with state in 5 (REQUIRED FOR BACKUP/HA), 6 (IN TRANSITION TO TOMBSTONE), or 7 (TOMBSTONE).</span></span>  
  
```  
SELECT state_desc  
 , file_type_desc  
 , COUNT(*) AS [count]  
 , SUM(CASE  
   WHEN state = 5 AND file_type=0 THEN 128*1024*1024  
   WHEN state = 5 AND file_type=1 THEN 8*1024*1024  
   WHEN state IN (6,7) THEN 68*1024*1024  
   ELSE file_size_in_bytes  
    END) / 1024 / 1024 AS [on-disk size MB]   
FROM sys.dm_db_xtp_checkpoint_files  
GROUP BY state, state_desc, file_type, file_type_desc  
ORDER BY state, file_type  
```  
  
 <span data-ttu-id="002f8-582">对于示例的初始状态，结果类似于下面这样（对于有 16 个逻辑处理器的服务器）：</span><span class="sxs-lookup"><span data-stu-id="002f8-582">For the initial state of the sample, the result will look something like for a server with 16 logical processors:</span></span>  
  
|||||  
|-|-|-|-|  
|<span data-ttu-id="002f8-583">**state_desc**</span><span class="sxs-lookup"><span data-stu-id="002f8-583">**state_desc**</span></span>|<span data-ttu-id="002f8-584">**file_type_desc**</span><span class="sxs-lookup"><span data-stu-id="002f8-584">**file_type_desc**</span></span>|<span data-ttu-id="002f8-585">**计数**</span><span class="sxs-lookup"><span data-stu-id="002f8-585">**count**</span></span>|<span data-ttu-id="002f8-586">**磁盘上大小 (MB)**</span><span class="sxs-lookup"><span data-stu-id="002f8-586">**on-disk size MB**</span></span>|  
|<span data-ttu-id="002f8-587">PRECREATED</span><span class="sxs-lookup"><span data-stu-id="002f8-587">PRECREATED</span></span>|<span data-ttu-id="002f8-588">DATA</span><span class="sxs-lookup"><span data-stu-id="002f8-588">DATA</span></span>|<span data-ttu-id="002f8-589">16</span><span class="sxs-lookup"><span data-stu-id="002f8-589">16</span></span>|<span data-ttu-id="002f8-590">2048</span><span class="sxs-lookup"><span data-stu-id="002f8-590">2048</span></span>|  
|<span data-ttu-id="002f8-591">PRECREATED</span><span class="sxs-lookup"><span data-stu-id="002f8-591">PRECREATED</span></span>|<span data-ttu-id="002f8-592">DELTA</span><span class="sxs-lookup"><span data-stu-id="002f8-592">DELTA</span></span>|<span data-ttu-id="002f8-593">16</span><span class="sxs-lookup"><span data-stu-id="002f8-593">16</span></span>|<span data-ttu-id="002f8-594">128</span><span class="sxs-lookup"><span data-stu-id="002f8-594">128</span></span>|  
|<span data-ttu-id="002f8-595">UNDER CONSTRUCTION</span><span class="sxs-lookup"><span data-stu-id="002f8-595">UNDER CONSTRUCTION</span></span>|<span data-ttu-id="002f8-596">DATA</span><span class="sxs-lookup"><span data-stu-id="002f8-596">DATA</span></span>|<span data-ttu-id="002f8-597">1</span><span class="sxs-lookup"><span data-stu-id="002f8-597">1</span></span>|<span data-ttu-id="002f8-598">128</span><span class="sxs-lookup"><span data-stu-id="002f8-598">128</span></span>|  
|<span data-ttu-id="002f8-599">UNDER CONSTRUCTION</span><span class="sxs-lookup"><span data-stu-id="002f8-599">UNDER CONSTRUCTION</span></span>|<span data-ttu-id="002f8-600">DELTA</span><span class="sxs-lookup"><span data-stu-id="002f8-600">DELTA</span></span>|<span data-ttu-id="002f8-601">1</span><span class="sxs-lookup"><span data-stu-id="002f8-601">1</span></span>|<span data-ttu-id="002f8-602">8</span><span class="sxs-lookup"><span data-stu-id="002f8-602">8</span></span>|  
  
 <span data-ttu-id="002f8-603">可以看到，大部分空间由预先创建的数据和差异文件使用。</span><span class="sxs-lookup"><span data-stu-id="002f8-603">As you can see, most of the space is used by precreated data and delta files.</span></span> [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="002f8-604">为每个逻辑处理器预先创建一对（数据、差异）文件。</span><span class="sxs-lookup"><span data-stu-id="002f8-604">pre-created one pair of (data, delta) files per logical processor.</span></span> <span data-ttu-id="002f8-605">此外，数据文件的预设大小为 128MB，差异文件的预设大小为 8MB，以便更高效地向这些文件插入数据。</span><span class="sxs-lookup"><span data-stu-id="002f8-605">In addition, data files are pre-sized at 128MB, and delta files at 8MB, in order to make inserting data into these files more efficient.</span></span>  
  
 <span data-ttu-id="002f8-606">内存优化表中的实际数据在单个数据文件中。</span><span class="sxs-lookup"><span data-stu-id="002f8-606">The actual data in the memory-optimized tables is in the single data file.</span></span>  
  
#### <a name="after-running-the-workload"></a><span data-ttu-id="002f8-607">运行工作负荷之后</span><span class="sxs-lookup"><span data-stu-id="002f8-607">After running the workload</span></span>  
 <span data-ttu-id="002f8-608">进行插入 1000 万个销售订单的单次测试运行之后，总体磁盘上大小类似于下面这样（对于 16 核测试服务器）：</span><span class="sxs-lookup"><span data-stu-id="002f8-608">After a single test run that inserts 10 million sales orders, the overall on-disk size looks something like this (for a 16-core test server):</span></span>  
  
```  
SELECT SUM(df.size) * 8 / 1024 AS [On-disk size in MB]  
FROM sys.filegroups f JOIN sys.database_files df   
   ON f.data_space_id=df.data_space_id  
WHERE f.type=N'FX'  
```  
  
||  
|-|  
|<span data-ttu-id="002f8-609">**磁盘上大小 (MB)**</span><span class="sxs-lookup"><span data-stu-id="002f8-609">**On-disk size in MB**</span></span>|  
|<span data-ttu-id="002f8-610">8828</span><span class="sxs-lookup"><span data-stu-id="002f8-610">8828</span></span>|  
  
 <span data-ttu-id="002f8-611">磁盘上大小接近 9GB，这接近于数据的内存中大小。</span><span class="sxs-lookup"><span data-stu-id="002f8-611">The on-disk size is close to 9GB, which comes close to the in-memory size of the data.</span></span>  
  
 <span data-ttu-id="002f8-612">更详细地查看各种状态间的检查点文件大小：</span><span class="sxs-lookup"><span data-stu-id="002f8-612">Looking more closely at the sizes of the checkpoint files across the various states:</span></span>  
  
```  
SELECT state_desc  
 , file_type_desc  
 , COUNT(*) AS [count]  
 , SUM(CASE  
   WHEN state = 5 AND file_type=0 THEN 128*1024*1024  
   WHEN state = 5 AND file_type=1 THEN 8*1024*1024  
   WHEN state IN (6,7) THEN 68*1024*1024  
   ELSE file_size_in_bytes  
    END) / 1024 / 1024 AS [on-disk size MB]   
FROM sys.dm_db_xtp_checkpoint_files  
GROUP BY state, state_desc, file_type, file_type_desc  
ORDER BY state, file_type  
```  
  
|||||  
|-|-|-|-|  
|<span data-ttu-id="002f8-613">**state_desc**</span><span class="sxs-lookup"><span data-stu-id="002f8-613">**state_desc**</span></span>|<span data-ttu-id="002f8-614">**file_type_desc**</span><span class="sxs-lookup"><span data-stu-id="002f8-614">**file_type_desc**</span></span>|<span data-ttu-id="002f8-615">**计数**</span><span class="sxs-lookup"><span data-stu-id="002f8-615">**count**</span></span>|<span data-ttu-id="002f8-616">**磁盘上大小 (MB)**</span><span class="sxs-lookup"><span data-stu-id="002f8-616">**on-disk size MB**</span></span>|  
|<span data-ttu-id="002f8-617">PRECREATED</span><span class="sxs-lookup"><span data-stu-id="002f8-617">PRECREATED</span></span>|<span data-ttu-id="002f8-618">DATA</span><span class="sxs-lookup"><span data-stu-id="002f8-618">DATA</span></span>|<span data-ttu-id="002f8-619">16</span><span class="sxs-lookup"><span data-stu-id="002f8-619">16</span></span>|<span data-ttu-id="002f8-620">2048</span><span class="sxs-lookup"><span data-stu-id="002f8-620">2048</span></span>|  
|<span data-ttu-id="002f8-621">PRECREATED</span><span class="sxs-lookup"><span data-stu-id="002f8-621">PRECREATED</span></span>|<span data-ttu-id="002f8-622">DELTA</span><span class="sxs-lookup"><span data-stu-id="002f8-622">DELTA</span></span>|<span data-ttu-id="002f8-623">16</span><span class="sxs-lookup"><span data-stu-id="002f8-623">16</span></span>|<span data-ttu-id="002f8-624">128</span><span class="sxs-lookup"><span data-stu-id="002f8-624">128</span></span>|  
|<span data-ttu-id="002f8-625">UNDER CONSTRUCTION</span><span class="sxs-lookup"><span data-stu-id="002f8-625">UNDER CONSTRUCTION</span></span>|<span data-ttu-id="002f8-626">DATA</span><span class="sxs-lookup"><span data-stu-id="002f8-626">DATA</span></span>|<span data-ttu-id="002f8-627">1</span><span class="sxs-lookup"><span data-stu-id="002f8-627">1</span></span>|<span data-ttu-id="002f8-628">128</span><span class="sxs-lookup"><span data-stu-id="002f8-628">128</span></span>|  
|<span data-ttu-id="002f8-629">UNDER CONSTRUCTION</span><span class="sxs-lookup"><span data-stu-id="002f8-629">UNDER CONSTRUCTION</span></span>|<span data-ttu-id="002f8-630">DELTA</span><span class="sxs-lookup"><span data-stu-id="002f8-630">DELTA</span></span>|<span data-ttu-id="002f8-631">1</span><span class="sxs-lookup"><span data-stu-id="002f8-631">1</span></span>|<span data-ttu-id="002f8-632">8</span><span class="sxs-lookup"><span data-stu-id="002f8-632">8</span></span>|  
  
 <span data-ttu-id="002f8-633">我们仍有 16 对预先创建的文件，准备好在关闭检查点时执行。</span><span class="sxs-lookup"><span data-stu-id="002f8-633">We still have 16 pairs of pre-created files, ready to go as checkpoints are closed.</span></span>  
  
 <span data-ttu-id="002f8-634">有一对尚在构造中，这一对会一直用到关闭当前检查点。</span><span class="sxs-lookup"><span data-stu-id="002f8-634">There is one pair under construction, which is used until the current checkpoint is closed.</span></span> <span data-ttu-id="002f8-635">这一对与活动的检查点文件一起，对于内存中 6.5GB 的数据使用了 6.5GB 的磁盘。</span><span class="sxs-lookup"><span data-stu-id="002f8-635">Along with the active checkpoint files this gives about 6.5GB of disk utilization for 6.5GB of data in memory.</span></span> <span data-ttu-id="002f8-636">请注意，索引不在磁盘上保存，因而在此例中，磁盘上的总体大小小于内存中的大小。</span><span class="sxs-lookup"><span data-stu-id="002f8-636">Recall that indexes are not persisted on disk, and thus the overall size on disk is smaller than the size in memory in this case.</span></span>  
  
#### <a name="after-demo-reset"></a><span data-ttu-id="002f8-637">演示重置之后</span><span class="sxs-lookup"><span data-stu-id="002f8-637">After demo reset</span></span>  
 <span data-ttu-id="002f8-638">演示重置之后，如果系统上没有事务工作负荷，则不会立即回收磁盘空间，并且没有数据库检查点。</span><span class="sxs-lookup"><span data-stu-id="002f8-638">After demo reset, disk space is not reclaimed immediately if there is no transactional workload on the system, and there are not database checkpoints.</span></span> <span data-ttu-id="002f8-639">对于要在其各个阶段中移动并最终丢弃的检查点文件，需要发生一些检查点和日志截断事件，以启动检查点文件合并以及启动垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="002f8-639">For checkpoint files to be moved through their various stages and eventually be discarded, a number of checkpoints and log truncation events need to happen, to initiate merge of checkpoint files, as well as to initiate garbage collection.</span></span> <span data-ttu-id="002f8-640">如果在系统中具有事务工作负荷 [并且在使用完整恢复模式时进行定期日志备份]，则这些事件会自动发生，但是在系统处于空闲时不会自动发生（如演示方案所示）。</span><span class="sxs-lookup"><span data-stu-id="002f8-640">These will happen automatically if you have a transactional workload in the system [and take regular log backups, in case you are using the FULL recovery model], but not when the system is idle, as in a demo scenario.</span></span>  
  
 <span data-ttu-id="002f8-641">在示例中，演示重置之后，可能会出现如下内容</span><span class="sxs-lookup"><span data-stu-id="002f8-641">In the example, after demo reset, you may see something like</span></span>  
  
```  
SELECT SUM(df.size) * 8 / 1024 AS [On-disk size in MB]  
FROM sys.filegroups f JOIN sys.database_files df   
   ON f.data_space_id=df.data_space_id  
WHERE f.type=N'FX'  
```  
  
||  
|-|  
|<span data-ttu-id="002f8-642">**磁盘上大小 (MB)**</span><span class="sxs-lookup"><span data-stu-id="002f8-642">**On-disk size in MB**</span></span>|  
|<span data-ttu-id="002f8-643">11839</span><span class="sxs-lookup"><span data-stu-id="002f8-643">11839</span></span>|  
  
 <span data-ttu-id="002f8-644">差不多 12GB，这显著大于演示重置之前的 9GB。</span><span class="sxs-lookup"><span data-stu-id="002f8-644">At nearly 12GB, this is significantly more than the 9GB we had before the demo reset.</span></span> <span data-ttu-id="002f8-645">这是因为某些检查点文件合并已启动，但是某些合并目标尚未安装，某些合并源文件尚未清理，如下所示：</span><span class="sxs-lookup"><span data-stu-id="002f8-645">This is because some checkpoint file merges have been started, but some of the merge targets have not yet been installed, and some of the merge source files have not yet been cleaned up, as can be seen from the following:</span></span>  
  
```  
SELECT state_desc  
 , file_type_desc  
 , COUNT(*) AS [count]  
 , SUM(CASE  
   WHEN state = 5 AND file_type=0 THEN 128*1024*1024  
   WHEN state = 5 AND file_type=1 THEN 8*1024*1024  
   WHEN state IN (6,7) THEN 68*1024*1024  
   ELSE file_size_in_bytes  
    END) / 1024 / 1024 AS [on-disk size MB]   
FROM sys.dm_db_xtp_checkpoint_files  
GROUP BY state, state_desc, file_type, file_type_desc  
ORDER BY state, file_type  
```  
  
|||||  
|-|-|-|-|  
|<span data-ttu-id="002f8-646">**state_desc**</span><span class="sxs-lookup"><span data-stu-id="002f8-646">**state_desc**</span></span>|<span data-ttu-id="002f8-647">**file_type_desc**</span><span class="sxs-lookup"><span data-stu-id="002f8-647">**file_type_desc**</span></span>|<span data-ttu-id="002f8-648">**计数**</span><span class="sxs-lookup"><span data-stu-id="002f8-648">**count**</span></span>|<span data-ttu-id="002f8-649">**磁盘上大小 (MB)**</span><span class="sxs-lookup"><span data-stu-id="002f8-649">**on-disk size MB**</span></span>|  
|<span data-ttu-id="002f8-650">PRECREATED</span><span class="sxs-lookup"><span data-stu-id="002f8-650">PRECREATED</span></span>|<span data-ttu-id="002f8-651">DATA</span><span class="sxs-lookup"><span data-stu-id="002f8-651">DATA</span></span>|<span data-ttu-id="002f8-652">16</span><span class="sxs-lookup"><span data-stu-id="002f8-652">16</span></span>|<span data-ttu-id="002f8-653">2048</span><span class="sxs-lookup"><span data-stu-id="002f8-653">2048</span></span>|  
|<span data-ttu-id="002f8-654">PRECREATED</span><span class="sxs-lookup"><span data-stu-id="002f8-654">PRECREATED</span></span>|<span data-ttu-id="002f8-655">DELTA</span><span class="sxs-lookup"><span data-stu-id="002f8-655">DELTA</span></span>|<span data-ttu-id="002f8-656">16</span><span class="sxs-lookup"><span data-stu-id="002f8-656">16</span></span>|<span data-ttu-id="002f8-657">128</span><span class="sxs-lookup"><span data-stu-id="002f8-657">128</span></span>|  
|<span data-ttu-id="002f8-658">ACTIVE</span><span class="sxs-lookup"><span data-stu-id="002f8-658">ACTIVE</span></span>|<span data-ttu-id="002f8-659">DATA</span><span class="sxs-lookup"><span data-stu-id="002f8-659">DATA</span></span>|<span data-ttu-id="002f8-660">38</span><span class="sxs-lookup"><span data-stu-id="002f8-660">38</span></span>|<span data-ttu-id="002f8-661">5152</span><span class="sxs-lookup"><span data-stu-id="002f8-661">5152</span></span>|  
|<span data-ttu-id="002f8-662">ACTIVE</span><span class="sxs-lookup"><span data-stu-id="002f8-662">ACTIVE</span></span>|<span data-ttu-id="002f8-663">DELTA</span><span class="sxs-lookup"><span data-stu-id="002f8-663">DELTA</span></span>|<span data-ttu-id="002f8-664">38</span><span class="sxs-lookup"><span data-stu-id="002f8-664">38</span></span>|<span data-ttu-id="002f8-665">1331</span><span class="sxs-lookup"><span data-stu-id="002f8-665">1331</span></span>|  
|<span data-ttu-id="002f8-666">MERGE TARGET</span><span class="sxs-lookup"><span data-stu-id="002f8-666">MERGE TARGET</span></span>|<span data-ttu-id="002f8-667">DATA</span><span class="sxs-lookup"><span data-stu-id="002f8-667">DATA</span></span>|<span data-ttu-id="002f8-668">7</span><span class="sxs-lookup"><span data-stu-id="002f8-668">7</span></span>|<span data-ttu-id="002f8-669">896</span><span class="sxs-lookup"><span data-stu-id="002f8-669">896</span></span>|  
|<span data-ttu-id="002f8-670">MERGE TARGET</span><span class="sxs-lookup"><span data-stu-id="002f8-670">MERGE TARGET</span></span>|<span data-ttu-id="002f8-671">DELTA</span><span class="sxs-lookup"><span data-stu-id="002f8-671">DELTA</span></span>|<span data-ttu-id="002f8-672">7</span><span class="sxs-lookup"><span data-stu-id="002f8-672">7</span></span>|<span data-ttu-id="002f8-673">56</span><span class="sxs-lookup"><span data-stu-id="002f8-673">56</span></span>|  
|<span data-ttu-id="002f8-674">MERGED SOURCE</span><span class="sxs-lookup"><span data-stu-id="002f8-674">MERGED SOURCE</span></span>|<span data-ttu-id="002f8-675">DATA</span><span class="sxs-lookup"><span data-stu-id="002f8-675">DATA</span></span>|<span data-ttu-id="002f8-676">13</span><span class="sxs-lookup"><span data-stu-id="002f8-676">13</span></span>|<span data-ttu-id="002f8-677">1772</span><span class="sxs-lookup"><span data-stu-id="002f8-677">1772</span></span>|  
|<span data-ttu-id="002f8-678">MERGED SOURCE</span><span class="sxs-lookup"><span data-stu-id="002f8-678">MERGED SOURCE</span></span>|<span data-ttu-id="002f8-679">DELTA</span><span class="sxs-lookup"><span data-stu-id="002f8-679">DELTA</span></span>|<span data-ttu-id="002f8-680">13</span><span class="sxs-lookup"><span data-stu-id="002f8-680">13</span></span>|<span data-ttu-id="002f8-681">455</span><span class="sxs-lookup"><span data-stu-id="002f8-681">455</span></span>|  
  
 <span data-ttu-id="002f8-682">事务活动在系统中进行时，合并目标会进行安装，合并源会进行清理。</span><span class="sxs-lookup"><span data-stu-id="002f8-682">Merge targets are installed and merged source are cleaned up as transactional activity happens in the system.</span></span>  
  
 <span data-ttu-id="002f8-683">第二次运行演示工作负荷（演示重置之后插入 1000 万个销售订单）之后，可以看到在第一次运行工作负荷过程中构造的文件已清理。</span><span class="sxs-lookup"><span data-stu-id="002f8-683">After a second run of the demo workload, inserting 10 million sales orders after the demo reset, you will see that the files constructed during the first run of the workload have been cleaned up.</span></span> <span data-ttu-id="002f8-684">如果在工作负荷运行期间多次运行以上查询，则可以查看检查点文件在各个阶段间移动。</span><span class="sxs-lookup"><span data-stu-id="002f8-684">If you run the above query several times while the workload is running, you can see the checkpoint files make their way through the various stages.</span></span>  
  
 <span data-ttu-id="002f8-685">第二次运行工作负荷（插入 1000 万个销售订单）之后，可以看到磁盘利用率非常类似于第一次运行之后的情况（不过不一定相同，因为系统在本质上是动态的）。</span><span class="sxs-lookup"><span data-stu-id="002f8-685">After the second run of the workload insert 10 million sales orders you will see disk utilization very similar to, though not necessarily the same as after the first run, as the system is dynamic in nature.</span></span> <span data-ttu-id="002f8-686">例如：</span><span class="sxs-lookup"><span data-stu-id="002f8-686">For example:</span></span>  
  
```  
SELECT state_desc  
 , file_type_desc  
 , COUNT(*) AS [count]  
 , SUM(CASE  
   WHEN state = 5 AND file_type=0 THEN 128*1024*1024  
   WHEN state = 5 AND file_type=1 THEN 8*1024*1024  
   WHEN state IN (6,7) THEN 68*1024*1024  
   ELSE file_size_in_bytes  
    END) / 1024 / 1024 AS [on-disk size MB]   
FROM sys.dm_db_xtp_checkpoint_files  
GROUP BY state, state_desc, file_type, file_type_desc  
ORDER BY state, file_type  
```  
  
|||||  
|-|-|-|-|  
|<span data-ttu-id="002f8-687">**state_desc**</span><span class="sxs-lookup"><span data-stu-id="002f8-687">**state_desc**</span></span>|<span data-ttu-id="002f8-688">**file_type_desc**</span><span class="sxs-lookup"><span data-stu-id="002f8-688">**file_type_desc**</span></span>|<span data-ttu-id="002f8-689">**计数**</span><span class="sxs-lookup"><span data-stu-id="002f8-689">**count**</span></span>|<span data-ttu-id="002f8-690">**磁盘上大小 (MB)**</span><span class="sxs-lookup"><span data-stu-id="002f8-690">**on-disk size MB**</span></span>|  
|<span data-ttu-id="002f8-691">PRECREATED</span><span class="sxs-lookup"><span data-stu-id="002f8-691">PRECREATED</span></span>|<span data-ttu-id="002f8-692">DATA</span><span class="sxs-lookup"><span data-stu-id="002f8-692">DATA</span></span>|<span data-ttu-id="002f8-693">16</span><span class="sxs-lookup"><span data-stu-id="002f8-693">16</span></span>|<span data-ttu-id="002f8-694">2048</span><span class="sxs-lookup"><span data-stu-id="002f8-694">2048</span></span>|  
|<span data-ttu-id="002f8-695">PRECREATED</span><span class="sxs-lookup"><span data-stu-id="002f8-695">PRECREATED</span></span>|<span data-ttu-id="002f8-696">DELTA</span><span class="sxs-lookup"><span data-stu-id="002f8-696">DELTA</span></span>|<span data-ttu-id="002f8-697">16</span><span class="sxs-lookup"><span data-stu-id="002f8-697">16</span></span>|<span data-ttu-id="002f8-698">128</span><span class="sxs-lookup"><span data-stu-id="002f8-698">128</span></span>|  
|<span data-ttu-id="002f8-699">UNDER CONSTRUCTION</span><span class="sxs-lookup"><span data-stu-id="002f8-699">UNDER CONSTRUCTION</span></span>|<span data-ttu-id="002f8-700">DATA</span><span class="sxs-lookup"><span data-stu-id="002f8-700">DATA</span></span>|<span data-ttu-id="002f8-701">2</span><span class="sxs-lookup"><span data-stu-id="002f8-701">2</span></span>|<span data-ttu-id="002f8-702">268</span><span class="sxs-lookup"><span data-stu-id="002f8-702">268</span></span>|  
|<span data-ttu-id="002f8-703">UNDER CONSTRUCTION</span><span class="sxs-lookup"><span data-stu-id="002f8-703">UNDER CONSTRUCTION</span></span>|<span data-ttu-id="002f8-704">DELTA</span><span class="sxs-lookup"><span data-stu-id="002f8-704">DELTA</span></span>|<span data-ttu-id="002f8-705">2</span><span class="sxs-lookup"><span data-stu-id="002f8-705">2</span></span>|<span data-ttu-id="002f8-706">16</span><span class="sxs-lookup"><span data-stu-id="002f8-706">16</span></span>|  
|<span data-ttu-id="002f8-707">ACTIVE</span><span class="sxs-lookup"><span data-stu-id="002f8-707">ACTIVE</span></span>|<span data-ttu-id="002f8-708">DATA</span><span class="sxs-lookup"><span data-stu-id="002f8-708">DATA</span></span>|<span data-ttu-id="002f8-709">41</span><span class="sxs-lookup"><span data-stu-id="002f8-709">41</span></span>|<span data-ttu-id="002f8-710">5608</span><span class="sxs-lookup"><span data-stu-id="002f8-710">5608</span></span>|  
|<span data-ttu-id="002f8-711">ACTIVE</span><span class="sxs-lookup"><span data-stu-id="002f8-711">ACTIVE</span></span>|<span data-ttu-id="002f8-712">DELTA</span><span class="sxs-lookup"><span data-stu-id="002f8-712">DELTA</span></span>|<span data-ttu-id="002f8-713">41</span><span class="sxs-lookup"><span data-stu-id="002f8-713">41</span></span>|<span data-ttu-id="002f8-714">328</span><span class="sxs-lookup"><span data-stu-id="002f8-714">328</span></span>|  
  
 <span data-ttu-id="002f8-715">在此例中，有两个检查点文件对处于“尚在构造”状态，这意味着多个文件对已变为“尚在构造”状态（可能是因为工作负荷的并发级别较高）。</span><span class="sxs-lookup"><span data-stu-id="002f8-715">In this case, there are two checkpoint file pairs in the 'under construction' state, which means multiple file pairs were moved to the 'under construction' state, likely due to the high level of concurrency in the workload.</span></span> <span data-ttu-id="002f8-716">多个并发线程同时需要一个新文件对，因而将一对从“预先创建”变为“尚在构造”。</span><span class="sxs-lookup"><span data-stu-id="002f8-716">Multiple concurrent threads required a new file pair at the same time, and thus moved a pair from 'precreated' to 'under construction'.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="002f8-717">另请参阅</span><span class="sxs-lookup"><span data-stu-id="002f8-717">See Also</span></span>  
 [<span data-ttu-id="002f8-718">内存中 OLTP（内存中优化）</span><span class="sxs-lookup"><span data-stu-id="002f8-718">In-Memory OLTP &#40;In-Memory Optimization&#41;</span></span>](../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
