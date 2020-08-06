---
title: 撤消对 XML 架构集合的权限 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- revoking permissions [SQL Server]
ms.assetid: 4e542b70-2d56-4a65-8a39-96a1ed477ca6
author: rothja
ms.author: jroth
ms.openlocfilehash: 3ab37c915f14207376e0c4a9582611bf8e65e0d2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688631"
---
# <a name="revoke-permissions-on-an-xml-schema-collection"></a><span data-ttu-id="f9f41-102">撤消对 XML 架构集合的权限</span><span class="sxs-lookup"><span data-stu-id="f9f41-102">Revoke Permissions on an XML Schema Collection</span></span>
  <span data-ttu-id="f9f41-103">可以使用下列一种方法撤消创建 XML 架构集合的权限：</span><span class="sxs-lookup"><span data-stu-id="f9f41-103">The permission to create an XML schema collection can be revoked by using one of the following:</span></span>  
  
-   <span data-ttu-id="f9f41-104">撤消对关系架构的 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="f9f41-104">Revoke the ALTER permission for the relational schema.</span></span> <span data-ttu-id="f9f41-105">这样，主体就不能在关系架构中创建 XML 架构集合。</span><span class="sxs-lookup"><span data-stu-id="f9f41-105">Then, the principal cannot create an XML schema collection in the relational schema.</span></span> <span data-ttu-id="f9f41-106">但是，主体仍然可以在同一数据库的其他关系架构中执行此操作。</span><span class="sxs-lookup"><span data-stu-id="f9f41-106">However, the principal can still do so in other relational schemas in the same database.</span></span>  
  
-   <span data-ttu-id="f9f41-107">撤消主体对数据库的 ALTER ANY SCHEMA 权限。</span><span class="sxs-lookup"><span data-stu-id="f9f41-107">Revoke the ALTER ANY SCHEMA permission on the database for the principal.</span></span> <span data-ttu-id="f9f41-108">这样，主体就不能在数据库中的任何位置创建 XML 架构集合。</span><span class="sxs-lookup"><span data-stu-id="f9f41-108">Then, the principal cannot create an XML schema collection anywhere in the database.</span></span>  
  
-   <span data-ttu-id="f9f41-109">撤消主体对数据库的 CREATE XML SCHEMA COLLECTION 或 ALTER XML SCHEMA COLLECTION 权限。</span><span class="sxs-lookup"><span data-stu-id="f9f41-109">Revoke the CREATE XML SCHEMA COLLECTION or ALTER XML SCHEMA COLLECTION permission on the database for the principal.</span></span> <span data-ttu-id="f9f41-110">这样，主体就无法在数据库中导入 XML 架构集合。</span><span class="sxs-lookup"><span data-stu-id="f9f41-110">This prevents the principal from importing an XML schema collection within the database.</span></span> <span data-ttu-id="f9f41-111">撤消对数据库的 ALTER 或 CONTROL 权限效果相同。</span><span class="sxs-lookup"><span data-stu-id="f9f41-111">Revoking the ALTER or CONTROL permission on the database has the same effect.</span></span>  
  
## <a name="revoking-permissions-on-an-existing-xml-schema-collection-object"></a><span data-ttu-id="f9f41-112">撤消对现有 XML 架构集合对象的权限</span><span class="sxs-lookup"><span data-stu-id="f9f41-112">Revoking Permissions on an Existing XML Schema Collection Object</span></span>  
 <span data-ttu-id="f9f41-113">下列是可以对 XML 架构集合撤消的权限及相应结果：</span><span class="sxs-lookup"><span data-stu-id="f9f41-113">Following are the permissions that can be revoked on an XML schema collection and the results:</span></span>  
  
-   <span data-ttu-id="f9f41-114">ALTER 权限，撤消后，主体无法修改 XML 架构集合的内容。</span><span class="sxs-lookup"><span data-stu-id="f9f41-114">Revoking the ALTER permission revokes a principal's ability to modify the content of the XML schema collection.</span></span>  
  
-   <span data-ttu-id="f9f41-115">TAKE OWNERSHIP 权限，撤消后，主体无法传输 XML 架构集合的所有权。</span><span class="sxs-lookup"><span data-stu-id="f9f41-115">Revoking the TAKE OWNERSHIP permission revokes a principal's ability to transfer ownership of the XML schema collection.</span></span>  
  
