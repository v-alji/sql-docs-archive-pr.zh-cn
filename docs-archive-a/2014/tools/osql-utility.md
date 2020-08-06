---
title: osql 实用工具 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- statements [SQL Server], command prompt
- QUIT command
- Transact-SQL statements, command prompt
- EXIT command
- operating systems [SQL Server], commands
- osql utility [SQL Server]
- stored procedures [SQL Server], command prompt
- scripts [SQL Server], command prompt
- RESET command
- GO command
- command prompt utilities [SQL Server], osql
- CTRL+C command
ms.assetid: cf530d9e-0609-4528-8975-ab8e08e40b9a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 95782afe0de8567781316e3478d04a090f968ed5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682518"
---
# <a name="osql-utility"></a><span data-ttu-id="a5227-102">osql 实用工具</span><span class="sxs-lookup"><span data-stu-id="a5227-102">osql Utility</span></span>
  <span data-ttu-id="a5227-103">使用 **osql** 实用工具可以输入 [!INCLUDE[tsql](../includes/tsql-md.md)] 语句、系统过程和脚本文件。</span><span class="sxs-lookup"><span data-stu-id="a5227-103">The **osql** utility allows you to enter [!INCLUDE[tsql](../includes/tsql-md.md)] statements, system procedures, and script files.</span></span> <span data-ttu-id="a5227-104">此实用工具通过 ODBC 与服务器通信。</span><span class="sxs-lookup"><span data-stu-id="a5227-104">This utility uses ODBC to communicate with the server.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="a5227-105">在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]的未来版本中将删除此功能。</span><span class="sxs-lookup"><span data-stu-id="a5227-105">This feature will be removed in a future version of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="a5227-106">请避免在新的开发工作中使用此功能，并计划修改当前使用此功能的应用程序。</span><span class="sxs-lookup"><span data-stu-id="a5227-106">Avoid using this feature in new development work, and plan to modify applications that currently use the feature.</span></span> <span data-ttu-id="a5227-107">改用 **sqlcmd** 。</span><span class="sxs-lookup"><span data-stu-id="a5227-107">Use **sqlcmd** instead.</span></span> <span data-ttu-id="a5227-108">有关详细信息，请参阅 [sqlcmd Utility](sqlcmd-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="a5227-108">For more information, see [sqlcmd Utility](sqlcmd-utility.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5227-109">语法</span><span class="sxs-lookup"><span data-stu-id="a5227-109">Syntax</span></span>  
  
```  
  
      osql  
[-?] |  
[-L] |  
[  
  {  
     {-Ulogin_id [-Ppassword]} | -E }  
     [-Sserver_name[\instance_name]] [-Hwksta_name] [-ddb_name]  
     [-ltime_out] [-ttime_out] [-hheaders]  
     [-scol_separator] [-wcolumn_width] [-apacket_size]  
     [-e] [-I] [-D data_source_name]  
     [-ccmd_end] [-q "query"] [-Q"query"]  
     [-n] [-merror_level] [-r {0 | 1}]  
     [-iinput_file] [-ooutput_file] [-p]  
     [-b] [-u] [-R] [-O]  
]  
```  
  
## <a name="arguments"></a><span data-ttu-id="a5227-110">参数</span><span class="sxs-lookup"><span data-stu-id="a5227-110">Arguments</span></span>  
 <span data-ttu-id="a5227-111">**-?**</span><span class="sxs-lookup"><span data-stu-id="a5227-111">**-?**</span></span>  
 <span data-ttu-id="a5227-112">显示 **osql** 开关的语法摘要。</span><span class="sxs-lookup"><span data-stu-id="a5227-112">Displays the syntax summary of **osql** switches.</span></span>  
  
 <span data-ttu-id="a5227-113">**-L**</span><span class="sxs-lookup"><span data-stu-id="a5227-113">**-L**</span></span>  
 <span data-ttu-id="a5227-114">列出在本地配置的服务器和在网络上广播的服务器的名称。</span><span class="sxs-lookup"><span data-stu-id="a5227-114">Lists the locally configured servers and the names of the servers broadcasting on the network.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a5227-115">鉴于网络上广播的特点， **osql** 可能不会及时接收来自所有服务器的响应。</span><span class="sxs-lookup"><span data-stu-id="a5227-115">Due to the nature of broadcasting on networks, **osql** may not receive a timely response from all servers.</span></span> <span data-ttu-id="a5227-116">因此，每次调用该选项所返回的服务器列表都可能不同。</span><span class="sxs-lookup"><span data-stu-id="a5227-116">Therefore the list of servers returned may vary for each invocation of this option.</span></span>  
  
 <span data-ttu-id="a5227-117">**-U** _login_id_</span><span class="sxs-lookup"><span data-stu-id="a5227-117">**-U** _login_id_</span></span>  
 <span data-ttu-id="a5227-118">用户登录 ID。</span><span class="sxs-lookup"><span data-stu-id="a5227-118">Is the user login ID.</span></span> <span data-ttu-id="a5227-119">登录 ID 区分大小写。</span><span class="sxs-lookup"><span data-stu-id="a5227-119">Login IDs are case-sensitive.</span></span>  
  
 <span data-ttu-id="a5227-120">**-P** _password_</span><span class="sxs-lookup"><span data-stu-id="a5227-120">**-P** _password_</span></span>  
 <span data-ttu-id="a5227-121">用户指定的密码。</span><span class="sxs-lookup"><span data-stu-id="a5227-121">Is a user-specified password.</span></span> <span data-ttu-id="a5227-122">如果未使用 **-P** 选项， **osql** 将提示输入密码。</span><span class="sxs-lookup"><span data-stu-id="a5227-122">If the **-P** option is not used, **osql** prompts for a password.</span></span> <span data-ttu-id="a5227-123">如果在命令提示符的末尾使用 **-P** 选项而不提供密码， **osql** 将使用默认密码 (NULL)。</span><span class="sxs-lookup"><span data-stu-id="a5227-123">If the **-P** option is used at the end of the command prompt without any password, **osql** uses the default password (NULL).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="a5227-124">不要使用空密码。</span><span class="sxs-lookup"><span data-stu-id="a5227-124">Do not use a blank password.</span></span> <span data-ttu-id="a5227-125">请使用强密码。</span><span class="sxs-lookup"><span data-stu-id="a5227-125">Use a strong password.</span></span> <span data-ttu-id="a5227-126">有关详细信息，请参阅 [Strong Passwords](../relational-databases/security/strong-passwords.md)。</span><span class="sxs-lookup"><span data-stu-id="a5227-126">For more information, see [Strong Passwords](../relational-databases/security/strong-passwords.md).</span></span>  
  
 <span data-ttu-id="a5227-127">密码是区分大小写的。</span><span class="sxs-lookup"><span data-stu-id="a5227-127">Passwords are case-sensitive.</span></span>  
  
 <span data-ttu-id="a5227-128">使用 OSQLPASSWORD 环境变量，可以为当前会话设置默认密码。</span><span class="sxs-lookup"><span data-stu-id="a5227-128">The OSQLPASSWORD environment variable allows you to set a default password for the current session.</span></span> <span data-ttu-id="a5227-129">因此，不需要通过硬编码在批处理文件中设置密码。</span><span class="sxs-lookup"><span data-stu-id="a5227-129">Therefore, you do not have to hard code a password into batch files.</span></span>  
  
 <span data-ttu-id="a5227-130">如果不使用 **-P** 选项指定密码， **osql** 将首先检查 OSQLPASSWORD 变量。</span><span class="sxs-lookup"><span data-stu-id="a5227-130">If you do not specify a password with the **-P** option, **osql** first checks for the OSQLPASSWORD variable.</span></span> <span data-ttu-id="a5227-131">如果未设置任何值，则 **osql** 将使用默认密码 (NULL)。</span><span class="sxs-lookup"><span data-stu-id="a5227-131">If no value is set, **osql** uses the default password, NULL.</span></span> <span data-ttu-id="a5227-132">以下示例将在命令提示符中设置 OSQLPASSWORD 变量，然后访问 **osql** 实用工具：</span><span class="sxs-lookup"><span data-stu-id="a5227-132">The following example sets the OSQLPASSWORD variable at a command prompt and then accesses the **osql** utility:</span></span>  
  
```  
C:\>SET OSQLPASSWORD=abracadabra  
C:\>osql   
```  
  
> [!IMPORTANT]  
>  <span data-ttu-id="a5227-133">若要屏蔽密码，请不要指定 **-P** 选项和 **-U** 选项。</span><span class="sxs-lookup"><span data-stu-id="a5227-133">To mask your password, do not specify the **-P** option along with the **-U** option.</span></span> <span data-ttu-id="a5227-134">相反，应在指定 **osql** 和 **-U** 选项以及其他开关（不指定 **-P**）之后，按“Enter”键，此时 **osql** 将提示你输入密码。</span><span class="sxs-lookup"><span data-stu-id="a5227-134">Instead, after specifying **osql** along with the **-U** option and other switches (do not specify **-P**), press ENTER, and **osql** will prompt you for a password.</span></span> <span data-ttu-id="a5227-135">这种方法可以确保输入密码时对其屏蔽。</span><span class="sxs-lookup"><span data-stu-id="a5227-135">This method ensures that your password will be masked when it is entered.</span></span>  
  
 <span data-ttu-id="a5227-136">**-E**</span><span class="sxs-lookup"><span data-stu-id="a5227-136">**-E**</span></span>  
 <span data-ttu-id="a5227-137">使用可信连接而不请求密码。</span><span class="sxs-lookup"><span data-stu-id="a5227-137">Uses a trusted connection instead of requesting a password.</span></span>  
  
 <span data-ttu-id="a5227-138">**-S** _server_name_[ **\\** _instance_name_]</span><span class="sxs-lookup"><span data-stu-id="a5227-138">**-S** _server_name_[ **\\**_instance_name_]</span></span>  
 <span data-ttu-id="a5227-139">指定要连接到的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="a5227-139">Specifies the instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to connect to.</span></span> <span data-ttu-id="a5227-140">指定要连接到该服务器上 *默认实例的* server_name [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="a5227-140">Specify *server_name* to connect to the default instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] on that server.</span></span> <span data-ttu-id="a5227-141">指定_server_name_ **\\** 要连接到该服务器上的命名实例 server_name_instance_name_ [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="a5227-141">Specify _server_name_**\\**_instance_name_ to connect to a named instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] on that server.</span></span> <span data-ttu-id="a5227-142">如果未指定服务器， **osql** 将连接到本地计算机上的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 默认实例。</span><span class="sxs-lookup"><span data-stu-id="a5227-142">If no server is specified, **osql** connects to the default instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] on the local computer.</span></span> <span data-ttu-id="a5227-143">从网络上的远程计算机执行 **osql** 时，此选项是必需的。</span><span class="sxs-lookup"><span data-stu-id="a5227-143">This option is required when executing **osql** from a remote computer on the network.</span></span>  
  
 <span data-ttu-id="a5227-144">**-H** _wksta_name_</span><span class="sxs-lookup"><span data-stu-id="a5227-144">**-H** _wksta_name_</span></span>  
 <span data-ttu-id="a5227-145">工作站的名称。</span><span class="sxs-lookup"><span data-stu-id="a5227-145">Is a workstation name.</span></span> <span data-ttu-id="a5227-146">工作站名称存储在 **sysprocesses.hostname** 中，并由 **sp_who**显示。</span><span class="sxs-lookup"><span data-stu-id="a5227-146">The workstation name is stored in **sysprocesses.hostname** and is displayed by **sp_who**.</span></span> <span data-ttu-id="a5227-147">如果不指定此选项，则采用当前计算机名称。</span><span class="sxs-lookup"><span data-stu-id="a5227-147">If this option is not specified, the current computer name is assumed.</span></span>  
  
 <span data-ttu-id="a5227-148">**-d** _db_name_</span><span class="sxs-lookup"><span data-stu-id="a5227-148">**-d** _db_name_</span></span>  
 <span data-ttu-id="a5227-149">启动 *osql* 时发出一个 USE **db_name**语句。</span><span class="sxs-lookup"><span data-stu-id="a5227-149">Issues a USE *db_name* statement when **osql**is started.</span></span>  
  
 <span data-ttu-id="a5227-150">**-l** _time_out_</span><span class="sxs-lookup"><span data-stu-id="a5227-150">**-l** _time_out_</span></span>  
 <span data-ttu-id="a5227-151">指定 **osql** 登录超时之前的秒数。登录到 **osql** 的默认超时时间为 8 秒。</span><span class="sxs-lookup"><span data-stu-id="a5227-151">Specifies the number of seconds before an **osql** login times out. The default time-out for login to **osql** is eight seconds.</span></span>  
  
 <span data-ttu-id="a5227-152">**-t** _time_out_</span><span class="sxs-lookup"><span data-stu-id="a5227-152">**-t** _time_out_</span></span>  
 <span data-ttu-id="a5227-153">指定命令超时之前的秒数。如果未指定 *time_out* 值，则命令将不会超时。</span><span class="sxs-lookup"><span data-stu-id="a5227-153">Specifies the number of seconds before a command times out. If a *time_out* value is not specified, commands do not time out.</span></span>  
  
 <span data-ttu-id="a5227-154">**-h** _headers_</span><span class="sxs-lookup"><span data-stu-id="a5227-154">**-h** _headers_</span></span>  
 <span data-ttu-id="a5227-155">指定要在列标题之间打印的行数。</span><span class="sxs-lookup"><span data-stu-id="a5227-155">Specifies the number of rows to print between column headings.</span></span> <span data-ttu-id="a5227-156">默认为每一组查询结果输出一次标题。</span><span class="sxs-lookup"><span data-stu-id="a5227-156">The default is to print headings one time for each set of query results.</span></span> <span data-ttu-id="a5227-157">使用 -1 可指定不打印标题。</span><span class="sxs-lookup"><span data-stu-id="a5227-157">Use -1 to specify that no headers will be printed.</span></span> <span data-ttu-id="a5227-158">如果使用的是 -1，参数和设置之间就不得有空格（可以是 -h-1，但不能是 -h -1）。</span><span class="sxs-lookup"><span data-stu-id="a5227-158">If -1 is used, there must be no space between the parameter and the setting (**-h-1**, not **-h -1**).</span></span>  
  
 <span data-ttu-id="a5227-159">**-s** _col_separator_</span><span class="sxs-lookup"><span data-stu-id="a5227-159">**-s** _col_separator_</span></span>  
 <span data-ttu-id="a5227-160">指定列分隔符字符，默认值为空格。</span><span class="sxs-lookup"><span data-stu-id="a5227-160">Specifies the column-separator character, which is a blank space by default.</span></span> <span data-ttu-id="a5227-161">若要使用对操作系统具有特殊意义的字符 (例如，|;& \< >) 中，用双引号将该字符括起来 ( ") 。</span><span class="sxs-lookup"><span data-stu-id="a5227-161">To use characters that have special meaning to the operating system (for example, | ; & \< >), enclose the character in double quotation marks (").</span></span>  
  
 <span data-ttu-id="a5227-162">**-w** _column_width_</span><span class="sxs-lookup"><span data-stu-id="a5227-162">**-w** _column_width_</span></span>  
 <span data-ttu-id="a5227-163">允许用户设置屏幕输出的宽度。</span><span class="sxs-lookup"><span data-stu-id="a5227-163">Allows the user to set the screen width for output.</span></span> <span data-ttu-id="a5227-164">默认为 80 个字符。</span><span class="sxs-lookup"><span data-stu-id="a5227-164">The default is 80 characters.</span></span> <span data-ttu-id="a5227-165">当输出行达到其最大屏幕宽度时，会拆分为多行。</span><span class="sxs-lookup"><span data-stu-id="a5227-165">When an output line has reached its maximum screen width, it is broken into multiple lines.</span></span>  
  
 <span data-ttu-id="a5227-166">**-a** _packet_size_</span><span class="sxs-lookup"><span data-stu-id="a5227-166">**-a** _packet_size_</span></span>  
 <span data-ttu-id="a5227-167">允许您请求不同大小的数据包。</span><span class="sxs-lookup"><span data-stu-id="a5227-167">Allows you to request a different-sized packet.</span></span> <span data-ttu-id="a5227-168">*packet_size* 的有效值介于 512 和 65535 之间。</span><span class="sxs-lookup"><span data-stu-id="a5227-168">The valid values for *packet_size* are 512 through 65535.</span></span> <span data-ttu-id="a5227-169">默认值 **osql** 是服务器默认值。</span><span class="sxs-lookup"><span data-stu-id="a5227-169">The default value **osql** is the server default.</span></span> <span data-ttu-id="a5227-170">执行较大的脚本时，各个 GO 命令之间的 SQL 语句的数量是庞大的，因此增大数据包可以提高性能。</span><span class="sxs-lookup"><span data-stu-id="a5227-170">Increased packet size can enhance performance on larger script execution where the amount of SQL statements between GO commands is substantial.</span></span> [!INCLUDE[msCoName](../includes/msconame-md.md)] <span data-ttu-id="a5227-171">的测试表明大容量复制操作的最快设置通常为 8192。</span><span class="sxs-lookup"><span data-stu-id="a5227-171">testing indicates that 8192 is typically the fastest setting for bulk copy operations.</span></span> <span data-ttu-id="a5227-172">可以请求更大的数据包，但如果请求不能得到批准，则 **osql** 会将此值默认为服务器的默认值。</span><span class="sxs-lookup"><span data-stu-id="a5227-172">A larger packet size can be requested, but **osql** defaults to the server default if the request cannot be granted.</span></span>  
  
 <span data-ttu-id="a5227-173">**-e**</span><span class="sxs-lookup"><span data-stu-id="a5227-173">**-e**</span></span>  
 <span data-ttu-id="a5227-174">回显输入。</span><span class="sxs-lookup"><span data-stu-id="a5227-174">Echoes input.</span></span>  
  
 <span data-ttu-id="a5227-175">**-I**</span><span class="sxs-lookup"><span data-stu-id="a5227-175">**-I**</span></span>  
 <span data-ttu-id="a5227-176">将 QUOTED_IDENTIFIER 连接选项设置为开启。</span><span class="sxs-lookup"><span data-stu-id="a5227-176">Sets the QUOTED_IDENTIFIER connection option on.</span></span>  
  
 <span data-ttu-id="a5227-177">**-D** _data_source_name_</span><span class="sxs-lookup"><span data-stu-id="a5227-177">**-D** _data_source_name_</span></span>  
 <span data-ttu-id="a5227-178">连接到某个通过用于 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]的 ODBC 驱动程序定义的 ODBC 数据源。</span><span class="sxs-lookup"><span data-stu-id="a5227-178">Connects to an ODBC data source that is defined using the ODBC driver for [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="a5227-179">**osql** 连接使用该数据源中指定的选项。</span><span class="sxs-lookup"><span data-stu-id="a5227-179">The **osql** connection uses the options specified in the data source.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a5227-180">此选项不适用于为其他驱动程序定义的数据源。</span><span class="sxs-lookup"><span data-stu-id="a5227-180">This option does not work with data sources defined for other drivers.</span></span>  
  
 <span data-ttu-id="a5227-181">**-c** _cmd_end_</span><span class="sxs-lookup"><span data-stu-id="a5227-181">**-c** _cmd_end_</span></span>  
 <span data-ttu-id="a5227-182">指定命令终止符。</span><span class="sxs-lookup"><span data-stu-id="a5227-182">Specifies the command terminator.</span></span> <span data-ttu-id="a5227-183">默认情况下，可以在行中输入一个单独的 GO 来终止命令，并将该命令发送到 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="a5227-183">By default, commands are terminated and sent to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] by entering GO on a line by itself.</span></span> <span data-ttu-id="a5227-184">如果要重置命令终止符，请勿使用对操作系统有特殊含义的 [!INCLUDE[tsql](../includes/tsql-md.md)] 保留字或字符，无论其前面是否有反斜杠。</span><span class="sxs-lookup"><span data-stu-id="a5227-184">When you reset the command terminator, do not use [!INCLUDE[tsql](../includes/tsql-md.md)] reserved words or characters that have special meaning to the operating system, whether preceded by a backslash or not.</span></span>  
  
 <span data-ttu-id="a5227-185">**-q "** _query_ **"**</span><span class="sxs-lookup"><span data-stu-id="a5227-185">**-q "** _query_ **"**</span></span>  
 <span data-ttu-id="a5227-186">启动 **osql** 时执行查询，但在查询完成时不退出 **osql** 。</span><span class="sxs-lookup"><span data-stu-id="a5227-186">Executes a query when **osql** starts, but does not exit **osql** when the query completes.</span></span> <span data-ttu-id="a5227-187">（注意查询语句不应包含 GO）。</span><span class="sxs-lookup"><span data-stu-id="a5227-187">(Note that the query statement should not include GO).</span></span> <span data-ttu-id="a5227-188">如果从批处理文件中发出查询，请使用 %variables 或环境 %variables%。</span><span class="sxs-lookup"><span data-stu-id="a5227-188">If you issue a query from a batch file, use %variables, or environment %variables%.</span></span> <span data-ttu-id="a5227-189">例如：</span><span class="sxs-lookup"><span data-stu-id="a5227-189">For example:</span></span>  
  
