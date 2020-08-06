---
title: “清除历史记录”任务（维护计划）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.maint.historycleanup.f1
helpviewer_keywords:
- History Cleanup Task dialog box
ms.assetid: 66bb6c39-958c-4053-a27f-b1118d2567f5
ms.reviewer: ''
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 03ff35b14fc13d2b4446b15501114489b52c421e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589052"
---
# <a name="history-cleanup-task-maintenance-plan"></a><span data-ttu-id="4e547-102">“清除历史记录”任务（维护计划）</span><span class="sxs-lookup"><span data-stu-id="4e547-102">History Cleanup Task (Maintenance Plan)</span></span>

  <span data-ttu-id="4e547-103">使用 **“清除历史记录”** 对话框，可以放弃 msdb 数据库表中旧的历史信息。</span><span class="sxs-lookup"><span data-stu-id="4e547-103">Use the **History Cleanup Task** dialog to discard old historical information from tables in the msdb database.</span></span> <span data-ttu-id="4e547-104">此任务支持删除备份和还原历史记录、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理作业历史记录和维护计划历史记录。</span><span class="sxs-lookup"><span data-stu-id="4e547-104">This task supports deleting backup and restore history, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent Job history, and maintenance plan history.</span></span>  
  
 <span data-ttu-id="4e547-105">此语句使用 **sp_purge_jobhistory** 和 **sp_delete_backuphistory** 语句。</span><span class="sxs-lookup"><span data-stu-id="4e547-105">This statement uses the **sp_purge_jobhistory** and **sp_delete_backuphistory** statements.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="4e547-106">UI 元素列表</span><span class="sxs-lookup"><span data-stu-id="4e547-106">UI element list</span></span>  
 <span data-ttu-id="4e547-107">**Connection**</span><span class="sxs-lookup"><span data-stu-id="4e547-107">**Connection**</span></span>  
 <span data-ttu-id="4e547-108">选择执行此任务时使用的服务器连接。</span><span class="sxs-lookup"><span data-stu-id="4e547-108">Select the server connection to use when performing this task.</span></span>  
  
 <span data-ttu-id="4e547-109">**新建**</span><span class="sxs-lookup"><span data-stu-id="4e547-109">**New**</span></span>  
 <span data-ttu-id="4e547-110">创建一个新的服务器连接，在执行此任务时使用。</span><span class="sxs-lookup"><span data-stu-id="4e547-110">Create a new server connection to use when performing this task.</span></span> <span data-ttu-id="4e547-111">本主题后面将介绍 **“新建连接”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="4e547-111">The **New Connection** dialog box is described later in this topic.</span></span>  
  
 <span data-ttu-id="4e547-112">**备份和还原历史记录**</span><span class="sxs-lookup"><span data-stu-id="4e547-112">**Backup and restore history**</span></span>  
 <span data-ttu-id="4e547-113">当您希望还原数据库时，保留有关最近备份创建时间的记录可帮助 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 创建恢复计划。</span><span class="sxs-lookup"><span data-stu-id="4e547-113">Retaining records of when recent backups were created can help [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] create a recovery plan when you want to restore a database.</span></span> <span data-ttu-id="4e547-114">保持期应当至少为完整数据库备份的频率。</span><span class="sxs-lookup"><span data-stu-id="4e547-114">The retention period should be at least the frequency of full database back ups.</span></span>  
  
 <span data-ttu-id="4e547-115">**SQL Server 代理作业历史记录**</span><span class="sxs-lookup"><span data-stu-id="4e547-115">**SQL Server Agent Job history**</span></span>  
 <span data-ttu-id="4e547-116">使用此历史记录有助于排除失败作业的故障，或者确定数据库操作发生的原因。</span><span class="sxs-lookup"><span data-stu-id="4e547-116">This history can help you troubleshoot failed jobs, or determine why database actions occurred.</span></span>  
  
 <span data-ttu-id="4e547-117">**维护计划历史记录**</span><span class="sxs-lookup"><span data-stu-id="4e547-117">**Maintenance plan history**</span></span>  
 <span data-ttu-id="4e547-118">使用此历史记录有助于排除失败的维护计划作业的故障，或者确定数据库操作发生的原因。</span><span class="sxs-lookup"><span data-stu-id="4e547-118">This history can help you troubleshoot failed maintenance plan jobs, or determine why database actions occurred.</span></span>  
  
 <span data-ttu-id="4e547-119">**删除历史数据，如果其保留时间超过**</span><span class="sxs-lookup"><span data-stu-id="4e547-119">**Remove historical data older than**</span></span>  
 <span data-ttu-id="4e547-120">指定要删除项的保留时间。</span><span class="sxs-lookup"><span data-stu-id="4e547-120">Specify age of items that you want to delete.</span></span>  
  
 <span data-ttu-id="4e547-121">**查看 T-SQL**</span><span class="sxs-lookup"><span data-stu-id="4e547-121">**View T-SQL**</span></span>  
 <span data-ttu-id="4e547-122">根据所选选项，查看针对此任务的服务器执行的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句。</span><span class="sxs-lookup"><span data-stu-id="4e547-122">View the [!INCLUDE[tsql](../../includes/tsql-md.md)] statements performed against the server for this task, based on the selected options.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4e547-123">当受影响的对象很多时，可能需要相当长的时间才可显示。</span><span class="sxs-lookup"><span data-stu-id="4e547-123">When the number of objects affected is large, this display can take a considerable amount of time.</span></span>  
  
