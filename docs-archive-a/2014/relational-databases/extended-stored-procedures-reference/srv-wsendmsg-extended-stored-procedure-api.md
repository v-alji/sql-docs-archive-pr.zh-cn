---
title: srv_wsendmsg（扩展存储过程 API）| Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_wsendmsg
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_wsendmsg
ms.assetid: f2153076-32c9-4a52-8e1b-fc9618153543
author: rothja
ms.author: jroth
ms.openlocfilehash: 4cc915cce0befccb5c5af58e703c11b750af855b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693891"
---
# <a name="srv_wsendmsg-extended-stored-procedure-api"></a><span data-ttu-id="f66dd-102">srv_wsendmsg（扩展存储过程 API）</span><span class="sxs-lookup"><span data-stu-id="f66dd-102">srv_wsendmsg (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]<span data-ttu-id="f66dd-103">请改用 CLR 集成。</span><span class="sxs-lookup"><span data-stu-id="f66dd-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="f66dd-104">向客户端发送 Unicode 消息。</span><span class="sxs-lookup"><span data-stu-id="f66dd-104">Sends a Unicode message to the client.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f66dd-105">语法</span><span class="sxs-lookup"><span data-stu-id="f66dd-105">Syntax</span></span>  
  
```  
  
int srv_wsendmsg(SRV_PROC *   
srvproc  
, int   
msgnum  
, int   
severity  
, WCHAR *   
message  
, int   
msglen  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="f66dd-106">参数</span><span class="sxs-lookup"><span data-stu-id="f66dd-106">Arguments</span></span>  
 <span data-ttu-id="f66dd-107">srvproc\*\*</span><span class="sxs-lookup"><span data-stu-id="f66dd-107">*srvproc*</span></span>  
 <span data-ttu-id="f66dd-108">指向作为特定客户端连接句柄的 SRV_PROC 结构的指针。</span><span class="sxs-lookup"><span data-stu-id="f66dd-108">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection.</span></span> <span data-ttu-id="f66dd-109">该结构包含扩展存储过程 API 库用于管理应用程序和客户端之间的通信和数据的信息。</span><span class="sxs-lookup"><span data-stu-id="f66dd-109">The structure contains information the Extended Stored Procedure API library uses to manage communication and data between the application and the client.</span></span>  
  
 <span data-ttu-id="f66dd-110">*Msgnum*</span><span class="sxs-lookup"><span data-stu-id="f66dd-110">*Msgnum*</span></span>  
 <span data-ttu-id="f66dd-111">4 字节消息编号。</span><span class="sxs-lookup"><span data-stu-id="f66dd-111">Is a 4-byte message number.</span></span>  
  
 <span data-ttu-id="f66dd-112">*严重性*</span><span class="sxs-lookup"><span data-stu-id="f66dd-112">*Severity*</span></span>  
 <span data-ttu-id="f66dd-113">指定错误的严重性。</span><span class="sxs-lookup"><span data-stu-id="f66dd-113">Specifies the severity of the error.</span></span> <span data-ttu-id="f66dd-114">严重性小于或等于 10 将被视为信息性消息；否则为错误消息。</span><span class="sxs-lookup"><span data-stu-id="f66dd-114">A severity less than or equal to 10 is considered an informational message; otherwise, it is an error.</span></span>  
  
 <span data-ttu-id="f66dd-115">*message*</span><span class="sxs-lookup"><span data-stu-id="f66dd-115">*message*</span></span>  
 <span data-ttu-id="f66dd-116">指向要发送到客户端的 Unicode 字符串的指针。</span><span class="sxs-lookup"><span data-stu-id="f66dd-116">Is a pointer to a Unicode string to be sent to the client.</span></span>  
  
 <span data-ttu-id="f66dd-117">msglen\*\*</span><span class="sxs-lookup"><span data-stu-id="f66dd-117">*msglen*</span></span>  
 <span data-ttu-id="f66dd-118">指定消息的长度（以字符为单位）\*\*。</span><span class="sxs-lookup"><span data-stu-id="f66dd-118">Specifies the length, in characters, of *message*.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="f66dd-119">返回</span><span class="sxs-lookup"><span data-stu-id="f66dd-119">Returns</span></span>  
 <span data-ttu-id="f66dd-120">SUCCEED 或 FAIL。</span><span class="sxs-lookup"><span data-stu-id="f66dd-120">SUCCEED or FAIL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f66dd-121">备注</span><span class="sxs-lookup"><span data-stu-id="f66dd-121">Remarks</span></span>  
 <span data-ttu-id="f66dd-122">使用此函数以 Unicode 格式发送消息。</span><span class="sxs-lookup"><span data-stu-id="f66dd-122">Use this function to send messages in Unicode.</span></span> <span data-ttu-id="f66dd-123">这类似于 srv_sendmsg，但是它发送的消息是一个 WCHAR 字符串而不是 DBCHAR 类型的字符串\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f66dd-123">It is similar to **srv_sendmsg**, but the message it sends is a WCHAR string rather than type DBCHAR string.</span></span> <span data-ttu-id="f66dd-124">请注意，以字符而不是字节为单位报告消息长度，而且 msglen 绝不会等于 SRV_NULLTERM\*\*。</span><span class="sxs-lookup"><span data-stu-id="f66dd-124">Note that message length is reported in characters rather than bytes, and *msglen* will never be equal to SRV_NULLTERM.</span></span>  
  
 <span data-ttu-id="f66dd-125">该函数在以下情况下返回 FAIL：</span><span class="sxs-lookup"><span data-stu-id="f66dd-125">The function returns FAIL when</span></span>  
  
-   <span data-ttu-id="f66dd-126">给定的 msglen 不在 0-32242 范围内\*\*。</span><span class="sxs-lookup"><span data-stu-id="f66dd-126">The *msglen* given is not in the range of 0-32242.</span></span>  
  
-   <span data-ttu-id="f66dd-127">给定的 msglen 为 0，但消息指针为 NULL\*\*。</span><span class="sxs-lookup"><span data-stu-id="f66dd-127">The *msglen* given is 0 but the message pointer is NULL.</span></span>  
  
-   <span data-ttu-id="f66dd-128">通过网络发送错误消息时出错。</span><span class="sxs-lookup"><span data-stu-id="f66dd-128">There is error when sending the error message through network.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="f66dd-129">应全面检查扩展存储过程的源代码，并在生产服务器中安装编译的 DLL 之前，对这些 DLL 进行测试。</span><span class="sxs-lookup"><span data-stu-id="f66dd-129">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="f66dd-130">有关安全检查和测试的信息，请访问此 [Microsoft 网站](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)。</span><span class="sxs-lookup"><span data-stu-id="f66dd-130">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f66dd-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f66dd-131">See Also</span></span>  
 [<span data-ttu-id="f66dd-132">srv_sendmsg（扩展存储过程 API）</span><span class="sxs-lookup"><span data-stu-id="f66dd-132">srv_sendmsg &#40;Extended Stored Procedure API&#41;</span></span>](srv-sendmsg-extended-stored-procedure-api.md)  
  
  
