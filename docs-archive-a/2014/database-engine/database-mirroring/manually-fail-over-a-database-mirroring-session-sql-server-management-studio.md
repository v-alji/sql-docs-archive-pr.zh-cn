---
title: 手动故障转移数据库镜像会话 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- failover [SQL Server], database mirroring
- manual failover [SQL Server]
- database mirroring [SQL Server], failover
ms.assetid: 4ecf9c63-b3a4-4c54-b553-5bc37973232b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 7f7f4547058b2dfd4229142dca73a7d9b4bdb239
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694116"
---
# <a name="manually-fail-over-a-database-mirroring-session-sql-server-management-studio"></a><span data-ttu-id="3a1cb-102">手动故障转移数据库镜像会话 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="3a1cb-102">Manually Fail Over a Database Mirroring Session (SQL Server Management Studio)</span></span>
  <span data-ttu-id="3a1cb-103">同步镜像数据库时（即数据库处于 SYNCHRONIZED 状态时），数据库所有者可以启动到镜像服务器的手动故障转移。</span><span class="sxs-lookup"><span data-stu-id="3a1cb-103">When the mirrored database is synchronized (that is, when the database is in the SYNCHRONIZED state), the database owner can initiate manual failover to the mirror server.</span></span>  
  
 <span data-ttu-id="3a1cb-104">在手动故障转移过程中，将交换发生故障转移的数据库的主体服务器和镜像服务器的角色。</span><span class="sxs-lookup"><span data-stu-id="3a1cb-104">During a manual failover, the principal and mirror server roles are swapped for the database on which the failover occurs.</span></span> <span data-ttu-id="3a1cb-105">镜像数据库变成主体数据库，而主体数据库变成镜像数据库。</span><span class="sxs-lookup"><span data-stu-id="3a1cb-105">The mirror database becomes the principal database and the principal database becomes the mirror.</span></span> <span data-ttu-id="3a1cb-106">例如，下表显示了手动故障转移如何交换下面两个镜像伙伴的角色： `SQLDBENGINE0_1` 和 `SQLDBENGINE0_2`。</span><span class="sxs-lookup"><span data-stu-id="3a1cb-106">For example, the following table shows the how a manual failover swaps the roles of two mirroring partners: `SQLDBENGINE0_1` and `SQLDBENGINE0_2`.</span></span>  
  
