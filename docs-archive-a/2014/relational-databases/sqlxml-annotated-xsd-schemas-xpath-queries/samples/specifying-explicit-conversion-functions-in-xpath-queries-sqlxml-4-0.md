---
title: " (SQLXML 4.0) 在 XPath 查询中指定显式转换函数 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- explicit conversion functions [SQLXML]
- string function
- number function
- XPath queries [SQLXML], explicit conversion functions
ms.assetid: 1111cb5d-2bd9-4bdb-8de2-dc0e47452dd6
author: rothja
ms.author: jroth
ms.openlocfilehash: 5b4b9bd5f5665c8cb86cb74c1397e2bd06e113fb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577476"
---
# <a name="specifying-explicit-conversion-functions-in-xpath-queries-sqlxml-40"></a><span data-ttu-id="3fcce-102">在 XPath 查询中指定显式转换函数 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="3fcce-102">Specifying Explicit Conversion Functions in XPath Queries (SQLXML 4.0)</span></span>
  <span data-ttu-id="3fcce-103">以下示例显示如何在 XPath 查询中指定显式转换函数。</span><span class="sxs-lookup"><span data-stu-id="3fcce-103">The following examples show how explicit conversion functions are specified in XPath queries.</span></span> <span data-ttu-id="3fcce-104">这些示例中的 XPath 查询是针对 SampleSchema1.xml 中包含的映射架构指定的。</span><span class="sxs-lookup"><span data-stu-id="3fcce-104">The XPath queries in these examples are specified against the mapping schema contained in SampleSchema1.xml.</span></span> <span data-ttu-id="3fcce-105">有关此示例架构的信息，请参阅[&#40;SQLXML 4.0&#41;的 XPath 批注的 XSD 架构示例](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="3fcce-105">For information about this sample schema, see [Sample Annotated XSD Schema for XPath Examples &#40;SQLXML 4.0&#41;](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="3fcce-106">示例</span><span class="sxs-lookup"><span data-stu-id="3fcce-106">Examples</span></span>  
  
### <a name="a-use-the-number-explicit-conversion-function"></a><span data-ttu-id="3fcce-107">A.</span><span class="sxs-lookup"><span data-stu-id="3fcce-107">A.</span></span> <span data-ttu-id="3fcce-108">使用 number() 显式转换函数</span><span class="sxs-lookup"><span data-stu-id="3fcce-108">Use the number() explicit conversion function</span></span>  
 <span data-ttu-id="3fcce-109">`number()` 函数将参数转换为数字。</span><span class="sxs-lookup"><span data-stu-id="3fcce-109">The `number()` function converts an argument to a number.</span></span>  
  
 <span data-ttu-id="3fcce-110">假设**ContactID**的值是非数字的，则以下查询会将**ContactID**转换为数字，并将其与值4进行比较。</span><span class="sxs-lookup"><span data-stu-id="3fcce-110">Assuming the value of **ContactID** is nonnumeric, the following query converts **ContactID** to a number and compares it with the value 4.</span></span> <span data-ttu-id="3fcce-111">然后，该查询将返回 **\<Employee>** 上下文节点的所有子元素，该属性的**ContactID**属性的数值为4：</span><span class="sxs-lookup"><span data-stu-id="3fcce-111">The query then returns all **\<Employee>** element children of the context node with the **ContactID** attribute that has a numeric value of 4:</span></span>  
  
```  
/child::Contact[number(attribute::ContactID)= 4]  
```  
  
 <span data-ttu-id="3fcce-112">可以指定 `attribute` 轴 (@) 的快捷方式，由于 `child` 轴是默认值，因此可以在查询中省略它：</span><span class="sxs-lookup"><span data-stu-id="3fcce-112">A shortcut to the `attribute` axis (@) can be specified, and because the `child` axis is the default, it can be omitted from the query:</span></span>  
  
```  
/Contact[number(@ContactID) = 4]  
```  
  
 <span data-ttu-id="3fcce-113">在关系术语中，查询返回**ContactID**为4的雇员。</span><span class="sxs-lookup"><span data-stu-id="3fcce-113">In relational terms, the query returns an employee with a **ContactID** of 4.</span></span>  
  
##### <a name="to-test-the-xpath-query-against-the-mapping-schema"></a><span data-ttu-id="3fcce-114">针对映射架构测试 XPath 查询</span><span class="sxs-lookup"><span data-stu-id="3fcce-114">To test the XPath query against the mapping schema</span></span>  
  
1.  <span data-ttu-id="3fcce-115">复制[示例架构代码](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md)，并将其粘贴到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="3fcce-115">Copy the [sample schema code](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) and paste it into a text file.</span></span> <span data-ttu-id="3fcce-116">将该文件另存为 SampleSchema1.xml。</span><span class="sxs-lookup"><span data-stu-id="3fcce-116">Save the file as SampleSchema1.xml.</span></span>  
  
2.  <span data-ttu-id="3fcce-117">创建以下模板 (ExplicitConversionA.xml)，并将它保存在保存 SampleSchema1.xml 的目录中。</span><span class="sxs-lookup"><span data-stu-id="3fcce-117">Create the following template (ExplicitConversionA.xml) and save it in the directory where SampleSchema1.xml was saved.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="SampleSchema1.xml">  
        /Contact[number(@ContactID)=4]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="3fcce-118">为映射架构 (SampleSchema1.xml) 指定的目录路径是相对于模板保存目录的相对路径。</span><span class="sxs-lookup"><span data-stu-id="3fcce-118">The directory path specified for the mapping schema (SampleSchema1.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="3fcce-119">也可以指定绝对路径，例如：</span><span class="sxs-lookup"><span data-stu-id="3fcce-119">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\SampleSchema1.xml"  
    ```  
  
3.  <span data-ttu-id="3fcce-120">创建并使用 SQLXML 4.0 测试脚本 (Sqlxml4test.vbs) 执行该模板。</span><span class="sxs-lookup"><span data-stu-id="3fcce-120">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="3fcce-121">有关详细信息，请参阅[使用 ADO 执行 SQLXML 4.0 查询](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="3fcce-121">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="3fcce-122">执行该模板的结果集是：</span><span class="sxs-lookup"><span data-stu-id="3fcce-122">The result set for this template execution is:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Contact ContactID="4" LastName="Acevedo" FirstName="Humberto" Title="Sr." />   
</ROOT>  
```  
  
### <a name="b-use-the-string-explicit-conversion-function"></a><span data-ttu-id="3fcce-123">B.</span><span class="sxs-lookup"><span data-stu-id="3fcce-123">B.</span></span> <span data-ttu-id="3fcce-124">使用 string() 显式转换函数</span><span class="sxs-lookup"><span data-stu-id="3fcce-124">Use the string() explicit conversion function</span></span>  
 <span data-ttu-id="3fcce-125">`string()` 函数将参数转换为字符串。</span><span class="sxs-lookup"><span data-stu-id="3fcce-125">The `string()` function converts an argument to a string.</span></span>  
  
 <span data-ttu-id="3fcce-126">以下查询将**ContactID**转换为字符串，并将其与字符串值 "4" 进行比较。</span><span class="sxs-lookup"><span data-stu-id="3fcce-126">The following query converts **ContactID** to a string and compares it with the string value "4".</span></span> <span data-ttu-id="3fcce-127">查询返回 **\<Employee>** 上下文节点的所有子元素，其**ContactID**的字符串值为 "4"：</span><span class="sxs-lookup"><span data-stu-id="3fcce-127">The query returns all **\<Employee>** element children of the context node with a **ContactID** with a string value of "4":</span></span>  
  
```  
/child::Contact[string(attribute::ContactID)="4"]  
```  
  
 <span data-ttu-id="3fcce-128">可以指定 `attribute` 轴 (@) 的快捷方式，由于 `child` 轴是默认值，因此可以在查询中省略它：</span><span class="sxs-lookup"><span data-stu-id="3fcce-128">A shortcut to the `attribute` axis (@) can be specified, and because the `child` axis is the default, it can be omitted from the query:</span></span>  
  
```  
/Contact[string(@ContactID)="4"]  
```  
  
 <span data-ttu-id="3fcce-129">就功能而言，该查询返回与前面的示例查询相同的结果，但它是根据字符串值而不是数字值（即数字 4）完成计算。</span><span class="sxs-lookup"><span data-stu-id="3fcce-129">Functionally, this query returns the same results as the previous example query, though the evaluation is done against a string value and not the numeric value (that is, the number 4).</span></span>  
  
##### <a name="to-test-the-xpath-query-against-the-mapping-schema"></a><span data-ttu-id="3fcce-130">针对映射架构测试 XPath 查询</span><span class="sxs-lookup"><span data-stu-id="3fcce-130">To test the XPath query against the mapping schema</span></span>  
  
1.  <span data-ttu-id="3fcce-131">复制[示例架构代码](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md)，并将其粘贴到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="3fcce-131">Copy the [sample schema code](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) and paste it into a text file.</span></span> <span data-ttu-id="3fcce-132">将该文件另存为 SampleSchema1.xml。</span><span class="sxs-lookup"><span data-stu-id="3fcce-132">Save the file as SampleSchema1.xml.</span></span>  
  
2.  <span data-ttu-id="3fcce-133">创建以下模板 (ExplicitConversionB.xml)，并将它保存在保存 SampleSchema1.xml 的目录中。</span><span class="sxs-lookup"><span data-stu-id="3fcce-133">Create the following template (ExplicitConversionB.xml) and save it in the directory where SampleSchema1.xml was saved.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="SampleSchema1.xml">  
        Contact[string(@ContactID)="4"]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="3fcce-134">为映射架构 (SampleSchema1.xml) 指定的目录路径是相对于模板保存目录的相对路径。</span><span class="sxs-lookup"><span data-stu-id="3fcce-134">The directory path specified for the mapping schema (SampleSchema1.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="3fcce-135">也可以指定绝对路径，例如：</span><span class="sxs-lookup"><span data-stu-id="3fcce-135">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\SampleSchema1.xml"  
    ```  
  
3.  <span data-ttu-id="3fcce-136">创建并使用 SQLXML 4.0 测试脚本 (Sqlxml4test.vbs) 执行该模板。</span><span class="sxs-lookup"><span data-stu-id="3fcce-136">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="3fcce-137">有关详细信息，请参阅[使用 ADO 执行 SQLXML 4.0 查询](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="3fcce-137">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="3fcce-138">下面是执行该模板的结果集：</span><span class="sxs-lookup"><span data-stu-id="3fcce-138">Here is the result set of the template execution:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Contact ContactID="4" LastName="Acevedo" FirstName="Humberto" Title="Sr." />   
</ROOT>  
```  
  
  
