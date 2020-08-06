---
title: 支持分布式事务 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- OLE DB, transactions
- distributed transactions [OLE DB]
- MS DTC
- transactions [OLE DB]
- SQL Server Native Client OLE DB provider, transactions
- ITransactionJoin interface
- MS DTC, about distributed transaction support
ms.assetid: d250b43b-9260-4ea4-90cc-57d9a2f67ea7
author: rothja
ms.author: jroth
ms.openlocfilehash: 5a30a44dc007852922aa71685728b26e5bb872c3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692361"
---
# <a name="supporting-distributed-transactions"></a><span data-ttu-id="e075e-102">支持分布式事务</span><span class="sxs-lookup"><span data-stu-id="e075e-102">Supporting Distributed Transactions</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="e075e-103">Native Client OLE DB 访问接口使用者可以使用**ITransactionJoin：： JoinTransaction**方法参与由 Microsoft 分布式事务处理协调器 (MS DTC) 协调的分布式事务。</span><span class="sxs-lookup"><span data-stu-id="e075e-103">Native Client OLE DB provider consumers can use the **ITransactionJoin::JoinTransaction** method to participate in a distributed transaction coordinated by Microsoft Distributed Transaction Coordinator (MS DTC).</span></span>  
  
 <span data-ttu-id="e075e-104">MS DTC 公开 COM 对象，这些对象允许客户端跨各种数据存储的多个连接来启动和参与协调的事务。</span><span class="sxs-lookup"><span data-stu-id="e075e-104">MS DTC exposes COM objects that allow clients to initiate and participate in coordinated transactions across multiple connections to a variety of data stores.</span></span> <span data-ttu-id="e075e-105">若要启动某个事务， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供程序使用者使用了 MS DTC **ITransactionDispenser**接口。</span><span class="sxs-lookup"><span data-stu-id="e075e-105">To initiate a transaction, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider consumer uses the MS DTC **ITransactionDispenser** interface.</span></span> <span data-ttu-id="e075e-106">ITransactionDispenser 的 BeginTransaction 成员返回分布式事务对象的引用\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e075e-106">The **BeginTransaction** member of **ITransactionDispenser** returns a reference on a distributed transaction object.</span></span> <span data-ttu-id="e075e-107">使用 JoinTransaction 将此引用传递给 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供**JoinTransaction**程序。</span><span class="sxs-lookup"><span data-stu-id="e075e-107">This reference is passed to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider using **JoinTransaction**.</span></span>  
  
 <span data-ttu-id="e075e-108">MS DTC 支持对分布式事务的异步提交和中止。</span><span class="sxs-lookup"><span data-stu-id="e075e-108">MS DTC supports asynchronous commit and abort on distributed transactions.</span></span> <span data-ttu-id="e075e-109">为了通知异步事务状态，使用者实现 ITransactionOutcomeEvents 接口并将该接口与 MS DTC 事务对象连接\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e075e-109">For notification on asynchronous transaction status, the consumer implements the **ITransactionOutcomeEvents** interface and connects the interface to an MS DTC transaction object.</span></span>  
  
 <span data-ttu-id="e075e-110">对于分布式事务， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供程序实现**ITransactionJoin：： JoinTransaction**参数，如下所示。</span><span class="sxs-lookup"><span data-stu-id="e075e-110">For distributed transactions, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider implements **ITransactionJoin::JoinTransaction** parameters as follows.</span></span>  
  
|<span data-ttu-id="e075e-111">参数</span><span class="sxs-lookup"><span data-stu-id="e075e-111">Parameter</span></span>|<span data-ttu-id="e075e-112">说明</span><span class="sxs-lookup"><span data-stu-id="e075e-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e075e-113">punkTransactionCoord\*\*</span><span class="sxs-lookup"><span data-stu-id="e075e-113">*punkTransactionCoord*</span></span>|<span data-ttu-id="e075e-114">指向 MS DTC 事务对象的指针。</span><span class="sxs-lookup"><span data-stu-id="e075e-114">A pointer to an MS DTC transaction object.</span></span>|  
|<span data-ttu-id="e075e-115">IsoLevel\*\*</span><span class="sxs-lookup"><span data-stu-id="e075e-115">*IsoLevel*</span></span>|<span data-ttu-id="e075e-116">由 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供程序忽略。</span><span class="sxs-lookup"><span data-stu-id="e075e-116">Ignored by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider.</span></span> <span data-ttu-id="e075e-117">使用者在从 MS DTC 获取事务对象时，确定由 MS DTC 协调的事务的隔离级别。</span><span class="sxs-lookup"><span data-stu-id="e075e-117">The isolation level for MS DTC-coordinated transactions is determined when the consumer acquires a transaction object from MS DTC.</span></span>|  
|<span data-ttu-id="e075e-118">IsoFlags\*\*</span><span class="sxs-lookup"><span data-stu-id="e075e-118">*IsoFlags*</span></span>|<span data-ttu-id="e075e-119">必须为 0。</span><span class="sxs-lookup"><span data-stu-id="e075e-119">Must be 0.</span></span> <span data-ttu-id="e075e-120">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]如果使用者指定了其他任何值，则 Native Client OLE DB 提供程序将返回 XACT_E_NOISORETAIN。</span><span class="sxs-lookup"><span data-stu-id="e075e-120">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider returns XACT_E_NOISORETAIN if any other value is specified by the consumer.</span></span>|  
|<span data-ttu-id="e075e-121">POtherOptions\*\*</span><span class="sxs-lookup"><span data-stu-id="e075e-121">*POtherOptions*</span></span>|<span data-ttu-id="e075e-122">如果不为 NULL，则 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供程序从接口请求 options 对象。</span><span class="sxs-lookup"><span data-stu-id="e075e-122">If not NULL, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider requests the options object from the interface.</span></span> <span data-ttu-id="e075e-123">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]如果 options 对象的*ulTimeout*成员不为零，则 Native Client OLE DB 提供程序将返回 XACT_E_NOTIMEOUT。</span><span class="sxs-lookup"><span data-stu-id="e075e-123">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider returns XACT_E_NOTIMEOUT if the options object's *ulTimeout* member is not zero.</span></span> <span data-ttu-id="e075e-124">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供程序忽略*szDescription*成员的值。</span><span class="sxs-lookup"><span data-stu-id="e075e-124">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider ignores the value of the *szDescription* member.</span></span>|  
  
 <span data-ttu-id="e075e-125">下面的示例通过使用 MS DTC 来协调事务：</span><span class="sxs-lookup"><span data-stu-id="e075e-125">This example coordinates transaction by using MS DTC.</span></span>  
  
