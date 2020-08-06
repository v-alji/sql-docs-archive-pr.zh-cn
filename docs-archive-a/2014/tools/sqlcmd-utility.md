---
title: sqlcmd 实用工具 | Microsoft Docs
ms.custom: ''
ms.date: 11/29/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- statements [SQL Server], command prompt
- QUIT command
- Transact-SQL statements, command prompt
- EXIT command
- sqlcmd commands
- ED command
- sqlcmd utility
- command prompt utilities [SQL Server], sqlcmd
- '!! command'
- stored procedures [SQL Server], command prompt
- system stored procedures [SQL Server], command prompt
- sqlcmd utility, about sqlcmd utility
- scripts [SQL Server], command prompt
- RESET command
- GO command
ms.assetid: e1728707-5215-4c04-8320-e36f161b834a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 9fbe5a3dcefb2218543e015dad71acfe79aea8e3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692618"
---
# <a name="sqlcmd-utility"></a><span data-ttu-id="fb31c-102">sqlcmd 实用工具</span><span class="sxs-lookup"><span data-stu-id="fb31c-102">sqlcmd Utility</span></span>
  <span data-ttu-id="fb31c-103">使用此 `sqlcmd` 实用工具，可以在 [!INCLUDE[tsql](../includes/tsql-md.md)] 命令提示符处、在 SQLCMD 模式下的**查询编辑器**中、在 Windows 脚本文件中或在运行代理作业 ( # A0) 作业步骤的命令提示符下输入语句、系统过程和脚本文件 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="fb31c-103">The `sqlcmd` utility lets you enter [!INCLUDE[tsql](../includes/tsql-md.md)] statements, system procedures, and script files at the command prompt, in **Query Editor** in SQLCMD mode, in a Windows script file or in an operating system (Cmd.exe) job step of a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent job.</span></span> <span data-ttu-id="fb31c-104">此实用工具使用 ODBC 执行 [!INCLUDE[tsql](../includes/tsql-md.md)] 批处理。</span><span class="sxs-lookup"><span data-stu-id="fb31c-104">This utility uses ODBC to execute [!INCLUDE[tsql](../includes/tsql-md.md)] batches.</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]<span data-ttu-id="fb31c-105">在查询编辑器中，使用 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] SqlClient 在常规模式和**Query Editor**SQLCMD 模式下执行。</span><span class="sxs-lookup"><span data-stu-id="fb31c-105">uses the [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]SqlClient for execution in regular and SQLCMD mode in **Query Editor**.</span></span> <span data-ttu-id="fb31c-106">从命令行运行 `sqlcmd` 时，`sqlcmd` 使用 ODBC 驱动程序。</span><span class="sxs-lookup"><span data-stu-id="fb31c-106">When `sqlcmd` is run from the command line, `sqlcmd` uses the ODBC driver.</span></span> <span data-ttu-id="fb31c-107">由于可以应用不同的默认选项，因此在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] SQLCMD 模式下以及在 `sqlcmd` 实用工具中执行相同的查询时，可能会看到不同的行为。</span><span class="sxs-lookup"><span data-stu-id="fb31c-107">Because different default options may apply, you might see different behavior when you execute the same query in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] in SQLCMD Mode and in the `sqlcmd` utility.</span></span>  
  
 <span data-ttu-id="fb31c-108">当前，`sqlcmd` 在命令行选项和值之间不需要空格。</span><span class="sxs-lookup"><span data-stu-id="fb31c-108">Currently, `sqlcmd` does not require a space between the command line option and the value.</span></span> <span data-ttu-id="fb31c-109">但是，在将来的版本中，在命令行选项和值之间可能需要空格。</span><span class="sxs-lookup"><span data-stu-id="fb31c-109">However, in a future release, a space may be required between the command line option and the value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb31c-110">语法</span><span class="sxs-lookup"><span data-stu-id="fb31c-110">Syntax</span></span>  
  
```  
  
   sqlcmd  
   -a  
   packet_size  
   -A (dedicated administrator connection)  
-b (terminate batch job if there is an error)  
-cbatch_terminator-C (trust the server certificate)  
-ddb_name-e (echo input)  
-E (use trusted connection)  
-fcodepage | i:codepage[,o:codepage] | o:codepage[,i:codepage]  
-hrows_per_header-Hworkstation_name-iinput_file-I (enable quoted identifiers)  
-k[1 | 2] (remove or replace control characters)  
-Kapplication_intent-llogin_timeout-L[c] (list servers, optional clean output)  
-merror_level-Mmultisubnet_failover-N (encrypt connection)  
-ooutput_file-p[1] (print statistics, optional colon format)  
-Ppassword-q "cmdline query"-Q "cmdline query" (and exit)  
-r[0 | 1] (msgs to stderr)  
-R (use client regional settings)  
-scol_separator-S [protocol:]server[\instance_name][,port]  
-tquery_timeout-u (unicode output file)  
-Ulogin_id-vvar = "value"-Verror_severity_level-wcolumn_width-W (remove trailing spaces)  
-x (disable variable substitution)  
-X[1] (disable commands, startup script, environment variables and optional exit)  
-yvariable_length_type_display_width-Yfixed_length_type_display_width-znew_password -Znew_password (and exit)  
  
-? (usage)  
```  
  
## <a name="command-line-options"></a><span data-ttu-id="fb31c-111">命令行选项</span><span class="sxs-lookup"><span data-stu-id="fb31c-111">Command-line Options</span></span>  
 <span data-ttu-id="fb31c-112">**登录相关选项**</span><span class="sxs-lookup"><span data-stu-id="fb31c-112">**Login-Related Options**</span></span>  
  <span data-ttu-id="fb31c-113">**-A**</span><span class="sxs-lookup"><span data-stu-id="fb31c-113">**-A**</span></span>  
 <span data-ttu-id="fb31c-114">使用专用管理员连接 (DAC) 登录到 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="fb31c-114">Logs in to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] with a Dedicated Administrator Connection (DAC).</span></span> <span data-ttu-id="fb31c-115">此类型连接用于排除服务器故障。</span><span class="sxs-lookup"><span data-stu-id="fb31c-115">This kind of connection is used to troubleshoot a server.</span></span> <span data-ttu-id="fb31c-116">这只适用于支持 DAC 的服务器。</span><span class="sxs-lookup"><span data-stu-id="fb31c-116">This will only work with server computers that support DAC.</span></span> <span data-ttu-id="fb31c-117">如果 DAC 不可用，`sqlcmd` 会生成错误消息，然后退出。</span><span class="sxs-lookup"><span data-stu-id="fb31c-117">If DAC is not available, `sqlcmd` generates an error message and then exits.</span></span> <span data-ttu-id="fb31c-118">有关 DAC 的详细信息，请参阅 [用于数据库管理员的诊断连接](../database-engine/configure-windows/diagnostic-connection-for-database-administrators.md)。</span><span class="sxs-lookup"><span data-stu-id="fb31c-118">For more information about DAC, see [Diagnostic Connection for Database Administrators](../database-engine/configure-windows/diagnostic-connection-for-database-administrators.md).</span></span>  
  
 <span data-ttu-id="fb31c-119">**-C**</span><span class="sxs-lookup"><span data-stu-id="fb31c-119">**-C**</span></span>  
 <span data-ttu-id="fb31c-120">该开关供客户端用于将其配置为隐式表示信任服务器证书且无需验证。</span><span class="sxs-lookup"><span data-stu-id="fb31c-120">This switch is used by the client to configure it to implicitly trust the server certificate without validation.</span></span> <span data-ttu-id="fb31c-121">此选项等同于 ADO.NET 选项 `TRUSTSERVERCERTIFICATE = true`。</span><span class="sxs-lookup"><span data-stu-id="fb31c-121">This option is equivalent to the ADO.NET option `TRUSTSERVERCERTIFICATE = true`.</span></span>  
  
 <span data-ttu-id="fb31c-122">-d db_name</span><span class="sxs-lookup"><span data-stu-id="fb31c-122">**-d** _db_name_</span></span>  
 <span data-ttu-id="fb31c-123">`USE`启动时发出*db_name*语句 `sqlcmd` 。</span><span class="sxs-lookup"><span data-stu-id="fb31c-123">Issues a `USE` *db_name* statement when you start `sqlcmd`.</span></span> <span data-ttu-id="fb31c-124">此选项设置 `sqlcmd` 脚本变量 SQLCMDDBNAME。</span><span class="sxs-lookup"><span data-stu-id="fb31c-124">This option sets the `sqlcmd` scripting variable SQLCMDDBNAME.</span></span> <span data-ttu-id="fb31c-125">它指定初始数据库。</span><span class="sxs-lookup"><span data-stu-id="fb31c-125">This specifies the initial database.</span></span> <span data-ttu-id="fb31c-126">默认为您的登录名的默认数据库属性。</span><span class="sxs-lookup"><span data-stu-id="fb31c-126">The default is your login's default-database property.</span></span> <span data-ttu-id="fb31c-127">如果数据库不存在，则生成错误消息且 `sqlcmd` 退出。</span><span class="sxs-lookup"><span data-stu-id="fb31c-127">If the database does not exist, an error message is generated and `sqlcmd` exits.</span></span>  
  
 <span data-ttu-id="fb31c-128">**-l** _login_timeout_</span><span class="sxs-lookup"><span data-stu-id="fb31c-128">**-l** _login_timeout_</span></span>  
 <span data-ttu-id="fb31c-129">指定在您尝试连接到服务器时 ODBC 驱动程序的 `sqlcmd` 登录超时时间（以秒计）。</span><span class="sxs-lookup"><span data-stu-id="fb31c-129">Specifies the number of seconds before a `sqlcmd` login to the ODBC driver times out when you try to connect to a server.</span></span> <span data-ttu-id="fb31c-130">此选项设置 `sqlcmd` 脚本变量 SQLCMDLOGINTIMEOUT。</span><span class="sxs-lookup"><span data-stu-id="fb31c-130">This option sets the `sqlcmd` scripting variable SQLCMDLOGINTIMEOUT.</span></span> <span data-ttu-id="fb31c-131">登录到 `sqlcmd` 的默认超时时间为 8 秒。</span><span class="sxs-lookup"><span data-stu-id="fb31c-131">The default time-out for login to `sqlcmd` is eight seconds.</span></span> <span data-ttu-id="fb31c-132">登录超时必须是介于 0 和 65534 之间的数字。</span><span class="sxs-lookup"><span data-stu-id="fb31c-132">The login time-out must be a number between 0 and 65534.</span></span> <span data-ttu-id="fb31c-133">如果提供的值不是数值或不在此范围内，则 `sqlcmd` 将生成错误消息。</span><span class="sxs-lookup"><span data-stu-id="fb31c-133">If the value supplied is not numeric or does not fall into that range, `sqlcmd` generates an error message.</span></span> <span data-ttu-id="fb31c-134">该值为 0 时，则允许无限制等待。</span><span class="sxs-lookup"><span data-stu-id="fb31c-134">A value of 0 specifies time-out to be infinite.</span></span>  
  
 <span data-ttu-id="fb31c-135">**-E**</span><span class="sxs-lookup"><span data-stu-id="fb31c-135">**-E**</span></span>  
 <span data-ttu-id="fb31c-136">使用信任连接而不是用户名和密码登录 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="fb31c-136">Uses a trusted connection instead of using a user name and password to log on to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="fb31c-137">默认情况下，如果未指定 -E，`sqlcmd` 将使用可信连接选项。</span><span class="sxs-lookup"><span data-stu-id="fb31c-137">By default, without -E specified, `sqlcmd` uses the trusted connection option.</span></span>  
  
 <span data-ttu-id="fb31c-138">**-E** 选项会忽略可能的用户名和密码环境变量设置，例如 SQLCMDPASSWORD。</span><span class="sxs-lookup"><span data-stu-id="fb31c-138">The **-E** option ignores possible user name and password environment variable settings such as SQLCMDPASSWORD.</span></span> <span data-ttu-id="fb31c-139">如果将 **-E** 选项与 **-U** 选项或 **-P** 选项一起使用，将生成错误消息。</span><span class="sxs-lookup"><span data-stu-id="fb31c-139">If the **-E** option is used together with the **-U** option or the **-P** option, an error message is generated.</span></span>  
  
 <span data-ttu-id="fb31c-140">-H workstation_name</span><span class="sxs-lookup"><span data-stu-id="fb31c-140">**-H** _workstation_name_</span></span>  
 <span data-ttu-id="fb31c-141">工作站的名称。</span><span class="sxs-lookup"><span data-stu-id="fb31c-141">A workstation name.</span></span> <span data-ttu-id="fb31c-142">此选项设置 `sqlcmd` 脚本变量 SQLCMDWORKSTATION。</span><span class="sxs-lookup"><span data-stu-id="fb31c-142">This option sets the `sqlcmd` scripting variable SQLCMDWORKSTATION.</span></span> <span data-ttu-id="fb31c-143">工作站名称列出在“sys.processes”\*\*\*\* 目录视图的“hostname”\*\*\*\* 列中，并且可使用存储过程“sp_who”\*\*\*\* 返回。</span><span class="sxs-lookup"><span data-stu-id="fb31c-143">The workstation name is listed in the **hostname** column of the **sys.processes** catalog view and can be returned using the stored procedure **sp_who**.</span></span> <span data-ttu-id="fb31c-144">如果不指定此选项，则默认为当前计算机名称。</span><span class="sxs-lookup"><span data-stu-id="fb31c-144">If this option is not specified, the default is the current computer name.</span></span> <span data-ttu-id="fb31c-145">此名称可用来标识不同的 `sqlcmd` 会话。</span><span class="sxs-lookup"><span data-stu-id="fb31c-145">This name can be used to identify different `sqlcmd` sessions.</span></span>  
  
 <span data-ttu-id="fb31c-146">-K application_intent</span><span class="sxs-lookup"><span data-stu-id="fb31c-146">**-K** _application_intent_</span></span>  
 <span data-ttu-id="fb31c-147">连接到服务器时声明应用程序工作负荷类型。</span><span class="sxs-lookup"><span data-stu-id="fb31c-147">Declares the application workload type when connecting to a server.</span></span> <span data-ttu-id="fb31c-148">目前唯一支持的值是 **ReadOnly**。</span><span class="sxs-lookup"><span data-stu-id="fb31c-148">The only currently supported value is **ReadOnly**.</span></span> <span data-ttu-id="fb31c-149">如果未指定 **-K**，sqlcmd 实用工具将不支持连接到 AlwaysOn 可用性组中的次要副本。</span><span class="sxs-lookup"><span data-stu-id="fb31c-149">If **-K** is not specified, the sqlcmd utility will not support connectivity to a secondary replica in an AlwaysOn availability group.</span></span> <span data-ttu-id="fb31c-150">有关详细信息，请参阅[活动辅助副本：可读辅助副本](../database-engine/availability-groups/windows/active-secondaries-readable-secondary-replicas-always-on-availability-groups.md)。</span><span class="sxs-lookup"><span data-stu-id="fb31c-150">For more information, see [Active Secondaries: Readable Secondary Replicas](../database-engine/availability-groups/windows/active-secondaries-readable-secondary-replicas-always-on-availability-groups.md).</span></span>  
  
 <span data-ttu-id="fb31c-151">`-M`*multisubnet_failover*</span><span class="sxs-lookup"><span data-stu-id="fb31c-151">`-M` *multisubnet_failover*</span></span>  
 <span data-ttu-id="fb31c-152">在连接到 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 可用性组侦听器或 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 故障转移群集实例的可用性组侦听器时，应始终指定 `-M`。</span><span class="sxs-lookup"><span data-stu-id="fb31c-152">Always specify `-M` when connecting to the availability group listener of a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] availability group or a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Failover Cluster Instance.</span></span> <span data-ttu-id="fb31c-153">`-M` 将为（当前）活动服务器提供更快的检测和连接。</span><span class="sxs-lookup"><span data-stu-id="fb31c-153">`-M` provides for faster detection of and connection to the (currently) active server.</span></span> <span data-ttu-id="fb31c-154">如果未指定 `-M`，则 `-M` 将关闭。</span><span class="sxs-lookup"><span data-stu-id="fb31c-154">If `-M` is not specified, `-M` is off.</span></span> <span data-ttu-id="fb31c-155">有关的详细信息 [!INCLUDE[ssHADR](../includes/sshadr-md.md)] ，请参阅[可用性组侦听器、客户端连接和应用程序故障转移 &#40;SQL Server&#41;](../database-engine/listeners-client-connectivity-application-failover.md)、[创建和配置可用性组 &#40;SQL Server ](../database-engine/availability-groups/windows/creation-and-configuration-of-availability-groups-sql-server.md)&#41;、[故障转移群集和 AlwaysOn 可用性组](../database-engine/availability-groups/windows/failover-clustering-and-always-on-availability-groups-sql-server.md)&#40;SQL Server&#41;和[活动辅助副本：可读辅助副本](../database-engine/availability-groups/windows/active-secondaries-readable-secondary-replicas-always-on-availability-groups.md)。</span><span class="sxs-lookup"><span data-stu-id="fb31c-155">For more information about [!INCLUDE[ssHADR](../includes/sshadr-md.md)], see [Availability Group Listeners, Client Connectivity, and Application Failover &#40;SQL Server&#41;](../database-engine/listeners-client-connectivity-application-failover.md), [Creation and Configuration of Availability Groups &#40;SQL Server&#41;](../database-engine/availability-groups/windows/creation-and-configuration-of-availability-groups-sql-server.md), [Failover Clustering and AlwaysOn Availability Groups &#40;SQL Server&#41;](../database-engine/availability-groups/windows/failover-clustering-and-always-on-availability-groups-sql-server.md), and [Active Secondaries: Readable Secondary Replicas](../database-engine/availability-groups/windows/active-secondaries-readable-secondary-replicas-always-on-availability-groups.md) .</span></span>  
  
 <span data-ttu-id="fb31c-156">**-N**</span><span class="sxs-lookup"><span data-stu-id="fb31c-156">**-N**</span></span>  
 <span data-ttu-id="fb31c-157">此开关供客户端用于请求加密连接。</span><span class="sxs-lookup"><span data-stu-id="fb31c-157">This switch is used by the client to request an encrypted connection.</span></span>  
  
 <span data-ttu-id="fb31c-158">-P password</span><span class="sxs-lookup"><span data-stu-id="fb31c-158">**-P** _password_</span></span>  
 <span data-ttu-id="fb31c-159">用户指定的密码。</span><span class="sxs-lookup"><span data-stu-id="fb31c-159">Is a user-specified password.</span></span> <span data-ttu-id="fb31c-160">密码是区分大小写的。</span><span class="sxs-lookup"><span data-stu-id="fb31c-160">Passwords are case sensitive.</span></span> <span data-ttu-id="fb31c-161">如果使用了-U 选项而未使用 **-P**选项，并且未设置 SQLCMDPASSWORD 环境变量，则 `sqlcmd` 会提示用户输入密码。</span><span class="sxs-lookup"><span data-stu-id="fb31c-161">If the -U option is used and the **-P** option is not used, and the SQLCMDPASSWORD environment variable has not been set, `sqlcmd` prompts the user for a password.</span></span> <span data-ttu-id="fb31c-162">如果在命令提示符的末尾使用 **-P**选项而没有密码，则 `sqlcmd` 使用默认密码 (NULL) 。</span><span class="sxs-lookup"><span data-stu-id="fb31c-162">If the **-P** option is used at the end of the command prompt without a password `sqlcmd` uses the default password (NULL).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="fb31c-163">不要使用空密码。</span><span class="sxs-lookup"><span data-stu-id="fb31c-163">Do not use a blank password.</span></span> <span data-ttu-id="fb31c-164">请使用强密码。</span><span class="sxs-lookup"><span data-stu-id="fb31c-164">Use a strong password.</span></span> <span data-ttu-id="fb31c-165">有关详细信息，请参阅 [Strong Passwords](../relational-databases/security/strong-passwords.md)。</span><span class="sxs-lookup"><span data-stu-id="fb31c-165">For more information, see [Strong Passwords](../relational-databases/security/strong-passwords.md).</span></span>  
  
 <span data-ttu-id="fb31c-166">通过向控制台输出密码提示，可以显示密码提示，如下所示： `Password:`</span><span class="sxs-lookup"><span data-stu-id="fb31c-166">The password prompt is displayed by printing the password prompt to the console, as follows: `Password:`</span></span>  
  
 <span data-ttu-id="fb31c-167">隐藏用户输入。</span><span class="sxs-lookup"><span data-stu-id="fb31c-167">User input is hidden.</span></span> <span data-ttu-id="fb31c-168">也就是说，将不会显示任何输入的内容，光标保留原位不动。</span><span class="sxs-lookup"><span data-stu-id="fb31c-168">This means that nothing is displayed and the cursor stays in position.</span></span>  
  
 <span data-ttu-id="fb31c-169">使用 SQLCMDPASSWORD 环境变量可以为当前会话设置默认密码。</span><span class="sxs-lookup"><span data-stu-id="fb31c-169">The SQLCMDPASSWORD environment variable lets you set a default password for the current session.</span></span> <span data-ttu-id="fb31c-170">因此，不必将密码硬编码到批处理文件中。</span><span class="sxs-lookup"><span data-stu-id="fb31c-170">Therefore, passwords do not have to be hard-coded into batch files.</span></span>  
  
 <span data-ttu-id="fb31c-171">以下示例首先在命令提示符处设置 SQLCMDPASSWORD 变量，然后访问 `sqlcmd` 实用工具。</span><span class="sxs-lookup"><span data-stu-id="fb31c-171">The following example first sets the SQLCMDPASSWORD variable at the command prompt and then accesses the `sqlcmd` utility.</span></span> <span data-ttu-id="fb31c-172">在命令提示符处，键入：</span><span class="sxs-lookup"><span data-stu-id="fb31c-172">At the command prompt, type:</span></span>  
  
 `SET SQLCMDPASSWORD= p@a$$w0rd`  
  
> [!IMPORTANT]  
>  <span data-ttu-id="fb31c-173">任何可以看到计算机监视器的人均可看到密码。</span><span class="sxs-lookup"><span data-stu-id="fb31c-173">The password will be visible to anyone who can see your computer monitor.</span></span>  
  
 <span data-ttu-id="fb31c-174">在以下命令提示符处键入：</span><span class="sxs-lookup"><span data-stu-id="fb31c-174">At the following command prompt, type:</span></span>  
  
 `sqlcmd`  
  
 <span data-ttu-id="fb31c-175">如果用户名和密码组合不正确，将生成错误消息。</span><span class="sxs-lookup"><span data-stu-id="fb31c-175">If the user name and password combination is incorrect, an error message is generated.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fb31c-176">为实现向后兼容性而保留了 OSQLPASSWORD 环境变量。</span><span class="sxs-lookup"><span data-stu-id="fb31c-176">The OSQLPASSWORD environment variable has been kept for backward compatibility.</span></span> <span data-ttu-id="fb31c-177">SQLCMDPASSWORD 环境变量优先于 OSQLPASSWORD 环境变量;这意味着 `sqlcmd` 和**osql**可以彼此相邻使用而不会受到干扰，旧脚本将继续工作。</span><span class="sxs-lookup"><span data-stu-id="fb31c-177">The SQLCMDPASSWORD environment variable takes precedence over the OSQLPASSWORD environment variable; this means that `sqlcmd` and **osql** can be used next to each other without interference and that old scripts will continue to work.</span></span>  
  
 <span data-ttu-id="fb31c-178">如果将 **-P** 选项与 **-E** 选项一起使用，将生成错误消息。</span><span class="sxs-lookup"><span data-stu-id="fb31c-178">If the **-P** option is used with the **-E** option, an error message is generated.</span></span>  
  
 <span data-ttu-id="fb31c-179">如果 **-P** 选项后有多个参数，将生成错误消息并退出程序。</span><span class="sxs-lookup"><span data-stu-id="fb31c-179">If the **-P** option is followed by more than one argument, an error message is generated and the program exits.</span></span>  
  
 <span data-ttu-id="fb31c-180">**-S** [*协议*：]*服务器*[ **\\** _instance_name_] [**，**_端口_]</span><span class="sxs-lookup"><span data-stu-id="fb31c-180">**-S** [*protocol*:]*server*[**\\**_instance_name_][**,**_port_]</span></span>  
 <span data-ttu-id="fb31c-181">指定要连接的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="fb31c-181">Specifies the instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to which to connect.</span></span> <span data-ttu-id="fb31c-182">它设置 `sqlcmd` 脚本变量 SQLCMDSERVER。</span><span class="sxs-lookup"><span data-stu-id="fb31c-182">It sets the `sqlcmd` scripting variable SQLCMDSERVER.</span></span>  
  
 <span data-ttu-id="fb31c-183">指定 *server_name* 可连接到该服务器计算机上的默认实例 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="fb31c-183">Specify *server_name* to connect to the default instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] on that server computer.</span></span> <span data-ttu-id="fb31c-184">指定*server_name* [ **\\** _instance_name_ ] 以连接到 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 该服务器计算机上的命名实例。</span><span class="sxs-lookup"><span data-stu-id="fb31c-184">Specify *server_name* [ **\\**_instance_name_ ] to connect to a named instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] on that server computer.</span></span> <span data-ttu-id="fb31c-185">如果不指定服务器，`sqlcmd` 将连接到本地计算机上 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的默认实例。</span><span class="sxs-lookup"><span data-stu-id="fb31c-185">If no server computer is specified, `sqlcmd` connects to the default instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] on the local computer.</span></span> <span data-ttu-id="fb31c-186">从网络上的远程计算机执行时，此选项是必需的 `sqlcmd` 。</span><span class="sxs-lookup"><span data-stu-id="fb31c-186">This option is required when you execute `sqlcmd` from a remote computer on the network.</span></span>  
  
 <span data-ttu-id="fb31c-187">*协议*可以 `tcp` (tcp/ip) 、 `lpc` (共享内存) 或 `np` (命名管道) 。</span><span class="sxs-lookup"><span data-stu-id="fb31c-187">*protocol* can be `tcp` (TCP/IP), `lpc` (shared memory), or `np` (named pipes).</span></span>  
  
 <span data-ttu-id="fb31c-188">如果在启动时未指定*server_name* [ **\\** _instance_name_ ] `sqlcmd` ，将 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 检查并使用 SQLCMDSERVER 环境变量。</span><span class="sxs-lookup"><span data-stu-id="fb31c-188">If you do not specify a *server_name* [ **\\**_instance_name_ ] when you start `sqlcmd`, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] checks for and uses the SQLCMDSERVER environment variable.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fb31c-189">为实现向后兼容性而保留了 OSQLSERVER 环境变量。</span><span class="sxs-lookup"><span data-stu-id="fb31c-189">The OSQLSERVER environment variable has been kept for backward compatibility.</span></span> <span data-ttu-id="fb31c-190">SQLCMDSERVER 环境变量优先于 OSQLSERVER 环境变量;这意味着 `sqlcmd` 和**osql**可以彼此相邻使用而不会受到干扰，旧脚本将继续工作。</span><span class="sxs-lookup"><span data-stu-id="fb31c-190">The SQLCMDSERVER environment variable takes precedence over the OSQLSERVER environment variable; this means that `sqlcmd` and **osql** can be used next to each other without interference and that old scripts will continue to work.</span></span>  
  
 <span data-ttu-id="fb31c-191">**-U** _login_id_</span><span class="sxs-lookup"><span data-stu-id="fb31c-191">**-U** _login_id_</span></span>  
 <span data-ttu-id="fb31c-192">用户登录 ID。</span><span class="sxs-lookup"><span data-stu-id="fb31c-192">Is the user login ID.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fb31c-193">OSQLUSER 环境变量可用于实现向后兼容性。</span><span class="sxs-lookup"><span data-stu-id="fb31c-193">The OSQLUSER environment variable is available for backward compatibility.</span></span> <span data-ttu-id="fb31c-194">SQLCMDUSER 环境变量优先于 OSQLUSER 环境变量。</span><span class="sxs-lookup"><span data-stu-id="fb31c-194">The SQLCMDUSER environment variable takes precedence over the OSQLUSER environment variable.</span></span> <span data-ttu-id="fb31c-195">这意味着 `sqlcmd` 和**osql**可以彼此相邻使用而不会受到干扰。</span><span class="sxs-lookup"><span data-stu-id="fb31c-195">This means that `sqlcmd` and **osql** can be used next to each other without interference.</span></span> <span data-ttu-id="fb31c-196">此外，现有的 **osql** 脚本可以继续使用。</span><span class="sxs-lookup"><span data-stu-id="fb31c-196">It also means that existing **osql** scripts will continue to work.</span></span>  
  
 <span data-ttu-id="fb31c-197">如果 **-U**选项和 **-P**选项均未指定，则将 `sqlcmd` 尝试使用 [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows 身份验证模式进行连接。</span><span class="sxs-lookup"><span data-stu-id="fb31c-197">If neither the **-U** option nor the **-P** option is specified, `sqlcmd` tries to connect by using [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows Authentication mode.</span></span> <span data-ttu-id="fb31c-198">身份验证基于运行 `sqlcmd` 的用户的 Windows 帐户。</span><span class="sxs-lookup"><span data-stu-id="fb31c-198">Authentication is based on the Windows account of the user who is running `sqlcmd`.</span></span>  
  
 <span data-ttu-id="fb31c-199">如果 **-U** 选项与 **-E** 选项（将在本主题的后面进行说明）一起使用，则会生成错误消息。</span><span class="sxs-lookup"><span data-stu-id="fb31c-199">If the **-U** option is used with the **-E** option (described later in this topic), an error message is generated.</span></span> <span data-ttu-id="fb31c-200">如果 -U 选项后跟多个参数，便会生成错误消息并退出程序。</span><span class="sxs-lookup"><span data-stu-id="fb31c-200">If the **-U** option is followed by more than one argument, an error message is generated and the program exits.</span></span>  
  
 <span data-ttu-id="fb31c-201">-z new_password</span><span class="sxs-lookup"><span data-stu-id="fb31c-201">**-z** _new_password_</span></span>  
 <span data-ttu-id="fb31c-202">更改密码：</span><span class="sxs-lookup"><span data-stu-id="fb31c-202">Change password:</span></span>  
  
 `sqlcmd -U someuser -P s0mep@ssword -z a_new_p@a$$w0rd`  
  
 <span data-ttu-id="fb31c-203">-Z new_password</span><span class="sxs-lookup"><span data-stu-id="fb31c-203">**-Z** _new_password_</span></span>  
 <span data-ttu-id="fb31c-204">更改密码并退出：</span><span class="sxs-lookup"><span data-stu-id="fb31c-204">Change password and exit:</span></span>  
  
 `sqlcmd -U someuser -P s0mep@ssword -Z a_new_p@a$$w0rd`  
  
 <span data-ttu-id="fb31c-205">**输入/输出选项**</span><span class="sxs-lookup"><span data-stu-id="fb31c-205">**Input/Output Options**</span></span>  
  <span data-ttu-id="fb31c-206">-f codepage | i:codepage[,o:codepage] | o:codepage[,i:codepage ]</span><span class="sxs-lookup"><span data-stu-id="fb31c-206">**-f** _codepage_ | **i:**_codepage_[**,o:**_codepage_] | **o:**_codepage_[**,i:**_codepage_]</span></span>  
 <span data-ttu-id="fb31c-207">指定输入和输出代码页。</span><span class="sxs-lookup"><span data-stu-id="fb31c-207">Specifies the input and output code pages.</span></span> <span data-ttu-id="fb31c-208">代码页页码是指定已安装的 Windows 代码页的数值。</span><span class="sxs-lookup"><span data-stu-id="fb31c-208">The codepage number is a numeric value that specifies an installed Windows code page.</span></span>  
  
 <span data-ttu-id="fb31c-209">代码页转换规则：</span><span class="sxs-lookup"><span data-stu-id="fb31c-209">Code-page conversion rules:</span></span>  
  
-   <span data-ttu-id="fb31c-210">如果未指定代码页，`sqlcmd` 会将当前代码页同时用于输入文件和输出文件，除非输入文件为 Unicode 文件，在此情况下无需进行转换。</span><span class="sxs-lookup"><span data-stu-id="fb31c-210">If no code pages are specified, `sqlcmd` will use the current code page for both input and output files, unless the input file is a Unicode file, in which case no conversion is required.</span></span>  
  
-   <span data-ttu-id="fb31c-211">`sqlcmd` 自动识别 Big-endian Unicode 和 Little-endian Unicode 输入文件。</span><span class="sxs-lookup"><span data-stu-id="fb31c-211">`sqlcmd` automatically recognizes both big-endian and little-endian Unicode input files.</span></span> <span data-ttu-id="fb31c-212">如果已指定 **-u** 选项，输出将始终为 Little-endian Unicode。</span><span class="sxs-lookup"><span data-stu-id="fb31c-212">If the **-u** option has been specified, the output will always be little-endian Unicode.</span></span>  
  
-   <span data-ttu-id="fb31c-213">如果未指定输出文件，输出代码页将为控制台代码页。</span><span class="sxs-lookup"><span data-stu-id="fb31c-213">If no output file is specified, the output code page will be the console code page.</span></span> <span data-ttu-id="fb31c-214">这将使输出正确显示在控制台上。</span><span class="sxs-lookup"><span data-stu-id="fb31c-214">This enables the output to be displayed correctly on the console.</span></span>  
  
-   <span data-ttu-id="fb31c-215">假定多个输入文件具有相同的代码页。</span><span class="sxs-lookup"><span data-stu-id="fb31c-215">Multiple input files are assumed to be of the same code page.</span></span> <span data-ttu-id="fb31c-216">可以将 Unicode 和非 Unicode 输入文件混合在一起。</span><span class="sxs-lookup"><span data-stu-id="fb31c-216">Unicode and non-Unicode input files can be mixed.</span></span>  
  
 <span data-ttu-id="fb31c-217">在命令提示符处输入 `chcp` 以验证 Cmd.exe 的代码页。</span><span class="sxs-lookup"><span data-stu-id="fb31c-217">Enter `chcp` at the command prompt to verify the code page of Cmd.exe.</span></span>  
  
 <span data-ttu-id="fb31c-218">**-i** _input_file_[**，**_input_file2_...]</span><span class="sxs-lookup"><span data-stu-id="fb31c-218">**-i** _input_file_[**,**_input_file2_...]</span></span>  
 <span data-ttu-id="fb31c-219">标识包含一批 SQL 语句或存储过程的文件。</span><span class="sxs-lookup"><span data-stu-id="fb31c-219">Identifies the file that contains a batch of SQL statements or stored procedures.</span></span> <span data-ttu-id="fb31c-220">可以指定要按顺序读取和处理的多个文件。</span><span class="sxs-lookup"><span data-stu-id="fb31c-220">Multiple files may be specified that will be read and processed in order.</span></span> <span data-ttu-id="fb31c-221">文件名之间不要使用任何空格。</span><span class="sxs-lookup"><span data-stu-id="fb31c-221">Do not use any spaces between file names.</span></span> <span data-ttu-id="fb31c-222">`sqlcmd` 将首先检查所有指定的文件是否都存在。</span><span class="sxs-lookup"><span data-stu-id="fb31c-222">`sqlcmd` will first check to see whether all the specified files exist.</span></span> <span data-ttu-id="fb31c-223">如果有一个或多个文件不存在，`sqlcmd` 将退出。</span><span class="sxs-lookup"><span data-stu-id="fb31c-223">If one or more files do not exist, `sqlcmd` will exit.</span></span> <span data-ttu-id="fb31c-224">-i 和 -Q/-q 选项是互斥的。</span><span class="sxs-lookup"><span data-stu-id="fb31c-224">The -i and the -Q/-q options are mutually exclusive.</span></span>  
  
 <span data-ttu-id="fb31c-225">路径示例：</span><span class="sxs-lookup"><span data-stu-id="fb31c-225">Path examples:</span></span>  
  
 <span data-ttu-id="fb31c-226">**-i**C： \\<文件名\></span><span class="sxs-lookup"><span data-stu-id="fb31c-226">**-i** C:\\<filename\></span></span>  
  
 <span data-ttu-id="fb31c-227">**-i** \\ \\<Server \> \\<Share $>\\<文件名\></span><span class="sxs-lookup"><span data-stu-id="fb31c-227">**-i** \\\\<Server\>\\<Share$>\\<filename\></span></span>  
  
 <span data-ttu-id="fb31c-228">**-i** "C:\Some Folder\\<file name\>"</span><span class="sxs-lookup"><span data-stu-id="fb31c-228">**-i** "C:\Some Folder\\<file name\>"</span></span>  
  
 <span data-ttu-id="fb31c-229">包含空格的文件路径必须用引号引起来。</span><span class="sxs-lookup"><span data-stu-id="fb31c-229">File paths that contain spaces must be enclosed in quotation marks.</span></span>  
  
 <span data-ttu-id="fb31c-230">此选项可能多次使用： **-i**_input_file_ **-** i_input_file。_</span><span class="sxs-lookup"><span data-stu-id="fb31c-230">This option may be used more than once: **-i**_input_file_ **-I**_I input_file._</span></span>  
  
 <span data-ttu-id="fb31c-231">-o output_file</span><span class="sxs-lookup"><span data-stu-id="fb31c-231">**-o** _output_file_</span></span>  
 <span data-ttu-id="fb31c-232">标识从 `sqlcmd` 接收输出的文件。</span><span class="sxs-lookup"><span data-stu-id="fb31c-232">Identifies the file that receives output from `sqlcmd`.</span></span>  
  
 <span data-ttu-id="fb31c-233">如果指定了 **-u** ，则 *output_file* 以 Unicode 格式存储。</span><span class="sxs-lookup"><span data-stu-id="fb31c-233">If **-u** is specified, the *output_file* is stored in Unicode format.</span></span> <span data-ttu-id="fb31c-234">如果文件名无效，将生成一个错误消息，并且 `sqlcmd` 将退出。</span><span class="sxs-lookup"><span data-stu-id="fb31c-234">If the file name is not valid, an error message is generated, and `sqlcmd` exits.</span></span> <span data-ttu-id="fb31c-235">`sqlcmd` 不支持向同一文件并发写入多个 `sqlcmd` 进程。</span><span class="sxs-lookup"><span data-stu-id="fb31c-235">`sqlcmd` does not support concurrent writing of multiple `sqlcmd` processes to the same file.</span></span> <span data-ttu-id="fb31c-236">文件输出将损坏或不正确。</span><span class="sxs-lookup"><span data-stu-id="fb31c-236">The file output will be corrupted or incorrect.</span></span> <span data-ttu-id="fb31c-237">有关文件格式的详细信息，请参阅 **-f** 开关。</span><span class="sxs-lookup"><span data-stu-id="fb31c-237">See the **-f** switch for more information about file formats.</span></span> <span data-ttu-id="fb31c-238">如果不存在，则将创建此文件。</span><span class="sxs-lookup"><span data-stu-id="fb31c-238">This file will be created if it does not exist.</span></span> <span data-ttu-id="fb31c-239">前一个 `sqlcmd` 会话中的同名文件将被覆盖。</span><span class="sxs-lookup"><span data-stu-id="fb31c-239">A file of the same name from a prior `sqlcmd` session will be overwritten.</span></span> <span data-ttu-id="fb31c-240">此处指定的文件不是 **stdout** 文件。</span><span class="sxs-lookup"><span data-stu-id="fb31c-240">The file specified here is not the **stdout** file.</span></span> <span data-ttu-id="fb31c-241">如果指定了**stdout**文件，则不会使用此文件。</span><span class="sxs-lookup"><span data-stu-id="fb31c-241">If a **stdout** file is specified this file will not be used.</span></span>  
  
 <span data-ttu-id="fb31c-242">路径示例：</span><span class="sxs-lookup"><span data-stu-id="fb31c-242">Path examples:</span></span>  
  
 <span data-ttu-id="fb31c-243">**-o**C： \\< 文件名></span><span class="sxs-lookup"><span data-stu-id="fb31c-243">**-o** C:\\< filename></span></span>  
  
 <span data-ttu-id="fb31c-244">**-o** \\ \\<Server \> \\<Share $>\\<文件名\></span><span class="sxs-lookup"><span data-stu-id="fb31c-244">**-o** \\\\<Server\>\\<Share$>\\<filename\></span></span>  
  
 <span data-ttu-id="fb31c-245">**-o "** C:\Some Folder\\<file name\>"</span><span class="sxs-lookup"><span data-stu-id="fb31c-245">**-o "** C:\Some Folder\\<file name\>"</span></span>  
  
 <span data-ttu-id="fb31c-246">包含空格的文件路径必须用引号引起来。</span><span class="sxs-lookup"><span data-stu-id="fb31c-246">File paths that contain spaces must be enclosed in quotation marks.</span></span>  
  
 <span data-ttu-id="fb31c-247">**-r**[**0** | **1**]</span><span class="sxs-lookup"><span data-stu-id="fb31c-247">**-r**[**0** | **1**]</span></span>  
 <span data-ttu-id="fb31c-248">将错误消息输出重定向到屏幕 (**stderr**)。</span><span class="sxs-lookup"><span data-stu-id="fb31c-248">Redirects the error message output to the screen (**stderr**).</span></span> <span data-ttu-id="fb31c-249">如果未指定参数或指定参数为 **0**，则仅重定向严重级别为 11 或更高的错误消息。</span><span class="sxs-lookup"><span data-stu-id="fb31c-249">If you do not specify a parameter or if you specify **0**, only error messages that have a severity level of 11 or higher are redirected.</span></span> <span data-ttu-id="fb31c-250">如果指定参数为 **1**，则将重定向所有消息输出（包括 PRINT）。</span><span class="sxs-lookup"><span data-stu-id="fb31c-250">If you specify **1**, all error message output including PRINT is redirected.</span></span> <span data-ttu-id="fb31c-251">如果使用 -o，将不起任何作用。</span><span class="sxs-lookup"><span data-stu-id="fb31c-251">Has no effect if you use -o.</span></span> <span data-ttu-id="fb31c-252">默认情况下，消息将发送到 **stdout**。</span><span class="sxs-lookup"><span data-stu-id="fb31c-252">By default, messages are sent to **stdout**.</span></span>  
  
 <span data-ttu-id="fb31c-253">**-R**</span><span class="sxs-lookup"><span data-stu-id="fb31c-253">**-R**</span></span>  
 <span data-ttu-id="fb31c-254">导致 `sqlcmd` [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 根据客户端的区域设置本地化从中检索到的数字、货币、日期和时间列。</span><span class="sxs-lookup"><span data-stu-id="fb31c-254">Causes `sqlcmd` to localize numeric, currency, date, and time columns retrieved from [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] based on the client's locale.</span></span> <span data-ttu-id="fb31c-255">默认情况下，这些列使用服务器的区域设置进行显示。</span><span class="sxs-lookup"><span data-stu-id="fb31c-255">By default, these columns are displayed using the server's regional settings.</span></span>  
  
 <span data-ttu-id="fb31c-256">**-u**</span><span class="sxs-lookup"><span data-stu-id="fb31c-256">**-u**</span></span>  
 <span data-ttu-id="fb31c-257">指定无论 *input_file* 为何种格式，都以 Unicode 格式存储 *output_file*。</span><span class="sxs-lookup"><span data-stu-id="fb31c-257">Specifies that *output_file* is stored in Unicode format, regardless of the format of *input_file*.</span></span>  
  
 <span data-ttu-id="fb31c-258">**查询执行选项**</span><span class="sxs-lookup"><span data-stu-id="fb31c-258">**Query Execution Options**</span></span>  
  <span data-ttu-id="fb31c-259">**-e**</span><span class="sxs-lookup"><span data-stu-id="fb31c-259">**-e**</span></span>  
 <span data-ttu-id="fb31c-260">将输入脚本写入标准输出设备 (**stdout**)。</span><span class="sxs-lookup"><span data-stu-id="fb31c-260">Writes input scripts to the standard output device (**stdout**).</span></span>  
  
 <span data-ttu-id="fb31c-261">**-I**</span><span class="sxs-lookup"><span data-stu-id="fb31c-261">**-I**</span></span>  
 <span data-ttu-id="fb31c-262">将 SET QUOTED_IDENTIFIER 连接选项设置为 ON。</span><span class="sxs-lookup"><span data-stu-id="fb31c-262">Sets the SET QUOTED_IDENTIFIER connection option to ON.</span></span> <span data-ttu-id="fb31c-263">默认情况下，此选项设置为 OFF。</span><span class="sxs-lookup"><span data-stu-id="fb31c-263">By default, it is set to OFF.</span></span> <span data-ttu-id="fb31c-264">有关详细信息，请参阅 [SET QUOTED_IDENTIFIER (Transact-SQL)](/sql/t-sql/statements/set-quoted-identifier-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="fb31c-264">For more information, see [SET QUOTED_IDENTIFIER &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-quoted-identifier-transact-sql).</span></span>  
  
 <span data-ttu-id="fb31c-265">**-q"** _cmdline query_ **"**</span><span class="sxs-lookup"><span data-stu-id="fb31c-265">**-q"** _cmdline query_ **"**</span></span>  
 <span data-ttu-id="fb31c-266">启动 `sqlcmd` 时执行查询，但是在查询结束运行时不退出 `sqlcmd`。</span><span class="sxs-lookup"><span data-stu-id="fb31c-266">Executes a query when `sqlcmd` starts, but does not exit `sqlcmd` when the query has finished running.</span></span> <span data-ttu-id="fb31c-267">可以执行多个以分号分隔的查询。</span><span class="sxs-lookup"><span data-stu-id="fb31c-267">Multiple-semicolon-delimited queries can be executed.</span></span> <span data-ttu-id="fb31c-268">将查询用引号引起来，如下例所示。</span><span class="sxs-lookup"><span data-stu-id="fb31c-268">Use quotation marks around the query, as shown in the following example.</span></span>  
  
 <span data-ttu-id="fb31c-269">在命令提示符处，键入：</span><span class="sxs-lookup"><span data-stu-id="fb31c-269">At the command prompt, type:</span></span>  
  
 `sqlcmd -d AdventureWorks2012 -q "SELECT FirstName, LastName FROM Person.Person WHERE LastName LIKE 'Whi%';"`  
  
 `sqlcmd -d AdventureWorks2012 -q "SELECT TOP 5 FirstName FROM Person.Person;SELECT TOP 5 LastName FROM Person.Person;"`  
  
> [!IMPORTANT]  
>  <span data-ttu-id="fb31c-270">请不要在查询中使用 GO 终止符。</span><span class="sxs-lookup"><span data-stu-id="fb31c-270">Do not use the GO terminator in the query.</span></span>  
  
 <span data-ttu-id="fb31c-271">如果在指定此选项的同时还指定了 `-b`，`sqlcmd` 在遇到错误时将退出。</span><span class="sxs-lookup"><span data-stu-id="fb31c-271">If `-b` is specified together with this option, `sqlcmd` exits on error.</span></span> <span data-ttu-id="fb31c-272">本主题的后面将介绍 `-b`。</span><span class="sxs-lookup"><span data-stu-id="fb31c-272">`-b` is described later in this topic.</span></span>  
  
 <span data-ttu-id="fb31c-273">**-Q "** _cmdline 查询_ **"**</span><span class="sxs-lookup"><span data-stu-id="fb31c-273">**-Q"** _cmdline query_ **"**</span></span>  
 <span data-ttu-id="fb31c-274">在 `sqlcmd` 启动时执行查询，随后立即退出 `sqlcmd`。</span><span class="sxs-lookup"><span data-stu-id="fb31c-274">Executes a query when `sqlcmd` starts and then immediately exits `sqlcmd`.</span></span> <span data-ttu-id="fb31c-275">可以执行多个以分号分隔的查询。</span><span class="sxs-lookup"><span data-stu-id="fb31c-275">Multiple-semicolon-delimited queries can be executed.</span></span>  
  
 <span data-ttu-id="fb31c-276">将查询用引号引起来，如下例所示。</span><span class="sxs-lookup"><span data-stu-id="fb31c-276">Use quotation marks around the query, as shown in the following example.</span></span>  
  
 <span data-ttu-id="fb31c-277">在命令提示符处，键入：</span><span class="sxs-lookup"><span data-stu-id="fb31c-277">At the command prompt, type:</span></span>  
  
 `sqlcmd -d AdventureWorks2012 -Q "SELECT FirstName, LastName FROM Person.Person WHERE LastName LIKE 'Whi%';"`  
  
 `sqlcmd -d AdventureWorks2012 -Q "SELECT TOP 5 FirstName FROM Person.Person;SELECT TOP 5 LastName FROM Person.Person;"`  
  
> [!IMPORTANT]  
>  <span data-ttu-id="fb31c-278">请不要在查询中使用 GO 终止符。</span><span class="sxs-lookup"><span data-stu-id="fb31c-278">Do not use the GO terminator in the query.</span></span>  
  
 <span data-ttu-id="fb31c-279">如果在指定此选项的同时还指定了 `-b`，`sqlcmd` 在遇到错误时将退出。</span><span class="sxs-lookup"><span data-stu-id="fb31c-279">If `-b` is specified together with this option, `sqlcmd` exits on error.</span></span> <span data-ttu-id="fb31c-280">本主题的后面将介绍 `-b`。</span><span class="sxs-lookup"><span data-stu-id="fb31c-280">`-b` is described later in this topic.</span></span>  
  
 <span data-ttu-id="fb31c-281">-t query_timeout</span><span class="sxs-lookup"><span data-stu-id="fb31c-281">**-t** _query_timeout_</span></span>  
 <span data-ttu-id="fb31c-282">指定命令 (或 SQL 语句) 超时前等待的秒数。此选项设置 `sqlcmd` 脚本变量 SQLCMDSTATTIMEOUT。</span><span class="sxs-lookup"><span data-stu-id="fb31c-282">Specifies the number of seconds before a command (or SQL statement) times out. This option sets the `sqlcmd` scripting variable SQLCMDSTATTIMEOUT.</span></span> <span data-ttu-id="fb31c-283">如果未指定 *time_out* 值，则命令将不会超时。querytime_out 必须是介于 1 和 65534 之间的数字。</span><span class="sxs-lookup"><span data-stu-id="fb31c-283">If a *time_out* value is not specified, the command does not time out. The *query\*\*time_out* must be a number between 1 and 65534.</span></span> <span data-ttu-id="fb31c-284">如果提供的值不是数值或不在此范围内，则 `sqlcmd` 将生成错误消息。</span><span class="sxs-lookup"><span data-stu-id="fb31c-284">If the value supplied is not numeric or does not fall into that range, `sqlcmd` generates an error message.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fb31c-285">实际的超时值可能会与指定的 time_out  值相差几秒。</span><span class="sxs-lookup"><span data-stu-id="fb31c-285">The actual time out value may vary from the specified *time_out* value by several seconds.</span></span>  
  
 <span data-ttu-id="fb31c-286">**-vvar =** _value_[ **var =** _value_...]</span><span class="sxs-lookup"><span data-stu-id="fb31c-286">**-vvar =** _value_[ **var =** _value_...]</span></span>  
 <span data-ttu-id="fb31c-287">创建 `sqlcmd` 可在脚本中使用的脚本变量 `sqlcmd` 。</span><span class="sxs-lookup"><span data-stu-id="fb31c-287">Creates a `sqlcmd`scripting variable that can be used in a `sqlcmd` script.</span></span> <span data-ttu-id="fb31c-288">如果该值包含空格，则将其用引号引起来。</span><span class="sxs-lookup"><span data-stu-id="fb31c-288">Enclose the value in quotation marks if the value contains spaces.</span></span> <span data-ttu-id="fb31c-289">可以指定多个**_var_** = **" *`values`* "** 值。</span><span class="sxs-lookup"><span data-stu-id="fb31c-289">You can specify multiple **_var_**=**"*`values`*"** values.</span></span> <span data-ttu-id="fb31c-290">如果指定的任何值中有错误，`sqlcmd` 会生成错误消息，然后退出。</span><span class="sxs-lookup"><span data-stu-id="fb31c-290">If there are errors in any of the values specified, `sqlcmd` generates an error message and then exits.</span></span>  
  
 `sqlcmd -v MyVar1=something MyVar2="some thing"`  
  
 `sqlcmd -v MyVar1=something -v MyVar2="some thing"`  
  
 <span data-ttu-id="fb31c-291">**-x**</span><span class="sxs-lookup"><span data-stu-id="fb31c-291">**-x**</span></span>  
 <span data-ttu-id="fb31c-292">导致 `sqlcmd` 忽略脚本变量。</span><span class="sxs-lookup"><span data-stu-id="fb31c-292">Causes `sqlcmd` to ignore scripting variables.</span></span> <span data-ttu-id="fb31c-293">当脚本中包含多个 INSERT 语句，并且这些语句可能包含格式与常规变量（例如 $(*variable_name*)）相同的字符串时，这一选项很有用。</span><span class="sxs-lookup"><span data-stu-id="fb31c-293">This is useful when a script contains many INSERT statements that may contain strings that have the same format as regular variables, such as $(*variable_name*).</span></span>  
  
 <span data-ttu-id="fb31c-294">**格式设置选项**</span><span class="sxs-lookup"><span data-stu-id="fb31c-294">**Formatting Options**</span></span>  
  <span data-ttu-id="fb31c-295">-h headers</span><span class="sxs-lookup"><span data-stu-id="fb31c-295">**-h** _headers_</span></span>  
 <span data-ttu-id="fb31c-296">指定要在列标题之间输出的行数。</span><span class="sxs-lookup"><span data-stu-id="fb31c-296">Specifies the number of rows to print between the column headings.</span></span> <span data-ttu-id="fb31c-297">默认为每一组查询结果输出一次标题。</span><span class="sxs-lookup"><span data-stu-id="fb31c-297">The default is to print headings one time for each set of query results.</span></span> <span data-ttu-id="fb31c-298">此选项设置 `sqlcmd` 脚本变量 SQLCMDHEADERS。</span><span class="sxs-lookup"><span data-stu-id="fb31c-298">This option sets the `sqlcmd` scripting variable SQLCMDHEADERS.</span></span> <span data-ttu-id="fb31c-299">使用 **-1** 指定不可输出标题。</span><span class="sxs-lookup"><span data-stu-id="fb31c-299">Use **-1** to specify that headers must not be printed.</span></span> <span data-ttu-id="fb31c-300">任何无效的值都将导致 `sqlcmd` 生成错误消息并随后退出。</span><span class="sxs-lookup"><span data-stu-id="fb31c-300">Any value that is not valid causes `sqlcmd` to generate an error message and then exit.</span></span>  
  
 <span data-ttu-id="fb31c-301">**-k** [**1** | **2**]</span><span class="sxs-lookup"><span data-stu-id="fb31c-301">**-k** [**1** | **2**]</span></span>  
 <span data-ttu-id="fb31c-302">删除输出中的所有控制字符，例如制表符和换行符。</span><span class="sxs-lookup"><span data-stu-id="fb31c-302">Removes all control characters, such as tabs and new line characters from the output.</span></span> <span data-ttu-id="fb31c-303">这会在返回数据时保留列格式。</span><span class="sxs-lookup"><span data-stu-id="fb31c-303">This preserves column formatting when data is returned.</span></span> <span data-ttu-id="fb31c-304">如果指定了 1，则控制字符被一个空格替代。</span><span class="sxs-lookup"><span data-stu-id="fb31c-304">If 1 is specified, the control characters are replaced by a single space.</span></span> <span data-ttu-id="fb31c-305">如果指定了 2，则连续的控制字符被一个空格替代。</span><span class="sxs-lookup"><span data-stu-id="fb31c-305">If 2 is specified, consecutive control characters are replaced by a single space.</span></span> <span data-ttu-id="fb31c-306">**-k** 与 **-k1**相同。</span><span class="sxs-lookup"><span data-stu-id="fb31c-306">**-k** is the same as **-k1**.</span></span>  
  
 <span data-ttu-id="fb31c-307">-s col_separator</span><span class="sxs-lookup"><span data-stu-id="fb31c-307">**-s** _col_separator_</span></span>  
 <span data-ttu-id="fb31c-308">指定列分隔符字符。</span><span class="sxs-lookup"><span data-stu-id="fb31c-308">Specifies the column-separator character.</span></span> <span data-ttu-id="fb31c-309">默认为空格。</span><span class="sxs-lookup"><span data-stu-id="fb31c-309">The default is a blank space.</span></span> <span data-ttu-id="fb31c-310">此选项设置 `sqlcmd` 脚本变量 SQLCMDCOLSEP。</span><span class="sxs-lookup"><span data-stu-id="fb31c-310">This option sets the `sqlcmd` scripting variable SQLCMDCOLSEP.</span></span> <span data-ttu-id="fb31c-311">若要使用对操作系统有特殊含义的字符，如“与”符号 (&) 或分号 (;)，请将该字符用双引号 (") 引起来。</span><span class="sxs-lookup"><span data-stu-id="fb31c-311">To use characters that have special meaning to the operating system such as the ampersand (&), or semicolon (;), enclose the character in quotation marks (").</span></span> <span data-ttu-id="fb31c-312">列分隔符可以是任意 8 位字符。</span><span class="sxs-lookup"><span data-stu-id="fb31c-312">The column separator can be any 8-bit character.</span></span>  
  
 <span data-ttu-id="fb31c-313">-w column_width</span><span class="sxs-lookup"><span data-stu-id="fb31c-313">**-w** _column_width_</span></span>  
 <span data-ttu-id="fb31c-314">指定用于输出的屏幕宽度。</span><span class="sxs-lookup"><span data-stu-id="fb31c-314">Specifies the screen width for output.</span></span> <span data-ttu-id="fb31c-315">此选项设置 `sqlcmd` 脚本变量 SQLCMDCOLWIDTH。</span><span class="sxs-lookup"><span data-stu-id="fb31c-315">This option sets the `sqlcmd` scripting variable SQLCMDCOLWIDTH.</span></span> <span data-ttu-id="fb31c-316">该列宽必须是介于 8 和 65536 之间的数字。</span><span class="sxs-lookup"><span data-stu-id="fb31c-316">The column width must be a number greater than 8 and less than 65536.</span></span> <span data-ttu-id="fb31c-317">如果指定的列宽不在此范围内，则 `sqlcmd` 将生成错误消息。</span><span class="sxs-lookup"><span data-stu-id="fb31c-317">If the specified column width does not fall into that range, `sqlcmd` generates and error message.</span></span> <span data-ttu-id="fb31c-318">默认宽度为 80 个字符。</span><span class="sxs-lookup"><span data-stu-id="fb31c-318">The default width is 80 characters.</span></span> <span data-ttu-id="fb31c-319">在输出行超出指定的列宽时，将转到下一行。</span><span class="sxs-lookup"><span data-stu-id="fb31c-319">When an output line exceeds the specified column width, it wraps on to the next line.</span></span>  
  
 <span data-ttu-id="fb31c-320">**-W**</span><span class="sxs-lookup"><span data-stu-id="fb31c-320">**-W**</span></span>  
 <span data-ttu-id="fb31c-321">此选项删除列的尾随空格。</span><span class="sxs-lookup"><span data-stu-id="fb31c-321">This option removes trailing spaces from a column.</span></span> <span data-ttu-id="fb31c-322">在准备要导出到另一应用程序的数据时，请将此选项和 **-s** 选项一起使用。</span><span class="sxs-lookup"><span data-stu-id="fb31c-322">Use this option together with the **-s** option when preparing data that is to be exported to another application.</span></span> <span data-ttu-id="fb31c-323">不能与 **-y** 或 **-Y** 选项一起使用。</span><span class="sxs-lookup"><span data-stu-id="fb31c-323">Cannot be used with the **-y** or **-Y** options.</span></span>  
  
 <span data-ttu-id="fb31c-324">-y variable_length_type_display_width</span><span class="sxs-lookup"><span data-stu-id="fb31c-324">**-y** _variable_length_type_display_width_</span></span>  
 <span data-ttu-id="fb31c-325">设置 `sqlcmd` 脚本变量 SQLCMDMAXVARTYPEWIDTH。</span><span class="sxs-lookup"><span data-stu-id="fb31c-325">Sets the `sqlcmd` scripting variable SQLCMDMAXVARTYPEWIDTH.</span></span> <span data-ttu-id="fb31c-326">默认值为 256。</span><span class="sxs-lookup"><span data-stu-id="fb31c-326">The default is 256.</span></span> <span data-ttu-id="fb31c-327">它限制为下列大型可变长度数据类型返回的字符的数目：</span><span class="sxs-lookup"><span data-stu-id="fb31c-327">It limits the number of characters that are returned for the large variable length data types:</span></span>  
  
-   `varchar(max)`  
  
-   `nvarchar(max)`  
  
-   `varbinary(max)`  
  
-   `xml`  
  
-   `UDT (user-defined data types)`  
  
-   `text`  
  
-   `ntext`  
  
-   `image`  
  
> [!NOTE]  
>  <span data-ttu-id="fb31c-328">根据实现，UDT 可以使用固定的长度。</span><span class="sxs-lookup"><span data-stu-id="fb31c-328">UDTs can be of fixed length depending on the implementation.</span></span> <span data-ttu-id="fb31c-329">如果此固定长度 UDT 的长度比 *display_width*短，则返回的 UDT 值将不受影响。</span><span class="sxs-lookup"><span data-stu-id="fb31c-329">If this length of a fixed length UDT is shorter that *display_width*, the value of the UDT returned is not affected.</span></span> <span data-ttu-id="fb31c-330">但是，如果此长度比 *display_width*长，则输出会被截断。</span><span class="sxs-lookup"><span data-stu-id="fb31c-330">However, if the length is longer than *display_width*, the output is truncated.</span></span>  
  
 
> [!IMPORTANT]  
>  <span data-ttu-id="fb31c-331">使用 **-y 0** 选项时要特别注意，因为根据返回的数据量大小，此选项可能导致服务器和网络上出现严重性能问题。</span><span class="sxs-lookup"><span data-stu-id="fb31c-331">Use the **-y 0** option with extreme caution because it may cause serious performance issues on both the server and the network, depending on the size of data returned.</span></span>  
  
 <span data-ttu-id="fb31c-332">-Y fixed_length_type_display_width</span><span class="sxs-lookup"><span data-stu-id="fb31c-332">**-Y** _fixed_length_type_display_width_</span></span>  
 <span data-ttu-id="fb31c-333">设置 `sqlcmd` 脚本变量 SQLCMDMAXFIXEDTYPEWIDTH。</span><span class="sxs-lookup"><span data-stu-id="fb31c-333">Sets the `sqlcmd` scripting variable SQLCMDMAXFIXEDTYPEWIDTH.</span></span> <span data-ttu-id="fb31c-334">默认值为 0（无限制）。</span><span class="sxs-lookup"><span data-stu-id="fb31c-334">The default is 0 (unlimited).</span></span> <span data-ttu-id="fb31c-335">它限制为以下数据类型返回的字符数：</span><span class="sxs-lookup"><span data-stu-id="fb31c-335">Limits the number of characters that are returned for the following data types:</span></span>  
  
-   <span data-ttu-id="fb31c-336">`char(`*n* `)` ，其中 1<= n<= 8000</span><span class="sxs-lookup"><span data-stu-id="fb31c-336">`char(` *n* `)`, where 1<=n<=8000</span></span>  
  
-   <span data-ttu-id="fb31c-337">`nchar(n`*n* `)` ，其中 1<= n<= 4000</span><span class="sxs-lookup"><span data-stu-id="fb31c-337">`nchar(n` *n* `)`, where 1<=n<=4000</span></span>  
  
-   <span data-ttu-id="fb31c-338">`varchar(n`*n* `)` ，其中 1<= n<= 8000</span><span class="sxs-lookup"><span data-stu-id="fb31c-338">`varchar(n` *n* `)`, where 1<=n<=8000</span></span>  
  
-   <span data-ttu-id="fb31c-339">`nvarchar(n`*n* `)` ，其中 1<= n<= 4000</span><span class="sxs-lookup"><span data-stu-id="fb31c-339">`nvarchar(n` *n* `)`, where 1<=n<=4000</span></span>  
  
-   <span data-ttu-id="fb31c-340">`varbinary(n`*n* `)` ，其中 1<= n<= 4000</span><span class="sxs-lookup"><span data-stu-id="fb31c-340">`varbinary(n` *n* `)`, where 1<=n<=4000</span></span>  
  
-   `variant`  
  
 <span data-ttu-id="fb31c-341">**错误报告选项**</span><span class="sxs-lookup"><span data-stu-id="fb31c-341">**Error Reporting Options**</span></span>  
  `-b`  
 <span data-ttu-id="fb31c-342">指定发生错误时，`sqlcmd` 退出并返回一个 DOS ERRORLEVEL 值。</span><span class="sxs-lookup"><span data-stu-id="fb31c-342">Specifies that `sqlcmd` exits and returns a DOS ERRORLEVEL value when an error occurs.</span></span> <span data-ttu-id="fb31c-343">当 **错误消息的严重级别高于 10 时，返回给 DOS ERRORLEVEL 变量的值为** 1 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ；否则返回的值为 **0**。</span><span class="sxs-lookup"><span data-stu-id="fb31c-343">The value that is returned to the DOS ERRORLEVEL variable is **1** when the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] error message has a severity level greater than 10; otherwise, the value returned is **0**.</span></span> <span data-ttu-id="fb31c-344">如果除 `-V` 选项外还设置了 `-b` 选项，则当严重级别低于使用 `-V` 设置的值时，`sqlcmd` 将不报告错误。</span><span class="sxs-lookup"><span data-stu-id="fb31c-344">If the `-V` option has been set in addition to `-b`, `sqlcmd` will not report an error if the severity level is lower than the values set using `-V`.</span></span> <span data-ttu-id="fb31c-345">命令提示符批处理文件可以测试 ERRORLEVEL 的值并相应处理错误。</span><span class="sxs-lookup"><span data-stu-id="fb31c-345">Command prompt batch files can test the value of ERRORLEVEL and handle the error appropriately.</span></span> <span data-ttu-id="fb31c-346">`sqlcmd` 不对严重级别 10 报告错误（信息性消息）。</span><span class="sxs-lookup"><span data-stu-id="fb31c-346">`sqlcmd` does not report errors for severity level 10 (informational messages).</span></span>  
  
 <span data-ttu-id="fb31c-347">如果 `sqlcmd` 脚本包含错误的注释、语法错误或缺少脚本变量，则返回的 ERRORLEVEL 为 1。</span><span class="sxs-lookup"><span data-stu-id="fb31c-347">If the `sqlcmd` script contains an incorrect comment, syntax error, or is missing a scripting variable, ERRORLEVEL returned is 1.</span></span>  
  
 <span data-ttu-id="fb31c-348">-m error_level</span><span class="sxs-lookup"><span data-stu-id="fb31c-348">**-m** _error_level_</span></span>  
 <span data-ttu-id="fb31c-349">控制发送到 **stdout**的错误消息类型。</span><span class="sxs-lookup"><span data-stu-id="fb31c-349">Controls which error messages are sent to **stdout**.</span></span> <span data-ttu-id="fb31c-350">将发送严重级别大于或等于此级别的消息。</span><span class="sxs-lookup"><span data-stu-id="fb31c-350">Messages that have a severity level greater than or equal to this level are sent.</span></span> <span data-ttu-id="fb31c-351">如果此值设置为 **-1**，将发送所有消息（包括信息性消息）。</span><span class="sxs-lookup"><span data-stu-id="fb31c-351">When this value is set to **-1**, all messages including informational messages, are sent.</span></span> <span data-ttu-id="fb31c-352">**-m** 和 **-1**之间不允许有空格。</span><span class="sxs-lookup"><span data-stu-id="fb31c-352">Spaces are not allowed between the **-m** and **-1**.</span></span> <span data-ttu-id="fb31c-353">例如， **-m-1** 有效，而 **-m-1** 无效。</span><span class="sxs-lookup"><span data-stu-id="fb31c-353">For example, **-m-1** is valid, and **-m-1** is not.</span></span>  
  
 <span data-ttu-id="fb31c-354">此选项还设置 `sqlcmd` 脚本变量 SQLCMDERRORLEVEL。</span><span class="sxs-lookup"><span data-stu-id="fb31c-354">This option also sets the `sqlcmd` scripting variable SQLCMDERRORLEVEL.</span></span> <span data-ttu-id="fb31c-355">此变量的默认值为 0。</span><span class="sxs-lookup"><span data-stu-id="fb31c-355">This variable has a default of 0.</span></span>  
  
 <span data-ttu-id="fb31c-356">`-V`*error_severity_level*</span><span class="sxs-lookup"><span data-stu-id="fb31c-356">`-V` *error_severity_level*</span></span>  
 <span data-ttu-id="fb31c-357">控制用于设置 ERRORLEVEL 变量的严重级别。</span><span class="sxs-lookup"><span data-stu-id="fb31c-357">Controls the severity level that is used to set the ERRORLEVEL variable.</span></span> <span data-ttu-id="fb31c-358">严重级别大于或等于此值的错误消息将设置 ERRORLEVEL。</span><span class="sxs-lookup"><span data-stu-id="fb31c-358">Error messages that have severity levels greater than or equal to this value set ERRORLEVEL.</span></span> <span data-ttu-id="fb31c-359">小于 0 的值将报告为 0。</span><span class="sxs-lookup"><span data-stu-id="fb31c-359">Values that are less than 0 are reported as 0.</span></span> <span data-ttu-id="fb31c-360">可以使用批处理文件和 CMD 文件来测试 ERRORLEVEL 变量的值。</span><span class="sxs-lookup"><span data-stu-id="fb31c-360">Batch and CMD files can be used to test the value of the ERRORLEVEL variable.</span></span>  
  
 <span data-ttu-id="fb31c-361">**其他选项**</span><span class="sxs-lookup"><span data-stu-id="fb31c-361">**Miscellaneous Options**</span></span>  
  <span data-ttu-id="fb31c-362">-a packet_size</span><span class="sxs-lookup"><span data-stu-id="fb31c-362">**-a** _packet_size_</span></span>  
 <span data-ttu-id="fb31c-363">需要不同大小的数据包。</span><span class="sxs-lookup"><span data-stu-id="fb31c-363">Requests a packet of a different size.</span></span> <span data-ttu-id="fb31c-364">此选项设置 `sqlcmd` 脚本变量 SQLCMDPACKETSIZE。</span><span class="sxs-lookup"><span data-stu-id="fb31c-364">This option sets the `sqlcmd` scripting variable SQLCMDPACKETSIZE.</span></span> <span data-ttu-id="fb31c-365">*packet_size* 必须是介于 512 和 32767 之间的值。</span><span class="sxs-lookup"><span data-stu-id="fb31c-365">*packet_size* must be a value between 512 and 32767.</span></span> <span data-ttu-id="fb31c-366">默认值为 4096。</span><span class="sxs-lookup"><span data-stu-id="fb31c-366">The default = 4096.</span></span> <span data-ttu-id="fb31c-367">如果脚本的两个 GO 命令之间包含大量 SQL 语句，则使用较大的数据包可以提高脚本执行的性能。</span><span class="sxs-lookup"><span data-stu-id="fb31c-367">A larger packet size can enhance performance for execution of scripts that have lots of SQL statements between GO commands.</span></span> <span data-ttu-id="fb31c-368">您可以请求更大的包大小。</span><span class="sxs-lookup"><span data-stu-id="fb31c-368">You can request a larger packet size.</span></span> <span data-ttu-id="fb31c-369">但是，如果请求遭拒绝，`sqlcmd` 将对包大小使用服务器默认值。</span><span class="sxs-lookup"><span data-stu-id="fb31c-369">However, if the request is denied, `sqlcmd` uses the server default for packet size.</span></span>  
  
 <span data-ttu-id="fb31c-370">-c batch_terminator</span><span class="sxs-lookup"><span data-stu-id="fb31c-370">**-c** _batch_terminator_</span></span>  
 <span data-ttu-id="fb31c-371">指定批处理终止符。</span><span class="sxs-lookup"><span data-stu-id="fb31c-371">Specifies the batch terminator.</span></span> <span data-ttu-id="fb31c-372">默认情况下，通过单独在一行中键入“GO”来终止命令并将其发送到 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="fb31c-372">By default, commands are terminated and sent to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] by typing the word "GO" on a line by itself.</span></span> <span data-ttu-id="fb31c-373">重置批处理终止符时，不要使用对操作系统具有特殊意义的 [!INCLUDE[tsql](../includes/tsql-md.md)] 保留关键字或字符，即便它们前面有反斜杠也是如此。</span><span class="sxs-lookup"><span data-stu-id="fb31c-373">When you reset the batch terminator, do not use [!INCLUDE[tsql](../includes/tsql-md.md)] reserved keywords or characters that have special meaning to the operating system, even if they are preceded by a backslash.</span></span>  
  
 <span data-ttu-id="fb31c-374">**-L**[**c**]</span><span class="sxs-lookup"><span data-stu-id="fb31c-374">**-L**[**c**]</span></span>  
 <span data-ttu-id="fb31c-375">列出本地配置的服务器计算机和在网络上播发的服务器计算机的名称。</span><span class="sxs-lookup"><span data-stu-id="fb31c-375">Lists the locally configured server computers, and the names of the server computers that are broadcasting on the network.</span></span> <span data-ttu-id="fb31c-376">此参数不能与其他参数结合使用。</span><span class="sxs-lookup"><span data-stu-id="fb31c-376">This parameter cannot be used in combination with other parameters.</span></span> <span data-ttu-id="fb31c-377">可以列出的服务器的最大数目是 3000。</span><span class="sxs-lookup"><span data-stu-id="fb31c-377">The maximum number of server computers that can be listed is 3000.</span></span> <span data-ttu-id="fb31c-378">如果服务器列表由于缓冲区大小而被截断，则会显示错误消息。</span><span class="sxs-lookup"><span data-stu-id="fb31c-378">If the server list is truncated because of the size of the buffer a warning message is displayed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fb31c-379">鉴于网络广播的特点，`sqlcmd` 不可能及时接收来自所有服务器的响应。</span><span class="sxs-lookup"><span data-stu-id="fb31c-379">Because of the nature of broadcasting on networks, `sqlcmd` may not receive a timely response from all servers.</span></span> <span data-ttu-id="fb31c-380">因此，每次调用该选项所返回的服务器列表都可能不同。</span><span class="sxs-lookup"><span data-stu-id="fb31c-380">Therefore, the list of servers returned may vary for each invocation of this option.</span></span>  
  
 <span data-ttu-id="fb31c-381">如果指定了可选参数**c** ，则输出将显示，但不显示服务器：标题行，并且列出的每个服务器行都没有前导空格。</span><span class="sxs-lookup"><span data-stu-id="fb31c-381">If the optional parameter **c** is specified, the output appears without the Servers: header line and each server line is listed without leading spaces.</span></span> <span data-ttu-id="fb31c-382">这被称为清除输出。</span><span class="sxs-lookup"><span data-stu-id="fb31c-382">This is referred to as clean output.</span></span> <span data-ttu-id="fb31c-383">清除输出可以提高脚本语言的处理性能。</span><span class="sxs-lookup"><span data-stu-id="fb31c-383">Clean output improves the processing performance of scripting languages.</span></span>  
  
 <span data-ttu-id="fb31c-384">**-p**[**1**]</span><span class="sxs-lookup"><span data-stu-id="fb31c-384">**-p**[**1**]</span></span>  
 <span data-ttu-id="fb31c-385">输出每个结果集的性能统计信息。</span><span class="sxs-lookup"><span data-stu-id="fb31c-385">Prints performance statistics for every result set.</span></span> <span data-ttu-id="fb31c-386">以下示例是性能统计信息的格式：</span><span class="sxs-lookup"><span data-stu-id="fb31c-386">The following is an example of the format for performance statistics:</span></span>  
  
 `Network packet size (bytes): n`  
  
 `x xact[s]:`  
  
 `Clock Time (ms.): total       t1  avg       t2 (t3 xacts per sec.)`  
  
 <span data-ttu-id="fb31c-387">其中：</span><span class="sxs-lookup"><span data-stu-id="fb31c-387">Where:</span></span>  
  
 <span data-ttu-id="fb31c-388">`x` = [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 处理的事务数。</span><span class="sxs-lookup"><span data-stu-id="fb31c-388">`x` = Number of transactions that are processed by [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="fb31c-389">`t1` = 所有事务的总时间。</span><span class="sxs-lookup"><span data-stu-id="fb31c-389">`t1` = Total time for all transactions.</span></span>  
  
 <span data-ttu-id="fb31c-390">`t2` = 单个事务的平均时间。</span><span class="sxs-lookup"><span data-stu-id="fb31c-390">`t2` = Average time for a single transaction.</span></span>  
  
 <span data-ttu-id="fb31c-391">`t3` = 每秒平均事务数。</span><span class="sxs-lookup"><span data-stu-id="fb31c-391">`t3` = Average number of transactions per second.</span></span>  
  
 <span data-ttu-id="fb31c-392">所有时间均以毫秒表示。</span><span class="sxs-lookup"><span data-stu-id="fb31c-392">All times are in milliseconds.</span></span>  
  
 <span data-ttu-id="fb31c-393">如果指定了可选参数 **1** ，则统计信息的输出格式为以冒号分隔的格式，此格式可以由脚本轻松导入到电子表格中或进行处理。</span><span class="sxs-lookup"><span data-stu-id="fb31c-393">If the optional parameter **1** is specified, the output format of the statistics is in colon-separated format that can be imported easily into a spreadsheet or processed by a script.</span></span>  
  
 <span data-ttu-id="fb31c-394">如果可选参数是除**1**之外的任何值，则会生成错误并 `sqlcmd` 退出。</span><span class="sxs-lookup"><span data-stu-id="fb31c-394">If the optional parameter is any value other than **1**, an error is generated and `sqlcmd` exits.</span></span>  
  
 <span data-ttu-id="fb31c-395">`-X`[**1**]</span><span class="sxs-lookup"><span data-stu-id="fb31c-395">`-X`[**1**]</span></span>  
 <span data-ttu-id="fb31c-396">从批处理文件执行 `sqlcmd` 时，将禁用可能危及系统安全的命令。</span><span class="sxs-lookup"><span data-stu-id="fb31c-396">Disables commands that might compromise system security when `sqlcmd` is executed from a batch file.</span></span> <span data-ttu-id="fb31c-397">禁用的命令仍然可以被识别；`sqlcmd` 发出警告消息并继续。</span><span class="sxs-lookup"><span data-stu-id="fb31c-397">The disabled commands are still recognized; `sqlcmd` issues a warning message and continues.</span></span> <span data-ttu-id="fb31c-398">如果指定了可选参数**1** ，则将 `sqlcmd` 生成错误消息，然后退出。</span><span class="sxs-lookup"><span data-stu-id="fb31c-398">If the optional parameter **1** is specified, `sqlcmd` generates an error message and then exits.</span></span> <span data-ttu-id="fb31c-399">使用 `-X` 选项时，将禁用以下命令：</span><span class="sxs-lookup"><span data-stu-id="fb31c-399">The following commands are disabled when the `-X` option is used:</span></span>  
  
-   <span data-ttu-id="fb31c-400">**ED**</span><span class="sxs-lookup"><span data-stu-id="fb31c-400">**ED**</span></span>  
  
-   <span data-ttu-id="fb31c-401">**!!**</span><span class="sxs-lookup"><span data-stu-id="fb31c-401">**!!**</span></span> <span data-ttu-id="fb31c-402">_command_</span><span class="sxs-lookup"><span data-stu-id="fb31c-402">_command_</span></span>  
  
 <span data-ttu-id="fb31c-403">如果指定 `-X` 选项，它会阻止将环境变量传递给 `sqlcmd`。</span><span class="sxs-lookup"><span data-stu-id="fb31c-403">If the `-X` option is specified, it prevents environment variables from being passed on to `sqlcmd`.</span></span> <span data-ttu-id="fb31c-404">同时该选项还会阻止执行通过使用 SQLCMDINI 脚本变量指定的启动脚本。</span><span class="sxs-lookup"><span data-stu-id="fb31c-404">It also prevents the startup script specified by using the SQLCMDINI scripting variable from being executed.</span></span> <span data-ttu-id="fb31c-405">有关脚本变量的详细信息 `sqlcmd` ，请参阅[将 Sqlcmd 与脚本变量结合使用](../relational-databases/scripting/sqlcmd-use-with-scripting-variables.md)。</span><span class="sxs-lookup"><span data-stu-id="fb31c-405">For more information about `sqlcmd` scripting variables, see [Use sqlcmd with Scripting Variables](../relational-databases/scripting/sqlcmd-use-with-scripting-variables.md).</span></span>  
  
 <span data-ttu-id="fb31c-406">**-?**</span><span class="sxs-lookup"><span data-stu-id="fb31c-406">**-?**</span></span>  
 <span data-ttu-id="fb31c-407">显示 `sqlcmd` 选项的语法摘要。</span><span class="sxs-lookup"><span data-stu-id="fb31c-407">Displays the syntax summary of `sqlcmd` options.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fb31c-408">备注</span><span class="sxs-lookup"><span data-stu-id="fb31c-408">Remarks</span></span>  
 <span data-ttu-id="fb31c-409">不必按语法部分所示的顺序使用选项。</span><span class="sxs-lookup"><span data-stu-id="fb31c-409">Options do not have to be used in the order shown in the syntax section.</span></span>  
  
 <span data-ttu-id="fb31c-410">在返回多个结果时，`sqlcmd` 在批处理中的每个结果集之间输出一个空行。</span><span class="sxs-lookup"><span data-stu-id="fb31c-410">When multiple results are returned, `sqlcmd` prints a blank line between each result set in a batch.</span></span> <span data-ttu-id="fb31c-411">此外，" \<x> 受影响的行" 消息不会应用于执行的语句。</span><span class="sxs-lookup"><span data-stu-id="fb31c-411">In addition, the "\<x> rows affected" message does not appear when it does not apply to the statement executed.</span></span>  
  
 <span data-ttu-id="fb31c-412">若要以 `sqlcmd` 交互方式使用，请 `sqlcmd` 在命令提示符下键入本主题前面所述的任何一个或多个选项。</span><span class="sxs-lookup"><span data-stu-id="fb31c-412">To use `sqlcmd` interactively, type `sqlcmd` at the command prompt with any one or more of the options described earlier in this topic.</span></span> <span data-ttu-id="fb31c-413">有关详细信息，请参阅 [使用 sqlcmd 实用工具](../relational-databases/scripting/sqlcmd-use-the-utility.md)</span><span class="sxs-lookup"><span data-stu-id="fb31c-413">For more information, see [Use the sqlcmd Utility](../relational-databases/scripting/sqlcmd-use-the-utility.md)</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fb31c-414">选项 **-L**、 **-Q**、 **-Z**或 **-i**会导致 `sqlcmd` 在执行后退出。</span><span class="sxs-lookup"><span data-stu-id="fb31c-414">The options **-L**, **-Q**, **-Z** or **-i** cause `sqlcmd` to exit after execution.</span></span>  
  
 <span data-ttu-id="fb31c-415">命令环境 (Cmd.exe) 中的 `sqlcmd` 命令行的总长度（包括所有参数和扩展变量）取决于 Cmd.exe 所在的操作系统。</span><span class="sxs-lookup"><span data-stu-id="fb31c-415">The total length of the `sqlcmd` command line in the command environment (Cmd.exe), including all arguments and expanded variables, is that which is determined by the operating system for Cmd.exe.</span></span>  
  
## <a name="variable-precedence-low-to-high"></a><span data-ttu-id="fb31c-416">变量优先级（从低到高）</span><span class="sxs-lookup"><span data-stu-id="fb31c-416">Variable Precedence (Low to High)</span></span>  
  
1.  <span data-ttu-id="fb31c-417">系统级环境变量。</span><span class="sxs-lookup"><span data-stu-id="fb31c-417">System-level environmental variables.</span></span>  
  
2.  <span data-ttu-id="fb31c-418">用户级环境变量</span><span class="sxs-lookup"><span data-stu-id="fb31c-418">User-level environmental variables</span></span>  
  
3.  <span data-ttu-id="fb31c-419">命令 shell (**设置**X = Y) 在命令提示符下运行之前设置 `sqlcmd` 。</span><span class="sxs-lookup"><span data-stu-id="fb31c-419">Command shell (**SET** X=Y) set at command prompt before running `sqlcmd`.</span></span>  
  
4.  <span data-ttu-id="fb31c-420">**sqlcmd-v** X=Y</span><span class="sxs-lookup"><span data-stu-id="fb31c-420">**sqlcmd-v** X=Y</span></span>  
  
5.  <span data-ttu-id="fb31c-421">**:Setvar** X Y</span><span class="sxs-lookup"><span data-stu-id="fb31c-421">**:Setvar** X Y</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fb31c-422">若要查看环境变量，请在“控制面板” 中打开“系统” ，然后单击“高级”  选项卡。</span><span class="sxs-lookup"><span data-stu-id="fb31c-422">To view the environmental variables, in **Control Panel**, open **System**, and then click the **Advanced** tab.</span></span>  
  
## <a name="sqlcmd-scripting-variables"></a><span data-ttu-id="fb31c-423">sqlcmd 脚本变量</span><span class="sxs-lookup"><span data-stu-id="fb31c-423">sqlcmd Scripting Variables</span></span>  
  
|<span data-ttu-id="fb31c-424">变量</span><span class="sxs-lookup"><span data-stu-id="fb31c-424">Variable</span></span>|<span data-ttu-id="fb31c-425">相关开关</span><span class="sxs-lookup"><span data-stu-id="fb31c-425">Related switch</span></span>|<span data-ttu-id="fb31c-426">R/W</span><span class="sxs-lookup"><span data-stu-id="fb31c-426">R/W</span></span>|<span data-ttu-id="fb31c-427">默认</span><span class="sxs-lookup"><span data-stu-id="fb31c-427">Default</span></span>|  
|--------------|--------------------|----------|-------------|  
|<span data-ttu-id="fb31c-428">SQLCMDUSER</span><span class="sxs-lookup"><span data-stu-id="fb31c-428">SQLCMDUSER</span></span>|<span data-ttu-id="fb31c-429">-U</span><span class="sxs-lookup"><span data-stu-id="fb31c-429">-U</span></span>|<span data-ttu-id="fb31c-430">R</span><span class="sxs-lookup"><span data-stu-id="fb31c-430">R</span></span>|<span data-ttu-id="fb31c-431">""</span><span class="sxs-lookup"><span data-stu-id="fb31c-431">""</span></span>|  
|<span data-ttu-id="fb31c-432">SQLCMDPASSWORD</span><span class="sxs-lookup"><span data-stu-id="fb31c-432">SQLCMDPASSWORD</span></span>|<span data-ttu-id="fb31c-433">-P</span><span class="sxs-lookup"><span data-stu-id="fb31c-433">-P</span></span>|--|<span data-ttu-id="fb31c-434">""</span><span class="sxs-lookup"><span data-stu-id="fb31c-434">""</span></span>|  
|<span data-ttu-id="fb31c-435">SQLCMDSERVER</span><span class="sxs-lookup"><span data-stu-id="fb31c-435">SQLCMDSERVER</span></span>|<span data-ttu-id="fb31c-436">sqlcmd</span><span class="sxs-lookup"><span data-stu-id="fb31c-436">-S</span></span>|<span data-ttu-id="fb31c-437">R</span><span class="sxs-lookup"><span data-stu-id="fb31c-437">R</span></span>|<span data-ttu-id="fb31c-438">"DefaultLocalInstance"</span><span class="sxs-lookup"><span data-stu-id="fb31c-438">"DefaultLocalInstance"</span></span>|  
|<span data-ttu-id="fb31c-439">SQLCMDWORKSTATION</span><span class="sxs-lookup"><span data-stu-id="fb31c-439">SQLCMDWORKSTATION</span></span>|<span data-ttu-id="fb31c-440">-H</span><span class="sxs-lookup"><span data-stu-id="fb31c-440">-H</span></span>|<span data-ttu-id="fb31c-441">R</span><span class="sxs-lookup"><span data-stu-id="fb31c-441">R</span></span>|<span data-ttu-id="fb31c-442">"ComputerName"</span><span class="sxs-lookup"><span data-stu-id="fb31c-442">"ComputerName"</span></span>|  
|<span data-ttu-id="fb31c-443">SQLCMDDBNAME</span><span class="sxs-lookup"><span data-stu-id="fb31c-443">SQLCMDDBNAME</span></span>|<span data-ttu-id="fb31c-444">-d</span><span class="sxs-lookup"><span data-stu-id="fb31c-444">-d</span></span>|<span data-ttu-id="fb31c-445">R</span><span class="sxs-lookup"><span data-stu-id="fb31c-445">R</span></span>|<span data-ttu-id="fb31c-446">""</span><span class="sxs-lookup"><span data-stu-id="fb31c-446">""</span></span>|  
|<span data-ttu-id="fb31c-447">SQLCMDLOGINTIMEOUT</span><span class="sxs-lookup"><span data-stu-id="fb31c-447">SQLCMDLOGINTIMEOUT</span></span>|<span data-ttu-id="fb31c-448">-l</span><span class="sxs-lookup"><span data-stu-id="fb31c-448">-l</span></span>|<span data-ttu-id="fb31c-449">R/W</span><span class="sxs-lookup"><span data-stu-id="fb31c-449">R/W</span></span>|<span data-ttu-id="fb31c-450">"8"（秒）</span><span class="sxs-lookup"><span data-stu-id="fb31c-450">"8" (seconds)</span></span>|  
|<span data-ttu-id="fb31c-451">SQLCMDSTATTIMEOUT</span><span class="sxs-lookup"><span data-stu-id="fb31c-451">SQLCMDSTATTIMEOUT</span></span>|<span data-ttu-id="fb31c-452">-t</span><span class="sxs-lookup"><span data-stu-id="fb31c-452">-t</span></span>|<span data-ttu-id="fb31c-453">R/W</span><span class="sxs-lookup"><span data-stu-id="fb31c-453">R/W</span></span>|<span data-ttu-id="fb31c-454">"0" = 无限期等待</span><span class="sxs-lookup"><span data-stu-id="fb31c-454">"0" = wait indefinitely</span></span>|  
|<span data-ttu-id="fb31c-455">SQLCMDHEADERS</span><span class="sxs-lookup"><span data-stu-id="fb31c-455">SQLCMDHEADERS</span></span>|<span data-ttu-id="fb31c-456">-H</span><span class="sxs-lookup"><span data-stu-id="fb31c-456">-h</span></span>|<span data-ttu-id="fb31c-457">R/W</span><span class="sxs-lookup"><span data-stu-id="fb31c-457">R/W</span></span>|<span data-ttu-id="fb31c-458">"0"</span><span class="sxs-lookup"><span data-stu-id="fb31c-458">"0"</span></span>|  
|<span data-ttu-id="fb31c-459">SQLCMDCOLSEP</span><span class="sxs-lookup"><span data-stu-id="fb31c-459">SQLCMDCOLSEP</span></span>|<span data-ttu-id="fb31c-460">-S</span><span class="sxs-lookup"><span data-stu-id="fb31c-460">-s</span></span>|<span data-ttu-id="fb31c-461">R/W</span><span class="sxs-lookup"><span data-stu-id="fb31c-461">R/W</span></span>|<span data-ttu-id="fb31c-462">" "</span><span class="sxs-lookup"><span data-stu-id="fb31c-462">" "</span></span>|  
|<span data-ttu-id="fb31c-463">SQLCMDCOLWIDTH</span><span class="sxs-lookup"><span data-stu-id="fb31c-463">SQLCMDCOLWIDTH</span></span>|<span data-ttu-id="fb31c-464">-w</span><span class="sxs-lookup"><span data-stu-id="fb31c-464">-w</span></span>|<span data-ttu-id="fb31c-465">R/W</span><span class="sxs-lookup"><span data-stu-id="fb31c-465">R/W</span></span>|<span data-ttu-id="fb31c-466">"0"</span><span class="sxs-lookup"><span data-stu-id="fb31c-466">"0"</span></span>|  
|<span data-ttu-id="fb31c-467">SQLCMDPACKETSIZE</span><span class="sxs-lookup"><span data-stu-id="fb31c-467">SQLCMDPACKETSIZE</span></span>|<span data-ttu-id="fb31c-468">-a</span><span class="sxs-lookup"><span data-stu-id="fb31c-468">-a</span></span>|<span data-ttu-id="fb31c-469">R</span><span class="sxs-lookup"><span data-stu-id="fb31c-469">R</span></span>|<span data-ttu-id="fb31c-470">"4096"</span><span class="sxs-lookup"><span data-stu-id="fb31c-470">"4096"</span></span>|  
|<span data-ttu-id="fb31c-471">SQLCMDERRORLEVEL</span><span class="sxs-lookup"><span data-stu-id="fb31c-471">SQLCMDERRORLEVEL</span></span>|<span data-ttu-id="fb31c-472">-M</span><span class="sxs-lookup"><span data-stu-id="fb31c-472">-m</span></span>|<span data-ttu-id="fb31c-473">R/W</span><span class="sxs-lookup"><span data-stu-id="fb31c-473">R/W</span></span>|<span data-ttu-id="fb31c-474">0</span><span class="sxs-lookup"><span data-stu-id="fb31c-474">0</span></span>|  
|<span data-ttu-id="fb31c-475">SQLCMDMAXVARTYPEWIDTH</span><span class="sxs-lookup"><span data-stu-id="fb31c-475">SQLCMDMAXVARTYPEWIDTH</span></span>|<span data-ttu-id="fb31c-476">-y</span><span class="sxs-lookup"><span data-stu-id="fb31c-476">-y</span></span>|<span data-ttu-id="fb31c-477">R/W</span><span class="sxs-lookup"><span data-stu-id="fb31c-477">R/W</span></span>|<span data-ttu-id="fb31c-478">"256"</span><span class="sxs-lookup"><span data-stu-id="fb31c-478">"256"</span></span>|  
|<span data-ttu-id="fb31c-479">SQLCMDMAXFIXEDTYPEWIDTH</span><span class="sxs-lookup"><span data-stu-id="fb31c-479">SQLCMDMAXFIXEDTYPEWIDTH</span></span>|<span data-ttu-id="fb31c-480">-y</span><span class="sxs-lookup"><span data-stu-id="fb31c-480">-Y</span></span>|<span data-ttu-id="fb31c-481">R/W</span><span class="sxs-lookup"><span data-stu-id="fb31c-481">R/W</span></span>|<span data-ttu-id="fb31c-482">"0" = 无限制</span><span class="sxs-lookup"><span data-stu-id="fb31c-482">"0" = unlimited</span></span>|  
|<span data-ttu-id="fb31c-483">SQLCMDEDITOR</span><span class="sxs-lookup"><span data-stu-id="fb31c-483">SQLCMDEDITOR</span></span>||<span data-ttu-id="fb31c-484">R/W</span><span class="sxs-lookup"><span data-stu-id="fb31c-484">R/W</span></span>|<span data-ttu-id="fb31c-485">"edit.com"</span><span class="sxs-lookup"><span data-stu-id="fb31c-485">"edit.com"</span></span>|  
|<span data-ttu-id="fb31c-486">SQLCMDINI</span><span class="sxs-lookup"><span data-stu-id="fb31c-486">SQLCMDINI</span></span>||<span data-ttu-id="fb31c-487">R</span><span class="sxs-lookup"><span data-stu-id="fb31c-487">R</span></span>|<span data-ttu-id="fb31c-488">""</span><span class="sxs-lookup"><span data-stu-id="fb31c-488">""</span></span>|  
  
 <span data-ttu-id="fb31c-489">SQLCMDUSER、SQLCMDPASSWORD 和 SQLCMDSERVER 是在使用 **:Connect**时</span><span class="sxs-lookup"><span data-stu-id="fb31c-489">SQLCMDUSER, SQLCMDPASSWORD and SQLCMDSERVER are set when **:Connect**</span></span>  
  
 <span data-ttu-id="fb31c-490">设置的。</span><span class="sxs-lookup"><span data-stu-id="fb31c-490">is used.</span></span>  
  
 <span data-ttu-id="fb31c-491">R 表示在程序初始化过程中只能设置一次值。</span><span class="sxs-lookup"><span data-stu-id="fb31c-491">R indicates the value can only be set one time during program initialization.</span></span>  
  
 <span data-ttu-id="fb31c-492">R/W 表示可以使用 **setvar** 命令修改值，并且后续命令将受新值的影响。</span><span class="sxs-lookup"><span data-stu-id="fb31c-492">R/W indicates that the value can be modified by using the **setvar** command and subsequent commands will be influenced by the new value.</span></span>  
  
## <a name="sqlcmd-commands"></a><span data-ttu-id="fb31c-493">sqlcmd 命令</span><span class="sxs-lookup"><span data-stu-id="fb31c-493">sqlcmd Commands</span></span>  
 <span data-ttu-id="fb31c-494">除 `sqlcmd` 中的 [!INCLUDE[tsql](../includes/tsql-md.md)] 语句之外，还可使用以下命令：</span><span class="sxs-lookup"><span data-stu-id="fb31c-494">In addition to [!INCLUDE[tsql](../includes/tsql-md.md)] statements within `sqlcmd`, the following commands are also available:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="fb31c-495">**GO** [*count*]</span><span class="sxs-lookup"><span data-stu-id="fb31c-495">**GO** [*count*]</span></span>|<span data-ttu-id="fb31c-496">**:List**</span><span class="sxs-lookup"><span data-stu-id="fb31c-496">**:List**</span></span>|  
|<span data-ttu-id="fb31c-497">[ **:** ] **RESET**</span><span class="sxs-lookup"><span data-stu-id="fb31c-497">[**:**] **RESET**</span></span>|<span data-ttu-id="fb31c-498">**:Error**</span><span class="sxs-lookup"><span data-stu-id="fb31c-498">**:Error**</span></span>|  
|<span data-ttu-id="fb31c-499">[ **:** ] **ED**</span><span class="sxs-lookup"><span data-stu-id="fb31c-499">[**:**] **ED**</span></span>|<span data-ttu-id="fb31c-500">**:Out**</span><span class="sxs-lookup"><span data-stu-id="fb31c-500">**:Out**</span></span>|  
|<span data-ttu-id="fb31c-501">[**:**] **!!**</span><span class="sxs-lookup"><span data-stu-id="fb31c-501">[**:**] **!!**</span></span>|<span data-ttu-id="fb31c-502">**:Perftrace**</span><span class="sxs-lookup"><span data-stu-id="fb31c-502">**:Perftrace**</span></span>|  
|<span data-ttu-id="fb31c-503">[ **:** ] **QUIT**</span><span class="sxs-lookup"><span data-stu-id="fb31c-503">[**:**] **QUIT**</span></span>|<span data-ttu-id="fb31c-504">**:Connect**</span><span class="sxs-lookup"><span data-stu-id="fb31c-504">**:Connect**</span></span>|  
|<span data-ttu-id="fb31c-505">[ **:** ] **EXIT**</span><span class="sxs-lookup"><span data-stu-id="fb31c-505">[**:**] **EXIT**</span></span>|<span data-ttu-id="fb31c-506">**:On Error**</span><span class="sxs-lookup"><span data-stu-id="fb31c-506">**:On Error**</span></span>|  
|<span data-ttu-id="fb31c-507">**:r**</span><span class="sxs-lookup"><span data-stu-id="fb31c-507">**:r**</span></span>|<span data-ttu-id="fb31c-508">**:Help**</span><span class="sxs-lookup"><span data-stu-id="fb31c-508">**:Help**</span></span>|  
|<span data-ttu-id="fb31c-509">**:ServerList**</span><span class="sxs-lookup"><span data-stu-id="fb31c-509">**:ServerList**</span></span>|<span data-ttu-id="fb31c-510">**:XML** [**ON** &#124; **OFF**]</span><span class="sxs-lookup"><span data-stu-id="fb31c-510">**:XML** [**ON** &#124; **OFF**]</span></span>|  
|<span data-ttu-id="fb31c-511">**:Setvar**</span><span class="sxs-lookup"><span data-stu-id="fb31c-511">**:Setvar**</span></span>|<span data-ttu-id="fb31c-512">**:Listvar**</span><span class="sxs-lookup"><span data-stu-id="fb31c-512">**:Listvar**</span></span>|  
  
 <span data-ttu-id="fb31c-513">使用 `sqlcmd` 命令时，请注意以下事项：</span><span class="sxs-lookup"><span data-stu-id="fb31c-513">Be aware of the following when you use `sqlcmd` commands:</span></span>  
  
-   <span data-ttu-id="fb31c-514">除 GO 以外，所有 `sqlcmd` 命令必须以冒号 (:) 为前缀。</span><span class="sxs-lookup"><span data-stu-id="fb31c-514">All `sqlcmd` commands, except GO, must be prefixed by a colon (:).</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="fb31c-515">为了保持现有 **osql** 脚本的向后兼容性，有些命令会被视为不带冒号。</span><span class="sxs-lookup"><span data-stu-id="fb31c-515">To maintain backward compatibility with existing **osql** scripts, some of the commands will be recognized without the colon.</span></span> <span data-ttu-id="fb31c-516">这由 [**:**] 指示。</span><span class="sxs-lookup"><span data-stu-id="fb31c-516">This is indicated by the [**:**].</span></span>  
  
-   <span data-ttu-id="fb31c-517">`sqlcmd` 命令只有出现在一行的开头时，才能够被识别。</span><span class="sxs-lookup"><span data-stu-id="fb31c-517">`sqlcmd` commands are recognized only if they appear at the start of a line.</span></span>  
  
-   <span data-ttu-id="fb31c-518">所有 `sqlcmd` 命令都不区分大小写。</span><span class="sxs-lookup"><span data-stu-id="fb31c-518">All `sqlcmd` commands are case insensitive.</span></span>  
  
-   <span data-ttu-id="fb31c-519">每个命令都必须位于单独的行中。</span><span class="sxs-lookup"><span data-stu-id="fb31c-519">Each command must be on a separate line.</span></span> <span data-ttu-id="fb31c-520">命令后面不能跟随 [!INCLUDE[tsql](../includes/tsql-md.md)] 语句或其他命令。</span><span class="sxs-lookup"><span data-stu-id="fb31c-520">A command cannot be followed by a [!INCLUDE[tsql](../includes/tsql-md.md)] statement or another command.</span></span>  
  
-   <span data-ttu-id="fb31c-521">命令将被立即执行。</span><span class="sxs-lookup"><span data-stu-id="fb31c-521">Commands are executed immediately.</span></span> <span data-ttu-id="fb31c-522">它们与 [!INCLUDE[tsql](../includes/tsql-md.md)] 语句不同，不会放在执行缓冲区中。</span><span class="sxs-lookup"><span data-stu-id="fb31c-522">They are not put in the execution buffer as [!INCLUDE[tsql](../includes/tsql-md.md)] statements are.</span></span>  
  
 <span data-ttu-id="fb31c-523">**编辑命令**</span><span class="sxs-lookup"><span data-stu-id="fb31c-523">**Editing Commands**</span></span>  
  <span data-ttu-id="fb31c-524">[ **:** ] **ED**</span><span class="sxs-lookup"><span data-stu-id="fb31c-524">[**:**] **ED**</span></span>  
 <span data-ttu-id="fb31c-525">启动文本编辑器。</span><span class="sxs-lookup"><span data-stu-id="fb31c-525">Starts the text editor.</span></span> <span data-ttu-id="fb31c-526">该编辑器可以用来编辑当前的 [!INCLUDE[tsql](../includes/tsql-md.md)] 批处理或上次执行的批处理。</span><span class="sxs-lookup"><span data-stu-id="fb31c-526">This editor can be used to edit the current [!INCLUDE[tsql](../includes/tsql-md.md)] batch, or the last executed batch.</span></span> <span data-ttu-id="fb31c-527">若要编辑上次执行的批处理，必须在上一批处理执行完之后立即键入 **ED** 命令。</span><span class="sxs-lookup"><span data-stu-id="fb31c-527">To edit the last executed batch, the **ED** command must be typed immediately after the last batch has completed execution.</span></span>  
  
 <span data-ttu-id="fb31c-528">文本编辑器由 SQLCMDEDITOR 环境变量定义。</span><span class="sxs-lookup"><span data-stu-id="fb31c-528">The text editor is defined by the SQLCMDEDITOR environment variable.</span></span> <span data-ttu-id="fb31c-529">默认编辑器为“Edit”。</span><span class="sxs-lookup"><span data-stu-id="fb31c-529">The default editor is 'Edit'.</span></span> <span data-ttu-id="fb31c-530">若要更改编辑器，请设置 SQLCMDEDITOR 环境变量。</span><span class="sxs-lookup"><span data-stu-id="fb31c-530">To change the editor, set the SQLCMDEDITOR environment variable.</span></span> <span data-ttu-id="fb31c-531">例如，若要将编辑器设置为 [!INCLUDE[msCoName](../includes/msconame-md.md)] 记事本，请在命令提示符处键入：</span><span class="sxs-lookup"><span data-stu-id="fb31c-531">For example, to set the editor to [!INCLUDE[msCoName](../includes/msconame-md.md)] Notepad, at the command prompt, type:</span></span>  
  
 `SET SQLCMDEDITOR=notepad`  
  
 <span data-ttu-id="fb31c-532">[ **:** ] **RESET**</span><span class="sxs-lookup"><span data-stu-id="fb31c-532">[**:**] **RESET**</span></span>  
 <span data-ttu-id="fb31c-533">清除语句缓存。</span><span class="sxs-lookup"><span data-stu-id="fb31c-533">Clears the statement cache.</span></span>  
  
 <span data-ttu-id="fb31c-534">**:List**</span><span class="sxs-lookup"><span data-stu-id="fb31c-534">**:List**</span></span>  
 <span data-ttu-id="fb31c-535">输出语句缓存的内容。</span><span class="sxs-lookup"><span data-stu-id="fb31c-535">Prints the content of the statement cache.</span></span>  
  
 <span data-ttu-id="fb31c-536">**变量**</span><span class="sxs-lookup"><span data-stu-id="fb31c-536">**Variables**</span></span>  
  <span data-ttu-id="fb31c-537">**： Setvar** \<**var**>[ **"*`value`*"** ]</span><span class="sxs-lookup"><span data-stu-id="fb31c-537">**:Setvar** \<**var**> [ **"*`value`*"** ]</span></span>  
 <span data-ttu-id="fb31c-538">定义 `sqlcmd` 脚本变量。</span><span class="sxs-lookup"><span data-stu-id="fb31c-538">Defines `sqlcmd` scripting variables.</span></span> <span data-ttu-id="fb31c-539">脚本变量具有如下格式： `$(VARNAME)`。</span><span class="sxs-lookup"><span data-stu-id="fb31c-539">Scripting variables have the following format: `$(VARNAME)`.</span></span>  
  
 <span data-ttu-id="fb31c-540">变量名称不区分大小写。</span><span class="sxs-lookup"><span data-stu-id="fb31c-540">Variable names are case insensitive.</span></span>  
  
 <span data-ttu-id="fb31c-541">可以通过下列方式设置脚本变量：</span><span class="sxs-lookup"><span data-stu-id="fb31c-541">Scripting variables can be set in the following ways:</span></span>  
  
-   <span data-ttu-id="fb31c-542">隐式使用命令行选项。</span><span class="sxs-lookup"><span data-stu-id="fb31c-542">Implicitly using a command-line option.</span></span> <span data-ttu-id="fb31c-543">例如， **-l**选项设置 SQLCMDLOGINTIMEOUT `sqlcmd` 变量。</span><span class="sxs-lookup"><span data-stu-id="fb31c-543">For example, the **-l** option sets the SQLCMDLOGINTIMEOUT `sqlcmd` variable.</span></span>  
  
-   <span data-ttu-id="fb31c-544">显式使用 **:Setvar** 命令。</span><span class="sxs-lookup"><span data-stu-id="fb31c-544">Explicitly by using the **:Setvar** command.</span></span>  
  
-   <span data-ttu-id="fb31c-545">在运行 `sqlcmd` 之前定义一个环境变量。</span><span class="sxs-lookup"><span data-stu-id="fb31c-545">By defining an environment variable before you run `sqlcmd`.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fb31c-546">`-X` 选项可阻止将环境变量传递给 `sqlcmd`。</span><span class="sxs-lookup"><span data-stu-id="fb31c-546">The `-X` option prevents environment variables from being passed on to `sqlcmd`.</span></span>  
  
 <span data-ttu-id="fb31c-547">如果使用 **:Setvar** 定义的变量和某个环境变量同名，则使用 **:Setvar** 定义的变量优先。</span><span class="sxs-lookup"><span data-stu-id="fb31c-547">If a variable defined by using **:Setvar** and an environment variable have the same name, the variable defined by using **:Setvar** takes precedence.</span></span>  
  
 <span data-ttu-id="fb31c-548">变量名中不能包含空格字符。</span><span class="sxs-lookup"><span data-stu-id="fb31c-548">Variable names must not contain blank space characters.</span></span>  
  
 <span data-ttu-id="fb31c-549">变量名不能与变量表达式（如 $(var)）具有相同的形式。</span><span class="sxs-lookup"><span data-stu-id="fb31c-549">Variable names cannot have the same form as a variable expression, such as $(var).</span></span>  
  
 <span data-ttu-id="fb31c-550">如果脚本变量的字符串值中含有空格，请用引号将该值引起来。</span><span class="sxs-lookup"><span data-stu-id="fb31c-550">If the string value of the scripting variable contains blank spaces, enclose the value in quotation marks.</span></span> <span data-ttu-id="fb31c-551">如果未指定脚本变量的值，则将删除该脚本变量。</span><span class="sxs-lookup"><span data-stu-id="fb31c-551">If a value for a scripting variable is not specified, the scripting variable is dropped.</span></span>  
  
 <span data-ttu-id="fb31c-552">**:Listvar**</span><span class="sxs-lookup"><span data-stu-id="fb31c-552">**:Listvar**</span></span>  
 <span data-ttu-id="fb31c-553">显示当前设置的脚本变量列表。</span><span class="sxs-lookup"><span data-stu-id="fb31c-553">Displays a list of the scripting variables that are currently set.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fb31c-554">仅显示由设置的脚本变量 `sqlcmd` 和使用 **： Setvar**命令设置的脚本变量。</span><span class="sxs-lookup"><span data-stu-id="fb31c-554">Only scripting variables that are set by `sqlcmd`, and those that are set using the **:Setvar** command will be displayed.</span></span>  
  
 <span data-ttu-id="fb31c-555">**输出命令**</span><span class="sxs-lookup"><span data-stu-id="fb31c-555">**Output Commands**</span></span>  
  <span data-ttu-id="fb31c-556">**:Error** </span><span class="sxs-lookup"><span data-stu-id="fb31c-556">**:Error** </span></span>  
 <span data-ttu-id="fb31c-557">**_\<_** _filename_  **_>|_ STDERR |STDOUT**</span><span class="sxs-lookup"><span data-stu-id="fb31c-557">**_\<_** _filename_  **_>|_ STDERR|STDOUT**</span></span>  
 <span data-ttu-id="fb31c-558">将所有错误输出重定向到 *file name*指定的文件、 **stderr** 或 **stdout**。</span><span class="sxs-lookup"><span data-stu-id="fb31c-558">Redirect all error output to the file specified by *file name*, to **stderr** or to **stdout**.</span></span> <span data-ttu-id="fb31c-559">**Error** 命令可以在一个脚本中多次出现。</span><span class="sxs-lookup"><span data-stu-id="fb31c-559">The **Error** command can appear multiple times in a script.</span></span> <span data-ttu-id="fb31c-560">默认情况下，错误输出将发送到 **stderr**。</span><span class="sxs-lookup"><span data-stu-id="fb31c-560">By default, error output is sent to **stderr**.</span></span>  
  
 <span data-ttu-id="fb31c-561">*file name*</span><span class="sxs-lookup"><span data-stu-id="fb31c-561">*file name*</span></span>  
 <span data-ttu-id="fb31c-562">创建并打开一个要接收输出的文件。</span><span class="sxs-lookup"><span data-stu-id="fb31c-562">Creates and opens a file that will receive the output.</span></span> <span data-ttu-id="fb31c-563">若该文件已经存在，则将其截断为零字节。</span><span class="sxs-lookup"><span data-stu-id="fb31c-563">If the file already exists, it will be truncated to zero bytes.</span></span> <span data-ttu-id="fb31c-564">若该文件不可用（由于权限或其他原因），将不会切换输出，也不会将输出发送到上次指定的目标或默认目标。</span><span class="sxs-lookup"><span data-stu-id="fb31c-564">If the file is not available because of permissions or other reasons, the output will not be switched and will be sent to the last specified or default destination.</span></span>  
  
 <span data-ttu-id="fb31c-565">**STDERR**</span><span class="sxs-lookup"><span data-stu-id="fb31c-565">**STDERR**</span></span>  
 <span data-ttu-id="fb31c-566">将错误输出切换到 **stderr** 流。</span><span class="sxs-lookup"><span data-stu-id="fb31c-566">Switches error output to the **stderr** stream.</span></span> <span data-ttu-id="fb31c-567">如果已经重定向，流的重定向目标将会收到错误输出。</span><span class="sxs-lookup"><span data-stu-id="fb31c-567">If this has been redirected, the target to which the stream has been redirected will receive the error output.</span></span>  
  
 <span data-ttu-id="fb31c-568">**STDOUT**</span><span class="sxs-lookup"><span data-stu-id="fb31c-568">**STDOUT**</span></span>  
 <span data-ttu-id="fb31c-569">将错误输出切换到 **stdout** 流。</span><span class="sxs-lookup"><span data-stu-id="fb31c-569">Switches error output to the **stdout** stream.</span></span> <span data-ttu-id="fb31c-570">如果已经重定向，流的重定向目标将会收到错误输出。</span><span class="sxs-lookup"><span data-stu-id="fb31c-570">If this has been redirected, the target to which the stream has been redirected will receive the error output.</span></span>  
  
 <span data-ttu-id="fb31c-571">\*\*： Out \<** _filename_ **> \*\* | **STDERR** | **STDOUT**</span><span class="sxs-lookup"><span data-stu-id="fb31c-571">**:Out \<** _filename_ **>**| **STDERR**| **STDOUT**</span></span>  
 <span data-ttu-id="fb31c-572">创建所有查询结果并将它们重定向到 *file name*指定的文件、 **stderr** 或 **stdout**。</span><span class="sxs-lookup"><span data-stu-id="fb31c-572">Creates and redirects all query results to the file specified by *file name*, to **stderr** or to **stdout**.</span></span> <span data-ttu-id="fb31c-573">默认情况下，输出将发送到 **stdout**。</span><span class="sxs-lookup"><span data-stu-id="fb31c-573">By default, output is sent to **stdout**.</span></span> <span data-ttu-id="fb31c-574">若该文件已经存在，则将其截断为零字节。</span><span class="sxs-lookup"><span data-stu-id="fb31c-574">If the file already exists, it will be truncated to zero bytes.</span></span> <span data-ttu-id="fb31c-575">**Out** 命令可以在一个脚本中多次出现。</span><span class="sxs-lookup"><span data-stu-id="fb31c-575">The **Out** command can appear multiple times in a script.</span></span>  
  
 <span data-ttu-id="fb31c-576">\*\*:P erftrace \<** _filename_ **> \*\* | **STDERR** | **STDOUT**</span><span class="sxs-lookup"><span data-stu-id="fb31c-576">**:Perftrace \<** _filename_ **>**| **STDERR**| **STDOUT**</span></span>  
 <span data-ttu-id="fb31c-577">创建所有性能跟踪信息并将它们重定向到 *file name*指定的文件、 **stderr** 或 **stdout**。</span><span class="sxs-lookup"><span data-stu-id="fb31c-577">Creates and redirects all performance trace information to the file specified by *file name*, to **stderr** or to **stdout**.</span></span> <span data-ttu-id="fb31c-578">默认情况下，性能跟踪输出将发送到 **stdout**。</span><span class="sxs-lookup"><span data-stu-id="fb31c-578">By default performance trace output is sent to **stdout**.</span></span> <span data-ttu-id="fb31c-579">若该文件已经存在，则将其截断为零字节。</span><span class="sxs-lookup"><span data-stu-id="fb31c-579">If the file already exists, it will be truncated to zero bytes.</span></span> <span data-ttu-id="fb31c-580">**Perftrace** 命令可以在一个脚本中多次出现。</span><span class="sxs-lookup"><span data-stu-id="fb31c-580">The **Perftrace** command can appear multiple times in a script.</span></span>  
  
 <span data-ttu-id="fb31c-581">**执行控制命令**</span><span class="sxs-lookup"><span data-stu-id="fb31c-581">**Execution Control Commands**</span></span>  
  <span data-ttu-id="fb31c-582">**：出错时**[ `exit`  |  `ignore` ]</span><span class="sxs-lookup"><span data-stu-id="fb31c-582">**:On Error**[ `exit` | `ignore`]</span></span>  
 <span data-ttu-id="fb31c-583">设置在脚本或批处理执行过程中发生错误时要执行的操作。</span><span class="sxs-lookup"><span data-stu-id="fb31c-583">Sets the action to be performed when an error occurs during script or batch execution.</span></span>  
  
 <span data-ttu-id="fb31c-584">使用 `exit` 选项时，`sqlcmd` 退出，并显示相应的错误值。</span><span class="sxs-lookup"><span data-stu-id="fb31c-584">When the `exit` option is used, `sqlcmd` exits with the appropriate error value.</span></span>  
  
 <span data-ttu-id="fb31c-585">使用 `ignore` 选项时，`sqlcmd` 会忽略错误，并继续执行批处理或脚本。</span><span class="sxs-lookup"><span data-stu-id="fb31c-585">When the `ignore` option is used, `sqlcmd` ignores the error and continues executing the batch or script.</span></span> <span data-ttu-id="fb31c-586">默认情况下，会输出错误消息。</span><span class="sxs-lookup"><span data-stu-id="fb31c-586">By default, an error message will be printed.</span></span>  
  
 <span data-ttu-id="fb31c-587">[ **:** ] **QUIT**</span><span class="sxs-lookup"><span data-stu-id="fb31c-587">[**:**] **QUIT**</span></span>  
 <span data-ttu-id="fb31c-588">导致 `sqlcmd` 退出。</span><span class="sxs-lookup"><span data-stu-id="fb31c-588">Causes `sqlcmd` to exit.</span></span>  
  
 <span data-ttu-id="fb31c-589">[**:**]**EXIT**[ \*\* (*`statement`*) \*\* ]</span><span class="sxs-lookup"><span data-stu-id="fb31c-589">[**:**] **EXIT**[ **(*`statement`*)** ]</span></span>  
 <span data-ttu-id="fb31c-590">允许您将 SELECT 语句的结果用作 `sqlcmd` 的返回值。</span><span class="sxs-lookup"><span data-stu-id="fb31c-590">Lets you use the result of a SELECT statement as the return value from `sqlcmd`.</span></span> <span data-ttu-id="fb31c-591">如果为数值，最后一个结果行的第一列将转换为 4 字节的整数（长整型）。</span><span class="sxs-lookup"><span data-stu-id="fb31c-591">If numeric, the first column of the last result row is converted to a 4-byte integer (long).</span></span> <span data-ttu-id="fb31c-592">MS-DOS 将低字节传递给父进程或操作系统错误级别。</span><span class="sxs-lookup"><span data-stu-id="fb31c-592">MS-DOS passes the low byte to the parent process or operating system error level.</span></span> <span data-ttu-id="fb31c-593">Windows 200x 传递整个 4 字节整数。</span><span class="sxs-lookup"><span data-stu-id="fb31c-593">Windows 200x passes the whole 4-byte integer.</span></span> <span data-ttu-id="fb31c-594">语法为：</span><span class="sxs-lookup"><span data-stu-id="fb31c-594">The syntax is:</span></span>  
  
 `:EXIT(query)`  
  
 <span data-ttu-id="fb31c-595">例如：</span><span class="sxs-lookup"><span data-stu-id="fb31c-595">For example:</span></span>  
  
 `:EXIT(SELECT @@ROWCOUNT)`  
  
 <span data-ttu-id="fb31c-596">您还可以在批处理文件中包含 **EXIT** 参数。</span><span class="sxs-lookup"><span data-stu-id="fb31c-596">You can also include the **EXIT** parameter as part of a batch file.</span></span> <span data-ttu-id="fb31c-597">例如，在命令提示符处键入：</span><span class="sxs-lookup"><span data-stu-id="fb31c-597">For example, at the command prompt, type:</span></span>  
  
 `sqlcmd -Q "EXIT(SELECT COUNT(*) FROM '%1')"`  
  
 <span data-ttu-id="fb31c-598">此 `sqlcmd` 实用工具将\*\* ( # B1\*\*之间的所有内容发送到服务器。</span><span class="sxs-lookup"><span data-stu-id="fb31c-598">The `sqlcmd` utility sends everything between the parentheses **()** to the server.</span></span> <span data-ttu-id="fb31c-599">如果系统存储过程选择了一个集合并返回一个值，则仅返回选择的内容。</span><span class="sxs-lookup"><span data-stu-id="fb31c-599">If a system stored procedure selects a set and returns a value, only the selection is returned.</span></span> <span data-ttu-id="fb31c-600">如果圆括号中没有任何内容，则 EXIT **()** 语句会执行批处理中此语句前的所有内容，然后退出，且不返回任何值。</span><span class="sxs-lookup"><span data-stu-id="fb31c-600">The EXIT **()** statement with nothing between the parentheses executes everything before it in the batch and then exits without a return value.</span></span>  
  
 <span data-ttu-id="fb31c-601">当指定了不正确的查询时，`sqlcmd` 将退出，且不返回任何值。</span><span class="sxs-lookup"><span data-stu-id="fb31c-601">When an incorrect query is specified, `sqlcmd` will exit without a return value.</span></span>  
  
 <span data-ttu-id="fb31c-602">下面是 EXIT 格式的列表：</span><span class="sxs-lookup"><span data-stu-id="fb31c-602">Here is a list of EXIT formats:</span></span>  
  
-   <span data-ttu-id="fb31c-603">:EXIT</span><span class="sxs-lookup"><span data-stu-id="fb31c-603">:EXIT</span></span>  
  
 <span data-ttu-id="fb31c-604">不执行批处理就立即退出，无返回值。</span><span class="sxs-lookup"><span data-stu-id="fb31c-604">Does not execute the batch, and then quits immediately and returns no value.</span></span>  
  
-   <span data-ttu-id="fb31c-605">:EXIT( )</span><span class="sxs-lookup"><span data-stu-id="fb31c-605">:EXIT( )</span></span>  
  
 <span data-ttu-id="fb31c-606">执行批处理后退出，不返回值。</span><span class="sxs-lookup"><span data-stu-id="fb31c-606">Executes the batch, and then quits and returns no value.</span></span>  
  
-   <span data-ttu-id="fb31c-607">:EXIT(query)</span><span class="sxs-lookup"><span data-stu-id="fb31c-607">:EXIT(query)</span></span>  
  
 <span data-ttu-id="fb31c-608">执行包括查询的批处理，返回查询的结果后退出。</span><span class="sxs-lookup"><span data-stu-id="fb31c-608">Executes the batch that includes the query, and then quits after it returns the results of the query.</span></span>  
  
 <span data-ttu-id="fb31c-609">如果在脚本中使用 RAISERROR， `sqlcmd` 并引发127状态， `sqlcmd` 将退出并将消息 ID 返回给客户端。</span><span class="sxs-lookup"><span data-stu-id="fb31c-609">If RAISERROR is used within a `sqlcmd` script and a state of 127 is raised, `sqlcmd` will quit and return the message ID back to the client.</span></span> <span data-ttu-id="fb31c-610">例如：</span><span class="sxs-lookup"><span data-stu-id="fb31c-610">For example:</span></span>  
  
 `RAISERROR(50001, 10, 127)`  
  
 <span data-ttu-id="fb31c-611">该错误会导致 `sqlcmd` 脚本终止并将消息 ID 50001 返回给客户端。</span><span class="sxs-lookup"><span data-stu-id="fb31c-611">This error will cause the `sqlcmd` script to end and return the message ID 50001 to the client.</span></span>  
  
 <span data-ttu-id="fb31c-612">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 保留了介于 -1 到 -99 之间的返回值；`sqlcmd` 定义了以下附加返回值：</span><span class="sxs-lookup"><span data-stu-id="fb31c-612">The return values -1 to -99 are reserved by [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]; `sqlcmd` defines the following additional return values:</span></span>  
  
|<span data-ttu-id="fb31c-613">返回值</span><span class="sxs-lookup"><span data-stu-id="fb31c-613">Return Values</span></span>|<span data-ttu-id="fb31c-614">说明</span><span class="sxs-lookup"><span data-stu-id="fb31c-614">Description</span></span>|  
|-------------------|-----------------|  
|<span data-ttu-id="fb31c-615">-100</span><span class="sxs-lookup"><span data-stu-id="fb31c-615">-100</span></span>|<span data-ttu-id="fb31c-616">选择返回值前遇到错误。</span><span class="sxs-lookup"><span data-stu-id="fb31c-616">Error encountered prior to selecting return value.</span></span>|  
|<span data-ttu-id="fb31c-617">-101</span><span class="sxs-lookup"><span data-stu-id="fb31c-617">-101</span></span>|<span data-ttu-id="fb31c-618">选择返回值时找不到行。</span><span class="sxs-lookup"><span data-stu-id="fb31c-618">No rows found when selecting return value.</span></span>|  
|<span data-ttu-id="fb31c-619">-102</span><span class="sxs-lookup"><span data-stu-id="fb31c-619">-102</span></span>|<span data-ttu-id="fb31c-620">选择返回值时发生转换错误。</span><span class="sxs-lookup"><span data-stu-id="fb31c-620">Conversion error occurred when selecting return value.</span></span>|  
  
 <span data-ttu-id="fb31c-621">**GO** [*count*]</span><span class="sxs-lookup"><span data-stu-id="fb31c-621">**GO** [*count*]</span></span>  
 <span data-ttu-id="fb31c-622">GO 在批处理和执行任何缓存 [!INCLUDE[tsql](../includes/tsql-md.md)] 语句结尾时会发出信号。</span><span class="sxs-lookup"><span data-stu-id="fb31c-622">GO signals both the end of a batch and the execution of any cached [!INCLUDE[tsql](../includes/tsql-md.md)] statements.</span></span> <span data-ttu-id="fb31c-623">在为 *count*指定一个值时，缓存的语句会被作为单个批处理执行 *count* 次。</span><span class="sxs-lookup"><span data-stu-id="fb31c-623">When specifying a value for *count*, the cached statements will be executed *count* times, as a single batch.</span></span>  
  
 <span data-ttu-id="fb31c-624">**其他命令**</span><span class="sxs-lookup"><span data-stu-id="fb31c-624">**Miscellaneous Commands**</span></span>  
  <span data-ttu-id="fb31c-625">**： r\<** _filename_ **>**</span><span class="sxs-lookup"><span data-stu-id="fb31c-625">**:r \<** _filename_ **>**</span></span>  
 <span data-ttu-id="fb31c-626">[!INCLUDE[tsql](../includes/tsql-md.md)] `sqlcmd` 将由指定的文件中的其他语句和命令分析 **<*`filename`*>** 到语句缓存中。</span><span class="sxs-lookup"><span data-stu-id="fb31c-626">Parses additional [!INCLUDE[tsql](../includes/tsql-md.md)] statements and `sqlcmd` commands from the file specified by **<*`filename`*>** into the statement cache.</span></span>  
  
 <span data-ttu-id="fb31c-627">如果文件包含的 [!INCLUDE[tsql](../includes/tsql-md.md)] 语句后面没有跟随 **GO**，则必须在 **:r** 的后一行中输入 **GO**。</span><span class="sxs-lookup"><span data-stu-id="fb31c-627">If the file contains [!INCLUDE[tsql](../includes/tsql-md.md)] statements that are not followed by **GO**, you must enter **GO** on the line that follows **:r**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fb31c-628">**\<** _filename_ **>** 相对于在其中运行的启动目录进行读取 `sqlcmd` 。</span><span class="sxs-lookup"><span data-stu-id="fb31c-628">**\<** _filename_ **>** is read relative to the startup directory in which `sqlcmd` was run.</span></span>  
  
 <span data-ttu-id="fb31c-629">当遇到批处理终止符之后，将读取并执行该文件。</span><span class="sxs-lookup"><span data-stu-id="fb31c-629">The file will be read and executed after a batch terminator is encountered.</span></span> <span data-ttu-id="fb31c-630">可以发出多个 **:r** 命令。</span><span class="sxs-lookup"><span data-stu-id="fb31c-630">You can issue multiple **:r** commands.</span></span> <span data-ttu-id="fb31c-631">该文件可以包含任何 `sqlcmd` 命令，</span><span class="sxs-lookup"><span data-stu-id="fb31c-631">The file may include any `sqlcmd` command.</span></span> <span data-ttu-id="fb31c-632">包括批处理终止符 **GO**。</span><span class="sxs-lookup"><span data-stu-id="fb31c-632">This includes the batch terminator **GO**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fb31c-633">每遇到一个 **:r** 命令，交互模式下显示的行计数都会加一。</span><span class="sxs-lookup"><span data-stu-id="fb31c-633">The line count that is displayed in interactive mode will be increased by one for every **:r** command encountered.</span></span> <span data-ttu-id="fb31c-634">**:r** 命令会出现在 list 命令的输出中。</span><span class="sxs-lookup"><span data-stu-id="fb31c-634">The **:r** command will appear in the output of the list command.</span></span>  
  
 <span data-ttu-id="fb31c-635">**:Serverlist**</span><span class="sxs-lookup"><span data-stu-id="fb31c-635">**:Serverlist**</span></span>  
 <span data-ttu-id="fb31c-636">列出在本地配置的服务器和在网络上广播的服务器的名称。</span><span class="sxs-lookup"><span data-stu-id="fb31c-636">Lists the locally configured servers and the names of the servers broadcasting on the network.</span></span>  
  
 <span data-ttu-id="fb31c-637">**：连接** _server_name_[ **\\** _instance_name_] [-l*超时*] [-U *user_name* [-P *password*]]</span><span class="sxs-lookup"><span data-stu-id="fb31c-637">**:Connect** _server_name_[**\\**_instance_name_] [-l *timeout*] [-U *user_name* [-P *password*]]</span></span>  
 <span data-ttu-id="fb31c-638">连接到 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的一个实例。</span><span class="sxs-lookup"><span data-stu-id="fb31c-638">Connects to an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="fb31c-639">同时关闭当前的连接。</span><span class="sxs-lookup"><span data-stu-id="fb31c-639">Also closes the current connection.</span></span>  
  
 <span data-ttu-id="fb31c-640">超时选项：</span><span class="sxs-lookup"><span data-stu-id="fb31c-640">Time-out options:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="fb31c-641">0</span><span class="sxs-lookup"><span data-stu-id="fb31c-641">0</span></span>|<span data-ttu-id="fb31c-642">永远等待</span><span class="sxs-lookup"><span data-stu-id="fb31c-642">wait forever</span></span>|  
|<span data-ttu-id="fb31c-643">n>0</span><span class="sxs-lookup"><span data-stu-id="fb31c-643">n>0</span></span>|<span data-ttu-id="fb31c-644">等待 n 秒钟</span><span class="sxs-lookup"><span data-stu-id="fb31c-644">wait for n seconds</span></span>|  
  
 <span data-ttu-id="fb31c-645">SQLCMDSERVER 脚本变量将反映当前的活动连接。</span><span class="sxs-lookup"><span data-stu-id="fb31c-645">The SQLCMDSERVER scripting variable will reflect the current active connection.</span></span>  
  
 <span data-ttu-id="fb31c-646">如果未指定 *timeout* ，则其默认值将为 SQLCMDLOGINTIMEOUT 变量的值。</span><span class="sxs-lookup"><span data-stu-id="fb31c-646">If *timeout* is not specified, the value of the SQLCMDLOGINTIMEOUT variable is the default.</span></span>  
  
 <span data-ttu-id="fb31c-647">仅当指定了 *user_name* （作为选项或环境变量）时，才会提示用户输入密码。</span><span class="sxs-lookup"><span data-stu-id="fb31c-647">If only *user_name* is specified (either as an option, or as an environment variable), the user will be prompted to enter a password.</span></span> <span data-ttu-id="fb31c-648">如果已设置 SQLCMDUSER 或 SQLCMDPASSWORD 环境变量，则不会出现此提示。</span><span class="sxs-lookup"><span data-stu-id="fb31c-648">This is not true if the SQLCMDUSER or SQLCMDPASSWORD environment variables have been set.</span></span> <span data-ttu-id="fb31c-649">如果既未提供选项，又未提供环境变量，则使用 Windows 身份验证模式登录。</span><span class="sxs-lookup"><span data-stu-id="fb31c-649">If neither options nor environment variables are provided, Windows Authentication mode is used to login.</span></span> <span data-ttu-id="fb31c-650">例如，若要使用集成安全性连接到 `instance1`[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]的一个实例（如 `myserver`），则会使用以下内容：</span><span class="sxs-lookup"><span data-stu-id="fb31c-650">For example to connect to an instance, `instance1`, of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], `myserver`, by using integrated security you would use the following:</span></span>  
  
 `:connect myserver\instance1`  
  
 <span data-ttu-id="fb31c-651">若要使用脚本变量连接到 `myserver` 的默认实例，您会使用以下内容：</span><span class="sxs-lookup"><span data-stu-id="fb31c-651">To connect to the default instance of `myserver` using scripting variables, you would use the following:</span></span>  
  
 `:setvar myusername test`  
  
 `:setvar myservername myserver`  
  
 `:connect $(myservername) $(myusername)`  
  
 <span data-ttu-id="fb31c-652">[**:**] **!!**\< *command*></span><span class="sxs-lookup"><span data-stu-id="fb31c-652">[**:**] **!!**\< *command*></span></span>  
 <span data-ttu-id="fb31c-653">执行操作系统命令。</span><span class="sxs-lookup"><span data-stu-id="fb31c-653">Executes operating system commands.</span></span> <span data-ttu-id="fb31c-654">若要执行操作系统命令，请用两个感叹号 ( **!!** ) 开始一行，后面输入操作系统命令。</span><span class="sxs-lookup"><span data-stu-id="fb31c-654">To execute an operating system command, start a line with two exclamation marks (**!!**) followed by the operating system command.</span></span> <span data-ttu-id="fb31c-655">例如：</span><span class="sxs-lookup"><span data-stu-id="fb31c-655">For example:</span></span>  
  
 `:!! Dir`  
  
> [!NOTE]  
>  <span data-ttu-id="fb31c-656">该命令在运行 `sqlcmd` 的计算机上执行。</span><span class="sxs-lookup"><span data-stu-id="fb31c-656">The command is executed on the computer on which `sqlcmd` is running.</span></span>  
  
 <span data-ttu-id="fb31c-657">**:XML** [**ON** | **OFF**]</span><span class="sxs-lookup"><span data-stu-id="fb31c-657">**:XML** [**ON** | **OFF**]</span></span>  
 <span data-ttu-id="fb31c-658">有关详细信息，请参阅本主题后面的“XML 输出格式”</span><span class="sxs-lookup"><span data-stu-id="fb31c-658">For more information, see "XML Output Format," later in this topic</span></span>  
  
 <span data-ttu-id="fb31c-659">**:Help**</span><span class="sxs-lookup"><span data-stu-id="fb31c-659">**:Help**</span></span>  
 <span data-ttu-id="fb31c-660">列出 `sqlcmd` 命令以及每个命令的简短说明。</span><span class="sxs-lookup"><span data-stu-id="fb31c-660">Lists `sqlcmd` commands together with a short description of each command.</span></span>  
  
### <a name="sqlcmd-file-names"></a><span data-ttu-id="fb31c-661">sqlcmd 文件名</span><span class="sxs-lookup"><span data-stu-id="fb31c-661">sqlcmd File Names</span></span>  
 <span data-ttu-id="fb31c-662">`sqlcmd`输入文件可以通过 **-i**选项或 **： r**命令指定。</span><span class="sxs-lookup"><span data-stu-id="fb31c-662">`sqlcmd` input files can be specified with the **-i** option or the **:r** command.</span></span> <span data-ttu-id="fb31c-663">可以使用 **-o** 选项或 **:Error**、 **:Out** 和 **:Perftrace** 命令指定输出文件。</span><span class="sxs-lookup"><span data-stu-id="fb31c-663">Output files can be specified with the **-o** option or the **:Error**, **:Out** and **:Perftrace** commands.</span></span> <span data-ttu-id="fb31c-664">以下是使用这些文件的一些原则：</span><span class="sxs-lookup"><span data-stu-id="fb31c-664">The following are some guidelines for working with these files:</span></span>  
  
-   <span data-ttu-id="fb31c-665">**： Error**、 **： Out**和 **:P erftrace**应使用不同 **<*`filename`*>** 的。</span><span class="sxs-lookup"><span data-stu-id="fb31c-665">**:Error**, **:Out** and **:Perftrace** should use separate **<*`filename`*>**.</span></span> <span data-ttu-id="fb31c-666">如果使用相同的 **<*`filename`*>** ，则命令中的输入可能会混杂在一起。</span><span class="sxs-lookup"><span data-stu-id="fb31c-666">If the same **<*`filename`*>** is used, inputs from the commands may be intermixed.</span></span>  
  
-   <span data-ttu-id="fb31c-667">如果从本地计算机的 `sqlcmd` 调用远程服务器上的输入文件，并且该文件包含驱动器文件路径（如 :out c:\OutputFile.txt），</span><span class="sxs-lookup"><span data-stu-id="fb31c-667">If an input file that is located on a remote server is called from `sqlcmd` on a local computer and the file contains a drive file path such as :out c:\OutputFile.txt.</span></span> <span data-ttu-id="fb31c-668">将在本地计算机而不是远程服务器上创建输出文件。</span><span class="sxs-lookup"><span data-stu-id="fb31c-668">The output file will be created on the local computer and not on the remote server.</span></span>  
  
-   <span data-ttu-id="fb31c-669">有效文件路径包括： C： \\ **<*`filename`*>** 、 \\ \\<Server \> \\<Share $>\\ **<*`filename`*>** 和 "C:\Some Folder \\ **<*`file name`*>** "。</span><span class="sxs-lookup"><span data-stu-id="fb31c-669">Valid file paths include: C:\\**<*`filename`*>**, \\\\<Server\>\\<Share$>\\**<*`filename`*>** and "C:\Some Folder\\**<*`file name`*>**".</span></span> <span data-ttu-id="fb31c-670">如果路径中包含空格，请使用引号。</span><span class="sxs-lookup"><span data-stu-id="fb31c-670">If there is a space in the path, use quotation marks.</span></span>  
  
-   <span data-ttu-id="fb31c-671">每个新的 `sqlcmd` 会话都将覆盖现有的同名文件。</span><span class="sxs-lookup"><span data-stu-id="fb31c-671">Each new `sqlcmd` session will overwrite existing files that have the same names.</span></span>  
  
### <a name="informational-messages"></a><span data-ttu-id="fb31c-672">信息性消息</span><span class="sxs-lookup"><span data-stu-id="fb31c-672">Informational Messages</span></span>  
 <span data-ttu-id="fb31c-673">`sqlcmd` 将输出由服务器发送的所有信息性消息。</span><span class="sxs-lookup"><span data-stu-id="fb31c-673">`sqlcmd` prints any informational message that are sent by the server.</span></span> <span data-ttu-id="fb31c-674">在以下示例中，执行 [!INCLUDE[tsql](../includes/tsql-md.md)] 语句后会输出信息性消息。</span><span class="sxs-lookup"><span data-stu-id="fb31c-674">In the following example, after the [!INCLUDE[tsql](../includes/tsql-md.md)] statements are executed, an informational message is printed.</span></span>  
  
 <span data-ttu-id="fb31c-675">在命令提示符处，键入以下内容：</span><span class="sxs-lookup"><span data-stu-id="fb31c-675">At the command prompt, type the following:</span></span>  
  
 `sqlcmd`  
  
 `At the sqlcmd prompt type:`  
  
 `USE AdventureWorks2012;`  
  
 `GO`  
  
 <span data-ttu-id="fb31c-676">按 ENTER 后，会输出以下信息性消息：“已将数据库上下文更改为 "AdventureWorks2012"。”</span><span class="sxs-lookup"><span data-stu-id="fb31c-676">When you press ENTER, the following informational message is printed: "Changed database context to 'AdventureWorks2012'."</span></span>  
  
### <a name="output-format-from-transact-sql-queries"></a><span data-ttu-id="fb31c-677">Transact-SQL 查询的输出格式</span><span class="sxs-lookup"><span data-stu-id="fb31c-677">Output Format from Transact-SQL Queries</span></span>  
 <span data-ttu-id="fb31c-678">`sqlcmd` 首先输出列标题，其中包含在选择列表中指定的列名。</span><span class="sxs-lookup"><span data-stu-id="fb31c-678">`sqlcmd` first prints a column header that contains the column names specified in the select list.</span></span> <span data-ttu-id="fb31c-679">列名使用 SQLCMDCOLSEP 字符分隔。</span><span class="sxs-lookup"><span data-stu-id="fb31c-679">The column names are separated by using the SQLCMDCOLSEP character.</span></span> <span data-ttu-id="fb31c-680">默认情况下，将使用空格。</span><span class="sxs-lookup"><span data-stu-id="fb31c-680">By default, this is a space.</span></span> <span data-ttu-id="fb31c-681">如果列名短于列宽，则使用空格填充输出，直到下一列。</span><span class="sxs-lookup"><span data-stu-id="fb31c-681">If the column name is shorter than the column width, the output is padded with spaces up to the next column.</span></span>  
  
 <span data-ttu-id="fb31c-682">此行将跟随一行分隔行，分隔行是一系列的破折号字符。</span><span class="sxs-lookup"><span data-stu-id="fb31c-682">This line will be followed by a separator line that is a series of dash characters.</span></span> <span data-ttu-id="fb31c-683">以下输出显示了一个示例。</span><span class="sxs-lookup"><span data-stu-id="fb31c-683">The following output shows an example.</span></span>  
  
 <span data-ttu-id="fb31c-684">启动 `sqlcmd`。</span><span class="sxs-lookup"><span data-stu-id="fb31c-684">Start `sqlcmd`.</span></span> <span data-ttu-id="fb31c-685">在 `sqlcmd` 命令提示符下键入以下内容：</span><span class="sxs-lookup"><span data-stu-id="fb31c-685">At the `sqlcmd` command prompt, type the following:</span></span>  
  
 `USE AdventureWorks2012;`  
  
 `SELECT TOP (2) BusinessEntityID, FirstName, LastName`  
  
 `FROM Person.Person;`  
  
 `GO`  
  
 <span data-ttu-id="fb31c-686">当你按下 Enter 后，系统便会返回以下结果集。</span><span class="sxs-lookup"><span data-stu-id="fb31c-686">When you press ENTER, the following result set is returned.</span></span>  
  
 `BusinessEntityID FirstName    LastName`  
  
 `---------------- ------------ ----------`  
  
 `285              Syed         Abbas`  
  
 `293              Catherine    Abel`  
  
 `(2 row(s) affected)`  
  
 <span data-ttu-id="fb31c-687">虽然 `BusinessEntityID` 列只有 4 个字符宽，但已将其扩展以适应更长的列名。</span><span class="sxs-lookup"><span data-stu-id="fb31c-687">Although the `BusinessEntityID` column is only 4 characters wide, it has been expanded to accommodate the longer column name.</span></span> <span data-ttu-id="fb31c-688">默认情况下，输出会在 80 个字符处终止。</span><span class="sxs-lookup"><span data-stu-id="fb31c-688">By default, output is terminated at 80 characters.</span></span> <span data-ttu-id="fb31c-689">可通过使用 **-w** 选项或设置 SQLCMDCOLWIDTH 脚本变量来进行更改。</span><span class="sxs-lookup"><span data-stu-id="fb31c-689">This can be changed by using the **-w** option, or by setting the SQLCMDCOLWIDTH scripting variable.</span></span>  
  
### <a name="xml-output-format"></a><span data-ttu-id="fb31c-690">XML 输出格式</span><span class="sxs-lookup"><span data-stu-id="fb31c-690">XML Output Format</span></span>  
 <span data-ttu-id="fb31c-691">从 FOR XML 子句得到的 XML 输出是在连续流中的未格式化的输出。</span><span class="sxs-lookup"><span data-stu-id="fb31c-691">XML output that is the result of a FOR XML clause is output, unformatted, in a continuous stream.</span></span>  
  
 <span data-ttu-id="fb31c-692">若要得到 XML 输出，请使用以下命令： `:XML ON`。</span><span class="sxs-lookup"><span data-stu-id="fb31c-692">When you expect XML output, use the following command: `:XML ON`.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fb31c-693">`sqlcmd` 将采用常见的格式返回错误消息。</span><span class="sxs-lookup"><span data-stu-id="fb31c-693">`sqlcmd` returns error messages in the usual format.</span></span> <span data-ttu-id="fb31c-694">请注意，XML 文本流中的错误消息还将采用 XML 格式输出。</span><span class="sxs-lookup"><span data-stu-id="fb31c-694">Notice that the error messages are also output in the XML text stream in XML format.</span></span> <span data-ttu-id="fb31c-695">如果使用 `:XML ON`，则 `sqlcmd` 不显示信息性消息。</span><span class="sxs-lookup"><span data-stu-id="fb31c-695">By using `:XML ON`, `sqlcmd` does not display informational messages.</span></span>  
  
 <span data-ttu-id="fb31c-696">若要关闭 XML 模式，请使用以下命令： `:XML OFF`。</span><span class="sxs-lookup"><span data-stu-id="fb31c-696">To set the XML mode off, use the following command: `:XML OFF`.</span></span>  
  
 <span data-ttu-id="fb31c-697">发出 XML OFF 命令之前不应显示 GO 命令，因为 XML OFF 命令会将 `sqlcmd` 切换回面向行的输出。</span><span class="sxs-lookup"><span data-stu-id="fb31c-697">The GO command should not appear before the XML OFF command is issued because the XML OFF command switches `sqlcmd` back to row-oriented output.</span></span>  
  
 <span data-ttu-id="fb31c-698">XML（流形式）数据和行集数据不能混合。</span><span class="sxs-lookup"><span data-stu-id="fb31c-698">XML (streamed) data and rowset data cannot be mixed.</span></span> <span data-ttu-id="fb31c-699">如果在执行输出 XML 流的 [!INCLUDE[tsql](../includes/tsql-md.md)] 语句之前未发出 XML ON 命令，则输出将为乱码。</span><span class="sxs-lookup"><span data-stu-id="fb31c-699">If the XML ON command has not been issued before a [!INCLUDE[tsql](../includes/tsql-md.md)] statement that outputs XML streams is executed, the output will be garbled.</span></span> <span data-ttu-id="fb31c-700">如果已发出 XML ON 指令，则无法执行输出常规行集的 [!INCLUDE[tsql](../includes/tsql-md.md)] 语句。</span><span class="sxs-lookup"><span data-stu-id="fb31c-700">If the XML ON command has been issued, you cannot execute [!INCLUDE[tsql](../includes/tsql-md.md)] statements that output regular row sets.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fb31c-701">**:XML** 命令不支持 SET STATISTICS XML 语句。</span><span class="sxs-lookup"><span data-stu-id="fb31c-701">The **:XML** command does not support the SET STATISTICS XML statement.</span></span>  
  
## <a name="sqlcmd-best-practices"></a><span data-ttu-id="fb31c-702">sqlcmd 最佳方法</span><span class="sxs-lookup"><span data-stu-id="fb31c-702">sqlcmd Best Practices</span></span>  
 <span data-ttu-id="fb31c-703">使用以下方法来帮助实现最高的安全性和效率。</span><span class="sxs-lookup"><span data-stu-id="fb31c-703">Use the following practices to help maximize security and efficiency.</span></span>  
  
-   <span data-ttu-id="fb31c-704">使用集成安全性。</span><span class="sxs-lookup"><span data-stu-id="fb31c-704">Use integrated security.</span></span>  
  
-   <span data-ttu-id="fb31c-705">在自动化环境中使用 `-X`。</span><span class="sxs-lookup"><span data-stu-id="fb31c-705">Use `-X` in automated environments.</span></span>  
  
-   <span data-ttu-id="fb31c-706">使用适当的 NTFS 文件系统权限保护输入文件和输出文件。</span><span class="sxs-lookup"><span data-stu-id="fb31c-706">Secure input and output files by using appropriate NTFS file system permissions.</span></span>  
  
-   <span data-ttu-id="fb31c-707">若要提高性能，请在一个 `sqlcmd` 会话中执行尽可能多的操作，而不是在一系列会话中来执行这些操作。</span><span class="sxs-lookup"><span data-stu-id="fb31c-707">To increase performance, do as much in one `sqlcmd` session as you can, instead of in a series of sessions.</span></span>  
  
-   <span data-ttu-id="fb31c-708">将批处理或查询执行的超时值设置为大于您所预期的值。</span><span class="sxs-lookup"><span data-stu-id="fb31c-708">Set time-out values for batch or query execution higher than you expect it will take to execute the batch or query.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb31c-709">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fb31c-709">See Also</span></span>  
 <span data-ttu-id="fb31c-710">[启动 sqlcmd 实用工具](../relational-databases/scripting/sqlcmd-start-the-utility.md) </span><span class="sxs-lookup"><span data-stu-id="fb31c-710">[Start the sqlcmd Utility](../relational-databases/scripting/sqlcmd-start-the-utility.md) </span></span>  
 <span data-ttu-id="fb31c-711">[使用 sqlcmd 运行 Transact-SQL 脚本文件](../relational-databases/scripting/sqlcmd-run-transact-sql-script-files.md) </span><span class="sxs-lookup"><span data-stu-id="fb31c-711">[Run Transact-SQL Script Files Using sqlcmd](../relational-databases/scripting/sqlcmd-run-transact-sql-script-files.md) </span></span>  
 <span data-ttu-id="fb31c-712">[使用 sqlcmd 实用工具](../relational-databases/scripting/sqlcmd-use-the-utility.md) </span><span class="sxs-lookup"><span data-stu-id="fb31c-712">[Use the sqlcmd Utility](../relational-databases/scripting/sqlcmd-use-the-utility.md) </span></span>  
 <span data-ttu-id="fb31c-713">[将 sqlcmd 与脚本变量结合使用](../relational-databases/scripting/sqlcmd-use-with-scripting-variables.md) </span><span class="sxs-lookup"><span data-stu-id="fb31c-713">[Use sqlcmd with Scripting Variables](../relational-databases/scripting/sqlcmd-use-with-scripting-variables.md) </span></span>  
 <span data-ttu-id="fb31c-714">[使用 sqlcmd 连接到数据库引擎](../relational-databases/scripting/sqlcmd-connect-to-the-database-engine.md) </span><span class="sxs-lookup"><span data-stu-id="fb31c-714">[Connect to the Database Engine With sqlcmd](../relational-databases/scripting/sqlcmd-connect-to-the-database-engine.md) </span></span>  
 <span data-ttu-id="fb31c-715">[使用查询编辑器编辑 SQLCMD 脚本](../relational-databases/scripting/edit-sqlcmd-scripts-with-query-editor.md) </span><span class="sxs-lookup"><span data-stu-id="fb31c-715">[Edit SQLCMD Scripts with Query Editor](../relational-databases/scripting/edit-sqlcmd-scripts-with-query-editor.md) </span></span>  
 <span data-ttu-id="fb31c-716">[管理作业步骤](../ssms/agent/manage-job-steps.md) </span><span class="sxs-lookup"><span data-stu-id="fb31c-716">[Manage Job Steps](../ssms/agent/manage-job-steps.md) </span></span>  
 [<span data-ttu-id="fb31c-717">创建 CmdExec 作业步骤</span><span class="sxs-lookup"><span data-stu-id="fb31c-717">Create a CmdExec Job Step</span></span>](../ssms/agent/create-a-cmdexec-job-step.md)  
  
  
