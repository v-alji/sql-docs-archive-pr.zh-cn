---
title: 创建 RSExecRole | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- RSExecRole
ms.assetid: 7ac17341-df7e-4401-870e-652caa2859c0
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 0037ef0c4d7a949b5a30bb45356613f6114db130
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689274"
---
# <a name="create-the-rsexecrole"></a><span data-ttu-id="1542a-102">创建 RSExecRole</span><span class="sxs-lookup"><span data-stu-id="1542a-102">Create the RSExecRole</span></span>
  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] <span data-ttu-id="1542a-103">使用称为 `RSExecRole` 的预定义数据库角色向报表服务器数据库授予报表服务器权限。</span><span class="sxs-lookup"><span data-stu-id="1542a-103">uses a predefined database role called `RSExecRole` to grant report server permissions to the report server database.</span></span> <span data-ttu-id="1542a-104">将 `RSExecRole` 自动创建具有 Report Server 数据库的角色。</span><span class="sxs-lookup"><span data-stu-id="1542a-104">The `RSExecRole` role is created automatically with the report server database.</span></span> <span data-ttu-id="1542a-105">通常，始终不应修改该角色或将其他用户分配给该角色。</span><span class="sxs-lookup"><span data-stu-id="1542a-105">As a rule, you should never modify it or assign other users to the role.</span></span> <span data-ttu-id="1542a-106">但是，将 Report Server 数据库移到新的或不同的数据库时 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../../includes/ssde-md.md)] ，必须在 MASTER 和 MSDB 系统数据库中重新创建该角色。</span><span class="sxs-lookup"><span data-stu-id="1542a-106">However, when you move a report server database to a new or different [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../../includes/ssde-md.md)], must re-create the role in the Master and MSDB system databases.</span></span>

 <span data-ttu-id="1542a-107">使用以下说明，您将执行下列步骤：</span><span class="sxs-lookup"><span data-stu-id="1542a-107">Using the following instructions, you will perform the following steps:</span></span>

-   <span data-ttu-id="1542a-108">在 Master 系统数据库中创建和设置 `RSExecRole`。</span><span class="sxs-lookup"><span data-stu-id="1542a-108">Create and provision the `RSExecRole` in the Master system database.</span></span>

-   <span data-ttu-id="1542a-109">在 MSDB 系统数据库中创建和设置 `RSExecRole`。</span><span class="sxs-lookup"><span data-stu-id="1542a-109">Create and provision the `RSExecRole` in the MSDB system database.</span></span>

