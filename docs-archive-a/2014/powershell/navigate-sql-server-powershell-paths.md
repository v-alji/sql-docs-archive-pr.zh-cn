---
title: 导航 SQL Server PowerShell 路径 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: scripting
ms.topic: conceptual
ms.assetid: d68aca48-d161-45ed-9f4f-14122ed30218
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0a605479991c3e907cd9dcae254cc1bc04a49392
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693387"
---
# <a name="navigate-sql-server-powershell-paths"></a><span data-ttu-id="047ec-102">导航 SQL ServerPowerShell 路径</span><span class="sxs-lookup"><span data-stu-id="047ec-102">Navigate SQL Server PowerShell Paths</span></span>
  <span data-ttu-id="047ec-103">[!INCLUDE[ssDE](../includes/ssde-md.md)] PowerShell 提供程序在与文件路径相似的结构中公开 SQL Server 实例中的对象集。</span><span class="sxs-lookup"><span data-stu-id="047ec-103">The [!INCLUDE[ssDE](../includes/ssde-md.md)] PowerShell provider exposes the set of objects in an instance of SQL Server in a structure similar to a file path.</span></span> <span data-ttu-id="047ec-104">您可以使用 Windows PowerShell cmdlet 导航提供程序路径，并且创建自定义驱动器以便缩短需键入的路径。</span><span class="sxs-lookup"><span data-stu-id="047ec-104">You can use Windows PowerShell cmdlets to navigate the provider path, and create custom drives to shorten the path you have to type.</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="047ec-105">开始之前</span><span class="sxs-lookup"><span data-stu-id="047ec-105">Before You Begin</span></span>  
 <span data-ttu-id="047ec-106">Windows PowerShell 实现 cmdlet 以便导航表示 PowerShell 提供程序支持的对象层次结构的路径结构。</span><span class="sxs-lookup"><span data-stu-id="047ec-106">Windows PowerShell implements cmdlets to navigate the path structure that represent the hierarchy of objects supported by a PowerShell provider.</span></span> <span data-ttu-id="047ec-107">在您导航到该路径中的节点时，可以使用其他 cmdlet 以便针对当前对象执行基本操作。</span><span class="sxs-lookup"><span data-stu-id="047ec-107">When you have navigated to a node in the path, you can use other cmdlets to perform basic operations on the current object.</span></span> <span data-ttu-id="047ec-108">由于 cmdlet 会经常用到，因此它们具有简短的规范别名。</span><span class="sxs-lookup"><span data-stu-id="047ec-108">Because the cmdlets are used frequently, they have short, canonical aliases.</span></span> <span data-ttu-id="047ec-109">还有一组将 cmdlet 映射到类似命令提示符命令的别名，以及另一组用于 UNIX shell 命令的别名。</span><span class="sxs-lookup"><span data-stu-id="047ec-109">There is also one set of aliases that maps the cmdlets to similar command prompt commands, and another set for UNIX shell commands.</span></span>  
  
 <span data-ttu-id="047ec-110">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 提供程序实现了提供程序 cmdlets 的一部分，如下表中所示。</span><span class="sxs-lookup"><span data-stu-id="047ec-110">The [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] provider implements a subset of the provider cmdlets, shown in the following table.</span></span>  
  
