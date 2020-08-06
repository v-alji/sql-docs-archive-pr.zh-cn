---
title: 创建交叉验证报表 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- validating data mining models
- mining structures [Analysis Services], how-to topics
- cross-validation [data mining]
- statistical standard deviation
ms.assetid: 7b1fec4c-7053-41eb-b030-5179257967a4
author: minewiskan
ms.author: owend
ms.openlocfilehash: ccbafe63b0026cd45a15ea71fd84e223c1b32a9c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682449"
---
# <a name="create-a-cross-validation-report"></a><span data-ttu-id="bd916-102">创建交叉验证报表</span><span class="sxs-lookup"><span data-stu-id="bd916-102">Create a Cross-Validation Report</span></span>
  <span data-ttu-id="bd916-103">本主题演练如何在数据挖掘设计器中使用“准确性图表”选项卡创建交叉验证报表。</span><span class="sxs-lookup"><span data-stu-id="bd916-103">This topic walks you through creation of a cross-validation report using the Accuracy Chart tab in Data Mining Designer.</span></span> <span data-ttu-id="bd916-104">有关交叉验证报表外观的常规信息，以及该报表包含的统计度量值，请参阅[交叉验证（Analysis Services - 数据挖掘）](cross-validation-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="bd916-104">For general information about what a cross-validation report looks like, and the statistical measures it includes, see [Cross-Validation &#40;Analysis Services - Data Mining&#41;](cross-validation-analysis-services-data-mining.md).</span></span>  
  
 <span data-ttu-id="bd916-105">交叉验证报表在本质上不同于提升图或分类矩阵之类的准确性图表。</span><span class="sxs-lookup"><span data-stu-id="bd916-105">A cross-validation report is fundamentally different from an accuracy chart, such as a lift chart or classification matrix.</span></span>  
  
-   <span data-ttu-id="bd916-106">交叉验证评估在模型或结构中使用的数据的总体分布情况；因此，您不指定测试数据集。</span><span class="sxs-lookup"><span data-stu-id="bd916-106">Cross-validation assesses the overall distribution of data that is used in a model or structure; therefore, you do not specify a testing data set.</span></span> <span data-ttu-id="bd916-107">交叉验证始终仅使用用于对模型或挖掘结构进行定型的原始数据。</span><span class="sxs-lookup"><span data-stu-id="bd916-107">Cross-validation always uses only the original data that was used to train the model or the mining structure.</span></span>  
  
-   <span data-ttu-id="bd916-108">只能针对单个可预测结果执行交叉验证。</span><span class="sxs-lookup"><span data-stu-id="bd916-108">Cross-validation can only be performed with respect to a single predictable outcome.</span></span> <span data-ttu-id="bd916-109">如果结构支持具有不同可预测属性的模型，则您必须为每个可预测输出都创建单独的报表。</span><span class="sxs-lookup"><span data-stu-id="bd916-109">If the structure supports models that have different predictable attributes, you must create separate reports for each predictable output.</span></span>  
  
-   <span data-ttu-id="bd916-110">只有与当前所选结构相关的模型才可用于交叉验证。</span><span class="sxs-lookup"><span data-stu-id="bd916-110">Only models that are related to the currently selected structure are available for cross-validation.</span></span>  
  
-   <span data-ttu-id="bd916-111">如果当前选择的结构支持聚类分析模型和非聚类分析模型的组合，则在你单击“获取结果”\*\*\*\* 时，交叉验证存储过程将自动加载具有相同预测列的模型，并且忽略不共享相同可预测属性的聚类分析模型。</span><span class="sxs-lookup"><span data-stu-id="bd916-111">If the structure that is currently selected supports a combination of clustering and non-clustering models, when you click **Get Results**, the cross-validation stored procedure will automatically load models that have the same predicted column, and ignore clustering models that do not share the same predictable attribute.</span></span>  
  
-   <span data-ttu-id="bd916-112">只有在挖掘模型不支持任何其他可预测属性的情况下，您才可以对不具有可预测属性的聚类分析模型创建交叉验证报表。</span><span class="sxs-lookup"><span data-stu-id="bd916-112">You can create a cross-validation report on a clustering model that does not have a predictable attribute only if the mining structure does not support any other predictable attributes.</span></span>  
  
### <a name="select-a-mining-structure"></a><span data-ttu-id="bd916-113">选择挖掘结构</span><span class="sxs-lookup"><span data-stu-id="bd916-113">Select a mining structure</span></span>  
  
1.  <span data-ttu-id="bd916-114">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中打开数据挖掘设计器。</span><span class="sxs-lookup"><span data-stu-id="bd916-114">Open the Data Mining Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="bd916-115">在解决方案资源管理器中，打开包含要为其创建报表的结构或模型的数据库。</span><span class="sxs-lookup"><span data-stu-id="bd916-115">In Solution Explorer, open the database that contains the structure or model for which you want to create a report.</span></span>  
  
3.  <span data-ttu-id="bd916-116">在数据挖掘设计器中，双击挖掘结构以打开结构及其相关模型。</span><span class="sxs-lookup"><span data-stu-id="bd916-116">Double-click the mining structure to open the structure and its related models in Data Mining Designer.</span></span>  
  
4.  <span data-ttu-id="bd916-117">单击 **“挖掘准确性图表”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="bd916-117">Click the **Mining Accuracy Chart** tab.</span></span>  
  
5.  <span data-ttu-id="bd916-118">单击 **“交叉验证”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="bd916-118">Click the **Cross Validation** tab.</span></span>  
  
### <a name="set-cross-validation-options"></a><span data-ttu-id="bd916-119">设置交叉验证选项</span><span class="sxs-lookup"><span data-stu-id="bd916-119">Set cross-validation options</span></span>  
  
1.  <span data-ttu-id="bd916-120">在 **“交叉验证”** 选项卡中，对于 **“折叠计数”**，单击向下箭头，选择一个 1 到 10 之间的数字。</span><span class="sxs-lookup"><span data-stu-id="bd916-120">On the **Cross Validation** tab, for **Fold Count**, click the down arrow to select a number between 1 and 10.</span></span> <span data-ttu-id="bd916-121">默认值为 10。</span><span class="sxs-lookup"><span data-stu-id="bd916-121">The default value is 10.</span></span>  
  
     <span data-ttu-id="bd916-122">**“折叠计数”** 表示将在原始数据集中创建的分区数。</span><span class="sxs-lookup"><span data-stu-id="bd916-122">The **Fold Count** represents the number of partitions that will be created within the original data set.</span></span> <span data-ttu-id="bd916-123">如果将“折叠计数”设置为 1，则将在不分区的情况下使用定型集。</span><span class="sxs-lookup"><span data-stu-id="bd916-123">If you set Fold Count to 1, the training set will be used without partitioning.</span></span>  
  
2.  <span data-ttu-id="bd916-124">对于 **“目标属性”**，单击向下箭头，从列表中选择一个列。</span><span class="sxs-lookup"><span data-stu-id="bd916-124">For **Target Attribute**, click the down arrow, and select a column from the list.</span></span> <span data-ttu-id="bd916-125">如果模型是聚类分析模型，则选择 **#Cluster** ，以指示该模型不具有可预测属性。</span><span class="sxs-lookup"><span data-stu-id="bd916-125">If the model is a clustering model, select **#Cluster** to indicate that the model does not have a predictable attribute.</span></span> <span data-ttu-id="bd916-126">请注意，只有在挖掘结构不支持其他类型的可预测属性的情况下，值 **#Cluster**才可用。</span><span class="sxs-lookup"><span data-stu-id="bd916-126">Note that the value, **#Cluster**, is available only when the mining structure does not support other types of predictable attributes.</span></span>  
  
     <span data-ttu-id="bd916-127">只能为每个报表选择一个可预测属性。</span><span class="sxs-lookup"><span data-stu-id="bd916-127">You can select only one predictable attribute per report.</span></span> <span data-ttu-id="bd916-128">默认情况下，所有具有同一可预测属性的相关模型都包括在一个报表中。</span><span class="sxs-lookup"><span data-stu-id="bd916-128">By default, all related models that have the same predictable attribute are included in the report.</span></span>  
  
3.  <span data-ttu-id="bd916-129">对于 **“最大事例数”**，键入一个足够大的数字，以便在将数据拆分到指定的折叠数中时提供数据的典型事例。</span><span class="sxs-lookup"><span data-stu-id="bd916-129">For **Max Cases**, type a number that is large enough to provide a representative sample of data when the data is split among the specified number of folds.</span></span> <span data-ttu-id="bd916-130">如果数字大于模型定型集中的事例计数，将使用所有的事例。</span><span class="sxs-lookup"><span data-stu-id="bd916-130">If the number is greater than the count of cases in the model training set, all cases will be used.</span></span>  
  
     <span data-ttu-id="bd916-131">如果定型数据集很大，则对 **“最大事例数”** 的值进行设置将会限制已处理事例的总数，从而加快报表完成的速度。</span><span class="sxs-lookup"><span data-stu-id="bd916-131">If the training data set is very large, setting the value for **Max Cases** limits the total number of cases processed, and lets the report finish faster.</span></span> <span data-ttu-id="bd916-132">但是，不应将“最大事例数”\*\*\*\* 设置得过低，否则将没有足够的数据可用于交叉验证。</span><span class="sxs-lookup"><span data-stu-id="bd916-132">However, you should not set **Max Cases** too low or there may be insufficient data for cross-validation.</span></span>  
  
4.  <span data-ttu-id="bd916-133">或者，对于 **“目标状态”**，键入希望建模的可预测属性的值。</span><span class="sxs-lookup"><span data-stu-id="bd916-133">Optionally, for **Target State**, type the value of the predictable attribute that you want to model.</span></span> <span data-ttu-id="bd916-134">例如，如果 [Bike Buyer] 列有两个可能的值：1 (Yes) 和 2 (No)，则可以输入值 1 来仅为预期结果评估模型的准确性。</span><span class="sxs-lookup"><span data-stu-id="bd916-134">For example, if the column [Bike Buyer] has two possible values, 1 (Yes) and 2 (No), you can enter the value 1 to assess the accuracy of the model for just the desired outcome.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="bd916-135"> 如果未输入值， **“目标阈值”** 选项将不可用，并且将会针对可预测属性的所有可能的值对该模型进行评估。</span><span class="sxs-lookup"><span data-stu-id="bd916-135">If you do not enter a value, the **Target Threshold** option is not available, and the model is assessed for all possible values of the predictable attribute.</span></span>  
  
5.  <span data-ttu-id="bd916-136">或者，对于 **“目标阈值”**，键入一个 0 到 1 之间的十进制数字，来指定预测一定会计为准确的最小概率。</span><span class="sxs-lookup"><span data-stu-id="bd916-136">Optionally, for **Target Threshold**, type a decimal number between 0 and 1 to specify the minimum probability that a prediction must have to be counted as accurate.</span></span>  
  
     <span data-ttu-id="bd916-137">有关如何设置概率阈值的更多技巧，请参阅 [交叉验证报表中的度量值](measures-in-the-cross-validation-report.md)。</span><span class="sxs-lookup"><span data-stu-id="bd916-137">For additional tips about how to set probability thresholds, see [Measures in the Cross-Validation Report](measures-in-the-cross-validation-report.md).</span></span>  
  
6.  <span data-ttu-id="bd916-138">单击 **“获取结果”**。</span><span class="sxs-lookup"><span data-stu-id="bd916-138">Click **Get Results**.</span></span>  
  
### <a name="print-the-cross-validation-report"></a><span data-ttu-id="bd916-139">打印交叉验证报表</span><span class="sxs-lookup"><span data-stu-id="bd916-139">Print the cross-validation report</span></span>  
  
1.  <span data-ttu-id="bd916-140">在“交叉验证”\*\*\*\* 选项卡中，右键单击已完成的报表。</span><span class="sxs-lookup"><span data-stu-id="bd916-140">Right-click the completed report on the **Cross Validation** tab.</span></span>  
  
2.  <span data-ttu-id="bd916-141">在快捷菜单中，选择 **“打印”** 或 **“打印预览”** 来预先查看该报表。</span><span class="sxs-lookup"><span data-stu-id="bd916-141">In the shortcut menu, select **Print** or **Print Preview** to review the report first.</span></span>  
  
### <a name="create-a-copy-of-the-report-in-microsoft-excel"></a><span data-ttu-id="bd916-142">在 Microsoft Excel 中创建报表的副本</span><span class="sxs-lookup"><span data-stu-id="bd916-142">Create a copy of the report in Microsoft Excel</span></span>  
  
1.  <span data-ttu-id="bd916-143">在“交叉验证”\*\*\*\* 选项卡中，右键单击已完成的报表。</span><span class="sxs-lookup"><span data-stu-id="bd916-143">Right-click the completed report on the **Cross Validation** tab.</span></span>  
  
2.  <span data-ttu-id="bd916-144">在快捷菜单中，选择 **“全选”**。</span><span class="sxs-lookup"><span data-stu-id="bd916-144">In the shortcut menu, select **Select All**.</span></span>  
  
3.  <span data-ttu-id="bd916-145">右键单击所选文本，然后选择“复制”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="bd916-145">Right-click the selected text, and select **Copy**.</span></span>  
  
4.  <span data-ttu-id="bd916-146">将所选内容粘贴到一个打开的 Excel 工作簿中。</span><span class="sxs-lookup"><span data-stu-id="bd916-146">Paste the selection into an open Excel workbook.</span></span> <span data-ttu-id="bd916-147">如果使用的是 **“粘贴”** 选项，该报表将作为 HTML 粘贴到 Excel 中，其中保留了行和列的格式。</span><span class="sxs-lookup"><span data-stu-id="bd916-147">If you use the **Paste** option, the report is pasted into Excel as HTML, which preserves row and column formatting.</span></span> <span data-ttu-id="bd916-148">如果使用的是用于文本或 Unicode 文本的“选择性粘贴”\*\*\*\* 选项粘贴报表，将以行分隔的格式粘贴报表。</span><span class="sxs-lookup"><span data-stu-id="bd916-148">If you paste the report by using the **Paste Special** options for text or Unicode text, the report is pasted in row-delimited format.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd916-149">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bd916-149">See Also</span></span>  
 [<span data-ttu-id="bd916-150">交叉验证报表中的度量值</span><span class="sxs-lookup"><span data-stu-id="bd916-150">Measures in the Cross-Validation Report</span></span>](measures-in-the-cross-validation-report.md)  
  
  
