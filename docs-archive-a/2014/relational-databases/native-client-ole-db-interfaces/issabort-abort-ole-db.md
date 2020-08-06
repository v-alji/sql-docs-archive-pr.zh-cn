---
title: ISSAbort::Abort (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- ISSAbort::Abort (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- Abort method
ms.assetid: a5bca169-694b-4895-84ac-e8fba491e479
author: rothja
ms.author: jroth
ms.openlocfilehash: 3daad53087c876af8dc46bccc9c4bf7952976067
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690601"
---
# <a name="issabortabort-ole-db"></a><span data-ttu-id="27e62-102">ISSAbort::Abort (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="27e62-102">ISSAbort::Abort (OLE DB)</span></span>
  <span data-ttu-id="27e62-103">取消当前行集以及与当前命令关联的任何批处理命令。</span><span class="sxs-lookup"><span data-stu-id="27e62-103">Cancels the current rowset plus any batched commands associated with the current command.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27e62-104">语法</span><span class="sxs-lookup"><span data-stu-id="27e62-104">Syntax</span></span>  
  
```  
  
HRESULT Abort(void);  
```  
  
## <a name="remarks"></a><span data-ttu-id="27e62-105">备注</span><span class="sxs-lookup"><span data-stu-id="27e62-105">Remarks</span></span>  
 <span data-ttu-id="27e62-106">如果要中止的命令位于存储过程中，则将终止存储过程（以及已调用该过程的任何过程）以及包含此存储过程调用的命令批处理的执行。</span><span class="sxs-lookup"><span data-stu-id="27e62-106">If the command being aborted is in a stored procedure, execution of the stored procedure (and any procedures which had called that procedure) will be terminated as well as the command batch which contains the stored procedure call.</span></span> <span data-ttu-id="27e62-107">如果服务器正在将结果集传输到客户端，则将停止此过程。</span><span class="sxs-lookup"><span data-stu-id="27e62-107">If the server is in the process of transferring a result set to the client, this will be stopped.</span></span> <span data-ttu-id="27e62-108">如果客户端不希望使用结果集，则在释放行集之前调用 ISSAbort::Abort 将加快行集释放，但是，如果存在打开的事务且 XACT_ABORT 为 ON，则当调用 ISSAbort::Abort 时，将回滚此事务\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="27e62-108">If the client does not want to consume a result set, calling **ISSAbort::Abort** before releasing the rowset will speed up the rowset release, but if there is an open transaction and XACT_ABORT is ON, the transaction will be rolled back when **ISSAbort::Abort** is called</span></span>  
  
 <span data-ttu-id="27e62-109">**ISSAbort：： Abort**返回 S_OK 后，关联的**IMultipleResults**接口将进入不可用状态，并将 DB_E_CANCELED 返回到所有方法调用 (除了**IUnknown**接口定义的方法) 直到它被释放。</span><span class="sxs-lookup"><span data-stu-id="27e62-109">After **ISSAbort::Abort** returns S_OK, the associated **IMultipleResults** interface enters a unusable state and returns DB_E_CANCELED to all method calls (except for methods defined by the **IUnknown** interface) until it is released.</span></span> <span data-ttu-id="27e62-110">如果在调用 Abort 之前已从 IMultipleResults 获取了 IRowset，则它也会进入不可用状态，并对所有方法调用返回 DB_E_CANCELED（由 IUnknown 接口和 IRowset::ReleaseRows 定义的方法除外），直到在成功调用 ISSAbort::Abort 之后释放它为止\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="27e62-110">If an **IRowset** had been obtained from **IMultipleResults** prior to a call to **Abort**, it also enters an unusable state and returns DB_E_CANCELED to all method calls (except for methods defined by the **IUnknown** interface and **IRowset::ReleaseRows**) until it is released after a successful call to **ISSAbort::Abort**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="27e62-111">从 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 开始，如果服务器 XACT_ABORT 状态为 ON，则当连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 时，ISSAbort::Abort 的执行将终止并回滚当前所有的隐式或显式事务\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="27e62-111">Beginning with [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], if the server XACT_ABORT state is ON, executing **ISSAbort::Abort** will terminate and roll back any current implicit or explicit transaction when connected to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="27e62-112">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的较早版本不中止当前事务。</span><span class="sxs-lookup"><span data-stu-id="27e62-112">Earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will not abort the current transaction.</span></span>  
  
## <a name="arguments"></a><span data-ttu-id="27e62-113">参数</span><span class="sxs-lookup"><span data-stu-id="27e62-113">Arguments</span></span>  
 <span data-ttu-id="27e62-114">无。</span><span class="sxs-lookup"><span data-stu-id="27e62-114">None.</span></span>  
  
## <a name="return-code-values"></a><span data-ttu-id="27e62-115">返回代码值</span><span class="sxs-lookup"><span data-stu-id="27e62-115">Return Code Values</span></span>  
 <span data-ttu-id="27e62-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="27e62-116">S_OK</span></span>  
 <span data-ttu-id="27e62-117">如果取消批处理，则 ISSAbort::Abort 方法返回 S_OK，否则返回 DB_E_CANTCANCEL\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="27e62-117">The **ISSAbort::Abort** method returns S_OK if the batch was canceled and DB_E_CANTCANCEL otherwise.</span></span> <span data-ttu-id="27e62-118">如果已经取消了批处理，则返回 DB_E_CANCELED。</span><span class="sxs-lookup"><span data-stu-id="27e62-118">If the batch has already been canceled, DB_E_CANCELED is returned.</span></span>  
  
 <span data-ttu-id="27e62-119">DB_E_CANCELED</span><span class="sxs-lookup"><span data-stu-id="27e62-119">DB_E_CANCELED</span></span>  
 <span data-ttu-id="27e62-120">已经取消批处理。</span><span class="sxs-lookup"><span data-stu-id="27e62-120">The batch has already been canceled.</span></span>  
  
 <span data-ttu-id="27e62-121">DB_E_CANTCANCEL</span><span class="sxs-lookup"><span data-stu-id="27e62-121">DB_E_CANTCANCEL</span></span>  
 <span data-ttu-id="27e62-122">批处理未取消。</span><span class="sxs-lookup"><span data-stu-id="27e62-122">The batch was not canceled.</span></span>  
  
 <span data-ttu-id="27e62-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="27e62-123">E_FAIL</span></span>  
 <span data-ttu-id="27e62-124">发生了特定于提供程序的错误;有关详细信息，请使用[ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md)接口。</span><span class="sxs-lookup"><span data-stu-id="27e62-124">A provider specific error occurred; for detailed information, use the [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md) interface.</span></span>  
  
 <span data-ttu-id="27e62-125">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="27e62-125">E_UNEXPECTED</span></span>  
 <span data-ttu-id="27e62-126">意外调用了该方法。</span><span class="sxs-lookup"><span data-stu-id="27e62-126">The call to the method was unexpected.</span></span> <span data-ttu-id="27e62-127">例如，因为已调用 ISSAbort::Abort，所以对象处于僵停状态\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="27e62-127">For example, the object is in a zombie state because **ISSAbort::Abort** has already been called.</span></span>  
  
 <span data-ttu-id="27e62-128">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="27e62-128">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="27e62-129">内存不足错误。</span><span class="sxs-lookup"><span data-stu-id="27e62-129">Out of memory error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27e62-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="27e62-130">See Also</span></span>  
 [<span data-ttu-id="27e62-131">ISSAbort &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="27e62-131">ISSAbort &#40;OLE DB&#41;</span></span>](../../database-engine/dev-guide/issabort-ole-db.md)  
  
  
