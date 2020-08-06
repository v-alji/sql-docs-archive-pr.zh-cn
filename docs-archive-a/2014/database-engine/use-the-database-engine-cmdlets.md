---
title: 使用数据库引擎 cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Cmdlets [SQL Server], Encode-Sqlname
- Encode-Sqlname cmdlet
- PowerShell [SQL Server], Encode-Sqlname
- Convert-UrnToPath cmdlet
- PowerShell [SQL Server], cmdlets
- Cmdlets [SQL Server]
- PowerShell [SQL Server], Convert-UrnToPath
- Cmdlets [SQL Server], Convert-UrnToPath
- Decode-Sqlname cmdlet
- PowerShell [SQL Server], Decode-Sqlname
- Cmdlets [SQL Server], Decode-Sqlname
ms.assetid: 720aa982-09ae-41a3-b603-a91004cfbe3e
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 015500c7c985f9f1a1d190954406844f3b184932
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577787"
---
# <a name="use-the-database-engine-cmdlets"></a><span data-ttu-id="f4748-102">使用数据库引擎 cmdlet</span><span class="sxs-lookup"><span data-stu-id="f4748-102">Use the Database Engine cmdlets</span></span>
  <span data-ttu-id="f4748-103">Windows PowerShell cmdlet 是单函数命令，通常采用“动词-名词”形式的命名约定，如 **Get-Help** 或 **Set-MachineName**。</span><span class="sxs-lookup"><span data-stu-id="f4748-103">Windows PowerShell cmdlets are single-function commands that typically have a verb-noun naming convention, such as **Get-Help** or **Set-MachineName**.</span></span> <span data-ttu-id="f4748-104">用于 Windows PowerShell 的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 提供程序提供特定于 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="f4748-104">The [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] provider for Windows PowerShell supplies cmdlets specific to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="database-engine-cmdlets"></a><span data-ttu-id="f4748-105">数据库引擎 cmdlet</span><span class="sxs-lookup"><span data-stu-id="f4748-105">Database Engine cmdlets</span></span>  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="f4748-106">实现了一小部分用于 [!INCLUDE[ssDE](../includes/ssde-md.md)]的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="f4748-106">implements a small number of cmdlets for the [!INCLUDE[ssDE](../includes/ssde-md.md)].</span></span> <span data-ttu-id="f4748-107">这些 cmdlet 主要用于从新的 PowerShell 脚本运行现有的 Transact-SQL 脚本，评估基于策略的管理策略并帮助在 SQL Server 提供程序路径中指定 SQL Server 标识符。</span><span class="sxs-lookup"><span data-stu-id="f4748-107">These cmdlets are primarily used to run existing Transact-SQL scripts from new PowerShell scripts, evaluate policy-based management policies, and aid in specifying SQL Server identifiers in SQL Server Provider paths.</span></span>  
  
 <span data-ttu-id="f4748-108">用于 [!INCLUDE[ssDE](../includes/ssde-md.md)] 的大多数 Windows PowerShell 脚本通过使用 SQL Server PowerShell 提供程序和 SQL Server 可管理性对象模型。</span><span class="sxs-lookup"><span data-stu-id="f4748-108">Most Windows PowerShell scripts work with the [!INCLUDE[ssDE](../includes/ssde-md.md)] by using the SQL Server PowerShell provider and the SQL Server manageability object models.</span></span> <span data-ttu-id="f4748-109">有关详细信息，请参阅 [SQL Server PowerShell](../powershell/sql-server-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="f4748-109">For more information, see [SQL Server PowerShell](../powershell/sql-server-powershell.md).</span></span>  
  
### <a name="get-cmdlet-help"></a><span data-ttu-id="f4748-110">获取 Cmdlet 帮助</span><span class="sxs-lookup"><span data-stu-id="f4748-110">Get Cmdlet Help</span></span>  
 <span data-ttu-id="f4748-111">在 Windows PowerShell 环境中， **Get-Help** cmdlet 提供了每个 cmdlet 的帮助信息。</span><span class="sxs-lookup"><span data-stu-id="f4748-111">In the Windows PowerShell environment, the **Get-Help** cmdlet provides help information for each cmdlet.</span></span> <span data-ttu-id="f4748-112">**Get-Help** 返回各种信息，如语法、参数定义、输入和输出类型以及 cmdlet 所执行操作的说明。</span><span class="sxs-lookup"><span data-stu-id="f4748-112">**Get-Help** returns information such as the syntax, parameter definitions, input and output types, and a description of the action performed by the cmdlet.</span></span> <span data-ttu-id="f4748-113">有关详细信息，请参阅 [Get Help SQL Server PowerShell](../../2014/database-engine/get-help-sql-server-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="f4748-113">For more information, see [Get Help SQL Server PowerShell](../../2014/database-engine/get-help-sql-server-powershell.md).</span></span>  
  
### <a name="partial-parameter-names"></a><span data-ttu-id="f4748-114">部分参数名称</span><span class="sxs-lookup"><span data-stu-id="f4748-114">Partial Parameter Names</span></span>  
 <span data-ttu-id="f4748-115">不需要指定 cmdlet 参数的完整名称。</span><span class="sxs-lookup"><span data-stu-id="f4748-115">You do not have to specify the entire name of a cmdlet parameter.</span></span> <span data-ttu-id="f4748-116">您只需指定该名称的一部分，以便能够将其与 cmdlet 支持的其他参数区分开。</span><span class="sxs-lookup"><span data-stu-id="f4748-116">You only have to specify enough of the name to uniquely separate it from the other parameters that are supported by the cmdlet.</span></span> <span data-ttu-id="f4748-117">例如，这些示例说明指定 **Invoke-Sqlcmd -QueryTimeout** 参数的三种方式：</span><span class="sxs-lookup"><span data-stu-id="f4748-117">For example, these examples show three ways of specifying the **Invoke-Sqlcmd -QueryTimeout** parameter:</span></span>  
  
```powershell
Invoke-Sqlcmd -Query "SELECT @@VERSION;" -QueryTimeout 3  
Invoke-Sqlcmd -Query "SELECT @@VERSION;" -QueryTime 3  
Invoke-Sqlcmd -Query "SELECT @@VERSION;" -QueryT 3  
```  
  
## <a name="database-engine-cmdlet-tasks"></a><span data-ttu-id="f4748-118">数据库引擎 cmdlet 任务</span><span class="sxs-lookup"><span data-stu-id="f4748-118">Database Engine cmdlet Tasks</span></span>  
  
|<span data-ttu-id="f4748-119">任务说明</span><span class="sxs-lookup"><span data-stu-id="f4748-119">Task Description</span></span>|<span data-ttu-id="f4748-120">主题</span><span class="sxs-lookup"><span data-stu-id="f4748-120">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="f4748-121">介绍使用 **Invoke-Sqlcmd** 运行包含 **或 XQuery 语句的** sqlcmd [!INCLUDE[tsql](../includes/tsql-md.md)] 脚本或命令。</span><span class="sxs-lookup"><span data-stu-id="f4748-121">Describes using **Invoke-Sqlcmd** to run **sqlcmd** scripts or commands that contain [!INCLUDE[tsql](../includes/tsql-md.md)] or XQuery statements.</span></span> <span data-ttu-id="f4748-122">它可以接受 **sqlcmd** 输入作为字符串输入参数或要打开的脚本文件的文件名。</span><span class="sxs-lookup"><span data-stu-id="f4748-122">It can accept the **sqlcmd** input as either a character string input parameter, or as the name of a script file to open.</span></span>|[<span data-ttu-id="f4748-123">Invoke-Sqlcmd cmdlet</span><span class="sxs-lookup"><span data-stu-id="f4748-123">Invoke-Sqlcmd cmdlet</span></span>](../../2014/database-engine/invoke-sqlcmd-cmdlet.md)|  
|<span data-ttu-id="f4748-124">介绍使用 **Invoke-PolicyEvaluation** 报告 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 对象的目标集是否符合基于策略的管理策略中定义的条件。</span><span class="sxs-lookup"><span data-stu-id="f4748-124">Describes using **Invoke-PolicyEvaluation** to report whether a target set of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] objects comply with the conditions that are defined in policy-based management policies.</span></span> <span data-ttu-id="f4748-125">可以选择使用 cmdlet 对不符合策略条件的目标对象中的任何可设置选项进行重新配置。</span><span class="sxs-lookup"><span data-stu-id="f4748-125">Optionally, the cmdlet can be used to reconfigure any settable options in the target objects that do not comply with the policy conditions.</span></span>|[<span data-ttu-id="f4748-126">Invoke-PolicyEvaluation cmdlet</span><span class="sxs-lookup"><span data-stu-id="f4748-126">Invoke-PolicyEvaluation cmdlet</span></span>](../../2014/database-engine/invoke-policyevaluation-cmdlet.md)|  
|<span data-ttu-id="f4748-127">介绍使用 `Encode-Sqlname` 和 `Decode-Sqlname` 处理包含 Windows PowerShell 路径中不支持的字符的 SQL Server 标识符。</span><span class="sxs-lookup"><span data-stu-id="f4748-127">Describes using `Encode-Sqlname` and `Decode-Sqlname` to handle SQL Server identifiers that contain characters not supported in Windows PowerShell paths.</span></span>|[<span data-ttu-id="f4748-128">对 SQL Server 标识符进行编码和解码</span><span class="sxs-lookup"><span data-stu-id="f4748-128">Encode and Decode SQL Server Identifiers</span></span>](../powershell/encode-and-decode-sql-server-identifiers.md)|  
|<span data-ttu-id="f4748-129">介绍使用 `Convert-UrnToPath` 将 SQL Server 可管理性对象统一资源名称 (URN) 转换为等价的 SQL Server 提供程序路径。</span><span class="sxs-lookup"><span data-stu-id="f4748-129">Describes using `Convert-UrnToPath` to convert a SQL Server Manageability Object Uniform Resource Name (URN) to the equivalent SQL Server Provider path.</span></span>|[<span data-ttu-id="f4748-130">将 URN 转换为 SQL Server 提供程序路径</span><span class="sxs-lookup"><span data-stu-id="f4748-130">Convert URNs to SQL Server Provider Paths</span></span>](../../2014/database-engine/convert-urns-to-sql-server-provider-paths.md)|  
  
## <a name="see-also"></a><span data-ttu-id="f4748-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f4748-131">See Also</span></span>  
 <span data-ttu-id="f4748-132">[SQL Server PowerShell 提供程序](../powershell/sql-server-powershell-provider.md) </span><span class="sxs-lookup"><span data-stu-id="f4748-132">[SQL Server PowerShell Provider](../powershell/sql-server-powershell-provider.md) </span></span>  
 <span data-ttu-id="f4748-133">[SQL Server PowerShell](../powershell/sql-server-powershell.md) </span><span class="sxs-lookup"><span data-stu-id="f4748-133">[SQL Server PowerShell](../powershell/sql-server-powershell.md) </span></span>  
 [<span data-ttu-id="f4748-134">适用于 AlwaysOn 可用性组 &#40;SQL Server 的 PowerShell Cmdlet 概述&#41;</span><span class="sxs-lookup"><span data-stu-id="f4748-134">Overview of PowerShell Cmdlets for AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](availability-groups/windows/overview-of-powershell-cmdlets-for-always-on-availability-groups-sql-server.md)  
  
  
