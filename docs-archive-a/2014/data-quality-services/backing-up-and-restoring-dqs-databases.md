---
title: 备份和还原 DQS 数据库 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: f3091f62-2234-4a80-a615-cf14c2a1da85
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 489664d8c64a99d1ea4dcec79b93e5b01b28f649
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578465"
---
# <a name="backing-up-and-restoring-dqs-databases"></a><span data-ttu-id="2ee5c-102">备份和还原 DQS 数据库</span><span class="sxs-lookup"><span data-stu-id="2ee5c-102">Backing Up and Restoring DQS Databases</span></span>
  <span data-ttu-id="2ee5c-103">本主题说明如何备份和还原 DQS 数据库。</span><span class="sxs-lookup"><span data-stu-id="2ee5c-103">This topic describes how to back up and restore the DQS databases.</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="2ee5c-104">开始之前</span><span class="sxs-lookup"><span data-stu-id="2ee5c-104">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a><span data-ttu-id="2ee5c-105">先决条件</span><span class="sxs-lookup"><span data-stu-id="2ee5c-105">Prerequisites</span></span>  
  
-   <span data-ttu-id="2ee5c-106">您必须知道或记住您在 DQS 服务器安装过程中提供的数据库主密钥的密码。</span><span class="sxs-lookup"><span data-stu-id="2ee5c-106">You must know or remember the password for the database master key that you provided during the DQS server installation.</span></span>  
  
-   <span data-ttu-id="2ee5c-107">确保 DQS 中没有正在运行的活动或过程。</span><span class="sxs-lookup"><span data-stu-id="2ee5c-107">Ensure that there are no running activities or processes in DQS.</span></span> <span data-ttu-id="2ee5c-108">这可以使用 **“活动监视”** 屏幕进行验证。</span><span class="sxs-lookup"><span data-stu-id="2ee5c-108">This can be verified using the **Activity Monitoring** screen.</span></span> <span data-ttu-id="2ee5c-109">有关使用该屏幕的详细信息，请参阅 [Monitor DQS Activities](../../2014/data-quality-services/monitor-dqs-activities.md)。</span><span class="sxs-lookup"><span data-stu-id="2ee5c-109">For detailed information about working in this screen, see [Monitor DQS Activities](../../2014/data-quality-services/monitor-dqs-activities.md).</span></span>  
  
-   <span data-ttu-id="2ee5c-110">确保没有用户已登录 DQS 服务器。</span><span class="sxs-lookup"><span data-stu-id="2ee5c-110">Ensure that there are no users logged on the DQS server.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="2ee5c-111">Security</span><span class="sxs-lookup"><span data-stu-id="2ee5c-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="2ee5c-112">权限</span><span class="sxs-lookup"><span data-stu-id="2ee5c-112">Permissions</span></span>  
  
-   <span data-ttu-id="2ee5c-113">您的 Windows 用户帐户必须为 SQL Server 实例中 sysadmin 固定服务器角色的成员，才能执行备份和还原操作。</span><span class="sxs-lookup"><span data-stu-id="2ee5c-113">Your Windows user account must be a member of the sysadmin fixed server role in the SQL Server instance to perform the backup and restore operations.</span></span>  
  
-   <span data-ttu-id="2ee5c-114">您必须具有 DQS_MAIN 数据库的 dqs_administrator 角色，才能终止 DQS 中任何正在运行的活动或停止任何正在运行的过程。</span><span class="sxs-lookup"><span data-stu-id="2ee5c-114">You must have the dqs_administrator role on the DQS_MAIN database to terminate any running activities or stop any running processes in DQS.</span></span>  
  
##  <a name="backup-and-restore-dqs-databases"></a><a name="BackupRestore"></a> <span data-ttu-id="2ee5c-115">备份和还原 DQS 数据库</span><span class="sxs-lookup"><span data-stu-id="2ee5c-115">Backup and Restore DQS Databases</span></span>  
  
1.  <span data-ttu-id="2ee5c-116">启动 Microsoft SQL Server Management Studio 并连接到适当的 SQL Server 实例。</span><span class="sxs-lookup"><span data-stu-id="2ee5c-116">Start Microsoft SQL Server Management Studio, and connect to the appropriate SQL Server instance.</span></span>  
  
2.  <span data-ttu-id="2ee5c-117">在“对象资源管理器”中，展开 **“数据库”** 节点。</span><span class="sxs-lookup"><span data-stu-id="2ee5c-117">In Object Explorer, expand the **Databases** node.</span></span>  
  