|<span data-ttu-id="3a1cb-107">服务器</span><span class="sxs-lookup"><span data-stu-id="3a1cb-107">Server</span></span>|<span data-ttu-id="3a1cb-108">在故障转移之前</span><span class="sxs-lookup"><span data-stu-id="3a1cb-108">Before failover</span></span>|<span data-ttu-id="3a1cb-109">在故障转移之后</span><span class="sxs-lookup"><span data-stu-id="3a1cb-109">After failover</span></span>|  
|------------|---------------------|--------------------|  
|`SQLDBENGINE0_1`|<span data-ttu-id="3a1cb-110">PRINCIPAL</span><span class="sxs-lookup"><span data-stu-id="3a1cb-110">PRINCIPAL</span></span>|<span data-ttu-id="3a1cb-111">MIRROR</span><span class="sxs-lookup"><span data-stu-id="3a1cb-111">MIRROR</span></span>|  
|`SQLDBENGINE0_2`|<span data-ttu-id="3a1cb-112">MIRROR</span><span class="sxs-lookup"><span data-stu-id="3a1cb-112">MIRROR</span></span>|<span data-ttu-id="3a1cb-113">PRINCIPAL</span><span class="sxs-lookup"><span data-stu-id="3a1cb-113">PRINCIPAL</span></span>|  
  
 <span data-ttu-id="3a1cb-114">注意，其他数据库镜像会话的服务器角色不会受到影响。</span><span class="sxs-lookup"><span data-stu-id="3a1cb-114">Note that the server roles for other database mirroring sessions are not affected.</span></span> <span data-ttu-id="3a1cb-115">有关详细信息，请参阅 [数据库镜像会话期间的角色切换 (SQL Server)](role-switching-during-a-database-mirroring-session-sql-server.md)的各版本中均未提供见证服务器实例。</span><span class="sxs-lookup"><span data-stu-id="3a1cb-115">For more information, see [Role Switching During a Database Mirroring Session &#40;SQL Server&#41;](role-switching-during-a-database-mirroring-session-sql-server.md).</span></span>  
  
### <a name="to-manually-fail-over-database-mirroring"></a><span data-ttu-id="3a1cb-116">对数据库镜像进行手动故障转移</span><span class="sxs-lookup"><span data-stu-id="3a1cb-116">To manually fail over database mirroring</span></span>  
  
1.  <span data-ttu-id="3a1cb-117">连接至主体服务器实例，在 **对象资源管理器** 窗格中，单击服务器名称以展开服务器树。</span><span class="sxs-lookup"><span data-stu-id="3a1cb-117">Connect to the principal server instance and, in the **Object Explorer** pane, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="3a1cb-118">展开 **“数据库”** ，再选择要进行故障转移的数据库。</span><span class="sxs-lookup"><span data-stu-id="3a1cb-118">Expand **Databases**, and select the database to be failed over.</span></span>  
  
3.  <span data-ttu-id="3a1cb-119">右键单击数据库，选择 **“任务”** ，再单击 **“镜像”** 。</span><span class="sxs-lookup"><span data-stu-id="3a1cb-119">Right-click the database, select **Tasks**, and then click **Mirror**.</span></span> <span data-ttu-id="3a1cb-120">这样便可打开 **“数据库属性”** 对话框的 **“镜像”** 页。</span><span class="sxs-lookup"><span data-stu-id="3a1cb-120">This opens the **Mirroring** page of the **Database Properties** dialog box.</span></span>  
  
4.  <span data-ttu-id="3a1cb-121">单击 **“故障转移”** 。</span><span class="sxs-lookup"><span data-stu-id="3a1cb-121">Click **Failover**.</span></span>  
  
     <span data-ttu-id="3a1cb-122">将显示一个确认框。</span><span class="sxs-lookup"><span data-stu-id="3a1cb-122">A confirmation box appears.</span></span>  <span data-ttu-id="3a1cb-123">主体服务器将开始尝试使用 Windows 身份验证连接到镜像服务器。</span><span class="sxs-lookup"><span data-stu-id="3a1cb-123">The principal server begins by trying to connect to the mirror server by using Windows Authentication.</span></span> <span data-ttu-id="3a1cb-124">如果 Windows 身份验证无效，主体服务器将显示 **“连接到服务器”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="3a1cb-124">If Windows Authentication does not work, the principal server displays the **Connect to Server** dialog box.</span></span> <span data-ttu-id="3a1cb-125">如果镜像服务器使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证，请选择 **“身份验证”** 框中的 **“SQL Server 身份验证”** 。</span><span class="sxs-lookup"><span data-stu-id="3a1cb-125">If the mirror server uses [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication, select **SQL Server Authentication** in the **Authentication** box.</span></span> <span data-ttu-id="3a1cb-126">在 **“登录名”** 文本框中，指定连接镜像服务器时使用的登录帐户，然后在 **“密码”** 文本框中指定该帐户的密码。</span><span class="sxs-lookup"><span data-stu-id="3a1cb-126">In the **Login** text box, specify the login account to connect with on the mirror server, and in the **Password** text box, specify the password for that account.</span></span>  
  
     <span data-ttu-id="3a1cb-127">如果故障转移成功， **“数据库属性”** 对话框关闭。</span><span class="sxs-lookup"><span data-stu-id="3a1cb-127">If failover succeeds, the **Database Properties** dialog box closes.</span></span> <span data-ttu-id="3a1cb-128">镜像数据库变成主体数据库，而主体数据库变成镜像数据库。</span><span class="sxs-lookup"><span data-stu-id="3a1cb-128">The mirror database becomes the principal database and the principal database becomes the mirror.</span></span>  
  
     <span data-ttu-id="3a1cb-129">如果故障转移失败，将显示一条错误消息，并且该对话框保持打开状态。</span><span class="sxs-lookup"><span data-stu-id="3a1cb-129">If failover fails, an error message is displayed and the dialog box remains open.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="3a1cb-130">如果打开“镜像”页后修改了某些属性，将不保存这些更改。</span><span class="sxs-lookup"><span data-stu-id="3a1cb-130">If you have modified any properties since opening the **Mirroring** page, those changes will not be saved.</span></span>  
  
     <span data-ttu-id="3a1cb-131">对话框将自动关闭。</span><span class="sxs-lookup"><span data-stu-id="3a1cb-131">The dialog box closes automatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a1cb-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3a1cb-132">See Also</span></span>  
 <span data-ttu-id="3a1cb-133">[数据库属性（“镜像”页）](../../relational-databases/databases/database-properties-mirroring-page.md) </span><span class="sxs-lookup"><span data-stu-id="3a1cb-133">[Database Properties &#40;Mirroring Page&#41;](../../relational-databases/databases/database-properties-mirroring-page.md) </span></span>  
 <span data-ttu-id="3a1cb-134">[数据库镜像 (SQL Server)](database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="3a1cb-134">[Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span></span>  
 <span data-ttu-id="3a1cb-135">[手动故障转移数据库镜像会话 (Transact-SQL)](manually-fail-over-a-database-mirroring-session-transact-sql.md) </span><span class="sxs-lookup"><span data-stu-id="3a1cb-135">[Manually Fail Over a Database Mirroring Session &#40;Transact-SQL&#41;](manually-fail-over-a-database-mirroring-session-transact-sql.md) </span></span>  
 <span data-ttu-id="3a1cb-136">[暂停或恢复数据库镜像会话 (SQL Server)](pause-or-resume-a-database-mirroring-session-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="3a1cb-136">[Pause or Resume a Database Mirroring Session &#40;SQL Server&#41;](pause-or-resume-a-database-mirroring-session-sql-server.md) </span></span>  
 [<span data-ttu-id="3a1cb-137">删除数据库镜像 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="3a1cb-137">Remove Database Mirroring &#40;SQL Server&#41;</span></span>](remove-database-mirroring-sql-server.md)  
  
  
