---
title: 在位置路径中指定节点测试 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XPath queries [SQLXML], location paths
- principal node types [SQLXML]
- node tests [SQLXML]
- location path for XPath query
ms.assetid: f46c30bf-1e24-4435-9ac2-f8ba43a8ff94
author: rothja
ms.author: jroth
ms.openlocfilehash: 9d8535154f4b481c8a47bfdb8b801e3136a1ef0f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587285"
---
# <a name="specifying-a-node-test-in-the-location-path-sqlxml-40"></a><span data-ttu-id="d6caf-102">在位置路径中指定节点测试 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="d6caf-102">Specifying a Node Test in the Location Path (SQLXML 4.0)</span></span>
  <span data-ttu-id="d6caf-103">节点测试指定根据位置步骤选择的节点类型。</span><span class="sxs-lookup"><span data-stu-id="d6caf-103">A node test specifies the node type selected by the location step.</span></span> <span data-ttu-id="d6caf-104">每个轴（`child`、`parent`、`attribute` 或 `self`）都具有主要节点类型。</span><span class="sxs-lookup"><span data-stu-id="d6caf-104">Every axis (`child`, `parent`, `attribute`, or `self`) has a principal node type.</span></span> <span data-ttu-id="d6caf-105">对于 `attribute` 轴，主体节点类型为 **\<attribute>** 。</span><span class="sxs-lookup"><span data-stu-id="d6caf-105">For the `attribute` axis, the principal node type is **\<attribute>**.</span></span> <span data-ttu-id="d6caf-106">对于 `parent` 、 `child` 和 `self` 轴，主体节点类型为 **\<element>** 。</span><span class="sxs-lookup"><span data-stu-id="d6caf-106">For the `parent`, `child`, and `self` axes, the principal node type is **\<element>**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d6caf-107">不支持通配符节点测试 \*（例如 `child::*`）。</span><span class="sxs-lookup"><span data-stu-id="d6caf-107">The wildcard node test \* (for example, `child::*`) is not supported.</span></span>  
  
## <a name="node-test-example-1"></a><span data-ttu-id="d6caf-108">节点测试：示例1</span><span class="sxs-lookup"><span data-stu-id="d6caf-108">Node Test: Example 1</span></span>  
 <span data-ttu-id="d6caf-109">位置路径 `child::Customer` 选择 **\<Customer>** 上下文节点的子元素。</span><span class="sxs-lookup"><span data-stu-id="d6caf-109">The location path `child::Customer` selects **\<Customer>** element children of the context node.</span></span>  
  
 <span data-ttu-id="d6caf-110">在本示例中，`child` 是轴，`Customer` 是节点测试。</span><span class="sxs-lookup"><span data-stu-id="d6caf-110">In this example, `child` is the axis and `Customer` is the node test.</span></span> <span data-ttu-id="d6caf-111">轴的主体节点类型 `child` 为 **\<element>** 。</span><span class="sxs-lookup"><span data-stu-id="d6caf-111">The principal node type for the `child` axis is **\<element>**.</span></span> <span data-ttu-id="d6caf-112">因此，如果节点是节点，则节点测试为 TRUE **\<Customer>** **\<element>** 。</span><span class="sxs-lookup"><span data-stu-id="d6caf-112">Therefore, the node test is TRUE if the **\<Customer>** node is an **\<element>** node.</span></span> <span data-ttu-id="d6caf-113">如果上下文节点没有任何 **\<Customer>** 子级，则返回一组空节点。</span><span class="sxs-lookup"><span data-stu-id="d6caf-113">If the context node has no **\<Customer>** children, an empty set of nodes is returned.</span></span>  
  
