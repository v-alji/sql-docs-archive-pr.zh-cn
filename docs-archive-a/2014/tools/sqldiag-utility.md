---
title: SQLdiag 实用工具 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- command prompt utilities [SQL Server], SQLdiag
- stopping diagnostic collection
- storing diagnostic information
- performance [SQL Server], diagnostic collection
- diagnostic records [SQL Server]
- scripts [SQL Server], diagnostic collection
- logs [SQL Server], diagnostic collection
- starting diagnostic collection
- clustered instance of SQL Server
- monitoring performance [SQL Server], diagnostic collection
- security [SQL Server], diagnostic collection
- SQLDIAG service
- space [SQL Server], diagnostic collection
- SQLdiag utility
- disk space [SQL Server], diagnostic collection
- configuration files [SQL Server]
- automatic diagnostic collection
- clusters [SQL Server], diagnostic collection
ms.assetid: 45ba1307-33d1-431e-872c-a6e4556f5ff2
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0559e0b2261ed5ba1c9c384608d04194d685f695
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682490"
---
# <a name="sqldiag-utility"></a><span data-ttu-id="f3e3b-102">SQLdiag 实用工具</span><span class="sxs-lookup"><span data-stu-id="f3e3b-102">SQLdiag Utility</span></span>
  <span data-ttu-id="f3e3b-103">**SQLdiag** 实用工具是一般用途的诊断信息收集实用工具，可作为控制台应用程序或服务运行。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-103">The **SQLdiag** utility is a general purpose diagnostics collection utility that can be run as a console application or as a service.</span></span> <span data-ttu-id="f3e3b-104">可以使用 **SQLdiag** 从 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 和其他类型的服务器中收集日志和数据文件，同时还可将其用于一直监视服务器或对服务器的特定问题进行故障排除。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-104">You can use **SQLdiag** to collect logs and data files from [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] and other types of servers, and use it to monitor your servers over time or troubleshoot specific problems with your servers.</span></span> <span data-ttu-id="f3e3b-105">**SQLdiag** 旨在加快和简化为 [!INCLUDE[msCoName](../includes/msconame-md.md)] 客户支持服务部门收集诊断信息的过程。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-105">**SQLdiag** is intended to expedite and simplify diagnostic information gathering for [!INCLUDE[msCoName](../includes/msconame-md.md)] Customer Support Services.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f3e3b-106">该实用工具可以进行更改，因此依赖于其命令行参数或行为的应用程序或脚本可能无法在未来版本中正常运行。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-106">This utility may be changed, and applications or scripts that rely on its command line arguments or behavior may not work correctly in future releases.</span></span>  
  
 <span data-ttu-id="f3e3b-107">**SQLdiag** 可以收集下列类型的诊断信息：</span><span class="sxs-lookup"><span data-stu-id="f3e3b-107">**SQLdiag** can collect the following types of diagnostic information:</span></span>  
  
-   <span data-ttu-id="f3e3b-108">Windows 性能日志</span><span class="sxs-lookup"><span data-stu-id="f3e3b-108">Windows performance logs</span></span>  
  
-   <span data-ttu-id="f3e3b-109">Windows 事件日志</span><span class="sxs-lookup"><span data-stu-id="f3e3b-109">Windows event logs</span></span>  
  
-   [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] <span data-ttu-id="f3e3b-110">跟踪</span><span class="sxs-lookup"><span data-stu-id="f3e3b-110">traces</span></span>  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="f3e3b-111">阻塞信息</span><span class="sxs-lookup"><span data-stu-id="f3e3b-111">blocking information</span></span>  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="f3e3b-112">配置信息</span><span class="sxs-lookup"><span data-stu-id="f3e3b-112">configuration information</span></span>  
  
 <span data-ttu-id="f3e3b-113">通过编辑配置文件 SQLDiag.xml，可以指定希望 **SQLdiag** 收集的信息类型，详细介绍见下文。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-113">You can specify what types of information you want **SQLdiag** to collect by editing the configuration file SQLDiag.xml, which is described in a following section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3e3b-114">语法</span><span class="sxs-lookup"><span data-stu-id="f3e3b-114">Syntax</span></span>  
  
```  
  
      sqldiag   
     { [/?] }  
     |  
     { [/I configuration_file]  
       [/O output_folder_path]  
       [/Psupport_folder_path]  
       [/Noutput_folder_management_option]  
       [/Mmachine1 [ machine2machineN]| @machinelistfile]  
       [/Cfile_compression_type]  
       [/B [+]start_time]  
       [/E [+]stop_time]  
       [/ASQLdiag_application_name]  
       [/T { tcp [ ,port ] | np | lpc } ]  
       [/Q] [/G] [/R] [/U] [/L] [/X] }  
     |  
     { [START | STOP | STOP_ABORT] }  
     |  
     { [START | STOP | STOP_ABORT] /ASQLdiag_application_name }  
```  
  
## <a name="arguments"></a><span data-ttu-id="f3e3b-115">参数</span><span class="sxs-lookup"><span data-stu-id="f3e3b-115">Arguments</span></span>  
 <span data-ttu-id="f3e3b-116">**/?**</span><span class="sxs-lookup"><span data-stu-id="f3e3b-116">**/?**</span></span>  
 <span data-ttu-id="f3e3b-117">显示用法信息。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-117">Displays usage information.</span></span>  
  
 <span data-ttu-id="f3e3b-118">**/I** _configuration_file_</span><span class="sxs-lookup"><span data-stu-id="f3e3b-118">**/I** _configuration_file_</span></span>  
 <span data-ttu-id="f3e3b-119">设置 **SQLdiag** 要使用的配置文件。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-119">Sets the configuration file for **SQLdiag** to use.</span></span> <span data-ttu-id="f3e3b-120">默认情况下， **/I** 设置为 SQLDiag.Xml。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-120">By default, **/I** is set to SQLDiag.Xml.</span></span>  
  
 <span data-ttu-id="f3e3b-121">**/O** _output_folder_path_</span><span class="sxs-lookup"><span data-stu-id="f3e3b-121">**/O** _output_folder_path_</span></span>  
 <span data-ttu-id="f3e3b-122">将 **SQLdiag** 输出重定向到指定文件夹。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-122">Redirects **SQLdiag** output to the specified folder.</span></span> <span data-ttu-id="f3e3b-123">如果未指定 **/O** 选项，则 **SQLdiag** 输出结果将会写入 **SQLdiag** 启动文件夹下名为 SQLDIAG 的子文件夹中。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-123">If the **/O** option is not specified, **SQLdiag** output is written to a subfolder named SQLDIAG under the **SQLdiag** startup folder.</span></span> <span data-ttu-id="f3e3b-124">如果 SQLDIAG 文件夹不存在，则 **SQLdiag** 将会尝试创建该文件夹。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-124">If the SQLDIAG folder does not exist, **SQLdiag** attempts to create it.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f3e3b-125">输出文件夹位置相对于可使用 **/P**指定的支持文件夹的位置。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-125">The output folder location is relative to the support folder location that can be specified with **/P**.</span></span> <span data-ttu-id="f3e3b-126">若要为输出文件夹设置一个完全不同的位置，请为 **/O**指定完整的目录路径。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-126">To set an entirely different location for the output folder, specify the full directory path for **/O**.</span></span>  
  
 <span data-ttu-id="f3e3b-127">**/P** _support_folder_path_</span><span class="sxs-lookup"><span data-stu-id="f3e3b-127">**/P** _support_folder_path_</span></span>  
 <span data-ttu-id="f3e3b-128">设置支持文件夹路径。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-128">Sets the support folder path.</span></span> <span data-ttu-id="f3e3b-129">默认情况下，将 **/P** 设置为存放 **SQLdiag** 可执行文件的文件夹。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-129">By default, **/P** is set to the folder where the **SQLdiag** executable resides.</span></span> <span data-ttu-id="f3e3b-130">支持文件夹包含 **SQLdiag** 支持文件，如 XML 配置文件、Transact-SQL 脚本以及该实用工具在收集诊断信息过程中所使用的其他文件。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-130">The support folder contains **SQLdiag** support files, such as the XML configuration file, Transact-SQL scripts, and other files that the utility uses during diagnostics collection.</span></span> <span data-ttu-id="f3e3b-131">如果使用该选项指定一个备用的支持文件路径，则 **SQLdiag** 会自动将其所需的支持文件复制到指定的文件夹（如果这些文件尚未存在）。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-131">If you use this option to specify an alternate support files path, **SQLdiag** will automatically copy the support files it requires to the specified folder if they do not already exist.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f3e3b-132">若要将当前文件夹设置为支持路径，请在命令行中指定 **%cd%** ，如下所示：</span><span class="sxs-lookup"><span data-stu-id="f3e3b-132">To set your current folder as the support path, specify **%cd%** on the command line as follows:</span></span>  
