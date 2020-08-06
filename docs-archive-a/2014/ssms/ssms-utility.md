---
title: Ssms 实用工具 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Management Studio [SQL Server], opening
- command prompt utilities [SQL Server], sqlwb
- sqlwb utility
- Management Studio command line
- opening SQL Server Management Studio
ms.assetid: aafda520-9e2a-4e1e-b936-1b165f1684e8
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0cfc9469e49e6ce3839d02a61477b8957fbc13e3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590511"
---
# <a name="ssms-utility"></a><span data-ttu-id="865e7-102">Ssms 实用工具</span><span class="sxs-lookup"><span data-stu-id="865e7-102">Ssms Utility</span></span>
  <span data-ttu-id="865e7-103">**Ssms**实用工具打开 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="865e7-103">The **Ssms**utility opens [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="865e7-104">如果指定， **Ssms** 还可以与服务器建立连接并打开查询、脚本、文件、项目和解决方案。</span><span class="sxs-lookup"><span data-stu-id="865e7-104">If specified, **Ssms** also establishes a connection to a server, and opens queries, scripts, files, projects, and solutions.</span></span>  
  
 <span data-ttu-id="865e7-105">可以指定包含查询、项目或解决方案的文件。</span><span class="sxs-lookup"><span data-stu-id="865e7-105">You can specify files that contain queries, projects, or solutions.</span></span> <span data-ttu-id="865e7-106">如果提供了连接信息并且文件类型与服务器类型关联，则包含查询的文件将自动连接到该服务器。</span><span class="sxs-lookup"><span data-stu-id="865e7-106">Files that contain queries are automatically connected to a server if connection information is provided and the file type is associated with that type of server.</span></span> <span data-ttu-id="865e7-107">例如，sql 文件将在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]中打开一个 SQL 查询编辑器窗口，.mdx 文件将在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]中打开一个 MDX 查询编辑器窗口。</span><span class="sxs-lookup"><span data-stu-id="865e7-107">For instance, .sql files will open a SQL Query Editor window in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], and .mdx files will open an MDX Query Editor window in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="865e7-108">**“SQL Server 解决方案和项目”** 将在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]中打开。</span><span class="sxs-lookup"><span data-stu-id="865e7-108">**SQL Server Solutions and Projects** will open in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="865e7-109">**Ssms** 实用工具不能运行查询。</span><span class="sxs-lookup"><span data-stu-id="865e7-109">The **Ssms** utility does not run queries.</span></span> <span data-ttu-id="865e7-110">若要从命令行运行查询，请使用 **sqlcmd** 实用工具。</span><span class="sxs-lookup"><span data-stu-id="865e7-110">To run queries from the command line, use the **sqlcmd** utility.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="865e7-111">语法</span><span class="sxs-lookup"><span data-stu-id="865e7-111">Syntax</span></span>  
  
```  
  
      Ssms  
    [scriptfile] [projectfile] [solutionfile]  
    [-Sservername] [-ddatabasename] [-Uusername] [-Ppassword]   
    [-E] [-nosplash] [-log[filename]?] [-?]  
```  
  