> [!NOTE]
>  <span data-ttu-id="1542a-110">本主题中的说明针对的是不需要运行脚本或编写 WMI 代码来设置报表服务器数据库的用户。</span><span class="sxs-lookup"><span data-stu-id="1542a-110">The instructions in this topic are intended for users who do not want to run a script or write WMI code to provision the report server database.</span></span> <span data-ttu-id="1542a-111">如果管理大型部署并且要例行移动数据库，则应编写脚本来自动执行这些步骤。</span><span class="sxs-lookup"><span data-stu-id="1542a-111">If you manage a large deployment and will be moving databases routinely, you should write a script to automate these steps.</span></span> <span data-ttu-id="1542a-112">有关详细信息，请参阅 [访问 Reporting Services WMI 提供程序](../tools/access-the-reporting-services-wmi-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="1542a-112">For more information, see [Access the Reporting Services WMI Provider](../tools/access-the-reporting-services-wmi-provider.md).</span></span>

## <a name="before-you-start"></a><span data-ttu-id="1542a-113">开始之前</span><span class="sxs-lookup"><span data-stu-id="1542a-113">Before you start</span></span>

-   <span data-ttu-id="1542a-114">备份加密密钥，以便可以在数据库移动之后对其进行还原。</span><span class="sxs-lookup"><span data-stu-id="1542a-114">Back up the encryption keys so that you can restore them after the database is moved.</span></span> <span data-ttu-id="1542a-115">这是不会直接影响您创建和设置 `RSExecRole` 的能力的步骤，不过您必须有密钥备份才能验证您的工作。</span><span class="sxs-lookup"><span data-stu-id="1542a-115">This is step does not directly affect your ability to create and provision the `RSExecRole`, but you must have a backup of the keys in order to verify your work.</span></span> <span data-ttu-id="1542a-116">有关详细信息，请参阅 [Back Up and Restore Reporting Services Encryption Keys](../install-windows/ssrs-encryption-keys-back-up-and-restore-encryption-keys.md)。</span><span class="sxs-lookup"><span data-stu-id="1542a-116">For more information, see [Back Up and Restore Reporting Services Encryption Keys](../install-windows/ssrs-encryption-keys-back-up-and-restore-encryption-keys.md).</span></span>

-   <span data-ttu-id="1542a-117">验证您是以具有 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例上的 `sysadmin` 权限的用户帐户身份登录的。</span><span class="sxs-lookup"><span data-stu-id="1542a-117">Verify you are logged on as a user account that has `sysadmin` permissions on the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance.</span></span>

-   <span data-ttu-id="1542a-118">验证 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 代理服务已安装在计划使用的 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 实例上并且正在运行。</span><span class="sxs-lookup"><span data-stu-id="1542a-118">Verify [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent service is installed and running on the instance of the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] instance that you plan to use.</span></span>

-   <span data-ttu-id="1542a-119">附加 reportservertempdb 和 reportserver 数据库。</span><span class="sxs-lookup"><span data-stu-id="1542a-119">Attach the reportservertempdb and reportserver databases.</span></span> <span data-ttu-id="1542a-120">不要求您附加这些数据库来创建实际的角色，不过必须要先附加它们才可以测试您的工作。</span><span class="sxs-lookup"><span data-stu-id="1542a-120">You are not required to attach the databases to create the actual role, but they must be attached before you can test your work.</span></span>

 <span data-ttu-id="1542a-121">关于手动创建 `RSExecRole` 的说明是供迁移报表服务器安装的上下文中使用的。</span><span class="sxs-lookup"><span data-stu-id="1542a-121">The instructions for manually creating the `RSExecRole` are intended to be used within the context of migrating a report server installation.</span></span> <span data-ttu-id="1542a-122">备份和移动报表服务器数据库等重要任务均不在本主题中讲述，但是会记录在数据库引擎文档中。</span><span class="sxs-lookup"><span data-stu-id="1542a-122">Important tasks such as backing up and moving the report server database are not addressed in this topic, but are documented in the Database Engine documentation.</span></span>

## <a name="create-rsexecrole-in-master"></a><span data-ttu-id="1542a-123">在 Master 中创建 RSExecRole</span><span class="sxs-lookup"><span data-stu-id="1542a-123">Create RSExecRole in Master</span></span>
 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] <span data-ttu-id="1542a-124">使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 代理服务的扩展存储过程来支持计划操作。</span><span class="sxs-lookup"><span data-stu-id="1542a-124">uses extended stored procedures for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent service to support scheduled operations.</span></span> <span data-ttu-id="1542a-125">下列步骤说明如何向 `RSExecRole` 角色授予这些过程的执行权限。</span><span class="sxs-lookup"><span data-stu-id="1542a-125">The following steps explain how to grant Execute permissions for the procedures to the `RSExecRole` role.</span></span>

#### <a name="to-create-rsexecrole-in-the-master-system-database-using-management-studio"></a><span data-ttu-id="1542a-126">使用 Management Studio 在 Master 系统数据库中创建 RSExecRole</span><span class="sxs-lookup"><span data-stu-id="1542a-126">To create RSExecRole in the Master system database using Management Studio</span></span>

1.  <span data-ttu-id="1542a-127">启动 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 并连接到承载报表服务器数据库的 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="1542a-127">Start [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] and connect to the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] instance that hosts the report server database.</span></span>

