---
title: 合并转换 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.mergetrans.f1
helpviewer_keywords:
- merging datasets [Integration Services]
- merging data [Integration Services]
- Merge transformation
- combining datasets
- datasets [Integration Services], merging
ms.assetid: cff8690c-07ac-46a0-aab5-20bd4848c677
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7d1d35e92b5978016b6a53956e5b6f1f6642f5ee
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693005"
---
# <a name="merge-transformation"></a><span data-ttu-id="3c414-102">合并转换</span><span class="sxs-lookup"><span data-stu-id="3c414-102">Merge Transformation</span></span>
  <span data-ttu-id="3c414-103">合并转换将两个排序后的数据集合并为一个数据集。</span><span class="sxs-lookup"><span data-stu-id="3c414-103">The Merge transformation combines two sorted datasets into a single dataset.</span></span> <span data-ttu-id="3c414-104">根据每个数据集中的行的键列的值，将这些行插入到输出中。</span><span class="sxs-lookup"><span data-stu-id="3c414-104">The rows from each dataset are inserted into the output based on values in their key columns.</span></span>  
  
 <span data-ttu-id="3c414-105">通过将合并转换纳入数据流，可以执行下列任务：</span><span class="sxs-lookup"><span data-stu-id="3c414-105">By including the Merge transformation in a data flow, you can perform the following tasks:</span></span>  
  
-   <span data-ttu-id="3c414-106">合并两个数据源的数据，如表和文件。</span><span class="sxs-lookup"><span data-stu-id="3c414-106">Merge data from two data sources, such as tables and files.</span></span>  
  
-   <span data-ttu-id="3c414-107">通过嵌套合并转换来创建复杂数据集。</span><span class="sxs-lookup"><span data-stu-id="3c414-107">Create complex datasets by nesting Merge transformations.</span></span>  
  
-   <span data-ttu-id="3c414-108">更正数据中的错误后重新合并行。</span><span class="sxs-lookup"><span data-stu-id="3c414-108">Remerge rows after correcting errors in the data.</span></span>  
  
 <span data-ttu-id="3c414-109">合并转换与 Union All 转换类似。</span><span class="sxs-lookup"><span data-stu-id="3c414-109">The Merge transformation is similar to the Union All transformations.</span></span> <span data-ttu-id="3c414-110">在下列情况下，请使用 Union All 转换代替合并转换：</span><span class="sxs-lookup"><span data-stu-id="3c414-110">Use the Union All transformation instead of the Merge transformation in the following situations:</span></span>  
  
-   <span data-ttu-id="3c414-111">转换输入未排序。</span><span class="sxs-lookup"><span data-stu-id="3c414-111">The transformation inputs are not sorted.</span></span>  
  
-   <span data-ttu-id="3c414-112">合并的输出无需排序。</span><span class="sxs-lookup"><span data-stu-id="3c414-112">The combined output does not need to be sorted.</span></span>  
  
-   <span data-ttu-id="3c414-113">转换的输入超过两个。</span><span class="sxs-lookup"><span data-stu-id="3c414-113">The transformation has more than two inputs.</span></span>  
  
