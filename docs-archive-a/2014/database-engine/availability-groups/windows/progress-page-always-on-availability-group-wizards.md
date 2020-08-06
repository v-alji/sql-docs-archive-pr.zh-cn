---
title: " (AlwaysOn 可用性组向导) 的进度页 |Microsoft Docs"
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.addreplicawizard.progress.f1
- sql12.swb.newagwizard.progress.f1
- sql11.swb.failoverwizard.progress.f1
- sql11.swb.adddatabasewizard.progress.f1
- sql11.swb.addreplicawizard.progress.f1
- sql11.swb.newagwizard.progress.f1
- sql12.swb.adddatabasewizard.progress.f1
- sql12.swb.failoverwixard.progress.f1
ms.assetid: bd3b0306-8384-4120-a1c9-03825f0ae26a
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 7de8df6906d930215d71a0adc562bd7cef961ebb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693110"
---
# <a name="progress-page-alwayson-availability-group-wizards"></a><span data-ttu-id="9924c-102">“进度”页（AlwaysOn 可用性组向导）</span><span class="sxs-lookup"><span data-stu-id="9924c-102">Progress Page (AlwaysOn Availability Group Wizards)</span></span>
  <span data-ttu-id="9924c-103">使用此对话框可以查看您在 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 中运行的 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]向导的进度。</span><span class="sxs-lookup"><span data-stu-id="9924c-103">Use this dialog box to view the progress of a [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] wizard that you are running in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="9924c-104">进度栏指示该向导正在执行的步骤的相对进度。</span><span class="sxs-lookup"><span data-stu-id="9924c-104">The progress bar indicates the relative progress of the steps that the wizard is performing.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="9924c-105">UI 元素列表</span><span class="sxs-lookup"><span data-stu-id="9924c-105">UI element list</span></span>  
 <span data-ttu-id="9924c-106">**更多详细信息**</span><span class="sxs-lookup"><span data-stu-id="9924c-106">**More details**</span></span>  
 <span data-ttu-id="9924c-107">单击下箭头可显示进度网格，其中按顺序列出所有已完成的步骤，后面跟有当前正在进行的操作。</span><span class="sxs-lookup"><span data-stu-id="9924c-107">Click the down arrow to display a progress grid that lists any completed steps, in order, followed by the current in-progress operation.</span></span> <span data-ttu-id="9924c-108">该网格包含以下列：</span><span class="sxs-lookup"><span data-stu-id="9924c-108">The grid contains the following columns:</span></span>  
  
 <span data-ttu-id="9924c-109">**名称**</span><span class="sxs-lookup"><span data-stu-id="9924c-109">**Name**</span></span>  
 <span data-ttu-id="9924c-110">显示描述特定步骤的短语。</span><span class="sxs-lookup"><span data-stu-id="9924c-110">Displays a phrase that describes a specific step.</span></span>  
  
 <span data-ttu-id="9924c-111">**Status**</span><span class="sxs-lookup"><span data-stu-id="9924c-111">**Status**</span></span>  
 <span data-ttu-id="9924c-112">指示已完成步骤的结果，以及当前步骤的完成百分比，如下所示：</span><span class="sxs-lookup"><span data-stu-id="9924c-112">Indicates the outcome of completed steps and the percentage of completion of the current step, as follows:</span></span>  
  
|<span data-ttu-id="9924c-113">结果</span><span class="sxs-lookup"><span data-stu-id="9924c-113">Result</span></span>|<span data-ttu-id="9924c-114">说明</span><span class="sxs-lookup"><span data-stu-id="9924c-114">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="9924c-115">**错误**</span><span class="sxs-lookup"><span data-stu-id="9924c-115">**Error**</span></span>|<span data-ttu-id="9924c-116">指示此步骤操作遇到了错误。</span><span class="sxs-lookup"><span data-stu-id="9924c-116">Indicates the operation for this step experienced an error.</span></span> <span data-ttu-id="9924c-117">单击该链接可显示一个描述该错误的消息对话框。</span><span class="sxs-lookup"><span data-stu-id="9924c-117">Click the link to display a message dialog box that describes the error.</span></span>|  
|<span data-ttu-id="9924c-118">正在进行（完成百分比）</span><span class="sxs-lookup"><span data-stu-id="9924c-118">**In Progress (** *percentage-completed* **)**</span></span>|<span data-ttu-id="9924c-119">指示操作正在发生，并且估计此步骤已完成的百分比。</span><span class="sxs-lookup"><span data-stu-id="9924c-119">Indicates that the operation is occurring now and estimates the percentage of this step that has completed.</span></span>|  
|<span data-ttu-id="9924c-120">**Success**</span><span class="sxs-lookup"><span data-stu-id="9924c-120">**Success**</span></span>|<span data-ttu-id="9924c-121">指示此步骤操作已成功完成。</span><span class="sxs-lookup"><span data-stu-id="9924c-121">Indicates the operation for this step completed successfully.</span></span>|  
  
 <span data-ttu-id="9924c-122">**更少详细信息**</span><span class="sxs-lookup"><span data-stu-id="9924c-122">**Fewer Details**</span></span>  
 <span data-ttu-id="9924c-123">单击此选项可隐藏进度网格。</span><span class="sxs-lookup"><span data-stu-id="9924c-123">Click to hide the progress grid.</span></span>  
  
 <span data-ttu-id="9924c-124">**取消**</span><span class="sxs-lookup"><span data-stu-id="9924c-124">**Cancel**</span></span>  
 <span data-ttu-id="9924c-125">单击此选项可跳过剩下的所有操作，然后退出该向导。</span><span class="sxs-lookup"><span data-stu-id="9924c-125">Click to skip any remaining operations and then exit the wizard.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="9924c-126">相关任务</span><span class="sxs-lookup"><span data-stu-id="9924c-126">Related Tasks</span></span>  
  
-   [<span data-ttu-id="9924c-127">使用“新建可用性组”对话框 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="9924c-127">Use the New Availability Group Dialog Box &#40;SQL Server Management Studio&#41;</span></span>](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="9924c-128">使用“将副本添加到可用性组向导”(SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="9924c-128">Use the Add Replica to Availability Group Wizard &#40;SQL Server Management Studio&#41;</span></span>](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="9924c-129">使用“将数据库添加到可用性组向导”(SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="9924c-129">Use the Add Database to Availability Group Wizard &#40;SQL Server Management Studio&#41;</span></span>](availability-group-add-database-to-group-wizard.md)  
  
-   [<span data-ttu-id="9924c-130">使用故障转移可用性组向导 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="9924c-130">Use the Fail Over Availability Group Wizard &#40;SQL Server Management Studio&#41;</span></span>](use-the-fail-over-availability-group-wizard-sql-server-management-studio.md)  
  
## <a name="see-also"></a><span data-ttu-id="9924c-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9924c-131">See Also</span></span>  
 [<span data-ttu-id="9924c-132">AlwaysOn 可用性组 &#40;SQL Server 概述&#41;</span><span class="sxs-lookup"><span data-stu-id="9924c-132">Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](overview-of-always-on-availability-groups-sql-server.md)  
  
  
