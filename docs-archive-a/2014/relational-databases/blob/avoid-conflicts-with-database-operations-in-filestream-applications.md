---
title: 避免与 FILESTREAM 应用程序中的数据库操作冲突 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.technology: filestream
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- FILESTREAM [SQL Server], Win32 and Transact-SQL Conflicts
ms.assetid: 8b1ee196-69af-4f9b-9bf5-63d8ac2bc39b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 0ac7e681766396d3a3b4412d91a968b4cdc653c4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589728"
---
# <a name="avoid-conflicts-with-database-operations-in-filestream-applications"></a><span data-ttu-id="07a7b-102">避免与 FILESTREAM 应用程序中的数据库操作冲突</span><span class="sxs-lookup"><span data-stu-id="07a7b-102">Avoid Conflicts with Database Operations in FILESTREAM Applications</span></span>
  <span data-ttu-id="07a7b-103">使用 SqlOpenFilestream() 打开 Win32 文件句柄以读取或写入 FILESTREAM BLOB 数据的应用程序可能会遇到与在通用事务中管理的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句的冲突错误。</span><span class="sxs-lookup"><span data-stu-id="07a7b-103">Applications that use SqlOpenFilestream() to open Win32 file handles for reading or writing FILESTREAM BLOB data can encounter conflict errors with [!INCLUDE[tsql](../../includes/tsql-md.md)] statements that are managed in a common transaction.</span></span> <span data-ttu-id="07a7b-104">这包括花很长时间才能完成执行的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 或 MARS 查询。</span><span class="sxs-lookup"><span data-stu-id="07a7b-104">This includes [!INCLUDE[tsql](../../includes/tsql-md.md)] or MARS queries that take a long time to finish execution.</span></span> <span data-ttu-id="07a7b-105">为了有助于避免这些类型的冲突，必须精心设计应用程序。</span><span class="sxs-lookup"><span data-stu-id="07a7b-105">Applications must be carefully designed to help avoid these types of conflicts.</span></span>  
  
 <span data-ttu-id="07a7b-106">当 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 或应用程序尝试打开 FILESTREAM BLOB 时， [!INCLUDE[ssDE](../../includes/ssde-md.md)] 会检查关联事务上下文。</span><span class="sxs-lookup"><span data-stu-id="07a7b-106">When [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] or applications try to open FILESTREAM BLOBs, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] checks the associated transaction context.</span></span> <span data-ttu-id="07a7b-107">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 根据打开操作是在处理 DDL 语句、DML 语句，在检索数据还是在管理事务，从而允许或拒绝请求。</span><span class="sxs-lookup"><span data-stu-id="07a7b-107">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] allows or denies the request based on whether the open operation is working with DDL statements, DML statements, retrieving data, or managing transactions.</span></span> <span data-ttu-id="07a7b-108">下表显示 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 如何根据事务中打开的文件的类型来确定是允许还是拒绝 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句。</span><span class="sxs-lookup"><span data-stu-id="07a7b-108">The following table shows how the [!INCLUDE[ssDE](../../includes/ssde-md.md)] determines whether a [!INCLUDE[tsql](../../includes/tsql-md.md)] statement will be allowed or denied based on the type of files that are open in the transaction.</span></span>  
  
