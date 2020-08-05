---
title: 在 Data Quality Client 中打开 Integration Services 项目 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: a8bad2f1-8fb0-4d14-a978-11a5720e62d6
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: fd29bbba274535d6489eb8d188aa4f0150ed7c4b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580383"
---
# <a name="open-integration-services-projects-in-data-quality-client"></a><span data-ttu-id="e9bfb-102">在数据质量客户端中打开 Integration Services 项目</span><span class="sxs-lookup"><span data-stu-id="e9bfb-102">Open Integration Services Projects in Data Quality Client</span></span>
  <span data-ttu-id="e9bfb-103">通过 [!INCLUDE[ssDQSCleansingLong](../includes/ssdqscleansinglong-md.md)] ，您可以在批处理模式下运行清理项目。</span><span class="sxs-lookup"><span data-stu-id="e9bfb-103">The [!INCLUDE[ssDQSCleansingLong](../includes/ssdqscleansinglong-md.md)] enables you to run a cleansing project in batch mode.</span></span> <span data-ttu-id="e9bfb-104">但是，有时您可能想要查看 Integration Services 包中的清理结果，这类似于您在 DQS 的数据质量项目中，在清理活动的 **“管理和查看结果”** 选项卡中查看清理结果。</span><span class="sxs-lookup"><span data-stu-id="e9bfb-104">However, at times you might want to review the cleansing results in an Integration Services package similar to how you can review the cleansing results in the **Manage and View Results** tab of a cleansing activity in a data quality project in DQS.</span></span> <span data-ttu-id="e9bfb-105">通过 DQS，您可以在 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 中打开 Integration Services 项目，就像从 **“打开项目”** 屏幕打开任何其他数据质量项目一样，并且您将具有在 Integration Services 项目中清理结果的交互式清理体验。</span><span class="sxs-lookup"><span data-stu-id="e9bfb-105">DQS enables you to open Integration Services projects in [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] just like any other data quality project from the **Open project** screen, and have an interactive cleansing experience of the cleansing results in an Integration Services project.</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="e9bfb-106">开始之前</span><span class="sxs-lookup"><span data-stu-id="e9bfb-106">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> <span data-ttu-id="e9bfb-107">限制和局限</span><span class="sxs-lookup"><span data-stu-id="e9bfb-107">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="e9bfb-108">**的** “打开项目” [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]屏幕中仅提供已完成的 Integration Services 项目。</span><span class="sxs-lookup"><span data-stu-id="e9bfb-108">Only completed Integration Services projects are available in the **Open project** screen in [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)].</span></span> <span data-ttu-id="e9bfb-109">**“打开项目”** 屏幕中不提供失败或正在运行的项目。</span><span class="sxs-lookup"><span data-stu-id="e9bfb-109">Failed or running projects are not available in the **Open project** screen.</span></span>  
  
-   <span data-ttu-id="e9bfb-110">Integration Services 项目在**中打开时会进入交互式清理阶段（** “管理和查看结果” [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]选项卡）。</span><span class="sxs-lookup"><span data-stu-id="e9bfb-110">Integration Services projects open at the interactive cleansing stage (**Manage View and Results** tab) in [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)].</span></span> <span data-ttu-id="e9bfb-111">您无法进入 **“清理”** 或 **“映射”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="e9bfb-111">You cannot go to the **Cleanse** or **Map** tabs.</span></span> <span data-ttu-id="e9bfb-112">只能通过单击 **“下一步”** 转到 **“导出”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="e9bfb-112">You can only go to the **Export** tab by clicking **Next**.</span></span>  
  
-   <span data-ttu-id="e9bfb-113">您无法从 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]中删除锁定的 Integration Services 项目。</span><span class="sxs-lookup"><span data-stu-id="e9bfb-113">You cannot delete a locked Integration Services project from [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)].</span></span> <span data-ttu-id="e9bfb-114">您必须先对其解锁后才能删除。</span><span class="sxs-lookup"><span data-stu-id="e9bfb-114">You must first unlock it to delete.</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a><span data-ttu-id="e9bfb-115">先决条件</span><span class="sxs-lookup"><span data-stu-id="e9bfb-115">Prerequisites</span></span>  
 <span data-ttu-id="e9bfb-116">您必须成功完成运行包含某个包以及 DQS 清理组件的 Integration Services 项目，然后才能在 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]中查看并打开该项目。</span><span class="sxs-lookup"><span data-stu-id="e9bfb-116">You must have successfully completed running an Integration Services project containing a package with a DQS Cleansing component to see and open it in [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)].</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="e9bfb-117">Security</span><span class="sxs-lookup"><span data-stu-id="e9bfb-117">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="e9bfb-118">权限</span><span class="sxs-lookup"><span data-stu-id="e9bfb-118">Permissions</span></span>  
 <span data-ttu-id="e9bfb-119">您必须对 DQS_MAIN 数据库具有 dqs_kb_editor 或 dqs_kb_operator 角色，才能打开 Integration Services 项目。</span><span class="sxs-lookup"><span data-stu-id="e9bfb-119">You must have the dqs_kb_editor or dqs_kb_operator role on the DQS_MAIN database to open an Integration Services project.</span></span>  
  
