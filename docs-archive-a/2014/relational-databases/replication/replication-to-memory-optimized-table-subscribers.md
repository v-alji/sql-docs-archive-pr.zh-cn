---
title: 复制到内存优化表订阅服务器 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
ms.assetid: 1a8e6bc7-433e-471d-b646-092dc80a2d1a
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: df61b83d2f6d07cbbd21773b8940dd4e5341f76b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577516"
---
# <a name="replication-to-memory-optimized-table-subscribers"></a><span data-ttu-id="a0700-102">复制到内存优化表订阅服务器</span><span class="sxs-lookup"><span data-stu-id="a0700-102">Replication to Memory-Optimized Table Subscribers</span></span>
  <span data-ttu-id="a0700-103">充当事务复制订阅服务器的表（不包括对等事务复制）可以配置为内存优化表。</span><span class="sxs-lookup"><span data-stu-id="a0700-103">Tables acting as transactional replication subscribers, excluding Peer-to-peer transactional replication, can be configured as memory-optimized tables.</span></span> <span data-ttu-id="a0700-104">其他复制配置与内存优化表不兼容。</span><span class="sxs-lookup"><span data-stu-id="a0700-104">Other replication configurations are not compatible with memory-optimized tables.</span></span>  
  
## <a name="configuring-a-memory-optimized-table-as-a-subscriber"></a><span data-ttu-id="a0700-105">将内存优化表配置为订阅服务器</span><span class="sxs-lookup"><span data-stu-id="a0700-105">Configuring a memory-optimized table as a subscriber</span></span>  
 <span data-ttu-id="a0700-106">若要讲内存优化表配置为订阅服务器，请执行以下步骤。</span><span class="sxs-lookup"><span data-stu-id="a0700-106">To configure a memory-optimized table as a subscriber, perform the following steps.</span></span>  
  
 <span data-ttu-id="a0700-107">**创建和启用发布**</span><span class="sxs-lookup"><span data-stu-id="a0700-107">**Create and Enable Publication**</span></span>  
  
1.  <span data-ttu-id="a0700-108">创建发布。</span><span class="sxs-lookup"><span data-stu-id="a0700-108">Create a publication.</span></span>  
  
2.  <span data-ttu-id="a0700-109">向发布添加项目。</span><span class="sxs-lookup"><span data-stu-id="a0700-109">Add articles to the publication.</span></span> <span data-ttu-id="a0700-110">对于 `@upd_cmd` 参数，请使用 SCALL 或 SQL 约定。</span><span class="sxs-lookup"><span data-stu-id="a0700-110">For the `@upd_cmd` parameter, use the SCALL or SQL convention.</span></span>  
  
    ```  
    EXEC sp_addarticle  
        @publication = N'Publication1',  
        @article = N'Mem_Table',  
        @source_owner = N'dbo',  
        @source_object = N'Mem_Table',  
        @type = N'logbased',  
        @description = null,  
        @creation_script = null,  
        @pre_creation_cmd = N'none',  
        @schema_option = 0x00000000080050DF,  
        @identityrangemanagementoption = N'manual',  
        @destination_table = N'Mem_Table',  
        @destination_owner = N'dbo',  
        @vertical_partition = N'false',  
        @ins_cmd = N'CALL sp_MSins_Mem_Table',  
        @del_cmd = N'CALL sp_MSdel_Mem_Table',  
        @upd_cmd = N'SCALL sp_MSupd_Mem_Table';  
    GO  
    ```  
  
 <span data-ttu-id="a0700-111">**生成快照和调整架构**</span><span class="sxs-lookup"><span data-stu-id="a0700-111">**Generate a Snapshot and Adjust the Schema**</span></span>  
  
