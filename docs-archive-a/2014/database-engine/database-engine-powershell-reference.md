---
title: 数据库引擎 PowerShell 参考 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 3c379a43-c497-47dd-8e7d-2b015c068bb7
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 2d72f9fcedee02e475369c32a7c263578c9ff156
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587582"
---
# <a name="database-engine-powershell-reference"></a><span data-ttu-id="70367-102">数据库引擎 PowerShell 参考</span><span class="sxs-lookup"><span data-stu-id="70367-102">Database Engine PowerShell Reference</span></span>
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="70367-103">包含一组 Windows PowerShell 2.0 cmdlet，用于在[!INCLUDE[ssDE](../includes/ssde-md.md)]中执行常见操作。</span><span class="sxs-lookup"><span data-stu-id="70367-103">includes a set of Windows PowerShell 2.0 cmdlets for performing common actions in the [!INCLUDE[ssDE](../includes/ssde-md.md)].</span></span> <span data-ttu-id="70367-104">此外，查询表达式和统一资源名称 (URN) 可以转换为 SQL Server PowerShell 路径，或用于指定 [!INCLUDE[ssDE](../includes/ssde-md.md)]中的一个或多个对象。</span><span class="sxs-lookup"><span data-stu-id="70367-104">In addition, Query Expressions and Uniform Resource Names (URN) can be converted to SQL Server PowerShell paths, or used to specify one or more objects in the [!INCLUDE[ssDE](../includes/ssde-md.md)].</span></span>  
  
