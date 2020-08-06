---
title: 添加具有嵌套表的数据源视图 (中间数据挖掘教程) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a14cd7f1-7a10-4ec6-af6a-f5f0676a0308
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: da1a9bff093e0b59e9d1166554d95bcf61aded08
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691411"
---
# <a name="adding-a-data-source-view-with-nested-tables-intermediate-data-mining-tutorial"></a><span data-ttu-id="bc5ee-102">添加带有嵌套表的数据源视图（数据挖掘中级教程）</span><span class="sxs-lookup"><span data-stu-id="bc5ee-102">Adding a Data Source View with Nested Tables (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="bc5ee-103">要创建市场篮模型，您必须使用支持关联数据的数据源视图。</span><span class="sxs-lookup"><span data-stu-id="bc5ee-103">To create a market basket model, you must use a data source view that supports associative data.</span></span> <span data-ttu-id="bc5ee-104">该数据源视图还将用于顺序分析和聚类分析方案。</span><span class="sxs-lookup"><span data-stu-id="bc5ee-104">This data source view will also be used for the sequence clustering scenario.</span></span>  
  
 <span data-ttu-id="bc5ee-105">此数据源视图不同于你可能使用的其他数据源视图，因为它包含*嵌套表*。</span><span class="sxs-lookup"><span data-stu-id="bc5ee-105">This data source view is different from others that you may have worked with because it contains a *nested table*.</span></span> <span data-ttu-id="bc5ee-106">*嵌套表*是一个表，其中包含有关事例表中单个行的多个行信息。</span><span class="sxs-lookup"><span data-stu-id="bc5ee-106">A *nested table* is a table that contains multiple rows of information about a single row in the case table.</span></span> <span data-ttu-id="bc5ee-107">例如，如果您的模型分析客户的购买行为，您通常会使用对于每个客户都包含一个唯一行的表作为事例表。</span><span class="sxs-lookup"><span data-stu-id="bc5ee-107">For example, if your model analyzes the purchasing behavior of customers, you would typically use a table that has a unique row for each customer as the case table.</span></span> <span data-ttu-id="bc5ee-108">但是，每个客户都可能有多个购买行为，您可能希望分析购买的顺序或者经常一起购买的产品。</span><span class="sxs-lookup"><span data-stu-id="bc5ee-108">However, each customer might make multiple purchases, and you might want to analyze the sequence of purchases, or products that are frequently purchased together.</span></span> <span data-ttu-id="bc5ee-109">若要在您的模型中以逻辑方式表示这些购买行为，您需要在该数据源视图中添加另一个表来列出每个客户的购买行为。</span><span class="sxs-lookup"><span data-stu-id="bc5ee-109">To logically represent these purchases in your model, you add another table to the data source view that lists the purchases for each customer.</span></span>  
  
 <span data-ttu-id="bc5ee-110">该嵌套购买表与客户表具有多对一的关系。</span><span class="sxs-lookup"><span data-stu-id="bc5ee-110">This nested purchases table is related to the customer table by a many-to-one relationship.</span></span> <span data-ttu-id="bc5ee-111">该嵌套表可能包含对应每个客户的多个行，每个行包含已购买的单件产品，还可能包含有关购买顺序、订购时的价格或任何促销手段等其他信息。</span><span class="sxs-lookup"><span data-stu-id="bc5ee-111">The nested table might contain many rows for each customer, each row containing a single product that was purchased, perhaps with additional information about the order that the purchases were made, the price at the time of the order, or any promotions that applied.</span></span> <span data-ttu-id="bc5ee-112">您可以使用嵌套表中的信息作为模型的输入，或者作为可预测属性。</span><span class="sxs-lookup"><span data-stu-id="bc5ee-112">You can use the information in the nested table as inputs to the model, or as the predictable attribute.</span></span>  
  
 <span data-ttu-id="bc5ee-113">在本课程中，您将执行以下任务：</span><span class="sxs-lookup"><span data-stu-id="bc5ee-113">In this lesson, you do the following tasks:</span></span>  
  
