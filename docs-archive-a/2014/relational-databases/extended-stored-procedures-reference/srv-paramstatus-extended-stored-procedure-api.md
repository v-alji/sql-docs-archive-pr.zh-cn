---
title: srv_paramstatus（扩展存储过程 API）| Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_paramstatus
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_paramstatus
ms.assetid: 86cecd45-0b09-42e9-8152-32a12a1c2b7a
author: rothja
ms.author: jroth
ms.openlocfilehash: d89d4ccbb6a97ff47669ad4ed9c0b4c22ac934eb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682830"
---
# <a name="srv_paramstatus-extended-stored-procedure-api"></a><span data-ttu-id="8e9b7-102">srv_paramstatus（扩展存储过程 API）</span><span class="sxs-lookup"><span data-stu-id="8e9b7-102">srv_paramstatus (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]<span data-ttu-id="8e9b7-103">请改用 CLR 集成。</span><span class="sxs-lookup"><span data-stu-id="8e9b7-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="8e9b7-104">返回特定远程存储过程调用参数的状态。</span><span class="sxs-lookup"><span data-stu-id="8e9b7-104">Returns the status of a particular remote stored procedure call parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e9b7-105">语法</span><span class="sxs-lookup"><span data-stu-id="8e9b7-105">Syntax</span></span>  
  
```  
  
int srv_paramstatus (  
SRV_PROC *  
srvproc  
,  
int  
n   
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="8e9b7-106">参数</span><span class="sxs-lookup"><span data-stu-id="8e9b7-106">Arguments</span></span>  
 <span data-ttu-id="8e9b7-107">srvproc\*\*</span><span class="sxs-lookup"><span data-stu-id="8e9b7-107">*srvproc*</span></span>  
 <span data-ttu-id="8e9b7-108">指向作为特定客户端连接句柄（在这里为接收远程存储过程调用的句柄）的 SRV_PROC 结构的指针。</span><span class="sxs-lookup"><span data-stu-id="8e9b7-108">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection (in this case, the handle that received the remote stored procedure call).</span></span> <span data-ttu-id="8e9b7-109">该结构包含扩展存储过程 API 库用于管理应用程序和客户端之间的通信和数据的信息。</span><span class="sxs-lookup"><span data-stu-id="8e9b7-109">The structure contains information the Extended Stored Procedure API library uses to manage communication and data between the application and the client.</span></span>  
  
 <span data-ttu-id="8e9b7-110">*n*</span><span class="sxs-lookup"><span data-stu-id="8e9b7-110">*n*</span></span>  
 <span data-ttu-id="8e9b7-111">指示参数的编号。</span><span class="sxs-lookup"><span data-stu-id="8e9b7-111">Indicates the number of the parameter.</span></span> <span data-ttu-id="8e9b7-112">第一个参数的编号为 1。</span><span class="sxs-lookup"><span data-stu-id="8e9b7-112">The first parameter is number 1.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="8e9b7-113">返回</span><span class="sxs-lookup"><span data-stu-id="8e9b7-113">Returns</span></span>  
 <span data-ttu-id="8e9b7-114">包含参数的状态标志的 `int`。</span><span class="sxs-lookup"><span data-stu-id="8e9b7-114">An `int` that contains status flags for the parameter.</span></span> <span data-ttu-id="8e9b7-115">目前，只有一个标志：如果位 0 设置为 1，则参数为一个返回参数。</span><span class="sxs-lookup"><span data-stu-id="8e9b7-115">Currently, there is only one flag: If bit 0 is set to 1, the parameter is a return parameter.</span></span> <span data-ttu-id="8e9b7-116">如果没有第 n 个参数或没有任何远程存储过程，则返回 -1\*\*。</span><span class="sxs-lookup"><span data-stu-id="8e9b7-116">If there is no *n*th parameter or if there is no remote stored procedure, it returns -1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8e9b7-117">备注</span><span class="sxs-lookup"><span data-stu-id="8e9b7-117">Remarks</span></span>  
 <span data-ttu-id="8e9b7-118">此例程返回远程存储过程调用参数的状态标志。</span><span class="sxs-lookup"><span data-stu-id="8e9b7-118">This routine returns the status flags for a remote stored procedure call parameter.</span></span>  
  
 <span data-ttu-id="8e9b7-119">参数包含通过远程存储过程在客户端和应用程序之间传递的数据。</span><span class="sxs-lookup"><span data-stu-id="8e9b7-119">Parameters contain data passed between clients and the application with remote stored procedures.</span></span> <span data-ttu-id="8e9b7-120">客户端可以指定某些参数作为返回参数。</span><span class="sxs-lookup"><span data-stu-id="8e9b7-120">The client can specify certain parameters as return parameters.</span></span> <span data-ttu-id="8e9b7-121">这些返回参数可包含应用程序传递回客户端的值。</span><span class="sxs-lookup"><span data-stu-id="8e9b7-121">These return parameters can contain values that the application passes back to the client.</span></span>  
  
 <span data-ttu-id="8e9b7-122">目前，只有一个状态标志，该标志指示参数是否为一个返回参数。</span><span class="sxs-lookup"><span data-stu-id="8e9b7-122">Currently, the only status flag is one that indicates whether the parameter is a return parameter.</span></span>  
  
 <span data-ttu-id="8e9b7-123">使用参数调用远程存储过程时，可以按名称或位置（未命名）传递参数。</span><span class="sxs-lookup"><span data-stu-id="8e9b7-123">When a remote stored procedure call is made with parameters, the parameters can be passed either by name or by position (unnamed).</span></span> <span data-ttu-id="8e9b7-124">如果使用部分按名称传递，部分按位置传递的参数调用远程存储过程，则会发生错误。</span><span class="sxs-lookup"><span data-stu-id="8e9b7-124">If the remote stored procedure call is made with some parameters passed by name and some passed by position, an error occurs.</span></span> <span data-ttu-id="8e9b7-125">如果发生错误，仍然会调用 SRV_RPC 处理程序，但它似乎没有参数， **srv_rpcparams**返回0。</span><span class="sxs-lookup"><span data-stu-id="8e9b7-125">If an error occurs, the SRV_RPC handler is still called, but it appears as if there were no parameters, and **srv_rpcparams** returns 0.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="8e9b7-126">应全面检查扩展存储过程的源代码，并在生产服务器中安装编译的 DLL 之前，对这些 DLL 进行测试。</span><span class="sxs-lookup"><span data-stu-id="8e9b7-126">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="8e9b7-127">有关安全检查和测试的信息，请访问此 [Microsoft 网站](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)。</span><span class="sxs-lookup"><span data-stu-id="8e9b7-127">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e9b7-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8e9b7-128">See Also</span></span>  
 [<span data-ttu-id="8e9b7-129">srv_rpcparams（扩展存储过程 API）</span><span class="sxs-lookup"><span data-stu-id="8e9b7-129">srv_rpcparams &#40;Extended Stored Procedure API&#41;</span></span>](srv-rpcparams-extended-stored-procedure-api.md)  
  
  