>   
>  <span data-ttu-id="f3e3b-133">**SQLDIAG /P %cd%**</span><span class="sxs-lookup"><span data-stu-id="f3e3b-133">**SQLDIAG /P %cd%**</span></span>  
  
 <span data-ttu-id="f3e3b-134">**/N** _output_folder_management_option_</span><span class="sxs-lookup"><span data-stu-id="f3e3b-134">**/N** _output_folder_management_option_</span></span>  
 <span data-ttu-id="f3e3b-135">设置 **SQLdiag** 在其启动时，是覆盖还是重命名输出文件夹。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-135">Sets whether **SQLdiag** overwrites or renames the output folder when it starts up.</span></span> <span data-ttu-id="f3e3b-136">可用选项：</span><span class="sxs-lookup"><span data-stu-id="f3e3b-136">Available options:</span></span>  
  
 <span data-ttu-id="f3e3b-137">1 = 覆盖输出文件夹（默认）</span><span class="sxs-lookup"><span data-stu-id="f3e3b-137">1 = Overwrites the output folder (default)</span></span>  
  
 <span data-ttu-id="f3e3b-138">2 = 当 **SQLdiag** 启动时，将输出文件夹重命名为 SQLDIAG_00001、SQLDIAG_00002 等等。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-138">2 = When **SQLdiag** starts up, it renames the output folder to SQLDIAG_00001, SQLDIAG_00002, and so on.</span></span> <span data-ttu-id="f3e3b-139">重命名当前输出文件夹之后， **SQLdiag** 将输出写入默认输出文件夹 SQLDIAG。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-139">After renaming the current output folder, **SQLdiag** writes output to the default output folder SQLDIAG.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f3e3b-140">**SQLdiag** 在启动时不会将输出追加到当前输出文件夹。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-140">**SQLdiag** does not append output to the current output folder when it starts up.</span></span> <span data-ttu-id="f3e3b-141">它只能覆盖默认的输出文件夹（选项 1）或重命名该文件夹（选项 2），然后将输出写入名为 SQLDIAG 的新默认输出文件夹。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-141">It can only overwrite the default output folder (option 1) or rename the folder (option 2), and then it writes output to the new default output folder named SQLDIAG.</span></span>  
  
 <span data-ttu-id="f3e3b-142">**/M** _machine1_ [ *machine2 \* \* machineN*] |*@machinelistfile*</span><span class="sxs-lookup"><span data-stu-id="f3e3b-142">**/M** _machine1_ [ *machine2\*\*machineN*] | *@machinelistfile*</span></span>  
 <span data-ttu-id="f3e3b-143">覆盖在配置文件中指定的计算机。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-143">Overrides the machines specified in the configuration file.</span></span> <span data-ttu-id="f3e3b-144">默认情况下，配置文件为 SQLDiag.Xml，也可以使用 **/I** 参数进行设置。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-144">By default the configuration file is SQLDiag.Xml, or is set with the **/I** parameter.</span></span> <span data-ttu-id="f3e3b-145">如果指定多台计算机，请用空格分隔各个计算机名称。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-145">When specifying more than one machine, separate each machine name with a space.</span></span>  
  
 <span data-ttu-id="f3e3b-146">使用 *@machinelistfile* 指定要存储在配置文件中的计算机列表文件名。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-146">Using *@machinelistfile* specifies a machine list filename to be stored in the configuration file.</span></span>  
  
 <span data-ttu-id="f3e3b-147">**/C** _file_compression_type_</span><span class="sxs-lookup"><span data-stu-id="f3e3b-147">**/C** _file_compression_type_</span></span>  
 <span data-ttu-id="f3e3b-148">设置 **SQLdiag** 输出文件夹文件所用的文件压缩类型。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-148">Sets the type of file compression used on the **SQLdiag** output folder files.</span></span> <span data-ttu-id="f3e3b-149">可用选项：</span><span class="sxs-lookup"><span data-stu-id="f3e3b-149">Available options:</span></span>  
  
 <span data-ttu-id="f3e3b-150">0 = 无（默认）</span><span class="sxs-lookup"><span data-stu-id="f3e3b-150">0 = none (default)</span></span>  
  
 <span data-ttu-id="f3e3b-151">1 = 使用 NTFS 压缩</span><span class="sxs-lookup"><span data-stu-id="f3e3b-151">1 = uses NTFS compression</span></span>  
  
 <span data-ttu-id="f3e3b-152">**/B** [ **+** ]*start_time*</span><span class="sxs-lookup"><span data-stu-id="f3e3b-152">**/B** [**+**]*start_time*</span></span>  
 <span data-ttu-id="f3e3b-153">按照以下格式指定开始收集诊断数据的日期和时间：</span><span class="sxs-lookup"><span data-stu-id="f3e3b-153">Specifies the date and time to start collecting diagnostic data in the following format:</span></span>  
  
 <span data-ttu-id="f3e3b-154">YYYYMMDD_HH:MM:SS</span><span class="sxs-lookup"><span data-stu-id="f3e3b-154">YYYYMMDD_HH:MM:SS</span></span>  
  
 <span data-ttu-id="f3e3b-155">时间使用二十四小时制指定。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-155">The time is specified using 24-hour notation.</span></span> <span data-ttu-id="f3e3b-156">例如，下午 2:00</span><span class="sxs-lookup"><span data-stu-id="f3e3b-156">For example, 2:00 P.M.</span></span> <span data-ttu-id="f3e3b-157">应指定为 **14:00:00**。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-157">should be specified as **14:00:00**.</span></span>  
  
 <span data-ttu-id="f3e3b-158">使用 **+** 并且不带日期（只使用 HH:MM:SS），以指定与当前日期和时间相对的时间。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-158">Use **+** without the date (HH:MM:SS only) to specify a time that is relative to the current date and time.</span></span> <span data-ttu-id="f3e3b-159">例如，如果指定 **/B +02:00:00**，则 **SQLdiag** 将会在 2 小时后开始收集信息。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-159">For example, if you specify **/B +02:00:00**, **SQLdiag** will wait 2 hours before it starts collecting information.</span></span>  
  
 <span data-ttu-id="f3e3b-160">不要在 **+** 和指定的 *start_time*之间插入空格。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-160">Do not insert a space between **+** and the specified *start_time*.</span></span>  
  
 <span data-ttu-id="f3e3b-161">如果指定的开始时间是过去的某一时间，则 **SQLdiag** 将会强行更改开始日期，以使开始日期和时间为将来的日期和时间。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-161">If you specify a start time that is in the past, **SQLdiag** forcibly changes the start date so the start date and time are in the future.</span></span> <span data-ttu-id="f3e3b-162">例如，如果指定时间为 **/B 01:00:00** ，而当前时间为 08:00:00，则 **SQLdiag** 将会强行将开始日期更改为下一天。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-162">For example, if you specify **/B 01:00:00** and the current time is 08:00:00, **SQLdiag** forcibly changes the start date so that the start date is the next day.</span></span>  
  
 <span data-ttu-id="f3e3b-163">请注意， **SQLdiag** 使用运行实用工具的计算机上的本地时间。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-163">Note that **SQLdiag** uses the local time on the computer where the utility is running.</span></span>  
  
 <span data-ttu-id="f3e3b-164">**/E** [ **+** ]*stop_time*</span><span class="sxs-lookup"><span data-stu-id="f3e3b-164">**/E** [**+**]*stop_time*</span></span>  
 <span data-ttu-id="f3e3b-165">按照以下格式指定停止收集诊断数据的日期和时间：</span><span class="sxs-lookup"><span data-stu-id="f3e3b-165">Specifies the date and time to stop collecting diagnostic data in the following format:</span></span>  
  
 <span data-ttu-id="f3e3b-166">YYYYMMDD_HH:MM:SS</span><span class="sxs-lookup"><span data-stu-id="f3e3b-166">YYYYMMDD_HH:MM:SS</span></span>  
  
 <span data-ttu-id="f3e3b-167">时间使用二十四小时制指定。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-167">The time is specified using 24-hour notation.</span></span> <span data-ttu-id="f3e3b-168">例如，下午 2:00</span><span class="sxs-lookup"><span data-stu-id="f3e3b-168">For example, 2:00 P.M.</span></span> <span data-ttu-id="f3e3b-169">应指定为 **14:00:00**。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-169">should be specified as **14:00:00**.</span></span>  
  
 <span data-ttu-id="f3e3b-170">使用 **+** 并且不带日期（只使用 HH:MM:SS），以指定与当前日期和时间相对的时间。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-170">Use **+** without the date (HH:MM:SS only) to specify a time that is relative to the current date and time.</span></span> <span data-ttu-id="f3e3b-171">例如，如果使用 **/B +02:00:00 /E +03:00:00**指定开始时间和结束时间，则 **SQLdiag** 将会在 2 小时后开始收集信息，经过 3 小时的信息收集后便停止收集并退出。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-171">For example, if you specify a start time and end time by using **/B +02:00:00 /E +03:00:00**, **SQLdiag** waits 2 hours before it starts collecting information, then collects information for 3 hours before it stops and exits.</span></span> <span data-ttu-id="f3e3b-172">如果不指定 **/B** ，则 **SQLdiag** 将会立即开始收集诊断信息，并按 **/E**指定的日期和时间结束收集操作。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-172">If **/B** is not specified, **SQLdiag** starts collecting diagnostics immediately and ends at the date and time specified by **/E**.</span></span>  
  
 <span data-ttu-id="f3e3b-173">不要在 **+** 和指定的 *start_time* 或 *end_time*之间插入空格。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-173">Do not insert a space between **+** and the specified *start_time* or *end_time*.</span></span>  
  
 <span data-ttu-id="f3e3b-174">请注意， **SQLdiag** 使用运行实用工具的计算机上的本地时间。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-174">Note that **SQLdiag** uses the local time on the computer where the utility is running.</span></span>  
  
 <span data-ttu-id="f3e3b-175">**/A** _SQLdiag_application_name_</span><span class="sxs-lookup"><span data-stu-id="f3e3b-175">**/A** _SQLdiag_application_name_</span></span>  
 <span data-ttu-id="f3e3b-176">使你可针对同一个 **实例运行多个** SQLdiag [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 实用工具的实例。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-176">Enables running multiple instances of the **SQLdiag** utility against the same [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance.</span></span>  
  
 <span data-ttu-id="f3e3b-177">每个 *SQLdiag_application_name* 标识不同的 **SQLdiag**的实例。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-177">Each *SQLdiag_application_name* identifies a different instance of **SQLdiag**.</span></span> <span data-ttu-id="f3e3b-178">*SQLdiag_application_name* 实例和 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 实例名称之间没有任何关系。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-178">No relationship exists between a *SQLdiag_application_name* instance and a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance name.</span></span>  
  
 <span data-ttu-id="f3e3b-179">*SQLdiag_application_name* 可用于启动或停止特定的 **SQLdiag** 服务实例。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-179">*SQLdiag_application_name* can be used to start or stop a specific instance of the **SQLdiag** service.</span></span>  
  
 <span data-ttu-id="f3e3b-180">例如：</span><span class="sxs-lookup"><span data-stu-id="f3e3b-180">For example:</span></span>  
  
 <span data-ttu-id="f3e3b-181">**SQLDIAG START /A** _SQLdiag_application_name_</span><span class="sxs-lookup"><span data-stu-id="f3e3b-181">**SQLDIAG START /A** _SQLdiag_application_name_</span></span>  
  
 <span data-ttu-id="f3e3b-182">它也可与 **/R** 选项一起使用，以将特定的 **SQLdiag** 实例注册为服务。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-182">It can also be used with the **/R** option to register a specific instance of **SQLdiag** as a service.</span></span> <span data-ttu-id="f3e3b-183">例如：</span><span class="sxs-lookup"><span data-stu-id="f3e3b-183">For example:</span></span>  
  
 <span data-ttu-id="f3e3b-184">**SQLDIAG /R /A** _SQLdiag_application_name_</span><span class="sxs-lookup"><span data-stu-id="f3e3b-184">**SQLDIAG /R /A** _SQLdiag_application_name_</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f3e3b-185">**SQLdiag** 会自动在为 *SQLdiag_application_name*指定的实例名称之前添加前缀 DIAG$。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-185">**SQLdiag** automatically prefixes DIAG$ to the instance name specified for *SQLdiag_application_name*.</span></span> <span data-ttu-id="f3e3b-186">如果你将 **SQLdiag** 注册为服务，则上述操作会提供有意义的服务名称。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-186">This provides a sensible service name if you register **SQLdiag** as a service.</span></span>  
  
 <span data-ttu-id="f3e3b-187">/T { tcp [ ,*port* ] | np | lpc }</span><span class="sxs-lookup"><span data-stu-id="f3e3b-187">/T { tcp [ ,*port* ] | np | lpc }</span></span>  
 <span data-ttu-id="f3e3b-188">使用指定协议连接到 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的实例。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-188">Connects to an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] using the specified protocol.</span></span>  
  
 <span data-ttu-id="f3e3b-189">tcp [,*port*]</span><span class="sxs-lookup"><span data-stu-id="f3e3b-189">tcp [,*port*]</span></span>  
 <span data-ttu-id="f3e3b-190">传输控制协议/Internet 协议 (TCP/IP)。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-190">Transmission Control Protocol/Internet Protocol (TCP/IP).</span></span> <span data-ttu-id="f3e3b-191">您可以选择为连接指定一个端口号。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-191">You can optionally specify a port number for the connection.</span></span>  
  
 <span data-ttu-id="f3e3b-192">np</span><span class="sxs-lookup"><span data-stu-id="f3e3b-192">np</span></span>  
 <span data-ttu-id="f3e3b-193">命名管道。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-193">Named pipes.</span></span> <span data-ttu-id="f3e3b-194">默认情况下， [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的默认实例侦听命名管道 `\\.\pipe\sql\query` 和 `\\.\pipe\MSSQL$<instancename>\sql\query` 以获取命名实例。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-194">By default, the default instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] listens on named pipe `\\.\pipe\sql\query` and `\\.\pipe\MSSQL$<instancename>\sql\query` for a named instance.</span></span> <span data-ttu-id="f3e3b-195">您不能使用备用管道名称连接到 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-195">You cannot connect to an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] by using an alternate pipe name.</span></span>  
  
 <span data-ttu-id="f3e3b-196">lpc</span><span class="sxs-lookup"><span data-stu-id="f3e3b-196">lpc</span></span>  
 <span data-ttu-id="f3e3b-197">本地过程调用。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-197">Local procedure call.</span></span> <span data-ttu-id="f3e3b-198">如果客户端要连接到同一计算机上的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 实例，则可以使用此 Shared Memory 协议。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-198">This shared memory protocol is available if the client is connecting to an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] on the same computer.</span></span>  
  
 <span data-ttu-id="f3e3b-199">**/Q**</span><span class="sxs-lookup"><span data-stu-id="f3e3b-199">**/Q**</span></span>  
 <span data-ttu-id="f3e3b-200">在静默模式下运行 **SQLdiag** 。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-200">Runs **SQLdiag** in quiet mode.</span></span> <span data-ttu-id="f3e3b-201">**/Q** 可取消所有提示，如密码提示。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-201">**/Q** suppresses all prompts, such as password prompts.</span></span>  
  
 <span data-ttu-id="f3e3b-202">**/G**</span><span class="sxs-lookup"><span data-stu-id="f3e3b-202">**/G**</span></span>  
 <span data-ttu-id="f3e3b-203">在常规模式下运行 **SQLdiag** 。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-203">Runs **SQLdiag** in generic mode.</span></span> <span data-ttu-id="f3e3b-204">指定 **/G** 后， **SQLdiag** 在启动时不会强制执行 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 连接检查或验证用户是否为 **sysadmin** 固定服务器角色的成员。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-204">When **/G** is specified, on startup **SQLdiag** does not enforce [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] connectivity checks or verify that the user is a member of the **sysadmin** fixed server role.</span></span> <span data-ttu-id="f3e3b-205">**SQLdiag** 会让 Windows 来确定用户是否具有收集各个请求的诊断信息的相应权限。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-205">Instead, **SQLdiag** defers to Windows to determine whether a user has the appropriate rights to gather each requested diagnostic.</span></span>  
  
 <span data-ttu-id="f3e3b-206">如果未指定 **/G** ，则 **SQLdiag** 将进行检查，以确定用户是否为 Windows **Administrators** 组的成员，如果该用户不是 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Administrators **组成员，则不收集** 诊断信息。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-206">If **/G** is not specified, **SQLdiag** checks to determine whether the user is a member of the Windows **Administrators** group, and will not collect [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] diagnostics if the user is not an **Administrators** group member.</span></span>  
  
 <span data-ttu-id="f3e3b-207">**/R**</span><span class="sxs-lookup"><span data-stu-id="f3e3b-207">**/R**</span></span>  
 <span data-ttu-id="f3e3b-208">将 **SQLdiag** 注册为服务。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-208">Registers **SQLdiag** as a service.</span></span> <span data-ttu-id="f3e3b-209">你将 **SQLdiag** 注册为服务时指定的所有命令行参数，都将留到以后用来运行该服务。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-209">Any command line arguments that are specified when you register **SQLdiag** as a service are preserved for future runs of the service.</span></span>  
  
 <span data-ttu-id="f3e3b-210">将 **SQLdiag** 注册为服务时，默认服务名称为 SQLDIAG。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-210">When **SQLdiag** is registered as a service, the default service name is SQLDIAG.</span></span> <span data-ttu-id="f3e3b-211">可以使用 **/A** 参数更改服务名称。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-211">You can change the service name by using the **/A** argument.</span></span>  
  
 <span data-ttu-id="f3e3b-212">使用 **START** 命令行参数可以启动该服务：</span><span class="sxs-lookup"><span data-stu-id="f3e3b-212">Use the **START** command line argument to start the service:</span></span>  
  
 <span data-ttu-id="f3e3b-213">**SQLDIAG START**</span><span class="sxs-lookup"><span data-stu-id="f3e3b-213">**SQLDIAG START**</span></span>  
  
 <span data-ttu-id="f3e3b-214">也可使用 **net start** 命令启动该服务：</span><span class="sxs-lookup"><span data-stu-id="f3e3b-214">You can also use the **net start** command to start the service:</span></span>  
  
 <span data-ttu-id="f3e3b-215">**net start SQLDIAG**</span><span class="sxs-lookup"><span data-stu-id="f3e3b-215">**net start SQLDIAG**</span></span>  
  
 <span data-ttu-id="f3e3b-216">**/U**</span><span class="sxs-lookup"><span data-stu-id="f3e3b-216">**/U**</span></span>  
 <span data-ttu-id="f3e3b-217">将 **SQLdiag** 撤消注册为服务。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-217">Unregisters **SQLdiag** as a service.</span></span>  
  
 <span data-ttu-id="f3e3b-218">如果撤消注册命名的 **SQLdiag** 实例，则也要使用 **/A** 参数。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-218">Use the **/A** argument also if unregistering a named **SQLdiag** instance.</span></span>  
  
 <span data-ttu-id="f3e3b-219">**/L**</span><span class="sxs-lookup"><span data-stu-id="f3e3b-219">**/L**</span></span>  
 <span data-ttu-id="f3e3b-220">如果还分别使用 **/B** 或 **/E** 参数指定了开始时间或结束时间，则以连续模式运行 **SQLdiag** 。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-220">Runs **SQLdiag** in continuous mode when a start time or end time is also specified with the **/B** or **/E** arguments, respectively.</span></span> <span data-ttu-id="f3e3b-221">在诊断信息收集工作因预定关闭而停止后，**SQLdiag** 会自动重新启动。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-221">**SQLdiag** automatically restarts after diagnostics collection stops due to a scheduled shutdown.</span></span> <span data-ttu-id="f3e3b-222">例如，使用 **/E** 或 **/X** 参数。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-222">For example, by using the **/E** or the **/X** arguments.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f3e3b-223">如果未使用**SQLdiag** 和 **/L** 命令行参数指定开始时间或结束时间，则 **SQLdiag** 将忽略 **/L** comm将忽略 line arguments.</span><span class="sxs-lookup"><span data-stu-id="f3e3b-223">**SQLdiag** ignores the **/L** argument if a start time or end time is not specified by using the **/B** and **/E** command line arguments.</span></span>  
  
 <span data-ttu-id="f3e3b-224">使用 **/L** 并不表示是服务模式。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-224">Using **/L** does not imply the service mode.</span></span> <span data-ttu-id="f3e3b-225">若要在 **SQLdiag** 作为服务运行时使用 **/L** ，请在注册该服务时的命令行中指定它。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-225">To use **/L** when running **SQLdiag** as a service, specify it on the command line when you register the service.</span></span>  
  
 <span data-ttu-id="f3e3b-226">**/X**</span><span class="sxs-lookup"><span data-stu-id="f3e3b-226">**/X**</span></span>  
 <span data-ttu-id="f3e3b-227">在快照模式下运行 **SQLdiag** 。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-227">Runs **SQLdiag** in snapshot mode.</span></span> <span data-ttu-id="f3e3b-228">**SQLdiag** 会拍摄所有配置的诊断信息的快照，然后自动关闭。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-228">**SQLdiag** takes a snapshot of all configured diagnostics and then shuts down automatically.</span></span>  
  
 <span data-ttu-id="f3e3b-229">**START** | **STOP** | **STOP_ABORT**</span><span class="sxs-lookup"><span data-stu-id="f3e3b-229">**START** | **STOP** | **STOP_ABORT**</span></span>  
 <span data-ttu-id="f3e3b-230">启动或停止 **SQLdiag** 服务。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-230">Starts or stops the **SQLdiag** service.</span></span> <span data-ttu-id="f3e3b-231">**STOP_ABORT** 强制在服务未完成当前正在进行的诊断信息收集的情况下尽快地关闭该服务。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-231">**STOP_ABORT** forces the service to shut down as quickly as possible without finishing collection of diagnostics it is currently collecting.</span></span>  
  
 <span data-ttu-id="f3e3b-232">使用这些服务控制参数时，它们必须为命令行中使用的第一个参数。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-232">When these service control arguments are used, they must be the first argument used on the command line.</span></span> <span data-ttu-id="f3e3b-233">例如：</span><span class="sxs-lookup"><span data-stu-id="f3e3b-233">For example:</span></span>  
  
 <span data-ttu-id="f3e3b-234">**SQLDIAG START**</span><span class="sxs-lookup"><span data-stu-id="f3e3b-234">**SQLDIAG START**</span></span>  
  
 <span data-ttu-id="f3e3b-235">只有指定 **SQLdiag** 命名实例的 **/A**参数才可以与 **START**、 **STOP**或 **STOP_ABORT** 一起使用，以控制特定的 **SQLdiag** 服务实例。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-235">Only the **/A** argument, which specifies a named instance of **SQLdiag**, can be used with **START**, **STOP**, or **STOP_ABORT** to control a specific instance of the **SQLdiag** service.</span></span> <span data-ttu-id="f3e3b-236">例如：</span><span class="sxs-lookup"><span data-stu-id="f3e3b-236">For example:</span></span>  
  
 <span data-ttu-id="f3e3b-237">**SQLDIAG START /A** _SQLdiag_application_name_</span><span class="sxs-lookup"><span data-stu-id="f3e3b-237">**SQLDIAG START /A** _SQLdiag_application_name_</span></span>  
  
