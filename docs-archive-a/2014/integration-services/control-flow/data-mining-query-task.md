---
title: 数据挖掘查询任务 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.dataminingquerytask.f1
helpviewer_keywords:
- prediction queries [Integration Services]
- Data Mining Query task [Integration Services]
ms.assetid: f489348c-2008-4f66-8c2c-c07c3029439a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6bb3cea630401f92395e2ca4416c03bcd870c881
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587554"
---
# <a name="data-mining-query-task"></a><span data-ttu-id="1427c-102">数据挖掘查询任务</span><span class="sxs-lookup"><span data-stu-id="1427c-102">Data Mining Query Task</span></span>
  <span data-ttu-id="1427c-103">数据挖掘查询任务根据 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]内置的数据挖掘模型运行预测查询。</span><span class="sxs-lookup"><span data-stu-id="1427c-103">The Data Mining Query task runs prediction queries based on data mining models built in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="1427c-104">预测查询通过使用挖掘模型来创建对新数据的预测。</span><span class="sxs-lookup"><span data-stu-id="1427c-104">The prediction query creates a prediction for new data by using mining models.</span></span> <span data-ttu-id="1427c-105">例如，预测查询可以预测夏季可能销售多少帆板，或生成可能购买帆板的预期客户列表。</span><span class="sxs-lookup"><span data-stu-id="1427c-105">For example, a prediction query can predict how many sailboats are likely to sell during the summer months or generate a list of prospective customers who are likely to buy a sailboat.</span></span>  
  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="1427c-106">提供执行其他商业智能操作的任务，如运行数据定义语言 (DDL) 语句和处理分析对象。</span><span class="sxs-lookup"><span data-stu-id="1427c-106">provides tasks that perform other business intelligence operations, such as running Data Definition Language (DDL) statements and processing analytic objects.</span></span>  
  
 <span data-ttu-id="1427c-107">有关其他商业智能任务的详细信息，请单击下列主题之一：</span><span class="sxs-lookup"><span data-stu-id="1427c-107">For more information about other business intelligence tasks, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="1427c-108">Analysis Services 执行 DDL 任务</span><span class="sxs-lookup"><span data-stu-id="1427c-108">Analysis Services Execute DDL Task</span></span>](analysis-services-execute-ddl-task.md)  
  
-   [<span data-ttu-id="1427c-109">Analysis Services 处理任务</span><span class="sxs-lookup"><span data-stu-id="1427c-109">Analysis Services Processing Task</span></span>](analysis-services-processing-task.md)  
  
