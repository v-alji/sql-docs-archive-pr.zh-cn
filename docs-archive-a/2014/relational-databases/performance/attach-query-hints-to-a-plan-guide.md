---
title: 将查询提示附加到计划指南 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: 2131f796-6359-4f9e-9047-da0b3d4dedaf
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 074c69ffefd2b5a7b2ef445f941f97b7130b0732
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588488"
---
# <a name="attach-query-hints-to-a-plan-guide"></a><span data-ttu-id="c0542-102">将查询提示附加到计划指南</span><span class="sxs-lookup"><span data-stu-id="c0542-102">Attach Query Hints to a Plan Guide</span></span>
  <span data-ttu-id="c0542-103">计划指南中可以使用有效查询提示的任何组合。</span><span class="sxs-lookup"><span data-stu-id="c0542-103">Any combination of valid query hints can be used in a plan guide.</span></span> <span data-ttu-id="c0542-104">当计划指南与某一查询匹配时，计划指南提示子句中指定的 OPTION 子句将先添加到该查询中，然后该查询才会进行编译和优化。</span><span class="sxs-lookup"><span data-stu-id="c0542-104">When a plan guide matches a query, the OPTION clause specified in the hints clause of a plan guide is added to the query before it compiles and optimizes.</span></span> <span data-ttu-id="c0542-105">如果与计划指南匹配的查询已包含 OPTION 子句，则计划指南中指定的查询提示将替换查询中已存在的查询提示。</span><span class="sxs-lookup"><span data-stu-id="c0542-105">If a query that is matched to a plan guide already has an OPTION clause, the query hints specified in the plan guide replace those in the query.</span></span> <span data-ttu-id="c0542-106">但是，对于要与已包含 OPTION 子句的查询匹配的计划指南，在 sp_create_plan_guide 语句中指定要匹配的查询文本时，必须包含查询的 OPTION 子句。</span><span class="sxs-lookup"><span data-stu-id="c0542-106">However, for a plan guide to match a query that already has an OPTION clause, you must include the OPTION clause of the query when you specify the text of the query to match in the sp_create_plan_guide statement.</span></span> <span data-ttu-id="c0542-107">若要将计划指南中指定的提示添加到查询中已存在的提示，而不是替换已存在的提示，则必须在计划指南的 OPTION 子句中同时指定原始提示和附加提示。</span><span class="sxs-lookup"><span data-stu-id="c0542-107">If you want the hints specified in the plan guide to be added to the hints that already exist on the query, instead of replacing them, you must specify both the original hints and the additional hints in the OPTION clause of the plan guide.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="c0542-108">计划指南错用查询提示会导致出现编译、执行或性能问题。</span><span class="sxs-lookup"><span data-stu-id="c0542-108">Plan guides that misuse query hints can cause compilation, execution, or performance problems.</span></span> <span data-ttu-id="c0542-109">因此计划指南应仅由经验丰富的开发人员和数据库管理员使用。</span><span class="sxs-lookup"><span data-stu-id="c0542-109">Plan guides should be used only by experienced developers and database administrators.</span></span>  
  
## <a name="common-query-hints-used-in-plan-guides"></a><span data-ttu-id="c0542-110">计划指南中常用的查询提示</span><span class="sxs-lookup"><span data-stu-id="c0542-110">Common Query Hints Used in Plan Guides</span></span>  
 <span data-ttu-id="c0542-111">能够从计划指南中受益的查询通常是基于参数的，并且性能较差，因为它们使用的是参数值不表示最差情况或最具代表性方案的缓存查询计划。</span><span class="sxs-lookup"><span data-stu-id="c0542-111">Queries that can benefit from plan guides are generally parameter-based, and may be performing poorly because they use cached query plans whose parameter values do not represent a worst-case or most representative scenario.</span></span> <span data-ttu-id="c0542-112">OPTIMIZE FOR 查询提示和 RECOMPILE 查询提示可用于解决这一问题。</span><span class="sxs-lookup"><span data-stu-id="c0542-112">The OPTIMIZE FOR and RECOMPILE query hints can be used to address this problem.</span></span> <span data-ttu-id="c0542-113">优化查询时，OPTIMIZE FOR 会指示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用参数的特定值。</span><span class="sxs-lookup"><span data-stu-id="c0542-113">OPTIMIZE FOR instructs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to use a particular value for a parameter when the query is optimized.</span></span> <span data-ttu-id="c0542-114">执行后，RECOMPILE 指示服务器放弃查询计划，并在下次执行相同的查询时强制查询优化器重新编译新的查询计划。</span><span class="sxs-lookup"><span data-stu-id="c0542-114">RECOMPILE instructs the server to discard a query plan after execution, forcing the query optimizer to recompile a new query plan the next time that the same query is executed.</span></span> <span data-ttu-id="c0542-115">有关示例，请参阅 [计划指南](plan-guides.md)。</span><span class="sxs-lookup"><span data-stu-id="c0542-115">For an example, see [Plan Guides](plan-guides.md).</span></span>  
  
 <span data-ttu-id="c0542-116">此外，您可以指定表提示 INDEX、FORCESCAN 和 FORCESEEK 作为查询提示。</span><span class="sxs-lookup"><span data-stu-id="c0542-116">In addition, you can specify the table hints INDEX, FORCESCAN, and FORCESEEK as query hints.</span></span> <span data-ttu-id="c0542-117">指定为查询提示时，这些提示的行为类似于内联表提示或视图提示。</span><span class="sxs-lookup"><span data-stu-id="c0542-117">When specified as query hints, these hints behave like an inline table or view hint.</span></span> <span data-ttu-id="c0542-118">INDEX 提示强制查询优化器仅使用指定的索引来访问被引用表或视图中的数据。</span><span class="sxs-lookup"><span data-stu-id="c0542-118">The INDEX hint forces the query optimizer to use only the specified indexes to access the data in the referenced table or view.</span></span> <span data-ttu-id="c0542-119">FORCESEEK 提示强制优化器仅使用索引查找操作来访问被引用表或视图中的数据。</span><span class="sxs-lookup"><span data-stu-id="c0542-119">The FORCESEEK hint forces the optimizer to use only an index seek operation to access the data in the referenced table or view.</span></span> <span data-ttu-id="c0542-120">这些提示提供了附加的计划指南功能并允许用户更多地干预使用计划指南的查询的优化。</span><span class="sxs-lookup"><span data-stu-id="c0542-120">These hints provide additional plan guide functionality and allow you to have more influence over the optimization of queries that use the plan guide.</span></span>  
  
  
