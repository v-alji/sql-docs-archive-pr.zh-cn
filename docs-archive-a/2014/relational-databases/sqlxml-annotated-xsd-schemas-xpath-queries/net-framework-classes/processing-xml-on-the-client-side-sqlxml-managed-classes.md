---
title: " (SQLXML 托管类) | 在客户端处理 XMLMicrosoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- processing XML on client side [SQLXML]
- client-side XML formatting
- Managed Classes [SQLXML], client-side XML formatting
- SQLXML Managed Classes, client-side XML formatting
- ClientSideXml property
ms.assetid: 5e7ecf18-66fc-49ff-bc50-83635cd7ac0b
author: rothja
ms.author: jroth
ms.openlocfilehash: fb90f7c5c823c750b64f47d0c9df9551b9f857b5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577495"
---
# <a name="processing-xml-on-the-client-side-sqlxml-managed-classes"></a><span data-ttu-id="1eacb-102">在客户端处理 XML（SQLXML 托管类）</span><span class="sxs-lookup"><span data-stu-id="1eacb-102">Processing XML on the Client Side (SQLXML Managed Classes)</span></span>
  <span data-ttu-id="1eacb-103">此示例演示如何使用 ClientSideXml 属性。</span><span class="sxs-lookup"><span data-stu-id="1eacb-103">This example illustrates the use of the ClientSideXml property.</span></span> <span data-ttu-id="1eacb-104">应用程序在服务器上执行存储过程。</span><span class="sxs-lookup"><span data-stu-id="1eacb-104">The application executes a stored procedure on the server.</span></span> <span data-ttu-id="1eacb-105">在客户端对存储过程的结果（一个有两列的行集）进行处理，以产生 XML 文档。</span><span class="sxs-lookup"><span data-stu-id="1eacb-105">The result of the stored procedure (a two-column rowset) is processed on the client side to produce an XML document.</span></span>  
  
 <span data-ttu-id="1eacb-106">下面的 GetContacts 存储过程将返回用户的**名字**和**姓氏**。 AdventureWorks 数据库中的 Contact 表。</span><span class="sxs-lookup"><span data-stu-id="1eacb-106">The following GetContacts stored procedure returns **FirstName** and **LastName** of employees in the Person.Contact table in the AdventureWorks database.</span></span>  
  
```  
USE AdventureWorks  
CREATE PROCEDURE GetContacts @LastName varchar(20)  
AS  
SELECT FirstName, LastName  
FROM   Person.Contact  
WHERE LastName = @LastName  
Go  
```  
  
 <span data-ttu-id="1eacb-107">此 c # 应用程序执行存储过程，并在指定 CommandText 值中指定 FOR XML AUTO 选项。</span><span class="sxs-lookup"><span data-stu-id="1eacb-107">This C# application executes the stored procedure and specifies the FOR XML AUTO option in specifying the CommandText value.</span></span> <span data-ttu-id="1eacb-108">在应用程序中，SqlXmlCommand 对象的 ClientSideXml 属性设置为 true。</span><span class="sxs-lookup"><span data-stu-id="1eacb-108">In the application, the ClientSideXml property of the SqlXmlCommand object is set to true.</span></span> <span data-ttu-id="1eacb-109">这将允许执行预先存在的存储过程，然后由存储过程返回行集，并在客户端上对它执行 XML 转换。</span><span class="sxs-lookup"><span data-stu-id="1eacb-109">This allows you to execute preexisting stored procedures that return a rowset and apply an XML transformation to it on the client.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1eacb-110">在代码中，必须在连接字符串中提供 Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例的名称。</span><span class="sxs-lookup"><span data-stu-id="1eacb-110">In the code, you must provide the name of the instance of Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in the connection string.</span></span>  
  
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
         SqlXmlParameter p;  
         SqlXmlCommand cmd = new SqlXmlCommand(ConnString);  
         cmd.ClientSideXml = true;  
         cmd.CommandText = "EXEC GetContacts ? FOR XML NESTED";  
         p = cmd.CreateParameter();  
         p.Value = "Achong";  
         using (Stream strm = cmd.ExecuteStream())   
         {  
            using (StreamReader sr = new StreamReader(strm))  
                  {  
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
  
 <span data-ttu-id="1eacb-111">若要测试该示例，必须在计算机上安装 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework。</span><span class="sxs-lookup"><span data-stu-id="1eacb-111">To test this example, you must have the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework installed on your computer.</span></span>  
  
### <a name="to-test-the-application"></a><span data-ttu-id="1eacb-112">测试应用程序</span><span class="sxs-lookup"><span data-stu-id="1eacb-112">To test the application</span></span>  
  
1.  <span data-ttu-id="1eacb-113">创建存储过程。</span><span class="sxs-lookup"><span data-stu-id="1eacb-113">Create the stored procedure.</span></span>  
  
2.  <span data-ttu-id="1eacb-114">将此示例中提供的 C# 代码 (DocSample.cs) 保存在某个文件夹中。</span><span class="sxs-lookup"><span data-stu-id="1eacb-114">Save the C# code (DocSample.cs) that is provided in this example in a folder.</span></span> <span data-ttu-id="1eacb-115">编辑代码，以指定合适的登录和密码信息。</span><span class="sxs-lookup"><span data-stu-id="1eacb-115">Edit the code to specify appropriate login and password information.</span></span>  
  
3.  <span data-ttu-id="1eacb-116">编译代码。</span><span class="sxs-lookup"><span data-stu-id="1eacb-116">Compile the code.</span></span> <span data-ttu-id="1eacb-117">若要在命令提示符下编译此代码，请使用：</span><span class="sxs-lookup"><span data-stu-id="1eacb-117">To compile the code at the command prompt, use:</span></span>  
  
    ```  
    csc /reference:Microsoft.Data.SqlXML.dll DocSample.cs  
    ```  
  
     <span data-ttu-id="1eacb-118">这将创建一个可执行文件 (DocSample.exe)。</span><span class="sxs-lookup"><span data-stu-id="1eacb-118">This creates an executable (DocSample.exe).</span></span>  
  
4.  <span data-ttu-id="1eacb-119">在命令提示符下，执行 DocSample.exe。</span><span class="sxs-lookup"><span data-stu-id="1eacb-119">At the command prompt, execute DocSample.exe.</span></span>  
  
  
