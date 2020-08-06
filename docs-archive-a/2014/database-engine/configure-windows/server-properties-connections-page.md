---
title: 服务器属性（“连接”页）| Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql12.swb.serverproperties.connections.f1
ms.assetid: 33be8ac5-12dd-4b8a-99e0-68261c219dd2
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 80943bc542209fd34cf83e8db7aa76becd04194a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692515"
---
# <a name="server-properties-connections-page"></a><span data-ttu-id="77c12-102">服务器属性（“连接”页）</span><span class="sxs-lookup"><span data-stu-id="77c12-102">Server Properties (Connections Page)</span></span>
  <span data-ttu-id="77c12-103">使用此页可以查看或修改连接选项。</span><span class="sxs-lookup"><span data-stu-id="77c12-103">Use this page to view or modify your connection options.</span></span>  
  
## <a name="connections"></a><span data-ttu-id="77c12-104">连接</span><span class="sxs-lookup"><span data-stu-id="77c12-104">Connections</span></span>  
 <span data-ttu-id="77c12-105">**最大并发连接数(0 = 无限制)**</span><span class="sxs-lookup"><span data-stu-id="77c12-105">**Maximum number of concurrent connections (0 = unlimited)**</span></span>  
 <span data-ttu-id="77c12-106">如果设置为非零值，则将限制 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 允许的连接数。</span><span class="sxs-lookup"><span data-stu-id="77c12-106">If set to a value other than zero, limits the number of connections that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will allow.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="77c12-107">如果将此值设置为较小的值（如 1 或 2），则可能会阻止管理员进行连接以管理该服务器；但是“专用管理员连接”始终可以连接。</span><span class="sxs-lookup"><span data-stu-id="77c12-107">Setting this to a small value, such as 1 or 2, can prevent administrators from connecting to administer the server; however, the Dedicated Admin Connection can always connect.</span></span>  
  
## <a name="default-connection-options"></a><span data-ttu-id="77c12-108">默认连接选项</span><span class="sxs-lookup"><span data-stu-id="77c12-108">Default Connection Options</span></span>  
 <span data-ttu-id="77c12-109">**Default connection options**</span><span class="sxs-lookup"><span data-stu-id="77c12-109">**Default connection options**</span></span>  
 <span data-ttu-id="77c12-110">指定默认连接选项，如下表所述：</span><span class="sxs-lookup"><span data-stu-id="77c12-110">Specifies the default connection options, as described in the following table.</span></span>  
  
