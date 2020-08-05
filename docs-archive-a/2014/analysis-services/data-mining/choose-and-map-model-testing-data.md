---
title: 选择和映射模型测试数据 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- columns [data mining], mining accuracy charts
- Mining Accuracy Chart [Analysis Services], column mappings
- input column mapping [Analysis Services]
- mapping input columns [Analysis Services]
ms.assetid: be0d9f20-40c3-4dac-81da-281cfe724126
author: minewiskan
ms.author: owend
ms.openlocfilehash: 84f1d01c40070069d610bb028ab003223c5afbcd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581039"
---
# <a name="choose-and-map-model-testing-data"></a><span data-ttu-id="49d16-102">选择和映射模型测试数据</span><span class="sxs-lookup"><span data-stu-id="49d16-102">Choose and Map Model Testing Data</span></span>
  <span data-ttu-id="49d16-103">若要在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]中创建准确性图表，您必须选择将用于测试模型的数据，并且将数据映射到模型。</span><span class="sxs-lookup"><span data-stu-id="49d16-103">To create an accuracy chart in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], you must choose the data that will be used to test the model, and map the data to the model.</span></span>  
  
 <span data-ttu-id="49d16-104">默认情况下， [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 将使用挖掘模型测试数据，只要在生成挖掘结构时创建了维持数据集。</span><span class="sxs-lookup"><span data-stu-id="49d16-104">By default, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] will use the mining model testing data, provided that you created a holdout data set when you built the mining structure.</span></span> <span data-ttu-id="49d16-105">创建维持测试集是测试基于相同挖掘结构的模型的最简单方式，因为列名和数据类型将始终与该模型匹配，并且您可以合理地确定数据分布是相似的。</span><span class="sxs-lookup"><span data-stu-id="49d16-105">Creating a holdout test set is the easiest way to test models that are based on the same mining structure, because the column names and data types will always match the model, and you can be reasonably assured that the distribution of the data is similar.</span></span> <span data-ttu-id="49d16-106">此外，设计器将自动创建输入和模型列之间的关系。</span><span class="sxs-lookup"><span data-stu-id="49d16-106">Also, the designer will automatically create the relationships between the input and model columns.</span></span>  
  
 <span data-ttu-id="49d16-107">或者，您可以指定外部数据源。</span><span class="sxs-lookup"><span data-stu-id="49d16-107">Alternatively, you can specify an external source of data.</span></span> <span data-ttu-id="49d16-108">对于外部数据，有一些其他要求：</span><span class="sxs-lookup"><span data-stu-id="49d16-108">For external data, there are some additional requirements:</span></span>  
  
-   <span data-ttu-id="49d16-109">外部数据集必须定义为 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]实例中的数据源视图。</span><span class="sxs-lookup"><span data-stu-id="49d16-109">The external data set must be defined as a data source view in an instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="49d16-110">外部数据集必须至少包含一个可映射到挖掘模型中可预测列的列。</span><span class="sxs-lookup"><span data-stu-id="49d16-110">The external data set must at least contain one column that can be mapped to the predictable column in the mining model.</span></span> <span data-ttu-id="49d16-111">可以选择忽略某些列。</span><span class="sxs-lookup"><span data-stu-id="49d16-111">You can choose to ignore some columns.</span></span>  
  
-   <span data-ttu-id="49d16-112">不能在另一个数据源视图中添加新列或映射列。</span><span class="sxs-lookup"><span data-stu-id="49d16-112">You cannot add new columns or map columns in a different data source view.</span></span> <span data-ttu-id="49d16-113">选择的数据源视图必须包含预测查询所需的所有列。</span><span class="sxs-lookup"><span data-stu-id="49d16-113">The data source view that you select must contain all the columns that you need for the prediction query.</span></span>  
  
-   <span data-ttu-id="49d16-114">如果外部列名称与模型中的列名称完全匹配，则设计器将自动映射这些列。</span><span class="sxs-lookup"><span data-stu-id="49d16-114">If the external column names exactly match those in the model, the designer will map them for you.</span></span> <span data-ttu-id="49d16-115">如果映射是错误的，您可以更改这些映射，或者删除它们并为现有列创建新映射。</span><span class="sxs-lookup"><span data-stu-id="49d16-115">If the mappings are wrong, you can change them, or delete and create new mappings for existing columns.</span></span>  
  
-   <span data-ttu-id="49d16-116">如果您使用外部数据源，则可以应用筛选器以将测试数据限制为事例的相关子集。</span><span class="sxs-lookup"><span data-stu-id="49d16-116">If you use an external data source, you can apply filters to restrict the testing data to a relevant subset of cases.</span></span>  
  
