---
title: 预加载缓存（报表管理器）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- cache [Reporting Services]
- preloading cache
ms.assetid: 152a1051-8aa5-4c01-bc85-f8be8971b0cd
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b60b74f7ab5c0c843b848c09ee574fd59a99c682
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689777"
---
# <a name="preload-the-cache-report-manager"></a><span data-ttu-id="6b071-102">预加载缓存（报表管理器）</span><span class="sxs-lookup"><span data-stu-id="6b071-102">Preload the Cache (Report Manager)</span></span>
  <span data-ttu-id="6b071-103">您可以通过为共享数据集创建缓存刷新计划，为共享数据集预加载缓存。</span><span class="sxs-lookup"><span data-stu-id="6b071-103">You can preload the cache for a shared dataset by creating a cache refresh plan for the shared dataset.</span></span>  
  
 <span data-ttu-id="6b071-104">您可以通过以下两种方式为报表预加载缓存：</span><span class="sxs-lookup"><span data-stu-id="6b071-104">You can preload the cache for a report in two ways:</span></span>  
  
1.  <span data-ttu-id="6b071-105">为报表创建缓存刷新计划。</span><span class="sxs-lookup"><span data-stu-id="6b071-105">Create a cache refresh plan for the report.</span></span> <span data-ttu-id="6b071-106">这是首选方法。</span><span class="sxs-lookup"><span data-stu-id="6b071-106">This is the preferred method.</span></span>  
  
