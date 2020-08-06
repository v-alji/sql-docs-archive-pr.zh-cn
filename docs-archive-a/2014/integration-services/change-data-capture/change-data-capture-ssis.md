---
title: 变更数据捕获 (SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- incremental loads [SQL Server change data capture]
- change data capture [SQL Server], Integration Services and
ms.assetid: c4aaba1b-73e5-4187-a97b-61c10069cc5a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 55293d4e2caa4c31cb004a2cdf1cda99769c77e2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691335"
---
# <a name="change-data-capture-ssis"></a><span data-ttu-id="973fb-102">变更数据捕获 (SSIS)</span><span class="sxs-lookup"><span data-stu-id="973fb-102">Change Data Capture (SSIS)</span></span>
  <span data-ttu-id="973fb-103">在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中，变更数据捕获为有效地执行从源表到数据市场和数据仓库的增量加载提供了一种颇有成效的解决方案。</span><span class="sxs-lookup"><span data-stu-id="973fb-103">In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], change data capture offers an effective solution to the challenge of efficiently performing incremental loads from source tables to data marts and data warehouses.</span></span>

## <a name="what-is-change-data-capture"></a><span data-ttu-id="973fb-104">什么是变更数据捕获？</span><span class="sxs-lookup"><span data-stu-id="973fb-104">What is Change Data Capture?</span></span>
 <span data-ttu-id="973fb-105">源表随时间而变化。</span><span class="sxs-lookup"><span data-stu-id="973fb-105">Source tables change over time.</span></span> <span data-ttu-id="973fb-106">基于这些表的数据市场或数据仓库需要反映这些变更。</span><span class="sxs-lookup"><span data-stu-id="973fb-106">A data mart or data warehouse that is based on those tables needs to reflect these changes.</span></span> <span data-ttu-id="973fb-107">但是，定期复制整个源的快照的过程要耗费大量时间和资源。</span><span class="sxs-lookup"><span data-stu-id="973fb-107">However, a process that periodically copies a snapshot of the entire source consumes too much time and resources.</span></span> <span data-ttu-id="973fb-108">而包括时间戳列、触发器或复杂查询在内的其他方法通常会损害性能和增加复杂性。</span><span class="sxs-lookup"><span data-stu-id="973fb-108">Alternate approaches that include timestamp columns, triggers, or complex queries often hurt performance and increase complexity.</span></span> <span data-ttu-id="973fb-109">用户所需要的是结构化的可靠更改数据流，以便使用者可以轻松地将其应用到数据的目标表示形式。</span><span class="sxs-lookup"><span data-stu-id="973fb-109">What is needed is a reliable stream of change data that is structured so that it can easily be applied by consumers to target representations of the data.</span></span> <span data-ttu-id="973fb-110">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中的变更数据捕获提供此种解决方案。</span><span class="sxs-lookup"><span data-stu-id="973fb-110">Change data capture in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] provides this solution.</span></span>

 <span data-ttu-id="973fb-111">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 的变更数据捕获功能捕获应用到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 表的插入、更新和删除活动，并以易于使用的关系格式提供这些变更的详细信息。</span><span class="sxs-lookup"><span data-stu-id="973fb-111">The change data capture feature of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] captures insert, update, and delete activity applied to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tables, and makes the details of the changes available in an easily-consumed, relational format.</span></span> <span data-ttu-id="973fb-112">变更数据捕获所使用的变更表中包含镜像所跟踪源表列结构的列，同时还包含了解逐行发生的变更所需的元数据。</span><span class="sxs-lookup"><span data-stu-id="973fb-112">The change tables used by change data capture contain columns that mirror the column structure of the tracked source tables, along with the metadata needed to understand the changes that have occurred on a row by row basis.</span></span>

