---
title: 在 RDL 文件中引用程序集 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- RDL [Reporting Services], referencing assemblies
- referencing custom assemblies
- custom assemblies [Reporting Services], referencing
- Report Definition Language, referencing assemblies
- report definition files [Reporting Services]
ms.assetid: 9a48e552-7d47-4243-9be1-894990c506d9
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 14593717d2319d7d702fd0c414e0c24428006f51
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687544"
---
# <a name="referencing-assemblies-in-an-rdl-file"></a><span data-ttu-id="22792-102">在 RDL 文件中引用程序集</span><span class="sxs-lookup"><span data-stu-id="22792-102">Referencing Assemblies in an RDL File</span></span>
  <span data-ttu-id="22792-103">为了支持在报表定义文件中使用自定义代码程序集，RDL 规范中包含两个报表定义语言 (RDL) 元素：CodeModules 元素和 Classes 元素\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="22792-103">To support the use of custom code assemblies in report definition files, two Report Definition Language (RDL) elements are included in the RDL specification: the **CodeModules** element and the **Classes** element.</span></span>  
  
 <span data-ttu-id="22792-104">通过 CodeModules 元素，可以在报表表达式中引用托管代码程序集\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="22792-104">The **CodeModules** element enables you to refer to managed code assemblies in report expressions.</span></span> <span data-ttu-id="22792-105">CodeModules 是一个顶级元素，它包含针对在报表定义文件中用来调用专用函数的程序集的引用\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="22792-105">**CodeModules** is a top-level element that contains the reference to the assembly that you use in your report definition files to call specialized functions.</span></span> <span data-ttu-id="22792-106">支持使用自定义程序集的报表定义中的一个条目可能如下所示：</span><span class="sxs-lookup"><span data-stu-id="22792-106">An entry in a report definition that supports the use of a custom assembly might look like the following:</span></span>  
  
```  
<CodeModules>  
   <CodeModule>CurrencyConversion, Version=1.0.1363.31103, Culture=neutral, PublicKeyToken=null</CodeModule>  
</CodeModules>  
```  
  
 <span data-ttu-id="22792-107">可以通过手动将 CodeModule 元素添加到 RDL 文件或使用“报表属性”对话框的“引用”选项卡来注册自定义程序集，而不是从自定义代码调用 <xref:System.Reflection.Assembly.Load%2A>\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="22792-107">Instead of calling <xref:System.Reflection.Assembly.Load%2A> from your custom code, register your custom assemblies by either manually adding **CodeModule** elements to your RDL file or by using the **References** tab of the **Report Properties** dialog.</span></span> <span data-ttu-id="22792-108">有关详细信息，请参阅 [报表设计器的表达式中的自定义代码和程序集引用 (SSRS)](../report-design/custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="22792-108">For more information, see [Custom Code and Assembly References in Expressions in Report Designer &#40;SSRS&#41;](../report-design/custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md).</span></span>  
  
 <span data-ttu-id="22792-109">Classes 元素支持在报表定义中使用实例成员\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="22792-109">The **Classes** element supports the use of instance members in a report definition.</span></span> <span data-ttu-id="22792-110">Classes 是一个顶级元素，它包含对类名称和实例名称的引用\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="22792-110">**Classes** is a top-level element that contains a reference to the class name and an instance name.</span></span> <span data-ttu-id="22792-111">支持使用实例成员的报表定义中的一个条目可能如下所示：</span><span class="sxs-lookup"><span data-stu-id="22792-111">An entry in a report definition that supports the use of instance members might look like the following:</span></span>  
  
```  
<Classes>  
   <Class>  
      <ClassName>CurrencyConversion.DollarCurrencyConversion</ClassName>  
      <InstanceName>m_myDollarConversion</InstanceName>  
   </Class>  
</Classes>  
```  
  
 <span data-ttu-id="22792-112">有关详细信息，请参阅[通过表达式访问自定义程序集](accessing-custom-assemblies-through-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="22792-112">For more information, see [Accessing Custom Assemblies Through Expressions](accessing-custom-assemblies-through-expressions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22792-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="22792-113">See Also</span></span>  
 [<span data-ttu-id="22792-114">将自定义程序集用于报表</span><span class="sxs-lookup"><span data-stu-id="22792-114">Using Custom Assemblies with Reports</span></span>](using-custom-assemblies-with-reports.md)  
  
  
