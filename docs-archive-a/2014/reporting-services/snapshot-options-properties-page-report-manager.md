---
title: "\"快照选项\" 属性页 (报表管理器) |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: f6641f59-5267-4f57-8957-63b93d1a9679
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3025b23dfe498a92c2ce1d8535229d8d23dfd429
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687415"
---
# <a name="snapshot-options-properties-page-report-manager"></a><span data-ttu-id="1753a-102">“快照选项”属性页（报表管理器）</span><span class="sxs-lookup"><span data-stu-id="1753a-102">Snapshot Options Properties Page (Report Manager)</span></span>
  <span data-ttu-id="1753a-103">使用“快照选项”属性页可以计划将报表快照添加到报表历史记录的时间，以及设置报表历史记录中存储的报表快照的数量限制。</span><span class="sxs-lookup"><span data-stu-id="1753a-103">Use the Snapshot Options properties page to schedule report snapshots to be added to report history, and to set limits on the number of report snapshots that are stored in report history.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1753a-104">并非在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]的每个版本中均提供此功能。</span><span class="sxs-lookup"><span data-stu-id="1753a-104">This feature is not available in every edition of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="1753a-105">有关各个版本支持的功能列表 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ，请参阅[其他数据库服务](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md#Add_DBServices)。</span><span class="sxs-lookup"><span data-stu-id="1753a-105">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], see [Additional Database Services](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md#Add_DBServices).</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="1753a-106">导航</span><span class="sxs-lookup"><span data-stu-id="1753a-106">Navigation</span></span>  
 <span data-ttu-id="1753a-107">使用以下过程导航到用户界面 (UI) 中的这一位置。</span><span class="sxs-lookup"><span data-stu-id="1753a-107">Use the following procedure to navigate to this location in the user interface (UI).</span></span>  
  
### <a name="to-open-the-snapshot-options-properties-page-for-a-report"></a><span data-ttu-id="1753a-108">打开报表的“快照选项”属性页</span><span class="sxs-lookup"><span data-stu-id="1753a-108">To open the Snapshot Options properties page for a report</span></span>  
  
1.  <span data-ttu-id="1753a-109">打开报表管理器，找到您要配置报表快照属性的报表。</span><span class="sxs-lookup"><span data-stu-id="1753a-109">Open Report Manager, and locate the report for which you want to configure report snapshot properties.</span></span>  
  
2.  <span data-ttu-id="1753a-110">悬停在该报表之上，然后单击下拉箭头。</span><span class="sxs-lookup"><span data-stu-id="1753a-110">Hover over the report, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="1753a-111">在下拉菜单中，单击 **“管理”**。</span><span class="sxs-lookup"><span data-stu-id="1753a-111">In the drop-down menu, click **Manage**.</span></span> <span data-ttu-id="1753a-112">这会打开该报表的“常规”属性页。</span><span class="sxs-lookup"><span data-stu-id="1753a-112">This opens the General properties page for the report.</span></span>  
  
4.  <span data-ttu-id="1753a-113">选择 **“快照选项”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="1753a-113">Select the **Snapshot Options** tab.</span></span>  
  
## <a name="options"></a><span data-ttu-id="1753a-114">选项</span><span class="sxs-lookup"><span data-stu-id="1753a-114">Options</span></span>  
 <span data-ttu-id="1753a-115">**允许手动创建报表历史记录**</span><span class="sxs-lookup"><span data-stu-id="1753a-115">**Allow report history to be created manually**</span></span>  
 <span data-ttu-id="1753a-116">选中此复选框可以根据需要将快照添加到报表历史记录中。</span><span class="sxs-lookup"><span data-stu-id="1753a-116">Select this check box to add snapshots to report history as needed.</span></span> <span data-ttu-id="1753a-117">选中此复选框后，“历史记录”页上将显示 **“新建快照”** 按钮。</span><span class="sxs-lookup"><span data-stu-id="1753a-117">Selecting this check box causes the **New Snapshot** button to appear on the History page.</span></span>  
  
 <span data-ttu-id="1753a-118">**将所有报表执行快照存储在报表历史记录中**</span><span class="sxs-lookup"><span data-stu-id="1753a-118">**Store all report execution snapshots in report history**</span></span>  
 <span data-ttu-id="1753a-119">选中此复选框可以根据报表执行属性将您生成的报表快照添加到报表历史记录中。</span><span class="sxs-lookup"><span data-stu-id="1753a-119">Select this check box to copy a report snapshot that you generate based on report execution properties to report history.</span></span> <span data-ttu-id="1753a-120">您可以设置报表执行属性以便从生成的快照运行报表。</span><span class="sxs-lookup"><span data-stu-id="1753a-120">You can set report execution properties to run a report from a generated snapshot.</span></span> <span data-ttu-id="1753a-121">设置此报表历史记录属性后，您可以将一段时间内生成的所有报表快照的副本放置在报表历史记录中，以跟踪这些报表快照。</span><span class="sxs-lookup"><span data-stu-id="1753a-121">By setting this report history property, you can keep a record of all reports snapshots that are generated over time by placing copies of them in report history.</span></span>  
  
 <span data-ttu-id="1753a-122">**使用下列计划将快照添加到报表历史记录中**</span><span class="sxs-lookup"><span data-stu-id="1753a-122">**Use the following schedule to add snapshots to report history**</span></span>  
 <span data-ttu-id="1753a-123">选中此复选框可以按计划将快照添加到报表历史记录中。</span><span class="sxs-lookup"><span data-stu-id="1753a-123">Select this check box to add snapshots to report history on a scheduled basis.</span></span> <span data-ttu-id="1753a-124">您可以创建专门用于此用途的计划，也可以选择包含您所需的计划信息的预定义共享计划。</span><span class="sxs-lookup"><span data-stu-id="1753a-124">You can create a schedule that is used exclusively for this purpose, or you can select a predefined shared schedule if one contains the schedule information you want.</span></span>  
  
 <span data-ttu-id="1753a-125">**选择要保留的快照数**</span><span class="sxs-lookup"><span data-stu-id="1753a-125">**Select the number of snapshots to keep**</span></span>  
 <span data-ttu-id="1753a-126">从以下选项中进行选择，以控制保留在报表历史记录中的报表数。</span><span class="sxs-lookup"><span data-stu-id="1753a-126">Select from the following options to control the number of reports that are kept in report history.</span></span> <span data-ttu-id="1753a-127">各个报表的报表历史记录设置可以不同。</span><span class="sxs-lookup"><span data-stu-id="1753a-127">Report history settings can vary for each report.</span></span>  
  
