---
title: srv_describe（扩展存储过程 API）| Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_describe
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_describe
ms.assetid: 2115600e-5ce7-4be0-9cd3-a1dd1fab0729
author: rothja
ms.author: jroth
ms.openlocfilehash: 52a397b79f4fcecaa2ccacde7500cb852ae793fd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590809"
---
# <a name="srv_describe-extended-stored-procedure-api"></a><span data-ttu-id="6314f-102">srv_describe（扩展存储过程 API）</span><span class="sxs-lookup"><span data-stu-id="6314f-102">srv_describe (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]<span data-ttu-id="6314f-103">请改用 CLR 集成。</span><span class="sxs-lookup"><span data-stu-id="6314f-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="6314f-104">定义行中特定列的列名以及源数据类型和目标数据类型。</span><span class="sxs-lookup"><span data-stu-id="6314f-104">Defines the column name and source and destination data types for a specific column in a row.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6314f-105">语法</span><span class="sxs-lookup"><span data-stu-id="6314f-105">Syntax</span></span>  
  
```  
  
int srv_describe (  
SRV_PROC *  
srvproc  
,  
int  
colnumber  
,  
DBCHAR *  
column_name  
,  
int  
namelen  
,  
DBINT  
desttype  
,  
DBINT  
destlen  
,  
DBINT  
srctype  
,  
DBINT  
srclen  
,  
void *  
srcdata  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="6314f-106">参数</span><span class="sxs-lookup"><span data-stu-id="6314f-106">Arguments</span></span>  
 <span data-ttu-id="6314f-107">srvproc\*\*</span><span class="sxs-lookup"><span data-stu-id="6314f-107">*srvproc*</span></span>  
 <span data-ttu-id="6314f-108">指向作为特定客户端连接（在本例中为发送相应行的客户端）句柄的 SRV_PROC 结构的指针。</span><span class="sxs-lookup"><span data-stu-id="6314f-108">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection (in this case, the client sending the row).</span></span> <span data-ttu-id="6314f-109">该结构包含扩展存储过程 API 库用于管理应用程序和客户端之间的通信和数据的所有信息。</span><span class="sxs-lookup"><span data-stu-id="6314f-109">The structure contains all the information that the Extended Stored Procedure API library uses to manage communications and data between the application and the client.</span></span>  
  
 <span data-ttu-id="6314f-110">colnumber\*\*</span><span class="sxs-lookup"><span data-stu-id="6314f-110">*colnumber*</span></span>  
 <span data-ttu-id="6314f-111">当前不受支持。</span><span class="sxs-lookup"><span data-stu-id="6314f-111">Is currently not supported.</span></span> <span data-ttu-id="6314f-112">必须按顺序描述列。</span><span class="sxs-lookup"><span data-stu-id="6314f-112">Columns must be described in order.</span></span> <span data-ttu-id="6314f-113">必须在调用 srv_sendrow 之前对所有列进行描述\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6314f-113">All columns must be described before **srv_sendrow** is called.</span></span>  
  
 <span data-ttu-id="6314f-114">column_name</span><span class="sxs-lookup"><span data-stu-id="6314f-114">*column_name*</span></span>  
 <span data-ttu-id="6314f-115">指定数据所属列的名称。</span><span class="sxs-lookup"><span data-stu-id="6314f-115">Specifies the name of the column to which the data belongs.</span></span> <span data-ttu-id="6314f-116">该参数可以为 NULL，因为列不是必须要有名称。</span><span class="sxs-lookup"><span data-stu-id="6314f-116">This parameter can be NULL because a column is not required to have a name.</span></span>  
  
 <span data-ttu-id="6314f-117">namelen\*\*</span><span class="sxs-lookup"><span data-stu-id="6314f-117">*namelen*</span></span>  
 <span data-ttu-id="6314f-118">指定 column_name 的长度（以字节为单位）\*\*。</span><span class="sxs-lookup"><span data-stu-id="6314f-118">Specifies the length, in bytes, of *column_name*.</span></span> <span data-ttu-id="6314f-119">如果 namelen 为 SRV_NULLTERM，则 column_name 必须以 Null 值终止\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6314f-119">If *namelen* is SRV_NULLTERM, then *column_name* must be null-terminated.</span></span>  
  
 <span data-ttu-id="6314f-120">desttype\*\*</span><span class="sxs-lookup"><span data-stu-id="6314f-120">*desttype*</span></span>  
 <span data-ttu-id="6314f-121">指定目标行列的数据类型。</span><span class="sxs-lookup"><span data-stu-id="6314f-121">Specifies the data type of the destination row column.</span></span> <span data-ttu-id="6314f-122">这是发送到客户端的数据类型。</span><span class="sxs-lookup"><span data-stu-id="6314f-122">This is the data type sent to the client.</span></span> <span data-ttu-id="6314f-123">即使数据为 NULL，也必须指定数据类型。有关详细信息，请参阅[数据类型（扩展存储过程 API）](data-types-extended-stored-procedure-api.md)。</span><span class="sxs-lookup"><span data-stu-id="6314f-123">The data type must be specified even if the data is NULL, for more information, see [Data Types &#40;Extended Stored Procedure API&#41;](data-types-extended-stored-procedure-api.md).</span></span>  
  
 <span data-ttu-id="6314f-124">destlen\*\*</span><span class="sxs-lookup"><span data-stu-id="6314f-124">*destlen*</span></span>  
 <span data-ttu-id="6314f-125">指定要发送到客户端的数据的长度（单位为字节）。</span><span class="sxs-lookup"><span data-stu-id="6314f-125">Specifies the length, in bytes, of the data to be sent to the client.</span></span> <span data-ttu-id="6314f-126">对于不允许使用 Null 值的固定长度的数据类型，将忽略 destlen\*\*。</span><span class="sxs-lookup"><span data-stu-id="6314f-126">For fixed-length data types that do not allow null values, *destlen* is ignored.</span></span> <span data-ttu-id="6314f-127">对于可变长度的数据类型和允许使用 Null 值的固定长度的数据类型，destlen 指定目标数据可以达到的最大长度\*\*。</span><span class="sxs-lookup"><span data-stu-id="6314f-127">For variable-length data types and fixed-length data types that allow null values, *destlen* specifies the maximum length the destination data can be.</span></span>  
  
 <span data-ttu-id="6314f-128">srctype\*\*</span><span class="sxs-lookup"><span data-stu-id="6314f-128">*srctype*</span></span>  
 <span data-ttu-id="6314f-129">指定源数据的数据类型。</span><span class="sxs-lookup"><span data-stu-id="6314f-129">Specifies the data type of the source data.</span></span>  
  
 <span data-ttu-id="6314f-130">srclen\*\*</span><span class="sxs-lookup"><span data-stu-id="6314f-130">*srclen*</span></span>  
 <span data-ttu-id="6314f-131">指定源数据的长度（单位为字节）。</span><span class="sxs-lookup"><span data-stu-id="6314f-131">Specifies the length, in bytes, of the source data.</span></span> <span data-ttu-id="6314f-132">对于固定长度数据类型，则忽略该值。</span><span class="sxs-lookup"><span data-stu-id="6314f-132">This value is ignored for fixed-length data types.</span></span>  
  
 <span data-ttu-id="6314f-133">srcdata\*\*</span><span class="sxs-lookup"><span data-stu-id="6314f-133">*srcdata*</span></span>  
 <span data-ttu-id="6314f-134">提供特定列的源数据地址。</span><span class="sxs-lookup"><span data-stu-id="6314f-134">Provides the source data address for a particular column.</span></span> <span data-ttu-id="6314f-135">调用 srv_sendrow 时，它将在 srcdata 处查找 colnumber 的数据\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6314f-135">When **srv_sendrow** is called, it looks for the data for *colnumber* at *srcdata*.</span></span> <span data-ttu-id="6314f-136">因此，在调用 srv_sendrow 前不应释放它\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6314f-136">Therefore it should not be freed before a call to **srv_sendrow**.</span></span> <span data-ttu-id="6314f-137">可以通过使用 srv_setcoldata 在 srv_sendrow 的调用之间更改源数据地址\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6314f-137">The source data address can be changed between calls to **srv_sendrow** by using **srv_setcoldata**.</span></span> <span data-ttu-id="6314f-138">在将列数据替换为对 srv_setcoldata 的其他调用或调用 srv_senddone 之前，不应释放为 srcdata 分配的内存\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6314f-138">Memory allocated for *srcdata* should not be freed until the column data is replaced by another call to **srv_setcoldata**, or until **srv_senddone** is called.</span></span>  
  
 <span data-ttu-id="6314f-139">如果 desttype 为 SRVDECIMAL 或 SRVNUMERIC，则 srcdata 参数必须为指向 DBNUMERIC 或 DBDECIMAL 结构的指针，并且此结构的精度和小数位数字段必须已设置为所需的值\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6314f-139">If *desttype* is SRVDECIMAL or SRVNUMERIC, the *srcdata* parameter must be a pointer to a DBNUMERIC or DBDECIMAL structure with the precision and scale fields of the structure already set to the values you want.</span></span> <span data-ttu-id="6314f-140">您可以使用 DEFAULTPRECISION 指定一个默认精度，使用 DEFAULTSCALE 指定一个默认小数位数。</span><span class="sxs-lookup"><span data-stu-id="6314f-140">You can use DEFAULTPRECISION to specify a default precision, and DEFAULTSCALE to specify a default scale.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="6314f-141">返回</span><span class="sxs-lookup"><span data-stu-id="6314f-141">Returns</span></span>  
 <span data-ttu-id="6314f-142">所描述的列的编号。</span><span class="sxs-lookup"><span data-stu-id="6314f-142">The number of the column described.</span></span> <span data-ttu-id="6314f-143">第一列为列 1。</span><span class="sxs-lookup"><span data-stu-id="6314f-143">The first column is column 1.</span></span> <span data-ttu-id="6314f-144">如果出现错误，则返回 0。</span><span class="sxs-lookup"><span data-stu-id="6314f-144">If an error occurs, returns 0.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6314f-145">备注</span><span class="sxs-lookup"><span data-stu-id="6314f-145">Remarks</span></span>  
 <span data-ttu-id="6314f-146">在首次调用 srv_sendrow 之前，必须为行中的每一列调用一次 srv_describe 函数\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6314f-146">The **srv_describe** function must be called once for each column in the row before the first call to **srv_sendrow**.</span></span> <span data-ttu-id="6314f-147">可以按任意顺序描述行的各列。</span><span class="sxs-lookup"><span data-stu-id="6314f-147">The columns of a row can be described in any order.</span></span>  
  
 <span data-ttu-id="6314f-148">若要在发送整个结果集之前更改列行中源数据的位置和长度，请分别使用 srv_setcoldata 和 srv_setcollen\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6314f-148">To change the location and length of the source data in column rows before the complete result set has been sent, use **srv_setcoldata** and **srv_setcollen**, respectively.</span></span>  
  
 <span data-ttu-id="6314f-149">有关数据类型和扩展存储过程 API 数据类型转换的说明，请参阅[数据类型（扩展存储过程 API）](data-types-extended-stored-procedure-api.md)。</span><span class="sxs-lookup"><span data-stu-id="6314f-149">For a description of data types and Extended Store Procedure API data type conversions, see[Data Types &#40;Extended Stored Procedure API&#41;](data-types-extended-stored-procedure-api.md).</span></span>  
  
 <span data-ttu-id="6314f-150">如果应用程序中的列名为 Unicode 格式，则在调用 srv_describe 前需要将该列名转换为服务器的多字节代码页\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6314f-150">If the column name in your application is in Unicode, you need to convert it to the multibyte code page of the server before calling **srv_describe**.</span></span> <span data-ttu-id="6314f-151">有关详细信息，请参阅[Unicode 数据和服务器代码页](../extended-stored-procedures-programming/unicode-data-and-server-code-pages.md)。</span><span class="sxs-lookup"><span data-stu-id="6314f-151">For more information, see [Unicode Data and Server Code Pages](../extended-stored-procedures-programming/unicode-data-and-server-code-pages.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="6314f-152">应全面检查扩展存储过程的源代码，并在生产服务器中安装编译的 DLL 之前，对这些 DLL 进行测试。</span><span class="sxs-lookup"><span data-stu-id="6314f-152">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="6314f-153">有关安全检查和测试的信息，请访问此 [Microsoft 网站](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)。</span><span class="sxs-lookup"><span data-stu-id="6314f-153">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6314f-154">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6314f-154">See Also</span></span>  
 <span data-ttu-id="6314f-155">[扩展存储过程 API srv_sendrow &#40;&#41;](srv-sendrow-extended-stored-procedure-api.md) </span><span class="sxs-lookup"><span data-stu-id="6314f-155">[srv_sendrow &#40;Extended Stored Procedure API&#41;](srv-sendrow-extended-stored-procedure-api.md) </span></span>  
 <span data-ttu-id="6314f-156">[扩展存储过程 API srv_setutype &#40;&#41;](srv-setutype-extended-stored-procedure-api.md) </span><span class="sxs-lookup"><span data-stu-id="6314f-156">[srv_setutype &#40;Extended Stored Procedure API&#41;](srv-setutype-extended-stored-procedure-api.md) </span></span>  
 [<span data-ttu-id="6314f-157">srv_setcoldata（扩展存储过程 API）</span><span class="sxs-lookup"><span data-stu-id="6314f-157">srv_setcoldata &#40;Extended Stored Procedure API&#41;</span></span>](srv-setcoldata-extended-stored-procedure-api.md)  
  
  
