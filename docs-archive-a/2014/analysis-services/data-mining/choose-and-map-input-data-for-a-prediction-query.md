---
title: 为预测查询选择和映射输入数据 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- tables [Analysis Services], prediction queries
- Mining Model Prediction [Analysis Services], input tables
ms.assetid: 00d330a0-879d-4da0-9f29-53c288116f4d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 54e11752d6278e01e50a379bf7bb57521ff9bb29
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581043"
---
# <a name="choose-and-map-input-data-for-a-prediction-query"></a><span data-ttu-id="50427-102">为预测查询选择和映射输入数据</span><span class="sxs-lookup"><span data-stu-id="50427-102">Choose and Map Input Data for a Prediction Query</span></span>
  <span data-ttu-id="50427-103">在您根据挖掘模型创建预测时，通常通过向模型馈送新数据来创建预测。</span><span class="sxs-lookup"><span data-stu-id="50427-103">When you create predictions from a mining model, you generally do this by feeding new data into the model.</span></span> <span data-ttu-id="50427-104">（时序模型是个例外情况，它只能基于历史数据进行预测。）若要向模型提供新数据，您必须确保数据可作为数据源视图的一部分提供。</span><span class="sxs-lookup"><span data-stu-id="50427-104">(The exception is time series models, which can make predictions based on historical data only.) To provide the model with new data, you must make sure that the data is available as part of a data source view.</span></span> <span data-ttu-id="50427-105">如果您事先知道哪些数据将用于预测，则可以在用于创建模型的数据源视图中包括这些数据。</span><span class="sxs-lookup"><span data-stu-id="50427-105">If you know in advance which data you will use for prediction, you can include it in the data source view that you used to create the model.</span></span> <span data-ttu-id="50427-106">否则，您可能需要创建一个新的数据源视图。</span><span class="sxs-lookup"><span data-stu-id="50427-106">Otherwise, you might have to create a new data source view.</span></span> <span data-ttu-id="50427-107">有关详细信息，请参阅 [多维模型中的数据源视图](../multidimensional-models/data-source-views-in-multidimensional-models.md)。</span><span class="sxs-lookup"><span data-stu-id="50427-107">For more information, see [Data Source Views in Multidimensional Models](../multidimensional-models/data-source-views-in-multidimensional-models.md).</span></span>  
  
 <span data-ttu-id="50427-108">有时候，您所需的数据可能包含在一对多联接中的多个表内。</span><span class="sxs-lookup"><span data-stu-id="50427-108">Sometimes the data that you need might be contained within more than one table in a one-to-many join.</span></span> <span data-ttu-id="50427-109">用于关联模型或顺序分析和聚类分析模型的数据便是这种情况，它们将使用链接到包含产品或事务详细信息的嵌套表的事例表。</span><span class="sxs-lookup"><span data-stu-id="50427-109">This is the case with data used for association models or sequence clustering models, which use a case table linked to a nested table that contains product or transaction details.</span></span> <span data-ttu-id="50427-110">如果您的模型使用事例嵌套表结构，则您用于预测的数据也必须具有事例嵌套表结构。</span><span class="sxs-lookup"><span data-stu-id="50427-110">If your model uses a case-nested table structure, the data that you use for prediction must also have a case-nested table structure.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="50427-111">不能添加位于其他数据源视图中的新列或映射列。</span><span class="sxs-lookup"><span data-stu-id="50427-111">You cannot add new columns or map columns that are in a different data source view.</span></span> <span data-ttu-id="50427-112">选择的数据源视图必须包含预测查询所需的所有列。</span><span class="sxs-lookup"><span data-stu-id="50427-112">The data source view that you select must contain all the columns that you need for the prediction query.</span></span>  
  
 <span data-ttu-id="50427-113">在您确定了包含将用于预测的数据的表后，必须将外部数据中的列映射到挖掘模型中的列。</span><span class="sxs-lookup"><span data-stu-id="50427-113">After you have identified the tables that contain the data you will use for predictions, you must map the columns in the external data to the columns in the mining model.</span></span> <span data-ttu-id="50427-114">例如，如果您的模型基于人口统计信息和调查响应预测客户购买行为，则您的输入数据应包含与模型中的数据通常对应的信息。</span><span class="sxs-lookup"><span data-stu-id="50427-114">For example, if your model predicts customer purchasing behavior based on demographics and survey responses, your input data should contains information that generally corresponds to what is in the model.</span></span> <span data-ttu-id="50427-115">您无需对每个单列都具有匹配的数据，但可以匹配的列越多，预测效果就越好。</span><span class="sxs-lookup"><span data-stu-id="50427-115">You do not need to have matching data for every single column, but the more columns you can match, the better.</span></span> <span data-ttu-id="50427-116">如果您尝试映射具有不同数据类型的列，则系统可能会显示错误消息。</span><span class="sxs-lookup"><span data-stu-id="50427-116">If you try to map columns that have different data types, you might get an error.</span></span> <span data-ttu-id="50427-117">在此情况下，您可以在数据源视图中定义命名计算，以便将新的列数据强制转换或转换为模型所需的数据类型。</span><span class="sxs-lookup"><span data-stu-id="50427-117">In that case, you could define a named calculation in the data source view to cast or convert the new column data to the data type required by the model.</span></span> <span data-ttu-id="50427-118">有关详细信息，请参阅[在数据源视图中定义命名计算 &#40;Analysis Services&#41;](../multidimensional-models/define-named-calculations-in-a-data-source-view-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="50427-118">For more information, see [Define Named Calculations in a Data Source View &#40;Analysis Services&#41;](../multidimensional-models/define-named-calculations-in-a-data-source-view-analysis-services.md).</span></span>  
  
 <span data-ttu-id="50427-119">在您选择要用于预测的数据时，所选数据源中的某些列可能会基于名称相似性和匹配的数据类型，自动映射到挖掘模型列。</span><span class="sxs-lookup"><span data-stu-id="50427-119">When you choose the data to use for prediction, some columns in the selected data source might be automatically mapped to the mining model columns, based on name similarity and matching data type.</span></span> <span data-ttu-id="50427-120">可以使用 **“挖掘模型预测”** 中的 **“修改映射”** 对话框更改映射的列、删除不合适的映射或为现有列创建新映射。</span><span class="sxs-lookup"><span data-stu-id="50427-120">You can use the **Modify Mapping** dialog box in the **Mining Model Prediction** to change the columns that are mapped, delete inappropriate mappings, or create new mappings for existing columns.</span></span> <span data-ttu-id="50427-121">“挖掘模型预测”\*\*\*\* 设计图面还支持连接的拖放编辑。</span><span class="sxs-lookup"><span data-stu-id="50427-121">The **Mining Model Prediction** design surface also supports drag-and-drop editing of connections.</span></span>  
  
-   <span data-ttu-id="50427-122">若要创建新连接，只需在“挖掘模型”\*\*\*\* 表中选择一列，然后将该列拖到“选择输入表”\*\*\*\* 表中的对应列上。</span><span class="sxs-lookup"><span data-stu-id="50427-122">To create a new connection, just select a column in the **Mining Model** table and drag it to the corresponding column in the **SelectInput Table(s)** table.</span></span>  
  
-   <span data-ttu-id="50427-123">若要删除某个连接，请选中该连接线，然后按 Delete 键。</span><span class="sxs-lookup"><span data-stu-id="50427-123">To remove a connection, select the connection line and press the DELETE key.</span></span>  
  
 <span data-ttu-id="50427-124">下面的过程说明如何使用 **“指定嵌套联接”** 对话框修改在事例表和嵌套表之间创建的、用作预测查询输入的联接。</span><span class="sxs-lookup"><span data-stu-id="50427-124">The following procedure describes how you can modify the joins that have been created between the case table and a nested table used as inputs to a prediction query, using the **Specify Nested Join** dialog box.</span></span>  
  
### <a name="select-an-input-table"></a><span data-ttu-id="50427-125">选择输入表</span><span class="sxs-lookup"><span data-stu-id="50427-125">Select an input table</span></span>  
  
1.  <span data-ttu-id="50427-126">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 的数据挖掘设计器中，单击“挖掘准确性图表”\*\*\*\* 选项卡的“选择输入表”\*\*\*\* 表上的“选择事例表”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="50427-126">On the **Select Input Table(s)** table of the **Mining Accuracy Chart** tab in Data Mining Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], click **Select Case Table**.</span></span>  
  
     <span data-ttu-id="50427-127">此时将打开 **“选择表”** 对话框，在该对话框中，您可以选择包含查询所基于的数据的表。</span><span class="sxs-lookup"><span data-stu-id="50427-127">The **Select Table** dialog box opens, in which you can select the table that contains the data on which to base your queries.</span></span>  
  