1.  <span data-ttu-id="a0700-112">创建一个快照作业并生成快照。</span><span class="sxs-lookup"><span data-stu-id="a0700-112">Create a snapshot job and generate a snapshot.</span></span>  
  
    ```  
    EXEC sp_addpublication_snapshot @publication = N'Publication1', @frequency_type = 1;  
    EXEC sp_startpublication_snapshot @publication = N'Publication1';  
    ```  
  
2.  <span data-ttu-id="a0700-113">导航到快照文件夹。</span><span class="sxs-lookup"><span data-stu-id="a0700-113">Navigate to the snapshot folder.</span></span> <span data-ttu-id="a0700-114">默认位置是 "C:\Program Files\Microsoft SQL Server\MSSQL12. \<INSTANCE>\MSSQL\repldata\unc\XXX\YYYYMMDDHHMMSS \\ "。</span><span class="sxs-lookup"><span data-stu-id="a0700-114">The default location is "C:\Program Files\Microsoft SQL Server\MSSQL12.\<INSTANCE>\MSSQL\repldata\unc\XXX\YYYYMMDDHHMMSS\\".</span></span>  
  
3.  <span data-ttu-id="a0700-115">找到 **。SCH-M**文件，并在 Management Studio 中打开该表。</span><span class="sxs-lookup"><span data-stu-id="a0700-115">Locate the **.SCH** file for your table and open it in Management Studio.</span></span> <span data-ttu-id="a0700-116">按如下所示更改表架构并且更新存储过程。</span><span class="sxs-lookup"><span data-stu-id="a0700-116">Change the table schema and update the stored procedure as described below.</span></span>  
  
     <span data-ttu-id="a0700-117">对在 IDX 文件中定义的索引进行求值。</span><span class="sxs-lookup"><span data-stu-id="a0700-117">Evaluate the indexes defined in the IDX file.</span></span> <span data-ttu-id="a0700-118">修改 `CREATE TABLE` 以指定所需索引、约束、主键和内存优化语法。</span><span class="sxs-lookup"><span data-stu-id="a0700-118">Modify `CREATE TABLE` to specify the required indexes, constraints, primary key, and memory-optimized syntax.</span></span> <span data-ttu-id="a0700-119">对于内存优化表，索引列应为 NOT NULL，而字符类型的索引列必须为 Unicode 并且使用 BIN2 排序规则。</span><span class="sxs-lookup"><span data-stu-id="a0700-119">For memory-optimized tables, index columns should be NOT NULL and index columns of character types must be Unicode and use BIN2 collation.</span></span> <span data-ttu-id="a0700-120">请参阅下面的示例：</span><span class="sxs-lookup"><span data-stu-id="a0700-120">See example below:</span></span>  
  
    ```  
    SET ANSI_PADDING ON;  
    GO  
  
    SET ANSI_NULLS ON;  
    GO  
  
    SET QUOTED_IDENTIFIER ON;  
    GO  
  
    CREATE TABLE [dbo].[Mem_Table]([c1] [int] NOT NULL,  
        [c2] [float] NOT NULL,  
        [c3] [decimal](10, 2) NOT NULL,  
        [c4] [nvarchar](5) COLLATE SQL_Latin1_General_CP850_BIN2 NOT NULL,  
        INDEX [hash_index_sample_memoryoptimizedtable_c2] HASH (c2) WITH (BUCKET_COUNT = 1024),  
        INDEX [index_sample_memoryoptimizedtable_c3] NONCLUSTERED ([c3]),  
        INDEX [nvarchar_index_sample_memoryoptimizedtable_c4] ([c4]),  
        CONSTRAINT [PK_sample_memoryoptimizedtable] PRIMARY KEY NONCLUSTERED ([c1])) WITH (MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_AND_DATA);  
    GO  
    ```  
  
