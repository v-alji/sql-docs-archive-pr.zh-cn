---
title: 用于配置管理的 WMI 提供程序概念 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
helpviewer_keywords:
- WMI Provider for Configuration Management
- SQL Server WMI Provider
- configuration management [WMI]
- WMI Provider for Configuration Management, about WMI Provider for Configuration Management
ms.assetid: 7e41db24-b915-4eb8-a1d6-e6948ee915b7
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: be0682e7d6de5cb8c3d67a2f300bb89122213652
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580065"
---
# <a name="wmi-provider-for-configuration-management-concepts"></a><span data-ttu-id="5ab57-102">用于配置管理的 WMI 提供程序的概念</span><span class="sxs-lookup"><span data-stu-id="5ab57-102">WMI Provider for Configuration Management Concepts</span></span>
  <span data-ttu-id="5ab57-103">WMI 提供程序是一个已发布层，与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[msCoName](../../includes/msconame-md.md)] 管理控制台 (MMC) 和 Configuration Manager 的 Configuration Manager 管理单元一起使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="5ab57-103">The WMI provider is a published layer that is used with the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager snap-in for [!INCLUDE[msCoName](../../includes/msconame-md.md)] Management Console (MMC) and the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.</span></span> <span data-ttu-id="5ab57-104">它提供了一种统一的方式，用于与管理 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置管理器所请求注册表操作的 API 调用进行连接，并可对选定的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务提供增强的控制和操作。</span><span class="sxs-lookup"><span data-stu-id="5ab57-104">It provides a unified way for interfacing with the API calls that manage the registry operations requested by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager and provides enhanced control and manipulation over the selected [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services.</span></span>  
  
 <span data-ttu-id="5ab57-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] WMI 提供程序是一个 DLL 和一个 MOF 文件，这些文件由 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装程序自动编译。</span><span class="sxs-lookup"><span data-stu-id="5ab57-105">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] WMI Provider is a DLL and a MOF file, which are compiled automatically by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup.</span></span>  
  
 <span data-ttu-id="5ab57-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]WMI 提供程序包含一组对象类，这些类用于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 通过以下方法控制服务：</span><span class="sxs-lookup"><span data-stu-id="5ab57-106">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] WMI Provider contains a set of object classes used to control the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services using the following methods:</span></span>  
  
-   <span data-ttu-id="5ab57-107">可以在其中嵌入 Windows 查询语言 (WQL) 的脚本语言，如 VBScript、[!INCLUDE[jsprjscript](../../includes/jsprjscript-md.md)] 或 Perl。</span><span class="sxs-lookup"><span data-stu-id="5ab57-107">A script language such as VBScript, [!INCLUDE[jsprjscript](../../includes/jsprjscript-md.md)], or Perl, in which Windows Query Language (WQL) can be embedded.</span></span>  
  
-   <span data-ttu-id="5ab57-108">SMO 托管代码程序中的 <xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer> 对象。</span><span class="sxs-lookup"><span data-stu-id="5ab57-108">The <xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer> object in an SMO managed code program.</span></span>  
  
-   <span data-ttu-id="5ab57-109">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置管理器或带有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] WMI 提供程序管理单元的 MMC。</span><span class="sxs-lookup"><span data-stu-id="5ab57-109">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager or MMC with the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] WMI provider snap-in.</span></span>  
  
## <a name="using-a-script-language"></a><span data-ttu-id="5ab57-110">使用脚本语言</span><span class="sxs-lookup"><span data-stu-id="5ab57-110">Using a Script Language</span></span>  
 <span data-ttu-id="5ab57-111">使用脚本语言具有以下优点：</span><span class="sxs-lookup"><span data-stu-id="5ab57-111">The advantages of using a script language include the following:</span></span>  
  
-   <span data-ttu-id="5ab57-112">无需开发环境。</span><span class="sxs-lookup"><span data-stu-id="5ab57-112">A development environment is not required.</span></span>  
  
