---
title: 移动数据挖掘对象 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data mining [Analysis Services], models
- data mining editor [Analysis Services]
- mining models [Analysis Services], managing
- Data Mining Designer
- mining models [Analysis Services], modifying
ms.assetid: bc108407-2603-4387-b930-b5bb9df78069
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2b10be3a79487376b173eab87059404b7f7a618e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687368"
---
# <a name="moving-data-mining-objects"></a><span data-ttu-id="01013-102">移动数据挖掘对象</span><span class="sxs-lookup"><span data-stu-id="01013-102">Moving Data Mining Objects</span></span>
  <span data-ttu-id="01013-103">移动数据挖掘对象的最常见情形是将模型从测试或分析环境部署到生产环境，或者与其他用户共享模型。</span><span class="sxs-lookup"><span data-stu-id="01013-103">The most common scenarios for moving data mining objects are to deploy a model from a testing or analysis environment to a production environment, or to share models with other users.</span></span>  
  
 <span data-ttu-id="01013-104">本主题介绍如何使用 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]提供的工具和脚本撰写语言来移动数据挖掘对象。</span><span class="sxs-lookup"><span data-stu-id="01013-104">This topic describes how you can use the tools and scripting languages provided by [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], for moving data mining objects.</span></span>  
  
## <a name="moving-data-mining-objects-between-databases-or-servers"></a><span data-ttu-id="01013-105">在数据库或服务器之间移动数据挖掘对象</span><span class="sxs-lookup"><span data-stu-id="01013-105">Moving Data Mining Objects between Databases or Servers</span></span>  
 <span data-ttu-id="01013-106">您可以通过以下方法在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 数据库之间或 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 实例之间移动数据挖掘对象：</span><span class="sxs-lookup"><span data-stu-id="01013-106">You can move data mining objects between [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] databases or between instances of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in the following ways:</span></span>  
  
-   <span data-ttu-id="01013-107">将解决方案重新部署到其他数据库。</span><span class="sxs-lookup"><span data-stu-id="01013-107">Re-deploying the solution to a different database.</span></span>  
  
-   <span data-ttu-id="01013-108">撰写单独对象的脚本。</span><span class="sxs-lookup"><span data-stu-id="01013-108">Scripting individual objects.</span></span>  
  
-   <span data-ttu-id="01013-109">备份然后还原分发数据库的副本。</span><span class="sxs-lookup"><span data-stu-id="01013-109">Backing up and then restoring a copy of the database.</span></span>  
  
-   <span data-ttu-id="01013-110">导出和导入结构和模型。</span><span class="sxs-lookup"><span data-stu-id="01013-110">Exporting and importing structures and models.</span></span>  
  
 <span data-ttu-id="01013-111">下一节更为详细地说明这些选项。</span><span class="sxs-lookup"><span data-stu-id="01013-111">The following section explains these options in more detail.</span></span>  
  
### <a name="deploying"></a><span data-ttu-id="01013-112">正在部署</span><span class="sxs-lookup"><span data-stu-id="01013-112">Deploying</span></span>  
 <span data-ttu-id="01013-113">将解决方案部署到不同的服务器或数据库要求您具有以前通过使用 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]创建的解决方案文件。</span><span class="sxs-lookup"><span data-stu-id="01013-113">Deploying the solution to a different server or database requires that you have the solution file that was created by using [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="01013-114">有关部署 Analysis Services 解决方案的详细信息，请参阅[部署 Analysis Services 项目 (SSDT)](../multidimensional-models/deploy-analysis-services-projects-ssdt.md)。</span><span class="sxs-lookup"><span data-stu-id="01013-114">For more information about deploying Analysis Services solutions, see [Deploy Analysis Services Projects &#40;SSDT&#41;](../multidimensional-models/deploy-analysis-services-projects-ssdt.md).</span></span>  
  
### <a name="scripting"></a><span data-ttu-id="01013-115">脚本编写</span><span class="sxs-lookup"><span data-stu-id="01013-115">Scripting</span></span>  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="01013-116">提供了几种语言，可用于撰写对象的脚本。</span><span class="sxs-lookup"><span data-stu-id="01013-116">provides several languages that you can use to script objects.</span></span>  
  
-   <span data-ttu-id="01013-117">**XMLA**：可以通过在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中右键单击对象，使用 XMLA 编写对象的脚本。</span><span class="sxs-lookup"><span data-stu-id="01013-117">**XMLA**: You can script objects using XMLA by right-clicking objects in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="01013-118">若要执行该脚本，请在目标服务器上的 **“XMLA 查询”** 窗口中打开该脚本。</span><span class="sxs-lookup"><span data-stu-id="01013-118">To execute the script, open it in an **XMLA Query** window on the target server.</span></span>  
  
-   <span data-ttu-id="01013-119">**DMX**：您可以通过使用模板或在 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] 和 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中提供的查询生成器之一创建脚本。</span><span class="sxs-lookup"><span data-stu-id="01013-119">**DMX**: You can create scripts by using templates or one of the query builders provided in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] and [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="01013-120">但请注意，在您可以使用各脚本撰写语言执行的任务之间存在差异：</span><span class="sxs-lookup"><span data-stu-id="01013-120">Note, however, that there are differences in the tasks that you can perform with each scripting language:</span></span>  
  
-   <span data-ttu-id="01013-121">诸如对象说明和数据绑定之类的属性只能通过使用 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] DDL 语言创建或更改，使用 DMX 则不可以。</span><span class="sxs-lookup"><span data-stu-id="01013-121">Properties such as the object description and data bindings can only by created or changed by using [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] DDL languages, not by using DMX.</span></span>  
  
