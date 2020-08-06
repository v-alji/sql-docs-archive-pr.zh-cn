---
title: srv_paramlen（扩展存储过程 API）| Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_paramlen
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_paramlen
ms.assetid: d1fe92ff-cad6-4396-8216-125e5642e81e
author: rothja
ms.author: jroth
ms.openlocfilehash: fc2a0fa7f8409767a2afaa9c4c621ea72732b701
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693903"
---
# <a name="srv_paramlen-extended-stored-procedure-api"></a><span data-ttu-id="51fa3-102">srv_paramlen（扩展存储过程 API）</span><span class="sxs-lookup"><span data-stu-id="51fa3-102">srv_paramlen (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]<span data-ttu-id="51fa3-103">请改用 CLR 集成。</span><span class="sxs-lookup"><span data-stu-id="51fa3-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="51fa3-104">返回远程存储过程调用参数的数据长度。</span><span class="sxs-lookup"><span data-stu-id="51fa3-104">Returns the data length of a remote stored procedure call parameter.</span></span> <span data-ttu-id="51fa3-105">此函数已被 srv_paraminfo 函数取代\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="51fa3-105">This function has been superseded by the **srv_paraminfo** function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51fa3-106">语法</span><span class="sxs-lookup"><span data-stu-id="51fa3-106">Syntax</span></span>  
  
