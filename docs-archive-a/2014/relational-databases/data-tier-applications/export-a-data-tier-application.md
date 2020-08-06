---
title: 导出数据层应用程序 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.exportdac.settings.f1
- sql12.swb. exportdac.settings.f1
- sql12.swb.exportdac.welcome.f1
- sql12.swb. exportdac.summary.f1
- sql12.swb.exportdac.progress.f1
- sql12.swb.exportdac.summary.f1
- sql12.swb.exportdac.results.f1
- sql12.swb. exportdac.results.f1
helpviewer_keywords:
- How to [DAC], export
- wizard [DAC], export
- export DAC
- data-tier application [SQL Server], export
ms.assetid: 61915bc5-0f5f-45ac-8cfe-3452bc185558
author: stevestein
ms.author: sstein
ms.openlocfilehash: d5e1bbfc5c38dee5e7f29598086d87b680880641
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589686"
---
# <a name="export-a-data-tier-application"></a><span data-ttu-id="e1a48-102">导出数据层应用程序</span><span class="sxs-lookup"><span data-stu-id="e1a48-102">Export a Data-tier Application</span></span>
  <span data-ttu-id="e1a48-103">导出部署的数据层应用程序 (DAC) 或数据库将创建一个导出文件，其中同时包括该数据库中的对象定义和表中包含的所有数据。</span><span class="sxs-lookup"><span data-stu-id="e1a48-103">Exporting a deployed data-tier application (DAC) or database creates an export file that includes both the definitions of the objects in the database and all of the data contained in the tables.</span></span> <span data-ttu-id="e1a48-104">然后，可将该导出文件导入到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的其他实例或 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]中。</span><span class="sxs-lookup"><span data-stu-id="e1a48-104">The export file can then be imported to another instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)], or to [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].</span></span> <span data-ttu-id="e1a48-105">可以将导出-导入操作组合起来以在实例之间迁移 DAC，或者创建一个逻辑备份，或者创建部署在 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 中的数据库的本地副本。</span><span class="sxs-lookup"><span data-stu-id="e1a48-105">The export-import operations can be combined to migrate a DAC between instances, to create a logical backup, or to create an on-premise copy of a database deployed in [!INCLUDE[ssSDS](../../includes/sssds-md.md)].</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="e1a48-106">开始之前</span><span class="sxs-lookup"><span data-stu-id="e1a48-106">Before You Begin</span></span>  
 <span data-ttu-id="e1a48-107">导出过程分两个阶段生成一个 DAC 导出文件。</span><span class="sxs-lookup"><span data-stu-id="e1a48-107">The export process builds a DAC export file in two stages.</span></span>  
  
1.  <span data-ttu-id="e1a48-108">导出操作在导出文件中生成 DAC 定义（BACPAC 文件），DAC 提取操作以同样的方式在 DAC 包文件中生成 DAC 定义。</span><span class="sxs-lookup"><span data-stu-id="e1a48-108">The export builds a DAC definition in the export file - BACPAC file - in the same way a DAC extract builds a DAC definition in a DAC package file.</span></span> <span data-ttu-id="e1a48-109">导出的 DAC 定义包含当前数据库中的所有对象。</span><span class="sxs-lookup"><span data-stu-id="e1a48-109">The exported DAC definition includes all of the objects in the current database.</span></span> <span data-ttu-id="e1a48-110">如果针对最初从 DAC 部署的数据库运行导出过程，且在部署后对数据库直接进行了更改，则导出的定义与数据库中的对象集匹配，而不是与原始 DAC 中定义的内容相匹配。</span><span class="sxs-lookup"><span data-stu-id="e1a48-110">If the export process is run against a database that was originally deployed from a DAC, and changes were made directly to the database after deployment, the exported definition matches the object set in the database, not what was defined in the original DAC.</span></span>  
  
