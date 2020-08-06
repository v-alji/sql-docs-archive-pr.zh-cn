---
title: 创建、更改和删除选择性 XML 索引 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
ms.assetid: c398f396-f630-4a2d-a264-f243c5346de1
author: rothja
ms.author: jroth
ms.openlocfilehash: bf4123a46cc13359c936e6f9cfc0db3dcfdaa175
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688651"
---
# <a name="create-alter-and-drop-selective-xml-indexes"></a><span data-ttu-id="649bc-102">创建、更改和删除选择性 XML 索引</span><span class="sxs-lookup"><span data-stu-id="649bc-102">Create, Alter, and Drop Selective XML Indexes</span></span>
  <span data-ttu-id="649bc-103">说明如何创建新的选择性 XML 索引或者更改或删除现有的选择性 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="649bc-103">Describes how to create a new selective XML index, or alter or drop an existing selective XML index.</span></span>  
  
 <span data-ttu-id="649bc-104">有关选择性 XML 索引的详细信息，请参阅 [选择性 XML 索引 (SXI)](selective-xml-indexes-sxi.md)。</span><span class="sxs-lookup"><span data-stu-id="649bc-104">For more information about selective XML indexes, see [Selective XML Indexes &#40;SXI&#41;](selective-xml-indexes-sxi.md).</span></span>  
  
##  <a name="creating-a-selective-xml-index"></a><a name="create"></a> <span data-ttu-id="649bc-105">创建选择性 XML 索引</span><span class="sxs-lookup"><span data-stu-id="649bc-105">Creating a Selective XML Index</span></span>  
  
### <a name="how-to-create-a-selective-xml-index"></a><span data-ttu-id="649bc-106">如何：创建选择性 XML 索引</span><span class="sxs-lookup"><span data-stu-id="649bc-106">How to: Create a Selective XML Index</span></span>  
 <span data-ttu-id="649bc-107">**通过使用 Transact-SQL 创建选择性 XML 索引**</span><span class="sxs-lookup"><span data-stu-id="649bc-107">**Create a Selective XML Index by Using Transact-SQL**</span></span>  
 <span data-ttu-id="649bc-108">通过调用 CREATE SELECTIVE XML INDEX 语句创建选择性 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="649bc-108">Create a selective XML index by calling the CREATE SELECTIVE XML INDEX statement.</span></span> <span data-ttu-id="649bc-109">有关详细信息，请参阅 [CREATE SELECTIVE XML INDEX (Transact-SQL)](/sql/t-sql/statements/create-selective-xml-index-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="649bc-109">For more information, see [CREATE SELECTIVE XML INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-selective-xml-index-transact-sql).</span></span>  
  
 <span data-ttu-id="649bc-110">**示例**</span><span class="sxs-lookup"><span data-stu-id="649bc-110">**Example**</span></span>  
  
 <span data-ttu-id="649bc-111">下面的示例显示了创建选择性 XML 索引的语法。</span><span class="sxs-lookup"><span data-stu-id="649bc-111">The following example shows the syntax for creating a selective XML index.</span></span> <span data-ttu-id="649bc-112">它还显示了该语法的若干变化形式，以便描述使用可选的优化提示建立索引的路径。</span><span class="sxs-lookup"><span data-stu-id="649bc-112">It also shows several variations of the syntax for describing the paths to be indexed, with optional optimization hints.</span></span>  
  
```sql  
CREATE SELECTIVE XML INDEX sxi_index  
ON Tbl(xmlcol)  
  
FOR(  
    pathab   = '/a/b' as XQUERY 'node()'  
    pathabc  = '/a/b/c' as XQUERY 'xs:double',   
    pathdtext = '/a/b/d/text()' as XQUERY 'xs:string' MAXLENGTH(200) SINGLETON  
    pathabe = '/a/b/e' as SQL NVARCHAR(100)  
)  
```  
  
  
  
##  <a name="altering-a-selective-xml-index"></a><a name="alter"></a> <span data-ttu-id="649bc-113">更改选择性 XML 索引</span><span class="sxs-lookup"><span data-stu-id="649bc-113">Altering a Selective XML Index</span></span>  
  
### <a name="how-to-alter-a-selective-xml-index"></a><span data-ttu-id="649bc-114">如何：更改选择性 XML 索引</span><span class="sxs-lookup"><span data-stu-id="649bc-114">How to: Alter a Selective XML Index</span></span>  
 <span data-ttu-id="649bc-115">**通过使用 Transact-SQL 更改选择性 XML 索引**</span><span class="sxs-lookup"><span data-stu-id="649bc-115">**Alter a Selective XML Index by Using Transact-SQL**</span></span>  
 <span data-ttu-id="649bc-116">通过调用 ALTER INDEX 语句更改现有的选择性 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="649bc-116">Alter an existing selective XML index by calling the ALTER INDEX statement.</span></span> <span data-ttu-id="649bc-117">有关详细信息，请参阅 [ALTER INDEX（选择性 XML 索引）](../indexes/indexes.md)。</span><span class="sxs-lookup"><span data-stu-id="649bc-117">For more information, see [ALTER INDEX &#40;Selective XML Indexes&#41;](../indexes/indexes.md).</span></span>  
  
 <span data-ttu-id="649bc-118">**示例**</span><span class="sxs-lookup"><span data-stu-id="649bc-118">**Example**</span></span>  
  
 <span data-ttu-id="649bc-119">下面的示例说明 ALTER INDEX 语句。</span><span class="sxs-lookup"><span data-stu-id="649bc-119">The following example shows an ALTER INDEX statement.</span></span> <span data-ttu-id="649bc-120">该语句将路径 `'/a/b/m'` 添加到索引的 XQuery 部分，并且从在 [CREATE SELECTIVE XML INDEX (Transact-SQL)](/sql/t-sql/statements/create-selective-xml-index-transact-sql) 主题的示例中创建的索引的 SQL 部分删除路径 `'/a/b/e'`。</span><span class="sxs-lookup"><span data-stu-id="649bc-120">This statement adds the path `'/a/b/m'` to the XQuery part of the index and deletes the path `'/a/b/e'` from the SQL part of the index created in the example in the topic [CREATE SELECTIVE XML INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-selective-xml-index-transact-sql).</span></span> <span data-ttu-id="649bc-121">要删除的路径由在创建时提供给它的名称标识。</span><span class="sxs-lookup"><span data-stu-id="649bc-121">The path to delete is identified by the name that was given to it when it was created.</span></span>  
  
```sql  
ALTER INDEX sxi_index  
ON Tbl  
FOR   
(  
    ADD pathm = '/a/b/m' as XQUERY 'node()' ,  
    REMOVE pathabe  
)  
```  
  
  
  
##  <a name="dropping-a-selective-xml-index"></a><a name="drop"></a> <span data-ttu-id="649bc-122">删除选择性 XML 索引</span><span class="sxs-lookup"><span data-stu-id="649bc-122">Dropping a Selective XML Index</span></span>  
  
### <a name="how-to-drop-a-selective-xml-index"></a><span data-ttu-id="649bc-123">如何：删除选择性 XML 索引</span><span class="sxs-lookup"><span data-stu-id="649bc-123">How to: Drop a Selective XML Index</span></span>  
 <span data-ttu-id="649bc-124">**通过使用 Transact-SQL 删除选择性 XML 索引**</span><span class="sxs-lookup"><span data-stu-id="649bc-124">**Drop a Selective XML Index by Using Transact-SQL**</span></span>  
 <span data-ttu-id="649bc-125">通过调用 DROP INDEX 语句删除选择性 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="649bc-125">Drop a selective XML index by calling the DROP INDEX statement.</span></span> <span data-ttu-id="649bc-126">有关详细信息，请参阅 [DROP INDEX（选择性 XML 索引）](/sql/t-sql/statements/drop-index-selective-xml-indexes)。</span><span class="sxs-lookup"><span data-stu-id="649bc-126">For more information, see [DROP INDEX &#40;Selective XML Indexes&#41;](/sql/t-sql/statements/drop-index-selective-xml-indexes).</span></span>  
  
 <span data-ttu-id="649bc-127">**示例**</span><span class="sxs-lookup"><span data-stu-id="649bc-127">**Example**</span></span>  
  
 <span data-ttu-id="649bc-128">下面的示例说明 DROP INDEX 语句。</span><span class="sxs-lookup"><span data-stu-id="649bc-128">The following example shows a DROP INDEX statement.</span></span>  
  
```sql  
DROP INDEX sxi_index ON tbl  
```  
  
 
  
  
