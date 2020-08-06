---
title: 将 RAW 模式与 FOR XML 一起使用 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- FOR XML RAW mode
- XMLSCHEMA option
- FOR XML clause, RAW mode
- RAW FOR XML mode
- ELEMENTS directive
- RAW mode
- XMLDATA option
ms.assetid: 02c1bc0b-760c-4589-9ab1-6927c6d9c734
author: rothja
ms.author: jroth
ms.openlocfilehash: b2908a98336ec8a6e12029ad471f22a33d7a4dcf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692301"
---
# <a name="use-raw-mode-with-for-xml"></a><span data-ttu-id="ef4db-102">将 RAW 模式与 FOR XML 一起使用</span><span class="sxs-lookup"><span data-stu-id="ef4db-102">Use RAW Mode with FOR XML</span></span>
  <span data-ttu-id="ef4db-103">RAW 模式可将查询结果集中的每一行转换为带有通用标识符 \<row> 或可能提供元素名称的 XML 元素。</span><span class="sxs-lookup"><span data-stu-id="ef4db-103">RAW mode transforms each row in the query result set into an XML element that has the generic identifier \<row>, or the optionally provided element name.</span></span> <span data-ttu-id="ef4db-104">默认情况下，非 NULL 行集中的每列值都将映射到 \<row> 元素的一个属性。</span><span class="sxs-lookup"><span data-stu-id="ef4db-104">By default, each column value in the rowset that is not NULL is mapped to an attribute of the \<row> element.</span></span> <span data-ttu-id="ef4db-105">如果将 ELEMENTS 指令添加到 FOR XML 子句，则每列值都将映射到 \<row> 元素的子元素。</span><span class="sxs-lookup"><span data-stu-id="ef4db-105">If the ELEMENTS directive is added to the FOR XML clause, each column value is mapped to a subelement of the \<row> element.</span></span> <span data-ttu-id="ef4db-106">指定 ELEMENTS 指令之后，您还可以选择性地指定 XSINIL 选项以将结果集中的 NULL 列值映射到具有 xsi:nil=`"`true`"`属性的元素。</span><span class="sxs-lookup"><span data-stu-id="ef4db-106">Together with the ELEMENTS directive, you can optionally specify the XSINIL option to map NULL column values in the result set to an element that has the attribute, xsi:nil=`"`true`"`.</span></span>  
  
 <span data-ttu-id="ef4db-107">您可以请求返回所产生的 XML 的架构。</span><span class="sxs-lookup"><span data-stu-id="ef4db-107">You can request a schema for the resulting XML.</span></span> <span data-ttu-id="ef4db-108">指定 XMLDATA 选项将返回内联 XDR 架构。</span><span class="sxs-lookup"><span data-stu-id="ef4db-108">Specifying the XMLDATA option returns an in-line XDR schema.</span></span> <span data-ttu-id="ef4db-109">指定 XMLSCHEMA 选项将返回内联 XSD 架构。</span><span class="sxs-lookup"><span data-stu-id="ef4db-109">Specifying the XMLSCHEMA option returns an in-line XSD schema.</span></span> <span data-ttu-id="ef4db-110">该架构显示在数据的开头。</span><span class="sxs-lookup"><span data-stu-id="ef4db-110">The schema appears at the start of the data.</span></span> <span data-ttu-id="ef4db-111">在结果中，每个顶级元素都引用架构命名空间。</span><span class="sxs-lookup"><span data-stu-id="ef4db-111">In the result, the schema namespace reference is repeated for every top-level element.</span></span>  
  
 <span data-ttu-id="ef4db-112">必须在 FOR XML 子句中指定 BINARY BASE64 选项以使用 base64 编码格式返回二进制数据。</span><span class="sxs-lookup"><span data-stu-id="ef4db-112">The BINARY BASE64 option must be specified in the FOR XML clause to return the binary data in base64-encoded format.</span></span> <span data-ttu-id="ef4db-113">在 RAW 模式下，如果不指定 BINARY BASE64 选项就检索二进制数据，将导致错误。</span><span class="sxs-lookup"><span data-stu-id="ef4db-113">In RAW mode, retrieving binary data without specifying the BINARY BASE64 option will result in an error.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ef4db-114">本节内容</span><span class="sxs-lookup"><span data-stu-id="ef4db-114">In This Section</span></span>  
 <span data-ttu-id="ef4db-115">本部分包含以下示例：</span><span class="sxs-lookup"><span data-stu-id="ef4db-115">This section contains the following examples:</span></span>  
  
