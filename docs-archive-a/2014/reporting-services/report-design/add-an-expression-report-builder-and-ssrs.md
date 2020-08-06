---
title: 添加表达式（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: a60ee091-b4ed-41e1-9b6a-032c316cd03f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 16f414bfad47ae92681de50eb576a6ac2cb3f5fe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687456"
---
# <a name="add-an-expression-report-builder-and-ssrs"></a><span data-ttu-id="c5b4a-102">添加表达式（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="c5b4a-102">Add an Expression (Report Builder and SSRS)</span></span>
  <span data-ttu-id="c5b4a-103">可在整个报表中使用表达式来定义报表项属性、筛选器、组、排序顺序、连接字符串和参数值。</span><span class="sxs-lookup"><span data-stu-id="c5b4a-103">Expressions are used throughout a report for defining report item properties, filters, groups, sort order, connection strings, and parameter values.</span></span> <span data-ttu-id="c5b4a-104">表达式通常以等号 (=) 开头，以 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 语言编写。</span><span class="sxs-lookup"><span data-stu-id="c5b4a-104">Expressions begin with an equal sign (=) and are written in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)].</span></span> <span data-ttu-id="c5b4a-105">它们由报表处理器在运行时进行计算，报表处理器会将计算结果和报表布局元素相结合。</span><span class="sxs-lookup"><span data-stu-id="c5b4a-105">They are evaluated at run time by the report processor, which combines the evaluation result with report layout elements.</span></span>  
  
 <span data-ttu-id="c5b4a-106">表达式可以是简单的，也可以是复杂的。</span><span class="sxs-lookup"><span data-stu-id="c5b4a-106">Expressions can be simple or complex.</span></span> <span data-ttu-id="c5b4a-107">简单表达式引用内置集合中的单个项。</span><span class="sxs-lookup"><span data-stu-id="c5b4a-107">Simple expression refer to a single item in a built-in collection.</span></span> <span data-ttu-id="c5b4a-108">复杂表达式可以包括常量、运算符、全局集合项和函数调用。</span><span class="sxs-lookup"><span data-stu-id="c5b4a-108">Complex expressions can contain constants, operators, global collection items, and function calls.</span></span> <span data-ttu-id="c5b4a-109">有关详细信息，请参阅[表达式（报表生成器和 SSRS）](expressions-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="c5b4a-109">For more information, see [Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-an-expression-to-a-text-box"></a><span data-ttu-id="c5b4a-110">向文本框添加表达式</span><span class="sxs-lookup"><span data-stu-id="c5b4a-110">To add an expression to a text box</span></span>  
  
-   <span data-ttu-id="c5b4a-111">在 **“设计”** 视图中，在设计图面上单击要向其添加表达式的文本框。</span><span class="sxs-lookup"><span data-stu-id="c5b4a-111">In **Design** view, click the text box on the design surface to which you want to add an expression.</span></span>  
  
    -   <span data-ttu-id="c5b4a-112">对于简单表达式，在文本框中键入该表达式的显示文本。</span><span class="sxs-lookup"><span data-stu-id="c5b4a-112">For a simple expression, type the display text for the expression in the text box.</span></span> <span data-ttu-id="c5b4a-113">例如，对于数据集字段 Sales，键入 `[Sales]`。</span><span class="sxs-lookup"><span data-stu-id="c5b4a-113">For example, for the dataset field Sales, type `[Sales]`.</span></span>  
  
    -   <span data-ttu-id="c5b4a-114">对于复杂表达式，右键单击文本框，然后选择 **“表达式”** 。</span><span class="sxs-lookup"><span data-stu-id="c5b4a-114">For a complex expression, right-click the text box, and select **Expression**.</span></span> <span data-ttu-id="c5b4a-115">此时将打开 **“表达式”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="c5b4a-115">The **Expression** dialog box opens.</span></span> <span data-ttu-id="c5b4a-116">在“表达式”窗格中，在等号“=”后键入或交互方式创建表达式，然后单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="c5b4a-116">Type or interactively create your expression after the '=' in the expression pane, and then click OK.</span></span>  
  
         <span data-ttu-id="c5b4a-117">该表达式将在设计图面上显示为 `<<Expr>>`。</span><span class="sxs-lookup"><span data-stu-id="c5b4a-117">The expression appears on the design surface as `<<Expr>>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5b4a-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c5b4a-118">See Also</span></span>  
 <span data-ttu-id="c5b4a-119">[设置文本和占位符的格式（报表生成器和 SSRS）](formatting-text-and-placeholders-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="c5b4a-119">[Formatting Text and Placeholders &#40;Report Builder and SSRS&#41;](formatting-text-and-placeholders-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="c5b4a-120">[文本框（报表生成器和 SSRS）](text-boxes-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="c5b4a-120">[Text Boxes &#40;Report Builder and SSRS&#41;](text-boxes-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="c5b4a-121">[在报表中使用表达式（报表生成器和 SSRS）](expression-uses-in-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="c5b4a-121">[Expression Uses in Reports &#40;Report Builder and SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="c5b4a-122">[筛选器公式示例（报表生成器和 SSRS）](filter-equation-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="c5b4a-122">[Filter Equation Examples &#40;Report Builder and SSRS&#41;](filter-equation-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="c5b4a-123">[组表达式示例（报表生成器和 SSRS）](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="c5b4a-123">[Group Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="c5b4a-124">[“表达式”对话框（报表生成器）](../expression-dialog-box-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="c5b4a-124">[Expression Dialog Box &#40;Report Builder&#41;](../expression-dialog-box-report-builder.md) </span></span>  
 <span data-ttu-id="c5b4a-125">[表达式示例（报表生成器和 SSRS）](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="c5b4a-125">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="c5b4a-126">向报表添加代码 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="c5b4a-126">Add Code to a Report &#40;SSRS&#41;</span></span>](add-code-to-a-report-ssrs.md)  
  
  
