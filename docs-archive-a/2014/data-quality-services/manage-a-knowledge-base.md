---
title: 管理知识库 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 27f306f4-d67c-47f5-b35c-4260cc5d36e3
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: cc5fdd87ddb3ea687db10a29d7001564fd8ff107
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590385"
---
# <a name="manage-a-knowledge-base"></a><span data-ttu-id="91101-102">管理知识库</span><span class="sxs-lookup"><span data-stu-id="91101-102">Manage a Knowledge Base</span></span>
  <span data-ttu-id="91101-103">本主题介绍如何在 [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) 中对知识库执行管理功能。</span><span class="sxs-lookup"><span data-stu-id="91101-103">This topic describes how to perform management functions on a knowledge base in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS).</span></span> <span data-ttu-id="91101-104">您可以删除知识库、对知识库进行解锁、放弃对知识库所做的工作、重命名知识库以及显示其属性。</span><span class="sxs-lookup"><span data-stu-id="91101-104">You can delete a knowledge base, unlock it, discard your work on it, rename it, and display its properties.</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="91101-105">开始之前</span><span class="sxs-lookup"><span data-stu-id="91101-105">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a><span data-ttu-id="91101-106">先决条件</span><span class="sxs-lookup"><span data-stu-id="91101-106">Prerequisites</span></span>  
 <span data-ttu-id="91101-107">若要管理知识库，该知识库必须已创建，并且已发布（如果另一个人创建了此知识库）或已关闭（如果您创建了该知识库）。</span><span class="sxs-lookup"><span data-stu-id="91101-107">To manage a knowledge base, the knowledge base must have already been created, and either published (if another person created it) or have been closed (if you created it).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="91101-108">Security</span><span class="sxs-lookup"><span data-stu-id="91101-108">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="91101-109">权限</span><span class="sxs-lookup"><span data-stu-id="91101-109">Permissions</span></span>  
 <span data-ttu-id="91101-110">您必须对 DQS_MAIN 数据库具有 dqs_kb_editor 或 dqs_administrator 角色，才能打开知识库。</span><span class="sxs-lookup"><span data-stu-id="91101-110">You must have the dqs_kb_editor role or the dqs_administrator on the DQS_MAIN database to open a knowledge base.</span></span>  
  
##  <a name="manage-a-knowledge-base"></a><a name="Manage"></a><span data-ttu-id="91101-111">管理知识库</span><span class="sxs-lookup"><span data-stu-id="91101-111">Manage a Knowledge Base</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="91101-112">[运行 Data Quality Client 应用程序](../../2014/data-quality-services/run-the-data-quality-client-application.md)。</span><span class="sxs-lookup"><span data-stu-id="91101-112">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="91101-113">在 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 主屏幕中，单击 **“打开知识库”**。</span><span class="sxs-lookup"><span data-stu-id="91101-113">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, click **Open knowledge base**.</span></span>  
  
3.  <span data-ttu-id="91101-114">在知识库表中右键单击某一知识库。</span><span class="sxs-lookup"><span data-stu-id="91101-114">Right-click a knowledge base in the knowledge base table.</span></span>  
  
