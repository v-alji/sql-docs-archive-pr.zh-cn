---
title: 删除呈现扩展插件 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- deleting rendering extensions
- removing rendering extensions
- rendering extensions [Reporting Services], removing
ms.assetid: 2abfebfb-065f-45cc-a904-c914394cf900
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 77a8a9ac44b35f338f978913985617e4f264ddb7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587228"
---
# <a name="removing-a-rendering-extension"></a><span data-ttu-id="df743-102">删除呈现扩展插件</span><span class="sxs-lookup"><span data-stu-id="df743-102">Removing a Rendering Extension</span></span>
  <span data-ttu-id="df743-103">若要删除 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 呈现扩展插件，只需 `Extension` 从位于 **%ProgramFiles%\Microsoft SQL Server \ MSRS10_50 的 rsreportserver.config 文件中删除呈现扩展插件的元素。 \<Instance Name>\Reporting Services\ReportServer**文件夹。</span><span class="sxs-lookup"><span data-stu-id="df743-103">To remove a [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] rendering extension, simply remove the `Extension` element for your rendering extension from the rsreportserver.config file, located in **%ProgramFiles%\Microsoft SQL Server\MSRS10_50.\<Instance Name>\Reporting Services\ReportServer** folder.</span></span> <span data-ttu-id="df743-104">如果为报表设计器和 Report Server 生成了条目，则 `Extension` 也从[Rsreportdesigner.config 配置文件](../../report-server/rsreportdesigner-configuration-file.md)中删除该元素。</span><span class="sxs-lookup"><span data-stu-id="df743-104">If you made entries for a Report Designer as well as a report server, remove the `Extension` element from the [RSReportDesigner Configuration File](../../report-server/rsreportdesigner-configuration-file.md) as well.</span></span> <span data-ttu-id="df743-105">在删除配置信息之后，该呈现扩展插件对于该组件将不再可用。</span><span class="sxs-lookup"><span data-stu-id="df743-105">After the configuration information is removed, the rendering extension is no longer available to the component.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df743-106">另请参阅</span><span class="sxs-lookup"><span data-stu-id="df743-106">See Also</span></span>  
 <span data-ttu-id="df743-107">[Reporting Services 配置文件](../../report-server/reporting-services-configuration-files.md) </span><span class="sxs-lookup"><span data-stu-id="df743-107">[Reporting Services Configuration Files](../../report-server/reporting-services-configuration-files.md) </span></span>  
 <span data-ttu-id="df743-108">[实现呈现扩展插件](implementing-a-rendering-extension.md) </span><span class="sxs-lookup"><span data-stu-id="df743-108">[Implementing a Rendering Extension](implementing-a-rendering-extension.md) </span></span>  
 <span data-ttu-id="df743-109">[呈现扩展插件概述](rendering-extensions-overview.md) </span><span class="sxs-lookup"><span data-stu-id="df743-109">[Rendering Extensions Overview](rendering-extensions-overview.md) </span></span>  
 <span data-ttu-id="df743-110">[实现 IRenderingExtension 接口](implementing-the-irenderingextension-interface.md) </span><span class="sxs-lookup"><span data-stu-id="df743-110">[Implementing the IRenderingExtension Interface](implementing-the-irenderingextension-interface.md) </span></span>  
 <span data-ttu-id="df743-111">[扩展插件的安全注意事项](../security-considerations-for-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="df743-111">[Security Considerations for Extensions](../security-considerations-for-extensions.md) </span></span>  
 [<span data-ttu-id="df743-112">部署呈现扩展插件</span><span class="sxs-lookup"><span data-stu-id="df743-112">Deploying a Rendering Extension</span></span>](deploying-a-rendering-extension.md)  
  
  
