---
title: 使用向导部署模型部署包 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- deployment packages [Master Data Services], deploying
- models [Master Data Services], deploying a package
ms.assetid: 4f65dc60-0ff8-46e6-9988-5bc5b9603ad0
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 75af9f7c12d866c6d9707f62c898aa7601f94800
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691764"
---
# <a name="deploy-a-model-deployment-package-by-using-the-wizard"></a><span data-ttu-id="a6acd-102">使用向导部署模型部署包</span><span class="sxs-lookup"><span data-stu-id="a6acd-102">Deploy a Model Deployment Package by Using the Wizard</span></span>
  <span data-ttu-id="a6acd-103">使用 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 模型部署向导部署只包含模型对象的包。</span><span class="sxs-lookup"><span data-stu-id="a6acd-103">Use the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] model deployment wizard to deploy packages that contain model objects only.</span></span> <span data-ttu-id="a6acd-104">如果需要部署包含数据的包，请参阅 [使用 MDSModelDeploy 部署模型部署包](../../2014/master-data-services/deploy-a-model-deployment-package-by-using-mdsmodeldeploy.md)。</span><span class="sxs-lookup"><span data-stu-id="a6acd-104">If you need to deploy a package with data, see [Deploy a Model Deployment Package by Using MDSModelDeploy](../../2014/master-data-services/deploy-a-model-deployment-package-by-using-mdsmodeldeploy.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="a6acd-105">包只能部署到创建它们的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 版本中。</span><span class="sxs-lookup"><span data-stu-id="a6acd-105">Packages can be deployed to the edition of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] they were created in only.</span></span> <span data-ttu-id="a6acd-106">这意味着在 [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] 中创建的包不能部署到 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="a6acd-106">This means that packages created in [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] cannot be deployed to [!INCLUDE[ssSQL11](../includes/sssql11-md.md)].</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="a6acd-107">先决条件</span><span class="sxs-lookup"><span data-stu-id="a6acd-107">Prerequisites</span></span>  
 <span data-ttu-id="a6acd-108">若要执行此过程：</span><span class="sxs-lookup"><span data-stu-id="a6acd-108">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="a6acd-109">您必须有权访问目标 **环境中的** “系统管理” [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 功能区域。</span><span class="sxs-lookup"><span data-stu-id="a6acd-109">You must have permission to access the **System Administration** functional area in the target [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] environment.</span></span>  
  
-   <span data-ttu-id="a6acd-110">模型部署包必须存在。</span><span class="sxs-lookup"><span data-stu-id="a6acd-110">A model deployment package must exist.</span></span> <span data-ttu-id="a6acd-111">有关详细信息，请参阅 [使用向导创建模型部署包](../../2014/master-data-services/create-a-model-deployment-package-by-using-the-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="a6acd-111">For more information, see [Create a Model Deployment Package by Using the Wizard](../../2014/master-data-services/create-a-model-deployment-package-by-using-the-wizard.md).</span></span>  
  
-   <span data-ttu-id="a6acd-112">您必须是部署模型的环境中的管理员。</span><span class="sxs-lookup"><span data-stu-id="a6acd-112">You must be an administrator in the environment where you are deploying the model.</span></span> <span data-ttu-id="a6acd-113">有关详细信息，请参阅[管理员 &#40;Master Data Services&#41;](administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="a6acd-113">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
### <a name="to-deploy-a-model-deployment-package-of-model-objects-only"></a><span data-ttu-id="a6acd-114">仅部署模型对象的模型部署包</span><span class="sxs-lookup"><span data-stu-id="a6acd-114">To deploy a model deployment package of model objects only</span></span>  
  
1.  <span data-ttu-id="a6acd-115">在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]中，单击 **“系统管理”**。</span><span class="sxs-lookup"><span data-stu-id="a6acd-115">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="a6acd-116">在 **“模型视图”** 页上，从菜单栏中，指向 **“系统”** ，然后单击 **“部署”**。</span><span class="sxs-lookup"><span data-stu-id="a6acd-116">On the **Model View** page, from the menu bar, point to **System** and click **Deployment**.</span></span>  
  
3.  <span data-ttu-id="a6acd-117">在 **“模型部署向导”** 上，单击 **“部署”**。</span><span class="sxs-lookup"><span data-stu-id="a6acd-117">On the **Model Deployment Wizard**, click **Deploy**.</span></span>  
  
4.  <span data-ttu-id="a6acd-118">单击“浏览” 。</span><span class="sxs-lookup"><span data-stu-id="a6acd-118">Click **Browse**.</span></span>  
  
5.  <span data-ttu-id="a6acd-119">找到部署包（.pkg 文件），然后单击“打开”。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="a6acd-119">Find your deployment package (.pkg file) and click **Open**.</span></span>  
  
6.  <span data-ttu-id="a6acd-120">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="a6acd-120">Click **Next**.</span></span>  
  
7.  <span data-ttu-id="a6acd-121">在加载包后，单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="a6acd-121">After the package is loaded, click **Next**.</span></span>  
  
8.  <span data-ttu-id="a6acd-122">如果该模型已存在，则可以通过选择 **“更新现有模型”** 更新该模型。</span><span class="sxs-lookup"><span data-stu-id="a6acd-122">If the model already exists, you can update it by selecting **Update the existing model**.</span></span> <span data-ttu-id="a6acd-123">若要创建新模型，请选择 **“创建新模型”** ，并且在单击 **“下一步”** 后，可为该新模型键入名称。</span><span class="sxs-lookup"><span data-stu-id="a6acd-123">To create a new model, select **Create a new model** and after you click **Next** you can type a name for the new model.</span></span>  
  
9. <span data-ttu-id="a6acd-124">单击“完成”\*\*\*\* 以退出向导。</span><span class="sxs-lookup"><span data-stu-id="a6acd-124">Click **Finish** to exit the wizard.</span></span>  
  
 <span data-ttu-id="a6acd-125">注意：</span><span class="sxs-lookup"><span data-stu-id="a6acd-125">**Notes:**</span></span>  
  
-   <span data-ttu-id="a6acd-126">如果包中的订阅视图与现有模型中的订阅视图同名，则该视图将创建为*modelname. modelname.subscriptionviewname*。</span><span class="sxs-lookup"><span data-stu-id="a6acd-126">If a subscription view in the package has the same name as a subscription view in an existing model, the view is created as *modelname.subscriptionviewname*.</span></span> <span data-ttu-id="a6acd-127">如果此名称已使用，则不会创建订阅视图。</span><span class="sxs-lookup"><span data-stu-id="a6acd-127">If this name is already in use, the subscription view is not created.</span></span>  
  
-   <span data-ttu-id="a6acd-128">部署过程具有以下四个步骤：</span><span class="sxs-lookup"><span data-stu-id="a6acd-128">The deployment process has four steps:</span></span>  
  
    1.  <span data-ttu-id="a6acd-129">创建模型对象。</span><span class="sxs-lookup"><span data-stu-id="a6acd-129">The model objects are created.</span></span>  
  
    2.  <span data-ttu-id="a6acd-130">创建订阅视图。</span><span class="sxs-lookup"><span data-stu-id="a6acd-130">Subscription views are created.</span></span>  
  
    3.  <span data-ttu-id="a6acd-131">创建业务规则。</span><span class="sxs-lookup"><span data-stu-id="a6acd-131">Business rules are created.</span></span>  
  
    4.  <span data-ttu-id="a6acd-132">填充主数据。</span><span class="sxs-lookup"><span data-stu-id="a6acd-132">Master data is populated.</span></span>  
  
-   <span data-ttu-id="a6acd-133">创建一个新的或克隆的模型时，如果该过程在任何步骤期间失败，该模型将被删除。</span><span class="sxs-lookup"><span data-stu-id="a6acd-133">When creating a new or cloned model, if the process fails during any step, the model is deleted.</span></span>  
  
     <span data-ttu-id="a6acd-134">在更新模型时，如果该过程在前三个步骤的任意步骤中失败，则该过程将不会继续；但是，已进行的更改将不会回滚。</span><span class="sxs-lookup"><span data-stu-id="a6acd-134">When updating a model, if the process fails during any of the first three steps, it does not proceed beyond that step; however, changes that are already made are not rolled back.</span></span> <span data-ttu-id="a6acd-135">如果该过程在步骤 4 中失败，则会更新可更新的成员。</span><span class="sxs-lookup"><span data-stu-id="a6acd-135">If the process fails in step 4, members that can be updated are updated.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="a6acd-136">后续步骤</span><span class="sxs-lookup"><span data-stu-id="a6acd-136">Next Steps</span></span>  
 <span data-ttu-id="a6acd-137">在模型部署包中不包括用户定义元数据、文件属性以及用户和组权限。</span><span class="sxs-lookup"><span data-stu-id="a6acd-137">User-defined metadata, file attributes, and user and group permissions are not included in model deployment packages.</span></span> <span data-ttu-id="a6acd-138">在您部署模型后，必须手动更新这些内容。</span><span class="sxs-lookup"><span data-stu-id="a6acd-138">After you deploy a model, you must update these manually.</span></span> <span data-ttu-id="a6acd-139">有关详细信息，请参见:</span><span class="sxs-lookup"><span data-stu-id="a6acd-139">For more information, see:</span></span>  
  
-   [<span data-ttu-id="a6acd-140">Master Data Services&#41;添加元数据 &#40;</span><span class="sxs-lookup"><span data-stu-id="a6acd-140">Add Metadata &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/add-metadata-master-data-services.md)  
  
-   [<span data-ttu-id="a6acd-141">分配模型对象权限 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="a6acd-141">Assign Model Object Permissions &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/assign-model-object-permissions-master-data-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="a6acd-142">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a6acd-142">See Also</span></span>  
 [<span data-ttu-id="a6acd-143">部署模型 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="a6acd-143">Deploying Models &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/deploying-models-master-data-services.md)  
  
  
