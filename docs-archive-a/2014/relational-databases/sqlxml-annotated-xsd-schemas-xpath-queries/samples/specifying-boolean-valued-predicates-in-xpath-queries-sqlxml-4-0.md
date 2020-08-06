---
title: " (SQLXML 4.0) 在 XPath 查询中指定布尔值谓词 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XPath queries [SQLXML], predicates
- nested predicates
- successive predicates
- predicates [SQLXML]
- top-level predicates
- Boolean-valued predicates
- multiple predicates
ms.assetid: 5f6e7219-6911-4bca-a54b-56b95e0b43dd
author: rothja
ms.author: jroth
ms.openlocfilehash: 56f2f94ec895c5b76382d5103ca9d518b78cc899
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577479"
---
# <a name="specifying-boolean-valued-predicates-in-xpath-queries-sqlxml-40"></a><span data-ttu-id="c23df-102">在 XPath 查询中指定布尔值谓词 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="c23df-102">Specifying Boolean-Valued Predicates in XPath Queries (SQLXML 4.0)</span></span>
  <span data-ttu-id="c23df-103">以下示例显示如何在 XPath 查询中指定布尔值谓词。</span><span class="sxs-lookup"><span data-stu-id="c23df-103">The following examples show how Boolean-valued predicates are specified in XPath queries.</span></span> <span data-ttu-id="c23df-104">这些示例中的 XPath 查询是针对 SampleSchema1.xml 中包含的映射架构指定的。</span><span class="sxs-lookup"><span data-stu-id="c23df-104">The XPath queries in these examples are specified against the mapping schema contained in SampleSchema1.xml.</span></span> <span data-ttu-id="c23df-105">有关此示例架构的信息，请参阅[&#40;SQLXML 4.0&#41;的 XPath 批注的 XSD 架构示例](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="c23df-105">For information about this sample schema, see [Sample Annotated XSD Schema for XPath Examples &#40;SQLXML 4.0&#41;](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="c23df-106">示例</span><span class="sxs-lookup"><span data-stu-id="c23df-106">Examples</span></span>  
  
### <a name="a-specify-multiple-predicates"></a><span data-ttu-id="c23df-107">A.</span><span class="sxs-lookup"><span data-stu-id="c23df-107">A.</span></span> <span data-ttu-id="c23df-108">指定多个谓词</span><span class="sxs-lookup"><span data-stu-id="c23df-108">Specify multiple predicates</span></span>  
 <span data-ttu-id="c23df-109">以下 XPath 查询使用多个谓词查找给定订单 ID 和客户 ID 的订单信息：</span><span class="sxs-lookup"><span data-stu-id="c23df-109">The following XPath query uses multiple predicates to find order information for a given order ID and a customer ID:</span></span>  
  
```  
/child::Customer[attribute::CustomerID="1"]/child::Order[attribute::OrderID="Ord-43860"]  
```  
  
 <span data-ttu-id="c23df-110">可以指定 `attribute` 轴 (@) 的快捷方式，由于 `child` 轴是默认值，因此可以在查询中省略它：</span><span class="sxs-lookup"><span data-stu-id="c23df-110">A shortcut to the `attribute` axis (@) can be specified, and because the `child` axis is the default, it can be omitted from the query:</span></span>  
  
```  
/Customer[@CustomerID="1"]/Order[@SalesOrderID="Ord-43860"]  
```  
  
##### <a name="to-test-the-xpath-query-against-the-mapping-schema"></a><span data-ttu-id="c23df-111">针对映射架构测试 XPath 查询</span><span class="sxs-lookup"><span data-stu-id="c23df-111">To test the XPath query against the mapping schema</span></span>  
  
1.  <span data-ttu-id="c23df-112">复制[示例架构代码](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md)，并将其粘贴到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="c23df-112">Copy the [sample schema code](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) and paste it into a text file.</span></span> <span data-ttu-id="c23df-113">将该文件另存为 SampleSchema1.xml。</span><span class="sxs-lookup"><span data-stu-id="c23df-113">Save the file as SampleSchema1.xml.</span></span>  
  
2.  <span data-ttu-id="c23df-114">创建以下模板 (BooleanValuedPredicatesA.xml)，并将它保存在保存 SampleSchema1.xml 的目录中。</span><span class="sxs-lookup"><span data-stu-id="c23df-114">Create the following template (BooleanValuedPredicatesA.xml) and save it in the directory where SampleSchema1.xml is saved.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="SampleSchema1.xml">  
        /Customer[@CustomerID="1"]/Order[@SalesOrderID="Ord-43860"]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="c23df-115">为映射架构 (SampleSchema1.xml) 指定的目录路径是相对于模板保存目录的相对路径。</span><span class="sxs-lookup"><span data-stu-id="c23df-115">The directory path specified for the mapping schema (SampleSchema1.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="c23df-116">也可以指定绝对路径，例如：</span><span class="sxs-lookup"><span data-stu-id="c23df-116">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\SampleSchema1.xml"  
    ```  
  
3.  <span data-ttu-id="c23df-117">创建并使用 SQLXML 4.0 测试脚本 (Sqlxml4test.vbs) 执行该模板。</span><span class="sxs-lookup"><span data-stu-id="c23df-117">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="c23df-118">有关详细信息，请参阅[使用 ADO 执行 SQLXML 4.0 查询](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="c23df-118">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
     <span data-ttu-id="c23df-119">下面是结果：</span><span class="sxs-lookup"><span data-stu-id="c23df-119">Here is the result:</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <Order SalesOrderID="Ord-43860" SalesPersonID="280" OrderDate="2001-08-01T00:00:00" DueDate="2001-08-13T00:00:00" ShipDate="2001-08-08T00:00:00">  
        <OrderDetail ProductID="Prod-729" UnitPrice="226.8571" OrderQty="1" UnitPriceDiscount="0" />   
        <OrderDetail ProductID="Prod-732" UnitPrice="440.1742" OrderQty="1" UnitPriceDiscount="0" />   
        <OrderDetail ProductID="Prod-738" UnitPrice="220.2496" OrderQty="1" UnitPriceDiscount="0" />   
        <OrderDetail ProductID="Prod-753" UnitPrice="2576.3544" OrderQty="2" UnitPriceDiscount="0" />   
        <OrderDetail ProductID="Prod-756" UnitPrice="1049.7528" OrderQty="1" UnitPriceDiscount="0" />   
        <OrderDetail ProductID="Prod-758" UnitPrice="1049.7528" OrderQty="2" UnitPriceDiscount="0" />   
        <OrderDetail ProductID="Prod-761" UnitPrice="503.3507" OrderQty="2" UnitPriceDiscount="0" />   
        <OrderDetail ProductID="Prod-762" UnitPrice="503.3507" OrderQty="1" UnitPriceDiscount="0" />   
        <OrderDetail ProductID="Prod-763" UnitPrice="503.3507" OrderQty="1" UnitPriceDiscount="0" />   
        <OrderDetail ProductID="Prod-765" UnitPrice="503.3507" OrderQty="2" UnitPriceDiscount="0" />   
        <OrderDetail ProductID="Prod-768" UnitPrice="503.3507" OrderQty="1" UnitPriceDiscount="0" />   
        <OrderDetail ProductID="Prod-770" UnitPrice="503.3507" OrderQty="1" UnitPriceDiscount="0" />   
      </Order>  
    </ROOT>  
    ```  
  
### <a name="b-specify-successive-and-nested-predicates"></a><span data-ttu-id="c23df-120">B.</span><span class="sxs-lookup"><span data-stu-id="c23df-120">B.</span></span> <span data-ttu-id="c23df-121">指定连续和嵌套的谓词</span><span class="sxs-lookup"><span data-stu-id="c23df-121">Specify successive and nested predicates</span></span>  
 <span data-ttu-id="c23df-122">以下查询使用连续谓词显示。</span><span class="sxs-lookup"><span data-stu-id="c23df-122">The following query shows using successive predicates.</span></span> <span data-ttu-id="c23df-123">查询返回 **\<Customer>** 上下文节点的所有子元素，该节点的**SalesPersonID**属性的值为277， **TerritoryID**属性值为3：</span><span class="sxs-lookup"><span data-stu-id="c23df-123">The query returns all the **\<Customer>** child elements of the context node that have both a **SalesPersonID** attribute with a value of 277 and a **TerritoryID** attribute with a value of 3:</span></span>  
  
```  
/child::Customer[attribute::SalesPersonID="277"][attribute::TerritoryID="3"]  
```  
  
 <span data-ttu-id="c23df-124">查询返回 **\<Customer>** 满足谓词中指定的条件的元素。</span><span class="sxs-lookup"><span data-stu-id="c23df-124">The query returns the **\<Customer>** elements that satisfy both the conditions specified in the predicates.</span></span>  
  
 <span data-ttu-id="c23df-125">可以指定 `attribute` 轴 (@) 的快捷方式，由于 `child` 轴是默认值，因此可以在查询中省略它：</span><span class="sxs-lookup"><span data-stu-id="c23df-125">A shortcut to the `attribute` axis (@) can be specified, and because the `child` axis is the default, it can be omitted from the query:</span></span>  
  
```  
/Customer[@SalesPersonID="277"][@TerritoryID="3"]  
```  
  
 <span data-ttu-id="c23df-126">以下 XPath 查询说明嵌套谓词的用法。</span><span class="sxs-lookup"><span data-stu-id="c23df-126">The following XPath query illustrates the use of nested predicates.</span></span> <span data-ttu-id="c23df-127">查询返回 **\<Customer>** 上下文节点的所有子元素，其中包含 **\<Order>** 至少一个 **\<Order>** 元素具有**SalesPersonID**属性值2的子元素。</span><span class="sxs-lookup"><span data-stu-id="c23df-127">The query returns all the **\<Customer>** child elements of the context node that include **\<Order>** child elements with at least one **\<Order>** element that has a **SalesPersonID** attribute value of 2.</span></span>  
  
```  
/Customer[Order[@SalesPersonID=2]]  
```  
  
##### <a name="to-test-the-xpath-query-against-the-mapping-schema"></a><span data-ttu-id="c23df-128">针对映射架构测试 XPath 查询</span><span class="sxs-lookup"><span data-stu-id="c23df-128">To test the XPath query against the mapping schema</span></span>  
  
1.  <span data-ttu-id="c23df-129">复制[示例架构代码](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md)，并将其粘贴到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="c23df-129">Copy the [sample schema code](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) and paste it into a text file.</span></span> <span data-ttu-id="c23df-130">将该文件另存为 SampleSchema1.xml。</span><span class="sxs-lookup"><span data-stu-id="c23df-130">Save the file as SampleSchema1.xml.</span></span>  
  
2.  <span data-ttu-id="c23df-131">创建以下模板 (nestedSuccessive.xml)，并将它保存在保存 SampleSchema1.xml 的目录中。</span><span class="sxs-lookup"><span data-stu-id="c23df-131">Create the following template (nestedSuccessive.xml) and save it in the directory where SampleSchema1.xml is saved.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="SampleSchema1.xml">  
             /Customer[@SalesPersonID="277"][@TerritoryID="3"]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="c23df-132">为映射架构 (SampleSchema1.xml) 指定的目录路径是相对于模板保存目录的相对路径。</span><span class="sxs-lookup"><span data-stu-id="c23df-132">The directory path specified for the mapping schema (SampleSchema1.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="c23df-133">也可以指定绝对路径，例如：</span><span class="sxs-lookup"><span data-stu-id="c23df-133">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\SampleSchema1.xml"  
    ```  
  
3.  <span data-ttu-id="c23df-134">创建并使用 SQLXML 4.0 测试脚本 (Sqlxml4test.vbs) 执行该模板。</span><span class="sxs-lookup"><span data-stu-id="c23df-134">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="c23df-135">有关详细信息，请参阅[使用 ADO 执行 SQLXML 4.0 查询](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="c23df-135">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="c23df-136">下面是部分结果：</span><span class="sxs-lookup"><span data-stu-id="c23df-136">The following is a partial result:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Customer CustomerID="22" SalesPersonID="277" TerritoryID="3"   
            AccountNumber="22" CustomerType="S"   
            Orders="Ord-43874 Ord-44519 Ord-46989 Ord-48013 Ord-49130 Ord-50274 Ord-51807 Ord-57113 Ord-63162 Ord-69495">  
    <Order SalesOrderID="Ord-43874" SalesPersonID="277"   
           OrderDate="2001-08-01T00:00:00"   
           DueDate="2001-08-13T00:00:00"   
           ShipDate="2001-08-08T00:00:00">  
      <OrderDetail ProductID="Prod-763" UnitPrice="503.3507"   
                   OrderQty="1" UnitPriceDiscount="0" />   
    </Order>  
    ...  
  </Customer>  
  <Customer CustomerID="39" SalesPersonID="277" TerritoryID="3"   
            AccountNumber="39" CustomerType="S"   
            Orders="Ord-47428 Ord-48367 Ord-49529 Ord-50742 Ord-53591 Ord-59051 Ord-65301 Ord-71912">    <Order SalesOrderID="Ord-47428" SalesPersonID="277"   
           OrderDate="2002-09-01T00:00:00"   
           DueDate="2002-09-13T00:00:00"   
           ShipDate="2002-09-08T00:00:00">  
      <OrderDetail ProductID="Prod-759" UnitPrice="563.7528" OrderQty="2" UnitPriceDiscount="0" />   
      <OrderDetail ProductID="Prod-769" UnitPrice="563.7528" OrderQty="1" UnitPriceDiscount="0" />   
      ...  
    </Order>  
    ...  
  </Customer>  
  ...  
</ROOT>  
```  
  
### <a name="c-specify-a-top-level-predicate"></a><span data-ttu-id="c23df-137">C.</span><span class="sxs-lookup"><span data-stu-id="c23df-137">C.</span></span> <span data-ttu-id="c23df-138">指定顶级谓词</span><span class="sxs-lookup"><span data-stu-id="c23df-138">Specify a top-level predicate</span></span>  
 <span data-ttu-id="c23df-139">下面的查询返回 **\<Customer>** 具有元素子级的上下文节点的子元素节点 **\<Order>** 。</span><span class="sxs-lookup"><span data-stu-id="c23df-139">The following query returns the **\<Customer>** child element nodes of the context node that have **\<Order>** element children.</span></span> <span data-ttu-id="c23df-140">该查询将位置路径作为顶级谓词进行测试：</span><span class="sxs-lookup"><span data-stu-id="c23df-140">The query tests the location path as the top-level predicate:</span></span>  
  
```  
/child::Customer[child::Order]  
```  
  
 <span data-ttu-id="c23df-141">`child` 轴为默认轴。</span><span class="sxs-lookup"><span data-stu-id="c23df-141">The `child` axis is the default.</span></span> <span data-ttu-id="c23df-142">因此，可以将该查询指定为：</span><span class="sxs-lookup"><span data-stu-id="c23df-142">Therefore, the query can be specified as:</span></span>  
  
```  
/Customer[Order]  
```  
  
##### <a name="to-test-the-xpath-query-against-the-mapping-schema"></a><span data-ttu-id="c23df-143">针对映射架构测试 XPath 查询</span><span class="sxs-lookup"><span data-stu-id="c23df-143">To test the XPath query against the mapping schema</span></span>  
  
1.  <span data-ttu-id="c23df-144">复制[示例架构代码](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md)，并将其粘贴到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="c23df-144">Copy the [sample schema code](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) and paste it into a text file.</span></span> <span data-ttu-id="c23df-145">将该文件另存为 SampleSchema1.xml。</span><span class="sxs-lookup"><span data-stu-id="c23df-145">Save the file as SampleSchema1.xml.</span></span>  
  
2.  <span data-ttu-id="c23df-146">创建以下模板 (TopLevelPredicate.xml)，并将它保存在保存 SampleSchema1.xml 的目录中。</span><span class="sxs-lookup"><span data-stu-id="c23df-146">Create the following template (TopLevelPredicate.xml) and save it in the directory where SampleSchema1.xml is saved.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="SampleSchema1.xml">  
        /Customer[Order]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="c23df-147">为映射架构 (SampleSchema1.xml) 指定的目录路径是相对于模板保存目录的相对路径。</span><span class="sxs-lookup"><span data-stu-id="c23df-147">The directory path specified for the mapping schema (SampleSchema1.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="c23df-148">也可以指定绝对路径，例如：</span><span class="sxs-lookup"><span data-stu-id="c23df-148">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\SampleSchema1.xml"  
    ```  
  
3.  <span data-ttu-id="c23df-149">创建并使用 SQLXML 4.0 测试脚本 (Sqlxml4test.vbs) 执行该模板。</span><span class="sxs-lookup"><span data-stu-id="c23df-149">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="c23df-150">有关详细信息，请参阅[使用 ADO 执行 SQLXML 4.0 查询](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="c23df-150">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="c23df-151">下面是部分结果：</span><span class="sxs-lookup"><span data-stu-id="c23df-151">Here is the partial result:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Customer CustomerID="1" SalesPersonID="280" TerritoryID="1" AccountNumber="1" CustomerType="S" Orders="Ord-43860 Ord-44501 Ord-45283 Ord-46042">  
    <Order SalesOrderID="Ord-43860" SalesPersonID="280" OrderDate="2001-08-01T00:00:00" DueDate="2001-08-13T00:00:00" ShipDate="2001-08-08T00:00:00">  
      <OrderDetail ProductID="Prod-729" UnitPrice="226.8571" OrderQty="1" UnitPriceDiscount="0" />   
      <OrderDetail ProductID="Prod-732" UnitPrice="440.1742" OrderQty="1" UnitPriceDiscount="0" />   
      <OrderDetail ProductID="Prod-738" UnitPrice="220.2496" OrderQty="1" UnitPriceDiscount="0" />   
      ...  
    </Order>  
    <Order SalesOrderID="Ord-44501" SalesPersonID="280" OrderDate="2001-11-01T00:00:00" DueDate="2001-11-13T00:00:00" ShipDate="2001-11-08T00:00:00">  
      <OrderDetail ProductID="Prod-725" UnitPrice="226.8571" OrderQty="3" UnitPriceDiscount="0" />   
      <OrderDetail ProductID="Prod-726" UnitPrice="226.8571" OrderQty="2" UnitPriceDiscount="0" />   
      ...  
    </Order>    ...  
  </Customer>  
  ...  
</ROOT>  
```  
  
  
