---
title: 使用 OpenSqlFilestream 访问 FILESTREAM 数据 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
api_name:
- OpenSqlFilestream
api_location:
- sqlncli11.dll
helpviewer_keywords:
- OpenSqlFilestream
ms.assetid: d8205653-93dd-4599-8cdf-f9199074025f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 1a1416c0104e07c7bd228a723192ecb35bbe9216
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690657"
---
# <a name="access-filestream-data-with-opensqlfilestream"></a><span data-ttu-id="e97dc-102">使用 OpenSqlFilestream 访问 FILESTREAM 数据</span><span class="sxs-lookup"><span data-stu-id="e97dc-102">Access FILESTREAM Data with OpenSqlFilestream</span></span>
  <span data-ttu-id="e97dc-103">OpenSqlFilestream API 为文件系统中存储的 FILESTREAM 二进制大型对象 (BLOB) 获取 Win32 兼容的文件句柄。</span><span class="sxs-lookup"><span data-stu-id="e97dc-103">The OpenSqlFilestream API obtains a Win32 compatible file handle for a FILESTREAM binary large object (BLOB) that is stored in the file system.</span></span> <span data-ttu-id="e97dc-104">句柄可以传递给以下任何 Win32 API：[ReadFile](https://go.microsoft.com/fwlink/?LinkId=86422)、[WriteFile](https://go.microsoft.com/fwlink/?LinkId=86423)、[TransmitFile](https://go.microsoft.com/fwlink/?LinkId=86424)、[SetFilePointer](https://go.microsoft.com/fwlink/?LinkId=86425)、[SetEndOfFile](https://go.microsoft.com/fwlink/?LinkId=86426) 或 [FlushFileBuffers](https://go.microsoft.com/fwlink/?LinkId=86427)。</span><span class="sxs-lookup"><span data-stu-id="e97dc-104">The handle can be passed to any of the following Win32 APIs: [ReadFile](https://go.microsoft.com/fwlink/?LinkId=86422), [WriteFile](https://go.microsoft.com/fwlink/?LinkId=86423), [TransmitFile](https://go.microsoft.com/fwlink/?LinkId=86424), [SetFilePointer](https://go.microsoft.com/fwlink/?LinkId=86425), [SetEndOfFile](https://go.microsoft.com/fwlink/?LinkId=86426), or [FlushFileBuffers](https://go.microsoft.com/fwlink/?LinkId=86427).</span></span> <span data-ttu-id="e97dc-105">如果将此句柄传递给其他任何 Win32 API，将返回错误 ERROR_ACCESS_DENIED。</span><span class="sxs-lookup"><span data-stu-id="e97dc-105">If you pass this handle to any other Win32 API, the error ERROR_ACCESS_DENIED is returned.</span></span> <span data-ttu-id="e97dc-106">必须首先将此句柄传递给 Win32 [CloseHandle](https://go.microsoft.com/fwlink/?LinkId=86428) API 来关闭它，才能提交或回退事务。</span><span class="sxs-lookup"><span data-stu-id="e97dc-106">The handle must be closed by passing it to the Win32 [CloseHandle](https://go.microsoft.com/fwlink/?LinkId=86428) API before the transaction is committed or rolled back.</span></span> <span data-ttu-id="e97dc-107">未能关闭句柄将导致服务器端资源泄漏。</span><span class="sxs-lookup"><span data-stu-id="e97dc-107">Failing to close the handle will cause server-side resource leaks.</span></span>  
  
 <span data-ttu-id="e97dc-108">所有 FILESTREAM 数据容器访问都必须在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 事务中执行。</span><span class="sxs-lookup"><span data-stu-id="e97dc-108">All FILESTREAM data container access must be performed in a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] transaction.</span></span> [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="e97dc-109">语句也可以在同一事务中执行。</span><span class="sxs-lookup"><span data-stu-id="e97dc-109">statements can also be executed in the same transaction.</span></span> <span data-ttu-id="e97dc-110">这样可保持 SQL 数据与 FILESTREAM BLOB 数据之间的一致性。</span><span class="sxs-lookup"><span data-stu-id="e97dc-110">This maintains consistency between the SQL data and FILESTREAM BLOB data.</span></span>  
  
 <span data-ttu-id="e97dc-111">若要使用 Win32 访问 FILESTREAM BLOB，必须启用 [Windows 授权](../security/choose-an-authentication-mode.md) 。</span><span class="sxs-lookup"><span data-stu-id="e97dc-111">To access the FILESTREAM BLOB by using Win32, [Windows Authorization](../security/choose-an-authentication-mode.md) must be enabled.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="e97dc-112">打开文件以进行写入访问时，事务由 FILESTREAM 代理所有。</span><span class="sxs-lookup"><span data-stu-id="e97dc-112">When the file is opened for write access, the transaction is owned by the FILESTREAM agent.</span></span> <span data-ttu-id="e97dc-113">在释放事务之前，仅允许执行 Win32 文件 I/O。</span><span class="sxs-lookup"><span data-stu-id="e97dc-113">Only Win32 file I/O is allowed until the transaction is released.</span></span> <span data-ttu-id="e97dc-114">若要释放事务，必须关闭写句柄。</span><span class="sxs-lookup"><span data-stu-id="e97dc-114">To release the transaction, the write handle must be closed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e97dc-115">语法</span><span class="sxs-lookup"><span data-stu-id="e97dc-115">Syntax</span></span>  
  
```  
  
  HANDLE OpenSqlFilestream (  
  LPCWSTR  
  FilestreamPath  
  ,  
  SQL_FILESTREAM_DESIRED_ACCESS  
  DesiredAccess,  
ULONGOpenOptions,LPBYTEFilestreamTransactionContext,SIZE_TFilestreamTransactionContextLength,PLARGE_INTEGERAllocationSize);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e97dc-116">参数</span><span class="sxs-lookup"><span data-stu-id="e97dc-116">Parameters</span></span>  
 <span data-ttu-id="e97dc-117">*FilestreamPath*</span><span class="sxs-lookup"><span data-stu-id="e97dc-117">*FilestreamPath*</span></span>  
 <span data-ttu-id="e97dc-118">中`nvarchar(max)` [PathName](/sql/relational-databases/system-functions/pathname-transact-sql)函数返回的路径。</span><span class="sxs-lookup"><span data-stu-id="e97dc-118">[in] Is the `nvarchar(max)` path that is returned by the [PathName](/sql/relational-databases/system-functions/pathname-transact-sql) function.</span></span> <span data-ttu-id="e97dc-119">必须从具有 FILESTREAM 表和列的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SELECT 或 UPDATE 权限的帐户的上下文中调用 PathName。</span><span class="sxs-lookup"><span data-stu-id="e97dc-119">PathName must be called from the context of an account that has [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SELECT or UPDATE permissions on the FILESTREAM table and column.</span></span>  
  
 <span data-ttu-id="e97dc-120">*DesiredAccess*</span><span class="sxs-lookup"><span data-stu-id="e97dc-120">*DesiredAccess*</span></span>  
 <span data-ttu-id="e97dc-121">[in] 设置用于访问 FILESTREAM BLOB 数据的模式。</span><span class="sxs-lookup"><span data-stu-id="e97dc-121">[in] Sets the mode used to access FILESTREAM BLOB data.</span></span> <span data-ttu-id="e97dc-122">该值传递到 [DeviceIoControl 函数](https://go.microsoft.com/fwlink/?LinkId=105527)。</span><span class="sxs-lookup"><span data-stu-id="e97dc-122">This value is passed to the [DeviceIoControl Function](https://go.microsoft.com/fwlink/?LinkId=105527).</span></span>  
  
|<span data-ttu-id="e97dc-123">名称</span><span class="sxs-lookup"><span data-stu-id="e97dc-123">Name</span></span>|<span data-ttu-id="e97dc-124">值</span><span class="sxs-lookup"><span data-stu-id="e97dc-124">Value</span></span>|<span data-ttu-id="e97dc-125">含义</span><span class="sxs-lookup"><span data-stu-id="e97dc-125">Meaning</span></span>|  
|----------|-----------|-------------|  
|<span data-ttu-id="e97dc-126">SQL_FILESTREAM_READ</span><span class="sxs-lookup"><span data-stu-id="e97dc-126">SQL_FILESTREAM_READ</span></span>|<span data-ttu-id="e97dc-127">0</span><span class="sxs-lookup"><span data-stu-id="e97dc-127">0</span></span>|<span data-ttu-id="e97dc-128">可从文件中读取数据。</span><span class="sxs-lookup"><span data-stu-id="e97dc-128">Data can be read from the file.</span></span>|  
|<span data-ttu-id="e97dc-129">SQL_FILESTREAM_WRITE</span><span class="sxs-lookup"><span data-stu-id="e97dc-129">SQL_FILESTREAM_WRITE</span></span>|<span data-ttu-id="e97dc-130">1</span><span class="sxs-lookup"><span data-stu-id="e97dc-130">1</span></span>|<span data-ttu-id="e97dc-131">可将数据写入文件。</span><span class="sxs-lookup"><span data-stu-id="e97dc-131">Data can be written to the file.</span></span>|  
|<span data-ttu-id="e97dc-132">SQL_FILESTREAM_READWRITE</span><span class="sxs-lookup"><span data-stu-id="e97dc-132">SQL_FILESTREAM_READWRITE</span></span>|<span data-ttu-id="e97dc-133">2</span><span class="sxs-lookup"><span data-stu-id="e97dc-133">2</span></span>|<span data-ttu-id="e97dc-134">可从文件读取数据并将数据写入文件。</span><span class="sxs-lookup"><span data-stu-id="e97dc-134">Data can be read and written from the file.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="e97dc-135">这些值在 sqlncli.h 的 SQL_FILESTREAM_DESIRED_ACCESS 枚举中定义。</span><span class="sxs-lookup"><span data-stu-id="e97dc-135">These values are defined in the SQL_FILESTREAM_DESIRED_ACCESS enumeration in sqlncli.h.</span></span>  
  
 <span data-ttu-id="e97dc-136">*OpenOptions*</span><span class="sxs-lookup"><span data-stu-id="e97dc-136">*OpenOptions*</span></span>  
 <span data-ttu-id="e97dc-137">[in] 文件属性和标志。</span><span class="sxs-lookup"><span data-stu-id="e97dc-137">[in] The file attributes and flags.</span></span> <span data-ttu-id="e97dc-138">此参数还可以包括下列标志的任意组合。</span><span class="sxs-lookup"><span data-stu-id="e97dc-138">This parameter can also include any combination of the following flags.</span></span>  
  
|<span data-ttu-id="e97dc-139">标志</span><span class="sxs-lookup"><span data-stu-id="e97dc-139">Flag</span></span>|<span data-ttu-id="e97dc-140">值</span><span class="sxs-lookup"><span data-stu-id="e97dc-140">Value</span></span>|<span data-ttu-id="e97dc-141">含义</span><span class="sxs-lookup"><span data-stu-id="e97dc-141">Meaning</span></span>|  
|----------|-----------|-------------|  
|<span data-ttu-id="e97dc-142">SQL_FILESTREAM_OPEN_NONE</span><span class="sxs-lookup"><span data-stu-id="e97dc-142">SQL_FILESTREAM_OPEN_NONE</span></span>|<span data-ttu-id="e97dc-143">0x00000000:</span><span class="sxs-lookup"><span data-stu-id="e97dc-143">0x00000000:</span></span>|<span data-ttu-id="e97dc-144">文件是未使用任何特殊选项打开或创建的。</span><span class="sxs-lookup"><span data-stu-id="e97dc-144">The file is being opened or created with no special options.</span></span>|  
|<span data-ttu-id="e97dc-145">SQL_FILESTREAM_OPEN_FLAG_ASYNC</span><span class="sxs-lookup"><span data-stu-id="e97dc-145">SQL_FILESTREAM_OPEN_FLAG_ASYNC</span></span>|<span data-ttu-id="e97dc-146">0x00000001L</span><span class="sxs-lookup"><span data-stu-id="e97dc-146">0x00000001L</span></span>|<span data-ttu-id="e97dc-147">文件是针对异步 I/O 打开或创建的。</span><span class="sxs-lookup"><span data-stu-id="e97dc-147">The file is being opened or created for asynchronous I/O.</span></span>|  
|<span data-ttu-id="e97dc-148">SQL_FILESTREAM_OPEN_FLAG_NO_BUFFERING</span><span class="sxs-lookup"><span data-stu-id="e97dc-148">SQL_FILESTREAM_OPEN_FLAG_NO_BUFFERING</span></span>|<span data-ttu-id="e97dc-149">0x00000002L</span><span class="sxs-lookup"><span data-stu-id="e97dc-149">0x00000002L</span></span>|<span data-ttu-id="e97dc-150">系统不使用系统缓存来打开文件。</span><span class="sxs-lookup"><span data-stu-id="e97dc-150">The system opens the file by using no system caching.</span></span>|  
|<span data-ttu-id="e97dc-151">SQL_FILESTREAM_OPEN_FLAG_NO_WRITE_THROUGH</span><span class="sxs-lookup"><span data-stu-id="e97dc-151">SQL_FILESTREAM_OPEN_FLAG_NO_WRITE_THROUGH</span></span>|<span data-ttu-id="e97dc-152">0x00000004L</span><span class="sxs-lookup"><span data-stu-id="e97dc-152">0x00000004L</span></span>|<span data-ttu-id="e97dc-153">系统不通过任何中间缓存来进行写入。</span><span class="sxs-lookup"><span data-stu-id="e97dc-153">The system does not write through an intermediate cache.</span></span> <span data-ttu-id="e97dc-154">直接将数据写入磁盘。</span><span class="sxs-lookup"><span data-stu-id="e97dc-154">Writes go directly to disk.</span></span>|  
|<span data-ttu-id="e97dc-155">SQL_FILESTREAM_OPEN_FLAG_SEQUENTIAL_SCAN</span><span class="sxs-lookup"><span data-stu-id="e97dc-155">SQL_FILESTREAM_OPEN_FLAG_SEQUENTIAL_SCAN</span></span>|<span data-ttu-id="e97dc-156">0x00000008L</span><span class="sxs-lookup"><span data-stu-id="e97dc-156">0x00000008L</span></span>|<span data-ttu-id="e97dc-157">从开头到末尾顺序访问文件。</span><span class="sxs-lookup"><span data-stu-id="e97dc-157">A file is accessed sequentially from beginning to end.</span></span> <span data-ttu-id="e97dc-158">系统可将此选项用作优化文件缓存的提示。</span><span class="sxs-lookup"><span data-stu-id="e97dc-158">The system can use this as a hint to optimize file caching.</span></span> <span data-ttu-id="e97dc-159">如果应用程序移动文件指针来进行随机访问，可能不会发生优化缓存。</span><span class="sxs-lookup"><span data-stu-id="e97dc-159">If an application moves the file pointer for random access, optimal caching may not occur.</span></span>|  
|<span data-ttu-id="e97dc-160">SQL_FILESTREAM_OPEN_FLAG_RANDOM_ACCESS</span><span class="sxs-lookup"><span data-stu-id="e97dc-160">SQL_FILESTREAM_OPEN_FLAG_RANDOM_ACCESS</span></span>|<span data-ttu-id="e97dc-161">0x00000010L</span><span class="sxs-lookup"><span data-stu-id="e97dc-161">0x00000010L</span></span>|<span data-ttu-id="e97dc-162">随机访问文件。</span><span class="sxs-lookup"><span data-stu-id="e97dc-162">A file is accessed randomly.</span></span> <span data-ttu-id="e97dc-163">系统可将此选项用作优化文件缓存的提示。</span><span class="sxs-lookup"><span data-stu-id="e97dc-163">The system can use this as a hint to optimize file caching.</span></span>|  
  
 <span data-ttu-id="e97dc-164">*FilestreamTransactionContext*</span><span class="sxs-lookup"><span data-stu-id="e97dc-164">*FilestreamTransactionContext*</span></span>  
 <span data-ttu-id="e97dc-165">[in] [GET_FILESTREAM_TRANSACTION_CONTEXT](/sql/t-sql/functions/get-filestream-transaction-context-transact-sql) 函数返回的值。</span><span class="sxs-lookup"><span data-stu-id="e97dc-165">[in] The value that is returned by the [GET_FILESTREAM_TRANSACTION_CONTEXT](/sql/t-sql/functions/get-filestream-transaction-context-transact-sql) function.</span></span>  
  
 <span data-ttu-id="e97dc-166">*FilestreamTransactionContextLength*</span><span class="sxs-lookup"><span data-stu-id="e97dc-166">*FilestreamTransactionContextLength*</span></span>  
 <span data-ttu-id="e97dc-167">[in] GET_FILESTREAM_TRANSACTION_CONTEXT 函数返回的 `varbinary(max)` 数据中的字节数。</span><span class="sxs-lookup"><span data-stu-id="e97dc-167">[in] Number of bytes in the `varbinary(max)` data that is returned by the GET_FILESTREAM_TRANSACTION_CONTEXT function.</span></span> <span data-ttu-id="e97dc-168">函数返回 N 个字节数组。</span><span class="sxs-lookup"><span data-stu-id="e97dc-168">The function returns an array of N bytes.</span></span> <span data-ttu-id="e97dc-169">N 由函数决定，是返回的字节数组的一个属性。</span><span class="sxs-lookup"><span data-stu-id="e97dc-169">N is determined by the function and is a property of the byte array that is returned.</span></span>  
  
 <span data-ttu-id="e97dc-170">*AllocationSize*</span><span class="sxs-lookup"><span data-stu-id="e97dc-170">*AllocationSize*</span></span>  
 <span data-ttu-id="e97dc-171">[in] 以字节为单位指定数据文件的初始分配大小。</span><span class="sxs-lookup"><span data-stu-id="e97dc-171">[in] Specifies the initial allocation size of the data file in bytes.</span></span> <span data-ttu-id="e97dc-172">在读取模式下将被忽略。</span><span class="sxs-lookup"><span data-stu-id="e97dc-172">It is ignored in read mode.</span></span> <span data-ttu-id="e97dc-173">此参数可以为 NULL，在这种情况下，将使用默认文件系统行为。</span><span class="sxs-lookup"><span data-stu-id="e97dc-173">This parameter can be NULL, in which case the default file system behavior is used.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e97dc-174">返回值</span><span class="sxs-lookup"><span data-stu-id="e97dc-174">Return Value</span></span>  
 <span data-ttu-id="e97dc-175">如果函数成功，则返回值为指定文件的打开句柄。</span><span class="sxs-lookup"><span data-stu-id="e97dc-175">If the function succeeds, the return value is an open handle to a specified file.</span></span> <span data-ttu-id="e97dc-176">如果函数失败，则返回值为 INVALID_HANDLE_VALUE。</span><span class="sxs-lookup"><span data-stu-id="e97dc-176">If the function fails, the return value is INVALID_HANDLE_VALUE.</span></span> <span data-ttu-id="e97dc-177">要获得更多的错误信息，请调用 GetLastError()。</span><span class="sxs-lookup"><span data-stu-id="e97dc-177">For extended error information, call GetLastError().</span></span>  
  
## <a name="examples"></a><span data-ttu-id="e97dc-178">示例</span><span class="sxs-lookup"><span data-stu-id="e97dc-178">Examples</span></span>  
 <span data-ttu-id="e97dc-179">下面的示例说明如何使用 `OpenSqlFilestream` API 获取 Win32 句柄。</span><span class="sxs-lookup"><span data-stu-id="e97dc-179">The following examples show you how to use the `OpenSqlFilestream` API to obtain a Win32 handle.</span></span>  
  
 [!code-csharp[FILESTREAM#FS_CS_ReadAndWriteBLOB](../../snippets/tsql/SQL15/tsql/filestream/cs/filestream.cs#fs_cs_readandwriteblob)]  
  
 [!code-vb[FILESTREAM#FS_VB_ReadAndWriteBLOB](../../snippets/tsql/SQL15/tsql/filestream/vb/filestream.vb#fs_vb_readandwriteblob)]  
  
 [!code-cpp[FILESTREAM#FS_CPP_WriteBLOB](../../snippets/tsql/SQL15/tsql/filestream/cpp/filestream.cpp#fs_cpp_writeblob)]  
  
## <a name="remarks"></a><span data-ttu-id="e97dc-180">备注</span><span class="sxs-lookup"><span data-stu-id="e97dc-180">Remarks</span></span>  
 <span data-ttu-id="e97dc-181">必须安装 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 才能使用此 API。</span><span class="sxs-lookup"><span data-stu-id="e97dc-181">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client must be installed to use this API.</span></span> <span data-ttu-id="e97dc-182">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 随同 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 客户端工具一起安装。</span><span class="sxs-lookup"><span data-stu-id="e97dc-182">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client is installed with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] client tools.</span></span> <span data-ttu-id="e97dc-183">有关详细信息，请参阅 [安装 SQL Server Native Client](../native-client/applications/installing-sql-server-native-client.md)。</span><span class="sxs-lookup"><span data-stu-id="e97dc-183">For more information, see [Installing SQL Server Native Client](../native-client/applications/installing-sql-server-native-client.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e97dc-184">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e97dc-184">See Also</span></span>  
 <span data-ttu-id="e97dc-185">[二进制大型对象 &#40;Blob&#41; 数据 &#40;SQL Server&#41;](binary-large-object-blob-data-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="e97dc-185">[Binary Large Object &#40;Blob&#41; Data &#40;SQL Server&#41;](binary-large-object-blob-data-sql-server.md) </span></span>  
 <span data-ttu-id="e97dc-186">[对 FILESTREAM 数据进行部分更新](make-partial-updates-to-filestream-data.md) </span><span class="sxs-lookup"><span data-stu-id="e97dc-186">[Make Partial Updates to FILESTREAM Data](make-partial-updates-to-filestream-data.md) </span></span>  
 [<span data-ttu-id="e97dc-187">避免与 FILESTREAM 应用程序中的数据库操作冲突</span><span class="sxs-lookup"><span data-stu-id="e97dc-187">Avoid Conflicts with Database Operations in FILESTREAM Applications</span></span>](avoid-conflicts-with-database-operations-in-filestream-applications.md)  
  
  
