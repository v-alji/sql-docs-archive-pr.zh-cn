---
title: MSSQLSERVER_17803 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 17803 (Database Engine error)
ms.assetid: 28591a19-258d-4891-b78a-4686789bb2d7
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8be63b3d05bff2ebf90122f66af4297d77376fce
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589628"
---
# <a name="mssqlserver_17803"></a><span data-ttu-id="44b75-102">MSSQLSERVER_17803</span><span class="sxs-lookup"><span data-stu-id="44b75-102">MSSQLSERVER_17803</span></span>
    
## <a name="details"></a><span data-ttu-id="44b75-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="44b75-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="44b75-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="44b75-104">Product Name</span></span>|<span data-ttu-id="44b75-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="44b75-105">SQL Server</span></span>|  
|<span data-ttu-id="44b75-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="44b75-106">Event ID</span></span>|<span data-ttu-id="44b75-107">17803</span><span class="sxs-lookup"><span data-stu-id="44b75-107">17803</span></span>|  
|<span data-ttu-id="44b75-108">事件源</span><span class="sxs-lookup"><span data-stu-id="44b75-108">Event Source</span></span>|<span data-ttu-id="44b75-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="44b75-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="44b75-110">组件</span><span class="sxs-lookup"><span data-stu-id="44b75-110">Component</span></span>|<span data-ttu-id="44b75-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="44b75-111">SQLEngine</span></span>|  
|<span data-ttu-id="44b75-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="44b75-112">Symbolic Name</span></span>|<span data-ttu-id="44b75-113">SRV_NOMEMORY</span><span class="sxs-lookup"><span data-stu-id="44b75-113">SRV_NOMEMORY</span></span>|  
|<span data-ttu-id="44b75-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="44b75-114">Message Text</span></span>|<span data-ttu-id="44b75-115">在建立连接过程中出现内存分配错误。</span><span class="sxs-lookup"><span data-stu-id="44b75-115">There was a memory allocation failure during connection establishment.</span></span> <span data-ttu-id="44b75-116">减少不必要的内存负载，或增加系统内存。</span><span class="sxs-lookup"><span data-stu-id="44b75-116">Reduce nonessential memory load, or increase system memory.</span></span> <span data-ttu-id="44b75-117">该连接已关闭。%.\*ls</span><span class="sxs-lookup"><span data-stu-id="44b75-117">The connection has been closed.%.\*ls</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="44b75-118">说明</span><span class="sxs-lookup"><span data-stu-id="44b75-118">Explanation</span></span>  
 <span data-ttu-id="44b75-119">服务器内存不足。</span><span class="sxs-lookup"><span data-stu-id="44b75-119">Server is running out of memory.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="44b75-120">用户操作</span><span class="sxs-lookup"><span data-stu-id="44b75-120">User Action</span></span>  
 <span data-ttu-id="44b75-121">确定服务器内存不足的原因。</span><span class="sxs-lookup"><span data-stu-id="44b75-121">Determine the cause for server running out of memory.</span></span> <span data-ttu-id="44b75-122">一般内存故障排除步骤可能会很有用</span><span class="sxs-lookup"><span data-stu-id="44b75-122">Generic memory troubleshooting steps may be useful</span></span>  
  
  
