---
title: 卸载 PowerPivot for SharePoint |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: 3941a2f0-0d0c-4d1a-8618-7a6a7751beac
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 8ca65a04578cbce2ed7eb2831068260d9f0e445a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586134"
---
# <a name="uninstall-powerpivot-for-sharepoint"></a><span data-ttu-id="67a04-102">卸载 PowerPivot for SharePoint</span><span class="sxs-lookup"><span data-stu-id="67a04-102">Uninstall PowerPivot for SharePoint</span></span>
  <span data-ttu-id="67a04-103">卸载 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 安装是一个由多个步骤构成的操作，包括准备卸载、从场中删除功能和解决方案以及删除程序文件和注册表设置。</span><span class="sxs-lookup"><span data-stu-id="67a04-103">Uninstalling a [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] installation is a multi-step operation that includes preparing for uninstall, removing features and solutions from the farm, and removing program files and registry settings.</span></span>  
  
 <span data-ttu-id="67a04-104">**[!INCLUDE[applies](../../includes/applies-md.md)]**  SharePoint 2013 | SharePoint 2010</span><span class="sxs-lookup"><span data-stu-id="67a04-104">**[!INCLUDE[applies](../../includes/applies-md.md)]**  SharePoint 2013 | SharePoint 2010</span></span>  
  
 <span data-ttu-id="67a04-105">**本主题内容：**</span><span class="sxs-lookup"><span data-stu-id="67a04-105">**In this topic:**</span></span>  
  
