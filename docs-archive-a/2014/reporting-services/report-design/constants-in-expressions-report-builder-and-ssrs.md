---
title: 表达式中的常量（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: b8ae650b-0f46-4848-b62b-15f8a40751b8
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d95005a04482cb03d3bb3860aea695c7e7969255
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580639"
---
# <a name="constants-in-expressions-report-builder-and-ssrs"></a><span data-ttu-id="a18d7-102">表达式中的常量（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="a18d7-102">Constants in Expressions (Report Builder and SSRS)</span></span>
  <span data-ttu-id="a18d7-103">常量由文字文本或预定义文本构成。</span><span class="sxs-lookup"><span data-stu-id="a18d7-103">A constant consists of literal text or predefined text.</span></span> <span data-ttu-id="a18d7-104">报表处理器具有对预定义常量的访问权限，所以当表达式中包含常量时，这些常量所代表的值会在计算之前进行替换。</span><span class="sxs-lookup"><span data-stu-id="a18d7-104">The report processor has access to predefined constants so that when you include them in an expression, the values they represent are substituted in the expression before it is evaluated.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="literal-text"></a><span data-ttu-id="a18d7-105">文字文本</span><span class="sxs-lookup"><span data-stu-id="a18d7-105">Literal Text</span></span>  
 <span data-ttu-id="a18d7-106">在表达式中，文字文本是用双引号括起来的文本。</span><span class="sxs-lookup"><span data-stu-id="a18d7-106">In an expression, literal text is text that is in double quotation marks.</span></span> <span data-ttu-id="a18d7-107">如果文本不是表达式的一部分，也可以在文本框中直接键入文本，而不使用双引号。</span><span class="sxs-lookup"><span data-stu-id="a18d7-107">You can also type text directly into a text box without double quotation marks if it is not part of an expression.</span></span> <span data-ttu-id="a18d7-108">如果文本框值不以等号 (=) 开头，则会将该文本视为文字文本。</span><span class="sxs-lookup"><span data-stu-id="a18d7-108">If the text box value does not begin with an equal sign (=), the text is treated as literal text.</span></span> <span data-ttu-id="a18d7-109">下表显示几个表达式中的文字文本示例。</span><span class="sxs-lookup"><span data-stu-id="a18d7-109">The following table shows several examples of literal text in an expression.</span></span>  
  
|<span data-ttu-id="a18d7-110">一直</span><span class="sxs-lookup"><span data-stu-id="a18d7-110">Constant</span></span>|<span data-ttu-id="a18d7-111">显示文本</span><span class="sxs-lookup"><span data-stu-id="a18d7-111">Display text</span></span>|<span data-ttu-id="a18d7-112">表达式文本</span><span class="sxs-lookup"><span data-stu-id="a18d7-112">Expression text</span></span>|  
|--------------|------------------|---------------------|  
|<span data-ttu-id="a18d7-113">Report run at:</span><span class="sxs-lookup"><span data-stu-id="a18d7-113">Report run at:</span></span>|<\<Expr>>|`="Report run at: " & Globals!ExecutionTime`|  
|<span data-ttu-id="a18d7-114">Adventure Works Cycles</span><span class="sxs-lookup"><span data-stu-id="a18d7-114">Adventure Works Cycles</span></span>|<span data-ttu-id="a18d7-115">Adventure Works Cycles</span><span class="sxs-lookup"><span data-stu-id="a18d7-115">Adventure Works Cycles</span></span>|<span data-ttu-id="a18d7-116">Adventure Works Cycles</span><span class="sxs-lookup"><span data-stu-id="a18d7-116">Adventure Works Cycles</span></span>|  
|<span data-ttu-id="a18d7-117">[Bracketed display text]</span><span class="sxs-lookup"><span data-stu-id="a18d7-117">[Bracketed display text]</span></span>|<span data-ttu-id="a18d7-118">\\[Bracketed display text\\]</span><span class="sxs-lookup"><span data-stu-id="a18d7-118">\\[Bracketed display text\\]</span></span>|<span data-ttu-id="a18d7-119">[Bracketed display text]</span><span class="sxs-lookup"><span data-stu-id="a18d7-119">[Bracketed display text]</span></span>|  
  
## <a name="rdl-constants"></a><span data-ttu-id="a18d7-120">RDL 常量</span><span class="sxs-lookup"><span data-stu-id="a18d7-120">RDL Constants</span></span>  
 <span data-ttu-id="a18d7-121">您可以在表达式中使用以报表定义语言 (RDL) 定义的常量。</span><span class="sxs-lookup"><span data-stu-id="a18d7-121">You can use constants defined in Report Definition Language (RDL) in an expression.</span></span> <span data-ttu-id="a18d7-122">在 **“表达式”** 对话框中，当创建只接受某些有效值（也称为枚举类型）的报表属性的表达式时，显示常量。</span><span class="sxs-lookup"><span data-stu-id="a18d7-122">In the **Expression** dialog box, constants appear when you create an expression for a report property that only accepts certain valid values, also known as enumerated types.</span></span> <span data-ttu-id="a18d7-123">下表显示两个示例。</span><span class="sxs-lookup"><span data-stu-id="a18d7-123">The following table shows two examples.</span></span>  
  
