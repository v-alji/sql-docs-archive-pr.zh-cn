---
title: MSSQLSERVER_8443 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 8443 (Database Engine error)
ms.assetid: a3541b9c-b1a8-4280-add1-275f08696b62
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ae02cc0d9e5661f4069884c22bf6eea0697bd2d7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691213"
---
# <a name="mssqlserver_8443"></a><span data-ttu-id="0b2d3-102">MSSQLSERVER_8443</span><span class="sxs-lookup"><span data-stu-id="0b2d3-102">MSSQLSERVER_8443</span></span>
    
## <a name="details"></a><span data-ttu-id="0b2d3-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="0b2d3-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0b2d3-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="0b2d3-104">Product Name</span></span>|<span data-ttu-id="0b2d3-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="0b2d3-105">SQL Server</span></span>|  
|<span data-ttu-id="0b2d3-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="0b2d3-106">Event ID</span></span>|<span data-ttu-id="0b2d3-107">8443</span><span class="sxs-lookup"><span data-stu-id="0b2d3-107">8443</span></span>|  
|<span data-ttu-id="0b2d3-108">事件源</span><span class="sxs-lookup"><span data-stu-id="0b2d3-108">Event Source</span></span>|<span data-ttu-id="0b2d3-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="0b2d3-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="0b2d3-110">组件</span><span class="sxs-lookup"><span data-stu-id="0b2d3-110">Component</span></span>|<span data-ttu-id="0b2d3-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="0b2d3-111">SQLEngine</span></span>|  
|<span data-ttu-id="0b2d3-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="0b2d3-112">Symbolic Name</span></span>|<span data-ttu-id="0b2d3-113">SB_DIALOG_WO_CONV_GROUP</span><span class="sxs-lookup"><span data-stu-id="0b2d3-113">SB_DIALOG_WO_CONV_GROUP</span></span>|  
|<span data-ttu-id="0b2d3-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="0b2d3-114">Message Text</span></span>|<span data-ttu-id="0b2d3-115">ID 为 '%.\*ls' 且发起方为 %d 的会话引用的会话组 '%.\*ls' 已丢失。</span><span class="sxs-lookup"><span data-stu-id="0b2d3-115">The conversation with ID '%.\*ls' and initiator %d references a missing conversation group '%.\*ls'.</span></span> <span data-ttu-id="0b2d3-116">请运行 DBCC CHECKDB 以分析和修复数据库。</span><span class="sxs-lookup"><span data-stu-id="0b2d3-116">Run DBCC CHECKDB to analyze and repair the database.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="0b2d3-117">说明</span><span class="sxs-lookup"><span data-stu-id="0b2d3-117">Explanation</span></span>  
 <span data-ttu-id="0b2d3-118">元数据层为会话组返回了 NULL。</span><span class="sxs-lookup"><span data-stu-id="0b2d3-118">The metadata layer returned NULL for the conversation group.</span></span> <span data-ttu-id="0b2d3-119">数据库由于某个原因已损坏。</span><span class="sxs-lookup"><span data-stu-id="0b2d3-119">The database has been corrupted in some way.</span></span> <span data-ttu-id="0b2d3-120">造成它损坏的一个可能原因是磁盘错误。</span><span class="sxs-lookup"><span data-stu-id="0b2d3-120">One possible source of corruption is a disk error.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="0b2d3-121">用户操作</span><span class="sxs-lookup"><span data-stu-id="0b2d3-121">User Action</span></span>  
 <span data-ttu-id="0b2d3-122">在修复模式下运行 DBCC CHECKDB 使数据库回复到一致状态。</span><span class="sxs-lookup"><span data-stu-id="0b2d3-122">Run DBCC CHECKDB in repair mode to bring the database back into a consistent state.</span></span> <span data-ttu-id="0b2d3-123">如果需要还原一致性，则它可能会删除消息。</span><span class="sxs-lookup"><span data-stu-id="0b2d3-123">It may delete messages if necessary to restore consistency.</span></span> <span data-ttu-id="0b2d3-124">调查系统错误日志以查看此错误是否由系统中的其他故障导致。</span><span class="sxs-lookup"><span data-stu-id="0b2d3-124">Investigate system error logs to see if this error was caused by another failure in the system.</span></span>  
  
  
