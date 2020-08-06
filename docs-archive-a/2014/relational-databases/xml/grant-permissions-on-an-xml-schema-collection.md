---
title: 授予对 XML 架构集合的权限 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- granting permissions [SQL Server], XML schema collections
- ALTER permission
ms.assetid: ffbb829c-3b8f-4e5d-97d9-ab4059aab0db
author: rothja
ms.author: jroth
ms.openlocfilehash: 2dc6384acb2f079245c80923e683ebe2c03d2562
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687564"
---
# <a name="grant-permissions-on-an-xml-schema-collection"></a><span data-ttu-id="cce25-102">授予对 XML 架构集合的权限</span><span class="sxs-lookup"><span data-stu-id="cce25-102">Grant Permissions on an XML Schema Collection</span></span>
  <span data-ttu-id="cce25-103">您可以授予创建 XML 架构集合的权限，也可以授予对 XML 架构集合对象的某些操作权限。</span><span class="sxs-lookup"><span data-stu-id="cce25-103">You can grant permissions to create an XML schema collection and also grant permissions on an XML schema collection object.</span></span>  
  
## <a name="granting-permission-to-create-an-xml-schema-collection"></a><span data-ttu-id="cce25-104">授予创建 XML 架构集合的权限</span><span class="sxs-lookup"><span data-stu-id="cce25-104">Granting Permission to Create an XML Schema Collection</span></span>  
 <span data-ttu-id="cce25-105">若要创建 XML 架构集合，必须具有下列权限：</span><span class="sxs-lookup"><span data-stu-id="cce25-105">To create an XML schema collection, the following permissions are required:</span></span>  
  
-   <span data-ttu-id="cce25-106">主体必须具有数据库级的 CREATE XML SCHEMA COLLECTION 权限。</span><span class="sxs-lookup"><span data-stu-id="cce25-106">The principal requires CREATE XML SCHEMA COLLECTION permission at the database-level.</span></span>  
  
-   <span data-ttu-id="cce25-107">由于 XML 架构集合是关系架构作用域对象，因此主体还必须具有对关系架构的 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="cce25-107">Because the XML schema collections are relational schema-scoped, the principal must also have ALTER permission on the relational schema.</span></span>  
  
 <span data-ttu-id="cce25-108">下列权限使主体可以在服务器数据库中的关系架构中创建 XML 架构集合：</span><span class="sxs-lookup"><span data-stu-id="cce25-108">The following permissions let a principal create an XML schema collection in a relational schema in a database on a server:</span></span>  
  
-   <span data-ttu-id="cce25-109">对服务器具有 CONTROL 权限</span><span class="sxs-lookup"><span data-stu-id="cce25-109">CONTROL permission on the server</span></span>  
  
-   <span data-ttu-id="cce25-110">对服务器具有 ALTER ANY DATABASE 权限</span><span class="sxs-lookup"><span data-stu-id="cce25-110">ALTER ANY DATABASE permission on the server</span></span>  
  
-   <span data-ttu-id="cce25-111">对数据库具有 ALTER 权限</span><span class="sxs-lookup"><span data-stu-id="cce25-111">ALTER permission on the database</span></span>  
  
-   <span data-ttu-id="cce25-112">数据库中的 CONTROL 权限</span><span class="sxs-lookup"><span data-stu-id="cce25-112">CONTROL permission in the database</span></span>  
  
-   <span data-ttu-id="cce25-113">数据库中的 ALTER ANY SCHEMA 权限和 CREATE XML SCHEMA COLLECTION 权限</span><span class="sxs-lookup"><span data-stu-id="cce25-113">ALTER ANY SCHEMA permission and CREATE XML SCHEMA COLLECTION permission in the database</span></span>  
  