-   <span data-ttu-id="49d16-117">即使在使用维持测试集时，您也应知道筛选器可能在与挖掘结构关联的测试数据和挖掘模型测试事例之间导致差异。</span><span class="sxs-lookup"><span data-stu-id="49d16-117">Even when you use the holdout test set, you should be aware that filters can cause differences between the testing data associated with a mining structure and the mining model test cases.</span></span>  
  
 <span data-ttu-id="49d16-118">本主题描述如何选择和映射测试数据：</span><span class="sxs-lookup"><span data-stu-id="49d16-118">This topic describes how to choose and map the testing data:</span></span>  
  
 [<span data-ttu-id="49d16-119">选择输入表以测试挖掘模型的准确性</span><span class="sxs-lookup"><span data-stu-id="49d16-119">Select input tables to test the accuracy of a mining model</span></span>](#bkmk_SelectInputs)  
  
 [<span data-ttu-id="49d16-120">将输入列映射到测试数据中的列</span><span class="sxs-lookup"><span data-stu-id="49d16-120">Map model columns to the columns in the testing data</span></span>](#bkmk_MapColumns)  
  
 [<span data-ttu-id="49d16-121">更改测试数据中的列映射到模型的方式</span><span class="sxs-lookup"><span data-stu-id="49d16-121">Change the way that columns in the testing data are mapped to the model</span></span>](#bkmk_ChangeMappings)  
  
##  <a name="to-select-input-tables-to-test-the-accuracy-of-a-mining-model"></a><a name="bkmk_SelectInputs"></a> <span data-ttu-id="49d16-122">选择输入表以测试挖掘模型的准确性</span><span class="sxs-lookup"><span data-stu-id="49d16-122">To select input tables to test the accuracy of a mining model</span></span>  
  
1.  <span data-ttu-id="49d16-123">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中的数据挖掘设计器中，双击包含要制作图表的模型的挖掘结构。</span><span class="sxs-lookup"><span data-stu-id="49d16-123">In Data Mining Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], double-click the mining structure that contains the models you want to chart.</span></span>  
  
2.  <span data-ttu-id="49d16-124">选择 **“挖掘准确性图表”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="49d16-124">Select the **Mining Accuracy Chart** tab.</span></span>  
  
3.  <span data-ttu-id="49d16-125">在 **“挖掘准确性图表”** 视图的 **“输入选择”** 选项卡中，选择下面的选项之一：</span><span class="sxs-lookup"><span data-stu-id="49d16-125">On the **Input Selection Tab** of the **Mining Accuracy Chart** view, select one of the following options:</span></span>  
  
     <span data-ttu-id="49d16-126">**使用挖掘模型测试事例**</span><span class="sxs-lookup"><span data-stu-id="49d16-126">**Use mining model test cases**</span></span>  
  
     <span data-ttu-id="49d16-127">**使用挖掘结构测试事例**</span><span class="sxs-lookup"><span data-stu-id="49d16-127">**Use mining structure test cases**</span></span>  
  
     <span data-ttu-id="49d16-128">**指定其他数据集**</span><span class="sxs-lookup"><span data-stu-id="49d16-128">**Specify a different data set**</span></span>  
  
4.  <span data-ttu-id="49d16-129">如果您选择的是 **“指定其他数据集”**，则可以选择单击 **“打开筛选器编辑器”** 来针对输入数据集创建筛选条件。</span><span class="sxs-lookup"><span data-stu-id="49d16-129">If you selected **Specify a different data set**, optionally click **Open Filter Editor** to create filter conditions on the input data set.</span></span> [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
5.  <span data-ttu-id="49d16-130">单击 **“提升图”** 选项卡或 **“分类矩阵”** 选项卡，使用指定的测试数据自动生成该图表。</span><span class="sxs-lookup"><span data-stu-id="49d16-130">Click the **Lift Chart** tab or the **Classification Matrix** tab to automatically build the chart by using the testing data you specified.</span></span>  
  
##  <a name="to-map-model-columns-to-the-columns-in-the-testing-data"></a><a name="bkmk_MapColumns"></a> <span data-ttu-id="49d16-131">将模型列映射到测试数据中的列</span><span class="sxs-lookup"><span data-stu-id="49d16-131">To map model columns to the columns in the testing data</span></span>  
  
1.  <span data-ttu-id="49d16-132">双击包含要建立图表的模型的挖掘结构，以在数据挖掘设计器中打开结构和模型。</span><span class="sxs-lookup"><span data-stu-id="49d16-132">Double-click the mining structure that contains the models you want to chart, to open the structure and models in Data Mining Designer.</span></span>  
  
2.  <span data-ttu-id="49d16-133">选择“挖掘准确性图表” \*\*\*\* 选项卡，然后选择“输入选择” \*\*\*\* 选项卡。</span><span class="sxs-lookup"><span data-stu-id="49d16-133">Select the **Mining Accuracy Chart** tab, and then select the **Input Selection** tab.</span></span>  
  
3.  <span data-ttu-id="49d16-134">在 **“输入选择”** 选项卡中的 **“选择要用于准确性图表的数据集”** 下，选择 **“指定其他数据集”**。</span><span class="sxs-lookup"><span data-stu-id="49d16-134">In the **Input Selection** tab, under **Select data set to be used for Accuracy Chart**, select **Specify a different data set**.</span></span>  
  
4.  <span data-ttu-id="49d16-135">单击 "浏览" 按钮\*\* ( ... ") \*\*打开一个对话框并生成外部数据集的定义。</span><span class="sxs-lookup"><span data-stu-id="49d16-135">Click the browse button **(...)** to open a dialog box and build the definition of the external data set.</span></span>  
  
5.  <span data-ttu-id="49d16-136">在 **“选择挖掘结构”** 对话框中，选择包含您要使用的模型的挖掘结构，然后单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="49d16-136">In the **Select Mining Structure** dialog box, select the mining structure that contains the models you want to work with, and then click **OK**.</span></span>  
  
6.  <span data-ttu-id="49d16-137">在“挖掘准确性图表”选项卡的“选择输入表”表上，单击“选择事例表”以打开“选择表”对话框\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="49d16-137">On the **Select Input Table(s)** table of the **Mining Accuracy Chart** tab, click **Select Case Table** to open the **Select Table** dialog box.</span></span>  
  
7.  <span data-ttu-id="49d16-138">在 **“选择表”** 对话框中，从 **“数据源”** 列表中选择数据源。</span><span class="sxs-lookup"><span data-stu-id="49d16-138">In the **Select Table** dialog box, select a data source from the **Data Source** list.</span></span> <span data-ttu-id="49d16-139">选择一个表，其中包含预测查询中要用来确定模型准确性的数据。</span><span class="sxs-lookup"><span data-stu-id="49d16-139">Choose a table that contains the data that you want to use in the prediction queries to determine the accuracy of the models.</span></span>  
  
8.  <span data-ttu-id="49d16-140">在“表/视图名称”\*\*\*\* 框中，选择包含要用来测试模型的数据的表。</span><span class="sxs-lookup"><span data-stu-id="49d16-140">In the **Table/View Name** box, select the table that contains the data that you want to use to test the models.</span></span>  
  
9. <span data-ttu-id="49d16-141">根据需要编辑映射。</span><span class="sxs-lookup"><span data-stu-id="49d16-141">Edit the mappings, if necessary.</span></span> <span data-ttu-id="49d16-142">挖掘结构中的列将自动映射到输入表中具有相同名称的列。</span><span class="sxs-lookup"><span data-stu-id="49d16-142">Columns in the mining structure are automatically mapped to the columns with the same name in the input table.</span></span> <span data-ttu-id="49d16-143">若要手动创建映射，请单击“选择输入表”表中的列并将它拖到“挖掘结构”表中相应的列\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="49d16-143">To manually create mappings, click a column in the **Select Input Table(s)** table and drag it onto the corresponding column in the **Mining Structure** table.</span></span> <span data-ttu-id="49d16-144">若要删除映射，请单击将“挖掘结构”表中的列链接到“选择输入表”表中的映射列的行，然后按 Delete\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="49d16-144">To delete a mapping, click the line that links the column in the **Mining Structure** table to the mapped column in the **Select Input Table(s)** table, and then press DELETE.</span></span>  
  
10. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##  <a name="to-modify-the-way-input-data-is-mapped-to-the-model"></a><a name="bkmk_ChangeMappings"></a> <span data-ttu-id="49d16-145">修改输入数据映射到模型的方式</span><span class="sxs-lookup"><span data-stu-id="49d16-145">To modify the way input data is mapped to the model</span></span>  
  
1.  <span data-ttu-id="49d16-146">在数据挖掘设计器中，双击包含要制作图表的模型的结构。</span><span class="sxs-lookup"><span data-stu-id="49d16-146">In Data Mining Designer, double-click the structure that contains the models you want to chart.</span></span>  
  
2.  <span data-ttu-id="49d16-147">选择 **“挖掘准确性图表”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="49d16-147">Select the **Mining Accuracy Chart** tab.</span></span>  
  
3.  <span data-ttu-id="49d16-148">单击 **“输入选择”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="49d16-148">Click the **Input Selection** tab.</span></span>  
  
4.  <span data-ttu-id="49d16-149">在 "**选择要用于准确性图表的数据集**" 中，选择选项 "**指定其他数据集**"。</span><span class="sxs-lookup"><span data-stu-id="49d16-149">In **Select data set to be used for Accuracy Chart**, select the option **Specify a different data set**.</span></span>  
  
5.  <span data-ttu-id="49d16-150">单击 "浏览" 按钮\*\* ( ... ") \*\*可打开一个对话框，并生成外部数据源的定义。</span><span class="sxs-lookup"><span data-stu-id="49d16-150">Click the browse button **(...)** to open a dialog box and build the definition of the external data source.</span></span>  
  
6.  <span data-ttu-id="49d16-151">在 **“指定列映射”** 对话框中，单击 **“选择事例表”**。</span><span class="sxs-lookup"><span data-stu-id="49d16-151">In the **Specify Column Mapping** dialog box, click **Select Case Table**.</span></span>  
  
7.  <span data-ttu-id="49d16-152">在“选择表”对话框中，从列表中选择数据源视图，然后选择包含事例数据的表。</span><span class="sxs-lookup"><span data-stu-id="49d16-152">In the Select Table dialog box, Select a data source view from the list, and select the table that contains the case data.</span></span> [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
8.  <span data-ttu-id="49d16-153">如果所需的表不可用，则关闭该对话框，然后创建一个包含该表的新的数据源视图。</span><span class="sxs-lookup"><span data-stu-id="49d16-153">If the tables you need are not available, close the dialog box and create a new data source view that contains the table.</span></span> <span data-ttu-id="49d16-154">有关如何创建数据源视图的信息，请参阅[定义数据源视图 (Analysis Services)](../multidimensional-models/defining-a-data-source-view-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="49d16-154">For information about how to create a data source view, see [Defining a Data Source View &#40;Analysis Services&#41;](../multidimensional-models/defining-a-data-source-view-analysis-services.md).</span></span>  
  
9. <span data-ttu-id="49d16-155">如果挖掘模型包含嵌套表，则单击 **“选择嵌套表”**，然后从数据源视图的表的列表中选择该嵌套表。</span><span class="sxs-lookup"><span data-stu-id="49d16-155">If the mining model contains a nested table, click **Select Nested Table**, and select the nested table from the list of tables in the data source view.</span></span> [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
10. <span data-ttu-id="49d16-156">选择要修改的映射的联接线，然后选择 **“修改连接”**。</span><span class="sxs-lookup"><span data-stu-id="49d16-156">Select the join line of the mapping you want to modify, and select **Modify Connections**.</span></span>  
  
     <span data-ttu-id="49d16-157">此时，将打开 **“修改映射”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="49d16-157">The **Modify Mapping** dialog box opens.</span></span> <span data-ttu-id="49d16-158">在此对话框的表中， **“挖掘结构列”** 列出了所选挖掘结构包含的每个列； **“表列”** 列出了输出表中的列，这些列映射到挖掘结构中的列。</span><span class="sxs-lookup"><span data-stu-id="49d16-158">In the table in this dialog box, **Mining Structure Column** lists each column that the selected mining structure contains, and **Table Column** lists the columns from input tables that are mapped to columns in the mining structure.</span></span>  
  
11. <span data-ttu-id="49d16-159">在 **“表列”** 下，选择与要修改其关系的 **“挖掘结构列”** 下的行对应的行。</span><span class="sxs-lookup"><span data-stu-id="49d16-159">Under **Table Column**, select the row that corresponds to the row under **Mining Structure Column** for which you want to modify a relationship.</span></span> <span data-ttu-id="49d16-160">从列表中选择一个新列，或者从列表中选择空白项以删除该列。</span><span class="sxs-lookup"><span data-stu-id="49d16-160">Select a new column from the list, or select the blank entry from the list to delete the column.</span></span>  
  
12. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     <span data-ttu-id="49d16-161">**“指定列映射”** 对话框中将显示新的列映射。</span><span class="sxs-lookup"><span data-stu-id="49d16-161">The new column mappings are displayed in the **Specify Column Mapping** dialog box.</span></span> <span data-ttu-id="49d16-162">通过选择列之间的连线，然后按 Delete 键，可以删除映射。</span><span class="sxs-lookup"><span data-stu-id="49d16-162">You can remove a mapping by selecting the line between the columns and pressing the DELETE key.</span></span> <span data-ttu-id="49d16-163">通过在“挖掘结构”表中选择列，然后将其拖到“选择输入表”表中的对应列，可以创建一个新连接\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="49d16-163">You can create a new connection by selecting a column in the **Mining Structure** table and dragging it to the corresponding column in the **SelectInput Table(s)** table.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49d16-164">另请参阅</span><span class="sxs-lookup"><span data-stu-id="49d16-164">See Also</span></span>  
 [<span data-ttu-id="49d16-165">测试和验证任务和操作指南（数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="49d16-165">Testing and Validation Tasks and How-tos &#40;Data Mining&#41;</span></span>](testing-and-validation-tasks-and-how-tos-data-mining.md)  
  
  