|<span data-ttu-id="07a7b-109">Transact-SQL 语句</span><span class="sxs-lookup"><span data-stu-id="07a7b-109">Transact-SQL statements</span></span>|<span data-ttu-id="07a7b-110">打开以进行读取</span><span class="sxs-lookup"><span data-stu-id="07a7b-110">Opened for read</span></span>|<span data-ttu-id="07a7b-111">打开以进行写入</span><span class="sxs-lookup"><span data-stu-id="07a7b-111">Opened for write</span></span>|  
|------------------------------|---------------------|----------------------|  
|<span data-ttu-id="07a7b-112">处理数据库元数据的 DDL 语句，例如 CREATE TABLE、CREATE INDEX、DROP TABLE 和 ALTER TABLE。</span><span class="sxs-lookup"><span data-stu-id="07a7b-112">DDL statements that work with database metadata, such as CREATE TABLE, CREATE INDEX, DROP TABLE, and ALTER TABLE.</span></span>|<span data-ttu-id="07a7b-113">允许</span><span class="sxs-lookup"><span data-stu-id="07a7b-113">Allowed</span></span>|<span data-ttu-id="07a7b-114">被阻止，并因超时而失败。</span><span class="sxs-lookup"><span data-stu-id="07a7b-114">Are blocked and fail with a time-out.</span></span>|  
|<span data-ttu-id="07a7b-115">处理存储在数据库中的数据的 DML 语句，例如 UPDATE、DELETE 和 INSERT。</span><span class="sxs-lookup"><span data-stu-id="07a7b-115">DML statements that work with the data that is stored in the database, such as UPDATE, DELETE, and INSERT.</span></span>|<span data-ttu-id="07a7b-116">允许</span><span class="sxs-lookup"><span data-stu-id="07a7b-116">Allowed</span></span>|<span data-ttu-id="07a7b-117">拒绝</span><span class="sxs-lookup"><span data-stu-id="07a7b-117">Denied</span></span>|  
|<span data-ttu-id="07a7b-118">SELECT</span><span class="sxs-lookup"><span data-stu-id="07a7b-118">SELECT</span></span>|<span data-ttu-id="07a7b-119">允许</span><span class="sxs-lookup"><span data-stu-id="07a7b-119">Allowed</span></span>|<span data-ttu-id="07a7b-120">允许</span><span class="sxs-lookup"><span data-stu-id="07a7b-120">Allowed</span></span>|  
|<span data-ttu-id="07a7b-121">COMMIT TRANSACTION</span><span class="sxs-lookup"><span data-stu-id="07a7b-121">COMMIT TRANSACTION</span></span>|<span data-ttu-id="07a7b-122">拒绝\*</span><span class="sxs-lookup"><span data-stu-id="07a7b-122">Denied\*</span></span>|<span data-ttu-id="07a7b-123">拒绝\*</span><span class="sxs-lookup"><span data-stu-id="07a7b-123">Denied\*.</span></span>|  
|<span data-ttu-id="07a7b-124">SAVE TRANSACTION</span><span class="sxs-lookup"><span data-stu-id="07a7b-124">SAVE TRANSACTION</span></span>|<span data-ttu-id="07a7b-125">拒绝\*</span><span class="sxs-lookup"><span data-stu-id="07a7b-125">Denied\*</span></span>|<span data-ttu-id="07a7b-126">拒绝\*</span><span class="sxs-lookup"><span data-stu-id="07a7b-126">Denied\*</span></span>|  
|<span data-ttu-id="07a7b-127">ROLLBACK</span><span class="sxs-lookup"><span data-stu-id="07a7b-127">ROLLBACK</span></span>|<span data-ttu-id="07a7b-128">允许\*</span><span class="sxs-lookup"><span data-stu-id="07a7b-128">Allowed\*</span></span>|<span data-ttu-id="07a7b-129">允许\*</span><span class="sxs-lookup"><span data-stu-id="07a7b-129">Allowed\*</span></span>|  
  
 <span data-ttu-id="07a7b-130">\* 取消事务，并且事务上下文的打开句柄无效。</span><span class="sxs-lookup"><span data-stu-id="07a7b-130">\* The transaction is canceled, and open handles for the transaction context are invalidated.</span></span> <span data-ttu-id="07a7b-131">应用程序必须关闭所有打开句柄。</span><span class="sxs-lookup"><span data-stu-id="07a7b-131">The application must close all open handles.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="07a7b-132">示例</span><span class="sxs-lookup"><span data-stu-id="07a7b-132">Examples</span></span>  
 <span data-ttu-id="07a7b-133">以下示例显示 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句和 FILESTREAM Win32 访问是如何导致冲突的。</span><span class="sxs-lookup"><span data-stu-id="07a7b-133">The following examples show how [!INCLUDE[tsql](../../includes/tsql-md.md)] statements and FILESTREAM Win32 access can cause conflicts.</span></span>  
  
