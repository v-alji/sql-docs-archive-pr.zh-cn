---
title: 将现有列更改为 XML 列 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- tables [XML]
ms.assetid: 0d951424-9862-41fe-bd46-127f1c059bcb
author: rothja
ms.author: jroth
ms.openlocfilehash: 32447851fcfe2a54143a028a94539532bba6708d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577437"
---
# <a name="change-existing-columns-to-xml-columns"></a><span data-ttu-id="89149-102">将现有列更改为 XML 列</span><span class="sxs-lookup"><span data-stu-id="89149-102">Change Existing Columns to XML Columns</span></span>
  <span data-ttu-id="89149-103">ALTER TABLE 语句支持 `xml` 数据类型。</span><span class="sxs-lookup"><span data-stu-id="89149-103">The ALTER TABLE statement supports the `xml` data type.</span></span> <span data-ttu-id="89149-104">例如，可以将任意字符串类型列更改为 `xml` 数据类型。</span><span class="sxs-lookup"><span data-stu-id="89149-104">For example, you can alter any string type column to the `xml` data type.</span></span> <span data-ttu-id="89149-105">注意，在这些情况下，列中包含的文档必须格式正确。</span><span class="sxs-lookup"><span data-stu-id="89149-105">Note that in these cases, the documents contained in the column must be well formed.</span></span> <span data-ttu-id="89149-106">此外，如果将列的类型从字符串更改为类型化的 xml，则列中的文档将根据指定的 XSD 架构进行验证。</span><span class="sxs-lookup"><span data-stu-id="89149-106">Also, if you are changing the type of the column from string to typed xml, the documents in the column are validated against the specified XSD schemas.</span></span>  
  
```  
CREATE TABLE T (Col1 int primary key, Col2 nvarchar(max))  
GO  
INSERT INTO T   
VALUES (1, '<Root><Product ProductID="1"/></Root>')  
GO  
ALTER TABLE T   
ALTER COLUMN Col2 xml  
GO  
```  
  
 <span data-ttu-id="89149-107">可以将 `xml` 类型列从非类型化的 XML 更改为类型化的 XML。</span><span class="sxs-lookup"><span data-stu-id="89149-107">You can change an `xml` type column from untyped XML to typed XML.</span></span> <span data-ttu-id="89149-108">例如：</span><span class="sxs-lookup"><span data-stu-id="89149-108">For example:</span></span>  
  
```  
CREATE TABLE T (Col1 int primary key, Col2 xml)  
GO  
INSERT INTO T   
values (1, '<p1:ProductDescription ProductModelID="1"   
xmlns:p1="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription">  
            </p1:ProductDescription>')  
GO   
-- Make it a typed xml column by specifying a schema collection.  
ALTER TABLE T   
ALTER COLUMN Col2 xml (Production.ProductDescriptionSchemaCollection)  
GO  
```  
  
> [!NOTE]  
>  <span data-ttu-id="89149-109">将对 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 数据库运行脚本，因为已将 XML 架构集合 `Production.ProductDescriptionSchemaCollection`创建为 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 数据库的一部分。</span><span class="sxs-lookup"><span data-stu-id="89149-109">The script will run against [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database, because the XML schema collection, `Production.ProductDescriptionSchemaCollection`, is created as part of the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database.</span></span>  
  
 <span data-ttu-id="89149-110">在上一个示例中，存储在列中的所有实例都将根据指定集合中的 XSD 架构来验证和类型化。</span><span class="sxs-lookup"><span data-stu-id="89149-110">In the previous example, all the instances stored in the column are validated and typed against the XSD schemas in the specified collection.</span></span> <span data-ttu-id="89149-111">如果列包含对于指定架构无效的一个或多个 XML 实例，则 `ALTER TABLE` 语句将失败，并且您无法将非类型化的 XML 列更改为类型化的 XML。</span><span class="sxs-lookup"><span data-stu-id="89149-111">If the column contains one or more XML instances that are invalid with regard to the specified schema, the `ALTER TABLE` statement will fail and you will not be able to change your untyped XML column into typed XML.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="89149-112">如果表非常庞大，则修改 `xml` 类型列的开销会很大。</span><span class="sxs-lookup"><span data-stu-id="89149-112">If a table is large, modifying an `xml` type column can be costly.</span></span> <span data-ttu-id="89149-113">这是因为必须检查每个文档格式是否正确，还必须验证每个文档是否为类型化的 XML。</span><span class="sxs-lookup"><span data-stu-id="89149-113">This is because each document must be checked for being well formed and, for typed XML, must also be validated.</span></span>  
  
 <span data-ttu-id="89149-114">有关类型化 XML 的详细信息，请参阅 [类型化的 XML 与非类型化的 XML 的比较](compare-typed-xml-to-untyped-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="89149-114">For more information about typed XML, see [Compare Typed XML to Untyped XML](compare-typed-xml-to-untyped-xml.md).</span></span>  
  
  
