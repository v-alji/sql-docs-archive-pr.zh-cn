---
title: Word 设备信息设置 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Word [Reporting Services]
- device information settings [Reporting Services], Word
ms.assetid: 28146498-fae7-4b13-b47f-6ec05aa8e057
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ddd145c5073003a8dc189e3ed9b1bbb25dc11d09
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577250"
---
# <a name="word-device-information-settings"></a><span data-ttu-id="8f070-102">Word 设备信息设置</span><span class="sxs-lookup"><span data-stu-id="8f070-102">Word Device Information Settings</span></span>
  <span data-ttu-id="8f070-103">下表列出以 [!INCLUDE[ofprword](../includes/ofprword-md.md)] 格式呈现时的设备信息设置。</span><span class="sxs-lookup"><span data-stu-id="8f070-103">The following table lists the device information settings for rendering in [!INCLUDE[ofprword](../includes/ofprword-md.md)] format.</span></span>  
  
|<span data-ttu-id="8f070-104">设置</span><span class="sxs-lookup"><span data-stu-id="8f070-104">Setting</span></span>|<span data-ttu-id="8f070-105">值</span><span class="sxs-lookup"><span data-stu-id="8f070-105">Value</span></span>|  
|-------------|-----------|  
|`AutoFit`|<span data-ttu-id="8f070-106">`False`.</span><span class="sxs-lookup"><span data-stu-id="8f070-106">`False`.</span></span> <span data-ttu-id="8f070-107">自动调整对于任何 Word 表都设置为 `false`。</span><span class="sxs-lookup"><span data-stu-id="8f070-107">AutoFit is set to `false` set on any Word table.</span></span><br /><br /> <span data-ttu-id="8f070-108">`True`.</span><span class="sxs-lookup"><span data-stu-id="8f070-108">`True`.</span></span> <span data-ttu-id="8f070-109">自动调整对于每个 Word 表都设置为 `true`。</span><span class="sxs-lookup"><span data-stu-id="8f070-109">AutoFit is set to `true` on every Word table.</span></span><br /><br /> <span data-ttu-id="8f070-110">`Never`.</span><span class="sxs-lookup"><span data-stu-id="8f070-110">`Never`.</span></span> <span data-ttu-id="8f070-111">对任何 Word 表均未设置自动调整值并且行为还原为 Word 默认值。</span><span class="sxs-lookup"><span data-stu-id="8f070-111">AutoFit values are not set on any Word table and behavior reverts to the Word default.</span></span><br /><br /> <span data-ttu-id="8f070-112">`Default`.</span><span class="sxs-lookup"><span data-stu-id="8f070-112">`Default`.</span></span> <span data-ttu-id="8f070-113">自动调整设置于窄于每个逻辑页上物理绘图区（不包括边距的物理页宽）的表。</span><span class="sxs-lookup"><span data-stu-id="8f070-113">AutoFit is set on tables that are narrower than the physical drawing area (physical page width excluding margins) per logical page.</span></span>|  
|`ExpandToggles`|<span data-ttu-id="8f070-114">指示可以滚动的所有项是否以其完全展开的状态呈现。</span><span class="sxs-lookup"><span data-stu-id="8f070-114">Indicates whether all items that can be toggled should render in their fully-expanded state.</span></span> <span data-ttu-id="8f070-115">默认值为 `false`。</span><span class="sxs-lookup"><span data-stu-id="8f070-115">The default value is `false`.</span></span>|  
|`FixedPageWidth`|<span data-ttu-id="8f070-116">指示写入 DOC 文件的页宽是否将增大以适合表体中最大页的宽度。</span><span class="sxs-lookup"><span data-stu-id="8f070-116">Indicates whether the Page Width written to the DOC file will grow to accommodate the width of the largest page in the Report Body.</span></span> <span data-ttu-id="8f070-117">默认值为 `false`。</span><span class="sxs-lookup"><span data-stu-id="8f070-117">The default value is `false`.</span></span>|  
|<span data-ttu-id="8f070-118">**OmitHyperlinks**</span><span class="sxs-lookup"><span data-stu-id="8f070-118">**OmitHyperlinks**</span></span>|<span data-ttu-id="8f070-119">指示是否忽略对所有项的超链接操作（如果设置）。</span><span class="sxs-lookup"><span data-stu-id="8f070-119">Indicates whether to omit the Hyperlink action on all items where it is set.</span></span> <span data-ttu-id="8f070-120">默认值为 `false`</span><span class="sxs-lookup"><span data-stu-id="8f070-120">The default value is `false`</span></span>|  
|`OmitDrillthroughs`|<span data-ttu-id="8f070-121">指示是否忽略对所有项的钻取操作（如果设置）。</span><span class="sxs-lookup"><span data-stu-id="8f070-121">Indicates whether to omit the Drillthrough action on all items where it is set.</span></span> <span data-ttu-id="8f070-122">默认值为 `false`</span><span class="sxs-lookup"><span data-stu-id="8f070-122">The default value is `false`</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8f070-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8f070-123">See Also</span></span>  
 <span data-ttu-id="8f070-124">[将设备信息设置传递给呈现扩展插件](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="8f070-124">[Passing Device Information Settings to Rendering Extensions](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md) </span></span>  
 <span data-ttu-id="8f070-125">[在 RSReportServer.Config中自定义呈现扩展插件参数](customize-rendering-extension-parameters-in-rsreportserver-config.md) </span><span class="sxs-lookup"><span data-stu-id="8f070-125">[Customize Rendering Extension Parameters in RSReportServer.Config](customize-rendering-extension-parameters-in-rsreportserver-config.md) </span></span>  
 [<span data-ttu-id="8f070-126">技术参考 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="8f070-126">Technical Reference &#40;SSRS&#41;</span></span>](../../2014/reporting-services/technical-reference-ssrs.md)  
  
  