2.  <span data-ttu-id="1542a-128">打开 **“数据库”** 。</span><span class="sxs-lookup"><span data-stu-id="1542a-128">Open **Databases**.</span></span>

3.  <span data-ttu-id="1542a-129">打开 **“系统数据库”** 。</span><span class="sxs-lookup"><span data-stu-id="1542a-129">Open **System Databases**.</span></span>

4.  <span data-ttu-id="1542a-130">打开 `Master`。</span><span class="sxs-lookup"><span data-stu-id="1542a-130">Open `Master`.</span></span>

5.  <span data-ttu-id="1542a-131">打开 **“安全性”** 。</span><span class="sxs-lookup"><span data-stu-id="1542a-131">Open **Security**.</span></span>

6.  <span data-ttu-id="1542a-132">打开 **“角色”** 。</span><span class="sxs-lookup"><span data-stu-id="1542a-132">Open **Roles**.</span></span>

7.  <span data-ttu-id="1542a-133">右键单击“数据库角色”，然后选择“新建数据库角色”   。</span><span class="sxs-lookup"><span data-stu-id="1542a-133">Right-click **Database Roles**, and select **New Database Role**.</span></span> <span data-ttu-id="1542a-134">将显示“常规”页。</span><span class="sxs-lookup"><span data-stu-id="1542a-134">The General page appears.</span></span>

8.  <span data-ttu-id="1542a-135">在 "**角色名称**" 中，键入 `RSExecRole` 。</span><span class="sxs-lookup"><span data-stu-id="1542a-135">In **Role name**, type `RSExecRole`.</span></span>

9. <span data-ttu-id="1542a-136">在 "**所有者**" 中，键入**DBO**。</span><span class="sxs-lookup"><span data-stu-id="1542a-136">In **Owner**, type **DBO**.</span></span>

10. <span data-ttu-id="1542a-137">单击 **“安全对象”**。</span><span class="sxs-lookup"><span data-stu-id="1542a-137">Click **Securables**.</span></span>

11. <span data-ttu-id="1542a-138">单击 **“搜索”** 。</span><span class="sxs-lookup"><span data-stu-id="1542a-138">Click **Search**.</span></span> <span data-ttu-id="1542a-139">此时，将显示 **“添加对象”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="1542a-139">The **Add Objects** dialog box appears.</span></span> <span data-ttu-id="1542a-140">**“指定对象”** 选项默认情况下处于选中状态。</span><span class="sxs-lookup"><span data-stu-id="1542a-140">The **Specific Objects** option is selected by default.</span></span>

12. <span data-ttu-id="1542a-141">单击“确定”。 </span><span class="sxs-lookup"><span data-stu-id="1542a-141">Click **OK**.</span></span> <span data-ttu-id="1542a-142">此时，将显示 **“选择对象”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="1542a-142">The **Select Objects** dialog box appears.</span></span>

13. <span data-ttu-id="1542a-143">单击 **“对象类型”** 。</span><span class="sxs-lookup"><span data-stu-id="1542a-143">Click **Object Types**.</span></span>

14. <span data-ttu-id="1542a-144">单击 **“扩展存储过程”** 。</span><span class="sxs-lookup"><span data-stu-id="1542a-144">Click **Extended Stored Procedures**.</span></span>

15. <span data-ttu-id="1542a-145">单击“确定”。 </span><span class="sxs-lookup"><span data-stu-id="1542a-145">Click **OK**.</span></span>

16. <span data-ttu-id="1542a-146">单击“浏览”  。</span><span class="sxs-lookup"><span data-stu-id="1542a-146">Click **Browse**.</span></span>

