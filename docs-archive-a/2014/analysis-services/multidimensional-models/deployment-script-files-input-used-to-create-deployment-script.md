---
title: 了解用于创建部署脚本的输入文件 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- input files [Analysis Services]
- Analysis Services Deployment Wizard, scripts
- deploying [Analysis Services], input files
- Analysis Services Deployment Wizard, input files
- scripts [Analysis Services], deployment
- Analysis Services deployments, input files
- modifying input files
ms.assetid: 20e080cd-6a0e-4591-b022-ea4cd3638e36
author: minewiskan
ms.author: owend
ms.openlocfilehash: 34695993d4f153c6c0b97fef744d92c682517c99
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587077"
---
# <a name="understanding-the-input-files-used-to-create-the-deployment-script"></a><span data-ttu-id="88c0e-102">了解用于创建部署脚本的输入文件</span><span class="sxs-lookup"><span data-stu-id="88c0e-102">Understanding the Input Files Used to Create the Deployment Script</span></span>
  <span data-ttu-id="88c0e-103">生成 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 项目时， [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 将为该项目生成 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="88c0e-103">When you build a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project, [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] generates XML files for the project.</span></span> [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] <span data-ttu-id="88c0e-104">将这些 XML 文件放在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 项目的输出文件夹中。</span><span class="sxs-lookup"><span data-stu-id="88c0e-104">puts these XML files in the Output folder of the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project.</span></span> <span data-ttu-id="88c0e-105">默认情况下，输出将输出到 \Bin 文件夹之中。</span><span class="sxs-lookup"><span data-stu-id="88c0e-105">By default output is out in the \Bin folder.</span></span> <span data-ttu-id="88c0e-106">下表列出了 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 创建的 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="88c0e-106">The following table lists the XML files that [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] creates.</span></span>  
  
|<span data-ttu-id="88c0e-107">XMLA 文件</span><span class="sxs-lookup"><span data-stu-id="88c0e-107">XMLA file</span></span>|<span data-ttu-id="88c0e-108">说明</span><span class="sxs-lookup"><span data-stu-id="88c0e-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="88c0e-109">\<*project name*>。 .asdatabase</span><span class="sxs-lookup"><span data-stu-id="88c0e-109">\<*project name*>.asdatabase</span></span>|<span data-ttu-id="88c0e-110">包含项目中所有 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 对象的声明性定义。</span><span class="sxs-lookup"><span data-stu-id="88c0e-110">Contains the declarative definitions for all the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] objects in the project.</span></span>|  
|<span data-ttu-id="88c0e-111">\<*project name*>。 .deploymenttargets</span><span class="sxs-lookup"><span data-stu-id="88c0e-111">\<*project name*>.deploymenttargets</span></span>|<span data-ttu-id="88c0e-112">包含将在其中创建 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 对象的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 实例和数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="88c0e-112">Contains the name of the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance and database in which the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] objects will be created.</span></span>|  
|<span data-ttu-id="88c0e-113">\<*project name*>。 .configsettings</span><span class="sxs-lookup"><span data-stu-id="88c0e-113">\<*project name*>.configsettings</span></span>|<span data-ttu-id="88c0e-114">包含特定于环境的设置，如数据源连接信息和对象存储位置。</span><span class="sxs-lookup"><span data-stu-id="88c0e-114">Contains environment specific settings, such as data source connection information and object storage locations.</span></span> <span data-ttu-id="88c0e-115">此文件中的设置将替代 .asdatabase 文件中的设置 \<*project name*> 。</span><span class="sxs-lookup"><span data-stu-id="88c0e-115">Settings in this file override settings in the \<*project name*>.asdatabase file.</span></span>|  
|<span data-ttu-id="88c0e-116">\<*project name*>。 d</span><span class="sxs-lookup"><span data-stu-id="88c0e-116">\<*project name*>.deploymentoptions</span></span>|<span data-ttu-id="88c0e-117">包含部署选项，例如部署是否是事务性的，以及是否在部署后处理已部署的对象。</span><span class="sxs-lookup"><span data-stu-id="88c0e-117">Contains deployment options, such as whether deployment is transactional and whether deployed objects should be processed after deployment.</span></span>|  
  
> [!NOTE]  
>  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] <span data-ttu-id="88c0e-118">从不在其项目文件中存储密码。</span><span class="sxs-lookup"><span data-stu-id="88c0e-118">never stores passwords in its project files.</span></span>  
  
## <a name="modifying-the-input-files"></a><span data-ttu-id="88c0e-119">修改输入文件</span><span class="sxs-lookup"><span data-stu-id="88c0e-119">Modifying the Input Files</span></span>  
 <span data-ttu-id="88c0e-120">修改输入文件中的值或从输入文件中检索的值，就可以更改部署目标、配置设置和部署选项，而无需编辑整个 \<*project name*> .asdatabase 文件 (或整个 XMLA 脚本文件（如果从现有 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 数据库) 生成脚本。</span><span class="sxs-lookup"><span data-stu-id="88c0e-120">Modifying the values in the input files, or the values retrieved from the input files, makes it possible to change the deployment destination, the configuration settings, and deployment options without editing the whole \<*project name*>.asdatabase file (or a whole XMLA script file if you generate a script from an existing [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database).</span></span> <span data-ttu-id="88c0e-121">能够修改各个文件使您可以轻松地创建用于不同用途的不同部署脚本。</span><span class="sxs-lookup"><span data-stu-id="88c0e-121">Being able to modify individual files lets you easily create different deployment scripts for different purposes.</span></span>  
  
 <span data-ttu-id="88c0e-122">以下主题解释了如何修改各个输入文件中的值：</span><span class="sxs-lookup"><span data-stu-id="88c0e-122">The following topics explain how to modify values in the various input files:</span></span>  
  
-   [<span data-ttu-id="88c0e-123">指定安装目标</span><span class="sxs-lookup"><span data-stu-id="88c0e-123">Specifying the Installation Target</span></span>](deployment-script-files-specifying-the-installation-target.md)  
  
-   [<span data-ttu-id="88c0e-124">指定分区和角色部署选项</span><span class="sxs-lookup"><span data-stu-id="88c0e-124">Specifying Partition and Role Deployment Options</span></span>](deployment-script-files-partition-and-role-deployment-options.md)  
  
-   [<span data-ttu-id="88c0e-125">为解决方案部署指定配置设置</span><span class="sxs-lookup"><span data-stu-id="88c0e-125">Specifying Configuration Settings for Solution Deployment</span></span>](deployment-script-files-solution-deployment-config-settings.md)  
  
-   [<span data-ttu-id="88c0e-126">指定处理选项</span><span class="sxs-lookup"><span data-stu-id="88c0e-126">Specifying Processing Options</span></span>](deployment-script-files-specifying-processing-options.md)  
  
## <a name="see-also"></a><span data-ttu-id="88c0e-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="88c0e-127">See Also</span></span>  
 <span data-ttu-id="88c0e-128">[运行 Analysis Services 部署向导](running-the-analysis-services-deployment-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="88c0e-128">[Running the Analysis Services Deployment Wizard](running-the-analysis-services-deployment-wizard.md) </span></span>  
 [<span data-ttu-id="88c0e-129">了解 Analysis Services 部署脚本</span><span class="sxs-lookup"><span data-stu-id="88c0e-129">Understanding the Analysis Services Deployment Script</span></span>](understanding-the-analysis-services-deployment-script.md)  
  
  
