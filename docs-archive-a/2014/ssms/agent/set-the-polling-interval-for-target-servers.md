---
title: 设置目标服务器的轮询间隔 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- interval for polling [SQL Server]
- target servers [SQL Server], polling interval
- polling interval [SQL Server]
ms.assetid: 4ffbbefa-77fb-442e-a77c-cb8c6cab9f3c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 36517f60a99a1a844f6d14d489587eef1de9cb13
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694204"
---
# <a name="set-the-polling-interval-for-target-servers"></a><span data-ttu-id="90ff6-102">Set the Polling Interval for Target Servers</span><span class="sxs-lookup"><span data-stu-id="90ff6-102">Set the Polling Interval for Target Servers</span></span>
  <span data-ttu-id="90ff6-103">本主题介绍如何设置 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理刷新从主服务器到目标服务器的信息的频率。</span><span class="sxs-lookup"><span data-stu-id="90ff6-103">This topic describes how to set the frequency that [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent refreshes information from the master to the target servers.</span></span> <span data-ttu-id="90ff6-104">作业是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理执行的一系列指定操作。</span><span class="sxs-lookup"><span data-stu-id="90ff6-104">A job is a specified series of actions that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent performs.</span></span> <span data-ttu-id="90ff6-105">多服务器作业是主服务器在一台或多台目标服务器上运行的作业。</span><span class="sxs-lookup"><span data-stu-id="90ff6-105">A multiserver job is a job that a master server runs on one or more target servers.</span></span>  
  
-   <span data-ttu-id="90ff6-106">**开始之前：** [安全性](#Security)</span><span class="sxs-lookup"><span data-stu-id="90ff6-106">**Before you begin:**  [Security](#Security)</span></span>  
  
-   <span data-ttu-id="90ff6-107">**若要设置目标服务器的轮询间隔，请使用**  [SQL Server Management Studio](#SSMS)、 [Transact-SQL](#TSQL)</span><span class="sxs-lookup"><span data-stu-id="90ff6-107">**To set the polling interval for target servers, using:**  [SQL Server Management Studio](#SSMS), [Transact-SQL](#TSQL)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="90ff6-108">开始之前</span><span class="sxs-lookup"><span data-stu-id="90ff6-108">Before You Begin</span></span>  
 <span data-ttu-id="90ff6-109">每个目标服务器一次只能运行一个相同作业的实例。</span><span class="sxs-lookup"><span data-stu-id="90ff6-109">Each target server can run one instance of the same job at the same time.</span></span> <span data-ttu-id="90ff6-110">每台目标服务器会定期轮询主服务器，下载分配给目标服务器的任何新作业的一个副本，然后断开连接。</span><span class="sxs-lookup"><span data-stu-id="90ff6-110">Each target server periodically polls the master server, downloads a copy of any new jobs assigned to the target server, and then disconnects.</span></span> <span data-ttu-id="90ff6-111">目标服务器在本地运行作业，然后重新连接到主服务器以上载作业结果状态。</span><span class="sxs-lookup"><span data-stu-id="90ff6-111">The target server runs the job locally and then reconnects to the master server to upload the job outcome status.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="90ff6-112">如果在目标服务器试图上载作业状态时无法访问主服务器，则作业将处于假脱机状态，直到可以访问主服务器。</span><span class="sxs-lookup"><span data-stu-id="90ff6-112">If the master server is inaccessible when the target server tries to upload job status, the job status is spooled until the master server can be accessed.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="90ff6-113">Security</span><span class="sxs-lookup"><span data-stu-id="90ff6-113">Security</span></span>  
 <span data-ttu-id="90ff6-114">有关详细信息，请参阅 [Implement SQL Server Agent Security](implement-sql-server-agent-security.md) 和 [Choose the Right SQL Server Agent Service Account for Multiserver Environments](choose-the-right-sql-server-agent-service-account-for-multiserver-environments.md)。</span><span class="sxs-lookup"><span data-stu-id="90ff6-114">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md) and [Choose the Right SQL Server Agent Service Account for Multiserver Environments](choose-the-right-sql-server-agent-service-account-for-multiserver-environments.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="90ff6-115">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="90ff6-115">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="90ff6-116">**设置目标服务器的轮询间隔**</span><span class="sxs-lookup"><span data-stu-id="90ff6-116">**To set the polling interval for target servers**</span></span>  
  
1.  <span data-ttu-id="90ff6-117">在**对象资源管理器中，** 连接到的实例 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] ，然后展开该实例。</span><span class="sxs-lookup"><span data-stu-id="90ff6-117">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="90ff6-118">右键单击“SQL Server 代理”\*\*\*\*，指向“多服务器管理”\*\*\*\*，再单击“管理目标服务器”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="90ff6-118">Right-click **SQL Server Agent**, point to **Multi Server Administration**, and then click **Manage Target Servers**.</span></span>  
  
3.  <span data-ttu-id="90ff6-119">在 **“目标服务器状态”** 选项卡上，单击 **“发布指令”**。</span><span class="sxs-lookup"><span data-stu-id="90ff6-119">On the **Target Server Status** tab, click **Post Instructions**.</span></span>  
  
4.  <span data-ttu-id="90ff6-120">在 **“指令类型”** 列表中，选择 **“设置轮询间隔”**。</span><span class="sxs-lookup"><span data-stu-id="90ff6-120">In the **Instruction type** list, select **Set polling interval**.</span></span>  
  
5.  <span data-ttu-id="90ff6-121">在 **“轮询间隔”** 框中，输入介于 10 到 28,800 之间的秒数，目标服务器必须在经过该秒数后才会轮询主服务器。</span><span class="sxs-lookup"><span data-stu-id="90ff6-121">In the **Polling interval** box, enter the number of seconds from 10 through 28,800 that must pass before the target server polls the master server.</span></span>  
  
6.  <span data-ttu-id="90ff6-122">在 **“收件人”** 下，执行以下操作之一：</span><span class="sxs-lookup"><span data-stu-id="90ff6-122">Under **Recipients**, do one of the following:</span></span>  
  
    1.  <span data-ttu-id="90ff6-123">如果所有目标服务器共享同一轮询间隔，则单击 **“所有目标服务器”** 。</span><span class="sxs-lookup"><span data-stu-id="90ff6-123">Click **All target servers** if all target servers share the same polling interval.</span></span>  
  
    2.  <span data-ttu-id="90ff6-124">如果并非所有目标服务器都共享同一轮询间隔，则单击 **“以下目标服务器”** ，然后选择将使用此轮询间隔的每台目标服务器。</span><span class="sxs-lookup"><span data-stu-id="90ff6-124">Click **These target servers** if not all target servers share the same polling interval, and then select each target server that will use this polling interval.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> <span data-ttu-id="90ff6-125">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="90ff6-125">Using Transact-SQL</span></span>  
 <span data-ttu-id="90ff6-126">**设置目标服务器的轮询间隔**</span><span class="sxs-lookup"><span data-stu-id="90ff6-126">**To set the polling interval for target servers**</span></span>  
  
1.  <span data-ttu-id="90ff6-127">在对象资源管理器中，连接到数据库引擎实例，然后展开该实例。</span><span class="sxs-lookup"><span data-stu-id="90ff6-127">In Object Explorer, connect to an instance of the Database Engine, and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="90ff6-128">在工具栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="90ff6-128">On the toolbar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="90ff6-129">在查询窗口中，使用[sp_post_msx_operation &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-post-msx-operation-transact-sql)系统存储过程设置目标服务器的轮询间隔。</span><span class="sxs-lookup"><span data-stu-id="90ff6-129">In the query window, use the [sp_post_msx_operation &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-post-msx-operation-transact-sql) system stored procedure to set the polling interval for target servers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90ff6-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="90ff6-130">See Also</span></span>  
 [<span data-ttu-id="90ff6-131">dbo.sysdownloadlist &#40;Transact-sql&#41;</span><span class="sxs-lookup"><span data-stu-id="90ff6-131">dbo.sysdownloadlist &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-tables/dbo-sysdownloadlist-transact-sql)  
  
  
