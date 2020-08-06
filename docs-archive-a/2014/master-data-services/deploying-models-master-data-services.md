---
title: 部署模型 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- deployment packages [Master Data Services], about deployment packages
- deployment packages [Master Data Services]
ms.assetid: 30085c08-034f-4efe-80fe-408f9091ff5c
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: a9cc99112ec874e89ae07faa575235d9a041a972
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591930"
---
# <a name="deploying-models-master-data-services"></a><span data-ttu-id="2e647-102">部署模型 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="2e647-102">Deploying Models (Master Data Services)</span></span>
  <span data-ttu-id="2e647-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，包是包含可部署模型结构以及来自模型的数据（可选）的 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="2e647-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], a package is an XML file that contains a deployable model structure, and optionally, data from the model.</span></span> <span data-ttu-id="2e647-104">使用模型包可以将模型的副本从一个 MDS 环境移到另一个环境，或者在现有的 MDS 环境中创建新模型。</span><span class="sxs-lookup"><span data-stu-id="2e647-104">Use model packages to move copies of models from one MDS environment to another, or to create new models in your existing MDS environment.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="2e647-105">包只能部署到创建它们的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 版本中。</span><span class="sxs-lookup"><span data-stu-id="2e647-105">Packages can be deployed to the edition of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] they were created in only.</span></span> <span data-ttu-id="2e647-106">这意味着在 [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] 中创建的包不能部署到 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="2e647-106">This means that packages created in [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] cannot be deployed to [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] or higher.</span></span>  
  
## <a name="tools-for-deploying-models"></a><span data-ttu-id="2e647-107">用于部署模型的工具</span><span class="sxs-lookup"><span data-stu-id="2e647-107">Tools for Deploying Models</span></span>  
 <span data-ttu-id="2e647-108">若要使用模型包，您可以根据需要使用以下三个工具之一。</span><span class="sxs-lookup"><span data-stu-id="2e647-108">To work with model packages, you can use one of three tools, depending on your needs.</span></span>  
  
-   <span data-ttu-id="2e647-109">**MDSModelDeploy 工具**：若要创建和部署模型对象和数据，请使用 MDSModelDeploy.exe 工具。</span><span class="sxs-lookup"><span data-stu-id="2e647-109">**MDSModelDeploy tool**: To create and deploy model objects and data, use the MDSModelDeploy.exe tool.</span></span> <span data-ttu-id="2e647-110">如果你在安装 MDS 时选择了默认路径，则该工具位于*驱动器*： \PROGRAM Files\Microsoft SQL Server\120\Master Data services\configuration。</span><span class="sxs-lookup"><span data-stu-id="2e647-110">If you selected the default path when installing MDS, this tool is located on *drive*:\Program Files\Microsoft SQL Server\120\Master Data Services\Configuration.</span></span>  
  
-   <span data-ttu-id="2e647-111">**模型部署向导**：若要创建和部署仅包含模型结构的包，请使用 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Web 应用程序中的向导。</span><span class="sxs-lookup"><span data-stu-id="2e647-111">**Model Deployment wizard**: To create and deploy packages of the model structure only, use the wizard in the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] web application.</span></span> <span data-ttu-id="2e647-112">您不能使用此向导来部署数据。</span><span class="sxs-lookup"><span data-stu-id="2e647-112">You cannot use this wizard to deploy data.</span></span>  
  
