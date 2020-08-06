---
title: srv_rpcdb（扩展存储过程 API）| Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_rpcdb
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_rpcdb
ms.assetid: d52bfd22-7a7c-4ab0-af65-df96ff359e6f
author: rothja
ms.author: jroth
ms.openlocfilehash: c951a4a821bbd49748182d9ddf5df017344a174d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692942"
---
# <a name="srv_rpcdb-extended-stored-procedure-api"></a><span data-ttu-id="941d2-102">srv_rpcdb（扩展存储过程 API）</span><span class="sxs-lookup"><span data-stu-id="941d2-102">srv_rpcdb (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]<span data-ttu-id="941d2-103">请改用 CLR 集成。</span><span class="sxs-lookup"><span data-stu-id="941d2-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="941d2-104">返回当前远程存储过程的数据库名称部分。</span><span class="sxs-lookup"><span data-stu-id="941d2-104">Returns the database name component for the current remote stored procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="941d2-105">语法</span><span class="sxs-lookup"><span data-stu-id="941d2-105">Syntax</span></span>  
  
```  
  
DBCHAR * srv_rpcdb (  
SRV_PROC * srvproc,int *len );  
```  
  
## <a name="arguments"></a><span data-ttu-id="941d2-106">参数</span><span class="sxs-lookup"><span data-stu-id="941d2-106">Arguments</span></span>  
 <span data-ttu-id="941d2-107">srvproc\*\*</span><span class="sxs-lookup"><span data-stu-id="941d2-107">*srvproc*</span></span>  
 <span data-ttu-id="941d2-108">指向作为特定客户端连接句柄的 SRV_PROC 结构的指针。</span><span class="sxs-lookup"><span data-stu-id="941d2-108">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection.</span></span> <span data-ttu-id="941d2-109">该结构包含扩展存储过程 API 库用于管理应用程序和客户端之间的通信和数据的信息。</span><span class="sxs-lookup"><span data-stu-id="941d2-109">The structure contains information the Extended Stored Procedure API library uses to manage communication and data between the application and the client.</span></span>  
  
 <span data-ttu-id="941d2-110">*长度*</span><span class="sxs-lookup"><span data-stu-id="941d2-110">*len*</span></span>  
 <span data-ttu-id="941d2-111">指向接收数据库名称长度的 `int` 变量的指针。</span><span class="sxs-lookup"><span data-stu-id="941d2-111">Is a pointer to an `int` variable that receives the length of the database name.</span></span> <span data-ttu-id="941d2-112">如果 len 为 NULL，则不返回数据库名称的长度\*\*。</span><span class="sxs-lookup"><span data-stu-id="941d2-112">If *len* is NULL, the length of the database name is not returned.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="941d2-113">返回</span><span class="sxs-lookup"><span data-stu-id="941d2-113">Returns</span></span>  
 <span data-ttu-id="941d2-114">一个 DBCHAR 指针，指向当前远程存储过程的数据库名称部分的以 NULL 值结束的字符串。</span><span class="sxs-lookup"><span data-stu-id="941d2-114">A DBCHAR pointer to the null-terminated string for the database name part of the current remote stored procedure.</span></span> <span data-ttu-id="941d2-115">如果当前无远程存储过程，则返回 NULL，且 len 参数设置为 -1\*\*。</span><span class="sxs-lookup"><span data-stu-id="941d2-115">If there is no current remote stored procedure, NULL is returned and the *len* parameter is set to - 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="941d2-116">备注</span><span class="sxs-lookup"><span data-stu-id="941d2-116">Remarks</span></span>  
 <span data-ttu-id="941d2-117">此函数只返回远程存储过程对象名称的数据库部分。</span><span class="sxs-lookup"><span data-stu-id="941d2-117">This function returns only the database component of the remote stored procedure object name.</span></span> <span data-ttu-id="941d2-118">它不包括所有者、远程存储过程名称和远程存储过程编号的可选说明符。</span><span class="sxs-lookup"><span data-stu-id="941d2-118">It does not include the optional specifiers for owner, remote stored procedure name, and remote stored procedure number.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="941d2-119">应全面检查扩展存储过程的源代码，并在生产服务器中安装编译的 DLL 之前，对这些 DLL 进行测试。</span><span class="sxs-lookup"><span data-stu-id="941d2-119">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="941d2-120">有关安全检查和测试的信息，请访问此 [Microsoft 网站](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)。</span><span class="sxs-lookup"><span data-stu-id="941d2-120">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
  
