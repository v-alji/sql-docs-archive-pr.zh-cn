---
title: srv_paramdata（扩展存储过程 API）| Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_paramdata
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_paramdata
ms.assetid: 3104514d-b404-47c9-b6d7-928106384874
author: rothja
ms.author: jroth
ms.openlocfilehash: 092ca5b811a12c3e6b199a6041ce6e4f8e02f4b7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589090"
---
# <a name="srv_paramdata-extended-stored-procedure-api"></a><span data-ttu-id="31d68-102">srv_paramdata（扩展存储过程 API）</span><span class="sxs-lookup"><span data-stu-id="31d68-102">srv_paramdata (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]<span data-ttu-id="31d68-103">请改用 CLR 集成。</span><span class="sxs-lookup"><span data-stu-id="31d68-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="31d68-104">返回远程存储过程调用参数的值。</span><span class="sxs-lookup"><span data-stu-id="31d68-104">Returns the value of a remote stored procedure call parameter.</span></span> <span data-ttu-id="31d68-105">此函数已被 srv_paraminfo 函数取代\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="31d68-105">This function has been superseded by the **srv_paraminfo** function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31d68-106">语法</span><span class="sxs-lookup"><span data-stu-id="31d68-106">Syntax</span></span>  
  
```  
  
void * srv_paramdata (  
SRV_PROC *  
srvproc  
,  
int  
n   
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="31d68-107">自变量</span><span class="sxs-lookup"><span data-stu-id="31d68-107">Arguments</span></span>  
 <span data-ttu-id="31d68-108">srvproc\*\*</span><span class="sxs-lookup"><span data-stu-id="31d68-108">*srvproc*</span></span>  
 <span data-ttu-id="31d68-109">指向作为特定客户端连接句柄（在这里为接收远程存储过程调用的句柄）的 SRV_PROC 结构的指针。</span><span class="sxs-lookup"><span data-stu-id="31d68-109">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection (in this case, the handle that received the remote stored procedure call).</span></span> <span data-ttu-id="31d68-110">该结构包含扩展存储过程库用于管理应用程序和客户端之间的通信和数据的信息。</span><span class="sxs-lookup"><span data-stu-id="31d68-110">The structure contains information the Extended Stored Procedure library uses to manage communication and data between the application and the client.</span></span>  
  
 <span data-ttu-id="31d68-111">*n*</span><span class="sxs-lookup"><span data-stu-id="31d68-111">*n*</span></span>  
 <span data-ttu-id="31d68-112">表示参数的编号。</span><span class="sxs-lookup"><span data-stu-id="31d68-112">Is the number of the parameter.</span></span> <span data-ttu-id="31d68-113">第一个参数的编号为 1。</span><span class="sxs-lookup"><span data-stu-id="31d68-113">The first parameter is number 1.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="31d68-114">返回</span><span class="sxs-lookup"><span data-stu-id="31d68-114">Returns</span></span>  
 <span data-ttu-id="31d68-115">一个指向参数值的指针。</span><span class="sxs-lookup"><span data-stu-id="31d68-115">A pointer to the parameter value.</span></span> <span data-ttu-id="31d68-116">如果第 n 个参数为 NULL，则没有第 n 个参数，或者没有任何远程存储过程，并返回 NULL\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="31d68-116">If the *n*th parameter is NULL, there is no *n*th parameter, or there is no remote stored procedure, returns NULL.</span></span> <span data-ttu-id="31d68-117">如果参数值为字符串，则不能以 Null 值结束。</span><span class="sxs-lookup"><span data-stu-id="31d68-117">If the parameter value is a string, it might not be null-terminated.</span></span> <span data-ttu-id="31d68-118">使用 srv_paramlen 确定字符串的长度\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="31d68-118">Use **srv_paramlen** to determine the length of the string.</span></span>  
  
 <span data-ttu-id="31d68-119">如果参数是数据类型之一，则此函数返回以下值 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="31d68-119">This function returns the following values, if the parameter is one of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types.</span></span> <span data-ttu-id="31d68-120">指针数据包括数据类型的指针是否为有效 (VP)、NULL 或不适用 (N/A)，以及指向的数据内容。</span><span class="sxs-lookup"><span data-stu-id="31d68-120">Pointer data includes whether the pointer for the data type is valid (VP), NULL, or not applicable (N/A), and the contents of the data pointed to.</span></span>  
  
|<span data-ttu-id="31d68-121">新数据类型</span><span class="sxs-lookup"><span data-stu-id="31d68-121">New data types</span></span>|<span data-ttu-id="31d68-122">输入数据长度</span><span class="sxs-lookup"><span data-stu-id="31d68-122">Input data length</span></span>|  
|--------------------|-----------------------|  
|<span data-ttu-id="31d68-123">BITN</span><span class="sxs-lookup"><span data-stu-id="31d68-123">BITN</span></span>|<span data-ttu-id="31d68-124">**NULL：VP、NULL**</span><span class="sxs-lookup"><span data-stu-id="31d68-124">**NULL:** VP, NULL</span></span><br /><br /> <span data-ttu-id="31d68-125">**ZERO：VP、NULL**</span><span class="sxs-lookup"><span data-stu-id="31d68-125">**ZERO:** VP, NULL</span></span><br /><br /> <span data-ttu-id="31d68-126">**>= 255：** 不适用</span><span class="sxs-lookup"><span data-stu-id="31d68-126">**>=255:** N/A</span></span><br /><br /> <span data-ttu-id="31d68-127">**<255：** 不适用</span><span class="sxs-lookup"><span data-stu-id="31d68-127">**<255:** N/A</span></span>|  
|<span data-ttu-id="31d68-128">BIGVARCHAR</span><span class="sxs-lookup"><span data-stu-id="31d68-128">BIGVARCHAR</span></span>|<span data-ttu-id="31d68-129">**NULL：NULL、N/A**</span><span class="sxs-lookup"><span data-stu-id="31d68-129">**NULL:** NULL, N/A</span></span><br /><br /> <span data-ttu-id="31d68-130">**ZERO：VP、NULL**</span><span class="sxs-lookup"><span data-stu-id="31d68-130">**ZERO:** VP, NULL</span></span><br /><br /> <span data-ttu-id="31d68-131">**>=255：VP、255 个字符**</span><span class="sxs-lookup"><span data-stu-id="31d68-131">**>=255:** VP, 255 chars</span></span><br /><br /> <span data-ttu-id="31d68-132"><255：VP、实际数据\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="31d68-132">**<255:** VP, actual data</span></span>|  
|<span data-ttu-id="31d68-133">BIGCHAR</span><span class="sxs-lookup"><span data-stu-id="31d68-133">BIGCHAR</span></span>|<span data-ttu-id="31d68-134">**NULL：NULL、N/A**</span><span class="sxs-lookup"><span data-stu-id="31d68-134">**NULL:** NULL, N/A</span></span><br /><br /> <span data-ttu-id="31d68-135">**ZERO：VP、255 个空格**</span><span class="sxs-lookup"><span data-stu-id="31d68-135">**ZERO:** VP, 255 spaces</span></span><br /><br /> <span data-ttu-id="31d68-136">**>=255：VP、255 个字符**</span><span class="sxs-lookup"><span data-stu-id="31d68-136">**>=255:** VP, 255 chars</span></span><br /><br /> <span data-ttu-id="31d68-137"><255：VP、实际数据加填充字符（最多 255 个）\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="31d68-137">**<255:** VP, actual data + padding (up to 255)</span></span>|  
|<span data-ttu-id="31d68-138">BIGBINARY</span><span class="sxs-lookup"><span data-stu-id="31d68-138">BIGBINARY</span></span>|<span data-ttu-id="31d68-139">**NULL：NULL、N/A**</span><span class="sxs-lookup"><span data-stu-id="31d68-139">**NULL:** NULL, N/A</span></span><br /><br /> <span data-ttu-id="31d68-140">**ZERO：VP、255 0x00**</span><span class="sxs-lookup"><span data-stu-id="31d68-140">**ZERO:** VP, 255 0x00</span></span><br /><br /> <span data-ttu-id="31d68-141">**>=255：VP、255 个字节**</span><span class="sxs-lookup"><span data-stu-id="31d68-141">**>=255:** VP, 255 bytes</span></span><br /><br /> <span data-ttu-id="31d68-142"><255：VP、实际数据加填充字符（最多 255 个）\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="31d68-142">**<255:** VP, actual data + padding (up to 255)</span></span>|  
|<span data-ttu-id="31d68-143">BIGVARBINARY</span><span class="sxs-lookup"><span data-stu-id="31d68-143">BIGVARBINARY</span></span>|<span data-ttu-id="31d68-144">**NULL：NULL、N/A**</span><span class="sxs-lookup"><span data-stu-id="31d68-144">**NULL:** NULL, N/A</span></span><br /><br /> <span data-ttu-id="31d68-145">**ZERO：VP、0x00**</span><span class="sxs-lookup"><span data-stu-id="31d68-145">**ZERO:** VP, 0x00</span></span><br /><br /> <span data-ttu-id="31d68-146">**>=255：VP、255 个字节**</span><span class="sxs-lookup"><span data-stu-id="31d68-146">**>=255:** VP, 255 bytes</span></span><br /><br /> <span data-ttu-id="31d68-147"><255：VP、实际数据\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="31d68-147">**<255:** VP, actual data</span></span>|  
|<span data-ttu-id="31d68-148">NCHAR</span><span class="sxs-lookup"><span data-stu-id="31d68-148">NCHAR</span></span>|<span data-ttu-id="31d68-149">**NULL：NULL、N/A**</span><span class="sxs-lookup"><span data-stu-id="31d68-149">**NULL:** NULL, N/A</span></span><br /><br /> <span data-ttu-id="31d68-150">**ZERO：VP、255 个空格**</span><span class="sxs-lookup"><span data-stu-id="31d68-150">**ZERO:** VP, 255 spaces</span></span><br /><br /> <span data-ttu-id="31d68-151">**>=255：VP、255 个字符**</span><span class="sxs-lookup"><span data-stu-id="31d68-151">**>=255:** VP, 255 chars</span></span><br /><br /> <span data-ttu-id="31d68-152"><255：VP、实际数据加填充字符（最多 255 个）\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="31d68-152">**<255:** VP, actual data + padding (up to 255)</span></span>|  
|<span data-ttu-id="31d68-153">NVARCHAR</span><span class="sxs-lookup"><span data-stu-id="31d68-153">NVARCHAR</span></span>|<span data-ttu-id="31d68-154">**NULL：NULL、N/A**</span><span class="sxs-lookup"><span data-stu-id="31d68-154">**NULL:** NULL, N/A</span></span><br /><br /> <span data-ttu-id="31d68-155">**ZERO：VP、NULL**</span><span class="sxs-lookup"><span data-stu-id="31d68-155">**ZERO:** VP, NULL</span></span><br /><br /> <span data-ttu-id="31d68-156">**>=255：VP、255 个字符**</span><span class="sxs-lookup"><span data-stu-id="31d68-156">**>=255:** VP, 255 chars</span></span><br /><br /> <span data-ttu-id="31d68-157"><255：VP、实际数据\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="31d68-157">**<255:** VP, actual data</span></span>|  
|<span data-ttu-id="31d68-158">NTEXT</span><span class="sxs-lookup"><span data-stu-id="31d68-158">NTEXT</span></span>|<span data-ttu-id="31d68-159">**NULL：N/A**</span><span class="sxs-lookup"><span data-stu-id="31d68-159">**NULL:** N/A</span></span><br /><br /> <span data-ttu-id="31d68-160">**ZERO：** N/A</span><span class="sxs-lookup"><span data-stu-id="31d68-160">**ZERO:** N/A</span></span><br /><br /> <span data-ttu-id="31d68-161">**>= 255：** 不适用</span><span class="sxs-lookup"><span data-stu-id="31d68-161">**>=255:** N/A</span></span><br /><br /> <span data-ttu-id="31d68-162">\*\* \< 255：\*\* 暂缺</span><span class="sxs-lookup"><span data-stu-id="31d68-162">**\<255:** N/A</span></span>|  
  
 <span data-ttu-id="31d68-163">\*   数据不能以 Null 值结束；截断 255 个字符以外的字符时不会发出警告。</span><span class="sxs-lookup"><span data-stu-id="31d68-163">\*   data is not null-terminated; no warning is issued on truncation for data >255 characters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="31d68-164">备注</span><span class="sxs-lookup"><span data-stu-id="31d68-164">Remarks</span></span>  
 <span data-ttu-id="31d68-165">如果知道参数名称，则可以使用 srv_paramnumber 获取参数编号\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="31d68-165">If you know the parameter name, you can use **srv_paramnumber** to get the parameter number.</span></span> <span data-ttu-id="31d68-166">要确定参数是否为 NULL，请使用 srv_paramlen\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="31d68-166">To determine whether a parameter is NULL, use **srv_paramlen**.</span></span>  
  
 <span data-ttu-id="31d68-167">使用参数执行远程存储过程调用时，可以通过名称或位置（未命名）来传递参数。</span><span class="sxs-lookup"><span data-stu-id="31d68-167">When a remote stored procedure call is made with parameters, the parameters can be passed by name or by position (unnamed).</span></span> <span data-ttu-id="31d68-168">如果使用部分按名称传递，部分按位置传递的参数调用远程存储过程，则会发生错误。</span><span class="sxs-lookup"><span data-stu-id="31d68-168">If the remote stored procedure call is made with some parameters passed by name and some passed by position, an error occurs.</span></span> <span data-ttu-id="31d68-169">如果出现错误，仍然会调用 SRV_RPC 处理程序，但是它看起来没有参数并且 srv_rpcparams 返回 0\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="31d68-169">If an error occurs, the SRV_RPC handler is still called, but it appears as if there were no parameters and **srv_rpcparams** returns 0.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="31d68-170">应全面检查扩展存储过程的源代码，并在生产服务器中安装编译的 DLL 之前，对这些 DLL 进行测试。</span><span class="sxs-lookup"><span data-stu-id="31d68-170">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="31d68-171">有关安全检查和测试的信息，请访问此 [Microsoft 网站](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)。</span><span class="sxs-lookup"><span data-stu-id="31d68-171">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31d68-172">另请参阅</span><span class="sxs-lookup"><span data-stu-id="31d68-172">See Also</span></span>  
 [<span data-ttu-id="31d68-173">srv_rpcparams（扩展存储过程 API）</span><span class="sxs-lookup"><span data-stu-id="31d68-173">srv_rpcparams &#40;Extended Stored Procedure API&#41;</span></span>](srv-rpcparams-extended-stored-procedure-api.md)  
  
  
