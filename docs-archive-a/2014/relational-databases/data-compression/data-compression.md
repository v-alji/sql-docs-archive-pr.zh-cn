---
title: 数据压缩 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- page compression [Database Engine]
- indexes [SQL Server], compressed
- compressed indexes [SQL Server]
- storage compression [Database Engine]
- tables [SQL Server], compressed
- storage [SQL Server], compressed
- compression [SQL Server]
- row compression [Database Engine]
- compression [SQL Server], about compressed tables and indexes
- data compression [Database Engine]
- compressed tables [SQL Server]
ms.assetid: 5f33e686-e115-4687-bd39-a00c48646513
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 48c4b11963d8e05ff7787ce9200329daf2e899ba
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589707"
---
# <a name="data-compression"></a><span data-ttu-id="41c3a-102">数据压缩</span><span class="sxs-lookup"><span data-stu-id="41c3a-102">Data Compression</span></span>
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="41c3a-103">支持针对行存储表和索引的行和页压缩，并且支持针对列存储表和索引的列存储和列存储存档压缩。</span><span class="sxs-lookup"><span data-stu-id="41c3a-103">supports row and page compression for rowstore tables and indexes, and supports columnstore and columnstore archival compression for columnstore tables and indexes.</span></span>  
  
 <span data-ttu-id="41c3a-104">对于行存储表和索引，使用数据压缩功能可帮助减小数据库的大小。</span><span class="sxs-lookup"><span data-stu-id="41c3a-104">For rowstore tables and indexes, use the data compression feature to help reduce the size of the database.</span></span> <span data-ttu-id="41c3a-105">除了节省空间之外，数据压缩还可以帮助提高 I/O 密集型工作负荷的性能，因为数据存储在更少的页中，查询需要从磁盘读取的页更少。</span><span class="sxs-lookup"><span data-stu-id="41c3a-105">In addition to saving space, data compression can help improve performance of I/O intensive workloads because the data is stored in fewer pages and queries need to read fewer pages from disk.</span></span> <span data-ttu-id="41c3a-106">但是，在与应用程序交换数据时，在数据库服务器上需要额外的 CPU 资源来压缩和解压缩数据。</span><span class="sxs-lookup"><span data-stu-id="41c3a-106">However, extra CPU resources are required on the database server to compress and decompress the data, while data is exchanged with the application.</span></span> <span data-ttu-id="41c3a-107">您可以在以下数据库对象上配置行和页压缩：</span><span class="sxs-lookup"><span data-stu-id="41c3a-107">You can configure row and page compression on the following database objects:</span></span>  
  
-   <span data-ttu-id="41c3a-108">存储为堆的整个表。</span><span class="sxs-lookup"><span data-stu-id="41c3a-108">A whole table that is stored as a heap.</span></span>  
  
-   <span data-ttu-id="41c3a-109">存储为聚集索引的整个表。</span><span class="sxs-lookup"><span data-stu-id="41c3a-109">A whole table that is stored as a clustered index.</span></span>  
  
-   <span data-ttu-id="41c3a-110">整个非聚集索引。</span><span class="sxs-lookup"><span data-stu-id="41c3a-110">A whole nonclustered index.</span></span>  
  
-   <span data-ttu-id="41c3a-111">整个索引视图。</span><span class="sxs-lookup"><span data-stu-id="41c3a-111">A whole indexed view.</span></span>  
  
-   <span data-ttu-id="41c3a-112">对于已分区表和已分区索引，可为每个分区配置压缩选项，且对象的各个分区的压缩设置不必相同。</span><span class="sxs-lookup"><span data-stu-id="41c3a-112">For partitioned tables and indexes, you can configure the compression option for each partition, and the various partitions of an object do not have to have the same compression setting.</span></span>  
  
 <span data-ttu-id="41c3a-113">对于列存储表和索引，所有列存储表和索引始终使用列存储压缩，并且用户无法对此进行配置。</span><span class="sxs-lookup"><span data-stu-id="41c3a-113">For columnstore tables and indexes, all columnstore tables and indexes always use columnstore compression and this is not user configurable.</span></span> <span data-ttu-id="41c3a-114">在您能够付出额外的时间和 CPU 资源来存储和检索数据的情况下，使用列存储存档压缩可进一步减少数据大小。</span><span class="sxs-lookup"><span data-stu-id="41c3a-114">Use columnstore archival compression to further reduce the data size for situations when you can afford extra time and CPU resources to store and retrieve the data.</span></span>  <span data-ttu-id="41c3a-115">您可以在以下数据库对象上配置列存储存档压缩：</span><span class="sxs-lookup"><span data-stu-id="41c3a-115">You can configure columnstore archival compression on the following database objects:</span></span>  
  
-   <span data-ttu-id="41c3a-116">整个列存储表或整个聚集列存储索引。</span><span class="sxs-lookup"><span data-stu-id="41c3a-116">A whole columnstore table or a whole clustered columnstore index.</span></span>  <span data-ttu-id="41c3a-117">因为列存储表存储为聚集列存储索引，所有两种方法具有相同的结果。</span><span class="sxs-lookup"><span data-stu-id="41c3a-117">Since a columnstore table is stored as a clustered columnstore index, both approaches have the same results.</span></span>  
  
-   <span data-ttu-id="41c3a-118">整个非聚集列存储索引。</span><span class="sxs-lookup"><span data-stu-id="41c3a-118">A whole nonclustered columnstore index.</span></span>  
  
-   <span data-ttu-id="41c3a-119">对于列存储表和列存储索引，可为每个分区配置存档压缩选项，且各个分区的存档压缩设置不必相同。</span><span class="sxs-lookup"><span data-stu-id="41c3a-119">For partitioned columnstore tables and columnstore indexes, you can configure the archival compression option for each partition, and the various partitions do not have to have the same archival compression setting.</span></span>  
  
