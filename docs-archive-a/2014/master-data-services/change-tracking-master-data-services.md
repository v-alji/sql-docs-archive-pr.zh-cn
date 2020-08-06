---
title: 更改跟踪 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- change tracking [SQL Server]
ms.assetid: 5e879c65-0d38-454f-9a20-62a6e72c89f7
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 2d3b69057b02884f41a43aa9a009ab3db937ed25
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689938"
---
# <a name="change-tracking-master-data-services"></a><span data-ttu-id="276cf-102">更改跟踪 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="276cf-102">Change Tracking (Master Data Services)</span></span>
  <span data-ttu-id="276cf-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，您可以使用更改跟踪组在属性值发生更改时执行操作。</span><span class="sxs-lookup"><span data-stu-id="276cf-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], you can use change tracking groups to take action when an attribute value changes.</span></span> <span data-ttu-id="276cf-104">如果不知道新值是什么，但想要知道是否发生了任何更改，则使用更改跟踪。</span><span class="sxs-lookup"><span data-stu-id="276cf-104">Use change tracking when you don't know what the new value will be, but instead want to know if any change occurred.</span></span>  
  
## <a name="configuring-change-tracking"></a><span data-ttu-id="276cf-105">配置更改跟踪</span><span class="sxs-lookup"><span data-stu-id="276cf-105">Configuring Change Tracking</span></span>  
 <span data-ttu-id="276cf-106">若要配置更改跟踪，请向更改跟踪组添加属性。</span><span class="sxs-lookup"><span data-stu-id="276cf-106">To configure change tracking, you add an attribute to a change tracking group.</span></span> <span data-ttu-id="276cf-107">该组可以包含一个或多个属性。</span><span class="sxs-lookup"><span data-stu-id="276cf-107">The group can contain one or many attributes.</span></span> <span data-ttu-id="276cf-108">然后，创建业务规则以定义在该组中任何属性发生更改时执行的操作。</span><span class="sxs-lookup"><span data-stu-id="276cf-108">Then, you create a business rule to define the action that is taken when any of the attributes in the group change.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="276cf-109">更改跟踪业务规则认为临时（导入）数据将发生更改。</span><span class="sxs-lookup"><span data-stu-id="276cf-109">Change tracking business rules consider staged (imported) data to be changed.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="276cf-110">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="276cf-110">Related Tasks</span></span>  
  
|<span data-ttu-id="276cf-111">任务说明</span><span class="sxs-lookup"><span data-stu-id="276cf-111">Task Description</span></span>|<span data-ttu-id="276cf-112">主题</span><span class="sxs-lookup"><span data-stu-id="276cf-112">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="276cf-113">向更改跟踪组添加属性。</span><span class="sxs-lookup"><span data-stu-id="276cf-113">Add attributes to a change tracking group.</span></span>|[<span data-ttu-id="276cf-114">向更改跟踪组添加属性 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="276cf-114">Add Attributes to a Change Tracking Group &#40;Master Data Services&#41;</span></span>](add-attributes-to-a-change-tracking-group-master-data-services.md)|  
|<span data-ttu-id="276cf-115">创建业务规则以便基于属性更改启动操作。</span><span class="sxs-lookup"><span data-stu-id="276cf-115">Create a business rule that initiates actions based on attribute changes.</span></span>|[<span data-ttu-id="276cf-116">基于属性值更改启动操作 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="276cf-116">Initiate Actions Based on Attribute Value Changes &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/initiate-actions-based-on-attribute-value-changes-master-data-services.md)|  
  
## <a name="related-content"></a><span data-ttu-id="276cf-117">相关内容</span><span class="sxs-lookup"><span data-stu-id="276cf-117">Related Content</span></span>  
  
-   [<span data-ttu-id="276cf-118">验证 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="276cf-118">Validation &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/validation-master-data-services.md)  
  
-   [<span data-ttu-id="276cf-119">业务规则 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="276cf-119">Business Rules &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/business-rules-master-data-services.md)  
  
-   [<span data-ttu-id="276cf-120">属性 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="276cf-120">Attributes &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/attributes-master-data-services.md)  
  
  
