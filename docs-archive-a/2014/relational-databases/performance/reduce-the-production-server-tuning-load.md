---
title: 减轻生产服务器优化负荷 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- overhead [Database Engine Tuning Advisor]
- tuning overhead [SQL Server]
- reducing production server tuning load
- Database Engine Tuning Advisor [SQL Server], test servers
- test servers [Database Engine Tuning Advisor]
- production servers [SQL Server]
- offload tuning overhead [SQL Server]
ms.assetid: bb95ecaf-444a-4771-a625-e0a91c8f0709
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 53a61b17793a50d6b819f7c1684afdc4de4377f4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588480"
---
# <a name="reduce-the-production-server-tuning-load"></a><span data-ttu-id="00135-102">减轻生产服务器优化负荷</span><span class="sxs-lookup"><span data-stu-id="00135-102">Reduce the Production Server Tuning Load</span></span>
  [!INCLUDE[ssDE](../../../includes/ssde-md.md)] <span data-ttu-id="00135-103">优化顾问依赖于查询优化器分析工作负荷并提供优化建议。</span><span class="sxs-lookup"><span data-stu-id="00135-103">Tuning Advisor relies on the query optimizer to analyze a workload and to make tuning recommendations.</span></span> <span data-ttu-id="00135-104">在生产服务器上执行此分析会增加服务器负荷，并且可能会在优化会话过程中影响服务器的性能。</span><span class="sxs-lookup"><span data-stu-id="00135-104">Performing this analysis on the production server adds to the server load and can hurt server performance during the tuning session.</span></span> <span data-ttu-id="00135-105">通过除了使用生产服务器以外，再使用一台测试服务器，可以减小在优化会话过程中对服务器负荷的影响。</span><span class="sxs-lookup"><span data-stu-id="00135-105">You can reduce the impact to the server load during a tuning session by using a test server in addition to the production server.</span></span>

