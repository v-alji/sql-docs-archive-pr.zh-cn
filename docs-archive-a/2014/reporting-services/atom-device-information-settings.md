---
title: ATOM 设备信息设置 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: fe4a56a4-5552-423c-85c1-895e2e212fee
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: bdbac1500063accf868d4b538b82ba9f3b5aebb0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586516"
---
# <a name="atom-device-information-settings"></a><span data-ttu-id="62379-102">ATOM 设备信息设置</span><span class="sxs-lookup"><span data-stu-id="62379-102">ATOM Device Information Settings</span></span>
  <span data-ttu-id="62379-103">用于 Atom 呈现扩展插件的设备信息设置支持要使用的 Atom 馈送和字符编码的名称的提交。</span><span class="sxs-lookup"><span data-stu-id="62379-103">The device information settings for the Atom rendering extension support submittal of the name of an Atom feed and character encoding to use.</span></span>  
  
 <span data-ttu-id="62379-104">下表列出了用于向数据服务文档呈现的设备信息设置。</span><span class="sxs-lookup"><span data-stu-id="62379-104">The following table lists the device information settings for rendering to a data service document.</span></span>  
  
|<span data-ttu-id="62379-105">设置</span><span class="sxs-lookup"><span data-stu-id="62379-105">Setting</span></span>|<span data-ttu-id="62379-106">值</span><span class="sxs-lookup"><span data-stu-id="62379-106">Value</span></span>|  
|-------------|-----------|  
|`DataFeed`|<span data-ttu-id="62379-107">如果指定，则呈现与在此设置中提供的馈送名称相对应的 Atom 馈送。</span><span class="sxs-lookup"><span data-stu-id="62379-107">If specified, renders the Atom feed corresponding to the feed name provided in this setting.</span></span> <span data-ttu-id="62379-108">如果未指定，则呈现报表的 Atom 服务文档。</span><span class="sxs-lookup"><span data-stu-id="62379-108">If not, renders the Atom service document for the report.</span></span> <span data-ttu-id="62379-109">数据馈送的唯一自动生成的标识符。</span><span class="sxs-lookup"><span data-stu-id="62379-109">The unique auto-generated identifier of the data feed.</span></span> <span data-ttu-id="62379-110">该值在内部使用，而且不应更改它。</span><span class="sxs-lookup"><span data-stu-id="62379-110">This  value is used internally and you should not change it.</span></span>|  
|<span data-ttu-id="62379-111">**编码**</span><span class="sxs-lookup"><span data-stu-id="62379-111">**Encoding**</span></span>|<span data-ttu-id="62379-112">.NET Framework 支持的字符编码的 Internet 编号分配机构 (IANA) 名称。</span><span class="sxs-lookup"><span data-stu-id="62379-112">The Internet Assigned Numbers Authority (IANA) name of a character encoding that is supported by the .NET Framework.</span></span> <span data-ttu-id="62379-113">默认值为 `UTF-8`。</span><span class="sxs-lookup"><span data-stu-id="62379-113">The default value is `UTF-8`.</span></span> <span data-ttu-id="62379-114">其他值的示例包括 ASCII、UTF-7 和 UTF-16。</span><span class="sxs-lookup"><span data-stu-id="62379-114">Examples of other values include ASCII, UTF-7, and UTF-16.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="62379-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="62379-115">See Also</span></span>  
 <xref:ReportExecution2005.ReportExecutionService.Render%2A>   
 <span data-ttu-id="62379-116">[将设备信息设置传递给呈现扩展插件](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="62379-116">[Passing Device Information Settings to Rendering Extensions](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md) </span></span>  
 <span data-ttu-id="62379-117">[在 RSReportServer.Config中自定义呈现扩展插件参数](customize-rendering-extension-parameters-in-rsreportserver-config.md) </span><span class="sxs-lookup"><span data-stu-id="62379-117">[Customize Rendering Extension Parameters in RSReportServer.Config](customize-rendering-extension-parameters-in-rsreportserver-config.md) </span></span>  
 [<span data-ttu-id="62379-118">技术参考 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="62379-118">Technical Reference &#40;SSRS&#41;</span></span>](../../2014/reporting-services/technical-reference-ssrs.md)  
  
  
