---
title: IBCPSession::BCPExec (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- IBCPSession::BCPExec (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- BCPExec method
ms.assetid: 0f4ebb63-cf03-4e53-846e-6c3021cde007
author: rothja
ms.author: jroth
ms.openlocfilehash: 1452888e046b6223c64a6cdf6fe09b074b815702
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687843"
---
# <a name="ibcpsessionbcpexec-ole-db"></a><span data-ttu-id="f5287-102">IBCPSession::BCPExec (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="f5287-102">IBCPSession::BCPExec (OLE DB)</span></span>
  <span data-ttu-id="f5287-103">执行大容量复制操作。</span><span class="sxs-lookup"><span data-stu-id="f5287-103">Performs the bulk copy operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5287-104">语法</span><span class="sxs-lookup"><span data-stu-id="f5287-104">Syntax</span></span>  
  
```  
  
HRESULT BCPExec(   
DBROWCOUNT *pRowsCopied);  
```  
  
## <a name="remarks"></a><span data-ttu-id="f5287-105">备注</span><span class="sxs-lookup"><span data-stu-id="f5287-105">Remarks</span></span>  
 <span data-ttu-id="f5287-106">BCPExec 方法将数据从用户文件复制到数据库表或执行相反的操作，具体取决于与 [IBCPSession::BCPInit](ibcpsession-bcpinit-ole-db.md) 方法一起使用的 eDirection 参数的值\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f5287-106">The **BCPExec** method copies data from a user file to a database table or vice versa, depending on the value of the *eDirection* parameter used with the [IBCPSession::BCPInit](ibcpsession-bcpinit-ole-db.md) method.</span></span>  
  
 <span data-ttu-id="f5287-107">在调用 BCPExec 之前，请用有效的用户文件名调用 BCPInit 方法\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f5287-107">Before calling **BCPExec**, call the **BCPInit** method with a valid user file name.</span></span> <span data-ttu-id="f5287-108">如果没有这样做，会导致错误。</span><span class="sxs-lookup"><span data-stu-id="f5287-108">Failure to do so results in an error.</span></span> <span data-ttu-id="f5287-109">唯一的例外就是如果查询要用于大容量复制操作。</span><span class="sxs-lookup"><span data-stu-id="f5287-109">The only exception is if a query is to be used for a bulk copy out operation.</span></span> <span data-ttu-id="f5287-110">这种情况下，在 BCPInit 方法中将表名指定为 NULL，然后使用 BCP_OPTION_HINTS 选项指定查询\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f5287-110">In that case specify NULL for the table name in the **BCPInit** method and then specify the query using the BCP_OPTION_HINTS option.</span></span>  
  
 <span data-ttu-id="f5287-111">BCPExec 方法是可能胜任任何时间长度的唯一大容量复制方法\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f5287-111">The **BCPExec** method is the only bulk copy method that is likely to be outstanding for any length of time.</span></span> <span data-ttu-id="f5287-112">因此，它是支持异步模式的唯一大容量复制方法。</span><span class="sxs-lookup"><span data-stu-id="f5287-112">It is therefore the only bulk copy method that supports asynchronous mode.</span></span> <span data-ttu-id="f5287-113">若要使用异步模式，请在调用 BCPExec 方法之前，将特定于提供程序的会话属性 SSPROP_ASYNCH_BULKCOPY 设置为 VARIANT_TRUE\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f5287-113">To use asynchronous mode, set the provider specific session property SSPROP_ASYNCH_BULKCOPY to VARIANT_TRUE before calling the **BCPExec** method.</span></span> <span data-ttu-id="f5287-114">此属性位于 DBPROPSET_SQLSERVERSESSION 属性集中。</span><span class="sxs-lookup"><span data-stu-id="f5287-114">This property is available in the DBPROPSET_SQLSERVERSESSION property set.</span></span> <span data-ttu-id="f5287-115">若要完成测试，请用相同参数调用 BCPExec 方法\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f5287-115">To test for completion, call the **BCPExec** method with the same parameters.</span></span> <span data-ttu-id="f5287-116">如果大容量复制尚未完成，则 BCPExec 方法会返回 DB_S_ASYNCHRONOUS\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f5287-116">If the bulk copy has not yet completed, the **BCPExec** method returns DB_S_ASYNCHRONOUS.</span></span> <span data-ttu-id="f5287-117">它还会在 pRowsCopied 参数中返回已发送到服务器或从服务器接收的行数的状态计数\*\*。</span><span class="sxs-lookup"><span data-stu-id="f5287-117">It also returns in the *pRowsCopied* argument a status count of the number of rows that have been sent to or received from the server.</span></span> <span data-ttu-id="f5287-118">发送到服务器的行直到到达批的末尾时才会提交。</span><span class="sxs-lookup"><span data-stu-id="f5287-118">Rows sent to the server are not committed until the end of a batch has been reached.</span></span>  
  
## <a name="arguments"></a><span data-ttu-id="f5287-119">参数</span><span class="sxs-lookup"><span data-stu-id="f5287-119">Arguments</span></span>  
 <span data-ttu-id="f5287-120">pRowsCopied\*\*[out]</span><span class="sxs-lookup"><span data-stu-id="f5287-120">*pRowsCopied*[out]</span></span>  
 <span data-ttu-id="f5287-121">指向 DWORD 的指针。</span><span class="sxs-lookup"><span data-stu-id="f5287-121">A pointer to a DWORD.</span></span> <span data-ttu-id="f5287-122">BCPExec 方法用成功复制的行数填充 DWORD\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f5287-122">The **BCPExec** method fills the DWORD with the number of rows successfully copied.</span></span> <span data-ttu-id="f5287-123">如果将 pRowsCopied 参数设置为 NULL，则 BCPExec 方法会忽略该参数\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f5287-123">If the *pRowsCopied* argument is set to NULL, it is ignored by the **BCPExec** method.</span></span>  
  
## <a name="return-code-values"></a><span data-ttu-id="f5287-124">返回代码值</span><span class="sxs-lookup"><span data-stu-id="f5287-124">Return Code Values</span></span>  
 <span data-ttu-id="f5287-125">S_OK</span><span class="sxs-lookup"><span data-stu-id="f5287-125">S_OK</span></span>  
 <span data-ttu-id="f5287-126">方法成功。</span><span class="sxs-lookup"><span data-stu-id="f5287-126">The method succeeded.</span></span>  
  
 <span data-ttu-id="f5287-127">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f5287-127">E_FAIL</span></span>  
 <span data-ttu-id="f5287-128">出现特定于提供程序的错误;有关详细信息，请使用[ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md)接口。</span><span class="sxs-lookup"><span data-stu-id="f5287-128">A provider-specific error occurred; for detailed information, use the [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md) interface.</span></span>  
  
 <span data-ttu-id="f5287-129">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="f5287-129">E_UNEXPECTED</span></span>  
 <span data-ttu-id="f5287-130">意外调用了该方法。</span><span class="sxs-lookup"><span data-stu-id="f5287-130">The call to the method was unexpected.</span></span> <span data-ttu-id="f5287-131">例如，在调用该方法之前，未调用 BCPInit 方法\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f5287-131">For example, the **BCPInit** method was not called before calling this method.</span></span> <span data-ttu-id="f5287-132">如果通过使用 BCP_OPTION_ABORT 选项中止了操作，并且随后调用了 BCPExec 方法，则也会发生此调用\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f5287-132">Also occurs if the operation has been aborted through using the BCP_OPTION_ABORT option, and the **BCPExec** method was called afterwards.</span></span>  
  
 <span data-ttu-id="f5287-133">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="f5287-133">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="f5287-134">内存不足错误。</span><span class="sxs-lookup"><span data-stu-id="f5287-134">Out-of-memory error.</span></span>  
  
 <span data-ttu-id="f5287-135">DB_S_ENDOFROWSET</span><span class="sxs-lookup"><span data-stu-id="f5287-135">DB_S_ENDOFROWSET</span></span>  
 <span data-ttu-id="f5287-136">大容量复制操作完成，所有数据传输已完成。</span><span class="sxs-lookup"><span data-stu-id="f5287-136">The bulk copy operation finished, and all the data transfer was completed.</span></span>  
  
 <span data-ttu-id="f5287-137">DB_S_ASYNCHRONOUS</span><span class="sxs-lookup"><span data-stu-id="f5287-137">DB_S_ASYNCHRONOUS</span></span>  
 <span data-ttu-id="f5287-138">当前这批行已复制。</span><span class="sxs-lookup"><span data-stu-id="f5287-138">The current batch of rows has been copied.</span></span> <span data-ttu-id="f5287-139">请再次调用 BCPExec 方法以传输下一批\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f5287-139">Call the **BCPExec** method again to transfer the next batch.</span></span>  
  
 <span data-ttu-id="f5287-140">DB_S_ERRORSOCCURRED</span><span class="sxs-lookup"><span data-stu-id="f5287-140">DB_S_ERRORSOCCURRED</span></span>  
 <span data-ttu-id="f5287-141">在大容量复制操作期间出现错误，可能尚未复制某些行。</span><span class="sxs-lookup"><span data-stu-id="f5287-141">Errors occurred during the bulk copy operation, and some rows might not have been copied.</span></span> <span data-ttu-id="f5287-142">错误数仍然小于允许的最大错误数。</span><span class="sxs-lookup"><span data-stu-id="f5287-142">The number of errors is still less than the maximum errors allowed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5287-143">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f5287-143">See Also</span></span>  
 <span data-ttu-id="f5287-144">[IBCPSession &#40;OLE DB&#41;](ibcpsession-ole-db.md) </span><span class="sxs-lookup"><span data-stu-id="f5287-144">[IBCPSession &#40;OLE DB&#41;](ibcpsession-ole-db.md) </span></span>  
 [<span data-ttu-id="f5287-145">执行大容量复制操作</span><span class="sxs-lookup"><span data-stu-id="f5287-145">Performing Bulk Copy Operations</span></span>](../native-client/features/performing-bulk-copy-operations.md)  
  
  
