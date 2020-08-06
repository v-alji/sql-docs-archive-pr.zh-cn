---
title: 拒绝对 XML 架构集合的权限 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- denying permissions [SQL Server], XML server collections
ms.assetid: e2b300b0-e734-4c43-a4da-c78e6e5d4fba
author: rothja
ms.author: jroth
ms.openlocfilehash: 0791a9bd9c7f6b323886a38bed27bea84940770d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577425"
---
# <a name="deny-permissions-on-an-xml-schema-collection"></a><span data-ttu-id="e6fed-102">拒绝对 XML 架构集合的权限</span><span class="sxs-lookup"><span data-stu-id="e6fed-102">Deny Permissions on an XML Schema Collection</span></span>
  <span data-ttu-id="e6fed-103">可以拒绝创建新 XML 架构集合或使用现有 XML 架构集合的权限。</span><span class="sxs-lookup"><span data-stu-id="e6fed-103">Permission can be denied to either create a new XML schema collection or use an existing one.</span></span>  
  
## <a name="denying-permission-to-create-an-xml-schema-collection"></a><span data-ttu-id="e6fed-104">拒绝创建 XML 架构集合的权限</span><span class="sxs-lookup"><span data-stu-id="e6fed-104">Denying Permission to Create an XML Schema Collection</span></span>  
 <span data-ttu-id="e6fed-105">可以通过下列方式拒绝创建 XML 架构集合的权限：</span><span class="sxs-lookup"><span data-stu-id="e6fed-105">You can deny permission to create an XML schema collection in the following ways:</span></span>  
  
-   <span data-ttu-id="e6fed-106">拒绝对关系架构的 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="e6fed-106">Deny ALTER permission on the relational schema.</span></span>  
  
-   <span data-ttu-id="e6fed-107">拒绝对关系架构的 CONTROL 权限可拒绝关系架构及其包含的所有对象的所有权限。</span><span class="sxs-lookup"><span data-stu-id="e6fed-107">Deny CONTROL on the relational schema to deny all permissions on the relational schema and on all the contained objects.</span></span>  
  
-   <span data-ttu-id="e6fed-108">拒绝对数据库的 ALTER ANY SCHEMA 权限。</span><span class="sxs-lookup"><span data-stu-id="e6fed-108">Deny ALTER ANY SCHEMA on the database.</span></span> <span data-ttu-id="e6fed-109">在这种情况下，主体无法在数据库的任意位置创建 XML 架构集合。</span><span class="sxs-lookup"><span data-stu-id="e6fed-109">In this case, the principal cannot create an XML schema collection anywhere in the database.</span></span> <span data-ttu-id="e6fed-110">请注意，拒绝对数据库的 ALTER 或 CONTROL 权限将拒绝对数据库中所有对象的所有权限。</span><span class="sxs-lookup"><span data-stu-id="e6fed-110">Note also that denying ALTER or CONTROL permission on the database denies all permissions on all objects in the database.</span></span>  
  
## <a name="denying-permissions-on-an-xml-schema-collection-object"></a><span data-ttu-id="e6fed-111">拒绝对 XML 架构集合对象的权限</span><span class="sxs-lookup"><span data-stu-id="e6fed-111">Denying Permissions on an XML Schema Collection Object</span></span>  
 <span data-ttu-id="e6fed-112">下面是可以拒绝的对现有 XML 架构集合的权限及结果：</span><span class="sxs-lookup"><span data-stu-id="e6fed-112">Following are the permission that can be denied on an existing XML schema collection and the results:</span></span>  
  
-   <span data-ttu-id="e6fed-113">拒绝 ALTER 权限将拒绝主体修改 XML 架构集合内容的功能。</span><span class="sxs-lookup"><span data-stu-id="e6fed-113">Denying the ALTER permission denies the principal the ability to modify the contents of the XML schema collection.</span></span>  
  
-   <span data-ttu-id="e6fed-114">拒绝 CONTROL 权限将拒绝主体对 XML 架构集合执行任何操作的功能。</span><span class="sxs-lookup"><span data-stu-id="e6fed-114">Denying the CONTROL permission denies the principal the ability to perform any operation on the XML schema collection.</span></span>  
  
-   <span data-ttu-id="e6fed-115">拒绝 REFERENCES 权限将拒绝主体使用 XML 架构集合类型化或约束 xml 类型列和参数的功能。</span><span class="sxs-lookup"><span data-stu-id="e6fed-115">Denying the REFERENCES permission denies the principal the ability to type or constrain xml type columns and parameters using the XML schema collection.</span></span> <span data-ttu-id="e6fed-116">还将拒绝主体从其他 XML 架构集合引用此 XML 架构集合的功能。</span><span class="sxs-lookup"><span data-stu-id="e6fed-116">It also denies the principal the ability to refer to this XML schema collection from other XML schema collections.</span></span>  
  
