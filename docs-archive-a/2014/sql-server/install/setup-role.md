---
title: 设置角色 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: c7e9db15-89f2-4d4d-8860-1e64c5821c4d
author: heidisteen
ms.author: heidist
ms.openlocfilehash: add000eed671303c78ab0500303f826bafe4ab77
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586150"
---
# <a name="setup-role"></a><span data-ttu-id="a34ee-102">安装角色</span><span class="sxs-lookup"><span data-stu-id="a34ee-102">Setup Role</span></span>
  <span data-ttu-id="a34ee-103">使用此页可以指定是使用“功能选择”页来分别选择各项功能，还是使用安装角色来进行安装。</span><span class="sxs-lookup"><span data-stu-id="a34ee-103">Use this page to specify whether to use the Feature Selection page to select individual features, or to install using a setup role.</span></span>  
  
 <span data-ttu-id="a34ee-104">`setup role`是实现预定义 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置所需全部功能和共享组件的固定选择集。</span><span class="sxs-lookup"><span data-stu-id="a34ee-104">A `setup role` is a fixed selection of all the features and shared components that are required to implement a predefined [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] configuration.</span></span>  
  
## <a name="options"></a><span data-ttu-id="a34ee-105">选项</span><span class="sxs-lookup"><span data-stu-id="a34ee-105">Options</span></span>  
 <span data-ttu-id="a34ee-106">**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]功能安装**</span><span class="sxs-lookup"><span data-stu-id="a34ee-106">**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Feature Installation**</span></span>  
 <span data-ttu-id="a34ee-107">选择此选项可分别选择各项功能和共享组件。</span><span class="sxs-lookup"><span data-stu-id="a34ee-107">Choose this option to select individual features and shared components.</span></span> <span data-ttu-id="a34ee-108">实例功能包括数据库引擎服务、Analysis Services（本机模式）和 Reporting Services。</span><span class="sxs-lookup"><span data-stu-id="a34ee-108">Instance features include Database Engine Services, Analysis Services (native mode), and Reporting Services.</span></span>  
  
 <span data-ttu-id="a34ee-109">**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]PowerPivot for SharePoint**</span><span class="sxs-lookup"><span data-stu-id="a34ee-109">**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerPivot for SharePoint**</span></span>  
 <span data-ttu-id="a34ee-110">选择此选项可以在 SharePoint 2010 场中安装 Analysis Services 服务器组件。</span><span class="sxs-lookup"><span data-stu-id="a34ee-110">Choose this option to install Analysis Services server components in a SharePoint 2010 farm.</span></span> <span data-ttu-id="a34ee-111">此选项在场中部署 PowerPivot 系统服务和 Analysis Services 服务器，同时支持对包含嵌入式 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 数据的已发布 Excel 工作簿进行查询和数据处理。</span><span class="sxs-lookup"><span data-stu-id="a34ee-111">This option deploys the PowerPivot System Service and the Analysis Services server in a farm, enabling query and data processing for published Excel workbooks that contain embedded [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] data.</span></span>  
  
 <span data-ttu-id="a34ee-112">如果需要使用关系数据库引擎实例在 SharePoint 场中承载数据库，可以选择在安装中添加关系数据库引擎实例。</span><span class="sxs-lookup"><span data-stu-id="a34ee-112">Optionally, you can add a relational database engine instance to your installation if you require it to host databases in a SharePoint farm.</span></span> <span data-ttu-id="a34ee-113">如果已配置场，则不必选择。</span><span class="sxs-lookup"><span data-stu-id="a34ee-113">If the farm is already configured, you can skip this option.</span></span>  
  
 <span data-ttu-id="a34ee-114">安装完成后，必须使用以下方法之一配置软件：PowerPivot 配置工具、PowerShell cmdlet 或 SharePoint 2010 管理中心。</span><span class="sxs-lookup"><span data-stu-id="a34ee-114">After Setup is finished, you must configure the software using one of the following approaches: PowerPivot Configuration tool, PowerShell cmdlets, or SharePoint 2010 Central Administration.</span></span> <span data-ttu-id="a34ee-115">与以往的版本相比，安装程序不再执行 PowerPivot 安装的任何配置任务。</span><span class="sxs-lookup"><span data-stu-id="a34ee-115">In contrast with previous releases, Setup no longer performs any configuration tasks for a PowerPivot installation.</span></span>  
  
 <span data-ttu-id="a34ee-116">基于角色的安装不包含 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerPivot for Excel 客户端应用程序。</span><span class="sxs-lookup"><span data-stu-id="a34ee-116">A role-based installation does not include the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerPivot for Excel client application.</span></span> <span data-ttu-id="a34ee-117">将单独安装此客户端应用程序。</span><span class="sxs-lookup"><span data-stu-id="a34ee-117">The client application is installed separately.</span></span>  
  
 <span data-ttu-id="a34ee-118">**所有功能以及默认值**</span><span class="sxs-lookup"><span data-stu-id="a34ee-118">**All Features With Defaults**</span></span>  
 <span data-ttu-id="a34ee-119">选择此安装角色将安装此版本提供的所有功能。</span><span class="sxs-lookup"><span data-stu-id="a34ee-119">Choose this setup role to install all features that are available for this release.</span></span> <span data-ttu-id="a34ee-120">请注意，从该角色中排除 PowerPivot for SharePoint。</span><span class="sxs-lookup"><span data-stu-id="a34ee-120">Note that PowerPivot for SharePoint is excluded from this role.</span></span> <span data-ttu-id="a34ee-121">您必须使用 PowerPivot for SharePoint 安装角色来安装该功能。</span><span class="sxs-lookup"><span data-stu-id="a34ee-121">You must use the PowerPivot for SharePoint setup role to install that feature.</span></span>  
  
 <span data-ttu-id="a34ee-122">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 配置为使用 **NT AUTHORITY\NETWORK SERVICE** 帐户开始。</span><span class="sxs-lookup"><span data-stu-id="a34ee-122">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] is configured to start using the **NT AUTHORITY\NETWORK SERVICE** account.</span></span> <span data-ttu-id="a34ee-123">将当前用户设置为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**sysadmin** 角色的成员。</span><span class="sxs-lookup"><span data-stu-id="a34ee-123">The current user will be provisioned as a member of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**sysadmin** role.</span></span> <span data-ttu-id="a34ee-124">此选项设置的值可以通过指定其他命令行参数来覆盖。</span><span class="sxs-lookup"><span data-stu-id="a34ee-124">Values set by this option can be overridden by specifying additional command line parameters.</span></span>  
  
 <span data-ttu-id="a34ee-125">当操作系统不是域控制器时，默认情况下，数据库引擎和 Reporting Services 将使用 NTAUTHORITY\NETWORK SERVICE 帐户，Integration Services 将使用 NTAUTHORITY\NETWORK SERVICE 帐户，而 SQL 全文筛选器后台程序启动器将使用 NTAUTHORITY\LOCAL SERVICE 帐户。</span><span class="sxs-lookup"><span data-stu-id="a34ee-125">When the operating system is not a domain controller, by default the Database Engine and Reporting Services will use the NTAUTHORITY\NETWORK SERVICE account, Integration Services will use the NTAUTHORITY\NETWORK SERVICE account, and the SQL Full text Filter Daemon Launcher will use the NTAUTHORITY\LOCAL SERVICE account.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a34ee-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a34ee-126">See Also</span></span>  
 <span data-ttu-id="a34ee-127">[安装 PowerPivot for SharePoint](https://go.microsoft.com/fwlink/?LinkId=206906) </span><span class="sxs-lookup"><span data-stu-id="a34ee-127">[Installing PowerPivot for SharePoint](https://go.microsoft.com/fwlink/?LinkId=206906) </span></span>  
 <span data-ttu-id="a34ee-128">[硬件和软件要求 (PowerPivot for SharePoint](https://go.microsoft.com/fwlink/?LinkId=216823) </span><span class="sxs-lookup"><span data-stu-id="a34ee-128">[Hardware and Software Requirements (PowerPivot for SharePoint](https://go.microsoft.com/fwlink/?LinkId=216823) </span></span>  
 [<span data-ttu-id="a34ee-129">功能选择</span><span class="sxs-lookup"><span data-stu-id="a34ee-129">Feature Selection</span></span>](../../../2014/sql-server/install/feature-selection.md)  
  
  
