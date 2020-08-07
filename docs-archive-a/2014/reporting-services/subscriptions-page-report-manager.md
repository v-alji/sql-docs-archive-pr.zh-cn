---
title: 订阅页 (报表管理器) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: cf3a6bd0-e0b2-4875-a532-63ef34cfa860
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c67895babe99c92b7c09afd8cb75ca88d5cd7553
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691038"
---
# <a name="subscriptions-page-report-manager"></a><span data-ttu-id="c3680-102">“订阅”页（报表管理器）</span><span class="sxs-lookup"><span data-stu-id="c3680-102">Subscriptions Page (Report Manager)</span></span>
  <span data-ttu-id="c3680-103">使用“订阅”页可以列出当前报表或共享数据源的所有订阅。</span><span class="sxs-lookup"><span data-stu-id="c3680-103">Use the Subscriptions page to list all of the subscriptions for the current report or shared data source.</span></span> <span data-ttu-id="c3680-104">如果有足够的权限（指“管理所有订阅”任务），则可以查看所有用户的订阅。</span><span class="sxs-lookup"><span data-stu-id="c3680-104">If you have sufficient permission (as conveyed by the "Manage all subscriptions" task), you can view the subscriptions of all users.</span></span> <span data-ttu-id="c3680-105">否则，此页仅显示您所拥有的订阅。</span><span class="sxs-lookup"><span data-stu-id="c3680-105">Otherwise, this page shows only the subscriptions that you own.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c3680-106">其他页也包含订阅信息。</span><span class="sxs-lookup"><span data-stu-id="c3680-106">Other pages also contain subscription information.</span></span> <span data-ttu-id="c3680-107">有关详细信息，请参阅["我的订阅" 页 &#40;报表管理器&#41;](../../2014/reporting-services/my-subscriptions-page-report-manager.md)在一个位置访问所有订阅，或者在 "新建订阅"[或 "编辑订阅" 页 &#40;报表管理器&#41;](../../2014/reporting-services/new-subscription-or-edit-subscription-page-report-manager.md)创建或编辑订阅。</span><span class="sxs-lookup"><span data-stu-id="c3680-107">For more information, see [My Subscriptions Page &#40;Report Manager&#41;](../../2014/reporting-services/my-subscriptions-page-report-manager.md) to access all your subscriptions in one place or the [New Subscription or Edit Subscription Page &#40;Report Manager&#41;](../../2014/reporting-services/new-subscription-or-edit-subscription-page-report-manager.md) to create or edit a subscription.</span></span>  
  
 <span data-ttu-id="c3680-108">某些选项只有在存在要处理的现有订阅时才可见。</span><span class="sxs-lookup"><span data-stu-id="c3680-108">Some options are visible only if there are existing subscriptions to work with.</span></span> <span data-ttu-id="c3680-109">如果在没有定义任何订阅的情况下从报表访问此页，则此页上仅显示 **“新建订阅”** 和 **“新建数据驱动订阅”** 选项。</span><span class="sxs-lookup"><span data-stu-id="c3680-109">If no subscriptions are defined and you are accessing this page from a report, the **New Subscription** and **New Data-Driven Subscription** are the only options on the page.</span></span>  
  
 <span data-ttu-id="c3680-110">必须确认报表数据源使用的是存储凭据，才能创建新订阅。</span><span class="sxs-lookup"><span data-stu-id="c3680-110">Before you can create a new subscription, you must verify that the report data source uses stored credentials.</span></span> <span data-ttu-id="c3680-111">使用“数据源”属性页可以存储凭据。</span><span class="sxs-lookup"><span data-stu-id="c3680-111">Use the Data Sources properties page to store credentials.</span></span> <span data-ttu-id="c3680-112">有关详细信息，请参阅 "[数据源属性" 页 &#40;报表管理器&#41;](../../2014/reporting-services/data-sources-properties-page-report-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="c3680-112">For more information, see [Data Sources Properties Page &#40;Report Manager&#41;](../../2014/reporting-services/data-sources-properties-page-report-manager.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c3680-113">并非在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]的每个版本中均提供此功能。</span><span class="sxs-lookup"><span data-stu-id="c3680-113">This feature is not available in every edition of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="c3680-114">有关各个版本支持的功能列表 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ，请参阅 SQL Server 2014 的各个[版本支持的功能](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)。</span><span class="sxs-lookup"><span data-stu-id="c3680-114">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="c3680-115">导航</span><span class="sxs-lookup"><span data-stu-id="c3680-115">Navigation</span></span>  
 <span data-ttu-id="c3680-116">使用以下过程导航到用户界面 (UI) 中的这一位置。</span><span class="sxs-lookup"><span data-stu-id="c3680-116">Use the following procedure to navigate to this location in the user interface (UI).</span></span>  
  
### <a name="to-open-the-subscriptions-page-for-report"></a><span data-ttu-id="c3680-117">打开报表的“订阅”页</span><span class="sxs-lookup"><span data-stu-id="c3680-117">To open the Subscriptions page for report</span></span>  
  
