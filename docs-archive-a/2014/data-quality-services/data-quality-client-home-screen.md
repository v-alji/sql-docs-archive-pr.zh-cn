---
title: Data Quality Client 主屏幕 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql12.dqs.clienthome.f1
ms.assetid: 7c6ec469-bc7d-4d19-8e21-11dcf8ade108
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 68257048530389d2e4ef78d11e47aa9b27f022b1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579062"
---
# <a name="data-quality-client-home-screen"></a><span data-ttu-id="310f3-102">数据质量客户端主屏幕</span><span class="sxs-lookup"><span data-stu-id="310f3-102">Data Quality Client Home Screen</span></span>
  <span data-ttu-id="310f3-103">使用此屏幕可以访问 [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) 的三组主要任务的用户界面：知识库管理、数据质量项目和管理。</span><span class="sxs-lookup"><span data-stu-id="310f3-103">Use this screen to gain access to the user interfaces for each the three major [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) groups of tasks: knowledge base management, data quality projects, and administration.</span></span>  
  
## <a name="options"></a><span data-ttu-id="310f3-104">选项</span><span class="sxs-lookup"><span data-stu-id="310f3-104">Options</span></span>  
  
### <a name="knowledge-base-management"></a><span data-ttu-id="310f3-105">知识库管理</span><span class="sxs-lookup"><span data-stu-id="310f3-105">Knowledge Base Management</span></span>  
 <span data-ttu-id="310f3-106">DQS 知识库是 DQS 用来提高数据质量的元数据储存库。</span><span class="sxs-lookup"><span data-stu-id="310f3-106">A DQS knowledge base is a repository of metadata that is used by DQS to improve the quality of data.</span></span> <span data-ttu-id="310f3-107">该元数据在两个过程中创建：在计算机辅助的知识发现过程中由 DQS 平台创建，以及在交互式的域管理过程中由数据专员创建。</span><span class="sxs-lookup"><span data-stu-id="310f3-107">This metadata is created both by the DQS platform in a computer-assisted knowledge discovery process and by the data steward in an interactive domain management process.</span></span>  
  
 <span data-ttu-id="310f3-108">**新建知识库**</span><span class="sxs-lookup"><span data-stu-id="310f3-108">**New Knowledge Base**</span></span>  
 <span data-ttu-id="310f3-109">启动知识库的创建过程，可以从头创建也可以基于现有知识库的元数据创建。</span><span class="sxs-lookup"><span data-stu-id="310f3-109">Start the process of creating a knowledge base either from scratch or based upon the metadata of an existing knowledge base.</span></span> <span data-ttu-id="310f3-110">此命令打开一个页面，您可以在其中标识知识库、使它基于现有知识库、选择所需知识库活动，然后创建知识库。</span><span class="sxs-lookup"><span data-stu-id="310f3-110">This command opens a page in which you can identify the knowledge base, base it on an existing knowledge base, select the desired knowledge base activity, and then create the knowledge base.</span></span>  
  
 <span data-ttu-id="310f3-111">**打开知识库**</span><span class="sxs-lookup"><span data-stu-id="310f3-111">**Open Knowledge Base**</span></span>  
 <span data-ttu-id="310f3-112">打开知识库，以便您可以管理域、执行知识发现或生成匹配策略。</span><span class="sxs-lookup"><span data-stu-id="310f3-112">Open a knowledge base so you can manage its domains, perform knowledge discovery, or build a matching policy.</span></span> <span data-ttu-id="310f3-113">单击 **“打开知识库”** 按钮将显示 **“打开知识库”** 页，其中显示现有知识库的列表，列出这些知识库的属性、当前状态、知识库及其域的详细信息。</span><span class="sxs-lookup"><span data-stu-id="310f3-113">Clicking the **Open Knowledge Base** button displays the **Open Knowledge Base** page that shows a list of existing knowledge bases with their properties, current state, knowledge base, and details of their domains.</span></span> <span data-ttu-id="310f3-114">从 **“打开知识库”** 页选择一个知识库并打开它。</span><span class="sxs-lookup"><span data-stu-id="310f3-114">Select a knowledge base and open it from the **Open Knowledge Base**.</span></span>  
  
 <span data-ttu-id="310f3-115">**最近的知识库**</span><span class="sxs-lookup"><span data-stu-id="310f3-115">**Recent Knowledge Base**</span></span>  
 <span data-ttu-id="310f3-116">从屏幕上的列表中，打开一个已创建的知识库。</span><span class="sxs-lookup"><span data-stu-id="310f3-116">From the list on the screen, open a knowledge base that has already been created.</span></span> <span data-ttu-id="310f3-117">如果未锁定，请单击向右箭头，然后选择要在（“域管理”、“知识发现”或“匹配策略”）中启动知识库的活动。</span><span class="sxs-lookup"><span data-stu-id="310f3-117">If not locked, click the right arrow and then select the activity that you want to start the knowledge base in (Domain Management, Knowledge Discovery, or Matching Policy).</span></span>  
  
 <span data-ttu-id="310f3-118">您可以打开锁定的知识库并仅在您锁定它的情况下进行编辑。</span><span class="sxs-lookup"><span data-stu-id="310f3-118">You can open a locked knowledge base and edit it only if you locked it.</span></span> <span data-ttu-id="310f3-119">如果这样，知识库将以它关闭时的状态打开，该状态在括号中标明。</span><span class="sxs-lookup"><span data-stu-id="310f3-119">If so, the knowledge base will be opened in the state that it was in when it was closed, which is indicated in parentheses.</span></span> <span data-ttu-id="310f3-120">如果知识库已锁定但是不是您锁定的，则只能以只读方式打开它。</span><span class="sxs-lookup"><span data-stu-id="310f3-120">If a knowledge base is locked, and you did not lock it, you can only open it as read-only.</span></span>  
  
