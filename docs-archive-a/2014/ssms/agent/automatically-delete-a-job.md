---
title: 自动删除作业 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- dropping jobs
- SQL Server Agent jobs, removing
- automatic job removal
- jobs [SQL Server Agent], deleting
- deleting jobs
- removing jobs
ms.assetid: 92dbb6da-5919-4bde-9354-d454e9ea3da0
author: stevestein
ms.author: sstein
ms.openlocfilehash: 07a10ec4a31d553a548bfecdcba426e3b46a1782
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588246"
---
# <a name="automatically-delete-a-job"></a><span data-ttu-id="e0c9c-102">Automatically Delete a Job</span><span class="sxs-lookup"><span data-stu-id="e0c9c-102">Automatically Delete a Job</span></span>
  <span data-ttu-id="e0c9c-103">本主题介绍如何 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 在中将代理配置 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 为在作业成功、失败或完成时通过使用或 SQL Server 管理对象自动删除作业 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="e0c9c-103">This topic describes how to configure [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] to automatically delete jobs when they succeed, fail, or complete by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or SQL Server Management Objects.</span></span>  
  
 <span data-ttu-id="e0c9c-104">作业响应可确保数据库管理员知道作业完成的时间和作业运行频率。</span><span class="sxs-lookup"><span data-stu-id="e0c9c-104">Job responses ensure that database administrators know when jobs complete and how frequently they run.</span></span> <span data-ttu-id="e0c9c-105">典型的作业响应包括：</span><span class="sxs-lookup"><span data-stu-id="e0c9c-105">Typical job responses include:</span></span>  
  
-   <span data-ttu-id="e0c9c-106">使用电子邮件、电子寻呼或 **net send** 消息通知操作员。</span><span class="sxs-lookup"><span data-stu-id="e0c9c-106">Notifying the operator by using e-mail, electronic paging, or a **net send** message.</span></span>  
  
     <span data-ttu-id="e0c9c-107">如果操作员必须执行后续操作，应使用其中的某种作业响应。</span><span class="sxs-lookup"><span data-stu-id="e0c9c-107">Use one of these job responses if the operator must perform a follow-up action.</span></span> <span data-ttu-id="e0c9c-108">例如，当一个备份作业成功地完成之后，必须通知操作员取出备份磁带并将其存放在安全处。</span><span class="sxs-lookup"><span data-stu-id="e0c9c-108">For example, if a backup job completes successfully, the operator must be notified to remove the backup tape and store it in a safe location.</span></span>  
  
-   <span data-ttu-id="e0c9c-109">将事件消息写入 Windows 应用程序日志。</span><span class="sxs-lookup"><span data-stu-id="e0c9c-109">Writing an event message to the Windows application log.</span></span>  
  
     <span data-ttu-id="e0c9c-110">只能对失败的作业使用这种响应。</span><span class="sxs-lookup"><span data-stu-id="e0c9c-110">You can use this response only for failed jobs.</span></span>  
  
-   <span data-ttu-id="e0c9c-111">自动删除作业。</span><span class="sxs-lookup"><span data-stu-id="e0c9c-111">Automatically deleting the job.</span></span>  
  
     <span data-ttu-id="e0c9c-112">如果确信不需要再次运行该作业，可以使用这种作业响应。</span><span class="sxs-lookup"><span data-stu-id="e0c9c-112">Use this job response if you are certain that you do not need to rerun this job.</span></span>  
  
 <span data-ttu-id="e0c9c-113">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="e0c9c-113">**In This Topic**</span></span>  
  
