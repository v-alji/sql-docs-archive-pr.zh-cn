---
title: 错误 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, errors
- OLE/COM errors
- errors [OLE DB]
- OLE DB error handling, about error handling
- OLE DB error handling
ms.assetid: bd0612f4-96ef-4919-b0f9-b5447210fe93
author: rothja
ms.author: jroth
ms.openlocfilehash: 0560a31b60a10e278f621aa53f1c7fa038fe8039
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589546"
---
# <a name="errors"></a><span data-ttu-id="c1e11-102">错误</span><span class="sxs-lookup"><span data-stu-id="c1e11-102">Errors</span></span>
  <span data-ttu-id="c1e11-103">OLE/COM 对象通过对象成员函数的 HRESULT 返回代码报告错误。</span><span class="sxs-lookup"><span data-stu-id="c1e11-103">OLE/COM objects report errors through the HRESULT return code of object member functions.</span></span> <span data-ttu-id="c1e11-104">OLE/COM HRESULT 是一种位压缩结构。</span><span class="sxs-lookup"><span data-stu-id="c1e11-104">An OLE/COM HRESULT is a bit-packed structure.</span></span> <span data-ttu-id="c1e11-105">OLE 提供取消对结构成员的引用的宏。</span><span class="sxs-lookup"><span data-stu-id="c1e11-105">OLE provides macros that dereference structure members.</span></span>  
  
 <span data-ttu-id="c1e11-106">OLE/COM 指定 IErrorInfo 接口  。</span><span class="sxs-lookup"><span data-stu-id="c1e11-106">OLE/COM specifies the **IErrorInfo** interface.</span></span> <span data-ttu-id="c1e11-107">该接口公开 GetDescription 之类的方法  。</span><span class="sxs-lookup"><span data-stu-id="c1e11-107">The interface exposes methods such as **GetDescription**.</span></span> <span data-ttu-id="c1e11-108">这允许客户端从 OLE/COM 服务器提取错误详细信息。</span><span class="sxs-lookup"><span data-stu-id="c1e11-108">This allows clients to extract error details from OLE/COM servers.</span></span> <span data-ttu-id="c1e11-109">OLE DB 扩展 IErrorInfo 以支持返回针对单成员函数执行的多个错误信息包  。</span><span class="sxs-lookup"><span data-stu-id="c1e11-109">OLE DB extends **IErrorInfo** to support the return of multiple error information packets on a single-member function execution.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="c1e11-110">可以返回多个错误。</span><span class="sxs-lookup"><span data-stu-id="c1e11-110">can return multiple errors.</span></span> <span data-ttu-id="c1e11-111">通过调用 [IMultipleResults::GetResult](https://go.microsoft.com/fwlink/?LinkId=129630) 并结合 ISQLErrorInfo 和 IErrorRecords，应用程序可以一次检索一个服务器错误。</span><span class="sxs-lookup"><span data-stu-id="c1e11-111">An application can retrieve server errors one at a time by calling [IMultipleResults::GetResult](https://go.microsoft.com/fwlink/?LinkId=129630) combined with ISQLErrorInfo and IErrorRecords.</span></span>  
  
 <span data-ttu-id="c1e11-112">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供程序公开了 OLE DB 的增强型**IErrorInfo**、自定义 `ISQLErrorInfo` 和特定于提供程序的[ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md)错误对象接口。</span><span class="sxs-lookup"><span data-stu-id="c1e11-112">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider exposes the OLE DB record-enhanced **IErrorInfo**, the custom `ISQLErrorInfo`, and the provider-specific [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md) error object interfaces.</span></span>  
  
 <span data-ttu-id="c1e11-113">有关跟踪错误的详细信息，请参阅[数据访问跟踪](https://go.microsoft.com/fwlink/?LinkId=125805)。</span><span class="sxs-lookup"><span data-stu-id="c1e11-113">For information about tracing errors, see [Data Access Tracing](https://go.microsoft.com/fwlink/?LinkId=125805).</span></span> <span data-ttu-id="c1e11-114">有关 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 中添加的错误跟踪的增强功能的信息，请参阅[访问扩展事件日志中的诊断信息](../native-client/features/accessing-diagnostic-information-in-the-extended-events-log.md)。</span><span class="sxs-lookup"><span data-stu-id="c1e11-114">For information about enhancements to error tracing added in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], see [Accessing Diagnostic Information in the Extended Events Log](../native-client/features/accessing-diagnostic-information-in-the-extended-events-log.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c1e11-115">本节内容</span><span class="sxs-lookup"><span data-stu-id="c1e11-115">In This Section</span></span>  
  
-   [<span data-ttu-id="c1e11-116">返回代码</span><span class="sxs-lookup"><span data-stu-id="c1e11-116">Return Codes</span></span>](return-codes.md)  
  
-   [<span data-ttu-id="c1e11-117">错误接口中的信息</span><span class="sxs-lookup"><span data-stu-id="c1e11-117">Information in Error Interfaces</span></span>](information-in-error-interfaces.md)  
  
-   [<span data-ttu-id="c1e11-118">SQL Server 错误详细信息</span><span class="sxs-lookup"><span data-stu-id="c1e11-118">SQL Server Error Detail</span></span>](sql-server-error-detail.md)  
  
-   [<span data-ttu-id="c1e11-119">检索错误信息</span><span class="sxs-lookup"><span data-stu-id="c1e11-119">Retrieving Error Information</span></span>](retrieving-error-information.md)  
  
-   [<span data-ttu-id="c1e11-120">SQL Server 消息结果</span><span class="sxs-lookup"><span data-stu-id="c1e11-120">SQL Server Message Results</span></span>](sql-server-message-results.md)  
  
## <a name="see-also"></a><span data-ttu-id="c1e11-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c1e11-121">See Also</span></span>  
 [<span data-ttu-id="c1e11-122">SQL Server Native Client (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="c1e11-122">SQL Server Native Client &#40;OLE DB&#41;</span></span>](../native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
