---
title: 删除数据层应用程序 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.deletedacwizard.introduction.f1
- sql12.swb.deletedacwizard.deletedac.f1
- sql12.swb.deletedacwizard.summary.f1
- sql12.swb.deletedacwizard.choosemethod.f1
helpviewer_keywords:
- How to [DAC], delete
- data-tier application [SQL Server], delete
- wizard [DAC], delete
- delete DAC
ms.assetid: 16fe1c18-4486-424d-81d6-d276ed97482f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 602256c287a8c7bcf9d3fa5597b2fec2085c626c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691742"
---
# <a name="delete-a-data-tier-application"></a><span data-ttu-id="b71c2-102">删除数据层应用程序</span><span class="sxs-lookup"><span data-stu-id="b71c2-102">Delete a Data-tier Application</span></span>
  <span data-ttu-id="b71c2-103">您可以通过使用“删除数据层应用程序向导”或 Windows PowerShell 脚本，删除数据层应用程序。</span><span class="sxs-lookup"><span data-stu-id="b71c2-103">You can delete a data-tier application by using either the Delete Data-tier Application wizard or a Windows PowerShell script.</span></span> <span data-ttu-id="b71c2-104">您可以指定是保留、分离还是删除关联数据库。</span><span class="sxs-lookup"><span data-stu-id="b71c2-104">You can specify whether the associated database is retained, detached, or dropped.</span></span>  
  
