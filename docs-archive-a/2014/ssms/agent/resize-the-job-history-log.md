---
title: 调整作业历史记录日志的大小 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], history
- resizing job history log
- size [SQL Server], job history log
- logs [SQL Server], jobs
- SQL Server Agent jobs, history
- historical information [SQL Server], jobs
ms.assetid: ddee1ce8-9d1b-4017-9894-bf7256aed95d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4c25cc43295d47b2bc19d48b5b257dbbe6bcfe9b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580519"
---
# <a name="resize-the-job-history-log"></a><span data-ttu-id="4fb48-102">Resize the Job History Log</span><span class="sxs-lookup"><span data-stu-id="4fb48-102">Resize the Job History Log</span></span>
  <span data-ttu-id="4fb48-103">本主题说明如何 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用在中设置代理作业历史记录日志的大小限制 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="4fb48-103">This topic describes how to set size limits for [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job history logs in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
-   <span data-ttu-id="4fb48-104">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="4fb48-104">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="4fb48-105">安全性</span><span class="sxs-lookup"><span data-stu-id="4fb48-105">Security</span></span>](#Security)  
  
-   <span data-ttu-id="4fb48-106">**若要设置作业历史记录日志的大小限制，可使用：**</span><span class="sxs-lookup"><span data-stu-id="4fb48-106">**To set size limits for job history logs, using:**</span></span>  
  
     [<span data-ttu-id="4fb48-107">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="4fb48-107">SQL Server Management Studio</span></span>](#SSMS)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="4fb48-108">开始之前</span><span class="sxs-lookup"><span data-stu-id="4fb48-108">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="4fb48-109">Security</span><span class="sxs-lookup"><span data-stu-id="4fb48-109">Security</span></span>  
 <span data-ttu-id="4fb48-110">有关详细信息，请参阅[实现 SQL Server 代理安全性](implement-sql-server-agent-security.md)。</span><span class="sxs-lookup"><span data-stu-id="4fb48-110">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="4fb48-111">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="4fb48-111">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-resize-the-job-history-log-based-on-raw-size"></a><span data-ttu-id="4fb48-112">基于原始大小调整作业历史记录日志的大小</span><span class="sxs-lookup"><span data-stu-id="4fb48-112">To resize the job history log based on raw size</span></span>  
  
1.  <span data-ttu-id="4fb48-113">在**对象资源管理器中，** 连接到的实例 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] ，然后展开该实例。</span><span class="sxs-lookup"><span data-stu-id="4fb48-113">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="4fb48-114">右键单击“SQL Server 代理”\*\*\*\*，然后单击“属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4fb48-114">Right-click **SQL Server Agent**, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="4fb48-115">选择“历史记录”\*\*\*\* 页，然后确认已选中“限制作业历史记录日志的大小”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4fb48-115">Select the **History** page, and then confirm that **Limit size of job history log**is checked.</span></span>  
  
4.  <span data-ttu-id="4fb48-116">在 **“作业历史记录日志的最大大小”** 框中，输入作业历史记录日志允许的最大行数。</span><span class="sxs-lookup"><span data-stu-id="4fb48-116">In the **Maximum job history log size** box, enter the maximum number of rows the job history log should allow.</span></span>  
  
5.  <span data-ttu-id="4fb48-117">在 **“每个作业的最大作业历史记录行数”** 框中，输入作业允许的作业历史记录的最大行数。</span><span class="sxs-lookup"><span data-stu-id="4fb48-117">In the **Maximum job history rows per job** box, enter the maximum number of job history rows to allow for a job.</span></span>  
  
#### <a name="to-resize-the-job-history-log-based-on-time"></a><span data-ttu-id="4fb48-118">基于时间调整作业历史记录日志的大小</span><span class="sxs-lookup"><span data-stu-id="4fb48-118">To resize the job history log based on time</span></span>  
  
1.  <span data-ttu-id="4fb48-119">在 **对象资源管理器**中，连接到 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]的实例，然后展开该实例。</span><span class="sxs-lookup"><span data-stu-id="4fb48-119">In **Object Explorer**, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="4fb48-120">右键单击“SQL Server 代理”\*\*\*\*，然后单击“属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4fb48-120">Right-click **SQL Server Agent**, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="4fb48-121">选择 **“历史记录”** 页，然后单击 **“自动删除代理历史记录”**。</span><span class="sxs-lookup"><span data-stu-id="4fb48-121">Select the **History** page, and then click **Automatically remove agent history**.</span></span>  
  
4.  <span data-ttu-id="4fb48-122">选择适当的“天”\*\*\*\*、“周”\*\*\*\* 或“月”\*\*\*\* 数。</span><span class="sxs-lookup"><span data-stu-id="4fb48-122">Select the appropriate number of **Days(s)**, **Week(s)**, or **Month(s)**.</span></span>  
  
  
