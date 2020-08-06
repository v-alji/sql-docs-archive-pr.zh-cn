---
title: 不支持对 master、tempdb 和 model 数据库建立全文索引 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- full-text indexes
ms.assetid: f7992965-42c1-4eb8-a7fb-afb38b67c740
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: fbd5e3133ed87fed9bdaf6d668df62c6471df766
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591742"
---
# <a name="full-text-indexes-on-master-tempdb-and-model-databases-are-not-supported"></a><span data-ttu-id="ea0a5-102">不支持对 master、tempdb 和 model 数据库建立全文检索</span><span class="sxs-lookup"><span data-stu-id="ea0a5-102">Full-text indexes on master, tempdb and model databases are not supported</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="ea0a5-103">不允许对任何系统数据库建立全文检索。</span><span class="sxs-lookup"><span data-stu-id="ea0a5-103">does not allow full-text indexes on any system database.</span></span>  
  
## <a name="description"></a><span data-ttu-id="ea0a5-104">说明</span><span class="sxs-lookup"><span data-stu-id="ea0a5-104">Description</span></span>  
 <span data-ttu-id="ea0a5-105">在 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] 中，支持对 master、tempdb 和 model 数据库建立全文索引。</span><span class="sxs-lookup"><span data-stu-id="ea0a5-105">In [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], full-text indexes were supported on the master, tempdb, and model databases.</span></span>  
  
 <span data-ttu-id="ea0a5-106">在升级过程中，将删除 master、tempdb 和 model 数据库中的所有全文目录。</span><span class="sxs-lookup"><span data-stu-id="ea0a5-106">Any full-text catalogs in the master, tempdb, and model databases are removed during the upgrade.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea0a5-107">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ea0a5-107">See Also</span></span>  
 [<span data-ttu-id="ea0a5-108">使用升级顾问</span><span class="sxs-lookup"><span data-stu-id="ea0a5-108">Working with Upgrade Advisor</span></span>](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