-   <span data-ttu-id="e6fed-117">拒绝 VIEW DEFINITION 权限将拒绝主体查看 XML 架构集合内容的功能。</span><span class="sxs-lookup"><span data-stu-id="e6fed-117">Denying the VIEW DEFINITION permission denies the principal the ability to view the contents of an XML schema collection.</span></span>  
  
-   <span data-ttu-id="e6fed-118">拒绝 EXECUTE 权限将拒绝主体插入或更新由 XML 架构集合类型化或受其约束的列、变量和参数中的值的功能。</span><span class="sxs-lookup"><span data-stu-id="e6fed-118">Denying the EXECUTE permission denies the principal the ability to insert or update the values in columns, variables, and parameters that are typed or constrained by the XML schema collection.</span></span> <span data-ttu-id="e6fed-119">还将拒绝主体查询相同 xml 类型列和变量的值的功能。</span><span class="sxs-lookup"><span data-stu-id="e6fed-119">It also denies the principal the ability to query the values in those same xml type columns and variables.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="e6fed-120">示例</span><span class="sxs-lookup"><span data-stu-id="e6fed-120">Examples</span></span>  
 <span data-ttu-id="e6fed-121">以下示例中的应用场景说明了 XML 架构权限的工作机制。</span><span class="sxs-lookup"><span data-stu-id="e6fed-121">The scenarios in the following examples show how XML schema permissions work.</span></span> <span data-ttu-id="e6fed-122">每个示例都创建有必需的测试数据库、关系架构和登录帐户。</span><span class="sxs-lookup"><span data-stu-id="e6fed-122">Each example creates the necessary test database, relational schemas, and logins.</span></span> <span data-ttu-id="e6fed-123">这些登录帐户已授予必需的 XML 架构集合权限。</span><span class="sxs-lookup"><span data-stu-id="e6fed-123">These logins are granted the necessary XML schema collection permissions.</span></span> <span data-ttu-id="e6fed-124">每个示例在结束时都会进行必要的清除操作。</span><span class="sxs-lookup"><span data-stu-id="e6fed-124">Each example does the necessary cleanup at the end.</span></span>  
  
### <a name="a-preventing-a-user-from-creating-an-xml-schema-collection"></a><span data-ttu-id="e6fed-125">A.</span><span class="sxs-lookup"><span data-stu-id="e6fed-125">A.</span></span> <span data-ttu-id="e6fed-126">禁止用户创建 XML 架构集合</span><span class="sxs-lookup"><span data-stu-id="e6fed-126">Preventing a user from creating an XML schema collection</span></span>  
 <span data-ttu-id="e6fed-127">禁止用户创建 XML 架构集合的一个方法是拒绝对关系架构的 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="e6fed-127">One of the ways to prevent a user from creating an XML schema collection is by denying the ALTER permission on a relational schema.</span></span> <span data-ttu-id="e6fed-128">下面的示例说明了这一点。</span><span class="sxs-lookup"><span data-stu-id="e6fed-128">This is shown in the following example.</span></span>  
  
 <span data-ttu-id="e6fed-129">该示例创建了一个用户 `TestLogin1`和一个数据库。</span><span class="sxs-lookup"><span data-stu-id="e6fed-129">The example creates a user, `TestLogin1`, and a database.</span></span> <span data-ttu-id="e6fed-130">除 `dbo` 架构外，它还在数据库中创建了一个关系架构。</span><span class="sxs-lookup"><span data-stu-id="e6fed-130">It also creates a relational schema, in addition to the `dbo` schema, in the database.</span></span> <span data-ttu-id="e6fed-131">最初， `CREATE XML SCHEMA` 权限允许用户在数据库的任何位置创建架构集合。</span><span class="sxs-lookup"><span data-stu-id="e6fed-131">Initially, the `CREATE XML SCHEMA` permission allows the user to create a schema collection anywhere in the database.</span></span> <span data-ttu-id="e6fed-132">然后，该示例拒绝用户对其中一个关系架构拥有 `ALTER` 权限。</span><span class="sxs-lookup"><span data-stu-id="e6fed-132">The example then denies `ALTER` permission to the user on one of the relational schemas.</span></span> <span data-ttu-id="e6fed-133">这就禁止了用户在该关系架构中创建 XML 架构集合。</span><span class="sxs-lookup"><span data-stu-id="e6fed-133">This prevents the user from creating an XML schema collection in that relational schema.</span></span>  
  
