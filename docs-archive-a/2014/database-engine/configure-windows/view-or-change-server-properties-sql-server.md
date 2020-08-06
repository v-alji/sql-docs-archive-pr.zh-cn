---
title: 查看或更改服务器属性 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- viewing server properties
- server properties [SQL Server]
- displaying server properties
- servers [SQL Server], viewing
ms.assetid: 55f3ac04-5626-4ad2-96bd-a1f1b079659d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 415d4e2d1aaa3166ae4df2dea53b34e064544e06
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688192"
---
# <a name="view-or-change-server-properties-sql-server"></a><span data-ttu-id="b229c-102">查看或更改服务器属性 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="b229c-102">View or Change Server Properties (SQL Server)</span></span>
  <span data-ttu-id="b229c-103">本主题说明如何使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]或 SQL Server 配置管理器查看或更改 [!INCLUDE[tsql](../../includes/tsql-md.md)]实例的属性。</span><span class="sxs-lookup"><span data-stu-id="b229c-103">This topic describes how to view or change the properties of an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or SQL Server Configuration Manager.</span></span>  
  
 <span data-ttu-id="b229c-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="b229c-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="b229c-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="b229c-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="b229c-106">限制和局限</span><span class="sxs-lookup"><span data-stu-id="b229c-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="b229c-107">安全性</span><span class="sxs-lookup"><span data-stu-id="b229c-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="b229c-108">**若要查看或更改服务器属性，请使用：**</span><span class="sxs-lookup"><span data-stu-id="b229c-108">**To view or change server properties, using:**</span></span>  
  
     [<span data-ttu-id="b229c-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="b229c-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="b229c-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="b229c-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="b229c-111">SQL Server 配置管理器</span><span class="sxs-lookup"><span data-stu-id="b229c-111">SQL Server Configuration Manager</span></span>](#PowerShellProcedure)  
  
-   <span data-ttu-id="b229c-112">**跟进：**  [更改服务器属性之后](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="b229c-112">**Follow Up:**  [After you change server properties](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="b229c-113">开始之前</span><span class="sxs-lookup"><span data-stu-id="b229c-113">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="b229c-114">限制和局限</span><span class="sxs-lookup"><span data-stu-id="b229c-114">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="b229c-115">使用 sp_configure 时，必须在设置配置选项之后运行 RECONFIGURE 或 RECONFIGURE WITH OVERRIDE。</span><span class="sxs-lookup"><span data-stu-id="b229c-115">When using sp_configure, you must run either RECONFIGURE or RECONFIGURE WITH OVERRIDE after setting a configuration option.</span></span> <span data-ttu-id="b229c-116">RECONFIGURE WITH OVERRIDE 语句通常专门用来设置那些使用起来应当十分小心的配置选项。</span><span class="sxs-lookup"><span data-stu-id="b229c-116">The RECONFIGURE WITH OVERRIDE statement is usually reserved for configuration options that should be used with extreme caution.</span></span> <span data-ttu-id="b229c-117">但是，RECONFIGURE WITH OVERRIDE 可用于所有的配置选项，并且可以用它代替 RECONFIGURE。</span><span class="sxs-lookup"><span data-stu-id="b229c-117">However, RECONFIGURE WITH OVERRIDE works for all configuration options, and you can use it in place of RECONFIGURE.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="b229c-118">RECONFIGURE 在事务内部执行。</span><span class="sxs-lookup"><span data-stu-id="b229c-118">RECONFIGURE executes within a transaction.</span></span> <span data-ttu-id="b229c-119">如果任意重新配置选项失败，则所有重新配置操作都将失效。</span><span class="sxs-lookup"><span data-stu-id="b229c-119">If any of the reconfigure operations fail, none of the reconfigure operations will take effect.</span></span>  
  
-   <span data-ttu-id="b229c-120">有些属性页会显示通过 Windows Management Instrumentation (WMI) 获得的信息。</span><span class="sxs-lookup"><span data-stu-id="b229c-120">Some property pages present information obtained via Windows Management Instrumentation (WMI).</span></span> <span data-ttu-id="b229c-121">若要显示这些页，WMI 必须安装在运行 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]的计算机上。</span><span class="sxs-lookup"><span data-stu-id="b229c-121">To display those pages, WMI must be installed on the computer running [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="b229c-122">Security</span><span class="sxs-lookup"><span data-stu-id="b229c-122">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="b229c-123">权限</span><span class="sxs-lookup"><span data-stu-id="b229c-123">Permissions</span></span>  
 <span data-ttu-id="b229c-124">有关详细信息，请参阅 [服务器级别角色](../../relational-databases/security/authentication-access/server-level-roles.md)。</span><span class="sxs-lookup"><span data-stu-id="b229c-124">For more information, see [Server-Level Roles](../../relational-databases/security/authentication-access/server-level-roles.md).</span></span>  
  
 <span data-ttu-id="b229c-125">`sp_configure`默认情况下，不带参数的执行权限或仅将第一个参数授予所有用户。</span><span class="sxs-lookup"><span data-stu-id="b229c-125">Execute permissions on `sp_configure` with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="b229c-126">若要 `sp_configure` 使用这两个参数来更改配置选项或运行重新配置语句，必须向用户授予 ALTER SETTINGS 服务器级别权限。</span><span class="sxs-lookup"><span data-stu-id="b229c-126">To execute `sp_configure` with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="b229c-127">ALTER SETTINGS 权限由 **sysadmin** 和 **serveradmin** 固定服务器角色隐式持有。</span><span class="sxs-lookup"><span data-stu-id="b229c-127">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="b229c-128">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="b229c-128">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-or-change-server-properties"></a><span data-ttu-id="b229c-129">查看或更改服务器属性</span><span class="sxs-lookup"><span data-stu-id="b229c-129">To view or change server properties</span></span>  
  
1.  <span data-ttu-id="b229c-130">在“对象资源管理器”中，右键单击服务器，再单击“属性” 。</span><span class="sxs-lookup"><span data-stu-id="b229c-130">In Object Explorer, right-click a server, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="b229c-131">在 **“服务器属性”** 对话框中，单击某页以查看或更改有关该页的服务器信息。</span><span class="sxs-lookup"><span data-stu-id="b229c-131">In the **Server Properties** dialog box, click a page to view or change server information about that page.</span></span> <span data-ttu-id="b229c-132">某些属性是只读属性。</span><span class="sxs-lookup"><span data-stu-id="b229c-132">Some properties are read-only.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="b229c-133">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="b229c-133">Using Transact-SQL</span></span>  
  
#### <a name="to-view-server-properties-by-using-the-serverproperty-built-in-function"></a><span data-ttu-id="b229c-134">通过使用 SERVERPROPERTY 内置函数查看服务器属性</span><span class="sxs-lookup"><span data-stu-id="b229c-134">To view server properties by using the SERVERPROPERTY built-in function</span></span>  
  
1.  <span data-ttu-id="b229c-135">连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b229c-135">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="b229c-136">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="b229c-136">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="b229c-137">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="b229c-137">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="b229c-138">此示例在 [语句中使用](/sql/t-sql/functions/serverproperty-transact-sql) SERVERPROPERTY `SELECT` 内置函数，以返回有关当前服务器的信息。</span><span class="sxs-lookup"><span data-stu-id="b229c-138">This example uses the [SERVERPROPERTY](/sql/t-sql/functions/serverproperty-transact-sql) built-in function in a `SELECT` statement to return information about the current server.</span></span> <span data-ttu-id="b229c-139">如果基于 Windows 的服务器上安装了多个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例，而且客户端必须打开另一个到当前连接所使用的同一实例连接，则此方案很有用。</span><span class="sxs-lookup"><span data-stu-id="b229c-139">This scenario is useful when there are multiple instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installed on a Windows-based server, and the client must open another connection to the same instance that is used by the current connection.</span></span>  
  
    ```sql  
    SELECT CONVERT( sysname, SERVERPROPERTY('servername'));  
    GO  
    ```  
  
#### <a name="to-view-server-properties-by-using-the-sysservers-catalog-view"></a><span data-ttu-id="b229c-140">通过使用 sys.servers 目录视图查看服务器属性</span><span class="sxs-lookup"><span data-stu-id="b229c-140">To view server properties by using the sys.servers catalog view</span></span>  
  
1.  <span data-ttu-id="b229c-141">连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b229c-141">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="b229c-142">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="b229c-142">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="b229c-143">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="b229c-143">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="b229c-144">此示例查询 [sys.servers](/sql/relational-databases/system-catalog-views/sys-servers-transact-sql) 目录视图，以返回当前服务器的名称 (`name`) 和 ID (`server_id`)，以及用于连接到链接服务器的 OLE DB 访问接口 (`provider`) 的名称。</span><span class="sxs-lookup"><span data-stu-id="b229c-144">This example queries the [sys.servers](/sql/relational-databases/system-catalog-views/sys-servers-transact-sql) catalog view to return the name (`name`) and ID (`server_id`) of the current server, and the name of the OLE DB provider (`provider`) for connecting to a linked server.</span></span>  
  
    ```sql  
    USE AdventureWorks2012;   
    GO  
    SELECT name, server_id, provider  
    FROM sys.servers ;   
    GO
    ```  
  
#### <a name="to-view-server-properties-by-using-the-sysconfigurations-catalog-view"></a><span data-ttu-id="b229c-145">通过使用 sys.configurations 目录视图查看服务器属性</span><span class="sxs-lookup"><span data-stu-id="b229c-145">To view server properties by using the sys.configurations catalog view</span></span>  
  
1.  <span data-ttu-id="b229c-146">连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b229c-146">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="b229c-147">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="b229c-147">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="b229c-148">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="b229c-148">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="b229c-149">此示例查询 [sys.configurations](/sql/relational-databases/system-catalog-views/sys-configurations-transact-sql) 目录视图，以返回有关当前服务器上的各个服务器配置选项的信息。</span><span class="sxs-lookup"><span data-stu-id="b229c-149">This example queries the [sys.configurations](/sql/relational-databases/system-catalog-views/sys-configurations-transact-sql) catalog view to return information about each server configuration option on the current server.</span></span> <span data-ttu-id="b229c-150">该示例返回选项的名称 (`name`) 和说明 (`description`)，以及该选项是否为高级选项 (`is_advanced`)。</span><span class="sxs-lookup"><span data-stu-id="b229c-150">The example returns the name (`name`) and description (`description`) of the option and whether the option is an advanced option (`is_advanced`).</span></span>  
  
    ```sql
    USE AdventureWorks2012;
    GO  
    SELECT name, description, is_advanced  
    FROM sys.configurations ;
    GO
    ```  
  
#### <a name="to-change-a-server-property-by-using-sp_configure"></a><span data-ttu-id="b229c-151">通过使用 sp_configure 更改服务器属性</span><span class="sxs-lookup"><span data-stu-id="b229c-151">To change a server property by using sp_configure</span></span>  
  
1.  <span data-ttu-id="b229c-152">连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b229c-152">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="b229c-153">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="b229c-153">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="b229c-154">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="b229c-154">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="b229c-155">此示例显示如何使用 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) 更改服务器属性。</span><span class="sxs-lookup"><span data-stu-id="b229c-155">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to change a server property.</span></span> <span data-ttu-id="b229c-156">本示例将 `fill factor` 选项的值更改为 `100`。</span><span class="sxs-lookup"><span data-stu-id="b229c-156">The example changes the value of the `fill factor` option to `100`.</span></span> <span data-ttu-id="b229c-157">必须重新启动服务器，更改才会生效。</span><span class="sxs-lookup"><span data-stu-id="b229c-157">The server must be restarted before the change can take effect.</span></span>  
  
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
  
 <span data-ttu-id="b229c-158">有关详细信息，请参阅 [服务器配置选项 (SQL Server)](server-configuration-options-sql-server.md)版本的组合自动配置的最大工作线程数。</span><span class="sxs-lookup"><span data-stu-id="b229c-158">For more information, see [Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="using-sql-server-configuration-manager"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="b229c-159">使用 SQL Server 配置管理器</span><span class="sxs-lookup"><span data-stu-id="b229c-159">Using SQL Server Configuration Manager</span></span>  
 <span data-ttu-id="b229c-160">可以通过使用 SQL Server 配置管理器查看或更改某些服务器属性。</span><span class="sxs-lookup"><span data-stu-id="b229c-160">Some server properties can be viewed or changed by using SQL Server Configuration Manager.</span></span> <span data-ttu-id="b229c-161">例如，您可以查看 SQL Server 实例的版本，或更改存储错误日志文件的位置。</span><span class="sxs-lookup"><span data-stu-id="b229c-161">For example, you can view the version and edition of the instance of SQL Server, or change the location where error log files are stored.</span></span> <span data-ttu-id="b229c-162">也可以通过查询 [服务器相关的动态管理视图和函数](/sql/relational-databases/system-dynamic-management-views/server-related-dynamic-management-views-and-functions-transact-sql)来查看这些属性。</span><span class="sxs-lookup"><span data-stu-id="b229c-162">These properties can also be viewed by querying the [Server-Related Dynamic Management Views and Functions](/sql/relational-databases/system-dynamic-management-views/server-related-dynamic-management-views-and-functions-transact-sql).</span></span>  
  
#### <a name="to-view-or-change-server-properties"></a><span data-ttu-id="b229c-163">查看或更改服务器属性</span><span class="sxs-lookup"><span data-stu-id="b229c-163">To view or change server properties</span></span>  
  
1.  <span data-ttu-id="b229c-164">在 **“开始”** 菜单中，依次指向 **“所有程序”** 、 [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)]、 **“配置工具”** ，然后单击 **“SQL Server 配置管理器”** 。</span><span class="sxs-lookup"><span data-stu-id="b229c-164">On the **Start** menu, point to **All Programs**, point to [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], point to **Configuration Tools**, and then click **SQL Server Configuration Manager**.</span></span>  
  
2.  <span data-ttu-id="b229c-165">在 **“SQL Server 配置管理器”** 中，单击 **“SQL Server 服务”** 。</span><span class="sxs-lookup"><span data-stu-id="b229c-165">In **SQL Server Configuration Manager**, click **SQL Server Services**.</span></span>  
  
3.  <span data-ttu-id="b229c-166">在“详细信息”窗格中，右键单击“SQL Server (\<***instancename***>)”，再单击“属性” 。</span><span class="sxs-lookup"><span data-stu-id="b229c-166">In the details pane, right-click **SQL Server (\<***instancename***>)**, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="b229c-167">在“SQL Server (\<***instancename***>) 属性”对话框中，更改“服务”选项卡或“高级”选项卡上的服务器属性，再单击“确定”   。</span><span class="sxs-lookup"><span data-stu-id="b229c-167">In the **SQL Server (\<***instancename***>) Properties** dialog box, change the server properties on the **Service** tab or the **Advanced** tab, and then click **OK**.</span></span>  
  
##  <a name="follow-up-after-you-change-server-properties"></a><a name="FollowUp"></a><span data-ttu-id="b229c-168">跟进：更改服务器属性之后</span><span class="sxs-lookup"><span data-stu-id="b229c-168">Follow Up: After you change server properties</span></span>  
 <span data-ttu-id="b229c-169">对于某些属性，可能必须重新启动服务器，才能使更改生效。</span><span class="sxs-lookup"><span data-stu-id="b229c-169">For some properties, the server might have to be restarted before the change can take effect.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b229c-170">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b229c-170">See Also</span></span>  
 <span data-ttu-id="b229c-171">[服务器配置选项 (SQL Server)](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="b229c-171">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="b229c-172">[SET 语句 (Transact-SQL)](/sql/t-sql/statements/set-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b229c-172">[SET Statements &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-statements-transact-sql) </span></span>  
 <span data-ttu-id="b229c-173">[SERVERPROPERTY (Transact-SQL)](/sql/t-sql/functions/serverproperty-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b229c-173">[SERVERPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/serverproperty-transact-sql) </span></span>  
 <span data-ttu-id="b229c-174">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b229c-174">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span></span>  
 <span data-ttu-id="b229c-175">[RECONFIGURE (Transact-SQL)](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b229c-175">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="b229c-176">[SELECT (Transact-SQL)](/sql/t-sql/queries/select-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b229c-176">[SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql) </span></span>  
 <span data-ttu-id="b229c-177">[在 SQL Server 工具中将 WMI 配置为显示服务器状态](../../ssms/configure-wmi-to-show-server-status-in-sql-server-tools.md) </span><span class="sxs-lookup"><span data-stu-id="b229c-177">[Configure WMI to Show Server Status in SQL Server Tools](../../ssms/configure-wmi-to-show-server-status-in-sql-server-tools.md) </span></span>  
 <span data-ttu-id="b229c-178">[SQL Server 配置管理器](../../relational-databases/sql-server-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="b229c-178">[SQL Server Configuration Manager](../../relational-databases/sql-server-configuration-manager.md) </span></span>  
 <span data-ttu-id="b229c-179">[配置函数 (Transact-SQL)](/sql/t-sql/functions/configuration-functions-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b229c-179">[Configuration Functions &#40;Transact-SQL&#41;](/sql/t-sql/functions/configuration-functions-transact-sql) </span></span>  
 [<span data-ttu-id="b229c-180">与服务器相关的动态管理视图和函数 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="b229c-180">Server-Related Dynamic Management Views and Functions &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/server-related-dynamic-management-views-and-functions-transact-sql)  