1.  <span data-ttu-id="c3680-118">打开报表管理器，找到您要查看或配置订阅的报表。</span><span class="sxs-lookup"><span data-stu-id="c3680-118">Open Report Manager, and locate the report for which you want to view or configure a subscription.</span></span>  
  
2.  <span data-ttu-id="c3680-119">悬停在该报表之上，然后单击下拉箭头。</span><span class="sxs-lookup"><span data-stu-id="c3680-119">Hover over the report, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="c3680-120">在下拉菜单中，单击 **“管理”**。</span><span class="sxs-lookup"><span data-stu-id="c3680-120">In the drop-down menu, click **Manage**.</span></span> <span data-ttu-id="c3680-121">这会打开该报表的“常规”属性页。</span><span class="sxs-lookup"><span data-stu-id="c3680-121">This opens the General properties page for the report.</span></span>  
  
4.  <span data-ttu-id="c3680-122">选择 **“订阅”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="c3680-122">Select the **Subscriptions** tab.</span></span>  
  
## <a name="options"></a><span data-ttu-id="c3680-123">选项</span><span class="sxs-lookup"><span data-stu-id="c3680-123">Options</span></span>  
 <span data-ttu-id="c3680-124">**删除**</span><span class="sxs-lookup"><span data-stu-id="c3680-124">**Delete**</span></span>  
 <span data-ttu-id="c3680-125">单击此选项可删除订阅。</span><span class="sxs-lookup"><span data-stu-id="c3680-125">Click to delete a subscription.</span></span> <span data-ttu-id="c3680-126">删除订阅之前，必须选中要删除的每个订阅旁边的复选框。</span><span class="sxs-lookup"><span data-stu-id="c3680-126">Before you can delete a subscription, select the check box next to each subscription that you want to delete.</span></span>  
  
 <span data-ttu-id="c3680-127">**新订阅**</span><span class="sxs-lookup"><span data-stu-id="c3680-127">**New Subscription**</span></span>  
 <span data-ttu-id="c3680-128">单击此选项可创建当前报表的新订阅。</span><span class="sxs-lookup"><span data-stu-id="c3680-128">Click to create a new subscription to the current report.</span></span> <span data-ttu-id="c3680-129">此按钮在报表使用存储的凭据或不使用凭据时启用。</span><span class="sxs-lookup"><span data-stu-id="c3680-129">This button is enabled when the report uses stored credentials or no credentials.</span></span> <span data-ttu-id="c3680-130">当通过共享数据源打开订阅页时，此按钮不可用。</span><span class="sxs-lookup"><span data-stu-id="c3680-130">This button is not available when you open the Subscriptions page for a shared data source.</span></span>  
  
 <span data-ttu-id="c3680-131">**“新建数据驱动订阅”**</span><span class="sxs-lookup"><span data-stu-id="c3680-131">**New Data-Driven Subscription**</span></span>  
 <span data-ttu-id="c3680-132">单击此选项可通过命令或查询针对包含此信息的数据存储区生成订阅服务器列表和传递选项。</span><span class="sxs-lookup"><span data-stu-id="c3680-132">Click to generate a subscriber list and delivery options from a command or query against a data store that contains this information.</span></span> <span data-ttu-id="c3680-133">此按钮在报表使用存储的凭据或不使用凭据时启用。</span><span class="sxs-lookup"><span data-stu-id="c3680-133">This button is enabled when the report uses stored credentials or no credentials.</span></span> <span data-ttu-id="c3680-134">当通过共享数据源打开订阅页时，此按钮不可用。</span><span class="sxs-lookup"><span data-stu-id="c3680-134">This button is not available when you open the Subscriptions page for a shared data source.</span></span>  
  
 <span data-ttu-id="c3680-135">**编辑**</span><span class="sxs-lookup"><span data-stu-id="c3680-135">**Edit**</span></span>  
 <span data-ttu-id="c3680-136">单击此选项可查看或编辑说明。</span><span class="sxs-lookup"><span data-stu-id="c3680-136">Click to view or edit the description.</span></span>  
  
 <span data-ttu-id="c3680-137">**Report**</span><span class="sxs-lookup"><span data-stu-id="c3680-137">**Report**</span></span>  
 <span data-ttu-id="c3680-138">从共享数据源打开此页时，此列标识为其定义了订阅的报表。</span><span class="sxs-lookup"><span data-stu-id="c3680-138">When you open this page from a shared data source, this column identifies the report for which the subscription is defined.</span></span> <span data-ttu-id="c3680-139">**“文件夹”** 列用于标识报表位置。</span><span class="sxs-lookup"><span data-stu-id="c3680-139">The **Folder** column identifies the location of the report.</span></span>  
  
 <span data-ttu-id="c3680-140">**描述**</span><span class="sxs-lookup"><span data-stu-id="c3680-140">**Description**</span></span>  
 <span data-ttu-id="c3680-141">显示订阅的说明。</span><span class="sxs-lookup"><span data-stu-id="c3680-141">Shows a description of the subscription.</span></span>  
  
 <span data-ttu-id="c3680-142">触发器\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="c3680-142">**Trigger**</span></span>  
 <span data-ttu-id="c3680-143">标识导致订阅运行的条件。</span><span class="sxs-lookup"><span data-stu-id="c3680-143">Identifies criteria that cause the subscription to run.</span></span> <span data-ttu-id="c3680-144">**TimedSubscription** 触发器基于定义订阅运行时间的计划。</span><span class="sxs-lookup"><span data-stu-id="c3680-144">A **TimedSubscription** trigger is based on a schedule that defines when the subscription runs.</span></span> <span data-ttu-id="c3680-145">**SnapshotUpdated** 触发器基于对报表快照的更新操作。</span><span class="sxs-lookup"><span data-stu-id="c3680-145">A **SnapshotUpdated** trigger is based on an update to a report snapshot.</span></span>  
  
 <span data-ttu-id="c3680-146">**所有者**</span><span class="sxs-lookup"><span data-stu-id="c3680-146">**Owner**</span></span>  
 <span data-ttu-id="c3680-147">显示创建订阅的用户的名称。</span><span class="sxs-lookup"><span data-stu-id="c3680-147">Shows the name of the user who created the subscription.</span></span>  
  
 <span data-ttu-id="c3680-148">**上次运行时间**</span><span class="sxs-lookup"><span data-stu-id="c3680-148">**Last Run**</span></span>  
 <span data-ttu-id="c3680-149">显示上次处理订阅的时间。</span><span class="sxs-lookup"><span data-stu-id="c3680-149">Shows the last time that the subscription was processed.</span></span>  
  
 <span data-ttu-id="c3680-150">**Status**</span><span class="sxs-lookup"><span data-stu-id="c3680-150">**Status**</span></span>  
 <span data-ttu-id="c3680-151">显示订阅的状态。</span><span class="sxs-lookup"><span data-stu-id="c3680-151">Shows the status of the subscription.</span></span> <span data-ttu-id="c3680-152">通常，状态值为“新建”或订阅上次运行的日期和时间。</span><span class="sxs-lookup"><span data-stu-id="c3680-152">Usually, the status value is either New or the date and time at which the subscription last ran.</span></span>  
  
 <span data-ttu-id="c3680-153">当订阅包括指向不再有效的加密值（即指向用于运行报表的已存储凭据）的指针时，将出现“错误数据”状态值。</span><span class="sxs-lookup"><span data-stu-id="c3680-153">A status value of "Bad Data" occurs when the subscription includes a pointer to encrypted values that are no longer valid (that is, to the stored credentials used to run the report).</span></span> <span data-ttu-id="c3680-154">在报表服务器上重新创建用于对数据进行加密和解密的对称密钥后，现有的加密值将无法使用。</span><span class="sxs-lookup"><span data-stu-id="c3680-154">Existing encrypted values become unusable when the symmetric keys used to encrypt and decrypt data are recreated on the report server.</span></span>  
  
 <span data-ttu-id="c3680-155">如果订阅已停用，将无法对其进行处理。</span><span class="sxs-lookup"><span data-stu-id="c3680-155">A subscription cannot be processed if it has been deactivated.</span></span> <span data-ttu-id="c3680-156">若要更新订阅并使其可操作，请先打开订阅，然后保存即可。</span><span class="sxs-lookup"><span data-stu-id="c3680-156">To update the subscription and make it operational, open and then save the subscription.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3680-157">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c3680-157">See Also</span></span>  
 <span data-ttu-id="c3680-158">[报表管理器（SSRS 本机模式）](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="c3680-158">[Report Manager  &#40;SSRS Native Mode&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="c3680-159">[在纯模式下创建、修改和删除标准订阅 &#40;Reporting Services&#41;](subscriptions/create-and-manage-subscriptions-for-native-mode-report-servers.md) </span><span class="sxs-lookup"><span data-stu-id="c3680-159">[Create, Modify, and Delete Standard Subscriptions &#40;Reporting Services in Native Mode&#41;](subscriptions/create-and-manage-subscriptions-for-native-mode-report-servers.md) </span></span>  
 <span data-ttu-id="c3680-160">[创建、修改和删除计划](subscriptions/create-modify-and-delete-schedules.md) </span><span class="sxs-lookup"><span data-stu-id="c3680-160">[Create, Modify, and Delete Schedules](subscriptions/create-modify-and-delete-schedules.md) </span></span>  
 [<span data-ttu-id="c3680-161">报表管理器的 F1 帮助</span><span class="sxs-lookup"><span data-stu-id="c3680-161">Report Manager F1 Help</span></span>](../../2014/reporting-services/report-manager-f1-help.md)  
  
  
