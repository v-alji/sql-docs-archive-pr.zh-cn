---
title: Union All 转换 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.unionalltrans.f1
helpviewer_keywords:
- merging datasets [Integration Services]
- combining datasets
- Union All transformation
- datasets [Integration Services], merging
ms.assetid: 942e4b90-9c41-4e9c-a6f3-80b3afe57f2f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: eaaab1abf2587979e947cc1be24cbedf8f61b6e4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589784"
---
# <a name="union-all-transformation"></a><span data-ttu-id="b6859-102">Union All 转换</span><span class="sxs-lookup"><span data-stu-id="b6859-102">Union All Transformation</span></span>
  <span data-ttu-id="b6859-103">Union All 转换将多个输入组合到一个输出中。</span><span class="sxs-lookup"><span data-stu-id="b6859-103">The Union All transformation combines multiple inputs into one output.</span></span> <span data-ttu-id="b6859-104">例如，可将来自五个不同平面文件源的输出输入到 Union All 转换并将其组合到一个输出中。</span><span class="sxs-lookup"><span data-stu-id="b6859-104">For example, the outputs from five different Flat File sources can be inputs to the Union All transformation and combined into one output.</span></span>  
  
## <a name="inputs-and-outputs"></a><span data-ttu-id="b6859-105">输入和输出</span><span class="sxs-lookup"><span data-stu-id="b6859-105">Inputs and Outputs</span></span>  
 <span data-ttu-id="b6859-106">转换输入是一个接一个地添加到转换输出中的；不对行进行重新排序。</span><span class="sxs-lookup"><span data-stu-id="b6859-106">The transformation inputs are added to the transformation output one after the other; no reordering of rows occurs.</span></span> <span data-ttu-id="b6859-107">如果包需要排序的输出，则应使用合并转换而不是 Union All 转换。</span><span class="sxs-lookup"><span data-stu-id="b6859-107">If the package requires a sorted output, you should use the Merge transformation instead of the Union All transformation.</span></span>  
  
 <span data-ttu-id="b6859-108">连接到 Union All 转换的第一个输入是转换从中创建转换输出的输入。</span><span class="sxs-lookup"><span data-stu-id="b6859-108">The first input that you connect to the Union All transformation is the input from which the transformation creates the transformation output.</span></span> <span data-ttu-id="b6859-109">随后连接到转换的输入中的列将会被映射到转换输出中的列。</span><span class="sxs-lookup"><span data-stu-id="b6859-109">The columns in the inputs you subsequently connect to the transformation are mapped to the columns in the transformation output.</span></span>  
  
 <span data-ttu-id="b6859-110">若要合并输入，可将输入中的列映射到输出中的列。</span><span class="sxs-lookup"><span data-stu-id="b6859-110">To merge inputs, you map columns in the inputs to columns in the output.</span></span> <span data-ttu-id="b6859-111">每个输出列至少要有一个输入中的列与其映射。</span><span class="sxs-lookup"><span data-stu-id="b6859-111">A column from at least one input must be mapped to each output column.</span></span> <span data-ttu-id="b6859-112">两列间的映射要求各列的元数据相匹配。</span><span class="sxs-lookup"><span data-stu-id="b6859-112">The mapping between two columns requires that the metadata of the columns match.</span></span> <span data-ttu-id="b6859-113">例如，映射列必须具有相同的数据类型。</span><span class="sxs-lookup"><span data-stu-id="b6859-113">For example, the mapped columns must have the same data type.</span></span>  
  
 <span data-ttu-id="b6859-114">如果映射列包含字符串数据，并且输出列的长度比输入列短，则输出列长度会自动增加以便包含输入列。</span><span class="sxs-lookup"><span data-stu-id="b6859-114">If the mapped columns contain string data and the output column is shorter in length than the input column, the output column is automatically increased in length to contain the input column.</span></span> <span data-ttu-id="b6859-115">未映射到输出列的输入列在输出列中被设置为空值。</span><span class="sxs-lookup"><span data-stu-id="b6859-115">Input columns that are not mapped to output columns are set to null values in the output columns.</span></span>  
  
 <span data-ttu-id="b6859-116">此转换具有多个输入和一个输出。</span><span class="sxs-lookup"><span data-stu-id="b6859-116">This transformation has multiple inputs and one output.</span></span> <span data-ttu-id="b6859-117">它不支持错误输出。</span><span class="sxs-lookup"><span data-stu-id="b6859-117">It does not support an error output.</span></span>  
  
## <a name="configuration-of-the-union-all-transformation"></a><span data-ttu-id="b6859-118">Union All 转换的配置</span><span class="sxs-lookup"><span data-stu-id="b6859-118">Configuration of the Union All Transformation</span></span>  
 <span data-ttu-id="b6859-119">可以通过 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器或以编程方式来设置属性。</span><span class="sxs-lookup"><span data-stu-id="b6859-119">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="b6859-120">有关可以在 **“Union All 转换编辑器”** 对话框中设置的属性的详细信息，请参阅 [Union All Transformation Editor](../../union-all-transformation-editor.md)。</span><span class="sxs-lookup"><span data-stu-id="b6859-120">For more information about the properties that you can set in the **Union All Transformation Editor** dialog box, see [Union All Transformation Editor](../../union-all-transformation-editor.md).</span></span>  
  
 <span data-ttu-id="b6859-121">有关可以编程方式设置的属性的详细信息，请参阅 [Common Properties](../../common-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="b6859-121">For more information about the properties that you can set programmatically, see [Common Properties](../../common-properties.md).</span></span>  
  
 <span data-ttu-id="b6859-122">有关如何设置属性的详细信息，请单击下列主题之一：</span><span class="sxs-lookup"><span data-stu-id="b6859-122">For more information about how to set properties, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="b6859-123">设置数据流组件的属性</span><span class="sxs-lookup"><span data-stu-id="b6859-123">Set the Properties of a Data Flow Component</span></span>](../set-the-properties-of-a-data-flow-component.md)  
  
## <a name="related-tasks"></a><span data-ttu-id="b6859-124">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="b6859-124">Related Tasks</span></span>  
 [<span data-ttu-id="b6859-125">通过使用 Union All 转换来合并数据</span><span class="sxs-lookup"><span data-stu-id="b6859-125">Merge Data by Using the Union All Transformation</span></span>](union-all-transformation.md)  
  
  