```  
  
int srv_paramlen (  
SRV_PROC *  
srvproc  
,  
int  
n   
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="51fa3-107">参数</span><span class="sxs-lookup"><span data-stu-id="51fa3-107">Arguments</span></span>  
 <span data-ttu-id="51fa3-108">srvproc\*\*</span><span class="sxs-lookup"><span data-stu-id="51fa3-108">*srvproc*</span></span>  
 <span data-ttu-id="51fa3-109">指向作为特定客户端连接句柄（在这里为接收远程存储过程调用的句柄）的 SRV_PROC 结构的指针。</span><span class="sxs-lookup"><span data-stu-id="51fa3-109">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection (in this case, the handle that received the remote stored procedure call).</span></span> <span data-ttu-id="51fa3-110">该结构包含扩展存储过程 API 库用于管理应用程序和客户端之间的通信和数据的信息。</span><span class="sxs-lookup"><span data-stu-id="51fa3-110">The structure contains information that the Extended Stored Procedure API library uses to manage communication and data between the application and the client.</span></span>  
  
 <span data-ttu-id="51fa3-111">*n*</span><span class="sxs-lookup"><span data-stu-id="51fa3-111">*n*</span></span>  
 <span data-ttu-id="51fa3-112">指示参数的编号。</span><span class="sxs-lookup"><span data-stu-id="51fa3-112">Indicates the number of the parameter.</span></span> <span data-ttu-id="51fa3-113">第一个参数是 1。</span><span class="sxs-lookup"><span data-stu-id="51fa3-113">The first parameter is 1.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="51fa3-114">返回</span><span class="sxs-lookup"><span data-stu-id="51fa3-114">Returns</span></span>  
 <span data-ttu-id="51fa3-115">参数数据的实际长度（字节）。</span><span class="sxs-lookup"><span data-stu-id="51fa3-115">The actual length, in bytes, of the parameter data.</span></span> <span data-ttu-id="51fa3-116">如果没有第 n 个参数或没有远程存储过程，则返回 -1\*\*。</span><span class="sxs-lookup"><span data-stu-id="51fa3-116">If there is no *n*th parameter or there is no remote stored procedure, it returns -1.</span></span> <span data-ttu-id="51fa3-117">如果第 n 个参数为 NULL，则返回 0\*\*。</span><span class="sxs-lookup"><span data-stu-id="51fa3-117">If the *n*th parameter is NULL, it returns 0.</span></span>  
  
 <span data-ttu-id="51fa3-118">如果参数为以下 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 系统数据类型之一，则此函数返回以下值 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="51fa3-118">This function returns the following values, if the parameter is one of the following [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] system data types.</span></span>  
  
|<span data-ttu-id="51fa3-119">新数据类型</span><span class="sxs-lookup"><span data-stu-id="51fa3-119">New data types</span></span>|<span data-ttu-id="51fa3-120">输入数据长度</span><span class="sxs-lookup"><span data-stu-id="51fa3-120">Input data length</span></span>|  
|--------------------|-----------------------|  
|`BITN`|<span data-ttu-id="51fa3-121">**NULL：** 1</span><span class="sxs-lookup"><span data-stu-id="51fa3-121">**NULL:** 1</span></span><br /><br /> <span data-ttu-id="51fa3-122">**零：** 1</span><span class="sxs-lookup"><span data-stu-id="51fa3-122">**ZERO:** 1</span></span><br /><br /> <span data-ttu-id="51fa3-123">**>= 255：** 不适用</span><span class="sxs-lookup"><span data-stu-id="51fa3-123">**>=255:** N/A</span></span><br /><br /> <span data-ttu-id="51fa3-124">**<255：** 不适用</span><span class="sxs-lookup"><span data-stu-id="51fa3-124">**<255:** N/A</span></span>|  
|`BIGVARCHAR`|<span data-ttu-id="51fa3-125">**NULL：** 0</span><span class="sxs-lookup"><span data-stu-id="51fa3-125">**NULL:** 0</span></span><br /><br /> <span data-ttu-id="51fa3-126">**零：** 1</span><span class="sxs-lookup"><span data-stu-id="51fa3-126">**ZERO:** 1</span></span><br /><br /> <span data-ttu-id="51fa3-127">**>= 255：** 255</span><span class="sxs-lookup"><span data-stu-id="51fa3-127">**>=255:** 255</span></span><br /><br /> <span data-ttu-id="51fa3-128"><255：实际长度\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="51fa3-128">**<255:** actual *len*</span></span>|  
|`BIGCHAR`|<span data-ttu-id="51fa3-129">**NULL：** 0</span><span class="sxs-lookup"><span data-stu-id="51fa3-129">**NULL:** 0</span></span><br /><br /> <span data-ttu-id="51fa3-130">**ZERO：** 255</span><span class="sxs-lookup"><span data-stu-id="51fa3-130">**ZERO:** 255</span></span><br /><br /> <span data-ttu-id="51fa3-131">**>= 255：** 255</span><span class="sxs-lookup"><span data-stu-id="51fa3-131">**>=255:** 255</span></span><br /><br /> <span data-ttu-id="51fa3-132">**<255：** 255</span><span class="sxs-lookup"><span data-stu-id="51fa3-132">**<255:** 255</span></span>|  
|`BIGBINARY`|<span data-ttu-id="51fa3-133">**NULL：** 0</span><span class="sxs-lookup"><span data-stu-id="51fa3-133">**NULL:** 0</span></span><br /><br /> <span data-ttu-id="51fa3-134">**ZERO：** 255</span><span class="sxs-lookup"><span data-stu-id="51fa3-134">**ZERO:** 255</span></span><br /><br /> <span data-ttu-id="51fa3-135">**>= 255：** 255</span><span class="sxs-lookup"><span data-stu-id="51fa3-135">**>=255:** 255</span></span><br /><br /> <span data-ttu-id="51fa3-136">**<255：** 255</span><span class="sxs-lookup"><span data-stu-id="51fa3-136">**<255:** 255</span></span>|  
|`BIGVARBINARY`|<span data-ttu-id="51fa3-137">**NULL：** 0</span><span class="sxs-lookup"><span data-stu-id="51fa3-137">**NULL:** 0</span></span><br /><br /> <span data-ttu-id="51fa3-138">**零：** 1</span><span class="sxs-lookup"><span data-stu-id="51fa3-138">**ZERO:** 1</span></span><br /><br /> <span data-ttu-id="51fa3-139">**>= 255：** 255</span><span class="sxs-lookup"><span data-stu-id="51fa3-139">**>=255:** 255</span></span><br /><br /> <span data-ttu-id="51fa3-140"><255：实际长度\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="51fa3-140">**<255:** actual *len*</span></span>|  
|`NCHAR`|<span data-ttu-id="51fa3-141">**NULL：** 0</span><span class="sxs-lookup"><span data-stu-id="51fa3-141">**NULL:** 0</span></span><br /><br /> <span data-ttu-id="51fa3-142">**ZERO：** 255</span><span class="sxs-lookup"><span data-stu-id="51fa3-142">**ZERO:** 255</span></span><br /><br /> <span data-ttu-id="51fa3-143">**>= 255：** 255</span><span class="sxs-lookup"><span data-stu-id="51fa3-143">**>=255:** 255</span></span><br /><br /> <span data-ttu-id="51fa3-144">**<255：** 255</span><span class="sxs-lookup"><span data-stu-id="51fa3-144">**<255:** 255</span></span>|  
|`NVARCHAR`|<span data-ttu-id="51fa3-145">**NULL：** 0</span><span class="sxs-lookup"><span data-stu-id="51fa3-145">**NULL:** 0</span></span><br /><br /> <span data-ttu-id="51fa3-146">**零：** 1</span><span class="sxs-lookup"><span data-stu-id="51fa3-146">**ZERO:** 1</span></span><br /><br /> <span data-ttu-id="51fa3-147">**>= 255：** 255</span><span class="sxs-lookup"><span data-stu-id="51fa3-147">**>=255:** 255</span></span><br /><br /> <span data-ttu-id="51fa3-148"><255：实际长度\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="51fa3-148">**<255:** actual *len*</span></span>|  
|`NTEXT`|<span data-ttu-id="51fa3-149">**NULL：** -1</span><span class="sxs-lookup"><span data-stu-id="51fa3-149">**NULL:** -1</span></span><br /><br /> <span data-ttu-id="51fa3-150">**ZERO：**-1</span><span class="sxs-lookup"><span data-stu-id="51fa3-150">**ZERO:** -1</span></span><br /><br /> <span data-ttu-id="51fa3-151">**>= 255：** -1</span><span class="sxs-lookup"><span data-stu-id="51fa3-151">**>=255:** -1</span></span><br /><br /> <span data-ttu-id="51fa3-152">**<255：** -1</span><span class="sxs-lookup"><span data-stu-id="51fa3-152">**<255:** -1</span></span>|  
  
 <span data-ttu-id="51fa3-153">\*   实际长度  = 多字节字符串 (cch) 的长度\*\*</span><span class="sxs-lookup"><span data-stu-id="51fa3-153">\*   actual *len* = Length of multibyte character string (cch)</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="51fa3-154">备注</span><span class="sxs-lookup"><span data-stu-id="51fa3-154">Remarks</span></span>  
 <span data-ttu-id="51fa3-155">每个远程存储过程参数都具有实际数据长度和最大数据长度。</span><span class="sxs-lookup"><span data-stu-id="51fa3-155">Each remote stored procedure parameter has an actual and a maximum data length.</span></span> <span data-ttu-id="51fa3-156">对于不允许使用 Null 值的标准固定长度数据类型，实际长度和最大长度相同。</span><span class="sxs-lookup"><span data-stu-id="51fa3-156">For standard fixed-length data types that do not allow null values, the actual and maximum lengths are the same.</span></span> <span data-ttu-id="51fa3-157">对于可变长度数据类型，长度可以变化。</span><span class="sxs-lookup"><span data-stu-id="51fa3-157">For variable-length data types, the lengths can vary.</span></span> <span data-ttu-id="51fa3-158">例如，声明为 `varchar(30)` 的参数可以具有长度仅为 10 个字节的数据。</span><span class="sxs-lookup"><span data-stu-id="51fa3-158">For example, a parameter declared as `varchar(30)` can have data that is only 10 bytes long.</span></span> <span data-ttu-id="51fa3-159">该参数的实际长度为 10，最大长度为 30。</span><span class="sxs-lookup"><span data-stu-id="51fa3-159">The parameter's actual length is 10 and its maximum length is 30.</span></span> <span data-ttu-id="51fa3-160">srv_paramlen 函数获取远程存储过程的实际数据长度（以字节为单位）\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="51fa3-160">The **srv_paramlen** function gets the actual data length, in bytes, of a remote stored procedure.</span></span> <span data-ttu-id="51fa3-161">要获取参数的最大数据长度，请使用 srv_parammaxlen\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="51fa3-161">To obtain the maximum data length of a parameter, use **srv_parammaxlen**.</span></span>  
  
 <span data-ttu-id="51fa3-162">使用参数调用远程存储过程时，可以按名称或位置（未命名）传递参数。</span><span class="sxs-lookup"><span data-stu-id="51fa3-162">When a remote stored procedure call is made with parameters, the parameters can be passed either by name or by position (unnamed).</span></span> <span data-ttu-id="51fa3-163">如果使用部分按名称传递，部分按位置传递的参数调用远程存储过程，则会发生错误。</span><span class="sxs-lookup"><span data-stu-id="51fa3-163">If the remote stored procedure call is made with some parameters passed by name and some passed by position, an error occurs.</span></span> <span data-ttu-id="51fa3-164">仍调用 SRV_RPC 处理程序，但它似乎没有参数并且**srv_rpcparams**返回0。</span><span class="sxs-lookup"><span data-stu-id="51fa3-164">The SRV_RPC handler is still called, but it appears as if there were no parameters and **srv_rpcparams** returns 0.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="51fa3-165">应全面检查扩展存储过程的源代码，并在生产服务器中安装编译的 DLL 之前，对这些 DLL 进行测试。</span><span class="sxs-lookup"><span data-stu-id="51fa3-165">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="51fa3-166">有关安全检查和测试的信息，请访问此 [Microsoft 网站](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)。</span><span class="sxs-lookup"><span data-stu-id="51fa3-166">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51fa3-167">另请参阅</span><span class="sxs-lookup"><span data-stu-id="51fa3-167">See Also</span></span>  
 <span data-ttu-id="51fa3-168">[扩展存储过程 API srv_paraminfo &#40;&#41;](srv-paraminfo-extended-stored-procedure-api.md) </span><span class="sxs-lookup"><span data-stu-id="51fa3-168">[srv_paraminfo &#40;Extended Stored Procedure API&#41;](srv-paraminfo-extended-stored-procedure-api.md) </span></span>  
 [<span data-ttu-id="51fa3-169">srv_rpcparams（扩展存储过程 API）</span><span class="sxs-lookup"><span data-stu-id="51fa3-169">srv_rpcparams &#40;Extended Stored Procedure API&#41;</span></span>](srv-rpcparams-extended-stored-procedure-api.md)  
  
  
