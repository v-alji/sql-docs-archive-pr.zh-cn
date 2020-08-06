---
title: 打开知识库 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql12.dqs.kb.openkb.f1
ms.assetid: a5f010a5-b762-41c9-881b-bf0c192dca83
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: f727a5ab75a60d29c830403892c56c87fc6d4ebf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691874"
---
# <a name="open-a-knowledge-base"></a><span data-ttu-id="6f3a1-102">打开知识库</span><span class="sxs-lookup"><span data-stu-id="6f3a1-102">Open a Knowledge Base</span></span>
  <span data-ttu-id="6f3a1-103">本主题描述如何在 [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) 中打开现有的知识库，以及如何准备知识库以用于域管理、知识发现或添加匹配策略。</span><span class="sxs-lookup"><span data-stu-id="6f3a1-103">This topic describes how to open an existing knowledge base in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS), and prepare it for domain management, knowledge discovery, or adding a matching policy.</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="6f3a1-104">开始之前</span><span class="sxs-lookup"><span data-stu-id="6f3a1-104">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a><span data-ttu-id="6f3a1-105">先决条件</span><span class="sxs-lookup"><span data-stu-id="6f3a1-105">Prerequisites</span></span>  
 <span data-ttu-id="6f3a1-106">若要打开知识库，该知识库必须已创建，并且已发布（如果另一个人创建了此知识库）或已关闭（如果您创建了该知识库）。</span><span class="sxs-lookup"><span data-stu-id="6f3a1-106">To open a knowledge base, the knowledge base must have already been created, and either published (if another person created it) or have been closed (if you created it).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="6f3a1-107">Security</span><span class="sxs-lookup"><span data-stu-id="6f3a1-107">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="6f3a1-108">权限</span><span class="sxs-lookup"><span data-stu-id="6f3a1-108">Permissions</span></span>  
 <span data-ttu-id="6f3a1-109">您必须对 DQS_MAIN 数据库具有 dqs_kb_editor 或 dqs_administrator 角色，才能打开知识库。</span><span class="sxs-lookup"><span data-stu-id="6f3a1-109">You must have the dqs_kb_editor role or the dqs_administrator on the DQS_MAIN database to open a knowledge base.</span></span>  
  
##  <a name="open-a-knowledge-base"></a><a name="Open"></a><span data-ttu-id="6f3a1-110">打开知识库</span><span class="sxs-lookup"><span data-stu-id="6f3a1-110">Open a knowledge base</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="6f3a1-111">[运行 Data Quality Client 应用程序](../../2014/data-quality-services/run-the-data-quality-client-application.md)。</span><span class="sxs-lookup"><span data-stu-id="6f3a1-111">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="6f3a1-112">在 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 主屏幕中，单击 **“打开知识库”**。</span><span class="sxs-lookup"><span data-stu-id="6f3a1-112">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, click **Open knowledge base**.</span></span>  
  
3.  <span data-ttu-id="6f3a1-113">在表中选择知识库。</span><span class="sxs-lookup"><span data-stu-id="6f3a1-113">Select a knowledge base in the table.</span></span> <span data-ttu-id="6f3a1-114">将在该页的右侧窗格中显示知识库中的域和匹配规则。</span><span class="sxs-lookup"><span data-stu-id="6f3a1-114">The domains and matching rules in the knowledge base will be displayed in the right-hand pane of the page.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6f3a1-115">可以通过在表中右键单击知识库对其执行操作。</span><span class="sxs-lookup"><span data-stu-id="6f3a1-115">You can perform operations on a knowledge base by right-clicking it in the table.</span></span> <span data-ttu-id="6f3a1-116">您可以打开知识库、用其他名称保存它、对其解除锁定、放弃操作、重命名或显示其属性。</span><span class="sxs-lookup"><span data-stu-id="6f3a1-116">You can open the knowledge base, save it with another name, unlock it, discard the work, rename it, or display its properties.</span></span>  
  