2.  <span data-ttu-id="50427-128">在 **“选择表”** 对话框中，从 **“数据源”** 列表中选择数据源。</span><span class="sxs-lookup"><span data-stu-id="50427-128">In the **Select Table** dialog box, select a data source from the **Data Source** list.</span></span>  
  
3.  <span data-ttu-id="50427-129">在“表/视图名称”\*\*\*\* 下，选择包含希望用于测试模型的数据的表。</span><span class="sxs-lookup"><span data-stu-id="50427-129">Under **Table/View Name**, select the table that contains the data you want to use to test the models.</span></span>  
  
4.  <span data-ttu-id="50427-130">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="50427-130">Click **OK**.</span></span>  
  
     <span data-ttu-id="50427-131">挖掘结构中的列将自动映射到输入表中相同名称的列。</span><span class="sxs-lookup"><span data-stu-id="50427-131">The columns in the mining structure are automatically mapped to the columns that have the same name in the input table.</span></span>  
  
### <a name="change-the-way-that-input-data-is-mapped-to-the-model"></a><span data-ttu-id="50427-132">更改输入数据映射到模型的方式</span><span class="sxs-lookup"><span data-stu-id="50427-132">Change the way that input data is mapped to the model</span></span>  
  
1.  <span data-ttu-id="50427-133">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]的数据挖掘设计器中，选择 **“挖掘模型预测”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="50427-133">In Data Mining Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], select the **Mining Model Prediction** tab.</span></span>  
  
