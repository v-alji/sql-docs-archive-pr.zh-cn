---
title: 数据质量项目 (DQS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: a43fc9c0-19b6-414a-8661-4c7c55e0c03e
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 471d528144b6687ffa3aeedb82cf479817c4edc0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579060"
---
# <a name="data-quality-projects-dqs"></a><span data-ttu-id="c7c78-102">数据质量项目 (DQS)</span><span class="sxs-lookup"><span data-stu-id="c7c78-102">Data Quality Projects (DQS)</span></span>
  <span data-ttu-id="c7c78-103">[!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) 中的数据质量项目就是使用知识库，通过执行“数据清理” \*\* 和 \*\* “数据匹配”活动改进源数据的质量，然后将结果数据导出到 SQL Server 数据库或 .csv 文件。</span><span class="sxs-lookup"><span data-stu-id="c7c78-103">A data quality project in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) is a means of using a knowledge base to improve the quality of your source data by performing *data cleansing* and *data matching* activities, and then exporting the resultant data to a SQL Server database or a .csv file.</span></span> <span data-ttu-id="c7c78-104">您可以将数据质量项目创建为一个清理项目或匹配项目，以执行相应的任务。</span><span class="sxs-lookup"><span data-stu-id="c7c78-104">You can create a data quality project as a cleansing project or a matching project to perform respective activities.</span></span> <span data-ttu-id="c7c78-105">可以通过使用同一个知识库运行清理项目和匹配项目，因为用于数据清理和匹配的知识可以内置于同一个知识库中。</span><span class="sxs-lookup"><span data-stu-id="c7c78-105">Cleansing and matching projects can be run using the same knowledge base, because knowledge for data cleansing and matching can be built into the same knowledge base.</span></span>  
  
 <span data-ttu-id="c7c78-106">数据质量项目具有以下优点：</span><span class="sxs-lookup"><span data-stu-id="c7c78-106">A data quality project has the following benefits:</span></span>  
  
-   <span data-ttu-id="c7c78-107">使您可以通过使用 DQS 知识库中的知识对您的数据源执行数据清理。</span><span class="sxs-lookup"><span data-stu-id="c7c78-107">Enables you to perform data cleansing on your source data by using the knowledge in a DQS knowledge base.</span></span>  
  
-   <span data-ttu-id="c7c78-108">使您可以通过使用知识库中的匹配策略对您的数据源执行数据匹配。</span><span class="sxs-lookup"><span data-stu-id="c7c78-108">Enables you to perform data matching on your source data by using the matching policy in a knowledge base.</span></span>  
  
-   <span data-ttu-id="c7c78-109">提供一个向导，指导您完成整个清理活动和匹配活动，并根据您的选择将数据导出到 SQL Server 数据库或 .csv 文件。</span><span class="sxs-lookup"><span data-stu-id="c7c78-109">Provides a wizard to guide you through the cleansing and matching activities, and export the data as per your selection to a SQL Server database or to a .csv file.</span></span> <span data-ttu-id="c7c78-110">数据专员可以使用数据质量项目来运行并控制计算机辅助/交互方式清理步骤和数据匹配步骤。</span><span class="sxs-lookup"><span data-stu-id="c7c78-110">The data steward can use the data quality project to run and control the computer-assisted/interactive cleansing and data matching steps.</span></span>  
  
##  <a name="data-quality-project-cleansing-activity"></a><a name="Cleansing"></a><span data-ttu-id="c7c78-111">数据质量项目：清理活动</span><span class="sxs-lookup"><span data-stu-id="c7c78-111">Data Quality Project: Cleansing Activity</span></span>  
 <span data-ttu-id="c7c78-112">清理数据质量项目使您可以基于知识库清理您的源数据。</span><span class="sxs-lookup"><span data-stu-id="c7c78-112">A cleansing data quality project enables you to cleanse your source data based on a knowledge base.</span></span> <span data-ttu-id="c7c78-113">DQS 中的数据清理活动分为两个步骤：</span><span class="sxs-lookup"><span data-stu-id="c7c78-113">The data cleansing activity in DQS is a two-step process:</span></span>  
  