## <a name="arguments"></a><span data-ttu-id="865e7-112">参数</span><span class="sxs-lookup"><span data-stu-id="865e7-112">Arguments</span></span>  
 <span data-ttu-id="865e7-113">*scriptfile*</span><span class="sxs-lookup"><span data-stu-id="865e7-113">*scriptfile*</span></span>  
 <span data-ttu-id="865e7-114">指定一个或多个要打开的脚本文件。</span><span class="sxs-lookup"><span data-stu-id="865e7-114">Specifies one or more script files to open.</span></span> <span data-ttu-id="865e7-115">该参数必须包含文件的完整路径。</span><span class="sxs-lookup"><span data-stu-id="865e7-115">The parameter must contain the full path to the files.</span></span>  
  
 <span data-ttu-id="865e7-116">*projectfile*</span><span class="sxs-lookup"><span data-stu-id="865e7-116">*projectfile*</span></span>  
 <span data-ttu-id="865e7-117">指定要打开的脚本项目。</span><span class="sxs-lookup"><span data-stu-id="865e7-117">Specifies a script project to open.</span></span> <span data-ttu-id="865e7-118">该参数必须包含脚本项目文件的完整路径。</span><span class="sxs-lookup"><span data-stu-id="865e7-118">The parameter must contain the full path to the script project file.</span></span>  
  
 <span data-ttu-id="865e7-119">*solutionfile*</span><span class="sxs-lookup"><span data-stu-id="865e7-119">*solutionfile*</span></span>  
 <span data-ttu-id="865e7-120">指定要打开的解决方案。</span><span class="sxs-lookup"><span data-stu-id="865e7-120">Specifies a solution to open.</span></span> <span data-ttu-id="865e7-121">该参数必须包含解决方案文件的完整路径。</span><span class="sxs-lookup"><span data-stu-id="865e7-121">The parameter must contain the full path to the solution file.</span></span>  
  
 <span data-ttu-id="865e7-122">[**-S** _servername_]</span><span class="sxs-lookup"><span data-stu-id="865e7-122">[**-S** _servername_]</span></span>  
 <span data-ttu-id="865e7-123">服务器名称</span><span class="sxs-lookup"><span data-stu-id="865e7-123">Server name</span></span>  
  
 <span data-ttu-id="865e7-124">[**-d** _databasename_]</span><span class="sxs-lookup"><span data-stu-id="865e7-124">[**-d** _databasename_]</span></span>  
 <span data-ttu-id="865e7-125">数据库名称</span><span class="sxs-lookup"><span data-stu-id="865e7-125">Database name</span></span>  
  
 <span data-ttu-id="865e7-126">[**-U** _username_]</span><span class="sxs-lookup"><span data-stu-id="865e7-126">[**-U** _username_]</span></span>  
 <span data-ttu-id="865e7-127">通过 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 身份验证进行连接时的用户名</span><span class="sxs-lookup"><span data-stu-id="865e7-127">User name when connecting with [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication</span></span>  
  
 <span data-ttu-id="865e7-128">[**-P** _password_]</span><span class="sxs-lookup"><span data-stu-id="865e7-128">[**-P** _password_]</span></span>  
 <span data-ttu-id="865e7-129">通过 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 身份验证进行连接时的密码</span><span class="sxs-lookup"><span data-stu-id="865e7-129">Password when connecting with [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication</span></span>  
  
 <span data-ttu-id="865e7-130">[**-E**]</span><span class="sxs-lookup"><span data-stu-id="865e7-130">[**-E**]</span></span>  
 <span data-ttu-id="865e7-131">使用 Windows 身份验证进行连接</span><span class="sxs-lookup"><span data-stu-id="865e7-131">Connect using Windows Authentication</span></span>  
  
 <span data-ttu-id="865e7-132">[**-nosplash**]</span><span class="sxs-lookup"><span data-stu-id="865e7-132">[**-nosplash**]</span></span>  
 <span data-ttu-id="865e7-133">阻止 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 在打开时显示初始屏幕。</span><span class="sxs-lookup"><span data-stu-id="865e7-133">Prevents [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] from displaying the splash screen graphic while opening.</span></span> <span data-ttu-id="865e7-134">在带宽有限的情况下，通过终端服务连接到运行 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 的计算机上时，使用此选项。</span><span class="sxs-lookup"><span data-stu-id="865e7-134">Use this option when connecting to the computer running [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] by means of Terminal Services over a connection with a limited bandwidth.</span></span> <span data-ttu-id="865e7-135">该参数不区分大小写，并且可放在其他参数前后</span><span class="sxs-lookup"><span data-stu-id="865e7-135">This argument is not case-sensitive and may appear before or after other arguments</span></span>  
  
 <span data-ttu-id="865e7-136">[**-log**_[filename]？_]</span><span class="sxs-lookup"><span data-stu-id="865e7-136">[**-log**_[filename]?_]</span></span>  
 <span data-ttu-id="865e7-137">将 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 活动记录到指定的文件中以便进行故障排除</span><span class="sxs-lookup"><span data-stu-id="865e7-137">Logs [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] activity to the specified file for troubleshooting</span></span>  
  
 <span data-ttu-id="865e7-138">[**-?**]</span><span class="sxs-lookup"><span data-stu-id="865e7-138">[**-?**]</span></span>  
 <span data-ttu-id="865e7-139">显示命令行帮助</span><span class="sxs-lookup"><span data-stu-id="865e7-139">Displays command line help</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="865e7-140">备注</span><span class="sxs-lookup"><span data-stu-id="865e7-140">Remarks</span></span>  
 <span data-ttu-id="865e7-141">上述所有开关都是可选的，并用空格分隔，但文件用逗号分隔。</span><span class="sxs-lookup"><span data-stu-id="865e7-141">All of the switches are optional and separated by a space except files which are separated by commas.</span></span> <span data-ttu-id="865e7-142">如果不指定任何开关，则 **Ssms** 将按照“工具”\*\*\*\* 菜单的“选项”\*\*\*\* 设置中指定的方式打开 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="865e7-142">If you do not specify any switches, **Ssms** opens [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] as specified in the **Options** settings on the **Tools** menu.</span></span> <span data-ttu-id="865e7-143">例如，如果“环境/常规”\*\*\*\* 页的“启动时”\*\*\*\* 选项指定了“打开新查询窗口”\*\*\*\*，**Ssms** 则会在打开时显示一个空白的查询编辑器。</span><span class="sxs-lookup"><span data-stu-id="865e7-143">For example, if the **Environment/General** page **At startup** option specifies **Open new query window**, **Ssms** will open with a blank Query Editor.</span></span>  
  
 <span data-ttu-id="865e7-144">**-Log**开关必须出现在命令行的末尾，位于所有其他开关之后。</span><span class="sxs-lookup"><span data-stu-id="865e7-144">The **-log** switch must appear at the end of the command line, after all other switches.</span></span> <span data-ttu-id="865e7-145">文件名参数是可选的。</span><span class="sxs-lookup"><span data-stu-id="865e7-145">The filename argument is optional.</span></span> <span data-ttu-id="865e7-146">如果指定了一个文件名，并且该文件不存在，则创建该文件。</span><span class="sxs-lookup"><span data-stu-id="865e7-146">If a filename is specified, and the file does not exist, the file is created.</span></span> <span data-ttu-id="865e7-147">如果无法创建该文件（例如，由于没有足够的写访问权限），日志将改为写入非本地化的 APPDATA 位置（见下文）。</span><span class="sxs-lookup"><span data-stu-id="865e7-147">If the file cannot be created - for example, due to insufficient write access, the log is written to the nonlocalized APPDATA location instead (See below).</span></span> <span data-ttu-id="865e7-148">如果未指定该文件名参数，则两个文件将写入当前用户的非本地化的应用程序数据文件夹。</span><span class="sxs-lookup"><span data-stu-id="865e7-148">If the filename argument is not specified, two files are written to the current user's nonlocalized application data folder.</span></span> <span data-ttu-id="865e7-149">SQL Server 的非本地化的应用程序数据文件夹可以从 APPDATA 环境变量中找到。</span><span class="sxs-lookup"><span data-stu-id="865e7-149">The nonlocalized application data folder for SQL Server can be found from the APPDATA environment variable.</span></span> <span data-ttu-id="865e7-150">例如，对于 SQL Server 2012，文件夹为 \<system drive> ： \Users \\<username \> \AppData\Roaming\Microsoft\AppEnv\10.0 \\ 。</span><span class="sxs-lookup"><span data-stu-id="865e7-150">For example, for SQL Server 2012, the folder is \<system drive>:\Users\\<username\>\AppData\Roaming\Microsoft\AppEnv\10.0\\.</span></span> <span data-ttu-id="865e7-151">默认情况下，这两个文件分别命名为 ActivityLog.xml 和 ActivityLog.xsl。</span><span class="sxs-lookup"><span data-stu-id="865e7-151">The two files are, by default, named ActivityLog.xml and ActivityLog.xsl.</span></span> <span data-ttu-id="865e7-152">前者包含活动日志数据，后者是一种 XML 样式表，提供了更方便的方法来查看 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="865e7-152">The former contains the activity log data and the latter is an XML style sheet which provides a more convenient way to view the XML file.</span></span> <span data-ttu-id="865e7-153">使用以下步骤在默认 XML 查看器（如 Internet Explorer）中查看日志文件：单击 "开始"，再单击 "运行 ..."，然后 \<system drive> 在提供的字段中键入 "： \Users \\<用户名 \>\AppData\Roaming\Microsoft\AppEnv\10.0\ActivityLog.xml"，然后按 enter。</span><span class="sxs-lookup"><span data-stu-id="865e7-153">Use the following steps to view the log file in your default XML viewer, like Internet Explorer:  Click Start, then click Run...", then type "\<system drive>:\Users\\<username\>\AppData\Roaming\Microsoft\AppEnv\10.0\ActivityLog.xml" into the field provided, and then press Enter.</span></span>  
  
 <span data-ttu-id="865e7-154">如果提供了连接信息并且文件类型与服务器类型关联，则包含查询的文件将立即连接到该服务器。</span><span class="sxs-lookup"><span data-stu-id="865e7-154">Files that contain queries will prompt to be connected to a server if connection information is provided and the file type is associated with that type of server.</span></span> <span data-ttu-id="865e7-155">例如，sql 文件将在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]中打开一个 SQL 查询编辑器窗口，.mdx 文件将在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]中打开一个 MDX 查询编辑器窗口。</span><span class="sxs-lookup"><span data-stu-id="865e7-155">For instance, .sql files will open a SQL Query Editor window in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], and .mdx files will open an MDX Query Editor window in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="865e7-156">**“SQL Server 解决方案和项目”** 将在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]中打开。</span><span class="sxs-lookup"><span data-stu-id="865e7-156">**SQL Server Solutions and Projects** will open in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="865e7-157">下表列出了与服务器类型相对应的文件扩展名。</span><span class="sxs-lookup"><span data-stu-id="865e7-157">The following table maps server types to file extensions.</span></span>  
  
