---
title: rsconfig 实用工具 (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- connections [Reporting Services], configuring
- rsconfig utility
- report servers [Reporting Services], connections
- command prompt utilities [Reporting Services]
- command prompt utilities [SQL Server], rsconfig
ms.assetid: 84e45a2f-3ca6-4c16-8259-c15ff49d72ad
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 499fa5529991b36e467567b4c7006845dfcd2578
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691574"
---
# <a name="rsconfig-utility-ssrs"></a><span data-ttu-id="fcf77-102">rsconfig 实用工具 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="fcf77-102">rsconfig Utility (SSRS)</span></span>
  <span data-ttu-id="fcf77-103">**rsconfig.exe** 实用工具可以在 RSReportServer.config 文件中加密并存储连接和帐户值。</span><span class="sxs-lookup"><span data-stu-id="fcf77-103">The **rsconfig.exe** utility encrypts and stores connection and account values in the RSReportServer.config file.</span></span> <span data-ttu-id="fcf77-104">加密值包括用于无人参与报表处理的报表服务器数据库连接信息和帐户值。</span><span class="sxs-lookup"><span data-stu-id="fcf77-104">Encrypted values include report server database connection information and account values used for unattended report processing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fcf77-105">语法</span><span class="sxs-lookup"><span data-stu-id="fcf77-105">Syntax</span></span>  
  
```  
  
      rsconfig {-?}  
{-cconnection}  
{-eunattendedaccount}  
{-mcomputername}  
{-iinstancename}  
{-sservername}  
{-ddatabasename}  
{-aauthmethod}  
{-uusername}  
{-ppassword}  
{-ttrace}  
```  
  
## <a name="arguments"></a><span data-ttu-id="fcf77-106">参数</span><span class="sxs-lookup"><span data-stu-id="fcf77-106">Arguments</span></span>  
  
|<span data-ttu-id="fcf77-107">术语</span><span class="sxs-lookup"><span data-stu-id="fcf77-107">Term</span></span>|<span data-ttu-id="fcf77-108">可选/必需</span><span class="sxs-lookup"><span data-stu-id="fcf77-108">Optional/Required</span></span>|<span data-ttu-id="fcf77-109">定义</span><span class="sxs-lookup"><span data-stu-id="fcf77-109">Definition</span></span>|  
|----------|------------------------|----------------|  
|<span data-ttu-id="fcf77-110">**-?**</span><span class="sxs-lookup"><span data-stu-id="fcf77-110">**-?**</span></span>|<span data-ttu-id="fcf77-111">可选。</span><span class="sxs-lookup"><span data-stu-id="fcf77-111">Optional.</span></span>|<span data-ttu-id="fcf77-112">显示 Rsconfig.exe 参数的语法。</span><span class="sxs-lookup"><span data-stu-id="fcf77-112">Displays the syntax of Rsconfig.exe arguments.</span></span>|  
|`-c`|<span data-ttu-id="fcf77-113">如果未使用 `-e` 参数，则为必需项。</span><span class="sxs-lookup"><span data-stu-id="fcf77-113">Required if `-e` argument is not used.</span></span>|<span data-ttu-id="fcf77-114">指定用于将报表服务器连接到报表服务器数据库的连接字符串、凭据和数据源值。</span><span class="sxs-lookup"><span data-stu-id="fcf77-114">Specifies the connection string, credentials, and data source values used to connect a report server to the report server database.</span></span><br /><br /> <span data-ttu-id="fcf77-115">此参数不带值。</span><span class="sxs-lookup"><span data-stu-id="fcf77-115">This argument does not take a value.</span></span> <span data-ttu-id="fcf77-116">但是，必须对其指定其他参数以提供所有必需的连接值。</span><span class="sxs-lookup"><span data-stu-id="fcf77-116">However, additional arguments must be specified with it to provide all of the required connection values.</span></span><br /><br /> <span data-ttu-id="fcf77-117">可以指定的参数 `-c` 包括 `-m` 、 **-s**、、、、、 `-i` `-d` `-a` `-u` `-p` 和 `-t` 。</span><span class="sxs-lookup"><span data-stu-id="fcf77-117">Arguments that you can specify with `-c` include `-m`, **-s**, `-i`,`-d`,`-a`,`-u`,`-p`, and`-t`.</span></span>|  
|`-e`|<span data-ttu-id="fcf77-118">如果未使用 `-c` 参数，则为必需项。</span><span class="sxs-lookup"><span data-stu-id="fcf77-118">Required if `-c` argument is not used.</span></span>|<span data-ttu-id="fcf77-119">指定无人参与报表执行帐户。</span><span class="sxs-lookup"><span data-stu-id="fcf77-119">Specifies the unattended report execution account.</span></span><br /><br /> <span data-ttu-id="fcf77-120">此参数不带值。</span><span class="sxs-lookup"><span data-stu-id="fcf77-120">This argument does not take a value.</span></span> <span data-ttu-id="fcf77-121">但是，您必须在命令行中指定其他参数，以指定配置文件中加密的值。</span><span class="sxs-lookup"><span data-stu-id="fcf77-121">However, you must include additional arguments on the command line to specify that values that are encrypted in the configuration file.</span></span><br /><br /> <span data-ttu-id="fcf77-122">可以使用 `-e` 指定的参数包括 `-u` 和 `-p`。</span><span class="sxs-lookup"><span data-stu-id="fcf77-122">Arguments that you can specify with `-e` include `-u` and `-p`.</span></span> <span data-ttu-id="fcf77-123">您还可以设置 `-t`。</span><span class="sxs-lookup"><span data-stu-id="fcf77-123">You can also set `-t`.</span></span>|  
|<span data-ttu-id="fcf77-124">`-m`  *computername*</span><span class="sxs-lookup"><span data-stu-id="fcf77-124">`-m`  *computername*</span></span>|<span data-ttu-id="fcf77-125">如果要配置远程报表服务器实例，则此参数是必需的。</span><span class="sxs-lookup"><span data-stu-id="fcf77-125">Required if you are configuring a remote report server instance.</span></span>|<span data-ttu-id="fcf77-126">指定承载报表服务器的计算机的名称。</span><span class="sxs-lookup"><span data-stu-id="fcf77-126">Specifies the name of the computer that is hosting the report server.</span></span> <span data-ttu-id="fcf77-127">如果省略该参数，则默认值为 `localhost`。</span><span class="sxs-lookup"><span data-stu-id="fcf77-127">If this argument is omitted, the default is `localhost`.</span></span>|  
|<span data-ttu-id="fcf77-128">-s\*\*  servername\*\*  \*\*</span><span class="sxs-lookup"><span data-stu-id="fcf77-128">**-s**  *servername*</span></span>|<span data-ttu-id="fcf77-129">必需。</span><span class="sxs-lookup"><span data-stu-id="fcf77-129">Required.</span></span>|<span data-ttu-id="fcf77-130">指定承载报表服务器数据库的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="fcf77-130">Specifies the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance that hosts the report server database.</span></span>|  
|<span data-ttu-id="fcf77-131">`-i`  *instancename*</span><span class="sxs-lookup"><span data-stu-id="fcf77-131">`-i`  *instancename*</span></span>|<span data-ttu-id="fcf77-132">如果使用了命名实例，则此参数是必需的。</span><span class="sxs-lookup"><span data-stu-id="fcf77-132">Required if you are using named instances.</span></span>|<span data-ttu-id="fcf77-133">如果使用了 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 命名实例承载报表服务器数据库，则此值指定该命名实例。</span><span class="sxs-lookup"><span data-stu-id="fcf77-133">If you used a named [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance to host the report server database, this value specifies the named instance.</span></span>|  
|<span data-ttu-id="fcf77-134">`-d`  *database*</span><span class="sxs-lookup"><span data-stu-id="fcf77-134">`-d`  *databasename*</span></span>|<span data-ttu-id="fcf77-135">必需。</span><span class="sxs-lookup"><span data-stu-id="fcf77-135">Required.</span></span>|<span data-ttu-id="fcf77-136">指定报表服务器数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="fcf77-136">Specifies the name of the report server database.</span></span>|  
|<span data-ttu-id="fcf77-137">`-a`  *authmethod*</span><span class="sxs-lookup"><span data-stu-id="fcf77-137">`-a`  *authmethod*</span></span>|<span data-ttu-id="fcf77-138">必需。</span><span class="sxs-lookup"><span data-stu-id="fcf77-138">Required.</span></span>|<span data-ttu-id="fcf77-139">指定报表服务器连接到报表服务器数据库时使用的身份验证方法。</span><span class="sxs-lookup"><span data-stu-id="fcf77-139">Specifies the authentication method that the report server uses to connect to the report server database.</span></span> <span data-ttu-id="fcf77-140">有效值是 `Windows` 或 `SQL`（该参数不区分大小写）。</span><span class="sxs-lookup"><span data-stu-id="fcf77-140">Valid values are `Windows` or `SQL` (this argument is not case-sensitive).</span></span><br /><br /> <span data-ttu-id="fcf77-141">`Windows` 指定报表服务器使用 Windows 身份验证。</span><span class="sxs-lookup"><span data-stu-id="fcf77-141">`Windows` specifies that the report server use Windows Authentication.</span></span><br /><br /> <span data-ttu-id="fcf77-142">`SQL` 指定报表服务器使用 SQL Server 身份验证。</span><span class="sxs-lookup"><span data-stu-id="fcf77-142">`SQL` specifies that the report server use SQL Server Authentication.</span></span>|  
|<span data-ttu-id="fcf77-143">`-u`  *[域 \\ ]用户名*</span><span class="sxs-lookup"><span data-stu-id="fcf77-143">`-u`  *[domain\\]username*</span></span>|<span data-ttu-id="fcf77-144">`-e` 是必需的，`-c` 是可选的。</span><span class="sxs-lookup"><span data-stu-id="fcf77-144">Required with `-e` Optional with `-c`.</span></span>|<span data-ttu-id="fcf77-145">指定报表服务器数据库连接或无人参与帐户的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="fcf77-145">Specifies a user account for the report server database connection or for the unattended account.</span></span><br /><br /> <span data-ttu-id="fcf77-146">对于 **rsconfig -e**，该参数是必需的。</span><span class="sxs-lookup"><span data-stu-id="fcf77-146">For **rsconfig -e**, this argument is required.</span></span> <span data-ttu-id="fcf77-147">必须是域用户帐户。</span><span class="sxs-lookup"><span data-stu-id="fcf77-147">It must be a domain user account.</span></span><br /><br /> <span data-ttu-id="fcf77-148">对于**rsconfig-c**和 `-a SQL` ，此参数必须指定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名。</span><span class="sxs-lookup"><span data-stu-id="fcf77-148">For **rsconfig -c** and `-a SQL`, this argument must specify a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login.</span></span><br /><br /> <span data-ttu-id="fcf77-149">对于**rsconfig**和 `-a Windows` ，此参数可以指定域用户、内置帐户或服务帐户凭据。</span><span class="sxs-lookup"><span data-stu-id="fcf77-149">For **rsconfig -c** and `-a Windows`, this argument may specify a domain user, a built-in account, or service account credentials.</span></span> <span data-ttu-id="fcf77-150">若要指定域帐户，请以“domain\username”\*\* 格式指定域\*\* 和用户名\*\*。</span><span class="sxs-lookup"><span data-stu-id="fcf77-150">If you are specifying a domain account, specify *domain* and *username* in the format *domain\username*.</span></span> <span data-ttu-id="fcf77-151">如果使用了内置帐户，则该参数是可选的。</span><span class="sxs-lookup"><span data-stu-id="fcf77-151">If you are using a built-in account, this argument is optional.</span></span> <span data-ttu-id="fcf77-152">如果要使用服务帐户凭据，则可省略该参数。</span><span class="sxs-lookup"><span data-stu-id="fcf77-152">If you want to use service account credentials, omit this argument.</span></span>|  
|<span data-ttu-id="fcf77-153">`-p`  *权限*</span><span class="sxs-lookup"><span data-stu-id="fcf77-153">`-p`  *password*</span></span>|<span data-ttu-id="fcf77-154">如果指定了 `-u`，则该参数是必需的。</span><span class="sxs-lookup"><span data-stu-id="fcf77-154">Required if `-u` is specified.</span></span>|<span data-ttu-id="fcf77-155">指定与 *username* 参数一起使用的密码。</span><span class="sxs-lookup"><span data-stu-id="fcf77-155">Specifies the password to use with the *username* argument.</span></span> <span data-ttu-id="fcf77-156">如果帐户不需要密码，则可将该参数设置为空值。</span><span class="sxs-lookup"><span data-stu-id="fcf77-156">You can set this argument to a blank value if the account does not require a password.</span></span> <span data-ttu-id="fcf77-157">对于域帐户，此值区分大小写。</span><span class="sxs-lookup"><span data-stu-id="fcf77-157">This value is case-sensitive for domain accounts.</span></span>|  
|`-t`|<span data-ttu-id="fcf77-158">可选。</span><span class="sxs-lookup"><span data-stu-id="fcf77-158">Optional.</span></span>|<span data-ttu-id="fcf77-159">将错误消息输出到跟踪日志。</span><span class="sxs-lookup"><span data-stu-id="fcf77-159">Outputs error messages to the trace log.</span></span> <span data-ttu-id="fcf77-160">此参数不带值。</span><span class="sxs-lookup"><span data-stu-id="fcf77-160">This argument does not take a value.</span></span> <span data-ttu-id="fcf77-161">有关详细信息，请参阅 [Report Server Service Trace Log](../report-server/report-server-service-trace-log.md)。</span><span class="sxs-lookup"><span data-stu-id="fcf77-161">For more information, see [Report Server Service Trace Log](../report-server/report-server-service-trace-log.md).</span></span>|  
  
## <a name="permissions"></a><span data-ttu-id="fcf77-162">权限</span><span class="sxs-lookup"><span data-stu-id="fcf77-162">Permissions</span></span>  
 <span data-ttu-id="fcf77-163">您必须是要配置的承载报表服务器的计算机本地管理员。</span><span class="sxs-lookup"><span data-stu-id="fcf77-163">You must be a local administrator on the computer that hosts the report server you are configuring.</span></span>  
  
## <a name="file-location"></a><span data-ttu-id="fcf77-164">文件位置</span><span class="sxs-lookup"><span data-stu-id="fcf77-164">File Location</span></span>  
 <span data-ttu-id="fcf77-165">Rsconfig.exe 位于 **\Program Files\Microsoft SQL Server\110\Tools\Binn**中。</span><span class="sxs-lookup"><span data-stu-id="fcf77-165">Rsconfig.exe is located in **\Program Files\Microsoft SQL Server\110\Tools\Binn**.</span></span> <span data-ttu-id="fcf77-166">可以在文件系统的任何文件夹中运行此实用工具。</span><span class="sxs-lookup"><span data-stu-id="fcf77-166">You can run the utility from any folder on your file system.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fcf77-167">备注</span><span class="sxs-lookup"><span data-stu-id="fcf77-167">Remarks</span></span>  
 <span data-ttu-id="fcf77-168">Rsconfig.exe 有以下两个用途：</span><span class="sxs-lookup"><span data-stu-id="fcf77-168">Rsconfig.exe is used for two purposes:</span></span>  
  
-   <span data-ttu-id="fcf77-169">修改报表服务器用于连接到报表服务器数据库的连接信息。</span><span class="sxs-lookup"><span data-stu-id="fcf77-169">To modify the connection information that a report server uses to connect to a report server database.</span></span>  
  
-   <span data-ttu-id="fcf77-170">配置报表服务器在其他凭据不可用时登录远程数据库服务器所用的特殊帐户。</span><span class="sxs-lookup"><span data-stu-id="fcf77-170">To configure a special account that the report server uses to log on to a remote database server when other credentials are not available.</span></span>  
  
 <span data-ttu-id="fcf77-171">可以针对**的本地或远程实例来运行** rsconfig [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]实用工具。</span><span class="sxs-lookup"><span data-stu-id="fcf77-171">You can run the**rsconfig** utility on a local or remote instance of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="fcf77-172">不能使用 **rsconfig** 实用工具解密和查看已设置的值。</span><span class="sxs-lookup"><span data-stu-id="fcf77-172">You cannot use the **rsconfig** utility to decrypt and view values that are already set.</span></span>  
  
 <span data-ttu-id="fcf77-173">要配置的计算机上必须安装 Windows Management Instrumentation (WMI) 才能运行此配置工具。</span><span class="sxs-lookup"><span data-stu-id="fcf77-173">Before you can run this utility, Windows Management Instrumentation (WMI) must be installed on the computer that you are configuring.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="fcf77-174">示例</span><span class="sxs-lookup"><span data-stu-id="fcf77-174">Examples</span></span>  
 <span data-ttu-id="fcf77-175">以下示例阐释了 **rsconfig**的使用方法。</span><span class="sxs-lookup"><span data-stu-id="fcf77-175">The following examples illustrate ways of using **rsconfig**.</span></span>  
  
#### <a name="specifying-a-domain-user-account"></a><span data-ttu-id="fcf77-176">指定域用户帐户</span><span class="sxs-lookup"><span data-stu-id="fcf77-176">Specifying a Domain User Account</span></span>  
 <span data-ttu-id="fcf77-177">此示例显示如何配置报表服务器，以便在连接本地报表服务器数据库时使用域用户帐户。</span><span class="sxs-lookup"><span data-stu-id="fcf77-177">This example shows how to configure a report server to use a domain user account when connecting to a local report server database.</span></span>  
  
```  
rsconfig -c -s <SQLSERVERNAME> -d reportserver -a Windows -u <MYDOMAIN\MYACCOUNT> -p <PASSWORD>  
```  
  
#### <a name="specifying-a-sql-server-database-user-account"></a><span data-ttu-id="fcf77-178">指定 SQL Server 数据库用户帐户</span><span class="sxs-lookup"><span data-stu-id="fcf77-178">Specifying a SQL Server Database User Account</span></span>  
 <span data-ttu-id="fcf77-179">此示例显示如何配置报表服务器配置以使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名连接到远程报表服务器数据库。</span><span class="sxs-lookup"><span data-stu-id="fcf77-179">This example shows how to configure a report server to use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login to connect to a remote report server database.</span></span>  
  
```  
rsconfig -c -m <REMOTECOMPUTERNAME> -s <SQLSERVERNAME> -d reportserver -a SQL -u SA -p <SAPASSWORD>  
```  
  
#### <a name="specifying-a-built-in-account"></a><span data-ttu-id="fcf77-180">指定内置帐户</span><span class="sxs-lookup"><span data-stu-id="fcf77-180">Specifying a Built-in Account</span></span>  
 <span data-ttu-id="fcf77-181">此示例显示如何配置报表服务器，以便在连接本地报表服务器数据库时使用内置帐户。</span><span class="sxs-lookup"><span data-stu-id="fcf77-181">This example shows how to configure a report server to use a built-in account when connecting to a local report server database.</span></span> <span data-ttu-id="fcf77-182">请注意，未使用 `-u` 参数。</span><span class="sxs-lookup"><span data-stu-id="fcf77-182">Notice that `-u` is not used.</span></span> <span data-ttu-id="fcf77-183">支持的内置帐户值的示例包括用于本地系统的 NT AUTHORITY\SYSTEM 和用于网络服务的 NT AUTHORITY\NETWORKSERVICE ([!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] 仅) 。</span><span class="sxs-lookup"><span data-stu-id="fcf77-183">Examples of supported built-in account values include NT AUTHORITY\SYSTEM for Local System and NT AUTHORITY\NETWORKSERVICE for Network Service ([!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] only).</span></span>  
  
```  
rsconfig -c -s <SQLSERVERNAME> -d reportserver -a Windows "NT AUTHORITY\SYSTEM"  
```  
  
#### <a name="specifying-a-service-account"></a><span data-ttu-id="fcf77-184">指定服务帐户</span><span class="sxs-lookup"><span data-stu-id="fcf77-184">Specifying a Service Account</span></span>  
 <span data-ttu-id="fcf77-185">此示例显示如何配置报表服务器，以便在连接本地报表服务器数据库时使用 Report Server Windows 服务帐户和 Web 服务帐户。</span><span class="sxs-lookup"><span data-stu-id="fcf77-185">This example shows how to configure a report server to use the Report Server Windows service account and Web service account when connecting to a local report server database.</span></span> <span data-ttu-id="fcf77-186">请注意，未使用 `-u` 参数，并且没有指定任何帐户信息。</span><span class="sxs-lookup"><span data-stu-id="fcf77-186">Notice that `-u` is not used and that no account information is specified.</span></span> <span data-ttu-id="fcf77-187">从命令中清除帐户值时， **rsconfig** 实用工具使用每个服务运行时都要使用的集成安全性和服务帐户。</span><span class="sxs-lookup"><span data-stu-id="fcf77-187">When you eliminate account values from the command, the **rsconfig** utility uses integrated security and the service account that each service runs under.</span></span>  
  
```  
rsconfig -c -s <SQLSERVERNAME> -d reportserver -a Windows  
```  
  
#### <a name="specifying-the-unattended-account-on-a-local-server"></a><span data-ttu-id="fcf77-188">指定本地服务器中的无人参与帐户</span><span class="sxs-lookup"><span data-stu-id="fcf77-188">Specifying the Unattended Account on a Local Server</span></span>  
 <span data-ttu-id="fcf77-189">此示例显示如何配置用于报表的无人参与报表执行的帐户，该帐户不向外部数据源传递凭据。</span><span class="sxs-lookup"><span data-stu-id="fcf77-189">This example shows how to configure the account used for unattended report execution for reports that do not pass credentials to the external data source.</span></span> <span data-ttu-id="fcf77-190">该帐户必须是 Windows 域帐户。</span><span class="sxs-lookup"><span data-stu-id="fcf77-190">The account must be a Windows domain account.</span></span> <span data-ttu-id="fcf77-191">无法为用户名和密码指定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名。</span><span class="sxs-lookup"><span data-stu-id="fcf77-191">You cannot specify a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login for the user name and password.</span></span> <span data-ttu-id="fcf77-192">该帐户在本地报表服务器实例中配置。</span><span class="sxs-lookup"><span data-stu-id="fcf77-192">The account is configured on a local report server instance.</span></span> <span data-ttu-id="fcf77-193">在 ReportingServices\LogFiles 文件夹的跟踪日志中捕获错误消息。</span><span class="sxs-lookup"><span data-stu-id="fcf77-193">Error messages are captured in the trace logs in the ReportingServices\LogFiles folder.</span></span>  
  
```  
rsconfig -e -u <DOMAIN\ACCOUNT> -p <PASSWORD> -t  
```  
  
#### <a name="specifying-the-unattended-account-on-a-remote-server"></a><span data-ttu-id="fcf77-194">指定远程服务器中的无人参与帐户</span><span class="sxs-lookup"><span data-stu-id="fcf77-194">Specifying the Unattended Account on a Remote Server</span></span>  
 <span data-ttu-id="fcf77-195">此示例显示在与 Rsconfig.exe 版本相同的远程报表服务器实例（例如，报表服务器和 Rsconfig.exe 都为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008 R2 版）中如何配置帐户。</span><span class="sxs-lookup"><span data-stu-id="fcf77-195">This example shows how to configure the account on a remote report server instance that is the same version as Rsconfig.exe (for example, the report server and Rsconfig.exe are the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008 R2 version).</span></span> <span data-ttu-id="fcf77-196">在远程服务器的跟踪日志中捕获错误消息信息。</span><span class="sxs-lookup"><span data-stu-id="fcf77-196">Error message information is captured in the trace logs on the remote server.</span></span>  
  
```  
rsconfig -e -m <REMOTECOMPUTERNAME> -s <SQLSERVERNAME> -u <DOMAIN\ACCOUNT> -p <PASSWORD> -t  
```  
  
## <a name="see-also"></a><span data-ttu-id="fcf77-197">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fcf77-197">See Also</span></span>  
 <span data-ttu-id="fcf77-198">[&#40;SSRS Configuration Manager 配置报表服务器数据库连接&#41;](../../sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="fcf77-198">[Configure a Report Server Database Connection  &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md) </span></span>  
 <span data-ttu-id="fcf77-199">[&#40;SSRS Configuration Manager 配置无人参与的执行帐户&#41;](../install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="fcf77-199">[Configure the Unattended Execution Account &#40;SSRS Configuration Manager&#41;](../install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md) </span></span>  
 <span data-ttu-id="fcf77-200">[Reporting Services 报表服务器（本机模式）](../report-server/reporting-services-report-server-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="fcf77-200">[Reporting Services Report Server &#40;Native Mode&#41;](../report-server/reporting-services-report-server-native-mode.md) </span></span>  
 <span data-ttu-id="fcf77-201">[存储加密的 Report Server 数据（SSRS 配置管理器）](../install-windows/ssrs-encryption-keys-store-encrypted-report-server-data.md) </span><span class="sxs-lookup"><span data-stu-id="fcf77-201">[Store Encrypted Report Server Data &#40;SSRS Configuration Manager&#41;](../install-windows/ssrs-encryption-keys-store-encrypted-report-server-data.md) </span></span>  
 <span data-ttu-id="fcf77-202">[Reporting Services 配置文件](../report-server/reporting-services-configuration-files.md) </span><span class="sxs-lookup"><span data-stu-id="fcf77-202">[Reporting Services Configuration Files](../report-server/reporting-services-configuration-files.md) </span></span>  
 <span data-ttu-id="fcf77-203">[报表服务器命令提示实用工具 &#40;SSRS&#41;](report-server-command-prompt-utilities-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="fcf77-203">[Report Server Command Prompt Utilities &#40;SSRS&#41;](report-server-command-prompt-utilities-ssrs.md) </span></span>  
 [<span data-ttu-id="fcf77-204">RSReportServer Configuration File</span><span class="sxs-lookup"><span data-stu-id="fcf77-204">RSReportServer Configuration File</span></span>](../report-server/rsreportserver-config-configuration-file.md)  
  
  
