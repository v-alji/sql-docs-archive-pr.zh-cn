---
title: 任务 2 (可选) ：使用主数据管理器创建 MDS 订阅视图 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: f3da8219-e0cb-4848-95ca-285a76ec1ba9
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 998436734ba5c3cf09cfe88f266a0908c0550abc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691373"
---
# <a name="task-2-optional-creating-a-mds-subscription-view-using-master-data-manager"></a><span data-ttu-id="cd8ee-102">任务 2（可选）：使用主数据管理器创建 MDS 订阅视图</span><span class="sxs-lookup"><span data-stu-id="cd8ee-102">Task 2 (Optional): Creating a MDS Subscription View using Master Data Manager</span></span>
  <span data-ttu-id="cd8ee-103">在此任务中，您将创建一个订阅视图，以便向其他应用程序公开**供应商**模型中的**供应商**实体。</span><span class="sxs-lookup"><span data-stu-id="cd8ee-103">In this task, you create a subscription view to expose the **Supplier** entity in the **Suppliers** model to other applications.</span></span> <span data-ttu-id="cd8ee-104">在当前版本的教程中，您将不使用此视图。</span><span class="sxs-lookup"><span data-stu-id="cd8ee-104">You do not consume this view in the current version of the tutorial.</span></span>  
  
1.  <span data-ttu-id="cd8ee-105">**Master Data Manager** `http://localhost/MDS` 单击顶部的**SQL Server 2012 Master Data Services** ，切换到主数据管理器 () 的主页。</span><span class="sxs-lookup"><span data-stu-id="cd8ee-105">Switch to the main page of **Master Data Manager** (`http://localhost/MDS`) by clicking **SQL Server 2012 Master Data Services** at the top.</span></span>  
  
2.  <span data-ttu-id="cd8ee-106">单击 "**集成管理**"。</span><span class="sxs-lookup"><span data-stu-id="cd8ee-106">Click **Integration Management**.</span></span>  
  
3.  <span data-ttu-id="cd8ee-107">单击菜单栏上的 "**创建视图**"。</span><span class="sxs-lookup"><span data-stu-id="cd8ee-107">Click **Create Views** on the menu bar.</span></span>  
  
     <span data-ttu-id="cd8ee-108">![“添加新的订阅视图”按钮](../../2014/tutorials/media/et-creatingamdssubscriptionviewusingmdm-01.jpg "“添加新的订阅视图”按钮")</span><span class="sxs-lookup"><span data-stu-id="cd8ee-108">![Add a New Subscription View Button](../../2014/tutorials/media/et-creatingamdssubscriptionviewusingmdm-01.jpg "Add a New Subscription View Button")</span></span>  
  
4.  <span data-ttu-id="cd8ee-109">单击工具栏上的 " \*\*+ (加) \*\* " 图标以创建订阅视图。</span><span class="sxs-lookup"><span data-stu-id="cd8ee-109">Click **+ (Plus)** icon on the toolbar to create a subscription view.</span></span>  
  
5.  <span data-ttu-id="cd8ee-110">在 "**创建订阅视图**" 窗格中，键入 "**供应商**" 作为**订阅视图名称**。</span><span class="sxs-lookup"><span data-stu-id="cd8ee-110">In the **Create Subscription View** pane, type **Suppliers** for **Subscription view name**.</span></span>  
  
6.  <span data-ttu-id="cd8ee-111">选择**模型**的**供应商**。</span><span class="sxs-lookup"><span data-stu-id="cd8ee-111">Select **Suppliers** for **Model**.</span></span>  
  
7.  <span data-ttu-id="cd8ee-112">为 "**版本**" 选择**VERSION_1** 。</span><span class="sxs-lookup"><span data-stu-id="cd8ee-112">Select **VERSION_1** for **Version**.</span></span>  
  
8.  <span data-ttu-id="cd8ee-113">选择**实体**的**供应商**。</span><span class="sxs-lookup"><span data-stu-id="cd8ee-113">Select **Supplier** for **Entity**.</span></span>  
  
9. <span data-ttu-id="cd8ee-114">选择**格式**的**叶成员**。</span><span class="sxs-lookup"><span data-stu-id="cd8ee-114">Select **Leaf members** for **Format**.</span></span>  
  
     <span data-ttu-id="cd8ee-115">![“保存订阅视图”按钮](../../2014/tutorials/media/et-creatingamdssubscriptionviewusingmdm-02.jpg "“保存订阅视图”按钮")</span><span class="sxs-lookup"><span data-stu-id="cd8ee-115">![Save Subscription View Button](../../2014/tutorials/media/et-creatingamdssubscriptionviewusingmdm-02.jpg "Save Subscription View Button")</span></span>  
  
10. <span data-ttu-id="cd8ee-116">单击工具栏上的 "**保存**" 以保存订阅视图。</span><span class="sxs-lookup"><span data-stu-id="cd8ee-116">Click **Save** on the toolbar to save the subscription view.</span></span> <span data-ttu-id="cd8ee-117">此操作在 SQL Server 名为 "**供应商**" 中创建视图。</span><span class="sxs-lookup"><span data-stu-id="cd8ee-117">This action creates a view in SQL Server named **Suppliers**.</span></span> <span data-ttu-id="cd8ee-118">您可以使用 SQL Server Management Studio (SSMS) 确认这一点。</span><span class="sxs-lookup"><span data-stu-id="cd8ee-118">You can verify this using SQL Server Management Studio (SSMS).</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="cd8ee-119">下一步</span><span class="sxs-lookup"><span data-stu-id="cd8ee-119">Next Step</span></span>  
 [<span data-ttu-id="cd8ee-120">任务 3 &#40;可选&#41;：查看订阅视图</span><span class="sxs-lookup"><span data-stu-id="cd8ee-120">Task 3 &#40;Optional&#41;: Reviewing the Subscription Views</span></span>](task-3-optional-reviewing-the-subscription-views.md)  
  
  