2.  <span data-ttu-id="e1a48-111">导出操作从数据库中的所有表中大容量复制数据，然后将这些数据集成到导出文件中。</span><span class="sxs-lookup"><span data-stu-id="e1a48-111">The export bulk copies out the data from all of the tables in the database and incorporates the data into the export file.</span></span>  
  
 <span data-ttu-id="e1a48-112">导出过程将 DAC 版本设置为 1.0.0.0，并将导出文件中的 DAC 说明设置为空字符串。</span><span class="sxs-lookup"><span data-stu-id="e1a48-112">The export process sets the DAC version to 1.0.0.0 and the DAC description in the export file to an empty string.</span></span> <span data-ttu-id="e1a48-113">如果从 DAC 部署数据库，则导出文件中的 DAC 定义包含为原始 DAC 指定的名称，否则，将把 DAC 名称设置为数据库名称。</span><span class="sxs-lookup"><span data-stu-id="e1a48-113">If the database was deployed from a DAC, the DAC definition in the export file contains the name given to the original DAC, otherwise the DAC name is set to the database name.</span></span>  
  

###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> <span data-ttu-id="e1a48-114">限制和局限</span><span class="sxs-lookup"><span data-stu-id="e1a48-114">Limitations and Restrictions</span></span>  
 <span data-ttu-id="e1a48-115">只能从 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]或 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 4 (SP4) 或更高版本的数据库导出 DAC 或数据库。</span><span class="sxs-lookup"><span data-stu-id="e1a48-115">A DAC or database can only be exported from a database in [!INCLUDE[ssSDS](../../includes/sssds-md.md)], or [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 4 (SP4) or later.</span></span>  
  
 <span data-ttu-id="e1a48-116">如果数据库有 DAC 中不支持的对象或包含用户，则不能导出该数据库。</span><span class="sxs-lookup"><span data-stu-id="e1a48-116">You cannot export a database that has objects that are not supported in a DAC, or contained users.</span></span> <span data-ttu-id="e1a48-117">有关 DAC 中支持的对象类型的详细信息，请参阅 [DAC Support For SQL Server Objects and Versions](dac-support-for-sql-server-objects-and-versions.md)。</span><span class="sxs-lookup"><span data-stu-id="e1a48-117">For more information about the types of objects supported in a DAC, see [DAC Support For SQL Server Objects and Versions](dac-support-for-sql-server-objects-and-versions.md).</span></span>  
  
###  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="e1a48-118">权限</span><span class="sxs-lookup"><span data-stu-id="e1a48-118">Permissions</span></span>  
 <span data-ttu-id="e1a48-119">导出 DAC 至少要求 ALTER ANY LOGIN 和数据库范围内的 VIEW DEFINITION 权限，以及对 **sys.sql_expression_dependencies**具有 SELECT 权限。</span><span class="sxs-lookup"><span data-stu-id="e1a48-119">Exporting a DAC requires at least ALTER ANY LOGIN and database scope VIEW DEFINITION permissions, as well as SELECT permissions on **sys.sql_expression_dependencies**.</span></span> <span data-ttu-id="e1a48-120">导出 DAC 可由 securityadmin 固定服务器角色的成员（也是从其导出 DAC 的数据库中 database_owner 固定数据库角色的成员）完成。</span><span class="sxs-lookup"><span data-stu-id="e1a48-120">Exporting a DAC can be done by members of the securityadmin fixed server role who are also members of the database_owner fixed database role in the database from which the DAC is exported.</span></span> <span data-ttu-id="e1a48-121">sysadmin 固定服务器角色的成员或名为 **sa** 的内置 SQL Server 系统管理员帐户也可以导出 DAC。</span><span class="sxs-lookup"><span data-stu-id="e1a48-121">Members of the sysadmin fixed server role or the built-in SQL Server system administrator account named **sa** can also export a DAC.</span></span>  
  
##  <a name="using-the-export-data-tier-application-wizard"></a><a name="UsingDeployDACWizard"></a><span data-ttu-id="e1a48-122">使用 "导出数据层应用程序向导"</span><span class="sxs-lookup"><span data-stu-id="e1a48-122">Using the Export Data-tier Application Wizard</span></span>  
 <span data-ttu-id="e1a48-123">**使用向导导出 DAC**</span><span class="sxs-lookup"><span data-stu-id="e1a48-123">**To Export a DAC Using a Wizard**</span></span>  
  
1.  <span data-ttu-id="e1a48-124">连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的实例（无论是在内部部署中还是在 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]中）。</span><span class="sxs-lookup"><span data-stu-id="e1a48-124">Connect to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], whether on-premise or in [!INCLUDE[ssSDS](../../includes/sssds-md.md)].</span></span>  
  
