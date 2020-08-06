---
title: 暂停报表和订阅处理 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- pausing schedules
- subscriptions [Reporting Services], pausing
- report processing [Reporting Services], pausing
- shared data sources [Reporting Services]
- pausing subscription processing
- pausing report processing
- temporarily stopping report processing
- disabling shared data sources
- roles [Reporting Services], modifying
- shared schedules [Reporting Services], pausing
ms.assetid: 3cf9a240-24cc-46d4-bec6-976f82d8f830
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 1607637630c507588602dd7e566917ce1eeb6080
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691579"
---
# <a name="pause-report-and-subscription-processing"></a><span data-ttu-id="c5eed-102">暂停报表和订阅处理</span><span class="sxs-lookup"><span data-stu-id="c5eed-102">Pause Report and Subscription Processing</span></span>
  <span data-ttu-id="c5eed-103">您不能直接暂停报表或订阅。</span><span class="sxs-lookup"><span data-stu-id="c5eed-103">You cannot pause a report or subscription directly.</span></span> <span data-ttu-id="c5eed-104">不过，在报表和订阅处理进程启动之前或者在建立数据源连接时，您可以中断报表和订阅处理。</span><span class="sxs-lookup"><span data-stu-id="c5eed-104">However, you can interrupt report and subscription processing prior to the process starting or when a data source connection is made.</span></span> <span data-ttu-id="c5eed-105">您还可以通过使用户不能访问报表或订阅，来阻止对报表或订阅进行处理。</span><span class="sxs-lookup"><span data-stu-id="c5eed-105">You can also prevent a report or subscription from processing by making it inaccessible to users.</span></span>  
  
 <span data-ttu-id="c5eed-106">您可以使用以下策略暂时阻止进行处理。</span><span class="sxs-lookup"><span data-stu-id="c5eed-106">The following strategies can be used to temporarily prevent a process from occurring.</span></span>  
  
## <a name="modify-role-assignments-to-prevent-access"></a><span data-ttu-id="c5eed-107">通过修改角色分配来阻止访问</span><span class="sxs-lookup"><span data-stu-id="c5eed-107">Modify Role Assignments to Prevent Access</span></span>  
 <span data-ttu-id="c5eed-108">使报表不可用的最佳方法是，暂时删除提供报表访问权限的角色分配。</span><span class="sxs-lookup"><span data-stu-id="c5eed-108">The best way to make a report unavailable is to temporarily remove the role assignment that provides access to the report.</span></span> <span data-ttu-id="c5eed-109">无论采用哪种数据源连接，对所有报表都可以使用这种方法。</span><span class="sxs-lookup"><span data-stu-id="c5eed-109">This approach can be used on all reports regardless of how the data source connection is made.</span></span> <span data-ttu-id="c5eed-110">这种方法只针对目标报表，不会影响其他报表或项的操作。</span><span class="sxs-lookup"><span data-stu-id="c5eed-110">This approach targets only the report, without affecting the operation of other reports or items.</span></span>  
  
 <span data-ttu-id="c5eed-111">若要删除角色分配，请在报表管理器中打开报表的“安全属性”页。</span><span class="sxs-lookup"><span data-stu-id="c5eed-111">To remove the role assignment, open the Security Properties page of the report in Report Manager.</span></span> <span data-ttu-id="c5eed-112">如果报表的安全设置是从父报表继承来的，则可以单击“编辑项安全设置”\*\*\*\*，创建一个忽略提供大范围访问权的角色分配的限制性安全策略。例如，可以删除为 Everyone 提供访问权的角色分配，而保留为一组少量用户（如 Administrators）提供访问权的角色分配。</span><span class="sxs-lookup"><span data-stu-id="c5eed-112">If the report inherits security from a parent, you can click **Edit Item Security** to create a restrictive security policy that omits role assignments that provide widespread access (for example, you can remove a role assignment that provides access to Everyone, and keep the role assignment that provides access to a small group of users, such as Administrators).</span></span>  
  