### <a name="a-opening-a-filestream-blob-for-write-access"></a><span data-ttu-id="07a7b-134">A.</span><span class="sxs-lookup"><span data-stu-id="07a7b-134">A.</span></span> <span data-ttu-id="07a7b-135">打开 FILESTREAM BLOB 以进行写访问</span><span class="sxs-lookup"><span data-stu-id="07a7b-135">Opening a FILESTREAM BLOB for write access</span></span>  
 <span data-ttu-id="07a7b-136">下例显示打开文件以仅进行写访问的效果。</span><span class="sxs-lookup"><span data-stu-id="07a7b-136">The following example shows the effect of opening a file for write access only.</span></span>  
  
```  
dstHandle =  OpenSqlFilestream(dstFilePath, Write, 0,  
    transactionToken, cbTransactionToken, 0);  
  
//Write some date to the FILESTREAM BLOB.  
WriteFile(dstHandle, updateData, ...);  
  
//DDL statements will be denied.  
//DML statements will be denied.  
//SELECT statements will be allowed. The FILESTREAM BLOB is  
//returned without the modifications that are made by  
//WriteFile(dstHandle, updateData, ...).  
CloseHandle(dstHandle);  
  
//DDL statements will be allowed.  
//DML statements will be allowed.  
//SELECT statements will be allowed. The FILESTREAM BLOB  
//is returned with the updateData applied.  
```  
  
### <a name="b-opening-a-filestream-blob-for-read-access"></a><span data-ttu-id="07a7b-137">B.</span><span class="sxs-lookup"><span data-stu-id="07a7b-137">B.</span></span> <span data-ttu-id="07a7b-138">打开 FILESTREAM BLOB 以进行读访问</span><span class="sxs-lookup"><span data-stu-id="07a7b-138">Opening a FILESTREAM BLOB for read access</span></span>  
 <span data-ttu-id="07a7b-139">下例显示打开文件以仅进行读访问的效果。</span><span class="sxs-lookup"><span data-stu-id="07a7b-139">The following example shows the effect of opening a file for read access only.</span></span>  
  
```  
dstHandle =  OpenSqlFilestream(dstFilePath, Read, 0,  
    transactionToken, cbTransactionToken, 0);  
//DDL statements will be denied.  
//DML statements will be allowed. Any changes that are  
//made to the FILESTREAM BLOB will not be returned until  
//the dstHandle is closed.  
//SELECT statements will be allowed.  
CloseHandle(dstHandle);  
  
//DDL statements will be allowed.  
//DML statements will be allowed.  
//SELECT statements will be allowed.  
```  
  
### <a name="c-opening-and-closing-multiple-filestream-blob-files"></a><span data-ttu-id="07a7b-140">C.</span><span class="sxs-lookup"><span data-stu-id="07a7b-140">C.</span></span> <span data-ttu-id="07a7b-141">打开和关闭多个 FILESTREAM BLOB 文件</span><span class="sxs-lookup"><span data-stu-id="07a7b-141">Opening and closing multiple FILESTREAM BLOB files</span></span>  
 <span data-ttu-id="07a7b-142">如果打开多个文件，则会使用限制性最强的规则。</span><span class="sxs-lookup"><span data-stu-id="07a7b-142">If multiple files are open, the most restrictive rule is used.</span></span> <span data-ttu-id="07a7b-143">下例打开了两个文件。</span><span class="sxs-lookup"><span data-stu-id="07a7b-143">The following example opens two files.</span></span> <span data-ttu-id="07a7b-144">打开第一个文件以进行读取，打开第二个文件以进行写入。</span><span class="sxs-lookup"><span data-stu-id="07a7b-144">The first file is opened for read and the second for write.</span></span> <span data-ttu-id="07a7b-145">DML 语句将被拒绝，直到第二个文件打开为止。</span><span class="sxs-lookup"><span data-stu-id="07a7b-145">DML statements will be denied until the second file is opened.</span></span>  
  
