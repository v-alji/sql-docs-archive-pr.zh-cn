---
title: 表和存储过程的本机编译 | Microsoft Docs
ms.custom: ''
ms.date: 07/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 5880fbd9-a23e-464a-8b44-09750eeb2dad
author: rothja
ms.author: jroth
ms.openlocfilehash: 32c5b04610d894e06278fbeecdaf3bbebe850d60
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587818"
---
# <a name="native-compilation-of-tables-and-stored-procedures"></a><span data-ttu-id="c0130-102">表和存储过程的本机编译</span><span class="sxs-lookup"><span data-stu-id="c0130-102">Native Compilation of Tables and Stored Procedures</span></span>
  <span data-ttu-id="c0130-103">内存中 OLTP 引入了本机编译的概念。</span><span class="sxs-lookup"><span data-stu-id="c0130-103">In-Memory OLTP introduces the concept of native compilation.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="c0130-104">可以本机编译访问内存优化表的存储过程。</span><span class="sxs-lookup"><span data-stu-id="c0130-104">can natively compile stored procedures that access memory-optimized tables.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="c0130-105">也可以本机编译内存优化表。</span><span class="sxs-lookup"><span data-stu-id="c0130-105">is also able to natively compile memory-optimized tables.</span></span> <span data-ttu-id="c0130-106">与解释型（传统） [!INCLUDE[tsql](../../includes/tsql-md.md)]相比，本机编译可提高访问数据的速度和执行查询的效率。</span><span class="sxs-lookup"><span data-stu-id="c0130-106">Native compilation allows faster data access and more efficient query execution than interpreted (traditional) [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="c0130-107">表和存储过程的本机编译生成 DLL。</span><span class="sxs-lookup"><span data-stu-id="c0130-107">Native compilation of tables and stored procedures produce DLLs.</span></span>  
  
 <span data-ttu-id="c0130-108">还支持内存优化表类型的本机编译。</span><span class="sxs-lookup"><span data-stu-id="c0130-108">Native compilation of memory optimized table types is also supported.</span></span> <span data-ttu-id="c0130-109">有关详细信息，请参阅 [Memory-Optimized Table Variables](../../database-engine/memory-optimized-table-variables.md)。</span><span class="sxs-lookup"><span data-stu-id="c0130-109">For more information, see [Memory-Optimized Table Variables](../../database-engine/memory-optimized-table-variables.md).</span></span>  
  
 <span data-ttu-id="c0130-110">本机编译是指将编程构造转换为本机代码的过程，这些代码由处理器指令组成，无需进一步编译或解释。</span><span class="sxs-lookup"><span data-stu-id="c0130-110">Native compilation refers to the process of converting programming constructs to native code, consisting of processor instructions without the need for further compilation or interpretation.</span></span>  
  
 <span data-ttu-id="c0130-111">内存中 OLTP 在创建内存优化表时编译内存优化表，并且在存储过程加载到本机 DLL 时本机编译存储过程。</span><span class="sxs-lookup"><span data-stu-id="c0130-111">In-Memory OLTP compiles memory-optimized tables when they are created, and natively compiled stored procedures when they are loaded to native DLLs.</span></span> <span data-ttu-id="c0130-112">此外，在数据库或服务器重新启动后，将重新编译这些 DLL。</span><span class="sxs-lookup"><span data-stu-id="c0130-112">In addition, the DLLs are recompiled after a database or server restart.</span></span> <span data-ttu-id="c0130-113">重新创建 DLL 所需的信息存储在数据库元数据中。</span><span class="sxs-lookup"><span data-stu-id="c0130-113">The information necessary to recreate the DLLs is stored in the database metadata.</span></span> <span data-ttu-id="c0130-114">这些 DLL 不是数据库的一部分，尽管它们与数据库相关联。</span><span class="sxs-lookup"><span data-stu-id="c0130-114">The DLLs are not part of the database, though they are associated with the database.</span></span> <span data-ttu-id="c0130-115">例如，这些 DLL 不包括在数据库备份中。</span><span class="sxs-lookup"><span data-stu-id="c0130-115">For example, the DLLs are not included in database backups.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c0130-116">在服务器重启过程中，将重新编译内存优化表。</span><span class="sxs-lookup"><span data-stu-id="c0130-116">Memory-optimized tables are recompiled during a server restart.</span></span> <span data-ttu-id="c0130-117">为了加快数据库恢复速度，本机编译的存储过程不会在服务器重启过程中重新编译，而是在首次执行时编译。</span><span class="sxs-lookup"><span data-stu-id="c0130-117">To speed up database recovery, natively compiled stored procedures are not recompiled during a server restart, they are compiled at the time of first execution.</span></span> <span data-ttu-id="c0130-118">由于这一延迟的编译，本机编译的存储过程仅在首次执行后调用 [sys.dm_os_loaded_modules (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-loaded-modules-transact-sql) 时显示。</span><span class="sxs-lookup"><span data-stu-id="c0130-118">As a result of this deferred compilation, natively compiled stored procedures only appear when calling [sys.dm_os_loaded_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-loaded-modules-transact-sql) after first execution.</span></span>  
  
## <a name="maintenance-of-in-memory-oltp-dlls"></a><span data-ttu-id="c0130-119">内存中 OLTP DLL 的维护</span><span class="sxs-lookup"><span data-stu-id="c0130-119">Maintenance of In-Memory OLTP DLLs</span></span>  
 <span data-ttu-id="c0130-120">以下查询显示当前在服务器上的内存中加载的所有表和存储过程 DLL：</span><span class="sxs-lookup"><span data-stu-id="c0130-120">The following query shows all table and stored procedure DLLs currently loaded in memory on the server:</span></span>  
  
```sql  
SELECT name, description FROM sys.dm_os_loaded_modules  
where description = 'XTP Native DLL'  
```  
  
 <span data-ttu-id="c0130-121">数据库管理员不需要维护由本机编译生成的文件。</span><span class="sxs-lookup"><span data-stu-id="c0130-121">Database administrators do not need to maintain files that are generated by a native compilation.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="c0130-122">将自动删除那些不再需要的生成的文件。</span><span class="sxs-lookup"><span data-stu-id="c0130-122">automatically removes generated files that are no longer needed.</span></span> <span data-ttu-id="c0130-123">例如，删除表和存储过程时或删除数据库时将删除生成的文件。</span><span class="sxs-lookup"><span data-stu-id="c0130-123">For example, generated files will be deleted when a table and stored procedure is deleted, or if a database is dropped.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c0130-124">如果编译失败或中断，则某些生成的文件将不会被删除。</span><span class="sxs-lookup"><span data-stu-id="c0130-124">If compilation fails or is interrupted, some generated files are not removed.</span></span> <span data-ttu-id="c0130-125">出于支持性目的这些文件被有意保留，并且在删除数据库时会被删除。</span><span class="sxs-lookup"><span data-stu-id="c0130-125">These files are intentionally left behind for supportability and are removed when the database is dropped.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c0130-126">在数据库启动过程中，SQL Server 会为进行数据库恢复所需的所有表编译 DLL。</span><span class="sxs-lookup"><span data-stu-id="c0130-126">During database startup, SQL Server compiles DLLs for all tables needed for database recovery.</span></span> <span data-ttu-id="c0130-127">如果某个表就在数据库重新启动之前删除，则检查点文件或事务日志中可能仍有该表的残余，因此可能会在数据库启动过程中重新编译该表的 DLL。</span><span class="sxs-lookup"><span data-stu-id="c0130-127">If a table was dropped just prior to a database restart there can still be remnants of the table in the checkpoint files or the transaction log so the DLL for the table might be recompiled during database startup.</span></span> <span data-ttu-id="c0130-128">重新启动之后，会卸载 DLL，并由正常清除过程删除文件。</span><span class="sxs-lookup"><span data-stu-id="c0130-128">After restart the DLL will be unloaded and the files will be removed by the normal cleanup process.</span></span>  
  
## <a name="native-compilation-of-tables"></a><span data-ttu-id="c0130-129">表的本机编译</span><span class="sxs-lookup"><span data-stu-id="c0130-129">Native Compilation of Tables</span></span>  
 <span data-ttu-id="c0130-130">如果使用 `CREATE TABLE` 语句创建内存优化表，会导致将表信息写入数据库元数据，并在内存中创建表和索引结构。</span><span class="sxs-lookup"><span data-stu-id="c0130-130">Creating a memory-optimized table using the `CREATE TABLE` statement results in the table information being written to the database metadata and the table and index structures created in memory.</span></span> <span data-ttu-id="c0130-131">还会将该表编译为 DLL。</span><span class="sxs-lookup"><span data-stu-id="c0130-131">The table will also be compiled to a DLL.</span></span>  
  
 <span data-ttu-id="c0130-132">请考虑下面的示例脚本，它创建一个数据库和一个内存优化的表：</span><span class="sxs-lookup"><span data-stu-id="c0130-132">Consider the following sample script, which creates a database and a memory-optimized table:</span></span>  
  
```sql  
use master  
go  
create database db1  
go  
alter database db1 add filegroup db1_mod contains memory_optimized_data  
go  
-- adapt filename as needed  
alter database db1 add file (name='db1_mod', filename='c:\data\db1_mod') to filegroup db1_mod  
go  
use db1  
go  
create table dbo.t1  
   (c1 int not null primary key nonclustered,  
    c2 INT)  
with (memory_optimized=on)  
go  
-- retrieve the path of the DLL for table t1  
select name, description FROM sys.dm_os_loaded_modules  
where name like '%xtp_t_' + cast(db_id() as varchar(10)) + '_' + cast(object_id('dbo.t1') as varchar(10)) + '.dll'  
go  
```  
  
 <span data-ttu-id="c0130-133">创建该表时还会创建表 DLL 并在内存中加载 DLL。</span><span class="sxs-lookup"><span data-stu-id="c0130-133">Creating the table also creates the table DLL and loads the DLL in memory.</span></span> <span data-ttu-id="c0130-134">CREATE TABLE 语句之后立即执行 DMV 查询将检索表 DLL 的路径。</span><span class="sxs-lookup"><span data-stu-id="c0130-134">The DMV query immediately after the CREATE TABLE statement retrieves the path of the table DLL.</span></span>  
  
 <span data-ttu-id="c0130-135">表 DLL 了解表的索引结构和行格式。</span><span class="sxs-lookup"><span data-stu-id="c0130-135">The table DLL understands the index structures and row format of the table.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="c0130-136">使用该 DLL 来遍历索引、检索行以及存储行的内容。</span><span class="sxs-lookup"><span data-stu-id="c0130-136">uses the DLL for traversing indexes, retrieving rows, as well as storing the contents of the rows.</span></span>  
  
## <a name="native-compilation-of-stored-procedures"></a><span data-ttu-id="c0130-137">存储过程的本机编译</span><span class="sxs-lookup"><span data-stu-id="c0130-137">Native Compilation of Stored Procedures</span></span>  
 <span data-ttu-id="c0130-138">对使用 NATIVE_COMPILATION 来标记的存储过程执行本机编译。</span><span class="sxs-lookup"><span data-stu-id="c0130-138">Stored procedures that are marked with NATIVE_COMPILATION are natively compiled.</span></span> <span data-ttu-id="c0130-139">这意味着该过程中的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句均被编译为本机代码，以便高效执行性能关键的业务逻辑。</span><span class="sxs-lookup"><span data-stu-id="c0130-139">This means the [!INCLUDE[tsql](../../includes/tsql-md.md)] statements in the procedure are all compiled to native code for efficient execution of performance-critical business logic.</span></span>  
  
 <span data-ttu-id="c0130-140">有关本机编译的存储过程的详细信息，请参阅 [Natively Compiled Stored Procedures](natively-compiled-stored-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="c0130-140">For more information about natively compiled stored procedures, see [Natively Compiled Stored Procedures](natively-compiled-stored-procedures.md).</span></span>  
  
 <span data-ttu-id="c0130-141">考虑下面的示例存储过程，它在前一示例的表 t1 中插入行：</span><span class="sxs-lookup"><span data-stu-id="c0130-141">Consider the following sample stored procedure, which inserts rows in the table t1 from the previous example:</span></span>  
  
```sql  
create procedure dbo.native_sp  
with native_compilation, schemabinding, execute as owner  
as  
begin atomic  
with (transaction isolation level=snapshot, language=N'us_english')  
  
  declare @i int = 1000000  
  while @i > 0  
  begin  
    insert dbo.t1 values (@i, @i+1)  
    set @i -= 1  
  end  
  
end  
go  
exec dbo.native_sp  
go  
-- reset  
delete from dbo.t1  
go  
```  
  
 <span data-ttu-id="c0130-142">native_sp 的 DLL 可直接与 t1 的 DLL 以及内存中 OLTP 存储引擎交互，以尽快插入行。</span><span class="sxs-lookup"><span data-stu-id="c0130-142">The DLL for native_sp can interact directly with the DLL for t1, as well as the In-Memory OLTP storage engine, to insert the rows as fast as possible.</span></span>  
  
 <span data-ttu-id="c0130-143">内存中 OLTP 编译器利用查询优化器为存储过程中的每个查询创建高效的执行计划。</span><span class="sxs-lookup"><span data-stu-id="c0130-143">The In-Memory OLTP compiler leverages the query optimizer to create an efficient execution plan for each of the queries in the stored procedure.</span></span> <span data-ttu-id="c0130-144">请注意，如果表中的数据更改了，本机编译的存储过程不会自动重新编译。</span><span class="sxs-lookup"><span data-stu-id="c0130-144">Note that natively compiled stored procedures are not automatically recompiled if the data in the table changes.</span></span> <span data-ttu-id="c0130-145">有关使用内存中 OLTP 维护统计信息和存储过程的详细信息，请参阅 [内存优化表的统计信息](memory-optimized-tables.md)。</span><span class="sxs-lookup"><span data-stu-id="c0130-145">For more information on maintaining statistics and stored procedures with In-Memory OLTP see [Statistics for Memory-Optimized Tables](memory-optimized-tables.md).</span></span>  
  
## <a name="security-considerations-for-native-compilation"></a><span data-ttu-id="c0130-146">有关本机编译的安全注意事项</span><span class="sxs-lookup"><span data-stu-id="c0130-146">Security Considerations for Native Compilation</span></span>  
 <span data-ttu-id="c0130-147">表和存储过程的本机编译使用内存中 OLTP 编译器。</span><span class="sxs-lookup"><span data-stu-id="c0130-147">Native compilation of tables and stored procedures uses the In-Memory OLTP compiler.</span></span> <span data-ttu-id="c0130-148">此编译器生成的文件将写入磁盘和载入内存。</span><span class="sxs-lookup"><span data-stu-id="c0130-148">This compiler produces files that are written to disk and loaded into memory.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="c0130-149">使用以下机制限制访问这些文件。</span><span class="sxs-lookup"><span data-stu-id="c0130-149">uses the following mechanisms to limit access to these files.</span></span>  
  
### <a name="native-compiler"></a><span data-ttu-id="c0130-150">本机编译器</span><span class="sxs-lookup"><span data-stu-id="c0130-150">Native Compiler</span></span>  
 <span data-ttu-id="c0130-151">编译器可执行文件以及本机编译所需的二进制文件和头文件安装在文件夹 MSSQL\Binn\Xtp 下，作为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例的一部分。</span><span class="sxs-lookup"><span data-stu-id="c0130-151">The compiler executable, as well as binaries and header files required for native compilation are installed as part of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance under the folder MSSQL\Binn\Xtp.</span></span> <span data-ttu-id="c0130-152">因此，如果默认实例安装在 C:\Program files 下，则编译器文件安装在 C:\Program files \MSSQL12. 中 \\ [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。MSSQLSERVER\MSSQL\Binn\Xtp.</span><span class="sxs-lookup"><span data-stu-id="c0130-152">So, if the default instance is installed under C:\Program Files, the compiler files are installed in C:\Program Files\\[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSSQL12.MSSQLSERVER\MSSQL\Binn\Xtp.</span></span>  
  
 <span data-ttu-id="c0130-153">为了限制访问编译器， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用访问控制列表 (ACL) 限制访问二进制文件。</span><span class="sxs-lookup"><span data-stu-id="c0130-153">To limit access to the compiler, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] uses access control lists (ACLs) to restrict access to binary files.</span></span> <span data-ttu-id="c0130-154">通过 ACL 保护所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 二进制文件免遭修改或篡改。</span><span class="sxs-lookup"><span data-stu-id="c0130-154">All [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] binaries are protected against modification or tampering through ACLs.</span></span> <span data-ttu-id="c0130-155">本机编译器的 ACL 还限制使用编译器；仅 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务帐户和系统管理员对本机编译器文件具有读取和执行权限。</span><span class="sxs-lookup"><span data-stu-id="c0130-155">The native compiler's ACLs also limit use of the compiler; only the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service account and system administrators have read and execute permissions for native compiler files.</span></span>  
  
### <a name="files-generated-by-a-native-compilation"></a><span data-ttu-id="c0130-156">本机编译生成的文件</span><span class="sxs-lookup"><span data-stu-id="c0130-156">Files Generated by a Native Compilation</span></span>  
 <span data-ttu-id="c0130-157">编译表或存储过程时生成的文件包括 DLL 和中间文件，其中包括如下扩展名的文件：.c、.obj、.xml 和 .pdb。</span><span class="sxs-lookup"><span data-stu-id="c0130-157">The files produced when a table or stored procedure is compiled include the DLL and intermediate files including files with the following extensions: .c, .obj, .xml, and .pdb.</span></span> <span data-ttu-id="c0130-158">生成的文件保存在默认数据文件夹的一个子文件夹中。</span><span class="sxs-lookup"><span data-stu-id="c0130-158">The generated files are saved in a subfolder of the default data folder.</span></span> <span data-ttu-id="c0130-159">该子文件夹称为 Xtp。</span><span class="sxs-lookup"><span data-stu-id="c0130-159">The subfolder is called Xtp.</span></span> <span data-ttu-id="c0130-160">在用默认数据文件夹安装默认实例时，生成的文件放置在 C:\Program files \MSSQL12. 中 \\ [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。MSSQLSERVER\MSSQL\DATA\Xtp.</span><span class="sxs-lookup"><span data-stu-id="c0130-160">When installing the default instance with the default data folder, the generated files are placed in C:\Program Files\\[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSSQL12.MSSQLSERVER\MSSQL\DATA\Xtp.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="c0130-161">通过以下三种方式防止纂改所生成的 DLL：</span><span class="sxs-lookup"><span data-stu-id="c0130-161">prevents tampering with the generated DLLs in three ways:</span></span>  
  
-   <span data-ttu-id="c0130-162">将表或存储过程编译为 DLL 后，此 DLL 将立即载入内存并链接到 sqlserver.exe 进程。</span><span class="sxs-lookup"><span data-stu-id="c0130-162">When a table or stored procedure is compiled to a DLL, this DLL is immediately loaded into memory and linked to the sqlserver.exe process.</span></span> <span data-ttu-id="c0130-163">DLL 链接到进程后，即无法修改该 DLL。</span><span class="sxs-lookup"><span data-stu-id="c0130-163">A DLL cannot be modified while it is linked to a process.</span></span>  
  
-   <span data-ttu-id="c0130-164">重新启动数据库后，将根据数据库元数据重新编译所有表和存储过程（删除再重新创建）。</span><span class="sxs-lookup"><span data-stu-id="c0130-164">When a database is restarted, all tables and stored procedures are recompiled (removed and recreated) based on the database metadata.</span></span> <span data-ttu-id="c0130-165">这样将消除恶意代理对所生成的文件作出的任何更改。</span><span class="sxs-lookup"><span data-stu-id="c0130-165">This will remove any changes made to a generated file by a malicious agent.</span></span>  
  
-   <span data-ttu-id="c0130-166">所生成的文件被视为用户数据的一部分，并且其安全限制（通过 ACL）与数据库文件相同：仅 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务帐户和系统管理员可访问这些文件。</span><span class="sxs-lookup"><span data-stu-id="c0130-166">The generated files are considered part of user data, and have the same security restrictions, via ACLs, as database files: only the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service account and system administrators can access these files.</span></span>  
  
 <span data-ttu-id="c0130-167">无需用户干预即可管理这些文件。</span><span class="sxs-lookup"><span data-stu-id="c0130-167">No user interaction is needed to manage these files.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="c0130-168">将根据需要创建和删除文件。</span><span class="sxs-lookup"><span data-stu-id="c0130-168">will create and remove the files as necessary.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0130-169">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c0130-169">See Also</span></span>  
 <span data-ttu-id="c0130-170">[内存优化表](memory-optimized-tables.md) </span><span class="sxs-lookup"><span data-stu-id="c0130-170">[Memory-Optimized Tables](memory-optimized-tables.md) </span></span>  
 [<span data-ttu-id="c0130-171">本机编译的存储过程</span><span class="sxs-lookup"><span data-stu-id="c0130-171">Natively Compiled Stored Procedures</span></span>](natively-compiled-stored-procedures.md)  
  
  
