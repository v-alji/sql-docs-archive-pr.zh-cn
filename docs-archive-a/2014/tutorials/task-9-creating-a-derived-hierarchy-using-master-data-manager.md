---
title: 任务9：使用主数据管理器创建派生层次结构 |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 3bd2ec05-933f-4947-b1fe-c9226961eb7d
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 5c85750e4556722c6e6a5edbccb4a3c82c119a74
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694177"
---
# <a name="task-9-creating-a-derived-hierarchy-using-master-data-manager"></a><span data-ttu-id="7ed82-102">任务 9：使用主数据管理器创建派生层次结构</span><span class="sxs-lookup"><span data-stu-id="7ed82-102">Task 9: Creating a Derived Hierarchy using Master Data Manager</span></span>
  <span data-ttu-id="7ed82-103">在本任务中，您将使用主数据管理器创建一个派生层次结构。</span><span class="sxs-lookup"><span data-stu-id="7ed82-103">In this task, you create a derived hierarchy by using Master Data Manager.</span></span> <span data-ttu-id="7ed82-104">此派生层次结构从**供应商**和**状态**实体之间的基于域的属性关系中派生。</span><span class="sxs-lookup"><span data-stu-id="7ed82-104">This derived hierarchy is derived from the domain-based attribute relationships between the **Supplier** and **State** entities.</span></span>  
  
1.  <span data-ttu-id="7ed82-105">单击页面顶部**SQL Server 2012 Master Data Services** ，切换到**主数据管理器**的主页。</span><span class="sxs-lookup"><span data-stu-id="7ed82-105">Switch to the main page of **Master Data Manager** by clicking **SQL Server 2012 Master Data Services** at the top of the page.</span></span>  
  
2.  <span data-ttu-id="7ed82-106">单击 "**管理任务**" 部分中的 "**系统管理**"。</span><span class="sxs-lookup"><span data-stu-id="7ed82-106">Click **System Administration** in the **Administrative Tasks** section.</span></span>  
  
3.  <span data-ttu-id="7ed82-107">将鼠标悬停在菜单栏上的 "**管理**" 上，然后单击 "**派生层次结构**"。</span><span class="sxs-lookup"><span data-stu-id="7ed82-107">Hover the mouse over **Manage** on the menu bar, and click **Derived Hierarchies**.</span></span>  
  
     <span data-ttu-id="7ed82-108">![“管理”菜单 - 已选择派生层次结构](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-01.jpg "“管理”菜单 - 已选择派生层次结构")</span><span class="sxs-lookup"><span data-stu-id="7ed82-108">![Manage Menu - Derived Hierarchies Selected](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-01.jpg "Manage Menu - Derived Hierarchies Selected")</span></span>  
  
