---
title: 非持久化上的全文索引，不允许使用计算列 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- full-text indexes
ms.assetid: cba737f7-b187-47d0-8458-23dc18d18aca
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: de153d45e2f652bfea6e9dce68428af84be68b6c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591741"
---
# <a name="full-text-indexes-on-nonpersisted-computed-columns-are-not-allowed"></a><span data-ttu-id="2f050-102">不允许对非持久化计算列建立全文检索</span><span class="sxs-lookup"><span data-stu-id="2f050-102">Full-text indexes on nonpersisted, computed columns are not allowed</span></span>
  <span data-ttu-id="2f050-103">不能对不确定的计算列和不精确的计算列创建全文检索。</span><span class="sxs-lookup"><span data-stu-id="2f050-103">You cannot create full-text indexes on nondeterministic and imprecise computed columns.</span></span> <span data-ttu-id="2f050-104">此类列不能用作类型列或全文键列。</span><span class="sxs-lookup"><span data-stu-id="2f050-104">Such columns cannot be used as type columns or as full-text key columns.</span></span>  
  
## <a name="description"></a><span data-ttu-id="2f050-105">说明</span><span class="sxs-lookup"><span data-stu-id="2f050-105">Description</span></span>  
 <span data-ttu-id="2f050-106">在 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] 中，可以通过将不确定的计算列和不精确的计算列用作类型列或全文键列来创建全文检索。</span><span class="sxs-lookup"><span data-stu-id="2f050-106">In [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], a full-text index can be created by using a nondeterministic and imprecise computed column as the type column or the full-text key column.</span></span> <span data-ttu-id="2f050-107">现在不支持此功能。</span><span class="sxs-lookup"><span data-stu-id="2f050-107">This functionality is not supported.</span></span> <span data-ttu-id="2f050-108">当升级时，将禁用旧的、不兼容的和不支持的全文检索。</span><span class="sxs-lookup"><span data-stu-id="2f050-108">When you upgrade, older, incompatible, and unsupported full-text indexes are disabled.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="2f050-109">纠正措施</span><span class="sxs-lookup"><span data-stu-id="2f050-109">Corrective Action</span></span>  
 <span data-ttu-id="2f050-110">若要启用这些全文检索，请修改相应的列定义，以使相应的列成为确定、精确的列。</span><span class="sxs-lookup"><span data-stu-id="2f050-110">To enable these full-text indexes, modify the column definitions so that the columns are deterministic and precise.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f050-111">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2f050-111">See Also</span></span>  
 [<span data-ttu-id="2f050-112">使用升级顾问</span><span class="sxs-lookup"><span data-stu-id="2f050-112">Working with Upgrade Advisor</span></span>](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
