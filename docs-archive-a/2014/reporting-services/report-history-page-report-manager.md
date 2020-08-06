---
title: 报表历史记录页 (报表管理器) |Microsoft Docs
ms.prod: sql-server-2014
ms.technology: reporting-services-native
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.custom: ''
ms.date: 06/13/2017
ms.openlocfilehash: 4070be8c1d6b0633131e96c665d4551c1b676a9e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586343"
---
# <a name="report-history-page-report-manager"></a><span data-ttu-id="c98bb-102">“报表历史记录”页（报表管理器）</span><span class="sxs-lookup"><span data-stu-id="c98bb-102">Report History Page (Report Manager)</span></span>

<span data-ttu-id="c98bb-103">使用“报表历史记录”页可以查看一段时间中生成并存储的报表快照。</span><span class="sxs-lookup"><span data-stu-id="c98bb-103">Use the Report History page to view report snapshots that are generated and stored over time.</span></span> <span data-ttu-id="c98bb-104">根据报表服务器上设置的选项，报表历史记录可能只包含较新的快照。</span><span class="sxs-lookup"><span data-stu-id="c98bb-104">Depending on options that are set on the report server, report history may contain only the more recent snapshots.</span></span>  
  

<span data-ttu-id="c98bb-105">报表历史记录总是显示在所源于的报表的上下文中。</span><span class="sxs-lookup"><span data-stu-id="c98bb-105">Report history is always viewed within the context of the report from which it originates.</span></span> <span data-ttu-id="c98bb-106">您不能一起查看报表服务器中所有报表的历史记录。</span><span class="sxs-lookup"><span data-stu-id="c98bb-106">You cannot view the history of all reports on a report server in one place.</span></span>  
  
<span data-ttu-id="c98bb-107">要生成报表历史记录，报表必须能够以无人参与的方式运行（也就是说，报表必须使用存储的凭据；参数化报表必须包含所有参数的默认参数值）。</span><span class="sxs-lookup"><span data-stu-id="c98bb-107">To generate report history, the report must be able to run unattended (that is, it must use stored credentials; parameterized reports must contain default parameter values for all parameters).</span></span> <span data-ttu-id="c98bb-108">可以手动或以计划操作方式生成报表历史记录。</span><span class="sxs-lookup"><span data-stu-id="c98bb-108">Report history can be generated manually or as a scheduled operation.</span></span> <span data-ttu-id="c98bb-109">报表的历史记录属性决定报表历史记录的创建方式。</span><span class="sxs-lookup"><span data-stu-id="c98bb-109">History properties on the report determine the ways in which report history can be created.</span></span>  
  
<span data-ttu-id="c98bb-110">您可以通过单击报表历史记录快照来查看它。</span><span class="sxs-lookup"><span data-stu-id="c98bb-110">You can click a report history snapshot to view it.</span></span> <span data-ttu-id="c98bb-111">报表历史记录中显示的快照只能通过创建的日期和时间来区分。</span><span class="sxs-lookup"><span data-stu-id="c98bb-111">Snapshots that appear in report history are distinguished only by the date and time at which they were created.</span></span> <span data-ttu-id="c98bb-112">无法通过直观方式判断出某个快照是为响应计划而生成的还是为响应某个手动操作而生成的。</span><span class="sxs-lookup"><span data-stu-id="c98bb-112">There is no visual indication to distinguish whether a snapshot was generated in response to a schedule or a manual operation.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c98bb-113">并非在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]的每个版本中均提供此功能。</span><span class="sxs-lookup"><span data-stu-id="c98bb-113">This feature is not available in every edition of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="c98bb-114">有关各个版本支持的功能列表 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ，请参阅 SQL Server 2014 的各个[版本支持的功能](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)。</span><span class="sxs-lookup"><span data-stu-id="c98bb-114">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="c98bb-115">导航</span><span class="sxs-lookup"><span data-stu-id="c98bb-115">Navigation</span></span>  
 <span data-ttu-id="c98bb-116">使用以下过程导航到用户界面 (UI) 中的这一位置。</span><span class="sxs-lookup"><span data-stu-id="c98bb-116">Use the following procedure to navigate to this location in the user interface (UI).</span></span>  
  
### <a name="to-open-the-report-history-page"></a><span data-ttu-id="c98bb-117">打开“报表历史记录”页</span><span class="sxs-lookup"><span data-stu-id="c98bb-117">To open the Report History page</span></span>  
  
1.  <span data-ttu-id="c98bb-118">打开报表管理器，找到要查看报表快照的报表。</span><span class="sxs-lookup"><span data-stu-id="c98bb-118">Open Report Manager, and locate the report for which you want to view report snapshots.</span></span>  
  
