---
title: SQL Server 错误详细信息 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, errors
- errors [OLE DB], error details
- IErrorRecords interface
- IErrorInfo interface
- OLE DB error handling, error details
- ISQLServerErrorInfo interface
ms.assetid: 51500ee3-3d78-47ec-b90f-ebfc55642e06
author: rothja
ms.author: jroth
ms.openlocfilehash: 4c03cf62dd274f9bcca213d33fb8969b26c9d980
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589537"
---
# <a name="sql-server-error-detail"></a><span data-ttu-id="ce608-102">SQL Server 错误详细信息</span><span class="sxs-lookup"><span data-stu-id="ce608-102">SQL Server Error Detail</span></span>
  <span data-ttu-id="ce608-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供程序定义特定于访问接口的错误接口[ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md)。</span><span class="sxs-lookup"><span data-stu-id="ce608-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider defines the provider-specific error interface [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md).</span></span> <span data-ttu-id="ce608-104">该接口返回有关 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 错误的更多详细信息，在命令执行或行集操作失败时这些信息很有用。</span><span class="sxs-lookup"><span data-stu-id="ce608-104">The interface returns more detail about a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error and is valuable when command execution or rowset operations fail.</span></span>  
  
 <span data-ttu-id="ce608-105">可以用两种方式访问 ISQLServerErrorInfo 接口\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ce608-105">There are two ways to obtain access to **ISQLServerErrorInfo** interface.</span></span>  
  
 <span data-ttu-id="ce608-106">使用者可调用 IErrorRecords::GetCustomerErrorObject 以获得 ISQLServerErrorInfo 指针，如以下代码示例所示\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ce608-106">The consumer may call **IErrorRecords::GetCustomerErrorObject** to obtain an **ISQLServerErrorInfo** pointer, as shown in the following code sample.</span></span> <span data-ttu-id="ce608-107">（不需要获得 ISQLErrorInfo。）ISQLErrorInfo 和 ISQLServerErrorInfo 都是自定义的 OLE DB 错误对象，并以 ISQLServerErrorInfo 作为用于获得服务器错误信息（包括诸如过程名称和行号这样的详细信息）的接口\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ce608-107">(There is no need to obtain **ISQLErrorInfo.**) Both **ISQLErrorInfo** and **ISQLServerErrorInfo** are custom OLE DB error objects, with **ISQLServerErrorInfo** being the interface to use to obtain information of server errors, including such details as procedure name and line numbers.</span></span>  
  
```  
// Get the SQL Server custom error object.  
if(FAILED(hr=pIErrorRecords->GetCustomErrorObject(  
   nRec, IID_ISQLServerErrorInfo,  
   (IUnknown**)&pISQLServerErrorErrorInfo)))  
```  
  
 <span data-ttu-id="ce608-108">获得 ISQLServerErrorInfo 指针的另一个方式是调用已经获得的 ISQLErrorInfo 指针的 QueryInterface 方法\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ce608-108">Another way to get an **ISQLServerErrorInfo** pointer is to call the **QueryInterface** method on an already-obtained **ISQLErrorInfo** pointer.</span></span> <span data-ttu-id="ce608-109">注意，由于 ISQLServerErrorInfo 包含从 ISQLErrorInfo 获得的信息的超集，因此通过 GetCustomerErrorObject 直接转到 ISQLServerErrorInfo 是有意义的\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ce608-109">Note that because **ISQLServerErrorInfo** contains a superset of the information available from **ISQLErrorInfo**, it makes sense to go directly to **ISQLServerErrorInfo** through **GetCustomerErrorObject**.</span></span>  
  
 <span data-ttu-id="ce608-110">ISQLServerErrorInfo 接口公开了一个成员函数 [ISQLServerErrorInfo::GetErrorInfo](../native-client-ole-db-interfaces/isqlservererrorinfo-geterrorinfo-ole-db.md)\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ce608-110">The **ISQLServerErrorInfo** interface exposes one member function, [ISQLServerErrorInfo::GetErrorInfo](../native-client-ole-db-interfaces/isqlservererrorinfo-geterrorinfo-ole-db.md).</span></span> <span data-ttu-id="ce608-111">该函数返回 SSERRORINFO 结构的指针和字符串缓冲区的指针。</span><span class="sxs-lookup"><span data-stu-id="ce608-111">The function returns a pointer to an SSERRORINFO structure and a pointer to a string buffer.</span></span> <span data-ttu-id="ce608-112">两个指针都引用使用者必须使用 IMalloc::Free 方法释放的内存\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ce608-112">Both pointers reference memory the consumer must deallocate by using the **IMalloc::Free** method.</span></span>  
  
 <span data-ttu-id="ce608-113">SSERRORINFO 结构成员由使用者解释如下。</span><span class="sxs-lookup"><span data-stu-id="ce608-113">SSERRORINFO structure members are interpreted by the consumer as follows.</span></span>  
  