-   <span data-ttu-id="cce25-114">对关系架构具有 ALTER 或 CONTROL 权限以及数据库中的 CREATE XML SCHEMA COLLECTION 权限</span><span class="sxs-lookup"><span data-stu-id="cce25-114">ALTER or CONTROL permission on the relational schema and CREATE XML SCHEMA COLLECTION permission in the database</span></span>  
  
 <span data-ttu-id="cce25-115">在下面的示例中使用了最后一种权限方法。</span><span class="sxs-lookup"><span data-stu-id="cce25-115">This last method of permissions is used in the following example.</span></span>  
  
 <span data-ttu-id="cce25-116">关系架构的所有者将变成在该架构中创建的 XML 架构集合的所有者。</span><span class="sxs-lookup"><span data-stu-id="cce25-116">The owner of the relational schema becomes the owner of the XML schema collection created in that schema.</span></span> <span data-ttu-id="cce25-117">这样，此所有者就可以完全控制 XML 架构集合。</span><span class="sxs-lookup"><span data-stu-id="cce25-117">This owner then has full control over the XML schema collection.</span></span> <span data-ttu-id="cce25-118">因此，此所有者就可以修改 XML 架构集合、类型化 xml 列或删除 XML 架构集合。</span><span class="sxs-lookup"><span data-stu-id="cce25-118">Therefore, this owner can modify the XML schema collection, type an xml column, or drop the XML schema collection.</span></span>  
  
## <a name="granting-permissions-on-an-xml-schema-collection-object"></a><span data-ttu-id="cce25-119">授予对 XML 架构集合对象的某些操作权限</span><span class="sxs-lookup"><span data-stu-id="cce25-119">Granting Permissions on an XML Schema Collection Object</span></span>  
 <span data-ttu-id="cce25-120">允许对 XML 架构集合具有下列权限：</span><span class="sxs-lookup"><span data-stu-id="cce25-120">The following permissions are allowed on the XML schema collection:</span></span>  
  
-   <span data-ttu-id="cce25-121">当使用 ALTER XML SCHEMA COLLECTION 语句修改现有 XML 架构集合的内容时，必须具有 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="cce25-121">The ALTER permission is required when modifying contents of an existing XML schema collection by using the ALTER XML SCHEMA COLLECTION statement.</span></span>  
  
-   <span data-ttu-id="cce25-122">CONTROL 权限使用户可以对 XML 架构集合执行任何操作。</span><span class="sxs-lookup"><span data-stu-id="cce25-122">The CONTROL permission lets a user perform any operation on the XML schema collection.</span></span>  
  
-   <span data-ttu-id="cce25-123">若要将 XML 架构集合的所有权从一个主体传递到另一个主体，必须具有 TAKE OWNERSHIP 权限。</span><span class="sxs-lookup"><span data-stu-id="cce25-123">The TAKE OWNERSHIP permission is required to transfer ownership of the XML schema collection from one principal to another.</span></span>  
  
-   <span data-ttu-id="cce25-124">REFERENCES 权限可授权主体使用 XML 架构集合来类型化或约束表和视图中的 `xml` 类型列以及参数。</span><span class="sxs-lookup"><span data-stu-id="cce25-124">The REFERENCES permission authorizes the principal to use the XML schema collection to type or constrain `xml` type columns, in tables and views and parameters.</span></span> <span data-ttu-id="cce25-125">当一个 XML 架构集合引用另一个 XML 架构集合时，也必须具有 REFERENCES 权限。</span><span class="sxs-lookup"><span data-stu-id="cce25-125">The REFERENCES permission is also required when one XML schema collection refers to another.</span></span>  
  
-   <span data-ttu-id="cce25-126">如果主体对 XML 架构集合具有 ALTER、REFERENCES 或 CONTROL 权限之一，则 VIEW DEFINITION 权限就使此主体能够通过 XML_SCHEMA_NAMESPACE 或目录视图来查询该集合的内容。</span><span class="sxs-lookup"><span data-stu-id="cce25-126">The VIEW DEFINITION permission allows the principal to query the contents of an XML schema collection either through XML_SCHEMA_NAMESPACE or through the catalog views, provided this principal also has one of the ALTER, REFERENCES, or CONTROL permissions on the collection.</span></span>  
  
