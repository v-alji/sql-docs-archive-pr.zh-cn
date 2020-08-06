---
title: 探查器实用工具 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- command prompt utilities [SQL Server], profiler90 utility
- profiler90 utility
- Profiler [SQL Server Profiler], starting
- SQL Server Profiler, starting
- starting SQL Server Profiler
ms.assetid: e91c30a9-0d29-4f84-bcb8-e8fb62afadda
author: stevestein
ms.author: sstein
ms.openlocfilehash: a8df3e8557bb52839d17291bae0c5ba507d0a671
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682515"
---
# <a name="profiler-utility"></a><span data-ttu-id="c639a-102">Profiler 实用工具</span><span class="sxs-lookup"><span data-stu-id="c639a-102">Profiler Utility</span></span>
  <span data-ttu-id="c639a-103">**Profiler** 实用工具可以启动 [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] 工具。</span><span class="sxs-lookup"><span data-stu-id="c639a-103">The **profiler** utility launches the [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] tool.</span></span> <span data-ttu-id="c639a-104">利用此主题后面列出的可选参数，可以控制应用程序的启动方式。</span><span class="sxs-lookup"><span data-stu-id="c639a-104">The optional arguments listed later in this topic allow you to control how the application starts.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c639a-105">**Profiler** 实用工具不适用于脚本跟踪。</span><span class="sxs-lookup"><span data-stu-id="c639a-105">The **profiler** utility is not intended for scripting traces.</span></span> <span data-ttu-id="c639a-106">有关详细信息，请参阅 [SQL Server Profiler](sql-server-profiler/sql-server-profiler.md)。</span><span class="sxs-lookup"><span data-stu-id="c639a-106">For more information, see [SQL Server Profiler](sql-server-profiler/sql-server-profiler.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c639a-107">语法</span><span class="sxs-lookup"><span data-stu-id="c639a-107">Syntax</span></span>  
  
```  
  
      profiler  
          [ /? ] |  
[  
{  
{ /U login_id [ /P password ] }  
| /E  
}  
{[ /S sql_server_name ] | [ /A analysis_services_server_name ] }  
[ /D database ]  
[ /T "template_name" ]  
[ /B { "trace_table_name" } ]  
{ [/F "filename" ] | [ /O "filename" ] }  
[ /L locale_ID ]  
[ /M "MM-DD-YY hh:mm:ss" ]  
[ /R ]  
[ /Z file_size ]  
]  
```  
  
