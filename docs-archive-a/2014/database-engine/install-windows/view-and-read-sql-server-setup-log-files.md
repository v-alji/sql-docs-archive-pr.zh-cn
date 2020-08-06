---
title: 查看和读取 SQL Server 安装程序日志文件 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- viewing logs
- displaying log files
- Setup [SQL Server], logs
- installation log files [SQL Server]
- installing SQL Server, logs
- errors [SQL Server], Setup
- logs [SQL Server], Setup
ms.assetid: 9d77af64-9084-4375-908a-d90f99535062
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 70f9bbb9a8ed72503dc6fe90077232748b2c4ac2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689016"
---
# <a name="view-and-read-sql-server-setup-log-files"></a><span data-ttu-id="83b9b-102">查看和阅读 SQL Server 安装程序日志文件</span><span class="sxs-lookup"><span data-stu-id="83b9b-102">View and Read SQL Server Setup Log Files</span></span>
  <span data-ttu-id="83b9b-103">每次执行安装程序时，将创建日志文件，并在% programfiles% \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \120\Setup Bootstrap\Log 处创建新的带时间戳的日志文件夹 \\ 。</span><span class="sxs-lookup"><span data-stu-id="83b9b-103">Each execution of Setup creates log files are created with a new timestamped log folder at %programfiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup Bootstrap\Log\\.</span></span> <span data-ttu-id="83b9b-104">带有时间戳的日志文件夹的名称格式为 YYYYMMDD_hhmmss。</span><span class="sxs-lookup"><span data-stu-id="83b9b-104">The time-stamped log folder name format is YYYYMMDD_hhmmss.</span></span> <span data-ttu-id="83b9b-105">在无人参与模式下运行安装程序时，将在 % temp%\sqlsetup\*.log 中创建日志。</span><span class="sxs-lookup"><span data-stu-id="83b9b-105">When Setup is run in an unattended mode, the logs are created at % temp%\sqlsetup\*.log.</span></span> <span data-ttu-id="83b9b-106">日志文件夹中的所有文件将归档到各自日志文件夹的 Log\*.cab 文件中。</span><span class="sxs-lookup"><span data-stu-id="83b9b-106">All files in the logs folder are archived into the Log\*.cab file in their respective log folder.</span></span>  
  
 <span data-ttu-id="83b9b-107">一个典型的安装请求将经历以下三个执行阶段：</span><span class="sxs-lookup"><span data-stu-id="83b9b-107">A typical Setup request goes through three execution phases:</span></span>  
  
1.  <span data-ttu-id="83b9b-108">全局规则文本</span><span class="sxs-lookup"><span data-stu-id="83b9b-108">Global rules text</span></span>  
  
2.  <span data-ttu-id="83b9b-109">组件更新</span><span class="sxs-lookup"><span data-stu-id="83b9b-109">Component update</span></span>  
  
3.  <span data-ttu-id="83b9b-110">用户请求的操作</span><span class="sxs-lookup"><span data-stu-id="83b9b-110">User-requested action</span></span>  
  
 <span data-ttu-id="83b9b-111">在每个阶段中，安装程序都生成详细信息日志和摘要日志，并根据需要创建其他日志。</span><span class="sxs-lookup"><span data-stu-id="83b9b-111">In each phase, Setup generates detail and summary logs with additional logs created as appropriate.</span></span> <span data-ttu-id="83b9b-112">在每次执行用户请求的安装操作时安装程序至少会被调用三次。</span><span class="sxs-lookup"><span data-stu-id="83b9b-112">Setup is called at least three times per user-requested Setup action.</span></span>  
  
 <span data-ttu-id="83b9b-113">数据存储文件包含安装过程所跟踪的所有配置对象状态的快照，对于纠正配置错误来说非常有用。</span><span class="sxs-lookup"><span data-stu-id="83b9b-113">Datastore files contain a snapshot of the state of all configuration objects being tracked by the Setup process, and are useful for troubleshooting configuration errors.</span></span> <span data-ttu-id="83b9b-114">XML 文件转储是为每个执行阶段的数据存储对象创建的。</span><span class="sxs-lookup"><span data-stu-id="83b9b-114">XML file dumps are created for datastore objects for each execution phase.</span></span> <span data-ttu-id="83b9b-115">它们保存在带有时间戳的日志文件夹下其自己的日志子文件夹中，如下所示：</span><span class="sxs-lookup"><span data-stu-id="83b9b-115">They are saved in their own log subfolder under the time-stamped log folder, as follows:</span></span>  
  
