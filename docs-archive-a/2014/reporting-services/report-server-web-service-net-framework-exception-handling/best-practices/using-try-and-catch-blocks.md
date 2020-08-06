---
title: 使用 Try 和 Catch 块 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- exceptions [Reporting Services], try/catch blocks
- try/catch blocks [Reporting Services]
ms.assetid: a7a9ef53-e3b6-4bf7-81f3-d85615954e6f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a6aadb392fa4117484f3373ae232c3ed9c4b1d63
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692684"
---
# <a name="using-try-and-catch-blocks"></a><span data-ttu-id="a8930-102">使用 Try 和 Catch 块</span><span class="sxs-lookup"><span data-stu-id="a8930-102">Using Try and Catch Blocks</span></span>
  <span data-ttu-id="a8930-103">在通过向代码添加条件语句以限制对于报表服务器的无效请求之后，应通过使用 try/catch 块提供适当的异常处理。</span><span class="sxs-lookup"><span data-stu-id="a8930-103">After you limit invalid requests to the report server by adding conditional statements to your code, you should supply adequate exception handling through the use of try/catch blocks.</span></span> <span data-ttu-id="a8930-104">此方法从另一个层面来防止无效的请求。</span><span class="sxs-lookup"><span data-stu-id="a8930-104">This technique provides another layer of protection against requests that are not valid.</span></span> <span data-ttu-id="a8930-105">如果对于报表服务器的请求包含在 try 块中，并且该请求导致报表服务器引发异常，则将在 catch 块中捕获此异常，从而防止应用程序意外终止。</span><span class="sxs-lookup"><span data-stu-id="a8930-105">If a request to the report server is encased in a try block and that request causes the report server to throw an exception, the exception is caught in the catch block, thus preventing your application from ending unexpectedly.</span></span> <span data-ttu-id="a8930-106">一旦捕获了异常，您就可以使用该异常来指导用户以不同方式操作，或者只是以友好的方式让用户知道已发生了错误。</span><span class="sxs-lookup"><span data-stu-id="a8930-106">Once the exception is caught, you can use the exception to either instruct the user to do something differently, or just let the user know, in a friendly way, that an error has occurred.</span></span> <span data-ttu-id="a8930-107">然后，您可以使用 finally 块来清除任何资源。</span><span class="sxs-lookup"><span data-stu-id="a8930-107">You can then use a finally block to clean up any resources.</span></span> <span data-ttu-id="a8930-108">在理想情况下，应生成一个常规异常处理计划以避免不必要地重复 try/catch 块。</span><span class="sxs-lookup"><span data-stu-id="a8930-108">Ideally, you should generate a general exception-handling plan to avoid unnecessary duplication of try/catch blocks.</span></span>  
  
 <span data-ttu-id="a8930-109">以下示例使用 try/catch 块以增强异常处理代码的可靠性。</span><span class="sxs-lookup"><span data-stu-id="a8930-109">The following example uses try/catch blocks to enhance the reliability of the exception handling code.</span></span>  
  
```  
// C#  
private void PublishReport()  
{  
   int index;  
   string reservedChar;  
   string message;  
  
   // Check the text value of the name text box for "/",  
   // a reserved character  
   index = nameTextBox.Text.IndexOf(@"/");  
  
   if ( index != -1) // The text contains the character  
   {  
      reservedChar = nameTextBox.Text.Substring(index, 1);  
      // Build a user-friendly error message  
      message = "The name of the report cannot contain the reserved character " +  
         "\"" + reservedChar + "\". " +  
         "Please enter a valid name for the report. " +  
         "For more information about reserved characters, " +  
         "consult the online documentation";  
  
      MessageBox.Show(message, "Invalid Input Error");  
   }  
   else // Publish the report  
   {  
      Byte[] definition = null;  
      Warning[] warnings = {};  
      string name = nameTextBox.Text;  
  
      try  
      {  
         FileStream stream = File.OpenRead("MyReport.rdl");  
         definition = new Byte[stream.Length];  
         stream.Read(definition, 0, (int) stream.Length);  
         stream.Close();  
         // Create report with user-defined name  
         rs.CreateCatalogItem("Report", name, "/Samples", false, definition, null, out warnings);  
         MessageBox.Show("Report: {0} created successfully", name);  
      }  
  
      // Catch expected exceptions beginning with the most specific,  
      // moving to the least specific  
      catch(IOException ex)  
      {  
         MessageBox.Show(ex.Message, "File IO Exception");  
      }  
  
      catch (SoapException ex)  
      {  
         // The exception is a SOAP exception, so use  
         // the Detail property's Message element.  
         MessageBox.Show(ex.Detail["Message"].InnerXml, "SOAP Exception");   
      }  
  
      catch (Exception ex)  
      {  
         MessageBox.Show(ex.Message, "General Exception");  
      }  
   }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="a8930-110">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a8930-110">See Also</span></span>  
 <span data-ttu-id="a8930-111">[介绍 Reporting Services 中的异常处理](../introducing-exception-handling-in-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="a8930-111">[Introducing Exception Handling in Reporting Services](../introducing-exception-handling-in-reporting-services.md) </span></span>  
 [<span data-ttu-id="a8930-112">Reporting Services SoapException 类</span><span class="sxs-lookup"><span data-stu-id="a8930-112">Reporting Services SoapException Class</span></span>](../soapexception-class/reporting-services-soapexception-class.md)  
  
  