-   <span data-ttu-id="1753a-128">选择 **“使用默认设置”** 可以保留默认设置。</span><span class="sxs-lookup"><span data-stu-id="1753a-128">Select **Use default setting** to retain the default setting.</span></span> <span data-ttu-id="1753a-129">报表服务器管理员控制报表历史记录存储的主设置。</span><span class="sxs-lookup"><span data-stu-id="1753a-129">The report server administrator controls a master setting for report history storage.</span></span> <span data-ttu-id="1753a-130">如果选择此选项，将从该主设置获取保留的快照数。</span><span class="sxs-lookup"><span data-stu-id="1753a-130">If you choose this option, the number of snapshots that are retained is obtained from this master setting.</span></span>  
  
-   <span data-ttu-id="1753a-131">选择 **“不限制报表历史记录中保留的快照数”** 可以保留所有的报表历史记录快照。</span><span class="sxs-lookup"><span data-stu-id="1753a-131">Select **Keep an unlimited number of snapshots in report history** to retain all report history snapshots.</span></span> <span data-ttu-id="1753a-132">要减少报表历史记录的大小，必须手动删除快照。</span><span class="sxs-lookup"><span data-stu-id="1753a-132">You must manually delete snapshots to reduce the size of report history.</span></span>  
  
-   <span data-ttu-id="1753a-133">选择 **“限制报表历史记录的副本数”** 可以保留设定数量的快照。</span><span class="sxs-lookup"><span data-stu-id="1753a-133">Select **Limit the copies of report history** to retain a set number of snapshots.</span></span> <span data-ttu-id="1753a-134">到达限制后，将从报表历史记录中删除较旧的副本以便为新副本腾出空间。</span><span class="sxs-lookup"><span data-stu-id="1753a-134">When the limit is reached, older copies are removed from report history to make room for newer copies.</span></span>  
  
 <span data-ttu-id="1753a-135">报表历史记录存储在报表服务器数据库中。</span><span class="sxs-lookup"><span data-stu-id="1753a-135">Report history is stored in the report server database.</span></span> <span data-ttu-id="1753a-136">如果要保留大型报表或许多报表的历史记录，请考虑限制报表历史记录的量，以帮助管理报表服务器数据库的磁盘空间要求。</span><span class="sxs-lookup"><span data-stu-id="1753a-136">If you have large reports or numerous reports for which you want to maintain history, consider limiting the amount of report history to help manage the disk space requirements of the report server database.</span></span>  
  
 <span data-ttu-id="1753a-137">**应用**</span><span class="sxs-lookup"><span data-stu-id="1753a-137">**Apply**</span></span>  
 <span data-ttu-id="1753a-138">单击此选项可保存所做的更改。</span><span class="sxs-lookup"><span data-stu-id="1753a-138">Click to save your changes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1753a-139">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1753a-139">See Also</span></span>  
 <span data-ttu-id="1753a-140">[将快照添加到报表历史记录 &#40;报表管理器&#41;](report-server/add-a-snapshot-to-report-history-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="1753a-140">[Add a Snapshot to Report History &#40;Report Manager&#41;](report-server/add-a-snapshot-to-report-history-report-manager.md) </span></span>  
 <span data-ttu-id="1753a-141">[报表管理器（SSRS 本机模式）](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="1753a-141">[Report Manager  &#40;SSRS Native Mode&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="1753a-142">[创建、修改和删除报表历史记录中的快照](report-server/create-modify-and-delete-snapshots-in-report-history.md) </span><span class="sxs-lookup"><span data-stu-id="1753a-142">[Create, Modify, and Delete Snapshots in Report History](report-server/create-modify-and-delete-snapshots-in-report-history.md) </span></span>  
 [<span data-ttu-id="1753a-143">报表管理器的 F1 帮助</span><span class="sxs-lookup"><span data-stu-id="1753a-143">Report Manager F1 Help</span></span>](../../2014/reporting-services/report-manager-f1-help.md)  
  
  
