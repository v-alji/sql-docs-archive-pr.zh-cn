---
title: Reporting Services WMI 提供程序库引用 (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- Reporting Services WMI Provider Library
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- WMI provider [Reporting Services], library
ms.assetid: 17ba711d-7eff-4423-9168-63dc425a3428
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2a98ca22f9d34627e484a698dcf540b31808d07e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581084"
---
# <a name="reporting-services-wmi-provider-library-reference-ssrs"></a><span data-ttu-id="6c09e-102">Reporting Services WMI 提供程序库引用 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="6c09e-102">Reporting Services WMI Provider Library Reference (SSRS)</span></span>
  <span data-ttu-id="6c09e-103">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Windows Management Instrumentation (WMI) 提供程序支持 WMI 操作，使用这些操作能够编写脚本和代码以修改报表服务器和报表管理器的设置。</span><span class="sxs-lookup"><span data-stu-id="6c09e-103">The [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Windows Management Instrumentation (WMI) provider supports WMI operations that enable you to write scripts and code to modify settings of the report server and Report Manager.</span></span>  
  
 <span data-ttu-id="6c09e-104">例如，在报表服务器连接到报表服务器数据库时，如果想更改是否使用集成安全性，则可以创建一个 MSReportServer_ConfigurationSetting 类的实例，并使用该报表服务器实例的 DatabaseIntegratedSecurity 属性。</span><span class="sxs-lookup"><span data-stu-id="6c09e-104">For example, if you want to change whether integrated security is used when the report server connects to the report server database, create an instance of the MSReportServer_ConfigurationSetting class and use the DatabaseIntegratedSecurity property of the of the report server instance.</span></span> <span data-ttu-id="6c09e-105">下表显示的类表示 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 组件。</span><span class="sxs-lookup"><span data-stu-id="6c09e-105">The classes shown in the following table represent [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] components.</span></span> <span data-ttu-id="6c09e-106">这些类在 [!INCLUDE[ssRSWMInmspc](../../includes/ssrswminmspc-md.md)] 或 [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)] 命名空间中进行定义。</span><span class="sxs-lookup"><span data-stu-id="6c09e-106">The classes are defined in either the [!INCLUDE[ssRSWMInmspc](../../includes/ssrswminmspc-md.md)] or the [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)] namespaces.</span></span> <span data-ttu-id="6c09e-107">每个类都支持读取和写入操作。</span><span class="sxs-lookup"><span data-stu-id="6c09e-107">Each of the classes support read and write operations.</span></span> <span data-ttu-id="6c09e-108">不支持创建操作。</span><span class="sxs-lookup"><span data-stu-id="6c09e-108">Create operations are not supported.</span></span>  
  
## <a name="classes"></a><span data-ttu-id="6c09e-109">类</span><span class="sxs-lookup"><span data-stu-id="6c09e-109">Classes</span></span>  
 [<span data-ttu-id="6c09e-110">MSReportServer_Instance 类</span><span class="sxs-lookup"><span data-stu-id="6c09e-110">MSReportServer_Instance Class</span></span>](msreportserver-instance-class.md)  
 <span data-ttu-id="6c09e-111">为客户端提供连接到已安装的报表服务器所需的基本信息。</span><span class="sxs-lookup"><span data-stu-id="6c09e-111">Provides basic information required for a client to connect to an installed report server.</span></span>  
  
 [<span data-ttu-id="6c09e-112">MSReportServer_ConfigurationSetting 类</span><span class="sxs-lookup"><span data-stu-id="6c09e-112">MSReportServer_ConfigurationSetting Class</span></span>](msreportserver-configurationsetting-class.md)  
 <span data-ttu-id="6c09e-113">表示报表服务器实例的安装和运行时参数。</span><span class="sxs-lookup"><span data-stu-id="6c09e-113">Represents the installation and run-time parameters of a report server instance.</span></span> <span data-ttu-id="6c09e-114">这些参数存储在报表服务器的配置文件中。</span><span class="sxs-lookup"><span data-stu-id="6c09e-114">These parameters are stored in the configuration file for the report server.</span></span>  
  
 <span data-ttu-id="6c09e-115">有关 WMI 操作的详细信息，请参阅 SDK 附带的 WMI SDK 文档 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="6c09e-115">For more information about WMI operations, see the WMI SDK documentation included with the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c09e-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6c09e-116">See Also</span></span>  
 <span data-ttu-id="6c09e-117">[访问 Reporting Services WMI 提供程序](../tools/access-the-reporting-services-wmi-provider.md) </span><span class="sxs-lookup"><span data-stu-id="6c09e-117">[Access the Reporting Services WMI Provider](../tools/access-the-reporting-services-wmi-provider.md) </span></span>  
 [<span data-ttu-id="6c09e-118">技术参考 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="6c09e-118">Technical Reference &#40;SSRS&#41;</span></span>](../technical-reference-ssrs.md)  
  
  