##  <a name="open-an-integration-services-project"></a><a name="Open"></a> <span data-ttu-id="e9bfb-120">打开 Integration Services 项目</span><span class="sxs-lookup"><span data-stu-id="e9bfb-120">Open an Integration Services Project</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="e9bfb-121">[运行 Data Quality Client 应用程序](../../2014/data-quality-services/run-the-data-quality-client-application.md)。</span><span class="sxs-lookup"><span data-stu-id="e9bfb-121">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="e9bfb-122">在 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 主屏幕中，单击 "**打开数据质量项目**"。</span><span class="sxs-lookup"><span data-stu-id="e9bfb-122">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, click **Open Data Quality Project**.</span></span> <span data-ttu-id="e9bfb-123">将出现 **“打开项目”** 屏幕。</span><span class="sxs-lookup"><span data-stu-id="e9bfb-123">The **Open project** screen appears.</span></span>  
  
3.  <span data-ttu-id="e9bfb-124">在 **“打开项目”** 屏幕上，可以通过以下方式之一标识 Integration Services 项目：</span><span class="sxs-lookup"><span data-stu-id="e9bfb-124">In the **Open project** screen, you can identify an Integration Services project in either of the following ways:</span></span>  
  
    1.  <span data-ttu-id="e9bfb-125">**项目名称**：使用以下命名术语列出 Integration Services 项目： "PACKAGE. DQS Cleansing_ *\<DATE>\*\*\<TIME>* _ {GUID}"。</span><span class="sxs-lookup"><span data-stu-id="e9bfb-125">**Project Name**: Integration Services projects are listed using the following naming terminology: "Package.DQS Cleansing_*\<DATE>\*\*\<TIME>*_{GUID}."</span></span> <span data-ttu-id="e9bfb-126">每次成功地在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中运行同一个包，就会在“打开项目”屏幕中列出一个新项目。 \*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="e9bfb-126">Every time you successfully run the same package in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], a new project is listed in the **Open project** screen.</span></span>  
  
    2.  <span data-ttu-id="e9bfb-127">**“项目类型”**：在 **“打开项目”** 屏幕中，Integration Services 项目具有 **SSIS** 作为项目类型。</span><span class="sxs-lookup"><span data-stu-id="e9bfb-127">**Project Type**: Integration Services projects have **SSIS** as the project type in the **Open project** screen.</span></span>  
  
     <span data-ttu-id="e9bfb-128">选择一个项目，然后单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="e9bfb-128">Select a project, and click **Next**.</span></span>  
  
4.  <span data-ttu-id="e9bfb-129">Integration Services 项目将打开并进入交互式清理阶段（**“管理和查看结果”** 选项卡）。</span><span class="sxs-lookup"><span data-stu-id="e9bfb-129">The Integration Services project opens at the interactive cleansing stage (**Manage View and Results** tab).</span></span> <span data-ttu-id="e9bfb-130">您可以对 Integration Services 项目中的数据执行交互式清理。</span><span class="sxs-lookup"><span data-stu-id="e9bfb-130">You can perform an interactive cleansing on the data in the Integration Services project.</span></span> <span data-ttu-id="e9bfb-131">有关“管理和查看结果”选项卡的详细信息，请参阅[使用 DQS（内部）知识清理数据](../../2014/data-quality-services/cleanse-data-using-dqs-internal-knowledge.md)中的[交互式清理阶段](../../2014/data-quality-services/cleanse-data-using-dqs-internal-knowledge.md#Interactive)\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e9bfb-131">For detailed information about the **Manage and View Results** tab, see [Interactive Cleansing Stage](../../2014/data-quality-services/cleanse-data-using-dqs-internal-knowledge.md#Interactive) in [Cleanse Data Using DQS &#40;Internal&#41; Knowledge](../../2014/data-quality-services/cleanse-data-using-dqs-internal-knowledge.md).</span></span>  
  
5.  <span data-ttu-id="e9bfb-132">单击 **“下一步”** 以转到 **“导出”** 选项卡，您可以在此处将处理后的数据导出到以下任一位置：SQL Server 数据库中的新表、.csv 文件或 Excel 文件。</span><span class="sxs-lookup"><span data-stu-id="e9bfb-132">Click **Next** to go to the **Export** tab where you can export the processed data to any of the following: a new table in the SQL Server database, a .csv file, or an Excel file.</span></span> <span data-ttu-id="e9bfb-133">有关“导出”选项卡的详细信息，请参阅[使用 DQS（内部）知识清理数据](../../2014/data-quality-services/cleanse-data-using-dqs-internal-knowledge.md)中的[导出阶段](../../2014/data-quality-services/cleanse-data-using-dqs-internal-knowledge.md#Export)\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="e9bfb-133">For detailed information about the **Export** tab, see [Export Stage](../../2014/data-quality-services/cleanse-data-using-dqs-internal-knowledge.md#Export) in [Cleanse Data Using DQS &#40;Internal&#41; Knowledge](../../2014/data-quality-services/cleanse-data-using-dqs-internal-knowledge.md)</span></span>  
  
6.  <span data-ttu-id="e9bfb-134">导出数据后，单击 **“完成”** 以关闭 Integration Services 项目。</span><span class="sxs-lookup"><span data-stu-id="e9bfb-134">After exporting the data, click **Finish** to close the Integration Services project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9bfb-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e9bfb-135">See Also</span></span>  
 <span data-ttu-id="e9bfb-136">[DQS 清理转换](../integration-services/data-flow/transformations/dqs-cleansing-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="e9bfb-136">[DQS Cleansing Transformation](../integration-services/data-flow/transformations/dqs-cleansing-transformation.md) </span></span>  
 [<span data-ttu-id="e9bfb-137">Integration Services (SSIS) 项目</span><span class="sxs-lookup"><span data-stu-id="e9bfb-137">Integration Services &#40;SSIS&#41; Projects</span></span>](../integration-services/integration-services-ssis-projects-and-solutions.md)  
