---
title: 事务 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- OLE DB, transactions
- transactions [OLE DB]
- SQL Server Native Client OLE DB provider, transactions
ms.assetid: 3b41e33a-c1ca-4b2a-9464-312b0ed3ca89
author: rothja
ms.author: jroth
ms.openlocfilehash: 1067820e80f9c7a4e1af2c8a14c85bc9dbfdd6aa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589521"
---
# <a name="transactions"></a><span data-ttu-id="57b35-102">事务</span><span class="sxs-lookup"><span data-stu-id="57b35-102">Transactions</span></span>
  <span data-ttu-id="57b35-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供程序实现本地事务支持。</span><span class="sxs-lookup"><span data-stu-id="57b35-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider implements local transaction support.</span></span> <span data-ttu-id="57b35-104">使用者可借助 Microsoft 分布式事务处理协调器 (MS DTC) 来使用分布式事务或协调事务。</span><span class="sxs-lookup"><span data-stu-id="57b35-104">The consumer can use distributed or coordinated transactions by using Microsoft Distributed Transaction Coordinator (MS DTC).</span></span> <span data-ttu-id="57b35-105">对于需要跨多个会话的事务控制的使用者， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供程序可以加入由 MS DTC 启动和维护的事务。</span><span class="sxs-lookup"><span data-stu-id="57b35-105">For consumers requiring transaction control that spans multiple sessions, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider can join transactions initiated and maintained by MS DTC.</span></span>  
  
 <span data-ttu-id="57b35-106">默认情况下， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供程序使用自动提交事务模式，在该模式下，对使用者会话的每个单独操作都包含一个针对实例的完整事务 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="57b35-106">By default, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider uses an autocommit transaction mode, where each discrete action on a consumer session comprises a complete transaction against an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="57b35-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供程序的自动提交模式是本地的，自动提交事务从不跨越多个会话。</span><span class="sxs-lookup"><span data-stu-id="57b35-107">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider autocommit mode is local, and autocommit transactions never span more than a single session.</span></span>  
  
 <span data-ttu-id="57b35-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供程序公开**ITransactionLocal**接口，该接口允许使用者显式和隐式地在与实例的单个连接上启动事务 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="57b35-108">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider exposes the **ITransactionLocal** interface, allowing the consumer to use explicitly and implicitly start transactions on a single connection to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="57b35-109">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供程序不支持嵌套的本地事务。</span><span class="sxs-lookup"><span data-stu-id="57b35-109">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider does not support nested local transactions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="57b35-110">本节内容</span><span class="sxs-lookup"><span data-stu-id="57b35-110">In This Section</span></span>  
  
-   [<span data-ttu-id="57b35-111">支持本地事务</span><span class="sxs-lookup"><span data-stu-id="57b35-111">Supporting Local Transactions</span></span>](supporting-local-transactions.md)  
  
-   [<span data-ttu-id="57b35-112">支持分布式事务</span><span class="sxs-lookup"><span data-stu-id="57b35-112">Supporting Distributed Transactions</span></span>](supporting-distributed-transactions.md)  
  
-   [<span data-ttu-id="57b35-113">隔离级别 (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="57b35-113">Isolation Levels &#40;OLE DB&#41;</span></span>](isolation-levels-ole-db.md)  
  
## <a name="see-also"></a><span data-ttu-id="57b35-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="57b35-114">See Also</span></span>  
 [<span data-ttu-id="57b35-115">SQL Server Native Client (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="57b35-115">SQL Server Native Client &#40;OLE DB&#41;</span></span>](../native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
