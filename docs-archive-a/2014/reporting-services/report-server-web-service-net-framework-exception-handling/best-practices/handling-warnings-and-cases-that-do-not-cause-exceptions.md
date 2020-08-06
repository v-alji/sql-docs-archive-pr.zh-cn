---
title: 处理不导致异常的警告和事例 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- exceptions [Reporting Services], warnings that don't cause
- warnings [Reporting Services]
ms.assetid: 475c0713-6265-44e7-9ebc-ebdd1b89e0af
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 88d3daf63cf5f04975a2941d0634f357ce81456c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690355"
---
# <a name="handling-warnings-and-cases-that-do-not-cause-exceptions"></a><span data-ttu-id="f90fc-102">处理不导致异常的警告和事例</span><span class="sxs-lookup"><span data-stu-id="f90fc-102">Handling Warnings and Cases That Do Not Cause Exceptions</span></span>
  <span data-ttu-id="f90fc-103">对于警告和某些错误，[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 不引发异常。</span><span class="sxs-lookup"><span data-stu-id="f90fc-103">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] does not throw exceptions for warnings and certain errors.</span></span> <span data-ttu-id="f90fc-104">例如，在您使用 <xref:ReportService2010.ReportingService2010.CreateCatalogItem%2A> 方法以便将新的报表发布到报表服务器时，出现的任何警告都将以 <xref:ReportService2010.Warning> 对象的数组形式返回。</span><span class="sxs-lookup"><span data-stu-id="f90fc-104">For example, when you use the <xref:ReportService2010.ReportingService2010.CreateCatalogItem%2A> method to publish a new report to a report server, any warnings that occur are returned as an array of <xref:ReportService2010.Warning> objects.</span></span> <span data-ttu-id="f90fc-105">应处理和显示这些警告，以便采取相应操作。</span><span class="sxs-lookup"><span data-stu-id="f90fc-105">These warnings should be handled and displayed so that appropriate action can be taken.</span></span>  
  
```vb  
Try  
   rs.CreateCatalogItem(name, parentFolder, False, definition, Nothing, warnings)  
  
   If Not (warnings.Length = 0) Then  
      Dim warning As Warning  
      For Each warning In warnings  
         Console.WriteLine(warning.Message)  
      Next warning  
   Else  
      Console.WriteLine("Report {0} created successfully with no warnings", name)  
   End If  
  
Catch ex As SoapException  
   Console.WriteLine(ex.Detail("Message").InnerXml)  
End Try  
```  
  
```csharp  
try  
{  
   rs.CreateCatalogItem("Report", name, parentFolder, false, definition, null, out warnings);  
  
   if (warnings.Length != 0)  
   {  
      foreach (Warning warning in warnings)  
      {  
         Console.WriteLine(warning.Message);  
      }  
   }  
   else  
      Console.WriteLine("Report {0} created successfully with no warnings", name);  
}  
  
catch (SoapException ex)  
{  
   Console.WriteLine(ex.Detail["Message"].InnerXml);  
}  
```  
  
 <span data-ttu-id="f90fc-106">处理错误的另一个方法是评估某些方法的返回值。</span><span class="sxs-lookup"><span data-stu-id="f90fc-106">Another way to handle errors is to evaluate the return values of certain methods.</span></span> <span data-ttu-id="f90fc-107">例如，<xref:ReportService2010.ReportingService2010.FindItems%2A> 方法可用于搜索报表服务器数据库中的特定项。</span><span class="sxs-lookup"><span data-stu-id="f90fc-107">For example, the <xref:ReportService2010.ReportingService2010.FindItems%2A> method can be used to search for specific items in the report server database.</span></span> <span data-ttu-id="f90fc-108">如果未找到匹配搜索条件的项，则返回空的 <xref:ReportService2010.CatalogItem> 对象的数组。</span><span class="sxs-lookup"><span data-stu-id="f90fc-108">If no items are found that match the search criteria, a null array of <xref:ReportService2010.CatalogItem> objects is returned.</span></span> <span data-ttu-id="f90fc-109">您应该对该数组进行评估、检查 `null` 并让用户知道未找到任何项。</span><span class="sxs-lookup"><span data-stu-id="f90fc-109">You should evaluate the array, check for `null`, and let the user know if no items were found.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f90fc-110">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f90fc-110">See Also</span></span>  
 <xref:ReportService2010.CatalogItem>   
 <span data-ttu-id="f90fc-111">[介绍 Reporting Services 中的异常处理](../introducing-exception-handling-in-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="f90fc-111">[Introducing Exception Handling in Reporting Services](../introducing-exception-handling-in-reporting-services.md) </span></span>  
 [<span data-ttu-id="f90fc-112">Reporting Services SoapException 类</span><span class="sxs-lookup"><span data-stu-id="f90fc-112">Reporting Services SoapException Class</span></span>](../soapexception-class/reporting-services-soapexception-class.md)  
  
  
