---
title: 有关 (SQLXML 4.0) 的 XML 安全注意事项 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- NESTED mode
- client-side XML formatting
- FOR XML clause, security
- server-side XML formatting
- AUTO mode
- security [SQLXML], FOR XML
ms.assetid: facba279-df93-475b-ad43-0043dc5bae03
author: rothja
ms.author: jroth
ms.openlocfilehash: 9a64fa61848e4b5435b2aa944c53953a8c083ab6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589477"
---
# <a name="for-xml-security-considerations-sqlxml-40"></a><span data-ttu-id="e9b71-102">FOR XML 安全注意事项 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="e9b71-102">FOR XML Security Considerations (SQLXML 4.0)</span></span>
  <span data-ttu-id="e9b71-103">FOR XML AUTO 模式生成这样一种 XML 层次结构，其中的元素名称映射到表名，属性名称映射到列名。</span><span class="sxs-lookup"><span data-stu-id="e9b71-103">The FOR XML AUTO mode generates an XML hierarchy in which element names map to table names and attribute names map to column names.</span></span> <span data-ttu-id="e9b71-104">这公开了数据库表和列的信息。</span><span class="sxs-lookup"><span data-stu-id="e9b71-104">This exposes the database table and column information.</span></span> <span data-ttu-id="e9b71-105">通过在查询中指定表和列的别名，可以在使用 AUTO 模式（服务器端格式）时隐藏数据库信息。</span><span class="sxs-lookup"><span data-stu-id="e9b71-105">You can hide the database information when you use AUTO mode (server-side formatting) by specifying table and column aliases in the query.</span></span> <span data-ttu-id="e9b71-106">在生成的 XML 文档中，这些别名作为元素和属性名称返回。</span><span class="sxs-lookup"><span data-stu-id="e9b71-106">These aliases are returned in the resulting XML document as element and attribute names.</span></span>  
  
 <span data-ttu-id="e9b71-107">例如，下面的查询指定 AUTO 模式；因此，在服务器上执行 XML 格式设置：</span><span class="sxs-lookup"><span data-stu-id="e9b71-107">For example, the following query specifies AUTO mode; therefore, the XML formatting is done on the server:</span></span>  
  
```  
SELECT C.FirstName as F,C.LastName as L   
FROM Person.Contact C   
FOR XML AUTO  
```  
  
 <span data-ttu-id="e9b71-108">在生成的 XML 文档中，这些别名用作元素和属性名称：</span><span class="sxs-lookup"><span data-stu-id="e9b71-108">In the resulting XML document, the aliases are used for element and attribute names:</span></span>  
  
```  
<?xml version="1.0" encoding="utf-8" ?>   
<root>  
  <C F="Nancy" L="Fuller" />   
  <CE F="Andrew" L="Peacock" />   
  <C F="Janet" L="Leverling" />   
  ...  
</root>  
```  
  
 <span data-ttu-id="e9b71-109">使用 NESTED 模式（客户端格式）时，在生成的 XML 中仅为属性返回别名。</span><span class="sxs-lookup"><span data-stu-id="e9b71-109">When you use NESTED mode (client-side formatting), aliases are returned only for attributes in the resulting XML document.</span></span> <span data-ttu-id="e9b71-110">基表的名称始终作为元素名称返回。</span><span class="sxs-lookup"><span data-stu-id="e9b71-110">The names of the base tables are always returned as element names.</span></span> <span data-ttu-id="e9b71-111">例如，下面的查询指定 NESTED 模式。</span><span class="sxs-lookup"><span data-stu-id="e9b71-111">For example, the following query specifies NESTED mode.</span></span>  
  
```  
SELECT C.FirstName as F,C.LastName as L   
FROM Person.Contact C   
FOR XML AUTO  
```  
  
 <span data-ttu-id="e9b71-112">在生成的 XML 文档中，基表的名称作为元素名称返回，且未使用表别名：</span><span class="sxs-lookup"><span data-stu-id="e9b71-112">In the resulting XML document, the names of the base tables are returned as element names and table aliases are not used:</span></span>  
  
```  
<?xml version="1.0" encoding="utf-8" ?>   
<root>  
  <Person.Contact F="Nancy" L="Fuller" />   
  <Person.Contact F="Andrew" L="Peacock" />   
  <Person.Contact F="Janet" L="Leverling" />   
       ...  
</root>  
```  
  
  
