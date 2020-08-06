---
title: 脚本编写和带 Reporting Services 的 PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- scripts [Reporting Services]
- Reporting Services, scripting
- scripting [Reporting Services]
ms.assetid: 1ac2646d-ed5a-4436-b18f-2150c33f3d87
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a7a8dc805351897c11202467ed8bcb0373ef77c6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587715"
---
# <a name="scripting-and-powershell-with-reporting-services"></a><span data-ttu-id="9c6f0-102">脚本编写和带 Reporting Services 的 PowerShell</span><span class="sxs-lookup"><span data-stu-id="9c6f0-102">Scripting and PowerShell with Reporting Services</span></span>
  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] <span data-ttu-id="9c6f0-103">支持广泛的开发和管理方案（通过脚本进行），包括 rs.exe 命令行实用工具、适用于 SharePoint 模式报告服务器的 PowerShell cmdlet 以及利用 PowerShell 中的 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 对象模式实现本机模式和 SharePoint 模式。</span><span class="sxs-lookup"><span data-stu-id="9c6f0-103">supports a wide range of development and management scenarios through script, including the rs.exe command line utility, PowerShell cmdlets for SharePoint mode report servers, and leveraging the [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] object model from PowerShell for both Native and SharePoint mode.</span></span>

-   <span data-ttu-id="9c6f0-104">管理员可以用 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] 编写脚本来自动部署和管理报表服务器安装。</span><span class="sxs-lookup"><span data-stu-id="9c6f0-104">Administrators can write script in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] to automate how they deploy and manage a report server installation.</span></span> <span data-ttu-id="9c6f0-105">可以生成和运行 [!INCLUDE[tsql](../../includes/tsql-md.md)] 脚本来创建、配置和更新报表服务器数据库，</span><span class="sxs-lookup"><span data-stu-id="9c6f0-105">Administrators can also generate and run [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts that create, configure, and update a report server database.</span></span> <span data-ttu-id="9c6f0-106">管理员还可以使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 中的记录和播放脚本功能来自动执行日常维护任务。</span><span class="sxs-lookup"><span data-stu-id="9c6f0-106">Administrators can also use the record and playback script features in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] to automate routine maintenance tasks.</span></span>

-   <span data-ttu-id="9c6f0-107">开发人员可以创建包括脚本的自定义应用程序。</span><span class="sxs-lookup"><span data-stu-id="9c6f0-107">Developers can create custom applications that include script.</span></span> <span data-ttu-id="9c6f0-108">您可以运行调用 Report Server Web 服务的脚本。</span><span class="sxs-lookup"><span data-stu-id="9c6f0-108">You can run script that makes calls to the Report Server Web service.</span></span> <span data-ttu-id="9c6f0-109">几乎所有可以用托管代码编写的操作都可以用脚本编写。</span><span class="sxs-lookup"><span data-stu-id="9c6f0-109">Almost any operation that you can write in managed code can also be written in script.</span></span>

-   [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] <span data-ttu-id="9c6f0-110">支持 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] .NET 脚本作为可通过 RS.exe 实用工具（在报表服务器上运行的脚本主机）处理的脚本语言。</span><span class="sxs-lookup"><span data-stu-id="9c6f0-110">supports [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] .NET script as the script language that can be processed by the RS.exe utility, a script host that runs on the report server.</span></span>

## <a name="reporting-services-sharepoint-mode-powershell-cmdlets-and-samples"></a><span data-ttu-id="9c6f0-111">Reporting Services SharePoint 模式 PowerShell cmdlet 和示例</span><span class="sxs-lookup"><span data-stu-id="9c6f0-111">Reporting Services SharePoint mode PowerShell cmdlets and samples</span></span>
 <span data-ttu-id="9c6f0-112">![PowerShell 相关内容](../media/rs-powershellicon.jpg "PowerShell 相关内容")</span><span class="sxs-lookup"><span data-stu-id="9c6f0-112">![PowerShell related content](../media/rs-powershellicon.jpg "PowerShell related content")</span></span>

 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] <span data-ttu-id="9c6f0-113">SharePoint 模式包括用于报表服务器管理的 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] cmdlet。</span><span class="sxs-lookup"><span data-stu-id="9c6f0-113">SharePoint mode includes [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] cmdlets for report server administration.</span></span>

-   <span data-ttu-id="9c6f0-114">[PowerShell cmdlets for Reporting Services SharePoint Mode](../powershell-cmdlets-for-reporting-services-sharepoint-mode.md) 包括以下示例：</span><span class="sxs-lookup"><span data-stu-id="9c6f0-114">[PowerShell cmdlets for Reporting Services SharePoint Mode](../powershell-cmdlets-for-reporting-services-sharepoint-mode.md) Includes the following examples:</span></span>

    -   <span data-ttu-id="9c6f0-115">创建服务应用程序和代理</span><span class="sxs-lookup"><span data-stu-id="9c6f0-115">Create a service application and proxy</span></span>

    -   <span data-ttu-id="9c6f0-116">查看和更新传递扩展插件</span><span class="sxs-lookup"><span data-stu-id="9c6f0-116">Review and update a delivery extension</span></span>

    -   <span data-ttu-id="9c6f0-117">获取和设置 Reporting Service 应用程序数据库的属性，例如数据库超时</span><span class="sxs-lookup"><span data-stu-id="9c6f0-117">Get and set Properties of the Reporting Service Application Database, for example database timeout</span></span>

    -   <span data-ttu-id="9c6f0-118">列表数据扩展插件</span><span class="sxs-lookup"><span data-stu-id="9c6f0-118">List Data Extensions</span></span>

