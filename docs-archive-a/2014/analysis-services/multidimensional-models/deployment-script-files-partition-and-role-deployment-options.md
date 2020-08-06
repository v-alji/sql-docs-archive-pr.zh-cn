---
title: 指定分区和角色部署选项 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- input files [Analysis Services]
- partitions [Analysis Services], deployment options
- Analysis Services deployments, roles
- Analysis Services deployments, partitions
- Analysis Services Deployment Wizard, roles
- Analysis Services Deployment Wizard, partitions
- deploying [Analysis Services], roles
- roles [Analysis Services], deployment options
- deploying [Analysis Services], partitions
- modifying role deployments
- modifying partition deployments
ms.assetid: e9b9ca57-a5cc-4fc0-87b5-305257038d56
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8c8dd7bcb482c2d28a18e3039f5acb777b121202
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590394"
---
# <a name="specifying-partition-and-role-deployment-options"></a><span data-ttu-id="e2472-102">指定分区和角色部署选项</span><span class="sxs-lookup"><span data-stu-id="e2472-102">Specifying Partition and Role Deployment Options</span></span>
  <span data-ttu-id="e2472-103">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]部署向导从 d 文件中读取分区和角色部署选项 \<*project name*> 。</span><span class="sxs-lookup"><span data-stu-id="e2472-103">The [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Deployment Wizard reads the partition and role deployment options from the \<*project name*>.deploymentoptions file.</span></span> [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]<span data-ttu-id="e2472-104">在生成项目时创建此文件 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="e2472-104">creates this file when you build the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project.</span></span> [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]<span data-ttu-id="e2472-105">当创建 d 文件时，使用当前项目的分区和角色部署选项 \<*project name*> 。</span><span class="sxs-lookup"><span data-stu-id="e2472-105">uses the partition and role deployment options of the current project when the \<*project name*>.deploymentoptions file is created.</span></span> <span data-ttu-id="e2472-106">有关配置设置的详细信息，请参阅 [Understanding the Input Files Used to Create the Deployment Script](deployment-script-files-input-used-to-create-deployment-script.md)。</span><span class="sxs-lookup"><span data-stu-id="e2472-106">For more information about configuration settings, see [Understanding the Input Files Used to Create the Deployment Script](deployment-script-files-input-used-to-create-deployment-script.md).</span></span>  
  
## <a name="reviewing-the-partition-and-role-deployment-options"></a><span data-ttu-id="e2472-107">检查分区和角色部署选项</span><span class="sxs-lookup"><span data-stu-id="e2472-107">Reviewing the Partition and Role Deployment Options</span></span>  
 <span data-ttu-id="e2472-108">D 文件中的部署选项 \<*project name*> 包括以下各项：</span><span class="sxs-lookup"><span data-stu-id="e2472-108">The deployment options in the \<*project name*>.deploymentoptions file include the following:</span></span>  
  
 <span data-ttu-id="e2472-109">**分区部署选项**</span><span class="sxs-lookup"><span data-stu-id="e2472-109">**Partition deployment options**</span></span>  
 <span data-ttu-id="e2472-110">\<*project name*>D 文件指定是否保留或覆盖目标数据库中的现有分区 (默认) 。</span><span class="sxs-lookup"><span data-stu-id="e2472-110">The \<*project name*>.deploymentoptions file specifies whether existing partitions in the destination database are retained or overwritten (default).</span></span> <span data-ttu-id="e2472-111">如果保留现有分区，则仅部署新的分区，所有现有度量值组的分区和聚合设计均保持不变。</span><span class="sxs-lookup"><span data-stu-id="e2472-111">If existing partitions are retained, only new partitions will be deployed, and the partitions and aggregation designs on all existing measure groups are left unchanged.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e2472-112">如果删除了分区所在的度量值组，则自动删除该分区。</span><span class="sxs-lookup"><span data-stu-id="e2472-112">If the measure group in which the partition exists is deleted, the partition is automatically deleted.</span></span>  
  
 <span data-ttu-id="e2472-113">**角色部署选项**</span><span class="sxs-lookup"><span data-stu-id="e2472-113">**Role deployment options**</span></span>  
 <span data-ttu-id="e2472-114">\<*project name*>D 文件指定下列角色部署选项之一：</span><span class="sxs-lookup"><span data-stu-id="e2472-114">The \<*project name*>.deploymentoptions file specifies one of the following role deployment options:</span></span>  
  
-   <span data-ttu-id="e2472-115">保留目标数据库中现有的角色和角色成员，仅部署新的角色和角色成员。</span><span class="sxs-lookup"><span data-stu-id="e2472-115">Existing roles and role members in the destination database are retained, and only new roles and role members are deployed.</span></span>  
  
-   <span data-ttu-id="e2472-116">目标数据库中所有现有的角色和成员将被当前部署的角色和成员替换。</span><span class="sxs-lookup"><span data-stu-id="e2472-116">All existing roles and members in the destination database are replaced by the roles and members being deployed.</span></span>  
  
-   <span data-ttu-id="e2472-117">保留目标数据库中现有的角色和角色成员，不部署任何新的角色。</span><span class="sxs-lookup"><span data-stu-id="e2472-117">Existing roles and role members in the destination database are retained, and no new roles are deployed.</span></span>  
  
-   <span data-ttu-id="e2472-118">**请注意** 保留现有角色和成员时，与这些角色关联的权限将重置为无。</span><span class="sxs-lookup"><span data-stu-id="e2472-118">**Note** When existing roles and members are retained, the permissions associated with those roles are reset to none.</span></span> <span data-ttu-id="e2472-119">安全权限包含在这些权限保护的对象中，而非包含在与这些权限关联的安全角色中。</span><span class="sxs-lookup"><span data-stu-id="e2472-119">Security permissions are contained by the objects they secure, not by the security roles with which they are associated.</span></span> <span data-ttu-id="e2472-120">有关如何通过使用 Analysis Services 部署向导来处理此行为的详细信息，请参阅 Microsoft 知识库中的 "保留角色和成员"。</span><span class="sxs-lookup"><span data-stu-id="e2472-120">For more information about how to work with this behavior by using the Analysis Service Deployment Wizard, see 'Retain Roles and Members' in the Microsoft Knowledge Base.</span></span>  
  
## <a name="modifying-the-partition-and-role-deployment-options"></a><span data-ttu-id="e2472-121">修改分区和角色部署选项</span><span class="sxs-lookup"><span data-stu-id="e2472-121">Modifying the Partition and Role Deployment Options</span></span>  
 <span data-ttu-id="e2472-122">可能需要 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 使用不同于 d 文件中存储的分区和角色选项来部署项目 \<*project name*> 。</span><span class="sxs-lookup"><span data-stu-id="e2472-122">You may have to deploy the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project using different partition and role options than those stored in the \<*project name*>.deploymentoptions file.</span></span> <span data-ttu-id="e2472-123">例如，你可能想要保留现有的分区、角色和角色成员，而不是替换 d 文件中所示的所有现有分区、角色和成员。 \<*project name*></span><span class="sxs-lookup"><span data-stu-id="e2472-123">For example, you may want to retain existing partitions, roles, and role members, instead of replacing all existing partitions, roles, and members as indicated in the \<*project name*>.deploymentoptions file.</span></span>  
  
 <span data-ttu-id="e2472-124">若要在项目中修改分区和角色的部署 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ，您不能在项目中更改分区和角色设置，因为中的 " *\<project name>* **属性页**" 对话框 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 不会显示这些选项。</span><span class="sxs-lookup"><span data-stu-id="e2472-124">To modify the deployment of partitions and roles in an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project, you cannot change the partition and roles settings within the project because the *\<project name>* **Properties Pages** dialog box in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] does not display these options.</span></span> <span data-ttu-id="e2472-125">如果要更改角色和分区的部署选项，则必须在 d 文件本身中更改此信息 \<*project name*> 。</span><span class="sxs-lookup"><span data-stu-id="e2472-125">If you want to change the deployment options for roles and partitions, you must change this information within the \<*project name*>.deploymentoptions file itself.</span></span> <span data-ttu-id="e2472-126">下面的过程介绍如何更改 d 文件中的分区和角色部署选项 \<*project name*> 。</span><span class="sxs-lookup"><span data-stu-id="e2472-126">The following procedure describes how to change the partition and role deployment options within the \<*project name*>.deploymentoptions file.</span></span>  
  