```  
SET table=sys.objects  
osql -E -q "select name, object_id from %table%"  
```  
  
 <span data-ttu-id="a5227-190">将查询用双引号括起来，将查询中嵌入的任何内容用单引号括起来。</span><span class="sxs-lookup"><span data-stu-id="a5227-190">Use double quotation marks around the query and single quotation marks around anything embedded in the query.</span></span>  
  
 <span data-ttu-id="a5227-191">**-Q"** _query_ **"**</span><span class="sxs-lookup"><span data-stu-id="a5227-191">**-Q"** _query_ **"**</span></span>  
 <span data-ttu-id="a5227-192">执行查询并立即退出 **osql**。</span><span class="sxs-lookup"><span data-stu-id="a5227-192">Executes a query and immediately exits **osql**.</span></span> <span data-ttu-id="a5227-193">将查询用双引号括起来，将查询中嵌入的任何内容用单引号括起来。</span><span class="sxs-lookup"><span data-stu-id="a5227-193">Use double quotation marks around the query and single quotation marks around anything embedded in the query.</span></span>  
  
 <span data-ttu-id="a5227-194">**-n**</span><span class="sxs-lookup"><span data-stu-id="a5227-194">**-n**</span></span>  
 <span data-ttu-id="a5227-195">从输入行中删除编号和提示符号 (>)。</span><span class="sxs-lookup"><span data-stu-id="a5227-195">Removes numbering and the prompt symbol (>) from input lines.</span></span>  
  
 <span data-ttu-id="a5227-196">**-m** _error_level_</span><span class="sxs-lookup"><span data-stu-id="a5227-196">**-m** _error_level_</span></span>  
 <span data-ttu-id="a5227-197">自定义错误消息的显示。</span><span class="sxs-lookup"><span data-stu-id="a5227-197">Customizes the display of error messages.</span></span> <span data-ttu-id="a5227-198">显示指定的或更高严重级别的错误的消息数、状态和错误级别。</span><span class="sxs-lookup"><span data-stu-id="a5227-198">The message number, state, and error level are displayed for errors of the specified severity level or higher.</span></span> <span data-ttu-id="a5227-199">不显示低于指定级别的错误的信息。</span><span class="sxs-lookup"><span data-stu-id="a5227-199">Nothing is displayed for errors of levels lower than the specified level.</span></span> <span data-ttu-id="a5227-200">使用 **-1** 可以指定返回所有标题及其消息，即使是信息型消息。</span><span class="sxs-lookup"><span data-stu-id="a5227-200">Use **-1** to specify that all headers are returned with messages, even informational messages.</span></span> <span data-ttu-id="a5227-201">如果使用 **-1**，则在参数和设置之间不能有空格（可以是 **-m-1**，不能是 **-m -1**）。</span><span class="sxs-lookup"><span data-stu-id="a5227-201">If using **-1**, there must be no space between the parameter and the setting (**-m-1**, not **-m -1**).</span></span>  
  
 <span data-ttu-id="a5227-202">**-r** { **0**| **1**}</span><span class="sxs-lookup"><span data-stu-id="a5227-202">**-r** { **0**| **1**}</span></span>  
 <span data-ttu-id="a5227-203">将消息输出重定向到屏幕 (**stderr**)。</span><span class="sxs-lookup"><span data-stu-id="a5227-203">Redirects message output to the screen (**stderr**).</span></span> <span data-ttu-id="a5227-204">如果不指定参数，或指定参数为 **0**，则仅重定向严重级别为 11 或更高的错误信息。</span><span class="sxs-lookup"><span data-stu-id="a5227-204">If you do not specify a parameter, or if you specify **0**, only error messages with a severity level 11 or higher are redirected.</span></span> <span data-ttu-id="a5227-205">如果指定参数为 **1**，则将重定向所有的消息输出（包括“print”）。</span><span class="sxs-lookup"><span data-stu-id="a5227-205">If you specify **1**, all message output (including "print") is redirected.</span></span>  
  
 <span data-ttu-id="a5227-206">**-i** _input_file_</span><span class="sxs-lookup"><span data-stu-id="a5227-206">**-i** _input_file_</span></span>  
 <span data-ttu-id="a5227-207">标识包含一批 SQL 语句或存储过程的文件。</span><span class="sxs-lookup"><span data-stu-id="a5227-207">Identifies the file that contains a batch of SQL statements or stored procedures.</span></span> <span data-ttu-id="a5227-208">小于 ( **\<** ) 比较运算符可以代替 **-i**使用。</span><span class="sxs-lookup"><span data-stu-id="a5227-208">The less than (**\<**) comparison operator can be used in place of **-i**.</span></span>  
  
 <span data-ttu-id="a5227-209">**-o** _output_file_</span><span class="sxs-lookup"><span data-stu-id="a5227-209">**-o** _output_file_</span></span>  
 <span data-ttu-id="a5227-210">标识从 **osql**接收输出的文件。</span><span class="sxs-lookup"><span data-stu-id="a5227-210">Identifies the file that receives output from **osql**.</span></span> <span data-ttu-id="a5227-211">大于 ( **>** ) 比较运算符可以代替 **-o**使用。</span><span class="sxs-lookup"><span data-stu-id="a5227-211">The greater than (**>**) comparison operator can be used in place of **-o**.</span></span>  
  
 <span data-ttu-id="a5227-212">如果 *input_file* 不是 Unicode 并且未指定 **-u** ，则以 OEM 格式存储 *output_file* 。</span><span class="sxs-lookup"><span data-stu-id="a5227-212">If *input_file* is not Unicode and **-u** is not specified, *output_file* is stored in OEM format.</span></span> <span data-ttu-id="a5227-213">如果 *input_file* 是 Unicode 或指定了 **-u** ，则以 Unicode 格式存储 *output_file* 。</span><span class="sxs-lookup"><span data-stu-id="a5227-213">If *input_file* is Unicode or **-u** is specified, *output_file* is stored in Unicode format.</span></span>  
  
 <span data-ttu-id="a5227-214">**-p**</span><span class="sxs-lookup"><span data-stu-id="a5227-214">**-p**</span></span>  
 <span data-ttu-id="a5227-215">打印性能统计信息。</span><span class="sxs-lookup"><span data-stu-id="a5227-215">Prints performance statistics.</span></span>  
  
 <span data-ttu-id="a5227-216">**-b**</span><span class="sxs-lookup"><span data-stu-id="a5227-216">**-b**</span></span>  
 <span data-ttu-id="a5227-217">指定发生错误时， **osql** 退出并返回一个 DOS ERRORLEVEL 值。</span><span class="sxs-lookup"><span data-stu-id="a5227-217">Specifies that **osql** exits and returns a DOS ERRORLEVEL value when an error occurs.</span></span> <span data-ttu-id="a5227-218">当 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 错误消息的严重级别为 11 或更大值时，返回给 DOS ERRORLEVE 变量的值为 1；否则返回的值为 0。</span><span class="sxs-lookup"><span data-stu-id="a5227-218">The value returned to the DOS ERRORLEVEL variable is 1 when the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] error message has a severity of 11 or greater; otherwise, the value returned is 0.</span></span> [!INCLUDE[msCoName](../includes/msconame-md.md)] <span data-ttu-id="a5227-219">MS-DOS 批处理文件可以测试 DOS ERRORLEVEL 的值并正确地处理错误。</span><span class="sxs-lookup"><span data-stu-id="a5227-219">MS-DOS batch files can test the value of DOS ERRORLEVEL and handle the error appropriately.</span></span>  
  
 <span data-ttu-id="a5227-220">**-u**</span><span class="sxs-lookup"><span data-stu-id="a5227-220">**-u**</span></span>  
 <span data-ttu-id="a5227-221">指定无论 *input_file* 为何种格式，都以 Unicode 格式存储 *output_file*。</span><span class="sxs-lookup"><span data-stu-id="a5227-221">Specifies that *output_file* is stored in Unicode format, regardless of the format of the *input_file*.</span></span>  
  
 <span data-ttu-id="a5227-222">**-R**</span><span class="sxs-lookup"><span data-stu-id="a5227-222">**-R**</span></span>  
 <span data-ttu-id="a5227-223">指定在将货币、日期和时间数据转换为字符数据时， [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ODBC 驱动程序使用客户端设置。</span><span class="sxs-lookup"><span data-stu-id="a5227-223">Specifies that the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ODBC driver use client settings when converting currency, date, and time data to character data.</span></span>  
  
 <span data-ttu-id="a5227-224">**-O**</span><span class="sxs-lookup"><span data-stu-id="a5227-224">**-O**</span></span>  
 <span data-ttu-id="a5227-225">指定停用某些 **osql** 功能以便与 **isql**的早期版本的行为匹配。</span><span class="sxs-lookup"><span data-stu-id="a5227-225">Specifies that certain **osql** features be deactivated to match the behavior of earlier versions of **isql**.</span></span> <span data-ttu-id="a5227-226">下列功能停用：</span><span class="sxs-lookup"><span data-stu-id="a5227-226">These features are deactivated:</span></span>  
  
-   <span data-ttu-id="a5227-227">EOF 批处理</span><span class="sxs-lookup"><span data-stu-id="a5227-227">EOF batch processing</span></span>  
  
-   <span data-ttu-id="a5227-228">自动调整控制台宽度</span><span class="sxs-lookup"><span data-stu-id="a5227-228">Automatic console width scaling</span></span>  
  
-   <span data-ttu-id="a5227-229">宽消息</span><span class="sxs-lookup"><span data-stu-id="a5227-229">Wide messages</span></span>  
  
 <span data-ttu-id="a5227-230">同时还将 DOS ERRORLEVEL 的默认值设置为 -1。</span><span class="sxs-lookup"><span data-stu-id="a5227-230">It also sets the default DOS ERRORLEVEL value to -1.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a5227-231">**-n**、 **-O** 和 **-D** 选项不再受 **osql**支持。</span><span class="sxs-lookup"><span data-stu-id="a5227-231">The **-n**, **-O** and **-D** options are no longer supported by **osql**.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a5227-232">备注</span><span class="sxs-lookup"><span data-stu-id="a5227-232">Remarks</span></span>  
 <span data-ttu-id="a5227-233">**osql** 实用工具从操作系统直接启动，并且使用本文中列出的区分大小写的选项。</span><span class="sxs-lookup"><span data-stu-id="a5227-233">The **osql** utility is started directly from the operating system with the case-sensitive options listed here.</span></span> <span data-ttu-id="a5227-234">**osql**启动后将接受 SQL 语句，然后以交互方式将这些语句发送到 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="a5227-234">After **osql**starts, it accepts SQL statements and sends them to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] interactively.</span></span> <span data-ttu-id="a5227-235">结果被格式化并在屏幕 (**stdout**) 上显示。</span><span class="sxs-lookup"><span data-stu-id="a5227-235">The results are formatted and displayed on the screen (**stdout**).</span></span> <span data-ttu-id="a5227-236">可使用 QUIT 或 EXIT 退出 **osql**。</span><span class="sxs-lookup"><span data-stu-id="a5227-236">Use QUIT or EXIT to exit from **osql**.</span></span>  
  
 <span data-ttu-id="a5227-237">如果在启动**osql**时未指定用户名，则 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 将检查环境变量并使用这些变量，例如， \**osqluser = (*`user`*) **或**osqlserver = (*`server`\*) \*\*。</span><span class="sxs-lookup"><span data-stu-id="a5227-237">If you do not specify a user name when you start **osql**, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] checks for the environment variables and uses those, for example, **osqluser=(*`user`*)** or **osqlserver=(*`server`*)**.</span></span> <span data-ttu-id="a5227-238">如果未设置环境变量，则使用工作站用户名。</span><span class="sxs-lookup"><span data-stu-id="a5227-238">If no environment variables are set, the workstation user name is used.</span></span> <span data-ttu-id="a5227-239">如果未指定服务器，则使用工作站名称。</span><span class="sxs-lookup"><span data-stu-id="a5227-239">If you do not specify a server, the name of the workstation is used.</span></span>  
  
 <span data-ttu-id="a5227-240">如果 **-U** 或 **-P** 选项都没有使用，则 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 将尝试使用 [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows 身份验证模式进行连接。</span><span class="sxs-lookup"><span data-stu-id="a5227-240">If neither the **-U** or **-P** options are used, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] attempts to connect using [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows Authentication Mode.</span></span> <span data-ttu-id="a5227-241">身份验证根据运行 [!INCLUDE[msCoName](../includes/msconame-md.md)] osql **的用户的**Windows 帐户进行。</span><span class="sxs-lookup"><span data-stu-id="a5227-241">Authentication is based on the [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows account of the user running **osql**.</span></span>  
  
 <span data-ttu-id="a5227-242">**osql** 实用工具使用 ODBC API。</span><span class="sxs-lookup"><span data-stu-id="a5227-242">The **osql** utility uses the ODBC API.</span></span> <span data-ttu-id="a5227-243">对于 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ISO 连接选项，该实用工具使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ODBC 驱动程序的默认设置。</span><span class="sxs-lookup"><span data-stu-id="a5227-243">The utility uses the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ODBC driver default settings for the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ISO connection options.</span></span> <span data-ttu-id="a5227-244">有关详细信息，请参阅“ANSI 选项的效果”。</span><span class="sxs-lookup"><span data-stu-id="a5227-244">For more information, see Effects of ANSI Options.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a5227-245">**osql** 实用工具不支持 CLR 用户定义数据类型。</span><span class="sxs-lookup"><span data-stu-id="a5227-245">The **osql** utility does not support CLR user-defined data types.</span></span> <span data-ttu-id="a5227-246">若要处理这些数据类型，必须使用 **sqlcmd** 实用工具。</span><span class="sxs-lookup"><span data-stu-id="a5227-246">To process these data types, you must use the **sqlcmd** utility.</span></span> <span data-ttu-id="a5227-247">有关详细信息，请参阅 [sqlcmd Utility](sqlcmd-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="a5227-247">For more information, see [sqlcmd Utility](sqlcmd-utility.md).</span></span>  
  
## <a name="osql-commands"></a><span data-ttu-id="a5227-248">OSQL 命令</span><span class="sxs-lookup"><span data-stu-id="a5227-248">OSQL Commands</span></span>  
 <span data-ttu-id="a5227-249">除了 [!INCLUDE[tsql](../includes/tsql-md.md)] osql **中的**语句外，还可以使用以下命令。</span><span class="sxs-lookup"><span data-stu-id="a5227-249">In addition to [!INCLUDE[tsql](../includes/tsql-md.md)] statements within **osql**, these commands are also available.</span></span>  
  
|<span data-ttu-id="a5227-250">Command</span><span class="sxs-lookup"><span data-stu-id="a5227-250">Command</span></span>|<span data-ttu-id="a5227-251">说明</span><span class="sxs-lookup"><span data-stu-id="a5227-251">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a5227-252">GO</span><span class="sxs-lookup"><span data-stu-id="a5227-252">GO</span></span>|<span data-ttu-id="a5227-253">执行上一个 GO 命令之后输入的所有语句。</span><span class="sxs-lookup"><span data-stu-id="a5227-253">Executes all statements entered after the last GO.</span></span>|  
|<span data-ttu-id="a5227-254">RESET</span><span class="sxs-lookup"><span data-stu-id="a5227-254">RESET</span></span>|<span data-ttu-id="a5227-255">清除已输入的所有语句。</span><span class="sxs-lookup"><span data-stu-id="a5227-255">Clears any statements you have entered.</span></span>|  
|<span data-ttu-id="a5227-256">QUIT 或 EXIT( )</span><span class="sxs-lookup"><span data-stu-id="a5227-256">QUIT or EXIT( )</span></span>|<span data-ttu-id="a5227-257">退出 **osql**。</span><span class="sxs-lookup"><span data-stu-id="a5227-257">Exits from **osql**.</span></span>|  
|<span data-ttu-id="a5227-258">Ctrl+C</span><span class="sxs-lookup"><span data-stu-id="a5227-258">CTRL+C</span></span>|<span data-ttu-id="a5227-259">结束查询但不退出 **osql**。</span><span class="sxs-lookup"><span data-stu-id="a5227-259">Ends a query without exiting from **osql**.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="a5227-260">!!</span><span class="sxs-lookup"><span data-stu-id="a5227-260">The !!</span></span> <span data-ttu-id="a5227-261">和 ED 命令不再受 **osql**支持。</span><span class="sxs-lookup"><span data-stu-id="a5227-261">and ED commands are no longer supported by **osql**.</span></span>  
  
 <span data-ttu-id="a5227-262">仅当命令终止符 GO（默认）、RESET EXIT、QUIT 和 Ctrl+C 出现在一行的开始（紧跟 **osql** 提示符）时，才会被识别。</span><span class="sxs-lookup"><span data-stu-id="a5227-262">The command terminators GO (by default), RESET EXIT, QUIT, and CTRL+C, are recognized only if they appear at the beginning of a line, immediately following the **osql** prompt.</span></span>  
  
 <span data-ttu-id="a5227-263">GO 在批处理和执行任何缓存 [!INCLUDE[tsql](../includes/tsql-md.md)] 语句结尾时会发出信号。</span><span class="sxs-lookup"><span data-stu-id="a5227-263">GO signals both the end of a batch and the execution of any cached [!INCLUDE[tsql](../includes/tsql-md.md)] statements.</span></span> <span data-ttu-id="a5227-264">在每个输入行的结尾按 Enter 键时， **osql** 将缓存此行的语句。</span><span class="sxs-lookup"><span data-stu-id="a5227-264">When you press ENTER at the end of each input line, **osql** caches the statements on that line.</span></span> <span data-ttu-id="a5227-265">键入 GO 后按 Enter 键时，所有当前已缓存的语句都将作为批处理发送到 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="a5227-265">When you press ENTER after typing GO, all of the currently cached statements are sent as a batch to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="a5227-266">使用当前的 **osql** 实用工具时，好像在所执行的脚本结尾处都带有隐含的 GO，因而将执行脚本中的所有语句。</span><span class="sxs-lookup"><span data-stu-id="a5227-266">The current **osql** utility works as if there is an implied GO at the end of any script executed, therefore all statements in the script execute.</span></span>  
  
 <span data-ttu-id="a5227-267">键入以命令终止符开始的行可结束命令。</span><span class="sxs-lookup"><span data-stu-id="a5227-267">End a command by typing a line beginning with a command terminator.</span></span> <span data-ttu-id="a5227-268">可以在命令终止符后输入一个整数来指定命令运行的次数。</span><span class="sxs-lookup"><span data-stu-id="a5227-268">You can follow the command terminator with an integer to specify how many times the command should be run.</span></span> <span data-ttu-id="a5227-269">例如，若要执行此命令 100 次，可键入：</span><span class="sxs-lookup"><span data-stu-id="a5227-269">For example, to execute this command 100 times, type:</span></span>  
  
```  
SELECT x = 1  
GO 100  
```  
  
 <span data-ttu-id="a5227-270">命令执行结束之后将打印结果。</span><span class="sxs-lookup"><span data-stu-id="a5227-270">The results are printed once at the end of execution.</span></span> <span data-ttu-id="a5227-271">**osql** 每行的字符数不得超过 1,000 个。</span><span class="sxs-lookup"><span data-stu-id="a5227-271">**osql** does not accept more than 1,000 characters per line.</span></span> <span data-ttu-id="a5227-272">长语句应当跨多行书写。</span><span class="sxs-lookup"><span data-stu-id="a5227-272">Large statements should be spread across multiple lines.</span></span>  
  
 <span data-ttu-id="a5227-273">Windows 的命令撤回功能可用来撤回和修改 **osql** 语句。</span><span class="sxs-lookup"><span data-stu-id="a5227-273">The command recall facilities of Windows can be used to recall and modify **osql** statements.</span></span> <span data-ttu-id="a5227-274">键入 RESET 可以清除现有的查询缓冲区。</span><span class="sxs-lookup"><span data-stu-id="a5227-274">The existing query buffer can be cleared by typing RESET.</span></span>  
  
 <span data-ttu-id="a5227-275">运行存储过程时， **osql** 在批处理中的每个结果集之间打印一个空行。</span><span class="sxs-lookup"><span data-stu-id="a5227-275">When running stored procedures, **osql** prints a blank line between each set of results in a batch.</span></span> <span data-ttu-id="a5227-276">此外，如果没有应用于执行的语句，则不会出现“0 行受到影响”消息。</span><span class="sxs-lookup"><span data-stu-id="a5227-276">In addition, the "0 rows affected" message does not appear when it does not apply to the statement executed.</span></span>  
  
## <a name="using-osql-interactively"></a><span data-ttu-id="a5227-277">以交互方式使用 osql</span><span class="sxs-lookup"><span data-stu-id="a5227-277">Using osql Interactively</span></span>  
 <span data-ttu-id="a5227-278">若要以交互方式使用 **osql** ，请在命令提示符中键入 **osql** 命令（以及任何选项）。</span><span class="sxs-lookup"><span data-stu-id="a5227-278">To use **osql** interactively, type the **osql** command (and any of the options) at a command prompt.</span></span>  
  
 <span data-ttu-id="a5227-279">通过键入类似下面的命令，可以读入一个包含由 **osql** 执行的查询的文件（例如 Stores.qry）：</span><span class="sxs-lookup"><span data-stu-id="a5227-279">You can read in a file containing a query (such as Stores.qry) for execution by **osql** by typing a command similar to this:</span></span>  
  
```  
osql -E -i stores.qry  
```  
  
 <span data-ttu-id="a5227-280">通过键入类似下面的命令，可以读入包含查询的文件（如 Titles.qry），并将结果导向其他文件：</span><span class="sxs-lookup"><span data-stu-id="a5227-280">You can read in a file containing a query (such as Titles.qry) and direct the results to another file by typing a command similar to this:</span></span>  
  
```  
osql -E -i titles.qry -o titles.res  
```  
  
> [!IMPORTANT]  
>  <span data-ttu-id="a5227-281">如果可能，请使用 **-E**选项（信任连接）。</span><span class="sxs-lookup"><span data-stu-id="a5227-281">When possible, use the **-E**option (trusted connection).</span></span>  
  
 <span data-ttu-id="a5227-282">以交互方式使用**osql**时，可以使用以下命令将操作系统文件读入命令缓冲区 **： r**_file_name_。</span><span class="sxs-lookup"><span data-stu-id="a5227-282">When using **osql** interactively, you can read an operating-system file into the command buffer with **:r**_file_name_.</span></span> <span data-ttu-id="a5227-283">这会将 *file_name* 中的 SQL 脚本作为单个批处理直接发送给服务器。</span><span class="sxs-lookup"><span data-stu-id="a5227-283">This sends the SQL script in *file_name* directly to the server as a single batch.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a5227-284">使用 **osql**时，如果批处理分隔符 GO 出现在 SQL 脚本文件中，则 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 会将其视为语法错误。</span><span class="sxs-lookup"><span data-stu-id="a5227-284">When using **osql**, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] treats the batch separator GO, if it appears in a SQL script file, as a syntax error.</span></span>  
  
## <a name="inserting-comments"></a><span data-ttu-id="a5227-285">插入注释</span><span class="sxs-lookup"><span data-stu-id="a5227-285">Inserting Comments</span></span>  
 <span data-ttu-id="a5227-286">可以在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] osql **提交给**的 Transact-SQL 语句中包含注释。</span><span class="sxs-lookup"><span data-stu-id="a5227-286">You can include comments in a Transact-SQL statement submitted to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] by **osql**.</span></span> <span data-ttu-id="a5227-287">允许使用两种类型的注释样式：-- 和 /\*...\*/。</span><span class="sxs-lookup"><span data-stu-id="a5227-287">Two types of commenting styles are allowed: -- and /\*...\*/.</span></span>  
  
