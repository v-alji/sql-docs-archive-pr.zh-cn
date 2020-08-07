---
title: Analysis Services 配置-帐户预配 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Analysis Services configuration
- account provisioning
ms.assetid: 169b1af2-6fe2-467f-8ca4-919f24c620ce
author: heidisteen
ms.author: heidist
ms.openlocfilehash: 109b5d9ddddf2b78c0bb8947cfa876d233f804ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586235"
---
# <a name="analysis-services-configuration---account-provisioning"></a><span data-ttu-id="be43b-102">Analysis Services 配置 – 帐户设置</span><span class="sxs-lookup"><span data-stu-id="be43b-102">Analysis Services Configuration - Account Provisioning</span></span>
  <span data-ttu-id="be43b-103">使用此页可以设置服务器节点，并向要求对 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 进行不受限访问的用户或服务授予管理权限。</span><span class="sxs-lookup"><span data-stu-id="be43b-103">Use this page to set the server mode, and to grant administrative permissions to users or services requiring unrestricted access to [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="be43b-104">安装程序不会自动将本地 Windows 组 BUILTIN\Administrators 添加到要安装的实例的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 服务器管理员角色。</span><span class="sxs-lookup"><span data-stu-id="be43b-104">Setup does not automatically add the local Windows Group BUILTIN\Administrators to the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] server administrator role of the instance you are installing.</span></span> <span data-ttu-id="be43b-105">如果要将本地管理员组添加到服务器管理员角色，则必须显式指定该组。</span><span class="sxs-lookup"><span data-stu-id="be43b-105">If you want to add the local Administrators group to the server administrator role, you must explicitly specify that group.</span></span>  
  
 <span data-ttu-id="be43b-106">如果您正在安装 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]，确保将管理权限授予负责在 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 场中部署 [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] 服务器的 SharePoint 场管理员或服务管理员。</span><span class="sxs-lookup"><span data-stu-id="be43b-106">If you are installing [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)], be sure to grant administrative permissions to SharePoint farm administrators or service administrators who are responsible for a [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] server deployment in a [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] farm.</span></span> <span data-ttu-id="be43b-107">有关 [!INCLUDE[ssGeminiMTS](../../includes/ssgeminimts-md.md)] 安装和服务帐户要求的详细信息，请参阅[随 SharePoint 一起安装 SQL Server BI 功能 &#40;PowerPivot 和 Reporting Services&#41;](../../../2014/sql-server/install/install-sql-server-bi-features-sharepoint-powerpivot-reporting-services.md)。</span><span class="sxs-lookup"><span data-stu-id="be43b-107">For more information about [!INCLUDE[ssGeminiMTS](../../includes/ssgeminimts-md.md)] installation and service account requirements, see [Install SQL Server BI Features with SharePoint &#40;PowerPivot and Reporting Services&#41;](../../../2014/sql-server/install/install-sql-server-bi-features-sharepoint-powerpivot-reporting-services.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="be43b-108">选项</span><span class="sxs-lookup"><span data-stu-id="be43b-108">Options</span></span>  
 <span data-ttu-id="be43b-109">**服务器模式** - 服务器模式指定可部署到服务器的 Analysis Services 数据库的类型。</span><span class="sxs-lookup"><span data-stu-id="be43b-109">**Server Mode** - The server mode specifies the type of Analysis Services databases that can be deployed to the server.</span></span> <span data-ttu-id="be43b-110">服务器模式在安装过程中确定，之后不能修改。</span><span class="sxs-lookup"><span data-stu-id="be43b-110">Server modes are determined during Setup and cannot be modified later.</span></span> <span data-ttu-id="be43b-111">各模式是互斥的，也就是说，您需要两个 Analysis Services 实例，它们配置为不同的模式，以便同时支持典型 OLAP 和表格模型解决方案。</span><span class="sxs-lookup"><span data-stu-id="be43b-111">Each mode is mutually exclusive, which means that you will need two instances of Analysis Services, each configured for a different mode, to support both classic OLAP and tabular model solutions.</span></span>  
  
 <span data-ttu-id="be43b-112">**指定管理员** - 必须为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例指定至少一个服务器管理员。</span><span class="sxs-lookup"><span data-stu-id="be43b-112">**Specify Administrators** - You must specify at least one server administrator for the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="be43b-113">您指定的用户或组将成为所安装的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 实例的服务器管理员角色的成员。</span><span class="sxs-lookup"><span data-stu-id="be43b-113">The users or groups that you specify will become members of the server administrator role of the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance you are installing.</span></span> <span data-ttu-id="be43b-114">这些都必须是与安装该软件的计算机处于同一域中的 Windows 域用户帐户。</span><span class="sxs-lookup"><span data-stu-id="be43b-114">These must be Windows domain user accounts in the same domain as the computer on which you are installing the software.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="be43b-115">用户帐户控制 (UAC) 是一个 Windows 安全功能，它要求在运行管理操作或应用程序之前，先由管理员专门审批。</span><span class="sxs-lookup"><span data-stu-id="be43b-115">User Account Control (UAC) is a Windows security feature that requires an administrator to specifically approve administrative actions or applications before they are allowed to run.</span></span> <span data-ttu-id="be43b-116">由于 UAC 在默认情况下处于打开状态，因此系统将提示您允许需要提升权限的特定操作。</span><span class="sxs-lookup"><span data-stu-id="be43b-116">Because UAC is on by default, you will be prompted to allow specific operations that require elevated privileges.</span></span> <span data-ttu-id="be43b-117">您可以配置 UAC 来更改默认行为，或针对特定程序自定义 UAC。</span><span class="sxs-lookup"><span data-stu-id="be43b-117">You can configure UAC to change the default behavior or customize UAC for specific programs.</span></span> <span data-ttu-id="be43b-118">有关 UAC 和 UAC 配置的详细信息，请参阅 [User Account Control Step by Step Guide](https://go.microsoft.com/fwlink/?linkid=196350)（用户帐户控制分步指南）和 [User Account Control (Wikipedia)](https://go.microsoft.com/fwlink/?linkid=196351)（用户帐户控制 (Wikipedia)）。</span><span class="sxs-lookup"><span data-stu-id="be43b-118">For more information about UAC and UAC configuration, see [User Account Control Step by Step Guide](https://go.microsoft.com/fwlink/?linkid=196350) and [User Account Control (Wikipedia)](https://go.microsoft.com/fwlink/?linkid=196351).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be43b-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="be43b-119">See Also</span></span>  
 <span data-ttu-id="be43b-120">[&#40;Analysis Services 配置服务帐户&#41;](../../../2014/analysis-services/instances/configure-service-accounts-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="be43b-120">[Configure Service Accounts &#40;Analysis Services&#41;](../../../2014/analysis-services/instances/configure-service-accounts-analysis-services.md) </span></span>  
 [<span data-ttu-id="be43b-121">配置 Windows 服务帐户和权限</span><span class="sxs-lookup"><span data-stu-id="be43b-121">Configure Windows Service Accounts and Permissions</span></span>](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)  
  
  
