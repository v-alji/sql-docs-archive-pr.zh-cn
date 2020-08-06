---
title: " (SQLXML 托管类) | 执行 XPath 查询 |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XPath queries [SQLXML], SQLXML Managed Classes
- queries [SQLXML], SQLXML Managed Classes
- Managed Classes [SQLXML], executing XPath queries
- mapping schema [SQLXML], XPath queries
- SQLXML Managed Classes, executing XPath queries
ms.assetid: 8bef4c4d-bf0e-4236-a875-fd7d3e058396
author: rothja
ms.author: jroth
ms.openlocfilehash: d8f5fd2612a0992f18e0b7f32c749c352d29d2b3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576604"
---
# <a name="executing-xpath-queries-sqlxml-managed-classes"></a><span data-ttu-id="0b91c-102">执行 XPath 查询（SQLXML 托管类）</span><span class="sxs-lookup"><span data-stu-id="0b91c-102">Executing XPath Queries (SQLXML Managed Classes)</span></span>
  <span data-ttu-id="0b91c-103">该示例说明如何针对映射架构执行 XPath 查询。</span><span class="sxs-lookup"><span data-stu-id="0b91c-103">This example illustrates how XPath queries are executed against a mapping schema.</span></span>  
  
 <span data-ttu-id="0b91c-104">考虑该架构：</span><span class="sxs-lookup"><span data-stu-id="0b91c-104">Consider this schema:</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="Con" sql:relation="Person.Contact" >  
   <xsd:complexType>  
     <xsd:sequence>  
        <xsd:element name="FName"    
                     sql:field="FirstName"   
                     type="xsd:string" />   
        <xsd:element name="LName"    
                     sql:field="LastName"    
                     type="xsd:string" />  
     </xsd:sequence>  
     <xsd:attribute name="ContactID" type="xsd:integer" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 <span data-ttu-id="0b91c-105">该 C# 应用程序针对此架构 (MySchema.xml) 执行 XPath 查询。</span><span class="sxs-lookup"><span data-stu-id="0b91c-105">This C# application executes an XPath query against this schema (MySchema.xml).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0b91c-106">在代码中，必须在连接字符串中提供 Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例的名称。</span><span class="sxs-lookup"><span data-stu-id="0b91c-106">In the code, you must provide the name of the instance of Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in the connection string.</span></span>  
  
```  
using System;  
using Microsoft.Data.SqlXml;  
using System.IO;  
class Test  
{  
      static string ConnString = "Provider=SQLOLEDB;Server=(local);database=AdventureWorks;Integrated Security=SSPI";  
  
      public static int testXPath()  
      {  
         Stream strm;  
         SqlXmlCommand cmd = new SqlXmlCommand(ConnString);  
         cmd.CommandText = "Con";  
         cmd.CommandType = SqlXmlCommandType.XPath;  
         cmd.RootTag = "ROOT";  
         cmd.SchemaPath = "MySchema.xml";  
         strm = cmd.ExecuteStream();  
         using (StreamReader sr = new StreamReader(strm)){  
            Console.WriteLine(sr.ReadToEnd());  
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
  
### <a name="to-test-the-application"></a><span data-ttu-id="0b91c-107">测试应用程序</span><span class="sxs-lookup"><span data-stu-id="0b91c-107">To test the application</span></span>  
  
1.  <span data-ttu-id="0b91c-108">确保已在计算机上安装了 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework。</span><span class="sxs-lookup"><span data-stu-id="0b91c-108">Make sure that you have the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework installed on your computer.</span></span>  
  
2.  <span data-ttu-id="0b91c-109">将在该示例中提供的 XSD 架构 (MySchema.xml) 保存到某个文件夹中。</span><span class="sxs-lookup"><span data-stu-id="0b91c-109">Save the XSD schema (MySchema.xml) that is provided in this example in a folder.</span></span>  
  
3.  <span data-ttu-id="0b91c-110">将此示例中提供的 c # 代码 (DocSample.cs) 保存到存储架构的相同文件夹中。</span><span class="sxs-lookup"><span data-stu-id="0b91c-110">Save the C# code (DocSample.cs) that is provided in this example in the same folder in which the schema is stored.</span></span> <span data-ttu-id="0b91c-111">（如果将文件存储在其他文件夹中，则必须编辑代码并为映射架构指定相应的目录路径。）</span><span class="sxs-lookup"><span data-stu-id="0b91c-111">(If you store the files in a different folder, you will have to edit the code and specify the appropriate directory path for the mapping schema.)</span></span>  
  
4.  <span data-ttu-id="0b91c-112">编译代码。</span><span class="sxs-lookup"><span data-stu-id="0b91c-112">Compile the code.</span></span> <span data-ttu-id="0b91c-113">若要在命令提示符下编译此代码，请使用：</span><span class="sxs-lookup"><span data-stu-id="0b91c-113">To compile the code at the command prompt, use:</span></span>  
  
    ```  
    csc /reference:Microsoft.Data.SqlXML.dll DocSample.cs  
    ```  
  
     <span data-ttu-id="0b91c-114">这将创建一个可执行文件 (DocSample.exe)。</span><span class="sxs-lookup"><span data-stu-id="0b91c-114">This creates an executable (DocSample.exe).</span></span>  
  
5.  <span data-ttu-id="0b91c-115">在命令提示符下，执行 DocSample.exe。</span><span class="sxs-lookup"><span data-stu-id="0b91c-115">At the command prompt, execute DocSample.exe.</span></span>  
  
  
