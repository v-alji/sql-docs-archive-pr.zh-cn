---
title: 隔离级别 (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- OLE DB, transactions
- isolation levels [OLE DB]
- transactions [OLE DB]
- SQL Server Native Client OLE DB provider, transactions
ms.assetid: d70ee72c-6e2a-4bcd-9456-4a697a866361
author: rothja
ms.author: jroth
ms.openlocfilehash: c7f6cbff4e68eaedd3e78a82cddd872ba5f8f19e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587778"
---
# <a name="isolation-levels-ole-db"></a><span data-ttu-id="bafde-102">隔离级别 (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="bafde-102">Isolation Levels (OLE DB)</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="bafde-103">客户端可以控制连接的事务隔离级别。</span><span class="sxs-lookup"><span data-stu-id="bafde-103">clients can control transaction-isolation levels for a connection.</span></span> <span data-ttu-id="bafde-104">若要控制事务隔离级别， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供程序使用：</span><span class="sxs-lookup"><span data-stu-id="bafde-104">To control transaction-isolation level, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider consumer uses:</span></span>  
  
-   <span data-ttu-id="bafde-105">DBPROPSET_SESSION [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供程序默认自动提交模式 DBPROP_SESS_AUTOCOMMITISOLEVELS。</span><span class="sxs-lookup"><span data-stu-id="bafde-105">DBPROPSET_SESSION property DBPROP_SESS_AUTOCOMMITISOLEVELS for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider default autocommit mode.</span></span>  
  
     <span data-ttu-id="bafde-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]级别的 Native Client OLE DB 提供程序默认为 DBPROPVAL_TI_READCOMMITTED。</span><span class="sxs-lookup"><span data-stu-id="bafde-106">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider default for the level is DBPROPVAL_TI_READCOMMITTED.</span></span>  
  
-   <span data-ttu-id="bafde-107">将 ITransactionLocal::StartTransaction 方法的 isoLevel 参数用于本地手动提交事务\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="bafde-107">The *isoLevel* parameter of the **ITransactionLocal::StartTransaction** method for local manual-commit transactions.</span></span>  
  
-   <span data-ttu-id="bafde-108">将 ITransactionDispenser::BeginTransaction 方法的 isoLevel 参数用于 MS DTC 协调的分布式事务\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="bafde-108">The *isoLevel* parameter of the **ITransactionDispenser::BeginTransaction** method for MS DTC-coordinated distributed transactions.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="bafde-109">在脏读隔离级别允许只读访问。</span><span class="sxs-lookup"><span data-stu-id="bafde-109">allows read-only access at the dirty read isolation level.</span></span> <span data-ttu-id="bafde-110">所有其他级别通过将锁应用到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 对象来限制并发。</span><span class="sxs-lookup"><span data-stu-id="bafde-110">All other levels restrict concurrency by applying locks to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] objects.</span></span> <span data-ttu-id="bafde-111">当客户端需要更高的并发级别时，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 会为数据并发访问设置更多限制。</span><span class="sxs-lookup"><span data-stu-id="bafde-111">As the client requires greater concurrency levels, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] applies greater restrictions on concurrent access to data.</span></span> <span data-ttu-id="bafde-112">为了保持对数据的最高级别的并发访问， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者应智能地控制其针对特定并发级别的请求。</span><span class="sxs-lookup"><span data-stu-id="bafde-112">To maintain the highest level of concurrent access to data, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider consumer should intelligently control its requests for specific concurrency levels.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] <span data-ttu-id="bafde-113">引入了快照隔离级别。</span><span class="sxs-lookup"><span data-stu-id="bafde-113">introduced snapshot isolation level.</span></span> <span data-ttu-id="bafde-114">有关详细信息，请参阅[使用快照隔离](../native-client/features/working-with-snapshot-isolation.md)。</span><span class="sxs-lookup"><span data-stu-id="bafde-114">For more information, see [Working with Snapshot Isolation](../native-client/features/working-with-snapshot-isolation.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bafde-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bafde-115">See Also</span></span>  
 [<span data-ttu-id="bafde-116">事务</span><span class="sxs-lookup"><span data-stu-id="bafde-116">Transactions</span></span>](transactions.md)  
  
  
