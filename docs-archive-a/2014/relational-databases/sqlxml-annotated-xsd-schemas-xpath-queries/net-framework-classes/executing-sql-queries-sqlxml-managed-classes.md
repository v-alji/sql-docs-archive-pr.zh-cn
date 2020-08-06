---
title: " (SQLXML 托管类) | 执行 SQL 查询 |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- queries [SQLXML], SQLXML Managed Classes
- SQLXML Managed Classes, executing SQL queries
- Managed Classes [SQLXML], executing SQL queries
- ExecuteToStream method
- SQL queries [SQLXML]
ms.assetid: a561ae83-a8b6-4b9b-a819-9b86839546b4
author: rothja
ms.author: jroth
ms.openlocfilehash: d869e45de359e602b2451b9f66fa3046f6823c1e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587270"
---
# <a name="executing-sql-queries-sqlxml-managed-classes"></a><span data-ttu-id="68141-102">执行 SQL 查询（SQLXML 托管类）</span><span class="sxs-lookup"><span data-stu-id="68141-102">Executing SQL Queries (SQLXML Managed Classes)</span></span>
  <span data-ttu-id="68141-103">此示例演示：</span><span class="sxs-lookup"><span data-stu-id="68141-103">This example demonstrates:</span></span>  
  
-   <span data-ttu-id="68141-104">) 创建参数 (SqlXmlParameter 对象。</span><span class="sxs-lookup"><span data-stu-id="68141-104">Creating parameters (SqlXmlParameter objects).</span></span>  
  
-   <span data-ttu-id="68141-105">为 SqlXmlParameter 对象的 "名称" 和 "值")  (属性赋值。</span><span class="sxs-lookup"><span data-stu-id="68141-105">Assigning values to the properties (Name and Value) of SqlXmlParameter objects.</span></span>  
  
 <span data-ttu-id="68141-106">在本示例中，将执行一个简单的 SQL 查询，以检索其姓氏值作为参数传递的雇员的名字、姓氏和出生日期。</span><span class="sxs-lookup"><span data-stu-id="68141-106">In this example, a simple SQL query is executed to retrieve the first name, last name, and birth date of the employee whose last name value is passed as a parameter.</span></span> <span data-ttu-id="68141-107">在 (*LastName*) 指定参数时，只设置 Value 属性。</span><span class="sxs-lookup"><span data-stu-id="68141-107">In specifying the parameter (*LastName*), only the Value property is set.</span></span> <span data-ttu-id="68141-108">未设置 Name 属性，因为在此查询中，参数是位置，无需名称。</span><span class="sxs-lookup"><span data-stu-id="68141-108">The Name property is not set, because in this query the parameter is positional and no name is required.</span></span>  
  
 <span data-ttu-id="68141-109">默认情况下，SqlXmlCommand 对象的 CommandType 属性为**Sql**。</span><span class="sxs-lookup"><span data-stu-id="68141-109">The CommandType property of the SqlXmlCommand object by default is **Sql**.</span></span> <span data-ttu-id="68141-110">因此，不显式设置此属性。</span><span class="sxs-lookup"><span data-stu-id="68141-110">Therefore, the property is not explicitly set.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="68141-111">在代码中，必须在连接字符串中提供 Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例的名称。</span><span class="sxs-lookup"><span data-stu-id="68141-111">In the code, you must provide the name of the instance of Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in the connection string.</span></span>  
  
 <span data-ttu-id="68141-112">以下是 C# 代码：</span><span class="sxs-lookup"><span data-stu-id="68141-112">This is the C# code:</span></span>  
  
```  
using System;  
  
using Microsoft.Data.SqlXml;  
using System.IO;  
class Test  
{  
      static string ConnString = "Provider=SQLOLEDB;Server=(local);database=AdventureWorks;Integrated Security=SSPI";  
      public static int testParams()  
      {  
         Stream strm;  
         SqlXmlParameter p;  
         SqlXmlCommand cmd = new SqlXmlCommand(ConnString);        
         cmd.CommandText = "SELECT FirstName, LastName FROM Person.Contact WHERE LastName=? For XML Auto";  
         p = cmd.CreateParameter();  
         p.Value = "Achong";  
         string strResult;  
         try   
         {  
            strm = cmd.ExecuteStream();  
            strm.Position = 0;  
            using(StreamReader sr = new StreamReader(strm))  
            {  
               Console.WriteLine(sr.ReadToEnd());  
            }  
         }  
         catch (SqlXmlException e)  
         {  
            //in case of an error, this prints error returned.  
            e.ErrorStream.Position=0;  
            strResult=new StreamReader(e.ErrorStream).ReadToEnd();  
            System.Console.WriteLine(strResult);  
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
  
### <a name="to-test-the-application"></a><span data-ttu-id="68141-113">测试应用程序</span><span class="sxs-lookup"><span data-stu-id="68141-113">To test the application</span></span>  
  
1.  <span data-ttu-id="68141-114">将本主题中提供的 C# 代码 (DocSample.cs) 保存在某个文件夹中。</span><span class="sxs-lookup"><span data-stu-id="68141-114">Save the C# code (DocSample.cs) provided in this topic in a folder.</span></span>  
  
2.  <span data-ttu-id="68141-115">编译代码。</span><span class="sxs-lookup"><span data-stu-id="68141-115">Compile the code.</span></span> <span data-ttu-id="68141-116">若要在命令提示符下编译此代码，请使用：</span><span class="sxs-lookup"><span data-stu-id="68141-116">To compile the code at the command prompt, use:</span></span>  
  
    ```  
    csc /reference:Microsoft.Data.SqlXML.dll DocSample.cs  
    ```  
  
     <span data-ttu-id="68141-117">这将创建一个可执行文件 (DocSample.exe)。</span><span class="sxs-lookup"><span data-stu-id="68141-117">This creates an executable (DocSample.exe).</span></span>  
  
3.  <span data-ttu-id="68141-118">在命令提示符下，执行 DocSample.exe。</span><span class="sxs-lookup"><span data-stu-id="68141-118">At the command prompt, execute DocSample.exe.</span></span>  
  
 <span data-ttu-id="68141-119">若要测试该示例，必须在计算机上安装 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework。</span><span class="sxs-lookup"><span data-stu-id="68141-119">To test this example, you must have the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework installed on your computer.</span></span>  
  
 <span data-ttu-id="68141-120">您可以指定一个模板（如下面的代码段所示），该模板执行 updategram（也是一个模板）来插入客户记录，而不是将 SQL 查询指定为命令文本。</span><span class="sxs-lookup"><span data-stu-id="68141-120">Instead of specifying SQL queries as the command text, you can specify a template (as shown in the following code fragment) that executes an updategram (which is also a template) to insert a customer record.</span></span> <span data-ttu-id="68141-121">您可以在文件中指定模板和 updategram，然后执行文件。</span><span class="sxs-lookup"><span data-stu-id="68141-121">You can specify templates and updategrams in files and execute files.</span></span> <span data-ttu-id="68141-122">有关详细信息，请参阅[使用 CommandText 属性执行模板文件](executing-template-files-by-using-the-commandtext-property.md)。</span><span class="sxs-lookup"><span data-stu-id="68141-122">For more information, see [Executing Template Files by Using the CommandText Property](executing-template-files-by-using-the-commandtext-property.md).</span></span>  
  
```  
SqlXmlCommand cmd = new SqlXmlCommand("Provider=SQLOLEDB;Data Source=SqlServerName;Initial Catalog=Database; Integrated Security=SSPI;");  
Stream stm;  
cmd.CommandType = SqlXmlCommandType.UpdateGram;  
cmd.CommandText = "<ROOT xmlns:sql='urn:schemas-microsoft-com:xml-sql' xmlns:updg='urn:schemas-microsoft-com:xml-updategram'>" +  
      "<updg:sync>" +  
       "<updg:before/>" +  
       "<updg:after>" +  
         "<Customer CustomerID='aaaaa' CustomerName='Some Name' CustomerTitle='SomeTitle' />" +  
       "</updg:after>" +  
       "</updg:sync>" +  
       "</ROOT>";  
  
stm = cmd.ExecuteStream();  
stm = null;  
cmd = null;  
```  
  
## <a name="using-executetostream"></a><span data-ttu-id="68141-123">使用 ExecuteToStream</span><span class="sxs-lookup"><span data-stu-id="68141-123">Using ExecuteToStream</span></span>  
 <span data-ttu-id="68141-124">如果有现有流，可以使用 ExecuteToStream 方法，而不是创建流对象和使用 Execute 方法。</span><span class="sxs-lookup"><span data-stu-id="68141-124">If you have an existing stream, you can use the ExecuteToStream method instead of creating a Stream object and using the Execute method.</span></span> <span data-ttu-id="68141-125">此处修改了上述示例中的代码，以使用 ExecuteToStream 方法：</span><span class="sxs-lookup"><span data-stu-id="68141-125">The code from the preceding example is revised here to use the ExecuteToStream method:</span></span>  
  
```  
using System;  
using Microsoft.Data.SqlXml;  
using System.IO;  
class Test  
{  
   static string ConnString = "Provider=SQLOLEDB;Server=SqlServerName;database=AdventureWorks;Integrated Security=SSPI;";  
   public static int testParams()  
   {  
      SqlXmlParameter p;  
      MemoryStream ms = new MemoryStream();  
      StreamReader sr = new StreamReader(ms);  
      ms.Position = 0;  
      SqlXmlCommand cmd = new SqlXmlCommand(ConnString);  
      cmd.CommandText = "select FirstName, LastName from Person.Contact where LastName = ? For XML Auto";  
      p = cmd.CreateParameter();  
      p.Value = "Achong";  
      cmd.ExecuteToStream(ms);  
      ms.Position = 0;  
      Console.WriteLine(sr.ReadToEnd());  
      return 0;        
   }  
   public static int Main(String[] args)  
   {  
      testParams();     
      return 0;  
   }  
}  
```  
  
> [!NOTE]  
>  <span data-ttu-id="68141-126">你还可以使用返回 XmlReader 对象的 ExecuteXMLReadermethod。</span><span class="sxs-lookup"><span data-stu-id="68141-126">You can also use the ExecuteXMLReadermethod that returns an XmlReader object.</span></span> <span data-ttu-id="68141-127">有关详细信息，请参阅[使用 ExecuteXMLReader 方法执行 SQL 查询](executing-sql-queries-by-using-the-executexmlreader-method.md)。</span><span class="sxs-lookup"><span data-stu-id="68141-127">For more information, see [Executing SQL Queries by Using the ExecuteXMLReader Method](executing-sql-queries-by-using-the-executexmlreader-method.md).</span></span>  
  
  
