---
title: Reporting Services 异常处理的最佳做法 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- exceptions [Reporting Services], best practices
ms.assetid: 72fecf28-f02e-4338-b50f-0b21f520302d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2e0561c19fbd3e709a0440a55f023f938eabf692
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581129"
---
# <a name="best-practices-for-reporting-services-exception-handling"></a><span data-ttu-id="620ac-102">Reporting Services 异常处理的最佳实践</span><span class="sxs-lookup"><span data-stu-id="620ac-102">Best Practices for Reporting Services Exception Handling</span></span>
  <span data-ttu-id="620ac-103">当开发 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 应用程序时，可以使用多种方法来消除或减少异常的发生。</span><span class="sxs-lookup"><span data-stu-id="620ac-103">When developing [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] applications, there are several methodologies you can use to eliminate or reduce the occurrence of exceptions.</span></span> <span data-ttu-id="620ac-104">当确实发生异常时，请向用户提供明确和简洁的错误消息，并添加适当的异常处理以防止应用程序意外结束。</span><span class="sxs-lookup"><span data-stu-id="620ac-104">When exceptions do occur, provide clear and concise error messages to the user, and add adequate exception handling to prevent your applications from ending unexpectedly.</span></span>  
  
 <span data-ttu-id="620ac-105">向报表服务器 Web 服务发送请求的应用程序应执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="620ac-105">An application that sends requests to the Report Server Web service should do the following:</span></span>  
  
-   <span data-ttu-id="620ac-106">通过尽量防止无效请求，以避免导致异常。</span><span class="sxs-lookup"><span data-stu-id="620ac-106">Avoid causing exceptions by preventing as many invalid requests as possible.</span></span>  
  
-   <span data-ttu-id="620ac-107">尽可能捕获异常并提供有针对性的错误处理代码。</span><span class="sxs-lookup"><span data-stu-id="620ac-107">Catch exceptions and provide specific error-handling code whenever possible.</span></span>  
  
-   <span data-ttu-id="620ac-108">处理不引发异常的错误情况。</span><span class="sxs-lookup"><span data-stu-id="620ac-108">Deal with error cases that do not throw exceptions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="620ac-109">本节内容</span><span class="sxs-lookup"><span data-stu-id="620ac-109">In This Section</span></span>  
  
|<span data-ttu-id="620ac-110">主题</span><span class="sxs-lookup"><span data-stu-id="620ac-110">Topic</span></span>|<span data-ttu-id="620ac-111">说明</span><span class="sxs-lookup"><span data-stu-id="620ac-111">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="620ac-112">防止无效请求</span><span class="sxs-lookup"><span data-stu-id="620ac-112">Preventing Invalid Requests</span></span>](preventing-invalid-requests.md)|<span data-ttu-id="620ac-113">介绍防止将无效请求发送到报表服务器的方法。</span><span class="sxs-lookup"><span data-stu-id="620ac-113">Describes techniques for preventing requests that are not valid from being sent to the report server.</span></span>|  
|[<span data-ttu-id="620ac-114">使用 Try 和 Catch 块</span><span class="sxs-lookup"><span data-stu-id="620ac-114">Using Try and Catch Blocks</span></span>](using-try-and-catch-blocks.md)|<span data-ttu-id="620ac-115">介绍如何通过 try/catch 块进一步增强应用程序的可靠性。</span><span class="sxs-lookup"><span data-stu-id="620ac-115">Describes how to further enhance the reliability of your application with try/catch blocks.</span></span>|  
|[<span data-ttu-id="620ac-116">处理不导致异常的警告和事例</span><span class="sxs-lookup"><span data-stu-id="620ac-116">Handling Warnings and Cases That Do Not Cause Exceptions</span></span>](handling-warnings-and-cases-that-do-not-cause-exceptions.md)|<span data-ttu-id="620ac-117">说明如何处理不会导致由 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 引发的异常的错误。</span><span class="sxs-lookup"><span data-stu-id="620ac-117">Explains how to handle errors that do not result in an exception being thrown by [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span>|  
|[<span data-ttu-id="620ac-118">使用 Detail 属性处理特定错误</span><span class="sxs-lookup"><span data-stu-id="620ac-118">Using the Detail Property to Handle Specific Errors</span></span>](using-the-detail-property-to-handle-specific-errors.md)|<span data-ttu-id="620ac-119">说明如何通过使用 SoapException 对象的 Detail 属性以编程方式处理特定的错误\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="620ac-119">Explains how to programmatically handle specific errors by using the **Detail** property of the **SoapException** object.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="620ac-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="620ac-120">See Also</span></span>  
 <span data-ttu-id="620ac-121">[Detail 属性](../soapexception-class/detail-property.md) </span><span class="sxs-lookup"><span data-stu-id="620ac-121">[Detail Property](../soapexception-class/detail-property.md) </span></span>  
 <span data-ttu-id="620ac-122">[介绍 Reporting Services 中的异常处理](../introducing-exception-handling-in-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="620ac-122">[Introducing Exception Handling in Reporting Services](../introducing-exception-handling-in-reporting-services.md) </span></span>  
 [<span data-ttu-id="620ac-123">Reporting Services SoapException 类</span><span class="sxs-lookup"><span data-stu-id="620ac-123">Reporting Services SoapException Class</span></span>](../soapexception-class/reporting-services-soapexception-class.md)  
  
  