2.  <span data-ttu-id="50427-134">在 **“挖掘模型”** 菜单中，选择 **“修改连接”**。</span><span class="sxs-lookup"><span data-stu-id="50427-134">On the **Mining Model** menu, select **Modify Connections**.</span></span>  
  
     <span data-ttu-id="50427-135">此时，将打开 **“修改映射”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="50427-135">The **Modify Mapping** dialog box opens.</span></span> <span data-ttu-id="50427-136">在此对话框中， **“挖掘模型列”** 列中列出了所选挖掘结构中的列。</span><span class="sxs-lookup"><span data-stu-id="50427-136">In this dialog box, the column **Mining Model Column** lists the columns in the selected mining structure.</span></span> <span data-ttu-id="50427-137">“表列”\*\*\*\* 列中列出了在“选择输入表”\*\*\*\* 对话框中选择的外部数据源中的列。</span><span class="sxs-lookup"><span data-stu-id="50427-137">The column **Table Column** lists the columns in the external data source that you chose in the **SelectInput Table(s)** dialog box.</span></span> <span data-ttu-id="50427-138">外部数据源中的列将映射到挖掘模型中的列。</span><span class="sxs-lookup"><span data-stu-id="50427-138">The columns in the external data source are mapped to columns in the mining model.</span></span>  
  
3.  <span data-ttu-id="50427-139">在 **“表列”** 下，选择与要映射到的挖掘模型列相对应的行。</span><span class="sxs-lookup"><span data-stu-id="50427-139">Under **Table Column**, select the row that corresponds to the mining model column that you want to map to.</span></span>  
  
4.  <span data-ttu-id="50427-140">从外部数据源可用列的列表中选择一个新列。</span><span class="sxs-lookup"><span data-stu-id="50427-140">Select a new column from the list of available columns in the external data source.</span></span> <span data-ttu-id="50427-141">选择列表中的空白项以删除列映射。</span><span class="sxs-lookup"><span data-stu-id="50427-141">Select the blank item in the list to delete the column mapping.</span></span>  
  
5.  <span data-ttu-id="50427-142">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="50427-142">Click **OK**.</span></span>  
  
     <span data-ttu-id="50427-143">设计器中将显示新的列映射。</span><span class="sxs-lookup"><span data-stu-id="50427-143">The new column mappings are displayed in the designer.</span></span>  
  
### <a name="remove-a-relationship-between-input-tables"></a><span data-ttu-id="50427-144">删除各输入表之间的关系</span><span class="sxs-lookup"><span data-stu-id="50427-144">Remove a relationship between input tables</span></span>  
  
1.  <span data-ttu-id="50427-145">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 的数据挖掘设计器中“挖掘模型预测”\*\*\*\* 选项卡的“选择输入表”\*\*\*\* 表上，单击“修改联接”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="50427-145">On the **Select Input Table(s)** table of the **Mining Model Prediction** tab in Data Mining Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], click **Modify Join**.</span></span>  
  
     <span data-ttu-id="50427-146">此时，将打开 **“指定嵌套联接”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="50427-146">The **Specify Nested Join** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="50427-147">选择关系。</span><span class="sxs-lookup"><span data-stu-id="50427-147">Select a relationship.</span></span>  
  
3.  <span data-ttu-id="50427-148">单击 **“删除关系”**。</span><span class="sxs-lookup"><span data-stu-id="50427-148">Click **Remove Relationship**.</span></span>  
  
4.  <span data-ttu-id="50427-149">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="50427-149">Click **OK**.</span></span>  
  
     <span data-ttu-id="50427-150">这样便可删除事例表和嵌套表之间的关系。</span><span class="sxs-lookup"><span data-stu-id="50427-150">The relationship between the case table and the nested table has been removed.</span></span>  
  
### <a name="create-a-new-relationship-between-input-tables"></a><span data-ttu-id="50427-151">创建各输入表之间新的关系</span><span class="sxs-lookup"><span data-stu-id="50427-151">Create a new relationship between input tables</span></span>  
  
