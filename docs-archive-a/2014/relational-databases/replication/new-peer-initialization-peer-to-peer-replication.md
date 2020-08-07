---
title: 新对等方的初始化（对等复制）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.p2pwizard.init.f1
ms.assetid: 050c00e1-78bd-4d9c-affe-40e22feb4d94
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 26658fdfbcf0d3d3a88bedbace4102cda6cee9c2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588983"
---
# <a name="new-peer-initialization-peer-to-peer-replication"></a><span data-ttu-id="2a4c0-102">新对等方的初始化（对等复制）</span><span class="sxs-lookup"><span data-stu-id="2a4c0-102">New Peer Initialization (Peer-to-Peer Replication)</span></span>
  <span data-ttu-id="2a4c0-103">可以使用 **“新对等方初始化”** 页指定如何初始化对等数据库。</span><span class="sxs-lookup"><span data-stu-id="2a4c0-103">Use the **New Peer Initialization** page to specify how peer databases were initialized.</span></span> <span data-ttu-id="2a4c0-104">必须先初始化 (对等方，然后才能完成此向导。 ) 对等方将手动初始化，或使用事务复制提供的**initialize with backup**功能来初始化。</span><span class="sxs-lookup"><span data-stu-id="2a4c0-104">(Peers must be initialized before you complete this wizard.) Peers are initialized manually or by using the **initialize with backup** functionality that is provided by transactional replication.</span></span> <span data-ttu-id="2a4c0-105"> (对等事务复制不支持使用快照初始化对等方。 ) 如果必须使用不同的方法初始化不同的对等方，则必须通过多次运行向导来添加对等方。</span><span class="sxs-lookup"><span data-stu-id="2a4c0-105">(Peer-to-peer transactional replication does not support initializing peers by using a snapshot.) If different peers have to be initialized using different methods, you must add the peers separately by running the wizard multiple times.</span></span>  
  
## <a name="options"></a><span data-ttu-id="2a4c0-106">选项</span><span class="sxs-lookup"><span data-stu-id="2a4c0-106">Options</span></span>  
 <span data-ttu-id="2a4c0-107">**指定如何初始化新的对等数据库**</span><span class="sxs-lookup"><span data-stu-id="2a4c0-107">**Specify how the new peer database(s) was initialized**</span></span>  
 <span data-ttu-id="2a4c0-108">所有已发布对象的架构和数据必须存在于每个对等方。</span><span class="sxs-lookup"><span data-stu-id="2a4c0-108">The schema and data for all published objects must be present at each peer.</span></span> <span data-ttu-id="2a4c0-109">选择以下选项之一：</span><span class="sxs-lookup"><span data-stu-id="2a4c0-109">Select one of the following options:</span></span>  
  
-   <span data-ttu-id="2a4c0-110">如果已经手动为已发布的对象创建了架构，或者已经还原了备份，并且在此备份后第一个发布数据库的数据未更改，则可以选择第一个选项。</span><span class="sxs-lookup"><span data-stu-id="2a4c0-110">Select the first option if you have manually created the schema for published objects or you have restored a backup, and no data changes have been made at the first publication database since the backup was taken.</span></span> <span data-ttu-id="2a4c0-111">如果手动创建了架构，则必须确保每个对等方存在所有所需的数据。</span><span class="sxs-lookup"><span data-stu-id="2a4c0-111">If you created the schema manually, you must ensure that all required data is present at each peer.</span></span> <span data-ttu-id="2a4c0-112">此选项对应于订阅属性 **sync_type** 的 **replication support only**值。</span><span class="sxs-lookup"><span data-stu-id="2a4c0-112">This option corresponds to a value of **replication support only** for the subscription property **sync_type**.</span></span>  
  