-   <span data-ttu-id="bc5ee-114">您可以向数据源中添加数据源视图 [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="bc5ee-114">You add a data source view to the [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] data source.</span></span>  
  
-   <span data-ttu-id="bc5ee-115">将事例表和嵌套表添加到此视图中。</span><span class="sxs-lookup"><span data-stu-id="bc5ee-115">You add the case and nested tables to this view.</span></span>  
  
-   <span data-ttu-id="bc5ee-116">在事例表和嵌套表之间指定多对一关系。</span><span class="sxs-lookup"><span data-stu-id="bc5ee-116">You specify the many-to-one relationship between the case and nested table.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="bc5ee-117">.</span><span class="sxs-lookup"><span data-stu-id="bc5ee-117">.</span></span> <span data-ttu-id="bc5ee-118">按照所述步骤执行很重要，这样可以正确指定事例表和嵌套表之间的关系，并且可以避免在处理模型时出现错误。</span><span class="sxs-lookup"><span data-stu-id="bc5ee-118">It is important that you follow the described procedure exactly, to correctly specify the relationship between the case table and the nested table and to avoid errors when you process the model.</span></span>  
  
-   <span data-ttu-id="bc5ee-119">定义如何在模型中使用数据列。</span><span class="sxs-lookup"><span data-stu-id="bc5ee-119">You define how the columns of data are used in the model.</span></span>  
  
 <span data-ttu-id="bc5ee-120">有关使用事例表和嵌套表以及如何选择嵌套表键的详细信息，请参阅[&#40;Analysis Services 数据挖掘&#41;的嵌套表](../../2014/analysis-services/data-mining/nested-tables-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="bc5ee-120">For more information about working with case and nested tables, and how to choose a nested table key, see [Nested Tables &#40;Analysis Services - Data Mining&#41;](../../2014/analysis-services/data-mining/nested-tables-analysis-services-data-mining.md).</span></span>  
  
### <a name="to-add-a-data-source-view"></a><span data-ttu-id="bc5ee-121">添加数据源视图</span><span class="sxs-lookup"><span data-stu-id="bc5ee-121">To add a data source view</span></span>  
  
1.  <span data-ttu-id="bc5ee-122">在解决方案资源管理器中，右键单击 "**数据源视图**"，然后选择 "**新建数据源视图**"。</span><span class="sxs-lookup"><span data-stu-id="bc5ee-122">In Solution Explorer, right-click **Data Source Views**, and then select **New Data Source View**.</span></span>  
  
     <span data-ttu-id="bc5ee-123">系统将打开数据源视图向导。</span><span class="sxs-lookup"><span data-stu-id="bc5ee-123">The Data Source View Wizard opens.</span></span>  
  
2.  <span data-ttu-id="bc5ee-124">在“欢迎使用数据源视图向导”  页上，单击“下一步” 。</span><span class="sxs-lookup"><span data-stu-id="bc5ee-124">On the **Welcome to the Data Source View Wizard** page, click **Next**.</span></span>  
  
3.  <span data-ttu-id="bc5ee-125">在 "**选择数据源**" 页的 "**关系数据源**" 下，选择 [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] 在基础数据挖掘教程中创建的数据源。</span><span class="sxs-lookup"><span data-stu-id="bc5ee-125">On the **Select a Data Source** page, under **Relational data sources**, select the [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] data source that you created in the Basic Data Mining Tutorial.</span></span> <span data-ttu-id="bc5ee-126">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="bc5ee-126">Click **Next**.</span></span>  
  
4.  <span data-ttu-id="bc5ee-127">在 "**选择表和视图**" 页上，选择下表，然后单击右箭头将它们包含在新的数据源视图中：</span><span class="sxs-lookup"><span data-stu-id="bc5ee-127">On the **Select Tables and Views** page, select the following tables, and then click the right arrow to include them in the new data source view:</span></span>  
  
    -   `vAssocSeqOrders`  
  
    -   `vAssocSeqLineItems`  
  
5.  <span data-ttu-id="bc5ee-128">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="bc5ee-128">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="bc5ee-129">在 "**完成向导**" 页上，默认将数据源视图命名为 [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="bc5ee-129">On the **Completing the Wizard** page, by default the data source view is named [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)].</span></span> <span data-ttu-id="bc5ee-130">将名称更改为 `Orders` ，然后单击 "**完成**"。</span><span class="sxs-lookup"><span data-stu-id="bc5ee-130">Change the name to `Orders`, and then click **Finish**.</span></span>  
  
     <span data-ttu-id="bc5ee-131">数据源视图设计器随即打开，并 `Orders` 显示数据源视图。</span><span class="sxs-lookup"><span data-stu-id="bc5ee-131">Data Source View Designer opens and the `Orders` data source view appears.</span></span>  
  
### <a name="to-create-a-relationship-between-tables"></a><span data-ttu-id="bc5ee-132">创建表之间的关系</span><span class="sxs-lookup"><span data-stu-id="bc5ee-132">To create a relationship between tables</span></span>  
  
1.  <span data-ttu-id="bc5ee-133">在数据源视图设计器中，定位 vAssocSeqLineItems 表和 vAssocSeqOrders 表，使其水平对齐，并且 vAssocSeqLineItems 表在左，vAssocSeqOrders 表在右。</span><span class="sxs-lookup"><span data-stu-id="bc5ee-133">In Data Source View Designer, position the two tables so that the tables are aligned horizontally, with the vAssocSeqLineItems table on the left side and the vAssocSeqOrders table on the right side.</span></span>  
  
2.  <span data-ttu-id="bc5ee-134">选择 vAssocSeqLineItems 表中的**OrderNumber**列。</span><span class="sxs-lookup"><span data-stu-id="bc5ee-134">Select the **OrderNumber** column in the vAssocSeqLineItems table.</span></span>  
  
3.  <span data-ttu-id="bc5ee-135">将该列拖到 "vAssocSeqOrders" 表中，并将其放到 " **OrderNumber** " 列。</span><span class="sxs-lookup"><span data-stu-id="bc5ee-135">Drag the column to the vAssocSeqOrders table, and put it on the **OrderNumber** column.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="bc5ee-136">请确保将**OrderNumber**列从 vAssocSeqLineItems 嵌套表中拖出，后者表示联接的多方，后者表示联接的一方。</span><span class="sxs-lookup"><span data-stu-id="bc5ee-136">Make sure to drag the **OrderNumber** column from the vAssocSeqLineItems nested table, which represents the many side of the join, to the vAssocSeqOrders case table, which represents the one side of the join.</span></span>  
  
     <span data-ttu-id="bc5ee-137">VAssocSeqLineItems 表和 vAssocSeqOrders 表之间现在存在新的*多对一关系*。</span><span class="sxs-lookup"><span data-stu-id="bc5ee-137">A new *many-to-one relationship* now exists between the vAssocSeqLineItems and vAssocSeqOrders tables.</span></span> <span data-ttu-id="bc5ee-138">如果您已正确联接表，则数据源视图应如下所示：</span><span class="sxs-lookup"><span data-stu-id="bc5ee-138">If you have joined the tables correctly, the data source view should appear as follows:</span></span>  
  
     <span data-ttu-id="bc5ee-139">![嵌套表和事例表之间需要的多对一联接](../../2014/tutorials/media/dsv-nestedjoin-illustration.gif "嵌套表和事例表之间需要的多对一联接")</span><span class="sxs-lookup"><span data-stu-id="bc5ee-139">![expected many-to-one join on nested and case table](../../2014/tutorials/media/dsv-nestedjoin-illustration.gif "expected many-to-one join on nested and case table")</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="bc5ee-140">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="bc5ee-140">Next Task in Lesson</span></span>  
 [<span data-ttu-id="bc5ee-141">创建市场篮结构和模型 &#40;中级数据挖掘教程&#41;</span><span class="sxs-lookup"><span data-stu-id="bc5ee-141">Creating a Market Basket Structure and Model &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/creating-a-market-basket-structure-and-model-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="bc5ee-142">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bc5ee-142">See Also</span></span>  
 <span data-ttu-id="bc5ee-143">[中级数据挖掘教程 &#40;Analysis Services 数据挖掘&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="bc5ee-143">[Intermediate Data Mining Tutorial &#40;Analysis Services - Data Mining&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="bc5ee-144">[挖掘结构 &#40;Analysis Services 数据挖掘&#41;](../../2014/analysis-services/data-mining/mining-structures-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="bc5ee-144">[Mining Structures &#40;Analysis Services - Data Mining&#41;](../../2014/analysis-services/data-mining/mining-structures-analysis-services-data-mining.md) </span></span>  
 [<span data-ttu-id="bc5ee-145">挖掘模型（Analysis Services - 数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="bc5ee-145">Mining Models &#40;Analysis Services - Data Mining&#41;</span></span>](../../2014/analysis-services/data-mining/mining-models-analysis-services-data-mining.md)  
  
  
