---
title: 打开活动监视器 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Activity Monitor [SQL Server], setting the refresh interval
- refresh interval for Activity Monitor
- Activity Monitor [SQL Server], opening
- opening Activity Monitor
ms.assetid: 0a6eeb16-f02b-479d-9a60-543e40ebf46b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: ea74122ad18a0a1ede5eef1e09684606ca0ce073
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692857"
---
# <a name="open-activity-monitor-sql-server-management-studio"></a><span data-ttu-id="a720d-102">打开活动监视器 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="a720d-102">Open Activity Monitor (SQL Server Management Studio)</span></span>
  <span data-ttu-id="a720d-103">本主题介绍如何打开活动监视器以便获取有关 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 进程的信息，并了解这些进程如何影响当前 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例。</span><span class="sxs-lookup"><span data-stu-id="a720d-103">This topic describes how to open the Activity Monitor to obtain information about [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] processes and how these processes affect the current instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="a720d-104">本主题还介绍如何设置活动监视器的刷新间隔。</span><span class="sxs-lookup"><span data-stu-id="a720d-104">It also describes how to set the refresh interval of the Activity Monitor.</span></span>  
  
 <span data-ttu-id="a720d-105">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="a720d-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="a720d-106">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="a720d-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="a720d-107">安全性</span><span class="sxs-lookup"><span data-stu-id="a720d-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="a720d-108">**使用以下工具打开活动监视器：**</span><span class="sxs-lookup"><span data-stu-id="a720d-108">**To open the Activity Monitor using:**</span></span>  
  
     [<span data-ttu-id="a720d-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="a720d-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
-   <span data-ttu-id="a720d-110">**使用以下工具设置刷新间隔：**  [SQL Server Management Studio](#Refresh)</span><span class="sxs-lookup"><span data-stu-id="a720d-110">**To set the refresh interval using:**  [SQL Server Management Studio](#Refresh)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="a720d-111">开始之前</span><span class="sxs-lookup"><span data-stu-id="a720d-111">Before You Begin</span></span>  
 <span data-ttu-id="a720d-112">活动监视器将在被监视的实例上运行查询以获取有关活动监视器显示窗格的信息。</span><span class="sxs-lookup"><span data-stu-id="a720d-112">Activity Monitor runs queries on the monitored instance to obtain information for the Activity Monitor display panes.</span></span> <span data-ttu-id="a720d-113">当刷新间隔设置为小于 10 秒时，运行这些查询所用的时间可能会对服务器性能产生影响。</span><span class="sxs-lookup"><span data-stu-id="a720d-113">When the refresh interval is set to less than 10 seconds, the time that is used to run these queries can affect server performance</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="a720d-114">Security</span><span class="sxs-lookup"><span data-stu-id="a720d-114">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="a720d-115">权限</span><span class="sxs-lookup"><span data-stu-id="a720d-115">Permissions</span></span>  
 <span data-ttu-id="a720d-116">若要查看活动监视器，用户必须拥有 VIEW SERVER STATE 权限。</span><span class="sxs-lookup"><span data-stu-id="a720d-116">To view the Activity Monitor, a user must have VIEW SERVER STATE permission.</span></span> <span data-ttu-id="a720d-117">若要查看活动监视器的“数据文件 I/O”部分，除了 VIEW SERVER STATE 之外，您还必须具有 CREATE DATABASE、ALTER ANY DATABASE 或 VIEW ANY DEFINITION 权限。</span><span class="sxs-lookup"><span data-stu-id="a720d-117">To view the Data File I/O section of Activity Monitor, you must have CREATE DATABASE, ALTER ANY DATABASE, or VIEW ANY DEFINITION permission in addition to VIEW SERVER STATE.</span></span>  
  
 <span data-ttu-id="a720d-118">若要终止进程，用户必须是 sysadmin 或 processadmin 固定服务器角色的成员。</span><span class="sxs-lookup"><span data-stu-id="a720d-118">To KILL a process, a user must be a member of the sysadmin or processadmin fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="a720d-119">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="a720d-119">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-open-activity-monitor-in-sql-server-management-studio"></a><span data-ttu-id="a720d-120">打开 SQL Server Management Studio 中的活动监视器</span><span class="sxs-lookup"><span data-stu-id="a720d-120">To open Activity Monitor in SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="a720d-121">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 标准工具栏上，单击 **“活动监视器”**。</span><span class="sxs-lookup"><span data-stu-id="a720d-121">On the [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] standard toolbar, click **Activity Monitor**.</span></span>  
  
2.  <span data-ttu-id="a720d-122">在 **“连接到服务器”** 对话框中，选择服务器名和身份验证模式，然后单击 **“连接”**。</span><span class="sxs-lookup"><span data-stu-id="a720d-122">In the **Connect to Server** dialog box, select the server name and authentication mode, and then click **Connect**.</span></span>  
  
 <span data-ttu-id="a720d-123">还可随时通过按 CTRL+ALT A 打开活动监视器。</span><span class="sxs-lookup"><span data-stu-id="a720d-123">You can also open Activity Monitor at any time by pressing CTRL+ALT A.</span></span>  
  
#### <a name="to-open-activity-monitor-in-object-explorer"></a><span data-ttu-id="a720d-124">在对象资源管理器中打开活动监视器</span><span class="sxs-lookup"><span data-stu-id="a720d-124">To open Activity Monitor in Object Explorer</span></span>  
  
-   <span data-ttu-id="a720d-125">在对象资源管理器中，右键单击实例名称，然后选择 "**活动监视器**"。</span><span class="sxs-lookup"><span data-stu-id="a720d-125">In Object Explorer, right-click the instance name, and then select **Activity Monitor**.</span></span>  
  
#### <a name="to-open-activity-monitor-when-opening-sql-server-management-studio"></a><span data-ttu-id="a720d-126">在打开 SQL Server Management Studio 时打开活动监视器</span><span class="sxs-lookup"><span data-stu-id="a720d-126">To open Activity Monitor when opening SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="a720d-127">在“工具”  菜单上，单击“选项”  。</span><span class="sxs-lookup"><span data-stu-id="a720d-127">On the **Tools** menu, click **Options**.</span></span>  
  
2.  <span data-ttu-id="a720d-128">在 **“选项”** 对话框中，展开 **“环境”**，再选择 **“常规”**。</span><span class="sxs-lookup"><span data-stu-id="a720d-128">In the **Options** dialog box, expand **Environment**, and then select **General**.</span></span>  
  
3.  <span data-ttu-id="a720d-129">在 **“启动时”** 框中，选择 **“打开对象资源管理器和活动监视器”**。</span><span class="sxs-lookup"><span data-stu-id="a720d-129">In the **At startup** box, select **Open Object Explorer and Activity Monitor**.</span></span>  
  
4.  <span data-ttu-id="a720d-130">若要激活更改，请先关闭再重新打开 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="a720d-130">To activate the changes, close and reopen [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
###  <a name="to-set-the-activity-monitor-refresh-interval"></a><a name="Refresh"></a><span data-ttu-id="a720d-131">设置活动监视器刷新间隔</span><span class="sxs-lookup"><span data-stu-id="a720d-131">To Set the Activity Monitor Refresh Interval</span></span>  
  
-   <span data-ttu-id="a720d-132">打开活动监视器。</span><span class="sxs-lookup"><span data-stu-id="a720d-132">Open the Activity Monitor.</span></span>  
  
-   <span data-ttu-id="a720d-133">右键单击“概述”，选择“刷新间隔”，然后选择活动监视器获取新实例信息所用的间隔。</span><span class="sxs-lookup"><span data-stu-id="a720d-133">Right-click **Overview**, select **Refresh Interval**, and then select the interval in which Activity Monitor should obtain new instance information.</span></span>  
  
  
