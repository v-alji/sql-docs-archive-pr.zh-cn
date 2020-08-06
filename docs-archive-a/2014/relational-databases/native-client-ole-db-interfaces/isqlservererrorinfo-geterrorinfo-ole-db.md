---
title: ISQLServerErrorInfo::GetErrorInfo (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- ISQLServerErrorInfo::GetErrorInfo (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- GetErrorInfo method
ms.assetid: 83265c9c-eaf9-41f0-9f73-b0ae0972f0d5
author: rothja
ms.author: jroth
ms.openlocfilehash: c3e325cd99276e04a178b89c19b233289edc09fa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690605"
---
# <a name="isqlservererrorinfogeterrorinfo-ole-db"></a><span data-ttu-id="2237e-102">ISQLServerErrorInfo::GetErrorInfo (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="2237e-102">ISQLServerErrorInfo::GetErrorInfo (OLE DB)</span></span>
  <span data-ttu-id="2237e-103">返回一个指针，该指针指向 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 包含 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 错误详细信息的 Native Client OLE DB provider SSERRORINFO 结构。</span><span class="sxs-lookup"><span data-stu-id="2237e-103">Returns a pointer to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider SSERRORINFO structure containing the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error details.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2237e-104">语法</span><span class="sxs-lookup"><span data-stu-id="2237e-104">Syntax</span></span>  
  
```  
  
   HRESULT GetErrorInfo(  
SSERRORINFO**ppSSErrorInfo,  
OLECHAR**ppErrorStrings);  
```  
  
## <a name="arguments"></a><span data-ttu-id="2237e-105">参数</span><span class="sxs-lookup"><span data-stu-id="2237e-105">Arguments</span></span>  
 <span data-ttu-id="2237e-106">ppSSErrorInfo[out]\*\*</span><span class="sxs-lookup"><span data-stu-id="2237e-106">*ppSSErrorInfo*[out]</span></span>  
 <span data-ttu-id="2237e-107">指向 SSERRORINFO 结构的指针。</span><span class="sxs-lookup"><span data-stu-id="2237e-107">A pointer to a SSERRORINFO structure.</span></span> <span data-ttu-id="2237e-108">如果方法失败或者不存在与该错误关联的任何 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 信息，则访问接口不会分配任何内存，并且会确保 ppSSErrorInfo 参数在输出时为一个空指针\*\*。</span><span class="sxs-lookup"><span data-stu-id="2237e-108">If the method fails or there is no [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] information associated with the error, the provider does not allocate any memory, and ensures that the *ppSSErrorInfo* argument is a null pointer on output.</span></span>  
  
 <span data-ttu-id="2237e-109">ppErrorStrings[out]\*\*</span><span class="sxs-lookup"><span data-stu-id="2237e-109">*ppErrorStrings*[out]</span></span>  
 <span data-ttu-id="2237e-110">指向 Unicode 字符串指针的指针。</span><span class="sxs-lookup"><span data-stu-id="2237e-110">A pointer to a Unicode character-string pointer.</span></span> <span data-ttu-id="2237e-111">如果方法失败或者不存在与该错误关联的任何 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 信息，则访问接口不会分配任何内存，并且会确保 ppErrorStrings 参数在输出时为一个空指针\*\*。</span><span class="sxs-lookup"><span data-stu-id="2237e-111">If the method fails or there is no [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] information associated with an error, the provider does not allocate any memory, and ensures that the *ppErrorStrings* argument is a null pointer on output.</span></span> <span data-ttu-id="2237e-112">如果使用 IMalloc::Free 方法释放 ppErrorStrings 参数，则会释放所返回的 SSERRORINFO 结构的三个单个字符串成员，因为内存是按块进行分配的\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2237e-112">Freeing the *ppErrorStrings* argument with the **IMalloc::Free** method frees the three individual string members of the returned SSERRORINFO structure, as the memory is allocated in a block.</span></span>  
  
## <a name="return-code-values"></a><span data-ttu-id="2237e-113">返回代码值</span><span class="sxs-lookup"><span data-stu-id="2237e-113">Return Code Values</span></span>  
 <span data-ttu-id="2237e-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="2237e-114">S_OK</span></span>  
 <span data-ttu-id="2237e-115">方法成功。</span><span class="sxs-lookup"><span data-stu-id="2237e-115">The method succeeded.</span></span>  
  
 <span data-ttu-id="2237e-116">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="2237e-116">E_INVALIDARG</span></span>  
 <span data-ttu-id="2237e-117">ppSSErrorInfo\*\* 或 ppErrorStrings\*\* 参数为 NULL。</span><span class="sxs-lookup"><span data-stu-id="2237e-117">Either the *ppSSErrorInfo* or the *ppErrorStrings* argument was NULL.</span></span>  
  
 <span data-ttu-id="2237e-118">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="2237e-118">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="2237e-119">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供程序无法分配足够的内存来完成请求。</span><span class="sxs-lookup"><span data-stu-id="2237e-119">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider could not allocate sufficient memory to complete the request.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2237e-120">备注</span><span class="sxs-lookup"><span data-stu-id="2237e-120">Remarks</span></span>  
 <span data-ttu-id="2237e-121">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供程序为通过使用者传递的指针返回的 SSERRORINFO 和 OLECHAR 字符串分配内存。</span><span class="sxs-lookup"><span data-stu-id="2237e-121">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider allocates memory for the SSERRORINFO and OLECHAR strings returned through the pointers passed by the consumer.</span></span> <span data-ttu-id="2237e-122">当使用者不再需要访问错误数据时，使用者必须使用 IMalloc::Free 方法释放该内存\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2237e-122">The consumer must deallocate this memory by using the **IMalloc::Free** method when it no longer requires access to the error data.</span></span>  
  
 <span data-ttu-id="2237e-123">SSERRORINFO 结构的定义如下所示：</span><span class="sxs-lookup"><span data-stu-id="2237e-123">The SSERRORINFO structure is defined as follows:</span></span>  
  
```  
typedef struct tagSSErrorInfo  
   {  
   LPOLESTR pwszMessage;  
   LPOLESTR pwszServer;  
   LPOLESTR pwszProcedure;  
   LONG lNative;  
   BYTE bState;  
   BYTE bClass;  
   WORD wLineNumber;  
   }  
SSERRORINFO;  
```  
  
|<span data-ttu-id="2237e-124">成员</span><span class="sxs-lookup"><span data-stu-id="2237e-124">Member</span></span>|<span data-ttu-id="2237e-125">描述</span><span class="sxs-lookup"><span data-stu-id="2237e-125">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="2237e-126">pwszMessage\*\*</span><span class="sxs-lookup"><span data-stu-id="2237e-126">*pwszMessage*</span></span>|<span data-ttu-id="2237e-127">来自 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的错误消息。</span><span class="sxs-lookup"><span data-stu-id="2237e-127">The error message from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="2237e-128">消息是通过 IErrorInfo::GetDescription 方法返回的\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2237e-128">The message is returned through the **IErrorInfo::GetDescription** method.</span></span>|  
|<span data-ttu-id="2237e-129">pwszServer\*\*</span><span class="sxs-lookup"><span data-stu-id="2237e-129">*pwszServer*</span></span>|<span data-ttu-id="2237e-130">在其上发生了该错误的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例的名称。</span><span class="sxs-lookup"><span data-stu-id="2237e-130">The name of the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on which the error occurred.</span></span>|  
|<span data-ttu-id="2237e-131">pwszProcedure\*\*</span><span class="sxs-lookup"><span data-stu-id="2237e-131">*pwszProcedure*</span></span>|<span data-ttu-id="2237e-132">如果错误发生在存储过程中，则为生成该错误的存储过程的名称；否则，为空字符串。</span><span class="sxs-lookup"><span data-stu-id="2237e-132">The name of the stored procedure generating the error if the error occurred in a stored procedure; otherwise, an empty string.</span></span>|  
|<span data-ttu-id="2237e-133">lNative\*\*</span><span class="sxs-lookup"><span data-stu-id="2237e-133">*lNative*</span></span>|<span data-ttu-id="2237e-134">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 错误号。</span><span class="sxs-lookup"><span data-stu-id="2237e-134">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error number.</span></span> <span data-ttu-id="2237e-135">该错误号与在 ISQLErrorInfo::GetSQLInfo 方法的 plNativeError 参数中返回的错误号相同\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2237e-135">The error number is identical to that returned in the *plNativeError* parameter of the **ISQLErrorInfo::GetSQLInfo** method.</span></span>|  
|<span data-ttu-id="2237e-136">bState\*\*</span><span class="sxs-lookup"><span data-stu-id="2237e-136">*bState*</span></span>|<span data-ttu-id="2237e-137">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 错误的状态。</span><span class="sxs-lookup"><span data-stu-id="2237e-137">The state of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error.</span></span>|  
|<span data-ttu-id="2237e-138">bClass\*\*</span><span class="sxs-lookup"><span data-stu-id="2237e-138">*bClass*</span></span>|<span data-ttu-id="2237e-139">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 错误的严重性。</span><span class="sxs-lookup"><span data-stu-id="2237e-139">The severity of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error.</span></span>|  
|<span data-ttu-id="2237e-140">wLineNumber\*\*</span><span class="sxs-lookup"><span data-stu-id="2237e-140">*wLineNumber*</span></span>|<span data-ttu-id="2237e-141">如果适用，为生成错误消息的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 存储过程的行。</span><span class="sxs-lookup"><span data-stu-id="2237e-141">When applicable, the line of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stored procedure that generated the error message.</span></span> <span data-ttu-id="2237e-142">如果与过程无关，则为默认值 1。</span><span class="sxs-lookup"><span data-stu-id="2237e-142">If no procedure is involved, the default value is 1.</span></span>|  
  
 <span data-ttu-id="2237e-143">结构中的指针引用在 ppErrorStrings 参数中返回的字符串中的地址\*\*。</span><span class="sxs-lookup"><span data-stu-id="2237e-143">Pointers in the structure reference addresses in the string returned in the *ppErrorStrings* argument.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2237e-144">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2237e-144">See Also</span></span>  
 <span data-ttu-id="2237e-145">[ISQLServerErrorInfo &#40;OLE DB&#41;](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md) </span><span class="sxs-lookup"><span data-stu-id="2237e-145">[ISQLServerErrorInfo &#40;OLE DB&#41;](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md) </span></span>  
 [<span data-ttu-id="2237e-146">RAISERROR (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="2237e-146">RAISERROR &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/language-elements/raiserror-transact-sql)  
  
  
