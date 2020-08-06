---
title: 在 URL 中指定设备信息设置 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- device information settings [Reporting Services], URLs
- URL access [Reporting Services], device information settings
ms.assetid: cb7f7577-c6a8-4e6f-8e60-5ec0760f29c3
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 00cd1fdc3b5fbe129ae4d51b220a11bc48b4744c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691043"
---
# <a name="specify-device-information-settings-in-a-url"></a><span data-ttu-id="5ae4e-102">在 URL 中指定设备信息设置</span><span class="sxs-lookup"><span data-stu-id="5ae4e-102">Specify Device Information Settings in a URL</span></span>
  <span data-ttu-id="5ae4e-103">设备信息设置是传递给呈现扩展插件的参数。</span><span class="sxs-lookup"><span data-stu-id="5ae4e-103">Device information settings are parameters that are passed to a rendering extension.</span></span> <span data-ttu-id="5ae4e-104">如果您使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 报表服务器 Web 服务的方法呈现报表，则 `DeviceInfo` XML 元素将作为输入参数传递。</span><span class="sxs-lookup"><span data-stu-id="5ae4e-104">If you use the methods of the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Report Server Web service to render a report, a `DeviceInfo` XML element is passed as an input parameter.</span></span> <span data-ttu-id="5ae4e-105">`DeviceInfo` 元素的子元素特定于不同呈现扩展插件的设备信息设置。</span><span class="sxs-lookup"><span data-stu-id="5ae4e-105">Child elements of the `DeviceInfo` element are specific to the device information settings of different rendering extensions.</span></span> <span data-ttu-id="5ae4e-106">可以通过使用 *rc:tag=value* 参数字符串在 URL 中加入设备信息设置，其中 *tag* 是所访问的设备信息设置元素的名称。</span><span class="sxs-lookup"><span data-stu-id="5ae4e-106">You can include device information settings in a URL by using the *rc:tag=value* parameter string, where *tag* is the name of the device information settings element being accessed.</span></span> <span data-ttu-id="5ae4e-107">有关 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 中的设备信息设置的详细信息，请参阅[将设备信息设置传递给呈现扩展插件](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)。</span><span class="sxs-lookup"><span data-stu-id="5ae4e-107">For more information about device information settings in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], see [Passing Device Information Settings to Rendering Extensions](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5ae4e-108">示例</span><span class="sxs-lookup"><span data-stu-id="5ae4e-108">Example</span></span>  
 <span data-ttu-id="5ae4e-109">以下示例通过使用图像呈现扩展插件的 *OutputFormat* 设备信息设置，将指定报表的格式设置为 JPEG（添加了换行符以增强可读性）：</span><span class="sxs-lookup"><span data-stu-id="5ae4e-109">The following example sets the format of the specified report to JPEG by using the *OutputFormat* device information setting of the image rendering extension (the line breaks have been added for legibility):</span></span>  
  
```  
http://servername/reportserver?/SampleReports  
/Employee Sales Summary&EmployeeID=38&rs:  
Command=Render&rs:Format=IMAGE&rc:OutputFormat=JPEG  
```  
  
## <a name="see-also"></a><span data-ttu-id="5ae4e-110">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5ae4e-110">See Also</span></span>  
 <span data-ttu-id="5ae4e-111">[URL 访问 (SSRS)](url-access-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="5ae4e-111">[URL Access &#40;SSRS&#41;](url-access-ssrs.md) </span></span>  
 [<span data-ttu-id="5ae4e-112">URL 访问参数引用</span><span class="sxs-lookup"><span data-stu-id="5ae4e-112">URL Access Parameter Reference</span></span>](url-access-parameter-reference.md)  
  
  
