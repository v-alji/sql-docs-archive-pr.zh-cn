---
title: 创建共享数据集或嵌入数据集（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: d1d7bc71-f0e9-4ce5-b3ad-6fee54388a31
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: fca74e1ba7965eeef6ce562e79e378af5bb9e145
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687515"
---
# <a name="create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs"></a><span data-ttu-id="cb65a-102">创建共享数据集或嵌入数据集（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="cb65a-102">Create a Shared Dataset or Embedded Dataset (Report Builder and SSRS)</span></span>
  <span data-ttu-id="cb65a-103">您可以创建供单个报表使用的嵌入数据集，也可以创建供多个报表使用的保存到报表服务器的共享数据集。</span><span class="sxs-lookup"><span data-stu-id="cb65a-103">You can create an embedded dataset for use in a single report or a shared dataset to save to a report server, for use by multiple reports.</span></span> <span data-ttu-id="cb65a-104">若要创建数据集，必须具有嵌入数据源或共享数据源。</span><span class="sxs-lookup"><span data-stu-id="cb65a-104">To create a dataset, you must have an embedded or shared data source.</span></span>

 <span data-ttu-id="cb65a-105">使用报表生成器可以执行以下任务：</span><span class="sxs-lookup"><span data-stu-id="cb65a-105">Use Report Builder to do the following tasks:</span></span>

-   <span data-ttu-id="cb65a-106">在数据集设计视图下创建共享数据集。</span><span class="sxs-lookup"><span data-stu-id="cb65a-106">Create a shared dataset in Dataset Design View.</span></span> <span data-ttu-id="cb65a-107">共享数据集必须使用已发布的共享数据源。</span><span class="sxs-lookup"><span data-stu-id="cb65a-107">Shared datasets must use published shared data sources.</span></span>

-   <span data-ttu-id="cb65a-108">在报表设计视图中创建嵌入数据集。</span><span class="sxs-lookup"><span data-stu-id="cb65a-108">Create an embedded dataset in Report Design View.</span></span>

-   <span data-ttu-id="cb65a-109">将数据集直接保存到报表服务器或 SharePoint 站点。</span><span class="sxs-lookup"><span data-stu-id="cb65a-109">Save the dataset directly to the report server or SharePoint site.</span></span>

 <span data-ttu-id="cb65a-110">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 中使用报表设计器可以执行以下任务：</span><span class="sxs-lookup"><span data-stu-id="cb65a-110">Use Report Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] to do the following tasks:</span></span>

1.  <span data-ttu-id="cb65a-111">在解决方案资源管理器中创建共享数据集。</span><span class="sxs-lookup"><span data-stu-id="cb65a-111">Create a shared dataset in Solution Explorer.</span></span> <span data-ttu-id="cb65a-112">共享数据集必须使用来自解决方案资源管理器的“共享数据源”文件夹中的数据源。</span><span class="sxs-lookup"><span data-stu-id="cb65a-112">Shared datasets must use data sources from the Shared Data Sources folder in Solution Explorer.</span></span>

2.  <span data-ttu-id="cb65a-113">在“报表数据”窗格中创建嵌入数据集。</span><span class="sxs-lookup"><span data-stu-id="cb65a-113">Create an embedded dataset in the Report Data pane.</span></span>

3.  <span data-ttu-id="cb65a-114">也可以将共享数据集和共享数据源与报表一起部署。</span><span class="sxs-lookup"><span data-stu-id="cb65a-114">Optionally deploy the shared datasets and shared data source with the report.</span></span> <span data-ttu-id="cb65a-115">对于每种类型的项，使用“项目属性”可以指定指向报表服务器或 SharePoint 站点上的文件夹的路径。</span><span class="sxs-lookup"><span data-stu-id="cb65a-115">For each type of item, use Project Properties to specify paths to folders on the report server or SharePoint site.</span></span>

 <span data-ttu-id="cb65a-116">有关详细信息，请参阅 [报表的嵌入数据集和共享数据集（报表生成器和 SSRS）](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="cb65a-116">For more information, see [Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md).</span></span>

> [!NOTE]
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]

### <a name="to-open-report-builder-and-create-a-shared-dataset"></a><span data-ttu-id="cb65a-117">打开报表生成器和创建共享数据集</span><span class="sxs-lookup"><span data-stu-id="cb65a-117">To open Report Builder and create a shared dataset</span></span>

