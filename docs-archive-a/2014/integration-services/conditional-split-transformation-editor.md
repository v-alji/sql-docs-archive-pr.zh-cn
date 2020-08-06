---
title: 有条件拆分转换编辑器 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.conditionalsplittransformation.f1
helpviewer_keywords:
- Conditional Split Transformation Editor
ms.assetid: c30e1633-537a-4837-9991-6203c6f2a21e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 386a93eb7c3058c7c3e98f2b652199d115d841f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578365"
---
# <a name="conditional-split-transformation-editor"></a><span data-ttu-id="5e5a0-102">有条件拆分转换编辑器</span><span class="sxs-lookup"><span data-stu-id="5e5a0-102">Conditional Split Transformation Editor</span></span>
  <span data-ttu-id="5e5a0-103">可以使用 **“有条件拆分转换编辑器”** 对话框创建表达式，设置表达式计算顺序，以及对有条件拆分输出进行命名。</span><span class="sxs-lookup"><span data-stu-id="5e5a0-103">Use the **Conditional Split Transformation Editor** dialog box to create expressions, set the order in which expressions are evaluated, and name the outputs of a conditional split.</span></span> <span data-ttu-id="5e5a0-104">此对话框包含可以用于生成表达式的数学、字符串和日期/时间函数及运算符。</span><span class="sxs-lookup"><span data-stu-id="5e5a0-104">This dialog box includes mathematical, string, and date/time functions and operators that you can use to build expressions.</span></span> <span data-ttu-id="5e5a0-105">计算结果为 True 的第一个条件确定了行定向到的输出。</span><span class="sxs-lookup"><span data-stu-id="5e5a0-105">The first condition that evaluates as true determines the output to which a row is directed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5e5a0-106">有条件拆分转换仅将每个输入行定向到一个输出。</span><span class="sxs-lookup"><span data-stu-id="5e5a0-106">The Conditional Split transformation directs each input row to one output only.</span></span> <span data-ttu-id="5e5a0-107">如果输入多个条件，则转换会将每一行发送到条件为 True 的第一个输出，而忽略各行的后续条件。</span><span class="sxs-lookup"><span data-stu-id="5e5a0-107">If you enter multiple conditions, the transformation sends each row to the first output for which the condition is true and disregards subsequent conditions for that row.</span></span> <span data-ttu-id="5e5a0-108">如果需要连续计算多个条件，则可能需要在数据流中连接多个有条件拆分转换。</span><span class="sxs-lookup"><span data-stu-id="5e5a0-108">If you need to evaluate several conditions successively, you may need to concatenate multiple Conditional Split transformations in the data flow.</span></span>  
  
 <span data-ttu-id="5e5a0-109">若要了解有关有条件拆分转换的详细信息，请参阅 [有条件拆分转换](data-flow/transformations/conditional-split-transformation.md)。</span><span class="sxs-lookup"><span data-stu-id="5e5a0-109">To learn more about the Conditional Split transformation, see [Conditional Split Transformation](data-flow/transformations/conditional-split-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="5e5a0-110">选项</span><span class="sxs-lookup"><span data-stu-id="5e5a0-110">Options</span></span>  
 <span data-ttu-id="5e5a0-111">**Order**</span><span class="sxs-lookup"><span data-stu-id="5e5a0-111">**Order**</span></span>  
 <span data-ttu-id="5e5a0-112">选择行并使用右边的箭头键，可以更改计算表达式的顺序。</span><span class="sxs-lookup"><span data-stu-id="5e5a0-112">Select a row and use the arrow keys at right to change the order in which to evaluate expressions.</span></span>  
  
 <span data-ttu-id="5e5a0-113">**输出名称**</span><span class="sxs-lookup"><span data-stu-id="5e5a0-113">**Output Name**</span></span>  
 <span data-ttu-id="5e5a0-114">提供输出名称。</span><span class="sxs-lookup"><span data-stu-id="5e5a0-114">Provide an output name.</span></span> <span data-ttu-id="5e5a0-115">默认为带编号的名称示例列表，不过，您也可以任选一个唯一的描述性名称。</span><span class="sxs-lookup"><span data-stu-id="5e5a0-115">The default is a numbered list of cases; however, you can choose any unique, descriptive name.</span></span>  
  
 <span data-ttu-id="5e5a0-116">Condition</span><span class="sxs-lookup"><span data-stu-id="5e5a0-116">**Condition**</span></span>  
 <span data-ttu-id="5e5a0-117">键入表达式，或通过从可用的列、变量、函数和运算符的列表中拖动相应项来生成表达式。</span><span class="sxs-lookup"><span data-stu-id="5e5a0-117">Type an expression or build one by dragging from the list of available columns, variables, functions, and operators.</span></span>  
  
 <span data-ttu-id="5e5a0-118">此属性的值可以使用属性表达式来指定。</span><span class="sxs-lookup"><span data-stu-id="5e5a0-118">The value of this property can be specified by using a property expression.</span></span>  
  
 <span data-ttu-id="5e5a0-119">**相关主题：**  [Integration Services (SSIS) 表达式](expressions/integration-services-ssis-expressions.md)、[运算符（SSIS 表达式）](expressions/operators-ssis-expression.md)和[函数（SSIS 表达式）](expressions/functions-ssis-expression.md)</span><span class="sxs-lookup"><span data-stu-id="5e5a0-119">**Related topics:**  [Integration Services &#40;SSIS&#41; Expressions](expressions/integration-services-ssis-expressions.md), [Operators &#40;SSIS Expression&#41;](expressions/operators-ssis-expression.md), and [Functions &#40;SSIS Expression&#41;](expressions/functions-ssis-expression.md)</span></span>  
  
 <span data-ttu-id="5e5a0-120">**默认输出名称**</span><span class="sxs-lookup"><span data-stu-id="5e5a0-120">**Default output name**</span></span>  
 <span data-ttu-id="5e5a0-121">为默认输出键入名称，或使用默认名称。</span><span class="sxs-lookup"><span data-stu-id="5e5a0-121">Type a name for the default output, or use the default.</span></span>  
  
 <span data-ttu-id="5e5a0-122">**配置错误输出**</span><span class="sxs-lookup"><span data-stu-id="5e5a0-122">**Configure error output**</span></span>  
 <span data-ttu-id="5e5a0-123">使用 [配置错误输出](../../2014/integration-services/configure-error-output.md) 对话框指定处理错误的方式。</span><span class="sxs-lookup"><span data-stu-id="5e5a0-123">Specify how to handle errors by using the [Configure Error Output](../../2014/integration-services/configure-error-output.md) dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e5a0-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5e5a0-124">See Also</span></span>  
 <span data-ttu-id="5e5a0-125">[Integration Services 错误和消息引用](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="5e5a0-125">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 [<span data-ttu-id="5e5a0-126">使用有条件拆分转换拆分数据集</span><span class="sxs-lookup"><span data-stu-id="5e5a0-126">Split a Dataset by Using the Conditional Split Transformation</span></span>](data-flow/transformations/split-a-dataset-by-using-the-conditional-split-transformation.md)  
  
  
