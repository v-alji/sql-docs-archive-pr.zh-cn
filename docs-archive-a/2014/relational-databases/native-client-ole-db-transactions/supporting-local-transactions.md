---
title: 支持本地事务 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- OLE DB, transactions
- autocommit mode
- transactions [OLE DB]
- ITransactionLocal interface
- SQL Server Native Client OLE DB provider, transactions
- local transactions [OLE DB]
ms.assetid: 78f2e5fc-b6fb-4eda-9f71-991a4d6c4902
author: rothja
ms.author: jroth
ms.openlocfilehash: a9bc11a038e56517aa42619117c371c1319b9ffe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589523"
---
# <a name="supporting-local-transactions"></a><span data-ttu-id="a8d60-102">支持本地事务</span><span class="sxs-lookup"><span data-stu-id="a8d60-102">Supporting Local Transactions</span></span>
  <span data-ttu-id="a8d60-103">会话分隔 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 本机客户端 OLE DB 提供程序本地事务的事务范围。</span><span class="sxs-lookup"><span data-stu-id="a8d60-103">A session delimits transaction scope for a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider local transaction.</span></span> <span data-ttu-id="a8d60-104">当使用者的方向时， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native client OLE DB 提供程序将请求提交给已连接的实例 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，该请求构成了 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native client OLE DB 提供程序的工作单元。</span><span class="sxs-lookup"><span data-stu-id="a8d60-104">When, at the direction of a consumer, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider submits a request to a connected instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the request constitutes a unit of work for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider.</span></span> <span data-ttu-id="a8d60-105">本地事务始终 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OLE DB 提供程序会话中包装一个或多个工作单元。</span><span class="sxs-lookup"><span data-stu-id="a8d60-105">Local transactions always wrap one or more units of work on a single [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider session.</span></span>  
  
 <span data-ttu-id="a8d60-106">使用默认的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供程序自动提交模式，单个工作单元被视为本地事务的作用域。</span><span class="sxs-lookup"><span data-stu-id="a8d60-106">Using the default [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider autocommit mode, a single unit of work is treated as the scope of a local transaction.</span></span> <span data-ttu-id="a8d60-107">只能有一个单元参与本地事务。</span><span class="sxs-lookup"><span data-stu-id="a8d60-107">Only one unit participates in the local transaction.</span></span> <span data-ttu-id="a8d60-108">当创建会话时， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供程序会为会话启动一个事务。</span><span class="sxs-lookup"><span data-stu-id="a8d60-108">When a session is created, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider begins a transaction for the session.</span></span> <span data-ttu-id="a8d60-109">在成功完成工作单元之后提交工作。</span><span class="sxs-lookup"><span data-stu-id="a8d60-109">Upon successful completion of a work unit, the work is committed.</span></span> <span data-ttu-id="a8d60-110">如果失败，则回滚任何已开始的任何工作，并向使用者报告错误。</span><span class="sxs-lookup"><span data-stu-id="a8d60-110">On failure, any work begun is rolled back and the error is reported to the consumer.</span></span> <span data-ttu-id="a8d60-111">在任一情况下， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供程序都将为会话启动新的本地事务，以便在事务中执行所有工作。</span><span class="sxs-lookup"><span data-stu-id="a8d60-111">In either case, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider begins a new local transaction for the session so that all work is conducted within a transaction.</span></span>  
  
 <span data-ttu-id="a8d60-112">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供程序使用者可以通过**ITransactionLocal**接口来更精确地控制本地事务范围。</span><span class="sxs-lookup"><span data-stu-id="a8d60-112">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider consumer can direct more precise control over local transaction scope by using the **ITransactionLocal** interface.</span></span> <span data-ttu-id="a8d60-113">当使用者会话启动事务时，事务起点和最终 Commit 或 Abort 方法调用之间的所有会话工作单元都被视为原子单元\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a8d60-113">When a consumer session initiates a transaction, all session work units between the transaction start point and the eventual **Commit** or **Abort** method calls are treated as an atomic unit.</span></span> <span data-ttu-id="a8d60-114">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]当使用者定向到此时，Native Client OLE DB 提供程序将隐式启动事务。</span><span class="sxs-lookup"><span data-stu-id="a8d60-114">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider implicitly begins a transaction when directed to do so by the consumer.</span></span> <span data-ttu-id="a8d60-115">如果使用者未请求保持，该会话恢复为父事务级行为，通常为自动提交模式。</span><span class="sxs-lookup"><span data-stu-id="a8d60-115">If the consumer does not request retention, the session reverts to parent transaction-level behavior, most commonly autocommit mode.</span></span>  
  
 <span data-ttu-id="a8d60-116">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供程序支持**ITransactionLocal：： StartTransaction**参数，如下所示。</span><span class="sxs-lookup"><span data-stu-id="a8d60-116">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider supports **ITransactionLocal::StartTransaction** parameters as follows.</span></span>  
  
|<span data-ttu-id="a8d60-117">参数</span><span class="sxs-lookup"><span data-stu-id="a8d60-117">Parameter</span></span>|<span data-ttu-id="a8d60-118">说明</span><span class="sxs-lookup"><span data-stu-id="a8d60-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a8d60-119">\*\* isoLevel[in]</span><span class="sxs-lookup"><span data-stu-id="a8d60-119">*isoLevel*[in]</span></span>|<span data-ttu-id="a8d60-120">用于该事务的隔离级别。</span><span class="sxs-lookup"><span data-stu-id="a8d60-120">The isolation level to be used with this transaction.</span></span> <span data-ttu-id="a8d60-121">在本地事务中， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供程序支持以下各项：</span><span class="sxs-lookup"><span data-stu-id="a8d60-121">In local transactions, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider supports the following:</span></span><br /><br /> <span data-ttu-id="a8d60-122">-ISOLATIONLEVEL_UNSPECIFIED</span><span class="sxs-lookup"><span data-stu-id="a8d60-122">-   ISOLATIONLEVEL_UNSPECIFIED</span></span><br /><span data-ttu-id="a8d60-123">-ISOLATIONLEVEL_CHAOS</span><span class="sxs-lookup"><span data-stu-id="a8d60-123">-   ISOLATIONLEVEL_CHAOS</span></span><br /><span data-ttu-id="a8d60-124">-ISOLATIONLEVEL_READUNCOMMITTED</span><span class="sxs-lookup"><span data-stu-id="a8d60-124">-   ISOLATIONLEVEL_READUNCOMMITTED</span></span><br /><span data-ttu-id="a8d60-125">-ISOLATIONLEVEL_READCOMMITTED</span><span class="sxs-lookup"><span data-stu-id="a8d60-125">-   ISOLATIONLEVEL_READCOMMITTED</span></span><br /><span data-ttu-id="a8d60-126">-ISOLATIONLEVEL_REPEATABLEREAD</span><span class="sxs-lookup"><span data-stu-id="a8d60-126">-   ISOLATIONLEVEL_REPEATABLEREAD</span></span><br /><span data-ttu-id="a8d60-127">-ISOLATIONLEVEL_CURSORSTABILITY</span><span class="sxs-lookup"><span data-stu-id="a8d60-127">-   ISOLATIONLEVEL_CURSORSTABILITY</span></span><br /><span data-ttu-id="a8d60-128">-ISOLATIONLEVEL_REPEATABLEREAD</span><span class="sxs-lookup"><span data-stu-id="a8d60-128">-   ISOLATIONLEVEL_REPEATABLEREAD</span></span><br /><span data-ttu-id="a8d60-129">-ISOLATIONLEVEL_SERIALIZABLE</span><span class="sxs-lookup"><span data-stu-id="a8d60-129">-   ISOLATIONLEVEL_SERIALIZABLE</span></span><br /><span data-ttu-id="a8d60-130">-ISOLATIONLEVEL_ISOLATED</span><span class="sxs-lookup"><span data-stu-id="a8d60-130">-   ISOLATIONLEVEL_ISOLATED</span></span><br /><span data-ttu-id="a8d60-131">-ISOLATIONLEVEL_SNAPSHOT**注意：** 从开始 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] ，无论是否为数据库启用了版本控制，ISOLATIONLEVEL_SNAPSHOT 对于*isoLevel*参数都有效。</span><span class="sxs-lookup"><span data-stu-id="a8d60-131">-   ISOLATIONLEVEL_SNAPSHOT **Note:**  Beginning with [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], ISOLATIONLEVEL_SNAPSHOT is valid for the *isoLevel* argument whether or not versioning is enabled for the database.</span></span> <span data-ttu-id="a8d60-132">但是，如果用户尝试执行语句，并且未启用版本支持和/或数据库不为只读，则将发生错误。</span><span class="sxs-lookup"><span data-stu-id="a8d60-132">However, an error will occur if the user attempts to execute a statement and versioning is not enabled and/or the database is not read-only.</span></span> <span data-ttu-id="a8d60-133">此外，如果在连接到 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以前的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 版本时将 ISOLATIONLEVEL_SNAPSHOT 指定为 isoLevel，将发生 XACT_E_ISOLATIONLEVEL 错误\*\*。</span><span class="sxs-lookup"><span data-stu-id="a8d60-133">In addition, the error XACT_E_ISOLATIONLEVEL will occur if ISOLATIONLEVEL_SNAPSHOT is specified as the *isoLevel* when connected to a version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] earlier than [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span>|  
|<span data-ttu-id="a8d60-134">\*\* isoFlags[in]</span><span class="sxs-lookup"><span data-stu-id="a8d60-134">*isoFlags*[in]</span></span>|<span data-ttu-id="a8d60-135">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供程序返回除零以外的任何值的错误。</span><span class="sxs-lookup"><span data-stu-id="a8d60-135">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider returns an error for any value other than zero.</span></span>|  
|<span data-ttu-id="a8d60-136">\*\* pOtherOptions[in]</span><span class="sxs-lookup"><span data-stu-id="a8d60-136">*pOtherOptions*[in]</span></span>|<span data-ttu-id="a8d60-137">如果不为 NULL，则 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供程序从接口请求 options 对象。</span><span class="sxs-lookup"><span data-stu-id="a8d60-137">If not NULL, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider requests the options object from the interface.</span></span> <span data-ttu-id="a8d60-138">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]如果 options 对象的*ulTimeout*成员不为零，则 Native Client OLE DB 提供程序将返回 XACT_E_NOTIMEOUT。</span><span class="sxs-lookup"><span data-stu-id="a8d60-138">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider returns XACT_E_NOTIMEOUT if the options object's *ulTimeout* member is not zero.</span></span> <span data-ttu-id="a8d60-139">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供程序忽略*szDescription*成员的值。</span><span class="sxs-lookup"><span data-stu-id="a8d60-139">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider ignores the value of the *szDescription* member.</span></span>|  
|<span data-ttu-id="a8d60-140">\*\* pulTransactionLevel[out]</span><span class="sxs-lookup"><span data-stu-id="a8d60-140">*pulTransactionLevel*[out]</span></span>|<span data-ttu-id="a8d60-141">如果不为 NULL，则 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供程序将返回事务的嵌套级别。</span><span class="sxs-lookup"><span data-stu-id="a8d60-141">If not NULL, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider returns the nested level of the transaction.</span></span>|  
  
 <span data-ttu-id="a8d60-142">对于本地事务， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供程序实现**ITransaction：： Abort**参数，如下所示。</span><span class="sxs-lookup"><span data-stu-id="a8d60-142">For local transactions, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider implements **ITransaction::Abort** parameters as follows.</span></span>  
  
