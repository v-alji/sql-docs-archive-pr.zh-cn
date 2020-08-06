---
title: 使用 MDSModelDeploy 创建模型部署包 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: c2687e39-dc20-494f-a707-2aa29f4c329e
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: c546d6398234dd43103d0e6c75822377e11de61a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591450"
---
# <a name="create-a-model-deployment-package-by-using-mdsmodeldeploy"></a><span data-ttu-id="524e3-102">使用 MDSModelDeploy 创建模型部署包</span><span class="sxs-lookup"><span data-stu-id="524e3-102">Create a Model Deployment Package by Using MDSModelDeploy</span></span>
  <span data-ttu-id="524e3-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，使用 MDSModelDeploy 工具来创建包。</span><span class="sxs-lookup"><span data-stu-id="524e3-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], use the MDSModelDeploy tool to create a package.</span></span> <span data-ttu-id="524e3-104">根据您指定的命令，包可以包含：</span><span class="sxs-lookup"><span data-stu-id="524e3-104">Depending on the commands you specify, the package can contain either:</span></span>  
  
-   <span data-ttu-id="524e3-105">仅模型对象。</span><span class="sxs-lookup"><span data-stu-id="524e3-105">Model objects only.</span></span>  
  
-   <span data-ttu-id="524e3-106">模型对象和数据。</span><span class="sxs-lookup"><span data-stu-id="524e3-106">Model objects and data.</span></span>  
  
 <span data-ttu-id="524e3-107">如果需要部署仅包含模型对象的包，可改为在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Web 应用程序中使用模型部署向导。</span><span class="sxs-lookup"><span data-stu-id="524e3-107">If you want to deploy a package that contains model objects only, you can use the model deployment wizard in the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] web application instead.</span></span> <span data-ttu-id="524e3-108">有关详细信息，请参阅 [使用向导创建模型部署包](../../2014/master-data-services/create-a-model-deployment-package-by-using-the-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="524e3-108">For more information, see [Create a Model Deployment Package by Using the Wizard](../../2014/master-data-services/create-a-model-deployment-package-by-using-the-wizard.md).</span></span>  
> [!NOTE]  
> <span data-ttu-id="524e3-109">此版本的 MDSModelDeploy 工具无法使用超过千兆字节 (GB) 内存。</span><span class="sxs-lookup"><span data-stu-id="524e3-109">This version of the MDSModelDeploy tool cannot use more than gigabytes (GB) of memory.</span></span> <span data-ttu-id="524e3-110">使用 "**模型对象和数据**" 选项创建或部署大型模型时，可能会出现 "内存不足" 或 "流过长" 错误。</span><span class="sxs-lookup"><span data-stu-id="524e3-110">When you create or deploy large models by using **Model objects and data** option, you may experience "Out of Memory" or "Stream was too long" errors.</span></span> <span data-ttu-id="524e3-111">若要解决此问题，请使用 MDS 过渡部署数据;或升级到 MDS 2016 或更高版本，其中包括 MDSModelDeploy 工具的更新版本。</span><span class="sxs-lookup"><span data-stu-id="524e3-111">To resolve this issue, use MDS staging to deploy the data; or upgrade to MDS 2016 or a later version, which includes the updated version of the MDSModelDeploy tool.</span></span>
## <a name="prerequisites"></a><span data-ttu-id="524e3-112">先决条件</span><span class="sxs-lookup"><span data-stu-id="524e3-112">Prerequisites</span></span>  
 <span data-ttu-id="524e3-113">若要执行此过程：</span><span class="sxs-lookup"><span data-stu-id="524e3-113">To perform this procedure:</span></span>  
  
1.  <span data-ttu-id="524e3-114">运行 MDSModelDeploy 工具所需的基本权限如下所示：</span><span class="sxs-lookup"><span data-stu-id="524e3-114">The basic permissions required to run the MDSModelDeploy tool are the following:</span></span>  
  
    -   <span data-ttu-id="524e3-115">与 MDS 配置管理器相同的 Windows 权限（Windows 管理员）</span><span class="sxs-lookup"><span data-stu-id="524e3-115">The same Windows permission as the MDS Configuration Manager (administrator of Windows)</span></span>  
  
    -   <span data-ttu-id="524e3-116">针对 MDS 数据库的 DBA 权限。</span><span class="sxs-lookup"><span data-stu-id="524e3-116">DBA permission on the MDS database.</span></span>  
  
2.  <span data-ttu-id="524e3-117">使用 MDSModelDeploy 工具创建包所需的权限如下所示：</span><span class="sxs-lookup"><span data-stu-id="524e3-117">The permissions required to create the package using the MDSModelDeploy tool are the following:</span></span>  
  
    -   <span data-ttu-id="524e3-118">针对数据模型的 MDS 模型管理员权限。</span><span class="sxs-lookup"><span data-stu-id="524e3-118">MDS model administrator permission on the data model.</span></span>  
  
    -   <span data-ttu-id="524e3-119">MDS 集成管理功能权限。</span><span class="sxs-lookup"><span data-stu-id="524e3-119">MDS Integration Management function permission.</span></span>  
  
3.  <span data-ttu-id="524e3-120">使用 MDSModelDeploy 工具部署模型所需的权限如下所示：</span><span class="sxs-lookup"><span data-stu-id="524e3-120">The permissions required to deploy a model using the MDSModelDeploy tool are the following:</span></span>  
  
    -   <span data-ttu-id="524e3-121">MDS 资源管理器功能权限</span><span class="sxs-lookup"><span data-stu-id="524e3-121">MDS Explorer function permission</span></span>  
  
    -   <span data-ttu-id="524e3-122">MDS 集成管理功能权限</span><span class="sxs-lookup"><span data-stu-id="524e3-122">MDS Integration Management function permission</span></span>  
  
    -   <span data-ttu-id="524e3-123">MDS 系统管理功能权限。</span><span class="sxs-lookup"><span data-stu-id="524e3-123">MDS System Administration function permission.</span></span>  
  
4.  <span data-ttu-id="524e3-124">使用 MDSModelDeploy 工具列出模型所需的权限如下所示：</span><span class="sxs-lookup"><span data-stu-id="524e3-124">The permissions required to list models using the MDSModelDeploy tool are the following:</span></span>  
  
    -   <span data-ttu-id="524e3-125">MDS 资源管理器功能权限</span><span class="sxs-lookup"><span data-stu-id="524e3-125">MDS Explorer function permission</span></span>  
  
    -   <span data-ttu-id="524e3-126">查看列表的模型所需的针对数据模型的 MDS 模型管理员权限。</span><span class="sxs-lookup"><span data-stu-id="524e3-126">MDS model administrator permission on the data model on order to see the model in the list.</span></span>  
  
 <span data-ttu-id="524e3-127">模型对于您要创建的包必须存在。</span><span class="sxs-lookup"><span data-stu-id="524e3-127">A model must exist for you to create a package of.</span></span> <span data-ttu-id="524e3-128">有关详细信息，请参阅[创建模型 (Master Data Services)](create-a-model-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="524e3-128">For more information, see [Create a Model &#40;Master Data Services&#41;](create-a-model-master-data-services.md).</span></span>  
  
 <span data-ttu-id="524e3-129">有关详细信息，请参阅[管理员 &#40;Master Data Services&#41;](../../2014/master-data-services/administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="524e3-129">For more information, see [Administrators &#40;Master Data Services&#41;](../../2014/master-data-services/administrators-master-data-services.md).</span></span>  
  
### <a name="to-create-a-model-deployment-package-by-using-mdsmodeldeploy"></a><span data-ttu-id="524e3-130">使用 MDSModelDeploy 创建模型部署包</span><span class="sxs-lookup"><span data-stu-id="524e3-130">To create a model deployment package by using MDSModelDeploy</span></span>  
  
1.  <span data-ttu-id="524e3-131">打开命令提示符。</span><span class="sxs-lookup"><span data-stu-id="524e3-131">Open a command prompt.</span></span>  
  
2.  <span data-ttu-id="524e3-132">导航到 MDSModelDeploy.exe 所在的位置。</span><span class="sxs-lookup"><span data-stu-id="524e3-132">Navigate to the location of MDSModelDeploy.exe.</span></span>  
  
    -   <span data-ttu-id="524e3-133">如果 MDS 安装在默认位置，则该文件位于*drive*： \PROGRAM Files\Microsoft SQL Server\120\Master Data services\configuration。中。</span><span class="sxs-lookup"><span data-stu-id="524e3-133">If MDS was installed in the default location, the file is in *drive*:\Program Files\Microsoft SQL Server\120\Master Data Services\Configuration.</span></span>  
  
    -   <span data-ttu-id="524e3-134">如果 MDS 未安装在默认位置，请在本地计算机上搜索 MDSModelDeploy.exe。</span><span class="sxs-lookup"><span data-stu-id="524e3-134">If MDS was not installed in the default location, search the local computer for MDSModelDeploy.exe.</span></span>  
  
3.  <span data-ttu-id="524e3-135">可选。</span><span class="sxs-lookup"><span data-stu-id="524e3-135">Optional.</span></span> <span data-ttu-id="524e3-136">查看选项和帮助。</span><span class="sxs-lookup"><span data-stu-id="524e3-136">View options and help.</span></span>  
  
    -   <span data-ttu-id="524e3-137">若要显示所有可用选项，请键入 `MDSModelDeploy` ，然后按 Enter 键。</span><span class="sxs-lookup"><span data-stu-id="524e3-137">To display all available options, type `MDSModelDeploy` and press Enter.</span></span>  
  
    -   <span data-ttu-id="524e3-138">若要显示某个选项的帮助，请键入以下命令，其中 OptionName\*\* 是该选项的名称：`MDSModelDeploy help OptionName`。</span><span class="sxs-lookup"><span data-stu-id="524e3-138">To display help for an option, type the following, where *OptionName* is the name of the option: `MDSModelDeploy help OptionName`.</span></span>  
  
4.  <span data-ttu-id="524e3-139">可选。</span><span class="sxs-lookup"><span data-stu-id="524e3-139">Optional.</span></span> <span data-ttu-id="524e3-140">如果您有多个 Web 应用程序，通过键入下面的命令并按 Enter 键，确定您要部署到的服务的名称：</span><span class="sxs-lookup"><span data-stu-id="524e3-140">If you have multiple web applications, determine the name of the service you will deploy to by typing this command and pressing Enter:</span></span>  
  
    ```  
    MDSModelDeploy listservices  
    ```  
  
     <span data-ttu-id="524e3-141">随即返回一个值列表，例如 `MDS1, Default Web Site, MDS`。</span><span class="sxs-lookup"><span data-stu-id="524e3-141">A list of values is returned, for example `MDS1, Default Web Site, MDS`.</span></span> <span data-ttu-id="524e3-142">需要此列表中的第一个值（在此例中为 `MDS1`）来部署模型。</span><span class="sxs-lookup"><span data-stu-id="524e3-142">The first value in this list (in this case, `MDS1`) is needed to deploy the model.</span></span>  
  
5.  <span data-ttu-id="524e3-143">若要创建包含模型对象和数据的包，请键入以下命令，其中 *ModelName*、 *VersionName*、 *ServiceName*和 *PackageName* 分别是模型名称、版本名称、服务名称以及 .pkg 输出文件的名称：</span><span class="sxs-lookup"><span data-stu-id="524e3-143">To create a package that contains model objects and data, type the following, where *ModelName*, *VersionName*, *ServiceName*,  and *PackageName* are the names of the model, version, service, and of the .pkg output file respectively:</span></span>  
  
    ```  
    MDSModelDeploy createpackage -model ModelName -version VersionName -service ServiceName -package PackageName -includedata  
    ```  
  
     <span data-ttu-id="524e3-144">如果您不希望包含数据，请不要使用 `-version` 和 `-includedata` 开关。</span><span class="sxs-lookup"><span data-stu-id="524e3-144">If you do not want to include data, do not use the `-version` and `-includedata` switches.</span></span>  
  
6.  <span data-ttu-id="524e3-145">按 Enter。</span><span class="sxs-lookup"><span data-stu-id="524e3-145">Press Enter.</span></span> <span data-ttu-id="524e3-146">成功创建包后，将显示一条消息“MDSModelDeploy 操作已成功完成”。</span><span class="sxs-lookup"><span data-stu-id="524e3-146">When the package is successfully created, a message stating "MDSModelDeploy operation completed successfully" is displayed.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="524e3-147">后续步骤</span><span class="sxs-lookup"><span data-stu-id="524e3-147">Next Steps</span></span>  
  
-   [<span data-ttu-id="524e3-148">使用 MDSModelDeploy 部署模型部署包</span><span class="sxs-lookup"><span data-stu-id="524e3-148">Deploy a Model Deployment Package by Using MDSModelDeploy</span></span>](../../2014/master-data-services/deploy-a-model-deployment-package-by-using-mdsmodeldeploy.md)  
  
## <a name="see-also"></a><span data-ttu-id="524e3-149">另请参阅</span><span class="sxs-lookup"><span data-stu-id="524e3-149">See Also</span></span>  
 <span data-ttu-id="524e3-150">[模型部署选项 &#40;Master Data Services&#41;](../../2014/master-data-services/model-deployment-options-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="524e3-150">[Model Deployment Options &#40;Master Data Services&#41;](../../2014/master-data-services/model-deployment-options-master-data-services.md) </span></span>  
 [<span data-ttu-id="524e3-151">部署模型 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="524e3-151">Deploying Models &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/deploying-models-master-data-services.md)  
  
  