## <a name="using-exit-to-return-results-in-osql"></a><span data-ttu-id="a5227-288">使用 EXIT 返回 osql 中的结果</span><span class="sxs-lookup"><span data-stu-id="a5227-288">Using EXIT to Return Results in osql</span></span>  
 <span data-ttu-id="a5227-289">可以使用 SELECT 语句的结果作为 **osql**的返回值。</span><span class="sxs-lookup"><span data-stu-id="a5227-289">You can use the result of a SELECT statement as the return value from **osql**.</span></span> <span data-ttu-id="a5227-290">如果为数值，则最后一个结果行的最后一列将转换为 4 字节的整数（长整型）。</span><span class="sxs-lookup"><span data-stu-id="a5227-290">If it is numeric, the last column of the last result row is converted to a 4-byte integer (long).</span></span> <span data-ttu-id="a5227-291">MS-DOS 将低字节传递给父进程或操作系统错误级别。</span><span class="sxs-lookup"><span data-stu-id="a5227-291">MS-DOS passes the low byte to the parent process or operating system error level.</span></span> <span data-ttu-id="a5227-292">Windows 则传递整个 4 字节整数。</span><span class="sxs-lookup"><span data-stu-id="a5227-292">Windows passes the entire 4-byte integer.</span></span> <span data-ttu-id="a5227-293">语法为：</span><span class="sxs-lookup"><span data-stu-id="a5227-293">The syntax is:</span></span>  
  
