---
title: MSSQLSERVER_3181 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3181 (Database Engine error)
ms.assetid: e6d2e716-5263-477c-ad0e-7bcbfef4c1f3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f18509d9a18ba8be1f4e40c93bff5abfcae3d69c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586718"
---
# <a name="mssqlserver_3181"></a><span data-ttu-id="ad8ec-102">MSSQLSERVER_3181</span><span class="sxs-lookup"><span data-stu-id="ad8ec-102">MSSQLSERVER_3181</span></span>
    
## <a name="details"></a><span data-ttu-id="ad8ec-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="ad8ec-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ad8ec-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="ad8ec-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="ad8ec-105">事件 ID</span><span class="sxs-lookup"><span data-stu-id="ad8ec-105">Event ID</span></span>|<span data-ttu-id="ad8ec-106">3181</span><span class="sxs-lookup"><span data-stu-id="ad8ec-106">3181</span></span>|  
|<span data-ttu-id="ad8ec-107">事件源</span><span class="sxs-lookup"><span data-stu-id="ad8ec-107">Event Source</span></span>|<span data-ttu-id="ad8ec-108">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="ad8ec-108">MSSQLSERVER</span></span>|  
|<span data-ttu-id="ad8ec-109">组件</span><span class="sxs-lookup"><span data-stu-id="ad8ec-109">Component</span></span>|<span data-ttu-id="ad8ec-110">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="ad8ec-110">SQLEngine</span></span>|  
|<span data-ttu-id="ad8ec-111">符号名称</span><span class="sxs-lookup"><span data-stu-id="ad8ec-111">Symbolic Name</span></span>|<span data-ttu-id="ad8ec-112">LDDB_STORAGE_VERIFY</span><span class="sxs-lookup"><span data-stu-id="ad8ec-112">LDDB_STORAGE_VERIFY</span></span>|  
|<span data-ttu-id="ad8ec-113">消息正文</span><span class="sxs-lookup"><span data-stu-id="ad8ec-113">Message Text</span></span>|<span data-ttu-id="ad8ec-114">还原此备份的尝试可能会遇到存储空间问题。</span><span class="sxs-lookup"><span data-stu-id="ad8ec-114">Attempting to restore this backup may encounter storage space problems.</span></span> <span data-ttu-id="ad8ec-115">后续消息将提供详细信息。</span><span class="sxs-lookup"><span data-stu-id="ad8ec-115">Subsequent messages will provide details.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="ad8ec-116">说明</span><span class="sxs-lookup"><span data-stu-id="ad8ec-116">Explanation</span></span>  
 <span data-ttu-id="ad8ec-117">RESTORE VERIFYONLY 语句会检查数据库将还原到的磁盘上的可用存储空间。</span><span class="sxs-lookup"><span data-stu-id="ad8ec-117">The RESTORE VERIFYONLY statement checks the available storage space on the disk to which the database is to be restored.</span></span>  
  
### <a name="possible-causes"></a><span data-ttu-id="ad8ec-118">可能的原因</span><span class="sxs-lookup"><span data-stu-id="ad8ec-118">Possible Causes</span></span>  
 <span data-ttu-id="ad8ec-119">可用磁盘空间不足，因此无法还原要验证的备份。</span><span class="sxs-lookup"><span data-stu-id="ad8ec-119">The available disk space may be insufficient to restore the backup being verified.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="ad8ec-120">用户操作</span><span class="sxs-lookup"><span data-stu-id="ad8ec-120">User Action</span></span>  
 <span data-ttu-id="ad8ec-121">将备份还原到拥有足够磁盘空间的位置，或提供更多磁盘空间。</span><span class="sxs-lookup"><span data-stu-id="ad8ec-121">Restore the backup to a location with sufficient disk space, or provide more space on the disk.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad8ec-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ad8ec-122">See Also</span></span>  
 <span data-ttu-id="ad8ec-123">[将数据库还原到新位置 (SQL Server)](../backup-restore/restore-a-database-to-a-new-location-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="ad8ec-123">[Restore a Database to a New Location &#40;SQL Server&#41;](../backup-restore/restore-a-database-to-a-new-location-sql-server.md) </span></span>  
 <span data-ttu-id="ad8ec-124">[将文件还原到 &#40;SQL Server 的新位置&#41;](../backup-restore/restore-files-to-a-new-location-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="ad8ec-124">[Restore Files to a New Location &#40;SQL Server&#41;](../backup-restore/restore-files-to-a-new-location-sql-server.md) </span></span>  
 <span data-ttu-id="ad8ec-125">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ad8ec-125">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 [<span data-ttu-id="ad8ec-126">RESTORE VERIFYONLY (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="ad8ec-126">RESTORE VERIFYONLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql)  
  
  
