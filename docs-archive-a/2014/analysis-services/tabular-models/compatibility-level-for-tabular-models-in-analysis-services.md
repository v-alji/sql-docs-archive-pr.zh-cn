---
title: " (SSAS 表格 SP1) 的兼容级别 |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.versioncompat.f1
ms.assetid: 8943d78d-4a73-4be8-ad14-3d428f5abd06
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2853cd5509b66dbfaadd78c578b9676399e81977
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693504"
---
# <a name="compatibility-level-ssas-tabular-sp1"></a><span data-ttu-id="6583e-102">兼容级别（SSAS 表格 SP1）</span><span class="sxs-lookup"><span data-stu-id="6583e-102">Compatibility Level (SSAS Tabular SP1)</span></span>
  <span data-ttu-id="6583e-103">您可以在创建新的表格模型项目时、升级现有表格模型项目时、升级现有的已部署表格模型数据库时或者在导入 PowerPivot 工作簿时指定*兼容性级别*。</span><span class="sxs-lookup"><span data-stu-id="6583e-103">You can specify *Compatibility Level* when creating new Tabular model projects, when upgrading existing Tabular model projects, when upgrading existing deployed Tabular model databases, or when importing PowerPivot workbooks.</span></span>  
  
## <a name="compatibility-level"></a><span data-ttu-id="6583e-104">兼容级别</span><span class="sxs-lookup"><span data-stu-id="6583e-104">Compatibility Level</span></span>  
 <span data-ttu-id="6583e-105">通常，应该先在开发和测试计算机上安装新版本和 Service Pack，然后再在生产计算机上安装。</span><span class="sxs-lookup"><span data-stu-id="6583e-105">It is common to install new versions and service packs on development and test computers prior to installing on production computers.</span></span> <span data-ttu-id="6583e-106">在此类情况下，了解如何为新的表格模型项目以及已部署到生产环境中的表格模型项目设置兼容级别十分重要。</span><span class="sxs-lookup"><span data-stu-id="6583e-106">In such cases, it is important to understand setting compatibility level for both new Tabular model projects as well as those that have already been deployed into a production environment.</span></span>  
  
 <span data-ttu-id="6583e-107">[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Analysis Services 实例支持以下兼容级别（数据库版本）：</span><span class="sxs-lookup"><span data-stu-id="6583e-107">A [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Analysis Services instance supports the following compatibility levels (database version):</span></span>  
  
-   <span data-ttu-id="6583e-108">SQL Server 2012 (1100) </span><span class="sxs-lookup"><span data-stu-id="6583e-108">SQL Server 2012 (1100)</span></span>  
  
-   <span data-ttu-id="6583e-109">SQL Server 2012 SP1 (1103)</span><span class="sxs-lookup"><span data-stu-id="6583e-109">SQL Server 2012 SP1 (1103)</span></span>  
  
-   <span data-ttu-id="6583e-110">SQL Server 2014 (1103)</span><span class="sxs-lookup"><span data-stu-id="6583e-110">SQL Server 2014 (1103)</span></span>  
  
### <a name="set-compatibility-level-when-creating-a-new-tabular-model-project"></a><span data-ttu-id="6583e-111">在创建新的表格模型项目时设置兼容级别</span><span class="sxs-lookup"><span data-stu-id="6583e-111">Set compatibility level when creating a new Tabular model project</span></span>  
 <span data-ttu-id="6583e-112">在 SQL Server Data Tools (SSDT) 中创建新的表格模型项目时，可以在 "**新建表格项目选项**" 对话框中指定兼容级别。</span><span class="sxs-lookup"><span data-stu-id="6583e-112">When creating a new Tabular model project in SQL Server Data Tools (SSDT), on the **New Tabular project options** dialog you can specify the compatibility level.</span></span> <span data-ttu-id="6583e-113">您可以在创建要部署到 [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] 或更高版本的 Analysis Services 实例还是 SQL Server 2012 Analysis Services 实例（不含 Service Pack 1）的新项目之间进行选择。</span><span class="sxs-lookup"><span data-stu-id="6583e-113">You can choose between creating a new project to be deployed to an [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] or later Analysis Services instance or to an SQL Server 2012 Analysis Services instance (without Service Pack 1).</span></span>  
  
 <span data-ttu-id="6583e-114">您还可以通过选择 **“不再显示此消息”** 选项指定默认的兼容级别。</span><span class="sxs-lookup"><span data-stu-id="6583e-114">You can also specify a default compatibility level by selecting the **Do not show this message again** option.</span></span> <span data-ttu-id="6583e-115">所有后续项目都将使用您指定的兼容级别。</span><span class="sxs-lookup"><span data-stu-id="6583e-115">All subsequent projects will use the compatibility level you specified.</span></span> <span data-ttu-id="6583e-116">您可以通过 SSDT 在“选项”中更改默认兼容级别。</span><span class="sxs-lookup"><span data-stu-id="6583e-116">You can change the default compatibility level in SSDT in Options.</span></span>  
  
### <a name="upgrade-an-existing-tabular-model-project-to-1103-compatibility-level"></a><span data-ttu-id="6583e-117">将现有的表格模型项目升级到 1103 兼容级别</span><span class="sxs-lookup"><span data-stu-id="6583e-117">Upgrade an existing Tabular model project to 1103 compatibility level</span></span>  
 <span data-ttu-id="6583e-118">您可以 [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] 使用 "模型**属性**" 窗口中的 "**兼容级别**" 属性升级在 SSDT 中创建的表格模型项目，然后再将或更高版本安装为与数据库版本1103兼容。</span><span class="sxs-lookup"><span data-stu-id="6583e-118">You can upgrade a Tabular model project created in SSDT prior to installing [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] or later to be database version 1103 compatible by using the **Compatibility Level** property in the model **Properties** window.</span></span> <span data-ttu-id="6583e-119">为了升级表格模型项目，安装 SSDT 的计算机必须安装了 [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] 或更高版本，并且工作区数据库所在的 Analysis Services 实例必须也安装了[!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="6583e-119">In order to upgrade a Tabular model project, the computer on which SSDT is installed must have [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] or later installed and the Analysis Services instance on which the workspace database resides must also have [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] or later installed.</span></span> <span data-ttu-id="6583e-120">不能降级到更早的版本。</span><span class="sxs-lookup"><span data-stu-id="6583e-120">You cannot downgrade to an earlier version.</span></span>  
  
### <a name="upgrade-a-deployed-tabular-model-database-to-1103-compatibility-level"></a><span data-ttu-id="6583e-121">将已部署的表格模型数据库升级到 1103 兼容级别</span><span class="sxs-lookup"><span data-stu-id="6583e-121">Upgrade a deployed Tabular model database to 1103 compatibility level</span></span>  
 <span data-ttu-id="6583e-122">您可以使用 "**数据库属性**" 中的 "**兼容级别**" 属性，将现有的已部署表格模型数据库升级到 SQL Server Management Studio (SSMS) 中兼容的数据库版本1103。</span><span class="sxs-lookup"><span data-stu-id="6583e-122">You can upgrade an existing deployed Tabular model database to database version 1103 compatible in SQL Server Management Studio (SSMS) by using the **Compatibility Level** property in **Database Properties**.</span></span> <span data-ttu-id="6583e-123">为了进行升级，安装 SQL Server Analysis Services 实例的计算机必须安装 [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="6583e-123">In order to upgrade, the computer on which the SQL Server Analysis Services instance is installed must have [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] or later installed.</span></span> <span data-ttu-id="6583e-124">不能将已部署的表格模型数据库降级到更早的版本。</span><span class="sxs-lookup"><span data-stu-id="6583e-124">You cannot downgrade a deployed Tabular model database to an earlier version.</span></span>  
  
### <a name="import-from-powerpivot"></a><span data-ttu-id="6583e-125">从 PowerPivot 导入</span><span class="sxs-lookup"><span data-stu-id="6583e-125">Import from PowerPivot</span></span>  
 <span data-ttu-id="6583e-126">在通过从 PowerPivot 导入来创建新的表格模型项目时，您可以指定是要将兼容级别升级到默认兼容级别（如果以前已在 SSDT 中配置），还是将该兼容级别保留为已在 PowerPivot 工作簿中指定的兼容级别。</span><span class="sxs-lookup"><span data-stu-id="6583e-126">When creating a new Tabular model project by importing from PowerPivot, you can specify if you want to upgrade the compatibility level to the default compatibility level (if previously configured in SSDT) or leave the compatibility level to that already specified in the PowerPivot workbook.</span></span>  
  
### <a name="check-compatibility-level-for-a-tabular-model-database-in-ssms"></a><span data-ttu-id="6583e-127">检查 SSMS 中表格模型数据库的兼容级别</span><span class="sxs-lookup"><span data-stu-id="6583e-127">Check compatibility level for a Tabular model database in SSMS</span></span>  
 <span data-ttu-id="6583e-128">您可以通过查看 "**兼容级别**" 属性，在 [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] **数据库属性**) 中的 " (新建" 来检查 SSMS 中表格模型数据库的兼容级别。</span><span class="sxs-lookup"><span data-stu-id="6583e-128">You can check the compatibility level for a Tabular model database in SSMS by viewing the **Compatibility Level** property (new in [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)]) in **Database Properties**.</span></span>  
  
### <a name="check-supported-compatibility-level-for-an-analysis-services-instance-in-ssms"></a><span data-ttu-id="6583e-129">检查 SSMS 中 Analysis Services 实例支持的兼容级别</span><span class="sxs-lookup"><span data-stu-id="6583e-129">Check supported compatibility level for an Analysis Services instance in SSMS</span></span>  
 <span data-ttu-id="6583e-130">你可以通过查看 "**信息**" 页上的 "**支持的兼容级别**" 属性来检查 SSMS 中支持的兼容性级别， ([!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] Analysis Services "**属性**") 中的 "新建"。</span><span class="sxs-lookup"><span data-stu-id="6583e-130">You can check the supported compatibility level in SSMS by viewing the **Supported Compatibility Level** property on the **Information** page (new in [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)]) in **Analysis Services Properties**.</span></span> <span data-ttu-id="6583e-131">支持的兼容级别 1103 指示安装了 SQL Server SP1 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="6583e-131">A supported compatibility level of 1103 indicates SQL Server SP1 or later is installed.</span></span> <span data-ttu-id="6583e-132">不能更改支持的兼容级别。</span><span class="sxs-lookup"><span data-stu-id="6583e-132">The supported compatibility level cannot be changed.</span></span>  
  
  
