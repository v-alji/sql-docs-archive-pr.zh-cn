---
title: 使用 Transact-SQL 访问 FILESTREAM 数据 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- FILESTREAM [SQL Server], Transact-SQL
ms.assetid: a6bf0ce7-7e5e-4a07-8917-ee526c9d0a05
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 06d395f1acc3723fc6b45fdfa08efbae354d8014
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690658"
---
# <a name="access-filestream-data-with-transact-sql"></a><span data-ttu-id="df94f-102">使用 Transact-SQL 访问 FILESTREAM 数据</span><span class="sxs-lookup"><span data-stu-id="df94f-102">Access FILESTREAM Data with Transact-SQL</span></span>
  <span data-ttu-id="df94f-103">本主题介绍如何使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] INSERT、UPDATE 和 DELETE 语句来管理 FILESTREAM 数据。</span><span class="sxs-lookup"><span data-stu-id="df94f-103">This topic describes how to use the [!INCLUDE[tsql](../../includes/tsql-md.md)] INSERT, UPDATE, and DELETE statements to manage FILESTREAM data.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="df94f-104">本主题中的示例需要在 [创建启用 FILESTREAM 的数据库](create-a-filestream-enabled-database.md) 和 [创建表以存储 FILESTREAM 数据](create-a-table-for-storing-filestream-data.md)中创建的启用了 FILESTREAM 的数据库和表。</span><span class="sxs-lookup"><span data-stu-id="df94f-104">The examples in this topic require the FILESTREAM-enabled database and table that are created in [Create a FILESTREAM-Enabled Database](create-a-filestream-enabled-database.md) and [Create a Table for Storing FILESTREAM Data](create-a-table-for-storing-filestream-data.md).</span></span>  
  
##  <a name="inserting-a-row-that-contains-filestream-data"></a><a name="ins"></a> <span data-ttu-id="df94f-105">插入包含 FILESTREAM 数据的行</span><span class="sxs-lookup"><span data-stu-id="df94f-105">Inserting a Row That Contains FILESTREAM Data</span></span>  
 <span data-ttu-id="df94f-106">若要在支持 FILESTREAM 数据的表中插入一行，请使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] INSERT 语句。</span><span class="sxs-lookup"><span data-stu-id="df94f-106">To add a row to a table that supports FILESTREAM data, use the [!INCLUDE[tsql](../../includes/tsql-md.md)] INSERT statement.</span></span> <span data-ttu-id="df94f-107">在 FILESTREAM 列中插入数据时，可以插入 NULL 或 `varbinary(max)` 值。</span><span class="sxs-lookup"><span data-stu-id="df94f-107">When you insert data into a FILESTREAM column, you can insert NULL or a `varbinary(max)` value.</span></span>  
  