```  
EXIT ( < query > )  
```  
  
 <span data-ttu-id="a5227-294">例如：</span><span class="sxs-lookup"><span data-stu-id="a5227-294">For example:</span></span>  
  
```  
EXIT(SELECT @@ROWCOUNT)  
```  
  
 <span data-ttu-id="a5227-295">还可以在批处理文件中包含 EXIT 参数。</span><span class="sxs-lookup"><span data-stu-id="a5227-295">You can also include the EXIT parameter as part of a batch file.</span></span> <span data-ttu-id="a5227-296">例如：</span><span class="sxs-lookup"><span data-stu-id="a5227-296">For example:</span></span>  
  
```  
osql -E -Q "EXIT(SELECT COUNT(*) FROM '%1')"  
```  
  
 <span data-ttu-id="a5227-297">**osql** 实用工具将在圆括号 **()** 中输入的所有内容原样传递给服务器。</span><span class="sxs-lookup"><span data-stu-id="a5227-297">The **osql** utility passes everything between the parentheses **()** to the server exactly as entered.</span></span> <span data-ttu-id="a5227-298">如果存储系统过程选择了一个集合并返回一个值，则仅返回选择的内容。</span><span class="sxs-lookup"><span data-stu-id="a5227-298">If a stored system procedure selects a set and returns a value, only the selection is returned.</span></span> <span data-ttu-id="a5227-299">圆括号中无参数的 EXIT **()** 语句将执行批处理中此语句前的所有内容，然后不返回值退出。</span><span class="sxs-lookup"><span data-stu-id="a5227-299">The EXIT **()** statement with nothing between the parentheses executes everything preceding it in the batch and then exits with no return value.</span></span>  
  
 <span data-ttu-id="a5227-300">EXIT 格式有四种：</span><span class="sxs-lookup"><span data-stu-id="a5227-300">There are four EXIT formats:</span></span>  
  
