---
title: 使用 CommandText 属性执行模板文件 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- Managed Classes [SQLXML], executing template files
- SQLXML Managed Classes, executing template files
- templates [SQLXML], SQLXML Managed Classes
- executing template files [SQLXML]
- CommandText property
ms.assetid: f1b1278d-252d-4a06-836e-4ef77f338ef9
author: rothja
ms.author: jroth
ms.openlocfilehash: f5507e84daf57ca4646fae3efe78c6105af35700
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576605"
---
# <a name="executing-template-files-by-using-the-commandtext-property"></a><span data-ttu-id="8933f-102">使用 CommandText 属性执行模板文件</span><span class="sxs-lookup"><span data-stu-id="8933f-102">Executing Template Files by Using the CommandText Property</span></span>
  <span data-ttu-id="8933f-103">此示例演示如何使用 CommandTextproperty 指定由 SQL 或 XPath 查询组成的模板文件。</span><span class="sxs-lookup"><span data-stu-id="8933f-103">This example illustrates how template files that consist of SQL or XPath queries can be specified by using the CommandTextproperty.</span></span> <span data-ttu-id="8933f-104">可以指定文件名作为值，而不是将 SQL 或 XPath 查询指定为 CommandText 值。</span><span class="sxs-lookup"><span data-stu-id="8933f-104">Instead of specifying the SQL or XPath query as the value of CommandText, you can specify a file name as the value.</span></span> <span data-ttu-id="8933f-105">在下面的示例中，CommandType 属性指定为 SqlXmlCommandType. TemplateFile。</span><span class="sxs-lookup"><span data-stu-id="8933f-105">In the following example, the CommandType property is specified as SqlXmlCommandType.TemplateFile.</span></span>  
  
 <span data-ttu-id="8933f-106">示例应用程序执行下面的模板：</span><span class="sxs-lookup"><span data-stu-id="8933f-106">The sample application executes this template:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <sql:query>  
    SELECT TOP 2 ContactID, FirstName, LastName   
    FROM   Person.Contact  
    FOR XML AUTO  
  </sql:query>  
</ROOT>  
```  
  
 <span data-ttu-id="8933f-107">这是 C# 示例应用程序。</span><span class="sxs-lookup"><span data-stu-id="8933f-107">This is the C# sample application.</span></span> <span data-ttu-id="8933f-108">若要测试该应用程序，请保存模板 (TemplateFile.xml)，然后执行该应用程序。</span><span class="sxs-lookup"><span data-stu-id="8933f-108">To test the application, save the template (TemplateFile.xml) and then execute the application.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8933f-109">在代码中，必须在连接字符串中提供 Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例的名称。</span><span class="sxs-lookup"><span data-stu-id="8933f-109">In the code, you must provide the name of the instance of Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in the connection string.</span></span>  
  
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
         SqlXmlCommand cmd = new SqlXmlCommand(ConnString);  
         cmd.CommandType = SqlXmlCommandType.TemplateFile;  
         cmd.CommandText = "TemplateFile.xml";  
         using (Stream strm = cmd.ExecuteStream()){  
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
  
### <a name="to-test-the-application"></a><span data-ttu-id="8933f-110">测试应用程序</span><span class="sxs-lookup"><span data-stu-id="8933f-110">To test the application</span></span>  
  
1.  <span data-ttu-id="8933f-111">确保已在计算机上安装了 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework。</span><span class="sxs-lookup"><span data-stu-id="8933f-111">Make sure that you have the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework installed on your computer.</span></span>  
  
2.  <span data-ttu-id="8933f-112">将该示例中提供的 XML 模板 (TemplateFile.xml) 保存在某个文件夹中。</span><span class="sxs-lookup"><span data-stu-id="8933f-112">Save the XML template (TemplateFile.xml) that is provided in this example in a folder.</span></span>  
  
3.  <span data-ttu-id="8933f-113">将此示例中提供的 c # 代码 (DocSample.cs) 保存到存储架构的相同文件夹中。</span><span class="sxs-lookup"><span data-stu-id="8933f-113">Save the C# code (DocSample.cs) that is provided in this example in the same folder in which the schema is stored.</span></span> <span data-ttu-id="8933f-114">（如果将文件存储在其他文件夹中，则必须编辑代码并为映射架构指定相应的目录路径。）</span><span class="sxs-lookup"><span data-stu-id="8933f-114">(If you store the files in a different folder, you will have to edit the code and specify the appropriate directory path for the mapping schema.)</span></span>  
  
4.  <span data-ttu-id="8933f-115">编译代码。</span><span class="sxs-lookup"><span data-stu-id="8933f-115">Compile the code.</span></span> <span data-ttu-id="8933f-116">若要在命令提示符下编译此代码，请使用：</span><span class="sxs-lookup"><span data-stu-id="8933f-116">To compile the code at the command prompt, use:</span></span>  
  
    ```  
    csc /reference:Microsoft.Data.SqlXML.dll DocSample.cs  
    ```  
  
     <span data-ttu-id="8933f-117">这将创建一个可执行文件 (DocSample.exe)。</span><span class="sxs-lookup"><span data-stu-id="8933f-117">This creates an executable (DocSample.exe).</span></span>  
  
5.  <span data-ttu-id="8933f-118">在命令提示符下，执行 DocSample.exe。</span><span class="sxs-lookup"><span data-stu-id="8933f-118">At the command prompt, execute DocSample.exe.</span></span>  
  
 <span data-ttu-id="8933f-119">如果将参数传递给模板，则参数名称必须以 at 符号 ( @ ) 开头。例如，p.Name = " @ContactID "，其中 p 是一个 SqlXmlParameter 对象。</span><span class="sxs-lookup"><span data-stu-id="8933f-119">If you pass a parameter to a template, the parameter name must begin with at sign (@); for example, p.Name="@ContactID", where p is a SqlXmlParameter object.</span></span>  
  
 <span data-ttu-id="8933f-120">下面是接受一个参数后的已更新模板。</span><span class="sxs-lookup"><span data-stu-id="8933f-120">This is the updated template which takes one parameter.</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <sql:header>  
     <sql:param name='ContactID'>1</sql:param>    
  </sql:header>  
  <sql:query>  
    SELECT ContactID, FirstName, LastName  
    FROM   Person.Contact  
    WHERE  ContactID=@ContactID  
    FOR XML AUTO  
  </sql:query>  
</ROOT>  
```  
  
 <span data-ttu-id="8933f-121">下面是传递参数所使用的已更新代码，用于执行模板。</span><span class="sxs-lookup"><span data-stu-id="8933f-121">This is the updated code in which a parameter is passed in to execute the template.</span></span>  
  
```  
public static int testParams()  
{  
  
   Stream strm;  
   SqlXmlParameter p;  
  
   SqlXmlCommand cmd = new SqlXmlCommand(ConnString);  
   cmd.CommandType = SqlXmlCommandType.TemplateFile;  
   cmd.CommandText = "TemplateFile.xml";  
   p = cmd.CreateParameter();  
   p.Name="@ContactID";  
   p.Value = "1";  
   strm = cmd.ExecuteStream();  
   StreamReader sw = new StreamReader(strm);  
   Console.WriteLine(sw.ReadToEnd());  
   return 0;        
}  
```  
  
  
