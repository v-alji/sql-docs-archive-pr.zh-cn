---
title: 设置 SQL Server 数据库警报 (Windows) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- alerts [SQL Server], creating
ms.assetid: 65d2c5c1-921f-4eff-9ef7-149170ab61e8
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 090eeda2c134857df18d083ce06d460214aa4dfb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591303"
---
# <a name="set-up-a-sql-server-database-alert-windows"></a><span data-ttu-id="eb8ff-102">设置 SQL Server 数据库警报 (Windows)</span><span class="sxs-lookup"><span data-stu-id="eb8ff-102">Set Up a SQL Server Database Alert (Windows)</span></span>
  <span data-ttu-id="eb8ff-103">通过使用系统监视器可以创建一个在达到系统监视器计数器的阈值时发出的警报。</span><span class="sxs-lookup"><span data-stu-id="eb8ff-103">Using System Monitor, you can create an alert to be raised when a threshold value for a System Monitor counter has been reached.</span></span> <span data-ttu-id="eb8ff-104">作为对警报的响应，系统监视器会启动一个应用程序，例如为处理警报情况而编写的自定义应用程序。</span><span class="sxs-lookup"><span data-stu-id="eb8ff-104">In response to the alert, System Monitor can launch an application, such as a custom application written to handle the alert condition.</span></span> <span data-ttu-id="eb8ff-105">例如，您可以创建在死锁数超过特定值时将会引发的警报。</span><span class="sxs-lookup"><span data-stu-id="eb8ff-105">For example, you can create an alert that is raised when the number of deadlocks exceeds a specific value.</span></span>  
  
 <span data-ttu-id="eb8ff-106">此外，还可以使用 Microsoft [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理来定义警报。</span><span class="sxs-lookup"><span data-stu-id="eb8ff-106">Alerts also can be defined using Microsoft [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span> <span data-ttu-id="eb8ff-107">有关详细信息，请参阅 [“警报”](../../ssms/agent/alerts.md)。</span><span class="sxs-lookup"><span data-stu-id="eb8ff-107">For more information, see [Alerts](../../ssms/agent/alerts.md).</span></span>  
  
### <a name="to-set-up-a-sql-server-database-alert"></a><span data-ttu-id="eb8ff-108">设置 SQL Server 数据库警报</span><span class="sxs-lookup"><span data-stu-id="eb8ff-108">To set up a SQL Server database alert</span></span>  
  
1.  <span data-ttu-id="eb8ff-109">在 "性能" 窗口的导航树中，展开**性能日志和警报**。</span><span class="sxs-lookup"><span data-stu-id="eb8ff-109">On the navigation tree of the Performance window, expand **Performance Logs and Alerts**.</span></span>  
  
2.  <span data-ttu-id="eb8ff-110">右键单击“警报”\*\*\*\*，再单击“新建警报设置”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="eb8ff-110">Right-click **Alerts**, and then click **New Alert Settings**.</span></span>  
  
3.  <span data-ttu-id="eb8ff-111">在 **“新建警报设置”** 对话框中，输入新警报的名称，再单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="eb8ff-111">In the **New Alert Settings** dialog box, type a name for the new alert, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="eb8ff-112">在新建警报对话框的 **“常规”** 选项卡上，添加一个 **注释**，再单击 **“添加”** 为该警报添加计数器。</span><span class="sxs-lookup"><span data-stu-id="eb8ff-112">On the **General** tab of the dialog box for the new alert, add a **Comment**, and click **Add** to add a counter to the alert.</span></span>  
  
     <span data-ttu-id="eb8ff-113">所有警报必须至少有一个计数器。</span><span class="sxs-lookup"><span data-stu-id="eb8ff-113">All alerts must have at least one counter.</span></span>  
  
5.  <span data-ttu-id="eb8ff-114">在“添加计数器”对话框中，从 **“性能对象”** 列表选择一个 SQL Server 对象，然后从 **“从列表中选择计数器”** 选择一个计数器。</span><span class="sxs-lookup"><span data-stu-id="eb8ff-114">In the Add Counters dialog box, select a SQL Server object from the **Performance Object** list, and then select a counter from the **Select counters from list**.</span></span>  
  
6.  <span data-ttu-id="eb8ff-115">若要为警报添加计数器，请单击 **“添加”**。</span><span class="sxs-lookup"><span data-stu-id="eb8ff-115">To add the counter to the alert, click **Add**.</span></span> <span data-ttu-id="eb8ff-116">您可以继续添加计数器，也可以单击 **“关闭”** 返回到新建警报对话框。</span><span class="sxs-lookup"><span data-stu-id="eb8ff-116">You can continue to add counters, or you can click **Close** to return to the dialog box for the new alert.</span></span>  
  
7.  <span data-ttu-id="eb8ff-117">在新建警报对话框的“将触发警报，如果值是：”\*\*\*\* 列表中，单击“超过”\*\*\*\* 或“低于”\*\*\*\*，然后在“限制”\*\*\*\* 中输入一个阈值。</span><span class="sxs-lookup"><span data-stu-id="eb8ff-117">In the new alert dialog box, click either **Over** or **Under**in the **Alert when the value is** list, and then enter a threshold value in **Limit**.</span></span>  
  
     <span data-ttu-id="eb8ff-118">当计数器的值大于或小于阈值时（取决于单击的是“超过”\*\*\*\* 还是“低于”\*\*\*\*），将生成警报。</span><span class="sxs-lookup"><span data-stu-id="eb8ff-118">The alert is generated when the value for the counter is more than or less than the threshold value (depending on whether you clicked **Over** or **Under**).</span></span>  
  
8.  <span data-ttu-id="eb8ff-119">在 **“数据采样间隔”** 框中，设置采样频率。</span><span class="sxs-lookup"><span data-stu-id="eb8ff-119">In the **Sample data every** boxes, set the sampling frequency.</span></span>  
  
9. <span data-ttu-id="eb8ff-120">在 **“操作”** 选项卡上，设置每次触发警报时要执行的操作。</span><span class="sxs-lookup"><span data-stu-id="eb8ff-120">On the **Action** tab, set actions to occur every time the alert is triggered.</span></span>  
  
10. <span data-ttu-id="eb8ff-121">在 **“计划”** 选项卡上，设置警报扫描的开始和停止计划。</span><span class="sxs-lookup"><span data-stu-id="eb8ff-121">On the **Schedule** tab, set the start and stop schedule for the alert scan.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb8ff-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="eb8ff-122">See Also</span></span>  
 [<span data-ttu-id="eb8ff-123">创建 SQL Server 数据库警报</span><span class="sxs-lookup"><span data-stu-id="eb8ff-123">Create a SQL Server Database Alert</span></span>](../performance-monitor/create-a-sql-server-database-alert.md)  
  
  
