---
title: 数据库引擎配置-Filestream |Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- FILESTREAM [SQL Server], about FILESTREAM
ms.assetid: 641a10a1-ae52-4d26-8f1c-a032a4aeff02
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: ab12b507246a3e13ac59be213813604d531d9a28
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691527"
---
# <a name="database-engine-configuration---filestream"></a><span data-ttu-id="2613d-102">数据库引擎配置 - 文件流</span><span class="sxs-lookup"><span data-stu-id="2613d-102">Database Engine Configuration - Filestream</span></span>
  <span data-ttu-id="2613d-103">使用此页可针对此 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]安装启用 FILESTREAM。</span><span class="sxs-lookup"><span data-stu-id="2613d-103">Use this page to enable FILESTREAM for this installation of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="2613d-104">FILESTREAM [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 通过将 `varbinary(max)` 二进制大型对象 (BLOB) 数据作为文件存储在文件系统上，将与 NTFS 文件系统集成。</span><span class="sxs-lookup"><span data-stu-id="2613d-104">FILESTREAM integrates the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] with an NTFS file system by storing `varbinary(max)` binary large object (BLOB) data as files on the file system.</span></span> [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="2613d-105">语句可插入、更新、查询、搜索和备份 FILESTREAM 数据。</span><span class="sxs-lookup"><span data-stu-id="2613d-105">statements can insert, update, query, search, and back up FILESTREAM data.</span></span> <span data-ttu-id="2613d-106">Win32 文件系统接口提供对数据的流访问权限。</span><span class="sxs-lookup"><span data-stu-id="2613d-106">Win32 file system interfaces provide streaming access to the data.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="2613d-107">UI 元素列表</span><span class="sxs-lookup"><span data-stu-id="2613d-107">UI element list</span></span>  
 <span data-ttu-id="2613d-108">**针对 Transact-SQL 访问启用 FILESTREAM**</span><span class="sxs-lookup"><span data-stu-id="2613d-108">**Enable FILESTREAM for Transact-SQL access**</span></span>  
 <span data-ttu-id="2613d-109">选中此项可针对 [!INCLUDE[tsql](../../includes/tsql-md.md)] 访问启用 FILESTREAM。</span><span class="sxs-lookup"><span data-stu-id="2613d-109">Select to enable FILESTREAM for [!INCLUDE[tsql](../../includes/tsql-md.md)] access.</span></span> <span data-ttu-id="2613d-110">必须选中此控制选项，才能使用其他控制选项。</span><span class="sxs-lookup"><span data-stu-id="2613d-110">This control must be checked before the other control options will be available.</span></span>  
  
 <span data-ttu-id="2613d-111">**针对文件 I/O 流访问启用 FILESTREAM**</span><span class="sxs-lookup"><span data-stu-id="2613d-111">**Enable FILESTREAM for file I/O streaming access**</span></span>  
 <span data-ttu-id="2613d-112">选中此项可针对 FILESTREAM 启用 Win32 流访问。</span><span class="sxs-lookup"><span data-stu-id="2613d-112">Select to enable Win32 streaming access for FILESTREAM.</span></span>  
  
 <span data-ttu-id="2613d-113">**Windows 共享名**</span><span class="sxs-lookup"><span data-stu-id="2613d-113">**Windows share name**</span></span>  
 <span data-ttu-id="2613d-114">使用此控制选项可输入将用来存储 FILESTREAM 数据的 Windows 共享的名称。</span><span class="sxs-lookup"><span data-stu-id="2613d-114">Use this control to enter the name of the Windows share in which the FILESTREAM data will be stored.</span></span>  
  
 <span data-ttu-id="2613d-115">**允许远程客户端针对 FILESTREAM 数据启用流访问**</span><span class="sxs-lookup"><span data-stu-id="2613d-115">**Allow remote clients to have streaming access to FILESTREAM data**</span></span>  
 <span data-ttu-id="2613d-116">选中此控制选项可允许远程客户端访问此服务器上的此 FILESTREAM 数据。</span><span class="sxs-lookup"><span data-stu-id="2613d-116">Select this control to allow remote clients to access this FILESTREAM data on this server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2613d-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2613d-117">See Also</span></span>  
 <span data-ttu-id="2613d-118">[启用和配置 FILESTREAM](../../relational-databases/blob/enable-and-configure-filestream.md) </span><span class="sxs-lookup"><span data-stu-id="2613d-118">[Enable and Configure FILESTREAM](../../relational-databases/blob/enable-and-configure-filestream.md) </span></span>  
 [<span data-ttu-id="2613d-119">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="2613d-119">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
