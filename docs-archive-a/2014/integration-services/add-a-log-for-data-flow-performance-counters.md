---
title: 添加数据流性能计数器的日志 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- performance counters [Integration Services]
- counters [Integration Services]
- logs [Integration Services], data flow counters
ms.assetid: b500d166-33ba-4b82-a92d-b0a333924e8d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 489bde1b0e5769f05d1063eb0af2376b659574de
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691838"
---
# <a name="add-a-log-for-data-flow-performance-counters"></a><span data-ttu-id="1445b-102">添加数据流性能计数器的日志</span><span class="sxs-lookup"><span data-stu-id="1445b-102">Add a Log for Data Flow Performance Counters</span></span>
  <span data-ttu-id="1445b-103">本过程介绍如何为数据流引擎提供的性能计数器添加日志。</span><span class="sxs-lookup"><span data-stu-id="1445b-103">This procedure describes how to add a log for the performance counters that the data flow engine provides.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1445b-104">如果在运行 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 的计算机上安装 [!INCLUDE[winxpsvr](../includes/winxpsvr-md.md)]，然后将该计算机升级到 [!INCLUDE[firstref_longhorn](../includes/firstref-longhorn-md.md)]，则升级过程会从该计算机删除 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 性能计数器。</span><span class="sxs-lookup"><span data-stu-id="1445b-104">If you install [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] on a computer that is running [!INCLUDE[winxpsvr](../includes/winxpsvr-md.md)], and then upgrade that computer to [!INCLUDE[firstref_longhorn](../includes/firstref-longhorn-md.md)], the upgrade process removes the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] performance counters from the computer.</span></span> <span data-ttu-id="1445b-105">若要还原计算机上的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 性能计数器，请在修复模式下运行 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 安装程序。</span><span class="sxs-lookup"><span data-stu-id="1445b-105">To restore the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] performance counters on the computer, run [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Setup in repair mode.</span></span>  
  
### <a name="to-add-logging-of-performance-counters"></a><span data-ttu-id="1445b-106">添加性能计数器的日志记录</span><span class="sxs-lookup"><span data-stu-id="1445b-106">To add logging of performance counters</span></span>  
  
1.  <span data-ttu-id="1445b-107">在 **“控制面板”** 中，如果您使用的是经典视图，请单击 **“管理工具”** 。</span><span class="sxs-lookup"><span data-stu-id="1445b-107">In **Control Panel**, if you are using Classic view, click **Administrative Tools**.</span></span> <span data-ttu-id="1445b-108">如果使用的是分类视图，请单击 **“性能和维护”** ，再单击 **“管理工具”** 。</span><span class="sxs-lookup"><span data-stu-id="1445b-108">If you are using Category view, click **Performance and Maintenance** and then click **Administrative Tools**.</span></span>  
  
2.  <span data-ttu-id="1445b-109">单击 **“性能”** 。</span><span class="sxs-lookup"><span data-stu-id="1445b-109">Click **Performance**.</span></span>  
  
3.  <span data-ttu-id="1445b-110">在“性能”对话框中，展开“性能日志和警报”，右键单击“计数器日志”，再单击“新建日志设置”。</span><span class="sxs-lookup"><span data-stu-id="1445b-110">In the **Performance** dialog box, expand **Performance Logs and Alerts**, right-click **Counter Logs**, and then click **New Log Settings**.</span></span> <span data-ttu-id="1445b-111">键入日志的名称。</span><span class="sxs-lookup"><span data-stu-id="1445b-111">Type the name of the log.</span></span> <span data-ttu-id="1445b-112">例如，键入 **MyLog**。</span><span class="sxs-lookup"><span data-stu-id="1445b-112">For example, type **MyLog**.</span></span>  
  
4.  <span data-ttu-id="1445b-113">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="1445b-113">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="1445b-114">在 **MyLog** 对话框中，单击 **“添加计数器”** 。</span><span class="sxs-lookup"><span data-stu-id="1445b-114">In the **MyLog** dialog box, click **Add Counters**.</span></span>  
  
6.  <span data-ttu-id="1445b-115">单击 **“使用本地计算机计数器”** 记录本地计算机上性能计数器的日志，或者单击 **“从计算机选择计数器”** ，然后从列表中选择计算机，以记录该指定的计算机的性能计数器的日志。</span><span class="sxs-lookup"><span data-stu-id="1445b-115">Click **Use local computer counters** to log performance counters on the local computer, or click **Select counters from computer** and then select a computer from the list to log performance counters on the specified computer.</span></span>  
  
7.  <span data-ttu-id="1445b-116">在 **“添加计数器”** 对话框中，选择 **“性能对象”** 列表中的 **“SQL Server:SSIS 管道”** 。</span><span class="sxs-lookup"><span data-stu-id="1445b-116">In the **Add Counters** dialog box, select **SQL Server:SSIS Pipeline** in the **Performance object** list.</span></span>  
  
8.  <span data-ttu-id="1445b-117">若要选择性能计数器，请执行下列操作之一：</span><span class="sxs-lookup"><span data-stu-id="1445b-117">To select performance counters, do one of the following:</span></span>  
  
    -   <span data-ttu-id="1445b-118">选择 **“所有计数器”** 以记录所有性能计数器的日志。</span><span class="sxs-lookup"><span data-stu-id="1445b-118">Select **All Counters** to log all performance counters.</span></span>  
  
    -   <span data-ttu-id="1445b-119">选择 **“选择列表中的计数器”** ，然后选择要使用的性能计数器。</span><span class="sxs-lookup"><span data-stu-id="1445b-119">Select **Select counters in list** and select the performance counters to use.</span></span>  
  
9. <span data-ttu-id="1445b-120">单击“添加”。</span><span class="sxs-lookup"><span data-stu-id="1445b-120">Click **Add**.</span></span>  
  
10. <span data-ttu-id="1445b-121">单击“关闭”。</span><span class="sxs-lookup"><span data-stu-id="1445b-121">Click **Close**.</span></span>  
  
11. <span data-ttu-id="1445b-122">在 **MyLog** 对话框中，检查 **“计数器”** 列表中记录日志的性能计数器的列表。</span><span class="sxs-lookup"><span data-stu-id="1445b-122">In the **MyLog** dialog box, review the list of logging performance counters in the **Counters** list.</span></span>  
  
12. <span data-ttu-id="1445b-123">若要添加其他计数器，请重复步骤 5 到步骤 10。</span><span class="sxs-lookup"><span data-stu-id="1445b-123">To add additional counters, repeat steps 5 through 10.</span></span>  
  
13. <span data-ttu-id="1445b-124">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="1445b-124">Click **OK**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="1445b-125">必须使用属于 Administrators 组成员的本地帐户或域帐户启动性能日志和警报服务。</span><span class="sxs-lookup"><span data-stu-id="1445b-125">You must start the Performance Logs and Alerts service using a local account or a domain account that is a member of the Administrators group.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1445b-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1445b-126">See Also</span></span>  
 <span data-ttu-id="1445b-127">[性能计数器](performance/performance-counters.md) </span><span class="sxs-lookup"><span data-stu-id="1445b-127">[Performance Counters](performance/performance-counters.md) </span></span>  
 [<span data-ttu-id="1445b-128">在“日志事件”窗口中查看日志项</span><span class="sxs-lookup"><span data-stu-id="1445b-128">View Log Entries in the Log Events Window</span></span>](../../2014/integration-services/view-log-entries-in-the-log-events-window.md)  
  
  
