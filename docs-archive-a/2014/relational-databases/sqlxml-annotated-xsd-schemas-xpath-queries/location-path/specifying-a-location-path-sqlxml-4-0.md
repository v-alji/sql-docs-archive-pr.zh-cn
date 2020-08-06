---
title: " (SQLXML 4.0) 指定位置路径 |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- absolute location path
- node-set [SQLXML]
- XPath queries [SQLXML], location paths
- relative location path [SQLXML]
- location path for XPath query
ms.assetid: a23a2b75-bc69-49f0-99db-05e14dc15bc0
author: rothja
ms.author: jroth
ms.openlocfilehash: 4dfa1717afe55c1599ccaba4b5d044c6e5a20e84
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587287"
---
# <a name="specifying-a-location-path-sqlxml-40"></a><span data-ttu-id="0fc66-102">指定位置路径 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="0fc66-102">Specifying a Location Path (SQLXML 4.0)</span></span>
  <span data-ttu-id="0fc66-103">XPath 查询以表达式形式指定。</span><span class="sxs-lookup"><span data-stu-id="0fc66-103">XPath queries are specified in the form of an expression.</span></span> <span data-ttu-id="0fc66-104">具有各种各样的表达式。</span><span class="sxs-lookup"><span data-stu-id="0fc66-104">There are various kinds of expressions.</span></span> <span data-ttu-id="0fc66-105">一个位置路径是一个表达式，它选择相对于上下文节点的一组节点。</span><span class="sxs-lookup"><span data-stu-id="0fc66-105">A location path is an expression that selects a set of nodes relative to the context node.</span></span> <span data-ttu-id="0fc66-106">对位置路径进行求值的结果为节点集。</span><span class="sxs-lookup"><span data-stu-id="0fc66-106">The result of evaluating a location path is a node-set.</span></span>  
  
## <a name="types-of-location-paths"></a><span data-ttu-id="0fc66-107">位置路径的类型</span><span class="sxs-lookup"><span data-stu-id="0fc66-107">Types of Location Paths</span></span>  
 <span data-ttu-id="0fc66-108">位置路径可能采用以下任一形式：</span><span class="sxs-lookup"><span data-stu-id="0fc66-108">A location path can take either of these forms:</span></span>  
  
-   <span data-ttu-id="0fc66-109">**绝对位置路径**</span><span class="sxs-lookup"><span data-stu-id="0fc66-109">**Absolute location path**</span></span>  
  
     <span data-ttu-id="0fc66-110">绝对位置路径以文档的根节点为起点。</span><span class="sxs-lookup"><span data-stu-id="0fc66-110">An absolute location path starts at the root node of the document.</span></span> <span data-ttu-id="0fc66-111">它包含斜杠标记 (/)，后面可选包括相对位置路径。</span><span class="sxs-lookup"><span data-stu-id="0fc66-111">It consists of a slash mark (/) optionally followed by a relative location path.</span></span> <span data-ttu-id="0fc66-112">斜杠标记 (/) 选择文档的根节点。</span><span class="sxs-lookup"><span data-stu-id="0fc66-112">The slash mark (/) selects the root node of the document.</span></span>  
  
