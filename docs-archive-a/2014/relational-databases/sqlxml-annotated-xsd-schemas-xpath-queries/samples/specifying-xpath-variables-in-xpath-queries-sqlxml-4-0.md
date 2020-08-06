---
title: 在 (SQLXML 4.0) 的 XPath 查询中指定 XPath 变量 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XPath queries [SQLXML], XPath variables
- XPath variables [SQLXML]
ms.assetid: c11ab816-11b8-4131-8b77-c03fe500fa10
author: rothja
ms.author: jroth
ms.openlocfilehash: 5045831f627722f7dbb9a9189be5c48d830f2add
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577469"
---
# <a name="specifying-xpath-variables-in-xpath-queries-sqlxml-40"></a><span data-ttu-id="02ff5-102">在 XPath 查询中指定 XPath 变量 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="02ff5-102">Specifying XPath Variables in XPath Queries (SQLXML 4.0)</span></span>
  <span data-ttu-id="02ff5-103">以下示例说明如何在 XPath 查询中传递 XPath 变量。</span><span class="sxs-lookup"><span data-stu-id="02ff5-103">The following examples show how XPath variables are passed in XPath queries.</span></span> <span data-ttu-id="02ff5-104">这些示例中的 XPath 查询是针对 SampleSchema1.xml 中包含的映射架构指定的。</span><span class="sxs-lookup"><span data-stu-id="02ff5-104">The XPath queries in these examples are specified against the mapping schema contained in SampleSchema1.xml.</span></span> <span data-ttu-id="02ff5-105">有关此示例架构的信息，请参阅[&#40;SQLXML 4.0&#41;的 XPath 批注的 XSD 架构示例](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="02ff5-105">For information about this sample schema, see [Sample Annotated XSD Schema for XPath Examples &#40;SQLXML 4.0&#41;](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="02ff5-106">示例</span><span class="sxs-lookup"><span data-stu-id="02ff5-106">Examples</span></span>  
  
### <a name="a-use-the-xpath-variables"></a><span data-ttu-id="02ff5-107">A.</span><span class="sxs-lookup"><span data-stu-id="02ff5-107">A.</span></span> <span data-ttu-id="02ff5-108">使用 XPath 变量</span><span class="sxs-lookup"><span data-stu-id="02ff5-108">Use the XPath variables</span></span>  
 <span data-ttu-id="02ff5-109">示例模板由两个 XPath 查询构成。</span><span class="sxs-lookup"><span data-stu-id="02ff5-109">A sample template consists of two XPath queries.</span></span> <span data-ttu-id="02ff5-110">每个 XPath 查询都采用一个参数。</span><span class="sxs-lookup"><span data-stu-id="02ff5-110">Each of the XPath queries takes one parameter.</span></span> <span data-ttu-id="02ff5-111">该模板还为这些参数指定默认值。</span><span class="sxs-lookup"><span data-stu-id="02ff5-111">The template also specifies default values for these parameters.</span></span> <span data-ttu-id="02ff5-112">如果未指定参数值，则使用默认值。</span><span class="sxs-lookup"><span data-stu-id="02ff5-112">The default values are used if parameter values are not specified.</span></span> <span data-ttu-id="02ff5-113">中指定了两个具有默认值的参数 **\<sql:header>** 。</span><span class="sxs-lookup"><span data-stu-id="02ff5-113">Two parameters with default values are specified in **\<sql:header>**.</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <sql:header>  
     <sql:param name='CustomerID'>1</sql:param>  
     <sql:param name='ContactID'>1</sql:param>   
  </sql:header>  
  <sql:xpath-query mapping-schema="SampleSchema1.xml">  
    Customer[@CustomerID=$CustomerID]   
  </sql:xpath-query >  
  <sql:xpath-query mapping-schema="SampleSchema1.xml">  
   Contact[@ContactID=$ContactID]   
  </sql:xpath-query>  
</ROOT>  
```  
  
##### <a name="to-test-the-xpath-query-against-the-mapping-schema"></a><span data-ttu-id="02ff5-114">针对映射架构测试 XPath 查询</span><span class="sxs-lookup"><span data-stu-id="02ff5-114">To test the XPath query against the mapping schema</span></span>  
  
1.  <span data-ttu-id="02ff5-115">复制[示例架构代码](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md)，并将其粘贴到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="02ff5-115">Copy the [sample schema code](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) and paste it into a text file.</span></span> <span data-ttu-id="02ff5-116">将该文件另存为 SampleSchema1.xml。</span><span class="sxs-lookup"><span data-stu-id="02ff5-116">Save the file as SampleSchema1.xml.</span></span>  
  
2.  <span data-ttu-id="02ff5-117">创建以下模板 (XPathVariables.xml)，并将它保存在以下目录中：</span><span class="sxs-lookup"><span data-stu-id="02ff5-117">Create the following template (XPathVariables.xml) and save it in the directory where:</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:header>  
         <sql:param name='CustomerID'>1</sql:param>  
         <sql:param name='ContactID'>1</sql:param>   
      </sql:header>  
      <sql:xpath-query mapping-schema="SampleSchema1.xml">  
        Customer[@CustomerID=$CustomerID]   
      </sql:xpath-query >  
      <sql:xpath-query mapping-schema="SampleSchema1.xml">  
       Contact[@ContactID=$ContactID]   
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="02ff5-118">为映射架构 (SampleSchema1.xml) 指定的目录路径是相对于模板保存目录的相对路径。</span><span class="sxs-lookup"><span data-stu-id="02ff5-118">The directory path specified for the mapping schema (SampleSchema1.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="02ff5-119">也可以指定绝对路径，例如：</span><span class="sxs-lookup"><span data-stu-id="02ff5-119">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\SampleSchema1.xml"  
    ```  
  
3.  <span data-ttu-id="02ff5-120">创建并使用 SQLXML 4.0 测试脚本 (Sqlxml4test.vbs) 执行该模板。</span><span class="sxs-lookup"><span data-stu-id="02ff5-120">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span> <span data-ttu-id="02ff5-121">有关详细信息，请参阅[使用 ADO 执行 SQLXML 4.0 查询](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="02ff5-121">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="02ff5-122">在此示例中，不传递参数。</span><span class="sxs-lookup"><span data-stu-id="02ff5-122">In this example, no parameters are passed.</span></span> <span data-ttu-id="02ff5-123">因此，使用默认参数值。</span><span class="sxs-lookup"><span data-stu-id="02ff5-123">Therefore, the default parameter values are used.</span></span>  
  
  
