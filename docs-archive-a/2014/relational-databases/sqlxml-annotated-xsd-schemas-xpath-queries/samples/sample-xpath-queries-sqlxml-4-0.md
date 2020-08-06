---
title: " (SQLXML 4.0) 的示例 XPath 查询 |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- examples [SQLXML], XPath
- sample applications [SQLXML]
- sample XPath queries [SQLXML]
- mapping schema [SQLXML], queries
- XPath queries [SQLXML], samples
ms.assetid: 1595c2d4-0e9c-4969-84c8-a793a32df57d
author: rothja
ms.author: jroth
ms.openlocfilehash: 08ed32433e9bed4cc1542d6700ad73dc96f3c2dc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577486"
---
# <a name="sample-xpath-queries-sqlxml-40"></a><span data-ttu-id="e0a60-102">示例 XPath 查询 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="e0a60-102">Sample XPath Queries (SQLXML 4.0)</span></span>
  <span data-ttu-id="e0a60-103">本节提供 SQLXML 4.0 的 XPath 查询示例。</span><span class="sxs-lookup"><span data-stu-id="e0a60-103">This section provides examples of XPath queries for SQLXML 4.0.</span></span> <span data-ttu-id="e0a60-104">为了便于说明，在使用 ADO 执行的模板中指定这些示例 XPath 查询。</span><span class="sxs-lookup"><span data-stu-id="e0a60-104">For illustration purposes, these example XPath queries are specified in a template executed using ADO.</span></span> <span data-ttu-id="e0a60-105">因此，您必须使用映射架构文件 SampleSchema1.xml，本节中也提供了此文件。</span><span class="sxs-lookup"><span data-stu-id="e0a60-105">Therefore, you must use a mapping schema file, SampleSchema1.xml, which is also provided in this section.</span></span> <span data-ttu-id="e0a60-106">将此文件保存在存储模板的目录中。</span><span class="sxs-lookup"><span data-stu-id="e0a60-106">Save this file in the directory where your templates are stored.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e0a60-107">本节中的示例查询按照查询执行的 XPath 操作的类型进行分组。</span><span class="sxs-lookup"><span data-stu-id="e0a60-107">The sample queries in this section are grouped by the type of XPath operation that is performed by the query.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e0a60-108">本节内容</span><span class="sxs-lookup"><span data-stu-id="e0a60-108">In This Section</span></span>  
 [<span data-ttu-id="e0a60-109">用于 XPath 示例的带批注的 XSD 架构示例 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="e0a60-109">Sample Annotated XSD Schema for XPath Examples &#40;SQLXML 4.0&#41;</span></span>](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md)  
 <span data-ttu-id="e0a60-110">将此文件与本节中提供的 XPath 查询示例一起使用。</span><span class="sxs-lookup"><span data-stu-id="e0a60-110">Use this file with the XPath query examples provided in this section.</span></span>  
  
 [<span data-ttu-id="e0a60-111">&#40;SQLXML 4.0&#41;在 XPath 查询中指定轴</span><span class="sxs-lookup"><span data-stu-id="e0a60-111">Specifying Axes in XPath Queries &#40;SQLXML 4.0&#41;</span></span>](specifying-axes-in-xpath-queries-sqlxml-4-0.md)  
 <span data-ttu-id="e0a60-112">说明如何在 XPath 查询中指定轴。</span><span class="sxs-lookup"><span data-stu-id="e0a60-112">Illustrates how axes are specified in XPath queries.</span></span>  
  
 [<span data-ttu-id="e0a60-113">&#40;SQLXML 4.0&#41;在 XPath 查询中指定布尔值谓词</span><span class="sxs-lookup"><span data-stu-id="e0a60-113">Specifying Boolean-Valued Predicates in XPath Queries &#40;SQLXML 4.0&#41;</span></span>](specifying-boolean-valued-predicates-in-xpath-queries-sqlxml-4-0.md)  
 <span data-ttu-id="e0a60-114">说明如何在 XPath 查询中指定布尔值谓词。</span><span class="sxs-lookup"><span data-stu-id="e0a60-114">Illustrates how Boolean-valued predicates are specified in XPath queries.</span></span>  
  
 [<span data-ttu-id="e0a60-115">&#40;SQLXML 4.0&#41;在 XPath 查询中指定关系运算符</span><span class="sxs-lookup"><span data-stu-id="e0a60-115">Specifying Relational Operators in XPath Queries &#40;SQLXML 4.0&#41;</span></span>](specifying-relational-operators-in-xpath-queries-sqlxml-4-0.md)  
 <span data-ttu-id="e0a60-116">说明如何在 XPath 查询中指定关系运算符。</span><span class="sxs-lookup"><span data-stu-id="e0a60-116">Illustrates how relational operators are specified in XPath queries.</span></span>  
  
 [<span data-ttu-id="e0a60-117">&#40;SQLXML 4.0&#41;在 XPath 查询中指定算术运算符</span><span class="sxs-lookup"><span data-stu-id="e0a60-117">Specifying Arithmetic Operators in XPath Queries &#40;SQLXML 4.0&#41;</span></span>](specifying-arithmetic-operators-in-xpath-queries-sqlxml-4-0.md)  
 <span data-ttu-id="e0a60-118">说明如何在 XPath 查询中指定算术运算符。</span><span class="sxs-lookup"><span data-stu-id="e0a60-118">Illustrates how arithmetic operators are specified in XPath queries.</span></span>  
  
 [<span data-ttu-id="e0a60-119">&#40;SQLXML 4.0&#41;在 XPath 查询中指定显式转换函数</span><span class="sxs-lookup"><span data-stu-id="e0a60-119">Specifying Explicit Conversion Functions in XPath Queries &#40;SQLXML 4.0&#41;</span></span>](specifying-explicit-conversion-functions-in-xpath-queries-sqlxml-4-0.md)  
 <span data-ttu-id="e0a60-120">说明如何在 XPath 查询中指定显式转换函数。</span><span class="sxs-lookup"><span data-stu-id="e0a60-120">Illustrates how explicit conversion functions are specified in XPath queries.</span></span>  
  
 [<span data-ttu-id="e0a60-121">在 &#40;SQLXML 4.0&#41;的 XPath 查询中指定布尔运算符</span><span class="sxs-lookup"><span data-stu-id="e0a60-121">Specifying Boolean Operators in XPath Queries &#40;SQLXML 4.0&#41;</span></span>](specifying-boolean-operators-in-xpath-queries-sqlxml-4-0.md)  
 <span data-ttu-id="e0a60-122">说明如何在 XPath 查询中指定布尔运算符。</span><span class="sxs-lookup"><span data-stu-id="e0a60-122">Illustrates how Boolean operators are specified in XPath queries.</span></span>  
  
 [<span data-ttu-id="e0a60-123">&#40;SQLXML 4.0&#41;在 XPath 查询中指定布尔函数</span><span class="sxs-lookup"><span data-stu-id="e0a60-123">Specifying Boolean Functions in XPath Queries &#40;SQLXML 4.0&#41;</span></span>](specifying-boolean-functions-in-xpath-queries-sqlxml-4-0.md)  
 <span data-ttu-id="e0a60-124">说明如何在 XPath 查询中指定布尔函数。</span><span class="sxs-lookup"><span data-stu-id="e0a60-124">Illustrates how Boolean functions are specified in XPath queries.</span></span>  
  
 [<span data-ttu-id="e0a60-125">在 &#40;SQLXML 4.0&#41;的 XPath 查询中指定 XPath 变量</span><span class="sxs-lookup"><span data-stu-id="e0a60-125">Specifying XPath Variables in XPath Queries &#40;SQLXML 4.0&#41;</span></span>](specifying-xpath-variables-in-xpath-queries-sqlxml-4-0.md)  
 <span data-ttu-id="e0a60-126">说明如何在 XPath 查询中指定 XPath 变量。</span><span class="sxs-lookup"><span data-stu-id="e0a60-126">Illustrates how XPath variables are specified in XPath queries.</span></span>  
  
  
