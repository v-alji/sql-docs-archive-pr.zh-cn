---
title: 将数据库注册为 DAC | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.registerdacwizard.registerdac.f1
- sql12.swb.registerdacwizard.summary.f1
- sql12.swb.registerdacwizard.introduction.f1
- sql12.swb.registerdacwizard.setproperties.f1
helpviewer_keywords:
- wizard [DAC], register
- How to [DAC], register
- register DAC
- data-tier application [SQL Server], register
ms.assetid: 08e52aa6-12f3-41dd-a793-14b99a083fd5
author: stevestein
ms.author: sstein
ms.openlocfilehash: c4e8061362d013dbfbd6cbaba47d0f2cb4d8e83b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591379"
---
# <a name="register-a-database-as-a-dac"></a><span data-ttu-id="998a2-102">将数据库注册为 DAC</span><span class="sxs-lookup"><span data-stu-id="998a2-102">Register a Database As a DAC</span></span>
  <span data-ttu-id="998a2-103">使用 "**注册数据层应用程序向导**" 或 Windows PowerShell 脚本生成数据层应用程序 () DAC 描述现有数据库中对象的数据层应用程序，并在) 中的 " `msdb` master" (**主**数据库中注册 dac 定义 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="998a2-103">Use either the **Register Data-tier Application Wizard** or a Windows PowerShell script to build a data-tier application (DAC) definition that describes the objects in an existing database, and register the DAC definition in the `msdb` system database (**master** in [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]).</span></span>  
  
-   <span data-ttu-id="998a2-104">**开始之前：** [限制和局限](#LimitationsRestrictions)、[权限](#Permissions)</span><span class="sxs-lookup"><span data-stu-id="998a2-104">**Before you begin:**  [Limitations and Restrictions](#LimitationsRestrictions), [Permissions](#Permissions)</span></span>  
  
-   <span data-ttu-id="998a2-105">若要升级 DAC，请使用：[注册数据层应用程序向导](#UsingRegisterDACWizard)、[PowerShell](#RegisterDACPowerShell)</span><span class="sxs-lookup"><span data-stu-id="998a2-105">**To upgrade a DAC, using:**  [The Register Data-tier Application Wizard](#UsingRegisterDACWizard), [PowerShell](#RegisterDACPowerShell)</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="998a2-106">开始之前</span><span class="sxs-lookup"><span data-stu-id="998a2-106">Before You Begin</span></span>  
 <span data-ttu-id="998a2-107">注册过程将创建用于定义数据库中的对象的 DAC 定义。</span><span class="sxs-lookup"><span data-stu-id="998a2-107">The registration process creates a DAC definition that defines the objects in the database.</span></span> <span data-ttu-id="998a2-108">DAC 定义与数据库的组合构成一个 DAC 实例。</span><span class="sxs-lookup"><span data-stu-id="998a2-108">The combination of the DAC definition and the database form a DAC instance.</span></span> <span data-ttu-id="998a2-109">如果在数据库引擎的托管实例上将数据库注册为 DAC，则在下次将实用工具收集组从该实例发送到实用工具控制点时，已注册的 DAC 将合并到 SQL Server 实用工具中。</span><span class="sxs-lookup"><span data-stu-id="998a2-109">If you register a database as a DAC on a managed instance of the Database Engine, the registered DAC will be incorporated into the SQL Server Utility the next time the utility collection set is sent from the instance to the Utility Control Point.</span></span> <span data-ttu-id="998a2-110">然后，该 DAC 将出现在 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 实用工具资源管理器的“已部署的数据层应用程序”节点中，并且将在“已部署的数据层应用程序”的详细信息页面中报告  。</span><span class="sxs-lookup"><span data-stu-id="998a2-110">The DAC will then be present in the **Deployed Data-tier Applications** node of the [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] **Utility Explorer** and reported in the **Deployed Data-tier Applications** details page.</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> <span data-ttu-id="998a2-111">限制和局限</span><span class="sxs-lookup"><span data-stu-id="998a2-111">Limitations and Restrictions</span></span>  
 <span data-ttu-id="998a2-112">只能在 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]、 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 4 (SP4) 或更高版本的数据库上执行 DAC 注册。</span><span class="sxs-lookup"><span data-stu-id="998a2-112">DAC registration can only be performed on a database in [!INCLUDE[ssSDS](../../includes/sssds-md.md)], or [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 4 (SP4) or later.</span></span> <span data-ttu-id="998a2-113">如果已为数据库注册了 DAC，则无法执行 DAC 注册。</span><span class="sxs-lookup"><span data-stu-id="998a2-113">DAC registration cannot be performed if a DAC is already registered for the database.</span></span> <span data-ttu-id="998a2-114">例如，如果数据库是通过部署 DAC 创建的，则无法运行 “注册数据层应用程序向导”。</span><span class="sxs-lookup"><span data-stu-id="998a2-114">For example, if the database was created by deploying a DAC, you cannot run the **Register Data-tier Application Wizard**.</span></span>  
  
 <span data-ttu-id="998a2-115">如果数据库有 DAC 中不支持的对象或包含的用户，则不能注册 DAC。</span><span class="sxs-lookup"><span data-stu-id="998a2-115">You cannot register a DAC if the database has objects that are not supported in a DAC, or contained users.</span></span> <span data-ttu-id="998a2-116">有关 DAC 中支持的对象类型的详细信息，请参阅 [DAC Support For SQL Server Objects and Versions](dac-support-for-sql-server-objects-and-versions.md)。</span><span class="sxs-lookup"><span data-stu-id="998a2-116">For more information about the types of objects supported in a DAC, see [DAC Support For SQL Server Objects and Versions](dac-support-for-sql-server-objects-and-versions.md).</span></span>  
  
###  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="998a2-117">权限</span><span class="sxs-lookup"><span data-stu-id="998a2-117">Permissions</span></span>  
 <span data-ttu-id="998a2-118">在 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 实例中注册 DAC 至少需要 ALTER ANY LOGIN 和数据库范围 VIEW DEFINITION 权限，对 **sys.sql_expression_dependencies**具有 SELECT 权限，且具备 **dbcreator** 固定服务器角色的成员身份。</span><span class="sxs-lookup"><span data-stu-id="998a2-118">Registering a DAC in an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] requires at least ALTER ANY LOGIN and database scope VIEW DEFINITION permissions, SELECT permissions on **sys.sql_expression_dependencies**, and membership in the **dbcreator** fixed server role.</span></span> <span data-ttu-id="998a2-119">**sysadmin** 固定服务器角色的成员或名为 **sa** 的内置 SQL Server 系统管理员帐户也可以注册 DAC。</span><span class="sxs-lookup"><span data-stu-id="998a2-119">Members of the **sysadmin** fixed server role or the built-in SQL Server system administrator account named **sa** can also register a DAC.</span></span> <span data-ttu-id="998a2-120">注册在 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 中不包含登录名的 DAC 要求具有 **dbmanager** 或 **serveradmin** 角色的成员身份。</span><span class="sxs-lookup"><span data-stu-id="998a2-120">Registering a DAC that does not contain logins in [!INCLUDE[ssSDS](../../includes/sssds-md.md)] requires membership in the **dbmanager** or **serveradmin** roles.</span></span> <span data-ttu-id="998a2-121">注册在 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 中包含登录名的 DAC 要求具有 **loginmanager** 或 **serveradmin** 角色的成员身份。</span><span class="sxs-lookup"><span data-stu-id="998a2-121">Registering a DAC that contains logins in [!INCLUDE[ssSDS](../../includes/sssds-md.md)] requires membership in the **loginmanager** or **serveradmin** roles.</span></span>  
  
##  <a name="using-the-register-data-tier-application-wizard"></a><a name="UsingRegisterDACWizard"></a> <span data-ttu-id="998a2-122">使用注册数据层应用程序向导</span><span class="sxs-lookup"><span data-stu-id="998a2-122">Using the Register Data-tier Application Wizard</span></span>  
 <span data-ttu-id="998a2-123">**使用向导注册 DAC**</span><span class="sxs-lookup"><span data-stu-id="998a2-123">**To Register a DAC Using a Wizard**</span></span>  
  
1.  <span data-ttu-id="998a2-124">在 **“对象资源管理器”** 中，展开包含要注册为 DAC 的数据库的实例的节点。</span><span class="sxs-lookup"><span data-stu-id="998a2-124">In **Object Explorer**, expand the node for the instance containing the database to be registered as a DAC.</span></span>  
  
2.  <span data-ttu-id="998a2-125">展开 **“数据库”** 节点。</span><span class="sxs-lookup"><span data-stu-id="998a2-125">Expand the **Databases** node.</span></span>  
  
3.  <span data-ttu-id="998a2-126">右键单击要注册的数据库，指向“任务”，然后选择“注册为数据层应用程序...” </span><span class="sxs-lookup"><span data-stu-id="998a2-126">Right-click the database to be registered, point to **Tasks**, and then select **Register As Data-tier Application...**</span></span>  
  
4.  <span data-ttu-id="998a2-127">完成向导对话框：</span><span class="sxs-lookup"><span data-stu-id="998a2-127">Complete the wizard dialogs:</span></span>  
  
    1.  [<span data-ttu-id="998a2-128">“简介”页</span><span class="sxs-lookup"><span data-stu-id="998a2-128">Introduction Page</span></span>](#Introduction)  
  
    2.  [<span data-ttu-id="998a2-129">“设置属性”页</span><span class="sxs-lookup"><span data-stu-id="998a2-129">Set Properties Page</span></span>](#Set_properties)  
  
    3.  [<span data-ttu-id="998a2-130">“验证和摘要”页</span><span class="sxs-lookup"><span data-stu-id="998a2-130">Validation and Summary Page</span></span>](#Summary)  
  
    4.  [<span data-ttu-id="998a2-131">“注册 DAC”页</span><span class="sxs-lookup"><span data-stu-id="998a2-131">Register DAC Page</span></span>](#Register)  
  
##  <a name="introduction-page"></a><a name="Introduction"></a> <span data-ttu-id="998a2-132">“简介”页</span><span class="sxs-lookup"><span data-stu-id="998a2-132">Introduction Page</span></span>  
 <span data-ttu-id="998a2-133">此页描述用于注册数据层应用程序的各个步骤。</span><span class="sxs-lookup"><span data-stu-id="998a2-133">This page describes the steps for registering a data-tier application.</span></span>  
  
 <span data-ttu-id="998a2-134">**不再显示此页。**</span><span class="sxs-lookup"><span data-stu-id="998a2-134">**Do not show this page again.**</span></span> <span data-ttu-id="998a2-135">- 选中该复选框可以停止在将来显示此页。</span><span class="sxs-lookup"><span data-stu-id="998a2-135">- Click the check box to stop the page from being displayed in the future.</span></span>  
  
 <span data-ttu-id="998a2-136">“下一步>”- 进入“设置属性”页。</span><span class="sxs-lookup"><span data-stu-id="998a2-136">**Next >** - Proceeds to the **Set Properties** page.</span></span>  
  
 <span data-ttu-id="998a2-137"> “取消”- 终止向导而不注册 DAC。</span><span class="sxs-lookup"><span data-stu-id="998a2-137">**Cancel** - Terminates the wizard without registering a DAC.</span></span>  
  
##  <a name="set-properties-page"></a><a name="Set_properties"></a> <span data-ttu-id="998a2-138">“设置属性”页</span><span class="sxs-lookup"><span data-stu-id="998a2-138">Set Properties Page</span></span>  
 <span data-ttu-id="998a2-139">使用此页可指定 DAC 级别的属性，如应用程序名称和版本。</span><span class="sxs-lookup"><span data-stu-id="998a2-139">Use this page to specify DAC-level properties such as the application name and version.</span></span>  
  
 <span data-ttu-id="998a2-140">**应用程序名称。**</span><span class="sxs-lookup"><span data-stu-id="998a2-140">**Application name.**</span></span> <span data-ttu-id="998a2-141">- 指定用于标识 DAC 定义的名称的字符串，该字段用数据库名称进行填充。</span><span class="sxs-lookup"><span data-stu-id="998a2-141">- A string that specifies the name used to identify the DAC definition, the field is been populated with the database name.</span></span>  
  
 <span data-ttu-id="998a2-142">**版本。**</span><span class="sxs-lookup"><span data-stu-id="998a2-142">**Version.**</span></span> <span data-ttu-id="998a2-143">- 标识 DAC 版本的数值。</span><span class="sxs-lookup"><span data-stu-id="998a2-143">- A numeric value that identifies the version of the DAC.</span></span> <span data-ttu-id="998a2-144">该 DAC 版本用于 Visual Studio 中，以便标识开发人员正在处理的 DAC 的版本。</span><span class="sxs-lookup"><span data-stu-id="998a2-144">The DAC version is used in Visual Studio to identify the version of the DAC that developers are working on.</span></span> <span data-ttu-id="998a2-145">部署 DAC 时，该版本存储在数据库中， `msdb` 并且以后可以在中的 "**数据层应用程序**" 节点下查看 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="998a2-145">When deploying a DAC, the version is stored in the `msdb` database and can later be viewed under the **Data-tier Applications** node in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="998a2-146">**说明。**</span><span class="sxs-lookup"><span data-stu-id="998a2-146">**Description.**</span></span> <span data-ttu-id="998a2-147">- 可选。</span><span class="sxs-lookup"><span data-stu-id="998a2-147">- Optional.</span></span> <span data-ttu-id="998a2-148">用来说明 DAC 用途的文本。</span><span class="sxs-lookup"><span data-stu-id="998a2-148">Text that explains the purpose of the DAC.</span></span> <span data-ttu-id="998a2-149">部署 DAC 时，说明存储在数据库中， `msdb` 并且以后可以在中的 "**数据层应用程序**" 节点下查看 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="998a2-149">When deploying a DAC, the description is stored in the `msdb` database and can later be viewed under the **Data-tier Applications** node in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span>  
  
 <span data-ttu-id="998a2-150">" \*\* \< 上一步**"-返回到 "**简介\*\*" 页。</span><span class="sxs-lookup"><span data-stu-id="998a2-150">**\< Previous** - Returns you to the **Introduction** page.</span></span>  
  
 <span data-ttu-id="998a2-151">“下一步>”- 验证 DAC 是否可从数据库中的对象生成，并在“验证和摘要”页中显示结果。</span><span class="sxs-lookup"><span data-stu-id="998a2-151">**Next >** - Verifies that a DAC can be built from the objects in the database, and displays the results in the **Validation and Summary** page.</span></span>  
  
 <span data-ttu-id="998a2-152"> “取消”- 终止向导而不注册 DAC。</span><span class="sxs-lookup"><span data-stu-id="998a2-152">**Cancel** - Terminates the wizard without registering the DAC.</span></span>  
  
##  <a name="validation-and-summary-page"></a><a name="Summary"></a> <span data-ttu-id="998a2-153">“验证和摘要”页</span><span class="sxs-lookup"><span data-stu-id="998a2-153">Validation and Summary Page</span></span>  
 <span data-ttu-id="998a2-154">使用此页可以查看在注册 DAC 时向导将执行的操作。</span><span class="sxs-lookup"><span data-stu-id="998a2-154">Use this page to review the actions the wizard will take when registering the DAC.</span></span> <span data-ttu-id="998a2-155">当该页验证可从数据库的对象中生成 DAC 时，它将经历三个状态。</span><span class="sxs-lookup"><span data-stu-id="998a2-155">The page transitions through three states as it verifies that a DAC can be built from the objects in the database.</span></span>  
  
### <a name="retrieving-objects"></a><span data-ttu-id="998a2-156">检索对象</span><span class="sxs-lookup"><span data-stu-id="998a2-156">Retrieving Objects</span></span>  
 <span data-ttu-id="998a2-157">**检索数据库和服务器对象。**</span><span class="sxs-lookup"><span data-stu-id="998a2-157">**Retrieving database and server objects.**</span></span> <span data-ttu-id="998a2-158">- 当该向导从数据库和数据库引擎实例中检索所有所需对象时，将显示一个进度栏。</span><span class="sxs-lookup"><span data-stu-id="998a2-158">- Displays a progress bar as the wizard retrieves all of the required objects from the database and the instance of the Database Engine.</span></span>  
  
 <span data-ttu-id="998a2-159">" \*\* \< 上一步**"-返回到 "**设置属性\*\*" 页以更改你的条目。</span><span class="sxs-lookup"><span data-stu-id="998a2-159">**\< Previous** - Returns you to the **Set Properties** page to change your entries.</span></span>  
  
 <span data-ttu-id="998a2-160">“下一步>”- 注册 DAC 并在“注册 DAC”页中显示结果。</span><span class="sxs-lookup"><span data-stu-id="998a2-160">**Next >** - Registers the DAC and displays the results in the **Register DAC** page.</span></span>  
  
 <span data-ttu-id="998a2-161"> “取消”- 终止向导而不注册 DAC。</span><span class="sxs-lookup"><span data-stu-id="998a2-161">**Cancel** - Terminates the wizard without registering the DAC.</span></span>  
  
### <a name="validating-objects"></a><span data-ttu-id="998a2-162">验证对象</span><span class="sxs-lookup"><span data-stu-id="998a2-162">Validating Objects</span></span>  
 <span data-ttu-id="998a2-163">检查 SchemaName.</span><span class="sxs-lookup"><span data-stu-id="998a2-163">**Checking**  _SchemaName_ **.**</span></span> <span data-ttu-id="998a2-164">ObjectName.</span><span class="sxs-lookup"><span data-stu-id="998a2-164">_ObjectName_ **.**</span></span> <span data-ttu-id="998a2-165">- 当该向导验证所检索对象的依赖项并验证这些对象都是用于 DAC 的有效对象时，将显示一个进度栏。</span><span class="sxs-lookup"><span data-stu-id="998a2-165">- Displays a progress bar as the wizard verifies the dependencies of the retrieved objects, and verifies that they are all valid objects for a DAC.</span></span> <span data-ttu-id="998a2-166">_SchemaName_ **.** _ObjectName_ 确定当前正在验证的对象。</span><span class="sxs-lookup"><span data-stu-id="998a2-166">_SchemaName_**.**_ObjectName_ identify which object is currently being verified.</span></span>  
  
 <span data-ttu-id="998a2-167">" \*\* \< 上一步**"-返回到 "**设置属性\*\*" 页以更改你的条目。</span><span class="sxs-lookup"><span data-stu-id="998a2-167">**\< Previous** - Returns you to the **Set Properties** page to change your entries.</span></span>  
  
 <span data-ttu-id="998a2-168">“下一步>”- 注册 DAC 并在“注册 DAC”页中显示结果。</span><span class="sxs-lookup"><span data-stu-id="998a2-168">**Next >** - Registers the DAC and displays the results in the **Register DAC** page.</span></span>  
  
 <span data-ttu-id="998a2-169"> “取消”- 终止向导而不注册 DAC。</span><span class="sxs-lookup"><span data-stu-id="998a2-169">**Cancel** - Terminates the wizard without registering the DAC.</span></span>  
  
### <a name="summary"></a><span data-ttu-id="998a2-170">总结</span><span class="sxs-lookup"><span data-stu-id="998a2-170">Summary</span></span>  
 <span data-ttu-id="998a2-171">**将使用以下设置注册 DAC。**</span><span class="sxs-lookup"><span data-stu-id="998a2-171">**The following setting will be used to register your DAC.**</span></span> <span data-ttu-id="998a2-172">- 显示将包含在 DAC 中的属性和对象的报表。</span><span class="sxs-lookup"><span data-stu-id="998a2-172">- Displays a report of the properties and objects that will be included in the DAC.</span></span>  
  
 <span data-ttu-id="998a2-173"> “保存报表”- 选择此按钮可以将验证报表的副本保存到某一 HTML 文件。</span><span class="sxs-lookup"><span data-stu-id="998a2-173">**Save Report** - Select this button to save a copy of the validation report to an HTML file.</span></span> <span data-ttu-id="998a2-174">默认文件夹是你 Windows 帐户的 Documents 文件夹中的 **SQL Server Management Studio\DAC Packages** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="998a2-174">The default folder is a **SQL Server Management Studio\DAC Packages** folder in the Documents folder of your Windows account.</span></span>  
  
 <span data-ttu-id="998a2-175">" \*\* \< 上一步**"-返回到 "**设置属性\*\*" 页以更改你的条目。</span><span class="sxs-lookup"><span data-stu-id="998a2-175">**\< Previous** - Returns you to the **Set Properties** page to change your entries.</span></span>  
  
 <span data-ttu-id="998a2-176">“下一步>”- 注册 DAC 并在“注册 DAC”页中显示结果。</span><span class="sxs-lookup"><span data-stu-id="998a2-176">**Next >** - Registers the DAC and displays the results in the **Register DAC** page.</span></span>  
  
 <span data-ttu-id="998a2-177"> “取消”- 终止向导而不注册 DAC。</span><span class="sxs-lookup"><span data-stu-id="998a2-177">**Cancel** - Terminates the wizard without registering the DAC.</span></span>  
  
##  <a name="register-dac-page"></a><a name="Register"></a> <span data-ttu-id="998a2-178">“注册 DAC”页</span><span class="sxs-lookup"><span data-stu-id="998a2-178">Register DAC Page</span></span>  
 <span data-ttu-id="998a2-179">此页报告注册成功与否。</span><span class="sxs-lookup"><span data-stu-id="998a2-179">This page reports the success or failure of the registration.</span></span>  
  
 <span data-ttu-id="998a2-180"> “注册 DAC”- 报告为注册 DAC 而执行的每个操作成功与否。</span><span class="sxs-lookup"><span data-stu-id="998a2-180">**Registering the DAC** - Reports the success or failure of each action taken to register the DAC.</span></span> <span data-ttu-id="998a2-181">查看信息以便确定每个操作是成功还是失败。</span><span class="sxs-lookup"><span data-stu-id="998a2-181">Review the information to determine the success or failure of each action.</span></span> <span data-ttu-id="998a2-182">遇到了错误的任何操作都将在 **“结果”** 列中具有一个链接。</span><span class="sxs-lookup"><span data-stu-id="998a2-182">Any action that encountered an error will have a link in the **Result** column.</span></span> <span data-ttu-id="998a2-183">选择该链接可以查看针对该操作的错误报告。</span><span class="sxs-lookup"><span data-stu-id="998a2-183">Select the link to view a report of the error for that action.</span></span>  
  
 <span data-ttu-id="998a2-184"> “保存报表”- 选择此按钮可以将注册报表保存到某一 HTML 文件。</span><span class="sxs-lookup"><span data-stu-id="998a2-184">**Save Report** - Select this button to save the registration report to an HTML file.</span></span> <span data-ttu-id="998a2-185">该文件报告每个操作的状态，并且包括任何操作生成的所有错误。</span><span class="sxs-lookup"><span data-stu-id="998a2-185">The file reports the status of each action, including all errors generated by any of the actions.</span></span> <span data-ttu-id="998a2-186">默认文件夹是你 Windows 帐户的 Documents 文件夹中的 **SQL Server Management Studio\DAC Packages** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="998a2-186">The default folder is a **SQL Server Management Studio\DAC Packages** folder in the Documents folder of your Windows account.</span></span> <span data-ttu-id="998a2-187">文件名采用 \<DACPackageName>_RegisterDACReport_yyyymmdd.html 的格式，其中，\<*DACPackageName*> 是所部署的包的名称，yyyy = 当前年份，mm = 当前月份，dd = 当前日期  。</span><span class="sxs-lookup"><span data-stu-id="998a2-187">The file name is in the format \<DACPackageName>_RegisterDACReport_yyyymmdd.html, where \<*DACPackageName*> is the name of the package being deployed, *yyyy* = the current year, *mm* = the current month, and *dd* = the current day.</span></span>  
  
 <span data-ttu-id="998a2-188">“完成” - 终止向导。</span><span class="sxs-lookup"><span data-stu-id="998a2-188">**Finish** - Terminates the wizard.</span></span>  
  
##  <a name="register-a-dac-using-powershell"></a><a name="RegisterDACPowerShell"></a> <span data-ttu-id="998a2-189">使用 PowerShell 注册 DAC</span><span class="sxs-lookup"><span data-stu-id="998a2-189">Register a DAC Using PowerShell</span></span>  
 <span data-ttu-id="998a2-190">**在 PowerShell 脚本中使用 Register() 方法将数据库注册为 DAC**</span><span class="sxs-lookup"><span data-stu-id="998a2-190">**To register a database as a DAC using the Register() method in a PowerShell script**</span></span>  
  
1.  <span data-ttu-id="998a2-191">创建一个 SMO Server 对象，并且将该对象设置为包含要注册为 DAC 的数据库的实例。</span><span class="sxs-lookup"><span data-stu-id="998a2-191">Create a SMO Server object and set it to the instance that contains the database to be registered as a DAC.</span></span>  
  
2.  <span data-ttu-id="998a2-192">添加一个指定数据库名称的变量。</span><span class="sxs-lookup"><span data-stu-id="998a2-192">Add a variable that specifies the name of the database.</span></span>  
  
3.  <span data-ttu-id="998a2-193">指定 DAC 的元数据，如 DAC 名称、版本和说明。</span><span class="sxs-lookup"><span data-stu-id="998a2-193">Specify the metadata for the DAC, such as the DAC name, version, and description.</span></span>  
  
4.  <span data-ttu-id="998a2-194">使用上面指定的信息运行 Register 方法。</span><span class="sxs-lookup"><span data-stu-id="998a2-194">Run the Register method with the information specified above.</span></span>  
  
### <a name="example-powershell"></a><span data-ttu-id="998a2-195">示例 (PowerShell)</span><span class="sxs-lookup"><span data-stu-id="998a2-195">Example (PowerShell)</span></span>  
 <span data-ttu-id="998a2-196">下面的示例将名为 MyDB 的数据库注册为 DAC。</span><span class="sxs-lookup"><span data-stu-id="998a2-196">The following example registers a database named MyDB as a DAC.</span></span>  
  
```powershell
## Set a SMO Server object to the default instance on the local computer.  
CD SQLSERVER:\SQL\localhost\DEFAULT  
$srv = Get-Item .  
  
## Specify the database to register as a DAC.  
$dbname = "MyDB"  
  
## Specify the DAC metadata.  
$applicationname = "MyApplication"  
$version = "1.0.0.0"  
$description = "This DAC defines the database used by my application."  
  
## Register the DAC.  
$registerunit = New-Object Microsoft.SqlServer.Management.Dac.DacExtractionUnit($srv, $dbname, $applicationname, $version)  
$registerunit.Description = $description  
$registerunit.Register()  
```  
  
## <a name="see-also"></a><span data-ttu-id="998a2-197">另请参阅</span><span class="sxs-lookup"><span data-stu-id="998a2-197">See Also</span></span>  
 [<span data-ttu-id="998a2-198">数据层应用程序</span><span class="sxs-lookup"><span data-stu-id="998a2-198">Data-tier Applications</span></span>](data-tier-applications.md)  