-   <span data-ttu-id="a5227-301">EXIT</span><span class="sxs-lookup"><span data-stu-id="a5227-301">EXIT</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a5227-302">不执行批处理，立即退出，不返回值。</span><span class="sxs-lookup"><span data-stu-id="a5227-302">Does not execute the batch; quits immediately and returns no value.</span></span>  
  
-   <span data-ttu-id="a5227-303">EXIT **()**</span><span class="sxs-lookup"><span data-stu-id="a5227-303">EXIT **()**</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a5227-304">执行批处理后退出，不返回值。</span><span class="sxs-lookup"><span data-stu-id="a5227-304">Executes the batch, and then quits and returns no value.</span></span>  
  
-   <span data-ttu-id="a5227-305">退出\*\* (*`query`*) \*\*</span><span class="sxs-lookup"><span data-stu-id="a5227-305">EXIT **(*`query`*)**</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a5227-306">执行包括查询的批处理，返回查询的结果后退出。</span><span class="sxs-lookup"><span data-stu-id="a5227-306">Executes the batch, including the query, and then quits after returning the results of the query.</span></span>  
  
-   <span data-ttu-id="a5227-307">状态为 127 的 RAISERROR。</span><span class="sxs-lookup"><span data-stu-id="a5227-307">RAISERROR with a state of 127</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a5227-308">如果在 **osql** 脚本中使用 RAISERROR，并且出现状态 127，则 **osql** 将退出，并将消息 ID 返回给客户端。</span><span class="sxs-lookup"><span data-stu-id="a5227-308">If RAISERROR is used within an **osql** script and a state of 127 is raised, **osql** will quit and return the message ID back to the client.</span></span> <span data-ttu-id="a5227-309">例如：</span><span class="sxs-lookup"><span data-stu-id="a5227-309">For example:</span></span>  
  
