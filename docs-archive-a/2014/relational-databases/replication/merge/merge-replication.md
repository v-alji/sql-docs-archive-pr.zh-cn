---
title: 合并复制 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- merge replication [SQL Server replication], about merge replication
- merge replication [SQL Server replication]
ms.assetid: ff87c368-4c00-4e48-809d-ea752839551e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 7feef9e4debc228d1685c664c072139d60b56c22
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576681"
---
# <a name="merge-replication"></a><span data-ttu-id="67d44-102">合并复制</span><span class="sxs-lookup"><span data-stu-id="67d44-102">Merge Replication</span></span>
  <span data-ttu-id="67d44-103">与事务复制相同，合并复制通常也是从发布数据库对象和数据的快照开始，</span><span class="sxs-lookup"><span data-stu-id="67d44-103">Merge replication, like transactional replication, typically starts with a snapshot of the publication database objects and data.</span></span> <span data-ttu-id="67d44-104">并且用触发器跟踪在发布服务器和订阅服务器上所做的后续数据更改和架构修改。</span><span class="sxs-lookup"><span data-stu-id="67d44-104">Subsequent data changes and schema modifications made at the Publisher and Subscribers are tracked with triggers.</span></span> <span data-ttu-id="67d44-105">订阅服务器在连接到网络时将与发布服务器进行同步，并交换自上次同步以来发布服务器和订阅服务器之间发生更改的所有行。</span><span class="sxs-lookup"><span data-stu-id="67d44-105">The Subscriber synchronizes with the Publisher when connected to the network and exchanges all rows that have changed between the Publisher and Subscriber since the last time synchronization occurred.</span></span>

 <span data-ttu-id="67d44-106">合并复制通常用于服务器到客户端的环境中。</span><span class="sxs-lookup"><span data-stu-id="67d44-106">Merge replication is typically used in server-to-client environments.</span></span> <span data-ttu-id="67d44-107">合并复制适用于下列各种情况：</span><span class="sxs-lookup"><span data-stu-id="67d44-107">Merge replication is appropriate in any of the following situations:</span></span>

-   <span data-ttu-id="67d44-108">多个订阅服务器可能会在不同时间更新同一数据，并将其更改传播到发布服务器和其他订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="67d44-108">Multiple Subscribers might update the same data at various times and propagate those changes to the Publisher and to other Subscribers.</span></span>

-   <span data-ttu-id="67d44-109">订阅服务器需要接收数据，脱机更改数据，并在以后与发布服务器和其他订阅服务器同步更改。</span><span class="sxs-lookup"><span data-stu-id="67d44-109">Subscribers need to receive data, make changes offline, and later synchronize changes with the Publisher and other Subscribers.</span></span>

-   <span data-ttu-id="67d44-110">每个订阅服务器都需要不同的数据分区。</span><span class="sxs-lookup"><span data-stu-id="67d44-110">Each Subscriber requires a different partition of data.</span></span>

-   <span data-ttu-id="67d44-111">可能会发生冲突，并且在冲突发生时，您需要具有检测和解决冲突的能力。</span><span class="sxs-lookup"><span data-stu-id="67d44-111">Conflicts might occur and, when they do, you need the ability to detect and resolve them.</span></span>

