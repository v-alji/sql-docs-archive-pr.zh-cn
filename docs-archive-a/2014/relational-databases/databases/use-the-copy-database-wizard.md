---
title: 使用复制数据库向导 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.cdw.transfermethod.f1
- sql12.swb.cdw.welcome.f1
- sql12.swb.cdw.packageconfiguration.f1
- sql12.swb.cdw.schedule.f1
- sql12.swb.cdw.destination.f1
- sql12.swb.cdw.complete.f1
- sql12.swb.cdw.destinationconfiguration.f1
- sql12.swb.cdw.selectdatabaseobjects.f1
- sql12.swb.cdw.databases.f1
- sql12.swb.cdw.source.f1
- sql12.swb.cdw.locationofsourcedbfiles.f1
helpviewer_keywords:
- Copy Database Wizard
- starting Copy Database Wizard
ms.assetid: 7a999fc7-0a26-4a0d-9eeb-db6fc794f3cb
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0baaeef6cb196a67b2f615aa280b61b61fbc5119
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693379"
---
# <a name="use-the-copy-database-wizard"></a><span data-ttu-id="9ed5a-102">使用复制数据库向导</span><span class="sxs-lookup"><span data-stu-id="9ed5a-102">Use the Copy Database Wizard</span></span>
  <span data-ttu-id="9ed5a-103">通过复制数据库向导，可以方便地将数据库及其对象从一台服务器移动或复制到另一台服务器，而服务器无需停机。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-103">The Copy Database Wizard lets you move or copy databases and their objects easily from one server to another, with no server downtime.</span></span> <span data-ttu-id="9ed5a-104">还可以将数据库从以前的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 版本升级到 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-104">You can also upgrade databases from a previous [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] version to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="9ed5a-105">使用此向导可执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="9ed5a-105">By using this wizard, you can do the following:</span></span>  
  
-   <span data-ttu-id="9ed5a-106">选取源服务器和目标服务器。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-106">Pick a source and destination server.</span></span>  
  
-   <span data-ttu-id="9ed5a-107">选择要移动、复制或升级的数据库。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-107">Select databases to move, copy or upgrade.</span></span>  
  
-   <span data-ttu-id="9ed5a-108">为数据库指定文件位置。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-108">Specify the file location for the databases.</span></span>  
  
-   <span data-ttu-id="9ed5a-109">在目标服务器上创建登录名。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-109">Create logins on the destination server.</span></span>  
  
-   <span data-ttu-id="9ed5a-110">复制其他支持的对象、作业、用户定义的存储过程和错误消息。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-110">Copy additional supporting objects, jobs, user-defined stored procedures, and error messages.</span></span>  
  
-   <span data-ttu-id="9ed5a-111">计划何时移动或复制数据库。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-111">Schedule when to move or copy the databases.</span></span>  
  
 <span data-ttu-id="9ed5a-112">除了复制数据库，还可以复制关联的元数据，例如 **master** 数据库的登录名和对象，它们是复制的数据库所必需的。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-112">In addition to copying databases, you can copy associated metadata, for example, logins and objects from the **master** database that are required by a copied database.</span></span>  
  
 <span data-ttu-id="9ed5a-113">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="9ed5a-113">**In This Topic**</span></span>  
  
