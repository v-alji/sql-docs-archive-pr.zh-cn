---
title: 比较用于存储 Blob 的选项 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.technology: filestream
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 6038697b-36a9-49e8-a02a-2ad9e2e60e5a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: c7f0d15950a8663852c84c4edbb8177e918a8895
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589721"
---
# <a name="compare-options-for-storing-blobs-sql-server"></a><span data-ttu-id="8cf52-102">比较用于存储 Blob 的选项 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="8cf52-102">Compare Options for Storing Blobs (SQL Server)</span></span>
  <span data-ttu-id="8cf52-103">讨论和比较用于在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中存储文件和文档的选项。</span><span class="sxs-lookup"><span data-stu-id="8cf52-103">Discusses and compares the options that are available for storing files and documents in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
##  <a name="storing-files-in-the-database---benefits-and-expectations"></a><a name="Expectations"></a> <span data-ttu-id="8cf52-104">在数据库中存储文件 - 好处和期望</span><span class="sxs-lookup"><span data-stu-id="8cf52-104">Storing Files in the Database - Benefits and Expectations</span></span>  
 <span data-ttu-id="8cf52-105">很大比例的企业数据本质上是非结构化的，通常作为文件和文档存储在文件系统中。</span><span class="sxs-lookup"><span data-stu-id="8cf52-105">A large percentage of enterprise data is unstructured in nature, and is typically stored as files and documents in file systems.</span></span> <span data-ttu-id="8cf52-106">大多数此类数据由应用程序生成、管理和使用，应用程序通过 Windows API 访问这些文件。</span><span class="sxs-lookup"><span data-stu-id="8cf52-106">Most of this data is produced, managed and consumed by applications that access the files through Windows APIs.</span></span> <span data-ttu-id="8cf52-107">企业通常将此类数据保存在文件系统中，同时将文件的相关元数据存储在关系数据库中。</span><span class="sxs-lookup"><span data-stu-id="8cf52-107">Enterprises typically keep this data in the file system, while storing the related metadata for the files in a relational database.</span></span>  
  
 <span data-ttu-id="8cf52-108">将非结构化数据集成到关系数据库可提供很多好处。</span><span class="sxs-lookup"><span data-stu-id="8cf52-108">Integrating unstructured data into the relational database provides significant benefits.</span></span> <span data-ttu-id="8cf52-109">其中包括：</span><span class="sxs-lookup"><span data-stu-id="8cf52-109">These benefits include the following:</span></span>  
  
-   <span data-ttu-id="8cf52-110">集成的存储和数据管理功能，例如备份。</span><span class="sxs-lookup"><span data-stu-id="8cf52-110">Integrated storage and data management capabilities such as backup.</span></span>  
  
-   <span data-ttu-id="8cf52-111">一些集成服务，如针对数据和元数据的全文搜索和语义搜索。</span><span class="sxs-lookup"><span data-stu-id="8cf52-111">Integrated services such as full-text search and semantic search over data and metadata.</span></span>  
  
-   <span data-ttu-id="8cf52-112">易于对非结构化数据的管理和策略管理。</span><span class="sxs-lookup"><span data-stu-id="8cf52-112">Ease of administration and policy management over the unstructured data.</span></span>  
  
 <span data-ttu-id="8cf52-113">但对于大部分企业而言，难以将这种非结构化数据存储在关系数据库中。</span><span class="sxs-lookup"><span data-stu-id="8cf52-113">For the most part, however, it has not been convenient to store unstructured data in a relational database.</span></span> <span data-ttu-id="8cf52-114">以前不能在关系型系统上运行基于 Windows 的现有应用程序。</span><span class="sxs-lookup"><span data-stu-id="8cf52-114">It has not previously been possible to run existing Windows-based applications on top of relational systems.</span></span> <span data-ttu-id="8cf52-115">重写现有应用程序（如 Microsoft Word 或 Adobe Reader）以便在关系数据库 API 上运行并不现实。</span><span class="sxs-lookup"><span data-stu-id="8cf52-115">It is not practical to rewrite established applications (such as Microsoft Word or Adobe Reader) to run on top relational database APIs.</span></span> <span data-ttu-id="8cf52-116">这些应用程序只是希望能够通过 Windows API 访问数据。</span><span class="sxs-lookup"><span data-stu-id="8cf52-116">These applications simply expect the data to be accessible through Windows APIs.</span></span> <span data-ttu-id="8cf52-117">换而言之，要求做到以下几点：</span><span class="sxs-lookup"><span data-stu-id="8cf52-117">In other words, the expectations include the following:</span></span>  
  
-   <span data-ttu-id="8cf52-118">Windows 应用程序并不识别数据库事务，也不需要它们。</span><span class="sxs-lookup"><span data-stu-id="8cf52-118">Windows applications are not aware of database transactions and do not require them.</span></span>  
  
