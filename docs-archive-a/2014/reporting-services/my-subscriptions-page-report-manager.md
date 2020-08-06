---
title: "\"我的订阅\" 页 (报表管理器) |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 491a85a3-f323-4155-a0a8-de2779899995
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 891796ec491b157f3c9bb5b4adfd15daedbc7c88
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692785"
---
# <a name="my-subscriptions-page-report-manager"></a><span data-ttu-id="80ff4-102">“我的订阅”页（报表管理器）</span><span class="sxs-lookup"><span data-stu-id="80ff4-102">My Subscriptions Page (Report Manager)</span></span>
  <span data-ttu-id="80ff4-103">使用“我的订阅”页可以在同一位置查看您的所有订阅。</span><span class="sxs-lookup"><span data-stu-id="80ff4-103">Use the My Subscriptions page to view all of your subscriptions in one place.</span></span> <span data-ttu-id="80ff4-104">使用此页可以访问、修改或删除您拥有的任何订阅。</span><span class="sxs-lookup"><span data-stu-id="80ff4-104">From this page, you can access and modify or delete any subscription that you own.</span></span> <span data-ttu-id="80ff4-105">您只拥有您所创建的订阅。</span><span class="sxs-lookup"><span data-stu-id="80ff4-105">You own only the subscriptions that you create.</span></span> <span data-ttu-id="80ff4-106">您不能访问其他用户的订阅，也不能访问您可使用但不能拥有的订阅（例如，如果您的名称已添加到由另一个用户定义的某个现有订阅中）。</span><span class="sxs-lookup"><span data-stu-id="80ff4-106">You cannot access those of other users, nor can you access subscriptions that you use but do not own (for example, if your name has been added to an existing subscription defined by another user).</span></span> <span data-ttu-id="80ff4-107">您不能从本页创建订阅。</span><span class="sxs-lookup"><span data-stu-id="80ff4-107">You cannot create subscriptions from this page.</span></span> <span data-ttu-id="80ff4-108">有关创建订阅的详细信息，请参阅 "[新建订阅" 或 "编辑订阅" 页 &#40;报表管理器&#41;](../../2014/reporting-services/new-subscription-or-edit-subscription-page-report-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="80ff4-108">For more information about creating subscriptions, see the [New Subscription or Edit Subscription Page &#40;Report Manager&#41;](../../2014/reporting-services/new-subscription-or-edit-subscription-page-report-manager.md).</span></span>  
  
 <span data-ttu-id="80ff4-109">默认情况下，订阅按报表名的字母顺序排列。</span><span class="sxs-lookup"><span data-stu-id="80ff4-109">By default, subscriptions are sorted in alphabetical order by report name.</span></span> <span data-ttu-id="80ff4-110">单击不同的列标题可以更改订阅的排序方式。</span><span class="sxs-lookup"><span data-stu-id="80ff4-110">Click a different column heading to change how subscriptions are sorted.</span></span> <span data-ttu-id="80ff4-111">如果没有任何订阅或者禁用了创建或管理订阅的权限，则该页不显示任何订阅。</span><span class="sxs-lookup"><span data-stu-id="80ff4-111">If you have no subscriptions or if permission to create or manage subscriptions is disabled, no subscriptions appear on the page.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="80ff4-112">并非在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]的每个版本中均提供此功能。</span><span class="sxs-lookup"><span data-stu-id="80ff4-112">This feature is not available in every edition of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="80ff4-113">有关各个版本支持的功能列表 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ，请参阅 SQL Server 2014 的各个[版本支持的功能](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)。</span><span class="sxs-lookup"><span data-stu-id="80ff4-113">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="80ff4-114">导航</span><span class="sxs-lookup"><span data-stu-id="80ff4-114">Navigation</span></span>  
 <span data-ttu-id="80ff4-115">使用以下过程导航到用户界面 (UI) 中的这一位置。</span><span class="sxs-lookup"><span data-stu-id="80ff4-115">Use the following procedure to navigate to this location in the user interface (UI).</span></span>  
  
### <a name="to-open-the-my-subscriptions-page"></a><span data-ttu-id="80ff4-116">打开“我的订阅”页</span><span class="sxs-lookup"><span data-stu-id="80ff4-116">To open the My Subscriptions page</span></span>  
  
1.  <span data-ttu-id="80ff4-117">打开报表管理器。</span><span class="sxs-lookup"><span data-stu-id="80ff4-117">Open Report Manager.</span></span>  
  
2.  <span data-ttu-id="80ff4-118">在页面顶部的右角，单击“我的订阅”。</span><span class="sxs-lookup"><span data-stu-id="80ff4-118">At the top of the page, in the right-hand corner, click My Subscriptions.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="80ff4-119">“我的订阅”始终可用，即使不具备创建订阅的权限也可使用。</span><span class="sxs-lookup"><span data-stu-id="80ff4-119">My Subscriptions is always available, even if you lack permission to create subscriptions.</span></span>  
  
