---
title: 快照代理（新建发布向导）| Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newpubwizard.configuresnapshotagent.f1
ms.assetid: 0257d4ee-1f7b-49fd-b4ef-65bfc1ef6951
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c45fa3444fb2f81436a40a2bfb80519aea105c47
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591242"
---
# <a name="snapshot-agent-new-publication-wizard"></a><span data-ttu-id="c4448-102">快照代理（新建发布向导）</span><span class="sxs-lookup"><span data-stu-id="c4448-102">Snapshot Agent (New Publication Wizard)</span></span>
  <span data-ttu-id="c4448-103">快照代理可以创建包含发布架构和数据（用于初始化新订阅）的文件。</span><span class="sxs-lookup"><span data-stu-id="c4448-103">The Snapshot Agent creates files containing the publication schema and data that are used to initialize new subscriptions.</span></span> <span data-ttu-id="c4448-104">默认情况下，在新建发布向导中创建发布之后，快照代理将立即运行。</span><span class="sxs-lookup"><span data-stu-id="c4448-104">By default, the Snapshot Agent runs immediately after the publication is created in the New Publication Wizard.</span></span> <span data-ttu-id="c4448-105">此后，该代理将按照您指定的计划运行。</span><span class="sxs-lookup"><span data-stu-id="c4448-105">Subsequently, the agent runs according to a schedule you specify.</span></span> <span data-ttu-id="c4448-106">代理每次运行时是否创建新的快照文件取决于复制类型和所选择的选项。</span><span class="sxs-lookup"><span data-stu-id="c4448-106">Whether the agent creates new snapshot files each time it runs depends on the type of replication and options chosen.</span></span> <span data-ttu-id="c4448-107">有关详细信息，请参阅[创建并应用快照](create-and-apply-the-snapshot.md)。</span><span class="sxs-lookup"><span data-stu-id="c4448-107">For more information, see [Create and Apply the Snapshot](create-and-apply-the-snapshot.md).</span></span>  
  
 <span data-ttu-id="c4448-108">对于使用参数化筛选器的合并发布，在完成发布快照后，您必须为数据的每个分区创建一个快照。</span><span class="sxs-lookup"><span data-stu-id="c4448-108">For merge publications that use parameterized filters, you must create a snapshot for each partition of data after the publication snapshot has completed.</span></span> <span data-ttu-id="c4448-109">有关详细信息，请参阅 [Snapshots for Merge Publications with Parameterized Filters](snapshots-for-merge-publications-with-parameterized-filters.md)。</span><span class="sxs-lookup"><span data-stu-id="c4448-109">For more information, see [Snapshots for Merge Publications with Parameterized Filters](snapshots-for-merge-publications-with-parameterized-filters.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="c4448-110">选项</span><span class="sxs-lookup"><span data-stu-id="c4448-110">Options</span></span>  
 <span data-ttu-id="c4448-111">**“立即创建快照”** （合并复制）或 **“立即创建快照并使快照保持可用状态，以初始化订阅”** （事务复制）</span><span class="sxs-lookup"><span data-stu-id="c4448-111">**Create a snapshot immediately** (merge replication) or **Create a snapshot immediately and keep the snapshot available to initialize subscriptions** (transactional replication)</span></span>  
 <span data-ttu-id="c4448-112">选中此复选框，可以在新建发布向导完成后立即创建快照。</span><span class="sxs-lookup"><span data-stu-id="c4448-112">Select this check box to create a snapshot immediately after the New Publication Wizard is completed.</span></span> <span data-ttu-id="c4448-113">如果计划在生成快照之前更改 **“发布属性”** 对话框中的快照属性，或者要在没有快照的情况下初始化订阅服务器，请清除此复选框。</span><span class="sxs-lookup"><span data-stu-id="c4448-113">Clear this check box if you plan to change snapshot properties in the **Publication Properties** dialog box before generating a snapshot, or if you will initialize the Subscriber without a snapshot.</span></span> <span data-ttu-id="c4448-114">有关详细信息，请参阅 [初始化事务订阅（不使用快照）](initialize-a-transactional-subscription-without-a-snapshot.md)中手动初始化订阅。</span><span class="sxs-lookup"><span data-stu-id="c4448-114">For more information, see [Initialize a Transactional Subscription Without a Snapshot](initialize-a-transactional-subscription-without-a-snapshot.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c4448-115">该向导可能会提示您连接到分发服务器，以启动分发代理或合并代理的相应作业。</span><span class="sxs-lookup"><span data-stu-id="c4448-115">The wizard might prompt for a connection to the Distributor in order to start the appropriate job for the Distribution Agent or Merge Agent.</span></span>  
  
 <span data-ttu-id="c4448-116">**计划在以下时间运行快照代理**</span><span class="sxs-lookup"><span data-stu-id="c4448-116">**Schedule the Snapshot Agent to run at the following times**</span></span>  
 <span data-ttu-id="c4448-117">接受运行快照代理的默认计划，或单击 **“更改”** 指定一个计划。</span><span class="sxs-lookup"><span data-stu-id="c4448-117">Accept the default schedule for running the Snapshot Agent, or click **Change** to specify a schedule.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4448-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c4448-118">See Also</span></span>  
 <span data-ttu-id="c4448-119">[Create a Publication](publish/create-a-publication.md) </span><span class="sxs-lookup"><span data-stu-id="c4448-119">[Create a Publication](publish/create-a-publication.md) </span></span>  
 <span data-ttu-id="c4448-120">[创建并应用初始快照](create-and-apply-the-initial-snapshot.md) </span><span class="sxs-lookup"><span data-stu-id="c4448-120">[Create and Apply the Initial Snapshot](create-and-apply-the-initial-snapshot.md) </span></span>  
 <span data-ttu-id="c4448-121">[查看和修改发布属性](publish/view-and-modify-publication-properties.md) </span><span class="sxs-lookup"><span data-stu-id="c4448-121">[View and Modify Publication Properties](publish/view-and-modify-publication-properties.md) </span></span>  
 <span data-ttu-id="c4448-122">[使用快照初始化订阅](initialize-a-subscription-with-a-snapshot.md) </span><span class="sxs-lookup"><span data-stu-id="c4448-122">[Initialize a Subscription with a Snapshot](initialize-a-subscription-with-a-snapshot.md) </span></span>  
 <span data-ttu-id="c4448-123">[发布数据和数据库对象](publish/publish-data-and-database-objects.md) </span><span class="sxs-lookup"><span data-stu-id="c4448-123">[Publish Data and Database Objects](publish/publish-data-and-database-objects.md) </span></span>  
 [<span data-ttu-id="c4448-124">复制代理概述</span><span class="sxs-lookup"><span data-stu-id="c4448-124">Replication Agents Overview</span></span>](agents/replication-agents-overview.md)  
  
  
