---
title: "\"报表属性\" 对话框-\"引用\" |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10530"
- sql12.rtp.rptdesigner.reportproperties.references.f1
ms.assetid: 4639d368-9918-4bb1-9953-7a724ca78dea
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 4b28ea0865d37bdc56054d6b23dc8c82d9279b08
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690356"
---
# <a name="report-properties-dialog-box-references"></a><span data-ttu-id="84a9e-102">“报表属性”对话框 ->“引用”</span><span class="sxs-lookup"><span data-stu-id="84a9e-102">Report Properties Dialog Box, References</span></span>
  <span data-ttu-id="84a9e-103">选择 **“报表属性”** 对话框中的 **“引用”** 可以添加或删除对报表定义中的表达式所使用的自定义程序集或其他外部程序集以及自定义类实例的引用。</span><span class="sxs-lookup"><span data-stu-id="84a9e-103">Select **References** on the **Report Properties** dialog box to add or remove references to custom or other external assemblies and custom class instances that are used by expressions in the report definition.</span></span>  
  
## <a name="options"></a><span data-ttu-id="84a9e-104">选项</span><span class="sxs-lookup"><span data-stu-id="84a9e-104">Options</span></span>  
 <span data-ttu-id="84a9e-105">**添加或删除程序集**</span><span class="sxs-lookup"><span data-stu-id="84a9e-105">**Add or remove assemblies**</span></span>  
 <span data-ttu-id="84a9e-106">列出报表引用的程序集。</span><span class="sxs-lookup"><span data-stu-id="84a9e-106">Lists the assemblies that the report references.</span></span> <span data-ttu-id="84a9e-107">该程序集在安装报表设计工具的计算机上以及报表服务器上必须可用。</span><span class="sxs-lookup"><span data-stu-id="84a9e-107">The assembly must be available on the computer on which the tool you are using to design the report is installed and on the report server.</span></span> <span data-ttu-id="84a9e-108">引用的名称必须与 **\<CodeModule>** 报表定义语言 ( .rdl) 文件中标记的内容完全匹配。</span><span class="sxs-lookup"><span data-stu-id="84a9e-108">The name of the reference must match the contents of **\<CodeModule>** tags in the Report Definition Language (.rdl) file exactly.</span></span>  
  
 <span data-ttu-id="84a9e-109">**添加**</span><span class="sxs-lookup"><span data-stu-id="84a9e-109">**Add**</span></span>  
 <span data-ttu-id="84a9e-110">单击该选项可以添加程序集。</span><span class="sxs-lookup"><span data-stu-id="84a9e-110">Click to add an assembly.</span></span> <span data-ttu-id="84a9e-111">单击省略号 ( ") " 按钮以打开 "**打开**" 对话框，并选择完成报表处理和表达式计算所需的程序集。</span><span class="sxs-lookup"><span data-stu-id="84a9e-111">Click the ellipsis (...) button to open the **Open** dialog box and select the assemblies necessary to complete report processing and expression evaluation.</span></span>  
  
 <span data-ttu-id="84a9e-112">**删除**</span><span class="sxs-lookup"><span data-stu-id="84a9e-112">**Delete**</span></span>  
 <span data-ttu-id="84a9e-113">若要从列表中删除程序集引用，请选择程序集名并单击“删除”\*\*\*\* 按钮。</span><span class="sxs-lookup"><span data-stu-id="84a9e-113">To remove an assembly reference from the list, select the assembly name and click the **Remove** button.</span></span>  
  
 <span data-ttu-id="84a9e-114">**添加或删除类**</span><span class="sxs-lookup"><span data-stu-id="84a9e-114">**Add or remove classes**</span></span>  
 <span data-ttu-id="84a9e-115">列出报表使用的类实例。</span><span class="sxs-lookup"><span data-stu-id="84a9e-115">Lists the class instances that are used by the report.</span></span> <span data-ttu-id="84a9e-116">该类列表仅适用于基于实例的成员，而不适用于静态成员。</span><span class="sxs-lookup"><span data-stu-id="84a9e-116">The class list is used only by instance-based members, not static members.</span></span>  
  
 <span data-ttu-id="84a9e-117">**添加**</span><span class="sxs-lookup"><span data-stu-id="84a9e-117">**Add**</span></span>  
 <span data-ttu-id="84a9e-118">单击该选项可以添加类引用。</span><span class="sxs-lookup"><span data-stu-id="84a9e-118">Click to add a class reference.</span></span> <span data-ttu-id="84a9e-119">单击省略号 ( ") " 按钮以打开 "**打开**" 对话框，并选择完成报表处理和表达式计算所需的类。</span><span class="sxs-lookup"><span data-stu-id="84a9e-119">Click the ellipsis (...) button to open the **Open** dialog box and select the classes necessary to complete report processing and expression evaluation.</span></span>  
  
 <span data-ttu-id="84a9e-120">**删除**</span><span class="sxs-lookup"><span data-stu-id="84a9e-120">**Delete**</span></span>  
 <span data-ttu-id="84a9e-121">若要删除类实例，请选中该实例并单击“删除”\*\*\*\* 按钮。</span><span class="sxs-lookup"><span data-stu-id="84a9e-121">To delete the class instance, select it and click the **Remove** button.</span></span>  
  
 <span data-ttu-id="84a9e-122">**Up**</span><span class="sxs-lookup"><span data-stu-id="84a9e-122">**Up**</span></span>  
 <span data-ttu-id="84a9e-123">可为有依赖关系的类在列表中上移该引用。</span><span class="sxs-lookup"><span data-stu-id="84a9e-123">For classes that have dependencies, you can move this reference higher in the list.</span></span>  
  
 <span data-ttu-id="84a9e-124">**向下**</span><span class="sxs-lookup"><span data-stu-id="84a9e-124">**Down**</span></span>  
 <span data-ttu-id="84a9e-125">可为有依赖关系的类在列表中下移该引用。</span><span class="sxs-lookup"><span data-stu-id="84a9e-125">For classes that have dependencies, you can move this reference lower in the list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84a9e-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="84a9e-126">See Also</span></span>  
 <span data-ttu-id="84a9e-127">[报表设计器的表达式中的自定义代码和程序集引用 (SSRS)](report-design/custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="84a9e-127">[Custom Code and Assembly References in Expressions in Report Designer &#40;SSRS&#41;](report-design/custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md) </span></span>  
 <span data-ttu-id="84a9e-128">[报表和组变量集合引用 &#40;报表生成器和 SSRS&#41;](report-design/built-in-collections-report-and-group-variables-references-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="84a9e-128">[Report and Group Variables Collections References &#40;Report Builder and SSRS&#41;](report-design/built-in-collections-report-and-group-variables-references-report-builder.md) </span></span>  
 [<span data-ttu-id="84a9e-129">表达式示例（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="84a9e-129">Expression Examples &#40;Report Builder and SSRS&#41;</span></span>](report-design/expression-examples-report-builder-and-ssrs.md)  
  
  