3.  <span data-ttu-id="2ee5c-118">备份 DQS_STAGING_DATA 数据库。</span><span class="sxs-lookup"><span data-stu-id="2ee5c-118">Back up the DQS_STAGING_DATA database.</span></span> <span data-ttu-id="2ee5c-119">有关备份 SQL Server 数据库的分步说明，请参阅[创建完整数据库备份 (SQL Server)](../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="2ee5c-119">For step-by-step instructions for backing a SQL Server database, see [Create a Full Database Backup &#40;SQL Server&#41;](../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md).</span></span>  
  
4.  <span data-ttu-id="2ee5c-120">备份 DQS_PROJECTS 数据库。</span><span class="sxs-lookup"><span data-stu-id="2ee5c-120">Back up the DQS_PROJECTS database.</span></span>  
  
5.  <span data-ttu-id="2ee5c-121">备份 DQS_MAIN 数据库。</span><span class="sxs-lookup"><span data-stu-id="2ee5c-121">Back up the DQS_MAIN database.</span></span>  
  
6.  <span data-ttu-id="2ee5c-122">断开与当前 SQL Server 实例的连接，然后连接到要还原这些数据库的 SQL Server 实例。</span><span class="sxs-lookup"><span data-stu-id="2ee5c-122">Disconnect from the current instance of SQL Server, and connect to the SQL Server instance where you want to restore these databases.</span></span>  
  
7.  <span data-ttu-id="2ee5c-123">还原 DQS_MAIN 数据库。</span><span class="sxs-lookup"><span data-stu-id="2ee5c-123">Restore DQS_MAIN database.</span></span> <span data-ttu-id="2ee5c-124">有关还原 SQL Server 数据库的分步说明，请参阅[还原数据库备份 &#40;SQL Server Management Studio&#41;](../relational-databases/backup-restore/restore-a-database-backup-using-ssms.md)。</span><span class="sxs-lookup"><span data-stu-id="2ee5c-124">For step-by-step instructions to restore a SQL Server database, see [Restore a Database Backup &#40;SQL Server Management Studio&#41;](../relational-databases/backup-restore/restore-a-database-backup-using-ssms.md).</span></span>  
  
8.  <span data-ttu-id="2ee5c-125">还原 DQS_PROJECTS 数据库。</span><span class="sxs-lookup"><span data-stu-id="2ee5c-125">Restore the DQS_PROJECTS database.</span></span>  
  
9. <span data-ttu-id="2ee5c-126">还原 DQS_STAGING_DATA 数据库。</span><span class="sxs-lookup"><span data-stu-id="2ee5c-126">Restore the DQS_STAGING_DATA database.</span></span>  
  
10. <span data-ttu-id="2ee5c-127">在“对象资源管理器”中，右键单击服务器，再单击 **“新建查询”**。</span><span class="sxs-lookup"><span data-stu-id="2ee5c-127">In Object Explorer, right-click the server, and then click **New Query**.</span></span>  
  
11. <span data-ttu-id="2ee5c-128">在查询编辑器窗口中，复制以下 SQL 语句，并将替换为在 *\<PASSWORD>* DQS 安装过程中为数据库主密钥提供的密码：</span><span class="sxs-lookup"><span data-stu-id="2ee5c-128">In the Query Editor window, copy the following SQL statements, and replace *\<PASSWORD>* with the password that you provided during the DQS installation for the database master key:</span></span>  
  
    ```sql  
    USE [DQS_MAIN]  
    GO  
    EXECUTE [internal_core].[RestoreDQDatabases] '<PASSWORD>'  
    GO  
    ```  
  
12. <span data-ttu-id="2ee5c-129">按 F5 执行这些语句。</span><span class="sxs-lookup"><span data-stu-id="2ee5c-129">Press F5 to execute the statements.</span></span> <span data-ttu-id="2ee5c-130">检查 "**结果**" 窗格以验证语句是否已成功执行。</span><span class="sxs-lookup"><span data-stu-id="2ee5c-130">Check the **Results** pane to verify that the statements have executed successfully.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ee5c-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2ee5c-131">See Also</span></span>  
 [<span data-ttu-id="2ee5c-132">管理 DQS 数据库</span><span class="sxs-lookup"><span data-stu-id="2ee5c-132">Manage DQS Databases</span></span>](../../2014/data-quality-services/manage-dqs-databases.md)  
  
  
