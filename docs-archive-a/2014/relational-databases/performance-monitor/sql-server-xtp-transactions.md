---
title: XTP 事务 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: 443d67e4-1c7f-41d7-b18d-2d657f58c22a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 75fa8bc9a673d9e0e018b8578a35af2e46b5044c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688855"
---
# <a name="xtp-transactions"></a><span data-ttu-id="a1ae2-102">XTP 事务</span><span class="sxs-lookup"><span data-stu-id="a1ae2-102">XTP Transactions</span></span>
  <span data-ttu-id="a1ae2-103">XTP 事务性能对象包含与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中的 XTP 引擎事务相关的计数器。</span><span class="sxs-lookup"><span data-stu-id="a1ae2-103">The XTP Transactions performance object contains counters related to XTP engine transactions in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="a1ae2-104">下表说明了**XTP 事务**计数器。</span><span class="sxs-lookup"><span data-stu-id="a1ae2-104">This table describes the **XTP Transactions** counters.</span></span>  
  
|<span data-ttu-id="a1ae2-105">计数器</span><span class="sxs-lookup"><span data-stu-id="a1ae2-105">Counter</span></span>|<span data-ttu-id="a1ae2-106">说明</span><span class="sxs-lookup"><span data-stu-id="a1ae2-106">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a1ae2-107">**级联中止数/秒**</span><span class="sxs-lookup"><span data-stu-id="a1ae2-107">**Cascading aborts/sec**</span></span>|<span data-ttu-id="a1ae2-108">由于提交依赖关系回滚而每秒回滚的事务数（平均值）。</span><span class="sxs-lookup"><span data-stu-id="a1ae2-108">The number of transactions that rolled back to due a commit dependency rollback (on average), per second.</span></span>|  
|<span data-ttu-id="a1ae2-109">**采用的提交依赖关系数/秒**</span><span class="sxs-lookup"><span data-stu-id="a1ae2-109">**Commit dependencies taken/sec**</span></span>|<span data-ttu-id="a1ae2-110">事务每秒采用的提交依赖关系数（平均值）。</span><span class="sxs-lookup"><span data-stu-id="a1ae2-110">The number of commit dependencies taken by transactions (on average), per second.</span></span>|  
|<span data-ttu-id="a1ae2-111">**准备好的只读事务数/秒**</span><span class="sxs-lookup"><span data-stu-id="a1ae2-111">**Read-only transactions prepared/sec**</span></span>|<span data-ttu-id="a1ae2-112">准备好进行提交处理的每秒只读事务数。</span><span class="sxs-lookup"><span data-stu-id="a1ae2-112">The number of read-only transactions that were prepared for commit processing, per second.</span></span>|  
|<span data-ttu-id="a1ae2-113">**保存点刷新次数/秒**</span><span class="sxs-lookup"><span data-stu-id="a1ae2-113">**Save point refreshes/sec**</span></span>|<span data-ttu-id="a1ae2-114">保存点每秒“刷新”的次数（平均值）。</span><span class="sxs-lookup"><span data-stu-id="a1ae2-114">The number of times a savepoint was "refreshed", (on average), per second.</span></span> <span data-ttu-id="a1ae2-115">保存点刷新指现有保存点重置为事务生存期中的当前点。</span><span class="sxs-lookup"><span data-stu-id="a1ae2-115">A savepoint refresh is when an existing savepoint is reset to the current point in the transaction's lifetime.</span></span>|  
|<span data-ttu-id="a1ae2-116">**保存点回滚次数/秒**</span><span class="sxs-lookup"><span data-stu-id="a1ae2-116">**Save point rollbacks/sec**</span></span>|<span data-ttu-id="a1ae2-117">事务每秒回滚到保存点的次数（平均值）。</span><span class="sxs-lookup"><span data-stu-id="a1ae2-117">The number of times a transaction rolled back to a save point (on average), per second.</span></span>|  
|<span data-ttu-id="a1ae2-118">**创建的保存点数/秒**</span><span class="sxs-lookup"><span data-stu-id="a1ae2-118">**Save points created /sec**</span></span>|<span data-ttu-id="a1ae2-119">每秒创建的保存点数（平均值）。</span><span class="sxs-lookup"><span data-stu-id="a1ae2-119">The number of save points created (on average), per second.</span></span>|  
|<span data-ttu-id="a1ae2-120">**事务验证失败数/秒**</span><span class="sxs-lookup"><span data-stu-id="a1ae2-120">**Transaction validation failure/sec**</span></span>|<span data-ttu-id="a1ae2-121">每秒验证失败的事务数（平均值）。</span><span class="sxs-lookup"><span data-stu-id="a1ae2-121">The number of transactions that failed validation processing (on average), per second.</span></span>|  
|<span data-ttu-id="a1ae2-122">**用户中止的事务数/秒**</span><span class="sxs-lookup"><span data-stu-id="a1ae2-122">**Transactions aborted by user/sec**</span></span>|<span data-ttu-id="a1ae2-123">用户每秒中止的事务数（平均值）。</span><span class="sxs-lookup"><span data-stu-id="a1ae2-123">The number of transactions that were aborted by the user (on average), per second.</span></span>|  
|<span data-ttu-id="a1ae2-124">**中止的事务数/秒**</span><span class="sxs-lookup"><span data-stu-id="a1ae2-124">**Transactions aborted/sec**</span></span>|<span data-ttu-id="a1ae2-125">（用户和系统）每秒中止的事务数（平均值）。</span><span class="sxs-lookup"><span data-stu-id="a1ae2-125">The number of transactions that aborted (both by the user and the system, on average), per second.</span></span>|  
|<span data-ttu-id="a1ae2-126">**创建的事务数/秒**</span><span class="sxs-lookup"><span data-stu-id="a1ae2-126">**Transactions created/sec**</span></span>|<span data-ttu-id="a1ae2-127">系统中每秒创建的事务数（平均值）。</span><span class="sxs-lookup"><span data-stu-id="a1ae2-127">The number of transactions created in the system (on average), per second.</span></span><br /><br /> <span data-ttu-id="a1ae2-128">对 XTP 事务的计数方式不同于基于磁盘的事务（反映在“数据库:事务数/秒”中）。</span><span class="sxs-lookup"><span data-stu-id="a1ae2-128">XTP transactions are counted differently than disk-based transactions (as reflected in Databases:Transactions/sec).</span></span> <span data-ttu-id="a1ae2-129">例如，“创建的事务数/秒”对只读事务进行计数，而“数据库:事务数/秒”则不然。</span><span class="sxs-lookup"><span data-stu-id="a1ae2-129">For example, Transactions created/sec counts read/only transactions, while Databases:Transactions/sec does not.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a1ae2-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a1ae2-130">See Also</span></span>  
 [<span data-ttu-id="a1ae2-131">XTP &#40;内存中 OLTP&#41; 性能计数器</span><span class="sxs-lookup"><span data-stu-id="a1ae2-131">XTP &#40;In-Memory OLTP&#41; Performance Counters</span></span>](../../integration-services/performance/performance-counters.md)  
  
  
