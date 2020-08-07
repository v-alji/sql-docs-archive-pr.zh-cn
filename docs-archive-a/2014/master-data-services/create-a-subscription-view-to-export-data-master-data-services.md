---
title: 创建订阅视图 (Master Data Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- subscription views [Master Data Services], creating
- creating subscription views [Master Data Services]
ms.assetid: a5e28961-af16-414a-9845-d2e06aac5214
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: e5e2b901e56d75e97a444fd2858ef95872f3b766
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588590"
---
# <a name="create-a-subscription-view-master-data-services"></a><span data-ttu-id="29ece-102">创建订阅视图 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="29ece-102">Create a Subscription View (Master Data Services)</span></span>
  <span data-ttu-id="29ece-103">如果要在数据库中创建 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 供订阅系统使用的数据视图，请创建订阅视图。</span><span class="sxs-lookup"><span data-stu-id="29ece-103">Create a subscription view when you want to create a view of your data in the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database for use by subscribing systems.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="29ece-104">必备条件</span><span class="sxs-lookup"><span data-stu-id="29ece-104">Prerequisites</span></span>  
 <span data-ttu-id="29ece-105">若要执行此过程：</span><span class="sxs-lookup"><span data-stu-id="29ece-105">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="29ece-106">您必须有权访问 **“集成管理”** 功能区域。</span><span class="sxs-lookup"><span data-stu-id="29ece-106">You must have permission to access the **Integration Management** functional area.</span></span>  
  
-   <span data-ttu-id="29ece-107">您必须是模型管理员。</span><span class="sxs-lookup"><span data-stu-id="29ece-107">You must be a model administrator.</span></span> <span data-ttu-id="29ece-108">有关详细信息，请参阅[管理员 &#40;Master Data Services&#41;](administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="29ece-108">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
### <a name="to-create-a-subscription-view"></a><span data-ttu-id="29ece-109">创建订阅视图</span><span class="sxs-lookup"><span data-stu-id="29ece-109">To create a subscription view</span></span>  
  
1.  <span data-ttu-id="29ece-110">在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]中，单击 **“集成管理”**。</span><span class="sxs-lookup"><span data-stu-id="29ece-110">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **Integration Management**.</span></span>  
  
2.  <span data-ttu-id="29ece-111">在菜单栏中，单击 **“创建视图”**。</span><span class="sxs-lookup"><span data-stu-id="29ece-111">From the menu bar, click **Create Views**.</span></span>  
  
3.  <span data-ttu-id="29ece-112">在 "**订阅视图**" 页上，单击 "**添加订阅视图**"。</span><span class="sxs-lookup"><span data-stu-id="29ece-112">On the **Subscription Views** page, click **Add subscription view**.</span></span>  
  
4.  <span data-ttu-id="29ece-113">在 "**创建订阅视图**" 窗格的 "**订阅视图名称**" 框中，键入视图的名称。</span><span class="sxs-lookup"><span data-stu-id="29ece-113">In the **Create Subscription View** pane, in the **Subscription view name** box, type a name for the view.</span></span>  
  
5.  <span data-ttu-id="29ece-114">从 **“模型”** 列表中，选择某一模型。</span><span class="sxs-lookup"><span data-stu-id="29ece-114">From the **Model** list, select a model.</span></span>  
  
6.  <span data-ttu-id="29ece-115">选择 "**版本**" 或 "**版本标志**" 选项，然后从相应的列表中进行选择。</span><span class="sxs-lookup"><span data-stu-id="29ece-115">Select either the **Version** or **Version Flag** option, and then select from the corresponding list.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="29ece-116">基于版本标志创建订阅视图。</span><span class="sxs-lookup"><span data-stu-id="29ece-116">Create a subscription view based on a version flag.</span></span> <span data-ttu-id="29ece-117">当锁定版本时，可以将该标志重新分配给打开的版本，而无需更新订阅视图。</span><span class="sxs-lookup"><span data-stu-id="29ece-117">When you lock a version, you can reassign the flag to an open version without updating the subscription view.</span></span>  
  
7.  <span data-ttu-id="29ece-118">选择 "**实体**" 或 "**派生层次结构**" 选项，然后从相应的列表中进行选择。</span><span class="sxs-lookup"><span data-stu-id="29ece-118">Select either the **Entity** or **Derived hierarchy** option, and then select from the corresponding list.</span></span>  
  
8.  <span data-ttu-id="29ece-119">从 **“格式”** 列表中，选择订阅视图格式。</span><span class="sxs-lookup"><span data-stu-id="29ece-119">From the **Format** list, select a subscription view format.</span></span>  
  
9. <span data-ttu-id="29ece-120">如果您从 **“格式”** 列表中选择 **“显式级别”** 或 **“派生级别”** ，则键入要包括在视图中的层次结构中的级别数。</span><span class="sxs-lookup"><span data-stu-id="29ece-120">If you chose **Explicit levels** or **Derived levels** from the **Format** list, type the number of levels in the hierarchy to include in the view.</span></span>  
  
10. <span data-ttu-id="29ece-121">单击 **“保存”** 。</span><span class="sxs-lookup"><span data-stu-id="29ece-121">Click **Save**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29ece-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="29ece-122">See Also</span></span>  
 <span data-ttu-id="29ece-123">[将数据导出 &#40;Master Data Services&#41;](overview-exporting-data-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="29ece-123">[Exporting Data &#40;Master Data Services&#41;](overview-exporting-data-master-data-services.md) </span></span>  
 <span data-ttu-id="29ece-124">[&#40;Master Data Services 中删除订阅视图&#41;](delete-a-subscription-view-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="29ece-124">[Delete a Subscription View &#40;Master Data Services&#41;](delete-a-subscription-view-master-data-services.md) </span></span>  
 [<span data-ttu-id="29ece-125">创建版本标志 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="29ece-125">Create a Version Flag &#40;Master Data Services&#41;</span></span>](create-a-version-flag-master-data-services.md)  
  
  
