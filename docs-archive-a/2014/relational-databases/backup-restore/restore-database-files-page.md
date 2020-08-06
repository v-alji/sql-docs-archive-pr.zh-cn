---
title: 还原数据库（“文件”页）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.restoredb.files.f1 in the code
- sql12.swb.restoredb.files.f1
ms.assetid: 714c36ea-a9f9-43a4-99f9-a6f73d1baf8e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: edffd9454b51ea80a18311f735d29407f97f6eb6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589159"
---
# <a name="restore-database-files-page"></a><span data-ttu-id="fe8c7-102">还原数据库（“文件”页）</span><span class="sxs-lookup"><span data-stu-id="fe8c7-102">Restore Database (Files Page)</span></span>
  <span data-ttu-id="fe8c7-103">使用 **“还原数据库”** 对话框的 **“文件”** 页可以管理数据库中您选择要还原的特定文件。</span><span class="sxs-lookup"><span data-stu-id="fe8c7-103">Use the **Files** page of the **Restore Database** dialog box to manage the specific files you have chosen to restore within the database.</span></span>  
  
## <a name="options"></a><span data-ttu-id="fe8c7-104">选项</span><span class="sxs-lookup"><span data-stu-id="fe8c7-104">Options</span></span>  
  
### <a name="restore-database-files-as"></a><span data-ttu-id="fe8c7-105">将数据库文件还原为</span><span class="sxs-lookup"><span data-stu-id="fe8c7-105">Restore database files as</span></span>  
 <span data-ttu-id="fe8c7-106">用来向还原的文件分配新文件路径并进行管理。</span><span class="sxs-lookup"><span data-stu-id="fe8c7-106">Use to assign and manage the new file path to the restored files.</span></span>  
  
 <span data-ttu-id="fe8c7-107">**将所有文件重新定位到文件夹**</span><span class="sxs-lookup"><span data-stu-id="fe8c7-107">**Relocate all files to folder**</span></span>  
 <span data-ttu-id="fe8c7-108">重新定位还原的文件。</span><span class="sxs-lookup"><span data-stu-id="fe8c7-108">Relocates restored files.</span></span>  
  
|<span data-ttu-id="fe8c7-109">选项</span><span class="sxs-lookup"><span data-stu-id="fe8c7-109">Option</span></span>|<span data-ttu-id="fe8c7-110">说明</span><span class="sxs-lookup"><span data-stu-id="fe8c7-110">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="fe8c7-111">**数据文件的文件夹**</span><span class="sxs-lookup"><span data-stu-id="fe8c7-111">**Data file folder**</span></span>|<span data-ttu-id="fe8c7-112">输入或搜索应将还原的数据文件重新定位到的数据文件的文件夹名称。</span><span class="sxs-lookup"><span data-stu-id="fe8c7-112">Enter or search for the data file folder name that the restored data file or files should be relocated to.</span></span>|  
|<span data-ttu-id="fe8c7-113">**日志文件的文件夹**</span><span class="sxs-lookup"><span data-stu-id="fe8c7-113">**Log file folder**</span></span>|<span data-ttu-id="fe8c7-114">输入或搜索应将还原的日志文件文件重新定位到的日志文件的文件夹。</span><span class="sxs-lookup"><span data-stu-id="fe8c7-114">Enter or search for the log file or files folder that the restored log file should be relocated to.</span></span>|  
  
 <span data-ttu-id="fe8c7-115">**逻辑文件名**</span><span class="sxs-lookup"><span data-stu-id="fe8c7-115">**Logical File Name**</span></span>  
 <span data-ttu-id="fe8c7-116">对于每个要还原的数据库文件显示一行。</span><span class="sxs-lookup"><span data-stu-id="fe8c7-116">Displays one row for each database file to be restored.</span></span>  
  
 <span data-ttu-id="fe8c7-117">**文件类型**</span><span class="sxs-lookup"><span data-stu-id="fe8c7-117">**File Type**</span></span>  
 <span data-ttu-id="fe8c7-118">显示文件类型。</span><span class="sxs-lookup"><span data-stu-id="fe8c7-118">Displays the file type.</span></span>  
  
 <span data-ttu-id="fe8c7-119">**原始文件名**</span><span class="sxs-lookup"><span data-stu-id="fe8c7-119">**Original File Name**</span></span>  
 <span data-ttu-id="fe8c7-120">显示已还原文件的原始文件路径。</span><span class="sxs-lookup"><span data-stu-id="fe8c7-120">Displays the original file path for the restored file.</span></span>  
  
 <span data-ttu-id="fe8c7-121">**还原为**</span><span class="sxs-lookup"><span data-stu-id="fe8c7-121">**Restore As**</span></span>  
 <span data-ttu-id="fe8c7-122">列出用于另存还原文件的文件名。</span><span class="sxs-lookup"><span data-stu-id="fe8c7-122">Lists the file names that the restored files are to be saved as.</span></span> <span data-ttu-id="fe8c7-123">输入或搜索适当的文件名。</span><span class="sxs-lookup"><span data-stu-id="fe8c7-123">Enter or search for the appropriate file name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe8c7-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fe8c7-124">See Also</span></span>  
 <span data-ttu-id="fe8c7-125">[还原数据库（“常规”页）](../../integration-services/general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="fe8c7-125">[Restore Database &#40;General Page&#41;](../../integration-services/general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="fe8c7-126">[还原数据库（“选项”页）](restore-database-options-page.md) </span><span class="sxs-lookup"><span data-stu-id="fe8c7-126">[Restore Database &#40;Options Page&#41;](restore-database-options-page.md) </span></span>  
 <span data-ttu-id="fe8c7-127">[RESTORE 参数 (Transact-SQL)](/sql/t-sql/statements/restore-statements-arguments-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="fe8c7-127">[RESTORE Arguments &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-arguments-transact-sql) </span></span>  
 <span data-ttu-id="fe8c7-128">[为磁带驱动器定义逻辑备份设备 (SQL Server)](define-a-logical-backup-device-for-a-tape-drive-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="fe8c7-128">[Define a Logical Backup Device for a Tape Drive &#40;SQL Server&#41;](define-a-logical-backup-device-for-a-tape-drive-sql-server.md) </span></span>  
 [<span data-ttu-id="fe8c7-129">RESTORE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="fe8c7-129">RESTORE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-transact-sql)  
  
  
