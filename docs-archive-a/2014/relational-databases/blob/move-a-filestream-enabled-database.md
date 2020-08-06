---
title: 移动启用了 FILESTREAM 的数据库 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- FILESTREAM [SQL Server], moving a FILESTREAM-enabled database
ms.assetid: dd4d270d-9283-431a-aa6b-e571fced1893
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 79740ee86a89566113650865e3fd6ec54c7cb918
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682895"
---
# <a name="move-a-filestream-enabled-database"></a><span data-ttu-id="e8d28-102">移动启用了 FILESTREAM 的数据库</span><span class="sxs-lookup"><span data-stu-id="e8d28-102">Move a FILESTREAM-Enabled Database</span></span>
  <span data-ttu-id="e8d28-103">本主题演示如何移动启用了 FILESTREAM 的数据库。</span><span class="sxs-lookup"><span data-stu-id="e8d28-103">This topic shows how to move a FILESTREAM-enabled database.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e8d28-104">本主题中的示例需要使用在 [创建启用了 FILESTREAM 的数据库](create-a-filestream-enabled-database.md)中创建的存档数据库。</span><span class="sxs-lookup"><span data-stu-id="e8d28-104">The examples in this topic require the Archive database that is created in [Create a FILESTREAM-Enabled Database](create-a-filestream-enabled-database.md).</span></span>  
  
### <a name="to-move-a-filestream-enabled-database"></a><span data-ttu-id="e8d28-105">移动启用了 FILESTREAM 的数据库</span><span class="sxs-lookup"><span data-stu-id="e8d28-105">To move a FILESTREAM-enabled database</span></span>  
  
1.  <span data-ttu-id="e8d28-106">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，单击 **“新建查询”** 以打开查询编辑器。</span><span class="sxs-lookup"><span data-stu-id="e8d28-106">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], click **New Query** to open the Query Editor.</span></span>  
  
2.  <span data-ttu-id="e8d28-107">将以下 [!INCLUDE[tsql](../../includes/tsql-md.md)] 脚本复制到查询编辑器中，然后单击“执行”。 </span><span class="sxs-lookup"><span data-stu-id="e8d28-107">Copy the following [!INCLUDE[tsql](../../includes/tsql-md.md)] script into the Query Editor, and then click **Execute**.</span></span> <span data-ttu-id="e8d28-108">此脚本显示 FILESTREAM 数据库所使用的物理数据库文件的位置。</span><span class="sxs-lookup"><span data-stu-id="e8d28-108">This script displays the location of the physical database files that the FILESTREAM database uses.</span></span>  
  
    ```sql  
    USE Archive  
    GO  
    SELECT type_desc, name, physical_name from sys.database_files  
    ```  
  
3.  <span data-ttu-id="e8d28-109">将以下 [!INCLUDE[tsql](../../includes/tsql-md.md)] 脚本复制到查询编辑器中，然后单击“执行”。 </span><span class="sxs-lookup"><span data-stu-id="e8d28-109">Copy the following [!INCLUDE[tsql](../../includes/tsql-md.md)] script into the Query Editor, and then click **Execute**.</span></span> <span data-ttu-id="e8d28-110">此代码使 `Archive` 数据库脱机。</span><span class="sxs-lookup"><span data-stu-id="e8d28-110">This code takes the `Archive` database offline.</span></span>  
  
    ```sql  
    USE master  
    EXEC sp_detach_db Archive  
    GO  
    ```  
  
4.  <span data-ttu-id="e8d28-111">创建文件夹 `C:\moved_location`，然后将步骤 2 中列出的文件和文件夹移动到该文件夹中。</span><span class="sxs-lookup"><span data-stu-id="e8d28-111">Create the folder `C:\moved_location`, and then move the files and folders that are listed in step 2 into it.</span></span>  
  
5.  <span data-ttu-id="e8d28-112">将以下 [!INCLUDE[tsql](../../includes/tsql-md.md)] 脚本复制到查询编辑器中，然后单击“执行”。 </span><span class="sxs-lookup"><span data-stu-id="e8d28-112">Copy the following [!INCLUDE[tsql](../../includes/tsql-md.md)] script into the Query Editor, and then click **Execute**.</span></span> <span data-ttu-id="e8d28-113">此脚本将 `Archive` 数据库设置为脱机。</span><span class="sxs-lookup"><span data-stu-id="e8d28-113">This script sets the `Archive` database online.</span></span>  
  
    ```sql  
    CREATE DATABASE Archive ON  
    PRIMARY ( NAME = Arch1,  
        FILENAME = 'c:\moved_location\archdat1.mdf'),  
    FILEGROUP FileStreamGroup1 CONTAINS FILESTREAM( NAME = Arch3,  
        FILENAME = 'c:\moved_location\filestream1')  
    LOG ON  ( NAME = Archlog1,  
        FILENAME = 'c:\moved_location\archlog1.ldf')  
    FOR ATTACH  
    GO  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="e8d28-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e8d28-114">See Also</span></span>  
 [<span data-ttu-id="e8d28-115">sp_detach_db (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="e8d28-115">sp_detach_db &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-detach-db-transact-sql)  
  
  