### <a name="inserting-null"></a><span data-ttu-id="df94f-108">插入 NULL</span><span class="sxs-lookup"><span data-stu-id="df94f-108">Inserting NULL</span></span>  
 <span data-ttu-id="df94f-109">下面的示例说明了如何插入 `NULL`。</span><span class="sxs-lookup"><span data-stu-id="df94f-109">The following example shows how to insert `NULL`.</span></span> <span data-ttu-id="df94f-110">如果 FILESTREAM 值为 `NULL`，则 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 不会在文件系统中创建文件。</span><span class="sxs-lookup"><span data-stu-id="df94f-110">When the FILESTREAM value is `NULL`, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] does not create a file in the file system.</span></span>  
  
 [!code-sql[FILESTREAM#FS_InsertNULL](../../snippets/tsql/SQL15/tsql/filestream/transact-sql/filestream.sql#fs_insertnull)]  
  
### <a name="inserting-a-zero-length-record"></a><span data-ttu-id="df94f-111">插入长度为零的记录</span><span class="sxs-lookup"><span data-stu-id="df94f-111">Inserting a Zero-Length Record</span></span>  
 <span data-ttu-id="df94f-112">下面的示例说明了如何使用 `INSERT` 创建长度为零的记录。</span><span class="sxs-lookup"><span data-stu-id="df94f-112">The following example shows how to use `INSERT` to create a zero-length record.</span></span> <span data-ttu-id="df94f-113">如果您要获取文件句柄，但使用 Win32 API 来操作文件，这是非常有用的。</span><span class="sxs-lookup"><span data-stu-id="df94f-113">This is useful for when you want to obtain a file handle, but will be manipulating the file by using Win32 APIs.</span></span>  
  
 [!code-sql[FILESTREAM#FS_InsertZero](../../snippets/tsql/SQL15/tsql/filestream/transact-sql/filestream.sql#fs_insertzero)]  
  
### <a name="creating-a-data-file"></a><span data-ttu-id="df94f-114">创建数据文件</span><span class="sxs-lookup"><span data-stu-id="df94f-114">Creating a Data File</span></span>  
 <span data-ttu-id="df94f-115">下面的示例说明了如何使用 `INSERT` 创建包含数据的文件。</span><span class="sxs-lookup"><span data-stu-id="df94f-115">The following example shows how to use `INSERT` to create a file that contains data.</span></span> <span data-ttu-id="df94f-116">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 将字符串 `Seismic Data` 转换为 `varbinary(max)` 值。</span><span class="sxs-lookup"><span data-stu-id="df94f-116">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] converts the string `Seismic Data` to a `varbinary(max)` value.</span></span> <span data-ttu-id="df94f-117">如果 Windows 文件尚未存在，FILESTREAM 将创建该文件。然后，在数据文件中添加数据。</span><span class="sxs-lookup"><span data-stu-id="df94f-117">FILESTREAM creates the Windows file if it does not already exist.The data is then added to the data file.</span></span>  
  
 [!code-sql[FILESTREAM#FS_InsertData](../../snippets/tsql/SQL15/tsql/filestream/transact-sql/filestream.sql#fs_insertdata)]  
  
 <span data-ttu-id="df94f-118">如果选择 `Archive`。`dbo.Records`</span><span class="sxs-lookup"><span data-stu-id="df94f-118">When you select all data from the `Archive`.`dbo.Records`</span></span> <span data-ttu-id="df94f-119">表中的所有数据，则结果与下表中显示的结果类似。</span><span class="sxs-lookup"><span data-stu-id="df94f-119">table, the results are similar to the results that are shown in the following table.</span></span> <span data-ttu-id="df94f-120">但是， `Id` 列将包含不同的 GUID。</span><span class="sxs-lookup"><span data-stu-id="df94f-120">However, the `Id` column will contain different GUIDs.</span></span>  
  
|<span data-ttu-id="df94f-121">ID</span><span class="sxs-lookup"><span data-stu-id="df94f-121">Id</span></span>|<span data-ttu-id="df94f-122">SerialNumber</span><span class="sxs-lookup"><span data-stu-id="df94f-122">SerialNumber</span></span>|<span data-ttu-id="df94f-123">继续</span><span class="sxs-lookup"><span data-stu-id="df94f-123">Resume</span></span>|  
|--------|------------------|------------|  
|`C871B90F-D25E-47B3-A560-7CC0CA405DAC`|`1`|`NULL`|  
|`F8F5C314-0559-4927-8FA9-1535EE0BDF50`|`2`|`0x`|  
|`7F680840-B7A4-45D4-8CD5-527C44D35B3F`|`3`|`0x536569736D69632044617461`|  
  
##  <a name="updating-filestream-data"></a><a name="upd"></a> <span data-ttu-id="df94f-124">更新 FILESTREAM 数据</span><span class="sxs-lookup"><span data-stu-id="df94f-124">Updating FILESTREAM Data</span></span>  
 <span data-ttu-id="df94f-125">可以使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 更新文件系统文件中的数据；但是，如果必须以流的方式将大量数据传输到文件，您可能并不希望这样做。</span><span class="sxs-lookup"><span data-stu-id="df94f-125">You can use [!INCLUDE[tsql](../../includes/tsql-md.md)] to update the data in the file system file; although, you might not want to do this when you have to stream large amounts of data to a file.</span></span>  
  
 <span data-ttu-id="df94f-126">下面的示例将文件记录中的所有文本替换为文本 `Xray 1`。</span><span class="sxs-lookup"><span data-stu-id="df94f-126">The following example replaces any text in the file record with the text `Xray 1`.</span></span>  
  
 [!code-sql[FILESTREAM#FS_UpdateData](../../snippets/tsql/SQL15/tsql/filestream/transact-sql/filestream.sql#fs_updatedata)]  
  
##  <a name="deleting-filestream-data"></a><a name="del"></a> <span data-ttu-id="df94f-127">删除 FILESTREAM 数据</span><span class="sxs-lookup"><span data-stu-id="df94f-127">Deleting FILESTREAM Data</span></span>  
 <span data-ttu-id="df94f-128">删除包含 FILESTREAM 字段的行时，会同时删除其基础文件系统文件。</span><span class="sxs-lookup"><span data-stu-id="df94f-128">When you delete a row that contains a FILESTREAM field, you also delete its underlying file system files.</span></span> <span data-ttu-id="df94f-129">删除行（从而删除文件）的唯一方式是使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] DELETE 语句。</span><span class="sxs-lookup"><span data-stu-id="df94f-129">The only way to delete a row, and therefore the file, is to use the [!INCLUDE[tsql](../../includes/tsql-md.md)] DELETE statement.</span></span>  
  
 <span data-ttu-id="df94f-130">下面的示例说明了如何删除一行及其关联的文件系统文件。</span><span class="sxs-lookup"><span data-stu-id="df94f-130">The following example shows how to delete a row and its associated file system files.</span></span>  
  
 [!code-sql[FILESTREAM#FS_DeleteData](../../snippets/tsql/SQL15/tsql/filestream/transact-sql/filestream.sql#fs_deletedata)]  
  
 <span data-ttu-id="df94f-131">如果选择 `dbo.Archive` 表中的所有数据，则会发现该行已被删除。</span><span class="sxs-lookup"><span data-stu-id="df94f-131">When you select all data from the `dbo.Archive` table, the row is gone.</span></span> <span data-ttu-id="df94f-132">您无法再使用关联的文件。</span><span class="sxs-lookup"><span data-stu-id="df94f-132">You can no longer use the associated file.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="df94f-133">基础文件是由 FILESTREAM 垃圾回收器删除的。</span><span class="sxs-lookup"><span data-stu-id="df94f-133">The underlying files are removed by the FILESTREAM garbage collector.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df94f-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="df94f-134">See Also</span></span>  
 <span data-ttu-id="df94f-135">[启用和配置 FILESTREAM](enable-and-configure-filestream.md) </span><span class="sxs-lookup"><span data-stu-id="df94f-135">[Enable and Configure FILESTREAM](enable-and-configure-filestream.md) </span></span>  
 [<span data-ttu-id="df94f-136">避免与 FILESTREAM 应用程序中的数据库操作冲突</span><span class="sxs-lookup"><span data-stu-id="df94f-136">Avoid Conflicts with Database Operations in FILESTREAM Applications</span></span>](avoid-conflicts-with-database-operations-in-filestream-applications.md)  
  
  
