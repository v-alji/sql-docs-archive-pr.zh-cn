---
title: 向报表添加程序集引用 (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- code [Reporting Services]
- custom assemblies [Reporting Services], referencing
- custom code [Reporting Services]
- adding assembly references
- assemblies [Reporting Services], references
ms.assetid: 0a03939e-48ce-4c30-b227-98533f2e0ccb
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 23dda0c65589e55849f906c621e42ce70f0d7ab5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588916"
---
# <a name="add-an-assembly-reference-to-a-report-ssrs"></a><span data-ttu-id="e3ac3-102">向报表添加程序集引用 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="e3ac3-102">Add an Assembly Reference to a Report (SSRS)</span></span>
  <span data-ttu-id="e3ac3-103">嵌入包含对 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 类的引用的自定义代码时，如果这些类不是 <xref:System.Math> 或 <xref:System.Convert> 中的类，必须提供对报表的程序集引用，以便报表处理器能够解析名称。</span><span class="sxs-lookup"><span data-stu-id="e3ac3-103">When you embed custom code that contains references to [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] classes that are not in <xref:System.Math> or <xref:System.Convert>, you must provide an assembly reference to the report so that the report processor can resolve the names.</span></span> <span data-ttu-id="e3ac3-104">有关详细信息，请参阅[向报表添加代码 (SSRS)](add-code-to-a-report-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="e3ac3-104">For more information, see [Add Code to a Report &#40;SSRS&#41;](add-code-to-a-report-ssrs.md).</span></span>  
  
### <a name="to-add-an-assembly-reference-to-a-report"></a><span data-ttu-id="e3ac3-105">向报表添加程序集引用</span><span class="sxs-lookup"><span data-stu-id="e3ac3-105">To add an assembly reference to a report</span></span>  
  
1.  <span data-ttu-id="e3ac3-106">在“设计”视图中，右键单击报表边框外的设计图面，然后单击“报表属性”   。</span><span class="sxs-lookup"><span data-stu-id="e3ac3-106">In **Design** view, right-click the design surface outside the border of the report and click **Report Properties**.</span></span>  
  
2.  <span data-ttu-id="e3ac3-107">单击 **“引用”** 。</span><span class="sxs-lookup"><span data-stu-id="e3ac3-107">Click **References**.</span></span>  
  
3.  <span data-ttu-id="e3ac3-108">在 **“添加或删除程序集”** 中，单击 **“添加”** ，然后单击省略号按钮浏览到程序集。</span><span class="sxs-lookup"><span data-stu-id="e3ac3-108">In **Add or remove assemblies**, click **Add** and then click the ellipsis button to browse to the assembly.</span></span>  
  
4.  <span data-ttu-id="e3ac3-109">在 **“添加或删除类”** 中，单击 **“添加”** ，然后键入类的名称，并提供要在报表中使用的实例名。</span><span class="sxs-lookup"><span data-stu-id="e3ac3-109">In **Add or remove classes**, click **Add** and then type name of the class and provide an instance name to use within the report.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e3ac3-110">仅为基于实例的成员指定类名称和实例名。</span><span class="sxs-lookup"><span data-stu-id="e3ac3-110">Specify a class and instance name only for instance-based members.</span></span> <span data-ttu-id="e3ac3-111">请不要在 **“类”** 列表中指定静态成员。</span><span class="sxs-lookup"><span data-stu-id="e3ac3-111">Do not specify static members in the **Classes** list.</span></span> <span data-ttu-id="e3ac3-112">有关详细信息，请参阅 [报表设计器的表达式中的自定义代码和程序集引用 (SSRS)](custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="e3ac3-112">For more information, see [Custom Code and Assembly References in Expressions in Report Designer &#40;SSRS&#41;](custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md).</span></span>  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e3ac3-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e3ac3-113">See Also</span></span>  
 <span data-ttu-id="e3ac3-114">[将自定义程序集用于报表](../custom-assemblies/using-custom-assemblies-with-reports.md) </span><span class="sxs-lookup"><span data-stu-id="e3ac3-114">[Using Custom Assemblies with Reports](../custom-assemblies/using-custom-assemblies-with-reports.md) </span></span>  
 [<span data-ttu-id="e3ac3-115">“报表属性”对话框 ->“引用”</span><span class="sxs-lookup"><span data-stu-id="e3ac3-115">Report Properties Dialog Box, References</span></span>](../report-properties-dialog-box-references.md)  
  
  