|<span data-ttu-id="047ec-111">cmdlet</span><span class="sxs-lookup"><span data-stu-id="047ec-111">cmdlet</span></span>|<span data-ttu-id="047ec-112">规范别名</span><span class="sxs-lookup"><span data-stu-id="047ec-112">Canonical alias</span></span>|<span data-ttu-id="047ec-113">cmd 别名</span><span class="sxs-lookup"><span data-stu-id="047ec-113">cmd alias</span></span>|<span data-ttu-id="047ec-114">UNIX shell 别名</span><span class="sxs-lookup"><span data-stu-id="047ec-114">UNIX shell alias</span></span>|<span data-ttu-id="047ec-115">说明</span><span class="sxs-lookup"><span data-stu-id="047ec-115">Description</span></span>|  
|------------|---------------------|---------------|----------------------|-----------------|  
|<span data-ttu-id="047ec-116">**Get-Location**</span><span class="sxs-lookup"><span data-stu-id="047ec-116">**Get-Location**</span></span>|<span data-ttu-id="047ec-117">**gl**</span><span class="sxs-lookup"><span data-stu-id="047ec-117">**gl**</span></span>|<span data-ttu-id="047ec-118">**pwd**</span><span class="sxs-lookup"><span data-stu-id="047ec-118">**pwd**</span></span>|<span data-ttu-id="047ec-119">**pwd**</span><span class="sxs-lookup"><span data-stu-id="047ec-119">**pwd**</span></span>|<span data-ttu-id="047ec-120">获取当前节点。</span><span class="sxs-lookup"><span data-stu-id="047ec-120">Gets the current node.</span></span>|  
|`Set-Location`|<span data-ttu-id="047ec-121">**sl**</span><span class="sxs-lookup"><span data-stu-id="047ec-121">**sl**</span></span>|<span data-ttu-id="047ec-122">**cd、chdir**</span><span class="sxs-lookup"><span data-stu-id="047ec-122">**cd, chdir**</span></span>|<span data-ttu-id="047ec-123">**cd、chdir**</span><span class="sxs-lookup"><span data-stu-id="047ec-123">**cd, chdir**</span></span>|<span data-ttu-id="047ec-124">更改当前节点。</span><span class="sxs-lookup"><span data-stu-id="047ec-124">Changes the current node.</span></span>|  
|<span data-ttu-id="047ec-125">**Get-ChildItem**</span><span class="sxs-lookup"><span data-stu-id="047ec-125">**Get-ChildItem**</span></span>|<span data-ttu-id="047ec-126">**gci**</span><span class="sxs-lookup"><span data-stu-id="047ec-126">**gci**</span></span>|<span data-ttu-id="047ec-127">**dir**</span><span class="sxs-lookup"><span data-stu-id="047ec-127">**dir**</span></span>|<span data-ttu-id="047ec-128">**'**</span><span class="sxs-lookup"><span data-stu-id="047ec-128">**ls**</span></span>|<span data-ttu-id="047ec-129">列出存储在当前节点中的对象。</span><span class="sxs-lookup"><span data-stu-id="047ec-129">Lists the objects stored at the current node.</span></span>|  
|<span data-ttu-id="047ec-130">**Get-Item**</span><span class="sxs-lookup"><span data-stu-id="047ec-130">**Get-Item**</span></span>|<span data-ttu-id="047ec-131">**gi**</span><span class="sxs-lookup"><span data-stu-id="047ec-131">**gi**</span></span>|||<span data-ttu-id="047ec-132">返回当前项的属性。</span><span class="sxs-lookup"><span data-stu-id="047ec-132">Returns the properties of the current item.</span></span>|  
|<span data-ttu-id="047ec-133">**Rename-Item**</span><span class="sxs-lookup"><span data-stu-id="047ec-133">**Rename-Item**</span></span>|<span data-ttu-id="047ec-134">**rni**</span><span class="sxs-lookup"><span data-stu-id="047ec-134">**rni**</span></span>|<span data-ttu-id="047ec-135">**rn**</span><span class="sxs-lookup"><span data-stu-id="047ec-135">**rn**</span></span>|<span data-ttu-id="047ec-136">**ren**</span><span class="sxs-lookup"><span data-stu-id="047ec-136">**ren**</span></span>|<span data-ttu-id="047ec-137">重命名对象。</span><span class="sxs-lookup"><span data-stu-id="047ec-137">Renames an object.</span></span>|  
|<span data-ttu-id="047ec-138">**Remove-Item**</span><span class="sxs-lookup"><span data-stu-id="047ec-138">**Remove-Item**</span></span>|<span data-ttu-id="047ec-139">**ri**</span><span class="sxs-lookup"><span data-stu-id="047ec-139">**ri**</span></span>|<span data-ttu-id="047ec-140">**del、rd**</span><span class="sxs-lookup"><span data-stu-id="047ec-140">**del, rd**</span></span>|<span data-ttu-id="047ec-141">**rm、rmdir**</span><span class="sxs-lookup"><span data-stu-id="047ec-141">**rm, rmdir**</span></span>|<span data-ttu-id="047ec-142">删除对象。</span><span class="sxs-lookup"><span data-stu-id="047ec-142">Removes an object.</span></span>|  
  
