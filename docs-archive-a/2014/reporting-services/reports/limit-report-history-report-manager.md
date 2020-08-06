---
title: 限制报表历史记录（报表管理器）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- viewing report history
- report history [Reporting Services], viewing history
- report history [Reporting Services], configuring history
- historical data [Reporting Services]
- displaying report history
ms.assetid: 8e255792-d9ef-496f-a26c-9e969c1209a0
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 01318b1e1ccf0b0bf4512ab57de90cbf5ebc7365
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688504"
---
# <a name="limit-report-history-report-manager"></a><span data-ttu-id="1fb33-102">限制报表历史记录（报表管理器）</span><span class="sxs-lookup"><span data-stu-id="1fb33-102">Limit Report History (Report Manager)</span></span>
  <span data-ttu-id="1fb33-103">报表历史记录是随着时间变化而创建的报表快照的集合。</span><span class="sxs-lookup"><span data-stu-id="1fb33-103">Report history is a collection of report snapshots that you create over time.</span></span> <span data-ttu-id="1fb33-104">您可以按需创建报表历史记录，也可以安排快照的创建频率以及将快照添加到报表历史记录中的频率。</span><span class="sxs-lookup"><span data-stu-id="1fb33-104">You can create report history on demand, or schedule how often a snapshot is created and added to report history.</span></span>  
  
 <span data-ttu-id="1fb33-105">报表历史记录存储在报表服务器数据库中。</span><span class="sxs-lookup"><span data-stu-id="1fb33-105">Report history is stored in the report server database.</span></span> <span data-ttu-id="1fb33-106">如果报表快照中包含大量数据，则可以考虑限制报表历史记录，以便尽可能减少快照保持期对数据库大小的影响。</span><span class="sxs-lookup"><span data-stu-id="1fb33-106">If report snapshots contain a large amount of data, you might consider limiting report history to minimize the affect of snapshot retention on database size.</span></span>  
  
### <a name="to-configure-report-history-for-a-report-server"></a><span data-ttu-id="1fb33-107">为报表服务器配置报表历史记录</span><span class="sxs-lookup"><span data-stu-id="1fb33-107">To configure report history for a report server</span></span>  
  
1.  <span data-ttu-id="1fb33-108">在报表管理器中，单击全局工具栏上的 **“站点设置”** 。</span><span class="sxs-lookup"><span data-stu-id="1fb33-108">In Report Manager, click **Site Settings** on the global toolbar.</span></span>  
  
2.  <span data-ttu-id="1fb33-109">如果希望无限制地保留所有报表历史记录，请选择 **“不限制报表历史记录中保留的快照数”** 。</span><span class="sxs-lookup"><span data-stu-id="1fb33-109">Select **Keep an unlimited number of snapshots in report history** if you want to keep all report history indefinitely.</span></span> <span data-ttu-id="1fb33-110">否则，请选择 **“限制报表历史记录的副本数”** ，以指定可以为任何给定报表保留的最多快照数。</span><span class="sxs-lookup"><span data-stu-id="1fb33-110">Otherwise, select **Limit the copies of report history** to specify the maximum number of snapshots that can be kept for any given report.</span></span>  
  
3.  <span data-ttu-id="1fb33-111">单击“应用”。</span><span class="sxs-lookup"><span data-stu-id="1fb33-111">Click **Apply**.</span></span>  
  
### <a name="to-configure-report-history-for-a-specific-report"></a><span data-ttu-id="1fb33-112">为特定的报表配置报表历史记录</span><span class="sxs-lookup"><span data-stu-id="1fb33-112">To configure report history for a specific report</span></span>  
  
1.  <span data-ttu-id="1fb33-113">在报表管理器中，导航到要配置历史记录的报表，再单击该报表将其打开。</span><span class="sxs-lookup"><span data-stu-id="1fb33-113">In Report Manager, navigate to the report for which you want to configure history, and then click the report to open it.</span></span>  
  
2.  <span data-ttu-id="1fb33-114">单击“属性”选项卡。</span><span class="sxs-lookup"><span data-stu-id="1fb33-114">Click the **Properties** tab.</span></span>  
  
3.  <span data-ttu-id="1fb33-115">单击 **“历史记录”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="1fb33-115">Click the **History** tab.</span></span>  
  
4.  <span data-ttu-id="1fb33-116">为您的报表选择相应选项，再单击 **“应用”**。</span><span class="sxs-lookup"><span data-stu-id="1fb33-116">Select the options for your report and click **Apply**.</span></span> <span data-ttu-id="1fb33-117">有关每个选项的详细信息，请参阅[“快照选项”属性页（报表管理器）](../snapshot-options-properties-page-report-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="1fb33-117">For details about each option, see [Snapshot Options Properties Page &#40;Report Manager&#41;](../snapshot-options-properties-page-report-manager.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1fb33-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1fb33-118">See Also</span></span>  
 <span data-ttu-id="1fb33-119">[将快照添加到报表历史记录 &#40;报表管理器&#41;](../report-server/add-a-snapshot-to-report-history-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="1fb33-119">[Add a Snapshot to Report History &#40;Report Manager&#41;](../report-server/add-a-snapshot-to-report-history-report-manager.md) </span></span>  
 [<span data-ttu-id="1fb33-120">报表管理器（SSRS 本机模式）</span><span class="sxs-lookup"><span data-stu-id="1fb33-120">Report Manager  &#40;SSRS Native Mode&#41;</span></span>](../report-manager-ssrs-native-mode.md)  
  
  
