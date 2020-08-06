---
title: 删除数据库镜像 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- database mirroring [SQL Server], removing
- removing database mirroring [SQL Server]
ms.assetid: bbc4d7f7-3bc7-40d6-a822-af195fe7f8c0
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 19c1d0449fa1c7434aeaf9c51e3b2dc7bc6b68c0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690111"
---
# <a name="remove-database-mirroring-sql-server"></a><span data-ttu-id="61a05-102">删除数据库镜像 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="61a05-102">Remove Database Mirroring (SQL Server)</span></span>
  <span data-ttu-id="61a05-103">本主题说明如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中从数据库删除数据库镜像。</span><span class="sxs-lookup"><span data-stu-id="61a05-103">This topic describes how to remove database mirroring from a database in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  <span data-ttu-id="61a05-104">数据库所有者可以随时通过从数据库中删除镜像来手动停止数据库镜像会话。</span><span class="sxs-lookup"><span data-stu-id="61a05-104">At any time, the database owner can manually stop a database mirroring session by removing mirroring from the database.</span></span>  
  
 
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="61a05-105">开始之前</span><span class="sxs-lookup"><span data-stu-id="61a05-105">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="61a05-106">Security</span><span class="sxs-lookup"><span data-stu-id="61a05-106">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="61a05-107">权限</span><span class="sxs-lookup"><span data-stu-id="61a05-107">Permissions</span></span>  
 <span data-ttu-id="61a05-108">需要对数据库拥有 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="61a05-108">Requires ALTER permission on the database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="61a05-109">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="61a05-109">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-remove-database-mirroring"></a><span data-ttu-id="61a05-110">删除数据库镜像</span><span class="sxs-lookup"><span data-stu-id="61a05-110">To remove database mirroring</span></span>  
  
1.  <span data-ttu-id="61a05-111">在数据库镜像会话期间，连接到主体服务器实例，然后在对象资源管理器中，单击服务器名称以展开服务器树。</span><span class="sxs-lookup"><span data-stu-id="61a05-111">During a database mirroring session, connect to the principal server instance, in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="61a05-112">展开 **“数据库”** 并选择数据库。</span><span class="sxs-lookup"><span data-stu-id="61a05-112">Expand **Databases**, and select the database.</span></span>  
  
3.  <span data-ttu-id="61a05-113">右键单击数据库，选择 **“任务”** ，再单击 **“镜像”** 。</span><span class="sxs-lookup"><span data-stu-id="61a05-113">Right-click the database, select **Tasks**, and then click **Mirror**.</span></span> <span data-ttu-id="61a05-114">这样便可打开 **“数据库属性”** 对话框的 **“镜像”** 页。</span><span class="sxs-lookup"><span data-stu-id="61a05-114">This opens the **Mirroring** page of the **Database Properties** dialog box.</span></span>  
  
4.  <span data-ttu-id="61a05-115">在 **“选择页”** 窗格中，单击 **“镜像”** 。</span><span class="sxs-lookup"><span data-stu-id="61a05-115">In the **Select a Page** pane, click **Mirroring**.</span></span>  
  
5.  <span data-ttu-id="61a05-116">若要删除镜像，请单击 **“删除镜像”** 。</span><span class="sxs-lookup"><span data-stu-id="61a05-116">To remove mirroring, click **Remove Mirroring**.</span></span> <span data-ttu-id="61a05-117">此时，将显示一个提示，要求您进行确认。</span><span class="sxs-lookup"><span data-stu-id="61a05-117">A prompt asks for confirmation.</span></span> <span data-ttu-id="61a05-118">如果单击 **“是”** ，会话将停止，并从数据库中删除镜像。</span><span class="sxs-lookup"><span data-stu-id="61a05-118">If you click **Yes**, the session is stopped and mirroring is removed from the database.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="61a05-119">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="61a05-119">Using Transact-SQL</span></span>  
 <span data-ttu-id="61a05-120">若要删除数据库镜像，请使用 **“数据库属性”** ，</span><span class="sxs-lookup"><span data-stu-id="61a05-120">To remove database mirroring, use the **Database Properties**.</span></span> <span data-ttu-id="61a05-121">即使用 **“数据库属性”** 对话框的 **“镜像”** 页。</span><span class="sxs-lookup"><span data-stu-id="61a05-121">use the **Mirroring** page of the **Database Properties** dialog box.</span></span>  
  
#### <a name="to-remove-database-mirroring"></a><span data-ttu-id="61a05-122">删除数据库镜像</span><span class="sxs-lookup"><span data-stu-id="61a05-122">To remove database mirroring</span></span>  
  
1.  <span data-ttu-id="61a05-123">为任一镜像伙伴连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="61a05-123">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)] of either mirroring partner.</span></span>  
  
2.  <span data-ttu-id="61a05-124">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="61a05-124">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="61a05-125">发出以下 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句：</span><span class="sxs-lookup"><span data-stu-id="61a05-125">Issue the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement:</span></span>  
  
    ```  
    ALTER DATABASE database_name SET PARTNER OFF  
    ```  
  
     <span data-ttu-id="61a05-126">其中 *database_name* 是要删除其会话的镜像数据库。</span><span class="sxs-lookup"><span data-stu-id="61a05-126">where *database_name* is the mirrored database whose session you want to remove.</span></span>  
  
     <span data-ttu-id="61a05-127">以下示例从 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 示例数据库删除数据库镜像。</span><span class="sxs-lookup"><span data-stu-id="61a05-127">The following example removes database mirroring from the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample database.</span></span>  
  
    ```  
    ALTER DATABASE AdventureWorks2012 SET PARTNER OFF;  
    ```  
  
