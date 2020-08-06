---
title: 模型部署选项 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: cf1b17b4-47d5-4eba-83f9-fb0555806867
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 25af38deef2a5476f64f364116dc5e9168345fb2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692986"
---
# <a name="model-deployment-options-master-data-services"></a><span data-ttu-id="7d682-102">模型部署选项 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="7d682-102">Model Deployment Options (Master Data Services)</span></span>
  <span data-ttu-id="7d682-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，在您部署某一模型包文件时，必须确定是部署新的或克隆的模型，还是更新以前已克隆的模型。</span><span class="sxs-lookup"><span data-stu-id="7d682-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], when you deploy a model package file, you must decide whether to deploy a new or cloned model, or to update a model that was previously cloned.</span></span>  
  
## <a name="workflows"></a><span data-ttu-id="7d682-104">工作流</span><span class="sxs-lookup"><span data-stu-id="7d682-104">Workflows</span></span>  
 <span data-ttu-id="7d682-105">当使用模型包时，有两个主要的工作流。</span><span class="sxs-lookup"><span data-stu-id="7d682-105">When working with model packages, there are two primary workflows.</span></span>  
  
-   <span data-ttu-id="7d682-106">在测试环境中创建某一模型的包以及将该模型的克隆部署到生产环境。</span><span class="sxs-lookup"><span data-stu-id="7d682-106">Create a package of a model in a test environment and deploy a clone of the model to a production environment.</span></span> <span data-ttu-id="7d682-107">一段时间后，将来自测试环境的更新部署到生产环境。</span><span class="sxs-lookup"><span data-stu-id="7d682-107">Over time, deploy updates from the test environment to the production environment.</span></span>  
  
-   <span data-ttu-id="7d682-108">创建模型的包，然后将其作为新模型部署到相同的环境。</span><span class="sxs-lookup"><span data-stu-id="7d682-108">Create a package of a model and deploy it as a new model to the same environment.</span></span> <span data-ttu-id="7d682-109">在此情况下，您必须为该模型提供一个新名称。</span><span class="sxs-lookup"><span data-stu-id="7d682-109">In this case, you must give the model a new name.</span></span>  
  
## <a name="options"></a><span data-ttu-id="7d682-110">选项</span><span class="sxs-lookup"><span data-stu-id="7d682-110">Options</span></span>  
 <span data-ttu-id="7d682-111">在 MDS 数据库中，每个模型对象都具有唯一的标识符 (ID)。</span><span class="sxs-lookup"><span data-stu-id="7d682-111">In the MDS database, each model object has a unique identifier (ID).</span></span> <span data-ttu-id="7d682-112">这些 ID 包含在模型部署包中。</span><span class="sxs-lookup"><span data-stu-id="7d682-112">These IDs are included in model deployment packages.</span></span> <span data-ttu-id="7d682-113">在部署包时，您必须选择如何处理这些 ID。</span><span class="sxs-lookup"><span data-stu-id="7d682-113">When you deploy the package, you must choose what to do with these IDs.</span></span>  
  
 <span data-ttu-id="7d682-114">下表可帮助您确定在使用系统管理模型部署向导或 MDSModelDeploy 工具时作出何种选择。</span><span class="sxs-lookup"><span data-stu-id="7d682-114">The following table should help you determine which choice to make when deploying a model by using either the System Administration model deployment wizard or the MDSModelDeploy tool.</span></span>  
  
