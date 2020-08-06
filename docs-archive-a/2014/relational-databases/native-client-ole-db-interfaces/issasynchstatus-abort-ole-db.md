---
title: ISSAsynchStatus::Abort (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- ISSAsynchStatus::Abort (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- Abort method
ms.assetid: 2a4bd312-839a-45a8-a299-fc8609be9a2a
author: rothja
ms.author: jroth
ms.openlocfilehash: 0fb352b6541240126dcd4c60521b93d57d6839f8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690599"
---
# <a name="issasynchstatusabort-ole-db"></a><span data-ttu-id="d408b-102">ISSAsynchStatus::Abort (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="d408b-102">ISSAsynchStatus::Abort (OLE DB)</span></span>
  <span data-ttu-id="d408b-103">取消异步执行的操作。</span><span class="sxs-lookup"><span data-stu-id="d408b-103">Cancels an asynchronously executing operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d408b-104">语法</span><span class="sxs-lookup"><span data-stu-id="d408b-104">Syntax</span></span>  
  
```  
  
HRESULT Abort(  
  HCHAPTER hChapter,  
  DBASYNCHOP eOperation);  
```  
  
## <a name="arguments"></a><span data-ttu-id="d408b-105">参数</span><span class="sxs-lookup"><span data-stu-id="d408b-105">Arguments</span></span>  
 <span data-ttu-id="d408b-106">hChapter[in]\*\*</span><span class="sxs-lookup"><span data-stu-id="d408b-106">*hChapter*[in]</span></span>  
 <span data-ttu-id="d408b-107">要中止其操作的章节的句柄。</span><span class="sxs-lookup"><span data-stu-id="d408b-107">The handle of the chapter for which to abort the operation.</span></span> <span data-ttu-id="d408b-108">如果被调用的对象不是行集对象或操作不适用于某一章节，则调用方必须将*hChapter*设置为 DB_NULL_HCHAPTER。</span><span class="sxs-lookup"><span data-stu-id="d408b-108">If the object being called is not a rowset object or the operation does not apply to a chapter, the caller must set *hChapter* to DB_NULL_HCHAPTER.</span></span>  
  
 <span data-ttu-id="d408b-109">eOperation[in]\*\*</span><span class="sxs-lookup"><span data-stu-id="d408b-109">*eOperation*[in]</span></span>  
 <span data-ttu-id="d408b-110">要中止的操作。</span><span class="sxs-lookup"><span data-stu-id="d408b-110">The operation to abort.</span></span> <span data-ttu-id="d408b-111">其值应为：</span><span class="sxs-lookup"><span data-stu-id="d408b-111">This should be the following value:</span></span>  
  
 <span data-ttu-id="d408b-112">DBASYNCHOP_OPEN - 要取消的请求应用于行集的异步打开或填充，或应用于数据源对象的异步初始化。</span><span class="sxs-lookup"><span data-stu-id="d408b-112">DBASYNCHOP_OPEN-The request to cancel applies to the asynchronous opening or population of a rowset or to the asynchronous initialization of a data source object.</span></span>  
  
## <a name="return-code-values"></a><span data-ttu-id="d408b-113">返回代码值</span><span class="sxs-lookup"><span data-stu-id="d408b-113">Return Code Values</span></span>  
 <span data-ttu-id="d408b-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="d408b-114">S_OK</span></span>  
 <span data-ttu-id="d408b-115">已处理取消异步操作的请求。</span><span class="sxs-lookup"><span data-stu-id="d408b-115">The request to cancel the asynchronous operation was processed.</span></span> <span data-ttu-id="d408b-116">这并不保证操作本身已取消。</span><span class="sxs-lookup"><span data-stu-id="d408b-116">This does not guarantee that the operation itself was canceled.</span></span> <span data-ttu-id="d408b-117">若要确定操作是否已取消，使用者应当调用 [ISSAsynchStatus::GetStatus](issasynchstatus-getstatus-ole-db.md)，并检查是否有 DB_E_CANCELED；但是，它可能不会正好在下一次调用中返回。</span><span class="sxs-lookup"><span data-stu-id="d408b-117">To determine whether the operation was canceled, the consumer should call [ISSAsynchStatus::GetStatus](issasynchstatus-getstatus-ole-db.md) and check for DB_E_CANCELED; however, it might not be returned in the very next call.</span></span>  
  
 <span data-ttu-id="d408b-118">DB_E_CANTCANCEL</span><span class="sxs-lookup"><span data-stu-id="d408b-118">DB_E_CANTCANCEL</span></span>  
 <span data-ttu-id="d408b-119">异步操作无法取消。</span><span class="sxs-lookup"><span data-stu-id="d408b-119">The asynchronous operation cannot be canceled.</span></span>  
  
 <span data-ttu-id="d408b-120">DB_E_CANCELED</span><span class="sxs-lookup"><span data-stu-id="d408b-120">DB_E_CANCELED</span></span>  
 <span data-ttu-id="d408b-121">中止异步操作的请求已在通知期间取消。</span><span class="sxs-lookup"><span data-stu-id="d408b-121">The request to abort the asynchronous operation was canceled during notifications.</span></span> <span data-ttu-id="d408b-122">操作仍然正在异步执行。</span><span class="sxs-lookup"><span data-stu-id="d408b-122">The operation is still being executed asynchronously.</span></span>  
  
 <span data-ttu-id="d408b-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d408b-123">E_FAIL</span></span>  
 <span data-ttu-id="d408b-124">发生了特定于访问接口的错误。</span><span class="sxs-lookup"><span data-stu-id="d408b-124">A provider-specific error occurred.</span></span>  
  
 <span data-ttu-id="d408b-125">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="d408b-125">E_INVALIDARG</span></span>  
 <span data-ttu-id="d408b-126">*HChapter*参数不是 DB_NULL_HCHAPTER 或*eOperation*不 DBASYNCH_OPEN。</span><span class="sxs-lookup"><span data-stu-id="d408b-126">The *hChapter* parameter is not DB_NULL_HCHAPTER or *eOperation* is not DBASYNCH_OPEN.</span></span>  
  
 <span data-ttu-id="d408b-127">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="d408b-127">E_UNEXPECTED</span></span>  
 <span data-ttu-id="d408b-128">对未在其上调用**IDBInitialize：： Initialize**的数据源对象调用了**ISSAsynchStatus：： Abort** ，或该对象尚未完成。</span><span class="sxs-lookup"><span data-stu-id="d408b-128">**ISSAsynchStatus::Abort** was called on a data source object on which **IDBInitialize::Initialize** has not been called, or has not completed.</span></span>  
  
 <span data-ttu-id="d408b-129">对在其上调用了**IDBInitialize：： Initialize**但随后在初始化之前取消的数据源对象调用了**ISSAsynchStatus：： Abort** ，或已超时。数据源对象仍未初始化。</span><span class="sxs-lookup"><span data-stu-id="d408b-129">**ISSAsynchStatus::Abort** was called on a data source object on which **IDBInitialize::Initialize** was called but subsequently canceled before initialization, or has timed out. The data source object is still uninitialized.</span></span>  
  
 <span data-ttu-id="d408b-130">在之前调用了**ITransaction：： Commit**或**ITransaction：： abort**的行集上调用了**ISSAsynchStatus：： abort** ，并且行集未保留在提交或中止后并且处于僵停状态。</span><span class="sxs-lookup"><span data-stu-id="d408b-130">**ISSAsynchStatus::Abort** was called on a rowset on which **ITransaction::Commit** or **ITransaction::Abort** was previously called, and the rowset did not survive the commit or abort and is in a zombie state.</span></span>  
  
 <span data-ttu-id="d408b-131">已对在初始化阶段异步取消的行集调用 ISSAsynchStatus::Abort\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d408b-131">**ISSAsynchStatus::Abort** was called on a rowset that was asynchronously canceled in its initialization phase.</span></span> <span data-ttu-id="d408b-132">该行集处于僵停状态。</span><span class="sxs-lookup"><span data-stu-id="d408b-132">The rowset is in a zombie state.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d408b-133">备注</span><span class="sxs-lookup"><span data-stu-id="d408b-133">Remarks</span></span>  
 <span data-ttu-id="d408b-134">中止行集或数据源对象的初始化可能使行集或数据源对象最后处于僵停状态，以至于除了 IUnknown 方法以外的所有方法都返回 E_UNEXPECTED\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d408b-134">Aborting the initialization of a rowset or data source object might leave the rowset or data source object in a zombie state, such that all methods other than **IUnknown** methods return E_UNEXPECTED.</span></span> <span data-ttu-id="d408b-135">发生这种情况时，使用者的唯一可能操作是释放行集或数据源对象。</span><span class="sxs-lookup"><span data-stu-id="d408b-135">When this happens, the only possible action for the consumer is to release the rowset or data source object.</span></span>  
  
 <span data-ttu-id="d408b-136">如果调用 ISSAsynchStatus::Abort 并为 eOperation 传递除了 DBASYNCHOP_OPEN 以外的值，将返回 S_OK\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d408b-136">Calling **ISSAsynchStatus::Abort** and passing a value for *eOperation* other than DBASYNCHOP_OPEN returns S_OK.</span></span> <span data-ttu-id="d408b-137">这并不意味着操作已完成或取消。</span><span class="sxs-lookup"><span data-stu-id="d408b-137">This does not imply that the operation completed or was canceled.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d408b-138">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d408b-138">See Also</span></span>  
 [<span data-ttu-id="d408b-139">执行异步操作</span><span class="sxs-lookup"><span data-stu-id="d408b-139">Performing Asynchronous Operations</span></span>](../native-client/features/performing-asynchronous-operations.md)  
  
  
