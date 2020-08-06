---
title: srv_senddone（扩展存储过程 API）| Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_senddone
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_senddone
ms.assetid: 1fc4f1d5-56d4-43f6-b5e4-0c0cc295cba3
author: rothja
ms.author: jroth
ms.openlocfilehash: 877acdc1b666c7f4cbaab737590a1c55e474eb05
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694457"
---
# <a name="srv_senddone-extended-stored-procedure-api"></a><span data-ttu-id="12e42-102">srv_senddone（扩展存储过程 API）</span><span class="sxs-lookup"><span data-stu-id="12e42-102">srv_senddone (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]<span data-ttu-id="12e42-103">请改用 CLR 集成。</span><span class="sxs-lookup"><span data-stu-id="12e42-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="12e42-104">将结果完成消息发送到客户端。</span><span class="sxs-lookup"><span data-stu-id="12e42-104">Sends a result completion message to the client.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12e42-105">语法</span><span class="sxs-lookup"><span data-stu-id="12e42-105">Syntax</span></span>  
  
```  
  
int srv_senddone (  
SRV_PROC *  
srvproc  
,  
DBUSMALLINT   
status  
,  
DBUSMALLINT  
info  
,  
DBINT  
count   
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="12e42-106">参数</span><span class="sxs-lookup"><span data-stu-id="12e42-106">Arguments</span></span>  
 <span data-ttu-id="12e42-107">srvproc\*\*</span><span class="sxs-lookup"><span data-stu-id="12e42-107">*srvproc*</span></span>  
 <span data-ttu-id="12e42-108">指向作为特定客户端连接句柄（在这里为接收语言请求的句柄）的 SRV_PROC 结构的指针。</span><span class="sxs-lookup"><span data-stu-id="12e42-108">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection (in this case, the handle that received the language request).</span></span> <span data-ttu-id="12e42-109">该结构包含扩展存储过程 API 库用于管理应用程序和客户端之间的通信和数据的信息。</span><span class="sxs-lookup"><span data-stu-id="12e42-109">The structure contains information that the Extended Stored Procedure API library uses to manage communication and data between the application and the client.</span></span>  
  
 <span data-ttu-id="12e42-110">*status*</span><span class="sxs-lookup"><span data-stu-id="12e42-110">*status*</span></span>  
 <span data-ttu-id="12e42-111">各种 status 标志的 2 字节字段\*\*。</span><span class="sxs-lookup"><span data-stu-id="12e42-111">Is a 2-byte field for various *status* flags.</span></span> <span data-ttu-id="12e42-112">通过与 status 标志值一起使用 AND 和 OR 逻辑运算符，可以设置多个标志\*\*。</span><span class="sxs-lookup"><span data-stu-id="12e42-112">Multiple flags can be set by using the AND and OR logical operators with *status* flag values.</span></span> <span data-ttu-id="12e42-113">下表列出了可能的 status 标志\*\*。</span><span class="sxs-lookup"><span data-stu-id="12e42-113">The following table lists possible *status* flags.</span></span>  
  
|<span data-ttu-id="12e42-114">状态标志</span><span class="sxs-lookup"><span data-stu-id="12e42-114">Status flag</span></span>|<span data-ttu-id="12e42-115">说明</span><span class="sxs-lookup"><span data-stu-id="12e42-115">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="12e42-116">SRV_DONE_COUNT</span><span class="sxs-lookup"><span data-stu-id="12e42-116">SRV_DONE_COUNT</span></span>|<span data-ttu-id="12e42-117">count 参数包含有效计数\*\*。</span><span class="sxs-lookup"><span data-stu-id="12e42-117">The *count* parameter contains a valid count.</span></span>|  
|<span data-ttu-id="12e42-118">SRV_DONE_ERROR</span><span class="sxs-lookup"><span data-stu-id="12e42-118">SRV_DONE_ERROR</span></span>|<span data-ttu-id="12e42-119">当前客户端命令收到了错误。</span><span class="sxs-lookup"><span data-stu-id="12e42-119">The current client command received an error.</span></span>|  
  
 <span data-ttu-id="12e42-120">*info*</span><span class="sxs-lookup"><span data-stu-id="12e42-120">*info*</span></span>  
 <span data-ttu-id="12e42-121">保留的 2 字节字段。</span><span class="sxs-lookup"><span data-stu-id="12e42-121">Is a reserved, 2-byte field.</span></span> <span data-ttu-id="12e42-122">将该值设置为 0。</span><span class="sxs-lookup"><span data-stu-id="12e42-122">Set this value to 0.</span></span>  
  
 <span data-ttu-id="12e42-123">*计数*</span><span class="sxs-lookup"><span data-stu-id="12e42-123">*count*</span></span>  
 <span data-ttu-id="12e42-124">用于指示当前结果集的计数的 4 字节字段。</span><span class="sxs-lookup"><span data-stu-id="12e42-124">Is a 4-byte field used to indicate a count for the current result set.</span></span> <span data-ttu-id="12e42-125">如果在 status 字段中设置 SRV_DONE_COUNT 标志，则 count 将保存有效计数\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="12e42-125">If the SRV_DONE_COUNT flag is set in the *status* field, *count* holds a valid count.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="12e42-126">返回</span><span class="sxs-lookup"><span data-stu-id="12e42-126">Returns</span></span>  
 <span data-ttu-id="12e42-127">SUCCEED 或 FAIL</span><span class="sxs-lookup"><span data-stu-id="12e42-127">SUCCEED or FAIL</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="12e42-128">备注</span><span class="sxs-lookup"><span data-stu-id="12e42-128">Remarks</span></span>  
 <span data-ttu-id="12e42-129">客户端请求会导致服务器执行许多命令和返回许多结果集。</span><span class="sxs-lookup"><span data-stu-id="12e42-129">A client request can cause the server to execute a number of commands and to return a number of result sets.</span></span> <span data-ttu-id="12e42-130">对于每个结果集，srv_senddone 必须将结果完成消息返回到客户端\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="12e42-130">For each result set, **srv_senddone** must return a result completion message to the client.</span></span>  
  
 <span data-ttu-id="12e42-131">count 字段指示受命令影响的行数\*\*。</span><span class="sxs-lookup"><span data-stu-id="12e42-131">The *count* field indicates the number of rows affected by a command.</span></span> <span data-ttu-id="12e42-132">如果 count 字段包含计数，则应在 status 字段中设置 SRV_DONE_COUNT 标志\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="12e42-132">If the *count* field contains a count, the SRV_DONE_COUNT flag should be set in the *status* field.</span></span> <span data-ttu-id="12e42-133">客户端通过该设置可区分等于 0 的 count 值和未使用的 count 字段\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="12e42-133">This setting allows the client to distinguish between a *count* value of 0 and an unused *count* field.</span></span>  
  
 <span data-ttu-id="12e42-134">请勿从 SRV_CONNECT 处理程序调用 srv_senddone\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="12e42-134">Do not call **srv_senddone** from the SRV_CONNECT handler.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="12e42-135">应全面检查扩展存储过程的源代码，并在生产服务器中安装编译的 DLL 之前，对这些 DLL 进行测试。</span><span class="sxs-lookup"><span data-stu-id="12e42-135">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="12e42-136">有关安全检查和测试的信息，请访问此 [Microsoft 网站](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)。</span><span class="sxs-lookup"><span data-stu-id="12e42-136">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
  