1.  <span data-ttu-id="c7c78-114">“计算机辅助” \*\* 数据清理过程，可以针对知识库中的知识分析源数据并提出更改建议。</span><span class="sxs-lookup"><span data-stu-id="c7c78-114">A *computer-assisted* data cleansing process that analyzes source data against the knowledge in the knowledge base, and proposes changes.</span></span> <span data-ttu-id="c7c78-115">DQS 对处理后的数据进行分类（建议、新建、无效、已更正和正确），然后向用户显示以供进一步处理。</span><span class="sxs-lookup"><span data-stu-id="c7c78-115">The processed data is categorized (suggested, new, invalid, corrected, and correct) by DQS, and displayed to the user for further processing.</span></span>  
  
2.  <span data-ttu-id="c7c78-116">“交互式” \*\* 清理过程，使数据专员可以批准、拒绝或修改计算机辅助数据清理过程建议的数据。</span><span class="sxs-lookup"><span data-stu-id="c7c78-116">An *interactive* cleansing process that enables the data steward to approve, reject, or modify the data proposed by the computer-assisted data cleansing process.</span></span>  
  
 <span data-ttu-id="c7c78-117">有关数据质量项目中的清理活动的详细信息，请参阅 [Data Cleansing](../../2014/data-quality-services/data-cleansing.md)。</span><span class="sxs-lookup"><span data-stu-id="c7c78-117">For detailed information about the cleansing activity in a data quality project, see [Data Cleansing](../../2014/data-quality-services/data-cleansing.md).</span></span>  
  
##  <a name="data-quality-project-matching-activity"></a><a name="Matching"></a><span data-ttu-id="c7c78-118">数据质量项目：匹配活动</span><span class="sxs-lookup"><span data-stu-id="c7c78-118">Data Quality Project: Matching Activity</span></span>  
 <span data-ttu-id="c7c78-119">匹配数据质量项目支持您基于知识库中的匹配策略执行匹配活动，通过标识精确匹配项和近似匹配项，进而删除重复数据，以防止数据重复。</span><span class="sxs-lookup"><span data-stu-id="c7c78-119">A matching data quality project enables you to perform matching activity based on matching policy in a knowledge base to prevent data duplication by identifying exact and approximate matches, and thereby enabling you to remove duplicate data.</span></span> <span data-ttu-id="c7c78-120">建议先清除数据，然后再运行匹配。</span><span class="sxs-lookup"><span data-stu-id="c7c78-120">It is recommended that you cleanse your data before running matching on it.</span></span> <span data-ttu-id="c7c78-121">执行此操作的步骤：</span><span class="sxs-lookup"><span data-stu-id="c7c78-121">To do so:</span></span>  
  
1.  <span data-ttu-id="c7c78-122">创建数据质量项目，选择 **“清理”** 活动，对源数据完成数据清理活动，然后将其导出到 SQL Server 数据库中的表。</span><span class="sxs-lookup"><span data-stu-id="c7c78-122">Create a data quality project, select the **Cleansing** activity, complete the data cleansing activity on your source data, and then export it to a table in a SQL Server database.</span></span>  
  
2.  <span data-ttu-id="c7c78-123">通过使用包含匹配策略的知识库创建另一个数据质量项目，选择 **“匹配”** 活动，然后在 **“映射”** 页中，选择在步骤 1 中导出已清理数据的数据库和表。</span><span class="sxs-lookup"><span data-stu-id="c7c78-123">Create another data quality project by using a knowledge base that contains a matching policy, select the **Matching** activity, and then in the **Map** page, select the database and the table where you exported the cleansed data in step 1.</span></span>  
  
3.  <span data-ttu-id="c7c78-124">完成针对已清理数据的匹配活动。</span><span class="sxs-lookup"><span data-stu-id="c7c78-124">Complete the matching activity on the cleansed data.</span></span>  
  
 <span data-ttu-id="c7c78-125">有关数据质量项目中的匹配活动的详细信息，请参阅 [Data Matching](../../2014/data-quality-services/data-matching.md)。</span><span class="sxs-lookup"><span data-stu-id="c7c78-125">For detailed information about the matching activity in a data quality project, see [Data Matching](../../2014/data-quality-services/data-matching.md).</span></span>  
  
