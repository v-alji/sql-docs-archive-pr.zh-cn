---
title: ISSAsynchStatus::WaitForAsynchCompletion (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- ISSAsynchStatus::WaitForAsynchCompletion (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- WaitForAsynchCompletion method
ms.assetid: 9f65e9e7-eb93-47a1-bc42-acd4649fbd0e
author: rothja
ms.author: jroth
ms.openlocfilehash: f57211d1c62535828704dc971e345b412c284cf1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580233"
---
# <a name="issasynchstatuswaitforasynchcompletion-ole-db"></a><span data-ttu-id="25d0f-102">ISSAsynchStatus::WaitForAsynchCompletion (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="25d0f-102">ISSAsynchStatus::WaitForAsynchCompletion (OLE DB)</span></span>
  <span data-ttu-id="25d0f-103">一直等待，直到异步执行的操作完成或发生超时。</span><span class="sxs-lookup"><span data-stu-id="25d0f-103">Waits until the asynchronously executing operation is complete or until a time-out occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25d0f-104">语法</span><span class="sxs-lookup"><span data-stu-id="25d0f-104">Syntax</span></span>  
  
```  
  
HRESULT WaitForAsynchCompletion(   
  DWORD dwMillisecTimeOut);  
```  
  
## <a name="arguments"></a><span data-ttu-id="25d0f-105">参数</span><span class="sxs-lookup"><span data-stu-id="25d0f-105">Arguments</span></span>  
 <span data-ttu-id="25d0f-106">dwMillisecTimeOut[in]\*\*</span><span class="sxs-lookup"><span data-stu-id="25d0f-106">*dwMillisecTimeOut*[in]</span></span>  
 <span data-ttu-id="25d0f-107">超时值（毫秒）。</span><span class="sxs-lookup"><span data-stu-id="25d0f-107">Time-out in milliseconds.</span></span>  
  
## <a name="return-code-values"></a><span data-ttu-id="25d0f-108">返回代码值</span><span class="sxs-lookup"><span data-stu-id="25d0f-108">Return Code Values</span></span>  
 <span data-ttu-id="25d0f-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="25d0f-109">S_OK</span></span>  
 <span data-ttu-id="25d0f-110">方法成功。</span><span class="sxs-lookup"><span data-stu-id="25d0f-110">The method succeeded.</span></span>  
  
 <span data-ttu-id="25d0f-111">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="25d0f-111">E_UNEXPECTED</span></span>  
 <span data-ttu-id="25d0f-112">由于已调用**ITransaction：： Commit**或**ITransaction：： Abort**或在其初始化阶段取消了行集，因此行集处于未使用状态。</span><span class="sxs-lookup"><span data-stu-id="25d0f-112">A rowset is in an unused state because **ITransaction::Commit** or **ITransaction::Abort** has been called or the rowset was cancelled during its initialization phase.</span></span>  
  
 <span data-ttu-id="25d0f-113">DB_E_CANCELED</span><span class="sxs-lookup"><span data-stu-id="25d0f-113">DB_E_CANCELED</span></span>  
 <span data-ttu-id="25d0f-114">异步处理在行集填充或数据源对象初始化过程中被取消。</span><span class="sxs-lookup"><span data-stu-id="25d0f-114">Asynchronous processing was cancelled during rowset population or data source object initialization.</span></span>  
  
 <span data-ttu-id="25d0f-115">DB_S_ASYNCHRONOUS</span><span class="sxs-lookup"><span data-stu-id="25d0f-115">DB_S_ASYNCHRONOUS</span></span>  
 <span data-ttu-id="25d0f-116">此操作尚未完成，即使已达到指定的超时值。</span><span class="sxs-lookup"><span data-stu-id="25d0f-116">The operation has not yet completed even though specified time-out has been reached.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="25d0f-117">除了上面列出的返回代码值之外，ISSAsynchStatus::WaitForAsynchCompletion 方法还支持由核心 OLEDB ICommand::Execute 和 IDBInitialize::Initialize 方法返回的返回代码值\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="25d0f-117">In addition to the return code values listed above, the **ISSAsynchStatus::WaitForAsynchCompletion** method also supports the return code values returned by the core OLEDB **ICommand::Execute** and **IDBInitialize::Initialize** methods.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="25d0f-118">备注</span><span class="sxs-lookup"><span data-stu-id="25d0f-118">Remarks</span></span>  
 <span data-ttu-id="25d0f-119">在经过超时值（毫秒）或完成挂起操作之前，ISSAsynchStatus::WaitForAsynchCompletion 方法将不会返回值\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="25d0f-119">The **ISSAsynchStatus::WaitForAsynchCompletion** method will not return until the time-out value (in milliseconds) has passed or the pending operation is done.</span></span> <span data-ttu-id="25d0f-120">**Command**对象具有**CommandTimeout**属性，该属性控制查询在超时之前将运行的秒数。如果将**CommandTimeout**属性与**ISSAsynchStatus：： WaitForAsynchCompletion**方法结合使用，则将忽略该属性。</span><span class="sxs-lookup"><span data-stu-id="25d0f-120">The **Command** object has a **CommandTimeout** property that controls the number of seconds a query will run before timing out. The **CommandTimeout** property will be ignored if used in conjunction with **ISSAsynchStatus::WaitForAsynchCompletion** method.</span></span>  
  
 <span data-ttu-id="25d0f-121">对于异步操作，将忽略超时属性。</span><span class="sxs-lookup"><span data-stu-id="25d0f-121">The time-out property is ignored for asynchronous operations.</span></span> <span data-ttu-id="25d0f-122">ISSAsynchStatus::WaitForAsynchCompletion 的超时参数指定在将控制权返回到调用方之前将经过的最大时间量\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="25d0f-122">The time-out parameter of **ISSAsynchStatus::WaitForAsynchCompletion** specifies the maximum amount of time that will elapse before control is returned to the caller.</span></span> <span data-ttu-id="25d0f-123">如果此超时值已到期，将返回 DB_S_ASYNCHRONOUS。</span><span class="sxs-lookup"><span data-stu-id="25d0f-123">If this time-out expires, DB_S_ASYNCHRONOUS will be returned.</span></span> <span data-ttu-id="25d0f-124">超时从不会取消异步操作。</span><span class="sxs-lookup"><span data-stu-id="25d0f-124">Time-outs never cancel asynchronous operations.</span></span> <span data-ttu-id="25d0f-125">如果应用程序需要取消在超时期限内未完成的异步操作，则它必须等待发生超时，然后，如果返回 DB_S_ASYNCHRONOUS，则显式取消此操作。</span><span class="sxs-lookup"><span data-stu-id="25d0f-125">If the application needs to cancel an asynchronous operation that does not complete within a time-out period, it must wait for the time-out and then explicitly cancel the operation if DB_S_ASYNCHRONOUS is returned.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="25d0f-126">当使用 OLE DB 服务组件时，在应返回 DB_S_ASYNCHRONOUS 时可能返回 S_OK，因此，应用程序应调用 [ISSAsynchStatus::GetStatus](issasynchstatus-getstatus-ole-db.md) 以检查在返回 S_OK 或 DB_S_ASYNCHRONOUS 时操作是否已完成。</span><span class="sxs-lookup"><span data-stu-id="25d0f-126">When the OLE DB Service Components are used, S_OK may be returned when DB_S_ASYNCHRONOUS is expected, so applications should call [ISSAsynchStatus::GetStatus](issasynchstatus-getstatus-ole-db.md) to check for completion when S_OK or DB_S_ASYNCHRONOUS is returned.</span></span>  
  
 <span data-ttu-id="25d0f-127">如果 dwMillisecTimeOut 值设置为 INFINITE，则 ISSAsynchStatus::WaitForAsynchCompletion 方法将在该操作完成之前一直阻止其他操作\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="25d0f-127">If the *dwMillisecTimeOut* value is set to INFINITE, the **ISSAsynchStatus::WaitForAsynchCompletion** method blocks until the operation is done.</span></span> <span data-ttu-id="25d0f-128">如果 dwMillisecTimeOut 值设置为 0，则该方法将立即返回并提供挂起操作的状态\*\*。</span><span class="sxs-lookup"><span data-stu-id="25d0f-128">If the *dwMillisecTimeOut* value is set to 0, then the method will return immediately with the status of the pending operation.</span></span> <span data-ttu-id="25d0f-129">如果在完成此操作之前超时值已到期，则将返回 DB_S_ASYNCHRONOUS。</span><span class="sxs-lookup"><span data-stu-id="25d0f-129">If the time-out expires before the operation is complete DB_S_ASYNCHRONOUS will be returned.</span></span>  
  
 <span data-ttu-id="25d0f-130">如果操作在超时值到期之前完成，则返回的 HRESULT 将为由此操作返回的 HRESULT（如果此操作已以异步方式执行，则应已返回 HRESULT）。</span><span class="sxs-lookup"><span data-stu-id="25d0f-130">If the operation completes before the time-out expires, the returned HRESULT will be the HRESULT returned by the operation (the HRESULT that would have been returned had the operation been performed synchronously).</span></span>  
  
 <span data-ttu-id="25d0f-131">此外，SSPROP_ISSAsynchStatus 属性已添加到 DBPROPSET_SQLSERVERROWSET 属性集。</span><span class="sxs-lookup"><span data-stu-id="25d0f-131">In addition, the SSPROP_ISSAsynchStatus property has been added to the DBPROPSET_SQLSERVERROWSET property set.</span></span> <span data-ttu-id="25d0f-132">支持 [ISSAsynchStatus](issasynchstatus-ole-db.md) 接口的提供程序必须使用值 VARIANT_TRUE 实现此属性。</span><span class="sxs-lookup"><span data-stu-id="25d0f-132">Providers that support the [ISSAsynchStatus](issasynchstatus-ole-db.md) interface must implement this property with a value of VARIANT_TRUE.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25d0f-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="25d0f-133">See Also</span></span>  
 <span data-ttu-id="25d0f-134">[执行异步操作](../native-client/features/performing-asynchronous-operations.md) </span><span class="sxs-lookup"><span data-stu-id="25d0f-134">[Performing Asynchronous Operations](../native-client/features/performing-asynchronous-operations.md) </span></span>  
 [<span data-ttu-id="25d0f-135">ISSAsynchStatus &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="25d0f-135">ISSAsynchStatus &#40;OLE DB&#41;</span></span>](issasynchstatus-ole-db.md)  
  
  
