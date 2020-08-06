---
title: 如何查看 CDC 实例属性 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 4bce9b82-7bbd-41df-b3f4-4b40b8bad474
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 86fa298b0e02a16ddbaea220ef7f3d9f6172bf85
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690014"
---
# <a name="how-to-view-the-cdc-instance-properties"></a><span data-ttu-id="ef2d6-102">如何查看 CDC 实例属性</span><span class="sxs-lookup"><span data-stu-id="ef2d6-102">How to View the CDC Instance Properties</span></span>
  <span data-ttu-id="ef2d6-103">本过程介绍如何使用 CDC 设计器控制台查看与您创建的实例有关的信息，以便帮助管理实例操作。</span><span class="sxs-lookup"><span data-stu-id="ef2d6-103">This procedure describes how to use the CDC Designer Console to view information about the instances that you create to help manage the operation of the instances.</span></span>  
  
### <a name="to-view-information-about-a-specific-instance"></a><span data-ttu-id="ef2d6-104">查看有关特定实例的信息</span><span class="sxs-lookup"><span data-stu-id="ef2d6-104">To view information about a specific instance</span></span>  
  
1.  <span data-ttu-id="ef2d6-105">从 **“开始”** 菜单上，选择 **“CDC 设计器控制台”** 。</span><span class="sxs-lookup"><span data-stu-id="ef2d6-105">From the **Start** menu, select the **CDC Designer Console**.</span></span>  
  
2.  <span data-ttu-id="ef2d6-106">在左侧的窗格中，展开 **“变更数据捕获”** ，然后展开包含您要查看的实例的服务。</span><span class="sxs-lookup"><span data-stu-id="ef2d6-106">In the left pane, expand **Change Data Capture** then expand the service that contains the instance you want to view.</span></span>  
  
3.  <span data-ttu-id="ef2d6-107">选择要使用的实例的名称。</span><span class="sxs-lookup"><span data-stu-id="ef2d6-107">Select the name of an instance you want to work with.</span></span>  
  
     <span data-ttu-id="ef2d6-108">与该实例有关的信息将显示在 CDC 设计器控制台的中央部分。</span><span class="sxs-lookup"><span data-stu-id="ef2d6-108">The information about the instance is displayed in the center part of the CDC Designer Console.</span></span> <span data-ttu-id="ef2d6-109">它分为四个选项卡。</span><span class="sxs-lookup"><span data-stu-id="ef2d6-109">It is divided into four tabs.</span></span> <span data-ttu-id="ef2d6-110">所有选项卡均为只读。</span><span class="sxs-lookup"><span data-stu-id="ef2d6-110">All of the tabs are read only.</span></span>  
  
     <span data-ttu-id="ef2d6-111">**Status**</span><span class="sxs-lookup"><span data-stu-id="ef2d6-111">**Status**</span></span>  
     <span data-ttu-id="ef2d6-112">此选项卡显示有关该实例的变更数据捕获的当前状态的信息。</span><span class="sxs-lookup"><span data-stu-id="ef2d6-112">This tab displays the information about the current status of the change data capture for the instance.</span></span> <span data-ttu-id="ef2d6-113">有关此选项卡中显示的内容的信息，请参阅 **Manage a CDC Instance** 中的 [“查看器选项卡”](manage-a-cdc-instance.md)部分。</span><span class="sxs-lookup"><span data-stu-id="ef2d6-113">For information about what is displayed in this tab, see the **Viewer Tabs** section in [Manage a CDC Instance](manage-a-cdc-instance.md).</span></span>  
  
     <span data-ttu-id="ef2d6-114">**Oracle**</span><span class="sxs-lookup"><span data-stu-id="ef2d6-114">**Oracle**</span></span>  
     <span data-ttu-id="ef2d6-115">此选项卡显示与 CDC 实例和 Oracle 源数据库有关的一般信息。</span><span class="sxs-lookup"><span data-stu-id="ef2d6-115">This tab displays general information about the CDC instance and the Oracle source database.</span></span> <span data-ttu-id="ef2d6-116">有关此选项卡中显示的内容的信息，请参阅 [Edit the Oracle Database Properties](edit-the-oracle-database-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="ef2d6-116">For information about what is displayed in this tab, see [Edit the Oracle Database Properties](edit-the-oracle-database-properties.md).</span></span>  
  
     <span data-ttu-id="ef2d6-117">**表**</span><span class="sxs-lookup"><span data-stu-id="ef2d6-117">**Tables**</span></span>  
     <span data-ttu-id="ef2d6-118">此选项卡显示有关变更数据捕获中包含的表的信息。</span><span class="sxs-lookup"><span data-stu-id="ef2d6-118">This tab displays information about the tables included in the change data capture.</span></span> <span data-ttu-id="ef2d6-119">它还列出捕获的列。</span><span class="sxs-lookup"><span data-stu-id="ef2d6-119">It also lists the columns that are captured.</span></span> <span data-ttu-id="ef2d6-120">有关此选项卡中显示的内容的信息，请参阅 [Edit Tables](edit-tables.md)。</span><span class="sxs-lookup"><span data-stu-id="ef2d6-120">For information about what is displayed in this tab, see [Edit Tables](edit-tables.md).</span></span>  
  
     <span data-ttu-id="ef2d6-121">**高级**</span><span class="sxs-lookup"><span data-stu-id="ef2d6-121">**Advanced**</span></span>  
     <span data-ttu-id="ef2d6-122">此选项卡显示在属性编辑器中定义的高级属性的列表。</span><span class="sxs-lookup"><span data-stu-id="ef2d6-122">This tab displays a list of advanced properties that you define in the properties editor.</span></span> <span data-ttu-id="ef2d6-123">有关此选项卡中显示的内容的信息，请参阅 [Edit the Advanced Properties](edit-the-advanced-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="ef2d6-123">For information about what is displayed in this tab, see [Edit the Advanced Properties](edit-the-advanced-properties.md).</span></span>  
  
  
