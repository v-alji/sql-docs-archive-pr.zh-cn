---
title: srv_paramsetoutput（扩展存储过程 API）| Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_paramsetoutput
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_paramsetoutput
ms.assetid: f2810e19-e513-458b-8925-5756b6ee1313
author: rothja
ms.author: jroth
ms.openlocfilehash: 2847367fe5d6052728cebf30467b68cb14fb8e63
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578208"
---
# <a name="srv_paramsetoutput-extended-stored-procedure-api"></a><span data-ttu-id="43763-102">srv_paramsetoutput（扩展存储过程 API）</span><span class="sxs-lookup"><span data-stu-id="43763-102">srv_paramsetoutput (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]<span data-ttu-id="43763-103">请改用 CLR 集成。</span><span class="sxs-lookup"><span data-stu-id="43763-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="43763-104">设置返回参数的值。</span><span class="sxs-lookup"><span data-stu-id="43763-104">Sets the value of a return parameter.</span></span> <span data-ttu-id="43763-105">此函数取代了 srv_paramset 函数\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="43763-105">This function supersedes the **srv_paramset** function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43763-106">语法</span><span class="sxs-lookup"><span data-stu-id="43763-106">Syntax</span></span>  
  
```  
  
int srv_paramsetoutput (  
SRV_PROC *  
srvproc  
,  
int  
n  
,  
BYTE *  
pbData  
,  
ULONG   
cbLen  
,  
BOOL  
fNull   
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="43763-107">参数</span><span class="sxs-lookup"><span data-stu-id="43763-107">Arguments</span></span>  
 <span data-ttu-id="43763-108">srvproc\*\*</span><span class="sxs-lookup"><span data-stu-id="43763-108">*srvproc*</span></span>  
 <span data-ttu-id="43763-109">客户端连接的句柄。</span><span class="sxs-lookup"><span data-stu-id="43763-109">Is a handle for a client connection.</span></span>  
  
 <span data-ttu-id="43763-110">*n*</span><span class="sxs-lookup"><span data-stu-id="43763-110">*n*</span></span>  
 <span data-ttu-id="43763-111">要设置的参数的序号。</span><span class="sxs-lookup"><span data-stu-id="43763-111">Is the ordinal number of the parameter to be set.</span></span> <span data-ttu-id="43763-112">第一个参数是 1。</span><span class="sxs-lookup"><span data-stu-id="43763-112">The first parameter is 1.</span></span>  
  
 <span data-ttu-id="43763-113">pbData\*\*</span><span class="sxs-lookup"><span data-stu-id="43763-113">*pbData*</span></span>  
 <span data-ttu-id="43763-114">指向要作为存储返回参数发送回客户端的数据值的指针。</span><span class="sxs-lookup"><span data-stu-id="43763-114">Is a pointer to the data value to be sent back to the client as a procedure return parameter.</span></span>  
  
 <span data-ttu-id="43763-115">cbLen\*\*</span><span class="sxs-lookup"><span data-stu-id="43763-115">*cbLen*</span></span>  
 <span data-ttu-id="43763-116">要返回的数据的实际长度。</span><span class="sxs-lookup"><span data-stu-id="43763-116">Is the actual length of the data to be returned.</span></span> <span data-ttu-id="43763-117">如果参数的数据类型指定了常量长度值且不允许 Null 值（例如 srvbit 或 srvint1），则将会忽略 cbLen\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="43763-117">If the data type of the parameter specifies values of a constant length and does not allow null values (for example, *srvbit* or *srvint1*), *cbLen* is ignored.</span></span> <span data-ttu-id="43763-118">如果 fNull 为 FALSE，值为 0 则表示长度为零的数据\*\*。</span><span class="sxs-lookup"><span data-stu-id="43763-118">A value of 0 signifies zero-length data if *fNull* is FALSE.</span></span>  
  
 <span data-ttu-id="43763-119">fNull\*\*</span><span class="sxs-lookup"><span data-stu-id="43763-119">*fNull*</span></span>  
 <span data-ttu-id="43763-120">指示返回参数的值是否为 NULL 的标志。</span><span class="sxs-lookup"><span data-stu-id="43763-120">Is a flag indicating whether the value of the return parameter is NULL.</span></span> <span data-ttu-id="43763-121">如果应将该参数设置为 NULL，请将此标志设置为 TRUE。</span><span class="sxs-lookup"><span data-stu-id="43763-121">Set this flag to TRUE if the parameter should be set to NULL.</span></span> <span data-ttu-id="43763-122">默认值是 FALSE。</span><span class="sxs-lookup"><span data-stu-id="43763-122">The default value is FALSE.</span></span> <span data-ttu-id="43763-123">如果 fNull 设置为 TRUE，cbLen 应设置为 0，否则该函数将失败\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="43763-123">If *fNull* is set to TRUE, *cbLen* should be set to 0 or the function will fail.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="43763-124">返回</span><span class="sxs-lookup"><span data-stu-id="43763-124">Returns</span></span>  
 <span data-ttu-id="43763-125">如果成功设置了参数信息，则返回 SUCCEED，否则返回 FAIL。</span><span class="sxs-lookup"><span data-stu-id="43763-125">If the parameter information was successfully set, SUCCEED is returned; otherwise, FAIL.</span></span> <span data-ttu-id="43763-126">以下情况下返回 FAIL：</span><span class="sxs-lookup"><span data-stu-id="43763-126">FAIL is returned when</span></span>  
  
-   <span data-ttu-id="43763-127">该参数不是返回参数，或者</span><span class="sxs-lookup"><span data-stu-id="43763-127">the parameter is not a return parameter, or</span></span>  
  
-   <span data-ttu-id="43763-128">cbLen 参数无效\*\*。</span><span class="sxs-lookup"><span data-stu-id="43763-128">the *cbLen* argument is invalid.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="43763-129">备注</span><span class="sxs-lookup"><span data-stu-id="43763-129">Remarks</span></span>  
 <span data-ttu-id="43763-130">**安全说明** 应全面检查扩展存储过程的源代码，并在生产服务器中安装编译的 DLL 之前，应对这些 DLL 进行测试。</span><span class="sxs-lookup"><span data-stu-id="43763-130">**Security Note** You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="43763-131">有关安全检查和测试的信息，请访问此 [Microsoft 网站](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)。</span><span class="sxs-lookup"><span data-stu-id="43763-131">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
  
