---
title: 缓存报表（报表管理器）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- report execution properties [Reporting Services]
- cache [Reporting Services]
- cached reports [Reporting Services]
- schedules [Reporting Services], report expiration
- expiration [Reporting Services]
ms.assetid: 723d1cb0-c2e7-4763-8690-a6a7a8bbbb90
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2e359e6c7a40b267979137ef2b3a285667a6fdb2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588308"
---
# <a name="cache-a-report-report-manager"></a><span data-ttu-id="e3f8e-102">如何缓存一个报表（报表管理器）</span><span class="sxs-lookup"><span data-stu-id="e3f8e-102">Cache a Report (Report Manager)</span></span>
  <span data-ttu-id="e3f8e-103">提高性能的一种方法是配置报表的缓存属性。</span><span class="sxs-lookup"><span data-stu-id="e3f8e-103">One way to improve performance is to configure caching properties for a report.</span></span> <span data-ttu-id="e3f8e-104">缓存报表后，会在一段时间内保存已呈现报表的副本。</span><span class="sxs-lookup"><span data-stu-id="e3f8e-104">When a report is cached, a copy of the rendered report is saved for a short period of time.</span></span> <span data-ttu-id="e3f8e-105">请求该报表的第一个用户必须等到所有处理全部完成后才能查看报表。</span><span class="sxs-lookup"><span data-stu-id="e3f8e-105">The first user who requests the report must wait for all processing to complete before viewing the report.</span></span> <span data-ttu-id="e3f8e-106">以后在缓存期间请求该报表的用户可以立即查看它，因为处理已经完成。</span><span class="sxs-lookup"><span data-stu-id="e3f8e-106">Subsequent users who request the report within the caching period can view it right away because processing has already occurred.</span></span>  
  
 <span data-ttu-id="e3f8e-107">可缓存的报表类型存在限制。</span><span class="sxs-lookup"><span data-stu-id="e3f8e-107">There are restrictions on the types of reports that you can cache.</span></span> <span data-ttu-id="e3f8e-108">例如，如果报表输出随着用户标识的变化而变化，或者使用请求该报表的用户的安全令牌检索数据，则无法缓存此报表。</span><span class="sxs-lookup"><span data-stu-id="e3f8e-108">For example, a report cannot be cached if report output varies based on the user identity or if data is retrieved using the security token of the user who requests the report.</span></span> <span data-ttu-id="e3f8e-109">有关详细信息，请参阅 [缓存报表 (SSRS)](caching-reports-ssrs.md)版本中预加载缓存的唯一方法。</span><span class="sxs-lookup"><span data-stu-id="e3f8e-109">For more information, see [Caching Reports &#40;SSRS&#41;](caching-reports-ssrs.md).</span></span>  
  
### <a name="to-schedule-the-expiration-of-a-cached-report"></a><span data-ttu-id="e3f8e-110">计划缓存报表的过期时间</span><span class="sxs-lookup"><span data-stu-id="e3f8e-110">To schedule the expiration of a cached report</span></span>  
  
1.  <span data-ttu-id="e3f8e-111">启动 [报表管理器（SSRS 本机模式）](../report-manager-ssrs-native-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="e3f8e-111">Start [Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md).</span></span>  
  
2.  <span data-ttu-id="e3f8e-112">在报表管理器中，导航到 **“内容”** 页。</span><span class="sxs-lookup"><span data-stu-id="e3f8e-112">In Report Manager, navigate to the **Contents** page.</span></span> <span data-ttu-id="e3f8e-113">导航到要设置缓存属性的报表，悬停在该项上，然后单击下拉箭头。</span><span class="sxs-lookup"><span data-stu-id="e3f8e-113">Navigate to the report for which you want to set caching properties, hover over the item, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="e3f8e-114">在下拉菜单中，单击 **“管理”** 。</span><span class="sxs-lookup"><span data-stu-id="e3f8e-114">In the drop-down menu, click **Manage**.</span></span>  
  
4.  <span data-ttu-id="e3f8e-115">在左框架中，单击 **“处理选项”** 。</span><span class="sxs-lookup"><span data-stu-id="e3f8e-115">In the left frame, click the **Processing Options**.</span></span>  
  
5.  <span data-ttu-id="e3f8e-116">在该页上，选择 **“始终用最新数据运行此报表”** 。</span><span class="sxs-lookup"><span data-stu-id="e3f8e-116">On the page, select **Always run this report with the most recent data**.</span></span>  
  
6.  <span data-ttu-id="e3f8e-117">选择以下两个缓存选项之一，并配置过期时间：</span><span class="sxs-lookup"><span data-stu-id="e3f8e-117">Select one of the following two cache options and configure expiration as follows:</span></span>  
  
    -   <span data-ttu-id="e3f8e-118">若要将缓存副本配置为在特定时间段后过期，请单击“缓存报表的临时副本。 **在数分钟之后使报表副本过期**。</span><span class="sxs-lookup"><span data-stu-id="e3f8e-118">To configure a cached copy to expire after a particular time period, click **Cache a temporary copy of the report. Expire copy of report after a number of minutes**.</span></span> <span data-ttu-id="e3f8e-119">键入报表过期所需的分钟数。</span><span class="sxs-lookup"><span data-stu-id="e3f8e-119">Type the number of minutes for report expiration.</span></span>  
  
    -   <span data-ttu-id="e3f8e-120">若要将缓存副本配置为按计划过期，请单击“缓存报表的临时副本”。 **按下列计划使报表副本过期。**</span><span class="sxs-lookup"><span data-stu-id="e3f8e-120">To configure a cached copy to expire on a schedule, click **Cache a temporary copy of the report. Expire copy of report on the following schedule.**</span></span> <span data-ttu-id="e3f8e-121">单击 **“配置”** ，或选择一个共享计划以控制报表过期时间。</span><span class="sxs-lookup"><span data-stu-id="e3f8e-121">Click **Configure**, or select a shared schedule to control report expiration</span></span>  
  
7.  <span data-ttu-id="e3f8e-122">单击“应用”  。</span><span class="sxs-lookup"><span data-stu-id="e3f8e-122">Click **Apply**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3f8e-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e3f8e-123">See Also</span></span>  
 <span data-ttu-id="e3f8e-124">[设置报表处理属性](set-report-processing-properties.md) </span><span class="sxs-lookup"><span data-stu-id="e3f8e-124">[Set Report Processing Properties](set-report-processing-properties.md) </span></span>  
 [<span data-ttu-id="e3f8e-125">缓存报表 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="e3f8e-125">Caching Reports &#40;SSRS&#41;</span></span>](caching-reports-ssrs.md)  
  
  
