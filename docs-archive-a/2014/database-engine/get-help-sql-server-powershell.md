---
title: 获取 SQL Server PowerShell 帮助 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Help [PowerShell]
- Help [SQL Server], PowerShell
- PowerShell [SQL Server], help
ms.assetid: 968c316d-db83-4c24-8ea6-9f18736842f7
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: f1d97a3b694eebb924f9e1ff228d4d38da4f45ec
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690039"
---
# <a name="get-help-sql-server-powershell"></a><span data-ttu-id="404b4-102">Get Help SQL Server PowerShell</span><span class="sxs-lookup"><span data-stu-id="404b4-102">Get Help SQL Server PowerShell</span></span>
  <span data-ttu-id="404b4-103">有关使用 Windows PowerShell 的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 提供程序和 cmdlet 的信息有多个来源，</span><span class="sxs-lookup"><span data-stu-id="404b4-103">There are several sources of information about using the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] provider for Windows PowerShell and cmdlets.</span></span> <span data-ttu-id="404b4-104">这包括 Windows PowerShell 环境中提供的帮助。</span><span class="sxs-lookup"><span data-stu-id="404b4-104">This includes the help that is available in the Windows PowerShell environment.</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="404b4-105">开始之前</span><span class="sxs-lookup"><span data-stu-id="404b4-105">Before You Begin</span></span>  
 <span data-ttu-id="404b4-106">若要了解有关 Windows PowerShell 的信息，请参阅 [Windows PowerShell 入门指南](https://technet.microsoft.com/library/hh857337.aspx)。</span><span class="sxs-lookup"><span data-stu-id="404b4-106">To learn about Windows PowerShell, see [Windows PowerShell Getting Started Guide](https://technet.microsoft.com/library/hh857337.aspx).</span></span>  
  
 <span data-ttu-id="404b4-107">有关 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] cmdlet 和提供程序的概述，请参阅 [SQL Server PowerShell](../powershell/sql-server-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="404b4-107">For an overview of the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] cmdlets and provider, see [SQL Server PowerShell](../powershell/sql-server-powershell.md).</span></span>  
  