> [!NOTE]
>  <span data-ttu-id="973fb-113">并非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]的每个版本中均提供变更数据捕获功能。</span><span class="sxs-lookup"><span data-stu-id="973fb-113">Change data capture is not available in every edition of [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="973fb-114">有关各个版本支持的功能列表 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ，请参阅 SQL Server 2014 的各个[版本支持的功能](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)。</span><span class="sxs-lookup"><span data-stu-id="973fb-114">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>

## <a name="how-change-data-capture-works-in-integration-services"></a><span data-ttu-id="973fb-115">变更数据捕获在集成服务中的工作原理</span><span class="sxs-lookup"><span data-stu-id="973fb-115">How Change Data Capture Works in Integration Services</span></span>
 <span data-ttu-id="973fb-116">[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 包很容易捕获 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 数据库中的更改数据，以便向数据仓库执行有效的增量加载。</span><span class="sxs-lookup"><span data-stu-id="973fb-116">An [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] package can easily harvest the change data in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] databases to perform efficient incremental loads to a data warehouse.</span></span> <span data-ttu-id="973fb-117">但是，在可以使用 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 加载更改数据之前，管理员必须在要从中捕获更改的数据库和表上启用变更数据捕获。</span><span class="sxs-lookup"><span data-stu-id="973fb-117">However, before you can use [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] to load change data, an administrator must enable change data capture on the database and the tables from which you want to capture changes.</span></span> <span data-ttu-id="973fb-118">有关如何在数据库上配置变更数据捕获的详细信息，请参阅[启用和禁用变更数据捕获 (SQL Server)](../../relational-databases/track-changes/enable-and-disable-change-data-capture-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="973fb-118">For more information on how to configure change data capture on a database, see [Enable and Disable Change Data Capture &#40;SQL Server&#41;](../../relational-databases/track-changes/enable-and-disable-change-data-capture-sql-server.md).</span></span>

 <span data-ttu-id="973fb-119">管理员在数据库上启用变更数据捕获后，即可以创建执行变更数据增量加载的包。</span><span class="sxs-lookup"><span data-stu-id="973fb-119">Once an administrator has enabled change data capture on the database, you can create a package that performs an incremental load of the change data.</span></span> <span data-ttu-id="973fb-120">下面的关系图显示的步骤用于创建一个从单表执行增量加载的包：</span><span class="sxs-lookup"><span data-stu-id="973fb-120">The following diagram shows the steps for creating such a package that performs an incremental load from a single table:</span></span>

 <span data-ttu-id="973fb-121">![变更数据捕获包的创建步骤](../media/cdc-package-creation.gif "变更数据捕获包的创建步骤")</span><span class="sxs-lookup"><span data-stu-id="973fb-121">![Change Data Capture Package Creation Steps](../media/cdc-package-creation.gif "Change Data Capture Package Creation Steps")</span></span>

 <span data-ttu-id="973fb-122">如上面的关系图所示，创建执行变更数据的增量加载的包涉及下列步骤：</span><span class="sxs-lookup"><span data-stu-id="973fb-122">As shown in the previous diagram, creating a package that performs an incremental load of changed data involves the following steps:</span></span>

 <span data-ttu-id="973fb-123">**步骤 1：设计控制流** 在包的控制流中，需要定义下列任务：</span><span class="sxs-lookup"><span data-stu-id="973fb-123">**Step 1: Designing the Control Flow** In the control flow in the package, the following tasks need to be defined:</span></span>

-   <span data-ttu-id="973fb-124">计算要检索的源数据更改间隔的起始和结束 `datetime` 值。</span><span class="sxs-lookup"><span data-stu-id="973fb-124">Calculate the starting and ending `datetime` values for the interval of changes to the source data that you want to retrieve.</span></span>

     <span data-ttu-id="973fb-125">若要计算这些值，请使用执行 SQL 任务或包含 `datetime` 函数的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 表达式。</span><span class="sxs-lookup"><span data-stu-id="973fb-125">To calculate these values, use an Execute SQL task or [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] expressions with `datetime` functions.</span></span> <span data-ttu-id="973fb-126">然后将这些端点存储在包变量中以供以后在包中使用。</span><span class="sxs-lookup"><span data-stu-id="973fb-126">You then store these endpoints in package variables for use later in the package.</span></span>

     <span data-ttu-id="973fb-127">**有关详细信息：**  [指定变更数据的间隔](specify-an-interval-of-change-data.md)</span><span class="sxs-lookup"><span data-stu-id="973fb-127">**For more information:**  [Specify an Interval of Change Data](specify-an-interval-of-change-data.md)</span></span>

-   <span data-ttu-id="973fb-128">确定所选间隔内的变更数据是否已准备就绪。</span><span class="sxs-lookup"><span data-stu-id="973fb-128">Determine whether the change data for the selected interval is ready.</span></span> <span data-ttu-id="973fb-129">此步骤是必需的，因为异步捕获进程可能尚未到达所选端点。</span><span class="sxs-lookup"><span data-stu-id="973fb-129">This step is necessary because the asynchronous capture process might not yet have reached the selected endpoint.</span></span>

     <span data-ttu-id="973fb-130">若要确定数据是否已准备就绪，可启动 For 循环容器来延迟执行，直到所选间隔内的更改数据准备就绪（如果需要）。</span><span class="sxs-lookup"><span data-stu-id="973fb-130">To determine whether the data is ready, start with a For Loop container to delay execution, if necessary, until the change data for the selected interval is ready.</span></span> <span data-ttu-id="973fb-131">在循环容器内，使用执行 SQL 任务来查询由变更数据捕获维护的时间映射表。</span><span class="sxs-lookup"><span data-stu-id="973fb-131">Inside the loop container, use an Execute SQL task to query the time mapping tables maintained by change data capture.</span></span> <span data-ttu-id="973fb-132">然后，使用调用 `Thread.Sleep` 方法的脚本任务或通过 `WAITFOR` 语句使用其他执行 SQL 任务来临时延迟对包的执行（如果需要）。</span><span class="sxs-lookup"><span data-stu-id="973fb-132">Then, use a Script task that calls the `Thread.Sleep` method, or another Execute SQL task with a `WAITFOR` statement, to delay the execution of the package temporarily, if necessary.</span></span> <span data-ttu-id="973fb-133">也可以使用其他脚本任务来记录错误情况或超时。</span><span class="sxs-lookup"><span data-stu-id="973fb-133">Optionally, use another Script task to log an error condition or a timeout.</span></span>

     <span data-ttu-id="973fb-134">**有关详细信息：**  [确定变更数据是否已准备就绪](determine-whether-the-change-data-is-ready.md)</span><span class="sxs-lookup"><span data-stu-id="973fb-134">**For more information:**  [Determine Whether the Change Data Is Ready](determine-whether-the-change-data-is-ready.md)</span></span>

-   <span data-ttu-id="973fb-135">准备将用于查询变更数据的查询字符串。</span><span class="sxs-lookup"><span data-stu-id="973fb-135">Prepare the query string that will be used to query for the change data.</span></span>

     <span data-ttu-id="973fb-136">使用脚本任务或执行 SQL 任务汇集将用于查询变更的 SQL 语句。</span><span class="sxs-lookup"><span data-stu-id="973fb-136">Use a Script task or an Execute SQL task to assemble the SQL statement that will be used to query for changes.</span></span>

     <span data-ttu-id="973fb-137">**有关详细信息：**  [准备查询变更数据](prepare-to-query-for-the-change-data.md)</span><span class="sxs-lookup"><span data-stu-id="973fb-137">**For more information:**  [Prepare to Query for the Change Data](prepare-to-query-for-the-change-data.md)</span></span>

 <span data-ttu-id="973fb-138">**步骤2：设置对变更数据的查询**创建将查询数据的表值函数。</span><span class="sxs-lookup"><span data-stu-id="973fb-138">**Step 2: Setting Up the Query for Change Data** Create the table-valued function that will query for the data.</span></span>

 <span data-ttu-id="973fb-139">使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 开发并保存查询。</span><span class="sxs-lookup"><span data-stu-id="973fb-139">Use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to develop and save the query.</span></span>

 <span data-ttu-id="973fb-140">**有关详细信息：**  [检索和了解变更数据](retrieve-and-understand-the-change-data.md)</span><span class="sxs-lookup"><span data-stu-id="973fb-140">**For more information:**  [Retrieve and Understand the Change Data](retrieve-and-understand-the-change-data.md)</span></span>

 <span data-ttu-id="973fb-141">**步骤 3：设计数据流** 在包的数据流中，需要定义下列任务：</span><span class="sxs-lookup"><span data-stu-id="973fb-141">**Step 3: Designing the Data Flow** In the data flow of the package, the following tasks need to be defined:</span></span>

-   <span data-ttu-id="973fb-142">从变更表中检索变更数据。</span><span class="sxs-lookup"><span data-stu-id="973fb-142">Retrieve the change data from the change tables.</span></span>

     <span data-ttu-id="973fb-143">若要检索数据，请使用源组件来查询变更表中在所选间隔内发生的变更。</span><span class="sxs-lookup"><span data-stu-id="973fb-143">To retrieve the data, use a source component to query the change tables for the changes that fall within the selected interval.</span></span> <span data-ttu-id="973fb-144">该源组件调用以前创建的 Transact-SQL 表值函数。</span><span class="sxs-lookup"><span data-stu-id="973fb-144">The source calls a Transact-SQL table-valued function that you must have previously created.</span></span>

     <span data-ttu-id="973fb-145">**有关详细信息：**  [检索和了解变更数据](retrieve-and-understand-the-change-data.md)</span><span class="sxs-lookup"><span data-stu-id="973fb-145">**For more information:**  [Retrieve and Understand the Change Data](retrieve-and-understand-the-change-data.md)</span></span>

-   <span data-ttu-id="973fb-146">将更改拆分为插入、更新和删除进行处理。</span><span class="sxs-lookup"><span data-stu-id="973fb-146">Split the changes into inserts, updates, and deletes for processing.</span></span>

     <span data-ttu-id="973fb-147">若要拆分更改，可使用有条件拆分转换将插入、更新和删除定向到不同的输出，以便于进行适当的处理。</span><span class="sxs-lookup"><span data-stu-id="973fb-147">To split the changes, use a Conditional Split transformation to direct inserts, updates, and deletes to different outputs for appropriate processing.</span></span>

     <span data-ttu-id="973fb-148">**有关详细信息：**  [处理插入、更新和删除](process-inserts-updates-and-deletes.md)</span><span class="sxs-lookup"><span data-stu-id="973fb-148">**For more information:**  [Process Inserts, Updates, and Deletes](process-inserts-updates-and-deletes.md)</span></span>

-   <span data-ttu-id="973fb-149">将插入、删除和更新应用到目标。</span><span class="sxs-lookup"><span data-stu-id="973fb-149">Apply the inserts, deletes, and updates to the destination.</span></span>

     <span data-ttu-id="973fb-150">若要将更改应用到目标，可使用目标组件将插入应用到目标。</span><span class="sxs-lookup"><span data-stu-id="973fb-150">To apply the changes to the destination, use a destination component to apply the inserts to the destination.</span></span> <span data-ttu-id="973fb-151">还可通过参数化的 UPDATE 和 DELETE 语句使用 OLE DB 命令转换，以将更新和删除应用到目标。</span><span class="sxs-lookup"><span data-stu-id="973fb-151">Also, use OLE DB Command transformations with parameterized UPDATE and DELETE statements to apply updates and deletes to the destination.</span></span> <span data-ttu-id="973fb-152">也可使用目标组件应用更新和删除，以便将行保存到临时表中。</span><span class="sxs-lookup"><span data-stu-id="973fb-152">You can also apply updates and deletes by using destination components to save the rows to temporary tables.</span></span> <span data-ttu-id="973fb-153">然后，使用执行 SQL 任务对临时表中的目标执行大容量更新和大容量删除操作。</span><span class="sxs-lookup"><span data-stu-id="973fb-153">Then, use Execute SQL tasks to perform bulk update and bulk delete operations against the destination from the temporary tables.</span></span>

     <span data-ttu-id="973fb-154">**有关详细信息：**  [将变更应用到目标](apply-the-changes-to-the-destination.md)</span><span class="sxs-lookup"><span data-stu-id="973fb-154">**For more information:**  [Apply the Changes to the Destination](apply-the-changes-to-the-destination.md)</span></span>

### <a name="change-data-from-multiple-tables"></a><span data-ttu-id="973fb-155">来自多个表的变更数据</span><span class="sxs-lookup"><span data-stu-id="973fb-155">Change Data from Multiple Tables</span></span>
 <span data-ttu-id="973fb-156">前面的关系图和步骤中介绍的过程涉及从单表进行增量加载。</span><span class="sxs-lookup"><span data-stu-id="973fb-156">The process outlined in the previous diagram and steps involves an incremental load from a single table.</span></span> <span data-ttu-id="973fb-157">当必须从多表执行增量加载时，整个过程是相同的。</span><span class="sxs-lookup"><span data-stu-id="973fb-157">When having to perform an incremental load from multiple tables, the overall process is the same.</span></span> <span data-ttu-id="973fb-158">但是，包的设计需要更改为满足多表处理。</span><span class="sxs-lookup"><span data-stu-id="973fb-158">However, the design of the package needs to be changed to accommodate the processing of multiple tables.</span></span> <span data-ttu-id="973fb-159">有关如何创建从多个表执行增量加载的包的详细信息，请参阅 [执行多个表的增量加载](perform-an-incremental-load-of-multiple-tables.md)。</span><span class="sxs-lookup"><span data-stu-id="973fb-159">For more information on how to create a package that performs an incremental load from multiples tables, see [Perform an Incremental Load of Multiple Tables](perform-an-incremental-load-of-multiple-tables.md).</span></span>

## <a name="samples-of-change-data-capture-packages"></a><span data-ttu-id="973fb-160">变更数据捕获包的示例</span><span class="sxs-lookup"><span data-stu-id="973fb-160">Samples of Change Data Capture Packages</span></span>
 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] <span data-ttu-id="973fb-161">提供了两个示例来演示如何使用包中的变更数据捕获。</span><span class="sxs-lookup"><span data-stu-id="973fb-161">provides two samples that demonstrate how to use change data capture in packages.</span></span> <span data-ttu-id="973fb-162">有关详细信息，请参阅下列主题：</span><span class="sxs-lookup"><span data-stu-id="973fb-162">For more information, see the following topics:</span></span>

-   [<span data-ttu-id="973fb-163">Readme_Change Data Capture for Specified Interval Package Sample（关于指定间隔的变更数据捕获包示例的自述文件）</span><span class="sxs-lookup"><span data-stu-id="973fb-163">Readme_Change Data Capture for Specified Interval Package Sample</span></span>](https://go.microsoft.com/fwlink/?LinkId=133507)

-   [<span data-ttu-id="973fb-164">关于自上次请求以来的变更数据捕获包示例的自述文件</span><span class="sxs-lookup"><span data-stu-id="973fb-164">Readme_Change Data Capture since Last Request Package Sample</span></span>](https://go.microsoft.com/fwlink/?LinkId=133508)

## <a name="related-tasks"></a><span data-ttu-id="973fb-165">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="973fb-165">Related Tasks</span></span>

-   [<span data-ttu-id="973fb-166">指定变更数据的间隔</span><span class="sxs-lookup"><span data-stu-id="973fb-166">Specify an Interval of Change Data</span></span>](specify-an-interval-of-change-data.md)

-   [<span data-ttu-id="973fb-167">确定变更数据是否已准备就绪</span><span class="sxs-lookup"><span data-stu-id="973fb-167">Determine Whether the Change Data Is Ready</span></span>](determine-whether-the-change-data-is-ready.md)

-   [<span data-ttu-id="973fb-168">准备查询变更数据</span><span class="sxs-lookup"><span data-stu-id="973fb-168">Prepare to Query for the Change Data</span></span>](prepare-to-query-for-the-change-data.md)

-   [<span data-ttu-id="973fb-169">创建函数以检索变更数据</span><span class="sxs-lookup"><span data-stu-id="973fb-169">Create the Function to Retrieve the Change Data</span></span>](create-the-function-to-retrieve-the-change-data.md)

-   [<span data-ttu-id="973fb-170">检索和了解变更数据</span><span class="sxs-lookup"><span data-stu-id="973fb-170">Retrieve and Understand the Change Data</span></span>](retrieve-and-understand-the-change-data.md)

-   [<span data-ttu-id="973fb-171">处理插入、更新和删除</span><span class="sxs-lookup"><span data-stu-id="973fb-171">Process Inserts, Updates, and Deletes</span></span>](process-inserts-updates-and-deletes.md)

-   [<span data-ttu-id="973fb-172">将变更应用到目标</span><span class="sxs-lookup"><span data-stu-id="973fb-172">Apply the Changes to the Destination</span></span>](apply-the-changes-to-the-destination.md)

-   [<span data-ttu-id="973fb-173">执行多个表的增量加载</span><span class="sxs-lookup"><span data-stu-id="973fb-173">Perform an Incremental Load of Multiple Tables</span></span>](perform-an-incremental-load-of-multiple-tables.md)

## <a name="related-content"></a><span data-ttu-id="973fb-174">相关内容</span><span class="sxs-lookup"><span data-stu-id="973fb-174">Related Content</span></span>
 <span data-ttu-id="973fb-175">sqlblog.com 上的博客文章 [SSIS 设计模式 - 增量加载](https://go.microsoft.com/fwlink/?LinkId=217679)</span><span class="sxs-lookup"><span data-stu-id="973fb-175">Blog entry, [SSIS Design Pattern - Incremental Load](https://go.microsoft.com/fwlink/?LinkId=217679), on sqlblog.com</span></span>


