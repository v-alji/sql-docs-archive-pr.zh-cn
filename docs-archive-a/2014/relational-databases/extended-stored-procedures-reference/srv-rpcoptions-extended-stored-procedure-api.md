---
title: srv_rpcoptions（扩展存储过程 API）| Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_rpcoptions
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_rpcoptions
ms.assetid: dbcce5d1-d5a1-4379-9597-04e43af5923d
author: rothja
ms.author: jroth
ms.openlocfilehash: f5ebe4ab48721002e679ce149293b474a934e348
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694462"
---
# <a name="srv_rpcoptions-extended-stored-procedure-api"></a><span data-ttu-id="ad938-102">srv_rpcoptions（扩展存储过程 API）</span><span class="sxs-lookup"><span data-stu-id="ad938-102">srv_rpcoptions (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]<span data-ttu-id="ad938-103">请改用 CLR 集成。</span><span class="sxs-lookup"><span data-stu-id="ad938-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="ad938-104">返回当前远程存储过程的运行时选项。</span><span class="sxs-lookup"><span data-stu-id="ad938-104">Returns run-time options for the current remote stored procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad938-105">语法</span><span class="sxs-lookup"><span data-stu-id="ad938-105">Syntax</span></span>  
  
```  
  
DBUSMALLINT srv_rpcoptions ( SRV_PROC *  
srvproc   
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="ad938-106">参数</span><span class="sxs-lookup"><span data-stu-id="ad938-106">Arguments</span></span>  
 <span data-ttu-id="ad938-107">srvproc\*\*</span><span class="sxs-lookup"><span data-stu-id="ad938-107">*srvproc*</span></span>  
 <span data-ttu-id="ad938-108">指向作为特定客户端连接句柄（在这里为接收远程存储过程的句柄）的 SRV_PROC 结构的指针。</span><span class="sxs-lookup"><span data-stu-id="ad938-108">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection (in this case, the handle that received the remote stored procedure).</span></span> <span data-ttu-id="ad938-109">该结构包含扩展存储过程 API 库用于管理应用程序和客户端之间的通信和数据的信息。</span><span class="sxs-lookup"><span data-stu-id="ad938-109">The structure contains information the Extended Stored Procedure API library uses to manage communication and data between the application and the client.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="ad938-110">返回</span><span class="sxs-lookup"><span data-stu-id="ad938-110">Returns</span></span>  
 <span data-ttu-id="ad938-111">一个位图，它包含用逻辑 OR 联接的当前远程存储过程的运行时标志。</span><span class="sxs-lookup"><span data-stu-id="ad938-111">A bitmap that contains the run-time flags joined in a logical OR for the current remote stored procedure.</span></span> <span data-ttu-id="ad938-112">如果无当前远程存储过程，则返回 0 并生成一条消息。</span><span class="sxs-lookup"><span data-stu-id="ad938-112">If there is not a current remote stored procedure, 0 is returned and a message is generated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ad938-113">备注</span><span class="sxs-lookup"><span data-stu-id="ad938-113">Remarks</span></span>  
 <span data-ttu-id="ad938-114">下表说明每个运行时标志。</span><span class="sxs-lookup"><span data-stu-id="ad938-114">The following table describes each run-time flag.</span></span>  
  
|<span data-ttu-id="ad938-115">运行时标志</span><span class="sxs-lookup"><span data-stu-id="ad938-115">Run-time flag</span></span>|<span data-ttu-id="ad938-116">说明</span><span class="sxs-lookup"><span data-stu-id="ad938-116">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="ad938-117">SRV_NOMETADATA</span><span class="sxs-lookup"><span data-stu-id="ad938-117">SRV_NOMETADATA</span></span>|<span data-ttu-id="ad938-118">客户端已请求不带元数据信息的结果。</span><span class="sxs-lookup"><span data-stu-id="ad938-118">The client has requested results without metadata information.</span></span> <span data-ttu-id="ad938-119">仅当客户端与实例通信时才使用此标志 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="ad938-119">This flag is only used when the client is communicating with an instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="ad938-120">扩展存储过程 API 应用程序不能省略元数据信息。</span><span class="sxs-lookup"><span data-stu-id="ad938-120">An Extended Stored Procedure API application cannot omit metadata information.</span></span>|  
|<span data-ttu-id="ad938-121">SRV_RECOMPILE</span><span class="sxs-lookup"><span data-stu-id="ad938-121">SRV_RECOMPILE</span></span>|<span data-ttu-id="ad938-122">客户端已请求在执行远程存储过程前重新编译它。</span><span class="sxs-lookup"><span data-stu-id="ad938-122">The client has requested to recompile the remote stored procedure before executing it.</span></span> <span data-ttu-id="ad938-123">此标志可能不适用于扩展存储过程 API 应用程序。</span><span class="sxs-lookup"><span data-stu-id="ad938-123">This flag may not apply to an Extended Stored Procedure API application.</span></span>|  
  
> [!IMPORTANT]  
>  <span data-ttu-id="ad938-124">应全面检查扩展存储过程的源代码，并在生产服务器中安装编译的 DLL 之前，对这些 DLL 进行测试。</span><span class="sxs-lookup"><span data-stu-id="ad938-124">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="ad938-125">有关安全检查和测试的信息，请访问此 [Microsoft 网站](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)。</span><span class="sxs-lookup"><span data-stu-id="ad938-125">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
  
