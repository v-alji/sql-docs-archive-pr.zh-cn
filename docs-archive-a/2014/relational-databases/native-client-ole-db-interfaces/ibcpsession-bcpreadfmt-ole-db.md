---
title: IBCPSession::BCPReadFmt (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- IBCPSession::BCPReadFmt (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- BCPReadFmt method
ms.assetid: e2a12050-94e4-48a3-8a48-b780d646f116
author: rothja
ms.author: jroth
ms.openlocfilehash: ca811dceb8ab6771e3bdd6689a8e11eca6a0e3ef
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692881"
---
# <a name="ibcpsessionbcpreadfmt-ole-db"></a><span data-ttu-id="515e7-102">IBCPSession::BCPReadFmt (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="515e7-102">IBCPSession::BCPReadFmt (OLE DB)</span></span>
  <span data-ttu-id="515e7-103">从格式化文件中读取每一列的格式信息。</span><span class="sxs-lookup"><span data-stu-id="515e7-103">Reads format information for each column from the format file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="515e7-104">语法</span><span class="sxs-lookup"><span data-stu-id="515e7-104">Syntax</span></span>  
  
```  
  
HRESULT BCPReadFmt(   
const wchar_t *pwszFormatFile);  
```  
  
## <a name="remarks"></a><span data-ttu-id="515e7-105">备注</span><span class="sxs-lookup"><span data-stu-id="515e7-105">Remarks</span></span>  
 <span data-ttu-id="515e7-106">可使用 BCPReadFmt 方法从格式化文件中读取数据，其中该文件指定数据文件中的数据格式\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="515e7-106">The **BCPReadFmt** method is used for reading data from a format file that specifies the format of data in the data file.</span></span> <span data-ttu-id="515e7-107">此方法能够检测格式化文件的正确版本。</span><span class="sxs-lookup"><span data-stu-id="515e7-107">This method is capable of detecting the correct version of the format file.</span></span> <span data-ttu-id="515e7-108">它可以自动检测格式化文件采用的是 xml 格式还是旧式的文本格式，并据此执行操作。</span><span class="sxs-lookup"><span data-stu-id="515e7-108">It can automatically detect whether the format file is in xml or old style text format and behaves accordingly.</span></span> <span data-ttu-id="515e7-109">本机客户端支持的格式化文件版本 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OLE DB 提供程序 BCP 为版本6.0 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="515e7-109">The format file versions supported by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider BCP are version 6.0 or newer.</span></span>  
  
 <span data-ttu-id="515e7-110">BCPReadFmt 方法在读取格式值之后，会相应调用 [IBCPSession::BCPColumns](ibcpsession-bcpcolumns-ole-db.md) 和 [IBCPSession::BCPColFmt](ibcpsession-bcpcolfmt-ole-db.md) 方法\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="515e7-110">After the **BCPReadFmt** method reads the format values, it makes the appropriate calls to the [IBCPSession::BCPColumns](ibcpsession-bcpcolumns-ole-db.md) and [IBCPSession::BCPColFmt](ibcpsession-bcpcolfmt-ole-db.md) methods.</span></span> <span data-ttu-id="515e7-111">用户不必分析格式化文件并发出上述调用。</span><span class="sxs-lookup"><span data-stu-id="515e7-111">There is no need for the user to parse a format file and make these calls.</span></span>  
  
 <span data-ttu-id="515e7-112">要保存格式化文件，请调用 [IBCPSession::BCPWriteFmt](ibcpsession-bcpwritefmt-ole-db.md) 方法。</span><span class="sxs-lookup"><span data-stu-id="515e7-112">To save a format file, call the [IBCPSession::BCPWriteFmt](ibcpsession-bcpwritefmt-ole-db.md) method.</span></span> <span data-ttu-id="515e7-113">调用 BCPReadFmt 方法可引用保存的格式\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="515e7-113">Calls to the **BCPReadFmt** method can reference saved formats.</span></span> <span data-ttu-id="515e7-114">或者，可使用大容量复制实用工具 (bcp) 将用户定义数据格式保存在可由 BCPReadFmt 方法引用的文件中\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="515e7-114">Alternatively, the bulk-copy utility (**bcp**) can save user-defined data formats in files that can be referenced by the **BCPReadFmt** method.</span></span>  
  
 <span data-ttu-id="515e7-115">`BCP_OPTION_DELAYREADFMT` [IBCPSession：： BCPControl](ibcpsession-bcpcontrol-ole-db.md)的*eOption*参数的值修改了 IBCPSession：： BCPReadFmt 的行为。</span><span class="sxs-lookup"><span data-stu-id="515e7-115">The `BCP_OPTION_DELAYREADFMT` value of the *eOption* parameter of [IBCPSession::BCPControl](ibcpsession-bcpcontrol-ole-db.md) modifies the behavior of IBCPSession::BCPReadFmt.</span></span>  
  
## <a name="arguments"></a><span data-ttu-id="515e7-116">参数</span><span class="sxs-lookup"><span data-stu-id="515e7-116">Arguments</span></span>  
 <span data-ttu-id="515e7-117">pwszFormatFile\*\*[in]</span><span class="sxs-lookup"><span data-stu-id="515e7-117">*pwszFormatFile*[in]</span></span>  
 <span data-ttu-id="515e7-118">包含数据文件格式值的文件的路径和文件名。</span><span class="sxs-lookup"><span data-stu-id="515e7-118">The path and file name of the file containing the format values for the data file.</span></span>  
  
## <a name="return-code-values"></a><span data-ttu-id="515e7-119">返回代码值</span><span class="sxs-lookup"><span data-stu-id="515e7-119">Return Code Values</span></span>  
 <span data-ttu-id="515e7-120">S_OK</span><span class="sxs-lookup"><span data-stu-id="515e7-120">S_OK</span></span>  
 <span data-ttu-id="515e7-121">方法成功。</span><span class="sxs-lookup"><span data-stu-id="515e7-121">The method succeeded.</span></span>  
  
 <span data-ttu-id="515e7-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="515e7-122">E_FAIL</span></span>  
 <span data-ttu-id="515e7-123">出现访问接口特定的错误；要获取详细信息，请使用 [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md) 接口。</span><span class="sxs-lookup"><span data-stu-id="515e7-123">A provider-specific error occurred, for detailed information use the [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md) interface.</span></span>  
  
 <span data-ttu-id="515e7-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="515e7-124">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="515e7-125">内存不足错误。</span><span class="sxs-lookup"><span data-stu-id="515e7-125">Out of memory error.</span></span>  
  
 <span data-ttu-id="515e7-126">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="515e7-126">E_UNEXPECTED</span></span>  
 <span data-ttu-id="515e7-127">意外调用了该方法。</span><span class="sxs-lookup"><span data-stu-id="515e7-127">The call to the method was unexpected.</span></span> <span data-ttu-id="515e7-128">例如，在调用该方法之前，未调用 [IBCPSession::BCPInit](ibcpsession-bcpinit-ole-db.md) 方法。</span><span class="sxs-lookup"><span data-stu-id="515e7-128">For example, the [IBCPSession::BCPInit](ibcpsession-bcpinit-ole-db.md) method was not called before calling this method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="515e7-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="515e7-129">See Also</span></span>  
 <span data-ttu-id="515e7-130">[IBCPSession &#40;OLE DB&#41;](ibcpsession-ole-db.md) </span><span class="sxs-lookup"><span data-stu-id="515e7-130">[IBCPSession &#40;OLE DB&#41;](ibcpsession-ole-db.md) </span></span>  
 [<span data-ttu-id="515e7-131">执行大容量复制操作</span><span class="sxs-lookup"><span data-stu-id="515e7-131">Performing Bulk Copy Operations</span></span>](../native-client/features/performing-bulk-copy-operations.md)  
  
  