1.  <span data-ttu-id="cb65a-118">打开报表生成器。</span><span class="sxs-lookup"><span data-stu-id="cb65a-118">Open Report Builder.</span></span> <span data-ttu-id="cb65a-119">**“新建报表或数据集”** 窗格将打开，如下图所示：</span><span class="sxs-lookup"><span data-stu-id="cb65a-119">The **New report or dataset pane** opens, as shown in the following figure:</span></span>

     <span data-ttu-id="cb65a-120">![rs_NewSharedDataset](../media/rs-newshareddataset.gif "rs_NewSharedDataset")</span><span class="sxs-lookup"><span data-stu-id="cb65a-120">![rs_NewSharedDataset](../media/rs-newshareddataset.gif "rs_NewSharedDataset")</span></span>

    > [!NOTE]
    >  <span data-ttu-id="cb65a-121"> 如果不显示 **“新建报表或数据集”** 窗格，则从“报表生成器”按钮中单击 **“新建”**。</span><span class="sxs-lookup"><span data-stu-id="cb65a-121">If the **New report or dataset pane** does not appear, from the Report Builder button, click **New**.</span></span>

2.  <span data-ttu-id="cb65a-122">在左窗格的 **“创建数据集”** 下，单击 **“共享数据集”**。</span><span class="sxs-lookup"><span data-stu-id="cb65a-122">In the left pane, under **Create a dataset**, click **Shared Dataset**.</span></span>

3.  <span data-ttu-id="cb65a-123">在右窗格中，单击 **“浏览”** 从报表服务器选择共享数据源，然后单击 **“创建”**。</span><span class="sxs-lookup"><span data-stu-id="cb65a-123">In the right pane, click **Browse** to select a shared data source from the report server, and then click **Create**.</span></span> <span data-ttu-id="cb65a-124">将打开与共享数据源关联的查询设计器。</span><span class="sxs-lookup"><span data-stu-id="cb65a-124">The query designer associated with the shared data source opens.</span></span>

4.  <span data-ttu-id="cb65a-125">在查询设计器中，指定要包含在数据集中的字段。</span><span class="sxs-lookup"><span data-stu-id="cb65a-125">In the query designer, specify the fields to include in the dataset.</span></span>

5.  <span data-ttu-id="cb65a-126">单击 "**运行** (**！**) 以运行查询。</span><span class="sxs-lookup"><span data-stu-id="cb65a-126">Click **Run** (**!**) to run the query.</span></span>

6.  <span data-ttu-id="cb65a-127">在 **“报表生成器”** 按钮上，单击 **“保存”** 或 **“另存为”** 将共享数据集保存到报表服务器。</span><span class="sxs-lookup"><span data-stu-id="cb65a-127">On the **Report Builder** button, click **Save** or **Save As** to save the shared dataset to the report server.</span></span>

7.  <span data-ttu-id="cb65a-128">若要退出报表生成器，请单击 **“报表生成器”**，然后单击 **“退出报表生成器”**。</span><span class="sxs-lookup"><span data-stu-id="cb65a-128">To exit Report Builder, click **Report Builder**, and then click **Exit Report Builder**.</span></span> <span data-ttu-id="cb65a-129">若要处理报表，请单击 **“报表生成器”**，然后单击 **“新建”** 或 **“打开”**。</span><span class="sxs-lookup"><span data-stu-id="cb65a-129">To work with reports, click **Report Builder**, and then click **New** or **Open**.</span></span>

### <a name="to-set-query-parameter-options"></a><span data-ttu-id="cb65a-130">设置查询参数选项</span><span class="sxs-lookup"><span data-stu-id="cb65a-130">To set query parameter options</span></span>

1.  <span data-ttu-id="cb65a-131">打开报表生成器。</span><span class="sxs-lookup"><span data-stu-id="cb65a-131">Open Report Builder.</span></span>

2.  <span data-ttu-id="cb65a-132">单击 **“打开”** 。</span><span class="sxs-lookup"><span data-stu-id="cb65a-132">Click **Open**.</span></span>

3.  <span data-ttu-id="cb65a-133">浏览到报表服务器，为共享数据源选择文件夹。</span><span class="sxs-lookup"><span data-stu-id="cb65a-133">Browse to the report server, and select the folder for the shared data source.</span></span>

4.  <span data-ttu-id="cb65a-134">在 **“项类型”** 的下拉列表中单击“数据集 (\*.rsd)”。</span><span class="sxs-lookup"><span data-stu-id="cb65a-134">In **Items of type**, click Datasets (\*.rsd) in the drop-down list.</span></span>

