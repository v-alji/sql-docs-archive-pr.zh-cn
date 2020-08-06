---
title: Analysis Services 向后兼容性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- installing Analysis Services, backward compatibility
- backward compatibility [Analysis Services]
- compatibility [Analysis Services]
- Analysis Services, backward compatibility
- upgrading Analysis Services
- SSAS, backward compatibility
- SQL Server Analysis Services, backward compatibility
ms.assetid: 618b6c3a-e20d-47a9-b2c6-6d848dfba05a
author: minewiskan
ms.author: owend
ms.openlocfilehash: 44a5296bfbd2bae746eb9936d416fd696de16cb7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579409"
---
# <a name="analysis-services-backward-compatibility"></a><span data-ttu-id="04f4a-102">Analysis Services 向后兼容性</span><span class="sxs-lookup"><span data-stu-id="04f4a-102">Analysis Services Backward Compatibility</span></span>
  <span data-ttu-id="04f4a-103">本节中的主题介绍的各个版本之间的行为变化 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="04f4a-103">The topics in this section describe the changes in behavior between versions of  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="04f4a-104">本节内容</span><span class="sxs-lookup"><span data-stu-id="04f4a-104">In This Section</span></span>  
  
|<span data-ttu-id="04f4a-105">主题</span><span class="sxs-lookup"><span data-stu-id="04f4a-105">Topics</span></span>|<span data-ttu-id="04f4a-106">说明</span><span class="sxs-lookup"><span data-stu-id="04f4a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="04f4a-107">SQL Server 2014 中不推荐使用的 Analysis Services 功能</span><span class="sxs-lookup"><span data-stu-id="04f4a-107">Deprecated Analysis Services Features in SQL Server 2014</span></span>](deprecated-analysis-services-features-in-sql-server-2014.md)|<span data-ttu-id="04f4a-108">介绍当前版本中为保持向后兼容而保留、但在未来版本的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]中将删除的功能。</span><span class="sxs-lookup"><span data-stu-id="04f4a-108">Describes features that have been retained in the current version to maintain backward compatibility,  but which will be removed in a future version of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>|  
|[<span data-ttu-id="04f4a-109">SQL Server 2014 中废弃的 Analysis Services 功能</span><span class="sxs-lookup"><span data-stu-id="04f4a-109">Discontinued Analysis Services Functionality in SQL Server 2014</span></span>](discontinued-analysis-services-functionality-in-sql-server-2014.md)|<span data-ttu-id="04f4a-110">介绍在  [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 的早期版本中存在但在后来的版本中已删除的功能。</span><span class="sxs-lookup"><span data-stu-id="04f4a-110">Describes features that existed in earlier versions of  [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] but that have since been removed in later versions.</span></span>|  
|[<span data-ttu-id="04f4a-111">SQL Server 2014 中 Analysis Services 功能的重大更改</span><span class="sxs-lookup"><span data-stu-id="04f4a-111">Breaking Changes to Analysis Services Features in SQL Server 2014</span></span>](breaking-changes-to-analysis-services-features-in-sql-server-2014.md)|<span data-ttu-id="04f4a-112">介绍在此版本的 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 中引入的代码更改，这些更改可能会中断在先前版本的软件中创建的模型、自定义应用程序或脚本。</span><span class="sxs-lookup"><span data-stu-id="04f4a-112">Describes code changes introduced in this release of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] that could potentially break a model or custom applications or script created in previous versions of the software .</span></span>|  
|[<span data-ttu-id="04f4a-113">SQL Server 2014 中 Analysis Services 功能的行为更改</span><span class="sxs-lookup"><span data-stu-id="04f4a-113">Behavior Changes to Analysis Services Features in SQL Server 2014</span></span>](behavior-changes-to-analysis-services-features-in-sql-server-2014.md)|<span data-ttu-id="04f4a-114">介绍在此版本的 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]中具有不同行为的现有功能。</span><span class="sxs-lookup"><span data-stu-id="04f4a-114">Describes existing features that have different behaviors in this release of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="04f4a-115">常见示例包括将默认值更改为新的或不同的值、禁止之前允许的操作或配置，或者引入手动修改或替换升级过程中丢失的设置或配置的要求。</span><span class="sxs-lookup"><span data-stu-id="04f4a-115">Common examples include changing a default to a new or different value, disallowing a previously allowable operation or configuration, or a introducing a requirement to manually revise or replace a setting or configuration that is lost during upgrade.</span></span><br /> <span data-ttu-id="04f4a-116">.</span><span class="sxs-lookup"><span data-stu-id="04f4a-116">.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="04f4a-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="04f4a-117">See Also</span></span>  
 <span data-ttu-id="04f4a-118">[Analysis Services 和商业智能中的新增功能](what-s-new-in-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="04f4a-118">[What's New in Analysis Services and Business Intelligence](what-s-new-in-analysis-services.md) </span></span>  
 [<span data-ttu-id="04f4a-119">升级 Analysis Services</span><span class="sxs-lookup"><span data-stu-id="04f4a-119">Upgrade Analysis Services</span></span>](../database-engine/install-windows/upgrade-analysis-services.md)  
  
  
