---
title: XTP (内存中 OLTP) 性能计数器 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: fe3cbaf4-65f4-44c5-acc6-7b735cda0c5d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 4363a526ada3694e92d18cac0d7abe8a26f6a92f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688859"
---
# <a name="xtp-in-memory-oltp-performance-counters"></a><span data-ttu-id="de96a-102">XTP（内存中 OLTP）性能计数器</span><span class="sxs-lookup"><span data-stu-id="de96a-102">XTP (In-Memory OLTP) Performance Counters</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="de96a-103">提供了对象和计数器，性能监视器可以使用它们来监视内存中 OLTP 活动。</span><span class="sxs-lookup"><span data-stu-id="de96a-103">provides objects and counters that can be used by Performance Monitor to monitor In-Memory OLTP activity.</span></span>  
  
##  <a name="xtp-in-memory-oltp-performance-objects"></a><a name="SQLServerPOs"></a><span data-ttu-id="de96a-104">XTP (内存中 OLTP) 性能对象</span><span class="sxs-lookup"><span data-stu-id="de96a-104">XTP (In-Memory OLTP) Performance Objects</span></span>  
 <span data-ttu-id="de96a-105">下表介绍 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 对象：</span><span class="sxs-lookup"><span data-stu-id="de96a-105">The following table describes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] objects.</span></span>  
  
|<span data-ttu-id="de96a-106">性能对象</span><span class="sxs-lookup"><span data-stu-id="de96a-106">Performance object</span></span>|<span data-ttu-id="de96a-107">说明</span><span class="sxs-lookup"><span data-stu-id="de96a-107">Description</span></span>|  
|------------------------|-----------------|  
|[<span data-ttu-id="de96a-108">XTP 游标</span><span class="sxs-lookup"><span data-stu-id="de96a-108">XTP Cursors</span></span>](../cursors.md)|<span data-ttu-id="de96a-109">XTP 游标性能对象包含与内部 XTP 引擎游标相关的计数器。</span><span class="sxs-lookup"><span data-stu-id="de96a-109">The XTP Cursors performance object contains counters related to internal XTP engine cursors.</span></span> <span data-ttu-id="de96a-110">游标是 XTP 引擎用于处理 [!INCLUDE[tsql](../../includes/tsql-md.md)] 查询的低级构建基块。</span><span class="sxs-lookup"><span data-stu-id="de96a-110">Cursors are the low-level building blocks the XTP engine uses to process [!INCLUDE[tsql](../../includes/tsql-md.md)] queries.</span></span> <span data-ttu-id="de96a-111">因此，您通常不能直接控制游标。</span><span class="sxs-lookup"><span data-stu-id="de96a-111">As such, you do not typically have direct control over them.</span></span>|  
|[<span data-ttu-id="de96a-112">XTP 垃圾收集</span><span class="sxs-lookup"><span data-stu-id="de96a-112">XTP Garbage Collection</span></span>](sql-server-xtp-garbage-collection.md)|<span data-ttu-id="de96a-113">XTP 垃圾收集性能对象包含与 XTP 引擎的垃圾收集器相关的计数器。</span><span class="sxs-lookup"><span data-stu-id="de96a-113">The XTP Garbage Collection performance object contains counters related to the XTP engine's garbage collector.</span></span>|  
|[<span data-ttu-id="de96a-114">XTP 虚拟处理器</span><span class="sxs-lookup"><span data-stu-id="de96a-114">XTP Phantom Processor</span></span>](sql-server-xtp-phantom-processor.md)|<span data-ttu-id="de96a-115">XTP 虚拟处理器性能对象包含与 XTP 引擎的虚拟处理子系统相关的计数器。</span><span class="sxs-lookup"><span data-stu-id="de96a-115">The XTP Phantom Processor performance object contains counters related to the XTP engine's phantom processing subsystem.</span></span> <span data-ttu-id="de96a-116">此组件用于检测在 SERIALIZABLE 隔离级别运行的事务中的虚拟行。</span><span class="sxs-lookup"><span data-stu-id="de96a-116">This component is responsible for detecting phantom rows in transactions running at the SERIALIZABLE isolation level.</span></span>|  
|[<span data-ttu-id="de96a-117">XTP 存储</span><span class="sxs-lookup"><span data-stu-id="de96a-117">XTP Storage</span></span>](sql-server-xtp-storage.md)|<span data-ttu-id="de96a-118">XTP 存储性能对象包含与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中的 XTP 存储相关的计数器。</span><span class="sxs-lookup"><span data-stu-id="de96a-118">The XTP Storage performance object contains counters related to XTP storage in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>|  
|[<span data-ttu-id="de96a-119">XTP 事务日志</span><span class="sxs-lookup"><span data-stu-id="de96a-119">XTP Transaction Log</span></span>](sql-server-xtp-transaction-log.md)|<span data-ttu-id="de96a-120">XTP 事务日志性能对象包含与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中的 XTP 事务日志记录相关的计数器。</span><span class="sxs-lookup"><span data-stu-id="de96a-120">The XTP Transaction Log performance object contains counters related to XTP transaction logging in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>|  
|[<span data-ttu-id="de96a-121">XTP 事务</span><span class="sxs-lookup"><span data-stu-id="de96a-121">XTP Transactions</span></span>](sql-server-xtp-transactions.md)|<span data-ttu-id="de96a-122">XTP 事务性能对象包含与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中的 XTP 引擎事务相关的计数器。</span><span class="sxs-lookup"><span data-stu-id="de96a-122">The XTP Transactions performance object contains counters related to XTP engine transactions in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>|  
  
  