-   <span data-ttu-id="e0c9c-114">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="e0c9c-114">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="e0c9c-115">安全性</span><span class="sxs-lookup"><span data-stu-id="e0c9c-115">Security</span></span>](#Security)  
  
-   <span data-ttu-id="e0c9c-116">**若要指定作业响应，可使用：**</span><span class="sxs-lookup"><span data-stu-id="e0c9c-116">**To specify job responses, using:**</span></span>  
  
     [<span data-ttu-id="e0c9c-117">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="e0c9c-117">SQL Server Management Studio</span></span>](#SSMS)  
  
     [<span data-ttu-id="e0c9c-118">SQL Server 管理对象</span><span class="sxs-lookup"><span data-stu-id="e0c9c-118">SQL Server Management Objects</span></span>](#SMO)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="e0c9c-119">开始之前</span><span class="sxs-lookup"><span data-stu-id="e0c9c-119">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="e0c9c-120">Security</span><span class="sxs-lookup"><span data-stu-id="e0c9c-120">Security</span></span>  
 <span data-ttu-id="e0c9c-121">有关详细信息，请参阅[实现 SQL Server 代理安全性](implement-sql-server-agent-security.md)。</span><span class="sxs-lookup"><span data-stu-id="e0c9c-121">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="e0c9c-122">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="e0c9c-122">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-automatically-delete-a-job"></a><span data-ttu-id="e0c9c-123">自动删除作业</span><span class="sxs-lookup"><span data-stu-id="e0c9c-123">To automatically delete a job</span></span>  
  
1.  <span data-ttu-id="e0c9c-124">在**对象资源管理器中，** 连接到的实例 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] ，然后展开该实例。</span><span class="sxs-lookup"><span data-stu-id="e0c9c-124">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="e0c9c-125">展开 **“SQL Server 代理”**，展开 **“作业”**，右键单击要编辑的作业，再单击 **“属性”**。</span><span class="sxs-lookup"><span data-stu-id="e0c9c-125">Expand **SQL Server Agent**, expand **Jobs**, right-click the job you want to edit, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="e0c9c-126">选择 **“通知”** 页。</span><span class="sxs-lookup"><span data-stu-id="e0c9c-126">Select the **Notifications** page.</span></span>  
  
4.  <span data-ttu-id="e0c9c-127">选中 **“自动删除作业”**，并选择以下某项：</span><span class="sxs-lookup"><span data-stu-id="e0c9c-127">Check **Automatically delete job**, and choose one of the following:</span></span>  
  
    -   <span data-ttu-id="e0c9c-128">单击 **“当作业成功时”** 以在作业成功完成时删除作业状态。</span><span class="sxs-lookup"><span data-stu-id="e0c9c-128">Click **When the job succeeds** to delete the job status when it has completed successfully.</span></span>  
  
    -   <span data-ttu-id="e0c9c-129">单击 **“当作业失败时”** 以在作业失败时删除作业。</span><span class="sxs-lookup"><span data-stu-id="e0c9c-129">Click **When the job fails** to delete the job when it has completed unsuccessfully.</span></span>  
  
    -   <span data-ttu-id="e0c9c-130">单击 **“当作业完成时”** 以删除作业，而不管完成状态如何。</span><span class="sxs-lookup"><span data-stu-id="e0c9c-130">Click **When the job completes** to delete the job regardless of completion status.</span></span>  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a><span data-ttu-id="e0c9c-131">使用 SQL Server 管理对象</span><span class="sxs-lookup"><span data-stu-id="e0c9c-131">Using SQL Server Management Objects</span></span>  
 <span data-ttu-id="e0c9c-132">**自动删除作业**</span><span class="sxs-lookup"><span data-stu-id="e0c9c-132">**To automatically delete a job**</span></span>  
  
 <span data-ttu-id="e0c9c-133">通过使用所选的编程语言（如 Visual Basic、Visual C# 或 PowerShell）来使用`DeleteLevel` 类的 `Job` 属性。</span><span class="sxs-lookup"><span data-stu-id="e0c9c-133">Use the `DeleteLevel` property of the `Job` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell.</span></span> <span data-ttu-id="e0c9c-134">有关详细信息，请参阅 [SQL Server 管理对象 (SMO)](https://msdn.microsoft.com/library/ms162169.aspx)。</span><span class="sxs-lookup"><span data-stu-id="e0c9c-134">For more information, see [SQL Server Management Objects (SMO)](https://msdn.microsoft.com/library/ms162169.aspx).</span></span>  
  
  
