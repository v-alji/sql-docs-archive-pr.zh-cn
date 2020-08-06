---
title: srv_setutype（扩展存储过程 API）| Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_setutype
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_setutype
ms.assetid: 6160f15d-1b68-411e-ab6d-491ec288f264
author: rothja
ms.author: jroth
ms.openlocfilehash: e9e02605995e44f5869633d5e8778a955236005f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692940"
---
# <a name="srv_setutype-extended-stored-procedure-api"></a><span data-ttu-id="244ef-102">srv_setutype（扩展存储过程 API）</span><span class="sxs-lookup"><span data-stu-id="244ef-102">srv_setutype (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]<span data-ttu-id="244ef-103">请改用 CLR 集成。</span><span class="sxs-lookup"><span data-stu-id="244ef-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="244ef-104">为行中的列设置用户定义数据类型。</span><span class="sxs-lookup"><span data-stu-id="244ef-104">Sets the user-defined data type for a column in a row.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="244ef-105">语法</span><span class="sxs-lookup"><span data-stu-id="244ef-105">Syntax</span></span>  
  
```  
  
int srv_setutype (  
SRV_PROC *  
srvproc  
,  
int   
column  
,   
DBINT  
user_type   
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="244ef-106">参数</span><span class="sxs-lookup"><span data-stu-id="244ef-106">Arguments</span></span>  
 <span data-ttu-id="244ef-107">srvproc\*\*</span><span class="sxs-lookup"><span data-stu-id="244ef-107">*srvproc*</span></span>  
 <span data-ttu-id="244ef-108">指向作为特定客户端连接句柄的 SRV_PROC 结构的指针。</span><span class="sxs-lookup"><span data-stu-id="244ef-108">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection.</span></span> <span data-ttu-id="244ef-109">该结构包含扩展存储过程 API 库用于管理应用程序和客户端之间的通信和数据的信息。</span><span class="sxs-lookup"><span data-stu-id="244ef-109">The structure contains information the Extended Stored Procedure API library uses to manage communication and data between the application and the client.</span></span>  
  
 <span data-ttu-id="244ef-110">*column*</span><span class="sxs-lookup"><span data-stu-id="244ef-110">*column*</span></span>  
 <span data-ttu-id="244ef-111">指示要设置的列。</span><span class="sxs-lookup"><span data-stu-id="244ef-111">Indicates which column to set.</span></span> <span data-ttu-id="244ef-112">列的编号从 1 开始。</span><span class="sxs-lookup"><span data-stu-id="244ef-112">Columns are numbered beginning with 1.</span></span>  
  
 <span data-ttu-id="244ef-113">*user_type*</span><span class="sxs-lookup"><span data-stu-id="244ef-113">*user_type*</span></span>  
 <span data-ttu-id="244ef-114">指定用户定义数据类型的代码。</span><span class="sxs-lookup"><span data-stu-id="244ef-114">Specifies the user-defined data type code.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="244ef-115">返回</span><span class="sxs-lookup"><span data-stu-id="244ef-115">Returns</span></span>  
 <span data-ttu-id="244ef-116">SUCCEED 或 FAIL。</span><span class="sxs-lookup"><span data-stu-id="244ef-116">SUCCEED or FAIL.</span></span> <span data-ttu-id="244ef-117">如果相应列不存在，则返回 FAIL。</span><span class="sxs-lookup"><span data-stu-id="244ef-117">Returns FAIL if the column does not exist.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="244ef-118">备注</span><span class="sxs-lookup"><span data-stu-id="244ef-118">Remarks</span></span>  
 <span data-ttu-id="244ef-119">列具有两种数据类型：其实际数据类型及其用户定义数据类型。</span><span class="sxs-lookup"><span data-stu-id="244ef-119">A column has two data types: its actual data type and its user-defined data type.</span></span> <span data-ttu-id="244ef-120">用户定义数据类型由用于存储列的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实际用户定义数据类型（如果有）和列说明信息（如为空性和可更新性）。</span><span class="sxs-lookup"><span data-stu-id="244ef-120">The user-defined data type is used by [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to store the actual user-defined data type of the column, if any, and column description information, such as nullability and updatability, for the column.</span></span>  
  
 <span data-ttu-id="244ef-121">在使用 srv_describe 定义列后，并且在发送最后一行前，随时都可以调用 srv_setutype 函数\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="244ef-121">The **srv_setutype** function can be called any time that *column* has been defined with **srv_describe** and before the last row has been sent.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="244ef-122">应全面检查扩展存储过程的源代码，并在生产服务器中安装编译的 DLL 之前，对这些 DLL 进行测试。</span><span class="sxs-lookup"><span data-stu-id="244ef-122">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="244ef-123">有关安全检查和测试的信息，请访问此 [Microsoft 网站](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)。</span><span class="sxs-lookup"><span data-stu-id="244ef-123">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="244ef-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="244ef-124">See Also</span></span>  
 [<span data-ttu-id="244ef-125">srv_describe（扩展存储过程 API）</span><span class="sxs-lookup"><span data-stu-id="244ef-125">srv_describe &#40;Extended Stored Procedure API&#41;</span></span>](srv-describe-extended-stored-procedure-api.md)  
  
  