|<span data-ttu-id="77c12-111">配置选项</span><span class="sxs-lookup"><span data-stu-id="77c12-111">Configuration option</span></span>|<span data-ttu-id="77c12-112">说明</span><span class="sxs-lookup"><span data-stu-id="77c12-112">Description</span></span>|  
|--------------------------|-----------------|  
|<span data-ttu-id="77c12-113">**disable deferred constraint checking**</span><span class="sxs-lookup"><span data-stu-id="77c12-113">**disable deferred constraint checking**</span></span>|<span data-ttu-id="77c12-114">控制执行期间或延迟的约束检查。</span><span class="sxs-lookup"><span data-stu-id="77c12-114">Controls interim or deferred constraint checking.</span></span>|  
|<span data-ttu-id="77c12-115">**隐式事务**</span><span class="sxs-lookup"><span data-stu-id="77c12-115">**implicit transactions**</span></span>|<span data-ttu-id="77c12-116">控制在运行一条语句时，是否隐式启动一项事务。</span><span class="sxs-lookup"><span data-stu-id="77c12-116">Controls whether a transaction is started implicitly when a statement is run.</span></span>|  
|<span data-ttu-id="77c12-117">**cursor close on commit**</span><span class="sxs-lookup"><span data-stu-id="77c12-117">**cursor close on commit**</span></span>|<span data-ttu-id="77c12-118">控制执行提交操作后游标的行为。</span><span class="sxs-lookup"><span data-stu-id="77c12-118">Controls behavior of cursors after a commit operation has been performed.</span></span>|  
|<span data-ttu-id="77c12-119">**ansi warnings**</span><span class="sxs-lookup"><span data-stu-id="77c12-119">**ansi warnings**</span></span>|<span data-ttu-id="77c12-120">控制聚合警告中的截断和 NULL。</span><span class="sxs-lookup"><span data-stu-id="77c12-120">Controls truncation and NULL in aggregate warnings.</span></span>|  
|<span data-ttu-id="77c12-121">**ansi padding**</span><span class="sxs-lookup"><span data-stu-id="77c12-121">**ansi padding**</span></span>|<span data-ttu-id="77c12-122">控制固定长度变量的填充。</span><span class="sxs-lookup"><span data-stu-id="77c12-122">Controls padding of fixed-length variables.</span></span>|  
|<span data-ttu-id="77c12-123">**ansi nulls**</span><span class="sxs-lookup"><span data-stu-id="77c12-123">**ansi nulls**</span></span>|<span data-ttu-id="77c12-124">在使用相等运算符时控制 `NULL` 的处理。</span><span class="sxs-lookup"><span data-stu-id="77c12-124">Controls `NULL` handling when using equality operators.</span></span>|  
|<span data-ttu-id="77c12-125">**arithmetic abort**</span><span class="sxs-lookup"><span data-stu-id="77c12-125">**arithmetic abort**</span></span>|<span data-ttu-id="77c12-126">在查询执行过程中发生溢出或被零除错误时终止查询。</span><span class="sxs-lookup"><span data-stu-id="77c12-126">Terminates a query when an overflow or divide-by-zero error occurs during query execution.</span></span>|  
|<span data-ttu-id="77c12-127">**arithmetic ignore**</span><span class="sxs-lookup"><span data-stu-id="77c12-127">**arithmetic ignore**</span></span>|<span data-ttu-id="77c12-128">在查询过程中出现溢出或被零除错误时返回 NULL。</span><span class="sxs-lookup"><span data-stu-id="77c12-128">Returns NULL when an overflow or divide-by-zero error occurs during a query.</span></span>|  
|<span data-ttu-id="77c12-129">**quoted identifier**</span><span class="sxs-lookup"><span data-stu-id="77c12-129">**quoted identifier**</span></span>|<span data-ttu-id="77c12-130">对表达式进行求值时区别单引号和双引号。</span><span class="sxs-lookup"><span data-stu-id="77c12-130">Differentiates between single and double quotation marks when evaluating an expression.</span></span>|  
|<span data-ttu-id="77c12-131">**no count**</span><span class="sxs-lookup"><span data-stu-id="77c12-131">**no count**</span></span>|<span data-ttu-id="77c12-132">关闭执行每个语句后返回的报告受影响的行数的消息。</span><span class="sxs-lookup"><span data-stu-id="77c12-132">Turns off the message returned at the end of each statement that states how many rows were affected.</span></span>|  
|<span data-ttu-id="77c12-133">**ansi null default on**</span><span class="sxs-lookup"><span data-stu-id="77c12-133">**ansi null default on**</span></span>|<span data-ttu-id="77c12-134">将会话的行为更改为使用 ANSI 兼容的空性。</span><span class="sxs-lookup"><span data-stu-id="77c12-134">Alters the session's behavior to use ANSI compatibility for nullability.</span></span> <span data-ttu-id="77c12-135">未显式定义为空性的新列允许使用空值。</span><span class="sxs-lookup"><span data-stu-id="77c12-135">New columns defined without explicit nullability are defined to allow nulls.</span></span>|  
|<span data-ttu-id="77c12-136">**ansi null default off**</span><span class="sxs-lookup"><span data-stu-id="77c12-136">**ansi null default off**</span></span>|<span data-ttu-id="77c12-137">将会话的行为更改为不使用 ANSI 兼容的空性。</span><span class="sxs-lookup"><span data-stu-id="77c12-137">Alters the session's behavior not to use ANSI compatibility for nullability.</span></span> <span data-ttu-id="77c12-138">未显式定义为空性的新列定义为不允许使用空值。</span><span class="sxs-lookup"><span data-stu-id="77c12-138">New columns defined without explicit nullability are defined not to allow nulls.</span></span>|  
|<span data-ttu-id="77c12-139">**concat null yields null**</span><span class="sxs-lookup"><span data-stu-id="77c12-139">**concat null yields null**</span></span>|<span data-ttu-id="77c12-140">将 NULL 值与字符串串联时返回 NULL。</span><span class="sxs-lookup"><span data-stu-id="77c12-140">Returns NULL when concatenating a NULL value with a string.</span></span>|  
|<span data-ttu-id="77c12-141">**numeric round abort**</span><span class="sxs-lookup"><span data-stu-id="77c12-141">**numeric round abort**</span></span>|<span data-ttu-id="77c12-142">表达式中出现精度降低时生成错误。</span><span class="sxs-lookup"><span data-stu-id="77c12-142">Generates an error when a loss of precision occurs in an expression.</span></span>|  
|<span data-ttu-id="77c12-143">**xact abort**</span><span class="sxs-lookup"><span data-stu-id="77c12-143">**xact abort**</span></span>|<span data-ttu-id="77c12-144">如果 Transact-SQL 语句引发运行时错误，则回滚事务。</span><span class="sxs-lookup"><span data-stu-id="77c12-144">Rolls back a transaction if a Transact-SQL statement raises a run-time error.</span></span>|  
  
 <span data-ttu-id="77c12-145">有关连接选项的详细信息，请搜索联机丛书中的特定选项内容。</span><span class="sxs-lookup"><span data-stu-id="77c12-145">For more information on connection options, search Books Online for the specific option.</span></span>  
  
