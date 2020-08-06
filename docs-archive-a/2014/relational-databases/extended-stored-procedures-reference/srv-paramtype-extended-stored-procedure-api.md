---
title: srv_paramtype（扩展存储过程 API）| Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_paramtype
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_paramtype
ms.assetid: badc6d36-8a87-42b5-b28c-9c4f5ded8552
author: rothja
ms.author: jroth
ms.openlocfilehash: 0c4b4006f8214670e3bd2bddfbaabe917fb9d778
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579586"
---
# <a name="srv_paramtype-extended-stored-procedure-api"></a><span data-ttu-id="cf591-102">srv_paramtype（扩展存储过程 API）</span><span class="sxs-lookup"><span data-stu-id="cf591-102">srv_paramtype (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]<span data-ttu-id="cf591-103">请改用 CLR 集成。</span><span class="sxs-lookup"><span data-stu-id="cf591-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="cf591-104">返回远程存储过程调用参数的数据类型。</span><span class="sxs-lookup"><span data-stu-id="cf591-104">Returns the data type of a remote stored procedure call parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf591-105">语法</span><span class="sxs-lookup"><span data-stu-id="cf591-105">Syntax</span></span>  
  
```  
  
int srv_paramtype (  
SRV_PROC *  
srvproc  
,  
int  
n   
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="cf591-106">参数</span><span class="sxs-lookup"><span data-stu-id="cf591-106">Arguments</span></span>  
 <span data-ttu-id="cf591-107">srvproc\*\*</span><span class="sxs-lookup"><span data-stu-id="cf591-107">*srvproc*</span></span>  
 <span data-ttu-id="cf591-108">指向作为特定客户端连接句柄（在这里为接收远程存储过程调用的句柄）的 SRV_PROC 结构的指针。</span><span class="sxs-lookup"><span data-stu-id="cf591-108">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection (in this case, the handle that received the remote stored procedure call).</span></span> <span data-ttu-id="cf591-109">该结构包含扩展存储过程 API 库用于管理应用程序和客户端之间的通信和数据的信息。</span><span class="sxs-lookup"><span data-stu-id="cf591-109">The structure contains information the Extended Stored Procedure API library uses to manage communication and data between the application and the client.</span></span>  
  
 <span data-ttu-id="cf591-110">*n*</span><span class="sxs-lookup"><span data-stu-id="cf591-110">*n*</span></span>  
 <span data-ttu-id="cf591-111">指示参数的编号。</span><span class="sxs-lookup"><span data-stu-id="cf591-111">Indicates the number of the parameter.</span></span> <span data-ttu-id="cf591-112">第一个参数是 1。</span><span class="sxs-lookup"><span data-stu-id="cf591-112">The first parameter is 1.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="cf591-113">返回</span><span class="sxs-lookup"><span data-stu-id="cf591-113">Returns</span></span>  
 <span data-ttu-id="cf591-114">参数的数据类型的标记值。</span><span class="sxs-lookup"><span data-stu-id="cf591-114">A token value for the data type of the parameter.</span></span> <span data-ttu-id="cf591-115">有关数据类型的信息，请参阅[数据类型（扩展存储过程 API）](data-types-extended-stored-procedure-api.md)。</span><span class="sxs-lookup"><span data-stu-id="cf591-115">For information about data types, see [Data Types &#40;Extended Stored Procedure API&#41;](data-types-extended-stored-procedure-api.md).</span></span> <span data-ttu-id="cf591-116">如果没有第 n 个参数或没有任何远程存储过程，则返回 -1\*\*。</span><span class="sxs-lookup"><span data-stu-id="cf591-116">If there is no *n*th parameter or if there is no remote stored procedure, it returns - 1.</span></span>  
  
 <span data-ttu-id="cf591-117">如果参数是数据类型之一，则此函数返回以下值 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="cf591-117">This function returns the following values, if the parameter is one of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] data types.</span></span>  
  
|<span data-ttu-id="cf591-118">新数据类型</span><span class="sxs-lookup"><span data-stu-id="cf591-118">New data types</span></span>|<span data-ttu-id="cf591-119">返回值</span><span class="sxs-lookup"><span data-stu-id="cf591-119">Return value</span></span>|  
|--------------------|------------------|  
|`BITN`|<span data-ttu-id="cf591-120">SRVBIT</span><span class="sxs-lookup"><span data-stu-id="cf591-120">SRVBIT</span></span>|  
|`BIGVARCHAR`|<span data-ttu-id="cf591-121">VARCHAR</span><span class="sxs-lookup"><span data-stu-id="cf591-121">VARCHAR</span></span>|  
|`BIGCHAR`|<span data-ttu-id="cf591-122">CHAR</span><span class="sxs-lookup"><span data-stu-id="cf591-122">CHAR</span></span>|  
|`BIGBINARY`|<span data-ttu-id="cf591-123">BINARY</span><span class="sxs-lookup"><span data-stu-id="cf591-123">BINARY</span></span>|  
|`BIGVARBINARY`|<span data-ttu-id="cf591-124">VARBINARY</span><span class="sxs-lookup"><span data-stu-id="cf591-124">VARBINARY</span></span>|  
|`NCHAR`|<span data-ttu-id="cf591-125">CHAR</span><span class="sxs-lookup"><span data-stu-id="cf591-125">CHAR</span></span>|  
|`NVARCHAR`|<span data-ttu-id="cf591-126">VARCHAR</span><span class="sxs-lookup"><span data-stu-id="cf591-126">VARCHAR</span></span>|  
|`NTEXT`|<span data-ttu-id="cf591-127">-1</span><span class="sxs-lookup"><span data-stu-id="cf591-127">-1</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cf591-128">备注</span><span class="sxs-lookup"><span data-stu-id="cf591-128">Remarks</span></span>  
 <span data-ttu-id="cf591-129">使用参数调用远程存储过程时，可以按名称或位置（未命名）传递参数。</span><span class="sxs-lookup"><span data-stu-id="cf591-129">When a remote stored procedure call is made with parameters, the parameters can be passed either by name or by position (unnamed).</span></span> <span data-ttu-id="cf591-130">如果使用部分按名称传递，部分按位置传递的参数调用远程存储过程，则会发生错误。</span><span class="sxs-lookup"><span data-stu-id="cf591-130">If the remote stored procedure call is made with some parameters passed by name and some passed by position, an error occurs.</span></span> <span data-ttu-id="cf591-131">仍调用 SRV_RPC 处理程序，但它似乎没有参数并且**srv_rpcparams**返回0。</span><span class="sxs-lookup"><span data-stu-id="cf591-131">The SRV_RPC handler is still called, but it appears as if there were no parameters and **srv_rpcparams** returns 0.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="cf591-132">应全面检查扩展存储过程的源代码，并在生产服务器中安装编译的 DLL 之前，对这些 DLL 进行测试。</span><span class="sxs-lookup"><span data-stu-id="cf591-132">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="cf591-133">有关安全检查和测试的信息，请访问此 [Microsoft 网站](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)。</span><span class="sxs-lookup"><span data-stu-id="cf591-133">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf591-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cf591-134">See Also</span></span>  
 <span data-ttu-id="cf591-135">[扩展存储过程 API srv_paraminfo &#40;&#41;](srv-paraminfo-extended-stored-procedure-api.md) </span><span class="sxs-lookup"><span data-stu-id="cf591-135">[srv_paraminfo &#40;Extended Stored Procedure API&#41;](srv-paraminfo-extended-stored-procedure-api.md) </span></span>  
 [<span data-ttu-id="cf591-136">srv_rpcparams（扩展存储过程 API）</span><span class="sxs-lookup"><span data-stu-id="cf591-136">srv_rpcparams &#40;Extended Stored Procedure API&#41;</span></span>](srv-rpcparams-extended-stored-procedure-api.md)  
  
  
