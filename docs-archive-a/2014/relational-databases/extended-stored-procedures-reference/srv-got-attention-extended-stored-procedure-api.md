---
title: srv_got_attention（扩展存储过程 API）| Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_got_attention
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_got_attention
ms.assetid: 805e68e1-d17f-41bd-8b9f-a27283bb6fbe
author: rothja
ms.author: jroth
ms.openlocfilehash: bb5432e2f5e259187e506237842fbb9110e27a69
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693908"
---
# <a name="srv_got_attention-extended-stored-procedure-api"></a><span data-ttu-id="d3abf-102">srv_got_attention（扩展存储过程 API）</span><span class="sxs-lookup"><span data-stu-id="d3abf-102">srv_got_attention (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]<span data-ttu-id="d3abf-103">请改用 CLR 集成。</span><span class="sxs-lookup"><span data-stu-id="d3abf-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="d3abf-104">请检查是否需要中止当前连接或任务以及在连接已终止或批已中止时是否返回 TRUE。</span><span class="sxs-lookup"><span data-stu-id="d3abf-104">Checks whether the current connection or task needs to be aborted and returns TRUE if the connection is killed or the batch is aborted</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3abf-105">语法</span><span class="sxs-lookup"><span data-stu-id="d3abf-105">Syntax</span></span>  
  
```  
  
BOOL srv_got_attention  
(SRV_PROC *  
srvproc  
);  
  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d3abf-106">参数</span><span class="sxs-lookup"><span data-stu-id="d3abf-106">Parameters</span></span>  
 <span data-ttu-id="d3abf-107">srvproc\*\*</span><span class="sxs-lookup"><span data-stu-id="d3abf-107">*srvproc*</span></span>  
 <span data-ttu-id="d3abf-108">标识数据库连接的指针。</span><span class="sxs-lookup"><span data-stu-id="d3abf-108">Pointer identifying a database connection.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d3abf-109">返回值</span><span class="sxs-lookup"><span data-stu-id="d3abf-109">Return Value</span></span>  
 <span data-ttu-id="d3abf-110">如果连接已终止或者批已中止，则为 TRUE。</span><span class="sxs-lookup"><span data-stu-id="d3abf-110">TRUE if the connection is killed or the batch is aborted.</span></span> <span data-ttu-id="d3abf-111">如果连接或批处于活动状态，则为 FALSE。</span><span class="sxs-lookup"><span data-stu-id="d3abf-111">FALSE if the connection or batch is active.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d3abf-112">备注</span><span class="sxs-lookup"><span data-stu-id="d3abf-112">Remarks</span></span>  
 <span data-ttu-id="d3abf-113">长时间运行的扩展存储过程应通过定期调用 srv_got_attention 来检查服务器的关注情况，这样使过程可以在连接终止或批处理中止时终止自身\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d3abf-113">A long-running extended stored procedure should check the server attention by calling **srv_got_attention** periodically so that the procedure may terminate itself when the connection is killed or the batch is aborted.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="d3abf-114">应全面检查扩展存储过程的源代码，并在生产服务器中安装编译的 DLL 之前，对这些 DLL 进行测试。</span><span class="sxs-lookup"><span data-stu-id="d3abf-114">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="d3abf-115">有关安全检查和测试的信息，请访问此 [Microsoft 网站](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)。</span><span class="sxs-lookup"><span data-stu-id="d3abf-115">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
  
