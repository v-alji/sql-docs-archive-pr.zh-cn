---
title: 在复合域中使用值关系 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql12.dqs.dm.cdvaluerelations.f1
ms.assetid: 5ee468f0-8538-4620-90e8-63f466c9000e
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 135934ec99fed612609e5e1b962f08bb93b98ede
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694131"
---
# <a name="use-value-relations-in-a-composite-domain"></a><span data-ttu-id="7320d-102">在复合域中使用值关系</span><span class="sxs-lookup"><span data-stu-id="7320d-102">Use Value Relations in a Composite Domain</span></span>
  <span data-ttu-id="7320d-103">本主题介绍如何在 [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) 知识发现过程中查看为复合域找到的值组合。</span><span class="sxs-lookup"><span data-stu-id="7320d-103">This topic describes how to view value combinations found for the composite domain during the knowledge discovery process in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS).</span></span> <span data-ttu-id="7320d-104">此页显示值组合的出现次数。</span><span class="sxs-lookup"><span data-stu-id="7320d-104">This page shows the number of occurrences of the value combinations.</span></span> <span data-ttu-id="7320d-105">复合域不支持值管理，因此，您无法对这些值执行任何操作。</span><span class="sxs-lookup"><span data-stu-id="7320d-105">Value management is not supported for composite domains, so you cannot perform any operations on these values.</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="7320d-106">开始之前</span><span class="sxs-lookup"><span data-stu-id="7320d-106">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a><span data-ttu-id="7320d-107">先决条件</span><span class="sxs-lookup"><span data-stu-id="7320d-107">Prerequisites</span></span>  
 <span data-ttu-id="7320d-108">若要查看值关系，您必须创建并打开了一个复合域。</span><span class="sxs-lookup"><span data-stu-id="7320d-108">To view value relations, you must have created and opened a composite domain.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="7320d-109">Security</span><span class="sxs-lookup"><span data-stu-id="7320d-109">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="7320d-110">权限</span><span class="sxs-lookup"><span data-stu-id="7320d-110">Permissions</span></span>  
 <span data-ttu-id="7320d-111">您必须对 DQS_MAIN 数据库具有 dqs_kb_editor 或 dqs_administrator 角色，才能在复合域中查看值关系。</span><span class="sxs-lookup"><span data-stu-id="7320d-111">You must have the dqs_kb_editor or the dqs_administrator role on the DQS_MAIN database to view value relations in a composite domain.</span></span>  
  
##  <a name="view-value-relations"></a><a name="Use"></a><span data-ttu-id="7320d-112">查看值关系</span><span class="sxs-lookup"><span data-stu-id="7320d-112">View Value Relations</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="7320d-113">[运行 Data Quality Client 应用程序](../../2014/data-quality-services/run-the-data-quality-client-application.md)。</span><span class="sxs-lookup"><span data-stu-id="7320d-113">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="7320d-114">在 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 的主屏幕中，打开或创建一个知识库。</span><span class="sxs-lookup"><span data-stu-id="7320d-114">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, open or create a knowledge base.</span></span> <span data-ttu-id="7320d-115">选择 **“域管理”** 作为活动，然后单击 **“打开”** 或 **“创建”**。</span><span class="sxs-lookup"><span data-stu-id="7320d-115">Select **Domain Management** as the activity, and then click **Open** or **Create**.</span></span> <span data-ttu-id="7320d-116">有关详细信息，请参阅 [创建知识库](../../2014/data-quality-services/create-a-knowledge-base.md) 或 [打开知识库](../../2014/data-quality-services/open-a-knowledge-base.md)。</span><span class="sxs-lookup"><span data-stu-id="7320d-116">For more information, see [Create a Knowledge Base](../../2014/data-quality-services/create-a-knowledge-base.md) or [Open a Knowledge Base](../../2014/data-quality-services/open-a-knowledge-base.md).</span></span>  
  
