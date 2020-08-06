---
title: 验证 DAC 包 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- data-tier application [SQL Server], validate
- data-tier application [SQL Server], compare
- validate DAC
- compare DACs
- data-tier application [SQL Server], view
- view DAC
ms.assetid: 726ffcc2-9221-424a-8477-99e3f85f03bd
author: stevestein
ms.author: sstein
ms.openlocfilehash: 078c7bfeef2ff8636243f4853c03de252c7b9289
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590864"
---
# <a name="validate-a-dac-package"></a><span data-ttu-id="6f3fe-102">验证 DAC 包</span><span class="sxs-lookup"><span data-stu-id="6f3fe-102">Validate a DAC Package</span></span>
  <span data-ttu-id="6f3fe-103">最好在生产中部署 DAC 包之前查看其内容，并且在升级现有 DAC 之前验证升级操作。</span><span class="sxs-lookup"><span data-stu-id="6f3fe-103">It is a good practice to review the contents of a DAC package before deploying it in production, and to validate the upgrade actions before upgrading an existing DAC.</span></span> <span data-ttu-id="6f3fe-104">当部署的包并非您的组织开发时更需要这样做。</span><span class="sxs-lookup"><span data-stu-id="6f3fe-104">This is especially true when deploying packages that were not developed in your organization.</span></span>  
  
1.  <span data-ttu-id="6f3fe-105">**开始之前：** [先决条件](#Prerequisites)</span><span class="sxs-lookup"><span data-stu-id="6f3fe-105">**Before you begin:**  [Prerequisites](#Prerequisites)</span></span>  
  
2.  <span data-ttu-id="6f3fe-106">若要升级 DAC，请使用：  [查看 DAC 的内容](#ViewDACContents)、[查看数据库更改](#ViewDBChanges)、[查看升级操作](#ViewUpgradeActions)、[比较 DAC](#CompareDACs)</span><span class="sxs-lookup"><span data-stu-id="6f3fe-106">**To upgrade a DAC, using:**  [View the Contents of a DAC](#ViewDACContents), [View Database Changes](#ViewDBChanges), [View Upgrade Actions](#ViewUpgradeActions), [Compare DACs](#CompareDACs)</span></span>  
  
##  <a name="prerequisites"></a><a name="Prerequisites"></a><span data-ttu-id="6f3fe-107">先决条件</span><span class="sxs-lookup"><span data-stu-id="6f3fe-107">Prerequisites</span></span>  
 <span data-ttu-id="6f3fe-108">建议您不要从未知或不可信源部署 DAC 包。</span><span class="sxs-lookup"><span data-stu-id="6f3fe-108">We recommend that you do not deploy a DAC package from unknown or untrusted sources.</span></span> <span data-ttu-id="6f3fe-109">此类 DAC 可能包含恶意代码，这些代码可能会执行非预期的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 代码，或者通过修改架构导致错误。</span><span class="sxs-lookup"><span data-stu-id="6f3fe-109">Such DACs could contain malicious code that might execute unintended [!INCLUDE[tsql](../../includes/tsql-md.md)] code or cause errors by modifying the schema.</span></span> <span data-ttu-id="6f3fe-110">使用来自未知源或不可信源的 DAC 前，请在[!INCLUDE[ssDE](../../includes/ssde-md.md)]的独立测试实例上部署它，对数据库运行 [DBCC CHECKDB (Transact-SQL)](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql)，然后检查数据库中的代码，例如存储过程或其他用户定义的代码。</span><span class="sxs-lookup"><span data-stu-id="6f3fe-110">Before you use a DAC from an unknown or untrusted source, deploy it on an isolated test instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)], run [DBCC CHECKDB &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) on the database, and also examine the code, such as stored procedures or other user-defined code, in the database.</span></span>  
  
