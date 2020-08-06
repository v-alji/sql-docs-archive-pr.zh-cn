---
title: 更改内存优化表 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 690b70b7-5be1-4014-af97-54e531997839
author: rothja
ms.author: jroth
ms.openlocfilehash: 4eedc6fdb45efc6c87765cd2208ead90c1887c27
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590205"
---
# <a name="altering-memory-optimized-tables"></a><span data-ttu-id="e297e-102">更改内存优化表</span><span class="sxs-lookup"><span data-stu-id="e297e-102">Altering Memory-Optimized Tables</span></span>
  <span data-ttu-id="e297e-103">不支持对内存优化表执行 ALTER 操作。</span><span class="sxs-lookup"><span data-stu-id="e297e-103">Performing ALTER operations on memory-optimized tables is not supported.</span></span> <span data-ttu-id="e297e-104">其中包括更改 bucket_count、添加或删除索引、添加或删除列等操作。</span><span class="sxs-lookup"><span data-stu-id="e297e-104">This includes such operations as changing the bucket_count, adding or removing an index, and adding or removing a column.</span></span> <span data-ttu-id="e297e-105">本主题指导如何更新内存优化表。</span><span class="sxs-lookup"><span data-stu-id="e297e-105">This topic provides guidelines on how to update memory-optimized tables.</span></span>  
  
## <a name="updating-the-definition-of-a-memory-optimized-table"></a><span data-ttu-id="e297e-106">更新内存优化表的定义</span><span class="sxs-lookup"><span data-stu-id="e297e-106">Updating the Definition of a Memory-Optimized Table</span></span>  
 <span data-ttu-id="e297e-107">更新内存优化表的定义要求您使用更新的表定义创建一个新表，将数据复制到新表，然后使用新表启动。</span><span class="sxs-lookup"><span data-stu-id="e297e-107">Updating the definition of a memory-optimized table requires you to create a new table with the updated table definition, copy the data to the new table, and start using the new table.</span></span> <span data-ttu-id="e297e-108">除非该表是只读的，否则这要求停止表上的工作负荷以确保在执行数据复制时不对表进行更改。</span><span class="sxs-lookup"><span data-stu-id="e297e-108">Unless the table is read-only, this requires stopping the workload on the table, to ensure no changes are made to the table while the data copy is performed.</span></span>  
  
 <span data-ttu-id="e297e-109">以下过程概述了更新表所需的步骤。</span><span class="sxs-lookup"><span data-stu-id="e297e-109">The following procedure outlines the steps required to update a table.</span></span> <span data-ttu-id="e297e-110">在此示例中，更新时添加了一个索引。</span><span class="sxs-lookup"><span data-stu-id="e297e-110">In this example, the update adds an index.</span></span> <span data-ttu-id="e297e-111">此过程保留了表的名称，需要两次数据复制操作：一次是复制临时表，另一次是复制新表。</span><span class="sxs-lookup"><span data-stu-id="e297e-111">This procedure preserves the name of the table and requires two data copy operations: once to a temporary table, and once to the new table.</span></span> <span data-ttu-id="e297e-112">以同样的方式更改索引的 bucket_count 或添加/删除列。</span><span class="sxs-lookup"><span data-stu-id="e297e-112">Changing the bucket_count of an index or adding or removing a column is performed the same way.</span></span>  
  
1.  <span data-ttu-id="e297e-113">停止表上的工作负荷。</span><span class="sxs-lookup"><span data-stu-id="e297e-113">Stop the workload on the table.</span></span>  
  
2.  <span data-ttu-id="e297e-114">生成表的脚本并将新索引添加到脚本。</span><span class="sxs-lookup"><span data-stu-id="e297e-114">Generate script for the table and add the new index to the script.</span></span>  
  