## <a name="security-requirements"></a><span data-ttu-id="f3e3b-238">安全要求</span><span class="sxs-lookup"><span data-stu-id="f3e3b-238">Security Requirements</span></span>  
 <span data-ttu-id="f3e3b-239">除非以通用模式（通过指定 /G 命令行参数）运行 SQLdiag，否则运行 SQLdiag 的用户必须为 Windows“管理员”组的成员和 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] sysadmin 固定服务器角色的成员。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-239">Unless **SQLdiag** is run in generic mode (by specifying the **/G** command line argument), the user who runs **SQLdiag** must be a member of the Windows **Administrators** group and a member of the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] **sysadmin** fixed server role.</span></span> <span data-ttu-id="f3e3b-240">默认情况下， **SQLdiag** 使用 Windows 身份验证连接到 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ，但是它也支持 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 身份验证。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-240">By default, **SQLdiag** connects to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] by using Windows Authentication, but it also supports [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
## <a name="performance-considerations"></a><span data-ttu-id="f3e3b-241">性能注意事项</span><span class="sxs-lookup"><span data-stu-id="f3e3b-241">Performance Considerations</span></span>  
 <span data-ttu-id="f3e3b-242">运行 **SQLdiag** 的性能效果取决于其配置收集的诊断数据的类型。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-242">The performance effects of running **SQLdiag** depend on the type of diagnostic data you have configured it to collect.</span></span> <span data-ttu-id="f3e3b-243">例如，如果已配置 **SQLdiag** 来收集 [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] 跟踪信息，则选择跟踪的事件类越多，服务器性能所受的影响就越大。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-243">For example, if you have configured **SQLdiag** to collect [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] tracing information, the more event classes you choose to trace, the more your server performance is affected.</span></span>  
  
 <span data-ttu-id="f3e3b-244">运行 **SQLdiag** 对服务器性能的影响大体相当于分别收集配置的诊断信息的开销之和。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-244">The performance impact of running **SQLdiag** is approximately equivalent to the sum of the costs of collecting the configured diagnostics separately.</span></span> <span data-ttu-id="f3e3b-245">例如，使用 **SQLdiag** 收集某个跟踪和使用 [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)]收集该跟踪所产生的性能开销相同。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-245">For example, collecting a trace with **SQLdiag** incurs the same performance cost as collecting it with [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)].</span></span> <span data-ttu-id="f3e3b-246">使用 **SQLdiag** 对性能的影响可以忽略不计。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-246">The performance impact of using **SQLdiag** is negligible.</span></span>  
  