4.  <span data-ttu-id="91101-115">在上下文菜单中，您可以执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="91101-115">In the context menu, you can do the following:</span></span>  
  
    1.  <span data-ttu-id="91101-116">**打开**：单击以便在 **“选择活动”** 窗格中选择的活动中打开该知识库。</span><span class="sxs-lookup"><span data-stu-id="91101-116">**Open**: Click to open the knowledge base in the activity selected in the **Select Activity** pane.</span></span>  
  
    2.  <span data-ttu-id="91101-117">**取消锁定**：如果您是在域管理、知识发现和匹配策略活动的某一步骤中正在使用该知识库的用户，并且关闭了该知识库，则可以取消锁定该知识库。</span><span class="sxs-lookup"><span data-stu-id="91101-117">**Unlock**: You can unlock the knowledge base if you are the user who was working on the knowledge base in one of the steps of domain management, knowledge discovery, and the matching policy activity, and closed it.</span></span> <span data-ttu-id="91101-118">如果您卸载了该知识库，则其他人士将能够打开并使用该知识库。</span><span class="sxs-lookup"><span data-stu-id="91101-118">If you unload the knowledge base, another person will be able to open it and work on it.</span></span> <span data-ttu-id="91101-119">如果知识库未处于某一活动状态中，则此命令将不可用。</span><span class="sxs-lookup"><span data-stu-id="91101-119">This command is not available if the knowledge base is not in a state of an activity.</span></span> <span data-ttu-id="91101-120">有关详细信息，请参阅 [Open a Knowledge Base](../../2014/data-quality-services/open-a-knowledge-base.md)。</span><span class="sxs-lookup"><span data-stu-id="91101-120">For more information, see [Open a Knowledge Base](../../2014/data-quality-services/open-a-knowledge-base.md).</span></span>  
  
    3.  <span data-ttu-id="91101-121">**放弃工作**：在知识库处于正被使用状态时单击，如表的“状态”字段中的条目所示。</span><span class="sxs-lookup"><span data-stu-id="91101-121">**Discard work**: Click when the knowledge base is in a state of being worked on, as shown with an entry in the State field in the table.</span></span> <span data-ttu-id="91101-122">如果知识库未处于某一活动状态中，则此命令将不可用；并且在知识库被锁定时不可用。</span><span class="sxs-lookup"><span data-stu-id="91101-122">This command is not available if the knowledge base is not in a state of an activity, and it is not available if the knowledge base is locked.</span></span> <span data-ttu-id="91101-123">有关详细信息，请参阅 [Open a Knowledge Base](../../2014/data-quality-services/open-a-knowledge-base.md)。</span><span class="sxs-lookup"><span data-stu-id="91101-123">For more information, see [Open a Knowledge Base](../../2014/data-quality-services/open-a-knowledge-base.md).</span></span>  
  
    4.  <span data-ttu-id="91101-124">**重命名**：单击可使表的“知识库”字段对于您右键单击的知识库而言可编辑。</span><span class="sxs-lookup"><span data-stu-id="91101-124">**Rename**: Click to make the Knowledge Base field of the table editable for the knowledge base that you right-clicked on.</span></span> <span data-ttu-id="91101-125">更改名称，然后单击该知识库和字段中的其他知识库，以便接受名称更改。</span><span class="sxs-lookup"><span data-stu-id="91101-125">Change the name, and then click on that knowledge base and another one in the field to accept the name change.</span></span>  
  
    5.  <span data-ttu-id="91101-126">**删除**：单击可从 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)]上的 DQS_MAIN 数据库中删除该知识库。</span><span class="sxs-lookup"><span data-stu-id="91101-126">**Delete**: Click to remove the knowledge base from the DQS_MAIN database on [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)].</span></span>  
  
    6.  <span data-ttu-id="91101-127">**属性**：单击可显示数据库的属性，这些属性是只读的。</span><span class="sxs-lookup"><span data-stu-id="91101-127">**Properties**: Click to display properties for the database in a read-only display.</span></span>  
  
        1.  <span data-ttu-id="91101-128">**源知识库**：此数据库所基于的知识库。</span><span class="sxs-lookup"><span data-stu-id="91101-128">**Source Knowledge Base**: the knowledge base that this database was based on.</span></span> <span data-ttu-id="91101-129">这是可选项。</span><span class="sxs-lookup"><span data-stu-id="91101-129">This is optional.</span></span>  
  
        2.  <span data-ttu-id="91101-130">**状态**：指示知识库是否为 **“工作中”** 状态，以及知识库是否处于特定的知识管理活动中，这由其在上次关闭时的状态确定。</span><span class="sxs-lookup"><span data-stu-id="91101-130">**State**: Indicates if the knowledge base is **In Work** and if it is in a specific knowledge management activity, as determined when it was last closed.</span></span> <span data-ttu-id="91101-131">该状态可以是 **“工作中”**，在此情况下，知识库在某一知识管理会话中打开，但未处于特定的活动中；也可以是 **“工作中”** 加上知识管理活动，在此情况下，知识库在某一知识管理会话中打开，并且处于特定的活动中。</span><span class="sxs-lookup"><span data-stu-id="91101-131">The state can be **In Work**, in which the knowledge base is opened in a knowledge management session, but not in a specific activity, or **In Work** plus a knowledge management activity, in which the knowledge base is opened in a knowledge management session, and in a specific activity.</span></span>  
  
        3.  <span data-ttu-id="91101-132">**已锁定**：如果知识库已锁定，则为 **True** ；否则为 **False** 。</span><span class="sxs-lookup"><span data-stu-id="91101-132">**Is Locked**: **True** if the knowledge base was locked, **False** if not</span></span>  
  
        4.  <span data-ttu-id="91101-133">**包含未发布的内容**：如果知识库包含尚未通过发布保存的内容，则为 True；否则为 False。</span><span class="sxs-lookup"><span data-stu-id="91101-133">**Contains unpublished content**: True if the knowledge base contains content that has not been saved by publishing, False if not</span></span>  
  
        5.  <span data-ttu-id="91101-134">**锁定方**：关闭了知识库并且锁定它的用户的名称。</span><span class="sxs-lookup"><span data-stu-id="91101-134">**Locked By**: the name of the user who closed the knowledge base, locking it</span></span>  
  
        6.  <span data-ttu-id="91101-135">**锁定日期**：锁定时的日期。</span><span class="sxs-lookup"><span data-stu-id="91101-135">**Locked Date**: date when locked</span></span>  
  
        7.  <span data-ttu-id="91101-136">**创建者**：通过其属于的网络创建了知识库的用户的名称。</span><span class="sxs-lookup"><span data-stu-id="91101-136">**Created By**: the name of the user who created the knowledge base, with the network that he or she belongs to</span></span>  
  
        8.  <span data-ttu-id="91101-137">**创建日期**：创建时的日期</span><span class="sxs-lookup"><span data-stu-id="91101-137">**Created Date**: date when created</span></span>  
  