## <a name="remote-server-connections"></a><span data-ttu-id="77c12-146">远程服务器连接</span><span class="sxs-lookup"><span data-stu-id="77c12-146">Remote Server Connections</span></span>  
 <span data-ttu-id="77c12-147">**允许远程连接到此服务器**</span><span class="sxs-lookup"><span data-stu-id="77c12-147">**Allow remote connections to this server**</span></span>  
 <span data-ttu-id="77c12-148">从运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例的远程服务器控制存储过程的执行。</span><span class="sxs-lookup"><span data-stu-id="77c12-148">Controls the execution of stored procedures from remote servers running instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="77c12-149">选中此复选框与将 **sp_configureremote access** 选项设置为 1 具有相同的作用。</span><span class="sxs-lookup"><span data-stu-id="77c12-149">Selecting this check box has the same effect as setting the **sp_configureremote access** option to 1.</span></span> <span data-ttu-id="77c12-150">清除此复选框可阻止从远程服务器执行存储过程。</span><span class="sxs-lookup"><span data-stu-id="77c12-150">Clearing it prevents execution of stored procedures from a remote server.</span></span>  
  
 <span data-ttu-id="77c12-151">**远程查询超时值(秒，0 = 无超时)**</span><span class="sxs-lookup"><span data-stu-id="77c12-151">**Remote query timeout (in seconds, 0 = no timeout)**</span></span>  
 <span data-ttu-id="77c12-152">指定在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 超时之前远程操作可以执行的时间（秒）。默认为 600 秒，或等待 10 分钟。</span><span class="sxs-lookup"><span data-stu-id="77c12-152">Specifies how long (in seconds) a remote operation may take before [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] times out. The default is 600 seconds, or a 10-minute wait.</span></span>  
  
 <span data-ttu-id="77c12-153">**需要将分布式事务用于服务器到服务器的通信**</span><span class="sxs-lookup"><span data-stu-id="77c12-153">**Require distributed transactions for server-to-server communication**</span></span>  
 <span data-ttu-id="77c12-154">通过 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 分布式事务处理协调器 (MS DTC) 事务保护服务器到服务器过程的操作。</span><span class="sxs-lookup"><span data-stu-id="77c12-154">Protects the actions of a server-to-server procedure through a [!INCLUDE[msCoName](../../includes/msconame-md.md)] Distributed Transaction Coordinator (MS DTC) transaction.</span></span> <span data-ttu-id="77c12-155">有关详细信息，请参阅 [配置远程过程事务服务器配置选项](configure-the-remote-proc-trans-server-configuration-option.md)。</span><span class="sxs-lookup"><span data-stu-id="77c12-155">For more information, see [Configure the remote proc trans Server Configuration Option](configure-the-remote-proc-trans-server-configuration-option.md).</span></span>  
  
## <a name="property-page-display-options"></a><span data-ttu-id="77c12-156">属性页显示选项</span><span class="sxs-lookup"><span data-stu-id="77c12-156">Property Page Display Options</span></span>  
 <span data-ttu-id="77c12-157">**配置值**</span><span class="sxs-lookup"><span data-stu-id="77c12-157">**Configured Values**</span></span>  
 <span data-ttu-id="77c12-158">显示此窗格上选项的配置值。</span><span class="sxs-lookup"><span data-stu-id="77c12-158">Displays the configured values for the options on this pane.</span></span> <span data-ttu-id="77c12-159">如果更改了这些值，请单击 **“运行值”** 以查看更改是否已生效。</span><span class="sxs-lookup"><span data-stu-id="77c12-159">If you change these values, click **Running Values** to see whether the changes have taken effect.</span></span> <span data-ttu-id="77c12-160">如果尚未生效，则必须首先重新启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的实例。</span><span class="sxs-lookup"><span data-stu-id="77c12-160">If they have not, the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] must be restarted first.</span></span>  
  
 <span data-ttu-id="77c12-161">**“运行值”**</span><span class="sxs-lookup"><span data-stu-id="77c12-161">**Running Values**</span></span>  
 <span data-ttu-id="77c12-162">查看此窗格上选项的当前运行值。</span><span class="sxs-lookup"><span data-stu-id="77c12-162">View the currently running values for the options on this pane.</span></span> <span data-ttu-id="77c12-163">这些值是只读的。</span><span class="sxs-lookup"><span data-stu-id="77c12-163">These values are read-only.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77c12-164">另请参阅</span><span class="sxs-lookup"><span data-stu-id="77c12-164">See Also</span></span>  
 <span data-ttu-id="77c12-165">[查询执行 &#40;选项： SQL Server： "高级" 页&#41;](../options-query-execution-sql-server-advanced-page.md) </span><span class="sxs-lookup"><span data-stu-id="77c12-165">[Options &#40;Query Execution:SQL Server:Advanced Page&#41;](../options-query-execution-sql-server-advanced-page.md) </span></span>  
 [<span data-ttu-id="77c12-166">服务器配置选项 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="77c12-166">Server Configuration Options &#40;SQL Server&#41;</span></span>](server-configuration-options-sql-server.md)  
  
  
