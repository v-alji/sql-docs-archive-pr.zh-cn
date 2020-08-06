---
title: 设置 CPU 空闲时间和持续时间 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- CPU [SQL Server], idle conditions
- time [SQL Server], CPU idle and duration
- duration of CPU idle [SQL Server]
- SQL Server Agent, CPU idle conditions
- idle time [SQL Server]
ms.assetid: 8647b465-d899-4cc7-9640-134a506d0a2e
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1660f6d70977b8f590a18adf952a6a19f32a26cf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694206"
---
# <a name="set-cpu-idle-time-and-duration-sql-server-management-studio"></a><span data-ttu-id="d4ee1-102">设置 CPU 空闲时间和持续时间 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="d4ee1-102">Set CPU Idle Time and Duration (SQL Server Management Studio)</span></span>
  <span data-ttu-id="d4ee1-103">本主题说明如何在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中通过使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]定义服务器的 CPU 空闲条件。</span><span class="sxs-lookup"><span data-stu-id="d4ee1-103">This topic explains how to define the CPU idle condition for your server in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="d4ee1-104">CPU 空闲定义会影响 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理对事件的响应方式。</span><span class="sxs-lookup"><span data-stu-id="d4ee1-104">The CPU idle definition influences how [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent responds to events.</span></span> <span data-ttu-id="d4ee1-105">例如，假设将 CPU 空闲条件定义为 CPU 平均使用率低于 10% 并在此级别保持 10 分钟。</span><span class="sxs-lookup"><span data-stu-id="d4ee1-105">For example, suppose that you define the CPU idle condition as when the average CPU usage falls below 10 percent and remains at this level for 10 minutes.</span></span> <span data-ttu-id="d4ee1-106">那么，如果将作业定义为在服务器 CPU 达到空闲条件时执行，则当 CPU 使用率低于 10% 并在该级别保持 10 分钟后，作业将开始执行。</span><span class="sxs-lookup"><span data-stu-id="d4ee1-106">Then if you have defined jobs to execute whenever the server CPU reaches an idle condition, the job will start when the CPU usage falls below 10 percent and remains at that level for 10 minutes.</span></span> <span data-ttu-id="d4ee1-107">如果作业对服务器的性能具有显著影响，如何定义 CPU 空闲条件将变得非常重要。</span><span class="sxs-lookup"><span data-stu-id="d4ee1-107">If this is a job that significantly impacts the performance of your server, how you define the CPU idle condition is important.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="d4ee1-108">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="d4ee1-108">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-set-cpu-idle-time-and-duration"></a><span data-ttu-id="d4ee1-109">设置 CPU 空闲时间和持续时间</span><span class="sxs-lookup"><span data-stu-id="d4ee1-109">To set CPU idle time and duration</span></span>  
  
1.  <span data-ttu-id="d4ee1-110">在**对象资源管理器中，** 连接到的实例 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] ，然后展开该实例。</span><span class="sxs-lookup"><span data-stu-id="d4ee1-110">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="d4ee1-111">右键单击“SQL Server 代理”\*\*\*\*，再单击“属性”\*\*\*\*，然后选择“高级”\*\*\*\* 页。</span><span class="sxs-lookup"><span data-stu-id="d4ee1-111">Right-click **SQL Server Agent**, click **Properties**, and select the **Advanced** page.</span></span>  
  
3.  <span data-ttu-id="d4ee1-112">在 **“空闲 CPU 条件”** 下，执行下列操作：</span><span class="sxs-lookup"><span data-stu-id="d4ee1-112">Under **Idle CPU condition**, do the following:</span></span>  
  
    -   <span data-ttu-id="d4ee1-113">选中 **“定义空闲 CPU 条件”**。</span><span class="sxs-lookup"><span data-stu-id="d4ee1-113">Check **Define idle CPU condition.**</span></span>  
  
    -   <span data-ttu-id="d4ee1-114">在“CPU 平均使用率低于”\*\*\*\*（对于所有 CPU 而言）框中指定百分比。</span><span class="sxs-lookup"><span data-stu-id="d4ee1-114">Specify a percentage for the **Average CPU usage falls below** (across all CPUs) box.</span></span> <span data-ttu-id="d4ee1-115">此选项设置 CPU 必须低于什么使用率级别才能变为空闲状态。</span><span class="sxs-lookup"><span data-stu-id="d4ee1-115">This sets the usage level that the CPU must fall below before it is considered idle.</span></span>  
  
    -   <span data-ttu-id="d4ee1-116">在 **“并且保持低于此级别”** 框中指定秒数。</span><span class="sxs-lookup"><span data-stu-id="d4ee1-116">Specify a number of seconds for the **And remains below this level for** box.</span></span> <span data-ttu-id="d4ee1-117">此选项设置 CPU 最小使用率必须保持多长时间 CPU 才能变为空闲状态。</span><span class="sxs-lookup"><span data-stu-id="d4ee1-117">This sets the duration that the minimum CPU usage must remain at before it is considered idle.</span></span>  
  
  