17. <span data-ttu-id="1542a-147">向下滚动扩展存储过程列表，然后选择下列各项：</span><span class="sxs-lookup"><span data-stu-id="1542a-147">Scroll down the list of extended stored procedures and select the following:</span></span>

    1.  <span data-ttu-id="1542a-148">xp_sqlagent_enum_jobs</span><span class="sxs-lookup"><span data-stu-id="1542a-148">xp_sqlagent_enum_jobs</span></span>

    2.  <span data-ttu-id="1542a-149">xp_sqlagent_is_starting</span><span class="sxs-lookup"><span data-stu-id="1542a-149">xp_sqlagent_is_starting</span></span>

    3.  <span data-ttu-id="1542a-150">xp_sqlagent_notify</span><span class="sxs-lookup"><span data-stu-id="1542a-150">xp_sqlagent_notify</span></span>

18. <span data-ttu-id="1542a-151">单击 **“确定”** ，然后再次单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="1542a-151">Click **OK**, and the click **OK** again.</span></span>

19. <span data-ttu-id="1542a-152">在 **“执行”** 一行的 **“授予”** 列中，单击复选框，然后单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="1542a-152">In the **Execute** row, in the **Grant** column, click the check box, and then click **OK**.</span></span>

20. <span data-ttu-id="1542a-153">对于其余的每个存储过程，重复此操作。</span><span class="sxs-lookup"><span data-stu-id="1542a-153">Repeat for each of the remaining stored procedures.</span></span> <span data-ttu-id="1542a-154">必须向 `RSExecRole` 授予全部三个存储过程的执行权限。</span><span class="sxs-lookup"><span data-stu-id="1542a-154">`RSExecRole` must be granted Execute permissions for all three stored procedures.</span></span>

 <span data-ttu-id="1542a-155">![数据库角色属性页](../media/rsexecroledbproperties.gif "数据库角色属性页")</span><span class="sxs-lookup"><span data-stu-id="1542a-155">![Database Role Properties page](../media/rsexecroledbproperties.gif "Database Role Properties page")</span></span>

## <a name="create-rsexecrole-in-msdb"></a><span data-ttu-id="1542a-156">在 MSDB 中创建 RSExecRole</span><span class="sxs-lookup"><span data-stu-id="1542a-156">Create RSExecRole in MSDB</span></span>
 <span data-ttu-id="1542a-157">Reporting Services 使用 SQL Server 代理服务的存储过程并从系统表中检索作业信息，以支持计划操作。</span><span class="sxs-lookup"><span data-stu-id="1542a-157">Reporting Services uses stored procedures for SQL Server Agent service and retrieves job information from system tables to support scheduled operations.</span></span> <span data-ttu-id="1542a-158">下列步骤说明如何向 RSExecRole 授予这些过程的执行权限和对表的选择权限。</span><span class="sxs-lookup"><span data-stu-id="1542a-158">The following steps explain how to grant Execute permissions for the procedures and Select permissions on the tables to the RSExecRole.</span></span>

#### <a name="to-create-rsexecrole-in-the-msdb-system-database"></a><span data-ttu-id="1542a-159">在 MSDB 系统数据库中创建 RSExecRole</span><span class="sxs-lookup"><span data-stu-id="1542a-159">To create RSExecRole in the MSDB system database</span></span>

1.  <span data-ttu-id="1542a-160">重复相似的步骤，授予 MSDB 中存储过程和表的权限。</span><span class="sxs-lookup"><span data-stu-id="1542a-160">Repeat similar steps for granting permissions to stored procedures and tables in MSDB.</span></span> <span data-ttu-id="1542a-161">若要简化这些步骤，需要单独设置存储过程和表。</span><span class="sxs-lookup"><span data-stu-id="1542a-161">To simplify the steps, you will provision the stored procedures and tables separately.</span></span>

2.  <span data-ttu-id="1542a-162">打开 `MSDB`。</span><span class="sxs-lookup"><span data-stu-id="1542a-162">Open `MSDB`.</span></span>

3.  <span data-ttu-id="1542a-163">打开 **“安全性”**。</span><span class="sxs-lookup"><span data-stu-id="1542a-163">Open **Security**.</span></span>

4.  <span data-ttu-id="1542a-164">打开 **“角色”**。</span><span class="sxs-lookup"><span data-stu-id="1542a-164">Open **Roles**.</span></span>