## <a name="reporting-services-object-model-and-powershell-samples"></a><span data-ttu-id="9c6f0-119">Reporting Service 对象模型和 Powershell 示例</span><span class="sxs-lookup"><span data-stu-id="9c6f0-119">Reporting Services Object model and Powershell samples</span></span>
 <span data-ttu-id="9c6f0-120">![PowerShell 相关内容](../media/rs-powershellicon.jpg "PowerShell 相关内容")</span><span class="sxs-lookup"><span data-stu-id="9c6f0-120">![PowerShell related content](../media/rs-powershellicon.jpg "PowerShell related content")</span></span>

 <span data-ttu-id="9c6f0-121">PowerShell 调用核心对象模型，对于 SharePoint 模式和本机模式大部分有效，例如迁移工作、订阅工作以及 SQL15 中的订阅工作的更多相关示例。</span><span class="sxs-lookup"><span data-stu-id="9c6f0-121">PowerShell calling the core object model and for the most part valid for SharePoint and native mode, for example the migration work, subscription work, and more related samples for subscriptions work in SQL15.</span></span>

-   <span data-ttu-id="9c6f0-122">[使用 PowerShell 更改和列出 Reporting Services 订阅所有者并运行订阅](../subscriptions/manage-subscription-owners-and-run-subscription-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="9c6f0-122">[Use PowerShell to Change and List Reporting Services Subscription Owners and Run a Subscription](../subscriptions/manage-subscription-owners-and-run-subscription-powershell.md).</span></span>

-   <span data-ttu-id="9c6f0-123">[使用 PowerShell 来创建带有本机模式报表服务器的 Azure VM](https://msdn.microsoft.com/library/azure/dn449661.aspx)。</span><span class="sxs-lookup"><span data-stu-id="9c6f0-123">[Use PowerShell to Create an Azure VM With a Native Mode Report Server](https://msdn.microsoft.com/library/azure/dn449661.aspx).</span></span>

-   <span data-ttu-id="9c6f0-124">请参阅[访问 Reporting Services WMI 提供程序](access-the-reporting-services-wmi-provider.md)中的“使用 PowerShell 访问 WMI 类”一节。</span><span class="sxs-lookup"><span data-stu-id="9c6f0-124">See the section "Access the WMI classes using PowerShell" in [Access the Reporting Services WMI Provider](access-the-reporting-services-wmi-provider.md).</span></span>

-   <span data-ttu-id="9c6f0-125">[如何使用 PowerShell 管理 SSRS](https://www.sqlshack.com/how-to-administer-sql-server-reporting-services-ssrs-subscriptions-using-powershell/).scriptin</span><span class="sxs-lookup"><span data-stu-id="9c6f0-125">[How to Administer SSRS using PowerShell](https://www.sqlshack.com/how-to-administer-sql-server-reporting-services-ssrs-subscriptions-using-powershell/).scriptin</span></span>

## <a name="rsexe-scripting-samples"></a><span data-ttu-id="9c6f0-126">RS.exe 脚本示例</span><span class="sxs-lookup"><span data-stu-id="9c6f0-126">RS.exe scripting samples</span></span>

-   <span data-ttu-id="9c6f0-127">[用于在报表服务器之间迁移内容的示例 Reporting Services rs.exe 脚本](sample-reporting-services-rs-exe-script-to-copy-content-between-report-servers.md)。</span><span class="sxs-lookup"><span data-stu-id="9c6f0-127">[Sample Reporting Services rs.exe Script to Migrate Content between Report Servers](sample-reporting-services-rs-exe-script-to-copy-content-between-report-servers.md).</span></span>

-   <span data-ttu-id="9c6f0-128">有关其他脚本、应用程序和扩展插件的示例，请参阅 [SQL Server Reporting Service 产品示例](https://go.microsoft.com/fwlink/?LinkId=177889)。</span><span class="sxs-lookup"><span data-stu-id="9c6f0-128">For additional script, application, and extension examples, see [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889).</span></span>

## <a name="see-also"></a><span data-ttu-id="9c6f0-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9c6f0-129">See Also</span></span>
 <span data-ttu-id="9c6f0-130">[RS.exe 实用工具 &#40;SSRS&#41;](rs-exe-utility-ssrs.md) [用 rs.exe 实用工具和 Web 服务](script-with-the-rs-exe-utility-and-the-web-service.md)[编写部署和管理任务](script-deployment-and-administrative-tasks.md)脚本</span><span class="sxs-lookup"><span data-stu-id="9c6f0-130">[RS.exe Utility &#40;SSRS&#41;](rs-exe-utility-ssrs.md) [Script Deployment and Administrative Tasks](script-deployment-and-administrative-tasks.md) [Script with the rs.exe Utility and the Web Service](script-with-the-rs-exe-utility-and-the-web-service.md)</span></span>


