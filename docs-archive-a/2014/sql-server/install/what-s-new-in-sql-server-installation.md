---
title: SQL Server 安装中的新增功能 | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- installing SQL Server, what's new
- SQL Server, what's new
- SQL Server, installing
ms.assetid: c8642a96-3a09-4ec7-a9c3-c539147e6330
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d34085e320cd8ca0b82d382d6d49eaa303086114
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586087"
---
# <a name="what39s-new-in-sql-server-installation"></a><span data-ttu-id="e1377-102">SQL Server 安装中的新增功能</span><span class="sxs-lookup"><span data-stu-id="e1377-102">What&#39;s New in SQL Server Installation</span></span>
  <span data-ttu-id="e1377-103">Windows Vista 不是 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 的支持的操作系统。</span><span class="sxs-lookup"><span data-stu-id="e1377-103">Windows Vista is not a supported operating system for [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)].</span></span> <span data-ttu-id="e1377-104">Service Pack 1 仍将作为针对 [!INCLUDE[win7](../../includes/win7-md.md)] 和 [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] 操作系统的最低要求。</span><span class="sxs-lookup"><span data-stu-id="e1377-104">Service Pack 1 remains as the minimum requirement for [!INCLUDE[win7](../../includes/win7-md.md)] and [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] operating systems.</span></span> <span data-ttu-id="e1377-105">有关操作系统要求的详细信息，请参阅[安装 SQL Server 2014 的硬件和软件要求](hardware-and-software-requirements-for-installing-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="e1377-105">For more information on operating system requirements, see [Hardware and Software Requirements for Installing SQL Server 2014](hardware-and-software-requirements-for-installing-sql-server.md).</span></span>  
  
 <span data-ttu-id="e1377-106">[!INCLUDE[ssExpCurrent](../../includes/ssexpcurrent-md.md)] 的安装将提示您指定要将提取的包保存到的目录。</span><span class="sxs-lookup"><span data-stu-id="e1377-106">Installation of [!INCLUDE[ssExpCurrent](../../includes/ssexpcurrent-md.md)] will prompt you to specify the directory to save the extracted package.</span></span> <span data-ttu-id="e1377-107">如果未输入位置，[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 将默认为计算机的系统驱动器。</span><span class="sxs-lookup"><span data-stu-id="e1377-107">If no location is entered, [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] will default to the computer's system drive.</span></span> <span data-ttu-id="e1377-108">在 [!INCLUDE[ssExpCurrent](../../includes/ssexpcurrent-md.md)] 安装完毕后，提取的文件仍将保持。</span><span class="sxs-lookup"><span data-stu-id="e1377-108">The extracted files will remain after [!INCLUDE[ssExpCurrent](../../includes/ssexpcurrent-md.md)] installation is complete.</span></span>  
  
 <span data-ttu-id="e1377-109">在 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 中，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的所有安装均支持 SysPrep。</span><span class="sxs-lookup"><span data-stu-id="e1377-109">In [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)], SysPrep is supported for all installations of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="e1377-110">SysPrep 现在支持故障转移群集安装。</span><span class="sxs-lookup"><span data-stu-id="e1377-110">SysPrep now supports failover cluster installations.</span></span> <span data-ttu-id="e1377-111">有关详细信息，请参阅[使用 Sysprep 安装 SQL Server 的注意事项](../../database-engine/install-windows/considerations-for-installing-sql-server-using-sysprep.md)和[使用 sysprep 安装 SQL Server 2014](../../database-engine/install-windows/install-sql-server-using-sysprep.md)。</span><span class="sxs-lookup"><span data-stu-id="e1377-111">For more information, see [Considerations for Installing SQL Server Using SysPrep](../../database-engine/install-windows/considerations-for-installing-sql-server-using-sysprep.md) and [Install SQL Server 2014 Using SysPrep](../../database-engine/install-windows/install-sql-server-using-sysprep.md).</span></span>  
  
 <span data-ttu-id="e1377-112">支持从 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 升级，但是不支持并行升级。</span><span class="sxs-lookup"><span data-stu-id="e1377-112">Upgrade from [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] is supported, but side-by-side is not supported.</span></span> <span data-ttu-id="e1377-113">有关 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 中 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]支持的详细信息，请参阅 [支持的版本升级](../../database-engine/install-windows/supported-version-and-edition-upgrades.md)。</span><span class="sxs-lookup"><span data-stu-id="e1377-113">For more information about [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] support in [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)], see [Supported Version and Edition Upgrades](../../database-engine/install-windows/supported-version-and-edition-upgrades.md).</span></span>  
  
 <span data-ttu-id="e1377-114">从 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 开始，Standard 版本中的数据库引擎具有 128 GB 内存容量。</span><span class="sxs-lookup"><span data-stu-id="e1377-114">Beginning in [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)], the database engine in the Standard edition has a memory capacity of 128 GB.</span></span> <span data-ttu-id="e1377-115">在中 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] ，标准版中的数据库引擎的内存容量为 64 GB。</span><span class="sxs-lookup"><span data-stu-id="e1377-115">In [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], the database engine in the Standard edition had a memory capacity of 64 GB.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1377-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e1377-116">See Also</span></span>  
 <span data-ttu-id="e1377-117">[SQL Server 2014 的新增功能](../what-s-new-in-sql-server-2016.md) </span><span class="sxs-lookup"><span data-stu-id="e1377-117">[What's New in SQL Server 2014](../what-s-new-in-sql-server-2016.md) </span></span>  
 <span data-ttu-id="e1377-118">[SQL Server 2014 的产品规格](../../../2014/getting-started/sql-server-2014-product-specifications.md) </span><span class="sxs-lookup"><span data-stu-id="e1377-118">[Product Specifications for SQL Server 2014](../../../2014/getting-started/sql-server-2014-product-specifications.md) </span></span>  
 <span data-ttu-id="e1377-119">[计划 SQL Server 安装](../../../2014/sql-server/install/planning-a-sql-server-installation.md) </span><span class="sxs-lookup"><span data-stu-id="e1377-119">[Planning a SQL Server Installation](../../../2014/sql-server/install/planning-a-sql-server-installation.md) </span></span>  
 [<span data-ttu-id="e1377-120">安装 SQL Server 2014 的硬件和软件要求</span><span class="sxs-lookup"><span data-stu-id="e1377-120">Hardware and Software Requirements for Installing SQL Server 2014</span></span>](hardware-and-software-requirements-for-installing-sql-server.md)  
  
  
