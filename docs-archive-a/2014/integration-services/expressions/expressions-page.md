---
title: “表达式”页 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.expressionspage.f1
helpviewer_keywords:
- Expressions Page dialog box
ms.assetid: c9016ec6-11c1-4ebd-b2a7-0fa6631fd9e4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ba4e73ea495456e8f9e452108ab09106a65543ae
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585914"
---
# <a name="expressions-page"></a><span data-ttu-id="66c93-102">“表达式”页</span><span class="sxs-lookup"><span data-stu-id="66c93-102">Expressions Page</span></span>
  <span data-ttu-id="66c93-103">可以使用 **“表达式”** 页编辑属性表达式以及访问 **“属性表达式编辑器”** 和 **“属性表达式生成器”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="66c93-103">Use the **Expressions** page to edit property expressions and to access the **Property Expressions Editor** and **Property Expression Builder** dialog boxes.</span></span>  
  
 <span data-ttu-id="66c93-104">属性表达式将在包运行时更新属性的值。</span><span class="sxs-lookup"><span data-stu-id="66c93-104">Property expressions update the values of properties when the package is run.</span></span> <span data-ttu-id="66c93-105">包、任务、容器、连接管理器以及一些数据流组件的属性可以使用属性表达式。</span><span class="sxs-lookup"><span data-stu-id="66c93-105">Property expressions can be used with the properties of packages, tasks, containers, connection managers, as well as some data flow components.</span></span> <span data-ttu-id="66c93-106">系统将对表达式求值，并且其结果将用来代替您在配置包和包对象时所设的属性的值。</span><span class="sxs-lookup"><span data-stu-id="66c93-106">The expressions are evaluated and their results are used instead of the values to which you set the properties when you configured the package and package objects.</span></span> <span data-ttu-id="66c93-107">表达式可以包含表达式语言所提供的变量、函数和运算符。</span><span class="sxs-lookup"><span data-stu-id="66c93-107">The expressions can include variables and the functions and operators that the expression language provides.</span></span> <span data-ttu-id="66c93-108">例如，可将一个包含“Weather forecast for”字符串的变量的值和 GETDATE() 函数的返回结果连接在一起形成字符串“Weather forecast for 4/5/2006”，从而为“发送邮件”任务生成主题行。</span><span class="sxs-lookup"><span data-stu-id="66c93-108">For example, you can generate the subject line for the Send Mail task by concatenating the value of a variable that contains the string "Weather forecast for " and the return results of the GETDATE() function to make the string "Weather forecast for 4/5/2006".</span></span>  
  
 <span data-ttu-id="66c93-109">了解有关编写表达式和使用属性表达式的详细信息，请参阅 [Integration Services (SSIS) 表达式](integration-services-ssis-expressions.md) 和 [在包中使用属性表达式](use-property-expressions-in-packages.md)。</span><span class="sxs-lookup"><span data-stu-id="66c93-109">To learn more about writing expressions and using property expressions, see [Integration Services &#40;SSIS&#41; Expressions](integration-services-ssis-expressions.md) and [Use Property Expressions in Packages](use-property-expressions-in-packages.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="66c93-110">选项</span><span class="sxs-lookup"><span data-stu-id="66c93-110">Options</span></span>  
 <span data-ttu-id="66c93-111">**表达式 (...)**</span><span class="sxs-lookup"><span data-stu-id="66c93-111">**Expressions (...)**</span></span>  
 <span data-ttu-id="66c93-112">单击省略号可以打开 **“属性表达式编辑器”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="66c93-112">Click the ellipsis to open the **Property Expressions Editor** dialog box.</span></span> <span data-ttu-id="66c93-113">有关详细信息，请参阅 [Property Expressions Editor](property-expressions-editor.md)。</span><span class="sxs-lookup"><span data-stu-id="66c93-113">For more information, see [Property Expressions Editor](property-expressions-editor.md).</span></span>  
  
 **\<property name>**  
 <span data-ttu-id="66c93-114">单击省略号可以打开 **“表达式生成器”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="66c93-114">Click the ellipsis to open the **Expression Builder** dialog box.</span></span> <span data-ttu-id="66c93-115">有关详细信息，请参阅 [Expression Builder](expression-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="66c93-115">For more information, see [Expression Builder](expression-builder.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66c93-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="66c93-116">See Also</span></span>  
 <span data-ttu-id="66c93-117">[Integration Services (SSIS) 变量](../integration-services-ssis-variables.md) </span><span class="sxs-lookup"><span data-stu-id="66c93-117">[Integration Services &#40;SSIS&#41; Variables](../integration-services-ssis-variables.md) </span></span>  
 <span data-ttu-id="66c93-118">[系统变量](../system-variables.md) </span><span class="sxs-lookup"><span data-stu-id="66c93-118">[System Variables](../system-variables.md) </span></span>  
 [<span data-ttu-id="66c93-119">Integration Services (SSIS) 表达式</span><span class="sxs-lookup"><span data-stu-id="66c93-119">Integration Services &#40;SSIS&#41; Expressions</span></span>](integration-services-ssis-expressions.md)  
  
  