## <a name="required-disk-space"></a><span data-ttu-id="f3e3b-247">所需磁盘空间</span><span class="sxs-lookup"><span data-stu-id="f3e3b-247">Required Disk Space</span></span>  
 <span data-ttu-id="f3e3b-248">因为 **SQLdiag** 可收集不同类型的诊断信息，所以，运行 **SQLdiag** 所需的可用磁盘空间也有所不同。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-248">Because **SQLdiag** can collect different types of diagnostic information, the free disk space that is required to run **SQLdiag** varies.</span></span> <span data-ttu-id="f3e3b-249">诊断信息的收集量取决于服务器正在处理的工作负荷的性质和数量，范围可以从数 MB 到数 GB。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-249">The amount of diagnostic information collected depends on the nature and volume of the workload that the server is processing and may range from a few megabytes to several gigabytes.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="f3e3b-250">配置文件</span><span class="sxs-lookup"><span data-stu-id="f3e3b-250">Configuration Files</span></span>  
 <span data-ttu-id="f3e3b-251">**SQLdiag** 启动时会读取指定的配置文件和命令行参数。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-251">On startup, **SQLdiag** reads the configuration file and the command line arguments that have been specified.</span></span> <span data-ttu-id="f3e3b-252">可以在配置文件中指定 **SQLdiag** 收集的诊断信息的类型。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-252">You specify the types of diagnostic information that **SQLdiag** collects in the configuration file.</span></span> <span data-ttu-id="f3e3b-253">默认情况下， **SQLdiag** 使用 SQLDiag.Xml 配置文件，每次运行工具时都会提取该文件，它位于 **SQLdiag** 实用工具启动文件夹中。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-253">By default, **SQLdiag** uses the SQLDiag.Xml configuration file, which is extracted each time the tool runs and is located in the **SQLdiag** utility startup folder.</span></span> <span data-ttu-id="f3e3b-254">配置文件使用 XML 架构 SQLDiag_schema.xsd，每次运行 **SQLdiag** 时，也会将该架构从可执行文件提取到实用工具启动目录中。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-254">The configuration file uses the XML schema, SQLDiag_schema.xsd, which is also extracted into the utility startup directory from the executable file each time **SQLdiag** runs.</span></span>  
  
