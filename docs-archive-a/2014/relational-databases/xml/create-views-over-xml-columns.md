---
title: 基于 XML 列创建视图 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- views [XML in SQL Server]
ms.assetid: eb5f0439-1f69-49c2-8759-e59bda1633b7
author: rothja
ms.author: jroth
ms.openlocfilehash: bf06f1107cbf4875eb63fe6747775b5c5c04810c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692305"
---
# <a name="create-views-over-xml-columns"></a><span data-ttu-id="656f5-102">对 XML 列创建视图</span><span class="sxs-lookup"><span data-stu-id="656f5-102">Create Views over XML Columns</span></span>
  <span data-ttu-id="656f5-103">可以使用 `xml` 类型列创建视图。</span><span class="sxs-lookup"><span data-stu-id="656f5-103">You can use an `xml` type column to create views.</span></span> <span data-ttu-id="656f5-104">下面的示例创建了一个视图，在该视图中，使用 `xml` 数据类型的 `value()` 方法检索 `xml` 类型列中的值。</span><span class="sxs-lookup"><span data-stu-id="656f5-104">The following example creates a view in which the value from an `xml` type column is retrieved using the `value()` method of the `xml` data type.</span></span>  
  
```  
-- Create the table.  
CREATE TABLE T (  
    ProductID          int primary key,   
    CatalogDescription xml)  
GO  
-- Insert sample data.  
INSERT INTO T values(1,'<ProductDescription ProductID="1" ProductName="SomeName" />')  
GO  
-- Create view (note the value() method used to retrieve ProductName   
-- attribute value from the XML).  
CREATE VIEW MyView AS   
  SELECT ProductID,  
         CatalogDescription.value('(/ProductDescription/@ProductName)[1]', 'varchar(40)') AS PName  
  FROM T  
GO   
```  
  
 <span data-ttu-id="656f5-105">对此视图执行下面的查询：</span><span class="sxs-lookup"><span data-stu-id="656f5-105">Execute the following query against the view:</span></span>  
  
```  
SELECT *   
FROM   MyView  
```  
  
 <span data-ttu-id="656f5-106">结果如下：</span><span class="sxs-lookup"><span data-stu-id="656f5-106">This is the result:</span></span>  
  
```  
ProductID   PName        
----------- ------------  
1           SomeName   
```  
  
 <span data-ttu-id="656f5-107">关于使用 `xml` 数据类型创建视图，请注意以下几点：</span><span class="sxs-lookup"><span data-stu-id="656f5-107">Note the following points about using the `xml` data type to create views:</span></span>  
  
-   <span data-ttu-id="656f5-108">可以在具体化视图中创建 xml 数据类型。</span><span class="sxs-lookup"><span data-stu-id="656f5-108">The xml data type can be created in a materialized view.</span></span> <span data-ttu-id="656f5-109">具体化视图不能基于 xml 数据类型方法。</span><span class="sxs-lookup"><span data-stu-id="656f5-109">The materialized view cannot be based on an xml data type method.</span></span> <span data-ttu-id="656f5-110">但是，它可以转换为不同于基表中的 xml 类型列的 XML 架构集合。</span><span class="sxs-lookup"><span data-stu-id="656f5-110">However, it can be cast to an XML schema collection that is different from the xml type column in the base table.</span></span>  
  
-   <span data-ttu-id="656f5-111">不能将 `xml` 数据类型用于分布式分区视图。</span><span class="sxs-lookup"><span data-stu-id="656f5-111">The `xml` data type cannot be used in Distributed Partitioned Views.</span></span>  
  
-   <span data-ttu-id="656f5-112">不会将对视图运行的 SQL 谓词推送到相应视图定义的 XQuery 中。</span><span class="sxs-lookup"><span data-stu-id="656f5-112">SQL predicates running against the view will not be pushed into the XQuery of the view definition.</span></span>  
  
-   <span data-ttu-id="656f5-113">视图中的 XML 数据类型方法不可更新。</span><span class="sxs-lookup"><span data-stu-id="656f5-113">XML data type methods in a view are not updatable.</span></span>  
  
  