-   <span data-ttu-id="8cf52-119">Windows 应用程序要求与文件和目录数据的文件系统 API 兼容。</span><span class="sxs-lookup"><span data-stu-id="8cf52-119">Windows applications require compatibility with file system APIs for file and directory data.</span></span>  
  
##  <a name="filestream"></a><a name="Filestream"></a> <span data-ttu-id="8cf52-120">FILESTREAM</span><span class="sxs-lookup"><span data-stu-id="8cf52-120">FILESTREAM</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="8cf52-121">已有 FILESTREAM 功能，它为作为文件存储在文件系统中的非结构化数据提供了高效的存储、管理和流式处理方法。</span><span class="sxs-lookup"><span data-stu-id="8cf52-121">already has the FILESTREAM feature, which provides efficient storage, management and streaming of unstructured data stored as files on the file system.</span></span> <span data-ttu-id="8cf52-122">但是，FILESTREAM 解决方案要求自定义的编程，并且不满足上文所述的完全 Windows 应用程序兼容性的要求。</span><span class="sxs-lookup"><span data-stu-id="8cf52-122">However, a FILESTREAM solution requires custom programming, and does not satisfy the requirement for full Windows application compatibility described above.</span></span>  
  
##  <a name="filetables"></a><a name="FileTables"></a> <span data-ttu-id="8cf52-123">FileTable</span><span class="sxs-lookup"><span data-stu-id="8cf52-123">FileTables</span></span>  
 <span data-ttu-id="8cf52-124">FileTable 功能以现有的 FILESTREAM 功能为基础，使企业客户只要满足对基于文件的数据的非事务性访问和 Windows 应用程序兼容性要求，就可以在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库中存储非结构化文件数据和目录层次结构。</span><span class="sxs-lookup"><span data-stu-id="8cf52-124">The FileTable feature builds on top of existing FILESTREAM capabilities to enable enterprise customers to store unstructured file data and directory hierarchies in a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database, by addressing the requirements for non-transactional access and Windows application compatibility for file-based data.</span></span>  
  
##  <a name="comparing-filestream-and-filetable"></a><a name="CompareFileTable"></a> <span data-ttu-id="8cf52-125">FILESTREAM 和 FileTable 的比较</span><span class="sxs-lookup"><span data-stu-id="8cf52-125">Comparing FILESTREAM and FileTable</span></span>  
  
