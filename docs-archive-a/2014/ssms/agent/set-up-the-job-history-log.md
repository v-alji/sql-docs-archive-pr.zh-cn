---
title: 设置作业历史记录日志 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], history
- logs [SQL Server], jobs
- SQL Server Agent jobs, history
- historical information [SQL Server], jobs
ms.assetid: 018e5c49-d3a0-4504-851a-f70996a34bb7
author: stevestein
ms.author: sstein
ms.openlocfilehash: cb42e1daaee8a3a9e5ae9cc3c09a8cc42dcbff56
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682655"
---
# <a name="set-up-the-job-history-log"></a><span data-ttu-id="0deea-102">Set Up the Job History Log</span><span class="sxs-lookup"><span data-stu-id="0deea-102">Set Up the Job History Log</span></span>
  <span data-ttu-id="0deea-103">本主题介绍如何设置 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理作业历史记录日志。</span><span class="sxs-lookup"><span data-stu-id="0deea-103">This topic describes how to set up the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job history log.</span></span>  
  
-   <span data-ttu-id="0deea-104">**开始之前：** [安全性](#Security)</span><span class="sxs-lookup"><span data-stu-id="0deea-104">**Before you begin:**  [Security](#Security)</span></span>  
  
-   <span data-ttu-id="0deea-105">**若要设置作业历史记录日志，请使用：**  [SQL Server Management Studio](#SSMS)</span><span class="sxs-lookup"><span data-stu-id="0deea-105">**To setup the job history log, using:**  [SQL Server Management Studio](#SSMS)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="0deea-106">开始之前</span><span class="sxs-lookup"><span data-stu-id="0deea-106">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="0deea-107">Security</span><span class="sxs-lookup"><span data-stu-id="0deea-107">Security</span></span>  
 <span data-ttu-id="0deea-108">有关详细信息，请参阅[实现 SQL Server 代理安全性](implement-sql-server-agent-security.md)。</span><span class="sxs-lookup"><span data-stu-id="0deea-108">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="0deea-109">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="0deea-109">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="0deea-110">**设置作业历史记录日志**</span><span class="sxs-lookup"><span data-stu-id="0deea-110">**To set up the job history log**</span></span>  
  
1.  <span data-ttu-id="0deea-111">在**对象资源管理器中，** 连接到的实例 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] ，然后展开该实例。</span><span class="sxs-lookup"><span data-stu-id="0deea-111">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="0deea-112">右键单击“SQL Server 代理”\*\*\*\*，然后单击“属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0deea-112">Right-click **SQL Server Agent**, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="0deea-113">在 **“SQL Server 代理属性”** 对话框中，选择 **“历史记录”** 页。</span><span class="sxs-lookup"><span data-stu-id="0deea-113">In the **SQL Server Agent Properties** dialog box, select the **History** page.</span></span>  
  
4.  <span data-ttu-id="0deea-114">从以下选项中选择：</span><span class="sxs-lookup"><span data-stu-id="0deea-114">Choose from the following options:</span></span>  
  
    1.  <span data-ttu-id="0deea-115">选中 **“限制作业历史记录日志的大小”**，然后键入作业历史记录日志的最大行数和每个作业的最大行数。</span><span class="sxs-lookup"><span data-stu-id="0deea-115">Check **Limit size of job history log**, and then type the maximum number of rows for the job history log, and the maximum number of rows per job.</span></span>  
  
    2.  <span data-ttu-id="0deea-116">选中 **“自动删除代理历史记录”**，然后指定时间段。这样，早于此时间段的历史记录将从日志中清除。</span><span class="sxs-lookup"><span data-stu-id="0deea-116">Check **Automatically remove agent history**, and specify a time period, such that history older than this period will be purged from the log.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0deea-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0deea-117">See Also</span></span>  
 <span data-ttu-id="0deea-118">[执行作业](implement-jobs.md) </span><span class="sxs-lookup"><span data-stu-id="0deea-118">[Implement Jobs](implement-jobs.md) </span></span>  
 <span data-ttu-id="0deea-119">[监视作业活动](monitor-job-activity.md) </span><span class="sxs-lookup"><span data-stu-id="0deea-119">[Monitor Job Activity](monitor-job-activity.md) </span></span>  
 [<span data-ttu-id="0deea-120">创建作业</span><span class="sxs-lookup"><span data-stu-id="0deea-120">Create Jobs</span></span>](create-jobs.md)  
  
  