4.  <span data-ttu-id="a0700-121">在将 SCALL 约定用于 `@upd_cmd` 参数时，转到架构 (.SCH) 文件并且在 `create procedure [sp_MSupd_<SCHEMA><TABLE_NAME>]` 中更改表更新语句，以便删除主键列。</span><span class="sxs-lookup"><span data-stu-id="a0700-121">When using SCALL convention for the `@upd_cmd` parameter, go to the schema (.SCH) file and change the table update statement in `create procedure [sp_MSupd_<SCHEMA><TABLE_NAME>]` to remove primary key columns.</span></span>  
  
     <span data-ttu-id="a0700-122">若要支持主键更新，请使用自定义更新存储过程替换主键更新语句，如下所示：</span><span class="sxs-lookup"><span data-stu-id="a0700-122">To support primary key updates, use a custom update stored procedure to replace the primary key update statement, as follows:</span></span>  
  
    1.  <span data-ttu-id="a0700-123">选择缺失的列值（SCALL 仅提供涉及到更新操作的列）。</span><span class="sxs-lookup"><span data-stu-id="a0700-123">Select missing column values (SCALL only provides the column involved into the update operation).</span></span>  
  
    2.  <span data-ttu-id="a0700-124">删除现有记录。</span><span class="sxs-lookup"><span data-stu-id="a0700-124">Delete the existing record.</span></span>  
  
    3.  <span data-ttu-id="a0700-125">将新记录以及提供的新值（包括新主键）一起插入。</span><span class="sxs-lookup"><span data-stu-id="a0700-125">Insert a new record with new values provided including the new primary key.</span></span>  
  
     <span data-ttu-id="a0700-126">原始更新过程如下所示：</span><span class="sxs-lookup"><span data-stu-id="a0700-126">The original update procedure looks like this:</span></span>  
  
    ```  
    create procedure [sp_MSupd_Mem_Table]  
                   @c1 int = NULL,  
                   @c2 float = NULL,  
                   @c3 decimal(10,2) = NULL,  
                   @c4 nvarchar(5) = NULL,  
                   @pkc1 int = NULL,  
                   @bitmap binary(1)  
    as  
    begin    
    if (substring(@bitmap,1,1) & 1 = 1)  
    begin   
    update [dbo].[Mem_Table] set  
                   [c1] = case substring(@bitmap,1,1) & 1 when 1 then @c1 else [c1] end,  
                   [c2] = case substring(@bitmap,1,1) & 2 when 2 then @c2 else [c2] end,  
                   [c3] = case substring(@bitmap,1,1) & 4 when 4 then @c3 else [c3] end,  
                   [c4] = case substring(@bitmap,1,1) & 8 when 8 then @c4 else [c4] end  
    where [c1] = @pkc1  
    if @@rowcount = 0  
        if @@microsoftversion>0x07320000  
            exec sp_MSreplraiserror 20598  
    end    
    else  
    begin   
    update [dbo].[Mem_Table] set  
                   [c2] = case substring(@bitmap,1,1) & 2 when 2 then @c2 else [c2] end,  
                   [c3] = case substring(@bitmap,1,1) & 4 when 4 then @c3 else [c3] end,  
                   [c4] = case substring(@bitmap,1,1) & 8 when 8 then @c4 else [c4] end  
    where [c1] = @pkc1  
    if @@rowcount = 0  
        if @@microsoftversion>0x07320000  
            exec sp_MSreplraiserror 20598  
    end   
    end   
    go  
    ```  
  
     <span data-ttu-id="a0700-127">如果主键始终不应在发布服务器上更新。</span><span class="sxs-lookup"><span data-stu-id="a0700-127">If the primary key should never be updated on a publisher.</span></span> <span data-ttu-id="a0700-128">按如下所示对更新过程中这些列的更新进行注释：</span><span class="sxs-lookup"><span data-stu-id="a0700-128">Comment out the update to such columns in the update procedure as follows:</span></span>  
  
    ```  
    create procedure [sp_MSupd_Mem_Table]  
                   @c1 int = NULL,  
                   @c2 float = NULL,  
                   @c3 decimal(10,2) = NULL,  
                   @c4 nvarchar(5) = NULL,  
                   @pkc1 int = NULL,  
                   @bitmap binary(1)  
    as  
    begin    
    if (substring(@bitmap,1,1) & 1 = 1)  
    begin   
    update [dbo].[Mem_Table] set  
    --             [c1] = case substring(@bitmap,1,1) & 1 when 1 then @c1 else [c1] end,  
                   [c2] = case substring(@bitmap,1,1) & 2 when 2 then @c2 else [c2] end,  
                   [c3] = case substring(@bitmap,1,1) & 4 when 4 then @c3 else [c3] end,  
                   [c4] = case substring(@bitmap,1,1) & 8 when 8 then @c4 else [c4] end  
    where [c1] = @pkc1  
    if @@rowcount = 0  
        if @@microsoftversion>0x07320000  
            exec sp_MSreplraiserror 20598  
    end    
    else  
    begin   
    update [dbo].[Mem_Table] set  
                   [c2] = case substring(@bitmap,1,1) & 2 when 2 then @c2 else [c2] end,  
                   [c3] = case substring(@bitmap,1,1) & 4 when 4 then @c3 else [c3] end,  
                   [c4] = case substring(@bitmap,1,1) & 8 when 8 then @c4 else [c4] end  
    where [c1] = @pkc1  
    if @@rowcount = 0  
        if @@microsoftversion>0x07320000  
            exec sp_MSreplraiserror 20598  
    end   
    end   
    go  
    ```  
  
     <span data-ttu-id="a0700-129">若要允许支持主键更新，请按如下所示修改更新过程</span><span class="sxs-lookup"><span data-stu-id="a0700-129">To allow the support of updates to the primary key, modify the update procedure to read as follows</span></span>  
  
    ```  
    create procedure [sp_MSupd_Mem_Table]  
                   @c1 int = NULL,  
                   @c2 float = NULL,  
                   @c3 decimal(10,2) = NULL,  
                   @c4 nvarchar(5) = NULL,  
                    @pkc1 int = NULL,  
                   @bitmap binary(1)  
    as  
    begin    
    if (substring(@bitmap,1,1) & 1 = 1)  
    begin   
    select  
                   @c1 = case substring(@bitmap,1,1) & 1 when 1 then @c1 else [c1] end,  
                   @c2 = case substring(@bitmap,1,1) & 2 when 2 then @c2 else [c2] end,  
                   @c3 = case substring(@bitmap,1,1) & 4 when 4 then @c3 else [c3] end,  
                   @c4 = case substring(@bitmap,1,1) & 8 when 8 then @c4 else [c4] end  
    from [dbo].[Mem_Table] where [c1] = @pkc1  
    if @@rowcount <> 0 begin  
            delete [dbo].[Mem_Table] where [c1] = @pkc1  
            if @@rowcount <> 0  
                   insert into [dbo].[Mem_Table]([c1],  
                           [c2],  
                           [c3],  
                           [c4]) values (  
                           @c1,  
                           @c2,  
                           @c3,  
                           @c4  
                   )   
    end  
    if @@rowcount = 0  
        if @@microsoftversion>0x07320000  
            exec sp_MSreplraiserror 20598  
    end    
    else  
    begin   
    update [dbo].[Mem_Table] set  
                   [c2] = case substring(@bitmap,1,1) & 2 when 2 then @c2 else [c2] end,  
                   [c3] = case substring(@bitmap,1,1) & 4 when 4 then @c3 else [c3] end,  
                   [c4] = case substring(@bitmap,1,1) & 8 when 8 then @c4 else [c4] end  
    where [c1] = @pkc1  
    if @@rowcount = 0  
        if @@microsoftversion>0x07320000  
            exec sp_MSreplraiserror 20598  
    end   
    end   
    go  
    ```  
  
