---
title: MSSQLSERVER_9692 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 9692 (Database Engine error)
ms.assetid: 02399d6e-ab5e-4f30-8a3e-2bb1e8c135b5
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6b6ba95771aafffa5a322ffa1b7443419936addd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581228"
---
# <a name="mssqlserver_9692"></a><span data-ttu-id="491b8-102">MSSQLSERVER_9692</span><span class="sxs-lookup"><span data-stu-id="491b8-102">MSSQLSERVER_9692</span></span>
    
## <a name="details"></a><span data-ttu-id="491b8-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="491b8-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="491b8-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="491b8-104">Product Name</span></span>|<span data-ttu-id="491b8-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="491b8-105">SQL Server</span></span>|  
|<span data-ttu-id="491b8-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="491b8-106">Event ID</span></span>|<span data-ttu-id="491b8-107">9692</span><span class="sxs-lookup"><span data-stu-id="491b8-107">9692</span></span>|  
|<span data-ttu-id="491b8-108">事件源</span><span class="sxs-lookup"><span data-stu-id="491b8-108">Event Source</span></span>|<span data-ttu-id="491b8-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="491b8-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="491b8-110">组件</span><span class="sxs-lookup"><span data-stu-id="491b8-110">Component</span></span>|<span data-ttu-id="491b8-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="491b8-111">SQLEngine</span></span>|  
|<span data-ttu-id="491b8-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="491b8-112">Symbolic Name</span></span>|<span data-ttu-id="491b8-113">SB2_CANT_LISTEN_PORT_IN_USE</span><span class="sxs-lookup"><span data-stu-id="491b8-113">SB2_CANT_LISTEN_PORT_IN_USE</span></span>|  
|<span data-ttu-id="491b8-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="491b8-114">Message Text</span></span>|<span data-ttu-id="491b8-115">%S_MSG 协议传输无法侦听端口 %d，因为其他进程正在使用此端口。</span><span class="sxs-lookup"><span data-stu-id="491b8-115">The %S_MSG protocol transport cannot listen on port %d because it is in use by another process.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="491b8-116">说明</span><span class="sxs-lookup"><span data-stu-id="491b8-116">Explanation</span></span>  
 <span data-ttu-id="491b8-117">计算机上的其他程序正在使用指示的 TCP 端口。</span><span class="sxs-lookup"><span data-stu-id="491b8-117">Another program on the computer is using the TCP port indicated.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="491b8-118">用户操作</span><span class="sxs-lookup"><span data-stu-id="491b8-118">User Action</span></span>  
 <span data-ttu-id="491b8-119">运行 `netstat -aon` 以确定哪个程序正在使用该端口。</span><span class="sxs-lookup"><span data-stu-id="491b8-119">Run `netstat -aon` to determine what program is using the port.</span></span> <span data-ttu-id="491b8-120">禁用该应用程序，或者为 Service Broker 指定其他端口。</span><span class="sxs-lookup"><span data-stu-id="491b8-120">Disable that application or specify a different port for Service Broker.</span></span>  
  
  
