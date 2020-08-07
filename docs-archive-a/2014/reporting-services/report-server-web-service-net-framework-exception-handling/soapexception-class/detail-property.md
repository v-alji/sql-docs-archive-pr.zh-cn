---
title: Detail 属性 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- Detail property
- SoapException class
ms.assetid: c1ddaeb6-c540-49fa-b06e-b6359d377ee8
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 060fbaba2b8d4f5a5171e8aa7995432622ba2ba0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691073"
---
# <a name="detail-property"></a><span data-ttu-id="825a3-102">Detail 属性</span><span class="sxs-lookup"><span data-stu-id="825a3-102">Detail Property</span></span>
  <span data-ttu-id="825a3-103">“SoapException”[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] \*\*\*\* 类的“Detail”\*\*\*\* 属性具有以下 XML 结构：</span><span class="sxs-lookup"><span data-stu-id="825a3-103">The **Detail** property of the [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] **SoapException** class has the following XML structure:</span></span>  
  
## <a name="elements"></a><span data-ttu-id="825a3-104">元素</span><span class="sxs-lookup"><span data-stu-id="825a3-104">Elements</span></span>  
 <span data-ttu-id="825a3-105">**详细信息**</span><span class="sxs-lookup"><span data-stu-id="825a3-105">**Detail**</span></span>  
 <span data-ttu-id="825a3-106">包含所有其他错误详细信息元素的顶级元素。</span><span class="sxs-lookup"><span data-stu-id="825a3-106">The top-level element that contains all other error detail elements.</span></span>  
  
 <span data-ttu-id="825a3-107">**ErrorCode**</span><span class="sxs-lookup"><span data-stu-id="825a3-107">**ErrorCode**</span></span>  
 <span data-ttu-id="825a3-108">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 特定的错误代码。</span><span class="sxs-lookup"><span data-stu-id="825a3-108">The [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]-specific error code.</span></span>  
  
 <span data-ttu-id="825a3-109">**HttpStatus**</span><span class="sxs-lookup"><span data-stu-id="825a3-109">**HttpStatus**</span></span>  
 <span data-ttu-id="825a3-110">HTTP 状态代码。</span><span class="sxs-lookup"><span data-stu-id="825a3-110">The HTTP status code.</span></span>  
  
 <span data-ttu-id="825a3-111">**Message**</span><span class="sxs-lookup"><span data-stu-id="825a3-111">**Message**</span></span>  
 <span data-ttu-id="825a3-112">报表服务器分配的错误消息和错误代码。</span><span class="sxs-lookup"><span data-stu-id="825a3-112">The error message and the error code assigned by the report server.</span></span>  
  
 <span data-ttu-id="825a3-113">**HelpLink**</span><span class="sxs-lookup"><span data-stu-id="825a3-113">**HelpLink**</span></span>  
 <span data-ttu-id="825a3-114">指向某网站的帮助链接 URL，在该网站中可以找到有关错误的更多信息。</span><span class="sxs-lookup"><span data-stu-id="825a3-114">The Help link URL to a Web site at which further information about the error can be found.</span></span> <span data-ttu-id="825a3-115">有关详细信息，请参阅 [HelpLink 元素](helplink-element.md)。</span><span class="sxs-lookup"><span data-stu-id="825a3-115">For more information, see [HelpLink Element](helplink-element.md).</span></span>  
  
 <span data-ttu-id="825a3-116">LinkID\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="825a3-116">**LinkID**</span></span>  
 <span data-ttu-id="825a3-117">分配给链接的 ID。</span><span class="sxs-lookup"><span data-stu-id="825a3-117">The ID assigned to the link.</span></span>  
  
 <span data-ttu-id="825a3-118">**ProductName**</span><span class="sxs-lookup"><span data-stu-id="825a3-118">**ProductName**</span></span>  
 <span data-ttu-id="825a3-119">产品的名称。</span><span class="sxs-lookup"><span data-stu-id="825a3-119">The name of the product.</span></span> <span data-ttu-id="825a3-120">默认值为“Microsoft SQL Server Reporting Services”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="825a3-120">The default value is **Microsoft SQL Server Reporting Services**.</span></span>  
  
 <span data-ttu-id="825a3-121">**ProductVersion**</span><span class="sxs-lookup"><span data-stu-id="825a3-121">**ProductVersion**</span></span>  
 <span data-ttu-id="825a3-122">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]的版本。</span><span class="sxs-lookup"><span data-stu-id="825a3-122">The version of [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="825a3-123">最大长度为 15 个字符。</span><span class="sxs-lookup"><span data-stu-id="825a3-123">The maximum length is 15 characters.</span></span> <span data-ttu-id="825a3-124">版本号的格式应如下所示：8.00.0xxx.00。</span><span class="sxs-lookup"><span data-stu-id="825a3-124">The format of the version number should be as follows: 8.00.0xxx.00.</span></span>  
  
 <span data-ttu-id="825a3-125">ProductLocaleId\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="825a3-125">**ProductLocaleId**</span></span>  
 <span data-ttu-id="825a3-126">应用程序的 INTL DLL 的区域设置 ID 或语言 ID（例如，0x41A）。</span><span class="sxs-lookup"><span data-stu-id="825a3-126">The locale ID or language ID of the application's INTL DLL (for example, 0x41A).</span></span>  
  
 <span data-ttu-id="825a3-127">**OperatingSystem**</span><span class="sxs-lookup"><span data-stu-id="825a3-127">**OperatingSystem**</span></span>  
 <span data-ttu-id="825a3-128">在其中安装 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 的操作系统。</span><span class="sxs-lookup"><span data-stu-id="825a3-128">The operating system [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] is installed on.</span></span> <span data-ttu-id="825a3-129">有效值包括：“0”\*\*\*\* 表示独立于操作系统，“1”\*\*\*\* 表示 [!INCLUDE[win2kfamily](../../../includes/win2kfamily-md.md)]，“16”\*\*\*\* 表示 Windows XP。</span><span class="sxs-lookup"><span data-stu-id="825a3-129">Valid values include **0** for operating system independent, **1** for [!INCLUDE[win2kfamily](../../../includes/win2kfamily-md.md)], and **16** for Windows XP.</span></span>  
  
 <span data-ttu-id="825a3-130">CountryLocaleId\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="825a3-130">**CountryLocaleId**</span></span>  
 <span data-ttu-id="825a3-131">操作系统的区域设置 ID 或语言 ID。</span><span class="sxs-lookup"><span data-stu-id="825a3-131">The locale ID or language ID of the operating system.</span></span> <span data-ttu-id="825a3-132">例如，对应于 Windows 法语版的值为 0x040c。</span><span class="sxs-lookup"><span data-stu-id="825a3-132">For example, the value for the French version of Windows is 0x040c.</span></span>  
  
 <span data-ttu-id="825a3-133">MoreInformation\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="825a3-133">**MoreInformation**</span></span>  
 <span data-ttu-id="825a3-134">一个 XML 字符串，其中包含在运行方法时出现的嵌套异常。</span><span class="sxs-lookup"><span data-stu-id="825a3-134">An XML string that contains nested exceptions that occurred while the method ran.</span></span>  
  
 <span data-ttu-id="825a3-135">**数据源**</span><span class="sxs-lookup"><span data-stu-id="825a3-135">**Source**</span></span>  
 <span data-ttu-id="825a3-136">“MoreInformation”\*\*\*\* 的一个子元素。</span><span class="sxs-lookup"><span data-stu-id="825a3-136">A child element of **MoreInformation**.</span></span> <span data-ttu-id="825a3-137">错误的源。</span><span class="sxs-lookup"><span data-stu-id="825a3-137">The source of the error.</span></span>  
  
 <span data-ttu-id="825a3-138">**Message**</span><span class="sxs-lookup"><span data-stu-id="825a3-138">**Message**</span></span>  
 <span data-ttu-id="825a3-139">“MoreInformation”\*\*\*\* 的一个子元素。</span><span class="sxs-lookup"><span data-stu-id="825a3-139">A child element of **MoreInformation**.</span></span> <span data-ttu-id="825a3-140">嵌套异常的错误消息。</span><span class="sxs-lookup"><span data-stu-id="825a3-140">The error message of a nested exception.</span></span> <span data-ttu-id="825a3-141">此元素包含“ErrorCode”\*\*\*\* 和“HelpLink”\*\*\*\* 的 XML 属性。</span><span class="sxs-lookup"><span data-stu-id="825a3-141">This element includes XML attributes for **ErrorCode** and **HelpLink**.</span></span>  
  
 <span data-ttu-id="825a3-142">**警告**</span><span class="sxs-lookup"><span data-stu-id="825a3-142">**Warnings**</span></span>  
 <span data-ttu-id="825a3-143">一个 XML 字符串，其中包含从报表处理返回的警告。</span><span class="sxs-lookup"><span data-stu-id="825a3-143">An XML string that contains the warnings returned from report processing.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="825a3-144">另请参阅</span><span class="sxs-lookup"><span data-stu-id="825a3-144">See Also</span></span>  
 <span data-ttu-id="825a3-145">[介绍 Reporting Services 中的异常处理](../introducing-exception-handling-in-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="825a3-145">[Introducing Exception Handling in Reporting Services](../introducing-exception-handling-in-reporting-services.md) </span></span>  
 <span data-ttu-id="825a3-146">[Reporting Services SoapException 类](reporting-services-soapexception-class.md) </span><span class="sxs-lookup"><span data-stu-id="825a3-146">[Reporting Services SoapException Class](reporting-services-soapexception-class.md) </span></span>  
 [<span data-ttu-id="825a3-147">使用 Detail 属性处理特定错误</span><span class="sxs-lookup"><span data-stu-id="825a3-147">Using the Detail Property to Handle Specific Errors</span></span>](../best-practices/using-the-detail-property-to-handle-specific-errors.md)  
  
  
