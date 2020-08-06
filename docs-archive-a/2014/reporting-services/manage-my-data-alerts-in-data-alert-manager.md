---
title: 在数据警报管理器中管理我的数据警报 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- managing, alerts
- managing, data alerts
ms.assetid: e0e4ffdf-bd4c-4ebd-872b-07486cbb47c2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 371c62c2f97334e20280a659c8039ab20852ccfb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691636"
---
# <a name="manage-my-data-alerts-in-data-alert-manager"></a><span data-ttu-id="22938-102">在数据警报管理器中管理我的数据警报</span><span class="sxs-lookup"><span data-stu-id="22938-102">Manage My Data Alerts in Data Alert Manager</span></span>
  <span data-ttu-id="22938-103">SharePoint 用户可以查看他们所创建的数据警报列表以及与这些警报有关的信息。</span><span class="sxs-lookup"><span data-stu-id="22938-103">SharePoint users can view a list of the data alerts that they created and information about the alerts.</span></span> <span data-ttu-id="22938-104">用户还可以删除其警报，打开警报定义以便在数据警报设计器中进行编辑，以及运行其警报。</span><span class="sxs-lookup"><span data-stu-id="22938-104">Users can also delete their alerts, open alert definitions for edit in Data Alert Designer, and run their alerts.</span></span> <span data-ttu-id="22938-105">下图显示数据警报管理器中可用于用户的功能。</span><span class="sxs-lookup"><span data-stu-id="22938-105">The following picture shows the features available to users in Data Alert Manager.</span></span>  
  
 <span data-ttu-id="22938-106">![面向 SharePoint 用户的警报管理器功能](media/rs-alertmanageriw.gif "面向 SharePoint 用户的警报管理器功能")</span><span class="sxs-lookup"><span data-stu-id="22938-106">![Alert Manager features for SharePoint users](media/rs-alertmanageriw.gif "Alert Manager features for SharePoint users")</span></span>  
  
### <a name="to-view-a-list-of-your-alerts"></a><span data-ttu-id="22938-107">查看您的警报列表</span><span class="sxs-lookup"><span data-stu-id="22938-107">To view a list of your alerts</span></span>  
  
1.  <span data-ttu-id="22938-108">转至您在其中保存了您已创建数据警报的报表的 SharePoint 库。</span><span class="sxs-lookup"><span data-stu-id="22938-108">Go to the SharePoint library where you saved the reports on which you created data alerts.</span></span>  
  
2.  <span data-ttu-id="22938-109">单击针对报表展开下拉菜单的图标，然后单击“管理数据警报”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="22938-109">Click the icon for the expand drop-down menu on a report and click **Manage Data Alerts**.</span></span> <span data-ttu-id="22938-110">下图显示该下拉菜单。</span><span class="sxs-lookup"><span data-stu-id="22938-110">The following picture shows the drop-down menu.</span></span>  
  
     <span data-ttu-id="22938-111">![从报表上下文菜单打开警报管理器](media/rs-openalertmanager.gif "从报表上下文菜单打开警报管理器")</span><span class="sxs-lookup"><span data-stu-id="22938-111">![Open Alert Manager from report context menu](media/rs-openalertmanager.gif "Open Alert Manager from report context menu")</span></span>  
  
     <span data-ttu-id="22938-112">数据警报管理器随之打开。</span><span class="sxs-lookup"><span data-stu-id="22938-112">Data Alert Manager opens.</span></span> <span data-ttu-id="22938-113">默认情况下，它列出了针对您在库中选择的报表的警报。</span><span class="sxs-lookup"><span data-stu-id="22938-113">By default, it lists the alerts for the report that you selected in the library.</span></span>  
  
3.  <span data-ttu-id="22938-114">单击 **“查看报表警报”** 列表旁的向下箭头并且选择要查看其警报的报表，或者单击 **“全部显示”** 以列出所有警报。</span><span class="sxs-lookup"><span data-stu-id="22938-114">Click the down arrow next to the **View alerts for report** list and select a report to view its alerts, or click **Show All** to list all alerts.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="22938-115">如果所选报表没有任何警报，则不必返回 SharePoint 库来查找和选择具有警报的报表。</span><span class="sxs-lookup"><span data-stu-id="22938-115">If the report that you selected does not have any alerts, you do not have to return to the SharePoint library to locate and select a report that hasalerts.</span></span> <span data-ttu-id="22938-116">而是单击 **“全部显示”** 以查看所有警报的列表。</span><span class="sxs-lookup"><span data-stu-id="22938-116">Instead, click **Show All** to see a list of all your alerts.</span></span>  
  
     <span data-ttu-id="22938-117">一个表将列出警报名称、报表名称、警报创建者的姓名、发送警报的数目、上次修改警报定义的时间以及警报的状态。</span><span class="sxs-lookup"><span data-stu-id="22938-117">A table lists the alert name, report name, your name as the creator of the alert, the number the alert was sent, the last time the alert definition was modified, and the status of the alert.</span></span> <span data-ttu-id="22938-118">如果无法生成或发送警报，则状态列将包含有关该错误的信息并且帮助您纠正该问题。</span><span class="sxs-lookup"><span data-stu-id="22938-118">If the alert cannot be generated or sent, the status column contains information about the error and helps you troubleshoot the problem.</span></span>  
  
