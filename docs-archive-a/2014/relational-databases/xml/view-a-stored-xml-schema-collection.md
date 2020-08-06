---
title: 查看存储 XML 架构集合 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- schema collections [SQL Server], viewing
- XML schemas [SQL Server], viewing
- CREATE XML SCHEMA COLLECTION statement
- xml_schema_namespace function
- XML schema collections [SQL Server], viewing
- displaying XML schema collections
- viewing XML schema collections
ms.assetid: e38031af-22df-4cd9-a14e-e316b822f91b
author: rothja
ms.author: jroth
ms.openlocfilehash: 6383fb17183a991d2f83325044663cc9671e9442
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578742"
---
# <a name="view-a-stored-xml-schema-collection"></a><span data-ttu-id="22a76-102">查看存储 XML 架构集合</span><span class="sxs-lookup"><span data-stu-id="22a76-102">View a Stored XML Schema Collection</span></span>
  <span data-ttu-id="22a76-103">使用 [CREATE XML SCHEMA COLLECTION](/sql/t-sql/statements/create-xml-schema-collection-transact-sql)导入 XML 架构集合之后，架构组件便存储在元数据中。</span><span class="sxs-lookup"><span data-stu-id="22a76-103">After you import an XML schema collection by using [CREATE XML SCHEMA COLLECTION](/sql/t-sql/statements/create-xml-schema-collection-transact-sql), the schema components are stored in the metadata.</span></span> <span data-ttu-id="22a76-104">你可以使用 [xml_schema_namespace](/sql/t-sql/xml/xml-schema-namespace)内部函数重新构造 XML 架构集合。</span><span class="sxs-lookup"><span data-stu-id="22a76-104">You can use the [xml_schema_namespace](/sql/t-sql/xml/xml-schema-namespace)intrinsic function to reconstruct the XML schema collection.</span></span> <span data-ttu-id="22a76-105">此函数返回 `xml` 数据类型实例。</span><span class="sxs-lookup"><span data-stu-id="22a76-105">This function returns an `xml` data type instance.</span></span>  
  
 <span data-ttu-id="22a76-106">例如，以下查询从`ProductDescriptionSchemaCollection`数据库中的产品关系架构中检索 XML 架构集合 ( [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] )。</span><span class="sxs-lookup"><span data-stu-id="22a76-106">For example, the following query retrieves an XML schema collection (`ProductDescriptionSchemaCollection`) from the production relational schema in the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database.</span></span>  
  
```  
SELECT xml_schema_namespace(N'Production',N'ProductDescriptionSchemaCollection')  
GO  
```  
  
 <span data-ttu-id="22a76-107">如果只需要查看 XML 架构集合中的一个架构，则可以针对由 `xml_schema_namespace` 返回的 `xml` 类型结果指定 XQuery。</span><span class="sxs-lookup"><span data-stu-id="22a76-107">If you want to see only one schema from the XML schema collection, you can specify XQuery against the `xml` type result that is returned by `xml_schema_namespace`.</span></span>  
  
```  
SELECT xml_schema_namespace(N'RelationalSchemaName',N'XmlSchemaCollectionName').query('  
/xs:schema[@targetNamespace="TargetNameSpace"]  
')  
GO  
```  
  
 <span data-ttu-id="22a76-108">例如，以下查询从 `ProductDescriptionSchemaCollection` XML 架构集合中检索产品保证和维护 XML 架构信息。</span><span class="sxs-lookup"><span data-stu-id="22a76-108">For example, the following query retrieves product warranty and maintenance XML schema information from the `ProductDescriptionSchemaCollection` XML schema collection.</span></span>  
  
```  
SELECT xml_schema_namespace(N'Production',N'ProductDescriptionSchemaCollection').query('  
/xs:schema[@targetNamespace="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain"]  
')  
GO  
```  
  
 <span data-ttu-id="22a76-109">也可以将可选的目标命名空间作为第三个参数传递到 `xml_schema_namespace` 函数，以便从集合中检索特定的架构，如以下查询所示：</span><span class="sxs-lookup"><span data-stu-id="22a76-109">You can also pass the optional target namespace as the third parameter to the `xml_schema_namespace` function to retrieve specific schema from the collection, as shown in the following query:</span></span>  
  
```  
SELECT xml_schema_namespace(N'Production',N'ProductDescriptionSchemaCollection', N'https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain')  
GO  
```  
  
 <span data-ttu-id="22a76-110">使用 CREATE XML SCHEMA COLLECTION 在数据库中创建 XML 架构集合时，该语句将架构组件存储在元数据中。</span><span class="sxs-lookup"><span data-stu-id="22a76-110">When you create an XML schema collection by using CREATE XML SCHEMA COLLECTION in the database, the statement stores the schema components in the metadata.</span></span> <span data-ttu-id="22a76-111">注意，仅存储 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 可识别的架构组件。</span><span class="sxs-lookup"><span data-stu-id="22a76-111">Note that only the schema components that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] understands are stored.</span></span> <span data-ttu-id="22a76-112">不存储任何注释、批注或非 XSD 属性。</span><span class="sxs-lookup"><span data-stu-id="22a76-112">Any comments, annotations, or non-XSD attributes are not stored.</span></span> <span data-ttu-id="22a76-113">因此，使用 **xml_schema_namespace** 重新构造的架构在功能上与原始架构相同，但外观不一定相同。</span><span class="sxs-lookup"><span data-stu-id="22a76-113">Therefore, the schema reconstructed by **xml_schema_namespace** is functionally equivalent to the original schema, but it will not necessarily look the same.</span></span> <span data-ttu-id="22a76-114">例如，显示的前缀与原始架构中的前缀不同。</span><span class="sxs-lookup"><span data-stu-id="22a76-114">For example, you will not see the same prefixes you had in the original schema.</span></span> <span data-ttu-id="22a76-115">**xml_schema_namespace** 返回的架构使用 **t** 作为目标命名空间的前缀，使用 **ns1**、 **ns2**（依此类推）作为其他命名空间的前缀。</span><span class="sxs-lookup"><span data-stu-id="22a76-115">The schema returned by **xml_schema_namespace** uses **t** as the prefix for the target namespace and **ns1**, **ns2**, and so on, for other namespaces.</span></span>  
  
 <span data-ttu-id="22a76-116">如果要保留 XML 架构的相同副本，则应将 XML 架构保存到文件或数据库表中的 `xml` 类型列。</span><span class="sxs-lookup"><span data-stu-id="22a76-116">If you want to retain an identical copy of the XML schemas, you should save your XML schema in a file or in a database table in an `xml` type column.</span></span>  
  
 <span data-ttu-id="22a76-117">[sys.xml_schema_collections](/sql/relational-databases/system-catalog-views/sys-xml-schema-collections-transact-sql) 目录视图也返回有关 XML 架构集合的信息。</span><span class="sxs-lookup"><span data-stu-id="22a76-117">The [sys.xml_schema_collections](/sql/relational-databases/system-catalog-views/sys-xml-schema-collections-transact-sql) catalog view also returns information about XML schema collections.</span></span> <span data-ttu-id="22a76-118">此信息包括集合名称、创建日期和集合的所有者。</span><span class="sxs-lookup"><span data-stu-id="22a76-118">This information includes the name of the collection, the creation date, and the owner of the collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22a76-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="22a76-119">See Also</span></span>  
 [<span data-ttu-id="22a76-120">XML 架构集合 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="22a76-120">XML Schema Collections &#40;SQL Server&#41;</span></span>](xml-schema-collections-sql-server.md)  
  
  