3.  <span data-ttu-id="e297e-115">为引用 T 的架构绑定对象（主要为本机编译的存储过程）及其权限生成脚本。</span><span class="sxs-lookup"><span data-stu-id="e297e-115">Generate script for the schema-bound objects (mainly natively compiled stored procedures) referencing T and their permissions.</span></span>  
  
     <span data-ttu-id="e297e-116">可使用以下查询查找引用表的架构绑定对象：</span><span class="sxs-lookup"><span data-stu-id="e297e-116">The schema-bound objects referencing the table can be found using the following query:</span></span>  
  
    ```sql  
    declare @t nvarchar(255) = N'<table name>'  
  
    select r.referencing_schema_name, r.referencing_entity_name  
    from sys.dm_sql_referencing_entities (@t, 'OBJECT') as r join sys.sql_modules m on r.referencing_id=m.object_id  
    where r.is_caller_dependent = 0 and m.is_schema_bound=1;  
    ```  
  
     <span data-ttu-id="e297e-117">使用以下 [!INCLUDE[tsql](../../includes/tsql-md.md)] 可对存储过程的权限编写脚本：</span><span class="sxs-lookup"><span data-stu-id="e297e-117">The permissions of a stored procedure can be scripted using the following [!INCLUDE[tsql](../../includes/tsql-md.md)]:</span></span>  
  
    ```sql  
    declare @sp nvarchar(255) = N'<procedure name>'  
    declare @permissions nvarchar(max) = N''  
  
    select @permissions += dp.state_desc + N' ' + dp.permission_name + N' ON ' +   
       quotename(schema_name(o.schema_id)) + N'.' + quotename(o.name) + N' TO ' +  
       quotename(u.name) + N'; ' + char(13)  
    from sys.database_permissions as dp  
  
    join sys.database_principals as u  
       on u.principal_id = dp.grantee_principal_id  
  
    join sys.objects as o  
       on o.object_id = dp.major_id  
    where dp.class = 1 /* object */  
       and dp.minor_id = 0 and o.object_id=object_id(@sp);  
  
    select @permissions  
    ```  
  
4.  <span data-ttu-id="e297e-118">创建表的副本并将数据从原始表复制到表的副本。</span><span class="sxs-lookup"><span data-stu-id="e297e-118">Create a copy of the table and copy the data from the original table to the copy of the table.</span></span> <span data-ttu-id="e297e-119">可以使用以下 [!INCLUDE[tsql](../../includes/tsql-md.md)] <sup>1</sup>创建副本。</span><span class="sxs-lookup"><span data-stu-id="e297e-119">The copy can be created using the following [!INCLUDE[tsql](../../includes/tsql-md.md)]<sup>1</sup>.</span></span>  
  
    ```sql  
    select * into dbo.T_copy from dbo.T  
    ```  
  
     <span data-ttu-id="e297e-120">如果有足够的可用内存，则 `T_copy` 可以是内存优化表，这会使数据复制更快。<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="e297e-120">If there is enough available memory, `T_copy` could be a memory-optimized table, which makes the data copy faster.<sup>2</sup></span></span>  
  
5.  <span data-ttu-id="e297e-121">删除引用原始表的架构绑定对象。</span><span class="sxs-lookup"><span data-stu-id="e297e-121">Drop the schema-bound objects referencing the original table.</span></span>  
  
6.  <span data-ttu-id="e297e-122">删除原始表。</span><span class="sxs-lookup"><span data-stu-id="e297e-122">Drop the original table.</span></span>  
  
7.  <span data-ttu-id="e297e-123">使用包含新索引的脚本创建新表 (`T`)。</span><span class="sxs-lookup"><span data-stu-id="e297e-123">Create the new table (`T`) with the script containing the new index.</span></span>  
  
8.  <span data-ttu-id="e297e-124">将数据从 `T_copy` 复制到 `T`。</span><span class="sxs-lookup"><span data-stu-id="e297e-124">Copy the data from `T_copy` to `T`.</span></span>  
  