-   <span data-ttu-id="2a4c0-113">如果您已经还原了备份，并且在此备份后第一个发布数据库的数据发生了更改，则可以选择第二个选项。</span><span class="sxs-lookup"><span data-stu-id="2a4c0-113">Select the second option if you have restored a backup, and data changes have been made at the first publication database since the backup was taken.</span></span> <span data-ttu-id="2a4c0-114">复制必须立即传递备份中不包括的第一个发布数据库的更改。</span><span class="sxs-lookup"><span data-stu-id="2a4c0-114">Replication must now deliver changes from the first publication database that were not included in the backup.</span></span> <span data-ttu-id="2a4c0-115">此选项对应于订阅属性 **sync_type** 的 **initialize with backup**值。</span><span class="sxs-lookup"><span data-stu-id="2a4c0-115">This option corresponds to a value of **initialize with backup** for the subscription property **sync_type**.</span></span>  
  
     <span data-ttu-id="2a4c0-116">为对等复制启用发布时，将设置 **allow_initialize_from_backup** 发布属性。</span><span class="sxs-lookup"><span data-stu-id="2a4c0-116">When a publication is enabled for peer-to-peer replication, the **allow_initialize_from_backup** publication property is set.</span></span> <span data-ttu-id="2a4c0-117">复制立即开始跟踪在第一个发布数据库中所做的更改。</span><span class="sxs-lookup"><span data-stu-id="2a4c0-117">Replication immediately starts to track changes in the first publication database.</span></span> <span data-ttu-id="2a4c0-118">因此，如果选择了 **initialize with backup** 选项，则可以将这些更改传递给一个或多个对等方上的已还原数据库。</span><span class="sxs-lookup"><span data-stu-id="2a4c0-118">Therefore, these changes can be delivered to a restored database at one or more peers if the **initialize with backup** option is selected.</span></span> <span data-ttu-id="2a4c0-119">单击 **“浏览”** 按钮以找到所使用的备份，然后复制将从该备份中读取日志序列号 (LSN)。</span><span class="sxs-lookup"><span data-stu-id="2a4c0-119">Click the **Browse** button to locate the backup used, and replication will read the log sequence number (LSN) from the backup.</span></span> <span data-ttu-id="2a4c0-120">具有较高 LSN 的第一个发布数据库中的所有更改都将传递到每个对等方。</span><span class="sxs-lookup"><span data-stu-id="2a4c0-120">All changes in the first publication database that have a higher LSN will be delivered to each peer.</span></span>  
  
     <span data-ttu-id="2a4c0-121">如果是创建或添加到包含 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]的拓扑中，则此选项可能不可用。</span><span class="sxs-lookup"><span data-stu-id="2a4c0-121">This option might not be available if you are creating or adding to a topology that includes [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span> <span data-ttu-id="2a4c0-122">下表显示了当将节点添加到现有拓扑中时此选项是否可用。</span><span class="sxs-lookup"><span data-stu-id="2a4c0-122">The following table shows whether the option is available when you are adding a node to an existing topology.</span></span>  
  
    |<span data-ttu-id="2a4c0-123">新建节点</span><span class="sxs-lookup"><span data-stu-id="2a4c0-123">New node</span></span>|<span data-ttu-id="2a4c0-124">第一个节点</span><span class="sxs-lookup"><span data-stu-id="2a4c0-124">First node</span></span>|<span data-ttu-id="2a4c0-125">其他节点</span><span class="sxs-lookup"><span data-stu-id="2a4c0-125">Additional nodes</span></span>|<span data-ttu-id="2a4c0-126">选项</span><span class="sxs-lookup"><span data-stu-id="2a4c0-126">Option</span></span>|  
    |--------------|----------------|----------------------|------------|  
    |[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|<span data-ttu-id="2a4c0-127">已禁用</span><span class="sxs-lookup"><span data-stu-id="2a4c0-127">Disabled</span></span>|  
    |[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|<span data-ttu-id="2a4c0-128">无</span><span class="sxs-lookup"><span data-stu-id="2a4c0-128">None</span></span>|<span data-ttu-id="2a4c0-129">已禁用</span><span class="sxs-lookup"><span data-stu-id="2a4c0-129">Disabled</span></span>|  
    |[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|<span data-ttu-id="2a4c0-130">已禁用</span><span class="sxs-lookup"><span data-stu-id="2a4c0-130">Disabled</span></span>|  
    |[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|<span data-ttu-id="2a4c0-131">无</span><span class="sxs-lookup"><span data-stu-id="2a4c0-131">None</span></span>|<span data-ttu-id="2a4c0-132">Enabled</span><span class="sxs-lookup"><span data-stu-id="2a4c0-132">Enabled</span></span>|  
    |[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|<span data-ttu-id="2a4c0-133">无</span><span class="sxs-lookup"><span data-stu-id="2a4c0-133">None</span></span>|<span data-ttu-id="2a4c0-134">Enabled</span><span class="sxs-lookup"><span data-stu-id="2a4c0-134">Enabled</span></span>|  
    |[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|<span data-ttu-id="2a4c0-135">已启用</span><span class="sxs-lookup"><span data-stu-id="2a4c0-135">Enabled</span></span>|  
    |[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|<span data-ttu-id="2a4c0-136">无</span><span class="sxs-lookup"><span data-stu-id="2a4c0-136">None</span></span>|<span data-ttu-id="2a4c0-137">Enabled</span><span class="sxs-lookup"><span data-stu-id="2a4c0-137">Enabled</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2a4c0-138">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2a4c0-138">See Also</span></span>  
 <span data-ttu-id="2a4c0-139">[管理对等拓扑（复制 Transact-SQL 编程）](administration/administer-a-peer-to-peer-topology-replication-transact-sql-programming.md) </span><span class="sxs-lookup"><span data-stu-id="2a4c0-139">[Administer a Peer-to-Peer Topology &#40;Replication Transact-SQL Programming&#41;](administration/administer-a-peer-to-peer-topology-replication-transact-sql-programming.md) </span></span>  
 [<span data-ttu-id="2a4c0-140">@loopback_detection</span><span class="sxs-lookup"><span data-stu-id="2a4c0-140">Peer-to-Peer Transactional Replication</span></span>](transactional/peer-to-peer-transactional-replication.md)  
  
  
