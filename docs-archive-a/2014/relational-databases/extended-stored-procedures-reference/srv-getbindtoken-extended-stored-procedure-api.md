---
title: srv_getbindtoken（扩展存储过程 API）| Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_getbindtoken
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_getbindtoken
ms.assetid: c947d011-08ac-4fb8-b925-3da6e0999277
author: rothja
ms.author: jroth
ms.openlocfilehash: d42f95c8a7df87f20ebaa30501b96b5f2a00815a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590808"
---
# <a name="srv_getbindtoken-extended-stored-procedure-api"></a><span data-ttu-id="78167-102">srv_getbindtoken（扩展存储过程 API）</span><span class="sxs-lookup"><span data-stu-id="78167-102">srv_getbindtoken (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]<span data-ttu-id="78167-103">请改用 CLR 集成。</span><span class="sxs-lookup"><span data-stu-id="78167-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="78167-104">获取调用该扩展存储过程的当前客户端会话中事务的绑定令牌。</span><span class="sxs-lookup"><span data-stu-id="78167-104">Obtains a bind token of the transaction in the current client session that invokes the extended stored procedure.</span></span>  
  
 <span data-ttu-id="78167-105">该扩展存储过程然后可以使用 sp_bindsession 将它针对同一服务器创建的任意新会话绑定到现有事务，以便新会话可以与调用了该扩展存储过程的客户端会话共享同一事务锁空间\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="78167-105">The extended stored procedure can then use **sp_bindsession** to bind any new session it creates against the same server to the existing transaction so that the new session can share the same transaction lock space with the client session that invoked the extended stored procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78167-106">语法</span><span class="sxs-lookup"><span data-stu-id="78167-106">Syntax</span></span>  
  
```  
  
int srv_getbindtoken (  
SRV_PROC*  
srvproc  
,  
char*  
bindtoken  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="78167-107">参数</span><span class="sxs-lookup"><span data-stu-id="78167-107">Arguments</span></span>  
 <span data-ttu-id="78167-108">srvproc\*\*</span><span class="sxs-lookup"><span data-stu-id="78167-108">*srvproc*</span></span>  
 <span data-ttu-id="78167-109">指向作为特定客户端连接句柄的 SRV_PROC 结构的指针。</span><span class="sxs-lookup"><span data-stu-id="78167-109">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection.</span></span> <span data-ttu-id="78167-110">该结构包含扩展存储过程 API 库用于管理应用程序和客户端之间的通信和数据的所有信息。</span><span class="sxs-lookup"><span data-stu-id="78167-110">The structure contains all the information that the Extended Stored Procedure API library uses to manage communications and data between the application and the client.</span></span>  
  
 <span data-ttu-id="78167-111">bindtoken\*\*</span><span class="sxs-lookup"><span data-stu-id="78167-111">*bindtoken*</span></span>  
 <span data-ttu-id="78167-112">指向要复制绑定令牌的缓冲区的指针。</span><span class="sxs-lookup"><span data-stu-id="78167-112">Is a pointer to a buffer where the bind token will be copied.</span></span> <span data-ttu-id="78167-113">该绑定令牌用以 Null 值结束的字符串表示。</span><span class="sxs-lookup"><span data-stu-id="78167-113">The bind token is represented as a null-terminated string.</span></span> <span data-ttu-id="78167-114">指定的缓冲区长度至少为 255 个字节。</span><span class="sxs-lookup"><span data-stu-id="78167-114">The buffer you specify should be at least 255 bytes in length.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="78167-115">返回</span><span class="sxs-lookup"><span data-stu-id="78167-115">Returns</span></span>  
 <span data-ttu-id="78167-116">SUCCEED 或 FAIL。</span><span class="sxs-lookup"><span data-stu-id="78167-116">SUCCEED or FAIL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="78167-117">备注</span><span class="sxs-lookup"><span data-stu-id="78167-117">Remarks</span></span>  
  
### <a name="to-bind-an-extended-stored-procedure-session-to-the-client-session-that-called-it-so-they-share-the-same-transaction-lock-space"></a><span data-ttu-id="78167-118">将扩展存储过程会话绑定到调用它的客户端会话以便它们共享同一事务锁空间</span><span class="sxs-lookup"><span data-stu-id="78167-118">To bind an extended stored procedure session to the client session that called it so they share the same transaction lock space</span></span>  
  
1.  <span data-ttu-id="78167-119">扩展存储过程调用 svr_getbindtoken 获取会话中当前事务的绑定令牌\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="78167-119">The extended stored procedure calls **svr_getbindtoken** to get the bind token for the current transaction in the session.</span></span> <span data-ttu-id="78167-120">在给定的 bindtoken 参数中返回该令牌\*\*。</span><span class="sxs-lookup"><span data-stu-id="78167-120">The token is returned in the given *bindtoken* parameter.</span></span>  
  
2.  <span data-ttu-id="78167-121">扩展存储过程打开针对同一服务器的新会话。</span><span class="sxs-lookup"><span data-stu-id="78167-121">The extended stored procedure opens new session(s) against the same server.</span></span> <span data-ttu-id="78167-122">在该会话内，扩展存储过程将绑定令牌用于 sp_bindsession 以将新会话绑定到同一事务\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="78167-122">Inside that session, the extended stored procedure uses the bind token with **sp_bindsession** to bind the new session to the same transaction.</span></span> <span data-ttu-id="78167-123">扩展存储过程可以创建多个会话并将所有会话绑定到同一事务。</span><span class="sxs-lookup"><span data-stu-id="78167-123">The extended stored procedure can create multiple sessions and bind all the sessions to the same transaction.</span></span>  
  
3.  <span data-ttu-id="78167-124">当外部存储过程返回空字符串或使用空字符串调用 sp_bindsession 时，解除对会话的绑定\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="78167-124">A bound session is unbound when the external stored procedure returns or when **sp_bindsession** is called with an empty string.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="78167-125">一次只能有一个绑定会话可以访问共享连接。</span><span class="sxs-lookup"><span data-stu-id="78167-125">Only one bound session at a time can have access to a shared connection.</span></span> <span data-ttu-id="78167-126">如果当前一个会话正在服务器上执行一个语句或其结果从服务器挂起，则在当前会话完成执行当前语句之前，其他共享同一绑定连接的会话都不能访问服务器。</span><span class="sxs-lookup"><span data-stu-id="78167-126">If one session is currently executing a statement at the server or has results pending from the server, no other sessions sharing the same bound connection can gain access to the server until the current session has finished executing the current statement.</span></span> <span data-ttu-id="78167-127">如果在服务器忙时会话试图访问该连接，将为冲突的会话返回错误，指明连接正在使用中，会话应稍后重试。</span><span class="sxs-lookup"><span data-stu-id="78167-127">If a session attempts to gain access to the connection while the server is busy, an error is returned to the conflicting session indicating the connection is in use and the session should retry later.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="78167-128">应全面检查扩展存储过程的源代码，并在生产服务器中安装编译的 DLL 之前，对这些 DLL 进行测试。</span><span class="sxs-lookup"><span data-stu-id="78167-128">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="78167-129">有关安全检查和测试的信息，请访问此 [Microsoft 网站](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)。</span><span class="sxs-lookup"><span data-stu-id="78167-129">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78167-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="78167-130">See Also</span></span>  
 <span data-ttu-id="78167-131">[sp_bindsession (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-bindsession-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="78167-131">[sp_bindsession &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-bindsession-transact-sql) </span></span>  
 [<span data-ttu-id="78167-132">sp_getbindtoken (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="78167-132">sp_getbindtoken &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-getbindtoken-transact-sql)  
  
  