### <a name="editing-the-configuration-files"></a><span data-ttu-id="f3e3b-255">编辑配置文件</span><span class="sxs-lookup"><span data-stu-id="f3e3b-255">Editing the Configuration Files</span></span>  
 <span data-ttu-id="f3e3b-256">可以复制和编辑 SQLDiag.Xml，以更改 **SQLdiag** 收集的诊断数据的类型。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-256">You can copy and edit SQLDiag.Xml to change the types of diagnostic data that **SQLdiag** collects.</span></span> <span data-ttu-id="f3e3b-257">编辑配置文件时，请始终使用可将配置文件对照其 XML 架构进行验证的 XML 编辑器，如 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-257">When editing the configuration file always use an XML editor that can validate the configuration file against its XML schema, such as [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)].</span></span> <span data-ttu-id="f3e3b-258">不应直接编辑 SQLDiag.Xml。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-258">You should not edit SQLDiag.Xml directly.</span></span> <span data-ttu-id="f3e3b-259">而应制作一个 SQLDiag.Xml 副本，为副本指定一个新名称并将其存储在同一文件夹中。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-259">Instead, make a copy of SQLDiag.Xml and rename it to a new file name in the same folder.</span></span> <span data-ttu-id="f3e3b-260">然后，编辑此新文件，并使用 **/I** 参数将该文件传递给 **SQLdiag**。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-260">Then edit the new file, and use the **/I** argument to pass it to **SQLdiag**.</span></span>  
  
#### <a name="editing-the-configuration-file-when-sqldiag-runs-as-a-service"></a><span data-ttu-id="f3e3b-261">SQLdiag 作为服务运行时编辑配置文件</span><span class="sxs-lookup"><span data-stu-id="f3e3b-261">Editing the Configuration File When SQLdiag Runs as a Service</span></span>  
 <span data-ttu-id="f3e3b-262">如果已将 **SQLdiag** 作为服务运行并需要编辑配置文件，请指定 **/U** 命令行参数以撤消注册 SQLDIAG 服务，然后使用 **/R** 命令行参数重新注册服务。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-262">If you have already run **SQLdiag** as a service and need to edit the configuration file, unregister the SQLDIAG service by specifying the **/U** command line argument and then re-register the service by using the **/R** command line argument.</span></span> <span data-ttu-id="f3e3b-263">撤消服务注册和重新注册服务会删除 Windows 注册表中缓存的旧配置信息。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-263">Unregistering and re-registering the service removes old configuration information that was cached in the Windows registry.</span></span>  
  
## <a name="output-folder"></a><span data-ttu-id="f3e3b-264">输出文件夹</span><span class="sxs-lookup"><span data-stu-id="f3e3b-264">Output Folder</span></span>  
 <span data-ttu-id="f3e3b-265">如果未使用 **/O** 参数指定输出文件夹， **SQLdiag** 将在 **SQLdiag** 启动文件夹下创建一个名为 SQLDIAG 的子文件夹。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-265">If you do not specify an output folder with the **/O** argument, **SQLdiag** creates a subfolder named SQLDIAG under the **SQLdiag** startup folder.</span></span> <span data-ttu-id="f3e3b-266">对于涉及大量跟踪的诊断信息收集（例如使用 [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] 时），请确保输出文件夹位于本地驱动器，并有足够的空间存储请求的诊断信息输出。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-266">For diagnostic information collection that involves high volume tracing, such as [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] , make sure that the output folder is on a local drive with enough space to store the requested diagnostic output.</span></span>  
  
 <span data-ttu-id="f3e3b-267">重新启动 **SQLdiag** 后，它将覆盖输出文件夹的内容。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-267">When **SQLdiag** is restarted, it overwrites the contents of the output folder.</span></span> <span data-ttu-id="f3e3b-268">若要避免出现这种情况，请在命令行中指定 **/N 2** 。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-268">To avoid this, specify **/N 2** on the command line.</span></span>  
  
