---
title: 模糊分组转换编辑器 (高级选项卡) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.fuzzygroupingtransformation.advanced.f1
helpviewer_keywords:
- Fuzzy Grouping Transformation Editor
ms.assetid: dd820d75-b8a7-4515-aea4-3553ba5b442e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2f5dd05eda56b4818914f659734eb3cdfb20c4d0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579634"
---
# <a name="fuzzy-grouping-transformation-editor-advanced-tab"></a><span data-ttu-id="4190a-102">模糊分组转换编辑器（“高级”选项卡）</span><span class="sxs-lookup"><span data-stu-id="4190a-102">Fuzzy Grouping Transformation Editor (Advanced Tab)</span></span>
  <span data-ttu-id="4190a-103">可以使用 **“模糊分组转换编辑器”** 对话框的 **“高级”** 选项卡，指定输入和输出列，设置相似性阈值以及定义分隔符。</span><span class="sxs-lookup"><span data-stu-id="4190a-103">Use the **Advanced** tab of the **Fuzzy Grouping Transformation Editor** dialog box to specify input and output columns, set similarity thresholds, and define delimiters.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4190a-104">`Exhaustive` `MaxMemoryUsage` 模糊分组转换的和属性在 "**模糊分组转换编辑器**" 中不可用，但可以使用 "**高级编辑器**" 进行设置。</span><span class="sxs-lookup"><span data-stu-id="4190a-104">The `Exhaustive` and the `MaxMemoryUsage` properties of the Fuzzy Grouping transformation are not available in the **Fuzzy Grouping Transformation Editor**, but can be set by using the **Advanced Editor**.</span></span> <span data-ttu-id="4190a-105">有关这些属性的详细信息，请参阅 [Transformation Custom Properties](data-flow/transformations/transformation-custom-properties.md)的“模糊分组转换”部分。</span><span class="sxs-lookup"><span data-stu-id="4190a-105">For more information on these properties, see the Fuzzy Grouping Transformation section of [Transformation Custom Properties](data-flow/transformations/transformation-custom-properties.md).</span></span>  
  
 <span data-ttu-id="4190a-106">若要了解有关模糊分组转换的详细信息，请参阅 [Fuzzy Grouping Transformation](data-flow/transformations/fuzzy-grouping-transformation.md)。</span><span class="sxs-lookup"><span data-stu-id="4190a-106">To learn more about the Fuzzy Grouping transformation, see [Fuzzy Grouping Transformation](data-flow/transformations/fuzzy-grouping-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="4190a-107">选项</span><span class="sxs-lookup"><span data-stu-id="4190a-107">Options</span></span>  
 <span data-ttu-id="4190a-108">**输入键列名**</span><span class="sxs-lookup"><span data-stu-id="4190a-108">**Input key column name**</span></span>  
 <span data-ttu-id="4190a-109">指定包含每个输入行的唯一表示符的输出列名称。</span><span class="sxs-lookup"><span data-stu-id="4190a-109">Specify the name of an output column that contains the unique identifier for each input row.</span></span> <span data-ttu-id="4190a-110">`_key_in` 列包含的值可唯一标识每个行。</span><span class="sxs-lookup"><span data-stu-id="4190a-110">The `_key_in` column has a value that uniquely identifies each row.</span></span>  
  
 <span data-ttu-id="4190a-111">**输出键列名**</span><span class="sxs-lookup"><span data-stu-id="4190a-111">**Output key column name**</span></span>  
 <span data-ttu-id="4190a-112">对于一组重复的行，指定包含其规范行的唯一标识符的输出列名称。</span><span class="sxs-lookup"><span data-stu-id="4190a-112">Specify the name of an output column that contains the unique identifier for the canonical row of a group of duplicate rows.</span></span> <span data-ttu-id="4190a-113">`_key_out` 列对应于规范数据行的 `_key_in` 值。</span><span class="sxs-lookup"><span data-stu-id="4190a-113">The `_key_out` column corresponds to the `_key_in` value of the canonical data row.</span></span>  
  
 <span data-ttu-id="4190a-114">**相似性计分列名**</span><span class="sxs-lookup"><span data-stu-id="4190a-114">**Similarity score column name**</span></span>  
 <span data-ttu-id="4190a-115">指定包含相似性得分的列的名称。</span><span class="sxs-lookup"><span data-stu-id="4190a-115">Specify a name for the column that contains the similarity score.</span></span> <span data-ttu-id="4190a-116">相似性得分是介于 0 和 1 之间的值，用于指示输入行与规范行的相似性。</span><span class="sxs-lookup"><span data-stu-id="4190a-116">The similarity score is a value between 0 and 1 that indicates the similarity of the input row to the canonical row.</span></span> <span data-ttu-id="4190a-117">得分越接近 1，行与规范行的匹配程度越高。</span><span class="sxs-lookup"><span data-stu-id="4190a-117">The closer the score is to 1, the more closely the row matches the canonical row.</span></span>  
  
 <span data-ttu-id="4190a-118">**相似性阈值**</span><span class="sxs-lookup"><span data-stu-id="4190a-118">**Similarity threshold**</span></span>  
 <span data-ttu-id="4190a-119">使用滑块设置相似性阈值。</span><span class="sxs-lookup"><span data-stu-id="4190a-119">Set the similarity threshold by using the slider.</span></span> <span data-ttu-id="4190a-120">阈值越接近于 1，则行必须越近似，才能被认定为重复。</span><span class="sxs-lookup"><span data-stu-id="4190a-120">The closer the threshold is to 1, the more the rows must resemble each other to qualify as duplicates.</span></span> <span data-ttu-id="4190a-121">增大阈值可以提高匹配的速度，因为需要考虑的候选记录更少。</span><span class="sxs-lookup"><span data-stu-id="4190a-121">Increasing the threshold can improve the speed of matching because fewer candidate records have to be considered.</span></span>  
  
 <span data-ttu-id="4190a-122">**标记分隔符**</span><span class="sxs-lookup"><span data-stu-id="4190a-122">**Token delimiters**</span></span>  
 <span data-ttu-id="4190a-123">转换提供了一组默认的分隔符用于对数据进行词汇切分，但是您可以根据需要通过编辑列表来添加或删除分隔符。</span><span class="sxs-lookup"><span data-stu-id="4190a-123">The transformation provides a default set of delimiters for tokenizing data, but you can add or remove delimiters as needed by editing the list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4190a-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4190a-124">See Also</span></span>  
 <span data-ttu-id="4190a-125">[Integration Services 错误和消息引用](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="4190a-125">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 [<span data-ttu-id="4190a-126">使用模糊分组转换标识相似数据行</span><span class="sxs-lookup"><span data-stu-id="4190a-126">Identify Similar Data Rows by Using the Fuzzy Grouping Transformation</span></span>](data-flow/transformations/identify-similar-data-rows-by-using-the-fuzzy-grouping-transformation.md)  
  
  
