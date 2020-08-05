---
title: 创建挖掘结构 (SQL Server 数据挖掘外接程序) |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining structures, creating
ms.assetid: b8b1eedc-4d6d-4429-a578-e629ec573934
author: minewiskan
ms.author: owend
ms.openlocfilehash: c75712a893c6271da291693f46771aa71263280e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580479"
---
# <a name="create-mining-structure-sql-server-data-mining-add-ins"></a><span data-ttu-id="ed6ae-102">创建挖掘结构（SQL Server 数据挖掘外接程序）</span><span class="sxs-lookup"><span data-stu-id="ed6ae-102">Create Mining Structure (SQL Server Data Mining Add-ins)</span></span>
  <span data-ttu-id="ed6ae-103">![“数据挖掘”功能区中的“创建挖掘结构”按钮](media/dmc-createstruct.gif "“数据挖掘”功能区中的“创建挖掘结构”按钮")</span><span class="sxs-lookup"><span data-stu-id="ed6ae-103">![Create Mining Structure button, Data Mining ribbon](media/dmc-createstruct.gif "Create Mining Structure button, Data Mining ribbon")</span></span>  
  
 <span data-ttu-id="ed6ae-104">如果要创建用于分析的数据集，而不需要创建模型，请使用 "**数据建模**" 组中的 "**高级**" 选项。</span><span class="sxs-lookup"><span data-stu-id="ed6ae-104">Use the **Advanced** option in the **Data Modeling** group when you want to create a data set used for analysis without necessarily creating a model.</span></span> <span data-ttu-id="ed6ae-105">在希望尝试使用不同算法时，此功能非常有用。</span><span class="sxs-lookup"><span data-stu-id="ed6ae-105">This is useful when you want to experiment with different algorithms.</span></span>  
  
 <span data-ttu-id="ed6ae-106">创建挖掘结构后，请使用[将模型添加到结构](add-model-to-structure-data-mining-add-ins-for-excel.md)向导来创建基于该结构的模型。</span><span class="sxs-lookup"><span data-stu-id="ed6ae-106">After you have created the mining structure, use the [Add Model to Structure](add-model-to-structure-data-mining-add-ins-for-excel.md) wizard to create a model based on that structure.</span></span> <span data-ttu-id="ed6ae-107">您还可以使用 "**数据挖掘高级查询编辑器**" 创建新模型。</span><span class="sxs-lookup"><span data-stu-id="ed6ae-107">You can also create new models by using the **Data Mining Advanced Query Editor**.</span></span>  
  
 <span data-ttu-id="ed6ae-108">如果使用高级算法之一（[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 支持这些算法，但是无法通过向导使用，例如线性回归或者顺序分析和聚类分析）生成模型，或是如果使用的是自定义算法，则也可以使用此选项。</span><span class="sxs-lookup"><span data-stu-id="ed6ae-108">You can also use this option when you intend to build models using one of the advanced algorithms, which are supported by [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] but not available through a wizard, such as linear regression or sequence clustering, or if you are using a custom algorithm.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ed6ae-109">创建挖掘结构时，也可以建立可用于验证所有模型的随机选择的测试数据集。</span><span class="sxs-lookup"><span data-stu-id="ed6ae-109">When you create the mining structure, you can also establish a randomly selected testing data set that you can use to validate all your models.</span></span> <span data-ttu-id="ed6ae-110">这样做十分方便，因为您可以针对公共数据集轻松地比较模型准确性。</span><span class="sxs-lookup"><span data-stu-id="ed6ae-110">This is handy because you can easily compare model accuracy against a common data set.</span></span> <span data-ttu-id="ed6ae-111">只需选择选项 "将**数据拆分为定型集和测试集**"，并指定要保留用于测试的数据的百分比，通常约为30%。</span><span class="sxs-lookup"><span data-stu-id="ed6ae-111">Just select the option, **Split data into training and testing sets** and specify an appropriate percentage of data to reserve for testing, usually around 30 percent.</span></span>  
  
## <a name="use-the-wizard-to-create-a-mining-structure"></a><span data-ttu-id="ed6ae-112">使用向导创建挖掘结构</span><span class="sxs-lookup"><span data-stu-id="ed6ae-112">Use the wizard to create a mining structure</span></span>  
  
1.  <span data-ttu-id="ed6ae-113">在 "**数据挖掘**" 功能区中，单击 "**高级**"，然后选择 "**创建结构**"。</span><span class="sxs-lookup"><span data-stu-id="ed6ae-113">In the **Data Mining** ribbon, click **Advanced**, and select **Create Structure**.</span></span>  
  
2.  <span data-ttu-id="ed6ae-114">在 "**选择源数据**" 对话框中，指定包含要用于分析的数据的 excel 区域、excel 数据表或外部数据源。</span><span class="sxs-lookup"><span data-stu-id="ed6ae-114">In the **Select source data** dialog box, specify the Excel range, Excel data table, or external data source that contains the data you want to use for analysis.</span></span>  
  
     <span data-ttu-id="ed6ae-115">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="ed6ae-115">Click **Next**.</span></span>  
  
3.  <span data-ttu-id="ed6ae-116">在 "**选择列**" 对话框中，查看所选数据源中可用列的列表。</span><span class="sxs-lookup"><span data-stu-id="ed6ae-116">In the **Select Columns** dialog box, review the list of columns available in the selected data source.</span></span>  
  
4.  <span data-ttu-id="ed6ae-117">单击列名右侧的箭头，以更改该列的**用法**，从以下值中进行选择：</span><span class="sxs-lookup"><span data-stu-id="ed6ae-117">Click the arrow to the right of the column name to change the **usage** of the column, choosing from these values:</span></span>  
  
    -   <span data-ttu-id="ed6ae-118">**Key**。</span><span class="sxs-lookup"><span data-stu-id="ed6ae-118">**Key**.</span></span> <span data-ttu-id="ed6ae-119">每个模型都需要至少一个键。</span><span class="sxs-lookup"><span data-stu-id="ed6ae-119">At least one key is required for each model.</span></span>  
  
    -   <span data-ttu-id="ed6ae-120">**关键时间**。</span><span class="sxs-lookup"><span data-stu-id="ed6ae-120">**Key time**.</span></span> <span data-ttu-id="ed6ae-121">此选项仅可用于预测模型（此选项在这些模型中是必需的）。</span><span class="sxs-lookup"><span data-stu-id="ed6ae-121">This option is available only for forecasting models, where it is required.</span></span>  
  
    -   <span data-ttu-id="ed6ae-122">**包括**。</span><span class="sxs-lookup"><span data-stu-id="ed6ae-122">**Include**.</span></span> <span data-ttu-id="ed6ae-123">指示列应包括在挖掘结构中，但不是键列。</span><span class="sxs-lookup"><span data-stu-id="ed6ae-123">Indicates that the column should be made available in the mining structure but is not a key column.</span></span>  
  
    -   <span data-ttu-id="ed6ae-124">**请勿使用**。</span><span class="sxs-lookup"><span data-stu-id="ed6ae-124">**Do not use**.</span></span> <span data-ttu-id="ed6ae-125">指示列不应包括在挖掘结构中。</span><span class="sxs-lookup"><span data-stu-id="ed6ae-125">Indicates that the column should not be included in the mining structure.</span></span>  
  
     <span data-ttu-id="ed6ae-126">请记住，您在生成模型时始终可以忽略列，但是以后添加列则需重新处理结构和模型。</span><span class="sxs-lookup"><span data-stu-id="ed6ae-126">Remember that you can always ignore columns when you build the model, but to add columns later requires that you reprocess the structure and model.</span></span>  
  
5.  <span data-ttu-id="ed6ae-127">单击 "浏览\*\* ( ..." ) \*\*按钮设置内容类型、数据类型和建模标志。</span><span class="sxs-lookup"><span data-stu-id="ed6ae-127">Click the browse **(...)** button to set the content type, data type, and modeling flags.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ed6ae-128">如果列中包含数值数据，则应始终打开此对话框以确保选择正确的数据类型。</span><span class="sxs-lookup"><span data-stu-id="ed6ae-128">If the column contains numeric data, you should always open this dialog box to ensure that the correct data type is chosen.</span></span> <span data-ttu-id="ed6ae-129">在某些情况下，即使输入数据是数字，您也需要将其视为类别变量或离散值，而不是连续数字。</span><span class="sxs-lookup"><span data-stu-id="ed6ae-129">In some cases, even if the input data is a number, you will want to treat it as a categorical variable, or discrete value, instead of a continuous number.</span></span>  
    >   
    >  <span data-ttu-id="ed6ae-130">例如，默认情况下，邮政编码列可能会作为连续的 Long 数据类型列出，但是为了获取更理想的结果，可以指定将其作为离散的文本值处理。</span><span class="sxs-lookup"><span data-stu-id="ed6ae-130">For example, a postal code column might be listed by default as a continuous long data type, but to get better results, you can specify that it be handled as a discrete text value.</span></span>  
    >   
    >  <span data-ttu-id="ed6ae-131">有关详细信息，请参阅为[数据挖掘选择数据](choosing-data-for-data-mining.md)中有关内容类型的部分。</span><span class="sxs-lookup"><span data-stu-id="ed6ae-131">For more information, see the section on content types in [Choosing Data for Data Mining](choosing-data-for-data-mining.md).</span></span>  
  
     <span data-ttu-id="ed6ae-132">单击 **“确定”** 关闭对话框。</span><span class="sxs-lookup"><span data-stu-id="ed6ae-132">Click **OK** to close the dialog box.</span></span>  
  