## <a name="disable-a-shared-data-source"></a><span data-ttu-id="c5eed-113">禁用共享数据源</span><span class="sxs-lookup"><span data-stu-id="c5eed-113">Disable a Shared Data Source</span></span>  
 <span data-ttu-id="c5eed-114">使用共享数据源的一个优点是您可以通过禁用它来阻止报表或数据驱动订阅运行。</span><span class="sxs-lookup"><span data-stu-id="c5eed-114">One advantage to using shared data sources is that you can disable it to prevent a report or data-driven subscription from running.</span></span> <span data-ttu-id="c5eed-115">禁用共享数据源会断开报表与其外部源的连接。</span><span class="sxs-lookup"><span data-stu-id="c5eed-115">Disabling a shared data source disconnects the report from its external source.</span></span> <span data-ttu-id="c5eed-116">禁用共享数据源后，所有原来使用该数据源的报表和订阅将无法再继续访问该数据源。</span><span class="sxs-lookup"><span data-stu-id="c5eed-116">While it is disabled, the data source is unavailable to all reports and subscriptions that use it.</span></span> <span data-ttu-id="c5eed-117">若要禁用共享数据源，请在报表管理器中打开相应的数据源，再清除 **“启用此数据源”** 复选框。</span><span class="sxs-lookup"><span data-stu-id="c5eed-117">To disable a shared data source, open the data source in Report Manager and clear the **Enable this data source** check box.</span></span>  
  
 <span data-ttu-id="c5eed-118">请注意，即使数据源不可用，您也仍可加载相应的报表。</span><span class="sxs-lookup"><span data-stu-id="c5eed-118">Note that the report still loads even if the data source is unavailable.</span></span> <span data-ttu-id="c5eed-119">该报表不包含任何数据，但具有适当权限的用户可以访问与该报表关联的属性页、安全设置、报表历史记录和订阅信息。</span><span class="sxs-lookup"><span data-stu-id="c5eed-119">The report does not contain data, but users with appropriate permissions can access the property pages, security settings, report history, and subscription information associated with the report.</span></span>  
  
## <a name="pause-a-shared-schedule"></a><span data-ttu-id="c5eed-120">暂停共享计划</span><span class="sxs-lookup"><span data-stu-id="c5eed-120">Pause a Shared Schedule</span></span>  
 <span data-ttu-id="c5eed-121">如果报表或订阅按照某个共享计划运行，您可以通过暂停该计划来阻止这些报表或订阅的处理。</span><span class="sxs-lookup"><span data-stu-id="c5eed-121">If a report or subscription runs from a shared schedule, you can pause the schedule to prevent processing.</span></span> <span data-ttu-id="c5eed-122">在恢复计划之前，会延迟由该计划驱动的所有报表和订阅处理。</span><span class="sxs-lookup"><span data-stu-id="c5eed-122">All report and subscription processing that is driven by the schedule is deferred until the schedule is resumed.</span></span> <span data-ttu-id="c5eed-123">有关详细信息，请参阅[暂停和恢复共享计划](schedules.md)。</span><span class="sxs-lookup"><span data-stu-id="c5eed-123">For more information, see [Pause and Resume Shared Schedules](schedules.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5eed-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c5eed-124">See Also</span></span>  
 <span data-ttu-id="c5eed-125">[Reporting Services 报表服务器（本机模式）](../report-server/reporting-services-report-server-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="c5eed-125">[Reporting Services Report Server &#40;Native Mode&#41;](../report-server/reporting-services-report-server-native-mode.md) </span></span>  
 <span data-ttu-id="c5eed-126">[报表管理器（SSRS 本机模式）](../report-manager-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="c5eed-126">[Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md) </span></span>  
 [<span data-ttu-id="c5eed-127">项的“安全性”属性页（报表管理器）</span><span class="sxs-lookup"><span data-stu-id="c5eed-127">Security Properties Page, Items &#40;Report Manager&#41;</span></span>](../security-properties-page-items-report-manager.md)  
  
  
