---
title: 字词提取转换编辑器 (高级选项卡) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.termextraction.advanced.f1
helpviewer_keywords:
- Term Extraction Transformation Editor
ms.assetid: 87118281-6e3c-499e-bac4-fa4c24bb12c6
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f4be56f8ac2deeab49e43071a07894a466019287
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690718"
---
# <a name="term-extraction-transformation-editor-advanced-tab"></a><span data-ttu-id="a7072-102">字词提取转换编辑器（“高级”选项卡）</span><span class="sxs-lookup"><span data-stu-id="a7072-102">Term Extraction Transformation Editor (Advanced Tab)</span></span>
  <span data-ttu-id="a7072-103">可以使用 **“字词提取转换编辑器”** 对话框的 **“高级”** 选项卡，指定频率、长度等提取属性以及指定是提取字词还是提取短语。</span><span class="sxs-lookup"><span data-stu-id="a7072-103">Use the **Advanced** tab of the **Term Extraction Transformation Editor** dialog box to specify properties for the extraction such as frequency, length, and whether to extract words or phrases.</span></span>  
  
 <span data-ttu-id="a7072-104">若要了解有关字词提取转换的详细信息，请参阅 [Term Extraction Transformation](data-flow/transformations/term-extraction-transformation.md)。</span><span class="sxs-lookup"><span data-stu-id="a7072-104">To learn more about the Term Extraction transformation, see [Term Extraction Transformation](data-flow/transformations/term-extraction-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="a7072-105">选项</span><span class="sxs-lookup"><span data-stu-id="a7072-105">Options</span></span>  
 <span data-ttu-id="a7072-106">**名词**</span><span class="sxs-lookup"><span data-stu-id="a7072-106">**Noun**</span></span>  
 <span data-ttu-id="a7072-107">指定转换仅提取各个名词。</span><span class="sxs-lookup"><span data-stu-id="a7072-107">Specify that the transformation extracts individual nouns only.</span></span>  
  
 <span data-ttu-id="a7072-108">**名词短语**</span><span class="sxs-lookup"><span data-stu-id="a7072-108">**Noun phrase**</span></span>  
 <span data-ttu-id="a7072-109">指定转换仅提取名词短语。</span><span class="sxs-lookup"><span data-stu-id="a7072-109">Specify that the transformation extracts noun phrases only.</span></span>  
  
 <span data-ttu-id="a7072-110">**名词和名词短语**</span><span class="sxs-lookup"><span data-stu-id="a7072-110">**Noun and noun phrase**</span></span>  
 <span data-ttu-id="a7072-111">指定转换既提取名词也提取名词短语。</span><span class="sxs-lookup"><span data-stu-id="a7072-111">Specify that the transformation extracts both nouns and noun phrases.</span></span>  
  
 <span data-ttu-id="a7072-112">**频率**</span><span class="sxs-lookup"><span data-stu-id="a7072-112">**Frequency**</span></span>  
 <span data-ttu-id="a7072-113">指定分数为字词的频率。</span><span class="sxs-lookup"><span data-stu-id="a7072-113">Specify that the score is the frequency of the term.</span></span>  
  
 <span data-ttu-id="a7072-114">**TFIDF**</span><span class="sxs-lookup"><span data-stu-id="a7072-114">**TFIDF**</span></span>  
 <span data-ttu-id="a7072-115">指定分数为字词的 TFIDF 值。</span><span class="sxs-lookup"><span data-stu-id="a7072-115">Specify that the score is the TFIDF value of the term.</span></span> <span data-ttu-id="a7072-116">TFIDF 分数是字词频率和文档频率倒数的乘积，其定义如下：TFIDF of a Term T = (frequency of T) \* log( (#rows in Input) / (#rows having T) )。</span><span class="sxs-lookup"><span data-stu-id="a7072-116">The TFIDF score is the product of Term Frequency and Inverse Document Frequency, defined as: TFIDF of a Term T = (frequency of T) \* log( (#rows in Input) / (#rows having T) )</span></span>  
  
 <span data-ttu-id="a7072-117">**频率阈值**</span><span class="sxs-lookup"><span data-stu-id="a7072-117">**Frequency threshold**</span></span>  
 <span data-ttu-id="a7072-118">指定某个词或短语必须出现多少次以后才对其进行提取。</span><span class="sxs-lookup"><span data-stu-id="a7072-118">Specify the number of times a word or phrase must occur before extracting it.</span></span> <span data-ttu-id="a7072-119">默认值为 2。</span><span class="sxs-lookup"><span data-stu-id="a7072-119">The default value is 2.</span></span>  
  
 <span data-ttu-id="a7072-120">**字词的最大长度**</span><span class="sxs-lookup"><span data-stu-id="a7072-120">**Maximum length of term**</span></span>  
 <span data-ttu-id="a7072-121">指定短语的最大长度（字）。</span><span class="sxs-lookup"><span data-stu-id="a7072-121">Specify the maximum length of a phrase in words.</span></span> <span data-ttu-id="a7072-122">此选项仅影响名词短语。</span><span class="sxs-lookup"><span data-stu-id="a7072-122">This option affects noun phrases only.</span></span> <span data-ttu-id="a7072-123">默认值为 12。</span><span class="sxs-lookup"><span data-stu-id="a7072-123">The default value is 12.</span></span>  
  
 <span data-ttu-id="a7072-124">**使用区分大小写的字词提取**</span><span class="sxs-lookup"><span data-stu-id="a7072-124">**Use case-sensitive term extraction**</span></span>  
 <span data-ttu-id="a7072-125">指定是否将提取设置为区分大小写。</span><span class="sxs-lookup"><span data-stu-id="a7072-125">Specify whether to make the extraction case-sensitive.</span></span> <span data-ttu-id="a7072-126">默认值为 `False`。</span><span class="sxs-lookup"><span data-stu-id="a7072-126">The default is `False`.</span></span>  
  
 <span data-ttu-id="a7072-127">**配置错误输出**</span><span class="sxs-lookup"><span data-stu-id="a7072-127">**Configure Error Output**</span></span>  
 <span data-ttu-id="a7072-128">使用[“配置错误输出” ](../../2014/integration-services/configure-error-output.md) 对话框可以为导致错误的行指定错误处理方式。</span><span class="sxs-lookup"><span data-stu-id="a7072-128">Use the [Configure Error Output](../../2014/integration-services/configure-error-output.md) dialog box to specify error handling for rows that cause errors.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7072-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a7072-129">See Also</span></span>  
 <span data-ttu-id="a7072-130">[Integration Services 错误和消息引用](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="a7072-130">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="a7072-131">[字词提取转换编辑器 &#40;字词提取选项卡&#41;](../../2014/integration-services/term-extraction-transformation-editor-term-extraction-tab.md) </span><span class="sxs-lookup"><span data-stu-id="a7072-131">[Term Extraction Transformation Editor &#40;Term Extraction Tab&#41;](../../2014/integration-services/term-extraction-transformation-editor-term-extraction-tab.md) </span></span>  
 <span data-ttu-id="a7072-132">[字词提取转换编辑器 &#40;排除选项卡&#41;](../../2014/integration-services/term-extraction-transformation-editor-exclusion-tab.md) </span><span class="sxs-lookup"><span data-stu-id="a7072-132">[Term Extraction Transformation Editor &#40;Exclusion Tab&#41;](../../2014/integration-services/term-extraction-transformation-editor-exclusion-tab.md) </span></span>  
 [<span data-ttu-id="a7072-133">字词查找转换</span><span class="sxs-lookup"><span data-stu-id="a7072-133">Term Lookup Transformation</span></span>](data-flow/transformations/lookup-transformation.md)  
  
  
