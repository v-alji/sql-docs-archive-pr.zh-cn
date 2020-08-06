---
title: 使用 BINARY BASE64 选项 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- AUTO FOR XML mode, BINARY BASE64 option
ms.assetid: 86a7bb85-7f83-412a-b775-d2c379702fe9
author: rothja
ms.author: jroth
ms.openlocfilehash: 090d6a91ee56707a4eb1d545aa5a05bc25999fab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692291"
---
# <a name="use-the-binary-base64-option"></a><span data-ttu-id="b0381-102">使用 BINARY BASE64 选项</span><span class="sxs-lookup"><span data-stu-id="b0381-102">Use the BINARY BASE64 Option</span></span>
  <span data-ttu-id="b0381-103">如果查询中指定了 BINARY BASE64 选项，则以 base64 编码格式返回二进制数据。</span><span class="sxs-lookup"><span data-stu-id="b0381-103">If the BINARY BASE64 option is specified in the query, the binary data is returned in base64 encoding format.</span></span> <span data-ttu-id="b0381-104">默认情况下，如果未指定 BINARY BASE64 选项，则 AUTO 模式支持二进制数据的 URL 编码。</span><span class="sxs-lookup"><span data-stu-id="b0381-104">By default, if the BINARY BASE64 option is not specified, AUTO mode supports URL encoding of binary data.</span></span> <span data-ttu-id="b0381-105">也就是说，不返回二进制数据，而返回执行查询的数据库的虚拟根目录的相对 URL 的引用。</span><span class="sxs-lookup"><span data-stu-id="b0381-105">That is, instead of binary data, a reference to a relative URL to the virtual root of the database where the query was executed is returned.</span></span> <span data-ttu-id="b0381-106">通过使用 SQLXML ISAPI dbobject 查询，可在后续操作中利用此引用访问实际二进制数据。</span><span class="sxs-lookup"><span data-stu-id="b0381-106">This reference can be used to access the actual binary data in subsequent operations by using the SQLXML ISAPI dbobject query.</span></span> <span data-ttu-id="b0381-107">查询必须提供足够的信息（如主键列），才能标识图像。</span><span class="sxs-lookup"><span data-stu-id="b0381-107">The query must provide enough information, such as primary key columns, to identify the image.</span></span>  
  
 <span data-ttu-id="b0381-108">在指定查询的过程中，如果对视图的二进制列使用了别名，将在二进制数据的 URL 编码中返回别名。</span><span class="sxs-lookup"><span data-stu-id="b0381-108">In specifying a query, if an alias is used for the binary column of the view, the alias is returned in the URL encoding of the binary data.</span></span> <span data-ttu-id="b0381-109">在后续操作中，别名没有意义，也不能用 URL 编码检索图像。</span><span class="sxs-lookup"><span data-stu-id="b0381-109">In subsequent operations, the alias is meaningless, and the URL encoding cannot be used to retrieve the image.</span></span> <span data-ttu-id="b0381-110">因此，在使用 FOR XML AUTO 模式查询视图时不要使用别名。</span><span class="sxs-lookup"><span data-stu-id="b0381-110">Therefore, do not use aliases when querying a view using FOR XML AUTO mode.</span></span>  
  
 <span data-ttu-id="b0381-111">例如，在 SELECT 查询中，将任意列转换为二进制大型对象 (BLOB) 后，由于该列丢失了其关联的表名和列名，它将成为临时实体。</span><span class="sxs-lookup"><span data-stu-id="b0381-111">For example, in a SELECT query, casting any column to a binary large object (BLOB) makes it a temporary entity in that it loses its associated table name and column name.</span></span> <span data-ttu-id="b0381-112">这将导致 AUTO 模式查询产生错误，因为它不知道将该值放在 XML 层次结构中的什么位置。</span><span class="sxs-lookup"><span data-stu-id="b0381-112">This causes AUTO mode queries to generate an error, because it does not know where to put this value in the XML hierarchy.</span></span> <span data-ttu-id="b0381-113">例如：</span><span class="sxs-lookup"><span data-stu-id="b0381-113">For example:</span></span>  
  
```  
CREATE TABLE MyTable (Col1 int PRIMARY KEY, Col2 binary)  
INSERT INTO MyTable VALUES (1, 0x7);  
```  
  
 <span data-ttu-id="b0381-114">由于会转换为二进制大型对象 (BLOB)，因此以下查询将产生错误：</span><span class="sxs-lookup"><span data-stu-id="b0381-114">This query produces an error, because of the casting to a binary large object (BLOB):</span></span>  
  
```  
SELECT Col1,  
CAST(Col2 as image) as Col2  
FROM MyTable  
FOR XML AUTO;  
```  
  
 <span data-ttu-id="b0381-115">解决方案是将 BINARY BASE64 选项添加到 FOR XML 子句中。</span><span class="sxs-lookup"><span data-stu-id="b0381-115">The solution is to add the BINARY BASE64 option to the FOR XML clause.</span></span> <span data-ttu-id="b0381-116">如果删除转换，此查询将生成预期的结果：</span><span class="sxs-lookup"><span data-stu-id="b0381-116">If you remove the casting, the query produces the results as expected:</span></span>  
  
```  
SELECT Col1,  
CAST(Col2 as image) as Col2  
FROM MyTable  
FOR XML AUTO, BINARY BASE64;  
```  
  
 <span data-ttu-id="b0381-117">结果如下：</span><span class="sxs-lookup"><span data-stu-id="b0381-117">This is the result:</span></span>  
  
```  
<MyTable Col1="1" Col2="Bw==" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="b0381-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b0381-118">See Also</span></span>  
 [<span data-ttu-id="b0381-119">将 AUTO 模式与 FOR XML 一起使用</span><span class="sxs-lookup"><span data-stu-id="b0381-119">Use AUTO Mode with FOR XML</span></span>](use-auto-mode-with-for-xml.md)  
  
  
