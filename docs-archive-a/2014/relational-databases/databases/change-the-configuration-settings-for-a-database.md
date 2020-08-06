---
title: 更改数据库的配置设置 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- database configuration [SQL Server]
- configuration options [SQL Server], databases
- modifying database configuration settings
ms.assetid: c29c3385-5043-400f-bb4e-044a4c9a9a4b
author: stevestein
ms.author: sstein
ms.openlocfilehash: f9edecefae5154bb66a65e38724d9e77a94fdbb4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693953"
---
# <a name="change-the-configuration-settings-for-a-database"></a><span data-ttu-id="f0031-102">更改数据库的配置设置</span><span class="sxs-lookup"><span data-stu-id="f0031-102">Change the Configuration Settings for a Database</span></span>
  <span data-ttu-id="f0031-103">本主题说明如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中更改服务器级别选项。</span><span class="sxs-lookup"><span data-stu-id="f0031-103">This topic describes how to change database-level options in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="f0031-104">这些选项仅针对各自的数据库，而不会影响其他数据库。</span><span class="sxs-lookup"><span data-stu-id="f0031-104">These options are unique to each database and do not affect other databases.</span></span>  
  
 <span data-ttu-id="f0031-105">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="f0031-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="f0031-106">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="f0031-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="f0031-107">限制和局限</span><span class="sxs-lookup"><span data-stu-id="f0031-107">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="f0031-108">安全性</span><span class="sxs-lookup"><span data-stu-id="f0031-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="f0031-109">**若要更改数据库的选项设置，请使用：**</span><span class="sxs-lookup"><span data-stu-id="f0031-109">**To change the option settings for a database, using:**</span></span>  
  
     [<span data-ttu-id="f0031-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="f0031-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="f0031-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="f0031-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="f0031-112">开始之前</span><span class="sxs-lookup"><span data-stu-id="f0031-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="f0031-113">限制和局限</span><span class="sxs-lookup"><span data-stu-id="f0031-113">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="f0031-114">只有系统管理员、数据库所有者、 **sysadmin** 和 **dbcreator** 固定服务器角色成员以及 **db_owner** 固定数据库角色成员才能修改这些选项。</span><span class="sxs-lookup"><span data-stu-id="f0031-114">Only the system administrator, database owner, members of the **sysadmin** and **dbcreator** fixed server roles and **db_owner** fixed database roles can modify these options.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="f0031-115">Security</span><span class="sxs-lookup"><span data-stu-id="f0031-115">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="f0031-116">权限</span><span class="sxs-lookup"><span data-stu-id="f0031-116">Permissions</span></span>  
 <span data-ttu-id="f0031-117">需要对数据库拥有 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="f0031-117">Requires ALTER permission on the database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="f0031-118">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="f0031-118">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-change-the-option-settings-for-a-database"></a><span data-ttu-id="f0031-119">更改数据库的选项设置</span><span class="sxs-lookup"><span data-stu-id="f0031-119">To change the option settings for a database</span></span>  
  
1.  <span data-ttu-id="f0031-120">在对象资源管理器中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 实例，扩展该服务器，然后扩展“数据库”，右键单击某个数据库，再单击“属性”。</span><span class="sxs-lookup"><span data-stu-id="f0031-120">In Object Explorer, connect to a [!INCLUDE[ssDE](../../includes/ssde-md.md)] instance, expand the server, expand **Databases**, right-click a database, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="f0031-121">在 **“数据库属性”** 对话框中，单击 **“选项”** 访问大多数配置设置。</span><span class="sxs-lookup"><span data-stu-id="f0031-121">In the **Database Properties** dialog box, click **Options** to access most of the configuration settings.</span></span> <span data-ttu-id="f0031-122">文件和文件组配置、镜像和日志传送都在各自相应的页上。</span><span class="sxs-lookup"><span data-stu-id="f0031-122">File and filegroup configurations, mirroring and log shipping are on their respective pages.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="f0031-123">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="f0031-123">Using Transact-SQL</span></span>  
  
#### <a name="to-change-the-option-settings-for-a-database"></a><span data-ttu-id="f0031-124">更改数据库的选项设置</span><span class="sxs-lookup"><span data-stu-id="f0031-124">To change the option settings for a database</span></span>  
  
1.  <span data-ttu-id="f0031-125">连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f0031-125">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="f0031-126">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="f0031-126">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="f0031-127">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="f0031-127">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="f0031-128">该示例设置 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 示例数据库的恢复模式和数据页面验证选项。</span><span class="sxs-lookup"><span data-stu-id="f0031-128">This example sets the recovery model and data page verification options for the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample database.</span></span>  
  
 [!code-sql[DatabaseDDL#AlterDatabase7](../../snippets/tsql/SQL14/tsql/databaseddl/transact-sql/alterdatabase.sql#alterdatabase7)]  
  
 <span data-ttu-id="f0031-129">详细信息，请参阅 [ALTER DATABASE SET 选项 (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql-set-options)。</span><span class="sxs-lookup"><span data-stu-id="f0031-129">For more examples, see [ALTER DATABASE SET Options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0031-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f0031-130">See Also</span></span>  
 <span data-ttu-id="f0031-131">[ALTER DATABASE 兼容级别 (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level) </span><span class="sxs-lookup"><span data-stu-id="f0031-131">[ALTER DATABASE Compatibility Level &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level) </span></span>  
 <span data-ttu-id="f0031-132">[ALTER DATABASE 数据库镜像 (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring) </span><span class="sxs-lookup"><span data-stu-id="f0031-132">[ALTER DATABASE Database Mirroring &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring) </span></span>  
 <span data-ttu-id="f0031-133">[ALTER DATABASE SET HADR (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql-set-hadr) </span><span class="sxs-lookup"><span data-stu-id="f0031-133">[ALTER DATABASE SET HADR &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-hadr) </span></span>  
 <span data-ttu-id="f0031-134">[重命名数据库](rename-a-database.md) </span><span class="sxs-lookup"><span data-stu-id="f0031-134">[Rename a Database](rename-a-database.md) </span></span>  
 [<span data-ttu-id="f0031-135">收缩数据库</span><span class="sxs-lookup"><span data-stu-id="f0031-135">Shrink a Database</span></span>](shrink-a-database.md)  
  
  
