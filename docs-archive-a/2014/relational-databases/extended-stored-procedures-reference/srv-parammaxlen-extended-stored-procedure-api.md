---
title: srv_parammaxlen（扩展存储过程 API）| Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_parammaxlen
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_parammaxlen
ms.assetid: 49bfc29d-f76a-4963-b0e6-b8532dfda850
author: rothja
ms.author: jroth
ms.openlocfilehash: b289743b3de4b115a67a029dcc0261854ee3a40b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693901"
---
# <a name="srv_parammaxlen-extended-stored-procedure-api"></a><span data-ttu-id="f778a-102">srv_parammaxlen（扩展存储过程 API）</span><span class="sxs-lookup"><span data-stu-id="f778a-102">srv_parammaxlen (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]<span data-ttu-id="f778a-103">请改用 CLR 集成。</span><span class="sxs-lookup"><span data-stu-id="f778a-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="f778a-104">返回远程存储过程调用参数的最大数据长度。</span><span class="sxs-lookup"><span data-stu-id="f778a-104">Returns the maximum data length of a remote stored procedure call parameter.</span></span> <span data-ttu-id="f778a-105">此函数已被 srv_paraminfo 函数取代\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f778a-105">This function has been superseded by the **srv_paraminfo** function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f778a-106">语法</span><span class="sxs-lookup"><span data-stu-id="f778a-106">Syntax</span></span>  
  