5.  <span data-ttu-id="a0700-130">使用 "**提升为快照隔离**" 选项创建订阅服务器数据库，并在使用非 Unicode 字符数据类型的情况下将默认排序规则设置为 Latin1_General_CS_AS_KS_WS。</span><span class="sxs-lookup"><span data-stu-id="a0700-130">Create subscriber database using the **elevate to snapshot isolation** option and set the default collation to Latin1_General_CS_AS_KS_WS in case of using non Unicode character data types.</span></span>  
  
    ```  
    CREATE DATABASE [Sub]   
    CONTAINMENT = NONE   
    ON PRIMARY ( NAME = [Sub], FILENAME = [C:\Program Files\Microsoft SQL Server\MSSQL12\MSSQL\DATA\Sub.mdf]),   
    FILEGROUP [mem] CONTAINS MEMORY_OPTIMIZED_DATA ( NAME = [mem],   
    FILENAME = [C:\Program Files\Microsoft SQL Server\MSSQL12\MSSQL\DATA\Sub])  
    LOG ON ( NAME = [Sub_log], FILENAME = [C:\Program Files\Microsoft SQL Server\MSSQL12\MSSQL\DATA\Sub.ldf])  
    COLLATE Latin1_General_CS_AS_KS_WS;  
  
    ALTER DATABASE [Sub] SET MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT = ON;  
    GO  
    ```  
  
