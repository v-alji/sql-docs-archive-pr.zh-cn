---
title: 排序转换编辑器 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.sorttransformation.f1
helpviewer_keywords:
- Sort Transformation Editor
ms.assetid: 8ae23970-49a9-4d6d-9f15-c7074783347c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9f48c366f4337af29b03877f6bb20b804457a293
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694013"
---
# <a name="sort-transformation-editor"></a><span data-ttu-id="798c4-102">排序转换编辑器</span><span class="sxs-lookup"><span data-stu-id="798c4-102">Sort Transformation Editor</span></span>
  <span data-ttu-id="798c4-103">可以使用 **“排序转换编辑器”** 对话框，选择要排序的列，设置排序顺序以及指定是否删除重复项。</span><span class="sxs-lookup"><span data-stu-id="798c4-103">Use the **Sort Transformation Editor** dialog box to select the columns to sort, set the sort order, and specify whether duplicates are removed.</span></span>  
  
 <span data-ttu-id="798c4-104">若要了解有关排序转换的详细信息，请参阅 [Sort Transformation](data-flow/transformations/sort-transformation.md)。</span><span class="sxs-lookup"><span data-stu-id="798c4-104">To learn more about the Sort transformation, see [Sort Transformation](data-flow/transformations/sort-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="798c4-105">选项</span><span class="sxs-lookup"><span data-stu-id="798c4-105">Options</span></span>  
 <span data-ttu-id="798c4-106">**可用输入列**</span><span class="sxs-lookup"><span data-stu-id="798c4-106">**Available Input Columns**</span></span>  
 <span data-ttu-id="798c4-107">使用此复选框可以指定要排序的列。</span><span class="sxs-lookup"><span data-stu-id="798c4-107">Using the check boxes, specify the columns to sort.</span></span>  
  
 <span data-ttu-id="798c4-108">**名称**</span><span class="sxs-lookup"><span data-stu-id="798c4-108">**Name**</span></span>  
 <span data-ttu-id="798c4-109">查看每个可用输入列的名称。</span><span class="sxs-lookup"><span data-stu-id="798c4-109">View the name of each available input column.</span></span>  
  
 <span data-ttu-id="798c4-110">**直通**</span><span class="sxs-lookup"><span data-stu-id="798c4-110">**Passthrough**</span></span>  
 <span data-ttu-id="798c4-111">指示是否在排序输出中包含相应列。</span><span class="sxs-lookup"><span data-stu-id="798c4-111">Indicate whether to include the column in the sorted output.</span></span>  
  
 <span data-ttu-id="798c4-112">**输入列**</span><span class="sxs-lookup"><span data-stu-id="798c4-112">**Input Column**</span></span>  
 <span data-ttu-id="798c4-113">从每行的可用输入列的列表中选择。</span><span class="sxs-lookup"><span data-stu-id="798c4-113">Select from the list of available input columns for each row.</span></span> <span data-ttu-id="798c4-114">通过选中 **“可用输入列”** 表中的复选框来选择列。</span><span class="sxs-lookup"><span data-stu-id="798c4-114">Your selections are reflected in the check box selections in the **Available Input Columns** table.</span></span>  
  
 <span data-ttu-id="798c4-115">**输出别名**</span><span class="sxs-lookup"><span data-stu-id="798c4-115">**Output Alias**</span></span>  
 <span data-ttu-id="798c4-116">为每个输出列键入一个别名。</span><span class="sxs-lookup"><span data-stu-id="798c4-116">Type an alias for each output column.</span></span> <span data-ttu-id="798c4-117">默认值为输入列的名称；不过，您也可以任选一个唯一的描述性名称。</span><span class="sxs-lookup"><span data-stu-id="798c4-117">The default is the name of the input column; however, you can choose any unique, descriptive name.</span></span>  
  
 <span data-ttu-id="798c4-118">**排序类型**</span><span class="sxs-lookup"><span data-stu-id="798c4-118">**Sort Type**</span></span>  
 <span data-ttu-id="798c4-119">指示按升序还是按降序排序。</span><span class="sxs-lookup"><span data-stu-id="798c4-119">Indicate whether to sort in ascending or descending order.</span></span>  
  
 <span data-ttu-id="798c4-120">**排序顺序**</span><span class="sxs-lookup"><span data-stu-id="798c4-120">**Sort Order**</span></span>  
 <span data-ttu-id="798c4-121">指示列的排序顺序。</span><span class="sxs-lookup"><span data-stu-id="798c4-121">Indicate the order in which to sort columns.</span></span> <span data-ttu-id="798c4-122">必须对每列手动设置此选项。</span><span class="sxs-lookup"><span data-stu-id="798c4-122">This must be set manually for each column.</span></span>  
  
 <span data-ttu-id="798c4-123">**比较标志**</span><span class="sxs-lookup"><span data-stu-id="798c4-123">**Comparison Flags**</span></span>  
 <span data-ttu-id="798c4-124">有关字符串比较选项的信息，请参阅 [比较字符串数据](data-flow/comparing-string-data.md)。</span><span class="sxs-lookup"><span data-stu-id="798c4-124">For information about the string comparison options, see [Comparing String Data](data-flow/comparing-string-data.md).</span></span>  
  
 <span data-ttu-id="798c4-125">**删除具有重复排序值的行**</span><span class="sxs-lookup"><span data-stu-id="798c4-125">**Remove rows with duplicate sort values**</span></span>  
 <span data-ttu-id="798c4-126">根据指定的字符串比较选项，指示转换是将重复行复制到转换输出，还是为所有重复项创建单个条目。</span><span class="sxs-lookup"><span data-stu-id="798c4-126">Indicate whether the transformation copies duplicate rows to the transformation output, or creates a single entry for all duplicates, based on the specified string comparison options.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="798c4-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="798c4-127">See Also</span></span>  
 [<span data-ttu-id="798c4-128">Integration Services 错误和消息引用</span><span class="sxs-lookup"><span data-stu-id="798c4-128">Integration Services Error and Message Reference</span></span>](../../2014/integration-services/integration-services-error-and-message-reference.md)  
  
  
