---
title: 使用 targetNamespace 属性指定目标命名空间 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- namespaces [SQLXML], annotated XSD schemas
- targetNamespace attribute
- XSD schemas [SQLXML], target namespaces
- annotated XSD schemas, target namespaces
- xsd:targetNamespace
- attributeFormDefault attribute
- elementFormDefault attribute
- target namespaces [SQLXML]
ms.assetid: f3df9877-6672-4444-8245-2670063c9310
author: rothja
ms.author: jroth
ms.openlocfilehash: 823bcbf7f4906a2e1d2ced1ff58b681c0ca41a8b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590123"
---
# <a name="specifying-a-target-namespace-using-the-targetnamespace-attribute-sqlxml-40"></a><span data-ttu-id="febcd-102">使用 targetNamespace 属性指定目标命名空间 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="febcd-102">Specifying a Target Namespace Using the targetNamespace Attribute (SQLXML 4.0)</span></span>
  <span data-ttu-id="febcd-103">在编写 XSD 架构时，可以使用 XSD **targetNamespace**属性指定目标命名空间。</span><span class="sxs-lookup"><span data-stu-id="febcd-103">In writing XSD schemas, you can use the XSD **targetNamespace** attribute to specify a target namespace.</span></span> <span data-ttu-id="febcd-104">本主题介绍 XSD **targetNamespace**、 **elementFormDefault**和**attributeFormDefault**属性如何工作，如何影响生成的 XML 实例，以及如何使用命名空间指定 XPath 查询。</span><span class="sxs-lookup"><span data-stu-id="febcd-104">This topic describes how the XSD **targetNamespace**, **elementFormDefault**, and **attributeFormDefault** attributes work, how they affect the XML instance that is generated, and how XPath queries are specified with namespaces.</span></span>  
  
 <span data-ttu-id="febcd-105">您可以使用**xsd： targetNamespace**属性将默认命名空间中的元素和属性放入不同的命名空间中。</span><span class="sxs-lookup"><span data-stu-id="febcd-105">You can use the **xsd:targetNamespace** attribute to place elements and attributes from the default namespace into a different namespace.</span></span> <span data-ttu-id="febcd-106">还可以指定在显示局部声明的架构元素和属性时，是否应由命名空间限定（使用前缀显式限定或默认隐式限定）。</span><span class="sxs-lookup"><span data-stu-id="febcd-106">You can also specify whether the locally declared elements and attributes of the schema should appear qualified by a namespace, either explicitly by using a prefix or implicitly by default.</span></span> <span data-ttu-id="febcd-107">您可以使用元素上的**elementFormDefault**和**attributeFormDefault**属性 **\<xsd:schema>** 来全局指定本地元素和属性的限定，或者可以使用**窗体**属性单独指定单独的元素和属性。</span><span class="sxs-lookup"><span data-stu-id="febcd-107">You can use the **elementFormDefault** and **attributeFormDefault** attributes on the **\<xsd:schema>** element to globally specify the qualification of local elements and attributes, or you can use the **form** attribute to specify individual elements and attributes separately.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="febcd-108">示例</span><span class="sxs-lookup"><span data-stu-id="febcd-108">Examples</span></span>  
 <span data-ttu-id="febcd-109">若要创建使用以下示例的工作示例，必须满足某些要求。</span><span class="sxs-lookup"><span data-stu-id="febcd-109">To create working samples using the following examples, you must meet certain requirements.</span></span> <span data-ttu-id="febcd-110">有关详细信息，请参阅[运行 SQLXML 示例的要求](../sqlxml/requirements-for-running-sqlxml-examples.md)。</span><span class="sxs-lookup"><span data-stu-id="febcd-110">For more information, see [Requirements for Running SQLXML Examples](../sqlxml/requirements-for-running-sqlxml-examples.md).</span></span>  
  
