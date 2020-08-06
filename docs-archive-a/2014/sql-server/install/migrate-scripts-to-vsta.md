---
title: 将脚本迁移到 VSTA |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- SSIS Script task, converting scripts
- Script component [Integration Services], converting scripts
- Script task [Integration Services], converting scripts
- SSIS Script component, converting scripts
ms.assetid: d685098b-86a1-46bf-939a-63d56951e009
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: afbc19c35f99a5abc5a6ebd92024e42baa6a9237
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693188"
---
# <a name="migrate-scripts-to-vsta"></a><span data-ttu-id="1fe5a-102">将脚本迁移到 VSTA</span><span class="sxs-lookup"><span data-stu-id="1fe5a-102">Migrate Scripts to VSTA</span></span>
  <span data-ttu-id="1fe5a-103">将包升级 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 到时 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ，会将 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 任何脚本任务或脚本组件中的脚本迁移到 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] (VSTA) 的应用程序的工具。</span><span class="sxs-lookup"><span data-stu-id="1fe5a-103">When you upgrade [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] packages to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] migrates the scripts in any Script tasks or Script components to [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA).</span></span> <span data-ttu-id="1fe5a-104">VSTA 是 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 使用的脚本环境。</span><span class="sxs-lookup"><span data-stu-id="1fe5a-104">VSTA is the scripting environment that [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] uses.</span></span> <span data-ttu-id="1fe5a-105">在中 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] ，的脚本编写环境适用 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 于 (VSA) 的应用程序。</span><span class="sxs-lookup"><span data-stu-id="1fe5a-105">In [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], the scripting environment for [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] is [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] for Applications (VSA).</span></span>  
  
 <span data-ttu-id="1fe5a-106">如果脚本任务或脚本组件中的脚本引用接口，您在升级包之前可能必须修改这些引用。</span><span class="sxs-lookup"><span data-stu-id="1fe5a-106">If the scripts in either the Script tasks or Script components reference interfaces, you might have to modify those references before you upgrade the package.</span></span> <span data-ttu-id="1fe5a-107">否则，将无法升级包或者将无法验证脚本，具体取决于所使用的升级方法。</span><span class="sxs-lookup"><span data-stu-id="1fe5a-107">Otherwise, the package will not be upgraded or the scripts will not be validated, depending on the upgrade method that you use.</span></span> <span data-ttu-id="1fe5a-108">若要修改这些引用，请将对 IDTS*xxx*90 接口的引用替换为对相应的 IDTS*xxx*100 接口的引用。</span><span class="sxs-lookup"><span data-stu-id="1fe5a-108">To modify these references, replace references to IDTS*xxx*90 interfaces with references to the corresponding IDTS*xxx*100 interfaces.</span></span>  
  
 <span data-ttu-id="1fe5a-109">有关如何迁移脚本和升级包的详细信息，请参阅[upgrade Integration Services 软件包](../../integration-services/install-windows/upgrade-integration-services-packages.md)。</span><span class="sxs-lookup"><span data-stu-id="1fe5a-109">For more information about how to migrate scripts and upgrade packages, see [Upgrade Integration Services Packages](../../integration-services/install-windows/upgrade-integration-services-packages.md).</span></span>  
  
## <a name="understanding-migration-failures"></a><span data-ttu-id="1fe5a-110">了解迁移失败</span><span class="sxs-lookup"><span data-stu-id="1fe5a-110">Understanding Migration Failures</span></span>  
 <span data-ttu-id="1fe5a-111">在迁移脚本时，脚本可能会由于以下原因之一而失败：</span><span class="sxs-lookup"><span data-stu-id="1fe5a-111">When you migrate the scripts, the migration can fail because of one of the following reasons:</span></span>  
  
-   <span data-ttu-id="1fe5a-112">VSA 脚本的入口点已重命名。</span><span class="sxs-lookup"><span data-stu-id="1fe5a-112">The entry point for the VSA script was renamed.</span></span>  
  
     <span data-ttu-id="1fe5a-113">入口点在 VSTA 项目中的 `ScriptMain` 类中指定一种方法，[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 运行时会将该方法作为脚本任务代码的入口点来调用。</span><span class="sxs-lookup"><span data-stu-id="1fe5a-113">The entry point specifies the method in the `ScriptMain` class in the VSTA project that the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] runtime calls as the entry point into the Script task code.</span></span> <span data-ttu-id="1fe5a-114">`ScriptMain` 类是由脚本模板生成的默认类。</span><span class="sxs-lookup"><span data-stu-id="1fe5a-114">The `ScriptMain` class is the default class that the script templates generate.</span></span>  
  
-   <span data-ttu-id="1fe5a-115">在 VSA 脚本中，没有入口点或者有多个入口点。</span><span class="sxs-lookup"><span data-stu-id="1fe5a-115">There is no entry point or there are multiple entry points in the VSA script.</span></span>  
  
-   <span data-ttu-id="1fe5a-116">无法添加程序集引用。</span><span class="sxs-lookup"><span data-stu-id="1fe5a-116">Assembly references could not be added.</span></span>  
  
-   <span data-ttu-id="1fe5a-117">已经将 `ScriptMain` 类修改为从 `ScriptObjectModelSSIS` 类以外的其他类中继承。</span><span class="sxs-lookup"><span data-stu-id="1fe5a-117">The `ScriptMain` class was modified to inherit from other classes in addition to the `ScriptObjectModelSSIS` class.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)]<span data-ttu-id="1fe5a-118">不 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 支持多重继承。</span><span class="sxs-lookup"><span data-stu-id="1fe5a-118">[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] does not support multiple inheritance.</span></span>  
  
 <span data-ttu-id="1fe5a-119">不能将使用的 VSA 脚本转换 [!INCLUDE[vbprvblong](../../includes/vbprvblong-md.md)] 为使用的 VSTA 脚本 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[csharp_orcas_long](../../includes/csharp-orcas-long-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="1fe5a-119">You cannot convert a VSA script that uses [!INCLUDE[vbprvblong](../../includes/vbprvblong-md.md)] to a VSTA script that uses [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[csharp_orcas_long](../../includes/csharp-orcas-long-md.md)].</span></span> <span data-ttu-id="1fe5a-120">但是，你可以创建一个使用的新的 VSTA 脚本 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[csharp_orcas_long](../../includes/csharp-orcas-long-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="1fe5a-120">However, you can create a new VSTA script that uses [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[csharp_orcas_long](../../includes/csharp-orcas-long-md.md)].</span></span> <span data-ttu-id="1fe5a-121">有关详细信息，请参阅[脚本任务的编码和调试](../../integration-services/control-flow/script-task.md)和[脚本组件的编码和调试](../../integration-services/data-flow/transformations/script-component.md)。</span><span class="sxs-lookup"><span data-stu-id="1fe5a-121">For more information, see [Coding and Debugging the Script Task](../../integration-services/control-flow/script-task.md) and [Coding and Debugging the Script Component](../../integration-services/data-flow/transformations/script-component.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1fe5a-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1fe5a-122">See Also</span></span>  
 [<span data-ttu-id="1fe5a-123">用脚本扩展包</span><span class="sxs-lookup"><span data-stu-id="1fe5a-123">Extending Packages with Scripting</span></span>](../../relational-databases/server-management-objects-smo/tasks/scripting.md)  
  
  