6.  <span data-ttu-id="ed6ae-133">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="ed6ae-133">Click **Next**.</span></span>  
  
     <span data-ttu-id="ed6ae-134">根据所用数据的类型，您可能希望在此步骤之后完成向导。</span><span class="sxs-lookup"><span data-stu-id="ed6ae-134">Depending on what type of data you are using, you might complete the wizard after this step.</span></span> <span data-ttu-id="ed6ae-135">在这种情况下，请跳转到 "**完成**" 页，为挖掘结构命名。</span><span class="sxs-lookup"><span data-stu-id="ed6ae-135">In that case, jump ahead to the **Finish** page to name your mining structure.</span></span>  
  
     <span data-ttu-id="ed6ae-136">对于其他模型，您可使用其他选项来创建测试数据集。</span><span class="sxs-lookup"><span data-stu-id="ed6ae-136">For other models, you have the additional option to create a testing data set.</span></span>  
  
7.  <span data-ttu-id="ed6ae-137">在 "将**数据拆分为定型和测试数据集**" 对话框中，指定数据的分区方式。</span><span class="sxs-lookup"><span data-stu-id="ed6ae-137">In the **Split data into training and testing data sets** dialog box, specify how you want your data partitioned.</span></span> <span data-ttu-id="ed6ae-138">默认情况下，30% 的数据用于测试。</span><span class="sxs-lookup"><span data-stu-id="ed6ae-138">By default, 30 percent of data is used for testing.</span></span>  
  
     <span data-ttu-id="ed6ae-139">可以选择键入要用于测试的最大行数。</span><span class="sxs-lookup"><span data-stu-id="ed6ae-139">Optionally, type the maximum number of rows to use for testing.</span></span>  
  
     <span data-ttu-id="ed6ae-140">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="ed6ae-140">Click **Next**.</span></span>  
  
