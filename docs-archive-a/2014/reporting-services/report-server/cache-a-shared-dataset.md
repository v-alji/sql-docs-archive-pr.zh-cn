---
title: 缓存共享数据集 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: c2d8c81a-da1e-4a8a-9845-fff9a0903d24
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d4757d82425368efcb6a0a555c6cfe1deacf48c0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588307"
---
# <a name="cache-a-shared-dataset"></a><span data-ttu-id="a07f1-102">如何缓存一个共享数据集</span><span class="sxs-lookup"><span data-stu-id="a07f1-102">Cache a Shared Dataset</span></span>
  <span data-ttu-id="a07f1-103">提高性能的一种方法是配置共享数据集的缓存属性。</span><span class="sxs-lookup"><span data-stu-id="a07f1-103">One way to improve performance is to configure caching properties for a shared dataset.</span></span> <span data-ttu-id="a07f1-104">缓存共享数据集后，会在指定的一段时间内保存查询结果。</span><span class="sxs-lookup"><span data-stu-id="a07f1-104">When a shared dataset is cached, a copy of the query results is saved for a specified period of time.</span></span> <span data-ttu-id="a07f1-105">第一个向使用该共享数据集的报表发出请求的用户必须等到查询结果和所有处理全部完成后才能查看报表。</span><span class="sxs-lookup"><span data-stu-id="a07f1-105">The first user who requests a report that uses the shared dataset must wait for the query results and all processing to complete before viewing the report.</span></span> <span data-ttu-id="a07f1-106">以后在缓存期间请求该报表的用户将会体验到性能改进，因为查询和处理已经完成。</span><span class="sxs-lookup"><span data-stu-id="a07f1-106">Subsequent users who request the report within the caching period will experience improved performance because the query and processing has already occurred.</span></span> <span data-ttu-id="a07f1-107">还可以指定运行查询的缓存刷新计划，并在指定的缓存过期时间之前一直缓存查询结果。</span><span class="sxs-lookup"><span data-stu-id="a07f1-107">You can also specify a cache refresh plan to run the query and cache the results until the specified cache expiration.</span></span>  
  
 <span data-ttu-id="a07f1-108">运行基于共享数据集或缓存刷新计划的报表的用户创建查询缓存，并且在这两种情况下，缓存是否可用都取决于缓存过期时间选项。</span><span class="sxs-lookup"><span data-stu-id="a07f1-108">Users running reports based on a shared dataset or cache refresh plans create the query cache and in both cases, the cache is available based on the cache expiration options.</span></span>  
  
 <span data-ttu-id="a07f1-109">可缓存的共享数据集类型存在限制。</span><span class="sxs-lookup"><span data-stu-id="a07f1-109">There are restrictions on the types of shared datasets that you can cache.</span></span> <span data-ttu-id="a07f1-110">例如，如果数据根据用户身份而有所不同，或者如果数据是使用请求报表的用户的安全令牌进行检索的，则无法缓存查询结果。</span><span class="sxs-lookup"><span data-stu-id="a07f1-110">For example, the query results cannot be cached if the data varies based on the user identity or if data is retrieved using the security token of the user who requests the report.</span></span> <span data-ttu-id="a07f1-111">有关详细信息，请参阅[缓存共享数据集 (SSRS)](cache-shared-datasets-ssrs.md) 和 [缓存报表 (SSRS)](caching-reports-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="a07f1-111">For more information, see [Cache Shared Datasets &#40;SSRS&#41;](cache-shared-datasets-ssrs.md) and [Caching Reports &#40;SSRS&#41;](caching-reports-ssrs.md).</span></span>  
  
### <a name="to-schedule-the-expiration-of-a-cached-report"></a><span data-ttu-id="a07f1-112">计划缓存报表的过期时间</span><span class="sxs-lookup"><span data-stu-id="a07f1-112">To schedule the expiration of a cached report</span></span>  
  
1.  <span data-ttu-id="a07f1-113">启动 [报表管理器（SSRS 本机模式）](../report-manager-ssrs-native-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="a07f1-113">Start [Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md).</span></span>  
  
2.  <span data-ttu-id="a07f1-114">在报表管理器中，导航到要为其设置缓存属性的共享数据集，将鼠标悬停在该项上，然后单击下拉箭头。</span><span class="sxs-lookup"><span data-stu-id="a07f1-114">In Report Manager, navigate to the shared dataset for which you want to set caching properties, hover over the item, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="a07f1-115">在下拉菜单中，单击 **“管理”** 。</span><span class="sxs-lookup"><span data-stu-id="a07f1-115">In the drop-down menu, click **Manage**.</span></span>  
  
4.  <span data-ttu-id="a07f1-116">在左框架中，单击 **“缓存”** 。</span><span class="sxs-lookup"><span data-stu-id="a07f1-116">In the left frame, click **Caching**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a07f1-117">如果看到错误 **“未存储用于运行共享数据集的凭据”** ，则缓存共享数据集选项将被禁用。</span><span class="sxs-lookup"><span data-stu-id="a07f1-117">If you see the error **Credentials used to run the shared dataset are not stored**, the cache shared dataset option will be disabled.</span></span> <span data-ttu-id="a07f1-118">您需要修改数据源以存储凭据，或修改共享数据集以使用其他确实存储了凭据的数据源。</span><span class="sxs-lookup"><span data-stu-id="a07f1-118">You need modify the data source to store credentials or modify the shared dataset to use a different data source that does store credentials.</span></span>  
  
5.  <span data-ttu-id="a07f1-119">选择 **“缓存共享数据集”** 。</span><span class="sxs-lookup"><span data-stu-id="a07f1-119">Select **Cache share dataset**.</span></span>  
  
6.  <span data-ttu-id="a07f1-120">选择缓存在 30 分钟后过期的选项。</span><span class="sxs-lookup"><span data-stu-id="a07f1-120">Select the option to expire the cache after 30 minutes.</span></span> <span data-ttu-id="a07f1-121">还可以选择缓存按指定的计划过期。</span><span class="sxs-lookup"><span data-stu-id="a07f1-121">You can also choose for the cache to expire on a specified schedule.</span></span>  
  
7.  <span data-ttu-id="a07f1-122">单击“应用”  。</span><span class="sxs-lookup"><span data-stu-id="a07f1-122">Click **Apply**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a07f1-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a07f1-123">See Also</span></span>  
 [<span data-ttu-id="a07f1-124">管理共享数据集</span><span class="sxs-lookup"><span data-stu-id="a07f1-124">Manage Shared Datasets</span></span>](../report-data/manage-shared-datasets.md)  
  
  