2.  <span data-ttu-id="6b071-107">使用数据驱动订阅可以用参数化报表的实例预加载缓存。</span><span class="sxs-lookup"><span data-stu-id="6b071-107">Use a data-driven subscription to preload the cache with instances of parameterized reports.</span></span> <span data-ttu-id="6b071-108">这也是在早于 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 的 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]版本中预加载缓存的唯一方法。</span><span class="sxs-lookup"><span data-stu-id="6b071-108">This was the only way to preload the cache in versions of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] earlier than [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)].</span></span> <span data-ttu-id="6b071-109">有关详细信息，请参阅 [缓存报表 (SSRS)](caching-reports-ssrs.md)版本中预加载缓存的唯一方法。</span><span class="sxs-lookup"><span data-stu-id="6b071-109">For more information, see [Caching Reports &#40;SSRS&#41;](caching-reports-ssrs.md).</span></span>  
  
 <span data-ttu-id="6b071-110">必须首先满足以下条件才能缓存报表或共享数据集：</span><span class="sxs-lookup"><span data-stu-id="6b071-110">The following conditions must be met before you can cache a report or a shared dataset:</span></span>  
  
-   <span data-ttu-id="6b071-111">共享数据集或报表必须已启用缓存。</span><span class="sxs-lookup"><span data-stu-id="6b071-111">The shared dataset or the report must have caching enabled.</span></span>  
  
-   <span data-ttu-id="6b071-112">共享数据集或报表的共享数据源必须配置为使用存储凭据或没有凭据。</span><span class="sxs-lookup"><span data-stu-id="6b071-112">The shared data sources for the shared dataset or the report must be configured to use stored credentials or no credentials.</span></span>  
  
-   <span data-ttu-id="6b071-113">必须运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理服务。</span><span class="sxs-lookup"><span data-stu-id="6b071-113">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service must be running.</span></span>  
  
### <a name="to-preload-the-cache-by-creating-a-cache-refresh-plan"></a><span data-ttu-id="6b071-114">通过创建缓存刷新计划预加载缓存</span><span class="sxs-lookup"><span data-stu-id="6b071-114">To preload the cache by creating a cache refresh plan</span></span>  
  
1.  <span data-ttu-id="6b071-115">启动 [报表管理器（SSRS 本机模式）](../report-manager-ssrs-native-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="6b071-115">Start [Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md).</span></span>  
  
2.  <span data-ttu-id="6b071-116">在报表管理器中，导航到 **“内容”** 页，然后导航到要缓存的项。</span><span class="sxs-lookup"><span data-stu-id="6b071-116">In Report Manager, navigate to the **Contents** page, and then navigate to the item that you want to cache.</span></span>  
  
3.  <span data-ttu-id="6b071-117">将光标悬停在项之上，单击下拉列表，然后单击“管理”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6b071-117">Hover over the item, click the drop-down list, and then click **Manage**.</span></span>  
  
4.  <span data-ttu-id="6b071-118">单击 **“缓存刷新选项”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="6b071-118">Click the **Cache Refresh Options** tab.</span></span>  
  
5.  <span data-ttu-id="6b071-119">在工具栏上，单击 **“新建缓存刷新计划”**。</span><span class="sxs-lookup"><span data-stu-id="6b071-119">On the toolbar, click **New Cache Refresh Plan**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6b071-120">如果该项未启用缓存，系统将会提示您启用缓存。</span><span class="sxs-lookup"><span data-stu-id="6b071-120">If the item does not have caching enabled, you will be prompted to enable caching.</span></span> <span data-ttu-id="6b071-121">若要启用缓存，请单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="6b071-121">To enable caching, click **OK**.</span></span>  
  
     <span data-ttu-id="6b071-122">“缓存刷新计划”页将打开。</span><span class="sxs-lookup"><span data-stu-id="6b071-122">The Cache Refresh Plan page opens.</span></span>  
  
6.  <span data-ttu-id="6b071-123">可以根据需要键入刷新计划的说明。</span><span class="sxs-lookup"><span data-stu-id="6b071-123">Optionally type a description for the refresh plan.</span></span>  
  
7.  <span data-ttu-id="6b071-124">对于共享计划，单击 **“共享计划”**，然后选择要使用的计划的名称。</span><span class="sxs-lookup"><span data-stu-id="6b071-124">For a shared schedule, click **Shared schedule**, and then select the name of the schedule to use.</span></span>  
  
     <span data-ttu-id="6b071-125">对于自定义计划，单击“项特定的计划”\*\*\*\*，然后单击“配置”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6b071-125">For a custom schedule, click **Item-specific schedule**, and then click **Configure**.</span></span>  
  
8.  <span data-ttu-id="6b071-126">配置计划</span><span class="sxs-lookup"><span data-stu-id="6b071-126">Configure the schedule</span></span>  
  
9. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-preload-the-cache-with-a-user-specific-report-by-using-a-data-driven-subscription"></a><span data-ttu-id="6b071-127">通过使用数据驱动订阅将用户特定报表预加载到缓存中</span><span class="sxs-lookup"><span data-stu-id="6b071-127">To preload the cache with a user-specific report by using a data-driven subscription</span></span>  
  
1.  <span data-ttu-id="6b071-128">启动 [报表管理器（SSRS 本机模式）](../report-manager-ssrs-native-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="6b071-128">Start [Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md).</span></span>  
  
2.  <span data-ttu-id="6b071-129">在报表管理器中，导航到 **“内容”** 页，然后导航到要为其创建订阅的报表。</span><span class="sxs-lookup"><span data-stu-id="6b071-129">In Report Manager, navigate to the **Contents** page, and then navigate to the report you want to create a subscription for.</span></span>  
  
3.  <span data-ttu-id="6b071-130">单击该报表，单击“订阅”\*\*\*\* 选项卡，再单击“新建数据驱动订阅”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6b071-130">Click the report, click the **Subscriptions** tab, and then click **New Data-Driven Subscription**.</span></span>  
  
4.  <span data-ttu-id="6b071-131">可以根据需要键入订阅的说明。</span><span class="sxs-lookup"><span data-stu-id="6b071-131">Optionally type a description for the subscription.</span></span>  
  
5.  <span data-ttu-id="6b071-132">从 **“指定通知收件人的方式”** 列表中，选择 **Null 传递提供程序**。</span><span class="sxs-lookup"><span data-stu-id="6b071-132">From the **Specify how recipients are notified** list, select **Null Delivery Provider**.</span></span>  
  
6.  <span data-ttu-id="6b071-133">指定数据源类型，再单击 **“下一步”** 以配置数据源。</span><span class="sxs-lookup"><span data-stu-id="6b071-133">Specify a data source type and then click **Next** to configure the data source.</span></span>  
  
7.  <span data-ttu-id="6b071-134">指定用于访问包含订阅服务器数据的数据源的连接类型、连接字符串和凭据。</span><span class="sxs-lookup"><span data-stu-id="6b071-134">Specify the connection type, connection string, and credentials for accessing the data source that contains subscriber data.</span></span> <span data-ttu-id="6b071-135">以下示例演示用于连接到名为 Subscribers 的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库的连接字符串：</span><span class="sxs-lookup"><span data-stu-id="6b071-135">The following example illustrates a connection string used to connect to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database called Subscribers:</span></span>  
  
    ```  
    data source=<servername>; initial catalog=Subscribers  
    ```  
  
8.  <span data-ttu-id="6b071-136">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="6b071-136">Click **Next**.</span></span>  
  
9. <span data-ttu-id="6b071-137">指定检索订阅服务器数据的查询或命令。</span><span class="sxs-lookup"><span data-stu-id="6b071-137">Specify the query or command that retrieves subscriber data.</span></span> <span data-ttu-id="6b071-138">对于处理时间很长的查询，可以根据需要延长超时期限。</span><span class="sxs-lookup"><span data-stu-id="6b071-138">Optionally increase the time-out period for queries that take a long time to process.</span></span> <span data-ttu-id="6b071-139">例如：</span><span class="sxs-lookup"><span data-stu-id="6b071-139">For example:</span></span>  
  
    ```  
    Select * from UserInfo  
    ```  
  
10. <span data-ttu-id="6b071-140">单击 **“验证”** 。</span><span class="sxs-lookup"><span data-stu-id="6b071-140">Click **Validate**.</span></span> <span data-ttu-id="6b071-141">在继续之前，必须验证查询。</span><span class="sxs-lookup"><span data-stu-id="6b071-141">The query must be validated before you continue.</span></span> <span data-ttu-id="6b071-142">在出现 **“查询验证成功”** 消息时，单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="6b071-142">When the **Query validated successfully** message appears, click **Next**.</span></span>  
  
11. <span data-ttu-id="6b071-143">由于不能为 Null 传递提供程序配置传递扩展插件设置，请单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="6b071-143">Because you cannot configure delivery extension settings for the null delivery provider, click **Next**.</span></span>  
  
12. <span data-ttu-id="6b071-144">为订阅指定报表参数值，再单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="6b071-144">Specify report parameter values for the subscription, and click **Next**.</span></span>  
  
13. <span data-ttu-id="6b071-145">指定处理订阅的时间。</span><span class="sxs-lookup"><span data-stu-id="6b071-145">Specify when the subscription is processed.</span></span> <span data-ttu-id="6b071-146">不要选择 **“在报表服务器上更新报表数据时”**。</span><span class="sxs-lookup"><span data-stu-id="6b071-146">Do not choose **When the report data is updated on the report server**.</span></span> <span data-ttu-id="6b071-147">该设置仅适用于快照。</span><span class="sxs-lookup"><span data-stu-id="6b071-147">That setting is for snapshots only.</span></span> <span data-ttu-id="6b071-148">如果要使用预先存在的计划，请选择“根据共享计划”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6b071-148">If want to use a pre-existing schedule, select **On a shared schedule**.</span></span>  
  
     <span data-ttu-id="6b071-149">若要创建自定义计划，请单击 **“根据为此订阅创建的计划”** ，再单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="6b071-149">Or, to create a custom schedule, click **On a schedule created for this subscription** and then click **Next**.</span></span> <span data-ttu-id="6b071-150">配置计划，再单击 **“完成”**。</span><span class="sxs-lookup"><span data-stu-id="6b071-150">Configure the schedule and then click **Finish**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6b071-151">为确保订阅服务器能接收到最新的报表，所配置的计划应与为订阅服务器定义的报表传递计划相一致。</span><span class="sxs-lookup"><span data-stu-id="6b071-151">In order for the subscribers to receive the newest report, the schedule that you configure should be consistent with the report delivery schedule that you have defined for the subscribers.</span></span> <span data-ttu-id="6b071-152">有关详细信息，请参阅[报表管理器（SSRS 本机模式）](../report-manager-ssrs-native-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="6b071-152">For more information, see [Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md).</span></span>  
  
14. <span data-ttu-id="6b071-153">按照下面的步骤为报表配置执行选项。</span><span class="sxs-lookup"><span data-stu-id="6b071-153">Configure the Execution options for the report as follows.</span></span> <span data-ttu-id="6b071-154">在报表页上，单击 **“属性”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="6b071-154">On the report page, click the **Properties** tab.</span></span>  
  
15. <span data-ttu-id="6b071-155">在左框架中，单击 **“执行”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="6b071-155">In the left frame, click the **Execution** tab.</span></span>  
  
16. <span data-ttu-id="6b071-156">在该页上，选择 **“用最新数据呈现此报表”**。</span><span class="sxs-lookup"><span data-stu-id="6b071-156">On the page, select **Render this report with the most recent data**.</span></span>  
  
17. <span data-ttu-id="6b071-157">选择如下两个缓存选项之一并配置过期时间：</span><span class="sxs-lookup"><span data-stu-id="6b071-157">Choose one of the following two cache options and configure the expiration as follows:</span></span>  
  
    -   <span data-ttu-id="6b071-158">若要使缓存的副本在特定的时间段后过期，请单击 **“缓存报表的临时副本。在数分钟之后使报表副本过期”。**</span><span class="sxs-lookup"><span data-stu-id="6b071-158">To make the cached copy expire after a particular time period, click **Cache a temporary copy of the report. Expire copy of report after a number of minutes.**</span></span> <span data-ttu-id="6b071-159">键入报表过期所需的分钟数。</span><span class="sxs-lookup"><span data-stu-id="6b071-159">Type the number of minutes for report expiration.</span></span>  
  
    -   <span data-ttu-id="6b071-160">若要按计划使缓存的副本过期，请单击“缓存报表的临时副本” **。按下列计划使报表副本过期。**</span><span class="sxs-lookup"><span data-stu-id="6b071-160">To make the cached copy expire on a schedule, click **Cache a temporary copy of the report. Expire copy of report on the following schedule.**</span></span> <span data-ttu-id="6b071-161">单击“配置”\*\*\*\*，或选择一个共享计划以设置报表过期计划。</span><span class="sxs-lookup"><span data-stu-id="6b071-161">Click **Configure**, or select a shared schedule to set a schedule for report expiration.</span></span>  
  
18. <span data-ttu-id="6b071-162">单击“应用”。</span><span class="sxs-lookup"><span data-stu-id="6b071-162">Click **Apply**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b071-163">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6b071-163">See Also</span></span>  
 <span data-ttu-id="6b071-164">[Data-Driven Subscriptions](../subscriptions/data-driven-subscriptions.md) </span><span class="sxs-lookup"><span data-stu-id="6b071-164">[Data-Driven Subscriptions](../subscriptions/data-driven-subscriptions.md) </span></span>  
 <span data-ttu-id="6b071-165">[创建数据驱动订阅（SSRS 教程）](../create-a-data-driven-subscription-ssrs-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="6b071-165">[Create a Data-Driven Subscription &#40;SSRS Tutorial&#41;](../create-a-data-driven-subscription-ssrs-tutorial.md) </span></span>  
 <span data-ttu-id="6b071-166">[性能、快照、缓存 &#40;Reporting Services&#41;](performance-snapshots-caching-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="6b071-166">[Performance, Snapshots, Caching &#40;Reporting Services&#41;](performance-snapshots-caching-reporting-services.md) </span></span>  
 <span data-ttu-id="6b071-167">[设置报表处理属性](set-report-processing-properties.md) </span><span class="sxs-lookup"><span data-stu-id="6b071-167">[Set Report Processing Properties](set-report-processing-properties.md) </span></span>  
 [<span data-ttu-id="6b071-168">缓存报表 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="6b071-168">Caching Reports &#40;SSRS&#41;</span></span>](caching-reports-ssrs.md)  
  
  
