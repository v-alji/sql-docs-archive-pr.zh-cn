---
title: 创建新的 OLAP 挖掘结构 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining structures [Analysis Services], OLAP
- mining structures [Analysis Services], creating
- OLAP [Analysis Services], mining models
ms.assetid: 368f4273-a016-4748-bcb6-505a3e745af3
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2851fe6180254b129471c442297c419fd594e123
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682443"
---
# <a name="create-a-new-olap-mining-structure"></a><span data-ttu-id="df278-102">创建新的 OLAP 挖掘结构</span><span class="sxs-lookup"><span data-stu-id="df278-102">Create a New OLAP Mining Structure</span></span>
  <span data-ttu-id="df278-103">您可以使用中的数据挖掘向导 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 来创建使用多维模型中的数据的挖掘结构。</span><span class="sxs-lookup"><span data-stu-id="df278-103">You can use the Data Mining Wizard in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] to create a mining structure that uses data from a multidimensional model.</span></span> <span data-ttu-id="df278-104">基于 OLAP 多维数据集的挖掘模型可以使用事实表、维度和度量值组中的列和值作为分析属性。</span><span class="sxs-lookup"><span data-stu-id="df278-104">Mining models that are based on OLAP cubes can use the column and values in fact tables, dimensions, and measure groups as attributes for analysis.</span></span>  
  
### <a name="to-create-a-new-olap-mining-structure"></a><span data-ttu-id="df278-105">创建新的 OLAP 挖掘结构</span><span class="sxs-lookup"><span data-stu-id="df278-105">To create a new OLAP mining structure</span></span>  
  
1.  <span data-ttu-id="df278-106">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 中的解决方案资源管理器中，右键单击 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 项目中的“挖掘结构”\*\*\*\* 文件夹，然后单击“新建挖掘结构”\*\*\*\* 打开数据挖掘向导。</span><span class="sxs-lookup"><span data-stu-id="df278-106">In Solution Explorer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], right-click the **Mining Structures** folder in an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project, and then click **New Mining Structure** to open the Data Mining Wizard.</span></span>  
  
2.  <span data-ttu-id="df278-107">在 **“欢迎使用数据挖掘向导”** 页上，单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="df278-107">On the **Welcome to the Data Mining Wizard** page, click **Next**.</span></span>  
  
3.  <span data-ttu-id="df278-108">在 **“选择定义方法”** 页上，选择 **“从现有多维数据集”**，然后单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="df278-108">On the **Select the Definition Method** page, select **From existing cube**, and then click **Next**.</span></span>  
  
     <span data-ttu-id="df278-109">如果收到错误以及错误消息“无法检索支持的数据挖掘算法的列表”，则打开“项目属性”对话框，确认你指定了支持多维模型的 Analysis Services 实例的名称。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="df278-109">If you get an error with the message, Unable to retrieve a list of supported data mining algorithms, open the **Project Properties** dialog box and verify that you have specified the name of an Analysis Services instance that supports multidimensional models.</span></span> <span data-ttu-id="df278-110">不能在支持表格建模的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 实例上创建挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="df278-110">You cannot create mining models on an instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] that supports tabular modeling.</span></span>  
  
