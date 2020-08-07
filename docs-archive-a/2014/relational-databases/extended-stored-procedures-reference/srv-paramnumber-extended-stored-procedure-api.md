---
title: srv_paramnumber（扩展存储过程 API）| Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_paramnumber
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_paramnumber
ms.assetid: d7a6dbff-71d9-4297-8a4f-bfd2876fe204
author: rothja
ms.author: jroth
ms.openlocfilehash: 1e621101c909ef251c40f38713e438d8e40d08a9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589087"
---
# <a name="srv_paramnumber-extended-stored-procedure-api"></a><span data-ttu-id="dcb5c-102">srv_paramnumber（扩展存储过程 API）</span><span class="sxs-lookup"><span data-stu-id="dcb5c-102">srv_paramnumber (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]<span data-ttu-id="dcb5c-103">请改用 CLR 集成。</span><span class="sxs-lookup"><span data-stu-id="dcb5c-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="dcb5c-104">返回远程存储过程调用参数的编号。</span><span class="sxs-lookup"><span data-stu-id="dcb5c-104">Returns the number of a remote stored procedure call parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dcb5c-105">语法</span><span class="sxs-lookup"><span data-stu-id="dcb5c-105">Syntax</span></span>  
  
```  
  
int srv_paramnumber (  
SRV_PROC *  
srvproc  
,  
DBCHAR *  
name  
,   
int  
namelen   
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="dcb5c-106">自变量</span><span class="sxs-lookup"><span data-stu-id="dcb5c-106">Arguments</span></span>  
 <span data-ttu-id="dcb5c-107">srvproc\*\*</span><span class="sxs-lookup"><span data-stu-id="dcb5c-107">*srvproc*</span></span>  
 <span data-ttu-id="dcb5c-108">指向作为特定客户端连接句柄（在这里为接收远程存储过程调用的句柄）的 SRV_PROC 结构的指针。</span><span class="sxs-lookup"><span data-stu-id="dcb5c-108">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection (in this case, the handle that received the remote stored procedure call).</span></span> <span data-ttu-id="dcb5c-109">该结构包含扩展存储过程 API 库用于管理应用程序和客户端之间的通信和数据的信息。</span><span class="sxs-lookup"><span data-stu-id="dcb5c-109">The structure contains information the Extended Stored Procedure API library uses to manage communication and data between the application and the client.</span></span>  
  
 <span data-ttu-id="dcb5c-110">name</span><span class="sxs-lookup"><span data-stu-id="dcb5c-110">*name*</span></span>  
 <span data-ttu-id="dcb5c-111">指向参数 name 的指针\*\*。</span><span class="sxs-lookup"><span data-stu-id="dcb5c-111">Is a pointer to the parameter *name*.</span></span>  
  
 <span data-ttu-id="dcb5c-112">namelen\*\*</span><span class="sxs-lookup"><span data-stu-id="dcb5c-112">*namelen*</span></span>  
 <span data-ttu-id="dcb5c-113">name 的长度\*\*。</span><span class="sxs-lookup"><span data-stu-id="dcb5c-113">Is the length of *name*.</span></span> <span data-ttu-id="dcb5c-114">如果 name 以 null 值终止，namelen 则设置为 SRV_NULLTERM\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="dcb5c-114">If *name* is null-terminated, set *namelen* to SRV_NULLTERM.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="dcb5c-115">返回</span><span class="sxs-lookup"><span data-stu-id="dcb5c-115">Returns</span></span>  
 <span data-ttu-id="dcb5c-116">命名参数的参数编号。</span><span class="sxs-lookup"><span data-stu-id="dcb5c-116">The parameter number of the named parameter.</span></span> <span data-ttu-id="dcb5c-117">第一个参数是 1。</span><span class="sxs-lookup"><span data-stu-id="dcb5c-117">The first parameter is 1.</span></span> <span data-ttu-id="dcb5c-118">如果没有参数命名为 name 或没有远程存储过程，则返回 0 并生成一条消息\*\*。</span><span class="sxs-lookup"><span data-stu-id="dcb5c-118">If there is no parameter named *name* or no remote stored procedure, 0 is returned and a message is generated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dcb5c-119">备注</span><span class="sxs-lookup"><span data-stu-id="dcb5c-119">Remarks</span></span>  
 <span data-ttu-id="dcb5c-120">使用参数调用远程存储过程时，可以按名称或位置（未命名）传递参数。</span><span class="sxs-lookup"><span data-stu-id="dcb5c-120">When a remote stored procedure call is made with parameters, the parameters can be passed either by name or by position (unnamed).</span></span> <span data-ttu-id="dcb5c-121">如果使用部分按名称传递，部分按位置传递的参数调用远程存储过程，则会发生错误。</span><span class="sxs-lookup"><span data-stu-id="dcb5c-121">If the remote stored procedure call is made with some parameters passed by name and some passed by position, an error occurs.</span></span> <span data-ttu-id="dcb5c-122">仍然会调用 SRV_RPC 处理程序，但是它看起来没有参数并且 srv_rpcparams 返回 0\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="dcb5c-122">The SRV_RPC handler is still called, but it appears as if there were no parameters, and **srv_rpcparams** returns 0.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="dcb5c-123">应全面检查扩展存储过程的源代码，并在生产服务器中安装编译的 DLL 之前，对这些 DLL 进行测试。</span><span class="sxs-lookup"><span data-stu-id="dcb5c-123">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="dcb5c-124">有关安全检查和测试的信息，请访问此 [Microsoft 网站](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)。</span><span class="sxs-lookup"><span data-stu-id="dcb5c-124">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcb5c-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="dcb5c-125">See Also</span></span>  
 [<span data-ttu-id="dcb5c-126">srv_rpcparams（扩展存储过程 API）</span><span class="sxs-lookup"><span data-stu-id="dcb5c-126">srv_rpcparams &#40;Extended Stored Procedure API&#41;</span></span>](srv-rpcparams-extended-stored-procedure-api.md)  
  
  
