---
title: srv_rpcname（扩展存储过程 API）| Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_rpcname
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_rpcname
ms.assetid: 0a1424e4-3319-4836-b8d8-5e0344cc683f
author: rothja
ms.author: jroth
ms.openlocfilehash: 21530b3e7b8aaa8c5a3f8770762cde7e258e3a43
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693896"
---
# <a name="srv_rpcname-extended-stored-procedure-api"></a><span data-ttu-id="e8cb8-102">srv_rpcname（扩展存储过程 API）</span><span class="sxs-lookup"><span data-stu-id="e8cb8-102">srv_rpcname (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]<span data-ttu-id="e8cb8-103">请改用 CLR 集成。</span><span class="sxs-lookup"><span data-stu-id="e8cb8-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="e8cb8-104">返回当前远程存储过程的过程名称部分。</span><span class="sxs-lookup"><span data-stu-id="e8cb8-104">Returns the procedure name component for the current remote stored procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8cb8-105">语法</span><span class="sxs-lookup"><span data-stu-id="e8cb8-105">Syntax</span></span>  
  
```  
  
DBCHAR * srv_rpcname (  
SRV_PROC *  
srvproc  
,  
int *  
len   
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="e8cb8-106">参数</span><span class="sxs-lookup"><span data-stu-id="e8cb8-106">Arguments</span></span>  
 <span data-ttu-id="e8cb8-107">srvproc\*\*</span><span class="sxs-lookup"><span data-stu-id="e8cb8-107">*srvproc*</span></span>  
 <span data-ttu-id="e8cb8-108">指向作为特定客户端连接句柄（在这里为接收远程存储过程的句柄）的 SRV_PROC 结构的指针。</span><span class="sxs-lookup"><span data-stu-id="e8cb8-108">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection (in this case, the handle that received the remote stored procedure).</span></span> <span data-ttu-id="e8cb8-109">该结构包含扩展存储过程 API 库用于管理应用程序和客户端之间的通信和数据的信息。</span><span class="sxs-lookup"><span data-stu-id="e8cb8-109">The structure contains information that the Extended Stored Procedure API library uses to manage communication and data between the application and the client.</span></span>  
  
 <span data-ttu-id="e8cb8-110">*长度*</span><span class="sxs-lookup"><span data-stu-id="e8cb8-110">*len*</span></span>  
 <span data-ttu-id="e8cb8-111">指向接收数据库名称长度的整型变量的指针。</span><span class="sxs-lookup"><span data-stu-id="e8cb8-111">Is a pointer to an integer variable that receives the length of the database name.</span></span> <span data-ttu-id="e8cb8-112">如果 len 为 NULL，则不返回远程存储过程名称的长度\*\*。</span><span class="sxs-lookup"><span data-stu-id="e8cb8-112">If *len* is NULL, the length of the remote stored procedure name is not returned.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="e8cb8-113">返回</span><span class="sxs-lookup"><span data-stu-id="e8cb8-113">Returns</span></span>  
 <span data-ttu-id="e8cb8-114">一个 DBCHAR 指针，指向当前远程存储过程的远程存储过程名称部分的以 NULL 值结束的字符串。</span><span class="sxs-lookup"><span data-stu-id="e8cb8-114">A DBCHAR pointer to the null-terminated string for the remote stored procedure name component of the current remote stored procedure.</span></span> <span data-ttu-id="e8cb8-115">如果当前无远程存储过程，则返回 NULL，且 len 设置为 -1\*\*。</span><span class="sxs-lookup"><span data-stu-id="e8cb8-115">If there is not a current remote stored procedure, NULL is returned and *len* is set to -1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e8cb8-116">备注</span><span class="sxs-lookup"><span data-stu-id="e8cb8-116">Remarks</span></span>  
 <span data-ttu-id="e8cb8-117">此函数只返回远程存储过程的名称。</span><span class="sxs-lookup"><span data-stu-id="e8cb8-117">This function returns only the name of the remote stored procedure.</span></span> <span data-ttu-id="e8cb8-118">不包括所有者、数据库名称和远程存储过程编号的可选说明符。</span><span class="sxs-lookup"><span data-stu-id="e8cb8-118">It does not include the optional specifiers for owner, database name, and remote stored procedure number.</span></span>  
  
 <span data-ttu-id="e8cb8-119">由于在无远程存储过程的情况下也可以调用 srv_rpcname（不会出现信息性错误），因此，该函数也可用于确定是否存在远程存储过程\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e8cb8-119">Because it is valid to call **srv_rpcname** when there is not a remote stored procedure (no informational error occurs), this function provides a method for determining whether a remote stored procedure exists.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="e8cb8-120">应全面检查扩展存储过程的源代码，并在生产服务器中安装编译的 DLL 之前，对这些 DLL 进行测试。</span><span class="sxs-lookup"><span data-stu-id="e8cb8-120">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="e8cb8-121">有关安全检查和测试的信息，请访问此 [Microsoft 网站](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)。</span><span class="sxs-lookup"><span data-stu-id="e8cb8-121">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
  