6.  <span data-ttu-id="a0700-131">将架构应用于订阅服务器的数据库，并保存架构以供将来使用。</span><span class="sxs-lookup"><span data-stu-id="a0700-131">Apply the schema to a subscriber's database and save the schema for future use.</span></span>  
  
7.  <span data-ttu-id="a0700-132">加载发布服务器（源）数据写入订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="a0700-132">Load the publisher (source) data to the subscriber.</span></span> <span data-ttu-id="a0700-133">在您添加订阅前，不应在发布服务器上更改数据。</span><span class="sxs-lookup"><span data-stu-id="a0700-133">Data should not change at the publisher until you add a subscription.</span></span>  <span data-ttu-id="a0700-134">可按如下所示使用 BCP：</span><span class="sxs-lookup"><span data-stu-id="a0700-134">You can use BCP as shown below:</span></span>  
  
    ```  
    bcp Pub.dbo.Mem_Table out Mem_Table.bcp -S. -T -C1252 -n  
    bcp Sub.dbo.Mem_Table in Mem_Table.bcp -S. -T -C1252 -n  
    ```  
  
8.  <span data-ttu-id="a0700-135">重新配置项目以便禁用订阅服务器上的架构更改：</span><span class="sxs-lookup"><span data-stu-id="a0700-135">Reconfigure the article to disable schema changes on the subscriber:</span></span>  
  
    ```  
    EXEC sp_changearticle  
        @publication = N'Publication1',  
        @article = N'Mem_Table',  
        @property = N'schema_option',  
        @value = 0,  
        @force_invalidate_snapshot = 1,  
        @force_reinit_subscription = 1;  
    GO  
    ```  
  
 <span data-ttu-id="a0700-136">**添加非同步订阅**</span><span class="sxs-lookup"><span data-stu-id="a0700-136">**Add no sync Subscription**</span></span>  
  
 <span data-ttu-id="a0700-137">添加非同步订阅。</span><span class="sxs-lookup"><span data-stu-id="a0700-137">Add a nosync subscription.</span></span>  
  
```  
EXEC sp_addsubscription  
    @publication = N' Publication1',  
    @subscriber = @@ServerName,  
    @destination_db = N'Sub',  
    @subscription_type = N'Push',  
    @sync_type = N'replication support only',  
    @article = N'all',  
    @update_mode = N'read only',  
    @subscriber_type = 0;  
GO  
```  
  
 <span data-ttu-id="a0700-138">内存优化表现在应该开始从发布服务器接收更新。</span><span class="sxs-lookup"><span data-stu-id="a0700-138">Memory-optimized tables should now start receiving updates from the publisher.</span></span>  
  
