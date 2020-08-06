---
title: 将 PowerPivot 迁移到 SharePoint 2013 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: f698ceb1-d53e-4717-a3a0-225b346760d0
author: minewiskan
ms.author: owend
ms.openlocfilehash: 1e59c6d6553cc9c43155b059fedf4eb6e124ca55
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688320"
---
# <a name="migrate-powerpivot-to-sharepoint-2013"></a><span data-ttu-id="077f8-102">将 PowerPivot 迁移到 SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="077f8-102">Migrate PowerPivot to SharePoint 2013</span></span>


 <span data-ttu-id="077f8-103">SharePoint 2013 不支持就地升级。</span><span class="sxs-lookup"><span data-stu-id="077f8-103">SharePoint 2013 does not support in-place upgrade.</span></span> <span data-ttu-id="077f8-104">但是**支持数据库附加升级**过程。</span><span class="sxs-lookup"><span data-stu-id="077f8-104">However the procedure of **database-attach upgrade is supported**.</span></span> <span data-ttu-id="077f8-105">该行为不同于升级到 SharePoint 2010，在后者，客户可以在两个基本的升级方法（就地升级和数据库附加升级）之间进行选择。</span><span class="sxs-lookup"><span data-stu-id="077f8-105">The behavior is different from upgrading to SharePoint 2010, where a customer could choose between the two basic upgrade approaches, in-place upgrade and database-attach upgrade.</span></span>

 <span data-ttu-id="077f8-106">如果您具有与 SharePoint 2010 相集成的 [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] 安装，则不能就地升级 SharePoint 服务器。</span><span class="sxs-lookup"><span data-stu-id="077f8-106">If you have a [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] installation integrated with SharePoint 2010, you cannot upgrade in-place the SharePoint server.</span></span> <span data-ttu-id="077f8-107">不过，您可以将内容数据库和服务应用程序数据库从 SharePoint 2010 场迁移到 SharePoint 2013 场。</span><span class="sxs-lookup"><span data-stu-id="077f8-107">However you can migrate content databases and service application databases from the SharePoint 2010 farm to a SharePoint 2013 farm.</span></span> <span data-ttu-id="077f8-108">本主题概要介绍了完成数据库附加升级以及完成与 PowerPivot 相关的迁移所需的步骤。</span><span class="sxs-lookup"><span data-stu-id="077f8-108">This topic is an overview of the steps required to complete a database-attach upgrade and complete a migration related to PowerPivot:</span></span>

 <span data-ttu-id="077f8-109">**[!INCLUDE[applies](../../../includes/applies-md.md)]** SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="077f8-109">**[!INCLUDE[applies](../../../includes/applies-md.md)]**  SharePoint 2013</span></span>

### <a name="migration-overview"></a><span data-ttu-id="077f8-110">迁移概述</span><span class="sxs-lookup"><span data-stu-id="077f8-110">Migration Overview</span></span>

|<span data-ttu-id="077f8-111">1</span><span class="sxs-lookup"><span data-stu-id="077f8-111">1</span></span>|<span data-ttu-id="077f8-112">2</span><span class="sxs-lookup"><span data-stu-id="077f8-112">2</span></span>|<span data-ttu-id="077f8-113">3</span><span class="sxs-lookup"><span data-stu-id="077f8-113">3</span></span>|<span data-ttu-id="077f8-114">4</span><span class="sxs-lookup"><span data-stu-id="077f8-114">4</span></span>|
|-------|-------|-------|-------|
|<span data-ttu-id="077f8-115">准备 SharePoint 2013 场</span><span class="sxs-lookup"><span data-stu-id="077f8-115">Prepare the SharePoint 2013 farm</span></span>|<span data-ttu-id="077f8-116">备份、复制、还原数据库。</span><span class="sxs-lookup"><span data-stu-id="077f8-116">Backup, copy, restore databases.</span></span>|<span data-ttu-id="077f8-117">装入内容数据库</span><span class="sxs-lookup"><span data-stu-id="077f8-117">Mount content databases</span></span>|<span data-ttu-id="077f8-118">迁移 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 计划</span><span class="sxs-lookup"><span data-stu-id="077f8-118">Migrate [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] Schedules</span></span>|
||[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]|<span data-ttu-id="077f8-119">SharePoint 管理中心</span><span class="sxs-lookup"><span data-stu-id="077f8-119">SharePoint Central Administration</span></span><br /><br /> <span data-ttu-id="077f8-120">Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="077f8-120">Windows PowerShell</span></span>|<span data-ttu-id="077f8-121">SharePoint 应用程序页</span><span class="sxs-lookup"><span data-stu-id="077f8-121">SharePoint application Pages</span></span><br /><br /> <span data-ttu-id="077f8-122">Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="077f8-122">Windows PowerShell</span></span>|

 <span data-ttu-id="077f8-123">**本主题内容：**</span><span class="sxs-lookup"><span data-stu-id="077f8-123">**In this topic:**</span></span>

