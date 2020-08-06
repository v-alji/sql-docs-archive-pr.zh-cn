---
title: 订阅服务器类型 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newpubwizard.subscribertypes.f1
ms.assetid: a70656cb-21c9-4489-be77-ccd396747e3b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4d356377dec1f5307fa136c94ea682c0824479a8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590734"
---
# <a name="subscriber-types"></a><span data-ttu-id="8bf8c-102">订阅服务器类型</span><span class="sxs-lookup"><span data-stu-id="8bf8c-102">Subscriber Types</span></span>
  <span data-ttu-id="8bf8c-103">进行合并发布时可以指定发布必须支持的订阅服务器的类型。</span><span class="sxs-lookup"><span data-stu-id="8bf8c-103">Merge replication allows you to specify the types of Subscribers that a publication must support.</span></span> <span data-ttu-id="8bf8c-104">选择订阅服务器类型将会设置“发布兼容级别  ”，该级别可确定发布能够使用哪些功能。</span><span class="sxs-lookup"><span data-stu-id="8bf8c-104">Selecting Subscriber types sets the *publication compatibility level*, which determines which features can be used by a publication.</span></span>  
  
 <span data-ttu-id="8bf8c-105">创建发布快照之后，可以在 **“发布属性”** 对话框的 **“常规”** 页上提高发布兼容级别（使其更为严格）；无法降低兼容级别。</span><span class="sxs-lookup"><span data-stu-id="8bf8c-105">After a publication snapshot is created, the publication compatibility level can be increased (made more restrictive) on the **General** page of the **Publication Properties** dialog box; the compatibility level cannot be decreased.</span></span>  
  
## <a name="options"></a><span data-ttu-id="8bf8c-106">选项</span><span class="sxs-lookup"><span data-stu-id="8bf8c-106">Options</span></span>  
 <span data-ttu-id="8bf8c-107">选择此发布必须支持的各个订阅服务器类型。</span><span class="sxs-lookup"><span data-stu-id="8bf8c-107">Select each Subscriber type that this publication must support.</span></span>  
  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
 <span data-ttu-id="8bf8c-108">该发布可使用所有功能。</span><span class="sxs-lookup"><span data-stu-id="8bf8c-108">The publication can use all features.</span></span>  
  
 [!INCLUDE[ssEW](../../includes/ssew-md.md)]  
 <span data-ttu-id="8bf8c-109">该发布要求快照文件采用字符格式（由快照代理自动处理）。</span><span class="sxs-lookup"><span data-stu-id="8bf8c-109">The publication requires snapshot files to be in character format (this is handled automatically by the Snapshot Agent).</span></span> [!INCLUDE[ssEW](../../includes/ssew-md.md)] <span data-ttu-id="8bf8c-110">还具有许多与兼容级别无关的限制。</span><span class="sxs-lookup"><span data-stu-id="8bf8c-110">also has a number of restrictions not related to compatibility level.</span></span>  
  
 <span data-ttu-id="8bf8c-111">如果选择了此选项，将为该发布启用 Web 同步选项。</span><span class="sxs-lookup"><span data-stu-id="8bf8c-111">If this option is selected, the Web synchronization option is enabled for the publication.</span></span> <span data-ttu-id="8bf8c-112">有关 Web 同步的详细信息，请参阅 [Web Synchronization for Merge Replication](web-synchronization-for-merge-replication.md)。</span><span class="sxs-lookup"><span data-stu-id="8bf8c-112">For more information about Web synchronization, see [Web Synchronization for Merge Replication](web-synchronization-for-merge-replication.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8bf8c-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8bf8c-113">See Also</span></span>  
 <span data-ttu-id="8bf8c-114">[发布数据和数据库对象](publish/publish-data-and-database-objects.md) </span><span class="sxs-lookup"><span data-stu-id="8bf8c-114">[Publish Data and Database Objects](publish/publish-data-and-database-objects.md) </span></span>  
 <span data-ttu-id="8bf8c-115">[Create a Publication](publish/create-a-publication.md) </span><span class="sxs-lookup"><span data-stu-id="8bf8c-115">[Create a Publication](publish/create-a-publication.md) </span></span>  
 [<span data-ttu-id="8bf8c-116">查看和修改分发服务器和发布服务器属性</span><span class="sxs-lookup"><span data-stu-id="8bf8c-116">View and Modify Distributor and Publisher Properties</span></span>](view-and-modify-distributor-and-publisher-properties.md)   

  