### <a name="to-edit-an-alert-definition"></a><span data-ttu-id="22938-119">编辑警报定义</span><span class="sxs-lookup"><span data-stu-id="22938-119">To edit an alert definition</span></span>  
  
-   <span data-ttu-id="22938-120">右键单击要编辑其警报定义的数据警报，然后单击“编辑”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="22938-120">Right-click the data alert for which you want to edit the alert definition and click **Edit**.</span></span>  
  
     <span data-ttu-id="22938-121">该警报定义将在数据警报设计器中打开。</span><span class="sxs-lookup"><span data-stu-id="22938-121">The alert definition opens in Data Alert Designer.</span></span> <span data-ttu-id="22938-122">有关详细信息，请参阅 [在警报设计器中编辑数据警报](edit-a-data-alert-in-alert-designer.md) 和 [数据警报设计器](../../2014/reporting-services/data-alert-designer.md)。</span><span class="sxs-lookup"><span data-stu-id="22938-122">For more information, see [Edit a Data Alert in Alert Designer](edit-a-data-alert-in-alert-designer.md) and [Data Alert Designer](../../2014/reporting-services/data-alert-designer.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="22938-123">只有创建了数据警报定义的用户才能对其进行编辑。</span><span class="sxs-lookup"><span data-stu-id="22938-123">Only the user that created the data alert definition can edit it.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="22938-124">如果报表已更改并且从该报表生成的数据馈送已更改，则警报定义将不再有效。</span><span class="sxs-lookup"><span data-stu-id="22938-124">If the report has changed and the data feeds generated from the report have changed the alert definition might no longer be valid.</span></span> <span data-ttu-id="22938-125">在发生以下情况之一时警报定义将不再有效：警报在其规则中引用的列从报表中删除、更改数据类型或包括在其他数据馈送中，或删除或移动了报表。</span><span class="sxs-lookup"><span data-stu-id="22938-125">This occurs when a column that the alert references in its rules is deleted from the report, changes data type, or is included in a different data feed or the report is deleted or moved.</span></span> <span data-ttu-id="22938-126">您可以打开无效的警报定义，但在其根据报表数据馈送所基于的当前版本变为有效之前无法重新保存。</span><span class="sxs-lookup"><span data-stu-id="22938-126">You can open an alert definition that is not valid, but you cannot resave it until it is valid based on the current version of the report data feed that it is built upon.</span></span> <span data-ttu-id="22938-127">若要深入了解如何从报表中生成数据馈送，请参阅[基于报表生成数据馈送（报表生成器和 SSRS）](report-builder/generating-data-feeds-from-reports-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="22938-127">To learn more about how data feeds are generated from reports, see [Generating Data Feeds from Reports &#40;Report Builder and SSRS&#41;](report-builder/generating-data-feeds-from-reports-report-builder-and-ssrs.md).</span></span>  
  
### <a name="to-delete-an-alert-definition"></a><span data-ttu-id="22938-128">删除警报定义</span><span class="sxs-lookup"><span data-stu-id="22938-128">To delete an alert definition</span></span>  
  
-   <span data-ttu-id="22938-129">右键单击要删除的数据警报，然后单击“删除”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="22938-129">Right-click the data alert that you want to delete and click **Delete**.</span></span>  
  
     <span data-ttu-id="22938-130">删除警报后，将不会发送进一步的警报消息。</span><span class="sxs-lookup"><span data-stu-id="22938-130">When you delete the alert, no further alert messages are sent.</span></span>  
  
### <a name="to-run-an-alert"></a><span data-ttu-id="22938-131">运行警报</span><span class="sxs-lookup"><span data-stu-id="22938-131">To run an alert</span></span>  
  
-   <span data-ttu-id="22938-132">右键单击要运行的数据警报，然后单击“运行”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="22938-132">Right-click the data alert that you want to run and click **Run**.</span></span>  
  
     <span data-ttu-id="22938-133">创建警报实例，并立即发送数据警报消息，而不考虑数据警报设计器中指定的计划选项。</span><span class="sxs-lookup"><span data-stu-id="22938-133">The alert instance is created and the data alert message is immediately sent, regardless of the schedule options you specified in Data Alert Designer.</span></span> <span data-ttu-id="22938-134">例如，配置为每周发送的警报，并且仅当结果更改时才发送。</span><span class="sxs-lookup"><span data-stu-id="22938-134">For example, an alert configured to be sent weekly and then only if the results change is sent.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22938-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="22938-135">See Also</span></span>  
 <span data-ttu-id="22938-136">[向管理员提出警报的数据警报管理器](../../2014/reporting-services/data-alert-manager-for-alerting-administrators.md) </span><span class="sxs-lookup"><span data-stu-id="22938-136">[Data Alert Manager for Alerting Administrators](../../2014/reporting-services/data-alert-manager-for-alerting-administrators.md) </span></span>  
 [<span data-ttu-id="22938-137">Reporting Services 数据警报</span><span class="sxs-lookup"><span data-stu-id="22938-137">Reporting Services Data Alerts</span></span>](../ssms/agent/alerts.md)  
  
  
