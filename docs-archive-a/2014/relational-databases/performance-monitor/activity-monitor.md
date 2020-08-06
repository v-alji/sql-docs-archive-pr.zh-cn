---
title: 活动监视器 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Activity Monitor [SQL Server]
ms.assetid: 1e6c430d-3a2a-468e-a3d5-ef5459c36c15
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 71fd0d1172b4fcd5739a3af1a60246cc7dce3b93
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692865"
---
# <a name="activity-monitor"></a><span data-ttu-id="202dd-102">活动监视器</span><span class="sxs-lookup"><span data-stu-id="202dd-102">Activity Monitor</span></span>
  <span data-ttu-id="202dd-103">活动监视器显示有关 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 进程的信息，并了解这些进程如何影响 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的当前实例。</span><span class="sxs-lookup"><span data-stu-id="202dd-103">Activity Monitor displays information about [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] processes and how these processes affect the current instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="benefits-of-activity-monitor"></a><span data-ttu-id="202dd-104">活动监视器的优点</span><span class="sxs-lookup"><span data-stu-id="202dd-104">Benefits of Activity Monitor</span></span>  
 <span data-ttu-id="202dd-105">活动监视器是一个选项卡式文档窗口，它包含以下可展开和可折叠的窗格：**概述**、**活动用户任务**、**资源等待**、**数据文件 I/o**和**最新的开销较高的查询**。</span><span class="sxs-lookup"><span data-stu-id="202dd-105">Activity Monitor is a tabbed document window that has the following expandable and collapsible panes: **Overview**, **Active User Tasks**, **Resource Waits**, **Data File I/O**, and **Recent Expensive Queries**.</span></span> <span data-ttu-id="202dd-106">展开任何窗格时，活动监视器都将查询实例以获取相关信息。</span><span class="sxs-lookup"><span data-stu-id="202dd-106">When any pane is expanded, Activity Monitor queries the instance for information.</span></span> <span data-ttu-id="202dd-107">折叠窗格时，该窗格的所有查询活动都将停止。</span><span class="sxs-lookup"><span data-stu-id="202dd-107">When a pane is collapsed, all querying activity stops for that pane.</span></span> <span data-ttu-id="202dd-108">还可以同时展开一个或多个窗格，以查看实例上不同种类的活动。</span><span class="sxs-lookup"><span data-stu-id="202dd-108">You can also expand one or more panes at the same time to view different kinds of activity on the instance.</span></span>  
  
 <span data-ttu-id="202dd-109">对于 "**活动用户任务**"、"**资源等待**"、"**数据文件 I/o**" 和 "**最近开销较高的查询**" 窗格中包括的列，可以通过以下方式自定义显示内容：</span><span class="sxs-lookup"><span data-stu-id="202dd-109">For the columns that are included in the **Active User Tasks**, **Resource Waits**, **Data File I/O**, and **Recent Expensive Queries** panes, you can customize the display in the following ways:</span></span>  
  
1.  <span data-ttu-id="202dd-110">若要重排列的顺序，请单击列标题，并将其拖到标题功能区中的另一位置。</span><span class="sxs-lookup"><span data-stu-id="202dd-110">To rearrange the order of the columns, click the column heading and drag it to another location in the heading ribbon.</span></span>  
  
2.  <span data-ttu-id="202dd-111">若要排序列，请单击列名称。</span><span class="sxs-lookup"><span data-stu-id="202dd-111">To sort a column, click the column name.</span></span>  
  
3.  <span data-ttu-id="202dd-112">若要对一个或多个列进行筛选，请单击列标题中的下拉箭头，然后选择值。</span><span class="sxs-lookup"><span data-stu-id="202dd-112">To filter on one or more columns, click the drop-down arrow in the column heading, and then select a value.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="202dd-113">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="202dd-113">Related Tasks</span></span>  
 <span data-ttu-id="202dd-114">通过以下任务以开始使用活动监视器：</span><span class="sxs-lookup"><span data-stu-id="202dd-114">Use the following tasks to get started with Activity Monitor:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="202dd-115">**说明**</span><span class="sxs-lookup"><span data-stu-id="202dd-115">**Description**</span></span>|<span data-ttu-id="202dd-116">**主题**</span><span class="sxs-lookup"><span data-stu-id="202dd-116">**Topic**</span></span>|  
|<span data-ttu-id="202dd-117">说明如何打开活动监视器和如何设置活动监视器刷新间隔。</span><span class="sxs-lookup"><span data-stu-id="202dd-117">Describes how to open Activity Monitor and how to set the Activity Monitor refresh interval.</span></span>|[<span data-ttu-id="202dd-118">打开活动监视器 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="202dd-118">Open Activity Monitor &#40;SQL Server Management Studio&#41;</span></span>](../performance-monitor/open-activity-monitor-sql-server-management-studio.md)|  
|<span data-ttu-id="202dd-119">链接到关于服务器性能和活动监视的主题。</span><span class="sxs-lookup"><span data-stu-id="202dd-119">Links to topics for server performance and activity monitoring.</span></span>|[<span data-ttu-id="202dd-120">服务器性能和活动监视</span><span class="sxs-lookup"><span data-stu-id="202dd-120">Server Performance and Activity Monitoring</span></span>](../performance/server-performance-and-activity-monitoring.md)|  
  
  