### <a name="data-quality-projects"></a><span data-ttu-id="310f3-121">数据质量项目</span><span class="sxs-lookup"><span data-stu-id="310f3-121">Data Quality Projects</span></span>  
 <span data-ttu-id="310f3-122">数据质量项目是 DQS 同时通过计算机辅助数据更正和交互式数据清理来执行数据清理或数据匹配的过程。</span><span class="sxs-lookup"><span data-stu-id="310f3-122">A data quality project is the process in which DQS performs data cleansing or data matching, both through computer-assisted data correction and interactive data cleansing.</span></span>  
  
 <span data-ttu-id="310f3-123">**新建数据质量项目**</span><span class="sxs-lookup"><span data-stu-id="310f3-123">**New Data Quality Project**</span></span>  
 <span data-ttu-id="310f3-124">启动创建新项目的项目。</span><span class="sxs-lookup"><span data-stu-id="310f3-124">Start the project of creating a new project.</span></span> <span data-ttu-id="310f3-125">此命令打开一个页面，您可以在其中标识项目、将它与知识库关联、显示知识库的详细信息、选择所需项目活动，然后创建项目。</span><span class="sxs-lookup"><span data-stu-id="310f3-125">This command opens a page in which you can identify the project, associate it with a knowledge base, display details of the knowledge base, select the desired project activity, and then create the project.</span></span>  
  
 <span data-ttu-id="310f3-126">**打开数据质量项目**</span><span class="sxs-lookup"><span data-stu-id="310f3-126">**Open Data Quality Project**</span></span>  
 <span data-ttu-id="310f3-127">打开项目，以便您可以执行数据清理或数据匹配。</span><span class="sxs-lookup"><span data-stu-id="310f3-127">Open a project so you can perform data cleansing or data matching.</span></span> <span data-ttu-id="310f3-128">单击 **“打开数据质量项目”** 按钮将显示 **“打开数据质量项目”** 页，其中显示现有项目的列表，列出这些项目的属性、当前状态、知识库及其域和匹配策略规则的详细信息。</span><span class="sxs-lookup"><span data-stu-id="310f3-128">Clicking the **Open data quality project** button displays the **Open data quality project** page that shows a list of existing projects with their properties, current state, knowledge base, and details of their domains and matching policy rules.</span></span> <span data-ttu-id="310f3-129">从 **“打开数据质量项目”** 页选择一个项目，然后打开它。</span><span class="sxs-lookup"><span data-stu-id="310f3-129">Select a project and open it from the **Open data quality project**.</span></span>  
  
 <span data-ttu-id="310f3-130">**最近的数据质量项目**</span><span class="sxs-lookup"><span data-stu-id="310f3-130">**Recent data quality project**</span></span>  
 <span data-ttu-id="310f3-131">从屏幕上的列表中，选择一个已创建的项目。</span><span class="sxs-lookup"><span data-stu-id="310f3-131">From the list on the screen, select a project that has already been created.</span></span> <span data-ttu-id="310f3-132">仅当您锁定它时，才可以打开锁定的项目。</span><span class="sxs-lookup"><span data-stu-id="310f3-132">You can open a locked project only if you locked it.</span></span> <span data-ttu-id="310f3-133">如果这样，项目将以它关闭时的状态打开，该状态在括号中标明。</span><span class="sxs-lookup"><span data-stu-id="310f3-133">If so, the project will be opened in the state that it was in when it was closed, which is indicated in parentheses.</span></span> <span data-ttu-id="310f3-134">如果项目已完成，将在活动的“导出”步骤中打开它。</span><span class="sxs-lookup"><span data-stu-id="310f3-134">If the project was completed, it will be opened in the Export step of the activity.</span></span>  
  