8.  <span data-ttu-id="ed6ae-141">在 "**完成**" 对话框中，键入新挖掘结构的名称和描述。</span><span class="sxs-lookup"><span data-stu-id="ed6ae-141">In the **Finish** dialog, type a name and description for the new mining structure.</span></span>  
  
9. <span data-ttu-id="ed6ae-142">单击“完成”。</span><span class="sxs-lookup"><span data-stu-id="ed6ae-142">Click **Finish**.</span></span>  
  
### <a name="related-options"></a><span data-ttu-id="ed6ae-143">相关选项</span><span class="sxs-lookup"><span data-stu-id="ed6ae-143">Related Options</span></span>  
  
|<span data-ttu-id="ed6ae-144">选项</span><span class="sxs-lookup"><span data-stu-id="ed6ae-144">Option</span></span>|<span data-ttu-id="ed6ae-145">注释</span><span class="sxs-lookup"><span data-stu-id="ed6ae-145">Comments</span></span>|  
|------------|--------------|  
|<span data-ttu-id="ed6ae-146">"**选择源数据**" 对话框</span><span class="sxs-lookup"><span data-stu-id="ed6ae-146">**Select Source Data** dialog box</span></span>|<span data-ttu-id="ed6ae-147">选择 Excel 表时，您应指示数据是否已具有标题。</span><span class="sxs-lookup"><span data-stu-id="ed6ae-147">When you select an Excel table, you should indicate whether the data already has headers.</span></span> <span data-ttu-id="ed6ae-148">如果跳过此操作，则第一行数据将用作列名。</span><span class="sxs-lookup"><span data-stu-id="ed6ae-148">If you skip this, the first row of data will be used as the column name.</span></span><br /><br /> <span data-ttu-id="ed6ae-149">如果使用选项 "**外部数据源**"，则可以使用可在数据源中定义的任何类型的数据 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="ed6ae-149">If you use the option, **External data source**, you can use any kind of data that can be defined in an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] data source.</span></span> <span data-ttu-id="ed6ae-150">但是，外接程序中用于创建新数据源的对话框并非包含 Analysis Services 支持的所有数据源，因此我们建议您提前在 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 服务器上创建数据源，然后使用外接程序进行连接。</span><span class="sxs-lookup"><span data-stu-id="ed6ae-150">However, the dialog box in the add-in for creating new data sources does not include the full range of data sources supported by Analysis Services, so we recommend that you create the data sources on the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] server in advance and then connect using the add-ins.</span></span>|  
|<span data-ttu-id="ed6ae-151">"**数据源查询编辑器**" 对话框</span><span class="sxs-lookup"><span data-stu-id="ed6ae-151">**Data Source Query Editor** dialog box</span></span>|<span data-ttu-id="ed6ae-152">连接到指定数据源之后，可以添加列，或创建自定义查询以生成自定义列。</span><span class="sxs-lookup"><span data-stu-id="ed6ae-152">After you have connected to the specified data source, you can add columns, or create a custom query to generate custom columns.</span></span>|  
|<span data-ttu-id="ed6ae-153">**将数据拆分为定型数据集和测试数据集**</span><span class="sxs-lookup"><span data-stu-id="ed6ae-153">**Split data into training and testing data sets**</span></span>|<span data-ttu-id="ed6ae-154">对于定型和测试集，建议的值为70% （对于测试，则为30%）;但是，如果有大量数据，则可以指定用于测试的最大行数。</span><span class="sxs-lookup"><span data-stu-id="ed6ae-154">A recommended value for training vs. testing sets is 70 percent for training and 30 percent for testing; however, if you have a lot of data, you can specify a maximum number of rows for testing.</span></span>|  
|<span data-ttu-id="ed6ae-155">“完成”对话框</span><span class="sxs-lookup"><span data-stu-id="ed6ae-155">Finish dialog box</span></span>|<span data-ttu-id="ed6ae-156">用于钻取的选项对某些模型类型可用，如果您在挖掘结构中包含详细信息列，则这些选项非常有用。</span><span class="sxs-lookup"><span data-stu-id="ed6ae-156">The options for drillthrough are available on some model types and are very useful if you included detail columns in your mining structure.</span></span> <span data-ttu-id="ed6ae-157">例如，如果您创建一个聚类分析模型，则可以包含详细信息（如名称或电子邮件地址）用于钻取但不用于分析，以方便联系特定群集中的客户。</span><span class="sxs-lookup"><span data-stu-id="ed6ae-157">For example, if you create a clustering model, you can include details such as name or email address for drillthrough but not analysis, to make it easier to contact customers in a particular cluster.</span></span>|  
  