4.  <span data-ttu-id="6f3a1-117">在 **“选择活动”** 中，选择要对知识库执行的活动：</span><span class="sxs-lookup"><span data-stu-id="6f3a1-117">In **Select Activity**, select the activity that you want to perform on the knowledge base:</span></span>  
  
    -   <span data-ttu-id="6f3a1-118">选择 **“域管理”** 可进入您用来修改知识库中的域的屏幕。</span><span class="sxs-lookup"><span data-stu-id="6f3a1-118">Select **Domain Management** to enter the screens that you use to modify the domains in the knowledge base.</span></span>  
  
    -   <span data-ttu-id="6f3a1-119">选择 **“知识发现”** 可以进入一个向导，您可以使用该向导分析数据样本并用分析结果填充知识库的各个域。</span><span class="sxs-lookup"><span data-stu-id="6f3a1-119">Select **Knowledge Discovery** to enter the wizard that you use to analyze a data sample and populate the domains of the knowledge base with the results.</span></span>  
  
    -   <span data-ttu-id="6f3a1-120">选择 **“匹配策略”** 可以创建匹配策略，并将其添加到知识库。</span><span class="sxs-lookup"><span data-stu-id="6f3a1-120">Select **Matching Policy** to create a matching policy and add it to the knowledge base.</span></span>  
  
5.  <span data-ttu-id="6f3a1-121">单击 **“打开”** 。</span><span class="sxs-lookup"><span data-stu-id="6f3a1-121">Click **Open**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6f3a1-122">还可以通过右键单击知识库，然后单击“打开”来打开该知识库。</span><span class="sxs-lookup"><span data-stu-id="6f3a1-122">You can also open the knowledge base by right-clicking it, and then clicking Open.</span></span> <span data-ttu-id="6f3a1-123">上下文菜单中的其他命令支持用其他名称保存它、对其解除锁定、放弃操作、重命名或显示其属性。</span><span class="sxs-lookup"><span data-stu-id="6f3a1-123">Other commands in the context menu enable you to save it with another name, unlock it, discard the work, rename it, or display its properties.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6f3a1-124">如果您因为该知识库已锁定而无法打开，则请参阅下一节。</span><span class="sxs-lookup"><span data-stu-id="6f3a1-124">If you cannot open the knowledge base because it is locked, see the section below.</span></span>  
  
## <a name="open-a-recent-knowledge-base"></a><span data-ttu-id="6f3a1-125">打开最近的知识库</span><span class="sxs-lookup"><span data-stu-id="6f3a1-125">Open a Recent Knowledge Base</span></span>  
 <span data-ttu-id="6f3a1-126">将在 DQS 主页的 **“最近的知识库”** 列表中显示 5 个最近打开的知识库。</span><span class="sxs-lookup"><span data-stu-id="6f3a1-126">The five most recently opened knowledge bases are displayed in the **Recent Knowledge Base** list in the DQS home page.</span></span> <span data-ttu-id="6f3a1-127">这使您可以打开最近使用的知识库，而无需通过 **“打开知识库”** 页面。</span><span class="sxs-lookup"><span data-stu-id="6f3a1-127">This enables you to open a knowledge base that you recently worked on without going through the **Open Knowledge Base** page.</span></span>  
  
-   <span data-ttu-id="6f3a1-128">若要打开“最近”列表中没有锁定的知识库，请单击该知识库的右箭头，然后选择要在其中打开该知识库的活动。</span><span class="sxs-lookup"><span data-stu-id="6f3a1-128">To open a knowledge base in the Recent list that is not locked, click the right arrow for the knowledge base, and then select the activity that you want to open the knowledge base in.</span></span>  
  
-   <span data-ttu-id="6f3a1-129">若要打开“最近”列表中已锁定的知识库，请单击该知识库，此时将在括号中标明的活动和页面中打开该知识库。</span><span class="sxs-lookup"><span data-stu-id="6f3a1-129">To open a knowledge base in the Recent list that you locked, click the knowledge base and it will open in the activity and page indicated in parentheses.</span></span>  
  
-   <span data-ttu-id="6f3a1-130">若要打开“最近”列表中已被其他成员锁定的知识库，请联系相关人员，让他们解除对该知识库的锁定。</span><span class="sxs-lookup"><span data-stu-id="6f3a1-130">To open a knowledge base in the Recent list that has been locked by someone else, contact that person and have them unlock the knowledge base.</span></span>  
  