##  <a name="view-the-contents-of-a-dac"></a><a name="ViewDACContents"></a> <span data-ttu-id="6f3fe-111">查看 DAC 的内容</span><span class="sxs-lookup"><span data-stu-id="6f3fe-111">View the Contents of a DAC</span></span>  
 <span data-ttu-id="6f3fe-112">有两种机制可用于查看数据层应用程序 (DAC) 包的内容。</span><span class="sxs-lookup"><span data-stu-id="6f3fe-112">There are two mechanisms for viewing the contents of a data-tier application (DAC) package.</span></span> <span data-ttu-id="6f3fe-113">您可以在 SQL Server 开发工具中将 DAC 包导入到某一 DAC 项目。</span><span class="sxs-lookup"><span data-stu-id="6f3fe-113">You can import the DAC package to a DAC project in SQL Server Developer Tools.</span></span> <span data-ttu-id="6f3fe-114">您可以将该包的内容解压缩到一个文件夹中。</span><span class="sxs-lookup"><span data-stu-id="6f3fe-114">You can unpack the contents of the package to a folder.</span></span>  
  
 <span data-ttu-id="6f3fe-115">**在 SQL Server 开发工具中查看 DAC**</span><span class="sxs-lookup"><span data-stu-id="6f3fe-115">**View a DAC in SQL Server Developer Tools**</span></span>  
  
1.  <span data-ttu-id="6f3fe-116">打开“文件”菜单，选择“新建”，然后选择“项目…”    。</span><span class="sxs-lookup"><span data-stu-id="6f3fe-116">Open the **File** menu, select **New**, and then select **Project...**.</span></span>  
  
2.  <span data-ttu-id="6f3fe-117">选择 **SQL Server** 项目模板，然后指定 **“名称”** 、 **“位置”** 和 **“解决方案名称”** 。</span><span class="sxs-lookup"><span data-stu-id="6f3fe-117">Select the **SQL Server** project template, and specify a **Name**, **Location**, and **Solution name**.</span></span>  
  
3.  <span data-ttu-id="6f3fe-118">在“解决方案资源管理器”中，右键单击该项目节点，然后选择“属性…”   。</span><span class="sxs-lookup"><span data-stu-id="6f3fe-118">In **Solution Explorer**, right click the project node and select **Properties...**.</span></span>  
  
4.  <span data-ttu-id="6f3fe-119">在“项目设置”  选项卡上的“输出类型”  部分中，选中“数据层应用程序（.dacpac 文件）”  复选框，然后关闭属性对话框。</span><span class="sxs-lookup"><span data-stu-id="6f3fe-119">On the **Project Settings** tab, in the **Output Types** section, select the **Data-tier Application (.dacpac File)** check box, and then close the properties dialog.</span></span>  
  
5.  <span data-ttu-id="6f3fe-120">在“解决方案资源管理器”中，右键单击该项目节点，然后选择“导入数据层应用程序…”   。</span><span class="sxs-lookup"><span data-stu-id="6f3fe-120">In **Solution Explorer**, right click the project node and select **Import Data-tier Application...**.</span></span>  
  
6.  <span data-ttu-id="6f3fe-121">使用“解决方案资源管理器”  可打开该 DAC 中的所有文件，例如服务器选择策略以及预部署和部署后脚本。</span><span class="sxs-lookup"><span data-stu-id="6f3fe-121">Use **Solution Explorer** to open all of the files in the DAC, such as the server selection policy and the pre- and post-deployment scripts.</span></span>  
  
7.  <span data-ttu-id="6f3fe-122">使用 **“架构视图”** 可查看架构中的所有对象，特别是查看对象（例如函数或存储过程）中的代码。</span><span class="sxs-lookup"><span data-stu-id="6f3fe-122">Use the **Schema View** to review all of the objects in the schema, particularly reviewing the code in objects such as functions or stored procedures.</span></span>  
  
 <span data-ttu-id="6f3fe-123">**查看文件夹中的 DAC**</span><span class="sxs-lookup"><span data-stu-id="6f3fe-123">**View a DAC in a Folder**</span></span>  
  