###  <a name="setting-column-usage-in-the-create-mining-structure-wizard"></a><a name="Bkmk_strctcolumn"></a><span data-ttu-id="ed6ae-158">在 "创建挖掘结构" 向导中设置列用法</span><span class="sxs-lookup"><span data-stu-id="ed6ae-158">Setting Column Usage in the Create Mining Structure Wizard</span></span>  
 <span data-ttu-id="ed6ae-159">创建新的挖掘结构时，可以指定在挖掘结构中应包括数据源中的哪些列以及应如何使用这些列。</span><span class="sxs-lookup"><span data-stu-id="ed6ae-159">When you create a new mining structure, you can specify which columns in the data source should be included in the mining structure, and how those columns should be used.</span></span> <span data-ttu-id="ed6ae-160">请记住，一个挖掘结构可以支持多个挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="ed6ae-160">Remember that a mining structure can support multiple mining models.</span></span>  
  
|<span data-ttu-id="ed6ae-161">值</span><span class="sxs-lookup"><span data-stu-id="ed6ae-161">Values</span></span>|<span data-ttu-id="ed6ae-162">说明</span><span class="sxs-lookup"><span data-stu-id="ed6ae-162">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="ed6ae-163">**包括**</span><span class="sxs-lookup"><span data-stu-id="ed6ae-163">**Include**</span></span>|<span data-ttu-id="ed6ae-164">指定该列包含可用于分析或预测的数据。</span><span class="sxs-lookup"><span data-stu-id="ed6ae-164">Specifies that the column contains data that can be used for analysis or prediction.</span></span>|  
|<span data-ttu-id="ed6ae-165">**Key**</span><span class="sxs-lookup"><span data-stu-id="ed6ae-165">**Key**</span></span>|<span data-ttu-id="ed6ae-166">指定该列包含事务 ID、序列 ID 或处理所需的另一个键。</span><span class="sxs-lookup"><span data-stu-id="ed6ae-166">Specifies that the column contains a transaction ID, a series ID, or another key required for processing.</span></span><br /><br /> <span data-ttu-id="ed6ae-167">所有算法均需要“键”列。</span><span class="sxs-lookup"><span data-stu-id="ed6ae-167">All algorithms require a Key column.</span></span> <span data-ttu-id="ed6ae-168">不过，有些算法仅允许单个键，有些算法则允许多个键。</span><span class="sxs-lookup"><span data-stu-id="ed6ae-168">However, some algorithms permit only a single key, while others permit multiple keys.</span></span><br /><br /> <span data-ttu-id="ed6ae-169">如果该列包含一个键，但没有进行处理，则选择 "不**使用**"。</span><span class="sxs-lookup"><span data-stu-id="ed6ae-169">If the column contains a key but is not required for processing, select **Do Not Use**.</span></span>|  
|<span data-ttu-id="ed6ae-170">**键时间**</span><span class="sxs-lookup"><span data-stu-id="ed6ae-170">**Key Time**</span></span>|<span data-ttu-id="ed6ae-171">指定该列包含可用于唯一标识时序中的项的日期或其他数值。</span><span class="sxs-lookup"><span data-stu-id="ed6ae-171">Specifies that the column contains a date or other numeric value that can be used to uniquely identify items in a time series.</span></span>|  
|<span data-ttu-id="ed6ae-172">**不要使用**</span><span class="sxs-lookup"><span data-stu-id="ed6ae-172">**Do Not Use**</span></span>|<span data-ttu-id="ed6ae-173">指定应忽略该列。</span><span class="sxs-lookup"><span data-stu-id="ed6ae-173">Specifies that the column should be ignored.</span></span> <span data-ttu-id="ed6ae-174">不会处理该列中的数据。</span><span class="sxs-lookup"><span data-stu-id="ed6ae-174">The data in the column will not be processed.</span></span>|  
  
 <span data-ttu-id="ed6ae-175">若要正确处理一个挖掘模型，该算法必须了解唯一地标识每行的键列、用于创建预测的目标列（如果要创建预测模型）以及创建用于预测目标列的关系时所用的输入列。</span><span class="sxs-lookup"><span data-stu-id="ed6ae-175">To process a model correctly, the algorithm must know which column is the key column that uniquely identifies each row, which column is the target column for creating predictions if you are creating a predictable model, and which columns to use as input columns to create the relationships that predict the target column.</span></span>  
  
