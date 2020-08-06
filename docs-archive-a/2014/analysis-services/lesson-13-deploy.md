---
title: 第14课：部署 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 24863a8a-9017-415a-a97b-fbac76ed0675
author: minewiskan
ms.author: owend
ms.openlocfilehash: c1a55960a0c33a386d978f3c15e489ed7bd861ce
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577028"
---
# <a name="lesson-14-deploy"></a><span data-ttu-id="69ed2-102">第 14 课：部署</span><span class="sxs-lookup"><span data-stu-id="69ed2-102">Lesson 14: Deploy</span></span>
  <span data-ttu-id="69ed2-103">在本课中，您将配置部署属性；同时指定在表格模式下运行的 Analysis Services 的部署服务器实例以及为您要部署的模型指定名称。</span><span class="sxs-lookup"><span data-stu-id="69ed2-103">In this lesson, you will configure deployment properties; specifying a deployment server instance of Analysis Services running in Tabular mode, and a name for the model you deploy.</span></span> <span data-ttu-id="69ed2-104">然后，将模型部署到该实例。</span><span class="sxs-lookup"><span data-stu-id="69ed2-104">You will then deploy the model to that instance.</span></span> <span data-ttu-id="69ed2-105">部署此模型之后，用户可以使用报表客户端应用程序连接到该模型。</span><span class="sxs-lookup"><span data-stu-id="69ed2-105">After it is deployed, users can connect to the model by using a reporting client application.</span></span> <span data-ttu-id="69ed2-106">若要了解详细信息，请参阅[表格模型解决方案部署（SSAS 表格）](tabular-models/tabular-model-solution-deployment-ssas-tabular.md)。</span><span class="sxs-lookup"><span data-stu-id="69ed2-106">To learn more, see [Tabular Model Solution Deployment &#40;SSAS Tabular&#41;](tabular-models/tabular-model-solution-deployment-ssas-tabular.md).</span></span>  
  
 <span data-ttu-id="69ed2-107">学完本课的估计时间： **5 分钟**</span><span class="sxs-lookup"><span data-stu-id="69ed2-107">Estimated time to complete this lesson: **5 minutes**</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="69ed2-108">先决条件</span><span class="sxs-lookup"><span data-stu-id="69ed2-108">Prerequisites</span></span>  
 <span data-ttu-id="69ed2-109">本主题是表格建模教程的一部分，应当按顺序完成。</span><span class="sxs-lookup"><span data-stu-id="69ed2-109">This topic is part of a tabular modeling tutorial, which should be completed in order.</span></span> <span data-ttu-id="69ed2-110">在执行本课程中的任务之前，应该已完成上一课： [第 13 课：在 Excel 中分析](lesson-12-analyze-in-excel.md)。</span><span class="sxs-lookup"><span data-stu-id="69ed2-110">Before performing the tasks in this lesson, you should have completed the previous lesson: [Lesson 13: Analyze in Excel](lesson-12-analyze-in-excel.md).</span></span>  
  
## <a name="deploy-the-model"></a><span data-ttu-id="69ed2-111">部署模型</span><span class="sxs-lookup"><span data-stu-id="69ed2-111">Deploy the Model</span></span>  
  
#### <a name="to-configure-deployment-properties"></a><span data-ttu-id="69ed2-112">配置部署属性</span><span class="sxs-lookup"><span data-stu-id="69ed2-112">To configure deployment properties</span></span>  
  
1.  <span data-ttu-id="69ed2-113">在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] 的“解决方案资源管理器”\*\*\*\* 中，右键单击“Adventure Works Internet Sales Tabular Model”\*\*\*\* 项目，然后在上下文菜单中单击“属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="69ed2-113">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], in **Solution Explorer**, right-click on the **Adventure Works Internet Sales Tabular Model** project, and then in the context menu, click **Properties**.</span></span>  
  
2.  <span data-ttu-id="69ed2-114">在“AW Internet Sales Tabular Model 属性页”\*\*\*\* 对话框中，在“部署服务器”\*\*\*\* 下的“服务器”\*\*\*\* 属性中，键入在表格模式下运行的 Analysis Services 实例的名称。</span><span class="sxs-lookup"><span data-stu-id="69ed2-114">In the **AW Internet Sales Tabular Model Property Pages** dialog box, under **Deployment Server**, in the **Server** property, type the name of an Analysis Services instance running in Tabular mode.</span></span> <span data-ttu-id="69ed2-115">这将是您的模型将被部署到的实例。</span><span class="sxs-lookup"><span data-stu-id="69ed2-115">This will be the instance your model will be deployed to.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="69ed2-116">您必须对远程 Analysis Services 实例具有管理员权限，才能将模型部署到该实例。</span><span class="sxs-lookup"><span data-stu-id="69ed2-116">You must have Administrator permissions on a remote Analysis Services instance in-order to deploy to it.</span></span>  
  
3.  <span data-ttu-id="69ed2-117">验证 "**查询模式**" 属性是否设置为 **"内存中**"。</span><span class="sxs-lookup"><span data-stu-id="69ed2-117">Verify the **Query Mode** property is set to **In-Memory**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="69ed2-118">在 DirectQuery 模式下，不支持使用本教程创建的模型。</span><span class="sxs-lookup"><span data-stu-id="69ed2-118">The model created by using this tutorial is not supported in DirectQuery mode.</span></span>  
  
