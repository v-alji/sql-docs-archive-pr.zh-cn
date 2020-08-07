---
title: 使用 Detail 属性处理特定错误 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- exceptions [Reporting Services], Detail property
- Detail property
- InnerText property
ms.assetid: 4392633d-b46b-41e6-bc12-efb64e166704
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 4f8ac62dc381d8f665a44fc0897ba1f4215aa8e5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691074"
---
# <a name="using-the-detail-property-to-handle-specific-errors"></a><span data-ttu-id="222ab-102">使用 Detail 属性处理特定错误</span><span class="sxs-lookup"><span data-stu-id="222ab-102">Using the Detail Property to Handle Specific Errors</span></span>
  <span data-ttu-id="222ab-103">为了进一步对异常进行分类，[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 在 SOAP 异常的 Detail 属性的子元素的 InnerText 属性中返回附加错误信息\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="222ab-103">To further classify exceptions, [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] returns additional error information in the **InnerText** property of the child elements in the SOAP exception's **Detail** property.</span></span> <span data-ttu-id="222ab-104">因为该 Detail 属性是 XmlNode 对象，所以，可以使用以下代码访问 Message 子元素的内部文本\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="222ab-104">Because the **Detail** property is an **XmlNode** object, you can access the inner text of the **Message** child element using the following code.</span></span>  
  
 <span data-ttu-id="222ab-105">有关在 Detail 属性中包含的所有可用子元素的列表，请参阅 [Detail 属性](../soapexception-class/detail-property.md)\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="222ab-105">For a list of all of the available child elements contained in the **Detail** property, see [Detail Property](../soapexception-class/detail-property.md).</span></span> <span data-ttu-id="222ab-106">有关详细信息，请参阅 SDK 文档中的 "Detail 属性" [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="222ab-106">For more information, see "Detail Property" in the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK documentation.</span></span>  
  
```vb  
Try  
' Code for accessing the report server  
Catch ex As SoapException  
   ' The exception is a SOAP exception, so use  
   ' the Detail property's Message element.  
   Console.WriteLine(ex.Detail("Message").InnerXml)  
End Try  
```  
  
```csharp  
try  
{  
   // Code for accessing the report server  
}  
catch (SoapException ex)  
{  
   // The exception is a SOAP exception, so use  
   // the Detail property's Message element.  
   Console.WriteLine(ex.Detail["Message"].InnerXml);  
}  
```  
  
```vb  
Try  
' Code for accessing the report server  
Catch ex As SoapException  
   If ex.Detail("ErrorCode").InnerXml = "rsInvalidItemName" Then  
   End If ' Perform an action based on the specific error code  
End Try  
```  
  
```csharp  
try  
{  
   // Code for accessing the report server  
}  
catch (SoapException ex)  
{  
   if (ex.Detail["ErrorCode"].InnerXml == "rsInvalidItemName")  
   {  
      // Perform an action based on the specific error code  
   }  
}  
```  
  
 <span data-ttu-id="222ab-107">下面的代码行将在 SOAP 异常中返回的特定错误代码写入控制台。</span><span class="sxs-lookup"><span data-stu-id="222ab-107">The following line of code writes the specific error code being returned in the SOAP Exception to the console.</span></span> <span data-ttu-id="222ab-108">您还可以对错误代码进行评估并执行特定操作。</span><span class="sxs-lookup"><span data-stu-id="222ab-108">You could also evaluate the error code and perform specific actions.</span></span>  
  
```vb  
Console.WriteLine(ex.Detail("ErrorCode").InnerXml)  
```  
  
```csharp  
Console.WriteLine(ex.Detail["ErrorCode"].InnerXml);  
```  
  
## <a name="see-also"></a><span data-ttu-id="222ab-109">另请参阅</span><span class="sxs-lookup"><span data-stu-id="222ab-109">See Also</span></span>  
 <span data-ttu-id="222ab-110">[介绍 Reporting Services 中的异常处理](../introducing-exception-handling-in-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="222ab-110">[Introducing Exception Handling in Reporting Services](../introducing-exception-handling-in-reporting-services.md) </span></span>  
 <span data-ttu-id="222ab-111">[Reporting Services SoapException 类](../soapexception-class/reporting-services-soapexception-class.md) </span><span class="sxs-lookup"><span data-stu-id="222ab-111">[Reporting Services SoapException Class](../soapexception-class/reporting-services-soapexception-class.md) </span></span>  
 [<span data-ttu-id="222ab-112">SoapException 错误表</span><span class="sxs-lookup"><span data-stu-id="222ab-112">SoapException Errors Table</span></span>](../soapexception-class/soapexception-errors-table.md)  
  
  
