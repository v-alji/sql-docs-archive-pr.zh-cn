---
title: 导入 SQLPS 模块 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: a972c56e-b2af-4fe6-abbd-817406e2c93a
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 37e66db05615ce8a285a80e5ac26b0cae411abeb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690796"
---
# <a name="import-the-sqlps-module"></a><span data-ttu-id="74fe4-102">导入 SQLPS 模块</span><span class="sxs-lookup"><span data-stu-id="74fe4-102">Import the SQLPS Module</span></span>
  <span data-ttu-id="74fe4-103">从 PowerShell 管理 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的建议的方法是将 `sqlps` 模块导入到 Windows PowerShell 2.0 环境中。</span><span class="sxs-lookup"><span data-stu-id="74fe4-103">The recommended way to manage [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] from PowerShell is to import the `sqlps` module into a Windows PowerShell 2.0 environment.</span></span> <span data-ttu-id="74fe4-104">该模块将加载并注册 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 管理单元和可管理性程序集。</span><span class="sxs-lookup"><span data-stu-id="74fe4-104">The module loads and registers the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] snap-ins and manageability assemblies.</span></span>  
  
1.  <span data-ttu-id="74fe4-105">**开始之前：**  [安全性](#Security)</span><span class="sxs-lookup"><span data-stu-id="74fe4-105">**Before You Begin:**  [Security](#Security)</span></span>  
  
2.  <span data-ttu-id="74fe4-106">**若要加载模块，请执行以下操作：**  [加载 sqlps 模块](#LoadSqlps)</span><span class="sxs-lookup"><span data-stu-id="74fe4-106">**To load the module:**  [Load the sqlps Module](#LoadSqlps)</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="74fe4-107">开始之前</span><span class="sxs-lookup"><span data-stu-id="74fe4-107">Before You Begin</span></span>  
 <span data-ttu-id="74fe4-108">在将 `sqlps` 模块导入到 Windows PowerShell 后，您可以：</span><span class="sxs-lookup"><span data-stu-id="74fe4-108">After importing the `sqlps` module into Windows PowerShell, you can then:</span></span>  
  
-   <span data-ttu-id="74fe4-109">以交互方式运行 Windows PowerShell 命令。</span><span class="sxs-lookup"><span data-stu-id="74fe4-109">Interactively run Windows PowerShell commands.</span></span>  
  
-   <span data-ttu-id="74fe4-110">运行 Windows PowerShell 脚本文件。</span><span class="sxs-lookup"><span data-stu-id="74fe4-110">Run Windows PowerShell script files.</span></span>  
  
-   <span data-ttu-id="74fe4-111">运行 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] cmdlet。</span><span class="sxs-lookup"><span data-stu-id="74fe4-111">Run [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] cmdlets.</span></span>  
  
-   <span data-ttu-id="74fe4-112">使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 提供程序路径可以浏览 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 对象的层次结构。</span><span class="sxs-lookup"><span data-stu-id="74fe4-112">Use the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] provider paths to navigate through the hierarchy of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] objects.</span></span>  
  