-   <span data-ttu-id="01013-122">只有 DMX 支持导入和导出挖掘对象。</span><span class="sxs-lookup"><span data-stu-id="01013-122">Only DMX supports the import and export of mining objects.</span></span>  
  
-   <span data-ttu-id="01013-123">只有 DMX 支持生成 PMML 或从 PMML 导入模型定义。</span><span class="sxs-lookup"><span data-stu-id="01013-123">Only DMX supports generating PMML or importing model definitions from PMML.</span></span>  
  
-   <span data-ttu-id="01013-124">只有 DMX 支持使用应用程序数据对模型定型。</span><span class="sxs-lookup"><span data-stu-id="01013-124">Only DMX supports training a model with application data.</span></span> <span data-ttu-id="01013-125">此外，DMX INSERT INTO 语句支持在不为键列提供值的情况下为模型定型。</span><span class="sxs-lookup"><span data-stu-id="01013-125">Moreover, the DMX INSERT INTO statement supports training a model without providing values for a key column.</span></span>  
  
 <span data-ttu-id="01013-126">有关详细信息，请参阅 [使用 Analysis Services 脚本语言 (ASSL) 开发](../multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md)。</span><span class="sxs-lookup"><span data-stu-id="01013-126">For more information, see [Developing with Analysis Services Scripting Language &#40;ASSL&#41;](../multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md).</span></span>  
  
### <a name="backup-and-restore"></a><span data-ttu-id="01013-127">备份和还原</span><span class="sxs-lookup"><span data-stu-id="01013-127">Backup and Restore</span></span>  
 <span data-ttu-id="01013-128">备份和还原整个 Analysis Services 数据库是在数据挖掘解决方案依赖于 OLAP 对象的情况下选择的方法。</span><span class="sxs-lookup"><span data-stu-id="01013-128">Backup and restore of an entire Analysis Services database is the method of choice if your data mining solution relies on OLAP objects.</span></span> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="01013-129">提供了备份和还原功能，可以更快、更方便地备份数据库。</span><span class="sxs-lookup"><span data-stu-id="01013-129">provides backup and restore functionality that makes database backups faster and easier.</span></span>  
  
 <span data-ttu-id="01013-130">有关备份的详细信息，请参阅 [备份和还原 Analysis Services 数据库](../multidimensional-models/backup-and-restore-of-analysis-services-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="01013-130">For more information about backup, see [Backup and Restore of Analysis Services Databases](../multidimensional-models/backup-and-restore-of-analysis-services-databases.md).</span></span>  
  
### <a name="exporting-and-importing"></a><span data-ttu-id="01013-131">导出和导入</span><span class="sxs-lookup"><span data-stu-id="01013-131">Exporting and Importing</span></span>  
 <span data-ttu-id="01013-132">导出后再导入挖掘模型和结构（使用 DMX 语句）是最简单的移动或备份各关系数据挖掘对象的方法。</span><span class="sxs-lookup"><span data-stu-id="01013-132">Exporting and then re-importing mining models and structures by using DMX statements is the easiest way to move or back up individual relational data mining objects.</span></span> <span data-ttu-id="01013-133">有关这些操作的 DMX 语法的详细信息，请参阅以下主题：</span><span class="sxs-lookup"><span data-stu-id="01013-133">For more information about the DMX syntax for these operations, see the following topics:</span></span>  
  
-   [<span data-ttu-id="01013-134">EXPORT (DMX)</span><span class="sxs-lookup"><span data-stu-id="01013-134">EXPORT &#40;DMX&#41;</span></span>](/sql/dmx/export-dmx)  
  
-   [<span data-ttu-id="01013-135">IMPORT (DMX)</span><span class="sxs-lookup"><span data-stu-id="01013-135">IMPORT &#40;DMX&#41;</span></span>](/sql/dmx/import-dmx)  
  
 <span data-ttu-id="01013-136">如果指定 INCLUDE DEPENDENCIES 选项， [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 还将导出所有所需数据源视图的定义，并且将在导入模型或结构时在目标服务器上重新创建数据源视图。</span><span class="sxs-lookup"><span data-stu-id="01013-136">If you specify the INCLUDE DEPENDENCIES option, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] will also export the definition of any required data source views, and when you import the model or structure, it will re-create the data source view on the target server.</span></span> <span data-ttu-id="01013-137">完成了模型导入后，请确保对对象设置必需的挖掘权限。</span><span class="sxs-lookup"><span data-stu-id="01013-137">After you have finished importing the model, make sure to set the necessary mining permissions on the object.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="01013-138">您不能使用 DMX 导出和导入 OLAP 模型。</span><span class="sxs-lookup"><span data-stu-id="01013-138">You cannot export and import OLAP models by using DMX.</span></span> <span data-ttu-id="01013-139">如果挖掘模型基于 OLAP 多维数据集，则必须使用 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 提供的功能来备份和还原整个数据库，或者重新部署多维数据集及其模型。</span><span class="sxs-lookup"><span data-stu-id="01013-139">If your mining model is based on an OLAP cube, you must use the functionality provided by [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] for backing up and restoring an entire database, or redeploy the cube and its models.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01013-140">另请参阅</span><span class="sxs-lookup"><span data-stu-id="01013-140">See Also</span></span>  
 [<span data-ttu-id="01013-141">管理数据挖掘解决方案和对象</span><span class="sxs-lookup"><span data-stu-id="01013-141">Management of Data Mining Solutions and Objects</span></span>](management-of-data-mining-solutions-and-objects.md)  
  
  