## <a name="how-database-engine-tuning-advisor-uses-a-test-server"></a><span data-ttu-id="00135-106">数据库引擎优化顾问如何使用测试服务器</span><span class="sxs-lookup"><span data-stu-id="00135-106">How Database Engine Tuning Advisor Uses a Test Server</span></span>
 <span data-ttu-id="00135-107">使用测试服务器的传统方法是将所有数据从生产服务器复制到测试服务器，优化测试服务器，然后在生产服务器上实现建议。</span><span class="sxs-lookup"><span data-stu-id="00135-107">The traditional way to use a test server is to copy all of the data from your production server to your test server, tune the test server, and then implement the recommendation on your production server.</span></span> <span data-ttu-id="00135-108">此过程可以消除对生产服务器的性能影响，但这不是最佳解决方案。</span><span class="sxs-lookup"><span data-stu-id="00135-108">This process eliminates the performance impact on your production server, but nevertheless is not the optimal solution.</span></span> <span data-ttu-id="00135-109">例如，将大量数据从生产服务器复制到测试服务器可能消耗大量时间和资源。</span><span class="sxs-lookup"><span data-stu-id="00135-109">For example, copying large amounts of data from the production to the test server can consume substantial amounts of time and resources.</span></span> <span data-ttu-id="00135-110">此外，测试服务器硬件很少像生产服务器中部署的硬件那样功能强大。</span><span class="sxs-lookup"><span data-stu-id="00135-110">In addition, test server hardware is seldom as powerful as the hardware that is deployed for production servers.</span></span> <span data-ttu-id="00135-111">优化进程依赖于查询优化器，而它生成的建议部分依赖于基础硬件。</span><span class="sxs-lookup"><span data-stu-id="00135-111">The tuning process relies on the query optimizer, and the recommendations it generates are based in part on the underlying hardware.</span></span> <span data-ttu-id="00135-112">如果测试服务器的硬件和生产服务器的硬件不相同， [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 优化顾问建议的质量就会降低。</span><span class="sxs-lookup"><span data-stu-id="00135-112">If the test and production server hardware are not identical, the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] Tuning Advisor recommendation quality is diminished.</span></span>

 <span data-ttu-id="00135-113">为避免出现此类问题， [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 优化顾问通过将大部分优化负荷转移到测试服务器来优化生产服务器上的数据库。</span><span class="sxs-lookup"><span data-stu-id="00135-113">To avoid these problems, [!INCLUDE[ssDE](../../../includes/ssde-md.md)] Tuning Advisor tunes a database on a production server by offloading most of the tuning load onto a test server.</span></span> <span data-ttu-id="00135-114">它通过使用生产服务器硬件配置信息，而不是真正地将数据从生产服务器复制到测试服务器，来执行该操作。</span><span class="sxs-lookup"><span data-stu-id="00135-114">It does this by using the production server hardware configuration information and without actually copying the data from the production server to the test server.</span></span> [!INCLUDE[ssDE](../../../includes/ssde-md.md)] <span data-ttu-id="00135-115">优化顾问不会将实际数据从生产服务器复制到测试服务器中。</span><span class="sxs-lookup"><span data-stu-id="00135-115">Tuning Advisor does not copy actual data from the production server to the test server.</span></span> <span data-ttu-id="00135-116">它仅复制元数据和必要的统计信息。</span><span class="sxs-lookup"><span data-stu-id="00135-116">It only copies the metadata and necessary statistics.</span></span>

 <span data-ttu-id="00135-117">下列步骤概要介绍了用于在测试服务器上优化生产数据库的过程：</span><span class="sxs-lookup"><span data-stu-id="00135-117">The following steps outline the process for tuning a production database on a test server:</span></span>

1.  <span data-ttu-id="00135-118">确保两台服务器上都存在要使用测试服务器的用户。</span><span class="sxs-lookup"><span data-stu-id="00135-118">Make sure that the user who wants to use the test server exists on both servers.</span></span>

     <span data-ttu-id="00135-119">开始之前，请确保两台服务器上都存在要使用测试服务器来优化生产服务器上的数据库的用户。</span><span class="sxs-lookup"><span data-stu-id="00135-119">Before you start, make sure that the user who wants to use the test server to tune a database on the production server exists on both servers.</span></span> <span data-ttu-id="00135-120">这就需要您在测试服务器上创建用户及其登录帐户。</span><span class="sxs-lookup"><span data-stu-id="00135-120">This requires that you create the user and his or her login on the test server.</span></span> <span data-ttu-id="00135-121">如果您在两台计算机上都是 **sysadmin** 固定服务器角色成员，将不需要执行此步骤。</span><span class="sxs-lookup"><span data-stu-id="00135-121">If you are a member of the **sysadmin** fixed server role on both computers, this step is not necessary.</span></span>

2.  <span data-ttu-id="00135-122">优化测试服务器上的工作负荷。</span><span class="sxs-lookup"><span data-stu-id="00135-122">Tune the workload on the test server.</span></span>

     <span data-ttu-id="00135-123">若要优化测试服务器上的工作负荷，必须通过 **dta** 命令行实用工具使用 XML 输入文件。</span><span class="sxs-lookup"><span data-stu-id="00135-123">To tune a workload on a test server, you must use an XML input file with the **dta** command-line utility.</span></span> <span data-ttu-id="00135-124">在 XML 输入文件中，在 **TuningOptions** 父元素下使用 **TestServer** 子元素指定测试服务器的名称，并为其他子元素指定值。</span><span class="sxs-lookup"><span data-stu-id="00135-124">In the XML input file, specify the name of your test server with the **TestServer** subelement in addition to specifying the values for the other subelements under the **TuningOptions** parent element.</span></span>

     <span data-ttu-id="00135-125">在优化进程中，数据库引擎优化顾问将在测试服务器上创建 Shell 数据库。</span><span class="sxs-lookup"><span data-stu-id="00135-125">During the tuning process, Database Engine Tuning Advisor creates a shell database on the test server.</span></span> <span data-ttu-id="00135-126">若要创建此 Shell 数据库并对其进行优化，数据库引擎优化顾问需要在下列情况下调用生产服务器：</span><span class="sxs-lookup"><span data-stu-id="00135-126">To create this shell database and tune it, Database Engine Tuning Advisor makes calls to the production server for the following:</span></span>

    1.  [!INCLUDE[ssDE](../../../includes/ssde-md.md)] <span data-ttu-id="00135-127">优化顾问将元数据从生产数据库导入到测试服务器 Shell 数据库。</span><span class="sxs-lookup"><span data-stu-id="00135-127">Tuning Advisor imports metadata from the production database to the test server shell database.</span></span> <span data-ttu-id="00135-128">此元数据包括空表、索引、视图、存储过程和触发器等。</span><span class="sxs-lookup"><span data-stu-id="00135-128">This metadata includes empty tables, indexes, views, stored procedures, triggers, and so on.</span></span> <span data-ttu-id="00135-129">这使得对测试服务器 Shell 数据库执行工作负荷查询成为可能。</span><span class="sxs-lookup"><span data-stu-id="00135-129">This makes it possible for the workload queries to execute against the test server shell database.</span></span>

    2.  [!INCLUDE[ssDE](../../../includes/ssde-md.md)] <span data-ttu-id="00135-130">优化顾问从生产服务器导入统计信息，以便查询优化器可以准确优化对测试服务器的查询。</span><span class="sxs-lookup"><span data-stu-id="00135-130">Tuning Advisor imports statistics from the production server so the query optimizer can accurately optimize queries on the test server.</span></span>

    3.  [!INCLUDE[ssDE](../../../includes/ssde-md.md)] <span data-ttu-id="00135-131">优化顾问从生产服务器导入指定处理器数和可用内存量的硬件参数，为查询优化器提供生成查询计划所需的信息。</span><span class="sxs-lookup"><span data-stu-id="00135-131">Tuning Advisor imports hardware parameters specifying the number of processors and available memory from the production server to provide the query optimizer with the information it needs to generate a query plan.</span></span>

3.  <span data-ttu-id="00135-132">在 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 优化顾问完成优化测试服务器 Shell 数据库后，将生成优化建议。</span><span class="sxs-lookup"><span data-stu-id="00135-132">After [!INCLUDE[ssDE](../../../includes/ssde-md.md)] Tuning Advisor finishes tuning the test server shell database, it generates a tuning recommendation.</span></span>

4.  <span data-ttu-id="00135-133">将通过优化测试服务器得到的建议应用于生产服务器。</span><span class="sxs-lookup"><span data-stu-id="00135-133">Apply the recommendation received from tuning the test server to the production server.</span></span>

 <span data-ttu-id="00135-134">下图显示了测试服务器和生产服务器方案：</span><span class="sxs-lookup"><span data-stu-id="00135-134">The following illustration shows the test server and production server scenario:</span></span>

 <span data-ttu-id="00135-135">![数据库引擎优化顾问测试服务器用法](../../database-engine/media/testsvr.gif "数据库引擎优化顾问测试服务器用法")</span><span class="sxs-lookup"><span data-stu-id="00135-135">![Database Engine Tuning Advisor test server usage](../../database-engine/media/testsvr.gif "Database Engine Tuning Advisor test server usage")</span></span>

> [!NOTE]
>  <span data-ttu-id="00135-136">[!INCLUDE[ssDE](../../../includes/ssde-md.md)] 优化顾问图形用户界面 (GUI) 不支持测试服务器优化功能。</span><span class="sxs-lookup"><span data-stu-id="00135-136">The test server tuning feature is not supported in the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] Tuning Advisor graphical user interface (GUI).</span></span>