## <a name="arguments"></a><span data-ttu-id="c639a-108">参数</span><span class="sxs-lookup"><span data-stu-id="c639a-108">Arguments</span></span>  
 <span data-ttu-id="c639a-109">**/?**</span><span class="sxs-lookup"><span data-stu-id="c639a-109">**/?**</span></span>  
 <span data-ttu-id="c639a-110">显示 **Profiler** 自变量的语法摘要。</span><span class="sxs-lookup"><span data-stu-id="c639a-110">Displays the syntax summary of **profiler** arguments.</span></span>  
  
 <span data-ttu-id="c639a-111">**/U** *login_id*</span><span class="sxs-lookup"><span data-stu-id="c639a-111">**/U** *login_id*</span></span>  
 <span data-ttu-id="c639a-112">用于 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 身份验证的用户登录 ID。</span><span class="sxs-lookup"><span data-stu-id="c639a-112">Is the user login ID for [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="c639a-113">登录 ID 区分大小写。</span><span class="sxs-lookup"><span data-stu-id="c639a-113">Login IDs are case sensitive.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteWinAuthentication](../includes/ssnotewinauthentication-md.md)]<span data-ttu-id="c639a-114">.</span><span class="sxs-lookup"><span data-stu-id="c639a-114">.</span></span>  
  
 <span data-ttu-id="c639a-115">**/P** *password*</span><span class="sxs-lookup"><span data-stu-id="c639a-115">**/P** *password*</span></span>  
 <span data-ttu-id="c639a-116">指定用户指定的用于 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 身份验证的密码。</span><span class="sxs-lookup"><span data-stu-id="c639a-116">Specifies a user-specified password for [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
 <span data-ttu-id="c639a-117">**/E**</span><span class="sxs-lookup"><span data-stu-id="c639a-117">**/E**</span></span>  
 <span data-ttu-id="c639a-118">指定使用当前用户的凭据与 Windows 身份验证连接。</span><span class="sxs-lookup"><span data-stu-id="c639a-118">Specifies connecting with Windows Authentication with the current user's credentials.</span></span>  
  
 <span data-ttu-id="c639a-119">**/S**  *sql_server_name*</span><span class="sxs-lookup"><span data-stu-id="c639a-119">**/S**  *sql_server_name*</span></span>  
 <span data-ttu-id="c639a-120">指定一个 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]实例。</span><span class="sxs-lookup"><span data-stu-id="c639a-120">Specifies an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="c639a-121">Profiler 会使用在 **/U** 和 **/P** 开关或 **/E** 开关中指定的身份验证信息，自动连接到指定的服务器。</span><span class="sxs-lookup"><span data-stu-id="c639a-121">Profiler will automatically connect to the specified server using the authentication information specified in the **/U** and **/P** switches or the **/E** switch.</span></span> <span data-ttu-id="c639a-122">若要连接到 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的命名实例，请使用 **/S** *sql_server_name*\\*instance_name*。</span><span class="sxs-lookup"><span data-stu-id="c639a-122">To connect to a named instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], use **/S** *sql_server_name*\\*instance_name*.</span></span>  
  
 <span data-ttu-id="c639a-123">**/A**  *analysis_services_server_name*</span><span class="sxs-lookup"><span data-stu-id="c639a-123">**/A**  *analysis_services_server_name*</span></span>  
 <span data-ttu-id="c639a-124">指定一个 Analysis Services 实例。</span><span class="sxs-lookup"><span data-stu-id="c639a-124">Specifies an instance of Analysis Services.</span></span> <span data-ttu-id="c639a-125">Profiler 会使用在 **/U** 和 **/P** 开关或 **/E** 开关中指定的身份验证信息，自动连接到指定的服务器。</span><span class="sxs-lookup"><span data-stu-id="c639a-125">Profiler will automatically connect to the specified server using the authentication information specified in the **/U** and **/P** switches or the **/E** switch.</span></span> <span data-ttu-id="c639a-126">若要连接到 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的命名实例，请使用 **/A** *analysis_services_server_name\instance_name*。</span><span class="sxs-lookup"><span data-stu-id="c639a-126">To connect to a named instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] use **/A** *analysis_services_server_name\instance_name*.</span></span>  
  
 <span data-ttu-id="c639a-127">**/D** *database*</span><span class="sxs-lookup"><span data-stu-id="c639a-127">**/D** *database*</span></span>  
 <span data-ttu-id="c639a-128">指定要用于连接的数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="c639a-128">Specifies the name of the database to be used with the connection.</span></span> <span data-ttu-id="c639a-129">如果不指定任何数据库，该选项将为指定的用户选择默认数据库。</span><span class="sxs-lookup"><span data-stu-id="c639a-129">This option will select the default database for the specified user if no database is specified.</span></span>  
  
 <span data-ttu-id="c639a-130">**/B "** *trace_table_name* **"**</span><span class="sxs-lookup"><span data-stu-id="c639a-130">**/B "** *trace_table_name* **"**</span></span>  
 <span data-ttu-id="c639a-131">指定要在事件探查器启动时加载的跟踪表。</span><span class="sxs-lookup"><span data-stu-id="c639a-131">Specifies a trace table to load when the profiler is launched.</span></span> <span data-ttu-id="c639a-132">必须指定数据库、用户或架构以及表。</span><span class="sxs-lookup"><span data-stu-id="c639a-132">You must specify the database, the user or schema, and the table.</span></span>  
  
 <span data-ttu-id="c639a-133">**/T"** *template_name* **"**</span><span class="sxs-lookup"><span data-stu-id="c639a-133">**/T"** *template_name* **"**</span></span>  
 <span data-ttu-id="c639a-134">指定要加载以便配置跟踪的模板。</span><span class="sxs-lookup"><span data-stu-id="c639a-134">Specifies the template that will be loaded to configure the trace.</span></span> <span data-ttu-id="c639a-135">模板名称必须括在引号中。</span><span class="sxs-lookup"><span data-stu-id="c639a-135">The template name must be in quotes.</span></span> <span data-ttu-id="c639a-136">模板名称必须位于系统模板目录或用户模板目录下。</span><span class="sxs-lookup"><span data-stu-id="c639a-136">The template name must be in either the system template directory or the user template directory.</span></span> <span data-ttu-id="c639a-137">如果这两个目录中同时存在同名的两个模板，则将加载系统目录下的模板。</span><span class="sxs-lookup"><span data-stu-id="c639a-137">If two templates with the same name exist in both directories, the template from the system directory will be loaded.</span></span> <span data-ttu-id="c639a-138">如果不存在具有指定名称的模板，则将加载标准模板。</span><span class="sxs-lookup"><span data-stu-id="c639a-138">If no template with the specified name exists, the standard template will be loaded.</span></span> <span data-ttu-id="c639a-139">请注意，模板的文件扩展名 (.tdf) 不能指定为 *template_name*的一部分。</span><span class="sxs-lookup"><span data-stu-id="c639a-139">Note that the file extension for the template (.tdf) should not be specified as part of the *template_name*.</span></span> <span data-ttu-id="c639a-140">例如：</span><span class="sxs-lookup"><span data-stu-id="c639a-140">For example:</span></span>  
  