-   <span data-ttu-id="cce25-127">若要验证主体针对类型化或约束 `xml` 类型列、变量和参数的 XML 架构集合插入或更新的值，必须具有 EXECUTE 权限。</span><span class="sxs-lookup"><span data-stu-id="cce25-127">The EXECUTE permission is required to validate values inserted or updated by the principal against the XML schema collection that is typing or constraining the `xml` type columns, variables, and parameters.</span></span> <span data-ttu-id="cce25-128">当查询存储在这些列和变量中的 XML 时，也必须具有此权限。</span><span class="sxs-lookup"><span data-stu-id="cce25-128">You also need this permission when you are querying the XML stored in these columns and variables.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="cce25-129">示例</span><span class="sxs-lookup"><span data-stu-id="cce25-129">Examples</span></span>  
 <span data-ttu-id="cce25-130">以下示例中的应用场景说明 XML 架构权限的工作机制。</span><span class="sxs-lookup"><span data-stu-id="cce25-130">The scenarios in the following examples illustrate how XML schema permissions work.</span></span> <span data-ttu-id="cce25-131">每个示例都创建有必需的测试数据库、关系架构和登录帐户。</span><span class="sxs-lookup"><span data-stu-id="cce25-131">Each example creates the necessary test database, relational schemas, and logins.</span></span> <span data-ttu-id="cce25-132">这些登录帐户已授予必需的 XML 架构集合权限。</span><span class="sxs-lookup"><span data-stu-id="cce25-132">These logins are granted the necessary XML schema collection permissions.</span></span> <span data-ttu-id="cce25-133">每个示例均在结束时进行了必要的清除。</span><span class="sxs-lookup"><span data-stu-id="cce25-133">Each example does the necessary clean up at the end.</span></span>  
  
### <a name="a-granting-permissions-to-create-an-xml-schema-collection"></a><span data-ttu-id="cce25-134">A.</span><span class="sxs-lookup"><span data-stu-id="cce25-134">A.</span></span> <span data-ttu-id="cce25-135">授予创建 XML 架构集合的权限</span><span class="sxs-lookup"><span data-stu-id="cce25-135">Granting permissions to create an XML schema collection</span></span>  
 <span data-ttu-id="cce25-136">下面的示例显示如何授予权限以便主体能够创建 XML 架构集合。</span><span class="sxs-lookup"><span data-stu-id="cce25-136">The following example shows how to grant permissions so that a principal can create an XML schema collection.</span></span> <span data-ttu-id="cce25-137">此示例将创建一个示例数据库和一个测试用户 `TestLogin1`。</span><span class="sxs-lookup"><span data-stu-id="cce25-137">The example creates a sample database and a test user, `TestLogin1`.</span></span> <span data-ttu-id="cce25-138">`TestLogin1` 针对关系架构的 `ALTER` 权限和针对数据库的 `CREATE XML SCHEMA COLLECTION` 权限。</span><span class="sxs-lookup"><span data-stu-id="cce25-138">`TestLogin1` is then given `ALTER` permission on the relational schema and given `CREATE XML SCHEMA COLLECTION` permission on the database.</span></span> <span data-ttu-id="cce25-139">有了这些权限， `TestLogin1` 便可以成功创建示例 XML 架构集合。</span><span class="sxs-lookup"><span data-stu-id="cce25-139">With these permissions, `TestLogin1` succeeds in creating a sample XML schema collection.</span></span>  
  