## <a name="data-collection-process"></a><span data-ttu-id="f3e3b-269">数据收集过程</span><span class="sxs-lookup"><span data-stu-id="f3e3b-269">Data Collection Process</span></span>  
 <span data-ttu-id="f3e3b-270">在 **SQLdiag** 启动时，它会执行收集 SQLDiag.Xml 中指定的诊断数据所必需的初始化检查。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-270">When **SQLdiag** starts, it performs the initialization checks necessary to collect the diagnostic data that have been specified in SQLDiag.Xml.</span></span> <span data-ttu-id="f3e3b-271">该过程需要持续数秒。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-271">This process may take several seconds.</span></span> <span data-ttu-id="f3e3b-272">如果 **SQLdiag** 作为控制台应用程序运行，则在它开始收集诊断数据时会显示一条消息，通知你 **SQLdiag** 已开始收集，你可以按 CTRL+C 停止收集。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-272">After **SQLdiag** has started collecting diagnostic data when it is run as a console application, a message displays informing you that **SQLdiag** collection has started and that you can press CTRL+C to stop it.</span></span> <span data-ttu-id="f3e3b-273">如果 **SQLdiag** 作为服务运行，类似消息将被写入 Windows 事件日志。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-273">When **SQLdiag** is run as a service, a similar message is written to the Windows event log.</span></span>  
  
 <span data-ttu-id="f3e3b-274">如果要使用 **SQLdiag** 诊断可以再现的问题，则请等到收到此消息后再在服务器中再现问题。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-274">If you are using **SQLdiag** to diagnose a problem that you can reproduce, wait until you receive this message before you reproduce the problem on your server.</span></span>  
  
 <span data-ttu-id="f3e3b-275">**SQLdiag** 以并行方式收集大多数诊断数据。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-275">**SQLdiag** collects most diagnostic data in parallel.</span></span> <span data-ttu-id="f3e3b-276">除了通过 Windows 性能日志和事件日志收集的信息之外，所有诊断信息都是通过连接到工具（如 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] sqlcmd 实用工具或 Windows 命令处理器）来收集的。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-276">All diagnostic information is collected by connecting to tools, such as the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] **sqlcmd** utility or the Windows command processor, except when information is collected from Windows performance logs and event logs.</span></span> <span data-ttu-id="f3e3b-277">**SQLdiag** 在每台计算机上使用一个工作线程来监视其他工具的诊断数据收集，经常会同时等待几个工具完成操作。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-277">**SQLdiag** uses one worker thread per computer to monitor the diagnostic data collection of these other tools, often simultaneously waiting for several tools to complete.</span></span> <span data-ttu-id="f3e3b-278">在收集过程中， **SQLdiag** 会将每个诊断信息的输出内容传送到输出文件夹。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-278">During the collection process, **SQLdiag** routes the output from each diagnostic to the output folder.</span></span>  
  
## <a name="stopping-data-collection"></a><span data-ttu-id="f3e3b-279">停止数据收集</span><span class="sxs-lookup"><span data-stu-id="f3e3b-279">Stopping Data Collection</span></span>  
 <span data-ttu-id="f3e3b-280">**SQLdiag** 在开始收集诊断数据后会持续进行收集，直至收集被停止或在配置好的指定时间停止。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-280">After **SQLdiag** starts collecting diagnostic data, it continues to do so unless you stop it or it is configured to stop at a specified time.</span></span> <span data-ttu-id="f3e3b-281">可以使用 **/E** 参数或 **/X** 参数将 **SQLdiag** 配置为在指定时间停止，第一个参数允许指定一个停止时间，第二个参数则使 **SQLdiag** 以快照模式运行。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-281">You can configure **SQLdiag** to stop at a specified time by using the **/E** argument, which allows you to specify a stop time, or by using the **/X** argument, which causes **SQLdiag** to run in snapshot mode.</span></span>  
  
 <span data-ttu-id="f3e3b-282">**SQLdiag** 停止时将停止它启动的所有诊断。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-282">When **SQLdiag** stops, it stops all diagnostics it has started.</span></span> <span data-ttu-id="f3e3b-283">例如，它将停止正在收集的 [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] 跟踪，停止执行其正在运行的 [!INCLUDE[tsql](../includes/tsql-md.md)] 脚本，同时还停止它在数据收集期间生成的任何子进程。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-283">For example, it stops [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] traces it was collecting, it stops executing [!INCLUDE[tsql](../includes/tsql-md.md)] scripts it was running, and it stops any sub processes it has spawned during data collection.</span></span> <span data-ttu-id="f3e3b-284">诊断数据收集完成后，便会退出 **SQLdiag** 。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-284">After diagnostic data collection has completed, **SQLdiag** exits.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f3e3b-285">不支持暂停 **SQLdiag** 服务。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-285">Pausing the **SQLdiag** service is not supported.</span></span> <span data-ttu-id="f3e3b-286">如果尝试暂停 **SQLdiag** 服务，则该服务会在完成收集你暂停时它正在收集的诊断信息后停止。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-286">If you attempt to pause the **SQLdiag** service, it stops after it finishes collecting the diagnostics that it was collecting when you paused it.</span></span> <span data-ttu-id="f3e3b-287">如果在停止 **SQLdiag** 后重新启动，则应用程序会重新启动并覆盖输出文件夹。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-287">If you restart **SQLdiag** after stopping it, the application restarts and overwrites the output folder.</span></span> <span data-ttu-id="f3e3b-288">若要避免覆盖输出文件夹，请在命令行中指定 **/N 2** 。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-288">To avoid overwriting the output folder, specify **/N 2** on the command line.</span></span>  
  
 <span data-ttu-id="f3e3b-289">**停止作为控制台应用程序运行的 SQLdiag**</span><span class="sxs-lookup"><span data-stu-id="f3e3b-289">**To stop SQLdiag when running as a console application**</span></span>  
  
 <span data-ttu-id="f3e3b-290">如果正将 **SQLdiag** 作为控制台应用程序运行，则在运行 **SQLdiag** 的控制台窗口中按 CTRL+C 将其停止。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-290">If you are running **SQLdiag** as a console application, press CTRL+C in the console window where **SQLdiag** is running to stop it.</span></span> <span data-ttu-id="f3e3b-291">按下 Ctrl+C 之后，控制台窗口中将显示一条消息，通知你正在终止 **SQLDiag** 数据收集，此时请等待过程结束。该过程可能需要几分钟的时间。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-291">After you press CTRL+C, a message displays in the console window informing you that **SQLDiag** data collection is ending, and that you should wait until the process shuts down, which may take several minutes.</span></span>  
  
 <span data-ttu-id="f3e3b-292">按 Ctrl+C 两次可终止所有子诊断过程并立即终止应用程序。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-292">Press Ctrl+C twice to terminate all child diagnostic processes and immediately terminate the application.</span></span>  
  
 <span data-ttu-id="f3e3b-293">**停止作为服务运行的 SQLdiag**</span><span class="sxs-lookup"><span data-stu-id="f3e3b-293">**To stop SQLdiag when running as a service**</span></span>  
  
 <span data-ttu-id="f3e3b-294">如果将 **SQLdiag** 作为服务运行，则在 **SQLdiag** 启动文件夹中运行 **SQLDiag STOP** 可将其停止。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-294">If you are running **SQLdiag** as a service, run **SQLDiag STOP** in the **SQLdiag** startup folder to stop it.</span></span>  
  
 <span data-ttu-id="f3e3b-295">如果在同一台计算机中运行多个 **SQLdiag** 实例，则停止该服务时，也可以将 **SQLdiag** 实例名传递到命令行中。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-295">If you are running multiple instances of **SQLdiag** on the same computer, you can also pass the **SQLdiag** instance name to on the command line when you stop the service.</span></span> <span data-ttu-id="f3e3b-296">例如，若要停止名为 Instance1 的 **SQLdiag** 实例，请使用以下语法：</span><span class="sxs-lookup"><span data-stu-id="f3e3b-296">For example, to stop a **SQLdiag** instance named Instance1, use the following syntax:</span></span>  
  
```  
SQLDIAG STOP /A Instance1  
```  
  
> [!NOTE]  
>  <span data-ttu-id="f3e3b-297">**/A** 是唯一可以与 **START**、 **STOP**或 **STOP_ABORT**一起使用的命令行参数。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-297">**/A** is the only command-line argument that can be used with **START**, **STOP**, or **STOP_ABORT**.</span></span> <span data-ttu-id="f3e3b-298">如果需要使用服务控制谓词之一指定 **SQLdiag** 命名实例，则在命令行中控制谓词的后面指定 **/A** ，如上述语法示例中所示。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-298">If you need to specify a named instance of **SQLdiag** with one of the service control verbs, specify **/A** after the control verb on the command line as shown in the previous syntax example.</span></span> <span data-ttu-id="f3e3b-299">使用控制谓词时，它们必须为命令行中的第一个参数。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-299">When control verbs are used, they must be the first argument on the command line.</span></span>  
  
 <span data-ttu-id="f3e3b-300">若要尽快停止服务，请在实用工具启动文件夹中运行 **SQLDIAG STOP_ABORT** 。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-300">To stop the service as quickly as possible, run **SQLDIAG STOP_ABORT** in the utility startup folder.</span></span> <span data-ttu-id="f3e3b-301">该命令会在不等待当前正在执行的任何诊断信息收集完成的情况下将其中止。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-301">This command aborts any diagnostics collecting currently being performed without waiting for them to finish.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f3e3b-302">使用 **SQLDiag STOP** 或 **SQLDIAG STOP_ABORT** 以停止 **SQLdiag** 服务。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-302">Use **SQLDiag STOP** or **SQLDIAG STOP_ABORT** to stop the **SQLdiag** service.</span></span> <span data-ttu-id="f3e3b-303">请不要使用 Windows 服务控制台停止 **SQLdiag** 或其他 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 服务。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-303">Do not use the Windows Services Console to stop **SQLdiag** or other [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] services.</span></span>  
  
