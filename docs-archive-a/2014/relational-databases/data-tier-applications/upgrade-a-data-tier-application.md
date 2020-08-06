---
title: 升级数据层应用程序 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.upgradedacwizard.reviewpolicy.f1
- sql12.swb.upgradedacwizard.selectoptions.f1
- sql12.swb.upgradedacwizard.selectpackage.f1
- sql12.swb.upgradedacwizard.reviewplan.f1
- sql12.swb.upgradedacwizard.checkdrift.f1
- sql12.swb.upgradedacwizard.summary.f1
- sql12.swb.upgradedacwizard.upgradedac.f1
- sql12.swb.upgradedacwizard.introduction.f1
helpviewer_keywords:
- upgrade DAC
- data-tier application [SQL Server], upgrade
- wizard [DAC], upgrade
- How to [DAC], upgrade
ms.assetid: c117df94-f02b-403f-9383-ec5b3ac3763c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0e597d02af28a16539b50ff76503059278ef7a03
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590865"
---
# <a name="upgrade-a-data-tier-application"></a><span data-ttu-id="56117-102">升级数据层应用程序</span><span class="sxs-lookup"><span data-stu-id="56117-102">Upgrade a Data-tier Application</span></span>
  <span data-ttu-id="56117-103">使用“升级数据层应用程序向导”或 Windows PowerShell 脚本可以更改当前部署的数据层应用程序 (DAC) 的架构和属性，以便匹配在 DAC 的新版本中定义的架构和属性。</span><span class="sxs-lookup"><span data-stu-id="56117-103">Use either the Upgrade Data-tier Application Wizard or a Windows PowerShell script to change the schema and properties of a currently deployed data-tier application (DAC) to match the schema and properties defined in a new version of the DAC.</span></span>  
  
