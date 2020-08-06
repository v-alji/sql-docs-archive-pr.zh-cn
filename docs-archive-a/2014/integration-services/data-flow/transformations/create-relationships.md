---
title: 创建关系 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.createrelationships.f1
ms.assetid: 6ebd305f-ffd2-4a1d-b24c-e28c151b94f5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5a1095e193587ae7d416311031e5297a035ca37e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579654"
---
# <a name="create-relationships"></a><span data-ttu-id="47e75-102">创建关系</span><span class="sxs-lookup"><span data-stu-id="47e75-102">Create Relationships</span></span>
  <span data-ttu-id="47e75-103">可以使用 **“创建关系”** 对话框，编辑源列与在模糊查找转换编辑器、查找转换编辑器或字词查找转换编辑器中配置的查找表列之间的映射。</span><span class="sxs-lookup"><span data-stu-id="47e75-103">Use the **Create Relationships** dialog box to edit mappings between the source columns and the lookup table columns that you configured in the Fuzzy Lookup Transformation Editor, the Lookup Transformation Editor, and the Term Lookup Transformation Editor.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="47e75-104">通过字词查找转换编辑器调用“创建关系”  对话框时，只显示“输入列”  和“查找列”  列表。</span><span class="sxs-lookup"><span data-stu-id="47e75-104">The **Create Relationships** dialog box displays only the **Input Column** and **Lookup Column** lists when invoked from the Term Lookup Transformation Editor.</span></span>  
  
 <span data-ttu-id="47e75-105">若要了解有关使用 **“创建关系”** 对话框的转换的详细信息，请参阅 [Fuzzy Lookup Transformation](lookup-transformation.md)、 [Lookup Transformation](lookup-transformation.md)和 [Term Lookup Transformation](term-lookup-transformation.md)。</span><span class="sxs-lookup"><span data-stu-id="47e75-105">To learn more about the transformations that use the **Create Relationships** dialog box, see [Fuzzy Lookup Transformation](lookup-transformation.md), [Lookup Transformation](lookup-transformation.md), and [Term Lookup Transformation](term-lookup-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="47e75-106">选项</span><span class="sxs-lookup"><span data-stu-id="47e75-106">Options</span></span>  
 <span data-ttu-id="47e75-107">**输入列**</span><span class="sxs-lookup"><span data-stu-id="47e75-107">**Input Column**</span></span>  
 <span data-ttu-id="47e75-108">从可用输入列的列表中进行选择。</span><span class="sxs-lookup"><span data-stu-id="47e75-108">Select from the list of available input columns.</span></span>  
  
 <span data-ttu-id="47e75-109">**查找列**</span><span class="sxs-lookup"><span data-stu-id="47e75-109">**Lookup Column**</span></span>  
 <span data-ttu-id="47e75-110">从可用查找列的列表中进行选择。</span><span class="sxs-lookup"><span data-stu-id="47e75-110">Select from the list of available lookup columns.</span></span>  
  
 <span data-ttu-id="47e75-111">**映射类型**</span><span class="sxs-lookup"><span data-stu-id="47e75-111">**Mapping Type**</span></span>  
 <span data-ttu-id="47e75-112">选择模糊匹配或完全匹配。</span><span class="sxs-lookup"><span data-stu-id="47e75-112">Select fuzzy or exact matching.</span></span>  
  
 <span data-ttu-id="47e75-113">在使用模糊匹配时，如果行中所有具有模糊匹配类型的列都非常相似，则将视为重复的行。</span><span class="sxs-lookup"><span data-stu-id="47e75-113">When you use fuzzy matching, rows are considered duplicates if they are sufficiently similar across all columns that have a fuzzy match type.</span></span> <span data-ttu-id="47e75-114">若要从模糊匹配中获取更为准确的结果，可以指定一些列使用完全匹配来代替模糊匹配。</span><span class="sxs-lookup"><span data-stu-id="47e75-114">To obtain better results from fuzzy matching, you can specify that some columns should use exact matching instead of fuzzy matching.</span></span> <span data-ttu-id="47e75-115">例如，如果知道特定列中没有错误或不存在不一致的情况，则可以对该列指定完全匹配，以便只有在此列中包含相同值的行才会视为可能重复。</span><span class="sxs-lookup"><span data-stu-id="47e75-115">For example, if you know that a certain column contains no errors or inconsistencies, you can specify exact matching on that column, so that only rows which contain identical values in this column are considered as possible duplicates.</span></span> <span data-ttu-id="47e75-116">这样可以提高其他列模糊匹配的准确性。</span><span class="sxs-lookup"><span data-stu-id="47e75-116">This increases the accuracy of fuzzy matching on other columns.</span></span>  
  
 <span data-ttu-id="47e75-117">**比较标志**</span><span class="sxs-lookup"><span data-stu-id="47e75-117">**Comparison Flags**</span></span>  
 <span data-ttu-id="47e75-118">有关字符串比较选项的信息，请参阅 [比较字符串数据](../comparing-string-data.md)。</span><span class="sxs-lookup"><span data-stu-id="47e75-118">For information about the string comparison options, see [Comparing String Data](../comparing-string-data.md).</span></span>  
  
 <span data-ttu-id="47e75-119">**最低相似性**</span><span class="sxs-lookup"><span data-stu-id="47e75-119">**Minimum Similarity**</span></span>  
 <span data-ttu-id="47e75-120">使用滑块在列级别设置相似性阈值。</span><span class="sxs-lookup"><span data-stu-id="47e75-120">Set the similarity threshold at the column level by using the slider.</span></span> <span data-ttu-id="47e75-121">该值越接近 1，查找值与源值必须越相似，才能视为匹配。</span><span class="sxs-lookup"><span data-stu-id="47e75-121">The closer the value is to 1, the more the lookup value must resemble the source value to qualify as a match.</span></span> <span data-ttu-id="47e75-122">增大阈值可以提高匹配的速度，因为需要考虑的候选记录更少。</span><span class="sxs-lookup"><span data-stu-id="47e75-122">Increasing the threshold can improve the speed of matching because fewer candidate records have to be considered.</span></span>  
  
 <span data-ttu-id="47e75-123">**相似性输出别名**</span><span class="sxs-lookup"><span data-stu-id="47e75-123">**Similarity Output Alias**</span></span>  
 <span data-ttu-id="47e75-124">为包含所选列相似性得分的新输出列指定名称。</span><span class="sxs-lookup"><span data-stu-id="47e75-124">Specify the name for a new output column that contains the similarity scores for the selected column.</span></span> <span data-ttu-id="47e75-125">如果将该值保留为空，将不会创建输出列。</span><span class="sxs-lookup"><span data-stu-id="47e75-125">If you leave this value empty, the output column is not created.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47e75-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="47e75-126">See Also</span></span>  
 <span data-ttu-id="47e75-127">[Integration Services 错误和消息引用](../../integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="47e75-127">[Integration Services Error and Message Reference](../../integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="47e75-128">[模糊查找转换编辑器（“列”选项卡）](../../fuzzy-lookup-transformation-editor-columns-tab.md) </span><span class="sxs-lookup"><span data-stu-id="47e75-128">[Fuzzy Lookup Transformation Editor &#40;Columns Tab&#41;](../../fuzzy-lookup-transformation-editor-columns-tab.md) </span></span>  
 <span data-ttu-id="47e75-129">[查找转换编辑器（“列”页）](../../lookup-transformation-editor-columns-page.md) </span><span class="sxs-lookup"><span data-stu-id="47e75-129">[Lookup Transformation Editor &#40;Columns Page&#41;](../../lookup-transformation-editor-columns-page.md) </span></span>  
 [<span data-ttu-id="47e75-130">字词查找转换编辑器（“字词查找”选项卡）</span><span class="sxs-lookup"><span data-stu-id="47e75-130">Term Lookup Transformation Editor &#40;Term Lookup Tab&#41;</span></span>](../../term-lookup-transformation-editor-term-lookup-tab.md)  
  
  
