---
title: 数据挖掘查询接口 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- predictions [Analysis Services], DMX prediction queries
- predictions [DMX]
- DMX [Analysis Services], prediction queries
- prediction queries [DMX]
- predictions [Analysis Services]
- queries [DMX], prediction queries
- mining models [Analysis Services], DMX
ms.assetid: a8952427-fd8c-4300-8f62-25f57ac1be0c
author: minewiskan
ms.author: owend
ms.openlocfilehash: 1702ad82c65b5a7370a62c4bc31a08007f374c9f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591005"
---
# <a name="data-mining-query-interfaces"></a><span data-ttu-id="1318a-102">数据挖掘查询接口</span><span class="sxs-lookup"><span data-stu-id="1318a-102">Data Mining Query Interfaces</span></span>
  <span data-ttu-id="1318a-103">数据挖掘基于数据挖掘扩展插件 (DMX) 语言。</span><span class="sxs-lookup"><span data-stu-id="1318a-103">Data mining queries are based on the Data Mining Extensions (DMX) language.</span></span> <span data-ttu-id="1318a-104">您可以为所有预测和建模任务使用 DMX，这些任务包括分类、风险分析、生成建议和线性回归。</span><span class="sxs-lookup"><span data-stu-id="1318a-104">You use DMX for all prediction and modeling tasks, including classification, risk analysis, generation of recommendations, and linear regression.</span></span> <span data-ttu-id="1318a-105">您还可以检索在处理模型时生成的模式和统计信息。</span><span class="sxs-lookup"><span data-stu-id="1318a-105">You can also retrieve the patterns and statistics that were generated when you processed the model.</span></span>  
  
 <span data-ttu-id="1318a-106">使用 DMX 的预测查询的语法与 [!INCLUDE[tsql](../../includes/tsql-md.md)] 中查询的语法相似。</span><span class="sxs-lookup"><span data-stu-id="1318a-106">The syntax for a prediction query using DMX is similar to the syntax for a query in [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="1318a-107">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 和 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 均提供了有助于生成 DMX 预测查询的工具。</span><span class="sxs-lookup"><span data-stu-id="1318a-107">Both [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] provide tools that help you build DMX prediction queries.</span></span>  
  
 <span data-ttu-id="1318a-108">本主题介绍了您可以使用 DMX 创建和执行数据挖掘查询的接口。</span><span class="sxs-lookup"><span data-stu-id="1318a-108">This topic describes the interfaces that you can use to create and execute data mining queries using DMX.</span></span>  
  
 [<span data-ttu-id="1318a-109">查询工具</span><span class="sxs-lookup"><span data-stu-id="1318a-109">Query Tools</span></span>](#bkmk_Tools)  
  
-   [<span data-ttu-id="1318a-110">预测查询生成器</span><span class="sxs-lookup"><span data-stu-id="1318a-110">Prediction Query Builder</span></span>](#bkmk_Builder)  
  
-   [<span data-ttu-id="1318a-111">查询编辑器</span><span class="sxs-lookup"><span data-stu-id="1318a-111">Query Editor</span></span>](#bkmk_QueryEditor)  
  
-   [<span data-ttu-id="1318a-112">DMX 模板</span><span class="sxs-lookup"><span data-stu-id="1318a-112">DMX Templates</span></span>](#bkmk_Templates)  
  
-   [<span data-ttu-id="1318a-113">Integration Services</span><span class="sxs-lookup"><span data-stu-id="1318a-113">Integration Services</span></span>](#bkmk_SSIS)  
  
 [<span data-ttu-id="1318a-114">应用程序编程接口</span><span class="sxs-lookup"><span data-stu-id="1318a-114">Application Programming Interfaces</span></span>](#bkmk_API)  
  
##  <a name="data-mining-query-tools"></a><a name="bkmk_Tools"></a><span data-ttu-id="1318a-115">数据挖掘查询工具</span><span class="sxs-lookup"><span data-stu-id="1318a-115">Data Mining Query Tools</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="1318a-116">提供了以下工具，可用于生成针对数据挖掘对象的预测查询、内容查询和数据定义查询：</span><span class="sxs-lookup"><span data-stu-id="1318a-116">provides the following tools that you can use to build prediction queries, content queries, and data definition queries against data mining objects:</span></span>  
  
-   <span data-ttu-id="1318a-117">预测查询生成器</span><span class="sxs-lookup"><span data-stu-id="1318a-117">Prediction Query Builder</span></span>  
  
-   <span data-ttu-id="1318a-118">查询编辑器</span><span class="sxs-lookup"><span data-stu-id="1318a-118">Query Editor</span></span>  
  
-   <span data-ttu-id="1318a-119">DMX 模板</span><span class="sxs-lookup"><span data-stu-id="1318a-119">DMX templates</span></span>  
  
-   <span data-ttu-id="1318a-120">Integration Services 数据挖掘组件</span><span class="sxs-lookup"><span data-stu-id="1318a-120">Integration Services data mining components</span></span>  
  
###  <a name="prediction-query-builder"></a><a name="bkmk_Builder"></a><span data-ttu-id="1318a-121">预测查询生成器</span><span class="sxs-lookup"><span data-stu-id="1318a-121">Prediction Query Builder</span></span>  
 <span data-ttu-id="1318a-122">数据挖掘设计器的 **“挖掘模型预测”** 选项卡中提供了预测查询生成器，可以在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]和 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中使用。</span><span class="sxs-lookup"><span data-stu-id="1318a-122">Prediction Query Builder is included in the **Mining Model Prediction** tab of Data Mining Designer, which is available in both [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]and [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="1318a-123">使用该查询生成器时，可以使用图形工具来选择挖掘模型、添加新事例数据和添加预测函数。</span><span class="sxs-lookup"><span data-stu-id="1318a-123">When you use the query builder, you can use graphical tools to select a mining model, add new case data, and add prediction functions.</span></span> <span data-ttu-id="1318a-124">预测查询生成器包括一个可用于手动修改查询的文本编辑器，以及一个用于查看查询结果的简单 "**结果**" 窗格。</span><span class="sxs-lookup"><span data-stu-id="1318a-124">The Prediction Query Builder includes a text editor that you can use to modify the query manually, and a simple **Results** pane to view the results of the query.</span></span>  
  
###  <a name="query-editor"></a><a name="bkmk_QueryEditor"></a><span data-ttu-id="1318a-125">查询编辑器</span><span class="sxs-lookup"><span data-stu-id="1318a-125">Query Editor</span></span>  
 <span data-ttu-id="1318a-126">中的查询编辑器 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 提供了可用于生成和运行 DMX 查询的工具。</span><span class="sxs-lookup"><span data-stu-id="1318a-126">The Query Editor in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] provides tools that you can use to build and run DMX queries.</span></span> <span data-ttu-id="1318a-127">可以连接到 SQL Server Analysis Services 的实例，然后选择数据库、挖掘结构列和挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="1318a-127">You can connect to an instance of SQL Server Analysis Services, and then select a database, mining structure columns, and a mining model.</span></span> <span data-ttu-id="1318a-128">**“元数据浏览器”** 包含可浏览的预测函数的列表。</span><span class="sxs-lookup"><span data-stu-id="1318a-128">The **Metadata Explorer** contains a list of prediction functions that you can browse.</span></span>  
  
###  <a name="dmx-templates"></a><a name="bkmk_Templates"></a><span data-ttu-id="1318a-129">DMX 模板</span><span class="sxs-lookup"><span data-stu-id="1318a-129">DMX Templates</span></span>  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="1318a-130">提供了可用于生成 DMX 查询的交互式 DMX 查询模板。</span><span class="sxs-lookup"><span data-stu-id="1318a-130">provides interactive DMX query templates that you can use to build DMX queries.</span></span> <span data-ttu-id="1318a-131">如果看不到模板列表，请单击工具栏上的 **“视图”** ，然后选择 **“模板资源管理器”**。</span><span class="sxs-lookup"><span data-stu-id="1318a-131">If you do not see the list of templates, click **View** on the toolbar, and select **Template Explorer**.</span></span> <span data-ttu-id="1318a-132">若要查看所有 Analysis Services 模板，包括用于 DMX、MDX 和 XMLA 的模板，请单击多维数据集图标。</span><span class="sxs-lookup"><span data-stu-id="1318a-132">To see all Analysis Services templates, including templates for DMX, MDX, and XMLA, click the cube icon.</span></span>  
  
 <span data-ttu-id="1318a-133">若要使用模板生成查询，您可以将模板拖入打开的查询窗口中，也可以双击模板以打开新的连接和新的查询窗格。</span><span class="sxs-lookup"><span data-stu-id="1318a-133">To build a query using a template, you can drag the template into an open query window, or you can double-click the template to open a new connection and a new query pane.</span></span>  
  
 <span data-ttu-id="1318a-134">有关如何通过模板创建预测查询的示例，请参阅 [通过模板创建单独预测查询](create-a-singleton-prediction-query-from-a-template.md)。</span><span class="sxs-lookup"><span data-stu-id="1318a-134">For an example of how to create a prediction query from a template, see [Create a Singleton Prediction Query from a Template](create-a-singleton-prediction-query-from-a-template.md).</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="1318a-135">针对 Microsoft Office Excel 的数据挖掘外接程序还包含多个模板以及可帮助您编写复杂的 DMX 语句的交互式查询生成器。</span><span class="sxs-lookup"><span data-stu-id="1318a-135">The Data Mining Add-in for Microsoft Office Excel also contains a number of templates, along with an interactive query builder which can help you compose complex DMX statements.</span></span> <span data-ttu-id="1318a-136">若要使用模板，请单击 **“查询”**，再单击数据挖掘客户端中的 **“高级”** 。</span><span class="sxs-lookup"><span data-stu-id="1318a-136">To use the templates, click **Query**, and click **Advanced** in the Data Mining Client.</span></span>  
  
###  <a name="integration-services-data-mining-components"></a><a name="bkmk_SSIS"></a><span data-ttu-id="1318a-137">Integration Services 数据挖掘组件</span><span class="sxs-lookup"><span data-stu-id="1318a-137">Integration Services Data Mining Components</span></span>  
 <span data-ttu-id="1318a-138">还可以将预测查询包括为包的一部分 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="1318a-138">You can also include prediction queries as part of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package.</span></span> <span data-ttu-id="1318a-139">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 中的以下任务和转换支持创建和执行 DMX 预测查询和 DMX 语句。</span><span class="sxs-lookup"><span data-stu-id="1318a-139">The following tasks and transformations in [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] support the creation and execution of DMX prediction queries and DMX statements.</span></span>  
  
|<span data-ttu-id="1318a-140">组件</span><span class="sxs-lookup"><span data-stu-id="1318a-140">Component</span></span>|<span data-ttu-id="1318a-141">说明</span><span class="sxs-lookup"><span data-stu-id="1318a-141">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1318a-142">数据挖掘查询任务</span><span class="sxs-lookup"><span data-stu-id="1318a-142">Data Mining Query task</span></span>|<span data-ttu-id="1318a-143">将 DMX 查询和其他 DMX 语句作为控制流的一部分执行。</span><span class="sxs-lookup"><span data-stu-id="1318a-143">Executes DMX queries and other DMX statements as part of a control flow.</span></span><br /><br /> <span data-ttu-id="1318a-144">任务编辑器提供了预测查询生成器和一个用于手动修改 DMX 查询的文本框。</span><span class="sxs-lookup"><span data-stu-id="1318a-144">The task editor provides the Prediction Query Builder, and a text box for modifying the DMX query manually.</span></span> <span data-ttu-id="1318a-145">但是，任务编辑器无法验证针对 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 解决方案中的对象的查询。</span><span class="sxs-lookup"><span data-stu-id="1318a-145">However, the task editor cannot validate the query against objects in an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] solution.</span></span> <span data-ttu-id="1318a-146">因此，最好是在 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] 或 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 中创建查询，然后将语句或查询的文本粘贴到任务编辑器中。</span><span class="sxs-lookup"><span data-stu-id="1318a-146">Therefore, it is best to create a query within [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] or [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] and then paste the text of the statement or query into the task editor.</span></span>|  
|<span data-ttu-id="1318a-147">数据挖掘查询转换</span><span class="sxs-lookup"><span data-stu-id="1318a-147">Data Mining Query transformation</span></span>|<span data-ttu-id="1318a-148">使用数据流源所提供的数据，在数据流内执行预测查询。</span><span class="sxs-lookup"><span data-stu-id="1318a-148">Executes a prediction query within a data flow, using data supplied by a data flow source.</span></span><br /><br /> <span data-ttu-id="1318a-149">任务编辑器提供了预测查询生成器和一个用于手动修改 DMX 查询的文本框。</span><span class="sxs-lookup"><span data-stu-id="1318a-149">The task editor provides the Prediction Query Builder, and a text box for modifying the DMX query manually.</span></span><br /><br /> <span data-ttu-id="1318a-150">转换只能用于创建使用数据流中的数据的查询；即使用 PREDICTION JOIN 语法的查询。</span><span class="sxs-lookup"><span data-stu-id="1318a-150">The transformation can only be used for creating queries that use data in the data flow; that is, queries that use the PREDICTION JOIN syntax.</span></span> <span data-ttu-id="1318a-151">此组件不能用于执行内容查询或其他类型的 DMX 语句。</span><span class="sxs-lookup"><span data-stu-id="1318a-151">This component cannot be used for executing content queries or other kinds of DMX statements.</span></span>|  
  
##  <a name="application-programming-interfaces"></a><a name="bkmk_API"></a><span data-ttu-id="1318a-152">应用程序编程接口</span><span class="sxs-lookup"><span data-stu-id="1318a-152">Application Programming Interfaces</span></span>  
 <span data-ttu-id="1318a-153">您可以创建自定义应用程序，这些应用程序通过使用多种编程语言，并且与 OLE DB 或 Analysis Services ADOMD 客户端之类的服务器协议相结合，针对数据挖掘模型执行查询。</span><span class="sxs-lookup"><span data-stu-id="1318a-153">You can create custom applications that execute queries against data mining models by using a variety of programming languages, in combination with server protocols such as OLE DB or Analysis Services ADOMD client.</span></span> <span data-ttu-id="1318a-154">有关详细信息，请参阅 [数据挖掘编程](../dev-guide/data-mining-programming.md)。</span><span class="sxs-lookup"><span data-stu-id="1318a-154">For more information, see [Data Mining Programming](../dev-guide/data-mining-programming.md).</span></span>  
  
 <span data-ttu-id="1318a-155">但是，XMLA 构成了与 Analysis Service 服务器进行的所有交互的基础邮件格式。</span><span class="sxs-lookup"><span data-stu-id="1318a-155">However, XMLA constitutes the underlying message format for all interactions with an Analysis Service server.</span></span> <span data-ttu-id="1318a-156">在某一 XMLA 消息内，根据您是否基于 DMX、内容查询或使用数据挖掘架构行集检索模型元数据的查询发送预测查询，表示查询的方式也将有所不同。</span><span class="sxs-lookup"><span data-stu-id="1318a-156">Within an XMLA message, queries are represented differently depending on whether you are sending a prediction query based on DMX, a content query, or a query that retrieves model metadata using the data mining schema rowsets.</span></span>  
  
-   <span data-ttu-id="1318a-157">**预测查询**的文本（以及所有其他 DMX 语句）通过使用 [Execute 方法 (XMLA)](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute) 以 XMLA 形式发送，而 DMX 查询以文本的形式放置于 XMLA [Command 元素 (XMLA)](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/command-element-xmla) 的 [Statement 元素 (XMLA)](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/statement-element-xmla) 内。</span><span class="sxs-lookup"><span data-stu-id="1318a-157">The text of **prediction queries** (and all other DMX statements) is sent in XMLA by using the [Execute Method &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute) method, with the DMX query placed as text within the [Statement Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/statement-element-xmla) element of the XMLA [Command Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/command-element-xmla) element.</span></span>  
  
-   <span data-ttu-id="1318a-158">若要检索**模型内容**和**模型元数据**，例如群集的数目、在决策树中使用的属性、上次处理模型的日期以及在创建模型时使用的算法参数，可以使用 [Discover 方法 (XMLA)](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-discover) 并在 [RequestType 元素 (XMLA)](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/type-element-xmla) 标头中指定数据挖掘架构行集之一。</span><span class="sxs-lookup"><span data-stu-id="1318a-158">To retrieve **model content** and **model metadata**, such as the number of clusters, the attributes used in decision trees, the date the model was last processed, and the algorithm parameters used when creating the model, you can use the [Discover Method &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-discover) method and specify one of the data mining schema rowsets in the [RequestType Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/type-element-xmla) header.</span></span> <span data-ttu-id="1318a-159">若要缩小查询范围，请在 [RestrictionList 元素 (XMLA)](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/restrictionlist-element-xmla) 内输入限制条件。</span><span class="sxs-lookup"><span data-stu-id="1318a-159">To narrow the scope of the query, enter criteria as restrictions within the [RestrictionList Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/restrictionlist-element-xmla) element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1318a-160">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1318a-160">See Also</span></span>  
 <span data-ttu-id="1318a-161">[&#40;DMX&#41; 的数据挖掘扩展插件](/sql/dmx/data-mining-extensions-dmx-reference) </span><span class="sxs-lookup"><span data-stu-id="1318a-161">[Data Mining Extensions &#40;DMX&#41; Reference](/sql/dmx/data-mining-extensions-dmx-reference) </span></span>  
 <span data-ttu-id="1318a-162">[数据挖掘解决方案](data-mining-solutions.md) </span><span class="sxs-lookup"><span data-stu-id="1318a-162">[Data Mining Solutions](data-mining-solutions.md) </span></span>  
 <span data-ttu-id="1318a-163">[了解 DMX Select 语句](/sql/dmx/understanding-the-dmx-select-statement) </span><span class="sxs-lookup"><span data-stu-id="1318a-163">[Understanding the DMX Select Statement](/sql/dmx/understanding-the-dmx-select-statement) </span></span>  
 <span data-ttu-id="1318a-164">[DMX 预测查询的结构和用法](/sql/dmx/structure-and-usage-of-dmx-prediction-queries) </span><span class="sxs-lookup"><span data-stu-id="1318a-164">[Structure and Usage of DMX Prediction Queries](/sql/dmx/structure-and-usage-of-dmx-prediction-queries) </span></span>  
 <span data-ttu-id="1318a-165">[使用预测查询生成器创建预测查询](create-a-prediction-query-using-the-prediction-query-builder.md) </span><span class="sxs-lookup"><span data-stu-id="1318a-165">[Create a Prediction Query Using the Prediction Query Builder](create-a-prediction-query-using-the-prediction-query-builder.md) </span></span>  
 [<span data-ttu-id="1318a-166">在 SQL Server Management Studio 中创建一个 DMX 查询</span><span class="sxs-lookup"><span data-stu-id="1318a-166">Create a DMX Query in SQL Server Management Studio</span></span>](create-a-dmx-query-in-sql-server-management-studio.md)  
  
  
