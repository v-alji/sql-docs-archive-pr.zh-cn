---
title: 创建知识库 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql12.dqs.kb.selectkb.f1
- sql12.dqs.kb.newkb.f1
ms.assetid: 2733a284-975f-4650-abcc-cc2aad074cab
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 281fa663362cc4462cd4e32839c1eaf6908394e0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578460"
---
# <a name="create-a-knowledge-base"></a><span data-ttu-id="4a44f-102">创建知识库</span><span class="sxs-lookup"><span data-stu-id="4a44f-102">Create a Knowledge Base</span></span>
  <span data-ttu-id="4a44f-103">本主题描述如何在 [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) 中创建知识库，以及如何准备知识库以用于域管理、知识发现或添加匹配策略。</span><span class="sxs-lookup"><span data-stu-id="4a44f-103">This topic describes how to create a knowledge base in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS), and prepare it for domain management, knowledge discovery, or adding a matching policy.</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="4a44f-104">开始之前</span><span class="sxs-lookup"><span data-stu-id="4a44f-104">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a><span data-ttu-id="4a44f-105">先决条件</span><span class="sxs-lookup"><span data-stu-id="4a44f-105">Prerequisites</span></span>  
 <span data-ttu-id="4a44f-106">要创建知识库，您必须安装有 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] 和 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4a44f-106">To create a knowledge base, you must have installed [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] and [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)].</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="4a44f-107">Security</span><span class="sxs-lookup"><span data-stu-id="4a44f-107">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="4a44f-108">权限</span><span class="sxs-lookup"><span data-stu-id="4a44f-108">Permissions</span></span>  
 <span data-ttu-id="4a44f-109">您必须对 DQS_MAIN 数据库具有 dqs_kb_editor 或 dqs_administrator 角色，才能创建知识库。</span><span class="sxs-lookup"><span data-stu-id="4a44f-109">You must have the dqs_kb_editor or the dqs_administrator role on the DQS_MAIN database to create a knowledge base.</span></span>  
  
##  <a name="create-a-knowledge-base"></a><a name="Createaknowledgebase"></a><span data-ttu-id="4a44f-110">创建知识库</span><span class="sxs-lookup"><span data-stu-id="4a44f-110">Create a knowledge base</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="4a44f-111">[运行 Data Quality Client 应用程序](../../2014/data-quality-services/run-the-data-quality-client-application.md)。</span><span class="sxs-lookup"><span data-stu-id="4a44f-111">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="4a44f-112">在 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 主屏幕中，单击 **“新建知识库”**。</span><span class="sxs-lookup"><span data-stu-id="4a44f-112">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, click **New knowledge base**.</span></span>  
  
3.  <span data-ttu-id="4a44f-113">输入新知识库的名称和说明。</span><span class="sxs-lookup"><span data-stu-id="4a44f-113">Enter a name and description for the new knowledge base.</span></span>  
  