##  <a name="follow-up-after-opening-a-knowledge-base"></a><a name="FollowUp"></a><span data-ttu-id="6f3a1-131">跟进：打开知识库后</span><span class="sxs-lookup"><span data-stu-id="6f3a1-131">Follow Up: After Opening a Knowledge Base</span></span>  
 <span data-ttu-id="6f3a1-132">打开知识库之后，该知识库将进入在“知识库”表的“状态”列中指示的状态。</span><span class="sxs-lookup"><span data-stu-id="6f3a1-132">After you open a knowledge base, the knowledge base is put into the state indicated in the State column of the Knowledge Base table.</span></span> <span data-ttu-id="6f3a1-133">对于知识发现和匹配策略活动，将在特定向导页中打开该知识库。</span><span class="sxs-lookup"><span data-stu-id="6f3a1-133">For the knowledge discovery and matching policy activities, the knowledge base will be opened in a specific wizard page.</span></span> <span data-ttu-id="6f3a1-134">对于域管理活动，将在域管理页面中打开知识库。</span><span class="sxs-lookup"><span data-stu-id="6f3a1-134">For the domain management activity, the knowledge base will be opened in the domain management page.</span></span> <span data-ttu-id="6f3a1-135">有关状态的详细信息，请参阅[执行知识发现](../../2014/data-quality-services/perform-knowledge-discovery.md)、[管理域](../../2014/data-quality-services/managing-a-domain.md)或[创建匹配策略](../../2014/data-quality-services/create-a-matching-policy.md)。</span><span class="sxs-lookup"><span data-stu-id="6f3a1-135">For more information about the states, see [Perform Knowledge Discovery](../../2014/data-quality-services/perform-knowledge-discovery.md), [Managing a Domain](../../2014/data-quality-services/managing-a-domain.md), or [Create a Matching Policy](../../2014/data-quality-services/create-a-matching-policy.md).</span></span>  
  
##  <a name="if-the-knowledge-base-is-locked"></a><a name="Locked"></a><span data-ttu-id="6f3a1-136">如果知识库已锁定</span><span class="sxs-lookup"><span data-stu-id="6f3a1-136">If the knowledge base is locked</span></span>  
 <span data-ttu-id="6f3a1-137">第一列中的锁图标显示是否已锁定知识库。</span><span class="sxs-lookup"><span data-stu-id="6f3a1-137">The lock icon in the first column shows whether the knowledge base is locked.</span></span> <span data-ttu-id="6f3a1-138">锁定的知识库名称将以红色字体显示。</span><span class="sxs-lookup"><span data-stu-id="6f3a1-138">The name of a locked knowledge base will be in red font.</span></span> <span data-ttu-id="6f3a1-139">特定用户正在通过知识库活动修改的知识库将标记为锁定。</span><span class="sxs-lookup"><span data-stu-id="6f3a1-139">A knowledge base that is being modified by a specific user through a knowledge base activity is marked as Locked.</span></span> <span data-ttu-id="6f3a1-140">任何其他用户都不能对锁定的知识库执行操作。</span><span class="sxs-lookup"><span data-stu-id="6f3a1-140">A locked knowledge base cannot be worked on by a second user.</span></span> <span data-ttu-id="6f3a1-141">对知识库执行操作的用户可以在“打开知识库”页上通过右键单击表中的知识库，然后单击 **“解锁”**，或通过发布该知识库，对其解除锁定。</span><span class="sxs-lookup"><span data-stu-id="6f3a1-141">The user who is working on the knowledge base can unlock it by right-clicking the knowledge base in the table on the Open Knowledge Base page, and clicking **Unlock**, or by publishing it.</span></span> <span data-ttu-id="6f3a1-142">当游标位于锁定的知识库上时，DQS 将显示提示，以显示锁定该知识库的人员以及何时锁定了此知识库。</span><span class="sxs-lookup"><span data-stu-id="6f3a1-142">When the cursor is positioned on a locked knowledge base, DQS will display a hint showing who locked the knowledge base and when they locked it.</span></span>  
  
##  <a name="state-of-a-knowledge-base"></a><a name="State"></a><span data-ttu-id="6f3a1-143">知识库的状态</span><span class="sxs-lookup"><span data-stu-id="6f3a1-143">State of a Knowledge Base</span></span>  
 <span data-ttu-id="6f3a1-144">“状态”字段指示知识库处于活动的哪个阶段。</span><span class="sxs-lookup"><span data-stu-id="6f3a1-144">The State field indicates which stage of an activity the knowledge base is at.</span></span> <span data-ttu-id="6f3a1-145">如果您打开知识库，则打开此知识库的该阶段。</span><span class="sxs-lookup"><span data-stu-id="6f3a1-145">If you open the knowledge base, it will open to that stage.</span></span>  
  
-   <span data-ttu-id="6f3a1-146">**\<Empty>**：如果已通过在 "域管理" 活动中单击 "**发布**" 发布知识库，并单击 **"是-发布知识库并退出**"，则知识库的 "状态" 字段为空。</span><span class="sxs-lookup"><span data-stu-id="6f3a1-146">**\<Empty>**: The State field is empty for a knowledge base if the knowledge base has been published by clicking **Publish** in the Domain Management activity, and clicking **Yes - Publish the knowledge base and exit**.</span></span>  
  