-   <span data-ttu-id="67d44-112">应用程序需要最终的数据更改结果，而不是访问中间数据状态。</span><span class="sxs-lookup"><span data-stu-id="67d44-112">The application requires net data change rather than access to intermediate data states.</span></span> <span data-ttu-id="67d44-113">例如，如果在订阅服务器与发布服务器进行同步之前，订阅服务器上的行更改了五次，则该行在发布服务器上仅更改一次来反映最终数据更改（也就是第五次更改的值）。</span><span class="sxs-lookup"><span data-stu-id="67d44-113">For example, if a row changes five times at a Subscriber before it synchronizes with a Publisher, the row will change only once at the Publisher to reflect the net data change (that is, the fifth value).</span></span>

 <span data-ttu-id="67d44-114">合并复制允许不同站点自主工作，并在以后将更新合并成一个统一的结果。</span><span class="sxs-lookup"><span data-stu-id="67d44-114">Merge replication allows various sites to work autonomously and later merge updates into a single, uniform result.</span></span> <span data-ttu-id="67d44-115">由于更新是在多个节点上进行的，同一数据可能由发布服务器和多个订阅服务器进行了更新。</span><span class="sxs-lookup"><span data-stu-id="67d44-115">Because updates are made at more than one node, the same data may have been updated by the Publisher and by more than one Subscriber.</span></span> <span data-ttu-id="67d44-116">因此，在合并更新时可能会产生冲突，合并复制提供了多种处理冲突的方法。</span><span class="sxs-lookup"><span data-stu-id="67d44-116">Therefore, conflicts can occur when updates are merged and merge replication provides a number of ways to handle conflicts.</span></span>

 <span data-ttu-id="67d44-117">合并复制是由 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 快照代理和合并代理实现的。</span><span class="sxs-lookup"><span data-stu-id="67d44-117">Merge replication is implemented by the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Snapshot Agent and Merge Agent.</span></span> <span data-ttu-id="67d44-118">如果发布未经筛选或使用静态筛选器，快照代理将创建单个快照。</span><span class="sxs-lookup"><span data-stu-id="67d44-118">If the publication is unfiltered or uses static filters, the Snapshot Agent creates a single snapshot.</span></span> <span data-ttu-id="67d44-119">如果发布使用参数化筛选器，则快照代理将为每个数据分区创建一个快照。</span><span class="sxs-lookup"><span data-stu-id="67d44-119">If the publication uses parameterized filters, the Snapshot Agent creates a snapshot for each partition of data.</span></span> <span data-ttu-id="67d44-120">合并代理将初始快照应用于订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="67d44-120">The Merge Agent applies the initial snapshots to the Subscribers.</span></span> <span data-ttu-id="67d44-121">它还将合并自初始快照创建后发布服务器或订阅服务器上所发生的增量数据更改，并根据所配置的规则检测和解决任何冲突。</span><span class="sxs-lookup"><span data-stu-id="67d44-121">It also merges incremental data changes that occurred at the Publisher or Subscribers after the initial snapshot was created, and detects and resolves any conflicts according to rules you configure.</span></span>

 <span data-ttu-id="67d44-122">若要跟踪更改，合并复制（和带有排队更新订阅的事务复制）必须能够唯一地标识每个已发布表中的每一行。</span><span class="sxs-lookup"><span data-stu-id="67d44-122">To track changes, merge replication (and transactional replication with queued updating subscriptions) must be able to uniquely identify every row in every published table.</span></span> <span data-ttu-id="67d44-123">为了完成这一合并复制，需要向每个表添加列 `rowguid`，除非表中已包含一个数据类型为 `uniqueidentifier` 且设置了 `ROWGUIDCOL` 属性的列（这种情况下将使用此列）。</span><span class="sxs-lookup"><span data-stu-id="67d44-123">To accomplish this merge replication adds the column `rowguid` to every table, unless the table already has a column of data type `uniqueidentifier` with the `ROWGUIDCOL` property set (in which case this column is used).</span></span> <span data-ttu-id="67d44-124">如果从发布中删除表，则删除 `rowguid` 列；如果将现有列用于跟踪，则不删除该列。</span><span class="sxs-lookup"><span data-stu-id="67d44-124">If the table is dropped from the publication, the `rowguid` column is removed; if an existing column was used for tracking, the column is not removed.</span></span> <span data-ttu-id="67d44-125">筛选器不能包含复制所用的 `rowguidcol` 来标识行。</span><span class="sxs-lookup"><span data-stu-id="67d44-125">A filter must not include the `rowguidcol` used by replication to identify rows.</span></span> <span data-ttu-id="67d44-126">提供 `newid()` 函数，为 `rowguid` 列提供默认值，但用户可以按需为每行提供 GUID。</span><span class="sxs-lookup"><span data-stu-id="67d44-126">The `newid()` function is provided as a default for the `rowguid` column, however customers can provide a guid for each row if needed.</span></span> <span data-ttu-id="67d44-127">不过，请不要提供值 00000000-0000-0000-0000-000000000000。</span><span class="sxs-lookup"><span data-stu-id="67d44-127">However, do not provide value 00000000-0000-0000-0000-000000000000.</span></span>

 <span data-ttu-id="67d44-128">下面的关系图显示了合并复制中使用的组件。</span><span class="sxs-lookup"><span data-stu-id="67d44-128">The following diagram shows the components used in merge replication.</span></span>

 <span data-ttu-id="67d44-129">![合并复制组件和数据流](../media/merge.gif "合并复制组件和数据流")</span><span class="sxs-lookup"><span data-stu-id="67d44-129">![Merge replication components and data flow](../media/merge.gif "Merge replication components and data flow")</span></span>