```  
dstHandle =  OpenSqlFilestream(dstFilePath, Read, 0,  
    transactionToken, cbTransactionToken, 0);  
//DDL statements will be denied.  
//DML statements will be allowed.  
//SELECT statements will be allowed.  
  
dstHandle1 =  OpenSqlFilestream(dstFilePath1, Write, 0,  
    transactionToken, cbTransactionToken, 0);  
  
//DDL statements will be denied.  
//DML statements will be denied.  
//SELECT statements will be allowed.  
  
//Close the read handle. The write handle is still open.  
CloseHandle(dstHandle);  
//DML statements are still denied because the write handle is open.  
  
//DDL statements will be denied.  
//DML statements will be denied.  
//SELECT statements will be allowed.  
  
CloseHandle(dstHandle1);  
//DDL statements will be allowed.  
//DML statements will be allowed.  
//SELECT statements will be allowed.  
```  
  
### <a name="d-failing-to-close-a-cursor"></a><span data-ttu-id="07a7b-146">D.</span><span class="sxs-lookup"><span data-stu-id="07a7b-146">D.</span></span> <span data-ttu-id="07a7b-147">无法关闭游标</span><span class="sxs-lookup"><span data-stu-id="07a7b-147">Failing to close a cursor</span></span>  
 <span data-ttu-id="07a7b-148">下例显示的是未关闭的语句游标如何阻止 `OpenSqlFilestream()` 打开 BLOB 进行写访问。</span><span class="sxs-lookup"><span data-stu-id="07a7b-148">The following example shows how a statement cursor that is not closed can prevent `OpenSqlFilestream()` from opening the BLOB for write access.</span></span>  
  
```  
TCHAR *sqlDBQuery =  
TEXT("SELECT GET_FILESTREAM_TRANSACTION_CONTEXT(),")  
TEXT("Chart.PathName() FROM Archive.dbo.Records");  
  
//Execute a long-running Transact-SQL statement. Do not allow  
//the statement to complete before trying to  
//open the file.  
  
SQLExecDirect(hstmt, sqlDBQuery, SQL_NTS);  
  
//Before you call OpenSqlFilestream() any open files  
//that the Cursor the Transact-SQL statement is using  
// must be closed. In this example,  
//SQLCloseCursor(hstmt) is not called so that  
//the transaction will indicate that there is a file  
//open for reading. This will cause the call to  
//OpenSqlFilestream() to fail because the file is  
//still open.  
  
HANDLE srcHandle =  OpenSqlFilestream(srcFilePath,  
     Write, 0,  transactionToken,  cbTransactionToken,  0);  
  
//srcHandle will == INVALID_HANDLE_VALUE because the  
//cursor is still open.  
```  
  
## <a name="see-also"></a><span data-ttu-id="07a7b-149">另请参阅</span><span class="sxs-lookup"><span data-stu-id="07a7b-149">See Also</span></span>  
 <span data-ttu-id="07a7b-150">[使用 OpenSqlFilestream 访问 FILESTREAM 数据](access-filestream-data-with-opensqlfilestream.md) </span><span class="sxs-lookup"><span data-stu-id="07a7b-150">[Access FILESTREAM Data with OpenSqlFilestream](access-filestream-data-with-opensqlfilestream.md) </span></span>  
 [<span data-ttu-id="07a7b-151">使用多个活动的结果集 (MARS)</span><span class="sxs-lookup"><span data-stu-id="07a7b-151">Using Multiple Active Result Sets &#40;MARS&#41;</span></span>](../native-client/features/using-multiple-active-result-sets-mars.md)  
  
  