## <a name="node-test-example-2"></a><span data-ttu-id="d6caf-114">节点测试：示例 2</span><span class="sxs-lookup"><span data-stu-id="d6caf-114">Node Test: Example 2</span></span>  
 <span data-ttu-id="d6caf-115">位置路径 `attribute::CustomerID` 选择上下文节点的**CustomerID**属性。</span><span class="sxs-lookup"><span data-stu-id="d6caf-115">The location path `attribute::CustomerID` selects the **CustomerID** attribute of the context node.</span></span>  
  
 <span data-ttu-id="d6caf-116">在此示例中， `attribute` 是轴， `CustomerID` 是节点测试。</span><span class="sxs-lookup"><span data-stu-id="d6caf-116">In the example, `attribute` is the axis and `CustomerID` is the node test.</span></span> <span data-ttu-id="d6caf-117">轴的主要节点类型 `attribute` 为 **\<attribute>** 。</span><span class="sxs-lookup"><span data-stu-id="d6caf-117">The principal node type of the `attribute` axis is **\<attribute>**.</span></span> <span data-ttu-id="d6caf-118">因此，如果**CustomerID**是节点，则节点测试为 TRUE **\<attribute>** 。</span><span class="sxs-lookup"><span data-stu-id="d6caf-118">Therefore, the node test is TRUE if **CustomerID** is an **\<attribute>** node.</span></span> <span data-ttu-id="d6caf-119">如果上下文节点没有**CustomerID**，则返回一组空节点。</span><span class="sxs-lookup"><span data-stu-id="d6caf-119">If the context node has no **CustomerID**, an empty set of nodes is returned.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d6caf-120">在此 XPath 实现中，如果定位步骤引用 **\<element>** **\<attribute>** 架构中未声明的或类型，则会生成错误。</span><span class="sxs-lookup"><span data-stu-id="d6caf-120">In this implementation of XPath, if a location step refers to an **\<element>** or an **\<attribute>** type that is not declared in the schema, an error is generated.</span></span> <span data-ttu-id="d6caf-121">这与 MSXML 中的 XPath 实现不同，在 MSXML 中返回空节点集。</span><span class="sxs-lookup"><span data-stu-id="d6caf-121">This is different from the implementation of XPath in MSXML, which returns an empty node set.</span></span>  
  
## <a name="abbreviated-syntax-for-the-axes"></a><span data-ttu-id="d6caf-122">轴的缩写语法</span><span class="sxs-lookup"><span data-stu-id="d6caf-122">Abbreviated Syntax for the Axes</span></span>  
 <span data-ttu-id="d6caf-123">支持以下位置路径的缩写语法：</span><span class="sxs-lookup"><span data-stu-id="d6caf-123">The following abbreviated syntax for the location path is supported:</span></span>  
  
-   <span data-ttu-id="d6caf-124">`attribute::` 可缩写为 `@`。</span><span class="sxs-lookup"><span data-stu-id="d6caf-124">`attribute::` can be abbreviated to `@`.</span></span>  
  
     <span data-ttu-id="d6caf-125">位置路径 `Customer[@CustomerID="ALFKI"]` 与 `child::Customer[attribute::CustomerID="ALFKI"]` 相同。</span><span class="sxs-lookup"><span data-stu-id="d6caf-125">The location path `Customer[@CustomerID="ALFKI"]` is the same as `child::Customer[attribute::CustomerID="ALFKI"]`.</span></span>  
  
-   <span data-ttu-id="d6caf-126">可以从位置步骤中省略 `child::`。</span><span class="sxs-lookup"><span data-stu-id="d6caf-126">`child::` can be omitted from a location step.</span></span>  
  
     <span data-ttu-id="d6caf-127">因此，`child` 为默认轴。</span><span class="sxs-lookup"><span data-stu-id="d6caf-127">Thus, `child` is the default axis.</span></span> <span data-ttu-id="d6caf-128">位置路径 `Customer/Order` 与 `child::Customer/child::Order` 相同。</span><span class="sxs-lookup"><span data-stu-id="d6caf-128">The location path `Customer/Order` is the same as `child::Customer/child::Order`.</span></span>  
  
-   <span data-ttu-id="d6caf-129">`self::node()` 可缩写为一个句点 (.)，`parent::node()` 可缩写为两个句点 (..)。</span><span class="sxs-lookup"><span data-stu-id="d6caf-129">`self::node()` can be abbreviated to one period (.), and `parent::node()` can be abbreviated to two periods (..).</span></span>  
  
  