4.  <span data-ttu-id="4a44f-114">在 **“创建知识库自”** 中，选择要基于其创建知识库的内容：</span><span class="sxs-lookup"><span data-stu-id="4a44f-114">In **Create knowledge base from**, select what to base the knowledge base on:</span></span>  
  
    -   <span data-ttu-id="4a44f-115">如果您不想基于现有知识库或数据文件来创建新知识库，则选择 **“无”** 。</span><span class="sxs-lookup"><span data-stu-id="4a44f-115">Select **None** if you do not want to base the new knowledge base on an existing knowledge base or data file.</span></span>  
  
    -   <span data-ttu-id="4a44f-116">选择 **“现有知识库”** 可以基于已在 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)]上创建的知识库或默认知识库来创建新知识库。</span><span class="sxs-lookup"><span data-stu-id="4a44f-116">Select **Existing Knowledge Base** to base the new knowledge base on a knowledge base that has already been created on [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)], or on the default knowledge base.</span></span> <span data-ttu-id="4a44f-117">从 **“选择知识库”** 下拉列表中选择知识库，或者单击 **“浏览”** 以便显示 **“选择知识库”** 对话框，选择新知识库要基于的一个现有知识库，然后单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="4a44f-117">Select the knowledge base from the **Select Knowledge Base** drop-down list, or click **Browse** to display the **Select a Knowledge Base** dialog box, select an existing knowledge base to base the new knowledge base on, and then click **OK**.</span></span> <span data-ttu-id="4a44f-118">在您从 Tablet 中选择一个知识库时，将在该对话框的右侧窗格中显示知识库中的域和匹配规则。</span><span class="sxs-lookup"><span data-stu-id="4a44f-118">When you select a knowledge base from the tablet, the domains and matching rules in the knowledge base will be displayed in the right-hand pane of the dialog box.</span></span> <span data-ttu-id="4a44f-119">你还可以选择“DQS 数据” \*\*\*\* 知识库，这是默认的知识库，包含与美国公司、地址和有关方数据相关的通用全新域和知识。</span><span class="sxs-lookup"><span data-stu-id="4a44f-119">You can also select the **DQS Data** knowledge base, which is the default knowledge base that contains common out-of-the-box domains and knowledge related to U.S. company, address, and party data.</span></span>  
  
    -   <span data-ttu-id="4a44f-120">选择 **“自 DQS 文件导入”** 将基于 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)]上的 DQS 文件创建新的知识库。</span><span class="sxs-lookup"><span data-stu-id="4a44f-120">Select **Import from DQS File** to base the new knowledge base on a DQS file on [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)].</span></span> <span data-ttu-id="4a44f-121">单击 **“浏览”**，选择扩展名为 .dqs 的 DQS 数据文件，然后单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="4a44f-121">Click **Browse**, select a DQS data file with an extension of .dqs, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="4a44f-122">在 **“选择活动”** 中，选择要对新知识库执行的活动：</span><span class="sxs-lookup"><span data-stu-id="4a44f-122">In **Select Activity**, select the activity that you want to perform on the new knowledge base:</span></span>  
  
    -   <span data-ttu-id="4a44f-123">选择 **“域管理”** 可创建知识库并进入您用来修改知识库中的域的屏幕。</span><span class="sxs-lookup"><span data-stu-id="4a44f-123">Select **Domain Management** to create the knowledge base and enter the screens that you use to modify the domains in the knowledge base.</span></span>  
  
    -   <span data-ttu-id="4a44f-124">选择 **“知识发现”** 可创建知识库并进入一个向导，您可以使用该向导分析数据样本并用分析结果填充知识库的各个域。</span><span class="sxs-lookup"><span data-stu-id="4a44f-124">Select **Knowledge Discovery** to create the knowledge base and enter the wizard that you use to analyze a data sample and populate the domains of the knowledge base with the results.</span></span>  
  
    -   <span data-ttu-id="4a44f-125">选择 **“匹配策略”** 可以创建匹配策略，并将其添加到知识库。</span><span class="sxs-lookup"><span data-stu-id="4a44f-125">Select **Matching Policy** to create a matching policy and add it to the knowledge base.</span></span>  
  
6.  <span data-ttu-id="4a44f-126">单击“创建”。</span><span class="sxs-lookup"><span data-stu-id="4a44f-126">Click **Create**.</span></span>  
  
##  <a name="follow-up-after-creating-a-knowledge-base"></a><a name="FollowUp"></a><span data-ttu-id="4a44f-127">跟进：在创建知识库后</span><span class="sxs-lookup"><span data-stu-id="4a44f-127">Follow Up: After Creating a Knowledge Base</span></span>  
 <span data-ttu-id="4a44f-128">在创建一个知识库后，系统将会向您提供可用于执行知识发现的向导、可用于创建匹配策略的向导或者可用于执行域管理的若干页。</span><span class="sxs-lookup"><span data-stu-id="4a44f-128">After you create a knowledge base, you are presented with a wizard that you can use to perform knowledge discovery, a wizard to create a matching policy, or pages to perform domain management.</span></span> <span data-ttu-id="4a44f-129">有关知识发现、域管理或匹配策略的详细信息，请参阅[执行知识发现](../../2014/data-quality-services/perform-knowledge-discovery.md)[管理域](../../2014/data-quality-services/managing-a-domain.md)或[创建匹配策略](../../2014/data-quality-services/create-a-matching-policy.md)。</span><span class="sxs-lookup"><span data-stu-id="4a44f-129">For more information about the knowledge discovery, domain management, or matching policy, see [Perform Knowledge Discovery](../../2014/data-quality-services/perform-knowledge-discovery.md), [Managing a Domain](../../2014/data-quality-services/managing-a-domain.md), or [Create a Matching Policy](../../2014/data-quality-services/create-a-matching-policy.md).</span></span>  
  
  
