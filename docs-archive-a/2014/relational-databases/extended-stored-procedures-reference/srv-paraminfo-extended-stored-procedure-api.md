---
title: srv_paraminfo（扩展存储过程 API）| Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_paraminfo
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_paraminfo
ms.assetid: ee2afd4e-0d91-462b-9403-98d481546330
author: rothja
ms.author: jroth
ms.openlocfilehash: cc3d51acc2ca560246c46267840db72934223999
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693907"
---
# <a name="srv_paraminfo-extended-stored-procedure-api"></a><span data-ttu-id="609d8-102">srv_paraminfo（扩展存储过程 API）</span><span class="sxs-lookup"><span data-stu-id="609d8-102">srv_paraminfo (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]<span data-ttu-id="609d8-103">请改用 CLR 集成。</span><span class="sxs-lookup"><span data-stu-id="609d8-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="609d8-104">返回有关参数的信息。</span><span class="sxs-lookup"><span data-stu-id="609d8-104">Returns information about a parameter.</span></span> <span data-ttu-id="609d8-105">此函数取代了以下函数：[srv_paramtype](srv-paramtype-extended-stored-procedure-api.md)、[srv_paramlen](srv-paramlen-extended-stored-procedure-api.md)、[srv_parammaxlen](srv-parammaxlen-extended-stored-procedure-api.md) 和 [srv_paramdata](srv-paramdata-extended-stored-procedure-api.md)。</span><span class="sxs-lookup"><span data-stu-id="609d8-105">This function supersedes the following functions: [srv_paramtype](srv-paramtype-extended-stored-procedure-api.md), [srv_paramlen](srv-paramlen-extended-stored-procedure-api.md), [srv_parammaxlen](srv-parammaxlen-extended-stored-procedure-api.md), and [srv_paramdata](srv-paramdata-extended-stored-procedure-api.md).</span></span> <span data-ttu-id="609d8-106">srv_paraminfo 支持[数据类型](data-types-extended-stored-procedure-api.md)中的数据类型和长度为零的数据\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="609d8-106">**srv_paraminfo** supports the data types in [Data Types](data-types-extended-stored-procedure-api.md) and zero-length data.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="609d8-107">语法</span><span class="sxs-lookup"><span data-stu-id="609d8-107">Syntax</span></span>  
  
