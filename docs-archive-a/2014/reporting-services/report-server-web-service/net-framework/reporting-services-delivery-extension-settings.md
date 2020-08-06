---
title: Reporting Services 传递扩展插件设置 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- XML Web service [Reporting Services], delivery extension settings
- Report Server Web service, delivery extension settings
- delivery [Reporting Services]
- network share delivery [Reporting Services]
- file share delivery [Reporting Services]
- e-mail [Reporting Services]
- mailing reports [Reporting Services]
- sharing reports
- extensions [Reporting Services], delivery
- mail [Reporting Services]
- Web service [Reporting Services], delivery extension settings
ms.assetid: 68c31a85-261c-4ec4-b8df-1f9842b46f8a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d5363c99cb858ce61f7be3b039e27a69944767b9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688528"
---
# <a name="reporting-services-delivery-extension-settings"></a><span data-ttu-id="92ceb-102">Reporting Services 传递扩展插件设置</span><span class="sxs-lookup"><span data-stu-id="92ceb-102">Reporting Services Delivery Extension Settings</span></span>
  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] <span data-ttu-id="92ceb-103">包括电子邮件传递扩展插件和文件共享传递扩展插件。</span><span class="sxs-lookup"><span data-stu-id="92ceb-103">includes an e-mail delivery extension and a file share delivery extension.</span></span> <span data-ttu-id="92ceb-104">电子邮件传递扩展插件提供了通过电子邮件将报表发送到单个用户或组的方式。</span><span class="sxs-lookup"><span data-stu-id="92ceb-104">E-mail delivery provides a way to send a report to individual users or groups through e-mail.</span></span> <span data-ttu-id="92ceb-105">文件共享传递扩展插件可用于将呈现的报表自动发送到网络上的共享区中。</span><span class="sxs-lookup"><span data-stu-id="92ceb-105">File share delivery enables you to automatically send rendered reports to a share on your network.</span></span> <span data-ttu-id="92ceb-106">您可以使用具有标准订阅或数据驱动订阅的支持的传递扩展插件之一。</span><span class="sxs-lookup"><span data-stu-id="92ceb-106">You can use either one of the supported delivery extensions with standard subscriptions or data-driven subscriptions.</span></span> <span data-ttu-id="92ceb-107">只要您调用 <xref:ReportService2010.ReportingService2010.CreateSubscription%2A>、<xref:ReportService2010.ReportingService2010.CreateDataDrivenSubscription%2A>、<xref:ReportService2010.ReportingService2010.SetSubscriptionProperties%2A> 和 <xref:ReportService2010.ReportingService2010.SetDataDrivenSubscriptionProperties%2A> 方法，就将传递特定于传递扩展插件类型的传递设置。</span><span class="sxs-lookup"><span data-stu-id="92ceb-107">You pass delivery settings that are specific to the type of delivery extension whenever you call the <xref:ReportService2010.ReportingService2010.CreateSubscription%2A>,<xref:ReportService2010.ReportingService2010.CreateDataDrivenSubscription%2A>,<xref:ReportService2010.ReportingService2010.SetSubscriptionProperties%2A>, and <xref:ReportService2010.ReportingService2010.SetDataDrivenSubscriptionProperties%2A> methods.</span></span> <span data-ttu-id="92ceb-108">若要以编程方式检索传递设置的列表，请使用 <xref:ReportService2010.ReportingService2010.GetExtensionSettings%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="92ceb-108">To retrieve a list of delivery settings programmatically, use the <xref:ReportService2010.ReportingService2010.GetExtensionSettings%2A> method.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="92ceb-109">传递扩展插件设置区分大小写。</span><span class="sxs-lookup"><span data-stu-id="92ceb-109">Delivery extension settings are case-sensitive.</span></span>  
  