##  <a name="data-profiling-and-notifications"></a><a name="ProfilingNotification"></a><span data-ttu-id="c7c78-126">数据事件探查和通知</span><span class="sxs-lookup"><span data-stu-id="c7c78-126">Data Profiling and Notifications</span></span>  
 <span data-ttu-id="c7c78-127">在数据质量项目中运行清理和匹配活动时，可查看与正由 DQS 处理的数据有关的实时统计信息和其他信息。</span><span class="sxs-lookup"><span data-stu-id="c7c78-127">While running the cleansing and matching activities in a data quality project, you can see real-time statistics and information about the data that is being processed by DQS.</span></span> <span data-ttu-id="c7c78-128">数据事件探查可帮助您评估清理或匹配过程的有效性，并且您可能能够确定数据清理或数据匹配在多大程度上可帮助您提高数据质量。</span><span class="sxs-lookup"><span data-stu-id="c7c78-128">Data profiling helps you assess the effectiveness of the cleansing and matching processes, and you can potentially determine the extent to which data cleansing or matching helped improve the data quality.</span></span> <span data-ttu-id="c7c78-129">DQS 事件探查提供两种数据质量维度：“完整性” \*\* （提供数据的范围）和“准确性” \*\* （数据可用于目标用途的程度）。</span><span class="sxs-lookup"><span data-stu-id="c7c78-129">DQS profiling provides two data-quality dimensions: *completeness* (the extent to which data is present) and *accuracy* (the extent to which data can be used for its intended use).</span></span> <span data-ttu-id="c7c78-130">此外，根据数据事件探查信息，对用户显示相关的通知，告知用户可以通过采取哪些措施来改善数据清理和数据匹配操作。</span><span class="sxs-lookup"><span data-stu-id="c7c78-130">Further, based on the data profiling information, notifications are displayed to the user on the actions that can be taken to enhance the data cleansing and data matching operations.</span></span> <span data-ttu-id="c7c78-131">有关数据事件探查和通知的详细信息，请参阅 [Data Profiling and Notifications in DQS](../../2014/data-quality-services/data-profiling-and-notifications-in-dqs.md)。</span><span class="sxs-lookup"><span data-stu-id="c7c78-131">For detailed information about data profiling and notifications, see [Data Profiling and Notifications in DQS](../../2014/data-quality-services/data-profiling-and-notifications-in-dqs.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="c7c78-132">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="c7c78-132">Related Tasks</span></span>  
  
|<span data-ttu-id="c7c78-133">任务说明</span><span class="sxs-lookup"><span data-stu-id="c7c78-133">Task Description</span></span>|<span data-ttu-id="c7c78-134">主题</span><span class="sxs-lookup"><span data-stu-id="c7c78-134">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="c7c78-135">描述如何创建数据质量项目。</span><span class="sxs-lookup"><span data-stu-id="c7c78-135">Describes how to create a data quality project.</span></span>|[<span data-ttu-id="c7c78-136">创建数据质量项目</span><span class="sxs-lookup"><span data-stu-id="c7c78-136">Create a Data Quality Project</span></span>](../../2014/data-quality-services/create-a-data-quality-project.md)|  
|<span data-ttu-id="c7c78-137">描述如何管理（打开、解锁、重命名和删除）数据质量项目。</span><span class="sxs-lookup"><span data-stu-id="c7c78-137">Describes how to manage (open, unlock, rename, and delete) a data quality project.</span></span>|[<span data-ttu-id="c7c78-138">管理数据质量项目&#41; &#40;打开、解锁、重命名和删除</span><span class="sxs-lookup"><span data-stu-id="c7c78-138">Manage &#40;Open, Unlock, Rename, and Delete&#41; a Data Quality Project</span></span>](../../2014/data-quality-services/manage-open-unlock-rename-and-delete-a-data-quality-project.md)|  
|<span data-ttu-id="c7c78-139">描述如何在 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]中打开 Integration Services 项目。</span><span class="sxs-lookup"><span data-stu-id="c7c78-139">Describes how to open an Integration Services project in [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)].</span></span>|[<span data-ttu-id="c7c78-140">在数据质量客户端中打开 Integration Services 项目</span><span class="sxs-lookup"><span data-stu-id="c7c78-140">Open Integration Services Projects in Data Quality Client</span></span>](../../2014/data-quality-services/open-integration-services-projects-in-data-quality-client.md)|  
  
## <a name="see-also"></a><span data-ttu-id="c7c78-141">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c7c78-141">See Also</span></span>  
 [<span data-ttu-id="c7c78-142">DQS 知识库和域</span><span class="sxs-lookup"><span data-stu-id="c7c78-142">DQS Knowledge Bases and Domains</span></span>](../../2014/data-quality-services/dqs-knowledge-bases-and-domains.md)  
  
  