|<span data-ttu-id="865e7-158">服务器类型</span><span class="sxs-lookup"><span data-stu-id="865e7-158">Server type</span></span>|<span data-ttu-id="865e7-159">扩展名</span><span class="sxs-lookup"><span data-stu-id="865e7-159">Extension</span></span>|  
|-----------------|---------------|  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]|<span data-ttu-id="865e7-160">.sql</span><span class="sxs-lookup"><span data-stu-id="865e7-160">.sql</span></span>|  
|<span data-ttu-id="865e7-161">SQL Server Analysis Services</span><span class="sxs-lookup"><span data-stu-id="865e7-161">SQL Server Analysis Services</span></span>|<span data-ttu-id="865e7-162">.mdx</span><span class="sxs-lookup"><span data-stu-id="865e7-162">.mdx</span></span><br /><br /> <span data-ttu-id="865e7-163">.xmla</span><span class="sxs-lookup"><span data-stu-id="865e7-163">.xmla</span></span>|  
  
## <a name="examples"></a><span data-ttu-id="865e7-164">示例</span><span class="sxs-lookup"><span data-stu-id="865e7-164">Examples</span></span>  
 <span data-ttu-id="865e7-165">以下脚本将在命令指示符下使用默认设置打开 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] ：</span><span class="sxs-lookup"><span data-stu-id="865e7-165">The following script opens [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] from a command prompt with the default settings:</span></span>  
  
