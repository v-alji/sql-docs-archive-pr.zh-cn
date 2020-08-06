---
title: dtexec 实用工具 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 7b6867fa-1039-49b3-90fb-85b84678a612
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 45820aa673f31ae9cea7d1f2f4e8b61d63b8670c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690740"
---
# <a name="dtexec-utility"></a><span data-ttu-id="e2dc8-102">dtexec 实用工具</span><span class="sxs-lookup"><span data-stu-id="e2dc8-102">dtexec Utility</span></span>
  <span data-ttu-id="e2dc8-103">`dtexec`命令提示实用工具用于配置和执行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-103">The `dtexec` command prompt utility is used to configure and execute [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages.</span></span> <span data-ttu-id="e2dc8-104">使用 `dtexec` 实用工具，可以访问所有包配置和执行功能，如参数、连接、属性、变量、日志和进度指示器等。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-104">The `dtexec` utility provides access to all the package configuration and execution features, such as parameters, connections, properties, variables, logging, and progress indicators.</span></span> <span data-ttu-id="e2dc8-105">`dtexec`利用此实用工具，你可以从以下源加载包： [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 服务器、.ispac 项目文件、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库、 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 包存储区和文件系统。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-105">The `dtexec` utility lets you load packages from these sources: the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server, an .ispac project file, a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database, the [!INCLUDE[ssIS](../../includes/ssis-md.md)] Package Store, and the file system.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e2dc8-106">当使用 [!INCLUDE[ssISversion11](../../includes/ssisversion11-md.md)] 附带的 `dtexec` 实用工具版本运行 [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] 或 [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)] 包时，[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 会临时将该包升级到 [!INCLUDE[ssISversion11](../../includes/ssisversion11-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-106">When you use the version of the `dtexec` utility that comes with [!INCLUDE[ssISversion11](../../includes/ssisversion11-md.md)] to run a [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] or a [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)] package, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] temporarily upgrades the package to [!INCLUDE[ssISversion11](../../includes/ssisversion11-md.md)].</span></span> <span data-ttu-id="e2dc8-107">不过，您不能使用 `dtexec` 实用工具保存这些升级的更改。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-107">However, you cannot use the `dtexec` utility to save these upgraded changes.</span></span> <span data-ttu-id="e2dc8-108">有关如何将包永久升级到的详细信息 [!INCLUDE[ssISversion11](../../includes/ssisversion11-md.md)] ，请参阅[upgrade Integration Services](../install-windows/upgrade-integration-services-packages.md)package。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-108">For more information about how to permanently upgrade a package to [!INCLUDE[ssISversion11](../../includes/ssisversion11-md.md)], see [Upgrade Integration Services Packages](../install-windows/upgrade-integration-services-packages.md).</span></span>  
  
 <span data-ttu-id="e2dc8-109">本主题包含下列部分：</span><span class="sxs-lookup"><span data-stu-id="e2dc8-109">This topic includes the following sections:</span></span>  
  
-   [<span data-ttu-id="e2dc8-110">Integration Services 服务器和项目文件</span><span class="sxs-lookup"><span data-stu-id="e2dc8-110">Integration Services Server and Project File</span></span>](#server)  
  
-   [<span data-ttu-id="e2dc8-111">64 位计算机上的安装注意事项</span><span class="sxs-lookup"><span data-stu-id="e2dc8-111">Installation Considerations on 64-bit Computers</span></span>](#bit)  
  
-   [<span data-ttu-id="e2dc8-112">有关使用并行安装的计算机的注意事项</span><span class="sxs-lookup"><span data-stu-id="e2dc8-112">Considerations on Computers with Side-by-Side Installations</span></span>](#side)  
  
-   [<span data-ttu-id="e2dc8-113">执行的阶段</span><span class="sxs-lookup"><span data-stu-id="e2dc8-113">Phases of Execution</span></span>](#phases)  
  
-   [<span data-ttu-id="e2dc8-114">返回的退出代码</span><span class="sxs-lookup"><span data-stu-id="e2dc8-114">Exit Codes Returned</span></span>](#exit)  
  
-   [<span data-ttu-id="e2dc8-115">语法规则</span><span class="sxs-lookup"><span data-stu-id="e2dc8-115">Syntax Rules</span></span>](#syntaxRules)  
  
-   [<span data-ttu-id="e2dc8-116">从 xp_cmdshell 中使用 dtexec</span><span class="sxs-lookup"><span data-stu-id="e2dc8-116">Using dtexec from the xp_cmdshell</span></span>](#cmdshell)  
  
-   [<span data-ttu-id="e2dc8-117">语法</span><span class="sxs-lookup"><span data-stu-id="e2dc8-117">Syntax</span></span>](#syntax)  
  
-   [<span data-ttu-id="e2dc8-118">参数</span><span class="sxs-lookup"><span data-stu-id="e2dc8-118">Parameters</span></span>](#parameter)  
  
-   [<span data-ttu-id="e2dc8-119">注释</span><span class="sxs-lookup"><span data-stu-id="e2dc8-119">Remarks</span></span>](#remark)  
  
-   [<span data-ttu-id="e2dc8-120">示例</span><span class="sxs-lookup"><span data-stu-id="e2dc8-120">Examples</span></span>](#example)  
  
##  <a name="integration-services-server-and-project-file"></a><a name="server"></a> <span data-ttu-id="e2dc8-121">Integration Services 服务器和项目文件</span><span class="sxs-lookup"><span data-stu-id="e2dc8-121">Integration Services Server and Project File</span></span>  
 <span data-ttu-id="e2dc8-122">当你使用在 `dtexec` 服务器上运行包 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 时，将 `dtexec` 调用[目录。 create_execution &#40;ssisdb 数据库&#41;](/sql/integration-services/system-stored-procedures/catalog-create-execution-ssisdb-database)、 [catalog. set_execution_parameter_value &#40;ssisdb 数据库&#41;](/sql/integration-services/system-stored-procedures/catalog-set-execution-parameter-value-ssisdb-database)和[目录。 start_execution &#40;ssisdb 数据库&#41;](/sql/integration-services/system-stored-procedures/catalog-start-execution-ssisdb-database)存储过程来创建执行、设置参数值并开始执行。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-122">When you use `dtexec` to run packages on the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server, `dtexec` calls the [catalog.create_execution &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-create-execution-ssisdb-database), [catalog.set_execution_parameter_value &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-set-execution-parameter-value-ssisdb-database) and [catalog.start_execution &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-start-execution-ssisdb-database) stored procedures to create an execution, set parameter values and start the execution.</span></span> <span data-ttu-id="e2dc8-123">可以在服务器的相关视图中或使用 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]中提供的标准报告来查看所有执行日志。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-123">All execution logs can be seen from the server in the related views or by using standard reports available in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="e2dc8-124">有关报表的详细信息，请参阅 [Integration Services 服务器的报表](../reports-for-the-integration-services-server.md)。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-124">For more information about the reports, see [Reports for the Integration Services Server](../reports-for-the-integration-services-server.md).</span></span>  
  
 <span data-ttu-id="e2dc8-125">以下是在 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 服务器上执行包的一个示例。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-125">The following is an example of executing a package on the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server.</span></span>  
  
```  
DTExec /ISSERVER "\SSISDB\folderB\Integration Services Project17\Package.dtsx" /SERVER "." /Envreference 2 /Par "$Project::ProjectParameter(Int32)";1 /Par "Parameter(Int32)";21 /Par "CM.sqlcldb2.SSIS_repro.InitialCatalog";ssisdb /Par "$ServerOption::SYNCHRONIZED(Boolean)";True  
```  
  
 <span data-ttu-id="e2dc8-126">使用 `dtexec` 从 .ispac 项目文件运行包时，相关选项 /Proj[ect] 和 /Pack[age] 用于指定项目路径和包流名称。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-126">When you use `dtexec` to run a package from the .ispac project file, the related options are: /Proj[ect] and /Pack[age] that are used to specify the project path and package stream name.</span></span> <span data-ttu-id="e2dc8-127">通过从 **运行** “Integration Services 项目转换向导” [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]将项目转换为项目部署模型时，该向导生成一个 .ispac 项目文件。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-127">When you convert a project to the project deployment model by running the **Integration Services Project Conversion Wizard** from [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], the wizard generates an .ispac projec file.</span></span> <span data-ttu-id="e2dc8-128">有关详细信息，请参阅 [Deploy Projects to Integration Services Server](../deploy-projects-to-integration-services-server.md)。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-128">For more information, see [Deploy Projects to Integration Services Server](../deploy-projects-to-integration-services-server.md).</span></span>  
  
 <span data-ttu-id="e2dc8-129">你可以使用 `dtexec` 与第三方计划工具来计划部署到服务器的包 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-129">You can use `dtexec` with third-party scheduling tools to schedule packages that are deployed to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server.</span></span>  
  
##  <a name="installation-considerations-on-64-bit-computers"></a><a name="bit"></a> <span data-ttu-id="e2dc8-130">64 位计算机上的安装注意事项</span><span class="sxs-lookup"><span data-stu-id="e2dc8-130">Installation Considerations on 64-bit Computers</span></span>  
 <span data-ttu-id="e2dc8-131">在 64 位计算机上，[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 将安装 64 位版本的 `dtexec` 实用工具 (dtexec.exe)。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-131">On a 64-bit computer, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] installs a 64-bit version of the `dtexec` utility (dtexec.exe).</span></span> <span data-ttu-id="e2dc8-132">如果需要以 32 位模式运行某些包，则必须安装 32 位版本的 `dtexec` 实用工具。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-132">If you have to run certain packages in 32-bit mode, you will have to install the 32-bit version of the `dtexec` utility.</span></span> <span data-ttu-id="e2dc8-133">若要安装 32 位版本的 `dtexec` 实用工具，必须在安装过程中选择“客户端工具”或 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-133">To install the 32-bit version of the `dtexec` utility, you must select either Client Tools or [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] during setup.</span></span>  
  
 <span data-ttu-id="e2dc8-134">默认情况下，同时安装了 64 位和 32 位版本的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 命令提示实用工具的 64 位计算机将在命令提示符处运行 32 位版本。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-134">By default, a 64-bit computer that has both the 64-bit and 32-bit versions of an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] command prompt utility installed will run the 32-bit version at the command prompt.</span></span> <span data-ttu-id="e2dc8-135">运行 32 位版本的原因是：在 PATH 环境变量中，32 位版本的目录路径显示在 64 位版本的目录路径之前。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-135">The 32-bit version runs because the directory path for the 32-bit version appears in the PATH environment variable before the directory path for the 64-bit version.</span></span> <span data-ttu-id="e2dc8-136">（通常，32 位目录路径是 \<drive>:\Program Files(x86)\Microsoft SQL Server\110\DTS\Binn，而 64 位目录路径是 \<drive>:\Program Files\Microsoft SQL Server\110\DTS\Binn。 ）</span><span class="sxs-lookup"><span data-stu-id="e2dc8-136">(Typically, the 32-bit directory path is *\<drive>*:\Program Files(x86)\Microsoft SQL Server\110\DTS\Binn, while the 64-bit directory path is *\<drive>*:\Program Files\Microsoft SQL Server\110\DTS\Binn.)</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e2dc8-137">如果使用 SQL Server 代理来运行此实用工具，则 SQL Server 代理会自动使用 64 位版本的实用工具。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-137">If you use SQL Server Agent to run the utility, SQL Server Agent automatically uses the 64-bit version of the utility.</span></span> <span data-ttu-id="e2dc8-138">SQL Server 代理使用注册表（而非 PATH 环境变量）来找到此实用工具的正确可执行文件。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-138">SQL Server Agent uses the registry, not the PATH environment variable, to locate the correct executable for the utility.</span></span>  
  
 <span data-ttu-id="e2dc8-139">若要确保在命令提示符处运行 64 位版本的实用工具，可以执行以下操作之一：</span><span class="sxs-lookup"><span data-stu-id="e2dc8-139">To ensure that you run the 64-bit version of the utility at the command prompt, you can take one of the following actions:</span></span>  
  
-   <span data-ttu-id="e2dc8-140">打开“命令提示符”窗口，更改到包含 64 位版本的实用工具的目录 (\<drive>:\Program Files\Microsoft SQL Server\110\DTS\Binn)，然后从该位置运行此实用工具。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-140">Open a Command Prompt window, change to the directory that contains the 64-bit version of the utility (*\<drive>*:\Program Files\Microsoft SQL Server\110\DTS\Binn), and then run the utility from that location.</span></span>  
  
-   <span data-ttu-id="e2dc8-141">在命令提示符处，输入 64 位版本的实用工具的完整路径 (\<drive>:\Program Files\Microsoft SQL Server\110\DTS\Binn) 来运行此实用工具。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-141">At the command prompt, run the utility by entering the full path (*\<drive>*:\Program Files\Microsoft SQL Server\110\DTS\Binn) to the 64-bit version of the utility.</span></span>  
  
-   <span data-ttu-id="e2dc8-142">将 64 位路径 (\<drive>:\Program Files\Microsoft SQL Server\110\DTS\Binn) 置于 32 位路径(\<drive>:\Program Files(x86)\Microsoft SQL Server\110\DTS\Binn) 之前，可永久更改 PATH 环境变量中路径的顺序 。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-142">Permanently change the order of the paths in the PATH environment variable by placing the 64-bit path (*\<drive>*:\Program Files\Microsoft SQL Server\110\DTS\Binn) before the 32-bit path (*\<drive>*:\ Program Files(x86)\Microsoft SQL Server\110\DTS\Binn) in the variable.</span></span>  
  
##  <a name="considerations-on-computers-with-side-by-side-installations"></a><a name="side"></a> <span data-ttu-id="e2dc8-143">有关使用并行安装的计算机的注意事项</span><span class="sxs-lookup"><span data-stu-id="e2dc8-143">Considerations on Computers with Side-by-Side Installations</span></span>  
 <span data-ttu-id="e2dc8-144">当在已安装 [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] 或 [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] 的计算机上安装 [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)] 时，安装多个版本的 `dtexec` 实用工具。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-144">When [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] is installed on a machine that has [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] or [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)] installed, multiple versions of the `dtexec` utility are installed.</span></span>  
  
 <span data-ttu-id="e2dc8-145">若要确保运行正确版本的实用工具，请在命令提示符处输入完整路径 (\<drive>:\Program Files\Microsoft SQL Server\\<version\>\DTS\Binn) 来运行此实用工具。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-145">To ensure that you run the correct version of the utility, at the command prompt run the utility by entering the full path (*\<drive>*:\Program Files\Microsoft SQL Server\\<version\>\DTS\Binn).</span></span>  
  
##  <a name="phases-of-execution"></a><a name="phases"></a> <span data-ttu-id="e2dc8-146">执行的阶段</span><span class="sxs-lookup"><span data-stu-id="e2dc8-146">Phases of Execution</span></span>  
 <span data-ttu-id="e2dc8-147">该实用工具的执行过程经历四个阶段。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-147">The utility has four phases that it proceeds through as it executes.</span></span> <span data-ttu-id="e2dc8-148">这些阶段如下所列：</span><span class="sxs-lookup"><span data-stu-id="e2dc8-148">The phases are as follows:</span></span>  
  
1.  <span data-ttu-id="e2dc8-149">命令溯源阶段：命令提示符读取选项列表和已指定的参数。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-149">Command sourcing phase: The command prompt reads the list of options and arguments that have been specified.</span></span> <span data-ttu-id="e2dc8-150">如果遇到 **/?**</span><span class="sxs-lookup"><span data-stu-id="e2dc8-150">All subsequent phases are skipped if a **/?**</span></span> <span data-ttu-id="e2dc8-151">或 **/HELP** 选项，则会跳过所有后续阶段。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-151">or **/HELP** option is encountered.</span></span>  
  
2.  <span data-ttu-id="e2dc8-152">包加载阶段： `/SQL` 加载、 **/FILE**或选项指定的包 `/DTS` 。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-152">Package load phase: The package specified by the `/SQL`, **/FILE**, or `/DTS` option is loaded.</span></span>  
  
3.  <span data-ttu-id="e2dc8-153">配置阶段：按以下顺序处理各个选项：</span><span class="sxs-lookup"><span data-stu-id="e2dc8-153">Configuration phase: Options are processed in this order:</span></span>  
  
    -   <span data-ttu-id="e2dc8-154">设置包标志、变量和属性的选项。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-154">Options that set package flags, variables, and properties.</span></span>  
  
    -   <span data-ttu-id="e2dc8-155">验证包版本和内部版本的选项。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-155">Options that verify the package version and build.</span></span>  
  
    -   <span data-ttu-id="e2dc8-156">配置实用工具运行时行为（如报告）的选项。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-156">Options that configure the run-time behavior of the utility, such as reporting.</span></span>  
  
4.  <span data-ttu-id="e2dc8-157">验证和执行阶段：运行包，如果指定了 /VALIDATE 选项，则验证但不运行包  。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-157">Validation and execution phase: The package is run, or validated without running if the **/VALIDATE** option was specified.</span></span>  
  
##  <a name="exit-codes-returned"></a><a name="exit"></a> <span data-ttu-id="e2dc8-158">返回的退出代码</span><span class="sxs-lookup"><span data-stu-id="e2dc8-158">Exit Codes Returned</span></span>  
 <span data-ttu-id="e2dc8-159">**dtexec 实用工具返回的退出代码**</span><span class="sxs-lookup"><span data-stu-id="e2dc8-159">**Exit codes returned from dtexec utility**</span></span>  
  
 <span data-ttu-id="e2dc8-160">运行包时，`dtexec` 可能会返回退出代码。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-160">When a package runs, `dtexec` can return an exit code.</span></span> <span data-ttu-id="e2dc8-161">使用该退出代码填充 ERRORLEVEL 变量，然后可以在批处理文件的条件语句或分支逻辑中测试该变量的值。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-161">The exit code is used to populate the ERRORLEVEL variable, the value of which can then be tested in conditional statements or branching logic within a batch file.</span></span> <span data-ttu-id="e2dc8-162">下表列出了 `dtexec` 实用工具退出时可以设置的值。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-162">The following table lists the values that the `dtexec` utility can set when exiting.</span></span>  
  
|<span data-ttu-id="e2dc8-163">值</span><span class="sxs-lookup"><span data-stu-id="e2dc8-163">Value</span></span>|<span data-ttu-id="e2dc8-164">说明</span><span class="sxs-lookup"><span data-stu-id="e2dc8-164">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e2dc8-165">0</span><span class="sxs-lookup"><span data-stu-id="e2dc8-165">0</span></span>|<span data-ttu-id="e2dc8-166">已成功执行包。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-166">The package executed successfully.</span></span>|  
|<span data-ttu-id="e2dc8-167">1</span><span class="sxs-lookup"><span data-stu-id="e2dc8-167">1</span></span>|<span data-ttu-id="e2dc8-168">包失败。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-168">The package failed.</span></span>|  
|<span data-ttu-id="e2dc8-169">3</span><span class="sxs-lookup"><span data-stu-id="e2dc8-169">3</span></span>|<span data-ttu-id="e2dc8-170">用户取消了包。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-170">The package was canceled by the user.</span></span>|  
|<span data-ttu-id="e2dc8-171">4</span><span class="sxs-lookup"><span data-stu-id="e2dc8-171">4</span></span>|<span data-ttu-id="e2dc8-172">实用工具找不到请求的包。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-172">The utility was unable to locate the requested package.</span></span> <span data-ttu-id="e2dc8-173">无法找到包。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-173">The package could not be found.</span></span>|  
|<span data-ttu-id="e2dc8-174">5</span><span class="sxs-lookup"><span data-stu-id="e2dc8-174">5</span></span>|<span data-ttu-id="e2dc8-175">实用工具无法加载请求的包。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-175">The utility was unable to load the requested package.</span></span> <span data-ttu-id="e2dc8-176">无法加载包。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-176">The package could not be loaded.</span></span>|  
|<span data-ttu-id="e2dc8-177">6</span><span class="sxs-lookup"><span data-stu-id="e2dc8-177">6</span></span>|<span data-ttu-id="e2dc8-178">实用工具的命令行中有内部语法错误或语义错误。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-178">The utility encountered an internal error of syntactic or semantic errors in the command line.</span></span>|  
  
##  <a name="syntax-rules"></a><a name="syntaxRules"></a> <span data-ttu-id="e2dc8-179">语法规则</span><span class="sxs-lookup"><span data-stu-id="e2dc8-179">Syntax Rules</span></span>  
 <span data-ttu-id="e2dc8-180">**实用工具语法规则**</span><span class="sxs-lookup"><span data-stu-id="e2dc8-180">**Utility syntax rules**</span></span>  
  
 <span data-ttu-id="e2dc8-181">所有选项必须以斜杠 (/) 或减号 (-) 开头。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-181">All options must start with a slash (/) or a minus sign (-).</span></span> <span data-ttu-id="e2dc8-182">此处显示的选项以斜杠 (/) 开始，但可用减号 (-) 替换。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-182">The options that are shown here start with a slash (/), but the minus sign (-) can be substituted.</span></span>  
  
 <span data-ttu-id="e2dc8-183">如果参数包含空格，则必须用引号将该参数引起来。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-183">An argument must be enclosed in quotation marks if it contains a space.</span></span> <span data-ttu-id="e2dc8-184">如果没有使用引号将参数引起来，则该参数不能包含空格。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-184">If the argument is not enclosed in quotation marks, the argument cannot contain white space.</span></span>  
  
 <span data-ttu-id="e2dc8-185">用引号引起来的字符串中的双引号表示转义单引号。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-185">Doubled quotation marks within quoted strings represent escaped single quotation marks.</span></span>  
  
 <span data-ttu-id="e2dc8-186">除密码外，其他选项和参数都不区分大小写。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-186">Options and arguments are not case-sensitive, except for passwords.</span></span>  
  
##  <a name="using-dtexec-from-the-xp_cmdshell"></a><a name="cmdshell"></a> <span data-ttu-id="e2dc8-187">从 xp_cmdshell 中使用 dtexec</span><span class="sxs-lookup"><span data-stu-id="e2dc8-187">Using dtexec from the xp_cmdshell</span></span>  
 <span data-ttu-id="e2dc8-188">**从 xp_cmdshell 中使用 dtexec**</span><span class="sxs-lookup"><span data-stu-id="e2dc8-188">**Using dtexec from the xp_cmdshell**</span></span>  
  
 <span data-ttu-id="e2dc8-189">可以从 **xp_cmdshell** 提示符处运行 dtexec。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-189">You can run dtexec from the **xp_cmdshell** prompt.</span></span> <span data-ttu-id="e2dc8-190">以下示例显示如何运行名为 UpsertData.dtsx 的包并忽略返回代码：</span><span class="sxs-lookup"><span data-stu-id="e2dc8-190">The following example shows how to run a package called UpsertData.dtsx and ignore the return code:</span></span>  
  
```  
EXEC xp_cmdshell 'dtexec /f "C:\UpsertData.dtsx"'  
```  
  
 <span data-ttu-id="e2dc8-191">以下示例显示如何运行相同的包并捕获返回代码：</span><span class="sxs-lookup"><span data-stu-id="e2dc8-191">The following example shows how to run the same package and capture the return code:</span></span>  
  
```  
DECLARE @returncode int  
EXEC @returncode = xp_cmdshell 'dtexec /f "C:\UpsertData.dtsx"'  
```  
  
> [!IMPORTANT]  
>  <span data-ttu-id="e2dc8-192">在 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中，新安装中将默认禁用 **xp_cmdshell** 选项。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-192">In [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the **xp_cmdshell** option is disabled by default on new installations.</span></span> <span data-ttu-id="e2dc8-193">运行 **sp_configure** 系统存储过程可以启用此选项。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-193">The option can be enabled by running the **sp_configure** system stored procedure.</span></span> <span data-ttu-id="e2dc8-194">有关详细信息，请参阅 [xp_cmdshell 服务器配置选项](../../database-engine/configure-windows/xp-cmdshell-server-configuration-option.md)。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-194">For more information, see [xp_cmdshell Server Configuration Option](../../database-engine/configure-windows/xp-cmdshell-server-configuration-option.md).</span></span>  
  
##  <a name="syntax"></a><a name="syntax"></a> <span data-ttu-id="e2dc8-195">语法</span><span class="sxs-lookup"><span data-stu-id="e2dc8-195">Syntax</span></span>  
  
```  
dtexec /option [value] [/option [value]]...  
```  
  
##  <a name="parameters"></a><a name="parameter"></a> <span data-ttu-id="e2dc8-196">Parameters</span><span class="sxs-lookup"><span data-stu-id="e2dc8-196">Parameters</span></span>  
  
-   <span data-ttu-id="e2dc8-197">**/?**</span><span class="sxs-lookup"><span data-stu-id="e2dc8-197">**/?**</span></span> <span data-ttu-id="e2dc8-198">[*option_name*]：可选。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-198">[*option_name*]: Optional.</span></span> <span data-ttu-id="e2dc8-199">显示命令提示符选项，或显示指定的 *option_name* 的帮助，然后关闭实用工具。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-199">Displays the command prompt options, or displays help for the specified *option_name* and then closes the utility.</span></span>  
  
     <span data-ttu-id="e2dc8-200">如果指定*option_name*参数，则将 `dtexec` 启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 联机丛书并显示 dtexec 实用工具主题。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-200">If you specify an *option_name* argument, `dtexec` starts [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online and displays the dtexec Utility topic.</span></span>  
  
-   <span data-ttu-id="e2dc8-201">**/Ca [llerInfo]**：</span><span class="sxs-lookup"><span data-stu-id="e2dc8-201">**/Ca[llerInfo]**:</span></span>   
                  <span data-ttu-id="e2dc8-202">可选。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-202">Optional.</span></span> <span data-ttu-id="e2dc8-203">指定有关包执行的其他信息。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-203">Specifies additional information for a package execution.</span></span> <span data-ttu-id="e2dc8-204">使用 SQL Server 代理运行包时，代理设置此参数以指示包执行由 SQL Server 代理调用。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-204">When you run a package using SQL Server Agent, agent sets this argument to indicate that the package execution is invoked by SQL Server Agent.</span></span> <span data-ttu-id="e2dc8-205">从命令行运行 `dtexec` 实用工具时，忽略此参数。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-205">This parameter is ignored when the `dtexec` utility is run from the command line.</span></span>  
  
-   <span data-ttu-id="e2dc8-206">**/CheckF[ile]** _filespec_：</span><span class="sxs-lookup"><span data-stu-id="e2dc8-206">**/CheckF[ile]** _filespec_:</span></span>   
                  <span data-ttu-id="e2dc8-207">可选。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-207">Optional.</span></span> <span data-ttu-id="e2dc8-208">将 `CheckpointFileName` 包的属性设置为*filespec*中的路径和文件为。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-208">Sets the `CheckpointFileName` property on the package to the path and file spemandcified in *filespec*.</span></span> <span data-ttu-id="e2dc8-209">重新启动包时将使用此文件。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-209">This file is used when the package restarts.</span></span> <span data-ttu-id="e2dc8-210">如果指定了该选项并且未提供文件名值，则包的 `CheckpointFileName` 将被设置为空字符串。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-210">If this option is specified and no value is supplied for the file name, the `CheckpointFileName` for the package is set to an empty string.</span></span> <span data-ttu-id="e2dc8-211">如果不指定该选项，则保留包中的值。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-211">If this option is not specified, the values in the package are retained.</span></span>  
  
-   <span data-ttu-id="e2dc8-212">**/CheckP [ointing]** _{on\off}_：</span><span class="sxs-lookup"><span data-stu-id="e2dc8-212">**/CheckP[ointing]** _{on\off}_:</span></span>   
                  <span data-ttu-id="e2dc8-213">可选。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-213">Optional.</span></span> <span data-ttu-id="e2dc8-214">设置一个值，用于确定包执行期间包是否使用检查点。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-214">Sets a value that determines whether the package will use checkpoints during package execution.</span></span> <span data-ttu-id="e2dc8-215">值 **on** 指定要重新运行失败的包。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-215">The value **on** specifies that a failed package is to be rerun.</span></span> <span data-ttu-id="e2dc8-216">重新运行失败的包时，运行时引擎将使用检查点文件，以便从失败点重新启动包。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-216">When the failed package is rerun, the run-time engine uses the checkpoint file to restart the package from the point of failure.</span></span>  
  
     <span data-ttu-id="e2dc8-217">如果声明该选项时未提供值，则默认值为“on”。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-217">The default value is on if the option is declared without a value.</span></span> <span data-ttu-id="e2dc8-218">如果值设置为“on”，但找不到检查点文件，则包执行将失败。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-218">Package execution will fail if the value is set to on and the checkpoint file cannot be found.</span></span> <span data-ttu-id="e2dc8-219">如果不指定该选项，则保留包中设置的值。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-219">If this option is not specified, the value set in the package is retained.</span></span> <span data-ttu-id="e2dc8-220">有关详细信息，请参阅 [通过使用检查点重新启动包](restart-packages-by-using-checkpoints.md)。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-220">For more information, see [Restart Packages by Using Checkpoints](restart-packages-by-using-checkpoints.md).</span></span>  
  
     <span data-ttu-id="e2dc8-221">Dtexec 的 **/checkpointing on on**选项等效于将 `SaveCheckpoints` 包的属性设置为 True，并将属性设置为 "始终" `CheckpointUsage` 。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-221">The **/CheckPointing on** option of dtexec is equivalent to setting the `SaveCheckpoints` property of the package to True, and the `CheckpointUsage` property to Always.</span></span>  
  
-   <span data-ttu-id="e2dc8-222">**/Com[mandFile]** _filespec_：</span><span class="sxs-lookup"><span data-stu-id="e2dc8-222">**/Com[mandFile]** _filespec_:</span></span>   
                  <span data-ttu-id="e2dc8-223">（可选）。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-223">(Optional).</span></span> <span data-ttu-id="e2dc8-224">指定要使用 `dtexec` 运行的命令选项。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-224">Specifies the command options that run with `dtexec`.</span></span> <span data-ttu-id="e2dc8-225">打开 *filespec* 中指定的文件，并读取该文件中的选项，直到在文件中找到 EOF。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-225">The file specified in *filespec* is opened and options from the file are read until EOF is found in the file.</span></span> <span data-ttu-id="e2dc8-226">*filespec* 是一个文本文件。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-226">*filespec* is a text file.</span></span> <span data-ttu-id="e2dc8-227">*filespec* 参数指定与包执行关联的命令文件的文件名和路径。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-227">The *filespec* argument specifies the file name and path of the command file to associate with the execution of the package.</span></span>  
  
-   <span data-ttu-id="e2dc8-228">**/Conf [igFile]** _filespec_： Optional。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-228">**/Conf[igFile]** _filespec_: Optional.</span></span> <span data-ttu-id="e2dc8-229">指定要从中提取值的配置文件。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-229">Specifies a configuration file to extract values from.</span></span> <span data-ttu-id="e2dc8-230">使用该选项，可以设置一个与设计包时指定的配置不同的运行时配置。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-230">Using this option, you can set a run-time configuration that differs from the configuration that was specified at design time for the package.</span></span> <span data-ttu-id="e2dc8-231">可以将不同的配置设置存储在 XML 配置文件中，然后在执行包之前使用 **/ConfigFile** 选项加载这些设置。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-231">You can store different configuration settings in an XML configuration file and then load the settings before package execution by using the **/ConfigFile** option.</span></span>  
  
     <span data-ttu-id="e2dc8-232">可以使用 **/ConfigFile** 选项在运行时加载在设计时未指定的其他配置。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-232">You can use the **/ConfigFile** option to load additional configurations at run time that you did not specify at design time.</span></span> <span data-ttu-id="e2dc8-233">不过，不能使用 **/ConfigFile** 选项来替换在设计时也指定了的配置值。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-233">However, you cannot use the **/ConfigFile** option to replace configured values that you also specified at design time.</span></span> <span data-ttu-id="e2dc8-234">若要了解如何应用包配置，请参阅 [Package Configurations](../package-configurations.md)。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-234">To understand how package configurations are applied, see [Package Configurations](../package-configurations.md).</span></span>  
  
-   <span data-ttu-id="e2dc8-235">**/Conn[ection]** _id_or_name;connection_string [[;id_or_name;connection_string]...]_：</span><span class="sxs-lookup"><span data-stu-id="e2dc8-235">**/Conn[ection]** _id_or_name;connection_string [[;id_or_name;connection_string]...]_:</span></span>   
                  <span data-ttu-id="e2dc8-236">可选。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-236">Optional.</span></span> <span data-ttu-id="e2dc8-237">指定带有指定名称或 GUID 的连接管理器位于包中，并指定了连接字符串。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-237">Specifies that the connection manager with the specified name or GUID is located in the package, and specifies a connection string.</span></span>  
  
     <span data-ttu-id="e2dc8-238">该选项要求同时指定两个参数：必须在 *id_or_name* 参数中提供连接管理器名称或 GUID，并且在 *connection_string* 参数中指定有效的连接字符串。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-238">This option requires that both parameters be specified: the connection manager name or GUID must be provided in the *id_or_name* argument, and a valid connection string must be specified in the *connection_string* argument.</span></span> <span data-ttu-id="e2dc8-239">有关详细信息，请参阅 [Integration Services (SSIS) 连接](../connection-manager/integration-services-ssis-connections.md)。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-239">For more information, see [Integration Services &#40;SSIS&#41; Connections](../connection-manager/integration-services-ssis-connections.md).</span></span>  
  
     <span data-ttu-id="e2dc8-240">在运行时，可以使用 **/Connection** 选项从在设计时指定的位置之外的某个位置加载包配置。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-240">At run time, you can use the **/Connection** option to load package configurations from a location other than the location that you specified at design time.</span></span> <span data-ttu-id="e2dc8-241">这些配置的值随后将替换最初指定的值。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-241">The values of these configurations then replace the values that were originally specified.</span></span> <span data-ttu-id="e2dc8-242">不过，可以将 **/Connection** 选项仅用于使用连接管理器的配置，如 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-242">However you can use the **/Connection** option only for configurations, such as [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] configurations, that use a connection manager.</span></span> <span data-ttu-id="e2dc8-243">若要了解如何应用包配置，请参阅[包配置](../package-configurations.md)和[SQL Server 2014 中 Integration Services 功能的行为更改](../behavior-changes-to-integration-services-features-in-sql-server-2014.md)。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-243">To understand how package configurations are applied, see [Package Configurations](../package-configurations.md) and [Behavior Changes to Integration Services Features in SQL Server 2014](../behavior-changes-to-integration-services-features-in-sql-server-2014.md).</span></span>  
  
-   <span data-ttu-id="e2dc8-244">**/Cons [oleLog]** [[*displayoptions*]; [*list_options*;*src_name_or_guid*]...]：可选。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-244">**/Cons[oleLog]** [[*displayoptions*];[*list_options*;*src_name_or_guid*]...]: Optional.</span></span> <span data-ttu-id="e2dc8-245">在包执行过程中，在控制台显示指定的日志项。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-245">Displays specified log entries to the console during package execution.</span></span> <span data-ttu-id="e2dc8-246">如果省略该选项，则不会在控制台中显示日志项。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-246">If this option is omitted, no log entries are shown in the console.</span></span> <span data-ttu-id="e2dc8-247">如果指定该选项时不带限制显示的参数，则会显示所有日志项。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-247">If the option is specified without parameters that limit the display, every log entry will display.</span></span> <span data-ttu-id="e2dc8-248">若要限制控制台显示的日志项，可以使用 *displayoptions* 参数指定要显示的列，并使用 *list_options* 参数限制日志项类型。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-248">To limit the entries that are displayed to the console, you can specify the columns to show by using the *displayoptions* parameter, and limit the log entry types by using the *list_options* parameter.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e2dc8-249">使用参数在服务器上运行包时 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] `/ISSERVER` ，控制台输出受限，大多数 **/Cons [oleLog]** 选项均不适用。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-249">When you run a package on the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server by using the `/ISSERVER` parameter, console output is limited and most of the **/Cons[oleLog]** options are not applicable.</span></span> <span data-ttu-id="e2dc8-250">可以在服务器的相关视图中或使用 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]中提供的标准报告来查看所有执行日志。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-250">All execution logs can be seen from the server in the related views or by using standard reports available in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="e2dc8-251">有关报表的详细信息，请参阅 [Integration Services 服务器的报表](../reports-for-the-integration-services-server.md)。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-251">For more information about the reports, see [Reports for the Integration Services Server](../reports-for-the-integration-services-server.md).</span></span>  
  
     <span data-ttu-id="e2dc8-252">*displayoptions* 值包括：</span><span class="sxs-lookup"><span data-stu-id="e2dc8-252">The *displayoptions* values are as follows:</span></span>  
  
    -   <span data-ttu-id="e2dc8-253">N（名称）</span><span class="sxs-lookup"><span data-stu-id="e2dc8-253">N (Name)</span></span>  
  
    -   <span data-ttu-id="e2dc8-254">C（计算机）</span><span class="sxs-lookup"><span data-stu-id="e2dc8-254">C (Computer)</span></span>  
  
    -   <span data-ttu-id="e2dc8-255">O（操作员）</span><span class="sxs-lookup"><span data-stu-id="e2dc8-255">O (Operator)</span></span>  
  
    -   <span data-ttu-id="e2dc8-256">S（源名称）</span><span class="sxs-lookup"><span data-stu-id="e2dc8-256">S (Source Name)</span></span>  
  
    -   <span data-ttu-id="e2dc8-257">G（源 GUID）</span><span class="sxs-lookup"><span data-stu-id="e2dc8-257">G (Source GUID)</span></span>  
  
    -   <span data-ttu-id="e2dc8-258">X（执行 GUID）</span><span class="sxs-lookup"><span data-stu-id="e2dc8-258">X (Execution GUID)</span></span>  
  
    -   <span data-ttu-id="e2dc8-259">M（消息）</span><span class="sxs-lookup"><span data-stu-id="e2dc8-259">M (Message)</span></span>  
  
    -   <span data-ttu-id="e2dc8-260">T（开始和结束时间）</span><span class="sxs-lookup"><span data-stu-id="e2dc8-260">T (Time Start and End)</span></span>  
  
     <span data-ttu-id="e2dc8-261">*list_options* 值包括：</span><span class="sxs-lookup"><span data-stu-id="e2dc8-261">The *list_options* values are as follows:</span></span>  
  
    -   <span data-ttu-id="e2dc8-262">*I* — 指定包含列表。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-262">*I* - Specifies the inclusion list.</span></span> <span data-ttu-id="e2dc8-263">仅记录指定的源名称或 GUID。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-263">Only the source names or GUIDs that are specified are logged.</span></span>  
  
    -   <span data-ttu-id="e2dc8-264">*E* — 指定排除列表。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-264">*E* - Specifies the exclusion list.</span></span> <span data-ttu-id="e2dc8-265">不记录指定的源名称或 GUID。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-265">The source names or GUIDs that are specified are not logged.</span></span>  
  
    -   <span data-ttu-id="e2dc8-266">为包含或排除指定的 *src_name_or_guid* 参数是事件名称、源名称或源 GUID。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-266">The *src_name_or_guid* parameter specified for inclusion or exclusion is an event name, source name, or source GUID.</span></span>  
  
     <span data-ttu-id="e2dc8-267">如果在同一个命令提示符中使用多个 **/ConsoleLog** 选项，它们的相互影响如下：</span><span class="sxs-lookup"><span data-stu-id="e2dc8-267">If you use multiple **/ConsoleLog** options on the same command prompt, they interact as follows:</span></span>  
  
    -   <span data-ttu-id="e2dc8-268">它们的出现顺序没有影响。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-268">Their order of appearance has no effect.</span></span>  
  
    -   <span data-ttu-id="e2dc8-269">如果命令行中不存在包含列表，将对所有类型日志项应用排除列表。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-269">If no inclusion lists are present on the command line, exclusion lists are applied against all kinds of log entries.</span></span>  
  
    -   <span data-ttu-id="e2dc8-270">如果命令行中存在包含列表，将对所有包含列表统一应用排除列表。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-270">If any inclusion lists are present on the command line, exclusion lists are applied against the union of all inclusion lists.</span></span>  
  
     <span data-ttu-id="e2dc8-271">有关 **/ConsoleLog**选项的示例，请参阅 "**备注**" 部分。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-271">For examples of the **/ConsoleLog** option, see the **Remarks** section.</span></span>  
  
-   <span data-ttu-id="e2dc8-272">**/D[ts]** _package_path_：</span><span class="sxs-lookup"><span data-stu-id="e2dc8-272">**/D[ts]** _package_path_:</span></span>   
                  <span data-ttu-id="e2dc8-273">可选。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-273">Optional.</span></span> <span data-ttu-id="e2dc8-274">从 SSIS 包存储区加载包。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-274">Loads a package from the SSIS Package Store.</span></span> <span data-ttu-id="e2dc8-275">使用旧的包部署模型部署存储在 SSIS 包存储区中的包。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-275">Packages that are stored in the SSIS Package Store, are deployed using the legacy package deployment model.</span></span> <span data-ttu-id="e2dc8-276">若要使用项目部署模型运行部署到 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 服务器的包，请使用 `/ISServer` 选项。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-276">To run packages that are deployed to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server using the project deployment model, use the `/ISServer` option.</span></span> <span data-ttu-id="e2dc8-277">有关包和项目部署模型的详细信息，请参阅 [Deployment of Projects and Packages](deploy-integration-services-ssis-projects-and-packages.md)。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-277">For more information about the package and project deployment models, see [Deployment of Projects and Packages](deploy-integration-services-ssis-projects-and-packages.md).</span></span>  
  
     <span data-ttu-id="e2dc8-278">*package_path* 参数指定 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 包的相对路径，从 SSIS 包存储的根目录开始，包括 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 包的名称。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-278">The *package_path* argument specifies the relative path of the [!INCLUDE[ssIS](../../includes/ssis-md.md)] package, starting at the root of the SSIS Package Store, and includes the name of the [!INCLUDE[ssIS](../../includes/ssis-md.md)] package.</span></span> <span data-ttu-id="e2dc8-279">如果 *package_path* 参数中指定的路径或文件名包含空格，则必须在 *package_path* 参数两侧加上引号。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-279">If the path or file name specified in the *package_path* argument contains a space, you must put quotation marks around the *package_path* argument.</span></span>  
  
     <span data-ttu-id="e2dc8-280">`/DTS` 选项不能与 `/File` 或 `/SQL` 选项一起使用。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-280">The `/DTS` option cannot be used together with the `/File` or `/SQL` option.</span></span> <span data-ttu-id="e2dc8-281">如果指定多个选项，`dtexec` 将失败。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-281">If multiple options are specified, `dtexec` fails.</span></span>  
  
-   <span data-ttu-id="e2dc8-282">**/De [dm-crypt]**  _password_： Optional。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-282">**/De[crypt]**  _password_: Optional.</span></span> <span data-ttu-id="e2dc8-283">设置加载使用密码加密的包时所用的解密密码。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-283">Sets the decryption password that is used when you load a package with password encryption.</span></span>  
  
-   <span data-ttu-id="e2dc8-284">**/Dump** _error code_：</span><span class="sxs-lookup"><span data-stu-id="e2dc8-284">**/Dump** _error code_:</span></span>  
                  <span data-ttu-id="e2dc8-285">可选：当包正在运行时，如果出现一个或多个指定的事件，则会创建调试转储文件 .mdmp 和 .tmp。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-285">Optional Creates the debug dump files, .mdmp and .tmp, when one or more specified events occur while the package is running.</span></span> <span data-ttu-id="e2dc8-286">error code 参数指定将触发系统创建调试转储文件的事件代码类型：错误、警告或信息  。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-286">The *error code* argument specifies the type of event code-error, warning, or information-that will trigger the system to create the debug dump files.</span></span> <span data-ttu-id="e2dc8-287">若要指定多个事件代码，请用分号 (;) 分隔每个 *error code* 参数。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-287">To specify multiple event codes, separate each *error code* argument by a semi-colon (;).</span></span> <span data-ttu-id="e2dc8-288">不要对 *error code* 参数使用引号。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-288">Do not include quotes with the *error code* argument.</span></span>  
  
     <span data-ttu-id="e2dc8-289">以下示例在发生 DTS_E_CANNOTACQUIRECONNECTIONFROMCONNECTIONMANAGER 错误时生成调试转储文件。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-289">The following example generates the debug dump files when the DTS_E_CANNOTACQUIRECONNECTIONFROMCONNECTIONMANAGER error occurs.</span></span>  
  
    ```  
    /Dump 0xC020801C  
    ```  
  
     <span data-ttu-id="e2dc8-290">默认情况下，将 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 调试转储文件存储在文件夹中 *\<drive>* ： \PROGRAM Files\Microsoft SQL server\110\shared\errordumps 文件夹</span><span class="sxs-lookup"><span data-stu-id="e2dc8-290">By default, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] stores the debug dump files in the folder, *\<drive>*:\Program Files\Microsoft SQL Server\110\Shared\ErrorDumps.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e2dc8-291">调试转储文件可能包含敏感信息。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-291">Debug dump files may contain sensitive information.</span></span> <span data-ttu-id="e2dc8-292">使用访问控制列表 (ACL) 来限制对这些文件的访问，或将文件复制到具有受限访问权限的文件夹中。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-292">Use an access control list (ACL) to restrict access to the files, or copy the files to a folder with restricted access.</span></span> <span data-ttu-id="e2dc8-293">例如，在将调试文件发送给 Microsoft 支持服务部门之前，建议您删除所有敏感信息或机密信息。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-293">For example, before you send your debug files to Microsoft support services, we recommended that you remove any sensitive or confidential information.</span></span>  
  
     <span data-ttu-id="e2dc8-294">若要将此选项应用到实用工具运行的所有包 `dtexec` ，请将**DumpOnCodes** REG_SZ 值添加到 HKEY_LOCAL_MACHINE \software\microsoft\microsoft SQL Server\110\SSIS\Setup\DtsPath 注册表项。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-294">To apply this option to all packages that the `dtexec` utility runs, add a **DumpOnCodes** REG_SZ value to the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\110\SSIS\Setup\DtsPath registry key.</span></span> <span data-ttu-id="e2dc8-295">**DumpOnCodes** 中的数据值指定将触发系统创建调试转储文件的错误代码或代码。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-295">The data value in **DumpOnCodes** specifies the error code or codes that will trigger the system to create debug dump files.</span></span> <span data-ttu-id="e2dc8-296">多个错误代码必须以分号 (;) 分隔。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-296">Multiple error codes must be separated by a semi-colon (;).</span></span>  
  
     <span data-ttu-id="e2dc8-297">如果将 **DumpOnCodes** 值添加到注册表项，并使用 **/Dump** 选项，系统将创建基于这两个设置的调试转储文件。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-297">If you add a **DumpOnCodes** value to the registry key, and use the **/Dump** option, the system will create debug dump files that are based on both settings.</span></span>  
  
     <span data-ttu-id="e2dc8-298">有关调试转储文件的详细信息，请参阅 [Generating Dump Files for Package Execution](../troubleshooting/generating-dump-files-for-package-execution.md)。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-298">For more information about debug dump files, see [Generating Dump Files for Package Execution](../troubleshooting/generating-dump-files-for-package-execution.md).</span></span>  
  
-   <span data-ttu-id="e2dc8-299">**/DumpOnError**：</span><span class="sxs-lookup"><span data-stu-id="e2dc8-299">**/DumpOnError**:</span></span>   
                  <span data-ttu-id="e2dc8-300">可选。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-300">Optional.</span></span> <span data-ttu-id="e2dc8-301">当包正在运行时，如果发生任何错误，则会创建调试转储文件 .mdmp 和 .tmp。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-301">Creates the debug dump files, .mdmp and .tmp, when any error occurs while the package is running.</span></span>  
  
     <span data-ttu-id="e2dc8-302">默认情况下，[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 将调试转储文件存储在 \<drive>:\Program Files\Microsoft SQL Server\110\Shared\ErrorDumps 文件夹中。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-302">By default, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] stores the debug dump files in the folder, *\<drive>*:\Program Files\Microsoft SQL Server\110\Shared\ErrorDumps folder.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e2dc8-303">调试转储文件可能包含敏感信息。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-303">Debug dump files may contain sensitive information.</span></span> <span data-ttu-id="e2dc8-304">使用访问控制列表 (ACL) 来限制对这些文件的访问，或将文件复制到具有受限访问权限的文件夹中。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-304">Use an access control list (ACL) to restrict access to the files, or copy the files to a folder with restricted access.</span></span> <span data-ttu-id="e2dc8-305">例如，在将调试文件发送给 Microsoft 支持服务部门之前，建议您删除所有敏感信息或机密信息。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-305">For example, before you send your debug files to Microsoft support services, we recommended that you remove any sensitive or confidential information.</span></span>  
  
     <span data-ttu-id="e2dc8-306">若要将此选项应用到实用工具运行的所有包 `dtexec` ，请将**DumpOnError** REG_DWORD 值添加到 HKEY_LOCAL_MACHINE \software\microsoft\microsoft SQL Server\110\SSIS\Setup\DtsPath 注册表项。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-306">To apply this option to all packages that the `dtexec` utility runs, add a **DumpOnError** REG_DWORD value to the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\110\SSIS\Setup\DtsPath registry key.</span></span> <span data-ttu-id="e2dc8-307">**DumpOnError**的值 REG_DWORD 值决定了 **/DumpOnError**选项是否需要与实用工具一起使用 `dtexec` ：</span><span class="sxs-lookup"><span data-stu-id="e2dc8-307">The value of the **DumpOnError** REG_DWORD value determines whether the **/DumpOnError** option needs to be used with the `dtexec` utility:</span></span>  
  
    -   <span data-ttu-id="e2dc8-308">非零数据值指示在发生任何错误时系统将创建调试转储文件，无论是否将 **/DumpOnError**选项与实用工具一起使用 `dtexec` 。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-308">A non-zero data value indicates that the system will create debug dump files when any error occurs, regardless of whether you use the **/DumpOnError** option with the `dtexec` utility.</span></span>  
  
    -   <span data-ttu-id="e2dc8-309">零数据值指示，除非将 **/DumpOnError**选项与实用工具一起使用，否则系统将不会创建调试转储文件 `dtexec` 。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-309">A zero data value indicates that the system will not create the debug dump files unless you use the **/DumpOnError** option with the `dtexec` utility.</span></span>  
  
     <span data-ttu-id="e2dc8-310">有关调试转储文件的详细信息，请参阅 [Generating Dump Files for Package Execution](../troubleshooting/generating-dump-files-for-package-execution.md)。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-310">For more information about debug dump files, see [Generating Dump Files for Package Execution](../troubleshooting/generating-dump-files-for-package-execution.md)</span></span>  
  
-   <span data-ttu-id="e2dc8-311">`/Env[Reference]`*环境引用 ID*：</span><span class="sxs-lookup"><span data-stu-id="e2dc8-311">`/Env[Reference]` *environment reference ID*:</span></span>   
                  <span data-ttu-id="e2dc8-312">可选。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-312">Optional.</span></span> <span data-ttu-id="e2dc8-313">为部署到 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 服务器的包指定包执行使用的环境引用 (ID)。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-313">Specifies the environment reference (ID) that is used by the package execution, for a package that is deployed to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server.</span></span> <span data-ttu-id="e2dc8-314">配置为绑定到变量的参数将使用环境中包含的变量值。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-314">The parameters configured to bind to variables will use the values of the variables that are contained in the environment.</span></span>  
  
     <span data-ttu-id="e2dc8-315">可以将 `/Env[Reference]` 选项与 `/ISServer` 和 `/Server` 选项一起使用。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-315">You use `/Env[Reference]` option together with the `/ISServer` and the `/Server` options.</span></span>  
  
     <span data-ttu-id="e2dc8-316">此参数由 SQL Server 代理使用。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-316">This parameter is used by SQL Server Agent.</span></span>  
  
-   <span data-ttu-id="e2dc8-317">**/F[ile]** _filespec_：</span><span class="sxs-lookup"><span data-stu-id="e2dc8-317">**/F[ile]** _filespec_:</span></span>   
                  <span data-ttu-id="e2dc8-318">可选。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-318">Optional.</span></span> <span data-ttu-id="e2dc8-319">加载保存在文件系统中的包。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-319">Loads a package that is saved in the file system.</span></span> <span data-ttu-id="e2dc8-320">使用旧的包部署模型部署保存在文件系统中的包。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-320">Packages that are saved in the file system, are deployed using the legacy package deployment model.</span></span> <span data-ttu-id="e2dc8-321">若要使用项目部署模型运行部署到 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 服务器的包，请使用 `/ISServer` 选项。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-321">To run packages that are deployed to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server using the project deployment model, use the `/ISServer` option.</span></span> <span data-ttu-id="e2dc8-322">有关包和项目部署模型的详细信息，请参阅 [Deployment of Projects and Packages](deploy-integration-services-ssis-projects-and-packages.md)。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-322">For more information about the package and project deployment models, see [Deployment of Projects and Packages](deploy-integration-services-ssis-projects-and-packages.md)</span></span>  
  
     <span data-ttu-id="e2dc8-323">*filespec* 参数指定包的路径和文件名。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-323">The *filespec* argument specifies the path and file name of the package.</span></span> <span data-ttu-id="e2dc8-324">可以将路径指定为通用命名约定 (UNC) 路径或本地路径。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-324">You can specify the path as either a Universal Naming Convention (UNC) path or a local path.</span></span> <span data-ttu-id="e2dc8-325">如果 *filespec* 参数中指定的路径或文件名包含空格，则必须在 *filespec* 参数两侧加上引号。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-325">If the path or file name specified in the *filespec* argument contains a space, you must put quotation marks around the *filespec* argument.</span></span>  
  
     <span data-ttu-id="e2dc8-326">`/File` 选项不能与 `/DTS` 或 `/SQL` 选项一起使用。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-326">The `/File` option cannot be used together with the `/DTS` or `/SQL` option.</span></span> <span data-ttu-id="e2dc8-327">如果指定多个选项，`dtexec` 将失败。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-327">If multiple options are specified, `dtexec` fails.</span></span>  
  
-   <span data-ttu-id="e2dc8-328">**/H [elp]** [*Option_name*]：可选。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-328">**/H[elp]** [*option_name*]: Optional.</span></span> <span data-ttu-id="e2dc8-329">显示选项的帮助，或显示指定的 *option_name* 的帮助，同时关闭实用工具。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-329">Displays help for the options, or displays help for the specified *option_name* and closes the utility.</span></span>  
  
     <span data-ttu-id="e2dc8-330">如果指定*option_name*参数，则将 `dtexec` 启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 联机丛书并显示 dtexec 实用工具主题。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-330">If you specify an *option_name* argument, `dtexec` starts [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online and displays the dtexec Utility topic.</span></span>  
  
-   <span data-ttu-id="e2dc8-331">`/ISServer`*packagepath*：</span><span class="sxs-lookup"><span data-stu-id="e2dc8-331">`/ISServer` *packagepath*:</span></span>  
                  <span data-ttu-id="e2dc8-332">可选。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-332">Optional.</span></span> <span data-ttu-id="e2dc8-333">运行部署到 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 服务器的包。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-333">Runs a package that is deployed to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server.</span></span> <span data-ttu-id="e2dc8-334">*PackagePath* 参数指定部署到 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 服务器的包的完整路径和文件名。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-334">The *PackagePath* argument specifies the full path and file name of the package deployed to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server.</span></span> <span data-ttu-id="e2dc8-335">如果 *PackagePath* 参数中指定的路径或文件名包含空格，则必须在 *PackagePath* 参数两侧加上引号。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-335">If the path or file name specified in the *PackagePath* argument contains a space, you must put quotation marks around the *PackagePath* argument.</span></span>  
  
     <span data-ttu-id="e2dc8-336">包格式如下所示：</span><span class="sxs-lookup"><span data-stu-id="e2dc8-336">The package format is as follows:</span></span>  
  
    ```  
    \<catalog name>\<folder name>\<project name>\package file name  
    ```  
  
     <span data-ttu-id="e2dc8-337">可以将 `/Server` 选项与 `/ISSERVER` 选项一起使用。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-337">You use `/Server` option together with the `/ISSERVER` option.</span></span> <span data-ttu-id="e2dc8-338">只有 Windows 身份验证可以在 SSIS 服务器上执行包。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-338">Only Windows Authentication can execute a package on the SSIS Server.</span></span> <span data-ttu-id="e2dc8-339">当前 Windows 用户用于访问该包。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-339">The current Windows user is used to access the package.</span></span> <span data-ttu-id="e2dc8-340">如果省略 /Server 选项，则假定使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的默认本地实例。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-340">If the /Server option is omitted, the default local instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is assumed.</span></span>  
  
     <span data-ttu-id="e2dc8-341">`/ISSERVER` 选项不能与 `/DTS`、`/SQL` 或 `/File` 选项一起使用。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-341">The `/ISSERVER` option cannot be used together with the `/DTS`, `/SQL` or `/File` option.</span></span> <span data-ttu-id="e2dc8-342">如果指定多个选项，dtexec 将失败。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-342">If multiple options are specified, dtexec fails.</span></span>  
  
     <span data-ttu-id="e2dc8-343">此参数由 SQL Server 代理使用。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-343">This parameter is used by SQL Server Agent.</span></span>  
  
-   <span data-ttu-id="e2dc8-344">**/L[ogger]** _classid_orprogid;configstring_：</span><span class="sxs-lookup"><span data-stu-id="e2dc8-344">**/L[ogger]** _classid_orprogid;configstring_:</span></span>  
                  <span data-ttu-id="e2dc8-345">可选。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-345">Optional.</span></span> <span data-ttu-id="e2dc8-346">将一个或多个日志提供程序与 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 包的执行关联。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-346">Associates one or more log providers with the execution of an [!INCLUDE[ssIS](../../includes/ssis-md.md)] package.</span></span> <span data-ttu-id="e2dc8-347">*classid_orprogid* 参数指定日志提供程序，可以指定为类 GUID。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-347">The *classid_orprogid* parameter specifies the log provider, and can be specified as a class GUID.</span></span> <span data-ttu-id="e2dc8-348">*configstring* 是用于配置日志提供程序的字符串。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-348">The *configstring* is the string that is used to configure the log provider.</span></span>  
  
     <span data-ttu-id="e2dc8-349">以下列表显示了可用的日志提供程序：</span><span class="sxs-lookup"><span data-stu-id="e2dc8-349">The following list shows the available log providers:</span></span>  
  
    -   <span data-ttu-id="e2dc8-350">文本文件：</span><span class="sxs-lookup"><span data-stu-id="e2dc8-350">Text file:</span></span>  
  
        -   <span data-ttu-id="e2dc8-351">ProgID：DTS.LogProviderTextFile.1</span><span class="sxs-lookup"><span data-stu-id="e2dc8-351">ProgID: DTS.LogProviderTextFile.1</span></span>  
  
        -   <span data-ttu-id="e2dc8-352">ClassID：{59B2C6A5-663F-4C20-8863-C83F9B72E2EB}</span><span class="sxs-lookup"><span data-stu-id="e2dc8-352">ClassID: {59B2C6A5-663F-4C20-8863-C83F9B72E2EB}</span></span>  
  
    -   [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]<span data-ttu-id="e2dc8-353">:</span><span class="sxs-lookup"><span data-stu-id="e2dc8-353">:</span></span>  
  
        -   <span data-ttu-id="e2dc8-354">ProgID：DTS.LogProviderSQLProfiler.1</span><span class="sxs-lookup"><span data-stu-id="e2dc8-354">ProgID: DTS.LogProviderSQLProfiler.1</span></span>  
  
        -   <span data-ttu-id="e2dc8-355">ClassID：{5C0B8D21-E9AA-462E-BA34-30FF5F7A42A1}</span><span class="sxs-lookup"><span data-stu-id="e2dc8-355">ClassID: {5C0B8D21-E9AA-462E-BA34-30FF5F7A42A1}</span></span>  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="e2dc8-356">:</span><span class="sxs-lookup"><span data-stu-id="e2dc8-356">:</span></span>  
  
        -   <span data-ttu-id="e2dc8-357">ProgID：DTS.LogProviderSQLServer.1</span><span class="sxs-lookup"><span data-stu-id="e2dc8-357">ProgID: DTS.LogProviderSQLServer.1</span></span>  
  
        -   <span data-ttu-id="e2dc8-358">ClassID：{6AA833A1-E4B2-4431-831B-DE695049DC61}</span><span class="sxs-lookup"><span data-stu-id="e2dc8-358">ClassID: {6AA833A1-E4B2-4431-831B-DE695049DC61}</span></span>  
  
    -   <span data-ttu-id="e2dc8-359">Windows 事件日志：</span><span class="sxs-lookup"><span data-stu-id="e2dc8-359">Windows Event Log:</span></span>  
  
        -   <span data-ttu-id="e2dc8-360">ProgID：DTS.LogProviderEventLog.1</span><span class="sxs-lookup"><span data-stu-id="e2dc8-360">ProgID: DTS.LogProviderEventLog.1</span></span>  
  
        -   <span data-ttu-id="e2dc8-361">ClassID：{97634F75-1DC7-4F1F-8A4C-DAF0E13AAA22}</span><span class="sxs-lookup"><span data-stu-id="e2dc8-361">ClassID: {97634F75-1DC7-4F1F-8A4C-DAF0E13AAA22}</span></span>  
  
    -   <span data-ttu-id="e2dc8-362">XML 文件：</span><span class="sxs-lookup"><span data-stu-id="e2dc8-362">XML File:</span></span>  
  
        -   <span data-ttu-id="e2dc8-363">ProgID：DTS.LogProviderXMLFile.1</span><span class="sxs-lookup"><span data-stu-id="e2dc8-363">ProgID: DTS.LogProviderXMLFile.1</span></span>  
  
        -   <span data-ttu-id="e2dc8-364">ClassID：{AFED6884-619C-484F-9A09-F42D56E1A7EA}</span><span class="sxs-lookup"><span data-stu-id="e2dc8-364">ClassID: {AFED6884-619C-484F-9A09-F42D56E1A7EA}</span></span>  
  
-   <span data-ttu-id="e2dc8-365">**/M[axConcurrent]** _concurrent_executables_：</span><span class="sxs-lookup"><span data-stu-id="e2dc8-365">**/M[axConcurrent]** _concurrent_executables_:</span></span>  
                  <span data-ttu-id="e2dc8-366">可选。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-366">Optional.</span></span> <span data-ttu-id="e2dc8-367">指定包可以同时执行的可执行文件数。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-367">Specifies the number of executable files that the package can run concurrently.</span></span> <span data-ttu-id="e2dc8-368">指定的值必须是非负整数或 -1。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-368">The value specified must be either a non-negative integer, or -1.</span></span> <span data-ttu-id="e2dc8-369">如果值为 -1，则表示 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 所允许的最大并发运行可执行文件数等于执行包的计算机上的处理器总数加二。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-369">A value of -1 means that [!INCLUDE[ssIS](../../includes/ssis-md.md)] will allow a maximum number of concurrently running executables that is equal to the total number of processors on the computer executing the package, plus two.</span></span>  
  
-   <span data-ttu-id="e2dc8-370">**/Pack[age]** _PackageName_：</span><span class="sxs-lookup"><span data-stu-id="e2dc8-370">**/Pack[age]** _PackageName_:</span></span>  
                  <span data-ttu-id="e2dc8-371">可选。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-371">Optional.</span></span> <span data-ttu-id="e2dc8-372">指定执行的包。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-372">Specifies the package that is executed.</span></span> <span data-ttu-id="e2dc8-373">当从 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]执行包时，主要使用此参数。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-373">This parameter is used primarily when you execute the package from [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].</span></span>  
  
-   <span data-ttu-id="e2dc8-374">**/P [assword]** _密码_：</span><span class="sxs-lookup"><span data-stu-id="e2dc8-374">**/P[assword]** _password_:</span></span>  
                  <span data-ttu-id="e2dc8-375">可选。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-375">Optional.</span></span> <span data-ttu-id="e2dc8-376">允许检索受 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证保护的包。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-376">Allows the retrieval of a package that is protected by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="e2dc8-377">该选项与 **/User** 选项一起使用。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-377">This option is used together with the **/User** option.</span></span> <span data-ttu-id="e2dc8-378">如果省略 **/Password** 选项但使用 **/User** 选项，则使用空白密码。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-378">If the **/Password** option is omitted and the **/User** option is used, a blank password is used.</span></span> <span data-ttu-id="e2dc8-379">*password* 值可以用引号引起来。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-379">The *password* value may be quoted.</span></span>  
  
    > [!IMPORTANT]  
    >  [!INCLUDE[ssNoteWinAuthentication](../../../includes/ssnotewinauthentication-md.md)]  
  
-   <span data-ttu-id="e2dc8-380">**/Par [ameter]** [$Package：： | $Project：： | $ServerOption：：] *parameter_name* [ (data_type) ];*literal_value*：可选。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-380">**/Par[ameter]** [$Package:: | $Project:: | $ServerOption::] *parameter_name* [(data_type)]; *literal_value*: Optional.</span></span> <span data-ttu-id="e2dc8-381">指定参数值。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-381">Specifies parameter values.</span></span> <span data-ttu-id="e2dc8-382">可以指定多个 **/Parameter** 选项。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-382">Multiple **/Parameter** options can be specified.</span></span> <span data-ttu-id="e2dc8-383">数据类型是作为字符串的 CLR TypeCodes。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-383">The data types are CLR TypeCodes as strings.</span></span> <span data-ttu-id="e2dc8-384">对于非字符串参数，在括号中指定数据类型，前面接着参数名称。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-384">For a non-string parameter, the data type is specified in parenthesis, following the parameter name.</span></span>  
  
     <span data-ttu-id="e2dc8-385">**/Parameter**选项只能与选项一起使用 `/ISServer` 。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-385">The **/Parameter** option can be used only with the `/ISServer` option.</span></span>  
  
     <span data-ttu-id="e2dc8-386">使用 $Package、$Project 和 $ServerOption 前缀分别指示包参数、项目参数和服务器选项参数。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-386">You use the $Package, $Project, and $ServerOption prefixes to indicate a package parameter, project parameter, and a server option parameter, respectively.</span></span> <span data-ttu-id="e2dc8-387">默认参数类型为包。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-387">The default parameter type is package.</span></span>  
  
     <span data-ttu-id="e2dc8-388">以下示例执行一个包并为项目参数 (myparam) 提供 myvalue 以及为包参数 (anotherparam) 提供整数值 12。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-388">The following is an example of executing a package and providing myvalue for the project parameter (myparam) and the integer value 12 for the package parameter (anotherparam).</span></span>  
  
     `Dtexec /isserver "SSISDB\MyFolder\MyProject\MyPackage.dtsx" /server "." /parameter $Project::myparam;myvalue /parameter anotherparam(int32);12`  
  
     <span data-ttu-id="e2dc8-389">您还可以通过使用参数设置连接管理器属性。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-389">You can also set connection manager properties by using parameters.</span></span> <span data-ttu-id="e2dc8-390">可以使用 CM 前缀来表示连接管理器参数。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-390">You use the CM prefix to denote a connection manager parameter.</span></span>  
  
     <span data-ttu-id="e2dc8-391">在以下示例中，将 SourceServer 连接管理器的 InitialCatalog 属性设置为 `ssisdb`。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-391">In the following example, InitialCatalog property of the SourceServer connection manager is set to `ssisdb`.</span></span>  
  
    ```  
    /parameter CM.SourceServer.InitialCatalog;ssisdb  
    ```  
  
     <span data-ttu-id="e2dc8-392">在以下示例中，将 SourceServer 连接管理器的 ServerName 属性设置为一个句点 (.)，用来指示本地服务器。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-392">In the following example, ServerName property of the SourceServer connection manager is set to a period (.) to indicate the local server.</span></span>  
  
    ```  
    /parameter CM.SourceServer.ServerName;.  
    ```  
  
-   <span data-ttu-id="e2dc8-393">**/Proj[ect]** _ProjectFile_：</span><span class="sxs-lookup"><span data-stu-id="e2dc8-393">**/Proj[ect]** _ProjectFile_:</span></span>  
                  <span data-ttu-id="e2dc8-394">可选。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-394">Optional.</span></span> <span data-ttu-id="e2dc8-395">指定从中检索执行的包的项目。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-395">Specifies the project from which to retrieve the package that is executed.</span></span> <span data-ttu-id="e2dc8-396">*ProjectFile* 参数指定 .ispac 文件名。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-396">The *ProjectFile* argument specifies the .ispac file name.</span></span> <span data-ttu-id="e2dc8-397">当从 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]执行包时，主要使用此参数。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-397">This parameter is used primarily when you execute the package from [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].</span></span>  
  
-   <span data-ttu-id="e2dc8-398">**/Rem** _comment_：</span><span class="sxs-lookup"><span data-stu-id="e2dc8-398">**/Rem** _comment_:</span></span>  
                  <span data-ttu-id="e2dc8-399">可选。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-399">Optional.</span></span> <span data-ttu-id="e2dc8-400">在命令提示符或命令文件中包含注释。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-400">Includes comments on the command prompt or in command files.</span></span> <span data-ttu-id="e2dc8-401">该参数可选。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-401">The argument is optional.</span></span> <span data-ttu-id="e2dc8-402">*comment* 的值是字符串，必须用引号引起来或不含空格。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-402">The value of *comment* is a string that must be enclosed in quotation marks, or contain no white space.</span></span> <span data-ttu-id="e2dc8-403">如果未指定参数，将插入一个空行。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-403">If no argument is specified, a blank line is inserted.</span></span> <span data-ttu-id="e2dc8-404">命令选项确定阶段，将放弃*comment* 值。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-404">*comment* values are discarded during the command sourcing phase.</span></span>  
  
-   <span data-ttu-id="e2dc8-405">**/Rep [orting]** _level_ [*; event_guid_or_name*[*; event_guid_or_name*[...]]：可选。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-405">**/Rep[orting]** _level_ [*;event_guid_or_name*[*;event_guid_or_name*[...]]: Optional.</span></span> <span data-ttu-id="e2dc8-406">指定要报告的消息类型。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-406">Specifies what types of messages to report.</span></span> <span data-ttu-id="e2dc8-407">*level* 可用的报告选项如下：</span><span class="sxs-lookup"><span data-stu-id="e2dc8-407">The available reporting options for *level* are as follows:</span></span>  
  
     <span data-ttu-id="e2dc8-408">**N** 无报告。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-408">**N** No reporting.</span></span>  
  
     <span data-ttu-id="e2dc8-409">`E`报告错误。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-409">`E` Errors are reported.</span></span>  
  
     <span data-ttu-id="e2dc8-410">**W** 报告警告。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-410">**W** Warnings are reported.</span></span>  
  
     <span data-ttu-id="e2dc8-411">`I`报告信息性消息。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-411">`I` Informational messages are reported.</span></span>  
  
     <span data-ttu-id="e2dc8-412">**C** 报告自定义事件。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-412">**C** Custom events are reported.</span></span>  
  
     <span data-ttu-id="e2dc8-413">**D** 报告数据流任务事件。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-413">**D** Data Flow task events are reported.</span></span>  
  
     <span data-ttu-id="e2dc8-414">**P** 报告进度。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-414">**P** Progress is reported.</span></span>  
  
     <span data-ttu-id="e2dc8-415">**V** 详细报告。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-415">**V** Verbose reporting.</span></span>  
  
     <span data-ttu-id="e2dc8-416">V 和 N 参数与所有其他参数互相排斥，必须单独指定。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-416">The arguments of V and N are mutually exclusive to all other arguments; they must be specified alone.</span></span> <span data-ttu-id="e2dc8-417">如果未指定 **/Reporting**选项，则默认级别为 `E` (错误) ， **W** (警告) ， **P** (进度) 。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-417">If the **/Reporting** option is not specified then the default level is `E` (errors), **W** (warnings), and **P** (progress).</span></span>  
  
     <span data-ttu-id="e2dc8-418">所有事件前都有一个格式为“YY/MM/DD HH:MM:SS”的时间戳以及一个 GUID 或友好名称（如果可用）。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-418">All events are preceded with a timestamp in the format "YY/MM/DD HH:MM:SS", and a GUID or friendly name if available.</span></span>  
  
     <span data-ttu-id="e2dc8-419">可选参数 *event_guid_or_name* 是日志提供程序的异常列表。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-419">The optional parameter *event_guid_or_name* is a list of exceptions to the log providers.</span></span> <span data-ttu-id="e2dc8-420">该异常指定本应记录但却未记录的事件。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-420">The exception specifies the events that are not logged that otherwise might have been logged.</span></span>  
  
     <span data-ttu-id="e2dc8-421">如果默认情况下通常不记录某个事件，则不必排除该事件。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-421">You do not have to exclude an event if the event is not ordinarily logged by default</span></span>  
  
-   <span data-ttu-id="e2dc8-422">**/Res [t) ]** {*deny | force | IfPossible*}： Optional。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-422">**/Res[tart]** {*deny | force | ifPossible*}: Optional.</span></span> <span data-ttu-id="e2dc8-423">为包的 <xref:Microsoft.SqlServer.Dts.Runtime.Package.CheckpointUsage%2A> 属性指定新值。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-423">Specifies a new value for the <xref:Microsoft.SqlServer.Dts.Runtime.Package.CheckpointUsage%2A> property on the package.</span></span> <span data-ttu-id="e2dc8-424">各参数的含义如下：</span><span class="sxs-lookup"><span data-stu-id="e2dc8-424">The meaning of the parameters are as follows:</span></span>  
  
     <span data-ttu-id="e2dc8-425">*Deny* 将 <xref:Microsoft.SqlServer.Dts.Runtime.Package.CheckpointUsage%2A> 属性设置为 <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DTSCheckpointUsage.DTSCU_NEVER>。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-425">*Deny* Sets <xref:Microsoft.SqlServer.Dts.Runtime.Package.CheckpointUsage%2A> property to <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DTSCheckpointUsage.DTSCU_NEVER>.</span></span>  
  
     <span data-ttu-id="e2dc8-426">*Force* 将 <xref:Microsoft.SqlServer.Dts.Runtime.Package.CheckpointUsage%2A> 属性设置为 <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DTSCheckpointUsage.DTSCU_ALWAYS>。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-426">*Force* Sets <xref:Microsoft.SqlServer.Dts.Runtime.Package.CheckpointUsage%2A> property to <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DTSCheckpointUsage.DTSCU_ALWAYS>.</span></span>  
  
     <span data-ttu-id="e2dc8-427">*ifPossible* 将 <xref:Microsoft.SqlServer.Dts.Runtime.Package.CheckpointUsage%2A> 属性设置为 <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DTSCheckpointUsage.DTSCU_IFEXISTS>。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-427">*ifPossible* Sets <xref:Microsoft.SqlServer.Dts.Runtime.Package.CheckpointUsage%2A> property to <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DTSCheckpointUsage.DTSCU_IFEXISTS>.</span></span>  
  
     <span data-ttu-id="e2dc8-428">如果不指定值，则使用默认值 **force** 。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-428">The default value of **force** is used if no value is specified.</span></span>  
  
-   <span data-ttu-id="e2dc8-429">**/Set** [$Sensitive：：]*propertyPath; 值*：可选。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-429">**/Set** [$Sensitive::]*propertyPath;value*: Optional.</span></span> <span data-ttu-id="e2dc8-430">覆盖包中参数、变量、属性、容器、日志提供程序、Foreach 枚举器或连接的配置。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-430">Overrides the configuration of a parameter, variable, property, container, log provider, Foreach enumerator, or connection within a package.</span></span> <span data-ttu-id="e2dc8-431">使用该选项时， **/Set** 可将 *propertyPath* 参数更改为指定的值。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-431">When this option is used, **/Set** changes the *propertyPath* argument to the value specified.</span></span> <span data-ttu-id="e2dc8-432">可以指定多个 **/Set** 选项。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-432">Multiple **/Set** options can be specified.</span></span>  
  
     <span data-ttu-id="e2dc8-433">除了将 **/set**选项与 **/f [ile]** 选项一起使用之外，还可以将 **/set**选项与 `/ISServer` 选项或选项一起使用 `/Project` 。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-433">In addition to using the **/Set** option with the **/F[ile]** option, you can also use the **/Set** option with the `/ISServer` option or the `/Project` option.</span></span> <span data-ttu-id="e2dc8-434">当你将 **/set**与结合使用时 `/Project` ， **/set**会设置参数值。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-434">When you use **/Set** with `/Project`, **/Set** sets parameter values.</span></span> <span data-ttu-id="e2dc8-435">当你将 **/set**与一起使用时 `/ISServer` ， **/set**会设置属性重写。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-435">When you use **/Set** with `/ISServer`, **/Set** sets property overrides.</span></span> <span data-ttu-id="e2dc8-436">此外，将 **/set**与结合使用时 `/ISServer` ，可以使用可选的 $Sensitive 前缀来指示应在服务器上将该属性视为敏感属性 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-436">In addition, when you use **/Set** with `/ISServer`, you can use the optional $Sensitive prefix to indicate that the property should be treated as sensitive on the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server.</span></span>  
  
     <span data-ttu-id="e2dc8-437">可以通过运行包配置向导确定 *propertyPath* 的值。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-437">You can determine the value of *propertyPath* by running the Package Configuration Wizard.</span></span> <span data-ttu-id="e2dc8-438">选定项的路径会显示在最后一个 **“完成向导”** 页中，可以进行复制和粘贴。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-438">The paths for items that you select are displayed on the final **Completing the Wizard** page, and can be copied and pasted.</span></span> <span data-ttu-id="e2dc8-439">如果仅以此目的使用该向导，则可以在复制路径后取消它。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-439">If you have used the wizard only for this purpose, you can cancel the wizard after you copy the paths.</span></span>  
  
     <span data-ttu-id="e2dc8-440">以下示例执行文件系统中保存的包并为变量提供新值：</span><span class="sxs-lookup"><span data-stu-id="e2dc8-440">The following is an example of executing a package that is saved in the file system and providing a new value for a variable:</span></span>  
  
     `dtexec /f mypackage.dtsx /set \package.variables[myvariable].Value;myvalue`  
  
     <span data-ttu-id="e2dc8-441">以下示例从 .ispac 项目文件运行包并设置包参数和项目参数。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-441">The following example of running a package from the .ispac project file and setting package and project parameters.</span></span>  
  
     `/Project c:\project.ispac /Package Package1.dtsx /SET \Package.Variables[$Package::Parameter];1 /SET \Package.Variables[$Project::Parameter];1`  
  
     <span data-ttu-id="e2dc8-442">可以使用 **/Set** 选项更改自其加载包配置的位置。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-442">You can use the **/Set** option to change the location from which package configurations are loaded.</span></span> <span data-ttu-id="e2dc8-443">但是，不能使用 **/Set** 选项覆盖设计时某个配置所指定的值。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-443">However, you cannot use the **/Set** option to override a value that was specified by a configuration at design time.</span></span> <span data-ttu-id="e2dc8-444">若要了解如何应用包配置，请参阅[包配置](../package-configurations.md)和[SQL Server 2014 中 Integration Services 功能的行为更改](../behavior-changes-to-integration-services-features-in-sql-server-2014.md)。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-444">To understand how package configurations are applied, see [Package Configurations](../package-configurations.md) and [Behavior Changes to Integration Services Features in SQL Server 2014](../behavior-changes-to-integration-services-features-in-sql-server-2014.md).</span></span>  
  
-   <span data-ttu-id="e2dc8-445">`/Ser[ver]`*服务器*：</span><span class="sxs-lookup"><span data-stu-id="e2dc8-445">`/Ser[ver]` *server*:</span></span>  
                  <span data-ttu-id="e2dc8-446">可选。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-446">Optional.</span></span> <span data-ttu-id="e2dc8-447">指定了 `/SQL` 或 `/DTS` 选项时，此选项可以指定从中检索包的服务器的名称。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-447">When the `/SQL` or `/DTS` option is specified, this option specifies the name of the server from which to retrieve the package.</span></span> <span data-ttu-id="e2dc8-448">如果省略 `/Server` 选项并指定 `/SQL` 或 `/DTS` 选项，则尝试对本地服务器执行包。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-448">If you omit the `/Server` option and the `/SQL` or `/DTS` option is specified, package execution is tried against the local server.</span></span> <span data-ttu-id="e2dc8-449">*server_instance* 值可以用引号引起来。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-449">The *server_instance* value may be quoted.</span></span>  
  
     <span data-ttu-id="e2dc8-450">指定 `/Ser[ver]` 选项时，必须指定 `/ISServer` 选项。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-450">The `/Ser[ver]` option is required when the `/ISServer` option is specified.</span></span>  
  
-   <span data-ttu-id="e2dc8-451">**/SQ[L]** _package_path_：</span><span class="sxs-lookup"><span data-stu-id="e2dc8-451">**/SQ[L]** _package_path_:</span></span>  
                  <span data-ttu-id="e2dc8-452">加载存储在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的 `msdb` 数据库中的包。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-452">Loads a package that is stored in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], in `msdb` database.</span></span> <span data-ttu-id="e2dc8-453">使用包部署模型部署存储在 `msdb` 数据库中的包。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-453">Packages that are stored in the `msdb` database, are deployed using the package deployment model.</span></span> <span data-ttu-id="e2dc8-454">若要使用项目部署模型运行部署到 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 服务器的包，请使用 `/ISServer` 选项。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-454">To run packages that are deployed to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server using the project deployment model, use the `/ISServer` option.</span></span> <span data-ttu-id="e2dc8-455">有关包和项目部署模型的详细信息，请参阅 [Deployment of Projects and Packages](deploy-integration-services-ssis-projects-and-packages.md)。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-455">For more information about the package and project deployment models, see [Deployment of Projects and Packages](deploy-integration-services-ssis-projects-and-packages.md).</span></span>  
  
     <span data-ttu-id="e2dc8-456">*package_path* 参数指定要检索的包的名称。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-456">The *package_path* argument specifies the name of the package to retrieve.</span></span> <span data-ttu-id="e2dc8-457">如果文件夹包含在路径中，则文件夹将以反斜杠（“\\”）结束。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-457">If folders are included in the path, they are terminated with backslashes ("\\").</span></span> <span data-ttu-id="e2dc8-458">*package_path* 值可以用引号引起来。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-458">The *package_path* value can be quoted.</span></span> <span data-ttu-id="e2dc8-459">如果 *package_path* 参数中指定的路径或文件名包含空格，则必须在 *package_path* 参数两侧加上引号。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-459">If the path or file name specified in the *package_path* argument contains a space, you must put quotation marks around the *package_path* argument.</span></span>  
  
     <span data-ttu-id="e2dc8-460">可以将 **/user**、 **/password**和 `/Server` 选项与选项一起使用 `/SQL` 。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-460">You can use the **/User**, **/Password**, and `/Server` options together with the `/SQL` option.</span></span>  
  
     <span data-ttu-id="e2dc8-461">如果省略 **/User** 选项，则使用 Windows 身份验证来访问包。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-461">If you omit the **/User** option, Windows Authentication is used to access the package.</span></span> <span data-ttu-id="e2dc8-462">如果使用 **/User** 选项，指定的 **/User** 登录名将与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证相关联。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-462">If you use the **/User** option, the **/User** login name specified is associated with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
     <span data-ttu-id="e2dc8-463">**/Password** 选项仅与 **/User** 选项一起使用。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-463">The **/Password** option is used only together with the **/User** option.</span></span> <span data-ttu-id="e2dc8-464">如果使用 **/Password** 选项，则使用提供的用户名和密码信息访问包。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-464">If you use the **/Password** option, the package is accessed with the user name and password information provided.</span></span> <span data-ttu-id="e2dc8-465">如果省略 **/Password** 选项，则使用空密码。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-465">If you omit the **/Password** option, a blank password is used.</span></span>  
  
    > [!IMPORTANT]  
    >  [!INCLUDE[ssNoteWinAuthentication](../../../includes/ssnotewinauthentication-md.md)]  
  
     <span data-ttu-id="e2dc8-466">如果省略 `/Server` 选项，则假定使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的默认本地实例。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-466">If the `/Server` option is omitted, the default local instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is assumed.</span></span>  
  
     <span data-ttu-id="e2dc8-467">`/SQL` 选项不能与 `/DTS` 或 `/File` 选项一起使用。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-467">The `/SQL` option cannot be used together with the `/DTS` or `/File` option.</span></span> <span data-ttu-id="e2dc8-468">如果指定多个选项，`dtexec` 将失败。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-468">If multiple options are specified, `dtexec` fails.</span></span>  
  
-   <span data-ttu-id="e2dc8-469">**/Su [m]**：可选。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-469">**/Su[m]**: Optional.</span></span> <span data-ttu-id="e2dc8-470">显示一个递增计数器，其中包含下一个组件将接收的行数。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-470">Shows an incremental counter that contains the number of rows that will be received by the next component.</span></span>  
  
-   <span data-ttu-id="e2dc8-471">**/U [ser]** _user_name_：</span><span class="sxs-lookup"><span data-stu-id="e2dc8-471">**/U[ser]** _user_name_:</span></span>  
                  <span data-ttu-id="e2dc8-472">可选。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-472">Optional.</span></span> <span data-ttu-id="e2dc8-473">允许检索受 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证保护的包。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-473">Allows the retrieval of a package that is protected by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="e2dc8-474">仅当指定了 `/SQL` 选项时才使用此选项。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-474">This option is used only when the `/SQL` option is specified.</span></span> <span data-ttu-id="e2dc8-475">*user_name* 值可以用引号引起来。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-475">The *user_name* value can be quoted.</span></span>  
  
    > [!IMPORTANT]  
    >  [!INCLUDE[ssNoteWinAuthentication](../../../includes/ssnotewinauthentication-md.md)]  
  
-   <span data-ttu-id="e2dc8-476">**/Va [lidate]**：</span><span class="sxs-lookup"><span data-stu-id="e2dc8-476">**/Va[lidate]**:</span></span>  
                  <span data-ttu-id="e2dc8-477">可选。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-477">Optional.</span></span> <span data-ttu-id="e2dc8-478">在验证阶段之后停止执行包，而不实际运行包。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-478">Stops the execution of the package after the validatation phase, without actually running the package.</span></span> <span data-ttu-id="e2dc8-479">在验证过程中，使用 **/WarnAsError**选项会导致 `dtexec` 将警告视为错误，因此，如果在验证期间出现警告，包将失败。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-479">During validation, use of the **/WarnAsError** option causes `dtexec` to treat a warning as an error; therefore the package fails if a warning occurs during validation.</span></span>  
  
-   <span data-ttu-id="e2dc8-480">**/VerifyB [u) ]** _主编_[*; 小调*[*; build*]]：可选。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-480">**/VerifyB[uild]** _major_[*;minor*[*;build*]]: Optional.</span></span> <span data-ttu-id="e2dc8-481">根据验证阶段在 *major*、 *minor*和 *build* 参数中指定的内部版本号，验证包的内部版本号。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-481">Verifies the build number of a package against the build numbers that were specified during the verification phase in the *major*, *minor*, and *build* arguments.</span></span> <span data-ttu-id="e2dc8-482">如果出现不匹配，则将不执行包。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-482">If a mismatch occurs, the package will not execute.</span></span>  
  
     <span data-ttu-id="e2dc8-483">这些值是长整数。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-483">The values are long integers.</span></span> <span data-ttu-id="e2dc8-484">此参数可以使用以下三种格式之一，其中必须要有 *major* 的值：</span><span class="sxs-lookup"><span data-stu-id="e2dc8-484">The argument can have one of three forms, with a value for *major* always required:</span></span>  
  
    -   <span data-ttu-id="e2dc8-485">*major*</span><span class="sxs-lookup"><span data-stu-id="e2dc8-485">*major*</span></span>  
  
    -   <span data-ttu-id="e2dc8-486">*major*;*minor*</span><span class="sxs-lookup"><span data-stu-id="e2dc8-486">*major*;*minor*</span></span>  
  
    -   <span data-ttu-id="e2dc8-487">*major*; *minor*; *build*</span><span class="sxs-lookup"><span data-stu-id="e2dc8-487">*major*; *minor*; *build*</span></span>  
  
-   <span data-ttu-id="e2dc8-488">**/VerifyP[ackageID]** _packageID_：</span><span class="sxs-lookup"><span data-stu-id="e2dc8-488">**/VerifyP[ackageID]** _packageID_:</span></span>  
                  <span data-ttu-id="e2dc8-489">可选。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-489">Optional.</span></span> <span data-ttu-id="e2dc8-490">通过将要执行的包的 GUID 与 *package_id* 参数中指定的值进行比较，来验证该 GUID。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-490">Verifies the GUID of the package to be executed by comparing it to the value specified in the *package_id* argument.</span></span>  
  
-   <span data-ttu-id="e2dc8-491">**/VerifyS[igned]**：</span><span class="sxs-lookup"><span data-stu-id="e2dc8-491">**/VerifyS[igned]**:</span></span>  
                  <span data-ttu-id="e2dc8-492">可选。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-492">Optional.</span></span> <span data-ttu-id="e2dc8-493">导致 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 检查包的数字签名。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-493">Causes [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] to check the digital signature of the package.</span></span> <span data-ttu-id="e2dc8-494">如果包未签名或签名无效，则包将失败。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-494">If the package is not signed or the signature is not valid, the package fails.</span></span> <span data-ttu-id="e2dc8-495">有关详细信息，请参阅 [使用数字签名标识包的源](../security/identify-the-source-of-packages-with-digital-signatures.md)。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-495">For more information, see [Identify the Source of Packages with Digital Signatures](../security/identify-the-source-of-packages-with-digital-signatures.md).</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="e2dc8-496">在配置为检查包签名时， [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 仅检查数字签名是否存在、是否有效以及是否来自可信来源。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-496">When configured to check the signature of the package, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] only checks whether the digital signature is present, is valid, and is from a trusted source.</span></span> [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="e2dc8-497">不检查包是否已更改。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-497">does not check whether the package has been changed.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e2dc8-498">可选的**BlockedSignatureStates**注册表值可指定比在中 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] 或在命令行中设置的数字签名选项限制性更强的设置 `dtexec` 。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-498">The optional **BlockedSignatureStates** registry value can specify a setting that is more restrictive than the digital signature option set in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] or at the `dtexec` command line.</span></span> <span data-ttu-id="e2dc8-499">在这种情况下，限制性更强的注册表设置将覆盖其他设置。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-499">In this situation, the more restrictive registry setting overrides the other settings.</span></span>  
  
-   <span data-ttu-id="e2dc8-500">**/VerifyV [ersionID]** _versionID_：可选。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-500">**/VerifyV[ersionID]** _versionID_: Optional.</span></span> <span data-ttu-id="e2dc8-501">通过将要执行的包的版本 GUID 与包验证阶段 *version_id* 参数中指定的值进行比较，来验证该 GUID。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-501">Verifies the version GUID of a package to be executed by comparing it to the value specified in the *version_id* argument during package Validation Phase.</span></span>  
  
-   <span data-ttu-id="e2dc8-502">**/VLog** _[Filespec]_：可选。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-502">**/VLog** _[Filespec]_: Optional.</span></span> <span data-ttu-id="e2dc8-503">将所有 Integration Services 包事件写入设计包时已启用的日志提供程序。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-503">Writes all Integration Services package events to the log providers that were enabled when the package was designed.</span></span> <span data-ttu-id="e2dc8-504">若要让 Integration Services 启用文本文件的日志提供程序并将日志事件写入指定的文本文件，请将路径和文件名包括为 *Filespec* 参数。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-504">To have Integration Services enable a log provider for text files and write log events to a specified text file, include a path and file name as the *Filespec* parameter.</span></span>  
  
     <span data-ttu-id="e2dc8-505">如果不包括 *Filespec* 参数，Integration Services 将不会为文本文件启用日志提供程序。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-505">If you do not include the *Filespec* parameter, Integration Services will not enable a log provider for text files.</span></span> <span data-ttu-id="e2dc8-506">Integration Services 仅将日志事件写入设计包时已启用的日志提供程序。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-506">Integration Services will only write log events to the log providers that were enabled when the package was designed.</span></span>  
  
-   <span data-ttu-id="e2dc8-507">**/W [arnAsError]**：</span><span class="sxs-lookup"><span data-stu-id="e2dc8-507">**/W[arnAsError]**:</span></span>  
                  <span data-ttu-id="e2dc8-508">可选。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-508">Optional.</span></span> <span data-ttu-id="e2dc8-509">导致包将警告视为错误，使得包在验证期间出现警告时失败。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-509">Causes the package to consider a warning as an error; therefore, the package will fail if a warning occurs during validation.</span></span> <span data-ttu-id="e2dc8-510">如果验证期间无警告并且未指定 **/Validate** 选项，则执行包。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-510">If no warnings occur during validation and the **/Validate** option is not specified, the package is executed.</span></span>  
  
-   <span data-ttu-id="e2dc8-511">**/X86**：可选。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-511">**/X86**: Optional.</span></span> <span data-ttu-id="e2dc8-512">使 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理在 64 位计算机上以 32 位模式运行包。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-512">Causes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to run the package in 32-bit mode on a 64-bit computer.</span></span> <span data-ttu-id="e2dc8-513">满足下列条件时此选项由 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理设置：</span><span class="sxs-lookup"><span data-stu-id="e2dc8-513">This option is set by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent when the following conditions are true:</span></span>  
  
    -   <span data-ttu-id="e2dc8-514">作业步骤类型为 **“SQL Server Integration Services 包”** 。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-514">The job step type is **SQL Server Integration Services package**.</span></span>  
  
    -   <span data-ttu-id="e2dc8-515">**“新建作业步骤”** 对话框中 **“执行选项”** 选项卡上的 **“使用 32 位运行时”** 选项处于选中状态。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-515">The **Use 32 bit runtime** option on the **Execution options** tab of the **New Job Step** dialog box is selected.</span></span>  
  
     <span data-ttu-id="e2dc8-516">您也可通过使用存储过程或 SQL Server 管理对象 (SMO) 以编程方式创建此作业，从而为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理作业步骤设置此选项。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-516">You can also set this option for a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job step by using stored procedures or SQL Server Management Objects (SMO) to programmatically create the job.</span></span>  
  
     <span data-ttu-id="e2dc8-517">此选项仅由 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理使用。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-517">This option is only used by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span> <span data-ttu-id="e2dc8-518">如果在命令提示符下运行 `dtexec` 实用工具则会忽略此选项。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-518">This option is ignored if you run the `dtexec` utility at the command prompt.</span></span>  
  
##  <a name="remarks"></a><a name="remark"></a> <span data-ttu-id="e2dc8-519">注释</span><span class="sxs-lookup"><span data-stu-id="e2dc8-519">Remarks</span></span>  
 <span data-ttu-id="e2dc8-520">命令选项的指定顺序可以影响包的执行方式：</span><span class="sxs-lookup"><span data-stu-id="e2dc8-520">The order in which you specify command options can influence the way in which the package executes:</span></span>  
  
-   <span data-ttu-id="e2dc8-521">选项的处理顺序与其在命令行中出现的顺序一致。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-521">Options are processed in the order they are encountered on the command line.</span></span> <span data-ttu-id="e2dc8-522">命令文件的读取顺序与其在命令行中出现的顺序一致。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-522">Command files are read in as they are encountered on the command line.</span></span> <span data-ttu-id="e2dc8-523">命令文件中的命令的处理顺序也与其出现的顺序一致。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-523">The commands in the command file are also processed in the order they are encountered.</span></span>  
  
-   <span data-ttu-id="e2dc8-524">如果在同一个命令行语句中多次出现相同的选项、参数或变量，则优先执行该选项的最后一个实例。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-524">If the same option, parameter, or variable appears in the same command line statement more than one time, the last instance of the option takes precedence.</span></span>  
  
-   <span data-ttu-id="e2dc8-525">**/Set** 和 **/ConfigFile** 选项将按其出现的顺序进行处理。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-525">**/Set** and **/ConfigFile** options are processed in the order they are encountered.</span></span>  
  
##  <a name="examples"></a><a name="example"></a> <span data-ttu-id="e2dc8-526">示例</span><span class="sxs-lookup"><span data-stu-id="e2dc8-526">Examples</span></span>  
 <span data-ttu-id="e2dc8-527">下面的示例演示如何使用 `dtexec` 命令提示实用工具配置和执行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-527">The following examples demonstrate how to use the `dtexec` command prompt utility to configure and execute [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages.</span></span>  
  
 <span data-ttu-id="e2dc8-528">**“正在运行的包”**</span><span class="sxs-lookup"><span data-stu-id="e2dc8-528">**Running Packages**</span></span>  
  
 <span data-ttu-id="e2dc8-529">若要使用 Windows 身份验证执行保存到 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 包，可使用以下代码：</span><span class="sxs-lookup"><span data-stu-id="e2dc8-529">To execute an [!INCLUDE[ssIS](../../includes/ssis-md.md)] package saved to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using Windows Authentication, use the following code:</span></span>  
  
```  
dtexec /sq pkgOne /ser productionServer  
```  
  
 <span data-ttu-id="e2dc8-530">若要执行保存到 SSIS 包存储区的“文件系统”文件夹中的 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 包，请使用以下代码：</span><span class="sxs-lookup"><span data-stu-id="e2dc8-530">To execute an [!INCLUDE[ssIS](../../includes/ssis-md.md)] package saved to the File System folder in the SSIS Package Store, use the following code:</span></span>  
  
```  
dtexec /dts "\File System\MyPackage"  
```  
  
 <span data-ttu-id="e2dc8-531">若要验证使用 Windows 身份验证并保存在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中的包但不执行该包，可使用以下代码：</span><span class="sxs-lookup"><span data-stu-id="e2dc8-531">To validate a package that uses Windows Authentication and is saved in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] without executing the package, use the following code:</span></span>  
  
```  
dtexec /sq pkgOne /ser productionServer /va  
```  
  
 <span data-ttu-id="e2dc8-532">若要执行保存在文件系统中的 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 包，可使用以下代码：</span><span class="sxs-lookup"><span data-stu-id="e2dc8-532">To execute an [!INCLUDE[ssIS](../../includes/ssis-md.md)] package that is saved in the file system, use the following code:</span></span>  
  
```  
dtexec /f "c:\pkgOne.dtsx"   
```  
  
 <span data-ttu-id="e2dc8-533">若要执行保存在文件系统中的 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 包并指定日志选项，可使用以下代码：</span><span class="sxs-lookup"><span data-stu-id="e2dc8-533">To execute an [!INCLUDE[ssIS](../../includes/ssis-md.md)] package that is saved in the file system, and specify logging options, use the following code:</span></span>  
  
```  
dtexec /f "c:\pkgOne.dtsx" /l "DTS.LogProviderTextFile;c:\log.txt"  
```  
  
 <span data-ttu-id="e2dc8-534">若要执行使用 Windows 身份验证并保存至 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的默认本地实例的包，并在执行前查看其版本，可使用以下代码：</span><span class="sxs-lookup"><span data-stu-id="e2dc8-534">To execute a package that uses Windows Authentication and is saved to the default local instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], and verify the version before it is executed, use the following code:</span></span>  
  
```  
dtexec /sq pkgOne /verifyv {c200e360-38c5-11c5-11ce-ae62-08002b2b79ef}  
```  
  
 <span data-ttu-id="e2dc8-535">若要执行保存在文件系统中并在外部配置的 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 包，可使用以下代码：</span><span class="sxs-lookup"><span data-stu-id="e2dc8-535">To execute an [!INCLUDE[ssIS](../../includes/ssis-md.md)] package that is saved in the file system and configured externally, use the following code:</span></span>  
  
```  
dtexec /f "c:\pkgOne.dtsx" /conf "c:\pkgOneConfig.cfg"  
```  
  
> [!NOTE]  
>  <span data-ttu-id="e2dc8-536">如果路径或文件名包含空格，则 /SQL、/DTS 或 /FILE 选项的 *package_path* 或 *filespec* 参数必须用引号引起来。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-536">The *package_path* or *filespec* arguments of the /SQL, /DTS, or /FILE options must be enclosed in quotation marks if the path or file name contains a space.</span></span> <span data-ttu-id="e2dc8-537">如果没有使用引号将参数引起来，则该参数不能包含空格。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-537">If the argument is not enclosed in quotation marks, the argument cannot contain white space.</span></span>  
  
 <span data-ttu-id="e2dc8-538">**日志记录选项**</span><span class="sxs-lookup"><span data-stu-id="e2dc8-538">**Logging Option**</span></span>  
  
 <span data-ttu-id="e2dc8-539">如果有三种日志项类型 A、B 和 C，以下不带参数的 **ConsoleLog** 选项可以显示所有三种日志类型和所有字段：</span><span class="sxs-lookup"><span data-stu-id="e2dc8-539">If there are three log entry types of A, B, and C, the following **ConsoleLog** option without a parameter displays all three log types with all fields:</span></span>  
  
```  
/CONSOLELOG  
```  
  
 <span data-ttu-id="e2dc8-540">以下选项显示所有日志类型，但只显示 Name 和 Message 列：</span><span class="sxs-lookup"><span data-stu-id="e2dc8-540">The following option displays all log types, but with the Name and Message columns only:</span></span>  
  
```  
/CONSOLELOG NM  
```  
  
 <span data-ttu-id="e2dc8-541">以下选项仅显示日志项类型 A 的所有列：</span><span class="sxs-lookup"><span data-stu-id="e2dc8-541">The following option displays all columns, but only for log entry type A:</span></span>  
  
```  
/CONSOLELOG I;LogEntryTypeA  
```  
  
 <span data-ttu-id="e2dc8-542">以下选项仅显示日志项类型 A 的 Name 和 Message 列：</span><span class="sxs-lookup"><span data-stu-id="e2dc8-542">The following option displays only log entry type A, with Name and Message columns:</span></span>  
  
```  
/CONSOLELOG NM;I;LogEntryTypeA  
```  
  
 <span data-ttu-id="e2dc8-543">以下选项显示日志项类型 A 和 B 的日志项：</span><span class="sxs-lookup"><span data-stu-id="e2dc8-543">The following option displays log entries for log entry types A and B:</span></span>  
  
```  
/CONSOLELOG I;LogEntryTypeA;LogEntryTypeB  
```  
  
 <span data-ttu-id="e2dc8-544">可以使用多个 **ConsoleLog** 选项来获得相同的结果：</span><span class="sxs-lookup"><span data-stu-id="e2dc8-544">You can achieve the same results by using multiple **ConsoleLog** options:</span></span>  
  
```  
/CONSOLELOG I;LogEntryTypeA /CONSOLELOG I;LogEntryTypeB  
```  
  
 <span data-ttu-id="e2dc8-545">如果使用不带参数的 **ConsoleLog** 选项，将显示所有字段。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-545">If the **ConsoleLog** option is used without parameters, all fields are displayed.</span></span> <span data-ttu-id="e2dc8-546">包含 *list_options* 参数会导致以下示例仅显示日志项类型 A 和所有字段：</span><span class="sxs-lookup"><span data-stu-id="e2dc8-546">The inclusion of a *list_options* parameter causes the following to displays only log entry type A, with all fields:</span></span>  
  
```  
/CONSOLELOG NM;I;LogEntryTypeA /CONSOLELOG  
```  
  
 <span data-ttu-id="e2dc8-547">以下示例可以显示除日志项类型 A 以外的所有日志项，即显示日志项类型 B 和 C：</span><span class="sxs-lookup"><span data-stu-id="e2dc8-547">The following displays all log entries except log entry type A: that is, it displays log entry types B and C:</span></span>  
  
```  
/CONSOLELOG E;LogEntryTypeA  
```  
  
 <span data-ttu-id="e2dc8-548">以下示例使用了多个 **ConsoleLog** 选项和一个排除条件，但获得的结果是相同的：</span><span class="sxs-lookup"><span data-stu-id="e2dc8-548">The following example achieves the same results by using multiple **ConsoleLog** options and a single exclusion:</span></span>  
  
```  
/CONSOLELOG E;LogEntryTypeA /CONSOLELOG  
/CONSOLELOG E;LogEntryTypeA /CONSOLELOG E;LogEntryTypeA  
/CONSOLELOG E;LogEntryTypeA;LogEntryTypeA  
```  
  
 <span data-ttu-id="e2dc8-549">以下示例不显示日志消息，因为一个日志文件类型同时出现在包含列表和排除列表中时，该类型将被排除。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-549">The following example displays no log messages, because when a log file type is found in both the included and excluded lists, it will be excluded.</span></span>  
  
```  
/CONSOLELOG E;LogEntryTypeA /CONSOLELOG I;LogEntryTypeA  
```  
  
 <span data-ttu-id="e2dc8-550">**SET 选项**</span><span class="sxs-lookup"><span data-stu-id="e2dc8-550">**SET Option**</span></span>  
  
 <span data-ttu-id="e2dc8-551">以下示例显示如何使用 **/SET** 选项。从命令行启动包时，使用该选项可以更改任何包属性或变量的值。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-551">The following example shows how to use the **/SET** option, which lets you change the value of any package property or variable when you start the package from the command line.</span></span>  
  
```  
/SET \package\DataFlowTask.Variables[User::MyVariable].Value;newValue  
```  
  
 <span data-ttu-id="e2dc8-552">**项目选项**</span><span class="sxs-lookup"><span data-stu-id="e2dc8-552">**Project Option**</span></span>  
  
 <span data-ttu-id="e2dc8-553">以下示例显示如何使用 `/Project` 和 `/Package` 选项。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-553">The following example shows how to use the `/Project` and the `/Package` option.</span></span>  
  
```  
/Project c:\project.ispac /Package Package1.dtsx  
```  
  
 <span data-ttu-id="e2dc8-554">以下示例显示如何使用 `/Project` 和 `/Package` 选项并设置包参数和项目参数。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-554">The following example shows how to use the `/Project` and `/Package` options, and set package and project parameters.</span></span>  
  
```  
/Project c:\project.ispac /Package Package1.dtsx /SET \Package.Variables[$Package::Parameter];1 /SET \Package.Variables[$Project::Parameter];1  
  
```  
  
 <span data-ttu-id="e2dc8-555">**ISServer 选项**</span><span class="sxs-lookup"><span data-stu-id="e2dc8-555">**ISServer Option**</span></span>  
  
 <span data-ttu-id="e2dc8-556">以下示例显示如何使用 `/ISServer` 选项。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-556">The following example shows how to use the `/ISServer` option.</span></span>  
  
```  
dtexec /isserver "\SSISDB\MyFolder\MyProject\MyPackage.dtsx" /server "."  
```  
  
 <span data-ttu-id="e2dc8-557">以下示例显示如何使用 `/ISServer` 选项并设置项目参数和连接管理器参数。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-557">The following example shows how to use the `/ISServer` option and set project and connection manager parameters.</span></span>  
  
```  
/Server localhost /ISServer "\SSISDB\MyFolder\Integration Services Project1\Package.dtsx" /Par "$Project::ProjectParameter(Int32)";1 /Par "CM.SourceServer.InitialCatalog";SourceDB  
  
```  
  
## <a name="related-tasks"></a><span data-ttu-id="e2dc8-558">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="e2dc8-558">Related Tasks</span></span>  
 [<span data-ttu-id="e2dc8-559">在 SQL Server Data Tools 中运行包</span><span class="sxs-lookup"><span data-stu-id="e2dc8-559">Run a Package in SQL Server Data Tools</span></span>](../run-a-package-in-sql-server-data-tools.md)  
  
## <a name="related-content"></a><span data-ttu-id="e2dc8-560">相关内容</span><span class="sxs-lookup"><span data-stu-id="e2dc8-560">Related Content</span></span>  
 <span data-ttu-id="e2dc8-561">[www.mattmasson.com](www.mattmasson.com) 上的博客文章 [退出代码、DTEXEC 和 SSIS 目录](https://www.mattmasson.com/2012/02/exit-codes-dtexec-and-ssis-catalog/)。</span><span class="sxs-lookup"><span data-stu-id="e2dc8-561">Blog entry, [Exit Codes, DTEXEC, and SSIS Catalog](https://www.mattmasson.com/2012/02/exit-codes-dtexec-and-ssis-catalog/), on www.mattmasson.com.</span></span>  
  
  