4.  <span data-ttu-id="69ed2-119">在 "**数据库**" 属性中，键入 `Adventure Works Internet Sales Model` 。</span><span class="sxs-lookup"><span data-stu-id="69ed2-119">In the **Database** property, type `Adventure Works Internet Sales Model`.</span></span>  
  
5.  <span data-ttu-id="69ed2-120">在 "**多维数据集**名称" 属性中，键入 `Adventure Works Internet Sales Model` 。</span><span class="sxs-lookup"><span data-stu-id="69ed2-120">In the **Cube** Name property, type `Adventure Works Internet Sales Model`.</span></span>  
  
6.  <span data-ttu-id="69ed2-121">验证你的选择，并单击“确定”。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="69ed2-121">Verify your selections and then click **OK**.</span></span>  
  
#### <a name="to-deploy-the-adventure-works-internet-sales-tabular-model"></a><span data-ttu-id="69ed2-122">部署 Adventure Works Internet Sales 表格模型</span><span class="sxs-lookup"><span data-stu-id="69ed2-122">To deploy the Adventure Works Internet Sales tabular model</span></span>  
  
1.  <span data-ttu-id="69ed2-123">在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] 中，单击“生成”\*\*\*\* 菜单，然后单击“部署 AW Internet Sales Tabular Model”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="69ed2-123">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], click the **Build** menu, and then click **Deploy AW Internet Sales Tabular Model**.</span></span>  
  
     <span data-ttu-id="69ed2-124">“部署”对话框将出现，并且显示模型中包括的元数据和每个表的部署状态。</span><span class="sxs-lookup"><span data-stu-id="69ed2-124">The Deploy dialog box appears and displays the deployment status of the metadata as well as each table included in the model.</span></span>  
  
## <a name="conclusion"></a><span data-ttu-id="69ed2-125">结论</span><span class="sxs-lookup"><span data-stu-id="69ed2-125">Conclusion</span></span>  
 <span data-ttu-id="69ed2-126">恭喜！</span><span class="sxs-lookup"><span data-stu-id="69ed2-126">Congratulations!</span></span> <span data-ttu-id="69ed2-127">您已完成了创作和部署第一个 Analysis Services 表格模型的过程。</span><span class="sxs-lookup"><span data-stu-id="69ed2-127">You are finished authoring and deploying your first Analysis Services tabular model.</span></span> <span data-ttu-id="69ed2-128">本教程已帮助指导您完成了创建表格模型的最常见任务。</span><span class="sxs-lookup"><span data-stu-id="69ed2-128">This tutorial has helped guide you through completing the most common tasks in creating a tabular model.</span></span> <span data-ttu-id="69ed2-129">既然已部署了 Adventure Works Internet Sales Model，就可以使用 SQL Server Management Studio 来管理此模型、创建进程脚本和备份计划。</span><span class="sxs-lookup"><span data-stu-id="69ed2-129">Now that your Adventure Works Internet Sales Model is deployed, you can use SQL Server Management Studio to manage the model; create process scripts and a backup plan.</span></span> <span data-ttu-id="69ed2-130">用户可以使用报表客户端应用程序（如 Microsoft Excel 或 [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)]）连接到此模型。</span><span class="sxs-lookup"><span data-stu-id="69ed2-130">Users can connect to the model using a reporting client application such as Microsoft Excel or [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)].</span></span>  
  
## <a name="additional-resources"></a><span data-ttu-id="69ed2-131">其他资源</span><span class="sxs-lookup"><span data-stu-id="69ed2-131">Additional Resources</span></span>  
 <span data-ttu-id="69ed2-132">若要了解有关支持 [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)] 报表的表格模型属性的详细信息，请参阅 [Power View 报表属性（SSAS 表格）](tabular-models/properties-ssas-tabular.md)。</span><span class="sxs-lookup"><span data-stu-id="69ed2-132">To learn more about tabular model properties that support [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)] reports, see [Power View Reporting Properties &#40;SSAS Tabular&#41;](tabular-models/properties-ssas-tabular.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69ed2-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="69ed2-133">See Also</span></span>  
 <span data-ttu-id="69ed2-134">[DirectQuery 模式 &#40;SSAS 表格&#41;](tabular-models/directquery-mode-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="69ed2-134">[DirectQuery Mode &#40;SSAS Tabular&#41;](tabular-models/directquery-mode-ssas-tabular.md) </span></span>  
 <span data-ttu-id="69ed2-135">[&#40;SSAS 表格&#41;配置默认数据建模和部署属性](tabular-models/configure-default-data-modeling-and-deployment-properties-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="69ed2-135">[Configure Default Data Modeling and Deployment Properties &#40;SSAS Tabular&#41;](tabular-models/configure-default-data-modeling-and-deployment-properties-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="69ed2-136">表格模型数据库（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="69ed2-136">Tabular Model Databases &#40;SSAS Tabular&#41;</span></span>](tabular-models/tabular-model-databases-ssas-tabular.md)  
  
  
