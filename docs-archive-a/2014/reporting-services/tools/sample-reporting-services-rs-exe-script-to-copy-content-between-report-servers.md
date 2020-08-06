---
title: 用于在报表服务器之间迁移内容的示例 Reporting Services rs.exe 脚本 |Microsoft Docs
ms.custom: ''
ms.date: 07/27/2015
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: d81bb03a-a89e-4fc1-a62b-886fb5338150
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9dece153485e4c683df42a04b9301cf3a47c869c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689272"
---
# <a name="sample-reporting-services-rsexe-script-to-migrate-content-between-report-servers"></a><span data-ttu-id="c2b39-102">用于在报表服务器之间迁移内容的示例 Reporting Services rs.exe 脚本</span><span class="sxs-lookup"><span data-stu-id="c2b39-102">Sample Reporting Services rs.exe Script to Migrate Content between Report Servers</span></span>
  <span data-ttu-id="c2b39-103">本主题包括并说明一个示例 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] RSS 脚本，该脚本使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] report server to another report server, using the **RS.exe** utility.</span><span class="sxs-lookup"><span data-stu-id="c2b39-103">This topic includes and describes a sample [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] RSS script that copies content items and settings from one [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] report server to another report server, using the **RS.exe** utility.</span></span> <span data-ttu-id="c2b39-104">本机模式和 SharePoint 模式下，RS.exe 都随 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]一起安装。</span><span class="sxs-lookup"><span data-stu-id="c2b39-104">RS.exe is installed with [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], both native and SharePoint mode.</span></span> <span data-ttu-id="c2b39-105">脚本将 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 项（例如，报表和订阅）从一个服务器复制到另一个服务器。</span><span class="sxs-lookup"><span data-stu-id="c2b39-105">The script copies [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] items, for example reports and subscriptions, from server to another server.</span></span> <span data-ttu-id="c2b39-106">该脚本支持 SharePoint 模式和本机模式报表服务器。</span><span class="sxs-lookup"><span data-stu-id="c2b39-106">The script supports both SharePoint mode and Native mode report servers.</span></span>  
  
||  
|-|  
|<span data-ttu-id="c2b39-107">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] SharePoint 模式 | [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 本机模式</span><span class="sxs-lookup"><span data-stu-id="c2b39-107">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] SharePoint mode &#124; [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] Native mode</span></span>|  
  
##  <a name="in-this-topic"></a><a name="bkmk_top"></a><span data-ttu-id="c2b39-108">本主题内容：</span><span class="sxs-lookup"><span data-stu-id="c2b39-108">In this Topic:</span></span>  
  