-   <span data-ttu-id="f9f41-116">REFERENCES 权限，撤消后，主体无法使用 XML 架构集合类型化或约束 xml 类型列（表和视图中）和参数。</span><span class="sxs-lookup"><span data-stu-id="f9f41-116">Revoking the REFERENCES permission revokes a principal's ability to use the XML schema collection for typing or constraining xml type columns, in tables and views, and parameters.</span></span> <span data-ttu-id="f9f41-117">它还撤消了从其他 XML 架构集合中引用此架构集合的权限。</span><span class="sxs-lookup"><span data-stu-id="f9f41-117">It also revokes the permission to refer to this schema collection from other XML schema collections.</span></span>  
  
-   <span data-ttu-id="f9f41-118">VIEW DEFINITION 权限，撤消后，主体无法查看 XML 架构集合的内容。</span><span class="sxs-lookup"><span data-stu-id="f9f41-118">Revoking the VIEW DEFINITION permission revokes a principal's ability to view the contents of an XML schema collection.</span></span>  
  
-   <span data-ttu-id="f9f41-119">EXECUTE 权限，撤消后，主体无法在通过 XML 集合类型化或约束的列、变量和参数中插入或更新值。</span><span class="sxs-lookup"><span data-stu-id="f9f41-119">Revoking the EXECUTE permission revokes a principal's ability to insert or update values in columns, variables, and parameters that are typed or constrained by the XML collection.</span></span> <span data-ttu-id="f9f41-120">它还撤消了查询这类 **xml** 类型列、变量或参数的功能。</span><span class="sxs-lookup"><span data-stu-id="f9f41-120">It also revokes the ability to query such **xml** type columns, variables, or parameters.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="f9f41-121">示例</span><span class="sxs-lookup"><span data-stu-id="f9f41-121">Examples</span></span>  
 <span data-ttu-id="f9f41-122">以下示例中的应用场景说明 XML 架构权限的工作机制。</span><span class="sxs-lookup"><span data-stu-id="f9f41-122">The scenarios in the following examples illustrate how XML schema permissions work.</span></span> <span data-ttu-id="f9f41-123">每个示例都创建有必需的测试数据库、关系架构和登录帐户。</span><span class="sxs-lookup"><span data-stu-id="f9f41-123">Each example creates the necessary test database, relational schemas, and logins.</span></span> <span data-ttu-id="f9f41-124">这些登录帐户已授予必需的 XML 架构集合权限。</span><span class="sxs-lookup"><span data-stu-id="f9f41-124">These logins are granted the necessary XML schema collection permissions.</span></span> <span data-ttu-id="f9f41-125">每个示例在结束时都会进行必要的清除操作。</span><span class="sxs-lookup"><span data-stu-id="f9f41-125">Each example does the necessary cleanup at the end.</span></span>  
  
### <a name="a-revoking-permissions-to-create-an-xml-schema-collection"></a><span data-ttu-id="f9f41-126">A.</span><span class="sxs-lookup"><span data-stu-id="f9f41-126">A.</span></span> <span data-ttu-id="f9f41-127">撤消创建 XML 架构集合的权限</span><span class="sxs-lookup"><span data-stu-id="f9f41-127">Revoking permissions to create an XML schema collection</span></span>  
 <span data-ttu-id="f9f41-128">该示例创建了一个登录帐户和一个示例数据库。</span><span class="sxs-lookup"><span data-stu-id="f9f41-128">This example creates a login and a sample database.</span></span> <span data-ttu-id="f9f41-129">并在数据库中添加了一个关系架构。</span><span class="sxs-lookup"><span data-stu-id="f9f41-129">It also adds a relational schema in the database.</span></span> <span data-ttu-id="f9f41-130">首先，为登录帐户授予对两个关系架构的 ALTER 权限和其他所需权限，以创建 XML 架构集合。</span><span class="sxs-lookup"><span data-stu-id="f9f41-130">Initially, the login is granted ALTER permission on both relational schemas and other necessary permissions to create XML schema collections.</span></span> <span data-ttu-id="f9f41-131">然后，该示例撤消了对数据库中一个关系架构的 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="f9f41-131">The example then revokes the ALTER permission on one of the relational schemas in the database.</span></span> <span data-ttu-id="f9f41-132">这使得登录帐户无法创建 XML 架构集合。</span><span class="sxs-lookup"><span data-stu-id="f9f41-132">This prevents the login from creating an XML schema collection.</span></span>  
  
