---
title: 创建启用了 FILESTREAM 的数据库 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- FILESTREAM [SQL Server], FILESTREAM-enabled databases
ms.assetid: 0fc16356-76f7-44b8-a58b-f0b7c43694ec
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 0fe6e5bc6e4f60bc0703482f3bf4d761104b3c5f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689923"
---
# <a name="create-a-filestream-enabled-database"></a><span data-ttu-id="1ce74-102">创建启用了 FILESTREAM 的数据库</span><span class="sxs-lookup"><span data-stu-id="1ce74-102">Create a FILESTREAM-Enabled Database</span></span>
  <span data-ttu-id="1ce74-103">本主题说明如何创建支持 FILESTREAM 的数据库。</span><span class="sxs-lookup"><span data-stu-id="1ce74-103">This topic shows how to create a database that supports FILESTREAM.</span></span> <span data-ttu-id="1ce74-104">由于 FILESTREAM 使用一种特殊类型的文件组，因此，在创建数据库时，必须至少为一个文件组指定 CONTAINS FILESTREAM 子句。</span><span class="sxs-lookup"><span data-stu-id="1ce74-104">Because FILESTREAM uses a special type of filegroup, when you create the database, you must specify the CONTAINS FILESTREAM clause for at least one filegroup.</span></span>  
  
 <span data-ttu-id="1ce74-105">一个 FILESTREAM 文件组可以包含多个文件。</span><span class="sxs-lookup"><span data-stu-id="1ce74-105">A FILESTREAM filegroup can contain more than one file.</span></span> <span data-ttu-id="1ce74-106">有关演示如何创建包含多个文件的 FILESTREAM 文件组的代码示例，请参阅 [CREATE DATABASE (SQL Server Transact-SQL)](/sql/t-sql/statements/create-database-sql-server-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="1ce74-106">For a code example that demonstrates how to create a FILESTREAM filegroup that contains multiple files, see [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql).</span></span>  
  
### <a name="to-create-a-filestream-enabled-database"></a><span data-ttu-id="1ce74-107">创建启用了 FILESTREAM 的数据库</span><span class="sxs-lookup"><span data-stu-id="1ce74-107">To create a FILESTREAM-enabled database</span></span>  
  
1.  <span data-ttu-id="1ce74-108">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，单击 **“新建查询”** 以显示查询编辑器。</span><span class="sxs-lookup"><span data-stu-id="1ce74-108">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], click **New Query** to display the Query Editor.</span></span>  
  
2.  <span data-ttu-id="1ce74-109">复制 [!INCLUDE[tsql](../../includes/tsql-md.md)] 代码会创建一个名为 Archive 的启用了 FILESTREAM 的数据库。</span><span class="sxs-lookup"><span data-stu-id="1ce74-109">Copy the [!INCLUDE[tsql](../../includes/tsql-md.md)] code creates a FILESTREAM-enabled database called Archive.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="1ce74-110">对于此脚本，C:\Data 目录必须存在。</span><span class="sxs-lookup"><span data-stu-id="1ce74-110">For this script, the directory C:\Data must exist.</span></span>  
  
3.  <span data-ttu-id="1ce74-111">若要生成数据库，请单击 **“执行”** 。</span><span class="sxs-lookup"><span data-stu-id="1ce74-111">To build the database, click **Execute**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1ce74-112">示例</span><span class="sxs-lookup"><span data-stu-id="1ce74-112">Example</span></span>  
 <span data-ttu-id="1ce74-113">下面的代码示例创建一个名为 `Archive`的数据库。</span><span class="sxs-lookup"><span data-stu-id="1ce74-113">The following code example creates a database that is named `Archive`.</span></span> <span data-ttu-id="1ce74-114">该数据库包含三个文件组： `PRIMARY`、 `Arch1`和 `FileStreamGroup1`。</span><span class="sxs-lookup"><span data-stu-id="1ce74-114">The database contains three filegroups: `PRIMARY`, `Arch1`, and `FileStreamGroup1`.</span></span> <span data-ttu-id="1ce74-115">`PRIMARY` 和 `Arch1` 是不能包含 FILESTREAM 数据的常规文件组。</span><span class="sxs-lookup"><span data-stu-id="1ce74-115">`PRIMARY` and `Arch1` are regular filegroups that cannot contain FILESTREAM data.</span></span> <span data-ttu-id="1ce74-116">`FileStreamGroup1` 是 `FILESTREAM` 文件组。</span><span class="sxs-lookup"><span data-stu-id="1ce74-116">`FileStreamGroup1` is the `FILESTREAM` filegroup.</span></span>  
  