-   <span data-ttu-id="ed6ae-176">指定为 "**不使用**" 的列不会出现在挖掘结构中。</span><span class="sxs-lookup"><span data-stu-id="ed6ae-176">Columns that are specified as **Do not use** will not be present in the mining structure.</span></span>  
  
     <span data-ttu-id="ed6ae-177">如果添加了不必要的列或具有错误值的列，则可能会对分析结果产生不利影响。</span><span class="sxs-lookup"><span data-stu-id="ed6ae-177">If you add columns that are unnecessary or have bad values, it can adversely affect the results of analysis.</span></span> <span data-ttu-id="ed6ae-178">因此，请确保只包括相关的列。</span><span class="sxs-lookup"><span data-stu-id="ed6ae-178">Therefore, be sure to include only those columns that are relevant.</span></span> <span data-ttu-id="ed6ae-179">不过，请记住，未在挖掘结构中使用的列将无法用于查询。</span><span class="sxs-lookup"><span data-stu-id="ed6ae-179">However, remember that the columns that you do not use in the mining structure will not be available for querying.</span></span>  
  
-   <span data-ttu-id="ed6ae-180">指定为**包含**类型的列将包括在挖掘结构中，稍后可用于挖掘模型中的分析或预测。</span><span class="sxs-lookup"><span data-stu-id="ed6ae-180">Columns that are specified as the **Include** type will be included in the mining structure and later can be used for either analysis or prediction in the mining models.</span></span>  
  
     <span data-ttu-id="ed6ae-181">如果不确定是否将需要使用该列，则可以在挖掘结构中始终包括该列，然后创建一个不使用该列的挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="ed6ae-181">If you are not sure whether you will need to use the column, you can always include the column in the mining structure and then create a mining model that does not use that column.</span></span> <span data-ttu-id="ed6ae-182">例如，您可以在数据中包括一个电话号码列用于以后引用，但创建一个忽略电话号码的聚类分析模型。</span><span class="sxs-lookup"><span data-stu-id="ed6ae-182">For example, you might include a phone number column in your data for later reference, but create a clustering model that ignores phone numbers.</span></span> <span data-ttu-id="ed6ae-183">创建分类之后，您可以创建将返回属于特定分类的人员的电话号码的查询。</span><span class="sxs-lookup"><span data-stu-id="ed6ae-183">After the clusters have been created, you can create a query that returns the phone numbers of people who belong to a particular cluster.</span></span>  
  