## <a name="prediction-queries"></a><span data-ttu-id="1427c-110">预测查询</span><span class="sxs-lookup"><span data-stu-id="1427c-110">Prediction Queries</span></span>  
 <span data-ttu-id="1427c-111">查询是数据挖掘扩展 (DMX) 语句。</span><span class="sxs-lookup"><span data-stu-id="1427c-111">The query is a Data Mining Extensions (DMX) statement.</span></span> <span data-ttu-id="1427c-112">DMX 语言是 SQL 语言的扩展，为对挖掘模型的操作提供支持。</span><span class="sxs-lookup"><span data-stu-id="1427c-112">The DMX language is an extension of the SQL language that provides support for working with mining models.</span></span> <span data-ttu-id="1427c-113">有关如何使用 DMX 语言的详细信息，请参阅[数据挖掘扩展插件 (DMX) 引用](/sql/dmx/data-mining-extensions-dmx-reference)。</span><span class="sxs-lookup"><span data-stu-id="1427c-113">For more information about how to use the DMX language, see [Data Mining Extensions &#40;DMX&#41; Reference](/sql/dmx/data-mining-extensions-dmx-reference).</span></span>  
  
 <span data-ttu-id="1427c-114">该任务可以查询根据同一挖掘结构生成的多个挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="1427c-114">The task can query multiple mining models that are built on the same mining structure.</span></span> <span data-ttu-id="1427c-115">挖掘模型是使用 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 提供的某种数据挖掘算法生成的。</span><span class="sxs-lookup"><span data-stu-id="1427c-115">A mining model is built using one of the data mining algorithms that [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] provides.</span></span> <span data-ttu-id="1427c-116">数据挖掘查询任务引用的挖掘结构可能包含使用不同算法生成的多个挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="1427c-116">The mining structure that the Data Mining Query task references can include multiple mining models, built using different algorithms.</span></span> <span data-ttu-id="1427c-117">有关详细信息，请参阅[挖掘结构（Analysis Services - 数据挖掘）](https://docs.microsoft.com/analysis-services/data-mining/mining-structures-analysis-services-data-mining)和[数据挖掘算法（Analysis Services - 数据挖掘）](https://docs.microsoft.com/analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining)。</span><span class="sxs-lookup"><span data-stu-id="1427c-117">For more information, see [Mining Structures &#40;Analysis Services - Data Mining&#41;](https://docs.microsoft.com/analysis-services/data-mining/mining-structures-analysis-services-data-mining) and [Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](https://docs.microsoft.com/analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining).</span></span>  
  
 <span data-ttu-id="1427c-118">数据挖掘查询任务运行的预测查询可返回单行或数据集结果。</span><span class="sxs-lookup"><span data-stu-id="1427c-118">The prediction query that the Data Mining Query task runs returns a result that is a single row or a data set.</span></span> <span data-ttu-id="1427c-119">返回单行的查询称为单独查询。例如，预测夏季可能销售多少帆船的查询将返回一个数字。</span><span class="sxs-lookup"><span data-stu-id="1427c-119">A query that returns a single row is called a singleton query: for example, the query that predicts how many sailboats will be sold during the summer months returns a number.</span></span> <span data-ttu-id="1427c-120">有关返回单行的预测查询的详细信息，请参阅[数据挖掘查询接口](https://docs.microsoft.com/analysis-services/data-mining/data-mining-query-tools)。</span><span class="sxs-lookup"><span data-stu-id="1427c-120">For more information about prediction queries that return a single row, see [Data Mining Query Interfaces](https://docs.microsoft.com/analysis-services/data-mining/data-mining-query-tools).</span></span>  
  
 <span data-ttu-id="1427c-121">查询结果将保存到表中。</span><span class="sxs-lookup"><span data-stu-id="1427c-121">The query results are saved to tables.</span></span> <span data-ttu-id="1427c-122">如果数据挖掘查询任务指定名称的表已经存在，则任务可以在相同名称后追加数字来创建新表，也可以覆盖表内容。</span><span class="sxs-lookup"><span data-stu-id="1427c-122">If a table with the name that the Data Mining Query task specifies already exists, the task can create a new table, using the same name with a number appended, or it can overwrite the table content.</span></span>  
  
 <span data-ttu-id="1427c-123">如果结果包含嵌套，则在保存前将结果简化。</span><span class="sxs-lookup"><span data-stu-id="1427c-123">If the results include nesting, the result is flattened before it is saved.</span></span> <span data-ttu-id="1427c-124">通过简化结果可将嵌套结果集更改为表。</span><span class="sxs-lookup"><span data-stu-id="1427c-124">Flattening a result changes a nested result set to a table.</span></span> <span data-ttu-id="1427c-125">例如，简化包含 **Customer** 列和 **Product** 嵌套列的嵌套结果时，将在 **Customer** 列中添加行，从而生成包含每个客户的产品数据的表。</span><span class="sxs-lookup"><span data-stu-id="1427c-125">For example, flattening a nested result with a **Customer** column and a nested **Product** column adds rows to the **Customer** column to make a table that includes product data for each customer.</span></span> <span data-ttu-id="1427c-126">例如，购买三个不同产品的客户将形成一个三行的表，每行都重复出现此客户，并在每行中包含不同的产品。</span><span class="sxs-lookup"><span data-stu-id="1427c-126">For example, a customer with three different products becomes a table with three rows, repeating the customer in each row and including a different product in each row.</span></span> <span data-ttu-id="1427c-127">如果省略了 FLATTENED 关键字，则表将只包含 **Customer** 列，而且每个客户只占一行。</span><span class="sxs-lookup"><span data-stu-id="1427c-127">If the FLATTENED keyword is omitted, the table contains only the **Customer** column and only one row per customer.</span></span> <span data-ttu-id="1427c-128">有关详细信息，请参阅 [SELECT (DMX)](/sql/dmx/select-dmx)。</span><span class="sxs-lookup"><span data-stu-id="1427c-128">For more information, see [SELECT &#40;DMX&#41;](/sql/dmx/select-dmx).</span></span>  
  
## <a name="configuration-of-the-data-mining-query-task"></a><span data-ttu-id="1427c-129">配置数据挖掘查询任务</span><span class="sxs-lookup"><span data-stu-id="1427c-129">Configuration of the Data Mining Query Task</span></span>  
 <span data-ttu-id="1427c-130">数据挖掘查询任务需要两个连接。</span><span class="sxs-lookup"><span data-stu-id="1427c-130">The Data Mining Query task requires two connections.</span></span> <span data-ttu-id="1427c-131">第一个连接是 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 连接管理器，连接到 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 的实例或包含挖掘结构和挖掘模型的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 项目。</span><span class="sxs-lookup"><span data-stu-id="1427c-131">The first connection is an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] connection manager that connects either to an instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] or to an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project that contains the mining structure and the mining model.</span></span> <span data-ttu-id="1427c-132">第二个连接是 OLE DB 连接管理器，连接到包含任务要向其写入的表的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 数据库。</span><span class="sxs-lookup"><span data-stu-id="1427c-132">The second connection is an OLE DB connection manager that connects to the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database that contains the table to which the task writes.</span></span> <span data-ttu-id="1427c-133">有关详细信息，请参阅 [Analysis Services Connection Manager](../connection-manager/analysis-services-connection-manager.md) 和 [OLE DB Connection Manager](../connection-manager/ole-db-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="1427c-133">For more information, see [Analysis Services Connection Manager](../connection-manager/analysis-services-connection-manager.md) and [OLE DB Connection Manager](../connection-manager/ole-db-connection-manager.md).</span></span>  
  
 <span data-ttu-id="1427c-134">可以通过 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器或以编程方式来设置属性。</span><span class="sxs-lookup"><span data-stu-id="1427c-134">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="1427c-135">有关可以在 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器中设置的属性的详细信息，请单击下列主题之一：</span><span class="sxs-lookup"><span data-stu-id="1427c-135">For more information about the properties that you can set in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="1427c-136">数据挖掘查询任务编辑器（“挖掘模型”选项卡）</span><span class="sxs-lookup"><span data-stu-id="1427c-136">Data Mining Query Task Editor &#40;Mining Model Tab&#41;</span></span>](../data-mining-query-task-editor-mining-model-tab.md)  
  
-   [<span data-ttu-id="1427c-137">数据挖掘查询任务编辑器（“查询”选项卡）</span><span class="sxs-lookup"><span data-stu-id="1427c-137">Data Mining Query Task Editor &#40;Query Tab&#41;</span></span>](../data-mining-query-task-editor-query-tab.md)  
  
-   [<span data-ttu-id="1427c-138">数据挖掘查询任务编辑器（“输出”选项卡）</span><span class="sxs-lookup"><span data-stu-id="1427c-138">Data Mining Query Task Editor &#40;Output Tab&#41;</span></span>](../data-mining-query-task-editor-output-tab.md)  
  
> [!NOTE]  
>  <span data-ttu-id="1427c-139">数据挖掘查询编辑器没有“表达式”页。</span><span class="sxs-lookup"><span data-stu-id="1427c-139">The Data Mining Query Editor has no Expressions page.</span></span> <span data-ttu-id="1427c-140">它使用 **“属性”** 窗口来访问工具，以便创建和管理数据挖掘查询任务的属性的属性表达式。</span><span class="sxs-lookup"><span data-stu-id="1427c-140">Instead, use the **Properties** window to access the tools for creating and managing property expressions for properties of the Data Mining Query task.</span></span>  
  
 <span data-ttu-id="1427c-141">有关如何在 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器中设置这些属性的详细信息，请单击下列主题：</span><span class="sxs-lookup"><span data-stu-id="1427c-141">For more information about how to set these properties in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="1427c-142">设置任务或容器的属性</span><span class="sxs-lookup"><span data-stu-id="1427c-142">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="programmatic-configuration-of-data-mining-query-task"></a><span data-ttu-id="1427c-143">以编程方式配置数据挖掘查询任务</span><span class="sxs-lookup"><span data-stu-id="1427c-143">Programmatic Configuration of Data Mining Query Task</span></span>  
 <span data-ttu-id="1427c-144">有关以编程方式设置这些属性的详细信息，请单击下列主题之一：</span><span class="sxs-lookup"><span data-stu-id="1427c-144">For more information about programmatically setting these properties, click one of the following topics:</span></span>  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.DMQueryTask.DMQueryTask>  
  
  