```  
RAISERROR(50001, 10, 127)  
```  
  
 <span data-ttu-id="a5227-310">此错误将导致 **osql** 脚本终止，并向客户端返回消息 ID 50001。</span><span class="sxs-lookup"><span data-stu-id="a5227-310">This error will cause the **osql** script to end and the message ID 50001 will be returned to the client.</span></span>  
  
 <span data-ttu-id="a5227-311">返回值 -1 到 -99 是为 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]保留的； **osql** 可定义下列值：</span><span class="sxs-lookup"><span data-stu-id="a5227-311">The return values -1 to -99 are reserved by [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]; **osql** defines these values:</span></span>  
  
-   <span data-ttu-id="a5227-312">-100</span><span class="sxs-lookup"><span data-stu-id="a5227-312">-100</span></span>  
  
     <span data-ttu-id="a5227-313">选择返回值前遇到错误。</span><span class="sxs-lookup"><span data-stu-id="a5227-313">Error encountered prior to selecting return value.</span></span>  
  
-   <span data-ttu-id="a5227-314">-101</span><span class="sxs-lookup"><span data-stu-id="a5227-314">-101</span></span>  
  
     <span data-ttu-id="a5227-315">选择返回值时找不到行。</span><span class="sxs-lookup"><span data-stu-id="a5227-315">No rows found when selecting return value.</span></span>  
  