### <a name="a-specifying-a-target-namespace"></a><span data-ttu-id="febcd-111">A.</span><span class="sxs-lookup"><span data-stu-id="febcd-111">A.</span></span> <span data-ttu-id="febcd-112">指定目标命名空间</span><span class="sxs-lookup"><span data-stu-id="febcd-112">Specifying a target namespace</span></span>  
 <span data-ttu-id="febcd-113">以下 XSD 架构使用**XSD： targetNamespace**属性指定目标命名空间。</span><span class="sxs-lookup"><span data-stu-id="febcd-113">The following XSD schema specifies a target namespace by using the **xsd:targetNamespace** attribute.</span></span> <span data-ttu-id="febcd-114">该架构还会将**elementFormDefault**和**attributeFormDefault**属性值设置为 **"未限定"** (这些属性) 的默认值。</span><span class="sxs-lookup"><span data-stu-id="febcd-114">The schema also sets the **elementFormDefault** and **attributeFormDefault** attribute values to **"unqualified"** (the default value for these attributes).</span></span> <span data-ttu-id="febcd-115">这是一种全局声明，它会影响架构中 (**\<Order>**) 和属性中的所有本地元素 (**CustomerID**、"**联系人姓名**" 和 "**订单 id** ") 。</span><span class="sxs-lookup"><span data-stu-id="febcd-115">This is a global declaration and affects all the local elements (**\<Order>** in the schema) and attributes (**CustomerID**, **ContactName**, and **OrderID** in the schema).</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema"  
            xmlns:CO="urn:MyNamespace"   
            targetNamespace="urn:MyNamespace" >  
<xsd:annotation>  
  <xsd:appinfo>  
    <sql:relationship name="CustOrders"  
          parent="Sales.Customer"  
          parent-key="CustomerID"  
          child="Sales.SalesOrderHeader"  
          child-key="CustomerID" />  
  </xsd:appinfo>  
</xsd:annotation>  
  
  <xsd:element name="Customer"   
               sql:relation="Sales.Customer"   
               type="CO:CustomerType" />  
  
  <xsd:complexType name="CustomerType" >  
     <xsd:sequence>  
        <xsd:element name="Order"   
                     sql:relation="Sales.SalesOrderHeader"  
                     sql:relationship="CustOrders"  
                     type="CO:OrderType" />  
     </xsd:sequence>  
        <xsd:attribute name="CustomerID"   type="xsd:string" />   
        <xsd:attribute name="SalesPersonID"  type="xsd:string" />  
  </xsd:complexType>  
  <xsd:complexType name="OrderType" >  
     <xsd:attribute name="SalesOrderID" type="xsd:integer" />  
     <xsd:attribute name="CustomerID" type="xsd:string" />  
  </xsd:complexType>  
