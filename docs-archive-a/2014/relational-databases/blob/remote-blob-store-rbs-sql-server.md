---
title: 远程 Blob 存储 (RBS) (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.technology: filestream
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- Remote Blob Store (RBS) [SQL Server]
- RBS (Remote Blob Store) [SQL Server]
ms.assetid: 31c947cf-53e9-4ff4-939b-4c1d034ea5b1
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8f3425474ec3b9013355536424ffcf55d9426b9c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682894"
---
# <a name="remote-blob-store-rbs-sql-server"></a><span data-ttu-id="bac30-102">远程 Blob 存储区 (RBS) (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="bac30-102">Remote Blob Store (RBS) (SQL Server)</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="bac30-103">远程 BLOB 存储区 (RBS) 是一个可选的附加组件，它允许数据库管理员在商用存储解决方案中存储二进制大型对象，而不是直接存储在主数据库服务器上。</span><span class="sxs-lookup"><span data-stu-id="bac30-103">Remote BLOB Store (RBS) is an optional add-on component that lets database administrators store binary large objects in commodity storage solutions instead of directly on the main database server.</span></span>  
  
 <span data-ttu-id="bac30-104">RBS 包括在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 安装介质上，但 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装程序不安装它。</span><span class="sxs-lookup"><span data-stu-id="bac30-104">RBS is included on the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] installation media, but is not installed by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup program.</span></span>  
  
 <span data-ttu-id="bac30-105">有关 RBS 的详细信息，请参阅本主题中的 [RBS 资源](#rbsresources) 。</span><span class="sxs-lookup"><span data-stu-id="bac30-105">For more information about RBS, see [RBS Resources](#rbsresources) in this topic.</span></span>  
  
## <a name="benefits-of-rbs"></a><span data-ttu-id="bac30-106">RBS 的优点</span><span class="sxs-lookup"><span data-stu-id="bac30-106">Benefits of RBS</span></span>  
 <span data-ttu-id="bac30-107">RBS 具有以下优点：</span><span class="sxs-lookup"><span data-stu-id="bac30-107">RBS provides the following benefits:</span></span>  
  
### <a name="optimized-database-storage-and-performance"></a><span data-ttu-id="bac30-108">优化的数据库存储和性能</span><span class="sxs-lookup"><span data-stu-id="bac30-108">Optimized database storage and performance</span></span>  
 <span data-ttu-id="bac30-109">在数据库中存储 BLOB 可能会占用大量文件空间和昂贵的服务器资源。</span><span class="sxs-lookup"><span data-stu-id="bac30-109">Storing BLOBs in the database can consume large amounts of file space and expensive server resources.</span></span> <span data-ttu-id="bac30-110">RBS 高效地将 BLOB 传输到您选择的专用存储解决方案，在数据库中存储对 BLOB 的引用。</span><span class="sxs-lookup"><span data-stu-id="bac30-110">RBS efficiently transfers the BLOBs to a dedicated storage solution of your choosing, and stores references to them in the database.</span></span> <span data-ttu-id="bac30-111">这样可以释放服务器存储空间用于结构化数据，释放服务器资源用于进行数据库操作。</span><span class="sxs-lookup"><span data-stu-id="bac30-111">This frees server storage for structured data, and frees server resources for database operations.</span></span>  
  
### <a name="efficient-management-of-blobs"></a><span data-ttu-id="bac30-112">高效管理 BLOB</span><span class="sxs-lookup"><span data-stu-id="bac30-112">Efficient management of BLOBs</span></span>  
 <span data-ttu-id="bac30-113">几项 RBS 功能支持对存储的 BLOB 进行方便的管理：</span><span class="sxs-lookup"><span data-stu-id="bac30-113">Several RBS features support the convenient management of stored BLOBs:</span></span>  
  
-   <span data-ttu-id="bac30-114">BLOB 是通过 ACID（原子性、一致性、隔离性和持久性）事务管理的。</span><span class="sxs-lookup"><span data-stu-id="bac30-114">BLOBS are managed with ACID (atomic consistency isolation durable) transactions.</span></span>  
  
-   <span data-ttu-id="bac30-115">BLOB 组织成集合。</span><span class="sxs-lookup"><span data-stu-id="bac30-115">BLOBs are organized into collections.</span></span>  
  
-   <span data-ttu-id="bac30-116">包括垃圾收集、一致性检查和其他维护功能。</span><span class="sxs-lookup"><span data-stu-id="bac30-116">Garbage collection, consistency checking, and other maintenance functions are included.</span></span>  
  
### <a name="standardized-api"></a><span data-ttu-id="bac30-117">标准化 API</span><span class="sxs-lookup"><span data-stu-id="bac30-117">Standardized API</span></span>  
 <span data-ttu-id="bac30-118">RBS 定义一组 API，可为应用程序提供用于访问和修改任何 BLOB 存储的标准化编程模型。</span><span class="sxs-lookup"><span data-stu-id="bac30-118">RBS defines a set of APIs that provide a standardized programming model for applications to access and modify any BLOB store.</span></span> <span data-ttu-id="bac30-119">每个 BLOB 存储区都可以指定自己的提供程序库，该库嵌入 RBS 客户端库，指定存储和访问 BLOB 的方式。</span><span class="sxs-lookup"><span data-stu-id="bac30-119">Each BLOB store can specify its own provider library, which plugs into the RBS client library and specifies how BLOBs are stored and accessed.</span></span>  
  
 <span data-ttu-id="bac30-120">许多第三方存储解决方案供应商都开发了符合这些标准 API、在不同存储平台上支持 BLOB 存储的 RBS 提供程序。</span><span class="sxs-lookup"><span data-stu-id="bac30-120">A number of third-party storage solution vendors have developed RBS providers that conform to these standard APIs and support BLOB storage on various storage platforms.</span></span>  
  
## <a name="rbs-requirements"></a><span data-ttu-id="bac30-121">RBS 要求</span><span class="sxs-lookup"><span data-stu-id="bac30-121">RBS Requirements</span></span>  
 <span data-ttu-id="bac30-122">对于存储 BLOB 元数据的主数据库服务器，RBS 要求安装有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Enterprise。</span><span class="sxs-lookup"><span data-stu-id="bac30-122">RBS requires [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Enterprise for the main database server in which the BLOB metadata is stored.</span></span> <span data-ttu-id="bac30-123">但是，如果使用提供的 FILESTREAM 提供程序，则可以在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Standard 上存储 BLOB 本身。</span><span class="sxs-lookup"><span data-stu-id="bac30-123">However, if you use the supplied FILESTREAM provider, you can store the BLOBs themselves on [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Standard.</span></span>  
  
 <span data-ttu-id="bac30-124">RBS 包括 FILESTREAM 提供程序，因此，您可以使用 RBS 在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的实例上存储 BLOB。</span><span class="sxs-lookup"><span data-stu-id="bac30-124">RBS includes a FILESTREAM provider that lets you use RBS to store BLOBs on an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="bac30-125">如果要使用 RBS 在其他存储解决方案中存储 BLOB，则必须使用为该存储解决方案开发的第三方 RBS 提供程序，或者使用 RBS API 开发自定义 RBS 提供程序。</span><span class="sxs-lookup"><span data-stu-id="bac30-125">If you want use RBS to store BLOBs in a different storage solution, you have to use a third party RBS provider developed for that storage solution, or develop a custom RBS provider using the RBS API.</span></span> <span data-ttu-id="bac30-126">[Codeplex](https://go.microsoft.com/fwlink/?LinkId=210190)上以学习资源的形式提供了在 NTFS 文件系统中存储 BLOB 的示例提供程序。</span><span class="sxs-lookup"><span data-stu-id="bac30-126">A sample provider that stores BLOBs in the NTFS file system is available as a learning resource on [Codeplex](https://go.microsoft.com/fwlink/?LinkId=210190).</span></span>  
  
## <a name="rbs-security"></a><span data-ttu-id="bac30-127">RBS 安全性</span><span class="sxs-lookup"><span data-stu-id="bac30-127">RBS Security</span></span>  
 <span data-ttu-id="bac30-128">当您使用自定义提供程序在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 外存储 BLOB 时，这些 BLOB 可能会被绕过 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安全系统的其他进程所利用。</span><span class="sxs-lookup"><span data-stu-id="bac30-128">When you use a custom provider to store BLOBs outside of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], they may be available to other processes that bypass the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] security system.</span></span> <span data-ttu-id="bac30-129">请确保您使用适合于自定义提供程序所使用的存储介质的权限和加密选项保护存储的 BLOB。</span><span class="sxs-lookup"><span data-stu-id="bac30-129">Make sure that you protect the stored BLOBs with permissions and encryption options that are appropriate to the storage medium used by the custom provider.</span></span>  
  
##  <a name="rbs-resources"></a><a name="rbsresources"></a><span data-ttu-id="bac30-130">RBS 资源</span><span class="sxs-lookup"><span data-stu-id="bac30-130">RBS Resources</span></span>  
 <span data-ttu-id="bac30-131">**RBS 文档**</span><span class="sxs-lookup"><span data-stu-id="bac30-131">**RBS documentation**</span></span>  
 <span data-ttu-id="bac30-132">RBS 文档包括在 Windows 安装程序包中。</span><span class="sxs-lookup"><span data-stu-id="bac30-132">The RBS documentation is included in the Windows installer package.</span></span> <span data-ttu-id="bac30-133">如果您想要不安装 RBS 就查看 RBS 文档，则可以在 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] MSDN 库 [中在线查看该文档的](https://go.microsoft.com/fwlink/?LinkId=210192)版本。</span><span class="sxs-lookup"><span data-stu-id="bac30-133">If you want to review the RBS documentation without installing RBS, you can view the [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] version of the documentation [online in the MSDN Library](https://go.microsoft.com/fwlink/?LinkId=210192).</span></span>  
  
 <span data-ttu-id="bac30-134">**RBS 白皮书**</span><span class="sxs-lookup"><span data-stu-id="bac30-134">**RBS white paper**</span></span>  
 <span data-ttu-id="bac30-135">你可以下载 Microsoft Word 文档格式的白皮书“[远程 BLOB 存储区](https://go.microsoft.com/fwlink/?LinkId=210422)”，它提供有关安装和配置 RBS 的详细信息。</span><span class="sxs-lookup"><span data-stu-id="bac30-135">The white paper "[Remote BLOB Storage](https://go.microsoft.com/fwlink/?LinkId=210422)", which is available for download as a Microsoft Word document, provides detailed information about installing and configuring RBS.</span></span>  
  
 <span data-ttu-id="bac30-136">**RBS 示例**</span><span class="sxs-lookup"><span data-stu-id="bac30-136">**RBS samples**</span></span>  
 <span data-ttu-id="bac30-137">[Codeplex](https://go.microsoft.com/fwlink/?LinkId=210190) 上提供的 RBS 示例演示如何开发 RBS 应用程序，如何开发和安装自定义 RBS 提供程序。</span><span class="sxs-lookup"><span data-stu-id="bac30-137">The RBS samples available on [Codeplex](https://go.microsoft.com/fwlink/?LinkId=210190) demonstrate how to develop an RBS application, and how to develop and install a custom RBS provider.</span></span>  
  
 <span data-ttu-id="bac30-138">**RBS 博客**</span><span class="sxs-lookup"><span data-stu-id="bac30-138">**RBS blog**</span></span>  
 <span data-ttu-id="bac30-139">[RBS 博客](https://go.microsoft.com/fwlink/?LinkId=210315) 提供可帮助你理解、部署和维护 RBS 的其他信息。</span><span class="sxs-lookup"><span data-stu-id="bac30-139">The [RBS blog](https://go.microsoft.com/fwlink/?LinkId=210315) provides additional information to help you understand, deploy, and maintain RBS.</span></span>  
  
  