## <a name="options"></a><span data-ttu-id="80ff4-120">选项</span><span class="sxs-lookup"><span data-stu-id="80ff4-120">Options</span></span>  
 <span data-ttu-id="80ff4-121">**删除**</span><span class="sxs-lookup"><span data-stu-id="80ff4-121">**Delete**</span></span>  
 <span data-ttu-id="80ff4-122">选中要删除的每个订阅旁边的复选框，再单击 **“删除”**。</span><span class="sxs-lookup"><span data-stu-id="80ff4-122">Select the check box next to each subscription that you want to delete and click **Delete**.</span></span>  
  
 <span data-ttu-id="80ff4-123">**编辑**</span><span class="sxs-lookup"><span data-stu-id="80ff4-123">**Edit**</span></span>  
 <span data-ttu-id="80ff4-124">单击此选项可查看或编辑说明。</span><span class="sxs-lookup"><span data-stu-id="80ff4-124">Click to view or edit the description.</span></span>  
  
 <span data-ttu-id="80ff4-125">**Report**</span><span class="sxs-lookup"><span data-stu-id="80ff4-125">**Report**</span></span>  
 <span data-ttu-id="80ff4-126">显示在订阅中指定的报表。</span><span class="sxs-lookup"><span data-stu-id="80ff4-126">Shows the report that is specified in the subscription.</span></span> <span data-ttu-id="80ff4-127">单击报表名称可以查看该报表。</span><span class="sxs-lookup"><span data-stu-id="80ff4-127">Click the report name to view the report.</span></span>  
  
 <span data-ttu-id="80ff4-128">**说明**</span><span class="sxs-lookup"><span data-stu-id="80ff4-128">**Description**</span></span>  
 <span data-ttu-id="80ff4-129">显示订阅的说明。</span><span class="sxs-lookup"><span data-stu-id="80ff4-129">Shows a description of the subscription.</span></span> <span data-ttu-id="80ff4-130">单击说明可以查看或编辑报表的订阅信息。</span><span class="sxs-lookup"><span data-stu-id="80ff4-130">Click the description to view or edit the subscription information for the report.</span></span>  
  
 <span data-ttu-id="80ff4-131">**文件夹**</span><span class="sxs-lookup"><span data-stu-id="80ff4-131">**Folder**</span></span>  
 <span data-ttu-id="80ff4-132">显示包含在订阅中指定的报表的文件夹。</span><span class="sxs-lookup"><span data-stu-id="80ff4-132">Shows the folder that contains the report that is specified in the subscription.</span></span> <span data-ttu-id="80ff4-133">单击文件夹名称可以查看该文件夹的内容。</span><span class="sxs-lookup"><span data-stu-id="80ff4-133">Click the folder name to view the contents of the folder.</span></span>  
  
 <span data-ttu-id="80ff4-134">触发器\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="80ff4-134">**Trigger**</span></span>  
 <span data-ttu-id="80ff4-135">标识导致订阅运行的条件。</span><span class="sxs-lookup"><span data-stu-id="80ff4-135">Identifies criteria that cause the subscription to run.</span></span> <span data-ttu-id="80ff4-136">**TimedSubscription** 触发器基于定义订阅运行时间的计划。</span><span class="sxs-lookup"><span data-stu-id="80ff4-136">A **TimedSubscription** trigger is based on a schedule that defines when the subscription runs.</span></span> <span data-ttu-id="80ff4-137">**SnapshotUpdated** 触发器基于对报表快照的更新操作。</span><span class="sxs-lookup"><span data-stu-id="80ff4-137">A **SnapshotUpdated** trigger is based on an update to a report snapshot.</span></span>  
  
 <span data-ttu-id="80ff4-138">**上次运行时间**</span><span class="sxs-lookup"><span data-stu-id="80ff4-138">**Last Run**</span></span>  
 <span data-ttu-id="80ff4-139">显示上次处理订阅的时间。</span><span class="sxs-lookup"><span data-stu-id="80ff4-139">Shows the last time that the subscription was processed.</span></span>  
  
 <span data-ttu-id="80ff4-140">**Status**</span><span class="sxs-lookup"><span data-stu-id="80ff4-140">**Status**</span></span>  
 <span data-ttu-id="80ff4-141">显示订阅的状态。</span><span class="sxs-lookup"><span data-stu-id="80ff4-141">Shows the status of the subscription.</span></span> <span data-ttu-id="80ff4-142">通常，状态值为“新建”或订阅上次运行的日期和时间。</span><span class="sxs-lookup"><span data-stu-id="80ff4-142">Usually, the status value is either "New" or the date and time at which the subscription last ran.</span></span>  
  
 <span data-ttu-id="80ff4-143">当订阅包括指向不再有效的加密值（即指向用于运行报表的已存储凭据）的指针时，将出现“错误数据”状态值。</span><span class="sxs-lookup"><span data-stu-id="80ff4-143">A status value of "Bad Data" occurs when the subscription includes a pointer to encrypted values that are no longer valid (that is, to the stored credentials used to run the report).</span></span> <span data-ttu-id="80ff4-144">在报表服务器上重新创建用于对数据进行加密和解密的对称密钥后，现有的加密值将无法使用。</span><span class="sxs-lookup"><span data-stu-id="80ff4-144">Existing encrypted values become unusable when the symmetric keys used to encrypt and decrypt data are recreated on the report server.</span></span>  
  
 <span data-ttu-id="80ff4-145">如果订阅已停用，将无法对其进行处理。</span><span class="sxs-lookup"><span data-stu-id="80ff4-145">A subscription cannot be processed if it has been deactivated.</span></span> <span data-ttu-id="80ff4-146">若要更新订阅并使其可操作，请先打开订阅，然后保存即可。</span><span class="sxs-lookup"><span data-stu-id="80ff4-146">To update the subscription and make it operational, open and then save the subscription.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80ff4-147">另请参阅</span><span class="sxs-lookup"><span data-stu-id="80ff4-147">See Also</span></span>  
 <span data-ttu-id="80ff4-148">[订阅和传递 (Reporting Services)](subscriptions/subscriptions-and-delivery-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="80ff4-148">[Subscriptions and Delivery &#40;Reporting Services&#41;](subscriptions/subscriptions-and-delivery-reporting-services.md) </span></span>  
 [<span data-ttu-id="80ff4-149">报表管理器的 F1 帮助</span><span class="sxs-lookup"><span data-stu-id="80ff4-149">Report Manager F1 Help</span></span>](../../2014/reporting-services/report-manager-f1-help.md)  
  
  