## <a name="example"></a><span data-ttu-id="00135-137">示例</span><span class="sxs-lookup"><span data-stu-id="00135-137">Example</span></span>
 <span data-ttu-id="00135-138">首先，请确保测试服务器和生产服务器上都存在要执行优化的用户。</span><span class="sxs-lookup"><span data-stu-id="00135-138">First, make sure that the user who wants to perform the tuning exists on both the test and production servers.</span></span>

 <span data-ttu-id="00135-139">将用户信息复制到测试服务器后，您即可在 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 优化顾问 XML 输入文件中定义测试服务器优化会话。</span><span class="sxs-lookup"><span data-stu-id="00135-139">After the user information is copied over to your test server, you can define your test server tuning session in the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] Tuning Advisor XML input file.</span></span> <span data-ttu-id="00135-140">下面的 XML 输入文件示例演示如何使用 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 优化顾问来指定测试服务器优化数据库。</span><span class="sxs-lookup"><span data-stu-id="00135-140">The following example XML input file illustrates how to specify a test server to tune a database with [!INCLUDE[ssDE](../../../includes/ssde-md.md)] Tuning Advisor.</span></span>

 <span data-ttu-id="00135-141">在此示例中， `MyDatabaseName` 数据库在 `MyServerName`上进行优化。</span><span class="sxs-lookup"><span data-stu-id="00135-141">In this example, the `MyDatabaseName` database is being tuned on `MyServerName`.</span></span> <span data-ttu-id="00135-142">[!INCLUDE[tsql](../../includes/tsql-md.md)] 脚本（即 `MyWorkloadScript.sql`）用作工作负荷。</span><span class="sxs-lookup"><span data-stu-id="00135-142">The [!INCLUDE[tsql](../../includes/tsql-md.md)] script, `MyWorkloadScript.sql`, is used as the workload.</span></span> <span data-ttu-id="00135-143">此工作负荷包含对 `MyDatabaseName`执行的事件。</span><span class="sxs-lookup"><span data-stu-id="00135-143">This workload contains events that execute against `MyDatabaseName`.</span></span> <span data-ttu-id="00135-144">查询优化器对此数据库的大部分调用操作（作为优化进程的一部分发生）是由驻留在 `MyTestServerName`上的 Shell 数据库实现的。</span><span class="sxs-lookup"><span data-stu-id="00135-144">Most of the query optimizer calls to this database, which occur as part of the tuning process, are handled by the shell database that resides on `MyTestServerName`.</span></span> <span data-ttu-id="00135-145">Shell 数据库由元数据和统计信息构成。</span><span class="sxs-lookup"><span data-stu-id="00135-145">The shell database is composed of metadata and statistics.</span></span> <span data-ttu-id="00135-146">此进程会将优化开销转移到测试服务器。</span><span class="sxs-lookup"><span data-stu-id="00135-146">This process results in the tuning overhead being offloaded to the test server.</span></span> <span data-ttu-id="00135-147">[!INCLUDE[ssDE](../../../includes/ssde-md.md)] 优化顾问使用此 XML 输入文件生成其优化建议时，它应只考虑索引 (`<FeatureSet>IDX</FeatureSet>`) 而不考虑分区，并且不需要在 `MyDatabaseName`中保留任何现有的物理设计结构。</span><span class="sxs-lookup"><span data-stu-id="00135-147">When [!INCLUDE[ssDE](../../../includes/ssde-md.md)] Tuning Advisor generates its tuning recommendation using this XML input file, it should consider indexes only (`<FeatureSet>IDX</FeatureSet>`), no partitioning, and need not keep any of the existing physical design structures in `MyDatabaseName`.</span></span>