```  
// Interfaces used in the example.  
IDBCreateSession*       pIDBCreateSession   = NULL;  
ITransactionJoin*       pITransactionJoin   = NULL;  
IDBCreateCommand*       pIDBCreateCommand   = NULL;  
IRowset*                pIRowset            = NULL;  
  
// Transaction dispenser and transaction from MS DTC.  
ITransactionDispenser*  pITransactionDispenser = NULL;  
ITransaction*           pITransaction       = NULL;  
  
    HRESULT             hr;  
  
// Get the command creation interface for the session.  
if (FAILED(hr = pIDBCreateSession->CreateSession(NULL,  
     IID_IDBCreateCommand, (IUnknown**) &pIDBCreateCommand)))  
    {  
    // Process error from session creation. Release any references and  
    // return.  
    }  
  
// Get a transaction dispenser object from MS DTC and  
// start a transaction.  
if (FAILED(hr = DtcGetTransactionManager(NULL, NULL,  
    IID_ITransactionDispenser, 0, 0, NULL,  
    (void**) &pITransactionDispenser)))  
    {  
    // Process error message from MS DTC, release any references,  
    // and then return.  
    }  
if (FAILED(hr = pITransactionDispenser->BeginTransaction(  
    NULL, ISOLATIONLEVEL_READCOMMITTED, ISOFLAG_RETAIN_DONTCARE,  
    NULL, &pITransaction)))  
    {  
    // Process error message from MS DTC, release any references,  
    // and then return.  
    }  
  
// Join the transaction.  
if (FAILED(pIDBCreateCommand->QueryInterface(IID_ITransactionJoin,  
    (void**) &pITransactionJoin)))  
    {  
    // Process failure to get an interface, release any references, and  
    // then return.  
    }  
if (FAILED(pITransactionJoin->JoinTransaction(  
    (IUnknown*) pITransaction, 0, 0, NULL)))  
    {  
    // Process join failure, release any references, and then return.  
    }  
  
// Get data into a rowset, then update the data. Functions are not  
// illustrated in this example.  
if (FAILED(hr = ExecuteCommand(pIDBCreateCommand, &pIRowset)))  
    {  
    // Release any references and return.  
    }  
  
// If rowset data update fails, then terminate the transaction, else  
// commit. The example doesn't retain the rowset.  
if (FAILED(hr = UpdateDataInRowset(pIRowset, bDelayedUpdate)))  
    {  
    // Get error from update, then abort.  
    pITransaction->Abort(NULL, FALSE, FALSE);  
    }  
else  
    {  
    if (FAILED(hr = pITransaction->Commit(FALSE, 0, 0)))  
        {  
        // Get error from failed commit.  
        //  
        // If a distributed commit fails, application logic could  
        // analyze failure and retry. In this example, terminate. The   
        // consumer must resolve this somehow.  
        pITransaction->Abort(NULL, FALSE, FALSE);  
        }  
    }  
  
if (FAILED(hr))  
    {  
    // Update of data or commit failed. Release any references and  
    // return.  
    }  
  
// Un-enlist from the distributed transaction by setting   
// the transaction object pointer to NULL.  
if (FAILED(pITransactionJoin->JoinTransaction(  
    (IUnknown*) NULL, 0, 0, NULL)))  
    {  
    // Process failure, and then return.  
    }  
  
// Release any references and continue.  
```  
  
## <a name="see-also"></a><span data-ttu-id="e075e-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e075e-126">See Also</span></span>  
 [<span data-ttu-id="e075e-127">事务</span><span class="sxs-lookup"><span data-stu-id="e075e-127">Transactions</span></span>](transactions.md)  
  
  