```  
/T "standard"  
```  
  
 <span data-ttu-id="c639a-141">**/F"** *filename* **"**</span><span class="sxs-lookup"><span data-stu-id="c639a-141">**/F"** *filename* **"**</span></span>  
 <span data-ttu-id="c639a-142">指定要在事件探查器启动时加载的跟踪文件的路径和文件名。</span><span class="sxs-lookup"><span data-stu-id="c639a-142">Specifies the path and filename of a trace file to load when profiler is launched.</span></span> <span data-ttu-id="c639a-143">整个路径和文件名必须置于引号中。</span><span class="sxs-lookup"><span data-stu-id="c639a-143">The entire path and filename must be in quotes.</span></span> <span data-ttu-id="c639a-144">此选项不能与 **/O**一起使用。</span><span class="sxs-lookup"><span data-stu-id="c639a-144">This option cannot be used with **/O**.</span></span>  
  
 <span data-ttu-id="c639a-145">**/O "** *filename*  **"**</span><span class="sxs-lookup"><span data-stu-id="c639a-145">**/O "** *filename*  **"**</span></span>  
 <span data-ttu-id="c639a-146">指定应在其中写入跟踪结果的文件的路径和文件名。</span><span class="sxs-lookup"><span data-stu-id="c639a-146">Specifies the path and filename of a file to which trace results should be written.</span></span> <span data-ttu-id="c639a-147">整个路径和文件名必须置于引号中。</span><span class="sxs-lookup"><span data-stu-id="c639a-147">The entire path and filename must be in quotes.</span></span> <span data-ttu-id="c639a-148">此选项不能与 **/F.** 一起使用。</span><span class="sxs-lookup"><span data-stu-id="c639a-148">This option cannot be used with **/F.**</span></span>  
  
 <span data-ttu-id="c639a-149">**/L** *locale_ID*</span><span class="sxs-lookup"><span data-stu-id="c639a-149">**/L** *locale_ID*</span></span>  
 <span data-ttu-id="c639a-150">不可用。</span><span class="sxs-lookup"><span data-stu-id="c639a-150">Not available.</span></span>  
  
 <span data-ttu-id="c639a-151">**/M "** *MM-DD-YY hh:mm:ss* **"**</span><span class="sxs-lookup"><span data-stu-id="c639a-151">**/M "** *MM-DD-YY hh:mm:ss* **"**</span></span>  
 <span data-ttu-id="c639a-152">指定跟踪停止的日期和时间。</span><span class="sxs-lookup"><span data-stu-id="c639a-152">Specifies the date and time for the trace to stop.</span></span> <span data-ttu-id="c639a-153">停止时间必须括在引号中。</span><span class="sxs-lookup"><span data-stu-id="c639a-153">The stop time must be in quotes.</span></span> <span data-ttu-id="c639a-154">根据下表中的参数指定停止时间：</span><span class="sxs-lookup"><span data-stu-id="c639a-154">Specify the stop time according to the parameters in the table below:</span></span>  
  
