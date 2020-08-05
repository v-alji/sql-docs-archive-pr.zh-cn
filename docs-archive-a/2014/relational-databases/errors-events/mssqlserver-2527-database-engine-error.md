---
title: MSSQLSERVER_2527 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2527 (Database Engine error)
ms.assetid: 1cef90ef-9c39-44e6-bc7f-316c8f53c10c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 900707634a016ecfd29f9f676e68b4d2f557ccea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580279"
---
# <a name="mssqlserver_2527"></a><span data-ttu-id="fce37-102">MSSQLSERVER_2527</span><span class="sxs-lookup"><span data-stu-id="fce37-102">MSSQLSERVER_2527</span></span>
    
## <a name="details"></a><span data-ttu-id="fce37-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="fce37-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="fce37-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="fce37-104">Product Name</span></span>|<span data-ttu-id="fce37-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="fce37-105">SQL Server</span></span>|  
|<span data-ttu-id="fce37-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="fce37-106">Event ID</span></span>|<span data-ttu-id="fce37-107">2527</span><span class="sxs-lookup"><span data-stu-id="fce37-107">2527</span></span>|  
|<span data-ttu-id="fce37-108">事件源</span><span class="sxs-lookup"><span data-stu-id="fce37-108">Event Source</span></span>|<span data-ttu-id="fce37-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="fce37-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="fce37-110">组件</span><span class="sxs-lookup"><span data-stu-id="fce37-110">Component</span></span>|<span data-ttu-id="fce37-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="fce37-111">SQLEngine</span></span>|  
|<span data-ttu-id="fce37-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="fce37-112">Symbolic Name</span></span>|<span data-ttu-id="fce37-113">DBCC_INDEX_FILEGROUP_IS_OFFLINE</span><span class="sxs-lookup"><span data-stu-id="fce37-113">DBCC_INDEX_FILEGROUP_IS_OFFLINE</span></span>|  
|<span data-ttu-id="fce37-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="fce37-114">Message Text</span></span>|<span data-ttu-id="fce37-115">无法处理表 O_NAME 的索引 I_NAME，因为文件组 F_NAME 离线。</span><span class="sxs-lookup"><span data-stu-id="fce37-115">Unable to process index I_NAME of table O_NAME because filegroup F_NAME is offline.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="fce37-116">说明</span><span class="sxs-lookup"><span data-stu-id="fce37-116">Explanation</span></span>  
 <span data-ttu-id="fce37-117">此信息性消息指示由于用来存储索引数据的某个文件组处于脱机状态而无法检查索引。</span><span class="sxs-lookup"><span data-stu-id="fce37-117">This informational message indicates that the index cannot be checked because one of the filegroups that stores data for the index is offline.</span></span> <span data-ttu-id="fce37-118">文件组中文件的状态决定整个文件组的可用性。</span><span class="sxs-lookup"><span data-stu-id="fce37-118">The state of the files in a filegroup determines the availability of the whole filegroup.</span></span> <span data-ttu-id="fce37-119">文件组中的所有文件都必须联机，文件组才可用。</span><span class="sxs-lookup"><span data-stu-id="fce37-119">For a filegroup to be available, all files within the filegroup must be online.</span></span> <span data-ttu-id="fce37-120">如果没有其他问题，将检查同一对象的所有其他索引。</span><span class="sxs-lookup"><span data-stu-id="fce37-120">If there are no other problems, all other indexes of the same object will be checked.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="fce37-121">用户操作</span><span class="sxs-lookup"><span data-stu-id="fce37-121">User Action</span></span>  
 <span data-ttu-id="fce37-122">若要查看指定文件组中文件的状态，请查询 **sys.database_files** 或 **sys.master_files** 目录视图。</span><span class="sxs-lookup"><span data-stu-id="fce37-122">To view the state of the files for the specified filegroup, query either the **sys.database_files** or **sys.master_files** catalog view.</span></span>  
  
 <span data-ttu-id="fce37-123">从备份还原离线文件。</span><span class="sxs-lookup"><span data-stu-id="fce37-123">Restore the offline file from a backup.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fce37-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fce37-124">See Also</span></span>  
 <span data-ttu-id="fce37-125">[sys.database_files (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-database-files-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="fce37-125">[sys.database_files &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-files-transact-sql) </span></span>  
 <span data-ttu-id="fce37-126">[sys. master_files &#40;Transact-sql&#41;](/sql/relational-databases/system-catalog-views/sys-master-files-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="fce37-126">[sys.master_files &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-master-files-transact-sql) </span></span>  
 [<span data-ttu-id="fce37-127">RESTORE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="fce37-127">RESTORE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-transact-sql)  
  
  
