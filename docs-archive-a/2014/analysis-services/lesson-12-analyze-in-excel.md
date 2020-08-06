---
title: 第13课：在 Excel 中分析 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: ce717071-193b-4c99-9654-c7a613e16327
author: minewiskan
ms.author: owend
ms.openlocfilehash: 129956ddc8e755d1f2b298a7ea36307d50f52344
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577029"
---
# <a name="lesson-13-analyze-in-excel"></a><span data-ttu-id="d652a-102">第 13 课：在 Excel 中分析</span><span class="sxs-lookup"><span data-stu-id="d652a-102">Lesson 13: Analyze in Excel</span></span>
  <span data-ttu-id="d652a-103">在本课中，您将使用 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] 中的“在 Excel 中分析”功能打开 Microsoft Excel、自动创建到模型工作区的数据源连接以及自动将数据透视表添加到工作表。</span><span class="sxs-lookup"><span data-stu-id="d652a-103">In this lesson, you will use the Analyze in Excel feature in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] to open Microsoft Excel, automatically create a data source connection to the model workspace, and automatically add a PivotTable to the worksheet.</span></span> <span data-ttu-id="d652a-104">“在 Excel 中分析”功能提供一种快速简单的方法在部署模型之前测试模型的功效。</span><span class="sxs-lookup"><span data-stu-id="d652a-104">The Analyze in Excel feature is meant to provide a quick and easy way to test the efficacy of your model design prior to deploying your model.</span></span> <span data-ttu-id="d652a-105">在本课中，将执行数据分析。</span><span class="sxs-lookup"><span data-stu-id="d652a-105">You will not perform any data analysis in this lesson.</span></span> <span data-ttu-id="d652a-106">本课的目的是让你（模型作者）熟悉可以用来测试模型设计的工具。</span><span class="sxs-lookup"><span data-stu-id="d652a-106">The purpose of this lesson is to familiarize you, the model author, with the tools you can use to test your model design.</span></span> <span data-ttu-id="d652a-107">与模型作者使用“在 Excel 中分析”功能所不同的是，最终用户将使用客户端报告应用程序（如 Excel 或 [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)] ）来连接和浏览部署的模型数据。</span><span class="sxs-lookup"><span data-stu-id="d652a-107">Unlike using the Analyze in Excel feature, which is meant for model authors, end-users will use client reporting applications such as Excel or [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)] to connect to and browse deployed model data.</span></span>  
  
 <span data-ttu-id="d652a-108">为了完成此课程，Excel 必须与 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]安装在同一台计算机上。</span><span class="sxs-lookup"><span data-stu-id="d652a-108">In order to complete this lesson, Excel must be installed on the same computer as [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)].</span></span> <span data-ttu-id="d652a-109">若要了解详细信息，请参阅[在 Excel 中分析（SSAS 表格）](tabular-models/analyze-in-excel-ssas-tabular.md)。</span><span class="sxs-lookup"><span data-stu-id="d652a-109">To learn more, see [Analyze in Excel &#40;SSAS Tabular&#41;](tabular-models/analyze-in-excel-ssas-tabular.md).</span></span>  
  
 <span data-ttu-id="d652a-110">本课预计完成时间：**20 分钟**</span><span class="sxs-lookup"><span data-stu-id="d652a-110">Estimated time to complete this lesson: **20 minutes**</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="d652a-111">先决条件</span><span class="sxs-lookup"><span data-stu-id="d652a-111">Prerequisites</span></span>  
 <span data-ttu-id="d652a-112">本主题是表格建模教程的一部分，应当按顺序完成。</span><span class="sxs-lookup"><span data-stu-id="d652a-112">This topic is part of a tabular modeling tutorial, which should be completed in order.</span></span> <span data-ttu-id="d652a-113">在执行本课程中的任务之前，须已完成上一课： [第 11 课：创建分区](lesson-10-create-partitions.md)。</span><span class="sxs-lookup"><span data-stu-id="d652a-113">Before performing the tasks in this lesson, you should have completed the previous lesson: [Lesson 11: Create Partitions](lesson-10-create-partitions.md).</span></span>  
  
## <a name="browse-using-the-default-and-internet-sales-perspectives"></a><span data-ttu-id="d652a-114">使用默认透视和 Internet 销售透视进行浏览</span><span class="sxs-lookup"><span data-stu-id="d652a-114">Browse using the Default and Internet Sales perspectives</span></span>  
 <span data-ttu-id="d652a-115">在第一批任务中，您将使用默认透视（包含所有模型对象）和您在第 8 课“创建透视”中创建的“Internet Sales”透视来浏览您的模型。</span><span class="sxs-lookup"><span data-stu-id="d652a-115">In these first tasks, you will browse your model by using both the default perspective, which includes all model objects, and also by using the Internet Sales perspective you created in Lesson 8: Create Perspectives.</span></span> <span data-ttu-id="d652a-116">“Internet Sales”透视将排除 Customer 表对象。</span><span class="sxs-lookup"><span data-stu-id="d652a-116">The Internet Sales perspective excludes the Customer table object.</span></span>  
  
#### <a name="to-browse-by-using-the-default-perspective"></a><span data-ttu-id="d652a-117">使用默认透视进行浏览</span><span class="sxs-lookup"><span data-stu-id="d652a-117">To browse by using the Default perspective</span></span>  
  
1.  <span data-ttu-id="d652a-118">在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]中，单击 **“模型”** 菜单，然后单击 **“在 Excel 中分析”**。</span><span class="sxs-lookup"><span data-stu-id="d652a-118">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], click the **Model** menu, and then click **Analyze in Excel**.</span></span>  
  
