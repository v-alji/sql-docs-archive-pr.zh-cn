---
title: 合并联接转换编辑器 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.mergejointransformation.f1
helpviewer_keywords:
- Merge Join Transformation Editor
ms.assetid: ac06f419-30b3-42aa-8b34-42000bec4285
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e0d15d1233c2e0ff836e9dbd17459e56c48183f6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587903"
---
# <a name="merge-join-transformation-editor"></a><span data-ttu-id="588c5-102">合并联接转换编辑器</span><span class="sxs-lookup"><span data-stu-id="588c5-102">Merge Join Transformation Editor</span></span>
  <span data-ttu-id="588c5-103">可以使用 **“合并联接转换编辑器”** 对话框指定联接类型、联接列和输出列，以合并通过联接组合的两个输入。</span><span class="sxs-lookup"><span data-stu-id="588c5-103">Use the **Merge Join Transformation Editor** dialog box to specify the join type, the join columns, and the output columns for merging two inputs combined by a join.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="588c5-104">合并联接转换要求输入已排序的数据。</span><span class="sxs-lookup"><span data-stu-id="588c5-104">The Merge Join Transformation requires sorted data for its inputs.</span></span> <span data-ttu-id="588c5-105">有关此重要要求的详细信息，请参阅 [为合并转换和合并联接转换排序数据](data-flow/transformations/sort-data-for-the-merge-and-merge-join-transformations.md)。</span><span class="sxs-lookup"><span data-stu-id="588c5-105">For more information about this important requirement, see [Sort Data for the Merge and Merge Join Transformations](data-flow/transformations/sort-data-for-the-merge-and-merge-join-transformations.md).</span></span>  
  
 <span data-ttu-id="588c5-106">若要了解有关合并联接转换的详细信息，请参阅 [Merge Join Transformation](data-flow/transformations/merge-join-transformation.md)。</span><span class="sxs-lookup"><span data-stu-id="588c5-106">To learn more about the Merge Join transformation, see [Merge Join Transformation](data-flow/transformations/merge-join-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="588c5-107">选项</span><span class="sxs-lookup"><span data-stu-id="588c5-107">Options</span></span>  
 <span data-ttu-id="588c5-108">**联接类型**</span><span class="sxs-lookup"><span data-stu-id="588c5-108">**Join type**</span></span>  
 <span data-ttu-id="588c5-109">指定要使用内部联接、左外部联接还是完全联接。</span><span class="sxs-lookup"><span data-stu-id="588c5-109">Specify whether you want to use an inner join, left outer join, or full join.</span></span>  
  
 <span data-ttu-id="588c5-110">**交换输入**</span><span class="sxs-lookup"><span data-stu-id="588c5-110">**Swap Inputs**</span></span>  
 <span data-ttu-id="588c5-111">通过使用“交换输入”\*\*\*\* 按钮来交换输入的顺序。</span><span class="sxs-lookup"><span data-stu-id="588c5-111">Switch the order between inputs by using the **Swap Inputs** button.</span></span> <span data-ttu-id="588c5-112">对于左外部联接选项，此选项可能有用。</span><span class="sxs-lookup"><span data-stu-id="588c5-112">This selection may be useful with the Left outer join option.</span></span>  
  
 <span data-ttu-id="588c5-113">**输入**</span><span class="sxs-lookup"><span data-stu-id="588c5-113">**Input**</span></span>  
 <span data-ttu-id="588c5-114">对于要在合并的输出中包含的每个列，请首先从可用输入列表中相应地进行选择。</span><span class="sxs-lookup"><span data-stu-id="588c5-114">For each column that you want in the merged output, first select from the list of available inputs.</span></span>  
  
 <span data-ttu-id="588c5-115">输入显示在两个单独的表中。</span><span class="sxs-lookup"><span data-stu-id="588c5-115">Inputs are displayed in two separate tables.</span></span> <span data-ttu-id="588c5-116">请选择要包含在输出中的列。</span><span class="sxs-lookup"><span data-stu-id="588c5-116">Select columns to include in the output.</span></span> <span data-ttu-id="588c5-117">通过拖动列可以在表之间创建联接。</span><span class="sxs-lookup"><span data-stu-id="588c5-117">Drag columns to create a join between the tables.</span></span> <span data-ttu-id="588c5-118">若要删除某个联接，请选定该联接，再按 Delete 键。</span><span class="sxs-lookup"><span data-stu-id="588c5-118">To delete a join, select it and then press the DELETE key.</span></span>  
  
 <span data-ttu-id="588c5-119">**输入列**</span><span class="sxs-lookup"><span data-stu-id="588c5-119">**Input Column**</span></span>  
 <span data-ttu-id="588c5-120">从所选输入的可用列的列表中选择要包含在合并的输出中的列。</span><span class="sxs-lookup"><span data-stu-id="588c5-120">Select a column to include in the merged output from the list of available columns on the selected input.</span></span>  
  
 <span data-ttu-id="588c5-121">**输出别名**</span><span class="sxs-lookup"><span data-stu-id="588c5-121">**Output Alias**</span></span>  
 <span data-ttu-id="588c5-122">为每个输出列键入一个别名。</span><span class="sxs-lookup"><span data-stu-id="588c5-122">Type an alias for each output column.</span></span> <span data-ttu-id="588c5-123">默认值为输入列的名称；不过，您也可以任选一个唯一的描述性名称。</span><span class="sxs-lookup"><span data-stu-id="588c5-123">The default is the name of the input column; however, you can choose any unique, descriptive name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="588c5-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="588c5-124">See Also</span></span>  
 <span data-ttu-id="588c5-125">[Integration Services 错误和消息引用](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="588c5-125">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="588c5-126">[为合并和合并联接转换排序数据](data-flow/transformations/sort-data-for-the-merge-and-merge-join-transformations.md) </span><span class="sxs-lookup"><span data-stu-id="588c5-126">[Sort Data for the Merge and Merge Join Transformations](data-flow/transformations/sort-data-for-the-merge-and-merge-join-transformations.md) </span></span>  
 <span data-ttu-id="588c5-127">[使用合并联接转换扩展数据集](data-flow/transformations/extend-a-dataset-by-using-the-merge-join-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="588c5-127">[Extend a Dataset by Using the Merge Join Transformation](data-flow/transformations/extend-a-dataset-by-using-the-merge-join-transformation.md) </span></span>  
 <span data-ttu-id="588c5-128">[合并转换](data-flow/transformations/merge-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="588c5-128">[Merge Transformation](data-flow/transformations/merge-transformation.md) </span></span>  
 [<span data-ttu-id="588c5-129">Union All 转换</span><span class="sxs-lookup"><span data-stu-id="588c5-129">Union All Transformation</span></span>](data-flow/transformations/union-all-transformation.md)  
  
  
