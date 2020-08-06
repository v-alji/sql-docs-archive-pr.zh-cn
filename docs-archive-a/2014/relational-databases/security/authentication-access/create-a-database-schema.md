---
title: 创建数据库架构 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.swb.schemas.general.f1
helpviewer_keywords:
- creating schemas with Management Studio
- CREATE SCHEMA [Management Studio]
- database schemas
- schemas [SQL Server], creating
ms.assetid: ed2a5522-f4d2-4111-95a4-d3e1e5081739
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 3ac0c00768db6501c7d786c35758c1a9d75a5a7b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688768"
---
# <a name="create-a-database-schema"></a><span data-ttu-id="b0c7f-102">创建数据库架构</span><span class="sxs-lookup"><span data-stu-id="b0c7f-102">Create a Database Schema</span></span>
  <span data-ttu-id="b0c7f-103">本主题说明如何使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../../includes/tsql-md.md)]中创建架构。</span><span class="sxs-lookup"><span data-stu-id="b0c7f-103">This topic describes how to create a schema in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="b0c7f-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="b0c7f-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="b0c7f-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="b0c7f-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="b0c7f-106">限制和局限</span><span class="sxs-lookup"><span data-stu-id="b0c7f-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="b0c7f-107">安全性</span><span class="sxs-lookup"><span data-stu-id="b0c7f-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="b0c7f-108">**若要创建架构，可使用：**</span><span class="sxs-lookup"><span data-stu-id="b0c7f-108">**To create a schema, using:**</span></span>  
  
     [<span data-ttu-id="b0c7f-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="b0c7f-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="b0c7f-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="b0c7f-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="b0c7f-111">开始之前</span><span class="sxs-lookup"><span data-stu-id="b0c7f-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="b0c7f-112">限制和局限</span><span class="sxs-lookup"><span data-stu-id="b0c7f-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="b0c7f-113">新架构由以下数据库级别主体之一拥有：数据库用户、数据库角色或应用程序角色。</span><span class="sxs-lookup"><span data-stu-id="b0c7f-113">The new schema is owned by one of the following database-level principals: database user, database role, or application role.</span></span> <span data-ttu-id="b0c7f-114">在架构内创建的对象由架构所有者拥有，这些对象在 **sys.objects** 中的 **principal_id**为 NULL。</span><span class="sxs-lookup"><span data-stu-id="b0c7f-114">Objects created within a schema are owned by the owner of the schema, and have a NULL **principal_id** in **sys.objects**.</span></span> <span data-ttu-id="b0c7f-115">架构所包含对象的所有权可转让给任何数据库级主体，但架构所有者始终保留对该架构内对象的 CONTROL 权限。</span><span class="sxs-lookup"><span data-stu-id="b0c7f-115">Ownership of schema-contained objects can be transferred to any database-level principal, but the schema owner always retains CONTROL permission on objects within the schema.</span></span>  
  
-   <span data-ttu-id="b0c7f-116">在创建数据库对象时，如果您将某一有效的域主体（用户或组）指定为对象所有者，则该域主体将作为架构添加到数据库中。</span><span class="sxs-lookup"><span data-stu-id="b0c7f-116">When creating a database object, if you specify a valid domain principal (user or group) as the object owner, the domain principal will be added to the database as a schema.</span></span> <span data-ttu-id="b0c7f-117">这个新架构将为该域主体所拥有。</span><span class="sxs-lookup"><span data-stu-id="b0c7f-117">The new schema will be owned by that domain principal.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="b0c7f-118">Security</span><span class="sxs-lookup"><span data-stu-id="b0c7f-118">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="b0c7f-119">权限</span><span class="sxs-lookup"><span data-stu-id="b0c7f-119">Permissions</span></span>  
  
-   <span data-ttu-id="b0c7f-120">需要对数据库拥有 CREATE SCHEMA 权限。</span><span class="sxs-lookup"><span data-stu-id="b0c7f-120">Requires CREATE SCHEMA permission on the database.</span></span>  
  
-   <span data-ttu-id="b0c7f-121">若要指定其他用户作为所创建架构的所有者，则调用方必须具有对该用户的 IMPERSONATE 权限。</span><span class="sxs-lookup"><span data-stu-id="b0c7f-121">To specify another user as the owner of the schema being created, the caller must have IMPERSONATE permission on that user.</span></span> <span data-ttu-id="b0c7f-122">如果指定一个数据库角色作为所有者，则调用方必须拥有该角色的成员身份或对该角色拥有 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="b0c7f-122">If a database role is specified as the owner, the caller must have one of the following: membership in the role or ALTER permission on the role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="b0c7f-123">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="b0c7f-123">Using SQL Server Management Studio</span></span>  
  
##### <a name="to-create-a-schema"></a><span data-ttu-id="b0c7f-124">创建架构</span><span class="sxs-lookup"><span data-stu-id="b0c7f-124">To create a schema</span></span>  
  
1.  <span data-ttu-id="b0c7f-125">在对象资源管理器中，展开 **“数据库”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="b0c7f-125">In Object Explorer, expand the **Databases** folder.</span></span>  
  
2.  <span data-ttu-id="b0c7f-126">展开要在其中创建新数据库架构的数据库。</span><span class="sxs-lookup"><span data-stu-id="b0c7f-126">Expand the database in which to create the new database schema.</span></span>  
  
3.  <span data-ttu-id="b0c7f-127">右键单击“安全性”文件夹，指向“新建”，并选择“架构”  。</span><span class="sxs-lookup"><span data-stu-id="b0c7f-127">Right-click the **Security** folder, point to **New**, and select **Schema**.</span></span>  
  
4.  <span data-ttu-id="b0c7f-128">在“架构 - 新建”对话框中的“常规”页上，在“架构名称”框中输入新架构的名称  。</span><span class="sxs-lookup"><span data-stu-id="b0c7f-128">In the **Schema - New** dialog box, on the **General** page, enter a name for the new schema in the **Schema name** box.</span></span>  
  
5.  <span data-ttu-id="b0c7f-129">在 **“架构所有者”** 框中，输入要拥有该架构的数据库用户或角色的名称。</span><span class="sxs-lookup"><span data-stu-id="b0c7f-129">In the **Schema owner** box, enter the name of a database user or role to own the schema.</span></span> <span data-ttu-id="b0c7f-130">或者，单击 **“搜索”** 以打开 **“搜索角色和用户”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="b0c7f-130">Alternately, click **Search** to open the **Search Roles and Users** dialog box.</span></span>  
  
6.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### <a name="additional-options"></a><span data-ttu-id="b0c7f-131">其他选项</span><span class="sxs-lookup"><span data-stu-id="b0c7f-131">Additional Options</span></span>  
 <span data-ttu-id="b0c7f-132">“架构 - 新建”对话框还在两个其他页上提供了选项：“权限”和“扩展属性” 。</span><span class="sxs-lookup"><span data-stu-id="b0c7f-132">The **Schema- New** dialog box also offers options on two additional pages: **Permissions** and **Extended Properties**.</span></span>  
  
-   <span data-ttu-id="b0c7f-133">**“权限”** 页将列出所有可能的安全对象以及可授予登录名的针对这些安全对象的权限。</span><span class="sxs-lookup"><span data-stu-id="b0c7f-133">The **Permissions** page lists all possible securables and the permissions on those securables that can be granted to the login.</span></span>  
  
-   <span data-ttu-id="b0c7f-134">**“扩展属性”** 页允许您向数据库用户添加自定义属性。</span><span class="sxs-lookup"><span data-stu-id="b0c7f-134">The **Extended properties** page allows you to add custom properties to database users.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="b0c7f-135">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="b0c7f-135">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-schema"></a><span data-ttu-id="b0c7f-136">创建架构</span><span class="sxs-lookup"><span data-stu-id="b0c7f-136">To create a schema</span></span>  
  
1.  <span data-ttu-id="b0c7f-137">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="b0c7f-137">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="b0c7f-138">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="b0c7f-138">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="b0c7f-139">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="b0c7f-139">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- Creates the schema Sprockets owned by Annik that contains table NineProngs.   
    -- The statement grants SELECT to Mandar and denies SELECT to Prasanna.  
  
    CREATE SCHEMA Sprockets AUTHORIZATION Annik  
        CREATE TABLE NineProngs (source int, cost int, partnumber int)  
        GRANT SELECT ON SCHEMA::Sprockets TO Mandar  
        DENY SELECT ON SCHEMA::Sprockets TO Prasanna;  
    GO  
    ```  
  
 <span data-ttu-id="b0c7f-140">有关详细信息，请参阅 [CREATE SCHEMA (Transact-SQL)](/sql/t-sql/statements/create-schema-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="b0c7f-140">For more information, see [CREATE SCHEMA &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-schema-transact-sql).</span></span>  
  
  
