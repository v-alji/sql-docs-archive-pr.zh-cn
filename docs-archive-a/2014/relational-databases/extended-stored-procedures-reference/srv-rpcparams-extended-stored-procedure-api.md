---
title: srv_rpcparams（扩展存储过程 API）| Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_rpcparams
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_rpcparams
ms.assetid: 96a5e6f6-d320-4623-b96e-0a856e3abebb
author: rothja
ms.author: jroth
ms.openlocfilehash: 443b9ea8a67341afdb92f0c384148c8b1b42f752
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694458"
---
# <a name="srv_rpcparams-extended-stored-procedure-api"></a><span data-ttu-id="65d67-102">srv_rpcparams（扩展存储过程 API）</span><span class="sxs-lookup"><span data-stu-id="65d67-102">srv_rpcparams (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]<span data-ttu-id="65d67-103">请改用 CLR 集成。</span><span class="sxs-lookup"><span data-stu-id="65d67-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="65d67-104">返回当前远程存储过程的参数个数。</span><span class="sxs-lookup"><span data-stu-id="65d67-104">Returns the number of parameters for the current remote stored procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65d67-105">语法</span><span class="sxs-lookup"><span data-stu-id="65d67-105">Syntax</span></span>  
  
```  
  
int srv_rpcparams ( SRV_PROC *  
srvproc   
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="65d67-106">参数</span><span class="sxs-lookup"><span data-stu-id="65d67-106">Arguments</span></span>  
 <span data-ttu-id="65d67-107">srvproc\*\*</span><span class="sxs-lookup"><span data-stu-id="65d67-107">*srvproc*</span></span>  
 <span data-ttu-id="65d67-108">指向作为特定客户端连接句柄（在这里为接收远程存储过程的句柄）的 SRV_PROC 结构的指针。</span><span class="sxs-lookup"><span data-stu-id="65d67-108">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection (in this case, the handle that received the remote stored procedure).</span></span> <span data-ttu-id="65d67-109">该结构包含扩展存储过程 API 库用于管理应用程序和客户端之间的通信和数据的信息。</span><span class="sxs-lookup"><span data-stu-id="65d67-109">The structure contains information that the Extended Stored Procedure API library uses to manage communication and data between the application and the client.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="65d67-110">返回</span><span class="sxs-lookup"><span data-stu-id="65d67-110">Returns</span></span>  
 <span data-ttu-id="65d67-111">远程存储过程中的参数个数。</span><span class="sxs-lookup"><span data-stu-id="65d67-111">The number of parameters in the remote stored procedure.</span></span> <span data-ttu-id="65d67-112">如果远程存储过程中没有参数，或没有当前远程存储过程，则返回 -1，并发生信息错误。</span><span class="sxs-lookup"><span data-stu-id="65d67-112">If there are no parameters in the remote stored procedure or if there is not a current remote stored procedure, -1 is returned and an information error occurs.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="65d67-113">备注</span><span class="sxs-lookup"><span data-stu-id="65d67-113">Remarks</span></span>  
 <span data-ttu-id="65d67-114">该函数返回当前远程存储过程中的参数个数。</span><span class="sxs-lookup"><span data-stu-id="65d67-114">This function returns the number of parameters in the current remote stored procedure.</span></span> <span data-ttu-id="65d67-115">通常是从远程存储过程调用该函数。</span><span class="sxs-lookup"><span data-stu-id="65d67-115">It is usually called from the remote stored procedure.</span></span>  
  
 <span data-ttu-id="65d67-116">使用参数调用远程存储过程时，可以按名称或位置（未命名）传递参数。</span><span class="sxs-lookup"><span data-stu-id="65d67-116">When a remote stored procedure call is made with parameters, the parameters can be passed either by name or by position (unnamed).</span></span> <span data-ttu-id="65d67-117">如果进行远程存储过程调用时，一些参数按名称传递而另一些按位置传递，则会出现错误。</span><span class="sxs-lookup"><span data-stu-id="65d67-117">If the remote stored procedure call was made with some parameters passed by name and some passed by position, an error occurs.</span></span> <span data-ttu-id="65d67-118">发生该错误时，将调用远程存储过程处理程序，但它不接收参数，并且 srv_rpcparams 返回 0\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="65d67-118">When this error occurs, the remote stored procedure handler is called, but it does not receive the parameters and **srv_rpcparams** returns 0.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="65d67-119">应全面检查扩展存储过程的源代码，并在生产服务器中安装编译的 DLL 之前，对这些 DLL 进行测试。</span><span class="sxs-lookup"><span data-stu-id="65d67-119">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="65d67-120">有关安全检查和测试的信息，请访问此 [Microsoft 网站](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)。</span><span class="sxs-lookup"><span data-stu-id="65d67-120">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
  
