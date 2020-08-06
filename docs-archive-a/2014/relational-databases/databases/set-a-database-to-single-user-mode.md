---
title: 将数据库设置为单用户模式 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- single-user mode [SQL Server], database option
ms.assetid: fb5254eb-b635-4b39-8361-136fd36f2b1f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 16281b5fa7d4f6698bb6c498915bfa84779b3e14
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682877"
---
# <a name="set-a-database-to-single-user-mode"></a><span data-ttu-id="63073-102">将数据库设置为单用户模式</span><span class="sxs-lookup"><span data-stu-id="63073-102">Set a Database to Single-user Mode</span></span>
  <span data-ttu-id="63073-103">本主题说明了如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中将用户定义数据库设置为单用户模式。</span><span class="sxs-lookup"><span data-stu-id="63073-103">This topic describes how to set a user-defined database to single-user mode in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="63073-104">单用户模式指定一次只有一个用户可访问数据库，该模式通常用于维护操作。</span><span class="sxs-lookup"><span data-stu-id="63073-104">Single-user mode specifies that only one user at a time can access the database and is generally used for maintenance actions.</span></span>  
  
 <span data-ttu-id="63073-105">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="63073-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="63073-106">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="63073-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="63073-107">限制和局限</span><span class="sxs-lookup"><span data-stu-id="63073-107">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="63073-108">先决条件</span><span class="sxs-lookup"><span data-stu-id="63073-108">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="63073-109">安全性</span><span class="sxs-lookup"><span data-stu-id="63073-109">Security</span></span>](#Security)  
  
-   <span data-ttu-id="63073-110">**若要将数据库设置为单用户模式，请使用：**</span><span class="sxs-lookup"><span data-stu-id="63073-110">**To set a database to single-user mode, using:**</span></span>  
  
     [<span data-ttu-id="63073-111">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="63073-111">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="63073-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="63073-112">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="63073-113">开始之前</span><span class="sxs-lookup"><span data-stu-id="63073-113">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="63073-114">限制和局限</span><span class="sxs-lookup"><span data-stu-id="63073-114">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="63073-115">如果其他用户在您将数据库设置为单用户模式时连接到了数据库，则他们与数据库的连接将被关闭，且不发出警告。</span><span class="sxs-lookup"><span data-stu-id="63073-115">If other users are connected to the database at the time that you set the database to single-user mode, their connections to the database will be closed without warning.</span></span>  
  
-   <span data-ttu-id="63073-116">即使设置此选项的用户已注销，数据库仍保持单用户模式。</span><span class="sxs-lookup"><span data-stu-id="63073-116">The database remains in single-user mode even if the user that set the option logs off.</span></span> <span data-ttu-id="63073-117">这时，其他用户（但只能是一个）可以连接到数据库。</span><span class="sxs-lookup"><span data-stu-id="63073-117">At that point, a different user, but only one, can connect to the database.</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a><span data-ttu-id="63073-118">先决条件</span><span class="sxs-lookup"><span data-stu-id="63073-118">Prerequisites</span></span>  
  
-   <span data-ttu-id="63073-119">在将数据库设置为 SINGLE_USER 之前，应验证 AUTO_UPDATE_STATISTICS_ASYNC 选项是否设置为 OFF。</span><span class="sxs-lookup"><span data-stu-id="63073-119">Before you set the database to SINGLE_USER, verify that the AUTO_UPDATE_STATISTICS_ASYNC option is set to OFF.</span></span> <span data-ttu-id="63073-120">在此选项设置为 ON 时，用于更新统计信息的后台线程将与数据库建立连接，您将无法以单用户模式访问数据库。</span><span class="sxs-lookup"><span data-stu-id="63073-120">When this option is set to ON, the background thread that is used to update statistics takes a connection against the database, and you will be unable to access the database in single-user mode.</span></span> <span data-ttu-id="63073-121">有关详细信息，请参阅 [ALTER DATABASE SET 选项 (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql-set-options)。</span><span class="sxs-lookup"><span data-stu-id="63073-121">For more information, see [ALTER DATABASE SET Options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="63073-122">Security</span><span class="sxs-lookup"><span data-stu-id="63073-122">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="63073-123">权限</span><span class="sxs-lookup"><span data-stu-id="63073-123">Permissions</span></span>  
 <span data-ttu-id="63073-124">需要对数据库拥有 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="63073-124">Requires ALTER permission on the database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="63073-125">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="63073-125">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-set-a-database-to-single-user-mode"></a><span data-ttu-id="63073-126">将数据库设置为单用户模式</span><span class="sxs-lookup"><span data-stu-id="63073-126">To set a database to single-user mode</span></span>  
  
1.  <span data-ttu-id="63073-127">在 **对象资源管理器**中，连接到 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]的实例，然后展开该实例。</span><span class="sxs-lookup"><span data-stu-id="63073-127">In **Object Explorer**, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="63073-128">右键单击要更改的数据库，再单击“属性”  。</span><span class="sxs-lookup"><span data-stu-id="63073-128">Right-click the database to change, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="63073-129">在 **“数据库属性”** 对话框中，单击 **“选项”** 页。</span><span class="sxs-lookup"><span data-stu-id="63073-129">In the **Database Properties** dialog box, click the **Options** page.</span></span>  
  
4.  <span data-ttu-id="63073-130">在 **“限制访问”** 选项中，选择 **“单用户”** 。</span><span class="sxs-lookup"><span data-stu-id="63073-130">From the **Restrict Access** option, select **Single**.</span></span>  
  
5.  <span data-ttu-id="63073-131">如果其他用户连接到数据库，将出现 **“打开的连接”** 消息。</span><span class="sxs-lookup"><span data-stu-id="63073-131">If other users are connected to the database, an **Open Connections** message will appear.</span></span> <span data-ttu-id="63073-132">若要更改属性并关闭所有其他连接，请单击 **“是”** 。</span><span class="sxs-lookup"><span data-stu-id="63073-132">To change the property and close all other connections, click **Yes**.</span></span>  
  
 <span data-ttu-id="63073-133">还可以使用此过程将数据库设置为“多用户”访问或“限制”访问。</span><span class="sxs-lookup"><span data-stu-id="63073-133">You can also set the database to Multiple or Restricted access by using this procedure.</span></span> <span data-ttu-id="63073-134">有关此“限制访问”选项的详细信息，请参阅[数据库属性（选项页）](database-properties-options-page.md)。</span><span class="sxs-lookup"><span data-stu-id="63073-134">For more information about the Restrict Access options, see [Database Properties &#40;Options Page&#41;](database-properties-options-page.md).</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="63073-135">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="63073-135">Using Transact-SQL</span></span>  
  
#### <a name="to-set-a-database-to-single-user-mode"></a><span data-ttu-id="63073-136">将数据库设置为单用户模式</span><span class="sxs-lookup"><span data-stu-id="63073-136">To set a database to single-user mode</span></span>  
  
1.  <span data-ttu-id="63073-137">连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="63073-137">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="63073-138">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="63073-138">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="63073-139">将以下示例复制并粘贴到查询窗口中，然后单击“执行”  。</span><span class="sxs-lookup"><span data-stu-id="63073-139">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="63073-140">此示例将数据库设置为 `SINGLE_USER` 模式，以获得独占访问权。</span><span class="sxs-lookup"><span data-stu-id="63073-140">This example sets the database to `SINGLE_USER` mode to obtain exclusive access.</span></span> <span data-ttu-id="63073-141">然后，该示例将 [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] 数据库的状态设置为 `READ_ONLY` ，并将对数据库的访问权返回给所有用户。在第一个 `WITH ROLLBACK IMMEDIATE` 语句中指定终止选项 `ALTER DATABASE` 。</span><span class="sxs-lookup"><span data-stu-id="63073-141">The example then sets the state of the [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] database to `READ_ONLY` and returns access to the database to all users.The termination option `WITH ROLLBACK IMMEDIATE` is specified in the first `ALTER DATABASE` statement.</span></span> <span data-ttu-id="63073-142">这将导致所有未完成事务都将被回滚，并将立刻断开 [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] 示例数据库的所有其他连接。</span><span class="sxs-lookup"><span data-stu-id="63073-142">This will cause all incomplete transactions to be rolled back and any other connections to the [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] database to be immediately disconnected.</span></span>  
  
 [!code-sql[DatabaseDDL#AlterDatabase8](../../snippets/tsql/SQL14/tsql/databaseddl/transact-sql/alterdatabase.sql#alterdatabase8)]  
  
## <a name="see-also"></a><span data-ttu-id="63073-143">另请参阅</span><span class="sxs-lookup"><span data-stu-id="63073-143">See Also</span></span>  
 [<span data-ttu-id="63073-144">ALTER DATABASE (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="63073-144">ALTER DATABASE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-database-transact-sql)  
  
  