## <a name="considerations-for-when-you-use-row-and-page-compression"></a><span data-ttu-id="41c3a-120">使用行压缩和页压缩时的注意事项</span><span class="sxs-lookup"><span data-stu-id="41c3a-120">Considerations for When You Use Row and Page Compression</span></span>  
 <span data-ttu-id="41c3a-121">使用行压缩和页压缩时，应注意以下事项：</span><span class="sxs-lookup"><span data-stu-id="41c3a-121">When you use row and page compression, be aware the following considerations:</span></span>  
  
-   <span data-ttu-id="41c3a-122">在 Service Pack 或后续版本中，有关数据压缩的详细信息如有更改，恕不另行通知。</span><span class="sxs-lookup"><span data-stu-id="41c3a-122">The details of data compression are subject to change without notice in service packs or subsequent releases.</span></span>  
  
-   <span data-ttu-id="41c3a-123">不是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的每个版本都提供压缩功能。</span><span class="sxs-lookup"><span data-stu-id="41c3a-123">Compression is not available in every edition of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="41c3a-124">有关详细信息，请参阅 [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)。</span><span class="sxs-lookup"><span data-stu-id="41c3a-124">For more information, see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
-   <span data-ttu-id="41c3a-125">压缩功能不可用于系统表。</span><span class="sxs-lookup"><span data-stu-id="41c3a-125">Compression is not available for system tables.</span></span>  
  
-   <span data-ttu-id="41c3a-126">通过压缩可在一页上存储更多的行，但不会更改表或索引的最大行大小。</span><span class="sxs-lookup"><span data-stu-id="41c3a-126">Compression can allow more rows to be stored on a page, but does not change the maximum row size of a table or index.</span></span>  
  
