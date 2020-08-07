---
title: 使用 MDSModelDeploy 部署模型部署包 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: fb2a4df4-5e0d-4b34-818f-383dbde1b15c
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: c23dcc592c2de34fa87703c8ba58d949dfec455c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588580"
---
# <a name="deploy-a-model-deployment-package-by-using-mdsmodeldeploy"></a><span data-ttu-id="95043-102">使用 MDSModelDeploy 部署模型部署包</span><span class="sxs-lookup"><span data-stu-id="95043-102">Deploy a Model Deployment Package by Using MDSModelDeploy</span></span>
  <span data-ttu-id="95043-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，使用 MDSModelDeploy 工具来部署包含以下任一信息的包：</span><span class="sxs-lookup"><span data-stu-id="95043-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], use the MDSModelDeploy tool to deploy a package that contains either:</span></span>  
  
-   <span data-ttu-id="95043-104">仅模型对象。</span><span class="sxs-lookup"><span data-stu-id="95043-104">Model objects only.</span></span>  
  
-   <span data-ttu-id="95043-105">模型对象和数据。</span><span class="sxs-lookup"><span data-stu-id="95043-105">Model objects and data.</span></span>  
  
 <span data-ttu-id="95043-106">如果需要部署仅包含模型对象的包，可改为在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Web 应用程序中使用模型部署向导。</span><span class="sxs-lookup"><span data-stu-id="95043-106">If you want to deploy a package that contains model objects only, you can use the model deployment wizard in the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] web application instead.</span></span> <span data-ttu-id="95043-107">有关详细信息，请参阅[通过使用向导部署模型部署包](../../2014/master-data-services/deploy-a-model-deployment-package-by-using-the-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="95043-107">For more information, see [Deploy a Model Deployment Package by Using the Wizard](../../2014/master-data-services/deploy-a-model-deployment-package-by-using-the-wizard.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="95043-108">包只能部署到创建它们的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 版本中。</span><span class="sxs-lookup"><span data-stu-id="95043-108">Packages can be deployed to the edition of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] they were created in only.</span></span> <span data-ttu-id="95043-109">这意味着在 [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] 中创建的包不能部署到 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="95043-109">This means that packages created in [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] cannot be deployed to [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] or higher.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="95043-110">必备条件</span><span class="sxs-lookup"><span data-stu-id="95043-110">Prerequisites</span></span>  
 <span data-ttu-id="95043-111">若要执行此过程：</span><span class="sxs-lookup"><span data-stu-id="95043-111">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="95043-112">您必须有权访问目标 **环境中的** “系统管理” [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 功能区域。</span><span class="sxs-lookup"><span data-stu-id="95043-112">You must have permission to access the **System Administration** functional area in the target [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] environment.</span></span>  
  
-   <span data-ttu-id="95043-113">模型部署包必须存在。</span><span class="sxs-lookup"><span data-stu-id="95043-113">A model deployment package must exist.</span></span> <span data-ttu-id="95043-114">有关详细信息，请参阅[使用向导创建模型部署包](../../2014/master-data-services/create-a-model-deployment-package-by-using-mdsmodeldeploy.md)。</span><span class="sxs-lookup"><span data-stu-id="95043-114">For more information, see  [Create a Model Deployment Package by Using MDSModelDeploy](../../2014/master-data-services/create-a-model-deployment-package-by-using-mdsmodeldeploy.md).</span></span>  
  
-   <span data-ttu-id="95043-115">您必须是部署模型的环境中的管理员。</span><span class="sxs-lookup"><span data-stu-id="95043-115">You must be an administrator in the environment where you are deploying the model.</span></span> <span data-ttu-id="95043-116">有关详细信息，请参阅[管理员 &#40;Master Data Services&#41;](administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="95043-116">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="95043-117">如果要使用数据更新模型，则不能**锁定**或**提交**正在部署到的版本。</span><span class="sxs-lookup"><span data-stu-id="95043-117">If you are updating a model with data, the version you're deploying to cannot be **Locked** or **Committed**.</span></span>  
  
### <a name="to-deploy-a-model-deployment-package"></a><span data-ttu-id="95043-118">部署模型部署包</span><span class="sxs-lookup"><span data-stu-id="95043-118">To deploy a model deployment package</span></span>  
  
1.  <span data-ttu-id="95043-119">确定您是在部署一个新模型、部署模型的一个克隆副本，还是在更新先前克隆的模型。</span><span class="sxs-lookup"><span data-stu-id="95043-119">Determine whether you are deploying a new model, a clone of a model, or updating a previously-cloned model.</span></span> <span data-ttu-id="95043-120">有关详细信息，请参阅[模型部署选项 (Master Data Services)](../../2014/master-data-services/model-deployment-options-master-data-services.md)</span><span class="sxs-lookup"><span data-stu-id="95043-120">For more information, see [Model Deployment Options &#40;Master Data Services&#41;](../../2014/master-data-services/model-deployment-options-master-data-services.md).</span></span>  
  
2.  <span data-ttu-id="95043-121">打开命令提示符，然后导航到 MDSModelDeploy.exe。</span><span class="sxs-lookup"><span data-stu-id="95043-121">Open a command prompt and navigate to MDSModelDeploy.exe.</span></span>  
  
    -   <span data-ttu-id="95043-122">如果 MDS 安装在默认位置，则该工具位于*驱动器*： \PROGRAM Files\Microsoft SQL Server\120\Master Data Services\Configuration\MDSModelDeploy.exe</span><span class="sxs-lookup"><span data-stu-id="95043-122">If MDS is installed at the default location, the tool is available at *drive*:\Program Files\Microsoft SQL Server\120\Master Data Services\Configuration\MDSModelDeploy.exe</span></span>  
  
    -   <span data-ttu-id="95043-123">如果 MDS 未安装在默认位置，请在本地计算机上搜索 MDSModelDeploy.exe。</span><span class="sxs-lookup"><span data-stu-id="95043-123">If MDS is not installed at the default location, search the local computer for MDSModelDeploy.exe.</span></span>  
  
3.  <span data-ttu-id="95043-124">可选。</span><span class="sxs-lookup"><span data-stu-id="95043-124">Optional.</span></span> <span data-ttu-id="95043-125">查看选项和帮助。</span><span class="sxs-lookup"><span data-stu-id="95043-125">View options and help.</span></span>  
  
    -   <span data-ttu-id="95043-126">若要显示所有可用选项，请键入 `MDSModelDeploy` ，然后按 Enter 键。</span><span class="sxs-lookup"><span data-stu-id="95043-126">To display all available options, type `MDSModelDeploy` and press Enter.</span></span>  
  
    -   <span data-ttu-id="95043-127">若要显示某个选项的帮助，请键入以下命令，其中 OptionName\*\* 是该选项的名称：`MDSModelDeploy help OptionName`。</span><span class="sxs-lookup"><span data-stu-id="95043-127">To display help for an option, type the following, where *OptionName* is the name of the option: `MDSModelDeploy help OptionName`.</span></span>  
  
4.  <span data-ttu-id="95043-128">可选。</span><span class="sxs-lookup"><span data-stu-id="95043-128">Optional.</span></span> <span data-ttu-id="95043-129">如果您有多个 Web 应用程序，通过键入下面的命令并按 Enter 键，确定您要部署到的服务的名称：</span><span class="sxs-lookup"><span data-stu-id="95043-129">If you have multiple web applications, determine the name of the service you will deploy to by typing this command and pressing Enter:</span></span>  
  
    ```  
    MDSModelDeploy listservices  
    ```  
  
     <span data-ttu-id="95043-130">随即返回一个值列表，例如 `MDS1, Default Web Site, MDS`。</span><span class="sxs-lookup"><span data-stu-id="95043-130">A list of values is returned, for example `MDS1, Default Web Site, MDS`.</span></span> <span data-ttu-id="95043-131">需要此列表中的第一个值（在此例中为 `MDS1`）来部署模型。</span><span class="sxs-lookup"><span data-stu-id="95043-131">The first value in this list (in this case, `MDS1`) is needed to deploy the model.</span></span>  
  
5.  <span data-ttu-id="95043-132">根据您是在创建模型部署、克隆模型还是更新模型，在命令提示符处，键入以下命令并按 Enter 键。</span><span class="sxs-lookup"><span data-stu-id="95043-132">Depending on whether you are creating a model, cloning a model, or updating a model, at the command prompt, type the following and press Enter.</span></span>  
  
    -   <span data-ttu-id="95043-133">创建新模型：</span><span class="sxs-lookup"><span data-stu-id="95043-133">To create a new model:</span></span>  
  
        ```  
        MDSModelDeploy deploynew -package PackageName -model ModelName -service ServiceName  
        ```  
  
    -   <span data-ttu-id="95043-134">创建模型的克隆：</span><span class="sxs-lookup"><span data-stu-id="95043-134">To create a clone of a model:</span></span>  
  
        ```  
        MDSModelDeploy deployclone -package PackageName  
        ```  
  
    -   <span data-ttu-id="95043-135">更新现有模型及其数据：</span><span class="sxs-lookup"><span data-stu-id="95043-135">To update an existing model and its data:</span></span>  
  
        ```  
        MDSModelDeploy deployupdate -package PackageName -version VersionName  
        ```  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="95043-136">如果使用 MDSModelDeploy 工具更新现有模型及其数据，并且该包不包含目标模型中存在的实体、属性或成员，则 MDSModelDeploy 不会从模型中删除此实体、属性或成员。</span><span class="sxs-lookup"><span data-stu-id="95043-136">If you use the MDSModelDeploy tool to update an existing model and its data, and the package does not contain an entity, attribute, or member that exists in the destination model, MDSModelDeploy will not delete that entity, attribute, or member from the model.</span></span>  
  
     <span data-ttu-id="95043-137">其中，PackageName\*\* 是包文件 (.pkg) 的名称，ModelName\*\* 是新模型的名称，VersionName\*\* 是版本的名称，ServiceName\*\* 是上一步中返回的服务的名称。</span><span class="sxs-lookup"><span data-stu-id="95043-137">Where *PackageName* is the name of the package (.pkg) file, *ModelName* is the name of the new model, *VersionName* is the name of the version, and *ServiceName* is the name of the service that you returned in the previous step.</span></span> <span data-ttu-id="95043-138">确保模型名称和版本名称完全匹配区分大小写的名称。</span><span class="sxs-lookup"><span data-stu-id="95043-138">Ensure that the model and version names match the exact case-sensitive names.</span></span>  
  
6.  <span data-ttu-id="95043-139">成功部署包后，将显示一条消息“MDSModelDeploy 操作已成功完成”。</span><span class="sxs-lookup"><span data-stu-id="95043-139">When the package is successfully deployed, a message stating "MDSModelDeploy operation completed successfully" is displayed.</span></span>  
  
 <span data-ttu-id="95043-140">注意：</span><span class="sxs-lookup"><span data-stu-id="95043-140">**Notes:**</span></span>  
  
-   <span data-ttu-id="95043-141">如果包中的订阅视图与现有模型中的订阅视图同名，则该视图将创建为*modelname. modelname.subscriptionviewname*。</span><span class="sxs-lookup"><span data-stu-id="95043-141">If a subscription view in the package has the same name as a subscription view in an existing model, the view is created as *modelname.subscriptionviewname*.</span></span> <span data-ttu-id="95043-142">如果此名称已使用，则不会创建订阅视图。</span><span class="sxs-lookup"><span data-stu-id="95043-142">If this name is already in use, the subscription view is not created.</span></span>  
  
-   <span data-ttu-id="95043-143">部署过程具有以下四个步骤：</span><span class="sxs-lookup"><span data-stu-id="95043-143">The deployment process has four steps:</span></span>  
  
    1.  <span data-ttu-id="95043-144">创建模型对象。</span><span class="sxs-lookup"><span data-stu-id="95043-144">The model objects are created.</span></span>  
  
    2.  <span data-ttu-id="95043-145">创建业务规则。</span><span class="sxs-lookup"><span data-stu-id="95043-145">Business rules are created.</span></span>  
  
    3.  <span data-ttu-id="95043-146">创建订阅视图。</span><span class="sxs-lookup"><span data-stu-id="95043-146">Subscription views are created.</span></span>  
  
    4.  <span data-ttu-id="95043-147">填充主数据。</span><span class="sxs-lookup"><span data-stu-id="95043-147">Master data is populated.</span></span>  
  
-   <span data-ttu-id="95043-148">创建一个新的或克隆的模型时，如果该过程在任何步骤期间失败，该模型将被删除。</span><span class="sxs-lookup"><span data-stu-id="95043-148">When creating a new or cloned model, if the process fails during any step, the model is deleted.</span></span>  
  
     <span data-ttu-id="95043-149">在更新某一模型时，如果该过程在前三个步骤中失败，则该过程将不会继续；但是，已进行的更改将不会回滚。</span><span class="sxs-lookup"><span data-stu-id="95043-149">When updating a model, if the process fails during the first three steps, it does not proceed; however, changes that are already made are not rolled back.</span></span> <span data-ttu-id="95043-150">如果该过程在步骤 4 中失败，则会更新可更新的成员。</span><span class="sxs-lookup"><span data-stu-id="95043-150">If the process fails in step 4, members that can be updated are updated.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="95043-151">后续步骤</span><span class="sxs-lookup"><span data-stu-id="95043-151">Next Steps</span></span>  
 <span data-ttu-id="95043-152">在模型部署包中不包括用户定义元数据、文件属性以及用户和组权限。</span><span class="sxs-lookup"><span data-stu-id="95043-152">User-defined metadata, file attributes, and user and group permissions are not included in model deployment packages.</span></span> <span data-ttu-id="95043-153">在您部署模型后，必须手动更新这些内容。</span><span class="sxs-lookup"><span data-stu-id="95043-153">After you deploy a model, you must update these manually.</span></span> <span data-ttu-id="95043-154">有关详情，请参阅：</span><span class="sxs-lookup"><span data-stu-id="95043-154">For more information, see:</span></span>  
  
-   [<span data-ttu-id="95043-155">Master Data Services&#41;添加元数据 &#40;</span><span class="sxs-lookup"><span data-stu-id="95043-155">Add Metadata &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/add-metadata-master-data-services.md)  
  
-   [<span data-ttu-id="95043-156">分配模型对象权限 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="95043-156">Assign Model Object Permissions &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/assign-model-object-permissions-master-data-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="95043-157">另请参阅</span><span class="sxs-lookup"><span data-stu-id="95043-157">See Also</span></span>  
 [<span data-ttu-id="95043-158">部署模型 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="95043-158">Deploying Models &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/deploying-models-master-data-services.md)  
  
  