-   [<span data-ttu-id="077f8-124">1) 准备 SharePoint 2013 场</span><span class="sxs-lookup"><span data-stu-id="077f8-124">1) Prepare the SharePoint 2013 Farm</span></span>](#bkmk_prepare_sharepoint2013)

-   [<span data-ttu-id="077f8-125">2) 备份、复制、还原数据库</span><span class="sxs-lookup"><span data-stu-id="077f8-125">2) Backup, Copy, Restore the Databases</span></span>](#bkmk_backup_restore)

-   [<span data-ttu-id="077f8-126">3) 准备 Web 应用程序和装入内容数据库</span><span class="sxs-lookup"><span data-stu-id="077f8-126">3) Prepare Web Applications and Mount Content Databases</span></span>](#bkmk_prepare_mount_databases)

-   [<span data-ttu-id="077f8-127">4) 升级 PowerPivot 计划</span><span class="sxs-lookup"><span data-stu-id="077f8-127">4) Upgrade PowerPivot Schedules</span></span>](#bkmk_upgrade_powerpivot_schedules)

-   [<span data-ttu-id="077f8-128">其他资源</span><span class="sxs-lookup"><span data-stu-id="077f8-128">Additional Resources</span></span>](#bkmk_additional_resources)

##  <a name="1-prepare-the-sharepoint-2013-farm"></a><a name="bkmk_prepare_sharepoint2013"></a><span data-ttu-id="077f8-129">1) 准备 SharePoint 2013 场</span><span class="sxs-lookup"><span data-stu-id="077f8-129">1) Prepare the SharePoint 2013 Farm</span></span>

1.  > [!TIP]
    >  <span data-ttu-id="077f8-130">查看为您的现有 Web 应用程序配置的身份验证方法。</span><span class="sxs-lookup"><span data-stu-id="077f8-130">Review the authentication method your existing web applications are configured for.</span></span> <span data-ttu-id="077f8-131">SharePoint 2013 Web 应用程序默认为基于声明的身份验证。</span><span class="sxs-lookup"><span data-stu-id="077f8-131">SharePoint 2013 web applications default to claims-based authentication.</span></span> <span data-ttu-id="077f8-132">为经典模式身份验证配置的 SharePoint 2010 Web 应用程序要求附加的步骤以便将数据库从 SharePoint 2010 迁移到 SharePoint 2013。</span><span class="sxs-lookup"><span data-stu-id="077f8-132">SharePoint 2010 web applications configured for classic-mode authentication require additional steps to migrate databases from SharePoint 2010 to SharePoint 2013.</span></span> <span data-ttu-id="077f8-133">如果为经典模式身份验证配置了您的 Web 应用程序，则查看 SharePoint 2013 文档。</span><span class="sxs-lookup"><span data-stu-id="077f8-133">If your web applications are configured for classic-mode authentication, review the SharePoint 2013 documentation.</span></span>

2.  <span data-ttu-id="077f8-134">安装新的 SharePoint Server 2013 场。</span><span class="sxs-lookup"><span data-stu-id="077f8-134">Install a new SharePoint Server 2013 farm.</span></span>

3.  <span data-ttu-id="077f8-135">[!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 在 SharePoint 模式下安装服务器的实例。</span><span class="sxs-lookup"><span data-stu-id="077f8-135">Install an instance of a [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] server in SharePoint mode.</span></span> <span data-ttu-id="077f8-136">有关详细信息，请参阅 [PowerPivot for SharePoint 2013 Installation](https://docs.microsoft.com/analysis-services/instances/install-windows/install-analysis-services-in-power-pivot-mode)。</span><span class="sxs-lookup"><span data-stu-id="077f8-136">For more information, see [PowerPivot for SharePoint 2013 Installation](https://docs.microsoft.com/analysis-services/instances/install-windows/install-analysis-services-in-power-pivot-mode).</span></span>

4.  <span data-ttu-id="077f8-137">在 SharePoint 场中的每台服务器上运行 [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] 2013 安装包 **spPowerPivot.msi** 。</span><span class="sxs-lookup"><span data-stu-id="077f8-137">Run the [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] 2013 installation package **spPowerPivot.msi** on each server in the SharePoint farm.</span></span> <span data-ttu-id="077f8-138">有关详细信息，请参阅[在 SharePoint 2013&#41;中安装或卸载 PowerPivot for SharePoint 外接程序 &#40;](https://docs.microsoft.com/analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013)。</span><span class="sxs-lookup"><span data-stu-id="077f8-138">For more information, see [Install or Uninstall the PowerPivot for SharePoint Add-in &#40;SharePoint 2013&#41;](https://docs.microsoft.com/analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013).</span></span>

5.  <span data-ttu-id="077f8-139">在 SharePoint 2013 管理中心配置 Excel Services 服务应用程序，以使用在前面的步骤中创建的 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] SharePoint 模式服务器。</span><span class="sxs-lookup"><span data-stu-id="077f8-139">In SharePoint 2013 Central Administration, configure the Excel Services service application to use the [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] SharePoint mode server created in the previous step.</span></span> <span data-ttu-id="077f8-140">有关详细信息，请参阅[PowerPivot for SharePoint 2013 安装](https://docs.microsoft.com/analysis-services/instances/install-windows/install-analysis-services-in-power-pivot-mode)中的 "配置基本 Analysis Services SharePoint 集成" 部分。</span><span class="sxs-lookup"><span data-stu-id="077f8-140">For more information, see the "Configure Basic Analysis Services SharePoint Integration" section of [PowerPivot for SharePoint 2013 Installation](https://docs.microsoft.com/analysis-services/instances/install-windows/install-analysis-services-in-power-pivot-mode).</span></span>

##  <a name="2-backup-copy-restore-the-databases"></a><a name="bkmk_backup_restore"></a><span data-ttu-id="077f8-141">2) 备份、复制、还原数据库</span><span class="sxs-lookup"><span data-stu-id="077f8-141">2) Backup, Copy, Restore the Databases</span></span>
 <span data-ttu-id="077f8-142">"SharePoint 数据库附加升级" 过程是一系列步骤，用于将 PowerPivot 相关内容和服务应用程序数据库备份、复制和还原到 SharePoint 2013 场。</span><span class="sxs-lookup"><span data-stu-id="077f8-142">The "SharePoint database-attach upgrade" process is a sequence of steps to back up, copy, and restore PowerPivot related content and service application databases to the SharePoint 2013 farm.</span></span>

1.  <span data-ttu-id="077f8-143">**将数据库设为只读：** 在 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 中，右键单击数据库名称，然后单击“属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="077f8-143">**Set Database to read-only:** In [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], right-click the database name and click **Properties**.</span></span> <span data-ttu-id="077f8-144">在“选项”\*\*\*\* 页中，将“数据库只读”\*\*\*\* 属性设置为 **True**。</span><span class="sxs-lookup"><span data-stu-id="077f8-144">On the **Options** page, set the **Database read-Only** property to **True**.</span></span>

2.  <span data-ttu-id="077f8-145">**备份：** 备份您要迁移到 SharePoint 2013 场的每个内容数据库和服务应用程序数据库。</span><span class="sxs-lookup"><span data-stu-id="077f8-145">**Back up:** Back up each content database and service application database that you want to migrate to the SharePoint 2013 farm.</span></span> <span data-ttu-id="077f8-146">在 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 中，右键单击数据库名称，再单击“任务”\*\*\*\*，然后单击“备份”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="077f8-146">In [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], right-click the database name, click **Tasks**, and click **Back up**.</span></span>

3.  <span data-ttu-id="077f8-147">将数据库备份文件 (.bak) 复制到所需的目标服务器。</span><span class="sxs-lookup"><span data-stu-id="077f8-147">File copy the database backup files (.bak) to the desired destination server.</span></span>

4.  <span data-ttu-id="077f8-148">**还原：** 将数据库还原到目标 [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="077f8-148">**Restore:** Restore the databases to the destination [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)].</span></span> <span data-ttu-id="077f8-149">可以使用 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]完成此步骤。</span><span class="sxs-lookup"><span data-stu-id="077f8-149">This step can be completed using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)].</span></span>

5.  <span data-ttu-id="077f8-150">**将数据库设为读写：** 将“数据库只读”\*\*\*\* 设置为 **False**。</span><span class="sxs-lookup"><span data-stu-id="077f8-150">**Set Database to read-write:** Set the **Database read-Only** to **False**.</span></span>

##  <a name="3-prepare-web-applications-and-mount-content-databases"></a><a name="bkmk_prepare_mount_databases"></a><span data-ttu-id="077f8-151">3) 准备 Web 应用程序并装载内容数据库</span><span class="sxs-lookup"><span data-stu-id="077f8-151">3) Prepare Web Applications and Mount Content Databases</span></span>
 <span data-ttu-id="077f8-152">有关以下过程的详细说明，请参阅[将数据库从 sharepoint 2010 升级到 sharepoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=256690) (https://go.microsoft.com/fwlink/p/?LinkId=256690) 。</span><span class="sxs-lookup"><span data-stu-id="077f8-152">For a more detailed explanation of the following procedures, see [Upgrade databases from SharePoint 2010 to SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=256690) (https://go.microsoft.com/fwlink/p/?LinkId=256690).</span></span>

1.  <span data-ttu-id="077f8-153">**使数据库脱机：**</span><span class="sxs-lookup"><span data-stu-id="077f8-153">**Take Databases Offline:**</span></span>

     <span data-ttu-id="077f8-154">使用 SharePoint 管理中心使每个 SharePoint 2013 内容数据库脱机。</span><span class="sxs-lookup"><span data-stu-id="077f8-154">Take each SharePoint 2013 content database offline, using SharePoint Central Administration.</span></span> <span data-ttu-id="077f8-155">内容数据库将被您所复制到的数据库替换。</span><span class="sxs-lookup"><span data-stu-id="077f8-155">The content databases are replaced by the databases you copied over.</span></span> <span data-ttu-id="077f8-156">考虑哪个顺序是针对您的环境的最佳顺序。</span><span class="sxs-lookup"><span data-stu-id="077f8-156">Consider what is the best sequence for your environment.</span></span> <span data-ttu-id="077f8-157">考虑首先使每个数据库脱机并装入其相关的替换数据库，然后再使下一内容数据库脱机。</span><span class="sxs-lookup"><span data-stu-id="077f8-157">Consider taking each database offline and mount its relevant replacement database before taking the next content database offline.</span></span> <span data-ttu-id="077f8-158">另一个选项是使所有内容数据库作为一组而一起脱机。</span><span class="sxs-lookup"><span data-stu-id="077f8-158">Another option is to take all the content databases offline as a group.</span></span>

    1.  <span data-ttu-id="077f8-159">在 SharePoint 管理中心中，单击 **“应用程序管理”**。</span><span class="sxs-lookup"><span data-stu-id="077f8-159">In SharePoint Central Administration, click **Application Management**.</span></span>

    2.  <span data-ttu-id="077f8-160">单击 **“管理内容数据库”**。</span><span class="sxs-lookup"><span data-stu-id="077f8-160">Click **Manage Content Databases**.</span></span>

    3.  <span data-ttu-id="077f8-161">单击数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="077f8-161">Click the name of the database.</span></span>

    4.  <span data-ttu-id="077f8-162">在 **“管理内容数据库设置”** 上，将 **“数据库状态”** 设置为 **“脱机”**。</span><span class="sxs-lookup"><span data-stu-id="077f8-162">On the **Manage Content Database Settings**, set **Database status** to **Offline**.</span></span>

    5.  <span data-ttu-id="077f8-163">选择 **“删除内容数据库”**。</span><span class="sxs-lookup"><span data-stu-id="077f8-163">Select **Remove Content Database**.</span></span> <span data-ttu-id="077f8-164">请注意显示的警告：在内容数据库中存储的站点将无法继续访问。</span><span class="sxs-lookup"><span data-stu-id="077f8-164">Note the warning that sites stored in the content database will no longer be accessible.</span></span>

-   <span data-ttu-id="077f8-165">**装入内容数据库：**</span><span class="sxs-lookup"><span data-stu-id="077f8-165">**Mount content databases:**</span></span>

     <span data-ttu-id="077f8-166">使用 SharePoint 2013 Management shell 中的 PowerShell cmdlet 装入已迁移的内容数据库。</span><span class="sxs-lookup"><span data-stu-id="077f8-166">Use PowerShell cmdlets in the SharePoint 2013 Management shell to mount the migrated content database.</span></span> <span data-ttu-id="077f8-167">无需装入服务应用程序数据库，只需安装内容数据库： ![PowerShell 相关内容](../../../reporting-services/media/rs-powershellicon.jpg "PowerShell 相关内容")</span><span class="sxs-lookup"><span data-stu-id="077f8-167">The service application database does not need to be mounted, only the content databases: ![PowerShell related content](../../../reporting-services/media/rs-powershellicon.jpg "PowerShell related content")</span></span>

    ```powershell
    Mount-SPContentDatabase "SharePoint_Content_O14-KJSP1" -DatabaseServer "[server name]\powerpivot" -WebApplication [web application URL]
    ```

     <span data-ttu-id="077f8-168">有关详细信息，请参阅[附加或分离 (SharePoint Server 2010)  (的内容数据库](https://technet.microsoft.com/library/ff628582.aspx) https://technet.microsoft.com/library/ff628582.aspx) 。</span><span class="sxs-lookup"><span data-stu-id="077f8-168">For more information, see [Attach or detach content databases (SharePoint Server 2010)](https://technet.microsoft.com/library/ff628582.aspx) (https://technet.microsoft.com/library/ff628582.aspx).</span></span>

     <span data-ttu-id="077f8-169">**步骤完成时的状态：**  在装入操作完成时，用户可以看到已处于旧的内容数据库中的文件。</span><span class="sxs-lookup"><span data-stu-id="077f8-169">**Status when the step is complete:**  When the mount operation is complete, users can see files that were in the old content database.</span></span> <span data-ttu-id="077f8-170">因此，用户可以在文档库中看到和打开工作簿。</span><span class="sxs-lookup"><span data-stu-id="077f8-170">Therefore users can see and open the workbooks in the document library.</span></span>

    > [!TIP]
    >  <span data-ttu-id="077f8-171">在迁移过程中在此时可为迁移的工作簿创建新计划。</span><span class="sxs-lookup"><span data-stu-id="077f8-171">It is possible at this point in the migration process to create new schedules for the migrated workbooks.</span></span> <span data-ttu-id="077f8-172">但是，这些计划在新的 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 服务应用程序数据库中创建，而非您从旧的 SharePoint 场中复制的数据库。</span><span class="sxs-lookup"><span data-stu-id="077f8-172">However, the schedules are created in the new [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] service application database, and not the database you copied from the old SharePoint farm.</span></span> <span data-ttu-id="077f8-173">因此，它们将不会包含任何旧计划。</span><span class="sxs-lookup"><span data-stu-id="077f8-173">Therefore it will not contain any of the old schedules.</span></span> <span data-ttu-id="077f8-174">在您完成以下步骤以便使用旧数据库和迁移旧计划后，新计划将不可用。</span><span class="sxs-lookup"><span data-stu-id="077f8-174">After you complete the following steps to use the old database and migrate the old schedules, the new schedules are not available.</span></span>

### <a name="troubleshoot-issues-when-you-attempt-to-mount-databases"></a><span data-ttu-id="077f8-175">解决在您尝试装入数据库时出现的问题</span><span class="sxs-lookup"><span data-stu-id="077f8-175">Troubleshoot issues when you attempt to mount databases</span></span>
 <span data-ttu-id="077f8-176">本节介绍在装入数据库时遇到的可能问题。</span><span class="sxs-lookup"><span data-stu-id="077f8-176">This section summarizes possible issues encountered when mounting the database.</span></span>

1.  <span data-ttu-id="077f8-177">**身份验证错误：** 如果您看到与身份验证相关的错误，则查看源 Web 应用程序正在使用的身份验证模式。</span><span class="sxs-lookup"><span data-stu-id="077f8-177">**Authentication errors:** If you see errors related to authentication, review what authentication mode the source web applications are using.</span></span> <span data-ttu-id="077f8-178">该错误可能是由于身份验证在 SharePoint 2013 Web 应用程序和 SharePoint 2010 Web 应用程序之间不匹配导致的。</span><span class="sxs-lookup"><span data-stu-id="077f8-178">The error could be caused by a mismatch in authentication between the SharePoint 2013 web application and the SharePoint 2010 web application.</span></span> <span data-ttu-id="077f8-179">有关详细信息，请参阅 [1) 准备 SharePoint 2013 场](#bkmk_prepare_sharepoint2013) 。</span><span class="sxs-lookup"><span data-stu-id="077f8-179">See the [1) Prepare the SharePoint 2013 Farm](#bkmk_prepare_sharepoint2013) for more information.</span></span>

2.  <span data-ttu-id="077f8-180">**缺少 PowerPivot 文件：** 如果您看到与缺少 PowerPivot .dll 相关的错误，则 **spPowerPivot.msi** 尚未安装或者 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 配置工具尚未用于配置 PowerPivot。</span><span class="sxs-lookup"><span data-stu-id="077f8-180">**Missing PowerPivot.Files:** If you see errors related to missing PowerPivot .dlls, the **spPowerPivot.msi** has not been installed or the [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] Configuration Tool has not been used to configure PowerPivot.</span></span>

##  <a name="4-upgrade-powerpivot-schedules"></a><a name="bkmk_upgrade_powerpivot_schedules"></a><span data-ttu-id="077f8-181">4) 升级 PowerPivot 计划</span><span class="sxs-lookup"><span data-stu-id="077f8-181">4) Upgrade PowerPivot Schedules</span></span>
 <span data-ttu-id="077f8-182">本节介绍了用于迁移 PowerPivot 计划的详细信息和选项。</span><span class="sxs-lookup"><span data-stu-id="077f8-182">This section describes the details and options for migrating PowerPivot schedules.</span></span> <span data-ttu-id="077f8-183">迁移计划是一个由两个步骤构成的过程。</span><span class="sxs-lookup"><span data-stu-id="077f8-183">Schedule migration is a two-step process.</span></span> <span data-ttu-id="077f8-184">首先将 PowerPivot 服务应用程序配置为使用已迁移的服务应用程序数据库。</span><span class="sxs-lookup"><span data-stu-id="077f8-184">First configure the PowerPivot service application to use the migrated service application database.</span></span> <span data-ttu-id="077f8-185">其次，选择用于计划迁移的两个选项之一。</span><span class="sxs-lookup"><span data-stu-id="077f8-185">Second, choose one of two options for schedule migration.</span></span>

 <span data-ttu-id="077f8-186">**将服务应用程序配置为使用已迁移的服务应用程序数据库。**</span><span class="sxs-lookup"><span data-stu-id="077f8-186">**Configure the service application to use the migrated service application database.**</span></span>

 <span data-ttu-id="077f8-187">在 SharePoint 管理中心中，将 PowerPivot 服务应用程序配置为使用您复制到的旧服务应用程序数据库。</span><span class="sxs-lookup"><span data-stu-id="077f8-187">In SharePoint Central Administration to configure the PowerPivot services application to use the old service application database you copied over.</span></span> <span data-ttu-id="077f8-188">PowerPivot 服务将服务应用程序数据库升级到新架构。</span><span class="sxs-lookup"><span data-stu-id="077f8-188">The PowerPivot Service upgrades the service application database to the new schema.</span></span>

1.  <span data-ttu-id="077f8-189">在 SharePoint 管理中心中，单击 **“管理服务应用程序”**。</span><span class="sxs-lookup"><span data-stu-id="077f8-189">In SharePoint Central Administration, click **Manage Service Applications**.</span></span>

2.  <span data-ttu-id="077f8-190">找到 PowerPivot 服务应用程序，例如 "默认 PowerPivot 服务应用程序"，单击服务应用程序的名称，然后单击 SharePoint 功能区中的 "**属性**"。</span><span class="sxs-lookup"><span data-stu-id="077f8-190">Find the PowerPivot service application, for example "Default PowerPivot Service Application", click the name of the service application and click **Properties** in the SharePoint ribbon.</span></span>

3.  <span data-ttu-id="077f8-191">更新数据库服务器名称实例和数据库名称。</span><span class="sxs-lookup"><span data-stu-id="077f8-191">Update the database server name-instance and the database name.</span></span> <span data-ttu-id="077f8-192">更新为您备份、复制和还原的数据库的正确名称。</span><span class="sxs-lookup"><span data-stu-id="077f8-192">To the correct names for the database you backed up, copied, and restored.</span></span> <span data-ttu-id="077f8-193">在您单击 **“确定”** 后，将升级服务应用程序数据库。</span><span class="sxs-lookup"><span data-stu-id="077f8-193">Once you click **Ok**, the service application database is upgraded.</span></span> <span data-ttu-id="077f8-194">错误将位于 ULS 日志中。</span><span class="sxs-lookup"><span data-stu-id="077f8-194">Errors will be in the ULS log.</span></span>

 <span data-ttu-id="077f8-195">**升级 PowerPivot 计划**</span><span class="sxs-lookup"><span data-stu-id="077f8-195">**Upgrade PowerPivot schedules**</span></span>

 <span data-ttu-id="077f8-196">配置 PowerPivot 服务应用程序以便迁移刷新计划。</span><span class="sxs-lookup"><span data-stu-id="077f8-196">Configure the PowerPivot service application to migrate refresh schedules.</span></span>

-   <span data-ttu-id="077f8-197">**迁移计划选项 1：SharePoint 场管理员**</span><span class="sxs-lookup"><span data-stu-id="077f8-197">**Migrate Schedules option1: SharePoint farm administrator**</span></span>

    1.  <span data-ttu-id="077f8-198">在 SharePoint 2013 管理中， `Set-PowerPivotServiceApplication` 使用开关运行 cmdlet， `-StartMigratingRefreshSchedules` 以便启用自动的按需计划迁移![与 PowerShell 相关的内容](../../../reporting-services/media/rs-powershellicon.jpg "PowerShell 相关内容")。</span><span class="sxs-lookup"><span data-stu-id="077f8-198">In the SharePoint 2013 Management Run the `Set-PowerPivotServiceApplication` cmdlet with the `-StartMigratingRefreshSchedules` switch to enable automatic on demand schedule migration ![PowerShell related content](../../../reporting-services/media/rs-powershellicon.jpg "PowerShell related content").</span></span> <span data-ttu-id="077f8-199">下面的 Windows PowerShell 脚本假定只有一个 PowerPivot 服务应用程序。</span><span class="sxs-lookup"><span data-stu-id="077f8-199">The following Windows PowerShell script assumes that there is only one PowerPivot service application.</span></span>

        ```powershell
        $app = Get-PowerPivotServiceApplication
        Set-PowerPivotServiceApplication $app -StartMigratingRefreshSchedules
        ```

         <span data-ttu-id="077f8-200">在运行 Windows PowerShell 脚本后，计划将处于活动状态并且计划将在下一个适当的时间运行。</span><span class="sxs-lookup"><span data-stu-id="077f8-200">After the Windows PowerShell script is run, the schedules are active and the schedules will run at the next appropriate time.</span></span> <span data-ttu-id="077f8-201">但是，计划刷新页上的状态将不启用。</span><span class="sxs-lookup"><span data-stu-id="077f8-201">However, the status one the schedule refresh page is not enabled.</span></span> <span data-ttu-id="077f8-202">在计划首次运行时，将迁移该计划，并且在计划刷新页上，“已启用” \*\*\*\*  将为 true。</span><span class="sxs-lookup"><span data-stu-id="077f8-202">When the schedule runs the first time it will be migrated and on the schedule refresh page, **Enabled**  will be true.</span></span>

    2.  <span data-ttu-id="077f8-203">如果您想要检查 StartMigratingRefreshSchedules 属性的当前值，则运行以下 PowerShell 脚本。</span><span class="sxs-lookup"><span data-stu-id="077f8-203">If you want to check the current value of the StartMigratingRefreshSchedules property, run the following PowerShell script.</span></span> <span data-ttu-id="077f8-204">该脚本将遍历所有 PowerPivot 服务应用程序对象并且显示名称和属性值：</span><span class="sxs-lookup"><span data-stu-id="077f8-204">The Script loops through all PowerPivot service application objects and display the name and property values:</span></span>

        ```powershell
        $apps = Get-PowerPivotServiceApplication
        foreach ($app in $apps){ Get-PowerPivotServiceApplication $app | Format-Table -Property displayname, id, StartMigratingRefreshSchedules }
        ```

     <span data-ttu-id="077f8-205">**迁移计划选项 2：用户更新每个工作簿**</span><span class="sxs-lookup"><span data-stu-id="077f8-205">**Migrate Schedules option2: User updates each workbook**</span></span>

    1.  <span data-ttu-id="077f8-206">另一个用于迁移计划的选项是对每个工作簿都启用计划刷新。</span><span class="sxs-lookup"><span data-stu-id="077f8-206">Another option to migrate schedules is to enable the schedule refresh for each workbook.</span></span> <span data-ttu-id="077f8-207">导航到包含工作簿的文档库。</span><span class="sxs-lookup"><span data-stu-id="077f8-207">Navigate to the document library that contains the workbooks.</span></span>

    2.  <span data-ttu-id="077f8-208">打开上下文菜单，然后单击 **“管理 PowerPivot 数据刷新”**。</span><span class="sxs-lookup"><span data-stu-id="077f8-208">Open the context menu and click **Manage PowerPivot Data Refresh**.</span></span>

    3.  <span data-ttu-id="077f8-209">在 **“计划刷新”** 部分中，单击 **“启用”**。</span><span class="sxs-lookup"><span data-stu-id="077f8-209">In the **schedule refresh** section, click **Enable**.</span></span>

    4.  <span data-ttu-id="077f8-210">您可以选择 **“也尽快刷新”**。</span><span class="sxs-lookup"><span data-stu-id="077f8-210">You can select **Also refresh as soon as possible**.</span></span> <span data-ttu-id="077f8-211">此选项会在您单击“确定”后立即将一个刷新实例添加到队列中。</span><span class="sxs-lookup"><span data-stu-id="077f8-211">This option adds one instance of the refresh to the queue as soon as you click ok.</span></span> <span data-ttu-id="077f8-212">定期刷新计划仍将在适当的时间触发。</span><span class="sxs-lookup"><span data-stu-id="077f8-212">The regular refresh schedule still triggers at the appropriate time.</span></span>

    5.  <span data-ttu-id="077f8-213">单击“确定” 。</span><span class="sxs-lookup"><span data-stu-id="077f8-213">Click **Ok**.</span></span> <span data-ttu-id="077f8-214">刷新历史记录现在将在刷新页中可见，并且刷新将在普通时间触发。</span><span class="sxs-lookup"><span data-stu-id="077f8-214">The refresh history is now visible in the refresh page, the schedule will fire at the normal time.</span></span>

 <span data-ttu-id="077f8-215">**SQL Server 2008 R2 PowerPivot 工作簿**</span><span class="sxs-lookup"><span data-stu-id="077f8-215">**SQL Server 2008 R2 PowerPivot workbooks**</span></span>

-   <span data-ttu-id="077f8-216">在 SQL Server 2012 SP1 PowerPivot for SharePoint 2013 中使用时，SQL Server 2008 R2 PowerPivot 工作簿将不会自动升级。</span><span class="sxs-lookup"><span data-stu-id="077f8-216">SQL Server 2008 R2 PowerPivot workbooks do not automatically upgrade when they are used in SQL Server 2012 SP1 PowerPivot for SharePoint 2013.</span></span> <span data-ttu-id="077f8-217">在您迁移包含 2008 R2 工作簿的内容数据库后，可以使用工作簿，但计划将不会升级。</span><span class="sxs-lookup"><span data-stu-id="077f8-217">After you migrate a content database containing the 2008 R2 workbooks, you can use the workbooks but the schedules do not upgrade.</span></span>

-   <span data-ttu-id="077f8-218">有关详细信息，请参阅 [升级工作簿和计划的数据刷新 (SharePoint 2013)](https://docs.microsoft.com/analysis-services/instances/install-windows/upgrade-workbooks-and-scheduled-data-refresh-sharepoint-2013)。</span><span class="sxs-lookup"><span data-stu-id="077f8-218">For more information, see [Upgrade Workbooks and Scheduled Data Refresh &#40;SharePoint 2013&#41;](https://docs.microsoft.com/analysis-services/instances/install-windows/upgrade-workbooks-and-scheduled-data-refresh-sharepoint-2013).</span></span>

##  <a name="additional-resources"></a><a name="bkmk_additional_resources"></a> <span data-ttu-id="077f8-219">其他资源</span><span class="sxs-lookup"><span data-stu-id="077f8-219">Additional Resources</span></span>

> [!NOTE]
>  <span data-ttu-id="077f8-220">有关 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 和 SharePoint 数据库附加升级的详细信息，请参阅以下内容：</span><span class="sxs-lookup"><span data-stu-id="077f8-220">For more information on [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] and SharePoint database-attach upgrade, see the following:</span></span>

-   <span data-ttu-id="077f8-221">[升级工作簿和计划的数据刷新 (SharePoint 2013)](https://docs.microsoft.com/analysis-services/instances/install-windows/upgrade-workbooks-and-scheduled-data-refresh-sharepoint-2013)。</span><span class="sxs-lookup"><span data-stu-id="077f8-221">[Upgrade Workbooks and Scheduled Data Refresh &#40;SharePoint 2013&#41;](https://docs.microsoft.com/analysis-services/instances/install-windows/upgrade-workbooks-and-scheduled-data-refresh-sharepoint-2013).</span></span>

-   <span data-ttu-id="077f8-222">[SharePoint 2013 (升级过程概述](https://go.microsoft.com/fwlink/p/?LinkId=256688) https://go.microsoft.com/fwlink/p/?LinkId=256688) 。</span><span class="sxs-lookup"><span data-stu-id="077f8-222">[Overview of the upgrade process to SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=256688) (https://go.microsoft.com/fwlink/p/?LinkId=256688).</span></span>

-   <span data-ttu-id="077f8-223">[升级到 SharePoint 2013 (之前进行清理准备](https://go.microsoft.com/fwlink/p/?LinkId=256689) https://go.microsoft.com/fwlink/p/?LinkId=256689) 。</span><span class="sxs-lookup"><span data-stu-id="077f8-223">[Clean up preparations before an upgrade to SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=256689) (https://go.microsoft.com/fwlink/p/?LinkId=256689).</span></span>

-   <span data-ttu-id="077f8-224">[将数据库从 sharepoint 2010 升级到 sharepoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=256690) (https://go.microsoft.com/fwlink/p/?LinkId=256690) 。</span><span class="sxs-lookup"><span data-stu-id="077f8-224">[Upgrade databases from SharePoint 2010 to SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=256690) (https://go.microsoft.com/fwlink/p/?LinkId=256690).</span></span>
