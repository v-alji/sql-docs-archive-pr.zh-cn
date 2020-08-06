---
title: Reporting Services SoapException 类 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- exceptions [Reporting Services], SoapException class
- SoapException class
ms.assetid: 2cec49ee-20b1-40eb-a75b-0908d9c05b34
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 6f6efdfac89014116957990ef2db21cf52e76a4f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689281"
---
# <a name="reporting-services-soapexception-class"></a><span data-ttu-id="a7dbe-102">Reporting Services SoapException 类</span><span class="sxs-lookup"><span data-stu-id="a7dbe-102">Reporting Services SoapException Class</span></span>
  <span data-ttu-id="a7dbe-103">您应该解决已知可能会发生的特定 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 错误。</span><span class="sxs-lookup"><span data-stu-id="a7dbe-103">You should address specific [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] errors that you know might happen.</span></span> <span data-ttu-id="a7dbe-104">例如，在您要求用户创建某一文件夹的应用程序中，该用户可能尝试创建已存在的文件夹。</span><span class="sxs-lookup"><span data-stu-id="a7dbe-104">For example, in an application where you ask the user to create a folder, it might be possible for the user to try to create a folder that already exists.</span></span> <span data-ttu-id="a7dbe-105">作为开发人员，您无法控制用户在您的应用程序的文件夹名称和路径字段中输入的内容，但可以控制当某人无意中尝试创建已存在的项时的用户体验。</span><span class="sxs-lookup"><span data-stu-id="a7dbe-105">As the developer, you do not have control over what the user enters in the folder name and path fields of your application, but you do have control over what the user experience is when someone incidentally tries to create an item that already exists.</span></span>  
  
 <span data-ttu-id="a7dbe-106">为了轻松捕获特定错误情况，[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 使用 SoapException 类的属性分类异常的错误代码，并返回错误的分类\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a7dbe-106">To make it easier for you to catch specific error conditions, [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] classifies an error code for the exception and returns the classification of the error using properties from the **SoapException** class.</span></span> <span data-ttu-id="a7dbe-107">有关详细信息，请参阅 SDK 文档中的 "SoapException 类" [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="a7dbe-107">For more information, see "SoapException Class" in the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK documentation.</span></span>  
  
 <span data-ttu-id="a7dbe-108">下表列出 SoapException 类的公共属性\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a7dbe-108">The following table lists the public properties of the **SoapException** class.</span></span>  
  
|<span data-ttu-id="a7dbe-109">公共属性</span><span class="sxs-lookup"><span data-stu-id="a7dbe-109">Public property</span></span>|<span data-ttu-id="a7dbe-110">说明</span><span class="sxs-lookup"><span data-stu-id="a7dbe-110">Description</span></span>|  
|---------------------|-----------------|  
|<span data-ttu-id="a7dbe-111">演员</span><span class="sxs-lookup"><span data-stu-id="a7dbe-111">**Actor**</span></span>|<span data-ttu-id="a7dbe-112">导致了异常的代码。</span><span class="sxs-lookup"><span data-stu-id="a7dbe-112">The code that caused the exception.</span></span> <span data-ttu-id="a7dbe-113">该值是指向 Web 服务方法的 URL。</span><span class="sxs-lookup"><span data-stu-id="a7dbe-113">The value is the URL to the Web service method.</span></span>|  
|<span data-ttu-id="a7dbe-114">**详细信息**</span><span class="sxs-lookup"><span data-stu-id="a7dbe-114">**Detail**</span></span>|<span data-ttu-id="a7dbe-115">应用程序特定的错误信息。</span><span class="sxs-lookup"><span data-stu-id="a7dbe-115">Application-specific error information.</span></span> <span data-ttu-id="a7dbe-116">该值由报表服务器设置并且采用 XML 格式。</span><span class="sxs-lookup"><span data-stu-id="a7dbe-116">The value is set by the report server and is in XML format.</span></span> <span data-ttu-id="a7dbe-117">有关详细信息，请参阅 [Detail 属性](detail-property.md)和[使用 Detail 属性处理特定错误](../best-practices/using-the-detail-property-to-handle-specific-errors.md)。</span><span class="sxs-lookup"><span data-stu-id="a7dbe-117">For more information, see [Detail Property](detail-property.md) and [Using the Detail Property to Handle Specific Errors](../best-practices/using-the-detail-property-to-handle-specific-errors.md).</span></span>|  
|<span data-ttu-id="a7dbe-118">**HelpLink**</span><span class="sxs-lookup"><span data-stu-id="a7dbe-118">**HelpLink**</span></span>|<span data-ttu-id="a7dbe-119">指向与错误相关联的帮助文件的 URL 或 URN。</span><span class="sxs-lookup"><span data-stu-id="a7dbe-119">A URL or URN to a Help file associated with the error.</span></span> <span data-ttu-id="a7dbe-120">该值通常由 Web 服务设置并且它设置指向 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] 帮助和支持的 URL。</span><span class="sxs-lookup"><span data-stu-id="a7dbe-120">The value is usually set by the Web service and it sets a URL to [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Help and Support.</span></span> <span data-ttu-id="a7dbe-121">因为 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 针对发生的错误支持多个帮助链接，所以，报表服务器将帮助链接信息设置为 Detail 属性的一部分\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a7dbe-121">Because [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] supports multiple help links for errors that occur, the report server sets help link information as part of the **Detail** property.</span></span> <span data-ttu-id="a7dbe-122">有关详细信息，请参阅 [HelpLink 元素](helplink-element.md)。</span><span class="sxs-lookup"><span data-stu-id="a7dbe-122">For more information, see [HelpLink Element](helplink-element.md).</span></span>|  
|<span data-ttu-id="a7dbe-123">**Message**</span><span class="sxs-lookup"><span data-stu-id="a7dbe-123">**Message**</span></span>|<span data-ttu-id="a7dbe-124">描述错误的描述性的本地化消息。</span><span class="sxs-lookup"><span data-stu-id="a7dbe-124">A descriptive, localized message that describes the error.</span></span> <span data-ttu-id="a7dbe-125">此文本可能出现在应用程序用户界面中。</span><span class="sxs-lookup"><span data-stu-id="a7dbe-125">This text might appear in the application UI.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a7dbe-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a7dbe-126">See Also</span></span>  
 <span data-ttu-id="a7dbe-127">[介绍 Reporting Services 中的异常处理](../introducing-exception-handling-in-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="a7dbe-127">[Introducing Exception Handling in Reporting Services](../introducing-exception-handling-in-reporting-services.md) </span></span>  
 [<span data-ttu-id="a7dbe-128">SoapException 错误表</span><span class="sxs-lookup"><span data-stu-id="a7dbe-128">SoapException Errors Table</span></span>](soapexception-errors-table.md)  
  
  
