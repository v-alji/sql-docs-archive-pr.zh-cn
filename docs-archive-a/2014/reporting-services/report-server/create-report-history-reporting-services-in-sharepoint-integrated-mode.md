---
title: 创建报表历史记录（SharePoint 集成模式下的 Reporting Services）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- report history [Reporting Services], SharePoint
ms.assetid: e57ec746-05ae-4ff6-8e39-6cde87310daa
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 996202580bbacc24080460c2c43218db27294d76
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588279"
---
# <a name="create-report-history-reporting-services-in-sharepoint-integrated-mode"></a><span data-ttu-id="d7fd8-102">创建报表历史记录（SharePoint 集成模式下的 Reporting Services）</span><span class="sxs-lookup"><span data-stu-id="d7fd8-102">Create Report History (Reporting Services in SharePoint Integrated Mode)</span></span>
  <span data-ttu-id="d7fd8-103">报表历史记录是随着时间变化而创建的报表快照的集合。</span><span class="sxs-lookup"><span data-stu-id="d7fd8-103">Report history is a collection of report snapshots that you create over time.</span></span> <span data-ttu-id="d7fd8-104">每个快照都是报表创建时所生成的报表的副本。</span><span class="sxs-lookup"><span data-stu-id="d7fd8-104">Each snapshot is a copy of the report as it existed when it was created.</span></span> <span data-ttu-id="d7fd8-105">它包含创建快照时该报表当时的布局和数据。</span><span class="sxs-lookup"><span data-stu-id="d7fd8-105">It includes the layout and data that was current for the report when the snapshot was created.</span></span> <span data-ttu-id="d7fd8-106">呈现信息不与快照存储在一起。</span><span class="sxs-lookup"><span data-stu-id="d7fd8-106">Rendering information is not stored with the snapshot.</span></span> <span data-ttu-id="d7fd8-107">打开报表历史记录中的快照时，它将在报表查看器 Web 部件中以 HTML 形式打开。</span><span class="sxs-lookup"><span data-stu-id="d7fd8-107">When you open a snapshot in report history, it opens in HTML in the Report Viewer Web Part.</span></span> <span data-ttu-id="d7fd8-108">呈现该快照后，您可以将其导出为其他应用程序格式。</span><span class="sxs-lookup"><span data-stu-id="d7fd8-108">After it is rendered, you can export it to other application formats.</span></span>  
  
 <span data-ttu-id="d7fd8-109">若要创建报表历史记录，报表必须能够以无人参与的形式运行（也就是说，报表服务器必须能够在没有用户交互的情况下运行报表）。</span><span class="sxs-lookup"><span data-stu-id="d7fd8-109">To create report history, the report must be able to run unattended (that is, the report server must be able to run the report without user interaction).</span></span> <span data-ttu-id="d7fd8-110">必须对包含报表的库拥有“编辑项”权限。</span><span class="sxs-lookup"><span data-stu-id="d7fd8-110">You must have Edit Items permission on the library that contains the report.</span></span> <span data-ttu-id="d7fd8-111">若要查看或删除报表历史记录，您必须拥有“查看版本”或“删除版本”权限。</span><span class="sxs-lookup"><span data-stu-id="d7fd8-111">To view or delete report history, you must have View Versions or Delete Versions permissions.</span></span>  
  
### <a name="to-create-a-snapshot-or-report-history-on-demand"></a><span data-ttu-id="d7fd8-112">按需创建快照或报表历史记录</span><span class="sxs-lookup"><span data-stu-id="d7fd8-112">To create a snapshot or report history on demand</span></span>  
  
1.  <span data-ttu-id="d7fd8-113">指向报表。</span><span class="sxs-lookup"><span data-stu-id="d7fd8-113">Point to the report.</span></span>  
  
2.  <span data-ttu-id="d7fd8-114">单击以显示下箭头，然后选择 **“查看报表历史记录”** 。</span><span class="sxs-lookup"><span data-stu-id="d7fd8-114">Click to display the down arrow, and then select **View Report History**.</span></span>  
  
3.  <span data-ttu-id="d7fd8-115">单击 **“新建快照”** 。</span><span class="sxs-lookup"><span data-stu-id="d7fd8-115">Click **New Snapshot**.</span></span> <span data-ttu-id="d7fd8-116">如果该按钮不可见，则是因为您没有在报表历史记录中创建快照的权限。</span><span class="sxs-lookup"><span data-stu-id="d7fd8-116">If the button is not visible, it is because you do not have permission to create snapshots in report history.</span></span>  
  