-   <span data-ttu-id="5ab57-113">支持脚本语言的文件可以广泛地使用。</span><span class="sxs-lookup"><span data-stu-id="5ab57-113">The files that support the script language are widely available.</span></span>  
  
 <span data-ttu-id="5ab57-114">除了 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] WMI 提供程序之外，脚本还可以与其他 WMI 提供程序配合使用。</span><span class="sxs-lookup"><span data-stu-id="5ab57-114">The script can also work with other WMI Providers in addition to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] WMI Provider.</span></span> <span data-ttu-id="5ab57-115">域管理员可以使用脚本在网络中的多台计算机上设置服务、网络设置和别名设置。</span><span class="sxs-lookup"><span data-stu-id="5ab57-115">A domain administrator can use a script to set up the services, network settings, and alias settings on multiple computers on a network.</span></span>  
  
 <span data-ttu-id="5ab57-116">本节将更为细致地介绍如何通过脚本访问用于配置管理的 WMI 提供程序。</span><span class="sxs-lookup"><span data-stu-id="5ab57-116">This section deals with accessing the WMI Provider for Configuration Management from scripts in further detail.</span></span>  
  
## <a name="using-the-smo-managedcomputer-object"></a><span data-ttu-id="5ab57-117">使用 SMO ManagedComputer 对象</span><span class="sxs-lookup"><span data-stu-id="5ab57-117">Using the SMO ManagedComputer Object</span></span>  
 <span data-ttu-id="5ab57-118"><xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer> 对象是一个托管 SMO 对象，它提供对用于配置管理的 WMI 提供程序的访问。</span><span class="sxs-lookup"><span data-stu-id="5ab57-118">The <xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer> object is a managed SMO object that provides access to the WMI Provider for Configuration Management.</span></span> <span data-ttu-id="5ab57-119">通过使用 SMO 程序，可使用 <xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer> 对象查看和修改 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务、网络设置和别名设置。</span><span class="sxs-lookup"><span data-stu-id="5ab57-119">By using an SMO program, the <xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer> object can be used to view and modify [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services, network settings, and alias settings.</span></span> <span data-ttu-id="5ab57-120">有关详细信息，请参阅[使用 WMI 提供程序管理服务和网络设置](../server-management-objects-smo/tasks/managing-services-and-network-settings-by-using-wmi-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="5ab57-120">For more information, see [Managing Services and Network Settings by Using WMI Provider](../server-management-objects-smo/tasks/managing-services-and-network-settings-by-using-wmi-provider.md).</span></span>  
  
## <a name="using-the-microsoft-management-console-or-sql-server-configuration-manager"></a><span data-ttu-id="5ab57-121">使用 Microsoft 管理控制台或 SQL Server 配置管理器</span><span class="sxs-lookup"><span data-stu-id="5ab57-121">Using the Microsoft Management Console or SQL Server Configuration Manager</span></span>  
 <span data-ttu-id="5ab57-122">与脚本语言或托管代码程序相反，Microsoft 管理控制台 (MMC) 提供一个用于管理 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务的接口。</span><span class="sxs-lookup"><span data-stu-id="5ab57-122">Microsoft Management Console (MMC) provides an interface to manage [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services, as opposed to a scripting language or managed code program.</span></span> <span data-ttu-id="5ab57-123">可使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理 MMC 管理单元停止和启动服务，以及更改服务帐户。</span><span class="sxs-lookup"><span data-stu-id="5ab57-123">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management MMC snap-in can be used to stop and start services, and to change service accounts.</span></span>  
  
 <span data-ttu-id="5ab57-124">此外，还可以使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置管理器管理 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务、客户端和服务器协议以及服务器别名。</span><span class="sxs-lookup"><span data-stu-id="5ab57-124">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager can also be used to manage [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services, client and server protocols, and server aliases</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ab57-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5ab57-125">See Also</span></span>  
 <span data-ttu-id="5ab57-126">[了解用于配置管理的 WMI 提供程序](understanding-the-wmi-provider-for-configuration-management.md) </span><span class="sxs-lookup"><span data-stu-id="5ab57-126">[Understanding the WMI Provider for Configuration Management](understanding-the-wmi-provider-for-configuration-management.md) </span></span>  
 <span data-ttu-id="5ab57-127">[使用 WMI 提供程序进行配置管理](working-with-the-wmi-provider-for-configuration-management.md) </span><span class="sxs-lookup"><span data-stu-id="5ab57-127">[Working with the WMI Provider for Configuration Management](working-with-the-wmi-provider-for-configuration-management.md) </span></span>  
 [<span data-ttu-id="5ab57-128">将 WQL 和脚本语言用于配置管理的 WMI 提供程序</span><span class="sxs-lookup"><span data-stu-id="5ab57-128">Using WQL and Scripting Languages with the WMI Provider for Configuration Management</span></span>](using-wql-and-scripting-languages-with-the-wmi-provider.md)  
  
  
