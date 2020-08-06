---
title: srv_pfield（扩展存储过程 API）| Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_pfield
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_pfield
ms.assetid: a61e4c1f-e65b-48ea-a7d1-3e1544af389d
author: rothja
ms.author: jroth
ms.openlocfilehash: 90680d59dbf36ad3f713fd7a09d07553890a8668
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693898"
---
# <a name="srv_pfield-extended-stored-procedure-api"></a><span data-ttu-id="313ad-102">srv_pfield（扩展存储过程 API）</span><span class="sxs-lookup"><span data-stu-id="313ad-102">srv_pfield (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]<span data-ttu-id="313ad-103">请改用 CLR 集成。</span><span class="sxs-lookup"><span data-stu-id="313ad-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="313ad-104">返回有关数据库连接的信息。</span><span class="sxs-lookup"><span data-stu-id="313ad-104">Returns information about a database connection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="313ad-105">语法</span><span class="sxs-lookup"><span data-stu-id="313ad-105">Syntax</span></span>  
  
```  
  
DBCHAR * srv_pfield (  
SRV_PROC *  
srvproc  
,  
int   
field  
,  
int *  
len  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="313ad-106">参数</span><span class="sxs-lookup"><span data-stu-id="313ad-106">Arguments</span></span>  
 <span data-ttu-id="313ad-107">srvproc\*\*</span><span class="sxs-lookup"><span data-stu-id="313ad-107">*srvproc*</span></span>  
 <span data-ttu-id="313ad-108">标识数据库连接的指针。</span><span class="sxs-lookup"><span data-stu-id="313ad-108">Pointer identifying a database connection.</span></span>  
  
 <span data-ttu-id="313ad-109">*定义域*</span><span class="sxs-lookup"><span data-stu-id="313ad-109">*field*</span></span>  
 <span data-ttu-id="313ad-110">指定连接将返回的数据。</span><span class="sxs-lookup"><span data-stu-id="313ad-110">Specifies data on the connection to return.</span></span>  
  
|<span data-ttu-id="313ad-111">值</span><span class="sxs-lookup"><span data-stu-id="313ad-111">Value</span></span>|<span data-ttu-id="313ad-112">返回</span><span class="sxs-lookup"><span data-stu-id="313ad-112">Returns</span></span>|  
|-----------|-------------|  
|<span data-ttu-id="313ad-113">SRV_APPLNAME</span><span class="sxs-lookup"><span data-stu-id="313ad-113">SRV_APPLNAME</span></span>|<span data-ttu-id="313ad-114">客户端建立连接时提供的应用程序名称。</span><span class="sxs-lookup"><span data-stu-id="313ad-114">The application name provided by the client when it established the connection.</span></span>|  
|<span data-ttu-id="313ad-115">SRV_BCPFLAG</span><span class="sxs-lookup"><span data-stu-id="313ad-115">SRV_BCPFLAG</span></span>|<span data-ttu-id="313ad-116">一个标志，如果客户端正在准备执行大容量复制操作，则为 TRUE；否则为 FALSE。</span><span class="sxs-lookup"><span data-stu-id="313ad-116">A flag that is TRUE if the client is preparing for a bulk copy operation; otherwise, FALSE.</span></span>|  
|<span data-ttu-id="313ad-117">SRV_CLIB</span><span class="sxs-lookup"><span data-stu-id="313ad-117">SRV_CLIB</span></span>|<span data-ttu-id="313ad-118">使客户端能够与服务器通信的库的名称。</span><span class="sxs-lookup"><span data-stu-id="313ad-118">The name of the library that enables the client to talk to a server.</span></span>|  
|<span data-ttu-id="313ad-119">SRV_CPID</span><span class="sxs-lookup"><span data-stu-id="313ad-119">SRV_CPID</span></span>|<span data-ttu-id="313ad-120">客户端源计算机上的客户端进程 ID。</span><span class="sxs-lookup"><span data-stu-id="313ad-120">The client process ID on the client source computer.</span></span>|  
|<span data-ttu-id="313ad-121">SRV_HOST</span><span class="sxs-lookup"><span data-stu-id="313ad-121">SRV_HOST</span></span>|<span data-ttu-id="313ad-122">客户端建立连接时提供的客户端计算机的名称。</span><span class="sxs-lookup"><span data-stu-id="313ad-122">The name of the client's machine provided by the client when it established the connection.</span></span>|  
|<span data-ttu-id="313ad-123">SRV_LIBVERS</span><span class="sxs-lookup"><span data-stu-id="313ad-123">SRV_LIBVERS</span></span>|<span data-ttu-id="313ad-124">客户端库的版本。</span><span class="sxs-lookup"><span data-stu-id="313ad-124">The version of the client library.</span></span>|  
|<span data-ttu-id="313ad-125">SRV_LSECURE</span><span class="sxs-lookup"><span data-stu-id="313ad-125">SRV_LSECURE</span></span>|<span data-ttu-id="313ad-126">一个标志。</span><span class="sxs-lookup"><span data-stu-id="313ad-126">A flag.</span></span> <span data-ttu-id="313ad-127">如果连接使用集成安全性进行登录，则为 TRUE。</span><span class="sxs-lookup"><span data-stu-id="313ad-127">TRUE if the connection used integrated security to login.</span></span>|  
|<span data-ttu-id="313ad-128">SRV_NETWORK_MODULE</span><span class="sxs-lookup"><span data-stu-id="313ad-128">SRV_NETWORK_MODULE</span></span>|<span data-ttu-id="313ad-129">连接使用的网络库 DLL 的名称。</span><span class="sxs-lookup"><span data-stu-id="313ad-129">The name of the Net-Library DLL used by the connection.</span></span>|  
|<span data-ttu-id="313ad-130">SRV_NETWORK_VERSION</span><span class="sxs-lookup"><span data-stu-id="313ad-130">SRV_NETWORK_VERSION</span></span>|<span data-ttu-id="313ad-131">连接使用的网络库 DLL 的版本。</span><span class="sxs-lookup"><span data-stu-id="313ad-131">The version of the Net-Library DLL used by the connection.</span></span>|  
|<span data-ttu-id="313ad-132">SRV_NETWORK_CONNECTION</span><span class="sxs-lookup"><span data-stu-id="313ad-132">SRV_NETWORK_CONNECTION</span></span>|<span data-ttu-id="313ad-133">传递到用于当前 srvproc 连接的网络库 DLL 的连接字符串\*\*。</span><span class="sxs-lookup"><span data-stu-id="313ad-133">The connection string passed to the Net-Library DLL used for the current *srvproc* connection.</span></span>|  
|<span data-ttu-id="313ad-134">SRV_PIPEHANDLE</span><span class="sxs-lookup"><span data-stu-id="313ad-134">SRV_PIPEHANDLE</span></span>|<span data-ttu-id="313ad-135">包含某个已连接客户端的管道句柄的字符串，或者，如果客户端连接到不使用命名管道的网络，则为 NULL。</span><span class="sxs-lookup"><span data-stu-id="313ad-135">A string containing the pipe handle of a connected client, or NULL if the client is connected on a network that does not use named pipes.</span></span> <span data-ttu-id="313ad-136">若要将此句柄用作 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 的有效管道句柄，请将此字符串转换为整数。</span><span class="sxs-lookup"><span data-stu-id="313ad-136">To use this handle as a valid pipe handle with [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows, convert this string to an integer.</span></span>|  
|<span data-ttu-id="313ad-137">SRV_RMTSERVER</span><span class="sxs-lookup"><span data-stu-id="313ad-137">SRV_RMTSERVER</span></span>|<span data-ttu-id="313ad-138">客户端进程从中登录的服务器。</span><span class="sxs-lookup"><span data-stu-id="313ad-138">The server from which the client process is logged in.</span></span> <span data-ttu-id="313ad-139">如果从客户端进行登录，则此值为空字符串。</span><span class="sxs-lookup"><span data-stu-id="313ad-139">If the login is from a client, this value is an empty string.</span></span>|  
|<span data-ttu-id="313ad-140">SRV_ROWSENT</span><span class="sxs-lookup"><span data-stu-id="313ad-140">SRV_ROWSENT</span></span>|<span data-ttu-id="313ad-141">srvproc 已经为当前结果集发送的行数\*\*。</span><span class="sxs-lookup"><span data-stu-id="313ad-141">The number of rows already sent by *srvproc* for the current set of results.</span></span>|  
|<span data-ttu-id="313ad-142">SRV_SPID</span><span class="sxs-lookup"><span data-stu-id="313ad-142">SRV_SPID</span></span>|<span data-ttu-id="313ad-143">srvproc 的服务器线程 ID\*\*。</span><span class="sxs-lookup"><span data-stu-id="313ad-143">The server thread ID of the *srvproc*.</span></span> <span data-ttu-id="313ad-144">对于扩展存储过程，此值与 sys.sysprocesses的 kpid 列相同，并且它可能随时间的推移而发生变化\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="313ad-144">For extended stored procedures, this value is the same as the **kpid** column of **sys.sysprocesses**, and it can change over time.</span></span>|  
|<span data-ttu-id="313ad-145">SRV_SPROC_CODEPAGE</span><span class="sxs-lookup"><span data-stu-id="313ad-145">SRV_SPROC_CODEPAGE</span></span>|<span data-ttu-id="313ad-146">服务器用于解释多字节数据的代码页。</span><span class="sxs-lookup"><span data-stu-id="313ad-146">Codepage that the server uses to interpret multbyte data.</span></span>|  
|<span data-ttu-id="313ad-147">SRV_STATUS</span><span class="sxs-lookup"><span data-stu-id="313ad-147">SRV_STATUS</span></span>|<span data-ttu-id="313ad-148">srvproc 的当前状态：正在运行或已关闭\*\*</span><span class="sxs-lookup"><span data-stu-id="313ad-148">The current status of *srvproc*: running or closed</span></span>|  
|<span data-ttu-id="313ad-149">SRV_TYPE</span><span class="sxs-lookup"><span data-stu-id="313ad-149">SRV_TYPE</span></span>|<span data-ttu-id="313ad-150">srvproc 的连接类型\*\*。</span><span class="sxs-lookup"><span data-stu-id="313ad-150">The connection type of *srvproc*.</span></span> <span data-ttu-id="313ad-151">如果返回服务器，srvproc 则来自 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的实例\*\*。</span><span class="sxs-lookup"><span data-stu-id="313ad-151">If server is returned, *srvproc* is from an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="313ad-152">如果返回客户端，srvproc 则来自 DB-Library 或 ODBC 客户端\*\*。</span><span class="sxs-lookup"><span data-stu-id="313ad-152">If client is returned, *srvproc* is from a DB-Library or ODBC client.</span></span>|  
|<span data-ttu-id="313ad-153">SRV_USER</span><span class="sxs-lookup"><span data-stu-id="313ad-153">SRV_USER</span></span>|<span data-ttu-id="313ad-154">连接的用户名。</span><span class="sxs-lookup"><span data-stu-id="313ad-154">The user name of the connection.</span></span>|  
|||  
  
 <span data-ttu-id="313ad-155">*长度*</span><span class="sxs-lookup"><span data-stu-id="313ad-155">*len*</span></span>  
 <span data-ttu-id="313ad-156">指向一个 int 变量的指针，该变量包含所返回的 field 值的长度\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="313ad-156">Is a pointer to an **int** variable that contains the length of the returned *field* value.</span></span> <span data-ttu-id="313ad-157">如果 len 为 NULL，则不返回字符串的长度\*\*。</span><span class="sxs-lookup"><span data-stu-id="313ad-157">If *len* is NULL, the length of the string is not returned.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="313ad-158">返回</span><span class="sxs-lookup"><span data-stu-id="313ad-158">Returns</span></span>  
 <span data-ttu-id="313ad-159">指向一个以 null 值结束的字符串的指针，该字符串包含 SRV_PROC 结构中指定字段的当前值。</span><span class="sxs-lookup"><span data-stu-id="313ad-159">A pointer to a null-terminated string containing the current value for the specified field in the SRV_PROC structure.</span></span> <span data-ttu-id="313ad-160">如果此字段为空，则返回指向空字符串的有效指针，并且 len 包含 0\*\*。</span><span class="sxs-lookup"><span data-stu-id="313ad-160">If the field is empty, a valid pointer to an empty string is returned and *len* contains 0.</span></span> <span data-ttu-id="313ad-161">如果此字段为未知，则返回 NULL 并且 len 包含值 -1\*\*。</span><span class="sxs-lookup"><span data-stu-id="313ad-161">If the field is unknown, NULL is returned and *len* contains the value -1.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="313ad-162">应全面检查扩展存储过程的源代码，并在生产服务器中安装编译的 DLL 之前，对这些 DLL 进行测试。</span><span class="sxs-lookup"><span data-stu-id="313ad-162">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="313ad-163">有关安全检查和测试的详细信息，请访问[安全开发人员中心](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)。</span><span class="sxs-lookup"><span data-stu-id="313ad-163">For information about security review and testing, see the [Security Developer Center](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
  