-   [<span data-ttu-id="ef4db-116">示例：以 XML 形式检索产品型号信息</span><span class="sxs-lookup"><span data-stu-id="ef4db-116">Example: Retrieving Product Model Information as XML</span></span>](example-retrieving-product-model-information-as-xml.md)  
  
-   [<span data-ttu-id="ef4db-117">示例：指定带有 ELEMENTS 指令的 XSINIL</span><span class="sxs-lookup"><span data-stu-id="ef4db-117">Example: Specifying XSINIL with the ELEMENTS Directive</span></span>](example-specifying-xsinil-with-the-elements-directive.md)  
  
-   [<span data-ttu-id="ef4db-118">示例：使用 XMLDATA 和 XMLSCHEMA 选项请求架构作为结果</span><span class="sxs-lookup"><span data-stu-id="ef4db-118">Example: Requesting Schemas as Results with the XMLDATA and XMLSCHEMA Options</span></span>](example-requesting-schemas-as-results-with-the-xmldata-and-xmlschema-options.md)  
  
-   [<span data-ttu-id="ef4db-119">示例：检索二进制数据</span><span class="sxs-lookup"><span data-stu-id="ef4db-119">Example: Retrieving Binary Data</span></span>](example-retrieving-binary-data.md)  
  
-   [<span data-ttu-id="ef4db-120">示例：重命名 &#60;row&#62; 元素</span><span class="sxs-lookup"><span data-stu-id="ef4db-120">Example: Renaming the &#60;row&#62; Element</span></span>](example-renaming-the-row-element.md)  
  
-   [<span data-ttu-id="ef4db-121">示例：为 FOR XML 生成的 XML 指定根元素</span><span class="sxs-lookup"><span data-stu-id="ef4db-121">Example: Specifying a Root Element for the XML Generated by FOR XML</span></span>](example-specifying-a-root-element-for-the-xml-generated-by-for-xml.md)  
  
-   [<span data-ttu-id="ef4db-122">示例：查询 XMLType 列</span><span class="sxs-lookup"><span data-stu-id="ef4db-122">Example: Querying XMLType Columns</span></span>](example-querying-xmltype-columns.md)  
  
## <a name="see-also"></a><span data-ttu-id="ef4db-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ef4db-123">See Also</span></span>  
 <span data-ttu-id="ef4db-124">[使用 WITH XMLNAMESPACES 将命名空间添加到查询](add-namespaces-to-queries-with-with-xmlnamespaces.md) </span><span class="sxs-lookup"><span data-stu-id="ef4db-124">[Add Namespaces to Queries with WITH XMLNAMESPACES](add-namespaces-to-queries-with-with-xmlnamespaces.md) </span></span>  
 <span data-ttu-id="ef4db-125">[将 AUTO 模式与 FOR XML 一起使用](use-auto-mode-with-for-xml.md) </span><span class="sxs-lookup"><span data-stu-id="ef4db-125">[Use AUTO Mode with FOR XML](use-auto-mode-with-for-xml.md) </span></span>  
 <span data-ttu-id="ef4db-126">[将 EXPLICIT 模式与 FOR XML 一起使用](use-explicit-mode-with-for-xml.md) </span><span class="sxs-lookup"><span data-stu-id="ef4db-126">[Use EXPLICIT Mode with FOR XML](use-explicit-mode-with-for-xml.md) </span></span>  
 <span data-ttu-id="ef4db-127">[将 PATH 模式与 FOR XML 一起使用](use-path-mode-with-for-xml.md) </span><span class="sxs-lookup"><span data-stu-id="ef4db-127">[Use PATH Mode with FOR XML](use-path-mode-with-for-xml.md) </span></span>  
 <span data-ttu-id="ef4db-128">[SELECT (Transact-SQL)](/sql/t-sql/queries/select-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ef4db-128">[SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql) </span></span>  
 [<span data-ttu-id="ef4db-129">FOR XML (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="ef4db-129">FOR XML &#40;SQL Server&#41;</span></span>](../xml/for-xml-sql-server.md)  
  
  