|<span data-ttu-id="c639a-155">参数</span><span class="sxs-lookup"><span data-stu-id="c639a-155">Parameter</span></span>|<span data-ttu-id="c639a-156">定义</span><span class="sxs-lookup"><span data-stu-id="c639a-156">Definition</span></span>|  
|---------------|----------------|  
|<span data-ttu-id="c639a-157">MM</span><span class="sxs-lookup"><span data-stu-id="c639a-157">MM</span></span>|<span data-ttu-id="c639a-158">两位数月份</span><span class="sxs-lookup"><span data-stu-id="c639a-158">Two-digit month</span></span>|  
|<span data-ttu-id="c639a-159">DD</span><span class="sxs-lookup"><span data-stu-id="c639a-159">DD</span></span>|<span data-ttu-id="c639a-160">两位数日期</span><span class="sxs-lookup"><span data-stu-id="c639a-160">Two-digit day</span></span>|  
|<span data-ttu-id="c639a-161">YY</span><span class="sxs-lookup"><span data-stu-id="c639a-161">YY</span></span>|<span data-ttu-id="c639a-162">两位数年份</span><span class="sxs-lookup"><span data-stu-id="c639a-162">Two-digit year</span></span>|  
|<span data-ttu-id="c639a-163">hh</span><span class="sxs-lookup"><span data-stu-id="c639a-163">hh</span></span>|<span data-ttu-id="c639a-164">24 小时制的两位数小时</span><span class="sxs-lookup"><span data-stu-id="c639a-164">Two-digit hour on a 24-hour clock</span></span>|  
|<span data-ttu-id="c639a-165">mm</span><span class="sxs-lookup"><span data-stu-id="c639a-165">mm</span></span>|<span data-ttu-id="c639a-166">两位数分钟</span><span class="sxs-lookup"><span data-stu-id="c639a-166">Two-digit minute</span></span>|  
|<span data-ttu-id="c639a-167">ss</span><span class="sxs-lookup"><span data-stu-id="c639a-167">ss</span></span>|<span data-ttu-id="c639a-168">两位数秒数</span><span class="sxs-lookup"><span data-stu-id="c639a-168">Two-digit second</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="c639a-169">仅当在 [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] 中启用了“使用区域设置来显示日期和时间值”选项时，才能使用“YY-MM-DD- hh:mm:ss”格式。</span><span class="sxs-lookup"><span data-stu-id="c639a-169">The "MM-DD-YY hh:mm:ss" format can only be used if the **Use regional settings to display date and time values** option is enabled in [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)].</span></span> <span data-ttu-id="c639a-170">如果未启用此选项，则必须使用“YYYY-MM-DD hh:mm:ss”日期和时间格式。</span><span class="sxs-lookup"><span data-stu-id="c639a-170">If this option is not enabled, you must use the "YYYY-MM-DD hh:mm:ss" date and time format.</span></span>  
  
 <span data-ttu-id="c639a-171">**/R**</span><span class="sxs-lookup"><span data-stu-id="c639a-171">**/R**</span></span>  
 <span data-ttu-id="c639a-172">启用跟踪文件滚动。</span><span class="sxs-lookup"><span data-stu-id="c639a-172">Enables trace file rollover.</span></span>  
  
 <span data-ttu-id="c639a-173">**/Z**  *file_size*</span><span class="sxs-lookup"><span data-stu-id="c639a-173">**/Z**  *file_size*</span></span>  
 <span data-ttu-id="c639a-174">指定跟踪文件的大小（以兆字节 (MB) 为单位）。</span><span class="sxs-lookup"><span data-stu-id="c639a-174">Specifies the size of the trace file in megabytes (MB).</span></span> <span data-ttu-id="c639a-175">默认大小是 5 MB。</span><span class="sxs-lookup"><span data-stu-id="c639a-175">The default size is 5 MB.</span></span> <span data-ttu-id="c639a-176">若启用了滚动功能，则所有滚动文件的大小将被限制为此参数所指定的值。</span><span class="sxs-lookup"><span data-stu-id="c639a-176">If rollover is enabled, all rollover files will be limited to the value specified in this argument.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c639a-177">备注</span><span class="sxs-lookup"><span data-stu-id="c639a-177">Remarks</span></span>  
 <span data-ttu-id="c639a-178">若要使用特定的模板启动跟踪，请同时使用 **/S** 和 **/T** 选项。</span><span class="sxs-lookup"><span data-stu-id="c639a-178">To start a trace with a specific template, use the **/S** and **/T** options together.</span></span> <span data-ttu-id="c639a-179">例如，若要使用 MyServer\MyInstance 上的 Standard 模板启动跟踪，请在命令提示符处输入以下内容：</span><span class="sxs-lookup"><span data-stu-id="c639a-179">For example, to start a trace using the Standard template on MyServer\MyInstance, enter the following at the command prompt:</span></span>  
  
```  
profiler /S MyServer\MyInstance /T "Standard"  
```  
  
## <a name="see-also"></a><span data-ttu-id="c639a-180">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c639a-180">See Also</span></span>  
 [<span data-ttu-id="c639a-181">命令提示实用工具参考（数据库引擎）</span><span class="sxs-lookup"><span data-stu-id="c639a-181">Command Prompt Utility Reference &#40;Database Engine&#41;</span></span>](command-prompt-utility-reference-database-engine.md)  
  
  