5.  <span data-ttu-id="1542a-165">右键单击“数据库角色”，然后选择“新建数据库角色”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1542a-165">Right-click **Database Roles**, and select **New Database Role**.</span></span> <span data-ttu-id="1542a-166">将显示“常规”页。</span><span class="sxs-lookup"><span data-stu-id="1542a-166">The General page appears.</span></span>

6.  <span data-ttu-id="1542a-167">在 "角色名称" 中，键入 `RSExecRole` 。</span><span class="sxs-lookup"><span data-stu-id="1542a-167">In Role name, type `RSExecRole`.</span></span>

7.  <span data-ttu-id="1542a-168">在 "所有者" 中，键入**DBO**。</span><span class="sxs-lookup"><span data-stu-id="1542a-168">In Owner, type **DBO**.</span></span>

8.  <span data-ttu-id="1542a-169">单击 **“安全对象”**。</span><span class="sxs-lookup"><span data-stu-id="1542a-169">Click **Securables**.</span></span>

9. <span data-ttu-id="1542a-170">单击“添加”。</span><span class="sxs-lookup"><span data-stu-id="1542a-170">Click **Add**.</span></span> <span data-ttu-id="1542a-171">此时，将显示 **“添加对象”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="1542a-171">The **Add Objects** dialog box appears.</span></span> <span data-ttu-id="1542a-172">**“指定对象”** 选项默认情况下处于选中状态。</span><span class="sxs-lookup"><span data-stu-id="1542a-172">The **Specify Objects** option is selected by default.</span></span>

10. <span data-ttu-id="1542a-173">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="1542a-173">Click **OK**.</span></span>

11. <span data-ttu-id="1542a-174">单击 **“对象类型”**。</span><span class="sxs-lookup"><span data-stu-id="1542a-174">Click **Object Types**.</span></span>

12. <span data-ttu-id="1542a-175">单击 **“存储过程”**。</span><span class="sxs-lookup"><span data-stu-id="1542a-175">Click **Stored Procedures.**</span></span>

13. <span data-ttu-id="1542a-176">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="1542a-176">Click **OK**.</span></span>

14. <span data-ttu-id="1542a-177">单击“浏览” 。</span><span class="sxs-lookup"><span data-stu-id="1542a-177">Click **Browse**.</span></span>

15. <span data-ttu-id="1542a-178">向下滚动项目列表，然后选择下列各项：</span><span class="sxs-lookup"><span data-stu-id="1542a-178">Scroll down the list of items and select the following:</span></span>

    1.  <span data-ttu-id="1542a-179">sp_add_category</span><span class="sxs-lookup"><span data-stu-id="1542a-179">sp_add_category</span></span>

    2.  <span data-ttu-id="1542a-180">sp_add_job</span><span class="sxs-lookup"><span data-stu-id="1542a-180">sp_add_job</span></span>

    3.  <span data-ttu-id="1542a-181">sp_add_jobschedule</span><span class="sxs-lookup"><span data-stu-id="1542a-181">sp_add_jobschedule</span></span>

    4.  <span data-ttu-id="1542a-182">sp_add_jobserver</span><span class="sxs-lookup"><span data-stu-id="1542a-182">sp_add_jobserver</span></span>

    5.  <span data-ttu-id="1542a-183">sp_add_jobstep</span><span class="sxs-lookup"><span data-stu-id="1542a-183">sp_add_jobstep</span></span>

    6.  <span data-ttu-id="1542a-184">sp_delete_job</span><span class="sxs-lookup"><span data-stu-id="1542a-184">sp_delete_job</span></span>

    7.  <span data-ttu-id="1542a-185">sp_help_category</span><span class="sxs-lookup"><span data-stu-id="1542a-185">sp_help_category</span></span>

    8.  <span data-ttu-id="1542a-186">sp_help_job</span><span class="sxs-lookup"><span data-stu-id="1542a-186">sp_help_job</span></span>

    9. <span data-ttu-id="1542a-187">sp_help_jobschedule</span><span class="sxs-lookup"><span data-stu-id="1542a-187">sp_help_jobschedule</span></span>

    10. <span data-ttu-id="1542a-188">sp_verify_job_identifiers</span><span class="sxs-lookup"><span data-stu-id="1542a-188">sp_verify_job_identifiers</span></span>