## <a name="input-requirements"></a><span data-ttu-id="3c414-114">输入要求</span><span class="sxs-lookup"><span data-stu-id="3c414-114">Input Requirements</span></span>  
 <span data-ttu-id="3c414-115">合并转换要求输入已排序的数据。</span><span class="sxs-lookup"><span data-stu-id="3c414-115">The Merge Transformation requires sorted data for its inputs.</span></span> <span data-ttu-id="3c414-116">有关此重要要求的详细信息，请参阅 [为合并转换和合并联接转换排序数据](sort-data-for-the-merge-and-merge-join-transformations.md)。</span><span class="sxs-lookup"><span data-stu-id="3c414-116">For more information about this important requirement, see [Sort Data for the Merge and Merge Join Transformations](sort-data-for-the-merge-and-merge-join-transformations.md).</span></span>  
  
 <span data-ttu-id="3c414-117">合并转换还要求输入中的已合并列具有匹配的元数据。</span><span class="sxs-lookup"><span data-stu-id="3c414-117">The Merge transformation also requires that the merged columns in its inputs have matching metadata.</span></span> <span data-ttu-id="3c414-118">例如，不能合并包含数值数据类型的列和包含字符数据类型的列。</span><span class="sxs-lookup"><span data-stu-id="3c414-118">For example, you cannot merge a column that has a numeric data type with a column that has a character data type.</span></span> <span data-ttu-id="3c414-119">如果数据为字符串数据类型，第二个输入中列的长度必须小于或等于被合并的第一个输入中列的长度。</span><span class="sxs-lookup"><span data-stu-id="3c414-119">If the data has a string data type, the length of the column in the second input must be less than or equal to the length of the column in the first input with which it is merged.</span></span>  
  
 <span data-ttu-id="3c414-120">在 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器中，合并转换的用户界面会自动映射具有相同元数据的列。</span><span class="sxs-lookup"><span data-stu-id="3c414-120">In the [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, the user interface for the Merge transformation automatically maps columns that have the same metadata.</span></span> <span data-ttu-id="3c414-121">然后，您可以手动映射具有兼容数据类型的其他列。</span><span class="sxs-lookup"><span data-stu-id="3c414-121">You can then manually map other columns that have compatible data types.</span></span>  
  
 <span data-ttu-id="3c414-122">此转换有两个输入和一个输出。</span><span class="sxs-lookup"><span data-stu-id="3c414-122">This transformation has two inputs and one output.</span></span> <span data-ttu-id="3c414-123">它不支持错误输出。</span><span class="sxs-lookup"><span data-stu-id="3c414-123">It does not support an error output.</span></span>  
  
## <a name="configuration-of-the-merge-transformation"></a><span data-ttu-id="3c414-124">合并转换的配置</span><span class="sxs-lookup"><span data-stu-id="3c414-124">Configuration of the Merge Transformation</span></span>  
 <span data-ttu-id="3c414-125">可以通过 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器或以编程方式来设置属性。</span><span class="sxs-lookup"><span data-stu-id="3c414-125">You can set properties through the [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="3c414-126">有关可以在 **“合并转换编辑器”** 对话框中设置的属性的详细信息，请参阅 [Merge Transformation Editor](../../merge-transformation-editor.md)。</span><span class="sxs-lookup"><span data-stu-id="3c414-126">For more information about the properties that you can set in the **Merge Transformation Editor** dialog box, see [Merge Transformation Editor](../../merge-transformation-editor.md).</span></span>  
  
 <span data-ttu-id="3c414-127">有关可以用编程方式设置的属性的详细信息，请单击下列主题之一：</span><span class="sxs-lookup"><span data-stu-id="3c414-127">For more information about the properties that you can programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="3c414-128">Common Properties</span><span class="sxs-lookup"><span data-stu-id="3c414-128">Common Properties</span></span>](../../common-properties.md)  
  
-   [<span data-ttu-id="3c414-129">转换自定义属性</span><span class="sxs-lookup"><span data-stu-id="3c414-129">Transformation Custom Properties</span></span>](transformation-custom-properties.md)  
  
## <a name="related-tasks"></a><span data-ttu-id="3c414-130">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="3c414-130">Related Tasks</span></span>  
 <span data-ttu-id="3c414-131">有关如何设置属性的详细信息，请参阅以下主题：</span><span class="sxs-lookup"><span data-stu-id="3c414-131">For details about how to set properties, see the following topics:</span></span>  
  
-   [<span data-ttu-id="3c414-132">设置数据流组件的属性</span><span class="sxs-lookup"><span data-stu-id="3c414-132">Set the Properties of a Data Flow Component</span></span>](../set-the-properties-of-a-data-flow-component.md)  
  
-   [<span data-ttu-id="3c414-133">为合并转换和合并联接转换排序数据</span><span class="sxs-lookup"><span data-stu-id="3c414-133">Sort Data for the Merge and Merge Join Transformations</span></span>](sort-data-for-the-merge-and-merge-join-transformations.md)  
  
## <a name="see-also"></a><span data-ttu-id="3c414-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3c414-134">See Also</span></span>  
 <span data-ttu-id="3c414-135">[合并联接转换](merge-join-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="3c414-135">[Merge Join Transformation](merge-join-transformation.md) </span></span>  
 <span data-ttu-id="3c414-136">[Union All 转换](union-all-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="3c414-136">[Union All Transformation](union-all-transformation.md) </span></span>  
 <span data-ttu-id="3c414-137">[数据流](../data-flow.md) </span><span class="sxs-lookup"><span data-stu-id="3c414-137">[Data Flow](../data-flow.md) </span></span>  
 [<span data-ttu-id="3c414-138">Integration Services 转换</span><span class="sxs-lookup"><span data-stu-id="3c414-138">Integration Services Transformations</span></span>](integration-services-transformations.md)  
  
  