9. <span data-ttu-id="e297e-125">重新创建引用的架构绑定对象并应用权限。</span><span class="sxs-lookup"><span data-stu-id="e297e-125">Recreate the referencing schema-bound objects and apply the permissions.</span></span>  
  
10. <span data-ttu-id="e297e-126">启动 `T` 上的工作负荷。</span><span class="sxs-lookup"><span data-stu-id="e297e-126">Start the workload on `T`.</span></span>  
  
 <span data-ttu-id="e297e-127"><sup>1</sup>请注意， `T_copy` 在此示例中，保存到磁盘。</span><span class="sxs-lookup"><span data-stu-id="e297e-127"><sup>1</sup> Note that `T_copy` is persisted to disk in this example.</span></span> <span data-ttu-id="e297e-128">如果 `T` 的备份可用，`T_copy` 可以为临时表或非持久表。</span><span class="sxs-lookup"><span data-stu-id="e297e-128">If a backup of `T` is available, `T_copy` could be a temporary or a non-durable table.</span></span>  
  
 <span data-ttu-id="e297e-129"><sup>2</sup>对于，必须有足够的内存 `T_copy` 。</span><span class="sxs-lookup"><span data-stu-id="e297e-129"><sup>2</sup> There must be enough memory for `T_copy`.</span></span> <span data-ttu-id="e297e-130">执行 `DROP TABLE` 后，不立即释放内存。</span><span class="sxs-lookup"><span data-stu-id="e297e-130">Memory is not freed immediately on `DROP TABLE`.</span></span> <span data-ttu-id="e297e-131">如果 `T_copy` 进行内存优化，需要有足够的内存用于新增的两个 `T` 副本。</span><span class="sxs-lookup"><span data-stu-id="e297e-131">If `T_copy` is memory optimized, there needs to be enough memory for two additional copies of `T`.</span></span> <span data-ttu-id="e297e-132">如果 `T_copy` 是基于磁盘的表，仅需要有足够的内存用于新增的一个 `T` 副本，因为在删除旧版本的 `T` 后垃圾收集器需要同步。</span><span class="sxs-lookup"><span data-stu-id="e297e-132">If `T_copy` is a disk-based table, there only needs to be enough memory for one additional copy of `T`, due to the garbage collector needing to catch up after dropping the old version of `T`.</span></span>  
  
## <a name="changing-schema-powershell"></a><span data-ttu-id="e297e-133">更改架构 (PowerShell)</span><span class="sxs-lookup"><span data-stu-id="e297e-133">Changing Schema (PowerShell)</span></span>  
 <span data-ttu-id="e297e-134">以下 PowerShell 脚本通过对表和相关权限编写脚本来为架构更改做准备和生成。</span><span class="sxs-lookup"><span data-stu-id="e297e-134">The following PowerShell scripts prepare and generate for schema changes by scripting the table and associated permissions.</span></span>  
  
```powershell
prepare_schema_change.ps1 <serverName> <databaseName> <schemaName> <tableName>
```
  
 <span data-ttu-id="e297e-135">此脚本提取作为变量的表，并对对象及其权限编写脚本，然后引用当前文件夹中架构绑定的对象及其权限。</span><span class="sxs-lookup"><span data-stu-id="e297e-135">This script takes as arguments a table, and scripts the object and its permissions and referencing schema-bound objects and their permissions in the current folder.</span></span> <span data-ttu-id="e297e-136">为更新输入表的架构总共生成了 7 个脚本：</span><span class="sxs-lookup"><span data-stu-id="e297e-136">A total of 7 scripts are generated for updating the schema of the input table:</span></span>  
  
-   <span data-ttu-id="e297e-137">将数据复制到临时表（堆）。</span><span class="sxs-lookup"><span data-stu-id="e297e-137">Copy data to a temporary table (a heap).</span></span>  
  
