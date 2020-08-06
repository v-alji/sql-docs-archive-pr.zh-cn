---
title: 从数据库中提取 DAC | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.extractdacwizard.buildandsave.f1
- sql12.swb.extractdacwizard.setdacproperties.f1
- sql12.swb.extractdacwizard.validationandsummary.f1
- sql12.swb.extractdacwizard.introduction.f1
- sql12.swb.extractdacwizard.selectdatapage.f1
helpviewer_keywords:
- extract DAC
- How to [DAC], extract
- data-tier application [SQL Server], extract
- wizard [DAC], extract
ms.assetid: ae52a723-91c4-43fd-bcc7-f8de1d1f90e5
author: stevestein
ms.author: sstein
ms.openlocfilehash: bd024af9c201563773e20bae7e5fded1985abbe1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590866"
---
# <a name="extract-a-dac-from-a-database"></a><span data-ttu-id="c5438-102">从数据库中提取 DAC</span><span class="sxs-lookup"><span data-stu-id="c5438-102">Extract a DAC From a Database</span></span>
  <span data-ttu-id="c5438-103">使用“提取数据层应用程序向导”  或 Windows PowerShell 脚本可以从现有 SQL Server 数据库提取数据层应用程序 (DAC) 包。</span><span class="sxs-lookup"><span data-stu-id="c5438-103">Use either the **Extract Data-tier Application Wizard** or a Windows PowerShell script to extract a data-tier application (DAC) package from an existing SQL Server database.</span></span> <span data-ttu-id="c5438-104">提取过程将创建一个 DAC 包文件，其中包含数据库对象及其相关实例级别元素的定义。</span><span class="sxs-lookup"><span data-stu-id="c5438-104">The extraction process creates a DAC package file that contains definitions of the database objects and their related instance-level elements.</span></span> <span data-ttu-id="c5438-105">例如，一个 DAC 包文件包含数据库表、存储过程、视图、用户以及映射到数据库用户的登录名。</span><span class="sxs-lookup"><span data-stu-id="c5438-105">For example, a DAC package file contains the database tables, stored procedures, views, and users, along with the logins that map to the database users.</span></span>  
  
