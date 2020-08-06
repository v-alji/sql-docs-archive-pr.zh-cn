---
title: 模糊分组转换编辑器 (列 "选项卡) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.fuzzygroupingtransformation.columns.f1
helpviewer_keywords:
- Fuzzy Grouping Transformation Editor
ms.assetid: 24f4539f-2a9f-4acd-acc7-06228a07f7df
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9d3aef9c30a81760b7f09378a8ecd66fee0dac62
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688031"
---
# <a name="fuzzy-grouping-transformation-editor-columns-tab"></a><span data-ttu-id="91cff-102">模糊分组转换编辑器（“列”选项卡）</span><span class="sxs-lookup"><span data-stu-id="91cff-102">Fuzzy Grouping Transformation Editor (Columns Tab)</span></span>
  <span data-ttu-id="91cff-103">可以使用 **“模糊分组转换编辑器”** 对话框的 **“列”** 选项卡，指定用于对带有重复值的行进行分组的列。</span><span class="sxs-lookup"><span data-stu-id="91cff-103">Use the **Columns** tab of the **Fuzzy Grouping Transformation Editor** dialog box to specify the columns used to group rows with duplicate values.</span></span>  
  
 <span data-ttu-id="91cff-104">若要了解有关模糊分组转换的详细信息，请参阅 [Fuzzy Grouping Transformation](data-flow/transformations/fuzzy-grouping-transformation.md)。</span><span class="sxs-lookup"><span data-stu-id="91cff-104">To learn more about the Fuzzy Grouping transformation, see [Fuzzy Grouping Transformation](data-flow/transformations/fuzzy-grouping-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="91cff-105">选项</span><span class="sxs-lookup"><span data-stu-id="91cff-105">Options</span></span>  
 <span data-ttu-id="91cff-106">**可用输入列**</span><span class="sxs-lookup"><span data-stu-id="91cff-106">**Available Input Columns**</span></span>  
 <span data-ttu-id="91cff-107">从此列表中选择用于对带有重复值的行进行分组的输入列。</span><span class="sxs-lookup"><span data-stu-id="91cff-107">Select from this list the input columns used to group rows with duplicate values.</span></span>  
  
 <span data-ttu-id="91cff-108">**名称**</span><span class="sxs-lookup"><span data-stu-id="91cff-108">**Name**</span></span>  
 <span data-ttu-id="91cff-109">查看可用输入列的名称。</span><span class="sxs-lookup"><span data-stu-id="91cff-109">View the names of available input columns.</span></span>  
  
 <span data-ttu-id="91cff-110">**传递**</span><span class="sxs-lookup"><span data-stu-id="91cff-110">**Pass Through**</span></span>  
 <span data-ttu-id="91cff-111">选择是否在转换的输出中包含输入列。</span><span class="sxs-lookup"><span data-stu-id="91cff-111">Select whether to include the input column in the output of the transformation.</span></span> <span data-ttu-id="91cff-112">用于分组的所有列将自动复制到输出中。</span><span class="sxs-lookup"><span data-stu-id="91cff-112">All columns used for grouping are automatically copied to the output.</span></span> <span data-ttu-id="91cff-113">通过选中此列可以包含其他列。</span><span class="sxs-lookup"><span data-stu-id="91cff-113">You can include additional columns by checking this column.</span></span>  
  
 <span data-ttu-id="91cff-114">**输入列**</span><span class="sxs-lookup"><span data-stu-id="91cff-114">**Input Column**</span></span>  
 <span data-ttu-id="91cff-115">选择先前在“可用输入列”\*\*\*\* 列表中选中的一个输入列。</span><span class="sxs-lookup"><span data-stu-id="91cff-115">Select one of the input columns selected earlier in the **Available Input Columns** list.</span></span>  
  
 <span data-ttu-id="91cff-116">**输出别名**</span><span class="sxs-lookup"><span data-stu-id="91cff-116">**Output Alias**</span></span>  
 <span data-ttu-id="91cff-117">为相应的输出列输入一个描述性名称。</span><span class="sxs-lookup"><span data-stu-id="91cff-117">Enter a descriptive name for the corresponding output column.</span></span> <span data-ttu-id="91cff-118">默认情况下，输出列名称与输入列名称相同。</span><span class="sxs-lookup"><span data-stu-id="91cff-118">By default, the output column name is the same as the input column name.</span></span>  
  
 <span data-ttu-id="91cff-119">**组输出别名**</span><span class="sxs-lookup"><span data-stu-id="91cff-119">**Group Output Alias**</span></span>  
 <span data-ttu-id="91cff-120">为包含分组重复项的规范值的列输入一个描述性名称。</span><span class="sxs-lookup"><span data-stu-id="91cff-120">Enter a descriptive name for the column that will contain the canonical value for the grouped duplicates.</span></span> <span data-ttu-id="91cff-121">此输出列的默认名称是在输入列名称后面追加 _clean。</span><span class="sxs-lookup"><span data-stu-id="91cff-121">The default name of this output column is the input column name with _clean appended.</span></span>  
  
 <span data-ttu-id="91cff-122">**匹配类型**</span><span class="sxs-lookup"><span data-stu-id="91cff-122">**Match Type**</span></span>  
 <span data-ttu-id="91cff-123">选择模糊匹配或完全匹配。</span><span class="sxs-lookup"><span data-stu-id="91cff-123">Select fuzzy or exact matching.</span></span> <span data-ttu-id="91cff-124">在指定了模糊匹配类型的所有列中，如果某些行足够相似，则会将这些行视为重复。</span><span class="sxs-lookup"><span data-stu-id="91cff-124">Rows are considered duplicates if they are sufficiently similar across all columns with a fuzzy match type.</span></span> <span data-ttu-id="91cff-125">如果还对某些列指定了完全匹配，则只会将在完全匹配列中包含相同值的行视为可能重复。</span><span class="sxs-lookup"><span data-stu-id="91cff-125">If you also specify exact matching on certain columns, only rows that contain identical values in the exact matching columns are considered as possible duplicates.</span></span> <span data-ttu-id="91cff-126">因此，如果知道特定列中没有错误或不存在不一致的情况，则可以对该列指定完全匹配以提高其他列模糊匹配的准确性。</span><span class="sxs-lookup"><span data-stu-id="91cff-126">Therefore, if you know that a certain column contains no errors or inconsistencies, you can specify exact matching on that column to increase the accuracy of the fuzzy matching on other columns.</span></span>  
  
 <span data-ttu-id="91cff-127">**最低相似性**</span><span class="sxs-lookup"><span data-stu-id="91cff-127">**Minimum Similarity**</span></span>  
 <span data-ttu-id="91cff-128">使用滑块在联接级别设置相似性阈值。</span><span class="sxs-lookup"><span data-stu-id="91cff-128">Set the similarity threshold at the join level by using the slider.</span></span> <span data-ttu-id="91cff-129">该值越接近 1，查找值与源值的相似性必须越接近，才能视为匹配。</span><span class="sxs-lookup"><span data-stu-id="91cff-129">The closer the value is to 1, the closer the resemblance of the lookup value to the source value must be to qualify as a match.</span></span> <span data-ttu-id="91cff-130">由于需要考虑的候选记录更少，因此增加阈值可以提高匹配的速度。</span><span class="sxs-lookup"><span data-stu-id="91cff-130">Increasing the threshold can improve the speed of matching since fewer candidate records need to be considered.</span></span>  
  
 <span data-ttu-id="91cff-131">**相似性输出别名**</span><span class="sxs-lookup"><span data-stu-id="91cff-131">**Similarity Output Alias**</span></span>  
 <span data-ttu-id="91cff-132">为包含所选联接相似性得分的新输出列指定名称。</span><span class="sxs-lookup"><span data-stu-id="91cff-132">Specify the name for a new output column that contains the similarity scores for the selected join.</span></span> <span data-ttu-id="91cff-133">如果将该值保留为空，将不会创建输出列。</span><span class="sxs-lookup"><span data-stu-id="91cff-133">If you leave this value empty, the output column is not created.</span></span>  
  
 <span data-ttu-id="91cff-134">**数字**</span><span class="sxs-lookup"><span data-stu-id="91cff-134">**Numerals**</span></span>  
 <span data-ttu-id="91cff-135">指定比较列数据时前导数字和尾随数字的重要性。</span><span class="sxs-lookup"><span data-stu-id="91cff-135">Specify the significance of leading and trailing numerals in comparing the column data.</span></span> <span data-ttu-id="91cff-136">例如，如果前导数字重要，则“123 Main Street”将不会与“456 Main Street”分组在一起。</span><span class="sxs-lookup"><span data-stu-id="91cff-136">For example, if leading numerals are significant, "123 Main Street" will not be grouped with "456 Main Street."</span></span>  
  
|<span data-ttu-id="91cff-137">值</span><span class="sxs-lookup"><span data-stu-id="91cff-137">Value</span></span>|<span data-ttu-id="91cff-138">说明</span><span class="sxs-lookup"><span data-stu-id="91cff-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="91cff-139">**两者均未选中**</span><span class="sxs-lookup"><span data-stu-id="91cff-139">**Neither**</span></span>|<span data-ttu-id="91cff-140">前导数字和尾随数字都不重要。</span><span class="sxs-lookup"><span data-stu-id="91cff-140">Leading and trailing numerals are not significant.</span></span>|  
|<span data-ttu-id="91cff-141">**Leading**</span><span class="sxs-lookup"><span data-stu-id="91cff-141">**Leading**</span></span>|<span data-ttu-id="91cff-142">只有前导数字重要。</span><span class="sxs-lookup"><span data-stu-id="91cff-142">Only leading numerals are significant.</span></span>|  
|<span data-ttu-id="91cff-143">**加**</span><span class="sxs-lookup"><span data-stu-id="91cff-143">**Trailing**</span></span>|<span data-ttu-id="91cff-144">只有尾随数字重要。</span><span class="sxs-lookup"><span data-stu-id="91cff-144">Only trailing numerals are significant.</span></span>|  
|<span data-ttu-id="91cff-145">**LeadingAndTrailing**</span><span class="sxs-lookup"><span data-stu-id="91cff-145">**LeadingAndTrailing**</span></span>|<span data-ttu-id="91cff-146">前导数字和尾随数字都重要。</span><span class="sxs-lookup"><span data-stu-id="91cff-146">Both leading and trailing numerals are significant.</span></span>|  
  
 <span data-ttu-id="91cff-147">**比较标志**</span><span class="sxs-lookup"><span data-stu-id="91cff-147">**Comparison Flags**</span></span>  
 <span data-ttu-id="91cff-148">有关字符串比较选项的信息，请参阅 [比较字符串数据](data-flow/comparing-string-data.md)。</span><span class="sxs-lookup"><span data-stu-id="91cff-148">For information about the string comparison options, see [Comparing String Data](data-flow/comparing-string-data.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91cff-149">另请参阅</span><span class="sxs-lookup"><span data-stu-id="91cff-149">See Also</span></span>  
 <span data-ttu-id="91cff-150">[Integration Services 错误和消息引用](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="91cff-150">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 [<span data-ttu-id="91cff-151">使用模糊分组转换标识相似数据行</span><span class="sxs-lookup"><span data-stu-id="91cff-151">Identify Similar Data Rows by Using the Fuzzy Grouping Transformation</span></span>](data-flow/transformations/identify-similar-data-rows-by-using-the-fuzzy-grouping-transformation.md)  
  
  
