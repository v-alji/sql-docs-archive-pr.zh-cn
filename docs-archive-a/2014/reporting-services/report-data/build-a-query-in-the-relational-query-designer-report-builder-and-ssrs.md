---
title: 在关系查询设计器中生成查询（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 28b25861-f3b4-4c3e-a9b0-03d6e4cfea26
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 555d72c4d3bca8677d04fdc4160639f004d6bbe9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692754"
---
# <a name="build-a-query-in-the-relational-query-designer-report-builder-and-ssrs"></a><span data-ttu-id="a5cc0-102">在关系查询设计器中生成查询（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="a5cc0-102">Build a Query in the Relational Query Designer (Report Builder and SSRS)</span></span>
  <span data-ttu-id="a5cc0-103">查询设计器可帮助您指定为报表数据集要从外部数据源中检索的数据。</span><span class="sxs-lookup"><span data-stu-id="a5cc0-103">A query designer helps you specify which data to retrieve from an external data source for a report dataset.</span></span> <span data-ttu-id="a5cc0-104">当您在向导中生成查询或创建数据集查询时，可以使用查询设计器。</span><span class="sxs-lookup"><span data-stu-id="a5cc0-104">You use a query designer when you build a query in a wizard or create a dataset query.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
 <span data-ttu-id="a5cc0-105">数据集基于数据源。</span><span class="sxs-lookup"><span data-stu-id="a5cc0-105">A dataset is based on a data source.</span></span> <span data-ttu-id="a5cc0-106">数据源的类型和创作环境决定在定义数据集查询时打开的查询设计器。</span><span class="sxs-lookup"><span data-stu-id="a5cc0-106">The type of data source and the authoring environment determines which query designer opens when you define the dataset query.</span></span> <span data-ttu-id="a5cc0-107">查询设计器功能根据基础数据源类型的不同而不同。</span><span class="sxs-lookup"><span data-stu-id="a5cc0-107">Query designer features vary based on the underlying data source.</span></span> <span data-ttu-id="a5cc0-108">有关数据层的详细信息，请参阅[数据连接、数据源和连接字符串（在](../data-connections-data-sources-and-connection-strings-in-report-builder.md)Reporting Services 中报表生成器或[数据连接、数据源和连接字符串](../data-connections-data-sources-and-connection-strings-in-reporting-services.md)）。</span><span class="sxs-lookup"><span data-stu-id="a5cc0-108">For more information about data layers, see [Data Connections, Data Sources, and Connection Strings in Report Builder](../data-connections-data-sources-and-connection-strings-in-report-builder.md) or [Data Connections, Data Sources, and Connection Strings in Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md).</span></span>  
  
 <span data-ttu-id="a5cc0-109">可为以下任务使用查询设计器：</span><span class="sxs-lookup"><span data-stu-id="a5cc0-109">You can use a query designer for the following tasks:</span></span>  
  
-   <span data-ttu-id="a5cc0-110">浏览外部数据源中的多个架构的元数据</span><span class="sxs-lookup"><span data-stu-id="a5cc0-110">Explore the metadata for multiple schemas on the external data source</span></span>  
  
-   <span data-ttu-id="a5cc0-111">指定要检索的数据集的字段</span><span class="sxs-lookup"><span data-stu-id="a5cc0-111">Specify fields to retrieve for the dataset</span></span>  
  
-   <span data-ttu-id="a5cc0-112">指定两个对象（如表）之间的关系</span><span class="sxs-lookup"><span data-stu-id="a5cc0-112">Specify relationships between two objects such as tables</span></span>  
  
-   <span data-ttu-id="a5cc0-113">指定在将数据作为报表数据进行检索之前用于限制它的筛选器</span><span class="sxs-lookup"><span data-stu-id="a5cc0-113">Specify filters to restrict the data before it is retrieved as report data</span></span>  
  
-   <span data-ttu-id="a5cc0-114">指示是否创建参数</span><span class="sxs-lookup"><span data-stu-id="a5cc0-114">Indicate whether to create parameters</span></span>  
  
