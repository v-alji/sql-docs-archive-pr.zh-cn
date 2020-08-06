---
title: 表达式生成器 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.expressionbuilder.f1
helpviewer_keywords:
- Expression Builder dialog box
ms.assetid: 4717ce33-bd4e-44bc-81e0-002de075b4d1
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 812b0d744d415d5419d54176359ddcd5837dd206
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585913"
---
# <a name="expression-builder"></a><span data-ttu-id="eb2ff-102">表达式生成器</span><span class="sxs-lookup"><span data-stu-id="eb2ff-102">Expression Builder</span></span>
  <span data-ttu-id="eb2ff-103">可以使用“表达式生成器”  对话框创建和编辑属性表达式，或者编写使用图形用户界面设置变量值的表达式，此类表达式列出不同的变量并提供对 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 表达式语言包含的函数、类型转换和运算符的内置引用。</span><span class="sxs-lookup"><span data-stu-id="eb2ff-103">Use the **Expression Builder** dialog box to create and edit a property expression or write the expression that sets the value of a variable using a graphical user interface that lists variables and provides a built-in reference to the functions, type casts, and operators that the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] expression language includes.</span></span>  
  
 <span data-ttu-id="eb2ff-104">属性表达式是分配给某个属性的表达式。</span><span class="sxs-lookup"><span data-stu-id="eb2ff-104">A property expression is an expression that is assigned to a property.</span></span> <span data-ttu-id="eb2ff-105">在对此类表达式求值时，属性将动态更新，以使用表达式的计算结果。</span><span class="sxs-lookup"><span data-stu-id="eb2ff-105">When the expression is evaluated, the property is dynamically updated to use the evaluation result of the expression.</span></span> <span data-ttu-id="eb2ff-106">同样，在变量中使用表达式时，也可以使用该表达式的计算结果来更新该变量值。</span><span class="sxs-lookup"><span data-stu-id="eb2ff-106">Likewise, an expression that is used in a variable enables the variable value to be updated with the evaluation result of the expression.</span></span>  
  
 <span data-ttu-id="eb2ff-107">使用表达式的方法很多：</span><span class="sxs-lookup"><span data-stu-id="eb2ff-107">There are many ways to use expressions:</span></span>  
  
-   <span data-ttu-id="eb2ff-108">**任务** ：通过插入存储在变量中的电子邮件地址来更新发送邮件任务使用的“收件人”行；或是将字符串（如“Sales for:”）与 GETDATE 函数返回的当前日期连接在一起以更新“主题”行。</span><span class="sxs-lookup"><span data-stu-id="eb2ff-108">**Tasks** Update the To line that a Send Mail task uses by inserting an e-mail address that is stored in a variable; or update the Subject line by concatenating a string such as "Sales for: " and the current date returned by the GETDATE function.</span></span>  
  
-   <span data-ttu-id="eb2ff-109">**变量** ：使用 `DATEPART("mm",GETDATE())`等表达式将变量值设置为当前月；或通过使用表达式 `"Today's date is " + (DT_WSTR,30)(GETDATE())`连接字符串文字与当前日期来设置字符串的值。</span><span class="sxs-lookup"><span data-stu-id="eb2ff-109">**Variables** Set the value of a variable to the current month by using an expression like `DATEPART("mm",GETDATE())`; or set the value of a string by concatenating the string literal and the current date by using the expression `"Today's date is " + (DT_WSTR,30)(GETDATE())`.</span></span>  
  
