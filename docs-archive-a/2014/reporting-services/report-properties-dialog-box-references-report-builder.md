---
title: "\"报表属性\" 对话框-\"引用 (报表生成器) |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10082"
ms.assetid: 3414c857-8ea6-4fc4-a6d5-b4883c039efa
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2c28e9053a1c13f8d0e0b7b44f3b1a037976c318
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690359"
---
# <a name="report-properties-dialog-box-references-report-builder"></a><span data-ttu-id="12668-102">“报表属性”对话框 -&gt;“引用”（报表生成器）</span><span class="sxs-lookup"><span data-stu-id="12668-102">Report Properties Dialog Box, References (Report Builder)</span></span>
  <span data-ttu-id="12668-103">选择 **“报表属性”** 对话框中的 **“引用”** 可以添加或删除对报表定义中的表达式所使用的自定义程序集或其他外部程序集以及自定义类实例的引用。</span><span class="sxs-lookup"><span data-stu-id="12668-103">Select **References** on the **Report Properties** dialog box to add or remove references to custom or other external assemblies and custom class instances that are used by expressions in the report definition.</span></span> <span data-ttu-id="12668-104">在报表生成器本地模式中，不支持自定义程序集。</span><span class="sxs-lookup"><span data-stu-id="12668-104">Custom assemblies are not supported in local mode in Report Builder.</span></span> <span data-ttu-id="12668-105">若要创作使用自定义程序集的报表，请使用中的报表设计器 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="12668-105">To author reports that use custom assemblies, use Report Designer in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
## <a name="options"></a><span data-ttu-id="12668-106">选项</span><span class="sxs-lookup"><span data-stu-id="12668-106">Options</span></span>  
 <span data-ttu-id="12668-107">**添加或删除程序集**</span><span class="sxs-lookup"><span data-stu-id="12668-107">**Add or remove assemblies**</span></span>  
 <span data-ttu-id="12668-108">列出报表引用的程序集。</span><span class="sxs-lookup"><span data-stu-id="12668-108">Lists the assemblies that the report references.</span></span> <span data-ttu-id="12668-109">该程序集在安装报表设计工具的计算机上以及报表服务器上必须可用。</span><span class="sxs-lookup"><span data-stu-id="12668-109">The assembly must be available on the computer on which the tool you are using to design the report is installed and on the report server.</span></span> <span data-ttu-id="12668-110">引用的名称必须与 **\<CodeModule>** 报表定义语言 ( .rdl) 文件中标记的内容完全匹配。</span><span class="sxs-lookup"><span data-stu-id="12668-110">The name of the reference must match the contents of **\<CodeModule>** tags in the Report Definition Language (.rdl) file exactly.</span></span>  
  
 <span data-ttu-id="12668-111">**添加**</span><span class="sxs-lookup"><span data-stu-id="12668-111">**Add**</span></span>  
 <span data-ttu-id="12668-112">单击该选项可以添加程序集。</span><span class="sxs-lookup"><span data-stu-id="12668-112">Click to add an assembly.</span></span> <span data-ttu-id="12668-113">单击省略号 ( ") " 按钮以打开 "**打开**" 对话框，并选择完成报表处理和表达式计算所需的程序集。</span><span class="sxs-lookup"><span data-stu-id="12668-113">Click the ellipsis (...) button to open the **Open** dialog box and select the assemblies necessary to complete report processing and expression evaluation.</span></span>  
  
 <span data-ttu-id="12668-114">**移除**</span><span class="sxs-lookup"><span data-stu-id="12668-114">**Remove**</span></span>  
 <span data-ttu-id="12668-115">若要从列表中删除程序集引用，请选择程序集名并单击“删除”\*\*\*\* 按钮。</span><span class="sxs-lookup"><span data-stu-id="12668-115">To remove an assembly reference from the list, select the assembly name and click the **Remove** button.</span></span>  
  
 <span data-ttu-id="12668-116">**添加或删除类**</span><span class="sxs-lookup"><span data-stu-id="12668-116">**Add or remove classes**</span></span>  
 <span data-ttu-id="12668-117">列出报表使用的类实例。</span><span class="sxs-lookup"><span data-stu-id="12668-117">Lists the class instances that are used by the report.</span></span> <span data-ttu-id="12668-118">该类列表仅适用于基于实例的成员，而不适用于静态成员。</span><span class="sxs-lookup"><span data-stu-id="12668-118">The class list is used only by instance-based members, not static members.</span></span>  
  
 <span data-ttu-id="12668-119">**添加**</span><span class="sxs-lookup"><span data-stu-id="12668-119">**Add**</span></span>  
 <span data-ttu-id="12668-120">单击该选项可以添加类引用。</span><span class="sxs-lookup"><span data-stu-id="12668-120">Click to add a class reference.</span></span> <span data-ttu-id="12668-121">单击省略号 ( ") " 按钮以打开 "**打开**" 对话框，并选择完成报表处理和表达式计算所需的类。</span><span class="sxs-lookup"><span data-stu-id="12668-121">Click the ellipsis (...) button to open the **Open** dialog box and select the classes necessary to complete report processing and expression evaluation.</span></span>  
  
 <span data-ttu-id="12668-122">**移除**</span><span class="sxs-lookup"><span data-stu-id="12668-122">**Remove**</span></span>  
 <span data-ttu-id="12668-123">若要删除类实例，请选中该实例并单击“删除”\*\*\*\* 按钮。</span><span class="sxs-lookup"><span data-stu-id="12668-123">To delete the class instance, select it and click the **Remove** button.</span></span>  
  
 <span data-ttu-id="12668-124">**Up**</span><span class="sxs-lookup"><span data-stu-id="12668-124">**Up**</span></span>  
 <span data-ttu-id="12668-125">可为有依赖关系的类在列表中上移该引用。</span><span class="sxs-lookup"><span data-stu-id="12668-125">For classes that have dependencies, you can move this reference higher in the list.</span></span>  
  
 <span data-ttu-id="12668-126">**向下**</span><span class="sxs-lookup"><span data-stu-id="12668-126">**Down**</span></span>  
 <span data-ttu-id="12668-127">可为有依赖关系的类在列表中下移该引用。</span><span class="sxs-lookup"><span data-stu-id="12668-127">For classes that have dependencies, you can move this reference lower in the list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12668-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="12668-128">See Also</span></span>  
 <span data-ttu-id="12668-129">[报表生成器对话框、窗格和向导的帮助](../../2014/reporting-services/report-builder-help-for-dialog-boxes-panes-and-wizards.md) </span><span class="sxs-lookup"><span data-stu-id="12668-129">[Report Builder Help for Dialog Boxes, Panes, and Wizards](../../2014/reporting-services/report-builder-help-for-dialog-boxes-panes-and-wizards.md) </span></span>  
 [<span data-ttu-id="12668-130">表达式（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="12668-130">Expressions &#40;Report Builder and SSRS&#41;</span></span>](report-design/expressions-report-builder-and-ssrs.md)  
  
  