4.  <span data-ttu-id="7ed82-109">单击工具栏上的 "\*\*添加派生层次结构" ("+) \*\* " 按钮。</span><span class="sxs-lookup"><span data-stu-id="7ed82-109">Click **Add Derived Hierarchy (+)** button on the toolbar.</span></span>  
  
     <span data-ttu-id="7ed82-110">![“添加派生层次结构”按钮](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-02.jpg "“添加派生层次结构”按钮")</span><span class="sxs-lookup"><span data-stu-id="7ed82-110">![Add Derived Hierarchy Button](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-02.jpg "Add Derived Hierarchy Button")</span></span>  
  
5.  <span data-ttu-id="7ed82-111">为**派生层次结构名称**键入**SuppliersInState** 。</span><span class="sxs-lookup"><span data-stu-id="7ed82-111">Type **SuppliersInState** for the **Derived hierarchy name**.</span></span>  
  
6.  <span data-ttu-id="7ed82-112">单击工具栏上的 "**保存**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="7ed82-112">Click **Save** button on the toolbar.</span></span>  
  
     <span data-ttu-id="7ed82-113">![“保存派生层次结构”按钮](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-03.jpg "“保存派生层次结构”按钮")</span><span class="sxs-lookup"><span data-stu-id="7ed82-113">![Save Derived Hierarchy Button](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-03.jpg "Save Derived Hierarchy Button")</span></span>  
  
7.  <span data-ttu-id="7ed82-114">从可用级别拖动**供应商** **： SuppliersInState**到**当前级别： SuppliersInState**。</span><span class="sxs-lookup"><span data-stu-id="7ed82-114">Drag **Supplier** from **Available Levels: SuppliersInState** to **Current Levels: SuppliersInState**.</span></span>  
  
     <span data-ttu-id="7ed82-115">![当前级别的可用实体和层次结构](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-04.jpg "当前级别的可用实体和层次结构")</span><span class="sxs-lookup"><span data-stu-id="7ed82-115">![Avialble Entities and Hierarchies to Current Level](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-04.jpg "Avialble Entities and Hierarchies to Current Level")</span></span>  
  
8.  <span data-ttu-id="7ed82-116">将**状态**从 "**可用级别： SuppliersInState** " 拖到 "**当前级别： SuppliersInState**"。</span><span class="sxs-lookup"><span data-stu-id="7ed82-116">Drag **State** from **Available Levels: SuppliersInState** to **Current Levels: SuppliersInState**.</span></span> <span data-ttu-id="7ed82-117">屏幕应具有**当前级别**，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="7ed82-117">The screen should have **Current Levels** as shown in the following picture.</span></span>  
  
     <span data-ttu-id="7ed82-118">![当前级别和派生层次结构预览](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-05.jpg "当前级别和派生层次结构预览")</span><span class="sxs-lookup"><span data-stu-id="7ed82-118">![Current Levels and Preview of Derived Hierarchy](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-05.jpg "Current Levels and Preview of Derived Hierarchy")</span></span>  
  
9. <span data-ttu-id="7ed82-119">在 "**预览**" 窗口中，展开 " **NY {纽约}** "，你应看到一个处于该状态的供应商，如上图所示。</span><span class="sxs-lookup"><span data-stu-id="7ed82-119">In the **Preview** window, expand **NY { New York}** and you should see one supplier in that state as shown in the preceding image.</span></span>  
  
10. <span data-ttu-id="7ed82-120">单击页面顶部**SQL Server 2012 Master Data Services** ，切换到**主数据管理器**的主页。</span><span class="sxs-lookup"><span data-stu-id="7ed82-120">Switch to the main page of **Master Data Manager** by clicking **SQL Server 2012 Master Data Services** at the top of the page.</span></span>  
  
11. <span data-ttu-id="7ed82-121">单击 **“资源管理器”**。</span><span class="sxs-lookup"><span data-stu-id="7ed82-121">Click **Explorer**.</span></span>  
  
12. <span data-ttu-id="7ed82-122">将鼠标悬停在**层次结构**上，然后单击 "**派生： SuppliersInState**"。</span><span class="sxs-lookup"><span data-stu-id="7ed82-122">Hover the mouse over **Hierarchies** and click **Derived:SuppliersInState**.</span></span>  
  
     <span data-ttu-id="7ed82-123">![层次结构 - Derived:SuppliersInState 菜单](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-06.jpg "层次结构 - Derived:SuppliersInState 菜单")</span><span class="sxs-lookup"><span data-stu-id="7ed82-123">![Hierarchies - Derived:SuppliersInState Menu](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-06.jpg "Hierarchies - Derived:SuppliersInState Menu")</span></span>  
  
13. <span data-ttu-id="7ed82-124">单击**树视图**中的任何 "**状态**" 节点，你应会在右窗格中看到该状态的供应商。</span><span class="sxs-lookup"><span data-stu-id="7ed82-124">Click on any **state** node in the **tree view** and you should see the suppliers in that state in the right pane.</span></span>  
  
     <span data-ttu-id="7ed82-125">![资源管理器中的派生层次结构](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-07.jpg "资源管理器中的派生层次结构")</span><span class="sxs-lookup"><span data-stu-id="7ed82-125">![Derived Hierarchy in Explorer](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-07.jpg "Derived Hierarchy in Explorer")</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="7ed82-126">下一步</span><span class="sxs-lookup"><span data-stu-id="7ed82-126">Next Step</span></span>  
 [<span data-ttu-id="7ed82-127">第 5 课：使用 SSIS 自动执行清理和匹配</span><span class="sxs-lookup"><span data-stu-id="7ed82-127">Lesson 5: Automating the Cleansing and Matching using SSIS</span></span>](../../2014/tutorials/lesson-5-automating-the-cleansing-and-matching-using-ssis.md)  
  
  
