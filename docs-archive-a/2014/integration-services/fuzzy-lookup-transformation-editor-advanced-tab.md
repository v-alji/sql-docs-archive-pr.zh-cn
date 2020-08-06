---
title: 模糊查找转换编辑器 (高级选项卡) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.fuzzylookuptransformation.advanced.f1
helpviewer_keywords:
- Fuzzy Lookup Transformation Editor
ms.assetid: 0a2919be-2ea7-4c06-82b8-0ffad5f0dd83
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 68f53eb2735dc07656fc8ff2b81c3259caa4847b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688032"
---
# <a name="fuzzy-lookup-transformation-editor-advanced-tab"></a><span data-ttu-id="57b33-102">模糊查找转换编辑器（“高级”选项卡）</span><span class="sxs-lookup"><span data-stu-id="57b33-102">Fuzzy Lookup Transformation Editor (Advanced Tab)</span></span>
  <span data-ttu-id="57b33-103">可以使用 **“模糊查找转换编辑器”** 对话框的 **“高级”** 选项卡设置模糊查找的参数。</span><span class="sxs-lookup"><span data-stu-id="57b33-103">Use the **Advanced** tab of the **Fuzzy Lookup Transformation Editor** dialog box to set parameters for the fuzzy lookup.</span></span>  
  
 <span data-ttu-id="57b33-104">若要了解有关模糊查找转换的详细信息，请参阅 [Fuzzy Lookup Transformation](data-flow/transformations/lookup-transformation.md)。</span><span class="sxs-lookup"><span data-stu-id="57b33-104">To learn more about the Fuzzy Lookup transformation, see [Fuzzy Lookup Transformation](data-flow/transformations/lookup-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="57b33-105">选项</span><span class="sxs-lookup"><span data-stu-id="57b33-105">Options</span></span>  
 <span data-ttu-id="57b33-106">**每次查找输出的最大匹配数**</span><span class="sxs-lookup"><span data-stu-id="57b33-106">**Maximum number of matches to output per lookup**</span></span>  
 <span data-ttu-id="57b33-107">指定为每个输入行返回的最大匹配转换数。</span><span class="sxs-lookup"><span data-stu-id="57b33-107">Specify the maximum number of matches the transformation can return for each input row.</span></span> <span data-ttu-id="57b33-108">默认值为 **1**。</span><span class="sxs-lookup"><span data-stu-id="57b33-108">The default is **1**.</span></span>  
  
 <span data-ttu-id="57b33-109">**相似性阈值**</span><span class="sxs-lookup"><span data-stu-id="57b33-109">**Similarity threshold**</span></span>  
 <span data-ttu-id="57b33-110">使用滑块在组件级别设置相似性阈值。</span><span class="sxs-lookup"><span data-stu-id="57b33-110">Set the similarity threshold at the component level by using the slider.</span></span> <span data-ttu-id="57b33-111">该值越接近 1，查找值与源值的相似性必须越接近，才能视为匹配。</span><span class="sxs-lookup"><span data-stu-id="57b33-111">The closer the value is to 1, the closer the resemblance of the lookup value to the source value must be to qualify as a match.</span></span> <span data-ttu-id="57b33-112">由于需要考虑的候选记录更少，因此增加阈值可以提高匹配的速度。</span><span class="sxs-lookup"><span data-stu-id="57b33-112">Increasing the threshold can improve the speed of matching since fewer candidate records need to be considered.</span></span>  
  
 <span data-ttu-id="57b33-113">**标记分隔符**</span><span class="sxs-lookup"><span data-stu-id="57b33-113">**Token delimiters**</span></span>  
 <span data-ttu-id="57b33-114">指定转换用来对列值进行词汇切分的分隔符。</span><span class="sxs-lookup"><span data-stu-id="57b33-114">Specify the delimiters that the transformation uses to tokenize column values.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57b33-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="57b33-115">See Also</span></span>  
 <span data-ttu-id="57b33-116">[Integration Services 错误和消息引用](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="57b33-116">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="57b33-117">[模糊查找转换编辑器 &#40;引用表 "选项卡&#41;](../../2014/integration-services/fuzzy-lookup-transformation-editor-reference-table-tab.md) </span><span class="sxs-lookup"><span data-stu-id="57b33-117">[Fuzzy Lookup Transformation Editor &#40;Reference Table Tab&#41;](../../2014/integration-services/fuzzy-lookup-transformation-editor-reference-table-tab.md) </span></span>  
 [<span data-ttu-id="57b33-118">模糊查找转换编辑器（“列”选项卡）</span><span class="sxs-lookup"><span data-stu-id="57b33-118">Fuzzy Lookup Transformation Editor &#40;Columns Tab&#41;</span></span>](../../2014/integration-services/fuzzy-lookup-transformation-editor-columns-tab.md)  
  
  
