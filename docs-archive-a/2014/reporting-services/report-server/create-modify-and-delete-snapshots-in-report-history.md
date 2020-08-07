---
title: 创建、修改和删除报表历史记录中的快照 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- snapshots [Reporting Services]
- report snapshots [Reporting Services]
ms.assetid: 5aebbbfa-a8db-462d-8ab9-746fad9525f0
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 8ee091ad3361280c4da258eb86c83492ade8b3bd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588283"
---
# <a name="create-modify-and-delete-snapshots-in-report-history"></a><span data-ttu-id="07de9-102">创建、修改和删除报表历史记录中的快照</span><span class="sxs-lookup"><span data-stu-id="07de9-102">Create, Modify, and Delete Snapshots in Report History</span></span>
  <span data-ttu-id="07de9-103">报表历史记录是报表快照的集合。</span><span class="sxs-lookup"><span data-stu-id="07de9-103">Report history is a collection of report snapshots.</span></span> <span data-ttu-id="07de9-104">通过添加和删除快照或修改影响报表历史记录存储的属性，可以对报表历史记录进行维护。</span><span class="sxs-lookup"><span data-stu-id="07de9-104">You can maintain report history by adding and deleting snapshots, or by modifying properties that affect report history storage.</span></span> <span data-ttu-id="07de9-105">您可以手动或按计划创建报表历史记录。</span><span class="sxs-lookup"><span data-stu-id="07de9-105">You can create report history manually or on a schedule.</span></span>  
  
 <span data-ttu-id="07de9-106">若要创建报表历史记录，您的角色分配必须包括“管理报表历史记录”任务。</span><span class="sxs-lookup"><span data-stu-id="07de9-106">To create report history, your role assignment must include the "Manage report history" task.</span></span> <span data-ttu-id="07de9-107">若要查看报表历史记录，您的角色分配必须包括“查看报表”任务。</span><span class="sxs-lookup"><span data-stu-id="07de9-107">To view report history, your role assignment must include the "View reports" task.</span></span> <span data-ttu-id="07de9-108">报表历史记录对有权访问该报表的所有用户均可用。</span><span class="sxs-lookup"><span data-stu-id="07de9-108">Report history is available to all users who have access to the report.</span></span> <span data-ttu-id="07de9-109">不能针对部分用户有选择地启用或禁用报表历史记录。</span><span class="sxs-lookup"><span data-stu-id="07de9-109">You cannot selectively enable or disable report history for a subset of users.</span></span>  
  
 <span data-ttu-id="07de9-110">报表历史记录中的快照按其创建日期和时间进行标识，</span><span class="sxs-lookup"><span data-stu-id="07de9-110">Snapshots in report history are identified by the date and time that they were created.</span></span> <span data-ttu-id="07de9-111">而日期和时间则基于查询的执行时间。</span><span class="sxs-lookup"><span data-stu-id="07de9-111">The date and time is based on when the query executed.</span></span>  
  