```  
  
int srv_paraminfo (  
SRV_PROC *  
srvproc  
,  
int  
n  
,  
BYTE *  
pbType  
,  
ULONG *  
pcbMaxLen  
,  
ULONG *  
pcbActualLen  
,  
BYTE *  
pbData  
,  
BOOL *  
pfNull  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="609d8-108">参数</span><span class="sxs-lookup"><span data-stu-id="609d8-108">Arguments</span></span>  
 <span data-ttu-id="609d8-109">srvproc\*\*</span><span class="sxs-lookup"><span data-stu-id="609d8-109">*srvproc*</span></span>  
 <span data-ttu-id="609d8-110">客户端连接的句柄。</span><span class="sxs-lookup"><span data-stu-id="609d8-110">A handle for a client connection.</span></span>  
  
 <span data-ttu-id="609d8-111">*n*</span><span class="sxs-lookup"><span data-stu-id="609d8-111">*n*</span></span>  
 <span data-ttu-id="609d8-112">要设置的参数的序号。</span><span class="sxs-lookup"><span data-stu-id="609d8-112">The ordinal number of the parameter to be set.</span></span> <span data-ttu-id="609d8-113">第一个参数是 1。</span><span class="sxs-lookup"><span data-stu-id="609d8-113">The first parameter is 1.</span></span>  
  
 <span data-ttu-id="609d8-114">pbType\*\*</span><span class="sxs-lookup"><span data-stu-id="609d8-114">*pbType*</span></span>  
 <span data-ttu-id="609d8-115">参数的数据类型。</span><span class="sxs-lookup"><span data-stu-id="609d8-115">The data type of the parameter.</span></span>  
  
 <span data-ttu-id="609d8-116">pcbMaxLen\*\*</span><span class="sxs-lookup"><span data-stu-id="609d8-116">*pcbMaxLen*</span></span>  
 <span data-ttu-id="609d8-117">指向参数的最大长度的指针。</span><span class="sxs-lookup"><span data-stu-id="609d8-117">Pointer to the maximum length of the parameter.</span></span>  
  
 <span data-ttu-id="609d8-118">pcbActualLen\*\*</span><span class="sxs-lookup"><span data-stu-id="609d8-118">*pcbActualLen*</span></span>  
 <span data-ttu-id="609d8-119">指向参数的实际长度的指针。</span><span class="sxs-lookup"><span data-stu-id="609d8-119">Pointer to the actual length of the parameter.</span></span> <span data-ttu-id="609d8-120">如果 \*pfNull 设置为 FALSE，值为 0 (\*pcbActualLen == 0) 表示长度为零的数据\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="609d8-120">A value of 0 (\**pcbActualLen* == 0) signifies zero-length data if \**pfNull* is set to FALSE.</span></span>  
  
 <span data-ttu-id="609d8-121">pbData\*\*</span><span class="sxs-lookup"><span data-stu-id="609d8-121">*pbData*</span></span>  
 <span data-ttu-id="609d8-122">指向参数数据的缓冲区的指针。</span><span class="sxs-lookup"><span data-stu-id="609d8-122">Pointer to the buffer for parameter data.</span></span> <span data-ttu-id="609d8-123">如果 pbData 不为 NULL，扩展存储过程 API 将 \*pcbActualLen 字节的数据写入 \*pbData\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="609d8-123">If *pbData* is not NULL, the Extended Store Procedure API writes \**pcbActualLen* bytes of data to \**pbData*.</span></span> <span data-ttu-id="609d8-124">如果 pbData 为 NULL，不会有任何数据写入 \*pbData，但函数返回 \*pbType、\*pcbMaxLen、\*pcbActualLen 和 \*pfNull\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="609d8-124">If *pbData* is NULL, no data is written to \**pbData* but the function returns \**pbType*, \**pcbMaxLen*, \**pcbActualLen*, and \**pfNull*.</span></span> <span data-ttu-id="609d8-125">此缓冲区的内存必须由应用程序管理。</span><span class="sxs-lookup"><span data-stu-id="609d8-125">The memory for this buffer must be managed by the application.</span></span>  
  
 <span data-ttu-id="609d8-126">pfNull\*\*</span><span class="sxs-lookup"><span data-stu-id="609d8-126">*pfNull*</span></span>  
 <span data-ttu-id="609d8-127">指向 Null 标志的指针。</span><span class="sxs-lookup"><span data-stu-id="609d8-127">Pointer to a null flag.</span></span><span data-ttu-id="609d8-128">如果参数的值为 NULL， \*pfNull 设置为 TRUE\*\*。</span><span class="sxs-lookup"><span data-stu-id="609d8-128">\ **pfNull* is set to TRUE if the value of the parameter is NULL.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="609d8-129">返回</span><span class="sxs-lookup"><span data-stu-id="609d8-129">Returns</span></span>  
 <span data-ttu-id="609d8-130">如果成功获取参数信息，则返回 SUCCEED，否则返回 FAIL。</span><span class="sxs-lookup"><span data-stu-id="609d8-130">If the parameter information was successfully obtained, SUCCEED is returned; otherwise, FAIL.</span></span> <span data-ttu-id="609d8-131">如果没有当前远程存储过程并且没有第 n 个远程存储过程参数，将返回 FAIL\*\*。</span><span class="sxs-lookup"><span data-stu-id="609d8-131">FAIL is returned when there is no current remote stored procedure and when there is no *n*th remote stored procedure parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="609d8-132">备注</span><span class="sxs-lookup"><span data-stu-id="609d8-132">Remarks</span></span>  
 <span data-ttu-id="609d8-133">**安全说明** 应全面检查扩展存储过程的源代码，并在生产服务器中安装编译的 DLL 之前，应对这些 DLL 进行测试。</span><span class="sxs-lookup"><span data-stu-id="609d8-133">**Security Note** You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="609d8-134">有关安全检查和测试的信息，请访问此 [Microsoft 网站](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)。</span><span class="sxs-lookup"><span data-stu-id="609d8-134">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="609d8-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="609d8-135">See Also</span></span>  
 [<span data-ttu-id="609d8-136">扩展存储过程程序员参考</span><span class="sxs-lookup"><span data-stu-id="609d8-136">Extended Stored Procedures Programmer's Reference</span></span>](database-engine-extended-stored-procedures-reference.md)  
  
  
