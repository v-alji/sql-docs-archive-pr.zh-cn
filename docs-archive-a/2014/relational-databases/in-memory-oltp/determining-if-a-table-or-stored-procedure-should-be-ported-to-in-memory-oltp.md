---
title: 确定表或存储过程是否应移植到内存中 OLTP | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
helpviewer_keywords:
- Analyze, Migrate, Report
- AMR
ms.assetid: c1ef96f1-290d-4952-8369-2f49f27afee2
author: rothja
ms.author: jroth
ms.openlocfilehash: 8e517cff394bc0c813e34763469f75147a0a16c5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586677"
---
# <a name="determining-if-a-table-or-stored-procedure-should-be-ported-to-in-memory-oltp"></a><span data-ttu-id="49ea8-102">确定表或存储过程是否应移植到内存中 OLTP</span><span class="sxs-lookup"><span data-stu-id="49ea8-102">Determining if a Table or Stored Procedure Should Be Ported to In-Memory OLTP</span></span>
  <span data-ttu-id="49ea8-103">中的事务性能收集器 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 可帮助您评估内存中 OLTP 是否将改进数据库应用程序的性能。</span><span class="sxs-lookup"><span data-stu-id="49ea8-103">The transaction performance collector in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] helps you evaluate if In-Memory OLTP will improve your database application's performance.</span></span> <span data-ttu-id="49ea8-104">事务性能分析报告还指示在应用程序中启用内存中 OLTP 所必须完成的工作量。</span><span class="sxs-lookup"><span data-stu-id="49ea8-104">The transaction performance analysis report also indicates how much work you must do to enable In-Memory OLTP in your application.</span></span> <span data-ttu-id="49ea8-105">在你标识了要移植到内存中 OLTP 的基于磁盘的表之后，可以使用 [内存优化顾问](memory-optimization-advisor.md)帮助你迁移表。</span><span class="sxs-lookup"><span data-stu-id="49ea8-105">After you identify a disk-based table to port to In-Memory OLTP, you can use the [Memory Optimization Advisor](memory-optimization-advisor.md), to help you migrate the table.</span></span> <span data-ttu-id="49ea8-106">同样， [Native Compilation Advisor](native-compilation-advisor.md) 帮助您将存储过程移植到本机编译的存储过程。</span><span class="sxs-lookup"><span data-stu-id="49ea8-106">Similarly, the [Native Compilation Advisor](native-compilation-advisor.md) will help you port a stored procedure to a natively compiled stored procedure.</span></span>  
  
 <span data-ttu-id="49ea8-107">本主题讨论如何：</span><span class="sxs-lookup"><span data-stu-id="49ea8-107">This topic will discuss how to:</span></span>  
  
-   <span data-ttu-id="49ea8-108">配置管理数据仓库。</span><span class="sxs-lookup"><span data-stu-id="49ea8-108">Configure Management Data Warehouse.</span></span>  
  
-   <span data-ttu-id="49ea8-109">配置数据收集。</span><span class="sxs-lookup"><span data-stu-id="49ea8-109">Configure data collection.</span></span>  
  