2.  <span data-ttu-id="d652a-119">在“在 Excel 中分析”对话框中，单击“确定”。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="d652a-119">In the **Analyze in Excel** dialog box, click **OK**.</span></span>  
  
     <span data-ttu-id="d652a-120">Excel 将打开一个新的工作簿。</span><span class="sxs-lookup"><span data-stu-id="d652a-120">Excel will open with a new workbook.</span></span> <span data-ttu-id="d652a-121">将使用当前用户帐户创建一个数据源连接，默认透视将用于定义可查看字段。</span><span class="sxs-lookup"><span data-stu-id="d652a-121">A data source connection is created using the current user account and the Default perspective is used to define viewable fields.</span></span> <span data-ttu-id="d652a-122">数据透视表将自动添加到工作表中。</span><span class="sxs-lookup"><span data-stu-id="d652a-122">A Pivot table is automatically added to the worksheet.</span></span>  
  
3.  <span data-ttu-id="d652a-123">在 Excel 的 "**数据透视表字段列表**" 中，请注意，将显示 "**日期**" 和 " **internet 销售**" 度量值，以及 "**客户**"、"**日期**"、"**地域**"、"**产品**"、"产品**类别**"、"**产品子类别**" 和 " **Internet 销售**" 表，其中</span><span class="sxs-lookup"><span data-stu-id="d652a-123">In Excel, in the **PivotTable Field List**, notice the **Date** and **Internet Sales** measures appear, as well as the **Customer**, **Date**, **Geography**, **Product**, **Product Category**, **Product Subcategory**, and **Internet Sales** tables with all of their respective columns appear.</span></span>  
  
4.  <span data-ttu-id="d652a-124">关闭 Excel 且不保存工作簿。</span><span class="sxs-lookup"><span data-stu-id="d652a-124">Close Excel without saving the workbook.</span></span>  
  
#### <a name="to-browse-by-using-the-internet-sales-perspective"></a><span data-ttu-id="d652a-125">使用 Internet 销售透视进行浏览</span><span class="sxs-lookup"><span data-stu-id="d652a-125">To browse by using the Internet Sales perspective</span></span>  
  
1.  <span data-ttu-id="d652a-126">在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]中，单击 **“模型”** 菜单，然后单击 **“在 Excel 中分析”**。</span><span class="sxs-lookup"><span data-stu-id="d652a-126">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], click the **Model** menu, and then click **Analyze in Excel**.</span></span>  
  
