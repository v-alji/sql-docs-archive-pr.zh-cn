---
title: MSSQLSERVER_17887 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 17887 (Database Engine error)
ms.assetid: ad0806e6-3296-4c32-b103-fccf0f8a8d3d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 006e616d80ef7e8d083f60675b02b4e6a4e8dc24
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577730"
---
# <a name="mssqlserver_17887"></a><span data-ttu-id="a93c9-102">MSSQLSERVER_17887</span><span class="sxs-lookup"><span data-stu-id="a93c9-102">MSSQLSERVER_17887</span></span>
    
## <a name="details"></a><span data-ttu-id="a93c9-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="a93c9-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a93c9-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="a93c9-104">Product Name</span></span>|<span data-ttu-id="a93c9-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="a93c9-105">SQL Server</span></span>|  
|<span data-ttu-id="a93c9-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="a93c9-106">Event ID</span></span>|<span data-ttu-id="a93c9-107">17887</span><span class="sxs-lookup"><span data-stu-id="a93c9-107">17887</span></span>|  
|<span data-ttu-id="a93c9-108">事件源</span><span class="sxs-lookup"><span data-stu-id="a93c9-108">Event Source</span></span>|<span data-ttu-id="a93c9-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="a93c9-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="a93c9-110">组件</span><span class="sxs-lookup"><span data-stu-id="a93c9-110">Component</span></span>|<span data-ttu-id="a93c9-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="a93c9-111">SQLEngine</span></span>|  
|<span data-ttu-id="a93c9-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="a93c9-112">Symbolic Name</span></span>|<span data-ttu-id="a93c9-113">SRV_IO_COMP_LISTENER_NONYIELDING</span><span class="sxs-lookup"><span data-stu-id="a93c9-113">SRV_IO_COMP_LISTENER_NONYIELDING</span></span>|  
|<span data-ttu-id="a93c9-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="a93c9-114">Message Text</span></span>|<span data-ttu-id="a93c9-115">节点 %ld 上的 IO 完成侦听器(0x%lx)工作线程 0x%p 似乎无法完成。</span><span class="sxs-lookup"><span data-stu-id="a93c9-115">IO Completion Listener (0x%lx) Worker 0x%p appears to be non-yielding on Node %ld.</span></span> <span data-ttu-id="a93c9-116">CPU 近似使用时间: 内核 %I64d 毫秒，用户 %I64d 毫秒，间隔: %I64d。</span><span class="sxs-lookup"><span data-stu-id="a93c9-116">Approx CPU Used: kernel %I64d ms, user %I64d ms, Interval: %I64d.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="a93c9-117">说明</span><span class="sxs-lookup"><span data-stu-id="a93c9-117">Explanation</span></span>  
 <span data-ttu-id="a93c9-118">指示当为某一网络读/写事件执行 I/O 完成例程时，指定节点上的 I/O 完成端口侦听器可能出现了问题。</span><span class="sxs-lookup"><span data-stu-id="a93c9-118">Indicates that there is a possible problem with the I/O Completion Port Listener on the specified node when executing the I/O Completion routine for a network read/write event.</span></span> <span data-ttu-id="a93c9-119">当 I/O 完成端口侦听器从执行 I/O 完成例程返回时，此错误将消失。</span><span class="sxs-lookup"><span data-stu-id="a93c9-119">This error will go away when the I/O Completion Port Listener returns from executing the I/O Completion routine.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="a93c9-120">用户操作</span><span class="sxs-lookup"><span data-stu-id="a93c9-120">User Action</span></span>  
 <span data-ttu-id="a93c9-121">请与 Microsoft 客户支持服务部门 (CSS) 联系。</span><span class="sxs-lookup"><span data-stu-id="a93c9-121">Contact Microsoft Customer Support Services (CSS).</span></span>  
  
  
