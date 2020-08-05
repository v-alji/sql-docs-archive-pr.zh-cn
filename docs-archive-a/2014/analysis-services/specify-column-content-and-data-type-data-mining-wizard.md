---
title: " (数据挖掘向导) 中指定列内容和数据类型 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 0634be64-4c38-4381-9b19-fe9a5889306c
author: minewiskan
ms.author: owend
ms.openlocfilehash: e22f46808877391376f721bcab55ea4fd9074186
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580913"
---
# <a name="specify-column-content-and-data-type-data-mining-wizard"></a><span data-ttu-id="97bee-102">指定列内容和数据类型（数据挖掘向导）</span><span class="sxs-lookup"><span data-stu-id="97bee-102">Specify Column Content and Data Type (Data Mining Wizard)</span></span>
  <span data-ttu-id="97bee-103">可以使用 **“指定列的内容和数据类型”** 页，为在向导的上一页中选择的每一列指定用法和数据类型。</span><span class="sxs-lookup"><span data-stu-id="97bee-103">Use the **Specify Column Content and Data Type** page to specify the usage and data type for each column that you selected on the previous page of the wizard.</span></span> <span data-ttu-id="97bee-104">如果希望忽略列，请单击 **“上一步”** 返回到 **“指定定型数据”** 页，并清除所有复选框。</span><span class="sxs-lookup"><span data-stu-id="97bee-104">If you want to ignore the column, click **Back** to return to the page **Specify the Training Data**, and clear all checkboxes.</span></span>  
  
 <span data-ttu-id="97bee-105">列的用法指示数据在模型中的使用方式。</span><span class="sxs-lookup"><span data-stu-id="97bee-105">The usage of a column indicates how the data will be used in the model.</span></span> <span data-ttu-id="97bee-106">列可以用作标识序列的键，用作分析中要使用的输入值，还可以用作要预测的值。</span><span class="sxs-lookup"><span data-stu-id="97bee-106">A column can be used as a key to identify a series, as an input value to use in analysis, or as the value that you want to predict.</span></span> <span data-ttu-id="97bee-107">列既可用于预测又可用于输入。</span><span class="sxs-lookup"><span data-stu-id="97bee-107">Columns can be used for both prediction and input.</span></span>  
  
 <span data-ttu-id="97bee-108">数据类型指定列中所包含数据的类型的更多详细信息，以及在定型过程中将如何使用数据。</span><span class="sxs-lookup"><span data-stu-id="97bee-108">The data type specifies additional detail about the type of data that is contained in the column, and how the data will be used during training.</span></span> <span data-ttu-id="97bee-109">某些内容类型需要某种特定的数据类型，反过来也是这样。</span><span class="sxs-lookup"><span data-stu-id="97bee-109">Some content types require a specific data type, and vice versa.</span></span> <span data-ttu-id="97bee-110">根据创建挖掘模型时所使用的算法，可能还需要指定特定数据类型。</span><span class="sxs-lookup"><span data-stu-id="97bee-110">You might also need to specify a particular data type depending on the algorithm that you use when you create a mining model.</span></span> <span data-ttu-id="97bee-111">有关挖掘模型和结构中的内容类型和数据类型的信息，请参阅[内容类型（数据挖掘）](data-mining/content-types-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="97bee-111">For information about content types and data types in mining models and structures, see [Content Types &#40;Data Mining&#41;](data-mining/content-types-data-mining.md).</span></span>  
  
 <span data-ttu-id="97bee-112">**有关详细信息：** [挖掘结构（Analysis Services - 数据挖掘）](data-mining/mining-structures-analysis-services-data-mining.md)、[挖掘模型列](data-mining/mining-model-columns.md)、[数据挖掘向导（Analysis Services - 数据挖掘）](data-mining/data-mining-wizard-analysis-services-data-mining.md)、[创建关系挖掘结构](data-mining/create-a-relational-mining-structure.md)</span><span class="sxs-lookup"><span data-stu-id="97bee-112">**For More Information:** [Mining Structures &#40;Analysis Services - Data Mining&#41;](data-mining/mining-structures-analysis-services-data-mining.md), [Mining Model Columns](data-mining/mining-model-columns.md), [Data Mining Wizard &#40;Analysis Services - Data Mining&#41;](data-mining/data-mining-wizard-analysis-services-data-mining.md), [Create a Relational Mining Structure](data-mining/create-a-relational-mining-structure.md)</span></span>  
  
## <a name="options"></a><span data-ttu-id="97bee-113">选项</span><span class="sxs-lookup"><span data-stu-id="97bee-113">Options</span></span>  
 <span data-ttu-id="97bee-114">**挖掘模型结构**</span><span class="sxs-lookup"><span data-stu-id="97bee-114">**Mining model structure**</span></span>  
 <span data-ttu-id="97bee-115">显示您在向导的上一页中所选视图和嵌套表中的列。</span><span class="sxs-lookup"><span data-stu-id="97bee-115">Displays the columns from the views and nested tables that you selected on the previous page of the wizard.</span></span>  
  
 <span data-ttu-id="97bee-116">**“列”**</span><span class="sxs-lookup"><span data-stu-id="97bee-116">**Columns**</span></span>  
 <span data-ttu-id="97bee-117">列出各列。</span><span class="sxs-lookup"><span data-stu-id="97bee-117">Lists the columns.</span></span>  
  
 <span data-ttu-id="97bee-118">**内容类型**</span><span class="sxs-lookup"><span data-stu-id="97bee-118">**Content type**</span></span>  
 <span data-ttu-id="97bee-119">指定列的内容类型。</span><span class="sxs-lookup"><span data-stu-id="97bee-119">Specify the content type for the column.</span></span> <span data-ttu-id="97bee-120">如果在向导的上一页上指定该列是键，则可用值如下：</span><span class="sxs-lookup"><span data-stu-id="97bee-120">If you specified that the column is a key on the previous page of the wizard, the following values are available:</span></span>  
  
|<span data-ttu-id="97bee-121">选项</span><span class="sxs-lookup"><span data-stu-id="97bee-121">Option</span></span>|<span data-ttu-id="97bee-122">说明</span><span class="sxs-lookup"><span data-stu-id="97bee-122">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="97bee-123">密钥</span><span class="sxs-lookup"><span data-stu-id="97bee-123">Key</span></span>|<span data-ttu-id="97bee-124">指定该列包含事例序列的唯一标识符。</span><span class="sxs-lookup"><span data-stu-id="97bee-124">Specify that the column contains a unique identifier for the case series.</span></span>|  
|<span data-ttu-id="97bee-125">键序列</span><span class="sxs-lookup"><span data-stu-id="97bee-125">Key Sequence</span></span>|<span data-ttu-id="97bee-126">指定该列包含序列标识符。</span><span class="sxs-lookup"><span data-stu-id="97bee-126">Specify that the column contains a sequence identifier.</span></span>|  
|<span data-ttu-id="97bee-127">键时间</span><span class="sxs-lookup"><span data-stu-id="97bee-127">Key Time</span></span>|<span data-ttu-id="97bee-128">指定该列包含用于标识日期或时序的日期或其他唯一连续数值。</span><span class="sxs-lookup"><span data-stu-id="97bee-128">Specify that the column contains a date or other unique continuous number that is used to identify a date or time series.</span></span>|  
  
 <span data-ttu-id="97bee-129">如果选择该列作为非键列，则可用值如下（具体取决于数据类型）：</span><span class="sxs-lookup"><span data-stu-id="97bee-129">If you selected the column as a non-key column, the following values are available, depending on the data type:</span></span>  
  
|<span data-ttu-id="97bee-130">选项</span><span class="sxs-lookup"><span data-stu-id="97bee-130">Option</span></span>|<span data-ttu-id="97bee-131">说明</span><span class="sxs-lookup"><span data-stu-id="97bee-131">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="97bee-132">连续</span><span class="sxs-lookup"><span data-stu-id="97bee-132">Continuous</span></span>|<span data-ttu-id="97bee-133">指定该列包含连续数值。</span><span class="sxs-lookup"><span data-stu-id="97bee-133">Specify that the column contains continuous numeric values.</span></span>|  
|<span data-ttu-id="97bee-134">离散化</span><span class="sxs-lookup"><span data-stu-id="97bee-134">Discretized</span></span>|<span data-ttu-id="97bee-135">指定该列包含已离散化数值或可被视为离散值的数值。</span><span class="sxs-lookup"><span data-stu-id="97bee-135">Specify that the column contains numeric values that either have been discretized, or can be treated as discrete values.</span></span>|  
|<span data-ttu-id="97bee-136">离散</span><span class="sxs-lookup"><span data-stu-id="97bee-136">Discrete</span></span>|<span data-ttu-id="97bee-137">指定该列包含文本或其他非数值。</span><span class="sxs-lookup"><span data-stu-id="97bee-137">Specify that the column contains text or other nonnumeric values.</span></span>|  
  
 <span data-ttu-id="97bee-138">**Data type**</span><span class="sxs-lookup"><span data-stu-id="97bee-138">**Data type**</span></span>  
 <span data-ttu-id="97bee-139">指定列的数据类型。</span><span class="sxs-lookup"><span data-stu-id="97bee-139">Specify the data type for the column.</span></span>  
  
 <span data-ttu-id="97bee-140">可用值如下：</span><span class="sxs-lookup"><span data-stu-id="97bee-140">The following values are available:</span></span>  
  
-   `Boolean`  
  
-   `Date`  
  
-   `Double`  
  
-   `Long`  
  
-   `Text`  
  
 <span data-ttu-id="97bee-141">**Detect**</span><span class="sxs-lookup"><span data-stu-id="97bee-141">**Detect**</span></span>  
 <span data-ttu-id="97bee-142">分析所有数值列中数据的示例。</span><span class="sxs-lookup"><span data-stu-id="97bee-142">Analyze a sample of data in all numeric columns.</span></span> <span data-ttu-id="97bee-143">利用建议的内容类型替换指定的 **“内容类型”** 值。</span><span class="sxs-lookup"><span data-stu-id="97bee-143">Replaces specified **Content Type** values with a recommended content type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97bee-144">另请参阅</span><span class="sxs-lookup"><span data-stu-id="97bee-144">See Also</span></span>  
 <span data-ttu-id="97bee-145">[数据挖掘向导 F1 帮助 &#40;Analysis Services 数据挖掘&#41;](data-mining-wizard-f1-help-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="97bee-145">[Data Mining Wizard F1 Help &#40;Analysis Services - Data Mining&#41;](data-mining-wizard-f1-help-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="97bee-146">[在数据挖掘向导 &#40;建议相关列&#41;](suggest-related-columns-data-mining-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="97bee-146">[Suggest Related Columns &#40;Data Mining Wizard&#41;](suggest-related-columns-data-mining-wizard.md) </span></span>  
 <span data-ttu-id="97bee-147">[在数据挖掘向导 &#40;指定表类型&#41;](specify-table-types-data-mining-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="97bee-147">[Specify Table Types &#40;Data Mining Wizard&#41;](specify-table-types-data-mining-wizard.md) </span></span>  
 [<span data-ttu-id="97bee-148">指定数据挖掘向导 &#40;列的内容和数据类型&#41;</span><span class="sxs-lookup"><span data-stu-id="97bee-148">Specify the Column's Content and Data Type &#40;Data Mining Wizard&#41;</span></span>](specify-the-column-s-content-and-data-type-data-mining-wizard.md)  
  
  
