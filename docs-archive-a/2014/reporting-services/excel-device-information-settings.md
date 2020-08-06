---
title: Excel 设备信息设置 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- device information settings [Reporting Services], Excel rendering
- Excel [Reporting Services], rendering
ms.assetid: bb5f3566-f033-4470-be87-1f52fb7a4ab6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d71c83195c8f91984bbbce95bd00402928fdb36e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691099"
---
# <a name="excel-device-information-settings"></a><span data-ttu-id="b3cdc-102">Excel 设备信息设置</span><span class="sxs-lookup"><span data-stu-id="b3cdc-102">Excel Device Information Settings</span></span>
  <span data-ttu-id="b3cdc-103">下表列出以 [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] 格式呈现时的设备信息设置。</span><span class="sxs-lookup"><span data-stu-id="b3cdc-103">The following table lists the device information settings for rendering in [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] format.</span></span>  
  
|<span data-ttu-id="b3cdc-104">设置</span><span class="sxs-lookup"><span data-stu-id="b3cdc-104">Setting</span></span>|<span data-ttu-id="b3cdc-105">值</span><span class="sxs-lookup"><span data-stu-id="b3cdc-105">Value</span></span>|  
|-------------|-----------|  
|<span data-ttu-id="b3cdc-106">**OmitDocumentMap**</span><span class="sxs-lookup"><span data-stu-id="b3cdc-106">**OmitDocumentMap**</span></span>|<span data-ttu-id="b3cdc-107">指示是否对于支持文档结构图的报表忽略文档结构图。</span><span class="sxs-lookup"><span data-stu-id="b3cdc-107">Indicates whether to omit the document map for reports that support it.</span></span> <span data-ttu-id="b3cdc-108">默认值为 `false`。</span><span class="sxs-lookup"><span data-stu-id="b3cdc-108">The default value is `false`.</span></span>|  
|<span data-ttu-id="b3cdc-109">**OmitFormulas**</span><span class="sxs-lookup"><span data-stu-id="b3cdc-109">**OmitFormulas**</span></span>|<span data-ttu-id="b3cdc-110">指示是否对所呈现报表忽略公式。</span><span class="sxs-lookup"><span data-stu-id="b3cdc-110">Indicates whether to omit formulas from the rendered report.</span></span> <span data-ttu-id="b3cdc-111">默认值为 `false`。</span><span class="sxs-lookup"><span data-stu-id="b3cdc-111">The default value is `false`.</span></span>|  
|<span data-ttu-id="b3cdc-112">`SimplePageHeade`rs</span><span class="sxs-lookup"><span data-stu-id="b3cdc-112">`SimplePageHeade`rs</span></span>|<span data-ttu-id="b3cdc-113">指示是否将报表的页眉呈现到 Excel 页眉。</span><span class="sxs-lookup"><span data-stu-id="b3cdc-113">Indicates whether the page header of the report is rendered to the Excel page header.</span></span> <span data-ttu-id="b3cdc-114">值为 `false` 指示将页眉呈现到工作表的第一行。</span><span class="sxs-lookup"><span data-stu-id="b3cdc-114">A value of `false` indicates that the page header is rendered to the first row of the worksheet.</span></span> <span data-ttu-id="b3cdc-115">默认值是 `false`。</span><span class="sxs-lookup"><span data-stu-id="b3cdc-115">The default value is `false`.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b3cdc-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b3cdc-116">See Also</span></span>  
 <xref:ReportExecution2005.ReportExecutionService.Render%2A>   
 <span data-ttu-id="b3cdc-117">[将设备信息设置传递给呈现扩展插件](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="b3cdc-117">[Passing Device Information Settings to Rendering Extensions](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md) </span></span>  
 <span data-ttu-id="b3cdc-118">[在 RSReportServer.Config中自定义呈现扩展插件参数](customize-rendering-extension-parameters-in-rsreportserver-config.md) </span><span class="sxs-lookup"><span data-stu-id="b3cdc-118">[Customize Rendering Extension Parameters in RSReportServer.Config](customize-rendering-extension-parameters-in-rsreportserver-config.md) </span></span>  
 [<span data-ttu-id="b3cdc-119">技术参考 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="b3cdc-119">Technical Reference &#40;SSRS&#41;</span></span>](../../2014/reporting-services/technical-reference-ssrs.md)  
  
  
