---
title: 使用 CommandStream 属性执行模板文件 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- Managed Classes [SQLXML], executing template files
- SQLXML Managed Classes, executing template files
- templates [SQLXML], SQLXML Managed Classes
- CommandStream property
ms.assetid: 55c564e3-56d1-4d85-bcaa-703e2905dd57
author: rothja
ms.author: jroth
ms.openlocfilehash: c57a2ab2f3780a8bc75b53b0cceeee0799fcfcc2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576606"
---
# <a name="executing-template-files-by-using-the-commandstream-property"></a><span data-ttu-id="7fd59-102">使用 CommandStream 属性执行模板文件</span><span class="sxs-lookup"><span data-stu-id="7fd59-102">Executing Template Files by Using the CommandStream Property</span></span>
  <span data-ttu-id="7fd59-103">此示例演示如何使用 SqlXmlCommand 对象的 CommandStream 属性来指定由 SQL 或 XPath 查询组成的模板文件。</span><span class="sxs-lookup"><span data-stu-id="7fd59-103">This example illustrates how template files that consist of SQL or XPath queries can be specified by using the CommandStream property of the SqlXmlCommand object.</span></span> <span data-ttu-id="7fd59-104">在此应用程序中，将为命令文件打开 FileStreamobject，并将文件流指定为执行的 CommandStream。</span><span class="sxs-lookup"><span data-stu-id="7fd59-104">In this application, a FileStreamobject is opened for a command file, and the file stream is assigned as the CommandStream that is executed.</span></span>  
  
 <span data-ttu-id="7fd59-105">在下面的示例中，CommandType 属性被指定为 SqlXmlCommandType (而不是 TemplateFile) 。</span><span class="sxs-lookup"><span data-stu-id="7fd59-105">In the following example, the CommandType property is specified as SqlXmlCommandType.Template (not as TemplateFile).</span></span>  
  
 <span data-ttu-id="7fd59-106">下面是示例 XML 模板：</span><span class="sxs-lookup"><span data-stu-id="7fd59-106">This is the sample XML template:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <sql:query>  
    SELECT TOP 2 ContactID, FirstName, LastName   
    FROM   Person.Contact  
    FOR XML AUTO  
  </sql:query>  
</ROOT>  
```  
  
 <span data-ttu-id="7fd59-107">这是示例 C# 应用程序。</span><span class="sxs-lookup"><span data-stu-id="7fd59-107">This is the sample C# application.</span></span> <span data-ttu-id="7fd59-108">若要测试该应用程序，请保存模板 (TemplateFile.xml)，然后执行该应用程序。</span><span class="sxs-lookup"><span data-stu-id="7fd59-108">To test the application, save the template (TemplateFile.xml) and then execute the application.</span></span> <span data-ttu-id="7fd59-109">应用程序将执行在 XML 模板中指定的查询，并在屏幕上显示所生成的 XML 文档。</span><span class="sxs-lookup"><span data-stu-id="7fd59-109">The application executes the query that is specified in the XML template and displays the XML document that is generated on the screen.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7fd59-110">在代码中，必须在连接字符串中提供 Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例的名称。</span><span class="sxs-lookup"><span data-stu-id="7fd59-110">In the code, you must provide the name of the instance of Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in the connection string.</span></span>  
  
```  
using System;  
using Microsoft.Data.SqlXml;  
using System.IO;  
  
class Test  
{  
      static string ConnString = "Provider=SQLOLEDB;Server=(local);database=AdventureWorks;Integrated Security=SSPI";  
      public static int testParams()  
      {  
         //Stream strm;  
         MemoryStream ms = new MemoryStream();  
         StreamWriter sw = new StreamWriter(ms);  
         ms.Position = 0;  
         SqlXmlCommand cmd = new SqlXmlCommand(ConnString);  
         cmd.CommandStream = new FileStream("TemplateFile.xml", FileMode.Open, FileAccess.Read);  
         cmd.CommandType = SqlXmlCommandType.Template;  
         using (Stream strm = cmd.ExecuteStream())  
         {  
            using (StreamReader sr = new StreamReader(strm)){  
               Console.WriteLine(sr.ReadToEnd());  
            }  
         }  
         return 0;        
      }  
  
      public static int Main(String[] args)  
      {  
         testParams();     
         return 0;  
      }  
   }  
```  
  
### <a name="to-test-the-application"></a><span data-ttu-id="7fd59-111">测试应用程序</span><span class="sxs-lookup"><span data-stu-id="7fd59-111">To test the application</span></span>  
  
1.  <span data-ttu-id="7fd59-112">将该示例中提供的 XML 模板 (TemplateFile.xml) 保存在某个文件夹中。</span><span class="sxs-lookup"><span data-stu-id="7fd59-112">Save the XML template (TemplateFile.xml) that is provided in this example in a folder.</span></span>  
  
2.  <span data-ttu-id="7fd59-113">将此示例中提供的 c # 代码 (DocSample.cs) 保存到存储架构的相同文件夹中。</span><span class="sxs-lookup"><span data-stu-id="7fd59-113">Save the C# code (DocSample.cs) that is provided in this example in the same folder in which the schema is stored.</span></span> <span data-ttu-id="7fd59-114">（如果将文件存储在其他文件夹中，则必须编辑代码并为映射架构指定相应的目录路径。）</span><span class="sxs-lookup"><span data-stu-id="7fd59-114">(If you store the files in a different folder, you will have to edit the code and specify the appropriate directory path for the mapping schema.)</span></span>  
  
3.  <span data-ttu-id="7fd59-115">编译代码。</span><span class="sxs-lookup"><span data-stu-id="7fd59-115">Compile the code.</span></span> <span data-ttu-id="7fd59-116">若要在命令提示符下编译此代码，请使用：</span><span class="sxs-lookup"><span data-stu-id="7fd59-116">To compile the code at the command prompt, use:</span></span>  
  
    ```  
    csc /reference:Microsoft.Data.SqlXML.dll DocSample.cs  
    ```  
  
     <span data-ttu-id="7fd59-117">这将创建一个可执行文件 (DocSample.exe)。</span><span class="sxs-lookup"><span data-stu-id="7fd59-117">This creates an executable (DocSample.exe).</span></span>  
  
4.  <span data-ttu-id="7fd59-118">在命令提示符下，执行 DocSample.exe。</span><span class="sxs-lookup"><span data-stu-id="7fd59-118">At the command prompt, execute DocSample.exe.</span></span>  
  
  
