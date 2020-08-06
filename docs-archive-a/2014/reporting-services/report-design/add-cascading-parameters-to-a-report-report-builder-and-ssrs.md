---
title: 向报表添加级联参数（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 3a22eec3-57a7-478e-b6fc-102a9dbe0591
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5419d448b2fa9526224e1bccd80d5c195e2763d7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687451"
---
# <a name="add-cascading-parameters-to-a-report-report-builder-and-ssrs"></a><span data-ttu-id="e7cfa-102">向报表添加级联参数（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="e7cfa-102">Add Cascading Parameters to a Report (Report Builder and SSRS)</span></span>
  <span data-ttu-id="e7cfa-103">级联参数提供了一种管理大量报表数据的方法。</span><span class="sxs-lookup"><span data-stu-id="e7cfa-103">Cascading parameters provide a way of managing large amounts of report data.</span></span> <span data-ttu-id="e7cfa-104">您可以定义一组相关参数，使一个参数的值列表取决于其他参数选取的值。</span><span class="sxs-lookup"><span data-stu-id="e7cfa-104">You can define a set of related parameters so that the list of values for one parameter depends on the value chosen in another parameter.</span></span> <span data-ttu-id="e7cfa-105">例如，第一个参数是独立的，并且可能提供产品类别列表。</span><span class="sxs-lookup"><span data-stu-id="e7cfa-105">For example, the first parameter is independent and might present a list of product categories.</span></span> <span data-ttu-id="e7cfa-106">当用户选中某个类别后，第二个参数则取决于第一个参数的值。</span><span class="sxs-lookup"><span data-stu-id="e7cfa-106">When the user selects a category, the second parameter is dependent on the value of the first parameter.</span></span> <span data-ttu-id="e7cfa-107">第二个参数的值根据所选类别中的子类别列表进行更新。</span><span class="sxs-lookup"><span data-stu-id="e7cfa-107">Its values are updated with a list of subcategories within the chosen category.</span></span> <span data-ttu-id="e7cfa-108">用户查看报表时，类别和子类别参数的值用于筛选报表数据。</span><span class="sxs-lookup"><span data-stu-id="e7cfa-108">When the user views the report, the values for both the category and subcategory parameters are used to filter report data.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
 <span data-ttu-id="e7cfa-109">若要创建级联参数，请首先定义数据集查询，并为所需的每个级联参数包括一个查询参数。</span><span class="sxs-lookup"><span data-stu-id="e7cfa-109">To create cascading parameters, you define the dataset query first and include a query parameter for each cascading parameter that you need.</span></span> <span data-ttu-id="e7cfa-110">您还必须为每个级联参数创建单独的数据集以提供可用值。</span><span class="sxs-lookup"><span data-stu-id="e7cfa-110">You must also create a separate dataset for each cascading parameter to provide available values.</span></span> <span data-ttu-id="e7cfa-111">有关详细信息，请参阅[为报表参数添加、更改或删除可用值（报表生成器和 SSRS）](add-change-or-delete-available-values-for-a-report-parameter.md)。</span><span class="sxs-lookup"><span data-stu-id="e7cfa-111">For more information, see [Add, Change, or Delete Available Values for a Report Parameter &#40;Report Builder and SSRS&#41;](add-change-or-delete-available-values-for-a-report-parameter.md).</span></span>  
  
 <span data-ttu-id="e7cfa-112">顺序对于级联参数来说很重要，因为对较晚出现在列表中的参数的数据集查询将包含对较早出现在列表中的每个参数的引用。</span><span class="sxs-lookup"><span data-stu-id="e7cfa-112">Order is important for cascading parameters because the dataset query for a parameter later in the list includes a reference to each parameter that is earlier in the list.</span></span> <span data-ttu-id="e7cfa-113">在运行时，参数在“报表数据”窗格中的顺序确定参数查询在报表中的显示顺序，并由此确定用户选择每个连续参数值的顺序。</span><span class="sxs-lookup"><span data-stu-id="e7cfa-113">At run time, the order of the parameters in the Report Data pane determines the order in which the parameter queries appear in the report, and therefore, the order in which a user chooses each successive parameter value.</span></span>  
  
 <span data-ttu-id="e7cfa-114">有关创建具有多个值的级联参数以及包括“全选”功能的信息，请参阅 [如何创建“全选”多值级联参数](https://go.microsoft.com/fwlink/?LinkId=184757)。</span><span class="sxs-lookup"><span data-stu-id="e7cfa-114">For information about creating cascading parameters with multiple values and including the Select All feature, see [How to have a Select All Multivalue Cascading Parameter](https://go.microsoft.com/fwlink/?LinkId=184757).</span></span>  
  
### <a name="to-create-the-main-dataset-with-a-query-that-includes-multiple-related-parameters"></a><span data-ttu-id="e7cfa-115">使用包含多个相关参数的查询创建主数据集</span><span class="sxs-lookup"><span data-stu-id="e7cfa-115">To create the main dataset with a query that includes multiple related parameters</span></span>  
  
1.  <span data-ttu-id="e7cfa-116">在“报表数据”窗格中，右键单击数据源，然后单击 **“添加数据集”** 。</span><span class="sxs-lookup"><span data-stu-id="e7cfa-116">In the Report Data pane, right-click a data source, and then click **Add Dataset**.</span></span>  
  
2.  <span data-ttu-id="e7cfa-117">在 **“名称”** 中，键入数据集的名称。</span><span class="sxs-lookup"><span data-stu-id="e7cfa-117">In **Name**, type the name of the dataset.</span></span>  
  
3.  <span data-ttu-id="e7cfa-118">在 **“数据源”** 中，选择数据源的名称，或单击 **“新建”** 创建一个数据源。</span><span class="sxs-lookup"><span data-stu-id="e7cfa-118">In **Data source**, choose the name of the data source or click **New** to create one.</span></span>  
  
4.  <span data-ttu-id="e7cfa-119">在 **“查询类型”** 中，选择所选数据源的查询类型。</span><span class="sxs-lookup"><span data-stu-id="e7cfa-119">In **Query type**, choose the type of query for the selected data source.</span></span> <span data-ttu-id="e7cfa-120">在本主题中，假定查询类型为 **“文本”** 。</span><span class="sxs-lookup"><span data-stu-id="e7cfa-120">In this topic, query type **Text** is assumed.</span></span>  
  
5.  <span data-ttu-id="e7cfa-121">在 **“查询”** 中，键入检索该报表的数据所使用的查询。</span><span class="sxs-lookup"><span data-stu-id="e7cfa-121">In **Query**, type the query to use to retrieve data for this report.</span></span> <span data-ttu-id="e7cfa-122">查询必须包含以下部分：</span><span class="sxs-lookup"><span data-stu-id="e7cfa-122">The query must include the following parts:</span></span>  
  
    1.  <span data-ttu-id="e7cfa-123">数据源字段列表。</span><span class="sxs-lookup"><span data-stu-id="e7cfa-123">A list of data source fields.</span></span> <span data-ttu-id="e7cfa-124">例如，在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句中，SELECT 语句指定给定表或视图中数据库列名的列表。</span><span class="sxs-lookup"><span data-stu-id="e7cfa-124">For example, in a [!INCLUDE[tsql](../../includes/tsql-md.md)] statement, the SELECT statement specifies a list of database column names from a given table or view.</span></span>  
  
    2.  <span data-ttu-id="e7cfa-125">每个级联参数的一个查询参数。</span><span class="sxs-lookup"><span data-stu-id="e7cfa-125">One query parameter for each cascading parameter.</span></span> <span data-ttu-id="e7cfa-126">查询参数通过指定查询中要包含或排除的特定值来限制从数据源中检索的数据。</span><span class="sxs-lookup"><span data-stu-id="e7cfa-126">A query parameter limits the data retrieved from the data source by specifying certain values to include or exclude from the query.</span></span> <span data-ttu-id="e7cfa-127">通常，查询参数出现在查询的限制子句中。</span><span class="sxs-lookup"><span data-stu-id="e7cfa-127">Typically, query parameters occur in a restriction clause in the query.</span></span> <span data-ttu-id="e7cfa-128">例如，在 [!INCLUDE[tsql](../../includes/tsql-md.md)] SELECT 语句中，查询参数出现在 WHERE 子句中。</span><span class="sxs-lookup"><span data-stu-id="e7cfa-128">For example, in a [!INCLUDE[tsql](../../includes/tsql-md.md)] SELECT statement, query parameters occur in the WHERE clause.</span></span> <span data-ttu-id="e7cfa-129">有关详细信息，请参阅位于 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SQL Server 联机丛书 [上的](https://go.microsoft.com/fwlink/?linkid=120955)文档中的“使用 WHERE 和 HAVING 筛选行”。</span><span class="sxs-lookup"><span data-stu-id="e7cfa-129">For more information, see "Filtering Rows by Using WHERE and HAVING" in the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] documentation in [SQL Server Books Online](https://go.microsoft.com/fwlink/?linkid=120955).</span></span>  
  
6.  <span data-ttu-id="e7cfa-130">单击 "**运行** (**！**) 。</span><span class="sxs-lookup"><span data-stu-id="e7cfa-130">Click **Run** (**!**).</span></span> <span data-ttu-id="e7cfa-131">在包括查询参数并运行查询之后，将自动创建对应于查询参数的报表参数。</span><span class="sxs-lookup"><span data-stu-id="e7cfa-131">After you include query parameters and then run the query, report parameters that correspond to the query parameters are automatically created.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e7cfa-132">首次运行查询时的查询参数顺序确定它们在报表中的创建顺序。</span><span class="sxs-lookup"><span data-stu-id="e7cfa-132">The order of query parameters the first time you run a query determines the order that they are created in the report.</span></span> <span data-ttu-id="e7cfa-133">若要更改顺序，请参阅[更改报表参数的顺序（报表生成器和 SSRS）](change-the-order-of-a-report-parameter-report-builder-and-ssrs.md)</span><span class="sxs-lookup"><span data-stu-id="e7cfa-133">To change the order, see [Change the Order of a Report Parameter &#40;Report Builder and SSRS&#41;](change-the-order-of-a-report-parameter-report-builder-and-ssrs.md)</span></span>  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
 <span data-ttu-id="e7cfa-134">接下来，您将创建一个提供独立参数的值的数据集。</span><span class="sxs-lookup"><span data-stu-id="e7cfa-134">Next, you will create a dataset that provides the values for the independent parameter.</span></span>  
  
### <a name="to-create-a-dataset-to-provide-values-for-an-independent-parameter"></a><span data-ttu-id="e7cfa-135">创建提供独立参数的值的数据集</span><span class="sxs-lookup"><span data-stu-id="e7cfa-135">To create a dataset to provide values for an independent parameter</span></span>  
  
1.  <span data-ttu-id="e7cfa-136">在“报表数据”窗格中，右键单击数据源，然后单击 **“添加数据集”**。</span><span class="sxs-lookup"><span data-stu-id="e7cfa-136">In the Report Data pane, right-click a data source, and then click **Add Dataset**.</span></span>  
  
2.  <span data-ttu-id="e7cfa-137">在 **“名称”** 中，键入数据集的名称。</span><span class="sxs-lookup"><span data-stu-id="e7cfa-137">In **Name**, type the name of the dataset.</span></span>  
  
3.  <span data-ttu-id="e7cfa-138">在 **“数据源”** 中，确保该名称是在第 1 步中选择的数据源的名称。</span><span class="sxs-lookup"><span data-stu-id="e7cfa-138">In **Data source**, verify the name is the name of the data source you chose in step 1.</span></span>  
  
4.  <span data-ttu-id="e7cfa-139">在 **“查询类型”** 中，选择所选数据源的查询类型。</span><span class="sxs-lookup"><span data-stu-id="e7cfa-139">In **Query type**, choose the type of query for the selected data source.</span></span> <span data-ttu-id="e7cfa-140">在本主题中，假定查询类型为 **“文本”** 。</span><span class="sxs-lookup"><span data-stu-id="e7cfa-140">In this topic, query type **Text** is assumed.</span></span>  
  
5.  <span data-ttu-id="e7cfa-141">在 **“查询”** 中，键入检索该参数的值所使用的查询。</span><span class="sxs-lookup"><span data-stu-id="e7cfa-141">In **Query**, type the query to use to retrieve values for this parameter.</span></span> <span data-ttu-id="e7cfa-142">对独立参数的查询通常不包含查询参数。</span><span class="sxs-lookup"><span data-stu-id="e7cfa-142">Queries for independent parameters typically do not contain query parameters.</span></span> <span data-ttu-id="e7cfa-143">例如，若要对提供所有类别值的参数创建查询，可以使用如下 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句：</span><span class="sxs-lookup"><span data-stu-id="e7cfa-143">For example, to create a query for a parameter that provides all category values, you might use a [!INCLUDE[tsql](../../includes/tsql-md.md)] statement similar to the following:</span></span>  
  
    ```  
    SELECT DISTINCT <column name> FROM <table>  
    ```  
  
     <span data-ttu-id="e7cfa-144">SELECT DISTINCT 命令从结果集删除重复值，以便从指定表的指定列中获取每个唯一值。</span><span class="sxs-lookup"><span data-stu-id="e7cfa-144">The SELECT DISTINCT command removes duplicate values from the result set so that you get each unique value from the specified column in the specified table.</span></span>  
  
     <span data-ttu-id="e7cfa-145">单击 "**运行** (**！**) 。</span><span class="sxs-lookup"><span data-stu-id="e7cfa-145">Click **Run** (**!**).</span></span> <span data-ttu-id="e7cfa-146">结果集显示以上第一个参数的可用值。</span><span class="sxs-lookup"><span data-stu-id="e7cfa-146">The result set shows the values that are available for this first parameter.</span></span>  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
 <span data-ttu-id="e7cfa-147">接下来，您将设置第一个参数的属性，以便在运行时使用该数据集填充其可用值。</span><span class="sxs-lookup"><span data-stu-id="e7cfa-147">Next, you will set the properties of the first parameter to use this dataset to populate its available values at run-time.</span></span>  
  
### <a name="to-set-available-values-for-a-report-parameter"></a><span data-ttu-id="e7cfa-148">设置报表参数的可用值</span><span class="sxs-lookup"><span data-stu-id="e7cfa-148">To set available values for a report parameter</span></span>  
  
1.  <span data-ttu-id="e7cfa-149">在“报表数据”窗格的“参数”文件夹中，右键单击第一个参数，然后单击 **“参数属性”**。</span><span class="sxs-lookup"><span data-stu-id="e7cfa-149">In the Report Data pane, in the Parameters folder, right-click the first parameter, and then click **Parameter Properties**.</span></span>  
  
2.  <span data-ttu-id="e7cfa-150">在 **“名称”** 中，确保参数名称准确无误。</span><span class="sxs-lookup"><span data-stu-id="e7cfa-150">In **Name**, verify that the name of the parameter is correct.</span></span>  
  
3.  <span data-ttu-id="e7cfa-151">单击 **“可用值”**。</span><span class="sxs-lookup"><span data-stu-id="e7cfa-151">Click **Available Values**.</span></span>  
  
4.  <span data-ttu-id="e7cfa-152">单击 **“从查询中获取值”**。</span><span class="sxs-lookup"><span data-stu-id="e7cfa-152">Click **Get values from a query**.</span></span> <span data-ttu-id="e7cfa-153">随即将显示以下三个字段。</span><span class="sxs-lookup"><span data-stu-id="e7cfa-153">Three fields appear.</span></span>  
  
5.  <span data-ttu-id="e7cfa-154">在 **“数据集”** 的下拉列表中，单击在前面过程中创建的数据集的名称。</span><span class="sxs-lookup"><span data-stu-id="e7cfa-154">In **Dataset**, from the drop-down list, click the name of the dataset you created in the previous procedure.</span></span>  
  
6.  <span data-ttu-id="e7cfa-155">在 **“值”** 字段中，单击提供参数值的字段的名称。</span><span class="sxs-lookup"><span data-stu-id="e7cfa-155">In **Value** field, click the name of the field that provides the parameter value.</span></span>  
  
7.  <span data-ttu-id="e7cfa-156">在 **“标签”** 字段中，单击提供参数标签的字段的名称。</span><span class="sxs-lookup"><span data-stu-id="e7cfa-156">In **Label** field, click the name of the field that provides the parameter label.</span></span>  
  
8.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
 <span data-ttu-id="e7cfa-157">接下来，您将创建一个提供依赖参数的值的数据集。</span><span class="sxs-lookup"><span data-stu-id="e7cfa-157">Next, you will create a dataset that provides the values for a dependent parameter.</span></span>  
  
### <a name="to-create-a-dataset-to-provide-values-for-a-dependent-parameter"></a><span data-ttu-id="e7cfa-158">创建提供依赖参数的值的数据集</span><span class="sxs-lookup"><span data-stu-id="e7cfa-158">To create a dataset to provide values for a dependent parameter</span></span>  
  
1.  <span data-ttu-id="e7cfa-159">在“报表数据”窗格中，右键单击数据源，然后单击 **“添加数据集”**。</span><span class="sxs-lookup"><span data-stu-id="e7cfa-159">In the Report Data pane, right-click a data source, and then click **Add Dataset**.</span></span>  
  
2.  <span data-ttu-id="e7cfa-160">在 **“名称”** 中，键入数据集的名称。</span><span class="sxs-lookup"><span data-stu-id="e7cfa-160">In **Name**, type the name of the dataset.</span></span>  
  
3.  <span data-ttu-id="e7cfa-161">在 **“数据源”** 中，确保该名称是在第 1 步中选择的数据源的名称。</span><span class="sxs-lookup"><span data-stu-id="e7cfa-161">In **Data source**, verify the name is the name of the data source you chose in step 1.</span></span>  
  
4.  <span data-ttu-id="e7cfa-162">在 **“查询类型”** 中，选择所选数据源的查询类型。</span><span class="sxs-lookup"><span data-stu-id="e7cfa-162">In **Query type**, choose the type of query for the selected data source.</span></span> <span data-ttu-id="e7cfa-163">在本主题中，假定查询类型为 **“文本”** 。</span><span class="sxs-lookup"><span data-stu-id="e7cfa-163">In this topic, query type **Text** is assumed.</span></span>  
  
5.  <span data-ttu-id="e7cfa-164">在 **“查询”** 中，键入检索该参数的值所使用的查询。</span><span class="sxs-lookup"><span data-stu-id="e7cfa-164">In **Query**, type the query to use to retrieve values for this parameter.</span></span> <span data-ttu-id="e7cfa-165">对依赖参数的查询通常包含该参数所依赖的每个参数的查询参数。</span><span class="sxs-lookup"><span data-stu-id="e7cfa-165">Queries for dependent parameters typically include query parameters for each parameter that this parameter is dependent on.</span></span> <span data-ttu-id="e7cfa-166">例如，若要对提供某一类别（独立参数）的所有子类别（依赖参数）值的参数创建查询，可以使用如下 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句：</span><span class="sxs-lookup"><span data-stu-id="e7cfa-166">For example, to create a query for a parameter that provides all subcategory (dependent parameter) values for a category (independent parameter), you might use a [!INCLUDE[tsql](../../includes/tsql-md.md)] statement similar to the following:</span></span>  
  
    ```  
    SELECT DISTINCT Subcategory FROM <table>   
    WHERE (Category = @Category)  
    ```  
  
     <span data-ttu-id="e7cfa-167">在 WHERE 子句中，Category 是中的字段的名称， \<table> @Category 是查询参数。</span><span class="sxs-lookup"><span data-stu-id="e7cfa-167">In the WHERE clause, Category is the name of a field from \<table> and @Category is a query parameter.</span></span> <span data-ttu-id="e7cfa-168">该语句生成在 @Category 中指定的类别的子类别列表。</span><span class="sxs-lookup"><span data-stu-id="e7cfa-168">This statement produces a list of subcategories for the category specified in @Category.</span></span> <span data-ttu-id="e7cfa-169">在运行时，将使用用户为同名报表参数选择的值来填充该值。</span><span class="sxs-lookup"><span data-stu-id="e7cfa-169">At run time, this value will be filled in with the value that the user chooses for the report parameter that has the same name.</span></span>  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
 <span data-ttu-id="e7cfa-170">接下来，您将设置第二个参数的属性，以便在运行时使用该数据集填充其可用值。</span><span class="sxs-lookup"><span data-stu-id="e7cfa-170">Next, you will set the properties of the second parameter to use this dataset to populate its available values at run time.</span></span>  
  
### <a name="to-set-available-values-for-a-report-parameter"></a><span data-ttu-id="e7cfa-171">设置报表参数的可用值</span><span class="sxs-lookup"><span data-stu-id="e7cfa-171">To set available values for a report parameter</span></span>  
  
1.  <span data-ttu-id="e7cfa-172">在“报表数据”窗格的“参数”文件夹中，右键单击第一个参数，然后单击 **“参数属性”**。</span><span class="sxs-lookup"><span data-stu-id="e7cfa-172">In the Report Data pane, in the Parameters folder, right-click the first parameter, and then click **Parameter Properties**.</span></span>  
  
2.  <span data-ttu-id="e7cfa-173">在 **“名称”** 中，确保参数名称准确无误。</span><span class="sxs-lookup"><span data-stu-id="e7cfa-173">In **Name**, verify that the name of the parameter is correct.</span></span>  
  
3.  <span data-ttu-id="e7cfa-174">单击 **“可用值”**。</span><span class="sxs-lookup"><span data-stu-id="e7cfa-174">Click **Available Values**.</span></span>  
  
4.  <span data-ttu-id="e7cfa-175">单击 **“从查询中获取值”**。</span><span class="sxs-lookup"><span data-stu-id="e7cfa-175">Click **Get values from a query**.</span></span>  
  
5.  <span data-ttu-id="e7cfa-176">在 **“数据集”** 的下拉列表中，单击在前面过程中创建的数据集的名称。</span><span class="sxs-lookup"><span data-stu-id="e7cfa-176">In **Dataset**, from the drop-down list, click the name of the dataset you created in the previous procedure.</span></span>  
  
6.  <span data-ttu-id="e7cfa-177">在 **“值”** 字段中，单击提供参数值的字段的名称。</span><span class="sxs-lookup"><span data-stu-id="e7cfa-177">In **Value** field, click the name of the field that provides the parameter value.</span></span>  
  
7.  <span data-ttu-id="e7cfa-178">在 **“标签”** 字段中，单击提供参数标签的字段的名称。</span><span class="sxs-lookup"><span data-stu-id="e7cfa-178">In **Label** field, click the name of the field that provides the parameter label.</span></span>  
  
8.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-test-the-cascading-parameters"></a><span data-ttu-id="e7cfa-179">测试级联参数</span><span class="sxs-lookup"><span data-stu-id="e7cfa-179">To test the cascading parameters</span></span>  
  
1.  <span data-ttu-id="e7cfa-180">单击 **“运行”** 。</span><span class="sxs-lookup"><span data-stu-id="e7cfa-180">Click **Run**.</span></span>  
  
2.  <span data-ttu-id="e7cfa-181">从第一个独立参数的下拉列表中，选择一个值。</span><span class="sxs-lookup"><span data-stu-id="e7cfa-181">From the drop-down list for the first, independent parameter, choose a value.</span></span>  
  
     <span data-ttu-id="e7cfa-182">报表处理器运行下一个参数的数据集查询，并向该参数传递为第一个参数选择的值。</span><span class="sxs-lookup"><span data-stu-id="e7cfa-182">The report processor runs the dataset query for the next parameter and passes it the value you chose for the first parameter.</span></span> <span data-ttu-id="e7cfa-183">使用基于第一个参数值的可用值来填充第二个参数的下拉列表。</span><span class="sxs-lookup"><span data-stu-id="e7cfa-183">The drop-down list for the second parameter is populated with the available values based on the first parameter value.</span></span>  
  
3.  <span data-ttu-id="e7cfa-184">从第二个依赖参数的下拉列表中，选择一个值。</span><span class="sxs-lookup"><span data-stu-id="e7cfa-184">From the drop-down list for the second, dependent parameter, choose a value.</span></span>  
  
     <span data-ttu-id="e7cfa-185">在选择最后一个参数之后，不会自动运行报表，这样，您便可以更改您的选择。</span><span class="sxs-lookup"><span data-stu-id="e7cfa-185">The report does not run automatically after you choose the last parameter so that you can change your choice.</span></span>  
  
4.  <span data-ttu-id="e7cfa-186">单击“查看报表”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e7cfa-186">Click **View Report**.</span></span> <span data-ttu-id="e7cfa-187">报表根据您选择的参数来更新显示内容。</span><span class="sxs-lookup"><span data-stu-id="e7cfa-187">The report updates the display based on the parameters you have chosen.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7cfa-188">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e7cfa-188">See Also</span></span>  
 <span data-ttu-id="e7cfa-189">[添加、更改或删除报表参数 &#40;报表生成器和 SSRS&#41;](add-change-or-delete-a-report-parameter-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="e7cfa-189">[Add, Change, or Delete a Report Parameter &#40;Report Builder and SSRS&#41;](add-change-or-delete-a-report-parameter-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="e7cfa-190">[报表参数 &#40;报表生成器和报表设计器&#41;](report-parameters-report-builder-and-report-designer.md) </span><span class="sxs-lookup"><span data-stu-id="e7cfa-190">[Report Parameters &#40;Report Builder and Report Designer&#41;](report-parameters-report-builder-and-report-designer.md) </span></span>  
 <span data-ttu-id="e7cfa-191">[教程：向报表添加参数 &#40;报表生成器&#41;](../tutorial-add-a-parameter-to-your-report-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="e7cfa-191">[Tutorial: Add a Parameter to Your Report &#40;Report Builder&#41;](../tutorial-add-a-parameter-to-your-report-report-builder.md) </span></span>  
 <span data-ttu-id="e7cfa-192">[教程 &#40;报表生成器&#41;](../report-builder-tutorials.md) </span><span class="sxs-lookup"><span data-stu-id="e7cfa-192">[Tutorials &#40;Report Builder&#41;](../report-builder-tutorials.md) </span></span>  
 <span data-ttu-id="e7cfa-193">[添加数据集筛选器、数据区域筛选器和组筛选器 &#40;报表生成器和 SSRS&#41;](add-dataset-filters-data-region-filters-and-group-filters.md) </span><span class="sxs-lookup"><span data-stu-id="e7cfa-193">[Add Dataset Filters, Data Region Filters, and Group Filters &#40;Report Builder and SSRS&#41;](add-dataset-filters-data-region-filters-and-group-filters.md) </span></span>  
 [<span data-ttu-id="e7cfa-194">报表的嵌入数据集和共享数据集（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="e7cfa-194">Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;</span></span>](../report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)  
  
  
