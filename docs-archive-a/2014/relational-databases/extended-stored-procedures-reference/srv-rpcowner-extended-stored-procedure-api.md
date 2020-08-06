---
title: srv_rpcowner（扩展存储过程 API）| Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_rpcowner
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_rpcowner
ms.assetid: e81a60e6-14ea-47bc-a11c-3d7635344447
author: rothja
ms.author: jroth
ms.openlocfilehash: f903870d0ee01256addb1557eb7e9123853b39e6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694461"
---
# <a name="srv_rpcowner-extended-stored-procedure-api"></a><span data-ttu-id="20dad-102">srv_rpcowner（扩展存储过程 API）</span><span class="sxs-lookup"><span data-stu-id="20dad-102">srv_rpcowner (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]<span data-ttu-id="20dad-103">请改用 CLR 集成。</span><span class="sxs-lookup"><span data-stu-id="20dad-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="20dad-104">返回当前远程存储过程的所有者组件。</span><span class="sxs-lookup"><span data-stu-id="20dad-104">Returns the owner component for the current remote stored procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20dad-105">语法</span><span class="sxs-lookup"><span data-stu-id="20dad-105">Syntax</span></span>  
  
```  
  
DBCHAR * srv_rpcowner (  
SRV_PROC *  
srvproc  
,  
int *  
len   
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="20dad-106">参数</span><span class="sxs-lookup"><span data-stu-id="20dad-106">Arguments</span></span>  
 <span data-ttu-id="20dad-107">srvproc\*\*</span><span class="sxs-lookup"><span data-stu-id="20dad-107">*srvproc*</span></span>  
 <span data-ttu-id="20dad-108">指向作为特定客户端连接句柄（在这里为接收远程存储过程的句柄）的 SRV_PROC 结构的指针。</span><span class="sxs-lookup"><span data-stu-id="20dad-108">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection (in this case, the handle that received the remote stored procedure).</span></span> <span data-ttu-id="20dad-109">该结构包含扩展存储过程 API 库用于管理应用程序和客户端之间的通信和数据的信息。</span><span class="sxs-lookup"><span data-stu-id="20dad-109">The structure contains information that the Extended Stored Procedure API library uses to manage communication and data between the application and the client.</span></span>  
  
 <span data-ttu-id="20dad-110">*长度*</span><span class="sxs-lookup"><span data-stu-id="20dad-110">*len*</span></span>  
 <span data-ttu-id="20dad-111">指向接收所有者名称长度的整数变量的指针。</span><span class="sxs-lookup"><span data-stu-id="20dad-111">Is a pointer to an integer variable that receives the length of the owner name.</span></span> <span data-ttu-id="20dad-112">参数 len 可为 NULL，在这种情况下不会返回所有者组件的长度\*\*。</span><span class="sxs-lookup"><span data-stu-id="20dad-112">The parameter *len* can be NULL, in which case the length of the owner component is not returned.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="20dad-113">返回</span><span class="sxs-lookup"><span data-stu-id="20dad-113">Returns</span></span>  
 <span data-ttu-id="20dad-114">一个 DBCHAR 指针，指向当前远程存储过程的以 Null 值结束的所有者组件。</span><span class="sxs-lookup"><span data-stu-id="20dad-114">A DBCHAR pointer to the null-terminated owner component for the current remote stored procedure.</span></span> <span data-ttu-id="20dad-115">如果当前无远程存储过程，则返回 NULL，且 len 设置为 -1\*\*。</span><span class="sxs-lookup"><span data-stu-id="20dad-115">If there is no current remote stored procedure, NULL is returned and *len* is set to - 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="20dad-116">备注</span><span class="sxs-lookup"><span data-stu-id="20dad-116">Remarks</span></span>  
 <span data-ttu-id="20dad-117">此函数只返回远程存储过程的所有者组件。</span><span class="sxs-lookup"><span data-stu-id="20dad-117">This function returns only the owner component of the remote stored procedure.</span></span> <span data-ttu-id="20dad-118">不包括名称、远程存储过程名称和远程存储过程编号的可选说明符。</span><span class="sxs-lookup"><span data-stu-id="20dad-118">It does not include the optional specifiers for name, remote stored procedure name, and remote stored procedure number.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="20dad-119">应全面检查扩展存储过程的源代码，并在生产服务器中安装编译的 DLL 之前，对这些 DLL 进行测试。</span><span class="sxs-lookup"><span data-stu-id="20dad-119">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="20dad-120">有关安全检查和测试的信息，请访问此 [Microsoft 网站](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)。</span><span class="sxs-lookup"><span data-stu-id="20dad-120">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
  
