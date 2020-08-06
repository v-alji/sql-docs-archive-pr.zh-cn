---
title: 指定处理选项 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Analysis Services deployments, processing options
- input files [Analysis Services]
- deploying [Analysis Services], processing options
- modifying processing options
- Analysis Services Deployment Wizard, processing options
ms.assetid: e9e50817-908e-4210-bc3d-8e2957568241
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9690aaa7e1d3b3870eb6ab01630b98027263655f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687284"
---
# <a name="specifying-processing-options"></a><span data-ttu-id="83c36-102">指定处理选项</span><span class="sxs-lookup"><span data-stu-id="83c36-102">Specifying Processing Options</span></span>
  <span data-ttu-id="83c36-103">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]部署向导从 d 文件中读取处理选项 \<*project name*> 。</span><span class="sxs-lookup"><span data-stu-id="83c36-103">The [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Deployment Wizard reads the processing options from the \<*project name*>.deploymentoptions file.</span></span> [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]<span data-ttu-id="83c36-104">在生成项目时创建此文件 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="83c36-104">creates this file when you build the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project.</span></span> [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]<span data-ttu-id="83c36-105">使用在 "属性页" 对话框的 "**部署**" 页上指定的处理选项 *\<project name>* **Properties Pages**来创建 \<*project name*> d 文件。</span><span class="sxs-lookup"><span data-stu-id="83c36-105">uses the processing options specified on the **Deployment** page of *\<project name>* **Properties Pages** dialog box to create the \<*project name*>.deploymentoptions file.</span></span>  
  
## <a name="reviewing-the-processing-options-for-deployment"></a><span data-ttu-id="83c36-106">检查部署的处理选项</span><span class="sxs-lookup"><span data-stu-id="83c36-106">Reviewing the Processing Options for Deployment</span></span>  
 <span data-ttu-id="83c36-107">D 文件中存储的配置设置如下所示 \<*project name*> ：</span><span class="sxs-lookup"><span data-stu-id="83c36-107">The configuration settings stored within the \<*project name*>.deploymentoptions file are as follows:</span></span>  
  
-   <span data-ttu-id="83c36-108">**处理方法** 此设置将控制在部署后是否处理部署的对象以及将执行的处理的类型。</span><span class="sxs-lookup"><span data-stu-id="83c36-108">**Processing Method** This setting controls whether the deployed objects are processed after deployment and the type of processing that will be performed.</span></span> <span data-ttu-id="83c36-109">有以下三个处理选项：</span><span class="sxs-lookup"><span data-stu-id="83c36-109">There are three processing options:</span></span>  
  
    -   <span data-ttu-id="83c36-110">默认处理（默认值）</span><span class="sxs-lookup"><span data-stu-id="83c36-110">Default processing (default)</span></span>  
  
    -   <span data-ttu-id="83c36-111">完全处理</span><span class="sxs-lookup"><span data-stu-id="83c36-111">Full processing</span></span>  
  
    -   <span data-ttu-id="83c36-112">无</span><span class="sxs-lookup"><span data-stu-id="83c36-112">None</span></span>  
  
-   <span data-ttu-id="83c36-113">**写回表选项** 如果在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 项目中启用了写回，则此设置可定义处理写回的方式。</span><span class="sxs-lookup"><span data-stu-id="83c36-113">**Writeback Table Options** If writeback is enabled in the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project, this setting defines how writeback is handled.</span></span> <span data-ttu-id="83c36-114">有以下三个写回表选项：</span><span class="sxs-lookup"><span data-stu-id="83c36-114">There are three writeback table options:</span></span>  
  
    -   <span data-ttu-id="83c36-115">默认情况下，如果存在写回表，则使用该表。</span><span class="sxs-lookup"><span data-stu-id="83c36-115">By default, if a writeback table exists, it will be used.</span></span> <span data-ttu-id="83c36-116">如果写回表不存在，则将创建一个新的写回表。</span><span class="sxs-lookup"><span data-stu-id="83c36-116">If a writeback table does not exist, a new writeback table will be created.</span></span>  
  
    -   <span data-ttu-id="83c36-117">如果写回表已经存在，则部署失败。</span><span class="sxs-lookup"><span data-stu-id="83c36-117">If a writeback table already exists, the deployment fails.</span></span> <span data-ttu-id="83c36-118">如果写回表不存在，则将创建一个新的写回表。</span><span class="sxs-lookup"><span data-stu-id="83c36-118">If a writeback table does not exist, a new writeback table will be created.</span></span>  
  
    -   <span data-ttu-id="83c36-119">不管写回表是否已存在，都将创建新的写回表。</span><span class="sxs-lookup"><span data-stu-id="83c36-119">Regardless of whether a writeback table already exists, a new writeback table will be created.</span></span> <span data-ttu-id="83c36-120">在这种情况下， [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 部署向导将删除任何现有的表，并用新的写回表来替换现有的表。</span><span class="sxs-lookup"><span data-stu-id="83c36-120">In this case, the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Deployment Wizard will delete any existing table and replace it with a new writeback table.</span></span>  
  
-   <span data-ttu-id="83c36-121">**事务性部署** 此设置控制元数据更改和进程命令的部署是在单个事务中进行还是在多个单独的事务中进行。</span><span class="sxs-lookup"><span data-stu-id="83c36-121">**Transactional Deployment** This setting controls whether the deployment of metadata changes and process commands occurs in a single transaction or in separate transactions.</span></span>  
  
    -   <span data-ttu-id="83c36-122">如果此选项为 `True`（默认值），则 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 将在单个事务中部署所有元数据更改和所有进程命令。</span><span class="sxs-lookup"><span data-stu-id="83c36-122">If this option is `True` (default), [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] deploys all metadata changes and all process commands within a single transaction.</span></span>  
  
    -   <span data-ttu-id="83c36-123">如果此选项为 `False`，则 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 将在单个事务中部署元数据更改，并在其自己的事务中部署每个处理命令。</span><span class="sxs-lookup"><span data-stu-id="83c36-123">If this option is `False`, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] deploys the metadata changes in a single transaction, and deploys each processing command in its own transaction.</span></span>  
  
## <a name="modifying-the-processing-options-for-deployment"></a><span data-ttu-id="83c36-124">修改部署的处理选项</span><span class="sxs-lookup"><span data-stu-id="83c36-124">Modifying the Processing Options for Deployment</span></span>  
 <span data-ttu-id="83c36-125">但是，你可能需要 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 使用与 d 文件中存储的选项不同的处理选项来部署项目 \<*project name*> 。</span><span class="sxs-lookup"><span data-stu-id="83c36-125">However, you may need to deploy the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project using different processing options than those stored in the \<*project name*>.deploymentoptions file.</span></span> <span data-ttu-id="83c36-126">例如，您也可能要完全处理所有对象，使用默认处理选项进行处理，也可不进行任何处理。</span><span class="sxs-lookup"><span data-stu-id="83c36-126">For example, you may want to have all objects fully processed, or processed using the default processing option, or have no processing occur.</span></span> <span data-ttu-id="83c36-127">如果多维数据集或维度启用了写操作，则可以指定是使用新的写回表还是现有的写回表。</span><span class="sxs-lookup"><span data-stu-id="83c36-127">If the cubes or dimensions are write-enabled, you can specify whether a new or existing writeback table be used.</span></span>  
  
 <span data-ttu-id="83c36-128">若要修改部署过程中使用的处理选项，可以编辑和重新生成项目，也可以通过使用下列步骤中介绍的方法之一来更改输入文件中的处理选项。</span><span class="sxs-lookup"><span data-stu-id="83c36-128">To modify the processing options used during deployment, you can either edit and rebuild the project, or change the processing options in the input file by using one of the methods as described in the following procedure.</span></span>  
  
#### <a name="to-change-processing-options-after-the-input-files-have-been-generated"></a><span data-ttu-id="83c36-129">在生成输入文件后更改处理选项</span><span class="sxs-lookup"><span data-stu-id="83c36-129">To change processing options after the input files have been generated</span></span>  
  
-   <span data-ttu-id="83c36-130">以交互方式运行 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 部署向导。</span><span class="sxs-lookup"><span data-stu-id="83c36-130">Run the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Deployment Wizard interactively.</span></span> <span data-ttu-id="83c36-131">在 **“处理选项”** 页上，为要部署的项目指定处理选项。</span><span class="sxs-lookup"><span data-stu-id="83c36-131">On the **Processing Options** page, specify the processing options for the project being deployed.</span></span>  
  
     <span data-ttu-id="83c36-132">- 或 -</span><span class="sxs-lookup"><span data-stu-id="83c36-132">-or-</span></span>  
  
-   <span data-ttu-id="83c36-133">在命令提示符下运行 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 部署向导，并设置向导，使其以应答文件模式运行。</span><span class="sxs-lookup"><span data-stu-id="83c36-133">Run the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Deployment Wizard at the command prompt and set the wizard to run in answer file mode.</span></span> <span data-ttu-id="83c36-134">有关应答文件模式的详细信息，请参阅 [Running the Analysis Services Deployment Wizard](running-the-analysis-services-deployment-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="83c36-134">For more information about answer file mode, see [Running the Analysis Services Deployment Wizard](running-the-analysis-services-deployment-wizard.md).</span></span>  
  
     <span data-ttu-id="83c36-135">- 或 -</span><span class="sxs-lookup"><span data-stu-id="83c36-135">-or-</span></span>  
  
-   <span data-ttu-id="83c36-136">\<*project name*>使用任意文本编辑器修改 d 文件。</span><span class="sxs-lookup"><span data-stu-id="83c36-136">Modify the \<*project name*>.deploymentoptions file by using any text editor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83c36-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="83c36-137">See Also</span></span>  
 <span data-ttu-id="83c36-138">[指定安装目标](deployment-script-files-specifying-the-installation-target.md) </span><span class="sxs-lookup"><span data-stu-id="83c36-138">[Specifying the Installation Target](deployment-script-files-specifying-the-installation-target.md) </span></span>  
 <span data-ttu-id="83c36-139">[指定分区和角色部署选项](deployment-script-files-partition-and-role-deployment-options.md) </span><span class="sxs-lookup"><span data-stu-id="83c36-139">[Specifying Partition and Role Deployment Options](deployment-script-files-partition-and-role-deployment-options.md) </span></span>  
 [<span data-ttu-id="83c36-140">为解决方案部署指定配置设置</span><span class="sxs-lookup"><span data-stu-id="83c36-140">Specifying Configuration Settings for Solution Deployment</span></span>](deployment-script-files-solution-deployment-config-settings.md)  
  
  