4.  <span data-ttu-id="d7fd8-117">若要查看您刚创建的快照，从列表中将其选中。</span><span class="sxs-lookup"><span data-stu-id="d7fd8-117">To view the snapshot you just created, select it from the list.</span></span> <span data-ttu-id="d7fd8-118">每个快照都是由用来显示何时创建快照的时间戳进行标识的。</span><span class="sxs-lookup"><span data-stu-id="d7fd8-118">Each snapshot is identified by a timestamp that shows when the snapshot was created.</span></span> <span data-ttu-id="d7fd8-119">您不能重命名快照，不能将其移动到另一个位置，也不能修改它。</span><span class="sxs-lookup"><span data-stu-id="d7fd8-119">You cannot rename the snapshot, move it to another location, or modify it.</span></span>  
  
### <a name="to-schedule-report-history"></a><span data-ttu-id="d7fd8-120">计划报表历史记录</span><span class="sxs-lookup"><span data-stu-id="d7fd8-120">To schedule report history</span></span>  
  
1.  <span data-ttu-id="d7fd8-121">指向报表。</span><span class="sxs-lookup"><span data-stu-id="d7fd8-121">Point to the report.</span></span>  
  
2.  <span data-ttu-id="d7fd8-122">单击以显示下箭头，然后选择 **“管理处理选项”** 。</span><span class="sxs-lookup"><span data-stu-id="d7fd8-122">Click to display the down arrow, and then select **Manage Processing Options**.</span></span>  
  
3.  <span data-ttu-id="d7fd8-123">在 **“历史记录快照选项”** 中，单击 **“根据计划创建报表历史记录快照”** 。</span><span class="sxs-lookup"><span data-stu-id="d7fd8-123">In **History Snapshot Options**, click **Create report history snapshots on a schedule**.</span></span>  
  
4.  <span data-ttu-id="d7fd8-124">如果您有包含要使用的计划信息的共享计划，请单击 **“根据共享计划”** 并选择要使用的计划。</span><span class="sxs-lookup"><span data-stu-id="d7fd8-124">If you have a shared schedule that contains the schedule information you want to use, click **On a shared schedule** and select the schedule you want to use.</span></span> <span data-ttu-id="d7fd8-125">否则，请单击 **“根据自定义计划”** ，然后单击 **“配置”** 以指定根据重复执行的计划来创建报表历史记录的选项。</span><span class="sxs-lookup"><span data-stu-id="d7fd8-125">Otherwise, click **On a custom schedule**, and then click **Configure** to specify options to create report history on a recurring schedule.</span></span>  
  
### <a name="to-create-report-history-when-data-is-refreshed-in-a-report"></a><span data-ttu-id="d7fd8-126">在刷新报表中的数据时创建报表历史记录</span><span class="sxs-lookup"><span data-stu-id="d7fd8-126">To create report history when data is refreshed in a report</span></span>  
  
1.  <span data-ttu-id="d7fd8-127">指向报表。</span><span class="sxs-lookup"><span data-stu-id="d7fd8-127">Point to the report.</span></span>  
  
2.  <span data-ttu-id="d7fd8-128">单击以显示下箭头，然后选择 **“管理处理选项”** 。</span><span class="sxs-lookup"><span data-stu-id="d7fd8-128">Click to display the down arrow, and then select **Manage Processing Options**.</span></span>  
  
3.  <span data-ttu-id="d7fd8-129">在 **“历史记录快照选项”** 中，单击 **“在报表历史记录中存储所有报表数据快照”** 。</span><span class="sxs-lookup"><span data-stu-id="d7fd8-129">In **History Snapshot Options**, click **Store all report data snapshots in report history**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7fd8-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d7fd8-130">See Also</span></span>  
 [<span data-ttu-id="d7fd8-131">设置处理选项（SharePoint 集成模式下的 Reporting Services）</span><span class="sxs-lookup"><span data-stu-id="d7fd8-131">Set Processing Options &#40;Reporting Services in SharePoint Integrated Mode&#41;</span></span>](../set-processing-options-reporting-services-in-sharepoint-integrated-mode.md)  
  
  