|<span data-ttu-id="8cf52-126">Feature</span><span class="sxs-lookup"><span data-stu-id="8cf52-126">Feature</span></span>|<span data-ttu-id="8cf52-127">文件服务器和数据库解决方案</span><span class="sxs-lookup"><span data-stu-id="8cf52-127">File Server and Database Solution</span></span>|<span data-ttu-id="8cf52-128">FILESTREAM 解决方案</span><span class="sxs-lookup"><span data-stu-id="8cf52-128">FILESTREAM Solution</span></span>|<span data-ttu-id="8cf52-129">FileTable 解决方案</span><span class="sxs-lookup"><span data-stu-id="8cf52-129">FileTable Solution</span></span>|  
|-------------|---------------------------------------|-------------------------|------------------------|  
|<span data-ttu-id="8cf52-130">**用于管理任务的单个存储区**</span><span class="sxs-lookup"><span data-stu-id="8cf52-130">**Single story for management tasks**</span></span>|<span data-ttu-id="8cf52-131">否</span><span class="sxs-lookup"><span data-stu-id="8cf52-131">No</span></span>|<span data-ttu-id="8cf52-132">是</span><span class="sxs-lookup"><span data-stu-id="8cf52-132">Yes</span></span>|<span data-ttu-id="8cf52-133">**是**</span><span class="sxs-lookup"><span data-stu-id="8cf52-133">**Yes**</span></span>|  
|<span data-ttu-id="8cf52-134">**单组服务**：搜索、报告、查询等</span><span class="sxs-lookup"><span data-stu-id="8cf52-134">**Single set of services**: search, reporting, querying, and so forth</span></span>|<span data-ttu-id="8cf52-135">否</span><span class="sxs-lookup"><span data-stu-id="8cf52-135">No</span></span>|<span data-ttu-id="8cf52-136">是</span><span class="sxs-lookup"><span data-stu-id="8cf52-136">Yes</span></span>|<span data-ttu-id="8cf52-137">**是**</span><span class="sxs-lookup"><span data-stu-id="8cf52-137">**Yes**</span></span>|  
|<span data-ttu-id="8cf52-138">**集成的安全模型**</span><span class="sxs-lookup"><span data-stu-id="8cf52-138">**Integrated security model**</span></span>|<span data-ttu-id="8cf52-139">否</span><span class="sxs-lookup"><span data-stu-id="8cf52-139">No</span></span>|<span data-ttu-id="8cf52-140">是</span><span class="sxs-lookup"><span data-stu-id="8cf52-140">Yes</span></span>|<span data-ttu-id="8cf52-141">**是**</span><span class="sxs-lookup"><span data-stu-id="8cf52-141">**Yes**</span></span>|  
|<span data-ttu-id="8cf52-142">**FILESTREAM 数据的就地更新**</span><span class="sxs-lookup"><span data-stu-id="8cf52-142">**In-place updates of FILESTREAM data**</span></span>|<span data-ttu-id="8cf52-143">是</span><span class="sxs-lookup"><span data-stu-id="8cf52-143">Yes</span></span>|<span data-ttu-id="8cf52-144">否</span><span class="sxs-lookup"><span data-stu-id="8cf52-144">No</span></span>|<span data-ttu-id="8cf52-145">**是**</span><span class="sxs-lookup"><span data-stu-id="8cf52-145">**Yes**</span></span>|  
|<span data-ttu-id="8cf52-146">**在数据库中维护文件和目录层次结构**</span><span class="sxs-lookup"><span data-stu-id="8cf52-146">**File and directory hierarchy maintained in the database**</span></span>|<span data-ttu-id="8cf52-147">否</span><span class="sxs-lookup"><span data-stu-id="8cf52-147">No</span></span>|<span data-ttu-id="8cf52-148">否</span><span class="sxs-lookup"><span data-stu-id="8cf52-148">No</span></span>|<span data-ttu-id="8cf52-149">**是**</span><span class="sxs-lookup"><span data-stu-id="8cf52-149">**Yes**</span></span>|  
|<span data-ttu-id="8cf52-150">**Windows 应用程序兼容性**</span><span class="sxs-lookup"><span data-stu-id="8cf52-150">**Windows application compatibility**</span></span>|<span data-ttu-id="8cf52-151">是</span><span class="sxs-lookup"><span data-stu-id="8cf52-151">Yes</span></span>|<span data-ttu-id="8cf52-152">否</span><span class="sxs-lookup"><span data-stu-id="8cf52-152">No</span></span>|<span data-ttu-id="8cf52-153">**是**</span><span class="sxs-lookup"><span data-stu-id="8cf52-153">**Yes**</span></span>|  
|<span data-ttu-id="8cf52-154">**对文件属性的关系访问**</span><span class="sxs-lookup"><span data-stu-id="8cf52-154">**Relational access to file attributes**</span></span>|<span data-ttu-id="8cf52-155">否</span><span class="sxs-lookup"><span data-stu-id="8cf52-155">No</span></span>|<span data-ttu-id="8cf52-156">否</span><span class="sxs-lookup"><span data-stu-id="8cf52-156">No</span></span>|<span data-ttu-id="8cf52-157">**是**</span><span class="sxs-lookup"><span data-stu-id="8cf52-157">**Yes**</span></span>|  
  
##  <a name="comparing-filestream-and-remote-blob-store-rbs"></a><a name="CompareRBS"></a> <span data-ttu-id="8cf52-158">FILESTREAM 和远程 BLOB 存储区 (RBS) 的比较</span><span class="sxs-lookup"><span data-stu-id="8cf52-158">Comparing FILESTREAM and Remote BLOB Store (RBS)</span></span>  
 <span data-ttu-id="8cf52-159">有关这两种功能的比较，请参阅来自 RBS 团队的以下博客： [SQL Server 远程 BLOB 存储区和 FILESTREAM 功能比较](https://go.microsoft.com/fwlink/?LinkId=210317)。</span><span class="sxs-lookup"><span data-stu-id="8cf52-159">For a comparison of these two features, see this blog post from the RBS team: [SQL Server Remote BLOB Store and FILESTREAM feature comparison](https://go.microsoft.com/fwlink/?LinkId=210317).</span></span>  
  
##  <a name="more-information"></a><a name="more"></a> <span data-ttu-id="8cf52-160">详细信息</span><span class="sxs-lookup"><span data-stu-id="8cf52-160">More Information</span></span>  
 [<span data-ttu-id="8cf52-161">FILESTREAM (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="8cf52-161">FILESTREAM &#40;SQL Server&#41;</span></span>](filestream-sql-server.md)  
 [<span data-ttu-id="8cf52-162">FileTables (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="8cf52-162">FileTables &#40;SQL Server&#41;</span></span>](filetables-sql-server.md)  
 [<span data-ttu-id="8cf52-163">远程 Blob 存储区 (RBS) (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="8cf52-163">Remote Blob Store &#40;RBS&#41; &#40;SQL Server&#41;</span></span>](remote-blob-store-rbs-sql-server.md)  
  