|<span data-ttu-id="a8d60-143">参数</span><span class="sxs-lookup"><span data-stu-id="a8d60-143">Parameter</span></span>|<span data-ttu-id="a8d60-144">说明</span><span class="sxs-lookup"><span data-stu-id="a8d60-144">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a8d60-145">\*\* pboidReason[in]</span><span class="sxs-lookup"><span data-stu-id="a8d60-145">*pboidReason*[in]</span></span>|<span data-ttu-id="a8d60-146">忽略（如果设置）。</span><span class="sxs-lookup"><span data-stu-id="a8d60-146">Ignored if set.</span></span> <span data-ttu-id="a8d60-147">可以安全地为 NULL。</span><span class="sxs-lookup"><span data-stu-id="a8d60-147">Can safely be NULL.</span></span>|  
|<span data-ttu-id="a8d60-148">\*\* fRetaining[in]</span><span class="sxs-lookup"><span data-stu-id="a8d60-148">*fRetaining*[in]</span></span>|<span data-ttu-id="a8d60-149">当该参数为 TRUE 时，将针对会话隐式开始新的事务。</span><span class="sxs-lookup"><span data-stu-id="a8d60-149">When TRUE, a new transaction is implicitly begun for the session.</span></span> <span data-ttu-id="a8d60-150">事务必须由使用者提交或中止。</span><span class="sxs-lookup"><span data-stu-id="a8d60-150">The transaction must be committed or terminated by the consumer.</span></span> <span data-ttu-id="a8d60-151">为 FALSE 时， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供程序将恢复为会话的自动提交模式。</span><span class="sxs-lookup"><span data-stu-id="a8d60-151">When FALSE, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider reverts to autocommit mode for the session.</span></span>|  
|<span data-ttu-id="a8d60-152">\*\* fAsync[in]</span><span class="sxs-lookup"><span data-stu-id="a8d60-152">*fAsync*[in]</span></span>|<span data-ttu-id="a8d60-153">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供程序不支持异步中止。</span><span class="sxs-lookup"><span data-stu-id="a8d60-153">Asynchronous abort is not supported by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider.</span></span> <span data-ttu-id="a8d60-154">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]如果值不为 FALSE，则 Native Client OLE DB 提供程序将返回 XACT_E_NOTSUPPORTED。</span><span class="sxs-lookup"><span data-stu-id="a8d60-154">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider returns XACT_E_NOTSUPPORTED if the value is not FALSE.</span></span>|  
  
 <span data-ttu-id="a8d60-155">对于本地事务， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供程序实现**ITransaction：： Commit**参数，如下所示。</span><span class="sxs-lookup"><span data-stu-id="a8d60-155">For local transactions, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider implements **ITransaction::Commit** parameters as follows.</span></span>  
  