-   <span data-ttu-id="0fc66-113">**相对位置路径**</span><span class="sxs-lookup"><span data-stu-id="0fc66-113">**Relative location path**</span></span>  
  
     <span data-ttu-id="0fc66-114">相对位置路径以文档中的上下文节点为起点。</span><span class="sxs-lookup"><span data-stu-id="0fc66-114">A relative location path starts at the context node in the document.</span></span> <span data-ttu-id="0fc66-115">位置路径由包含一个或多个位置步骤的序列组成，位置步骤间以斜杠标记 (/) 分隔。</span><span class="sxs-lookup"><span data-stu-id="0fc66-115">A location path consists of a sequence of one or more location steps separated by a slash mark (/).</span></span> <span data-ttu-id="0fc66-116">每个步骤选择相对于上下文节点的一组节点。</span><span class="sxs-lookup"><span data-stu-id="0fc66-116">Each step selects a set of nodes relative to the context node.</span></span> <span data-ttu-id="0fc66-117">初始步骤序列选择相对于某个上下文节点的一组节点。</span><span class="sxs-lookup"><span data-stu-id="0fc66-117">The initial sequence of steps selects a set of nodes relative to a context node.</span></span> <span data-ttu-id="0fc66-118">该组节点中的每个节点都用作下一个步骤的上下文节点。</span><span class="sxs-lookup"><span data-stu-id="0fc66-118">Each node in that set is used as a context node for the following step.</span></span> <span data-ttu-id="0fc66-119">由该步骤表示的节点集将联接起来。</span><span class="sxs-lookup"><span data-stu-id="0fc66-119">The sets of nodes identified by that step are joined.</span></span> <span data-ttu-id="0fc66-120">例如， **child：： Order/child：： OrderDetail**选择 **\<OrderDetail>** **\<Order>** 上下文节点的元素子级的元素子级。</span><span class="sxs-lookup"><span data-stu-id="0fc66-120">For example, **child::Order/child::OrderDetail** selects the **\<OrderDetail>** element children of the **\<Order>** element children of the context node.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="0fc66-121">在 XPath 的 SQLXML 4.0 实现中，每个 XPath 查询都从根上下文开始，即使 XPath 并非显式绝对路径也不例外。</span><span class="sxs-lookup"><span data-stu-id="0fc66-121">In the SQLXML 4.0 implementation of XPath, every XPath query begins at the root context, even if the XPath is not explicitly absolute.</span></span> <span data-ttu-id="0fc66-122">例如，以“Customer”开始的 XPath 查询被视为“/Customer”。</span><span class="sxs-lookup"><span data-stu-id="0fc66-122">For example, an XPath query beginning with "Customer" is treated as "/Customer".</span></span> <span data-ttu-id="0fc66-123">在 XPath 查询**customer [订单]** 中，客户从根上下文开始，但从客户上下文开始排序。</span><span class="sxs-lookup"><span data-stu-id="0fc66-123">In the XPath query **Customer[Order]**, Customer begins at the root context, but Order begins at the Customer context.</span></span> <span data-ttu-id="0fc66-124">有关详细信息，请参阅[&#40;SQLXML 4.0&#41;使用 XPath 查询简介](../introduction-to-using-xpath-queries-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="0fc66-124">For more information, see [Introduction to Using XPath Queries &#40;SQLXML 4.0&#41;](../introduction-to-using-xpath-queries-sqlxml-4-0.md).</span></span>  
  
## <a name="location-steps"></a><span data-ttu-id="0fc66-125">位置步骤</span><span class="sxs-lookup"><span data-stu-id="0fc66-125">Location Steps</span></span>  
 <span data-ttu-id="0fc66-126">位置路径（绝对或相对）由位置步骤组成，而位置步骤包含三个部分：</span><span class="sxs-lookup"><span data-stu-id="0fc66-126">A location path (absolute or relative) is composed of location steps that contain three parts:</span></span>  
  
-   <span data-ttu-id="0fc66-127">**轴**</span><span class="sxs-lookup"><span data-stu-id="0fc66-127">**Axis**</span></span>  
  
     <span data-ttu-id="0fc66-128">轴指定根据位置步骤和上下文节点选择的节点之间的树关系。</span><span class="sxs-lookup"><span data-stu-id="0fc66-128">The axis specifies the tree relationship between the nodes selected by the location step and the context node.</span></span> <span data-ttu-id="0fc66-129">支持 `parent`、`child`、`attribute` 和 `self` 轴。</span><span class="sxs-lookup"><span data-stu-id="0fc66-129">The `parent`, `child`, `attribute`, and `self` axes are supported.</span></span> <span data-ttu-id="0fc66-130">如果在位置路径中指定 `child` 轴，则由查询选择的所有节点均为上下文节点的子级。</span><span class="sxs-lookup"><span data-stu-id="0fc66-130">If a `child` axis is specified in the location path, all the nodes selected by the query are the children of the context node.</span></span> <span data-ttu-id="0fc66-131">如果指定 `parent` 轴，则所选节点为上下文节点的父节点。</span><span class="sxs-lookup"><span data-stu-id="0fc66-131">If a `parent` axis is specified, the node selected is the parent node of the context node.</span></span> <span data-ttu-id="0fc66-132">如果指定 `attribute` 轴，则所选节点为上下文节点的属性。</span><span class="sxs-lookup"><span data-stu-id="0fc66-132">If an `attribute` axis is specified, the nodes selected are the attributes of the context node.</span></span>  
  
-   <span data-ttu-id="0fc66-133">**节点测试**</span><span class="sxs-lookup"><span data-stu-id="0fc66-133">**Node test**</span></span>  
  
     <span data-ttu-id="0fc66-134">节点测试指定根据位置步骤选择的节点类型。</span><span class="sxs-lookup"><span data-stu-id="0fc66-134">A node test specifies the node type selected by the location step.</span></span> <span data-ttu-id="0fc66-135">每个轴（`child`、`parent`、`attribute` 和 `self`）都具有主要节点类型。</span><span class="sxs-lookup"><span data-stu-id="0fc66-135">Every axis (`child`, `parent`, `attribute`, and `self`) has a principal node type.</span></span> <span data-ttu-id="0fc66-136">对于 `attribute` 轴，主体节点类型为 **\<attribute>** 。</span><span class="sxs-lookup"><span data-stu-id="0fc66-136">For the `attribute` axis, the principal node type is **\<attribute>**.</span></span> <span data-ttu-id="0fc66-137">对于 `parent` 、 `child` 和 `self` 轴，主体节点类型为 **\<element>** 。</span><span class="sxs-lookup"><span data-stu-id="0fc66-137">For the `parent`, `child`, and `self` axes, the principal node type is **\<element>**.</span></span>  
  
     <span data-ttu-id="0fc66-138">例如，如果 location 路径指定了**child：： Customer**，则 **\<Customer>** 会选择上下文节点的子元素。</span><span class="sxs-lookup"><span data-stu-id="0fc66-138">For example, if the location path specifies **child::Customer**, the **\<Customer>** element children of the context node are selected.</span></span> <span data-ttu-id="0fc66-139">由于 `child` 轴的 **\<element>** 主体节点类型为，因此，如果客户是节点，则节点测试为 customer **\<element>** 。</span><span class="sxs-lookup"><span data-stu-id="0fc66-139">Because the `child` axis has **\<element>** as its principal node type, the node test, Customer, is TRUE if Customer is an **\<element>** node.</span></span>  
  
-   <span data-ttu-id="0fc66-140">**选择谓词（零个或多个）**</span><span class="sxs-lookup"><span data-stu-id="0fc66-140">**Selection predicates (zero or more)**</span></span>  
  
     <span data-ttu-id="0fc66-141">谓词针对轴筛选节点集。</span><span class="sxs-lookup"><span data-stu-id="0fc66-141">A predicate filters a node-set with respect to an axis.</span></span> <span data-ttu-id="0fc66-142">在 XPath 表达式中指定选择谓词类似于在 SELECT 语句中指定 WHERE 子句。</span><span class="sxs-lookup"><span data-stu-id="0fc66-142">Specifying selection predicates in an XPath expression is similar to specifying a WHERE clause in a SELECT statement.</span></span> <span data-ttu-id="0fc66-143">在方括号之间指定谓词。</span><span class="sxs-lookup"><span data-stu-id="0fc66-143">The predicate is specified between brackets.</span></span> <span data-ttu-id="0fc66-144">应用在选择谓词中指定的测试可以筛选由节点测试返回的节点。</span><span class="sxs-lookup"><span data-stu-id="0fc66-144">Applying the test specified in the selection predicates filters the nodes returned by the node test.</span></span> <span data-ttu-id="0fc66-145">对于要筛选的节点集中的每个节点，将使用该节点作为上下文节点并使用节点集中的节点数作为上下文大小来对谓词表达式求值。</span><span class="sxs-lookup"><span data-stu-id="0fc66-145">For each node in the node-set to be filtered, the predicate expression is evaluated with that node as the context node, with the number of nodes in the node-set as context size.</span></span> <span data-ttu-id="0fc66-146">如果对于该节点谓词表达式求值为 TRUE，则该节点将包含在结果节点集中。</span><span class="sxs-lookup"><span data-stu-id="0fc66-146">If the predicate expression evaluates to TRUE for that node, the node is included in the resulting node-set.</span></span>  
  
     <span data-ttu-id="0fc66-147">位置步骤的语法为轴名称和节点测试（用双冒号 (::) 分隔），后跟零或多个表达式，每个表达式都位于方括号中。</span><span class="sxs-lookup"><span data-stu-id="0fc66-147">The syntax for a location step is the axis name and node test separated by two colons (::), followed by zero or more expressions, each in square brackets.</span></span> <span data-ttu-id="0fc66-148">例如，XPath 表达式 (location 路径) **child：： Customer [ @CustomerID = ' ALFKI ']** 选择上下文节点的所有 **\<Customer>** 元素子级。</span><span class="sxs-lookup"><span data-stu-id="0fc66-148">For example, the XPath expression (location path) **child::Customer[@CustomerID='ALFKI']** selects all the **\<Customer>** element children of the context node.</span></span> <span data-ttu-id="0fc66-149">然后，谓词中的测试应用于节点集，后者仅返回 **\<Customer>** 其**CustomerID**属性的属性值为 "ALFKI" 的元素节点。</span><span class="sxs-lookup"><span data-stu-id="0fc66-149">Then the test in the predicate is applied to the node-set, which returns only the **\<Customer>** element nodes with attribute value 'ALFKI' for its **CustomerID** attribute.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0fc66-150">本节内容</span><span class="sxs-lookup"><span data-stu-id="0fc66-150">In This Section</span></span>  
 [<span data-ttu-id="0fc66-151">&#40;SQLXML 4.0&#41;指定轴</span><span class="sxs-lookup"><span data-stu-id="0fc66-151">Specifying an Axis &#40;SQLXML 4.0&#41;</span></span>](specifying-an-axis-sqlxml-4-0.md)  
 <span data-ttu-id="0fc66-152">提供用于指定轴的示例。</span><span class="sxs-lookup"><span data-stu-id="0fc66-152">Provides examples of specifying an axis.</span></span>  
  
 [<span data-ttu-id="0fc66-153">在位置路径中指定节点测试 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="0fc66-153">Specifying a Node Test in the Location Path &#40;SQLXML 4.0&#41;</span></span>](specifying-a-node-test-in-the-location-path-sqlxml-4-0.md)  
 <span data-ttu-id="0fc66-154">提供用于指定节点测试的示例。</span><span class="sxs-lookup"><span data-stu-id="0fc66-154">Provides examples of specifying a node test.</span></span>  
  
 [<span data-ttu-id="0fc66-155">在位置路径中指定选择谓词 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="0fc66-155">Specifying Selection Predicates in the Location Path &#40;SQLXML 4.0&#41;</span></span>](specifying-selection-predicates-in-the-location-path-sqlxml-4-0.md)  
 <span data-ttu-id="0fc66-156">提供用于指定选择谓词的示例。</span><span class="sxs-lookup"><span data-stu-id="0fc66-156">Provides examples of specifying selection predicates.</span></span>  
  
  