## <a name="e-mail-delivery-settings"></a><span data-ttu-id="92ceb-110">电子邮件传递设置</span><span class="sxs-lookup"><span data-stu-id="92ceb-110">E-Mail Delivery Settings</span></span>  
 <span data-ttu-id="92ceb-111">下表列出用于使用报表服务器电子邮件的订阅的电子邮件传递设置。</span><span class="sxs-lookup"><span data-stu-id="92ceb-111">The following table lists the e-mail delivery settings for subscriptions that use report server e-mail.</span></span>  
  
|<span data-ttu-id="92ceb-112">设置</span><span class="sxs-lookup"><span data-stu-id="92ceb-112">Setting</span></span>|<span data-ttu-id="92ceb-113">值</span><span class="sxs-lookup"><span data-stu-id="92ceb-113">Value</span></span>|  
|-------------|-----------|  
|<span data-ttu-id="92ceb-114">**自**</span><span class="sxs-lookup"><span data-stu-id="92ceb-114">**TO**</span></span>|<span data-ttu-id="92ceb-115">在电子邮件的 `To` 行中出现的电子邮件地址。</span><span class="sxs-lookup"><span data-stu-id="92ceb-115">The e-mail address that appears on the `To` line of the e-mail message.</span></span> <span data-ttu-id="92ceb-116">多个电子邮件地址之间用分号分隔。</span><span class="sxs-lookup"><span data-stu-id="92ceb-116">Multiple e-mail addresses are separated by semicolons.</span></span> <span data-ttu-id="92ceb-117">必需。</span><span class="sxs-lookup"><span data-stu-id="92ceb-117">Required.</span></span>|  
|<span data-ttu-id="92ceb-118">**字幕**</span><span class="sxs-lookup"><span data-stu-id="92ceb-118">**CC**</span></span>|<span data-ttu-id="92ceb-119">在电子邮件的 `Cc` 行中出现的电子邮件地址。</span><span class="sxs-lookup"><span data-stu-id="92ceb-119">The e-mail address that appears on the `Cc` line of the e-mail message.</span></span> <span data-ttu-id="92ceb-120">多个电子邮件地址之间用分号分隔。</span><span class="sxs-lookup"><span data-stu-id="92ceb-120">Multiple e-mail addresses are separated by semicolons.</span></span> <span data-ttu-id="92ceb-121">可选。</span><span class="sxs-lookup"><span data-stu-id="92ceb-121">Optional.</span></span>|  
|<span data-ttu-id="92ceb-122">**框**</span><span class="sxs-lookup"><span data-stu-id="92ceb-122">**BCC**</span></span>|<span data-ttu-id="92ceb-123">在电子邮件的 `Bcc` 行中出现的电子邮件地址。</span><span class="sxs-lookup"><span data-stu-id="92ceb-123">The e-mail address that appears on the `Bcc` line of the e-mail message.</span></span> <span data-ttu-id="92ceb-124">多个电子邮件地址之间用分号分隔。</span><span class="sxs-lookup"><span data-stu-id="92ceb-124">Multiple e-mail addresses are separated by semicolons.</span></span> <span data-ttu-id="92ceb-125">可选。</span><span class="sxs-lookup"><span data-stu-id="92ceb-125">Optional.</span></span>|  
|<span data-ttu-id="92ceb-126">**ReplyTo**</span><span class="sxs-lookup"><span data-stu-id="92ceb-126">**ReplyTo**</span></span>|<span data-ttu-id="92ceb-127">在电子邮件的 `Reply-To` 标题中出现的电子邮件地址。</span><span class="sxs-lookup"><span data-stu-id="92ceb-127">The e-mail address that appears in the `Reply-To` header of the e-mail message.</span></span> <span data-ttu-id="92ceb-128">该值必须为单个电子邮件地址。</span><span class="sxs-lookup"><span data-stu-id="92ceb-128">The value must be a single e-mail address.</span></span> <span data-ttu-id="92ceb-129">可选。</span><span class="sxs-lookup"><span data-stu-id="92ceb-129">Optional.</span></span>|  
|`IncludeReport`|<span data-ttu-id="92ceb-130">指示是否在电子邮件传递中包括报表的值。</span><span class="sxs-lookup"><span data-stu-id="92ceb-130">A value that indicates whether to include the report in the e-mail delivery.</span></span> <span data-ttu-id="92ceb-131">如果值为 `true`，则指示在电子邮件的正文中传递报表。</span><span class="sxs-lookup"><span data-stu-id="92ceb-131">A value of `true` indicates that the report is delivered in the body of the e-mail message.</span></span>|  
|<span data-ttu-id="92ceb-132">**RenderFormat**</span><span class="sxs-lookup"><span data-stu-id="92ceb-132">**RenderFormat**</span></span>|<span data-ttu-id="92ceb-133">要用于生成呈现的报表的呈现扩展插件的名称。</span><span class="sxs-lookup"><span data-stu-id="92ceb-133">The name of the rendering extension to use to generate the rendered report.</span></span> <span data-ttu-id="92ceb-134">该名称必须与在报表服务器上安装的可见呈现扩展插件之一相符。</span><span class="sxs-lookup"><span data-stu-id="92ceb-134">The name must correspond to one of the visible rendering extensions installed on the report server.</span></span> <span data-ttu-id="92ceb-135">如果该 `IncludeReport` 设置设置为 `true` 值，则该值是必需的。</span><span class="sxs-lookup"><span data-stu-id="92ceb-135">This value is required if the `IncludeReport` setting is set to a value of `true`.</span></span>|  
|<span data-ttu-id="92ceb-136">**Priority**</span><span class="sxs-lookup"><span data-stu-id="92ceb-136">**Priority**</span></span>|<span data-ttu-id="92ceb-137">电子邮件按其发送的优先级。</span><span class="sxs-lookup"><span data-stu-id="92ceb-137">The priority with which the e-mail message is sent.</span></span> <span data-ttu-id="92ceb-138">有效值为 `LOW`、`NORMAL` 和 `HIGH`。</span><span class="sxs-lookup"><span data-stu-id="92ceb-138">Valid values are `LOW`, `NORMAL`, and `HIGH`.</span></span> <span data-ttu-id="92ceb-139">默认值为 `NORMAL`。</span><span class="sxs-lookup"><span data-stu-id="92ceb-139">The default value is `NORMAL`.</span></span>|  
|<span data-ttu-id="92ceb-140">**主题**</span><span class="sxs-lookup"><span data-stu-id="92ceb-140">**Subject**</span></span>|<span data-ttu-id="92ceb-141">电子邮件的主题行中的文本。</span><span class="sxs-lookup"><span data-stu-id="92ceb-141">The text in the subject line of the e-mail message.</span></span>|  
|<span data-ttu-id="92ceb-142">**注释**</span><span class="sxs-lookup"><span data-stu-id="92ceb-142">**Comment**</span></span>|<span data-ttu-id="92ceb-143">包括在电子邮件的正文中的文本。</span><span class="sxs-lookup"><span data-stu-id="92ceb-143">The text included in the body of the e-mail message.</span></span>|  
|<span data-ttu-id="92ceb-144">IncludeLink\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="92ceb-144">**IncludeLink**</span></span>|<span data-ttu-id="92ceb-145">指示是否在电子邮件正文中包括指向报表的链接的值。</span><span class="sxs-lookup"><span data-stu-id="92ceb-145">A value that indicates whether to include a link to the report in the body of the e-mail.</span></span>|  
  