-   <span data-ttu-id="a5cc0-115">指定用于对外部数据源执行计算的聚合</span><span class="sxs-lookup"><span data-stu-id="a5cc0-115">Specify aggregates to perform calculations on the external data source</span></span>  
  
 <span data-ttu-id="a5cc0-116">打开查询设计器后，以生成嵌入数据集或共享数据集的相同方式生成查询。</span><span class="sxs-lookup"><span data-stu-id="a5cc0-116">After you open a query designer, you build a query in the same way for either an embedded dataset or a shared dataset.</span></span> <span data-ttu-id="a5cc0-117">以下过程使用嵌入数据集查询。</span><span class="sxs-lookup"><span data-stu-id="a5cc0-117">The following procedures use an embedded dataset query.</span></span>  
  
 <span data-ttu-id="a5cc0-118">有关详细信息，请参阅[关系查询设计器用户界面（报表生成器）](relational-query-designer-user-interface-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="a5cc0-118">For more information, see [Relational Query Designer User Interface &#40;Report Builder&#41;](relational-query-designer-user-interface-report-builder.md).</span></span>  
  
### <a name="to-build-a-query-for-an-embedded-dataset-in-report-design-view"></a><span data-ttu-id="a5cc0-119">在报表设计视图中为嵌入数据集生成查询</span><span class="sxs-lookup"><span data-stu-id="a5cc0-119">To build a query for an embedded dataset in Report Design View</span></span>  
  
1.  <span data-ttu-id="a5cc0-120">打开查询设计器。</span><span class="sxs-lookup"><span data-stu-id="a5cc0-120">Open the query designer.</span></span> <span data-ttu-id="a5cc0-121">在“报表数据”窗格中，右键单击该数据集，然后单击“查询”  。</span><span class="sxs-lookup"><span data-stu-id="a5cc0-121">In the Report Data pane, right-click the dataset, and then click **Query**.</span></span>  
  
     <span data-ttu-id="a5cc0-122">将打开与数据源关联的查询设计器。</span><span class="sxs-lookup"><span data-stu-id="a5cc0-122">The query designer that is associated with the data source opens.</span></span>  
  
2.  <span data-ttu-id="a5cc0-123">在“数据库视图”窗格中，展开显示数据库架构对象（如表、视图和存储过程）的层次结构视图的文件夹。</span><span class="sxs-lookup"><span data-stu-id="a5cc0-123">In the Database view pane, expand the folders that display a hierarchical view of database schema objects such as tables, views, and stored procedures.</span></span> <span data-ttu-id="a5cc0-124">单击选择框为某个对象选择所有字段，或展开节点以选择单个字段。</span><span class="sxs-lookup"><span data-stu-id="a5cc0-124">Click the select box to select all fields for an object or expand the node to select individual fields.</span></span>  
  
     <span data-ttu-id="a5cc0-125">在从“数据库视图”窗格中选择字段时， **“选择字段”** 窗格将显示您的选择。</span><span class="sxs-lookup"><span data-stu-id="a5cc0-125">As you select fields from the Database view pane, the **Select fields** pane displays your selections.</span></span>  
  
     <span data-ttu-id="a5cc0-126">如果从多个相关数据库表中选择字段，则使用“关系”窗格查看从数据库架构中检测到的表关系。</span><span class="sxs-lookup"><span data-stu-id="a5cc0-126">If you select fields from more than one related database table, use the Relationships pane to view the table relationships that were detected from the database schema.</span></span>  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     <span data-ttu-id="a5cc0-127">数据集字段的列表将显示在“报表数据”窗格中。</span><span class="sxs-lookup"><span data-stu-id="a5cc0-127">The list of dataset fields appears in the Report Data pane.</span></span>  
  
### <a name="to-specify-limits-for-a-query"></a><span data-ttu-id="a5cc0-128">为查询指定限制</span><span class="sxs-lookup"><span data-stu-id="a5cc0-128">To specify limits for a query</span></span>  
  
1.  <span data-ttu-id="a5cc0-129">在关系查询设计器中，确认您已选择字段且这些字段显示在 **“所选字段”** 窗格中。</span><span class="sxs-lookup"><span data-stu-id="a5cc0-129">In the relational query designer, verify that you have fields selected and that the fields appear in the **Selected fields** pane.</span></span>  
  
2.  <span data-ttu-id="a5cc0-130">在“应用的筛选器”窗格工具栏中，单击 **“添加筛选器”** 。</span><span class="sxs-lookup"><span data-stu-id="a5cc0-130">In the Applied filters pane toolbar, click **Add Filter**.</span></span> <span data-ttu-id="a5cc0-131">此时将显示一个新的筛选器行。</span><span class="sxs-lookup"><span data-stu-id="a5cc0-131">A new filter row appears.</span></span>  
  
3.  <span data-ttu-id="a5cc0-132">在“字段名称”中，单击以显示字段的下拉列表，然后单击要作为筛选依据的字段名称  。</span><span class="sxs-lookup"><span data-stu-id="a5cc0-132">In **Field name**, click to display the drop-down list of fields, and then click the name of the field that you want to filter by.</span></span> <span data-ttu-id="a5cc0-133">例如，若要按数量进行筛选，则单击包含项数的字段。</span><span class="sxs-lookup"><span data-stu-id="a5cc0-133">For example, to filter by quantity, click the field that contains the number of items.</span></span>  
  
4.  <span data-ttu-id="a5cc0-134">在“运算符”中，单击以显示运算符的下拉列表，然后选择要在筛选器中使用的比较运算符  。</span><span class="sxs-lookup"><span data-stu-id="a5cc0-134">In **Operator**, click to display the drop-down list of operators, and then select the comparison operator to use in the filter.</span></span>  
  
5.  <span data-ttu-id="a5cc0-135">在 **“值”** 中，键入要作为筛选依据的值。</span><span class="sxs-lookup"><span data-stu-id="a5cc0-135">In **Value**, type the value that you want to filter by.</span></span> <span data-ttu-id="a5cc0-136">例如，若要针对大于 100 的数量进行筛选，则键入 100。</span><span class="sxs-lookup"><span data-stu-id="a5cc0-136">For example, to filter on quantity greater than 100, type 100.</span></span>  
  
6.  <span data-ttu-id="a5cc0-137">在此行中选择参数选项，以创建一个数据集参数，从而使用户能够指定筛选器值。</span><span class="sxs-lookup"><span data-stu-id="a5cc0-137">Select the parameter option in this row to create a dataset parameter to enable a user to specify a filter value.</span></span> <span data-ttu-id="a5cc0-138">系统会自动创建与数据集参数匹配的报表参数。</span><span class="sxs-lookup"><span data-stu-id="a5cc0-138">A report parameter that matches the dataset parameter is automatically created.</span></span>  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
8.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
 <span data-ttu-id="a5cc0-139">数据集字段的列表将显示在“报表数据”窗格中。</span><span class="sxs-lookup"><span data-stu-id="a5cc0-139">The list of dataset fields appears in the Report Data pane.</span></span>  
  
### <a name="to-view-a-query-result-set"></a><span data-ttu-id="a5cc0-140">查看查询结果集</span><span class="sxs-lookup"><span data-stu-id="a5cc0-140">To view a query result set</span></span>  
  
1.  <span data-ttu-id="a5cc0-141">在查询设计器工具栏中，单击“运行查询(!)”  。</span><span class="sxs-lookup"><span data-stu-id="a5cc0-141">On the query designer toolbar, click **Run Query (!)**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a5cc0-142">查询设计器使用设计时凭据运行查询并检索结果集。</span><span class="sxs-lookup"><span data-stu-id="a5cc0-142">The query designer uses design time credentials to run the query and retrieve the result set.</span></span> <span data-ttu-id="a5cc0-143">有关详细信息，请参阅 [在报表生成器中指定凭据](../specify-credentials-in-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="a5cc0-143">For more information, see [Specify Credentials in Report Builder](../specify-credentials-in-report-builder.md).</span></span>  
  
 <span data-ttu-id="a5cc0-144">查询在数据源上运行并在“查询结果”窗格中返回示例数据。</span><span class="sxs-lookup"><span data-stu-id="a5cc0-144">The query runs on the data source and returns example data in the Query results pane.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5cc0-145">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a5cc0-145">See Also</span></span>  
 <span data-ttu-id="a5cc0-146">[将数据添加到报表 &#40;报表生成器和 SSRS&#41;](report-datasets-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="a5cc0-146">[Add Data to a Report &#40;Report Builder and SSRS&#41;](report-datasets-ssrs.md) </span></span>  
 <span data-ttu-id="a5cc0-147">[从外部数据源中添加数据 (SSRS)](add-data-from-external-data-sources-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="a5cc0-147">[Add Data from External Data Sources &#40;SSRS&#41;](add-data-from-external-data-sources-ssrs.md) </span></span>  
 <span data-ttu-id="a5cc0-148">[查询设计器 &#40;报表生成器&#41;](../query-designers-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="a5cc0-148">[Query Designers &#40;Report Builder&#41;](../query-designers-report-builder.md) </span></span>  
 <span data-ttu-id="a5cc0-149">[创建共享数据集或嵌入数据集（报表生成器和 SSRS）](create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="a5cc0-149">[Create a Shared Dataset or Embedded Dataset &#40;Report Builder and SSRS&#41;](create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="a5cc0-150">[报表设计视图（报表生成器）](../report-builder/report-design-view-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="a5cc0-150">[Report Design View &#40;Report Builder&#41;](../report-builder/report-design-view-report-builder.md) </span></span>  
 <span data-ttu-id="a5cc0-151">[共享数据集设计视图（报表生成器）](../report-builder/shared-dataset-design-view-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="a5cc0-151">[Shared Dataset Design View &#40;Report Builder&#41;](../report-builder/shared-dataset-design-view-report-builder.md) </span></span>  
 [<span data-ttu-id="a5cc0-152">Reporting Services 查询设计器</span><span class="sxs-lookup"><span data-stu-id="a5cc0-152">Reporting Services Query Designers</span></span>](../reporting-services-query-designers.md)  
  
  
