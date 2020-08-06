---
title: 修改使用了不再使用的全文搜索属性的存储过程 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- discontinued properties [Full-Text Search]
- stored procedures [Full-Text Search]
ms.assetid: 8d9392d9-a9ba-4378-84e4-59f516b67ddb
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 12262a588742f0e3be094e32a2a0208a85b6f28a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586170"
---
# <a name="modify-stored-procedures-that-use-discontinued-full-text-search-properties"></a><span data-ttu-id="f5cbf-102">修改使用已停用全文搜索属性的存储过程</span><span class="sxs-lookup"><span data-stu-id="f5cbf-102">Modify stored procedures that use discontinued Full-Text Search properties</span></span>
  <span data-ttu-id="f5cbf-103">为确保存储过程正确执行，应编辑现有过程并删除已删除或已废弃的与全文相关的属性和设置。</span><span class="sxs-lookup"><span data-stu-id="f5cbf-103">To ensure that your stored procedures perform correctly, you should edit existing procedures and remove those full-text related properties and settings that have been removed or deprecated.</span></span>  
  
## <a name="component"></a><span data-ttu-id="f5cbf-104">组件</span><span class="sxs-lookup"><span data-stu-id="f5cbf-104">Component</span></span>  
 <span data-ttu-id="f5cbf-105">全文搜索</span><span class="sxs-lookup"><span data-stu-id="f5cbf-105">Full-Text Search</span></span>  
  
## <a name="description"></a><span data-ttu-id="f5cbf-106">说明</span><span class="sxs-lookup"><span data-stu-id="f5cbf-106">Description</span></span>  
 <span data-ttu-id="f5cbf-107">以下与全文搜索相关的属性和设置已删除。</span><span class="sxs-lookup"><span data-stu-id="f5cbf-107">The following Full-Text Search-related properties and settings have been removed.</span></span>  
  
-   <span data-ttu-id="f5cbf-108">**DataTimeout**</span><span class="sxs-lookup"><span data-stu-id="f5cbf-108">**DataTimeout**</span></span>  
  
-   <span data-ttu-id="f5cbf-109">**ConnectTimeout**</span><span class="sxs-lookup"><span data-stu-id="f5cbf-109">**ConnectTimeout**</span></span>  
  
-   <span data-ttu-id="f5cbf-110">**Clean_up**</span><span class="sxs-lookup"><span data-stu-id="f5cbf-110">**Clean_up**</span></span>  
  
-   <span data-ttu-id="f5cbf-111">**LogSize**</span><span class="sxs-lookup"><span data-stu-id="f5cbf-111">**LogSize**</span></span>  
  
 <span data-ttu-id="f5cbf-112">以下与全文搜索相关的属性和设置已删除或已废弃：</span><span class="sxs-lookup"><span data-stu-id="f5cbf-112">The following Full-Text Search-related properties and settings have been removed or deprecated:</span></span>  
  
-   <span data-ttu-id="f5cbf-113">全文目录的“路径”。</span><span class="sxs-lookup"><span data-stu-id="f5cbf-113">'Path' of the Full-Text Catalog.</span></span> <span data-ttu-id="f5cbf-114">全文目录将是在系统中没有特定文件路径的一个逻辑对象。</span><span class="sxs-lookup"><span data-stu-id="f5cbf-114">The Full-Text Catalog will be a logic object without a specific file path in the system.</span></span>  
  
-   <span data-ttu-id="f5cbf-115">在 SP_FULLTEXT_DATABASE 中启用/禁用全文检索不会再产生任何影响，这是因为 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 中在任何时间（以及在默认情况下）总是为数据库启用全文搜索。</span><span class="sxs-lookup"><span data-stu-id="f5cbf-115">Enable/disable in SP_FULLTEXT_DATABASE has no effect anymore as databases are enabled for Full-Text Search at all times and by default in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="f5cbf-116">纠正措施</span><span class="sxs-lookup"><span data-stu-id="f5cbf-116">Corrective Action</span></span>  
 <span data-ttu-id="f5cbf-117">修改存储过程以删除这些属性。</span><span class="sxs-lookup"><span data-stu-id="f5cbf-117">Modify your stored procedures to remove these properties.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5cbf-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f5cbf-118">See Also</span></span>  
 [<span data-ttu-id="f5cbf-119">使用升级顾问</span><span class="sxs-lookup"><span data-stu-id="f5cbf-119">Working with Upgrade Advisor</span></span>](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
