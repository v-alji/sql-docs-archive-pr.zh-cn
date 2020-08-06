---
title: 在数据警报管理器中管理 SharePoint 站点上的所有数据警报 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- managing, alerts
- managing, data alerts
ms.assetid: 9c70b0f4-2db8-4c2e-acbf-96e2a55ddc48
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b41fdbd18a0b1b4a7a69a3ca202de1c555c070de
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691635"
---
# <a name="manage-all-data-alerts-on-a-sharepoint-site-in-data-alert-manager"></a><span data-ttu-id="a9f64-102">在数据警报管理器中管理 SharePoint 站点上的所有数据警报</span><span class="sxs-lookup"><span data-stu-id="a9f64-102">Manage All Data Alerts on a SharePoint Site in Data Alert Manager</span></span>
  <span data-ttu-id="a9f64-103">SharePoint 警报管理员可以查看由任何站点用户创建的数据警报的列表以及有关警报的信息。</span><span class="sxs-lookup"><span data-stu-id="a9f64-103">SharePoint alerting administrators can view a list of the data alerts that were created by any site user and information about the alerts.</span></span> <span data-ttu-id="a9f64-104">警报管理员也可以删除警报。</span><span class="sxs-lookup"><span data-stu-id="a9f64-104">Alerting administrators can also delete alerts.</span></span> <span data-ttu-id="a9f64-105">下图显示数据警报管理器中可用于警报管理员的功能。</span><span class="sxs-lookup"><span data-stu-id="a9f64-105">The following picture shows the features available to alerting administrators in Data Alert Manager.</span></span>  
  
 <span data-ttu-id="a9f64-106">![SharePoint 网站管理员的警报管理器](media/rs-alertmanagersite.gif "SharePoint 网站管理员的警报管理器")</span><span class="sxs-lookup"><span data-stu-id="a9f64-106">![Alert Manager for SharePoin tsite administrators](media/rs-alertmanagersite.gif "Alert Manager for SharePoin tsite administrators")</span></span>  
  
### <a name="to-view-a-list-of-alerts-created-by-a-site-user"></a><span data-ttu-id="a9f64-107">查看站点用户所创建的警报列表</span><span class="sxs-lookup"><span data-stu-id="a9f64-107">To view a list of alerts created by a site user</span></span>  
  
1.  <span data-ttu-id="a9f64-108">转到保存数据警报定义的 SharePoint 站点。</span><span class="sxs-lookup"><span data-stu-id="a9f64-108">Go to the SharePoint site where data alerts definitions are saved.</span></span>  
  
2.  <span data-ttu-id="a9f64-109">在主页上，单击 **“网站操作”**。</span><span class="sxs-lookup"><span data-stu-id="a9f64-109">On the Home page, click **Site Actions**.</span></span>  
  
3.  <span data-ttu-id="a9f64-110">滚动到该列表的底部，然后单击 **“站点设置”**。</span><span class="sxs-lookup"><span data-stu-id="a9f64-110">Scroll to the bottom of the list and click **Site Settings**.</span></span>  
  
4.  <span data-ttu-id="a9f64-111">在 **Reporting Services**下，单击 **“管理数据警报”**。</span><span class="sxs-lookup"><span data-stu-id="a9f64-111">Under **Reporting Services**, click **Manage Data Alerts**.</span></span>  
  
5.  <span data-ttu-id="a9f64-112">单击 **“查看用户警报”** 列表旁的向下箭头并且选择您要查看其警报的用户。</span><span class="sxs-lookup"><span data-stu-id="a9f64-112">Click the down arrow by the **View alerts for user** list and select the user whose alerts you want to view.</span></span>  
  
6.  <span data-ttu-id="a9f64-113">单击 **“查看报表警报”** 列表旁的向下箭头并且选择要查看的特定警报，或者单击 **“全部显示”** 以列出所选用户创建的所有警报。</span><span class="sxs-lookup"><span data-stu-id="a9f64-113">Click the down arrow next to the **View alerts for report** list and select a specific alert to view, or click **Show All** to list all alerts created by the selected user.</span></span>  
  
     <span data-ttu-id="a9f64-114">表将列出名称、报表名称、创建了数据警报的人员的姓名、发送数据警报的数目、上次修改数据警报定义的时间以及数据警报的状态。</span><span class="sxs-lookup"><span data-stu-id="a9f64-114">A table lists the name, report name, name of the person who created the data alert, the number times the data alert was sent, the last time the data alert definition was modified, and the status of the data alert.</span></span> <span data-ttu-id="a9f64-115">如果无法生成或发送数据警报，则状态列将包含有关该错误的信息并且帮助您解决这个问题。</span><span class="sxs-lookup"><span data-stu-id="a9f64-115">If the data alert cannot be generated or sent, the status column contains information about the error and helps you troubleshoot the problem.</span></span>  
  
### <a name="to-delete-an-alert-definition"></a><span data-ttu-id="a9f64-116">删除警报定义</span><span class="sxs-lookup"><span data-stu-id="a9f64-116">To delete an alert definition</span></span>  
  
-   <span data-ttu-id="a9f64-117">右键单击要删除的数据警报，然后单击“删除”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a9f64-117">Right-click the data alert that you want to delete and click **Delete**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a9f64-118">删除警报定义后，将不会发送进一步的警报消息。</span><span class="sxs-lookup"><span data-stu-id="a9f64-118">After you delete the alert, no further alert messages are sent.</span></span> <span data-ttu-id="a9f64-119">但是，如果您查询警报数据库，可能会发现该警报定义仍存在。</span><span class="sxs-lookup"><span data-stu-id="a9f64-119">However, if you query the alerting database you might find that the alert definition still exists.</span></span> <span data-ttu-id="a9f64-120">警报服务将按照计划执行清除，因此该警报定义将在下次清除中被永久删除。</span><span class="sxs-lookup"><span data-stu-id="a9f64-120">The alerting service performs clean up on a schedule and the alert definition is deleted permanently in the next cleanup.</span></span> <span data-ttu-id="a9f64-121">默认清除间隔为 20 分钟。</span><span class="sxs-lookup"><span data-stu-id="a9f64-121">The default cleanup interval is 20 minutes.</span></span> <span data-ttu-id="a9f64-122">此设置以及其他清除间隔都是可配置的。</span><span class="sxs-lookup"><span data-stu-id="a9f64-122">This and other cleanup intervals are configurable.</span></span> <span data-ttu-id="a9f64-123">有关详细信息，请参阅 [Reporting Services 数据警报](../ssms/agent/alerts.md)。</span><span class="sxs-lookup"><span data-stu-id="a9f64-123">For more information, see [Reporting Services Data Alerts](../ssms/agent/alerts.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9f64-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a9f64-124">See Also</span></span>  
 <span data-ttu-id="a9f64-125">[向管理员提出警报的数据警报管理器](../../2014/reporting-services/data-alert-manager-for-alerting-administrators.md) </span><span class="sxs-lookup"><span data-stu-id="a9f64-125">[Data Alert Manager for Alerting Administrators](../../2014/reporting-services/data-alert-manager-for-alerting-administrators.md) </span></span>  
 [<span data-ttu-id="a9f64-126">Reporting Services 数据警报</span><span class="sxs-lookup"><span data-stu-id="a9f64-126">Reporting Services Data Alerts</span></span>](../ssms/agent/alerts.md)  
  
  
