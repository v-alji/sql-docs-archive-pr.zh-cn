---
title: 防止无效请求 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- invalid requests [Reporting Services]
- exceptions [Reporting Services], invalid requests
- valid requests [Reporting Services]
ms.assetid: 4a4a2d97-4c10-43a9-8298-ef5a820ea549
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 12343955c46fb98fea75048a38749b1db993fa11
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590041"
---
# <a name="preventing-invalid-requests"></a><span data-ttu-id="adac2-102">防止无效请求</span><span class="sxs-lookup"><span data-stu-id="adac2-102">Preventing Invalid Requests</span></span>
  <span data-ttu-id="adac2-103">您可以通过分析应用程序流程并确保要发送到报表服务器的请求有效，防止引发某些类型的异常。</span><span class="sxs-lookup"><span data-stu-id="adac2-103">You can prevent some types of exceptions from being thrown by analyzing your application flow and ensuring that the requests being sent to the report server are valid.</span></span> <span data-ttu-id="adac2-104">例如，在使用户能够添加或更新报表名称、数据源或其他报表服务器项的应用程序中，您应该对用户可能输入的文本进行验证。</span><span class="sxs-lookup"><span data-stu-id="adac2-104">For example, in applications that enable users to add or update the name of a report, data source, or other report server item, you should validate the text that a user might enter.</span></span> <span data-ttu-id="adac2-105">您应该始终在将请求发送到报表服务器之前检查是否使用了保留字符。</span><span class="sxs-lookup"><span data-stu-id="adac2-105">You should always check for reserved characters before sending the request to a report server.</span></span> <span data-ttu-id="adac2-106">在代码中使用条件 if\*\*\*\* 语句或其他逻辑构造可以向用户发出警报，提醒用户尚未满足将请求发送到报表服务器所需的条件。</span><span class="sxs-lookup"><span data-stu-id="adac2-106">Use conditional **if** statements or other logical constructs in your code to alert the user that they have not met the conditions necessary to send requests to the report server.</span></span>  
  
 <span data-ttu-id="adac2-107">下面是一个简化的 C# 示例，在用户尝试创建名称中包含正斜杠 (/) 字符的报表时向其提供用户友好的错误消息。</span><span class="sxs-lookup"><span data-stu-id="adac2-107">In the following, simplified C# example, users are presented with a friendly error message when they attempt to create a report with a name that contains a forward slash (/) character.</span></span>  
  
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
         "see the help documentation";  
  
      MessageBox.Show(message, "Invalid Input Error");  
   }  
   else // Publish the report  
   {  
      Byte[] definition = null;  
      Warning[] warnings = {};  
      string name = nameTextBox.Text;  
  
      FileStream stream = File.OpenRead("MyReport.rdl");  
      definition = new Byte[stream.Length];  
      stream.Read(definition, 0, (int) stream.Length);  
      stream.Close();  
      // Create report with user-defined name  
      rs.CreateCatalogItem("Report", name, "/Samples", false, definition, null, out warnings);  
      MessageBox.Show("Report: {0} created successfully", name);  
   }  
}  
```  
  
 <span data-ttu-id="adac2-108">有关在将请求发送到报表服务器前可避免的错误类型的详细信息，请参阅 [SoapException 错误表](../soapexception-class/soapexception-errors-table.md)。</span><span class="sxs-lookup"><span data-stu-id="adac2-108">For more information about the types of errors that can be prevented before requests are sent to the report server, see [SoapException Errors Table](../soapexception-class/soapexception-errors-table.md).</span></span> <span data-ttu-id="adac2-109">有关使用 try/catch 块进一步增强前一个示例的详细信息，请参阅[使用 Try 和 Catch 块](using-try-and-catch-blocks.md)。</span><span class="sxs-lookup"><span data-stu-id="adac2-109">For more information about further enhancing the previous example using try/catch blocks, see [Using Try and Catch Blocks](using-try-and-catch-blocks.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="adac2-110">另请参阅</span><span class="sxs-lookup"><span data-stu-id="adac2-110">See Also</span></span>  
 <span data-ttu-id="adac2-111">[介绍 Reporting Services 中的异常处理](../introducing-exception-handling-in-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="adac2-111">[Introducing Exception Handling in Reporting Services](../introducing-exception-handling-in-reporting-services.md) </span></span>  
 [<span data-ttu-id="adac2-112">Reporting Services SoapException 类</span><span class="sxs-lookup"><span data-stu-id="adac2-112">Reporting Services SoapException Class</span></span>](../soapexception-class/reporting-services-soapexception-class.md)  
  
  
