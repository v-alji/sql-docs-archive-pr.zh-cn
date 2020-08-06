---
title: 导出数据 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- exporting data [Master Data Services]
- subscription views [Master Data Services]
- subscription views [Master Data Services], about subscription views
ms.assetid: 8b74409a-ea70-45f8-84c7-da6905e4901a
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: edae5b996c25a1b6053231ed2f69ef511b9fbfa6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586775"
---
# <a name="exporting-data-master-data-services"></a><span data-ttu-id="82078-102">导出数据 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="82078-102">Exporting Data (Master Data Services)</span></span>
  <span data-ttu-id="82078-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 您可以通过创建订阅视图将  数据导出到订阅系统。</span><span class="sxs-lookup"><span data-stu-id="82078-103">You can export [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] data to subscribing systems by creating subscriptions views.</span></span> <span data-ttu-id="82078-104">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 然后，任何订阅系统都可以在  数据库中查看发布的数据。</span><span class="sxs-lookup"><span data-stu-id="82078-104">Any subscribing system can then view the published data in the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database.</span></span> <span data-ttu-id="82078-105">有关视图的详细信息，请参阅[视图](../relational-databases/views/views.md)。</span><span class="sxs-lookup"><span data-stu-id="82078-105">For more information about views, see [Views](../relational-databases/views/views.md).</span></span>  
  
## <a name="subscription-view-formats"></a><span data-ttu-id="82078-106">订阅视图格式</span><span class="sxs-lookup"><span data-stu-id="82078-106">Subscription View Formats</span></span>  
 <span data-ttu-id="82078-107">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 中创建某一视图时，从  提供的一组标准视图格式中进行选择。</span><span class="sxs-lookup"><span data-stu-id="82078-107">When you create a view in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], you choose from a set of standard view formats that [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] provides.</span></span> <span data-ttu-id="82078-108">可以使用这些格式创建显示以下内容的视图：</span><span class="sxs-lookup"><span data-stu-id="82078-108">You can use these formats to create views that show:</span></span>  
  
-   <span data-ttu-id="82078-109">所有叶成员及其属性。</span><span class="sxs-lookup"><span data-stu-id="82078-109">All leaf members and their attributes.</span></span>  
  
-   <span data-ttu-id="82078-110">所有合并成员及其属性。</span><span class="sxs-lookup"><span data-stu-id="82078-110">All consolidated members and their attributes.</span></span>  
  
-   <span data-ttu-id="82078-111">所有集合及其属性。</span><span class="sxs-lookup"><span data-stu-id="82078-111">All collections and their attributes.</span></span>  
  
-   <span data-ttu-id="82078-112">显式添加到集合的成员。</span><span class="sxs-lookup"><span data-stu-id="82078-112">The members explicitly added to a collection.</span></span>  
  
-   <span data-ttu-id="82078-113">派生层次结构中的成员，采用父子或级别格式。</span><span class="sxs-lookup"><span data-stu-id="82078-113">The members in a derived hierarchy, in either a parent child or level format.</span></span>  
  
-   <span data-ttu-id="82078-114">某一实体的所有显式层次结构中的成员，采用父子或级别格式。</span><span class="sxs-lookup"><span data-stu-id="82078-114">The members in all explicit hierarchies for an entity, in either a parent child or level format.</span></span>  
  
## <a name="subscription-views-can-become-out-of-date"></a><span data-ttu-id="82078-115">订阅视图可能会过期</span><span class="sxs-lookup"><span data-stu-id="82078-115">Subscription Views Can Become Out-of-Date</span></span>  
 <span data-ttu-id="82078-116">在您创建针对某一实体或层次结构的订阅视图后，对关联的模型对象的更改不能自动反映在视图中。</span><span class="sxs-lookup"><span data-stu-id="82078-116">After you create a subscription view for an entity or hierarchy, changes to the associated model objects are not automatically reflected in the view.</span></span> <span data-ttu-id="82078-117">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 您可能需要在中重新生成一个订阅视图，以便反映对模型对象的更改。</span><span class="sxs-lookup"><span data-stu-id="82078-117">You might need to regenerate a subscription view in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] to reflect changes to model objects.</span></span> <span data-ttu-id="82078-118">在对象模型更改时， **“导出”** 页上的 **“已更改”** 列将更新为 **True** 。</span><span class="sxs-lookup"><span data-stu-id="82078-118">The **Changed** column on the **Export** page is updated to **True** when model objects change.</span></span> <span data-ttu-id="82078-119">**True** 指示您应该编辑订阅视图并且保存它，这将重新生成该视图。</span><span class="sxs-lookup"><span data-stu-id="82078-119">**True** indicates that you should edit the subscription view and save it, which regenerates the view.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="82078-120">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="82078-120">Related Tasks</span></span>  
  
|<span data-ttu-id="82078-121">任务说明</span><span class="sxs-lookup"><span data-stu-id="82078-121">Task Description</span></span>|<span data-ttu-id="82078-122">主题</span><span class="sxs-lookup"><span data-stu-id="82078-122">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="82078-123">创建主数据的订阅视图。</span><span class="sxs-lookup"><span data-stu-id="82078-123">Create a subscription view of your master data.</span></span>|[<span data-ttu-id="82078-124">&#40;Master Data Services 创建订阅视图&#41;</span><span class="sxs-lookup"><span data-stu-id="82078-124">Create a Subscription View &#40;Master Data Services&#41;</span></span>](create-a-subscription-view-to-export-data-master-data-services.md)|  
|<span data-ttu-id="82078-125">删除现有订阅视图。</span><span class="sxs-lookup"><span data-stu-id="82078-125">Delete an existing subscription view.</span></span>|[<span data-ttu-id="82078-126">删除订阅视图 &#40;Master Data Services&#41; </span><span class="sxs-lookup"><span data-stu-id="82078-126">Delete a Subscription View &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/delete-a-subscription-view-master-data-services.md)|  
  
## <a name="related-content"></a><span data-ttu-id="82078-127">相关内容</span><span class="sxs-lookup"><span data-stu-id="82078-127">Related Content</span></span>  
  
-   [<span data-ttu-id="82078-128">订阅视图格式 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="82078-128">Subscription View Formats &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/subscription-view-formats-master-data-services.md)  
  
-   [<span data-ttu-id="82078-129">视图</span><span class="sxs-lookup"><span data-stu-id="82078-129">Views</span></span>](../relational-databases/views/views.md)  
  
  
