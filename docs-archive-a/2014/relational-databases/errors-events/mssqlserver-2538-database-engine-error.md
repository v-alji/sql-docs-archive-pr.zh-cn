---
title: MSSQLSERVER_2538 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2538 (Database Engine error)
ms.assetid: 0a0f7d79-f1ba-4749-8804-fb660cca3492
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 9f4ae886a6fd0abee2f7aa22c6a234c0a6c2d040
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589610"
---
# <a name="mssqlserver_2538"></a><span data-ttu-id="aa33c-102">MSSQLSERVER_2538</span><span class="sxs-lookup"><span data-stu-id="aa33c-102">MSSQLSERVER_2538</span></span>
    
## <a name="details"></a><span data-ttu-id="aa33c-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="aa33c-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="aa33c-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="aa33c-104">Product Name</span></span>|<span data-ttu-id="aa33c-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="aa33c-105">SQL Server</span></span>|  
|<span data-ttu-id="aa33c-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="aa33c-106">Event ID</span></span>|<span data-ttu-id="aa33c-107">2538</span><span class="sxs-lookup"><span data-stu-id="aa33c-107">2538</span></span>|  
|<span data-ttu-id="aa33c-108">事件源</span><span class="sxs-lookup"><span data-stu-id="aa33c-108">Event Source</span></span>|<span data-ttu-id="aa33c-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="aa33c-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="aa33c-110">组件</span><span class="sxs-lookup"><span data-stu-id="aa33c-110">Component</span></span>|<span data-ttu-id="aa33c-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="aa33c-111">SQLEngine</span></span>|  
|<span data-ttu-id="aa33c-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="aa33c-112">Symbolic Name</span></span>|<span data-ttu-id="aa33c-113">DBCC_ALLOCATION_SUMMARY_PER_FILE</span><span class="sxs-lookup"><span data-stu-id="aa33c-113">DBCC_ALLOCATION_SUMMARY_PER_FILE</span></span>|  
|<span data-ttu-id="aa33c-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="aa33c-114">Message Text</span></span>|<span data-ttu-id="aa33c-115">文件 FILE。</span><span class="sxs-lookup"><span data-stu-id="aa33c-115">File FILE.</span></span> <span data-ttu-id="aa33c-116">区数 = EXTENTS，已用页数 = USED_PAGES，保留页数 = RESERVED_PAGES。</span><span class="sxs-lookup"><span data-stu-id="aa33c-116">Number of extents = EXTENTS, used pages = USED_PAGES, reserved pages = RESERVED_PAGES.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="aa33c-117">说明</span><span class="sxs-lookup"><span data-stu-id="aa33c-117">Explanation</span></span>  
 <span data-ttu-id="aa33c-118">此信息是 DBCC CHECKALLOC 命令输出的一部分。</span><span class="sxs-lookup"><span data-stu-id="aa33c-118">This information is part of the output from the DBCC CHECKALLOC command.</span></span> <span data-ttu-id="aa33c-119">此信息是指定数据库的已分配区数、已用页数和保留页数的按文件摘要。</span><span class="sxs-lookup"><span data-stu-id="aa33c-119">This information is the per-file summary of allocated extents, used pages, and reserved pages for the specified database.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="aa33c-120">用户操作</span><span class="sxs-lookup"><span data-stu-id="aa33c-120">User Action</span></span>  
 <span data-ttu-id="aa33c-121">无</span><span class="sxs-lookup"><span data-stu-id="aa33c-121">None</span></span>  
  
  
