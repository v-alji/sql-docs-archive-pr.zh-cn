---
title: srv_paramname（扩展存储过程 API）| Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_paramname
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_paramname
ms.assetid: 1a53d707-7b06-49cc-a0df-ac727cfe953f
author: rothja
ms.author: jroth
ms.openlocfilehash: 2227ac3d46efe7d09abc05964248229f3533d42d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693900"
---
# <a name="srv_paramname-extended-stored-procedure-api"></a><span data-ttu-id="31459-102">srv_paramname（扩展存储过程 API）</span><span class="sxs-lookup"><span data-stu-id="31459-102">srv_paramname (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]<span data-ttu-id="31459-103">请改用 CLR 集成。</span><span class="sxs-lookup"><span data-stu-id="31459-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="31459-104">返回远程存储过程调用参数的名称。</span><span class="sxs-lookup"><span data-stu-id="31459-104">Returns the name of a remote stored procedure call parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31459-105">语法</span><span class="sxs-lookup"><span data-stu-id="31459-105">Syntax</span></span>  
  
```  
  
DBCHAR * srv_paramname (  
SRV_PROC * srvproc,intn, int *len );  
```  
  
## <a name="arguments"></a><span data-ttu-id="31459-106">参数</span><span class="sxs-lookup"><span data-stu-id="31459-106">Arguments</span></span>  
 <span data-ttu-id="31459-107">srvproc\*\*</span><span class="sxs-lookup"><span data-stu-id="31459-107">*srvproc*</span></span>  
 <span data-ttu-id="31459-108">指向作为特定客户端连接句柄（在这里为接收远程存储过程调用的句柄）的 SRV_PROC 结构的指针。</span><span class="sxs-lookup"><span data-stu-id="31459-108">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection (in this case, the handle that received the remote stored procedure call).</span></span> <span data-ttu-id="31459-109">该结构包含扩展存储过程 API 库用于管理应用程序和客户端之间的通信和数据的信息。</span><span class="sxs-lookup"><span data-stu-id="31459-109">The structure contains information the Extended Stored Procedure API library uses to manage communication and data between the application and the client.</span></span>  
  
 <span data-ttu-id="31459-110">*n*</span><span class="sxs-lookup"><span data-stu-id="31459-110">*n*</span></span>  
 <span data-ttu-id="31459-111">指示参数的编号。</span><span class="sxs-lookup"><span data-stu-id="31459-111">Indicates the number of the parameter.</span></span> <span data-ttu-id="31459-112">第一个参数是 1。</span><span class="sxs-lookup"><span data-stu-id="31459-112">The first parameter is 1.</span></span>  
  
 <span data-ttu-id="31459-113">*长度*</span><span class="sxs-lookup"><span data-stu-id="31459-113">*len*</span></span>  
 <span data-ttu-id="31459-114">提供指向 `int` 变量的指针，该变量包含以字节为单位的参数名称的长度。</span><span class="sxs-lookup"><span data-stu-id="31459-114">Provides a pointer to an `int` variable that contains the length, in bytes, of the parameter name.</span></span> <span data-ttu-id="31459-115">如果 len 为 NULL，则不返回远程存储过程参数名称的长度\*\*。</span><span class="sxs-lookup"><span data-stu-id="31459-115">If *len* is NULL, the length of the remote stored procedure parameter name is not returned.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="31459-116">返回</span><span class="sxs-lookup"><span data-stu-id="31459-116">Returns</span></span>  
 <span data-ttu-id="31459-117">指向包含参数名称的 Null 值结束字符串的指针。</span><span class="sxs-lookup"><span data-stu-id="31459-117">A pointer to a null-terminated character string that contains the parameter name.</span></span> <span data-ttu-id="31459-118">参数名称的长度存储在 len 中\*\*。</span><span class="sxs-lookup"><span data-stu-id="31459-118">The length of the parameter name is stored in *len*.</span></span> <span data-ttu-id="31459-119">如果没有第 n 个参数或没有远程存储过程，则返回 NULL，len 会设置为 -1，并且会发送信息性错误消息\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="31459-119">If there is no *n*th parameter or no remote stored procedure, it returns NULL, *len* is set to -1, and an informational error message is sent.</span></span> <span data-ttu-id="31459-120">如果参数名称为 NULL，len 则将设置为 0，并且返回以 null 值终止的空字符串\*\*。</span><span class="sxs-lookup"><span data-stu-id="31459-120">If the parameter name is NULL, *len* is set to 0 and a null-terminated empty string is returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="31459-121">备注</span><span class="sxs-lookup"><span data-stu-id="31459-121">Remarks</span></span>  
 <span data-ttu-id="31459-122">该函数获取远程存储过程调用参数的名称。</span><span class="sxs-lookup"><span data-stu-id="31459-122">This function gets the name of a remote stored procedure call parameter.</span></span> <span data-ttu-id="31459-123">使用参数调用远程存储过程时，可以按名称或位置（未命名）传递参数。</span><span class="sxs-lookup"><span data-stu-id="31459-123">When a remote stored procedure call is made with parameters, the parameters can be passed either by name or by position (unnamed).</span></span> <span data-ttu-id="31459-124">如果使用部分按名称传递，部分按位置传递的参数调用远程存储过程，则会发生错误。</span><span class="sxs-lookup"><span data-stu-id="31459-124">If the remote stored procedure call is made with some parameters passed by name and some passed by position, an error occurs.</span></span> <span data-ttu-id="31459-125">仍然会调用 SRV_RPC 处理程序，但是它看起来没有参数并且 srv_rpcparams 返回 0\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="31459-125">The SRV_RPC handler is still called, but it appears as if there were no parameters, and **srv_rpcparams** returns 0.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="31459-126">应全面检查扩展存储过程的源代码，并在生产服务器中安装编译的 DLL 之前，对这些 DLL 进行测试。</span><span class="sxs-lookup"><span data-stu-id="31459-126">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="31459-127">有关安全检查和测试的信息，请访问此 [Microsoft 网站](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)。</span><span class="sxs-lookup"><span data-stu-id="31459-127">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31459-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="31459-128">See Also</span></span>  
 [<span data-ttu-id="31459-129">srv_rpcparams（扩展存储过程 API）</span><span class="sxs-lookup"><span data-stu-id="31459-129">srv_rpcparams &#40;Extended Stored Procedure API&#41;</span></span>](srv-rpcparams-extended-stored-procedure-api.md)  
  
  