-   <span data-ttu-id="b71c2-105">**开始之前：** [限制和局限](#LimitationsRestrictions)、[权限](#Permissions)</span><span class="sxs-lookup"><span data-stu-id="b71c2-105">**Before you begin:**  [Limitations and Restrictions](#LimitationsRestrictions), [Permissions](#Permissions)</span></span>  
  
-   <span data-ttu-id="b71c2-106">若要升级 DAC，请使用：  [注册数据层应用程序向导](#UsingDeleteDACWizard)、[PowerShell](#DeleteDACPowerShell)</span><span class="sxs-lookup"><span data-stu-id="b71c2-106">**To upgrade a DAC, using:**  [The Register Data-tier Application Wizard](#UsingDeleteDACWizard), [PowerShell](#DeleteDACPowerShell)</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="b71c2-107">开始之前</span><span class="sxs-lookup"><span data-stu-id="b71c2-107">Before You Begin</span></span>  
 <span data-ttu-id="b71c2-108">在删除某一数据层应用程序 (DAC) 实例时，您可以选择三个选项之一，这三个选项指定要对与该数据层应用程序相关联的数据库执行何种操作。</span><span class="sxs-lookup"><span data-stu-id="b71c2-108">When you delete a data-tier application (DAC) instance, you choose one of three options specifying what is to be done with the database associated with the data-tier application.</span></span> <span data-ttu-id="b71c2-109">所有这三个选项都删除 DAC 定义元数据。</span><span class="sxs-lookup"><span data-stu-id="b71c2-109">All three options delete the DAC definition metadata.</span></span> <span data-ttu-id="b71c2-110">这些选项在如何处理与数据层应用程序相关联的数据库上有所不同。</span><span class="sxs-lookup"><span data-stu-id="b71c2-110">The options differ in what they do with the database associated with the data-tier application.</span></span> <span data-ttu-id="b71c2-111">向导并不删除与 DAC 或数据库相关联的任何实例级别的对象，例如登录名。</span><span class="sxs-lookup"><span data-stu-id="b71c2-111">The wizard does not delete any of the instance-level objects associated with the DAC or database, such as logins.</span></span>  
  
|<span data-ttu-id="b71c2-112">选项</span><span class="sxs-lookup"><span data-stu-id="b71c2-112">Option</span></span>|<span data-ttu-id="b71c2-113">数据库操作</span><span class="sxs-lookup"><span data-stu-id="b71c2-113">Database actions</span></span>|  
|------------|----------------------|  
|<span data-ttu-id="b71c2-114">删除注册</span><span class="sxs-lookup"><span data-stu-id="b71c2-114">Delete registration</span></span>|<span data-ttu-id="b71c2-115">关联的数据库保持不变。</span><span class="sxs-lookup"><span data-stu-id="b71c2-115">The associated database remains intact.</span></span>|  
|<span data-ttu-id="b71c2-116">分离数据库</span><span class="sxs-lookup"><span data-stu-id="b71c2-116">Detach database</span></span>|<span data-ttu-id="b71c2-117">关联的数据库被分离。</span><span class="sxs-lookup"><span data-stu-id="b71c2-117">The associated database is detached.</span></span> <span data-ttu-id="b71c2-118">数据库引擎的实例无法引用该数据库，但数据和日志文件保持不变。</span><span class="sxs-lookup"><span data-stu-id="b71c2-118">The instance of the Database Engine cannot reference the database, but the data and log files are intact.</span></span>|  
|<span data-ttu-id="b71c2-119">删除数据库</span><span class="sxs-lookup"><span data-stu-id="b71c2-119">Delete database</span></span>|<span data-ttu-id="b71c2-120">关联的数据库被删除。</span><span class="sxs-lookup"><span data-stu-id="b71c2-120">The associated database is dropped.</span></span> <span data-ttu-id="b71c2-121">数据和日志文件被删除。</span><span class="sxs-lookup"><span data-stu-id="b71c2-121">The data and log files are deleted.</span></span>|  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> <span data-ttu-id="b71c2-122">限制和局限</span><span class="sxs-lookup"><span data-stu-id="b71c2-122">Limitations and Restrictions</span></span>  
 <span data-ttu-id="b71c2-123">在删除某一 DAC 后，没有自动的机制可以还原该 DAC 的定义元数据或数据库。</span><span class="sxs-lookup"><span data-stu-id="b71c2-123">There is no automatic mechanism to restore the DAC definition metadata or the database after you delete a DAC.</span></span> <span data-ttu-id="b71c2-124">您可以手动重新生成 DAC 实例的方式取决于删除选项。</span><span class="sxs-lookup"><span data-stu-id="b71c2-124">How you can manually rebuild the DAC instance depends on the delete option.</span></span>  
  
|<span data-ttu-id="b71c2-125">选项</span><span class="sxs-lookup"><span data-stu-id="b71c2-125">Option</span></span>|<span data-ttu-id="b71c2-126">如何重新生成 DAC 实例</span><span class="sxs-lookup"><span data-stu-id="b71c2-126">How to Rebuild the DAC Instance</span></span>|  
|------------|-------------------------------------|  
|<span data-ttu-id="b71c2-127">删除注册</span><span class="sxs-lookup"><span data-stu-id="b71c2-127">Delete registration</span></span>|<span data-ttu-id="b71c2-128">从原来的数据库中注册一个 DAC。</span><span class="sxs-lookup"><span data-stu-id="b71c2-128">Register a DAC from the database left in place.</span></span>|  
|<span data-ttu-id="b71c2-129">分离数据库</span><span class="sxs-lookup"><span data-stu-id="b71c2-129">Detach database</span></span>|<span data-ttu-id="b71c2-130">通过使用 **sp_attachdb** 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]重新附加数据库，然后从该数据库注册一个新的 DAC 实例。</span><span class="sxs-lookup"><span data-stu-id="b71c2-130">Re-attach the database by using **sp_attachdb** or [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], and then register a new DAC instance from the database.</span></span>|  
|<span data-ttu-id="b71c2-131">删除数据库</span><span class="sxs-lookup"><span data-stu-id="b71c2-131">Delete database</span></span>|<span data-ttu-id="b71c2-132">从在删除 DAC 前生成的完整备份还原数据库，然后从该数据库注册一个新的 DAC 实例。</span><span class="sxs-lookup"><span data-stu-id="b71c2-132">Restore the database from a full backup made before the DAC was deleted, and then register a new DAC instance from the database.</span></span>|  
  
> [!WARNING]  
>  <span data-ttu-id="b71c2-133">通过从还原或重新连接的数据库注册 DAC 重新生成一个 DAC 实例时，将不会重新创建该原始 DAC 的某些部分，例如服务器选择策略。</span><span class="sxs-lookup"><span data-stu-id="b71c2-133">Rebuilding a DAC instance by registering a DAC from a restored or re-attached database will not recreate some parts of the original DAC, such as the server selection policy.</span></span>  
  
###  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="b71c2-134">权限</span><span class="sxs-lookup"><span data-stu-id="b71c2-134">Permissions</span></span>  
 <span data-ttu-id="b71c2-135">只能由 **sysadmin** 或 **serveradmin** 固定服务器角色的成员删除 DAC，或者由数据库所有者删除。</span><span class="sxs-lookup"><span data-stu-id="b71c2-135">A DAC can only be deleted by members of the **sysadmin** or **serveradmin** fixed server roles, or by the database owner.</span></span> <span data-ttu-id="b71c2-136">名为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sa **的内置** 系统管理员帐户也可以启动该向导。</span><span class="sxs-lookup"><span data-stu-id="b71c2-136">The built-in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system administrator account named **sa** can also launch the wizard.</span></span>  
  
##  <a name="using-the-delete-data-tier-application-wizard"></a><a name="UsingDeleteDACWizard"></a> <span data-ttu-id="b71c2-137">使用“删除数据层应用程序向导”</span><span class="sxs-lookup"><span data-stu-id="b71c2-137">Using the Delete Data-tier Application Wizard</span></span>  
 <span data-ttu-id="b71c2-138">**使用向导删除 DAC**</span><span class="sxs-lookup"><span data-stu-id="b71c2-138">**To Delete a DAC Using a Wizard**</span></span>  
  
1.  <span data-ttu-id="b71c2-139">在 **“对象资源管理器”** 中，展开包含要删除的 DAC 的实例的节点。</span><span class="sxs-lookup"><span data-stu-id="b71c2-139">In **Object Explorer**, expand the node for the instance containing the DAC to be deleted.</span></span>  
  
2.  <span data-ttu-id="b71c2-140">展开 **“管理”** 节点。</span><span class="sxs-lookup"><span data-stu-id="b71c2-140">Expand the **Management** node.</span></span>  
  
3.  <span data-ttu-id="b71c2-141">展开 **数据层应用程序** 节点。</span><span class="sxs-lookup"><span data-stu-id="b71c2-141">Expand the **Data-tier Applications** node.</span></span>  
  
4.  <span data-ttu-id="b71c2-142">右键单击要删除的 DAC，然后选择“删除数据层应用程序…” </span><span class="sxs-lookup"><span data-stu-id="b71c2-142">Right-click the DAC to be deleted, and then select **Delete Data-tier Application...**</span></span>  
  
5.  <span data-ttu-id="b71c2-143">完成向导对话框：</span><span class="sxs-lookup"><span data-stu-id="b71c2-143">Complete the wizard dialogs:</span></span>  
  
    1.  [<span data-ttu-id="b71c2-144">简介</span><span class="sxs-lookup"><span data-stu-id="b71c2-144">Introduction</span></span>](#Introduction)  
  
    2.  [<span data-ttu-id="b71c2-145">选择方法</span><span class="sxs-lookup"><span data-stu-id="b71c2-145">Choose Method</span></span>](#Choose_method)  
  
    3.  [<span data-ttu-id="b71c2-146">摘要</span><span class="sxs-lookup"><span data-stu-id="b71c2-146">Summary</span></span>](#Summary)  
  
    4.  [<span data-ttu-id="b71c2-147">删除数据层应用程序</span><span class="sxs-lookup"><span data-stu-id="b71c2-147">Delete Data-tier Application</span></span>](#Delete_datatier_application)  
  
##  <a name="introduction-page"></a><a name="Introduction"></a> <span data-ttu-id="b71c2-148">“简介”页</span><span class="sxs-lookup"><span data-stu-id="b71c2-148">Introduction Page</span></span>  
 <span data-ttu-id="b71c2-149">此页描述用于删除数据层应用程序的各个步骤。</span><span class="sxs-lookup"><span data-stu-id="b71c2-149">This page describes the steps for deleting a data-tier application.</span></span>  
  
 <span data-ttu-id="b71c2-150">**不再显示此页。**</span><span class="sxs-lookup"><span data-stu-id="b71c2-150">**Do not show this page again.**</span></span> <span data-ttu-id="b71c2-151">- 选中该复选框可以停止在将来显示此页。</span><span class="sxs-lookup"><span data-stu-id="b71c2-151">- Click the check box to stop the page from being displayed in the future.</span></span>  
  
 <span data-ttu-id="b71c2-152">“下一步 >”  - 进入“选择方法”  页。</span><span class="sxs-lookup"><span data-stu-id="b71c2-152">**Next >** - Proceeds to the **Choose Method** page.</span></span>  
  
 <span data-ttu-id="b71c2-153">**取消** - 结束向导且不删除数据层应用程序或数据库。</span><span class="sxs-lookup"><span data-stu-id="b71c2-153">**Cancel** - Ends the wizard without deleting a data-tier application or database.</span></span>  
  
##  <a name="choose-method-page"></a><a name="Choose_method"></a><span data-ttu-id="b71c2-154">选择方法页</span><span class="sxs-lookup"><span data-stu-id="b71c2-154">Choose Method Page</span></span>  
 <span data-ttu-id="b71c2-155">使用此页可以指定用于处理与要删除的 DAC 关联的数据库的选项。</span><span class="sxs-lookup"><span data-stu-id="b71c2-155">Use this page to specify the option for handling the database associated with the DAC to be deleted.</span></span>  
  
 <span data-ttu-id="b71c2-156">**删除注册** - 删除用于定义数据层应用程序的元数据，但保持关联的数据库不变。</span><span class="sxs-lookup"><span data-stu-id="b71c2-156">**Delete registration** - Removes the metadata defining the data-tier application, but leaves the associated database intact.</span></span>  
  
 <span data-ttu-id="b71c2-157">**分离数据库** - 删除用于定义数据层应用程序的元数据并且分离关联的数据库。</span><span class="sxs-lookup"><span data-stu-id="b71c2-157">**Detach database** - Removes the metadata defining the data-tier application and detaches the associated database.</span></span>  
  
 <span data-ttu-id="b71c2-158">数据库不再被 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的该实例引用，但数据和日志文件保持不变。</span><span class="sxs-lookup"><span data-stu-id="b71c2-158">The database can no longer be referenced by that instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)], but the data and log files remain intact.</span></span>  
  
 <span data-ttu-id="b71c2-159">**删除数据库** - 删除用于定义 DAC 的元数据并且删除关联的数据库。</span><span class="sxs-lookup"><span data-stu-id="b71c2-159">**Delete database** - Removes the metadata defining the DAC and drops the associated database.</span></span>  
  
 <span data-ttu-id="b71c2-160">数据库的数据和日志文件被永久删除。</span><span class="sxs-lookup"><span data-stu-id="b71c2-160">The data and log files for the database are permanently deleted.</span></span>  
  
 <span data-ttu-id="b71c2-161">" \*\* \< 上一步**"-返回到 "**简介\*\*" 页。</span><span class="sxs-lookup"><span data-stu-id="b71c2-161">**\< Previous** - Returns to the **Introduction** page.</span></span>  
  
 <span data-ttu-id="b71c2-162">“下一步 >”\*\*\*\*- 继续到“摘要”\*\*\*\* 页。</span><span class="sxs-lookup"><span data-stu-id="b71c2-162">**Next >** - Proceeds to the **Summary** page.</span></span>  
  
 <span data-ttu-id="b71c2-163">**取消** - 结束向导且不删除 DAC 或数据库。</span><span class="sxs-lookup"><span data-stu-id="b71c2-163">**Cancel** - Ends the wizard without deleting the DAC or database.</span></span>  
  
##  <a name="summary-page"></a><a name="Summary"></a> <span data-ttu-id="b71c2-164">摘要页</span><span class="sxs-lookup"><span data-stu-id="b71c2-164">Summary Page</span></span>  
 <span data-ttu-id="b71c2-165">使用此页可以查看在删除 DAC 实例时向导将执行的操作。</span><span class="sxs-lookup"><span data-stu-id="b71c2-165">Use this page to review the actions the wizard will take when deleting the DAC instance.</span></span>  
  
 <span data-ttu-id="b71c2-166">**查看选择摘要** - 查看在该框中显示的 DAC、数据库和删除方法。</span><span class="sxs-lookup"><span data-stu-id="b71c2-166">**Review your selection summary** - Review the DAC, database, and deletion method displayed in the box.</span></span> <span data-ttu-id="b71c2-167">如果信息正确，则选择 **“下一步”** 或者 **“完成”** 以便删除 DAC。</span><span class="sxs-lookup"><span data-stu-id="b71c2-167">If the information is correct, select either **Next** or **Finish** to delete the DAC.</span></span> <span data-ttu-id="b71c2-168">如果 DAC 和数据库信息不正确，则选择 **“取消”** 并且选择正确的 DAC。</span><span class="sxs-lookup"><span data-stu-id="b71c2-168">If the DAC and database information is not correct, select **Cancel** and select the correct DAC.</span></span> <span data-ttu-id="b71c2-169">如果删除方法不正确，则选择 **“上一步”** 返回到 **“选择方法”** 页并且选择其他方法。</span><span class="sxs-lookup"><span data-stu-id="b71c2-169">If the deletion method is not correct, select **Previous** to return to the **Choose Method** page and select a different method.</span></span>  
  
 <span data-ttu-id="b71c2-170">" \*\* \< 上一步**"-返回到 "**选择方法\*\*" 页以选择其他删除方法。</span><span class="sxs-lookup"><span data-stu-id="b71c2-170">**\< Previous** - Returns to the **Choose Method** page to choose a different delete method.</span></span>  
  
 <span data-ttu-id="b71c2-171">**下一步 >** - 使用你在上一页中选择的方法删除 DAC 实例，并且继续到“删除数据层应用程序”\*\*\*\* 页。</span><span class="sxs-lookup"><span data-stu-id="b71c2-171">**Next >** - Deletes the DAC instance using the method you chose on the previous page, and proceeds to the **Delete Data-tier Application** page.</span></span>  
  
 <span data-ttu-id="b71c2-172">**取消** - 结束向导且不删除 DAC 实例。</span><span class="sxs-lookup"><span data-stu-id="b71c2-172">**Cancel** - Ends the wizard without deleting the DAC instance.</span></span>  
  
##  <a name="delete-data-tier-application-page"></a><a name="Delete_datatier_application"></a><span data-ttu-id="b71c2-173">"删除数据层应用程序" 页</span><span class="sxs-lookup"><span data-stu-id="b71c2-173">Delete Data-tier Application Page</span></span>  
 <span data-ttu-id="b71c2-174">此页报告删除操作是成功还是失败。</span><span class="sxs-lookup"><span data-stu-id="b71c2-174">This page reports the success or failure of the delete operation.</span></span>  
  
 <span data-ttu-id="b71c2-175">**删除 DAC** - 报告为删除 DAC 实例而执行的每个操作是成功还是失败。</span><span class="sxs-lookup"><span data-stu-id="b71c2-175">**Deleting the DAC** - Reports the success or failure of each action taken to delete the DAC instance.</span></span> <span data-ttu-id="b71c2-176">查看信息以便确定每个操作是成功还是失败。</span><span class="sxs-lookup"><span data-stu-id="b71c2-176">Review the information to determine the success or failure of each action.</span></span> <span data-ttu-id="b71c2-177">遇到了错误的任何操作都将在 **“结果”** 列中具有一个链接。</span><span class="sxs-lookup"><span data-stu-id="b71c2-177">Any action that encountered an error will have a link in the **Result** column.</span></span> <span data-ttu-id="b71c2-178">选择该链接可以查看针对该操作的错误报告。</span><span class="sxs-lookup"><span data-stu-id="b71c2-178">Select the link to view a report of the error for that action.</span></span>  
  
 <span data-ttu-id="b71c2-179">**保存报表** - 选择此按钮可以将删除报表保存到某一 HTML 文件。</span><span class="sxs-lookup"><span data-stu-id="b71c2-179">**Save Report** - Select this button to save the deletion report to an HTML file.</span></span> <span data-ttu-id="b71c2-180">该文件报告每个操作的状态，并且包括任何操作生成的所有错误。</span><span class="sxs-lookup"><span data-stu-id="b71c2-180">The file reports the status of each action, including all errors generated by any of the actions.</span></span> <span data-ttu-id="b71c2-181">默认文件夹是您的 Windows 帐户的 Documents 文件夹中的 SQL Server Management Studio\DAC Packages 文件夹。</span><span class="sxs-lookup"><span data-stu-id="b71c2-181">The default folder is a SQL Server Management Studio\DAC Packages folder in the Documents folder of your Windows account..</span></span>  
  
 <span data-ttu-id="b71c2-182">**完成** - 结束向导。</span><span class="sxs-lookup"><span data-stu-id="b71c2-182">**Finish** - Ends the wizard.</span></span>  
  
##  <a name="delete-a-dac-using-powershell"></a><a name="DeleteDACPowerShell"></a><span data-ttu-id="b71c2-183">使用 PowerShell 删除 DAC</span><span class="sxs-lookup"><span data-stu-id="b71c2-183">Delete a DAC Using PowerShell</span></span>  
 <span data-ttu-id="b71c2-184">**使用 PowerShell 脚本删除 DAC**</span><span class="sxs-lookup"><span data-stu-id="b71c2-184">**To delete a DAC using a PowerShell script**</span></span>  
  
1.  <span data-ttu-id="b71c2-185">创建一个 SMO Server 对象，并且将该对象设置为包含要删除的 DAC 的实例。</span><span class="sxs-lookup"><span data-stu-id="b71c2-185">Create a SMO Server object and set it to the instance that contains the DAC to be deleted.</span></span>  
  
2.  <span data-ttu-id="b71c2-186">打开 `ServerConnection` 对象，并连接到同一实例。</span><span class="sxs-lookup"><span data-stu-id="b71c2-186">Open a `ServerConnection` object and connect to the same instance.</span></span>  
  
3.  <span data-ttu-id="b71c2-187">使用 `add_DacActionStarted` 和 `add_DacActionFinished` 订阅 DAC 升级事件。</span><span class="sxs-lookup"><span data-stu-id="b71c2-187">Use `add_DacActionStarted` and `add_DacActionFinished` to subscribe to the DAC upgrade events.</span></span>  
  
4.  <span data-ttu-id="b71c2-188">指定要删除的 DAC。</span><span class="sxs-lookup"><span data-stu-id="b71c2-188">Specify the DAC to delete.</span></span>  
  
5.  <span data-ttu-id="b71c2-189">根据适合的删除选项，使用以下三个代码集之一：</span><span class="sxs-lookup"><span data-stu-id="b71c2-189">Use one of these three sets of code, depending on which delete option is appropriate:</span></span>  
  
    -   <span data-ttu-id="b71c2-190">若要删除 DAC 注册但保持数据库不变，请使用 `Unmanage()` 方法。</span><span class="sxs-lookup"><span data-stu-id="b71c2-190">To delete the DAC registration but leave the database intact, use the `Unmanage()` method.</span></span>  
  
    -   <span data-ttu-id="b71c2-191">若要删除 DAC 注册并分离数据库，请使用 `Uninstall()` 方法并指定 `DetachDatabase`。</span><span class="sxs-lookup"><span data-stu-id="b71c2-191">To delete the DAC registration and detach the database, use the `Uninstall()` method and specify `DetachDatabase`.</span></span>  
  
    -   <span data-ttu-id="b71c2-192">若要删除 DAC 注册并删除数据库，请使用 `Uninstall()` 方法并指定 `DropDatabase`。</span><span class="sxs-lookup"><span data-stu-id="b71c2-192">To delete the DAC registration and drop the database, use the `Uninstall()` method and specify `DropDatabase`.</span></span>  
  
### <a name="example-deleting-the-dac-but-leaving-the-database-powershell"></a><span data-ttu-id="b71c2-193">删除 DAC 但保留数据库的示例 (PowerShell)</span><span class="sxs-lookup"><span data-stu-id="b71c2-193">Example Deleting the DAC but Leaving the Database (PowerShell)</span></span>  
 <span data-ttu-id="b71c2-194">下面的示例通过使用 `Unmanage()` 方法删除 DAC 但保持数据库不变来删除名为 MyApplication 的 DAC。</span><span class="sxs-lookup"><span data-stu-id="b71c2-194">The following example deletes a DAC named MyApplication using the `Unmanage()` method to delete the DAC but leave the database intact.</span></span>  
  
```powershell
## Set a SMO Server object to the default instance on the local computer.  
CD SQLSERVER:\SQL\localhost\DEFAULT  
$srv = Get-Item .  
  
## Open a Common.ServerConnection to the same instance.  
$serverconnection = New-Object Microsoft.SqlServer.Management.Common.ServerConnection($srv.ConnectionContext.SqlConnectionObject)  
$serverconnection.Connect()  
$dacstore = New-Object Microsoft.SqlServer.Management.Dac.DacStore($serverconnection)  
  
## Subscribe to the DAC delete events.  
$dacstore.add_DacActionStarted({Write-Host `n`nStarting at $(get-date) :: $_.Description})  
$dacstore.add_DacActionFinished({Write-Host Completed at $(get-date) :: $_.Description})  
  
## Specify the DAC to delete.  
$dacName  = "MyApplication"  
  
## Only delete the DAC definition from msdb, the associated database remains active.  
$dacstore.Unmanage($dacName)  
```  
  
### <a name="example-deleting-the-dac-and-detaching-the-database-powershell"></a><span data-ttu-id="b71c2-195">删除 DAC 并且分离数据库的示例 (PowerShell)</span><span class="sxs-lookup"><span data-stu-id="b71c2-195">Example Deleting the DAC and Detaching the Database (PowerShell)</span></span>  
 <span data-ttu-id="b71c2-196">下面的示例通过使用 `Uninstall()` 方法删除 DAC 且分离数据库来删除名为 MyApplication 的 DAC。</span><span class="sxs-lookup"><span data-stu-id="b71c2-196">The following example deletes a DAC named MyApplication using the `Uninstall()` method to delete the DAC and detach the database.</span></span>  
  
```powershell
## Set a SMO Server object to the default instance on the local computer.  
CD SQLSERVER:\SQL\localhost\DEFAULT  
$srv = get-item .  
  
## Open a Common.ServerConnection to the same instance.  
$serverconnection = New-Object Microsoft.SqlServer.Management.Common.ServerConnection($srv.ConnectionContext.SqlConnectionObject)  
$serverconnection.Connect()  
$dacstore = New-Object Microsoft.SqlServer.Management.Dac.DacStore($serverconnection)  
  
## Subscribe to the DAC delete events.  
$dacstore.add_DacActionStarted({Write-Host `n`nStarting at $(get-date) :: $_.Description})  
$dacstore.add_DacActionFinished({Write-Host Completed at $(get-date) :: $_.Description})  
  
## Specify the DAC to delete.  
$dacName  = "MyApplication"  
  
## Delete the DAC definition from msdb and detach the associated database.  
$dacstore.Uninstall($dacName, [Microsoft.SqlServer.Management.Dac.DacUninstallMode]::DetachDatabase)  
```  
  
### <a name="example-deleting-the-dac-and-dropping-the-database-powershell"></a><span data-ttu-id="b71c2-197">删除 DAC 并且删除数据库的示例 (PowerShell)</span><span class="sxs-lookup"><span data-stu-id="b71c2-197">Example Deleting the DAC and Dropping the Database (PowerShell)</span></span>  
 <span data-ttu-id="b71c2-198">下面的示例通过使用 `Uninstall()` 方法删除 DAC 且删除数据库来删除名为 MyApplication 的 DAC。</span><span class="sxs-lookup"><span data-stu-id="b71c2-198">The following example deletes a DAC named MyApplication using the `Uninstall()` method to delete the DAC and drop the database.</span></span>  
  
```powershell
## Set a SMO Server object to the default instance on the local computer.  
CD SQLSERVER:\SQL\localhost\DEFAULT  
$srv = Get-Item .  
  
## Open a Common.ServerConnection to the same instance.  
$serverconnection = New-Object Microsoft.SqlServer.Management.Common.ServerConnection($srv.ConnectionContext.SqlConnectionObject)  
$serverconnection.Connect()  
$dacstore = New-Object Microsoft.SqlServer.Management.Dac.DacStore($serverconnection)  
  
## Subscribe to the DAC delete events.  
$dacstore.add_DacActionStarted({Write-Host `n`nStarting at $(get-date) :: $_.Description})  
$dacstore.add_DacActionFinished({Write-Host Completed at $(get-date) :: $_.Description})  
  
## Specify the DAC to delete.  
$dacName  = "MyApplication"  
  
## Delete the DAC definition from msdb and drop the associated database.  
## $dacstore.Uninstall($dacName, [Microsoft.SqlServer.Management.Dac.DacUninstallMode]::DropDatabase)  
```  
  
## <a name="see-also"></a><span data-ttu-id="b71c2-199">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b71c2-199">See Also</span></span>  
 <span data-ttu-id="b71c2-200">[数据层应用程序](data-tier-applications.md) </span><span class="sxs-lookup"><span data-stu-id="b71c2-200">[Data-tier Applications](data-tier-applications.md) </span></span>  
 <span data-ttu-id="b71c2-201">[数据层应用程序](data-tier-applications.md) </span><span class="sxs-lookup"><span data-stu-id="b71c2-201">[Data-tier Applications](data-tier-applications.md) </span></span>  
 <span data-ttu-id="b71c2-202">[部署数据层应用程序](deploy-a-data-tier-application.md) </span><span class="sxs-lookup"><span data-stu-id="b71c2-202">[Deploy a Data-tier Application](deploy-a-data-tier-application.md) </span></span>  
 <span data-ttu-id="b71c2-203">[将数据库注册为 DAC](register-a-database-as-a-dac.md) </span><span class="sxs-lookup"><span data-stu-id="b71c2-203">[Register a Database As a DAC](register-a-database-as-a-dac.md) </span></span>  
 <span data-ttu-id="b71c2-204">[SQL Server 数据库的备份和还原](../backup-restore/back-up-and-restore-of-sql-server-databases.md) </span><span class="sxs-lookup"><span data-stu-id="b71c2-204">[Back Up and Restore of SQL Server Databases](../backup-restore/back-up-and-restore-of-sql-server-databases.md) </span></span>  
 [<span data-ttu-id="b71c2-205">数据库分离和附加 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="b71c2-205">Database Detach and Attach &#40;SQL Server&#41;</span></span>](../databases/database-detach-and-attach-sql-server.md)  