#### <a name="to-change-the-deployment-of-partitions-or-roles-after-the-input-files-have-been-generated"></a><span data-ttu-id="e2472-127">在生成了输入文件后更改分区或角色的部署</span><span class="sxs-lookup"><span data-stu-id="e2472-127">To change the deployment of partitions or roles after the input files have been generated</span></span>  
  
-   <span data-ttu-id="e2472-128">以交互方式运行 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 部署向导，然后在 **“分区和角色部署选项”** 页上，为分区和角色指定新的部署选项。</span><span class="sxs-lookup"><span data-stu-id="e2472-128">Run the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Deployment Wizard interactively, and on the **Partition and Role Deployment Options** page, specify new deployment options for the partitions and roles.</span></span>  
  
     <span data-ttu-id="e2472-129">- 或 -</span><span class="sxs-lookup"><span data-stu-id="e2472-129">-or-</span></span>  
  
-   <span data-ttu-id="e2472-130">在命令提示符下运行 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 部署向导，并将该向导设置为以应答文件模式运行。</span><span class="sxs-lookup"><span data-stu-id="e2472-130">Run the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Deployment Wizard at the command prompt, and set the wizard to run in answer file mode.</span></span> <span data-ttu-id="e2472-131"> (有关应答文件模式的详细信息，请参阅[运行 Analysis Services 部署向导](running-the-analysis-services-deployment-wizard.md)。 ) </span><span class="sxs-lookup"><span data-stu-id="e2472-131">(For more information about answer file mode, see [Running the Analysis Services Deployment Wizard](running-the-analysis-services-deployment-wizard.md).)</span></span>  
  
     <span data-ttu-id="e2472-132">- 或 -</span><span class="sxs-lookup"><span data-stu-id="e2472-132">-or-</span></span>  
  
-   <span data-ttu-id="e2472-133">\<*project name*>在任何文本编辑器中打开 d，并手动更改选项。</span><span class="sxs-lookup"><span data-stu-id="e2472-133">Open the \<*project name*>.deploymentoptions in any text editor and manually change the options.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2472-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e2472-134">See Also</span></span>  
 <span data-ttu-id="e2472-135">[指定安装目标](deployment-script-files-specifying-the-installation-target.md) </span><span class="sxs-lookup"><span data-stu-id="e2472-135">[Specifying the Installation Target](deployment-script-files-specifying-the-installation-target.md) </span></span>  
 <span data-ttu-id="e2472-136">[为解决方案部署指定配置设置](deployment-script-files-solution-deployment-config-settings.md) </span><span class="sxs-lookup"><span data-stu-id="e2472-136">[Specifying Configuration Settings for Solution Deployment](deployment-script-files-solution-deployment-config-settings.md) </span></span>  
 [<span data-ttu-id="e2472-137">指定处理选项</span><span class="sxs-lookup"><span data-stu-id="e2472-137">Specifying Processing Options</span></span>](deployment-script-files-specifying-processing-options.md)  
  
  