```  
SETUSER  
GO  
USE master  
GO  
CREATE LOGIN TestLogin1 WITH password='SQLSvrPwd1'  
GO  
CREATE DATABASE SampleDBForSchemaPermissions  
GO  
USE SampleDBForSchemaPermissions  
GO  
CREATE USER TestLogin1  
GO  
-- User must have ALTER permission on the relational schema in the database.  
GRANT ALTER ON SCHEMA::dbo TO TestLogin1  
GO  
-- User also must have permission to create XML schema collections in the database.  
GRANT CREATE XML SCHEMA COLLECTION   
TO TestLogin1  
GO  
-- Execute CREATE XML SCHEMA COLLECTION.  
SETUSER 'TestLogin1'  
GO  
CREATE XML SCHEMA COLLECTION myTestSchemaCollection AS '<?xml version="1.0" encoding="UTF-8" ?>  
<xsd:schema targetNamespace="http://schemas.adventure-works.com/Additional/ContactInfo"   
            xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
elementFormDefault="qualified">  
<xsd:element name="AdditionalContactInfo" >  
  <xsd:complexType mixed="true" >  
    <xsd:sequence>  
      <xsd:any processContents="strict"    
               namespace="http://schemas.adventure-works.com/Contact/Record   
                          http://schemas.adventure-works.com/AdditionalContactTypes"  
               minOccurs="0" maxOccurs="unbounded" />  
    </xsd:sequence>  
  </xsd:complexType>  
</xsd:element>  
<xsd:element name="root" type="xsd:byte"/>  
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
  
### <a name="b-granting-permission-to-use-an-existing-xml-schema-collection"></a><span data-ttu-id="cce25-140">B.</span><span class="sxs-lookup"><span data-stu-id="cce25-140">B.</span></span> <span data-ttu-id="cce25-141">授予使用现有 XML 架构集合的权限</span><span class="sxs-lookup"><span data-stu-id="cce25-141">Granting permission to use an existing XML schema collection</span></span>  
 <span data-ttu-id="cce25-142">以下示例将进一步显示针对 XML 架构集合的权限模式。</span><span class="sxs-lookup"><span data-stu-id="cce25-142">The following example further shows the permission model for the XML schema collection.</span></span> <span data-ttu-id="cce25-143">该示例将显示创建和使用 XML 架构集合时需要哪些不同的权限。</span><span class="sxs-lookup"><span data-stu-id="cce25-143">The example shows how different permissions are required to create and use the XML schema collection.</span></span>  
  
 <span data-ttu-id="cce25-144">此示例将创建一个测试数据库和一个登录帐户 `TestLogin1`。</span><span class="sxs-lookup"><span data-stu-id="cce25-144">The example creates a test database and a login, `TestLogin1`.</span></span> <span data-ttu-id="cce25-145">`TestLogin1` 将在该数据库中创建一个 XML 架构集合。</span><span class="sxs-lookup"><span data-stu-id="cce25-145">`TestLogin1` creates an XML schema collection in the database.</span></span> <span data-ttu-id="cce25-146">然后，此登录帐户将创建一个表并使用 XML 架构集合创建一个类型化的 xml 列。</span><span class="sxs-lookup"><span data-stu-id="cce25-146">The login then creates a table and uses the XML schema collection to create a typed xml column.</span></span> <span data-ttu-id="cce25-147">用户随后将插入数据并查询该数据。</span><span class="sxs-lookup"><span data-stu-id="cce25-147">The user then inserts data and queries it.</span></span> <span data-ttu-id="cce25-148">所有这些步骤都需要必要的架构权限，如代码中所示。</span><span class="sxs-lookup"><span data-stu-id="cce25-148">All these steps require the necessary schema permissions, as shown in the code.</span></span>  
  
```  
SETUSER  
GO  
USE master  
GO  
CREATE LOGIN TestLogin1 WITH password='SQLSvrPwd1'  
GO  
CREATE DATABASE SampleDBForSchemaPermissions  
GO  
USE SampleDBForSchemaPermissions  
GO  
CREATE USER TestLogin1  
GO  
-- Grant permission to the user.  
SETUSER  
GO  
-- User must have ALTER permission on the relational schema in the database.  
GRANT ALTER ON SCHEMA::dbo TO TestLogin1  
GO  
-- User also must have permission to create XML schema collections in the database.  
GRANT CREATE XML SCHEMA COLLECTION   
TO TestLogin1  
GO  
-- Now user can execute the previous CREATE XML SCHEMA COLLECTION statement.  
SETUSER 'TestLogin1'  
GO  
CREATE XML SCHEMA COLLECTION myTestSchemaCollection AS '<?xml version="1.0" encoding="UTF-8" ?>  
<xsd:schema targetNamespace="http://schemas.adventure-works.com/Additional/ContactInfo"   
            xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
elementFormDefault="qualified">  
  
<xsd:element name="AdditionalContactInfo" >  
  <xsd:complexType mixed="true" >  
    <xsd:sequence>  
      <xsd:any processContents="strict"    
               namespace="http://schemas.adventure-works.com/Contact/Record   
                          http://schemas.adventure-works.com/AdditionalContactTypes"  
               minOccurs="0" maxOccurs="unbounded" />  
    </xsd:sequence>  
  </xsd:complexType>  
</xsd:element>  
<xsd:element name="telephone" type="xsd:string" />  
</xsd:schema>'  
GO  
  
