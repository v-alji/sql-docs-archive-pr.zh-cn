---
title: 创建、更改和删除辅助选择性 XML 索引 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
ms.assetid: 45128105-833b-40a9-9cc9-1ae03ac0b52b
author: rothja
ms.author: jroth
ms.openlocfilehash: e6f7296896b6421db5329565403cdcbaf10b26a5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688652"
---
# <a name="create-alter-and-drop-secondary-selective-xml-indexes"></a><span data-ttu-id="185e8-102">创建、更改和删除辅助选择性 XML 索引</span><span class="sxs-lookup"><span data-stu-id="185e8-102">Create, Alter, and Drop Secondary Selective XML Indexes</span></span>
  <span data-ttu-id="185e8-103">说明如何创建新的辅助选择性 XML 索引或者更改或删除现有的辅助选择性 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="185e8-103">Describes how to create a new secondary selective XML index, or alter or drop an existing secondary selective XML index.</span></span>  
  
##  <a name="creating-a-secondary-selective-xml-index"></a><a name="create"></a> <span data-ttu-id="185e8-104">创建辅助选择性 XML 索引</span><span class="sxs-lookup"><span data-stu-id="185e8-104">Creating a Secondary Selective XML Index</span></span>  
  
### <a name="how-to-create-a-secondary-selective-xml-index"></a><span data-ttu-id="185e8-105">如何：创建辅助选择性 XML 索引</span><span class="sxs-lookup"><span data-stu-id="185e8-105">How to: Create a Secondary Selective XML Index</span></span>  
 <span data-ttu-id="185e8-106">**使用 Transact-SQL 创建辅助选择性 XML 索引**</span><span class="sxs-lookup"><span data-stu-id="185e8-106">**Create a Secondary Selective XML Index by Using Transact-SQL**</span></span>  
 <span data-ttu-id="185e8-107">通过调用 CREATE XML INDEX 语句创建辅助选择性 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="185e8-107">Create a secondary selective XML index by calling the CREATE XML INDEX statement.</span></span> <span data-ttu-id="185e8-108">有关详细信息，请参阅 [CREATE XML INDEX &#40;选择性 XML 索引&#41;] (~/t-sql/statements/create-xml-index-selective-xml-indexes。</span><span class="sxs-lookup"><span data-stu-id="185e8-108">For more information, see [CREATE XML INDEX &#40;Selective XML Indexes&#41;](~/t-sql/statements/create-xml-index-selective-xml-indexes.</span></span>  
  
 <span data-ttu-id="185e8-109">**示例**</span><span class="sxs-lookup"><span data-stu-id="185e8-109">**Example**</span></span>  
  
 <span data-ttu-id="185e8-110">下面的示例对路径 `'pathabc'`创建辅助选择性 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="185e8-110">The following example creates a secondary selective XML index on the path `'pathabc'`.</span></span> <span data-ttu-id="185e8-111">用 CREATE SELECTIVE XML INDEX 语句创建索引时向其提供的名称标识该索引的路径。</span><span class="sxs-lookup"><span data-stu-id="185e8-111">The path to index is identified by the name that was given to it when it was created with the CREATE SELECTIVE XML INDEX statement.</span></span> <span data-ttu-id="185e8-112">有关详细信息，请参阅 [CREATE SELECTIVE XML INDEX (Transact-SQL)](/sql/t-sql/statements/create-selective-xml-index-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="185e8-112">For more information, see [CREATE SELECTIVE XML INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-selective-xml-index-transact-sql).</span></span>  
  
```sql  
CREATE XML INDEX filt_sxi_index_c  
ON Tbl(xmlcol)  
USING XML INDEX sxi_index  
FOR  
(  
    pathabc  
)  
```  
  
  
##  <a name="altering-a-secondary-selective-xml-index"></a><a name="alter"></a> <span data-ttu-id="185e8-113">更改辅助选择性 XML 索引</span><span class="sxs-lookup"><span data-stu-id="185e8-113">Altering a Secondary Selective XML Index</span></span>  
 <span data-ttu-id="185e8-114">辅助选择性 XML 索引不支持 ALTER 语句。</span><span class="sxs-lookup"><span data-stu-id="185e8-114">The ALTER statement is not supported for secondary selective XML indexes.</span></span> <span data-ttu-id="185e8-115">若要更改辅助选择性 XML 索引，请删除现有索引，然后重新创建它。</span><span class="sxs-lookup"><span data-stu-id="185e8-115">To change a secondary selective XML index, drop the existing index and recreate it.</span></span>  
  
### <a name="how-to-alter-a-secondary-selective-xml-index"></a><span data-ttu-id="185e8-116">如何：更改辅助选择性 XML 索引</span><span class="sxs-lookup"><span data-stu-id="185e8-116">How to: Alter a Secondary Selective XML Index</span></span>  
 <span data-ttu-id="185e8-117">**使用 Transact-SQL 更改辅助选择性 XML 索引**</span><span class="sxs-lookup"><span data-stu-id="185e8-117">**Alter a Secondary Selective XML Index by Using Transact-SQL**</span></span>  
 1.  <span data-ttu-id="185e8-118">通过调用 DROP INDEX 语句删除现有辅助选择性 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="185e8-118">Drop the existing secondary selective XML index by calling the DROP INDEX statement.</span></span> <span data-ttu-id="185e8-119">有关详细信息，请参阅 [DROP INDEX（选择性 XML 索引）](../indexes/indexes.md)。</span><span class="sxs-lookup"><span data-stu-id="185e8-119">For more information, see [DROP INDEX &#40;Selective XML Indexes&#41;](../indexes/indexes.md).</span></span>  
  
2.  <span data-ttu-id="185e8-120">通过调用 CREATE XML INDEX 语句，用所需的选项重新创建该索引。</span><span class="sxs-lookup"><span data-stu-id="185e8-120">Recreate the index with the desired options by calling the CREATE XML INDEX statement.</span></span> <span data-ttu-id="185e8-121">有关详细信息，请参阅 [CREATE XML INDEX &#40;选择性 XML 索引&#41;] (~/t-sql/statements/create-xml-index-selective-xml-indexes。</span><span class="sxs-lookup"><span data-stu-id="185e8-121">For more information, see [CREATE XML INDEX &#40;Selective XML Indexes&#41;](~/t-sql/statements/create-xml-index-selective-xml-indexes.</span></span>  
  
 <span data-ttu-id="185e8-122">**示例**</span><span class="sxs-lookup"><span data-stu-id="185e8-122">**Example**</span></span>  
  
 <span data-ttu-id="185e8-123">以下示例通过删除再重新创建辅助选择性 XML 索引，更改该索引。</span><span class="sxs-lookup"><span data-stu-id="185e8-123">The following example changes a secondary selective XML index by dropping it and recreating it.</span></span>  
  
```sql  
DROP INDEX filt_sxi_index_c  
  
CREATE XML INDEX filt_sxi_index_c  
ON Tbl(xmlcol)  
USING XML INDEX sxi_index  
FOR  
(  
    pathabc  
)  
```  
  
  
##  <a name="dropping-a-secondary-selective-xml-index"></a><a name="drop"></a> <span data-ttu-id="185e8-124">删除辅助选择性 XML 索引</span><span class="sxs-lookup"><span data-stu-id="185e8-124">Dropping a Secondary Selective XML Index</span></span>  
  
### <a name="how-to-drop-a-secondary-selective-xml-index"></a><span data-ttu-id="185e8-125">如何：删除辅助选择性 XML 索引</span><span class="sxs-lookup"><span data-stu-id="185e8-125">How to: Drop a Secondary Selective XML Index</span></span>  
 <span data-ttu-id="185e8-126">**使用 Transact-SQL 删除辅助选择性 XML 索引**</span><span class="sxs-lookup"><span data-stu-id="185e8-126">**Drop a Secondary Selective XML Index by Using Transact-SQL**</span></span>  
 <span data-ttu-id="185e8-127">通过调用 DROP INDEX 语句删除辅助选择性 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="185e8-127">Drop a secondary selective XML index by calling the DROP INDEX statement.</span></span> <span data-ttu-id="185e8-128">有关详细信息，请参阅 [DROP INDEX（选择性 XML 索引）](../indexes/indexes.md)。</span><span class="sxs-lookup"><span data-stu-id="185e8-128">For more information, see [DROP INDEX &#40;Selective XML Indexes&#41;](../indexes/indexes.md).</span></span>  
  
 <span data-ttu-id="185e8-129">**示例**</span><span class="sxs-lookup"><span data-stu-id="185e8-129">**Example**</span></span>  
  
 <span data-ttu-id="185e8-130">下面的示例说明 DROP INDEX 语句。</span><span class="sxs-lookup"><span data-stu-id="185e8-130">The following example shows a DROP INDEX statement.</span></span>  
  
```sql  
DROP INDEX ssxi_index  
ON tbl  
```  
  
  
## <a name="see-also"></a><span data-ttu-id="185e8-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="185e8-131">See Also</span></span>  
 [<span data-ttu-id="185e8-132">选择性 XML 索引 (SXI)</span><span class="sxs-lookup"><span data-stu-id="185e8-132">Selective XML Indexes &#40;SXI&#41;</span></span>](selective-xml-indexes-sxi.md)  
  
  
