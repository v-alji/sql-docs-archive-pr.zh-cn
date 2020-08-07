---
title: MHTML 设备信息设置 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- device information settings [Reporting Services], MHTML rendering
- MHTML [Reporting Services]
ms.assetid: 60b85dd8-b4fb-4ad9-be6a-e7c89ac076fe
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 076a0179871775984799fc8ce5366a220f812867
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588943"
---
# <a name="mhtml-device-information-settings"></a><span data-ttu-id="88fc7-102">MHTML 设备信息设置</span><span class="sxs-lookup"><span data-stu-id="88fc7-102">MHTML Device Information Settings</span></span>
  <span data-ttu-id="88fc7-103">下表列出的是以 Web 存档 (MHTML) 格式呈现报表时的设备信息设置。</span><span class="sxs-lookup"><span data-stu-id="88fc7-103">The following table lists the device information settings for rendering reports in Web archive (MHTML) format.</span></span>  
  
|<span data-ttu-id="88fc7-104">设置</span><span class="sxs-lookup"><span data-stu-id="88fc7-104">Setting</span></span>|<span data-ttu-id="88fc7-105">值</span><span class="sxs-lookup"><span data-stu-id="88fc7-105">Value</span></span>|  
|-------------|-----------|  
|<span data-ttu-id="88fc7-106">**JavaScript**</span><span class="sxs-lookup"><span data-stu-id="88fc7-106">**JavaScript**</span></span>|<span data-ttu-id="88fc7-107">指示是否在所呈现报表中支持 JavaScript。</span><span class="sxs-lookup"><span data-stu-id="88fc7-107">Indicates whether JavaScript is supported in the rendered report.</span></span>|  
|<span data-ttu-id="88fc7-108">**OutlookCompat**</span><span class="sxs-lookup"><span data-stu-id="88fc7-108">**OutlookCompat**</span></span>|<span data-ttu-id="88fc7-109">指示是否呈现可改善报表在 Outlook 中的外观的额外元数据。</span><span class="sxs-lookup"><span data-stu-id="88fc7-109">Indicates whether to render with extra metadata that makes the report look better in Outlook.</span></span> <span data-ttu-id="88fc7-110">默认值为 `true`。</span><span class="sxs-lookup"><span data-stu-id="88fc7-110">The default value is `true`.</span></span>|  
|<span data-ttu-id="88fc7-111">**MHTML 片段**</span><span class="sxs-lookup"><span data-stu-id="88fc7-111">**MHTML Fragment**</span></span>|<span data-ttu-id="88fc7-112">指示是否创建一个 MHTML 片段以取代完整 MHTML 文档。</span><span class="sxs-lookup"><span data-stu-id="88fc7-112">Indicates whether an MHTML fragment is created in place of a full MHTML document.</span></span> <span data-ttu-id="88fc7-113">MHTML 片段包含 TABLE 元素中的报表内容，并忽略 HTML 和 BODY 元素。</span><span class="sxs-lookup"><span data-stu-id="88fc7-113">An MHTML fragment includes the report content in a TABLE element and omits the HTML and BODY elements.</span></span> <span data-ttu-id="88fc7-114">默认值为 `false`。</span><span class="sxs-lookup"><span data-stu-id="88fc7-114">The default value is `false`.</span></span>|  
|<span data-ttu-id="88fc7-115">**DataVisualizationFitSizing**</span><span class="sxs-lookup"><span data-stu-id="88fc7-115">**DataVisualizationFitSizing**</span></span>|<span data-ttu-id="88fc7-116">指示 tablix 内数据可视化调整大小行为。</span><span class="sxs-lookup"><span data-stu-id="88fc7-116">Indicates data visualization fit behavior when inside a tablix.</span></span> <span data-ttu-id="88fc7-117">这包括图表、仪表和地图。</span><span class="sxs-lookup"><span data-stu-id="88fc7-117">This includes chart, gauge, and map.</span></span><br /><br /> <span data-ttu-id="88fc7-118">可能的值包括 **“近似”** 和 **“精确”** 。</span><span class="sxs-lookup"><span data-stu-id="88fc7-118">The possible values are **Approximate** and **Exact**.</span></span><br /><br /> <span data-ttu-id="88fc7-119">默认值为 **“近似”** 。</span><span class="sxs-lookup"><span data-stu-id="88fc7-119">The default value is **Approximate**.</span></span> <span data-ttu-id="88fc7-120">如果从 **rsreportserver.config** 文件删除该设置，则默认行为为 **“精确”** 。</span><span class="sxs-lookup"><span data-stu-id="88fc7-120">If the setting is removed from the **rsreportserver.config** file then the default behavior is **Exact**.</span></span><br /><br /> <span data-ttu-id="88fc7-121">启用 **“精确”** 可能会影响性能，因为确定精确大小所需的处理时间可能更长。</span><span class="sxs-lookup"><span data-stu-id="88fc7-121">Enabling **Exact** may have performance impact because the processing to determine the exact size may take longer.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="88fc7-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="88fc7-122">See Also</span></span>  
 <xref:ReportExecution2005.ReportExecutionService.Render%2A>   
 <span data-ttu-id="88fc7-123">[将设备信息设置传递给呈现扩展插件](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="88fc7-123">[Passing Device Information Settings to Rendering Extensions](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md) </span></span>  
 <span data-ttu-id="88fc7-124">[在 RSReportServer.Config 中自定义呈现扩展插件参数](customize-rendering-extension-parameters-in-rsreportserver-config.md) </span><span class="sxs-lookup"><span data-stu-id="88fc7-124">[Customize Rendering Extension Parameters in RSReportServer.Config](customize-rendering-extension-parameters-in-rsreportserver-config.md) </span></span>  
 [<span data-ttu-id="88fc7-125">技术参考 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="88fc7-125">Technical Reference &#40;SSRS&#41;</span></span>](../../2014/reporting-services/technical-reference-ssrs.md)  
  
  