2.  <span data-ttu-id="d652a-127">在“在 Excel 中分析”对话框中，使“当前 Windows 用户”保持选中状态，在“透视”下拉列表框中选择“Internet 销售”，并单击“确定”。\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="d652a-127">In the **Analyze in Excel** dialog box, leave **Current Windows User** selected, then in the **Perspective** drop-down listbox, select **Internet Sales**, and then click **OK**.</span></span> <span data-ttu-id="d652a-128">Excel 将打开。</span><span class="sxs-lookup"><span data-stu-id="d652a-128">Excel opens.</span></span>  
  
3.  <span data-ttu-id="d652a-129">在 Excel 的“数据透视表字段列表”\*\*\*\* 中，请注意 Customer 表已从字段列表中排除。</span><span class="sxs-lookup"><span data-stu-id="d652a-129">In Excel, in the **PivotTable Field List**, notice the Customer table is excluded from the field list.</span></span>  
  
## <a name="browse-using-roles"></a><span data-ttu-id="d652a-130">使用角色进行浏览</span><span class="sxs-lookup"><span data-stu-id="d652a-130">Browse Using Roles</span></span>  
 <span data-ttu-id="d652a-131">角色是任何表格模型中不可或缺的一部分。</span><span class="sxs-lookup"><span data-stu-id="d652a-131">Roles are an integral part of any tabular model.</span></span> <span data-ttu-id="d652a-132">一个角色都没有（用户可以作为成员添加到这些角色），用户将不能使用您的模型访问和分析数据。</span><span class="sxs-lookup"><span data-stu-id="d652a-132">Without at least one role, to which users are added as members, users will not be able to access and analyze data using your model.</span></span> <span data-ttu-id="d652a-133">“在 Excel 中分析”功能为您提供测试所定义的角色的方法。</span><span class="sxs-lookup"><span data-stu-id="d652a-133">The Analyze in Excel feature provides a way for you to test the roles you have defined.</span></span>  
  
#### <a name="to-browse-by-using-the-internet-sales-manager-user-role"></a><span data-ttu-id="d652a-134">使用“Internet Sales Manager”用户角色进行浏览</span><span class="sxs-lookup"><span data-stu-id="d652a-134">To browse by using the Internet Sales Manager user role</span></span>  
  
1.  <span data-ttu-id="d652a-135">在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]中，单击 **“模型”** 菜单，然后单击 **“在 Excel 中分析”**。</span><span class="sxs-lookup"><span data-stu-id="d652a-135">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], click the **Model** menu, and then click **Analyze in Excel**.</span></span>  
  
2.  <span data-ttu-id="d652a-136">在“在 Excel 中分析”\*\*\*\* 对话框的“指定要用于连接到模型的用户名或角色”\*\*\*\* 中，选中“角色”\*\*\*\*，然后在下拉列表框中，选中 **Internet Sales Manager**，然后单击“确定”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d652a-136">In the **Analyze in Excel** dialog box, in **Specify the user name or role to use to connect to the model**, select **Role**, and then in the drop-down listbox, select **Internet Sales Manager**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="d652a-137">Excel 将打开一个新的工作簿。</span><span class="sxs-lookup"><span data-stu-id="d652a-137">Excel will open with a new workbook.</span></span> <span data-ttu-id="d652a-138">将自动创建一个数据透视表。</span><span class="sxs-lookup"><span data-stu-id="d652a-138">A Pivot table is automatically created.</span></span> <span data-ttu-id="d652a-139">数据透视表字段列表包含您的新模型中提供的所有数据字段。</span><span class="sxs-lookup"><span data-stu-id="d652a-139">The Pivot Table Field List includes all of the data fields available in your new model.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="d652a-140">后续步骤</span><span class="sxs-lookup"><span data-stu-id="d652a-140">Next Steps</span></span>  
 <span data-ttu-id="d652a-141">要继续学习本教程，请转到下一课： [第 14 课：部署](lesson-13-deploy.md)。</span><span class="sxs-lookup"><span data-stu-id="d652a-141">To continue this tutorial, go to the next lesson: [Lesson 14: Deploy](lesson-13-deploy.md).</span></span>  
  
  
