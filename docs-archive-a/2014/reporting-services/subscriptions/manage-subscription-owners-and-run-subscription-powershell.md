---
title: 使用 PowerShell 更改和列出 Reporting Services 订阅所有者并运行订阅 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 0fa6cb36-68fc-4fb8-b1dc-ae4f12bf6ff0
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b274dc190d8830a2cf7b55110f15267a00c581e2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587165"
---
# <a name="use-powershell-to-change-and-list-reporting-services-subscription-owners-and-run-a-subscription"></a><span data-ttu-id="63342-102">Use PowerShell to Change and List Reporting Services Subscription Owners and Run a Subscription</span><span class="sxs-lookup"><span data-stu-id="63342-102">Use PowerShell to Change and List Reporting Services Subscription Owners and Run a Subscription</span></span>
  <span data-ttu-id="63342-103">从 [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)][!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 开始，可通过编程方式将 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 订阅的所有权从一个用户转移给另一个用户。</span><span class="sxs-lookup"><span data-stu-id="63342-103">Starting with [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)][!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] you can programmatically transfer the ownership of a [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] subscription from one user to another.</span></span> <span data-ttu-id="63342-104">本主题提供多个 Windows PowerShell 脚本，这些脚本可用于更改订阅所有权，或只是列出订阅所有权。</span><span class="sxs-lookup"><span data-stu-id="63342-104">This topic provides several Windows PowerShell scripts you can use to change or simply list subscription ownership.</span></span> <span data-ttu-id="63342-105">每个示例都包含本机模式和 SharePoint 模式的语法示例。</span><span class="sxs-lookup"><span data-stu-id="63342-105">Each sample includes sample syntax for both Native mode and SharePoint mode.</span></span> <span data-ttu-id="63342-106">更改订阅的所有者后，订阅将在新所有者的安全上下文中执行，并且报表中的 User!UserID 字段将显示新所有者的值。</span><span class="sxs-lookup"><span data-stu-id="63342-106">After you change the subscription owner, the subscription will then execute in the security context of the new owner, and the User!UserID field in the report will display the value of new owner.</span></span> <span data-ttu-id="63342-107">有关 PowerShell 示例调用的对象模型的详细信息，请参阅 <xref:ReportService2010.ReportingService2010.ChangeSubscriptionOwner%2A></span><span class="sxs-lookup"><span data-stu-id="63342-107">For more information on the object model the PowerShell samples call, see <xref:ReportService2010.ReportingService2010.ChangeSubscriptionOwner%2A></span></span>

 <span data-ttu-id="63342-108">![PowerShell 相关内容](../media/rs-powershellicon.jpg "PowerShell 相关内容")</span><span class="sxs-lookup"><span data-stu-id="63342-108">![PowerShell related content](../media/rs-powershellicon.jpg "PowerShell related content")</span></span>

||
|-|
|<span data-ttu-id="63342-109">**[!INCLUDE[applies](../../includes/applies-md.md)]** [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 本机模式 | [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] SharePoint 模式</span><span class="sxs-lookup"><span data-stu-id="63342-109">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] Native mode &#124; [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] SharePoint mode</span></span>|

 <span data-ttu-id="63342-110">**本主题内容：**</span><span class="sxs-lookup"><span data-stu-id="63342-110">**In this topic:**</span></span>