-   <span data-ttu-id="e297e-138">删除引用表的架构绑定对象。</span><span class="sxs-lookup"><span data-stu-id="e297e-138">Drop schema-bound objects referencing the table.</span></span>  
  
-   <span data-ttu-id="e297e-139">删除表。</span><span class="sxs-lookup"><span data-stu-id="e297e-139">Drop the table.</span></span>  
  
-   <span data-ttu-id="e297e-140">使用新架构重新创建表并重新应用权限。</span><span class="sxs-lookup"><span data-stu-id="e297e-140">Recreate the table with the new schema and reapply permissions.</span></span>  
  
-   <span data-ttu-id="e297e-141">将数据从临时表复制到重新创建的表。</span><span class="sxs-lookup"><span data-stu-id="e297e-141">Copy data from the temporary table to the recreated table.</span></span>  
  
-   <span data-ttu-id="e297e-142">重新创建引用表的架构绑定对象及其权限。</span><span class="sxs-lookup"><span data-stu-id="e297e-142">Recreate schema-bound objects referencing the table and their permissions.</span></span>  
  
-   <span data-ttu-id="e297e-143">删除临时表。</span><span class="sxs-lookup"><span data-stu-id="e297e-143">Drop the temporary table.</span></span>  
  
 <span data-ttu-id="e297e-144">应更新步骤 4 的脚本以反映所需的架构更改。</span><span class="sxs-lookup"><span data-stu-id="e297e-144">The script for step 4 should be updated to reflect the desired schema changes.</span></span> <span data-ttu-id="e297e-145">如果表中的列发生更改，应根据需要更新第 5 步（从临时表复制数据）的脚本和第 6 步（重新创建存储过程）的脚本。</span><span class="sxs-lookup"><span data-stu-id="e297e-145">If there are any changes in the columns of the table, the scripts for steps 5 (copy data from temporary table) and 6 (recreate stored procedures) should be updated as necessary.</span></span>  
  
```powershell
# Prepare for schema changes by scripting out the table, as well as associated permissions
# Usage: prepare_schema_change.ps1 server_name db_name schema_name table_name  
# stop execution once an error occurs  
$ErrorActionPreference="Stop"  
  
if($args.Count -le 3)  
{  
   throw "Usage prepare_schema_change.ps1 server_name db_name schema_name table_name"  
}  
  
$servername = $args[0]  
$database = $args[1]  
$schema = $args[2]  
$object = $args[3]  
  
$object_heap = "$object$(Get-Random)"  
  
[System.Reflection.Assembly]::LoadWithPartialName("Microsoft.SqlServer.SMO") | Out-Null  
  
$server =  New-Object ("Microsoft.SqlServer.Management.SMO.Server") ($servername)  
$scripter = New-Object ("Microsoft.SqlServer.Management.SMO.Scripter") ($server)  
  
## initialize table variable  
$tableUrn = $server.Databases[$database].Tables[$object, $schema]  
if($tableUrn.Count -eq 0)  
{  
   throw "Table or database not found"  
}  
  
## initialize scripting object  
$scriptingOptions = New-Object ("Microsoft.SqlServer.Management.SMO.ScriptingOptions")
$scriptingOptions.Permissions = $True  
$scriptingOptions.ScriptDrops = $True  
  
$scripter.Options = $scriptingOptions;  
  
Write-Host "(1) Scripting SELECT INTO $object_heap for table [$object] to 1_copy_to_heap_for_$schema`_$object.sql"  
Echo "SELECT * INTO $schema.$object_heap FROM $schema.$object WITH (SNAPSHOT)" | Out-File "1_copy_to_heap_$schema`_$object.sql";  
Write-Host "--done--"  
Write-Host ""  
  
