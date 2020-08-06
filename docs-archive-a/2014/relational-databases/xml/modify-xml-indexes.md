---
title: 修改 XML 索引 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- XML indexes [SQL Server], modifying
- modifying indexes
ms.assetid: 24d50fe1-c6ec-49e6-91a3-9791851ba53d
author: rothja
ms.author: jroth
ms.openlocfilehash: c5c67470fc9aaaeefe49e5ccb1a8602e082c4054
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687556"
---
# <a name="modify-xml-indexes"></a><span data-ttu-id="a7dd5-102">修改 XML 索引</span><span class="sxs-lookup"><span data-stu-id="a7dd5-102">Modify XML Indexes</span></span>
  <span data-ttu-id="a7dd5-103">[ALTER INDEX (Transact-SQL)](/sql/t-sql/statements/alter-index-transact-sql)[!INCLUDE[tsql](../../includes/tsql-md.md)] DDL 语句可用于修改现有的 XML 和非 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="a7dd5-103">The [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql)[!INCLUDE[tsql](../../includes/tsql-md.md)] DDL statement can be used to modify existing XML and non-XML indexes.</span></span> <span data-ttu-id="a7dd5-104">但是，并非所有的 ALTER INDEX 选项都适用于 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="a7dd5-104">However, not all the ALTER INDEX options are available to XML indexes.</span></span> <span data-ttu-id="a7dd5-105">修改 XML 索引时以下选项不可用：</span><span class="sxs-lookup"><span data-stu-id="a7dd5-105">The following options are not valid when modifying XML indexes:</span></span>  
  
-   <span data-ttu-id="a7dd5-106">对于 XML 索引，重新生成和设置选项 IGNORE_DUP_KEY 无效。</span><span class="sxs-lookup"><span data-stu-id="a7dd5-106">The rebuild and set option IGNORE_DUP_KEY is not valid for XML indexes.</span></span> <span data-ttu-id="a7dd5-107">对于辅助 XML 索引，重新生成选项 ONLINE 必须设置为 OFF。</span><span class="sxs-lookup"><span data-stu-id="a7dd5-107">The rebuild option ONLINE must be set to OFF for secondary XML indexes.</span></span> <span data-ttu-id="a7dd5-108">在 ALTER INDEX 语句中，不允许 DROP_EXISTING 选项。</span><span class="sxs-lookup"><span data-stu-id="a7dd5-108">The option DROP_EXISTING is not permitted in the ALTER INDEX statement.</span></span>  
  
-   <span data-ttu-id="a7dd5-109">对用户表中的主键约束进行的修改不会自动传播到 XML 索引中。</span><span class="sxs-lookup"><span data-stu-id="a7dd5-109">The modifications of the primary key constraint in the user table are not automatically propagated to XML indexes.</span></span> <span data-ttu-id="a7dd5-110">用户必须首先删除 XML 索引，然后再重新创建它们。</span><span class="sxs-lookup"><span data-stu-id="a7dd5-110">The user must drop the XML indexes first and then re-create them.</span></span>  
  
-   <span data-ttu-id="a7dd5-111">如果指定了 ALTER INDEX ALL，则它将应用于非 XML 索引和 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="a7dd5-111">If ALTER INDEX ALL is specified, it applies to both non-XML and XML indexes.</span></span> <span data-ttu-id="a7dd5-112">指定的索引选项可能对两种索引无效。</span><span class="sxs-lookup"><span data-stu-id="a7dd5-112">Indexing options may be specified that are not valid for both types of indexes.</span></span> <span data-ttu-id="a7dd5-113">在这种情况下，整个语句将失败。</span><span class="sxs-lookup"><span data-stu-id="a7dd5-113">In this case, the whole statement fails.</span></span>  
  
## <a name="example-modifying-an-xml-index"></a><span data-ttu-id="a7dd5-114">示例：修改 XML 索引</span><span class="sxs-lookup"><span data-stu-id="a7dd5-114">Example: Modifying an XML Index</span></span>  
 <span data-ttu-id="a7dd5-115">在以下示例中，创建了 XML 索引，然后通过将选项 `ALLOW_ROW_LOCKS` 设置为 `OFF`来修改该索引。</span><span class="sxs-lookup"><span data-stu-id="a7dd5-115">In the following example, an XML index is created and then modified by setting the option `ALLOW_ROW_LOCKS` to `OFF`.</span></span> <span data-ttu-id="a7dd5-116">当 `ALLOW_ROW_LOCKS` 为 `OFF`时，不会锁定行，并且可以使用页级锁和表级锁获得对指定索引的访问权限。</span><span class="sxs-lookup"><span data-stu-id="a7dd5-116">When `ALLOW_ROW_LOCKS` is `OFF`, rows are not locked and access to the specified indexes is obtained by using page-and table-level locks.</span></span>  
  
```  
CREATE TABLE T (Col1 INT PRIMARY KEY, XmlCol XML)  
GO  
-- Create primary XML index.   
CREATE PRIMARY XML INDEX PIdx_T_XmlCol   
ON T(XmlCol)  
GO  
-- Note the type 3 is index on XML type.  
SELECT *  
FROM sys.xml_indexes  
WHERE object_id = object_id('T')  
AND name='PIdx_T_XmlCol'  
  
-- Modify and set an index option.  
ALTER INDEX PIdx_T_XmlCol on T   
SET (ALLOW_ROW_LOCKS = OFF)  
```  
  
## <a name="example-disabling-and-enabling-an-xml-index"></a><span data-ttu-id="a7dd5-117">示例：禁用和启用 XML 索引</span><span class="sxs-lookup"><span data-stu-id="a7dd5-117">Example: Disabling and Enabling an XML Index</span></span>  
 <span data-ttu-id="a7dd5-118">默认情况下，启用 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="a7dd5-118">By default, an XML index is enabled.</span></span> <span data-ttu-id="a7dd5-119">如果禁用 XML 索引，则对 XML 列运行的查询不使用 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="a7dd5-119">If an XML index is disabled, the queries running against the XML column do not use the XML index.</span></span> <span data-ttu-id="a7dd5-120">若要启用 XML 索引，请将 `ALTER INDEX` 和 `REBUILD` 选项一起使用。</span><span class="sxs-lookup"><span data-stu-id="a7dd5-120">To enable an XML index, use `ALTER INDEX` with the `REBUILD` option.</span></span>  
  
```  
CREATE TABLE T (Col1 INT PRIMARY KEY, XmlCol XML)  
GO  
CREATE PRIMARY XML INDEX PIdx_T_XmlCol ON T(XmlCol)  
GO  
ALTER INDEX PIdx_T_XmlCol on T DISABLE  
Go  
-- Verify index is disabled.  
SELECT *  
FROM sys.xml_indexes  
WHERE object_id = object_id('T')  
AND name='PIdx_T_XmlCol'  
-- Rebuild the index.  
ALTER INDEX PIdx_T_XmlCol on T REBUILD  
Go  
```  
  
## <a name="see-also"></a><span data-ttu-id="a7dd5-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a7dd5-121">See Also</span></span>  
 [<span data-ttu-id="a7dd5-122">XML 索引 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="a7dd5-122">XML Indexes &#40;SQL Server&#41;</span></span>](xml-indexes-sql-server.md)  
  
  
