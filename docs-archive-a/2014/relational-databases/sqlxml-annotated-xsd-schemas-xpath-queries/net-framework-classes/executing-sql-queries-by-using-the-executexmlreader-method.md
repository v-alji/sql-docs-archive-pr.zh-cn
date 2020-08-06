---
title: 使用 ExecuteXMLReader 方法执行 SQL 查询 |Microsoft Docs
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
- ExecuteXmlReader method
- SQL queries [SQLXML]
ms.assetid: f106a4c5-8d6e-40c0-bf1f-11e121afcb01
author: rothja
ms.author: jroth
ms.openlocfilehash: 1570e877ae84a813e5a053df34c35d5fe840969c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587272"
---
# <a name="executing-sql-queries-by-using-the-executexmlreader-method"></a><span data-ttu-id="68710-102">使用 ExecuteXMLReader 方法执行 SQL 查询</span><span class="sxs-lookup"><span data-stu-id="68710-102">Executing SQL Queries by Using the ExecuteXMLReader Method</span></span>
  <span data-ttu-id="68710-103">您可以使用 SqlXmlCommand 对象的 ExecuteXmlReader 方法来执行命令，而不是使用 ExecuteToStream 方法。</span><span class="sxs-lookup"><span data-stu-id="68710-103">Instead of using the ExecuteToStream method, you can use the ExecuteXmlReader method of the SqlXmlCommand object to execute commands.</span></span> <span data-ttu-id="68710-104">此方法返回一个 XmlReader 对象，该对象可用于进一步处理结果 (在本示例中，将在此示例中打印元素或属性名称以及) 的值。</span><span class="sxs-lookup"><span data-stu-id="68710-104">This method returns an XmlReader object that can be used for further processing of the result (which in this example is printing the element or attribute names and the values).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="68710-105">在代码中，必须在连接字符串中提供 Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例的名称。</span><span class="sxs-lookup"><span data-stu-id="68710-105">In the code, you must provide the name of the instance of Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in the connection string.</span></span>  
  
```  
using System;  
using Microsoft.Data.SqlXml;  
using System.IO;  
using System.Xml;  
   class Test  
   {  
      static string ConnString = "Provider=SQLOLEDB;Server=(local);database=AdventureWorks2012;Integrated Security=SSPI";  
      public static int testParams()  
      {  
         SqlXmlParameter p;  
         XmlReader Reader;  
         XmlTextWriter tw;  
         SqlXmlCommand cmd = new SqlXmlCommand(ConnString);  
         cmd.CommandText = "select FirstName, LastName from Person.Person where LastName = ? For XML Auto";  
         p = cmd.CreateParameter();  
         p.Value = "Achong";  
         Reader = cmd.ExecuteXmlReader();  
            tw = new XmlTextWriter(Console.Out);  
         Reader.MoveToContent();  
         tw.WriteNode(Reader, false);  
         tw.Flush();  
         tw.Close();  
         Reader.Close();  
  
         return 0;  
      }  
  
      static int Main(string[] args)  
      {  
         testParams();  
         return 0;  
      }  
   }  
```  
  
### <a name="to-test-the-application"></a><span data-ttu-id="68710-106">测试应用程序</span><span class="sxs-lookup"><span data-stu-id="68710-106">To test the application</span></span>  
  
1.  <span data-ttu-id="68710-107">确保已在计算机上安装了 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework。</span><span class="sxs-lookup"><span data-stu-id="68710-107">Make sure that you have the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework installed on your computer.</span></span>  
  
2.  <span data-ttu-id="68710-108">保存 (DocSample.cs) 的 c # 代码，该代码在文件夹中提供。</span><span class="sxs-lookup"><span data-stu-id="68710-108">Save the C# code (DocSample.cs) that is provided in this topic in a folder.</span></span>  
  
3.  <span data-ttu-id="68710-109">编译代码。</span><span class="sxs-lookup"><span data-stu-id="68710-109">Compile the code.</span></span> <span data-ttu-id="68710-110">若要在命令提示符下编译此代码，请使用：</span><span class="sxs-lookup"><span data-stu-id="68710-110">To compile the code at the command prompt, use:</span></span>  
  
    ```  
    csc /reference:Microsoft.Data.SqlXML.dll DocSample.cs  
    ```  
  
     <span data-ttu-id="68710-111">这将创建一个可执行文件 (DocSample.exe)。</span><span class="sxs-lookup"><span data-stu-id="68710-111">This creates an executable (DocSample.exe).</span></span>  
  
4.  <span data-ttu-id="68710-112">在命令提示符下，执行 DocSample.exe。</span><span class="sxs-lookup"><span data-stu-id="68710-112">At the command prompt, execute DocSample.exe.</span></span>  
  
  
