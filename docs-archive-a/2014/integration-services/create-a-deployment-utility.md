---
title: 创建部署实用工具 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- deploying packages [Integration Services], deployment utility
- deployment utility [Integration Services]
ms.assetid: 354322a4-ae8c-4d92-8e71-42d29dbd0614
author: chugugrace
ms.author: chugu
ms.openlocfilehash: bdf1328d440920fed98e5fa1d16024c5fec32cbb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587533"
---
# <a name="create-a-deployment-utility"></a><span data-ttu-id="a17cc-102">Create a Deployment Utility</span><span class="sxs-lookup"><span data-stu-id="a17cc-102">Create a Deployment Utility</span></span>
  <span data-ttu-id="a17cc-103">部署包的第一步是为 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目创建一个部署实用工具。</span><span class="sxs-lookup"><span data-stu-id="a17cc-103">The first step in deploying packages is to create a deployment utility for an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project.</span></span> <span data-ttu-id="a17cc-104">部署实用工具是一个文件夹，其中包含在不同服务器上部署 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目中的包所需的文件。</span><span class="sxs-lookup"><span data-stu-id="a17cc-104">The deployment utility is a folder that contains the files you need to deploy the packages in an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project on a different server.</span></span> <span data-ttu-id="a17cc-105">部署实用工具是在存储 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目的计算机上创建的。</span><span class="sxs-lookup"><span data-stu-id="a17cc-105">The deployment utility is created on the computer on which the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project is stored.</span></span>  
  
 <span data-ttu-id="a17cc-106">通过首先配置创建部署实用工具的生成过程，然后生成 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目，可以为该项目创建一个包部署实用工具。</span><span class="sxs-lookup"><span data-stu-id="a17cc-106">You create a package deployment utility for an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project by first configuring the build process to create a deployment utility, and then building the project.</span></span> <span data-ttu-id="a17cc-107">在生成项目时，将自动包括项目中的所有包和包配置。</span><span class="sxs-lookup"><span data-stu-id="a17cc-107">When you build the project, all packages and package configurations in the project are automatically included.</span></span> <span data-ttu-id="a17cc-108">若要部署其他文件（如项目的自述文件），请将这些文件放在 **项目的** “杂项” [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 文件夹中。</span><span class="sxs-lookup"><span data-stu-id="a17cc-108">To deploy additional files such as a Readme file with the project, place the files in the **Miscellaneous** folder of the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project.</span></span> <span data-ttu-id="a17cc-109">当生成项目时，也会自动包括这些文件。</span><span class="sxs-lookup"><span data-stu-id="a17cc-109">When the project is built, these files are also automatically included.</span></span>  
  
 <span data-ttu-id="a17cc-110">您可以按照不同的方式配置每个项目部署。</span><span class="sxs-lookup"><span data-stu-id="a17cc-110">You can configure each project deployment differently.</span></span> <span data-ttu-id="a17cc-111">在生成项目和创建包部署实用工具之前，您可以设置部署实用工具的属性，自定义项目中包的部署方法。</span><span class="sxs-lookup"><span data-stu-id="a17cc-111">Before you build the project and create the package deployment utility, you can set the properties on the deployment utility to customize the way the packages in the project will be deployed.</span></span> <span data-ttu-id="a17cc-112">例如，您可以指定在部署项目时是否可以更新包配置。</span><span class="sxs-lookup"><span data-stu-id="a17cc-112">For example, you can specify whether package configurations can be updated when the project is deployed.</span></span> <span data-ttu-id="a17cc-113">若要访问 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目的属性，请右键单击该项目，再单击  “属性”。</span><span class="sxs-lookup"><span data-stu-id="a17cc-113">To access the properties of an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project, right-click the project and click **Properties**.</span></span>  
  
 <span data-ttu-id="a17cc-114">下表列出了部署实用工具属性。</span><span class="sxs-lookup"><span data-stu-id="a17cc-114">The following table lists the deployment utility properties.</span></span>  
  
|<span data-ttu-id="a17cc-115">properties</span><span class="sxs-lookup"><span data-stu-id="a17cc-115">Property</span></span>|<span data-ttu-id="a17cc-116">说明</span><span class="sxs-lookup"><span data-stu-id="a17cc-116">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="a17cc-117">AllowConfigurationChange</span><span class="sxs-lookup"><span data-stu-id="a17cc-117">AllowConfigurationChange</span></span>|<span data-ttu-id="a17cc-118">一个指定在部署过程中是否可以更新配置的值。</span><span class="sxs-lookup"><span data-stu-id="a17cc-118">A value that specifies whether configurations can be updated during deployment.</span></span>|  
|<span data-ttu-id="a17cc-119">CreateDeploymentUtility</span><span class="sxs-lookup"><span data-stu-id="a17cc-119">CreateDeploymentUtility</span></span>|<span data-ttu-id="a17cc-120">一个指定在生成项目时是否创建包部署实用工具的值。</span><span class="sxs-lookup"><span data-stu-id="a17cc-120">A value that specifies whether a package deployment utility is created when the project is built.</span></span> <span data-ttu-id="a17cc-121">此属性必须为 `True` 才能创建部署实用工具。</span><span class="sxs-lookup"><span data-stu-id="a17cc-121">This property must be `True` to create a deployment utility.</span></span>|  
|<span data-ttu-id="a17cc-122">DeploymentOutputPath</span><span class="sxs-lookup"><span data-stu-id="a17cc-122">DeploymentOutputPath</span></span>|<span data-ttu-id="a17cc-123">部署实用工具的位置，相对于 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目。</span><span class="sxs-lookup"><span data-stu-id="a17cc-123">The location, relative to the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project, of the deployment utility.</span></span>|  
  
 <span data-ttu-id="a17cc-124">在生成 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目时，除了创建项目包的副本和包依赖项外，还会创建一个清单文件 \<project name>.SSISDeploymentManifest.xml，并将它们都添加到项目的 bin\Deployment 文件夹中，或添加到 DeploymentOutputPath 属性中所指定的位置。</span><span class="sxs-lookup"><span data-stu-id="a17cc-124">When you build an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project, a manifest file, \<project name>.SSISDeploymentManifest.xml, is created and added, together with copies of the project packages and package dependencies, to the bin\Deployment folder in the project, or to the location specified in the DeploymentOutputPath property.</span></span> <span data-ttu-id="a17cc-125">该清单文件列出了项目中的包、包配置和所有杂项文件。</span><span class="sxs-lookup"><span data-stu-id="a17cc-125">The manifest file lists the packages, the package configurations, and any miscellaneous files in the project.</span></span>  
  
 <span data-ttu-id="a17cc-126">每次生成项目时将刷新部署文件夹的内容。</span><span class="sxs-lookup"><span data-stu-id="a17cc-126">The content of the deployment folder is refreshed every time that you build the project.</span></span> <span data-ttu-id="a17cc-127">这意味着系统将删除所有已保存到此文件夹中但未由生成进程再次复制到该文件夹中的文件。</span><span class="sxs-lookup"><span data-stu-id="a17cc-127">This means that any file saved to this folder that is not copied to the folder again by the build process will be deleted.</span></span> <span data-ttu-id="a17cc-128">例如，将删除保存到部署文件夹中的包配置文件。</span><span class="sxs-lookup"><span data-stu-id="a17cc-128">For example, package configuration files saved to the deployment folders will be deleted.</span></span>  
  
### <a name="to-create-a-package-deployment-utility"></a><span data-ttu-id="a17cc-129">创建包部署实用工具</span><span class="sxs-lookup"><span data-stu-id="a17cc-129">To create a package deployment utility</span></span>  
  
1.  <span data-ttu-id="a17cc-130">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，打开包含要为其创建包部署实用工具的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目的解决方案。</span><span class="sxs-lookup"><span data-stu-id="a17cc-130">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the solution that contains the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project for which you want to create a package deployment utility.</span></span>  
  
2.  <span data-ttu-id="a17cc-131">右键单击该项目，再单击“属性”  。</span><span class="sxs-lookup"><span data-stu-id="a17cc-131">Right-click the project and click **Properties**.</span></span>  
  
3.  <span data-ttu-id="a17cc-132">在“\<project name> 属性页”对话框中，单击“部署实用工具” 。</span><span class="sxs-lookup"><span data-stu-id="a17cc-132">In the **\<project name> Property Pages** dialog box, click **Deployment Utility**.</span></span>  
  
4.  <span data-ttu-id="a17cc-133">若要在部署包时更新包配置，请将**AllowConfigurationChanges**设置为 `True` 。</span><span class="sxs-lookup"><span data-stu-id="a17cc-133">To update package configurations when packages are deployed, set **AllowConfigurationChanges** to `True`.</span></span>  
  
5.  <span data-ttu-id="a17cc-134">将 `CreateDeploymentUtility` 设置为 `True`。</span><span class="sxs-lookup"><span data-stu-id="a17cc-134">Set `CreateDeploymentUtility` to `True`.</span></span>  
  
6.  <span data-ttu-id="a17cc-135">还可以通过修改 `DeploymentOutputPath` 属性来更新部署实用工具的位置。</span><span class="sxs-lookup"><span data-stu-id="a17cc-135">Optionally, update the location of the deployment utility by modifying the `DeploymentOutputPath` property.</span></span>  
  
7.  <span data-ttu-id="a17cc-136">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="a17cc-136">Click **OK**.</span></span>  
  
8.  <span data-ttu-id="a17cc-137">在解决方案资源管理器中，右键单击该项目，再单击  “生成”。</span><span class="sxs-lookup"><span data-stu-id="a17cc-137">In Solution Explorer, right-click the project, and then click **Build**.</span></span>  
  
9. <span data-ttu-id="a17cc-138">在 **“输出”** 窗口中查看生成进度和生成错误。</span><span class="sxs-lookup"><span data-stu-id="a17cc-138">View the build progress and build errors in the **Output** window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a17cc-139">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a17cc-139">See Also</span></span>  
 <span data-ttu-id="a17cc-140">[包配置](../../2014/integration-services/package-configurations.md) </span><span class="sxs-lookup"><span data-stu-id="a17cc-140">[Package Configurations](../../2014/integration-services/package-configurations.md) </span></span>  
 <span data-ttu-id="a17cc-141">[创建包配置](../../2014/integration-services/create-package-configurations.md) </span><span class="sxs-lookup"><span data-stu-id="a17cc-141">[Create Package Configurations](../../2014/integration-services/create-package-configurations.md) </span></span>  
 <span data-ttu-id="a17cc-142">[使用部署实用工具部署包](../../2014/integration-services/deploy-packages-by-using-the-deployment-utility.md) </span><span class="sxs-lookup"><span data-stu-id="a17cc-142">[Deploy Packages by Using the Deployment Utility](../../2014/integration-services/deploy-packages-by-using-the-deployment-utility.md) </span></span>  
 [<span data-ttu-id="a17cc-143">包部署 &#40;SSIS&#41;</span><span class="sxs-lookup"><span data-stu-id="a17cc-143">Package Deployment &#40;SSIS&#41;</span></span>](packages/legacy-package-deployment-ssis.md)  
  
  
