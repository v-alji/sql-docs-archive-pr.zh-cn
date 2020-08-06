---
title: srv_convert（扩展存储过程 API）| Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_convert
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_convert
ms.assetid: 216b4a31-786e-4361-8a33-e5f6e9790f90
author: rothja
ms.author: jroth
ms.openlocfilehash: 30a0ea356f017ed3d1b3ecc85cf483b4553e120a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590810"
---
# <a name="srv_convert-extended-stored-procedure-api"></a><span data-ttu-id="e8f1c-102">srv_convert（扩展存储过程 API）</span><span class="sxs-lookup"><span data-stu-id="e8f1c-102">srv_convert (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]<span data-ttu-id="e8f1c-103">请改用 CLR 集成。</span><span class="sxs-lookup"><span data-stu-id="e8f1c-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="e8f1c-104">将数据从一个数据类型更改为另一数据类型。</span><span class="sxs-lookup"><span data-stu-id="e8f1c-104">Changes data from one data type to another.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8f1c-105">语法</span><span class="sxs-lookup"><span data-stu-id="e8f1c-105">Syntax</span></span>  
  
```  
  
int srv_convert (  
SRV_PROC *  
srvproc  
,  
int  
srctype  
,  
void *  
src  
,  
DBINT  
srclen  
,  
int  
desttype  
,  
void *  
dest  
,  
DBINT  
destlen  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="e8f1c-106">参数</span><span class="sxs-lookup"><span data-stu-id="e8f1c-106">Arguments</span></span>  
 <span data-ttu-id="e8f1c-107">srvproc\*\*</span><span class="sxs-lookup"><span data-stu-id="e8f1c-107">*srvproc*</span></span>  
 <span data-ttu-id="e8f1c-108">指向作为特定客户端连接句柄的 SRV_PROC 结构的指针。</span><span class="sxs-lookup"><span data-stu-id="e8f1c-108">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection.</span></span> <span data-ttu-id="e8f1c-109">该结构包含扩展存储过程 API 用于管理应用程序和客户端之间的通信和数据的所有控制信息。</span><span class="sxs-lookup"><span data-stu-id="e8f1c-109">The structure contains all the control information that the Extended Stored Procedure API uses to manage communications and data between the application and the client.</span></span> <span data-ttu-id="e8f1c-110">如果提供了 srvproc 句柄，在发生错误时它则会被传递给扩展存储过程 API 错误处理程序函数\*\*。</span><span class="sxs-lookup"><span data-stu-id="e8f1c-110">If the *srvproc* handle is supplied, it is passed to the Extended Stored Procedure API error handler function when an error occurs.</span></span>  
  
 <span data-ttu-id="e8f1c-111">srctype\*\*</span><span class="sxs-lookup"><span data-stu-id="e8f1c-111">*srctype*</span></span>  
 <span data-ttu-id="e8f1c-112">指定要转换的数据的数据类型。</span><span class="sxs-lookup"><span data-stu-id="e8f1c-112">Specifies the data type of the data to be converted.</span></span> <span data-ttu-id="e8f1c-113">该参数可以为任意一种扩展存储过程 API 数据类型。</span><span class="sxs-lookup"><span data-stu-id="e8f1c-113">This parameter can be any of the Extended Store Procedure API data types.</span></span>  
  
 <span data-ttu-id="e8f1c-114">*src*</span><span class="sxs-lookup"><span data-stu-id="e8f1c-114">*src*</span></span>  
 <span data-ttu-id="e8f1c-115">指向要转换的数据的指针。</span><span class="sxs-lookup"><span data-stu-id="e8f1c-115">Is a pointer to the data to be converted.</span></span> <span data-ttu-id="e8f1c-116">该参数可以为任意一种扩展存储过程 API 数据类型。</span><span class="sxs-lookup"><span data-stu-id="e8f1c-116">This parameter can be any of the Extended Store Procedure API data types.</span></span>  
  
 <span data-ttu-id="e8f1c-117">srclen\*\*</span><span class="sxs-lookup"><span data-stu-id="e8f1c-117">*srclen*</span></span>  
 <span data-ttu-id="e8f1c-118">指定要转换的数据的长度（单位为字节）。</span><span class="sxs-lookup"><span data-stu-id="e8f1c-118">Specifies the length, in bytes, of the data to be converted.</span></span> <span data-ttu-id="e8f1c-119">如果 srclen 为 0，srv_convert 将向目标变量中放入一个 Null 值\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e8f1c-119">If *srclen* is 0, **srv_convert** places a null value in the destination variable.</span></span> <span data-ttu-id="e8f1c-120">除非它为 0，否则对于固定长度数据类型，会忽略该参数，在这种情况下会假定源数据为 NULL。</span><span class="sxs-lookup"><span data-stu-id="e8f1c-120">Unless it is 0, this parameter is ignored for fixed-length data types, in which case the source data is assumed to be NULL.</span></span> <span data-ttu-id="e8f1c-121">对于 SRVCHAR 数据类型的数据，长度为 -1 表示字符串以 Null 值结束。</span><span class="sxs-lookup"><span data-stu-id="e8f1c-121">For data of the SRVCHAR data type, a length of -1 indicates the string is null-terminated.</span></span>  
  
 <span data-ttu-id="e8f1c-122">desttype\*\*</span><span class="sxs-lookup"><span data-stu-id="e8f1c-122">*desttype*</span></span>  
 <span data-ttu-id="e8f1c-123">指示要将源转换为何种数据类型。</span><span class="sxs-lookup"><span data-stu-id="e8f1c-123">Specifies the data type to convert the source to.</span></span> <span data-ttu-id="e8f1c-124">该参数可以为任意一种扩展存储过程 API 数据类型。</span><span class="sxs-lookup"><span data-stu-id="e8f1c-124">This parameter can be any of the Extended Store Procedure API data types.</span></span>  
  
 <span data-ttu-id="e8f1c-125">*目的*</span><span class="sxs-lookup"><span data-stu-id="e8f1c-125">*dest*</span></span>  
 <span data-ttu-id="e8f1c-126">指向接收转换后的数据的目标变量的指针。</span><span class="sxs-lookup"><span data-stu-id="e8f1c-126">Is a pointer to the destination variable that receives converted data.</span></span> <span data-ttu-id="e8f1c-127">如果该指针为 NULL，srv_convert 将调用用户提供的错误处理程序（如果有的话），并返回 -1\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e8f1c-127">If this pointer is NULL, **srv_convert** calls the user-supplied error handler ,if any, and returns -1.</span></span>  
  
 <span data-ttu-id="e8f1c-128">如果 desttype 为 SRVDECIMAL 或 SRVNUMERIC，则 dest 参数必须为指向 DBNUMERIC 或 DBDECIMAL 结构的指针，并且此结构的精度和小数位数字段必须已设置为所需的值\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e8f1c-128">If *desttype* is SRVDECIMAL or SRVNUMERIC, the *dest* parameter must be a pointer to a DBNUMERIC or DBDECIMAL structure with the precision and scale fields of the structure already set to the desired values.</span></span> <span data-ttu-id="e8f1c-129">您可以使用 DEFAULTPRECISION 指定一个默认精度，使用 DEFAULTSCALE 指定一个默认小数位数。</span><span class="sxs-lookup"><span data-stu-id="e8f1c-129">You can use DEFAULTPRECISION to specify a default precision, and DEFAULTSCALE to specify a default scale.</span></span>  
  
 <span data-ttu-id="e8f1c-130">destlen\*\*</span><span class="sxs-lookup"><span data-stu-id="e8f1c-130">*destlen*</span></span>  
 <span data-ttu-id="e8f1c-131">指定目标变量的长度（单位为字节）。</span><span class="sxs-lookup"><span data-stu-id="e8f1c-131">Specifies the length, in bytes, of the destination variable.</span></span> <span data-ttu-id="e8f1c-132">对于固定长度数据类型，则会忽略该参数。</span><span class="sxs-lookup"><span data-stu-id="e8f1c-132">This parameter is ignored for fixed-length data types.</span></span> <span data-ttu-id="e8f1c-133">对于 SRVCHAR 类型的目标变量，destlen 的值必须为目标缓冲区空间的总长度\*\*。</span><span class="sxs-lookup"><span data-stu-id="e8f1c-133">For a destination variable of type SRVCHAR, the value of *destlen* must be the total length of the destination buffer space.</span></span> <span data-ttu-id="e8f1c-134">SRVCHAR 或 SRVBINARY 类型的目标变量的长度为 -1 时，表示有足够的可用空间。</span><span class="sxs-lookup"><span data-stu-id="e8f1c-134">A length of -1 for a destination variable of type SRVCHAR or SRVBINARY indicates there is sufficient space available.</span></span> <span data-ttu-id="e8f1c-135">对于 srvchar 类型的目标变量，长度为 -1 将使字符串以 Null 值终止\*\*。</span><span class="sxs-lookup"><span data-stu-id="e8f1c-135">For a destination variable of type *srvchar*, a length of -1 causes the character string to be null-terminated.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="e8f1c-136">返回</span><span class="sxs-lookup"><span data-stu-id="e8f1c-136">Returns</span></span>  
 <span data-ttu-id="e8f1c-137">如果数据类型转换成功，则返回转换后的数据的长度（单位为字节）。</span><span class="sxs-lookup"><span data-stu-id="e8f1c-137">The length of the converted data, in bytes, if the data type conversion succeeds.</span></span> <span data-ttu-id="e8f1c-138">当 srv_convert 遇到它不支持的转换请求时，它将调用开发人员提供的错误处理程序（如果有），设置全局错误号，并返回 -1\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e8f1c-138">When **srv_convert** encounters a request for a conversion it does not support, it calls the developer-supplied error handler, if any, sets a global error number, and returns -1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e8f1c-139">备注</span><span class="sxs-lookup"><span data-stu-id="e8f1c-139">Remarks</span></span>  
 <span data-ttu-id="e8f1c-140">srv_willconvert 函数决定是否允许进行特定转换\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e8f1c-140">The **srv_willconvert** function determines whether a particular conversion is allowed.</span></span>  
  
 <span data-ttu-id="e8f1c-141">转换为近似的数字数据类型 SRVFLT4 或 SRVFLT8 可能会造成一定的精度损失。</span><span class="sxs-lookup"><span data-stu-id="e8f1c-141">Converting to the approximate numeric data types SRVFLT4 or SRVFLT8 can result in some loss of precision.</span></span> <span data-ttu-id="e8f1c-142">从近似的数字数据类型 SRVFLT4 或 SRVFLT8 转换为 SRVCHAR 或 SRVTEXT 也可能造成一定的精度损失。</span><span class="sxs-lookup"><span data-stu-id="e8f1c-142">Converting from the approximate numeric data types SRVFLT4 or SRVFLT8 to SRVCHAR or SRVTEXT can also result in some loss of precision.</span></span>  
  
 <span data-ttu-id="e8f1c-143">转换为 SRVFLT*x*、SRVINT*x*、SRVMONEY、SRVMONEY4、SRVDECIMAL 或 SRVNUMERIC 时，如果数字大于目标的最大值，则可能导致溢出，如果数字小于目标的最小值，则可能导致下溢。</span><span class="sxs-lookup"><span data-stu-id="e8f1c-143">Converting to SRVFLT*x*, SRVINT*x*, SRVMONEY, SRVMONEY4, SRVDECIMAL, or SRVNUMERIC can result in overflow if the number is larger than the maximum value of the destination, or in underflow if the number is smaller than the minimum value of the destination.</span></span> <span data-ttu-id="e8f1c-144">如果在转换为 SRVCHAR 或 SRVTEXT 时发生上溢，则所得值的第一个字符将包含一个星号 (\*)，以指示出错。</span><span class="sxs-lookup"><span data-stu-id="e8f1c-144">If overflow occurs when converting to SRVCHAR or SRVTEXT, the first character of the resulting value contains an asterisk (\*) to indicate the error.</span></span>  
  
 <span data-ttu-id="e8f1c-145">将 SRVCHAR 转换为 SRVBINARY 时，srv_convert 将 SRVCHAR 解释为十六进制，无论字符串是否包含前导 0 都是如此\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e8f1c-145">When converting SRVCHAR to SRVBINARY, **srv_convert** interprets SRVCHAR as hexadecimal, whether or not the string contains a leading 0.</span></span> <span data-ttu-id="e8f1c-146">将 SRVBINARY 转换为 SRVCHAR 时，srv_convert 将创建一个不带前导 0 的十六进制字符串\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e8f1c-146">When converting SRVBINARY to SRVCHAR, **srv_convert** creates a hexadecimal string without a leading 0.</span></span> <span data-ttu-id="e8f1c-147">在所有其他情况下，以 SRVBINARY 数据类型为目标类型或源类型的转换都是直接逐位复制。</span><span class="sxs-lookup"><span data-stu-id="e8f1c-147">In all other cases, a conversion to or from the SRVBINARY data type is a straight bit-copy.</span></span>  
  
 <span data-ttu-id="e8f1c-148">在某些情况下，将数据类型转换为自身可能比较有用。</span><span class="sxs-lookup"><span data-stu-id="e8f1c-148">In certain cases, it can be useful to convert a data type to itself.</span></span> <span data-ttu-id="e8f1c-149">例如，将 SRVCHAR 转换为 destlen 为 -1 的 SRVCHAR 将向字符串添加一个 Null 终止符\*\*。</span><span class="sxs-lookup"><span data-stu-id="e8f1c-149">For example, converting SRVCHAR to SRVCHAR with a *destlen* of -1 adds a null terminator to a string.</span></span>  
  
 <span data-ttu-id="e8f1c-150">有关数据类型和扩展存储过程 API 数据类型转换的说明，请参阅[数据类型（扩展存储过程 API）](data-types-extended-stored-procedure-api.md)。</span><span class="sxs-lookup"><span data-stu-id="e8f1c-150">For a description of data types and Extended Store Procedure API data type conversions, see [Data Types &#40;Extended Stored Procedure API&#41;](data-types-extended-stored-procedure-api.md).</span></span>  
  
 <span data-ttu-id="e8f1c-151">srv_convert 函数可能会因以下几种原因失败\*\*\*\*：</span><span class="sxs-lookup"><span data-stu-id="e8f1c-151">The **srv_convert** function can fail for several reasons:</span></span>  
  
-   <span data-ttu-id="e8f1c-152">请求的转换不可用。</span><span class="sxs-lookup"><span data-stu-id="e8f1c-152">The requested conversion is not available.</span></span>  
  
-   <span data-ttu-id="e8f1c-153">转换导致目标变量出现截断、上溢或精度损失。</span><span class="sxs-lookup"><span data-stu-id="e8f1c-153">The conversion resulted in truncation, overflow, or loss of precision in the destination variable.</span></span>  
  
-   <span data-ttu-id="e8f1c-154">将字符串转换为数字数据类型时出现语法错误。</span><span class="sxs-lookup"><span data-stu-id="e8f1c-154">A syntax error occurred while converting a character string to a numeric data type.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="e8f1c-155">应全面检查扩展存储过程的源代码，并在生产服务器中安装编译的 DLL 之前，对这些 DLL 进行测试。</span><span class="sxs-lookup"><span data-stu-id="e8f1c-155">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="e8f1c-156">有关安全检查和测试的信息，请访问此 [Microsoft 网站](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)。</span><span class="sxs-lookup"><span data-stu-id="e8f1c-156">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8f1c-157">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e8f1c-157">See Also</span></span>  
 <span data-ttu-id="e8f1c-158">[扩展存储过程 API srv_setutype &#40;&#41;](srv-setutype-extended-stored-procedure-api.md) </span><span class="sxs-lookup"><span data-stu-id="e8f1c-158">[srv_setutype &#40;Extended Stored Procedure API&#41;](srv-setutype-extended-stored-procedure-api.md) </span></span>  
 [<span data-ttu-id="e8f1c-159">srv_willconvert（扩展存储过程 API）</span><span class="sxs-lookup"><span data-stu-id="e8f1c-159">srv_willconvert &#40;Extended Stored Procedure API&#41;</span></span>](srv-willconvert-extended-stored-procedure-api.md)  
  
  
