---
title: 创建数据质量项目 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql12.dqs.dqproject.newdqproject.f1
helpviewer_keywords:
- create,data quality project
- data quality project,create
ms.assetid: 19c52d2b-d28e-4449-ab59-5fe0dc326cd9
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 3bab14b34123464450bcf0de7540364fc642343e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87683063"
---
# <a name="create-a-data-quality-project"></a><span data-ttu-id="1d973-102">创建数据质量项目</span><span class="sxs-lookup"><span data-stu-id="1d973-102">Create a Data Quality Project</span></span>
  <span data-ttu-id="1d973-103">本主题介绍如何使用 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]创建数据质量项目。</span><span class="sxs-lookup"><span data-stu-id="1d973-103">This topic describes how to create a data quality project by using [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)].</span></span> <span data-ttu-id="1d973-104">数据质量项目用于在 [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) 中运行清理或匹配活动。</span><span class="sxs-lookup"><span data-stu-id="1d973-104">A data quality project is used to run the cleansing or matching activity in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS).</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="1d973-105">开始之前</span><span class="sxs-lookup"><span data-stu-id="1d973-105">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a><span data-ttu-id="1d973-106">先决条件</span><span class="sxs-lookup"><span data-stu-id="1d973-106">Prerequisites</span></span>  
 <span data-ttu-id="1d973-107">对于清理或匹配活动，您必须具有要在数据质量项目中使用的相关知识库。</span><span class="sxs-lookup"><span data-stu-id="1d973-107">You must have a relevant knowledge base to use in the data quality project for the cleansing or matching activity.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="1d973-108">Security</span><span class="sxs-lookup"><span data-stu-id="1d973-108">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="1d973-109">权限</span><span class="sxs-lookup"><span data-stu-id="1d973-109">Permissions</span></span>  
 <span data-ttu-id="1d973-110">您必须对 DQS_MAIN 数据库具有 dqs_kb_editor 或 dqs_kb_operator 角色才能创建数据质量项目。</span><span class="sxs-lookup"><span data-stu-id="1d973-110">You must have the dqs_kb_editor or dqs_kb_operator role on the DQS_MAIN database to create a data quality project.</span></span>  
  
##  <a name="create-a-data-quality-project"></a><a name="Create"></a><span data-ttu-id="1d973-111">创建数据质量项目</span><span class="sxs-lookup"><span data-stu-id="1d973-111">Create a Data Quality Project</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="1d973-112">[运行 Data Quality Client 应用程序](../../2014/data-quality-services/run-the-data-quality-client-application.md)。</span><span class="sxs-lookup"><span data-stu-id="1d973-112">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="1d973-113">在 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 主屏幕中，单击 **“新建数据质量项目”**。</span><span class="sxs-lookup"><span data-stu-id="1d973-113">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, click **New data quality project**.</span></span>  
  
3.  <span data-ttu-id="1d973-114">在 **“新建数据质量项目”** 屏幕中：</span><span class="sxs-lookup"><span data-stu-id="1d973-114">In the **New Data Quality Project** screen:</span></span>  
  
    1.  <span data-ttu-id="1d973-115">在 **“名称”** 框中，键入新的数据质量项目的名称。</span><span class="sxs-lookup"><span data-stu-id="1d973-115">In the **Name** box, type a name for the new data quality project.</span></span>  
  
    2.  <span data-ttu-id="1d973-116">还可以在 **“说明”** 框中键入新的数据质量项目的说明。</span><span class="sxs-lookup"><span data-stu-id="1d973-116">(Optional) In the **Description** box, type a description for the new data quality project.</span></span>  
  
    3.  <span data-ttu-id="1d973-117">在 **“使用知识库”** 列表中，单击以便选择要用于数据质量项目的知识库</span><span class="sxs-lookup"><span data-stu-id="1d973-117">In the **Use Knowledge base** list, click to select a knowledge base to be used for the data quality project.</span></span> <span data-ttu-id="1d973-118">右侧的“知识库详细信息: <Knowledge_Base_Name>”区域将显示所选知识库中提供的域名\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1d973-118">The **Knowledge base details: <Knowledge_Base_Name>** area on the right side displays the domain names available in the selected knowledge base.</span></span>  
  
    4.  <span data-ttu-id="1d973-119">在 **“选择活动”** 区域中，单击您要使用此数据质量项目执行的活动：</span><span class="sxs-lookup"><span data-stu-id="1d973-119">In the **Select Activity** area, click on an activity that you want to perform using this data quality project:</span></span>  
  
        -   <span data-ttu-id="1d973-120">**清理**：选择此活动将清理源数据。</span><span class="sxs-lookup"><span data-stu-id="1d973-120">**Cleansing**: Select this activity to cleanse the source data.</span></span>  
  
        -   <span data-ttu-id="1d973-121">**匹配**：选择此活动将执行匹配。</span><span class="sxs-lookup"><span data-stu-id="1d973-121">**Matching**: Select this activity to perform matching.</span></span> <span data-ttu-id="1d973-122">只有在为数据质量项目选择的知识库包含匹配策略的情况下，此活动才可用。</span><span class="sxs-lookup"><span data-stu-id="1d973-122">This activity is available only if the knowledge base selected for the data quality project contains a matching policy.</span></span>  
  
4.  <span data-ttu-id="1d973-123">单击 **“创建”** 将创建数据质量项目。</span><span class="sxs-lookup"><span data-stu-id="1d973-123">Click **Create** to create a data quality project.</span></span>  
  
##  <a name="follow-up-after-creating-a-data-quality-project"></a><a name="FollowUp"></a><span data-ttu-id="1d973-124">跟进：在创建数据质量项目后</span><span class="sxs-lookup"><span data-stu-id="1d973-124">Follow Up: After Creating a Data Quality Project</span></span>  
 <span data-ttu-id="1d973-125">在创建数据质量项目后，将向您提供一个向导，可用于执行所选活动：清理或匹配。</span><span class="sxs-lookup"><span data-stu-id="1d973-125">After you create a data quality project, you are presented with a wizard that you use to perform the selected activity: cleansing or matching.</span></span> <span data-ttu-id="1d973-126">有关清理和匹配活动的详细信息，请参阅[数据清理](../../2014/data-quality-services/data-cleansing.md)和[数据匹配](../../2014/data-quality-services/data-matching.md)。</span><span class="sxs-lookup"><span data-stu-id="1d973-126">For more information about the cleansing and matching activities, see [Data Cleansing](../../2014/data-quality-services/data-cleansing.md) and [Data Matching](../../2014/data-quality-services/data-matching.md).</span></span>  
  
  
