---
title: 向报表添加代码 (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- code [Reporting Services]
- custom code [Reporting Services]
- expressions [Reporting Services], code
- adding code
- reports [Reporting Services], code
ms.assetid: 00ef8fc6-99fe-49b2-8a22-7eb475881dc4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c1964e69d00e1a27da29ce8cfb73b7bee1bece7a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690401"
---
# <a name="add-code-to-a-report-ssrs"></a><span data-ttu-id="e82e2-102">向报表添加代码 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="e82e2-102">Add Code to a Report (SSRS)</span></span>
  <span data-ttu-id="e82e2-103">您可以在任何表达式中调用自己的自定义代码。</span><span class="sxs-lookup"><span data-stu-id="e82e2-103">In any expression, you can call your own custom code.</span></span> <span data-ttu-id="e82e2-104">可以通过下列两种方式提供代码：</span><span class="sxs-lookup"><span data-stu-id="e82e2-104">You can provide code in the following two ways:</span></span>  
  
-   <span data-ttu-id="e82e2-105">直接在报表中使用 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 编写的嵌入代码。</span><span class="sxs-lookup"><span data-stu-id="e82e2-105">Embed code written in [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] directly in your report.</span></span> <span data-ttu-id="e82e2-106">如果代码引用非 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 或 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 的 <xref:System.Math> <xref:System.Convert>，必须向报表中添加引用。</span><span class="sxs-lookup"><span data-stu-id="e82e2-106">If your code refers to a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] that is not <xref:System.Math> or <xref:System.Convert>, you must add the reference to the report.</span></span> <span data-ttu-id="e82e2-107">有关详细信息，请参阅 [向报表添加程序集引用 (SSRS)](add-an-assembly-reference-to-a-report-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="e82e2-107">For more information, see [Add an Assembly Reference to a Report &#40;SSRS&#41;](add-an-assembly-reference-to-a-report-ssrs.md).</span></span> <span data-ttu-id="e82e2-108">有关可从代码中使用的其他引用的详细信息，请参阅[报表设计器的表达式中的自定义代码和程序集引用 (SSRS)](custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="e82e2-108">For more information about other references you can make from your code, see [Custom Code and Assembly References in Expressions in Report Designer &#40;SSRS&#41;](custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md).</span></span>  
  
-   <span data-ttu-id="e82e2-109">使用 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]提供自定义代码程序集。</span><span class="sxs-lookup"><span data-stu-id="e82e2-109">Provide a custom code assembly by using the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="e82e2-110">如果提供自定义程序集，则必须同时在创作报表的计算机上和查看报表的报表服务器上安装该自定义程序集。</span><span class="sxs-lookup"><span data-stu-id="e82e2-110">If you provide a custom assembly, you must install it on both the computer where you author the report and the report server where you view the report.</span></span> <span data-ttu-id="e82e2-111">有关详细信息，请参阅 [Using Custom Assemblies with Reports](../custom-assemblies/using-custom-assemblies-with-reports.md)。</span><span class="sxs-lookup"><span data-stu-id="e82e2-111">For more information, see [Using Custom Assemblies with Reports](../custom-assemblies/using-custom-assemblies-with-reports.md).</span></span>  
  
### <a name="to-add-embedded-code-to-a-report"></a><span data-ttu-id="e82e2-112">向报表添加嵌入代码</span><span class="sxs-lookup"><span data-stu-id="e82e2-112">To add embedded code to a report</span></span>  
  
1.  <span data-ttu-id="e82e2-113">在“设计”视图中，右键单击报表边框外的设计图面，然后单击“报表属性”   。</span><span class="sxs-lookup"><span data-stu-id="e82e2-113">In **Design** view, right-click the design surface outside the border of the report and click **Report Properties**.</span></span>  
  
2.  <span data-ttu-id="e82e2-114">单击 **“代码”** 。</span><span class="sxs-lookup"><span data-stu-id="e82e2-114">Click **Code**.</span></span>  
  
3.  <span data-ttu-id="e82e2-115">在 **“自定义代码”** 中键入代码。</span><span class="sxs-lookup"><span data-stu-id="e82e2-115">In **Custom code**, type the code.</span></span> <span data-ttu-id="e82e2-116">报表运行时，代码中的错误会引发警告。</span><span class="sxs-lookup"><span data-stu-id="e82e2-116">Errors in the code produce warnings when the report runs.</span></span> <span data-ttu-id="e82e2-117">下面的示例创建一个名为 `ChangeWord` 的自定义函数，该函数可使用词语“`Bike`”替换“`Bicycle`”。</span><span class="sxs-lookup"><span data-stu-id="e82e2-117">The following example creates a custom function named `ChangeWord` that replaces the word "`Bike`" with "`Bicycle`".</span></span>  
  
    ```  
    Public Function ChangeWord(ByVal s As String) As String  
       Dim strBuilder As New System.Text.StringBuilder(s)  
       If s.Contains("Bike") Then  
          strBuilder.Replace("Bike", "Bicycle")  
          Return strBuilder.ToString()  
          Else : Return s  
       End If  
    End Function  
    ```  
  
4.  <span data-ttu-id="e82e2-118">下面的示例演示如何在表达式中向此函数传递名为 Category 的数据集字段。</span><span class="sxs-lookup"><span data-stu-id="e82e2-118">The following example shows how to pass a dataset field named Category to this function in an expression:</span></span>  
  
    ```  
    =Code.ChangeWord(Fields!Category.Value)  
    ```  
  
     <span data-ttu-id="e82e2-119">如果将此表达式添加到显示类别值的表单元，则只要该行的数据集字段中出现词语“Bike”，表单元值就会显示词语“Bicycle”。</span><span class="sxs-lookup"><span data-stu-id="e82e2-119">If you add this expression to a table cell that displays category values, whenever the word "Bike" is in the dataset field for that row, the table cell value displays the word "Bicycle" instead.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e82e2-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e82e2-120">See Also</span></span>  
 <span data-ttu-id="e82e2-121">[“报表属性”对话框 -&gt;“代码”](../report-properties-dialog-box-code.md) </span><span class="sxs-lookup"><span data-stu-id="e82e2-121">[Report Properties Dialog Box, Code](../report-properties-dialog-box-code.md) </span></span>  
 <span data-ttu-id="e82e2-122">[表达式示例（报表生成器和 SSRS）](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="e82e2-122">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="e82e2-123">Parameters 集合引用（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="e82e2-123">Parameters Collection References &#40;Report Builder and SSRS&#41;</span></span>](built-in-collections-parameters-collection-references-report-builder.md)  
  
  