### <a name="help-in-the-windows-powershell-environment"></a><span data-ttu-id="404b4-108">Windows PowerShell 环境中的帮助</span><span class="sxs-lookup"><span data-stu-id="404b4-108">Help in the Windows PowerShell Environment</span></span>  
 <span data-ttu-id="404b4-109">使用 **Get-Help** cmdlet 可在 Windows PowerShell 环境中获得帮助。</span><span class="sxs-lookup"><span data-stu-id="404b4-109">Use the **Get-Help** cmdlet to get help in the Windows PowerShell environment.</span></span> <span data-ttu-id="404b4-110">**Get-Help** 为 Windows PowerShell 语言以及 Windows PowerShell 中的各种 cmdlet 和提供程序提供基本帮助。</span><span class="sxs-lookup"><span data-stu-id="404b4-110">**Get-Help** provides basic help for the Windows PowerShell language and the various cmdlets and providers available in Windows PowerShell.</span></span>  
  
 <span data-ttu-id="404b4-111">有关使用 **Get-Help**的方式的详细信息，请参阅 [Get-Help：获取帮助](https://go.microsoft.com/fwlink/?LinkId=102136)。</span><span class="sxs-lookup"><span data-stu-id="404b4-111">For more information on the ways you can use **Get-Help**, see [Get-Help: Getting Help](https://go.microsoft.com/fwlink/?LinkId=102136).</span></span>  
  
### <a name="sql-server-powershell-provider-help"></a><span data-ttu-id="404b4-112">SQL Server PowerShell 提供程序帮助</span><span class="sxs-lookup"><span data-stu-id="404b4-112">SQL Server PowerShell Provider Help</span></span>  
 <span data-ttu-id="404b4-113">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell 提供程序实现 SQLSERVER 虚拟驱动器上的若干文件夹，例如 SQLSERVER:\SQL 和 SQLSERVER:\DAC 文件夹。</span><span class="sxs-lookup"><span data-stu-id="404b4-113">The [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell provider implements several folders on a SQLSERVER virtual drive, such as the SQLSERVER:\SQL and SQLSERVER:\DAC folders.</span></span> <span data-ttu-id="404b4-114">每个文件夹都与一个 SQL Server 可管理性对象模型相关联。</span><span class="sxs-lookup"><span data-stu-id="404b4-114">Each folder is associated with one of the SQL Server manageability object models.</span></span> <span data-ttu-id="404b4-115">虽然您可以列出与 SQL Server 路径中的每个节点关联的方法和属性，便不能在 PowerShell 环境中获取它们的帮助。</span><span class="sxs-lookup"><span data-stu-id="404b4-115">While you can list the methods and properties associated with each node in a SQL Server path, you cannot get help for them in the PowerShell environment.</span></span> <span data-ttu-id="404b4-116">有关带有指向关联的编程参考的文件夹的表，请参阅 [SQL Server PowerShell Provider](../powershell/sql-server-powershell-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="404b4-116">For a table of the folders with links to the associated programming reference, see [SQL Server PowerShell Provider](../powershell/sql-server-powershell-provider.md).</span></span>  
  
### <a name="invoke-sqlcmd-help"></a><span data-ttu-id="404b4-117">Invoke-Sqlcmd 帮助</span><span class="sxs-lookup"><span data-stu-id="404b4-117">Invoke-Sqlcmd Help</span></span>  
 <span data-ttu-id="404b4-118">**Invoke-Sqlcmd** cmdlet 将可由 **sqlcmd** 实用工具运行的查询或脚本文件作为输入。</span><span class="sxs-lookup"><span data-stu-id="404b4-118">The **Invoke-Sqlcmd** cmdlet takes as input any query or script file that can be run by the **sqlcmd** utility.</span></span> <span data-ttu-id="404b4-119">可以使用 **Get-Help** 获取有关 **Invoke-Sqlcmd** 及其参数的信息，但是 **Get-Help** 不作用于 **sqlcmd** 查询。</span><span class="sxs-lookup"><span data-stu-id="404b4-119">You can use **Get-Help** to get information about **Invoke-Sqlcmd** and its parameters, but there is no **Get-Help** coverage for the **sqlcmd** queries.</span></span>  
  
 <span data-ttu-id="404b4-120">*-Query* 或 *-QueryFromFile* 输入可以包含：</span><span class="sxs-lookup"><span data-stu-id="404b4-120">The *-Query* or *-QueryFromFile* input can contain:</span></span>  
  
-   <span data-ttu-id="404b4-121">**sqlcmd** 变量和命令。</span><span class="sxs-lookup"><span data-stu-id="404b4-121">**sqlcmd** variables and commands.</span></span> <span data-ttu-id="404b4-122">有关这些变量和命令的信息，请参阅 [sqlcmd Utility](../tools/sqlcmd-utility.md)的“备注”部分。</span><span class="sxs-lookup"><span data-stu-id="404b4-122">For information about these variables and commands, see the Remarks section of [sqlcmd Utility](../tools/sqlcmd-utility.md).</span></span>  
  
-   [!INCLUDE[tsql](../includes/tsql-md.md)] <span data-ttu-id="404b4-123">语句。</span><span class="sxs-lookup"><span data-stu-id="404b4-123">statements.</span></span> <span data-ttu-id="404b4-124">有关 [!INCLUDE[tsql](../includes/tsql-md.md)] 语言的详细信息，请参阅 [TRANSACT-SQL 引用（数据库引擎）](/sql/t-sql/language-reference)。</span><span class="sxs-lookup"><span data-stu-id="404b4-124">For more information about the [!INCLUDE[tsql](../includes/tsql-md.md)] language, see [Transact-SQL Reference &#40;Database Engine&#41;](/sql/t-sql/language-reference).</span></span>  
  
-   <span data-ttu-id="404b4-125">XQuery 语句。</span><span class="sxs-lookup"><span data-stu-id="404b4-125">XQuery statements.</span></span> <span data-ttu-id="404b4-126">有关 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 支持的 XQuery 语言的详细信息，请参阅 [XQuery 语言参考 (SQL Server)](/sql/xquery/xquery-language-reference-sql-server)。</span><span class="sxs-lookup"><span data-stu-id="404b4-126">For more information about the XQuery language supported by [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], see [XQuery Language Reference &#40;SQL Server&#41;](/sql/xquery/xquery-language-reference-sql-server).</span></span>  
  
## <a name="get-help-for-a-sql-server-cmdlet"></a><span data-ttu-id="404b4-127">获取 SQL Server cmdlet 的帮助</span><span class="sxs-lookup"><span data-stu-id="404b4-127">Get Help for a SQL Server cmdlet</span></span>  
 <span data-ttu-id="404b4-128">**获取有关 cmdlet 的帮助信息**</span><span class="sxs-lookup"><span data-stu-id="404b4-128">**To get help for a cmdlet**</span></span>  
  
-   <span data-ttu-id="404b4-129">运行 Get-Help 并且指定 cmdlet 的名称和要返回的帮助级别。</span><span class="sxs-lookup"><span data-stu-id="404b4-129">Run Get-Help specifying the name of the cmdlet and the level of help to be returned.</span></span>  
  
### <a name="example-cmdlet-get-help"></a><span data-ttu-id="404b4-130">示例：cmdlet Get-Help</span><span class="sxs-lookup"><span data-stu-id="404b4-130">Example: cmdlet Get-Help</span></span>  
 <span data-ttu-id="404b4-131">以下示例返回 **Invoke-Sqlcmd**的各个级别的帮助：</span><span class="sxs-lookup"><span data-stu-id="404b4-131">The following examples return various levels of help for **Invoke-Sqlcmd**:</span></span>  
  
```powershell
## Get the basic help.  
Get-Help Invoke-Sqlcmd  
  
## Get the full help.  
Get-Help Invoke-Sqlcmd -Full  
  
## Get the parameter descriptions.  
Get-Help Invoke-Sqlcmd -Parameter *  
  
## Get the code examples.  
Get-Help Invoke-Sqlcmd -Examples  
  
## Get the syntax diagram.  
Get-Help Invoke-Sqlcmd -Syntax  
```  
  
## <a name="get-a-list-of-providers"></a><span data-ttu-id="404b4-132">获取提供程序的列表</span><span class="sxs-lookup"><span data-stu-id="404b4-132">Get a List of Providers</span></span>  

### <a name="to-get-a-list-of-active-providers"></a><span data-ttu-id="404b4-133">获取活动提供程序的列表</span><span class="sxs-lookup"><span data-stu-id="404b4-133">To get a list of active providers</span></span>
  
1.  <span data-ttu-id="404b4-134">运行 Get-Help 并且指定提供程序类别。</span><span class="sxs-lookup"><span data-stu-id="404b4-134">Run Get-Help specifying the provider category.</span></span>  
  
 <span data-ttu-id="404b4-135">有关在 Windows PowerShell 中获得提供程序帮助的详细信息，请参阅 [驱动器和提供程序](https://go.microsoft.com/fwlink/?LinkId=102137)。</span><span class="sxs-lookup"><span data-stu-id="404b4-135">For more information about getting provider help in Windows PowerShell, see [Drives and Providers](https://go.microsoft.com/fwlink/?LinkId=102137).</span></span>  
  
### <a name="example-get-a-list-of-providers"></a><span data-ttu-id="404b4-136">示例：获取提供程序的列表</span><span class="sxs-lookup"><span data-stu-id="404b4-136">Example: Get a List of Providers</span></span>  
 <span data-ttu-id="404b4-137">下面的代码返回当前在 Windows PowerShell 会话中启用的提供程序的列表：</span><span class="sxs-lookup"><span data-stu-id="404b4-137">This code returns a list of the providers currently enabled in your Windows PowerShell session:</span></span>  
  
```powershell
Get-Help -Category provider  
```  
  
## <a name="get-help-about-the-sql-server-provider"></a><span data-ttu-id="404b4-138">获取有关 SQL Server 提供程序的帮助</span><span class="sxs-lookup"><span data-stu-id="404b4-138">Get Help About the SQL Server Provider</span></span>  
 <span data-ttu-id="404b4-139">**获取有关提供程序的帮助**</span><span class="sxs-lookup"><span data-stu-id="404b4-139">**To get help about the provider**</span></span>  
  
1.  <span data-ttu-id="404b4-140">运行 Get-Help 并且指定名称 SQLServer</span><span class="sxs-lookup"><span data-stu-id="404b4-140">Run Get-Help specifying the name SQLServer</span></span>  
  
### <a name="example-get-sql-server-provider-help"></a><span data-ttu-id="404b4-141">示例：获取 SQL Server 提供程序帮助</span><span class="sxs-lookup"><span data-stu-id="404b4-141">Example: Get SQL Server Provider Help</span></span>  
 <span data-ttu-id="404b4-142">此示例将返回有关 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 提供程序的基本信息：</span><span class="sxs-lookup"><span data-stu-id="404b4-142">This example returns basic information about the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] provider:</span></span>  
  
```powershell
Get-Help SQLServer  
```  
  
## <a name="list-methods-and-properties"></a><span data-ttu-id="404b4-143">列出方法和属性</span><span class="sxs-lookup"><span data-stu-id="404b4-143">List Methods and Properties</span></span>  
 <span data-ttu-id="404b4-144">**列出 SQL Server 提供程序路径中的节点的方法和属性**</span><span class="sxs-lookup"><span data-stu-id="404b4-144">**To list the methods and properties for a node in a SQL Server provider path**</span></span>  
  
1.  <span data-ttu-id="404b4-145">使用 CD 命令转到 SQL Server 路径中的节点，或创建一个指向该位置的变量集。</span><span class="sxs-lookup"><span data-stu-id="404b4-145">Either CD to a node in the SQL Server path, or create a variable set to that location.</span></span>  
  
2.  <span data-ttu-id="404b4-146">运行具有-Type 参数且设置为方法或属性的**Get Member** cmdlet</span><span class="sxs-lookup"><span data-stu-id="404b4-146">Run the **Get-Member** cmdlet with the -Type parameter set to either Methods or Properties</span></span>  
  
### <a name="examples-listing-methods-and-properties"></a><span data-ttu-id="404b4-147">示例：列出方法和属性</span><span class="sxs-lookup"><span data-stu-id="404b4-147">Examples: Listing Methods and Properties</span></span>  
 <span data-ttu-id="404b4-148">此示例列出 Databases 节点支持的方法：</span><span class="sxs-lookup"><span data-stu-id="404b4-148">This example lists the methods supported for the Databases node:</span></span>  
  
```powershell
Set-Location SQL:\MyComputer\DEFAULT\Databases  
Get-Item . | Get-Member -Type Methods  
```  
  
 <span data-ttu-id="404b4-149">此示例列出已经设置为 SMO Table 对象的变量的属性：</span><span class="sxs-lookup"><span data-stu-id="404b4-149">This example lists the properties for a variable that has been set to an SMO Table object:</span></span>  
  
```powershell
$MyVar = New-Object Microsoft.SqlServer.Management.SMO.Table  
$MyVar | Get-Member -Type Properties  
```  
  
## <a name="see-also"></a><span data-ttu-id="404b4-150">另请参阅</span><span class="sxs-lookup"><span data-stu-id="404b4-150">See Also</span></span>  
 <span data-ttu-id="404b4-151">[SQL Server PowerShell 提供程序](../powershell/sql-server-powershell-provider.md) </span><span class="sxs-lookup"><span data-stu-id="404b4-151">[SQL Server PowerShell Provider](../powershell/sql-server-powershell-provider.md) </span></span>  
 [<span data-ttu-id="404b4-152">使用数据库引擎 cmdlet</span><span class="sxs-lookup"><span data-stu-id="404b4-152">Use the Database Engine cmdlets</span></span>](../../2014/database-engine/use-the-database-engine-cmdlets.md)  
