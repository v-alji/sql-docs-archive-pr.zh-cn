---
title: 创建递归层次结构组（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 06eccab6-4089-46e8-a84f-5bf3bbe0c23b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: aeb99e725c5c61a6dc66c83e53afbc43b1224582
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580603"
---
# <a name="creating-recursive-hierarchy-groups-report-builder-and-ssrs"></a><span data-ttu-id="40aa6-102">创建递归层次结构组（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="40aa6-102">Creating Recursive Hierarchy Groups (Report Builder and SSRS)</span></span>
  <span data-ttu-id="40aa6-103">若要显示递归数据（其中父级和子级之间的关系由数据集中的字段表示），可以根据子字段设置数据区域组表达式，并根据父字段设置父属性。</span><span class="sxs-lookup"><span data-stu-id="40aa6-103">To display recursive data where the relationship between parent and child is represented by fields in the dataset, you can set the data region group expression based on the child field and set the Parent property based on the parent field.</span></span>  
  
 <span data-ttu-id="40aa6-104">递归层次结构组通常用于显示分层数据，例如，显示组织结构图中的雇员。</span><span class="sxs-lookup"><span data-stu-id="40aa6-104">Displaying hierarchical data is a common use for recursive hierarchy groups, for example, employees in an organizational chart.</span></span> <span data-ttu-id="40aa6-105">数据集包含雇员和经理的列表，其中经理的姓名也显示在雇员列表中。</span><span class="sxs-lookup"><span data-stu-id="40aa6-105">The dataset includes a list of employees and the managers, where the manager names also appear in the list of employees.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="creating-recursive-hierarchies"></a><span data-ttu-id="40aa6-106">创建递归层次结构</span><span class="sxs-lookup"><span data-stu-id="40aa6-106">Creating Recursive Hierarchies</span></span>  
 <span data-ttu-id="40aa6-107">若要在 Tablix 数据区域中创建一个递归层次结构，必须将组表达式设置为指定子数据的字段，并将该组的 Parent 属性设置为指定父数据的字段。</span><span class="sxs-lookup"><span data-stu-id="40aa6-107">To build a recursive hierarchy in a tablix data region, you must set the group expression to the field that specifies the child data and the Parent property of the group to the field that specifies the parent data.</span></span> <span data-ttu-id="40aa6-108">例如，对于包含雇员 ID 字段和经理 ID 字段的数据集（其中雇员向经理报告），将组表达式设置为雇员 ID，并将 Parent 属性设置为经理 ID。</span><span class="sxs-lookup"><span data-stu-id="40aa6-108">For example, for a dataset that includes fields for employee ID and manager ID where employees report to managers, set the group expression to employee ID and the Parent property to manager ID.</span></span>  
  
 <span data-ttu-id="40aa6-109">定义为递归层次结构的组（即使用 Parent 属性的组）只能有一个组表达式。</span><span class="sxs-lookup"><span data-stu-id="40aa6-109">A group that is defined as a recursive hierarchy (that is, a group that uses the Parent property) can have only one group expression.</span></span> <span data-ttu-id="40aa6-110">您可以在文本框填充中使用 `Level` 函数，以便基于雇员在层次结构中的级别来缩进雇员姓名。</span><span class="sxs-lookup"><span data-stu-id="40aa6-110">You can use the `Level` function in text box padding to indent employee names based on their level in the hierarchy.</span></span>  
  
 <span data-ttu-id="40aa6-111">有关详细信息，请参阅[在数据区域中添加或删除组（报表生成器和 SSRS）](add-or-delete-a-group-in-a-data-region-report-builder-and-ssrs.md)和[创建递归层次结构组（报表生成器和 SSRS）](create-a-recursive-hierarchy-group-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="40aa6-111">For more information, see [Add or Delete a Group in a Data Region &#40;Report Builder and SSRS&#41;](add-or-delete-a-group-in-a-data-region-report-builder-and-ssrs.md) and  [Create a Recursive Hierarchy Group &#40;Report Builder and SSRS&#41;](create-a-recursive-hierarchy-group-report-builder-and-ssrs.md).</span></span>  
  
### <a name="aggregate-functions-that-support-recursion"></a><span data-ttu-id="40aa6-112">支持递归的聚合函数</span><span class="sxs-lookup"><span data-stu-id="40aa6-112">Aggregate Functions that support Recursion</span></span>  
 <span data-ttu-id="40aa6-113">可以使用接受 *Recursive* 参数的 Reporting Services 聚合函数来计算递归层次结构的汇总数据。</span><span class="sxs-lookup"><span data-stu-id="40aa6-113">You can use Reporting Services aggregate functions that accept the parameter *Recursive* to calculate summary data for a recursive hierarchy.</span></span> <span data-ttu-id="40aa6-114">以下函数接受 `Recursive` 作为参数： [Sum](report-builder-functions-sum-function.md)、 [Avg](report-builder-functions-avg-function.md)、 [Count](report-builder-functions-count-function.md)、 [CountDistinct](report-builder-functions-countdistinct-function.md)、 [CountRows](report-builder-functions-countrows-function.md)、 [Max](report-builder-functions-max-function.md)、 [Min](report-builder-functions-min-function.md)、 [StDev](report-builder-functions-stdev-function.md)、 [StDevP](report-builder-functions-stdevp-function.md)、 [Sum](report-builder-functions-sum-function.md)、 [Var](report-builder-functions-var-function.md)和[VarP](report-builder-functions-varp-function.md)。</span><span class="sxs-lookup"><span data-stu-id="40aa6-114">The following functions accept `Recursive` as a parameter: [Sum](report-builder-functions-sum-function.md), [Avg](report-builder-functions-avg-function.md), [Count](report-builder-functions-count-function.md), [CountDistinct](report-builder-functions-countdistinct-function.md), [CountRows](report-builder-functions-countrows-function.md), [Max](report-builder-functions-max-function.md), [Min](report-builder-functions-min-function.md), [StDev](report-builder-functions-stdev-function.md), [StDevP](report-builder-functions-stdevp-function.md), [Sum](report-builder-functions-sum-function.md), [Var](report-builder-functions-var-function.md), and [VarP](report-builder-functions-varp-function.md).</span></span> <span data-ttu-id="40aa6-115">有关详细信息，请参阅 [聚合函数引用（报表生成器和 SSRS）](report-builder-functions-aggregate-functions-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="40aa6-115">For more information, see [Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](report-builder-functions-aggregate-functions-reference.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40aa6-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="40aa6-116">See Also</span></span>  
 <span data-ttu-id="40aa6-117">[表、矩阵和列表（报表生成器和 SSRS）](tables-matrices-and-lists-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="40aa6-117">[Tables, Matrices, and Lists &#40;Report Builder and SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="40aa6-118">[Tablix 数据区域（报表生成器和 SSRS）](../tablix-data-region-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="40aa6-118">[Tablix Data Region &#40;Report Builder and SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="40aa6-119">[聚合函数引用（报表生成器和 SSRS）](report-builder-functions-aggregate-functions-reference.md) </span><span class="sxs-lookup"><span data-stu-id="40aa6-119">[Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) </span></span>  
 <span data-ttu-id="40aa6-120">[表（报表生成器和 SSRS）](tables-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="40aa6-120">[Tables &#40;Report Builder  and SSRS&#41;](tables-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="40aa6-121">[矩阵（报表生成器和 SSRS）](create-a-matrix-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="40aa6-121">[Matrices &#40;Report Builder and SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="40aa6-122">[列表（报表生成器和 SSRS）](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="40aa6-122">[Lists &#40;Report Builder and SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="40aa6-123">表、矩阵和列表（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="40aa6-123">Tables, Matrices, and Lists &#40;Report Builder and SSRS&#41;</span></span>](tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
