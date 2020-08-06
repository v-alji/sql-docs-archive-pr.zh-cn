---
title: 迁移到部分包含的数据库 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- contained database, migrating to
ms.assetid: 90faac38-f79e-496d-b589-e8b2fe01c562
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6142d46dc0540e5998fa66d463538d1453a17d84
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693918"
---
# <a name="migrate-to-a-partially-contained-database"></a><span data-ttu-id="512b0-102">Migrate to a Partially Contained Database</span><span class="sxs-lookup"><span data-stu-id="512b0-102">Migrate to a Partially Contained Database</span></span>
  <span data-ttu-id="512b0-103">本主题讨论要更改为部分包含的数据库模型的准备工作，接着提供了迁移步骤。</span><span class="sxs-lookup"><span data-stu-id="512b0-103">This topic discusses how to prepare to change to the partially contained database model and then provides the migration steps.</span></span>  
  
 <span data-ttu-id="512b0-104">**本主题内容：**</span><span class="sxs-lookup"><span data-stu-id="512b0-104">**In this topic:**</span></span>  
  
-   [<span data-ttu-id="512b0-105">准备迁移数据库</span><span class="sxs-lookup"><span data-stu-id="512b0-105">Preparing to Migrate a Database</span></span>](#prepare)  
  
-   [<span data-ttu-id="512b0-106">启用包含的数据库</span><span class="sxs-lookup"><span data-stu-id="512b0-106">Enable Contained Databases</span></span>](#enable)  
  
-   [<span data-ttu-id="512b0-107">将数据库转换为部分包含的数据库</span><span class="sxs-lookup"><span data-stu-id="512b0-107">Converting a Database to Partially Contained</span></span>](#convert)  
  
-   [<span data-ttu-id="512b0-108">将用户迁移为包含的数据库用户</span><span class="sxs-lookup"><span data-stu-id="512b0-108">Migrating Users to Contained Database Users</span></span>](#users)  
  
##  <a name="preparing-to-migrate-a-database"></a><a name="prepare"></a> <span data-ttu-id="512b0-109">准备迁移数据库</span><span class="sxs-lookup"><span data-stu-id="512b0-109">Preparing to Migrate a Database</span></span>  
 <span data-ttu-id="512b0-110">在考虑将数据库迁移到部分包含的数据库模型时，请复查以下各项。</span><span class="sxs-lookup"><span data-stu-id="512b0-110">Review the following items when considering migrating a database to the partially contained database model.</span></span>  
  
-   <span data-ttu-id="512b0-111">您应该了解部分包含的数据库模型。</span><span class="sxs-lookup"><span data-stu-id="512b0-111">You should understand the partially contained database model.</span></span> <span data-ttu-id="512b0-112">有关详细信息，请参阅 [Contained Databases](contained-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="512b0-112">For more information, see [Contained Databases](contained-databases.md).</span></span>  
  
-   <span data-ttu-id="512b0-113">您应该了解部分包含的数据库所独有的风险。</span><span class="sxs-lookup"><span data-stu-id="512b0-113">You should understand risks that are unique to partially contained databases.</span></span> <span data-ttu-id="512b0-114">有关详细信息，请参阅 [Security Best Practices with Contained Databases](security-best-practices-with-contained-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="512b0-114">For more information, see [Security Best Practices with Contained Databases](security-best-practices-with-contained-databases.md).</span></span>  
  
-   <span data-ttu-id="512b0-115">包含的数据库不支持复制、变更数据结构或更改跟踪。</span><span class="sxs-lookup"><span data-stu-id="512b0-115">Contained databases do not support replication, change data capture, or change tracking.</span></span> <span data-ttu-id="512b0-116">确认数据库没有使用这些功能。</span><span class="sxs-lookup"><span data-stu-id="512b0-116">Confirm the database does not use these features.</span></span>  
  
-   <span data-ttu-id="512b0-117">复查为了部分包含的数据库而修改的数据库功能的列表。</span><span class="sxs-lookup"><span data-stu-id="512b0-117">Review the list of database features that are modified for partially contained databases.</span></span> <span data-ttu-id="512b0-118">有关详细信息，请参阅[经过修改的功能（包含的数据库）](modified-features-contained-database.md)。</span><span class="sxs-lookup"><span data-stu-id="512b0-118">For more information, see [Modified Features &#40;Contained Database&#41;](modified-features-contained-database.md).</span></span>  
  
-   <span data-ttu-id="512b0-119">若要在数据库中查找非包含的对象或功能，请查询 [sys.dm_db_uncontained_entities (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-uncontained-entities-transact-sql) 。</span><span class="sxs-lookup"><span data-stu-id="512b0-119">Query [sys.dm_db_uncontained_entities &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-uncontained-entities-transact-sql) to find uncontained objects or features in the database.</span></span> <span data-ttu-id="512b0-120">有关详细信息，请参阅</span><span class="sxs-lookup"><span data-stu-id="512b0-120">For more information, see.</span></span>  
  
-   <span data-ttu-id="512b0-121">监视 **database_uncontained_usage** XEvent 以了解何时使用非包含的功能。</span><span class="sxs-lookup"><span data-stu-id="512b0-121">Monitor the **database_uncontained_usage** XEvent to see when uncontained features are used.</span></span>  
  
##  <a name="enable-contained-databases"></a><a name="enable"></a> <span data-ttu-id="512b0-122">启用包含的数据库</span><span class="sxs-lookup"><span data-stu-id="512b0-122">Enable Contained Databases</span></span>  
 <span data-ttu-id="512b0-123">必须先在 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]的实例上启用包含的数据库，然后才能创建包含的数据库。</span><span class="sxs-lookup"><span data-stu-id="512b0-123">Contained databases must be enabled on the instance of [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], before contained databases can be created.</span></span>  
  
### <a name="enabling-contained-databases-using-transact-sql"></a><span data-ttu-id="512b0-124">使用 Transact-SQL 启用包含的数据库</span><span class="sxs-lookup"><span data-stu-id="512b0-124">Enabling Contained Databases Using Transact-SQL</span></span>  
 <span data-ttu-id="512b0-125">下面的示例对 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]的实例启用包含的数据库。</span><span class="sxs-lookup"><span data-stu-id="512b0-125">The following example enables contained databases on the instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].</span></span>  
  
```sql  
sp_configure 'contained database authentication', 1;  
GO  
RECONFIGURE ;  
GO  
```  
  
#### <a name="enabling-contained-databases-using-management-studio"></a><span data-ttu-id="512b0-126">使用 Management Studio 启用包含的数据库</span><span class="sxs-lookup"><span data-stu-id="512b0-126">Enabling Contained Databases Using Management Studio</span></span>  
 <span data-ttu-id="512b0-127">下面的示例对 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]的实例启用包含的数据库。</span><span class="sxs-lookup"><span data-stu-id="512b0-127">The following example enables contained databases on the instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].</span></span>  
  
1.  <span data-ttu-id="512b0-128">在对象资源管理器中，右键单击服务器名称，然后单击“属性”  。</span><span class="sxs-lookup"><span data-stu-id="512b0-128">In Object Explorer, right-click the server name, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="512b0-129">在 **“高级”** 页面上的 **“包含”** 部分中，将 **“启用包含的数据库”** 选项设置为 **“True”** 。</span><span class="sxs-lookup"><span data-stu-id="512b0-129">On the **Advanced** page, in the **Containment** section, set the **Enable Contained Databases** option to **True**.</span></span>  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="converting-a-database-to-partially-contained"></a><a name="convert"></a> <span data-ttu-id="512b0-130">将数据库转换为部分包含的数据库</span><span class="sxs-lookup"><span data-stu-id="512b0-130">Converting a Database to Partially Contained</span></span>  
 <span data-ttu-id="512b0-131">通过更改 **CONTAINMENT** 选项可以将数据库转换为包含的数据库。</span><span class="sxs-lookup"><span data-stu-id="512b0-131">A database is converted to a contained database by changing the **CONTAINMENT** option.</span></span>  
  
### <a name="converting-a-database-to-partially-contained-using-transact-sql"></a><span data-ttu-id="512b0-132">使用 Transact-SQL 将数据库转换为部分包含的数据库</span><span class="sxs-lookup"><span data-stu-id="512b0-132">Converting a Database to Partially Contained Using Transact-SQL</span></span>  
 <span data-ttu-id="512b0-133">下面的示例将名为 `Accounting` 的数据库转换为部分包含的数据库。</span><span class="sxs-lookup"><span data-stu-id="512b0-133">The following example converts a database named `Accounting` to a partially contained database.</span></span>  
  
```sql  
USE [master]  
GO  
ALTER DATABASE [Accounting] SET CONTAINMENT = PARTIAL  
GO  
```  
  
### <a name="converting-a-database-to-partially-contained-using-management-studio"></a><span data-ttu-id="512b0-134">使用 Management Studio 将数据库转换为部分包含的数据库</span><span class="sxs-lookup"><span data-stu-id="512b0-134">Converting a Database to Partially contained Using Management Studio</span></span>  
 <span data-ttu-id="512b0-135">下面的示例将数据库转换为部分包含的数据库。</span><span class="sxs-lookup"><span data-stu-id="512b0-135">The following example converts a database to a partially contained database.</span></span>  
  
1.  <span data-ttu-id="512b0-136">在对象资源管理器中，展开“数据库”  ，右键单击要转换的数据库，然后单击“属性”  。</span><span class="sxs-lookup"><span data-stu-id="512b0-136">In Object Explorer, expand **Databases**, right-click the database to be converted, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="512b0-137">在 **“选项”** 页面上，将 **“包含类型”** 选项更改为 **“部分”** 。</span><span class="sxs-lookup"><span data-stu-id="512b0-137">On the **Options** page, change the **Containment type** option to **Partial**.</span></span>  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="migrating-users-to-contained-database-users"></a><a name="users"></a> <span data-ttu-id="512b0-138">将用户迁移为包含的数据库用户</span><span class="sxs-lookup"><span data-stu-id="512b0-138">Migrating Users to Contained Database Users</span></span>  
 <span data-ttu-id="512b0-139">以下示例将所有基于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名的用户迁移到具有密码的包含数据库用户。</span><span class="sxs-lookup"><span data-stu-id="512b0-139">The following example migrates all users that are based on [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] logins to contained database users with passwords.</span></span> <span data-ttu-id="512b0-140">该示例不包括未启用的登录名。</span><span class="sxs-lookup"><span data-stu-id="512b0-140">The example excludes logins that are not enabled.</span></span> <span data-ttu-id="512b0-141">必须在包含的数据库中执行该示例。</span><span class="sxs-lookup"><span data-stu-id="512b0-141">The example must be executed in the contained database.</span></span>  
  
```sql  
DECLARE @username sysname ;  
DECLARE user_cursor CURSOR  
    FOR   
        SELECT dp.name   
        FROM sys.database_principals AS dp  
        JOIN sys.server_principals AS sp   
        ON dp.sid = sp.sid  
        WHERE dp.authentication_type = 1 AND sp.is_disabled = 0;  
OPEN user_cursor  
FETCH NEXT FROM user_cursor INTO @username  
    WHILE @@FETCH_STATUS = 0  
    BEGIN  
        EXECUTE sp_migrate_user_to_contained   
        @username = @username,  
        @rename = N'keep_name',  
        @disablelogin = N'disable_login';  
    FETCH NEXT FROM user_cursor INTO @username  
    END  
CLOSE user_cursor ;  
DEALLOCATE user_cursor ;  
```  
  
## <a name="see-also"></a><span data-ttu-id="512b0-142">另请参阅</span><span class="sxs-lookup"><span data-stu-id="512b0-142">See Also</span></span>  
 <span data-ttu-id="512b0-143">[包含的数据库](contained-databases.md) </span><span class="sxs-lookup"><span data-stu-id="512b0-143">[Contained Databases](contained-databases.md) </span></span>  
 <span data-ttu-id="512b0-144">[sp_migrate_user_to_contained (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-migrate-user-to-contained-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="512b0-144">[sp_migrate_user_to_contained &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-migrate-user-to-contained-transact-sql) </span></span>  
 [<span data-ttu-id="512b0-145">sys.dm_db_uncontained_entities (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="512b0-145">sys.dm_db_uncontained_entities &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-uncontained-entities-transact-sql)  
  
  
