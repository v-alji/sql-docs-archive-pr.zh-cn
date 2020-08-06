---
title: sqlps 实用工具 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- sqlps utility
- PowerShell [SQL Server], sqlps utility
ms.assetid: 4b2515a6-12c3-44fb-b263-1c567681cd2b
author: stevestein
ms.author: sstein
ms.openlocfilehash: b445366b3fb99ad4beebdf7b203ada77afe90c8d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682476"
---
# <a name="sqlps-utility"></a><span data-ttu-id="b5103-102">sqlps 实用工具</span><span class="sxs-lookup"><span data-stu-id="b5103-102">sqlps Utility</span></span>
  <span data-ttu-id="b5103-103">`sqlps` 实用工具会启动一个 Windows PowerShell 2.0 会话，并加载和注册 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell 提供程序和 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b5103-103">The `sqlps` utility starts a Windows PowerShell 2.0 session with the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell provider and cmdlets loaded and registered.</span></span> <span data-ttu-id="b5103-104">您可以输入 PowerShell 命令或脚本，它们使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell 组件来处理 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的实例及其对象。</span><span class="sxs-lookup"><span data-stu-id="b5103-104">You can enter PowerShell commands or scripts that use the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell components to work with instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] and their objects.</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../includes/ssnotedepfutureavoid-md.md)]<span data-ttu-id="b5103-105">请改用 `sqlps` PowerShell 模块。</span><span class="sxs-lookup"><span data-stu-id="b5103-105">Use the `sqlps` PowerShell module instead.</span></span> <span data-ttu-id="b5103-106">有关模块的详细信息 `sqlps` ，请参阅[导入 SQLPS 模块](../database-engine/import-the-sqlps-module.md)。</span><span class="sxs-lookup"><span data-stu-id="b5103-106">For more information about the `sqlps` module, see [Import the SQLPS Module](../database-engine/import-the-sqlps-module.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5103-107">语法</span><span class="sxs-lookup"><span data-stu-id="b5103-107">Syntax</span></span>  
  