-- Create a table by using the collection to type an XML column.   
--TestLogin1 must have permission to create a table.  
SETUSER  
GO  
GRANT CREATE TABLE TO TestLogin1  
GO  
-- The user also must have REFERENCES permission to use the XML schema collection  
-- to create a typed XML column (REFERENCES permission on schema   
-- collection is not needed).  
GRANT REFERENCES ON XML SCHEMA COLLECTION::myTestSchemaCollection   
TO TestLogin1  
GO  
-- Now user can create a table and use the XML schema collection to create   
-- a typed XML column.  
SETUSER 'TestLogin1'  
GO  
CREATE TABLE MyTestTable (xmlCol xml (dbo.myTestSchemaCollection))  
GO  
-- To insert data in the table, the user needs EXECUTE permission on the XML schema collection.  
-- GRANT EXECUTE permission to TestLogin2 on the xml schema collection.  
SETUSER  
GO  
GRANT EXECUTE ON XML SCHEMA COLLECTION::myTestSchemaCollection   
TO TestLogin1  
GO  
-- TestLogin1 does not own the dbo schema. This user must have INSERT permission.  
GRANT INSERT TO TestLogin1  
GO  
-- Now the user can insert data into the table.  
SETUSER 'TestLogin1'  
GO  
INSERT INTO MyTestTable VALUES('  
<telephone xmlns="http://schemas.adventure-works.com/Additional/ContactInfo">111-1111</telephone>  
')  
GO  
-- To query the table, TestLogin1 must have permissions: SELECT on the table and EXECUTE on the XML schema collection.  
SETUSER  
GO  
GRANT SELECT TO TestLogin1  
GO  
-- TestLogin1 already has EXECUTE permission on the schema (granted before inserting a record in the table).  
SELECT xmlCol.query('declare default element namespace "http://schemas.adventure-works.com/Additional/ContactInfo" /telephone[1]')  
FROM MyTestTable  
GO  
-- To show that the user must have EXECUTE permission to query, revoke the  
-- previously granted permission and return the query.  
SETUSER  
GO  
REVOKE EXECUTE ON XML SCHEMA COLLECTION::myTestSchemaCollection to TestLogin1  
Go  
-- Now TestLogin1 cannot execute the query.  
SETUSER 'TestLogin1'  
GO  
SELECT xmlCol.query('declare default element namespace "http://schemas.adventure-works.com/Additional/ContactInfo" /telephone[1]')  
FROM MyTestTable  
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
  
### <a name="c-granting-alter-permission-on-an-xml-schema-collection"></a><span data-ttu-id="cce25-149">C.</span><span class="sxs-lookup"><span data-stu-id="cce25-149">C.</span></span> <span data-ttu-id="cce25-150">授予对 XML 架构集合的 ALTER 权限</span><span class="sxs-lookup"><span data-stu-id="cce25-150">Granting ALTER permission on an XML schema collection</span></span>  
 <span data-ttu-id="cce25-151">要修改数据库中的现有 XML 架构集合，用户必须具有 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="cce25-151">A user must have ALTER permission to modify an existing XML schema collection in the database.</span></span> <span data-ttu-id="cce25-152">下面的示例显示如何授予 `ALTER` 权限。</span><span class="sxs-lookup"><span data-stu-id="cce25-152">The following example shows how to grant `ALTER` permission.</span></span>  
  
```  
SETUSER  
GO  
USE master  
GO  
CREATE LOGIN TestLogin1 WITH password='SQLSvrPwd1'  
GO  
CREATE DATABASE SampleDBForSchemaPermissions  
GO  
USE SampleDBForSchemaPermissions  
GO  
CREATE USER TestLogin1  
GO  
-- Grant permission to the user.  
SETUSER  
GO  
-- User must have ALTER permission on the relational schema in the database.  
GRANT ALTER ON SCHEMA::dbo TO TestLogin1  
GO  
-- User also must have permission to create XML schema collections in the database.  
GRANT CREATE XML SCHEMA COLLECTION   
TO TestLogin1  
GO  
-- Now user can execute the previous CREATE XML SCHEMA COLLECTION statement.  
SETUSER 'TestLogin1'  
GO  
CREATE XML SCHEMA COLLECTION myTestSchemaCollection AS '<?xml version="1.0" encoding="UTF-8" ?>  
<xsd:schema targetNamespace="http://schemas.adventure-works.com/Additional/ContactInfo"   
            xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
elementFormDefault="qualified">  
  
<xsd:element name="AdditionalContactInfo" >  
  <xsd:complexType mixed="true" >  
    <xsd:sequence>  
      <xsd:any processContents="strict"    
               namespace="http://schemas.adventure-works.com/Contact/Record   
                          http://schemas.adventure-works.com/AdditionalContactTypes"  
               minOccurs="0" maxOccurs="unbounded" />  
    </xsd:sequence>  
  </xsd:complexType>  
</xsd:element>  
<xsd:element name="telephone" type="xsd:string" />  
</xsd:schema>'  
GO  
-- Grant ALTER permission to TestLogin1.  
setuser  
GO  
GRANT ALTER ON XML SCHEMA COLLECTION::myTestSchemaCollection TO TestLogin1  
GO  
-- TestLogin1 should be able to add components to the collection.  
SETUSER 'TestLogin1'  
GO  
ALTER XML SCHEMA COLLECTION myTestSchemaCollection ADD '  
<xsd:schema targetNamespace="http://schemas.adventure-works.com/Additional/ContactInfo"   
            xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
            xmlns="http://schemas.adventure-works.com/Additional/ContactInfo"   
elementFormDefault="qualified">  
 <xsd:element name="pager" type="xsd:string"/>  
</xsd:schema>  
'  
Go  
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
  
### <a name="d-granting-take-ownership-permission-on-an-xml-schema-collection"></a><span data-ttu-id="cce25-153">D.</span><span class="sxs-lookup"><span data-stu-id="cce25-153">D.</span></span> <span data-ttu-id="cce25-154">授予对 XML 架构集合的 TAKE OWNERSHIP 权限</span><span class="sxs-lookup"><span data-stu-id="cce25-154">Granting TAKE OWNERSHIP permission on an XML schema collection</span></span>  
 <span data-ttu-id="cce25-155">下面的示例显示如何将 XML 架构的所有权从一个用户传递到另一个用户。</span><span class="sxs-lookup"><span data-stu-id="cce25-155">The following example shows how to transfer XML schema ownership from one user to another.</span></span> <span data-ttu-id="cce25-156">为了使此示例更加生动，此示例中的用户在不同的默认关系架构中工作。</span><span class="sxs-lookup"><span data-stu-id="cce25-156">To make the example more interesting, the users in this example work in different default relational schemas.</span></span>  
  
 <span data-ttu-id="cce25-157">此示例将执行下列操作：</span><span class="sxs-lookup"><span data-stu-id="cce25-157">This example does the following:</span></span>  
  
-   <span data-ttu-id="cce25-158">创建一个带有两个关系架构（ `dbo` 和 `myOtherDBSchema`）的数据库。</span><span class="sxs-lookup"><span data-stu-id="cce25-158">Creates a database with two relational schemas, `dbo` and `myOtherDBSchema`).</span></span>  
  
-   <span data-ttu-id="cce25-159">创建两个用户，即 `TestLogin1` 和 `TestLogin2`。</span><span class="sxs-lookup"><span data-stu-id="cce25-159">Creates two users, `TestLogin1` and `TestLogin2`.</span></span> <span data-ttu-id="cce25-160">`TestLogin2` 成为 `myOtherDBSchema` 关系架构的所有者。</span><span class="sxs-lookup"><span data-stu-id="cce25-160">`TestLogin2` is made the owner of the `myOtherDBSchema` relational schema.</span></span>  
  
-   <span data-ttu-id="cce25-161">`TestLogin1` 将在 `dbo` 关系架构中创建一个 XML 架构集合。</span><span class="sxs-lookup"><span data-stu-id="cce25-161">`TestLogin1` creates an XML schema collection in the `dbo` relational schema.</span></span>  
  
-   <span data-ttu-id="cce25-162">`TestLogin1` 然后向 `TAKE OWNERSHIP` 授予针对 XML 架构集合的 `TestLogin2`权限。</span><span class="sxs-lookup"><span data-stu-id="cce25-162">`TestLogin1` then gives `TAKE OWNERSHIP` permission on the XML schema collection to `TestLogin2`.</span></span>  
  
-   <span data-ttu-id="cce25-163">`TestLogin2` 将成为 `myOtherDBSchema`中的 XML 架构集合的所有者，而不用更改 XML 架构集合的关系架构。</span><span class="sxs-lookup"><span data-stu-id="cce25-163">`TestLogin2` becomes the owner of the XML schema collection in `myOtherDBSchema`, without changing the relational schema of the XML schema collection.</span></span>  
  
```  
CREATE LOGIN TestLogin1 with password='SQLSvrPwd1'  
GO  
CREATE LOGIN TestLogin2 with password='SQLSvrPwd2'  
GO  
CREATE DATABASE SampleDBForSchemaPermissions  
GO  
USE SampleDBForSchemaPermissions  
GO  
-- Create another relational schema in the database.  
CREATE SCHEMA myOtherDBSchema  
GO  
-- Create users in the database. Note TestLogin2's default schema is  
-- myOtherDBSchema.  
CREATE USER TestLogin1  
GO  
CREATE USER TestLogin2 WITH DEFAULT_SCHEMA=myOtherDBSchema  
GO  
-- TestLogin2 will own myOtherDBSchema relational schema.  
ALTER AUTHORIZATION ON SCHEMA::myOtherDBSchema TO TestLogin2  
GO  
  
-- For TestLogin1 to create XML schema collection, the following  
-- permission is required.  
GRANT CREATE XML SCHEMA COLLECTION   
TO TestLogin1  
GO  
GRANT ALTER ON SCHEMA::dbo TO TestLogin1  
GO  
-- Now TestLogin1 can create an XML schema collection.  
setuser 'TestLogin1'  
GO  
CREATE XML SCHEMA COLLECTION myTestSchemaCollection AS '<?xml version="1.0" encoding="UTF-8" ?>  
<xsd:schema targetNamespace="http://schemas.adventure-works.com/Additional/ContactInfo"   
            xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
elementFormDefault="qualified">  
  
<xsd:element name="AdditionalContactInfo" >  
 <xsd:complexType mixed="true" >  
    <xsd:sequence>  
      <xsd:any processContents="strict"   
               namespace="http://schemas.adventure-works.com/Contact/Record   
                          http://schemas.adventure-works.com/AdditionalContactTypes"  
               minOccurs="0" maxOccurs="unbounded" />  
    </xsd:sequence>  
 </xsd:complexType>  
</xsd:element>  
<xsd:element name="telephone" type="xsd:string" />  
</xsd:schema>'  
GO  
  
-- Grant TAKE OWNERSHIP to TestLogin2.  
SETUSER  
GO  
GRANT TAKE OWNERSHIP ON XML SCHEMA COLLECTION::dbo.myTestSchemaCollection   
TO TestLogin2  
GO  
-- Verify the owner. Note the UserName and Principal_id is null.   
SELECT user_name(sys.xml_schema_collections.principal_id) as UserName,   
       sys.schemas.name as RelSchemaName,*   
FROM   sys.xml_schema_collections   
      JOIN sys.schemas   
      ON sys.schemas.schema_id=sys.xml_schema_collections.schema_id  
GO  
-- TestLogin2 can take ownership now.  
setuser 'TestLogin2'  
GO  
ALTER AUTHORIZATION ON XML SCHEMA COLLECTION::dbo.myTestSchemaCollection   
TO TestLogin2  
GO  
-- Note that although TestLogin2 is the owner,the XML schema collection   
-- is still in dbo.  
SELECT user_name(sys.xml_schema_collections.principal_id) as UserName,   
      sys.schemas.name as RelSchemaName,*   
FROM sys.xml_schema_collections JOIN sys.schemas   
     ON sys.schemas.schema_id=sys.xml_schema_collections.schema_id  
GO  
  
-- TestLogin2 moves the collection from dbo to myOtherDBSchema relational schema.  
-- TestLogin2 already has all necessary permissions.  
-- 1) TestLogin2 owns the destination relational schema so he can alter it.  
-- 2) TestLogin2 owns the XML schema collection (therefore, has CONTROL permission).  
ALTER SCHEMA myOtherDBSchema  
TRANSFER XML SCHEMA COLLECTION::dbo.myTestSchemaCollection  
GO  
  
