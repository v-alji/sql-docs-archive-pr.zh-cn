---
title: 从 SQL Server Data Tools (SSAS 表格) 部署 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.deploystatus.f1
ms.assetid: 67dde3fe-ba43-41f3-b56c-c656029ee93f
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8bc8008e7c79e1652b54b21e6afb116301d1700b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587618"
---
# <a name="deploy-from-sql-server-data-tools-ssas-tabular"></a><span data-ttu-id="6c183-102">从 SQL Server Data Tools 进行部署（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="6c183-102">Deploy From SQL Server Data Tools (SSAS Tabular)</span></span>
  <span data-ttu-id="6c183-103">使用本主题中的任务以通过在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中使用“部署”命令来部署表格模型解决方案。</span><span class="sxs-lookup"><span data-stu-id="6c183-103">Use the tasks in this topic to deploy a tabular model solution by using the Deploy command in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="6c183-104">本主题的内容：</span><span class="sxs-lookup"><span data-stu-id="6c183-104">Sections in this topic:</span></span>  
  
-   [<span data-ttu-id="6c183-105">配置部署选项和部署服务器属性</span><span class="sxs-lookup"><span data-stu-id="6c183-105">Configure Deployment Options and Deployment Server Properties</span></span>](#bkmk_deploy)  
  
-   [<span data-ttu-id="6c183-106">部署表格模型解决方案</span><span class="sxs-lookup"><span data-stu-id="6c183-106">Deploy a Tabular Model Solution</span></span>](#bkmk_deploy_proc)  
  
-   [<span data-ttu-id="6c183-107">部署状态</span><span class="sxs-lookup"><span data-stu-id="6c183-107">Deploy Status</span></span>](#bkmk_deploy_status)  
  
##  <a name="configure-deployment-options-and-deployment-server-properties"></a><a name="bkmk_deploy"></a><span data-ttu-id="6c183-108">配置部署选项和部署服务器属性</span><span class="sxs-lookup"><span data-stu-id="6c183-108">Configure Deployment Options and Deployment Server Properties</span></span>  
 <span data-ttu-id="6c183-109">在您部署表格模型解决方案之前，必须首先指定“部署选项”属性和“部署服务器”属性。</span><span class="sxs-lookup"><span data-stu-id="6c183-109">Before you deploy your tabular model solution, you must first specify the Deployment Options and Deployment Server properties.</span></span> <span data-ttu-id="6c183-110">有关部署属性和设置的详细信息，请参阅 [表格模型解决方案部署（SSAS 表格）](tabular-model-solution-deployment-ssas-tabular.md)中使用“部署”命令来部署表格模型解决方案。</span><span class="sxs-lookup"><span data-stu-id="6c183-110">For more information about deployment properties and settings, see [Tabular Model Solution Deployment &#40;SSAS Tabular&#41;](tabular-model-solution-deployment-ssas-tabular.md).</span></span>  
  
#### <a name="to-configure-deployment-options-and-deployment-server-properties"></a><span data-ttu-id="6c183-111">配置“部署选项”和“部署服务器”属性</span><span class="sxs-lookup"><span data-stu-id="6c183-111">To configure Deployment Options and Deployment Server properties</span></span>  
  
1.  <span data-ttu-id="6c183-112">在 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] 中的“解决方案资源管理器”\*\*\*\* 中，右键单击项目名称，再单击“属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6c183-112">In [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], in **Solution Explorer**, right-click the project name, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="6c183-113">在 " \*\* \<project name> 属性**" 对话框的 "**部署选项\*\*" 中，指定属性设置（如果不同于默认设置）。</span><span class="sxs-lookup"><span data-stu-id="6c183-113">In the **\<project name> Properties** dialog, in **Deployment Options**, specify property settings if different from the default settings.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6c183-114">对于缓存模式下的模型，“查询模式”\*\*\*\* 始终为“内存中”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6c183-114">For models in cached mode, **Query Mode** is always **In-Memory**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6c183-115">不能为 DirectQuery 模式下的模型指定“模拟设置”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6c183-115">You cannot specify **Impersonation Settings** for models in DirectQuery mode.</span></span>  
  
3.  <span data-ttu-id="6c183-116">在“部署服务器”\*\*\*\* 中，指定“服务器”\*\*\*\*（名称）、“版本”\*\*\*\*、“数据库”（名称）\*\*\*\* 和“多维数据集名称”\*\*\*\* 属性设置（如果这些设置不同于默认设置），然后单击“确定”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6c183-116">In **Deployment Server**, specify the **Server** (name), **Edition**, **Database** (name), and **Cube Name** property settings, if different from the default settings, and then click **OK**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6c183-117">还可以指定“默认部署服务器”属性设置，以便您创建的任何新项目将自动部署到指定的服务器。</span><span class="sxs-lookup"><span data-stu-id="6c183-117">You can also specify the Default Deployment Server property setting so any new projects you create will automatically be deployed to the specified server.</span></span> <span data-ttu-id="6c183-118">有关详细信息，请参阅 [配置默认数据建模和部署属性（SSAS 表格）](properties-ssas-tabular.md)。</span><span class="sxs-lookup"><span data-stu-id="6c183-118">For more information, see [Configure Default Data Modeling and Deployment Properties &#40;SSAS Tabular&#41;](properties-ssas-tabular.md).</span></span>  
  
##  <a name="deploy-a-tabular-model-solution"></a><a name="bkmk_deploy_proc"></a><span data-ttu-id="6c183-119">部署表格模型解决方案</span><span class="sxs-lookup"><span data-stu-id="6c183-119">Deploy a Tabular Model Solution</span></span>  
  
#### <a name="to-deploy-a-tabular-model-solution"></a><span data-ttu-id="6c183-120">部署表格模型解决方案</span><span class="sxs-lookup"><span data-stu-id="6c183-120">To deploy a tabular model solution</span></span>  
  
-   <span data-ttu-id="6c183-121">在 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] 的 "**生成**" 菜单上，单击 "\*\*部署 \<project name> \*\*"。</span><span class="sxs-lookup"><span data-stu-id="6c183-121">In [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], on the **Build** menu, click **Deploy \<project name>**.</span></span>  
  
     <span data-ttu-id="6c183-122">“部署”\*\*\*\* 对话框将出现，并且指示在模型中包括的每个表的元数据部署和处理的状态（除非将“处理选项”属性设置为“不处理”）。</span><span class="sxs-lookup"><span data-stu-id="6c183-122">The **Deploy** dialog box will appear and indicate the status of the metadata deployment and the processing (unless Processing Option property is set to Do Not Process) of each table included in the model.</span></span> <span data-ttu-id="6c183-123">在部署过程完成后，使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 连接到 Analysis Services 实例并且确认已创建新的模型数据库对象或使用客户端报告应用程序连接到已部署的模型。</span><span class="sxs-lookup"><span data-stu-id="6c183-123">After the deployment process is complete, use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to connect to the Analysis Services instance and verify the new model database object has been created or use a client reporting application to connect to the deployed model.</span></span>  
  
##  <a name="deploy-status"></a><a name="bkmk_deploy_status"></a> <span data-ttu-id="6c183-124">部署状态</span><span class="sxs-lookup"><span data-stu-id="6c183-124">Deploy Status</span></span>  
 <span data-ttu-id="6c183-125">通过 **“部署”** 对话框，您可以监视“部署”操作的进度。</span><span class="sxs-lookup"><span data-stu-id="6c183-125">The **Deploy** dialog box enables you to monitor the progress of a Deploy operation.</span></span> <span data-ttu-id="6c183-126">也可以停止部署操作。</span><span class="sxs-lookup"><span data-stu-id="6c183-126">A deploy operation can also be stopped.</span></span>  
  
 <span data-ttu-id="6c183-127">**Status**</span><span class="sxs-lookup"><span data-stu-id="6c183-127">**Status**</span></span>  
 <span data-ttu-id="6c183-128">指示部署操作成功与否。</span><span class="sxs-lookup"><span data-stu-id="6c183-128">Indicates whether the Deploy operation was successful or not.</span></span>  
  
 <span data-ttu-id="6c183-129">**详细信息**</span><span class="sxs-lookup"><span data-stu-id="6c183-129">**Details**</span></span>  
 <span data-ttu-id="6c183-130">列出已部署的元数据项、每个元数据项的状态并提供针对任何问题的一条消息。</span><span class="sxs-lookup"><span data-stu-id="6c183-130">Lists the metadata items that were deployed, the status for each metadata item, and provides a message of any issues.</span></span>  
  
 <span data-ttu-id="6c183-131">**停止部署**</span><span class="sxs-lookup"><span data-stu-id="6c183-131">**Stop Deploy**</span></span>  
 <span data-ttu-id="6c183-132">单击此选项可以暂停部署操作。</span><span class="sxs-lookup"><span data-stu-id="6c183-132">Click to halt the Deploy operation.</span></span> <span data-ttu-id="6c183-133">如果部署操作用时过长或出现太多错误，则此选项很有用。</span><span class="sxs-lookup"><span data-stu-id="6c183-133">This option is useful if the Deploy operation is taking too long, or if there are too many errors.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c183-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6c183-134">See Also</span></span>  
 <span data-ttu-id="6c183-135">[&#40;SSAS 表格部署的表格模型解决方案部署&#41;](tabular-model-solution-deployment-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="6c183-135">[Tabular Model Solution Deployment &#40;SSAS Tabular&#41;](tabular-model-solution-deployment-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="6c183-136">配置默认数据建模和部署属性（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="6c183-136">Configure Default Data Modeling and Deployment Properties &#40;SSAS Tabular&#41;</span></span>](properties-ssas-tabular.md)  
  
  