|<span data-ttu-id="ce608-114">成员</span><span class="sxs-lookup"><span data-stu-id="ce608-114">Member</span></span>|<span data-ttu-id="ce608-115">描述</span><span class="sxs-lookup"><span data-stu-id="ce608-115">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="ce608-116">pwszMessage\*\*</span><span class="sxs-lookup"><span data-stu-id="ce608-116">*pwszMessage*</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="ce608-117">错误消息。</span><span class="sxs-lookup"><span data-stu-id="ce608-117">error message.</span></span> <span data-ttu-id="ce608-118">与在 IErrorInfo::GetDescription 中返回的字符串相同\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ce608-118">Identical to the string returned in **IErrorInfo::GetDescription**.</span></span>|  
|<span data-ttu-id="ce608-119">pwszServer\*\*</span><span class="sxs-lookup"><span data-stu-id="ce608-119">*pwszServer*</span></span>|<span data-ttu-id="ce608-120">会话的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例的名称。</span><span class="sxs-lookup"><span data-stu-id="ce608-120">Name of the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] for the session.</span></span>|  
|<span data-ttu-id="ce608-121">pwszProcedure\*\*</span><span class="sxs-lookup"><span data-stu-id="ce608-121">*pwszProcedure*</span></span>|<span data-ttu-id="ce608-122">如果适用，则为产生错误的过程的名称。</span><span class="sxs-lookup"><span data-stu-id="ce608-122">If appropriate, the name of the procedure in which the error originated.</span></span> <span data-ttu-id="ce608-123">否则为空字符串。</span><span class="sxs-lookup"><span data-stu-id="ce608-123">An empty string otherwise.</span></span>|  
|<span data-ttu-id="ce608-124">lNative\*\*</span><span class="sxs-lookup"><span data-stu-id="ce608-124">*lNative*</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="ce608-125">本机错误号。</span><span class="sxs-lookup"><span data-stu-id="ce608-125">native error number.</span></span> <span data-ttu-id="ce608-126">与在 ISQLErrorInfo::GetSQLInfo 的 plNativeError 参数中返回的值相同\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ce608-126">Identical to the value returned in the *plNativeError* parameter of **ISQLErrorInfo::GetSQLInfo**.</span></span>|  
|<span data-ttu-id="ce608-127">bState\*\*</span><span class="sxs-lookup"><span data-stu-id="ce608-127">*bState*</span></span>|<span data-ttu-id="ce608-128">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 错误消息的状态。</span><span class="sxs-lookup"><span data-stu-id="ce608-128">State of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error message.</span></span>|  
|<span data-ttu-id="ce608-129">bClass\*\*</span><span class="sxs-lookup"><span data-stu-id="ce608-129">*bClass*</span></span>|<span data-ttu-id="ce608-130">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 错误消息的严重性。</span><span class="sxs-lookup"><span data-stu-id="ce608-130">Severity of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error message.</span></span>|  
|<span data-ttu-id="ce608-131">wLineNumber\*\*</span><span class="sxs-lookup"><span data-stu-id="ce608-131">*wLineNumber*</span></span>|<span data-ttu-id="ce608-132">如果适用，则为发生错误的存储过程的行号。</span><span class="sxs-lookup"><span data-stu-id="ce608-132">When applicable, the line number of a stored procedure on which the error occurred.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ce608-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ce608-133">See Also</span></span>  
 <span data-ttu-id="ce608-134">[错误](errors.md) </span><span class="sxs-lookup"><span data-stu-id="ce608-134">[Errors](errors.md) </span></span>  
 [<span data-ttu-id="ce608-135">RAISERROR (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="ce608-135">RAISERROR &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/language-elements/raiserror-transact-sql)  
  
  
