---
title: 配置 remote login timeout 服务器配置选项 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- remote login timeout option
ms.assetid: 077adebe-0e3f-42a5-a75e-5e6d04847e2b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 58b3405f9b0e51bd43edcaa31e84c8ebbcc48547
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578424"
---
# <a name="configure-the-remote-login-timeout-server-configuration-option"></a><span data-ttu-id="f545a-102">配置 remote login timeout 服务器配置选项</span><span class="sxs-lookup"><span data-stu-id="f545a-102">Configure the remote login timeout Server Configuration Option</span></span>
  <span data-ttu-id="f545a-103">本主题说明如何使用 **或** 在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中配置 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] remote login timeout [!INCLUDE[tsql](../../includes/tsql-md.md)]服务器配置选项。</span><span class="sxs-lookup"><span data-stu-id="f545a-103">This topic describes how to configure the **remote login timeout** server configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="f545a-104">**remote login timeout** 选项指定从登录远程服务器失败返回前等待的秒数。</span><span class="sxs-lookup"><span data-stu-id="f545a-104">The **remote login timeout** option specifies the number of seconds to wait before returning from a failed attempt to log in to a remote server.</span></span> <span data-ttu-id="f545a-105">例如，如果您尝试登录到一个远程服务器而该服务器已关闭， **remote login timeout** 帮助确保您在计算机停止登录尝试前不必无限期地等待下去。</span><span class="sxs-lookup"><span data-stu-id="f545a-105">For example, if you are trying to log in to a remote server and that server is down, **remote login timeout** helps make sure that you do not have to wait indefinitely before your computer stops trying to log in.</span></span> <span data-ttu-id="f545a-106">此选项的默认值为 10 秒。</span><span class="sxs-lookup"><span data-stu-id="f545a-106">The default value for this option is 10 seconds.</span></span> <span data-ttu-id="f545a-107">如果该值为 0，则允许无限期等待。</span><span class="sxs-lookup"><span data-stu-id="f545a-107">A value of 0 allows for an infinite wait.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f545a-108">此选项的默认值在 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]中为 20 秒。</span><span class="sxs-lookup"><span data-stu-id="f545a-108">The default value for this option is 20 seconds in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].</span></span>  
  
 <span data-ttu-id="f545a-109">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="f545a-109">**In This Topic**</span></span>  
  
-   <span data-ttu-id="f545a-110">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="f545a-110">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="f545a-111">限制和局限</span><span class="sxs-lookup"><span data-stu-id="f545a-111">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="f545a-112">安全性</span><span class="sxs-lookup"><span data-stu-id="f545a-112">Security</span></span>](#Security)  
  
-   <span data-ttu-id="f545a-113">**配置 remote login timeout 选项，使用：**</span><span class="sxs-lookup"><span data-stu-id="f545a-113">**To configure the remote login timeout option, using:**</span></span>  
  
     [<span data-ttu-id="f545a-114">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="f545a-114">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="f545a-115">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="f545a-115">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="f545a-116">**跟进：** [在配置远程登录超时选项之后](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="f545a-116">**Follow Up:**  [After you configure the remote login timeout option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="f545a-117">开始之前</span><span class="sxs-lookup"><span data-stu-id="f545a-117">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="f545a-118">限制和局限</span><span class="sxs-lookup"><span data-stu-id="f545a-118">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="f545a-119">**remote login timeout** 选项影响与 OLE DB 访问接口之间为异类查询建立的连接。</span><span class="sxs-lookup"><span data-stu-id="f545a-119">The **remote login timeout** option affects connections to OLE DB providers made for heterogeneous queries.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="f545a-120">Security</span><span class="sxs-lookup"><span data-stu-id="f545a-120">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="f545a-121">权限</span><span class="sxs-lookup"><span data-stu-id="f545a-121">Permissions</span></span>  
 <span data-ttu-id="f545a-122">默认情况下，所有用户都具备不带参数或仅带第一个参数的 **sp_configure** 的执行权限。</span><span class="sxs-lookup"><span data-stu-id="f545a-122">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="f545a-123">若要执行带两个参数的 **sp_configure** 以更改配置选项或运行 RECONFIGURE 语句，则用户必须具备 ALTER SETTINGS 服务器级别的权限。</span><span class="sxs-lookup"><span data-stu-id="f545a-123">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="f545a-124">ALTER SETTINGS 权限由 **sysadmin** 和 **serveradmin** 固定服务器角色隐式持有。</span><span class="sxs-lookup"><span data-stu-id="f545a-124">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="f545a-125">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="f545a-125">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-the-remote-login-timeout-option"></a><span data-ttu-id="f545a-126">配置 remote login timeout 选项</span><span class="sxs-lookup"><span data-stu-id="f545a-126">To configure the remote login timeout option</span></span>  
  
1.  <span data-ttu-id="f545a-127">在对象资源管理器中，右键单击服务器并选择 **“属性”** 。</span><span class="sxs-lookup"><span data-stu-id="f545a-127">In Object Explorer, right-click a server and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="f545a-128">单击 **“高级”** 节点。</span><span class="sxs-lookup"><span data-stu-id="f545a-128">Click the **Advanced** node.</span></span>  
  
3.  <span data-ttu-id="f545a-129">在 **“网络”** 下，为 **“远程登录超时值”** 框选择一个值。</span><span class="sxs-lookup"><span data-stu-id="f545a-129">Under **Network**, select a value for the **Remote Login Timeout** box.</span></span>  
  
     <span data-ttu-id="f545a-130">使用 **remote login timeout** 选项可以指定从远程登录失败返回前等待的秒数。</span><span class="sxs-lookup"><span data-stu-id="f545a-130">Use the **remote login timeout** option to specify the number of seconds to wait before returning from a failed remote login attempt.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="f545a-131">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="f545a-131">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-the-remote-login-timeout-option"></a><span data-ttu-id="f545a-132">配置 remote login timeout 选项</span><span class="sxs-lookup"><span data-stu-id="f545a-132">To configure the remote login timeout option</span></span>  
  
1.  <span data-ttu-id="f545a-133">连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f545a-133">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="f545a-134">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="f545a-134">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="f545a-135">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="f545a-135">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="f545a-136">此示例说明如何使用 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) 将 `remote login timeout` 选项的值设置为 `35` 秒。</span><span class="sxs-lookup"><span data-stu-id="f545a-136">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to set the value of the `remote login timeout` option to `35` seconds.</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'remote login timeout', 35 ;  
GO  
RECONFIGURE ;  
GO  
  
```  
  
 <span data-ttu-id="f545a-137">有关详细信息，请参阅 [服务器配置选项 (SQL Server)](server-configuration-options-sql-server.md)版本的组合自动配置的最大工作线程数。</span><span class="sxs-lookup"><span data-stu-id="f545a-137">For more information, see [Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="follow-up-after-you-configure-the-remote-login-timeout-option"></a><a name="FollowUp"></a> <span data-ttu-id="f545a-138">跟进：在配置远程登录超时选项之后</span><span class="sxs-lookup"><span data-stu-id="f545a-138">Follow Up: After you configure the remote login timeout option</span></span>  
 <span data-ttu-id="f545a-139">该设置将立即生效，无需重新启动服务器。</span><span class="sxs-lookup"><span data-stu-id="f545a-139">The setting takes effect immediately without restarting the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f545a-140">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f545a-140">See Also</span></span>  
 <span data-ttu-id="f545a-141">[RECONFIGURE (Transact-SQL)](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f545a-141">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="f545a-142">[服务器配置选项 (SQL Server)](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="f545a-142">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="f545a-143">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f545a-143">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