5.  <span data-ttu-id="cb65a-135">选中共享数据集，然后单击 **“打开”**。</span><span class="sxs-lookup"><span data-stu-id="cb65a-135">Select the shared dataset, and then click **Open**.</span></span> <span data-ttu-id="cb65a-136">将打开关联的查询设计器。</span><span class="sxs-lookup"><span data-stu-id="cb65a-136">The associated query designer opens.</span></span>

6.  <span data-ttu-id="cb65a-137">在功能区上，单击 **“数据集属性”**。</span><span class="sxs-lookup"><span data-stu-id="cb65a-137">On the Ribbon, click **Dataset Properties**.</span></span>

7.  <span data-ttu-id="cb65a-138">单击 **“参数”** 。</span><span class="sxs-lookup"><span data-stu-id="cb65a-138">Click **Parameters**.</span></span> <span data-ttu-id="cb65a-139">在此页上，将默认值设置为一个常量或者一个表达式，将该参数标记为只读、可以为 null 或“从查询中省略”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="cb65a-139">On this page, set a default value to a constant or an expression, mark the parameter as read-only, nullable, or **Omit From Query**.</span></span> <span data-ttu-id="cb65a-140">有关详细信息，请参阅[“数据集属性”对话框 ->参数（报表生成器）](../dataset-properties-dialog-box-parameters-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="cb65a-140">For more information, see [Dataset Properties Dialog Box, Parameters &#40;Report Builder&#41;](../dataset-properties-dialog-box-parameters-report-builder.md).</span></span>

8.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]


### <a name="to-create-a-dataset-from-a-sql-server-relational-database"></a><span data-ttu-id="cb65a-141">从 SQL Server 关系数据库创建数据集</span><span class="sxs-lookup"><span data-stu-id="cb65a-141">To create a dataset from a SQL Server relational database</span></span>

1.  <span data-ttu-id="cb65a-142">在“报表数据”窗格中，右键单击数据源的名称，然后单击 **“添加数据集”**。</span><span class="sxs-lookup"><span data-stu-id="cb65a-142">In the Report Data pane, right-click the name of the data source, and then click **Add Dataset**.</span></span> <span data-ttu-id="cb65a-143">此时将打开 **“数据集属性”** 对话框的 **“查询”** 页。</span><span class="sxs-lookup"><span data-stu-id="cb65a-143">The **Query** page of the **Dataset Properties** dialog box opens.</span></span>

2.  <span data-ttu-id="cb65a-144">在 **“名称”** 中，键入数据集的名称，或接受默认名称。</span><span class="sxs-lookup"><span data-stu-id="cb65a-144">In **Name**, type a name for the dataset or accept the default name.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="cb65a-145">数据集名称将在报表内部使用。</span><span class="sxs-lookup"><span data-stu-id="cb65a-145">The dataset name is used internally within the report.</span></span> <span data-ttu-id="cb65a-146">为便于识别，建议在数据集名称中对查询所返回的数据予以描述。</span><span class="sxs-lookup"><span data-stu-id="cb65a-146">For clarity, we recommend that the name of the dataset describe the data that the query returns.</span></span>

3.  <span data-ttu-id="cb65a-147">在 **“数据源”** 中，浏览并选择现有共享数据源的名称，或单击 **“新建”** 创建新的嵌入数据源。</span><span class="sxs-lookup"><span data-stu-id="cb65a-147">In **Data source**, browse to and select the name of an existing shared data source, or click **New** to create a new embedded data source.</span></span>

4.  <span data-ttu-id="cb65a-148">选择 **“查询类型”** 选项。</span><span class="sxs-lookup"><span data-stu-id="cb65a-148">Select a **Query type** option.</span></span> <span data-ttu-id="cb65a-149">具体选项取决于数据源类型。</span><span class="sxs-lookup"><span data-stu-id="cb65a-149">Options depend on the data source type.</span></span>

    -   <span data-ttu-id="cb65a-150">选择 **Text** 可以采用该数据源的查询语言编写查询。</span><span class="sxs-lookup"><span data-stu-id="cb65a-150">Select **Text** to write a query using the query language of the data source.</span></span>

    -   <span data-ttu-id="cb65a-151">选择 **Table** 可以返回关系数据库表中的所有字段。</span><span class="sxs-lookup"><span data-stu-id="cb65a-151">Select **Table** to return all the fields in a relational database table.</span></span>

    -   <span data-ttu-id="cb65a-152">选择 **StoredProcedure** 可以按名称运行存储过程。</span><span class="sxs-lookup"><span data-stu-id="cb65a-152">Select **StoredProcedure** to run a stored procedure by name.</span></span>

5.  <span data-ttu-id="cb65a-153">在 **“查询”** 中，键入查询、存储过程或表名。</span><span class="sxs-lookup"><span data-stu-id="cb65a-153">In **Query**, type the query, stored procedure, or table name.</span></span> <span data-ttu-id="cb65a-154">此外，也可以单击 **“查询设计器”** 打开图形查询设计器或基于文本的查询设计器工具，或单击 **“导入”** 从现有报表中导入查询。</span><span class="sxs-lookup"><span data-stu-id="cb65a-154">Alternatively, click **Query Designer** to open the graphical or text-based query designer tool, or **Import** to import the query from an existing report.</span></span>

     <span data-ttu-id="cb65a-155">在少数情况下，查询指定的字段集合只能通过在数据源中运行查询来确定。</span><span class="sxs-lookup"><span data-stu-id="cb65a-155">In a few cases, the field collection specified by the query can only be determined by running the query on the data source.</span></span> <span data-ttu-id="cb65a-156">例如，存储过程可能在结果集中返回可变字段集。</span><span class="sxs-lookup"><span data-stu-id="cb65a-156">For example, a stored procedure may return a variable set of fields in the result set.</span></span> <span data-ttu-id="cb65a-157">单击 **“刷新字段”** 可以在数据源中运行查询，并检索填充“报表数据”窗格中的数据集字段集合时所需的字段名称。</span><span class="sxs-lookup"><span data-stu-id="cb65a-157">Click **Refresh Fields** to run the query on the data source and retrieve the field names that are needed to populate the dataset field collection in the Report Data pane.</span></span> <span data-ttu-id="cb65a-158">关闭 **“数据集属性”** 对话框后，将在数据集节点下显示字段集合。</span><span class="sxs-lookup"><span data-stu-id="cb65a-158">The field collection appears under the dataset node after you close the **Dataset Properties** dialog box.</span></span>

6.  <span data-ttu-id="cb65a-159">在 **“超时”** 中，键入报表服务器等待数据库响应的秒数。</span><span class="sxs-lookup"><span data-stu-id="cb65a-159">In **Timeout**, type the number of seconds that the report server waits for a response from the database.</span></span> <span data-ttu-id="cb65a-160">默认值为 0 秒。</span><span class="sxs-lookup"><span data-stu-id="cb65a-160">The default value is 0 seconds.</span></span> <span data-ttu-id="cb65a-161">超时值为 0 秒时，查询将不会超时。</span><span class="sxs-lookup"><span data-stu-id="cb65a-161">When the time out value is 0 seconds, the query does not time out.</span></span>

7.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]

     <span data-ttu-id="cb65a-162">数据集及其字段集合显示在“报表数据”窗格的数据源节点下。</span><span class="sxs-lookup"><span data-stu-id="cb65a-162">The dataset and its field collection appear in the Report Data pane under the data source node.</span></span>