-   <span data-ttu-id="83b9b-116">Datastore_GlobalRules</span><span class="sxs-lookup"><span data-stu-id="83b9b-116">Datastore_GlobalRules</span></span>  
  
-   <span data-ttu-id="83b9b-117">Datastore_ComponentUpdated</span><span class="sxs-lookup"><span data-stu-id="83b9b-117">Datastore_ComponentUpdated</span></span>  
  
-   <span data-ttu-id="83b9b-118">数据存储</span><span class="sxs-lookup"><span data-stu-id="83b9b-118">Datastore</span></span>  
  
 <span data-ttu-id="83b9b-119">以下部分介绍 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装程序日志文件。</span><span class="sxs-lookup"><span data-stu-id="83b9b-119">The following sections describe [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup log files.</span></span>  
  
## <a name="summary-text"></a><span data-ttu-id="83b9b-120">摘要文本</span><span class="sxs-lookup"><span data-stu-id="83b9b-120">Summary Text</span></span>  
  
### <a name="overview"></a><span data-ttu-id="83b9b-121">概述</span><span class="sxs-lookup"><span data-stu-id="83b9b-121">Overview</span></span>  
 <span data-ttu-id="83b9b-122">此文件显示在安装过程中检测到的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 组件、操作系统环境、命令行参数值（如果已指定），以及执行的每个 MSI/MSP 的总体状态。</span><span class="sxs-lookup"><span data-stu-id="83b9b-122">This file shows the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] components that were detected during Setup, the operating system environment, command-line parameter values if they are specified, and the overall status of each MSI/MSP that was executed.</span></span>  
  
 <span data-ttu-id="83b9b-123">本日志归纳为以下部分：</span><span class="sxs-lookup"><span data-stu-id="83b9b-123">The log is organized into the following sections:</span></span>  
  
-   <span data-ttu-id="83b9b-124">执行的总体摘要</span><span class="sxs-lookup"><span data-stu-id="83b9b-124">An overall summary of the execution</span></span>  
  
