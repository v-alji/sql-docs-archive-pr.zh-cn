---
title: 配置“嵌套触发器”服务器配置选项 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- nested triggers option
ms.assetid: 29d7372b-d406-4a5b-80c6-a2d231d25211
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 7b27e185b0833f2e51be16393ff4d59a81046970
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588043"
---
# <a name="configure-the-nested-triggers-server-configuration-option"></a><span data-ttu-id="63754-102">配置 nested triggers 服务器配置选项</span><span class="sxs-lookup"><span data-stu-id="63754-102">Configure the nested triggers Server Configuration Option</span></span>
  <span data-ttu-id="63754-103">本主题说明如何使用 **或** 在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中配置 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] nested triggers [!INCLUDE[tsql](../../includes/tsql-md.md)]服务器配置选项。</span><span class="sxs-lookup"><span data-stu-id="63754-103">This topic describes how to configure the **nested triggers** server configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="63754-104">**nested triggers** 选项控制 AFTER 触发器是否可以级联。</span><span class="sxs-lookup"><span data-stu-id="63754-104">The **nested triggers** option controls whether an AFTER trigger can cascade.</span></span> <span data-ttu-id="63754-105">即执行某项操作将启动另一个触发器，而该触发器又将启动另外一个，依此类推。</span><span class="sxs-lookup"><span data-stu-id="63754-105">That is, perform an action that initiates another trigger, which initiates another trigger, and so on.</span></span> <span data-ttu-id="63754-106">如果 **nested triggers** 设置为 0，AFTER 触发器不能级联。</span><span class="sxs-lookup"><span data-stu-id="63754-106">When **nested triggers** is set to 0, AFTER triggers cannot cascade.</span></span> <span data-ttu-id="63754-107">如果 **嵌套触发器** 设置为 1（默认值），AFTER 触发器最多能级联 32 级。</span><span class="sxs-lookup"><span data-stu-id="63754-107">When **nested triggers** is set to 1 (the default), AFTER triggers can cascade to as many as 32 levels.</span></span> <span data-ttu-id="63754-108">不管此选项如何设置，INSTEAD OF 触发器都可以嵌套。</span><span class="sxs-lookup"><span data-stu-id="63754-108">INSTEAD OF triggers can be nested regardless of the setting of this option.</span></span>  
  
 <span data-ttu-id="63754-109">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="63754-109">**In This Topic**</span></span>  
  
-   <span data-ttu-id="63754-110">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="63754-110">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="63754-111">安全性</span><span class="sxs-lookup"><span data-stu-id="63754-111">Security</span></span>](#Security)  
  
-   <span data-ttu-id="63754-112">**配置 nested triggers 选项，使用：**</span><span class="sxs-lookup"><span data-stu-id="63754-112">**To configure the nested triggers option, using:**</span></span>  
  
     [<span data-ttu-id="63754-113">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="63754-113">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="63754-114">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="63754-114">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="63754-115">**跟进：** [在配置嵌套触发器选项之后](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="63754-115">**Follow Up:**  [After you configure the nested triggers option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="63754-116">开始之前</span><span class="sxs-lookup"><span data-stu-id="63754-116">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="63754-117">Security</span><span class="sxs-lookup"><span data-stu-id="63754-117">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="63754-118">权限</span><span class="sxs-lookup"><span data-stu-id="63754-118">Permissions</span></span>  
 <span data-ttu-id="63754-119">默认情况下，所有用户都具备不带参数或仅带第一个参数的 **sp_configure** 的执行权限。</span><span class="sxs-lookup"><span data-stu-id="63754-119">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="63754-120">若要执行带两个参数的 **sp_configure** 以更改配置选项或运行 RECONFIGURE 语句，则用户必须具备 ALTER SETTINGS 服务器级别的权限。</span><span class="sxs-lookup"><span data-stu-id="63754-120">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="63754-121">ALTER SETTINGS 权限由 **sysadmin** 和 **serveradmin** 固定服务器角色隐式持有。</span><span class="sxs-lookup"><span data-stu-id="63754-121">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="63754-122">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="63754-122">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-the-nested-triggers-option"></a><span data-ttu-id="63754-123">配置 nested triggers 选项</span><span class="sxs-lookup"><span data-stu-id="63754-123">To configure the nested triggers option</span></span>  
  
1.  <span data-ttu-id="63754-124">在“对象资源管理器”中，右键单击服务器，然后选择“属性”。</span><span class="sxs-lookup"><span data-stu-id="63754-124">In **Object Explorer**, right-click a server, and then select **Properties**.</span></span>  
  
2.  <span data-ttu-id="63754-125">在“高级”页上，将“允许触发器激发其他触发器”选项设置为“True”（默认值）或“False”。</span><span class="sxs-lookup"><span data-stu-id="63754-125">On the **Advanced** page, set the **Allow Triggers to Fire Others** option to **True** (the default) or **False**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="63754-126">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="63754-126">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-the-nested-triggers-option"></a><span data-ttu-id="63754-127">配置 nested triggers 选项</span><span class="sxs-lookup"><span data-stu-id="63754-127">To configure the nested triggers option</span></span>  
  
1.  <span data-ttu-id="63754-128">连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="63754-128">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="63754-129">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="63754-129">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="63754-130">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="63754-130">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="63754-131">此示例说明如何使用 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) 将 `nested triggers` 选项的值设置为 `0`。</span><span class="sxs-lookup"><span data-stu-id="63754-131">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to set the value of the `nested triggers` option to `0`.</span></span>  
  
```wmimof  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE ;  
GO  
EXEC sp_configure 'nested triggers', 0 ;  
GO  
RECONFIGURE;  
GO  
  
```  
  
 <span data-ttu-id="63754-132">有关详细信息，请参阅 [服务器配置选项 (SQL Server)](server-configuration-options-sql-server.md)版本的组合自动配置的最大工作线程数。</span><span class="sxs-lookup"><span data-stu-id="63754-132">For more information, see [Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="follow-up-after-you-configure-the-nested-triggers-option"></a><a name="FollowUp"></a> <span data-ttu-id="63754-133">跟进：在配置嵌套触发器选项之后</span><span class="sxs-lookup"><span data-stu-id="63754-133">Follow Up: After you configure the nested triggers option</span></span>  
 <span data-ttu-id="63754-134">该设置将立即生效，无需重新启动服务器。</span><span class="sxs-lookup"><span data-stu-id="63754-134">The setting takes effect immediately without restarting the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63754-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="63754-135">See Also</span></span>  
 <span data-ttu-id="63754-136">[创建嵌套触发器](../../relational-databases/triggers/create-nested-triggers.md) </span><span class="sxs-lookup"><span data-stu-id="63754-136">[Create Nested Triggers](../../relational-databases/triggers/create-nested-triggers.md) </span></span>  
 <span data-ttu-id="63754-137">[RECONFIGURE (Transact-SQL)](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="63754-137">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="63754-138">[服务器配置选项 (SQL Server)](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="63754-138">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="63754-139">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="63754-139">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