```  
  
int srv_parammaxlen (  
SRV_PROC *  
srvproc  
,  
int  
n   
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="f778a-107">参数</span><span class="sxs-lookup"><span data-stu-id="f778a-107">Arguments</span></span>  
 <span data-ttu-id="f778a-108">srvproc\*\*</span><span class="sxs-lookup"><span data-stu-id="f778a-108">*srvproc*</span></span>  
 <span data-ttu-id="f778a-109">指向作为特定客户端连接句柄（在这里为接收远程存储过程调用的句柄）的 SRV_PROC 结构的指针。</span><span class="sxs-lookup"><span data-stu-id="f778a-109">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection (in this case, the handle that received the remote stored procedure call).</span></span> <span data-ttu-id="f778a-110">该结构包含扩展存储过程 API 库用于管理应用程序和客户端之间的通信和数据的信息。</span><span class="sxs-lookup"><span data-stu-id="f778a-110">The structure contains information the Extended Stored Procedure API library uses to manage communication and data between the application and the client.</span></span>  
  
 <span data-ttu-id="f778a-111">*n*</span><span class="sxs-lookup"><span data-stu-id="f778a-111">*n*</span></span>  
 <span data-ttu-id="f778a-112">指示参数的编号。</span><span class="sxs-lookup"><span data-stu-id="f778a-112">Indicates the number of the parameter.</span></span> <span data-ttu-id="f778a-113">第一个参数是 1。</span><span class="sxs-lookup"><span data-stu-id="f778a-113">The first parameter is 1.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="f778a-114">返回</span><span class="sxs-lookup"><span data-stu-id="f778a-114">Returns</span></span>  
 <span data-ttu-id="f778a-115">参数数据的最大长度（以字节为单位）。</span><span class="sxs-lookup"><span data-stu-id="f778a-115">The maximum length, in bytes, of the parameter data.</span></span> <span data-ttu-id="f778a-116">如果没有第 n 个参数或没有任何远程存储过程，则返回 -1\*\*。</span><span class="sxs-lookup"><span data-stu-id="f778a-116">If there is no *n*th parameter or if there is no remote stored procedure, it returns -1.</span></span>  
  
 <span data-ttu-id="f778a-117">如果参数为以下数据类型之一，则此函数返回以下值 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="f778a-117">This function returns the following values, if the parameter is one of the following [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types.</span></span>  
  
|<span data-ttu-id="f778a-118">新数据类型</span><span class="sxs-lookup"><span data-stu-id="f778a-118">New data types</span></span>|<span data-ttu-id="f778a-119">输入数据长度</span><span class="sxs-lookup"><span data-stu-id="f778a-119">Input data length</span></span>|  
|--------------------|-----------------------|  
|`BITN`|<span data-ttu-id="f778a-120">**NULL：** 1</span><span class="sxs-lookup"><span data-stu-id="f778a-120">**NULL:** 1</span></span><br /><br /> <span data-ttu-id="f778a-121">**零：** 1</span><span class="sxs-lookup"><span data-stu-id="f778a-121">**ZERO:** 1</span></span><br /><br /> <span data-ttu-id="f778a-122">**>= 255：** 不适用</span><span class="sxs-lookup"><span data-stu-id="f778a-122">**>=255:** N/A</span></span><br /><br /> <span data-ttu-id="f778a-123">**<255：** 不适用</span><span class="sxs-lookup"><span data-stu-id="f778a-123">**<255:** N/A</span></span>|  
|`BIGVARCHAR`|<span data-ttu-id="f778a-124">**NULL：** 255</span><span class="sxs-lookup"><span data-stu-id="f778a-124">**NULL:** 255</span></span><br /><br /> <span data-ttu-id="f778a-125">**ZERO：** 255</span><span class="sxs-lookup"><span data-stu-id="f778a-125">**ZERO:** 255</span></span><br /><br /> <span data-ttu-id="f778a-126">**>= 255：** 255</span><span class="sxs-lookup"><span data-stu-id="f778a-126">**>=255:** 255</span></span><br /><br /> <span data-ttu-id="f778a-127">**<255：** 255</span><span class="sxs-lookup"><span data-stu-id="f778a-127">**<255:** 255</span></span>|  
|`BIGCHAR`|<span data-ttu-id="f778a-128">**NULL：** 255</span><span class="sxs-lookup"><span data-stu-id="f778a-128">**NULL:** 255</span></span><br /><br /> <span data-ttu-id="f778a-129">**ZERO：** 255</span><span class="sxs-lookup"><span data-stu-id="f778a-129">**ZERO:** 255</span></span><br /><br /> <span data-ttu-id="f778a-130">**>= 255：** 255</span><span class="sxs-lookup"><span data-stu-id="f778a-130">**>=255:** 255</span></span><br /><br /> <span data-ttu-id="f778a-131">**<255：** 255</span><span class="sxs-lookup"><span data-stu-id="f778a-131">**<255:** 255</span></span>|  
|`BIGBINARY`|<span data-ttu-id="f778a-132">**NULL：** 255</span><span class="sxs-lookup"><span data-stu-id="f778a-132">**NULL:** 255</span></span><br /><br /> <span data-ttu-id="f778a-133">**ZERO：** 255</span><span class="sxs-lookup"><span data-stu-id="f778a-133">**ZERO:** 255</span></span><br /><br /> <span data-ttu-id="f778a-134">**>= 255：** 255</span><span class="sxs-lookup"><span data-stu-id="f778a-134">**>=255:** 255</span></span><br /><br /> <span data-ttu-id="f778a-135">**<255：** 255</span><span class="sxs-lookup"><span data-stu-id="f778a-135">**<255:** 255</span></span>|  
|`BIGVARBINARY`|<span data-ttu-id="f778a-136">**NULL：** 255</span><span class="sxs-lookup"><span data-stu-id="f778a-136">**NULL:** 255</span></span><br /><br /> <span data-ttu-id="f778a-137">**ZERO：** 255</span><span class="sxs-lookup"><span data-stu-id="f778a-137">**ZERO:** 255</span></span><br /><br /> <span data-ttu-id="f778a-138">**>= 255：** 255</span><span class="sxs-lookup"><span data-stu-id="f778a-138">**>=255:** 255</span></span><br /><br /> <span data-ttu-id="f778a-139">**<255：** 255</span><span class="sxs-lookup"><span data-stu-id="f778a-139">**<255:** 255</span></span>|  
|`NCHAR`|<span data-ttu-id="f778a-140">**NULL：** 255</span><span class="sxs-lookup"><span data-stu-id="f778a-140">**NULL:** 255</span></span><br /><br /> <span data-ttu-id="f778a-141">**ZERO：** 255</span><span class="sxs-lookup"><span data-stu-id="f778a-141">**ZERO:** 255</span></span><br /><br /> <span data-ttu-id="f778a-142">**>= 255：** 255</span><span class="sxs-lookup"><span data-stu-id="f778a-142">**>=255:** 255</span></span><br /><br /> <span data-ttu-id="f778a-143">**<255：** 255</span><span class="sxs-lookup"><span data-stu-id="f778a-143">**<255:** 255</span></span>|  
|`NVARCHAR`|<span data-ttu-id="f778a-144">**NULL：** 255</span><span class="sxs-lookup"><span data-stu-id="f778a-144">**NULL:** 255</span></span><br /><br /> <span data-ttu-id="f778a-145">**ZERO：** 255</span><span class="sxs-lookup"><span data-stu-id="f778a-145">**ZERO:** 255</span></span><br /><br /> <span data-ttu-id="f778a-146">**>= 255：** 255</span><span class="sxs-lookup"><span data-stu-id="f778a-146">**>=255:** 255</span></span><br /><br /> <span data-ttu-id="f778a-147">**<255：** 255</span><span class="sxs-lookup"><span data-stu-id="f778a-147">**<255:** 255</span></span>|  
|`NTEXT`|<span data-ttu-id="f778a-148">**NULL：** -1</span><span class="sxs-lookup"><span data-stu-id="f778a-148">**NULL:** -1</span></span><br /><br /> <span data-ttu-id="f778a-149">**ZERO：**-1</span><span class="sxs-lookup"><span data-stu-id="f778a-149">**ZERO:** -1</span></span><br /><br /> <span data-ttu-id="f778a-150">**>= 255：** -1</span><span class="sxs-lookup"><span data-stu-id="f778a-150">**>=255:** -1</span></span><br /><br /> <span data-ttu-id="f778a-151">\*\* \< 255：\*\* -1</span><span class="sxs-lookup"><span data-stu-id="f778a-151">**\<255:** -1</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f778a-152">备注</span><span class="sxs-lookup"><span data-stu-id="f778a-152">Remarks</span></span>  
 <span data-ttu-id="f778a-153">每个远程存储过程参数都具有实际数据长度和最大数据长度。</span><span class="sxs-lookup"><span data-stu-id="f778a-153">Each remote stored procedure parameter has an actual and a maximum data length.</span></span> <span data-ttu-id="f778a-154">对于不允许使用 Null 值的标准固定长度数据类型，实际长度和最大长度相同。</span><span class="sxs-lookup"><span data-stu-id="f778a-154">For standard fixed-length data types that do not allow null values, the actual and maximum lengths are the same.</span></span> <span data-ttu-id="f778a-155">对于可变长度数据类型，长度可以变化。</span><span class="sxs-lookup"><span data-stu-id="f778a-155">For variable-length data types, the lengths can vary.</span></span> <span data-ttu-id="f778a-156">例如，声明为 varchar(30) 的参数可以具有长度仅为 10 个字节的数据\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f778a-156">For example, a parameter declared as **varchar(30)** can have data that is only 10 bytes long.</span></span> <span data-ttu-id="f778a-157">该参数的实际长度为 10，最大长度为 30。</span><span class="sxs-lookup"><span data-stu-id="f778a-157">The parameter's actual length is 10 and its maximum length is 30.</span></span> <span data-ttu-id="f778a-158">srv_parammaxlen 函数获取远程存储过程的最大数据长度\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f778a-158">The **srv_parammaxlen** function gets the maximum data length of a remote stored procedure.</span></span> <span data-ttu-id="f778a-159">若要获取参数的实际长度，请使用 srv_paramlen\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f778a-159">To obtain the actual length of a parameter, use **srv_paramlen**.</span></span>  
  
 <span data-ttu-id="f778a-160">使用参数调用远程存储过程时，可以按名称或位置（未命名）传递参数。</span><span class="sxs-lookup"><span data-stu-id="f778a-160">When a remote stored procedure call is made with parameters, the parameters can be passed either by name or by position (unnamed).</span></span> <span data-ttu-id="f778a-161">如果使用部分按名称传递，部分按位置传递的参数调用远程存储过程，则会发生错误。</span><span class="sxs-lookup"><span data-stu-id="f778a-161">If the remote stored procedure call is made with some parameters passed by name and some passed by position, an error occurs.</span></span> <span data-ttu-id="f778a-162">仍然会调用 SRV_RPC 处理程序，但是它看起来没有参数并且 srv_rpcparams 返回 0\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f778a-162">The SRV_RPC handler is still called, but it appears as if there were no parameters, and **srv_rpcparams** returns 0.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="f778a-163">应全面检查扩展存储过程的源代码，并在生产服务器中安装编译的 DLL 之前，对这些 DLL 进行测试。</span><span class="sxs-lookup"><span data-stu-id="f778a-163">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="f778a-164">有关安全检查和测试的信息，请访问此 [Microsoft 网站](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)。</span><span class="sxs-lookup"><span data-stu-id="f778a-164">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f778a-165">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f778a-165">See Also</span></span>  
 <span data-ttu-id="f778a-166">[扩展存储过程 API srv_paraminfo &#40;&#41;](srv-paraminfo-extended-stored-procedure-api.md) </span><span class="sxs-lookup"><span data-stu-id="f778a-166">[srv_paraminfo &#40;Extended Stored Procedure API&#41;](srv-paraminfo-extended-stored-procedure-api.md) </span></span>  
 [<span data-ttu-id="f778a-167">srv_rpcparams（扩展存储过程 API）</span><span class="sxs-lookup"><span data-stu-id="f778a-167">srv_rpcparams &#40;Extended Stored Procedure API&#41;</span></span>](srv-rpcparams-extended-stored-procedure-api.md)  
  
  