## <a name="database-engine-cmdlets"></a><span data-ttu-id="70367-105">数据库引擎 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="70367-105">Database Engine Cmdlets</span></span>  
 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] <span data-ttu-id="70367-106">包含相对较少的用于 [!INCLUDE[ssDE](../includes/ssde-md.md)]的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="70367-106">includes relatively few cmdlets for the [!INCLUDE[ssDE](../includes/ssde-md.md)].</span></span> <span data-ttu-id="70367-107">大多数用于 [!INCLUDE[ssDE](../includes/ssde-md.md)] 的 PowerShell 脚本使用 SQL Server PowerShell 提供程序和可管理性对象模型。</span><span class="sxs-lookup"><span data-stu-id="70367-107">Most PowerShell scripts working with the [!INCLUDE[ssDE](../includes/ssde-md.md)] use the SQL Server PowerShell provider and the manageability object models.</span></span> <span data-ttu-id="70367-108">有关详细信息，请参阅 [SQL Server PowerShell Provider](../powershell/sql-server-powershell-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="70367-108">For more information, see [SQL Server PowerShell Provider](../powershell/sql-server-powershell-provider.md).</span></span>  
  
 <span data-ttu-id="70367-109">要了解如何获取有关 Windows PowerShell 环境中的 SQL Server cmdlet 的帮助，请参阅 [Get Help SQL Server PowerShell](../powershell/sql-server-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="70367-109">To learn how to get help about the SQL Server cmdlets in a Windows PowerShell environment, see [Get Help SQL Server PowerShell](../powershell/sql-server-powershell.md).</span></span>  
  
### <a name="in-this-section"></a><span data-ttu-id="70367-110">本节内容</span><span class="sxs-lookup"><span data-stu-id="70367-110">In This Section</span></span>  
 <span data-ttu-id="70367-111">本节包含有关这些 cmdlet 的信息。</span><span class="sxs-lookup"><span data-stu-id="70367-111">This section contains information about these cmdlets.</span></span>  
  
|<span data-ttu-id="70367-112">说明</span><span class="sxs-lookup"><span data-stu-id="70367-112">Description</span></span>|<span data-ttu-id="70367-113">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="70367-113">Cmdlet</span></span>|  
|-----------------|------------|  
|<span data-ttu-id="70367-114">运行 Transact-SQL 和 XQuery 脚本，如可以使用 `sqlcmd` 实用工具运行的脚本。</span><span class="sxs-lookup"><span data-stu-id="70367-114">Runs Transact-SQL and XQuery scripts, such as scripts that can be run using the `sqlcmd` utility.</span></span>|[<span data-ttu-id="70367-115">Invoke-Sqlcmd cmdlet</span><span class="sxs-lookup"><span data-stu-id="70367-115">Invoke-Sqlcmd cmdlet</span></span>](../../2014/database-engine/invoke-sqlcmd-cmdlet.md)|  
|<span data-ttu-id="70367-116">评估数据库引擎对象是否符合基于策略的管理策略。</span><span class="sxs-lookup"><span data-stu-id="70367-116">Evaluates whether a Database Engine object complies with a Policy-based Management policy.</span></span>|[<span data-ttu-id="70367-117">Invoke-PolicyEvaluation cmdlet</span><span class="sxs-lookup"><span data-stu-id="70367-117">Invoke-PolicyEvaluation cmdlet</span></span>](../../2014/database-engine/invoke-policyevaluation-cmdlet.md)|  
  
### <a name="information-about-other-cmdlets"></a><span data-ttu-id="70367-118">有关其他 Cmdlet 的信息</span><span class="sxs-lookup"><span data-stu-id="70367-118">Information About Other Cmdlets</span></span>  
 <span data-ttu-id="70367-119">`Encode-Sqlname` 和 `Decode-Sqlname` cmdlet 帮助您指定包含 PowerShell 路径中不支持的字符的 SQL Server 标识符。</span><span class="sxs-lookup"><span data-stu-id="70367-119">The `Encode-Sqlname` and `Decode-Sqlname` cmdlets help you specify SQL Server identifiers that contain characters not supported in PowerShell paths.</span></span> <span data-ttu-id="70367-120">有关详细信息，请参阅 [SQL Server Identifiers in PowerShell](../powershell/sql-server-identifiers-in-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="70367-120">For more information, see [SQL Server Identifiers in PowerShell](../powershell/sql-server-identifiers-in-powershell.md).</span></span>  
  
 <span data-ttu-id="70367-121">使用 `Convert-UrnToPath` cmdlet 将[!INCLUDE[ssDE](../includes/ssde-md.md)]对象的统一资源名称转换为 SQL Server PowerShell 提供程序的路径。</span><span class="sxs-lookup"><span data-stu-id="70367-121">Use the `Convert-UrnToPath` cmdlet to convert a Unique Resource Name for a [!INCLUDE[ssDE](../includes/ssde-md.md)] object to a path for the SQL Server PowerShell provider.</span></span> <span data-ttu-id="70367-122">有关详细信息，请参阅 [Convert URNs to SQL Server Provider Paths](../../2014/database-engine/convert-urns-to-sql-server-provider-paths.md)。</span><span class="sxs-lookup"><span data-stu-id="70367-122">For more information, see [Convert URNs to SQL Server Provider Paths](../../2014/database-engine/convert-urns-to-sql-server-provider-paths.md).</span></span>  
  
## <a name="query-expressions-and-unique-resource-names"></a><span data-ttu-id="70367-123">查询表达式和唯一资源名称</span><span class="sxs-lookup"><span data-stu-id="70367-123">Query Expressions and Unique Resource Names</span></span>  
 <span data-ttu-id="70367-124">查询表达式是使用与 XPath 类似的语法指定一组条件的字符串，用于枚举对象模型层次结构中的一个或多个对象。</span><span class="sxs-lookup"><span data-stu-id="70367-124">Query expressions are strings that use syntax similar to XPath to specify a set of criteria that enumerate one or more objects in an object model hierarchy.</span></span> <span data-ttu-id="70367-125">唯一资源名称 (URN) 是一种特定类型的查询表达式字符串，用于唯一标识单个对象。</span><span class="sxs-lookup"><span data-stu-id="70367-125">A Unique Resource Name (URN) is a specific type of query expression string that uniquely identifies a single object.</span></span> <span data-ttu-id="70367-126">有关详细信息，请参阅 [Query Expressions and Uniform Resource Names](../powershell/query-expressions-and-uniform-resource-names.md)。</span><span class="sxs-lookup"><span data-stu-id="70367-126">For more information, see [Query Expressions and Uniform Resource Names](../powershell/query-expressions-and-uniform-resource-names.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70367-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="70367-127">See Also</span></span>  
 [<span data-ttu-id="70367-128">SQL Server PowerShell</span><span class="sxs-lookup"><span data-stu-id="70367-128">SQL Server PowerShell</span></span>](../powershell/sql-server-powershell.md)  
  
  
