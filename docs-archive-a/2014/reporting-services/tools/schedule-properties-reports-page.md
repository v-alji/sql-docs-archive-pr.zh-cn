---
title: 计划属性（“报表”页）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.scheduleproperties.reports.f1
ms.assetid: 7db728bd-4b08-43ef-a49a-e8dcdd37cf89
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: da0b5255e73522572fa22da8668329a28f108104
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580556"
---
# <a name="schedule-properties-reports-page"></a><span data-ttu-id="875b7-102">计划属性（“报表”页）</span><span class="sxs-lookup"><span data-stu-id="875b7-102">Schedule Properties (Reports Page)</span></span>
  <span data-ttu-id="875b7-103">使用此页可以查看使用此共享计划的所有报表的列表。</span><span class="sxs-lookup"><span data-stu-id="875b7-103">Use this page to view a list of all reports that use this shared schedule.</span></span> <span data-ttu-id="875b7-104">计划可用于刷新报表快照、生成报表历史记录、触发订阅或使报表的缓存副本过期。</span><span class="sxs-lookup"><span data-stu-id="875b7-104">Schedules can be used to refresh report snapshots, generate report history, trigger a subscription, or expire a cached copy of the report.</span></span> <span data-ttu-id="875b7-105">若要了解如何使用计划，请查看报表的属性和订阅信息。</span><span class="sxs-lookup"><span data-stu-id="875b7-105">To find out how the schedule is used, view the property and subscription information of the report.</span></span>  
  
 <span data-ttu-id="875b7-106">尽管此页显示了所有使用共享计划的报表，但是它并没有说明共享计划在单个报表中的使用次数。</span><span class="sxs-lookup"><span data-stu-id="875b7-106">Although this page shows each report that uses the shared schedule, it does not indicate how many times the shared schedule is used within that single report.</span></span> <span data-ttu-id="875b7-107">例如，假设 Company Sales 报表的 20 个不同的订阅均使用同一个共享计划来触发订阅处理。</span><span class="sxs-lookup"><span data-stu-id="875b7-107">For example, suppose 20 different subscribers to the Company Sales report all use the same shared schedule to trigger subscription processing.</span></span> <span data-ttu-id="875b7-108">在这种情况下，Company Sales 报表将仅在该列表中出现一次，即使该报表对共享计划引用了 20 次也是如此。</span><span class="sxs-lookup"><span data-stu-id="875b7-108">In this case, the Company Sales report will only appear once in this list, even though the report has 20 references to the shared schedule.</span></span>  
  
 <span data-ttu-id="875b7-109">若要打开此页，请启动 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，连接到 Report Server，打开 "**共享**计划" 文件夹，右键单击共享计划，选择 "**属性**"，然后单击 "**报表**"。</span><span class="sxs-lookup"><span data-stu-id="875b7-109">To open this page, start [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to a report server, open the **Shared Schedules** folder, right-click a shared schedule, select **Properties**, and then click **Reports**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="875b7-110">并非在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的每个版本中均提供此功能。</span><span class="sxs-lookup"><span data-stu-id="875b7-110">This feature is not available in every edition of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="875b7-111">有关各个版本支持的功能列表 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，请参阅[SQL Server 2012 (版本支持的功能](https://go.microsoft.com/fwlink/?linkid=232473) https://go.microsoft.com/fwlink/?linkid=232473) 。</span><span class="sxs-lookup"><span data-stu-id="875b7-111">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2012](https://go.microsoft.com/fwlink/?linkid=232473) (https://go.microsoft.com/fwlink/?linkid=232473).</span></span>  
  
## <a name="options"></a><span data-ttu-id="875b7-112">选项</span><span class="sxs-lookup"><span data-stu-id="875b7-112">Options</span></span>  
 <span data-ttu-id="875b7-113">**文件夹**</span><span class="sxs-lookup"><span data-stu-id="875b7-113">**Folder**</span></span>  
 <span data-ttu-id="875b7-114">指定报表的路径。</span><span class="sxs-lookup"><span data-stu-id="875b7-114">Specifies the path of the report.</span></span>  
  
 <span data-ttu-id="875b7-115">**Report**</span><span class="sxs-lookup"><span data-stu-id="875b7-115">**Report**</span></span>  
 <span data-ttu-id="875b7-116">指定使用该计划的报表的名称。</span><span class="sxs-lookup"><span data-stu-id="875b7-116">Specifies the name of the report that uses the schedule.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="875b7-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="875b7-117">See Also</span></span>  
 <span data-ttu-id="875b7-118">[创建、修改和删除计划](../subscriptions/create-modify-and-delete-schedules.md) </span><span class="sxs-lookup"><span data-stu-id="875b7-118">[Create, Modify, and Delete Schedules](../subscriptions/create-modify-and-delete-schedules.md) </span></span>  
 <span data-ttu-id="875b7-119">[“计划”](../subscriptions/schedules.md) </span><span class="sxs-lookup"><span data-stu-id="875b7-119">[Schedules](../subscriptions/schedules.md) </span></span>  
 <span data-ttu-id="875b7-120">[Management Studio F1 帮助中的报表服务器](report-server-in-management-studio-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="875b7-120">[Report Server in Management Studio F1 Help](report-server-in-management-studio-f1-help.md) </span></span>  
 <span data-ttu-id="875b7-121">[在 Management Studio 中连接到报表服务器](connect-to-a-report-server-in-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="875b7-121">[Connect to a Report Server in Management Studio](connect-to-a-report-server-in-management-studio.md) </span></span>  
 [<span data-ttu-id="875b7-122">配置报表的常规属性 &#40;报表管理器&#41;</span><span class="sxs-lookup"><span data-stu-id="875b7-122">Configure General Properties for a Report &#40;Report Manager&#41;</span></span>](../configure-general-properties-for-a-report-report-manager.md)  
  
  