-   [<span data-ttu-id="67a04-106">先决条件</span><span class="sxs-lookup"><span data-stu-id="67a04-106">Prerequisites</span></span>](#prereq)  
  
-   [<span data-ttu-id="67a04-107">步骤 1：卸载前一览表</span><span class="sxs-lookup"><span data-stu-id="67a04-107">Step 1: Pre-Uninstall Checklist</span></span>](#bkmk_before)  
  
-   [<span data-ttu-id="67a04-108">步骤 2：从 SharePoint 删除功能和解决方案</span><span class="sxs-lookup"><span data-stu-id="67a04-108">Step 2: Remove Features and Solutions from SharePoint</span></span>](#bkmk_remove)  
  
-   [<span data-ttu-id="67a04-109">步骤 3：运行 SQL Server 安装程序以便从本地计算机中删除程序</span><span class="sxs-lookup"><span data-stu-id="67a04-109">Step 3: Run SQL Server Setup to Remove Programs from the Local Computer</span></span>](#bkmk_uninstall)  
  
-   [<span data-ttu-id="67a04-110">步骤 4：卸载 PowerPivot for SharePoint 外接程序</span><span class="sxs-lookup"><span data-stu-id="67a04-110">Step 4: Uninstall the PowerPivot for SharePoint add-in</span></span>](#bkmk_addin)  
  
-   [<span data-ttu-id="67a04-111">步骤 5：验证卸载情况</span><span class="sxs-lookup"><span data-stu-id="67a04-111">Step 5: Verify Uninstall</span></span>](#verify)  
  
-   [<span data-ttu-id="67a04-112">步骤 6：卸载后一览表</span><span class="sxs-lookup"><span data-stu-id="67a04-112">Step 6: Post-Uninstall Checklist</span></span>](#bkmk_post)  
  
##  <a name="prerequisites"></a><a name="prereq"></a><span data-ttu-id="67a04-113">先决条件</span><span class="sxs-lookup"><span data-stu-id="67a04-113">Prerequisites</span></span>  
  
-   <span data-ttu-id="67a04-114">您必须是 SharePoint 场管理员或服务应用程序管理员，才能在场中卸载功能和解决方案。</span><span class="sxs-lookup"><span data-stu-id="67a04-114">You must be a SharePoint farm administrator or service application administrator to uninstall features and solutions in the farm.</span></span>  
  
-   <span data-ttu-id="67a04-115">如果您还要卸载数据库引擎，必须是 SQL Server 系统管理员和本地 Administrators 组的成员。</span><span class="sxs-lookup"><span data-stu-id="67a04-115">You must be a SQL Server System Administrator and a member of the local Administrators group if you are also uninstalling the Database Engine.</span></span>  
  
-   <span data-ttu-id="67a04-116">您必须是 Analysis Services 系统管理员和本地 Administrators 组的成员才能卸载 Analysis Services 和 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="67a04-116">You must be an Analysis Services System Administrator and a member of the local Administrators group to uninstall Analysis Services and [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)].</span></span>  
  
##  <a name="step-1-pre-uninstall-checklist"></a><a name="bkmk_before"></a> <span data-ttu-id="67a04-117">步骤 1：卸载前一览表</span><span class="sxs-lookup"><span data-stu-id="67a04-117">Step 1: Pre-Uninstall Checklist</span></span>  
 <span data-ttu-id="67a04-118">一旦支持查询和数据处理的软件从场中删除后，PowerPivot 数据访问就会被禁用。</span><span class="sxs-lookup"><span data-stu-id="67a04-118">PowerPivot data access will be disabled once the software that supports query and data processing is removed from the farm.</span></span> <span data-ttu-id="67a04-119">作为第一步，您应该主动删除不再正常运行的文件和库。</span><span class="sxs-lookup"><span data-stu-id="67a04-119">As a first step, you should preemptively delete files and libraries that will no longer be operational.</span></span> <span data-ttu-id="67a04-120">这样，可以在卸载软件前解决与“缺少数据”有关的任何问题。</span><span class="sxs-lookup"><span data-stu-id="67a04-120">This lets you address any questions or concerns about 'missing data' before you uninstall the software.</span></span>  
  
1.  <span data-ttu-id="67a04-121">删除与 PowerPivot for SharePoint 安装关联的所有 PowerPivot 工作簿、文档和库。</span><span class="sxs-lookup"><span data-stu-id="67a04-121">Delete all PowerPivot workbooks, documents, and libraries that are associated with a PowerPivot for SharePoint installation.</span></span> <span data-ttu-id="67a04-122">一旦卸载软件后，库和文档都将失效。</span><span class="sxs-lookup"><span data-stu-id="67a04-122">Neither the libraries nor the documents will function once the software is uninstalled.</span></span>  
  
    -   [<span data-ttu-id="67a04-123">删除 PowerPivot 库</span><span class="sxs-lookup"><span data-stu-id="67a04-123">Delete PowerPivot Gallery</span></span>](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/delete-power-pivot-gallery)  
  
    -   [<span data-ttu-id="67a04-124">删除 PowerPivot 数据馈送库</span><span class="sxs-lookup"><span data-stu-id="67a04-124">Delete a PowerPivot Data Feed Library</span></span>](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/delete-a-power-pivot-data-feed-library)  
  
2.  <span data-ttu-id="67a04-125">删除包含或引用 PowerPivot 数据的其他库中的 Excel 工作簿或 Reporting Services 报表。</span><span class="sxs-lookup"><span data-stu-id="67a04-125">Delete Excel workbooks or Reporting Services reports in other libraries that contain or reference PowerPivot data.</span></span>  
  
3.  <span data-ttu-id="67a04-126">删除引用 PowerPivot 数据的 PerformancePoint 面板中的所有 Web 部件。</span><span class="sxs-lookup"><span data-stu-id="67a04-126">Remove any web part in a PerformancePoint dashboard that references PowerPivot data.</span></span>  
  
4.  <span data-ttu-id="67a04-127">查看针对现有站点和库的 SharePoint 权限，以便确定是否将需要更改它们。</span><span class="sxs-lookup"><span data-stu-id="67a04-127">Review SharePoint permissions on existing sites and libraries to determine whether you need to change them.</span></span> <span data-ttu-id="67a04-128">某些 PowerPivot 数据访问方案（尤其是通过 URL 连接字符串访问其他工作簿中的 PowerPivot 数据的辅助数据访问）要求读取权限，此权限高于通常分配给只能访问站点的 SharePoint 用户的“查看”权限。</span><span class="sxs-lookup"><span data-stu-id="67a04-128">Some PowerPivot data access scenarios, particularly secondary data access via a URL connection string to PowerPivot data in another workbook, require Read permissions, which is higher than the View permissions that are typically assigned to SharePoint users who only visit a site.</span></span> <span data-ttu-id="67a04-129">如果您不再要求“读取”权限，则可以相应降低权限。</span><span class="sxs-lookup"><span data-stu-id="67a04-129">If you no longer require Read permissions, you can reduce permissions accordingly.</span></span>  
  
5.  <span data-ttu-id="67a04-130">或者，在停止服务后等上几天，然后再卸载软件。</span><span class="sxs-lookup"><span data-stu-id="67a04-130">Optionally, stop the services and wait several days before uninstalling the software.</span></span> <span data-ttu-id="67a04-131">此步骤并非卸载所必需的，但在您解决可能疏漏的任何数据迁移或技术替代问题时，将能够选择暂时恢复服务。</span><span class="sxs-lookup"><span data-stu-id="67a04-131">This step is not necessary for uninstall, but it gives you the option of temporarily resuming the service while you work out any data migration or technology substitution issues that you might have missed.</span></span>  
  
##  <a name="step-2-remove-features-and-solutions-from-sharepoint"></a><a name="bkmk_remove"></a> <span data-ttu-id="67a04-132">步骤 2：从 SharePoint 删除功能和解决方案</span><span class="sxs-lookup"><span data-stu-id="67a04-132">Step 2: Remove Features and Solutions from SharePoint</span></span>  
 <span data-ttu-id="67a04-133">使用 PowerPivot 配置工具从 SharePoint 中删除 PowerPivot 服务和应用程序。</span><span class="sxs-lookup"><span data-stu-id="67a04-133">Use the PowerPivot Configuration Tool to remove PowerPivot services and applications from SharePoint.</span></span>  
  
-   <span data-ttu-id="67a04-134">你必须是场管理员、Analysis Services 实例上的服务器管理员和场的配置数据库上的“db_owner”  。</span><span class="sxs-lookup"><span data-stu-id="67a04-134">You must be a farm administrator, a server administrator on the Analysis Services instance, and **db_owner** on the farm's configuration database.</span></span>  
  
-   <span data-ttu-id="67a04-135">使用适合 SharePoint 版本的配置工具版本。</span><span class="sxs-lookup"><span data-stu-id="67a04-135">Use the appropriate version of the configuration tool for the version of SharePoint.</span></span> <span data-ttu-id="67a04-136">不能对 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 安装使用这两个工具。</span><span class="sxs-lookup"><span data-stu-id="67a04-136">Do not use either tool with [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] installations.</span></span>  
  
-   <span data-ttu-id="67a04-137">验证“SharePoint 管理”服务是否正在运行。</span><span class="sxs-lookup"><span data-stu-id="67a04-137">Verify that the SharePoint Administration service is running.</span></span>  
  
1.  <span data-ttu-id="67a04-138">**运行配置文件：** 注意，仅当 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 安装在本地服务器上时，才会列出这些配置工具。请在“开始”  菜单上，指向“所有程序”  ，依次单击 [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)]、“配置工具”  ，然后单击以下项之一：</span><span class="sxs-lookup"><span data-stu-id="67a04-138">**Run the Configuration tool:** Note the configuration tools are only listed only when [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] is installed on the local server.On the **Start** menu, point to **All Programs**, click [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], click **Configuration Tools**, and then click one of the following:</span></span>  
  
    -   <span data-ttu-id="67a04-139">**PowerPivot for SharePoint 2013 配置**</span><span class="sxs-lookup"><span data-stu-id="67a04-139">**PowerPivot for SharePoint 2013 Configuration**</span></span>  
  
    -   <span data-ttu-id="67a04-140">**PowerPivot 配置工具**</span><span class="sxs-lookup"><span data-stu-id="67a04-140">**PowerPivot Configuration Tool**</span></span>  
  
2.  <span data-ttu-id="67a04-141">选择 **“删除功能、服务、应用程序和解决方案”** ，然后单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="67a04-141">Select **Remove Features, Services, Applications, and Solutions** and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="67a04-142">也可以将窗口放大为实际大小。</span><span class="sxs-lookup"><span data-stu-id="67a04-142">Optionally, expand the window to full size.</span></span> <span data-ttu-id="67a04-143">您应该在该窗口的底部看到一个菜单栏，其中包含 **“验证”** 、 **“运行”** 和 **“退出”** 命令。</span><span class="sxs-lookup"><span data-stu-id="67a04-143">You should see a button bar at the bottom of the window that includes **Validate**, **Run**, and **Exit** commands.</span></span>  
  
4.  <span data-ttu-id="67a04-144">检查任务列表中的每个操作，了解每个操作的作用。</span><span class="sxs-lookup"><span data-stu-id="67a04-144">Review each action in the task list to understand what each one does.</span></span>  
  
     <span data-ttu-id="67a04-145">在 **“PowerPivot 服务应用程序”** 中，您可以选择删除与服务应用程序相关联的应用程序数据。</span><span class="sxs-lookup"><span data-stu-id="67a04-145">In **Remove PowerPivot Service Applications**, you are given the option of deleting application data associated with the service application.</span></span> <span data-ttu-id="67a04-146">应用程序数据是随服务应用程序创建的 SQL Server 数据库，目的在于存储数据刷新计划、数据库实例信息、使用情况数据，以及 PowerPivot for SharePoint 所使用的其他数据。</span><span class="sxs-lookup"><span data-stu-id="67a04-146">The application data is a SQL Server database that was created with the service application for the purpose of storing data refresh schedules, database instance information, usage data, and other data used by PowerPivot for SharePoint.</span></span> <span data-ttu-id="67a04-147">它并不存储用户文件，如 PowerPivot 工作簿。</span><span class="sxs-lookup"><span data-stu-id="67a04-147">It does not store user files, such as PowerPivot workbooks.</span></span> <span data-ttu-id="67a04-148">除非您有特定原因要保留应用程序数据（例如，您有与数据刷新或数据访问相关的数据保留策略），否则您可以删除应用程序数据库，而不删除 SharePoint 用户创建或保存的任何文件。</span><span class="sxs-lookup"><span data-stu-id="67a04-148">Unless you have a specific reason to keep the application data (for example, if you have data retention policies related to data refresh or data access) you can delete the application database without removing any files that were created or saved by SharePoint users.</span></span>  
  
     <span data-ttu-id="67a04-149">若要删除该数据库，请依次选择 **“删除 PowerPivot 服务应用程序”** 和 **“删除与此服务应用程序相关联的应用程序数据”**。</span><span class="sxs-lookup"><span data-stu-id="67a04-149">To delete the database, select **Remove PowerPivot Service Applications** and then select the **Delete application data associated with this service application**.</span></span>  
  
5.  <span data-ttu-id="67a04-150">或者，检查 **“输出”** 选项卡或 **“脚本”** 选项卡中的详细信息。</span><span class="sxs-lookup"><span data-stu-id="67a04-150">Optionally, review detailed information in the **Output** tab or **Script** tab.</span></span>  
  
     <span data-ttu-id="67a04-151">“输出”选项卡汇总了将由该工具执行的所有操作。</span><span class="sxs-lookup"><span data-stu-id="67a04-151">The Output tab is a summary of the actions that will be performed by the tool.</span></span> <span data-ttu-id="67a04-152">此信息保存在位于以下位置的日志文件中：</span><span class="sxs-lookup"><span data-stu-id="67a04-152">This information is saved in log files at:</span></span>  
  
     `C:\Program Files\Microsoft SQL Server\120\Tools\PowerPivotTools\SPAddinConfiguration\Log`  
  
     <span data-ttu-id="67a04-153">“脚本”选项卡显示 PowerShell cmdlet，或引用该工具将运行的 PowerShell 脚本文件。</span><span class="sxs-lookup"><span data-stu-id="67a04-153">The Script tab shows the PowerShell cmdlets or references the PowerShell script files that the tool will run.</span></span>  
  
6.  <span data-ttu-id="67a04-154">单击 **“验证”** 可检查每个操作是否有效。</span><span class="sxs-lookup"><span data-stu-id="67a04-154">Click **Validate** to check whether each action is valid.</span></span> <span data-ttu-id="67a04-155">如果 **“验证”** 不可用，这意味着所有操作都适用于您的系统。</span><span class="sxs-lookup"><span data-stu-id="67a04-155">If **Validate** is not available, it means that all of the actions are valid for your system.</span></span>  
  
7.  <span data-ttu-id="67a04-156">单击 **“运行”** 执行对此任务有效的所有操作。</span><span class="sxs-lookup"><span data-stu-id="67a04-156">Click **Run** to perform all of the actions that are valid for this task.</span></span> <span data-ttu-id="67a04-157">只有通过验证检查后， **“运行”** 才可用。</span><span class="sxs-lookup"><span data-stu-id="67a04-157">**Run** is available only after the validation check is passed.</span></span> <span data-ttu-id="67a04-158">单击“运行”后，出现以下警告，提醒你将在批处理模式下处理操作：“在工具中标记为有效的所有配置设置都将应用于 SharePoint 场  。</span><span class="sxs-lookup"><span data-stu-id="67a04-158">When you click **Run**, the following warning appears, reminding you that actions are processed in batch mode: "All of the configuration settings that are flagged as valid in the tool will be applied to the SharePoint farm.</span></span> <span data-ttu-id="67a04-159">是否继续?”</span><span class="sxs-lookup"><span data-stu-id="67a04-159">Do you want to continue?"</span></span>  
  
8.  <span data-ttu-id="67a04-160">单击 **“是”** 继续操作。</span><span class="sxs-lookup"><span data-stu-id="67a04-160">Click **Yes** to continue.</span></span>  
  
 <span data-ttu-id="67a04-161">**解决错误：**</span><span class="sxs-lookup"><span data-stu-id="67a04-161">**Troubleshooting errors:**</span></span>  
  
 <span data-ttu-id="67a04-162">在配置工具中，可以在“参数”窗格中查看每个操作的错误信息。</span><span class="sxs-lookup"><span data-stu-id="67a04-162">In the Configuration Tool, you can view error information in the Parameters pane for each action.</span></span> <span data-ttu-id="67a04-163">对于与解决方案部署或收回相关的问题，请验证是否已启动 SharePoint 管理服务。</span><span class="sxs-lookup"><span data-stu-id="67a04-163">For problems related to solution deployment or retraction, verify the SharePoint Administration service is started.</span></span> <span data-ttu-id="67a04-164">此服务运行可触发场中配置更改的计时器作业。</span><span class="sxs-lookup"><span data-stu-id="67a04-164">This service runs the timer jobs that trigger configuration changes in a farm.</span></span> <span data-ttu-id="67a04-165">如果该服务未运行，解决方案部署或收回将失败。</span><span class="sxs-lookup"><span data-stu-id="67a04-165">If the service is not running, solution deployment or retraction will fail.</span></span> <span data-ttu-id="67a04-166">持续出现的错误表示现有的部署或收回作业已存在于队列中，阻止配置工具执行进一步的操作。</span><span class="sxs-lookup"><span data-stu-id="67a04-166">Persistent errors indicate that an existing deployment or retraction job is already in the queue and blocking further action from the configuration tool.</span></span> <span data-ttu-id="67a04-167">可以使用以下 PowerShell 命令来验证服务是否正在运行。</span><span class="sxs-lookup"><span data-stu-id="67a04-167">You can use the following PowerShell command to verify the service is running.</span></span>  
  
```powershell
Get-Service | Where {$_.displayname -like "*sharepoint* administration*"}  
```  
  
 <span data-ttu-id="67a04-168">若要查找并删除已存在于队列中的部署或收回作业，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="67a04-168">To find and remove a deployment or retraction job that is already in the queue, do the following:</span></span>  
  
1.  <span data-ttu-id="67a04-169">对于其他所有错误，请查看 ULS 日志。</span><span class="sxs-lookup"><span data-stu-id="67a04-169">For all other errors, check the ULS logs.</span></span> <span data-ttu-id="67a04-170">有关详细信息，请参阅[配置和查看 SharePoint 日志文件和诊断日志记录 &#40;PowerPivot for SharePoint&#41;](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/configure-and-view-sharepoint-and-diagnostic-logging)。</span><span class="sxs-lookup"><span data-stu-id="67a04-170">For more information, see [Configure and View SharePoint Log Files  and Diagnostic Logging &#40;PowerPivot for SharePoint&#41;](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/configure-and-view-sharepoint-and-diagnostic-logging).</span></span>  
  
2.  <span data-ttu-id="67a04-171">以管理员身份启动 SharePoint Management Shell，然后运行以下命令查看队列中的作业：</span><span class="sxs-lookup"><span data-stu-id="67a04-171">Start the SharePoint Management Shell as an administrator and then run the following command to view jobs in the queue:</span></span>  
  
    ```cmd
    stsadm -o enumdeployments  
    ```  
  
3.  <span data-ttu-id="67a04-172">检查现有部署的以下信息： **“类型”** 是“收回”或“部署”， **“文件”** 为 powerpivotwebapp.wsp 或 powerpivotfarm.wsp。</span><span class="sxs-lookup"><span data-stu-id="67a04-172">Review existing deployments for the following information: **Type** is Retraction or Deployment, **File** is powerpivotwebapp.wsp or powerpivotfarm.wsp.</span></span>  
  
4.  <span data-ttu-id="67a04-173">对于与 PowerPivot 解决方案相关的部署或收回，请复制**JobId**的 GUID 值，然后将其粘贴到以下命令中 (使用 Shell 的 "编辑" 菜单上的 "标记"、"复制" 和 "粘贴" 命令复制 GUID) ：</span><span class="sxs-lookup"><span data-stu-id="67a04-173">For deployments or retractions related to PowerPivot solutions, copy the GUID value for **JobId** and then paste it into the following command (use the Mark, Copy, and Paste commands on the Shell's Edit menu to copy the GUID):</span></span>  
  
    ```cmd
    stsadm -o canceldeployment -id "<GUID>"  
    ```  
  
5.  <span data-ttu-id="67a04-174">通过依次单击 **“验证”** 和 **“运行”** ，在该配置工具中重试该任务。</span><span class="sxs-lookup"><span data-stu-id="67a04-174">Retry the task in the configuration tool by clicking **Validate** followed by **Run**.</span></span>  
  
 <span data-ttu-id="67a04-175">或者，您可以使用 PowerShell 从场中删除功能和解决方案。</span><span class="sxs-lookup"><span data-stu-id="67a04-175">Alternatively, you can use PowerShell to remove features and solutions from the farm.</span></span> <span data-ttu-id="67a04-176">有关详细信息，请参阅[PowerShell Reference for PowerPivot for SharePoint](/sql/analysis-services/powershell/powershell-reference-for-power-pivot-for-sharepoint)。</span><span class="sxs-lookup"><span data-stu-id="67a04-176">For more information, see [PowerShell Reference for PowerPivot for SharePoint](/sql/analysis-services/powershell/powershell-reference-for-power-pivot-for-sharepoint).</span></span>  
  
##  <a name="step-3-run-sql-server-setup-to-remove-programs-from-the-local-computer"></a><a name="bkmk_uninstall"></a> <span data-ttu-id="67a04-177">步骤 3：运行 SQL Server 安装程序以便从本地计算机中删除程序</span><span class="sxs-lookup"><span data-stu-id="67a04-177">Step 3: Run SQL Server Setup to Remove Programs from the Local Computer</span></span>  
 <span data-ttu-id="67a04-178">删除程序文件时，需运行 SQL Server 安装程序来卸载软件。</span><span class="sxs-lookup"><span data-stu-id="67a04-178">Deleting program files requires that you run SQL Server Setup to uninstall the software.</span></span> <span data-ttu-id="67a04-179">卸载程序将删除安装程序已创建的文件和注册表项。</span><span class="sxs-lookup"><span data-stu-id="67a04-179">Uninstall removes both files and the registry entries that were created by Setup.</span></span> <span data-ttu-id="67a04-180">您可以使用“程序和功能”页来卸载软件。</span><span class="sxs-lookup"><span data-stu-id="67a04-180">You can use the Programs and Features page to uninstall the software.</span></span> <span data-ttu-id="67a04-181">[!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 的安装是 SQL Server 安装的一部分。</span><span class="sxs-lookup"><span data-stu-id="67a04-181">An installation of [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] is part of a SQL Server installation.</span></span>  
  
 <span data-ttu-id="67a04-182">可以卸载部分安装而不影响已安装的其他 SQL Server 实例（或同一实例中的功能）。</span><span class="sxs-lookup"><span data-stu-id="67a04-182">You can uninstall part of an installation without impacting other SQL Server instances (or features in the same instance) that are already installed.</span></span> <span data-ttu-id="67a04-183">例如，可以卸载 PowerPivot for SharePoint 而保留安装的其他组件，例如 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 或数据库引擎。</span><span class="sxs-lookup"><span data-stu-id="67a04-183">For example, you can uninstall PowerPivot for SharePoint while leaving other components, such as [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] or the Database Engine, installed.</span></span>  
  
1.  <span data-ttu-id="67a04-184">从程序列表中选择“Microsoft SQL Server 2014 (64 位)”  。</span><span class="sxs-lookup"><span data-stu-id="67a04-184">Select **Microsoft SQL Server 2014 (64-bit)** from the program list.</span></span>  
  
2.  <span data-ttu-id="67a04-185">单击“卸载/更改”。 </span><span class="sxs-lookup"><span data-stu-id="67a04-185">Click **Uninstall/Change**.</span></span>  
  
3.  <span data-ttu-id="67a04-186">单击 **“删除”** 。</span><span class="sxs-lookup"><span data-stu-id="67a04-186">Click **Remove**.</span></span> <span data-ttu-id="67a04-187">这将启动 SQL Server 安装程序。</span><span class="sxs-lookup"><span data-stu-id="67a04-187">This starts SQL Server Setup.</span></span>  
  
     <span data-ttu-id="67a04-188">您可以从安装程序中选择 **PowerPivot** 实例，然后选择 **“Analysis Services”** 和 **“Analysis Services SharePoint 集成”** ，这样就可以只删除该功能，而保留其他功能。</span><span class="sxs-lookup"><span data-stu-id="67a04-188">From Setup, you can select the **PowerPivot** instance, and then select **Analysis Services** and **Analysis Services SharePoint Integration** to remove just that feature, leaving everything else in place.</span></span>  
  
##  <a name="step-4-uninstall-the-powerpivot-for-sharepoint-add-in"></a><a name="bkmk_addin"></a><span data-ttu-id="67a04-189">步骤4：卸载 PowerPivot for SharePoint 外接程序</span><span class="sxs-lookup"><span data-stu-id="67a04-189">Step 4: Uninstall the PowerPivot for SharePoint add-in</span></span>  
 <span data-ttu-id="67a04-190">如果您的 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 部署具有两个或更多服务器且您安装了 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 外接程序，则从安装它的每个服务器卸载 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 外接程序以完全卸载所有 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 文件。</span><span class="sxs-lookup"><span data-stu-id="67a04-190">If your [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] deployment has two or more servers and you installed the [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] Add-in, then uninstall the [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] add-in from each server where it was installed to completely uninstall all [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] files.</span></span> <span data-ttu-id="67a04-191">有关详细信息，请参阅[在 SharePoint 2013&#41;中安装或卸载 PowerPivot for SharePoint 外接程序 &#40;](https://docs.microsoft.com/analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013)。</span><span class="sxs-lookup"><span data-stu-id="67a04-191">For more information, see [Install or Uninstall the PowerPivot for SharePoint Add-in &#40;SharePoint 2013&#41;](https://docs.microsoft.com/analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013).</span></span>  
  
##  <a name="step-5-verify-uninstall"></a><a name="verify"></a> <span data-ttu-id="67a04-192">步骤 5：验证卸载情况</span><span class="sxs-lookup"><span data-stu-id="67a04-192">Step 5: Verify Uninstall</span></span>  
  
1.  <span data-ttu-id="67a04-193">在管理中心的 **“管理服务器上的服务”** 中，连接到卸载了 PowerPivot for SharePoint 的服务器。</span><span class="sxs-lookup"><span data-stu-id="67a04-193">In Central Administration, in **Manage services on server**, connect to the server from which you uninstalled PowerPivot for SharePoint.</span></span>  
  
2.  -   <span data-ttu-id="67a04-194">如果您卸载了 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2013，请验证 **“SQL Server PowerPivot 系统服务”** 不再显示在列表中。</span><span class="sxs-lookup"><span data-stu-id="67a04-194">If you uninstalled [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2013, verify that **SQL Server PowerPivot System Service** no longer appear in the list.</span></span>  
  
    -   <span data-ttu-id="67a04-195">如果卸载了 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2010，请验证 **SQL Server Analysis Services** 和 **“SQL Server PowerPivot 系统服务”** 不再显示在列表中。</span><span class="sxs-lookup"><span data-stu-id="67a04-195">If you uninstalled [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2010, verify that **SQL Server Analysis Services** and **SQL Server PowerPivot System Service** no longer appear in the list.</span></span>  
  
3.  <span data-ttu-id="67a04-196">卸载场中的最后一个 PowerPivot for SharePoint 服务器后，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="67a04-196">After you uninstall the last PowerPivot for SharePoint server in the farm, do the following:</span></span>  
  
    1.  <span data-ttu-id="67a04-197">在“应用程序管理”的 **“管理服务应用程序”** 中，验证“PowerPivot 服务应用程序”不再显示在列表中。</span><span class="sxs-lookup"><span data-stu-id="67a04-197">In Application Management, in **Manage service applications**, verify that PowerPivot Service Application no longer appears in the list.</span></span>  
  
    2.  <span data-ttu-id="67a04-198">在“系统设置”的 **“管理场功能”** 中，验证“PowerPivot 集成功能”不再出现在该页上。</span><span class="sxs-lookup"><span data-stu-id="67a04-198">In System Settings, in **Manage farm features**, verify that PowerPivot Integration Feature is no longer on the page.</span></span> <span data-ttu-id="67a04-199">在 **“管理场解决方案”** 中，验证 PowerPivot 解决方案不再出现在该页上。</span><span class="sxs-lookup"><span data-stu-id="67a04-199">In **Manage farm solutions**, verify that the PowerPivot solutions no longer appear on the page.</span></span>  
  
    3.  <span data-ttu-id="67a04-200">在“监视”的 **“配置诊断日志记录”** 和 **“配置使用情况和运行状况数据收集”** 中，验证 PowerPivot 事件和事件类别不再出现。</span><span class="sxs-lookup"><span data-stu-id="67a04-200">In Monitoring, in **Configure diagnostic logging** and in **Configure usage and health data collection**, verify that PowerPivot events and event categories no longer appear.</span></span>  
  
    4.  <span data-ttu-id="67a04-201">在“常规应用程序设置”中，验证 **“PowerPivot 管理面板”** 不再出现在该页上。</span><span class="sxs-lookup"><span data-stu-id="67a04-201">In General Application Settings, verify that **PowerPivot Management Dashboard** is no longer on the page.</span></span>  
  
##  <a name="step-6-post-uninstall-checklist"></a><a name="bkmk_post"></a> <span data-ttu-id="67a04-202">步骤 6：卸载后一览表</span><span class="sxs-lookup"><span data-stu-id="67a04-202">Step 6: Post-Uninstall Checklist</span></span>  
 <span data-ttu-id="67a04-203">使用下表删除在卸载过程中未删除的软件和文件。</span><span class="sxs-lookup"><span data-stu-id="67a04-203">Use the following list to remove software and files that were not deleted during uninstall.</span></span>  
  
1.  <span data-ttu-id="67a04-204">从 `C:\Program Files\Microsoft SQL Server\MSAS12.PowerPivot`删除所有数据文件和子文件夹，然后删除该文件夹。</span><span class="sxs-lookup"><span data-stu-id="67a04-204">Delete all data files and subfolders from `C:\Program Files\Microsoft SQL Server\MSAS12.PowerPivot`, and then delete the folder.</span></span> <span data-ttu-id="67a04-205">此步骤还将删除 DATA 目录中以前缓存的文件。</span><span class="sxs-lookup"><span data-stu-id="67a04-205">This step also deletes previously cached files in the DATA directory.</span></span>  
  
2.  <span data-ttu-id="67a04-206">如果您尚未执行，则删除所有 PowerPivot 工作簿、文档和库。</span><span class="sxs-lookup"><span data-stu-id="67a04-206">Delete all PowerPivot workbooks, documents, and libraries if you have not already done so.</span></span>  
  
    -   [<span data-ttu-id="67a04-207">删除 PowerPivot 库</span><span class="sxs-lookup"><span data-stu-id="67a04-207">Delete PowerPivot Gallery</span></span>](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/delete-power-pivot-gallery)  
  
    -   [<span data-ttu-id="67a04-208">删除 PowerPivot 数据馈送库</span><span class="sxs-lookup"><span data-stu-id="67a04-208">Delete a PowerPivot Data Feed Library</span></span>](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/delete-a-power-pivot-data-feed-library)  
  
3.  <span data-ttu-id="67a04-209">在 Secure Store Service 中，删除包含 PowerPivot for SharePoint 使用的存储凭据的所有目标应用程序。</span><span class="sxs-lookup"><span data-stu-id="67a04-209">In Secure Store Service, delete any target applications that contain stored credentials used by PowerPivot for SharePoint.</span></span> <span data-ttu-id="67a04-210">在您卸载 PowerPivot for SharePoint 时，Secure Store Service 中的某些条目（但不是全部条目）将会被删除。</span><span class="sxs-lookup"><span data-stu-id="67a04-210">Some, but not all, entries in Secure Store Service are deleted when you uninstall PowerPivot for SharePoint.</span></span> <span data-ttu-id="67a04-211">为 PowerPivot 无人参与的数据刷新帐户创建的目标应用程序以及您为数据刷新创建的所有目标应用程序仍将存在，因此必须手动删除。</span><span class="sxs-lookup"><span data-stu-id="67a04-211">Target applications created for the PowerPivot unattended data refresh account plus any target applications you created for data refresh still exist and must be deleted manually.</span></span>  
  
     <span data-ttu-id="67a04-212">相反，PowerPivot 系统服务自动生成的单独目标应用程序将在卸载 PowerPivot 时被自动删除。</span><span class="sxs-lookup"><span data-stu-id="67a04-212">In contrast, individual target applications that were auto-generated by the PowerPivot System Service are deleted automatically when PowerPivot is uninstalled.</span></span>  
  
4.  <span data-ttu-id="67a04-213">在控制面板中，单击 **“程序”** ，然后单击 **“卸载程序”**</span><span class="sxs-lookup"><span data-stu-id="67a04-213">In Control Panel, click **Programs**, and then click **Uninstall a program.**</span></span> <span data-ttu-id="67a04-214">。卸载不再使用的任何 Analysis Services 客户端库。</span><span class="sxs-lookup"><span data-stu-id="67a04-214">Uninstall any Analysis Services client libraries that are no longer used.</span></span> <span data-ttu-id="67a04-215">在您卸载 PowerPivot for SharePoint 时，将不删除 Analysis Services ADOMD.NET 和 Microsoft SQL Server Analysis Management Objects。</span><span class="sxs-lookup"><span data-stu-id="67a04-215">Analysis Services ADOMD.NET and Microsoft SQL Server Analysis Management Objects are not removed when you uninstall PowerPivot for SharePoint.</span></span> <span data-ttu-id="67a04-216">因为这些库可能由使用 Analysis Services 数据的其他程序使用，所以，SQL Server 安装程序将不会自动卸载它们。</span><span class="sxs-lookup"><span data-stu-id="67a04-216">Because the libraries might be used by other programs that use Analysis Services data, SQL Server Setup does not uninstall them automatically.</span></span> <span data-ttu-id="67a04-217">如果不再需要，您必须单独卸载这些客户端库。</span><span class="sxs-lookup"><span data-stu-id="67a04-217">You must uninstall these client libraries individually if you no longer need them.</span></span>  
  
     <span data-ttu-id="67a04-218">除非您在执行故障排除或者安装说明明确指示您进行卸载，否则，不要卸载 SQL Server Reporting Services SharePoint 2010 外接程序。</span><span class="sxs-lookup"><span data-stu-id="67a04-218">Do not uninstall the SQL Server Reporting Services SharePoint 2010 Add-in unless you are following troubleshooting or installation instructions that specifically direct you to uninstall it.</span></span> <span data-ttu-id="67a04-219">该 Reporting Services 外接程序由 Access Services 使用。</span><span class="sxs-lookup"><span data-stu-id="67a04-219">The Reporting Services Add-in is used by Access Services.</span></span> <span data-ttu-id="67a04-220">它是由 SharePoint 产品准备工具安装的，并且应保留在系统上以便支持 SharePoint 所需的功能。</span><span class="sxs-lookup"><span data-stu-id="67a04-220">It is installed by the SharePoint Products Preparation tool and should remain on the system to support functionality required by SharePoint.</span></span>  
  
     <span data-ttu-id="67a04-221">不要卸载 Analysis Services OLE DB 访问接口。</span><span class="sxs-lookup"><span data-stu-id="67a04-221">Do not uninstall the Analysis Services OLE DB provider.</span></span> <span data-ttu-id="67a04-222">SharePoint 将 OLE DB 访问接口作为连接到 Analysis Services 数据库的 Excel 工作簿的必备软件安装。</span><span class="sxs-lookup"><span data-stu-id="67a04-222">SharePoint installs the OLE DB provider as a prerequisite for Excel workbooks that connect to Analysis Services databases.</span></span> [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] <span data-ttu-id="67a04-223">将安装更新的版本，但此版本是可以向后兼容的，因此，您应该在系统上保留此版本以免以后出现数据连接问题。</span><span class="sxs-lookup"><span data-stu-id="67a04-223">installs a newer version, but this version is backwards compatible so you should leave it on the system to avoid data connection problems later.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67a04-224">另请参阅</span><span class="sxs-lookup"><span data-stu-id="67a04-224">See Also</span></span>  
 <span data-ttu-id="67a04-225">[在 SharePoint 2013 &#40;安装或卸载 PowerPivot for SharePoint 加载项&#41;](https://docs.microsoft.com/analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013) </span><span class="sxs-lookup"><span data-stu-id="67a04-225">[Install or Uninstall the PowerPivot for SharePoint Add-in &#40;SharePoint 2013&#41;](https://docs.microsoft.com/analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013) </span></span>  
 [<span data-ttu-id="67a04-226">PowerPivot Configuration Tools</span><span class="sxs-lookup"><span data-stu-id="67a04-226">PowerPivot Configuration Tools</span></span>](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/power-pivot-configuration-tools)  
