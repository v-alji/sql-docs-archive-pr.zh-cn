---
title: 获取有关程序集的信息 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- assemblies [CLR integration], metadata
- status information [SQL Server], assemblies
- metadata [SQL Server], assemblies
ms.assetid: 6aa7f18e-baad-4481-9777-8c3b230b392f
author: rothja
ms.author: jroth
ms.openlocfilehash: ec559ba5ccbb53dd92f3a5e1175a10a59fbaf43c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691252"
---
# <a name="getting-information-about-assemblies"></a><span data-ttu-id="fe2c3-102">获取有关程序集的信息</span><span class="sxs-lookup"><span data-stu-id="fe2c3-102">Getting Information About Assemblies</span></span>
  <span data-ttu-id="fe2c3-103">可以查询下列目录视图和函数来获取有关程序集的元数据。</span><span class="sxs-lookup"><span data-stu-id="fe2c3-103">The following catalog views and functions can be queried for metadata about assemblies.</span></span>  
  
 <span data-ttu-id="fe2c3-104">**获取有关各个程序集的信息**</span><span class="sxs-lookup"><span data-stu-id="fe2c3-104">**To get information about individual assemblies**</span></span>  
  
-   [<span data-ttu-id="fe2c3-105">ASSEMBLYPROPERTY &#40;Transact-sql&#41;</span><span class="sxs-lookup"><span data-stu-id="fe2c3-105">ASSEMBLYPROPERTY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/assemblyproperty-transact-sql)  
  
 <span data-ttu-id="fe2c3-106">**获取有关数据库中所有程序集的信息**</span><span class="sxs-lookup"><span data-stu-id="fe2c3-106">**To get information about all assemblies in the database**</span></span>  
  
-   [<span data-ttu-id="fe2c3-107">sys.databases &#40;Transact-sql&#41;</span><span class="sxs-lookup"><span data-stu-id="fe2c3-107">sys.assemblies &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-assemblies-transact-sql)  
  
 <span data-ttu-id="fe2c3-108">**获取有关程序集文件（包括程序集二进制文件、源文件和调试文件）的信息**</span><span class="sxs-lookup"><span data-stu-id="fe2c3-108">**To get information about assembly files, including assembly binaries, source files, and debug files**</span></span>  
  
-   [<span data-ttu-id="fe2c3-109">sys. assembly_files &#40;Transact-sql&#41;</span><span class="sxs-lookup"><span data-stu-id="fe2c3-109">sys.assembly_files &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-assembly-files-transact-sql)  
  
 <span data-ttu-id="fe2c3-110">**获取有关跨程序集引用的信息**</span><span class="sxs-lookup"><span data-stu-id="fe2c3-110">**To get information about cross-assembly references**</span></span>  
  
-   [<span data-ttu-id="fe2c3-111">sys. assembly_references &#40;Transact-sql&#41;</span><span class="sxs-lookup"><span data-stu-id="fe2c3-111">sys.assembly_references &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-assembly-references-transact-sql)  
  
 <span data-ttu-id="fe2c3-112">**获取有关用户定义类型的程序集信息**</span><span class="sxs-lookup"><span data-stu-id="fe2c3-112">**To get assembly information about user-defined types**</span></span>  
  
-   [<span data-ttu-id="fe2c3-113">sys. assembly_types &#40;Transact-sql&#41;</span><span class="sxs-lookup"><span data-stu-id="fe2c3-113">sys.assembly_types &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-assembly-types-transact-sql)  
  
-   [<span data-ttu-id="fe2c3-114">sys.types (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="fe2c3-114">sys.types &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-types-transact-sql)  
  
 <span data-ttu-id="fe2c3-115">**获取有关公共语言运行时 (CLR) 存储过程、触发器和函数的程序集信息**</span><span class="sxs-lookup"><span data-stu-id="fe2c3-115">**To get assembly information about common language runtime (CLR) stored procedures, triggers, and functions**</span></span>  
  
-   [<span data-ttu-id="fe2c3-116">sys.assembly_modules (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="fe2c3-116">sys.assembly_modules &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-assembly-modules-transact-sql)  
  
 <span data-ttu-id="fe2c3-117">**获取有关非 CLR 对象的信息**</span><span class="sxs-lookup"><span data-stu-id="fe2c3-117">**To get information about non-CLR objects**</span></span>  
  
-   [<span data-ttu-id="fe2c3-118">sys.sql_modules (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="fe2c3-118">sys.sql_modules &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-sql-modules-transact-sql)  
  
## <a name="see-also"></a><span data-ttu-id="fe2c3-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fe2c3-119">See Also</span></span>  
 <span data-ttu-id="fe2c3-120">[程序集 &#40;数据库引擎&#41;](../../relational-databases/clr-integration/assemblies-database-engine.md) </span><span class="sxs-lookup"><span data-stu-id="fe2c3-120">[Assemblies &#40;Database Engine&#41;](../../relational-databases/clr-integration/assemblies-database-engine.md) </span></span>  
 <span data-ttu-id="fe2c3-121">[设计程序集](../../relational-databases/clr-integration/assemblies-designing.md) </span><span class="sxs-lookup"><span data-stu-id="fe2c3-121">[Designing Assemblies](../../relational-databases/clr-integration/assemblies-designing.md) </span></span>  
 [<span data-ttu-id="fe2c3-122">实现程序集</span><span class="sxs-lookup"><span data-stu-id="fe2c3-122">Implementing Assemblies</span></span>](assemblies-implementing.md)  
  
  
