---
title: MSSQLSERVER_41342 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 41342 (Database Engine error)
ms.assetid: 28270d98-c543-4e7d-b40c-2200e38dce1c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c0269322b30cee88e5ba3d50b6d391464b735f54
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588572"
---
# <a name="mssqlserver_41342"></a><span data-ttu-id="475f6-102">MSSQLSERVER_41342</span><span class="sxs-lookup"><span data-stu-id="475f6-102">MSSQLSERVER_41342</span></span>
    
## <a name="details"></a><span data-ttu-id="475f6-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="475f6-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="475f6-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="475f6-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="475f6-105">事件 ID</span><span class="sxs-lookup"><span data-stu-id="475f6-105">Event ID</span></span>|<span data-ttu-id="475f6-106">41342</span><span class="sxs-lookup"><span data-stu-id="475f6-106">41342</span></span>|  
|<span data-ttu-id="475f6-107">事件源</span><span class="sxs-lookup"><span data-stu-id="475f6-107">Event Source</span></span>|<span data-ttu-id="475f6-108">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="475f6-108">MSSQLSERVER</span></span>|  
|<span data-ttu-id="475f6-109">组件</span><span class="sxs-lookup"><span data-stu-id="475f6-109">Component</span></span>|<span data-ttu-id="475f6-110">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="475f6-110">SQLEngine</span></span>|  
|<span data-ttu-id="475f6-111">符号名称</span><span class="sxs-lookup"><span data-stu-id="475f6-111">Symbolic Name</span></span>|<span data-ttu-id="475f6-112">HK_HW_NOT_SUPPORTED</span><span class="sxs-lookup"><span data-stu-id="475f6-112">HK_HW_NOT_SUPPORTED</span></span>|  
|<span data-ttu-id="475f6-113">消息正文</span><span class="sxs-lookup"><span data-stu-id="475f6-113">Message Text</span></span>|<span data-ttu-id="475f6-114">系统上的处理器型号不支持创建 *construct*。</span><span class="sxs-lookup"><span data-stu-id="475f6-114">The model of the processor on the system does not support creating *construct*.</span></span> <span data-ttu-id="475f6-115">较早的处理器通常会出现此错误。</span><span class="sxs-lookup"><span data-stu-id="475f6-115">This error typically occurs with older processors.</span></span> <span data-ttu-id="475f6-116">有关支持的型号的信息，请参阅 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 联机丛书。</span><span class="sxs-lookup"><span data-stu-id="475f6-116">See [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online for information on supported models.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="475f6-117">说明</span><span class="sxs-lookup"><span data-stu-id="475f6-117">Explanation</span></span>  
 <span data-ttu-id="475f6-118">内存优化的表要求处理器型号支持对 128 位值执行原子比较和交换操作，这要求装配说明 CMPXCHG16B。</span><span class="sxs-lookup"><span data-stu-id="475f6-118">Memory-optimized tables require a processor model that supports atomic compare-and-exchange operations on 128-bit values, which require the assembly instruction CMPXCHG16B.</span></span> <span data-ttu-id="475f6-119">一些较旧的 AMD 处理器型号不支持 CMPXCHG16B 指令。</span><span class="sxs-lookup"><span data-stu-id="475f6-119">Certain older AMD processor models do not support the CMPXCHG16B instruction.</span></span> <span data-ttu-id="475f6-120">此外，默认情况下，某些虚拟化环境不启用此指令。</span><span class="sxs-lookup"><span data-stu-id="475f6-120">Also, certain virtualization environments do not enable this instruction by default.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="475f6-121">用户操作</span><span class="sxs-lookup"><span data-stu-id="475f6-121">User Action</span></span>  
 <span data-ttu-id="475f6-122">升级您的处理器。</span><span class="sxs-lookup"><span data-stu-id="475f6-122">Upgrade your processor.</span></span> <span data-ttu-id="475f6-123">如果您的处理器支持该指令并且您正在虚拟机中运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，则更改配置以便支持指令 CMPXCHG16B。</span><span class="sxs-lookup"><span data-stu-id="475f6-123">If your processor supports the instruction and you are running [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in a virtual machine, change the configuration to support the instruction CMPXCHG16B.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="475f6-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="475f6-124">See Also</span></span>  
 [<span data-ttu-id="475f6-125">内存中 OLTP（内存中优化）</span><span class="sxs-lookup"><span data-stu-id="475f6-125">In-Memory OLTP &#40;In-Memory Optimization&#41;</span></span>](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