|<span data-ttu-id="a18d7-124">属性</span><span class="sxs-lookup"><span data-stu-id="a18d7-124">Property</span></span>|<span data-ttu-id="a18d7-125">说明</span><span class="sxs-lookup"><span data-stu-id="a18d7-125">Description</span></span>|<span data-ttu-id="a18d7-126">值</span><span class="sxs-lookup"><span data-stu-id="a18d7-126">Values</span></span>|  
|--------------|-----------------|------------|  
|<span data-ttu-id="a18d7-127">TextAlign</span><span class="sxs-lookup"><span data-stu-id="a18d7-127">TextAlign</span></span>|<span data-ttu-id="a18d7-128">文本框中对齐文本的有效值。</span><span class="sxs-lookup"><span data-stu-id="a18d7-128">Valid values for aligning text in a text box.</span></span>|<span data-ttu-id="a18d7-129">General、Left、Center、Right</span><span class="sxs-lookup"><span data-stu-id="a18d7-129">General, Left, Center, Right</span></span>|  
|<span data-ttu-id="a18d7-130">BorderStyle</span><span class="sxs-lookup"><span data-stu-id="a18d7-130">BorderStyle</span></span>|<span data-ttu-id="a18d7-131">添加到报表的行的有效值。</span><span class="sxs-lookup"><span data-stu-id="a18d7-131">Valid values for a line added to a report.</span></span>|<span data-ttu-id="a18d7-132">Default、None、Dotted、Dashed、Solid、Double、DashDot、DashDotdot</span><span class="sxs-lookup"><span data-stu-id="a18d7-132">Default, None, Dotted, Dashed, Solid, Double, DashDot, DashDotdot</span></span>|  
  
## <a name="visual-basic-constants"></a><span data-ttu-id="a18d7-133">Visual Basic 常量</span><span class="sxs-lookup"><span data-stu-id="a18d7-133">Visual Basic Constants</span></span>  
 <span data-ttu-id="a18d7-134">您可以在表达式中使用在 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 运行时库定义的常量。</span><span class="sxs-lookup"><span data-stu-id="a18d7-134">You can use constants defined in the [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] run-time library in an expression.</span></span> <span data-ttu-id="a18d7-135">例如，可以使用常量 `DateInterval.Day`。</span><span class="sxs-lookup"><span data-stu-id="a18d7-135">For example, you can use the constant `DateInterval.Day`.</span></span> <span data-ttu-id="a18d7-136">对于日期 2008 年 1 月 10 日，以下表达式会返回数字 10：</span><span class="sxs-lookup"><span data-stu-id="a18d7-136">The following expression for the date January 10, 2008 returns the number 10:</span></span>  
  
 `=DatePart("d",Globals!ExecutionTime)`  
  
## <a name="clr-constants"></a><span data-ttu-id="a18d7-137">CLR 常量</span><span class="sxs-lookup"><span data-stu-id="a18d7-137">CLR Constants</span></span>  
 <span data-ttu-id="a18d7-138">可以在表达式中使用在 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 公共语言运行时 (CLR) 类中定义的常量。</span><span class="sxs-lookup"><span data-stu-id="a18d7-138">You can use constants defined in [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] common language run-time (CLR) classes in an expression.</span></span> <span data-ttu-id="a18d7-139">下表显示了系统定义的颜色的一个示例。</span><span class="sxs-lookup"><span data-stu-id="a18d7-139">The following table shows an example of a system-defined color.</span></span>  
  
|<span data-ttu-id="a18d7-140">返回的常量</span><span class="sxs-lookup"><span data-stu-id="a18d7-140">Constant</span></span>|<span data-ttu-id="a18d7-141">描述</span><span class="sxs-lookup"><span data-stu-id="a18d7-141">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="a18d7-142">MistyRose</span><span class="sxs-lookup"><span data-stu-id="a18d7-142">MistyRose</span></span>|<span data-ttu-id="a18d7-143">创建基于背景色的报表属性的表达式时，可以按名称指定颜色。</span><span class="sxs-lookup"><span data-stu-id="a18d7-143">When you create an expression for a report property that is based on background color, you can specify a color by name.</span></span> <span data-ttu-id="a18d7-144">**“表达式”** 对话框中列出了有效名称。</span><span class="sxs-lookup"><span data-stu-id="a18d7-144">Valid names are listed in the **Expression** dialog box.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a18d7-145">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a18d7-145">See Also</span></span>  
 <span data-ttu-id="a18d7-146">["表达式" 对话框](../expression-dialog-box.md) </span><span class="sxs-lookup"><span data-stu-id="a18d7-146">[Expression Dialog Box](../expression-dialog-box.md) </span></span>  
 <span data-ttu-id="a18d7-147">[表达式（报表生成器和 SSRS）](expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="a18d7-147">[Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="a18d7-148">[表达式示例（报表生成器和 SSRS）](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="a18d7-148">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="a18d7-149">[表达式中的数据类型 &#40;报表生成器和 SSRS&#41;](data-types-in-expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="a18d7-149">[Data Types in Expressions &#40;Report Builder and SSRS&#41;](data-types-in-expressions-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="a18d7-150">“表达式”对话框（报表生成器）</span><span class="sxs-lookup"><span data-stu-id="a18d7-150">Expression Dialog Box &#40;Report Builder&#41;</span></span>](../expression-dialog-box-report-builder.md)  
  
  