16. <span data-ttu-id="1542a-189">单击 **“确定”**，然后再次单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="1542a-189">Click **OK**, and the click **OK** again.</span></span>

17. <span data-ttu-id="1542a-190">选择第一个存储过程：sp_add_category。</span><span class="sxs-lookup"><span data-stu-id="1542a-190">Select the first stored procedure: sp_add_category.</span></span>

18. <span data-ttu-id="1542a-191">在 **“执行”** 一行的 **“授予”** 列中，单击复选框，然后单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="1542a-191">In the **Execute** row, in the **Grant** column, click the checkbox, and then click **OK**.</span></span>

19. <span data-ttu-id="1542a-192">对于其余的每个存储过程，重复此操作。</span><span class="sxs-lookup"><span data-stu-id="1542a-192">Repeat for each of the remaining stored procedures.</span></span> <span data-ttu-id="1542a-193">必须向 RSExecRole 授予全部十个存储过程的执行权限。</span><span class="sxs-lookup"><span data-stu-id="1542a-193">RSExecRole must be granted Execute permissions for all ten stored procedures.</span></span>

20. <span data-ttu-id="1542a-194">在“安全对象”选项卡上，再次单击 **“添加”** 。</span><span class="sxs-lookup"><span data-stu-id="1542a-194">On the Securables tab, and click **Add** again.</span></span> <span data-ttu-id="1542a-195">此时，将显示 **“添加对象”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="1542a-195">The **Add Objects** dialog box appears.</span></span> <span data-ttu-id="1542a-196">**“指定对象”** 选项默认情况下处于选中状态。</span><span class="sxs-lookup"><span data-stu-id="1542a-196">The **Specify Objects** option is selected by default.</span></span>

21. <span data-ttu-id="1542a-197">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="1542a-197">Click **OK**.</span></span>

22. <span data-ttu-id="1542a-198">单击 **“对象类型”**。</span><span class="sxs-lookup"><span data-stu-id="1542a-198">Click **Object Types**.</span></span>

23. <span data-ttu-id="1542a-199">单击 **“表”**。</span><span class="sxs-lookup"><span data-stu-id="1542a-199">Click **Tables.**</span></span>

24. <span data-ttu-id="1542a-200">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="1542a-200">Click **OK**.</span></span>

25. <span data-ttu-id="1542a-201">单击“浏览” 。</span><span class="sxs-lookup"><span data-stu-id="1542a-201">Click **Browse**.</span></span>

26. <span data-ttu-id="1542a-202">向下滚动项目列表，然后选择下列各项：</span><span class="sxs-lookup"><span data-stu-id="1542a-202">Scroll down the list of items and select the following:</span></span>

    1.  <span data-ttu-id="1542a-203">syscategories</span><span class="sxs-lookup"><span data-stu-id="1542a-203">syscategories</span></span>

    2.  <span data-ttu-id="1542a-204">sysjobs</span><span class="sxs-lookup"><span data-stu-id="1542a-204">sysjobs</span></span>

27. <span data-ttu-id="1542a-205">单击 **“确定”**，然后再次单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="1542a-205">Click **OK**, and the click **OK** again.</span></span>

28. <span data-ttu-id="1542a-206">选择第一个表：syscategories。</span><span class="sxs-lookup"><span data-stu-id="1542a-206">Select the first table: syscategories.</span></span>

29. <span data-ttu-id="1542a-207">在 **“选择”** 一行的 **“授予”** 列中，单击复选框，然后单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="1542a-207">In the **Select** row, in the **Grant** column, click the checkbox, and then click **OK**.</span></span>