## <a name="restrictions"></a><span data-ttu-id="a0700-139">限制</span><span class="sxs-lookup"><span data-stu-id="a0700-139">Restrictions</span></span>  
 <span data-ttu-id="a0700-140">仅支持单向事务复制。</span><span class="sxs-lookup"><span data-stu-id="a0700-140">Only one-way transactional replication is supported.</span></span> <span data-ttu-id="a0700-141">不支持对等事务复制。</span><span class="sxs-lookup"><span data-stu-id="a0700-141">Peer-to-peer transactional replication is not supported.</span></span>  
  
 <span data-ttu-id="a0700-142">内存优化表无法发布。</span><span class="sxs-lookup"><span data-stu-id="a0700-142">Memory-optimized tables cannot be published.</span></span>  
  
 <span data-ttu-id="a0700-143">分发服务器上的复制表无法配置为内存优化表。</span><span class="sxs-lookup"><span data-stu-id="a0700-143">Replication tables on the distributor cannot be configured as memory-optimized tables.</span></span>  
  
 <span data-ttu-id="a0700-144">合并复制无法包括内存优化表。</span><span class="sxs-lookup"><span data-stu-id="a0700-144">Merge replication cannot include memory-optimized tables.</span></span>  
  
 <span data-ttu-id="a0700-145">在订阅服务器上，在事务复制中涉及的表可以配置为内存优化表，但订阅服务器上的表必须满足针对内存优化表的要求。</span><span class="sxs-lookup"><span data-stu-id="a0700-145">At the subscriber, tables involved in transactional replication can be configured as memory optimized tables, but the subscriber tables must meet the requirements of memory-optimized tables.</span></span> <span data-ttu-id="a0700-146">这要求以下限制。</span><span class="sxs-lookup"><span data-stu-id="a0700-146">This requires the following restrictions.</span></span>  
  
