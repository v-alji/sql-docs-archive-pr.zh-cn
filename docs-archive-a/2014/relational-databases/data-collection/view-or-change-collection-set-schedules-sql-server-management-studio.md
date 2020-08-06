---
title: 查看或更改收集组计划 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.dc.collectionsetprop.uploads.f1
- sql12.swb.dc.collectionsetprop.general.f1
- sql12.swb.dc.collectionsetprop.description.f1
helpviewer_keywords:
- collection sets [SQL Server], changing schedules
- schedules [SQL Server], changing collection set
- collection sets [SQL Server], viewing schedules
- schedules [SQL Server], viewing collection set
ms.assetid: 26336c98-78c5-414f-8d6a-574fc3af60c4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2eb1acf0346b3e16bd1d54829abbc070e1d9d63b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589708"
---
# <a name="view-or-change-collection-set-schedules-sql-server-management-studio"></a><span data-ttu-id="495d3-102">查看或更改收集组计划 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="495d3-102">View or Change Collection Set Schedules (SQL Server Management Studio)</span></span>
  <span data-ttu-id="495d3-103">可以使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]查看或更改收集组计划。</span><span class="sxs-lookup"><span data-stu-id="495d3-103">You can view or change collection set schedules by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="495d3-104">收集模式（缓存或非缓存）决定变更计划的方式。</span><span class="sxs-lookup"><span data-stu-id="495d3-104">The collection mode, cached or non-cached, determines how you can make changes to a schedule.</span></span> <span data-ttu-id="495d3-105">缓存模式使用不同的计划进行收集和上载。</span><span class="sxs-lookup"><span data-stu-id="495d3-105">Cached mode uses separate schedules for collection and upload.</span></span> <span data-ttu-id="495d3-106">非缓存模式使用同一计划进行收集和上载。</span><span class="sxs-lookup"><span data-stu-id="495d3-106">Non-cached mode uses the same schedule for collection and upload.</span></span> <span data-ttu-id="495d3-107">每个系统数据收集组的收集模式类型如下：</span><span class="sxs-lookup"><span data-stu-id="495d3-107">The type of collection mode for each of the System Datacollection sets is as follows:</span></span>  
  
-   <span data-ttu-id="495d3-108">“磁盘使用情况”使用非缓存收集模式。</span><span class="sxs-lookup"><span data-stu-id="495d3-108">**Disk Usage** uses non-cached collection mode.</span></span>  
  
-   <span data-ttu-id="495d3-109">**“查询统计信息”** 使用缓存收集模式。</span><span class="sxs-lookup"><span data-stu-id="495d3-109">**Query Statistics** uses cached collection mode.</span></span>  
  
-   <span data-ttu-id="495d3-110">**“服务器活动”** 使用缓存收集模式。</span><span class="sxs-lookup"><span data-stu-id="495d3-110">**Server Activity** uses cached collection mode.</span></span>  
  
### <a name="to-view-collection-set-schedules"></a><span data-ttu-id="495d3-111">查看收集组计划</span><span class="sxs-lookup"><span data-stu-id="495d3-111">To view collection set schedules</span></span>  
  
1.  <span data-ttu-id="495d3-112">在对象资源管理器中，依次展开 **“管理”** 节点、 **“数据收集”** 和 **“系统数据收集组”** 。</span><span class="sxs-lookup"><span data-stu-id="495d3-112">In Object Explorer, expand the **Management** node, expand **Data Collection**, and then expand **System Data Collection Sets**.</span></span>  
  
