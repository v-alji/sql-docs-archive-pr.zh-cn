---
title: 实现呈现扩展插件 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- rendering extensions [Reporting Services]
- custom rendering extensions [Reporting Services]
- transformations [Reporting Services]
- extensions [Reporting Services], rendering
- rendering extensions [Reporting Services], implementing
ms.assetid: 4a5c64f5-2391-4597-ba3f-81d265b23703
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 03deb7c818de8d875f69b585ae6015fc178e707d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587230"
---
# <a name="implementing-a-rendering-extension"></a><span data-ttu-id="b6332-102">实现呈现扩展插件</span><span class="sxs-lookup"><span data-stu-id="b6332-102">Implementing a Rendering Extension</span></span>
  <span data-ttu-id="b6332-103">呈现扩展插件是将报表数据和布局信息转换为设备特定格式的报表服务器的组件或模块。</span><span class="sxs-lookup"><span data-stu-id="b6332-103">A rendering extension is a component or module of a report server that transforms report data and layout information into a device-specific format.</span></span> <span data-ttu-id="b6332-104">SQL Server Reporting Services 包含六种呈现扩展插件：HTML、Excel、Word、CSV 或 Text、XML、Image 和 PDF。</span><span class="sxs-lookup"><span data-stu-id="b6332-104">SQL Server Reporting Services includes six rendering extensions: HTML, Excel, Word, CSV or Text, XML, Image, and PDF.</span></span> <span data-ttu-id="b6332-105">您可以创建其他呈现扩展插件以便以其他格式生成报表。</span><span class="sxs-lookup"><span data-stu-id="b6332-105">You can create additional rendering extensions to generate reports in other formats.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b6332-106">若要确定哪些呈现扩展插件可用，您可以在 RSReportServer.config 文件中查看已安装的扩展插件列表。</span><span class="sxs-lookup"><span data-stu-id="b6332-106">To determine which rendering extensions are available, you can view the list of installed extensions in the RSReportServer.config file.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b6332-107">本节内容</span><span class="sxs-lookup"><span data-stu-id="b6332-107">In This Section</span></span>  
 [<span data-ttu-id="b6332-108">呈现扩展插件概述</span><span class="sxs-lookup"><span data-stu-id="b6332-108">Rendering Extensions Overview</span></span>](rendering-extensions-overview.md)  
 <span data-ttu-id="b6332-109">介绍如何为 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 编写自定义呈现扩展插件。</span><span class="sxs-lookup"><span data-stu-id="b6332-109">Introduces how to write a custom rendering extension for [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="b6332-110">实现 IRenderingExtension 接口</span><span class="sxs-lookup"><span data-stu-id="b6332-110">Implementing the IRenderingExtension Interface</span></span>](implementing-the-irenderingextension-interface.md)  
 <span data-ttu-id="b6332-111">说明呈现扩展插件的属性。</span><span class="sxs-lookup"><span data-stu-id="b6332-111">Describes the attributes of a rendering extension.</span></span>  
  
 [<span data-ttu-id="b6332-112">部署呈现扩展插件</span><span class="sxs-lookup"><span data-stu-id="b6332-112">Deploying a Rendering Extension</span></span>](deploying-a-rendering-extension.md)  
 <span data-ttu-id="b6332-113">说明如何将呈现扩展插件部署到报表服务器。</span><span class="sxs-lookup"><span data-stu-id="b6332-113">Describes how to deploy a rendering extension on a report server.</span></span>  
  
 [<span data-ttu-id="b6332-114">删除呈现扩展插件</span><span class="sxs-lookup"><span data-stu-id="b6332-114">Removing a Rendering Extension</span></span>](removing-a-rendering-extension.md)  
 <span data-ttu-id="b6332-115">说明如何从报表服务器上删除呈现扩展插件。</span><span class="sxs-lookup"><span data-stu-id="b6332-115">Describes how to remove a rendering extension from a report server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6332-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b6332-116">See Also</span></span>  
 <span data-ttu-id="b6332-117">[Reporting Services 扩展插件](../reporting-services-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="b6332-117">[Reporting Services Extensions](../reporting-services-extensions.md) </span></span>  
 [<span data-ttu-id="b6332-118">Reporting Services 扩展插件库</span><span class="sxs-lookup"><span data-stu-id="b6332-118">Reporting Services Extension Library</span></span>](../reporting-services-extension-library.md)  
  
  
