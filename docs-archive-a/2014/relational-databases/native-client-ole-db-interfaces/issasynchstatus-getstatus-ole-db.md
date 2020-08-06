---
title: ISSAsynchStatus::GetStatus (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- ISSAsynchStatus::GetStatus (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- GetStatus method
ms.assetid: 354b6ee4-b5a1-48f6-9403-da3bdc911067
author: rothja
ms.author: jroth
ms.openlocfilehash: 14c20ae5d9a5cd31139db74aeedabb2d017f6ce6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578864"
---
# <a name="issasynchstatusgetstatus-ole-db"></a><span data-ttu-id="41882-102">ISSAsynchStatus::GetStatus (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="41882-102">ISSAsynchStatus::GetStatus (OLE DB)</span></span>
  <span data-ttu-id="41882-103">返回异步执行操作的状态。</span><span class="sxs-lookup"><span data-stu-id="41882-103">Returns the status of an asynchronously executing operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41882-104">语法</span><span class="sxs-lookup"><span data-stu-id="41882-104">Syntax</span></span>  
  
```  
  
HRESULT GetStatus(  
  HCHAPTER hChapter,  
  DBASYNCHOP eOperation,  
  DBCOUNTITEM *pulProgress,  
  DBCOUNTITEM *pulProgressMax,  
  DBASYNCHPHASE *peAsynchPhase,  
  LPOLESTR *ppwszStatusText);  
```  
  
## <a name="arguments"></a><span data-ttu-id="41882-105">参数</span><span class="sxs-lookup"><span data-stu-id="41882-105">Arguments</span></span>  
 <span data-ttu-id="41882-106">hChapter[in]\*\*</span><span class="sxs-lookup"><span data-stu-id="41882-106">*hChapter*[in]</span></span>  
 <span data-ttu-id="41882-107">章节句柄。</span><span class="sxs-lookup"><span data-stu-id="41882-107">The chapter handle.</span></span> <span data-ttu-id="41882-108">如果轮询的对象不是行集对象或操作不适用于某一章节，则应将此参数设置为 DB_NULL_HCHAPTER，访问接口将忽略此参数。</span><span class="sxs-lookup"><span data-stu-id="41882-108">If the object being polled is not a rowset object or the operation does not apply to a chapter, this should be set to DB_NULL_HCHAPTER, which is ignored by the provider.</span></span>  
  
 <span data-ttu-id="41882-109">eOperation[in]\*\*</span><span class="sxs-lookup"><span data-stu-id="41882-109">*eOperation*[in]</span></span>  
 <span data-ttu-id="41882-110">请求其异步状态的操作。</span><span class="sxs-lookup"><span data-stu-id="41882-110">The operation for which the asynchronous status is being requested.</span></span> <span data-ttu-id="41882-111">其值应为：</span><span class="sxs-lookup"><span data-stu-id="41882-111">This should be the following value:</span></span>  
  
 <span data-ttu-id="41882-112">DBASYNCHOP_OPEN - 使用者请求获取有关行集的异步打开或填充的信息，或有关数据源对象的异步初始化的信息。</span><span class="sxs-lookup"><span data-stu-id="41882-112">DBASYNCHOP_OPEN-The consumer requests information about the asynchronous opening or population of a rowset or about the asynchronous initialization of a data source object.</span></span> <span data-ttu-id="41882-113">如果访问接口是支持直接 URL 绑定且与 OLE DB 2.5 兼容的访问接口，使用者则请求有关异步初始化或填充数据源、行集、行或流对象的信息。</span><span class="sxs-lookup"><span data-stu-id="41882-113">If the provider is an OLE DB 2.5-compliant provider that supports direct URL binding, the consumer requests information about the asynchronous initialization or population of a data source, rowset, row, or stream object.</span></span>  
  
 <span data-ttu-id="41882-114">pulProgress[out]\*\*</span><span class="sxs-lookup"><span data-stu-id="41882-114">*pulProgress*[out]</span></span>  
 <span data-ttu-id="41882-115">指向内存的指针，将在此内存中返回与 pulProgressMax 参数指示的预期最大值相关的异步操作的当前进度\*\*。</span><span class="sxs-lookup"><span data-stu-id="41882-115">A pointer to memory in which to return the current progress of the asynchronous operation relative to the expected maximum indicated in the *pulProgressMax* parameter.</span></span> <span data-ttu-id="41882-116">有关 pulProgress 的含义的详细信息，请参阅对 peAsynchPhase 的说明\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="41882-116">For more information about the meaning of *pulProgress*, see the description of *peAsynchPhase*.</span></span>  
  
 <span data-ttu-id="41882-117">如果 pulProgress 为空指针，则不返回进度\*\*。</span><span class="sxs-lookup"><span data-stu-id="41882-117">If *pulProgress* is a null pointer, no progress is returned.</span></span>  
  
 <span data-ttu-id="41882-118">pulProgressMax[out]\*\*</span><span class="sxs-lookup"><span data-stu-id="41882-118">*pulProgressMax*[out]</span></span>  
 <span data-ttu-id="41882-119">指向内存的指针，将在此内存中返回 pulProgress 参数的预期最大值\*\*。</span><span class="sxs-lookup"><span data-stu-id="41882-119">A pointer to memory in which to return the expected maximum value of the *pulProgress* parameter.</span></span> <span data-ttu-id="41882-120">此值可以随此方法的每次调用而更改。</span><span class="sxs-lookup"><span data-stu-id="41882-120">This value may change across calls to this method.</span></span> <span data-ttu-id="41882-121">有关 pulProgressMax 的含义的详细信息，请参阅对 peAsynchPhase 的说明\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="41882-121">For more information about the meaning of *pulProgressMax*, see the description of *peAsynchPhase*.</span></span>  
  
 <span data-ttu-id="41882-122">如果 pulProgressMax 为空指针，则不返回预期的最大值\*\*。</span><span class="sxs-lookup"><span data-stu-id="41882-122">If *pulProgressMax* is a null pointer, no expected maximum value is returned.</span></span>  
  
 <span data-ttu-id="41882-123">peAsynchPhase[out]\*\*</span><span class="sxs-lookup"><span data-stu-id="41882-123">*peAsynchPhase*[out]</span></span>  
 <span data-ttu-id="41882-124">指向内存的指针，将在此内存中返回有关异步操作的进度的其他信息。</span><span class="sxs-lookup"><span data-stu-id="41882-124">A pointer to memory in which to return additional information regarding the progress of the asynchronous operation.</span></span> <span data-ttu-id="41882-125">有效值包括：</span><span class="sxs-lookup"><span data-stu-id="41882-125">Valid values include:</span></span>  
  
 <span data-ttu-id="41882-126">DBASYNCHPHASE_INITIALIZATION - 对象处于初始化阶段。</span><span class="sxs-lookup"><span data-stu-id="41882-126">DBASYNCHPHASE_INITIALIZATION-The object is in an initialization phase.</span></span> <span data-ttu-id="41882-127">参数 pulProgress 和 pulProgressMax 指示估计的完成比率\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="41882-127">The arguments *pulProgress* and *pulProgressMax* indicate an estimated ratio of completion.</span></span> <span data-ttu-id="41882-128">对象尚未完全具体化。</span><span class="sxs-lookup"><span data-stu-id="41882-128">The object is not yet fully materialized.</span></span> <span data-ttu-id="41882-129">尝试调用任何其他接口可能失败，并且可能无法对该对象使用整套接口。</span><span class="sxs-lookup"><span data-stu-id="41882-129">Attempting to call any other interfaces may fail, and the full set of interfaces may not be available on the object.</span></span> <span data-ttu-id="41882-130">如果异步操作是因调用更新、删除或插入行的命令的 ICommand::Execute 而引起的，并且如果 cParamSets 大于 1，pulProgress 和 pulProgressMax 可以指示一个参数集或所有参数集的进度\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="41882-130">If the asynchronous operation was a result of calling **ICommand::Execute** for a command that updates, deletes, or inserts rows and if *cParamSets* is greater than 1, *pulProgress* and *pulProgressMax* may indicate the progress for a single set of parameters or for the full array of parameter sets.</span></span>  
  
 <span data-ttu-id="41882-131">DBASYNCHPHASE_POPULATION - 对象处于填充阶段。</span><span class="sxs-lookup"><span data-stu-id="41882-131">DBASYNCHPHASE_POPULATION-The object is in a population phase.</span></span> <span data-ttu-id="41882-132">尽管已完全初始化行集，并且可针对该对象使用整套接口，但是可能还有其他行尚未填充到行集中。</span><span class="sxs-lookup"><span data-stu-id="41882-132">Although the rowset is fully initialized and the full range of interfaces is available on the object, there may be additional rows not yet populated into the rowset.</span></span> <span data-ttu-id="41882-133">虽然 pulProgress 和 pulProgressMax 可以基于填充的行数，但它们通常基于填充行集所需的时间和工作\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="41882-133">While *pulProgress* and *pulProgressMax* can be based on the number of rows populated, they are generally based on the time or effort required to populate the rowset.</span></span> <span data-ttu-id="41882-134">因此，调用方应将此信息用作对此过程所需时间的粗略估计，而不是最终的行计数。</span><span class="sxs-lookup"><span data-stu-id="41882-134">A caller should therefore use this information as a rough estimate of how long the process might take, not the eventual row count.</span></span> <span data-ttu-id="41882-135">此阶段仅在填充行集期间返回；它永远不会在数据源对象初始化期间返回，也不会因执行更新、删除或插入行的命令而返回。</span><span class="sxs-lookup"><span data-stu-id="41882-135">This phase is returned only during population of a rowset; it is never returned in the initialization of a data source object or by the execution of a command that updates, deletes, or inserts rows.</span></span>  
  
 <span data-ttu-id="41882-136">DBASYNCHPHASE_COMPLETE - 已完成对象的所有异步处理。</span><span class="sxs-lookup"><span data-stu-id="41882-136">DBASYNCHPHASE_COMPLETE-All asynchronous processing of the object has completed.</span></span> <span data-ttu-id="41882-137">**ISSAsynchStatus：： GetStatus**返回一个 HRESULT，指示操作的结果。</span><span class="sxs-lookup"><span data-stu-id="41882-137">**ISSAsynchStatus::GetStatus** returns an HRESULT indicating the outcome of the operation.</span></span> <span data-ttu-id="41882-138">通常，如果已同步调用操作，则将返回 HRESULT。</span><span class="sxs-lookup"><span data-stu-id="41882-138">Typically, this will be the HRESULT that would have been returned had the operation been called synchronously.</span></span> <span data-ttu-id="41882-139">如果异步操作是因调用更新、删除或插入行的命令的 ICommand::Execute 而引起的，pulProgress 和 pulProgressMax 则等于该命令所影响的总行数\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="41882-139">If the asynchronous operation was a result of calling **ICommand::Execute** for a command that updates, deletes, or inserts rows, *pulProgress* and *pulProgressMax* are equal to the total number of rows affected by the command.</span></span> <span data-ttu-id="41882-140">如果 cParamSets 大于 1，则等于执行过程中指定的所有参数集所影响的总行数\*\*。</span><span class="sxs-lookup"><span data-stu-id="41882-140">If *cParamSets* is greater than 1, this is the total number of rows affected by all of the sets of parameters specified in the execution.</span></span> <span data-ttu-id="41882-141">如果 peAsynchPhase 为空指针，则不返回状态代码\*\*。</span><span class="sxs-lookup"><span data-stu-id="41882-141">If *peAsynchPhase* is a null pointer, no status code is returned.</span></span>  
  
 <span data-ttu-id="41882-142">DBASYNCHPHASE_CANCELED - 已中止对象的异步处理。</span><span class="sxs-lookup"><span data-stu-id="41882-142">DBASYNCHPHASE_CANCELED-Asynchronous processing of the object was aborted.</span></span> <span data-ttu-id="41882-143">**ISSAsynchStatus：： GetStatus**返回 DB_E_CANCELED。</span><span class="sxs-lookup"><span data-stu-id="41882-143">**ISSAsynchStatus::GetStatus** returns DB_E_CANCELED.</span></span> <span data-ttu-id="41882-144">如果异步操作是因调用更新、删除或插入行的命令的 ICommand::Execute 而引起的，pulProgress 则等于取消之前该命令所影响的所有参数集的总行数\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="41882-144">If the asynchronous operation was a result of calling **ICommand::Execute** for a command that updates, deletes, or inserts rows, *pulProgress* is equal to the total number of rows, for all parameter sets, affected by the command prior to cancellation.</span></span>  
  
 <span data-ttu-id="41882-145">ppwszStatusText[in/out]\*\*</span><span class="sxs-lookup"><span data-stu-id="41882-145">*ppwszStatusText*[in/out]</span></span>  
 <span data-ttu-id="41882-146">指向包含有关操作的其他信息的内存的指针。</span><span class="sxs-lookup"><span data-stu-id="41882-146">A pointer to memory containing additional information about the operation.</span></span> <span data-ttu-id="41882-147">提供程序可以使用此值来区分不同的操作元素（例如，要访问的不同资源）。</span><span class="sxs-lookup"><span data-stu-id="41882-147">A provider may use this value to distinguish between different elements of an operation-for example, different resources being accessed.</span></span> <span data-ttu-id="41882-148">该字符串的本地化形式基于数据源对象的 DBPROP_INIT_LCID 属性。</span><span class="sxs-lookup"><span data-stu-id="41882-148">This string is localized according to the DBPROP_INIT_LCID property on the data source object.</span></span>  
  
 <span data-ttu-id="41882-149">如果 ppwszStatusText 在输入时为非 Null，提供程序则返回与 ppwszStatusText 标识的特定元素相关联的状态\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="41882-149">If *ppwszStatusText* is non-null on input, the provider returns status associated with the particular element identified by *ppwszStatusText*.</span></span> <span data-ttu-id="41882-150">如果 ppwszStatusText 未指示 eOperation 的元素，提供程序则返回 S_OK，并将 pulProgress 和 pulProgressMax 设置为相同的值\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="41882-150">If *ppwszStatusText* does not indicate an element of *eOperation*, the provider returns S_OK with *pulProgress* and *pulProgressMax* set to the same value.</span></span> <span data-ttu-id="41882-151">如果提供程序不能基于文本标识符区分各元素，则会将 ppwszStatusText 设置为 NULL，并返回有关整个操作的信息；否则，如果 ppwszStatusText 在输入时为非 Null，提供程序将使 ppwszStatusText 保持不变\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="41882-151">If the provider does not distinguish between elements based on a textual identifier, it sets *ppwszStatusText* to NULL and returns information about the operation as a whole; otherwise, if *ppwszStatusText* is non-null on input, the provider leaves *ppwszStatusText* untouched.</span></span>  
  
 <span data-ttu-id="41882-152">如果*ppwszStatusText*在输入时为 null，则提供程序将*ppwszStatusText*设置为一个值，指示有关操作的详细信息; 如果没有此类信息，则为 null; 如果**ISSAsynchStatus：： GetStatus**返回错误，则为 null。</span><span class="sxs-lookup"><span data-stu-id="41882-152">If *ppwszStatusText* is null on input, the provider sets *ppwszStatusText* to a value indicating more information about the operation, or to NULL if no such information is available or if **ISSAsynchStatus::GetStatus** returns an error.</span></span> <span data-ttu-id="41882-153">如果 ppwszStatusText 在输入时为 Null，提供程序将为状态字符串分配内存，并返回此内存的地址\*\*。</span><span class="sxs-lookup"><span data-stu-id="41882-153">When *ppwszStatusText* is null on input, the provider allocates memory for the status string and returns the address to this memory.</span></span> <span data-ttu-id="41882-154">如果不再需要此字符串，使用者可以使用 IMalloc::Free 释放此内存\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="41882-154">The consumer releases this memory with **IMalloc::Free** when it no longer needs the string.</span></span>  
  
 <span data-ttu-id="41882-155">如果 ppwszStatusText 在输入时为 NULL，则不会返回状态字符串，提供程序将返回有关操作的任一元素的信息或有关操作的总体信息\*\*。</span><span class="sxs-lookup"><span data-stu-id="41882-155">If *ppwszStatusText* is NULL on input, no status string is returned and the provider returns information about any element of the operation or about the operation in general.</span></span>  
  
## <a name="return-code-values"></a><span data-ttu-id="41882-156">返回代码值</span><span class="sxs-lookup"><span data-stu-id="41882-156">Return Code Values</span></span>  
 <span data-ttu-id="41882-157">S_OK</span><span class="sxs-lookup"><span data-stu-id="41882-157">S_OK</span></span>  
 <span data-ttu-id="41882-158">该方法已成功返回。</span><span class="sxs-lookup"><span data-stu-id="41882-158">The method returned successfully.</span></span>  
  
-   <span data-ttu-id="41882-159">如果 peAsynchPhase 等于 DBASYNCHPHASE_INITIALIZATION，则尚未完全初始化对象；尝试调用任何其他接口可能失败，并且可能无法对该对象使用整套接口\*\*。</span><span class="sxs-lookup"><span data-stu-id="41882-159">If *peAsynchPhase* is equal to DBASYNCHPHASE_INITIALIZATION, the object is not yet fully initialized; attempting to call any other interfaces might fail, and the full set of interfaces might not be available on the object.</span></span>  
  
-   <span data-ttu-id="41882-160">如果 peAsynchPhase 等于 DBASYNCHPHASE_POPULATION，则已完全初始化行集，并且可针对该对象使用整套接口；但是可能还有其他行尚未填充到行集中\*\*。</span><span class="sxs-lookup"><span data-stu-id="41882-160">If *peAsynchPhase* is equal to DBASYNCHPHASE_POPULATION, the rowset is fully initialized and the full range of interfaces is available on the object; however, there might be additional rows not yet populated into the rowset.</span></span>  
  
-   <span data-ttu-id="41882-161">如果 peAsynchPhase 等于 DBASYNCHPHASE_COMPLETE，则已完成对象的所有异步处理\*\*。</span><span class="sxs-lookup"><span data-stu-id="41882-161">If *peAsynchPhase* is equal to DBASYNCHPHASE_COMPLETE, all asynchronous processing of the object has completed.</span></span> <span data-ttu-id="41882-162">已完全初始化并填充该对象。</span><span class="sxs-lookup"><span data-stu-id="41882-162">The object is fully initialized and populated.</span></span>  
  
 <span data-ttu-id="41882-163">DB_E_CANCELED</span><span class="sxs-lookup"><span data-stu-id="41882-163">DB_E_CANCELED</span></span>  
 <span data-ttu-id="41882-164">异步处理在行集填充过程中取消。</span><span class="sxs-lookup"><span data-stu-id="41882-164">Asynchronous processing was canceled during rowset population.</span></span> <span data-ttu-id="41882-165">填充停止，但是对于已填充的行，该行集仍保持有效。</span><span class="sxs-lookup"><span data-stu-id="41882-165">Population stops, but the rowset remains valid for the rows already populated.</span></span>  
  
 <span data-ttu-id="41882-166">异步处理在数据源对象的初始化过程中取消。</span><span class="sxs-lookup"><span data-stu-id="41882-166">Asynchronous processing was canceled during data source object initialization.</span></span> <span data-ttu-id="41882-167">数据源对象处于未初始化状态。</span><span class="sxs-lookup"><span data-stu-id="41882-167">The data source object is in an uninitialized state.</span></span>  
  
 <span data-ttu-id="41882-168">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="41882-168">E_INVALIDARG</span></span>  
 <span data-ttu-id="41882-169">hChapter\*\* 参数不正确。</span><span class="sxs-lookup"><span data-stu-id="41882-169">The *hChapter* parameter is incorrect.</span></span>  
  
 <span data-ttu-id="41882-170">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="41882-170">E_UNEXPECTED</span></span>  
 <span data-ttu-id="41882-171">已对数据源对象调用**ISSAsynchStatus：： GetStatus** ，但未对数据源对象调用**IDBInitialize：： Initialize** 。</span><span class="sxs-lookup"><span data-stu-id="41882-171">**ISSAsynchStatus::GetStatus** was called on a data source object, and **IDBInitialize::Initialize** has not been called on the data source object.</span></span>  
  
 <span data-ttu-id="41882-172">在行集上调用了**ISSAsynchStatus：： GetStatus** ， **ITransaction：： Commit**或**ITransaction：： Abort**调用了，并且该对象处于僵停状态。</span><span class="sxs-lookup"><span data-stu-id="41882-172">**ISSAsynchStatus::GetStatus** was called on a rowset, **ITransaction::Commit** or **ITransaction::Abort** was called, and the object is in a zombie state.</span></span>  
  
 <span data-ttu-id="41882-173">在异步取消的行集的初始化阶段中调用了**ISSAsynchStatus：： GetStatus** 。</span><span class="sxs-lookup"><span data-stu-id="41882-173">**ISSAsynchStatus::GetStatus** was called on a rowset that was asynchronously canceled in its initialization phase.</span></span> <span data-ttu-id="41882-174">该行集处于僵停状态。</span><span class="sxs-lookup"><span data-stu-id="41882-174">The rowset is in a zombie state.</span></span>  
  
 <span data-ttu-id="41882-175">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="41882-175">E_FAIL</span></span>  
 <span data-ttu-id="41882-176">发生了特定于访问接口的错误。</span><span class="sxs-lookup"><span data-stu-id="41882-176">A provider-specific error occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="41882-177">备注</span><span class="sxs-lookup"><span data-stu-id="41882-177">Remarks</span></span>  
 <span data-ttu-id="41882-178">ISSAsynchStatus::GetStatus 方法的行为与 IDBAsynchStatus::GetStatus 方法完全类似，不同之处在于如果中止对数据源对象的初始化，前者将返回 E_UNEXPECTED，而不是 DB_E_CANCELED（但是 [ISSAsynchStatus::WaitForAsynchCompletion](issasynchstatus-waitforasynchcompletion-ole-db.md) 将返回 DB_E_CANCELED）\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="41882-178">The **ISSAsynchStatus::GetStatus** method behaves exactly as the **IDBAsynchStatus::GetStatus** method except that if initialization of a data source object is aborted, E_UNEXPECTED is returned rather than DB_E_CANCELED (although [ISSAsynchStatus::WaitForAsynchCompletion](issasynchstatus-waitforasynchcompletion-ole-db.md) will return DB_E_CANCELED).</span></span> <span data-ttu-id="41882-179">这是因为在中止后，数据源对象不会照常处于僵停状态，以便进一步尝试初始化操作。</span><span class="sxs-lookup"><span data-stu-id="41882-179">This is because the data source object is not left in the usual zombie state following an abort, in order that further initialization operations may be attempted.</span></span>  
  
 <span data-ttu-id="41882-180">如果异步初始化或填充行集，则必须支持此方法。</span><span class="sxs-lookup"><span data-stu-id="41882-180">If the rowset is initialized or populated asynchronously, it must support this method.</span></span>  
  
 <span data-ttu-id="41882-181">除列出的返回值以外，ISSAsynchStatus::GetStatus 还可以返回应由启动异步操作的方法返回的任何 HRESULT，以指示操作成功或失败\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="41882-181">In addition to the return values listed, **ISSAsynchStatus::GetStatus** can return any HRESULT that would have been returned by the method that initiated the asynchronous operation, indicating the success or failure of the operation.</span></span>  
  
 <span data-ttu-id="41882-182">某些异步操作可能无法返回除“完成”和“尚未完成”以外的任何状态。</span><span class="sxs-lookup"><span data-stu-id="41882-182">Some asynchronous operations might not be able to return any states other than "finished" and "not finished".</span></span> <span data-ttu-id="41882-183">这些异步操作应将 pulProgressMax 值设置为 1，指示其估计的粒度（全部粒度或没有任何粒度），因此返回的值将为 0/1 或 1/1\*\*。</span><span class="sxs-lookup"><span data-stu-id="41882-183">They should set *pulProgressMax* to a value of 1, indicating the all-or-nothing granularity of their estimate, so their answers would be either 0/1 or 1/1.</span></span>  
  
 <span data-ttu-id="41882-184">提供程序可以在后续调用中更改 pulProgressMax，甚至返回比先前更小的比率，条件是该比率反映对任务完成程度的改善估计\*\*。</span><span class="sxs-lookup"><span data-stu-id="41882-184">A provider may change *pulProgressMax* in successive calls and even return a smaller ratio than previously, if this reflects an improving estimate of the degree of completion of the task.</span></span>  
  
 <span data-ttu-id="41882-185">访问接口不必保证任何进一步的准确性，但是对于可以对完成情况进行合理估计的情况，建议执行此工作。</span><span class="sxs-lookup"><span data-stu-id="41882-185">The provider is not obliged to guarantee any further accuracy but is encouraged to do so in cases where reasonable estimates of completion are possible.</span></span> <span data-ttu-id="41882-186">这一工作将改进用户界面的质量，因为此函数的主要用途是向用户提供进度反馈。</span><span class="sxs-lookup"><span data-stu-id="41882-186">Such efforts will improve user-interface quality because the main use of this function is likely to be to give progress feedback to the user.</span></span> <span data-ttu-id="41882-187">由于改善了长期运行的不可见任务的反馈质量，用户的满意度也随之提高。</span><span class="sxs-lookup"><span data-stu-id="41882-187">User satisfaction increases with the quality of feedback on an invisible, long-running task.</span></span>  
  
 <span data-ttu-id="41882-188">对已初始化的数据源对象或已填充的行集调用 ISSAsynchStatus::GetStatus，或者传递除 DBASYNCHOP_OPEN 以外的 eOperation 值将返回 S_OK，并将 pulProgress 和 pulProgressMax 设置为相同的值\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="41882-188">Calling **ISSAsynchStatus::GetStatus** on an initialized data source object or a populated rowset, or passing a value for *eOperation* other than DBASYNCHOP_OPEN, returns S_OK with *pulProgress* and *pulProgressMax* set to the same value.</span></span> <span data-ttu-id="41882-189">如果对通过执行用于更新、删除或插入行的命令而创建的对象调用**ISSAsynchStatus：： GetStatus** ，则*pulProgress*和*pulProgressMax*都指示受该命令影响的总行数。</span><span class="sxs-lookup"><span data-stu-id="41882-189">If **ISSAsynchStatus::GetStatus** is called on an object created from the execution of a command that updates, deletes, or inserts rows, both *pulProgress* and *pulProgressMax* indicate the total number of rows affected by the command.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41882-190">另请参阅</span><span class="sxs-lookup"><span data-stu-id="41882-190">See Also</span></span>  
 <span data-ttu-id="41882-191">[执行异步操作](../native-client/features/performing-asynchronous-operations.md) </span><span class="sxs-lookup"><span data-stu-id="41882-191">[Performing Asynchronous Operations](../native-client/features/performing-asynchronous-operations.md) </span></span>  
 [<span data-ttu-id="41882-192">ISSAsynchStatus &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="41882-192">ISSAsynchStatus &#40;OLE DB&#41;</span></span>](issasynchstatus-ole-db.md)  
  
  
