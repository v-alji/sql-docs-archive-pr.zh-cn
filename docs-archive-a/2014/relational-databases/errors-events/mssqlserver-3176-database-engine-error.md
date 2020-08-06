---
title: MSSQLSERVER_3176 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3176 (Database Engine error)
ms.assetid: 4be24c64-2d52-4cb4-b4d7-36efbe4555b6
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 64e1a836995fe8738bb5c2ff0cb4de10d84d1f29
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586719"
---
# <a name="mssqlserver_3176"></a><span data-ttu-id="a4262-102">MSSQLSERVER_3176</span><span class="sxs-lookup"><span data-stu-id="a4262-102">MSSQLSERVER_3176</span></span>
    
## <a name="details"></a><span data-ttu-id="a4262-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="a4262-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a4262-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="a4262-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="a4262-105">事件 ID</span><span class="sxs-lookup"><span data-stu-id="a4262-105">Event ID</span></span>|<span data-ttu-id="a4262-106">3176</span><span class="sxs-lookup"><span data-stu-id="a4262-106">3176</span></span>|  
|<span data-ttu-id="a4262-107">事件源</span><span class="sxs-lookup"><span data-stu-id="a4262-107">Event Source</span></span>|<span data-ttu-id="a4262-108">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="a4262-108">MSSQLSERVER</span></span>|  
|<span data-ttu-id="a4262-109">组件</span><span class="sxs-lookup"><span data-stu-id="a4262-109">Component</span></span>|<span data-ttu-id="a4262-110">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="a4262-110">SQLEngine</span></span>|  
|<span data-ttu-id="a4262-111">符号名称</span><span class="sxs-lookup"><span data-stu-id="a4262-111">Symbolic Name</span></span>|<span data-ttu-id="a4262-112">LDDB_FILE_CLAIM</span><span class="sxs-lookup"><span data-stu-id="a4262-112">LDDB_FILE_CLAIM</span></span>|  
|<span data-ttu-id="a4262-113">消息正文</span><span class="sxs-lookup"><span data-stu-id="a4262-113">Message Text</span></span>|<span data-ttu-id="a4262-114">'%ls'(%d)和 '%ls'(%d)要求使用文件 '%ls'。</span><span class="sxs-lookup"><span data-stu-id="a4262-114">File '%ls' is claimed by '%ls'(%d) and '%ls'(%d).</span></span> <span data-ttu-id="a4262-115">WITH MOVE 子句可用于重新定位一个或多个文件。</span><span class="sxs-lookup"><span data-stu-id="a4262-115">The WITH MOVE clause can be used to relocate one or more files.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="a4262-116">说明</span><span class="sxs-lookup"><span data-stu-id="a4262-116">Explanation</span></span>  
 <span data-ttu-id="a4262-117">尝试在多项操作中使用同一文件。</span><span class="sxs-lookup"><span data-stu-id="a4262-117">Attempting to use a file for more than one purpose.</span></span>  
  
### <a name="possible-causes"></a><span data-ttu-id="a4262-118">可能的原因</span><span class="sxs-lookup"><span data-stu-id="a4262-118">Possible Causes</span></span>  
 <span data-ttu-id="a4262-119">其他数据库已经在使用该文件名。</span><span class="sxs-lookup"><span data-stu-id="a4262-119">Another database is already using the file name.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="a4262-120">用户操作</span><span class="sxs-lookup"><span data-stu-id="a4262-120">User Action</span></span>  
 <span data-ttu-id="a4262-121">将数据库文件还原到不同位置。</span><span class="sxs-lookup"><span data-stu-id="a4262-121">Restore the database files to a different location.</span></span> <span data-ttu-id="a4262-122">在 RESTORE 语句中，使用 WITH MOVE 子句移动各个文件。</span><span class="sxs-lookup"><span data-stu-id="a4262-122">In a RESTORE statement, use a WITH MOVE clause to move each file.</span></span> <span data-ttu-id="a4262-123">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中，在“还原数据库选项”对话框的“将数据库文件还原为”网格中更改文件位置。</span><span class="sxs-lookup"><span data-stu-id="a4262-123">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], change the file locations in the **Restore the database files as** grid of the **Restore Database Options** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4262-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a4262-124">See Also</span></span>  
 <span data-ttu-id="a4262-125">[将数据库还原到新位置 (SQL Server)](../backup-restore/restore-a-database-to-a-new-location-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="a4262-125">[Restore a Database to a New Location &#40;SQL Server&#41;](../backup-restore/restore-a-database-to-a-new-location-sql-server.md) </span></span>  
 <span data-ttu-id="a4262-126">[将文件还原到 &#40;SQL Server 的新位置&#41;](../backup-restore/restore-files-to-a-new-location-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="a4262-126">[Restore Files to a New Location &#40;SQL Server&#41;](../backup-restore/restore-files-to-a-new-location-sql-server.md) </span></span>  
 [<span data-ttu-id="a4262-127">RESTORE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a4262-127">RESTORE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-transact-sql)  
  
  