-   [<span data-ttu-id="c2b39-109">下载 ssrs_migration.rss 脚本</span><span class="sxs-lookup"><span data-stu-id="c2b39-109">To Download the ssrs_migration.rss Script</span></span>](#bkmk_download_script)  
  
-   [<span data-ttu-id="c2b39-110">支持的方案</span><span class="sxs-lookup"><span data-stu-id="c2b39-110">Supported Scenarios</span></span>](#bkmk_supported_scenarios)  
  
-   [<span data-ttu-id="c2b39-111">脚本迁移的项和资源</span><span class="sxs-lookup"><span data-stu-id="c2b39-111">Items and resources the script migrates</span></span>](#bkmk_what_is_migrated)  
  
-   [<span data-ttu-id="c2b39-112">所需的权限</span><span class="sxs-lookup"><span data-stu-id="c2b39-112">Required Permissions</span></span>](#bkmk_required_permissions)  
  
-   [<span data-ttu-id="c2b39-113">如何使用脚本</span><span class="sxs-lookup"><span data-stu-id="c2b39-113">How to use the script</span></span>](#bkmk_how_to_use_the_script)  
  
-   [<span data-ttu-id="c2b39-114">参数说明</span><span class="sxs-lookup"><span data-stu-id="c2b39-114">Parameter Description</span></span>](#bkmk_parameter_description)  
  
-   [<span data-ttu-id="c2b39-115">更多示例</span><span class="sxs-lookup"><span data-stu-id="c2b39-115">More Examples</span></span>](#bkmk_more_examples)  
  
    -   [<span data-ttu-id="c2b39-116">本机模式报表服务器到本机模式报表服务器</span><span class="sxs-lookup"><span data-stu-id="c2b39-116">Native Mode Report Server to Native Mode Report Server</span></span>](#bkmk_native_2_native)  
  
    -   [<span data-ttu-id="c2b39-117">本机模式到 SharePoint 模式-根站点</span><span class="sxs-lookup"><span data-stu-id="c2b39-117">Native Mode to SharePoint Mode - root site</span></span>](#bkmk_native_2_sharepoint_root)  
  
    -   [<span data-ttu-id="c2b39-118">本机模式到 SharePoint 模式-"bi" 网站集</span><span class="sxs-lookup"><span data-stu-id="c2b39-118">Native mode to SharePoint Mode -'bi' site collection</span></span>](#bkmk_native_2_sharepoint_with_site)  
  
    -   [<span data-ttu-id="c2b39-119">SharePoint 模式到 SharePoint 模式-"bi" 网站集</span><span class="sxs-lookup"><span data-stu-id="c2b39-119">SharePoint Mode to SharePoint Mode -'bi' site collection</span></span>](#bkmk_sharepoint_2_sharepoint)  
  
    -   [<span data-ttu-id="c2b39-120">本机模式到本机模式-Azure 虚拟机</span><span class="sxs-lookup"><span data-stu-id="c2b39-120">Native Mode to Native Mode - Azure Virtual Machine</span></span>](#bkmk_native_to_native_Azure_vm)  
  
    -   [<span data-ttu-id="c2b39-121">SharePoint 模式-Azure 虚拟机上的本机模式服务器的 "bi" 网站集</span><span class="sxs-lookup"><span data-stu-id="c2b39-121">SharePoint Mode -'bi' site collection to a Native Mode Server on Azure Virtual Machine</span></span>](#bkmk_sharepoint_site_to_native_Azure_vm)  
  
-   [<span data-ttu-id="c2b39-122">验证</span><span class="sxs-lookup"><span data-stu-id="c2b39-122">Verification</span></span>](#bkmk_verification)  
  
-   [<span data-ttu-id="c2b39-123">疑难解答</span><span class="sxs-lookup"><span data-stu-id="c2b39-123">Troubleshooting</span></span>](#bkmk_troubleshoot)  
  
##  <a name="to-download-the-ssrs_migrationrss-script"></a><a name="bkmk_download_script"></a><span data-ttu-id="c2b39-124">下载 ssrs_migration rss 脚本</span><span class="sxs-lookup"><span data-stu-id="c2b39-124">To Download the ssrs_migration.rss Script</span></span>  
 <span data-ttu-id="c2b39-125">从 CodePlex 站点 [Reporting Services RS.exe 脚本迁移内容](https://azuresql.codeplex.com/releases/view/115207) 将脚本下载到本地文件夹。</span><span class="sxs-lookup"><span data-stu-id="c2b39-125">Download the script from the CodePlex site [Reporting Services RS.exe script migrates content](https://azuresql.codeplex.com/releases/view/115207) to a local folder.</span></span> <span data-ttu-id="c2b39-126">有关详细信息，请参阅本主题中的 [如何使用该脚本](#bkmk_how_to_use_the_script) 部分。</span><span class="sxs-lookup"><span data-stu-id="c2b39-126">See the section [How to use the script](#bkmk_how_to_use_the_script) in this topic for more information.</span></span>  
  
##  <a name="supported-scenarios"></a><a name="bkmk_supported_scenarios"></a><span data-ttu-id="c2b39-127">支持的方案</span><span class="sxs-lookup"><span data-stu-id="c2b39-127">Supported Scenarios</span></span>  
 <span data-ttu-id="c2b39-128">该脚本支持 SharePoint 模式和本机模式报表服务器。</span><span class="sxs-lookup"><span data-stu-id="c2b39-128">The script supports both SharePoint mode and Native mode report servers.</span></span> <span data-ttu-id="c2b39-129">该脚本支持以下报表服务器版本：</span><span class="sxs-lookup"><span data-stu-id="c2b39-129">The script supports the following report server versions:</span></span>  
  
-   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]  
  
-   [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]  
  
-   [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)]  
  
 <span data-ttu-id="c2b39-130">该脚本可用于在相同模式或不同模式的报表服务器之间复制内容。</span><span class="sxs-lookup"><span data-stu-id="c2b39-130">The script can be used to copy content between report servers of the same mode or different modes.</span></span> <span data-ttu-id="c2b39-131">例如，可以运行该脚本以便将 [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] 本机模式报表服务器的内容复制到 [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] SharePoint 模式报表服务器。</span><span class="sxs-lookup"><span data-stu-id="c2b39-131">For example, you can run the script to copy content from a [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] native mode report server to a [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] SharePoint mode report server.</span></span> <span data-ttu-id="c2b39-132">可以从安装了 RS.exe 的任何服务器运行该脚本。</span><span class="sxs-lookup"><span data-stu-id="c2b39-132">You can run the script from any server where RS.exe is installed.</span></span> <span data-ttu-id="c2b39-133">例如，在以下部署中，您可以：</span><span class="sxs-lookup"><span data-stu-id="c2b39-133">For example, in the following deployment, you can:</span></span>  
  
-   <span data-ttu-id="c2b39-134">在服务器 A **上** 运行 RS.exe 和脚本。</span><span class="sxs-lookup"><span data-stu-id="c2b39-134">Run RS.exe and the script **ON** Server A.</span></span>  
  
-   <span data-ttu-id="c2b39-135">将内容从 \*\*\*\* 服务器 B</span><span class="sxs-lookup"><span data-stu-id="c2b39-135">To copy content **FROM** Server B</span></span>  
  
-   <span data-ttu-id="c2b39-136">复制到\*\*\*\* 服务器 C</span><span class="sxs-lookup"><span data-stu-id="c2b39-136">**TO** Server C</span></span>  
  
|<span data-ttu-id="c2b39-137">服务器名称</span><span class="sxs-lookup"><span data-stu-id="c2b39-137">Server name</span></span>|<span data-ttu-id="c2b39-138">报表服务器模式</span><span class="sxs-lookup"><span data-stu-id="c2b39-138">Report Server Mode</span></span>|  
|-----------------|------------------------|  
|<span data-ttu-id="c2b39-139">服务器 A</span><span class="sxs-lookup"><span data-stu-id="c2b39-139">Server A</span></span>|<span data-ttu-id="c2b39-140">本机</span><span class="sxs-lookup"><span data-stu-id="c2b39-140">Native</span></span>|  
|<span data-ttu-id="c2b39-141">服务器 B</span><span class="sxs-lookup"><span data-stu-id="c2b39-141">Server B</span></span>|<span data-ttu-id="c2b39-142">SharePoint</span><span class="sxs-lookup"><span data-stu-id="c2b39-142">SharePoint</span></span>|  
|<span data-ttu-id="c2b39-143">服务器 C</span><span class="sxs-lookup"><span data-stu-id="c2b39-143">Server C</span></span>|<span data-ttu-id="c2b39-144">SharePoint</span><span class="sxs-lookup"><span data-stu-id="c2b39-144">SharePoint</span></span>|  
  
 <span data-ttu-id="c2b39-145">有关使用 RS.exe 实用工具的详细信息，请参阅 [RS.exe 实用工具 (SSRS)](rs-exe-utility-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="c2b39-145">For more information on the RS.exe utility, see [RS.exe Utility &#40;SSRS&#41;](rs-exe-utility-ssrs.md).</span></span>  
  
###  <a name="items-and-resources-the-script-migrates"></a><a name="bkmk_what_is_migrated"></a><span data-ttu-id="c2b39-146">脚本迁移的项和资源</span><span class="sxs-lookup"><span data-stu-id="c2b39-146">Items and resources the script migrates</span></span>  
 <span data-ttu-id="c2b39-147">该脚本将不会覆盖同名的现有内容项。</span><span class="sxs-lookup"><span data-stu-id="c2b39-147">The script will not write over existing content items of the same name.</span></span>  <span data-ttu-id="c2b39-148">如果该脚本在目标服务器上检测到名称与源服务器上相同的项，则这些单独的项将导致“失败”消息，但该脚本将继续运行。</span><span class="sxs-lookup"><span data-stu-id="c2b39-148">If the script detects items with the same name on the destination server that are on the source server, the individual items will result in a "failure" message and the script will continue.</span></span> <span data-ttu-id="c2b39-149">下表列出该脚本可迁移到目标报表服务器模式的内容和资源的类型。</span><span class="sxs-lookup"><span data-stu-id="c2b39-149">The following table lists the types of content and resources the script can migrate to target report server modes.</span></span>  
  
|<span data-ttu-id="c2b39-150">项</span><span class="sxs-lookup"><span data-stu-id="c2b39-150">Item</span></span>|<span data-ttu-id="c2b39-151">是否迁移</span><span class="sxs-lookup"><span data-stu-id="c2b39-151">Migrated</span></span>|<span data-ttu-id="c2b39-152">SharePoint</span><span class="sxs-lookup"><span data-stu-id="c2b39-152">SharePoint</span></span>|<span data-ttu-id="c2b39-153">说明</span><span class="sxs-lookup"><span data-stu-id="c2b39-153">Description</span></span>|  
|----------|--------------|----------------|-----------------|  
|<span data-ttu-id="c2b39-154">密码</span><span class="sxs-lookup"><span data-stu-id="c2b39-154">Passwords</span></span>|<span data-ttu-id="c2b39-155">**否**</span><span class="sxs-lookup"><span data-stu-id="c2b39-155">**No**</span></span>|<span data-ttu-id="c2b39-156">**否**</span><span class="sxs-lookup"><span data-stu-id="c2b39-156">**No**</span></span>|<span data-ttu-id="c2b39-157">**不** 迁移密码。</span><span class="sxs-lookup"><span data-stu-id="c2b39-157">Passwords are **NOT** migrated.</span></span> <span data-ttu-id="c2b39-158">在迁移内容项后，在目标服务器上更新凭据信息。</span><span class="sxs-lookup"><span data-stu-id="c2b39-158">After content items are migrated, update the credential information on the destination server.</span></span> <span data-ttu-id="c2b39-159">例如，具有已存储凭据的数据源。</span><span class="sxs-lookup"><span data-stu-id="c2b39-159">For example, data sources with stored credentials.</span></span>|  
|<span data-ttu-id="c2b39-160">我的报表</span><span class="sxs-lookup"><span data-stu-id="c2b39-160">My Reports</span></span>|<span data-ttu-id="c2b39-161">**否**</span><span class="sxs-lookup"><span data-stu-id="c2b39-161">**No**</span></span>|<span data-ttu-id="c2b39-162">**是**</span><span class="sxs-lookup"><span data-stu-id="c2b39-162">**No**</span></span>|<span data-ttu-id="c2b39-163">本机模式 "我的报表" 功能基于单个用户登录名，因此，脚本服务无法访问用于运行 rss 脚本的 **-u**参数以外的用户的 "我的报表" 文件夹中的内容。</span><span class="sxs-lookup"><span data-stu-id="c2b39-163">The Native mode "My Reports" feature is based on individual user logins therefore the scripting service does not have access to content in "My Reports" folders for users other than the **-u** parameter used to run the rss script.</span></span> <span data-ttu-id="c2b39-164">此外，"我的报表" 不是 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] sharepoint 模式的一项功能，文件夹中的项不能复制到 sharepoint 环境。</span><span class="sxs-lookup"><span data-stu-id="c2b39-164">Also, "My Reports" is not a feature of [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] SharePoint mode and items in the folders cannot be copied to a SharePoint environment.</span></span> <span data-ttu-id="c2b39-165">因此，此脚本不会复制源本机模式 Report Server 上 "我的报表" 文件夹中的报表项。</span><span class="sxs-lookup"><span data-stu-id="c2b39-165">Therefore, the script does not copy report items that are in the "My Reports" folders on a source native mode report server.</span></span> <span data-ttu-id="c2b39-166">若要通过此脚本迁移 "我的报表" 文件夹中的内容，请完成以下操作：</span><span class="sxs-lookup"><span data-stu-id="c2b39-166">To migrate the content in "My Reports" folders with this script, complete the following:</span></span><br /><br /> <span data-ttu-id="c2b39-167">1) 在报表管理器中创建 (s) 的新文件夹。</span><span class="sxs-lookup"><span data-stu-id="c2b39-167">1) Create new folder(s) in Report Manager.</span></span> <span data-ttu-id="c2b39-168">或者，您可为每个用户创建文件夹或子文件夹。</span><span class="sxs-lookup"><span data-stu-id="c2b39-168">Optionally, you can create folders or subfolder for each user.</span></span><br /><br /> <span data-ttu-id="c2b39-169">2) 以 "我的报表" 内容的用户身份登录。</span><span class="sxs-lookup"><span data-stu-id="c2b39-169">2) Login as one of the users with "My Reports" content.</span></span><br /><br /> <span data-ttu-id="c2b39-170">3) 在报表管理器中，单击**我的报表**文件夹。</span><span class="sxs-lookup"><span data-stu-id="c2b39-170">3) In Report Manager, click the **My Reports** folder.</span></span><br /><br /> <span data-ttu-id="c2b39-171">4) 单击该文件夹的**详细信息**视图。</span><span class="sxs-lookup"><span data-stu-id="c2b39-171">4) Click the **Details** view for the folder.</span></span><br /><br /> <span data-ttu-id="c2b39-172">5) 选择要复制的每个报表。</span><span class="sxs-lookup"><span data-stu-id="c2b39-172">5) Select each report that you want to copy.</span></span><br /><br /> <span data-ttu-id="c2b39-173">6) 单击报表管理器工具栏中的 "**移动**"。</span><span class="sxs-lookup"><span data-stu-id="c2b39-173">6) Click **Move** in the Report Manager toolbar.</span></span><br /><br /> <span data-ttu-id="c2b39-174">7) 选择所需的目标文件夹。</span><span class="sxs-lookup"><span data-stu-id="c2b39-174">7) Select the desired destination folder.</span></span><br /><br /> <span data-ttu-id="c2b39-175">8) 为每个用户重复步骤2-7。</span><span class="sxs-lookup"><span data-stu-id="c2b39-175">8) Repeat steps 2-7 for each user.</span></span><br /><br /> <span data-ttu-id="c2b39-176">9) 运行脚本。</span><span class="sxs-lookup"><span data-stu-id="c2b39-176">9) Run the script.</span></span>|  
|<span data-ttu-id="c2b39-177">历史记录</span><span class="sxs-lookup"><span data-stu-id="c2b39-177">History</span></span>|<span data-ttu-id="c2b39-178">**否**</span><span class="sxs-lookup"><span data-stu-id="c2b39-178">**No**</span></span>|<span data-ttu-id="c2b39-179">**否**</span><span class="sxs-lookup"><span data-stu-id="c2b39-179">**No**</span></span>||  
|<span data-ttu-id="c2b39-180">历史记录设置</span><span class="sxs-lookup"><span data-stu-id="c2b39-180">History settings</span></span>|<span data-ttu-id="c2b39-181">是</span><span class="sxs-lookup"><span data-stu-id="c2b39-181">Yes</span></span>|<span data-ttu-id="c2b39-182">是</span><span class="sxs-lookup"><span data-stu-id="c2b39-182">Yes</span></span>|<span data-ttu-id="c2b39-183">将迁移历史记录设置，但不迁移历史记录详细信息。</span><span class="sxs-lookup"><span data-stu-id="c2b39-183">The history settings are migrated however the history details are NOT migrated.</span></span>|  
|<span data-ttu-id="c2b39-184">计划</span><span class="sxs-lookup"><span data-stu-id="c2b39-184">Schedules</span></span>|<span data-ttu-id="c2b39-185">是</span><span class="sxs-lookup"><span data-stu-id="c2b39-185">yes</span></span>|<span data-ttu-id="c2b39-186">是</span><span class="sxs-lookup"><span data-stu-id="c2b39-186">yes</span></span>|<span data-ttu-id="c2b39-187">若要迁移计划，在目标服务器上需运行 SQL Server 代理。</span><span class="sxs-lookup"><span data-stu-id="c2b39-187">To migrate schedules, it is required that SQL Server Agent is running on the target server.</span></span> <span data-ttu-id="c2b39-188">如果在目标服务器上未运行 SQL Server 代理，将会显示如下错误消息：</span><span class="sxs-lookup"><span data-stu-id="c2b39-188">If SQL Server Agent is not running on the target, you will see an error message similar to the following:</span></span><br /><br /> `Migrating schedules: 1 items found. Migrating schedule: theMondaySchedule ... FAILURE:  The SQL Agent service is not running. This operation requires the SQL Agent service. ---> Microsoft.ReportingServices.Diagnostics.Utilities.SchedulerNotResponding Exception: The SQL Agent service is not running. This operation requires the SQL Agent service.`|  
|<span data-ttu-id="c2b39-189">角色和系统策略</span><span class="sxs-lookup"><span data-stu-id="c2b39-189">Roles and system policies</span></span>|<span data-ttu-id="c2b39-190">是</span><span class="sxs-lookup"><span data-stu-id="c2b39-190">Yes</span></span>|<span data-ttu-id="c2b39-191">是</span><span class="sxs-lookup"><span data-stu-id="c2b39-191">Yes</span></span>|<span data-ttu-id="c2b39-192">默认情况下，该脚本不会在服务器之间复制自定义权限架构。</span><span class="sxs-lookup"><span data-stu-id="c2b39-192">By default the script will not copy custom permission schema between servers.</span></span> <span data-ttu-id="c2b39-193">默认行为是将 "inherit parent 权限" 标志设置为 TRUE 的项将复制目标服务器。</span><span class="sxs-lookup"><span data-stu-id="c2b39-193">The default behavior is the items will be coied to the destination server with the 'inherit parent permissions' flag set to TRUE.</span></span> <span data-ttu-id="c2b39-194">如果您希望该脚本复制单独项的权限，请使用 SECURITY 开关。</span><span class="sxs-lookup"><span data-stu-id="c2b39-194">If you want the script to copy permissions for individual items, use the SECURITY switch.</span></span><br /><br /> <span data-ttu-id="c2b39-195">如果源服务器和目标服务器 **未处于相同报表服务器模式下**，例如从本机模式到 SharePoint 模式，并且您使用 SECURITY 开关，则该脚本将尝试基于比较（请参阅主题 [Reporting Services 中的角色和任务与 SharePoint 组和权限的比较](../reporting-services-roles-tasks-vs-sharepoint-groups-permissions.md)）映射默认角色和组。</span><span class="sxs-lookup"><span data-stu-id="c2b39-195">If the source and target servers are **not the same report server mode**, for example from native mode to SharePoint mode, and you use the SECURITY switch, the script will attempt to map default roles and groups based on the comparison in the following topic [Compare Roles and Tasks in Reporting Services to SharePoint Groups and Permissions](../reporting-services-roles-tasks-vs-sharepoint-groups-permissions.md).</span></span> <span data-ttu-id="c2b39-196">自定义角色和组不复制到目标服务器。</span><span class="sxs-lookup"><span data-stu-id="c2b39-196">Custom roles and groups are not copied to the destination server.</span></span><br /><br /> <span data-ttu-id="c2b39-197">在 **处于相同模式下**的服务器之间复制脚本并且使用 SECURITY 开关时，该脚本将在目标服务器上创建新角色（本机模式）或组（SharePoint 模式）。</span><span class="sxs-lookup"><span data-stu-id="c2b39-197">When the script is copying between servers **that are the same mode**, and you use the SECURITY switch, the script will create new roles (native mode) or groups (SharePoint mode) on the destination server.</span></span><br /><br /> <span data-ttu-id="c2b39-198">如果某一角色已在目标服务器上存在，该脚本将创建如下“失败”消息，并且继续迁移其他项。</span><span class="sxs-lookup"><span data-stu-id="c2b39-198">If a role already exists on the destination server, the script will create a "Failure" message similar to the following, and continue migrating other items.</span></span> <span data-ttu-id="c2b39-199">在该脚本运行完毕之后，请验证目标服务器上的角色已配置为满足您的需要。</span><span class="sxs-lookup"><span data-stu-id="c2b39-199">After the script completes, verify the roles on the destination server are configured to meet your needs.</span></span> <span data-ttu-id="c2b39-200">迁移角色：找到了 8 项。</span><span class="sxs-lookup"><span data-stu-id="c2b39-200">the Migrating roles: 8 items found.</span></span><br /><br /> `Migrating role: Browser ... FAILURE: The role 'Browser' already exists and cannot be created. ---> Microsoft.ReportingServices.Diagnostics.Utilities.RoleAlreadyExistsException: The role 'Browser' already exists and cannot be created.`<br /><br /> <span data-ttu-id="c2b39-201">有关详细信息，请参阅[授予用户对报表服务器的访问权限 &#40;报表管理器&#41;](../security/grant-user-access-to-a-report-server.md)</span><span class="sxs-lookup"><span data-stu-id="c2b39-201">For more information, see [Grant User Access to a Report Server &#40;Report Manager&#41;](../security/grant-user-access-to-a-report-server.md)</span></span><br /><br /> <span data-ttu-id="c2b39-202">**注意：** 如果某一用户在源服务器上存在，但在目标服务器上不存在，则该脚本无法在目标服务器上应用角色分配，即使使用了 SECURITY 开关，该脚本也无法应用角色分配。</span><span class="sxs-lookup"><span data-stu-id="c2b39-202">**Note:** if a user that exists on the source server does not exist on the destination server, the script cannot apply role assignments on the destination server, the script cannot apply role assignments, even if the SECURITY switch is used.</span></span>|  
|<span data-ttu-id="c2b39-203">共享数据源</span><span class="sxs-lookup"><span data-stu-id="c2b39-203">Shared data source</span></span>|<span data-ttu-id="c2b39-204">是</span><span class="sxs-lookup"><span data-stu-id="c2b39-204">Yes</span></span>|<span data-ttu-id="c2b39-205">是</span><span class="sxs-lookup"><span data-stu-id="c2b39-205">Yes</span></span>|<span data-ttu-id="c2b39-206">该脚本将不覆盖目标服务器上的现有项。</span><span class="sxs-lookup"><span data-stu-id="c2b39-206">The script will not overwrite existing items on the target server.</span></span> <span data-ttu-id="c2b39-207">如果目标服务器上已存在同名的项，将显示如下错误消息：</span><span class="sxs-lookup"><span data-stu-id="c2b39-207">If an item on the target server already exists with the same name, you will see an error message similar to the following:</span></span><br /><br /> `Migrating DataSource: /Data Sources/Aworks2012_oltp ... FAILURE:The item '/Data Sources/Aworks2012_oltp' already exists. ---> Microsoft.ReportingServices.Diagnostics.Utilities.ItemAlreadyExistsException: The item '/Data Source s/Aworks2012_oltp' already exists.`<br /><br /> <span data-ttu-id="c2b39-208">凭据 **不** 作为数据源的一部分被复制。</span><span class="sxs-lookup"><span data-stu-id="c2b39-208">Credentials are **NOT** copied over as part of the data source.</span></span> <span data-ttu-id="c2b39-209">在迁移内容项后，在目标服务器上更新凭据信息。</span><span class="sxs-lookup"><span data-stu-id="c2b39-209">After content items are migrated, update the credential information on the destination server.</span></span>|  
|<span data-ttu-id="c2b39-210">共享数据集</span><span class="sxs-lookup"><span data-stu-id="c2b39-210">Shared dataset</span></span>|<span data-ttu-id="c2b39-211">是</span><span class="sxs-lookup"><span data-stu-id="c2b39-211">Yes</span></span>|<span data-ttu-id="c2b39-212">是</span><span class="sxs-lookup"><span data-stu-id="c2b39-212">Yes</span></span>||  
|<span data-ttu-id="c2b39-213">Folder</span><span class="sxs-lookup"><span data-stu-id="c2b39-213">Folder</span></span>|<span data-ttu-id="c2b39-214">是</span><span class="sxs-lookup"><span data-stu-id="c2b39-214">Yes</span></span>|<span data-ttu-id="c2b39-215">是</span><span class="sxs-lookup"><span data-stu-id="c2b39-215">Yes</span></span>|<span data-ttu-id="c2b39-216">该脚本将不覆盖目标服务器上的现有项。</span><span class="sxs-lookup"><span data-stu-id="c2b39-216">The script will not overwrite existing items on the target server.</span></span> <span data-ttu-id="c2b39-217">如果目标服务器上已存在同名的项，将显示如下错误消息：</span><span class="sxs-lookup"><span data-stu-id="c2b39-217">If an item on the target server already exists with the same name, you will see an error message similar to the following:</span></span><br /><br /> `Migrating Folder: /Reports ... FAILURE: The item '/Reports' already exists. ---> Microsoft.ReportingServices.Diagnostics.Utilities.ItemAlreadyExistsException: The item '/Reports' already exists.`|  
|<span data-ttu-id="c2b39-218">报表</span><span class="sxs-lookup"><span data-stu-id="c2b39-218">Report</span></span>|<span data-ttu-id="c2b39-219">是</span><span class="sxs-lookup"><span data-stu-id="c2b39-219">Yes</span></span>|<span data-ttu-id="c2b39-220">是</span><span class="sxs-lookup"><span data-stu-id="c2b39-220">Yes</span></span>|<span data-ttu-id="c2b39-221">该脚本将不覆盖目标服务器上的现有项。</span><span class="sxs-lookup"><span data-stu-id="c2b39-221">The script will not overwrite existing items on the target server.</span></span> <span data-ttu-id="c2b39-222">如果目标服务器上已存在同名的项，将显示如下错误消息：</span><span class="sxs-lookup"><span data-stu-id="c2b39-222">If an item on the target server already exists with the same name, you will see an error message similar to the following:</span></span><br /><br /> `Migrating Report: /Reports/testThe item '/Reports/test' already exists. ---> Microsoft.ReportingServices.Diagnostics.Utilities.ItemAlreadyExistsException: The item '/Reports/test' already exists.`|  
|<span data-ttu-id="c2b39-223">参数</span><span class="sxs-lookup"><span data-stu-id="c2b39-223">Parameters</span></span>|<span data-ttu-id="c2b39-224">是</span><span class="sxs-lookup"><span data-stu-id="c2b39-224">Yes</span></span>|<span data-ttu-id="c2b39-225">是</span><span class="sxs-lookup"><span data-stu-id="c2b39-225">Yes</span></span>||  
|<span data-ttu-id="c2b39-226">订阅</span><span class="sxs-lookup"><span data-stu-id="c2b39-226">Subscriptions</span></span>|<span data-ttu-id="c2b39-227">是</span><span class="sxs-lookup"><span data-stu-id="c2b39-227">Yes</span></span>|<span data-ttu-id="c2b39-228">是</span><span class="sxs-lookup"><span data-stu-id="c2b39-228">Yes</span></span>||  
|<span data-ttu-id="c2b39-229">历史记录设置</span><span class="sxs-lookup"><span data-stu-id="c2b39-229">History Settings</span></span>|<span data-ttu-id="c2b39-230">是</span><span class="sxs-lookup"><span data-stu-id="c2b39-230">Yes</span></span>|<span data-ttu-id="c2b39-231">是</span><span class="sxs-lookup"><span data-stu-id="c2b39-231">Yes</span></span>|<span data-ttu-id="c2b39-232">将迁移历史记录设置，但不迁移历史记录详细信息。</span><span class="sxs-lookup"><span data-stu-id="c2b39-232">The history settings are migrated however the history details are NOT migrated.</span></span>|  
|<span data-ttu-id="c2b39-233">处理选项</span><span class="sxs-lookup"><span data-stu-id="c2b39-233">processing options</span></span>|<span data-ttu-id="c2b39-234">是</span><span class="sxs-lookup"><span data-stu-id="c2b39-234">Yes</span></span>|<span data-ttu-id="c2b39-235">是</span><span class="sxs-lookup"><span data-stu-id="c2b39-235">Yes</span></span>||  
|<span data-ttu-id="c2b39-236">高速缓存刷新选项</span><span class="sxs-lookup"><span data-stu-id="c2b39-236">cache refresh options</span></span>|<span data-ttu-id="c2b39-237">是</span><span class="sxs-lookup"><span data-stu-id="c2b39-237">Yes</span></span>|<span data-ttu-id="c2b39-238">是</span><span class="sxs-lookup"><span data-stu-id="c2b39-238">Yes</span></span>|<span data-ttu-id="c2b39-239">相关设置作为目录项的一部分迁移。</span><span class="sxs-lookup"><span data-stu-id="c2b39-239">Dependent settings are migrated as part of a catalog item.</span></span> <span data-ttu-id="c2b39-240">下面是该脚本的示例，它迁移报表 (.rdl) 以及高速缓存刷新选项之类的相关设置：</span><span class="sxs-lookup"><span data-stu-id="c2b39-240">The following is the sample out of the script as it migrates a report (.rdl) and related settings such as cache refresh options:</span></span><br /><br /> <span data-ttu-id="c2b39-241">正在迁移报表 TitleOnly.rdl 的参数: 找到了 0 项。</span><span class="sxs-lookup"><span data-stu-id="c2b39-241">Migrating parameters for report TitleOnly.rdl 0 items found.</span></span><br /><br /> <span data-ttu-id="c2b39-242">正在迁移报表 TitleOnly.rdl 的订阅:找到 1 项。</span><span class="sxs-lookup"><span data-stu-id="c2b39-242">Migrating subscriptions for report TitleOnly.rdl: 1 items found.</span></span><br /><br /> <span data-ttu-id="c2b39-243">正在迁移作为 \server\public\savedreports 中的订阅保存 \\ 为 titleonly.rdl .。。辉煌</span><span class="sxs-lookup"><span data-stu-id="c2b39-243">Migrating subscription Save in \\\server\public\savedreports as TitleOnly ... SUCCESS</span></span><br /><br /> <span data-ttu-id="c2b39-244">正在迁移报表 TitleOnly.rdl 的历史记录设置...成功</span><span class="sxs-lookup"><span data-stu-id="c2b39-244">Migrating history settings for report TitleOnly.rdl ... SUCCESS</span></span><br /><br /> <span data-ttu-id="c2b39-245">正在迁移报表 TitleOnly.rdl 的处理选项...找到 0 项。</span><span class="sxs-lookup"><span data-stu-id="c2b39-245">Migrating processing options for report TitleOnly.rdl ... 0 items found.</span></span><br /><br /> <span data-ttu-id="c2b39-246">正在迁移报表 TitleOnly.rdl 的高速缓存刷新选项...成功</span><span class="sxs-lookup"><span data-stu-id="c2b39-246">Migrating cache refresh options for report TitleOnly.rdl ... SUCCESS</span></span><br /><br /> <span data-ttu-id="c2b39-247">正在迁移报表 TitleOnly.rdl 的高速缓存刷新计划:找到 1 项。</span><span class="sxs-lookup"><span data-stu-id="c2b39-247">Migrating cache refresh plans for report TitleOnly.rdl: 1 items found.</span></span><br /><br /> <span data-ttu-id="c2b39-248">正在迁移高速缓存刷新计划 titleonly_refresh735amM2F...成功</span><span class="sxs-lookup"><span data-stu-id="c2b39-248">Migrating cache refresh plan titleonly_refresh735amM2F ... SUCCESS</span></span>|  
|<span data-ttu-id="c2b39-249">高速缓存刷新计划</span><span class="sxs-lookup"><span data-stu-id="c2b39-249">Cache refresh plans</span></span>|<span data-ttu-id="c2b39-250">是</span><span class="sxs-lookup"><span data-stu-id="c2b39-250">Yes</span></span>|<span data-ttu-id="c2b39-251">是</span><span class="sxs-lookup"><span data-stu-id="c2b39-251">Yes</span></span>||  
|<span data-ttu-id="c2b39-252">映像</span><span class="sxs-lookup"><span data-stu-id="c2b39-252">Images</span></span>|<span data-ttu-id="c2b39-253">是</span><span class="sxs-lookup"><span data-stu-id="c2b39-253">Yes</span></span>|<span data-ttu-id="c2b39-254">是</span><span class="sxs-lookup"><span data-stu-id="c2b39-254">Yes</span></span>||  
|<span data-ttu-id="c2b39-255">报表部件</span><span class="sxs-lookup"><span data-stu-id="c2b39-255">Report parts</span></span>|<span data-ttu-id="c2b39-256">是</span><span class="sxs-lookup"><span data-stu-id="c2b39-256">Yes</span></span>|<span data-ttu-id="c2b39-257">是</span><span class="sxs-lookup"><span data-stu-id="c2b39-257">Yes</span></span>||  
  
##  <a name="required-permissions"></a><a name="bkmk_required_permissions"></a> <span data-ttu-id="c2b39-258">所需的权限</span><span class="sxs-lookup"><span data-stu-id="c2b39-258">Required Permissions</span></span>  
 <span data-ttu-id="c2b39-259">读取或写入项和资源的权限并不是对于在该脚本中使用的所有方法全都相同。</span><span class="sxs-lookup"><span data-stu-id="c2b39-259">The permissions required to read or write items and resources is not the same for all of the methods used in the script.</span></span> <span data-ttu-id="c2b39-260">下表总结了用于每一项或资源的方法以及相关内容的链接。</span><span class="sxs-lookup"><span data-stu-id="c2b39-260">The following table summarizes the methods used for each item or resource and links to related content.</span></span> <span data-ttu-id="c2b39-261">导航到单独的主题可看到所需权限。</span><span class="sxs-lookup"><span data-stu-id="c2b39-261">Navigate to the individual topic to see the required permissions.</span></span> <span data-ttu-id="c2b39-262">例如，ListChildren 方法主题记录了以下所需权限：</span><span class="sxs-lookup"><span data-stu-id="c2b39-262">For example the ListChildren method topic notes the required permissions of:</span></span>  
  
-   <span data-ttu-id="c2b39-263">**本机模式所需的权限：** 对项的 ReadProperties</span><span class="sxs-lookup"><span data-stu-id="c2b39-263">**Native Mode Required Permissions:** ReadProperties on Item</span></span>  
  
-   <span data-ttu-id="c2b39-264">**SharePoint 模式所需的权限：** ViewListItems</span><span class="sxs-lookup"><span data-stu-id="c2b39-264">**SharePoint Mode Required Permissions:** ViewListItems</span></span>  
  
|<span data-ttu-id="c2b39-265">项或资源</span><span class="sxs-lookup"><span data-stu-id="c2b39-265">Item or Resource</span></span>|<span data-ttu-id="c2b39-266">Source</span><span class="sxs-lookup"><span data-stu-id="c2b39-266">Source</span></span>|<span data-ttu-id="c2b39-267">目标</span><span class="sxs-lookup"><span data-stu-id="c2b39-267">Target</span></span>|  
|----------------------|------------|------------|  
|<span data-ttu-id="c2b39-268">目录项</span><span class="sxs-lookup"><span data-stu-id="c2b39-268">Catalog items</span></span>|<xref:ReportService2010.ReportingService2010.ListChildren%2A><br /><br /> <xref:ReportService2010.ReportingService2010.GetProperties%2A><br /><br /> <xref:ReportService2010.ReportingService2010.GetItemDataSources%2A><br /><br /> <xref:ReportService2010.ReportingService2010.GetItemReferences%2A><br /><br /> <xref:ReportService2010.ReportingService2010.GetDataSourceContents%2A><br /><br /> <xref:ReportService2010.ReportingService2010.GetItemLink%2A>|<xref:ReportService2010.ReportingService2010.CreateCatalogItem%2A><br /><br /> <xref:ReportService2010.ReportingService2010.SetItemDataSources%2A><br /><br /> <xref:ReportService2010.ReportingService2010.GetItemReferences%2A><br /><br /> <xref:ReportService2010.ReportingService2010.CreateDataSource%2A><br /><br /> <xref:ReportService2010.ReportingService2010.CreateLinkedItem%2A><br /><br /> <xref:ReportService2010.ReportingService2010.CreateFolder%2A>|  
|<span data-ttu-id="c2b39-269">角色</span><span class="sxs-lookup"><span data-stu-id="c2b39-269">Role</span></span>|<xref:ReportService2010.ReportingService2010.ListRoles%2A><br /><br /> <xref:ReportService2010.ReportingService2010.GetRoleProperties%2A>|<xref:ReportService2010.ReportingService2010.CreateRole%2A>|  
|<span data-ttu-id="c2b39-270">系统策略</span><span class="sxs-lookup"><span data-stu-id="c2b39-270">System Policy</span></span>|<xref:ReportService2010.ReportingService2010.GetSystemPolicies%2A>|<xref:ReportService2010.ReportingService2010.SetSystemPolicies%2A>|  
|<span data-ttu-id="c2b39-271">计划</span><span class="sxs-lookup"><span data-stu-id="c2b39-271">Schedule</span></span>|<xref:ReportService2010.ReportingService2010.ListSchedules%2A>|<xref:ReportService2010.ReportingService2010.CreateSchedule%2A>|  
|<span data-ttu-id="c2b39-272">订阅</span><span class="sxs-lookup"><span data-stu-id="c2b39-272">Subscription</span></span>|<xref:ReportService2010.ReportingService2010.ListSubscriptions%2A><br /><br /> <xref:ReportService2010.ReportingService2010.GetSubscriptionProperties%2A><br /><br /> <xref:ReportService2010.ReportingService2010.GetDataDrivenSubscriptionProperties%2A>|<xref:ReportService2010.ReportingService2010.CreateSubscription%2A><br /><br /> <xref:ReportService2010.ReportingService2010.CreateDataDrivenSubscription%2A>|  
|<span data-ttu-id="c2b39-273">高速缓存刷新计划</span><span class="sxs-lookup"><span data-stu-id="c2b39-273">Cache refresh plan</span></span>|<xref:ReportService2010.ReportingService2010.ListCacheRefreshPlans%2A><br /><br /> <xref:ReportService2010.ReportingService2010.GetCacheRefreshPlanProperties%2A>|<xref:ReportService2010.ReportingService2010.CreateCacheRefreshPlan%2A>|  
|<span data-ttu-id="c2b39-274">参数</span><span class="sxs-lookup"><span data-stu-id="c2b39-274">Parameters</span></span>|<xref:ReportService2010.ReportingService2010.GetItemParameters%2A>|<xref:ReportService2010.ReportingService2010.SetItemParameters%2A>|  
|<span data-ttu-id="c2b39-275">执行选项</span><span class="sxs-lookup"><span data-stu-id="c2b39-275">Execution options</span></span>|<xref:ReportService2010.ReportingService2010.GetExecutionOptions%2A>|<xref:ReportService2010.ReportingService2010.SetExecutionOptions%2A>|  
|<span data-ttu-id="c2b39-276">高速缓存选项</span><span class="sxs-lookup"><span data-stu-id="c2b39-276">Cache options</span></span>|<xref:ReportService2010.ReportingService2010.GetCacheOptions%2A>|<xref:ReportService2010.ReportingService2010.SetCacheOptions%2A>|  
|<span data-ttu-id="c2b39-277">历史记录设置</span><span class="sxs-lookup"><span data-stu-id="c2b39-277">History settings</span></span>|<xref:ReportService2010.ReportingService2010.GetItemHistoryOptions%2A>|<xref:ReportService2010.ReportingService2010.SetItemHistoryOptions%2A>|  
|<span data-ttu-id="c2b39-278">项策略</span><span class="sxs-lookup"><span data-stu-id="c2b39-278">Item Policy</span></span>|<xref:ReportService2010.ReportingService2010.GetPolicies%2A>|<xref:ReportService2010.ReportingService2010.SetPolicies%2A>|  
  
 <span data-ttu-id="c2b39-279">有关详细信息，请参阅 [Reporting Services 中的角色和任务与 SharePoint 组和权限的比较](../reporting-services-roles-tasks-vs-sharepoint-groups-permissions.md)。</span><span class="sxs-lookup"><span data-stu-id="c2b39-279">For more information, see [Compare Roles and Tasks in Reporting Services to SharePoint Groups and Permissions](../reporting-services-roles-tasks-vs-sharepoint-groups-permissions.md).</span></span>  
  
##  <a name="how-to-use-the-script"></a><a name="bkmk_how_to_use_the_script"></a><span data-ttu-id="c2b39-280">如何使用脚本</span><span class="sxs-lookup"><span data-stu-id="c2b39-280">How to use the script</span></span>  
  
1.  <span data-ttu-id="c2b39-281">将该脚本文件下载到一个本地文件夹中，例如 **c:\rss\ssrs_migration.rss**。</span><span class="sxs-lookup"><span data-stu-id="c2b39-281">Download the script file to a local folder, for example **c:\rss\ssrs_migration.rss**.</span></span>  
  
2.  <span data-ttu-id="c2b39-282">**使用管理权限**打开命令提示符。</span><span class="sxs-lookup"><span data-stu-id="c2b39-282">Open a command prompt **with administrative privileges**.</span></span>  
  
3.  <span data-ttu-id="c2b39-283">导航到包含 ssrs_migration.rss 文件的文件夹。</span><span class="sxs-lookup"><span data-stu-id="c2b39-283">Navigate to the folder containing the ssrs_migration.rss file.</span></span>  
  
4.  <span data-ttu-id="c2b39-284">使用适合于您的方案的参数运行命令。</span><span class="sxs-lookup"><span data-stu-id="c2b39-284">Run the command with the parameters appropriate for your scenario.</span></span>  
  
 <span data-ttu-id="c2b39-285">**基本示例，本机模式报表服务器到本机模式报表服务器：**</span><span class="sxs-lookup"><span data-stu-id="c2b39-285">**Basic Example, native mode report server to native mode report server:**</span></span>  
  
 <span data-ttu-id="c2b39-286">下面的示例将本机模式 **Sourceserver** 中的内容迁移到本机模式 **Targetserver**。</span><span class="sxs-lookup"><span data-stu-id="c2b39-286">The following example migrates content from the native mode **Sourceserver** to the native mode **Targetserver**.</span></span>  
  
 ```cmd
rs.exe -i ssrs_migration.rss -e Mgmt2010 -s http://SourceServer/ReportServer -u Domain\User -p password -v ts="http://TargetServer/reportserver" -v tu="Domain\Userser" -v tp="password"
```
  
 <span data-ttu-id="c2b39-287">**使用说明：**</span><span class="sxs-lookup"><span data-stu-id="c2b39-287">**Usage notes:**</span></span>  
  
-   <span data-ttu-id="c2b39-288">该脚本分两步运行。</span><span class="sxs-lookup"><span data-stu-id="c2b39-288">The script runs in two steps.</span></span>  
  
     <span data-ttu-id="c2b39-289">第一步是审核，以便返回将迁移的项的列表，第二步是迁移过程。</span><span class="sxs-lookup"><span data-stu-id="c2b39-289">The first step is an audit, to return a list of items that will be migrated and the second step is the migration process.</span></span>  
  
     <span data-ttu-id="c2b39-290">如果你只想要查看可能的迁移列表或者想要修改参数，则可以在第一步后 **取消该脚本** 。</span><span class="sxs-lookup"><span data-stu-id="c2b39-290">You can **cancel the script after step** one if you only want to see the possible migration list or you want to modify the parameters.</span></span> <span data-ttu-id="c2b39-291">相关设置不在第一步中列出。</span><span class="sxs-lookup"><span data-stu-id="c2b39-291">Dependent settings are not listed in step one.</span></span> <span data-ttu-id="c2b39-292">例如，不列出报表的高速缓存选项，而只列出报表本身。</span><span class="sxs-lookup"><span data-stu-id="c2b39-292">For example, the cache options of a report are not listed but the report itself is.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="c2b39-293">如果想要仅审核单个服务器，则对源和目标使用相同的服务器并在步骤 1 后取消</span><span class="sxs-lookup"><span data-stu-id="c2b39-293">If you want to just audit a single server, use the same server for source and destination and cancel after step 1</span></span>  
  
     <span data-ttu-id="c2b39-294">从第一步中获得的审核信息适用于查看源和目标本机模式服务器上的现有角色。</span><span class="sxs-lookup"><span data-stu-id="c2b39-294">A good use of the step 1 audit information is to review existing roles on both the source and target Native mode server.</span></span> <span data-ttu-id="c2b39-295">下面是第一步审核列表的示例。</span><span class="sxs-lookup"><span data-stu-id="c2b39-295">The following is an example of the step one audit list.</span></span> <span data-ttu-id="c2b39-296">请注意，该列表包含“roles”部分，因为使用了开关-v security="True"：</span><span class="sxs-lookup"><span data-stu-id="c2b39-296">Notice the list includes a "roles" section because the switch-v security="True" was used:</span></span>  
  
    -   `Retrieve and report the list of items that will be migrated. You can cancel the script after step 1 if you do not want to start the actual migration.`  
  
         `Retrieving roles:`  
  
         `Role: Browser`  
  
         `Role: Content Manager`  
  
         `Role: Model Item Browser`  
  
         `Retrieve and report the list of items that will be migrated. You can cancel the script after step 1 if you do not want to start the actual migration.`  
  
         `Retrieving roles:`  
  
         `Role: Browser`  
  
         `Role: Content Manager`  
  
         `Role: CustomRole`  
  
         `Role: Model Item Browser`  
  
         `Role: My Reports`  
  
         `Role: Publisher`  
  
         `Role: Report Builder`  
  
         `Role: System Administrator`  
  
         `Role: System User`  
  
         `Retrieving system policies:`  
  
         `Retrieving system policies:`  
  
         `System policy: BUILTIN\Administrators`  
  
         `System policy: domain\user1`  
  
         `System policy: domain\ueser2`  
  
         `Retrieving schedules:`  
  
         `Schedule: theMondaySchedule`  
  
         `Retrieving catalog items. This may take a while.`  
  
         `Folder: /Data Sources`  
  
         `DataSource: /Data Sources/Aworks2012_oltp`  
  
         `Folder: /images`  
  
         `Resource: /images/Boba Fett.png`  
  
         `Resource: /images/R2-D2.png`  
  
         `Folder: /Reports`  
  
         `Report: /Reports/products`  
  
         `Report: /Reports/test`  
  
         `Report: /Reports/TitleOnly`  
  
-   <span data-ttu-id="c2b39-297">SOURCE_URL 和 TARGET_URL 必须是指向源和目标 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 报表服务器的有效报表服务器 URL。</span><span class="sxs-lookup"><span data-stu-id="c2b39-297">The SOURCE_URL and TARGET_URL must be valid report server URLs that point to the source and target [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] report server.</span></span> <span data-ttu-id="c2b39-298">在本机模式下，报表服务器 URL 如下所示：</span><span class="sxs-lookup"><span data-stu-id="c2b39-298">In native mode, a report server URL looks like the following:</span></span>  
  
    -   `http://servername/reportserver`  
  
     <span data-ttu-id="c2b39-299">在 SharePoint 模式下，URL 如下所示：</span><span class="sxs-lookup"><span data-stu-id="c2b39-299">In SharePoint mode the URL looks like the following:</span></span>  
  
    -   `http://servername/_vti_bin/reportserver`  
  
-   <span data-ttu-id="c2b39-300">在 SharePoint 中提供给用户的虚拟文件夹结构可能与基础结构不同。</span><span class="sxs-lookup"><span data-stu-id="c2b39-300">The virtual folder structure presented to the user in SharePoint might be different than the underlying one.</span></span> <span data-ttu-id="c2b39-301">在浏览器中打开 `http://servername/_vti_bin/reportserver` 或 `http://servername/sites/site_name/_vti_bin/reportserver` 可看到非虚拟文件夹结构。</span><span class="sxs-lookup"><span data-stu-id="c2b39-301">Open `http://servername/_vti_bin/reportserver` or `http://servername/sites/site_name/_vti_bin/reportserver` in a browser to see the non-virtual folder structure.</span></span> <span data-ttu-id="c2b39-302">对于 SharePoint 模式下的服务器，这有助于将源文件夹和目标文件夹设置为“/”以外的内容。</span><span class="sxs-lookup"><span data-stu-id="c2b39-302">This is helpful for setting source folder and target folder to something other than "/", for a server in SharePoint mode.</span></span>  
  
-   <span data-ttu-id="c2b39-303">密码不迁移，并且必须重新输入，例如具有存储的凭据的数据源。</span><span class="sxs-lookup"><span data-stu-id="c2b39-303">Passwords are not migrated, and must be re-entered, for example data sources with stored credentials.</span></span>  
  
##  <a name="parameter-description"></a><a name="bkmk_parameter_description"></a><span data-ttu-id="c2b39-304">参数说明</span><span class="sxs-lookup"><span data-stu-id="c2b39-304">Parameter Description</span></span>  
  
|<span data-ttu-id="c2b39-305">参数</span><span class="sxs-lookup"><span data-stu-id="c2b39-305">Parameter</span></span>|<span data-ttu-id="c2b39-306">说明</span><span class="sxs-lookup"><span data-stu-id="c2b39-306">Description</span></span>|<span data-ttu-id="c2b39-307">必需</span><span class="sxs-lookup"><span data-stu-id="c2b39-307">Required</span></span>|  
|---------------|-----------------|--------------|  
|<span data-ttu-id="c2b39-308">**-s** Source_URL</span><span class="sxs-lookup"><span data-stu-id="c2b39-308">**-s** Source_URL</span></span>|<span data-ttu-id="c2b39-309">源报表服务器的 URL</span><span class="sxs-lookup"><span data-stu-id="c2b39-309">URL of the source report server</span></span>|<span data-ttu-id="c2b39-310">是</span><span class="sxs-lookup"><span data-stu-id="c2b39-310">Yes</span></span>|  
|<span data-ttu-id="c2b39-311">-u Domain\password -p password\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="c2b39-311">**-u** Domain\password **-p** password</span></span>|<span data-ttu-id="c2b39-312">源服务器的凭据。</span><span class="sxs-lookup"><span data-stu-id="c2b39-312">Credentials for source server.</span></span>|<span data-ttu-id="c2b39-313">可选，如果缺失则使用默认凭据</span><span class="sxs-lookup"><span data-stu-id="c2b39-313">OPTIONAL, default credentials are used if missing</span></span>|  
|<span data-ttu-id="c2b39-314">**-v st**="SITE"</span><span class="sxs-lookup"><span data-stu-id="c2b39-314">**-v st**="SITE"</span></span>||<span data-ttu-id="c2b39-315">可选。</span><span class="sxs-lookup"><span data-stu-id="c2b39-315">OPTIONAL.</span></span> <span data-ttu-id="c2b39-316">此参数仅用于 SharePoint 模式报表服务器。</span><span class="sxs-lookup"><span data-stu-id="c2b39-316">This parameter is only used for SharePoint mode report servers.</span></span>|  
|<span data-ttu-id="c2b39-317">**- v f**="SOURCEFOLDER"</span><span class="sxs-lookup"><span data-stu-id="c2b39-317">**- v f**="SOURCEFOLDER"</span></span>|<span data-ttu-id="c2b39-318">设置为“/”将迁移所有内容，设置为“/folder/subfolder”之类的项将执行部分迁移。</span><span class="sxs-lookup"><span data-stu-id="c2b39-318">Set to "/" for migrating everything, or to something like "/folder/subfolder" for partial migration.</span></span> <span data-ttu-id="c2b39-319">将复制该文件夹内的所有内容</span><span class="sxs-lookup"><span data-stu-id="c2b39-319">Everything within this folder will be copied</span></span>|<span data-ttu-id="c2b39-320">可选，默认为“/”。</span><span class="sxs-lookup"><span data-stu-id="c2b39-320">OPTIONAL, default is "/".</span></span>|  
|<span data-ttu-id="c2b39-321">**-v ts**="TARGET_URL"</span><span class="sxs-lookup"><span data-stu-id="c2b39-321">**-v ts**="TARGET_URL"</span></span>|<span data-ttu-id="c2b39-322">目标 RS 服务器的 URL</span><span class="sxs-lookup"><span data-stu-id="c2b39-322">'URL of the target RS server"</span></span>||  
|<span data-ttu-id="c2b39-323">**-v tu**="domain\username" **-v tp**="password"</span><span class="sxs-lookup"><span data-stu-id="c2b39-323">**-v tu**="domain\username" **-v tp**="password"</span></span>|<span data-ttu-id="c2b39-324">目标服务器的凭据。</span><span class="sxs-lookup"><span data-stu-id="c2b39-324">'Credentials for target server.</span></span>|<span data-ttu-id="c2b39-325">可选，如果缺失则使用默认凭据。</span><span class="sxs-lookup"><span data-stu-id="c2b39-325">OPTIONAL, default credentials are used if missing.</span></span> <span data-ttu-id="c2b39-326">**注意：** 在目标服务器中，用户将作为共享计划的“创建者”以及报表项的“修改者”帐户列出。</span><span class="sxs-lookup"><span data-stu-id="c2b39-326">**Note:** the user will be listed as the "creator" of shared schedules and "modified by" account for report items, in the target server.</span></span>|  
|<span data-ttu-id="c2b39-327">**-v tst**="SITE"</span><span class="sxs-lookup"><span data-stu-id="c2b39-327">**-v tst**="SITE"</span></span>||<span data-ttu-id="c2b39-328">可选。</span><span class="sxs-lookup"><span data-stu-id="c2b39-328">OPTIONAL.</span></span> <span data-ttu-id="c2b39-329">此参数仅用于 SharePoint 模式报表服务器。</span><span class="sxs-lookup"><span data-stu-id="c2b39-329">This parameter is only used for SharePoint mode report servers.</span></span>|  
|<span data-ttu-id="c2b39-330">**-v tf** ="TARGETFOLDER"</span><span class="sxs-lookup"><span data-stu-id="c2b39-330">**-v tf** ="TARGETFOLDER"</span></span>|<span data-ttu-id="c2b39-331">设置为“/”可迁移到根级别中。</span><span class="sxs-lookup"><span data-stu-id="c2b39-331">'Set to "/" for migrating into the root level.</span></span> <span data-ttu-id="c2b39-332">设置为“/folder/subfolder”可复制到已存在的目录下。</span><span class="sxs-lookup"><span data-stu-id="c2b39-332">Set to "/folder/subfolder" to copy into a that already exists.</span></span> <span data-ttu-id="c2b39-333">“SOURCEFOLDER”内的所有内容都将复制到“TARGETFOLDER”。</span><span class="sxs-lookup"><span data-stu-id="c2b39-333">Everything within "SOURCEFOLDER" will be copied into "TARGETFOLDER.</span></span>|<span data-ttu-id="c2b39-334">可选，默认为“/”。</span><span class="sxs-lookup"><span data-stu-id="c2b39-334">OPTIONAL, default is "/".</span></span>|  
|<span data-ttu-id="c2b39-335">**-v security**= "True/False"</span><span class="sxs-lookup"><span data-stu-id="c2b39-335">**-v security**= "True/False"</span></span>|<span data-ttu-id="c2b39-336">如果设置为“False”，目标目录项将根据目标系统的设置继承安全设置。</span><span class="sxs-lookup"><span data-stu-id="c2b39-336">If set to "False", destination catalog items will inherit security setting according to the settings of the target system.</span></span> <span data-ttu-id="c2b39-337">这是在不同的报表服务器类型之间进行迁移（例如本机模式到 SharePoint 模式）的推荐设置。</span><span class="sxs-lookup"><span data-stu-id="c2b39-337">This is the recommended setting for migrations between different report server types, for example native mode to SharePoint mode.</span></span> <span data-ttu-id="c2b39-338">如果设置为“True”，则该脚本将尝试迁移安全设置。</span><span class="sxs-lookup"><span data-stu-id="c2b39-338">If set to "True", the script attempts to migrate security settings.</span></span>|<span data-ttu-id="c2b39-339">可选，默认值为“False”。</span><span class="sxs-lookup"><span data-stu-id="c2b39-339">OPTIONAL, default is "False".</span></span>|  
  
##  <a name="more-examples"></a><a name="bkmk_more_examples"></a><span data-ttu-id="c2b39-340">更多示例</span><span class="sxs-lookup"><span data-stu-id="c2b39-340">More Examples</span></span>  
  
###  <a name="native-mode-report-server-to-native-mode-report-server"></a><a name="bkmk_native_2_native"></a><span data-ttu-id="c2b39-341">本机模式报表服务器到本机模式报表服务器</span><span class="sxs-lookup"><span data-stu-id="c2b39-341">Native Mode Report Server to Native Mode Report Server</span></span>  
 <span data-ttu-id="c2b39-342">下面的示例将本机模式 **Sourceserver** 中的内容迁移到本机模式 **Targetserver**。</span><span class="sxs-lookup"><span data-stu-id="c2b39-342">The following example migrates content from the native mode **Sourceserver** to the native mode **Targetserver**.</span></span>  
  
```cmd
rs.exe -i ssrs_migration.rss -e Mgmt2010 -s http://SourceServer/ReportServer -u Domain\User -p password -v ts="http://TargetServer/reportserver" -v tu="Domain\Userser" -v tp="password"  
```  
  
 <span data-ttu-id="c2b39-343">以下示例添加安全开关：</span><span class="sxs-lookup"><span data-stu-id="c2b39-343">The following example adds the security switch:</span></span>  
  
```cmd
rs.exe -i ssrs_migration.rss -e Mgmt2010 -s http://SourceServer/ReportServer -u Domain\User -p password -v ts="http://TargetServer/reportserver" -v tu="Domain\Userser" -v tp="password" -v security="True"  
```  
  
###  <a name="native-mode-to-sharepoint-mode---root-site"></a><a name="bkmk_native_2_sharepoint_root"></a><span data-ttu-id="c2b39-344">本机模式到 SharePoint 模式-根站点</span><span class="sxs-lookup"><span data-stu-id="c2b39-344">Native Mode to SharePoint Mode - root site</span></span>  
 <span data-ttu-id="c2b39-345">以下示例将内容从本机模式 SourceServer 迁移到 SharePoint 模式服务器 TargetServer 上的“根站点”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c2b39-345">The following example migrates content from a native mode **SourceServer** to the "root site " on a SharePoint mode server **TargetServer**.</span></span> <span data-ttu-id="c2b39-346">本机模式服务器上的“报表”和“数据源”文件夹作为 SharePoint 部署上的新库迁移。</span><span class="sxs-lookup"><span data-stu-id="c2b39-346">The "Reports" and "Data Sources" folders on the native mode server as migrated as new libraries on the SharePoint deployment.</span></span>  
  
 <span data-ttu-id="c2b39-347">![ssrs_rss_migrate_root_site](../media/ssrs-rss-migrate-root-site.gif "ssrs_rss_migrate_root_site")</span><span class="sxs-lookup"><span data-stu-id="c2b39-347">![ssrs_rss_migrate_root_site](../media/ssrs-rss-migrate-root-site.gif "ssrs_rss_migrate_root_site")</span></span>  
  
```cmd
rs.exe -i ssrs_migration.rss -e Mgmt2010 -s http://SourceServer/ReportServer -u Domain\User -p Password -v ts="http://TargetServer/_vti_bin/ReportServer" -v tu="Domain\User" -v tp="Password"  
```  
  
###  <a name="native-mode-to-sharepoint-mode--bi-site-collection"></a><a name="bkmk_native_2_sharepoint_with_site"></a> <span data-ttu-id="c2b39-348">本机模式到 SharePoint 模式 -“bi”网站集</span><span class="sxs-lookup"><span data-stu-id="c2b39-348">Native mode to SharePoint Mode -'bi' site collection</span></span>  
 <span data-ttu-id="c2b39-349">下面的示例将本机模式服务器的内容迁移到包含网站集“sites/bi”和共享文档库的 SharePoint 服务器。</span><span class="sxs-lookup"><span data-stu-id="c2b39-349">The following example migrates content from a native mode server to a SharePoint server that contains a site collection of "sites/bi" and a shared documents library.</span></span> <span data-ttu-id="c2b39-350">该脚本在目标文档库中创建文件夹。</span><span class="sxs-lookup"><span data-stu-id="c2b39-350">The script creates folders in document the destination library.</span></span> <span data-ttu-id="c2b39-351">例如，该脚本在目标文档库中创建“报表”和“数据源”文件夹。</span><span class="sxs-lookup"><span data-stu-id="c2b39-351">For example, the script will create a "Reports" and "Data Sources" folders in the target document library.</span></span>  
  
```cmd
rs.exe -i ssrs_migration.rss -e Mgmt2010 -s http://SourceServer/ReportServer -u Domain\User -p Password -v ts="http://TargetServer/sites/bi/_vti_bin/reportserver" -v tst="sites/bi" -v tf="Shared Documents" -v tu="Domain\User" -v tp="Password"  
```  
  
###  <a name="sharepoint-mode-to-sharepoint-mode--bi-site-collection"></a><a name="bkmk_sharepoint_2_sharepoint"></a> <span data-ttu-id="c2b39-352">SharePoint 模式到 SharePoint 模式 -“bi”网站集</span><span class="sxs-lookup"><span data-stu-id="c2b39-352">SharePoint Mode to SharePoint Mode -'bi' site collection</span></span>  
 <span data-ttu-id="c2b39-353">下面的示例将迁移内容：</span><span class="sxs-lookup"><span data-stu-id="c2b39-353">The following example migrates content:</span></span>  
  
-   <span data-ttu-id="c2b39-354">从包含网站集“sites/bi”和共享文档库的 SharePoint 服务器 **SourceServer** 。</span><span class="sxs-lookup"><span data-stu-id="c2b39-354">From a SharePoint server **SourceServer** that contains a site collection of "sites/bi" and a shared documents library.</span></span>  
  
-   <span data-ttu-id="c2b39-355">到包含网站集“sites/bi”和共享文档库的 **TargetServer** SharePoint 服务器。</span><span class="sxs-lookup"><span data-stu-id="c2b39-355">To a **TargetServer** SharePoint server that contains a site collection of "sites/bi" and a shared documents library.</span></span>  
  
```cmd
rs.exe -i ssrs_migration.rss -e Mgmt2010 -s http://SourceServer/_vti_bin/reportserver -v st="sites/bi" -v f="Shared Documents" -u Domain\User1 -p Password -v ts="http://TargetServer/sites/bi/_vti_bin/reportserver" -v tst="sites/bi" -v tf="Shared Documents" -v tu="Domain\User" -v tp="Password"  
```  
  
###  <a name="native-mode-to-native-mode---azure-virtual-machine"></a><a name="bkmk_native_to_native_Azure_vm"></a><span data-ttu-id="c2b39-356">本机模式到本机模式-Azure 虚拟机</span><span class="sxs-lookup"><span data-stu-id="c2b39-356">Native Mode to Native Mode - Azure Virtual Machine</span></span>  
 <span data-ttu-id="c2b39-357">下面的示例将迁移内容：</span><span class="sxs-lookup"><span data-stu-id="c2b39-357">The following example migrates content:</span></span>  
  
-   <span data-ttu-id="c2b39-358">从本机模式报表服务器 **SourceServer**。</span><span class="sxs-lookup"><span data-stu-id="c2b39-358">From a Native mode report server **SourceServer**.</span></span>  
  
-   <span data-ttu-id="c2b39-359">到在 Azure 虚拟机上运行的“TargetServer”\*\*\*\* 本机模式报表服务器。</span><span class="sxs-lookup"><span data-stu-id="c2b39-359">To a **TargetServer** Native mode report server running on an Azure virtual machine.</span></span> <span data-ttu-id="c2b39-360">**TargetServer**未加入**SourceServer**的域，并且是 Azure 虚拟机**TargetServer\*\*\*\*上的管理员**。</span><span class="sxs-lookup"><span data-stu-id="c2b39-360">The **TargetServer** is not joined to the domain of the **SourceServer** and the **User2** is an administrator on the Azure virtual machine **TargetServer**.</span></span>  
  
```cmd
rs.exe -i ssrs_migration.rss -e Mgmt2010 -s http://SourceServer/ReportServer -u Domain\user1 -p Password -v ts="http://ssrsnativeazure.cloudapp.net/ReportServer" -v tu="user2" -v tp="Password2"  
```  
  
> [!TIP]  
>  <span data-ttu-id="c2b39-361">有关如何使用 Windows PowerShell 在 Azure 虚拟机上创建 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 报表服务器的信息，请参阅[使用 PowerShell 创建运行本机模式报表服务器的 Azure VM](https://msdn.microsoft.com/library/dn449661.aspx)。</span><span class="sxs-lookup"><span data-stu-id="c2b39-361">For information on how to use Windows PowerShell to create [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] report servers on Azure virtual machines, see [Use PowerShell to Create an Azure VM With a Native Mode Report Server](https://msdn.microsoft.com/library/dn449661.aspx).</span></span>  
  
##  <a name="sharepoint-mode--bi-site-collection-to-a-native-mode-server-on-azure-virtual-machine"></a><a name="bkmk_sharepoint_site_to_native_Azure_vm"></a><span data-ttu-id="c2b39-362">SharePoint 模式-Azure 虚拟机上的本机模式服务器的 "bi" 网站集</span><span class="sxs-lookup"><span data-stu-id="c2b39-362">SharePoint Mode -'bi' site collection to a Native Mode Server on Azure Virtual Machine</span></span>  
 <span data-ttu-id="c2b39-363">下面的示例将迁移内容：</span><span class="sxs-lookup"><span data-stu-id="c2b39-363">The following example migrates content:</span></span>  
  
-   <span data-ttu-id="c2b39-364">从包含网站集 “sites/bi” 和共享文档库的 SharePoint 模式报表服务器 **SourceServer** 。</span><span class="sxs-lookup"><span data-stu-id="c2b39-364">From a SharePoint mode report server **SourceServer** that contains a site collection of "sites/bi" and a shared documents library.</span></span>  
  
-   <span data-ttu-id="c2b39-365">到在 Azure 虚拟机上运行的“TargetServer”\*\*\*\* 本机模式报表服务器。</span><span class="sxs-lookup"><span data-stu-id="c2b39-365">To a **TargetServer** Native mode report server running on an Azure virtual machine.</span></span> <span data-ttu-id="c2b39-366">**TargetServer**未加入**SourceServer**的域，并且是 Azure 虚拟机**TargetServer\*\*\*\*上的管理员**。</span><span class="sxs-lookup"><span data-stu-id="c2b39-366">The **TargetServer** is not joined to the domain of the **SourceServer** and the **User2** is an administrator on the Azure virtual machine **TargetServer**.</span></span>  
  
```cmd
rs.exe -i ssrs_migration.rss -e Mgmt2010 -s http://uetesta02/_vti_bin/reportserver -u user1 -p Password -v ts="http://ssrsnativeazure.cloudapp.net/ReportServer" -v tu="user2" -v tp="Passowrd2"  
```  
  
##  <a name="verification"></a><a name="bkmk_verification"></a><span data-ttu-id="c2b39-367">针对</span><span class="sxs-lookup"><span data-stu-id="c2b39-367">Verification</span></span>  
 <span data-ttu-id="c2b39-368">本节总结了为验证内容和策略是否已成功迁移而在目标服务器上要执行的一些步骤。</span><span class="sxs-lookup"><span data-stu-id="c2b39-368">The section summarizes some of the steps to take on the destination server to verify content and policies were successfully migrated.</span></span>  
  
### <a name="schedules"></a><span data-ttu-id="c2b39-369">计划</span><span class="sxs-lookup"><span data-stu-id="c2b39-369">Schedules</span></span>  
 <span data-ttu-id="c2b39-370">验证目标服务器上的计划：</span><span class="sxs-lookup"><span data-stu-id="c2b39-370">To verify schedules on the target server:</span></span>  
  
 <span data-ttu-id="c2b39-371">**本机模式**</span><span class="sxs-lookup"><span data-stu-id="c2b39-371">**Native Mode**</span></span>  
  
1.  <span data-ttu-id="c2b39-372">浏览到目标服务器上的报表管理器。</span><span class="sxs-lookup"><span data-stu-id="c2b39-372">Browse to Report Manager on the destination server.</span></span>  
  
2.  <span data-ttu-id="c2b39-373">在顶部菜单上，单击 **“网站设置”** 。</span><span class="sxs-lookup"><span data-stu-id="c2b39-373">Click **Site Settings** on the top menu.</span></span>  
  
3.  <span data-ttu-id="c2b39-374">在左窗格中，单击 **“计划”** 。</span><span class="sxs-lookup"><span data-stu-id="c2b39-374">Click **Schedules** in the left pane.</span></span>  
  
 <span data-ttu-id="c2b39-375">**SharePoint 模式：**</span><span class="sxs-lookup"><span data-stu-id="c2b39-375">**SharePoint Mode:**</span></span>  
  
1.  <span data-ttu-id="c2b39-376">浏览至“站点设置” \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c2b39-376">Browse to **Site settings**.</span></span>  
  
2.  <span data-ttu-id="c2b39-377">在 **Reporting Services** 组中，单击 **“管理共享计划”**。</span><span class="sxs-lookup"><span data-stu-id="c2b39-377">In the **Reporting Services** group, click **Manage Shared Schedules**.</span></span>  
  
### <a name="roles-and-groups"></a><span data-ttu-id="c2b39-378">角色和组</span><span class="sxs-lookup"><span data-stu-id="c2b39-378">Roles and Groups</span></span>  
 <span data-ttu-id="c2b39-379">**本机模式**</span><span class="sxs-lookup"><span data-stu-id="c2b39-379">**Native Mode**</span></span>  
  
1.  <span data-ttu-id="c2b39-380">打开 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 并且连接到您的本机模式报表服务器。</span><span class="sxs-lookup"><span data-stu-id="c2b39-380">Open [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and connect to your native mode report server.</span></span>  
  
2.  <span data-ttu-id="c2b39-381">在**对象资源管理器**单击 "**安全**"。</span><span class="sxs-lookup"><span data-stu-id="c2b39-381">In **Object Explorer** click **Security**.</span></span>  
  
3.  <span data-ttu-id="c2b39-382">单击“角色”。</span><span class="sxs-lookup"><span data-stu-id="c2b39-382">Click **Roles**.</span></span>  
  
##  <a name="troubleshooting"></a><a name="bkmk_troubleshoot"></a> <span data-ttu-id="c2b39-383">故障排除</span><span class="sxs-lookup"><span data-stu-id="c2b39-383">Troubleshooting</span></span>  
 <span data-ttu-id="c2b39-384">使用跟踪标志 **-t**可接收更多信息。</span><span class="sxs-lookup"><span data-stu-id="c2b39-384">Use the trace flag **-t** to receive more information.</span></span> <span data-ttu-id="c2b39-385">例如，如果您运行此脚本并看到如下消息</span><span class="sxs-lookup"><span data-stu-id="c2b39-385">For example, if you run the script and see a message similar to the following</span></span>  
  
-   <span data-ttu-id="c2b39-386">无法连接到服务器： http:// \<servername> /ReportServer/ReportService2010.asmx</span><span class="sxs-lookup"><span data-stu-id="c2b39-386">Could not connect to server: http://\<servername>/ReportServer/ReportService2010.asmx</span></span>  
  
 <span data-ttu-id="c2b39-387">使用 **-t**标志再次运行该脚本，以查看类似于以下内容的消息：</span><span class="sxs-lookup"><span data-stu-id="c2b39-387">Run the script again with the **-t** flag, to see a message similar to the following:</span></span>  
  
-   <span data-ttu-id="c2b39-388">System.exception：无法连接到服务器： http:// \<servername> /ReportServer/ReportService2010.asmx---> 系统 .net。 WebException：**请求失败，http 状态401：未经授权**。</span><span class="sxs-lookup"><span data-stu-id="c2b39-388">System.Exception: Could not connect to server: http://\<servername>/ReportServer/ReportService2010.asmx ---> System.Net.WebException: **The request failed with HTTP status 401: Unauthorized**.</span></span>   <span data-ttu-id="c2b39-389">在 System.Web.Services.Protocols.SoapHttpClientProtocol.ReadResponse （SoapClientMessage 消息、 WebResponse 响应、 流 responseStream、 布尔值 asyncCall） 在 System.Web.Services.Protocols.SoapHttpClientProtocol.Invoke （字符串方法名称，对象 [] 参数） 在 Microsoft.SqlServer.ReportingServices2010.ReportingService2010.IsSSLRequired() 在 Microsoft.ReportingServices.ScriptHost.Management2010Endpoint.PingService （字符串 url、 String userName、 字符串密码字符串域、 Int32 超时) 在 Microsoft.ReportingServices.ScriptHost.ScriptHost.DetermineServerUrlSecurity()-内部异常堆栈跟踪结束----</span><span class="sxs-lookup"><span data-stu-id="c2b39-389">at System.Web.Services.Protocols.SoapHttpClientProtocol.ReadResponse(SoapClientMessage message, WebResponse response, Stream responseStream, Boolean asyncCall)   at System.Web.Services.Protocols.SoapHttpClientProtocol.Invoke(String methodName, Object[] parameters)   at Microsoft.SqlServer.ReportingServices2010.ReportingService2010.IsSSLRequired()   at Microsoft.ReportingServices.ScriptHost.Management2010Endpoint.PingService(String url, String userName, String password, String domain, Int32 timeout)   at Microsoft.ReportingServices.ScriptHost.ScriptHost.DetermineServerUrlSecurity()   --- End of inner exception stack trace ---</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2b39-390">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c2b39-390">See Also</span></span>  
 <span data-ttu-id="c2b39-391">[RS.exe 实用程序 &#40;SSRS&#41;](rs-exe-utility-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="c2b39-391">[RS.exe Utility &#40;SSRS&#41;](rs-exe-utility-ssrs.md) </span></span>  
 [<span data-ttu-id="c2b39-392">Reporting Services 中的角色和任务与 SharePoint 组和权限的比较</span><span class="sxs-lookup"><span data-stu-id="c2b39-392">Compare Roles and Tasks in Reporting Services to SharePoint Groups and Permissions</span></span>](../reporting-services-roles-tasks-vs-sharepoint-groups-permissions.md)  
