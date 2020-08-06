---
title: 扩展存储过程程序员引用 | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
topic_type:
- apiref
- apinav
helpviewer_keywords:
- extended stored procedures [SQL Server], listed
ms.assetid: 4e9d0374-0927-4f17-bab9-2215b1b8fea8
author: rothja
ms.author: jroth
ms.openlocfilehash: f3b1beade751cd7a7407f3c33eb7f8ae58c9fd4a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590812"
---
# <a name="extended-stored-procedures-programmer39s-reference"></a><span data-ttu-id="80b81-102">扩展存储过程程序员&#39;s 参考</span><span class="sxs-lookup"><span data-stu-id="80b81-102">Extended Stored Procedures Programmer&#39;s Reference</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]<span data-ttu-id="80b81-103">请改用 CLR 集成。</span><span class="sxs-lookup"><span data-stu-id="80b81-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="80b81-104">[!INCLUDE[msCoName](../../includes/msconame-md.md)]扩展存储过程 API （以前是开放式数据服务的一部分）提供了基于服务器的应用程序编程接口 (API) 来扩展 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 功能。</span><span class="sxs-lookup"><span data-stu-id="80b81-104">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Extended Stored Procedure API, previously part of Open Data Services, provides a server-based application programming interface (API) for extending [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] functionality.</span></span> <span data-ttu-id="80b81-105">该 API 由用于生成应用程序的 C 和 C++ 函数及宏组成。</span><span class="sxs-lookup"><span data-stu-id="80b81-105">The API consists of C and C++ functions and macros used to build applications.</span></span>  
  
 <span data-ttu-id="80b81-106">随着诸如 CLR 集成这样更新和功能更强大的技术的出现，对扩展存储过程的需求已大幅减少。</span><span class="sxs-lookup"><span data-stu-id="80b81-106">With the emergence of newer and more powerful technologies such as CLR integration, the need for extended stored procedures has largely been replaced.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="80b81-107">应全面检查扩展存储过程的源代码，并在生产服务器中安装编译的 DLL 之前，对这些 DLL 进行测试。</span><span class="sxs-lookup"><span data-stu-id="80b81-107">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="80b81-108">有关安全检查和测试的信息，请访问此 [Microsoft 网站](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)。</span><span class="sxs-lookup"><span data-stu-id="80b81-108">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="80b81-109">本节内容</span><span class="sxs-lookup"><span data-stu-id="80b81-109">In This Section</span></span>  
  
|||  
|-|-|  
|[<span data-ttu-id="80b81-110">数据类型</span><span class="sxs-lookup"><span data-stu-id="80b81-110">Data Types</span></span>](srv-pfield-extended-stored-procedure-api.md)|  
|[<span data-ttu-id="80b81-111">srv_alloc</span><span class="sxs-lookup"><span data-stu-id="80b81-111">srv_alloc</span></span>](srv-alloc-extended-stored-procedure-api.md)||  
|[<span data-ttu-id="80b81-112">srv_convert</span><span class="sxs-lookup"><span data-stu-id="80b81-112">srv_convert</span></span>](srv-pfieldex-extended-stored-procedure-api.md)|  
|[<span data-ttu-id="80b81-113">srv_describe</span><span class="sxs-lookup"><span data-stu-id="80b81-113">srv_describe</span></span>](srv-rpcdb-extended-stored-procedure-api.md)|  
|[<span data-ttu-id="80b81-114">srv_getbindtoken</span><span class="sxs-lookup"><span data-stu-id="80b81-114">srv_getbindtoken</span></span>](srv-rpcname-extended-stored-procedure-api.md)|  
|[<span data-ttu-id="80b81-115">srv_got_attention</span><span class="sxs-lookup"><span data-stu-id="80b81-115">srv_got_attention</span></span>](srv-rpcnumber-extended-stored-procedure-api.md)|  
||[<span data-ttu-id="80b81-116">srv_rpcoptions</span><span class="sxs-lookup"><span data-stu-id="80b81-116">srv_rpcoptions</span></span>](srv-rpcoptions-extended-stored-procedure-api.md)|  
|[<span data-ttu-id="80b81-117">srv_message_handler</span><span class="sxs-lookup"><span data-stu-id="80b81-117">srv_message_handler</span></span>](srv-rpcowner-extended-stored-procedure-api.md)|  
|[<span data-ttu-id="80b81-118">srv_paramdata</span><span class="sxs-lookup"><span data-stu-id="80b81-118">srv_paramdata</span></span>](srv-rpcparams-extended-stored-procedure-api.md)|  
|[<span data-ttu-id="80b81-119">srv_paraminfo</span><span class="sxs-lookup"><span data-stu-id="80b81-119">srv_paraminfo</span></span>](srv-senddone-extended-stored-procedure-api.md)|  
|[<span data-ttu-id="80b81-120">srv_paramlen</span><span class="sxs-lookup"><span data-stu-id="80b81-120">srv_paramlen</span></span>](srv-sendmsg-extended-stored-procedure-api.md)|  
|[<span data-ttu-id="80b81-121">srv_parammaxlen</span><span class="sxs-lookup"><span data-stu-id="80b81-121">srv_parammaxlen</span></span>](srv-sendrow-extended-stored-procedure-api.md)|  
|[<span data-ttu-id="80b81-122">srv_paramname</span><span class="sxs-lookup"><span data-stu-id="80b81-122">srv_paramname</span></span>](srv-setcoldata-extended-stored-procedure-api.md)|  
|[<span data-ttu-id="80b81-123">srv_paramnumber</span><span class="sxs-lookup"><span data-stu-id="80b81-123">srv_paramnumber</span></span>](srv-setcollen-extended-stored-procedure-api.md)|  
|[<span data-ttu-id="80b81-124">srv_paramset</span><span class="sxs-lookup"><span data-stu-id="80b81-124">srv_paramset</span></span>](srv-setutype-extended-stored-procedure-api.md)|  
|[<span data-ttu-id="80b81-125">srv_paramsetoutput</span><span class="sxs-lookup"><span data-stu-id="80b81-125">srv_paramsetoutput</span></span>](srv-willconvert-extended-stored-procedure-api.md)|  
|[<span data-ttu-id="80b81-126">srv_paramstatus</span><span class="sxs-lookup"><span data-stu-id="80b81-126">srv_paramstatus</span></span>](srv-wsendmsg-extended-stored-procedure-api.md)|  
|[<span data-ttu-id="80b81-127">srv_paramtype</span><span class="sxs-lookup"><span data-stu-id="80b81-127">srv_paramtype</span></span>](srv-paramtype-extended-stored-procedure-api.md)||  
  
  