-   <span data-ttu-id="2e647-113">**模型包编辑器**：若要编辑模型包，请使用启动模型包编辑器向导的 ModelPackageEditor.exe。</span><span class="sxs-lookup"><span data-stu-id="2e647-113">**Model Package Editor**: To edit a model package, use the ModelPackageEditor.exe that launches the Model Package Editor wizard.</span></span> <span data-ttu-id="2e647-114">您可以使用此向导来编辑由 MDSModelDeploy 工具或模型部署向导创建的包。</span><span class="sxs-lookup"><span data-stu-id="2e647-114">You use this wizard to edit a package that was created by the MDSModelDeploy tool or the Model Deployment wizard.</span></span> <span data-ttu-id="2e647-115">如果你在安装 MDS 时选择了默认路径，则该工具位于*驱动器*： \PROGRAM Files\Microsoft SQL Server\120\Master Data services\configuration。</span><span class="sxs-lookup"><span data-stu-id="2e647-115">If you selected the default path when installing MDS, this tool is located on *drive*:\Program Files\Microsoft SQL Server\120\Master Data Services\Configuration.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="2e647-116">可以使用 MDSDeployModel 创建新模型、创建模型的克隆或更新现有模型及其数据。</span><span class="sxs-lookup"><span data-stu-id="2e647-116">You can use the MDSDeployModel to create a new model, create a clone of a model, or update an existing model and its data.</span></span> <span data-ttu-id="2e647-117">如果使用 MDSModelDeploy 工具更新现有模型及其数据，并且该包不包含目标模型中存在的实体、属性或成员，则 MDSModelDeploy 不会从模型中删除此实体、属性或成员。</span><span class="sxs-lookup"><span data-stu-id="2e647-117">If you use the MDSModelDeploy tool to update an existing model and its data, and the package does not contain an entity, attribute, or member that exists in the destination model, MDSModelDeploy will not delete that entity, attribute, or member from the model.</span></span>  
  
## <a name="what-packages-contain"></a><span data-ttu-id="2e647-118">包所包含的内容</span><span class="sxs-lookup"><span data-stu-id="2e647-118">What Packages Contain</span></span>  
 <span data-ttu-id="2e647-119">模型包是使用 .pkg 扩展名进行保存的 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="2e647-119">A model package is an XML file that is saved with the .pkg extension.</span></span> <span data-ttu-id="2e647-120">在您创建部署包时，可以决定是否包括数据。</span><span class="sxs-lookup"><span data-stu-id="2e647-120">When you create a deployment package, you can decide whether or not to include data.</span></span> <span data-ttu-id="2e647-121">如果决定包括数据，则必须选择要包括的数据。</span><span class="sxs-lookup"><span data-stu-id="2e647-121">If you decide to include data, you must select a version of the data to include.</span></span>  
  
 <span data-ttu-id="2e647-122">所有模型对象都包括在一个包中。</span><span class="sxs-lookup"><span data-stu-id="2e647-122">All model objects are included in a package.</span></span> <span data-ttu-id="2e647-123">这些对象是：</span><span class="sxs-lookup"><span data-stu-id="2e647-123">These objects are:</span></span>  
  
-   <span data-ttu-id="2e647-124">实体</span><span class="sxs-lookup"><span data-stu-id="2e647-124">Entities</span></span>  
  
-   <span data-ttu-id="2e647-125">属性</span><span class="sxs-lookup"><span data-stu-id="2e647-125">Attributes</span></span>  
  
-   <span data-ttu-id="2e647-126">特性组</span><span class="sxs-lookup"><span data-stu-id="2e647-126">Attribute groups</span></span>  
  
-   <span data-ttu-id="2e647-127">层次结构</span><span class="sxs-lookup"><span data-stu-id="2e647-127">Hierarchies</span></span>  
  
-   <span data-ttu-id="2e647-128">集合</span><span class="sxs-lookup"><span data-stu-id="2e647-128">Collections</span></span>  
  
-   <span data-ttu-id="2e647-129">业务规则</span><span class="sxs-lookup"><span data-stu-id="2e647-129">Business rules</span></span>  
  
-   <span data-ttu-id="2e647-130">版本标志</span><span class="sxs-lookup"><span data-stu-id="2e647-130">Version flags</span></span>  
  
-   <span data-ttu-id="2e647-131">订阅视图</span><span class="sxs-lookup"><span data-stu-id="2e647-131">Subscription views</span></span>  
  
 <span data-ttu-id="2e647-132">不包括用户定义元数据、文件属性以及用户和组权限。</span><span class="sxs-lookup"><span data-stu-id="2e647-132">User-defined metadata, file attributes, and user and group permissions are not included.</span></span> <span data-ttu-id="2e647-133">在您部署模型后，必须手动更新这些内容。</span><span class="sxs-lookup"><span data-stu-id="2e647-133">After you deploy a model, you must update these manually.</span></span>  
  