> [!IMPORTANT]  
>  <span data-ttu-id="047ec-143">某些 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 标识符（对象名称）包含 Windows PowerShell 不支持在路径名称中使用的字符。</span><span class="sxs-lookup"><span data-stu-id="047ec-143">Some [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] identifiers (object names) contain characters that Windows PowerShell does not support in path names.</span></span> <span data-ttu-id="047ec-144">有关如何使用包含这些字符的名称的详细信息，请参阅 [SQL Server Identifiers in PowerShell](sql-server-identifiers-in-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="047ec-144">For more information about how to use names that contain these characters, see [SQL Server Identifiers in PowerShell](sql-server-identifiers-in-powershell.md).</span></span>  
  
### <a name="sql-server-information-returned-by-get-childitem"></a><span data-ttu-id="047ec-145">Get-ChildItem 返回的 SQL Server 信息</span><span class="sxs-lookup"><span data-stu-id="047ec-145">SQL Server Information Returned by Get-ChildItem</span></span>  
 <span data-ttu-id="047ec-146">由 **Get-ChildItem** （或其 **dir** 和 **ls** 别名）返回的信息取决于你在 SQLSERVER: 路径中的位置。</span><span class="sxs-lookup"><span data-stu-id="047ec-146">The information returned by **Get-ChildItem** (or its **dir** and **ls** aliases) depends on your location in a SQLSERVER: path.</span></span>  
  
|<span data-ttu-id="047ec-147">路径位置</span><span class="sxs-lookup"><span data-stu-id="047ec-147">Path location</span></span>|<span data-ttu-id="047ec-148">Get-ChildItem 结果</span><span class="sxs-lookup"><span data-stu-id="047ec-148">Get-ChildItem results</span></span>|  
|-------------------|----------------------------|  
|<span data-ttu-id="047ec-149">SQLSERVER:\SQL</span><span class="sxs-lookup"><span data-stu-id="047ec-149">SQLSERVER:\SQL</span></span>|<span data-ttu-id="047ec-150">返回本地计算机的名称。</span><span class="sxs-lookup"><span data-stu-id="047ec-150">Returns the name of the local computer.</span></span> <span data-ttu-id="047ec-151">如果在连接到其他计算机上的 [!INCLUDE[ssDE](../includes/ssde-md.md)] 实例时使用的是 SMO 或 WMI，则还将列出这些计算机。</span><span class="sxs-lookup"><span data-stu-id="047ec-151">If you have used the SMO or WMI to connect to instances of the [!INCLUDE[ssDE](../includes/ssde-md.md)] on other computers, those computers are also listed.</span></span>|  
|<span data-ttu-id="047ec-152">SQLSERVER:\SQL\\*ComputerName*</span><span class="sxs-lookup"><span data-stu-id="047ec-152">SQLSERVER:\SQL\\*ComputerName*</span></span>|<span data-ttu-id="047ec-153">计算机上 [!INCLUDE[ssDE](../includes/ssde-md.md)] 实例的列表。</span><span class="sxs-lookup"><span data-stu-id="047ec-153">The list of instances of the [!INCLUDE[ssDE](../includes/ssde-md.md)] on the computer.</span></span>|  
|<span data-ttu-id="047ec-154">SQLSERVER： \ SQL \\ *ComputerName* \\ *实例*名称</span><span class="sxs-lookup"><span data-stu-id="047ec-154">SQLSERVER:\SQL\\*ComputerName*\\*InstanceName*</span></span>|<span data-ttu-id="047ec-155">实例中顶层对象类型（如 Endpoints、Certificates 和 Databases）的列表。</span><span class="sxs-lookup"><span data-stu-id="047ec-155">The list of top-level object types in the instance, such as Endpoints, Certificates, and Databases.</span></span>|  
|<span data-ttu-id="047ec-156">对象类节点，如 Databases</span><span class="sxs-lookup"><span data-stu-id="047ec-156">Object class node, such as Databases</span></span>|<span data-ttu-id="047ec-157">该类型的对象列表，如数据库列表：master、model、AdventureWorks20008R2。</span><span class="sxs-lookup"><span data-stu-id="047ec-157">The list of objects of that type, such as the list of databases: master, model, AdventureWorks20008R2.</span></span>|  
|<span data-ttu-id="047ec-158">对象名称节点，如 AdventureWorks2012</span><span class="sxs-lookup"><span data-stu-id="047ec-158">Object name node, such as AdventureWorks2012</span></span>|<span data-ttu-id="047ec-159">包含在该对象中的对象类型的列表。</span><span class="sxs-lookup"><span data-stu-id="047ec-159">The list of object types contained within the object.</span></span> <span data-ttu-id="047ec-160">例如，数据库将列出表和视图之类的对象类型。</span><span class="sxs-lookup"><span data-stu-id="047ec-160">For example, a database would list object types such as tables and views.</span></span>|  
  
 <span data-ttu-id="047ec-161">默认情况下， **Get-ChildItem** 不会列出任何系统对象。</span><span class="sxs-lookup"><span data-stu-id="047ec-161">By default, **Get-ChildItem** does not list any system objects.</span></span> <span data-ttu-id="047ec-162">使用 *Force* 参数可查看系统对象，例如 **sys** 架构中的对象。</span><span class="sxs-lookup"><span data-stu-id="047ec-162">Use the *Force* parameter to see system objects, such as the objects in the **sys** schema.</span></span>  
  
### <a name="custom-drives"></a><span data-ttu-id="047ec-163">自定义驱动器</span><span class="sxs-lookup"><span data-stu-id="047ec-163">Custom Drives</span></span>  
 <span data-ttu-id="047ec-164">Windows PowerShell 允许用户定义虚拟驱动器，这些驱动器称为 PowerShell 驱动器。</span><span class="sxs-lookup"><span data-stu-id="047ec-164">Windows PowerShell lets users define virtual drives, which are referred to as PowerShell drives.</span></span> <span data-ttu-id="047ec-165">这些虚拟驱动器映射到路径语句的起始节点。</span><span class="sxs-lookup"><span data-stu-id="047ec-165">These map over the starting nodes of a path statement.</span></span> <span data-ttu-id="047ec-166">使用它们的目的通常是为了缩短经常键入的路径。</span><span class="sxs-lookup"><span data-stu-id="047ec-166">They are typically used to shorten paths that are typed frequently.</span></span> <span data-ttu-id="047ec-167">SQLSERVER: 路径可能会很长，会在 Windows PowerShell 窗口中占据一定的空间，而且需要键入大量内容。</span><span class="sxs-lookup"><span data-stu-id="047ec-167">SQLSERVER: paths can get long, taking space in the Windows PowerShell window and requiring a lot of typing.</span></span> <span data-ttu-id="047ec-168">如果您打算针对特定的路径节点执行大量工作，则可以定义一个映射到该节点的自定义 Windows PowerShell 驱动器。</span><span class="sxs-lookup"><span data-stu-id="047ec-168">If you are going to do a lot of work at a particular path node, you can define a custom Windows PowerShell drive that maps to that node.</span></span>  
  
## <a name="use-powershell-cmdlet-aliases"></a><span data-ttu-id="047ec-169">使用 PowerShell Cmdlet 别名</span><span class="sxs-lookup"><span data-stu-id="047ec-169">Use PowerShell Cmdlet Aliases</span></span>  
 <span data-ttu-id="047ec-170">**使用 cmdlet 别名**</span><span class="sxs-lookup"><span data-stu-id="047ec-170">**Use a cmdlet alias**</span></span>  
  
-   <span data-ttu-id="047ec-171">代替键入整个 cmdlet 名称，键入一个较短的别名，或者映射到熟悉的注释提示命令的别名。</span><span class="sxs-lookup"><span data-stu-id="047ec-171">Instead of typing a full cmdlet name, type a shorter alias, or one that maps to a familiar commend prompt command.</span></span>  
  
### <a name="alias-example-powershell"></a><span data-ttu-id="047ec-172">别名示例 (PowerShell)</span><span class="sxs-lookup"><span data-stu-id="047ec-172">Alias Example (PowerShell)</span></span>  
 <span data-ttu-id="047ec-173">例如，可以使用下面的其中一组 cmdlet 或别名，导航到 SQLSERVER:\SQL 文件夹并请求该文件夹的子项列表，从而检索可供使用的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 实例的列表：</span><span class="sxs-lookup"><span data-stu-id="047ec-173">For example, you can use one of the following sets of cmdlets or aliases to retrieve a listing of the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instances available to you by navigating to the SQLSERVER:\SQL folder and requesting the list of child items for the folder:</span></span>  
  
```powershell
## Shows using the full cmdet name.  
Set-Location SQLSERVER:\SQL  
Get-ChildItem  
  
## Shows using canonical aliases.  
sl SQLSERVER:\SQL  
gci  
  
## Shows using command prompt aliases.  
cd SQLSERVER:\SQL  
dir  
  
## Shows using Unix shell aliases.  
cd SQLSERVER:\SQL  
ls  
```  
  
## <a name="use-get-childitem"></a><span data-ttu-id="047ec-174">使用 Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="047ec-174">Use Get-ChildItem</span></span>  

### <a name="return-information-by-using-get-childitem"></a><span data-ttu-id="047ec-175">通过使用 Get-Childitem 返回信息</span><span class="sxs-lookup"><span data-stu-id="047ec-175">Return information by using Get-Childitem</span></span>
  
1.  <span data-ttu-id="047ec-176">导航到要获取其子级的列表的节点</span><span class="sxs-lookup"><span data-stu-id="047ec-176">Navigate to the node for which you want a list of childrem</span></span>  
  
2.  <span data-ttu-id="047ec-177">运行 Get-Childitem 以便获取该列表。</span><span class="sxs-lookup"><span data-stu-id="047ec-177">Run Get-Childitem to get the list.</span></span>  
  
### <a name="get-childitem-example-powershell"></a><span data-ttu-id="047ec-178">Get-ChildItem 示例 (PowerShell)</span><span class="sxs-lookup"><span data-stu-id="047ec-178">Get-ChildItem Example (PowerShell)</span></span>  
 <span data-ttu-id="047ec-179">这些示例阐释 Get-Childitem 为 SQL Server 提供程序路径中的不同节点返回的信息。</span><span class="sxs-lookup"><span data-stu-id="047ec-179">These examples illustrate the information returned by Get-Childitem for different nodes in a SQL Server provider path.</span></span>  
  
```powershell
## Return the current computer and any computer  
## to which you have made a SQL or WMI connection.  
Set-Location SQLSERVER:\SQL  
Get-ChildItem  
  
## List the instances of the Database Engine on the local computer.  
Set-Location SQLSERVER:\SQL\localhost  
Get-ChildItem  
  
## Lists the categories of objects available in the  
## default instance on the local computer.  
Set-Location SQLSERVER:\SQL\localhost\DEFAULT  
Get-ChildItem  
  
## Lists the databases from the local default instance.  
## The force parameter is used to include the system databases.  
Set-Location SQLSERVER:\SQL\localhost\DEFAULT\Databases  
Get-ChildItem -force  
```  
  
## <a name="create-a-custom-drive"></a><span data-ttu-id="047ec-180">创建自定义驱动器</span><span class="sxs-lookup"><span data-stu-id="047ec-180">Create a Custom Drive</span></span>  

### <a name="create-and-use-a-custom-drive"></a><span data-ttu-id="047ec-181">创建和使用自定义驱动器</span><span class="sxs-lookup"><span data-stu-id="047ec-181">Create and use a custom drive</span></span>
  
1.  <span data-ttu-id="047ec-182">使用 `New-PSDrive` 可以定义自定义驱动器。</span><span class="sxs-lookup"><span data-stu-id="047ec-182">Use `New-PSDrive` to define a custom drive.</span></span> <span data-ttu-id="047ec-183">使用 `Root` 参数可以指定自定义驱动器名称表示的路径。</span><span class="sxs-lookup"><span data-stu-id="047ec-183">Use the `Root` parameter to specify the path that is represented by the custom drive name.</span></span>  
  
2.  <span data-ttu-id="047ec-184">在 `Set-Location` 之类的路径导航 cmdlet 中引用自定义驱动器名称。</span><span class="sxs-lookup"><span data-stu-id="047ec-184">Reference the custom drive name in path navigation cmdlets such as `Set-Location`.</span></span>  
  
### <a name="custom-drive-example-powershell"></a><span data-ttu-id="047ec-185">自定义驱动器示例 (PowerShell)</span><span class="sxs-lookup"><span data-stu-id="047ec-185">Custom Drive Example (PowerShell)</span></span>  
 <span data-ttu-id="047ec-186">此示例创建一个名为 AWDB 的虚拟驱动器，该驱动器映射到 AdventureWorks2012 示例数据库的已部署副本的节点。</span><span class="sxs-lookup"><span data-stu-id="047ec-186">This example creates a virtual drive named AWDB that maps to the node for a deployed copy of the AdventureWorks2012 sample database.</span></span> <span data-ttu-id="047ec-187">然后，使用该虚拟驱动器导航到数据库中的表。</span><span class="sxs-lookup"><span data-stu-id="047ec-187">The virtual drive is then used to navigate to a table in the database.</span></span>  
  
```powershell
## Create a new virtual drive.  
New-PSDrive -Name AWDB -Root SQLSERVER:\SQL\localhost\DEFAULT\Databases\AdventureWorks2012  
  
## Use AWDB: to navigate to a specific table.  
Set-Location AWDB:\Tables\Purchasing.Vendor  
```  
  
## <a name="see-also"></a><span data-ttu-id="047ec-188">另请参阅</span><span class="sxs-lookup"><span data-stu-id="047ec-188">See Also</span></span>  
 <span data-ttu-id="047ec-189">[SQL Server PowerShell 提供程序](sql-server-powershell-provider.md) </span><span class="sxs-lookup"><span data-stu-id="047ec-189">[SQL Server PowerShell Provider](sql-server-powershell-provider.md) </span></span>  
 <span data-ttu-id="047ec-190">[使用 SQL Server PowerShell 路径](work-with-sql-server-powershell-paths.md) </span><span class="sxs-lookup"><span data-stu-id="047ec-190">[Work With SQL Server PowerShell Paths](work-with-sql-server-powershell-paths.md) </span></span>  
 <span data-ttu-id="047ec-191">[将 Urn 转换为 SQL Server 提供程序路径](../database-engine/convert-urns-to-sql-server-provider-paths.md) </span><span class="sxs-lookup"><span data-stu-id="047ec-191">[Convert URNs to SQL Server Provider Paths](../database-engine/convert-urns-to-sql-server-provider-paths.md) </span></span>  
 [<span data-ttu-id="047ec-192">SQL Server PowerShell</span><span class="sxs-lookup"><span data-stu-id="047ec-192">SQL Server PowerShell</span></span>](sql-server-powershell.md)  
