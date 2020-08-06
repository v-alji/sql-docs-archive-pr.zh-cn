---
title: srv_alloc（扩展存储过程 API）| Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_alloc
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_alloc
ms.assetid: 91505c59-a273-452f-b71d-5e8205c21863
author: rothja
ms.author: jroth
ms.openlocfilehash: 7b372c1b43987e5bebd1fb82e995dc6d262455ae
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579590"
---
# <a name="srv_alloc-extended-stored-procedure-api"></a><span data-ttu-id="d8e84-102">srv_alloc（扩展存储过程 API）</span><span class="sxs-lookup"><span data-stu-id="d8e84-102">srv_alloc (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]<span data-ttu-id="d8e84-103">请改用 CLR 集成。</span><span class="sxs-lookup"><span data-stu-id="d8e84-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="d8e84-104">动态分配内存。</span><span class="sxs-lookup"><span data-stu-id="d8e84-104">Allocates memory dynamically.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8e84-105">语法</span><span class="sxs-lookup"><span data-stu-id="d8e84-105">Syntax</span></span>  
  
```  
  
void * srv_alloc ( DBINT  
size  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="d8e84-106">参数</span><span class="sxs-lookup"><span data-stu-id="d8e84-106">Arguments</span></span>  
 <span data-ttu-id="d8e84-107">*大小*</span><span class="sxs-lookup"><span data-stu-id="d8e84-107">*size*</span></span>  
 <span data-ttu-id="d8e84-108">指定要分配的字节数。</span><span class="sxs-lookup"><span data-stu-id="d8e84-108">Specifies the number of bytes to allocate.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="d8e84-109">返回</span><span class="sxs-lookup"><span data-stu-id="d8e84-109">Returns</span></span>  
 <span data-ttu-id="d8e84-110">指向新分配的空间的指针。</span><span class="sxs-lookup"><span data-stu-id="d8e84-110">A pointer to the newly allocated space.</span></span> <span data-ttu-id="d8e84-111">如果无法分配 size 字节，则返回 Null 指针\*\*。</span><span class="sxs-lookup"><span data-stu-id="d8e84-111">If *size* bytes cannot be allocated, a null pointer is returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d8e84-112">备注</span><span class="sxs-lookup"><span data-stu-id="d8e84-112">Remarks</span></span>  
 <span data-ttu-id="d8e84-113">srv_alloc 函数等效于 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows API GlobalAlloc 函数\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d8e84-113">The **srv_alloc** function is equivalent to the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows API  **GlobalAlloc** function.</span></span> <span data-ttu-id="d8e84-114">可以在扩展存储过程 API 应用程序中使用普通 Windows API C 运行时内存管理函数。</span><span class="sxs-lookup"><span data-stu-id="d8e84-114">Normal Windows API C run-time memory management functions can be used in an Extended Stored Procedure API application.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="d8e84-115">应全面检查扩展存储过程的源代码，并在生产服务器中安装编译的 DLL 之前，对这些 DLL 进行测试。</span><span class="sxs-lookup"><span data-stu-id="d8e84-115">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="d8e84-116">有关安全检查和测试的信息，请访问此 [Microsoft 网站](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)。</span><span class="sxs-lookup"><span data-stu-id="d8e84-116">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
  
