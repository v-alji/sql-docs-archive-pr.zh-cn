---
title: 查看或配置远程服务器连接选项 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- remote servers [SQL Server], connection options
- servers [SQL Server], remote
- connections [SQL Server], remote servers
ms.assetid: 356d3e6b-8514-4bd2-a683-9de147949b2b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 73fe5e484d62cde025d1a560937e8cbcf5ec361d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688188"
---
# <a name="view-or-configure-remote-server-connection-options-sql-server"></a><span data-ttu-id="a475b-102">查看或配置远程服务器连接选项 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="a475b-102">View or Configure Remote Server Connection Options (SQL Server)</span></span>
  <span data-ttu-id="a475b-103">本主题说明如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中在服务器级别查看或配置远程服务器连接选项。</span><span class="sxs-lookup"><span data-stu-id="a475b-103">This topic describes how to view or configure remote server connection options at the server level in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="a475b-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="a475b-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="a475b-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="a475b-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="a475b-106">安全性</span><span class="sxs-lookup"><span data-stu-id="a475b-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="a475b-107">**若要查看或配置远程服务器连接选项，请使用：**</span><span class="sxs-lookup"><span data-stu-id="a475b-107">**To view or configure remote server connection options, using:**</span></span>  
  
     [<span data-ttu-id="a475b-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="a475b-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="a475b-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="a475b-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="a475b-110">**跟进：** [在配置远程服务器连接选项之后](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="a475b-110">**Follow Up:**  [After you configure remote server connection options](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="a475b-111">开始之前</span><span class="sxs-lookup"><span data-stu-id="a475b-111">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="a475b-112">Security</span><span class="sxs-lookup"><span data-stu-id="a475b-112">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="a475b-113">权限</span><span class="sxs-lookup"><span data-stu-id="a475b-113">Permissions</span></span>  
 <span data-ttu-id="a475b-114">执行 **sp_serveroption** 要求服务器上的 ALTER ANY LINKED SERVER 权限。</span><span class="sxs-lookup"><span data-stu-id="a475b-114">Executing **sp_serveroption** requires ALTER ANY LINKED SERVER permission on the server.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="a475b-115">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="a475b-115">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-or-configure-remote-server-connection-options"></a><span data-ttu-id="a475b-116">查看或配置远程服务器连接选项</span><span class="sxs-lookup"><span data-stu-id="a475b-116">To view or configure remote server connection options</span></span>  
  
1.  <span data-ttu-id="a475b-117">在“对象资源管理器”中，右键单击服务器，再单击“属性” 。</span><span class="sxs-lookup"><span data-stu-id="a475b-117">In Object Explorer, right-click a server, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="a475b-118">在“SQL Server 属性 - \<***server_name***>”对话框中，单击“连接”。</span><span class="sxs-lookup"><span data-stu-id="a475b-118">In the **SQL Server Properties - \<***server_name***>** dialog box, click **Connections**.</span></span>  
  
3.  <span data-ttu-id="a475b-119">在 **“连接”** 页上，查看 **“远程服务器连接”** 设置，并根据需要进行修改。</span><span class="sxs-lookup"><span data-stu-id="a475b-119">On the **Connections** page, review the **Remote server connections** settings, and modify them if necessary.</span></span>  
  
4.  <span data-ttu-id="a475b-120">在远程服务器对的另一台服务器上重复步骤 1 到 3。</span><span class="sxs-lookup"><span data-stu-id="a475b-120">Repeat steps 1 through 3 on the other server of the remote server pair.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="a475b-121">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="a475b-121">Using Transact-SQL</span></span>  
  
#### <a name="to-view-remote-server-connection-options"></a><span data-ttu-id="a475b-122">查看远程服务器连接选项</span><span class="sxs-lookup"><span data-stu-id="a475b-122">To view remote server connection options</span></span>  
  
1.  <span data-ttu-id="a475b-123">连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="a475b-123">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="a475b-124">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="a475b-124">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="a475b-125">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="a475b-125">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="a475b-126">此示例使用 [sp_helpserver](/sql/relational-databases/system-stored-procedures/sp-helpserver-transact-sql) 返回有关所有远程服务器的信息。</span><span class="sxs-lookup"><span data-stu-id="a475b-126">This example uses [sp_helpserver](/sql/relational-databases/system-stored-procedures/sp-helpserver-transact-sql) to return information about all remote servers.</span></span>  
  
```sql  
USE master;  
GO  
EXEC sp_helpserver ;  
```  
  
#### <a name="to-configure-remote-server-connection-options"></a><span data-ttu-id="a475b-127">配置远程服务器连接选项</span><span class="sxs-lookup"><span data-stu-id="a475b-127">To configure remote server connection options</span></span>  
  
1.  <span data-ttu-id="a475b-128">连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="a475b-128">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="a475b-129">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="a475b-129">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="a475b-130">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="a475b-130">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="a475b-131">本示例显示如何使用 [sp_serveroption](/sql/relational-databases/system-stored-procedures/sp-serveroption-transact-sql) 配置远程服务器。</span><span class="sxs-lookup"><span data-stu-id="a475b-131">This example shows how to use [sp_serveroption](/sql/relational-databases/system-stored-procedures/sp-serveroption-transact-sql) to configure a remote server.</span></span> <span data-ttu-id="a475b-132">该示例配置与另一个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例（即 `SEATTLE3`）相对应的远程服务器，使其排序规则与本地 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例兼容。</span><span class="sxs-lookup"><span data-stu-id="a475b-132">The example configures a remote server corresponding to another instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], `SEATTLE3`, to be collation compatible with the local instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
```sql  
USE master;  
EXEC sp_serveroption 'SEATTLE3', 'collation compatible', 'true';  
```  
  
##  <a name="follow-up-after-you-configure-remote-server-connection-options"></a><a name="FollowUp"></a> <span data-ttu-id="a475b-133">跟进：在配置远程服务器连接选项之后</span><span class="sxs-lookup"><span data-stu-id="a475b-133">Follow Up: After you configure remote server connection options</span></span>  
 <span data-ttu-id="a475b-134">必须停止后再重新启动远程服务器，设置才会生效。</span><span class="sxs-lookup"><span data-stu-id="a475b-134">The remote server must be stopped and restarted before the setting can take effect.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a475b-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a475b-135">See Also</span></span>  
 <span data-ttu-id="a475b-136">[服务器配置选项 (SQL Server)](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="a475b-136">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="a475b-137">[远程服务器](remote-servers.md) </span><span class="sxs-lookup"><span data-stu-id="a475b-137">[Remote Servers](remote-servers.md) </span></span>  
 <span data-ttu-id="a475b-138">[链接服务器（数据库引擎）](../../relational-databases/linked-servers/linked-servers-database-engine.md) </span><span class="sxs-lookup"><span data-stu-id="a475b-138">[Linked Servers &#40;Database Engine&#41;](../../relational-databases/linked-servers/linked-servers-database-engine.md) </span></span>  
 <span data-ttu-id="a475b-139">[sp_linkedservers (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-linkedservers-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a475b-139">[sp_linkedservers &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-linkedservers-transact-sql) </span></span>  
 <span data-ttu-id="a475b-140">[sp_helpserver (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-helpserver-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a475b-140">[sp_helpserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpserver-transact-sql) </span></span>  
 [<span data-ttu-id="a475b-141">sp_serveroption (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="a475b-141">sp_serveroption &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-serveroption-transact-sql)  
  
  