-   [<span data-ttu-id="63342-111">如何使用脚本</span><span class="sxs-lookup"><span data-stu-id="63342-111">How to use the scripts</span></span>](#bkmk_how_to)

-   [<span data-ttu-id="63342-112">脚本：列出所有订阅的所有权</span><span class="sxs-lookup"><span data-stu-id="63342-112">Script: List the ownership of all subscriptions</span></span>](#bkmk_list_ownership_all)

-   [<span data-ttu-id="63342-113">脚本：列出特定用户拥有的全部订阅</span><span class="sxs-lookup"><span data-stu-id="63342-113">Script: List all subscriptions owned by a specific user</span></span>](#bkmk_list_all_one_user)

-   [<span data-ttu-id="63342-114">脚本：更改特定用户拥有的全部订阅的所有权</span><span class="sxs-lookup"><span data-stu-id="63342-114">Script: Change ownership for all subscriptions owned by a specific user</span></span>](#bkmk_change_all)

-   [<span data-ttu-id="63342-115">脚本：列出与特定报表关联的全部订阅</span><span class="sxs-lookup"><span data-stu-id="63342-115">Script: List all subscriptions associated with a specific report</span></span>](#bkmk_list_for_1_report)

-   [<span data-ttu-id="63342-116">脚本：更改特定订阅的所有权</span><span class="sxs-lookup"><span data-stu-id="63342-116">Script: Change ownership of a specific subscription</span></span>](#bkmk_change_all_1_subscription)

-   [<span data-ttu-id="63342-117">脚本：运行（触发）单个订阅</span><span class="sxs-lookup"><span data-stu-id="63342-117">Script: Run (fire) a single subscription</span></span>](#bkmk_run_1_subscription)

##  <a name="how-to-use-the-scripts"></a><a name="bkmk_how_to"></a> <span data-ttu-id="63342-118">如何使用脚本</span><span class="sxs-lookup"><span data-stu-id="63342-118">How to use the scripts</span></span>

### <a name="permissions"></a><span data-ttu-id="63342-119">权限</span><span class="sxs-lookup"><span data-stu-id="63342-119">Permissions</span></span>
 <span data-ttu-id="63342-120">本节总结了使用各本机模式和 SharePoint 模式 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]方法所需的权限级别。</span><span class="sxs-lookup"><span data-stu-id="63342-120">This section summarizes the permission levels required to use each of the methods for both Native and SharePoint mode [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="63342-121">本主题中的脚本使用以下 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 方法：</span><span class="sxs-lookup"><span data-stu-id="63342-121">The scripts in this topic use the following [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] methods:</span></span>

-   [<span data-ttu-id="63342-122">ReportingService2010.ListSubscriptions 方法</span><span class="sxs-lookup"><span data-stu-id="63342-122">ReportingService2010.ListSubscriptions Method</span></span>](https://technet.microsoft.com/library/reportservice2010.reportingservice2010.listsubscriptions.aspx)

-   [<span data-ttu-id="63342-123">ReportingService2010.ChangeSubscriptionOwner 方法</span><span class="sxs-lookup"><span data-stu-id="63342-123">ReportingService2010.ChangeSubscriptionOwner Method</span></span>](https://technet.microsoft.com/library/reportservice2010.reportingservice2010.changesubscriptionowner.aspx)

-   [<span data-ttu-id="63342-124">ReportingService2010.ListChildren</span><span class="sxs-lookup"><span data-stu-id="63342-124">ReportingService2010.ListChildren</span></span>](https://technet.microsoft.com/library/reportservice2010.reportingservice2010.listchildren.aspx)

-   <span data-ttu-id="63342-125">[ReportingService2010.FireEvent](https://technet.microsoft.com/library/reportservice2010.reportingservice2010.fireevent.aspx) 方法仅在最后一个脚本中使用，以触发特定订阅运行。</span><span class="sxs-lookup"><span data-stu-id="63342-125">The method [ReportingService2010.FireEvent](https://technet.microsoft.com/library/reportservice2010.reportingservice2010.fireevent.aspx) is only used in the last script to trigger a specific subscription to run.</span></span> <span data-ttu-id="63342-126">如果不计划使用该脚本，则可以忽略针对 FireEvent 方法的权限要求。</span><span class="sxs-lookup"><span data-stu-id="63342-126">If you do not plan to use that script you can ignore the permission requirements for the FireEvent method.</span></span>

 <span data-ttu-id="63342-127">**本机模式：**</span><span class="sxs-lookup"><span data-stu-id="63342-127">**Native mode:**</span></span>

-   <span data-ttu-id="63342-128">列出订阅：报表上 ( HYPERLINK " https://technet.microsoft.com/library/microsoft.reportingservices.interfaces.reportoperation.aspx " READSUBSCRIPTION，用户是订阅所有者) 或 ReadAnySubscription</span><span class="sxs-lookup"><span data-stu-id="63342-128">List Subscriptions: ( HYPERLINK "https://technet.microsoft.com/library/microsoft.reportingservices.interfaces.reportoperation.aspx" ReadSubscription on the report AND the user is the subscription owner) OR ReadAnySubscription</span></span>

-   <span data-ttu-id="63342-129">更改订阅：用户必须是 BUILTIN\Administrators 组的成员</span><span class="sxs-lookup"><span data-stu-id="63342-129">Change Subscriptions: The user must be a member of the BUILTIN\Administrators group</span></span>

-   <span data-ttu-id="63342-130">列出子级：项上的 ReadProperties</span><span class="sxs-lookup"><span data-stu-id="63342-130">List Children: ReadProperties on Item</span></span>

-   <span data-ttu-id="63342-131">触发事件：GenerateEvents（系统）</span><span class="sxs-lookup"><span data-stu-id="63342-131">Fire Event: GenerateEvents (System)</span></span>

 <span data-ttu-id="63342-132">**SharePoint 模式：**</span><span class="sxs-lookup"><span data-stu-id="63342-132">**SharePoint mode:**</span></span>

-   <span data-ttu-id="63342-133">列出订阅：报表上的 Managealerts or 或 ( HYPERLINK " https://technet.microsoft.com/library/microsoft.sharepoint.spbasepermissions.aspx " CREATEALERTS，用户是订阅所有者，订阅是计时订阅) 。</span><span class="sxs-lookup"><span data-stu-id="63342-133">List Subscriptions: ManageAlerts OR ( HYPERLINK "https://technet.microsoft.com/library/microsoft.sharepoint.spbasepermissions.aspx" CreateAlerts on the report AND the user is the subscription owner and the subscription is a timed subscription).</span></span>

-   <span data-ttu-id="63342-134">更改订阅：ManageWeb</span><span class="sxs-lookup"><span data-stu-id="63342-134">Change Subscriptions: ManageWeb</span></span>

-   <span data-ttu-id="63342-135">列出子级：ViewListItems</span><span class="sxs-lookup"><span data-stu-id="63342-135">List Children: ViewListItems</span></span>

-   <span data-ttu-id="63342-136">触发事件：ManageWeb</span><span class="sxs-lookup"><span data-stu-id="63342-136">Fire Event: ManageWeb</span></span>

 <span data-ttu-id="63342-137">有关详细信息，请参阅 [Reporting Services 中的角色和任务与 SharePoint 组和权限的比较](../reporting-services-roles-tasks-vs-sharepoint-groups-permissions.md)。</span><span class="sxs-lookup"><span data-stu-id="63342-137">For more information, see [Compare Roles and Tasks in Reporting Services to SharePoint Groups and Permissions](../reporting-services-roles-tasks-vs-sharepoint-groups-permissions.md).</span></span>

### <a name="script-usage"></a><span data-ttu-id="63342-138">脚本使用情况</span><span class="sxs-lookup"><span data-stu-id="63342-138">Script usage</span></span>
 <span data-ttu-id="63342-139">**创建脚本文件 (.ps1)**</span><span class="sxs-lookup"><span data-stu-id="63342-139">**Create Script files (.ps1)**</span></span>

1.  <span data-ttu-id="63342-140">创建一个名为 **c:\scripts**的文件夹。</span><span class="sxs-lookup"><span data-stu-id="63342-140">Create a folder named **c:\scripts**.</span></span> <span data-ttu-id="63342-141">如果选择不同的文件夹，则请修改命令行语法语句示例中使用的文件夹名称。</span><span class="sxs-lookup"><span data-stu-id="63342-141">If you choose a different folder then modify the folder name used in the example command line syntax statements.</span></span>

2.  <span data-ttu-id="63342-142">为每个脚本创建文本文件并将文件保存至 c:\scripts 文件夹。</span><span class="sxs-lookup"><span data-stu-id="63342-142">Create a text file for each script and save the files to the c:\scripts folder.</span></span> <span data-ttu-id="63342-143">创建 .ps1 时，请使用各命令行语法示例中的名称。</span><span class="sxs-lookup"><span data-stu-id="63342-143">When you create the .ps1 files, use the name from each example command line syntax.</span></span>

3.  <span data-ttu-id="63342-144">使用管理员权限打开命令提示符。</span><span class="sxs-lookup"><span data-stu-id="63342-144">Open a command prompt with administrative privileges.</span></span>

4.  <span data-ttu-id="63342-145">使用各示例提供的示例命令行语法运行各脚本文件。</span><span class="sxs-lookup"><span data-stu-id="63342-145">Run each script file, using the sample command line syntax provided with each example.</span></span>

 <span data-ttu-id="63342-146">**经测试的环境**</span><span class="sxs-lookup"><span data-stu-id="63342-146">**Tested environments**</span></span>

 <span data-ttu-id="63342-147">本主题中的脚本已在 PowerShell 版本 3 上和以下版本的 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]上进行了测试：</span><span class="sxs-lookup"><span data-stu-id="63342-147">The scripts in this topic were tested on PowerShell version 3 and with the following versions of [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]:</span></span>

-   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]

-   [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]

-   [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)]

##  <a name="script-list-the-ownership-of-all-subscriptions"></a><a name="bkmk_list_ownership_all"></a> <span data-ttu-id="63342-148">脚本：列出全部订阅的所有权</span><span class="sxs-lookup"><span data-stu-id="63342-148">Script: List the ownership of all subscriptions</span></span>
 <span data-ttu-id="63342-149">此脚本列出站点上的所有订阅。</span><span class="sxs-lookup"><span data-stu-id="63342-149">This script lists all of the subscriptions on a site.</span></span> <span data-ttu-id="63342-150">可以使用此脚本测试连接或验证在其他脚本中使用的报表路径和订阅 ID。</span><span class="sxs-lookup"><span data-stu-id="63342-150">You can use this script to test your connection or to verify the report path and subscription id for use in the other scripts.</span></span> <span data-ttu-id="63342-151">这也是用于轻松审核存在哪些订阅以及它们的所有者是谁的一个有用脚本。</span><span class="sxs-lookup"><span data-stu-id="63342-151">This is also a useful script to simply audit what subscriptions exist and who owns them.</span></span>

### <a name="native-mode-syntax"></a><span data-ttu-id="63342-152">纯模式语法</span><span class="sxs-lookup"><span data-stu-id="63342-152">Native mode syntax</span></span>

```cmd
powershell c:\scripts\ListAll_SSRS_Subscriptions.ps1 "[server]/reportserver" "/"
```

### <a name="sharepoint-mode-syntax"></a><span data-ttu-id="63342-153">SharePoint 模式语法</span><span class="sxs-lookup"><span data-stu-id="63342-153">SharePoint mode syntax</span></span>

```cmd
powershell c:\scripts\ListAll_SSRS_Subscriptions.ps1 "[server]/_vti_bin/reportserver" "http://[server]"
```

### <a name="script"></a><span data-ttu-id="63342-154">Script</span><span class="sxs-lookup"><span data-stu-id="63342-154">Script</span></span>

```powershell
# Parameters
#    server   - server and instance name (e.g. myserver/reportserver or myserver/reportserver_db2)

Param(
    [string]$server,
    [string]$site
   )

$rs2010 += New-WebServiceProxy -Uri "http://$server/ReportService2010.asmx" -Namespace SSRS.ReportingService2010 -UseDefaultCredential ;
$subscriptions += $rs2010.ListSubscriptions($site); # use "/" for default native mode site

Write-Host " "
Write-Host "----- $server's Subscriptions: "
$subscriptions | select Path, report, Description, Owner, SubscriptionID, lastexecuted, Status
```

> [!TIP]
>  <span data-ttu-id="63342-155">要在 SharePoint 模式下验证站点 URL，请使用 SharePoint cmdlet **Get-SPSite**。</span><span class="sxs-lookup"><span data-stu-id="63342-155">To verify site URLS in SharePoint mode, use the SharePoint cmdlet **Get-SPSite**.</span></span> <span data-ttu-id="63342-156">有关详细信息，请参阅 [Get-SPSite](https://technet.microsoft.com/library/ff607950\(v=office.15\).aspx)。</span><span class="sxs-lookup"><span data-stu-id="63342-156">For more information, see [Get-SPSite](https://technet.microsoft.com/library/ff607950\(v=office.15\).aspx).</span></span>

##  <a name="script-list-all-subscriptions-owned-by-a-specific-user"></a><a name="bkmk_list_all_one_user"></a> <span data-ttu-id="63342-157">脚本：列出特定用户拥有的全部订阅</span><span class="sxs-lookup"><span data-stu-id="63342-157">Script: List all subscriptions owned by a specific user</span></span>
 <span data-ttu-id="63342-158">此脚本列出特定用户拥有的全部订阅。</span><span class="sxs-lookup"><span data-stu-id="63342-158">This script lists all of the subscriptions owned by a specific user.</span></span> <span data-ttu-id="63342-159">可以使用此脚本测试连接或验证在其他脚本中使用的报表路径和订阅 ID。</span><span class="sxs-lookup"><span data-stu-id="63342-159">You can use this script to test your connection or to verify the report path and subscription id for use in the other scripts.</span></span> <span data-ttu-id="63342-160">当有人离开您的组织，而您想要验证他们拥有哪些订阅，以便更改所有者或删除订阅时，此脚本非常有用。</span><span class="sxs-lookup"><span data-stu-id="63342-160">This script is useful when someone in your organization leaves and you want to verify what subscriptions they owned so you can change the owner or delete the subscription.</span></span>

### <a name="native-mode-syntax"></a><span data-ttu-id="63342-161">纯模式语法</span><span class="sxs-lookup"><span data-stu-id="63342-161">Native mode syntax</span></span>

```cmd
powershell c:\scripts\ListAll_SSRS_Subscriptions4User.ps1 "[Domain]\[user]" "[server]/reportserver" "/"
```

### <a name="sharepoint-mode-syntax"></a><span data-ttu-id="63342-162">SharePoint 模式语法</span><span class="sxs-lookup"><span data-stu-id="63342-162">SharePoint mode syntax</span></span>

```cmd
powershell c:\scripts\ListAll_SSRS_Subscriptions4User.ps1 "[Domain]\[user]"  "[server]/_vti_bin/reportserver" "http://[server]"
```

### <a name="script"></a><span data-ttu-id="63342-163">Script</span><span class="sxs-lookup"><span data-stu-id="63342-163">Script</span></span>

```powershell
# Parameters:
#    currentOwner - DOMAIN\USER that owns the subscriptions you wish to change
#    server        - server and instance name (e.g. myserver/reportserver or myserver/reportserver_db2)
#    site        - use "/" for default native mode site
Param(
    [string]$currentOwner,
    [string]$server,
    [string]$site
)

$rs2010 = New-WebServiceProxy -Uri "http://$server/ReportService2010.asmx" -Namespace SSRS.ReportingService2010 -UseDefaultCredential ;
$subscriptions += $rs2010.ListSubscriptions($site);

Write-Host " "
Write-Host " "
Write-Host "----- $currentOwner's Subscriptions: "
$subscriptions | select Path, report, Description, Owner, SubscriptionID, lastexecuted,Status | where {$_.owner -eq $currentOwner}
```

##  <a name="script-change-ownership-for-all-subscriptions-owned-by-a-specific-user"></a><a name="bkmk_change_all"></a> <span data-ttu-id="63342-164">脚本：更改特定用户拥有的全部订阅的所有权</span><span class="sxs-lookup"><span data-stu-id="63342-164">Script: Change ownership for all subscriptions owned by a specific user</span></span>
 <span data-ttu-id="63342-165">此脚本将特定用户拥有的全部订阅的所有权更改为新所有者参数。</span><span class="sxs-lookup"><span data-stu-id="63342-165">This script changes the ownership for all subscriptions owned by a specific user to the new owner parameter.</span></span>

### <a name="native-mode-syntax"></a><span data-ttu-id="63342-166">纯模式语法</span><span class="sxs-lookup"><span data-stu-id="63342-166">Native mode syntax</span></span>

```cmd
powershell c:\scripts\ChangeALL_SSRS_SubscriptionOwner.ps1 "[Domain]\current owner]" "[Domain]\[new owner]" "[server]/reportserver"
```

### <a name="sharepoint-mode-syntax"></a><span data-ttu-id="63342-167">SharePoint 模式语法</span><span class="sxs-lookup"><span data-stu-id="63342-167">SharePoint mode syntax</span></span>

```cmd
powershell c:\scripts\ChangeALL_SSRS_SubscriptionOwner.ps1 "[Domain]\{current owner]" "[Domain]\[new owner]" "[server]/_vti_bin/reportserver"
```

### <a name="script"></a><span data-ttu-id="63342-168">Script</span><span class="sxs-lookup"><span data-stu-id="63342-168">Script</span></span>

```powershell
# Parameters:
#    currentOwner - DOMAIN\USER that owns the subscriptions you wish to change
#    newOwner      - DOMAIN\USER that will own the subscriptions you wish to change
#    server        - server and instance name (e.g. myserver/reportserver, myserver/reportserver_db2, myserver/_vti_bin/reportserver)

Param(
    [string]$currentOwner,
    [string]$newOwner,
    [string]$server
)

$rs2010 = New-WebServiceProxy -Uri "http://$server/ReportService2010.asmx" -Namespace SSRS.ReportingService2010 -UseDefaultCredential ;
$items = $rs2010.ListChildren("/", $true);

$subscriptions = @();

ForEach ($item in $items)
{
    if ($item.TypeName -eq "Report")
    {
        $curRepSubs = $rs2010.ListSubscriptions($item.Path);
        ForEach ($curRepSub in $curRepSubs)
        {
            if ($curRepSub.Owner -eq $currentOwner)
            {
                $subscriptions += $curRepSub;
            }
        }
    }
}

Write-Host " "
Write-Host " "
Write-Host -foregroundcolor "green" "-----  $currentOwner's Subscriptions changing ownership to $newOwner : "
$subscriptions | select SubscriptionID, Owner, Path, Description,  Status  | format-table -AutoSize

ForEach ($sub in $subscriptions)
{
    $rs2010.ChangeSubscriptionOwner($sub.SubscriptionID, $newOwner);
}

$subs2 = @();

ForEach ($item in $items)
{
    if ($item.TypeName -eq "Report")
    {
        $subs2 += $rs2010.ListSubscriptions($item.Path);
    }
}
```

##  <a name="script-list-all-subscriptions-associated-with-a-specific-report"></a><a name="bkmk_list_for_1_report"></a> <span data-ttu-id="63342-169">脚本：列出与特定报表关联的全部订阅</span><span class="sxs-lookup"><span data-stu-id="63342-169">Script: List all subscriptions associated with a specific report</span></span>
 <span data-ttu-id="63342-170">此脚本列出与特定报表关联的全部订阅。</span><span class="sxs-lookup"><span data-stu-id="63342-170">This script lists all of the subscriptions associated with a specific report.</span></span> <span data-ttu-id="63342-171">报表路径语法是需要完整 URL 的不同 SharePoint 模式。</span><span class="sxs-lookup"><span data-stu-id="63342-171">The report path syntax is different SharePoint mode which requires a full URL.</span></span> <span data-ttu-id="63342-172">语法示例中使用的报表名称是“title only”，包含一个空格，因此报表名称两边需要带单引号。</span><span class="sxs-lookup"><span data-stu-id="63342-172">In the syntax examples, the report name used is "title only", which contains a space and therefore requires the single quotes around the report name.</span></span>

### <a name="native-mode-syntax"></a><span data-ttu-id="63342-173">纯模式语法</span><span class="sxs-lookup"><span data-stu-id="63342-173">Native mode syntax</span></span>

```cmd
powershell c:\scripts\List_SSRS_One_Reports_Subscriptions.ps1 "[server]/reportserver" "'/reports/title only'" "/"
```

### <a name="sharepoint-mode-syntax"></a><span data-ttu-id="63342-174">SharePoint 模式语法</span><span class="sxs-lookup"><span data-stu-id="63342-174">SharePoint mode syntax</span></span>

```cmd
powershell c:\scripts\List_SSRS_One_Reports_Subscriptions.ps1 "[server]/_vti_bin/reportserver"  "'http://[server]/shared documents/title only.rdl'" "http://[server]"
```

### <a name="script"></a><span data-ttu-id="63342-175">Script</span><span class="sxs-lookup"><span data-stu-id="63342-175">Script</span></span>

```powershell
# Parameters:
#    server      - server and instance name (e.g. myserver/reportserver or myserver/reportserver_db2)
#    reportpath  - path to report in the report server, including report name e.g. /reports/test report >> pass in  "'/reports/title only'"
#    site        - use "/" for default native mode site
Param
(
      [string]$server,
      [string]$reportpath,
      [string]$site
)

$rs2010 = New-WebServiceProxy -Uri "http://$server/ReportService2010.asmx" -Namespace SSRS.ReportingService2010 -UseDefaultCredential ;
$subscriptions += $rs2010.ListSubscriptions($site);

Write-Host " "
Write-Host " "
Write-Host "----- $reportpath 's Subscriptions: "
$subscriptions | select Path, report, Description, Owner, SubscriptionID, lastexecuted,Status | where {$_.path -eq $reportpath}
```

##  <a name="script-change-ownership-of-a-specific-subscription"></a><a name="bkmk_change_all_1_subscription"></a> <span data-ttu-id="63342-176">脚本：更改特定订阅的所有权</span><span class="sxs-lookup"><span data-stu-id="63342-176">Script: Change ownership of a specific subscription</span></span>
 <span data-ttu-id="63342-177">此脚本更改特定订阅的所有权。</span><span class="sxs-lookup"><span data-stu-id="63342-177">This script changes the ownership for a specific subscription.</span></span> <span data-ttu-id="63342-178">订阅由传递到脚本中的 SubscriptionID 标识。</span><span class="sxs-lookup"><span data-stu-id="63342-178">The subscription is identified by the SubscriptionID that you pass into the script.</span></span> <span data-ttu-id="63342-179">可以使用所列订阅脚本之一来确定正确的 SubscriptionID。</span><span class="sxs-lookup"><span data-stu-id="63342-179">You can use one of the list subscription scripts to determine the correct SubscriptionID.</span></span>

### <a name="native-mode-syntax"></a><span data-ttu-id="63342-180">纯模式语法</span><span class="sxs-lookup"><span data-stu-id="63342-180">Native mode syntax</span></span>

```cmd
powershell c:\scripts\Change_SSRS_Owner_One_Subscription.ps1 "[Domain]\[new owner]" "[server]/reportserver" "/" "ac5637a1-9982-4d89-9d69-a72a9c3b3150"
```

### <a name="sharepoint-mode-syntax"></a><span data-ttu-id="63342-181">SharePoint 模式语法</span><span class="sxs-lookup"><span data-stu-id="63342-181">SharePoint mode syntax</span></span>

```cmd
powershell c:\scripts\Change_SSRS_Owner_One_Subscription.ps1 "[Domain]\[new owner]" "[server]/_vti_bin/reportserver" "http://[server]" "9660674b-f020-453f-b1e3-d9ba37624519"
```

### <a name="script"></a><span data-ttu-id="63342-182">Script</span><span class="sxs-lookup"><span data-stu-id="63342-182">Script</span></span>

```powershell
# Parameters:
#    newOwner       - DOMAIN\USER that will own the subscriptions you wish to change
#    server         - server and instance name (e.g. myserver/reportserver or myserver/reportserver_db2)
#    site        - use "/" for default native mode site
#    subscriptionID - guid for the single subscription to change

Param(
    [string]$newOwner,
    [string]$server,
    [string]$site,
    [string]$subscriptionid
   )
$rs2010 = New-WebServiceProxy -Uri "http://$server/ReportService2010.asmx" -Namespace SSRS.ReportingService2010 -UseDefaultCredential;

$subscription += $rs2010.ListSubscriptions($site) | where {$_.SubscriptionID -eq $subscriptionid};

Write-Host " "
Write-Host "----- $subscriptionid's Subscription properties: "
$subscription | select Path, report, Description, SubscriptionID, Owner, Status

$rs2010.ChangeSubscriptionOwner($subscription.SubscriptionID, $newOwner)

#refresh the list
$subscription = $rs2010.ListSubscriptions($site) | where {$_.SubscriptionID -eq $subscriptionid}; # use "/" for default native mode site
Write-Host "----- $subscriptionid's Subscription properties: "
$subscription | select Path, report, Description, SubscriptionID, Owner, Status
```

##  <a name="script-run-fire-a-single-subscription"></a><a name="bkmk_run_1_subscription"></a> <span data-ttu-id="63342-183">脚本：运行（触发）单个订阅</span><span class="sxs-lookup"><span data-stu-id="63342-183">Script: Run (fire) a single subscription</span></span>
 <span data-ttu-id="63342-184">此脚本将使用 FireEvent 方法运行特定订阅。</span><span class="sxs-lookup"><span data-stu-id="63342-184">This script will run a specific subscription using the FireEvent method.</span></span> <span data-ttu-id="63342-185">无论为订阅配置的计划如何，该脚本都将立即运行订阅。</span><span class="sxs-lookup"><span data-stu-id="63342-185">The script will immediately run the subscription regardless of the schedule configured for the subscription.</span></span> <span data-ttu-id="63342-186">EventType 与在报表服务器配置文件 **rsreportserver.config** 中定义的一组已知事件匹配。该脚本为标准订阅使用以下事件类型：</span><span class="sxs-lookup"><span data-stu-id="63342-186">The EventType is matched against the known set of events that are defined in the report server configuration file **rsreportserver.config** The script uses the following event type for standard subscriptions:</span></span>

 `<Event>`

 `<Type>TimedSubscription</Type>`

 `</Event>`

 <span data-ttu-id="63342-187">有关配置文件的详细信息，请参阅 [RSReportServer Configuration File](../report-server/rsreportserver-config-configuration-file.md)。</span><span class="sxs-lookup"><span data-stu-id="63342-187">For more information on the configuration file, see [RSReportServer Configuration File](../report-server/rsreportserver-config-configuration-file.md).</span></span>

 <span data-ttu-id="63342-188">脚本包括延迟逻辑“`Start-Sleep -s 6`”，因此事件触发后尚有时间可供更新状态用于 ListSubscription 方法。</span><span class="sxs-lookup"><span data-stu-id="63342-188">The script includes delay logic "`Start-Sleep -s 6`" so there is time after the event fires, for the updated status to be available with the ListSubscription method.</span></span>

### <a name="native-mode-syntax"></a><span data-ttu-id="63342-189">纯模式语法</span><span class="sxs-lookup"><span data-stu-id="63342-189">Native mode syntax</span></span>

```cmd
powershell c:\scripts\FireSubscription.ps1 "[server]/reportserver" $null "70366e82-2d3c-4edd-a216-b97e51e26de9"
```

### <a name="sharepoint-mode-syntax"></a><span data-ttu-id="63342-190">SharePoint 模式语法</span><span class="sxs-lookup"><span data-stu-id="63342-190">SharePoint mode syntax</span></span>

```cmd
powershell c:\scripts\FireSubscription.ps1 "[server]/_vti_bin/reportserver" "http://[server]" "c3425c72-580d-423e-805a-41cf9799fd25"
```

### <a name="script"></a><span data-ttu-id="63342-191">Script</span><span class="sxs-lookup"><span data-stu-id="63342-191">Script</span></span>

```powershell
# Parameters
#    server         - server and instance name (e.g. myserver/reportserver or myserver/reportserver_db2)
#    site           - use $null for a native mode server
#    subscriptionid - subscription guid

Param(
  [string]$server,
  [string]$site,
  [string]$subscriptionid
  )

$rs2010 = New-WebServiceProxy -Uri "http://$server/ReportService2010.asmx" -Namespace SSRS.ReportingService2010 -UseDefaultCredential ;
#event type is case sensative to what is in the rsreportserver.config
$rs2010.FireEvent("TimedSubscription",$subscriptionid,$site)

Write-Host " "
Write-Host "----- Subscription ($subscriptionid) status: "
#get list of subscriptions and filter to the specific ID to see the Status and LastExecuted
Start-Sleep -s 6 # slight delay in processing so ListSubscription returns the updated Status and LastExecuted
$subscriptions = $rs2010.ListSubscriptions($site); 
$subscriptions | select Status, Path, report, Description, Owner, SubscriptionID, EventType, lastexecuted | where {$_.SubscriptionID -eq $subscriptionid}
```

## <a name="see-also"></a><span data-ttu-id="63342-192">另请参阅</span><span class="sxs-lookup"><span data-stu-id="63342-192">See Also</span></span>
 <span data-ttu-id="63342-193"><xref:ReportService2010.ReportingService2010.ListSubscriptions%2A> <xref:ReportService2010.ReportingService2010.ChangeSubscriptionOwner%2A></span><span class="sxs-lookup"><span data-stu-id="63342-193"><xref:ReportService2010.ReportingService2010.ListSubscriptions%2A> <xref:ReportService2010.ReportingService2010.ChangeSubscriptionOwner%2A></span></span> 
 <xref:ReportService2010.ReportingService2010.ListChildren%2A> 
 <xref:ReportService2010.ReportingService2010.FireEvent%2A>
