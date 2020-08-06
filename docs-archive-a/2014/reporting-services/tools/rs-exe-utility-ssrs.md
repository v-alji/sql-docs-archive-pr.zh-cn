---
title: RS.exe 实用工具 (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- automatic report server tasks
- rs utility
- command prompt utilities [Reporting Services]
- report servers [Reporting Services], automating tasks
- command prompt utilities [SQL Server], rs
- scripts [Reporting Services], command prompt
- deploying reports [Reporting Services]
ms.assetid: bd6f958f-cce6-4e79-8a0f-9475da2919ce
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: bcf21a1bf2453d2bd1f0644e31ca46f3f94e6884
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691570"
---
# <a name="rsexe-utility-ssrs"></a><span data-ttu-id="5a8a6-102">RS.exe 实用工具 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="5a8a6-102">RS.exe Utility (SSRS)</span></span>
  <span data-ttu-id="5a8a6-103">rs.exe 实用工具处理您在输入文件中提供的脚本。</span><span class="sxs-lookup"><span data-stu-id="5a8a6-103">The rs.exe utility processes script that you provide in an input file.</span></span> <span data-ttu-id="5a8a6-104">使用此实用工具，可以实现报表服务器部署与管理任务的自动化。</span><span class="sxs-lookup"><span data-stu-id="5a8a6-104">Use this utility to automate report server deployment and administration tasks.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5a8a6-105">从 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]开始，配置为 SharePoint 集成模式的报表服务器以及配置为本机模式的服务器均支持 **rs** 实用工具。</span><span class="sxs-lookup"><span data-stu-id="5a8a6-105">Beginning with [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], the **rs** utility is supported against report servers that are configured for SharePoint integrated mode as well as servers configured in native mode.</span></span> <span data-ttu-id="5a8a6-106">以前的版本仅支持本机模式配置。</span><span class="sxs-lookup"><span data-stu-id="5a8a6-106">Previous versions only supported native mode configurations.</span></span>  
  
 <span data-ttu-id="5a8a6-107">**本主题内容：**</span><span class="sxs-lookup"><span data-stu-id="5a8a6-107">**In this topic:**</span></span>  
  
-   [<span data-ttu-id="5a8a6-108">文件位置</span><span class="sxs-lookup"><span data-stu-id="5a8a6-108">File Location</span></span>](#bkmk_filelocation)  
  
-   [<span data-ttu-id="5a8a6-109">参数</span><span class="sxs-lookup"><span data-stu-id="5a8a6-109">Arguments</span></span>](#bkmk_arguments)  
  
-   [<span data-ttu-id="5a8a6-110">权限</span><span class="sxs-lookup"><span data-stu-id="5a8a6-110">Permissions</span></span>](#bkmk_permissions)  
  
-   [<span data-ttu-id="5a8a6-111">示例</span><span class="sxs-lookup"><span data-stu-id="5a8a6-111">Examples</span></span>](#bkmk_examples)  
  
## <a name="syntax"></a><span data-ttu-id="5a8a6-112">语法</span><span class="sxs-lookup"><span data-stu-id="5a8a6-112">Syntax</span></span>  
  
```  
  
      rs {-?}  
{-i input_file=}  
{-s serverURL}  
{-u username}  
{-p password}  
{-e endpoint}  
{-l time_out}  
{-b batchmode}  
{-v globalvars=}  
{-t trace}  
```  
  
##  <a name="file-location"></a><a name="bkmk_filelocation"></a> <span data-ttu-id="5a8a6-113">文件位置</span><span class="sxs-lookup"><span data-stu-id="5a8a6-113">File Location</span></span>  
 <span data-ttu-id="5a8a6-114">**RS.exe** 位于 **\Program Files\Microsoft SQL Server\110\Tools\Binn**。</span><span class="sxs-lookup"><span data-stu-id="5a8a6-114">**RS.exe** is located at **\Program Files\Microsoft SQL Server\110\Tools\Binn**.</span></span> <span data-ttu-id="5a8a6-115">可以在文件系统的任何文件夹中运行此实用工具。</span><span class="sxs-lookup"><span data-stu-id="5a8a6-115">You can run the utility from any folder on your file system.</span></span>  
  
##  <a name="arguments"></a><a name="bkmk_arguments"></a> <span data-ttu-id="5a8a6-116">参数</span><span class="sxs-lookup"><span data-stu-id="5a8a6-116">Arguments</span></span>  
 <span data-ttu-id="5a8a6-117">**-?**</span><span class="sxs-lookup"><span data-stu-id="5a8a6-117">**-?**</span></span>  
 <span data-ttu-id="5a8a6-118">（可选）显示 **rs** 参数的语法。</span><span class="sxs-lookup"><span data-stu-id="5a8a6-118">(Optional) Displays the syntax of **rs** arguments.</span></span>  
  
 <span data-ttu-id="5a8a6-119">`-i`*input_file*</span><span class="sxs-lookup"><span data-stu-id="5a8a6-119">`-i` *input_file*</span></span>  
 <span data-ttu-id="5a8a6-120">（必需）指定要执行的 .rss 文件。</span><span class="sxs-lookup"><span data-stu-id="5a8a6-120">(Required) Specifies the .rss file to execute.</span></span> <span data-ttu-id="5a8a6-121">此值可以是指向 .rss 文件的相对路径或完全限定路径。</span><span class="sxs-lookup"><span data-stu-id="5a8a6-121">This value can be a relative or fully qualified path to the .rss file.</span></span>  
  
 <span data-ttu-id="5a8a6-122">`-s`*serverURL*</span><span class="sxs-lookup"><span data-stu-id="5a8a6-122">`-s` *serverURL*</span></span>  
 <span data-ttu-id="5a8a6-123">（必需）指定执行文件的 Web 服务器的名称和报表服务器的虚拟目录名。</span><span class="sxs-lookup"><span data-stu-id="5a8a6-123">(Required) Specifies the Web server name and report server virtual directory name to execute the file against.</span></span> <span data-ttu-id="5a8a6-124">以下是报表服务器 URL 的一个示例： `http://examplewebserver/reportserver`。</span><span class="sxs-lookup"><span data-stu-id="5a8a6-124">An example of a report server URL is `http://examplewebserver/reportserver`.</span></span> <span data-ttu-id="5a8a6-125">服务器名称开头处的前缀 http:// 或 https:// 是可选的。</span><span class="sxs-lookup"><span data-stu-id="5a8a6-125">The prefix http:// or https:// at the beginning of the server name is optional.</span></span> <span data-ttu-id="5a8a6-126">如果省略前缀，报表服务器脚本主机将先尝试使用 https，并在 https 无效时使用 http。</span><span class="sxs-lookup"><span data-stu-id="5a8a6-126">If you omit the prefix, the report server script host tries to use https first, and then uses http if https does not work.</span></span>  
  
 <span data-ttu-id="5a8a6-127">`-u`[*域* \\ ]*用户名*</span><span class="sxs-lookup"><span data-stu-id="5a8a6-127">`-u` [*domain*\\]*username*</span></span>  
 <span data-ttu-id="5a8a6-128">（可选）指定用于连接到报表服务器的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="5a8a6-128">(Optional) Specifies a user account used to connect to the report server.</span></span> <span data-ttu-id="5a8a6-129">如果省略 `-u` 和 `-p`，则使用当前的 Windows 用户帐户。</span><span class="sxs-lookup"><span data-stu-id="5a8a6-129">If `-u` and `-p` are omitted, the current Windows user account is used.</span></span>  
  
 <span data-ttu-id="5a8a6-130">`-p`*密码*</span><span class="sxs-lookup"><span data-stu-id="5a8a6-130">`-p` *password*</span></span>  
 <span data-ttu-id="5a8a6-131">（指定了 `-u` 时为必需）指定与 `-u` 参数一起使用的密码。</span><span class="sxs-lookup"><span data-stu-id="5a8a6-131">(Required if `-u` is specified) Specifies the password to use with the `-u` argument.</span></span> <span data-ttu-id="5a8a6-132">此值区分大小写。</span><span class="sxs-lookup"><span data-stu-id="5a8a6-132">This value is case-sensitive.</span></span>  
  
 `-e`  
 <span data-ttu-id="5a8a6-133">（可选）指定应对其运行脚本的 SOAP 端点。</span><span class="sxs-lookup"><span data-stu-id="5a8a6-133">(Optional) Specifies the SOAP endpoint against which the script should run.</span></span> <span data-ttu-id="5a8a6-134">有效值如下：</span><span class="sxs-lookup"><span data-stu-id="5a8a6-134">Valid values are the following:</span></span>  
  
-   <span data-ttu-id="5a8a6-135">Mgmt2010</span><span class="sxs-lookup"><span data-stu-id="5a8a6-135">Mgmt2010</span></span>  
  
-   <span data-ttu-id="5a8a6-136">Mgmt2006</span><span class="sxs-lookup"><span data-stu-id="5a8a6-136">Mgmt2006</span></span>  
  
-   <span data-ttu-id="5a8a6-137">Mgmt2005</span><span class="sxs-lookup"><span data-stu-id="5a8a6-137">Mgmt2005</span></span>  
  
-   <span data-ttu-id="5a8a6-138">Exec2005</span><span class="sxs-lookup"><span data-stu-id="5a8a6-138">Exec2005</span></span>  
  
 <span data-ttu-id="5a8a6-139">如果未指定值，则使用 Mgmt2005 端点。</span><span class="sxs-lookup"><span data-stu-id="5a8a6-139">If a value is not specified, the Mgmt2005 endpoint is used.</span></span> <span data-ttu-id="5a8a6-140">有关 SOAP 端点的详细信息，请参阅 [Report Server Web Service Endpoints](../report-server-web-service/methods/report-server-web-service-endpoints.md)。</span><span class="sxs-lookup"><span data-stu-id="5a8a6-140">For more information about the SOAP endpoints, see [Report Server Web Service Endpoints](../report-server-web-service/methods/report-server-web-service-endpoints.md).</span></span>  
  
 <span data-ttu-id="5a8a6-141">`-l`*time_out*</span><span class="sxs-lookup"><span data-stu-id="5a8a6-141">`-l` *time_out*</span></span>  
 <span data-ttu-id="5a8a6-142"> (可选) 指定到服务器的连接超时之前经过的秒数。默认值为60秒。</span><span class="sxs-lookup"><span data-stu-id="5a8a6-142">(Optional) Specifies the number of seconds that elapse before the connection to the server times out. The default is 60 seconds.</span></span> <span data-ttu-id="5a8a6-143">如果未指定超时值，则使用默认值。</span><span class="sxs-lookup"><span data-stu-id="5a8a6-143">If you do not specify a time-out value, the default is used.</span></span> <span data-ttu-id="5a8a6-144">`0` 值指定连接从不超时。</span><span class="sxs-lookup"><span data-stu-id="5a8a6-144">A value of `0` specifies that the connection never times out.</span></span>  
  
 <span data-ttu-id="5a8a6-145">**-b**</span><span class="sxs-lookup"><span data-stu-id="5a8a6-145">**-b**</span></span>  
 <span data-ttu-id="5a8a6-146">（可选）指定脚本文件中的命令以批处理方式运行。</span><span class="sxs-lookup"><span data-stu-id="5a8a6-146">(Optional) Specifies that the commands in the script file run in a batch.</span></span> <span data-ttu-id="5a8a6-147">如有任何命令失败，则回滚批处理。</span><span class="sxs-lookup"><span data-stu-id="5a8a6-147">If any commands fail, the batch is rolled back.</span></span> <span data-ttu-id="5a8a6-148">某些命令无法以批处理方式运行，这些命令将按常规方式运行。</span><span class="sxs-lookup"><span data-stu-id="5a8a6-148">Some commands cannot be batched, and those run as usual.</span></span> <span data-ttu-id="5a8a6-149">仅当脚本中产生异常并且未在脚本中得到处理时，才会导致回滚。</span><span class="sxs-lookup"><span data-stu-id="5a8a6-149">Only exceptions that are thrown and are not handled within the script result in a rollback.</span></span> <span data-ttu-id="5a8a6-150">如果脚本处理了异常，并从 `Main` 正常返回，则将提交批处理。</span><span class="sxs-lookup"><span data-stu-id="5a8a6-150">If the script handles an exception and returns normally from `Main`, the batch is committed.</span></span> <span data-ttu-id="5a8a6-151">如果省略此参数，则命令将不以批处理方式运行。</span><span class="sxs-lookup"><span data-stu-id="5a8a6-151">If you omit this parameter, the commands run without creating a batch.</span></span> <span data-ttu-id="5a8a6-152">有关详细信息，请参阅 [Batching Methods](../report-server-web-service-net-framework-soap-headers/batching-methods.md)。</span><span class="sxs-lookup"><span data-stu-id="5a8a6-152">For more information, see [Batching Methods](../report-server-web-service-net-framework-soap-headers/batching-methods.md).</span></span>  
  
 <span data-ttu-id="5a8a6-153">`-v`*globalvar*</span><span class="sxs-lookup"><span data-stu-id="5a8a6-153">`-v` *globalvar*</span></span>  
 <span data-ttu-id="5a8a6-154">（可选）指定脚本中使用的全局变量。</span><span class="sxs-lookup"><span data-stu-id="5a8a6-154">(Optional) Specifies global variables that are used in the script.</span></span> <span data-ttu-id="5a8a6-155">如果脚本使用全局变量，则必须指定此参数。</span><span class="sxs-lookup"><span data-stu-id="5a8a6-155">If the script uses global variables, you must specify this argument.</span></span> <span data-ttu-id="5a8a6-156">指定的值必须对 .rss 文件中定义的全局变量有效。</span><span class="sxs-lookup"><span data-stu-id="5a8a6-156">The value that you specify must be valid for global variable defined in the .rss file.</span></span> <span data-ttu-id="5a8a6-157">必须为每个 –v 参数指定一个全局变量\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5a8a6-157">You must specify one global variable for each **-v** argument.</span></span>  
  
 <span data-ttu-id="5a8a6-158">`-v` 参数在命令行上指定，可用来为运行时在脚本中定义的全局变量设置值。</span><span class="sxs-lookup"><span data-stu-id="5a8a6-158">The `-v` argument is specified on the command line and is used to set the value for a global variable that is defined in your script at run time.</span></span> <span data-ttu-id="5a8a6-159">例如，如果脚本中包含一个名为 *parentFolder*的变量，则可以在命令行上为该文件夹指定一个名称：</span><span class="sxs-lookup"><span data-stu-id="5a8a6-159">For example, if your script contains a variable named *parentFolder*, you can specify a name for that folder on the command line:</span></span>  
  
 `rs.exe -i myScriptFile.rss -s http://myServer/reportserver -v parentFolder="Financial Reports"`  
  
 <span data-ttu-id="5a8a6-160">全局变量以给定的名称命名，并设置为提供的值。</span><span class="sxs-lookup"><span data-stu-id="5a8a6-160">Global variables are created with the names given and set to the values supplied.</span></span> <span data-ttu-id="5a8a6-161">例如， **-v a =**" `1` " **-v b =**"" 将 `2` 生成一个名为 `a` 且值为 "" 的变量 `1` ，以及一个值为 "" 的变量**b** `2` 。</span><span class="sxs-lookup"><span data-stu-id="5a8a6-161">For example, **-v a=**"`1`" **-v b=**"`2`" results in a variable named `a` with a value of"`1`" and a variable **b** with a value of "`2`".</span></span>  
  
 <span data-ttu-id="5a8a6-162">全局变量可用于脚本中的所有函数。</span><span class="sxs-lookup"><span data-stu-id="5a8a6-162">Global variables are available to any function in the script.</span></span> <span data-ttu-id="5a8a6-163">反斜杠和引号 (\*\* \\ "\*\*) 被解释为双引号。</span><span class="sxs-lookup"><span data-stu-id="5a8a6-163">A backslash and quotation mark (**\\"**) is interpreted as a double quotation mark.</span></span> <span data-ttu-id="5a8a6-164">仅当字符串中包含空格时才需要使用英文引号。</span><span class="sxs-lookup"><span data-stu-id="5a8a6-164">The quotation marks are required only if the string contains a space.</span></span> <span data-ttu-id="5a8a6-165">变量名必须对有效 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] ; 这些名称必须以字母字符或下划线开头，并包含字母字符、数字或下划线。</span><span class="sxs-lookup"><span data-stu-id="5a8a6-165">Variable names must be valid for [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]; they must start with alphabetical character or underscore and contain alphabetical characters, digits, or underscores.</span></span> <span data-ttu-id="5a8a6-166">不能将保留字用作变量名。</span><span class="sxs-lookup"><span data-stu-id="5a8a6-166">Reserved words cannot be used as variable names.</span></span> <span data-ttu-id="5a8a6-167">有关使用全局变量的详细信息，请参阅[表达式中的内置集合（报表生成器和 SSRS）](../report-design/built-in-collections-in-expressions-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="5a8a6-167">For more information about using global variables, see [Built-in Collections in Expressions &#40;Report Builder and SSRS&#41;](../report-design/built-in-collections-in-expressions-report-builder.md).</span></span>  
  
 <span data-ttu-id="5a8a6-168">**-t**</span><span class="sxs-lookup"><span data-stu-id="5a8a6-168">**-t**</span></span>  
 <span data-ttu-id="5a8a6-169">（可选）将错误信息输出到跟踪日志中。</span><span class="sxs-lookup"><span data-stu-id="5a8a6-169">(Optional) Outputs error messages to the trace log.</span></span> <span data-ttu-id="5a8a6-170">此参数不带值。</span><span class="sxs-lookup"><span data-stu-id="5a8a6-170">This argument does not take a value.</span></span> <span data-ttu-id="5a8a6-171">有关详细信息，请参阅 [Report Server Service Trace Log](../report-server/report-server-service-trace-log.md)。</span><span class="sxs-lookup"><span data-stu-id="5a8a6-171">For more information, see [Report Server Service Trace Log](../report-server/report-server-service-trace-log.md).</span></span>  
  
##  <a name="permissions"></a><a name="bkmk_permissions"></a> <span data-ttu-id="5a8a6-172">权限</span><span class="sxs-lookup"><span data-stu-id="5a8a6-172">Permissions</span></span>  
 <span data-ttu-id="5a8a6-173">若要运行该工具，必须拥有与运行脚本的报表服务器实例连接的权限。</span><span class="sxs-lookup"><span data-stu-id="5a8a6-173">To run the tool, you must have permission to connect to the report server instance you are running the script against.</span></span> <span data-ttu-id="5a8a6-174">可以运行脚本来更改本地计算机或远程计算机。</span><span class="sxs-lookup"><span data-stu-id="5a8a6-174">You can run scripts to make changes to the local computer or a remote computer.</span></span> <span data-ttu-id="5a8a6-175">若要更改远程计算机上的报表服务器，请在 `-s` 参数中指定远程计算机。</span><span class="sxs-lookup"><span data-stu-id="5a8a6-175">To make changes to a report server installed on a remote computer, specify the remote computer in the `-s` argument.</span></span>  
  
##  <a name="examples"></a><a name="bkmk_examples"></a> <span data-ttu-id="5a8a6-176">示例</span><span class="sxs-lookup"><span data-stu-id="5a8a6-176">Examples</span></span>  
 <span data-ttu-id="5a8a6-177">下面的示例说明如何指定包含 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] .NET 脚本的脚本文件以及要执行的 Web 服务方法。</span><span class="sxs-lookup"><span data-stu-id="5a8a6-177">The following example illustrates how to specify the script file that contains [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] .NET script and Web service methods that you want to execute.</span></span>  
  
```  
rs -i c:\scriptfiles\script_copycontent.rss -s http://localhost/reportserver  
```  
  
 <span data-ttu-id="5a8a6-178"> 有关详细示例，请参阅 [Sample Reporting Services rs.exe Script to Migrate Content between Report Servers](sample-reporting-services-rs-exe-script-to-copy-content-between-report-servers.md)。</span><span class="sxs-lookup"><span data-stu-id="5a8a6-178">For a detailed example, see [Sample Reporting Services rs.exe Script to Migrate Content between Report Servers](sample-reporting-services-rs-exe-script-to-copy-content-between-report-servers.md).</span></span>  
  
 <span data-ttu-id="5a8a6-179">有关其他示例，请参阅 [运行 Reporting Services 脚本文件](run-a-reporting-services-script-file.md)</span><span class="sxs-lookup"><span data-stu-id="5a8a6-179">For additional examples, see [Run a Reporting Services Script File](run-a-reporting-services-script-file.md)</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5a8a6-180">备注</span><span class="sxs-lookup"><span data-stu-id="5a8a6-180">Remarks</span></span>  
 <span data-ttu-id="5a8a6-181">可以定义脚本来设置系统属性，发布报表，等等。</span><span class="sxs-lookup"><span data-stu-id="5a8a6-181">You can define scripts to set system properties, publish reports, and so forth.</span></span> <span data-ttu-id="5a8a6-182">所创建的脚本可以包含 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] API 的任何方法。</span><span class="sxs-lookup"><span data-stu-id="5a8a6-182">The scripts that you create can include any methods of the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] API.</span></span> <span data-ttu-id="5a8a6-183">有关可以使用的方法和属性的详细信息，请参阅 [Report Server Web Service](../report-server-web-service/report-server-web-service.md)。</span><span class="sxs-lookup"><span data-stu-id="5a8a6-183">For more information about the methods and properties available to you, see [Report Server Web Service](../report-server-web-service/report-server-web-service.md).</span></span>  
  
 <span data-ttu-id="5a8a6-184">必须用 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] .NET 代码编写脚本，并存储在文件扩展名为 .rss 的 Unicode 或 UTF-8 文本文件中。</span><span class="sxs-lookup"><span data-stu-id="5a8a6-184">The script must be written in [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] .NET code, and stored in a Unicode or UTF-8 text file with an .rss file name extension.</span></span> <span data-ttu-id="5a8a6-185">不能使用 **rs** 实用工具调试脚本。</span><span class="sxs-lookup"><span data-stu-id="5a8a6-185">You cannot debug scripts with the **rs** utility.</span></span> <span data-ttu-id="5a8a6-186">若要调试脚本，请在中运行代码 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="5a8a6-186">To debug a script, run the code within [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="5a8a6-187"> 有关详细示例，请参阅 [Sample Reporting Services rs.exe Script to Migrate Content between Report Servers](sample-reporting-services-rs-exe-script-to-copy-content-between-report-servers.md)。</span><span class="sxs-lookup"><span data-stu-id="5a8a6-187">For a detailed example, see [Sample Reporting Services rs.exe Script to Migrate Content between Report Servers](sample-reporting-services-rs-exe-script-to-copy-content-between-report-servers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a8a6-188">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5a8a6-188">See Also</span></span>  
 <span data-ttu-id="5a8a6-189">[运行 Reporting Services 脚本文件](run-a-reporting-services-script-file.md) </span><span class="sxs-lookup"><span data-stu-id="5a8a6-189">[Run a Reporting Services Script File](run-a-reporting-services-script-file.md) </span></span>  
 <span data-ttu-id="5a8a6-190">[为部署和管理任务编写脚本](script-deployment-and-administrative-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="5a8a6-190">[Script Deployment and Administrative Tasks](script-deployment-and-administrative-tasks.md) </span></span>  
 <span data-ttu-id="5a8a6-191">[用 rs.exe 实用工具和 Web 服务编写脚本](script-with-the-rs-exe-utility-and-the-web-service.md) </span><span class="sxs-lookup"><span data-stu-id="5a8a6-191">[Script with the rs.exe Utility and the Web Service](script-with-the-rs-exe-utility-and-the-web-service.md) </span></span>  
 [<span data-ttu-id="5a8a6-192">报表服务器命令提示实用工具 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="5a8a6-192">Report Server Command Prompt Utilities &#40;SSRS&#41;</span></span>](report-server-command-prompt-utilities-ssrs.md)  
  
  