4.  <span data-ttu-id="df278-111">在 **“创建数据挖掘结构”** 页上，确定是仅创建一个挖掘结构还是创建一个挖掘结构和一个相关挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="df278-111">On the **Create the Data Mining Structure** page, decide whether you will create a mining structure only, or a mining structure plus one related mining model.</span></span> <span data-ttu-id="df278-112">通常，可以很容易地同时创建挖掘模型，这样，系统将会提示您包括必需的列。</span><span class="sxs-lookup"><span data-stu-id="df278-112">Generally it is easier to create a mining model at the same time, so that you can be prompted to include necessary columns.</span></span>  
  
     <span data-ttu-id="df278-113">如果将创建一个挖掘模型，请选择要使用的数据挖掘算法，再单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="df278-113">If you will create a mining model, select the data mining algorithm that you want to use, and then click **Next**.</span></span> <span data-ttu-id="df278-114">有关如何选择一种算法的详细信息，请参阅[数据挖掘算法（Analysis Services - 数据挖掘）](data-mining-algorithms-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="df278-114">For more information about how to choose an algorithm, see [Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining-algorithms-analysis-services-data-mining.md).</span></span>  
  
5.  <span data-ttu-id="df278-115">在 **“选择源多维数据集维度”** 页上的 **“选择源多维数据集维度”** 下，找到包含您的主要事例数据的维度。</span><span class="sxs-lookup"><span data-stu-id="df278-115">On the **Select the Source Cube Dimension** page, under **Select a Source Cube Dimension**, locate the dimension that contains the majority of your case data.</span></span>  
  
     <span data-ttu-id="df278-116">例如，如果你正在尝试标识客户分组，则可以选择“客户”维度；如果你正在尝试分析交易中的购买行为，则可以选择“Internet 销售订单详细信息”维度。</span><span class="sxs-lookup"><span data-stu-id="df278-116">For example, if you are trying to identify customer groupings, you might choose the Customer dimension; if you are trying to analyze purchases across transactions, you might choose the Internet Sales Order Details dimension.</span></span> <span data-ttu-id="df278-117">您不会被局限为仅使用此维度中的数据，但该维度应该包含要在分析中使用的重要属性。</span><span class="sxs-lookup"><span data-stu-id="df278-117">You are not restricted to using only the data in this dimension, but it should contain important attributes to use in analysis.</span></span>  
  
     <span data-ttu-id="df278-118">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="df278-118">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="df278-119">在 **“选择事例键”** 页的 **“属性”** 下，选择将成为挖掘结构键的属性，然后单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="df278-119">On the **Select the Case Key** page, under **Attributes**, select the attribute that will be the key of the mining structure, and then click **Next**.</span></span>  
  
     <span data-ttu-id="df278-120">通常，您用作挖掘架结构的键的属性也是用于维度的键并且将预先选择。</span><span class="sxs-lookup"><span data-stu-id="df278-120">Typically the attribute that you use as key for the mining structure is also a key for the dimension and will be pre-selected.</span></span>  
  
7.  <span data-ttu-id="df278-121">在 **“选择事例级别列”** 页的 **“相关属性和度量值”** 下，选择包含您要作为事例数据添加到挖掘架构的值的属性和度量值。</span><span class="sxs-lookup"><span data-stu-id="df278-121">On the **Select Case Level Columns** page, under **Related Attributes and Measures**, select the attributes and measures that contain values you want to add to the mining structure as case data.</span></span> <span data-ttu-id="df278-122">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="df278-122">Click **Next**.</span></span>  
  
8.  <span data-ttu-id="df278-123">在 **“指定挖掘模型列用法”** 页的 **“挖掘模型结构”** 下，首先选择可预测列，然后选择要用作输入的列。</span><span class="sxs-lookup"><span data-stu-id="df278-123">On the **Specify Mining Model Column Usage** page, under **Mining model structure**, first set the predictable column, and then choose columns to use as inputs.</span></span>  
  
    -   <span data-ttu-id="df278-124">选中最左侧列中的复选框可包括挖掘模型中的数据。</span><span class="sxs-lookup"><span data-stu-id="df278-124">Select the checkbox in the leftmost column to include the data in the mining structure.</span></span> <span data-ttu-id="df278-125">您可以在将用于引用的结构中包括列，但不使用这些列进行分析。</span><span class="sxs-lookup"><span data-stu-id="df278-125">You can include columns in the structure that you will use for reference, but not use them for analysis.</span></span>  
  
    -   <span data-ttu-id="df278-126">选中 **“输入”** 列中的复选框可以将属性用作分析中的变量。</span><span class="sxs-lookup"><span data-stu-id="df278-126">Select the checkbox in the **Input** column to use the attribute as a variable in analysis.</span></span>  
  
    -   <span data-ttu-id="df278-127">仅对于可预测属性，选中 **“预测”** 列中的复选框。</span><span class="sxs-lookup"><span data-stu-id="df278-127">Select the checkbox in the **Predict** column only for predictable attributes.</span></span>  
  
     <span data-ttu-id="df278-128">请注意，已指定为键的列不能用于输入或预测。</span><span class="sxs-lookup"><span data-stu-id="df278-128">Note that columns you have designated as keys cannot be used for input or prediction.</span></span>  
  
     <span data-ttu-id="df278-129">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="df278-129">Click **Next**.</span></span>  
  
9. <span data-ttu-id="df278-130">在 **“指定挖掘模型列用法”** 页上，您还可以使用 **“添加嵌套表”** 和 **“删除嵌套表”**，添加和删除挖掘模型中的嵌套表。</span><span class="sxs-lookup"><span data-stu-id="df278-130">On the **Specify Mining Model Column Usage** page, you can also add and remove nested tables to the mining structure, using **Add Nested Tables** and **Nested Tables**.</span></span>  
  
     <span data-ttu-id="df278-131">在 OLAP 挖掘模型中，嵌套表是多维数据集中与表示事例属性的维度具有一对多关系的另一组数据。</span><span class="sxs-lookup"><span data-stu-id="df278-131">In an OLAP mining model, a nested table is another set of data within the cube that has a one-to-many relationship with the dimension that represents the case attributes.</span></span> <span data-ttu-id="df278-132">因此，在对话框打开时，它将预先选择已经与您作为事例表选择的维度相关的维度组。</span><span class="sxs-lookup"><span data-stu-id="df278-132">Therefore, when the dialog box opens, it pre-selects measure groups that are already related to the dimension you selected as the case table.</span></span> <span data-ttu-id="df278-133">此时，您可以选择包含可用于分析的附加信息的其他维度。</span><span class="sxs-lookup"><span data-stu-id="df278-133">At this point, you would choose a different dimension that contains additional information useful for analysis.</span></span>  
  
     <span data-ttu-id="df278-134">例如，如果你正在分析客户，则可以使用 [Customer] 维度作为事例表。</span><span class="sxs-lookup"><span data-stu-id="df278-134">For example, if you are analyzing customers, you would use the [Customer] dimension as the case table.</span></span> <span data-ttu-id="df278-135">对于嵌套表，可以添加客户在进行购买时陈述的原因，该原因包含在 [Sales Reason] 维度中。</span><span class="sxs-lookup"><span data-stu-id="df278-135">For the nested table, you might add the reason customers cited when making a purchase, which is included in the [Sales Reason] dimension.</span></span>  
  
     <span data-ttu-id="df278-136">如果您添加嵌套数据，则必须还要指定两个列：</span><span class="sxs-lookup"><span data-stu-id="df278-136">If you add nested data, you must specify two additional columns:</span></span>  
  
    -   <span data-ttu-id="df278-137">嵌套表的键：这应该在“选择嵌套表键”页上预先选择。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="df278-137">The key of the nested table: This should be pre-selected on the page, **Select Nested Table Key**.</span></span>  
  
    -   <span data-ttu-id="df278-138">要用于分析的属性： **“选择嵌套表列”** 页提供嵌套表选择中度量值和属性的列表。</span><span class="sxs-lookup"><span data-stu-id="df278-138">The attributes or attributes to use for analysis: The page, **Select Nested Table Columns**, provides a list of measures and attributes in the nested table selection.</span></span>  
  
        -   <span data-ttu-id="df278-139">对于要包含在模型中的每个属性，请选中左侧列中的复选框。</span><span class="sxs-lookup"><span data-stu-id="df278-139">For each attribute that you include in the model, check the box in the left column.</span></span>  
  
        -   <span data-ttu-id="df278-140">如果您要将该属性仅用于分析，请选中 **“输入”**。</span><span class="sxs-lookup"><span data-stu-id="df278-140">If you want to use the attribute for analysis only, check **Input**.</span></span>  
  
        -   <span data-ttu-id="df278-141">如果您想要将列作为模型的可预测属性之一包括，则选中 **“预测”**。</span><span class="sxs-lookup"><span data-stu-id="df278-141">If you want to include the column as one of the predictable attributes for the model, select **Predict**.</span></span>  
  
        -   <span data-ttu-id="df278-142">您包括在该结构中、但未指定为输入属性或可预测属性的任何项都将添加到该结构中并且具有标志 `Ignore`；这意味着在生成模型时处理数据，但数据未用于分析，并且仅可用于钻取。</span><span class="sxs-lookup"><span data-stu-id="df278-142">Any item that you include in the structure but do not specify as an input or predictable attribute is added to the structure with the flag `Ignore`; this means that the data is processed when you build the model but is not used in analysis, and is available only for drillthrough.</span></span> <span data-ttu-id="df278-143">如果你想要包括客户名称等详细信息，但不想在分析中使用这些信息，这会很方便。</span><span class="sxs-lookup"><span data-stu-id="df278-143">This can be handy if you want to include details such as customer names but don't want to use them in analysis.</span></span>  
  
     <span data-ttu-id="df278-144">单击 **“完成”** 关闭用于嵌套表的向导部分。</span><span class="sxs-lookup"><span data-stu-id="df278-144">Click **Finish** to close the part of the wizard that works with nested tables.</span></span> <span data-ttu-id="df278-145">您可以重复此过程，添加多个嵌套列。</span><span class="sxs-lookup"><span data-stu-id="df278-145">You can repeat the process to add multiple nested columns.</span></span>  
  
10. <span data-ttu-id="df278-146">在 **“指定列的内容和数据类型”** 页的 **“挖掘模型结构”** 下，设置每列的内容类型和数据类型。</span><span class="sxs-lookup"><span data-stu-id="df278-146">On the **Specify Columns' Content and Data Type** page, under **Mining model structure**, set the content type and data type for each column.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="df278-147"> OLAP 挖掘模型不支持使用 **“检测”** 功能自动检测列包含连续数据还是离散数据。</span><span class="sxs-lookup"><span data-stu-id="df278-147">OLAP mining models do not support using the **Detect** feature to automatically detect whether a column contains continuous or discrete data.</span></span>  
  
     <span data-ttu-id="df278-148">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="df278-148">Click **Next**.</span></span>  
  
11. <span data-ttu-id="df278-149">在 **“对源多维数据集进行切片”** 页上，您可以筛选用于创建挖掘结构的数据。</span><span class="sxs-lookup"><span data-stu-id="df278-149">On the **Slice Source Cube** page, you can filter the data that is used to create the mining structure.</span></span>  
  
     <span data-ttu-id="df278-150">通过对多维数据集进行切片操作，您可以限制用于生成模型的数据。</span><span class="sxs-lookup"><span data-stu-id="df278-150">Slicing the cube lets you restrict the data that is used to build the model.</span></span> <span data-ttu-id="df278-151">例如，您可以通过对“地域”层次结构执行切片操作，为每个区域生成单独的模型。</span><span class="sxs-lookup"><span data-stu-id="df278-151">For example, you could build separate models for each region by slicing on the Geography hierarchy and</span></span>  
  
    -   <span data-ttu-id="df278-152">**维度**：从下拉列表中选择一个相关维度。</span><span class="sxs-lookup"><span data-stu-id="df278-152">**Dimension**: Choose a related dimension from the dropdown list.</span></span>  
  
    -   <span data-ttu-id="df278-153">**层次结构**：选择要应用筛选器的维度层次结构的级别。</span><span class="sxs-lookup"><span data-stu-id="df278-153">**Hierarchy**:  Select the level of the dimension hierarchy at which you want to apply the filter.</span></span> <span data-ttu-id="df278-154">例如，如果按 [Geography] 维度进行切片，则可以选择某一层次结构级别，例如 [Region Country Name]。</span><span class="sxs-lookup"><span data-stu-id="df278-154">For example, if you are slicing by the [Geography] dimension, you would choose a hierarchy level such as [Region Country Name] .</span></span>  
  
    -   <span data-ttu-id="df278-155">**运算符**：从列表中选择运算符。</span><span class="sxs-lookup"><span data-stu-id="df278-155">**Operator**: Choose an operator from the list.</span></span>  
  
    -   <span data-ttu-id="df278-156">**筛选表达式**：键入要用作筛选条件的值或表达式，或者使用下拉列表从层次结构的指定级别上的成员列表中选择某一值。</span><span class="sxs-lookup"><span data-stu-id="df278-156">**Filter Expression**: Type a value or expression to serve as the filter condition, or use the dropdown list to select a value from the list of members at the specified level of the hierarchy.</span></span>  
  
         <span data-ttu-id="df278-157">例如，如果你选择了 [Geography] 作为维度，并且选择了 [区域国家名] 作为层次结构级别，则下拉列表将包含可用作筛选条件的所有有效国家/地区。</span><span class="sxs-lookup"><span data-stu-id="df278-157">For example, if you selected [Geography] as the dimension and [Region Country Name] as the hierarchy level, the dropdown list contains all the valid countries/regions that you can use as a filter condition.</span></span> <span data-ttu-id="df278-158">您可以进行多选。</span><span class="sxs-lookup"><span data-stu-id="df278-158">You can make multiple selections.</span></span> <span data-ttu-id="df278-159">因此，挖掘结构中的数据将被限制为来自这些地域的多维数据集数据。</span><span class="sxs-lookup"><span data-stu-id="df278-159">As a result, the data in the mining structure will be limited to cube data from these geographical areas.</span></span>  
  
    -   <span data-ttu-id="df278-160">**参数**：忽略此复选框。</span><span class="sxs-lookup"><span data-stu-id="df278-160">**Parameters**: Ignore this check box.</span></span> <span data-ttu-id="df278-161">此对话框支持多个多维数据集筛选方案，并且此选项不针对生成挖掘结构。</span><span class="sxs-lookup"><span data-stu-id="df278-161">This dialog box supports multiple cube filtering scenarios and this option is not relevant to building a mining structure.</span></span>  
  
     <span data-ttu-id="df278-162">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="df278-162">Click **Next**.</span></span>  
  
12. <span data-ttu-id="df278-163">在 **“将数据拆分为定型集和测试集”** 页上，指定为测试保留的挖掘结构数据的百分比，或者指定最大测试事例数。</span><span class="sxs-lookup"><span data-stu-id="df278-163">On the **Split data into training and testing sets** page, specify a percentage of the mining structure data to reserve for testing, or specify the maximum number of test cases.</span></span> <span data-ttu-id="df278-164">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="df278-164">Click **Next**.</span></span>  
  
     <span data-ttu-id="df278-165">如果指定两个值，则使用这两个限制值中的最小值。</span><span class="sxs-lookup"><span data-stu-id="df278-165">If you specify both values, the limits are combined to use whichever is lowest.</span></span>  
  
13. <span data-ttu-id="df278-166">在 **“完成向导”** 页上，提供新的 OLAP 挖掘结构的名称以及初始挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="df278-166">On the **Completing the Wizard** page, provide a name for the new OLAP mining structure and the initial mining model.</span></span>  
  
14. <span data-ttu-id="df278-167">单击“完成”。</span><span class="sxs-lookup"><span data-stu-id="df278-167">Click **Finish**.</span></span>  
  
15. <span data-ttu-id="df278-168">在“完成向导”页上，还具有创建挖掘模型维度的选项和/或使用挖掘模型维度的多维数据集。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="df278-168">On the **Completing the Wizard** page, you also have the option to create a mining model dimension and/or a cube using the mining model dimension.</span></span> <span data-ttu-id="df278-169">只有使用下列算法生成的模型才支持这些选项：</span><span class="sxs-lookup"><span data-stu-id="df278-169">These options are supported only for models built using the following algorithms:</span></span>  
  
    -   <span data-ttu-id="df278-170">Microsoft 聚类分析算法</span><span class="sxs-lookup"><span data-stu-id="df278-170">Microsoft Clustering algorithm</span></span>  
  
    -   <span data-ttu-id="df278-171">Microsoft 决策树算法</span><span class="sxs-lookup"><span data-stu-id="df278-171">Microsoft Decision Trees algorithm</span></span>  
  
    -   <span data-ttu-id="df278-172">Microsoft 关联规则算法</span><span class="sxs-lookup"><span data-stu-id="df278-172">Microsoft Association Rules algorithm</span></span>  
  
     <span data-ttu-id="df278-173">**创建挖掘模型维度**：选中此复选框并且为挖掘模型维度提供类型名称。</span><span class="sxs-lookup"><span data-stu-id="df278-173">**Create mining model dimension**: Select this check box and provide a type name for the mining model dimension.</span></span> <span data-ttu-id="df278-174">在您使用此选项时，将在用于生成挖掘结构的原始多维数据集内创建一个新维度。</span><span class="sxs-lookup"><span data-stu-id="df278-174">When you use this option, a new dimension is created within the original cube that was used to build the mining structure.</span></span> <span data-ttu-id="df278-175">您可以使用此维度进行下钻和执行进一步的分析。</span><span class="sxs-lookup"><span data-stu-id="df278-175">You can use this dimension to drill down and conduct further analysis.</span></span> <span data-ttu-id="df278-176">因为该维度位于多维数据集内，所以，该维度将自动映射到事例数据维度。</span><span class="sxs-lookup"><span data-stu-id="df278-176">Because the dimension is located within the cube, the dimension is automatically mapped to the case data dimension.</span></span>  
  
     <span data-ttu-id="df278-177">**使用挖掘模型维度创建多维数据集**：选中此复选框，并且为新的多维数据集提供名称。</span><span class="sxs-lookup"><span data-stu-id="df278-177">**Create cube using mining model dimension**: Select this check box, and provide a name for the new cube.</span></span> <span data-ttu-id="df278-178">在您使用此选项时，将创建一个新的多维数据集，该多维数据集包含在生成结构中使用的现有维度和包含模型结果的新数据挖掘维度。</span><span class="sxs-lookup"><span data-stu-id="df278-178">When you use this option, a new cube is created that contains both the existing dimensions that were used in building the structure, and the new data mining dimension that contains the results from the model.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df278-179">另请参阅</span><span class="sxs-lookup"><span data-stu-id="df278-179">See Also</span></span>  
 [<span data-ttu-id="df278-180">挖掘结构任务和操作指南</span><span class="sxs-lookup"><span data-stu-id="df278-180">Mining Structure Tasks and How-tos</span></span>](mining-structure-tasks-and-how-tos.md)  