-   <span data-ttu-id="eb2ff-110">**连接管理器** ：通过使用包含不同代码页标识符的变量来设置平面文件连接管理器的代码页；或通过在表达式中输入正整数（如 3）来指定在数据文件中跳过的行数。</span><span class="sxs-lookup"><span data-stu-id="eb2ff-110">**Connection Managers** Set the code page of a Flat File connection manager by using a variable that contains a different code page identifier; or specify the number of rows in the data file to skip by entering a positive integer like 3 in the expression.</span></span>  
  
 <span data-ttu-id="eb2ff-111">了解有关属性表达式和编写表达式的详细信息，请参阅[在包中使用属性表达式](use-property-expressions-in-packages.md)和 [Integration Services (SSIS) 表达式](integration-services-ssis-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="eb2ff-111">To learn more about property expressions and writing expressions, see [Use Property Expressions in Packages](use-property-expressions-in-packages.md) and [Integration Services &#40;SSIS&#41; Expressions](integration-services-ssis-expressions.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="eb2ff-112">选项</span><span class="sxs-lookup"><span data-stu-id="eb2ff-112">Options</span></span>  
  
|<span data-ttu-id="eb2ff-113">术语</span><span class="sxs-lookup"><span data-stu-id="eb2ff-113">Term</span></span>|<span data-ttu-id="eb2ff-114">定义</span><span class="sxs-lookup"><span data-stu-id="eb2ff-114">Definition</span></span>|  
|----------|----------------|  
|<span data-ttu-id="eb2ff-115">**变量**</span><span class="sxs-lookup"><span data-stu-id="eb2ff-115">**Variables**</span></span>|<span data-ttu-id="eb2ff-116">展开 **“变量”** 文件夹，再将变量拖至 **“表达式”** 框。</span><span class="sxs-lookup"><span data-stu-id="eb2ff-116">Expand the **Variables** folder and drag variables to the **Expression** box.</span></span>|  
|<span data-ttu-id="eb2ff-117">**数学函数**</span><span class="sxs-lookup"><span data-stu-id="eb2ff-117">**Mathematical Functions**</span></span><br /><br /> <span data-ttu-id="eb2ff-118">**字符串函数**</span><span class="sxs-lookup"><span data-stu-id="eb2ff-118">**String Functions**</span></span><br /><br /> <span data-ttu-id="eb2ff-119">**日期/时间函数**</span><span class="sxs-lookup"><span data-stu-id="eb2ff-119">**Date/Time Functions**</span></span><br /><br /> <span data-ttu-id="eb2ff-120">**NULL 函数**</span><span class="sxs-lookup"><span data-stu-id="eb2ff-120">**NULL Functions**</span></span><br /><br /> <span data-ttu-id="eb2ff-121">**类型转换**</span><span class="sxs-lookup"><span data-stu-id="eb2ff-121">**Type Casts**</span></span><br /><br /> <span data-ttu-id="eb2ff-122">**运算符**</span><span class="sxs-lookup"><span data-stu-id="eb2ff-122">**Operators**</span></span>|<span data-ttu-id="eb2ff-123">展开相应的文件夹，再将函数、类型转换和运算符拖至 **“表达式”** 框。</span><span class="sxs-lookup"><span data-stu-id="eb2ff-123">Expand the folders and drag functions, type casts, and operators to the **Expression** box.</span></span>|  
|<span data-ttu-id="eb2ff-124">**表达式**</span><span class="sxs-lookup"><span data-stu-id="eb2ff-124">**Expression**</span></span>|<span data-ttu-id="eb2ff-125">编辑或键入表达式。</span><span class="sxs-lookup"><span data-stu-id="eb2ff-125">Edit or type an expression.\`</span></span>|  
|<span data-ttu-id="eb2ff-126">**计算结果值**</span><span class="sxs-lookup"><span data-stu-id="eb2ff-126">**Evaluated value**</span></span>|<span data-ttu-id="eb2ff-127">列出表达式的计算结果。</span><span class="sxs-lookup"><span data-stu-id="eb2ff-127">Lists the evaluation result of the expression.</span></span>|  
|<span data-ttu-id="eb2ff-128">**计算表达式**</span><span class="sxs-lookup"><span data-stu-id="eb2ff-128">**Evaluate Expression**</span></span>|<span data-ttu-id="eb2ff-129">单击 **“计算表达式”** 可以查看表达式的计算结果。</span><span class="sxs-lookup"><span data-stu-id="eb2ff-129">Click **Evaluate Expression** to view the evaluation result of the expression.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="eb2ff-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="eb2ff-130">See Also</span></span>  
 <span data-ttu-id="eb2ff-131">[“表达式”页](expressions-page.md) </span><span class="sxs-lookup"><span data-stu-id="eb2ff-131">[Expressions Page](expressions-page.md) </span></span>  
 <span data-ttu-id="eb2ff-132">[属性表达式编辑器](property-expressions-editor.md) </span><span class="sxs-lookup"><span data-stu-id="eb2ff-132">[Property Expressions Editor](property-expressions-editor.md) </span></span>  
 <span data-ttu-id="eb2ff-133">[Integration Services (SSIS) 变量](../integration-services-ssis-variables.md) </span><span class="sxs-lookup"><span data-stu-id="eb2ff-133">[Integration Services &#40;SSIS&#41; Variables](../integration-services-ssis-variables.md) </span></span>  
 [<span data-ttu-id="eb2ff-134">系统变量</span><span class="sxs-lookup"><span data-stu-id="eb2ff-134">System Variables</span></span>](../system-variables.md)  
  
  