```  
  
      sqlps   
[ [ [ -NoLogo ][ -NoExit ][ -NoProfile ]  
    [ -OutPutFormat { Text | XML } ] [ -InPutFormat { Text | XML } ]  
  ]  
  [ -Command { -  
             | script_block [ -argsargument_array ]  
             | string [ command_parameters ]  
             }  
  ]  
]  
[ -? | -Help ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="b5103-108">参数</span><span class="sxs-lookup"><span data-stu-id="b5103-108">Arguments</span></span>  
 <span data-ttu-id="b5103-109">**-NoLogo**</span><span class="sxs-lookup"><span data-stu-id="b5103-109">**-NoLogo**</span></span>  
 <span data-ttu-id="b5103-110">指定 `sqlps` 实用工具在启动时隐藏版权标志。</span><span class="sxs-lookup"><span data-stu-id="b5103-110">Specifies that the `sqlps` utility hide the copyright banner when it starts.</span></span>  
  
 <span data-ttu-id="b5103-111">**-NoExit**</span><span class="sxs-lookup"><span data-stu-id="b5103-111">**-NoExit**</span></span>  
 <span data-ttu-id="b5103-112">指定 `sqlps` 实用工具在完成启动命令后仍继续运行。</span><span class="sxs-lookup"><span data-stu-id="b5103-112">Specifies that the `sqlps` utility continue running after the startup commands have completed.</span></span>  
  
 <span data-ttu-id="b5103-113">**-NoProfile**</span><span class="sxs-lookup"><span data-stu-id="b5103-113">**-NoProfile**</span></span>  
 <span data-ttu-id="b5103-114">指定 `sqlps` 实用工具不加载用户配置文件。</span><span class="sxs-lookup"><span data-stu-id="b5103-114">Specifies that the `sqlps` utility not load a user profile.</span></span> <span data-ttu-id="b5103-115">用户配置文件记录 PowerShell 会话期间常用的别名、函数和变量。</span><span class="sxs-lookup"><span data-stu-id="b5103-115">User profiles record commonly used aliases, functions, and variables for use across PowerShell sessions.</span></span>  
  
 <span data-ttu-id="b5103-116">**-OutPutFormat** { **Text** | **XML** }</span><span class="sxs-lookup"><span data-stu-id="b5103-116">**-OutPutFormat** { **Text** | **XML** }</span></span>  
 <span data-ttu-id="b5103-117">指定将 `sqlps` 实用工具输出的格式设置为文本字符串 (**文本**) 或 (**XML**) 的序列化的 export-clixml 格式。</span><span class="sxs-lookup"><span data-stu-id="b5103-117">Specifies that the `sqlps` utility output be formatted as either text strings (**Text**) or in a serialized CLIXML format (**XML**).</span></span>  
  
 <span data-ttu-id="b5103-118">**-InPutFormat** { **Text** | **XML** }</span><span class="sxs-lookup"><span data-stu-id="b5103-118">**-InPutFormat** { **Text** | **XML** }</span></span>  
 <span data-ttu-id="b5103-119">指定对实用工具的输入 `sqlps` (**文本**格式设置为文本字符串) 或 (**XML**) 以序列化的 export-clixml 格式。</span><span class="sxs-lookup"><span data-stu-id="b5103-119">Specifies that input to the `sqlps` utility is formatted as either text strings (**Text**) or in a serialized CLIXML format (**XML**).</span></span>  
  
 <span data-ttu-id="b5103-120">**-Command**</span><span class="sxs-lookup"><span data-stu-id="b5103-120">**-Command**</span></span>  
 <span data-ttu-id="b5103-121">指定要使 `sqlps` 实用工具运行的命令。</span><span class="sxs-lookup"><span data-stu-id="b5103-121">Specifies the command for the `sqlps` utility to run.</span></span> <span data-ttu-id="b5103-122">`sqlps`实用工具运行命令，然后退出，除非也指定了 **-NoExit** 。</span><span class="sxs-lookup"><span data-stu-id="b5103-122">The `sqlps` utility runs the command and then exits, unless **-NoExit** is also specified.</span></span> <span data-ttu-id="b5103-123">请不要在 **-Command**后指定任何其他开关，如果指定，它们将被读作命令参数。</span><span class="sxs-lookup"><span data-stu-id="b5103-123">Do not specify any other switches after **-Command**, they will be read as command parameters.</span></span>  
  
 **-**  
 <span data-ttu-id="b5103-124">**-Command-** 指定 `sqlps` 实用工具从标准输入读取输入。</span><span class="sxs-lookup"><span data-stu-id="b5103-124">**-Command-** specifies that the `sqlps` utility read the input from the standard input.</span></span>  
  
 <span data-ttu-id="b5103-125">*script_block* [ **-args**_argument_array_ ]</span><span class="sxs-lookup"><span data-stu-id="b5103-125">*script_block* [ **-args**_argument_array_ ]</span></span>  
 <span data-ttu-id="b5103-126">指定要运行的 PowerShell 命令块，块必须用大括号 {} 括起来。</span><span class="sxs-lookup"><span data-stu-id="b5103-126">Specifies a block of PowerShell commands to run, the block must be enclosed in braces: {}.</span></span> <span data-ttu-id="b5103-127">*Script_block*仅当 `sqlps` 从**PowerShell**或其他实用工具会话调用实用工具时，才能指定 Script_block `sqlps` 。</span><span class="sxs-lookup"><span data-stu-id="b5103-127">*Script_block* can only be specified when the `sqlps` utility is called from either **PowerShell** or another `sqlps` utility session.</span></span> <span data-ttu-id="b5103-128">*Argument_array* 是 PowerShell 变量的数组，包含 *script_block*中 PowerShell 命令的参数。</span><span class="sxs-lookup"><span data-stu-id="b5103-128">The *argument_array* is an array of PowerShell variables containing the arguments for the PowerShell commands in the *script_block*.</span></span>  
  
 <span data-ttu-id="b5103-129">*字符串* [ *command_parameters* ]</span><span class="sxs-lookup"><span data-stu-id="b5103-129">*string* [ *command_parameters* ]</span></span>  
 <span data-ttu-id="b5103-130">指定包含要运行的 PowerShell 命令的字符串。</span><span class="sxs-lookup"><span data-stu-id="b5103-130">Specifies a string that contains the PowerShell commands to be run.</span></span> <span data-ttu-id="b5103-131">使用 **"& { *`command`* }"** 格式。</span><span class="sxs-lookup"><span data-stu-id="b5103-131">Use the format **"&{*`command`*}"**.</span></span> <span data-ttu-id="b5103-132">引号指示一个字符串，调用运算符 ( # A0) 使 `sqlps` 实用工具运行该命令。</span><span class="sxs-lookup"><span data-stu-id="b5103-132">The quotation marks indicate a string, and the invoke operator (&) causes the `sqlps` utility to run the command.</span></span>  
  
 <span data-ttu-id="b5103-133">[ **-?**</span><span class="sxs-lookup"><span data-stu-id="b5103-133">[ **-?**</span></span><span data-ttu-id="b5103-134"> |  **-Help** ]</span><span class="sxs-lookup"><span data-stu-id="b5103-134"> | **-Help** ]</span></span>  
 <span data-ttu-id="b5103-135">显示 `sqlps` 实用工具选项的语法摘要。</span><span class="sxs-lookup"><span data-stu-id="b5103-135">Shows the syntax summary of the `sqlps` utility options.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b5103-136">备注</span><span class="sxs-lookup"><span data-stu-id="b5103-136">Remarks</span></span>  
 <span data-ttu-id="b5103-137">`sqlps`实用工具启动 powershell 环境 ( # A0) 并加载 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] powershell 模块。</span><span class="sxs-lookup"><span data-stu-id="b5103-137">The `sqlps` utility starts the PowerShell environment (PowerShell.exe) and loads the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell module.</span></span> <span data-ttu-id="b5103-138">该模块（也称为 `sqlps` ）将加载并注册以下 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell 管理单元：</span><span class="sxs-lookup"><span data-stu-id="b5103-138">The module, also named `sqlps`, loads and registers these [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell snap-ins:</span></span>  
  
-   <span data-ttu-id="b5103-139">Microsoft.SqlServer.Management.PSProvider.dll</span><span class="sxs-lookup"><span data-stu-id="b5103-139">Microsoft.SqlServer.Management.PSProvider.dll</span></span>  
  
     <span data-ttu-id="b5103-140">实现 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell 提供程序和关联的 cmdlets，如 **Encode-SqlName** 和 **Decode-SqlName**。</span><span class="sxs-lookup"><span data-stu-id="b5103-140">Implements the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell provider and associated cmdlets such as **Encode-SqlName** and **Decode-SqlName**.</span></span>  
  
-   <span data-ttu-id="b5103-141">Microsoft.SqlServer.Management.PSSnapin.dll</span><span class="sxs-lookup"><span data-stu-id="b5103-141">Microsoft.SqlServer.Management.PSSnapin.dll</span></span>  
  
     <span data-ttu-id="b5103-142">实现 **Invoke-Sqlcmd** 和 **Invoke-PolicyEvaluation** cmdlets。</span><span class="sxs-lookup"><span data-stu-id="b5103-142">Implements the **Invoke-Sqlcmd** and **Invoke-PolicyEvaluation** cmdlets.</span></span>  
  
 <span data-ttu-id="b5103-143">可以使用 `sqlps` 实用工具执行下列操作：</span><span class="sxs-lookup"><span data-stu-id="b5103-143">You can use the `sqlps` utility to do the following:</span></span>  
  
-   <span data-ttu-id="b5103-144">以交互方式运行 PowerShell 命令。</span><span class="sxs-lookup"><span data-stu-id="b5103-144">Interactively run PowerShell commands.</span></span>  
  
-   <span data-ttu-id="b5103-145">运行 PowerShell 脚本文件。</span><span class="sxs-lookup"><span data-stu-id="b5103-145">Run PowerShell script files.</span></span>  
  
-   <span data-ttu-id="b5103-146">运行 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b5103-146">Run [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] cmdlets.</span></span>  
  
-   <span data-ttu-id="b5103-147">使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 提供程序路径可以浏览 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 对象的层次结构。</span><span class="sxs-lookup"><span data-stu-id="b5103-147">Use the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] provider paths to navigate through the hierarchy of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] objects.</span></span>  
  
 <span data-ttu-id="b5103-148">默认情况下， `sqlps` 实用工具运行时将脚本执行策略设置为 "**受限**"。</span><span class="sxs-lookup"><span data-stu-id="b5103-148">By default, the `sqlps` utility runs with the scripting execution policy set to **Restricted**.</span></span> <span data-ttu-id="b5103-149">这样可以防止运行任何 PowerShell 脚本。</span><span class="sxs-lookup"><span data-stu-id="b5103-149">This prevents running any PowerShell scripts.</span></span> <span data-ttu-id="b5103-150">可以使用 **Set-ExecutionPolicy** cmdlet 来启用运行签名的脚本或任意脚本。</span><span class="sxs-lookup"><span data-stu-id="b5103-150">You can use the **Set-ExecutionPolicy** cmdlet to enable running signed scripts, or any scripts.</span></span> <span data-ttu-id="b5103-151">请仅运行来自受信任源的脚本，并通过使用适当的 NTFS 权限来保证所有输入和输出文件的安全。</span><span class="sxs-lookup"><span data-stu-id="b5103-151">Only run scripts from trusted sources, and secure all input and output files by using the appropriate NTFS permissions.</span></span> <span data-ttu-id="b5103-152">有关启用 PowerShell 脚本的详细信息，请参阅 [Running Windows PowerShell Scripts](https://www.tech-recipes.com/rx/2513/powershell_enable_script_support/)（运行 Windows PowerShell 脚本）。</span><span class="sxs-lookup"><span data-stu-id="b5103-152">For more information about enabling PowerShell scripts, see [Running Windows PowerShell Scripts](https://www.tech-recipes.com/rx/2513/powershell_enable_script_support/).</span></span>  
  
 <span data-ttu-id="b5103-153">在 [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] 和 [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] 中，此 `sqlps` 实用工具版本已作为 Windows PowerShell 1.0 微型 shell 实现。</span><span class="sxs-lookup"><span data-stu-id="b5103-153">The version of the `sqlps` utility in [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] and [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] was implemented as a Windows PowerShell 1.0 mini-shell.</span></span> <span data-ttu-id="b5103-154">微型外壳程序具有某些限制，例如不允许用户加载不是由微型外壳程序所加载的管理单元。</span><span class="sxs-lookup"><span data-stu-id="b5103-154">Mini-shells have certain restrictions, such as not allowing users to load snap-ins other than those loaded by the mini-shell.</span></span> <span data-ttu-id="b5103-155">这些限制并不适用于 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] 版本及更高的版本的实用工具，这些版本已更改为使用 `sqlps` 模块。</span><span class="sxs-lookup"><span data-stu-id="b5103-155">These restrictions do not apply to the [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] and higher versions of the utility, which have been changed to use the `sqlps` module.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="b5103-156">示例</span><span class="sxs-lookup"><span data-stu-id="b5103-156">Examples</span></span>  

### <a name="a-run-the-sqlps-utility-in-default-interactive-mode-without-the-copyright-banner"></a><span data-ttu-id="b5103-157">A.</span><span class="sxs-lookup"><span data-stu-id="b5103-157">A.</span></span> <span data-ttu-id="b5103-158">以默认的交互模式运行 sqlps 实用工具，不显示版权标志</span><span class="sxs-lookup"><span data-stu-id="b5103-158">Run the sqlps utility in default, interactive mode without the copyright banner</span></span>
  
```cmd
sqlps -NoLogo  
```  
  
### <a name="b-run-a-sql-server-powershell-script-from-the-command-prompt"></a><span data-ttu-id="b5103-159">B.</span><span class="sxs-lookup"><span data-stu-id="b5103-159">B.</span></span> <span data-ttu-id="b5103-160">从命令提示符下运行 SQL Server PowerShell 脚本</span><span class="sxs-lookup"><span data-stu-id="b5103-160">Run a SQL Server PowerShell script from the command prompt</span></span>
  
```cmd
sqlps -Command "&{.\MyFolder.MyScript.ps1}"  
```  
  
### <a name="c-run-a-sql-server-powershell-script-from-the-command-prompt-and-keep-running-after-the-script-completes"></a><span data-ttu-id="b5103-161">C.</span><span class="sxs-lookup"><span data-stu-id="b5103-161">C.</span></span> <span data-ttu-id="b5103-162">从命令提示符下运行 SQL Server PowerShell 脚本，并在脚本完成后继续运行</span><span class="sxs-lookup"><span data-stu-id="b5103-162">Run a SQL Server PowerShell script from the command prompt, and keep running after the script completes</span></span>
  
```cmd
sqlps -NoExit -Command "&{.\MyFolder.MyScript.ps1}"  
```  
  
## <a name="see-also"></a><span data-ttu-id="b5103-163">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b5103-163">See Also</span></span>  
 <span data-ttu-id="b5103-164">[启用或禁用服务器网络协议](../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md) </span><span class="sxs-lookup"><span data-stu-id="b5103-164">[Enable or Disable a Server Network Protocol](../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md) </span></span>  
 [<span data-ttu-id="b5103-165">SQL Server PowerShell</span><span class="sxs-lookup"><span data-stu-id="b5103-165">SQL Server PowerShell</span></span>](../powershell/sql-server-powershell.md)  