```sql  
CREATE DATABASE Archive   
ON  
PRIMARY ( NAME = Arch1,  
    FILENAME = 'c:\data\archdat1.mdf'),  
FILEGROUP FileStreamGroup1 CONTAINS FILESTREAM( NAME = Arch3,  
    FILENAME = 'c:\data\filestream1')  
LOG ON  ( NAME = Archlog1,  
    FILENAME = 'c:\data\archlog1.ldf')  
GO  
```  
  
 <span data-ttu-id="1ce74-117">对于 `FILESTREAM` 文件组， `FILENAME` 引用一个路径。</span><span class="sxs-lookup"><span data-stu-id="1ce74-117">For a `FILESTREAM` filegroup, `FILENAME` refers to a path.</span></span> <span data-ttu-id="1ce74-118">在最后一个文件夹之前的路径必须存在，但不能存在最后一个文件夹。</span><span class="sxs-lookup"><span data-stu-id="1ce74-118">The path up to the last folder must exist, and the last folder must not exist.</span></span> <span data-ttu-id="1ce74-119">在此示例中， `c:\data` 必须存在。</span><span class="sxs-lookup"><span data-stu-id="1ce74-119">In this example, `c:\data` must exist.</span></span> <span data-ttu-id="1ce74-120">但是，在执行 `filestream1` 语句时， `CREATE DATABASE` 子文件夹不能存在。</span><span class="sxs-lookup"><span data-stu-id="1ce74-120">However, the `filestream1` subfolder cannot exist when you execute the `CREATE DATABASE` statement.</span></span> <span data-ttu-id="1ce74-121">有关语法的详细信息，请参阅 [CREATE DATABASE (SQL Server Transact-SQL)](/sql/t-sql/statements/create-database-sql-server-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="1ce74-121">For more information about the syntax, see [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql).</span></span>  
  
 <span data-ttu-id="1ce74-122">在运行上面的示例后，filestream.hdr 文件和 $FSLOG 文件夹将出现在 c:\Data\filestream1 文件夹中。</span><span class="sxs-lookup"><span data-stu-id="1ce74-122">After you run the previous example, a filestream.hdr file and an $FSLOG folder appears in the c:\Data\filestream1 folder.</span></span> <span data-ttu-id="1ce74-123">filestream.hdr 文件是 FILESTREAM 容器的头文件。</span><span class="sxs-lookup"><span data-stu-id="1ce74-123">The filestream.hdr file is a header file for the FILESTREAM container.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="1ce74-124">filestream.hdr 文件是重要的系统文件。</span><span class="sxs-lookup"><span data-stu-id="1ce74-124">The filestream.hdr file is an important system file.</span></span> <span data-ttu-id="1ce74-125">它包含 FILESTREAM 标头信息。</span><span class="sxs-lookup"><span data-stu-id="1ce74-125">It contains FILESTREAM header information.</span></span> <span data-ttu-id="1ce74-126">请勿删除或修改此文件。</span><span class="sxs-lookup"><span data-stu-id="1ce74-126">Do not remove or modify this file.</span></span>  
  
 <span data-ttu-id="1ce74-127">对于现有数据库，可以使用 [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql) 语句来添加 FILESTREAM 文件组。</span><span class="sxs-lookup"><span data-stu-id="1ce74-127">For existing databases, you can use the [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql) statement to add a FILESTREAM filegroup.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ce74-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1ce74-128">See Also</span></span>  
 <span data-ttu-id="1ce74-129">[CREATE DATABASE (SQL Server Transact-SQL)](/sql/t-sql/statements/create-database-sql-server-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="1ce74-129">[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) </span></span>  
 [<span data-ttu-id="1ce74-130">ALTER DATABASE (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="1ce74-130">ALTER DATABASE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-database-transact-sql)  
  
  