```  
setuser  
go  
create login TestLogin1 with password='SQLSvrPwd1'  
go  
create database SampleDBForSchemaPermissions  
go  
use SampleDBForSchemaPermissions  
go  
-- Create another relational schema in the db (in addition to dbo schema)  
CREATE SCHEMA myOtherDBSchema  
go  
CREATE USER TestLogin1  
go  
-- For TestLogin1 to create/import XML schema collection, following  
-- permission needed  
-- CREATE XML SCHEMA is a database level permission  
GRANT CREATE XML SCHEMA COLLECTION TO TestLogin1  
go  
GRANT ALTER ON SCHEMA::myOtherDBSchema TO TestLogin1  
go  
GRANT ALTER ON SCHEMA::dbo TO TestLogin1  
go  
-- Now TestLogin1 can import an XML schema collection in both relational schemas.  
setuser 'TestLogin1'  
go  
CREATE XML SCHEMA COLLECTION dbo.myTestSchemaCollection AS '<?xml version="1.0" encoding="UTF-8" ?>  
  
<xsd:schema targetNamespace="http://schemas.adventure-works.com/Additional/ContactInfo"   
            xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
elementFormDefault="qualified">  
<xsd:element name="telephone" type="xsd:string" />  
</xsd:schema>'  
go  
-- TestLogin1 can create XML schema collection in myOtherDBSchema relational schema  
CREATE XML SCHEMA COLLECTION myOtherDBSchema.myTestSchemaCollection AS '<?xml version="1.0" encoding="UTF-8" ?>  
  
<xsd:schema targetNamespace="http://schemas.adventure-works.com/Additional/ContactInfo"   
            xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
elementFormDefault="qualified">  
<xsd:element name="telephone" type="xsd:string" />  
</xsd:schema>'  
go  
-- Let us drop XML schema collections from both relational schemas  
DROP XML SCHEMA COLLECTION myOtherDBSchema.myTestSchemaCollection  
go  
DROP XML SCHEMA COLLECTION dbo.myTestSchemaCollection  
go  
-- now REVOKE permission from TestLogin1 to alter myOtherDBSchema  
setuser  
go  
REVOKE ALTER ON SCHEMA::myOtherDBSchema FROM TestLogin1  
go  
-- now TestLogin1 cannot create xml schema collection in myOtherDBSchema  
setuser 'TestLogin1'  
go  
CREATE XML SCHEMA COLLECTION myOtherDBSchema.myTestSchemaCollection AS '<?xml version="1.0" encoding="UTF-8" ?>  
<xsd:schema targetNamespace="http://schemas.adventure-works.com/Additional/ContactInfo"   
            xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
elementFormDefault="qualified">  
<xsd:element name="telephone" type="xsd:string" />  
</xsd:schema>'  
go  
  
-- TestLogin1 can still create XML schema collections in dbo  
-- It cannot create XML schema collections anywhere in the database  
-- if we REVOKE CREATE XML SCHEMA COLLECTION permission  
SETUSER  
go  
REVOKE CREATE XML SCHEMA COLLECTION FROM TestLogin1  
go  
  
setuser 'TestLogin1'  
go  
-- the following now should fail  
CREATE XML SCHEMA COLLECTION dbo.myTestSchemaCollection AS '<?xml version="1.0" encoding="UTF-8" ?>  
<xsd:schema targetNamespace="http://schemas.adventure-works.com/Additional/ContactInfo"   
            xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
elementFormDefault="qualified">  
<xsd:element name="telephone" type="xsd:string" />  
</xsd:schema>'  
go  
  
-- Final cleanup  
SETUSER  
go  
USE master  
go  
DROP DATABASE SampleDBForSchemaPermissions  
go  
DROP LOGIN TestLogin1  
Go  
```  
  
## <a name="see-also"></a><span data-ttu-id="f9f41-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f9f41-133">See Also</span></span>  
 <span data-ttu-id="f9f41-134">[XML 数据 (SQL Server)](xml-data-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="f9f41-134">[XML Data &#40;SQL Server&#41;](xml-data-sql-server.md) </span></span>  
 <span data-ttu-id="f9f41-135">[类型化的 XML 与非类型化的 XML 的比较](compare-typed-xml-to-untyped-xml.md) </span><span class="sxs-lookup"><span data-stu-id="f9f41-135">[Compare Typed XML to Untyped XML](compare-typed-xml-to-untyped-xml.md) </span></span>  
 <span data-ttu-id="f9f41-136">[XML 架构集合 (SQL Server)](xml-schema-collections-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="f9f41-136">[XML Schema Collections &#40;SQL Server&#41;](xml-schema-collections-sql-server.md) </span></span>  
 [<span data-ttu-id="f9f41-137">在服务器上使用 XML 架构集合的要求和限制</span><span class="sxs-lookup"><span data-stu-id="f9f41-137">Requirements and Limitations for XML Schema Collections on the Server</span></span>](requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  