2.  <span data-ttu-id="495d3-113">右键单击收集组名称，然后单击“属性”[以便打开](#CollectionSet)“数据收集组属性”对话框。</span><span class="sxs-lookup"><span data-stu-id="495d3-113">Right-click a collection set name, and then click **Properties** to open the [Data Collection Set Properties](#CollectionSet) dialog box.</span></span>  
  
### <a name="to-change-the-schedules-for-a-cached-mode-collection-set"></a><span data-ttu-id="495d3-114">更改缓存模式收集组的计划</span><span class="sxs-lookup"><span data-stu-id="495d3-114">To change the schedules for a cached mode collection set</span></span>  
  
1.  <span data-ttu-id="495d3-115">在对象资源管理器中，依次展开 **“管理”** 节点、 **“数据收集”** 和 **“系统数据收集组”** 。</span><span class="sxs-lookup"><span data-stu-id="495d3-115">In Object Explorer, expand the **Management** node, expand **Data Collection**, and then expand **System Data Collection Sets**.</span></span>  
  
2.  <span data-ttu-id="495d3-116">右键单击使用缓存模式的收集组（如“查询统计信息”），然后单击“属性”以便打开“[数据收集组属性](#CollectionSet)”对话框。 </span><span class="sxs-lookup"><span data-stu-id="495d3-116">Right-click a collection set that uses cached mode, such as **Query Statistics**, and then click **Properties** to open the [Data Collection Set Properties](#CollectionSet) dialog box.</span></span>  
  
3.  <span data-ttu-id="495d3-117">可以在 **“常规”** 页上更改收集频率。</span><span class="sxs-lookup"><span data-stu-id="495d3-117">You can change the collection frequency on the **General** page.</span></span> <span data-ttu-id="495d3-118">为此，请按照下列步骤进行操作：</span><span class="sxs-lookup"><span data-stu-id="495d3-118">To do this, follow these steps:</span></span>  
  
    1.  <span data-ttu-id="495d3-119">在详细信息窗格中，双击“收集项”表中的**Collection items**“收集频率(秒)”列中显示的数字。</span><span class="sxs-lookup"><span data-stu-id="495d3-119">In the details pane, double-click the number that is displayed for the **Collection Frequency (sec)** column in the **Collection items** table.</span></span>  
  
    2.  <span data-ttu-id="495d3-120">若要提高或降低收集频率，请键入一个更小或更大的数字，然后按 Enter 存储这个新值。</span><span class="sxs-lookup"><span data-stu-id="495d3-120">To increase or decrease the collection frequency, type a lower or higher number, and then press ENTER to store the new value.</span></span>  
  
4.  <span data-ttu-id="495d3-121">若要更改收集组的现有上载计划，请按照下列步骤进行操作：</span><span class="sxs-lookup"><span data-stu-id="495d3-121">To change the existing upload schedule for the collection set, follow these steps:</span></span>  
  
    1.  <span data-ttu-id="495d3-122">单击 **“上载”** 页。</span><span class="sxs-lookup"><span data-stu-id="495d3-122">Click the **Uploads** page.</span></span>  
  
    2.  <span data-ttu-id="495d3-123">在详细信息窗格中，单击 **“选取”** 。</span><span class="sxs-lookup"><span data-stu-id="495d3-123">In the details pane, click **Pick**.</span></span>  
  
         <span data-ttu-id="495d3-124">将打开 **“为作业选取计划”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="495d3-124">The **Pick Schedule for Job** dialog box opens.</span></span> <span data-ttu-id="495d3-125">可用的计划以表的形式出现。</span><span class="sxs-lookup"><span data-stu-id="495d3-125">The available schedules appear as a table.</span></span>  
  
    3.  <span data-ttu-id="495d3-126">单击包含所需计划的行。</span><span class="sxs-lookup"><span data-stu-id="495d3-126">Click the row with the schedule that you want.</span></span> <span data-ttu-id="495d3-127">例如，若要将计划更改为每隔 5 分钟运行一次，请单击其中的计划名称为 **CollectorSchedule_Every_5min**的行。</span><span class="sxs-lookup"><span data-stu-id="495d3-127">For example, to change the schedule to every 5 minutes, click the row where the schedule name is **CollectorSchedule_Every_5min.**</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="495d3-128">可以单击 **“属性”** 打开选定计划的 **“作业计划属性”** 对话框，以查看和编辑该计划的属性。</span><span class="sxs-lookup"><span data-stu-id="495d3-128">You can view and edit the properties for the selected schedule by clicking **Properties** to open the **Job Schedule Properties** dialog box for the schedule.</span></span> <span data-ttu-id="495d3-129">可使用此对话框来更改计划信息，例如频率。</span><span class="sxs-lookup"><span data-stu-id="495d3-129">You can use this dialog box to change schedule information, such as the frequency.</span></span>  
        >   
        >  <span data-ttu-id="495d3-130">除了修改现有计划外，还可以通过单击 **“上载”** 页上的 **“新建”** 来创建新的上载计划。</span><span class="sxs-lookup"><span data-stu-id="495d3-130">As an alternative to modifying an existing schedule, you can create a new upload schedule by clicking **New** on the **Uploads** page.</span></span> <span data-ttu-id="495d3-131">此操作将打开 **“新建作业计划”** 对话框，可使用该对话框来创建自定义计划。</span><span class="sxs-lookup"><span data-stu-id="495d3-131">This action opens the **New Job Schedule** dialog box, which you can use to create a custom schedule.</span></span>  
  
    4.  <span data-ttu-id="495d3-132">完成对该计划的配置后，请单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="495d3-132">When you are finished configuring the schedule, click **OK**.</span></span>  
  
         <span data-ttu-id="495d3-133">您所做的更改将出现在 **“上载”** 页上。</span><span class="sxs-lookup"><span data-stu-id="495d3-133">The changes that you made appear on the **Uploads** page.</span></span>  
  
5.  <span data-ttu-id="495d3-134">单击 **“确定”** 以保存对收集频率和上载计划所做的更改，并关闭 **“数据收集组属性”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="495d3-134">Click **OK** to save the changes to the collection frequency and the upload schedule, and to close the **Data Collection Set Properties** dialog box.</span></span>  
  
### <a name="to-change-the-schedule-for-a-non-cached-mode-collection-set"></a><span data-ttu-id="495d3-135">更改非缓存模式收集组的计划</span><span class="sxs-lookup"><span data-stu-id="495d3-135">To change the schedule for a non-cached mode collection set</span></span>  
  
1.  <span data-ttu-id="495d3-136">在对象资源管理器中，依次展开 **“管理”** 节点、 **“数据收集”** 和 **“系统数据收集组”** 。</span><span class="sxs-lookup"><span data-stu-id="495d3-136">In Object Explorer, expand the **Management** node, expand **Data Collection**, and then expand **System Data Collection Sets**.</span></span>  
  
2.  <span data-ttu-id="495d3-137">右键单击使用非缓存模式的收集组（如“磁盘使用情况”），然后单击“属性”以便打开[数据收集组属性](#CollectionSet)对话框。</span><span class="sxs-lookup"><span data-stu-id="495d3-137">Right-click a collection set that uses non-cached mode, such as **Disk Usage**, and then click **Properties** to open the [Data Collection Set Properties](#CollectionSet) dialog box.</span></span>  
  
     <span data-ttu-id="495d3-138">**“数据收集组属性”** 对话框将显示收集组属性的分页视图。</span><span class="sxs-lookup"><span data-stu-id="495d3-138">The **Data Collection Set Properties** dialog box displays a paged view of the collection set properties.</span></span>  
  
3.  <span data-ttu-id="495d3-139">若要更改该收集组的计划，请单击 **“选取”** 。</span><span class="sxs-lookup"><span data-stu-id="495d3-139">To change the schedule for the collection set, click **Pick**.</span></span>  
  
     <span data-ttu-id="495d3-140">将打开 **“为作业选取计划”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="495d3-140">The **Pick Schedule for Job** dialog box opens.</span></span> <span data-ttu-id="495d3-141">可用的计划以表的形式显示。</span><span class="sxs-lookup"><span data-stu-id="495d3-141">The available schedules are displayed as a table.</span></span>  
  
4.  <span data-ttu-id="495d3-142">单击包含所需计划的行。</span><span class="sxs-lookup"><span data-stu-id="495d3-142">Click the row with the schedule that you want.</span></span> <span data-ttu-id="495d3-143">例如，若要将计划更改为每隔 5 分钟运行一次，请单击其中的计划名称为 **CollectorSchedule_Every_5min**的行。</span><span class="sxs-lookup"><span data-stu-id="495d3-143">For example, to change the schedule to every 5 minutes, click the row where the schedule name is **CollectorSchedule_Every_5min**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="495d3-144">可以单击 **“属性”** 打开选定计划的 **“作业计划属性”** 对话框，以查看和编辑该计划的属性。</span><span class="sxs-lookup"><span data-stu-id="495d3-144">You can view and edit the properties for the selected schedule by clicking **Properties** to open the **Job Schedule Properties** dialog box for the schedule.</span></span> <span data-ttu-id="495d3-145">可使用此对话框来更改计划信息，例如频率。</span><span class="sxs-lookup"><span data-stu-id="495d3-145">You can use this dialog box to change schedule information, such as the frequency.</span></span>  
    >   
    >  <span data-ttu-id="495d3-146">除了修改现有计划外，还可以通过单击 **“常规”** 页上的 **“新建”** 来创建新的收集和上载计划。</span><span class="sxs-lookup"><span data-stu-id="495d3-146">As an alternative to modifying an existing schedule, you can create a new collect and upload schedule by clicking **New** on the **General** page.</span></span> <span data-ttu-id="495d3-147">此操作将打开 **“新建作业计划”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="495d3-147">This action opens the **New Job Schedule** dialog box.</span></span>  
  
5.  <span data-ttu-id="495d3-148">完成对该计划的配置后，请单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="495d3-148">When you are finished configuring the schedule, click **OK**.</span></span>  
  
6.  <span data-ttu-id="495d3-149">单击 **“确定”** 保存更改并关闭 **“数据收集组属性”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="495d3-149">Click **OK** to save the changes and to close the **Data Collection Set Properties** dialog box.</span></span>  
  
####  <a name="data-collection-set-properties-dialog-box"></a><a name="CollectionSet"></a> <span data-ttu-id="495d3-150">“数据收集组属性”对话框</span><span class="sxs-lookup"><span data-stu-id="495d3-150">Data Collection Set Properties Dialog Box</span></span>  
 <span data-ttu-id="495d3-151">**“常规”页**</span><span class="sxs-lookup"><span data-stu-id="495d3-151">**General Page**</span></span>  
  
 <span data-ttu-id="495d3-152">使用此页可以配置数据的收集和上载方式、配置计划以及配置数据在管理数据仓库中的保持期。</span><span class="sxs-lookup"><span data-stu-id="495d3-152">Use this page to configure how data is collected and uploaded, configure schedules, and configure data retention periods in the management data warehouse.</span></span> <span data-ttu-id="495d3-153">此页还提供了收集组的相关信息，如收集器类型、收集频率以及用于收集组的输入参数。</span><span class="sxs-lookup"><span data-stu-id="495d3-153">This page also provides information about collection sets, such as collector types and collection frequencies, as well as the input parameters that are used for a collection set.</span></span>  
  
 <span data-ttu-id="495d3-154">**名称**</span><span class="sxs-lookup"><span data-stu-id="495d3-154">**Name**</span></span>  
 <span data-ttu-id="495d3-155">显示此页引用的收集组的名称。</span><span class="sxs-lookup"><span data-stu-id="495d3-155">Displays the name of the collection set that this page refers to.</span></span>  
  
 <span data-ttu-id="495d3-156">**数据收集和上载**</span><span class="sxs-lookup"><span data-stu-id="495d3-156">**Data collection and upload**</span></span>  
 <span data-ttu-id="495d3-157">指定收集数据并将其上载到管理数据仓库的方式。</span><span class="sxs-lookup"><span data-stu-id="495d3-157">Specifies how data is collected and uploaded to the management data warehouse.</span></span> <span data-ttu-id="495d3-158">选取下列选项之一。</span><span class="sxs-lookup"><span data-stu-id="495d3-158">Pick one of the following options.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="495d3-159">**不缓存。按照相同的计划收集和上载数据。**</span><span class="sxs-lookup"><span data-stu-id="495d3-159">**Non-cached. Collection and data upload on the same schedule.**</span></span>|<span data-ttu-id="495d3-160">选择此选项后，请指定以下选项之一：</span><span class="sxs-lookup"><span data-stu-id="495d3-160">When selected, specify one of the following:</span></span><br /><br /> <span data-ttu-id="495d3-161">**按需**。</span><span class="sxs-lookup"><span data-stu-id="495d3-161">**On-demand**.</span></span> <span data-ttu-id="495d3-162">按需收集和上载数据。</span><span class="sxs-lookup"><span data-stu-id="495d3-162">Data is collected and uploaded on demand.</span></span><br /><br /> <span data-ttu-id="495d3-163">**计划**。</span><span class="sxs-lookup"><span data-stu-id="495d3-163">**Schedule**.</span></span> <span data-ttu-id="495d3-164">按计划收集和上载数据。</span><span class="sxs-lookup"><span data-stu-id="495d3-164">Data is collected and uploaded according to a schedule.</span></span> <span data-ttu-id="495d3-165">单击 **“选取”** 可从预定义的计划列表中进行选择，或单击 **“新建”** 创建新计划。</span><span class="sxs-lookup"><span data-stu-id="495d3-165">Click **Pick** to select from a predefined list of schedules, or click **New** to create a new schedule.</span></span>|  
|<span data-ttu-id="495d3-166">**已缓存。按照一组收集频率收集数据并对其进行缓存。按照单独的计划上载缓存的数据。**</span><span class="sxs-lookup"><span data-stu-id="495d3-166">**Cached. Collect and cache data at a set of collection frequencies. Upload cached data on a separate schedule.**</span></span>|<span data-ttu-id="495d3-167">按照指定的收集频率收集数据并对其进行缓存。</span><span class="sxs-lookup"><span data-stu-id="495d3-167">Collect and cache data for a specified collection frequency.</span></span> <span data-ttu-id="495d3-168">按照单独的计划上载收集的数据。</span><span class="sxs-lookup"><span data-stu-id="495d3-168">Upload the collected data on a separate schedule.</span></span>|  
  
 <span data-ttu-id="495d3-169">**收集项**</span><span class="sxs-lookup"><span data-stu-id="495d3-169">**Collection items**</span></span>  
 <span data-ttu-id="495d3-170">显示收集组中的收集项。</span><span class="sxs-lookup"><span data-stu-id="495d3-170">Displays the collection items in the collection set.</span></span> <span data-ttu-id="495d3-171">以下是针对每个收集项提供的信息：</span><span class="sxs-lookup"><span data-stu-id="495d3-171">The following information is provided for each collection item:</span></span>  
  
-   <span data-ttu-id="495d3-172">**名称**</span><span class="sxs-lookup"><span data-stu-id="495d3-172">**Name**</span></span>  
  
-   <span data-ttu-id="495d3-173">**收集器类型**</span><span class="sxs-lookup"><span data-stu-id="495d3-173">**Collector Type**</span></span>  
  
-   <span data-ttu-id="495d3-174">**收集频率** （秒）。</span><span class="sxs-lookup"><span data-stu-id="495d3-174">**Collection Frequency** (secs).</span></span> <span data-ttu-id="495d3-175">如果将 **“数据收集和上载”** 配置为缓存，则可以编辑此字段。</span><span class="sxs-lookup"><span data-stu-id="495d3-175">This field is editable if **Data collection and upload** is configured as cached.</span></span> <span data-ttu-id="495d3-176">双击此单元格可设置收集频率。</span><span class="sxs-lookup"><span data-stu-id="495d3-176">Double-click this cell to set the collection frequency.</span></span>  
  
 <span data-ttu-id="495d3-177">**输入参数**</span><span class="sxs-lookup"><span data-stu-id="495d3-177">**Input parameters**</span></span>  
 <span data-ttu-id="495d3-178">显示用于收集组的输入参数。</span><span class="sxs-lookup"><span data-stu-id="495d3-178">Displays the input parameters used for the collection set.</span></span>  
  
 <span data-ttu-id="495d3-179">**运行身份**</span><span class="sxs-lookup"><span data-stu-id="495d3-179">**Run as**</span></span>  
 <span data-ttu-id="495d3-180">指定用来运行收集组的帐户。</span><span class="sxs-lookup"><span data-stu-id="495d3-180">Specifies the account used to run the collection set.</span></span> <span data-ttu-id="495d3-181">默认情况下，此帐户为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理服务帐户。</span><span class="sxs-lookup"><span data-stu-id="495d3-181">By default this is the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent Service Account.</span></span> <span data-ttu-id="495d3-182">如果定义了代理帐户，则此列表中包含可用代理帐户的名称。</span><span class="sxs-lookup"><span data-stu-id="495d3-182">If proxy accounts are defined, this list includes the names of the available proxy accounts.</span></span>  
  
 <span data-ttu-id="495d3-183">**设置收集的数据将在管理数据仓库中保留的时间。**</span><span class="sxs-lookup"><span data-stu-id="495d3-183">**Set how long collected data will be retained in the management data warehouse.**</span></span>  
 <span data-ttu-id="495d3-184">指定收集的数据保留的时间。</span><span class="sxs-lookup"><span data-stu-id="495d3-184">Specifies how long collected data is retained.</span></span> <span data-ttu-id="495d3-185">选取下列选项之一。</span><span class="sxs-lookup"><span data-stu-id="495d3-185">Pick one of the following options.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="495d3-186">**数据保留时间**</span><span class="sxs-lookup"><span data-stu-id="495d3-186">**Retain data for**</span></span>|<span data-ttu-id="495d3-187">默认情况下选择此选项，并且默认保持期为 14 天。</span><span class="sxs-lookup"><span data-stu-id="495d3-187">This option is selected by default, and the default retention period is 14 days.</span></span>|  
|<span data-ttu-id="495d3-188">**无限期保留数据**</span><span class="sxs-lookup"><span data-stu-id="495d3-188">**Retain data indefinitely**</span></span>|<span data-ttu-id="495d3-189">对数据保留的时间长度没有限制。</span><span class="sxs-lookup"><span data-stu-id="495d3-189">There is no time limit on the length of time that data is retained.</span></span>|  
  
 <span data-ttu-id="495d3-190">**“上载”页**</span><span class="sxs-lookup"><span data-stu-id="495d3-190">**Uploads Page**</span></span>  
  
 <span data-ttu-id="495d3-191">使用此页可以为由此收集组收集的数据配置上载计划。</span><span class="sxs-lookup"><span data-stu-id="495d3-191">Use this page to configure the upload schedule for data that is collected by this collection set.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="495d3-192">仅当已为 “数据收集和上传”配置了“已缓存”选项时才启用此选项卡。</span><span class="sxs-lookup"><span data-stu-id="495d3-192">This tab is only enabled if the **Cached** option is configured for **Data collection and upload**.</span></span>  
  
 <span data-ttu-id="495d3-193">**Server**</span><span class="sxs-lookup"><span data-stu-id="495d3-193">**Server**</span></span>  
 <span data-ttu-id="495d3-194">显示承载管理数据仓库的服务器的名称。</span><span class="sxs-lookup"><span data-stu-id="495d3-194">Displays the name of the server that hosts the management data warehouse.</span></span> <span data-ttu-id="495d3-195">有关详细信息。请参阅[配置管理数据仓库 (SQL Server Management Studio)](configure-the-management-data-warehouse-sql-server-management-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="495d3-195">For more information, see [Configure the Management Data Warehouse &#40;SQL Server Management Studio&#41;](configure-the-management-data-warehouse-sql-server-management-studio.md).</span></span>  
  
 <span data-ttu-id="495d3-196">**管理数据仓库**</span><span class="sxs-lookup"><span data-stu-id="495d3-196">**Management data warehouse**</span></span>  
 <span data-ttu-id="495d3-197">显示管理数据仓库的名称。</span><span class="sxs-lookup"><span data-stu-id="495d3-197">Displays the name of the management data warehouse.</span></span> <span data-ttu-id="495d3-198">有关详细信息。请参阅[配置管理数据仓库 (SQL Server Management Studio)](configure-the-management-data-warehouse-sql-server-management-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="495d3-198">For more information, see [Configure the Management Data Warehouse &#40;SQL Server Management Studio&#41;](configure-the-management-data-warehouse-sql-server-management-studio.md).</span></span>  
  
 <span data-ttu-id="495d3-199">**上次上载时间**</span><span class="sxs-lookup"><span data-stu-id="495d3-199">**Last upload**</span></span>  
 <span data-ttu-id="495d3-200">显示为收集组完成的上次上载的日期和时间信息。</span><span class="sxs-lookup"><span data-stu-id="495d3-200">Displays date and time information for the last upload done for the collection set.</span></span>  
  
 <span data-ttu-id="495d3-201">**上载计划**</span><span class="sxs-lookup"><span data-stu-id="495d3-201">**Upload schedule**</span></span>  
 <span data-ttu-id="495d3-202">指定收集组的上载计划。</span><span class="sxs-lookup"><span data-stu-id="495d3-202">Specifies the upload schedule for the collection set.</span></span> <span data-ttu-id="495d3-203">如果启用，请单击 **“选取”** 从预定义的计划列表中进行选择，或单击 **“新建”** 创建新计划。</span><span class="sxs-lookup"><span data-stu-id="495d3-203">If enabled, Click **Pick** to select from a predefined list of schedules, or click **New** to create a new schedule.</span></span>  
  
 <span data-ttu-id="495d3-204">**“说明”页**</span><span class="sxs-lookup"><span data-stu-id="495d3-204">**Description Page**</span></span>  
  
 <span data-ttu-id="495d3-205">使用此页可以查看此属性页引用的收集组的说明。</span><span class="sxs-lookup"><span data-stu-id="495d3-205">Use this page to view a description of the collection set that this properties page refers to.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="495d3-206">另请参阅</span><span class="sxs-lookup"><span data-stu-id="495d3-206">See Also</span></span>  
 <span data-ttu-id="495d3-207">[管理数据收集](manage-data-collection.md) </span><span class="sxs-lookup"><span data-stu-id="495d3-207">[Manage Data Collection](manage-data-collection.md) </span></span>  
 [<span data-ttu-id="495d3-208">“数据收集”</span><span class="sxs-lookup"><span data-stu-id="495d3-208">Data Collection</span></span>](data-collection.md)  
  
  