2.  <span data-ttu-id="c98bb-119">悬停在该报表之上，然后单击下拉箭头。</span><span class="sxs-lookup"><span data-stu-id="c98bb-119">Hover over the report, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="c98bb-120">在下拉菜单中，单击 **“查看报表历史记录”**。</span><span class="sxs-lookup"><span data-stu-id="c98bb-120">In the drop-down menu, click **View Report History**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="c98bb-121">选项</span><span class="sxs-lookup"><span data-stu-id="c98bb-121">Options</span></span>  
 <span data-ttu-id="c98bb-122">**删除**</span><span class="sxs-lookup"><span data-stu-id="c98bb-122">**Delete**</span></span>  
 <span data-ttu-id="c98bb-123">单击此选项可删除一个或多个快照。</span><span class="sxs-lookup"><span data-stu-id="c98bb-123">Click to delete one or more snapshots.</span></span> <span data-ttu-id="c98bb-124">在单击 **“删除”** 之前，请选中要删除的快照旁的复选框。</span><span class="sxs-lookup"><span data-stu-id="c98bb-124">Before clicking **Delete**, select the check box next to the snapshot that you want to delete.</span></span>  
  
 <span data-ttu-id="c98bb-125">**新建快照**</span><span class="sxs-lookup"><span data-stu-id="c98bb-125">**New Snapshot**</span></span>  
 <span data-ttu-id="c98bb-126">单击此选项可向报表历史记录中添加快照。</span><span class="sxs-lookup"><span data-stu-id="c98bb-126">Click to add a snapshot to report history.</span></span> <span data-ttu-id="c98bb-127">如果在报表的“历史记录”属性页上选择了 **“允许手动创建历史记录”** 选项，则此按钮可用。</span><span class="sxs-lookup"><span data-stu-id="c98bb-127">This button is available when you choose the option **Allow history to be created manually** on the History properties page of the report.</span></span>  
  
 <span data-ttu-id="c98bb-128">**上次运行时间**</span><span class="sxs-lookup"><span data-stu-id="c98bb-128">**Last Run**</span></span>  
 <span data-ttu-id="c98bb-129">显示快照创建的日期和时间。</span><span class="sxs-lookup"><span data-stu-id="c98bb-129">Displays the date and time at which the snapshot was created.</span></span> <span data-ttu-id="c98bb-130">单击说明可以查看某个特定的快照。</span><span class="sxs-lookup"><span data-stu-id="c98bb-130">Click a description to view a particular snapshot.</span></span>  
  
 <span data-ttu-id="c98bb-131">**大小**</span><span class="sxs-lookup"><span data-stu-id="c98bb-131">**Size**</span></span>  
 <span data-ttu-id="c98bb-132">显示报表定义及报表中的数据的总大小。</span><span class="sxs-lookup"><span data-stu-id="c98bb-132">Displays the size of the report definition plus the data in the report.</span></span> <span data-ttu-id="c98bb-133">此值指示报表定义和数据所占用的报表服务器数据库的空间。</span><span class="sxs-lookup"><span data-stu-id="c98bb-133">This value indicates how much space in the report server database is used by the report definition and data.</span></span> <span data-ttu-id="c98bb-134">呈现的报表的大小（包括格式）实际偏大。</span><span class="sxs-lookup"><span data-stu-id="c98bb-134">The size of the rendered report, which includes formatting, is actually larger.</span></span> <span data-ttu-id="c98bb-135">括号中的总大小是当前报表的报表历史记录中所有快照大小的总和。</span><span class="sxs-lookup"><span data-stu-id="c98bb-135">The total size, indicated in parentheses, sums the sizes of all snapshots in the report history for the current report.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c98bb-136">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c98bb-136">See Also</span></span>  
 <span data-ttu-id="c98bb-137">[查看或删除报表历史记录 &#40;报表管理器&#41;](../../2014/reporting-services/view-or-delete-report-history-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="c98bb-137">[View or Delete Report History &#40;Report Manager&#41;](../../2014/reporting-services/view-or-delete-report-history-report-manager.md) </span></span>  
 <span data-ttu-id="c98bb-138">[将快照添加到报表历史记录 &#40;报表管理器&#41;](report-server/add-a-snapshot-to-report-history-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="c98bb-138">[Add a Snapshot to Report History &#40;Report Manager&#41;](report-server/add-a-snapshot-to-report-history-report-manager.md) </span></span>  
 <span data-ttu-id="c98bb-139">[报表 &#40;报表管理器的 "常规属性" 页&#41;](../../2014/reporting-services/general-properties-page-reports-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="c98bb-139">[General Properties Page, Reports &#40;Report Manager&#41;](../../2014/reporting-services/general-properties-page-reports-report-manager.md) </span></span>  
 <span data-ttu-id="c98bb-140">[报表管理器 F1 帮助](../../2014/reporting-services/report-manager-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="c98bb-140">[Report Manager F1 Help](../../2014/reporting-services/report-manager-f1-help.md) </span></span>  
 [<span data-ttu-id="c98bb-141">"快照选项" 属性页 &#40;报表管理器&#41;</span><span class="sxs-lookup"><span data-stu-id="c98bb-141">Snapshot Options Properties Page &#40;Report Manager&#41;</span></span>](../../2014/reporting-services/snapshot-options-properties-page-report-manager.md)