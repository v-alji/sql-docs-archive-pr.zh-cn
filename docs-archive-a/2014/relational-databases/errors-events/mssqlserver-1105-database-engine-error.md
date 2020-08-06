---
title: MSSQLSERVER_1105 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1105 (Database Engine error)
ms.assetid: e7f4ad02-8c7f-4bb9-9781-2c86253f2138
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: dea326fab7edd6a5c155c8f0182bffc044505eb5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577735"
---
# <a name="mssqlserver_1105"></a><span data-ttu-id="1a5c3-102">MSSQLSERVER_1105</span><span class="sxs-lookup"><span data-stu-id="1a5c3-102">MSSQLSERVER_1105</span></span>
    
## <a name="details"></a><span data-ttu-id="1a5c3-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="1a5c3-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1a5c3-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="1a5c3-104">Product Name</span></span>|<span data-ttu-id="1a5c3-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="1a5c3-105">SQL Server</span></span>|  
|<span data-ttu-id="1a5c3-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="1a5c3-106">Event ID</span></span>|<span data-ttu-id="1a5c3-107">1105</span><span class="sxs-lookup"><span data-stu-id="1a5c3-107">1105</span></span>|  
|<span data-ttu-id="1a5c3-108">事件源</span><span class="sxs-lookup"><span data-stu-id="1a5c3-108">Event Source</span></span>|<span data-ttu-id="1a5c3-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="1a5c3-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="1a5c3-110">组件</span><span class="sxs-lookup"><span data-stu-id="1a5c3-110">Component</span></span>|<span data-ttu-id="1a5c3-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="1a5c3-111">SQLEngine</span></span>|  
|<span data-ttu-id="1a5c3-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="1a5c3-112">Symbolic Name</span></span>|<span data-ttu-id="1a5c3-113">NO_MORE_SPACE_IN_FG</span><span class="sxs-lookup"><span data-stu-id="1a5c3-113">NO_MORE_SPACE_IN_FG</span></span>|  
|<span data-ttu-id="1a5c3-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="1a5c3-114">Message Text</span></span>|<span data-ttu-id="1a5c3-115">无法为数据库 '%.\*ls' 中的对象 '%.\*ls'%.\*ls 分配空间，因为 '%.\*ls' 文件组已满。</span><span class="sxs-lookup"><span data-stu-id="1a5c3-115">Could not allocate space for object '%.\*ls'%.\*ls in database '%.\*ls' because the '%.\*ls' filegroup is full.</span></span> <span data-ttu-id="1a5c3-116">请删除不需要的文件、删除文件组中的对象、将其他文件添加到文件组或为文件组中的现有文件启用自动增长，以便增加可用磁盘空间。</span><span class="sxs-lookup"><span data-stu-id="1a5c3-116">Create disk space by deleting unneeded files, dropping objects in the filegroup, adding additional files to the filegroup, or setting autogrowth on for existing files in the filegroup.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="1a5c3-117">说明</span><span class="sxs-lookup"><span data-stu-id="1a5c3-117">Explanation</span></span>  
 <span data-ttu-id="1a5c3-118">文件组中没有可用的磁盘空间。</span><span class="sxs-lookup"><span data-stu-id="1a5c3-118">No disk space is available in a filegroup.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="1a5c3-119">用户操作</span><span class="sxs-lookup"><span data-stu-id="1a5c3-119">User Action</span></span>  
 <span data-ttu-id="1a5c3-120">以下操作可能会使空间在文件组中可用：</span><span class="sxs-lookup"><span data-stu-id="1a5c3-120">The following actions may make space available in the filegroup:</span></span>  
  
-   <span data-ttu-id="1a5c3-121">打开 autogrow。</span><span class="sxs-lookup"><span data-stu-id="1a5c3-121">Turn on autogrow.</span></span>  
  
-   <span data-ttu-id="1a5c3-122">向文件组添加更多文件。</span><span class="sxs-lookup"><span data-stu-id="1a5c3-122">Add more files to the file group.</span></span>  
  
-   <span data-ttu-id="1a5c3-123">通过删除不再需要的索引或表来释放磁盘空间。</span><span class="sxs-lookup"><span data-stu-id="1a5c3-123">Free disk space by dropping index or tables that are no longer needed.</span></span>  
  
-   <span data-ttu-id="1a5c3-124">有关详细信息，请参阅 SQL Server 联机丛书中的“解决数据磁盘空间不足的问题”。</span><span class="sxs-lookup"><span data-stu-id="1a5c3-124">For more information, see "Troubleshooting Insufficient Data Disk Space" in SQL Server Books Online.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1a5c3-125">当一个索引位于多个文件上时，`ALTER INDEX REORGANIZE` 会在其中一个文件已满后返回错误 1105。</span><span class="sxs-lookup"><span data-stu-id="1a5c3-125">When an index is located on several files, `ALTER INDEX REORGANIZE` can return error 1105 when one of the files is full.</span></span> <span data-ttu-id="1a5c3-126">重组进程在尝试将行移到已满的文件时被阻止。</span><span class="sxs-lookup"><span data-stu-id="1a5c3-126">The reorganization process is blocked when the process tries to move rows to the full file.</span></span> <span data-ttu-id="1a5c3-127">若要消除此限制，执行 `ALTER INDEX REBUILD`，而不是 `ALTER INDEX REORGANIZE`，或提高任何已满文件的文件增长限制。</span><span class="sxs-lookup"><span data-stu-id="1a5c3-127">To work around this limitation perform an `ALTER INDEX REBUILD` instead of `ALTER INDEX REORGANIZE` or increase the file growth limit of any files that are full.</span></span>  
  
  
