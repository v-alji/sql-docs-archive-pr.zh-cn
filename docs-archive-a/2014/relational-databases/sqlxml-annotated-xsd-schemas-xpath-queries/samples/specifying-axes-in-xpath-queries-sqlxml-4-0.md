---
title: 在 (SQLXML 4.0) 的 XPath 查询中指定轴 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XPath queries [SQLXML], axes
- context node [SQLXML]
- attribute axis [SQLXML]
- axis [SQLXML]
- child axis
- parent axis
- axes [SQLXML]
ms.assetid: d17b8278-da58-4576-95b4-7a92772566d8
author: rothja
ms.author: jroth
ms.openlocfilehash: f6f17404ea109bb0e687f9116b61025bbc411008
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577483"
---
# <a name="specifying-axes-in-xpath-queries-sqlxml-40"></a><span data-ttu-id="5a2f8-102">在 XPath 查询中指定轴 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="5a2f8-102">Specifying Axes in XPath Queries (SQLXML 4.0)</span></span>
  <span data-ttu-id="5a2f8-103">以下示例显示如何在 XPath 查询中指定轴。</span><span class="sxs-lookup"><span data-stu-id="5a2f8-103">The following examples show how axes are specified in XPath queries.</span></span>  
  
 <span data-ttu-id="5a2f8-104">这些示例中的 XPath 查询是针对 SampleSchema1.xml 中包含的映射架构指定的。</span><span class="sxs-lookup"><span data-stu-id="5a2f8-104">The XPath queries in these examples are specified against the mapping schema contained in SampleSchema1.xml.</span></span> <span data-ttu-id="5a2f8-105">有关此示例架构的信息，请参阅[&#40;SQLXML 4.0&#41;的 XPath 批注的 XSD 架构示例](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="5a2f8-105">For information about this sample schema, see [Sample Annotated XSD Schema for XPath Examples &#40;SQLXML 4.0&#41;](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="5a2f8-106">示例</span><span class="sxs-lookup"><span data-stu-id="5a2f8-106">Examples</span></span>  
  
### <a name="a-retrieve-child-elements-of-the-context-node"></a><span data-ttu-id="5a2f8-107">A.</span><span class="sxs-lookup"><span data-stu-id="5a2f8-107">A.</span></span> <span data-ttu-id="5a2f8-108">检索上下文节点的子元素</span><span class="sxs-lookup"><span data-stu-id="5a2f8-108">Retrieve child elements of the context node</span></span>  
 <span data-ttu-id="5a2f8-109">以下 XPath 查询选择 **\<Contact>** 上下文节点的所有子元素：</span><span class="sxs-lookup"><span data-stu-id="5a2f8-109">The following XPath query selects all the **\<Contact>** child elements of the context node:</span></span>  
  
```  
/child::Contact  
```  
  
 <span data-ttu-id="5a2f8-110">在查询中， `child` 是轴， `Contact` 是节点测试 (如果 `Contact` 是节点，则为 TRUE **\<element>** ，因为 \<element> 是与轴) 相关联的主节点类型 `child` 。</span><span class="sxs-lookup"><span data-stu-id="5a2f8-110">In the query, `child` is the axis and `Contact` is the node test (TRUE if `Contact` is an **\<element>** node, because \<element> is the primary node type associated with the `child` axis).</span></span>  
  
 <span data-ttu-id="5a2f8-111">`child` 轴为默认轴。</span><span class="sxs-lookup"><span data-stu-id="5a2f8-111">The `child` axis is the default.</span></span> <span data-ttu-id="5a2f8-112">因此，可以将该查询编写为：</span><span class="sxs-lookup"><span data-stu-id="5a2f8-112">Therefore, the query can be written as:</span></span>  
  
```  
/Contact  
```  
  
##### <a name="to-test-the-xpath-query-against-the-mapping-schema"></a><span data-ttu-id="5a2f8-113">针对映射架构测试 XPath 查询</span><span class="sxs-lookup"><span data-stu-id="5a2f8-113">To test the XPath query against the mapping schema</span></span>  
  
1.  <span data-ttu-id="5a2f8-114">复制[示例架构代码](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md)，并将其粘贴到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="5a2f8-114">Copy the [sample schema code](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) and paste it into a text file.</span></span> <span data-ttu-id="5a2f8-115">将该文件另存为 SampleSchema1.xml。</span><span class="sxs-lookup"><span data-stu-id="5a2f8-115">Save the file as SampleSchema1.xml.</span></span>  
  
2.  <span data-ttu-id="5a2f8-116">创建以下模板 (XPathAxesSampleA.xml)，并将它保存在保存 SampleSchema1.xml 的目录中。</span><span class="sxs-lookup"><span data-stu-id="5a2f8-116">Create the following template (XPathAxesSampleA.xml) and save it in the directory where SampleSchema1.xml was saved.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="SampleSchema1.xml">  
        /Contact  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="5a2f8-117">为映射架构 (SampleSchema1.xml) 指定的目录路径是相对于模板保存目录的相对路径。</span><span class="sxs-lookup"><span data-stu-id="5a2f8-117">The directory path specified for the mapping schema (SampleSchema1.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="5a2f8-118">也可以指定绝对路径，例如：</span><span class="sxs-lookup"><span data-stu-id="5a2f8-118">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\SampleSchema1.xml"  
    ```  
  
3.  <span data-ttu-id="5a2f8-119">创建并使用 SQLXML 4.0 测试脚本 (Sqlxml4test.vbs) 执行该模板。</span><span class="sxs-lookup"><span data-stu-id="5a2f8-119">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="5a2f8-120">有关详细信息，请参阅[使用 ADO 执行 SQLXML 4.0 查询](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="5a2f8-120">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="5a2f8-121">下面是执行该模板的部分结果集：</span><span class="sxs-lookup"><span data-stu-id="5a2f8-121">Here is the partial result set of the template execution:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">   
  <Contact ContactID="1" LastName="Achong" FirstName="Gustavo" Title="Mr." />   
  <Contact ContactID="2" LastName="Abel" FirstName="Catherine" Title="Ms." />   
  <Contact ContactID="3" LastName="Abercrombie" FirstName="Kim" Title="Ms." />   
  <Contact ContactID="4" LastName="Acevedo" FirstName="Humberto" Title="Sr." />  
  ...  
</ROOT>  
```  
  
### <a name="b-retrieve-grandchildren-of-the-context-node"></a><span data-ttu-id="5a2f8-122">B.</span><span class="sxs-lookup"><span data-stu-id="5a2f8-122">B.</span></span> <span data-ttu-id="5a2f8-123">检索上下文节点的孙级</span><span class="sxs-lookup"><span data-stu-id="5a2f8-123">Retrieve grandchildren of the context node</span></span>  
 <span data-ttu-id="5a2f8-124">以下 XPath 查询选择 **\<Order>** 上下文节点的元素子级的所有元素子级 **\<Customer>** ：</span><span class="sxs-lookup"><span data-stu-id="5a2f8-124">The following XPath query selects all the **\<Order>** element children of the **\<Customer>** element children of the context node:</span></span>  
  
```  
/child::Customer/child::Order  
```  
  
 <span data-ttu-id="5a2f8-125">在查询中， `child` 是轴， `Customer` 并且 `Order` 是节点测试 (如果客户和订单是节点，则这些节点测试是否为 TRUE **\<element>** ，因为 **\<element>** 节点是轴的主节点 `child`) 。</span><span class="sxs-lookup"><span data-stu-id="5a2f8-125">In the query, `child` is the axis and `Customer` and `Order` are the node tests (these node tests are TRUE if Customer and Order are **\<element>** nodes, because the **\<element>** node is the primary node for the `child` axis).</span></span> <span data-ttu-id="5a2f8-126">对于每个匹配的节点 **\<Customer>** ，会将匹配的节点 **\<Orders>** 添加到结果中。</span><span class="sxs-lookup"><span data-stu-id="5a2f8-126">For each node matching **\<Customer>**, the nodes matching **\<Orders>** are added to the result.</span></span> <span data-ttu-id="5a2f8-127">仅 **\<Order>** 在结果集中返回。</span><span class="sxs-lookup"><span data-stu-id="5a2f8-127">Only **\<Order>** is returned in the result set.</span></span>  
  
 <span data-ttu-id="5a2f8-128">`child` 轴为默认轴。</span><span class="sxs-lookup"><span data-stu-id="5a2f8-128">The `child` axis is the default.</span></span> <span data-ttu-id="5a2f8-129">因此，可以将该查询指定为：</span><span class="sxs-lookup"><span data-stu-id="5a2f8-129">Therefore, the query can be specified as:</span></span>  
  
```  
/Customer/Order  
```  
  
##### <a name="to-test-the-xpath-query-against-the-mapping-schema"></a><span data-ttu-id="5a2f8-130">针对映射架构测试 XPath 查询</span><span class="sxs-lookup"><span data-stu-id="5a2f8-130">To test the XPath query against the mapping schema</span></span>  
  
1.  <span data-ttu-id="5a2f8-131">复制[示例架构代码](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md)，并将其粘贴到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="5a2f8-131">Copy the [sample schema code](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) and paste it into a text file.</span></span> <span data-ttu-id="5a2f8-132">将该文件另存为 SampleSchema1.xml。</span><span class="sxs-lookup"><span data-stu-id="5a2f8-132">Save the file as SampleSchema1.xml.</span></span>  
  
2.  <span data-ttu-id="5a2f8-133">创建以下模板 (XPathAxesSampleB.xml)，并将它保存在以下目录中：</span><span class="sxs-lookup"><span data-stu-id="5a2f8-133">Create the following template (XPathAxesSampleB.xml) and save it in the directory where:</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="SampleSchema1.xml">  
        /Customer/Order  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="5a2f8-134">为映射架构 (SampleSchema1.xml) 指定的目录路径是相对于模板保存目录的相对路径。</span><span class="sxs-lookup"><span data-stu-id="5a2f8-134">The directory path specified for the mapping schema (SampleSchema1.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="5a2f8-135">也可以指定绝对路径，例如：</span><span class="sxs-lookup"><span data-stu-id="5a2f8-135">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\SampleSchema1.xml"  
    ```  
  
3.  <span data-ttu-id="5a2f8-136">创建并使用 SQLXML 4.0 测试脚本 (Sqlxml4test.vbs) 执行该模板。</span><span class="sxs-lookup"><span data-stu-id="5a2f8-136">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="5a2f8-137">有关详细信息，请参阅[使用 ADO 执行 SQLXML 4.0 查询](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="5a2f8-137">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="5a2f8-138">下面是执行该模板的部分结果集：</span><span class="sxs-lookup"><span data-stu-id="5a2f8-138">Here is the partial result set of the template execution:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Order SalesOrderID="Ord-43860" SalesPersonID="280"   
         OrderDate="2001-08-01T00:00:00"   
         DueDate="2001-08-13T00:00:00"   
         ShipDate="2001-08-08T00:00:00">  
  <OrderDetail ProductID="Prod-729" UnitPrice="226.8571"   
               OrderQty="1" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-732" UnitPrice="440.1742"   
               OrderQty="1" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-738" UnitPrice="220.2496"   
               OrderQty="1" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-753" UnitPrice="2576.3544"   
               OrderQty="2" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-756" UnitPrice="1049.7528"   
               OrderQty="1" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-758" UnitPrice="1049.7528"   
               OrderQty="2" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-761" UnitPrice="503.3507"   
               OrderQty="2" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-762" UnitPrice="503.3507"   
               OrderQty="1" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-763" UnitPrice="503.3507"   
               OrderQty="1" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-765" UnitPrice="503.3507"   
               OrderQty="2" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-768" UnitPrice="503.3507"   
               OrderQty="1" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-770" UnitPrice="503.3507"   
               OrderQty="1" UnitPriceDiscount="0" />   
  </Order>  
   ...  
</ROOT>  
```  
  
 <span data-ttu-id="5a2f8-139">如果将 XPath 查询指定为 `Customer/Order/OrderDetail` ，则从查询匹配的每个节点 **\<Customer>** 将导航到其 **\<Order>** 元素。</span><span class="sxs-lookup"><span data-stu-id="5a2f8-139">If the XPath query is specified as `Customer/Order/OrderDetail`, from each node matching **\<Customer>** the query navigates to its **\<Order>** elements.</span></span> <span data-ttu-id="5a2f8-140">对于每个匹配的节点 **\<Order>** ，该查询会将节点添加 **\<OrderDetail>** 到结果中。</span><span class="sxs-lookup"><span data-stu-id="5a2f8-140">And for each node matching **\<Order>**, the query adds the nodes **\<OrderDetail>** to the result.</span></span> <span data-ttu-id="5a2f8-141">仅 **\<OrderDetail>** 在结果集中返回。</span><span class="sxs-lookup"><span data-stu-id="5a2f8-141">Only **\<OrderDetail>** is returned in the result set.</span></span>  
  
### <a name="c-use--to-specify-the-parent-axis"></a><span data-ttu-id="5a2f8-142">C.</span><span class="sxs-lookup"><span data-stu-id="5a2f8-142">C.</span></span> <span data-ttu-id="5a2f8-143">使用 .</span><span class="sxs-lookup"><span data-stu-id="5a2f8-143">Use ..</span></span> <span data-ttu-id="5a2f8-144">指定父轴</span><span class="sxs-lookup"><span data-stu-id="5a2f8-144">to specify the parent axis</span></span>  
 <span data-ttu-id="5a2f8-145">下面的查询检索 **\<Order>** 具有 **\<Customer>** **CustomerID**属性值为1的父元素的所有元素。</span><span class="sxs-lookup"><span data-stu-id="5a2f8-145">The following query retrieves all the **\<Order>** elements with a parent **\<Customer>** element with a **CustomerID** attribute value of 1.</span></span> <span data-ttu-id="5a2f8-146">查询使用 `child` 谓词中的轴查找元素的父 **\<Order>** 元素。</span><span class="sxs-lookup"><span data-stu-id="5a2f8-146">The query uses the `child` axis in the predicate to find the parent of the **\<Order>** element.</span></span>  
  
```  
/child::Customer/child::Order[../@CustomerID="1"]  
```  
  
 <span data-ttu-id="5a2f8-147">`child`轴为默认轴。</span><span class="sxs-lookup"><span data-stu-id="5a2f8-147">The `child` axis is the default axis.</span></span> <span data-ttu-id="5a2f8-148">因此，可以将该查询指定为：</span><span class="sxs-lookup"><span data-stu-id="5a2f8-148">Therefore, the query can be specified as:</span></span>  
  
```  
/Customer/Order[../@CustomerID="1"]  
```  
  
 <span data-ttu-id="5a2f8-149">XPath 查询等效于：</span><span class="sxs-lookup"><span data-stu-id="5a2f8-149">The XPath query is equivalent to:</span></span>  
  
```  
/Customer[@CustomerID="1"]/Order.  
```  
  
> [!NOTE]  
>  <span data-ttu-id="5a2f8-150">XPath 查询 `/Order[../@CustomerID="1"]` 将返回错误，因为没有的父项 **\<Order>** 。</span><span class="sxs-lookup"><span data-stu-id="5a2f8-150">The XPath query `/Order[../@CustomerID="1"]` will return an error because there is no parent of **\<Order>**.</span></span> <span data-ttu-id="5a2f8-151">尽管映射架构中可能存在包含的元素，但 **\<Order>** XPath 并未在任何位置开始; 因此， **\<Order>** 被视为文档中的顶级元素类型。</span><span class="sxs-lookup"><span data-stu-id="5a2f8-151">Although there may be elements in the mapping schema that contain **\<Order>**, the XPath did not begin at any of them; consequently, **\<Order>** is considered to be the top-level element type in the document.</span></span>  
  
##### <a name="to-test-the-xpath-query-against-the-mapping-schema"></a><span data-ttu-id="5a2f8-152">针对映射架构测试 XPath 查询</span><span class="sxs-lookup"><span data-stu-id="5a2f8-152">To test the XPath query against the mapping schema</span></span>  
  
1.  <span data-ttu-id="5a2f8-153">复制[示例架构代码](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md)，并将其粘贴到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="5a2f8-153">Copy the [sample schema code](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) and paste it into a text file.</span></span> <span data-ttu-id="5a2f8-154">将该文件另存为 SampleSchema1.xml。</span><span class="sxs-lookup"><span data-stu-id="5a2f8-154">Save the file as SampleSchema1.xml.</span></span>  
  
2.  <span data-ttu-id="5a2f8-155">创建以下模板 (XPathAxesSampleC.xml)，并将它保存在以下目录中：</span><span class="sxs-lookup"><span data-stu-id="5a2f8-155">Create the following template (XPathAxesSampleC.xml) and save it in the directory where:</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="SampleSchema1.xml">  
        /Customer/Order[../@CustomerID="1"]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="5a2f8-156">为映射架构 (SampleSchema1.xml) 指定的目录路径是相对于模板保存目录的相对路径。</span><span class="sxs-lookup"><span data-stu-id="5a2f8-156">The directory path specified for the mapping schema (SampleSchema1.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="5a2f8-157">也可以指定绝对路径，例如：</span><span class="sxs-lookup"><span data-stu-id="5a2f8-157">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\SampleSchema1.xml"  
    ```  
  
3.  <span data-ttu-id="5a2f8-158">创建并使用 SQLXML 4.0 测试脚本 (Sqlxml4test.vbs) 执行该模板。</span><span class="sxs-lookup"><span data-stu-id="5a2f8-158">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="5a2f8-159">有关详细信息，请参阅[使用 ADO 执行 SQLXML 4.0 查询](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="5a2f8-159">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="5a2f8-160">下面是执行该模板的部分结果集：</span><span class="sxs-lookup"><span data-stu-id="5a2f8-160">Here is the partial result set of the template execution:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Order SalesOrderID="Ord-43860" SalesPersonID="280"   
         OrderDate="2001-08-01T00:00:00"   
         DueDate="2001-08-13T00:00:00"   
         ShipDate="2001-08-08T00:00:00">  
  <OrderDetail ProductID="Prod-729" UnitPrice="226.8571"   
               OrderQty="1" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-732" UnitPrice="440.1742"   
               OrderQty="1" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-738" UnitPrice="220.2496"   
               OrderQty="1" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-753" UnitPrice="2576.3544"   
               OrderQty="2" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-756" UnitPrice="1049.7528"   
               OrderQty="1" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-758" UnitPrice="1049.7528"   
               OrderQty="2" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-761" UnitPrice="503.3507"   
               OrderQty="2" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-762" UnitPrice="503.3507"   
               OrderQty="1" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-763" UnitPrice="503.3507"   
               OrderQty="1" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-765" UnitPrice="503.3507"   
               OrderQty="2" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-768" UnitPrice="503.3507"   
               OrderQty="1" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-770" UnitPrice="503.3507"   
               OrderQty="1" UnitPriceDiscount="0" />   
  </Order>  
   ...  
</Order>  
</ROOT>  
```  
  
### <a name="d-specify-the-attribute-axis"></a><span data-ttu-id="5a2f8-161">D.</span><span class="sxs-lookup"><span data-stu-id="5a2f8-161">D.</span></span> <span data-ttu-id="5a2f8-162">指定 attribute 轴</span><span class="sxs-lookup"><span data-stu-id="5a2f8-162">Specify the attribute axis</span></span>  
 <span data-ttu-id="5a2f8-163">以下 XPath 查询选择 **\<Customer>** **CustomerID**属性值为1的上下文节点的所有子元素：</span><span class="sxs-lookup"><span data-stu-id="5a2f8-163">The following XPath query selects all the **\<Customer>** child elements of the context node with a **CustomerID** attribute value of 1:</span></span>  
  
```  
/child::Customer[attribute::CustomerID="1"]  
```  
  
 <span data-ttu-id="5a2f8-164">在谓词中 `attribute::CustomerID` ， `attribute` 是轴， `CustomerID` 是节点测试 (如果 `CustomerID` 是属性，则节点测试为 TRUE，因为 **\<attribute>** 节点是轴的主节点 `attribute`) 。</span><span class="sxs-lookup"><span data-stu-id="5a2f8-164">In the predicate `attribute::CustomerID`, `attribute` is the axis and `CustomerID` is the node test (if `CustomerID` is an attribute the node test is TRUE, because the **\<attribute>** node is the primary node for the `attribute` axis).</span></span>  
  
 <span data-ttu-id="5a2f8-165">可以指定 `attribute` 轴的快捷方式 (@)，因为 `child` 是默认轴，因此可以在查询中省略它：</span><span class="sxs-lookup"><span data-stu-id="5a2f8-165">A shortcut to the `attribute` axis (@) can be specified, and because `child` is the default axis, it can be omitted from the query:</span></span>  
  
```  
/Customer[@CustomerID="1"]  
```  
  
##### <a name="to-test-the-xpath-query-against-the-mapping-schema"></a><span data-ttu-id="5a2f8-166">针对映射架构测试 XPath 查询</span><span class="sxs-lookup"><span data-stu-id="5a2f8-166">To test the XPath query against the mapping schema</span></span>  
  
1.  <span data-ttu-id="5a2f8-167">复制[示例架构代码](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md)，并将其粘贴到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="5a2f8-167">Copy the [sample schema code](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) and paste it into a text file.</span></span> <span data-ttu-id="5a2f8-168">将该文件另存为 SampleSchema1.xml。</span><span class="sxs-lookup"><span data-stu-id="5a2f8-168">Save the file as SampleSchema1.xml.</span></span>  
  
2.  <span data-ttu-id="5a2f8-169">创建以下模板 (XPathAxesSampleD.xml)，并将它保存在保存 SampleSchema1.xml 的目录中。</span><span class="sxs-lookup"><span data-stu-id="5a2f8-169">Create the following template (XPathAxesSampleD.xml) and save it in the directory where SampleSchema1.xml is saved.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="SampleSchema1.xml">  
        child::Customer[attribute::CustomerID="1"]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="5a2f8-170">为映射架构 (SampleSchema1.xml) 指定的目录路径是相对于模板保存目录的相对路径。</span><span class="sxs-lookup"><span data-stu-id="5a2f8-170">The directory path specified for the mapping schema (SampleSchema1.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="5a2f8-171">也可以指定绝对路径，例如：</span><span class="sxs-lookup"><span data-stu-id="5a2f8-171">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\SampleSchema1.xml"  
    ```  
  
3.  <span data-ttu-id="5a2f8-172">创建并使用 SQLXML 4.0 测试脚本 (Sqlxml4test.vbs) 执行该模板。</span><span class="sxs-lookup"><span data-stu-id="5a2f8-172">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="5a2f8-173">有关详细信息，请参阅[使用 ADO 执行 SQLXML 4.0 查询](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="5a2f8-173">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="5a2f8-174">下面是执行该模板的部分结果集：</span><span class="sxs-lookup"><span data-stu-id="5a2f8-174">Here is the partial result set of the template execution:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Customer CustomerID="1" SalesPersonID="280"   
            TerritoryID="1" AccountNumber="1"   
            CustomerType="S" Orders="Ord-43860 Ord-44501 Ord-45283 Ord-46042">  
    <Order SalesOrderID="Ord-43860" SalesPersonID="280"   
           OrderDate="2001-08-01T00:00:00"   
           DueDate="2001-08-13T00:00:00"   
           ShipDate="2001-08-08T00:00:00">  
       <OrderDetail ProductID="Prod-729" UnitPrice="226.8571"   
                    OrderQty="1" UnitPriceDiscount="0" />   
       <OrderDetail ProductID="Prod-732" UnitPrice="440.1742"   
                    OrderQty="1" UnitPriceDiscount="0" />   
       <OrderDetail ProductID="Prod-738" UnitPrice="220.2496"   
                    OrderQty="1" UnitPriceDiscount="0" />   
      ...   
    </Order>  
   ...  
  </Customer>  
</ROOT>  
```  
  
  
