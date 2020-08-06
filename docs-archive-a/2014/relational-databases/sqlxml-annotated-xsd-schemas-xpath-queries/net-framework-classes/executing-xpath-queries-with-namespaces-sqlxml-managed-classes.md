---
title: 通过命名空间执行 XPath 查询 (SQLXML 托管类) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- namespaces property
- XPath queries [SQLXML], SQLXML Managed Classes
- queries [SQLXML], SQLXML Managed Classes
- XPath queries [SQLXML], namespaces
- Managed Classes [SQLXML], executing XPath queries
- SQLXML Managed Classes, executing XPath queries
- namespaces [SQLXML], XPath queries
ms.assetid: c6fc46d8-6b42-4992-a8f1-a8d4b8886e6e
author: rothja
ms.author: jroth
ms.openlocfilehash: a2d726de95929709c1ae958ee22388df3195bc84
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576603"
---
# <a name="executing-xpath-queries-with-namespaces-sqlxml-managed-classes"></a><span data-ttu-id="50246-102">执行带命名空间的 XPath 查询（SQLXML 托管类）</span><span class="sxs-lookup"><span data-stu-id="50246-102">Executing XPath Queries with Namespaces (SQLXML Managed Classes)</span></span>
  <span data-ttu-id="50246-103">XPath 查询可以包含命名空间。</span><span class="sxs-lookup"><span data-stu-id="50246-103">XPath queries can include namespaces.</span></span> <span data-ttu-id="50246-104">如果架构元素为限定命名空间（使用目标命名空间），则针对该架构的 XPath 查询必须指定该命名空间。</span><span class="sxs-lookup"><span data-stu-id="50246-104">If the schema elements are namespace-qualified (use a target namespace), the XPath queries against the schema must specify the namespace.</span></span>  
  
 <span data-ttu-id="50246-105">由于 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML 4.0 中不支持使用通配符 (\*)，因此必须使用命名空间前缀来指定 XPath 查询。</span><span class="sxs-lookup"><span data-stu-id="50246-105">Because the wildcard character (\*) is not supported in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML 4.0, you must specify the XPath query by using a namespace prefix.</span></span> <span data-ttu-id="50246-106">若要解析此前缀，请使用 namespace 属性来指定命名空间绑定。</span><span class="sxs-lookup"><span data-stu-id="50246-106">To resolve the prefix, use the namespaces property to specify the namespace binding.</span></span>  
  
 <span data-ttu-id="50246-107">在下面的示例中，XPath 查询使用通配符指定命名空间 (\*) 和本地名称 ( # A3 和 namespace uri ( # A5 XPath 函数。</span><span class="sxs-lookup"><span data-stu-id="50246-107">In the following example, the XPath query specifies namespaces by using the wildcard character (\*) and the local-name() and namespace-uri() XPath functions.</span></span> <span data-ttu-id="50246-108">此 XPath 查询将返回其本地名称为 `Employee` 且其命名空间 URI 为 `urn:myschema:Contacts` 的所有元素：</span><span class="sxs-lookup"><span data-stu-id="50246-108">This XPath query returns all the elements where the local name is `Employee` and the namespace URI is `urn:myschema:Contacts`:</span></span>  
  
```  
/*[local-name() = 'Contact' and namespace-uri() = 'urn:myschema:Contacts']  
```  
  
 <span data-ttu-id="50246-109">在 SQLXML 4.0 中，用命名空间前缀来指定此 XPath 查询。</span><span class="sxs-lookup"><span data-stu-id="50246-109">In SQLXML 4.0, specify this XPath query with a namespace prefix.</span></span> <span data-ttu-id="50246-110">例如，`x:Contact`，其中 `x` 为命名空间前缀。</span><span class="sxs-lookup"><span data-stu-id="50246-110">An example is `x:Contact`, where `x` is the namespace prefix.</span></span> <span data-ttu-id="50246-111">请看以下 XSD 架构：</span><span class="sxs-lookup"><span data-stu-id="50246-111">Consider the following XSD schema:</span></span>  
  
```  
<schema xmlns="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema"  
            xmlns:con="urn:myschema:Contacts"  
            targetNamespace="urn:myschema:Contacts">  
<complexType name="ContactType">  
  <attribute name="CID" sql:field="ContactID" type="ID"/>  
  <attribute name="FName" sql:field="FirstName" type="string"/>  
  <attribute name="LName" sql:field="LastName"/>   
</complexType>  
<element name="Contact" type="con:ContactType" sql:relation="Person.Contact"/>  
</schema>  
```  
  
 <span data-ttu-id="50246-112">由于此架构定义了目标命名空间，因此针对此架构的 XPath 查询 (如 "Employee" ) 必须包含命名空间。</span><span class="sxs-lookup"><span data-stu-id="50246-112">Because this schema defines the target namespace, an XPath query (such as "Employee") against this schema must include the namespace.</span></span>  
  
 <span data-ttu-id="50246-113">以下 C# 应用程序示例针对前述 XSD 架构 (MySchema.xml) 执行 XPath 查询。</span><span class="sxs-lookup"><span data-stu-id="50246-113">The following C# sample application executes an XPath query against the preceding XSD schema (MySchema.xml).</span></span> <span data-ttu-id="50246-114">若要解析此前缀，请使用 SqlXmlCommand 对象的 namespace 属性指定命名空间绑定。</span><span class="sxs-lookup"><span data-stu-id="50246-114">To resolve the prefix, specify the namespace binding by using the Namespaces property of the SqlXmlCommand object.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="50246-115">在该代码中，必须在连接字符串中提供 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例的名称。</span><span class="sxs-lookup"><span data-stu-id="50246-115">In the code, you must provide the name of the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in the connection string.</span></span>  
  
```  
using System;  
using Microsoft.Data.SqlXml;  
using System.IO;  
class Test  
{  
      static string ConnString = "Provider=SQLOLEDB;Server=(local);database=AdventureWorks;Integrated Security=SSPI";  
      public static int testXPath()  
      {  
         //Stream strm;  
         SqlXmlCommand cmd = new SqlXmlCommand(ConnString);  
         cmd.CommandText = "x:Contact[@CID='1']";  
         cmd.CommandType = SqlXmlCommandType.XPath;  
         cmd.RootTag = "ROOT";  
         cmd.Namespaces = "xmlns:x='urn:myschema:Contacts'";  
         cmd.SchemaPath = "MySchema.xml";  
         using (Stream strm = cmd.ExecuteStream()){  
            using (StreamReader sr = new StreamReader(strm)){  
               Console.WriteLine(sr.ReadToEnd());  
            }  
         }  
         return 0;  
      }  
      public static int Main(String[] args)  
      {  
         testXPath();  
         return 0;  
      }  
   }  
```  
  
 <span data-ttu-id="50246-116">若要测试该示例，必须在计算机上安装 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework。</span><span class="sxs-lookup"><span data-stu-id="50246-116">To test this example, you must have the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework installed on your computer.</span></span>  
  
### <a name="to-test-the-application"></a><span data-ttu-id="50246-117">测试应用程序</span><span class="sxs-lookup"><span data-stu-id="50246-117">To test the application</span></span>  
  
1.  <span data-ttu-id="50246-118">将在该示例中提供的 XSD 架构 (MySchema.xml) 保存到某个文件夹中。</span><span class="sxs-lookup"><span data-stu-id="50246-118">Save the XSD schema (MySchema.xml) that is provided in this example in a folder.</span></span>  
  
2.  <span data-ttu-id="50246-119">将此示例中提供的 c # 代码 (DocSample.cs) 保存到存储架构的相同文件夹中。</span><span class="sxs-lookup"><span data-stu-id="50246-119">Save the C# code (DocSample.cs) that is provided in this example in the same folder in which the schema is stored.</span></span> <span data-ttu-id="50246-120">（如果将文件存储在其他文件夹中，则必须编辑代码并为映射架构指定相应的目录路径。）</span><span class="sxs-lookup"><span data-stu-id="50246-120">(If you store the files in a different folder, you will have to edit the code and specify the appropriate directory path for the mapping schema.)</span></span>  
  
3.  <span data-ttu-id="50246-121">编译代码。</span><span class="sxs-lookup"><span data-stu-id="50246-121">Compile the code.</span></span> <span data-ttu-id="50246-122">若要在命令提示符下编译此代码，请使用：</span><span class="sxs-lookup"><span data-stu-id="50246-122">To compile the code at the command prompt, use:</span></span>  
  
    ```  
    csc /reference:Microsoft.Data.SqlXML.dll DocSample.cs  
    ```  
  
     <span data-ttu-id="50246-123">这将创建一个可执行文件 (DocSample.exe)。</span><span class="sxs-lookup"><span data-stu-id="50246-123">This creates an executable (DocSample.exe).</span></span>  
  
4.  <span data-ttu-id="50246-124">在命令提示符下，执行 DocSample.exe。</span><span class="sxs-lookup"><span data-stu-id="50246-124">At the command prompt, execute DocSample.exe.</span></span>  
  
  