-   <span data-ttu-id="56117-104">**开始之前：** [选择 DAC 升级选项](#ChoseDACUpgOptions)、[限制和局限](#LimitationsRestrictions)、[先决条件](#Prerequisites)、[安全性](#Security)、[权限](#Permissions)</span><span class="sxs-lookup"><span data-stu-id="56117-104">**Before you begin:**  [Choosing DAC Upgrade Options](#ChoseDACUpgOptions), [Limitations and Restrictions](#LimitationsRestrictions), [Prerequisites](#Prerequisites), [Security](#Security), [Permissions](#Permissions)</span></span>  
  
-   <span data-ttu-id="56117-105">若要升级 DAC，请使用：  [升级数据层应用程序向导](#UsingDACUpgradeWizard)、[PowerShell](#UpgradeDACPowerShell)</span><span class="sxs-lookup"><span data-stu-id="56117-105">**To upgrade a DAC, using:**  [The Upgrade Data-tier Application Wizard](#UsingDACUpgradeWizard), [PowerShell](#UpgradeDACPowerShell)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="56117-106">开始之前</span><span class="sxs-lookup"><span data-stu-id="56117-106">Before You Begin</span></span>  
 <span data-ttu-id="56117-107">DAC 升级是一个就地过程，此过程更改现有数据库的架构以匹配在新版本的 DAC 中定义的架构。</span><span class="sxs-lookup"><span data-stu-id="56117-107">A DAC upgrade is an in-place process that alters the schema of the existing database to match the schema defined in a new version of the DAC.</span></span> <span data-ttu-id="56117-108">这一新版本的 DAC 在 DAC 包文件中提供。</span><span class="sxs-lookup"><span data-stu-id="56117-108">The new version of the DAC is supplied in a DAC package file.</span></span> <span data-ttu-id="56117-109">有关创建 DAC 包的详细信息，请参阅 [数据层应用程序](data-tier-applications.md)。</span><span class="sxs-lookup"><span data-stu-id="56117-109">For more information about creating a DAC package, see [Data-tier Applications](data-tier-applications.md).</span></span>  
  
###  <a name="choosing-dac-upgrade-options"></a><a name="ChoseDACUpgOptions"></a> <span data-ttu-id="56117-110">选择 DAC 升级选项</span><span class="sxs-lookup"><span data-stu-id="56117-110">Choosing DAC Upgrade Options</span></span>  
 <span data-ttu-id="56117-111">就地升级有四种升级选项：</span><span class="sxs-lookup"><span data-stu-id="56117-111">There are four upgrade options for an in-place upgrade:</span></span>  
  
-   <span data-ttu-id="56117-112">**忽略数据丢失**-如果 `True` 为，则即使某些操作导致数据丢失，升级也将继续。</span><span class="sxs-lookup"><span data-stu-id="56117-112">**Ignore Data Loss** - If `True`, the upgrade will proceed even if some of the operations result in the loss of data.</span></span> <span data-ttu-id="56117-113">如果为 `False`，则上述操作将终止升级。</span><span class="sxs-lookup"><span data-stu-id="56117-113">If `False`, these operations will terminate the upgrade.</span></span> <span data-ttu-id="56117-114">例如，如果当前数据库中的表在新的 DAC 的架构中不存在，则在指定 `True` 时该表将被删除。</span><span class="sxs-lookup"><span data-stu-id="56117-114">For example, if a table in the current database is not present in the schema of the new DAC, the table will be dropped if `True` is specified.</span></span> <span data-ttu-id="56117-115">默认设置为 `True`。</span><span class="sxs-lookup"><span data-stu-id="56117-115">The default setting is `True`.</span></span>  
  
-   <span data-ttu-id="56117-116">**更改时阻止**-如果为，则在 `True` 数据库架构不同于在之前的 DAC 中定义的架构时，升级将终止。</span><span class="sxs-lookup"><span data-stu-id="56117-116">**Block on Changes** - If `True`, the upgrade is terminated if the database schema is different than that defined in the previous DAC.</span></span> <span data-ttu-id="56117-117">如果为 `False`，则即使检测到更改，升级也将继续。</span><span class="sxs-lookup"><span data-stu-id="56117-117">If `False`, the upgrade continues even if changes are detected.</span></span> <span data-ttu-id="56117-118">默认设置为 `False`。</span><span class="sxs-lookup"><span data-stu-id="56117-118">The default setting is `False`.</span></span>  
  
-   <span data-ttu-id="56117-119">**失败时回滚**-如果为 `True` ，则在事务中包含升级，如果遇到错误，则将尝试回滚。</span><span class="sxs-lookup"><span data-stu-id="56117-119">**Rollback on Failure** - If `True`, the upgrade is enclosed in a transaction, and if errors are encountered a rollback will be attempted.</span></span> <span data-ttu-id="56117-120">如果为 `False`，则在进行更改时所有更改都将提交，并且在出错时，您可能要还原数据库的以前的备份。</span><span class="sxs-lookup"><span data-stu-id="56117-120">If `False`, all changes are committed as they are made and if errors occur you may have to restore a previous backup of the database.</span></span> <span data-ttu-id="56117-121">默认设置为 `False`。</span><span class="sxs-lookup"><span data-stu-id="56117-121">The default setting is `False`.</span></span>  
  
-   <span data-ttu-id="56117-122">**跳过策略验证**-如果为 `True` ，则不评估 DAC 服务器选择策略。</span><span class="sxs-lookup"><span data-stu-id="56117-122">**Skip Policy Validation** - If `True`, the DAC server selection policy is not evaluated.</span></span> <span data-ttu-id="56117-123">如果为 `False`，将评估策略，并且在存在验证错误时升级将终止。</span><span class="sxs-lookup"><span data-stu-id="56117-123">If `False`, the policy is evaluated and the upgrade terminates if there is a validation error.</span></span> <span data-ttu-id="56117-124">默认设置为 `False`。</span><span class="sxs-lookup"><span data-stu-id="56117-124">The default setting is `False`.</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> <span data-ttu-id="56117-125">限制和局限</span><span class="sxs-lookup"><span data-stu-id="56117-125">Limitations and Restrictions</span></span>  
 <span data-ttu-id="56117-126">DAC 升级只能在 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]或者 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 4 (SP4) 或更高版本中执行。</span><span class="sxs-lookup"><span data-stu-id="56117-126">DAC uprades can only be performed in [!INCLUDE[ssSDS](../../includes/sssds-md.md)], or [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 4 (SP4) or later.</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a><span data-ttu-id="56117-127">先决条件</span><span class="sxs-lookup"><span data-stu-id="56117-127">Prerequisites</span></span>  
 <span data-ttu-id="56117-128">出于谨慎起见，在开始升级前应生成完整数据库备份。</span><span class="sxs-lookup"><span data-stu-id="56117-128">It is prudent to take a full database backup before starting the upgrade.</span></span> <span data-ttu-id="56117-129">如果升级遇到了错误并且无法回滚其所有更改，可能需要还原该备份。</span><span class="sxs-lookup"><span data-stu-id="56117-129">If an upgrade encounters an error and cannot roll back all of its changes, you may need to restore the backup.</span></span>  
  
 <span data-ttu-id="56117-130">在开始升级前，您应该采取若干操作以便验证 DAC 包和升级操作。</span><span class="sxs-lookup"><span data-stu-id="56117-130">Before starting the upgrade, there are several actions that you should take to validate the DAC package and the upgrade actions.</span></span> <span data-ttu-id="56117-131">有关如何执行这些检查的详细信息，请参阅 [Validate a DAC Package](validate-a-dac-package.md)。</span><span class="sxs-lookup"><span data-stu-id="56117-131">For more information about how to perform these checks, see [Validate a DAC Package](validate-a-dac-package.md).</span></span>  
  
-   <span data-ttu-id="56117-132">建议您不要使用来自未知或不可信源的 DAC 包进行升级。</span><span class="sxs-lookup"><span data-stu-id="56117-132">We recommend that you do not upgrade by using a DAC package from unknown or untrusted sources.</span></span> <span data-ttu-id="56117-133">此类包可能包含恶意代码，这些代码可能会执行非预期的 Transact-SQL 代码，或者通过修改架构导致错误。</span><span class="sxs-lookup"><span data-stu-id="56117-133">Such packages could contain malicious code that might execute unintended Transact-SQL code or cause errors by modifying the schema.</span></span> <span data-ttu-id="56117-134">在使用来自未知或不可信源的包之前，请解压缩该 DAC 并检查代码，例如存储过程或者其他用户定义的代码。</span><span class="sxs-lookup"><span data-stu-id="56117-134">Before you use a package from an unknown or untrusted source, unpack the DAC and examine the code, such as stored procedures or other user-defined code.</span></span>  
  
-   <span data-ttu-id="56117-135">如果在部署了上一版本的 DAC 后对当前数据库进行了更改，则某些更改可能会阻碍升级的成功完成，或者可能被升级删除。</span><span class="sxs-lookup"><span data-stu-id="56117-135">If changes have been made to the current database after the last version of the DAC was deployed, some of the changes may prevent the successful completion of the upgrade, or be removed by the upgrade.</span></span> <span data-ttu-id="56117-136">您应该首先生成并查看在数据库中进行的任何此类更改的报告。</span><span class="sxs-lookup"><span data-stu-id="56117-136">You should first generate and review a report of any such changes made in the database.</span></span>  
  
-   <span data-ttu-id="56117-137">出于谨慎起见，应该生成升级将执行的架构更改的列表，并且检查该列表以免有任何问题。</span><span class="sxs-lookup"><span data-stu-id="56117-137">It is prudent to generate a list of the schema changes the upgrade will perform, and review the list for any problems.</span></span>  
  
 <span data-ttu-id="56117-138">DAC 包中的应用程序名称必须与当前已部署的 DAC 的应用程序名称匹配。</span><span class="sxs-lookup"><span data-stu-id="56117-138">The application name in the DAC package must match the application name of the currently deployed DAC.</span></span> <span data-ttu-id="56117-139">例如，如果当前 DAC 的应用程序名称是 **GeneralLedger**，则只能通过使用其应用程序也是 **GeneralLedger**的 DAC 包进行升级。</span><span class="sxs-lookup"><span data-stu-id="56117-139">For example, if the current DAC has an application name of **GeneralLedger**, you can only upgrade by using a DAC package that also has an application name of **GeneralLedger**.</span></span>  
  
 <span data-ttu-id="56117-140">请确保有足够事务日志空间可用于记录所有修改。</span><span class="sxs-lookup"><span data-stu-id="56117-140">Ensure there is enough transaction log space available to log all of the modifications.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="56117-141">Security</span><span class="sxs-lookup"><span data-stu-id="56117-141">Security</span></span>  
 <span data-ttu-id="56117-142">为了提高安全性，SQL Server 身份验证登录名存储在 DAC 包中且没有密码。</span><span class="sxs-lookup"><span data-stu-id="56117-142">To improve security, SQL Server Authentication logins are stored in a DAC package without a password.</span></span> <span data-ttu-id="56117-143">在部署或升级该包时，登录名将作为含有生成的密码的已禁用登录名创建。</span><span class="sxs-lookup"><span data-stu-id="56117-143">When the package is deployed or upgraded, the login is created as a disabled login with a generated password.</span></span> <span data-ttu-id="56117-144">若要启用这些登录名，请使用具有 ALTER ANY LOGIN 权限的登录名登录，并且使用 ALTER LOGIN 来启用该登录名并且分配可以传达给用户的新密码。</span><span class="sxs-lookup"><span data-stu-id="56117-144">To enable the logins, log in using a login that has ALTER ANY LOGIN permission and use ALTER LOGIN to enable the login and assign a new password that can be communicated to the user.</span></span> <span data-ttu-id="56117-145">对于 Windows 身份验证登录名则无需执行此操作，因为其密码不是由 SQL Server 管理的。</span><span class="sxs-lookup"><span data-stu-id="56117-145">This is not needed for Windows Authentication logins because their passwords are not managed by SQL Server.</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="56117-146">权限</span><span class="sxs-lookup"><span data-stu-id="56117-146">Permissions</span></span>  
 <span data-ttu-id="56117-147">DAC 只能由 **sysadmin** 或 **serveradmin** 固定服务器角色的成员升级，或者由 **dbcreator** 固定服务器角色中具有 ALTER ANY LOGIN 权限的登录名升级。</span><span class="sxs-lookup"><span data-stu-id="56117-147">A DAC can only be upgraded by members of the **sysadmin** or **serveradmin** fixed server roles, or by logins that are in the **dbcreator** fixed server role and have ALTER ANY LOGIN permissions.</span></span> <span data-ttu-id="56117-148">该登录名必须是现有数据库的所有者。</span><span class="sxs-lookup"><span data-stu-id="56117-148">The login must be the owner of the existing database.</span></span> <span data-ttu-id="56117-149">名为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sa **的内置** 系统管理员帐户也可以升级 DAC。</span><span class="sxs-lookup"><span data-stu-id="56117-149">The built-in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system administrator account named **sa** can also upgrade a DAC.</span></span>  
  
##  <a name="using-the-upgrade-data-tier-application-wizard"></a><a name="UsingDACUpgradeWizard"></a> <span data-ttu-id="56117-150">使用“升级数据层应用程序向导”</span><span class="sxs-lookup"><span data-stu-id="56117-150">Using the Upgrade Data-tier Application Wizard</span></span>  
 <span data-ttu-id="56117-151">**使用向导升级 DAC**</span><span class="sxs-lookup"><span data-stu-id="56117-151">**To Upgrade a DAC Using a Wizard**</span></span>  
  
1.  <span data-ttu-id="56117-152">在 **“对象资源管理器”** 中，展开包含要升级的 DAC 的实例的节点。</span><span class="sxs-lookup"><span data-stu-id="56117-152">In **Object Explorer**, expand the node for the instance containing the DAC to be upgraded.</span></span>  
  
2.  <span data-ttu-id="56117-153">展开“管理”节点，然后展开“数据层应用程序”节点   。</span><span class="sxs-lookup"><span data-stu-id="56117-153">Expand the **Management** node, and then expand the **Data-tier Applications** node.</span></span>  
  
3.  <span data-ttu-id="56117-154">右键单击要升级的 DAC 的节点，然后选择“升级数据层应用程序…” </span><span class="sxs-lookup"><span data-stu-id="56117-154">Right-click the node for the DAC to be upgraded, and then select **Upgrade Data-tier Application...**</span></span>  
  
4.  <span data-ttu-id="56117-155">完成向导对话框：</span><span class="sxs-lookup"><span data-stu-id="56117-155">Complete the wizard dialogs:</span></span>  
  
    1.  [<span data-ttu-id="56117-156">“简介”页</span><span class="sxs-lookup"><span data-stu-id="56117-156">Introduction Page</span></span>](#Introduction)  
  
    2.  [<span data-ttu-id="56117-157">“选择包”页</span><span class="sxs-lookup"><span data-stu-id="56117-157">Select Package Page</span></span>](#Select_dac_package)  
  
    3.  [<span data-ttu-id="56117-158">“查看策略”页</span><span class="sxs-lookup"><span data-stu-id="56117-158">Review Policy Page</span></span>](#Review_policy)  
  
    4.  [<span data-ttu-id="56117-159">“检测更改”页</span><span class="sxs-lookup"><span data-stu-id="56117-159">Detect Change Page</span></span>](#Detect_change)  
  
    5.  [<span data-ttu-id="56117-160">查看升级计划</span><span class="sxs-lookup"><span data-stu-id="56117-160">Review the Upgrade Plan</span></span>](#ReviewUpgPlan)  
  
    6.  [<span data-ttu-id="56117-161">摘要页</span><span class="sxs-lookup"><span data-stu-id="56117-161">Summary Page</span></span>](#Summary)  
  
    7.  [<span data-ttu-id="56117-162">“升级 DAC”页</span><span class="sxs-lookup"><span data-stu-id="56117-162">Upgrade DAC Page</span></span>](#Upgrade)  
  
##  <a name="introduction-page"></a><a name="Introduction"></a> <span data-ttu-id="56117-163">“简介”页</span><span class="sxs-lookup"><span data-stu-id="56117-163">Introduction Page</span></span>  
 <span data-ttu-id="56117-164">此页描述数据层应用程序的升级步骤。</span><span class="sxs-lookup"><span data-stu-id="56117-164">This page describes the steps for upgrading a data-tier application.</span></span>  
  
 <span data-ttu-id="56117-165">**不再显示此页。**</span><span class="sxs-lookup"><span data-stu-id="56117-165">**Do not show this page again.**</span></span> <span data-ttu-id="56117-166">- 选中该复选框可以停止在将来显示此页。</span><span class="sxs-lookup"><span data-stu-id="56117-166">- Click the check box to stop the page from being displayed in the future.</span></span>  
  
 <span data-ttu-id="56117-167">**下一步 >** - 继续到“选择包”页  。</span><span class="sxs-lookup"><span data-stu-id="56117-167">**Next >** - Proceeds to the **Select Package** page.</span></span>  
  
 <span data-ttu-id="56117-168">**取消** - 终止向导且不升级 DAC。</span><span class="sxs-lookup"><span data-stu-id="56117-168">**Cancel** - Terminates the wizard without upgrading the DAC.</span></span>  
  
##  <a name="select-package-page"></a><a name="Select_dac_package"></a> <span data-ttu-id="56117-169">“选择包”页</span><span class="sxs-lookup"><span data-stu-id="56117-169">Select Package Page</span></span>  
 <span data-ttu-id="56117-170">使用此页可以指定包含数据层应用程序的新版本的 DAC 包。</span><span class="sxs-lookup"><span data-stu-id="56117-170">Use this page to specify the DAC package that contains the new version of the data-tier application.</span></span> <span data-ttu-id="56117-171">该页可为两种状态。</span><span class="sxs-lookup"><span data-stu-id="56117-171">The page transitions through two states.</span></span>  
  
### <a name="select-the-dac-package"></a><span data-ttu-id="56117-172">选择 DAC 包</span><span class="sxs-lookup"><span data-stu-id="56117-172">Select the DAC Package</span></span>  
 <span data-ttu-id="56117-173">使用该页的初始状态可以选择要部署的 DAC 包。</span><span class="sxs-lookup"><span data-stu-id="56117-173">Use the initial state of the page to choose the DAC package to deploy.</span></span> <span data-ttu-id="56117-174">该 DAC 包必须是有效的 DAC 包文件，并且必须具有 .dacpac 扩展名。</span><span class="sxs-lookup"><span data-stu-id="56117-174">The DAC package must be a valid DAC package file and must have a .dacpac extension.</span></span> <span data-ttu-id="56117-175">DAC 包中的 DAC 应用程序名称必须与当前 DAC 的应用程序名称相同。</span><span class="sxs-lookup"><span data-stu-id="56117-175">The DAC application name in the DAC package must be the same as the application name of the current DAC.</span></span>  
  
 <span data-ttu-id="56117-176">**DAC 包** - 指定包含数据层应用程序的新版本的 DAC 包的路径和文件名。</span><span class="sxs-lookup"><span data-stu-id="56117-176">**DAC Package** - Specify the path and file name of the DAC package that contains the new version of the data-tier application.</span></span> <span data-ttu-id="56117-177">您可以选择框右侧的 **“浏览”** 按钮以便浏览到 DAC 包的位置。</span><span class="sxs-lookup"><span data-stu-id="56117-177">You can select the **Browse** button at the right of the box to browse to the location of the DAC package.</span></span>  
  
 <span data-ttu-id="56117-178">**应用程序名称** - 一个只读框，它显示创作 DAC 或者从某一数据库中提取 DAC 时分配的 DAC 应用程序名称。</span><span class="sxs-lookup"><span data-stu-id="56117-178">**Application Name** - A read-only box that displays the DAC application name assigned when the DAC was authored or extracted from a database.</span></span>  
  
 <span data-ttu-id="56117-179">“版本”  - 一个只读框，它显示创作 DAC 或者从某一数据库中提取 DAC 时分配的版本。</span><span class="sxs-lookup"><span data-stu-id="56117-179">**Version** - A read-only box that displays the version assigned when the DAC was authored or extracted from a database.</span></span>  
  
 <span data-ttu-id="56117-180">“说明”  - 一个只读框，它显示创作 DAC 或者从某一数据库中提取 DAC 时编写的版本。</span><span class="sxs-lookup"><span data-stu-id="56117-180">**Description** - A read-only box that displays the description written when the DAC was authored or extracted from a database.</span></span>  
  
 <span data-ttu-id="56117-181">" \*\* \< 上一步**"-返回到 "**简介\*\*" 页。</span><span class="sxs-lookup"><span data-stu-id="56117-181">**\< Previous** - Returns to the **Introduction** page.</span></span>  
  
 <span data-ttu-id="56117-182">“下一步 >”  - 显示进度栏，因为向导已确认所选文件为有效的 DAC 包。</span><span class="sxs-lookup"><span data-stu-id="56117-182">**Next >** - Displays a progress bar as the wizard confirms that the selected file is a valid DAC package.</span></span>  
  
 <span data-ttu-id="56117-183">**取消** - 终止向导且不升级 DAC。</span><span class="sxs-lookup"><span data-stu-id="56117-183">**Cancel** - Terminates the wizard without upgrading the DAC.</span></span>  
  
### <a name="validating-the-dac-package"></a><span data-ttu-id="56117-184">验证 DAC 包</span><span class="sxs-lookup"><span data-stu-id="56117-184">Validating the DAC Package</span></span>  
 <span data-ttu-id="56117-185">在向导确认所选文件是有效的 DAC 包时显示一个进度栏。</span><span class="sxs-lookup"><span data-stu-id="56117-185">Displays a progress bar as the wizard confirms that the selected file is a valid DAC package.</span></span> <span data-ttu-id="56117-186">如果验证该 DAC 包，则向导将继续到 **“查看策略”** 页。</span><span class="sxs-lookup"><span data-stu-id="56117-186">If the DAC package is validated, the wizard proceeds to the **Review Policy** page.</span></span> <span data-ttu-id="56117-187">如果该文件不是有效的 DAC 包，则向导会保持在 **“选择 DAC 包”** 页上。</span><span class="sxs-lookup"><span data-stu-id="56117-187">If the file is not a valid DAC package, the wizard remains on the **Select DAC Package** page.</span></span> <span data-ttu-id="56117-188">或者选择另一个有效的 DAC 包，或者取消该向导并且生成一个新的 DAC 包。</span><span class="sxs-lookup"><span data-stu-id="56117-188">Either select another valid DAC package or cancel the wizard and generate a new DAC package.</span></span>  
  
 <span data-ttu-id="56117-189">“正在验证 DAC 的内容”  - 报告验证过程的当前状态的进度栏。</span><span class="sxs-lookup"><span data-stu-id="56117-189">**Validating the contents of the DAC** - The progress bar that reports the current status of the validation process.</span></span>  
  
 <span data-ttu-id="56117-190">" \*\* \< 上一步**"-返回到 "**选择包\*\*" 页的初始状态。</span><span class="sxs-lookup"><span data-stu-id="56117-190">**\< Previous** - Returns to the initial state of the **Select Package** page.</span></span>  
  
 <span data-ttu-id="56117-191">“下一步 >”  - 继续到“选择包”  页的最终版本。</span><span class="sxs-lookup"><span data-stu-id="56117-191">**Next >** - Proceeds to the final version of the **Select Package** page.</span></span>  
  
 <span data-ttu-id="56117-192">“取消”  - 终止向导且不部署 DAC。</span><span class="sxs-lookup"><span data-stu-id="56117-192">**Cancel** - Terminates the wizard without deploying the DAC.</span></span>  
  
##  <a name="review-policy-page"></a><a name="Review_policy"></a> <span data-ttu-id="56117-193">“查看策略”页</span><span class="sxs-lookup"><span data-stu-id="56117-193">Review Policy Page</span></span>  
 <span data-ttu-id="56117-194">使用此页可查看评估 DAC 服务器选择策略的结果（如果该 DAC 具有策略）。</span><span class="sxs-lookup"><span data-stu-id="56117-194">Use this page to review the results of evaluating the DAC server selection policy, if the DAC has a policy.</span></span> <span data-ttu-id="56117-195">该 DAC 服务器选择策略是可选的，并分配给在 Microsoft Visual Studio 中创作的 DAC。</span><span class="sxs-lookup"><span data-stu-id="56117-195">The DAC server selection policy is optional, and is assigned to a DAC authored in Microsoft Visual Studio.</span></span> <span data-ttu-id="56117-196">该策略使用该服务器选择策略方面指定 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的实例为承载该 DAC 而必须满足的条件。</span><span class="sxs-lookup"><span data-stu-id="56117-196">The policy uses the server selection policy facets to specify conditions an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] should meet to host the DAC.</span></span>  
  
 <span data-ttu-id="56117-197">**策略条件的评估结果** - 一个只读报告，显示 DAC 服务器选择策略中的条件评估是否成功。</span><span class="sxs-lookup"><span data-stu-id="56117-197">**Evaluation results of policy conditions** - A read-only report showing whether the evaluations of the conditions in the DAC server selection policy succeeded.</span></span> <span data-ttu-id="56117-198">将在单独的行上报告对每个条件进行评估的结果。</span><span class="sxs-lookup"><span data-stu-id="56117-198">The results of evaluating each condition are reported on a separate line.</span></span>  
  
 <span data-ttu-id="56117-199">**忽略违反策略情况** - 使用此复选框可以在未能满足一个或多个策略条件的情况下继续进行升级。</span><span class="sxs-lookup"><span data-stu-id="56117-199">**Ignore policy violations** - Use this check box to proceed with the upgrade if one or more of the policy conditions failed.</span></span> <span data-ttu-id="56117-200">只有在您确保未满足的所有条件都不会阻碍 DAC 操作成功条件的情况下，才选择此选项。</span><span class="sxs-lookup"><span data-stu-id="56117-200">Only select this option if you are sure that all of the conditions which failed will not prevent the successful operation of the DAC.</span></span>  
  
 <span data-ttu-id="56117-201">" \*\* \< 上一步**"-返回到 "**选择包\*\*" 页。</span><span class="sxs-lookup"><span data-stu-id="56117-201">**\< Previous** - Returns to the **Select Package** page.</span></span>  
  
 <span data-ttu-id="56117-202">**下一步 >** - 继续到“检测更改”  页。</span><span class="sxs-lookup"><span data-stu-id="56117-202">**Next >** - Proceeds to the **Detect Change** page.</span></span>  
  
 <span data-ttu-id="56117-203">**取消** - 终止向导且不升级 DAC。</span><span class="sxs-lookup"><span data-stu-id="56117-203">**Cancel** - Terminates the wizard without upgrading the DAC.</span></span>  
  
##  <a name="detect-change-page"></a><a name="Detect_change"></a> <span data-ttu-id="56117-204">“检测更改”页</span><span class="sxs-lookup"><span data-stu-id="56117-204">Detect Change Page</span></span>  
 <span data-ttu-id="56117-205">使用此页可以报告向导对所发生的数据库更改的检测结果，这些更改应该是使数据库架构不同于在 **msdb**的 DAC 元数据中存储的架构定义的更改。</span><span class="sxs-lookup"><span data-stu-id="56117-205">Use this page reports the results of the wizards check for changes made to the database that make it's schema different than the schema definition stored in the DAC metadata in **msdb**.</span></span> <span data-ttu-id="56117-206">例如，如果 CREATE、ALTER 或 DROP 语句已用于在最初部署 DAC 后从数据库中添加、更改或删除对象。</span><span class="sxs-lookup"><span data-stu-id="56117-206">For example, if CREATE, ALTER, or DROP statements have been used to add, change, or remove objects from the database after the DAC was originally deployed.</span></span> <span data-ttu-id="56117-207">则该页将首先显示一个进度栏，然后报告分析的结果。</span><span class="sxs-lookup"><span data-stu-id="56117-207">The page first displays a progress bar, and then reports the results of the analysis.</span></span>  
  
 <span data-ttu-id="56117-208">**正在检测更改，这可能需要几分钟的时间** - 在向导检查数据库的当前架构和 DAC 定义中的对象之间的差异时显示一个进度栏。</span><span class="sxs-lookup"><span data-stu-id="56117-208">**Detecting change, this may take a few minutes** - Displays a progress bar as the wizard checks for differences between the current schema of the database and the objects in the DAC definition.</span></span>  
  
 <span data-ttu-id="56117-209">**更改检测结果:** - 指示分析已完成并且在下面报告结果。</span><span class="sxs-lookup"><span data-stu-id="56117-209">**Change detection results:** - Indicates that the analysis has completed and the results are reported below.</span></span>  
  
 <span data-ttu-id="56117-210">**数据库 DatabaseName 尚未更改** - 向导检测到在数据库中定义的对象和 DAC 定义中其匹配对象之间没有差异。</span><span class="sxs-lookup"><span data-stu-id="56117-210">**The database DatabaseName has not changed** - The wizard detected no differences in the objects defined in the database and their counterparts in the DAC definition.</span></span>  
  
 <span data-ttu-id="56117-211">**数据库 DatabaseName 已更改** - 向导检测到数据库中的对象和 DAC 定义中其匹配对象之间发生了更改。</span><span class="sxs-lookup"><span data-stu-id="56117-211">**The database DatabaseName has changed** - The wizard detected changes between the objects in the database and their counterparts in the DAC definition.</span></span>  
  
 <span data-ttu-id="56117-212">**继续而不管可能的更改丢失** - 指定你理解当前数据库中的某些对象或数据在新数据库中将不存在，并且愿意继续进行升级。</span><span class="sxs-lookup"><span data-stu-id="56117-212">**Proceed despite possible loss of changes** - Specifies that you understand some of the objects or data in the current database will not be present in the new database, and that you are willing to proceed with the upgrade.</span></span> <span data-ttu-id="56117-213">只有在您对更改报表进行了分析并且理解您必须执行以便手动传输新数据库中所需的任何对象或数据的步骤后，才应选择此按钮。</span><span class="sxs-lookup"><span data-stu-id="56117-213">You should select this button only if you have analyzed the change report and understand the steps you must perform to manually transfer any objects or data required in the new database.</span></span> <span data-ttu-id="56117-214">如果您不能确定，请单击 **“保存报表”** 按钮以便保存更改报表，然后单击 **“取消”** 。</span><span class="sxs-lookup"><span data-stu-id="56117-214">If you are not sure, click the **Save Report** button to save the change report, then click **Cancel**.</span></span> <span data-ttu-id="56117-215">对报表进行分析，计划如何在升级完成后传输所需的任何对象和数据，然后重新启动该向导。</span><span class="sxs-lookup"><span data-stu-id="56117-215">Analyze the report, plan how to transfer any required objects and data after the upgrade completes, then restart the wizard.</span></span>  
  
 <span data-ttu-id="56117-216">**保存报表** - 单击此按钮可以保存向导检测到的数据库中对象和其在 DAC 定义中的匹配对象之间的更改的报表。</span><span class="sxs-lookup"><span data-stu-id="56117-216">**Save Report** - Click the button to save a report of the changes the wizard detected between the objects in the database and their counterparts in the DAC definition.</span></span> <span data-ttu-id="56117-217">然后，您可以查看该报表以确定是否需要在升级完成后执行一些操作，以便将报表中列出的某些或全部对象合并到新的数据库中。</span><span class="sxs-lookup"><span data-stu-id="56117-217">You can then review the report to determine if you need to take actions after the upgrade completes to incorporate some or all of the objects listed in the report into the new database.</span></span>  
  
 <span data-ttu-id="56117-218">" \*\* \< 上一步**"-返回到 "**选择 DAC 包\*\*" 页。</span><span class="sxs-lookup"><span data-stu-id="56117-218">**\< Previous** - Returns to the **Select DAC Package** page.</span></span>  
  
 <span data-ttu-id="56117-219">**下一步 >** - 继续到“选项”  页。</span><span class="sxs-lookup"><span data-stu-id="56117-219">**Next >** - Proceeds to the **Options** page.</span></span>  
  
 <span data-ttu-id="56117-220">“取消”  - 终止向导且不部署 DAC。</span><span class="sxs-lookup"><span data-stu-id="56117-220">**Cancel** - Terminates the wizard without deploying the DAC.</span></span>  
  
## <a name="options-page"></a><span data-ttu-id="56117-221">“选项”页</span><span class="sxs-lookup"><span data-stu-id="56117-221">Options Page</span></span>  
 <span data-ttu-id="56117-222">使用此页可以选择用于升级的失败时回滚选项。</span><span class="sxs-lookup"><span data-stu-id="56117-222">Use this page to select the rollback on failure option for the upgrade.</span></span>  
  
 <span data-ttu-id="56117-223">**失败时回滚** - 选择此选项可以将升级封装在向导在出错时可尝试回滚的事务中。</span><span class="sxs-lookup"><span data-stu-id="56117-223">**Rollback on failure** - Select this option to enclose the upgrade in a transaction which the wizard can attempt to roll back if errors occur.</span></span> <span data-ttu-id="56117-224">有关该选项的详细信息，请参阅 [选择 DAC 升级选项](#ChoseDACUpgOptions)。</span><span class="sxs-lookup"><span data-stu-id="56117-224">For more information about the option, see [Choosing DAC Upgrade Options](#ChoseDACUpgOptions).</span></span>  
  
 <span data-ttu-id="56117-225">**还原默认值** - 将选项恢复为默认设置 False。</span><span class="sxs-lookup"><span data-stu-id="56117-225">**Restore Defaults** - Returns the option to its default setting of false.</span></span>  
  
 <span data-ttu-id="56117-226">" \*\* \< 上一步**"-返回到 "**检测更改\*\*" 页。</span><span class="sxs-lookup"><span data-stu-id="56117-226">**\< Previous** - Returns to the **Detect Change** page.</span></span>  
  
 <span data-ttu-id="56117-227">**下一步 >** - 继续到“查看升级计划”  页。</span><span class="sxs-lookup"><span data-stu-id="56117-227">**Next >** - Proceeds to the **Review the Upgrade Plan** page.</span></span>  
  
 <span data-ttu-id="56117-228">“取消”  - 终止向导且不部署 DAC。</span><span class="sxs-lookup"><span data-stu-id="56117-228">**Cancel** - Terminates the wizard without deploying the DAC.</span></span>  
  
##  <a name="review-the-upgrade-plan-page"></a><a name="ReviewUpgPlan"></a> <span data-ttu-id="56117-229">“查看升级计划”页</span><span class="sxs-lookup"><span data-stu-id="56117-229">Review the Upgrade Plan Page</span></span>  
 <span data-ttu-id="56117-230">使用此页可以查看升级过程将执行的操作。</span><span class="sxs-lookup"><span data-stu-id="56117-230">Use this page to do review the actions that will be taken by the upgrade process.</span></span> <span data-ttu-id="56117-231">仅当确信升级不会导致问题时才继续。</span><span class="sxs-lookup"><span data-stu-id="56117-231">Only proceed when you are confident the upgrade will not create problems.</span></span>  
  
 <span data-ttu-id="56117-232">**将使用以下操作升级 DAC。**</span><span class="sxs-lookup"><span data-stu-id="56117-232">**The following actions will be used to upgrade the DAC.**</span></span> <span data-ttu-id="56117-233">- 查看显示的信息以便确保将执行的操作正确。</span><span class="sxs-lookup"><span data-stu-id="56117-233">- Review the information displayed to ensure the actions taken will be correct.</span></span> <span data-ttu-id="56117-234">“操作”  列显示要用于执行升级的操作（如 Transact-SQL 语句）。</span><span class="sxs-lookup"><span data-stu-id="56117-234">The **Action** column displays the actions, such as Transact-SQL statements, that will be run to perform the upgrade.</span></span> <span data-ttu-id="56117-235">**“数据丢失”** 列将包含在相关操作删除数据时给出的警告。</span><span class="sxs-lookup"><span data-stu-id="56117-235">The **Data Loss** column will contain a warning if the associated action could delete data.</span></span>  
  
 <span data-ttu-id="56117-236">**刷新** - 刷新操作列表。</span><span class="sxs-lookup"><span data-stu-id="56117-236">**Refresh** - refreshes the action list.</span></span>  
  
 <span data-ttu-id="56117-237">**保存操作报告** - 将操作窗口的内容保存到某一 HTML 文件。</span><span class="sxs-lookup"><span data-stu-id="56117-237">**Save Action Report** - saves the contents of the action window to an HTML file.</span></span>  
  
 <span data-ttu-id="56117-238">**继续而不管可能的更改丢失** - 指定你理解当前数据库中的某些对象或数据在新数据库中将不存在，并且愿意继续进行升级。</span><span class="sxs-lookup"><span data-stu-id="56117-238">**Proceed despite possible loss of changes** - Specifies that you understand some of the objects or data in the current database will not be present in the new database, and that you are willing to proceed with the upgrade.</span></span> <span data-ttu-id="56117-239">只有在您对更改报表进行了分析并且理解您必须执行以便手动传输新数据库中所需的任何对象或数据的步骤后，才应选择此按钮。</span><span class="sxs-lookup"><span data-stu-id="56117-239">You should select this button only if you have analyzed the change report and understand the steps you must perform to manually transfer any objects or data required in the new database.</span></span> <span data-ttu-id="56117-240">如果你不能确定，请单击“保存操作报告”按钮以保存更改报告，单击“保存脚本”按钮以保存 Transact-SQL 脚本，然后单击“取消”    。</span><span class="sxs-lookup"><span data-stu-id="56117-240">If you are not sure, click the **Save Action Report** button to save the change report and the **Save Scripts** button to save the Transact-SQL script, then click **Cancel**.</span></span> <span data-ttu-id="56117-241">对报告和脚本进行分析，计划如何在升级完成后传输所需的任何对象和数据，然后重新启动该向导。</span><span class="sxs-lookup"><span data-stu-id="56117-241">Analyze the report and script, and then plan how to transfer any required objects and data after the upgrade completes, then restart the wizard.</span></span>  
  
 <span data-ttu-id="56117-242">**保存脚本** - 将用于执行升级的 Transact-SQL 语句保存为文本文件。</span><span class="sxs-lookup"><span data-stu-id="56117-242">**Save Scripts** - saves the Transact-SQL statements that will be used to perform the upgrade to a text file.</span></span>  
  
 <span data-ttu-id="56117-243">**还原默认值** - 将选项恢复为默认设置 False。</span><span class="sxs-lookup"><span data-stu-id="56117-243">**Restore Defaults** - Returns the option to its default setting of false.</span></span>  
  
 <span data-ttu-id="56117-244">" \*\* \< 上一步**"-返回到 "**检测更改\*\*" 页。</span><span class="sxs-lookup"><span data-stu-id="56117-244">**\< Previous** - Returns to the **Detect Change** page.</span></span>  
  
 <span data-ttu-id="56117-245">“下一步 >”  - 继续到“摘要”  页。</span><span class="sxs-lookup"><span data-stu-id="56117-245">**Next >** - Proceeds to the **Summary** page.</span></span>  
  
 <span data-ttu-id="56117-246">“取消”  - 终止向导且不部署 DAC。</span><span class="sxs-lookup"><span data-stu-id="56117-246">**Cancel** - Terminates the wizard without deploying the DAC.</span></span>  
  
##  <a name="summary-page"></a><a name="Summary"></a> <span data-ttu-id="56117-247">摘要页</span><span class="sxs-lookup"><span data-stu-id="56117-247">Summary Page</span></span>  
 <span data-ttu-id="56117-248">使用此页可以最后查看在升级 DAC 时向导将执行的操作。</span><span class="sxs-lookup"><span data-stu-id="56117-248">Use this page to do a final review of the actions the wizard will take when upgrading the DAC.</span></span>  
  
 <span data-ttu-id="56117-249">**将使用以下设置升级 DAC。**</span><span class="sxs-lookup"><span data-stu-id="56117-249">**The following settings will be used to upgrade your DAC.**</span></span> <span data-ttu-id="56117-250">- 查看显示的信息以便确保将执行的操作正确。</span><span class="sxs-lookup"><span data-stu-id="56117-250">- Review the information displayed to ensure the actions taken will be correct.</span></span> <span data-ttu-id="56117-251">该窗口将显示您选择要升级的 DAC 以及包含该 DAC 的新版本的 DAC 包。</span><span class="sxs-lookup"><span data-stu-id="56117-251">The window displays the DAC you selected to be upgraded, and the DAC package containing the new version of the DAC.</span></span> <span data-ttu-id="56117-252">该窗口还显示数据库的当前版本是否与当前的 DAC 定义相同，或者显示数据库是否已更改。</span><span class="sxs-lookup"><span data-stu-id="56117-252">The window also displays whether the current version of the database is the same as the current DAC definition, or if the database has changed.</span></span>  
  
 <span data-ttu-id="56117-253">" \*\* \< 上一步**"-返回到 "**查看升级计划"\*\* 页。</span><span class="sxs-lookup"><span data-stu-id="56117-253">**\< Previous** - Returns you to the **Review the Upgrade Plan** page.</span></span>  
  
 <span data-ttu-id="56117-254">**下一步 >** - 部署 DAC，并在“升级 DAC”  页中显示结果。</span><span class="sxs-lookup"><span data-stu-id="56117-254">**Next >** - Deploys the DAC and displays the results in the **Upgrade DAC** page.</span></span>  
  
 <span data-ttu-id="56117-255">“取消”  - 终止向导且不部署 DAC。</span><span class="sxs-lookup"><span data-stu-id="56117-255">**Cancel** - Terminates the wizard without deploying the DAC.</span></span>  
  
##  <a name="upgrade-dac-page"></a><a name="Upgrade"></a> <span data-ttu-id="56117-256">“升级 DAC”页</span><span class="sxs-lookup"><span data-stu-id="56117-256">Upgrade DAC Page</span></span>  
 <span data-ttu-id="56117-257">此页报告升级操作是成功还是失败。</span><span class="sxs-lookup"><span data-stu-id="56117-257">This page reports the success or failure of the upgrade operation.</span></span>  
  
 <span data-ttu-id="56117-258">**升级 DAC** - 报告为升级 DAC 而执行的每个操作是成功还是失败。</span><span class="sxs-lookup"><span data-stu-id="56117-258">**Upgrading the DAC** - Reports the success or failure of each action taken to upgrade the DAC.</span></span> <span data-ttu-id="56117-259">查看信息以便确定每个操作是成功还是失败。</span><span class="sxs-lookup"><span data-stu-id="56117-259">Review the information to determine the success or failure of each action.</span></span> <span data-ttu-id="56117-260">遇到了错误的任何操作都将在 **“结果”** 列中具有一个链接。</span><span class="sxs-lookup"><span data-stu-id="56117-260">Any action that encountered an error will have a link in the **Result** column.</span></span> <span data-ttu-id="56117-261">选择该链接可以查看针对该操作的错误报告。</span><span class="sxs-lookup"><span data-stu-id="56117-261">Select the link to view a report of the error for that action.</span></span>  
  
 <span data-ttu-id="56117-262">**保存报表** - 选择此按钮可以将升级报表保存到某一 HTML 文件。</span><span class="sxs-lookup"><span data-stu-id="56117-262">**Save Report** - Select this button to save the upgrade report to an HTML file.</span></span> <span data-ttu-id="56117-263">该文件报告每个操作的状态，并且包括任何操作生成的所有错误。</span><span class="sxs-lookup"><span data-stu-id="56117-263">The file reports the status of each action, including all errors generated by any of the actions.</span></span> <span data-ttu-id="56117-264">默认文件夹是您的 Windows 帐户的 Documents 文件夹中的 SQL Server Management Studio\DAC Packages 文件夹。</span><span class="sxs-lookup"><span data-stu-id="56117-264">The default folder is a SQL Server Management Studio\DAC Packages folder in the Documents folder of your Windows account.</span></span>  
  
 <span data-ttu-id="56117-265">“完成”  - 终止向导。</span><span class="sxs-lookup"><span data-stu-id="56117-265">**Finish** - Terminates the wizard.</span></span>  
  
##  <a name="using-powershell"></a><a name="UpgradeDACPowerShell"></a> <span data-ttu-id="56117-266">使用 PowerShell</span><span class="sxs-lookup"><span data-stu-id="56117-266">Using PowerShell</span></span>  
 <span data-ttu-id="56117-267">**使用 PowerShell 脚本中的 IncrementalUpgrade() 方法升级 DAC**</span><span class="sxs-lookup"><span data-stu-id="56117-267">**To upgrade a DAC using the IncrementalUpgrade() method in a PowerShell script**</span></span>  
  
1.  <span data-ttu-id="56117-268">创建一个 SMO Server 对象，并且将该对象设置为包含要升级的 DAC 的实例。</span><span class="sxs-lookup"><span data-stu-id="56117-268">Create a SMO Server object and set it to the instance that contains the DAC to be upgraded.</span></span>  
  
2.  <span data-ttu-id="56117-269">打开 `ServerConnection` 对象，并连接到同一实例。</span><span class="sxs-lookup"><span data-stu-id="56117-269">Open a `ServerConnection` object and connect to the same instance.</span></span>  
  
3.  <span data-ttu-id="56117-270">使用 `System.IO.File` 加载 DAC 包文件。</span><span class="sxs-lookup"><span data-stu-id="56117-270">Use `System.IO.File` to load the DAC package file.</span></span>  
  
4.  <span data-ttu-id="56117-271">使用 `add_DacActionStarted` 和 `add_DacActionFinished` 订阅 DAC 升级事件。</span><span class="sxs-lookup"><span data-stu-id="56117-271">Use `add_DacActionStarted` and `add_DacActionFinished` to subscribe to the DAC upgrade events.</span></span>  
  
5.  <span data-ttu-id="56117-272">设置 `DacUpgradeOptions` 。</span><span class="sxs-lookup"><span data-stu-id="56117-272">Set the `DacUpgradeOptions`.</span></span>  
  
6.  <span data-ttu-id="56117-273">使用 `IncrementalUpgrade` 方法升级 DAC。</span><span class="sxs-lookup"><span data-stu-id="56117-273">Use the `IncrementalUpgrade` method to upgrade the DAC.</span></span>  
  
7.  <span data-ttu-id="56117-274">关闭用于读取 DAC 包文件的文件流。</span><span class="sxs-lookup"><span data-stu-id="56117-274">Close the file stream used to read the DAC package file.</span></span>  
  
### <a name="example-powershell"></a><span data-ttu-id="56117-275">示例 (PowerShell)</span><span class="sxs-lookup"><span data-stu-id="56117-275">Example (PowerShell)</span></span>  
 <span data-ttu-id="56117-276">下面的示例使用 MyApplicationVNext.dacpac 包中的新的 DAC 版本，将名为 MyApplication 的 DAC 升级到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的默认实例。</span><span class="sxs-lookup"><span data-stu-id="56117-276">The following example upgrades a DAC named MyApplication on a default instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)], using a new DAC version in a MyApplicationVNext.dacpac package.</span></span>  
  
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
  
## Subscribe to the DAC upgrade events.  
$dacstore.add_DacActionStarted({Write-Host `n`nStarting at $(get-date) :: $_.Description})  
$dacstore.add_DacActionFinished({Write-Host Completed at $(get-date) :: $_.Description})  
  
## Upgrade the DAC and close the package.  
$dacName  = "MyApplication"  
  
## Set the upgrade options.  
$upgradeProperties = New-Object Microsoft.SqlServer.Management.Dac.DacUpgradeOptions  
$upgradeProperties.blockonchanges = $true  
$upgradeProperties.ignoredataloss = $false  
$upgradeProperties.rollbackonfailure = $true  
$ upgradeProperties.skippolicyvalidation = $false  
  
## Upgrade the DAC  
$dacstore.IncrementalUpgrade($dacName, $dacType, $upgradeProperties)  
## Close the package file.  
$fileStream.Close()  
```  
  
## <a name="see-also"></a><span data-ttu-id="56117-277">另请参阅</span><span class="sxs-lookup"><span data-stu-id="56117-277">See Also</span></span>  
 <span data-ttu-id="56117-278">[数据层应用程序](data-tier-applications.md) </span><span class="sxs-lookup"><span data-stu-id="56117-278">[Data-tier Applications](data-tier-applications.md) </span></span>  
 [<span data-ttu-id="56117-279">SQL Server PowerShell</span><span class="sxs-lookup"><span data-stu-id="56117-279">SQL Server PowerShell</span></span>](../../powershell/sql-server-powershell.md)  
