---
title: “创建新条件”或“打开条件”对话框，“常规”页 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.swb.dmf.condition.f1
ms.assetid: 106954bf-e4ba-412b-9c1a-907d06153dcd
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 72e4a77df553ac8e97609e82bd51c8fd93b64b23
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591301"
---
# <a name="create-new-condition-or-open-condition-dialog-box-general-page"></a><span data-ttu-id="63a4c-102">“创建新条件”或“打开条件”对话框，“常规”页</span><span class="sxs-lookup"><span data-stu-id="63a4c-102">Create New Condition or Open Condition Dialog Box, General Page</span></span>
  <span data-ttu-id="63a4c-103">此对话框用于创建或更改基于策略的管理条件。</span><span class="sxs-lookup"><span data-stu-id="63a4c-103">Use this dialog box to create or change a Policy-Based Management condition.</span></span> <span data-ttu-id="63a4c-104">条件是一个布尔表达式，用于针对方面指定基于策略的管理目标的一组允许状态。</span><span class="sxs-lookup"><span data-stu-id="63a4c-104">A condition is a Boolean expression that specifies a set of allowed states of a Policy-Based Management managed target with regard to facets.</span></span> <span data-ttu-id="63a4c-105">可在\*\*\*\*“表达式”/“字段”框中选择的属性取决于所使用的方面。</span><span class="sxs-lookup"><span data-stu-id="63a4c-105">The properties that can be selected in the **Expression/Field** box depend upon the facet that is used.</span></span> <span data-ttu-id="63a4c-106">有关条件与方面和策略如何关联的详细信息，请参阅 [使用基于策略的管理来管理服务器](administer-servers-by-using-policy-based-management.md)。</span><span class="sxs-lookup"><span data-stu-id="63a4c-106">For more information about how conditions relate to facets and policies, see [Administer Servers by Using Policy-Based Management](administer-servers-by-using-policy-based-management.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="63a4c-107">选项</span><span class="sxs-lookup"><span data-stu-id="63a4c-107">Options</span></span>  
 <span data-ttu-id="63a4c-108">**名称**</span><span class="sxs-lookup"><span data-stu-id="63a4c-108">**Name**</span></span>  
 <span data-ttu-id="63a4c-109">对于新条件，请键入新条件的名称。</span><span class="sxs-lookup"><span data-stu-id="63a4c-109">For a new condition, type the new condition name.</span></span> <span data-ttu-id="63a4c-110">对于现有条件，将显示其名称。</span><span class="sxs-lookup"><span data-stu-id="63a4c-110">For an existing condition, the name is displayed.</span></span>  
  
 <span data-ttu-id="63a4c-111">**方面**</span><span class="sxs-lookup"><span data-stu-id="63a4c-111">**Facet**</span></span>  
 <span data-ttu-id="63a4c-112">此条件所使用的方面。</span><span class="sxs-lookup"><span data-stu-id="63a4c-112">The facet used by this condition.</span></span>  
  
 <span data-ttu-id="63a4c-113">**AndOr**</span><span class="sxs-lookup"><span data-stu-id="63a4c-113">**AndOr**</span></span>  
 <span data-ttu-id="63a4c-114">在添加多个表达式时，指示是否应使用 **And** 或 **Or**联接这些表达式。</span><span class="sxs-lookup"><span data-stu-id="63a4c-114">When you add multiple expressions, indicates whether the expressions should be joined by using **And** or **Or**.</span></span> <span data-ttu-id="63a4c-115">如果只有一个表达式，将保留空白。</span><span class="sxs-lookup"><span data-stu-id="63a4c-115">Remains blank when there is only one expression.</span></span>  
  
 <span data-ttu-id="63a4c-116">**字段**</span><span class="sxs-lookup"><span data-stu-id="63a4c-116">**Field**</span></span>  
 <span data-ttu-id="63a4c-117">每个方面公开一个或多个可设置的属性。</span><span class="sxs-lookup"><span data-stu-id="63a4c-117">Each facet exposes one or more properties that can be set.</span></span> <span data-ttu-id="63a4c-118">在“字段”框中，从可用属性列表中选择一个属性，为此条件创建一个表达式。</span><span class="sxs-lookup"><span data-stu-id="63a4c-118">In the field box, select a property from the list of available properties to create an expression for this condition.</span></span>  
  
 <span data-ttu-id="63a4c-119">**“运算符”**</span><span class="sxs-lookup"><span data-stu-id="63a4c-119">**Operator**</span></span>  
 <span data-ttu-id="63a4c-120">为该表达式选择一个比较运算符。</span><span class="sxs-lookup"><span data-stu-id="63a4c-120">Select a comparison operator for this expression.</span></span> <span data-ttu-id="63a4c-121">比较运算符包括：=、!=、>、>=、<、<=、[NOT]LIKE、[NOT]IN。</span><span class="sxs-lookup"><span data-stu-id="63a4c-121">Operators are as follows: =, !=, >, >=, <, <=, [NOT]LIKE, [NOT]IN.</span></span> <span data-ttu-id="63a4c-122">并非所有运算符都适用于某些属性。</span><span class="sxs-lookup"><span data-stu-id="63a4c-122">Not all operators are available for some properties.</span></span>  
  
 <span data-ttu-id="63a4c-123">**值**</span><span class="sxs-lookup"><span data-stu-id="63a4c-123">**Value**</span></span>  
 <span data-ttu-id="63a4c-124">该表达式的值设置。</span><span class="sxs-lookup"><span data-stu-id="63a4c-124">The value setting for this expression.</span></span> <span data-ttu-id="63a4c-125">允许的值取决于方面。</span><span class="sxs-lookup"><span data-stu-id="63a4c-125">The allowed values depend on the facet.</span></span> <span data-ttu-id="63a4c-126">值可以为 TRUE/FALSE、字符串或数值。</span><span class="sxs-lookup"><span data-stu-id="63a4c-126">Values can be TRUE/FALSE, string, or numeric.</span></span> <span data-ttu-id="63a4c-127">字符串值必须用单引号引起来，例如： **'AdventureWorks'**。</span><span class="sxs-lookup"><span data-stu-id="63a4c-127">String values must be enclosed in single quotation marks, for example: **'AdventureWorks'**.</span></span> <span data-ttu-id="63a4c-128">并非所有运算符都适用于某些属性。</span><span class="sxs-lookup"><span data-stu-id="63a4c-128">Not all operators are available for some properties.</span></span>  
  
## <a name="group-clauses"></a><span data-ttu-id="63a4c-129">子句分组</span><span class="sxs-lookup"><span data-stu-id="63a4c-129">Group Clauses</span></span>  
 <span data-ttu-id="63a4c-130">可以对子句进行分组，以使其作为独立于查询其余部分的一个单元来运行，就像在数学等式或逻辑语句中的表达式两侧加上括号一样。</span><span class="sxs-lookup"><span data-stu-id="63a4c-130">Clauses can be grouped to operate as a single unit separate from the rest of the query, just like putting parentheses around an expression in a mathematical equation or logic statement.</span></span> <span data-ttu-id="63a4c-131">在生成复杂查询时，对子句进行分组是非常有用的。</span><span class="sxs-lookup"><span data-stu-id="63a4c-131">Grouping clauses is useful when you are building complex queries.</span></span>  
  
 <span data-ttu-id="63a4c-132">**对子句进行分组**</span><span class="sxs-lookup"><span data-stu-id="63a4c-132">**To group clauses**</span></span>  
  
-   <span data-ttu-id="63a4c-133">按 Shift 或 Ctrl 键，然后单击两个或多个子句以选择一个范围。</span><span class="sxs-lookup"><span data-stu-id="63a4c-133">Press the SHIFT or CTRL keys, and then click two or more clauses to select a range.</span></span> <span data-ttu-id="63a4c-134">右键单击所选区域，然后单击\*\*\*\*“子句分组”。</span><span class="sxs-lookup"><span data-stu-id="63a4c-134">Right-click the selected area, and then click **Group Clauses**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63a4c-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="63a4c-135">See Also</span></span>  
 [<span data-ttu-id="63a4c-136">使用基于策略的管理来管理服务器</span><span class="sxs-lookup"><span data-stu-id="63a4c-136">Administer Servers by Using Policy-Based Management</span></span>](administer-servers-by-using-policy-based-management.md)  
  
  