2.  <span data-ttu-id="e1a48-125">在 **“对象资源管理器”** 中，展开要从中导出 DAC 的实例的节点。</span><span class="sxs-lookup"><span data-stu-id="e1a48-125">In **Object Explorer**, expand the node for the instance from which you want to export the DAC.</span></span>  
  
3.  <span data-ttu-id="e1a48-126">右键单击数据库名称。</span><span class="sxs-lookup"><span data-stu-id="e1a48-126">Right-click the database name.</span></span>  
  
4.  <span data-ttu-id="e1a48-127">单击“任务”，然后选择“导出数据层应用程序…”\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="e1a48-127">Click **Tasks** and then select **Export Data-tier Application...**</span></span>  
  
5.  <span data-ttu-id="e1a48-128">完成向导对话框：</span><span class="sxs-lookup"><span data-stu-id="e1a48-128">Complete the wizard dialogs:</span></span>  
  
    -   [<span data-ttu-id="e1a48-129">“简介”页</span><span class="sxs-lookup"><span data-stu-id="e1a48-129">Introduction Page</span></span>](#Introduction)  
  
    -   [<span data-ttu-id="e1a48-130">“导出设置”页</span><span class="sxs-lookup"><span data-stu-id="e1a48-130">Export Settings Page</span></span>](#Export_settings)  
  
    -   [<span data-ttu-id="e1a48-131">“验证”页</span><span class="sxs-lookup"><span data-stu-id="e1a48-131">Validation Page</span></span>](#Validation)  
  
    -   [<span data-ttu-id="e1a48-132">摘要页</span><span class="sxs-lookup"><span data-stu-id="e1a48-132">Summary Page</span></span>](#Summary)  
  
    -   [<span data-ttu-id="e1a48-133">进度页面</span><span class="sxs-lookup"><span data-stu-id="e1a48-133">Progress Page</span></span>](#Progress)  
  
    -   [<span data-ttu-id="e1a48-134">“结果”页</span><span class="sxs-lookup"><span data-stu-id="e1a48-134">Results Page</span></span>](#Results)  
  
##  <a name="introduction-page"></a><a name="Introduction"></a> <span data-ttu-id="e1a48-135">“简介”页</span><span class="sxs-lookup"><span data-stu-id="e1a48-135">Introduction Page</span></span>  
 <span data-ttu-id="e1a48-136">此页介绍“导出数据层应用程序向导”的各个步骤。</span><span class="sxs-lookup"><span data-stu-id="e1a48-136">This page describes the steps for the Export Data-tier Application Wizard.</span></span>  
  
 <span data-ttu-id="e1a48-137">**选项**</span><span class="sxs-lookup"><span data-stu-id="e1a48-137">**Options**</span></span>  
  
 <span data-ttu-id="e1a48-138">**不再显示此页。**</span><span class="sxs-lookup"><span data-stu-id="e1a48-138">**Do not show this page again.**</span></span> <span data-ttu-id="e1a48-139">- 选中此复选框可以停止在将来显示“简介”页。</span><span class="sxs-lookup"><span data-stu-id="e1a48-139">- Click the check box to stop the Introduction page from being displayed in the future.</span></span>  
  
 <span data-ttu-id="e1a48-140">**下一步** - 继续到“选择 DAC 包”\*\*\*\* 页。</span><span class="sxs-lookup"><span data-stu-id="e1a48-140">**Next** - Proceeds to the **Select DAC Package** page.</span></span>  
  
 <span data-ttu-id="e1a48-141">**取消**-取消操作并关闭向导。</span><span class="sxs-lookup"><span data-stu-id="e1a48-141">**Cancel** - Cancels the operation and closes the Wizard.</span></span>  
  
##  <a name="export-settings-page"></a><a name="Export_settings"></a><span data-ttu-id="e1a48-142">"导出设置" 页</span><span class="sxs-lookup"><span data-stu-id="e1a48-142">Export Settings Page</span></span>  
 <span data-ttu-id="e1a48-143">使用此页可以指定要创建 BACPAC 文件的位置。</span><span class="sxs-lookup"><span data-stu-id="e1a48-143">Use this page to specify the location where you want the BACPAC file to be created.</span></span>  
  
-   <span data-ttu-id="e1a48-144">**保存到本地磁盘** - 在本地计算机上的目录中创建 BACPAC 文件。</span><span class="sxs-lookup"><span data-stu-id="e1a48-144">**Save to local disk** - Creates a BACPAC file in a directory on the local computer.</span></span> <span data-ttu-id="e1a48-145">单击“浏览…”以导航本地计算机，或在提供的空间中指定路径\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e1a48-145">Click **Browse...** to navigate the local computer, or specify the path in the space provided.</span></span> <span data-ttu-id="e1a48-146">路径名必须包含文件名和 .bacpac 扩展名。</span><span class="sxs-lookup"><span data-stu-id="e1a48-146">The path name must include a file name and the .bacpac extension.</span></span>  
  
-   <span data-ttu-id="e1a48-147">**保存到 Azure** - 在 Azure 容器中创建 BACPAC 文件。</span><span class="sxs-lookup"><span data-stu-id="e1a48-147">**Save to Azure** - Creates a BACPAC file in an Azure container.</span></span> <span data-ttu-id="e1a48-148">若要验证此选项，则必须连接到 Azure 容器。</span><span class="sxs-lookup"><span data-stu-id="e1a48-148">You must connect to an Azure container in order to validate this option.</span></span> <span data-ttu-id="e1a48-149">请注意，此选项还要求您为临时文件指定一个本地目录。</span><span class="sxs-lookup"><span data-stu-id="e1a48-149">Note that this option also requires that you specify a local directory for the temporary file.</span></span> <span data-ttu-id="e1a48-150">请注意，将在指定位置创建临时文件，并且在操作完成后，临时文件将保留在该位置。</span><span class="sxs-lookup"><span data-stu-id="e1a48-150">Note that the temporary file will be created at the specified location and will remain there after the operation completes.</span></span>  
  
 <span data-ttu-id="e1a48-151">若要指定要导出的表的子集，请使用 **“高级”** 选项。</span><span class="sxs-lookup"><span data-stu-id="e1a48-151">To specify a subset of tables to export, use the **Advanced** option.</span></span>  
  
##  <a name="validation-page"></a><a name="Validation"></a><span data-ttu-id="e1a48-152">验证页</span><span class="sxs-lookup"><span data-stu-id="e1a48-152">Validation Page</span></span>  
 <span data-ttu-id="e1a48-153">使用验证页可查看阻止操作的任何问题。</span><span class="sxs-lookup"><span data-stu-id="e1a48-153">Use the validation page to review any issues that block the operation.</span></span> <span data-ttu-id="e1a48-154">若要继续，请解决阻止问题，然后单击“重新运行验证”\*\*\*\* 确保验证成功。</span><span class="sxs-lookup"><span data-stu-id="e1a48-154">To continue, resolve blocking issues and then click **Re-run Validation** to ensure that validation is successful.</span></span>  
  
 <span data-ttu-id="e1a48-155">若要继续，请单击 **“下一步”** 。</span><span class="sxs-lookup"><span data-stu-id="e1a48-155">To continue, click **Next**.</span></span>  
  
##  <a name="summary-page"></a><a name="Summary"></a> <span data-ttu-id="e1a48-156">摘要页</span><span class="sxs-lookup"><span data-stu-id="e1a48-156">Summary Page</span></span>  
 <span data-ttu-id="e1a48-157">使用此页可查看操作的指定的源和目标设置。</span><span class="sxs-lookup"><span data-stu-id="e1a48-157">Use this page to review the specified source and target settings for the operation.</span></span> <span data-ttu-id="e1a48-158">若要使用指定设置完成导出操作，请单击 **“完成”**。</span><span class="sxs-lookup"><span data-stu-id="e1a48-158">To complete the export operation using the specified settings, click **Finish**.</span></span> <span data-ttu-id="e1a48-159">若要取消导出操作并退出向导，请单击 **“取消”**。</span><span class="sxs-lookup"><span data-stu-id="e1a48-159">To cancel the export operation and exit the Wizard, click **Cancel**.</span></span>  
  
##  <a name="progress-page"></a><a name="Progress"></a> <span data-ttu-id="e1a48-160">“进度”页</span><span class="sxs-lookup"><span data-stu-id="e1a48-160">Progress Page</span></span>  
 <span data-ttu-id="e1a48-161">此页将显示一个指示操作状态的进度栏。</span><span class="sxs-lookup"><span data-stu-id="e1a48-161">This page displays a progress bar that indicates the status of the operation.</span></span> <span data-ttu-id="e1a48-162">若要查看详细状态，请单击 **“查看详细信息”** 选项。</span><span class="sxs-lookup"><span data-stu-id="e1a48-162">To view detailed status, click the **View details** option.</span></span>  
  
##  <a name="results-page"></a><a name="Results"></a><span data-ttu-id="e1a48-163">结果页</span><span class="sxs-lookup"><span data-stu-id="e1a48-163">Results Page</span></span>  
 <span data-ttu-id="e1a48-164">此页将报告导出操作是成功还是失败，并显示每个操作的结果。</span><span class="sxs-lookup"><span data-stu-id="e1a48-164">This page reports the success or failure of the export operation, showing the results of each action.</span></span> <span data-ttu-id="e1a48-165">遇到了错误的任何操作都将在 **“结果”** 列中具有一个链接。</span><span class="sxs-lookup"><span data-stu-id="e1a48-165">Any action that encountered an error will have a link in the **Result** column.</span></span> <span data-ttu-id="e1a48-166">单击该链接可以查看针对该操作的错误报告。</span><span class="sxs-lookup"><span data-stu-id="e1a48-166">Click the link to view a report of the error for that action.</span></span>  
  
 <span data-ttu-id="e1a48-167">单击 "**完成**" 关闭向导。</span><span class="sxs-lookup"><span data-stu-id="e1a48-167">Click **Finish** to close the Wizard.</span></span>  
  
##  <a name="using-a-net-framework-application"></a><a name="NetApp"></a><span data-ttu-id="e1a48-168">使用 .Net Framework 应用程序</span><span class="sxs-lookup"><span data-stu-id="e1a48-168">Using a .Net Framework Application</span></span>  
 <span data-ttu-id="e1a48-169">**使用 .Net Framework 应用程序中的 Export() 方法导出 DAC。**</span><span class="sxs-lookup"><span data-stu-id="e1a48-169">**To export a DAC using the Export() method in a .Net Framework application.**</span></span>  
  
 <span data-ttu-id="e1a48-170">若要查看代码示例，请下载有关 [Codeplex](https://go.microsoft.com/fwlink/?LinkId=219575)的 DAC 示例应用程序</span><span class="sxs-lookup"><span data-stu-id="e1a48-170">To view a code example, download the DAC sample application on [Codeplex](https://go.microsoft.com/fwlink/?LinkId=219575)</span></span>  
  
1.  <span data-ttu-id="e1a48-171">创建一个 SMO Server 对象，并且将该对象设置为包含要导出的 DAC 的实例。</span><span class="sxs-lookup"><span data-stu-id="e1a48-171">Create a SMO Server object and set it to the instance that contains the DAC to be exported.</span></span>  
  
2.  <span data-ttu-id="e1a48-172">打开 `ServerConnection` 对象，并连接到同一实例。</span><span class="sxs-lookup"><span data-stu-id="e1a48-172">Open a `ServerConnection` object and connect to the same instance.</span></span>  
  
3.  <span data-ttu-id="e1a48-173">使用 `Export` 类型的 `Microsoft.SqlServer.Management.Dac.DacStore` 方法导出 DAC。</span><span class="sxs-lookup"><span data-stu-id="e1a48-173">Use the `Export` method of the `Microsoft.SqlServer.Management.Dac.DacStore` type to export the DAC.</span></span> <span data-ttu-id="e1a48-174">指定要导出的 DAC 的名称以及指向将用于放置导出文件的文件夹的路径。</span><span class="sxs-lookup"><span data-stu-id="e1a48-174">Specify the name of the DAC to be exported, and the path to the folder where the export file is to be placed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1a48-175">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e1a48-175">See Also</span></span>  
 <span data-ttu-id="e1a48-176">[数据层应用程序](data-tier-applications.md) </span><span class="sxs-lookup"><span data-stu-id="e1a48-176">[Data-tier Applications](data-tier-applications.md) </span></span>  
 [<span data-ttu-id="e1a48-177">从数据库中提取 DAC</span><span class="sxs-lookup"><span data-stu-id="e1a48-177">Extract a DAC From a Database</span></span>](extract-a-dac-from-a-database.md)  
  
  