```  
Ssms  
  
```  
  
 <span data-ttu-id="865e7-166">以下脚本将在命令指示符下，使用 Windows 身份验证打开 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] ，其中代码编辑器设置为 `ACCTG and the database AdventureWorks2012,` ，并且不显示初始屏幕：</span><span class="sxs-lookup"><span data-stu-id="865e7-166">The following script opens [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] from a command prompt, with Windows Authentication, with the Code Editor set to the server `ACCTG and the database AdventureWorks2012,` without showing the splash screen:</span></span>  
  
```  
Ssms -E -S ACCTG -d AdventureWorks2012 -nosplash  
  
```  
  
 <span data-ttu-id="865e7-167">以下脚本将在命令指示符下打开 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] ，并打开 MonthEndQuery 脚本。</span><span class="sxs-lookup"><span data-stu-id="865e7-167">The following script opens [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] from a command prompt, and opens the MonthEndQuery script.</span></span>  
  
```  
Ssms "C:\Documents and Settings\username\My Documents\SQL Server Management Studio Projects\FinanceScripts\FinanceScripts\MonthEndQuery.sql"  
  
```  
  
 <span data-ttu-id="865e7-168">以下脚本在命令指示符下打开 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] ，并打开名为 `developer`的计算机上的 NewReportsProject 项目：</span><span class="sxs-lookup"><span data-stu-id="865e7-168">The following script opens [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] from a command prompt, and opens the NewReportsProject project on the computer named `developer`:</span></span>  
  
```  
Ssms "\\developer\fin\ReportProj\ReportProj\NewReportProj.ssmssqlproj"  
  
```  
  
 <span data-ttu-id="865e7-169">以下脚本在命令提示符下打开 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] ，并打开 MonthlyReports 解决方案：</span><span class="sxs-lookup"><span data-stu-id="865e7-169">The following script opens [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] from a command prompt, and opens the MonthlyReports solution:</span></span>  
  
```  
Ssms "C:\solutionsfolder\ReportProj\MonthlyReports.ssmssln"  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="865e7-170">另请参阅</span><span class="sxs-lookup"><span data-stu-id="865e7-170">See Also</span></span>  
 [<span data-ttu-id="865e7-171">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="865e7-171">Use SQL Server Management Studio</span></span>](../database-engine/use-sql-server-management-studio.md)  
  
  
