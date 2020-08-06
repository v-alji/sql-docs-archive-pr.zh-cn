---
title: 二进制大型对象 (Blob) 数据 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- FILESTREAM [SQL Server], design and implementation
ms.assetid: 97509274-c3f8-43e5-a37c-52f1ffe0961a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: a663dedf34d75a21ee8df6b97979548c04abf7ff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589726"
---
# <a name="binary-large-object-blob-data-sql-server"></a><span data-ttu-id="059c4-102">二进制大型对象 (Blob) 数据 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="059c4-102">Binary Large Object (Blob) Data (SQL Server)</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="059c4-103">提供用于在数据库中或远程存储设备上存储文件和文档的解决方案。</span><span class="sxs-lookup"><span data-stu-id="059c4-103">provides solutions for storing files and documents in the database or on remote storage devices.</span></span>  
  
##  <a name="in-this-section"></a><a name="section"></a> <span data-ttu-id="059c4-104">本节内容</span><span class="sxs-lookup"><span data-stu-id="059c4-104">In This Section</span></span>  
 [<span data-ttu-id="059c4-105">比较用于存储 Blob 的选项 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="059c4-105">Compare Options for Storing Blobs &#40;SQL Server&#41;</span></span>](compare-options-for-storing-blobs-sql-server.md)  
 <span data-ttu-id="059c4-106">比较 FILESTREAM、FileTable 和远程 Blob 存储区的优劣</span><span class="sxs-lookup"><span data-stu-id="059c4-106">Compare the advantages of FILESTREAM, FileTables, and Remote Blob Store.</span></span>  
  
 [<span data-ttu-id="059c4-107">FILESTREAM (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="059c4-107">FILESTREAM &#40;SQL Server&#41;</span></span>](filestream-sql-server.md)  
 <span data-ttu-id="059c4-108">借助 FILESTREAM，基于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的应用程序可以将非结构化的数据（如文档和图像）存储在文件系统中。</span><span class="sxs-lookup"><span data-stu-id="059c4-108">FILESTREAM enables [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-based applications to store unstructured data, such as documents and images, on the file system.</span></span> <span data-ttu-id="059c4-109">应用程序在利用丰富的流式 API 和文件系统的性能的同时，还可保持非结构化数据和对应的结构化数据之间的事务一致性。</span><span class="sxs-lookup"><span data-stu-id="059c4-109">Applications can leverage the rich streaming APIs and performance of the file system and at the same time maintain transactional consistency between the unstructured data and corresponding structured data.</span></span>  
  
 [<span data-ttu-id="059c4-110">FileTables (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="059c4-110">FileTables &#40;SQL Server&#41;</span></span>](filetables-sql-server.md)  
 <span data-ttu-id="059c4-111">FileTable 功能为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中存储的文件数据提供对 Windows 文件命名空间的支持以及与 Windows 应用程序的兼容性支持。</span><span class="sxs-lookup"><span data-stu-id="059c4-111">The FileTable feature brings support for the Windows file namespace and compatibility with Windows applications to the file data stored in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="059c4-112">FileTable 使得应用程序可以集成其存储和数据管理组件，可对非结构化数据和元数据提供集成的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务（包括全文搜索和语义搜索）。</span><span class="sxs-lookup"><span data-stu-id="059c4-112">FileTable lets an application integrate its storage and data management components, and provides integrated [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services - including full-text search and semantic search - over unstructured data and metadata.</span></span>  
  
 <span data-ttu-id="059c4-113">换言之，您可以在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中将文件和文档存储在称作 FileTable 的特别的表中，但是从 Windows 应用程序访问它们，就好像它们存储在文件系统中，而不必对您的客户端应用程序进行任何更改。</span><span class="sxs-lookup"><span data-stu-id="059c4-113">In other words, you can store files and documents in special tables in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] called FileTables, but access them from Windows applications as if they were stored in the file system, without making any changes to your client applications.</span></span>  
  
 [<span data-ttu-id="059c4-114">远程 Blob 存储区 (RBS) (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="059c4-114">Remote Blob Store &#40;RBS&#41; &#40;SQL Server&#41;</span></span>](remote-blob-store-rbs-sql-server.md)  
 <span data-ttu-id="059c4-115">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的远程 BLOB 存储 (RBS) 使数据库管理员能够在商用存储解决方案中存储二进制大型对象 (BLOB)，而不是直接存储在服务器上。</span><span class="sxs-lookup"><span data-stu-id="059c4-115">Remote BLOB store (RBS) for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] lets database administrators store binary large objects (BLOBs) in commodity storage solutions instead of directly on the server.</span></span> <span data-ttu-id="059c4-116">这可以节省大量空间，避免浪费昂贵的服务器硬件资源。</span><span class="sxs-lookup"><span data-stu-id="059c4-116">This saves a significant amount of space and avoids wasting expensive server hardware resources.</span></span> <span data-ttu-id="059c4-117">RBS 提供一组可定义应用程序标准化模型的 API 库以访问 BLOB 数据。</span><span class="sxs-lookup"><span data-stu-id="059c4-117">RBS provides a set of API libraries that define a standardized model for applications to access BLOB data.</span></span> <span data-ttu-id="059c4-118">RBS 还包含维护工具（如垃圾收集）以帮助管理远程 BLOB 数据。</span><span class="sxs-lookup"><span data-stu-id="059c4-118">RBS also includes maintenance tools, such as garbage collection, to help manage remote BLOB data.</span></span>  
  
 <span data-ttu-id="059c4-119">RBS 包括在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装介质上，但 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装程序不安装它。</span><span class="sxs-lookup"><span data-stu-id="059c4-119">RBS is included on the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation media, but is not installed by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup program.</span></span>  
  
  
