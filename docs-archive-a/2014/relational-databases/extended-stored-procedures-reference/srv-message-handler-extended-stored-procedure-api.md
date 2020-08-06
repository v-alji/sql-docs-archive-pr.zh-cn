---
title: srv_message_handler（扩展存储过程 API）| Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_message_handler
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_message_handler
ms.assetid: 41bcd057-436f-4fa8-8293-fc8057a30877
author: rothja
ms.author: jroth
ms.openlocfilehash: 7e7b6472ed4fabb6dc2d545eb51a1e026635ce19
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579589"
---
# <a name="srv_message_handler-extended-stored-procedure-api"></a><span data-ttu-id="ae96c-102">srv_message_handler（扩展存储过程 API）</span><span class="sxs-lookup"><span data-stu-id="ae96c-102">srv_message_handler (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]<span data-ttu-id="ae96c-103">请改用 CLR 集成。</span><span class="sxs-lookup"><span data-stu-id="ae96c-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="ae96c-104">调用安装的扩展存储过程 API 消息处理程序。</span><span class="sxs-lookup"><span data-stu-id="ae96c-104">Calls the installed Extended Stored Procedure API message handler.</span></span> <span data-ttu-id="ae96c-105">此函数通常用于 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 从扩展存储过程调用，以记录由 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 错误日志文件或 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 应用程序日志中的扩展存储过程) 定义的错误 (。</span><span class="sxs-lookup"><span data-stu-id="ae96c-105">This function is usually used to call [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from an extended stored procedure to log an error (defined by the extended stored procedure) in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log file or the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows application log.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae96c-106">语法</span><span class="sxs-lookup"><span data-stu-id="ae96c-106">Syntax</span></span>  
  
