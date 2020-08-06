---
title: srv_paramset（扩展存储过程 API）| Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_paramset
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_paramset
ms.assetid: 2a509206-a1b8-4b20-b0a2-ef680cef7bd8
author: rothja
ms.author: jroth
ms.openlocfilehash: 9ebe308e5e0c8fc24382582fb71db2f48c77541e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578211"
---
# <a name="srv_paramset-extended-stored-procedure-api"></a><span data-ttu-id="60c6c-102">srv_paramset（扩展存储过程 API）</span><span class="sxs-lookup"><span data-stu-id="60c6c-102">srv_paramset (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]<span data-ttu-id="60c6c-103">请改用 CLR 集成。</span><span class="sxs-lookup"><span data-stu-id="60c6c-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="60c6c-104">设置远程存储过程调用返回参数的值。</span><span class="sxs-lookup"><span data-stu-id="60c6c-104">Sets the value of a remote stored procedure call return parameter.</span></span> <span data-ttu-id="60c6c-105">此函数已被 srv_paramsetoutput 函数取代\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="60c6c-105">This function has been superseded by the **srv_paramsetoutput** function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60c6c-106">语法</span><span class="sxs-lookup"><span data-stu-id="60c6c-106">Syntax</span></span>  
  
```  
  
int srv_paramset (  
SRV_PROC *  
srvproc  
,  
int  
n  
,   
void *  
data  
,  
int  
len   
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="60c6c-107">参数</span><span class="sxs-lookup"><span data-stu-id="60c6c-107">Arguments</span></span>  
 <span data-ttu-id="60c6c-108">srvproc\*\*</span><span class="sxs-lookup"><span data-stu-id="60c6c-108">*srvproc*</span></span>  
 <span data-ttu-id="60c6c-109">指向作为特定客户端连接句柄（在这里为接收远程存储过程调用的句柄）的 SRV_PROC 结构的指针。</span><span class="sxs-lookup"><span data-stu-id="60c6c-109">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection (in this case, the handle that received the remote stored procedure call).</span></span> <span data-ttu-id="60c6c-110">该结构包含扩展存储过程 API 库用于管理应用程序和客户端之间的通信和数据的信息。</span><span class="sxs-lookup"><span data-stu-id="60c6c-110">The structure contains information the Extended Stored Procedure API library uses to manage communication and data between the application and the client.</span></span>  
  
 <span data-ttu-id="60c6c-111">*n*</span><span class="sxs-lookup"><span data-stu-id="60c6c-111">*n*</span></span>  
 <span data-ttu-id="60c6c-112">指示要设置的参数的编号。</span><span class="sxs-lookup"><span data-stu-id="60c6c-112">Indicates the number of the parameter to set.</span></span> <span data-ttu-id="60c6c-113">第一个参数是 1。</span><span class="sxs-lookup"><span data-stu-id="60c6c-113">The first parameter is 1.</span></span>  
  
 <span data-ttu-id="60c6c-114">*data*</span><span class="sxs-lookup"><span data-stu-id="60c6c-114">*data*</span></span>  
 <span data-ttu-id="60c6c-115">是指向要发送回客户端的数据值的指针，该数据值将作为远程存储过程返回参数。</span><span class="sxs-lookup"><span data-stu-id="60c6c-115">Is a pointer to the data value to be sent back to the client as the remote stored procedure return parameter.</span></span>  
  
 <span data-ttu-id="60c6c-116">*长度*</span><span class="sxs-lookup"><span data-stu-id="60c6c-116">*len*</span></span>  
 <span data-ttu-id="60c6c-117">指定要返回的数据的实际长度。</span><span class="sxs-lookup"><span data-stu-id="60c6c-117">Specifies the actual length of the data to be returned.</span></span> <span data-ttu-id="60c6c-118">如果参数的数据类型的长度为常量且该数据类型不允许 null 值（例如 srvbit 或 srvint1），则将会忽略 len\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="60c6c-118">If the data type of the parameter is of a constant length and does not allow null values (for example, *srvbit* or *srvint1*), *len* is ignored.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="60c6c-119">返回</span><span class="sxs-lookup"><span data-stu-id="60c6c-119">Returns</span></span>  
 <span data-ttu-id="60c6c-120">如果参数值设置成功，则返回 SUCCEED，否则返回 FAIL。</span><span class="sxs-lookup"><span data-stu-id="60c6c-120">SUCCEED if the parameter value was successfully set; otherwise, FAIL.</span></span> <span data-ttu-id="60c6c-121">如果属于以下情况则返回 FAIL：无当前远程存储过程、没有第 n 个远程存储过程参数、参数不是返回参数以及 len 参数是非法的\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="60c6c-121">FAIL is returned when there is no current remote stored procedure, when there is no *n*th remote stored procedure parameter, when the parameter is not a return parameter, and when the *len* argument is not legal.</span></span>  
  
 <span data-ttu-id="60c6c-122">如果 len 为 0，则返回 NULL\*\*。</span><span class="sxs-lookup"><span data-stu-id="60c6c-122">If *len*is 0, it returns NULL.</span></span> <span data-ttu-id="60c6c-123">将 len 设置为 0 是将 NULL 返回给客户端的唯一方法\*\*。</span><span class="sxs-lookup"><span data-stu-id="60c6c-123">Setting *len* to 0 is the only way to return NULL to the client.</span></span>  
  
 <span data-ttu-id="60c6c-124">如果参数是数据类型之一，则此函数返回以下值 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="60c6c-124">This function returns the following values, if the parameter is one of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] data types.</span></span>  
  
|<span data-ttu-id="60c6c-125">新数据类型</span><span class="sxs-lookup"><span data-stu-id="60c6c-125">New data types</span></span>|<span data-ttu-id="60c6c-126">返回数据长度</span><span class="sxs-lookup"><span data-stu-id="60c6c-126">Return data length</span></span>|  
|--------------------|------------------------|  
|`BITN`|<span data-ttu-id="60c6c-127">**NULL：** *len* = 0, data = IG, RET = 0</span><span class="sxs-lookup"><span data-stu-id="60c6c-127">**NULL:** *len* = 0, data = IG, RET = 0</span></span><br /><br /> <span data-ttu-id="60c6c-128">**ZERO：** N/A</span><span class="sxs-lookup"><span data-stu-id="60c6c-128">**ZERO:** N/A</span></span><br /><br /> <span data-ttu-id="60c6c-129">**>= 255：** 不适用</span><span class="sxs-lookup"><span data-stu-id="60c6c-129">**>=255:** N/A</span></span><br /><br /> <span data-ttu-id="60c6c-130">**<255：** 不适用</span><span class="sxs-lookup"><span data-stu-id="60c6c-130">**<255:** N/A</span></span>|  
|`BIGVARCHAR`|<span data-ttu-id="60c6c-131">**NULL：** *len* = 0, data = IG, RET = 1</span><span class="sxs-lookup"><span data-stu-id="60c6c-131">**NULL:** *len* = 0, data = IG, RET = 1</span></span><br /><br /> <span data-ttu-id="60c6c-132">**ZERO：** *len* = IG, data = IG, RET = 0</span><span class="sxs-lookup"><span data-stu-id="60c6c-132">**ZERO:** *len* = IG, data = IG, RET = 0</span></span><br /><br /> <span data-ttu-id="60c6c-133">**>=255：** *len* = max8k, data = valid, RET = 0</span><span class="sxs-lookup"><span data-stu-id="60c6c-133">**>=255:** *len* = max8k, data = valid, RET = 0</span></span><br /><br /> <span data-ttu-id="60c6c-134">**<255：** *len* = <8k, data = valid, RET = 1</span><span class="sxs-lookup"><span data-stu-id="60c6c-134">**<255:** *len* = <8k, data = valid, RET = 1</span></span>|  
|`BIGCHAR`|<span data-ttu-id="60c6c-135">**NULL：** *len* = 0, data = IG, RET = 1</span><span class="sxs-lookup"><span data-stu-id="60c6c-135">**NULL:** *len* = 0, data = IG, RET = 1</span></span><br /><br /> <span data-ttu-id="60c6c-136">**ZERO：** *len* = IG, data = IG, RET = 0</span><span class="sxs-lookup"><span data-stu-id="60c6c-136">**ZERO:** *len* = IG, data = IG, RET = 0</span></span><br /><br /> <span data-ttu-id="60c6c-137">**>=255：** *len* = max8k, data = valid, RET = 0</span><span class="sxs-lookup"><span data-stu-id="60c6c-137">**>=255:** *len* = max8k, data = valid, RET = 0</span></span><br /><br /> <span data-ttu-id="60c6c-138">**<255：** *len* = <8k, data = valid, RET = 1</span><span class="sxs-lookup"><span data-stu-id="60c6c-138">**<255:** *len* = <8k, data = valid, RET = 1</span></span>|  
|`BIGBINARY`|<span data-ttu-id="60c6c-139">**NULL：** *len* = 0, data = IG, RET = 1</span><span class="sxs-lookup"><span data-stu-id="60c6c-139">**NULL:** *len* = 0, data = IG, RET = 1</span></span><br /><br /> <span data-ttu-id="60c6c-140">**ZERO：** *len* = IG, data = IG, RET = 0</span><span class="sxs-lookup"><span data-stu-id="60c6c-140">**ZERO:** *len* = IG, data = IG, RET = 0</span></span><br /><br /> <span data-ttu-id="60c6c-141">**>=255：** *len* = max8k, data = valid, RET = 0</span><span class="sxs-lookup"><span data-stu-id="60c6c-141">**>=255:** *len* = max8k, data = valid, RET = 0</span></span><br /><br /> <span data-ttu-id="60c6c-142">**<255：** *len* = <8k, data = valid, RET = 1</span><span class="sxs-lookup"><span data-stu-id="60c6c-142">**<255:** *len* = <8k, data = valid, RET = 1</span></span>|  
|`BIGVARBINARY`|<span data-ttu-id="60c6c-143">**NULL：** *len* = 0, data = IG, RET = 1</span><span class="sxs-lookup"><span data-stu-id="60c6c-143">**NULL:** *len* = 0, data = IG, RET = 1</span></span><br /><br /> <span data-ttu-id="60c6c-144">**ZERO：** *len* = IG, data = IG, RET = 0</span><span class="sxs-lookup"><span data-stu-id="60c6c-144">**ZERO:** *len* = IG, data = IG, RET = 0</span></span><br /><br /> <span data-ttu-id="60c6c-145">**>=255：** *len* = max8k, data = valid, RET = 0</span><span class="sxs-lookup"><span data-stu-id="60c6c-145">**>=255:** *len* = max8k, data = valid, RET = 0</span></span><br /><br /> <span data-ttu-id="60c6c-146">**<255：** *len* = <8k, data = valid, RET = 1</span><span class="sxs-lookup"><span data-stu-id="60c6c-146">**<255:** *len* = <8k, data = valid, RET = 1</span></span>|  
|<span data-ttu-id="60c6c-147">NCHAR</span><span class="sxs-lookup"><span data-stu-id="60c6c-147">NCHAR</span></span>|<span data-ttu-id="60c6c-148">**NULL：** *len* = 0, data = IG, RET = 1</span><span class="sxs-lookup"><span data-stu-id="60c6c-148">**NULL:** *len* = 0, data = IG, RET = 1</span></span><br /><br /> <span data-ttu-id="60c6c-149">**ZERO：** *len* = IG, data = IG, RET = 0</span><span class="sxs-lookup"><span data-stu-id="60c6c-149">**ZERO:** *len* = IG, data = IG, RET = 0</span></span><br /><br /> <span data-ttu-id="60c6c-150">**>=255：** *len* = max8k, data = valid, RET = 0</span><span class="sxs-lookup"><span data-stu-id="60c6c-150">**>=255:** *len* = max8k, data = valid, RET = 0</span></span><br /><br /> <span data-ttu-id="60c6c-151">**<255：** *len* = <8k, data = valid, RET = 1</span><span class="sxs-lookup"><span data-stu-id="60c6c-151">**<255:** *len* = <8k, data = valid, RET = 1</span></span>|  
|<span data-ttu-id="60c6c-152">NVARCHAR</span><span class="sxs-lookup"><span data-stu-id="60c6c-152">NVARCHAR</span></span>|<span data-ttu-id="60c6c-153">**NULL：** *len* = 0, data = IG, RET = 1</span><span class="sxs-lookup"><span data-stu-id="60c6c-153">**NULL:** *len* = 0, data = IG, RET = 1</span></span><br /><br /> <span data-ttu-id="60c6c-154">**ZERO：** *len* = IG, data = IG, RET = 0</span><span class="sxs-lookup"><span data-stu-id="60c6c-154">**ZERO:** *len* = IG, data = IG, RET = 0</span></span><br /><br /> <span data-ttu-id="60c6c-155">**>=255：** *len* = max8k, data = valid, RET = 0</span><span class="sxs-lookup"><span data-stu-id="60c6c-155">**>=255:** *len* = max8k, data = valid, RET = 0</span></span><br /><br /> <span data-ttu-id="60c6c-156">**<255：** *len* = <8k, data = valid, RET = 1</span><span class="sxs-lookup"><span data-stu-id="60c6c-156">**<255:** *len* = <8k, data = valid, RET = 1</span></span>|  
|`NTEXT`|<span data-ttu-id="60c6c-157">**NULL：** *len* = IG, data = IG, RET = 0</span><span class="sxs-lookup"><span data-stu-id="60c6c-157">**NULL:** *len* = IG, data = IG, RET = 0</span></span><br /><br /> <span data-ttu-id="60c6c-158">**ZERO：** *len* = IG, data = IG, RET = 0</span><span class="sxs-lookup"><span data-stu-id="60c6c-158">**ZERO:** *len* = IG, data = IG, RET = 0</span></span><br /><br /> <span data-ttu-id="60c6c-159">**>=255：** *len* = IG, data = IG, RET = 0</span><span class="sxs-lookup"><span data-stu-id="60c6c-159">**>=255:** *len* = IG, data = IG, RET = 0</span></span><br /><br /> <span data-ttu-id="60c6c-160">\*\* \< 255：\*\* *len* = IG，data = IG，RET = 0</span><span class="sxs-lookup"><span data-stu-id="60c6c-160">**\<255:** *len* = IG, data = IG, RET = 0</span></span>|  
|<span data-ttu-id="60c6c-161">RET = srv_paramset 的返回值</span><span class="sxs-lookup"><span data-stu-id="60c6c-161">RET = Return value of srv_paramset</span></span>||  
|<span data-ttu-id="60c6c-162">IG = 将忽略值</span><span class="sxs-lookup"><span data-stu-id="60c6c-162">IG = Value will be ignored</span></span>||  
|<span data-ttu-id="60c6c-163">valid = 任何有效的数据指针</span><span class="sxs-lookup"><span data-stu-id="60c6c-163">valid = Any valid pointer to data</span></span>||  
  
## <a name="remarks"></a><span data-ttu-id="60c6c-164">备注</span><span class="sxs-lookup"><span data-stu-id="60c6c-164">Remarks</span></span>  
 <span data-ttu-id="60c6c-165">参数包含通过远程存储过程在客户端和应用程序之间传递的数据。</span><span class="sxs-lookup"><span data-stu-id="60c6c-165">Parameters contain data passed between clients and the application with remote stored procedures.</span></span> <span data-ttu-id="60c6c-166">客户端可以指定某些参数作为返回参数。</span><span class="sxs-lookup"><span data-stu-id="60c6c-166">The client can specify certain parameters as return parameters.</span></span> <span data-ttu-id="60c6c-167">这些返回参数可包含开放式数据服务服务器应用程序传递回客户端的值。</span><span class="sxs-lookup"><span data-stu-id="60c6c-167">These return parameters can contain values that the Open Data Services server application passes back to the client.</span></span> <span data-ttu-id="60c6c-168">使用返回参数类似于通过引用传递参数。</span><span class="sxs-lookup"><span data-stu-id="60c6c-168">Using return parameters is analogous to passing parameters by reference.</span></span>  
  
 <span data-ttu-id="60c6c-169">不能设置未作为返回参数调用的参数的返回值。</span><span class="sxs-lookup"><span data-stu-id="60c6c-169">You cannot set the return value for a parameter that wasn't invoked as a return parameter.</span></span> <span data-ttu-id="60c6c-170">可以使用 srv_paramstatus 来确定参数的调用方式\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="60c6c-170">You can use **srv_paramstatus** to determine how the parameter was invoked.</span></span>  
  
 <span data-ttu-id="60c6c-171">此函数会为参数设置返回值，但它不会向客户端实际发送返回值。</span><span class="sxs-lookup"><span data-stu-id="60c6c-171">This function sets the return value for a parameter but it does not actually send the return value to the client.</span></span> <span data-ttu-id="60c6c-172">在设置了状态标记 SRV_DONE_FINAL 的情况下调用 srv_senddone 时，所有返回参数（无论是否使用 srv_paramset 设置了返回值）都会自动发送到客户端\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="60c6c-172">All return parameters, whether their return values have been set with **srv_paramset** or not, are automatically sent to the client when **srv_senddone** is called with the status flag SRV_DONE_FINAL set.</span></span>  
  
 <span data-ttu-id="60c6c-173">使用参数调用远程存储过程时，可以按名称或位置（未命名）传递参数。</span><span class="sxs-lookup"><span data-stu-id="60c6c-173">When a remote stored procedure call is made with parameters, the parameters can be passed either by name or by position (unnamed).</span></span> <span data-ttu-id="60c6c-174">如果使用部分按名称传递，部分按位置传递的参数调用远程存储过程，则会发生错误。</span><span class="sxs-lookup"><span data-stu-id="60c6c-174">If the remote stored procedure call is made with some parameters passed by name and some passed by position, an error occurs.</span></span> <span data-ttu-id="60c6c-175">仍然会调用 SRV_RPC 处理程序，但是它看起来没有参数并且 srv_rpcparams 返回 0\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="60c6c-175">The SRV_RPC handler is still called, but it appears as if there were no parameters, and **srv_rpcparams** returns 0.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="60c6c-176">应全面检查扩展存储过程的源代码，并在生产服务器中安装编译的 DLL 之前，对这些 DLL 进行测试。</span><span class="sxs-lookup"><span data-stu-id="60c6c-176">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="60c6c-177">有关安全检查和测试的信息，请访问此 [Microsoft 网站](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)。</span><span class="sxs-lookup"><span data-stu-id="60c6c-177">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60c6c-178">另请参阅</span><span class="sxs-lookup"><span data-stu-id="60c6c-178">See Also</span></span>  
 [<span data-ttu-id="60c6c-179">srv_paramsetoutput（扩展存储过程 API）</span><span class="sxs-lookup"><span data-stu-id="60c6c-179">srv_paramsetoutput &#40;Extended Stored Procedure API&#41;</span></span>](srv-paramsetoutput-extended-stored-procedure-api.md)  
  
  