-   <span data-ttu-id="83b9b-125">运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装程序的计算机的属性和配置</span><span class="sxs-lookup"><span data-stu-id="83b9b-125">Properties and the configuration of the computer where [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup was run</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="83b9b-126">产品功能</span><span class="sxs-lookup"><span data-stu-id="83b9b-126">product features previously installed on the computer</span></span>  
  
-   <span data-ttu-id="83b9b-127">安装版本和安装包属性的说明</span><span class="sxs-lookup"><span data-stu-id="83b9b-127">Description of the installation version and installation package properties</span></span>  
  
-   <span data-ttu-id="83b9b-128">安装过程中提供的运行时输入设置</span><span class="sxs-lookup"><span data-stu-id="83b9b-128">Runtime input settings that are provided during install</span></span>  
  
-   <span data-ttu-id="83b9b-129">配置文件的位置</span><span class="sxs-lookup"><span data-stu-id="83b9b-129">Location of the configuration file</span></span>  
  
-   <span data-ttu-id="83b9b-130">执行结果的详细信息</span><span class="sxs-lookup"><span data-stu-id="83b9b-130">Details of the execution results</span></span>  
  
-   <span data-ttu-id="83b9b-131">全局规则</span><span class="sxs-lookup"><span data-stu-id="83b9b-131">Global rules</span></span>  
  
-   <span data-ttu-id="83b9b-132">特定于安装方案的规则</span><span class="sxs-lookup"><span data-stu-id="83b9b-132">Rules specific to the installation scenario</span></span>  
  
-   <span data-ttu-id="83b9b-133">失败的规则</span><span class="sxs-lookup"><span data-stu-id="83b9b-133">Failed rules</span></span>  
  
-   <span data-ttu-id="83b9b-134">规则报表文件的位置</span><span class="sxs-lookup"><span data-stu-id="83b9b-134">Location of the rules report file</span></span>  
  
### <a name="location"></a><span data-ttu-id="83b9b-135">位置</span><span class="sxs-lookup"><span data-stu-id="83b9b-135">Location</span></span>  
 <span data-ttu-id="83b9b-136">它位于% programfiles% \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \120\Setup Bootstrap\Log \\ 。</span><span class="sxs-lookup"><span data-stu-id="83b9b-136">It is located at %programfiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup Bootstrap\Log\\.</span></span>  
  
 <span data-ttu-id="83b9b-137">若要找到摘要文本文件中的错误，请使用“error”或“failed”关键字搜索该文件。</span><span class="sxs-lookup"><span data-stu-id="83b9b-137">To find errors in the summary text file, search the file by using the "error" or "failed" keywords.</span></span>  
  
## <a name="summary_engine-base_yyyymmdd_hhmmsstxt"></a><span data-ttu-id="83b9b-138">Summary_engine-base_YYYYMMDD_HHMMss.txt</span><span class="sxs-lookup"><span data-stu-id="83b9b-138">Summary_engine-base_YYYYMMDD_HHMMss.txt</span></span>  
  
### <a name="overview"></a><span data-ttu-id="83b9b-139">概述</span><span class="sxs-lookup"><span data-stu-id="83b9b-139">Overview</span></span>  
 <span data-ttu-id="83b9b-140">summary_engine 基本文件类似于摘要文件，是在主工作流中生成的。</span><span class="sxs-lookup"><span data-stu-id="83b9b-140">The summary_engine base file is similar to the summary file and is generated during the main workflow.</span></span>  
  
### <a name="location"></a><span data-ttu-id="83b9b-141">位置</span><span class="sxs-lookup"><span data-stu-id="83b9b-141">Location</span></span>  
 <span data-ttu-id="83b9b-142">它位于% programfiles% \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \120\Setup Bootstrap\Log \\<YYYYMMDD_HHMM>\\ 。</span><span class="sxs-lookup"><span data-stu-id="83b9b-142">It is located at %programfiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup Bootstrap\Log\\<YYYYMMDD_HHMM>\\.</span></span>  
  
## <a name="summary_engine-base_yyyymmdd_hhmmss_componentupdatetxt"></a><span data-ttu-id="83b9b-143">Summary_engine-base_YYYYMMDD_HHMMss_ComponentUpdate.txt</span><span class="sxs-lookup"><span data-stu-id="83b9b-143">Summary_engine-base_YYYYMMDD_HHMMss_ComponentUpdate.txt</span></span>  
  
### <a name="overview"></a><span data-ttu-id="83b9b-144">概述</span><span class="sxs-lookup"><span data-stu-id="83b9b-144">Overview</span></span>  
 <span data-ttu-id="83b9b-145">组件更新摘要日志文件类似于摘要文件，是在组件更新工作流中生成的。</span><span class="sxs-lookup"><span data-stu-id="83b9b-145">The component update summary log file is similar to the summary file and is generated during the component update workflow.</span></span>  
  
### <a name="location"></a><span data-ttu-id="83b9b-146">位置</span><span class="sxs-lookup"><span data-stu-id="83b9b-146">Location</span></span>  
 <span data-ttu-id="83b9b-147">它位于% programfiles% \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \120\Setup Bootstrap\Log \\<YYYYMMDD_HHMM>\\ 。</span><span class="sxs-lookup"><span data-stu-id="83b9b-147">It is located at %programfiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup Bootstrap\Log\\<YYYYMMDD_HHMM>\\.</span></span>  
  
## <a name="summary_engine-base_versionnumbermmdd_hhmmss_globalrulestxt"></a><span data-ttu-id="83b9b-148">Summary_engine-base_ \<VersionNumber>MMDD_HHMMss_GlobalRules.txt</span><span class="sxs-lookup"><span data-stu-id="83b9b-148">Summary_engine-base_\<VersionNumber>MMDD_HHMMss_GlobalRules.txt</span></span>  
  
### <a name="overview"></a><span data-ttu-id="83b9b-149">概述</span><span class="sxs-lookup"><span data-stu-id="83b9b-149">Overview</span></span>  
 <span data-ttu-id="83b9b-150">全局规则摘要日志文件类似于摘要文件，是在全局规则工作流中生成的。</span><span class="sxs-lookup"><span data-stu-id="83b9b-150">The global rules summary log file is similar to the summary file generated during the global rules workflow.</span></span>  
  
### <a name="location"></a><span data-ttu-id="83b9b-151">位置</span><span class="sxs-lookup"><span data-stu-id="83b9b-151">Location</span></span>  
 <span data-ttu-id="83b9b-152">它位于% programfiles% \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \120\Setup Bootstrap\Log \\<YYYYMMDD_HHMM>\\ 。</span><span class="sxs-lookup"><span data-stu-id="83b9b-152">It is located at %programfiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup Bootstrap\Log\\<YYYYMMDD_HHMM>\\.</span></span>  
  
## <a name="detailtxt"></a><span data-ttu-id="83b9b-153">Detail.txt</span><span class="sxs-lookup"><span data-stu-id="83b9b-153">Detail.txt</span></span>  
  
### <a name="overview"></a><span data-ttu-id="83b9b-154">概述</span><span class="sxs-lookup"><span data-stu-id="83b9b-154">Overview</span></span>  
 <span data-ttu-id="83b9b-155">Detail.txt 是针对主工作流（如安装或升级）生成的，它提供有关执行的详细信息。</span><span class="sxs-lookup"><span data-stu-id="83b9b-155">Detail.txt is generated for the main workflow such as install or upgrade, and provides the details of the execution.</span></span> <span data-ttu-id="83b9b-156">文件中的日志基于调用每个安装操作的时间而生成，并且显示操作的执行顺序以及其依赖项。</span><span class="sxs-lookup"><span data-stu-id="83b9b-156">The logs in the file are generated based on the time when each action for the installation was invoked, and show the order in which the actions were executed, and their dependencies.</span></span>  
  
### <a name="location"></a><span data-ttu-id="83b9b-157">位置</span><span class="sxs-lookup"><span data-stu-id="83b9b-157">Location</span></span>  
 <span data-ttu-id="83b9b-158">它位于% programfiles% \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \120\Setup</span><span class="sxs-lookup"><span data-stu-id="83b9b-158">It is located at %programfiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup</span></span>  
  
 <span data-ttu-id="83b9b-159">Bootstrap\Log\\<YYYYMMDD_HHMM>\Detail.txt。</span><span class="sxs-lookup"><span data-stu-id="83b9b-159">Bootstrap\Log\\<YYYYMMDD_HHMM>\Detail.txt.</span></span>  
  
 <span data-ttu-id="83b9b-160">如果在安装过程中发生错误，则将异常或错误记录在该文件的末尾。</span><span class="sxs-lookup"><span data-stu-id="83b9b-160">If an error occurs during the Setup process, the exception or error are logged at the end of this file.</span></span> <span data-ttu-id="83b9b-161">若要查找该文件中的错误，请首先检查文件末尾，然后在文件中搜索“错误”或“异常”关键字。</span><span class="sxs-lookup"><span data-stu-id="83b9b-161">To find the errors in this file, first examine the end of the file followed by a search of the file for the "error" or "exception" keywords.</span></span>  
  
## <a name="detail_componentupdatetxt"></a><span data-ttu-id="83b9b-162">Detail_ComponentUpdate.txt</span><span class="sxs-lookup"><span data-stu-id="83b9b-162">Detail_ComponentUpdate.txt</span></span>  
  
### <a name="overview"></a><span data-ttu-id="83b9b-163">概述</span><span class="sxs-lookup"><span data-stu-id="83b9b-163">Overview</span></span>  
 <span data-ttu-id="83b9b-164">Detail_ComponentUpdate.txt 文件是针对组件更新工作流而生成的，它类似于 Detail.txt。</span><span class="sxs-lookup"><span data-stu-id="83b9b-164">The Detail_ComponentUpdate.txt file is generated for the component update workflow and is similar to Detail.txt.</span></span>  
  
### <a name="location"></a><span data-ttu-id="83b9b-165">位置</span><span class="sxs-lookup"><span data-stu-id="83b9b-165">Location</span></span>  
 <span data-ttu-id="83b9b-166">它位于% programfiles% \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \120\Setup Bootstrap\Log \\<YYYYMMDD_HHMM>\\ 。</span><span class="sxs-lookup"><span data-stu-id="83b9b-166">It is located at %programfiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup Bootstrap\Log\\<YYYYMMDD_HHMM>\\.</span></span>  
  
## <a name="detail_globalrulestxt"></a><span data-ttu-id="83b9b-167">Detail_GlobalRules.txt</span><span class="sxs-lookup"><span data-stu-id="83b9b-167">Detail_GlobalRules.txt</span></span>  
  
### <a name="overview"></a><span data-ttu-id="83b9b-168">概述</span><span class="sxs-lookup"><span data-stu-id="83b9b-168">Overview</span></span>  
 <span data-ttu-id="83b9b-169">Detail_GlobalRules.txt 是针对全局规则执行而生成的，它类似于 Detail.txt。</span><span class="sxs-lookup"><span data-stu-id="83b9b-169">Detail_GlobalRules.txt is generated for the global rules execution and is similar to Detail.txt.</span></span>  
  
### <a name="location"></a><span data-ttu-id="83b9b-170">位置</span><span class="sxs-lookup"><span data-stu-id="83b9b-170">Location</span></span>  
 <span data-ttu-id="83b9b-171">它位于% programfiles% \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \120\Setup Bootstrap\Log \\<YYYYMMDD_HHMM>\\ 。</span><span class="sxs-lookup"><span data-stu-id="83b9b-171">It is located at %programfiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup Bootstrap\Log\\<YYYYMMDD_HHMM>\\.</span></span>  
  
## <a name="msi-log-files"></a><span data-ttu-id="83b9b-172">MSI 日志文件</span><span class="sxs-lookup"><span data-stu-id="83b9b-172">MSI log files</span></span>  
  
### <a name="overview"></a><span data-ttu-id="83b9b-173">概述</span><span class="sxs-lookup"><span data-stu-id="83b9b-173">Overview</span></span>  
 <span data-ttu-id="83b9b-174">MSI 日志文件提供安装包进程的详细信息。</span><span class="sxs-lookup"><span data-stu-id="83b9b-174">The MSI log files provide details of the installation package process.</span></span> <span data-ttu-id="83b9b-175">它们是在安装指定的包的过程中由 MSIEXEC 生成的。</span><span class="sxs-lookup"><span data-stu-id="83b9b-175">They are generated by the MSIEXEC during the installation of the specified package.</span></span>  
  
 <span data-ttu-id="83b9b-176">MSI 日志文件的类型：</span><span class="sxs-lookup"><span data-stu-id="83b9b-176">Types of MSI log files:</span></span>  
  
-   <span data-ttu-id="83b9b-177">\<Feature>_\<Architecture>\_\<Interaction>.log</span><span class="sxs-lookup"><span data-stu-id="83b9b-177">\<Feature>_\<Architecture>\_\<Interaction>.log</span></span>  
  
-   <span data-ttu-id="83b9b-178">\<Feature>_\<Architecture>\_\<Language>\_\<Interaction>.log</span><span class="sxs-lookup"><span data-stu-id="83b9b-178">\<Feature>_\<Architecture>\_\<Language>\_\<Interaction>.log</span></span>  
  
-   <span data-ttu-id="83b9b-179">\<Feature>_\<Architecture>\_\<Interaction>\_\<workflow>.log</span><span class="sxs-lookup"><span data-stu-id="83b9b-179">\<Feature>_\<Architecture>\_\<Interaction>\_\<workflow>.log</span></span>  
  
### <a name="location"></a><span data-ttu-id="83b9b-180">位置</span><span class="sxs-lookup"><span data-stu-id="83b9b-180">Location</span></span>  
 <span data-ttu-id="83b9b-181">MSI 日志文件位于% programfiles% \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \120\Setup Bootstrap\Log \\<YYYYMMDD_HHMM>\\<Name \> .log。</span><span class="sxs-lookup"><span data-stu-id="83b9b-181">The MSI log files are located at %programfiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup Bootstrap\Log\\<YYYYMMDD_HHMM>\\<Name\>.log.</span></span>  
  
 <span data-ttu-id="83b9b-182">该文件的末尾是有关执行的摘要，其中包括成功状态或失败状态以及属性。</span><span class="sxs-lookup"><span data-stu-id="83b9b-182">At the end of the file is a summary of the execution which includes the success or failure status and properties.</span></span> <span data-ttu-id="83b9b-183">若要找到 MSI 文件中的错误，请搜索“value 3”，通常可找到的错误与此字符串接近。</span><span class="sxs-lookup"><span data-stu-id="83b9b-183">To find the error in the MSI file, search for "value 3" and usually the errors can be found close to the string.</span></span>  
  
## <a name="configurationfileini"></a><span data-ttu-id="83b9b-184">ConfigurationFile.ini</span><span class="sxs-lookup"><span data-stu-id="83b9b-184">ConfigurationFile.ini</span></span>  
  
### <a name="overview"></a><span data-ttu-id="83b9b-185">概述</span><span class="sxs-lookup"><span data-stu-id="83b9b-185">Overview</span></span>  
 <span data-ttu-id="83b9b-186">本配置文件包含安装过程中提供的输入设置。</span><span class="sxs-lookup"><span data-stu-id="83b9b-186">The configuration file contains the input settings that are provided during installation.</span></span> <span data-ttu-id="83b9b-187">该文件可用于在无需手动输入设置的情况下重新启动安装。</span><span class="sxs-lookup"><span data-stu-id="83b9b-187">It can be used to restart the installation without having to enter the settings manually.</span></span> <span data-ttu-id="83b9b-188">但是，帐户的密码、PID 和某些参数不保存在该配置文件中。</span><span class="sxs-lookup"><span data-stu-id="83b9b-188">However, passwords for the accounts, PID, and some parameters are not saved in the configuration file.</span></span> <span data-ttu-id="83b9b-189">可以将这些设置添加到该文件中，也可通过使用命令行或安装程序用户界面提供这些设置。</span><span class="sxs-lookup"><span data-stu-id="83b9b-189">The settings can be either added to the file or provided by using the command line or the Setup user interface.</span></span> <span data-ttu-id="83b9b-190">有关详细信息，请参阅[使用配置文件安装 SQL Server 2014](install-sql-server-using-a-configuration-file.md)。</span><span class="sxs-lookup"><span data-stu-id="83b9b-190">For more information, see [Install SQL Server 2014 Using a Configuration File](install-sql-server-using-a-configuration-file.md).</span></span>  
  
### <a name="location"></a><span data-ttu-id="83b9b-191">位置</span><span class="sxs-lookup"><span data-stu-id="83b9b-191">Location</span></span>  
 <span data-ttu-id="83b9b-192">它位于% programfiles% \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \120\Setup Bootstrap\Log \\<YYYYMMDD_HHMM>\\ 。</span><span class="sxs-lookup"><span data-stu-id="83b9b-192">It is located at %programfiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup Bootstrap\Log\\<YYYYMMDD_HHMM>\\.</span></span>  
  
## <a name="systemconfigurationcheck_reporthtm"></a><span data-ttu-id="83b9b-193">SystemConfigurationCheck_Report.htm</span><span class="sxs-lookup"><span data-stu-id="83b9b-193">SystemConfigurationCheck_Report.htm</span></span>  
  
### <a name="overview"></a><span data-ttu-id="83b9b-194">概述</span><span class="sxs-lookup"><span data-stu-id="83b9b-194">Overview</span></span>  
 <span data-ttu-id="83b9b-195">系统配置检查报表包含有关每个执行规则的简短说明，以及执行状态。</span><span class="sxs-lookup"><span data-stu-id="83b9b-195">The system configuration check report contains a short description for each executed rule, and the execution status.</span></span>  
  
### <a name="location"></a><span data-ttu-id="83b9b-196">位置</span><span class="sxs-lookup"><span data-stu-id="83b9b-196">Location</span></span>  
 <span data-ttu-id="83b9b-197">它位于% programfiles% \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \120\Setup Bootstrap\Log \\<YYYYMMDD_HHMM>\\ 。</span><span class="sxs-lookup"><span data-stu-id="83b9b-197">It is located at %programfiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup Bootstrap\Log\\<YYYYMMDD_HHMM>\\.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83b9b-198">另请参阅</span><span class="sxs-lookup"><span data-stu-id="83b9b-198">See Also</span></span>  
 <span data-ttu-id="83b9b-199">[安装操作指南主题](../../sql-server/install/installation-how-to-topics.md) </span><span class="sxs-lookup"><span data-stu-id="83b9b-199">[Installation How-to Topics](../../sql-server/install/installation-how-to-topics.md) </span></span>  
 [<span data-ttu-id="83b9b-200">安装 SQL Server 2014</span><span class="sxs-lookup"><span data-stu-id="83b9b-200">Install SQL Server 2014</span></span>](install-sql-server.md)  
  
  