|<span data-ttu-id="a8d60-156">参数</span><span class="sxs-lookup"><span data-stu-id="a8d60-156">Parameter</span></span>|<span data-ttu-id="a8d60-157">说明</span><span class="sxs-lookup"><span data-stu-id="a8d60-157">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a8d60-158">\*\* fRetaining[in]</span><span class="sxs-lookup"><span data-stu-id="a8d60-158">*fRetaining*[in]</span></span>|<span data-ttu-id="a8d60-159">当该参数为 TRUE 时，将针对会话隐式开始新的事务。</span><span class="sxs-lookup"><span data-stu-id="a8d60-159">When TRUE, a new transaction is implicitly begun for the session.</span></span> <span data-ttu-id="a8d60-160">事务必须由使用者提交或中止。</span><span class="sxs-lookup"><span data-stu-id="a8d60-160">The transaction must be committed or terminated by the consumer.</span></span> <span data-ttu-id="a8d60-161">为 FALSE 时， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供程序将恢复为会话的自动提交模式。</span><span class="sxs-lookup"><span data-stu-id="a8d60-161">When FALSE, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider reverts to autocommit mode for the session.</span></span>|  
|<span data-ttu-id="a8d60-162">\*\* grfTC[in]</span><span class="sxs-lookup"><span data-stu-id="a8d60-162">*grfTC*[in]</span></span>|<span data-ttu-id="a8d60-163">Native Client OLE DB 提供程序不支持异步和阶段的一个返回 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="a8d60-163">Asynchronous and phase one returns are not supported by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider.</span></span> <span data-ttu-id="a8d60-164">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供程序为除 XACTTC_SYNC 之外的任何值返回 XACT_E_NOTSUPPORTED。</span><span class="sxs-lookup"><span data-stu-id="a8d60-164">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider returns XACT_E_NOTSUPPORTED for any value other than XACTTC_SYNC.</span></span>|  
|<span data-ttu-id="a8d60-165">\*\* grfRM[in]</span><span class="sxs-lookup"><span data-stu-id="a8d60-165">*grfRM*[in]</span></span>|<span data-ttu-id="a8d60-166">必须为 0。</span><span class="sxs-lookup"><span data-stu-id="a8d60-166">Must be 0.</span></span>|  
  
 <span data-ttu-id="a8d60-167">会话上的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供程序行集基于行集属性的值在本地提交或中止操作上保留 DBPROP_ABORTPRESERVE 和 DBPROP_COMMITPRESERVE。</span><span class="sxs-lookup"><span data-stu-id="a8d60-167">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider rowsets on the session are preserved on a local commit or abort operation based on the values of the rowset properties DBPROP_ABORTPRESERVE and DBPROP_COMMITPRESERVE.</span></span> <span data-ttu-id="a8d60-168">默认情况下，这些属性都是 VARIANT_FALSE 的，并且 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 会话上的所有 Native Client OLE DB 提供程序行集在中止或提交操作后将丢失。</span><span class="sxs-lookup"><span data-stu-id="a8d60-168">By default, these properties are both VARIANT_FALSE and all [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider rowsets on the session are lost following an abort or commit operation.</span></span>  
  
 <span data-ttu-id="a8d60-169">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供程序未实现**ITransactionObject**接口。</span><span class="sxs-lookup"><span data-stu-id="a8d60-169">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider does not implement the **ITransactionObject** interface.</span></span> <span data-ttu-id="a8d60-170">尝试检索接口上的引用的使用者将返回 E_NOINTERFACE。</span><span class="sxs-lookup"><span data-stu-id="a8d60-170">A consumer attempt to retrieve a reference on the interface returns E_NOINTERFACE.</span></span>  
  
 <span data-ttu-id="a8d60-171">此示例使用 ITransactionLocal\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a8d60-171">This example uses **ITransactionLocal**.</span></span>  
  
```  
// Interfaces used in the example.  
IDBCreateSession*   pIDBCreateSession   = NULL;  
ITransaction*       pITransaction       = NULL;  
IDBCreateCommand*   pIDBCreateCommand   = NULL;  
IRowset*            pIRowset            = NULL;  
  
HRESULT             hr;  
  
// Get the command creation and local transaction interfaces for the  
// session.  
if (FAILED(hr = pIDBCreateSession->CreateSession(NULL,  
     IID_IDBCreateCommand, (IUnknown**) &pIDBCreateCommand)))  
    {  
    // Process error from session creation. Release any references and  
    // return.  
    }  
  
if (FAILED(hr = pIDBCreateCommand->QueryInterface(IID_ITransactionLocal,  
    (void**) &pITransaction)))  
    {  
    // Process error. Release any references and return.  
    }  
  
// Start the local transaction.  
if (FAILED(hr = ((ITransactionLocal*) pITransaction)->StartTransaction(  
    ISOLATIONLEVEL_REPEATABLEREAD, 0, NULL, NULL)))  
    {  
    // Process error from StartTransaction. Release any references and  
    // return.  
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
    // Get error from update, then terminate.  
    pITransaction->Abort(NULL, FALSE, FALSE);  
    }  
else  
    {  
    if (FAILED(hr = pITransaction->Commit(FALSE, XACTTC_SYNC, 0)))  
        {  
        // Get error from failed commit.  
        }  
    }  
  
if (FAILED(hr))  
    {  
    // Update of data or commit failed. Release any references and  
    // return.  
    }  
  
// Release any references and continue.  
```  
  
## <a name="see-also"></a><span data-ttu-id="a8d60-172">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a8d60-172">See Also</span></span>  
 <span data-ttu-id="a8d60-173">[事务](transactions.md) </span><span class="sxs-lookup"><span data-stu-id="a8d60-173">[Transactions](transactions.md) </span></span>  
 [<span data-ttu-id="a8d60-174">使用快照隔离</span><span class="sxs-lookup"><span data-stu-id="a8d60-174">Working with Snapshot Isolation</span></span>](../native-client/features/working-with-snapshot-isolation.md)  
  
  
