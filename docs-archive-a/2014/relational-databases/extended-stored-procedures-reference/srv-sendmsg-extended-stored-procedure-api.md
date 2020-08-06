---
title: srv_sendmsg（扩展存储过程 API）| Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_sendmsg
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_sendmsg
ms.assetid: efcb50b9-f8ff-4121-bf67-05830171b928
author: rothja
ms.author: jroth
ms.openlocfilehash: 0821ad88f48313cfadea634a489def9b242a49f0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694455"
---
# <a name="srv_sendmsg-extended-stored-procedure-api"></a><span data-ttu-id="f0692-102">srv_sendmsg（扩展存储过程 API）</span><span class="sxs-lookup"><span data-stu-id="f0692-102">srv_sendmsg (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]<span data-ttu-id="f0692-103">请改用 CLR 集成。</span><span class="sxs-lookup"><span data-stu-id="f0692-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="f0692-104">向客户端发送消息。</span><span class="sxs-lookup"><span data-stu-id="f0692-104">Sends a message to the client.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0692-105">语法</span><span class="sxs-lookup"><span data-stu-id="f0692-105">Syntax</span></span>  
  
```  
  
int srv_sendmsg (  
SRV_PROC *  
srvproc  
,  
int  
msgtype  
,  
DBINT  
msgnum  
,  
DBTINYINT  
class  
,   
DBTINYINT  
state  
,  
DBCHAR *  
rpcname  
,  
int   
rpcnamelen  
,  
DBUSMALLINT  
linenum  
,  
DBCHAR *  
message  
,  
int  
msglen   
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="f0692-106">参数</span><span class="sxs-lookup"><span data-stu-id="f0692-106">Arguments</span></span>  
 <span data-ttu-id="f0692-107">srvproc\*\*</span><span class="sxs-lookup"><span data-stu-id="f0692-107">*srvproc*</span></span>  
 <span data-ttu-id="f0692-108">指向作为特定客户端连接句柄（在这里为接收语言请求的句柄）的 SRV_PROC 结构的指针。</span><span class="sxs-lookup"><span data-stu-id="f0692-108">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection (in this case, the handle that received the language request).</span></span> <span data-ttu-id="f0692-109">该结构包含扩展存储过程 API 库用于管理应用程序和客户端之间的通信和数据的信息。</span><span class="sxs-lookup"><span data-stu-id="f0692-109">The structure contains information that the Extended Stored Procedure API library uses to manage communication and data between the application and the client.</span></span>  
  
 <span data-ttu-id="f0692-110">msgtype\*\*</span><span class="sxs-lookup"><span data-stu-id="f0692-110">*msgtype*</span></span>  
 <span data-ttu-id="f0692-111">SRV_MSG_INFO 或 SRV_MSG_ERROR，具体取决于服务器发送的是信息性消息还是错误消息。</span><span class="sxs-lookup"><span data-stu-id="f0692-111">Is either SRV_MSG_INFO or SRV_MSG_ERROR, depending on whether the server is sending an informational or error message.</span></span>  
  
 <span data-ttu-id="f0692-112">msgnum\*\*</span><span class="sxs-lookup"><span data-stu-id="f0692-112">*msgnum*</span></span>  
 <span data-ttu-id="f0692-113">4 字节消息编号。</span><span class="sxs-lookup"><span data-stu-id="f0692-113">Is a 4-byte message number.</span></span>  
  
 <span data-ttu-id="f0692-114">*class*</span><span class="sxs-lookup"><span data-stu-id="f0692-114">*class*</span></span>  
 <span data-ttu-id="f0692-115">指定错误严重性。</span><span class="sxs-lookup"><span data-stu-id="f0692-115">Specifies the error severity.</span></span> <span data-ttu-id="f0692-116">严重性小于或等于 10 将被视为信息性消息。</span><span class="sxs-lookup"><span data-stu-id="f0692-116">A severity less than or equal to 10 is considered an informational message.</span></span>  
  
 <span data-ttu-id="f0692-117">State</span><span class="sxs-lookup"><span data-stu-id="f0692-117">*state*</span></span>  
 <span data-ttu-id="f0692-118">提供当前消息的错误状态编号。</span><span class="sxs-lookup"><span data-stu-id="f0692-118">Provides the error state number for the current message.</span></span> <span data-ttu-id="f0692-119">错误状态编号提供有关错误上下文的信息。</span><span class="sxs-lookup"><span data-stu-id="f0692-119">The error state number provides information about the context of the error.</span></span> <span data-ttu-id="f0692-120">有效的状态编号介于 0 到 255 之间。</span><span class="sxs-lookup"><span data-stu-id="f0692-120">Valid state numbers are from 0 through 255.</span></span>  
  
 <span data-ttu-id="f0692-121">rpcname\*\*</span><span class="sxs-lookup"><span data-stu-id="f0692-121">*rpcname*</span></span>  
 <span data-ttu-id="f0692-122">当前不受支持。</span><span class="sxs-lookup"><span data-stu-id="f0692-122">Is currently not supported.</span></span>  
  
 <span data-ttu-id="f0692-123">rpcnamelen\*\*</span><span class="sxs-lookup"><span data-stu-id="f0692-123">*rpcnamelen*</span></span>  
 <span data-ttu-id="f0692-124">当前不受支持。</span><span class="sxs-lookup"><span data-stu-id="f0692-124">Is currently not supported.</span></span>  
  
 <span data-ttu-id="f0692-125">*linenum*</span><span class="sxs-lookup"><span data-stu-id="f0692-125">*linenum*</span></span>  
 <span data-ttu-id="f0692-126">消息应用到的语言命令批处理中的行号。</span><span class="sxs-lookup"><span data-stu-id="f0692-126">Is the line number in the language command batch where the message applies.</span></span> <span data-ttu-id="f0692-127">行号从 1 开始。</span><span class="sxs-lookup"><span data-stu-id="f0692-127">Line numbers start at 1.</span></span> <span data-ttu-id="f0692-128">如果 linenum 不适用于消息，则设置为 0\*\*。</span><span class="sxs-lookup"><span data-stu-id="f0692-128">If *linenum* does not apply to the message, set to 0.</span></span>  
  
 <span data-ttu-id="f0692-129">*message*</span><span class="sxs-lookup"><span data-stu-id="f0692-129">*message*</span></span>  
 <span data-ttu-id="f0692-130">指向要发送到客户端的字符串的指针。</span><span class="sxs-lookup"><span data-stu-id="f0692-130">Is a pointer to the character string to be sent to the client.</span></span>  
  
 <span data-ttu-id="f0692-131">msglen\*\*</span><span class="sxs-lookup"><span data-stu-id="f0692-131">*msglen*</span></span>  
 <span data-ttu-id="f0692-132">指定消息的长度（以字节为单位）\*\*。</span><span class="sxs-lookup"><span data-stu-id="f0692-132">Specifies the length, in bytes, of *message*.</span></span> <span data-ttu-id="f0692-133">如果消息以 null 值结束，则将 msglen 设置为 SRV_NULLTERM\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f0692-133">If *message* is null-terminated, set *msglen* to SRV_NULLTERM.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="f0692-134">返回</span><span class="sxs-lookup"><span data-stu-id="f0692-134">Returns</span></span>  
 <span data-ttu-id="f0692-135">SUCCEED 或 FAIL</span><span class="sxs-lookup"><span data-stu-id="f0692-135">SUCCEED or FAIL</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f0692-136">备注</span><span class="sxs-lookup"><span data-stu-id="f0692-136">Remarks</span></span>  
 <span data-ttu-id="f0692-137">此函数向客户端发送错误或信息性消息。</span><span class="sxs-lookup"><span data-stu-id="f0692-137">This function sends error or informational messages to the client.</span></span> <span data-ttu-id="f0692-138">每一要发送的消息都调用一次该函数。</span><span class="sxs-lookup"><span data-stu-id="f0692-138">It is called once for each message to be sent.</span></span>  
  
 <span data-ttu-id="f0692-139">可以在使用 srv_sendrow 发送所有行（如果有）之前或之后，使用 srv_sendmsg 以任意顺序向客户端发送消息\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f0692-139">Messages can be sent to the client with **srv_sendmsg** in any order before or after all rows (if any) have been sent with **srv_sendrow**.</span></span> <span data-ttu-id="f0692-140">在使用 srv_senddone 发送完成状态之前，所有消息（如果有）都必须发送到客户端\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f0692-140">All messages, if any, must be sent to the client before the completion status is sent with **srv_senddone**.</span></span>  
  
 <span data-ttu-id="f0692-141">如果通过 Unicode 发送消息，请使用 srv_wsendmsg 而不是 srv_sendmsg\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f0692-141">To send messages in Unicode, use **srv_wsendmsg** rather than **srv_sendmsg**.</span></span>  
  
 <span data-ttu-id="f0692-142">有关详细信息，请参阅 [Unicode 数据和服务器代码页](../extended-stored-procedures-programming/unicode-data-and-server-code-pages.md)。</span><span class="sxs-lookup"><span data-stu-id="f0692-142">For more information see [Unicode Data and Server Code Pages](../extended-stored-procedures-programming/unicode-data-and-server-code-pages.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="f0692-143">应全面检查扩展存储过程的源代码，并在生产服务器中安装编译的 DLL 之前，对这些 DLL 进行测试。</span><span class="sxs-lookup"><span data-stu-id="f0692-143">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="f0692-144">有关安全检查和测试的信息，请访问此 [Microsoft 网站](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)。</span><span class="sxs-lookup"><span data-stu-id="f0692-144">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
  