```  
CREATE LOGIN TestLogin1 WITH password='SQLSvrPwd1'  
GO  
CREATE DATABASE SampleDBForSchemaPermissions  
GO  
USE SampleDBForSchemaPermissions  
GO  
-- Create another relational schema in the database.  
CREATE SCHEMA myOtherDBSchema  
GO  
CREATE USER TestLogin1  
GO  
-- For TestLogin1 to create/import XML schema collection, following  
-- permission needed.  
-- Database-level permissions  
GRANT CREATE XML SCHEMA COLLECTION TO TestLogin1  
GO  
GRANT ALTER ANY SCHEMA TO TestLogin1  
GO  
-- Now TestLogin1 can import an XML schema collection.  
SETUSER 'TestLogin1'  
GO  
CREATE XML SCHEMA COLLECTION myOtherDBSchema.myTestSchemaCollection AS '<?xml version="1.0" encoding="UTF-8" ?>  
<xsd:schema targetNamespace="http://schemas.adventure-works.com/Additional/ContactInfo"   
            xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
elementFormDefault="qualified">  
<xsd:element name="telephone" type="xsd:string" />  
</xsd:schema>'  
GO  
DROP XML SCHEMA COLLECTION myOtherDBSchema.myTestSchemaCollection  
GO  
-- Now deny permission from TestLogin1 to alter myOtherDBSchema.  
setuser  
GO  
DENY ALTER ON SCHEMA::myOtherDBSchema TO TestLogin1  
GO  
-- Now TestLogin1 cannot create xml schema collection.  
SETUSER 'TestLogin1'  
GO  
CREATE XML SCHEMA COLLECTION myOtherDBSchema.myTestSchemaCollection AS '<?xml version="1.0" encoding="UTF-8" ?>  
<xsd:schema targetNamespace="http://schemas.adventure-works.com/Additional/ContactInfo"   
            xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
elementFormDefault="qualified">  
<xsd:element name="telephone" type="xsd:string" />  
</xsd:schema>'  
GO  
-- Final cleanup  
SETUSER  
GO  
USE master  
GO  
DROP DATABASE SampleDBForSchemaPermissions  
GO  
DROP LOGIN TestLogin1  
GO  
```  
  
### <a name="b-denying-permissions-on-an-xml-schema-collection"></a><span data-ttu-id="e6fed-134">B.</span><span class="sxs-lookup"><span data-stu-id="e6fed-134">B.</span></span> <span data-ttu-id="e6fed-135">拒绝对 XML 架构集合的权限</span><span class="sxs-lookup"><span data-stu-id="e6fed-135">Denying permissions on an XML schema collection</span></span>  
 <span data-ttu-id="e6fed-136">下面的示例说明了如何拒绝登录名对现有 XML 架构集合拥有特定权限。</span><span class="sxs-lookup"><span data-stu-id="e6fed-136">The following example shows how a specific permission on an existing XML schema collection can be denied to a login.</span></span> <span data-ttu-id="e6fed-137">在本例中，拒绝了测试登录名对现有 XML 架构集合的 REFERENCES 权限。</span><span class="sxs-lookup"><span data-stu-id="e6fed-137">In this example, a test login is denied REFERENCES permission on an existing XML schema collection.</span></span>  
  
 <span data-ttu-id="e6fed-138">该示例创建了一个用户 `TestLogin1`和一个数据库。</span><span class="sxs-lookup"><span data-stu-id="e6fed-138">The example creates a user, `TestLogin1`, and a database.</span></span> <span data-ttu-id="e6fed-139">除 `dbo` 架构外，它还在数据库中创建了一个关系架构。</span><span class="sxs-lookup"><span data-stu-id="e6fed-139">It also creates a relational schema, in addition to the `dbo` schema, in the database.</span></span> <span data-ttu-id="e6fed-140">最初， `CREATE XML SCHEMA` 权限允许用户在数据库的任何位置创建架构集合。</span><span class="sxs-lookup"><span data-stu-id="e6fed-140">Initially, the `CREATE XML SCHEMA` permission allows the user to create a schema collection anywhere in the database.</span></span>  
  
 <span data-ttu-id="e6fed-141">`REFERENCES` 利用对 XML 架构集合的 `TestLogin1` 权限使用架构在表中创建 `xml` 类型的列。</span><span class="sxs-lookup"><span data-stu-id="e6fed-141">The `REFERENCES` permission on the XML schema collection lets `TestLogin1` use the schema in creating a typed `xml` column in a table.</span></span> <span data-ttu-id="e6fed-142">如果对 XML 架构集合的 `REFERENCES` 权限被拒绝，将禁止 `TestLogin1` 使用 XML 架构集合。</span><span class="sxs-lookup"><span data-stu-id="e6fed-142">If the `REFERENCES` permission on the XML schema collection is denied, it prevents the `TestLogin1` from using the XML schema collection.</span></span>  
  