-   <span data-ttu-id="9ed5a-114">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="9ed5a-114">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="9ed5a-115">限制和局限</span><span class="sxs-lookup"><span data-stu-id="9ed5a-115">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="9ed5a-116">先决条件</span><span class="sxs-lookup"><span data-stu-id="9ed5a-116">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="9ed5a-117">建议</span><span class="sxs-lookup"><span data-stu-id="9ed5a-117">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="9ed5a-118">安全性</span><span class="sxs-lookup"><span data-stu-id="9ed5a-118">Security</span></span>](#Security)  
  
-   <span data-ttu-id="9ed5a-119">**使用复制数据库向导：**</span><span class="sxs-lookup"><span data-stu-id="9ed5a-119">**Using the Copy Database Wizard to:**</span></span>  
  
     [<span data-ttu-id="9ed5a-120">复制、移动或升级数据库</span><span class="sxs-lookup"><span data-stu-id="9ed5a-120">Copy, Move, or Upgrade Databases</span></span>](#Copy_Move)  
  
-   <span data-ttu-id="9ed5a-121">**跟进，在升级之后：**</span><span class="sxs-lookup"><span data-stu-id="9ed5a-121">**Follow up, after upgrade:**</span></span>  
  
     [<span data-ttu-id="9ed5a-122">在升级 SQL Server 数据库之后</span><span class="sxs-lookup"><span data-stu-id="9ed5a-122">After Upgrading a SQL Server Database</span></span>](#FollowUp)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="9ed5a-123">开始之前</span><span class="sxs-lookup"><span data-stu-id="9ed5a-123">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="9ed5a-124">限制和局限</span><span class="sxs-lookup"><span data-stu-id="9ed5a-124">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="9ed5a-125">在 Express 版本中未提供复制数据库向导。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-125">The Copy Database Wizard is not available in the Express edition.</span></span>  
  
-   <span data-ttu-id="9ed5a-126">复制数据库向导不能用于复制或移动以下数据库。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-126">The Copy Database Wizard cannot be used to copy or move the following databases.</span></span>  
  
    -   <span data-ttu-id="9ed5a-127">系统数据库</span><span class="sxs-lookup"><span data-stu-id="9ed5a-127">System databases</span></span>  
  
    -   <span data-ttu-id="9ed5a-128">为复制操作标记的数据库。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-128">Databases marked for replication.</span></span>  
  
    -   <span data-ttu-id="9ed5a-129">标记为“无法访问”、“正在加载”、“脱机”、“正在恢复”、“可疑”或处于“紧急模式”的数据库。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-129">Databases marked Inaccessible, Loading, Offline, Recovering, Suspect, or in Emergency Mode.</span></span>  
  
-   <span data-ttu-id="9ed5a-130">升级数据库后，它无法降级到以前的版本。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-130">After a database has been upgraded, it cannot be downgraded to a previous version.</span></span>  
  
-   <span data-ttu-id="9ed5a-131">如果选择 **“移动”** 选项，则在移动数据库之后，该向导将自动删除源数据库。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-131">If you select the **Move** option, the wizard deletes the source database automatically after moving the database.</span></span> <span data-ttu-id="9ed5a-132">如果选择 **“复制”** 选项，则复制数据库向导不会删除源数据库。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-132">The Copy Database Wizard does not delete a source database if you select the **Copy** option.</span></span>  
  
-   <span data-ttu-id="9ed5a-133">如果使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理对象方法移动全文目录，则必须在移动后重新填充索引。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-133">If you use the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Object method to move the full-text catalog, you must repopulate the index after the move.</span></span>  
  
-   <span data-ttu-id="9ed5a-134">分离和附加方法可分离数据库，移动或复制数据库 .mdf、.ndf、.ldf 文件，并在新的位置重新附加该数据库。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-134">The detach-and-attach method detaches the database, moves or copies the database .mdf, .ndf, .ldf files and reattaches the database in the new location.</span></span> <span data-ttu-id="9ed5a-135">对于分离和附加方法，若要避免数据丢失或不一致，不能将活动会话附加到正在移动或复制的数据库。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-135">For the detach-and-attach method, to avoid data loss or inconsistency, active sessions cannot be attached to the database being moved or copied.</span></span> <span data-ttu-id="9ed5a-136">如果存在活动会话，复制数据库向导不会执行移动或复制操作。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-136">If any active sessions exist, the Copy Database Wizard does not execute the move or copy operation.</span></span> <span data-ttu-id="9ed5a-137">对于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理对象方法，由于数据库从不会脱机，因此允许活动会话。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-137">For the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Object method, active sessions are allowed because the database is never taken offline.</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a><span data-ttu-id="9ed5a-138">先决条件</span><span class="sxs-lookup"><span data-stu-id="9ed5a-138">Prerequisites</span></span>  
 <span data-ttu-id="9ed5a-139">确保在目标服务器上启动了 SQL Server 代理。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-139">Ensure that SQL Server Agent is started on the destination server.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="9ed5a-140">建议</span><span class="sxs-lookup"><span data-stu-id="9ed5a-140">Recommendations</span></span>  
  
-   <span data-ttu-id="9ed5a-141">为了确保升级后的数据库具有最佳性能，请对升级后的数据库运行 sp_updatestats（更新统计信息）。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-141">To ensure optimal performance of an upgraded database, run sp_updatestats (update statistics) against the upgraded database.</span></span>  
  
-   <span data-ttu-id="9ed5a-142">将数据库复制到另一个服务器实例时，为了给用户和应用程序提供一致的体验，您最好在另一个服务器实例上重新创建该数据库的部分或全部元数据（例如登录名和作业）。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-142">When you copy a database to another server instance, to provide a consistent experience to users and applications, you might have to re-create some or all of the metadata for the database, such as logins and jobs, on the other server instance.</span></span> <span data-ttu-id="9ed5a-143">有关详细信息，请参阅 [当数据库在其他服务器实例上可用时管理元数据 (SQL Server)](manage-metadata-when-making-a-database-available-on-another-server.md)。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-143">For more information, see [Manage Metadata When Making a Database Available on Another Server Instance &#40;SQL Server&#41;](manage-metadata-when-making-a-database-available-on-another-server.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="9ed5a-144">Security</span><span class="sxs-lookup"><span data-stu-id="9ed5a-144">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="9ed5a-145">权限</span><span class="sxs-lookup"><span data-stu-id="9ed5a-145">Permissions</span></span>  
 <span data-ttu-id="9ed5a-146">您必须是源服务器和目标服务器上 **sysadmin** 固定服务器角色的成员。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-146">You must be a member of the **sysadmin** fixed server role on both the source and destination servers.</span></span>  
  
##  <a name="copy-move-or-upgrade-databases"></a><a name="Copy_Move"></a><span data-ttu-id="9ed5a-147">复制、移动或升级数据库</span><span class="sxs-lookup"><span data-stu-id="9ed5a-147">Copy, Move or Upgrade Databases</span></span>  
  
1.  <span data-ttu-id="9ed5a-148">在的对象资源管理器中， [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 展开 "**数据库**"，右键单击数据库，指向 "**任务**"，然后单击 "**复制数据库**"。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-148">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], in Object Explorer, expand **Databases**, right-click a database, point to **Tasks**, and then click **Copy Database**.</span></span>  
  
2.  <span data-ttu-id="9ed5a-149">从 **“选择源服务器”** 页，指定要移动或复制的数据库所在的服务器并输入登录信息。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-149">From the **Select a Source Server** page, specify the server with the database to move or copy, and to enter login information.</span></span> <span data-ttu-id="9ed5a-150">在选择身份验证方法并输入登录信息之后，单击 **“下一步”** 即可与源服务器建立连接。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-150">After you select the authentication method and enter login information, click **Next** to establish the connection to the source server.</span></span> <span data-ttu-id="9ed5a-151">此连接会在整个会话过程中保持打开状态。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-151">This connection remains open throughout the session.</span></span>  
  
     <span data-ttu-id="9ed5a-152">**源服务器**</span><span class="sxs-lookup"><span data-stu-id="9ed5a-152">**Source server**</span></span>  
     <span data-ttu-id="9ed5a-153">选择要移动或复制的数据库所在的服务器的名称，或者单击 "浏览 (**...**) " 按钮以找到所需的服务器。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-153">Select the name of the server on which the database or databases you want to move or copy are located, or click the browse (**...**) button to locate the server you want.</span></span> <span data-ttu-id="9ed5a-154">该服务器必须至少为 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-154">The server must be at least [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span>  
  
     <span data-ttu-id="9ed5a-155">**Use Windows Authentication**</span><span class="sxs-lookup"><span data-stu-id="9ed5a-155">**Use Windows Authentication**</span></span>  
     <span data-ttu-id="9ed5a-156">允许用户通过 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 用户帐户进行连接。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-156">Allow a user to connect through a [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows user account.</span></span>  
  
     <span data-ttu-id="9ed5a-157">**Use SQL Server Authentication**</span><span class="sxs-lookup"><span data-stu-id="9ed5a-157">**Use SQL Server Authentication**</span></span>  
     <span data-ttu-id="9ed5a-158">允许用户通过提供 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证用户名和密码进行连接。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-158">Allow a user to connect by providing a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication user name and password.</span></span>  
  
     <span data-ttu-id="9ed5a-159">**用户名**</span><span class="sxs-lookup"><span data-stu-id="9ed5a-159">**User name**</span></span>  
     <span data-ttu-id="9ed5a-160">输入连接所使用的用户名。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-160">Enter the user name to connect with.</span></span> <span data-ttu-id="9ed5a-161">只有选择使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证进行连接时，此选项才可用。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-161">This option is only available if you have selected to connect using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication .</span></span>  
  
     <span data-ttu-id="9ed5a-162">**密码**</span><span class="sxs-lookup"><span data-stu-id="9ed5a-162">**Password**</span></span>  
     <span data-ttu-id="9ed5a-163">输入登录名的密码。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-163">Enter the password for the login.</span></span> <span data-ttu-id="9ed5a-164">只有选择使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证进行连接时，此选项才可用。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-164">This option is only available if you have selected to connect using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
     <span data-ttu-id="9ed5a-165">**下一页**</span><span class="sxs-lookup"><span data-stu-id="9ed5a-165">**Next**</span></span>  
     <span data-ttu-id="9ed5a-166">连接到服务器并验证用户。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-166">Connect to the server and validate the user.</span></span> <span data-ttu-id="9ed5a-167">此过程将检查用户是否是所选计算机上 **sysadmin** 固定服务器角色的成员。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-167">This process checks whether the user is a member of the **sysadmin** fixed server role on the selected computer.</span></span>  
  
3.  <span data-ttu-id="9ed5a-168">从 **“选择目标服务器”** 页，指定数据库移动或复制的目标服务器。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-168">From the **Select a Destination Server** page, specify the server where the database will be moved or copied.</span></span> <span data-ttu-id="9ed5a-169">如果将源服务器和目标服务器设置为同一个服务器实例，则将会创建一个数据库的副本。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-169">If you set the source and destination servers to the same server instance, you will make a copy of a database.</span></span> <span data-ttu-id="9ed5a-170">在此情况下，必须稍后在向导中重命名数据库。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-170">In this case you must rename the database at a later point in the wizard.</span></span> <span data-ttu-id="9ed5a-171">仅当目标服务器上不存在名称冲突时，源数据库名称才能用于复制或移动的数据库。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-171">The source database name can be used for the copied or moved database only if name conflicts do not exist on the destination server.</span></span> <span data-ttu-id="9ed5a-172">如果存在名称冲突，则必须在目标服务器上手动解决冲突问题，然后才能在此处使用源数据库名称。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-172">If name conflicts exist, you must resolve them manually on the destination server before you can use the source database name there.</span></span>  
  
     <span data-ttu-id="9ed5a-173">**目标服务器**</span><span class="sxs-lookup"><span data-stu-id="9ed5a-173">**Destination server**</span></span>  
     <span data-ttu-id="9ed5a-174">选择要将数据库移动或复制到的服务器的名称，或者单击 "浏览 (**...** ") 按钮以查找目标服务器。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-174">Select the name of the server to which the database or databases will be moved or copied, or click the browse (**...**) button to locate a destination server.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="9ed5a-175">可以使用群集服务器作为目标；复制数据库向导将确保您只选择群集目标服务器上的共享驱动器。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-175">You can use a destination that is a clustered server; the Copy Database Wizard will make sure you select only shared drives on a clustered destination server.</span></span>  
  
     <span data-ttu-id="9ed5a-176">**Use Windows Authentication**</span><span class="sxs-lookup"><span data-stu-id="9ed5a-176">**Use Windows Authentication**</span></span>  
     <span data-ttu-id="9ed5a-177">允许用户通过 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 用户帐户进行连接。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-177">Allow a user to connect through a [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows user account.</span></span>  
  
     <span data-ttu-id="9ed5a-178">**Use SQL Server Authentication**</span><span class="sxs-lookup"><span data-stu-id="9ed5a-178">**Use SQL Server Authentication**</span></span>  
     <span data-ttu-id="9ed5a-179">允许用户通过提供 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证用户名和密码进行连接。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-179">Allow a user to connect by providing a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication user name and password.</span></span>  
  
     <span data-ttu-id="9ed5a-180">**用户名**</span><span class="sxs-lookup"><span data-stu-id="9ed5a-180">**User name**</span></span>  
     <span data-ttu-id="9ed5a-181">输入连接所使用的用户名。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-181">Enter the user name to connect with.</span></span> <span data-ttu-id="9ed5a-182">只有选择 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证时，此选项才可用。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-182">This option is only available if you have selected [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
     <span data-ttu-id="9ed5a-183">**密码**</span><span class="sxs-lookup"><span data-stu-id="9ed5a-183">**Password**</span></span>  
     <span data-ttu-id="9ed5a-184">输入登录名的密码。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-184">Enter the password for the login.</span></span> <span data-ttu-id="9ed5a-185">只有选择 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证时，此选项才可用。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-185">This option is only available if you have selected [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
     <span data-ttu-id="9ed5a-186">**下一页**</span><span class="sxs-lookup"><span data-stu-id="9ed5a-186">**Next**</span></span>  
     <span data-ttu-id="9ed5a-187">连接到服务器并验证用户。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-187">Connect to the server and validate the user.</span></span> <span data-ttu-id="9ed5a-188">此过程检查用户是否对所选计算机拥有上述权限。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-188">This process checks whether the user has the permissions listed above on the selected computers.</span></span>  
  
4.  <span data-ttu-id="9ed5a-189">从 **“选择传输方法”** 页，选择传输方法。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-189">From the **Select a Transfer Method** page, select the transfer method.</span></span>  
  
     <span data-ttu-id="9ed5a-190">**使用分离和附加方法**</span><span class="sxs-lookup"><span data-stu-id="9ed5a-190">**Use the detach and attach method**</span></span>  
     <span data-ttu-id="9ed5a-191">从源服务器上分离数据库，将数据库文件（.mdf、.ndf 和 .ldf）复制到目标服务器，然后在目标服务器上附加数据库。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-191">Detach the database from the source server, copy the database files (.mdf, .ndf, and .ldf) to the destination server, and attach the database at the destination server.</span></span> <span data-ttu-id="9ed5a-192">此方法通常较快，因为其主要任务只是读取源磁盘和写入目标磁盘。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-192">This method is usually the faster method because the principal work is reading the source disk and writing the destination disk.</span></span> <span data-ttu-id="9ed5a-193">无需使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 逻辑在数据库中创建对象或创建数据存储结构。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-193">No [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] logic is required to create objects within the database, or create data storage structures.</span></span> <span data-ttu-id="9ed5a-194">但是，如果数据库包含大量已分配但未使用的空间，此方法会比较慢。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-194">This method can be slower, however, if the database contains a large amount of allocated but unused space.</span></span> <span data-ttu-id="9ed5a-195">例如，对于一个在创建时分配了 100 MB 空间的几乎为空的新数据库，即使只使用了 5 MB 空间，也会复制全部 100 MB 空间。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-195">For instance, a new and practically empty database that is created allocating 100 MB, copies the entire 100 MB, even if only 5 MB is full.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="9ed5a-196">如果使用此方法。用户将无法在传输过程中使用数据库。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-196">This method makes the database unavailable to users during the transfer.</span></span>  
  
     <span data-ttu-id="9ed5a-197">**如果失败，则重新附加源数据库**</span><span class="sxs-lookup"><span data-stu-id="9ed5a-197">**If a failure occurs, reattach the source database**</span></span>  
     <span data-ttu-id="9ed5a-198">数据库复制之后，原始数据库文件将始终重新附加到源服务器。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-198">When a database is copied, the original database files are always reattached to the source server.</span></span> <span data-ttu-id="9ed5a-199">如果无法完成数据库移动，请使用此框将原始文件重新附加到源数据库。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-199">Use this box to reattach original files to the source database if a database move cannot be completed.</span></span>  
  
     <span data-ttu-id="9ed5a-200">**使用 SQL 管理对象方法**</span><span class="sxs-lookup"><span data-stu-id="9ed5a-200">**Use the SQL Management Object method**</span></span>  
     <span data-ttu-id="9ed5a-201">此方法读取源数据库上每个数据库对象的定义，在目标数据库上创建每个对象。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-201">This method reads the definition of each database object on the source database and creates each object in the destination database.</span></span> <span data-ttu-id="9ed5a-202">然后，它从源表向目标表传输数据，重新创建索引和元数据。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-202">Then it transfers the data from the source tables to the destination tables, recreating indexes and metadata.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="9ed5a-203">数据库用户可以在传输过程中继续访问数据库。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-203">Database users can continue to access the database during the transfer.</span></span>  
  
5.  <span data-ttu-id="9ed5a-204">从 **“选择数据库”** 页，选择要从源服务器移动或复制到目标服务器的数据库。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-204">From the **Select Database** page, select the database or databases you want to move or copy from the source server to the destination server.</span></span> <span data-ttu-id="9ed5a-205">请参阅本主题的 "在 Begin 之前" 部分中的[限制和限制](#Restrictions)。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-205">See [Limitations and Restrictions](#Restrictions) in the 'Before You Begin' section of this topic.</span></span>  
  
     <span data-ttu-id="9ed5a-206">**移动**</span><span class="sxs-lookup"><span data-stu-id="9ed5a-206">**Move**</span></span>  
     <span data-ttu-id="9ed5a-207">将数据库移动到目标服务器。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-207">Move the database to the destination server.</span></span>  
  
     <span data-ttu-id="9ed5a-208">**复制**</span><span class="sxs-lookup"><span data-stu-id="9ed5a-208">**Copy**</span></span>  
     <span data-ttu-id="9ed5a-209">将数据库复制到目标服务器。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-209">Copy the database to the destination server.</span></span>  
  
     <span data-ttu-id="9ed5a-210">**数据源**</span><span class="sxs-lookup"><span data-stu-id="9ed5a-210">**Source**</span></span>  
     <span data-ttu-id="9ed5a-211">显示源服务器上的数据库。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-211">Displays the databases that exist on the source server.</span></span>  
  
     <span data-ttu-id="9ed5a-212">**Status**</span><span class="sxs-lookup"><span data-stu-id="9ed5a-212">**Status**</span></span>  
     <span data-ttu-id="9ed5a-213">如果可以移动数据库，则显示 **"确定"** 。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-213">Displays **OK** if the database can be moved.</span></span> <span data-ttu-id="9ed5a-214">否则将显示无法移动该数据库的原因。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-214">Otherwise displays the reason why the database cannot be moved.</span></span>  
  
     <span data-ttu-id="9ed5a-215">**“刷新”**</span><span class="sxs-lookup"><span data-stu-id="9ed5a-215">**Refresh**</span></span>  
     <span data-ttu-id="9ed5a-216">刷新数据库列表。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-216">Refresh the list of databases.</span></span>  
  
     <span data-ttu-id="9ed5a-217">**下一页**</span><span class="sxs-lookup"><span data-stu-id="9ed5a-217">**Next**</span></span>  
     <span data-ttu-id="9ed5a-218">开始验证过程，然后转到下一屏幕。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-218">Start the validation process, and then move to the next screen.</span></span>  
  
6.  <span data-ttu-id="9ed5a-219">从“配置目标数据库” \*\*\*\* 页，更改数据库名称（如果适用）并指定数据库文件的位置和名称。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-219">From the **Configure Destination Database** page, change the database name if appropriate and specify the location and names of the database files.</span></span> <span data-ttu-id="9ed5a-220">在移动或复制每个数据库时都会出现此页。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-220">This page appears once for each database being moved or copied.</span></span>  
  
7.  <span data-ttu-id="9ed5a-221">从 **“选择数据库对象”** 页，选择要在移动或复制操作中包括的对象。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-221">From the **Select Database Objects** page, select the objects to include in the move or copy operation.</span></span> <span data-ttu-id="9ed5a-222">只有当源和目标为不同服务器的时候，此页才可用。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-222">This page is only available when the source and destination are different servers.</span></span> <span data-ttu-id="9ed5a-223">若要包含某个对象，请在“可用相关对象”\*\*\*\* 框中单击对象名称，然后单击 **>>** 按钮，将该对象移动到“所选相关对象”\*\*\*\* 框中。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-223">To include an object, click the object name in the **Available related objects** box, and then click the **>>** button to move the object to the **Selected related objects** box.</span></span> <span data-ttu-id="9ed5a-224">若要排除某个对象，请在 "**所选相关对象**" 框中单击对象名称，然后单击按钮，将 **<\<** 该对象移动到 "**可用相关对象**" 框中。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-224">To exclude an object, click the object name in the **Selected related objects** box, and then click the **<\<** button to move the object to the **Available related objects** box.</span></span> <span data-ttu-id="9ed5a-225">默认情况下，将传输每个所选类型中的所有对象。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-225">By default all objects of each selected type are transferred.</span></span> <span data-ttu-id="9ed5a-226">若要选择某个类型中的单个对象，请在 **“所选相关对象”** 框中单击该对象类型旁边的省略号按钮。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-226">To choose individual objects of any type, click the ellipsis button next to any object type in the **Selected related objects** box.</span></span> <span data-ttu-id="9ed5a-227">这将打开一个对话框，您可以从中选择各个对象。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-227">This opens a dialog box where you can select individual objects.</span></span>  
  
     <span data-ttu-id="9ed5a-228">**登录名(运行时的所有登录名)**</span><span class="sxs-lookup"><span data-stu-id="9ed5a-228">**Logins (All logins at run time)**</span></span>  
     <span data-ttu-id="9ed5a-229">在移动或复制操作中包括登录名。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-229">Include logins in the move or copy operation.</span></span> <span data-ttu-id="9ed5a-230">默认为选中状态。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-230">Selected by default.</span></span>  
  
     <span data-ttu-id="9ed5a-231">**master 数据库中的存储过程**</span><span class="sxs-lookup"><span data-stu-id="9ed5a-231">**Stored procedures from master database**</span></span>  
     <span data-ttu-id="9ed5a-232">在移动或复制操作中包括**master**数据库中的存储过程。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-232">Include stored procedures from the **master** database in the move or copy operation.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="9ed5a-233">不能对扩展存储过程及其相关的 DLL 进行自动复制。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-233">Extended stored procedures and their associated DLLs are not eligible for automated copy.</span></span>  
  
     <span data-ttu-id="9ed5a-234">**SQL Server 代理作业**</span><span class="sxs-lookup"><span data-stu-id="9ed5a-234">**SQL Server Agent jobs**</span></span>  
     <span data-ttu-id="9ed5a-235">在移动或复制操作中包括**msdb**数据库中的作业。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-235">Include jobs from the **msdb** database in the move or copy operation.</span></span>  
  
     <span data-ttu-id="9ed5a-236">**用户定义的错误消息**</span><span class="sxs-lookup"><span data-stu-id="9ed5a-236">**User-defined error messages**</span></span>  
     <span data-ttu-id="9ed5a-237">在移动或复制操作中包括用户定义的错误消息。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-237">Include user-defined error messages in the move or copy operation.</span></span>  
  
     <span data-ttu-id="9ed5a-238">**Endpoints**</span><span class="sxs-lookup"><span data-stu-id="9ed5a-238">**Endpoints**</span></span>  
     <span data-ttu-id="9ed5a-239">包括源数据库中定义的端点。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-239">Include endpoints defined in the source database.</span></span>  
  
     <span data-ttu-id="9ed5a-240">**全文目录**</span><span class="sxs-lookup"><span data-stu-id="9ed5a-240">**Full-text catalog**</span></span>  
     <span data-ttu-id="9ed5a-241">包括源数据库中的全文目录。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-241">Include full-text catalogs from the source database.</span></span>  
  
     <span data-ttu-id="9ed5a-242">**SSIS 包**</span><span class="sxs-lookup"><span data-stu-id="9ed5a-242">**SSIS Package**</span></span>  
     <span data-ttu-id="9ed5a-243">包括源数据库中定义的 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 包。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-243">Include [!INCLUDE[ssIS](../../includes/ssis-md.md)] packages defined in the source database.</span></span>  
  
     <span data-ttu-id="9ed5a-244">**说明**</span><span class="sxs-lookup"><span data-stu-id="9ed5a-244">**Description**</span></span>  
     <span data-ttu-id="9ed5a-245">对象的说明。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-245">A description of the object.</span></span>  
  
8.  <span data-ttu-id="9ed5a-246">从 **“源数据库文件的位置”** 页，指定源服务器上包含数据库文件的文件系统共享。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-246">From the **Location of Source Database Files** page, specify a file system share that contains the database files on the source server.</span></span> <span data-ttu-id="9ed5a-247">如果源服务器实例和目标服务器实例位于不同的计算机上，这是必需的。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-247">This is required if the source and destination server instances are on different computers.</span></span>  
  
     <span data-ttu-id="9ed5a-248">**Database**</span><span class="sxs-lookup"><span data-stu-id="9ed5a-248">**Database**</span></span>  
     <span data-ttu-id="9ed5a-249">显示正在移动的每个数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-249">Displays the name of each database being moved.</span></span>  
  
     <span data-ttu-id="9ed5a-250">**文件夹位置**</span><span class="sxs-lookup"><span data-stu-id="9ed5a-250">**Folder location**</span></span>  
     <span data-ttu-id="9ed5a-251">指定文件系统上源数据库文件所在的位置。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-251">Specify the location of the source database files on the file system.</span></span>  
  
     <span data-ttu-id="9ed5a-252">例如：C:\Program Files\Microsoft SQL Server\MSSQL110.MSSQLSERVER\MSSQL\DATA</span><span class="sxs-lookup"><span data-stu-id="9ed5a-252">For example: C:\Program Files\Microsoft SQL Server\MSSQL110.MSSQLSERVER\MSSQL\DATA</span></span>  
  
     <span data-ttu-id="9ed5a-253">**源服务器上的文件共享**</span><span class="sxs-lookup"><span data-stu-id="9ed5a-253">**File share on source server**</span></span>  
     <span data-ttu-id="9ed5a-254">指定源数据库文件的位置作为文件共享的路径。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-254">Specify the location of the source database files as a path of a file share.</span></span>  
  
     <span data-ttu-id="9ed5a-255">例如： " \\ \\ *server_name*\c $ \Program Files\Microsoft SQL Server\MSSQL110。MSSQLSERVER\MSSQL\Data</span><span class="sxs-lookup"><span data-stu-id="9ed5a-255">For example: "\\\\*server_name*\C$\Program Files\Microsoft SQL Server\MSSQL110.MSSQLSERVER\MSSQL\Data</span></span>  
  
9. <span data-ttu-id="9ed5a-256">复制数据库向导将创建一个要传输数据库的 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 包。从 **“配置包”** 页，对包进行自定义（如果适用）。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-256">The Copy Database Wizard creates a [!INCLUDE[ssIS](../../includes/ssis-md.md)] package to transfer the database From the **Configure the Package** page, customize the package if appropriate.</span></span>  
  
     <span data-ttu-id="9ed5a-257">**包位置**</span><span class="sxs-lookup"><span data-stu-id="9ed5a-257">**Package location**</span></span>  
     <span data-ttu-id="9ed5a-258">显示 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 包的写入位置。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-258">Displays where the [!INCLUDE[ssIS](../../includes/ssis-md.md)] package will be written.</span></span>  
  
     <span data-ttu-id="9ed5a-259">**包名称**</span><span class="sxs-lookup"><span data-stu-id="9ed5a-259">**Package name**</span></span>  
     <span data-ttu-id="9ed5a-260">输入 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 包的名称。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-260">Enter a name for the [!INCLUDE[ssIS](../../includes/ssis-md.md)] package.</span></span>  
  
     <span data-ttu-id="9ed5a-261">**日志记录选项**</span><span class="sxs-lookup"><span data-stu-id="9ed5a-261">**Logging options**</span></span>  
     <span data-ttu-id="9ed5a-262">选择是将日志记录信息存储在 Windows 事件日志中还是文本文件中。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-262">Select whether to store the logging information in the Windows event log, or in a text file.</span></span>  
  
     <span data-ttu-id="9ed5a-263">**错误日志文件路径**</span><span class="sxs-lookup"><span data-stu-id="9ed5a-263">**Error log file path**</span></span>  
     <span data-ttu-id="9ed5a-264">提供日志文件位置的路径。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-264">Provide a path for the location of the log file.</span></span> <span data-ttu-id="9ed5a-265">只有在选择了文本文件日志记录选项后，才能使用此选项。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-265">This option is only available if the text file logging option is selected.</span></span>  
  
10. <span data-ttu-id="9ed5a-266">从 **“安排运行包”** 页，指定希望何时启动移动操作或复制操作。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-266">From the **Schedule the Package** page, specify when you want the move or copy operation to start.</span></span> <span data-ttu-id="9ed5a-267">如果您不是系统管理员，必须指定有权访问 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SSIS) 包执行子系统的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 代理的代理帐户。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-267">If you are not a system administrator, you must specify a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent Proxy account that has access to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] (SSIS) Package execution subsystem.</span></span>  
  
     <span data-ttu-id="9ed5a-268">**Run immediately**</span><span class="sxs-lookup"><span data-stu-id="9ed5a-268">**Run immediately**</span></span>  
     <span data-ttu-id="9ed5a-269">单击 "**下一步**" 后开始移动或复制操作。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-269">Start the move or copy operation after you click **Next**.</span></span>  
  
     <span data-ttu-id="9ed5a-270">**计划**</span><span class="sxs-lookup"><span data-stu-id="9ed5a-270">**Schedule**</span></span>  
     <span data-ttu-id="9ed5a-271">以后启动移动操作或复制操作。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-271">Start the move or copy operation later.</span></span> <span data-ttu-id="9ed5a-272">当前的计划设置显示在说明框中。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-272">The current schedule settings appear in the description box.</span></span> <span data-ttu-id="9ed5a-273">若要更改该计划，请单击 **“更改”**。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-273">To change the schedule, click **Change**.</span></span>  
  
     <span data-ttu-id="9ed5a-274">**更改**</span><span class="sxs-lookup"><span data-stu-id="9ed5a-274">**Change**</span></span>  
     <span data-ttu-id="9ed5a-275">打开 "**新建作业计划**" 对话框。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-275">Open the **New Job Schedule** dialog box.</span></span>  
  
     <span data-ttu-id="9ed5a-276">**Integration Services 代理帐户**</span><span class="sxs-lookup"><span data-stu-id="9ed5a-276">**Integration Services proxy account**</span></span>  
     <span data-ttu-id="9ed5a-277">选择可用的代理帐户。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-277">Select an available proxy account.</span></span> <span data-ttu-id="9ed5a-278">若要计划传输，则必须至少有一个代理帐户可供用户使用，而且必须将该帐户配置为拥有对 **“SQL Server Integration Services 包执行”** 子系统的权限。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-278">To schedule the transfer, there must be at least one proxy account available to the user, configured with permission to the **SQL Server Integration Services package execution** subsystem.</span></span>  
  
     <span data-ttu-id="9ed5a-279">若要为包执行创建代理帐户 [!INCLUDE[ssIS](../../includes/ssis-md.md)] ，请在对象资源管理器中展开 " **SQL Server 代理**"，展开 "**代理**"，右键单击 " **SSIS 包执行**"，然后单击 "**新建代理**"。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-279">To create a proxy account for [!INCLUDE[ssIS](../../includes/ssis-md.md)] package execution, in Object Explorer, expand **SQL Server Agent**, expand **Proxies**, right-click **SSIS Package Execution**, and then click **New Proxy**.</span></span>  
  
     <span data-ttu-id="9ed5a-280">**sysadmin** 固定服务器角色的成员可以选择 **“SQL Server 代理服务帐户”**，该帐户拥有必要的权限。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-280">Members of the **sysadmin** fixed server role can select the **SQL Server Agent Service Account**, which has the necessary permissions.</span></span>  
  
11. <span data-ttu-id="9ed5a-281">从 **“完成该向导”** 页，查看所选选项的摘要。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-281">From the **Complete the Wizard** page, review the summary of the selected options.</span></span> <span data-ttu-id="9ed5a-282">单击 **“上一步”** 可以更改选项。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-282">Click **Back** to change an option.</span></span> <span data-ttu-id="9ed5a-283">单击 **“完成”** 将创建数据库。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-283">Click **Finish** to create the database.</span></span> <span data-ttu-id="9ed5a-284">在传输过程中， **“正在执行操作”** 页会监视与 **“复制数据库向导”** 的执行有关的状态信息。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-284">During the transfer, the **Performing operation** page monitors status information about the execution of the **Copy Database Wizard**.</span></span>  
  
     <span data-ttu-id="9ed5a-285">**Action**</span><span class="sxs-lookup"><span data-stu-id="9ed5a-285">**Action**</span></span>  
     <span data-ttu-id="9ed5a-286">列出要执行的每项操作。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-286">Lists each action being performed.</span></span>  
  
     <span data-ttu-id="9ed5a-287">**Status**</span><span class="sxs-lookup"><span data-stu-id="9ed5a-287">**Status**</span></span>  
     <span data-ttu-id="9ed5a-288">指示操作总体来说是成功还是失败。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-288">Indicates whether the action as a whole succeeded or failed.</span></span>  
  
     <span data-ttu-id="9ed5a-289">**Message**</span><span class="sxs-lookup"><span data-stu-id="9ed5a-289">**Message**</span></span>  
     <span data-ttu-id="9ed5a-290">提供每个步骤返回的任何消息。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-290">Provides any messages returned from each step.</span></span>  
  
##  <a name="follow-up-after-upgrading-a-sql-server-database"></a><a name="FollowUp"></a> <span data-ttu-id="9ed5a-291">跟进：在升级 SQL Server 数据库之后</span><span class="sxs-lookup"><span data-stu-id="9ed5a-291">Follow Up: After Upgrading a SQL Server Database</span></span>  
 <span data-ttu-id="9ed5a-292">使用复制数据库向导将数据库从早期版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 升级到 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]后，该数据库将立即变为可用，然后自动升级。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-292">After you use the Copy Database Wizard to upgrade a database from an earlier version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], the database becomes available immediately and is automatically upgraded.</span></span> <span data-ttu-id="9ed5a-293">如果数据库具有全文检索，升级过程将导入、重置或重新生成它们，具体取决于 **全文升级选项** 服务器属性的设置。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-293">If the database has full-text indexes, the upgrade process either imports, resets, or rebuilds them, depending on the setting of the **Full-Text Upgrade Option** server property.</span></span> <span data-ttu-id="9ed5a-294">如果将升级选项设置为“导入”或“重新生成”，在升级过程中将无法使用全文检索。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-294">If the upgrade option is set to **Import** or **Rebuild**, the full-text indexes will be unavailable during the upgrade.</span></span> <span data-ttu-id="9ed5a-295">导入可能需要数小时，而重新生成所需的时间最多时可能十倍于此，具体取决于要编制索引的数据量。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-295">Depending the amount of data being indexed, importing can take several hours, and rebuilding can take up to ten times longer.</span></span> <span data-ttu-id="9ed5a-296">另请注意，当升级选项设置为“导入”时，如果全文目录不可用，将重新生成关联的全文检索。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-296">Note also that when the upgrade option is set to **Import**, if a full-text catalog is not available, the associated full-text indexes are rebuilt.</span></span> <span data-ttu-id="9ed5a-297">有关查看或更改“全文升级选项”属性设置的信息，请参阅[管理和监视服务器实例的全文搜索](../search/manage-and-monitor-full-text-search-for-a-server-instance.md)。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-297">For information about viewing or changing the setting of the **Full-Text Upgrade Option** property, see [Manage and Monitor Full-Text Search for a Server Instance](../search/manage-and-monitor-full-text-search-for-a-server-instance.md).</span></span>  
  
 <span data-ttu-id="9ed5a-298">如果升级前用户数据库的兼容级别为 100 或更高，升级后将保持相应级别。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-298">If the compatibility level of a user database was 100 or higher before upgrade, it remains the same after upgrade.</span></span> <span data-ttu-id="9ed5a-299">如果兼容级别为 90，则在升级后的数据库中，兼容级别将设置为 100，该级别为 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]支持的最低兼容级别。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-299">If the compatibility level was 90 in the upgraded database, the compatibility level is set to 100, which is the lowest supported compatibility level in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="9ed5a-300">有关详细信息，请参阅 [ALTER DATABASE 兼容级别 (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level)。</span><span class="sxs-lookup"><span data-stu-id="9ed5a-300">For more information, see [ALTER DATABASE Compatibility Level &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ed5a-301">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9ed5a-301">See Also</span></span>  
 <span data-ttu-id="9ed5a-302">[使用分离和附加 &#40;Transact-sql&#41;升级数据库](upgrade-a-database-using-detach-and-attach-transact-sql.md) </span><span class="sxs-lookup"><span data-stu-id="9ed5a-302">[Upgrade a Database Using Detach and Attach &#40;Transact-SQL&#41;](upgrade-a-database-using-detach-and-attach-transact-sql.md) </span></span>  
 [<span data-ttu-id="9ed5a-303">创建 SQL Server 代理的代理帐户</span><span class="sxs-lookup"><span data-stu-id="9ed5a-303">Create a SQL Server Agent Proxy</span></span>](../../ssms/agent/create-a-sql-server-agent-proxy.md)  
  
  