## <a name="new-connection-dialog-box"></a><span data-ttu-id="4e547-124">“新建连接”对话框</span><span class="sxs-lookup"><span data-stu-id="4e547-124">New Connection Dialog Box</span></span>  
 <span data-ttu-id="4e547-125">**连接名称**</span><span class="sxs-lookup"><span data-stu-id="4e547-125">**Connection name**</span></span>  
 <span data-ttu-id="4e547-126">输入新连接的名称。</span><span class="sxs-lookup"><span data-stu-id="4e547-126">Enter a name for the new connection.</span></span>  
  
 <span data-ttu-id="4e547-127">**选择或输入服务器名称**</span><span class="sxs-lookup"><span data-stu-id="4e547-127">**Select or enter a server name**</span></span>  
 <span data-ttu-id="4e547-128">选择执行此任务时所要连接的服务器。</span><span class="sxs-lookup"><span data-stu-id="4e547-128">Select a server to connect to when performing this task.</span></span>  
  
 <span data-ttu-id="4e547-129">**“刷新”**</span><span class="sxs-lookup"><span data-stu-id="4e547-129">**Refresh**</span></span>  
 <span data-ttu-id="4e547-130">刷新可用服务器的列表。</span><span class="sxs-lookup"><span data-stu-id="4e547-130">Refresh the list of available servers.</span></span>  
  
 <span data-ttu-id="4e547-131">**输入登录服务器所需的信息**</span><span class="sxs-lookup"><span data-stu-id="4e547-131">**Enter information to log on to the server**</span></span>  
 <span data-ttu-id="4e547-132">指定如何对服务器进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="4e547-132">Specify how to authenticate against the server.</span></span>  
  
 <span data-ttu-id="4e547-133">**使用 Windows 集成安全性**</span><span class="sxs-lookup"><span data-stu-id="4e547-133">**Use Windows integrated security**</span></span>  
 <span data-ttu-id="4e547-134">使用 Microsoft Windows 身份验证连接到 SQL Server [!INCLUDE[ssDE](../../includes/ssde-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="4e547-134">Connect to an instance of the SQL Server [!INCLUDE[ssDE](../../includes/ssde-md.md)] with Microsoft Windows Authentication.</span></span>  
  
 <span data-ttu-id="4e547-135">**使用特定用户名和密码**</span><span class="sxs-lookup"><span data-stu-id="4e547-135">**Use a specific user name and password**</span></span>  
 <span data-ttu-id="4e547-136">使用 SQL Server 身份验证连接到 SQL Server [!INCLUDE[ssDE](../../includes/ssde-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="4e547-136">Connect to an instance of the SQL Server [!INCLUDE[ssDE](../../includes/ssde-md.md)] using SQL Server Authentication.</span></span> <span data-ttu-id="4e547-137">此选项不可用。</span><span class="sxs-lookup"><span data-stu-id="4e547-137">This option is not available.</span></span>  
  
 <span data-ttu-id="4e547-138">**用户名**</span><span class="sxs-lookup"><span data-stu-id="4e547-138">**User name**</span></span>  
 <span data-ttu-id="4e547-139">提供一个在进行身份验证时要使用的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名。</span><span class="sxs-lookup"><span data-stu-id="4e547-139">Provide a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login to use when authenticating.</span></span> <span data-ttu-id="4e547-140">此选项不可用。</span><span class="sxs-lookup"><span data-stu-id="4e547-140">This option is not available.</span></span>  
  
 <span data-ttu-id="4e547-141">**密码**</span><span class="sxs-lookup"><span data-stu-id="4e547-141">**Password**</span></span>  
 <span data-ttu-id="4e547-142">提供一个在进行身份验证时要使用的密码。</span><span class="sxs-lookup"><span data-stu-id="4e547-142">Provide a password to use when authenticating.</span></span> <span data-ttu-id="4e547-143">此选项不可用。</span><span class="sxs-lookup"><span data-stu-id="4e547-143">This option is not available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e547-144">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4e547-144">See Also</span></span>  
 <span data-ttu-id="4e547-145">[sp_purge_jobhistory (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-purge-jobhistory-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="4e547-145">[sp_purge_jobhistory &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-purge-jobhistory-transact-sql) </span></span>  
 [<span data-ttu-id="4e547-146">sp_delete_backuphistory (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="4e547-146">sp_delete_backuphistory &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-delete-backuphistory-transact-sql)  
  
  