-   <span data-ttu-id="41c3a-127">当最大行大小加上压缩开销超过最大行大小 8060 个字节时，不能对表启用压缩功能。</span><span class="sxs-lookup"><span data-stu-id="41c3a-127">A table cannot be enabled for compression when the maximum row size plus the compression overhead exceeds the maximum row size of 8060 bytes.</span></span> <span data-ttu-id="41c3a-128">例如，不能压缩具有 c1 和 c2 列的表， `char(8000)` `char(53)` 因为存在额外的压缩开销。</span><span class="sxs-lookup"><span data-stu-id="41c3a-128">For example, a table that has the columns c1`char(8000)` and c2`char(53)` cannot be compressed because of the additional compression overhead.</span></span> <span data-ttu-id="41c3a-129">当使用 vardecimal 存储格式时，会在启用此格式时执行行大小检查。</span><span class="sxs-lookup"><span data-stu-id="41c3a-129">When the vardecimal storage format is used, the row-size check is performed when the format is enabled.</span></span> <span data-ttu-id="41c3a-130">对于行压缩和页压缩，在最初压缩对象时会执行行大小检查，以后在每插入或修改一行时也都会执行这一检查。</span><span class="sxs-lookup"><span data-stu-id="41c3a-130">For row and page compression, the row-size check is performed when the object is initially compressed, and then checked as each row is inserted or modified.</span></span> <span data-ttu-id="41c3a-131">压缩功能要求遵循下面两条规则：</span><span class="sxs-lookup"><span data-stu-id="41c3a-131">Compression enforces the following two rules:</span></span>  
  
    -   <span data-ttu-id="41c3a-132">固定长度类型的更新必须始终成功。</span><span class="sxs-lookup"><span data-stu-id="41c3a-132">An update to a fixed-length type must always succeed.</span></span>  
  
    -   <span data-ttu-id="41c3a-133">禁用数据压缩必须总是成功。</span><span class="sxs-lookup"><span data-stu-id="41c3a-133">Disabling data compression must always succeed.</span></span> <span data-ttu-id="41c3a-134">即使已压缩的行可以容纳在页面中（意味着它小于 8060 个字节）， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 也不允许对哪些在未压缩时无法容纳在行中的更新。</span><span class="sxs-lookup"><span data-stu-id="41c3a-134">Even if the compressed row fits on the page, which means that it is less than 8060 bytes; [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prevents updates that would not fit on the row when it is uncompressed.</span></span>  
  
-   <span data-ttu-id="41c3a-135">当指定分区列表时，可以将各个分区的压缩类型设置为 ROW、PAGE 或 NONE。</span><span class="sxs-lookup"><span data-stu-id="41c3a-135">When a list of partitions is specified, the compression type can be set to ROW, PAGE, or NONE on individual partitions.</span></span> <span data-ttu-id="41c3a-136">如果未指定分区列表，将使用语句中指定的数据压缩属性来设置所有分区。</span><span class="sxs-lookup"><span data-stu-id="41c3a-136">If the list of partitions is not specified, all partitions are set with the data compression property that is specified in the statement.</span></span> <span data-ttu-id="41c3a-137">创建表或索引时，除非指定了其他压缩设置，否则数据压缩将设置为 NONE。</span><span class="sxs-lookup"><span data-stu-id="41c3a-137">When a table or index is created, data compression is set to NONE unless otherwise specified.</span></span> <span data-ttu-id="41c3a-138">修改表时，除非指定了其他压缩设置，否则将保留现有压缩设置。</span><span class="sxs-lookup"><span data-stu-id="41c3a-138">When a table is modified, the existing compression is preserved unless otherwise specified.</span></span>  
  
-   <span data-ttu-id="41c3a-139">如果指定的分区列表或分区超出范围，将生成错误。</span><span class="sxs-lookup"><span data-stu-id="41c3a-139">If you specify a list of partitions or a partition that is out of range, an error will be generated.</span></span>  
  
-   <span data-ttu-id="41c3a-140">非聚集索引不继承表的压缩属性。</span><span class="sxs-lookup"><span data-stu-id="41c3a-140">Nonclustered indexes do not inherit the compression property of the table.</span></span> <span data-ttu-id="41c3a-141">若要压缩索引，必须显式设置索引的压缩属性。</span><span class="sxs-lookup"><span data-stu-id="41c3a-141">To compress indexes, you must explicitly set the compression property of the indexes.</span></span> <span data-ttu-id="41c3a-142">默认情况下，在创建索引时，索引的压缩设置将设置为 NONE。</span><span class="sxs-lookup"><span data-stu-id="41c3a-142">By default, the compression setting for indexes will set to NONE when the index is created.</span></span>  
  
-   <span data-ttu-id="41c3a-143">对堆创建聚集索引时，聚集索引会继承该堆的压缩状态，除非指定了另一压缩状态。</span><span class="sxs-lookup"><span data-stu-id="41c3a-143">When a clustered index is created on a heap, the clustered index inherits the compression state of the heap unless an alternative compression state is specified.</span></span>  
  
-   <span data-ttu-id="41c3a-144">如果堆配置为页级压缩，则只有在以下情况下，页才会进行页级压缩：</span><span class="sxs-lookup"><span data-stu-id="41c3a-144">When a heap is configured for page-level compression, pages receive page-level compression only in the following ways:</span></span>  
  
    -   <span data-ttu-id="41c3a-145">在启用大容量优化的情况下大容量导入数据。</span><span class="sxs-lookup"><span data-stu-id="41c3a-145">Data is bulk imported with bulk optimizations enabled.</span></span>  
  
    -   <span data-ttu-id="41c3a-146">数据是使用 INSERT INTO ...WITH (TABLOCK) 语法和表没有非聚集索引。</span><span class="sxs-lookup"><span data-stu-id="41c3a-146">Data is inserted using INSERT INTO ... WITH (TABLOCK) syntax and the table does not have a nonclustered index.</span></span>  
  
    -   <span data-ttu-id="41c3a-147">表是通过执行带 PAGE 压缩选项的 ALTER TABLE ...REBUILD 语句重新生成的。</span><span class="sxs-lookup"><span data-stu-id="41c3a-147">A table is rebuilt by executing the ALTER TABLE ... REBUILD statement with the PAGE compression option.</span></span>  
  
-   <span data-ttu-id="41c3a-148">通过 DML 操作被分配到堆中的新页面将不会使用 PAGE 压缩，除非重新生成该堆。</span><span class="sxs-lookup"><span data-stu-id="41c3a-148">New pages allocated in a heap as part of DML operations will not use PAGE compression until the heap is rebuilt.</span></span> <span data-ttu-id="41c3a-149">重新生成堆的方法有：删除压缩然后重新应用压缩，或者创建聚集索引然后再删除聚集索引。</span><span class="sxs-lookup"><span data-stu-id="41c3a-149">Rebuild the heap by removing and reapplying compression, or by creating and removing a clustered index.</span></span>  
  
-   <span data-ttu-id="41c3a-150">若要更改堆的压缩设置，要求对表重新生成所有非聚集索引，以便它们具有指向堆中的新行位置的指针。</span><span class="sxs-lookup"><span data-stu-id="41c3a-150">Changing the compression setting of a heap requires all nonclustered indexes on the table to be rebuilt so that they have pointers to the new row locations in the heap.</span></span>  
  
-   <span data-ttu-id="41c3a-151">可以联机或脱机启用或禁用 ROW 或 PAGE 压缩功能。</span><span class="sxs-lookup"><span data-stu-id="41c3a-151">You can enable or disable ROW or PAGE compression online or offline.</span></span> <span data-ttu-id="41c3a-152">当执行联机操作时，对堆启用压缩功能是单线程的。</span><span class="sxs-lookup"><span data-stu-id="41c3a-152">Enabling compression on a heap is single threaded for an online operation.</span></span>  
  
-   <span data-ttu-id="41c3a-153">启用或禁用行压缩或页压缩的磁盘空间要求与创建或重新生成索引时的磁盘空间要求相同。</span><span class="sxs-lookup"><span data-stu-id="41c3a-153">The disk space requirements for enabling or disabling row or page compression are the same as for creating or rebuilding an index.</span></span> <span data-ttu-id="41c3a-154">对于已分区数据，可以通过每次对一个分区启用或禁用压缩功能来减少所需的空间。</span><span class="sxs-lookup"><span data-stu-id="41c3a-154">For partitioned data, you can reduce the space that is required by enabling or disabling compression for one partition at a time.</span></span>  
  
-   <span data-ttu-id="41c3a-155">若要确定已分区表中分区的压缩状态，请查询 sys.partitions 目录视图的 data_compression 列。</span><span class="sxs-lookup"><span data-stu-id="41c3a-155">To determine the compression state of partitions in a partitioned table, query the data_compression column of the sys.partitions catalog view.</span></span>  
  
-   <span data-ttu-id="41c3a-156">压缩索引时，可以使用行压缩和页压缩来压缩叶级页。</span><span class="sxs-lookup"><span data-stu-id="41c3a-156">When you are compressing indexes, leaf-level pages can be compressed with both row and page compression.</span></span> <span data-ttu-id="41c3a-157">非叶级页不接收页压缩。</span><span class="sxs-lookup"><span data-stu-id="41c3a-157">Non-leaf-level pages do not receive page compression.</span></span>  
  
-   <span data-ttu-id="41c3a-158">由于大小的关系，大值数据类型有时不与普通行数据存储在一起，而是存储在特殊用途的页上。</span><span class="sxs-lookup"><span data-stu-id="41c3a-158">Because of their size, large-value data types are sometimes stored separately from the normal row data on special purpose pages.</span></span> <span data-ttu-id="41c3a-159">对于单独存储的数据，数据压缩不可用。</span><span class="sxs-lookup"><span data-stu-id="41c3a-159">Data compression is not available for the data that is stored separately.</span></span>  
  
-   <span data-ttu-id="41c3a-160">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 中实现 vardecimal 存储格式的表在升级后会保留该设置。</span><span class="sxs-lookup"><span data-stu-id="41c3a-160">Tables which implemented the vardecimal storage format in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] will retain that setting when upgraded.</span></span> <span data-ttu-id="41c3a-161">可以向具有 vardecimal 存储格式的表应用行压缩。</span><span class="sxs-lookup"><span data-stu-id="41c3a-161">You can apply row compression to a table that has the vardecimal storage format.</span></span> <span data-ttu-id="41c3a-162">但是，因为行压缩是 vardecimal 存储格式的超集，所以不必保留 vardecimal 存储格式。</span><span class="sxs-lookup"><span data-stu-id="41c3a-162">However, because row compression is a superset of the vardecimal storage format, there is no reason to retain the vardecimal storage format.</span></span> <span data-ttu-id="41c3a-163">将 vardecimal 存储格式与行压缩一起使用时，十进制值不会进一步压缩。</span><span class="sxs-lookup"><span data-stu-id="41c3a-163">Decimal values gain no additional compression when you combine the vardecimal storage format with row compression.</span></span> <span data-ttu-id="41c3a-164">可以向具有 vardecimal 存储格式的表应用页压缩；但是，vardecimal 存储格式列可能不会实现进一步的压缩。</span><span class="sxs-lookup"><span data-stu-id="41c3a-164">You can apply page compression to a table that has the vardecimal storage format; however, the vardecimal storage format columns probably will not achieve additional compression.</span></span>  
  
    > [!NOTE]  
    >  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="41c3a-165">支持 vardecimal 存储格式；但是，由于行级压缩可实现同样的目标，因此不推荐使用 vardecimal 存储格式。</span><span class="sxs-lookup"><span data-stu-id="41c3a-165">supports the vardecimal storage format; however, because row-level compression achieves the same goals, the vardecimal storage format is deprecated.</span></span> [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
## <a name="using-columnstore-and-columnstore-archive-compression"></a><span data-ttu-id="41c3a-166">使用列存储和列存储存档压缩</span><span class="sxs-lookup"><span data-stu-id="41c3a-166">Using Columnstore and Columnstore Archive Compression</span></span>  
  
||  
|-|  
|<span data-ttu-id="41c3a-167">**适用范围**： [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] （[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 到 [当前版本](https://go.microsoft.com/fwlink/p/?LinkId=299658)）。</span><span class="sxs-lookup"><span data-stu-id="41c3a-167">**Applies to**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] through [current version](https://go.microsoft.com/fwlink/p/?LinkId=299658)).</span></span>|  
  
### <a name="basics"></a><span data-ttu-id="41c3a-168">基础</span><span class="sxs-lookup"><span data-stu-id="41c3a-168">Basics</span></span>  
 <span data-ttu-id="41c3a-169">列存储表和索引始终使用列存储压缩进行存储。</span><span class="sxs-lookup"><span data-stu-id="41c3a-169">Columnstore tables and indexes are always stored with columnstore compression.</span></span> <span data-ttu-id="41c3a-170">您可以通过配置称作存档压缩的附加压缩，进一步减少列存储数据的大小。</span><span class="sxs-lookup"><span data-stu-id="41c3a-170">You can further reduce the size of columnstore data by configuring an additional compression called archival compression.</span></span>  <span data-ttu-id="41c3a-171">为了执行存档压缩， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 将对数据运行 Microsoft XPRESS 压缩算法。</span><span class="sxs-lookup"><span data-stu-id="41c3a-171">To perform archival compression, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] runs the Microsoft XPRESS compression algorithm on the data.</span></span> <span data-ttu-id="41c3a-172">通过使用以下数据压缩类型添加或删除存档压缩：</span><span class="sxs-lookup"><span data-stu-id="41c3a-172">Add or remove archival compression by using the following data compression types:</span></span>  
  
-   <span data-ttu-id="41c3a-173">使用 `COLUMNSTORE_ARCHIVE` 数据压缩可使用存档压缩来压缩列存储数据。</span><span class="sxs-lookup"><span data-stu-id="41c3a-173">Use `COLUMNSTORE_ARCHIVE` data compression to compress columnstore data with archival compression.</span></span>  
  
-   <span data-ttu-id="41c3a-174">使用 **COLUMNSTORE** 数据压缩可对存档压缩执行解压缩。</span><span class="sxs-lookup"><span data-stu-id="41c3a-174">Use **COLUMNSTORE** data compression to decompress archival compression.</span></span> <span data-ttu-id="41c3a-175">这样生成的数据将继续使用列存储压缩进行压缩。</span><span class="sxs-lookup"><span data-stu-id="41c3a-175">This resulting data will continue to be compressed with columnstore compression.</span></span>  
  
 <span data-ttu-id="41c3a-176">若要添加存档压缩，请使用具有 REBUILD 选项且 DATA COMPRESSION = COLUMNSTORE 的 [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql) 或者 [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql) 。</span><span class="sxs-lookup"><span data-stu-id="41c3a-176">To add archival compression, use [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql) or [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql) with the REBUILD option and DATA COMPRESSION = COLUMNSTORE.</span></span>  
  
 <span data-ttu-id="41c3a-177">示例：</span><span class="sxs-lookup"><span data-stu-id="41c3a-177">Examples:</span></span>  
  
```  
ALTER TABLE ColumnstoreTable1   
REBUILD PARTITION = 1 WITH (DATA_COMPRESSION =  COLUMNSTORE_ARCHIVE) ;  
  
ALTER TABLE ColumnstoreTable1   
REBUILD PARTITION = ALL WITH (DATA_COMPRESSION =  COLUMNSTORE_ARCHIVE) ;  
  
ALTER TABLE ColumnstoreTable1   
REBUILD PARTITION = ALL WITH (DATA_COMPRESSION =  COLUMNSTORE_ARCHIVE ON PARTITIONS (2,4)) ;  
  
```  
  
 <span data-ttu-id="41c3a-178">若要删除存档压缩并且将数据还原为列存储压缩，请使用带有 REBUILD 选项并且 DATA COMPRESSION = COLUMNSTORE 的 [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql) 或者 [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql) 。</span><span class="sxs-lookup"><span data-stu-id="41c3a-178">To remove archival compression and restore the data to columnstore compression, use [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql) or [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql) with the REBUILD option and DATA COMPRESSION = COLUMNSTORE.</span></span>  
  
 <span data-ttu-id="41c3a-179">示例：</span><span class="sxs-lookup"><span data-stu-id="41c3a-179">Examples:</span></span>  
  
```  
ALTER TABLE ColumnstoreTable1   
REBUILD PARTITION = 1 WITH (DATA_COMPRESSION =  COLUMNSTORE) ;  
  
ALTER TABLE ColumnstoreTable1   
REBUILD PARTITION = ALL WITH (DATA_COMPRESSION =  COLUMNSTORE) ;  
  
ALTER TABLE ColumnstoreTable1   
REBUILD PARTITION = ALL WITH (DATA_COMPRESSION =  COLUMNSTORE ON PARTITIONS (2,4) ) ;  
  
```  
  
 <span data-ttu-id="41c3a-180">下一示例将数据压缩设置为对于某些分区是列存储，对于其他分区是列存储存档。</span><span class="sxs-lookup"><span data-stu-id="41c3a-180">This next example sets the data compression to columnstore on some partitions, and to columnstore archival on other partitions.</span></span>  
  
```  
ALTER TABLE ColumnstoreTable1   
REBUILD PARTITION = ALL WITH (  
    DATA_COMPRESSION =  COLUMNSTORE ON PARTITIONS (4,5),  
    DATA COMPRESSION = COLUMNSTORE_ARCHIVE ON PARTITIONS (1,2,3)  
) ;  
```  
  
### <a name="performance"></a><span data-ttu-id="41c3a-181">性能</span><span class="sxs-lookup"><span data-stu-id="41c3a-181">Performance</span></span>  
 <span data-ttu-id="41c3a-182">使用存档压缩对列存储索引进行压缩将导致索引执行速度慢于未进行存档压缩的列存储索引。</span><span class="sxs-lookup"><span data-stu-id="41c3a-182">Compressing columnstore indexes with archival compression will cause the index to perform slower than columnstore indexes that do not have the archival compression.</span></span>  <span data-ttu-id="41c3a-183">仅在您能够付出额外的时间和 CPU 资源来压缩和检索数据时，才使用存档压缩。</span><span class="sxs-lookup"><span data-stu-id="41c3a-183">Use archival compression only when you can afford to use extra time and CPU resources to compress and retrieve the data.</span></span>  
  
 <span data-ttu-id="41c3a-184">尽管执行速度放慢，但好处是用于不频繁访问的数据的存储缩小了。</span><span class="sxs-lookup"><span data-stu-id="41c3a-184">The benefit of slower performance is reduced storage which is useful for data that is not frequently accessed.</span></span> <span data-ttu-id="41c3a-185">例如，如果您对每个月的数据都具有一个分区，并且您的大多数活动是针对最近月份的，则可以将较早月份的数据存档以便降低存储要求。</span><span class="sxs-lookup"><span data-stu-id="41c3a-185">For example, if you have a partition for each month of data, and most of your activity is for the most recent months, you could archive older months to reduce the storage requirements.</span></span>  
  
### <a name="metadata"></a><span data-ttu-id="41c3a-186">元数据</span><span class="sxs-lookup"><span data-stu-id="41c3a-186">Metadata</span></span>  
 <span data-ttu-id="41c3a-187">下面的系统视图包含有关聚集索引的数据压缩的信息：</span><span class="sxs-lookup"><span data-stu-id="41c3a-187">The following system views contain information about data compression for clustered indexes:</span></span>  
  
-   <span data-ttu-id="41c3a-188">[sys. 索引 &#40;transact-sql&#41;](/sql/relational-databases/system-catalog-views/sys-indexes-transact-sql) - `type` 和 `type_desc` 列包含聚集列存储和非聚集列存储。</span><span class="sxs-lookup"><span data-stu-id="41c3a-188">[sys.indexes &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-indexes-transact-sql) - The `type` and `type_desc` columns include CLUSTERED COLUMNSTORE and NONCLUSTERED COLUMNSTORE.</span></span>  
  
-   <span data-ttu-id="41c3a-189">[sys.databases &#40;transact-sql&#41;](/sql/relational-databases/system-catalog-views/sys-partitions-transact-sql) - `data_compression` 和 `data_compression_desc` 列包含列存储和 COLUMNSTORE_ARCHIVE。</span><span class="sxs-lookup"><span data-stu-id="41c3a-189">[sys.partitions &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-partitions-transact-sql) - The `data_compression` and `data_compression_desc` columns include COLUMNSTORE and COLUMNSTORE_ARCHIVE.</span></span>  
  
 <span data-ttu-id="41c3a-190">[sp_estimate_data_compression_savings (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-estimate-data-compression-savings-transact-sql) 过程不会应用在列存储索引中。</span><span class="sxs-lookup"><span data-stu-id="41c3a-190">The procedure [sp_estimate_data_compression_savings &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-estimate-data-compression-savings-transact-sql) does not apply to columnstore indexes.</span></span>  
  
## <a name="how-compression-affects-partitioned-tables-and-indexes"></a><span data-ttu-id="41c3a-191">压缩对已分区表和已分区索引的影响</span><span class="sxs-lookup"><span data-stu-id="41c3a-191">How Compression Affects Partitioned Tables and Indexes</span></span>  
 <span data-ttu-id="41c3a-192">如果对已分区表和已分区索引使用数据压缩，则应注意以下事项：</span><span class="sxs-lookup"><span data-stu-id="41c3a-192">When you use data compression with partitioned tables and indexes, be aware of the following considerations:</span></span>  
  
-   <span data-ttu-id="41c3a-193">如果使用 ALTER PARTITION 语句拆分分区，则两个分区均继承原始分区的数据压缩属性。</span><span class="sxs-lookup"><span data-stu-id="41c3a-193">When partitions are split by using the ALTER PARTITION statement, both partitions inherit the data compression attribute of the original partition.</span></span>  
  
-   <span data-ttu-id="41c3a-194">合并两个分区时，生成的分区将继承目标分区的数据压缩属性。</span><span class="sxs-lookup"><span data-stu-id="41c3a-194">When two partitions are merged, the resultant partition inherits the data compression attribute of the destination partition.</span></span>  
  
-   <span data-ttu-id="41c3a-195">若要切换分区，该分区的数据压缩属性必须与表的压缩属性匹配。</span><span class="sxs-lookup"><span data-stu-id="41c3a-195">To switch a partition, the data compression property of the partition must match the compression property of the table.</span></span>  
  
-   <span data-ttu-id="41c3a-196">可以使用两种语法变体来修改已分区表或已分区索引的压缩：</span><span class="sxs-lookup"><span data-stu-id="41c3a-196">There are two syntax variations that you can use to modify the compression of a partitioned table or index:</span></span>  
  
    -   <span data-ttu-id="41c3a-197">下面的语法仅重新生成被引用分区：</span><span class="sxs-lookup"><span data-stu-id="41c3a-197">The following syntax rebuilds only the referenced partition:</span></span>  
  
        ```  
        ALTER TABLE <table_name>   
        REBUILD PARTITION = 1 WITH (DATA_COMPRESSION =  <option>)  
        ```  
  
    -   <span data-ttu-id="41c3a-198">下面的语法通过对未引用的任何分区使用现有压缩设置来重新生成整个表：</span><span class="sxs-lookup"><span data-stu-id="41c3a-198">The following syntax rebuilds the whole table by using the existing compression setting for any partitions that are not referenced:</span></span>  
  
        ```  
        ALTER TABLE <table_name>   
        REBUILD PARTITION = ALL   
        WITH (DATA_COMPRESSION = PAGE ON PARTITIONS(<range>),  
        ... )  
        ```  
  
     <span data-ttu-id="41c3a-199">已分区索引使用 ALTER INDEX 遵循同样的原则。</span><span class="sxs-lookup"><span data-stu-id="41c3a-199">Partitioned indexes follow the same principle using ALTER INDEX.</span></span>  
  
-   <span data-ttu-id="41c3a-200">删除聚集索引时，除非修改了分区方案，否则相应的堆分区将保留其数据压缩设置。</span><span class="sxs-lookup"><span data-stu-id="41c3a-200">When a clustered index is dropped, the corresponding heap partitions retain their data compression setting unless the partitioning scheme is modified.</span></span> <span data-ttu-id="41c3a-201">如果分区方案已更改，则所有分区都将重新生成为未压缩状态。</span><span class="sxs-lookup"><span data-stu-id="41c3a-201">If the partitioning scheme is changed, all partitions are rebuilt to an uncompressed state.</span></span> <span data-ttu-id="41c3a-202">若要删除聚集索引并更改分区方案，需要执行下列步骤：</span><span class="sxs-lookup"><span data-stu-id="41c3a-202">To drop a clustered index and change the partitioning scheme requires the following steps:</span></span>  
  
     1. <span data-ttu-id="41c3a-203">删除聚集索引。</span><span class="sxs-lookup"><span data-stu-id="41c3a-203">Drop the clustered index.</span></span>  
  
     2. <span data-ttu-id="41c3a-204">使用指定压缩选项的 ALTER TABLE ...REBUILD ... 选项来修改表。</span><span class="sxs-lookup"><span data-stu-id="41c3a-204">Modify the table by using the ALTER TABLE ... REBUILD ... option that specifies the compression option.</span></span>  
  
     <span data-ttu-id="41c3a-205">若要删除聚集索引，脱机操作的执行速度很快，因为只删除较高级别的聚集索引。</span><span class="sxs-lookup"><span data-stu-id="41c3a-205">To drop a clustered index OFFLINE is a very fast operation, because only the upper levels of clustered indexes are removed.</span></span> <span data-ttu-id="41c3a-206">如果联机删除聚集索引，则 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 必须重新生成堆两次，一次针对步骤 1，一次针对步骤 2。</span><span class="sxs-lookup"><span data-stu-id="41c3a-206">When a clustered index is dropped ONLINE, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] must rebuild the heap two times, once for step 1 and once for step 2.</span></span>  
  
## <a name="how-compression-affects-replication"></a><span data-ttu-id="41c3a-207">压缩对复制的影响</span><span class="sxs-lookup"><span data-stu-id="41c3a-207">How Compression Affects Replication</span></span>  
 <span data-ttu-id="41c3a-208">如果将数据压缩与复制一起使用，则应注意以下事项：</span><span class="sxs-lookup"><span data-stu-id="41c3a-208">When you are using data compression with replication, be aware of the following considerations:</span></span>  
  
-   <span data-ttu-id="41c3a-209">当快照代理生成初始架构脚本时，新架构将对表及其索引使用相同的压缩设置。</span><span class="sxs-lookup"><span data-stu-id="41c3a-209">When the Snapshot Agent generates the initial schema script, the new schema will use the same compression settings for both the table and its indexes.</span></span> <span data-ttu-id="41c3a-210">不能仅对表启用压缩，而不对索引启用压缩。</span><span class="sxs-lookup"><span data-stu-id="41c3a-210">Compression cannot be enabled on just the table and not the index.</span></span>  
  
-   <span data-ttu-id="41c3a-211">对于事务复制，项目架构选项决定了必须对哪些依赖对象和属性编写脚本。</span><span class="sxs-lookup"><span data-stu-id="41c3a-211">For transactional replication the article schema option determines what dependent objects and properties have to be scripted.</span></span> <span data-ttu-id="41c3a-212">有关详细信息，请参阅 [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="41c3a-212">For more information, see [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql).</span></span>  
  
     <span data-ttu-id="41c3a-213">分发代理在应用脚本时，不对下级订阅服务器进行检查。</span><span class="sxs-lookup"><span data-stu-id="41c3a-213">The Distribution Agent does not check for down-level Subscribers when it applies scripts.</span></span> <span data-ttu-id="41c3a-214">如果选择了压缩的复制，则在下级订阅服务器上创建表将会失败。</span><span class="sxs-lookup"><span data-stu-id="41c3a-214">If the replication of compression is selected, creating the table on down-level Subscribers will fail.</span></span> <span data-ttu-id="41c3a-215">在混合拓扑中，不启用压缩的复制。</span><span class="sxs-lookup"><span data-stu-id="41c3a-215">In the case of a mixed topology, do not enable the replication of compression.</span></span>  
  
-   <span data-ttu-id="41c3a-216">对于合并复制，发布兼容级别优先于架构选项，并决定了将编写脚本的架构对象。</span><span class="sxs-lookup"><span data-stu-id="41c3a-216">For merge replication, publication compatibility level overrides the schema options and determines the schema objects that will be scripted.</span></span>  
  
     <span data-ttu-id="41c3a-217">在混合拓扑中，如果不是必须支持新的压缩选项，则发布兼容级别应设置为下级订阅服务器版本。</span><span class="sxs-lookup"><span data-stu-id="41c3a-217">In the case of a mixed topology, if it is not required to support the new compression options, the publication compatibility level should be set to the down-level Subscriber version.</span></span> <span data-ttu-id="41c3a-218">否则，应在创建表后在订阅服务器上压缩表。</span><span class="sxs-lookup"><span data-stu-id="41c3a-218">If it is required, compress tables on the Subscriber after they have been created.</span></span>  
  
 <span data-ttu-id="41c3a-219">下表列出了在复制期间控制压缩的复制设置。</span><span class="sxs-lookup"><span data-stu-id="41c3a-219">The following table shows replication settings that control compression during replication.</span></span>  
  
|<span data-ttu-id="41c3a-220">用户意图</span><span class="sxs-lookup"><span data-stu-id="41c3a-220">User intent</span></span>|<span data-ttu-id="41c3a-221">为表或索引复制分区方案</span><span class="sxs-lookup"><span data-stu-id="41c3a-221">Replicate partition scheme for a table or index</span></span>|<span data-ttu-id="41c3a-222">复制压缩设置</span><span class="sxs-lookup"><span data-stu-id="41c3a-222">Replicate compression settings</span></span>|<span data-ttu-id="41c3a-223">脚本编写行为</span><span class="sxs-lookup"><span data-stu-id="41c3a-223">Scripting behavior</span></span>|  
|-----------------|-----------------------------------------------------|------------------------------------|------------------------|  
|<span data-ttu-id="41c3a-224">复制分区方案并在该分区上的订阅服务器上启用压缩。</span><span class="sxs-lookup"><span data-stu-id="41c3a-224">To replicate the partition scheme and enable compression on the Subscriber on the partition.</span></span>|<span data-ttu-id="41c3a-225">True</span><span class="sxs-lookup"><span data-stu-id="41c3a-225">True</span></span>|<span data-ttu-id="41c3a-226">True</span><span class="sxs-lookup"><span data-stu-id="41c3a-226">True</span></span>|<span data-ttu-id="41c3a-227">对分区方案和压缩设置均编写脚本。</span><span class="sxs-lookup"><span data-stu-id="41c3a-227">Scripts both the partition scheme and the compression settings.</span></span>|  
|<span data-ttu-id="41c3a-228">复制分区方案，但不压缩订阅服务器上的数据。</span><span class="sxs-lookup"><span data-stu-id="41c3a-228">To replicate the partition scheme but not compress the data on the Subscriber.</span></span>|<span data-ttu-id="41c3a-229">正确</span><span class="sxs-lookup"><span data-stu-id="41c3a-229">True</span></span>|<span data-ttu-id="41c3a-230">错误</span><span class="sxs-lookup"><span data-stu-id="41c3a-230">False</span></span>|<span data-ttu-id="41c3a-231">对分区方案编写脚本，但不对分区的压缩设置编写脚本。</span><span class="sxs-lookup"><span data-stu-id="41c3a-231">Scripts out the partition scheme but not the compression settings for the partition.</span></span>|  
|<span data-ttu-id="41c3a-232">不复制分区方案，也不压缩订阅服务器上的数据。</span><span class="sxs-lookup"><span data-stu-id="41c3a-232">To not replicate the partition scheme and not compress the data on the Subscriber.</span></span>|<span data-ttu-id="41c3a-233">False</span><span class="sxs-lookup"><span data-stu-id="41c3a-233">False</span></span>|<span data-ttu-id="41c3a-234">False</span><span class="sxs-lookup"><span data-stu-id="41c3a-234">False</span></span>|<span data-ttu-id="41c3a-235">不对分区和压缩设置编写脚本。</span><span class="sxs-lookup"><span data-stu-id="41c3a-235">Does not script partition or compression settings.</span></span>|  
|<span data-ttu-id="41c3a-236">如果发布服务器上的所有分区均压缩，则压缩订阅服务器上的表，但不复制分区方案。</span><span class="sxs-lookup"><span data-stu-id="41c3a-236">To compress the table on the Subscriber if all the partitions are compressed on the Publisher, but not replicate the partition scheme.</span></span>|<span data-ttu-id="41c3a-237">错误</span><span class="sxs-lookup"><span data-stu-id="41c3a-237">False</span></span>|<span data-ttu-id="41c3a-238">True</span><span class="sxs-lookup"><span data-stu-id="41c3a-238">True</span></span>|<span data-ttu-id="41c3a-239">检查是否对所有分区均启用了压缩。</span><span class="sxs-lookup"><span data-stu-id="41c3a-239">Checks if all the partitions are enabled for compression.</span></span><br /><br /> <span data-ttu-id="41c3a-240">在表级别对压缩编写脚本。</span><span class="sxs-lookup"><span data-stu-id="41c3a-240">Scripts out compression at the table level.</span></span>|  
  
## <a name="how-compression-affects-other-sql-server-components"></a><span data-ttu-id="41c3a-241">压缩对其他 SQL Server 组件的影响</span><span class="sxs-lookup"><span data-stu-id="41c3a-241">How Compression Affects Other SQL Server Components</span></span>  
 <span data-ttu-id="41c3a-242">压缩发生在存储引擎中，数据以未压缩状态呈现给 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的其他大部分组件。</span><span class="sxs-lookup"><span data-stu-id="41c3a-242">Compression occurs in the storage engine and the data is presented to most of the other components of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in an uncompressed state.</span></span> <span data-ttu-id="41c3a-243">这决定了其他组件上的压缩效果仅限于以下方面：</span><span class="sxs-lookup"><span data-stu-id="41c3a-243">This limits the effects of compression on the other components to the following:</span></span>  
  
-   <span data-ttu-id="41c3a-244">大容量导入和导出操作</span><span class="sxs-lookup"><span data-stu-id="41c3a-244">Bulk import and export operations</span></span>  
  
     <span data-ttu-id="41c3a-245">导出数据时，即使采用本机格式，数据也以未压缩的行格式输出。</span><span class="sxs-lookup"><span data-stu-id="41c3a-245">When data is exported, even in native format, the data is output in the uncompressed row format.</span></span> <span data-ttu-id="41c3a-246">这会导致导出的数据文件的大小比源数据要大得多。</span><span class="sxs-lookup"><span data-stu-id="41c3a-246">This can cause the size of exported data file to be significantly larger than the source data.</span></span>  
  
     <span data-ttu-id="41c3a-247">导入数据时，如果已对目标表启用压缩，则存储引擎会将数据转换为压缩的行格式。</span><span class="sxs-lookup"><span data-stu-id="41c3a-247">When data is imported, if the target table has been enabled for compression, the data is converted by the storage engine into compressed row format.</span></span> <span data-ttu-id="41c3a-248">这样所使用的 CPU 资源会比将数据导入未压缩表时使用的 CPU 资源多。</span><span class="sxs-lookup"><span data-stu-id="41c3a-248">This can cause increased CPU usage compared to when data is imported into an uncompressed table.</span></span>  
  
     <span data-ttu-id="41c3a-249">如果以大容量方式将数据导入具有页压缩设置的堆，则在插入数据时，大容量导入操作会尝试使用页压缩来压缩数据。</span><span class="sxs-lookup"><span data-stu-id="41c3a-249">When data is bulk imported into a heap with page compression, the bulk import operation will try to compress the data with page compression when the data is inserted.</span></span>  
  
-   <span data-ttu-id="41c3a-250">压缩对备份和还原没有影响。</span><span class="sxs-lookup"><span data-stu-id="41c3a-250">Compression does not affect backup and restore.</span></span>  
  
-   <span data-ttu-id="41c3a-251">压缩对日志传送没有影响。</span><span class="sxs-lookup"><span data-stu-id="41c3a-251">Compression does not affect log shipping.</span></span>  
  
-   <span data-ttu-id="41c3a-252">数据压缩与稀疏列不兼容。</span><span class="sxs-lookup"><span data-stu-id="41c3a-252">Data compression is incompatible with sparse columns.</span></span> <span data-ttu-id="41c3a-253">因此，无法压缩包含稀疏列的表，也不能将稀疏列添加到压缩表。</span><span class="sxs-lookup"><span data-stu-id="41c3a-253">Therefore, tables containing sparse columns cannot be compressed nor can sparse columns be added to a compressed table.</span></span>  
  
-   <span data-ttu-id="41c3a-254">启用压缩可以导致查询计划更改，因为数据是用不同的页数和每页不同的行数存储的。</span><span class="sxs-lookup"><span data-stu-id="41c3a-254">Enabling compression can cause query plans to change because the data is stored using a different number of pages and number of rows per page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41c3a-255">另请参阅</span><span class="sxs-lookup"><span data-stu-id="41c3a-255">See Also</span></span>  
 <span data-ttu-id="41c3a-256">[行压缩的实现](row-compression-implementation.md) </span><span class="sxs-lookup"><span data-stu-id="41c3a-256">[Row Compression Implementation](row-compression-implementation.md) </span></span>  
 <span data-ttu-id="41c3a-257">[页压缩的实现](page-compression-implementation.md) </span><span class="sxs-lookup"><span data-stu-id="41c3a-257">[Page Compression Implementation](page-compression-implementation.md) </span></span>  
 <span data-ttu-id="41c3a-258">[Unicode 压缩的实现](unicode-compression-implementation.md) </span><span class="sxs-lookup"><span data-stu-id="41c3a-258">[Unicode Compression Implementation](unicode-compression-implementation.md) </span></span>  
 <span data-ttu-id="41c3a-259">[CREATE PARTITION SCHEME (Transact-SQL)](/sql/t-sql/statements/create-partition-scheme-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="41c3a-259">[CREATE PARTITION SCHEME &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-partition-scheme-transact-sql) </span></span>  
 <span data-ttu-id="41c3a-260">[CREATE PARTITION FUNCTION (Transact-SQL)](/sql/t-sql/statements/create-partition-function-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="41c3a-260">[CREATE PARTITION FUNCTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-partition-function-transact-sql) </span></span>  
 <span data-ttu-id="41c3a-261">[CREATE TABLE (Transact-SQL)](/sql/t-sql/statements/create-table-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="41c3a-261">[CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql) </span></span>  
 <span data-ttu-id="41c3a-262">[ALTER TABLE (Transact-SQL)](/sql/t-sql/statements/alter-table-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="41c3a-262">[ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql) </span></span>  
 <span data-ttu-id="41c3a-263">[CREATE INDEX (Transact-SQL)](/sql/t-sql/statements/create-index-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="41c3a-263">[CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql) </span></span>  
 [<span data-ttu-id="41c3a-264">ALTER INDEX (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="41c3a-264">ALTER INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-index-transact-sql)  
  
  