## <a name="sample-packages"></a><span data-ttu-id="2e647-134">示例包</span><span class="sxs-lookup"><span data-stu-id="2e647-134">Sample Packages</span></span>  
 <span data-ttu-id="2e647-135">在您安装 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]时将包括示例包文件。</span><span class="sxs-lookup"><span data-stu-id="2e647-135">Sample package files are included when you install [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)].</span></span> <span data-ttu-id="2e647-136">这些包文件位于安装了 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]的 Master Data Services\Samples\Packages 目录中。</span><span class="sxs-lookup"><span data-stu-id="2e647-136">These package files are in the Master Data Services\Samples\Packages directory where you installed [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)].</span></span> <span data-ttu-id="2e647-137">在使用 MDSModelDeploy 工具部署这些示例包时，将创建并使用数据填充示例模型。</span><span class="sxs-lookup"><span data-stu-id="2e647-137">When you deploy these sample packages by using the MDSModelDeploy tool, sample models are created and populated with data.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="2e647-138">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="2e647-138">Related Tasks</span></span>  
  
|<span data-ttu-id="2e647-139">任务说明</span><span class="sxs-lookup"><span data-stu-id="2e647-139">Task Description</span></span>|<span data-ttu-id="2e647-140">主题</span><span class="sxs-lookup"><span data-stu-id="2e647-140">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="2e647-141">通过使用 MDSModelDeploy 工具创建模型对象和/或数据的新的部署包。</span><span class="sxs-lookup"><span data-stu-id="2e647-141">Create a new deployment package of model objects and/or data by using the MDSModelDeploy tool.</span></span>|[<span data-ttu-id="2e647-142">使用 MDSModelDeploy 创建模型部署包</span><span class="sxs-lookup"><span data-stu-id="2e647-142">Create a Model Deployment Package by Using MDSModelDeploy</span></span>](../../2014/master-data-services/create-a-model-deployment-package-by-using-mdsmodeldeploy.md)|  
|<span data-ttu-id="2e647-143">通过使用向导创建只包含模型对象的新的部署包。</span><span class="sxs-lookup"><span data-stu-id="2e647-143">Create a new deployment package of model objects only by using the wizard.</span></span>|[<span data-ttu-id="2e647-144">使用向导创建模型部署包</span><span class="sxs-lookup"><span data-stu-id="2e647-144">Create a Model Deployment Package by Using the Wizard</span></span>](../../2014/master-data-services/create-a-model-deployment-package-by-using-the-wizard.md)|  
|<span data-ttu-id="2e647-145">通过使用 MDSModelDeploy 工具部署包含模型对象和数据的包。</span><span class="sxs-lookup"><span data-stu-id="2e647-145">Deploy a package of model objects and data by using the MDSModelDeploy tool.</span></span>|[<span data-ttu-id="2e647-146">使用 MDSModelDeploy 部署模型部署包</span><span class="sxs-lookup"><span data-stu-id="2e647-146">Deploy a Model Deployment Package by Using MDSModelDeploy</span></span>](../../2014/master-data-services/deploy-a-model-deployment-package-by-using-mdsmodeldeploy.md)|  
|<span data-ttu-id="2e647-147">通过使用向导部署只包含模型对象的包。</span><span class="sxs-lookup"><span data-stu-id="2e647-147">Deploy a package of model objects only by using the wizard.</span></span>|[<span data-ttu-id="2e647-148">使用向导部署模型部署包</span><span class="sxs-lookup"><span data-stu-id="2e647-148">Deploy a Model Deployment Package by Using the Wizard</span></span>](../../2014/master-data-services/deploy-a-model-deployment-package-by-using-the-wizard.md)|  
|<span data-ttu-id="2e647-149">编辑模型部署包，以部署选定的模型部分而不是整个模型。</span><span class="sxs-lookup"><span data-stu-id="2e647-149">Edit a model deployment package to deploy selected parts of a model, rather than the entire model.</span></span>|[<span data-ttu-id="2e647-150">编辑模型部署包</span><span class="sxs-lookup"><span data-stu-id="2e647-150">Edit a Model Deployment Package</span></span>](../../2014/master-data-services/edit-a-model-deployment-package.md)|  
  
## <a name="related-content"></a><span data-ttu-id="2e647-151">相关内容</span><span class="sxs-lookup"><span data-stu-id="2e647-151">Related Content</span></span>  
  
-   [<span data-ttu-id="2e647-152">模型部署选项 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="2e647-152">Model Deployment Options &#40;Master Data Services&#41;</span></span>](model-deployment-options-master-data-services.md)  
  
  
