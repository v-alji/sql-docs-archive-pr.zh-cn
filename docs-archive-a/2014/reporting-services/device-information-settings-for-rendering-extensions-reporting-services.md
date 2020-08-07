---
title: 呈现扩展插件的设备信息设置 (Reporting Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 947b0ee1-bb35-4b4e-9527-dc501566e7d1
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f15e27e01cd43bafda3aede3deca7729f2c89756
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691115"
---
# <a name="device-information-settings-for-rendering-extensions-reporting-services"></a><span data-ttu-id="c5128-102">呈现扩展插件的设备信息设置 (Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="c5128-102">Device Information Settings for Rendering Extensions (Reporting Services)</span></span>
  <span data-ttu-id="c5128-103">在 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]中，设备信息设置用于将呈现参数传递到呈现扩展插件。</span><span class="sxs-lookup"><span data-stu-id="c5128-103">In [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], device information settings are used to pass rendering parameters to a rendering extension.</span></span> <span data-ttu-id="c5128-104">每个呈现扩展插件接受一组特定设置。</span><span class="sxs-lookup"><span data-stu-id="c5128-104">Each rendering extension accepts a specific set of settings.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c5128-105">本节内容</span><span class="sxs-lookup"><span data-stu-id="c5128-105">In This Section</span></span>  
  
|<span data-ttu-id="c5128-106">主题</span><span class="sxs-lookup"><span data-stu-id="c5128-106">Topic</span></span>|<span data-ttu-id="c5128-107">说明</span><span class="sxs-lookup"><span data-stu-id="c5128-107">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="c5128-108">ATOM 设备信息设置</span><span class="sxs-lookup"><span data-stu-id="c5128-108">ATOM Device Information Settings</span></span>](../../2014/reporting-services/atom-device-information-settings.md)|<span data-ttu-id="c5128-109">介绍与 Atom 兼容的呈现输出相关的设备信息设置。</span><span class="sxs-lookup"><span data-stu-id="c5128-109">Describes the device information settings that are associated with Atom compliant rendering output.</span></span>|  
|[<span data-ttu-id="c5128-110">CSV 设备信息设置</span><span class="sxs-lookup"><span data-stu-id="c5128-110">CSV Device Information Settings</span></span>](csv-device-information-settings.md)|<span data-ttu-id="c5128-111">介绍与 CSV 呈现输出相关的设备信息设置。</span><span class="sxs-lookup"><span data-stu-id="c5128-111">Describes the device information settings that are associated with CSV rendering output.</span></span>|  
|[<span data-ttu-id="c5128-112">Excel 设备信息设置</span><span class="sxs-lookup"><span data-stu-id="c5128-112">Excel Device Information Settings</span></span>](excel-device-information-settings.md)|<span data-ttu-id="c5128-113">介绍与 Excel 呈现输出相关的设备信息设置。</span><span class="sxs-lookup"><span data-stu-id="c5128-113">Describes the device information settings that are associated with Excel rendering output.</span></span>|  
|[<span data-ttu-id="c5128-114">Word 设备信息设置</span><span class="sxs-lookup"><span data-stu-id="c5128-114">Word Device Information Settings</span></span>](word-device-information-settings.md)|<span data-ttu-id="c5128-115">介绍与 Word 呈现输出相关的设备信息设置。</span><span class="sxs-lookup"><span data-stu-id="c5128-115">Describes the device information settings that are associated with Word rendering output.</span></span>|  
|[<span data-ttu-id="c5128-116">HTML 设备信息设置</span><span class="sxs-lookup"><span data-stu-id="c5128-116">HTML Device Information Settings</span></span>](html-device-information-settings.md)|<span data-ttu-id="c5128-117">介绍与 HTML 呈现输出相关的设备信息设置。</span><span class="sxs-lookup"><span data-stu-id="c5128-117">Describes the device information settings that are associated with HTML rendering output.</span></span>|  
|[<span data-ttu-id="c5128-118">图像设备信息设置</span><span class="sxs-lookup"><span data-stu-id="c5128-118">Image Device Information Settings</span></span>](image-device-information-settings.md)|<span data-ttu-id="c5128-119">介绍与 IMAGE 呈现输出相关的设备信息设置。</span><span class="sxs-lookup"><span data-stu-id="c5128-119">Describes the device information settings that are associated with IMAGE rendering output.</span></span>|  
|[<span data-ttu-id="c5128-120">MHTML 设备信息设置</span><span class="sxs-lookup"><span data-stu-id="c5128-120">MHTML Device Information Settings</span></span>](mhtml-device-information-settings.md)|<span data-ttu-id="c5128-121">介绍与 MHTML 呈现输出相关的设备信息设置。</span><span class="sxs-lookup"><span data-stu-id="c5128-121">Describes the device information settings that are associated with MHTML rendering output.</span></span>|  
|[<span data-ttu-id="c5128-122">PDF 设备信息设置</span><span class="sxs-lookup"><span data-stu-id="c5128-122">PDF Device Information Settings</span></span>](pdf-device-information-settings.md)|<span data-ttu-id="c5128-123">介绍与 PDF 呈现输出相关的设备信息设置。</span><span class="sxs-lookup"><span data-stu-id="c5128-123">Describes the device information settings that are associated with PDF rendering output.</span></span>|  
|[<span data-ttu-id="c5128-124">XML 设备信息设置</span><span class="sxs-lookup"><span data-stu-id="c5128-124">XML Device Information Settings</span></span>](xml-device-information-settings.md)|<span data-ttu-id="c5128-125">介绍与 XML 呈现输出关联的设备信息设置。</span><span class="sxs-lookup"><span data-stu-id="c5128-125">Describes the device information settings that are associated with XML rendering output.</span></span>|  
|[<span data-ttu-id="c5128-126">RGDI 设备信息设置</span><span class="sxs-lookup"><span data-stu-id="c5128-126">RGDI Device Information Settings</span></span>](rgdi-device-information-settings.md)|<span data-ttu-id="c5128-127">介绍与 RGDI 呈现输出关联的设备信息设置。</span><span class="sxs-lookup"><span data-stu-id="c5128-127">Describes the device information settings that are associated with RGDI rendering output.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c5128-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c5128-128">See Also</span></span>  
 [<span data-ttu-id="c5128-129">在 RSReportServer.Config 中自定义呈现扩展插件参数</span><span class="sxs-lookup"><span data-stu-id="c5128-129">Customize Rendering Extension Parameters in RSReportServer.Config</span></span>](customize-rendering-extension-parameters-in-rsreportserver-config.md)  
  
  