-   <span data-ttu-id="6f3a1-147">**工作中**：通过在域管理活动中单击 "**发布**"，然后单击 "**否" 保存对知识库所做的工作并退出**。</span><span class="sxs-lookup"><span data-stu-id="6f3a1-147">**In Work**: Work on the knowledge base has been saved by clicking **Publish** in the Domain Management activity, and clicking **No - Save the work on the knowledge base and exit**.</span></span>  
  
-   <span data-ttu-id="6f3a1-148">**域管理**：已为知识库中的域输入数据，但尚未发布该知识库，工作仍保留在域管理活动中。</span><span class="sxs-lookup"><span data-stu-id="6f3a1-148">**Domain Management**: Data has been entered for a domain in the knowledge base, but the knowledge base has not been published and the work remains in the Domain Management activity.</span></span> <span data-ttu-id="6f3a1-149">知识发现活动不可用。</span><span class="sxs-lookup"><span data-stu-id="6f3a1-149">The Knowledge Discovery activity is not available.</span></span> <span data-ttu-id="6f3a1-150">在 **“域管理”** 屏幕中单击 **“关闭”** 后出现此状态。</span><span class="sxs-lookup"><span data-stu-id="6f3a1-150">This occurs when you click **Close** in the **Domain Management** screen.</span></span>  
  
-   <span data-ttu-id="6f3a1-151">**发现 - 映射**：在 **“知识库管理: 映射”** 页上关闭了知识库。</span><span class="sxs-lookup"><span data-stu-id="6f3a1-151">**Discovery - Mapping**: The knowledge base was closed on the **Knowledge Base Management: Mapping** page.</span></span> <span data-ttu-id="6f3a1-152">该知识库已锁定，且域管理活动和匹配活动不可用。</span><span class="sxs-lookup"><span data-stu-id="6f3a1-152">The knowledge base is locked, and the Domain Management and Matching activities are not available.</span></span>  
  
-   <span data-ttu-id="6f3a1-153">**发现 - 发现**：在 **“知识库管理: 分析”** 页上关闭了知识库。</span><span class="sxs-lookup"><span data-stu-id="6f3a1-153">**Discovery - Discover**: The knowledge base was closed on the **Knowledge Base Management: Analyze** page.</span></span> <span data-ttu-id="6f3a1-154">知识库已锁定，且域管理活动不可用。</span><span class="sxs-lookup"><span data-stu-id="6f3a1-154">The knowledge base is locked, and The Domain Management activity is not available.</span></span>  
  
-   <span data-ttu-id="6f3a1-155">**发现-值管理**：在 "**知识库管理：管理域字词**" 页上关闭了知识库。</span><span class="sxs-lookup"><span data-stu-id="6f3a1-155">**Discovery - Value Management**: The knowledge base was closed on the **Knowledge Base Management: Manage Domain Terms** page.</span></span> <span data-ttu-id="6f3a1-156">知识库已锁定，且域管理活动不可用。</span><span class="sxs-lookup"><span data-stu-id="6f3a1-156">The knowledge base is locked, and the Domain Management activity is not available.</span></span>  
  
-   <span data-ttu-id="6f3a1-157">**匹配策略-匹配策略**：在 "**匹配策略-匹配策略**" 页上关闭了知识库。</span><span class="sxs-lookup"><span data-stu-id="6f3a1-157">**Matching Policy - Matching Policy**: The knowledge base was closed on the **Matching Policy - Matching Policy** page.</span></span> <span data-ttu-id="6f3a1-158">该知识库已锁定，且知识发现和域管理活动不可用。</span><span class="sxs-lookup"><span data-stu-id="6f3a1-158">The knowledge base is locked, and the Knowledge Discovery and Domain Management activities are not available.</span></span>  
  
-   <span data-ttu-id="6f3a1-159">**匹配策略-匹配结果**：在 "**匹配策略-匹配结果**" 页上关闭了知识库。</span><span class="sxs-lookup"><span data-stu-id="6f3a1-159">**Matching Policy - Matching Results**: The knowledge base was closed on the **Matching Policy - Matching Results** page.</span></span> <span data-ttu-id="6f3a1-160">该知识库已锁定，且知识发现和域管理活动不可用。</span><span class="sxs-lookup"><span data-stu-id="6f3a1-160">The knowledge base is locked, and the Knowledge Discovery and Domain Management activities are not available.</span></span>  
  
  