```  
CREATE LOGIN TestLogin1 WITH password='SQLSvrPwd1'  
GO  
CREATE DATABASE SampleDBForSchemaPermissions  
GO  
USE SampleDBForSchemaPermissions  
GO  
-- Create another relational schema in the database.  
CREATE SCHEMA myOtherDBSchema  
GO  
CREATE USER TestLogin1  
GO  
-- For TestLogin1 to create/import XML schema collection, the following  
-- permission is required.  
-- Database-level permissions  
GRANT CREATE XML SCHEMA COLLECTION TO TestLogin1  
GO  
GRANT ALTER ANY SCHEMA TO TestLogin1  
GO  
-- Now TestLogin1 can import an XML schema collection.  
SETUSER 'TestLogin1'  
GO  
CREATE XML SCHEMA COLLECTION myOtherDBSchema.myTestSchemaCollection AS '<?xml version="1.0" encoding="UTF-8" ?>  
<xsd:schema targetNamespace="http://schemas.adventure-works.com/Additional/ContactInfo"   
            xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
elementFormDefault="qualified">  
<xsd:element name="telephone" type="xsd:string" />  
</xsd:schema>'  
GO  
-- Grant permission to TestLogin1 to create a table and reference the XML schema collection.  
SETUSER  
GO  
GRANT CREATE TABLE TO TestLogin1  
GO  
-- The user also needs REFERENCES permission to use the XML schema collection  
-- to create a typed XML column (REFERENCES permission on the schema   
-- collection is not needed).  
GRANT REFERENCES ON XML SCHEMA COLLECTION::myOtherDBSchema.myTestSchemaCollection   
TO TestLogin1  
GO  
  
--TestLogin1 can use the schema.  
CREATE TABLE T(i int, x xml (myOtherDBSchema.myTestSchemaCollection))  
GO  
-- Drop the table.  
DROP TABLE T  
GO  
-- Now deny REFERENCES permission to TestLogin1 on the schema created previously.  
SETUSER  
GO  
DENY REFERENCES ON XML SCHEMA COLLECTION::myOtherDBSchema.myTestSchemaCollection TO TestLogin1  
  
GO  
-- Now TestLogin1 cannot create xml schema collection  
SETUSER 'TestLogin1'  
GO  
-- Following statement fails. TestLogin1 does not have REFERENCES   
-- permission on the XML schema collection.  
CREATE TABLE T(i int, x xml (myOtherDBSchema.myTestSchemaCollection))  
GO  
  
-- Final cleanup  
SETUSER  
GO  
USE master  
GO  
DROP DATABASE SampleDBForSchemaPermissions  
GO  
DROP LOGIN TestLogin1  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="e6fed-143">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e6fed-143">See Also</span></span>  
 <span data-ttu-id="e6fed-144">[类型化的 XML 与非类型化的 XML 的比较](compare-typed-xml-to-untyped-xml.md) </span><span class="sxs-lookup"><span data-stu-id="e6fed-144">[Compare Typed XML to Untyped XML](compare-typed-xml-to-untyped-xml.md) </span></span>  
 <span data-ttu-id="e6fed-145">[XML 架构集合 (SQL Server)](xml-schema-collections-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="e6fed-145">[XML Schema Collections &#40;SQL Server&#41;](xml-schema-collections-sql-server.md) </span></span>  
 <span data-ttu-id="e6fed-146">[在服务器上使用 XML 架构集合的要求和限制](requirements-and-limitations-for-xml-schema-collections-on-the-server.md) </span><span class="sxs-lookup"><span data-stu-id="e6fed-146">[Requirements and Limitations for XML Schema Collections on the Server](requirements-and-limitations-for-xml-schema-collections-on-the-server.md) </span></span>  
 <span data-ttu-id="e6fed-147">[DENY 对象权限 (Transact-SQL)](/sql/t-sql/statements/deny-object-permissions-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e6fed-147">[DENY Object Permissions &#40;Transact-SQL&#41;](/sql/t-sql/statements/deny-object-permissions-transact-sql) </span></span>  
 <span data-ttu-id="e6fed-148">[GRANT 对象权限 (Transact-SQL)](/sql/t-sql/statements/grant-object-permissions-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e6fed-148">[GRANT Object Permissions &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-object-permissions-transact-sql) </span></span>  
 [<span data-ttu-id="e6fed-149">XML 数据 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="e6fed-149">XML Data &#40;SQL Server&#41;</span></span>](xml-data-sql-server.md)  
  
  