-   <span data-ttu-id="a5227-316">-102</span><span class="sxs-lookup"><span data-stu-id="a5227-316">-102</span></span>  
  
     <span data-ttu-id="a5227-317">选择返回值时发生转换错误。</span><span class="sxs-lookup"><span data-stu-id="a5227-317">Conversion error occurred when selecting return value.</span></span>  
  
## <a name="displaying-money-and-smallmoney-data-types"></a><span data-ttu-id="a5227-318">显示 Money 和 Smallmoney 数据类型</span><span class="sxs-lookup"><span data-stu-id="a5227-318">Displaying money and smallmoney Data Types</span></span>  
 <span data-ttu-id="a5227-319">**osql**显示 `money` `smallmoney` 具有两个小数位的和数据类型，但 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 在内部存储值四个小数位。</span><span class="sxs-lookup"><span data-stu-id="a5227-319">**osql** displays the `money` and `smallmoney` data types with two decimal places although [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] stores the value internally with four decimal places.</span></span> <span data-ttu-id="a5227-320">请看下例：</span><span class="sxs-lookup"><span data-stu-id="a5227-320">Consider the example:</span></span>  
  
```  
SELECT CAST(CAST(10.3496 AS money) AS decimal(6, 4))  
GO  
```  
  
 <span data-ttu-id="a5227-321">此语句的结果为 `10.3496`，说明该值是原样按完整的小数位存储的。</span><span class="sxs-lookup"><span data-stu-id="a5227-321">This statement produces a result of `10.3496`, which indicates that the value is stored with all decimal places intact.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5227-322">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a5227-322">See Also</span></span>  
 <span data-ttu-id="a5227-323">[注释 (MDX)](/sql/mdx/comment-mdx) </span><span class="sxs-lookup"><span data-stu-id="a5227-323">[Comment &#40;MDX&#41;](/sql/mdx/comment-mdx) </span></span>  
 <span data-ttu-id="a5227-324">[--（注释）(MDX)](/sql/mdx/comment-mdx) </span><span class="sxs-lookup"><span data-stu-id="a5227-324">[-- &#40;Comment&#41; &#40;MDX&#41;](/sql/mdx/comment-mdx) </span></span>  
 <span data-ttu-id="a5227-325">[CAST 和 CONVERT (Transact-SQL)](/sql/t-sql/functions/cast-and-convert-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a5227-325">[CAST and CONVERT &#40;Transact-SQL&#41;](/sql/t-sql/functions/cast-and-convert-transact-sql) </span></span>  
 [<span data-ttu-id="a5227-326">RAISERROR (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="a5227-326">RAISERROR &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/language-elements/raiserror-transact-sql)  
  
  