|<span data-ttu-id="7d682-115">选项</span><span class="sxs-lookup"><span data-stu-id="7d682-115">Option</span></span>|<span data-ttu-id="7d682-116">说明</span><span class="sxs-lookup"><span data-stu-id="7d682-116">Description</span></span>|<span data-ttu-id="7d682-117">注释</span><span class="sxs-lookup"><span data-stu-id="7d682-117">Notes</span></span>|  
|------------|-----------------|-----------|  
|<span data-ttu-id="7d682-118">新建</span><span class="sxs-lookup"><span data-stu-id="7d682-118">New</span></span>|<span data-ttu-id="7d682-119">使用唯一名称创建一个新模型。</span><span class="sxs-lookup"><span data-stu-id="7d682-119">Create a new model with a unique name.</span></span> <span data-ttu-id="7d682-120">为所有模型对象创建新的标识符。</span><span class="sxs-lookup"><span data-stu-id="7d682-120">New identifiers are created for all model objects.</span></span>|<span data-ttu-id="7d682-121">如果您使用新的标识符创建一个新模型，则在以后无法使用模型部署工具将更新应用于该模型。</span><span class="sxs-lookup"><span data-stu-id="7d682-121">If you create a new model with new identifiers, you cannot use model deployment tools to apply updates to the model later.</span></span> <span data-ttu-id="7d682-122">在 Web 应用程序中使用向导部署一个模型包时，只有在具有相同名称或 ID 的模型已存在时，您才能选择创建一个新模型。</span><span class="sxs-lookup"><span data-stu-id="7d682-122">When using the wizard in the web application to deploy a model package, you have the option to create a new model only if a model with the same name or ID already exists.</span></span>|  
|<span data-ttu-id="7d682-123">克隆</span><span class="sxs-lookup"><span data-stu-id="7d682-123">Clone</span></span>|<span data-ttu-id="7d682-124">创建一个新模型，该模型是包中模型的精确克隆。</span><span class="sxs-lookup"><span data-stu-id="7d682-124">Create a new model that is an exact clone of the model in the package.</span></span> <span data-ttu-id="7d682-125">这仅适用于该模型在目标环境中不存在的情况（按名称或标识符）。</span><span class="sxs-lookup"><span data-stu-id="7d682-125">This works only if the model does not exist (by name or identifier) in the target environment.</span></span> <span data-ttu-id="7d682-126">如果想要在多个环境中拥有相同的模型并在经过一段时间后更新克隆的模型，请使用“克隆”。</span><span class="sxs-lookup"><span data-stu-id="7d682-126">Use "clone" when you want to have the same model in multiple environments and update the cloned model over time.</span></span>|<span data-ttu-id="7d682-127">这是 Web 应用程序中向导的默认行为。</span><span class="sxs-lookup"><span data-stu-id="7d682-127">This is the default behavior of the wizard in the web application.</span></span> <span data-ttu-id="7d682-128">如果已经存在具有相同名称或 ID 的模型，则系统将会提示您改为创建新的模型。</span><span class="sxs-lookup"><span data-stu-id="7d682-128">If a model with the same name or ID already exists, you are prompted to create a new model instead.</span></span>|  
|<span data-ttu-id="7d682-129">更新</span><span class="sxs-lookup"><span data-stu-id="7d682-129">Update</span></span>|<span data-ttu-id="7d682-130">使用包中的模型更新现有模型。</span><span class="sxs-lookup"><span data-stu-id="7d682-130">Update an existing model with the model in the package.</span></span> <span data-ttu-id="7d682-131">标识符在这两个模型中必须相同。</span><span class="sxs-lookup"><span data-stu-id="7d682-131">The identifiers must be the same in both models.</span></span> <span data-ttu-id="7d682-132">这用来更新您以前克隆的模型。</span><span class="sxs-lookup"><span data-stu-id="7d682-132">This is used to update a model that you previously cloned.</span></span>|<span data-ttu-id="7d682-133">您只能更新以前克隆的模型。</span><span class="sxs-lookup"><span data-stu-id="7d682-133">You can only update models that were previously cloned.</span></span> <span data-ttu-id="7d682-134">（名称和 ID 必须匹配。）</span><span class="sxs-lookup"><span data-stu-id="7d682-134">(The names and IDs must match.)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7d682-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7d682-135">See Also</span></span>  
 <span data-ttu-id="7d682-136">[使用 MDSModelDeploy 部署模型部署包](../../2014/master-data-services/deploy-a-model-deployment-package-by-using-mdsmodeldeploy.md) </span><span class="sxs-lookup"><span data-stu-id="7d682-136">[Deploy a Model Deployment Package by Using MDSModelDeploy](../../2014/master-data-services/deploy-a-model-deployment-package-by-using-mdsmodeldeploy.md) </span></span>  
 <span data-ttu-id="7d682-137">[使用向导部署模型部署包](../../2014/master-data-services/deploy-a-model-deployment-package-by-using-the-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="7d682-137">[Deploy a Model Deployment Package by Using the Wizard](../../2014/master-data-services/deploy-a-model-deployment-package-by-using-the-wizard.md) </span></span>  
 [<span data-ttu-id="7d682-138">部署模型 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="7d682-138">Deploying Models &#40;Master Data Services&#41;</span></span>](deploying-models-master-data-services.md)  
  
  