-   <span data-ttu-id="a0700-147">若要在事务复制订阅服务器上创建内存优化表，必须手动修改用于创建内存优化表的快照架构文件。</span><span class="sxs-lookup"><span data-stu-id="a0700-147">To create a memory-optimized table on a transactional replication subscriber, the snapshot schema files used to create the memory-optimized tables must be manually modified.</span></span> <span data-ttu-id="a0700-148">有关详细信息，请参阅[修改架构文件](#Schema)。</span><span class="sxs-lookup"><span data-stu-id="a0700-148">For more information, see [Modifying a schema file](#Schema).</span></span>  
  
-   <span data-ttu-id="a0700-149">根据内存优化表的行限制，复制到订阅服务器上的内存优化表的表限制为 8060 字节。</span><span class="sxs-lookup"><span data-stu-id="a0700-149">Tables replicated to memory-optimized tables on a subscriber are limited to the 8060 bytes per row limit of memory-optimized tables.</span></span>  
  
-   <span data-ttu-id="a0700-150">复制到订阅服务器上的内存优化表的表限制为内存优化表允许的数据类型。</span><span class="sxs-lookup"><span data-stu-id="a0700-150">Tables replicated to memory-optimized tables on a subscriber are limited to the data types permitted in memory-optimized tables.</span></span> <span data-ttu-id="a0700-151">有关详细信息，请参阅[支持的数据类型](../in-memory-oltp/supported-data-types-for-in-memory-oltp.md)。</span><span class="sxs-lookup"><span data-stu-id="a0700-151">For more information, see [Supported Data Types](../in-memory-oltp/supported-data-types-for-in-memory-oltp.md).</span></span>  
  
-   <span data-ttu-id="a0700-152">对于更新要复制到订阅服务器上内存优化表的表的主键，存在一些限制。</span><span class="sxs-lookup"><span data-stu-id="a0700-152">There are restrictions on updating the primary key of tables being replicated to a memory-optimized table on a subscriber.</span></span> <span data-ttu-id="a0700-153">有关详细信息，请参阅[将更改复制到主键](#PrimaryKey)。</span><span class="sxs-lookup"><span data-stu-id="a0700-153">For more information, see [Replicating changes to a primary key](#PrimaryKey).</span></span>  
  
-   <span data-ttu-id="a0700-154">在内存优化表中不支持外键、唯一约束、触发器、架构修改、ROWGUIDCOL、计算列、数据压缩、别名数据类型、版本化和锁。</span><span class="sxs-lookup"><span data-stu-id="a0700-154">Foreign key, unique constraint, triggers, schema modifications, ROWGUIDCOL, computed columns, data compression, alias data types, versioning, and locks are not supported in memory-optimized tables.</span></span> <span data-ttu-id="a0700-155">有关信息，请参阅 [Transact-SQL Constructs Not Supported by In-Memory OLTP](../in-memory-oltp/transact-sql-constructs-not-supported-by-in-memory-oltp.md) 。</span><span class="sxs-lookup"><span data-stu-id="a0700-155">See [Transact-SQL Constructs Not Supported by In-Memory OLTP](../in-memory-oltp/transact-sql-constructs-not-supported-by-in-memory-oltp.md) for information.</span></span>  
  
##  <a name="modifying-a-schema-file"></a><a name="Schema"></a><span data-ttu-id="a0700-156">修改架构文件</span><span class="sxs-lookup"><span data-stu-id="a0700-156">Modifying a schema file</span></span>  
  
-   <span data-ttu-id="a0700-157">不支持聚集索引。</span><span class="sxs-lookup"><span data-stu-id="a0700-157">Clustered indexes are not supported.</span></span> <span data-ttu-id="a0700-158">将所有聚集索引更改为非聚集索引。</span><span class="sxs-lookup"><span data-stu-id="a0700-158">Change any clustered indexes to nonclustered indexes.</span></span>  
  
-   <span data-ttu-id="a0700-159">索引键中的所有列都必须指定为 `NOT NULL`。</span><span class="sxs-lookup"><span data-stu-id="a0700-159">All columns in the key of an index must be specified as `NOT NULL`.</span></span>  
  
-   <span data-ttu-id="a0700-160">如果使用内存优化表选项 `DURABILITY = SCHEMA_AND_DATA` ，则表必须具有非聚集主键索引。</span><span class="sxs-lookup"><span data-stu-id="a0700-160">If using the memory-optimized table option `DURABILITY = SCHEMA_AND_DATA` the table must have a nonclustered primary key index.</span></span>  
  
-   <span data-ttu-id="a0700-161">ANSI_PADDING 必须为 ON。</span><span class="sxs-lookup"><span data-stu-id="a0700-161">ANSI_PADDING must be ON.</span></span>  
  
##  <a name="replicating-changes-to-a-primary-key"></a><a name="PrimaryKey"></a><span data-ttu-id="a0700-162">将更改复制到主键</span><span class="sxs-lookup"><span data-stu-id="a0700-162">Replicating changes to a primary key</span></span>  
 <span data-ttu-id="a0700-163">内存优化表的主键无法更新。</span><span class="sxs-lookup"><span data-stu-id="a0700-163">The primary key of a memory-optimized table cannot be updated.</span></span> <span data-ttu-id="a0700-164">若要复制订阅服务器上的主键更新，请修改更新存储过程以便将该更新作为删除和插入对提供。</span><span class="sxs-lookup"><span data-stu-id="a0700-164">To replicate a primary key update on a subscriber, modify the update stored procedure to deliver the update as a delete and insert pair.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0700-165">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a0700-165">See Also</span></span>  
 [<span data-ttu-id="a0700-166">SQL Server 复制</span><span class="sxs-lookup"><span data-stu-id="a0700-166">SQL Server Replication</span></span>](sql-server-replication.md)  
  
  
