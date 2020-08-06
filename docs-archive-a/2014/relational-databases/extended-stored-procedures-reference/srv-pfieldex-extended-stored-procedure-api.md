---
title: srv_pfieldex（扩展存储过程 API）| Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_pfieldex
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_pfieldex
ms.assetid: d4e9a34b-b3a3-434f-8556-768bd20d145a
author: rothja
ms.author: jroth
ms.openlocfilehash: a474eafcb6b6d42161a7e67ce7f93636269c46c7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579585"
---
# <a name="srv_pfieldex-extended-stored-procedure-api"></a><span data-ttu-id="bb573-102">srv_pfieldex（扩展存储过程 API）</span><span class="sxs-lookup"><span data-stu-id="bb573-102">srv_pfieldex (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]<span data-ttu-id="bb573-103">请改用 CLR 集成。</span><span class="sxs-lookup"><span data-stu-id="bb573-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="bb573-104">返回一个指针，指向包含请求的 SRV_PROC 字段的数据。</span><span class="sxs-lookup"><span data-stu-id="bb573-104">Returns a pointer to data containing the requested SRV_PROC field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb573-105">语法</span><span class="sxs-lookup"><span data-stu-id="bb573-105">Syntax</span></span>  
  
```  
  
void *srv_pfieldex(SRV_PROC *   
srvproc  
, int   
field  
, int *   
len  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="bb573-106">参数</span><span class="sxs-lookup"><span data-stu-id="bb573-106">Arguments</span></span>  
 <span data-ttu-id="bb573-107">srvproc\*\*</span><span class="sxs-lookup"><span data-stu-id="bb573-107">*srvproc*</span></span>  
 <span data-ttu-id="bb573-108">指向作为特定客户端连接句柄的 SRV_PROC 结构的指针。</span><span class="sxs-lookup"><span data-stu-id="bb573-108">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection.</span></span> <span data-ttu-id="bb573-109">该结构包含扩展存储过程 API 库用于管理应用程序和客户端之间的通信和数据的信息。</span><span class="sxs-lookup"><span data-stu-id="bb573-109">The structure contains information the Extended Stored Procedure API library uses to manage communication and data between the application and the client.</span></span>  
  
 <span data-ttu-id="bb573-110">*定义域*</span><span class="sxs-lookup"><span data-stu-id="bb573-110">*field*</span></span>  
 <span data-ttu-id="bb573-111">指定要返回的 srvproc 字段\*\*。</span><span class="sxs-lookup"><span data-stu-id="bb573-111">Specifies the *srvproc* field to return.</span></span>  
  
|<span data-ttu-id="bb573-112">字段</span><span class="sxs-lookup"><span data-stu-id="bb573-112">Field</span></span>|<span data-ttu-id="bb573-113">说明</span><span class="sxs-lookup"><span data-stu-id="bb573-113">Description</span></span>|<span data-ttu-id="bb573-114">返回类型</span><span class="sxs-lookup"><span data-stu-id="bb573-114">Return-type</span></span>|  
|-----------|-----------------|------------------|  
|<span data-ttu-id="bb573-115">SRV_MSGLCID</span><span class="sxs-lookup"><span data-stu-id="bb573-115">SRV_MSGLCID</span></span>|<span data-ttu-id="bb573-116">当前会话消息 LCID。</span><span class="sxs-lookup"><span data-stu-id="bb573-116">Current session message LCID.</span></span>|<span data-ttu-id="bb573-117">ULONG\*</span><span class="sxs-lookup"><span data-stu-id="bb573-117">ULONG\*</span></span>|  
|<span data-ttu-id="bb573-118">SRV_INSTANCENAME</span><span class="sxs-lookup"><span data-stu-id="bb573-118">SRV_INSTANCENAME</span></span>|<span data-ttu-id="bb573-119">实例名称（如果已命名）；否则返回 NULL。</span><span class="sxs-lookup"><span data-stu-id="bb573-119">Instance name (if named); otherwise, returns NULL.</span></span>|<span data-ttu-id="bb573-120">WCHAR\*</span><span class="sxs-lookup"><span data-stu-id="bb573-120">WCHAR\*</span></span>|  
  
 <span data-ttu-id="bb573-121">*长度*</span><span class="sxs-lookup"><span data-stu-id="bb573-121">*len*</span></span>  
 <span data-ttu-id="bb573-122">指向一个 int 变量的指针，该变量包含所返回的 field 值的长度（以字节为单位）\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="bb573-122">Is a pointer to an **int** variable that contains the length of the returned *field* value in bytes.</span></span> <span data-ttu-id="bb573-123">如果 len 为 NULL，则不返回长度\*\*。</span><span class="sxs-lookup"><span data-stu-id="bb573-123">If *len* is NULL, the length is not returned.</span></span> <span data-ttu-id="bb573-124">返回 NULL 时，\*len 设置为 0\*\*。</span><span class="sxs-lookup"><span data-stu-id="bb573-124">When NULL is returned \**len* is set to 0.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="bb573-125">返回</span><span class="sxs-lookup"><span data-stu-id="bb573-125">Returns</span></span>  
 <span data-ttu-id="bb573-126">一个指针，指向其类型取决于 field 的数据\*\*。</span><span class="sxs-lookup"><span data-stu-id="bb573-126">A pointer to data whose type depends on *field*.</span></span> <span data-ttu-id="bb573-127">len 为 NULL 或 srvproc 为 NULL 时，则返回 NULL\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="bb573-127">NULL is returned when *len* is NULL or *srvproc* is NULL.</span></span> <span data-ttu-id="bb573-128">如果 field 未知，则返回 NULL\*\*。</span><span class="sxs-lookup"><span data-stu-id="bb573-128">If the *field* is unknown, NULL is returned.</span></span> <span data-ttu-id="bb573-129">返回 NULL 时，\*len 设置为 0\*\*。</span><span class="sxs-lookup"><span data-stu-id="bb573-129">When NULL is returned \**len* is set to 0.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="bb573-130">从服务器返回的缓冲区应为只读的。</span><span class="sxs-lookup"><span data-stu-id="bb573-130">The buffer returned from the server should be read only.</span></span> <span data-ttu-id="bb573-131">否则，可能损坏服务器状态。</span><span class="sxs-lookup"><span data-stu-id="bb573-131">Otherwise, the server state may be corrupted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bb573-132">备注</span><span class="sxs-lookup"><span data-stu-id="bb573-132">Remarks</span></span>  
 <span data-ttu-id="bb573-133">**安全说明** 应全面检查扩展存储过程的源代码，并在生产服务器中安装编译的 DLL 之前，应对这些 DLL 进行测试。</span><span class="sxs-lookup"><span data-stu-id="bb573-133">**Security Note** You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="bb573-134">有关安全检查和测试的信息，请访问此 [Microsoft 网站](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)。</span><span class="sxs-lookup"><span data-stu-id="bb573-134">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
  