##  <a name="follow-up-after-managing-a-knowledge-base"></a><a name="FollowUp"></a> <span data-ttu-id="91101-138">跟进：管理知识库后</span><span class="sxs-lookup"><span data-stu-id="91101-138">Follow Up: After Managing a Knowledge Base</span></span>  
 <span data-ttu-id="91101-139">在管理某一知识库后，您的后续步骤取决于您对该知识库执行的操作：</span><span class="sxs-lookup"><span data-stu-id="91101-139">After you manage a knowledge base, your next step depends upon the action you took on the knowledge base:</span></span>  
  
-   <span data-ttu-id="91101-140">如果您打开了该知识库，将继续所选择的活动。</span><span class="sxs-lookup"><span data-stu-id="91101-140">If you opened the knowledge base, you will continue in the activity that you selected.</span></span>  
  
-   <span data-ttu-id="91101-141">如果您取消锁定该知识库，则其他人可以根据指示的状态打开和使用该知识库。</span><span class="sxs-lookup"><span data-stu-id="91101-141">If you unlocked it, it will be available for another person to open and work on, in the state indicated.</span></span>  
  
-   <span data-ttu-id="91101-142">如果您放弃对其执行的工作，则该知识库将处于上次发布的状态。</span><span class="sxs-lookup"><span data-stu-id="91101-142">If you discarded the work on it, the knowledge base will be available in its last published state.</span></span>  
  
-   <span data-ttu-id="91101-143">如果重命名了该知识库，将需要打开重命名的知识库才能使用它。</span><span class="sxs-lookup"><span data-stu-id="91101-143">If you renamed it, you will have to open the renamed knowledge base to work on it.</span></span>  
  
-   <span data-ttu-id="91101-144">如果您删除该知识库，将需要选择另一个知识库以便使用，或者创建一个新的知识库。</span><span class="sxs-lookup"><span data-stu-id="91101-144">If you delete it, you will have to select another knowledge base to work on, or create a new one.</span></span>  
  
  