## <a name="file-share-delivery-settings"></a><span data-ttu-id="92ceb-146">文件共享传递设置</span><span class="sxs-lookup"><span data-stu-id="92ceb-146">File Share Delivery Settings</span></span>  
 <span data-ttu-id="92ceb-147">下表列出用于订阅的文件共享传递设置。</span><span class="sxs-lookup"><span data-stu-id="92ceb-147">The following table lists the file share delivery settings for subscriptions.</span></span>  
  
|<span data-ttu-id="92ceb-148">设置</span><span class="sxs-lookup"><span data-stu-id="92ceb-148">Setting</span></span>|<span data-ttu-id="92ceb-149">值</span><span class="sxs-lookup"><span data-stu-id="92ceb-149">Value</span></span>|  
|-------------|-----------|  
|<span data-ttu-id="92ceb-150">**名字**</span><span class="sxs-lookup"><span data-stu-id="92ceb-150">**FILENAME**</span></span>|<span data-ttu-id="92ceb-151">保存到磁盘的文件的名称。</span><span class="sxs-lookup"><span data-stu-id="92ceb-151">The name of the file that is saved to disk.</span></span>|  
|<span data-ttu-id="92ceb-152">FILEEXTN\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="92ceb-152">**FILEEXTN**</span></span>|<span data-ttu-id="92ceb-153">指示是否为所呈现报表包括文件扩展名。</span><span class="sxs-lookup"><span data-stu-id="92ceb-153">Indicates whether to include a file extension for the rendered report.</span></span> <span data-ttu-id="92ceb-154">该值为 `true` 或 `false`。</span><span class="sxs-lookup"><span data-stu-id="92ceb-154">The value is either `true` or `false`.</span></span>|  
|<span data-ttu-id="92ceb-155">PATH</span><span class="sxs-lookup"><span data-stu-id="92ceb-155">**PATH**</span></span>|<span data-ttu-id="92ceb-156">要将报表保存到的文件夹路径或 UNC 文件共享路径。</span><span class="sxs-lookup"><span data-stu-id="92ceb-156">The folder path or UNC file share path to which to save the report.</span></span>|  
|<span data-ttu-id="92ceb-157">RENDER_FORMAT\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="92ceb-157">**RENDER_FORMAT**</span></span>|<span data-ttu-id="92ceb-158">保存到磁盘的报表的格式。</span><span class="sxs-lookup"><span data-stu-id="92ceb-158">The format of the report that is saved to disk.</span></span>|  
|<span data-ttu-id="92ceb-159">**用户名**</span><span class="sxs-lookup"><span data-stu-id="92ceb-159">**USERNAME**</span></span>|<span data-ttu-id="92ceb-160">访问网络资源或磁盘所需的用户名。</span><span class="sxs-lookup"><span data-stu-id="92ceb-160">The username required to access the network resource or disk.</span></span>|  
|<span data-ttu-id="92ceb-161">**权限**</span><span class="sxs-lookup"><span data-stu-id="92ceb-161">**PASSWORD**</span></span>|<span data-ttu-id="92ceb-162">访问网络资源或磁盘所需的密码。</span><span class="sxs-lookup"><span data-stu-id="92ceb-162">The password required to access the network resource or disk.</span></span>|  
|<span data-ttu-id="92ceb-163">WRITEMODE\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="92ceb-163">**WRITEMODE**</span></span>|<span data-ttu-id="92ceb-164">访问磁盘时要使用的写入模式。</span><span class="sxs-lookup"><span data-stu-id="92ceb-164">The write mode to use when accessing the disk.</span></span> <span data-ttu-id="92ceb-165">有效值为 `None`、`Overwrite` 和 `AutoIncrement`。</span><span class="sxs-lookup"><span data-stu-id="92ceb-165">Valid values are `None`, `Overwrite`, and `AutoIncrement`.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="92ceb-166">另请参阅</span><span class="sxs-lookup"><span data-stu-id="92ceb-166">See Also</span></span>  
 <span data-ttu-id="92ceb-167">[SSRS&#41;&#40;技术参考](../../technical-reference-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="92ceb-167">[Technical Reference &#40;SSRS&#41;](../../technical-reference-ssrs.md) </span></span>  
 [<span data-ttu-id="92ceb-168">使用 Web 服务和 .NET Framework 生成应用程序</span><span class="sxs-lookup"><span data-stu-id="92ceb-168">Building Applications Using the Web Service and the .NET Framework</span></span>](building-applications-using-the-web-service-and-the-net-framework.md)  
  
  