## <a name="creating-snapshots-in-report-history"></a><span data-ttu-id="07de9-112">在报表历史记录中创建快照</span><span class="sxs-lookup"><span data-stu-id="07de9-112">Creating Snapshots in Report History</span></span>  
 <span data-ttu-id="07de9-113">对于所有可在无人参与情况下运行的报表，可以手动或按计划间隔为其创建快照。</span><span class="sxs-lookup"><span data-stu-id="07de9-113">Snapshots can be created manually or at scheduled intervals for any report that can run unattended.</span></span> <span data-ttu-id="07de9-114">若要在无人参与的情况下运行，报表必须使用已存储凭据或根本不使用凭据。</span><span class="sxs-lookup"><span data-stu-id="07de9-114">To run unattended, the report must use stored credentials or no credentials at all.</span></span> <span data-ttu-id="07de9-115">此外，如果报表使用参数，则必须指定运行报表时所用的默认值。</span><span class="sxs-lookup"><span data-stu-id="07de9-115">Furthermore, if the report uses parameters, you must specify default values to use when the report runs.</span></span> <span data-ttu-id="07de9-116">可以在报表的属性页中指定已存储凭据和参数值。</span><span class="sxs-lookup"><span data-stu-id="07de9-116">You can specify stored credentials and parameter values in the property pages for the report.</span></span> <span data-ttu-id="07de9-117">有关详细信息，请参阅[参数属性页（报表管理器）](../parameters-properties-page-report-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="07de9-117">For more information, see [Parameters Properties Page &#40;Report Manager&#41;](../parameters-properties-page-report-manager.md).</span></span>  
  
 <span data-ttu-id="07de9-118">创建报表快照后，以下元素将随报表快照一起存储在报表服务器数据库中：</span><span class="sxs-lookup"><span data-stu-id="07de9-118">When you create a report snapshot, the following elements are stored along with the report snapshot in the report server database:</span></span>  
  
-   <span data-ttu-id="07de9-119">结果集（即通过报表的“数据源”属性页中指定的凭据检索到的报表数据）。</span><span class="sxs-lookup"><span data-stu-id="07de9-119">The result set (that is, the data in the report, retrieved through the credentials specified in the Data Sources properties page of the report).</span></span>  
  
-   <span data-ttu-id="07de9-120">创建快照时的基础报表定义。</span><span class="sxs-lookup"><span data-stu-id="07de9-120">The underlying report definition, as it exists at the time the snapshot was created.</span></span> <span data-ttu-id="07de9-121">如果在生成快照后修改了报表定义，所做更改不会反映在快照中。</span><span class="sxs-lookup"><span data-stu-id="07de9-121">If the report definition is subsequently modified after the snapshot is generated, those changes are not reflected in the snapshot.</span></span>  
  
-   <span data-ttu-id="07de9-122">用于获取或筛选结果集的参数值。</span><span class="sxs-lookup"><span data-stu-id="07de9-122">Parameter values that are used to obtain or filter the result set.</span></span>  
  
-   <span data-ttu-id="07de9-123">嵌入的资源，如图像。</span><span class="sxs-lookup"><span data-stu-id="07de9-123">Embedded resources, such as images.</span></span> <span data-ttu-id="07de9-124">链接到报表的外部资源不与报表快照一同存储。</span><span class="sxs-lookup"><span data-stu-id="07de9-124">External resources that are linked to a report are not stored with the report snapshot.</span></span>  
  
 <span data-ttu-id="07de9-125">报表历史记录的创建方式以及可以存储的报表快照数由相应设置确定。</span><span class="sxs-lookup"><span data-stu-id="07de9-125">The ways in which report history can be created and the number of report snapshots that can be stored are determined by settings.</span></span>  
  
 <span data-ttu-id="07de9-126">如果报表出错，则不会创建快照。</span><span class="sxs-lookup"><span data-stu-id="07de9-126">If a report produces an error, a snapshot is not created.</span></span> <span data-ttu-id="07de9-127">生成警告但仍能运行的报表可以用来生成快照。</span><span class="sxs-lookup"><span data-stu-id="07de9-127">Reports that produce warnings, yet still run, can be used to generate snapshots.</span></span>  
  
## <a name="modifying-properties-and-deleting-report-history"></a><span data-ttu-id="07de9-128">修改属性和删除报表历史记录</span><span class="sxs-lookup"><span data-stu-id="07de9-128">Modifying Properties and Deleting Report History</span></span>  
 <span data-ttu-id="07de9-129">报表快照一旦生成就无法修改。</span><span class="sxs-lookup"><span data-stu-id="07de9-129">Once a report snapshot exists, you cannot modify it.</span></span> <span data-ttu-id="07de9-130">但是，您可以采用删除报表历史记录的方法来修改属性。</span><span class="sxs-lookup"><span data-stu-id="07de9-130">However, you can modify properties in a way that deletes report history.</span></span>  
  
 <span data-ttu-id="07de9-131">可采用以下方法删除报表历史记录：</span><span class="sxs-lookup"><span data-stu-id="07de9-131">Report history can be deleted in the following ways:</span></span>  
  
-   <span data-ttu-id="07de9-132">手动删除单个或成组快照。</span><span class="sxs-lookup"><span data-stu-id="07de9-132">Manually delete snapshots singly or in groups.</span></span>  
  
     <span data-ttu-id="07de9-133">您可以从报表管理器的“历史记录”页中删除快照。</span><span class="sxs-lookup"><span data-stu-id="07de9-133">You can delete snapshots from the History page in Report Manager.</span></span> <span data-ttu-id="07de9-134">导航到报表，单击“历史记录”，选中要删除的快照旁边的复选框，再单击 **“删除”** 。</span><span class="sxs-lookup"><span data-stu-id="07de9-134">Navigate to the report, click History, select the check box next to the snapshots that you want to delete, and then click **Delete**.</span></span>  
  
-   <span data-ttu-id="07de9-135">降低报表历史记录限值以减少存储的快照数。</span><span class="sxs-lookup"><span data-stu-id="07de9-135">Lower the report history limit to reduce the number of snapshots that are stored.</span></span> <span data-ttu-id="07de9-136">可以为报表服务器或特定报表设置报表历史记录限值。</span><span class="sxs-lookup"><span data-stu-id="07de9-136">The report history limit can be set for the report server or for specific reports.</span></span> <span data-ttu-id="07de9-137">如果降低限值，将从历史记录中删除最早的快照。</span><span class="sxs-lookup"><span data-stu-id="07de9-137">When the limit is lowered, the oldest snapshots are deleted from history.</span></span>  
  
 <span data-ttu-id="07de9-138">不能通过大容量操作来删除报表服务器上存储的所有报表历史记录。</span><span class="sxs-lookup"><span data-stu-id="07de9-138">You cannot delete all report history stored on a report server in a bulk operation.</span></span>  
  
 <span data-ttu-id="07de9-139">删除报表时将同时删除报表历史记录。</span><span class="sxs-lookup"><span data-stu-id="07de9-139">Report history is also deleted when you delete a report.</span></span> <span data-ttu-id="07de9-140">例如，如果删除月销售情况报表，代之以新报表，则与该报表关联的所有报表历史记录也将随之删除。</span><span class="sxs-lookup"><span data-stu-id="07de9-140">For example, if you delete a monthly sales report because you are replacing it with a newer version, all report history that is associated with the report is also deleted.</span></span> <span data-ttu-id="07de9-141">但是，如果移动报表，所有报表历史记录也将随之移动。</span><span class="sxs-lookup"><span data-stu-id="07de9-141">However, if you move a report, all report history moves with it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07de9-142">另请参阅</span><span class="sxs-lookup"><span data-stu-id="07de9-142">See Also</span></span>  
 <span data-ttu-id="07de9-143">[创建报表历史记录（SharePoint 集成模式下的 Reporting Services）](create-report-history-reporting-services-in-sharepoint-integrated-mode.md) </span><span class="sxs-lookup"><span data-stu-id="07de9-143">[Create Report History &#40;Reporting Services in SharePoint Integrated Mode&#41;](create-report-history-reporting-services-in-sharepoint-integrated-mode.md) </span></span>  
 <span data-ttu-id="07de9-144">[报表管理器（SSRS 本机模式）](../report-manager-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="07de9-144">[Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="07de9-145">[报表服务器内容管理（SSRS 本机模式）](report-server-content-management-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="07de9-145">[Report Server Content Management &#40;SSRS Native Mode&#41;](report-server-content-management-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="07de9-146">[向报表历史记录添加快照（报表管理器）](add-a-snapshot-to-report-history-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="07de9-146">[Add a Snapshot to Report History &#40;Report Manager&#41;](add-a-snapshot-to-report-history-report-manager.md) </span></span>  
 [<span data-ttu-id="07de9-147">限制报表历史记录（报表管理器）</span><span class="sxs-lookup"><span data-stu-id="07de9-147">Limit Report History &#40;Report Manager&#41;</span></span>](../reports/limit-report-history-report-manager.md)  
  
  
