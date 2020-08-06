---
title: srv_rpcnumber（扩展存储过程 API）| Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_rpcnumber
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_rpcnumber
ms.assetid: 3094085e-fe9e-423d-bf87-7852352c2d26
author: rothja
ms.author: jroth
ms.openlocfilehash: 25f30f8288125cf64d6b10a867d6af03c0f8ee91
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693895"
---
# <a name="srv_rpcnumber-extended-stored-procedure-api"></a><span data-ttu-id="60762-102">srv_rpcnumber（扩展存储过程 API）</span><span class="sxs-lookup"><span data-stu-id="60762-102">srv_rpcnumber (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]<span data-ttu-id="60762-103">请改用 CLR 集成。</span><span class="sxs-lookup"><span data-stu-id="60762-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="60762-104">返回当前远程存储过程调用的编号组件。</span><span class="sxs-lookup"><span data-stu-id="60762-104">Returns the number component for the current remote stored procedure call.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60762-105">语法</span><span class="sxs-lookup"><span data-stu-id="60762-105">Syntax</span></span>  
  
```  
  
int srv_rpcnumber ( SRV_PROC *  
srvproc   
)  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="60762-106">参数</span><span class="sxs-lookup"><span data-stu-id="60762-106">Arguments</span></span>  
 <span data-ttu-id="60762-107">srvproc\*\*</span><span class="sxs-lookup"><span data-stu-id="60762-107">*srvproc*</span></span>  
 <span data-ttu-id="60762-108">指向作为特定客户端连接句柄（在这里为接收远程存储过程的句柄）的 SRV_PROC 结构的指针。</span><span class="sxs-lookup"><span data-stu-id="60762-108">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection (in this case, the handle that received the remote stored procedure).</span></span> <span data-ttu-id="60762-109">该结构包含扩展存储过程 API 库用于管理应用程序和客户端之间的通信和数据的信息。</span><span class="sxs-lookup"><span data-stu-id="60762-109">The structure contains information that the Extended Stored Procedure API library uses to manage communication and data between the application and the client.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="60762-110">返回</span><span class="sxs-lookup"><span data-stu-id="60762-110">Returns</span></span>  
 <span data-ttu-id="60762-111">当前远程存储过程的编号组件。</span><span class="sxs-lookup"><span data-stu-id="60762-111">The number component for the current remote stored procedure.</span></span> <span data-ttu-id="60762-112">如果客户端在运行远程存储过程时未使用编号组件，或者如果当前没有远程存储过程，则返回 - 1。</span><span class="sxs-lookup"><span data-stu-id="60762-112">If the client does not use a number component when running the remote stored procedure or if there is no current remote stored procedure, it returns - 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="60762-113">备注</span><span class="sxs-lookup"><span data-stu-id="60762-113">Remarks</span></span>  
 <span data-ttu-id="60762-114">此函数只返回远程存储过程的编号组件。</span><span class="sxs-lookup"><span data-stu-id="60762-114">This function returns only the number component of the remote stored procedure.</span></span> <span data-ttu-id="60762-115">不包括所有者、远程存储过程名称和数据库名称的可选说明符。</span><span class="sxs-lookup"><span data-stu-id="60762-115">It does not include the optional specifiers for owner, remote stored procedure name, and database name.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="60762-116">应全面检查扩展存储过程的源代码，并在生产服务器中安装编译的 DLL 之前，对这些 DLL 进行测试。</span><span class="sxs-lookup"><span data-stu-id="60762-116">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="60762-117">有关安全检查和测试的信息，请访问此 [Microsoft 网站](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)。</span><span class="sxs-lookup"><span data-stu-id="60762-117">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
  
