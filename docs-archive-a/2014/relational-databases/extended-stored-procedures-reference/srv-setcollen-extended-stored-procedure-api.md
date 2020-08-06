---
title: srv_setcollen（扩展存储过程 API）| Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_setcollen
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_setcollen
ms.assetid: 3c60f1c3-4562-463a-a259-12df172788bd
author: rothja
ms.author: jroth
ms.openlocfilehash: 8e3023e2ac239e074656329da7d8af3aba3afa88
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688916"
---
# <a name="srv_setcollen-extended-stored-procedure-api"></a><span data-ttu-id="1e93b-102">srv_setcollen（扩展存储过程 API）</span><span class="sxs-lookup"><span data-stu-id="1e93b-102">srv_setcollen (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]<span data-ttu-id="1e93b-103">请改用 CLR 集成。</span><span class="sxs-lookup"><span data-stu-id="1e93b-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="1e93b-104">指定长度可变的列或允许 NULL 值的列的当前数据长度（以字节为单位）。</span><span class="sxs-lookup"><span data-stu-id="1e93b-104">Specifies the current data length in bytes of a variable-length column or a column that allows NULL values.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e93b-105">语法</span><span class="sxs-lookup"><span data-stu-id="1e93b-105">Syntax</span></span>  
  
```  
  
int srv_setcollen (  
SRV_PROC *  
srvproc  
,  
int   
column  
,  
int  
len   
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="1e93b-106">参数</span><span class="sxs-lookup"><span data-stu-id="1e93b-106">Arguments</span></span>  
 <span data-ttu-id="1e93b-107">srvproc\*\*</span><span class="sxs-lookup"><span data-stu-id="1e93b-107">*srvproc*</span></span>  
 <span data-ttu-id="1e93b-108">指向作为特定客户端连接句柄的 SRV_PROC 结构的指针。</span><span class="sxs-lookup"><span data-stu-id="1e93b-108">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection.</span></span> <span data-ttu-id="1e93b-109">该结构包含扩展存储过程 API 库用于管理应用程序和客户端之间的通信和数据的信息。</span><span class="sxs-lookup"><span data-stu-id="1e93b-109">The structure contains information the Extended Stored Procedure API library uses to manage communication and data between the application and the client.</span></span>  
  
 <span data-ttu-id="1e93b-110">*column*</span><span class="sxs-lookup"><span data-stu-id="1e93b-110">*column*</span></span>  
 <span data-ttu-id="1e93b-111">指示指定其数据长度的列的编号。</span><span class="sxs-lookup"><span data-stu-id="1e93b-111">Indicates the number of the column for which the data length is being specified.</span></span> <span data-ttu-id="1e93b-112">列的编号从 1 开始。</span><span class="sxs-lookup"><span data-stu-id="1e93b-112">Columns are numbered beginning with 1.</span></span>  
  
 <span data-ttu-id="1e93b-113">*长度*</span><span class="sxs-lookup"><span data-stu-id="1e93b-113">*len*</span></span>  
 <span data-ttu-id="1e93b-114">指示列数据的长度（以字节为单位）。</span><span class="sxs-lookup"><span data-stu-id="1e93b-114">Indicates the length, in bytes, of the column data.</span></span> <span data-ttu-id="1e93b-115">长度为 0 表示列数据值为 Null。</span><span class="sxs-lookup"><span data-stu-id="1e93b-115">A length of 0 means the column data value is null.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="1e93b-116">返回</span><span class="sxs-lookup"><span data-stu-id="1e93b-116">Returns</span></span>  
 <span data-ttu-id="1e93b-117">SUCCEED 或 FAIL。</span><span class="sxs-lookup"><span data-stu-id="1e93b-117">SUCCEED or FAIL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1e93b-118">备注</span><span class="sxs-lookup"><span data-stu-id="1e93b-118">Remarks</span></span>  
 <span data-ttu-id="1e93b-119">必须首先使用 srv_describe 定义行的每个列\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1e93b-119">Each column of the row must first be defined with **srv_describe**.</span></span> <span data-ttu-id="1e93b-120">列数据长度通过对 srv_describe 或 srv_setcollen 的最后一次调用进行设置\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1e93b-120">The column data length is set by the last call to **srv_describe** or **srv_setcollen**.</span></span> <span data-ttu-id="1e93b-121">如果某一行长度可变的数据（以 Null 值结束的数据）发生更改，必须使用 srv_setcollen 将该数据设置为新的长度，然后才能调用 srv_sendrow\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1e93b-121">If variable-length data (null-terminated data) changes for a row, **srv_setcollen** must be used to set it to the new length before calling **srv_sendrow**.</span></span> <span data-ttu-id="1e93b-122">对于允许 Null 值的列，必须已调用 srv_describe，并将 desttype 设置为允许 Null 值的数据类型（如 SRVINTN），NULL 数据的指定方法是：调用 srv_setcollen 并将 len 设置为 0\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1e93b-122">For a column that allows null values, **srv_describe** must have been called with *desttype* set to a data type that allows nulls (like SRVINTN) and null data is specified by calling **srv_setcollen** with *len* set to 0.</span></span> <span data-ttu-id="1e93b-123">不能使用扩展存储过程 API 指定长度为零的数据。</span><span class="sxs-lookup"><span data-stu-id="1e93b-123">Zero length data cannot be specified using the Extended Stored Procedure API.</span></span>  
  
 <span data-ttu-id="1e93b-124">请注意，当列数据类型的长度可变时，则不检查 len\*\*。</span><span class="sxs-lookup"><span data-stu-id="1e93b-124">Note that when the data type of the column is variable-length, *len* is not checked.</span></span> <span data-ttu-id="1e93b-125">如果调用固定长度的列，该函数则返回 FAIL。</span><span class="sxs-lookup"><span data-stu-id="1e93b-125">This function returns FAIL if called for a fixed-length column.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="1e93b-126">应全面检查扩展存储过程的源代码，并在生产服务器中安装编译的 DLL 之前，对这些 DLL 进行测试。</span><span class="sxs-lookup"><span data-stu-id="1e93b-126">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="1e93b-127">有关安全检查和测试的信息，请访问此 [Microsoft 网站](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)。</span><span class="sxs-lookup"><span data-stu-id="1e93b-127">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e93b-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1e93b-128">See Also</span></span>  
 [<span data-ttu-id="1e93b-129">srv_describe（扩展存储过程 API）</span><span class="sxs-lookup"><span data-stu-id="1e93b-129">srv_describe &#40;Extended Stored Procedure API&#41;</span></span>](srv-describe-extended-stored-procedure-api.md)  
  
  
