---
title: 缓存页，报表管理器)  (共享数据集 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: eac372e9-d2a1-48a8-bbe5-09d101df16ea
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 62d899964911a6f2d35e59d49d925ff80013af42
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586509"
---
# <a name="caching-page-shared-datasets-report-manager"></a><span data-ttu-id="1ab63-102">共享数据集的“缓存”页（报表管理器）</span><span class="sxs-lookup"><span data-stu-id="1ab63-102">Caching Page, Shared Datasets (Report Manager)</span></span>
  <span data-ttu-id="1ab63-103">使用“缓存”属性页可以设置共享数据集的缓存选项。</span><span class="sxs-lookup"><span data-stu-id="1ab63-103">Use the Caching properties page to set the cache options for a shared dataset.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1ab63-104">并非在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]的每个版本中均提供此功能。</span><span class="sxs-lookup"><span data-stu-id="1ab63-104">This feature is not available in every edition of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="1ab63-105">有关各个版本支持的功能列表 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ，请参阅 SQL Server 2014 的各个[版本支持的功能](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)。</span><span class="sxs-lookup"><span data-stu-id="1ab63-105">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="1ab63-106">导航</span><span class="sxs-lookup"><span data-stu-id="1ab63-106">Navigation</span></span>  
 <span data-ttu-id="1ab63-107">使用以下过程导航到用户界面中的这一位置。</span><span class="sxs-lookup"><span data-stu-id="1ab63-107">Use the following procedure to navigate to this location in the user interface.</span></span>  
  
### <a name="to-open-the-caching-properties-page-for-a-shared-dataset"></a><span data-ttu-id="1ab63-108">打开共享数据集的“缓存”属性页</span><span class="sxs-lookup"><span data-stu-id="1ab63-108">To open the Caching properties page for a shared dataset</span></span>  
  
1.  <span data-ttu-id="1ab63-109">打开报表管理器，找到您要配置共享数据集属性的报表。</span><span class="sxs-lookup"><span data-stu-id="1ab63-109">Open Report Manager, and locate the report for which you want to configure shared dataset properties.</span></span>  
  
2.  <span data-ttu-id="1ab63-110">指向该共享数据集，然后单击下拉箭头。</span><span class="sxs-lookup"><span data-stu-id="1ab63-110">Point to the shared dataset, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="1ab63-111">在下拉列表中，单击 **“管理”**。</span><span class="sxs-lookup"><span data-stu-id="1ab63-111">In the drop-down list, click **Manage**.</span></span> <span data-ttu-id="1ab63-112">这会打开该报表的“常规”属性页。</span><span class="sxs-lookup"><span data-stu-id="1ab63-112">The General properties page for the report opens.</span></span>  
  
4.  <span data-ttu-id="1ab63-113">单击 **“缓存”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="1ab63-113">Click the **Caching** tab.</span></span>  
  
## <a name="options"></a><span data-ttu-id="1ab63-114">选项</span><span class="sxs-lookup"><span data-stu-id="1ab63-114">Options</span></span>  
 <span data-ttu-id="1ab63-115">**缓存共享数据集**</span><span class="sxs-lookup"><span data-stu-id="1ab63-115">**Cache shared dataset**</span></span>  
 <span data-ttu-id="1ab63-116">用户首次打开使用此共享数据集的报表时，在缓存中放置数据的临时副本。</span><span class="sxs-lookup"><span data-stu-id="1ab63-116">Places a temporary copy of the data in a cache when a user first opens a report that uses this shared dataset.</span></span> <span data-ttu-id="1ab63-117">以后在缓存期内运行报表的用户将收到数据的缓存副本。</span><span class="sxs-lookup"><span data-stu-id="1ab63-117">Subsequent users who run the report within the caching period receive the cached copy of the data.</span></span> <span data-ttu-id="1ab63-118">由于将从缓存中返回数据（而不是重新运行数据集查询），因此进行缓存通常会提高性能。</span><span class="sxs-lookup"><span data-stu-id="1ab63-118">Caching usually improves performance because the data is returned from the cache instead of running the dataset query again.</span></span>  
  
 <span data-ttu-id="1ab63-119">**缓存在此分钟数后到期**</span><span class="sxs-lookup"><span data-stu-id="1ab63-119">**Expire the cache after a number of minutes**</span></span>  
 <span data-ttu-id="1ab63-120">指定要保存数据缓存副本的分钟数。</span><span class="sxs-lookup"><span data-stu-id="1ab63-120">Specify the number of minutes to save the cached copy of the data.</span></span> <span data-ttu-id="1ab63-121">临时副本一到期，就不会再从缓存中返回数据。</span><span class="sxs-lookup"><span data-stu-id="1ab63-121">As soon as a temporary copy expires, the data is no longer returned from the cache.</span></span> <span data-ttu-id="1ab63-122">下次用户打开使用此共享数据集的报表时，将运行数据集查询，之后报表服务器将刷新后的数据副本存入缓存。</span><span class="sxs-lookup"><span data-stu-id="1ab63-122">The next time a user opens a report that uses this shared dataset, the dataset query runs and the report server places a copy of the refreshed data back in the cache.</span></span>  
  
 <span data-ttu-id="1ab63-123">**缓存根据以下计划到期**</span><span class="sxs-lookup"><span data-stu-id="1ab63-123">**Expire the cache on the following schedule**</span></span>  
 <span data-ttu-id="1ab63-124">预设缓存的数据不再有效并且从缓存中删除的时间。</span><span class="sxs-lookup"><span data-stu-id="1ab63-124">Schedule the time when the cached data is no longer valid and is removed from the cache.</span></span> <span data-ttu-id="1ab63-125">计划可以是共享计划，也可以是仅适用于当前共享数据集的特定计划。</span><span class="sxs-lookup"><span data-stu-id="1ab63-125">The schedule can be a shared schedule or one that is specific for only the current shared dataset.</span></span>  
  
 <span data-ttu-id="1ab63-126">**数据集特定计划**</span><span class="sxs-lookup"><span data-stu-id="1ab63-126">**Dataset-specific schedule**</span></span>  
 <span data-ttu-id="1ab63-127">指定仅用于此数据集的计划。</span><span class="sxs-lookup"><span data-stu-id="1ab63-127">Specify a schedule that is used only by this dataset.</span></span>  
  
 <span data-ttu-id="1ab63-128">**共享计划**</span><span class="sxs-lookup"><span data-stu-id="1ab63-128">**Shared schedule**</span></span>  
 <span data-ttu-id="1ab63-129">指定在报表、订阅和其他共享数据集之间共享的计划。</span><span class="sxs-lookup"><span data-stu-id="1ab63-129">Specify a schedule that is shared among reports, subscriptions, and other shared datasets.</span></span>  
  
 <span data-ttu-id="1ab63-130">**应用**</span><span class="sxs-lookup"><span data-stu-id="1ab63-130">**Apply**</span></span>  
 <span data-ttu-id="1ab63-131">保存所做更改。</span><span class="sxs-lookup"><span data-stu-id="1ab63-131">Save your changes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ab63-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1ab63-132">See Also</span></span>  
 <span data-ttu-id="1ab63-133">[报表管理器（SSRS 本机模式）](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="1ab63-133">[Report Manager  &#40;SSRS Native Mode&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="1ab63-134">[报表管理器 F1 帮助](../../2014/reporting-services/report-manager-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="1ab63-134">[Report Manager F1 Help](../../2014/reporting-services/report-manager-f1-help.md) </span></span>  
 <span data-ttu-id="1ab63-135">[&#40;SSRS&#41;缓存共享数据集](report-server/cache-shared-datasets-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="1ab63-135">[Cache Shared Datasets &#40;SSRS&#41;](report-server/cache-shared-datasets-ssrs.md) </span></span>  
 [<span data-ttu-id="1ab63-136">计划</span><span class="sxs-lookup"><span data-stu-id="1ab63-136">Schedules</span></span>](subscriptions/schedules.md)  
  
  
