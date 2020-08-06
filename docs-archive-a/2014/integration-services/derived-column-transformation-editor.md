---
title: 派生列转换编辑器 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.derivedcolumntransformation.f1
helpviewer_keywords:
- Derived Column Transformation Editor
ms.assetid: ff73923e-d245-43d8-bf24-af3bdc942e51
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 41a0f0dcd253473f78f2f38426b5fbd3d2ac2812
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590307"
---
# <a name="derived-column-transformation-editor"></a><span data-ttu-id="ee1d4-102">派生列转换编辑器</span><span class="sxs-lookup"><span data-stu-id="ee1d4-102">Derived Column Transformation Editor</span></span>
  <span data-ttu-id="ee1d4-103">可以使用 **“派生列转换编辑器”** 对话框，创建填充新列或替换列的表达式。</span><span class="sxs-lookup"><span data-stu-id="ee1d4-103">Use the **Derived Column Transformation Editor** dialog box to create expressions that populate new or replacement columns.</span></span>  
  
 <span data-ttu-id="ee1d4-104">若要了解有关派生列转换的详细信息，请参阅 [Derived Column Transformation](data-flow/transformations/derived-column-transformation.md)。</span><span class="sxs-lookup"><span data-stu-id="ee1d4-104">To learn more about the Derived Column transformation, see [Derived Column Transformation](data-flow/transformations/derived-column-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="ee1d4-105">选项</span><span class="sxs-lookup"><span data-stu-id="ee1d4-105">Options</span></span>  
 <span data-ttu-id="ee1d4-106">**变量和列**</span><span class="sxs-lookup"><span data-stu-id="ee1d4-106">**Variables and Columns**</span></span>  
 <span data-ttu-id="ee1d4-107">通过将变量或输入列从可用变量和列的列表中拖到下面窗格中的现有表行，或者拖到列表底部的新行中，生成使用变量或输入列的表达式。</span><span class="sxs-lookup"><span data-stu-id="ee1d4-107">Build an expression that uses a variable or an input column by dragging the variable or column from the list of available variables and columns to an existing table row in the pane below, or to a new row at the bottom of the list.</span></span>  
  
 <span data-ttu-id="ee1d4-108">**函数和运算符**</span><span class="sxs-lookup"><span data-stu-id="ee1d4-108">**Functions and Operators**</span></span>  
 <span data-ttu-id="ee1d4-109">通过将函数和运算符从列表中拖到下面的窗格中，生成使用函数或运算符的表达式，以计算输入数据和直接输出数据。</span><span class="sxs-lookup"><span data-stu-id="ee1d4-109">Build an expression that uses a function or an operator to evaluate input data and direct output data by dragging functions and operators from the list to the pane below.</span></span>  
  
 <span data-ttu-id="ee1d4-110">**派生列名称**</span><span class="sxs-lookup"><span data-stu-id="ee1d4-110">**Derived Column Name**</span></span>  
 <span data-ttu-id="ee1d4-111">提供派生列名称。</span><span class="sxs-lookup"><span data-stu-id="ee1d4-111">Provide a derived column name.</span></span> <span data-ttu-id="ee1d4-112">默认值为带编号的派生列列表；不过，您也可以任选一个唯一的描述性名称。</span><span class="sxs-lookup"><span data-stu-id="ee1d4-112">The default is a numbered list of derived columns; however, you can choose any unique, descriptive name.</span></span>  
  
 <span data-ttu-id="ee1d4-113">**派生列**</span><span class="sxs-lookup"><span data-stu-id="ee1d4-113">**Derived Column**</span></span>  
 <span data-ttu-id="ee1d4-114">从列表中选择派生列。</span><span class="sxs-lookup"><span data-stu-id="ee1d4-114">Select a derived column from the list.</span></span> <span data-ttu-id="ee1d4-115">选择是将派生列添加为新的输出列，还是替换现有列中的数据。</span><span class="sxs-lookup"><span data-stu-id="ee1d4-115">Choose whether to add the derived column as a new output column, or to replace the data in an existing column.</span></span>  
  
 <span data-ttu-id="ee1d4-116">**表达式**</span><span class="sxs-lookup"><span data-stu-id="ee1d4-116">**Expression**</span></span>  
 <span data-ttu-id="ee1d4-117">键入表达式，或通过从可用列、变量、函数和运算符的以前列表中进行拖动来生成表达式。</span><span class="sxs-lookup"><span data-stu-id="ee1d4-117">Type an expression or build one by dragging from the previous list of available columns, variables, functions, and operators.</span></span>  
  
 <span data-ttu-id="ee1d4-118">此属性的值可以使用属性表达式来指定。</span><span class="sxs-lookup"><span data-stu-id="ee1d4-118">The value of this property can be specified by using a property expression.</span></span>  
  
 <span data-ttu-id="ee1d4-119">**相关主题**：[Integration Services (SSIS) 表达式](expressions/integration-services-ssis-expressions.md)、[运算符（SSIS 表达式）](expressions/operators-ssis-expression.md)和[函数（SSIS 表达式）](expressions/functions-ssis-expression.md)</span><span class="sxs-lookup"><span data-stu-id="ee1d4-119">**Related topics**: [Integration Services &#40;SSIS&#41; Expressions](expressions/integration-services-ssis-expressions.md), [Operators &#40;SSIS Expression&#41;](expressions/operators-ssis-expression.md), and [Functions &#40;SSIS Expression&#41;](expressions/functions-ssis-expression.md)</span></span>  
  
 <span data-ttu-id="ee1d4-120">**数据类型**</span><span class="sxs-lookup"><span data-stu-id="ee1d4-120">**Data Type**</span></span>  
 <span data-ttu-id="ee1d4-121">如果向新列中添加数据，“派生列转换编辑器”\*\*\*\* 对话框将自动计算表达式的值并设置相应的数据类型。</span><span class="sxs-lookup"><span data-stu-id="ee1d4-121">If adding data to a new column, the **Derived Column TransformationEditor** dialog box automatically evaluates the expression and sets the data type appropriately.</span></span> <span data-ttu-id="ee1d4-122">该列的值是只读的。</span><span class="sxs-lookup"><span data-stu-id="ee1d4-122">The value of this column is read-only.</span></span> <span data-ttu-id="ee1d4-123">有关详细信息，请参阅 [Integration Services 数据类型](data-flow/integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="ee1d4-123">For more information, see [Integration Services Data Types](data-flow/integration-services-data-types.md).</span></span>  
  
 <span data-ttu-id="ee1d4-124">**长度**</span><span class="sxs-lookup"><span data-stu-id="ee1d4-124">**Length**</span></span>  
 <span data-ttu-id="ee1d4-125">如果向新列中添加数据，“派生列转换编辑器”\*\*\*\* 对话框将自动计算表达式的值并设置字符串数据的列长度。</span><span class="sxs-lookup"><span data-stu-id="ee1d4-125">If adding data to a new column, the **Derived Column TransformationEditor** dialog box automatically evaluates the expression and sets the column length for string data.</span></span> <span data-ttu-id="ee1d4-126">该列的值是只读的。</span><span class="sxs-lookup"><span data-stu-id="ee1d4-126">The value of this column is read-only.</span></span>  
  
 <span data-ttu-id="ee1d4-127">**精度**</span><span class="sxs-lookup"><span data-stu-id="ee1d4-127">**Precision**</span></span>  
 <span data-ttu-id="ee1d4-128">如果向新列中添加数据，“派生列转换编辑器”\*\*\*\* 对话框将自动根据数据类型来设置数值数据的精度。</span><span class="sxs-lookup"><span data-stu-id="ee1d4-128">If adding data to a new column, the **Derived Column TransformationEditor** dialog box automatically sets the precision for numeric data based on the data type.</span></span> <span data-ttu-id="ee1d4-129">该列的值是只读的。</span><span class="sxs-lookup"><span data-stu-id="ee1d4-129">The value of this column is read-only.</span></span>  
  
 <span data-ttu-id="ee1d4-130">**缩放**</span><span class="sxs-lookup"><span data-stu-id="ee1d4-130">**Scale**</span></span>  
 <span data-ttu-id="ee1d4-131">如果向新列中添加数据，“派生列转换编辑器”\*\*\*\* 对话框将自动根据数据类型来设置数值数据的小数位数。</span><span class="sxs-lookup"><span data-stu-id="ee1d4-131">If adding data to a new column, the **Derived Column TransformationEditor** dialog box automatically sets the scale for numeric data based on the data type.</span></span> <span data-ttu-id="ee1d4-132">该列的值是只读的。</span><span class="sxs-lookup"><span data-stu-id="ee1d4-132">The value of this column is read-only.</span></span>  
  
 <span data-ttu-id="ee1d4-133">**代码页**</span><span class="sxs-lookup"><span data-stu-id="ee1d4-133">**Code Page**</span></span>  
 <span data-ttu-id="ee1d4-134">如果向新列中添加数据，“派生列转换编辑器”\*\*\*\* 对话框将自动设置 DT_STR 数据类型的代码页。</span><span class="sxs-lookup"><span data-stu-id="ee1d4-134">If adding data to a new column, the **Derived Column TransformationEditor** dialog box automatically sets code page for the DT_STR data type.</span></span> <span data-ttu-id="ee1d4-135">可以更新 **“代码页”**。</span><span class="sxs-lookup"><span data-stu-id="ee1d4-135">You can update **Code Page**.</span></span>  
  
 <span data-ttu-id="ee1d4-136">**配置错误输出**</span><span class="sxs-lookup"><span data-stu-id="ee1d4-136">**Configure error output**</span></span>  
 <span data-ttu-id="ee1d4-137">使用 [配置错误输出](../../2014/integration-services/configure-error-output.md) 对话框指定处理错误的方式。</span><span class="sxs-lookup"><span data-stu-id="ee1d4-137">Specify how to handle errors by using the [Configure Error Output](../../2014/integration-services/configure-error-output.md) dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee1d4-138">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ee1d4-138">See Also</span></span>  
 <span data-ttu-id="ee1d4-139">[Integration Services 错误和消息引用](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="ee1d4-139">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 [<span data-ttu-id="ee1d4-140">使用派生列转换派生列值</span><span class="sxs-lookup"><span data-stu-id="ee1d4-140">Derive Column Values by Using the Derived Column Transformation</span></span>](data-flow/transformations/derive-column-values-by-using-the-derived-column-transformation.md)  
  
  
