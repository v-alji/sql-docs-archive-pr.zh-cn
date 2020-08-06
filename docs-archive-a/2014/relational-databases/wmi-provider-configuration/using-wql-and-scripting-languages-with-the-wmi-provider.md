---
title: 通过用于配置管理的 WMI 提供程序使用 WQL 和脚本语言 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
helpviewer_keywords:
- queries [WMI]
- scripts [WMI]
- query language [WMI]
- WMI Query Language [WMI]
- WQL [WMI]
- WMI Provider for Configuration Management, WQL
- WMI Provider for Configuration Management, scripts
ms.assetid: c1e64905-3c2b-4974-88f4-abf17cf7e289
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: d8c903cd0e993728865bce3371c349a2d0ba7485
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586539"
---
# <a name="using-wql-and-scripting-languages-with-the-wmi-provider-for-configuration-management"></a><span data-ttu-id="2fa83-102">将 WQL 和脚本语言用于配置管理的 WMI 提供程序</span><span class="sxs-lookup"><span data-stu-id="2fa83-102">Using WQL and Scripting Languages with the WMI Provider for Configuration Management</span></span>
  <span data-ttu-id="2fa83-103">管理应用程序以两种方式使用针对配置管理对象的 Windows Management Instrumentation (WMI) 提供程序访问 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务和网络设置：</span><span class="sxs-lookup"><span data-stu-id="2fa83-103">Management applications access [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services and network settings using the Windows Management Instrumentation (WMI) Provider for Configuration Management objects in two ways:</span></span>  
  
-   <span data-ttu-id="2fa83-104">使用某一 WQL 编辑器或查询工具（例如 WBEMTest.exe）可以查询通过 Windows Management Instrumentation 语言 (WQL) 设置的对象。</span><span class="sxs-lookup"><span data-stu-id="2fa83-104">Using a WQL editor or query tool, such as WBEMTest.exe to query the object set with the Windows Management Instrumentation Language (WQL).</span></span>  
  
-   <span data-ttu-id="2fa83-105">使用某一脚本语言，例如 VBScript。</span><span class="sxs-lookup"><span data-stu-id="2fa83-105">Using a scripting language, such as VBScript.</span></span>  
  
 <span data-ttu-id="2fa83-106">或者，可以使用 SMO 中的 WMI 托管对象以编程方式管理 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务和网络设置。</span><span class="sxs-lookup"><span data-stu-id="2fa83-106">Alternatively, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services and network settings can be managed programmatically using the WMI managed objects in SMO.</span></span> <span data-ttu-id="2fa83-107">有关 WMI 托管对象编程的详细信息，请参阅[使用 Wmi 提供程序管理服务和网络设置](../server-management-objects-smo/tasks/managing-services-and-network-settings-by-using-wmi-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="2fa83-107">For more information about programming WMI managed objects, see [Managing Services and Network Settings by Using WMI Provider](../server-management-objects-smo/tasks/managing-services-and-network-settings-by-using-wmi-provider.md).</span></span>  
  
 <span data-ttu-id="2fa83-108">可通过使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置管理器和 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 管理控制台访问用于配置管理的 WMI 提供程序。</span><span class="sxs-lookup"><span data-stu-id="2fa83-108">The WMI provider for Configuration Management can be accessed by using the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager and [!INCLUDE[msCoName](../../includes/msconame-md.md)] Management Console.</span></span> <span data-ttu-id="2fa83-109">有关从用户界面访问 WMI 提供程序的详细信息，请参阅[管理服务操作指南主题 &#40;SQL Server 配置管理器&#41;](../../database-engine/managing-services-how-to-topics-sql-server-configuration-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="2fa83-109">For more information about accessing the WMI provider from a user interface, see [Managing Services How-to Topics &#40;SQL Server Configuration Manager&#41;](../../database-engine/managing-services-how-to-topics-sql-server-configuration-manager.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2fa83-110">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2fa83-110">See Also</span></span>  
 <span data-ttu-id="2fa83-111">[使用 WQL 访问用于配置管理的 WMI 提供程序](access-wmi-provider-for-configuration-management-using-wql.md) </span><span class="sxs-lookup"><span data-stu-id="2fa83-111">[Access WMI Provider for Configuration Management using WQL](access-wmi-provider-for-configuration-management-using-wql.md) </span></span>  
 [<span data-ttu-id="2fa83-112">使用 VBScript 修改 SQL Server 服务高级属性</span><span class="sxs-lookup"><span data-stu-id="2fa83-112">Modify SQL Server Service Advanced Properties using VBScript</span></span>](access-wmi-provider-for-configuration-management-using-vbscript.md)  
  
  
