---
title: 管理数据质量项目)  (打开、解锁、重命名和删除 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql12.dqs.dqproject.opendqproject.f1
helpviewer_keywords:
- data quality project,delete
- data quality project,rename
- data quality project,unlock
- data quality project,open
ms.assetid: de8a2b04-4673-4beb-b4cf-96a28cdf3a93
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 216c95937676954c509890b879abdee8f55b778c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590372"
---
# <a name="manage-open-unlock-rename-and-delete-a-data-quality-project"></a><span data-ttu-id="8b7de-102">管理（打开、解锁、重命名和删除）数据质量项目</span><span class="sxs-lookup"><span data-stu-id="8b7de-102">Manage (Open, Unlock, Rename, and Delete) a Data Quality Project</span></span>
  <span data-ttu-id="8b7de-103">本主题介绍如何使用 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 管理数据质量项目，如打开、解锁、重命名和删除数据质量项目。</span><span class="sxs-lookup"><span data-stu-id="8b7de-103">This topic describes how to manage a data quality project by using [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] such as open, unlock, rename, and delete a data quality project.</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="8b7de-104">开始之前</span><span class="sxs-lookup"><span data-stu-id="8b7de-104">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> <span data-ttu-id="8b7de-105">限制和局限</span><span class="sxs-lookup"><span data-stu-id="8b7de-105">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="8b7de-106">您不能打开其他用户创建的锁定项目。</span><span class="sxs-lookup"><span data-stu-id="8b7de-106">You cannot open a locked project that is created by another user.</span></span>  
  
-   <span data-ttu-id="8b7de-107">您不能解锁、重命名或删除其他用户创建的数据质量项目。</span><span class="sxs-lookup"><span data-stu-id="8b7de-107">You cannot unlock, rename, or delete a data quality project that is created by another user.</span></span>  
  
-   <span data-ttu-id="8b7de-108">您不能删除锁定的数据质量项目。</span><span class="sxs-lookup"><span data-stu-id="8b7de-108">You cannot delete a locked data quality project.</span></span> <span data-ttu-id="8b7de-109">您必须先对其解锁后才能删除。</span><span class="sxs-lookup"><span data-stu-id="8b7de-109">You must first unlock it to delete.</span></span>  
  
-   <span data-ttu-id="8b7de-110">您只能解锁您创建的数据质量项目。</span><span class="sxs-lookup"><span data-stu-id="8b7de-110">You can only unlock a data quality project that is created by you.</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a><span data-ttu-id="8b7de-111">先决条件</span><span class="sxs-lookup"><span data-stu-id="8b7de-111">Prerequisites</span></span>  
 <span data-ttu-id="8b7de-112">您必须至少具有一个数据质量项目才能进行管理。</span><span class="sxs-lookup"><span data-stu-id="8b7de-112">You must have at least one data quality project to manage.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="8b7de-113">Security</span><span class="sxs-lookup"><span data-stu-id="8b7de-113">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="8b7de-114">权限</span><span class="sxs-lookup"><span data-stu-id="8b7de-114">Permissions</span></span>  
 <span data-ttu-id="8b7de-115">您必须对 DQS_MAIN 数据库具有 dqs_kb_editor 或 dqs_kb_operator 角色才能管理数据质量项目。</span><span class="sxs-lookup"><span data-stu-id="8b7de-115">You must have the dqs_kb_editor or dqs_kb_operator role on the DQS_MAIN database to manage a data quality project.</span></span>  
  
##  <a name="open-a-data-quality-project"></a><a name="Open"></a> <span data-ttu-id="8b7de-116">打开数据质量项目</span><span class="sxs-lookup"><span data-stu-id="8b7de-116">Open a Data Quality Project</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="8b7de-117">[运行 Data Quality Client 应用程序](../../2014/data-quality-services/run-the-data-quality-client-application.md)。</span><span class="sxs-lookup"><span data-stu-id="8b7de-117">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="8b7de-118">在 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 主屏幕中，单击 **“打开数据质量项目”**。</span><span class="sxs-lookup"><span data-stu-id="8b7de-118">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, click **Open data quality project**.</span></span> <span data-ttu-id="8b7de-119">将出现 **“打开项目”** 屏幕。</span><span class="sxs-lookup"><span data-stu-id="8b7de-119">The **Open project** screen appears.</span></span>  
  
     <span data-ttu-id="8b7de-120">或者，可以通过单击 **“最近的数据质量项目”** 区域下列出的数据质量项目来打开。</span><span class="sxs-lookup"><span data-stu-id="8b7de-120">Alternately, you can directly open a data quality project listed under **Recent data quality project** area by clicking it.</span></span>  
  
3.  <span data-ttu-id="8b7de-121">在 **“打开项目”** 屏幕中，单击以选择要打开的数据质量项目，然后单击 **“打开”**。</span><span class="sxs-lookup"><span data-stu-id="8b7de-121">In the **Open project** screen, click to select the data quality project that you want to open, and click **Next**.</span></span>  
  
4.  <span data-ttu-id="8b7de-122">数据质量项目打开时的状态就是上次在其中关闭该项目的活动的状态。</span><span class="sxs-lookup"><span data-stu-id="8b7de-122">The data quality project opens at the same state of the activity where it was last closed.</span></span> <span data-ttu-id="8b7de-123">数据质量项目具有以下状态：</span><span class="sxs-lookup"><span data-stu-id="8b7de-123">A data quality project has the following states:</span></span>  
  
    -   <span data-ttu-id="8b7de-124">对于 "**清理**" 活动，数据质量项目可具有以下状态： "**清理**"、"**清理-** 清理"、"**清理-管理和查看结果**" 和 "**清理导出**"。</span><span class="sxs-lookup"><span data-stu-id="8b7de-124">For the **Cleansing** activity, a data quality project can have the following states: **Cleansing - Map**, **Cleansing - Cleanse**, **Cleansing - Manage and View Results**, and **Cleansing - Export**.</span></span>  
  
    -   <span data-ttu-id="8b7de-125">对于“匹配”活动，数据质量项目可具有以下状态：“匹配 - 映射”、“匹配 - 匹配”、“匹配 - 存活”和“匹配 - 导出”\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8b7de-125">For the **Matching** activity, a data quality project can have the following states: **Matching - Map**, **Matching - Matching**, **Matching - Survivorship**, and **Matching - Export**.</span></span>  
  
##  <a name="unlock-a-data-quality-project"></a><a name="Unlock"></a> <span data-ttu-id="8b7de-126">解锁数据质量项目</span><span class="sxs-lookup"><span data-stu-id="8b7de-126">Unlock a Data Quality Project</span></span>  
 <span data-ttu-id="8b7de-127">数据质量项目在创建时处于锁定状态，以防其他用户使用或修改。</span><span class="sxs-lookup"><span data-stu-id="8b7de-127">When you create a data quality project, it is in a locked state to prevent usage or modification by other users.</span></span> <span data-ttu-id="8b7de-128">在完成操作后，如果您希望其他用户使用您的数据质量项目，则必须对该数据质量项目解锁。</span><span class="sxs-lookup"><span data-stu-id="8b7de-128">You must unlock the data quality project after you have completed your work if you want other users to work on your data quality project.</span></span> <span data-ttu-id="8b7de-129">锁定的项目将显示一个锁符号。</span><span class="sxs-lookup"><span data-stu-id="8b7de-129">A lock symbol is displayed for projects that are locked.</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="8b7de-130">[运行 Data Quality Client 应用程序](../../2014/data-quality-services/run-the-data-quality-client-application.md)。</span><span class="sxs-lookup"><span data-stu-id="8b7de-130">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="8b7de-131">在 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 主屏幕中，单击 **“打开数据质量项目”**。</span><span class="sxs-lookup"><span data-stu-id="8b7de-131">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, click **Open data quality project**.</span></span> <span data-ttu-id="8b7de-132">将出现 **“打开项目”** 屏幕。</span><span class="sxs-lookup"><span data-stu-id="8b7de-132">The **Open project** screen appears.</span></span>  
  
3.  <span data-ttu-id="8b7de-133">在 **“打开项目”** 屏幕中，右键单击您创建的锁定数据质量项目，再单击快捷菜单中的 **“解锁”** 。</span><span class="sxs-lookup"><span data-stu-id="8b7de-133">In the **Open project** screen, right-click a locked data quality project that is created by you, and then click **Unlock** in the shortcut menu.</span></span> <span data-ttu-id="8b7de-134">系统将为此项目显示一个绿色对钩标记，指示项目未锁定。</span><span class="sxs-lookup"><span data-stu-id="8b7de-134">A green check mark is displayed for the project indicating that it is unlocked.</span></span>  
  
##  <a name="rename-a-data-quality-project"></a><a name="Rename"></a> <span data-ttu-id="8b7de-135">重命名数据质量项目</span><span class="sxs-lookup"><span data-stu-id="8b7de-135">Rename a Data Quality Project</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="8b7de-136">[运行 Data Quality Client 应用程序](../../2014/data-quality-services/run-the-data-quality-client-application.md)。</span><span class="sxs-lookup"><span data-stu-id="8b7de-136">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="8b7de-137">在 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 主屏幕中，单击 **“打开数据质量项目”**。</span><span class="sxs-lookup"><span data-stu-id="8b7de-137">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, click **Open data quality project**.</span></span> <span data-ttu-id="8b7de-138">将出现 **“打开项目”** 屏幕。</span><span class="sxs-lookup"><span data-stu-id="8b7de-138">The **Open project** screen appears.</span></span>  
  
3.  <span data-ttu-id="8b7de-139">在 **“打开项目”** 屏幕中，右键单击您创建的数据质量项目，再单击快捷菜单中的 **“重命名”** 。</span><span class="sxs-lookup"><span data-stu-id="8b7de-139">In the **Open project** screen, right-click a data quality project that is created by you, and then click **Rename** in the shortcut menu.</span></span>  
  
4.  <span data-ttu-id="8b7de-140">在 **“名称”** 列中，数据质量项目名称将变为可编辑的。</span><span class="sxs-lookup"><span data-stu-id="8b7de-140">The data quality project name becomes editable in the **Name** column.</span></span> <span data-ttu-id="8b7de-141">键入新名称，然后按 Enter。</span><span class="sxs-lookup"><span data-stu-id="8b7de-141">Type a new name, and then press Enter.</span></span>  
  
##  <a name="delete-a-data-quality-project"></a><a name="Delete"></a> <span data-ttu-id="8b7de-142">删除数据质量项目</span><span class="sxs-lookup"><span data-stu-id="8b7de-142">Delete a Data Quality Project</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="8b7de-143">[运行 Data Quality Client 应用程序](../../2014/data-quality-services/run-the-data-quality-client-application.md)。</span><span class="sxs-lookup"><span data-stu-id="8b7de-143">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="8b7de-144">在 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 主屏幕中，单击 **“打开数据质量项目”**。</span><span class="sxs-lookup"><span data-stu-id="8b7de-144">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, click **Open data quality project**.</span></span> <span data-ttu-id="8b7de-145">将出现 **“打开项目”** 屏幕。</span><span class="sxs-lookup"><span data-stu-id="8b7de-145">The **Open project** screen appears.</span></span>  
  
3.  <span data-ttu-id="8b7de-146">在 **“打开项目”** 屏幕中，右键单击您创建的未锁定的数据质量项目，再单击快捷菜单中的 **“删除”** 。</span><span class="sxs-lookup"><span data-stu-id="8b7de-146">In the **Open project** screen, right-click an unlocked data quality project that is created by you, and then click **Delete** in the shortcut menu.</span></span>  
  
4.  <span data-ttu-id="8b7de-147">此时会显示确认消息。</span><span class="sxs-lookup"><span data-stu-id="8b7de-147">A confirmation message appears.</span></span> <span data-ttu-id="8b7de-148">单击 **“是”** 。</span><span class="sxs-lookup"><span data-stu-id="8b7de-148">Click **Yes**.</span></span>  
  
  