-   <span data-ttu-id="74fe4-113">使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 可管理性对象模型（例如 Microsoft.SqlServer.Management.Smo）管理 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 对象。</span><span class="sxs-lookup"><span data-stu-id="74fe4-113">Use the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] manageability object models (such as Microsoft.SqlServer.Management.Smo) to manage [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] objects.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="74fe4-114">在两个 SQL Server cmdlet（`Encode-Sqlname` 和 `Decode-Sqlname`）的名称中使用的动词与 Windows PowerShell 2.0 的批准的动词不匹配。</span><span class="sxs-lookup"><span data-stu-id="74fe4-114">The verbs used in the names of two SQL Server cmdlets (`Encode-Sqlname` and `Decode-Sqlname`) do not match the approved verbs for Windows PowerShell 2.0.</span></span> <span data-ttu-id="74fe4-115">这对其操作没有影响，但在将 `sqlps` 模块导入到某一会话时 Windows PowerShell 将引发警告。</span><span class="sxs-lookup"><span data-stu-id="74fe4-115">This has no effect on their operation, but Windows PowerShell raises a warning when the `sqlps` module is imported to a session.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="74fe4-116">Security</span><span class="sxs-lookup"><span data-stu-id="74fe4-116">Security</span></span>  
 <span data-ttu-id="74fe4-117">默认情况下，Windows PowerShell 会在脚本执行策略设置为 **Restricted**（即，禁止运行任何 Windows PowerShell 脚本）的情况下运行。</span><span class="sxs-lookup"><span data-stu-id="74fe4-117">By default, Windows PowerShell runs with the scripting execution policy set to **Restricted**, which prevents running any Windows PowerShell scripts.</span></span> <span data-ttu-id="74fe4-118">若要加载 `sqlps` 模块，您可以使用 `Set-ExecutionPolicy` cmdlet 来运行已签名脚本或任意脚本。</span><span class="sxs-lookup"><span data-stu-id="74fe4-118">To load the `sqlps` module, you can use the `Set-ExecutionPolicy` cmdlet to enable running signed scripts, or any scripts.</span></span> <span data-ttu-id="74fe4-119">请仅运行来自受信任源的脚本，并通过使用适当的 NTFS 权限来保证所有输入和输出文件的安全。</span><span class="sxs-lookup"><span data-stu-id="74fe4-119">Only run scripts from trusted sources, and secure all input and output files using the appropriate NTFS permissions.</span></span> <span data-ttu-id="74fe4-120">有关启用 Windows PowerShell 脚本的详细信息，请参阅 [Running Windows PowerShell Scripts](https://docs.microsoft.com/powershell/scripting/getting-started/starting-windows-powershell?view=powershell-6#how-to-enable-windows-powershell-ise-on-earlier-releases-of-windows)（运行 Windows PowerShell 脚本）。</span><span class="sxs-lookup"><span data-stu-id="74fe4-120">For more information about enabling Windows PowerShell scripts, see [Running Windows PowerShell Scripts](https://docs.microsoft.com/powershell/scripting/getting-started/starting-windows-powershell?view=powershell-6#how-to-enable-windows-powershell-ise-on-earlier-releases-of-windows).</span></span>  
  
##  <a name="load-the-sqlps-module"></a><a name="LoadSqlps"></a> <span data-ttu-id="74fe4-121">加载 sqlps 模块</span><span class="sxs-lookup"><span data-stu-id="74fe4-121">Load the sqlps Module</span></span>  

### <a name="to-load-the-sqlps-module-in-windows-powershell"></a><span data-ttu-id="74fe4-122">加载 Windows PowerShell 中的 sqlps 模块</span><span class="sxs-lookup"><span data-stu-id="74fe4-122">To load the sqlps module in Windows PowerShell</span></span>
  
1.  <span data-ttu-id="74fe4-123">使用 `Set-ExecutionPolicy` cmdlet 设置相应的脚本执行策略。</span><span class="sxs-lookup"><span data-stu-id="74fe4-123">Use the `Set-ExecutionPolicy` cmdlet to set the appropriate script execution policy.</span></span>  
  
2.  <span data-ttu-id="74fe4-124">使用 `Import-Module` cmdlet 导入 sqlps 模块。</span><span class="sxs-lookup"><span data-stu-id="74fe4-124">Use the `Import-Module` cmdlet to import the sqlps module.</span></span> <span data-ttu-id="74fe4-125">如果您想要不显示与 `DisableNameChecking` 和 `Encode-Sqlname` 有关的警告，请指定 `Decode-Sqlname` 参数。</span><span class="sxs-lookup"><span data-stu-id="74fe4-125">Specify the `DisableNameChecking` parameter if you want to suppress the warning about `Encode-Sqlname` and `Decode-Sqlname`.</span></span>  
  
### <a name="example-powershell"></a><span data-ttu-id="74fe4-126">示例 (PowerShell)</span><span class="sxs-lookup"><span data-stu-id="74fe4-126">Example (PowerShell)</span></span>  
 <span data-ttu-id="74fe4-127">此示例加载 `sqlps` 模块并且禁用了名称检查。</span><span class="sxs-lookup"><span data-stu-id="74fe4-127">This example loads the `sqlps` module with name checking turned off.</span></span>  
  
```powershell
## Import the SQL Server Module.  
  
Import-Module "sqlps" -DisableNameChecking  
```  

## <a name="see-also"></a><span data-ttu-id="74fe4-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="74fe4-128">See Also</span></span>  
 <span data-ttu-id="74fe4-129">[SQL Server PowerShell](../powershell/sql-server-powershell.md) </span><span class="sxs-lookup"><span data-stu-id="74fe4-129">[SQL Server PowerShell](../powershell/sql-server-powershell.md) </span></span>  
 <span data-ttu-id="74fe4-130">[SQL Server PowerShell 提供程序](../powershell/sql-server-powershell-provider.md) </span><span class="sxs-lookup"><span data-stu-id="74fe4-130">[SQL Server PowerShell Provider](../powershell/sql-server-powershell-provider.md) </span></span>  
 [<span data-ttu-id="74fe4-131">使用数据库引擎 cmdlet</span><span class="sxs-lookup"><span data-stu-id="74fe4-131">Use the Database Engine cmdlets</span></span>](../../2014/database-engine/use-the-database-engine-cmdlets.md)  
