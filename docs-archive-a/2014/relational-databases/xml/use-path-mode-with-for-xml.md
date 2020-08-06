---
title: 将 PATH 模式与 FOR XML 一起使用 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- PATH FOR XML mode
- characters [SQL Server], XML
- aliases [SQL Server], XML
- FOR XML clause, PATH mode
- FOR XML PATH mode
- column names [SQL Server]
- XPath queries [SQL Server]
ms.assetid: a685a9ad-3d28-4596-aa72-119202df3976
author: rothja
ms.author: jroth
ms.openlocfilehash: ce0cf811f1e610d14a94993b54c51ea079f613e9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587257"
---
# <a name="use-path-mode-with-for-xml"></a><span data-ttu-id="1b8c0-102">将 PATH 模式与 FOR XML 一起使用</span><span class="sxs-lookup"><span data-stu-id="1b8c0-102">Use PATH Mode with FOR XML</span></span>
  <span data-ttu-id="1b8c0-103">如 [使用 FOR XML 构造 XML](for-xml-sql-server.md)中所述，PATH 模式提供了一种较简单的方法来混合元素和属性。</span><span class="sxs-lookup"><span data-stu-id="1b8c0-103">As described in [Constructing XML Using FOR XML](for-xml-sql-server.md), the PATH mode provides a simpler way to mix elements and attributes.</span></span> <span data-ttu-id="1b8c0-104">PATH 模式还是一种用于引入附加嵌套来表示复杂属性的较简单的方法。</span><span class="sxs-lookup"><span data-stu-id="1b8c0-104">PATH mode is also a simpler way to introduce additional nesting for representing complex properties.</span></span> <span data-ttu-id="1b8c0-105">尽管您可以使用 FOR XML EXPLICIT 模式查询从行集构造这种 XML，但 PATH 模式为可能很麻烦的 EXPLICIT 模式查询提供了一种较简单的替代方法。</span><span class="sxs-lookup"><span data-stu-id="1b8c0-105">You can use FOR XML EXPLICIT mode queries to construct such XML from a rowset, but the PATH mode provides a simpler alternative to the potentially cumbersome EXPLICIT mode queries.</span></span> <span data-ttu-id="1b8c0-106">通过 PATH 模式，以及用于编写嵌套 FOR XML 查询的功能和返回 **xml** 类型实例的 TYPE 指令，您可以编写简单的查询。</span><span class="sxs-lookup"><span data-stu-id="1b8c0-106">PATH mode, together with the ability to write nested FOR XML queries and the TYPE directive to return **xml** type instances, allows you to write queries with less complexity.</span></span>  
  
 <span data-ttu-id="1b8c0-107">在 PATH 模式中，列名或列别名被作为 XPath 表达式来处理。</span><span class="sxs-lookup"><span data-stu-id="1b8c0-107">In PATH mode, column names or column aliases are treated as XPath expressions.</span></span> <span data-ttu-id="1b8c0-108">这些表达式指明了如何将值映射到 XML。</span><span class="sxs-lookup"><span data-stu-id="1b8c0-108">These expressions indicate how the values are being mapped to XML.</span></span> <span data-ttu-id="1b8c0-109">每个 XPath 表达式都是一个相对 XPath，它提供了项类型（例如属性、元素和标量值）以及将相对于行元素而生成的节点的名称和层次结构。</span><span class="sxs-lookup"><span data-stu-id="1b8c0-109">Each XPath expression is a relative XPath that provides the item type., such as the attribute, element, and scalar value, and the name and hierarchy of the node that will be generated relative to the row element.</span></span>  
  
 <span data-ttu-id="1b8c0-110">本节介绍了如何在各种条件下映射行集中的列，并提供了相关示例。</span><span class="sxs-lookup"><span data-stu-id="1b8c0-110">This section describes mapping columns in a rowset under various conditions, and provides examples.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1b8c0-111">本节内容</span><span class="sxs-lookup"><span data-stu-id="1b8c0-111">In This Section</span></span>  
  
-   [<span data-ttu-id="1b8c0-112">没有名称的列</span><span class="sxs-lookup"><span data-stu-id="1b8c0-112">Columns without a Name</span></span>](columns-without-a-name.md)  
  
-   [<span data-ttu-id="1b8c0-113">具有名称的列</span><span class="sxs-lookup"><span data-stu-id="1b8c0-113">Columns with a Name</span></span>](columns-with-a-name.md)  
  
-   [<span data-ttu-id="1b8c0-114">名称指定为通配符的列</span><span class="sxs-lookup"><span data-stu-id="1b8c0-114">Columns with a Name Specified as a Wildcard Character</span></span>](columns-with-a-name-specified-as-a-wildcard-character.md)  
  
-   [<span data-ttu-id="1b8c0-115">列名为 XPath 节点测试的列</span><span class="sxs-lookup"><span data-stu-id="1b8c0-115">Columns with the Name of an XPath Node Test</span></span>](columns-with-the-name-of-an-xpath-node-test.md)  
  
-   [<span data-ttu-id="1b8c0-116">带有指定为 data() 的路径的列名</span><span class="sxs-lookup"><span data-stu-id="1b8c0-116">Column Names with the Path Specified as data&#40;&#41;</span></span>](column-names-with-the-path-specified-as-data.md)  
  
-   [<span data-ttu-id="1b8c0-117">默认情况下包含 Null 值的列</span><span class="sxs-lookup"><span data-stu-id="1b8c0-117">Columns that Contain a Null Value By Default</span></span>](columns-that-contain-a-null-value-by-default.md)  
  
-   [<span data-ttu-id="1b8c0-118">PATH 模式中的命名空间支持</span><span class="sxs-lookup"><span data-stu-id="1b8c0-118">Namespace Support in PATH Mode</span></span>](namespace-support-in-path-mode.md)  
  
-   [<span data-ttu-id="1b8c0-119">示例：使用 PATH 模式</span><span class="sxs-lookup"><span data-stu-id="1b8c0-119">Examples: Using PATH Mode</span></span>](examples-using-path-mode.md)  
  
## <a name="see-also"></a><span data-ttu-id="1b8c0-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1b8c0-120">See Also</span></span>  
 <span data-ttu-id="1b8c0-121">[使用 WITH XMLNAMESPACES 将命名空间添加到查询](add-namespaces-to-queries-with-with-xmlnamespaces.md) </span><span class="sxs-lookup"><span data-stu-id="1b8c0-121">[Add Namespaces to Queries with WITH XMLNAMESPACES](add-namespaces-to-queries-with-with-xmlnamespaces.md) </span></span>  
 <span data-ttu-id="1b8c0-122">[SELECT (Transact-SQL)](/sql/t-sql/queries/select-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="1b8c0-122">[SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql) </span></span>  
 [<span data-ttu-id="1b8c0-123">FOR XML (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="1b8c0-123">FOR XML &#40;SQL Server&#41;</span></span>](for-xml-sql-server.md)  
  
  