3.  <span data-ttu-id="7320d-117">从 **“域管理”** 页上的 **“域列表”** 中，选择您要为其创建域规则的复合域，或者创建一个新的复合域。</span><span class="sxs-lookup"><span data-stu-id="7320d-117">From the **Domain list** on the **Domain Management** page, select the composite domain that you want to create a domain rule for, or create a new composite domain.</span></span> <span data-ttu-id="7320d-118">如果您必须创建新域，请参阅 [Create a Composite Domain](../../2014/data-quality-services/create-a-composite-domain.md)。</span><span class="sxs-lookup"><span data-stu-id="7320d-118">If you have to create a new domain, see [Create a Composite Domain](../../2014/data-quality-services/create-a-composite-domain.md).</span></span>  
  
4.  <span data-ttu-id="7320d-119">单击 **“查看关系”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="7320d-119">Click the **Value Relations** tab.</span></span>  
  
5.  <span data-ttu-id="7320d-120">查看为每个值组合显示的频率。</span><span class="sxs-lookup"><span data-stu-id="7320d-120">View the frequencies displayed for each value combination.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="7320d-121">**“值”** 表显示在复合域中存在的每个值组合。</span><span class="sxs-lookup"><span data-stu-id="7320d-121">The **Value** table shows each combination of values that exists in the composite domain.</span></span> <span data-ttu-id="7320d-122">每个值都显示在它应用于的单一域中。</span><span class="sxs-lookup"><span data-stu-id="7320d-122">Each value is shown in the single domain that it applies to.</span></span> <span data-ttu-id="7320d-123">值关系表的默认排序是按频率，但您可以单击其他列以便按该列排序。</span><span class="sxs-lookup"><span data-stu-id="7320d-123">The default sorting of the value relations table is by frequency, but you can click on another column to sort by that column.</span></span> <span data-ttu-id="7320d-124">仅显示其频率大于或等于 20 的那些值。</span><span class="sxs-lookup"><span data-stu-id="7320d-124">Only those values with a frequency greater than or equal to 20 are displayed.</span></span>  
  
6.  <span data-ttu-id="7320d-125">您不能更改该表中的任何值。</span><span class="sxs-lookup"><span data-stu-id="7320d-125">You cannot change any of the values in the table.</span></span> <span data-ttu-id="7320d-126">如果您已执行了其他操作，则单击 **“完成”** 可完成域管理活动。</span><span class="sxs-lookup"><span data-stu-id="7320d-126">If you have performed other operations, click **Finish** to complete the domain management activity.</span></span> <span data-ttu-id="7320d-127">否则，单击 "**取消**"。</span><span class="sxs-lookup"><span data-stu-id="7320d-127">Otherwise, click **Cancel**.</span></span>  
  
##  <a name="follow-up-after-viewing-value-relations"></a><a name="FollowUp"></a> <span data-ttu-id="7320d-128">跟进：在查看值关系后</span><span class="sxs-lookup"><span data-stu-id="7320d-128">Follow Up: After Viewing Value Relations</span></span>  
 <span data-ttu-id="7320d-129">在查看值关系后，您可以对域执行其他域管理任务，可以执行知识发现以便向域添加知识，或者可以向域添加匹配策略。</span><span class="sxs-lookup"><span data-stu-id="7320d-129">After you view value relations, you can perform other domain management tasks on the domain, you can perform knowledge discovery to add knowledge to the domain, or you can add a matching policy to the domain.</span></span> <span data-ttu-id="7320d-130">有关详细信息，请参阅[执行知识发现](../../2014/data-quality-services/perform-knowledge-discovery.md)、[管理域](../../2014/data-quality-services/managing-a-domain.md)或[创建匹配策略](../../2014/data-quality-services/create-a-matching-policy.md)。</span><span class="sxs-lookup"><span data-stu-id="7320d-130">For more information, see [Perform Knowledge Discovery](../../2014/data-quality-services/perform-knowledge-discovery.md), [Managing a Domain](../../2014/data-quality-services/managing-a-domain.md), or [Create a Matching Policy](../../2014/data-quality-services/create-a-matching-policy.md).</span></span>  
  
  
