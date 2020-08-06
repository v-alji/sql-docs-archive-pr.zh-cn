---
title: 引用内置 XML 架构集合 (sys) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- sys XML schema collections [SQL Server]
- schema collections [SQL Server], predefined
- predefined XML schema collections [SQL Server]
- XML schema collections [SQL Server], predefined
- built-in XML schema collections [SQL Server]
ms.assetid: 1e118303-5df0-4ee4-bd8d-14ced7544144
author: rothja
ms.author: jroth
ms.openlocfilehash: 7fa30107e1746b33e3f9b8eb1cfa53d1f4d25fb8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688644"
---
# <a name="reference-the-built-in-xml-schema-collection-sys"></a><span data-ttu-id="7b269-102">引用内置 XML 架构集合 (sys)</span><span class="sxs-lookup"><span data-stu-id="7b269-102">Reference the Built-in XML Schema Collection (sys)</span></span>
  <span data-ttu-id="7b269-103">创建的每个数据库在 **sys** 关系架构中都有一个预定义的 **sys** XML 架构集合。</span><span class="sxs-lookup"><span data-stu-id="7b269-103">Every database you create has a predefined **sys** XML schema collection in the **sys** relational schema.</span></span> <span data-ttu-id="7b269-104">数据库将保留这些预定义架构，这些架构可以从任何其他用户创建的 XML 架构集合进行访问。</span><span class="sxs-lookup"><span data-stu-id="7b269-104">It reserves these predefined schemas, and they can be accessed from any other user-created XML schema collection.</span></span> <span data-ttu-id="7b269-105">这些预定义架构中使用的前缀在 XQuery 中是有意义的。</span><span class="sxs-lookup"><span data-stu-id="7b269-105">The prefixes used in these predefined schemas are meaningful in XQuery.</span></span> <span data-ttu-id="7b269-106">只有 **xml** 是保留前缀。</span><span class="sxs-lookup"><span data-stu-id="7b269-106">Only **xml** is a reserved prefix.</span></span>  
  