## <a name="see-also"></a><span data-ttu-id="cb65a-163">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cb65a-163">See Also</span></span>
 <span data-ttu-id="cb65a-164">[报表嵌入数据集和共享数据集 &#40;报表生成器和 ssrs&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) [数据集字段集合 &#40;报表生成器和 Ssrs&#41;](dataset-fields-collection-report-builder-and-ssrs.md) [查询设计器 &#40;报表生成器](../query-designers-report-builder.md)&#41;报表生成器[的对话框、窗格和向导](../report-builder-help-for-dialog-boxes-panes-and-wizards.md)[将数据添加到报表 &#40;报表生成器和](report-datasets-ssrs.md)共享数据集中&#41;[数据连接、数据源和连接字符串](../data-connections-data-sources-and-connection-strings-in-report-builder.md)报表生成器[&#40;和 ssrs](embedded-and-shared-datasets-report-builder-and-ssrs.md)报表生成器</span><span class="sxs-lookup"><span data-stu-id="cb65a-164">[Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) [Dataset Fields Collection &#40;Report Builder and SSRS&#41;](dataset-fields-collection-report-builder-and-ssrs.md) [Query Designers &#40;Report Builder&#41;](../query-designers-report-builder.md) [Report Builder Help for Dialog Boxes, Panes, and Wizards](../report-builder-help-for-dialog-boxes-panes-and-wizards.md) [Add Data to a Report &#40;Report Builder and SSRS&#41;](report-datasets-ssrs.md) [Data Connections, Data Sources, and Connection Strings in Report Builder](../data-connections-data-sources-and-connection-strings-in-report-builder.md) [Embedded and Shared Datasets &#40;Report Builder and SSRS&#41;](embedded-and-shared-datasets-report-builder-and-ssrs.md)</span></span>