## <a name="automatically-starting-and-stopping-sqldiag"></a><span data-ttu-id="f3e3b-304">自动启动和停止 SQLdiag</span><span class="sxs-lookup"><span data-stu-id="f3e3b-304">Automatically Starting and Stopping SQLdiag</span></span>  
 <span data-ttu-id="f3e3b-305">若要在指定时间自动启动和停止诊断数据收集，请使用 **/b**_start_time_和 **/e**_stop_time_参数（使用24小时表示法）。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-305">To automatically start and stop diagnostic data collection at a specified time, use the **/B**_start_time_ and **/E**_stop_time_ arguments, using 24-hour notation.</span></span> <span data-ttu-id="f3e3b-306">例如，如果要解决一个总是在 02:00:00 左右出现的问题，可以配置 **SQLdiag** ，使其自动在 01:00 开始收集诊断数据，并自动在 03:00:00 停止收集。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-306">For example, if you are troubleshooting a problem that consistently appears at approximately 02:00:00, you can configure **SQLdiag** to automatically start collecting diagnostic data at 01:00 and automatically stop at 03:00:00.</span></span> <span data-ttu-id="f3e3b-307">可以使用 **/B** 和 **/E** 参数指定开始和停止时间。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-307">Use the **/B** and **/E** arguments to specify the start and stop time.</span></span> <span data-ttu-id="f3e3b-308">请使用 24 小时制来指定确切的开始和停止日期和时间，格式为 YYYYMMDD_HH:MM:SS。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-308">Use 24-hour notation to specify an exact start and stop date and time with the format YYYYMMDD_HH:MM:SS.</span></span> <span data-ttu-id="f3e3b-309">若要指定一个相对的开始或停止时间，请在开始和停止时间之前添加前缀 **+** ，并省略日期部分 (YYYYMMDD_)，如下例所示。在下例中，可使 **SQLdiag** 在等待 1 小时后开始收集信息，然后经过 3 小时的信息收集后便停止并退出：</span><span class="sxs-lookup"><span data-stu-id="f3e3b-309">To specify a relative start or stop time, prefix the start and stop time with **+** and omit the date portion (YYYYMMDD_) as shown in the following example, which causes **SQLdiag** to wait 1 hour before it starts collecting information, then it collects information for 3 hours before it stops and exits:</span></span>  
  
```  
sqldiag /B +01:00:00 /E +03:00:00  
```  
  
 <span data-ttu-id="f3e3b-310">如果指定了相对的 *start_time* ，则 **SQLdiag** 将会在与当前日期和时间相对的某个时间启动。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-310">When a relative *start_time* is specified, **SQLdiag** starts at a time that is relative to the current date and time.</span></span> <span data-ttu-id="f3e3b-311">如果指定了相对的 *end_time* ，则 **SQLdiag** 将会在与指定的 *start_time*相对的某个时间结束。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-311">When a relative *end_time* is specified, **SQLdiag** ends at a time that is relative to the specified *start_time*.</span></span> <span data-ttu-id="f3e3b-312">如果指定的开始或结束日期和时间均为过去的时间，则 **SQLdiag** 将会强行更改开始日期，以使开始日期和时间为将来的时间。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-312">If the start or end date and time that you have specified is in the past, **SQLdiag** forcibly changes the start date so that the start date and time are in the future.</span></span>  
  
 <span data-ttu-id="f3e3b-313">这对所选的开始和结束日期具有重要的意义。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-313">This has important implications on the start and end dates you choose.</span></span> <span data-ttu-id="f3e3b-314">请考虑以下示例：</span><span class="sxs-lookup"><span data-stu-id="f3e3b-314">Consider the following example:</span></span>  
  
```  
sqldiag /B +01:00:00 /E 08:30:00  
```  
  
 <span data-ttu-id="f3e3b-315">如果当前时间为 08:00，则在诊断收集操作实际开始之前，结束时间已经过去。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-315">If the current time is 08:00, the end time passes before diagnostic collection actually begins.</span></span> <span data-ttu-id="f3e3b-316">因为当开始和结束日期为过去的时间时， **SQLDiag** 会自动将开始和结束日期调整为下一天，所以，该示例中的诊断收集将在当天的 09:00（已使用 **+** 指定的一个相对开始时间）开始，一直到第二天早上的 08:30 才结束。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-316">Because **SQLDiag** automatically adjusts start and end dates to the next day when they occur in the past, in this example diagnostic collection starts at 09:00 today (a relative start time has been specified with **+**) and continues collecting until 08:30 the following morning.</span></span>  
  
### <a name="stopping-and-restarting-sqldiag-to-collect-daily-diagnostics"></a><span data-ttu-id="f3e3b-317">停止并重新启动 SQLdiag 以收集每天的诊断信息</span><span class="sxs-lookup"><span data-stu-id="f3e3b-317">Stopping and Restarting SQLdiag to Collect Daily Diagnostics</span></span>  
 <span data-ttu-id="f3e3b-318">若要 **SQLdiag**每天收集一组指定的诊断信息而无需手动启动和停止，可使用 **/L** 参数。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-318">To collect a specified set of diagnostics on a daily basis without having to manually start and stop **SQLdiag**, use the **/L** argument.</span></span> <span data-ttu-id="f3e3b-319">**/L** 参数可以使 **SQLdiag** 在预定时间关闭后自动重新启动，从而实现连续运行。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-319">The **/L** argument causes **SQLdiag** to run continuously by automatically restarting itself after a scheduled shutdown.</span></span> <span data-ttu-id="f3e3b-320">指定了 **/L** 之后，如果 **SQLdiag** 因到达 **/E** 参数指定的结束时间而停止，或者因使用 **/X** 参数在快照模式下运行而停止，则 **SQLdiag** 将会重新启动，而不是退出。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-320">When **/L** is specified, and **SQLdiag** stops because it has reached the end time specified with the **/E** argument, or it stops because it is being run in snapshot mode by using the **/X** argument, **SQLdiag** restarts instead of exiting.</span></span>  
  
 <span data-ttu-id="f3e3b-321">在以下示例中，指定了 **SQLdiag** 以连续模式运行，在 03:00:00 和 05:00:00 之间收集诊断数据后自动重新启动。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-321">The following example specifies that **SQLdiag** run in continuous mode to automatically restart after diagnostic data collecting occurs between 03:00:00 and 05:00:00.</span></span>  
  
```  
sqldiag /B 03:00:00 /E 05:00:00 /L  
```  
  
 <span data-ttu-id="f3e3b-322">在以下示例中，指定了 **SQLdiag** 以连续模式运行，在 03:00:00 拍摄诊断数据快照后自动重新启动。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-322">The following example specifies that **SQLdiag** run in continuous mode to automatically restart after taking a diagnostic data snapshot at 03:00:00.</span></span>  
  
```  
sqldiag /B 03:00:00 /X /L  
```  
  
