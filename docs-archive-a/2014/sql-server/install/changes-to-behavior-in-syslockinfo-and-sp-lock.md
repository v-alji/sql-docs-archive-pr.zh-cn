---
title: Syslockinfo 和 sp_lock 中的行为的更改 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- syslockinfo
- sp_lock
ms.assetid: b9892ae3-ac15-48be-8b52-78dbed6467ed
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 65ace190004cab911dd8996642720620eba94935
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586219"
---
# <a name="changes-to-behavior-in-syslockinfo-and-sp_lock"></a><span data-ttu-id="c8d46-102">对 syslockinfo 和 sp_lock 中的行为的更改</span><span class="sxs-lookup"><span data-stu-id="c8d46-102">Changes to behavior in syslockinfo and sp_lock</span></span>
  <span data-ttu-id="c8d46-103">**syslockinfo**和**sp_lock**可能返回意外值。</span><span class="sxs-lookup"><span data-stu-id="c8d46-103">**syslockinfo** and **sp_lock** may return unexpected values.</span></span> <span data-ttu-id="c8d46-104">它们还可以返回其他行，而以前版本的**syslockinfo**和**sp_lock**每个锁资源最多返回两行。</span><span class="sxs-lookup"><span data-stu-id="c8d46-104">They may also return additional rows, whereas previous versions of **syslockinfo** and **sp_lock** returned a maximum of two rows per lock resource.</span></span>  
  
 <span data-ttu-id="c8d46-105">若要从**syslockinfo**或执行**sp_lock**中访问信息，需要对服务器具有 VIEW server STATE 权限。</span><span class="sxs-lookup"><span data-stu-id="c8d46-105">To access information from **syslockinfo** or execute **sp_lock** requires VIEW SERVER STATE permission on the server.</span></span>  
  
## <a name="component"></a><span data-ttu-id="c8d46-106">组件</span><span class="sxs-lookup"><span data-stu-id="c8d46-106">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="c8d46-107">说明</span><span class="sxs-lookup"><span data-stu-id="c8d46-107">Description</span></span>  
 <span data-ttu-id="c8d46-108">在中 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] ，" **syslockinfo** " 和 " **objid** " 中的 " **rsc_indid** **rsc_objid** " 和 " **indid** " 列在**sp_lock**一致地返回对象 id 和索引 id。</span><span class="sxs-lookup"><span data-stu-id="c8d46-108">In [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], the **rsc_objid** and **rsc_indid** columns in **syslockinfo** and the **objid** and **indid** columns in **sp_lock** consistently return the object ID and index ID.</span></span> <span data-ttu-id="c8d46-109">在 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 中，可能会返回值 0。</span><span class="sxs-lookup"><span data-stu-id="c8d46-109">In [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], a value of 0 may be returned.</span></span>  
  
 <span data-ttu-id="c8d46-110">在中 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] ， **syslockinfo**和**sp_lock**为单个事务中的任何给定的锁资源最多返回两行。</span><span class="sxs-lookup"><span data-stu-id="c8d46-110">In [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], **syslockinfo** and **sp_lock** return a maximum of two rows for any given lock resource in a single transaction.</span></span> <span data-ttu-id="c8d46-111">从 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 开始，如果启用了锁分区，就可以针对在一个事务中运行的同一资源返回多行。</span><span class="sxs-lookup"><span data-stu-id="c8d46-111">Starting with [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], when lock partitioning is enabled, multiple rows for the same resource running under one transaction may be returned.</span></span> <span data-ttu-id="c8d46-112">最多可以返回 N + 1 行，其中 N 是 Cpu 的数目。</span><span class="sxs-lookup"><span data-stu-id="c8d46-112">There may be up to N + 1 rows returned, where N is the number of CPUs.</span></span> <span data-ttu-id="c8d46-113">另外，现在可以针对同一资源显示 GRANTED 和 WAITING 请求，这在 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] 中是不可能实现的。</span><span class="sxs-lookup"><span data-stu-id="c8d46-113">Also, it is now possible to have GRANTED and WAITING requests displayed for the same resource, which was not possible in [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)].</span></span>  
  
## <a name="permissions"></a><span data-ttu-id="c8d46-114">权限</span><span class="sxs-lookup"><span data-stu-id="c8d46-114">Permissions</span></span>  
 <span data-ttu-id="c8d46-115">要求具有服务器的 VIEW SERVER STATE 权限。</span><span class="sxs-lookup"><span data-stu-id="c8d46-115">Requires VIEW SERVER STATE permission on the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8d46-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c8d46-116">See Also</span></span>  
 <span data-ttu-id="c8d46-117">[数据库引擎升级问题](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="c8d46-117">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="c8d46-118">SQL Server 2014 升级顾问 &#91;新&#93;</span><span class="sxs-lookup"><span data-stu-id="c8d46-118">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