```  
xml = http://www.w3.org/XML/1998/namespace  
xs = http://www.w3.org/2001/XMLSchema  
xsi = http://www.w3.org/2001/XMLSchema-instance  
fn = http://www.w3.org/2004/07/xpath-functions  
sqltypes = https://schemas.microsoft.com/sqlserver/2004/sqltypes  
xdt = http://www.w3.org/2004/07/xpath-datatypes  
(no prefix) = urn:schemas-microsoft-com:xml-sql  
(no prefix) = https://schemas.microsoft.com/sqlserver/2004/SOAP  
```  
  
 <span data-ttu-id="7b269-107">注意， **sqltypes** 命名空间包含可以从任何用户创建的 XML 架构集合引用的组件。</span><span class="sxs-lookup"><span data-stu-id="7b269-107">Note that the **sqltypes** namespace contains components that can be referenced from any user-created XML schema collection.</span></span> <span data-ttu-id="7b269-108">可以从 **Microsoft Web site** 下载 [sqltypes](https://go.microsoft.com/fwlink/?linkid=31850)架构。</span><span class="sxs-lookup"><span data-stu-id="7b269-108">You can download the **sqltypes** schema from this [Microsoft Web site](https://go.microsoft.com/fwlink/?linkid=31850).</span></span> <span data-ttu-id="7b269-109">内置组件包括：</span><span class="sxs-lookup"><span data-stu-id="7b269-109">The built-in components include the following:</span></span>  
  
-   <span data-ttu-id="7b269-110">XSD 类型</span><span class="sxs-lookup"><span data-stu-id="7b269-110">XSD types</span></span>  
  
-   <span data-ttu-id="7b269-111">XML 属性 **lang**, **base**和 **space**</span><span class="sxs-lookup"><span data-stu-id="7b269-111">XML attributes **lang**, **base**, and **space**</span></span>  
  
-   <span data-ttu-id="7b269-112">**sqltypes** 命名空间的组件</span><span class="sxs-lookup"><span data-stu-id="7b269-112">Components of the **sqltypes** namespace</span></span>  
  
 <span data-ttu-id="7b269-113">下面的查询将返回可以从用户创建的 XML 架构集合引用的内置组件：</span><span class="sxs-lookup"><span data-stu-id="7b269-113">The following query returns built-in components that can be referenced from a user-created XML schema collection:</span></span>  
  
```  
SELECT C.name, N.name, C.symbol_space_desc from sys.xml_schema_components C join sys.xml_schema_namespaces N  
on ((C.xml_namespace_id = N.xml_namespace_id) AND (C.xml_collection_id = N.xml_collection_id))  
join sys.xml_schema_collections SC  
on SC.xml_collection_id = C.xml_collection_id  
where ((C.xml_collection_id = 1) AND (C.name is not null) AND (C.scoping_xml_component_id is null)   
AND (SC.schema_id = 4))  
GO  
```  
  
 <span data-ttu-id="7b269-114">以下示例说明如何在用户架构中引用这些组件。</span><span class="sxs-lookup"><span data-stu-id="7b269-114">The following example shows how these components are referenced in a user schema.</span></span> <span data-ttu-id="7b269-115">`CREATE XML SCHEMA COLLECTION` 可创建引用在 `varchar` 命名空间中定义的 `sqltypes` 类型的 XML 架构集。</span><span class="sxs-lookup"><span data-stu-id="7b269-115">`CREATE XML SCHEMA COLLECTION` creates an XML schema collection that references the `varchar` type defined in the `sqltypes` namespace.</span></span> <span data-ttu-id="7b269-116">该示例还引用了在 `lang` 命名空间中定义的 `xml` 属性。</span><span class="sxs-lookup"><span data-stu-id="7b269-116">The example also references the `lang` attribute that is defined in the `xml` namespace.</span></span>  
  
```  
CREATE XML SCHEMA COLLECTION SC AS '  
<schema   
   xmlns="http://www.w3.org/2001/XMLSchema"   
   targetNamespace="myNS"  
   xmlns:ns="myNS"  
   xmlns:s="https://schemas.microsoft.com/sqlserver/2004/sqltypes" >   
   <import namespace="http://www.w3.org/XML/1998/namespace"/>  
   <import namespace="https://schemas.microsoft.com/sqlserver/2004/sqltypes"/>  
   <element name="root">  
      <complexType>  
          <sequence>  
             <element name="a" type="string"/>  
             <element name="b" type="string"/>  
             <!-- varchar type is defined in the sys.sys collection and   
                  can be referenced in any user-defined schema -->  
             <element name="c" type="s:varchar"/>  
          </sequence>  
          <attribute name="att" type="int"/>  
          <!-- xml:lang attribute is defined in the sys.sys collection   
               and can be referenced in any user-defined schema -->  
          <attribute ref="xml:lang"/>  
      </complexType>  
    </element>  
 </schema>'  
GO  
 -- Cleanup  
DROP xml schema collection SC   
GO  
```  
  
 <span data-ttu-id="7b269-117">您应当注意下列问题：</span><span class="sxs-lookup"><span data-stu-id="7b269-117">You should note the following:</span></span>  
  
-   <span data-ttu-id="7b269-118">您不能在任何用户定义的 XML 架构集合中使用这些命名空间来修改 XML 架构。</span><span class="sxs-lookup"><span data-stu-id="7b269-118">You cannot modify XML schemas with these namespaces in any user-defined XML schema collection.</span></span> <span data-ttu-id="7b269-119">例如，由于正在向受保护的命名空间 `sqltypes` 添加组件，下面的 XML 架构集合将失败：</span><span class="sxs-lookup"><span data-stu-id="7b269-119">For example, the following XML schema collection fails, because it is adding a component to the `sqltypes` protected namespace:</span></span>  
  
    ```  
    CREATE XML SCHEMA COLLECTION SC AS '  
    <schema xmlns="http://www.w3.org/2001/XMLSchema"   
    targetNamespace    
        ="https://schemas.microsoft.com/sqlserver/2004/sqltypes" >   
          <element name="root" type="string"/>  
    </schema>'  
    GO  
    ```  
  
-   <span data-ttu-id="7b269-120">您不能使用 `sys` XML 架构集类型化 `xml` 列、变量或参数。</span><span class="sxs-lookup"><span data-stu-id="7b269-120">You cannot use the `sys` XML schema collection to type `xml` columns, variables, or parameters.</span></span> <span data-ttu-id="7b269-121">例如，下面的代码将返回错误：</span><span class="sxs-lookup"><span data-stu-id="7b269-121">For example, the following code returns an error:</span></span>  
  
    ```  
    DECLARE @x xml (sys.sys)  
    ```  
  
-   <span data-ttu-id="7b269-122">不支持序列化这些内置架构。</span><span class="sxs-lookup"><span data-stu-id="7b269-122">Serialization of these built-in schemas is not supported.</span></span> <span data-ttu-id="7b269-123">例如，下面的代码将返回错误：</span><span class="sxs-lookup"><span data-stu-id="7b269-123">For example, the following code returns an error:</span></span>  
  
    ```  
    SELECT XML_SCHEMA_NAMESPACE(N'sys',N'sys')  
    GO  
    ```  
  
 <span data-ttu-id="7b269-124">下面的代码是另一个示例，其中创建了使用在 `varchar` 命名空间中定义的 `sqltypes` 类型的 XML 架构集。</span><span class="sxs-lookup"><span data-stu-id="7b269-124">The following code is another example in which you create an XML schema collection that uses the `varchar` type defined in the `sqltypes` namespace:</span></span>  
  
```  
CREATE XML SCHEMA COLLECTION SC AS '  
<schema xmlns="http://www.w3.org/2001/XMLSchema"   
        targetNamespace="myNS" xmlns:ns="myNS"  
        xmlns:s="https://schemas.microsoft.com/sqlserver/2004/sqltypes">  
   <import     
     namespace="https://schemas.microsoft.com/sqlserver/2004/sqltypes"/>  
      <simpleType name="myType">  
            <restriction base="s:varchar">  
                  <maxLength value="20"/>  
            </restriction>  
      </simpleType>  
      <element name="root" type="ns:myType"/>  
</schema>'  
go  
```  
  
 <span data-ttu-id="7b269-125">如下所示，您可以创建类型化的 `XML` 变量，为其分配一个 XML 实例，并验证 <`root`> 元素类型的值是否是 `varchar` 类型。</span><span class="sxs-lookup"><span data-stu-id="7b269-125">As shown in the following, you can create a typed `XML` variable, assign an XML instance to it, and verify that the value of the <`root`> element type is a `varchar` type.</span></span>  
  
```  
DECLARE @var XML(SC)  
SET @var = '<root xmlns="myNS">My data</root>'  
SELECT @var.query('declare namespace sqltypes = "https://schemas.microsoft.com/sqlserver/2004/sqltypes";  
declare namespace ns="myNS";   
data(/ns:root[1]) instance of sqltypes:varchar?')  
GO  
```  
  
 <span data-ttu-id="7b269-126">由于 <`root`> 元素值的类型是根据与 `@var` 变量关联的架构从 **varchar** 中派生，因此，`instance of sqltypes:varchar?` 表达式返回 TRUE。</span><span class="sxs-lookup"><span data-stu-id="7b269-126">The `instance of sqltypes:varchar?` expression returns TRUE, because the <`root`> element value is of a type derived from **varchar** according to the schema that is associated with the `@var` variable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b269-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7b269-127">See Also</span></span>  
 [<span data-ttu-id="7b269-128">XML 架构集合 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="7b269-128">XML Schema Collections &#40;SQL Server&#41;</span></span>](xml-schema-collections-sql-server.md)  
  
  