1.  <span data-ttu-id="50427-152">在数据挖掘设计器中“挖掘模型预测”\*\*\*\* 选项卡的“选择输入表”\*\*\*\* 表上，单击“修改联接”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="50427-152">On the **Select Input Table(s)** table of the **Mining Model Prediction** tab in Data Mining Designer, click **Modify Join**.</span></span>  
  
     <span data-ttu-id="50427-153">此时，将打开 **“指定嵌套联接”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="50427-153">The **Specify Nested Join** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="50427-154">单击 **“添加关系”**。</span><span class="sxs-lookup"><span data-stu-id="50427-154">Click **Add Relationship**.</span></span>  
  
     <span data-ttu-id="50427-155">将打开 **“创建关系”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="50427-155">The **Create Relationship** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="50427-156">在 **“源列”** 中选择嵌套表的键。</span><span class="sxs-lookup"><span data-stu-id="50427-156">Select the key of the nested table in **Source Columns**.</span></span>  
  
4.  <span data-ttu-id="50427-157">在 **“目标列”** 中选择事例表的键。</span><span class="sxs-lookup"><span data-stu-id="50427-157">Select the key of the case table in **Destination Columns**.</span></span>  
  
5.  <span data-ttu-id="50427-158">在 **“创建关系”** 对话框中，单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="50427-158">Click **OK** in the **Create Relationship** dialog box.</span></span>  
  
6.  <span data-ttu-id="50427-159">在 **“指定嵌套联接”** 对话框中，单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="50427-159">Click **OK** in the **Specify Nested Join** dialog box.</span></span>  
  
     <span data-ttu-id="50427-160">这样便在事例表和嵌套表之间创建了新的关系。</span><span class="sxs-lookup"><span data-stu-id="50427-160">A new relationship has been created between the case table and the nested table.</span></span>  
  
### <a name="add-a-nested-table-to-the-input-tables-of-a-prediction-query"></a><span data-ttu-id="50427-161">将嵌套表添加到预测查询的输入表</span><span class="sxs-lookup"><span data-stu-id="50427-161">Add a nested table to the input tables of a prediction query</span></span>  
  
1.  <span data-ttu-id="50427-162">在数据挖掘设计器的 **“挖掘模型预测”** 选项卡中，单击 **“选择事例表”** 打开 **“选择表”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="50427-162">On the **Mining Model Prediction** tab in Data Mining Designer, click **Select Case Table** to open the **Select Table** dialog box.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="50427-163">如果尚未指定事例表，则不能将嵌套表添加到输入中。</span><span class="sxs-lookup"><span data-stu-id="50427-163">You cannot add a nested table to the inputs unless you have specified a case table.</span></span> <span data-ttu-id="50427-164">使用嵌套表要求您正用于预测的挖掘模型也使用嵌套表。</span><span class="sxs-lookup"><span data-stu-id="50427-164">Use of a nested table requires that the mining model you are using for prediction also uses a nested table.</span></span>  
  
2.  <span data-ttu-id="50427-165">在 **“选择表”** 对话框中，从 **“数据源”** 列表中选择一个数据源，然后在数据源视图中选择包含事例数据的表。</span><span class="sxs-lookup"><span data-stu-id="50427-165">In the **Select Table** dialog box, select a data source from the **Data Source** list, and select the table in the data source view that contains the case data.</span></span> [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
3.  <span data-ttu-id="50427-166">单击 **“选择嵌套表”** 打开 **“选择表”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="50427-166">Click **Select Nested Table** to open the **Select Table** dialog box.</span></span>  
  
4.  <span data-ttu-id="50427-167">在 **“选择表”** 对话框中，从 **“数据源”** 列表中选择一个数据源，然后在数据源视图中选择包含嵌套数据的表。</span><span class="sxs-lookup"><span data-stu-id="50427-167">In the **Select Table** dialog box, select a data source from the **Data Source** list, and select the table in the data source view that contains the nested data.</span></span> [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     <span data-ttu-id="50427-168">如果已经存在关系，则挖掘模型中的列将自动映射到输入表中具有相同名称的列。</span><span class="sxs-lookup"><span data-stu-id="50427-168">If a relationship already exists, the columns in the mining model are automatically mapped to the columns that have the same name in the input table.</span></span> <span data-ttu-id="50427-169">通过单击 **“修改联接”** 以打开 **“创建关系”** 对话框，可以修改嵌套表与事例表之间的关系。</span><span class="sxs-lookup"><span data-stu-id="50427-169">You can modify the relationship between the nested table and the case table by clicking **Modify Join**, which opens the **Create Relationship** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50427-170">另请参阅</span><span class="sxs-lookup"><span data-stu-id="50427-170">See Also</span></span>  
 [<span data-ttu-id="50427-171">预测查询（数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="50427-171">Prediction Queries &#40;Data Mining&#41;</span></span>](prediction-queries-data-mining.md)  
  
  