-   <span data-ttu-id="c5438-106">**开始之前：** [限制和局限](#LimitationsRestrictions)、[权限](#Permissions)</span><span class="sxs-lookup"><span data-stu-id="c5438-106">**Before you begin:**  [Limitations and Restrictions](#LimitationsRestrictions), [Permissions](#Permissions)</span></span>  
  
-   <span data-ttu-id="c5438-107">**若要提取 DAC，请使用：**  [提取数据层应用程序向导](#UsingDACExtractWizard)、 [PowerShell](#ExtractDACPowerShell)</span><span class="sxs-lookup"><span data-stu-id="c5438-107">**To extract a DAC, using:**  [The Extract Data-tier Application Wizard](#UsingDACExtractWizard), [PowerShell](#ExtractDACPowerShell)</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="c5438-108">开始之前</span><span class="sxs-lookup"><span data-stu-id="c5438-108">Before You Begin</span></span>  
 <span data-ttu-id="c5438-109">您可以从驻留在 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]或者 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] Service Pack 4 或更高版本的实例上的数据库中提取 DAC。</span><span class="sxs-lookup"><span data-stu-id="c5438-109">You can extract a DAC from databases residing on instances of [!INCLUDE[ssSDS](../../includes/sssds-md.md)], or [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] Service Pack 4 or later.</span></span> <span data-ttu-id="c5438-110">如果对已从 DAC 部署的数据库运行提取进程，则仅提取数据库中对象的定义。</span><span class="sxs-lookup"><span data-stu-id="c5438-110">If the extraction process is run against a database that was deployed from a DAC, only the definitions of the objects in the database are extracted.</span></span> <span data-ttu-id="c5438-111">该进程不引用在 `msdb`) 中 (**master**注册的 DAC [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="c5438-111">The process does not reference the DAC registered in `msdb` (**master** in [!INCLUDE[ssSDS](../../includes/sssds-md.md)]).</span></span> <span data-ttu-id="c5438-112">该提取进程不注册当前数据库引擎实例中的 DAC 定义。</span><span class="sxs-lookup"><span data-stu-id="c5438-112">The extraction process does not register the DAC definition in the current instance of the Database Engine.</span></span> <span data-ttu-id="c5438-113">有关注册 DAC 的详细信息，请参阅 [Register a Database As a DAC](register-a-database-as-a-dac.md)。</span><span class="sxs-lookup"><span data-stu-id="c5438-113">For more information about registering a DAC, see [Register a Database As a DAC](register-a-database-as-a-dac.md).</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> <span data-ttu-id="c5438-114">限制和局限</span><span class="sxs-lookup"><span data-stu-id="c5438-114">Limitations and Restrictions</span></span>  
 <span data-ttu-id="c5438-115">只能从 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]、 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 4 (SP4) 或更高版本的数据库中提取 DAC。</span><span class="sxs-lookup"><span data-stu-id="c5438-115">A DAC can only be extracted from a database in [!INCLUDE[ssSDS](../../includes/sssds-md.md)], or [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 4 (SP4) or later.</span></span> <span data-ttu-id="c5438-116">如果数据库有 DAC 中不支持的对象或包含的用户，则不能提取 DAC。</span><span class="sxs-lookup"><span data-stu-id="c5438-116">You cannot extract a DAC if the database has objects that are not supported in a DAC, or contained users.</span></span> <span data-ttu-id="c5438-117">有关 DAC 中支持的对象类型的详细信息，请参阅 [DAC Support For SQL Server Objects and Versions](dac-support-for-sql-server-objects-and-versions.md)。</span><span class="sxs-lookup"><span data-stu-id="c5438-117">For more information about the types of objects supported in a DAC, see [DAC Support For SQL Server Objects and Versions](dac-support-for-sql-server-objects-and-versions.md).</span></span>  
  
###  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="c5438-118">权限</span><span class="sxs-lookup"><span data-stu-id="c5438-118">Permissions</span></span>  
 <span data-ttu-id="c5438-119">提取 DAC 至少要求 ALTER ANY LOGIN 和数据库作用域 VIEW DEFINITION 权限，以及对 **sys.sql_expression_dependencies**具有 SELECT 权限。</span><span class="sxs-lookup"><span data-stu-id="c5438-119">Extracting a DAC requires at least ALTER ANY LOGIN and database scope VIEW DEFINITION permissions, as well as SELECT permissions on **sys.sql_expression_dependencies**.</span></span> <span data-ttu-id="c5438-120">提取 DAC 可由 securityadmin 固定服务器角色的成员（也是从其提取 DAC 的数据库中 database_owner 固定数据库角色的成员）完成。</span><span class="sxs-lookup"><span data-stu-id="c5438-120">Extracting a DAC can be done by members of the securityadmin fixed server role who are also members of the database_owner fixed database role in the database from which the DAC is extracted.</span></span> <span data-ttu-id="c5438-121">sysadmin 固定服务器角色的成员或名为 **sa** 的内置 SQL Server 系统管理员帐户也可以提取 DAC。</span><span class="sxs-lookup"><span data-stu-id="c5438-121">Members of the sysadmin fixed server role or the built-in SQL Server system administrator account named **sa** can also extract a DAC.</span></span>  
  
##  <a name="using-the-extract-data-tier-application-wizard"></a><a name="UsingDACExtractWizard"></a><span data-ttu-id="c5438-122">使用 "提取数据层应用程序向导"</span><span class="sxs-lookup"><span data-stu-id="c5438-122">Using the Extract Data-tier Application Wizard</span></span>  
 <span data-ttu-id="c5438-123">**使用向导提取 DAC**</span><span class="sxs-lookup"><span data-stu-id="c5438-123">**To Extract a DAC Using a Wizard**</span></span>  
  
1.  <span data-ttu-id="c5438-124">在 **“对象资源管理器”** 中，展开包含要从其提取 DAC 的数据库的实例的节点。</span><span class="sxs-lookup"><span data-stu-id="c5438-124">In **Object Explorer**, expand the node for the instance containing the database from which the DAC is to be extracted.</span></span>  
  
2.  <span data-ttu-id="c5438-125">展开 **“数据库”** 节点。</span><span class="sxs-lookup"><span data-stu-id="c5438-125">Expand the **Databases** node.</span></span>  
  
3.  <span data-ttu-id="c5438-126">右键单击要从其提取 DAC 的数据库的节点，指向“任务”，然后选择“提取数据层应用程序…”\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="c5438-126">Right-click the node for the database from which the DAC is to be extracted, point to **Tasks**, and then select **Extract Data-tier Application...**</span></span>  
  
4.  <span data-ttu-id="c5438-127">完成向导对话框：</span><span class="sxs-lookup"><span data-stu-id="c5438-127">Complete the wizard dialogs:</span></span>  
  
    1.  [<span data-ttu-id="c5438-128">“简介”页</span><span class="sxs-lookup"><span data-stu-id="c5438-128">Introduction Page</span></span>](#Introduction)  
  
    2.  [<span data-ttu-id="c5438-129">“选择数据”页</span><span class="sxs-lookup"><span data-stu-id="c5438-129">Select Data Page</span></span>](#SelectData)  
  
    3.  [<span data-ttu-id="c5438-130">“设置属性”页</span><span class="sxs-lookup"><span data-stu-id="c5438-130">Set Properties Page</span></span>](#SetProperties)  
  
    4.  [<span data-ttu-id="c5438-131">“验证和摘要”页</span><span class="sxs-lookup"><span data-stu-id="c5438-131">Validation and Summary Page</span></span>](#ValidateSummary)  
  
    5.  [<span data-ttu-id="c5438-132">“生成包”页</span><span class="sxs-lookup"><span data-stu-id="c5438-132">Build Package Page</span></span>](#BuildPackage)  
  
###  <a name="introduction-page"></a><a name="Introduction"></a> <span data-ttu-id="c5438-133">“简介”页</span><span class="sxs-lookup"><span data-stu-id="c5438-133">Introduction Page</span></span>  
 <span data-ttu-id="c5438-134">此页描述用于提取数据层应用程序的各个步骤。</span><span class="sxs-lookup"><span data-stu-id="c5438-134">This page describes the steps for extracting a data-tier application.</span></span>  
  
 <span data-ttu-id="c5438-135">**不再显示此页。**</span><span class="sxs-lookup"><span data-stu-id="c5438-135">**Do not show this page again.**</span></span> <span data-ttu-id="c5438-136">- 选中该复选框可以停止在将来显示此页。</span><span class="sxs-lookup"><span data-stu-id="c5438-136">- Click the check box to stop the page from being displayed in the future.</span></span>  
  
 <span data-ttu-id="c5438-137">“下一步 >”\*\*\*\* - 进入“选择方法”\*\*\*\* 页。</span><span class="sxs-lookup"><span data-stu-id="c5438-137">**Next >** - Proceeds to the **Choose Method** page.</span></span>  
  
 <span data-ttu-id="c5438-138">**取消** - 结束向导且不从数据层提取数据层应用程序。</span><span class="sxs-lookup"><span data-stu-id="c5438-138">**Cancel** - Ends the wizard without extracting a data-tier application from the database.</span></span>  
  
###  <a name="select-data-page"></a><a name="SelectData"></a><span data-ttu-id="c5438-139">选择数据页</span><span class="sxs-lookup"><span data-stu-id="c5438-139">Select Data Page</span></span>  
 <span data-ttu-id="c5438-140">使用向导的此页可以选择要包括在数据层应用程序 (DAC) 包文件中的引用数据。</span><span class="sxs-lookup"><span data-stu-id="c5438-140">Use this page of the wizard to select the reference data that you want to include in your data-tier application (DAC) package file.</span></span> <span data-ttu-id="c5438-141">在 DAC 包中包括数据是可选的。</span><span class="sxs-lookup"><span data-stu-id="c5438-141">Including data in your DAC package is optional.</span></span> <span data-ttu-id="c5438-142">DAC 包将已包括与数据库相关的所有受支持的数据库对象和实例对象的架构。</span><span class="sxs-lookup"><span data-stu-id="c5438-142">The DAC package will already include the schema of all supported database objects and instance objects related to your database.</span></span>  
  
 <span data-ttu-id="c5438-143">您可以在 DAC 包文件中包含多达 10 MB 的引用数据。</span><span class="sxs-lookup"><span data-stu-id="c5438-143">You can include up to 10 MB of reference data in your DAC package file.</span></span> <span data-ttu-id="c5438-144">但是，对于要包含在该 DAC 中的表，它们可能不包含二进制大型对象 (BLOB) 数据类型（如 **image** 或 **varchar(max)**）。</span><span class="sxs-lookup"><span data-stu-id="c5438-144">However, for tables to be included in the DAC, they may not contain binary large object (BLOB) data types such as **image** or **varchar(max)**.</span></span> <span data-ttu-id="c5438-145">若要提取大量数据以转移到另一个数据库，应使用 SQL Server Integration Services、大容量复制实用工具或许多其他数据迁移方法之一。</span><span class="sxs-lookup"><span data-stu-id="c5438-145">To extract larger amounts of data for transferring to another database, use SQL Server Integration Services, the bulk copy utility, or one of many other data migration techniques.</span></span>  
  
 <span data-ttu-id="c5438-146">**数据库表** - 对于包含你要包括在 DAC 包中的数据的数据库表，在其旁边选中对应的复选框。</span><span class="sxs-lookup"><span data-stu-id="c5438-146">**Database table** - Select the check box next to the database tables which contain the data that you want to include in your DAC package.</span></span> <span data-ttu-id="c5438-147">您最多可以选择十个表，这些表中具有 10,000 行或更少的行。</span><span class="sxs-lookup"><span data-stu-id="c5438-147">You can select up to ten tables that have 10,000 rows or less.</span></span>  
  
###  <a name="set-properties-page"></a><a name="SetProperties"></a> <span data-ttu-id="c5438-148">“设置属性”页</span><span class="sxs-lookup"><span data-stu-id="c5438-148">Set Properties Page</span></span>  
 <span data-ttu-id="c5438-149">使用该向导页描述数据层应用程序 (DAC)。</span><span class="sxs-lookup"><span data-stu-id="c5438-149">Use this page of the wizard to describe the data-tier application (DAC).</span></span> <span data-ttu-id="c5438-150">这些属性用于标识 DAC，并有助于与其他应用程序区分开。</span><span class="sxs-lookup"><span data-stu-id="c5438-150">These properties are used to identify the DAC and help distinguish it from others.</span></span>  
  
 <span data-ttu-id="c5438-151">**名称** - 此名称标识 DAC。</span><span class="sxs-lookup"><span data-stu-id="c5438-151">**Name** - This name identifies the DAC.</span></span> <span data-ttu-id="c5438-152">它可以不同于 DAC 包文件的名称，并且应描述您的应用程序。</span><span class="sxs-lookup"><span data-stu-id="c5438-152">It can be different than the name of the DAC package file and should describe your application.</span></span> <span data-ttu-id="c5438-153">例如，如果数据库用于财务应用程序，则可能要命名为“DAC Finance”。</span><span class="sxs-lookup"><span data-stu-id="c5438-153">For example, if the database is used for a finance application, you may wish to name the DAC Finance.</span></span>  
  
 <span data-ttu-id="c5438-154">**版本（使用 xx.xx.xx.xx，其中 x 是数字）** - 标识 DAC 版本的数值。</span><span class="sxs-lookup"><span data-stu-id="c5438-154">**Version (use xx.xx.xx.xx, where x is a number)** - A numeric value that identifies the version of the DAC.</span></span> <span data-ttu-id="c5438-155">该 DAC 版本用于 Visual Studio 中，以便标识开发人员正在处理的 DAC 的版本。</span><span class="sxs-lookup"><span data-stu-id="c5438-155">The DAC version is used in Visual Studio to identify the version of the DAC that developers are working on.</span></span> <span data-ttu-id="c5438-156">部署 DAC 时，该版本存储在数据库中， `msdb` 并且以后可以在中的 "**数据层应用程序**" 节点下查看 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="c5438-156">When deploying a DAC, the version is stored in the `msdb` database and can later be viewed under the **Data-tier Applications** node in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="c5438-157">**说明：** - 可选。</span><span class="sxs-lookup"><span data-stu-id="c5438-157">**Description:** - Optional.</span></span> <span data-ttu-id="c5438-158">说明该 DAC。</span><span class="sxs-lookup"><span data-stu-id="c5438-158">Describes the DAC.</span></span> <span data-ttu-id="c5438-159">部署 DAC 时，说明存储在数据库中， `msdb` 并且以后可以在中的 "**数据层应用程序**" 节点下查看 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="c5438-159">When deploying a DAC, the description is stored in the `msdb` database and can later be viewed under the **Data-tier Applications** node in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span>  
  
 <span data-ttu-id="c5438-160">**保存到 DAC 包文件(文件名中包括 .dacpac 扩展名)：** - 将 DAC 保存到某一 DAC 包文件，并且具有 .dacpac 扩展名。</span><span class="sxs-lookup"><span data-stu-id="c5438-160">**Save to DAC package file (include .dacpac extension with file name):** - Saves the DAC to a DAC package file, with a .dacpac extension.</span></span> <span data-ttu-id="c5438-161">单击 **“浏览”** 按钮可以指定文件的名称和位置。</span><span class="sxs-lookup"><span data-stu-id="c5438-161">Click the **Browse** button to specify a name and location for the file.</span></span>  
  
 <span data-ttu-id="c5438-162">**覆盖现有文件** - 如果已存在同名的 DAC 包文件，则选中此复选框可以替换该文件。</span><span class="sxs-lookup"><span data-stu-id="c5438-162">**Overwrite existing file** - Select this check box to replace the DAC package file if one already exists with the same name.</span></span>  
  
###  <a name="validation-and-summary-page"></a><a name="ValidateSummary"></a> <span data-ttu-id="c5438-163">“验证和摘要”页</span><span class="sxs-lookup"><span data-stu-id="c5438-163">Validation and Summary Page</span></span>  
 <span data-ttu-id="c5438-164">在此页上，该向导将验证数据层应用程序 (DAC) 是否支持所有数据库对象。</span><span class="sxs-lookup"><span data-stu-id="c5438-164">On this page, the wizard validates that all database objects are supported by a data-tier application (DAC).</span></span> <span data-ttu-id="c5438-165">它还检查数据库对象之间的依赖关系，以便确定该组对象是否可以成功包括在 DAC 中。</span><span class="sxs-lookup"><span data-stu-id="c5438-165">It also checks dependencies across database objects to determine the set of objects that can be successfully included in the DAC.</span></span> <span data-ttu-id="c5438-166">之后，它将显示一个验证报表，汇总您在此向导中选择的选项。</span><span class="sxs-lookup"><span data-stu-id="c5438-166">After that, it displays the validation report and summarizes the options that you have selected in this wizard.</span></span> <span data-ttu-id="c5438-167">若要更改某个选项，请单击 **“上一步”** 。</span><span class="sxs-lookup"><span data-stu-id="c5438-167">To change an option, click **Previous**.</span></span> <span data-ttu-id="c5438-168">若要开始提取 DAC，请单击 **“下一步”** 。</span><span class="sxs-lookup"><span data-stu-id="c5438-168">To begin extracting a DAC, click **Next**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c5438-169">如果 DAC 不支持一个或多个对象，则 **“下一步”** 按钮将被禁用，并且提取过程可能会停止。</span><span class="sxs-lookup"><span data-stu-id="c5438-169">If one or more objects are not supported by a DAC, then the **Next** button is disabled and the extraction process may not continue.</span></span> <span data-ttu-id="c5438-170">在这样的情况下，建议删除不支持的对象，然后再次运行此向导。</span><span class="sxs-lookup"><span data-stu-id="c5438-170">In such cases, it is recommended to remove the non-supported objects and then run this wizard again.</span></span>  
  
 <span data-ttu-id="c5438-171">**摘要** - 你已选择的选项的摘要在“DAC 属性”  下列出。</span><span class="sxs-lookup"><span data-stu-id="c5438-171">**Summary** - A summary of the options you have selected are listed under **DAC properties**.</span></span> <span data-ttu-id="c5438-172">验证的结果在 **“DAC 对象”** 下列出。</span><span class="sxs-lookup"><span data-stu-id="c5438-172">The results of the validation are listed under **DAC objects**.</span></span> <span data-ttu-id="c5438-173">有三种类型的验证结果：</span><span class="sxs-lookup"><span data-stu-id="c5438-173">There are three types of results from the validation:</span></span>  
  
-   <span data-ttu-id="c5438-174">**对象成功包括在 DAC 中**：支持这些对象及其依赖关系，并且它们可以成功包括在 DAC 中。</span><span class="sxs-lookup"><span data-stu-id="c5438-174">**Objects included in DAC successfully**: these objects and their dependencies are supported, and can be included in the DAC successfully.</span></span>  
  
-   <span data-ttu-id="c5438-175">**对象包括在 DAC 中但具有警告**：支持这些对象，但依赖于在 DAC 中不支持的其他对象。</span><span class="sxs-lookup"><span data-stu-id="c5438-175">**Objects included in DAC with warnings**: these objects are supported, but depend on other objects that are not supported in a DAC.</span></span>  
  
-   <span data-ttu-id="c5438-176">**对象不包括在 DAC 中**：不支持这些对象，并且这些对象必须从数据库中删除后才能成功提取 DAC。</span><span class="sxs-lookup"><span data-stu-id="c5438-176">**Objects not included in DAC**: these objects are not supported and must be removed from the database before successfully extracting a DAC.</span></span>  
  
 <span data-ttu-id="c5438-177">验证过程将检查多个级别的依赖关系。</span><span class="sxs-lookup"><span data-stu-id="c5438-177">The validation process checks multiple levels of dependencies.</span></span> <span data-ttu-id="c5438-178">例如，如果某一存储过程依赖于使用不支持的 CLR 数据类型的表，则该存储过程将在 **“对象包括在 DAC 中但具有警告”** 下列出。</span><span class="sxs-lookup"><span data-stu-id="c5438-178">For example, if a stored procedure depends on a table that uses the unsupported CLR data type, the stored procedure will be listed under **Objects included in DAC with warnings**.</span></span>  
  
 <span data-ttu-id="c5438-179">如果 DAC 不支持一个或多个对象，则 **“下一步”** 按钮将被禁用，并且提取过程将停止。</span><span class="sxs-lookup"><span data-stu-id="c5438-179">If one or more objects are not supported by a DAC, then the **Next** button is disabled and the extraction process will not continue.</span></span> <span data-ttu-id="c5438-180">在这样的情况下，建议删除不支持的对象，然后再次运行此向导。</span><span class="sxs-lookup"><span data-stu-id="c5438-180">In such cases, it is recommended to remove the objects that are not supported and then run this wizard again.</span></span>  
  
 <span data-ttu-id="c5438-181">**保存报告** - 使你可以保存一个基于 HTML 的文件，该文件列出摘要中“DAC 对象”  节点下的所有对象。</span><span class="sxs-lookup"><span data-stu-id="c5438-181">**Save Report** - Enables you to save an HTML-based file that lists all of the objects under the **DAC Objects** node in the summary.</span></span> <span data-ttu-id="c5438-182">当在 DAC 中不支持您的一些数据库对象时，此报表可能会非常有用。</span><span class="sxs-lookup"><span data-stu-id="c5438-182">This report can be useful when some of your database objects are not supported in a DAC.</span></span> <span data-ttu-id="c5438-183">使用此报表可以在尝试再次提取 DAC 前更改或删除不支持的对象。</span><span class="sxs-lookup"><span data-stu-id="c5438-183">Use the report to change or remove objects that are not supported, before trying to extract the DAC again.</span></span>  
  
###  <a name="build-package-page"></a><a name="BuildPackage"></a><span data-ttu-id="c5438-184">"生成包" 页</span><span class="sxs-lookup"><span data-stu-id="c5438-184">Build Package Page</span></span>  
 <span data-ttu-id="c5438-185">使用该页监视向导在提取数据层应用程序 (DAC) 时的进度。</span><span class="sxs-lookup"><span data-stu-id="c5438-185">Use this page to monitor the progress of the wizard as it extracts the data-tier application (DAC).</span></span>  
  
 <span data-ttu-id="c5438-186">**操作** - 在“创建并保存 DAC 包文件”  操作期间，向导从你的 SQL Server 数据库提取 DAC。</span><span class="sxs-lookup"><span data-stu-id="c5438-186">**Action** - During the **Create and save DAC package file** action, the wizard extracts a DAC from your SQL Server database.</span></span> <span data-ttu-id="c5438-187">然后，一个 DAC 包将在内存中创建并保存到您指定的位置中。</span><span class="sxs-lookup"><span data-stu-id="c5438-187">Then, a DAC package is created in memory and saved to the location you specified.</span></span> <span data-ttu-id="c5438-188">单击 **“结果”** 列中的链接可以查看相应步骤的结果。</span><span class="sxs-lookup"><span data-stu-id="c5438-188">Click on the links in the **Result** column to see the outcome of the corresponding step.</span></span>  
  
 <span data-ttu-id="c5438-189">**保存报告** - 单击此项可将向导的进度结果保存到文件中。</span><span class="sxs-lookup"><span data-stu-id="c5438-189">**Save Report** - Click to save the results of the wizard's progress to a file.</span></span>  
  
 <span data-ttu-id="c5438-190">“完成”  - 单击此项可在完成处理后或出错时关闭向导。</span><span class="sxs-lookup"><span data-stu-id="c5438-190">**Finish** - Click to close the wizard after processing has completed, or if an error occurs.</span></span>  
  
##  <a name="extract-a-dac-using-powershell"></a><a name="ExtractDACPowerShell"></a><span data-ttu-id="c5438-191">使用 PowerShell 提取 DAC</span><span class="sxs-lookup"><span data-stu-id="c5438-191">Extract a DAC Using PowerShell</span></span>  
 <span data-ttu-id="c5438-192">**使用 PowerShell 脚本中的 Extract() 方法从数据库提取 DAC**</span><span class="sxs-lookup"><span data-stu-id="c5438-192">**To extract a DAC from a database using the Extract() method in a PowerShell script**</span></span>  
  
1.  <span data-ttu-id="c5438-193">创建一个 SMO Server 对象，并且将其设置为包含要从其提取 DAC 的数据库的实例。</span><span class="sxs-lookup"><span data-stu-id="c5438-193">Create a SMO Server object and set it to the instance that contains the database from which the DAC is to be extracted.</span></span>  
  
2.  <span data-ttu-id="c5438-194">添加一个指定数据库名称的变量。</span><span class="sxs-lookup"><span data-stu-id="c5438-194">Add a variable that specifies the name of the database.</span></span>  
  
3.  <span data-ttu-id="c5438-195">指定 DAC 的元数据，如 DAC 名称、版本和说明。</span><span class="sxs-lookup"><span data-stu-id="c5438-195">Specify the metadata for the DAC, such as the DAC name, version, and description.</span></span>  
  
4.  <span data-ttu-id="c5438-196">为提取的 DAC 包文件指定路径和文件名。</span><span class="sxs-lookup"><span data-stu-id="c5438-196">Specify the path and file name for the extracted DAC package file.</span></span>  
  
5.  <span data-ttu-id="c5438-197">使用上面指定的信息运行 Extract 方法。</span><span class="sxs-lookup"><span data-stu-id="c5438-197">Run the Extract method with the information specified above.</span></span>  
  
### <a name="example-powershell"></a><span data-ttu-id="c5438-198">示例 (PowerShell)</span><span class="sxs-lookup"><span data-stu-id="c5438-198">Example (PowerShell)</span></span>  
 <span data-ttu-id="c5438-199">下面的示例从名为 MyDB 的数据库中提取名为 MyApplication 的 DAC。</span><span class="sxs-lookup"><span data-stu-id="c5438-199">The following example extracts a DAC named MyApplication from a database named MyDB.</span></span>  
  
```powershell
## Set a SMO Server object to the default instance on the local computer.  
CD SQLSERVER:\SQL\localhost\DEFAULT  
$srv = Get-Item .  
  
## Specify the database to extract to a DAC.  
$dbname = "MyDB"  
  
## Specify the DAC metadata.  
$applicationname = "MyApplication"  
$version = "1.0.0.0"  
$description = "This DAC defines the database used by my application."  
  
## Specify the location and name for the extracted DAC package.  
$dacpacPath = "C:\MyDACs\MyApplication.dacpac"  
  
## Extract the DAC.  
$extractionunit = New-Object Microsoft.SqlServer.Management.Dac.DacExtractionUnit($srv, $dbname, $applicationname, $version)  
$extractionunit.Description = $description  
$extractionunit.Extract($dacpacPath)  
```  
  
## <a name="see-also"></a><span data-ttu-id="c5438-200">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c5438-200">See Also</span></span>  
 [<span data-ttu-id="c5438-201">数据层应用程序</span><span class="sxs-lookup"><span data-stu-id="c5438-201">Data-tier Applications</span></span>](data-tier-applications.md)  