-   <span data-ttu-id="6f3fe-124">按照 [Unpack a DAC Package](unpack-a-dac-package.md)中的说明将 DAC 包解压缩到一个文件夹中。</span><span class="sxs-lookup"><span data-stu-id="6f3fe-124">Unpack the DAC package into a folder by following the instructions in [Unpack a DAC Package](unpack-a-dac-package.md).</span></span>  
  
-   <span data-ttu-id="6f3fe-125">通过在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 中的 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 查询编辑器中打开 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]脚本来查看其内容。</span><span class="sxs-lookup"><span data-stu-id="6f3fe-125">View the contents of the [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts by opening them in the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span>  
  
-   <span data-ttu-id="6f3fe-126">在记事本等工具中查看文本文件的内容。</span><span class="sxs-lookup"><span data-stu-id="6f3fe-126">View the contents of the text files in tools such as notepad.</span></span>  
  
##  <a name="view-database-changes"></a><a name="ViewDBChanges"></a> <span data-ttu-id="6f3fe-127">查看数据库更改</span><span class="sxs-lookup"><span data-stu-id="6f3fe-127">View Database Changes</span></span>  
 <span data-ttu-id="6f3fe-128">将 DAC 的当前版本部署到生产后，可能已直接对关联的数据库进行了更改，这些更改可能与新版本 DAC 中定义的架构相冲突。</span><span class="sxs-lookup"><span data-stu-id="6f3fe-128">After the current version of a DAC was deployed to production, changes may have been made directly to the associated database that might conflict with the schema defined in a new version of the DAC.</span></span> <span data-ttu-id="6f3fe-129">升级到新版本的 DAC 之前，检查是否已对数据库进行了此类更改。</span><span class="sxs-lookup"><span data-stu-id="6f3fe-129">Before upgrading to a new version of the DAC, check to see if such changes have been made to the database.</span></span>  
  
 <span data-ttu-id="6f3fe-130">**使用向导查看数据库更改**</span><span class="sxs-lookup"><span data-stu-id="6f3fe-130">**View Database Changes by Using a Wizard**</span></span>  
  
1.  <span data-ttu-id="6f3fe-131">运行“升级数据层应用程序”  向导，指定当前部署的 DAC 和包含新版本 DAC 的 DAC 包。</span><span class="sxs-lookup"><span data-stu-id="6f3fe-131">Run the **Upgrade Data-tier Application** wizard, specifying the currently deployed DAC and the DAC package containing the new version of the DAC.</span></span>  
  
2.  <span data-ttu-id="6f3fe-132">在 **“检测更改”** 页上，查看已对数据库进行的更改的报告。</span><span class="sxs-lookup"><span data-stu-id="6f3fe-132">On the **Detect Change** page, review the report of the changes that have been made to the database.</span></span>  
  
3.  <span data-ttu-id="6f3fe-133">如果您不希望继续进行升级，则选择 **“取消”** 。</span><span class="sxs-lookup"><span data-stu-id="6f3fe-133">Select **Cancel** if you do not want to continue with the upgrade.</span></span>  
  
4.  <span data-ttu-id="6f3fe-134">有关使用该向导的详细信息，请参阅 [升级数据层应用程序](upgrade-a-data-tier-application.md)。</span><span class="sxs-lookup"><span data-stu-id="6f3fe-134">For more information on using the wizard, see [Upgrade a Data-tier Application](upgrade-a-data-tier-application.md).</span></span>  
  
### <a name="view-database-changes-by-using-powershell"></a><span data-ttu-id="6f3fe-135">使用 PowerShell 查看数据库更改</span><span class="sxs-lookup"><span data-stu-id="6f3fe-135">View Database Changes by Using PowerShell</span></span>
  
1.  <span data-ttu-id="6f3fe-136">创建一个 SMO Server 对象，并且将该对象设置为包含要查看的 DAC 的实例。</span><span class="sxs-lookup"><span data-stu-id="6f3fe-136">Create a SMO Server object and set it to the instance that contains the DAC to be viewed.</span></span>  
  
2.  <span data-ttu-id="6f3fe-137">打开 `ServerConnection` 对象，并连接到同一实例。</span><span class="sxs-lookup"><span data-stu-id="6f3fe-137">Open a `ServerConnection` object and connect to the same instance.</span></span>  
  
3.  <span data-ttu-id="6f3fe-138">在变量中指定 DAC 名称。</span><span class="sxs-lookup"><span data-stu-id="6f3fe-138">Specify the DAC name in a variable.</span></span>  
  
4.  <span data-ttu-id="6f3fe-139">使用 `GetDatabaseChanges()` 方法检索 `ChangeResults` 对象，并且将该对象加入到某个文本文件中以便生成新的、已删除和已更改的对象的简单报表。</span><span class="sxs-lookup"><span data-stu-id="6f3fe-139">Use the `GetDatabaseChanges()` method to retrieve a `ChangeResults` object, and pipe the object to a text file to generate a simple report of new, deleted, and changed objects.</span></span>  
  
### <a name="view-database-changes-example-powershell"></a><span data-ttu-id="6f3fe-140">查看数据库更改示例 (PowerShell)</span><span class="sxs-lookup"><span data-stu-id="6f3fe-140">View Database Changes Example (PowerShell)</span></span>
  
 <span data-ttu-id="6f3fe-141">下面的示例报告已在名为 MyApplicaiton 的已部署 DAC 中进行的所有数据库更改。</span><span class="sxs-lookup"><span data-stu-id="6f3fe-141">The following example reports any database changes that have been made in a deployed DAC named MyApplicaiton.</span></span>  
  
```powershell
## Set a SMO Server object to the default instance on the local computer.  
CD SQLSERVER:\SQL\localhost\DEFAULT  
$srv = Get-Item .  
  
## Open a Common.ServerConnection to the same instance.  
$serverconnection = New-Object Microsoft.SqlServer.Management.Common.ServerConnection($srv.ConnectionContext.SqlConnectionObject)  
$serverconnection.Connect()  
$dacstore = New-Object Microsoft.SqlServer.Management.Dac.DacStore($serverconnection)  
  
## Specify the DAC instance name.  
$dacName  = "MyApplication"  
  
## Generate the change list and save to file.  
$dacChanges = $dacstore.GetDatabaseChanges($dacName) | Out-File -Filepath C:\DACScripts\MyApplicationChanges.txt  
```  
  
##  <a name="view-upgrade-actions"></a><a name="ViewUpgradeActions"></a> <span data-ttu-id="6f3fe-142">查看升级操作</span><span class="sxs-lookup"><span data-stu-id="6f3fe-142">View Upgrade Actions</span></span>  
 <span data-ttu-id="6f3fe-143">在使用新版本的 DAC 包升级从早期的 DAC 包部署的 DAC 之前，您可以生成一个报告，该报告包含在升级期间将运行的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句，然后查看该语句。</span><span class="sxs-lookup"><span data-stu-id="6f3fe-143">Before using a new version of a DAC package to upgrade a DAC that was deployed from an earlier DAC package, you can generate a report that contains the [!INCLUDE[tsql](../../includes/tsql-md.md)] statements that will be run during the upgrade, and then review the statements.</span></span>  
  
 <span data-ttu-id="6f3fe-144">**使用向导报告升级操作**</span><span class="sxs-lookup"><span data-stu-id="6f3fe-144">**Report Upgrade Actions by Using a Wizard**</span></span>  
  
1.  <span data-ttu-id="6f3fe-145">运行“升级数据层应用程序”\*\*\*\* 向导，指定当前部署的 DAC 和包含新版本 DAC 的 DAC 包。</span><span class="sxs-lookup"><span data-stu-id="6f3fe-145">Run the **Upgrade Data-tier Application** wizard, specifying the currently deployed DAC and the DAC package containing the new version of the DAC.</span></span>  
  
2.  <span data-ttu-id="6f3fe-146">对 **“摘要”** 页上，查看升级操作的报告。</span><span class="sxs-lookup"><span data-stu-id="6f3fe-146">On the **Summary** page, review the report of the upgrade actions.</span></span>  
  
3.  <span data-ttu-id="6f3fe-147">如果您不希望继续进行升级，则选择 **“取消”** 。</span><span class="sxs-lookup"><span data-stu-id="6f3fe-147">Select **Cancel** if you do not want to continue with the upgrade.</span></span>  
  
4.  <span data-ttu-id="6f3fe-148">有关使用该向导的详细信息，请参阅 [升级数据层应用程序](upgrade-a-data-tier-application.md)。</span><span class="sxs-lookup"><span data-stu-id="6f3fe-148">For more information on using the wizard, see [Upgrade a Data-tier Application](upgrade-a-data-tier-application.md).</span></span>  
  
 <span data-ttu-id="6f3fe-149">**使用 PowerShell 报告升级操作**</span><span class="sxs-lookup"><span data-stu-id="6f3fe-149">**Report Upgrade Actions by Using PowerShell**</span></span>  
  
1.  <span data-ttu-id="6f3fe-150">创建一个 SMO Server 对象，并将该对象设置为包含部署的 DAC 的实例。</span><span class="sxs-lookup"><span data-stu-id="6f3fe-150">Create a SMO Server object and set it to the instance that contains the deployed DAC.</span></span>  
  
2.  <span data-ttu-id="6f3fe-151">打开 `ServerConnection` 对象，并连接到同一实例。</span><span class="sxs-lookup"><span data-stu-id="6f3fe-151">Open a `ServerConnection` object and connect to the same instance.</span></span>  
  
3.  <span data-ttu-id="6f3fe-152">使用 `System.IO.File` 加载 DAC 包文件。</span><span class="sxs-lookup"><span data-stu-id="6f3fe-152">Use `System.IO.File` to load the DAC package file.</span></span>  
  
4.  <span data-ttu-id="6f3fe-153">在变量中指定 DAC 名称。</span><span class="sxs-lookup"><span data-stu-id="6f3fe-153">Specify the DAC name in a variable.</span></span>  
  
5.  <span data-ttu-id="6f3fe-154">使用 `GetIncrementalUpgradeScript()` 方法可获取升级时将运行的 Transact-SQL 语句的列表，然后将该列表加入到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="6f3fe-154">Use the `GetIncrementalUpgradeScript()` method to get a list of the Transact-SQL statements an upgrade would run, and pipe the list to a text file.</span></span>  
  
6.  <span data-ttu-id="6f3fe-155">关闭用于读取 DAC 包文件的文件流。</span><span class="sxs-lookup"><span data-stu-id="6f3fe-155">Close the file stream used to read the DAC package file.</span></span>  
  
### <a name="view-upgrade-actions-example-powershell"></a><span data-ttu-id="6f3fe-156">查看升级操作示例 （PowerShell)</span><span class="sxs-lookup"><span data-stu-id="6f3fe-156">View Upgrade Actions Example (PowerShell)</span></span>
  
 <span data-ttu-id="6f3fe-157">以下示例报告一些 Transact-SQL 语句，为了将名为 MyApplicaiton 的 DAC 升级到 MyApplicationVNext.dacpac 文件中定义的架构将运行这些语句。</span><span class="sxs-lookup"><span data-stu-id="6f3fe-157">The following example reports the Transact-SQL statements that would be run to upgrading a DAC named MyApplicaiton to the schema defined in a MyApplicationVNext.dacpac file.</span></span>  
  
```powershell
## Set a SMO Server object to the default instance on the local computer.  
CD SQLSERVER:\SQL\localhost\DEFAULT  
$srv = Get-Item .  
  
## Open a Common.ServerConnection to the same instance.  
$serverconnection = New-Object Microsoft.SqlServer.Management.Common.ServerConnection($srv.ConnectionContext.SqlConnectionObject)  
$serverconnection.Connect()  
$dacstore = New-Object Microsoft.SqlServer.Management.Dac.DacStore($serverconnection)  
  
## Load the DAC package file.  
$dacpacPath = "C:\MyDACs\MyApplicationVNext.dacpac"  
$fileStream = [System.IO.File]::Open($dacpacPath,[System.IO.FileMode]::OpenOrCreate)  
$dacType = [Microsoft.SqlServer.Management.Dac.DacType]::Load($fileStream)  
  
## Specify the DAC instance name.  
$dacName  = "MyApplication"  
  
## Generate the upgrade script and save to file.  
$dacstore.GetIncrementalUpgradeScript($dacName, $dacType) | Out-File -Filepath C:\DACScripts\MyApplicationUpgrade.sql  
  
## Close the filestream to the new DAC package.  
$fileStream.Close()  
```  
  
##  <a name="compare-dacs"></a><a name="CompareDACs"></a><span data-ttu-id="6f3fe-158">比较 Dac</span><span class="sxs-lookup"><span data-stu-id="6f3fe-158">Compare DACs</span></span>  
 <span data-ttu-id="6f3fe-159">在升级 DAC 之前，最好检查当前 DAC 和新 DAC 之间数据库和实例级别对象中的差别。</span><span class="sxs-lookup"><span data-stu-id="6f3fe-159">Before upgrading a DAC, it is a good practice to review the differences in the database and instance-level objects between the current and new DACs.</span></span> <span data-ttu-id="6f3fe-160">如果您对于当前 DAC 没有该包的副本，则可以从当前数据库中提取一个包。</span><span class="sxs-lookup"><span data-stu-id="6f3fe-160">If you do not have a copy of the package for the current DAC, you can extract a package from the current database.</span></span>  
  
 <span data-ttu-id="6f3fe-161">如果您在 SQL Server 开发工具中将两个 DAC 包都导入 DAC 项目中，则可以使用架构比较工具来分析这两个 DAC 之间的差别。</span><span class="sxs-lookup"><span data-stu-id="6f3fe-161">If you import both DAC packages into DAC projects in SQL Server Developer Tools, you can use the Schema Compare tool to analyze the differences between the two DACs.</span></span>  
  
 <span data-ttu-id="6f3fe-162">或者，将 DAC 解压缩到单独的文件夹。</span><span class="sxs-lookup"><span data-stu-id="6f3fe-162">Alternatively, unpack the DACs into separate folders.</span></span> <span data-ttu-id="6f3fe-163">然后，可以使用 WinDiff 实用工具之类的差异工具分析这些差异。</span><span class="sxs-lookup"><span data-stu-id="6f3fe-163">You can then use a difference tool, such as the WinDiff utility, to analyze the differences.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f3fe-164">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6f3fe-164">See Also</span></span>  
 <span data-ttu-id="6f3fe-165">[数据层应用程序](data-tier-applications.md) </span><span class="sxs-lookup"><span data-stu-id="6f3fe-165">[Data-tier Applications](data-tier-applications.md) </span></span>  
 <span data-ttu-id="6f3fe-166">[部署数据层应用程序](deploy-a-data-tier-application.md) </span><span class="sxs-lookup"><span data-stu-id="6f3fe-166">[Deploy a Data-tier Application](deploy-a-data-tier-application.md) </span></span>  
 [<span data-ttu-id="6f3fe-167">升级数据层应用程序</span><span class="sxs-lookup"><span data-stu-id="6f3fe-167">Upgrade a Data-tier Application</span></span>](upgrade-a-data-tier-application.md)  