### <a name="administration"></a><span data-ttu-id="310f3-135">管理</span><span class="sxs-lookup"><span data-stu-id="310f3-135">Administration</span></span>  
 <span data-ttu-id="310f3-136">通过 DQS 管理，您可以监视、配置和维护 DQS。</span><span class="sxs-lookup"><span data-stu-id="310f3-136">DQS administration enables you to monitor, configure, and maintain DQS.</span></span>  
  
 <span data-ttu-id="310f3-137">**活动监视**</span><span class="sxs-lookup"><span data-stu-id="310f3-137">**Activity Monitoring**</span></span>  
 <span data-ttu-id="310f3-138">显示与所连接的 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)]相关的所有活动（当前和历史活动）的状态的视图。</span><span class="sxs-lookup"><span data-stu-id="310f3-138">Display a view of the status of all activities (both current and historical) that are related to the connected [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)].</span></span> <span data-ttu-id="310f3-139">监视的活动类型包括知识管理、数据质量项目和基于 SSIS 的数据更正。</span><span class="sxs-lookup"><span data-stu-id="310f3-139">The types of activities monitored include Knowledge Management, Data Quality Project, and SSIS-based data correction.</span></span>  
  
 <span data-ttu-id="310f3-140">**配置**</span><span class="sxs-lookup"><span data-stu-id="310f3-140">**Configuration**</span></span>  
 <span data-ttu-id="310f3-141">显示引用数据服务帐户的配置属性，这些属性可通过 Azure Marketplace (，并直接用于引用数据服务) 、常规设置 (交互式清理、匹配和分析) 和日志严重性设置。</span><span class="sxs-lookup"><span data-stu-id="310f3-141">Display the configuration properties for reference data service accounts (both through Azure Marketplace and directly to reference data services), general settings (interactive cleansing, matching, and profiling) and log severity settings.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="310f3-142">另请参阅</span><span class="sxs-lookup"><span data-stu-id="310f3-142">See Also</span></span>  
 <span data-ttu-id="310f3-143">[DQS 知识库和域](../../2014/data-quality-services/dqs-knowledge-bases-and-domains.md) </span><span class="sxs-lookup"><span data-stu-id="310f3-143">[DQS Knowledge Bases and Domains](../../2014/data-quality-services/dqs-knowledge-bases-and-domains.md) </span></span>  
 <span data-ttu-id="310f3-144">[&#40;DQS&#41;的数据质量项目](../../2014/data-quality-services/data-quality-projects-dqs.md) </span><span class="sxs-lookup"><span data-stu-id="310f3-144">[Data Quality Projects &#40;DQS&#41;](../../2014/data-quality-services/data-quality-projects-dqs.md) </span></span>  
 [<span data-ttu-id="310f3-145">dqs 管理</span><span class="sxs-lookup"><span data-stu-id="310f3-145">DQS Administration</span></span>](../../2014/data-quality-services/dqs-administration.md)  
  
  