```  
  
int srv_message_handler (  
SRV_PROC *  
srvproc  
,  
int  
errornum  
,  
BYTE   
severity  
,  
BYTE  
state  
,  
int  
oserrnum  
,  
char *  
errtext  
,  
int  
errtextlen  
,  
char *  
oserrtext  
,  
int  
oserrtextlen  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="ae96c-107">参数</span><span class="sxs-lookup"><span data-stu-id="ae96c-107">Arguments</span></span>  
 <span data-ttu-id="ae96c-108">srvproc\*\*</span><span class="sxs-lookup"><span data-stu-id="ae96c-108">*srvproc*</span></span>  
 <span data-ttu-id="ae96c-109">指向作为特定客户端连接句柄的 SRV_PROC 结构的指针。</span><span class="sxs-lookup"><span data-stu-id="ae96c-109">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection.</span></span> <span data-ttu-id="ae96c-110">srvproc 参数包含用于管理应用程序和客户端之间的通信和数据的信息\*\*。</span><span class="sxs-lookup"><span data-stu-id="ae96c-110">The *srvproc* parameter contains information that is used to manage communication and data between the application and the client.</span></span>  
  
 <span data-ttu-id="ae96c-111">errornum\*\*</span><span class="sxs-lookup"><span data-stu-id="ae96c-111">*errornum*</span></span>  
 <span data-ttu-id="ae96c-112">由扩展存储过程定义的错误编号。</span><span class="sxs-lookup"><span data-stu-id="ae96c-112">Is an error number defined by the extended stored procedure.</span></span> <span data-ttu-id="ae96c-113">该数字必须介于 50,001 和 2,147,483,647 之间。</span><span class="sxs-lookup"><span data-stu-id="ae96c-113">This number must be from 50,001 through 2,147,483,647.</span></span>  
  
 <span data-ttu-id="ae96c-114">severity </span><span class="sxs-lookup"><span data-stu-id="ae96c-114">*severity*</span></span>  
 <span data-ttu-id="ae96c-115">错误的标准 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 严重性值。</span><span class="sxs-lookup"><span data-stu-id="ae96c-115">Is a standard [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] severity value for the error.</span></span> <span data-ttu-id="ae96c-116">该数字必须介于 0 和 24 之间。</span><span class="sxs-lookup"><span data-stu-id="ae96c-116">This number must be from 0 through 24.</span></span>  
  
 <span data-ttu-id="ae96c-117">State</span><span class="sxs-lookup"><span data-stu-id="ae96c-117">*state*</span></span>  
 <span data-ttu-id="ae96c-118">错误的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 状态值。</span><span class="sxs-lookup"><span data-stu-id="ae96c-118">Is a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] state value for the error.</span></span>  
  
 <span data-ttu-id="ae96c-119">oserrnum\*\*</span><span class="sxs-lookup"><span data-stu-id="ae96c-119">*oserrnum*</span></span>  
 <span data-ttu-id="ae96c-120">操作系统错误编号。</span><span class="sxs-lookup"><span data-stu-id="ae96c-120">Is the operating-system error number.</span></span> <span data-ttu-id="ae96c-121">此参数忽略。</span><span class="sxs-lookup"><span data-stu-id="ae96c-121">This argument is ignored.</span></span>  
  
 <span data-ttu-id="ae96c-122">errtext\*\*</span><span class="sxs-lookup"><span data-stu-id="ae96c-122">*errtext*</span></span>  
 <span data-ttu-id="ae96c-123">扩展存储过程错误 errornum 的说明\*\*。</span><span class="sxs-lookup"><span data-stu-id="ae96c-123">Is the description of the extended stored procedure error *errornum*.</span></span>  
  
 <span data-ttu-id="ae96c-124">errtextlen\*\*</span><span class="sxs-lookup"><span data-stu-id="ae96c-124">*errtextlen*</span></span>  
 <span data-ttu-id="ae96c-125">扩展存储过程错误字符串 errtext 的长度\*\*。</span><span class="sxs-lookup"><span data-stu-id="ae96c-125">Is the length of the extended stored procedure error string *errtext*.</span></span>  
  
 <span data-ttu-id="ae96c-126">oserrtext\*\*</span><span class="sxs-lookup"><span data-stu-id="ae96c-126">*oserrtext*</span></span>  
 <span data-ttu-id="ae96c-127">操作系统错误 oserrnum 的说明\*\*。</span><span class="sxs-lookup"><span data-stu-id="ae96c-127">Is the description of the operating-system error *oserrnum*.</span></span> <span data-ttu-id="ae96c-128">此参数忽略。</span><span class="sxs-lookup"><span data-stu-id="ae96c-128">This argument is ignored.</span></span>  
  
 <span data-ttu-id="ae96c-129">oserrtextlen\*\*</span><span class="sxs-lookup"><span data-stu-id="ae96c-129">*oserrtextlen*</span></span>  
 <span data-ttu-id="ae96c-130">操作系统错误字符串 oserrtext 的长度\*\*。</span><span class="sxs-lookup"><span data-stu-id="ae96c-130">Is the length of the operating-system error string *oserrtext*.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="ae96c-131">返回</span><span class="sxs-lookup"><span data-stu-id="ae96c-131">Returns</span></span>  
 <span data-ttu-id="ae96c-132">SUCCEED 或 FAIL。</span><span class="sxs-lookup"><span data-stu-id="ae96c-132">SUCCEED or FAIL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ae96c-133">备注</span><span class="sxs-lookup"><span data-stu-id="ae96c-133">Remarks</span></span>  
 <span data-ttu-id="ae96c-134">srv_message_handler 函数使扩展存储过程能够与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的集中错误日志记录和报告功能集成\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ae96c-134">The **srv_message_handler** function enables an extended stored procedure to integrate with the centralized error logging and reporting features of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="ae96c-135">可以为扩展存储过程中的事件建立 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 警报，SQL Server 代理将监视这些警报情况。</span><span class="sxs-lookup"><span data-stu-id="ae96c-135">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] alerts can be established for events from extended stored procedures, and SQL Server Agent will monitor for these alert conditions.</span></span>  
  
 <span data-ttu-id="ae96c-136">如果错误消息较长，则将其截断为 412 个字节。</span><span class="sxs-lookup"><span data-stu-id="ae96c-136">If the error message is longer, it is truncated to 412 bytes.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="ae96c-137">应全面检查扩展存储过程的源代码，并在生产服务器中安装编译的 DLL 之前，对这些 DLL 进行测试。</span><span class="sxs-lookup"><span data-stu-id="ae96c-137">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="ae96c-138">有关安全检查和测试的信息，请访问此 [Microsoft 网站](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)。</span><span class="sxs-lookup"><span data-stu-id="ae96c-138">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
  