30. <span data-ttu-id="1542a-208">对于 sysjobs 表重复此操作。</span><span class="sxs-lookup"><span data-stu-id="1542a-208">Repeat for the sysjobs table.</span></span> <span data-ttu-id="1542a-209">必须向 RSExecRole 授予这两个表的选择权限。</span><span class="sxs-lookup"><span data-stu-id="1542a-209">RSExecRole must be granted Select permissions for both tables.</span></span>

## <a name="move-the-report-server-database"></a><span data-ttu-id="1542a-210">移动报表服务器数据库</span><span class="sxs-lookup"><span data-stu-id="1542a-210">Move the Report Server Database</span></span>
 <span data-ttu-id="1542a-211">创建角色之后，可以将报表服务器数据库移到新的 SQL Server 实例。</span><span class="sxs-lookup"><span data-stu-id="1542a-211">After you create the roles, you can move the report server database to new SQL Server instance.</span></span> <span data-ttu-id="1542a-212">有关详细信息，请参阅 [将报表服务器数据库移至其他计算机（SSRS 本机模式）](../report-server/moving-the-report-server-databases-to-another-computer-ssrs-native-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="1542a-212">For more information, see [Moving the Report Server Databases to Another Computer &#40;SSRS Native Mode&#41;](../report-server/moving-the-report-server-databases-to-another-computer-ssrs-native-mode.md).</span></span>

 <span data-ttu-id="1542a-213">如果要将 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 升级到 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]，则可以在数据库移动之前或之后进行升级。</span><span class="sxs-lookup"><span data-stu-id="1542a-213">If you are upgrading the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] to [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], you can upgrade it before or after moving the database.</span></span>

 <span data-ttu-id="1542a-214">当报表服务器连接到报表服务器数据库时，该数据库将自动升级到 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="1542a-214">The report server database will be upgraded to the [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] automatically when the report server connects to it.</span></span> <span data-ttu-id="1542a-215">数据库升级不要求任何特定的步骤。</span><span class="sxs-lookup"><span data-stu-id="1542a-215">There are no specific steps required for upgrading the database.</span></span>

## <a name="restore-encryption-keys-and-verify-your-work"></a><span data-ttu-id="1542a-216">还原加密密钥和验证您的工作</span><span class="sxs-lookup"><span data-stu-id="1542a-216">Restore Encryption Keys and Verify Your Work</span></span>
 <span data-ttu-id="1542a-217">如果已附加报表服务器数据库，则现在应可以完成以下步骤来验证您的工作。</span><span class="sxs-lookup"><span data-stu-id="1542a-217">If you have attached the report server databases, you should now be able to complete the following steps to verify your work.</span></span>

#### <a name="to-verify-report-server-operability-after-a-database-move"></a><span data-ttu-id="1542a-218">数据库移动后验证报表服务器的可操作性</span><span class="sxs-lookup"><span data-stu-id="1542a-218">To verify report server operability after a database move</span></span>

1.  <span data-ttu-id="1542a-219">启动 Reporting Services 配置工具，然后连接到报表服务器。</span><span class="sxs-lookup"><span data-stu-id="1542a-219">Start the Reporting Services Configuration tool and connect to the report server.</span></span>

2.  <span data-ttu-id="1542a-220">单击 **“数据库”**。</span><span class="sxs-lookup"><span data-stu-id="1542a-220">Click **Database**.</span></span>

3.  <span data-ttu-id="1542a-221">单击 **“更改数据库”**。</span><span class="sxs-lookup"><span data-stu-id="1542a-221">Click **Change Database**.</span></span>

4.  <span data-ttu-id="1542a-222">单击 **“选择现有报表服务器数据库”**。</span><span class="sxs-lookup"><span data-stu-id="1542a-222">Click **Choose an existing report server database**.</span></span>