SELECT user_name(sys.xml_schema_collections.principal_id) as UserName,   
       sys.schemas.name as RelSchemaName,*   
FROM   sys.xml_schema_collections JOIN sys.schemas   
       ON sys.schemas.schema_id=sys.xml_schema_collections.schema_id  
GO  
-- Final cleanup   
SETUSER  
GO  
USE master  
GO  
DROP DATABASE SampleDBForSchemaPermissions  
GO  
DROP LOGIN TestLogin1  
DROP LOGIN TestLogin2  
go   
```  
  
### <a name="e-granting-view-definition-permission-on-an-xml-schema-collection"></a><span data-ttu-id="cce25-164">E.</span><span class="sxs-lookup"><span data-stu-id="cce25-164">E.</span></span> <span data-ttu-id="cce25-165">授予对 XML 架构集合的 VIEW DEFINITION 权限</span><span class="sxs-lookup"><span data-stu-id="cce25-165">Granting VIEW DEFINITION permission on an XML schema collection</span></span>  
 <span data-ttu-id="cce25-166">下面的示例显示如何授予对 XML 架构集合的 VIEW DEFINITION 权限。</span><span class="sxs-lookup"><span data-stu-id="cce25-166">The following example shows how to grant VIEW DEFINITION permissions for an XML schema collection.</span></span>  
  
```  
SETUSER  
GO  
USE master  
GO  
IF EXISTS( SELECT * FROM sysdatabases WHERE name='permissionsDB' )  
   DROP DATABASE permissionsDB  
