---
title: 配置 fill factor 服务器配置选项 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- fill factor option [SQL Server]
ms.assetid: b920ec34-ba8b-4bb8-af53-a3ffd06bafa6
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 02258c92b4a09277d371e605fd4729ba9fda3461
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587602"
---
# <a name="configure-the-fill-factor-server-configuration-option"></a><span data-ttu-id="c952a-102">配置填充因子服务器配置选项</span><span class="sxs-lookup"><span data-stu-id="c952a-102">Configure the fill factor Server Configuration Option</span></span>
  <span data-ttu-id="c952a-103">本主题说明了如何使用 **或** 在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中配置 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] “填充因子” [!INCLUDE[tsql](../../includes/tsql-md.md)]服务器配置选项。</span><span class="sxs-lookup"><span data-stu-id="c952a-103">This topic describes how to configure the **fill factor** server configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="c952a-104">提供填充因子是为了优化索引数据存储和性能。</span><span class="sxs-lookup"><span data-stu-id="c952a-104">Fill factor is provided for fine-tuning index data storage and performance.</span></span> <span data-ttu-id="c952a-105">当创建或重新生成索引时，填充因子的值可确定每个叶级页上要填充数据的空间百分比，以便保留一些剩余空间作为以后扩展索引的可用空间。</span><span class="sxs-lookup"><span data-stu-id="c952a-105">When an index is created or rebuilt, the fill-factor value determines the percentage of space on each leaf-level page to be filled with data, reserving the rest as free space for future growth.</span></span> <span data-ttu-id="c952a-106">有关详细信息，请参阅 [为索引指定填充因子](../../relational-databases/indexes/specify-fill-factor-for-an-index.md)。</span><span class="sxs-lookup"><span data-stu-id="c952a-106">For more information, see [Specify Fill Factor for an Index](../../relational-databases/indexes/specify-fill-factor-for-an-index.md).</span></span>  
  
 <span data-ttu-id="c952a-107">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="c952a-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="c952a-108">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="c952a-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="c952a-109">建议</span><span class="sxs-lookup"><span data-stu-id="c952a-109">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="c952a-110">安全性</span><span class="sxs-lookup"><span data-stu-id="c952a-110">Security</span></span>](#Security)  
  
-   <span data-ttu-id="c952a-111">**要配置填充因子选项，请使用：**</span><span class="sxs-lookup"><span data-stu-id="c952a-111">**To configure the fill factor option, using:**</span></span>  
  
     [<span data-ttu-id="c952a-112">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="c952a-112">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="c952a-113">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="c952a-113">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="c952a-114">**跟进：** [在配置填充因子选项之后](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="c952a-114">**Follow Up:**  [After you configure the fill factor option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="c952a-115">开始之前</span><span class="sxs-lookup"><span data-stu-id="c952a-115">Before You Begin</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="c952a-116">建议</span><span class="sxs-lookup"><span data-stu-id="c952a-116">Recommendations</span></span>  
  
-   <span data-ttu-id="c952a-117">此选项是一个高级选项，仅应由有经验的数据库管理员或认证的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 技术人员更改。</span><span class="sxs-lookup"><span data-stu-id="c952a-117">This option is an advanced option and should be changed only by an experienced database administrator or certified [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] technician.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="c952a-118">Security</span><span class="sxs-lookup"><span data-stu-id="c952a-118">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="c952a-119">权限</span><span class="sxs-lookup"><span data-stu-id="c952a-119">Permissions</span></span>  
 <span data-ttu-id="c952a-120">默认情况下，所有用户都具备不带参数或仅带第一个参数的 **sp_configure** 的执行权限。</span><span class="sxs-lookup"><span data-stu-id="c952a-120">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="c952a-121">若要执行带两个参数的 **sp_configure** 以更改配置选项或运行 RECONFIGURE 语句，则用户必须具备 ALTER SETTINGS 服务器级别的权限。</span><span class="sxs-lookup"><span data-stu-id="c952a-121">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="c952a-122">ALTER SETTINGS 权限由 **sysadmin** 和 **serveradmin** 固定服务器角色隐式持有。</span><span class="sxs-lookup"><span data-stu-id="c952a-122">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="c952a-123">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="c952a-123">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-the-fill-factor-option"></a><span data-ttu-id="c952a-124">配置填充因子选项</span><span class="sxs-lookup"><span data-stu-id="c952a-124">To configure the fill factor option</span></span>  
  
1.  <span data-ttu-id="c952a-125">在对象资源管理器中，右键单击服务器并选择 **“属性”** 。</span><span class="sxs-lookup"><span data-stu-id="c952a-125">In Object Explorer, right-click a server and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="c952a-126">单击 **“数据库设置”** 节点。</span><span class="sxs-lookup"><span data-stu-id="c952a-126">Click the **Database Settings** node.</span></span>  
  
3.  <span data-ttu-id="c952a-127">在 **“默认索引填充因子”** 框中，键入或选择所需的索引填充因子。</span><span class="sxs-lookup"><span data-stu-id="c952a-127">In the **Default index fill factor** box, type or select the index fill factor that you want.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="c952a-128">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="c952a-128">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-the-fill-factor-option"></a><span data-ttu-id="c952a-129">配置填充因子选项</span><span class="sxs-lookup"><span data-stu-id="c952a-129">To configure the fill factor option</span></span>  
  
1.  <span data-ttu-id="c952a-130">连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="c952a-130">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="c952a-131">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="c952a-131">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="c952a-132">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="c952a-132">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="c952a-133">此示例说明如何使用 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) 将 `fill factor` 选项的值设置为 `100`。</span><span class="sxs-lookup"><span data-stu-id="c952a-133">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to set the value of the `fill factor` option to `100`.</span></span>  
  
```sql  
Use AdventureWorks2012;  
GO  
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'fill factor', 100;  
GO  
RECONFIGURE;  
GO  
```  
  
 <span data-ttu-id="c952a-134">有关详细信息，请参阅 [服务器配置选项 (SQL Server)](server-configuration-options-sql-server.md)版本的组合自动配置的最大工作线程数。</span><span class="sxs-lookup"><span data-stu-id="c952a-134">For more information, see [Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="follow-up-after-you-configure-the-fill-factor-option"></a><a name="FollowUp"></a> <span data-ttu-id="c952a-135">跟进：在配置填充因子选项之后</span><span class="sxs-lookup"><span data-stu-id="c952a-135">Follow Up: After you configure the fill factor option</span></span>  
 <span data-ttu-id="c952a-136">必须重新启动服务器，设置才会生效。</span><span class="sxs-lookup"><span data-stu-id="c952a-136">The server must be restarted before the setting can take effect.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c952a-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c952a-137">See Also</span></span>  
 <span data-ttu-id="c952a-138">[RECONFIGURE (Transact-SQL)](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c952a-138">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="c952a-139">[ALTER INDEX (Transact-SQL)](/sql/t-sql/statements/alter-index-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c952a-139">[ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql) </span></span>  
 <span data-ttu-id="c952a-140">[CREATE INDEX (Transact-SQL)](/sql/t-sql/statements/create-index-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c952a-140">[CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql) </span></span>  
 <span data-ttu-id="c952a-141">[为索引指定填充因子](../../relational-databases/indexes/specify-fill-factor-for-an-index.md) </span><span class="sxs-lookup"><span data-stu-id="c952a-141">[Specify Fill Factor for an Index](../../relational-databases/indexes/specify-fill-factor-for-an-index.md) </span></span>  
 <span data-ttu-id="c952a-142">[服务器配置选项 (SQL Server)](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="c952a-142">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="c952a-143">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c952a-143">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span></span>  
 [<span data-ttu-id="c952a-144">sys.indexes (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="c952a-144">sys.indexes &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-indexes-transact-sql)  
  
  