-   <span data-ttu-id="ed6ae-184">所有算法都需要**键**列。</span><span class="sxs-lookup"><span data-stu-id="ed6ae-184">All algorithms require a **Key** column.</span></span> <span data-ttu-id="ed6ae-185">“键”列中的值必须是唯一的。</span><span class="sxs-lookup"><span data-stu-id="ed6ae-185">The values in the Key column must be unique.</span></span> <span data-ttu-id="ed6ae-186">只有预测或时序模型需要**键时间**列。</span><span class="sxs-lookup"><span data-stu-id="ed6ae-186">A **Key Time** column is required only for forecasting or time series models.</span></span> <span data-ttu-id="ed6ae-187">.</span><span class="sxs-lookup"><span data-stu-id="ed6ae-187">.</span></span>  
  
### <a name="requirements"></a><span data-ttu-id="ed6ae-188">要求</span><span class="sxs-lookup"><span data-stu-id="ed6ae-188">Requirements</span></span>  
 <span data-ttu-id="ed6ae-189">若要创建数据挖掘结构，必须具有到 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 实例的连接。</span><span class="sxs-lookup"><span data-stu-id="ed6ae-189">To create a data mining structure, you must have a connection to an instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="ed6ae-190">连接是必需的，即使处理的是临时结构也需要连接。</span><span class="sxs-lookup"><span data-stu-id="ed6ae-190">A connection is required even if you are working with temporary structures.</span></span> <span data-ttu-id="ed6ae-191">有关如何创建或更改连接的详细信息，请参阅[连接到源数据 &#40;Excel 数据挖掘客户端&#41;](connect-to-source-data-data-mining-client-for-excel.md)。</span><span class="sxs-lookup"><span data-stu-id="ed6ae-191">For more information about how to create or change a connection, see [Connect to Source Data &#40;Data Mining Client for Excel&#41;](connect-to-source-data-data-mining-client-for-excel.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed6ae-192">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ed6ae-192">See Also</span></span>  
 [<span data-ttu-id="ed6ae-193">创建数据挖掘模型</span><span class="sxs-lookup"><span data-stu-id="ed6ae-193">Creating a Data Mining Model</span></span>](creating-a-data-mining-model.md)  
  
  
