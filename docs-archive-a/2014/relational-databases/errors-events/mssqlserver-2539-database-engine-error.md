---
title: MSSQLSERVER_2539 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2539 (Database Engine error)
ms.assetid: e638efcc-56f4-40f9-9740-17ef67b47d79
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 9f061d2a827dca641bfc0c348af1328fd71856fd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589609"
---
# <a name="mssqlserver_2539"></a><span data-ttu-id="b31c8-102">MSSQLSERVER_2539</span><span class="sxs-lookup"><span data-stu-id="b31c8-102">MSSQLSERVER_2539</span></span>
    
## <a name="details"></a><span data-ttu-id="b31c8-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="b31c8-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b31c8-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="b31c8-104">Product Name</span></span>|<span data-ttu-id="b31c8-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="b31c8-105">SQL Server</span></span>|  
|<span data-ttu-id="b31c8-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="b31c8-106">Event ID</span></span>|<span data-ttu-id="b31c8-107">2539</span><span class="sxs-lookup"><span data-stu-id="b31c8-107">2539</span></span>|  
|<span data-ttu-id="b31c8-108">事件源</span><span class="sxs-lookup"><span data-stu-id="b31c8-108">Event Source</span></span>|<span data-ttu-id="b31c8-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="b31c8-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="b31c8-110">组件</span><span class="sxs-lookup"><span data-stu-id="b31c8-110">Component</span></span>|<span data-ttu-id="b31c8-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="b31c8-111">SQLEngine</span></span>|  
|<span data-ttu-id="b31c8-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="b31c8-112">Symbolic Name</span></span>|<span data-ttu-id="b31c8-113">DBCC_ALLOCATION_SUMMARY_FOR_DATABASE</span><span class="sxs-lookup"><span data-stu-id="b31c8-113">DBCC_ALLOCATION_SUMMARY_FOR_DATABASE</span></span>|  
|<span data-ttu-id="b31c8-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="b31c8-114">Message Text</span></span>|<span data-ttu-id="b31c8-115">在此数据库中，总区数 = EXTENTS，已用页数 = USED_PAGES，保留页数 = RESERVED_PAGES。</span><span class="sxs-lookup"><span data-stu-id="b31c8-115">Total number of extents = EXTENTS, used pages = USED_PAGES, reserved pages = RESERVED_PAGES in this database.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="b31c8-116">说明</span><span class="sxs-lookup"><span data-stu-id="b31c8-116">Explanation</span></span>  
 <span data-ttu-id="b31c8-117">此信息是 DBCC CHECKALLOC 命令输出的一部分。</span><span class="sxs-lookup"><span data-stu-id="b31c8-117">This information is part of the output from the DBCC CHECKALLOC command.</span></span> <span data-ttu-id="b31c8-118">此信息是指定数据库的已分配区数、已用页数和保留页数的摘要。</span><span class="sxs-lookup"><span data-stu-id="b31c8-118">This information is the summary of allocated extents, used pages, and reserved pages for the specified database.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="b31c8-119">用户操作</span><span class="sxs-lookup"><span data-stu-id="b31c8-119">User Action</span></span>  
 <span data-ttu-id="b31c8-120">无</span><span class="sxs-lookup"><span data-stu-id="b31c8-120">None</span></span>  
  
  