## <a name="running-sqldiag-as-a-service"></a><span data-ttu-id="f3e3b-323">将 SQLdiag 作为服务运行</span><span class="sxs-lookup"><span data-stu-id="f3e3b-323">Running SQLdiag as a Service</span></span>  
 <span data-ttu-id="f3e3b-324">如果希望使用 **SQLdiag** 长时间收集诊断数据，而在该时间段内可能需要注销运行 **SQLdiag** 的计算机，则可将其作为服务运行。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-324">When you want to use **SQLdiag** to collect diagnostic data for long periods of time during which you might need to log out of the computer on which **SQLdiag** is running, you can run it as a service.</span></span>  
  
 <span data-ttu-id="f3e3b-325">**将 SQLDiag 注册为作为服务运行**</span><span class="sxs-lookup"><span data-stu-id="f3e3b-325">**To register SQLDiag to run as a service**</span></span>  
  
 <span data-ttu-id="f3e3b-326">通过在命令行指定 **/R** 参数，可以将 **SQLdiag** 注册为作为服务运行。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-326">You can register **SQLdiag** to run as a service by specifying the **/R** argument at the command line.</span></span> <span data-ttu-id="f3e3b-327">这会将 **SQLdiag** 注册为作为服务运行。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-327">This registers **SQLdiag** to run as a service.</span></span> <span data-ttu-id="f3e3b-328">**SQLdiag** 服务名为 SQLDIAG。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-328">The **SQLdiag** service name is SQLDIAG.</span></span> <span data-ttu-id="f3e3b-329">将 **SQLDiag** 注册为服务时在命令行上指定的任何其他参数将被保留，以供启动服务时重新使用。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-329">Any other arguments you specify on the command line when you register **SQLDiag** as a service are preserved and reused when the service is started.</span></span>  
  
 <span data-ttu-id="f3e3b-330">若要更改默认的 SQLDIAG 服务名称，请使用 **/A** 命令行参数来指定其他名称。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-330">To change the default SQLDIAG service name, use the **/A** command-line argument to specify another name.</span></span> <span data-ttu-id="f3e3b-331">**SQLdiag** 会自动为使用 **/A** 指定的任意 **SQLdiag** 实例名称添加前缀 DIAG$，以创建有合理的服务名称。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-331">**SQLdiag** automatically prefixes DIAG$ to any **SQLdiag** instance name specified with **/A** to create sensible service names.</span></span>  
  
 <span data-ttu-id="f3e3b-332">**撤消 SQLDIAG 服务注册**</span><span class="sxs-lookup"><span data-stu-id="f3e3b-332">**To unregister the SQLDIAG service**</span></span>  
  
 <span data-ttu-id="f3e3b-333">若要撤消服务注册，请指定 **/U** 参数。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-333">To unregister the service, specify the **/U** argument.</span></span> <span data-ttu-id="f3e3b-334">撤消 **SQLdiag** 的服务注册将同时删除该服务的 Windows 注册表项。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-334">Unregistering **SQLdiag** as a service also deletes the Windows registry keys of the service.</span></span>  
  
 <span data-ttu-id="f3e3b-335">**启动或重新启动 SQLDIAG 服务**</span><span class="sxs-lookup"><span data-stu-id="f3e3b-335">**To start or restart the SQLDIAG service**</span></span>  
  
 <span data-ttu-id="f3e3b-336">若要启动或重新启动 SQLDIAG 服务，请从命令行运行 **SQLDiag START** 。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-336">To start or restart the SQLDIAG service, run **SQLDiag START** from the command line.</span></span>  
  
 <span data-ttu-id="f3e3b-337">如果使用 **/A** 参数运行多个 **SQLdiag** 实例，则启动服务时也可以在命令行中传递 **SQLdiag** 实例名。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-337">If you are running multiple instances of **SQLdiag** by using the **/A** argument, you can also pass the **SQLdiag** instance name on the command line when you start the service.</span></span> <span data-ttu-id="f3e3b-338">例如，若要启动名为 Instance1 的 **SQLdiag** 实例，请使用以下语法：</span><span class="sxs-lookup"><span data-stu-id="f3e3b-338">For example, to start a **SQLdiag** instance named Instance1, use the following syntax:</span></span>  
  
```  
SQLDIAG START /A Instance1  
```  
  
 <span data-ttu-id="f3e3b-339">也可使用 **net start** 命令启动 SQLDIAG 服务。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-339">You can also use the **net start** command to start the SQLDIAG service.</span></span>  
  
 <span data-ttu-id="f3e3b-340">重新启动 **SQLdiag**后，它将覆盖当前输出文件夹中的内容。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-340">When you restart **SQLdiag**, it overwrites the contents in the current output folder.</span></span> <span data-ttu-id="f3e3b-341">若要避免出现这种情况，请在命令行中指定 **/N 2** ，以在实用工具启动时重命名输出文件夹。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-341">To avoid this, specify **/N 2** on the command line to rename the output folder when the utility starts.</span></span>  
  
 <span data-ttu-id="f3e3b-342">不支持暂停 **SQLdiag** 服务。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-342">Pausing the **SQLdiag** service is not supported.</span></span>  
  
## <a name="running-multiple-instances-of-sqldiag"></a><span data-ttu-id="f3e3b-343">运行多个 SQLdiag 实例</span><span class="sxs-lookup"><span data-stu-id="f3e3b-343">Running Multiple Instances of SQLdiag</span></span>  
 <span data-ttu-id="f3e3b-344">通过在命令行上指定 **/a**_SQLdiag_application_name_ ，在同一台计算机上运行多个**SQLdiag**实例。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-344">Run multiple instances of **SQLdiag** on the same computer by specifying **/A**_SQLdiag_application_name_ on the command line.</span></span> <span data-ttu-id="f3e3b-345">这对于同时从同一个 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 实例收集不同诊断信息集的操作会很有用。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-345">This is useful for collecting different sets of diagnostics simultaneously from the same [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="f3e3b-346">例如，可以将 **SQLdiag** 命名实例配置为连续执行轻型数据收集。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-346">For example, you can configure a named instance of **SQLdiag** to continuously perform lightweight data collection.</span></span> <span data-ttu-id="f3e3b-347">然后，如果 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]中出现特定问题，则可以运行默认 **SQLdiag** 实例以收集该问题的诊断信息，也可以收集 [!INCLUDE[msCoName](../includes/msconame-md.md)] 客户支持服务部门要求你收集用以诊断问题的诊断信息集。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-347">Then, if a specific problem occurs on [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], you can run the default **SQLdiag** instance to collect diagnostics for that problem, or to gather a set of diagnostics that [!INCLUDE[msCoName](../includes/msconame-md.md)] Customer Support Services has asked you to gather to diagnose a problem.</span></span>  
  
## <a name="collecting-diagnostic-data-from-clustered-sql-server-instances"></a><span data-ttu-id="f3e3b-348">从群集 SQL Server 实例中收集诊断数据</span><span class="sxs-lookup"><span data-stu-id="f3e3b-348">Collecting Diagnostic Data from Clustered SQL Server Instances</span></span>  
 <span data-ttu-id="f3e3b-349">**SQLdiag** 支持从群集 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 实例中收集诊断数据。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-349">**SQLdiag** supports collecting diagnostic data from clustered [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instances.</span></span> <span data-ttu-id="f3e3b-350">要从群集 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 实例中收集诊断信息，请确保已在配置文件 SQLDiag.Xml 中为 \<Machine> 元素的 name 属性指定了 "."，并且命令行中未指定 /G 参数。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-350">To gather diagnostics from clustered [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instances, make sure that **"."** is specified for the **name** attribute of the **\<Machine>** element in the configuration file SQLDiag.Xml and do not specify the **/G** argument on the command line.</span></span> <span data-ttu-id="f3e3b-351">默认情况下，将在配置文件中为 **name** 属性指定 **"."** ，并禁用 **/G** 参数。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-351">By default, **"."** is specified for the **name** attribute in the configuration file and the **/G** argument is turned off.</span></span> <span data-ttu-id="f3e3b-352">通常，在从群集 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 实例中收集诊断信息时，无需编辑配置文件或更改命令行参数。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-352">Typically, you do not need to edit the configuration file or change the command line arguments when collecting from a clustered [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance.</span></span>  
  
 <span data-ttu-id="f3e3b-353">如果将 **"."** 指定为计算机名称，则 **SQLdiag** 会检测到它正在群集中运行，同时从该群集中安装的所有虚拟 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 实例中检索诊断信息。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-353">When **"."** is specified as the machine name, **SQLdiag** detects that it is running on a cluster, and simultaneously retrieves diagnostic information from all virtual instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] that are installed on the cluster.</span></span> <span data-ttu-id="f3e3b-354">如果只希望从计算机上运行的其中一个虚拟 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 实例中收集诊断信息，请在 SQLDiag.Xml 中为 \<Machine> 元素的 name 属性指定该虚拟 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-354">If you want to collect diagnostic information from only one virtual instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] that is running on a computer, specify that virtual [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] for the **name** attribute of the **\<Machine>** element in SQLDiag.Xml.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f3e3b-355">若要从群集 [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] 实例中收集 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 跟踪信息，必须在群集中启用管理共享 (ADMIN$)。</span><span class="sxs-lookup"><span data-stu-id="f3e3b-355">To collect [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] trace information from clustered [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instances, administrative shares (ADMIN$) must be enabled on the cluster.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3e3b-356">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f3e3b-356">See Also</span></span>  
 [<span data-ttu-id="f3e3b-357">命令提示实用工具参考（数据库引擎）</span><span class="sxs-lookup"><span data-stu-id="f3e3b-357">Command Prompt Utility Reference &#40;Database Engine&#41;</span></span>](command-prompt-utility-reference-database-engine.md)  
  
  