##  <a name="follow-up-removing-database-mirroring"></a><a name="FollowUp"></a> <span data-ttu-id="61a05-128">跟进：删除数据库镜像</span><span class="sxs-lookup"><span data-stu-id="61a05-128">Follow Up: Removing Database Mirroring</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="61a05-129">有关删除镜像的影响的信息，请参阅[删除数据库镜像 (SQL Server)](database-mirroring-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="61a05-129">For information about the impact of removing mirroring, see [Removing Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md).</span></span>  
  
-   <span data-ttu-id="61a05-130">**如果您打算在数据库上重新启动镜像**</span><span class="sxs-lookup"><span data-stu-id="61a05-130">**If you intend to restart mirroring on the database**</span></span>  
  
     <span data-ttu-id="61a05-131">重新启动镜像之前，必须将在删除镜像后对主体数据库执行的日志备份全部应用到镜像数据库中。</span><span class="sxs-lookup"><span data-stu-id="61a05-131">Any log backups taken on the principal database after mirroring was removed must all be applied to the mirror database before you can restart mirroring.</span></span>  
  
-   <span data-ttu-id="61a05-132">**如果不打算重新启动镜像**</span><span class="sxs-lookup"><span data-stu-id="61a05-132">**If you do not intent to restart mirroring**</span></span>  
  
     <span data-ttu-id="61a05-133">或者，可以恢复以前的镜像数据库。</span><span class="sxs-lookup"><span data-stu-id="61a05-133">Optionally, you can recover the former mirror database.</span></span> <span data-ttu-id="61a05-134">在作为镜像服务器的服务器实例上，可以使用以下 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句：</span><span class="sxs-lookup"><span data-stu-id="61a05-134">On the server instance that was the mirror server, you can use the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement:</span></span>  
  
    ```  
    RESTORE DATABASE database_name WITH RECOVERY;  
    ```  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="61a05-135">如果恢复该数据库，则两个同名的不同数据库处于联机状态。</span><span class="sxs-lookup"><span data-stu-id="61a05-135">If you recover this database, two divergent databases with the same name are online.</span></span> <span data-ttu-id="61a05-136">因此，需要确保客户端仅可访问其中一个数据库，通常为最新的主体数据库。</span><span class="sxs-lookup"><span data-stu-id="61a05-136">Therefore, you need to ensure that clients can access only one of them-typically the most recent principal database.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="61a05-137">相关任务</span><span class="sxs-lookup"><span data-stu-id="61a05-137">Related Tasks</span></span>  
  
-   [<span data-ttu-id="61a05-138">暂停或恢复数据库镜像会话 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="61a05-138">Pause or Resume a Database Mirroring Session &#40;SQL Server&#41;</span></span>](pause-or-resume-a-database-mirroring-session-sql-server.md)  
  
-   [<span data-ttu-id="61a05-139">从数据库镜像会话删除见证服务器 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="61a05-139">Remove the Witness from a Database Mirroring Session &#40;SQL Server&#41;</span></span>](remove-the-witness-from-a-database-mirroring-session-sql-server.md)  
  
-   [<span data-ttu-id="61a05-140">使用 Windows 身份验证建立数据库镜像会话 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="61a05-140">Establish a Database Mirroring Session Using Windows Authentication &#40;SQL Server Management Studio&#41;</span></span>](establish-database-mirroring-session-windows-authentication.md)  
  
-   [<span data-ttu-id="61a05-141">使用 Windows 身份验证建立数据库镜像会话 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="61a05-141">Establish a Database Mirroring Session Using Windows Authentication &#40;Transact-SQL&#41;</span></span>](database-mirroring-establish-session-windows-authentication.md)  
  
-   [<span data-ttu-id="61a05-142">示例：使用证书设置数据库镜像 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="61a05-142">Example: Setting Up Database Mirroring Using Certificates &#40;Transact-SQL&#41;</span></span>](example-setting-up-database-mirroring-using-certificates-transact-sql.md)  
  
## <a name="see-also"></a><span data-ttu-id="61a05-143">另请参阅</span><span class="sxs-lookup"><span data-stu-id="61a05-143">See Also</span></span>  
 <span data-ttu-id="61a05-144">[数据库镜像 (SQL Server)](database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="61a05-144">[Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span></span>  
 <span data-ttu-id="61a05-145">[设置数据库镜像 (SQL Server)](setting-up-database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="61a05-145">[Setting Up Database Mirroring &#40;SQL Server&#41;](setting-up-database-mirroring-sql-server.md) </span></span>  
 [<span data-ttu-id="61a05-146">AlwaysOn 可用性组 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="61a05-146">AlwaysOn Availability Groups (SQL Server)</span></span>](../availability-groups/windows/always-on-availability-groups-sql-server.md)  
  
  
