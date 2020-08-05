---
title: " (SSAS 表格) 的计算 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 738816e3-0e1d-44a5-8d1b-81068dce8ac0
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2da86ae5c5652c8b2614cae4bbb721802700d973
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580907"
---
# <a name="calculations-ssas-tabular"></a><span data-ttu-id="1fb80-102">计算（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="1fb80-102">Calculations (SSAS Tabular)</span></span>
  <span data-ttu-id="1fb80-103">将数据导入模型之后，可以添加计算来聚合、筛选、扩展、组合和保护该数据。</span><span class="sxs-lookup"><span data-stu-id="1fb80-103">After you have imported data into your model, you can add calculations to aggregate, filter, extend, combine, and secure that data.</span></span> <span data-ttu-id="1fb80-104">表格模型采用数据分析表达式 (DAX)，这是一种用于创建自定义计算的公式语言。</span><span class="sxs-lookup"><span data-stu-id="1fb80-104">Tabular models use Data Analysis Expressions (DAX), a formula language for creating custom calculations.</span></span> <span data-ttu-id="1fb80-105">在表格模型中，使用 DAX 公式创建的计算用在“计算列” \*\*、“度量值” \*\* 和“行筛选器” \*\* 中。</span><span class="sxs-lookup"><span data-stu-id="1fb80-105">In tabular models, the calculations you create by using DAX formulas are used in *Calculated Columns*, *Measures*, and *Row Filters*.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1fb80-106">本节内容</span><span class="sxs-lookup"><span data-stu-id="1fb80-106">In This Section</span></span>  
  
|<span data-ttu-id="1fb80-107">主题</span><span class="sxs-lookup"><span data-stu-id="1fb80-107">Topic</span></span>|<span data-ttu-id="1fb80-108">说明</span><span class="sxs-lookup"><span data-stu-id="1fb80-108">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="1fb80-109">了解表格模型中的 DAX（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="1fb80-109">Understanding DAX in Tabular Models &#40;SSAS Tabular&#41;</span></span>](understanding-dax-in-tabular-models-ssas-tabular.md)|<span data-ttu-id="1fb80-110">说明为表格模型中的计算列、度量值和行筛选器创建计算所用的数据分析表达式 (DAX) 公式语言。</span><span class="sxs-lookup"><span data-stu-id="1fb80-110">Describes the Data Analysis Expressions (DAX) formula language used to create calculations for calculated columns, measures, and row filters in tabular models.</span></span>|  
|[<span data-ttu-id="1fb80-111">DirectQuery 模式下的公式兼容性</span><span class="sxs-lookup"><span data-stu-id="1fb80-111">Formula Compatibility in DirectQuery Mode</span></span>](../dax-formula-compatibility-in-directquery-mode-ssas-2014.md)|<span data-ttu-id="1fb80-112">说明差异，列出在 DirectQuery 模式下不支持的函数，并列出受支持但可能返回不同结果的函数。</span><span class="sxs-lookup"><span data-stu-id="1fb80-112">Describes the differences, lists the functions that are not supported in DirectQuery mode, and lists the functions that are supported but could return different results.</span></span>|  
|[<span data-ttu-id="1fb80-113">&#40;DAX&#41; 参考的数据分析表达式</span><span class="sxs-lookup"><span data-stu-id="1fb80-113">Data Analysis Expressions &#40;DAX&#41; Reference</span></span>](/dax/data-analysis-expressions-dax-reference)|<span data-ttu-id="1fb80-114">本节提供了 DAX 语法、运算符和函数的详细说明。</span><span class="sxs-lookup"><span data-stu-id="1fb80-114">This section provides detailed descriptions of DAX syntax, operators, and functions.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="1fb80-115">本节不提供用于创建计算的分步任务。</span><span class="sxs-lookup"><span data-stu-id="1fb80-115">Step-by-step tasks for creating calculations are not provided in this section.</span></span> <span data-ttu-id="1fb80-116">因为在计算列、度量值和行筛选器（在角色中）中指定了计算，在与这些功能相关的任务中将提供关于在何处创建 DAX 公式的说明。</span><span class="sxs-lookup"><span data-stu-id="1fb80-116">Because calculations are specified in calculated columns, measures, and row filters (in roles), instructions on where to create DAX formulas are provided in tasks related to those features.</span></span> <span data-ttu-id="1fb80-117">有关详细信息，请参阅[创建计算列（SSAS 表格）](ssas-calculated-columns-create-a-calculated-column.md)、[创建和管理度量值（SSAS 表格）](measures-ssas-tabular.md)和[创建和管理角色（SSAS 表格）](roles-ssas-tabular.md)。</span><span class="sxs-lookup"><span data-stu-id="1fb80-117">For more information, see [Create a Calculated Column &#40;SSAS Tabular&#41;](ssas-calculated-columns-create-a-calculated-column.md), [Create and Manage Measures &#40;SSAS Tabular&#41;](measures-ssas-tabular.md), and [Create and Manage Roles &#40;SSAS Tabular&#41;](roles-ssas-tabular.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1fb80-118">尽管也可以使用 DAX 查询表格模型，但本节中的主题侧重于介绍如何使用 DAX 公式来创建计算。</span><span class="sxs-lookup"><span data-stu-id="1fb80-118">While DAX can also be used to query a tabular model, topics in this section focus specifically on using DAX formulas to create calculations.</span></span>  
  
  