-   <span data-ttu-id="49ea8-110">生成事务性能分析报告以便标识性能至关重要的表和存储过程。</span><span class="sxs-lookup"><span data-stu-id="49ea8-110">Generate transaction performance analysis reports to identify performance-critical tables and stored procedures.</span></span>  
  
 <span data-ttu-id="49ea8-111">有关迁移方法的信息，请参阅 [内存中 OLTP - 常见的工作负荷模式和迁移注意事项](https://msdn.microsoft.com/library/dn673538.aspx)。</span><span class="sxs-lookup"><span data-stu-id="49ea8-111">For information about migration methodologies, see [In-Memory OLTP - Common Workload Patterns and Migration Considerations](https://msdn.microsoft.com/library/dn673538.aspx).</span></span>  
  
 <span data-ttu-id="49ea8-112">事务性能收集器和事务性能分析报告可帮助您完成下列任务：</span><span class="sxs-lookup"><span data-stu-id="49ea8-112">The transaction performance collector and the transaction performance analysis reports help you accomplish the following tasks:</span></span>  
  
-   <span data-ttu-id="49ea8-113">分析工作负荷以确定内存中 OLTP 能否提升性能。</span><span class="sxs-lookup"><span data-stu-id="49ea8-113">Analyze your workload to determine if In-Memory OLTP will improve performance.</span></span> <span data-ttu-id="49ea8-114">事务性能收集器收集并评估工作负荷的性能特征。</span><span class="sxs-lookup"><span data-stu-id="49ea8-114">The transaction performance collector collects and evaluates the performance characteristics of your workload.</span></span> <span data-ttu-id="49ea8-115">.</span><span class="sxs-lookup"><span data-stu-id="49ea8-115">.</span></span> <span data-ttu-id="49ea8-116">之后，事务性能分析报告会建议可从转换到内存中 OLTP 获益最多的表和存储过程。</span><span class="sxs-lookup"><span data-stu-id="49ea8-116">The transaction performance analysis report then recommends tables and stored procedures that would benefit most from conversion to In-Memory OLTP.</span></span>  
  
-   <span data-ttu-id="49ea8-117">帮助您规划和执行到内存中 OLTP 的迁移。</span><span class="sxs-lookup"><span data-stu-id="49ea8-117">Help you plan and execute your migration to In-Memory OLTP.</span></span> <span data-ttu-id="49ea8-118">从基于磁盘的表到内存优化表的迁移路径可能比较费时。</span><span class="sxs-lookup"><span data-stu-id="49ea8-118">The migration path from a disk based table to a memory-optimized table can be time consuming.</span></span> <span data-ttu-id="49ea8-119">内存优化顾问可帮助您找到表中的不兼容之处（必须在将表迁移到内存中 OLTP 之前予以解决）。</span><span class="sxs-lookup"><span data-stu-id="49ea8-119">The Memory-Optimization Advisor helps you identify the incompatibilities in your table that you must remove before moving the table to In-Memory OLTP.</span></span> <span data-ttu-id="49ea8-120">此外，内存优化顾问还可帮助您了解将表迁移到内存优化表会对应用程序产生何种影响。</span><span class="sxs-lookup"><span data-stu-id="49ea8-120">The Memory-Optimization Advisor also helps you understand the impact that the migration of a table to a memory-optimized table will have on your application.</span></span>  
  
     <span data-ttu-id="49ea8-121">在规划到内存中 OLTP 的迁移时，或每当您需要将某些表或存储过程迁移到内存中 OLTP 时，都可了解应用程序是否可从内存中 OLTP 获益。</span><span class="sxs-lookup"><span data-stu-id="49ea8-121">You can see if your application would benefit from In-Memory OLTP, when you want to plan your migration to In-Memory OLTP, and whenever you work to migrate some of your tables and stored procedures to In-Memory OLTP.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="49ea8-122">数据库的性能取决于多种因素，不是所有这些因素都能被事务性能收集器发现和度量。</span><span class="sxs-lookup"><span data-stu-id="49ea8-122">The performance of a database system is dependent on a variety of factors, not all of which the transaction performance collector can observe and measure.</span></span> <span data-ttu-id="49ea8-123">因此，事务性能分析报告不保证实际性能收益会符合其预测（如果作出任何预测）。</span><span class="sxs-lookup"><span data-stu-id="49ea8-123">Therefore, the transaction performance analysis report does not guarantee actual performance gains will match its predictions, if any predictions are made.</span></span>  
  
 <span data-ttu-id="49ea8-124">当你在安装时选择 "**管理工具-基本**" 或 "**管理工具-高级**" 时，会安装事务性能收集器和生成事务性能分析报告的功能 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="49ea8-124">The transaction performance collector and the ability to generate a transaction performance analysis report are installed when you select **Management Tools-Basic** or **Management Tools-Advanced** when you install [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span>  
  
## <a name="best-practices"></a><span data-ttu-id="49ea8-125">最佳方案</span><span class="sxs-lookup"><span data-stu-id="49ea8-125">Best Practices</span></span>  
 <span data-ttu-id="49ea8-126">下面的流程图给出了建议的工作流程。</span><span class="sxs-lookup"><span data-stu-id="49ea8-126">The recommended workflow is illustrated in the following flowchart.</span></span> <span data-ttu-id="49ea8-127">黄色节点表示可选过程：</span><span class="sxs-lookup"><span data-stu-id="49ea8-127">The yellow nodes represent optional procedures:</span></span>  
  
 <span data-ttu-id="49ea8-128">![AMR 工作流](../../database-engine/media/amr-1.gif "AMR 工作流")</span><span class="sxs-lookup"><span data-stu-id="49ea8-128">![AMR workflow](../../database-engine/media/amr-1.gif "AMR workflow")</span></span>  
  
 <span data-ttu-id="49ea8-129">可使用任意方法设立性能基准，包括但不限于使用性能计数器日志或 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 活动监视器。</span><span class="sxs-lookup"><span data-stu-id="49ea8-129">You can use any method to establish a performance baseline, including but not limited to using performance counter logs or the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Activity Monitor.</span></span> <span data-ttu-id="49ea8-130">可在性能基准和比较中使用的信息包括：</span><span class="sxs-lookup"><span data-stu-id="49ea8-130">The information to use in your performance baseline and your comparisons are:</span></span>  
  
-   <span data-ttu-id="49ea8-131"> 的 CPU 占用率。</span><span class="sxs-lookup"><span data-stu-id="49ea8-131">CPU consumption of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="49ea8-132"> 的内存占用率。</span><span class="sxs-lookup"><span data-stu-id="49ea8-132">Memory consumption of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="49ea8-133"> 的 I/O 活动。</span><span class="sxs-lookup"><span data-stu-id="49ea8-133">I/O activity of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="49ea8-134">处理事务时，实例的事务吞吐量。</span><span class="sxs-lookup"><span data-stu-id="49ea8-134">Transaction throughput of the instance while processing transactions.</span></span>  
  
 <span data-ttu-id="49ea8-135">事务性能收集器每 15 分钟捕获数据。</span><span class="sxs-lookup"><span data-stu-id="49ea8-135">The transaction performance collector captures data every 15 minutes.</span></span> <span data-ttu-id="49ea8-136">若要获得稳定的结果，运行事务性能收集器至少 1 小时。</span><span class="sxs-lookup"><span data-stu-id="49ea8-136">To obtain usable results, run the transaction performance collector for at least one hour.</span></span> <span data-ttu-id="49ea8-137">若要获得最佳结果，请根据需要运行尽可能长时间的事务性能收集器，以便捕获针对您的主要情形的数据。</span><span class="sxs-lookup"><span data-stu-id="49ea8-137">To obtain best results, run the transaction performance collector for as much time as needed to capture data for your primary scenarios.</span></span> <span data-ttu-id="49ea8-138">只有在完成数据收集后，才生成事务性能分析报告。</span><span class="sxs-lookup"><span data-stu-id="49ea8-138">Generate a transaction performance analysis report only after you have finished gathering data.</span></span>  
  
 <span data-ttu-id="49ea8-139">将事务性能收集器配置为在生产中在您的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例上运行，并且在您的开发（测试）环境中收集 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例上的数据以便确保最小的系统开销。</span><span class="sxs-lookup"><span data-stu-id="49ea8-139">Configure the transaction performance collector to run on your [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance in production and collect the data on a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance in your development (test) environment to ensure minimum overhead.</span></span> <span data-ttu-id="49ea8-140">有关如何在远程实例上的管理数据仓库数据库中保存数据的信息 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ，请参阅[在远程 SQL Server 实例上配置数据收集](determining-if-a-table-or-stored-procedure-should-be-ported-to-in-memory-oltp.md#xxx)。</span><span class="sxs-lookup"><span data-stu-id="49ea8-140">For information on how to save data in a Management Data Warehouse database on a remote [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance, see [Configure Data Collection on a Remote SQL Server Instance](determining-if-a-table-or-stored-procedure-should-be-ported-to-in-memory-oltp.md#xxx).</span></span>  
  
## <a name="performance-impacts"></a><span data-ttu-id="49ea8-141">性能影响</span><span class="sxs-lookup"><span data-stu-id="49ea8-141">Performance Impacts</span></span>  
 <span data-ttu-id="49ea8-142">事务性能收集器由两个数据收集组构成：</span><span class="sxs-lookup"><span data-stu-id="49ea8-142">The transaction performance collector consists of two data collection sets:</span></span>  
  
-   <span data-ttu-id="49ea8-143">表使用情况分析</span><span class="sxs-lookup"><span data-stu-id="49ea8-143">Table Usage Analysis</span></span>  
  
-   <span data-ttu-id="49ea8-144">存储过程分析</span><span class="sxs-lookup"><span data-stu-id="49ea8-144">Stored Procedure Analysis</span></span>  
  
 <span data-ttu-id="49ea8-145">事务性能收集器的收集组每 15 分钟从三个动态管理视图 (DMV) 设置收集数据，并且将数据上载到配置为充当管理数据仓库的数据库。</span><span class="sxs-lookup"><span data-stu-id="49ea8-145">The collection sets collect data from three dynamic management views (DMV) every fifteen minutes, and upload the data to the database configured to act as the Management Data Warehouse.</span></span> <span data-ttu-id="49ea8-146">上载收集的数据会产生最小的性能影响。</span><span class="sxs-lookup"><span data-stu-id="49ea8-146">Uploading the collected data incurs minimal performance impact.</span></span>  
  
## <a name="use-the-transaction-performance-collector"></a><span data-ttu-id="49ea8-147">使用事务性能收集器</span><span class="sxs-lookup"><span data-stu-id="49ea8-147">Use the Transaction Performance Collector</span></span>  
 <span data-ttu-id="49ea8-148">以下步骤需要 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]（包含在 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 中）。</span><span class="sxs-lookup"><span data-stu-id="49ea8-148">The following steps require [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="49ea8-149">不要在探查期间更改架构（例如，添加或删除数据库或创建或删除表）。</span><span class="sxs-lookup"><span data-stu-id="49ea8-149">Do not change the schema (for example, add or remove databases or create or drop tables) during profiling.</span></span> <span data-ttu-id="49ea8-150">如果您在收集数据时更改数据库的架构，则报告中可能不会准确地包含该数据库。</span><span class="sxs-lookup"><span data-stu-id="49ea8-150">If you change the schema of a database while collecting data, the database may not be accurately included in the report.</span></span>  
  
### <a name="configure-management-data-warehouse"></a><span data-ttu-id="49ea8-151">配置管理数据仓库</span><span class="sxs-lookup"><span data-stu-id="49ea8-151">Configure Management Data Warehouse</span></span>  
 <span data-ttu-id="49ea8-152">必须配置管理数据仓库以便使用事务性能收集器。</span><span class="sxs-lookup"><span data-stu-id="49ea8-152">Management Data Warehouse must be configured to use the transaction performance collector.</span></span>  
  
 <span data-ttu-id="49ea8-153">将对其收集数据的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例（探查对象）的版本应与配置管理数据仓库的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的版本相同，或低于后者。</span><span class="sxs-lookup"><span data-stu-id="49ea8-153">The version of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance that you will collect data on (profile) should be the same version or older than the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] where Management Data Warehouse is configured.</span></span>  
  
1.  <span data-ttu-id="49ea8-154">在对象资源管理器中，展开 **“管理”** 。</span><span class="sxs-lookup"><span data-stu-id="49ea8-154">In Object Explorer, expand **Management**.</span></span>  
  
2.  <span data-ttu-id="49ea8-155">右键单击 "**数据收集**" 并选择 "**任务**"，然后**配置 "管理数据仓库**"。</span><span class="sxs-lookup"><span data-stu-id="49ea8-155">Right click **Data Collection** and select **Tasks** and then **Configure Management Data Warehouse**.</span></span> <span data-ttu-id="49ea8-156">"**配置管理数据仓库向导**" 随即开始。</span><span class="sxs-lookup"><span data-stu-id="49ea8-156">The **Configure Management Data Warehouse Wizard** begins.</span></span>  
  
3.  <span data-ttu-id="49ea8-157">单击 "**下一步**" 以选择将充当管理数据仓库的数据库。</span><span class="sxs-lookup"><span data-stu-id="49ea8-157">Click **Next** to select the database that will act as the Management Data Warehouse.</span></span>  
  
4.  <span data-ttu-id="49ea8-158">单击 "**新建**" 以创建一个新数据库来保存配置文件数据。</span><span class="sxs-lookup"><span data-stu-id="49ea8-158">Click **New** to create a new database to hold the profile data.</span></span> <span data-ttu-id="49ea8-159">数据库创建完成后，在向导中单击 "**下一步**"。</span><span class="sxs-lookup"><span data-stu-id="49ea8-159">After you finish creating the database, click **Next** in the wizard.</span></span>  
  
5.  <span data-ttu-id="49ea8-160">在向导中的下一步，可以添加用户并登录。</span><span class="sxs-lookup"><span data-stu-id="49ea8-160">The next step in the wizard lets you add users and logins.</span></span> <span data-ttu-id="49ea8-161">可以将登录映射到 MDW 实例的角色成员身份。</span><span class="sxs-lookup"><span data-stu-id="49ea8-161">You may map logins to role memberships for the MDW instance.</span></span> <span data-ttu-id="49ea8-162">从本地实例收集数据时无需执行该操作。</span><span class="sxs-lookup"><span data-stu-id="49ea8-162">This is not required to collect data from the local instance.</span></span> <span data-ttu-id="49ea8-163">如果不是从本地实例收集数据，则可将数据库角色成员身份 `mdw_admin` 授予将运行待探查事务的帐户。</span><span class="sxs-lookup"><span data-stu-id="49ea8-163">If you are not collecting data from the local instance, you can grant database role membership `mdw_admin` to the account that will run transactions that will be profiled.</span></span> <span data-ttu-id="49ea8-164">完成后单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="49ea8-164">When done, click **Next**.</span></span>  
  
6.  <span data-ttu-id="49ea8-165">请确保 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 代理正在运行。</span><span class="sxs-lookup"><span data-stu-id="49ea8-165">Make sure that [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent is running.</span></span>  
  
7.  <span data-ttu-id="49ea8-166">在下一个屏幕上，单击 "**完成**" 退出向导。</span><span class="sxs-lookup"><span data-stu-id="49ea8-166">On the next screen, click **Finish** to exit the wizard.</span></span>  
  
### <a name="configure-data-collection-on-a-local-ssnoversion-instance"></a><span data-ttu-id="49ea8-167">在本地 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例上配置数据收集</span><span class="sxs-lookup"><span data-stu-id="49ea8-167">Configure Data Collection on a Local [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Instance</span></span>  
 <span data-ttu-id="49ea8-168">数据收集需要启动 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 代理。</span><span class="sxs-lookup"><span data-stu-id="49ea8-168">Data collection requires [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent to be started.</span></span> <span data-ttu-id="49ea8-169">在一个服务器上，您仅需配置一个数据收集器。</span><span class="sxs-lookup"><span data-stu-id="49ea8-169">You only need to configure one data collector on a server.</span></span>  
  
 <span data-ttu-id="49ea8-170">可以在 SQL Server 2012 或更高版本的上配置数据收集器 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="49ea8-170">A data collector can be configured on a SQL Server 2012 or later version of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="49ea8-171">若要配置数据收集以便上载到同一实例上的管理数据仓库数据库，请执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="49ea8-171">To configure data collection to upload to a Management Data Warehouse database on the same instance,</span></span>  
  
1.  <span data-ttu-id="49ea8-172">在**对象资源管理器**中，展开 "**管理**"。</span><span class="sxs-lookup"><span data-stu-id="49ea8-172">In **Object Explorer**, expand **Management**.</span></span>  
  
2.  <span data-ttu-id="49ea8-173">右键单击 "**数据收集**"，选择 "**任务**"，然后**配置 "数据收集**"。</span><span class="sxs-lookup"><span data-stu-id="49ea8-173">Right click **Data Collection**, select **Tasks**, and then **Configure Data Collection**.</span></span> <span data-ttu-id="49ea8-174">"**配置数据收集向导**" 随即开始。</span><span class="sxs-lookup"><span data-stu-id="49ea8-174">The **Configure Data Collection Wizard** begins.</span></span>  
  
3.  <span data-ttu-id="49ea8-175">单击 "**下一步**" 以选择将收集配置文件数据的数据库。</span><span class="sxs-lookup"><span data-stu-id="49ea8-175">Click **Next** to select the database that will collect the profile data.</span></span>  
  
4.  <span data-ttu-id="49ea8-176">选择当前 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例，然后在该实例上选择管理数据仓库数据库。</span><span class="sxs-lookup"><span data-stu-id="49ea8-176">Select the current [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance and a Management Data Warehouse database on that instance.</span></span>  
  
5.  <span data-ttu-id="49ea8-177">在标记为 "**选择要启用的数据收集器集**" 的框中，选择 "**事务性能收集组**"。</span><span class="sxs-lookup"><span data-stu-id="49ea8-177">In the box labeled **Select data collector sets you want to enable**, select **Transaction Performance Collection Sets**.</span></span> <span data-ttu-id="49ea8-178">操作完成后，单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="49ea8-178">Click **Next** when done.</span></span>  
  
6.  <span data-ttu-id="49ea8-179">验证所做的选择。</span><span class="sxs-lookup"><span data-stu-id="49ea8-179">Verify the selections.</span></span> <span data-ttu-id="49ea8-180">单击 "**上一步**" 以修改设置。</span><span class="sxs-lookup"><span data-stu-id="49ea8-180">Click **Back** to modify the settings.</span></span> <span data-ttu-id="49ea8-181">完成操作后，请单击 **“完成”** 。</span><span class="sxs-lookup"><span data-stu-id="49ea8-181">Click **Finish** when done.</span></span>  
  
###  <a name="configure-data-collection-on-a-remote-ssnoversion-instance"></a><a name="xxx"></a><span data-ttu-id="49ea8-182">在远程实例上配置数据收集 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49ea8-182">Configure Data Collection on a Remote [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Instance</span></span>  
 <span data-ttu-id="49ea8-183">数据收集要求在收集该数据的实例上启动 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 代理。</span><span class="sxs-lookup"><span data-stu-id="49ea8-183">Data collection requires [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent to be started on the instance that will collect the data.</span></span>  
  
 <span data-ttu-id="49ea8-184">可以在 SQL Server 2012 或更高版本的上配置数据收集器 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="49ea8-184">A data collector can be configured on a SQL Server 2012 or later version of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="49ea8-185">需要使用用于数据收集器的正确凭据建立 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 代理，以便将数据上载到其他实例（非待探查事务所在实例）上的管理数据仓库数据库。</span><span class="sxs-lookup"><span data-stu-id="49ea8-185">You need a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent proxy established with the correct credential for a data collector to upload data to a Management Data Warehouse database on an instance that is different from where transactions will be profiled.</span></span> <span data-ttu-id="49ea8-186">若要启用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 代理，必须首先使用启用域的登录建立凭据。</span><span class="sxs-lookup"><span data-stu-id="49ea8-186">To enable a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent proxy, you must first establish a credential with a domain-enabled login.</span></span> <span data-ttu-id="49ea8-187">该启用域的登录必须是管理数据仓库数据库的 `mdw_admin` 组的成员。</span><span class="sxs-lookup"><span data-stu-id="49ea8-187">The domain-enabled login must be a member of `mdw_admin` group for the Management Data Warehouse database.</span></span> <span data-ttu-id="49ea8-188">有关如何创建凭据的信息，请参阅[如何：创建凭据 (SQL Server Management Studio) ](../security/authentication-access/create-a-credential.md) 。</span><span class="sxs-lookup"><span data-stu-id="49ea8-188">See [How to: Create a Credential (SQL Server Management Studio)](../security/authentication-access/create-a-credential.md) for information on how to create a credential.</span></span>  
  
 <span data-ttu-id="49ea8-189">若要配置数据收集以便上载到不同实例上的管理数据仓库数据库，请执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="49ea8-189">To configure data collection to upload to a Management Data Warehouse database on a different instance,</span></span>  
  
1.  <span data-ttu-id="49ea8-190">在包含要迁移到内存中 OLTP 的基于磁盘的对象的实例上，展开对象资源管理器中的 "**管理**" 节点。</span><span class="sxs-lookup"><span data-stu-id="49ea8-190">On the instance that contains the disk-based objects that you want to migrate to In-Memory OLTP, expand the **Management** node in Object Explorer.</span></span>  
  
2.  <span data-ttu-id="49ea8-191">右键单击 "**数据收集**"，然后选择 "**任务**"，然后**配置 "数据收集**"。</span><span class="sxs-lookup"><span data-stu-id="49ea8-191">Right click **Data Collection** and select **Tasks** and then **Configure Data Collection**.</span></span> <span data-ttu-id="49ea8-192">"**配置数据收集向导**" 随即开始。</span><span class="sxs-lookup"><span data-stu-id="49ea8-192">The **Configure Data Collection Wizard** begins.</span></span>  
  
3.  <span data-ttu-id="49ea8-193">单击 "**下一步**" 以选择将收集配置文件数据的数据库。</span><span class="sxs-lookup"><span data-stu-id="49ea8-193">Click **Next** to select the database that will collect the profile data.</span></span>  
  
4.  <span data-ttu-id="49ea8-194">确保管理数据仓库数据库在其他 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例上存在。</span><span class="sxs-lookup"><span data-stu-id="49ea8-194">Make sure that a Management Data Warehouse database exists on the other [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance.</span></span>  
  
5.  <span data-ttu-id="49ea8-195">选择另一 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例，然后在该实例上选择管理数据仓库数据库。</span><span class="sxs-lookup"><span data-stu-id="49ea8-195">Select another [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance and a Management Data Warehouse database on that instance.</span></span>  
  
     <span data-ttu-id="49ea8-196">将对其收集数据的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例（探查对象）的版本应与配置管理数据仓库的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的版本相同，或低于后者。</span><span class="sxs-lookup"><span data-stu-id="49ea8-196">The version of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance that you will collect data on (profile) should be the same version or older than the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] where Management Data Warehouse is configured.</span></span>  
  
6.  <span data-ttu-id="49ea8-197">在标记为 "**选择要启用的数据收集器集**" 的框中，选择 "**事务性能收集组**"。</span><span class="sxs-lookup"><span data-stu-id="49ea8-197">In the box labeled **Select data collector sets you want to enable**, select **Transaction Performance Collection Sets**.</span></span>  
  
7.  <span data-ttu-id="49ea8-198">选择 "**使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 代理程序代理进行远程上载**"。</span><span class="sxs-lookup"><span data-stu-id="49ea8-198">Select **Use a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent proxy for remote uploads**.</span></span>  
  
8.  <span data-ttu-id="49ea8-199">操作完成后，单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="49ea8-199">Click **Next** when done.</span></span>  
  
9. <span data-ttu-id="49ea8-200">选择代理。</span><span class="sxs-lookup"><span data-stu-id="49ea8-200">Select the proxy.</span></span>  
  
     <span data-ttu-id="49ea8-201">如果要创建新的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 代理的代理帐户，请执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="49ea8-201">If you want to create a new [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent proxy,</span></span>  
  
    1.  <span data-ttu-id="49ea8-202">单击 "**新建**" 以显示 "**新建代理帐户**" 对话框。</span><span class="sxs-lookup"><span data-stu-id="49ea8-202">Click **New** to display the **New Proxy Account** dialog box.</span></span>  
  
    2.  <span data-ttu-id="49ea8-203">在 "**新建代理帐户**" 对话框中，输入代理名称，选择凭据，并选择性地输入说明。</span><span class="sxs-lookup"><span data-stu-id="49ea8-203">In the **New Proxy Account** dialog box, enter the name of the proxy, select the credential, and optionally enter a description.</span></span> <span data-ttu-id="49ea8-204">然后单击 "**主体**"。</span><span class="sxs-lookup"><span data-stu-id="49ea8-204">Then, click **Principals**.</span></span>  
  
    3.  <span data-ttu-id="49ea8-205">单击 "**添加**"，然后选择 " **Msdb**角色"。</span><span class="sxs-lookup"><span data-stu-id="49ea8-205">Click **Add** and select **Msdb** role.</span></span>  
  
    4.  <span data-ttu-id="49ea8-206">选择 `dc_proxy` 并单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="49ea8-206">Select `dc_proxy` and click **OK**.</span></span> <span data-ttu-id="49ea8-207">然后再次单击“确定”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="49ea8-207">Then click **OK** again.</span></span>  
  
     <span data-ttu-id="49ea8-208">选择正确的代理后，单击 "**下一步**"。</span><span class="sxs-lookup"><span data-stu-id="49ea8-208">After the correct proxy is selected, click **Next**.</span></span>  
  
10. <span data-ttu-id="49ea8-209">若要配置系统收集组，请检查**系统收集组**，然后单击 "**下一步**"。</span><span class="sxs-lookup"><span data-stu-id="49ea8-209">To configure System Collection Sets, check **System Collection Sets** and click **Next**.</span></span>  
  
11. <span data-ttu-id="49ea8-210">验证所做的选择。</span><span class="sxs-lookup"><span data-stu-id="49ea8-210">Verify the selections.</span></span> <span data-ttu-id="49ea8-211">单击 "**上一步**" 以修改设置。</span><span class="sxs-lookup"><span data-stu-id="49ea8-211">Click **Back** to modify the settings.</span></span> <span data-ttu-id="49ea8-212">完成后，完成**完成**。</span><span class="sxs-lookup"><span data-stu-id="49ea8-212">Clicck **Finish** when done.</span></span>  
  
 <span data-ttu-id="49ea8-213">数据收集组现已配置完成并运行在实例上。</span><span class="sxs-lookup"><span data-stu-id="49ea8-213">Data collection sets should now be configured and running on your instance.</span></span>  
  
### <a name="generate-reports"></a><span data-ttu-id="49ea8-214">生成报告</span><span class="sxs-lookup"><span data-stu-id="49ea8-214">Generate Reports</span></span>  
 <span data-ttu-id="49ea8-215">您可以通过右键单击管理数据仓库的数据库，然后依次选择 "**报表**"、"**管理数据仓库**"、"**事务性能分析概述**" 来生成事务性能分析报告。</span><span class="sxs-lookup"><span data-stu-id="49ea8-215">You can generate transaction performance analysis reports by right clicking the database of the Management Data Warehouse and selecting **Reports**, then **Management Data Warehouse**, and then **Transaction Performance Analysis Overview**.</span></span>  
  
 <span data-ttu-id="49ea8-216">该报告收集有关工作负荷服务器上的所有用户数据库的信息。</span><span class="sxs-lookup"><span data-stu-id="49ea8-216">The report collects information about all user databases on the workload server.</span></span> <span data-ttu-id="49ea8-217">如果您的管理数据仓库 (MDW) 数据库在本地计算机上，会在报告中看到 MDW 数据库。</span><span class="sxs-lookup"><span data-stu-id="49ea8-217">If your Management Data Warehouse (MDW) database is on the local computer, you will see the MDW database(s) in the report.</span></span>  
  
 <span data-ttu-id="49ea8-218">CPU 时间与占用时间的比值较高的存储过程适合迁移。</span><span class="sxs-lookup"><span data-stu-id="49ea8-218">A stored procedure with high ratio of CPU time to elapsed time is a candidate for migration.</span></span> <span data-ttu-id="49ea8-219">该报告显示所有表引用，因为本机编译的存储过程只能引用内存优化的表，这可能加大迁移成本。</span><span class="sxs-lookup"><span data-stu-id="49ea8-219">The report shows all table references, because natively compiled stored procedures can only reference memory-optimized tables, which can add to the migration cost.</span></span>  
  
 <span data-ttu-id="49ea8-220">表的详细报告包含三个部分：</span><span class="sxs-lookup"><span data-stu-id="49ea8-220">The details report for a table consists of three sections:</span></span>  
  
-   <span data-ttu-id="49ea8-221">扫描统计信息部分</span><span class="sxs-lookup"><span data-stu-id="49ea8-221">Scan Statistics Section</span></span>  
  
     <span data-ttu-id="49ea8-222">本部分包含一个表，其中显示已收集的有关数据库表扫描的统计信息。</span><span class="sxs-lookup"><span data-stu-id="49ea8-222">This section includes a single table that shows the statistics that were collected about scans on the database table.</span></span> <span data-ttu-id="49ea8-223">列包括：</span><span class="sxs-lookup"><span data-stu-id="49ea8-223">The columns are:</span></span>  
  
    -   <span data-ttu-id="49ea8-224">总访问次数百分比。</span><span class="sxs-lookup"><span data-stu-id="49ea8-224">Percent of total accesses.</span></span> <span data-ttu-id="49ea8-225">对此表的扫描和查询次数相对于整个数据库的活动的百分比。</span><span class="sxs-lookup"><span data-stu-id="49ea8-225">The percentage of scans and seeks on this table with respect to the activity of the entire database.</span></span> <span data-ttu-id="49ea8-226">这个比例越高，使用此表的频率相对于数据库中的其他表就越大。</span><span class="sxs-lookup"><span data-stu-id="49ea8-226">The higher this percentage, the more heavily used the table is compared to other tables in the database.</span></span>  
  
    -   <span data-ttu-id="49ea8-227">查找统计数据/范围扫描统计数据。</span><span class="sxs-lookup"><span data-stu-id="49ea8-227">Lookup Statistics/Range Scan Statistics.</span></span> <span data-ttu-id="49ea8-228">此列记录在探查期间对表执行的点查询和范围扫描（索引扫描和表扫描）次数。</span><span class="sxs-lookup"><span data-stu-id="49ea8-228">This column records the number of point lookups and range scans (index scans and table scans) conducted on the table during profiling.</span></span> <span data-ttu-id="49ea8-229">每事务的平均值为估计值。</span><span class="sxs-lookup"><span data-stu-id="49ea8-229">Average per transaction is an estimate.</span></span>  
  
    -   <span data-ttu-id="49ea8-230">互操作提升和本机提升。</span><span class="sxs-lookup"><span data-stu-id="49ea8-230">Interop Gain and Native Gain.</span></span> <span data-ttu-id="49ea8-231">这些列估计在将表转换为内存优化表时，点查询或范围扫描将会获得的性能优势量。</span><span class="sxs-lookup"><span data-stu-id="49ea8-231">These columns estimate the amount of performance benefit a point lookup or range scan would have if the table is converted to a memory-optimized table.</span></span>  
  
-   <span data-ttu-id="49ea8-232">争用统计数据部分</span><span class="sxs-lookup"><span data-stu-id="49ea8-232">Contention Statistics Section</span></span>  
  
     <span data-ttu-id="49ea8-233">本部分包含一个表，其中显示数据库表的争用。</span><span class="sxs-lookup"><span data-stu-id="49ea8-233">This section includes a table that shows contention on the database table.</span></span> <span data-ttu-id="49ea8-234">有关数据库闩锁和锁的详细信息，请参阅[锁定体系结构](https://msdn.microsoft.com/library/aa224738\(v=sql.80\).aspx)。</span><span class="sxs-lookup"><span data-stu-id="49ea8-234">For more information regarding database latches and locks, please see [Locking Architecture](https://msdn.microsoft.com/library/aa224738\(v=sql.80\).aspx).</span></span> <span data-ttu-id="49ea8-235">这些列如下所示：</span><span class="sxs-lookup"><span data-stu-id="49ea8-235">The columns are as follows:</span></span>  
  
    -   <span data-ttu-id="49ea8-236">总等待百分比。</span><span class="sxs-lookup"><span data-stu-id="49ea8-236">Percent of total waits.</span></span> <span data-ttu-id="49ea8-237">此数据库表上闩锁和锁等待数占数据库活动的百分比。</span><span class="sxs-lookup"><span data-stu-id="49ea8-237">The percentage of latch and lock waits on this database table compared to activity of the database.</span></span> <span data-ttu-id="49ea8-238">这个比例越高，使用此表的频率相对于数据库中的其他表就越大。</span><span class="sxs-lookup"><span data-stu-id="49ea8-238">The higher this percentage, the more heavily used the table is compared to other tables in the database.</span></span>  
  
    -   <span data-ttu-id="49ea8-239">闩锁统计信息。</span><span class="sxs-lookup"><span data-stu-id="49ea8-239">Latch Statistics.</span></span> <span data-ttu-id="49ea8-240">这些列记录涉及此表的查询的闩锁等待数。</span><span class="sxs-lookup"><span data-stu-id="49ea8-240">These columns record the number of latch waits for queries involving for this table.</span></span> <span data-ttu-id="49ea8-241">有关闩锁的信息，[请参阅闩锁。](https://msdn.microsoft.com/library/aa224727\(v=SQL.80\).aspx)</span><span class="sxs-lookup"><span data-stu-id="49ea8-241">For information on latches, see [Latching](https://msdn.microsoft.com/library/aa224727\(v=SQL.80\).aspx).</span></span> <span data-ttu-id="49ea8-242">此数值越高，表的闩锁争用就越多。</span><span class="sxs-lookup"><span data-stu-id="49ea8-242">The higher this number, the more latch contention on the table.</span></span>  
  
    -   <span data-ttu-id="49ea8-243">锁定统计信息。</span><span class="sxs-lookup"><span data-stu-id="49ea8-243">Lock Statistics.</span></span> <span data-ttu-id="49ea8-244">这组列记录对此表的查询的页锁定获取和等待次数。</span><span class="sxs-lookup"><span data-stu-id="49ea8-244">This group of columns record the number of page lock acquisitions and waits for queries for this table.</span></span> <span data-ttu-id="49ea8-245">有关锁的详细信息，请参阅[了解 SQL Server 中的锁定](https://msdn.microsoft.com/library/aa213039\(v=SQL.80\).aspx)。</span><span class="sxs-lookup"><span data-stu-id="49ea8-245">For more information on locks, see [Understanding Locking in SQL Server](https://msdn.microsoft.com/library/aa213039\(v=SQL.80\).aspx).</span></span> <span data-ttu-id="49ea8-246">等待越多，对表的锁定争用就越多。</span><span class="sxs-lookup"><span data-stu-id="49ea8-246">The more waits, the more lock contention on the table.</span></span>  
  
-   <span data-ttu-id="49ea8-247">迁移难度部分</span><span class="sxs-lookup"><span data-stu-id="49ea8-247">Migration Difficulties Section</span></span>  
  
     <span data-ttu-id="49ea8-248">本部分包含一个表，其中显示将此数据库表转换为内存优化表的困难程度。</span><span class="sxs-lookup"><span data-stu-id="49ea8-248">This section includes a table that shows the difficulty of converting this database table to a memory-optimized table.</span></span> <span data-ttu-id="49ea8-249">难度等级越高，转换表的难度就越大。</span><span class="sxs-lookup"><span data-stu-id="49ea8-249">A higher difficulty rating indicates more difficultly to convert the table.</span></span> <span data-ttu-id="49ea8-250">若要查看转换此数据库表的详细信息，请使用[内存优化顾问](memory-optimization-advisor.md)。</span><span class="sxs-lookup"><span data-stu-id="49ea8-250">To see details to convert this database table, please use the [Memory Optimization Advisor](memory-optimization-advisor.md).</span></span>  
  
 <span data-ttu-id="49ea8-251">"表详细信息" 报告中的扫描和争用统计信息将从[sys. dm_db_index_operational_stats &#40;transact-sql&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-index-operational-stats-transact-sql)进行收集和聚合。</span><span class="sxs-lookup"><span data-stu-id="49ea8-251">Scan and contention statistics on the table details report is gathered and aggregated from [sys.dm_db_index_operational_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-index-operational-stats-transact-sql).</span></span>  
  
 <span data-ttu-id="49ea8-252">存储过程的详细报告包含两个部分：</span><span class="sxs-lookup"><span data-stu-id="49ea8-252">The details report for a stored procedure consists of two sections:</span></span>  
  
-   <span data-ttu-id="49ea8-253">执行统计信息部分</span><span class="sxs-lookup"><span data-stu-id="49ea8-253">Execution Statistics Section</span></span>  
  
     <span data-ttu-id="49ea8-254">本部分包含一个表，其中显示与已收集的存储过程执行相关的统计信息。</span><span class="sxs-lookup"><span data-stu-id="49ea8-254">This section includes a table that shows the statistics that were collected about the stored procedure's executions.</span></span> <span data-ttu-id="49ea8-255">这些列如下所示：</span><span class="sxs-lookup"><span data-stu-id="49ea8-255">The columns are as follows:</span></span>  
  
    -   <span data-ttu-id="49ea8-256">缓存的时间。</span><span class="sxs-lookup"><span data-stu-id="49ea8-256">Cached Time.</span></span> <span data-ttu-id="49ea8-257">高速缓存此执行计划的时间。</span><span class="sxs-lookup"><span data-stu-id="49ea8-257">The time this execution plan is cached.</span></span> <span data-ttu-id="49ea8-258">如果存储过程删除计划高速缓存并重新输入，这里将有每个缓存的时间。</span><span class="sxs-lookup"><span data-stu-id="49ea8-258">If the stored procedure drops out of the plan cache and re-enters, there will be times for each cache.</span></span>  
  
    -   <span data-ttu-id="49ea8-259">总 CPU 时间。</span><span class="sxs-lookup"><span data-stu-id="49ea8-259">Total CPU Time.</span></span> <span data-ttu-id="49ea8-260">存储过程在探查期间使用的总 CPU 时间。</span><span class="sxs-lookup"><span data-stu-id="49ea8-260">The total CPU time that the stored procedure consumed during profiling.</span></span> <span data-ttu-id="49ea8-261">此数值越高，存储过程使用的 CPU 就越多。</span><span class="sxs-lookup"><span data-stu-id="49ea8-261">The higher this number, the more CPU the stored procedure used.</span></span>  
  
    -   <span data-ttu-id="49ea8-262">总执行时间。</span><span class="sxs-lookup"><span data-stu-id="49ea8-262">Total Execution Time.</span></span> <span data-ttu-id="49ea8-263">存储过程在探查期间使用的执行时间总量。</span><span class="sxs-lookup"><span data-stu-id="49ea8-263">The total amount of execution time the stored procedure used during profiling.</span></span> <span data-ttu-id="49ea8-264">此数值与 CPU 时间之间的差值越高，存储过程使用 CPU 的效率就越低。</span><span class="sxs-lookup"><span data-stu-id="49ea8-264">The higher the difference between this number and the CPU time is, the less efficiently the stored procedure is using the CPU.</span></span>  
  
    -   <span data-ttu-id="49ea8-265">总高速缓存失误数。</span><span class="sxs-lookup"><span data-stu-id="49ea8-265">Total Cache Missed.</span></span> <span data-ttu-id="49ea8-266">探查期间由存储过程执行引起的高速缓存失误数（从物理存储读取）。</span><span class="sxs-lookup"><span data-stu-id="49ea8-266">The number of cache misses (reads from physical storage) that is caused by the stored procedure's executions during profiling.</span></span>  
  
    -   <span data-ttu-id="49ea8-267">执行计数。</span><span class="sxs-lookup"><span data-stu-id="49ea8-267">Execution Count.</span></span> <span data-ttu-id="49ea8-268">在探查期间，此存储过程执行的次数。</span><span class="sxs-lookup"><span data-stu-id="49ea8-268">The number of times this stored procedure executed during profiling.</span></span>  
  
-   <span data-ttu-id="49ea8-269">表引用部分</span><span class="sxs-lookup"><span data-stu-id="49ea8-269">Table References Section</span></span>  
  
     <span data-ttu-id="49ea8-270">本部分包含一个表，其中显示此存储过程引用的那些表。</span><span class="sxs-lookup"><span data-stu-id="49ea8-270">This section includes a table that shows the tables to which this stored procedure refers.</span></span> <span data-ttu-id="49ea8-271">在将存储过程转换为本机编译的存储过程前，所有这些表必须转换为内存优化表，且它们必须位于同一服务器和数据库上。</span><span class="sxs-lookup"><span data-stu-id="49ea8-271">Before converting the stored procedure into a natively compiled stored procedure, all of these tables must be converted to memory-optimized tables, and they must stay on the same server and database.</span></span>  
  
 <span data-ttu-id="49ea8-272">有关存储过程详细信息的执行统计信息，请从[sys.databases&#41;dm_exec_procedure_stats &#40;](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-procedure-stats-transact-sql)收集和聚合。</span><span class="sxs-lookup"><span data-stu-id="49ea8-272">Execution Statistics on the stored procedure details report is gathered and aggregated from [sys.dm_exec_procedure_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-procedure-stats-transact-sql).</span></span> <span data-ttu-id="49ea8-273">这些引用是从[sql_expression_dependencies &#40;transact-sql&#41;](/sql/relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql)获取的。</span><span class="sxs-lookup"><span data-stu-id="49ea8-273">The references are obtained from [sys.sql_expression_dependencies &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql).</span></span>  
  
 <span data-ttu-id="49ea8-274">若要查看有关如何将存储过程转换为本机编译的存储过程的详细信息，请使用[本机编译顾问](native-compilation-advisor.md)。</span><span class="sxs-lookup"><span data-stu-id="49ea8-274">To see details about how to convert a stored procedure to a natively compiled stored procedure, please use the [Native Compilation Advisor](native-compilation-advisor.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49ea8-275">另请参阅</span><span class="sxs-lookup"><span data-stu-id="49ea8-275">See Also</span></span>  
 [<span data-ttu-id="49ea8-276">迁移到内存中 OLTP</span><span class="sxs-lookup"><span data-stu-id="49ea8-276">Migrating to In-Memory OLTP</span></span>](migrating-to-in-memory-oltp.md)  
  
  
