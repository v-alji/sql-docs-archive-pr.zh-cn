---
title: 使用 SQL Server PowerShell 路径 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: scripting
ms.topic: conceptual
ms.assetid: f31d8e2c-8d59-4fee-ac2a-324668e54262
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6d2647251eb1c8843d4ab7a95d2c439e47f5bb6a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689460"
---
# <a name="work-with-sql-server-powershell-paths"></a><span data-ttu-id="e8990-102">使用 SQL ServerPowerShell 路径</span><span class="sxs-lookup"><span data-stu-id="e8990-102">Work With SQL Server PowerShell Paths</span></span>
  <span data-ttu-id="e8990-103">在您导航到 [!INCLUDE[ssDE](../includes/ssde-md.md)] 提供程序路径中的某一节点后，可通过使用与该节点相关联的 [!INCLUDE[ssDE](../includes/ssde-md.md)] 管理对象中的方法和属性，执行工作或检索信息。</span><span class="sxs-lookup"><span data-stu-id="e8990-103">After you have navigated to a node in a [!INCLUDE[ssDE](../includes/ssde-md.md)] provider path, you can perform work or retrieve information by using the methods and properties from the [!INCLUDE[ssDE](../includes/ssde-md.md)] management object associated with the node.</span></span>  
  
1.  [<span data-ttu-id="e8990-104">开始之前</span><span class="sxs-lookup"><span data-stu-id="e8990-104">Before You Begin</span></span>](#BeforeYouBegin)  
  
2.  <span data-ttu-id="e8990-105">**To work on a path node:**  [Listing Methods and Properties](#ListPropMeth), [Using Methods and Properties](#UsePropMeth)</span><span class="sxs-lookup"><span data-stu-id="e8990-105">**To work on a path node:**  [Listing Methods and Properties](#ListPropMeth), [Using Methods and Properties](#UsePropMeth)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="e8990-106">开始之前</span><span class="sxs-lookup"><span data-stu-id="e8990-106">Before You Begin</span></span>  
 <span data-ttu-id="e8990-107">在导航到 [!INCLUDE[ssDE](../includes/ssde-md.md)] 提供程序路径中的节点之后，可以执行两种类型的操作：</span><span class="sxs-lookup"><span data-stu-id="e8990-107">After you have navigated to a node in a [!INCLUDE[ssDE](../includes/ssde-md.md)] provider path, you can perform two types of actions:</span></span>  
  
-   <span data-ttu-id="e8990-108">可以运行作用于节点的 Windows PowerShell cmdlet，如 **Rename-Item**。</span><span class="sxs-lookup"><span data-stu-id="e8990-108">You can run Windows PowerShell cmdlets that operate on nodes, such as **Rename-Item**.</span></span>  
  
-   <span data-ttu-id="e8990-109">可以调用相关联的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 管理对象模型中的方法，如 SMO。</span><span class="sxs-lookup"><span data-stu-id="e8990-109">You can call the methods from the associated [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] management object model, such as SMO.</span></span> <span data-ttu-id="e8990-110">例如，如果你导航到路径中的 Databases 节点，则可以使用 <xref:Microsoft.SqlServer.Management.Smo.Database> 类的方法和属性。</span><span class="sxs-lookup"><span data-stu-id="e8990-110">For example, if you navigate to the Databases node in a path, you can use the methods and properties of the <xref:Microsoft.SqlServer.Management.Smo.Database> class.</span></span>  
  
 <span data-ttu-id="e8990-111">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 提供程序用于管理 [!INCLUDE[ssDE](../includes/ssde-md.md)]实例中的对象，</span><span class="sxs-lookup"><span data-stu-id="e8990-111">The [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] provider is used to manage the objects in an instance of the [!INCLUDE[ssDE](../includes/ssde-md.md)].</span></span> <span data-ttu-id="e8990-112">而不能用于处理数据库中的数据。</span><span class="sxs-lookup"><span data-stu-id="e8990-112">It is not used to work with the data in databases.</span></span> <span data-ttu-id="e8990-113">如果您已经导航到表或视图，则不能使用该提供程序选择、插入、更新或删除数据。</span><span class="sxs-lookup"><span data-stu-id="e8990-113">If you have navigated to a table or view, you cannot use the provider to select, insert, update, or delete data.</span></span> <span data-ttu-id="e8990-114">可以使用 **Invoke-Sqlcmd** cmdlet 来查询或更改 Windows PowerShell 环境内表和视图中的数据。</span><span class="sxs-lookup"><span data-stu-id="e8990-114">Use the **Invoke-Sqlcmd** cmdlet to query or change data in tables and views from the Windows PowerShell environment.</span></span> <span data-ttu-id="e8990-115">有关详细信息，请参阅 [Invoke-Sqlcmd cmdlet](../database-engine/invoke-sqlcmd-cmdlet.md)。</span><span class="sxs-lookup"><span data-stu-id="e8990-115">For more information, see [Invoke-Sqlcmd cmdlet](../database-engine/invoke-sqlcmd-cmdlet.md).</span></span>  
  
##  <a name="listing-methods-and-properties"></a><a name="ListPropMeth"></a> <span data-ttu-id="e8990-116">列出方法和属性</span><span class="sxs-lookup"><span data-stu-id="e8990-116">Listing Methods and Properties</span></span>
  
 <span data-ttu-id="e8990-117">若要查看可供特定对象或对象类使用的方法和属性，请使用 **Get-Member** cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e8990-117">To view the methods and properties available for specific objects or object classes, use the **Get-Member** cmdlet.</span></span>  
  
### <a name="examples-listing-methods-and-properties"></a><span data-ttu-id="e8990-118">示例：列出方法和属性</span><span class="sxs-lookup"><span data-stu-id="e8990-118">Examples: Listing Methods and Properties</span></span>  
 <span data-ttu-id="e8990-119">下面的示例将 Windows PowerShell 变量设置为 SMO <xref:Microsoft.SqlServer.Management.Smo.Database> 类并列出其方法和属性：</span><span class="sxs-lookup"><span data-stu-id="e8990-119">This example sets a Windows PowerShell variable to the SMO <xref:Microsoft.SqlServer.Management.Smo.Database> class and lists the methods and properties:</span></span>  
  
```powershell
$MyDBVar = New-Object Microsoft.SqlServer.Management.SMO.Database  
$MyDBVar | Get-Member -Type Methods  
$MyDBVar | Get-Member -Type Properties  
```  
  
 <span data-ttu-id="e8990-120">还可以使用 **Get-Member** 列出与 Windows PowerShell 路径的结束节点相关联的方法和属性。</span><span class="sxs-lookup"><span data-stu-id="e8990-120">You can also use **Get-Member** to list the methods and properties that are associated with the end node of a Windows PowerShell path.</span></span>  
  
 <span data-ttu-id="e8990-121">下面的示例导航到 SQLSERVER: 路径中的 Databases 节点，并列出集合属性：</span><span class="sxs-lookup"><span data-stu-id="e8990-121">This example navigates to the Databases node in a SQLSERVER: path and lists the collection properties:</span></span>  
  
```powershell
Set-Location SQLSERVER:\SQL\localhost\DEFAULT\Databases  
Get-Item . | Get-Member -Type Properties  
```  
  
 <span data-ttu-id="e8990-122">下面的示例导航到 SQLSERVER: 路径中的 AdventureWorks2012 节点，并列出对象属性：</span><span class="sxs-lookup"><span data-stu-id="e8990-122">This example navigates to the AdventureWorks2012 node in a SQLSERVER: path and lists the object properties:</span></span>  
  
```powershell
Set-Location SQLSERVER:\SQL\localhost\DEFAULT\Databases\AdventureWorks2012  
Get-Item . | Get-Member -Type Properties  
```  
  
##  <a name="using-smo-methods-and-properties"></a><a name="UsePropMeth"></a><span data-ttu-id="e8990-123">使用 SMO 方法和属性</span><span class="sxs-lookup"><span data-stu-id="e8990-123">Using SMO Methods and Properties</span></span>  
  
 <span data-ttu-id="e8990-124">若要从 [!INCLUDE[ssDE](../includes/ssde-md.md)] 提供程序路径对对象执行操作，您可以使用 SMO 方法和属性。</span><span class="sxs-lookup"><span data-stu-id="e8990-124">To perform work on objects from a [!INCLUDE[ssDE](../includes/ssde-md.md)] provider path, you can use SMO methods and properties.</span></span>  
  
### <a name="examples-using-methods-and-properties"></a><span data-ttu-id="e8990-125">示例：使用方法和属性</span><span class="sxs-lookup"><span data-stu-id="e8990-125">Examples: Using Methods and Properties</span></span>  
 <span data-ttu-id="e8990-126">下面的示例使用 SMO **Schema** 属性，从 AdventureWorks2012 中的 Sales 架构中获取表的列表：</span><span class="sxs-lookup"><span data-stu-id="e8990-126">This example uses the SMO **Schema** property to get a list of the tables from the Sales schema in AdventureWorks2012:</span></span>  
  
```powershell
Set-Location SQLSERVER:\SQL\localhost\DEFAULT\Databases\AdventureWorks2012\Tables  
Get-ChildItem | Where {$_.Schema -eq "Sales"}  
```  
  
 <span data-ttu-id="e8990-127">此示例使用 SMO **script**方法生成一个包含语句的脚本， `CREATE VIEW` 您必须在 AdventureWorks2012 中重新创建视图：</span><span class="sxs-lookup"><span data-stu-id="e8990-127">This example uses the SMO **Script** method to generate a script that contains the `CREATE VIEW` statements you must have to re-create the views in AdventureWorks2012:</span></span>  
  
```powershell
Remove-Item C:\PowerShell\CreateViews.sql  
Set-Location SQLSERVER:\SQL\localhost\DEFAULT\Databases\AdventureWorks2012\Views  
foreach ($Item in Get-ChildItem) { $Item.Script() | Out-File -Filepath C:\PowerShell\CreateViews.sql -append }  
```  
  
 <span data-ttu-id="e8990-128">下面的示例使用 SMO **Create** 方法创建一个数据库，然后使用 **State** 属性显示该数据库是否存在：</span><span class="sxs-lookup"><span data-stu-id="e8990-128">This example uses the SMO **Create** method to create a database, and then uses the **State** property to show whether the database exists:</span></span>  
  
```powershell
Set-Location SQLSERVER:\SQL\localhost\DEFAULT\Databases  
$MyDBVar = New-Object Microsoft.SqlServer.Management.SMO.Database  
$MyDBVar.Parent = (Get-Item ..)  
$MyDBVar.Name = "NewDB"  
$MyDBVar.Create()  
$MyDBVar.State  
```  
  
## <a name="see-also"></a><span data-ttu-id="e8990-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e8990-129">See Also</span></span>  
 <span data-ttu-id="e8990-130">[SQL Server PowerShell 提供程序](sql-server-powershell-provider.md) </span><span class="sxs-lookup"><span data-stu-id="e8990-130">[SQL Server PowerShell Provider](sql-server-powershell-provider.md) </span></span>  
 <span data-ttu-id="e8990-131">[导航 SQL Server PowerShell 路径](navigate-sql-server-powershell-paths.md) </span><span class="sxs-lookup"><span data-stu-id="e8990-131">[Navigate SQL Server PowerShell Paths](navigate-sql-server-powershell-paths.md) </span></span>  
 <span data-ttu-id="e8990-132">[将 Urn 转换为 SQL Server 提供程序路径](../database-engine/convert-urns-to-sql-server-provider-paths.md) </span><span class="sxs-lookup"><span data-stu-id="e8990-132">[Convert URNs to SQL Server Provider Paths](../database-engine/convert-urns-to-sql-server-provider-paths.md) </span></span>  
 [<span data-ttu-id="e8990-133">SQL Server PowerShell</span><span class="sxs-lookup"><span data-stu-id="e8990-133">SQL Server PowerShell</span></span>](sql-server-powershell.md)  
  
  