</xsd:schema>  
```  
  
 <span data-ttu-id="febcd-116">在架构中：</span><span class="sxs-lookup"><span data-stu-id="febcd-116">In the schema:</span></span>  
  
-   <span data-ttu-id="febcd-117">**CustomerType**和**OrderType**类型声明是全局的，因此包含在架构的目标命名空间中。</span><span class="sxs-lookup"><span data-stu-id="febcd-117">The **CustomerType** and **OrderType** type declarations are global and, therefore, are included in the schema's target namespace.</span></span> <span data-ttu-id="febcd-118">因此，当在元素及其子元素的声明中引用这些类型时 **\<Customer>** **\<Order>** ，将指定与目标命名空间关联的前缀。</span><span class="sxs-lookup"><span data-stu-id="febcd-118">As a result, when these types are referenced in the declaration of **\<Customer>** element and its **\<Order>** child element, a prefix is specified that is associated with the target namespace.</span></span>  
  
-   <span data-ttu-id="febcd-119">**\<Customer>** 元素也包含在架构的目标命名空间中，因为它是架构中的全局元素。</span><span class="sxs-lookup"><span data-stu-id="febcd-119">The **\<Customer>** element is also included in the target namespace of the schema because it is a global element in the schema.</span></span>  
  
 <span data-ttu-id="febcd-120">针对该架构执行以下 XPath 查询：</span><span class="sxs-lookup"><span data-stu-id="febcd-120">Execute the following XPath query against the schema:</span></span>  
  
```  
(/CO:Customer[@CustomerID=1)   
```  
  
 <span data-ttu-id="febcd-121">该 XPath 查询生成以下实例文档（仅显示了一部分订单）：</span><span class="sxs-lookup"><span data-stu-id="febcd-121">The XPath query generates this instance document (only a few of the orders are shown):</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <y0:Customer xmlns:y0="urn:MyNamespace"   
      CustomerID="ALFKI" ContactName="Maria Anders">  
        <Order CustomerID="ALFKI" OrderID="10643" />   
        <Order CustomerID="ALFKI" OrderID="10692" />   
        ...  
  </y0:Customer>  
  </ROOT>  
```  
  
 <span data-ttu-id="febcd-122">此实例文档定义了 urn： MyNamespace 命名空间，并将前缀 (y0) 关联到该命名空间。</span><span class="sxs-lookup"><span data-stu-id="febcd-122">This instance document defines the urn:MyNamespace namespace and associates a prefix (y0) to it.</span></span> <span data-ttu-id="febcd-123">前缀仅应用于 **\<Customer>** 全局元素。</span><span class="sxs-lookup"><span data-stu-id="febcd-123">The prefix is applied only to the **\<Customer>** global element.</span></span> <span data-ttu-id="febcd-124"> (元素是全局性的，因为它在架构中声明为元素的子元素 **\<xsd:schema>** 。 ) </span><span class="sxs-lookup"><span data-stu-id="febcd-124">(The element is global because it is declared as a child of **\<xsd:schema>** element in the schema.)</span></span>  
  
 <span data-ttu-id="febcd-125">前缀不适用于本地元素和属性，因为**elementFormDefault**和**attributeFormDefault**属性的值在架构中设置为 **"非限定"** 。</span><span class="sxs-lookup"><span data-stu-id="febcd-125">The prefix is not applied to the local elements and attributes because the value of **elementFormDefault** and **attributeFormDefault** attributes is set to **"unqualified"** in the schema.</span></span> <span data-ttu-id="febcd-126">请注意， **\<Order>** 元素是局部的，因为其声明显示为 **\<complexType>** 定义元素的元素的子元素 **\<CustomerType>** 。</span><span class="sxs-lookup"><span data-stu-id="febcd-126">Note that the **\<Order>** element is local because its declaration appears as a child of the **\<complexType>** element that defines the **\<CustomerType>** element.</span></span> <span data-ttu-id="febcd-127">同样， (**CustomerID**、**订单 Id**和**联系人姓名**) 的属性都是本地的，而不是全局的。</span><span class="sxs-lookup"><span data-stu-id="febcd-127">Similarly, the attributes (**CustomerID**, **OrderID**, and **ContactName**) are local, not global.</span></span>  
  
##### <a name="to-create-a-working-sample-of-this-schema"></a><span data-ttu-id="febcd-128">创建此架构的工作示例</span><span class="sxs-lookup"><span data-stu-id="febcd-128">To create a working sample of this schema</span></span>  
  
1.  <span data-ttu-id="febcd-129">复制上面的架构代码，并将它粘贴到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="febcd-129">Copy the schema code above and paste it into a text file.</span></span> <span data-ttu-id="febcd-130">将文件另存为 targetNameSpace.xml。</span><span class="sxs-lookup"><span data-stu-id="febcd-130">Save the file as targetNameSpace.xml.</span></span>  
  
2.  <span data-ttu-id="febcd-131">复制以下模板，并将它粘贴到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="febcd-131">Copy the following template and paste it into a text file.</span></span> <span data-ttu-id="febcd-132">在保存 targetNamespace.xml 的目录中将该文件另存为 targetNameSpaceT.xml。</span><span class="sxs-lookup"><span data-stu-id="febcd-132">Save the file as targetNameSpaceT.xml in the same directory where you saved targetNamespace.xml.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="targetNamespace.xml"  
                       xmlns:CO="urn:MyNamespace" >  
        /CO:Customer[@CustomerID=1]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="febcd-133">模板中的 XPath 查询 **\<Customer>** 为 CustomerID 为1的客户返回元素。</span><span class="sxs-lookup"><span data-stu-id="febcd-133">The XPath query in the template returns the **\<Customer>** element for the customer with a CustomerID of 1.</span></span> <span data-ttu-id="febcd-134">请注意，XPath 查询为查询中的元素（而不是属性）指定命名空间前缀。</span><span class="sxs-lookup"><span data-stu-id="febcd-134">Note that the XPath query specifies the namespace prefix for the element in the query and not for the attribute.</span></span> <span data-ttu-id="febcd-135">（根据架构中的指定，未限定局部属性。）</span><span class="sxs-lookup"><span data-stu-id="febcd-135">(Local attributes are not qualified, as specified in the schema.)</span></span>  
  
     <span data-ttu-id="febcd-136">为映射架构 (targetNamespace.xml) 指定的目录路径是相对于模板保存目录的相对路径。</span><span class="sxs-lookup"><span data-stu-id="febcd-136">The directory path specified for the mapping schema (targetNamespace.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="febcd-137">也可以指定绝对路径，例如：</span><span class="sxs-lookup"><span data-stu-id="febcd-137">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\targetNamepsace.xml"  
    ```  
  
3.  <span data-ttu-id="febcd-138">创建并使用 SQLXML 4.0 测试脚本 (Sqlxml4test.vbs) 执行该模板。</span><span class="sxs-lookup"><span data-stu-id="febcd-138">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="febcd-139">有关详细信息，请参阅[使用 ADO 执行 SQLXML 查询](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="febcd-139">For more information, see [Using ADO to Execute SQLXML Queries](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="febcd-140">如果架构指定了值为 **"限定"** 的**elementFormDefault**和**attributeFormDefault**属性，实例文档将具有限定的所有局部元素和属性。</span><span class="sxs-lookup"><span data-stu-id="febcd-140">If the schema specifies **elementFormDefault** and **attributeFormDefault** attributes with value **"qualified"**, the instance document will have all of the local elements and attributes qualified.</span></span> <span data-ttu-id="febcd-141">您可以更改以前的架构以在元素中包含这些属性 **\<xsd:schema>** ，并再次执行模板。</span><span class="sxs-lookup"><span data-stu-id="febcd-141">You can change the previous schema to include these attributes in the **\<xsd:schema>** element and execute the template again.</span></span> <span data-ttu-id="febcd-142">由于当前在实例中也限定了这些属性，XPath 查询将改为包括命名空间前缀。</span><span class="sxs-lookup"><span data-stu-id="febcd-142">Because the attributes are now also qualified in the instance, the XPath query will change to include the namespace prefix.</span></span>  
  
 <span data-ttu-id="febcd-143">下面是修改后的 XPath 查询：</span><span class="sxs-lookup"><span data-stu-id="febcd-143">This is the revised XPath query:</span></span>  
  
```  
/CO:Customer[@CO:CustomerID=1]  
```  
  
 <span data-ttu-id="febcd-144">下面是返回的 XML 文档：</span><span class="sxs-lookup"><span data-stu-id="febcd-144">This is the XML document that is returned:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
   <y0:Customer xmlns:y0="urn:MyNamespace" CustomerID="1" SalesPersonID="280">  
      <Order SalesOrderID="43860" CustomerID="1" />   
      <Order SalesOrderID="44501" CustomerID="1" />   
      <Order SalesOrderID="45283" CustomerID="1" />   
      <Order SalesOrderID="46042" CustomerID="1" />   
   </y0:Customer>  
</ROOT>  
```  
  
  
