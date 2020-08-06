---
title: srv_sendrow（扩展存储过程 API）| Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_sendrow
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_sendrow
ms.assetid: a08f608a-10e6-4bff-9b48-0d02e8026cdb
author: rothja
ms.author: jroth
ms.openlocfilehash: df40348b8792a70f84719abfb42152fda9487e6b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694454"
---
# <a name="srv_sendrow-extended-stored-procedure-api"></a><span data-ttu-id="64059-102">srv_sendrow（扩展存储过程 API）</span><span class="sxs-lookup"><span data-stu-id="64059-102">srv_sendrow (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]<span data-ttu-id="64059-103">请改用 CLR 集成。</span><span class="sxs-lookup"><span data-stu-id="64059-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="64059-104">将一行数据传送到客户端。</span><span class="sxs-lookup"><span data-stu-id="64059-104">Transmits a row of data to the client.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64059-105">语法</span><span class="sxs-lookup"><span data-stu-id="64059-105">Syntax</span></span>  
  
```  
  
int srv_sendrow ( SRV_PROC *  
srvproc   
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="64059-106">参数</span><span class="sxs-lookup"><span data-stu-id="64059-106">Arguments</span></span>  
 <span data-ttu-id="64059-107">srvproc\*\*</span><span class="sxs-lookup"><span data-stu-id="64059-107">*srvproc*</span></span>  
 <span data-ttu-id="64059-108">指向作为特定客户端连接句柄（在这里为接收语言请求的句柄）的 SRV_PROC 结构的指针。</span><span class="sxs-lookup"><span data-stu-id="64059-108">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection (in this case, the handle that received the language request).</span></span> <span data-ttu-id="64059-109">该结构包含扩展存储过程 API 库用于管理应用程序和客户端之间的通信和数据的信息。</span><span class="sxs-lookup"><span data-stu-id="64059-109">The structure contains information that the Extended Stored Procedure API library uses to manage communication and data between the application and the client.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="64059-110">返回</span><span class="sxs-lookup"><span data-stu-id="64059-110">Returns</span></span>  
 <span data-ttu-id="64059-111">SUCCEED 或 FAIL。</span><span class="sxs-lookup"><span data-stu-id="64059-111">SUCCEED or FAIL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="64059-112">备注</span><span class="sxs-lookup"><span data-stu-id="64059-112">Remarks</span></span>  
 <span data-ttu-id="64059-113">对于发送到客户端的每行调用一次 srv_sendrow 函数\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="64059-113">The **srv_sendrow** function is called once for each row sent to the client.</span></span> <span data-ttu-id="64059-114">在使用 srv_sendmsg、srv_status 或 srv_senddone 发送任何消息、状态值或完成状态之前，必须将所有行发送到客户端\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="64059-114">All rows must be sent to the client before any messages, status values, or completion statuses are sent with **srv_sendmsg**, **srv_status**, or **srv_senddone**.</span></span>  
  
 <span data-ttu-id="64059-115">如果发送尚未使用 srv_describe 定义其所有列的某行，则会导致扩展存储过程 API 应用程序引发信息性错误消息并向客户端返回 FAIL\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="64059-115">Sending a row that has not had all its columns defined with **srv_describe** causes the Extended Stored Procedure API application to raise an informational error message and return FAIL to the client.</span></span> <span data-ttu-id="64059-116">在此情况下，将不发送该行。</span><span class="sxs-lookup"><span data-stu-id="64059-116">In this case, the row is not sent.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="64059-117">扩展存储过程 API 不支持将计算行发送到客户端。</span><span class="sxs-lookup"><span data-stu-id="64059-117">The Extended Stored Procedure API does not support sending compute rows to the client.</span></span> <span data-ttu-id="64059-118">此外，如果将包含 `ntext`、`text` 或 `image` 数据的行发送到客户端，则不包含文本指针和文本时间戳。</span><span class="sxs-lookup"><span data-stu-id="64059-118">Also, if a row containing `ntext`, `text`, or `image` data is sent to the client, the text pointer and text timestamp are not included.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="64059-119">应全面检查扩展存储过程的源代码，并在生产服务器中安装编译的 DLL 之前，对这些 DLL 进行测试。</span><span class="sxs-lookup"><span data-stu-id="64059-119">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="64059-120">有关安全检查和测试的信息，请访问此 [Microsoft 网站](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)。</span><span class="sxs-lookup"><span data-stu-id="64059-120">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64059-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="64059-121">See Also</span></span>  
 [<span data-ttu-id="64059-122">srv_describe（扩展存储过程 API）</span><span class="sxs-lookup"><span data-stu-id="64059-122">srv_describe &#40;Extended Stored Procedure API&#41;</span></span>](srv-describe-extended-stored-procedure-api.md)  
  
  
