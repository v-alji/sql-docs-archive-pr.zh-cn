---
title: 表达式参考（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: bb16e4ab-b13f-48f2-8cfe-1851656875ef
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7854aa2cc256d63fe93ddb049486e782bfaa0e11
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580599"
---
# <a name="expression-reference-report-builder-and-ssrs"></a><span data-ttu-id="94959-102">表达式引用（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="94959-102">Expression Reference (Report Builder and SSRS)</span></span>
  <span data-ttu-id="94959-103">报表表达式支持对内置函数和内置集合的多种形式的引用。</span><span class="sxs-lookup"><span data-stu-id="94959-103">Report expressions support a variety of references to built-in functions and built-in collections.</span></span> <span data-ttu-id="94959-104">表达式必须具有有效的 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 语法，然后才能发布或处理报表。</span><span class="sxs-lookup"><span data-stu-id="94959-104">Expressions must have valid [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] syntax before a report can be published or processed.</span></span>  
  
 <span data-ttu-id="94959-105">若要开发复杂表达式或使用自定义代码或自定义程序集的表达式，建议您使用 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中的报表设计器。</span><span class="sxs-lookup"><span data-stu-id="94959-105">To develop complex expressions or expressions that use custom code or custom assemblies, we recommend that you use Report Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="94959-106">有关详细信息，请参阅 [报表设计器的表达式中的自定义代码和程序集引用 (SSRS)](custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="94959-106">For more information, see [Custom Code and Assembly References in Expressions in Report Designer &#40;SSRS&#41;](custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
 <span data-ttu-id="94959-107">本节中的主题可帮助编写报表中的简单表达式。</span><span class="sxs-lookup"><span data-stu-id="94959-107">Use the topics in this section to help write simple expressions in a report.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="94959-108">本节内容</span><span class="sxs-lookup"><span data-stu-id="94959-108">In This Section</span></span>  
 [<span data-ttu-id="94959-109">表达式中的数据类型（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="94959-109">Data Types in Expressions &#40;Report Builder and SSRS&#41;</span></span>](expressions-report-builder-and-ssrs.md)  
  
 [<span data-ttu-id="94959-110">表达式中的常量类型（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="94959-110">Constants in Expressions &#40;Report Builder and SSRS&#41;</span></span>](constants-in-expressions-report-builder-and-ssrs.md)  
  
 [<span data-ttu-id="94959-111">表达式中的运算符类型（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="94959-111">Operators in Expressions &#40;Report Builder and SSRS&#41;</span></span>](operators-in-expressions-report-builder-and-ssrs.md)  
  
 [<span data-ttu-id="94959-112">表达式中的内置集合（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="94959-112">Built-in Collections in Expressions &#40;Report Builder and SSRS&#41;</span></span>](built-in-collections-in-expressions-report-builder.md)  
  
 [<span data-ttu-id="94959-113">内置的全局和用户引用（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="94959-113">Built-in Globals and Users References &#40;Report Builder and SSRS&#41;</span></span>](built-in-collections-built-in-globals-and-users-references-report-builder.md)  
  
 [<span data-ttu-id="94959-114">Parameters 集合引用（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="94959-114">Parameters Collection References &#40;Report Builder and SSRS&#41;</span></span>](built-in-collections-parameters-collection-references-report-builder.md)  
  
 [<span data-ttu-id="94959-115">数据集字段集合引用（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="94959-115">Dataset Fields Collection References &#40;Report Builder and SSRS&#41;</span></span>](built-in-collections-dataset-fields-collection-references-report-builder.md)  
  
 [<span data-ttu-id="94959-116">DataSources 和 DataSets 集合引用（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="94959-116">DataSources and DataSets Collection References &#40;Report Builder and SSRS&#41;</span></span>](built-in-collections-datasources-and-datasets-references-report-builder.md)  
  
 [<span data-ttu-id="94959-117">报表和组变量集合引用（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="94959-117">Report and Group Variables Collections References &#40;Report Builder and SSRS&#41;</span></span>](built-in-collections-report-and-group-variables-references-report-builder.md)  
  
 [<span data-ttu-id="94959-118">ReportItems 集合引用（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="94959-118">ReportItems Collection References &#40;Report Builder and SSRS&#41;</span></span>](built-in-collections-reportitems-collection-references-report-builder.md)  
  
## <a name="see-also"></a><span data-ttu-id="94959-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="94959-119">See Also</span></span>  
 [<span data-ttu-id="94959-120">表达式（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="94959-120">Expressions &#40;Report Builder and SSRS&#41;</span></span>](expressions-report-builder-and-ssrs.md)  
  
  