Write-Host "(2) Scripting DROP for procs schema-bound to [$object] 2_drop_procs_$schema`_$object.sql"  
## query referencing schema-bound objects  
$dt = $server.Databases[$database].ExecuteWithResults("select r.referencing_schema_name, r.referencing_entity_name  
from sys.dm_sql_referencing_entities ('$schema.$object', 'OBJECT') as r join sys.sql_modules m on r.referencing_id=m.object_id  
where r.is_caller_dependent = 0 and m.is_schema_bound=1;")  
  
## initialize out file  
Echo "" | Out-File "2_drop_procs_$schema`_$object.sql"  
## loop through schema-bound objects  
ForEach ($t In $dt.Tables)  
{    
   ForEach ($r In $t.Rows)  
   {    
      ## script object   
      $so =  $server.Databases[$database].StoredProcedures[$r[1], $r[0]]  
      $scripter.Script($so) | Out-File -Append "2_drop_procs_$schema`_$object.sql"  
   }  
}  
Write-Host "--done--"  
Write-Host ""  
Write-Host "(3) Scripting DROP table for [$object] to 3_drop_table_$schema`_$object.sql"
$scripter.Script($tableUrn) | Out-File "3_drop_table_$schema`_$object.sql";
Write-Host "--done--"  
Write-Host ""  
  
## now script creates  
$scriptingOptions.ScriptDrops = $False  
  
Write-Host "(4) Scripting CREATE table and permissions for [$object] to !please_edit_4_create_table_$schema`_$object.sql"  
Write-Host "***** rename this script to 4_create_table.sql after completing the updates to the schema"
$scripter.Script($tableUrn) | Out-File "!please_edit_4_create_table_$schema`_$object.sql";  
Write-Host "--done--"  
Write-Host ""  
  
Write-Host "(5) Scripting INSERT INTO table from heap and UPDATE STATISTICS for [$object] to 5_copy_from_heap_$schema`_$object.sql"  
Write-Host "[update this script if columns are added to or removed from the table]"  
Echo "INSERT INTO [$schema].[$object] SELECT * FROM [$schema].[$object_heap]; UPDATE STATISTICS [$schema].[$object] WITH FULLSCAN, NORECOMPUTE" | Out-File "5_copy_from_heap_$schema`_$object.sql";  
Write-Host "--done--"  
Write-Host ""  
  
Write-Host "(6) Scripting CREATE PROC and permissions for procedures schema-bound to [$object] to 6_create_procs_$schema`_$object.sql"  
Write-Host "[update the procedure definitions if columns are renamed or removed]"  
## initialize out file  
Echo "" | Out-File "6_create_procs_$schema`_$object.sql"  
## loop through schema-bound objects  
ForEach ($t In $dt.Tables)  
{    
   ForEach ($r In $t.Rows)  
   {    
      ## script the schema-bound object  
      $so =  $server.Databases[$database].StoredProcedures[$r[1], $r[0]]  
      ForEach($s In $scripter.Script($so))  
        {  
            Echo $s | Out-File -Append "6_create_procs_$schema`_$object.sql"  
            Echo "GO" | Out-File -Append "6_create_procs_$schema`_$object.sql"  
        }  
   }  
}  
Write-Host "--done--"  
Write-Host ""  
  
Write-Host "(7) Scripting DROP $object_heap to 7_drop_heap_$schema`_$object.sql"  
Echo "DROP TABLE $schema.$object_heap" | Out-File "7_drop_heap_$schema`_$object.sql";  
Write-Host "--done--"  
Write-Host ""  
```  
  
 <span data-ttu-id="e297e-146">以下 PowerShell 脚本执行在上一示例中脚本化的架构更改。</span><span class="sxs-lookup"><span data-stu-id="e297e-146">The following PowerShell script executes the schema changes that were scripted in the previous sample.</span></span> <span data-ttu-id="e297e-147">此脚本提取作为变量的表，并执行为该表和相关存储过程生成的架构更改脚本。</span><span class="sxs-lookup"><span data-stu-id="e297e-147">This script takes as argument a table, and executes the schema change scripts that were generated for that table and the associated stored procedures.</span></span>  
  
 <span data-ttu-id="e297e-148">用法： execute_schema_change.ps1 *server_name \* \* db_name `schema_name` table_name*</span><span class="sxs-lookup"><span data-stu-id="e297e-148">Usage: execute_schema_change.ps1 *server_name\*\*db_name`schema_name`table_name*</span></span>  
  
```powershell
# stop execution once an error occurs  
$ErrorActionPreference="Stop"  
  
if($args.Count -le 3)  
{  
   throw "Usage execute_schema_change.ps1 server_name db_name schema_name table_name"  
}  
  
$servername = $args[0]  
$database = $args[1]  
$schema = $args[2]  
$object = $args[3]  
  
[System.Reflection.Assembly]::LoadWithPartialName("Microsoft.SqlServer.SMO") | Out-Null  
  
$server =  New-Object ("Microsoft.SqlServer.Management.SMO.Server") ($servername)  
$database = $server.Databases[$database]  
$table = $database.Tables[$object, $schema]  
if($table.Count -eq 0)  
{  
   throw "Table or database not found"  
}  
  
$1 = Get-Item "1_copy_to_heap_$schema`_$object.sql"  
$2 = Get-Item "2_drop_procs_$schema`_$object.sql"  
$3 = Get-Item "3_drop_table_$schema`_$object.sql"  
$4 = Get-Item "4_create_table_$schema`_$object.sql"  
$5 = Get-Item "5_copy_from_heap_$schema`_$object.sql"  
$6 = Get-Item "6_create_procs_$schema`_$object.sql"  
$7 = Get-Item "7_drop_heap_$schema`_$object.sql"  
  
Write-Host "(1) Running SELECT INTO heap for table [$object] from 1_copy_to_heap_for_$schema`_$object.sql"  
$database.ExecuteNonQuery("$(Echo $1.OpenText().ReadToEnd())")  
Write-Host "--done--"  
Write-Host ""  
  
Write-Host "(2) Running DROP for procs schema-bound from [$object] 2_drop_procs_$schema`_$object.sql"  
$database.ExecuteNonQuery("$(Echo $2.OpenText().ReadToEnd())")  
Write-Host "--done--"  
Write-Host ""  
  
Write-Host "(3) Running DROP table for [$object] to 4_drop_table_$schema`_$object.sql"  
$database.ExecuteNonQuery("$(Echo $3.OpenText().ReadToEnd())")  
Write-Host "--done--"  
Write-Host ""  
  
Write-Host "(4) Running CREATE table and permissions for [$object] from 4_create_table_$schema`_$object.sql"  
$database.ExecuteNonQuery("$(Echo $4.OpenText().ReadToEnd())")  
Write-Host "--done--"  
Write-Host ""  
  
Write-Host "(5) Running INSERT INTO table from heap for [$object] and UPDATE STATISTICS from 5_copy_from_heap_$schema`_$object.sql"  
$database.ExecuteNonQuery("$(Echo $5.OpenText().ReadToEnd())")  
Write-Host "--done--"  
Write-Host ""  
  
Write-Host "(6) Running CREATE PROC and permissions for procedures schema-bound to [$object] from 6_create_procs_$schema`_$object.sql"  
$database.ExecuteNonQuery("$(Echo $6.OpenText().ReadToEnd())")  
Write-Host "--done--"  
Write-Host ""  
  
Write-Host "(7) Running DROP heap from 7_drop_heap_$schema`_$object.sql"  
$database.ExecuteNonQuery("$(Echo $7.OpenText().ReadToEnd())")  
Write-Host "--done--"  
Write-Host ""  
```  
  
## <a name="see-also"></a><span data-ttu-id="e297e-149">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e297e-149">See Also</span></span>  
 [<span data-ttu-id="e297e-150">Memory-Optimized Tables</span><span class="sxs-lookup"><span data-stu-id="e297e-150">Memory-Optimized Tables</span></span>](memory-optimized-tables.md)  
