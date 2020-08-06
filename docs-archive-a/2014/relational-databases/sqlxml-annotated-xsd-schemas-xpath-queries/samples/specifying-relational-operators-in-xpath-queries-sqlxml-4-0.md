---
title: " (SQLXML 4.0) 在 XPath 查询中指定关系运算符 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XPath queries [SQLXML], relational operators
- relational operators [SQLXML]
- XPath operators [SQLXML]
- operators [SQLXML]
ms.assetid: 177a0eb2-11ef-4459-a317-485a433ee769
author: rothja
ms.author: jroth
ms.openlocfilehash: 50d59ebd3a776386c61f4c3a8a1e892d30981d1b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577472"
---
# <a name="specifying-relational-operators-in-xpath-queries-sqlxml-40"></a><span data-ttu-id="76b70-102">在 XPath 查询中指定关系运算符 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="76b70-102">Specifying Relational Operators in XPath Queries (SQLXML 4.0)</span></span>
  <span data-ttu-id="76b70-103">以下示例显示如何在 XPath 查询中指定关系运算符。</span><span class="sxs-lookup"><span data-stu-id="76b70-103">The following examples show how relational operators are specified in XPath queries.</span></span> <span data-ttu-id="76b70-104">这些示例中的 XPath 查询是针对 SampleSchema1.xml 中包含的映射架构指定的。</span><span class="sxs-lookup"><span data-stu-id="76b70-104">The XPath queries in these examples are specified against the mapping schema contained in SampleSchema1.xml.</span></span> <span data-ttu-id="76b70-105">有关此示例架构的信息，请参阅[&#40;SQLXML 4.0&#41;的 XPath 批注的 XSD 架构示例](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="76b70-105">For information about this sample schema, see [Sample Annotated XSD Schema for XPath Examples &#40;SQLXML 4.0&#41;](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="76b70-106">示例</span><span class="sxs-lookup"><span data-stu-id="76b70-106">Examples</span></span>  
  
### <a name="a-specify-relational-operator"></a><span data-ttu-id="76b70-107">A.</span><span class="sxs-lookup"><span data-stu-id="76b70-107">A.</span></span> <span data-ttu-id="76b70-108">指定关系运算符</span><span class="sxs-lookup"><span data-stu-id="76b70-108">Specify relational operator</span></span>  
 <span data-ttu-id="76b70-109">此 XPath 查询返回元素的子元素， **\<Customer>** 其中**CustomerID**属性值为 "1"，其中任何子 **\<Order>** 元素包含 **\<OrderDetail>** 具有值大于3的**OrderQty**属性的子元素：</span><span class="sxs-lookup"><span data-stu-id="76b70-109">This XPath query returns the child elements of the **\<Customer>** element where the **CustomerID** attribute value is "1" and where any child **\<Order>** elements contain an **\<OrderDetail>** child with a **OrderQty** attribute with a value greater than 3:</span></span>  
  
```  
/child::Customer[@CustomerID="1"]/Order/OrderDetail[@OrderQty > 3]  
```  
  
 <span data-ttu-id="76b70-110">方括号中指定的谓词筛选 **\<Customer>** 元素。</span><span class="sxs-lookup"><span data-stu-id="76b70-110">The predicate specified in the brackets filters the **\<Customer>** elements.</span></span> <span data-ttu-id="76b70-111">仅 **\<Customer>** 返回至少一个具有 **\<OrderDetail>** 大于3的 OrderQty 特性值的孙元素。</span><span class="sxs-lookup"><span data-stu-id="76b70-111">Only the **\<Customer>** elements that have at least one **\<OrderDetail>** grandchild with a OrderQty attribute value greater than 3 are returned.</span></span>  
  
 <span data-ttu-id="76b70-112">`child` 轴为默认轴。</span><span class="sxs-lookup"><span data-stu-id="76b70-112">The `child` axis is the default.</span></span> <span data-ttu-id="76b70-113">因此，可以将该查询指定为：</span><span class="sxs-lookup"><span data-stu-id="76b70-113">Therefore, the query can be specified as:</span></span>  
  
```  
/Customer[@CustomerID="1"]/Order/OrderDetail[@OrderQty > 3]  
```  
  
##### <a name="to-test-the-xpath-query-against-the-mapping-schema"></a><span data-ttu-id="76b70-114">针对映射架构测试 XPath 查询</span><span class="sxs-lookup"><span data-stu-id="76b70-114">To test the XPath query against the mapping schema</span></span>  
  
1.  <span data-ttu-id="76b70-115">复制[示例架构代码](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md)，并将其粘贴到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="76b70-115">Copy the [sample schema code](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) and paste it into a text file.</span></span> <span data-ttu-id="76b70-116">将该文件另存为 SampleSchema1.xml。</span><span class="sxs-lookup"><span data-stu-id="76b70-116">Save the file as SampleSchema1.xml.</span></span>  
  
2.  <span data-ttu-id="76b70-117">创建以下模板 (SpecifyRelationalA.xml)，并将它保存在保存 SampleSchema1.xml 的目录中。</span><span class="sxs-lookup"><span data-stu-id="76b70-117">Create the following template (SpecifyRelationalA.xml) and save it in the directory where SampleSchema1.xml is saved.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="SampleSchema1.xml">  
        /Customer[@CustomerID="1"]/Order/OrderDetail[@OrderQty > 3]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="76b70-118">为映射架构 (SampleSchema1.xml) 指定的目录路径是相对于模板保存目录的相对路径。</span><span class="sxs-lookup"><span data-stu-id="76b70-118">The directory path specified for the mapping schema (SampleSchema1.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="76b70-119">也可以指定绝对路径，例如：</span><span class="sxs-lookup"><span data-stu-id="76b70-119">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\SampleSchema1.xml"  
    ```  
  
3.  <span data-ttu-id="76b70-120">创建并使用 SQLXML 4.0 测试脚本 (Sqlxml4test.vbs) 执行该模板。</span><span class="sxs-lookup"><span data-stu-id="76b70-120">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="76b70-121">有关详细信息，请参阅[使用 ADO 执行 SQLXML 4.0 查询](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="76b70-121">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="76b70-122">下面是执行该模板的结果集：</span><span class="sxs-lookup"><span data-stu-id="76b70-122">Here is the result set of the template execution:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <OrderDetail ProductID="Prod-760" UnitPrice="503.3507" OrderQty="4" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-763" UnitPrice="503.3507" OrderQty="4" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-766" UnitPrice="503.3507" OrderQty="4" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-732" UnitPrice="440.1742" OrderQty="4" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-757" UnitPrice="1049.7528" OrderQty="4" UnitPriceDiscount="0" />   
</ROOT>  
```  
  
### <a name="b-specify-relational-operator-in-the-xpath-query-and-use-boolean-function-to-compare-the-result"></a><span data-ttu-id="76b70-123">B.</span><span class="sxs-lookup"><span data-stu-id="76b70-123">B.</span></span> <span data-ttu-id="76b70-124">在 XPath 查询中指定关系运算符并使用布尔函数比较该结果</span><span class="sxs-lookup"><span data-stu-id="76b70-124">Specify relational operator in the XPath query and use Boolean function to compare the result</span></span>  
 <span data-ttu-id="76b70-125">此查询返回 **\<Order>** 上下文节点的所有子元素子级，该节点的**SalesPersonID**属性值小于270：</span><span class="sxs-lookup"><span data-stu-id="76b70-125">This query returns all the **\<Order>** element children of the context node that have an **SalesPersonID** attribute value that is less than 270:</span></span>  
  
```  
/child::Customer/child::Order[(attribute::SalesPersonID < 270)=true()]  
```  
  
 <span data-ttu-id="76b70-126">可以指定 `attribute` 轴 (@) 的快捷方式，由于 `child` 轴是默认值，因此可以在查询中省略它：</span><span class="sxs-lookup"><span data-stu-id="76b70-126">A shortcut to the `attribute` axis (@) can be specified, and because the `child` axis is the default, it can be omitted from the query:</span></span>  
  
```  
/Customer/Order[(@SalesPersonID < 270)=true()]  
```  
  
> [!NOTE]  
>  <span data-ttu-id="76b70-127">在模板中指定该查询时，必须对 < 字符进行实体编码，因为 < 字符在 XML 文档中具有特殊含义。</span><span class="sxs-lookup"><span data-stu-id="76b70-127">When this query is specified in a template, the < character must be entity encoded because the < character has special meaning in an XML document.</span></span> <span data-ttu-id="76b70-128">在模板中，使用 `<` 指定 < 字符。</span><span class="sxs-lookup"><span data-stu-id="76b70-128">In a template, use `<` to specify the < character.</span></span>  
  
##### <a name="to-test-the-xpath-query-against-the-mapping-schema"></a><span data-ttu-id="76b70-129">针对映射架构测试 XPath 查询</span><span class="sxs-lookup"><span data-stu-id="76b70-129">To test the XPath query against the mapping schema</span></span>  
  
1.  <span data-ttu-id="76b70-130">复制[示例架构代码](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md)，并将其粘贴到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="76b70-130">Copy the [sample schema code](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) and paste it into a text file.</span></span> <span data-ttu-id="76b70-131">将该文件另存为 SampleSchema1.xml。</span><span class="sxs-lookup"><span data-stu-id="76b70-131">Save the file as SampleSchema1.xml.</span></span>  
  
2.  <span data-ttu-id="76b70-132">创建以下模板 (SpecifyRelationalB.xml)，并将它保存在保存 SampleSchema1.xml 的目录中。</span><span class="sxs-lookup"><span data-stu-id="76b70-132">Create the following template (SpecifyRelationalB.xml) and save it in the directory where SampleSchema1.xml is saved.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="SampleSchema1.xml">  
            /Customer/Order[(@SalesPersonID<270)=true()]  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="76b70-133">为映射架构 (SampleSchema1.xml) 指定的目录路径是相对于模板保存目录的相对路径。</span><span class="sxs-lookup"><span data-stu-id="76b70-133">The directory path specified for the mapping schema (SampleSchema1.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="76b70-134">也可以指定绝对路径，例如：</span><span class="sxs-lookup"><span data-stu-id="76b70-134">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\SampleSchema1.xml"  
    ```  
  
3.  <span data-ttu-id="76b70-135">创建并使用 SQLXML 4.0 测试脚本 (Sqlxml4test.vbs) 执行该模板。</span><span class="sxs-lookup"><span data-stu-id="76b70-135">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="76b70-136">有关详细信息，请参阅[使用 ADO 执行 SQLXML 4.0 查询](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="76b70-136">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="76b70-137">下面是执行该模板的部分结果集：</span><span class="sxs-lookup"><span data-stu-id="76b70-137">Here is the partial result set of the template execution:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Order SalesOrderID="Ord-46613" SalesPersonID="268"   
         OrderDate="2002-07-01T00:00:00"   
         DueDate="2002-07-13T00:00:00"   
         ShipDate="2002-07-08T00:00:00">  
    <OrderDetail ProductID="Prod-739" UnitPrice="917.9363"   
                 OrderQty="2" UnitPriceDiscount="0" />   
    <OrderDetail ProductID="Prod-779" UnitPrice="1491.4221"   
                 OrderQty="1" UnitPriceDiscount="0" />   
    <OrderDetail ProductID="Prod-825" UnitPrice="242.1391"   
                 OrderQty="1" UnitPriceDiscount="0" />   
  </Order>  
  <Order SalesOrderID="Ord-71919" SalesPersonID="268"  
         OrderDate="2004-06-01T00:00:00"   
         DueDate="2004-06-13T00:00:00"   
         ShipDate="2004-06-08T00:00:00">  
    <OrderDetail ProductID="Prod-961" UnitPrice="534.492"   
                 OrderQty="1" UnitPriceDiscount="0" />   
    <OrderDetail ProductID="Prod-965" UnitPrice="534.492"   
                 OrderQty="1" UnitPriceDiscount="0" />   
    <OrderDetail ProductID="Prod-966" UnitPrice="1716.5304"   
                 OrderQty="1" UnitPriceDiscount="0" />   
  </Order>  
  ...  
</ROOT>  
```  
  
  
