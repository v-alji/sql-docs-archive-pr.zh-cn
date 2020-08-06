---
title: srv_setcoldata（扩展存储过程 API）| Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_setcoldata
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_setcoldata
ms.assetid: 2e19205a-25ca-4d4a-916b-d591cf2c892b
author: rothja
ms.author: jroth
ms.openlocfilehash: b67aa2f7b5a37057d2ed87846689919d84ec4aaf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692941"
---
# <a name="srv_setcoldata-extended-stored-procedure-api"></a><span data-ttu-id="6ccc9-102">srv_setcoldata（扩展存储过程 API）</span><span class="sxs-lookup"><span data-stu-id="6ccc9-102">srv_setcoldata (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]<span data-ttu-id="6ccc9-103">请改用 CLR 集成。</span><span class="sxs-lookup"><span data-stu-id="6ccc9-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="6ccc9-104">指定列的数据的当前地址。</span><span class="sxs-lookup"><span data-stu-id="6ccc9-104">Specifies the current address for a column's data.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ccc9-105">语法</span><span class="sxs-lookup"><span data-stu-id="6ccc9-105">Syntax</span></span>  
  
```  
  
int srv_setcoldata (  
SRV_PROC *  
srvproc  
,  
int   
column  
,  
void *  
data   
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="6ccc9-106">参数</span><span class="sxs-lookup"><span data-stu-id="6ccc9-106">Arguments</span></span>  
 <span data-ttu-id="6ccc9-107">srvproc\*\*</span><span class="sxs-lookup"><span data-stu-id="6ccc9-107">*srvproc*</span></span>  
 <span data-ttu-id="6ccc9-108">指向作为特定客户端连接句柄的 SRV_PROC 结构的指针。</span><span class="sxs-lookup"><span data-stu-id="6ccc9-108">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection.</span></span> <span data-ttu-id="6ccc9-109">该结构包含扩展存储过程 API 库用于管理应用程序和客户端之间的通信和数据的信息。</span><span class="sxs-lookup"><span data-stu-id="6ccc9-109">The structure contains information the Extended Stored Procedure API library uses to manage communication and data between the application and the client.</span></span>  
  
 <span data-ttu-id="6ccc9-110">*column*</span><span class="sxs-lookup"><span data-stu-id="6ccc9-110">*column*</span></span>  
 <span data-ttu-id="6ccc9-111">指示指定其地址的列的编号。</span><span class="sxs-lookup"><span data-stu-id="6ccc9-111">Indicates the number of the column the address is being specified for.</span></span> <span data-ttu-id="6ccc9-112">列的编号从 1 开始。</span><span class="sxs-lookup"><span data-stu-id="6ccc9-112">Columns are numbered beginning with 1.</span></span>  
  
 <span data-ttu-id="6ccc9-113">*data*</span><span class="sxs-lookup"><span data-stu-id="6ccc9-113">*data*</span></span>  
 <span data-ttu-id="6ccc9-114">指向列的数据的指针。</span><span class="sxs-lookup"><span data-stu-id="6ccc9-114">Is a pointer for a column's data.</span></span> <span data-ttu-id="6ccc9-115">在将列数据替换为对 srv_setcoldata 的其他调用或调用 srv_senddone 之前，不能释放为 data 分配的内存\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6ccc9-115">Memory allocated for *data* should not be freed until the column data is replaced by another call to **srv_setcoldata**, or until **srv_senddone** is called.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="6ccc9-116">返回</span><span class="sxs-lookup"><span data-stu-id="6ccc9-116">Returns</span></span>  
 <span data-ttu-id="6ccc9-117">SUCCEED 或 FAIL。</span><span class="sxs-lookup"><span data-stu-id="6ccc9-117">SUCCEED or FAIL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6ccc9-118">备注</span><span class="sxs-lookup"><span data-stu-id="6ccc9-118">Remarks</span></span>  
 <span data-ttu-id="6ccc9-119">必须首先使用 srv_describe 定义行的每个列\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6ccc9-119">Each column of the row must be defined first with **srv_describe**.</span></span> <span data-ttu-id="6ccc9-120">列数据地址最初使用 srv_describe 进行设置\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6ccc9-120">Column data addresses are initially set with **srv_describe**.</span></span> <span data-ttu-id="6ccc9-121">如果列数据的地址发生更改，则必须调用 srv_setcoldata 以便指定该数据的新地址，并且必须针对更改后的每个列单独调用 srv_setcoldata\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6ccc9-121">If the address of the column data changes, **srv_setcoldata** must be called to specify the new address of the data and **srv_setcoldata** must be called separately for each changed column.</span></span>  
  
 <span data-ttu-id="6ccc9-122">使用 srv_setcollen 将列的长度设置为 0 可以表示 Null 数据\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6ccc9-122">Null data is represented by setting the column's length to 0 with **srv_setcollen**.</span></span> <span data-ttu-id="6ccc9-123">随后将忽略数据地址。</span><span class="sxs-lookup"><span data-stu-id="6ccc9-123">The data address is then ignored.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="6ccc9-124">应全面检查扩展存储过程的源代码，并在生产服务器中安装编译的 DLL 之前，对这些 DLL 进行测试。</span><span class="sxs-lookup"><span data-stu-id="6ccc9-124">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="6ccc9-125">有关安全检查和测试的信息，请访问此 [Microsoft 网站](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)。</span><span class="sxs-lookup"><span data-stu-id="6ccc9-125">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ccc9-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6ccc9-126">See Also</span></span>  
 [<span data-ttu-id="6ccc9-127">srv_describe（扩展存储过程 API）</span><span class="sxs-lookup"><span data-stu-id="6ccc9-127">srv_describe &#40;Extended Stored Procedure API&#41;</span></span>](srv-describe-extended-stored-procedure-api.md)  
  
  