```
<?xml version="1.0" encoding="utf-16" ?>
<DTAXML xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="https://schemas.microsoft.com/sqlserver/2004/07/dta">
  <DTAInput>
    <Server>
      <Name>MyServerName</Name>
      <Database>
        <Name>MyDatabaseName</Name>
      </Database>
    </Server>
    <Workload>
      <File>MyWorkloadScript.sql</File>
    </Workload>
    <TuningOptions>
      <TestServer>MyTestServerName</TestServer>
      <FeatureSet>IDX</FeatureSet>
      <Partitioning>NONE</Partitioning>
      <KeepExisting>NONE</KeepExisting>
    </TuningOptions>
  </DTAInput>
</DTAXML>
```

## <a name="see-also"></a><span data-ttu-id="00135-148">另请参阅</span><span class="sxs-lookup"><span data-stu-id="00135-148">See Also</span></span>
 <span data-ttu-id="00135-149">[使用测试服务器](considerations-for-using-test-servers.md) [XML 输入文件引用 &#40;数据库引擎优化顾问](database-engine-tuning-advisor.md)的注意事项&#41;</span><span class="sxs-lookup"><span data-stu-id="00135-149">[Considerations for Using Test Servers](considerations-for-using-test-servers.md) [XML Input File Reference &#40;Database Engine Tuning Advisor&#41;](database-engine-tuning-advisor.md)</span></span>