GO  
IF EXISTS( SELECT * FROM sys.sql_logins WHERE name='schemaUser' )  
   DROP LOGIN schemaUser  
GO  
CREATE DATABASE permissionsDB  
GO  
CREATE LOGIN schemaUser WITH PASSWORD='Pass#123',DEFAULT_DATABASE=permissionsDB  
GO  
GRANT CONNECT SQL TO schemaUser  
GO  
USE permissionsDB  
GO  
CREATE USER schemaUser WITH DEFAULT_SCHEMA=dbo  
GO  
CREATE XML SCHEMA COLLECTION MySC AS '  
<schema xmlns="http://www.w3.org/2001/XMLSchema" targetNamespace="http://ns"  
xmlns:ns="http://ns">  
  
   <simpleType name="ListOfIntegers">  
      <list itemType="integer"/>  
   </simpleType>  
  
   <element name="root" type="ns:ListOfIntegers"/>  
  
   <element name="gRoot" type="gMonth"/>  
  
</schema>  
'  
GO  
-- schemaUser cannot see the contents of the collection.  
SETUSER 'schemaUser'  
GO  
SELECT XML_SCHEMA_NAMESPACE(N'dbo',N'MySC')  
GO  
  
-- Grant schemaUser VIEW DEFINITION and REFERENCES permissions  
-- on the XML schema collection.  
SETUSER  
GO  
GRANT VIEW DEFINITION ON XML SCHEMA COLLECTION::dbo.MySC TO schemaUser  
GO  
GRANT REFERENCES ON XML SCHEMA COLLECTION::dbo.MySC TO schemaUser  
GO  
-- Now schemaUser can see the content of the collection.  
SETUSER 'schemaUser'  
GO  
SELECT XML_SCHEMA_NAMESPACE(N'dbo',N'MySC')  
GO  
-- Revoke schemaUser VIEW DEFINITION permissions  
-- on the XML schema collection.  
SETUSER  
GO  
REVOKE VIEW DEFINITION ON XML SCHEMA COLLECTION::dbo.MySC FROM schemaUser  
GO  
-- Now schemaUser cannot see the contents of   
-- the collection.  
setuser 'schemaUser'  
GO  
SELECT XML_SCHEMA_NAMESPACE(N'dbo',N'MySC')  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="cce25-167">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cce25-167">See Also</span></span>  
 <span data-ttu-id="cce25-168">[XML 数据 (SQL Server)](xml-data-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="cce25-168">[XML Data &#40;SQL Server&#41;](xml-data-sql-server.md) </span></span>  
 <span data-ttu-id="cce25-169">[类型化的 XML 与非类型化的 XML 的比较](compare-typed-xml-to-untyped-xml.md) </span><span class="sxs-lookup"><span data-stu-id="cce25-169">[Compare Typed XML to Untyped XML](compare-typed-xml-to-untyped-xml.md) </span></span>  
 <span data-ttu-id="cce25-170">[XML 架构集合 (SQL Server)](xml-schema-collections-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="cce25-170">[XML Schema Collections &#40;SQL Server&#41;](xml-schema-collections-sql-server.md) </span></span>  
 [<span data-ttu-id="cce25-171">在服务器上使用 XML 架构集合的要求和限制</span><span class="sxs-lookup"><span data-stu-id="cce25-171">Requirements and Limitations for XML Schema Collections on the Server</span></span>](requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  