5.  <span data-ttu-id="1542a-223">输入数据库引擎的服务器名称。</span><span class="sxs-lookup"><span data-stu-id="1542a-223">Enter the server name of the Database Engine.</span></span> <span data-ttu-id="1542a-224">如果将 Report Server 数据库附加到命名实例，则必须按以下格式键入实例名称： \<servername> \\<instancename \> 。</span><span class="sxs-lookup"><span data-stu-id="1542a-224">If you attached the report server databases to a named instance, you must type the instance name in this format: \<servername>\\<instancename\>.</span></span>

6.  <span data-ttu-id="1542a-225">单击 **“测试连接”** 。</span><span class="sxs-lookup"><span data-stu-id="1542a-225">Click **Test Connection**.</span></span>

7.  <span data-ttu-id="1542a-226">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="1542a-226">Click **Next**.</span></span>

8.  <span data-ttu-id="1542a-227">在“数据库”上，选择报表服务器数据库。</span><span class="sxs-lookup"><span data-stu-id="1542a-227">On the Database, select the report server database.</span></span>

9. <span data-ttu-id="1542a-228">单击“下一步”  并完成向导。</span><span class="sxs-lookup"><span data-stu-id="1542a-228">Click **Next** and complete the wizard.</span></span>

10. <span data-ttu-id="1542a-229">单击 **“加密密钥”**。</span><span class="sxs-lookup"><span data-stu-id="1542a-229">Click **Encryption Keys**.</span></span>

11. <span data-ttu-id="1542a-230">单击 "**还原**"。</span><span class="sxs-lookup"><span data-stu-id="1542a-230">Click **Restore**.</span></span>

12. <span data-ttu-id="1542a-231">选择强文件 (.snk)，该文件拥有用来对报表服务器数据库中存储的凭据和连接信息进行解密的对称密钥的备份副本。</span><span class="sxs-lookup"><span data-stu-id="1542a-231">Select the strong file (.snk) that has the backup copy of the symmetric key used to decrypt stored credentials and connection information in the report server database.</span></span>

13. <span data-ttu-id="1542a-232">输入密码，然后单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="1542a-232">Enter the password and click **OK**.</span></span>

14. <span data-ttu-id="1542a-233">单击 **“报表管理器 URL”**。</span><span class="sxs-lookup"><span data-stu-id="1542a-233">Click **Report Manager URL**.</span></span>

15. <span data-ttu-id="1542a-234">单击链接打开报表管理器。</span><span class="sxs-lookup"><span data-stu-id="1542a-234">Click the link to open Report Manager.</span></span> <span data-ttu-id="1542a-235">您应看到报表服务器数据库中的报表服务器项。</span><span class="sxs-lookup"><span data-stu-id="1542a-235">You should see the report server items from the report server database.</span></span>

## <a name="see-also"></a><span data-ttu-id="1542a-236">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1542a-236">See Also</span></span>
 <span data-ttu-id="1542a-237">[将报表服务器数据库移动到另一台计算机 &#40;Ssrs 本机模式&#41;](../report-server/moving-the-report-server-databases-to-another-computer-ssrs-native-mode.md) [Reporting Services 配置管理器 &#40;纯模式&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md) [创建本机模式报表服务器数据库 &#40;SSRS Configuration Manager](../install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md)&#41;[备份和还原 Reporting Services 加密密钥](../install-windows/ssrs-encryption-keys-back-up-and-restore-encryption-keys.md)</span><span class="sxs-lookup"><span data-stu-id="1542a-237">[Moving the Report Server Databases to Another Computer &#40;SSRS Native Mode&#41;](../report-server/moving-the-report-server-databases-to-another-computer-ssrs-native-mode.md) [Reporting Services Configuration Manager &#40;Native Mode&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md) [Create a Native Mode Report Server Database  &#40;SSRS Configuration Manager&#41;](../install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md) [Back Up and Restore Reporting Services Encryption Keys](../install-windows/ssrs-encryption-keys-back-up-and-restore-encryption-keys.md)</span></span>


