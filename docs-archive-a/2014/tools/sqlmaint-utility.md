---
title: sqlmaint 实用程序 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- database maintenance plans [SQL Server]
- sqlmaint utility
- maintaining databases [SQL Server]
- backups [SQL Server], sqlmaint utility
- command prompt utilities [SQL Server], sqlmaint
- maintenance plans [SQL Server], command prompt
- backing up [SQL Server], sqlmaint utility
ms.assetid: 937a9932-4aed-464b-b97a-a5acfe6a50de
author: stevestein
ms.author: sstein
ms.openlocfilehash: 80e60b75305ee91e8b62a201d9c86af301326789
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682477"
---
# <a name="sqlmaint-utility"></a><span data-ttu-id="09af7-102">sqlmaint 实用工具</span><span class="sxs-lookup"><span data-stu-id="09af7-102">sqlmaint Utility</span></span>
  <span data-ttu-id="09af7-103">如果成功运行，则**sqlmaint** 实用工具可以对一个或多个数据库执行一组指定的维护操作。</span><span class="sxs-lookup"><span data-stu-id="09af7-103">The**sqlmaint** utility performs a specified set of maintenance operations on one or more databases.</span></span> <span data-ttu-id="09af7-104">使用 **sqlmaint** 可以运行 DBCC 检查、备份数据库及其事务日志、更新统计信息以及重新生成索引。</span><span class="sxs-lookup"><span data-stu-id="09af7-104">Use **sqlmaint** to run DBCC checks, back up a database and its transaction log, update statistics, and rebuild indexes.</span></span> <span data-ttu-id="09af7-105">所有数据库维护活动都会生成报表，可以将此报表发送到指定的文本文件、HTML 文件或电子邮件帐户。</span><span class="sxs-lookup"><span data-stu-id="09af7-105">All database maintenance activities generate a report that can be sent to a designated text file, HTML file, or e-mail account.</span></span> <span data-ttu-id="09af7-106">**sqlmaint** 可以执行使用早期版本的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]创建的数据库维护计划。</span><span class="sxs-lookup"><span data-stu-id="09af7-106">**sqlmaint** executes database maintenance plans created with previous versions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="09af7-107">若要从命令提示符运行 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 维护计划，请使用 [dtexec 实用工具](../integration-services/packages/dtexec-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="09af7-107">To run [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] maintenance plans from the command prompt, use the [dtexec Utility](../integration-services/packages/dtexec-utility.md).</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepNextAvoid](../includes/ssnotedepnextavoid-md.md)] <span data-ttu-id="09af7-108">将使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 维护计划功能代替此实用工具。</span><span class="sxs-lookup"><span data-stu-id="09af7-108">Use [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] maintenance plan feature instead.</span></span> <span data-ttu-id="09af7-109">有关维护计划的详细信息，请参阅 [维护计划](../relational-databases/maintenance-plans/maintenance-plans.md)。</span><span class="sxs-lookup"><span data-stu-id="09af7-109">For more information on maintenance plans, see [Maintenance Plans](../relational-databases/maintenance-plans/maintenance-plans.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09af7-110">语法</span><span class="sxs-lookup"><span data-stu-id="09af7-110">Syntax</span></span>  
  
```  
  
      sqlmaint   
[-?] |  
[  
     [-Sserver_name[\instance_name]]  
     [-Ulogin_ID [-Ppassword]]  
     {  
          [-Ddatabase_name | -PlanNamename | -PlanIDguid ]  
          [-Rpttext_file]  
          [-Tooperator_name]  
          [-HtmlRpthtml_file [-DelHtmlRpt <time_period>] ]  
          [-RmUnusedSpacethreshold_percentfree_percent]  
          [-CkDB | -CkDBNoIdx]  
          [-CkAl | -CkAlNoIdx]  
          [-CkCat]  
          [-UpdOptiStatssample_percent]  
          [-RebldIdxfree_space]  
          [-SupportComputedColumn]  
          [-WriteHistory]  
          [  
               {-BkUpDB [backup_path] | -BkUpLog [backup_path] }  
               {-BkUpMedia  
                    {DISK [  
                           [-DelBkUps<time_period>]   
                           [-CrBkSubDir ]   
                           [-UseDefDir ]   
                          ]  
                     | TAPE   
                    }  
               }  
               [-BkUpOnlyIfClean]  
               [-VrfyBackup]  
          ]  
     }  
]  
<time_period> ::=  
number[minutes | hours | days | weeks | months]  
```  
  
## <a name="arguments"></a><span data-ttu-id="09af7-111">参数</span><span class="sxs-lookup"><span data-stu-id="09af7-111">Arguments</span></span>  
 <span data-ttu-id="09af7-112">参数与其值之间必须用一个空格分隔。</span><span class="sxs-lookup"><span data-stu-id="09af7-112">The parameters and their values must be separated by a space.</span></span> <span data-ttu-id="09af7-113">例如，在 **-S** 和 *server_name*之间必须留一个空格。</span><span class="sxs-lookup"><span data-stu-id="09af7-113">For example, there must be a space between **-S** and *server_name*.</span></span>  
  
 <span data-ttu-id="09af7-114">**-?**</span><span class="sxs-lookup"><span data-stu-id="09af7-114">**-?**</span></span>  
 <span data-ttu-id="09af7-115">指定返回 **sqlmaint** 的语法关系图。</span><span class="sxs-lookup"><span data-stu-id="09af7-115">Specifies that the syntax diagram for **sqlmaint** be returned.</span></span> <span data-ttu-id="09af7-116">此参数必须单独使用。</span><span class="sxs-lookup"><span data-stu-id="09af7-116">This parameter must be used alone.</span></span>  
  
 <span data-ttu-id="09af7-117">**-S** _server_name_[ **\\** _instance_name_]</span><span class="sxs-lookup"><span data-stu-id="09af7-117">**-S** _server_name_[ **\\**_instance_name_]</span></span>  
 <span data-ttu-id="09af7-118">指定 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的目标实例。</span><span class="sxs-lookup"><span data-stu-id="09af7-118">Specifies the target instance of [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="09af7-119">指定要连接到该服务器上 *默认实例的* server_name [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="09af7-119">Specify *server_name* to connect to the default instance of [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] on that server.</span></span> <span data-ttu-id="09af7-120">指定要连接到该服务器上的命名实例*server_name **_\\_** instance_name* [!INCLUDE[ssDE](../includes/ssde-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="09af7-120">Specify *server_name\*\*_\\_*\* instance_name\* to connect to a named instance of [!INCLUDE[ssDE](../includes/ssde-md.md)] on that server.</span></span> <span data-ttu-id="09af7-121">如果未指定服务器， **sqlmaint** 将连接到本地计算机上的 [!INCLUDE[ssDE](../includes/ssde-md.md)] 默认实例。</span><span class="sxs-lookup"><span data-stu-id="09af7-121">If no server is specified, **sqlmaint** connects to the default instance of [!INCLUDE[ssDE](../includes/ssde-md.md)] on the local computer.</span></span>  
  
 <span data-ttu-id="09af7-122">**-U** _login_ID_</span><span class="sxs-lookup"><span data-stu-id="09af7-122">**-U** _login_ID_</span></span>  
 <span data-ttu-id="09af7-123">指定连接服务器时使用的登录 ID。</span><span class="sxs-lookup"><span data-stu-id="09af7-123">Specifies the login ID to use when connecting to the server.</span></span> <span data-ttu-id="09af7-124">如果未提供， **sqlmaint** 将尝试使用 [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows 身份验证。</span><span class="sxs-lookup"><span data-stu-id="09af7-124">If not supplied, **sqlmaint** attempts to use [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows Authentication.</span></span> <span data-ttu-id="09af7-125">如果 *login_ID* 包含特殊字符，则必须用双引号 (") 引起来；否则，双引号为可选。</span><span class="sxs-lookup"><span data-stu-id="09af7-125">If *login_ID* contains special characters, it must be enclosed in double quotation marks ("); otherwise, the double quotation marks are optional.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="09af7-126">请尽可能使用 Windows 身份验证。</span><span class="sxs-lookup"><span data-stu-id="09af7-126">When possible, use Windows Authentication.</span></span>  
  
 <span data-ttu-id="09af7-127">**-P** _password_</span><span class="sxs-lookup"><span data-stu-id="09af7-127">**-P** _password_</span></span>  
 <span data-ttu-id="09af7-128">指定登录 ID 的密码。</span><span class="sxs-lookup"><span data-stu-id="09af7-128">Specifies the password for the login ID.</span></span> <span data-ttu-id="09af7-129">仅在同时提供 **-U** 参数时有效。</span><span class="sxs-lookup"><span data-stu-id="09af7-129">Only valid if the **-U** parameter is also supplied.</span></span> <span data-ttu-id="09af7-130">如果 *password* 包含特殊字符，则必须用双引号引起来；否则，双引号为可选。</span><span class="sxs-lookup"><span data-stu-id="09af7-130">If *password* contains special characters, it must be enclosed in double quotation marks; otherwise, the double quotation marks are optional.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="09af7-131">密码不屏蔽。</span><span class="sxs-lookup"><span data-stu-id="09af7-131">The password is not masked.</span></span> <span data-ttu-id="09af7-132">请尽可能使用 Windows 身份验证。</span><span class="sxs-lookup"><span data-stu-id="09af7-132">When possible, use Windows Authentication.</span></span>  
  
 <span data-ttu-id="09af7-133">**-D** _database_name_</span><span class="sxs-lookup"><span data-stu-id="09af7-133">**-D** _database_name_</span></span>  
 <span data-ttu-id="09af7-134">指定要在其中执行维护操作的数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="09af7-134">Specifies the name of the database in which to perform the maintenance operation.</span></span> <span data-ttu-id="09af7-135">如果 *database_name* 包含特殊字符，则必须用双引号引起来；否则，双引号为可选。</span><span class="sxs-lookup"><span data-stu-id="09af7-135">If *database_name* contains special characters, it must be enclosed in double quotation marks; otherwise, the double quotation marks are optional.</span></span>  
  
 <span data-ttu-id="09af7-136">**-PlanName** _name_</span><span class="sxs-lookup"><span data-stu-id="09af7-136">**-PlanName** _name_</span></span>  
 <span data-ttu-id="09af7-137">指定使用数据库维护计划向导定义的数据库维护计划的名称。</span><span class="sxs-lookup"><span data-stu-id="09af7-137">Specifies the name of a database maintenance plan defined using the Database Maintenance Plan Wizard.</span></span> <span data-ttu-id="09af7-138">**sqlmaint** 仅使用该计划中的数据库列表信息。</span><span class="sxs-lookup"><span data-stu-id="09af7-138">The only information **sqlmaint** uses from the plan is the list of the databases in the plan.</span></span> <span data-ttu-id="09af7-139">在其他 **sqlmaint** 参数中指定的任何维护活动都会应用到此数据库列表。</span><span class="sxs-lookup"><span data-stu-id="09af7-139">Any maintenance activities you specify in the other **sqlmaint** parameters are applied to this list of databases.</span></span>  
  
 <span data-ttu-id="09af7-140">**-PlanID** _guid_</span><span class="sxs-lookup"><span data-stu-id="09af7-140">**-PlanID** _guid_</span></span>  
 <span data-ttu-id="09af7-141">指定使用数据库维护计划向导定义的数据库维护计划的全局唯一标识符 (GUID)。</span><span class="sxs-lookup"><span data-stu-id="09af7-141">Specifies the globally unique identifier (GUID) of a database maintenance plan defined using the Database Maintenance Plan Wizard.</span></span> <span data-ttu-id="09af7-142">**sqlmaint** 仅使用该计划中的数据库列表信息。</span><span class="sxs-lookup"><span data-stu-id="09af7-142">The only information **sqlmaint** uses from the plan is the list of the databases in the plan.</span></span> <span data-ttu-id="09af7-143">在其他 **sqlmaint** 参数中指定的任何维护活动都会应用到此数据库列表。</span><span class="sxs-lookup"><span data-stu-id="09af7-143">Any maintenance activities you specify in the other **sqlmaint** parameters are applied to this list of databases.</span></span> <span data-ttu-id="09af7-144">这必须与 msdb.dbo.sysdbmaintplans 中的 plan_id 值匹配。</span><span class="sxs-lookup"><span data-stu-id="09af7-144">This must match a plan_id value in msdb.dbo.sysdbmaintplans.</span></span>  
  
 <span data-ttu-id="09af7-145">**-Rpt** _text_file_</span><span class="sxs-lookup"><span data-stu-id="09af7-145">**-Rpt** _text_file_</span></span>  
 <span data-ttu-id="09af7-146">指定包含要生成的报表的文件的完整路径和名称。</span><span class="sxs-lookup"><span data-stu-id="09af7-146">Specifies the full path and name of the file into which the report is to be generated.</span></span> <span data-ttu-id="09af7-147">报表也可在屏幕上生成。</span><span class="sxs-lookup"><span data-stu-id="09af7-147">The report is also generated on the screen.</span></span> <span data-ttu-id="09af7-148">报表通过在文件名中添加日期来维护版本信息。</span><span class="sxs-lookup"><span data-stu-id="09af7-148">The report maintains version information by adding a date to the file name.</span></span> <span data-ttu-id="09af7-149">日期是按以下格式生成的：在文件名末尾句点之前使用 _*yyyyMMddhhmm*格式。</span><span class="sxs-lookup"><span data-stu-id="09af7-149">The date is generated as follows: at the end of the file name but before the period, in the form _*yyyyMMddhhmm*.</span></span> <span data-ttu-id="09af7-150">*yyyy* = 年， *MM* = 月， *dd* = 日， *hh* = 小时， *mm* = 分钟。</span><span class="sxs-lookup"><span data-stu-id="09af7-150">*yyyy* = year, *MM* = month, *dd* = day, *hh* = hour, *mm* = minute.</span></span>  
  
 <span data-ttu-id="09af7-151">如果您在 1996 年 12 月 1 日上午 10:23 运行过该实用工具，</span><span class="sxs-lookup"><span data-stu-id="09af7-151">If you run the utility at 10:23 A.M.</span></span> <span data-ttu-id="09af7-152">在 1996 年 12 月 1 日， *text_file* 的值为：</span><span class="sxs-lookup"><span data-stu-id="09af7-152">on December 1, 1996, and this is the *text_file* value:</span></span>  
  
```  
c:\Program Files\Microsoft SQL Server\Mssql\Backup\AdventureWorks2012_maint.rpt  
```  
  
 <span data-ttu-id="09af7-153">则生成的文件名为：</span><span class="sxs-lookup"><span data-stu-id="09af7-153">The generated file name is:</span></span>  
  
```  
c:\Program Files\Microsoft SQL Server\Mssql\Backup\AdventureWorks2012_maint_199612011023.rpt  
```  
  
 <span data-ttu-id="09af7-154">*sqlmaint* 访问远程服务器时， **text_file** 需要完整的通用命名约定 (UNC) 文件名。</span><span class="sxs-lookup"><span data-stu-id="09af7-154">The full Universal Naming Convention (UNC) file name is required for *text_file* when **sqlmaint** accesses a remote server.</span></span>  
  
 <span data-ttu-id="09af7-155">**-要** _operator_name_</span><span class="sxs-lookup"><span data-stu-id="09af7-155">**-To** _operator_name_</span></span>  
 <span data-ttu-id="09af7-156">指定通过 SQL 邮件接收生成的报表的操作员。</span><span class="sxs-lookup"><span data-stu-id="09af7-156">Specifies the operator to whom the generated report is sent through SQL Mail.</span></span>  
  
 <span data-ttu-id="09af7-157">**-HtmlRpt** _html_file_</span><span class="sxs-lookup"><span data-stu-id="09af7-157">**-HtmlRpt** _html_file_</span></span>  
 <span data-ttu-id="09af7-158">指定 HTML 报表将生成到其中的文件的完整路径和名称。</span><span class="sxs-lookup"><span data-stu-id="09af7-158">Specifies the full path and name of the file into which an HTML report is to be generated.</span></span> <span data-ttu-id="09af7-159">**sqlmaint** 生成文件名的方式是在文件名中追加格式为 _*yyyyMMddhhmm* 的字符串，这与针对 **-Rpt** 参数的文件命名方式相同。</span><span class="sxs-lookup"><span data-stu-id="09af7-159">**sqlmaint** generates the file name by appending a string of the format _*yyyyMMddhhmm* to the file name, just as it does for the **-Rpt** parameter.</span></span>  
  
 <span data-ttu-id="09af7-160">*sqlmaint* 访问远程服务器时， **html_file** 需要完整的 UNC 文件名。</span><span class="sxs-lookup"><span data-stu-id="09af7-160">The full UNC file name is required for *html_file* when **sqlmaint** accesses a remote server.</span></span>  
  
 <span data-ttu-id="09af7-161">-DelHtmlRpt \<*time_period*></span><span class="sxs-lookup"><span data-stu-id="09af7-161">**-DelHtmlRpt** \<*time_period*></span></span>  
 <span data-ttu-id="09af7-162">指定报表文件创建后的时间间隔超出 \<*time_period*> 时，删除报表目录中的所有 HTML 报表。</span><span class="sxs-lookup"><span data-stu-id="09af7-162">Specifies that any HTML report in the report directory be deleted if the time interval after the creation of the report file exceeds \<*time_period*>.</span></span> <span data-ttu-id="09af7-163">**-DelHtmlRpt** 将查找名称符合由 *html_file* 参数生成的模式的文件。</span><span class="sxs-lookup"><span data-stu-id="09af7-163">**-DelHtmlRpt** looks for files whose name fits the pattern generated from the *html_file* parameter.</span></span> <span data-ttu-id="09af7-164">如果 html_file 为 c:\Program Files\Microsoft SQL Server\Mssql\Backup\AdventureWorks2012_maint.htm，则 -DelHtmlRpt 将导致 sqlmaint 删除任何名称与 C:\Program Files\Microsoft SQL Server\Mssql\Backup\AdventureWorks2012_maint\*.htm 模式匹配的文件，以及早于指定 \<*time_period*> 的文件。</span><span class="sxs-lookup"><span data-stu-id="09af7-164">If *html_file* is c:\Program Files\Microsoft SQL Server\Mssql\Backup\AdventureWorks2012_maint.htm, then **-DelHtmlRpt** causes **sqlmaint** to delete any files whose names match the pattern C:\Program Files\Microsoft SQL Server\Mssql\Backup\AdventureWorks2012_maint\*.htm and that are older than the specified \<*time_period*>.</span></span>  
  
 <span data-ttu-id="09af7-165">**-RmUnusedSpace** _threshold_percent free_percent_</span><span class="sxs-lookup"><span data-stu-id="09af7-165">**-RmUnusedSpace** _threshold_percent free_percent_</span></span>  
 <span data-ttu-id="09af7-166">指定从 **-D**. 指定的数据库中删除未使用的空间。</span><span class="sxs-lookup"><span data-stu-id="09af7-166">Specifies that unused space be removed from the database specified in **-D**.</span></span> <span data-ttu-id="09af7-167">该选项仅适用于定义为自动增长的数据库。</span><span class="sxs-lookup"><span data-stu-id="09af7-167">This option is only useful for databases that are defined to grow automatically.</span></span> <span data-ttu-id="09af7-168">*Threshold_percent* 指定在 **sqlmaint** 可以尝试删除未使用数据空间之前数据库必须达到的大小 (MB)。</span><span class="sxs-lookup"><span data-stu-id="09af7-168">*Threshold_percent* specifies in megabytes the size that the database must reach before **sqlmaint** attempts to remove unused data space.</span></span> <span data-ttu-id="09af7-169">如果数据库小于 *threshold_percent*，则不采取任何操作。</span><span class="sxs-lookup"><span data-stu-id="09af7-169">If the database is smaller than the *threshold_percent*, no action is taken.</span></span> <span data-ttu-id="09af7-170">*Free_percent* 指定数据库中必须保留的未使用空间的大小，以数据库最终大小的百分比表示。</span><span class="sxs-lookup"><span data-stu-id="09af7-170">*Free_percent* specifies how much unused space must remain in the database, specified as a percentage of the final size of the database.</span></span> <span data-ttu-id="09af7-171">例如，如果一个 200 MB 的数据库包含 100 MB 数据，则将 *free_percent* 指定为 10 将使数据库最终大小变为 110 MB。</span><span class="sxs-lookup"><span data-stu-id="09af7-171">For example, if a 200-MB database contains 100 MB of data, specifying 10 for *free_percent* results in the final database size being 110 MB.</span></span> <span data-ttu-id="09af7-172">请注意，如果数据库小于 *free_percent* 加上数据库中数据量的大小，则数据库不会扩展。</span><span class="sxs-lookup"><span data-stu-id="09af7-172">Note that a database is not expanded if it is smaller than *free_percent* plus the amount of data in the database.</span></span> <span data-ttu-id="09af7-173">例如，如果 108 MB 的数据库有 100 MB 数据，则将 *free_percent* 指定为 10 不会将数据库扩展为 110 MB，而是仍保持为 108 MB。</span><span class="sxs-lookup"><span data-stu-id="09af7-173">For example, if a 108-MB database has 100 MB of data, specifying 10 for *free_percent* does not expand the database to 110 MB; it remains at 108 MB.</span></span>  
  
 <span data-ttu-id="09af7-174">**-CkDB** |  **-CkDBNoIdx**</span><span class="sxs-lookup"><span data-stu-id="09af7-174">**-CkDB** | **-CkDBNoIdx**</span></span>  
 <span data-ttu-id="09af7-175">指定在 **-D**指定的数据库中运行 DBCC CHECKDB 语句或带 NOINDEX 选项的 DBCC CHECKDB 语句。</span><span class="sxs-lookup"><span data-stu-id="09af7-175">Specifies that a DBCC CHECKDB statement or a DBCC CHECKDB statement with the NOINDEX option be run in the database specified in **-D**.</span></span> <span data-ttu-id="09af7-176">有关详细信息，请参阅 DBCC CHECKDB。</span><span class="sxs-lookup"><span data-stu-id="09af7-176">For more information, see DBCC CHECKDB.</span></span>  
  
 <span data-ttu-id="09af7-177">如果 *sqlmaint* 运行时数据库正在使用，则将在 **text_file** 中写入一个警告。</span><span class="sxs-lookup"><span data-stu-id="09af7-177">A warning is written to *text_file* if the database is in use when **sqlmaint** runs.</span></span>  
  
 <span data-ttu-id="09af7-178">**-CkAl** |  **-CkAlNoIdx**</span><span class="sxs-lookup"><span data-stu-id="09af7-178">**-CkAl** | **-CkAlNoIdx**</span></span>  
 <span data-ttu-id="09af7-179">指定在 **-D**指定的数据库中运行带 NOINDEX 选项的 DBCC CHECKALLOC 语句。</span><span class="sxs-lookup"><span data-stu-id="09af7-179">Specifies that a DBCC CHECKALLOC statement with the NOINDEX option be run in the database specified in **-D**.</span></span> <span data-ttu-id="09af7-180">有关详细信息，请参阅 [DBCC CHECKALLOC (Transact-SQL)](/sql/t-sql/database-console-commands/dbcc-checkalloc-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="09af7-180">For more information, see [DBCC CHECKALLOC &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkalloc-transact-sql).</span></span>  
  
 <span data-ttu-id="09af7-181">**-CkCat**</span><span class="sxs-lookup"><span data-stu-id="09af7-181">**-CkCat**</span></span>  
 <span data-ttu-id="09af7-182">指定在 **-D** 指定的数据库中运行 DBCC CHECKCATALOG (Transact-SQL) 语句。</span><span class="sxs-lookup"><span data-stu-id="09af7-182">Specifies that a DBCC CHECKCATALOG (Transact-SQL) statement be run in the database specified in **-D**.</span></span> <span data-ttu-id="09af7-183">有关详细信息，请参阅 [DBCC CHECKCATALOG (Transact-SQL)](/sql/t-sql/database-console-commands/dbcc-checkcatalog-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="09af7-183">For more information, see [DBCC CHECKCATALOG &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkcatalog-transact-sql).</span></span>  
  
 <span data-ttu-id="09af7-184">**-UpdOptiStats** _sample_percent_</span><span class="sxs-lookup"><span data-stu-id="09af7-184">**-UpdOptiStats** _sample_percent_</span></span>  
 <span data-ttu-id="09af7-185">指定对数据库中的每个表运行下列语句：</span><span class="sxs-lookup"><span data-stu-id="09af7-185">Specifies that the following statement be run on each table in the database:</span></span>  
  
```  
UPDATE STATISTICS table WITH SAMPLE sample_percent PERCENT;  
```  
  
 <span data-ttu-id="09af7-186">如果表包含计算列，则在使用 **-UpdOptiStats** 时，还必须指定 **-SupportedComputedColumn**参数。</span><span class="sxs-lookup"><span data-stu-id="09af7-186">If the tables contain computed columns, you must also specify the **-SupportedComputedColumn** argument when you use **-UpdOptiStats**.</span></span>  
  
 <span data-ttu-id="09af7-187">有关详细信息，请参阅 [更新统计信息 (Transact-SQL)](/sql/t-sql/statements/update-statistics-transact-sql)创建的数据库维护计划。</span><span class="sxs-lookup"><span data-stu-id="09af7-187">For more information, see [UPDATE STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/update-statistics-transact-sql).</span></span>  
  
 <span data-ttu-id="09af7-188">**-RebldIdx** _free_space_</span><span class="sxs-lookup"><span data-stu-id="09af7-188">**-RebldIdx** _free_space_</span></span>  
 <span data-ttu-id="09af7-189">指定应使用 *free_space* 百分比值作为填充因子的反数，重新生成目标数据库的表索引。</span><span class="sxs-lookup"><span data-stu-id="09af7-189">Specifies that indexes on tables in the target database should be rebuilt by using the *free_space* percent value as the inverse of the fill factor.</span></span> <span data-ttu-id="09af7-190">例如，如果 *free_space* 百分比是 30，则使用的填充因子为 70。</span><span class="sxs-lookup"><span data-stu-id="09af7-190">For example, if *free_space* percentage is 30, then the fill factor used is 70.</span></span> <span data-ttu-id="09af7-191">如果指定 *free_space* 百分比值为 100，则使用原始填充因子值重新生成索引。</span><span class="sxs-lookup"><span data-stu-id="09af7-191">If a *free_space* percentage value of 100 is specified, then the indexes are rebuilt with the original fill factor value.</span></span>  
  
 <span data-ttu-id="09af7-192">如果索引位于计算列，则在使用 **-RebldIdx** 时，还必须指定 **-SupportComputedColumn**参数。</span><span class="sxs-lookup"><span data-stu-id="09af7-192">If the indexes are on computed columns, you must also specify the **-SupportComputedColumn** argument when you use **-RebldIdx**.</span></span>  
  
 <span data-ttu-id="09af7-193">**-RebldIdx**</span><span class="sxs-lookup"><span data-stu-id="09af7-193">**-SupportComputedColumn**</span></span>  
 <span data-ttu-id="09af7-194">对计算列使用 **sqlmaint** 运行 DBCC 维护命令时，必须指定此参数。</span><span class="sxs-lookup"><span data-stu-id="09af7-194">Must be specified to run DBCC maintenance commands with **sqlmaint** on computed columns.</span></span>  
  
 <span data-ttu-id="09af7-195">**-WriteHistory**</span><span class="sxs-lookup"><span data-stu-id="09af7-195">**-WriteHistory**</span></span>  
 <span data-ttu-id="09af7-196">指定在 msdb.dbo.sysdbmaintplan_history 中为 **sqlmaint**所执行的每个维护操作建立一个条目。</span><span class="sxs-lookup"><span data-stu-id="09af7-196">Specifies that an entry be made in msdb.dbo.sysdbmaintplan_history for each maintenance action performed by **sqlmaint**.</span></span> <span data-ttu-id="09af7-197">如果指定 **-PlanName** 或 **-PlanID** ，则 sysdbmaintplan_history 中的条目使用指定计划的 ID。</span><span class="sxs-lookup"><span data-stu-id="09af7-197">If **-PlanName** or **-PlanID** is specified, the entries in sysdbmaintplan_history use the ID of the specified plan.</span></span> <span data-ttu-id="09af7-198">如果指定 **-D** ，则通过给计划 ID 赋予零值来生成 sysdbmaintplan_history 中的条目。</span><span class="sxs-lookup"><span data-stu-id="09af7-198">If **-D** is specified, the entries in sysdbmaintplan_history are made with zeroes for the plan ID.</span></span>  
  
 <span data-ttu-id="09af7-199">**-BkUpDB** [ *backup_path*] |  **-BkUpLog** [ *backup_path* ]</span><span class="sxs-lookup"><span data-stu-id="09af7-199">**-BkUpDB** [ *backup_path*] |  **-BkUpLog** [ *backup_path* ]</span></span>  
 <span data-ttu-id="09af7-200">指定备份操作。</span><span class="sxs-lookup"><span data-stu-id="09af7-200">Specifies a backup action.</span></span> <span data-ttu-id="09af7-201">**-BkUpDb** 备份整个数据库。</span><span class="sxs-lookup"><span data-stu-id="09af7-201">**-BkUpDb** backs up the entire database.</span></span> <span data-ttu-id="09af7-202">**-BkUpLog** 只备份事务日志。</span><span class="sxs-lookup"><span data-stu-id="09af7-202">**-BkUpLog** backs up only the transaction log.</span></span>  
  
 <span data-ttu-id="09af7-203">*backup_path* 指定备份的目录。</span><span class="sxs-lookup"><span data-stu-id="09af7-203">*backup_path* specifies the directory for the backup.</span></span> <span data-ttu-id="09af7-204">如果还指定了*backup_path* ，则不需要 **backup_path** 。如果同时指定了二者，则 **backup_path** 会覆盖后者。</span><span class="sxs-lookup"><span data-stu-id="09af7-204">*backup_path* is not needed if **-UseDefDir** is also specified, and is overridden by **-UseDefDir** if both are specified.</span></span> <span data-ttu-id="09af7-205">备份的存放地址可以是目录或磁带设备地址（例如， \\\\.\TAPE0）。</span><span class="sxs-lookup"><span data-stu-id="09af7-205">The backup can be placed in a directory or a tape device address (for example, \\\\.\TAPE0).</span></span> <span data-ttu-id="09af7-206">数据库备份的文件名按如下格式自动生成：</span><span class="sxs-lookup"><span data-stu-id="09af7-206">The file name for a database backup is generated automatically as follows:</span></span>  
  
```  
dbname_db_yyyyMMddhhmm.BAK  
  
```  
  
 <span data-ttu-id="09af7-207">其中</span><span class="sxs-lookup"><span data-stu-id="09af7-207">where</span></span>  
  
-   <span data-ttu-id="09af7-208">*dbname* 是被备份的数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="09af7-208">*dbname* is the name of the database being backed up.</span></span>  
  
-   <span data-ttu-id="09af7-209">*yyyyMMddhhmm* 为备份操作的时间，其中 *yyyy* = 年， *MM* = 月， *dd* = 日， *hh* = 小时， *mm* = 分钟。</span><span class="sxs-lookup"><span data-stu-id="09af7-209">*yyyyMMddhhmm* is the time of the backup operation with *yyyy* = year, *MM* = month, *dd* = day, *hh* = hour, and *mm* = minute.</span></span>  
  
 <span data-ttu-id="09af7-210">事务备份的文件名自动使用类似的格式生成：</span><span class="sxs-lookup"><span data-stu-id="09af7-210">The file name for a transaction backup is generated automatically with a similar format:</span></span>  
  
```  
dbname_log_yyyymmddhhmm.BAK  
  
```  
  
 <span data-ttu-id="09af7-211">如果使用 **-BkUpDB** 参数，则必须同时使用 **-BkUpMedia** 参数指定介质。</span><span class="sxs-lookup"><span data-stu-id="09af7-211">If you use the **-BkUpDB** parameter, you must also specify the media by using the **-BkUpMedia** parameter.</span></span>  
  
 <span data-ttu-id="09af7-212">**-BkUpMedia**</span><span class="sxs-lookup"><span data-stu-id="09af7-212">**-BkUpMedia**</span></span>  
 <span data-ttu-id="09af7-213">指定备份的介质类型，DISK 或 TAPE。</span><span class="sxs-lookup"><span data-stu-id="09af7-213">Specifies the media type of the backup, either DISK or TAPE.</span></span>  
  
 <span data-ttu-id="09af7-214">**DISK**</span><span class="sxs-lookup"><span data-stu-id="09af7-214">**DISK**</span></span>  
 <span data-ttu-id="09af7-215">指定备份介质为磁盘。</span><span class="sxs-lookup"><span data-stu-id="09af7-215">Specifies that the backup medium is disk.</span></span>  
  
 <span data-ttu-id="09af7-216">**-DelBkUps**\< *time_period* ></span><span class="sxs-lookup"><span data-stu-id="09af7-216">**-DelBkUps**\< *time_period* ></span></span>  
 <span data-ttu-id="09af7-217">对于磁盘备份，指定如果创建备份后的时间间隔超出了 \<*time_period*>，则删除备份目录中的所有备份文件。</span><span class="sxs-lookup"><span data-stu-id="09af7-217">For disk backups, specifies that any backup file in the backup directory be deleted if the time interval after the creation of the backup exceeds the \<*time_period*>.</span></span>  
  
 <span data-ttu-id="09af7-218">**-CrBkSubDir**</span><span class="sxs-lookup"><span data-stu-id="09af7-218">**-CrBkSubDir**</span></span>  
 <span data-ttu-id="09af7-219">对于磁盘备份，指定在 [*backup_path*] 目录中创建子目录。如果同时指定了 **-UseDefDir** ，则在默认备份目录中创建子目录。</span><span class="sxs-lookup"><span data-stu-id="09af7-219">For disk backups, specifies that a subdirectory be created in the [*backup_path*] directory or in the default backup directory if **-UseDefDir** is also specified.</span></span> <span data-ttu-id="09af7-220">子目录的名称根据 **-D**中指定的数据库名称生成。</span><span class="sxs-lookup"><span data-stu-id="09af7-220">The name of the subdirectory is generated from the database name specified in **-D**.</span></span> <span data-ttu-id="09af7-221">**-CrBkSubDir** 提供一种简单的方法将不同数据库的所有备份放置到单独的子目录中，而无需更改 *backup_path* 参数。</span><span class="sxs-lookup"><span data-stu-id="09af7-221">**-CrBkSubDir** offers an easy way to put all the backups for different databases into separate subdirectories without having to change the *backup_path* parameter.</span></span>  
  
 <span data-ttu-id="09af7-222">**backup_path**</span><span class="sxs-lookup"><span data-stu-id="09af7-222">**-UseDefDir**</span></span>  
 <span data-ttu-id="09af7-223">对于磁盘备份，指定在默认的备份目录中创建备份文件。</span><span class="sxs-lookup"><span data-stu-id="09af7-223">For disk backups, specifies that the backup file be created in the default backup directory.</span></span> <span data-ttu-id="09af7-224">如果同时指定两者，则**UseDefDir** 将覆盖 *backup_path* 。</span><span class="sxs-lookup"><span data-stu-id="09af7-224">**UseDefDir** overrides *backup_path* if both are specified.</span></span> <span data-ttu-id="09af7-225">在默认 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 安装中，默认备份目录为 C:\Program Files\Microsoft SQL Server\MSSQL10_50.MSSQLSERVER\MSSQL\Backup。</span><span class="sxs-lookup"><span data-stu-id="09af7-225">With a default [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] setup, the default backup directory is C:\Program Files\Microsoft SQL Server\MSSQL10_50.MSSQLSERVER\MSSQL\Backup.</span></span>  
  
 <span data-ttu-id="09af7-226">**TAPE**</span><span class="sxs-lookup"><span data-stu-id="09af7-226">**TAPE**</span></span>  
 <span data-ttu-id="09af7-227">指定备份介质为磁带。</span><span class="sxs-lookup"><span data-stu-id="09af7-227">Specifies that the backup medium is tape.</span></span>  
  
 <span data-ttu-id="09af7-228">**-BkUpOnlyIfClean**</span><span class="sxs-lookup"><span data-stu-id="09af7-228">**-BkUpOnlyIfClean**</span></span>  
 <span data-ttu-id="09af7-229">指定仅当指定的 **-Ck** 检查未发现数据问题时才进行备份。</span><span class="sxs-lookup"><span data-stu-id="09af7-229">Specifies that the backup occur only if any specified **-Ck** checks did not find problems with the data.</span></span> <span data-ttu-id="09af7-230">维护操作的运行顺序与其在命令提示中出现的顺序相同。</span><span class="sxs-lookup"><span data-stu-id="09af7-230">Maintenance actions run in the same sequence as they appear in the command prompt.</span></span> <span data-ttu-id="09af7-231">如果还要指定 **-BkUpOnlyIfClean** 或指定无论检查报告问题与否都进行备份，则需在 **-BkUpDB**/ **-BkUpLog** 参数之前指定 **-CkDB**、 **-CkDBNoIdx**、 **-CkAl**、 **-CkAlNoIdx** **-CkTxtAl** 或 **-CkCat** 参数。</span><span class="sxs-lookup"><span data-stu-id="09af7-231">Specify the parameters **-CkDB**, **-CkDBNoIdx**, **-CkAl**, **-CkAlNoIdx**, **-CkTxtAl**, or **-CkCat** before the **-BkUpDB**/**-BkUpLog** parameter(s) if you are also going to specify **-BkUpOnlyIfClean**, or the backup occurs whether or not the check reports problems.</span></span>  
  
 <span data-ttu-id="09af7-232">**-VrfyBackup**</span><span class="sxs-lookup"><span data-stu-id="09af7-232">**-VrfyBackup**</span></span>  
 <span data-ttu-id="09af7-233">指定备份完成时，对备份运行 RESTORE VERIFYONLY。</span><span class="sxs-lookup"><span data-stu-id="09af7-233">Specifies that RESTORE VERIFYONLY be run on the backup when it completes.</span></span>  
  
 <span data-ttu-id="09af7-234">*number*[**minutes**| **hours**| **day**| **weeks**| **months**]</span><span class="sxs-lookup"><span data-stu-id="09af7-234">*number*[**minutes**| **hours**| **day**| **weeks**| **months**]</span></span>  
 <span data-ttu-id="09af7-235">指定时间间隔，用于确定报表或备份文件是否旧到需要将其删除。</span><span class="sxs-lookup"><span data-stu-id="09af7-235">Specifies the time interval used to determine if a report or backup file is old enough to be deleted.</span></span> <span data-ttu-id="09af7-236">*number* 是一个整数，后跟时间单位（没有空格）。</span><span class="sxs-lookup"><span data-stu-id="09af7-236">*number* is an integer followed (without a space) by a unit of time.</span></span> <span data-ttu-id="09af7-237">有效示例：</span><span class="sxs-lookup"><span data-stu-id="09af7-237">Valid examples:</span></span>  
  
-   <span data-ttu-id="09af7-238">**12weeks**</span><span class="sxs-lookup"><span data-stu-id="09af7-238">**12weeks**</span></span>  
  
-   <span data-ttu-id="09af7-239">**3months**</span><span class="sxs-lookup"><span data-stu-id="09af7-239">**3months**</span></span>  
  
-   <span data-ttu-id="09af7-240">**15days**</span><span class="sxs-lookup"><span data-stu-id="09af7-240">**15days**</span></span>  
  
 <span data-ttu-id="09af7-241">如果仅指定 *number* ，则默认日期部分为 **weeks**。</span><span class="sxs-lookup"><span data-stu-id="09af7-241">If only *number* is specified, the default date part is **weeks**.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="09af7-242">备注</span><span class="sxs-lookup"><span data-stu-id="09af7-242">Remarks</span></span>  
 <span data-ttu-id="09af7-243">**sqlmaint** 实用工具可对一个或多个数据库执行维护操作。</span><span class="sxs-lookup"><span data-stu-id="09af7-243">The **sqlmaint** utility performs maintenance operations on one or more databases.</span></span> <span data-ttu-id="09af7-244">如果指定 **-D** ，则在剩余的命令开关中指定的操作仅对指定数据库执行。</span><span class="sxs-lookup"><span data-stu-id="09af7-244">If **-D** is specified, the operations specified in the remaining switches are performed only on the specified database.</span></span> <span data-ttu-id="09af7-245">如果指定 **-PlanName** 或 **-PlanID** ，则 **sqlmaint** 只从指定的维护计划中检索数据库列表信息。</span><span class="sxs-lookup"><span data-stu-id="09af7-245">If **-PlanName** or **-PlanID** are specified, the only information **sqlmaint** retrieves from the specified maintenance plan is the list of databases in the plan.</span></span> <span data-ttu-id="09af7-246">在其余的 **sqlmaint** 参数中指定的所有操作都会应用于从计划获取的列表中的每个数据库。</span><span class="sxs-lookup"><span data-stu-id="09af7-246">All operations specified in the remaining **sqlmaint** parameters are applied against each database in the list obtained from the plan.</span></span> <span data-ttu-id="09af7-247">**sqlmaint** 实用工具不会应用在计划本身中定义的任何维护活动。</span><span class="sxs-lookup"><span data-stu-id="09af7-247">The **sqlmaint** utility does not apply any of the maintenance activities defined in the plan itself.</span></span>  
  
 <span data-ttu-id="09af7-248">如果成功运行，则 **sqlmaint** 实用工具将返回 0，如果失败则返回 1。</span><span class="sxs-lookup"><span data-stu-id="09af7-248">The **sqlmaint** utility returns 0 if it runs successfully or 1 if it fails.</span></span> <span data-ttu-id="09af7-249">在下列情况下将报告失败：</span><span class="sxs-lookup"><span data-stu-id="09af7-249">Failure is reported:</span></span>  
  
-   <span data-ttu-id="09af7-250">任何维护操作失败。</span><span class="sxs-lookup"><span data-stu-id="09af7-250">If any of the maintenance actions fail.</span></span>  
  
-   <span data-ttu-id="09af7-251">**-CkDB**、 **-CkDBNoIdx**、 **-CkAl**、 **-CkAlNoIdx**、 **-CkTxtAl**或 **-CkCat** 检查发现数据问题。</span><span class="sxs-lookup"><span data-stu-id="09af7-251">If **-CkDB**, **-CkDBNoIdx**, **-CkAl**, **-CkAlNoIdx**, **-CkTxtAl**, or **-CkCat** checks find problems with the data.</span></span>  
  
-   <span data-ttu-id="09af7-252">发生常规错误。</span><span class="sxs-lookup"><span data-stu-id="09af7-252">If a general failure is encountered.</span></span>  
  
## <a name="permissions"></a><span data-ttu-id="09af7-253">权限</span><span class="sxs-lookup"><span data-stu-id="09af7-253">Permissions</span></span>  
 <span data-ttu-id="09af7-254">对 **具有** 读取和执行 **权限的任何 Windows 用户都可以执行** sqlmaint `sqlmaint.exe`实用工具，默认情况下，该工具存储在 `x:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER1\MSSQL\Binn` 文件夹中。</span><span class="sxs-lookup"><span data-stu-id="09af7-254">The **sqlmaint** utility can be executed by any Windows user with **Read and Execute** permission on `sqlmaint.exe`, which by default is stored in the `x:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER1\MSSQL\Binn` folder.</span></span> <span data-ttu-id="09af7-255">此外，使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -login_ID **指定的** 登录名必须具有执行指定的操作所需的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 权限。</span><span class="sxs-lookup"><span data-stu-id="09af7-255">Additionally, the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] login specified with **-login_ID** must have the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] permissions required to perform the specified action.</span></span> <span data-ttu-id="09af7-256">如果使用 Windows 身份验证连接到 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ，则映射到经过身份验证的 Windows 用户的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 登录名必须具有执行指定操作所需的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 权限。</span><span class="sxs-lookup"><span data-stu-id="09af7-256">If the connection to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] uses Windows Authentication, the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] login mapped to the authenticated Windows user must have the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] permissions required to perform the specified action.</span></span>  
  
 <span data-ttu-id="09af7-257">例如，使用 **-BkUpDB** 需要执行 BACKUP 语句的权限。</span><span class="sxs-lookup"><span data-stu-id="09af7-257">For example, using the **-BkUpDB** requires permission to execute the BACKUP statement.</span></span> <span data-ttu-id="09af7-258">使用 **-UpdOptiStats** 参数需要执行 UPDATE STATISTICS 语句的权限。</span><span class="sxs-lookup"><span data-stu-id="09af7-258">And using the **-UpdOptiStats** argument requires permission to execute the UPDATE STATISTICS statement.</span></span> <span data-ttu-id="09af7-259">有关详细信息，请参阅联机丛书中相应主题的“权限”部分。</span><span class="sxs-lookup"><span data-stu-id="09af7-259">For more information, see the "Permissions" sections of the corresponding topics in Books Online.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="09af7-260">示例</span><span class="sxs-lookup"><span data-stu-id="09af7-260">Examples</span></span>  
  
### <a name="a-performing-dbcc-checks-on-a-database"></a><span data-ttu-id="09af7-261">A.</span><span class="sxs-lookup"><span data-stu-id="09af7-261">A.</span></span> <span data-ttu-id="09af7-262">对数据库执行 DBCC 检查</span><span class="sxs-lookup"><span data-stu-id="09af7-262">Performing DBCC checks on a database</span></span>  
  
```  
sqlmaint -S MyServer -D AdventureWorks2012 -CkDB -CkAl -CkCat -Rpt C:\MyReports\AdvWks_chk.rpt  
```  
  
### <a name="b-updating-statistics-using-a-15-sample-in-all-databases-in-a-plan-also-shrink-any-of-the-database-that-have-reached-110-mb-to-having-only-10-free-space"></a><span data-ttu-id="09af7-263">B.</span><span class="sxs-lookup"><span data-stu-id="09af7-263">B.</span></span> <span data-ttu-id="09af7-264">使用计划中所有数据库的 15% 样本更新统计信息。</span><span class="sxs-lookup"><span data-stu-id="09af7-264">Updating statistics using a 15% sample in all databases in a plan.</span></span> <span data-ttu-id="09af7-265">同时，压缩任何已达到 110 MB 的数据库，以便仅使用 10% 可用空间</span><span class="sxs-lookup"><span data-stu-id="09af7-265">Also, shrink any of the database that have reached 110 MB to having only 10% free space</span></span>  
  
```  
sqlmaint -S MyServer -PlanName MyUserDBPlan -UpdOptiStats 15 -RmUnusedSpace 110 10  
```  
  
### <a name="c-backing-up-all-the-databases-in-a-plan-to-their-individual-subdirectories-in-the-default-xprogram-filesmicrosoft-sql-servermssql12mssqlservermssqlbackup-directory-also-delete-any-backups-older-than-2-weeks"></a><span data-ttu-id="09af7-266">C.</span><span class="sxs-lookup"><span data-stu-id="09af7-266">C.</span></span> <span data-ttu-id="09af7-267">将计划中的所有数据库备份到默认 x:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Backup 目录下各自的子目录中。</span><span class="sxs-lookup"><span data-stu-id="09af7-267">Backing up all the databases in a plan to their individual subdirectories in the default x:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Backup directory.</span></span> <span data-ttu-id="09af7-268">同时，删除所有超过两个星期的备份</span><span class="sxs-lookup"><span data-stu-id="09af7-268">Also, delete any backups older than 2 weeks</span></span>  
  
```  
sqlmaint -S MyServer -PlanName MyUserDBPlan -BkUpDB -BkUpMedia DISK -UseDefDir -CrBkSubDir -DelBkUps 2weeks  
```  
  
### <a name="d-backing-up-a-database-to-the-default-xprogram-filesmicrosoft-sql-servermssql12mssqlservermssqlbackup-directory"></a><span data-ttu-id="09af7-269">D.</span><span class="sxs-lookup"><span data-stu-id="09af7-269">D.</span></span> <span data-ttu-id="09af7-270">将数据库备份到默认 x:\Program Files\Microsoft SQL Server\MSSQL12。MSSQLSERVER\MSSQL\Backup 目录 </span><span class="sxs-lookup"><span data-stu-id="09af7-270">Backing up a database to the default x:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Backup directory.</span></span>\  
  
```  
sqlmaint -S MyServer -BkUpDB -BkUpMedia DISK -UseDefDir  
```  
  
## <a name="see-also"></a><span data-ttu-id="09af7-271">另请参阅</span><span class="sxs-lookup"><span data-stu-id="09af7-271">See Also</span></span>  
 <span data-ttu-id="09af7-272">[BACKUP (Transact-SQL)](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="09af7-272">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 [<span data-ttu-id="09af7-273">更新统计信息 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="09af7-273">UPDATE STATISTICS &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/update-statistics-transact-sql)  
  
  
