---
title: 配置管理数据仓库 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.dc.datacollection.wizard_finish.f1
- sql12.swb.dc.datacollection.wizard_maploginuser.f1
- sql12.swb.dc.datacollection.wizard_welcome.f1
- sql12.swb.dc.datacollection.wizard_choosemdw.f1
- sql12.swb.dc.datacollection.wizard_completecfg.f1
- sql12.swb.dc.datacollection.wizard_config.f1
- sql12.swb.dc.datacollection.wizard_createmdw.f1
helpviewer_keywords:
- data warehouse [SQL Server], multiple instances
- data warehouse [SQL Server], configuring
- Configure Management Data Warehouse Wizard
- management data warehouse, configuring
ms.assetid: 23a584f3-c5e1-414c-9afe-73cd7efbda4b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1ef4ddd518343a3076c72ecc41f9b15ddf092dc0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591909"
---
# <a name="configure-the-management-data-warehouse-sql-server-management-studio"></a><span data-ttu-id="9d9e4-102">配置管理数据仓库 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="9d9e4-102">Configure the Management Data Warehouse (SQL Server Management Studio)</span></span>
  <span data-ttu-id="9d9e4-103">本主题介绍如何配置管理数据仓库以支持使用数据收集器的单个或多个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例的数据存储。</span><span class="sxs-lookup"><span data-stu-id="9d9e4-103">This topic describes how to configure the management data warehouse to support data storage on a single instance or multiple instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that are using the data collector.</span></span> <span data-ttu-id="9d9e4-104">这些实例可能位于相同或不同的服务器上。</span><span class="sxs-lookup"><span data-stu-id="9d9e4-104">These instances can be on the same server or on different servers.</span></span> <span data-ttu-id="9d9e4-105">本主题还提供针对 [配置管理数据仓库向导](#Wizard) 对话框的用户界面的说明。</span><span class="sxs-lookup"><span data-stu-id="9d9e4-105">This topic also provides descriptions of the user interface for the [Configure Data Management Warehouse Wizard](#Wizard) dialog box.</span></span> <span data-ttu-id="9d9e4-106">有关配置数据收集器的信息，请参阅 [Configure Properties of a Data Collector](configure-properties-of-a-data-collector.md)。</span><span class="sxs-lookup"><span data-stu-id="9d9e4-106">For information about configuring a data collector, see [Configure Properties of a Data Collector](configure-properties-of-a-data-collector.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9d9e4-107">如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理配置为使用其中一个系统服务帐户（Local System、Network Service 或 Local Service）运行，且创建管理数据仓库的实例与数据收集器的实例不同，则必须将收集组配置为使用代理将数据上载到管理数据仓库。</span><span class="sxs-lookup"><span data-stu-id="9d9e4-107">If [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent is configured to run using one of the System service accounts (Local System, Network Service, or Local Service), and the management data warehouse is created on a different instance from the data collector, you must configure collection sets to use a proxy for uploading data to the management data warehouse.</span></span>  
  
### <a name="configure-the-management-data-warehouse-on-a-single-instance-or-multiple-instances-of-ssnoversion"></a><span data-ttu-id="9d9e4-108">配置 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d9e4-108">Configure the management data warehouse on a single instance or multiple instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span></span>  
  
1.  <span data-ttu-id="9d9e4-109">请确保 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理正在运行。</span><span class="sxs-lookup"><span data-stu-id="9d9e4-109">Ensure that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent is running.</span></span>  
  
2.  <span data-ttu-id="9d9e4-110">在对象资源管理器中，展开 **“管理”** 节点。</span><span class="sxs-lookup"><span data-stu-id="9d9e4-110">In Object Explorer, expand the **Management** node.</span></span>  
  
3.  <span data-ttu-id="9d9e4-111">右键单击“数据收集”，展开“任务”，然后单击“配置管理数据仓库”。</span><span class="sxs-lookup"><span data-stu-id="9d9e4-111">Right-click **Data Collection**, expand **Tasks**, and then click **Configure Management Data Warehouse**.</span></span>  
  
4.  <span data-ttu-id="9d9e4-112">使用 [配置管理数据仓库向导](#Wizard) 创建一个管理数据仓库，配置登录名，启用数据收集，然后启动 **“系统数据收集组”** 。</span><span class="sxs-lookup"><span data-stu-id="9d9e4-112">Use the [Configure Management Data Warehouse Wizard](#Wizard) to create a management data warehouse, configure logins, enable data collection, and start the **System Data Collection Sets**.</span></span>  
  
     <span data-ttu-id="9d9e4-113">若要配置多个实例，请继续执行步骤 5。</span><span class="sxs-lookup"><span data-stu-id="9d9e4-113">To configure multiple instances, continue with step 5.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="9d9e4-114">在数据收集器安装在使用同一管理数据仓库的多个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例上的部署中，使用代理是最佳做法。</span><span class="sxs-lookup"><span data-stu-id="9d9e4-114">It is considered best practice to use proxies in deployments where the data collector is installed on multiple instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that are using the same management data warehouse.</span></span>  
  
5.  <span data-ttu-id="9d9e4-115">在另一个实例上打开 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，然后执行以下任意一项操作：</span><span class="sxs-lookup"><span data-stu-id="9d9e4-115">Open [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] on another instance and do either of the following:</span></span>  
  
    -   <span data-ttu-id="9d9e4-116">使用配置管理数据仓库向导为现有的管理数据仓库配置数据收集。</span><span class="sxs-lookup"><span data-stu-id="9d9e4-116">Use the Configure Management Data Warehouse wizard to configure data collection for the existing management data warehouse.</span></span>  
  
    -   <span data-ttu-id="9d9e4-117">右键单击“数据收集”，然后单击“属性”。</span><span class="sxs-lookup"><span data-stu-id="9d9e4-117">Right-click **Data Collection**, and then click **Properties**.</span></span> <span data-ttu-id="9d9e4-118">在 **“常规”** 选项卡上，指定现有的管理数据仓库以及安装该管理数据仓库的服务器。</span><span class="sxs-lookup"><span data-stu-id="9d9e4-118">On the **General** tab, specify the existing management data warehouse and the server that it is installed on.</span></span>  
  
6.  <span data-ttu-id="9d9e4-119">重复步骤 5 直至将使用该数据收集的所有数据库实例均配置为将数据上载到共享的管理数据仓库。</span><span class="sxs-lookup"><span data-stu-id="9d9e4-119">Repeat step 5 until all the database instances that use the data collector are configured to upload data to the shared management data warehouse.</span></span>  
  
####  <a name="configure-management-data-warehouse-wizard"></a><a name="Wizard"></a> <span data-ttu-id="9d9e4-120">配置管理数据仓库向导</span><span class="sxs-lookup"><span data-stu-id="9d9e4-120">Configure Management Data Warehouse Wizard</span></span>  
 <span data-ttu-id="9d9e4-121">**“欢迎”页**</span><span class="sxs-lookup"><span data-stu-id="9d9e4-121">**Welcome Page**</span></span>  
  
 <span data-ttu-id="9d9e4-122">欢迎页是配置数据收集向导的起始页。</span><span class="sxs-lookup"><span data-stu-id="9d9e4-122">The Welcome page is the starting page of the Configure Data Collection Wizard.</span></span> <span data-ttu-id="9d9e4-123">是否显示此页是可选的。</span><span class="sxs-lookup"><span data-stu-id="9d9e4-123">Displaying this page is optional.</span></span>  
  
 <span data-ttu-id="9d9e4-124">**不再显示此起始页。**</span><span class="sxs-lookup"><span data-stu-id="9d9e4-124">**Do not show this starting page again.**</span></span>  
 <span data-ttu-id="9d9e4-125">选择此选项可在下一次启动配置数据收集向导时不显示该页。</span><span class="sxs-lookup"><span data-stu-id="9d9e4-125">Select to suppress this page the next time you launch the Configure Data Collection Wizard.</span></span>  
  
 <span data-ttu-id="9d9e4-126">**“配置管理数据仓库存储”页**</span><span class="sxs-lookup"><span data-stu-id="9d9e4-126">**Configure Management Data Warehouse Storage Page**</span></span>  
  
 <span data-ttu-id="9d9e4-127">使用此页可选择 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库服务器和管理数据仓库。</span><span class="sxs-lookup"><span data-stu-id="9d9e4-127">Use this page to select a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database server and management data warehouse.</span></span> <span data-ttu-id="9d9e4-128">管理数据仓库是将存储收集的数据的关系数据库。</span><span class="sxs-lookup"><span data-stu-id="9d9e4-128">The management data warehouse is a relational database that will store collected data.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9d9e4-129">您必须拥有相应级别的权限才能在服务器上创建管理数据仓库。</span><span class="sxs-lookup"><span data-stu-id="9d9e4-129">You must have the appropriate level of permissions in order to create the management data warehouse on the server.</span></span> <span data-ttu-id="9d9e4-130">有关详细信息，请参阅 [CREATE DATABASE (SQL Server Transact-SQL)](/sql/t-sql/statements/create-database-sql-server-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="9d9e4-130">For more information, see [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql).</span></span> <span data-ttu-id="9d9e4-131">您还必须拥有为管理数据仓库角色创建登录名的相应级别权限。</span><span class="sxs-lookup"><span data-stu-id="9d9e4-131">You also must have the appropriate level of permissions to create logins for management data warehouse roles.</span></span>  
  
 <span data-ttu-id="9d9e4-132">**服务器名称**</span><span class="sxs-lookup"><span data-stu-id="9d9e4-132">**Server name**</span></span>  
 <span data-ttu-id="9d9e4-133">指定将承载管理数据仓库的服务器的名称。</span><span class="sxs-lookup"><span data-stu-id="9d9e4-133">Specifies the name of the server that will host the management data warehouse.</span></span>  
  
 <span data-ttu-id="9d9e4-134">配置管理数据仓库时， **“服务器名称”** 始终为本地服务器的名称且不能修改。</span><span class="sxs-lookup"><span data-stu-id="9d9e4-134">When configuring a management data warehouse, **Server name** is always the name of the local server and cannot be modified.</span></span>  
  
 <span data-ttu-id="9d9e4-135">**数据库名称**</span><span class="sxs-lookup"><span data-stu-id="9d9e4-135">**Database name**</span></span>  
 <span data-ttu-id="9d9e4-136">指定将存储收集的数据的关系数据库。</span><span class="sxs-lookup"><span data-stu-id="9d9e4-136">Specifies the relational database that will store collected data.</span></span> <span data-ttu-id="9d9e4-137">从列表中选择现有数据库，或单击 **“新建”** 通过 **“新建数据库”** 对话框创建新的数据库。</span><span class="sxs-lookup"><span data-stu-id="9d9e4-137">Use the list to select an existing database or click **New** to create a new database using the **New Database** dialog.</span></span>  
  
 <span data-ttu-id="9d9e4-138">只有在配置数据收集组时， **“新建”** 选项才可用。</span><span class="sxs-lookup"><span data-stu-id="9d9e4-138">The **New** option is available only when configuring a data collection set</span></span>  
  
 <span data-ttu-id="9d9e4-139">**“映射登录名和用户”页**</span><span class="sxs-lookup"><span data-stu-id="9d9e4-139">**Map Logins and Users Page**</span></span>  
  
 <span data-ttu-id="9d9e4-140">使用此页可以将登录名映射到管理数据仓库的数据库用户角色。</span><span class="sxs-lookup"><span data-stu-id="9d9e4-140">Use this page to map logins to database user roles for the management data warehouse.</span></span>  
  
 <span data-ttu-id="9d9e4-141">**映射到此登录名的用户**</span><span class="sxs-lookup"><span data-stu-id="9d9e4-141">**Users mapped to this login**</span></span>  
 <span data-ttu-id="9d9e4-142">显示将承载管理数据仓库的服务器中的现有登录名。</span><span class="sxs-lookup"><span data-stu-id="9d9e4-142">Displays the existing logins on the server that will host the management data warehouse.</span></span> <span data-ttu-id="9d9e4-143">每一行包含一个可编辑的 **“映射”** 复选框、一个 **“登录”** 名和一个登录名的 **“类型”** 。</span><span class="sxs-lookup"><span data-stu-id="9d9e4-143">Each row contains an editable **Map** check box, a **Login** name, and a **Type** of login.</span></span>  
  
 <span data-ttu-id="9d9e4-144">可通过为某个登录名选中 **“映射”** 复选框来指定该登录名。</span><span class="sxs-lookup"><span data-stu-id="9d9e4-144">Specify a login by selecting the **Map** checkbox for the login.</span></span>  
  
 <span data-ttu-id="9d9e4-145">\<data warehouse name> 的数据库角色成员身份</span><span class="sxs-lookup"><span data-stu-id="9d9e4-145">**Database role membership for:**  *\<data warehouse name>*</span></span>  
 <span data-ttu-id="9d9e4-146">通过单击以下一个或多个选项旁边的复选框，选择登录名映射到的管理数据仓库角色：</span><span class="sxs-lookup"><span data-stu-id="9d9e4-146">Select the management data warehouse role that the login is mapped to by clicking the checkbox by one or more of the following options:</span></span>  
  
-   <span data-ttu-id="9d9e4-147">**mdw_admin**</span><span class="sxs-lookup"><span data-stu-id="9d9e4-147">**mdw_admin**</span></span>  
  
-   <span data-ttu-id="9d9e4-148">**mdw_reader**</span><span class="sxs-lookup"><span data-stu-id="9d9e4-148">**mdw_reader**</span></span>  
  
-   <span data-ttu-id="9d9e4-149">**mdw_writer**</span><span class="sxs-lookup"><span data-stu-id="9d9e4-149">**mdw_writer**</span></span>  
  
 <span data-ttu-id="9d9e4-150">**新建登录名**</span><span class="sxs-lookup"><span data-stu-id="9d9e4-150">**New Login**</span></span>  
 <span data-ttu-id="9d9e4-151">打开“登录名 - 新建”对话框并为管理数据仓库创建新的登录名。</span><span class="sxs-lookup"><span data-stu-id="9d9e4-151">Open the **Login - New** dialog box and create a new login for the management data warehouse.</span></span>  
  
 <span data-ttu-id="9d9e4-152">**“完成向导”页**</span><span class="sxs-lookup"><span data-stu-id="9d9e4-152">**Complete the Wizard Page**</span></span>  
  
 <span data-ttu-id="9d9e4-153">使用此页可验证和完成数据收集配置。</span><span class="sxs-lookup"><span data-stu-id="9d9e4-153">Use this page to verify and complete data collection configuration.</span></span> <span data-ttu-id="9d9e4-154">显示在查看窗口中的树用于说明将应用的配置以及单击 **“完成”** 时将执行的操作。</span><span class="sxs-lookup"><span data-stu-id="9d9e4-154">The tree displayed in the viewing window shows what configurations will applied as well as what actions will take place when you click **Finish**.</span></span>  
  
 <span data-ttu-id="9d9e4-155">**“配置数据收集向导进度”页**</span><span class="sxs-lookup"><span data-stu-id="9d9e4-155">**Configure Data Collection Wizard Progress Page**</span></span>  
  
 <span data-ttu-id="9d9e4-156">使用此页可查看每个配置步骤的结果。</span><span class="sxs-lookup"><span data-stu-id="9d9e4-156">Use this page to view the results of each configuration step.</span></span>  
  
 <span data-ttu-id="9d9e4-157">**详细信息**</span><span class="sxs-lookup"><span data-stu-id="9d9e4-157">**Details**</span></span>  
 <span data-ttu-id="9d9e4-158">每个配置步骤在“详细信息”网格中显示为一行。</span><span class="sxs-lookup"><span data-stu-id="9d9e4-158">Displays each configuration step as a row in the **Details** grid.</span></span> <span data-ttu-id="9d9e4-159">每一行均包含描述相应步骤的 **“操作”** 列和指示该步骤成功或失败的 **“状态”** 列。</span><span class="sxs-lookup"><span data-stu-id="9d9e4-159">Each row contains an **Action** column that describes the step, and a **Status** column that indicates the success or failure of the step.</span></span> <span data-ttu-id="9d9e4-160">如果有错误，则在 **“消息”** 列中会显示消息。</span><span class="sxs-lookup"><span data-stu-id="9d9e4-160">If there is an error, a message appears in the **Message** column.</span></span>  
  
 <span data-ttu-id="9d9e4-161">**Stop**</span><span class="sxs-lookup"><span data-stu-id="9d9e4-161">**Stop**</span></span>  
 <span data-ttu-id="9d9e4-162">停止向导的处理。</span><span class="sxs-lookup"><span data-stu-id="9d9e4-162">Stop wizard processing.</span></span>  
  
 <span data-ttu-id="9d9e4-163">**Report**</span><span class="sxs-lookup"><span data-stu-id="9d9e4-163">**Report**</span></span>  
 <span data-ttu-id="9d9e4-164">查看数据收集配置的报告。</span><span class="sxs-lookup"><span data-stu-id="9d9e4-164">View a report of the data collection configuration.</span></span> <span data-ttu-id="9d9e4-165">提供了以下报告选项：</span><span class="sxs-lookup"><span data-stu-id="9d9e4-165">The following report options are provided:</span></span>  
  
-   <span data-ttu-id="9d9e4-166">查看报告</span><span class="sxs-lookup"><span data-stu-id="9d9e4-166">View Report</span></span>  
  
-   <span data-ttu-id="9d9e4-167">将报告保存到文件</span><span class="sxs-lookup"><span data-stu-id="9d9e4-167">Save Report to File</span></span>  
  
-   <span data-ttu-id="9d9e4-168">“将报告复制到剪贴板”</span><span class="sxs-lookup"><span data-stu-id="9d9e4-168">Copy Report to Clipboard</span></span>  
  
-   <span data-ttu-id="9d9e4-169">将报告作为电子邮件发送</span><span class="sxs-lookup"><span data-stu-id="9d9e4-169">Send Report as E-mail</span></span>  
  
 <span data-ttu-id="9d9e4-170">**关闭**</span><span class="sxs-lookup"><span data-stu-id="9d9e4-170">**Close**</span></span>  
 <span data-ttu-id="9d9e4-171">关闭向导。</span><span class="sxs-lookup"><span data-stu-id="9d9e4-171">Close the wizard.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d9e4-172">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9d9e4-172">See Also</span></span>  
 <span data-ttu-id="9d9e4-173">[sp_syscollector_enable_collector (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-syscollector-enable-collector-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="9d9e4-173">[sp_syscollector_enable_collector &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syscollector-enable-collector-transact-sql) </span></span>  
 <span data-ttu-id="9d9e4-174">[sp_syscollector_disable_collector (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-syscollector-disable-collector-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="9d9e4-174">[sp_syscollector_disable_collector &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syscollector-disable-collector-transact-sql) </span></span>  
 <span data-ttu-id="9d9e4-175">[数据收集](data-collection.md) </span><span class="sxs-lookup"><span data-stu-id="9d9e4-175">[Data Collection](data-collection.md) </span></span>  
 [<span data-ttu-id="9d9e4-176">管理数据收集</span><span class="sxs-lookup"><span data-stu-id="9d9e4-176">Manage Data Collection</span></span>](manage-data-collection.md)  
  
  
